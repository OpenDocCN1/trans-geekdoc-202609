
```
5.     x = layers.LeakyReLU(0.2)(x)
6.     y = layers.Reshape((64,64,1))(y)
7.     
8.     x = layers.concatenate([img, y])
9.     
10.    x = layers.Conv2D(filters=128, kernel_size=5,
11.                       strides=2, padding='same')(x)
12.    for filter_size in [256, 512, 1024]:
13.        x = layers.Conv2D(filters=filter_size, kernel_size=5,
14.                           strides=2, padding='same')(x)
15.        x = layers.LeakyReLU(0.2)(x)
16.        x = layers.BatchNormalization()(x)
17.
18.    x = layers.Flatten()(x)
19.    x = layers.Dense(1)(x)
20.    return Model(inputs=[img, label], outputs=x)
```

In `line 8` of the preceding code, we are adding the auxiliary information of a new channel as the fourth channel, along with three channels of the input image. The rest of the code remains the same as before for the vanilla discriminator. Similarly, for the conditional generator, we take the first convolution layer as is in the vanilla generator to create the first 3D tensor of size 4×4×1024 and then append the embedding layer of auxiliary information after mapping and reshaping it to 4×4×1 as another channel.

The training loop remains the same as for the vanilla GAN, except that the generator also needs fake labels as input, and the discriminator requires real label as input. The rest of the code remains the same, as shown in the following code:

```
1. def train_step(images, labels):
2.     noise = tf.random.normal([BATCH_SIZE, noise_dim])
3.     
4.     with tf.GradientTape() as gen_tape, tf.GradientTape() as disc_tape:
5.         generated_images = G(noise, training=True)
6.         fake_labels = np.random.randint(0, 2, BATCH_SIZE)
7.         
8.         real_output = D([images, labels], training=True)
9.         fake_output = D([generated_images, fake_labels], training=True)
```

Conditional GANs are also used for image-to-image translation tasks. Image-to-image translation is the task of taking images from one domain and transforming them to another image so that they have the characteristics of images from another domain. Instead of passing auxiliary data as input, we can pass image from source image to condition the generator. Also, the auxiliary information being so rich, the generator can take source image as input directly and random noise vector is not required at all. To generate a good quality image output now, the simple CNN architecture we used so far may not be sufficient. We can use architectures with higher capacity, like U-Net or Resnet-50, to create the conditional generator. Pix2Pix model is a cGAN where output generation is conditioned on an input source image, and they use U-Net architecture for generator.

# Cycle GAN (CycleGAN)

CycleGAN is a GAN architecture that uses two generators and two discriminators and is primarily applied to various image-to-image translation tasks where paired image data from two domains are not available.

For example, if we define source image domain as a set of natural images. We take a hand-drawn image of a beach where we spent our holiday in childhood. How nice would it be if we could input this hand-drawn image to the generator and get a photo realistic beach image with our childhood memories! Image translation is a classical computer vision problem, and all the traditional approaches to solve this involves using paired training data set, that is, a data set that has pairwise images from two different domains. Examples of paired data sets are (1) pair of satellite image and Google map image, and (2) facades data set that consists of 506 Building Facades and the corresponding segmentations. However, getting paired image data set is not always possible; this is where CycleGANs can be useful. Let’s now formally introduce CycleGANs.

Let ![](images/3010.jpg) and ![](images/3011.jpg) be data sets with image samples from two different domains. We can denote the data distributions as ![](images/3012.jpg) and ![](images/3013.jpg). Let’s define two generators ![](images/3014.jpg) and ![](images/3015.jpg). Note that unlike the previously defined generators, the generators here take an image as input directly and not a random noise vector. Also, we define two adversarial discriminators ![](images/3016.jpg) and ![](images/3017.jpg), where ![](images/3018.jpg)’s goal is to distinguish between images ![](images/3019.jpg) and translated images {![](images/3020.jpg)()}, and ![](images/3021.jpg)’s aims to discriminate between ![](images/3022.jpg) and {![](images/3023.jpg)(x)}.

So, now we have four neural networks to train: ![](images/3024.jpg). We can define a joint objective function for training this network. Also, we have to state the steps for training these networks. As there are two separate GANs, we have two adversarial losses:

![](images/3025.jpg)

and ![](images/3026.jpg)

This objective will also have the same issues as seen in vanilla GAN adversarial loss formulation, like vanishing gradient and mode collapse. Similar to the feature matching technique we used in vanilla GANs, we can enforce the generators F and G to be consistent, that is, if ![](images/3027.jpg), then transforming x using G and then applying F on the transformed image, we should get an image ![](images/3028.jpg) very close to x. If ![](images/3029.jpg). Refer to the following figure:

![](images/Image49357.jpg)

**Figure 12.16:** CycleGAN

So, ![](images/3030.jpg) should be minimized, that is, ![](images/3031.jpg) should be minimized and similarly, ![](images/3032.jpg) should be minimized. We call the total quantity **cycle consistency loss**:

![](images/3033.jpg)

Hence, the loss for CycleGAN can be written as adversarial loss + cycle consistency loss: ![](images/3034.jpg). Here, l is a hyperparameter that controls how much weight should be given to the cycle consistency loss. For better colour preservation in the output, another loss term was proposed, which is optional and is called identity loss term. This is also a pixel wise L1 loss term, like ![](images/3035.jpg). The idea behind this is that for the generator ![](images/3036.jpg), if we take an image from the target domain ![](images/3037.jpg), we should leave it as is because this image already belongs to Y, and hence, no transformation is required. Ideally, ![](images/3038.jpg) and ![](images/3039.jpg), and hence, we should minimize the term ![](images/3040.jpg). So, our loss has one more term and one more hyperparameter m:

![](images/3041.jpg)

Here, the adversarial loss terms can be replaced by Wasserstein loss for more stable training of the cycle GAN.

Here are the steps for training cycle GANs:

1.  Choose hyperparameters l, m.
2.  Randomly initialize the weights of the generator and discriminator networks.
3.  Freeze the generator and find an optimal discriminator for the given generator:
    1.  Take a batch of images ![](images/3042.jpg) and ![](images/3043.jpg)
    2.  Run SGD to optimize discriminator weights by computing gradient of the adversarial loss for discriminator.
4.  Update Generator weights by optimizing the generator loss and keeping discriminator fixed:
    1.  For images ![](images/3044.jpg) and ![](images/3045.jpg), compute:
        i. Cycled x for all x in ![](images/3046.jpg)
        ii. Cycled y for all y in ![](images/3047.jpg)
        iii. Same x for identity loss: for all y in ![](images/3048.jpg)
        iv. Same y for identity loss: for all x in ![](images/3049.jpg)
        v. Compute all three loss components and then the total generator loss gradient.
5.  Repeat 3 and 4 until convergence.

**TIP:** The following link provides an implementation of cycle GAN using U-Net generator and discriminator:

[https://www.tensorflow.org/tutorials/generative/cyclegan](https://www.tensorflow.org/tutorials/generative/cyclegan)

# Autoregressive generative models
