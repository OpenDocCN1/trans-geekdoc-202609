
neonatal_mri.npz, which contains compressed numpy arrays with this data. Before we can start on this example, we have to make sure that we have access to GPU.

## 11.3.1 Accessing GPU

### Your local GPU card

If you have an NVIDIA GPU with at least 4 GB memory and CUDA installed, you can implement the example in this section locally on your computer. If you do not have these resources, you can use Google Colab.

To check whether CUDA is available, run the following code:

```
torch.cuda.is_available()
>>> True
```

If the answer is true, PyTorch is able to access your GPU. You can also check properties of your GPU as follows:

```
print(torch.cuda.get_device_properties('cuda:0'))
>>> CudaProperties(name='Quadro M2000',
major=5, minor=2, total_memory=4096MB,
multi_processor_count=6)
```

We can see that the GPU used has 4096 MB of memory, which is approximately 4 GB.

### Google Colab

Google Colab offers limited access to GPU free of charge, and this resource is ample for implementing the example in this section. To use Google Colab, you will need a google account. Once you are signed in go to

colab.research.google.com

You will see a screen where you have several options, including existing notebooks. If you already created your notebook, click on upload and drag the file there. Alternatively, if you plan to type code into a new notebook, click New notebook. You can change the name of this notebook by clicking on it in the top corner. By default Google Colab runs on CPU. To access the GPU, click Runtime -> Hardware Accelerator dropdown menu and choose GPU.

Finally you need to upload the data. To do that, type the following code to an empty cell and run it (by clicking the arrow):

github.com/MachineLearning/Applications/notebooks

from google.colab import files
files.upload()
```

After a while, a button will appear called Files. Click on this button and upload the file neonatal_mri.npz. It will take a minute or so for the file to upload. Now you are ready to proceed with the code given in the rest of this chapter. To add a new cell to your notebook, click +Code if you would like to write code, or +Text if you would like to write comments.

## 11.3.2 Load and prepare the data

### Load the data

First we use numpy package to load the compressed data:

```python
import numpy as np
data = np.load('neonatal_mri.npz')
data.files
>>> ['MR_images', 'prematurity']
```

We see that the file contains two arrays named 'MR_images' and 'prematurity'. We will now extract these arrays. The first array contains 157 MR images with 1 channel (grayscale) and size 64×64.

```python
mri = data['MR_images']
print(mri.shape)
>>> (157, 1, 64, 64)
```

The second array contains maturity status, a binary label where 1 means 'preterm' and 0 means 'term'.

```python
prem = data['prematurity']
print(prem.shape)
>>> (157,)
```

We also find that 41% preterm babies in the data set:

```python
np.round(np.sum(prem)/np.size(prem), 2)
>>> 0.41
```

### Plot the data

We will now plot the first 8 images with maturity status in the titles. The plot resulting from the code below is presented in Fig. 11.7.

```python
from matplotlib import pyplot as plt
plt.figure(figsize=(12,6))

for i in range(8):
    plt.subplot(2,4,i+1)
    plt.imshow(mri[i,0:], cmap='gray')
    if prem[i]:
        plt.title('Preterm')
    else:
        plt.title('Term')
    plt.axis('off')
```

![](img/d2194c20ff50f4b97845dec7aacecb_266_0.png)

Figure 11.7 Example images from neonatal MRI dataset.

### Convert to Pytorch tensors

Note that data has been already prepared in the shapes required by Pytorch. We still need to convert it to Pytorch tensors of a correct type, namely `float` for the images and `long` for the labels:

```python
import torch
X = torch.tensor(mri).float()
y = torch.tensor(prem).long()
```

### Training, validation and test sets

Next, we need to split the data for training, validation and testing. We will remove 20% of the data for testing, and another 10% for validation. We will perform stratified split to ensure there is the same proportion of preterm babies in all sets:

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = \
    train_test_split(X, y, test_size=0.2, stratify=y)
X_train, X_val, y_train, y_val = \
    train_test_split(X_train, y_train, test_size=0.1, stratify=y_train)
print('Training samples:', y_train.size())
print('Validation samples:', y_val.size())
print('Test samples:', y_test.size())
>>> Training samples: torch.Size([112])
>>> Validation samples: torch.Size([13])
>>> Test samples: torch.Size([32])
```

We have 112 samples for training, 13 for validation and 32 for testing. We are ready to implement and train our CNN.

## 11.3.3 CNN classifier

### Model architecture

The network architecture will be similar to the one that we have seen in Sect. 11.2, with some small differences. We will have three convolutional blocks, and one fully connected blocks. These will be implemented as follows:

- conv_block1: 2D convolutional layer with 8 filters and kernel size 3, followed by batch-norm, ReLU and max-pooling
- conv_block2: 2D convolutional layer with 16 filters and kernel size 3, followed by batch-norm, ReLU and max-pooling
- conv_block3: 2D convolutional layer with 32 filters and kernel size 3, followed by batch-norm, ReLU and max-pooling
- fc: fully connected layer

```python
import torch
import torch.nn as nn
import torch.optim as optim

class CNNclf(nn.Module):
    def __init__(self):
        super(CNNclf, self).__init__()
        self.conv_block1 = nn.Sequential(
            nn.Conv2d(1, 8, 3, padding=1),
            nn.BatchNorm2d(8),
            nn.ReLU(),
            nn.MaxPool2d(2)
        )
        self.conv_block2 = nn.Sequential(
            nn.Conv2d(8, 16, 3, padding=1),
            nn.BatchNorm2d(16),
            nn.ReLU(),
            nn.MaxPool2d(2)
        )
        self.conv_block3 = nn.Sequential(
            nn.Conv2d(16, 32, 3, padding=1),
            nn.BatchNorm2d(32),
            nn.ReLU(),
            nn.MaxPool2d(2)
        )
        self.fc_block = nn.Sequential(
            nn.Flatten(),
            nn.Linear(32 * 8 * 8, 2)
        )

    def forward(self, x):
        x = self.conv_block1(x)
        x = self.conv_block2(x)
        x = self.conv_block3(x)
        x = self.fc_block(x)
        return x
```

### Set up the model on CUDA device

We by setting up our cuda device:

```python
if torch.cuda.is_available():
    device = torch.device("cuda")
else:
    device = torch.device("cpu")
print(device)
>>> cuda
```

Next, we create an instance of the CNN classifier and send it to the GPU:

```python
net = CNNclf().to(device)
```

We are building a CNN classifier, so we choose a cross-entropy loss, which we also send to GPU, with:

```python
loss = nn.CrossEntropyLoss().to(device)
```

Finally, we also create the optimizer. It is important to send the model to GPU before creating the optimizer:

```python
optimizer = optim.SGD(net.parameters(), lr=0.001, momentum=0.5)
```

## 11.3.4 Training

Now we are ready to start training. We will train for a maximum 2,000 epochs (iterations). We choose to start training after 100 epochs has passed (to let network find an initial solution) and until the validation stops decreasing.

Note that we are using all data for training every iteration, each iteration is an epoch. This is generally not possible with larger data sets, and training is performed with mini-batches as we will show in the next section.

Note that training and validation data need to be sent to GPU before performing a forward pass. We save both training and validation losses to plot the training finished. We also print these losses every 100 iterations to be able to monitor the training. Here is how we implement this in Pytorch:

```python
epochs = 2000
train_losses=[]
val_losses=[]

for epoch in range(epochs):

    # training mode
    net.train()
    # send training data to GPU
    data = X_train.to(device)
    labels = y_train.to(device)
    # training
    optimizer.zero_grad()
    pred = net(data)
    ce = loss(pred, labels)
    ce.backward()
    optimizer.step()
    train_losses.append(ce.item())
```
