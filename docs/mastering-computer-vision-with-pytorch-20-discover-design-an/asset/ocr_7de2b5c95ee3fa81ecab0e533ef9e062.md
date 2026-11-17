![](bbox=[0.26, 0.08, 0.73, 0.46])

**Figure 7.12:** Confusion Matrix of the model trained from scratch

# # Comparison Pre-trained vs. Scratch

If we look at the output of the training, we can see that in the first epoch itself, the difference in loss is very high, 0.77 for the model started from pre-trained weights and 1.99 for the model started from scratch. Since the pre-trained model is already trained on the ImageNet dataset, it has learned all the low-level features and does not need to train for that. While in the case of training from scratch, the weights are initialized randomly so, the amount of training required is a lot higher.

Also, when we look at the accuracy, in 5 epochs, the pre-trained version was able to achieve 89% accuracy, while the model from scratch could only reach 69.63%. Another thing to note here is that compared to our SimpleCNN, these perform a lot better since they are very complex architectures proven to perform well on such image tasks.