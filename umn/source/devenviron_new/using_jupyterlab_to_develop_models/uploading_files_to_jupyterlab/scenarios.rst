:original_name: modelarts_30_0042.html

.. _modelarts_30_0042:

Scenarios
=========

Easy and fast file uploading is a common requirement in AI development.

Before the optimization, ModelArts only allowed local files not exceeding 100 MB to be directly uploaded to a notebook instance. However, the files to be uploaded are not all stored locally, which may be from an open-source repository of GitHub, an open-source dataset (https://nodejs.org/dist/v12.4.0/node-v12.4.0-linux-x64.tar.xz), or OBS. Additionally, ModelArts did not show the file uploading progress or speed.

ModelArts has been optimized for better file uploading experience. It not only provides more file upload functions, but also displays more file upload details.

Optimized file uploading:

-  Supports local files.
-  Supports cloning files from open-source repositories in GitHub.
-  Supports OBS files.
-  Supports remote files.
-  Supports visualized upload progress.
