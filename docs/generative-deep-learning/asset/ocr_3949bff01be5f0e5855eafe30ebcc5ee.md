![](bbox=[0.17, 0.08, 0.25, 0.16])

# Training Your Own StyleGAN2

The official code for training your own StyleGAN using TensorFlow is available on GitHub. Bear in mind that training a StyleGAN2 to achieve the results from the paper requires a significant amount of computing power.

# Weight Modulation and Demodulation

The artifact problem is solved by removing the AdaIN layers in the generator and replacing them with weight modulation and demodulation steps, as shown in Figure 10-11. w represents the weights of the convolutional layer, which are directly updated by the modulation and demodulation steps in StyleGAN2 at runtime. In comparison, the AdaIN layers of StyleGAN operate on the image tensor as it flows through the network.

The AdaIN layer in StyleGAN is simply an instance normalization followed by style modulation (scaling and bias). The idea in StyleGAN2 is to apply style modulation and normalization (demodulation) directly to the weights of the convolutional layers at runtime, rather than the output from the convolutional layers, as shown in Figure 10-11. The authors show how this removes the artifact issue while retaining control of the image style.

![](bbox=[0.18, 0.47, 0.87, 0.84])

Figure 10-11. A comparison between the StyleGAN and StyleGAN2 style blocks