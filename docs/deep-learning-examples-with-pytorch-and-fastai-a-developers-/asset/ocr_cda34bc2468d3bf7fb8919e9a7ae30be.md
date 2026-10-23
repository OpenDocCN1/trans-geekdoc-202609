pet/images/Siamese_175.jpg']

If we have a look at the filenames, we see that the name contains the label that we want to predict later. E.g. /home/bmayr/.fastai/data/oxford-iiit-pet/images/Birman_105.jpg - this is the image of a Birman cat.

With fastai we have different options on how to get the labels for our training data. We can either extract the label from a parent folder path, from a csv-file or data frame or we use a regular expression to extract the label from the path.

So let’s grab all characters after the last / to the _: '(.*)_\d+.jpg$'

If you are not familiar with regular expressions – don’t be afraid, you are not alone. There are plenty of good tutorials on the web and you will find examples for nearly all possible applications on stack overflow. To test your regEx you can use one of the many online-editors that show which portion of a string matches your regular expression. E.g. regex101.com: (https://regex101.com/)

```
pat = r'(.*)_\d+.jpg$'
```

Next we want to add some basic transforms. Batch-transforms are applied to each batch on your training data whereas item_transforms will be applied to any of your items before adding them to different batches.

Transforms are an excellent way of augmenting your training data. E.g. you can zoom in or out a bit, flip your images, warp, etc. to generate even more training examples. Fastai implements data augmentation in a very fast way by doing image data augmentation in parallel on your GPU.

In this example we want to resize our images to 224x224 pixels and normalize on the imagenet_stats because we will use ResNet34 as a base model for transfer learning.

Each image will be randomly cropped before being added to a batch.

The batch size will be 64 – you can adjust the value according to your