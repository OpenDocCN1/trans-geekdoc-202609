
# Machine Learning

## Chapter 3: Training the Image Classifier

Here's what happened on my Mac: With 10 iterations, training completed after 2 minutes, 38 seconds — only 9 seconds less than 25 iterations! But accuracy values are much lower:

![](img/5720be5c3cca252e12448e68d25607b5_109_0.png)

![](img/5720be5c3cca252e12448e68d25607b5_109_1.png)

Training accuracy (92%) decreased more than validation accuracy (89%), but the two values are closer (3%).

Now see what happens when you use the snacks/val subdirectory, which has about 50 images per class, instead of letting ML take 5% at random.

Add a third Model Source, and rename it to Multisnacks manual val. This is a good time to rename the other two to Multisnacks 25 iter and Multisnacks 10 iter.

**In Multisnacks manual val, choose train for Training Data, then select snacks/val for Validation Data:**

![](img/5720be5c3cca252e12448e68d25607b5_109_2.png)

Set Max iterations at 25, and click Train.

![](img/5720be5c3cca252e12448e68d25607b5_109_3.png)

## Here’s what I got:

![](img/5720be5c3cca252e12448e68d25607b5_110_0.png)

This is with 955 validation images, 240 training images. And this time the training used a lot more, 4,838 training images. But validation accuracy actually got worse, indicating the model may be **overfitting.**

## Overfitting happens

Overfitting is a term you learn in machine learning. It means that the model has started to remember *specific* training images. For example, the image train/cream/b0ff2ec6c49c78.jpg has a person in a blue shirt enjoying a sundae:

![](img/5720be5c3cca252e12448e68d25607b5_111_0.png)

### Yummy!

Suppose a classifier learns a rule that says, "If there is a blue blob in the image, then the class is ice cream." That's obviously not what you want the model to learn, as the blue shirt does not anything to do with ice cream in general. It just happens to work for this particular image. This is why you use a validation set of images that are not used for training. Since the model has never seen these before, it hasn't learned anything about them, making this a good test of how well the trained model can generalize to new images.

The accuracy of this particular model is 92% (validation accuracy), 98% (training accuracy). If you only look at the training accuracy, your estimate of the model's accuracy can be too optimistic. Ideally, you want the validation accuracy to be similar to the training accuracy, as it was after 10 iterations — that means your model is doing a good job. Typically, validation accuracy is a bit lower, but if the gap between them is too big, it means the model has learned too many irrelevant details from the training set — in effect, memorizing the specific images. Overfitting is one of the most prevalent issues with deep learning models.

There are several ways to deal with overfitting. The best strategy is to train with more data. Unfortunately, for this book we can't really make you a 100GB dataset, so we've decided to do with a relatively small dataset. For image classifiers, we can augment your image data by flipping, rotating or changing the exposure of images. Here's an illustration of data augmentation:

![](img/5720be5c3cca252e12448e68d25607b5_112_0.png)

So try it: add a new **Model Source**, name it Multisnacks crop, set the options before, but also select some data augmentation:

| Augmentations | Augment Data |
| :--- | :--- |
| Add Noise | |
| Blur | |
| [x] Crop | |
| Exposure | |
| Rotate | |

The augmentation options appear in alphabetical order, but the window lists them from greatest to least effectiveness, with Crop the most effective choice:

![](img/5720be5c3cca252e12448e68d25607b5_113_0.png)

This is also the order in which the classifier applies options, if you select more than one. Selecting Crop creates four images for each original image, so feature extraction takes five times longer (14m 48s for example). Selecting all augmentation options creates 100 augmented images for each original! Actually, the number of augmentation images is capped at 100. Click Train, then go brew a pot of tea or bake some cookies. Back again? Here's what I got:

| Input | Metrics | Output |
| :--- | :--- | :--- |
| 20 Classes | 97% Training | 91% Testing 32 KB |

![](img/5720be5c3cca252e12448e68d25607b5_113_1.png)

| Class | Item Count | Precision | Recall |
| :--- | :--- | :--- | :--- |
| apple | 1250 | 90% | 97% |
| banana | 1250 | 88% | 97% |
| cake | 1245 | 91% | 97% |

Training completed after 14 minutes, 48 seconds — today at 11/14

![](img/5720be5c3cca252e12448e68d25607b5_113_2.png)

Well, training accuracy is a little lower (97%), but so is validation accuracy (91%), by the same amount. So it's still overfitting, but it's also taking longer to learn — that’s understandable, with almost 25,000 images!

The takeaway is that training accuracy is a useful metric, but it only says about whether the model is still learning things, not how well the model works in practice. A good score on the training images isn't really interesting, since you already know what their classes are, after all.

What you care about is how the model works on images that it has never seen before. Then, the metric to keep your eye on is the validation accuracy, as this is a good indicator of the performance of the model in the real world.

> Note: Overfitting isn't the reason why validation accuracy can be lower than the training accuracy. If your training images are different from your validation images in some fundamental way (silly example: all your training images are photos taken at night while the validation images are taken during the day), your model obviously won't get a good validation score. It doesn't really matter where your validation images come from, as long as images were not used for training but they contain the same kinds of objects. This is why Create ML randomly picks 5% of the training images for use. You'll take a closer look at overfitting and the difference between training and validation accuracies in the next chapters.

## More metrics and the testing set

Now that you've trained the model, it's good to know how well it does on new images that it has never seen before. You already got a little taste of that from the validation accuracy during training, but the dataset also comes with a collection of test images that you haven't used yet. These are stored in the snacks/test folder, and organized by class name, just like the training data.

Switch to the Model Source with the highest Validation accuracy — in my case, it’s the first 25 iter, with 94% validation accuracy.

Select the Testing tab, then select snacks/test:

| Input | Metrics |
| :--- | :--- | :--- |
| Multisnacks | 20 100% | 94% |
| Choose | Training | Version |
| Model Sources | | |
| Multisnacks 25 iter | Data Inputs | |
| Multisnacks 10 iter | Testing Data 952 Items | |
| Multisnacks: val | test | |

Click Test Model: This takes a few moments to compute. Just like during training, the feature extraction on the images takes more time than classification.

| Input | Metrics | Output |
| :--- | :--- | :--- |
| 20 100% | 94% | 88% | 312 KB |
| Class Training Validation | | |
| Data Inputs | Testing Data 952 Items test Test Model | |
| Metrics | | Item Count Precision Result |
| :--- | :--- | :--- | :--- |
| apple | 50 | 83% | 86% |
| banana | 50 | 89% | 96% |
| case | 50 | 68% | 82% |
