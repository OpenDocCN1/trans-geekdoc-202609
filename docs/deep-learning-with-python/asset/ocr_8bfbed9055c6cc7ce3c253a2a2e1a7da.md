![](bbox=[0.17, 0.08, 0.86, 0.38])

Figure 8.8 Samples from the Dogs vs. Cats dataset. Sizes weren't modified: the samples come in different sizes, colors, backgrounds, etc.

a validation set with 500 samples of each class, and a test set with 1,000 samples of each class. Why do this? Because many of the image datasets you'll encounter in your career only contain a few thousand samples, not tens of thousands. Having more data available would make the problem easier, so it's good practice to learn with a small dataset.

The subsampled dataset we will work with will have the following directory structure:

```
cats_vs_dogs_small/
...train/
...cat/ ... Contains 1,000 cat images
...dog/ ... Contains 1,000 dog images
...validation/
...cat/ ... Contains 500 cat images
...dog/ ... Contains 500 dog images
...test/
...cat/ ... Contains 1,000 cat images
...dog/ ... Contains 1,000 dog images
```

Let's make it happen in a couple calls to shutil.

# Listing 8.6 Copying images to training, validation, and test directories

```
import os, shutil, pathlib
original_dir = pathlib.Path("train")
new_base_dir = pathlib.Path("cats_vs_dogs_small")
```