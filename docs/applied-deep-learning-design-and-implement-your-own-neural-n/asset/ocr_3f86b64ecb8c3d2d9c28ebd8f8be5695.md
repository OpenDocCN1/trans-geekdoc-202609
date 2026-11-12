Now, for simplification of the ConvNet, let us redraw the figure as shown in figure 5.15:

![](bbox=[0.13, 0.15, 0.85, 0.3])

# Figure 5.15: Simplification of the ConvNet

Now, suppose we have an image of size (16*16*3), and we want to detect objects in the input image using the sliding window technique.

For this, we have to create four separate windows of size (14*14*3) from the pixels of the test image and then execute each of the windows using ConvNet to detect the different objects in the test image:

![](bbox=[0.23, 0.48, 0.76, 0.85])

# Figure 5.16: Sliding window of 14*14*3 on test image of 16*16*3

Now, with each of the sliding window of size 14*14*3, we perform the ConvNet operation with the same number of filters and the same amount of operations used