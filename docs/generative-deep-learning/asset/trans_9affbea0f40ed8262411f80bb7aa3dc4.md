
The dataset consists of an array of four numbers for each timestep: the MIDI note pitches of each of the four voices. A timestep in this dataset is equal to a 16th note (a semiquaver). So, for example, in a single bar of 4 quarter (crotchet) beats, there are 16 timesteps. The dataset is automatically split into train, validation, and test sets. We will be using the train dataset to train the MuseGAN.

To start, we need to get the data into the correct shape to feed the GAN. In this example we’ll generate two bars of music, so we’ll extract only the first two bars of each chorale. Each bar consists of 16 timesteps and there are a potential 84 pitches across the 4 voices.

![](img/f0f0f5d89818fdddf117bbe758ac8143_344_0.png)

Voices will be referred to as tracks from here on, to keep the terminology in line with the original paper.

Therefore, the transformed data will have the following shape:

```
[BATCH_SIZE, N_BARS, N_STEPS_PER_BAR, N_PITCHES, N_TRACKS]
```

where:

```
BATCH_SIZE = 64
N_BARS = 2
N_STEPS_PER_BAR = 16
N_PITCHES = 84
N_TRACKS = 4
```

To get the data into this shape, we one-hot encode the pitch numbers into a vector of length 84 and split each sequence of notes into two bars of 16 timesteps each. We are making the assumption here that each chorale in the dataset has four beats in each bar, which is reasonable, and even if this were not the case it would not adversely affect the training of the model.

Figure 11-14 shows how two bars of raw data are converted into the transformed piano roll dataset that we will use to train the GAN.

## Musical score

2 bars

16 timesteps

4 tracks

Raw data

Transformed data

4 tracks

```
array([[74., 70., 65., 58.],
[74., 70., 65., 58.],
[74., 70., 65., 58.],
[74., 70., 65., 58.],
[75., 70., 58., 55.],
[75., 70., 58., 55.],
[75., 70., 60., 55.],
[77., 69., 62., 50.],
[77., 69., 62., 50.],
[77., 69., 62., 50.],
[77., 69., 62., 50.],
[77., 70., 62., 55.],
[77., 69., 62., 55.],
[75., 67., 63., 48.],
[75., 67., 63., 48.],
[75., 69., 63., 48.],
[75., 69., 63., 48.],
[74., 70., 65., 46.],
[74., 70., 65., 46.],
[74., 70., 65., 46.],
[74., 70., 65., 46.],
[72., 69., 65., 53.],
[72., 69., 65., 53.],
[72., 69., 65., 53.],
[72., 69., 65., 53.],
[72., 69., 65., 53.],
[72., 69., 65., 53.],
[72., 69., 65., 53.]]
```

16 timesteps

2 bars

4 tracks

84 pitches

16 timesteps

2 bars

Figure 11-14. Processing two bars of raw data into piano roll data that we can use to train the GAN

![](img/f0f0f5d89818fdddf117bbe758ac8143_345_0.png)

![](img/f0f0f5d89818fdddf117bbe758ac8143_345_1.png)

## The MuseGAN Generator

Like all GANs, MuseGAN consists of a generator and a critic. The generator tries to fool the critic with its musical creations, and the critic tries to prevent this from happening by ensuring it is able to tell the difference between the generator's forged Bach chorales and the real thing.

Where MuseGAN differs is in the fact that the generator doesn't just accept a single noise vector as input, but instead has four separate inputs, which correspond to four different characteristics of the music: chords, style, melody, and groove. By manipulating each of these inputs independently we can change high-level properties of the generated music.

A high-level view of the generator is shown in Figure 11-15.

## THE MUSEGAN GENERATOR

![](img/f0f0f5d89818fdddf117bbe758ac8143_346_0.png)

Figure 11-15. High-level diagram of the MuseGAN generator

The diagram shows how the chords and melody inputs are first passed through a temporal network that outputs a tensor with one of the dimensions equal to the number of bars to be generated. The style and groove inputs are not stretched temporally in this way, as they remain constant through the piece.

Then, to generate a particular bar for a particular track, the relevant outputs from the chords, style, melody, and groove parts of the network are concatenated to form a longer vector. This is then passed to a bar generator, which ultimately outputs the specified bar for the specified track.

By concatenating the generated bars for all tracks, we create a score that can be compared with real scores by the critic.

Let’s first take a look at how to build a temporal network.

## The temporal network

The job of a temporal network—a neural network consisting of convolutional transpose layers—is to transform a single input noise vector of length Z_DIM = 32 into a different noise vector for every bar (also of length 32). The Keras code to build this is shown in Example 11-6.

### Example 11-6. Building the temporal network

```
def conv_t(x, f, k, s, a, p, bn):
    x = layers.Conv2DTranspose(
        filters = f
        , kernel_size = k
        , padding = p
        , strides = s
        , kernel_initializer = initializer
    )(x)

    if bn:
        x = layers.BatchNormalization(momentum = 0.9)(x)

    x = layers.Activation(a)(x)
    return x

def TemporalNetwork():
    input_layer = layers.Input(shape=(Z_DIM,), name='temporal_input')
    x = layers.Reshape([1,1,Z_DIM])(input_layer)
    x = conv_t(
        x, f=1024, k=(2,1), s=(1,1), a = 'relu', p = 'valid', bn = True
    )
    x = conv_t(
        x, f=Z_DIM, k=(N_BARS - 1,1), s=(1,1), a = 'relu', p = 'valid', bn = True
    )
    output_layer = layers.Reshape([N_BARS, Z_DIM])(x)
    return models.Model(input_layer, output_layer)
```

① The input to the temporal network is a vector of length 32 (Z_DIM).

② We reshape this vector to a 1 × 1 tensor with 32 channels, so that we can apply convolutional 2D transpose operations to it.

③ We apply Conv2DTranspose layers to expand the size of the tensor along one axis, so that it is the same length as N_BARS.

④ We remove the unnecessary extra dimension with a Reshape layer.

The reason we use convolutional operations rather than requiring two independent vectors into the network is because we would like the network to learn how one bar should follow on from another in a consistent way. Using a neural network to expand the input vector along the time axis means the model has a chance to learn how music flows across bars, rather than treating each bar as completely independent of the last.

## Chords, style, melody, and groove

Let’s now take a closer look at the four different inputs that feed the generator:

### Chords

The chords input is a single noise vector of length Z_DIM. This vector’s job is to control the general progression of the music over time, shared across tracks, so we use a TemporalNetwork to transform this single vector into a different latent vector for every bar. Note that while we call this input chords, it really could control anything about the music that changes per bar, such as general rhythmic style, without being specific to any particular track.

### Style

The style input is also a vector of length Z_DIM. This is carried forward without transformation, so it is the same across all bars and tracks. It can be thought of as the vector that controls the overall style of the piece (i.e., it affects all bars and tracks consistently).

### Melody

The melody input is an array of shape [N_TRACKS, Z_DIM]—that is, we provide the model with a random noise vector of length Z_DIM for each track.

Each of these vectors is passed through a track-specific TemporalNetwork, where the weights are not shared between tracks. The output is a vector of length Z_DIM for every bar of every track. The model can therefore use these input vectors to fine-tune the content of every single bar and track independently.

### Groove

The groove input is also an array of shape [N_TRACKS, Z_DIM]—a random noise vector of length Z_DIM for each track. Unlike the melody input, these vectors are not passed through the temporal network but instead are fed straight through, just like the style vector. Therefore, each groove vector will affect the overall properties of a track, across all bars.

We can summarize the responsibilities of each component of the MuseGAN generator as shown in Table 11-1.

## Table 11-1. Components of the MuseGAN generator

|  | Output differs across bars? | Output differs across parts? |
|---|---|---|
| Style | X | X |
| Groove | X | ✓ |
| Chords | ✓ | X |
| Melody | ✓ | ✓ |

The final piece of the MuseGAN generator is the bar generator—let’s see how we can use this to glue together the outputs from the chord, style, melody, and groove components.

## The bar generator

The bar generator receives four latent vectors—one from each of the chord, style, melody, and groove components. These are concatenated to produce a vector of length 4 * Z_DIM as input. The output is a piano roll representation of a single bar for a single track—i.e., a tensor of shape [1, n_steps_per_bar, n_pitches, 1].

The bar generator is just a neural network that uses convolutional transpose layers to expand the time and pitch dimensions of the input vector. We create one bar generator for every track, and weights are not shared between tracks. The Keras code to build a BarGenerator is given in Example 11-7.

### Example 11-7. Building the BarGenerator

```
def BarGenerator():
    input_layer = layers.Input(shape=(Z_DIM * 4,), name='bar_generator_input') ①
    x = layers.Dense(1024)(input_layer) ②
    x = layers.BatchNormalization(momentum = 0.9)(x)
    x = layers.Activation('relu')(x)
    x = layers.Reshape([2,1,512])(x)
    x = conv_t(x, f=512, k=(2,1), s=(2,1), a= 'relu',  p = 'same', bn = True) ③
    x = conv_t(x, f=256, k=(2,1), s=(2,1), a= 'relu',  p = 'same', bn = True)
    x = conv_t(x, f=256, k=(2,1), s=(2,1), a= 'relu',  p = 'same', bn = True)
    x = conv_t(x, f=256, k=(1,7), s=(1,7), a= 'relu',  p = 'same', bn = True) ④
    x = conv_t(x, f=1, k=(1,12), s=(1,12), a= 'tanh', p = 'same', bn = False) ⑤
    output_layer = layers.Reshape([1, N_STEPS_PER_BAR , N_PITCHES ,1])(x) ⑥
    return models.Model(input_layer, output_layer)
```

