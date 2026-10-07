# Machine Learning

# Chapter 3: Training the Image Classifier

The augmentation options appear in alphabetical order, but the pre-Xcode-11 options window lists them from greatest to least training effectiveness, with Crop the most effective choice:

![](bbox=[0.366, 0.191, 0.632, 0.396])

This is also the order in which the classifier applies options, if you select more than one. Selecting Crop creates four flipped images for each original image, so feature extraction takes five times longer (14m 48s for we). Selecting all augmentation options creates 100 augmented images for each original! Actually, "only 100," because the number of augmentation images is capped at 100.

Click Train, then go brew a pot of tea or bake some cookies.

Back again? Here's what I got:

| Input | Metrics | | Output |
|---|---|---|---|
| 20 Classes | 97% Training | 91% Testing | 312 KB |

![](bbox=[0.266, 0.636, 0.732, 0.806])

| Class | Item Count | Precision | Recall |
|---|---|---|---|
| apple | 1250 | 90% | 97% |
| banana | 1250 | 88% | 97% |
| cake | 1245 | 91% | 97% |
| Training completed after 14 minutes, 48 seconds — today at 11/14

![](bbox=[0.161, 0.921, 0.341, 0.951])

114