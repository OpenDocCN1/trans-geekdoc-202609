```
In [25]:
from skimage.io import imread

test_path = osp.join(objcat_path, 'accordion', 'image_0001.jpg')
test_img = imread(test_path)

fig, ax = plt.subplots(1,1,figsize=(2,2))
ax.imshow(test_img)
ax.axis('off');
```

![](bbox=[0.4, 0.32, 0.6, 0.48])

It’s probably a reasonable guess that without some preprocessing—feature extraction—we have little hope of classifying these images correctly.

# 14.3.3 An End-to-End System

For our learning problem, we have a basket of images and a category they come from. Our strategy to make an end-to-end learning system is shown in Figures 14.1 and 14.2. Here are the major steps:

+   1. Describe each image in terms of its own, local visual words.
+   2. Group those local words into their respective synonyms. The synonyms will form our global visual vocabulary.
+   3. Translate each local visual word into a global visual word.
+   4. Replace the list of global visual words with the counts of the global words. This gives us a BoGVW—bag of (global visual) words (or simply BoVW, for bag of visual words).
+   5. Learn the relationship between the BoGVW and the target categories.

When we want to predict a new test image, we will:

+   1. Convert the test image to its own local words.
+   2. Translate the local words to global words.
+   3. Create the BoGVW for the test image.
+   4. Predict with the BoGVW.

The prediction process for a new test image relies on two components from the trained learning system: the translator we built in step 2 and the learning model we built in step 5.