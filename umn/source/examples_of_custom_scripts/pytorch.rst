.. _modelarts_23_0175:

PyTorch
=======

Training a Model
----------------

+-----------------------------------+------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                   |
|                                   |                                                                                                      |
|     1                             |    from __future__ import print_function                                                             |
|     2                             |    import argparse                                                                                   |
|     3                             |    import torch                                                                                      |
|     4                             |    import torch.nn as nn                                                                             |
|     5                             |    import torch.nn.functional as F                                                                   |
|     6                             |    import torch.optim as optim                                                                       |
|     7                             |    from torchvision import datasets, transforms                                                      |
|     8                             |                                                                                                      |
|     9                             |    # Define a network structure.                                                                     |
|    10                             |    class Net(nn.Module):                                                                             |
|    11                             |        def __init__(self):                                                                           |
|    12                             |            super(Net, self).__init__()                                                               |
|    13                             |    # The second dimension of the input must be 784.                                                  |
|    14                             |            self.hidden1 = nn.Linear(784, 5120, bias=False)                                           |
|    15                             |            self.output = nn.Linear(5120, 10, bias=False)                                             |
|    16                             |                                                                                                      |
|    17                             |        def forward(self, x):                                                                         |
|    18                             |            x = x.view(x.size()[0], -1)                                                               |
|    19                             |            x = F.relu((self.hidden1(x)))                                                             |
|    20                             |            x = F.dropout(x, 0.2)                                                                     |
|    21                             |            x = self.output(x)                                                                        |
|    22                             |            return F.log_softmax(x)                                                                   |
|    23                             |                                                                                                      |
|    24                             |    def train(model, device, train_loader, optimizer, epoch):                                         |
|    25                             |        model.train()                                                                                 |
|    26                             |        for batch_idx, (data, target) in enumerate(train_loader):                                     |
|    27                             |            data, target = data.to(device), target.to(device)                                         |
|    28                             |            optimizer.zero_grad()                                                                     |
|    29                             |            output = model(data)                                                                      |
|    30                             |            loss = F.cross_entropy(output, target)                                                    |
|    31                             |            loss.backward()                                                                           |
|    32                             |            optimizer.step()                                                                          |
|    33                             |            if batch_idx % 10 == 0:                                                                   |
|    34                             |                print('Train Epoch: {} [{}/{} ({:.0f}%)]\tLoss: {:.6f}'.format(                       |
|    35                             |                    epoch, batch_idx * len(data), len(train_loader.dataset),                          |
|    36                             |                           100. * batch_idx / len(train_loader), loss.item()))                        |
|    37                             |                                                                                                      |
|    38                             |    def test( model, device, test_loader):                                                            |
|    39                             |        model.eval()                                                                                  |
|    40                             |        test_loss = 0                                                                                 |
|    41                             |        correct = 0                                                                                   |
|    42                             |        with torch.no_grad():                                                                         |
|    43                             |            for data, target in test_loader:                                                          |
|    44                             |                data, target = data.to(device), target.to(device)                                     |
|    45                             |                output = model(data)                                                                  |
|    46                             |                test_loss += F.nll_loss(output, target, reduction='sum').item()  # sum up batch loss  |
|    47                             |                pred = output.argmax(dim=1, keepdim=True)  # get the index of the max log-probability |
|    48                             |                correct += pred.eq(target.view_as(pred)).sum().item()                                 |
|    49                             |                                                                                                      |
|    50                             |        test_loss /= len(test_loader.dataset)                                                         |
|    51                             |                                                                                                      |
|    52                             |        print('\nTest set: Average loss: {:.4f}, Accuracy: {}/{} ({:.0f}%)\n'.format(                 |
|    53                             |            test_loss, correct, len(test_loader.dataset),                                             |
|    54                             |            100. * correct / len(test_loader.dataset)))                                               |
|    55                             |                                                                                                      |
|    56                             |    device = torch.device("cpu")                                                                      |
|    57                             |                                                                                                      |
|    58                             |    batch_size=64                                                                                     |
|    59                             |                                                                                                      |
|    60                             |    kwargs={}                                                                                         |
|    61                             |                                                                                                      |
|    62                             |    train_loader = torch.utils.data.DataLoader(                                                       |
|    63                             |        datasets.MNIST('.', train=True, download=True,                                                |
|    64                             |                       transform=transforms.Compose([                                                 |
|    65                             |                           transforms.ToTensor()                                                      |
|    66                             |                       ])),                                                                           |
|    67                             |        batch_size=batch_size, shuffle=True, **kwargs)                                                |
|    68                             |    test_loader = torch.utils.data.DataLoader(                                                        |
|    69                             |        datasets.MNIST('.', train=False, transform=transforms.Compose([                               |
|    70                             |            transforms.ToTensor()                                                                     |
|    71                             |        ])),                                                                                          |
|    72                             |        batch_size=1000, shuffle=True, **kwargs)                                                      |
|    73                             |                                                                                                      |
|    74                             |    model = Net().to(device)                                                                          |
|    75                             |    optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.5)                                  |
|    76                             |    optimizer = optim.Adam(model.parameters())                                                        |
|    77                             |                                                                                                      |
|    78                             |    for epoch in range(1, 2 + 1):                                                                     |
|    79                             |        train(model, device, train_loader, optimizer, epoch)                                          |
|    80                             |        test(model, device, test_loader)                                                              |
+-----------------------------------+------------------------------------------------------------------------------------------------------+

Saving a Model
--------------

+-----------------------------------+-----------------------------------------------------------------------------+
| ::                                | ::                                                                          |
|                                   |                                                                             |
|    1                              |    # The model must be saved using state_dict and can be deployed remotely. |
|    2                              |    torch.save(model.state_dict(), "pytorch_mnist/mnist_mlp.pt")             |
+-----------------------------------+-----------------------------------------------------------------------------+

Inference Code
--------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                       |
|                                   |                                                                                                          |
|      1                            |    from PIL import Image                                                                                 |
|      2                            |    import log                                                                                            |
|      3                            |    from model_service.pytorch_model_service import PTServingBaseService                                  |
|      4                            |    import torch.nn.functional as F                                                                       |
|      5                            |                                                                                                          |
|      6                            |    import torch.nn as nn                                                                                 |
|      7                            |    import torch                                                                                          |
|      8                            |    import json                                                                                           |
|      9                            |                                                                                                          |
|     10                            |    import numpy as np                                                                                    |
|     11                            |                                                                                                          |
|     12                            |    logger = log.getLogger(__name__)                                                                      |
|     13                            |                                                                                                          |
|     14                            |    import torchvision.transforms as transforms                                                           |
|     15                            |                                                                                                          |
|     16                            |    # Define model preprocessing.                                                                         |
|     17                            |    infer_transformation = transforms.Compose([                                                           |
|     18                            |        transforms.Resize((28,28)),                                                                       |
|     19                            |        # Transform to a PyTorch tensor.                                                                  |
|     20                            |        transforms.ToTensor()                                                                             |
|     21                            |    ])                                                                                                    |
|     22                            |                                                                                                          |
|     23                            |                                                                                                          |
|     24                            |    import os                                                                                             |
|     25                            |                                                                                                          |
|     26                            |                                                                                                          |
|     27                            |    class PTVisionService(PTServingBaseService):                                                          |
|     28                            |                                                                                                          |
|     29                            |        def __init__(self, model_name, model_path):                                                       |
|     30                            |            # Call the constructor of the parent class.                                                   |
|     31                            |            super(PTVisionService, self).__init__(model_name, model_path)                                 |
|     32                            |            # Call the customized function to load the model.                                             |
|     33                            |            self.model = Mnist(model_path)                                                                |
|     34                            |             # Load tags.                                                                                 |
|     35                            |            self.label = [0,1,2,3,4,5,6,7,8,9]                                                            |
|     36                            |            # Labels can also be loaded by label file.                                                    |
|     37                            |            # Store the label.json file in the model directory. The following information is read:        |
|     38                            |            dir_path = os.path.dirname(os.path.realpath(self.model_path))                                 |
|     39                            |            with open(os.path.join(dir_path, 'label.json')) as f:                                         |
|     40                            |                self.label = json.load(f)                                                                 |
|     41                            |                                                                                                          |
|     42                            |                                                                                                          |
|     43                            |        def _preprocess(self, data):                                                                      |
|     44                            |                                                                                                          |
|     45                            |            preprocessed_data = {}                                                                        |
|     46                            |            for k, v in data.items():                                                                     |
|     47                            |                input_batch = []                                                                          |
|     48                            |                for file_name, file_content in v.items():                                                 |
|     49                            |                    with Image.open(file_content) as image1:                                              |
|     50                            |                        # Gray processing                                                                 |
|     51                            |                        image1 = image1.convert("L")                                                      |
|     52                            |                        if torch.cuda.is_available():                                                     |
|     53                            |                            input_batch.append(infer_transformation(image1).cuda())                       |
|     54                            |                        else:                                                                             |
|     55                            |                            input_batch.append(infer_transformation(image1))                              |
|     56                            |                input_batch_var = torch.autograd.Variable(torch.stack(input_batch, dim=0), volatile=True) |
|     57                            |                print(input_batch_var.shape)                                                              |
|     58                            |                preprocessed_data[k] = input_batch_var                                                    |
|     59                            |                                                                                                          |
|     60                            |            return preprocessed_data                                                                      |
|     61                            |                                                                                                          |
|     62                            |        def _postprocess(self, data):                                                                     |
|     63                            |            results = []                                                                                  |
|     64                            |            for k, v in data.items():                                                                     |
|     65                            |                result = torch.argmax(v[0])                                                               |
|     66                            |                result = {k: self.label[result]}                                                          |
|     67                            |                results.append(result)                                                                    |
|     68                            |            return results                                                                                |
|     69                            |                                                                                                          |
|     70                            |    class Net(nn.Module):                                                                                 |
|     71                            |        def __init__(self):                                                                               |
|     72                            |            super(Net, self).__init__()                                                                   |
|     73                            |            self.hidden1 = nn.Linear(784, 5120, bias=False)                                               |
|     74                            |            self.output = nn.Linear(5120, 10, bias=False)                                                 |
|     75                            |                                                                                                          |
|     76                            |        def forward(self, x):                                                                             |
|     77                            |            x = x.view(x.size()[0], -1)                                                                   |
|     78                            |            x = F.relu((self.hidden1(x)))                                                                 |
|     79                            |            x = F.dropout(x, 0.2)                                                                         |
|     80                            |            x = self.output(x)                                                                            |
|     81                            |            return F.log_softmax(x)                                                                       |
|     82                            |                                                                                                          |
|     83                            |                                                                                                          |
|     84                            |                                                                                                          |
|     85                            |    def Mnist(model_path, **kwargs):                                                                      |
|     86                            |        # Generate a network.                                                                             |
|     87                            |        model = Net()                                                                                     |
|     88                            |        # Load the model.                                                                                 |
|     89                            |        if torch.cuda.is_available():                                                                     |
|     90                            |            device = torch.device('cuda')                                                                 |
|     91                            |            model.load_state_dict(torch.load(model_path, map_location="cuda:0"))                          |
|     92                            |        else:                                                                                             |
|     93                            |            device = torch.device('cpu')                                                                  |
|     94                            |            model.load_state_dict(torch.load(model_path, map_location=device))                            |
|     95                            |        # CPU or GPU mapping                                                                              |
|     96                            |        model.to(device)                                                                                  |
|     97                            |        # Declare an inference mode.                                                                      |
|     98                            |        model.eval()                                                                                      |
|     99                            |                                                                                                          |
|    100                            |        return model                                                                                      |
+-----------------------------------+----------------------------------------------------------------------------------------------------------+
