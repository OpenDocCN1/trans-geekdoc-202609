
## Chapter 6: Recurrent Neural Networks 188

### Setting up a basic Recurrent Neural Network 188

- Getting ready 189
- How to do it... 189
- How it works... 192

### Setting up a bidirectional RNN model 193

- Getting ready 193
- How to do it... 194

### Setting up a deep RNN model 197

- How to do it... 197

### Setting up a Long short-term memory based sequence model 198

- How to do it... 198
- How it works... 199

## Chapter 7: Reinforcement Learning 202

### Introduction 202

### Setting up a Markov Decision Process 204

- Getting ready 204
- How to do it... 205

### Performing model-based learning 210

- How to do it... 212

### Performing model-free learning 213

- Getting ready 213
- How to do it... 215

## Chapter 8: Application of Deep Learning in Text Mining 218

### Performing preprocessing of textual data and extraction of sentiments 218

- How to do it... 219
- How it works... 225

### Analyzing documents using tf-idf 226

- How to do it... 226
- How it works... 228

### Performing sentiment prediction using LSTM network 229

- How to do it... 229
- How it works... 233

### Application using text2vec examples 233

- How to do it... 233
- How it works... 236

## Chapter 9: Application of Deep Learning to Signal processing 237

### Introducing and preprocessing music MIDI files

- Getting ready
- How to do it...

### Building an RBM model

- Getting ready
- How to do it...

### Generating new music notes

- How to do it...

## Chapter 10: Transfer Learning

### Introduction

### Illustrating the use of a pretrained model

- Getting ready
- How to do it...

### Setting up the Transfer Learning model

- Getting ready
- How to do it...

### Building an image classification model

- Getting ready
- How to do it...

### Training a deep learning model on a GPU

- Getting ready
- How to do it...

### Comparing performance using CPU and GPU

- Getting ready
- How to do it...
- There's more...
- See also

## Index

## Preface

Deep learning is one of the most commonly discussed areas in machine learning due to its ability to model complex functions and learn through a variety of data sources and structures, such as cross-sectional data, sequential data, images, text, audio, and video. Also, R is one of the most popular languages used in the data science community. With the growth of deep learning, the relationship between R and deep learning is growing tremendously. Thus, Deep Learning Cookbook in R aims to provide a crash course in building different deep learning models. The application of deep learning is demonstrated through structured, unstructured, image, and audio case studies. The book will also cover transfer learning and how to utilize the power of GPU to enhance the computation efficiency of the deep learning model.

## What this book covers

- *Chapter 1, Getting Started,* introduces different packages that are available for building deep learning models, such as TensorFlow, MXNet, and H2O. and how to set them up to be utilized later in the book.

- *Chapter 2, Deep Learning with R,* introduces the basics of neural network and deep learning. This chapter covers multiple recipes for building a neural network models using multiple toolboxes in R.

- *Chapter 3, Convolution Neural Network,* covers recipes on **Convolution Neural Networks** (CNN) through applications in image processing and classification.

- *Chapter 4, Data Representation Using Autoencoders,* builds the foundation of autoencoder using multiple recipes and also covers the application in data compression and denoising.

- *Chapter 5, Generative Models in Deep learning,* extends the concept of autoencoders to generative models and covers recipes such as Boltzmann machines, **restricted Boltzmann machines** (RBMs), and deep belief networks.

- *Chapter 6, Recurrent Neural Networks,* sets up the foundation for building machine learning models on a sequential datasets using multiple **recurrent neural networks** (RNNs).

- *Chapter 7, Reinforcement Learning,* provides the fundamentals for building reinforcement learning using **Markov Decision Process** (MDP) and covers both model-based learning and model-free learning.

Chapter 8, Application of Deep Learning in Text-Mining, provides an end-to-end implementation of the deep learning text mining domain.

Chapter 9, Application of Deep Learning to Signal processing, covers a detailed case study of deep learning in the signal processing domain.

Chapter 10, Transfer Learning, covers recipes for using pretrained models such as VGG16 and Inception and explains how to deploy a deep learning model using GPU.

## What you need for this book

A lot of inquisitiveness, perseverance, and passion is required to build a strong background in data science. The scope of deep learning is quite broad; thus, the following backgrounds is required to effectively utilize this cookbook:

- Basics of machine learning and data analysis
- Proficiency in R programming
- Basics of Python and Docker

Lastly, you need to appreciate deep learning algorithms and know how they solve complex problems in multiple domains.

## Who this book is for

This book is for data science professionals or analysts who have performed machine learning tasks and now want to explore deep learning and want a quick reference that address the pain points that crop up while implementing deep learning. Those who wish to have an edge over other deep learning professionals will find this book quite useful.

## Conventions

In this book, you will find a number of text styles that distinguish between different kinds of information. Here are some examples of these styles and an explanation of their meaning.

Code words in text, database table names, folder names, filenames, file extensions, pathnames, dummy URLs, user input, and Twitter handles are shown as follows: “We can include other contexts through the use of the include directive.”

A block of code is set as follows:

```
[default]
exten => s,1,Dial(Zap/1|30)
exten => s,2,Voicemail(u100)
exten => s,102,Voicemail(b100)
exten => i,1,Voicemail(s0)
```

When we wish to draw your attention to a particular part of a code block, the relevant lines or items are set in bold:

```
[default]
exten => s,1,**Dial**(Zap/1|30)
exten => s,2,Voicemail(u100)
exten => s, 102,Voicemail(b100)
exten => i,1,Voicemail(s0)
```

Any command-line input or output is written as follows:

```
# cp /usr/src/asterisk-addons/configs/cdr_mysql.conf.sample
/etc/asterisk/cdr_mysql.conf
```

New terms and important words are shown in bold. Words that you see on the screen, for example, in menus or dialog boxes, appear in the text like this: "Clicking the Next button moves you to the next screen."

> Warnings or important notes appear in a box like this.

> Tips and tricks appear like this.

## Reader feedback

Feedback from our readers is always welcome. Let us know what you think about this book–what you liked or disliked. Reader feedback is important for us as it helps us develop titles that you will really get the most out of.

To send us general feedback, simply email feedback@packtpub.com, and mention the book's title in the subject of your message.

If there is a topic that you have expertise in and you are interested in either writing or contributing to a book, see our author guide at www.packtpub.com/authors.

## Customer support

Now that you are the proud owner of a Packt book, we have a number of things to help you to get the most from your purchase.

### Downloading the example code

You can download the example code files for this book from your account at http://www.packtpub.com. If you purchased this book elsewhere, you can visit http://www.packtpub.com/support and register to have the files e-mailed directly to you.

You can download the code files by following these steps:

- 1. Log in or register to our website using your email address and password.
- 2. Hover the mouse pointer on the SUPPORT tab at the top.
- 3. Click on Code Downloads & Errata.
- 4. Enter the name of the book in the Search box.
- 5. Select the book for which you’re looking to download the code files.
- 6. Choose from the drop-down menu where you purchased this book from.
- 7. Click on Code Download.

You can also download the code files by clicking on the Code Files button on the book’s webpage at the Packt Publishing website. This page can be accessed by entering the book’s name in the Search box. Please note that you need to be logged in to your Packt account.

Once the file is downloaded, please make sure that you unzip or extract the folder using the latest version of:

- WinRAR / 7-Zip for Windows
- Zipeg / iZip / UnRarX for Mac
- 7-Zip / PeaZip for Linux

The code bundle for the book is also hosted on GitHub at https://github.com/PacktPublishing/R-Deep-Learning-Cookbook. We also have other code bundles from our rich catalog of books and videos available at https://github.com/PacktPublishing/. Check them out!
