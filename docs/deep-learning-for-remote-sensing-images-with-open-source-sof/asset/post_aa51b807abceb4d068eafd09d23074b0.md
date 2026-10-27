
```python
    conv7 = tf.layers.conv2d(inputs=conv6, filters=32, kernel_size=[2,2],
                         padding="valid", activation=tf.nn.relu)

    # conv7 out size: 1x1x32

    # Features
    features = tf.reshape(conv7, shape=[-1, 32], name="features")

    # Neurons for classes
    estimated = tf.layers.dense(inputs=features, units=nclasses,
                             activation=None)
    estimated_label = tf.argmax(estimated, 1, name="prediction")

    return estimated, estimated_label

""" Main """
if len(sys.argv) != 2:
    print("Usage: <output_directory_for_SavedModel>")
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
              (y, [-1, 1]), logits=tf.reshape(y_estimated, [-1, nclasses]))

    # Optimizer
    optimizer = tf.train.AdamOptimizer(learning_rate=lr,
              name="optimizer").minimize(cost)

    # Initializer, saver, session
    init = tf.global_variables_initializer()
    saver = tf.train.Saver( max_to_keep=20 )
    sess = tf.Session()
    sess.run(init)

    # Create a SavedModel
    CreateSavedModel(sess=sess,
                     inputs=["x:0", "y:0"],
                     outputs=["features:0", "prediction:0"],
                     directory=sys.argv[1])
```

Run the *create_model2.py* Python script from the terminal to generate the *SavedModel* of our new FCN architecture:

```bash
# Generate the model

# The "create_model2.py" file can be downloaded from:
# https://github.com/remicres/otbf_tutorials_resources.git
python3 ~/python/create_model2.py "model2"
```

As there is no stride in convolution, and stride in pooling, our new model has an output scale factor of 1 and can produce a classification map at the same scale as the input image!

### 6.3 Training

We can now train this new model over the same patches as for the simple CNN.

> **Important note**
>
> The proposed FCN has a lot more weight than the previously introduced CNN one. We can then expect that the gradient descent will take more time. It could be better to set a higher number of epochs!

To train the new model, just run:

```bash
# Train the deep learning model
otbcli_TensorflowModelTrain \
-training.source1.il Sentinel-2_B4328_10m-patches_A.tif \
-training.source1.patchsize 16 \
-training.source1.patchsizey 16 \
-training.source1.placeholder "x" \
-training.source2.il Sentinel-2_B4328_10m-labels_A.tif \
-training.source2.patchsize 1 \
-training.source2.patchsizey 1 \
-training.source2.placeholder "y" \
-model.dir model2 \
-training.targetnodes "optimizer" \
-validation.mode "class" \
-validation.source1.il Sentinel-2_B4328_10m_patches_B.tif \
-validation.source1.name "x" \
-validation.source2.il Sentinel-2_B4328_10m_labels_B.tif \
-validation.source2.name "prediction" \
-model.savetodisk model2/variables/variables
```

After 100 epochs, we can notice that the scores are great and that this FCN model outperforms the simple CNN. That might come from the fact that we have significantly increased the number of variables in the model (compared to our first CNN, we added 2 new convolution operators, and we also have enlarged all convolution kernels of the network).

### 6.4 Inference

We now want to produce the classification map over the entire image. We run the model over the image subset:

```text
otbcli_TensorflowModelServe \
--source1.il Sentinel-2_B4328_10m.tif \
--source1.rfieldx 16 \
--source1.rfieldy 16 \
--source1.placeholder "x" \
--model.dir model2 \
--model.fullyconv on \
--output.names "prediction" \
--out "classif_model2.tif?&box=4000:4000:1000:1000"
```

The map can be produced over the whole image. The **optim** parameter group of **TensorflowModelServe** enables us to adjust settings for the model execution to reach better performance. To speed up the process, you can force the application to produce the result using large tiles. In the following, we force the output tiles to large rectangular tiles of 128-pixel height, in order to reduce the computation from partially overlapping input areas.

```text
# Generate the landcover map over the entire image
otbcli_TensorflowModelServe \
--source1.il Sentinel-2_B4328_10m.tif \
--source1.rfieldx 16 \
--source1.rfieldy 16 \
--source1.placeholder "x" \
--model.dir model2 \
--model.fullyconv on \
--output.names "prediction" \
--optim.tilesizex 999999 \
--optim.tilesizey 128 \
--out classif_model2_full.tif uint8
```

The processing of the entire image lasts approximately **80 seconds** on an Intel(R) Xeon(R) CPU E5-1650 @ 3.20 GHz with 16 GB RAM. You can open the land cover map in QGIS.

> **Important note**
>
> You must have enough memory for processing large tiles. If there is not enough memory, TensorFlow will throw warning messages indicating that the efficiency of the computation is compromised. In this case, you can reduce the tile height, e.g. 64 instead of 128.

## Classifiers on deep features

Recent studies have pointed out that using the features computed with deep nets in machine learning algorithms like Support Vector Machines or Random Forests, offers state-of-the-art results [20, 21, 22]. This section provides insight into classification using classic Machine Learning techniques on deep learning features. Here, deep learning is used merely as feature engineering rather than a sole classifier.

### 7.1 Principle

We will use algorithms that are already implemented in the Orfeo ToolBox with features coming from our deep net. The whole workflow is summarized in figure 7.1.

![](img/f70619500c7a30b0babf83918d56ad93_63_0.png)

**FIGURE 7.1**  
Workflow for hybrid classification, mixing deep nets with random forest.

In section 5.3.2, we have described the model guts. In particular, before computing the classes pseudo-probability on the last neurons, our model computes a number of features, as shown on figure 7.2. This is done by reshaping the output of the last convolution operator to a vector of dimension 2: one dimension for the batch size, which is not fixed, the other for the components of the features, which is fixed (32 elements). In a TensorFlow model, once an operator has a name, it is possible to fetch its result during the inference.

Since the *tf.reshape* operator performing this is named **features**, it is possible to use the **TensorflowModelServe** application to produce the *features* for an entire image, using the same mechanisms as described in previous sessions.

![](img/f70619500c7a30b0babf83918d56ad93_64_0.png)

**FIGURE 7.2**

The model outputs the tensor named “*features*.” The output of the dense layer composed of 6 neurons is not used. Only “*features*” is computed using the net, and the classification is performed using another classifier.

This enables us to use the **TensorflowModelServe** to produce the *features* output tensor for pixels of the image, and the resulting pixels are then used as features for training a Random Forest (with the **TrainImagesClassifier** application). Once the RF rule is produced, it can be used to classify the entire image from the deep features computed on each pixel.

### 7.2 Overview of composite applications in OTB

In OTB, composite applications are multiple applications connected together. Typically, one application input can come from another application output, instead of being read from file. The major benefit is that temporary file read and write are avoided, which (i) saves some disk space, and (ii) helps in reducing processing time when I/O is a bottleneck. Presented in section 2.1.2, the streaming mechanism enables the processing of large images, in splitting the requested parts of the images into multiple regions. Composite applications that involve applications with streaming support, also benefit from this mechanism.

In OTBTF there are currently two composite applications.

- **TrainClassifierFromDeepFeatures**, which reuses our model serving application (**TensorflowModelServe**) as input of the *TrainImagesClassifier* to train a machine learning algorithm based on the features of the deep net given in the first application.
