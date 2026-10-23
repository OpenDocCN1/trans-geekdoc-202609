
0, ‘n_mels’: 128, ‘window_fn’: <function _VariableFunctions.hann_window>, ‘wkwargs’: None, ‘stype’: ‘power’, ‘top_db’: None, ‘sr’: 8000, ‘nchannels’: 1}

Now we want to narrow them down a bit.

```
aud2spec = DBMelSpec(n_mels=128,
    f_max=10000,
    n_fft=1024,
    hop_length=128,
    top_db=100)
```

For our transforms, we’ll use:

- **RemoveSilence**
  - Splits a signal at points of silence more than 2 * pad_ms (default is 20)
- **CropSignal**
  - Crops a signal by duration and adds padding if needed
- **aud2spec**
  - Our SpectrogramTransformer with parameters
- **MaskTime**
  - Wrapper for MaskFreq, which applies einsum operations
- **MaskFreq**
  - SpecAugment Time Masking (https://arxiv.org/abs/1904.08779)

Let’s look a bit more at the padding ‘CropSignal uses:

There are three different types:

- **AudioPadType.Zeros:** The default, random zeros before and after
- **AudioPadType.Repeat:** Repeat the signal until proper length (great for acoustic scene classification and voice recognition, terrible for speech recognition)
- **AudioPadType.ZerosAfter:** This is the default for many other libraries, just pad with zeros until you get the specified length. Now let’s rebuild our DataBlock:

```
item_tfms = [RemoveSilence(),
CropSignal(1000),
aud2spec,
MaskTime(size=4),
MaskFreq(size=10)]
```

```
aud_digit = DataBlock(blocks=(AudioBlock, CategoryBlock),
get_items=get_audio_files,
splitter=RandomSplitter(),
item_tfms = item_tfms,
get_y=get_y)
```

```
dls = aud_digit.dataloaders(path_dig, bs=128)
```

If we now look at our dataloaders we see a completely different image. Our spectrograms show these time segmentation.

```
dls.show_batch(max_n=2)
```

![](img/d5454da46c702784893ef8b0b539e5b9_302_0.png)

Now we can train our model again using the augmented data. We have built an audio_learner-function that helps us to build our learner faster by passing in just the dataloaders, architecture, loss_function and the metrics. This function only alters the learner if we pass in a one-channel image.

```
def audio_learner(dls, arch, loss_func, metrics):
"Prepares a `Learner` for audio processing"
```

```
learn = Learner(dls, arch, loss_func, metrics=metrics)
n_c = dls.one_batch()[0].shape[1]
if n_c == 1: alter_learner(learn)
return learn
```

![](img/d5454da46c702784893ef8b0b539e5b9_303_0.png)

```
learn = audio_learner(dls,
 xresnet18(),
 CrossEntropyLossFlat(), accuracy)

learn.lr_find()
(0.10964782238006592, 0.0030199517495930195)
```

![](img/d5454da46c702784893ef8b0b539e5b9_304_0.png)

```
learn.fit_one_cycle(10, 3e-3)
```

| epoch | train_loss | valid_loss | accuracy | time |
|---|---|---|---|---|
| 0 | 6.643846 | 5.578056 | 0.102500 | 00:02 |
| 1 | 4.678609 | 3.434466 | 0.142500 | 00:02 |
| 2 | 3.457336 | 4.610990 | 0.220000 | 00:02 |
| 3 | 2.746760 | 3.941507 | 0.247500 | 00:02 |
| 4 | 2.230091 | 1.606534 | 0.445000 | 00:02 |
| 5 | 1.816660 | 1.344395 | 0.525000 | 00:02 |
| 6 | 1.475092 | 0.606622 | 0.827500 | 00:02 |
| 7 | 1.199739 | 0.578236 | 0.840000 | 00:02 |
| 8 | 0.978478 | 0.376330 | 0.915000 | 00:02 |
| 9 | 0.809246 | 0.402364 | 0.900000 | 00:02 |

## 20.7 Mel Frequency Cepstral Coefficient (MFCC)

The MFCC basically is a linear cosine transform of a log power spectrum on a nonlinear mel scale of frequency. This means we take a bunch of lines (waves) and try to fit some linear representations.

![](img/d5454da46c702784893ef8b0b539e5b9_305_0.png)

Let’s try this. We start with the AudioToMFCC and set some default values. Then we adjust our item transforms.

```
aud2mfcc = AudioToMFCC(n_mfcc=40, melkwargs={'n_fft':2048, 'hop_length':256, 'n_mels':128})
```

```
item_tfms = [CropSignal(1000), aud2mfcc]
```

Instead of rebuilding the datablock each time, we can simply override the item-transforms from the dataset and rebuild our dataloaders.

```
aud_digit.item_tfms
(#6) [ToTensor: (PILMask,object) -> encodes (PILBase,object) -> encodes ,<function RemoveSilence.._inner at 0x7f7804c7b9e0>,<function CropSignal.._inner at 0x7f7804c7bd40>,AudioToSpec: (AudioTensor,object) -> encodes ,<function MaskTime.._inner at 0x7f7804c7bf80>,<function MaskFreq.._inner at 0x7f7804c7bb00>]
```

```
aud_digit.item_tfms = item_tfms
dls = aud_digit.dataloaders(path_dig, bs=128)
```

If we now look at a batch, everything looks very different.

```
dls.show_batch(max_n=2)
```

# Channel 0 Image 0: 40 X 32px

![](img/d5454da46c702784893ef8b0b539e5b9_306_0.png)

# Channel 0 Image 0: 40 X 32px

![](img/d5454da46c702784893ef8b0b539e5b9_306_1.png)

Now we train our model for 5 epochs and we get an accuracy of 0.96 after training. Here we understand the importance of doing the right augmentation to improve the performance of our model.

```
learn = audio_learner(dls, xresnet18(), CrossEntropyLossFlat(), accuracy)
learn.lr_find()
```

(0.06309573650360108, 0.0030199517495930195)

![](img/d5454da46c702784893ef8b0b539e5b9_307_0.png)

```
learn.fit_one_cycle(5, 1e-2)
```

| epoch | train_loss | valid_loss | accuracy | time |
|---|---|---|---|---|
| 0 | 3.944870 | 2.120851 | 0.300000 | 00:01 |
| 1 | 2.000032 | 4.179723 | 0.307500 | 00:01 |
| 2 | 1.246085 | 0.557256 | 0.835000 | 00:01 |
| 3 | 0.844206 | 0.506152 | 0.847500 | 00:01 |
| 4 | 0.599616 | 0.128170 | 0.960000 | 00:01 |

## 20.8 MFCC + Delta

Another transform we are looking at is the Delta transform.
A delta is defined as the local estimate of the derivative of the input data along the selected axis.

This means we can generate multiple channels out of one single signal. We see the different channels with the batch-data (channel image 0, channel image 1, etc.).

Now we have a three-channel image input to our model again. This is why we made the change to the function audio_learner above, to only change if the input has one channel.

```
item_tfms = [CropSignal(1000), aud2mfcc, Delta()]
aud_digit.item_tfms = item_tfms
```

```
dls = aud_digit.dataloaders(path_dig, bs=128)
dls.show_batch(max_n=2)
```

![](img/d5454da46c702784893ef8b0b539e5b9_308_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_308_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_308_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_308_3.png)

![](img/d5454da46c702784893ef8b0b539e5b9_308_4.png)

![](img/d5454da46c702784893ef8b0b539e5b9_308_5.png)

Again we look for a good learning rate and do some training on our learner.

```
learn = audio_learner(dls,
xresnet18(),
CrossEntropyLossFlat(),
accuracy)
```

```
learn.lr_find()
```

(0.012022644281387329, 0.002511886414140463)

![](img/d5454da46c702784893ef8b0b539e5b9_309_0.png)

```
learn.fit_one_cycle(5, 1e-2)
```

| epoch | train_loss | valid_loss | accuracy | time |
|---|---|---|---|---|
| 0 | 3.853784 | 5.124284 | 0.085000 | 00:01 |
| 1 | 1.951959 | 2.674761 | 0.525000 | 00:01 |
| 2 | 1.199445 | 0.654258 | 0.810000 | 00:01 |
| 3 | 0.804199 | 0.207820 | 0.930000 | 00:01 |
| 4 | 0.567783 | 0.096261 | 0.977500 | 00:01 |

This time our accuracy is nearly up to 98% – a great improvement. In this chapter we have shown how we can use the fastai library to analyse audiostreams with deep learning models. We haven’t used the audio streams per se, but different spectrogram images and applied deep learning techniques from computer vision.

You see that you can use different techniques by just transforming your input data.

## Chapter 21

### Introduction to Tabular Data – How to use Pandas DataFrame

Before starting with tabular data, we have to go deeper into how tabular data is represented. The basic representation for tabular data in python is with the help of the Pandas-Library.

Pandas is a library that makes working with tabular data really easy.
Therefore we will now have a quick look at the pandas library - especially the pandas DataFrame class.

We can create pandas DataFrame from different sources of data. These are some of them:

- **read_csv**
- **read_excel**
- **read_feather**
- **read_html**
- **read_json**
- **read_pickle**
- **read_sql**
- **read_table**

We will focus on the read_csv-function to create a DataFrame. Generally you can read data from anything that can store data in a kind of table structure.
For this intro we will use the *Titanic* dataset from kaggle.

The *Titanic* dataset contains information on the passengers of the Titanic and if they have survived or not. For this introduction to pandas we will only use a minimum of the fastai library.

```
!pip install pandas==0.25
#!pip install fastai --upgrade
```
