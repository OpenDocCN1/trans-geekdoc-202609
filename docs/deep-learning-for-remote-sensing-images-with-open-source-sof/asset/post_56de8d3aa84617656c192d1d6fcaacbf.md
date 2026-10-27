
```python
nclasses=6

def myModel(x):

    # input patches: 16x16x4
    conv1 = tf.layers.conv2d(inputs=x, filters=16, kernel_size=[5,5],
                             padding="valid", activation=tf.nn.relu)
    # conv1 out size: 12x12x16
    pool1 = tf.layers.max_pooling2d(inputs=conv1, pool_size=[2, 2],
                                    strides=2)
    # pool1 out: 6x6x16
    conv2 = tf.layers.conv2d(inputs=pool1, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv2 out size: 4x4x16
    pool2 = tf.layers.max_pooling2d(inputs=conv2, pool_size=[2, 2],
                                    strides=2)
    # pool2 out: 2x2x16
    conv3 = tf.layers.conv2d(inputs=pool2, filters=32, kernel_size=[2,2],
                             padding="valid",activation=tf.nn.relu)
    # conv3 out: 1x1x32

    # Features
    features = tf.reshape(conv3, shape=[-1, 32], name="features")

    # Neurons for classes
    estimated = tf.layers.dense(inputs=features, units=nclasses,
        activation=None)
    estimated_label = tf.argmax(estimated, 1, name="prediction")

    return estimated, estimated_label

""" Main """
if len(sys.argv) != 2:
    print("Usage: output_directory_for_SavedModel")
    sys.exit(1)

# Create the TensorFlow graph
with tf.Graph().as_default():

    # Placeholders
    x = tf.placeholder(tf.float32, [None, None, None, 4], name="x")
    y = tf.placeholder(tf.int32, [None, None, None, 1], name="y")
    default_lr = tf.constant(0.0002, dtype=tf.float32, shape=[])
    lr = tf.placeholder_with_default(default_lr, shape=[], name="lr")

    # Output
    y_estimated, y_label = myModel(x)

    # Loss function
    cost = tf.losses.sparse_softmax_cross_entropy(labels=tf.reshape
        (y, [-1, 1]), logits=tf.reshape(y_estimated,
        [-1, nclasses]))
```

```python
# Optimizer
optimizer = tf.train.AdamOptimizer(learning_rate=lr,
    name="optimizer").minimize(cost)
```

```python
# Initializer, saver, session
init = tf.global_variables_initializer()
saver = tf.train.Saver( max_to_keep=20 )
sess = tf.Session()
sess.run(init)
```

```python
# Create a SavedModel
# Create a SavedModel
CreateSavedModel(sess=sess,
    inputs=["x:0", "y:0"],
    outputs=["features:0", "prediction:0"],
    directory=sys.argv[1])
```

**Important note**
The Python syntax is sensitive to indentation: you must preserve the same indentation for each line under a block (e.g. function). Be careful of indentations if you copy/paste or modify the provided codes. We recommend cloning the GitHub repository instead of using copy/paste.

To run the Python script, just type:

```
# Add otbtf python directory to PYTHONPATH
export PYTHONPATH=$PYTHONPATH:/work/otb/otb/Modules/Remote/otbtf/python/
```

```
# Generate the model (you might need to provide the correct path
# to the "create_model1.py" file if you have downloaded elsewhere)
# The "create_model1.py" file can be downloaded from:
# https://github.com/remicres/otbtf_tutorials_resources.git
python3 create_model1.py "model1"
```

Of course, you can change the model directory ("model1") if you want to write it elsewhere than the current directory.

## 5.5 Train the model from scratch

If you take a look at the SavedModel directory, you will see a .pb file (protobuf) and a Variables folder. The protobuf file serializes the computational graph, and the Variables folder contains the values of the model weights (kernels, etc.). As you could have noticed in the Python script, the model weights are initialized before exporting the SavedModel. We will use the TensorflowModelTrain application to train the CNN from its initialized state, updating its weights for the image classification task. For each dataset (training data and validation data), the validation step of the **Tensorflow-ModelTrain** application consists of computing the following metrics:

- Confusion matrix
- Overall accuracy index
- Kappa index
- For each class:
  - Precision
  - Recall
  - F-Score

Depending on the placeholder names of the sources used for training, and the names of the sources used for evaluation, the application to detect which source is used as input of the model, or as a baseline to compute evaluation metrics, is explained in figure 5.3.

![](img/f70619500c7a30b0babf83918d56ad93_50_0.png)

## FIGURE 5.3

Computation of classification metrics, performed separately on the training dataset and validation dataset.

The application parameters are the following:

- **training.source1** is the parameter group for the first source, i.e. image patches (for learning)
  - **training.source1.il** is the input image filename
  - **training.source1.patchsizex** is the patch width
  - **training.source1.patchsizey** is the patch height
  - **training.source1.placeholder** is the name of the placeholder for the image patches
- **training.source2** is the parameter group for the second source, i.e. label patches (for learning)
- **training.source2.il** is the input image filename
- **training.source2.patchsizex** is the label width
- **training.source2.patchsizey** is the label height
- **training.source2.placeholder** is the name of the placeholder for the label patches
- **model.dir** is the directory containing the TensorFlow *SavedModel*
- **training.targetnodes** is the name of the operator that computes the gradient descent in the training step. In our model, the gradient descent is performed with the adam optimizer called **“optimizer.”**
- **validation.mode** is the validation mode. The **“class”** validation mode enables the computation of classification metrics for both training data and validation data.
- **validation.source1** is the patch source (for validation). As the name of the source for validation (**validation.source1.name**) is the same as the placeholder name of the same source for training (**training.source1.placeholder**), this source is considered as an input of the model, and is fed to the corresponding placeholder during the validation step.
- **validation.source2** is the label source (for validation). As the name of the source (**validation.source2.name**) is different than the placeholder name of the same source for training (**training.source2.placeholder**), this source is considered as a reference to be compared to the output of the model that has the same tensor name during the validation step.
- **model.saveto** enables us to export the model variables (i.e. weights) to a file.

The command line corresponding to the above description is the following:

```bash
# Train the deep learning model
otbcli_TensorflowModelTrain \
-training.source1.il Sentinel-2_B4328_10m_patches_A.tif \
-training.source1.patchsizex 16 \
-training.source1.patchsizey 16 \
-training.source1.placeholder "x" \
-training.source2.il Sentinel-2_B4328_10m_labels_A.tif \
-training.source2.patchsizex 1 \
-training.source2.patchsizey 1 \
-training.source2.placeholder "y" \
-model.dir model1 \
-training.targetnodes "optimizer" \
-validation.mode "class" \
-validation.source1.il Sentinel-2_B4328_10m_patches_B.tif \
-validation.source1.name "x" \
-validation.source2.il Sentinel-2_B4328_10m_labels_B.tif \
-validation.source2.name "prediction" \
-model.saveto model1/variables/variables
```

As you can notice, the training.source1.placeholder and validation.source1.name are the same (“x”), and training.source2.placeholder and validation.source2.name are different (“y” versus “prediction”). This causes the placeholder x to be used for both training and validation, but the placeholder y is used only for training, and the placeholder prediction for validation, as explained in figure 5.3.

We could tune the learning rate (which has, as mentioned in the Python code, a default value of 0.0002) using the training.userplaceholders parameter:

```
...
-training.userplaceholders "lr=0.005" \
...
```

Run the TensorflowModelTrain application. After the epochs, note the kappa and overall accuracy indexes (should be, respectively, around 0.7 over the validation dataset). Browse the file system, and take a look in the data/results/model1/variables/ directory: you can notice that the application has updated two files:

- *model_variables_cnn.index* is a summary of the saved variables,
- *model_variables_cnn.data-00000-of-00001* is the saved variable number 1, saved at the end of the training process.

## 5.6 Comparison with Random Forest

Here, we compare our small deep net to a Random Forest (RF) classifier. We use the metrics deriving from the confusion matrix. We use the machine learning framework of OTB to train and evaluate the performance of the RF classifier. First, we use exactly the same samples as for the deep net training and validation, to extract the pixel values of the image:

```
# Extract the pixels values at samples locations (Learning data)
otbcli_SampleExtraction \
-in Sentinel-2_B4328_10m.tif \
-vec terrain_truth_epsg32654_A_pos.shp \
-field "class" \
-out terrain_truth_epsg32654_A_pixelvalues.shp
```

Then, we do the same with the terrain_truth_epsg32654_B_pos.shp vector data (validation data).

```
# Extract the pixels values at samples locations (Validation data)
otbcli_SampleExtraction \
-in Sentinel-2_B4328_10m.tif \
-vec terrain_truth_epsg32654_B_pos.shp \
-field "class" \
-out terrain_truth_epsg32654_B_pixelvalues.shp
```
