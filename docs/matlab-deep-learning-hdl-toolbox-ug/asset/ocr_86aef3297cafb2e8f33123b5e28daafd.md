![](bbox=[0.185, 0.133, 0.772, 0.513])

Use the helper function helperCreateRGBfromTF to create the scalograms as RGB images and write them to the appropriate subdirectory in dataDir. The source code for this helper function is in the Supporting Functions at the end of this example. To be compatible with the GoogLeNet architecture, each RGB image is an array of size 224-by-224-by3.

helperCreateRGBfromTF(ECListData,parentDir,dataDir)...

# Divide into Training and Validation Data

Load the scalogram as an image datastore. The imageDatastore function automatically labels the images by folder names and stores the data as an imageDatastore object. An image datastore enables you to store large image, including data that does not fit in memory, and efficiently reads batches of images during training of a CNN.

```
allImages = imageDatastore(fullfile(parentDir,dataDir),..
    'IncludeSubfolders',true,
    'LabelSource','foldernames');
```

Randomly divide the images into two groups, one for training and the other for validation. Use 80% of the images for training, and the remainder for validation. For purposes reproducibility, we set the random seed to the default value.

```
rng default
[imgsTrain,imgsValidation] = splitEachLabel(allImages,0.8,'randomized');
disp(['Number of training images: ',num2str(numel(imgsTrain.Files))
```

Number of training images: 130