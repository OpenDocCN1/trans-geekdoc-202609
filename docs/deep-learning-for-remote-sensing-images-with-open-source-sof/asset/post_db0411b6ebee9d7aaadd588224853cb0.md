
Finally, we train an RF classifier with default parameters.

```bash
# Train a Random Forest classifier with validation
otbcli_TrainVectorClassifier \
-io.vd terrain_truth_epsg32654_A_pixelvalues.shp \
-valid.vd terrain_truth_epsg32654_B_pixelvalues.shp \
-feat "value_0" "value_1" "value_2" "value_3" \
-cfield "class" \
-classifier "rf" \
-io.out randomforest_model.yaml
```

Note the kappa index: it should be around 0.5, i.e. about 20% less than our CNN model.

> **Important note**
>
> The CNN uses more information for training, compared to the RF. Indeed, it learns on 16 × 16 patches of a multispectral image, whereas the RF learns only on multispectral pixels (that could be interpreted as 1 × 1 patches of multispectral image). Our goal here is not to compare RF vs CNN, but just to show that the contextual information processed by the CNN is useful in classification task. A more fair competitor could be an RF using spatial features like textures, local Fourier transforms, SIFTs, etc.

## 5.7 Inference

In section 5.3 we successfully trained our CNN model. Now we will apply the model over the Sentinel-2 image to produce a land cover map. The optimizer is not used anymore, we just employ the model with its fixed weights as updated after the training. This part is called the *inference*. To perform the inference, we use the **TensorflowModelServe** application. We know that our CNN input has a receptive field of 16 × 16 pixels and the placeholder name is **“x.”** The output of the model is the estimated class, which is the tensor result of the **Argmax** operator, named **“prediction.”** We don’t use the optimizer node anymore, as it is part of the training procedure: we use only the model subset that computes **“prediction”** from **“x”** as shown in *figure 5.4*.

Now import the generated image in QGIS, refer to figure 5.5. You can change the style of the raster: in the **layers panel** (left side of the window), right-click on the image, then select **Properties**, go to the **Symbology** tab and select **render type** as **single band pseudocolor**. Then, you can select the color for each class value, the annotations, etc. You can also load the predefined style by clicking on the **Style** button (bottom of the window) and opening the file named *legend-style.qml* stored in the *tokyo/terrain-truth* directory.

![](img/f70619500c7a30b0babf83918d56ad93_55_0.png)

**FIGURE 5.5**  
Import the output classification map in QGIS.

> **Important note**  
> We just have run the CNN in **patch-based** mode, meaning that the application extracts and processes patches independently at regular intervals. This is costly, because the sampling strategy requires that we duplicate a lot of overlapping patches and process them independently.

## 6 Fully Convolutional Neural Network

In the previous section, we performed pixel-wise classification using a deep convolutional neural network. We have performed the inference in patch-based mode, meaning that for each output pixel, we have run the model on one small patch of the input image, centered on the output pixel position. While this kind of network architecture is easy to implement, it is not efficient in terms of processing. Due to patch overlap, the data is copied multiple times with different memory alignment (for each different patch) and passed to the model. The costliest operations implemented in the deep net are the convolutions, which are massively parallel and can be implemented so that the intermediate results are reused for other patch processing (e.g. intermediate sums, see equations 1.2 and 1.3). However, the patch-based mode disables the possible reuse of the intermediate results since they are re-computed at each new patch, which is not efficient. We will introduce the Fully Convolutional Neural Networks (FCNN, or FCN) that are just CNNs that can process entire image regions instead of being limited to small patches.

### 6.1 Using the existing model as an FCN

From the constitution of the simple CNN we used in section 5.4, we can notice that this model can be used as an FCN. Its properties are summarized as the following:

- **receptive field** (16 × 16 pixels),
- **expression field** (1 × 1 pixel),
- **scale factor** (there is a total of 2 successive pooling operators of size 2, meaning that the scale factor is 2 × 2 = 4).

We can check that they are consistent with operators implemented in the model. If we let n be the size of the input image, we can see how the model propagates the image region to the output of size m:

1. convolution with 5 × 5 kernel: output size is n − 4,
2. 2× pooling with stride (2,2): output size is (n − 4)/2 = n/2 − 2,
3. convolution with 3×3 kernel: output size is (n/2 − 2) − 2 = n/2 − 4,
4. 2× pooling with stride (2,2): output size is (n/2 − 4)/2 = n/4 − 2,
5. convolution with 2×2 kernel: output size is (n/4 − 2) − 1 = n/4 − 3.

In conclusion, we have m = n/4 − 3, which is quite consistent with the properties (receptive field, expression field, spacing factor) of the model: the model produces an output of size 1 × 1 from an input image of size 16 × 16. The physical spacing of its output pixel is equal to the input pixel spacing multiplied by 4. Run the CNN model with the parameter `model.fullyconv` set to on in order to enable the fully convolutional processing.

```bash
otbcli_TensorflowModelServe \
-source1.il Sentinel-2_B4328_10m.tif \
-source1.rfieldx 16 \
-source1.rfieldy 16 \
-source1.placeholder "x" \
-model.dir model1 \
-model.fullyconv on \
-output.names "prediction" \
-output.spcscale 4 \
-out "classif_model1_fcn.tif?&box=1000:1000:250:250"
```

Open the resulting image in QGIS, and compare with the classification map created by the original CNN. Open the Properties > Metadata tab and check that the physical spacing of the new map is 4 times greater than the original.

### 6.2 Pixel-wise fully convolutional model

A fully convolutional network runs faster than patch-based, enough to process the full image in reasonable time (to test it, just remove the extended filename in the previous command). However, pooling completely destroys the resolution of the output (the output image spacing is 4 times greater than the input pixel spacing). We can modify our original model a bit to create a pixel-wise fully convolutional network which preserves the input image spacing.

We remove the pooling operators, and add some convolutional layers with unit strides. Our goal is to keep the same receptive field and expression field as the previously used architecture (this way, we can reuse our image patches that we have generated in section 5.2). Figure 6.1 summarizes our new architecture.

![](img/f70619500c7a30b0babf83918d56ad93_59_0.png)

**FIGURE 6.1**  
The new Fully Convolutional Neural Network. Pooling operators have been removed, and convolution operators have been added. Note that there is no stride in convolution, preserving the physical spacing in spatial dimensions.

Let’s implement our new FCN architecture. We will use the `create_model2.py` Python code provided in the resources repository.[^1]

```python
#
# Do not forget to add the otbtf/python directory to your PYTHONPATH.
# Else "tricks" can’t be imported.
# In the OTBTF Docker image, tricks.py is located in the following
# path: /work/otb/otb/Modules/otbtf
#
# Works with OTBTF 1.7
#
from tricks import *
import sys

nclasses=6

def myModel(x):

    # input patches: 16x16x4
    conv1 = tf.layers.conv2d(inputs=x, filters=16, kernel_size=[5,5],
                             padding="valid", activation=tf.nn.relu)
    # conv1 out size: 12x12x16
    conv2 = tf.layers.conv2d(inputs=conv1, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv2 out size: 10x10x16
    conv3 = tf.layers.conv2d(inputs=conv2, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv3 out size: 8x8x16
    conv4 = tf.layers.conv2d(inputs=conv3, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv4 out size: 6x6x32
    conv5 = tf.layers.conv2d(inputs=conv4, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv5 out size: 4x4x32
    conv6 = tf.layers.conv2d(inputs=conv5, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv6 out size: 2x2x32
```

[^1]: https://github.com/remicres/otbtf_tutorials_resources
