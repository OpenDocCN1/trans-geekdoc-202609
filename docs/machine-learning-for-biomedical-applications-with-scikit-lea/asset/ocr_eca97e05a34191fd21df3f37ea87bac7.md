16 segmentations with size $16 \times 256 \times 256$. Segmentations do not have the dimension since the cross-entropy loss function requires labels to be coded by integers of type long, with no channels needed. Similarly, the object data\_train\_loader contains 20 batches of data with size 16, and the test object data\_test\_loader contains 3 batches. You can verify that by changing the data loader object in the for loop.

# 11.4.3 Training the segmentation model

Now, we are ready to train our model. In fact, training a UNet segmentation network is not any different from training a classifier in Sect. 11.3, except that we need to incorporate data loaders into the training loop to be able to train in batches.

# Create the UNet model and the loss

We start us by creating the GPU device for fast training with

```
if torch.cuda.is_available():
    device = torch.device("cuda")
else:
    device = torch.device("cpu")
print(device)
>>> cuda
```

Next, we create the instance of a UNet network and the cross-entropy loss. Both are sent to the GPU with

```
net = UNet().to(device)
loss = nn.CrossEntropyLoss().to(device)
```

# Optimizer

We could use a standard Stochastic Gradient Descent (SGD) optimizer as usual, however this time we will choose the Adam optimizer [25]. The Adam (Adaptive Moment Estimation) optimizer takes advantage of second-order information to improve convergence and speed up training. In our example we can observe significant improvement compared to SGD. To create the Adam optimizer, we call the PyTorch object torch.optim.Adam and set learning rate to 0.005

```
import torch.optim as optim
optimizer = optim.Adam(net.parameters(), lr=0.005)
```

# Training

The training loop is very similar to what we implemented in Sect. 11.3.4. The training loop over the epochs now also contains an inner loop over the batches of the training and validation data loaders: