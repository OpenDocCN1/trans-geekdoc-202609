# Video Classification

```
net.add(tf.keras.layers.Dropout(0.25))
net.add(tf.keras.layers.Flatten())
net.add(tf.keras.layers.Dense(512, activation='sigmoid'))
net.add(tf.keras.layers.Dropout(0.5))
net.add(tf.keras.layers.Dense(no_classes, activation='softmax'))
net.compile(loss=tf.keras.losses.categorical_crossentropy,
              optimizer=tf.keras.optimizers.Adam(), metrics=['accuracy'])
```

3D convolution needs a lot of computing power. 3D convolution achieves an accuracy of 90.2% on the Sports1M dataset.

# Using trajectory for classification

Wang et al. (https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Wang_Action_Recognition_With_2015_CVPR_paper.pdf) used the trajectory of parts to classify the actions performed. This work combines handcrafted and deep learned features for final predictions. The following is a representation of the classification:

![](bbox=[0.185, 0.506, 0.812, 0.816])