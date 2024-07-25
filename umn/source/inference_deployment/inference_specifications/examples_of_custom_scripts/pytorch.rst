:original_name: inference-modelarts-0082.html

.. _inference-modelarts-0082:

PyTorch
=======

Training a Model
----------------

.. code-block::

   from __future__ import print_function
   import argparse
   import torch
   import torch.nn as nn
   import torch.nn.functional as F
   import torch.optim as optim
   from torchvision import datasets, transforms

   # Define a network structure.
   class Net(nn.Module):
       def __init__(self):
           super(Net, self).__init__()
   # The second dimension of the input must be 784.
           self.hidden1 = nn.Linear(784, 5120, bias=False)
           self.output = nn.Linear(5120, 10, bias=False)

       def forward(self, x):
           x = x.view(x.size()[0], -1)
           x = F.relu((self.hidden1(x)))
           x = F.dropout(x, 0.2)
           x = self.output(x)
           return F.log_softmax(x)

   def train(model, device, train_loader, optimizer, epoch):
       model.train()
       for batch_idx, (data, target) in enumerate(train_loader):
           data, target = data.to(device), target.to(device)
           optimizer.zero_grad()
           output = model(data)
           loss = F.cross_entropy(output, target)
           loss.backward()
           optimizer.step()
           if batch_idx % 10 == 0:
               print('Train Epoch: {} [{}/{} ({:.0f}%)]\tLoss: {:.6f}'.format(
                   epoch, batch_idx * len(data), len(train_loader.dataset),
                          100. * batch_idx / len(train_loader), loss.item()))

   def test( model, device, test_loader):
       model.eval()
       test_loss = 0
       correct = 0
       with torch.no_grad():
           for data, target in test_loader:
               data, target = data.to(device), target.to(device)
               output = model(data)
               test_loss += F.nll_loss(output, target, reduction='sum').item()  # sum up batch loss
               pred = output.argmax(dim=1, keepdim=True)  # get the index of the max log-probability
               correct += pred.eq(target.view_as(pred)).sum().item()

       test_loss /= len(test_loader.dataset)

       print('\nTest set: Average loss: {:.4f}, Accuracy: {}/{} ({:.0f}%)\n'.format(
           test_loss, correct, len(test_loader.dataset),
           100. * correct / len(test_loader.dataset)))

   device = torch.device("cpu")

   batch_size=64

   kwargs={}

   train_loader = torch.utils.data.DataLoader(
       datasets.MNIST('.', train=True, download=True,
                      transform=transforms.Compose([
                          transforms.ToTensor()
                      ])),
       batch_size=batch_size, shuffle=True, **kwargs)
   test_loader = torch.utils.data.DataLoader(
       datasets.MNIST('.', train=False, transform=transforms.Compose([
           transforms.ToTensor()
       ])),
       batch_size=1000, shuffle=True, **kwargs)

   model = Net().to(device)
   optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.5)
   optimizer = optim.Adam(model.parameters())

   for epoch in range(1, 2 + 1):
       train(model, device, train_loader, optimizer, epoch)
       test(model, device, test_loader)

Saving a Model
--------------

.. code-block::

   # The model must be saved using state_dict and can be deployed remotely.
   torch.save(model.state_dict(), "pytorch_mnist/mnist_mlp.pt")

Inference Code
--------------

In the model inference code file **customize_service.py**, add a child model class which inherits properties from its parent model class. For details about the import statements of different types of parent model classes, see :ref:`Table 1 <en-us_topic_0000001910014882__en-us_topic_0172466150_table55021545175412>`.

.. code-block::

   from PIL import Image
   import log
   from model_service.pytorch_model_service import PTServingBaseService
   import torch.nn.functional as F

   import torch.nn as nn
   import torch
   import json

   import numpy as np

   logger = log.getLogger(__name__)

   import torchvision.transforms as transforms

   # Define model preprocessing.
   infer_transformation = transforms.Compose([
       transforms.Resize((28,28)),
       # Transform to a PyTorch tensor.
       transforms.ToTensor()
   ])


   import os


   class PTVisionService(PTServingBaseService):

       def __init__(self, model_name, model_path):
           # Call the constructor of the parent class.
           super(PTVisionService, self).__init__(model_name, model_path)
           # Call the customized function to load the model.
           self.model = Mnist(model_path)
            # Load tags.
           self.label = [0,1,2,3,4,5,6,7,8,9]
           # Labels can also be loaded by label file.
           # Store the label.json file in the model directory. The following information is read:
           dir_path = os.path.dirname(os.path.realpath(self.model_path))
           with open(os.path.join(dir_path, 'label.json')) as f:
               self.label = json.load(f)


       def _preprocess(self, data):

           preprocessed_data = {}
           for k, v in data.items():
               input_batch = []
               for file_name, file_content in v.items():
                   with Image.open(file_content) as image1:
                       # Gray processing
                       image1 = image1.convert("L")
                       if torch.cuda.is_available():
                           input_batch.append(infer_transformation(image1).cuda())
                       else:
                           input_batch.append(infer_transformation(image1))
               input_batch_var = torch.autograd.Variable(torch.stack(input_batch, dim=0), volatile=True)
               print(input_batch_var.shape)
               preprocessed_data[k] = input_batch_var

           return preprocessed_data

       def _postprocess(self, data):
           results = []
           for k, v in data.items():
               result = torch.argmax(v[0])
               result = {k: self.label[result]}
               results.append(result)
           return results

       def _inference(self, data):

           result = {}
           for k, v in data.items():
               result[k] = self.model(v)

           return result

   class Net(nn.Module):
       def __init__(self):
           super(Net, self).__init__()
           self.hidden1 = nn.Linear(784, 5120, bias=False)
           self.output = nn.Linear(5120, 10, bias=False)

       def forward(self, x):
           x = x.view(x.size()[0], -1)
           x = F.relu((self.hidden1(x)))
           x = F.dropout(x, 0.2)
           x = self.output(x)
           return F.log_softmax(x)



   def Mnist(model_path, **kwargs):
       # Generate a network.
       model = Net()
       # Load the model.
       if torch.cuda.is_available():
           device = torch.device('cuda')
           model.load_state_dict(torch.load(model_path, map_location="cuda:0"))
       else:
           device = torch.device('cpu')
           model.load_state_dict(torch.load(model_path, map_location=device))
       # CPU or GPU mapping
       model.to(device)
       # Declare an inference mode.
       model.eval()

       return model
