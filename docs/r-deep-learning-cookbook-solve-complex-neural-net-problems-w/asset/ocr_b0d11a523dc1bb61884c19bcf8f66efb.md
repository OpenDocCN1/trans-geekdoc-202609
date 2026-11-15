# 5. Redefine the VGG16 network:

```
# Define VGG16 network
library(magrittr)
VGG16.model<-function(slim, input.image){
  vgg16.network = slim$conv2d(input.image, 64, shape (3, 3),
                 scope='vgg_16/conv1/conv1_1') %>%
  slim$conv2d(64, shape (3, 3), scope='vgg_16/conv1/conv1_2') %>%
  slim$max_pool2d(shape (2, 2), scope='vgg_16/pool1') %>%
  slim$conv2d(128, shape (3, 3), scope='vgg_16/conv2/conv2_1') %>%
  slim$conv2d(128, shape (3, 3), scope='vgg_16/conv2/conv2_2') %>%
  slim$max_pool2d(shape (2, 2), scope='vgg_16/pool2') %>%
  slim$conv2d(256, shape (3, 3), scope='vgg_16/conv3/conv3_1') %>%
  slim$conv2d(256, shape (3, 3), scope='vgg_16/conv3/conv3_2') %>%
  slim$conv2d(256, shape (3, 3), scope='vgg_16/conv3/conv3_3') %>%
  slim$max_pool2d(shape (2, 2), scope='vgg_16/pool3') %>%
  slim$conv2d(512, shape (3, 3), scope='vgg_16/conv4/conv4_1') %>%
  slim$conv2d(512, shape (3, 3), scope='vgg_16/conv4/conv4_2') %>%
  slim$conv2d(512, shape (3, 3), scope='vgg_16/conv4/conv4_3') %>%
  slim$max_pool2d(shape (2, 2), scope='vgg_16/pool4') %>%
  slim$conv2d(512, shape (3, 3), scope='vgg_16/conv5/conv5_1') %>%
  slim$conv2d(512, shape (3, 3), scope='vgg_16/conv5/conv5_2') %>%
  slim$conv2d(512, shape (3, 3), scope='vgg_16/conv5/conv5_3') %>%
  slim$max_pool2d(shape (2, 2), scope='vgg_16/pool5') %>%
  slim$conv2d(4096, shape (7, 7), padding='VALID',
         scope='vgg_16/fc6') %>%
  slim$conv2d(4096, shape (1, 1), scope='vgg_16/fc7') %>%
  slim$conv2d(1000, shape (1, 1), scope='vgg_16/fc8') %>%
  tf$squeeze(shape (1, 2), name='vgg_16/fc8/squeezed')
  return (vgg16.network)
}
```

6. The preceding function defines the network architecture used for the VGG16 network. The network can be assigned using the following script:

```
vgg16.network<-VGG16.model(slim, input.image = scaled.img)
```

7. Load the VGG16 weights vgg_16_2016_08_28.tar.gz downloaded in the *Getting started* section:

```
# Restore the weights
restorer = tf$trainSaver()
sess = tf$Session()
restorer$restore(sess, 'vgg_16.ckpt')
```