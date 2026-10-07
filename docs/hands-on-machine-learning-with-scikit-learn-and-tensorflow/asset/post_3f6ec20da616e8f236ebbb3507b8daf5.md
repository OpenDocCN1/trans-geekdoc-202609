
- Randomized PCA 227
- Incremental PCA 227
- Kernel PCA 228
- Selecting a Kernel and Tuning Hyperparameters 229
- LLE 232
- Other Dimensionality Reduction Techniques 234
- Exercises 235

## 9. Unsupervised Learning Techniques.................................................................... 237
- Clustering 238
- K-Means 240
- Limits of K-Means 250
- Using clustering for image segmentation 251
- Using Clustering for Preprocessing 252
- Using Clustering for Semi-Supervised Learning 254
- DBSCAN 256
- Other Clustering Algorithms 259
- Gaussian Mixtures 260
- Anomaly Detection using Gaussian Mixtures 266
- Selecting the Number of Clusters 267
- Bayesian Gaussian Mixture Models 270
- Other Anomaly Detection and Novelty Detection Algorithms 274

# Part II. Neural Networks and Deep Learning

## 10. Introduction to Artificial Networks with Keras............................................... 277
- From Biological to Artificial Neurons 278
- Biological Neurons 279
- Logical Computations with Neurons 281
- The Perceptron 281
- Multi-Layer Perceptron and Backpropagation 286
- Regression MLPs 289
- Classification MLPs 290
- Implementing MLPs with Keras 292
- Installing TensorFlow2 293
- Building an Image Classifier Using the Sequential API 294
- Building a Regression MLP Using the Sequential API 303
- Building Complex Models Using the Functional API 304
- Building Dynamic Models Using the Subclassing API 309
- Saving and Restoring a Model 311
- Using Callbacks 311
- Visualization Using TensorBoard 313
- Fine-Tuning Neural Network Hyperparameters 315
- Number of Hidden Layers 319
- Number of Neurons per Hidden Layer 320
- Learning Rate, Batch Size and Other Hyperparameters 320
- Exercises 322

## 11. Training Deep Networks. ........................................................................... 325
- Vanishing/Exploding Gradients and He Initialization 326
- Glorot and l2 Regularization 327
- Nonsaturating Activation Functions 329
- Batch Normalization 333
- Gradient Clipping 338
- Reusing Pretrained Layers 339
- Transfer Learning With Keras 341
- Unsupervised Pretraining 343
- Pretraining on an Auxiliary Task 344
- Faster Optimizers 344
- Momentum Optimization 345
- Nesterov Accelerated Gradient 346
- AdaGrad 347
- RMSProp 349
- Adam and Adam Optimization 349
- Learning Rate Scheduling 352
- Avoiding Overfitting Through Regularization 356
- l1 and l2 Regularization 356
- Dropout 357
- Monte-Carlo (MC) Dropout 360
- Max-Norm Regularization 362
- Summary and Practical Guidelines 363
- Exercises 364

## 12. Custom Models and Training with TensorFlow. ........................................ 367
- A Quick Tour of TensorFlow 368
- Using TensorFlow like NumPy 371
- Tensors and Operations 371
- Tensors and NumPy 373
- Type Conversions 374
- Variables 374
- Other Data Structures 375
- Customizing Models and Training Algorithms 376
- Custom Loss Functions 376
## Saving and Loading Models That Contain Custom Components 377
- Custom Activation Functions, Initializers, Regularizers, and Constraints 379
- Custom Metrics 380
- Custom Layers 383
- Custom Models 386
- Losses and Metrics Based on Model Internals 388
- Computing Gradients Using Autodiff 389
- Custom Training Loops 393
- TensorFlow Functions and Graphs 396
- Autograph and Tracing 398
- TF Function Rules 400

## 13. Loading and Preprocessing Data with TensorFlow................ 403
- The Data API 404
- Chaining Transformations 405
- Shuffling the Data 406
- Preprocessing the Data 409
- Putting Everything Together 410
- Prefetching 411
- Using the Dataset with tf.keras 413
- The TFRecord Format 414
- Compressed TFRecord Files 415
- A Brief Introduction to Protocol Buffers 415
- TensorFlow Protobuf 416
- Loading and Parsing Examples 418
- Handling Lists of Lists Using the SequenceExample Protobuf 419
- The Features API 420
- Categorical Features 421
- Crossed Categorical Features 421
- Encoding Categorical Features Using One-Hot Vectors 422
- Encoding Categorical Features Using Embeddings 423
- Using Feature Columns for Parsing 426
- Using Feature Columns in Your Models 426
- TF Transform 428
- The TensorFlow Datasets (TFDS) 429

## 14. Deep Computer Vision Using Convolutional Neural Networks................ 431
- The Architecture of the Visual Cortex 432
- Convolutional Layer 434
- Filters 436
- Stacking Multiple Feature Maps 437
- TensorFlow Implementation 439
- Memory Requirements 441
- Pooling Layer 442
- TensorFlow Implementation 444
- CNN Architectures 446
- LeNet-5 449
- AlexNet 450
- GoogLeNet 452
- VGGNet 456
- ResNet 457
- Xception 459
- SENet 461
- Implementing a ResNet-34 CNN Using Keras 464
- Using Pretrained Models From Keras 465
- Pretrained Models for Transfer Learning 467
- Classification and Localization 469
- Object Detection 471
- Fully Convolutional Networks (FCNs) 473
- You Only Look Once (YOLO) 475
- Semantic Segmentation 478
- Exercises 482

# Preface

## The Machine Learning Tsunami

In 2006, Geoffrey Hinton et al. published a paper¹ showing how to train a deep neural network capable of recognizing handwritten digits with state-of-the-art precision (>98%). They branded this technique "Deep Learning." Training a deep neural net was widely considered impossible at the time², and most researchers had abandoned the idea since the 1990s. This paper revived the interest of the scientific community and before long many new papers demonstrated that Deep Learning was not only possible, but capable of mind-blowing achievements that no other Machine Learning (ML) technique could hope to match (with the help of tremendous computing power and great amounts of data). This enthusiasm soon extended to many other areas of Machine Learning.

Fast-forward 10 years and Machine Learning has conquered the industry: it is now at the heart of much of the magic in today's high-tech products, ranking your search results, powering your smartphone’s speech recognition, recommending videos and beating the world champion at the game of Go. Before you know it, it will be driving your car.

## Machine Learning in Your Projects

So naturally you are excited about Machine Learning and you would love to join the party!

Perhaps you would like to give your homemade robot a brain of its own? Make it recognize faces? Or learn to walk around

¹ Available on Hinton’s home page at http://www.cs.toronto.edu/~hinton/.

² Despite the fact that Yann Lecun’s deep convolutional networks had worked well for image recognition since the 1990s, although they were not as general

# Objective and Approach

This book assumes that you know nothing about Machine Learning. Its goal is to give you the concepts, the intuitions, and the tools you need to actually implement programs capable learning from data.

We will cover a large number of techniques, from the simplest and most commonly used (such as linear regression) to some of the Deep Learning techniques that regularly win competitions.

Rather than implementing our toy versions of each algorithm, we will be using actual production-ready Python frameworks:

- Scikit-Learn is very easy to use, it implements many Machine Learning algorithms efficiently, so it is a great entry point to learn Machine Learning.
- TensorFlow is a more complex library for distributed numerical computation. It makes it possible to train and run large neural networks by distributing the computations across potentially hundreds of multi-GPU servers. TensorFlow was created at Google and supports many of their large-scale Machine Learning applications. It was opened in November 2015.
- Keras is a high level Deep Learning API that makes it very simple to train and run neural networks. It can run on top of TensorFlow, Theano or Soft Cognitive Toolkit (formerly known as CNTK). TensorFlow comes with its own implementation of this API, called tf.keras, which provides support for some advanced TensorFlow features (e.g., efficiently to load data).

The book favors a hands-on approach, giving an intuitive understanding of Machine Learning through concrete examples and a little bit of theory. While you can read this book without picking up your laptop, we highly recommend
