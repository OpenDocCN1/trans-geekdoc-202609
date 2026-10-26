creased the variety of the training data set and the ability of the classifier to generalize on unseen samples. By intentionally increasing the quantity of samples for underrepresented classes, augmentation can alleviate class imbalance. By putting these strategies into practice, U-Net models can perform much better, while reducing the chance of overfitting.

![](bbox=[0.106, 0.214, 0.567, 0.658])

**Figure 4:** Training U-Net models efficiently.

# ### 3.3.2 Optimization of loss functions

For U-Net models to train effectively, loss function selection and optimization are essential. Common loss functions used in biomedical image segmentation are the Dice coefficient, the pixel-wise cross-entropy loss, and combination losses like Dice + cross-entropy. By concentrating on the overlap between the expected and ground truth masks, the Dice loss was especially helpful in addressing class disparities. It is often beneficial to use a combination of loss functions to balance segmentation accuracy