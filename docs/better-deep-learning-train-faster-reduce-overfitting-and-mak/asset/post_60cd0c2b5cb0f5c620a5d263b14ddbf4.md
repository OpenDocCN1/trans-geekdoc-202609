
## CONTENTS
- **20 Combine Models From Multiple Runs with Model Averaging Ensemble** ........................................ 379
  - 20.1 Model Averaging Ensemble .................................................................... 379
  - 20.2 Ensembles in Keras ............................................................................... 380
  - 20.3 Model Averaging Ensemble Case Study ............................................................ 382
  - 20.4 Extensions ............................................................................................ 396
  - 20.5 Further Reading ...................................................................................... 396
  - 20.6 Summary ................................................................................................. 397
- **21 Contribute Proportional to Trust with Weighted Average Ensemble** ................................ 398
  - 21.1 Weighted Average Ensemble ....................................................................... 398
  - 21.2 Weighted Average Ensemble Case Study ............................................................ 399
  - 21.3 Extensions ............................................................................................ 417
  - 21.4 Further Reading ...................................................................................... 417
  - 21.5 Summary ................................................................................................. 419
- **22 Fit Models on Different Samples with Resampling Ensembles** ...................................... 420
  - 22.1 Resampling Ensembles .............................................................................. 420
  - 22.2 Resampling Ensembles Case Study ................................................................. 422
  - 22.3 Extensions ............................................................................................ 440
  - 22.4 Further Reading ...................................................................................... 441
  - 22.5 Summary ................................................................................................. 442
- **23 Models from Contiguous Epochs with Horizontal Voting Ensembles** ............................... 443
  - 23.1 Horizontal Voting Ensemble ....................................................................... 443
  - 23.2 Horizontal Voting Ensembles Case Study .......................................................... 444
  - 23.3 Extensions ............................................................................................ 456
  - 23.4 Further Reading ...................................................................................... 456
  - 23.5 Summary ................................................................................................. 457
- **24 Cyclic Learning Rate and Snapshot Ensembles** .................................................... 458
  - 24.1 Snapshot Ensembles .................................................................................. 458
  - 24.2 Snapshot Ensembles Case Study .................................................................... 460
  - 24.3 Extensions ............................................................................................ 479
  - 24.4 Further Reading ...................................................................................... 480
  - 24.5 Summary ................................................................................................. 480
- **25 Learn to Combine Predictions with Stacked Generalization Ensemble** ............................ 482
  - 25.1 Stacked Generalization Ensemble ................................................................ 482
  - 25.2 Stacked Generalization Ensemble Case Study ..................................................... 484
  - 25.3 Extensions ............................................................................................ 500
  - 25.4 Further Reading ...................................................................................... 500
  - 25.5 Summary ................................................................................................. 502
- **26 Combine Model Parameters with Average Model Weights Ensemble** ............................... 503
  - 26.1 Average Model Weight Ensemble ................................................................... 503
  - 26.2 Average Model Weight Ensemble Case Study ...................................................... 505
  - 26.3 Extensions ............................................................................................ 523
- 26.4 Further Reading 523
- 26.5 Summary 524

## IV Appendix 525
## A Getting Help 526
### A.1 Applied Neural Networks 526
### A.2 Official Keras Destinations 526
### A.3 Where to Get Help with Keras 527
### A.4 How to Ask Questions 527
### A.5 Contact the Author 528
## B How to Setup Your Workstation 529
### B.1 Overview 529
### B.2 Download Anaconda 529
### B.3 Install Anaconda 531
### B.4 Start and Update Anaconda 533
### B.5 Install Deep Learning Libraries 536
### B.6 Further Reading 537
### B.7 Summary 537
## V Conclusions 538
## How Far You Have Come 539

## Preface
Modern open source libraries for developing neural network models are amazing. Gone are the days where we might spend weeks debugging the translation of poorly documented mathematics into code in the hopes of getting even the simplest model running. Today, using libraries like Keras, we can define and begin fitting a Multilayer Perceptron, Convolutional or even Recurrent Neural Network model of arbitrary complexity in minutes.

While defining and fitting models has become trivial, getting good performance with a neural network model on a specific problem remains challenging. Traditionally, configuring neural networks in order to get good performance was referred to as a *dark art*. This is because there are no clear rules on how to best prepare data and configure a model for a given problem. Instead, experience must be developed over time from working on many different projects. Nevertheless, neural networks have been used in academia and industry for decades now and there are a suite of standard techniques, tips, and configurations that you can use to greatly increase the likelihood of getting better-than-average performance with a neural network model.

I wrote this book to pull together the best classical and modern techniques in order to provide a playbook that you can use to get better performance on your next project using deep learning neural networks. A lot has changed in the last 5 to 10 years and there are activation functions, regularization methods, and even new ensemble methods that result in remarkably faster learning, lower generalization error, and more robust results. I hope that you're as excited as me about the journey ahead.

Jason Brownlee
2019

## Introduction

## Welcome
Welcome to *Better Deep Learning*. Deep learning neural networks have become easy to define and fit, but it remains challenging to achieve good predictive modeling performance. Neural networks have been studied in academia and used in industry for decades, and there is a wealth of techniques, tips, and model configurations that are known to result in better than average performance. In addition, the last 5 to 10 years has seen the development and adoption of modern network configurations, regularization techniques, and ensemble algorithms that result in superior performance. I designed this book to tie together classical and modern techniques into a single playbook and teach you step-by-step how to improve the performance of deep learning neural network models on your predictive modeling problems.

## Who Is This Book For?
Before we get started, let’s make sure you are in the right place. This book is for developers that know some applied machine learning and some deep learning. Maybe you want or need to start using deep learning on your research project or on a project at work. This guide was written to help you do that quickly and efficiently by compressing years of knowledge and experience into a laser-focused course of hands-on tutorials. The lessons in this book assume a few things about you, such as:

- You know your way around basic Python for programming.
- You know your way around basic NumPy for array manipulation.
- You know your way around basic Keras for deep learning.

This guide was written in the top-down and results-first machine learning style that you’re used to from MachineLearningMastery.com.

## About Your Outcomes
This book will teach you how to get results as a machine learning practitioner interested in getting the most out of deep learning models on your own predictive modeling projects. Techniques are demonstrated in the context of small well-understood predictive modeling problems and Multilayer Perceptron neural network models, but can easily be applied to a wide range of problems and with a suite of different types of neural network models. After reading and working through this book, you will know:
