3. Modify the code to perform multi-label segmentation of 5 classes: background (0), CSF (1), cortex (2), white matter (4). To obtain the labels, you can process the segmentations in the NeonatalDataset object with

```
seg = np.round(labels/62.5,0)
```

Note that you also need to change the number of outputs of the UNet object to five. Evaluation also needs to be performed for each label sample. For details of how to evaluate performance of multi-label segmentation, see Sect. 4.1.5. Hint: You will need to increase the number of feature maps in the lowest-level encoder convolution and the decoder convolutions.

# 11.5. Conclusion

Congratulations! You have just trained and evaluated your first advanced neural network for image segmentation. And this is where the learning objectives of this book have been fully achieved. Of course, there is so much to learn: Machine learning and deep learning, in particular, are very fast evolving fields, with new ideas, algorithms and concepts being generated every year. There are many more architectures to learn, such as attention mechanisms, visual transformers and generative adversarial networks, which are all widely used in biomedical applications. We hope that the strong foundation that you gained while studying the material in this book will motivate you to confidently explore these advanced concepts. And, as importantly, we hope that you enjoyed learning with us!