
Now, if we have a look at the Figure 6, we can see an obvious pattern. The first clear observation we can make from the graph is that the real score is always greater than the fake scores and it confirms that the model of the GANs is working just fine. The second important observation is that, from the 20th to 28th epoch, the real scores are mostly in the higher regions and the fake scores are in the lower regions. This shows that training of minimum 20 and maximum 28 epoch will give the best possible optimal results. Now the CycleGANs of stage II comes into play. As discussed, this GAN is designed for mapping one image to another image, or image-to-image translations. If two images of animated characters with different artstyles are subjected to the Image-Image translation process, we can find a mapping function that can transform the first image into the second image and vice versa by adding or removing features in accordance with the mapping function, so that the predicted output and actual output have the lowest overall degree of loss. In our model, the adversarial discriminators DX and DY are CNNs that can see an image and attempt to categorize it as real or phony. Authentic photos have an output close to 1, whereas bogus classifications have an output near to 0. DY promotes and categorizes the transformation from domain X to domain Y. (making photos into Monet pictures). DX denotes transformation classification from domain Y to domain X.

Figure 6. Epochs vs. scores

![](img/4a898a1f1442f24bfffba36e7ac62ad8_276_0.png)

Here, in Figure 7, are some of the output sample of unique anime faces generated at the first stage of the hybrid GANs model.

We begin by writing a helper function that generates a convolutional layer with batch or instance normalisation. Batch normalisation was previously expected to help deep learning models by eliminating the “internal covariate shift”. The fundamental benefit of utilizing batch normalisation, however, is an improvement in the smoothness of the optimization landscape.

Figure 7. Generated images after 30 epochs of training. As we can see the contrast is not that balanced, so while choosing the parameter, we must be very careful. We can stop at 27th or 28th epoch to achieve better results.

![](img/4a898a1f1442f24bfffba36e7ac62ad8_277_0.png)

G XtoY and G YtoX are our two generators. They are made of the following:

- 1. Encoder (compressing the image into a smaller feature representation),
- 2. Residual blocks (which connect the output of one layer to the input of a previous layer) and
- 3. Decoder (converting compressed representation into a modified image)

As previously stated, we have two discriminator losses. The mean squared error between the output of the corresponding discriminator and the target value will be the loss for both functions (either 1 or 0). This is accomplished in the code by using real_mse_loss and fake_mse_loss.

- **Loss of Cycle Consistency:** Forward cycle consistency from X->Y->X. Loss of backward cycle consistency from Y->X->Y.
- **Loss of Identity:** Backward identity loss from Y->X. Forward identity loss from X->Y.

Now, in the training part, we trained the CycleGANs model for a total of 260 epochs to yield optimal results as CycleGANs is quite new to the domain of image-to-image and style transfer, so a large number of epochs are required. Some ranges of the epochs are mentioned in Table 2. After training 10 epochs, we found the following results as shown in Figure 8.

## Generating Complex Animated Characters of Various Art Styles

Figure 8. Training result of 10 epochs

![](img/4a898a1f1442f24bfffba36e7ac62ad8_279_0.png)

Fake Y (Monet-esque)

![](img/4a898a1f1442f24bfffba36e7ac62ad8_279_1.png)

However, if we refer the above graphs in Figures 10 and 11, we can see that the majority of losses occur till the training of 45 epochs in both generator and discriminator for both the translations. For the most optimal training results, we should limit the number of epochs to 200 in both the cases. As we can see in the graph, the region of the graph just before and after 200 is almost a straight line for the discriminator, so the losses there are uniform and steady and as a result, yield the most optimal images. So, if we put everything together, the result can be displayed as shown in Figure 12 below. As we can see, the starting set of images are of high quality and solid colors, which when mapped with the outdated blur anime photos, they yield a blurred and mixed color version photo of the previous ones. For example, we can see that the hair color of the first character has changed its shade from before to a very light brown one, the 5th character got some extra shadow details to the lower bangs of his hairline.

Although the changes are not that major, these small changes will pave the way for bigger and better changes in the future. However, when the opposite was tried, that is, converting the blurred photos to the high resolution ones, we got the results in Figure 13.

As seen in Figure 13, we can again observe some key and minor changes such as change of eye color, change in hair lines and hair color and an increase in resolution and clarity of the images. As observed and expected, the adversarial losses led to a huge amount of identity and resolution loss. The identity loss is inevitable as GANs are still in development and being continuously researched on. However, the resolution loss can be recovered to a certain extent by implementing the SRGANs in the final and IIIrd stage.

## Generating Complex Animated Characters of Various Art Styles

Figure 11. Generator and discriminator loss functions graph for AnimeFacesX -> AnimeFacesY

![](img/4a898a1f1442f24bfffba36e7ac62ad8_281_0.png)

Figure 12. AnimeFacesY -> AnimeFacesX

![](img/4a898a1f1442f24bfffba36e7ac62ad8_281_1.png)

Figure 13. AnimeFacesX -> AnimeFacesY

![](img/4a898a1f1442f24bfffba36e7ac62ad8_281_2.png)

Goodfellow, I. J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A. C., & Bengio, Y. (2014). Generative adversarial nets. NIPS.

Granqvist, P., Mikulincer, M., & Shaver, P. R. (2009). Religion as Attachment: Normative Processes and Individual Differences. Personality and Social Psychology Review, 14(1), 49–59. doi:10.1177/1088868309348618 PMID:20023208

Gregor, K., Danihelka, I., Graves, A., & Wierstra, D. (2015). Draw: A recurrent neural network for image generation. arXiv preprint arXiv:1502.04623.

Hays, J., & Efros, A. A. (2007). Scene completion using millions of photographs. ACM Transactions on Graphics, 26(3), 4. doi:10.1145/1276377.1276382

Hazan, C., & Shaver, P. (1987). Romantic Love Conceptualized as an Attachment Process. Journal of Personality and Social Psychology, 52(3), 511–524. doi:10.1037/0022-3514.52.3.511 PMID:3572722

Huang, Q.-X., & Guibas, L. (2013). Consistent shape maps via semidefinite programming. Symposium on Geometry Processing.

Kalal, Z., Mikolajczyk, K., & Matas, J. (2010). Forwardbackward error: Automatic detection of tracking failures. ICPR.

Kannadasan, R., Prabakaran, N., Boominathan, P., Krishnamoorthy, A., Naresh, K., & Sivashanmugam, G. (2018). High performance parallel computing with cloud technologies. Procedia Computer Science, 132, 518–524. doi:10.1016/j.procs.2018.05.004

Kingma, D. P., & Ba, J. L. (2014). Adam: A method for stochastic optimization. arXiv preprint arXiv:1412.6980.

Mordvintsev, A., Olah, C., & Tyka, M. (n.d.). Inceptionism: Going deeper into neural networks. https://googleresearch.blogspot.com/2015/06/inceptionism-going-deeper-into-neural.html

Portilla, J., & Simoncelli, E. P. (2000). A parametric texture model based on joint statistics of complex wavelet coefficients. International Journal of Computer Vision, 40(1), 49–70. doi:10.1023/A:1026553619983

Prabakaran, N., & Kannan, R. J. (2017). Sustainable life-span of WSN nodes using participatory devices in pervasive environment. Microsystem Technologies, 23(3), 651–657. doi:10.100700542-016-3117-7

Prabakaran, N., Kumar, S.S.S., Kiran, P.K., & Supriya, P. (2022). A deep learning based social distance analyzer with person detection and Tracking Using Region based convolutional neural networks for novel coronavirus. Journal of Mobile Multimedia, 541-560.

Prabakaran, N., Palaniappan, R., Kannadasan, R., Dudi, S. V., & Sasidhar, V. (2021). Forecasting the momentum using customised loss function for financial series. International Journal of Intelligent Computing and Cybernetics, 14(4), 702–713. doi:10.1108/IJICC-05-2021-0098

Radford, A., Metz, L., & Chintala, S. (2015). Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks. https://doi.org/arXiv.1511.06434 doi:10.48550

Rasmus, A., Valpola, H., Honkala, M., Berglund, M., & Raiko, T. (2015). Semisupervised learning with ladder network. arXiv preprint arXiv:1507.02672.
