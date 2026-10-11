![image](images/Cover.jpg)

Mastering Computer Vision with PyTorch and Machine Learning

**Caide Xiao**

*University of Calgary, Calgary, Canada*

**IOP** Publishing, Bristol, UK

© IOP Publishing Ltd 2024

This book is available under the terms of the [IOP-Standard Books License](https://publishingsupport.iopscience.iop.org/iop-standard/books)

All rights reserved. No part of this publication may be reproduced, stored in a retrieval system or transmitted in any form or by any means, electronic, mechanical, photocopying, recording or otherwise, without the prior permission of the publisher, or as expressly permitted by law or under terms agreed with the appropriate rights organization. Multiple copying is permitted in accordance with the terms of licences issued by the Copyright Licensing Agency, the Copyright Clearance Centre and other reproduction rights organizations.

Permission to make use of IOP Publishing content other than as set out above may be sought at [permissions@ioppublishing.org](mailto:permissions@ioppublishing.org).

Caide Xiao has asserted his right to be identified as the author of this work in accordance with sections 77 and 78 of the Copyright, Designs and Patents Act 1988.

Supplementary material is available for this book from [https://doi.org/10.1088/978-0-7503-6244-3](https://doi.org/10.1088/978-0-7503-6244-3).

ISBN 978-0-7503-6244-3 (ebook)

ISBN 978-0-7503-6242-9 (print)

ISBN 978-0-7503-6245-0 (myPrint)

ISBN 978-0-7503-6243-6 (mobi)

DOI 10.1088/978-0-7503-6244-3

Version: 20240401

IOP ebooks

British Library Cataloguing-in-Publication Data: A catalogue record for this book is available from the British Library.

Published by IOP Publishing, wholly owned by The Institute of Physics, London

IOP Publishing, No.2 The Distillery, Glassfields, Avon Street, Bristol, BS2 0GR, UK

US Office: IOP Publishing, Inc., 190 North Independence Mall West, Suite 601, Philadelphia, PA 19106, USA

*This book is dedicated to my wife Rongju Sun and my mother Fengying Yin.*

# Contents

[Preface](#Preface.xhtml)

[Acknowledgements](#Acknowledgements.xhtml)

[Author biography](#Author_biography.xhtml#bk978-0-7503-6244-3ch0bio1)

[1 Mathematical tools for computer vision](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1)

[1.1 Probability, entropy and Kullback–Leibler divergence](#Chapter_1.xhtml#sec1.1)

[1.1.1 Probability and Shannon entropy](#Chapter_1.xhtml#sec1.1.1)

[1.1.2 Kullback–Leibler divergence and cross entropy](#Chapter_1.xhtml#sec1.1.2)

[1.1.3 Conditional probability and joint entropies](#Chapter_1.xhtml#sec1.1.3)

[1.1.4 Jensen's inequality](#Chapter_1.xhtml#sec1.1.4)

[1.1.5 Maximum likelihood estimation and over fitting](#Chapter_1.xhtml#sec1.1.5)

[1.1.6 Application of expectation-maximization algorithm to find a PDF](#Chapter_1.xhtml#sec1.1.6)

[1.2 Using a gradient descent algorithm for linear regression](#Chapter_1.xhtml#sec1.2)

[1.3 Automatic gradient calculations and learning rate schedulers](#Chapter_1.xhtml#sec1.3)

[1.4 Dataset, dataloader, GPU and models saving](#Chapter_1.xhtml#sec1.4)

[1.5 Activation functions for nonlinear regressions](#Chapter_1.xhtml#sec1.5)

[References](#Chapter_1.xhtml#ST24)

[2 Image classifications by convolutional neural networks](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2)

[2.1 Classification of hand written digits in the MNIST database](#Chapter_2.xhtml#sec2.1)

[2.2 Mathematical operations of a 2D convolution](#Chapter_2.xhtml#sec2.2)

[2.3 Using ResNet9 for CIFAR-10 classification](#Chapter_2.xhtml#sec2.3)

[2.4 Transfer learning with ResNet for a dataset of Vegetable Images](#Chapter_2.xhtml#sec2.4)

[References](#Chapter_2.xhtml#ST31)

[3 Image generation by GANs](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3)

[3.1 The GAN theory](#Chapter_3.xhtml#sec3.1)

[3.1.1 Implement a GAN for quadratic curve generation](#Chapter_3.xhtml#sec3.1.1)

[3.1.2 Using a GAN with two fully connected layers to generate MINST Images](#Chapter_3.xhtml#sec3.1.2)

[3.2 Applications of deep convolutional GANs](#Chapter_3.xhtml#sec3.2)

[3.2.1 Mathematical operations of ConvTranspose2D](#Chapter_3.xhtml#sec3.2.1)

[3.2.2 Applications of a DCGAN for MNIST and fashion MNIST](#Chapter_3.xhtml#sec3.2.2)

[3.2.3 Using a DCGAN to generate fake anime-faces and fake CelebA images](#Chapter_3.xhtml#sec3.2.3)

[3.3 Conditional deep convolutional GANs](#Chapter_3.xhtml#sec3.3)

[3.3.1 Applications of a cDCGAN to MNIST and fashion MNIST datasets](#Chapter_3.xhtml#sec3.3.1)

[3.3.2 Applications of a cDCGAN to generate fake Rock Paper Scissors images](#Chapter_3.xhtml#sec3.3.2)

[References](#Chapter_3.xhtml#ST44)

[4 Image generation by WGANs with gradient penalty](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4)

[4.1 Using a WGAN or a WGAN-GP for generation of fake quadratic curves](#Chapter_4.xhtml#sec4.1)

[4.2 Using a WGAN-GP for Fashion MNIST](#Chapter_4.xhtml#sec4.2)

[4.3 WGAN-GP for CelebA dataset and Anime Face dataset](#Chapter_4.xhtml#sec4.3)

[4.4 Implementation of a cWGAN-GP for Rock Paper Scissors dataset](#Chapter_4.xhtml#sec4.4)

[References](#Chapter_4.xhtml#ST51)

[5 Image generation by VAEs](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5)

[5.1 VAE and beta-VAE](#Chapter_5.xhtml#sec5.1)

[5.2 Application of beta-VAE for fake quadratic curves](#Chapter_5.xhtml#sec5.2)

[5.3 Application of beta-VAE for the MNIST dataset](#Chapter_5.xhtml#sec5.3)

[5.4 Using VAE-GAN for MNIST, Fashion MNIST & Anime-Face Dataset](#Chapter_5.xhtml#sec5.4)

[References](#Chapter_5.xhtml#ST58)

[6 Image generation by infoGANs](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6)

[6.1 Using infoGAN to generate quadratic curves](#Chapter_6.xhtml#sec6.1)

[6.2 Implementation of infoGAN for the MNIST dataset](#Chapter_6.xhtml#sec6.2)

[6.3 infoGAN for fake Anime-face dataset images](#Chapter_6.xhtml#sec6.3)

[6.4 Implementation of infoGAN to the rock paper scissors dataset](#Chapter_6.xhtml#sec6.4)

[Reference](#Chapter_6.xhtml#ST66)

[7 Object detection by YOLOv1/YOLOv3 models](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7)

[7.1 Bounding boxes of Pascal VOC database for YOLOv1](#Chapter_7.xhtml#sec7.1)

[7.2 Encode VOC images with bounding boxes for YOLOv1](#Chapter_7.xhtml#sec7.2)

[7.2.1 VOC image augmentations with bounding boxes](#Chapter_7.xhtml#sec7.2.1)

[7.2.2 Encoding bounding boxes to grid cells for YOLOv1 model training](#Chapter_7.xhtml#sec7.2.2)

[7.2.3 Chess pieces dataset from Roboflow](#Chapter_7.xhtml#sec7.2.3)

[7.3 ResNet18 model, IOU and a loss function](#Chapter_7.xhtml#sec7.3)

[7.3.1 Using ResNet18 to replace YOLOv1 model](#Chapter_7.xhtml#sec7.3.1)

[7.3.2 Intersection over union (IOU) and the loss function](#Chapter_7.xhtml#sec7.3.2)

[7.4 Utility functions for model training](#Chapter_7.xhtml#sec7.4)

[7.5 Applications of YOLOv3 for real-time object detection](#Chapter_7.xhtml#sec7.5)

[References](#Chapter_7.xhtml#ST79)

[8 YOLOv7, YOLOv8, YOLOv9 and YOLO-World](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8)

[8.1 YOLOv7 for object detection for a custom dataset: MNIST4yolo](#Chapter_8.xhtml#sec8.1)

[8.2 YOLOv7 for instance segmentation](#Chapter_8.xhtml#sec8.2)

[8.3 Using YOLOv7 for human pose estimation (key point detection)](#Chapter_8.xhtml#sec8.3)

[8.4 Applications of YOLOv8, YOLOv9 and YOLO-World models](#Chapter_8.xhtml#sec8.4)

[8.4.1 Image object detection, segmentation, classification and pose estimation](#Chapter_8.xhtml#sec8.4.1)

[8.4.2 Object counting on an image or a video frame](#Chapter_8.xhtml#sec8.4.2)

[8.4.3 Car tracking and counting for a video file](#Chapter_8.xhtml#sec8.4.3)

[8.4.4 Fine tuning YOLOv8 for objection detection and annotation for a custom dataset](#Chapter_8.xhtml#sec8.4.4)

[References](#Chapter_8.xhtml#ST90)

[9 U-Nets for image segmentation and diffusion models for image generation](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9)

[9.1 Retinal vessel segmentation by a U-Net for DRIVE dataset](#Chapter_9.xhtml#sec9.1)

[9.2 Using an attention U-Net diffusion model for quadratic curve generation](#Chapter_9.xhtml#sec9.2)

[9.2.1 The forward process in a DDPM](#Chapter_9.xhtml#sec9.2.1)

[9.2.2 The backward process in the DDPM](#Chapter_9.xhtml#sec9.2.2)

[9.3 Using a pre-trained U-Net from Hugging Face to generate images](#Chapter_9.xhtml#sec9.3)

[9.4 Generate photorealistic images from text prompts by stable diffusion](#Chapter_9.xhtml#sec9.4)

[References](#Chapter_9.xhtml#ST99)

[10 Applications of vision transformers](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10)

[10.1 The architecture of a basic ViT model](#Chapter_10.xhtml#sec10.1)

[10.2 Hugging Face ViT for CIFAR10 image classification](#Chapter_10.xhtml#sec10.2)

[10.3 Zero shot image classification by OpenAI CLIP](#Chapter_10.xhtml#sec10.3)

[10.4 Zero shot object detection by Hugging Face's OWL-ViT](#Chapter_10.xhtml#sec10.4)

[10.5 RT-DETR (a vision transformers-based real-time object detector)](#Chapter_10.xhtml#sec10.5)

[References](#Chapter_10.xhtml#ST107)

[11 Knowledge distillation and its applications in DINO and SAM](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11)

[11.1 Knowledge distillation for neural network compression](#Chapter_11.xhtml#sec11.1)

[11.2 DINO: emerging properties in self-supervised vision transformers](#Chapter_11.xhtml#sec11.2)

[11.3 DINOv2 for image retrieval, classification and feature visualization](#Chapter_11.xhtml#sec11.3)

[11.4 Segment anything model: SAM and FastSAM](#Chapter_11.xhtml#sec11.4)

[References](#Chapter_11.xhtml#ST114)

[12 Applications of NeRF and 3D Gaussian splatting for synthesis of 3D scenes](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12)

[12.1 Using MiDaS for image depth estimation](#Chapter_12.xhtml#sec12.1)

[12.2 Neural Radiance Fields (NeRF) for synthesis of 3D scenes](#Chapter_12.xhtml#sec12.2)

[12.2.1 Camera intrinsic and extrinsic matrices](#Chapter_12.xhtml#sec12.2.1)

[12.2.2 Using MLP with Gaussian Fourier feature mapping to reconstruct images](#Chapter_12.xhtml#sec12.2.2)

[12.2.3 The physics principle of render volume density in NeRF](#Chapter_12.xhtml#sec12.2.3)

[12.3 Introduce 3D Gaussian splatting by 2D Gaussian splatting](#Chapter_12.xhtml#sec12.3)

[References](#Chapter_12.xhtml#ST123)

[Appendix](#Appendix1.xhtml)

# Preface

### What this book is about

*Mastering Computer Vision with Pytorch and Machine Learning* is a book which provides a thorough and extensive guide for mastering advanced computer vision techniques for image processing by using Python and PyTorch from the ground up. Computer vision is a field of artificial intelligence and computer science that focuses on enabling computers to interpret and understand visual information from the world around them. Computer vision and machine learning are closely related fields. Machine learning is used in computer vision to enable computers to automatically find patterns and relationships in large datasets of images and videos. With a focus on practical applications, this book covers essential concepts such as Kullback Leibler divergence, maximum likelihood, convolutional neural networks (CNN), generative adversarial networks (GAN), Wasserstein generative adversarial networks (WGAN), WGAN with gradient penalty (WGAN-GP), information maximizing generative adversarial networks (infoGAN), variational autoencoders (VAE), and their applications for image classification/image generation. Readers will also learn how to leverage the latest computer vision techniques like Yolov8 for object detection, stable diffusion models for image generation, vision transformers for zero-shot object detection, knowledge distillation for compression of neural networks, DINO for self-supervised learning, segment anything models (SAM), NeRF and 3D Gaussian Splatting for 3D scenes synthesis. This book is a valuable resource for professionals, researchers, and students who want to expand their knowledge of advanced computer vision techniques using PyTorch. With clear explanations, practical examples, and real-world use cases, readers will learn how to apply computer vision techniques to image analysis tasks, and develop skills necessary to build and train their own models for advanced image analysis. Whether you are a beginner or an experienced data scientist, this book will provide you with the knowledge and tools you need to succeed.

### Prerequisites to readers

Computer vision projects use neural network models or vision transformers as mathematical functions to process images. The outputs of these functions could be integers for image classification, or new images similar to images in train datasets for image generation, or bounding boxes with class identities and probabilities for objection detection. Neural networks in models are mathematical operators organized in special sequences. Large-scale computer vision models may have billions of parameters to learn from training datasets. Model training time is dependent on the sizes of the input data, Python codes, and computer hardware to process the data. This book is written for readers with linear algebra knowledge about matrix calculations and basic ideas about statistics. With such mathematics background, readers can write their codes even they have no idea about Python which is a simple yet powerful programming language with excellent functionality for machine learning. Kaggle and Google Colab provide free GPUs for any people with a Google account. In those two free internet platforms, powerful computer hardware and software are ready to use. Most codes listed in the book can run on either of the two free internet platforms. Readers do not need to buy expensive computers.

Because of some limits in Kaggle and Google Colab, it's better to have your own computer with the following open-source software. The first is Microsoft Visual Studio Code (VS Code). It is a free code editor provided by Microsoft for Windows, Linux, and macOS. It has many features and extensions for editing, debugging, and developing codes in many programming languages. It is a popular choice for people of all skill levels due to its ease of use, customizability, and community-driven development. In a VS Code terminal, we can then install many extensions, such as Python, Jupyter notebook, PyTorch, Torchvision, NumPy, Pandas, Matplotlib, OpenCV, tqdm, and more. The development of computer science is very fast. We need to have more than one virtual workspace in VS Code for different versions of Python and other libraries. Most codes in the book can run with Python v3.6, and many codes in the last six chapters must run with Python v3.9 to v3.11 for the latest computer vision techniques, such as Ultralytics Yolov7 to Yolov9, Hugging Face zero-shot object detection, Facebook DINO and SAM.

### Structure of the book

There are twelve chapters in this book. Chapter [1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1) introduces mathematical concepts and tools about computer vision and machine learning; these are probability, maximum likelihood, Shannon entropy, gradients, activation functions, loss functions, datasets, dataloaders and learning rate etc. Nine pairs of numbers about Celsius and Fahrenheit temperature conversion are used in different projects of this chapter to introduce those mathematical concepts step by step. Chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2) introduces deep convolution neuron networks for image classifications of three datasets: MNIST, CIFAR10 and Vegetable Images. These are supervised learning projects where models learn to make predictions based on labeled training data. Chapters [3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3)–[6](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6) are about image generation with different algorithms: GANs, VAEs, WGANs, and infoGANs. Using conditional GANs, infoGANs, VAEs, or VAE-GANs, we can generate the desired images with special styles. VAEs and infoGANs are used in unsupervised learning projects. The main advantage of unsupervised learning is that it can be used to uncover hidden patterns and structure in data without any prior knowledge or labeled data.

Codes in all projects listed in the book are in the same style with four parts: data input, data display, data process and output data visualization. A simple dataset for quadratic curve generation is used in chapters [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2)–[9](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9) to help readers understand complex algorithms in new models. In many projects, readers only need to focus on the third part which is about how to construct and use models to process data. Chapters [7](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7)–[12](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12) introduce the latest computer vision techniques (up to February of 2024) for image classification, image generation, object detection, object segmentation and synthesis of 3D scenes. YOLOv8 from Ultralytics is one of the latest techniques for object detection and segmentation. It is easy to install and use for image analysis tasks. OpenAI, Hugging Face, Meta AI and Intelligent Systems Lab provide us with new tools for image analysis. With their libraries, we only need to write codes in a few lines to generate photo-realistic images, to detect/segment/classify objects, to retrieve images, and to estimate image relative depth without model training (zero-shot). The last chapter is about synthesis of 3D scenes by NeRF or 3D Gaussian splatting. Many detailed mathematics derivations are put in the appendices. Many extra project codes can also be found in the appendices.

### Keywords

Computer vision, Machine Learning, Kullback Leibler Divergence, maximum likelihood, PyTorch, CNN, GAN, WGAN, WGAN-GP, infoGAN, VAE, image classification, object detection, image segmentation, image generation, image retrieve, YOLO, U-Net, Stable Diffusion, zero-shot, ViT, Knowledge Distillation, DINO, SAM, fastSAM, MiDaS, NeRF, 3D scenes and 3D Gaussian Splatting.

# Acknowledgements

I wish to express my sincere appreciation to the professional editors of the Institute of Physics Publishing (IOPP) Ltd. They are Senior Commissioning Manager John Navas, eBooks Coordinator Phebe Hooper and Production Editor Chris Benson. It would have been almost impossible to finish the book in two years without my wife Rongju Sun’s support and patience. I also received help about subjects in the book from my PhD supervisor, Professor Senfang Sui. In the early 1980s, I began to learn to write computer codes in BASIC. Comparing with other computer languages such as BASIC, Fortran, Java, C, I found Python is the best. It is free (open source) for people, and it is easy to use if you know English words and Algebra. Many smart people publicly released their Python and Pytorch libraries for people to use. These free libraries are just like transistors, capacitors, inductors and resistors in electronics. We can use them to construct computer vision models which would work day and night to generate photorealistic images. Many kind people have published their Python codes on GitHub, and even teach people how to use their codes by YouTube videos. Many of my codes in the book were inspired by these people. I have much to thank those teachers for in the great YouTube University on Earth, and can only mention some of them: Dr Sreenivas Bhattiprolu (DigitalSreeni), Aladdin Persson, Aarohi Singla, FreedomWebTech, Rob Mulla and OutofAi. Many free and publicly available image datasets and pre-trained weights files were used in computer vision projects of this book. They were generated by Torchvision, Hugging Face, Roboflow, OpenAI, Meta AI. Professor Ziwei Liu gave me permission to use CelebA dataset, and Dr Alex Krizhevsky gave me permission to use CIFA10 dataset in the book.

# Author biography

Dr Caide Xiao

![](images/bk978-0-7503-6244-3ch0f1_online.jpg)

**Dr Caide Xiao** was born on 25 October 1961. He was a physics teacher at Yunyang Medical College in China after he received his Batchelor degree in 1983 from the Physics Department of Central China Normal University in Wuhan, where he learnt to write computer codes on Apple II. From 1990 to 1996, he was a postgraduate student in Professor Senfang Sui's laboratory for optical biosensors in Tsinghua University, Beijing. Then he worked as a visiting scholar in many Biophysics laboratories in Italy, Canada and United States of America. Now, he has established his home in Calgary, Canada. Many photos in the book came from Calgary Stampede Parades and Banff National Park.

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 1

## Mathematical tools for computer vision

This chapter is about mathematical tools and a Python/PyTorch platform for computer vision projects. Section [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1s1-1) introduces some mathematical concepts about information entropy, statistics probability distribution functions, Kullback–Leibler divergence, Jensen's inequality and an overfitting issue in nonlinear regression. The remaining four sections are about the gradient descent algorithm for model training in machine learning, Python/PyTorch libraries (tools) for datasets, dataloaders, activation functions, GPU usage and model training/saving. A simple data file is used many times in this chapter to introduce these concepts and libraries.

Humans have the ability to imagine, create and build new things that have never existed before. The ability to innovate and invent is one of the key characteristics of human intelligence and has led to significant advancements in various fields, such as science, technology, engineering and the arts. We build skyscrapers in cities to live in, make cellphones to keep in our pockets for communication and launch rockets to carry satellites to the edge of our solar system to explore our universe. All these engineering achievements are based on laws of physics and mathematics, such as Newton's law of universal gravitation, Maxwell's electromagnetic law, Einstein's theory of relativity, quantum mechanics, etc. These laws are the foundations of our civilization. They are keys for us to understand and modify our world. However, knowing these physics and mathematics laws is not enough, experts or professionals also have to do work based on their experiences. Those experiences come from life-time practices. Once, when an expert passed away, all of the experiences of that expert were lost. Now it is possible for professionals to train computers with machine learning algorithms, so that human experiences can be inherited and stored in computers forever. The goal of computer vision research is to enable computers to have humanlike perception capabilities. Machine learning is a branch of artificial intelligence (AI) that deals with the development of algorithms and statistical models. Machine learning allows computers to 'learn' from data without being explicitly programmed. In machine learning, models based on algorithms are trained on datasets to find patterns in the datasets to predict new data. There are several types of machine learning, including supervised learning, unsupervised learning, semi-supervised learning, and reinforcement learning, each having a unique set of algorithms and approaches.

### 1.1 Probability, entropy and Kullback–Leibler divergence

Images are composed of pixels, which are minuscule dots on a screen. When numerous pixels are arranged in a specific configuration (pattern), they form an image. The resolution of an image is determined by the number of pixels it contains. Higher image resolutions give us clearer and more detailed visuals. From the pattern or probability of an image's pixels distributed in a space, we can generate new images. To begin our study of computer vision, it is essential to embrace the concept of statistics, particularly probability. Utilizing the Bayesian probability theorem and Shannon's information entropy theory, we can derive loss functions for model training. These models would be so smart that they can not only tell us if there are dogs or cats in an image, but also can generate photorealistic images/videos according to our text prompts.

#### 1.1.1 Probability and Shannon entropy

To a fair coin, its ‘head’ and ‘tail’ sides have the same probability (50%) to appear when you toss it. In the coin system, we have a discrete random variable *X* within a space of {‘head’, ‘tail’}, and its probability mass function (PMD) is *P*(*X*) = {1/2, 1/2}. In case when a coin is not fair, its head probability is *p* = 0.45, and we toss the coin ten times (*n* = 10), what is the probability of getting four heads (*x* = 4)? This unfair coin system has a discrete random variable *X* within a space of {0, 1, …, 10} with the binomial dstribution function. Taking those parameters into equation ([1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn1)), you will obtain the answer: 23.8%.

  
$$P\\left( {X = x} \\right) = \\frac{n!}{x!\\left( {n - x} \\right)!}p^{x}\\left( {1 - p} \\right)^{n - x}$$  
(1.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn1.gif" position="float"/

The height variable (*X*) of our bodies is a continuous random number with a Gaussian distribution function which is the most important probability density function (PDF) for machine learning. Although probability density functions of many image datasets are too complex to write down explicitly, we can still try to use Gaussian distribution functions to approximate them.

  
$$P\\left( {X = x} \\right) = N\\left( {x;\\mu,\\sigma^{2}} \\right) = \\frac{1}{\\sqrt{2\\pi\\sigma^{2}}}e^{- \\frac{1}{2}{(\\frac{x - \\mu}{\\sigma})}^{2}}$$  
(1.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn2.gif" position="float"/

In equation ([1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn2)), *μ* is the **mean** or expected value of *X*, *σ* is the standard deviation of *X* and *σ*² is the **variance** of *X*. For any random variable *X* with a known PDF, its expected value *E*[*p*]\[*X*\] and variance *E*[*p*]\[(*X-μ*)²\] are:

  
$$\\mu = \\sum\\limits\_{i = 1}^{n}x\_{i}p\\left( x\_{i} \\right)\\begin{matrix} \\mathit{or} \\\\ \\left. \\ \\rightarrow\\mspace{2mu} \\right. \\\\ \\end{matrix}\\int\_{- \\infty}^{\\infty}{\\mathit{xp}\\left( x \\right)\\mathit{dx}}$$  
(1.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn3.gif" position="float"/

  
$${\\sigma^{2} = \\sum\\limits\_{i = 1}^{n}{(x\_{i}} - \\mu)}^{2}p\\left( x\_{i} \\right)\\begin{matrix} {\\ \\mathit{or}\\ } \\\\ \\left. \\ \\rightarrow\\ \\right. \\\\ \\end{matrix}\\int\_{- \\infty}^{\\infty}{\\left( {x - \\mu} \\right)^{2}p\\left( x \\right)\\mathit{dx}}$$  
(1.4)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn4.gif" position="float"/

 

Shannon ‘**Entropy**' of information is the 'amount of information' contained in a random variable, or the minimum bits to encode information of a system.

  
$$H\\left( { p} \\right) = - \\sum\\limits\_{i = 1}^{n}{p\_{i}{\\ \\log}\_{2}\\left( p\_{i} \\right)}\\begin{matrix} {\\ \\mathit{or}\\ } \\\\ \\left. \\ \\rightarrow\\ \\right. \\\\ \\end{matrix} - \\int\_{- \\infty}^{\\infty}{p\\left( x \\right){\\ \\log}\_{2}p\\left( x \\right)\\mathit{dx}}$$  
(1.5)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn5.gif" position="float"/

A fair coin system's entropy is $H\\left( { p} \\right) = - 2\\frac{1}{2}{\\ \\log}\_{2}\\left( \\frac{1}{2} \\right) = 1$inline-graphic style="height:2.0625em;" xlink:href="bk978-0-7503-6244-3ch1ieqn6.gif"/ bit, and a fair dice system's entropy is $H\\left( { p} \\right) = - 6\\frac{1}{6}{\\ \\log}\_{2}\\left( \\frac{1}{6} \\right) = 2.585$inline-graphic style="height:2.0625em;" xlink:href="bk978-0-7503-6244-3ch1ieqn7.gif"/ bits. For mathematical convenience in machine learning, we usually use natural logarithm, and the entropy unit is ‘nit’. The coin's entropy and the dice's entropy are 0.69 nits and 1.79 nits respectively.

#### 1.1.2 Kullback–Leibler divergence and cross entropy

In the case where there are two distribution functions *p* and *q* for a same random variable *X*, their log likelihood ratio is a function $f\\left( x \\right) = \\ln\\ \\left\\lbrack \\frac{ p\\left( x \\right)}{q\\left( x \\right)} \\right\\rbrack$inline-graphic style="height:2.3125em;" xlink:href="bk978-0-7503-6244-3ch1ieqn8.gif"/. The expected value of the log likelihood ratio is called **Kullback–Leibler divergence** (*D*[KL]):

  
$$D\_{KL}( p{\\mid\\mid}q) = E\_{p}\\left\\lbrack {\\ln\\ \\frac{p\\left( X \\right)}{q\\left( X \\right)}} \\right\\rbrack = \\sum\\limits\_{i = 1}^{n}{p\\left( x\_{i} \\right)\\ \\ln\\ \\frac{p\\left( x\_{i} \\right)}{q\\left( x\_{i} \\right)}}$$  
(1.6)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn9.gif" position="float"/

*D*[KL] is used to measure the difference between two PDFs of a system with the same random variable *X*. If *p* and *q* are the same, we have *D*[KL] *\=* 0. Cross entropy is another index to quantify the difference between two PDFs, and it is often used as a loss function in machine learning.

  
$$H( p,q) = - \\sum\\limits\_{i = 1}^{n}{p\\left( x\_{i} \\right)\\ \\ln\\ \\left( {q\\left( x\_{i} \\right)} \\right)} = D\_{KL}( p{\\mid\\mid}q) + H\\left( { p} \\right)$$  
(1.7)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn10.gif" position="float"/

The following scenario is used to enable us to understand these formulae. On a big desk in a casino, a coin is used as a gambling machine. At the beginning of a game, a gambler asks to verify if the coin is fair and the request is permitted. The target PMD is *P*(*X*) = {1/2, 1/2}. After tossing the coin 10 000 times, the gambler finds the real PMD is *Q*(*X*) = {0.65, 0.35}. The *D*[KL] of the two distributions is *D*[KL] = 0.5ln(0.5/0. 65)+0.5ln(0.5/0. 35) = 0.047; and the cross entropy is obtained with *H*(*p,q*) = −0.5ln(0.65)−0.5ln(0.35) = 0.740. With the fair coin's entropy *H*(*p*) = 0.693 nit, we would be sure that equation ([1.7](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn7)) is correct. When two distributions of a system are the same, their cross entropy has the minimum value: *H*(*p*). That is why cross entropy can be used as a loss function in model training for machine learning.

Kullback–Leibler divergence is not symmetry: *D*[KL](*p∣∣q*) *≠ D*[KL](*q∣∣p*), and it is a positive number: *D*[KL](*p∣∣q*) ⩾ 0. The first property is obvious, and the second property can be proved with (*x*−1) ⩾ ln(*x*) in a condition *x* ⩾ 0. Based on this information, we have \[*q*(*x*)*/p*(*x*)−1\] ⩾ ln\[*q*(*x*)*/p*(*x*)\] or −ln\[*q*(*x*)*/p*(*x*)\] ⩾−\[*q*(*x*)*/p*(*x*)-1\], and then we get:

  
$$D\_{KL}( p{\\mid\\mid}q) = - \\int\\limits\_{x}{p\\left( x \\right)}\\ \\ln\\ \\left( \\frac{q\\left( x \\right)}{p\\left( x \\right)} \\right)\\mathit{dx} \\geqslant - \\int\\limits\_{x}{p\\left( x \\right)}\\left( {\\frac{q\\left( x \\right)}{p\\left( x \\right)} - 1} \\right)\\mathit{dx} = 0$$  
graphic style="width:27.5625em;" xlink:href="bk978-0-7503-6244-3ch1ueqn11.gif" position="float"/

**Jensen–Shannon divergence** (*D*[JS]) is a symmetry divergence. You can calculate the *D*[JS] of the unfair coin found by the gambler with equation ([1.8](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn8)) (using a discrete sum but not by an integration), and it should be 0.0128 nit. It is obvious that we have 0 *⩽ D*[JS](*p∣∣q*) ⩽ ln(2). By replacing both *p*/(*p+q*) and *q*/(*p+q*) with 1.0 in the following equation, you can prove it, because those two fractions are less than 1.0

  
$$D\_{JS}( p{\\mid \\mid}q) = \\frac{1}{2}\\int\\left( { p\\left( x \\right){\\ \\ln\\ }\\left( \\frac{2p\\left( x \\right)}{p\\left( x \\right) + q\\left( x \\right)} \\right) + q\\left( x \\right){\\ \\ln\\ }\\left( \\frac{2q\\left( x \\right)}{p\\left( x \\right) + q\\left( x \\right)} \\right)} \\right)\\mathit{dx}$$  
(1.8)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn12.gif" position="float"/

We know the univariate Gaussian distributions from equation ([1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn2)). In computer vision projects, we also need to use **multivariate normal distributions** to create fake images. For mathematical convenience, we just handle a multivariate normal distribution system with three independent random variables *x*[1], *x*[2] and *x*[3] whose means are *μ*[1], *μ*[2] and *μ*[3] and standard deviations are *σ*[1], *σ*[2] and *σ*[3] respectively. Their variances construct a diagonal matrix Σ whose inverse matrix is Σ^(\-1)

  
$$X = \\begin{bmatrix} x\_{1} \\\\ x\_{2} \\\\ x\_{3} \\\\ \\end{bmatrix}\\mspace{22mu}\\Sigma = \\begin{bmatrix} \\sigma\_{1}^{2} & 0 & 0 \\\\ 0 & \\sigma\_{2}^{2} & 0 \\\\ 0 & 0 & \\sigma\_{3}^{2} \\\\ \\end{bmatrix}\\mspace{22mu}\\Sigma^{- 1} = \\begin{bmatrix} \\frac{1}{\\sigma\_{1}^{2}} & 0 & 0 \\\\ 0 & \\frac{1}{\\sigma\_{2}^{2}} & 0 \\\\ 0 & 0 & \\frac{1}{\\sigma\_{3}^{2}} \\\\ \\end{bmatrix}\\mspace{22mu}{\\mid\\Sigma\\mid}^{1/2} = \\left( {\\sigma\_{1}^{2}\\sigma\_{2}^{2}\\sigma\_{3}^{2}} \\right)^{1/2}$$  
graphic style="width:32.8125em;" xlink:href="bk978-0-7503-6244-3ch1ueqn13.gif" position="float"/

  
$$p\\left( {X = x} \\right) = \\prod\\limits\_{i = 1}^{3}{N\\left( {x\_{i};\\mu\_{i},\\sigma\_{i}^{2}} \\right)} = \\frac{1}{\\left( {2\\pi} \\right)^{3/2}\\mid\\Sigma\\mid^{1/2}}e^{- \\frac{1}{2}{({x - \\mu})}^{T}\\Sigma^{- 1}{({x - \\mu})}}$$  
(1.9)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn14.gif" position="float"/

If there is another multivariate normal distribution *q*(*X* = *x*) whose means are zeros and the Σ matrix is a 3 × 3 identity matrix I, it is not difficult to obtain *D*[KL](*p∣∣q*) with all the above information (appendix [A](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-A))

  
$$D\_{KL}( p{\\mid\\mid}q) = \\frac{1}{2}\\sum\\limits\_{i = 1}^{3}\\left\\lbrack {\\mu\_{i}^{2} + \\sigma\_{i}^{2} - 1 - \\ln\\ \\left( \\sigma\_{i}^{2} \\right)} \\right\\rbrack$$  
(1.10)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn15.gif" position="float"/

#### 1.1.3 Conditional probability and joint entropies

Sometimes there are two or more random variables in a system. Each of them has its own PDF. These variables combine together to create a joint PDF. For example, in a gamble machine there is a fair coin and fair dice, and they are independent. The dice number variable is *X* with a uniform probability mass function *P*(*X*) = {1/6, 1/6, 1/6, 1/6, 1/6, 1/6}; a variable about the coin's sides is *Y* with another uniform probability mass function *P*(*Y*) = {1/2, 1/2}. The joint PDF of the coin and the dice is also a uniform probability distribution *P*(*X,Y*) with twelve statuses, and the probability of any status is equal to 1/12 as shown in table [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t1).

**Table 1.1.** Joint probabilities *P*(*X,Y*) of a system with a fair coin and fair dice.

| *P*(*X*,*Y*)  || Dice numbers (*X*) ||  |
| --- | --- | --- |
| Coin side(*Y*) || One(*x*[1]) || Two(*x*[2]) || Three(*x*[3]) || Four(*x*[4]) || Five(*x*[5]) || Six(*x*[6]) || *P*(*Y*) |
| Head(*y*[1]) || 1/12 || 1/12 || 1/12 || 1/12 || 1/12 || 1/12 || 1/2 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Tail(*y*[2]) || 1/12 || 1/12 || 1/12 || 1/12 || 1/12 || 1/12 || 1/2 |
| *P*(*X*) || 1/6 || 1/6 || 1/6 || 1/6 || 1/6 || 1/6 || 1 |

The sum of the six joint probabilities *p*(*x*[*i*], *y*[1]) on the first row titled ‘Head(*y*[1])’ is equal to *p*(*y*[1]) = 1/2, and the sum of other six joint probabilities *p*(*x*[*i*], *y*[2]) on the second row for ‘Tail(*y*[2])’ is *p*(*y*[2]) = 1/2, where *i* = 1,2,…,6. The coin's PMF *P*(*Y*) is constructed by the two numbers in a 1D array: *P*(*Y*) = {*p*(*y*[1]), p(*y*[1])}. The sum of a column titled ‘One(*x*[1])’ is *p*(*x*[1]) = 1/6. The sum of each of the rest five columns is also equal to *p*(*x*[*i*]) = 1/6 where *i* = 2, 3, …, 6. The dice's PMF *P*(*X*) is constructed by the six numbers in a 1D array: *P*(*X*) = {*p*(*x*[1]), *p*(*x*[2]), …, *p*(*x*[6])}. The sum of all the 12 joint probabilities *p*(*x*[*i*], *y*[*j*]), the sum of the dice's six probabilities *p*(*x*[*i*]) and the sum of the coin's two probabilities *p*(*y*[*j*]) are all equal to one (*i* = 1,2,…,6, *j* = 1,2). *P*(*X*) and *P*(*Y*) are marginal probabilities.

A conditional probability of an event *Y* is the coin's probability when a dice event *X* has already happened or is known. It is written as *P*(*Y*∣*X*) for the probability of *Y* given *X*. For example, the dice was tossed with the digit five on its top, and then the coin will be tossed. The conditional probabilities of the coin are still half and half: *p*(*y*[1]∣*x*[*i*] = 5) = ½ and *p*(*y*[2]∣*x*[*i*] = 5) = ½ as shown in table [1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t2). The conditional probability table *P*(*Y*∣*X*) could be obtained by normalizations of each of the six columns in table [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t1) by a *P*(*X*) element at the bottom of the joint *P*(*X*,*Y*) table respectively. Each of the 12 elements in the *P*(*Y*∣*X*) table [1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t2) is the same: ½. A conditional probability table *P*(*X*∣*Y*) could also be obtained by normalizations of each of the two rows of the joint *P*(*X*,*Y*) table by a *P*(*Y*) element on the right side respectively. Each of the 12 elements of the *P*(*X*∣*Y*) table [1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t3) is also the same: 1/6 as shown in table [1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t3). According to **Bayes' theorem**, the element-wise relationship among *p*(*x,y*), *p*(*x*∣*y*), *p*(*y*∣*x*), *p*(*x*) and *p*(*y*) is set by equation ([1.11](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn11)).

  
$$p\\left( { y \\mid x} \\right) = \\frac{p\\left( {x,y} \\right)}{p\\left( x \\right)} = \\frac{p\\left( {x \\mid y} \\right)}{p\\left( x \\right)}p\\left( { y} \\right)$$  
(1.11)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn16.gif" position="float"/

**Table 1.2.** Conditional possibilities *P*(*Y∣X*).

| *P*(*Y∣X*)  || Dice numbers (*X*) |
| --- | --- |
| Coin side (*Y*) || One (*x*[1]) || Two (*x*[2]) || Three (*x*[3]) || Four (*x*[4]) || Five (*x*[5]) || Six (*x*[6]) |
| Head(*y*[1]) || 1/2 || 1/2 || 1/2 || 1/2 || 1/2 || 1/2 |
| --- | --- | --- | --- | --- | --- | --- |
| Tail (y[2]) || 1/2 || 1/2 || 1/2 || 1/2 || 1/2 || 1/2 |

**Table 1.3.** Conditional possibilities *P*(*X∣Y*).

| *P*(*X∣Y*)  || Dice numbers(*X*) |
| --- | --- |
| Coin side (*Y*) || One (*x*[1]) || Two (*x*[2]) || Three (*x*[3]) || Four (*x*[4]) || Five (*x*[5]) || Six (*x*[6]) |
| Head (*y*[1]) || 1/6 || 1/6 || 1/6 || 1/6 || 1/6 || 1/6 |
| --- | --- | --- | --- | --- | --- | --- |
| Tail (y[2]) || 1/6 || 1/6 || 1/6 || 1/6 || 1/6 || 1/6 |

In the above formula, *p*(*x*) and *p*(*y*) are marginal probabilities or prior probabilities, *p*(*x*∣*y*) is the likelihood of *x* given *y*, and *p*(*y*∣*x*) is the posterior probability of *y* given *x*. I use the following example to explain these probability names. Among the people on a small island, 55% (= *p*(*x*[1])) are women and 45% (= *p*(*x*[2])) are men. Among those women, 10% (= *p*(*y*[1]∣*x*[1])) are smokers, and among the men, 30% (= *p*(*y*[1]∣*x*[2])) are smokers. The variables for smokers and non-smokers are *y*[1] and *y*[2] respectively. From the sound and the smell in the air, you know a person is smoking. What is the probability that the smoker is a woman? To answer this question, we need to construct a posterior probability *P*(*X*∣*Y*) sub-table shown by three columns on the right side of in table [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t4) based on the above data. We start our work from a likelihood sub-table about *P*(*Y*∣*X*) constructed by the three columns on the left side of the table. Values in cells of the row ‘Smokers(*y*[1])’ and in cells of the marginal *P*(*X*) row are known. Values in cells of the row ‘Non-smokers(*y*[2])’ are obtained logically. Among women on the island, 90% are non-smokers, and among men, 70% are non-smokers.

**Table 1.4.** Probabilities of smokers among men and women on an island.

| *P*(*Y*∣*X*) || Women (*x*[[1]]) || Men (*x*[[2]]) || *P*(*X,Y*) || *x*[[1]] || *x*[[2]] || *P*(*Y*) || *P*(*X*∣*Y*) || *x*[[1]] || *x*[[2]] |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Smokers (*y*[[1]]) || p(*y*[[1]]∣*x*[[1]]) = 0.10 || p(*y*[[1]]∣*x*[[2]]) = 0.30 || *y*[[1]] || 0.055 || 0.135 || 0.19 || *y*[[1]] || 0.289 || 0.711 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Non-smokers (*y*[[2]]) || p(*y*[2]∣*x*[1]) = 0.90 || p(*y*[2]∣*x*[2]) = 0.70 || *y*[[2]] || 0.495 || 0.315 || 0.81 || *y*[[2]] || 0.611 || 0.389 |
| *P*(*X*) || 0.55 || 0.45 || *P*(*X*) || 0.55 || 0.45 || 1.00 ||  ||  ||  |

From the likelihood *P*(*Y*∣*X*) sub-table, we are able to construct the joint probability sub-table *P*(*X*,*Y*) shown in the middle three columns of table [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t4). The values of four cells in the *P*(*X,Y*) table are obtained according to equation ([1.11](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn11)) with *p*(*x,y*) = *p*(*y*∣*x*) *p*(*x*). Now we know that among all the people on the island, 5.5% of the smokers are women; 13.5% of the smokers are men; 49.5% of the non-smokers are women; and 31.5% of the non-smokers are men. The marginal possibilities *p*(*y*[1]) and *p*(*y*[2]) for smokers and non-smokers are 19% and 81% respectively. With the joint possibility sub-table, we can calculate the values in the four cells of the posterior probability *P*(*X*∣*Y*) shown on the right side of table [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t4). These calculations are also based on equation ([1.11](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn11)) with *p*(*x*∣*y*) = *p*(*x*,*y*)/*p*(*y*). For example, the probability of a smoker who is a woman is *p*(*x*[1]∣*y*[1]) = *p*(*x*[1], *y*[1]) /*p*(*y*[1]) = 28.9%.

The above explanations about the posterior probability calculations are very complex even for the simple question with four variables: men, women, smokers, non-smokers. Aren’t they? Since we had limited life-time and limited resources, we only could explore a part of our world which is accessible for us. With information from the accessible data and Bayes' theorem, we could deduce information of the whole system. In the above simple example, the joint probability table *P*(*X,Y*) is about the probabilities relative to the whole population on the island. The prior possibility table *P*(*Y*∣*X*) came from our investigation or exploration. It is about probabilities relative to each sub-population: men and women. The posterior probability table *P*(*X*∣*Y*) has information derived from the prior probability table and the joint probability table. It is about probabilities relative to each sub-group: smokers and non-smokers. In fact, it is not necessary to construct those three sub-tables shown in table [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t4). According to Bayes' theorem, we have *p*(*x*[1]∣*y*[1]) = *p*(*y*[1]∣*x*[1])*p*(*x*[1])/*p*(*y*[1]) = *p*(*y*[1]∣*x*[1])*p*(*x*[1])/\[*p(y*[*1*]*∣x*[*1*]*)p(x*[*1*])+ *p*(*y*[1]∣*x*[2])*p*(*x*[2])\] = 28.9%. You see that prior probabilities or likelihood are known data, and the posterior probability is the inference from these known data. From probabilities in table [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t4), we can calculate the joint entropy *H*(*X,Y*), the prior conditional entropy *H*(*X*∣*Y*), the posterior conditional entropy *H*(*Y*∣*X*) and the mutual information *I*(*X,Y*) with the following formulae

  
$$H\\left( {X,Y} \\right) = - \\sum\\limits\_{i = 1}^{2}{\\sum\\limits\_{j = 1}^{2}{p\\left( {x\_{i},y\_{j}} \\right)\\ \\ln\\ \\left( { p\\left( {x\_{i},y\_{j}} \\right)} \\right)}} = 1$$  
(1.12)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn17.gif" position="float"/

  
$$H\\left( {X \\mid Y} \\right) = - \\sum\\limits\_{i = 1}^{2}{\\sum\\limits\_{j = 1}^{2}{p\\left( {x\_{i},y\_{j}} \\right)}}\\ \\ln\\ \\left( { p\\left( {x\_{i} \\mid y\_{j}} \\right)} \\right) = 0$$  
(1.13)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn18.gif" position="float"/

  
$$H\\left( {Y \\mid X} \\right) = - \\sum\\limits\_{i = 1}^{2}{\\sum\\limits\_{j = 1}^{2}{p\\left( {x\_{i},y\_{j}} \\right)}}\\ \\ln\\ \\left( { p\\left( {y\_{i} \\mid x\_{j}} \\right)} \\right) = 0.454$$  
(1.14)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn19.gif" position="float"/

  
$$I\\left( {X,Y} \\right) = I\\left( {Y,X} \\right) = \\sum\\limits\_{i = 1}^{2}{\\sum\\limits\_{j = 1}^{2}{p\\left( {x\_{i},y\_{j}} \\right)}}\\ \\ln\\ \\left( \\frac{ p\\left( {y\_{i},x\_{j}} \\right)}{p\\left( y\_{i} \\right)p\\left( x\_{j} \\right)} \\right) = 0.032$$  
(1.15)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn20.gif" position="float"/

  
$$H\\left( X \\right) = - \\sum\\limits\_{j = 1}^{2}{p\\left( x\_{j} \\right)\\ \\ln\\ \\left( { p\\left( x\_{j} \\right)} \\right) = 0.688}$$  
(1.16)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn21.gif" position="float"/

  
$$H\\left( Y \\right) = - \\sum\\limits\_{j = 1}^{2}{p\\left( y\_{j} \\right)\\ \\ln\\ \\left( { p\\left( y\_{j} \\right)} \\right) = 0.486}$$  
(1.17)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn22.gif" position="float"/

  
*I*(*X*,*Y*) = *H*(*X*) − *H*(*X*∣*Y*) = *H*(*Y*) − *H*(*Y*∣*X*) = 0.032  
(1.18)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn23.gif" position="float"/

  
*H*(*X*,*Y*) = *H*(*X*) + *H*(*Y*∣*X*) = *H*(*Y*) + *H*(*X*∣*Y*) = 1.142  
(1.19)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn24.gif" position="float"/

If random variables *X* and *Y* are not independent, the mutual information *I*(*X,Y*) is a positive number. Using tables [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t1)–[1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t3), you will find that the mutual information *I*(*X,Y*) of the gambling machine with a fair coin and a fair dice is equal to zero. In chapter [6](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6), the mutual information *I*(*X,Y*) will enable us to control what images to generate.

#### 1.1.4 Jensen's inequality

If a function *g*(*x*) is a **convex function** in a range *x*∈*X* with *E*\[*g*(*X*)\] and *g*\[*E*(*X*)\] are finite, then the average of the function's values in the range is bigger or equal to the function's value at the average of *X*: *E*\[*g*(*X*)\] ⩾ *g*\[*E*(*X*)\]. The PDF of *x* can be a normal distribution or another kind of distribution.

**Example 01**: There is a convex function *g*(*x*) = *x* ² with *x*∈\[−1,1\] and PDF *p*(*x*) = 1/2

  
$$\\mu = E\_{p}\\left\\lbrack X \\right\\rbrack = \\overline{X} = \\int\_{- 1}^{1}{\\mathit{xp}\\left( x \\right)\\mathit{dx} = 0},g\\left( {E\_{p}\\left\\lbrack X \\right\\rbrack} \\right) = \\left( \\mu \\right)^{2} = 0$$  
graphic style="width:23.6875em;" xlink:href="bk978-0-7503-6244-3ch1ueqn25.gif" position="float"/

  
$$E\_{p}\\left\\lbrack {g\\left( X \\right)} \\right\\rbrack = \\overline{X^{2}} = \\int\_{- 1}^{1}x^{2}p\\left( x \\right)\\mathit{dx} = \\frac{1}{3}, E\_{p}\\left\\lbrack {g\\left( X \\right)} \\right\\rbrack \\geqslant g\\left( {E\_{p}\\left\\lbrack X \\right\\rbrack} \\right)$$  
graphic style="width:25.1875em;" xlink:href="bk978-0-7503-6244-3ch1ueqn26.gif" position="float"/

**Example 02**: There is another convex function *g*(*x*) = -ln(*x*) with *x*∈\[0.5,4.5\] and PDF *p*(*x*) = 1/4

  
$$\\mu = E\_{p}\\left\\lbrack X \\right\\rbrack = \\int\_{0.5}^{4.5}{\\mathit{xp}\\left( x \\right)\\mathit{dx}} = \\frac{5}{2},g(E\_{p}\\left\\lbrack X \\right\\rbrack) = - \\ln\\ \\left( \\mu \\right) = - \\ln\\ \\left( \\frac{5}{2} \\right) = - 0.92$$  
graphic style="width:30.5625em;" xlink:href="bk978-0-7503-6244-3ch1ueqn27.gif" position="float"/

  
*E*[*p*]\[*g*(*X*)\] =  − ∫[0.5]^(4.5) ln  (*x*)*p*(*x*)*d**x* =  − 0.78, *E*[*p*]\[*g*(*X*)\] ≥ *g*(*E*[*p*]\[*X*\])  
graphic style="width:26.125em;" xlink:href="bk978-0-7503-6244-3ch1ueqn28.gif" position="float"/

#### 1.1.5 Maximum likelihood estimation and over fitting

In machine learning, we need to know probability density functions of datasets for image generation. From a PDF of a dataset, we can generate new data (images). In most cases, we only have data (images), how can we find a PDF hidden in the dataset? Maximum likelihood estimation (MLE) is a method which allows us to find a PDF in a dataset if we have a set of data {*x*[*i*]}, where *i* = 1, 2, …, *n*. For example, the dataset is about body heights of students, and the data in the dataset follow a Gaussian distribution *N*(*x*;*μ*,*σ*). Using MLE, we will find the PDF's parameters: *μ* and *σ*. Likelihood is the probability of an event which has happened with an unknown PDF. The body height *x*[*i*] of a student is a sample from a likelihood function *N*(*x*;*μ*,*σ*) in which each student's body height is independent. The likelihood function is the joint probability of the dataset:

  
$${likelihood}\\left( {\\mu,\\sigma^{2} \\mid x\_{1},x\_{2},\\ldots x\_{n}} \\right) = \\prod\\limits\_{i = 1}^{n}N(x\_{i};\\mu,\\sigma^{2})$$  
(1.20)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn29.gif" position="float"/

The above likelihood function should be maximized by optimizing its two parameters: *μ*, and *σ*². For mathematics convenience in the Python and PyTorch coding environment, we need to minimize the negative log likelihood, and use it as a **loss function** $L = - \\ln\\ \\left( {\\prod\\limits\_{i = 1}^{n}{N(x\_{i};\\mu,\\sigma^{2})}} \\right)$inline-graphic style="height:3.5em;" xlink:href="bk978-0-7503-6244-3ch1ieqn30.gif"/ as shown in equation ([1.21](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn21)). Then from ∂*L*/∂μ = 0 and ∂*L*/∂σ = 0, it is easy to get the PDF's mean *μ* = $\\overline{X}$inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch1ieqn31.gif"/, and the variance *σ*² = $\\overline{X^{2}} - {\\overline{X}}^{2}$inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch1ieqn32.gif"/

  
$$L = \\frac{n}{2}\\ \\ln\\ \\left( {2\\pi} \\right) + \\frac{n}{2}\\ \\ln\\ \\left( \\sigma^{2} \\right) + \\frac{1}{2\\sigma^{2}}\\sum\\limits\_{i = 1}^{n}\\left( {x\_{i} - \\mu} \\right)^{2}$$  
(1.21)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn33.gif" position="float"/

 

The mean squared error (MSE) loss function can be derived from the maximum likelihood estimation. For a set of data pairs {*x*[*i*], *y*[*i*]}, we assume that each target *y[i]* of a given *x[i]* is a random number coming from an independent Gaussian distribution *p*[*i*](*y*[*i*]∣*x*[*i*]) = ℕ(*y*[*i*];*μ*[*i*], *σ*²)inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch1ieqn34.gif"/. All those Gaussian distributions have the same variance (*σ*² = 1/*β*), where *β* has a name ‘precision’, and the mean of each Gaussian distribution is a predicted value (*μ[i]*) of the target *y*[*i*], where *i* = 1, 2, …, *n*. We suppose *μ* is a linear function of weights: $\\mu\_{i} = f\\left( {x\_{i},W} \\right) = w\_{0} + \\sum\\limits\_{j = 1}^{m}{w\_{j}x\_{i}^{j}}$inline-graphic style="height:3.25em;" xlink:href="bk978-0-7503-6244-3ch1ieqn35.gif"/ or *μ* = *X* ⋅ *W*.inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch1ieqn36.gif"/

  
$$\\begin{bmatrix} \\mu\_{1} \\\\ \\mu\_{2} \\\\ \\ldots \\\\ \\mu\_{n} \\\\ \\end{bmatrix} = \\begin{bmatrix} 1 & x\_{1} & \\ldots & x\_{1}^{m} \\\\ 1 & x\_{2} & \\ldots & x\_{2}^{m} \\\\ \\ldots & \\ldots & \\ldots & \\ldots \\\\ 1 & x\_{n} & \\ldots & x\_{n}^{m} \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} w\_{0} \\\\ w\_{1} \\\\ \\ldots \\\\ w\_{m} \\\\ \\end{bmatrix}$$  
(1.22)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn37.gif" position="float"/

From the joint likelihood of these random variables ${likelihood}\\left( {Y \\mid X} \\right) = \\prod\\limits\_{i = 1}^{n}p\_{i}\\left( {y\_{i} \\mid x\_{i}} \\right)$inline-graphic style="height:3.125em;" xlink:href="bk978-0-7503-6244-3ch1ieqn38.gif"/, we have a loss function $L = - \\ln\\ ⁡\\left( \\prod\_{i = 1}^{n}{\\frac{1}{\\sqrt{2\\pi\\sigma^{2}}}e^{- \\frac{1}{2}{(\\frac{y\_{i} - \\mu\_{i}}{\\sigma})}^{2}}} \\right)$inline-graphic style="height:2.1875em;" xlink:href="bk978-0-7503-6244-3ch1ieqn39.gif"/

  
$$L = \\frac{\\beta}{2}\\sum\\limits\_{i = 1}^{n}\\left( {\\mu\_{i} - y\_{i}} \\right)^{2} - \\frac{n}{2}\\ \\ln\\ \\left( \\beta \\right) + \\frac{n}{2}\\ \\ln\\ \\left( {2\\pi} \\right)$$  
(1.23)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn40.gif" position="float"/

To obtain *W* and *β*, we need to maximize the likelihood function. The reults are the same to minimize the loss function. From ∇[*W*]*L =* 0 and ∇[*β*]*L =* 0, we get:

  
*W* = (*X*^(*T*)⋅*X*)^( − 1) ⋅ *X*^(*T*) ⋅ *Y*  
(1.24)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn41.gif" position="float"/

  
$$\\beta = \\frac{1}{N}\\sum\\limits\_{i = 1}^{N}\\left( {\\mu\_{i} - y\_{i}} \\right)^{2}$$  
(1.25)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn42.gif" position="float"/

If *β* = 1, equation ([1.23](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn23)) becomes a MSE loss function. The constant in the loss function doesn’t affect the loss function's gradients. In fact, in Ridge regression (Hilt *et al* [1977](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1bib2)) we add a constant to the MSE loss function to fight overfitting issues by adjusting a parameter λ in $L = \\frac{1}{2}\\sum\\limits\_{i = 1}^{N}\\left( {{\\widehat{y}}\_{i} - y\_{i}} \\right)^{2} + \\frac{\\lambda}{2}{\\mid\\mid}\\mathit{W}{\\mid\\mid}^{2}$inline-graphic style="height:3.25em;" xlink:href="bk978-0-7503-6244-3ch1ieqn43.gif"/, where  ∣ ∣*W* ∣ ∣² = *w*[0]² + *w*[1]² + … + *w*[*M*]²inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch1ieqn44.gif"/

  
*W* = (*X*^(*T*)⋅*X*+*λ**I*)^( − 1)*X*^(*T*) ⋅ *Y*  
(1.26)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn45.gif" position="float"/

The code in project [1.1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn7) is an application of using MLE for a nonlinear regression about *y = x*⁴*+x*²−1, which is defined in Cell 01 of a Jupyter notebook in VS Code as a lambda function named *f*. If you are having issues understanding the codes in the project, you can skip them and just remember the overfitting issue shown in figure [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig1). We will not use the codes again. The tools for the project are libraries from NumPy and Matplotlib. **NumPy** is an open-source Python library for scientific computing and data analysis. From the library, we can import many high-level mathematical functions for linear algebra and nonlinear algebra calculations. Since its core is a well-optimized C code, NumPy is easy to handle with the speed of compiled codes. **Matplotlib** is a data visualization Python library. There are many Matplotlib functions for use in creating different kinds of plots.

![Figure 1.1. Nonlinear regression results with maximum likelihood estimation algorithm. Overfitting can be seen from the dashed zig-zag line (m: the order of a univariate polynomial function for nonlinear regression).](images/bk978-0-7503-6244-3ch1f1_online.jpg)

**Figure 1.1.** Nonlinear regression results with maximum likelihood estimation algorithm. Overfitting can be seen from the dashed zig-zag line (*m*: the order of a univariate polynomial function for nonlinear regression).

Nonlinear regression results are shown in figure [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig1). The green curve in the figure has 101 points generated by the function as a ground truth for the regression results. The eleven blue dots come from a train dataset used for the nonlinear regression. The *y* value of each blue dot at its *x* position is assumed to be a random number with an independent Gaussian distribution whose mean is *μ* according to equation ([1.22](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn22)). All the eleven Gaussian distributions have the same variance. Based on equation ([1.25](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn25)), a function y\_hat defined in Cell 02 returns mu and W. The inputs of the function are 11 data pairs {*x*[*i*], *y*[*i*]} of the train dataset, and the order (*m*) is the univariate polynomial (equation ([1.22](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn22)))

![image](images/bk978-0-7503-6244-3ch1uf1_pr.gif)

Codes in Cell 03 are used to display the nonlinear regression results. Using an order *m* = 3 univariate polynomial function to numerically simulate an order 4 univariate polynomial function, we know the regression result (the red curve) would not be good enough. In real world cases, we often do not know the ground truth as shown by the green curve in figure [1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig1). We have to try many times to get what we need. With an order *m* = 9 univariate polynomial, we obtained a dashed zig-zag line which goes through each blue dot. From the black dashed line, we see an overfitting issue. Although the loss function value or beta value is close to zero, the order 9 nonlinear regression result is worser than the result of order 3. Overfitting is a big issue in machine learning. We will try to avoid it. The email symbol @ in Cell 02 denotes a dot production between two matrices in algebra.

#### 1.1.6 Application of expectation-maximization algorithm to find a PDF

In many machine learning projects we need to find a PDF of a dataset in a high dimensional space. The **expectation-maximization algorithm** (Dempster *et al* [1977](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1bib1)) is a useful method to perform maximum likelihood estimation for these projects. In a scenario where a teacher gives his students a 1D dataset in a csv text file for homework to find a PDF, the first thing the student should do is plot a histogram of the data with the codes in project [1.1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn8). From the histogram shown in figure [1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig2)(A), the student can guess that the teacher generated the data file with three Gaussian distributions, and their contributions to a DPF of the dataset are the same (weight = 1/3). From the histogram, the student can also guess that the means and variances of the three normal distributions are: \[−5.5, 0.0, 4.0\], \[1.0, 1.0, 1.0\]. If the student finished the homework just by guessing, the teacher would not award the student a pass.

![Figure 1.2. (A) Histogram of 1D dataset from a csv file with 300 numbers (output of Cell 02). (B) A PDF of the 1D dataset found by expectation-maximization algorithm (output of Cell 04).](images/bk978-0-7503-6244-3ch1f2_online.jpg)

**Figure 1.2.** (A) Histogram of 1D dataset from a csv file with 300 numbers (output of Cell 02). (B) A PDF of the 1D dataset found by expectation-maximization algorithm (output of Cell 04).

The dataset *X* = {*x*[1], *x*[2], …, *x*[*n*]} in the project could be generated from a 3D latent space *Z* = {*z*[1], *z*[2], *z*[3]}. The likelihood of each point (*x*[*j*]) in the dataset is obtained by equation ([1.27](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn27)) with those parameters guessed about the three Gaussian distributions, and they are listed in table [1.5](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t5), in which *P*(*Z*) is for marginal probability with *p*(*z*[*i*]) = 1/3. Each element of *P*(*Z*) is the weight of a Gaussian distribution contributed to the PDF of the dataset *X*. The parameters of the three Gaussian distributions and their weights would be updated at each step or epoch of model training of the project.

  
$$p\\left( {x\_{j} \\mid z\_{i}} \\right) = \\frac{1}{\\sqrt{2\\pi\\sigma\_{i}^{2}}}e^{- \\frac{1}{2}{(\\frac{x\_{j} - \\mu\_{i}}{\\sigma\_{i}})}^{2}},\\left( {i = 1,2,3,j = 1,2,\\ldots,n} \\right)$$  
(1.27)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn46.gif" position="float"/

**Table 1.5.** Likelihood *P*(*X*∣*Z*) and marginal possibilities *P*(*Z*).

| *P*(*X∣Z*) || *x*[1] || *x*[2] || *…* || *x*[*n*] || *P*(*Z*) |
| --- | --- | --- | --- | --- | --- |
| *z*[1] || *p*(*x*[1]*∣z*[1]) || *p*(*x*[2]*∣z*[1]) || *…* || *p*(*x*[*n*]*∣z*[1]) || *p*(*z*[1]) *\=* 1*/*3 |
| --- | --- | --- | --- | --- | --- |
| *z*[2] || *p*(*x*[1]*∣z*[2]) || *p*(*x*[2]*∣z*[2]) || *…* || *p*(*x*[*n*]*∣z*[2]) || *p*(*z*[2]) *\=* 1*/*3 |
| *z*[3] || *p*(*x*[1]*∣z*[3]) || *p*(*x*[2]*∣z*[3]) || *…* || *p*(*x*[*n*]*∣z*[3]) || *p*(*z*[3]) *\=* 1*/*3 |

Each point *x*[*j*] could be treated as a random number with a marginal possibility *p*(*x*[*j*]) which is obtained with equation ([1.28](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn28)). The joint probability density function of the dataset is *P*(*X*) *\= p*(*x*[1])*p*(*x*[2])*…p*(*x*[*n*]). The loss function of model training for the dataset is:

  
$$L = - \\ln\\ \\left( {P\\left( X \\right)} \\right) = \\ln\\ \\prod\_{i = 1}^{n}{p\\left( x\_{j} \\right)} = - \\sum\\limits\_{j = 1}^{n}{\\ \\ln\\ \\left( {\\sum\\limits\_{i = 1}^{m = 3}{p\\left( {x\_{j} \\mid z\_{i}} \\right)p\\left( z\_{i} \\right)}} \\right)}$$  
(1.28)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn47.gif" position="float"/

Then we can calculate the posterior possibilities *P*(*Z∣X*) according to equation ([1.29](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn29)). The calculation results are shown in table [1.6](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t6) in which *p*(*z*[*i*]*∣x*[*j*]) is the posterior possibility at *z*[*i*] of a given *x*[*j*]

  
$$p\\left( {z\_{i} \\mid x\_{j}} \\right) = \\frac{p\\left( {x\_{j} \\mid z\_{i}} \\right)p\\left( z\_{i} \\right)}{p\\left( x\_{j} \\right)} = \\frac{p\\left( {x\_{j} \\mid z\_{i}} \\right)p\\left( z\_{i} \\right)}{\\sum\\limits\_{k = 1}^{3}{p\\left( {x\_{j} \\mid z\_{k}} \\right)}p\\left( z\_{k} \\right)}$$  
(1.29)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn48.gif" position="float"/

**Table 1.6.** Posterior possibility *P*(*Z*∣*X*) and marginal possibilities *P*(*X*).

| *P*(*Z∣X*) || *x*[1] || *x*[2] || *…* || *x*[*n*] |
| --- | --- | --- | --- | --- |
| *z*[1] || *p*(*z*[1]*∣x*[1]) || *p*(*z*[1]*∣x*[2]) || *…* || *p*(*z*[1]*∣x*[*n*]) |
| --- | --- | --- | --- | --- |
| *z*[2] || *p*(*z*[2]*∣x*[1]) || *p*(*z*[2]*∣x*[2]) || *…* || *p*(*z*[2]*∣x*[*n*]) |
| *z*[3] || *p*(*z*[3]*∣x*[1]) || *p*(*z*[3]*∣x*[2]) || *…* || *p*(*z*[3]*∣x*[*n*]) |
| *P*(*X*) || *p*(*x*[1]) || *p*(*x*[2]) || *…* || *p*(*x*[*n*]) |

By setting the gradients of the loss function to be equal to zero, we can obtain optimized parameters of the three Gaussian distributions and their weights *P*(*Z*). It is easy to get *μ*[*i*] and *σ*[*i*]. There is a trick to getting *p*(*z*[*i*]). With the condition *p*(*z*[1])*+p*(*z*[2])*+p*(*z*[3]) *\=* 1 in table [1.5](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t5), we know that only two of the three marginal probabilities are independent. Using derivations in appendix [B](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-B), we obtain formulae from equations ([1.30](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn30))–([1.32](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn32)). From them, we will update those three Gaussian distributions’ parameters for tables [1.5](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t5)–[1.6](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1t6) in the second epoch of model training. This updating process repeats many times (*n*\_epochs = 5000) in a for-loop iteration on line 02 of Cell 04. The blue curve in figure [1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig2)(B) is a predicted PDF of the 1D dataset. After getting the student's homework, the teacher told the student that three Gaussian distributions with equal weights were used to generate the data of the csv file. Codes to generated the csv file are listed in Cell 06. The original parameters of these Gaussian distributions were *μ* = \[−6, 0, 5\] and *σ* = \[1.5, 1.2, 2\]. For comparison, the student drew the true PDF curve (green curve) in figure [1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig2)(B). From the simple project about finding a PDF of a dataset, we now know how to calculate posterior possibilities for data predications. In chapter [5](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5), we will use posterior possibilities to generate images. You can skip the codes if they are not easy to understand, because this is not the way to write machine learning codes

  
$$p\\left( z\_{i} \\right) = \\frac{1}{n}\\sum\\limits\_{j = 1}^{n}{p\\left( {z\_{i} \\mid x\_{j}} \\right)}$$  
(1.30)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn49.gif" position="float"/

  
$$\\mu\_{i} = \\frac{\\sum\\limits\_{j = 1}^{n}{x\_{j}p\\left( {z\_{i} \\mid x\_{j}} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( {z\_{i} \\mid x\_{j}} \\right)}}$$  
(1.31)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn50.gif" position="float"/

  
$$\\sigma\_{i}^{2} = \\frac{\\sum\\limits\_{j = 1}^{n}{\\left( {x\_{j} - \\mu\_{i}} \\right)^{2}p\\left( {z\_{i} \\mid x\_{j}} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( {z\_{i} \\mid x\_{j}} \\right)}}$$  
(1.32)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn51.gif" position="float"/

![](images/bk978-0-7503-6244-3ch1uf2_pr.gif)

![](images/bk978-0-7503-6244-3ch1uf3_pr.gif)

### 1.2 Using a gradient descent algorithm for linear regression

We will finish a linear regression project by using a gradient descent algorithm, the way to write machine learning codes. In project [1.2.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn10), we need to find a linear relationship between two temperature scales: Fahrenheit (F) and Celsius (C). One array is for temperatures measured in Celsius: *C* = \[−20, −15, −10, −5, 0, 5, 10, 15, 20\], and another array is generated by using a function F = 32 + 9C/5 for temperatures in Fahrenheit: *F* = \[−4, 5, 14, 23, 32, 41, 50, 59, 68\]. This is very easy homework. Just type those numbers in array C and array F into two columns of a Microsoft Excel sheet, a straight line and a linear regression function *F* = 30.0+1.8C would be displayed on screen by a few mouse clicks. But we have to do extra work by using a Jupyter Notebook file in VS Code as an integrated development environment (IDE).

Many computer vision projects are very complex. They are not 'as easy as a cakes, but 'as hard as a nut'. We have to have to use powerful tools to solve problems in those projects. Jupyter Notebook is an open-source web-based interactive computational environment which supports a wide range of programming languages, including Python, R, Julia, and more. Jupyter Notebook files are saved with a suffix ‘*ipynb*’ and can be opened in any web browser, where users can run codes in cells to get results. VS Code is a free, open-source code editor. It supports a wide range of programming languages, including Python, C++, JavaScript, etc. It provides features such as syntax highlighting, debugging, code completion, and GitHub integration. In a Jupyter notebook, we can create a mathematical model or models with parameters of millions or even billions to extract information hiding in a large amount of data for computer vision projects. The data can be images, videos, voices, text, time series graphs such as stock prices. The sizes of the data files can be a few hundred megabytes (MB) to many gigabytes (GB). It is impossible and unnecessary for us to type those data into our computer. We only need to know how to download data files into computers. Python and PyTorch have many libraries or tools to use to help with data input into VS code.

Usually, a machine learning model has many neural layers. Those digital neurons are different from the biological neurons in our brains. In a computer vision model, a neuron layer is a set of artificial neurons that process input data and produce output data. Those layers can be treated as a series of filters that successively extract and refine the information contained in the input data. The digital neurons are mathematical operators. Each neuron layer has some learnable parameters. All of these parameters in a model are automatically updated during model training, and they are called model **parameters**. For example, finishing the project about the relationship between array C and array F, we will obtain a slope 1.8 and an intercept or bias 32.0 in a linear function. They are the linear model's two parameters. To obtain a model's parameters by model training, we need a criterion to evaluate how good the model is by comparing the model's outputs with the original data. A criterion is also called a loss function in machine learning. In each step or epoch of model training, we use a gradient descent algorithm to reduce the value of the loss function. We need to set learning rate and training steps (epochs) to train the model. These parameters set by ourselves are different from model parameters, and we call them the model's **hyperparameters**. A train process could take a few seconds, hours, days or even weeks. The training time is dependent on data size, codes and computer hardware. One or more graphics processing units (GPU) in a computer are needed to reduce model training time. Optimized for parallel processing, GPUs can perform many computation tasks simultaneously.

It is easy to find the minimum or maximum of a function *y = f*(*x*) with *y′ =* 0. We can set the gradient of a function such as *y = x*² *+* 2*x* + 3 to be equal to zero (*y′ =* 2*x* + 2 *\=* 0) to find the function's minimum at *x =* −1. Usually, there are hundreds, thousands, even billions of parameters distributed in many neural layers of a model. Most of those parameters are in arrays or matrices, not scalars. It is not easy for us to explicitly write down formulae of a loss function's gradients for those arrays. You know how hard it is to get equations ([1.30](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn30))–([1.32](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn32)) from the loss function (equation ([1.28](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn28))) in appendix [B](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-B). Now, we create a *Jupyter Notebook* file and name it ‘LinearRegression.ipynb’ in VS Code. In the notebook, we can add many cells. In each cell, we write codes to do a specific job. Codes in all the cells are like specific machines on an assembly line. Working together, these codes can handle a huge amount of data. Codes in the first cell of all projects in the book are used to import Python and PyTorch libraries as tools. Hyperparameters for model training are also listed in the first cell. Codes in Cell 02 of each project are used to read and pack data. In Cell 02 of project [1.2.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn10), a ‘comma separated values’ text file ‘d:/C2F.csv’ is loaded into computer memory.

![](images/bk978-0-7503-6244-3ch1uf4_pr.gif)

 

With codes on line 01–02 of Cell 01 (the line number starting with a hash symbol # is line 0), two Python libraries are imported for the linear regression project. To save pages of typing, we will use them with their abbreviated names: np and plt. A NumPy function ‘*np.loadtxt*’ in Cell 02 loads a csv file on hard disk and stores data as a 9 × 2 array named ‘CF’ in the computer memory. If you open the csv file with MS Excel, you will see two columns and each column has a name. We do not need the column names in model training, so we set the option *skiprows = 1* for the function on line 01 of Cell 02. If you open the file in a text editor, you will see all data are separated by commas, so we set another option of the function to read data with *delimiter = ‘,’*, The second and third line of Cell 02 are used to separate the 9 × 2 NumPy array into a 1D array C and a 1D array F. Finally array C and array F are printed on screen with codes on the fourth and fifth lines. Checking the numbers of the two arrays on screen, you need to make sure that there are no mistakes in data loading.

On the sixth line of Cell 2, the length of the C array is obtained with a NumPy function *np.len(C)*. From this number, a 1D ONES array is created by another NumPpy function *np.ones(len(C))*. Each element of the ONES array is equal to 1.0. Array C and the ONES array are vertically stacked into a 2 × 9 array which is then transposed into a 9 × 2 array *X* as shown in equation ([1.33](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn33)). The Python function *reshape(−1,1)* changes the shape of array F from 1D to 9 × 1. With ‘−1’ in the reshape function, the computer automatically counts the row or column numbers

  
$$X = \\begin{bmatrix} x\_{0,0} & 1 \\\\ x\_{1,0} & 1 \\\\ \\ldots & \\ldots \\\\ x\_{8,0} & 1 \\\\ \\end{bmatrix} = \\begin{bmatrix} {- \\ 20} & 1 \\\\ {- \\ 15} & 1 \\\\ \\ldots & \\ldots \\\\ 20 & 1 \\\\ \\end{bmatrix},\\ \\mathit{Y} = \\begin{bmatrix} y\_{0} \\\\ y\_{1} \\\\ \\ldots \\\\ y\_{8} \\\\ \\end{bmatrix} = \\begin{bmatrix} {- \\ 4} \\\\ 5 \\\\ \\ldots \\\\ 68 \\\\ \\end{bmatrix},\\ \\widehat{y} = \\begin{bmatrix} x\_{0,0} & 1 \\\\ x\_{1,0} & 1 \\\\ \\ldots & \\ldots \\\\ x\_{8,0} & 1 \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} w\_{0} \\\\ w\_{1} \\\\ \\end{bmatrix}\\mspace{9mu}$$  
(1.33)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn52.gif" position="float"/

To obtain a linear relationship (*F* = *kC* + *b*) about the two 1D arrays, we need two parameters: the slope *k* and the intercept *b*. For mathematical convenience, we pack them into a weight array *W =* \[*w*[0],*w*[1]\]^(*T*) *\=* \[*k,b*\]^(*T*). The superscript *T* on an array means a transpose operation to the array, so the weight array has two rows and one column. The model of the project is defined as y\_hat = *X@W* on the second line of Cell 03, where *X* is a 9 × 2 array (equation ([1.33](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn33))). The first column of array *X* is the array *C* in a column, and each element of its second column is equal to 1.0. The @ operation result of *X* and *W* gives us an array y\_hat with a shape of 9 × 1, and each element of y\_hat is a prediction of the model. Each parameter of array *W* is initialized to be zero by a code on line 03 of Cell 04. With these settings, we obtain the initial prediction array y\_hat with all nine elements to be zeros at epoch = 0. We need the model's prediction y\_hat to be as close as to the target *Y* by using a MSE criterion or loss function during model training.

  
$$L\\left( {X,w} \\right) = \\frac{1}{\\left( {n + 1} \\right)}\\sum\\limits\_{i = 0}^{n}\\left( {{\\widehat{y}}\_{i} - y\_{i}} \\right)^{2}$$  
(1.34)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn53.gif" position="float"/

  
$$\\nabla L = \\begin{bmatrix} \\frac{\\partial L}{\\partial w\_{0}} \\\\ \\frac{\\partial L}{\\partial w\_{1}} \\\\ \\end{bmatrix} = \\frac{2}{n + 1}\\begin{bmatrix} x\_{0,0} & x\_{1,0} & \\ldots & x\_{n,0} \\\\ 1 & 1 & \\ldots & 1 \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} {{\\widehat{y}}\_{0} - y\_{0}} \\\\ {{\\widehat{y}}\_{1} - y\_{1}} \\\\ \\ldots \\\\ {{\\widehat{y}}\_{n - 1} - y\_{n - 1}} \\\\ \\end{bmatrix}$$  
(1.35)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch1eqn54.gif" position="float"/

The formula of the loss function and the formula of the gradient of the loss function to the weights are shown in equation ([1.34](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn34)) and ([1.35](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn35)), where *n* = 9 (appendix [C](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-C)). The MSE loss function sets a 3D digital valley with a lowest point, or a minimum of zero. The weight matrix is then updated in a direction opposite to the direction of the gradient of the loss function: *w*[*i* + 1] = *w*[*i*] − *l**r* ⋅ ∇*L*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch1ieqn55.gif"/, where ‘*lr*’ is a small number for learning rate. In this way, the model can be trained in each epoch with a step of ‘*lr*’ to approach the lowest point. This is an optimization algorithm to train models and it is called the ‘gradient descent algorithm’.

In Cell 03, three functions are defined according to equations ([1.33](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn33))–([1.35](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn35)). They are the model, the MSE criterion and the gradient function. A square array operation in the criterion function is not a regular mathematic operation in linear algebra. There are many of this kind of non-algebra operations in NumPy and PyTorch for element-wise operations without for-loops to accelerate calculations. The learning rate hyperparameter in Cell 01 should be set before model training. If the learning rate is too small, the model training may take longer to reach its minimum. Or if the learning rate is too big, the model's loss values may oscillate around the loss function's minimum, and the training process will never be finished. With an optimized learning rate, the training loss would decrease significantly at the beginning of model training, and then decreases slowly. We will use variable learning rates by using learning rate schedulers provided by PyTorch later.

![](images/bk978-0-7503-6244-3ch1uf5_pr.gif)

 

A fit function for the linear regression project is defined in Cell 04. This function needs four inputs. The first two are input data with specific array shapes shown in equation ([1.33](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn33)). The remaining two are the training epochs and learning rate. They are hyperparameters of the model. A small Python module *tqdm* is used to show a progress bar during model training. For a big computer vision project, model running time may be hours or even weeks. This tool will tell us how long we should wait. In a for-loop of the fit function with a progress bar, the model's prediction y\_hat and loss function values are calculated. On the progress bar, we can see the epoch, the loss, the slope w\[0,0\] and the intercept w\[1,0\]. Then the weight array is updated with the gradient descent algorithm. After model training, the fit function returns the weight array. This fit function is used on the last line of Cell 04, and its output is the weight array. This is a simple machine learning project with 20 000 training epochs. My computer finishes calculations of the project in less than 24 s. Later, you will see that big projects could take more than 60 min for 20 epochs. Even for the model training with 20 000 epochs, the slope of the linear regression is still about 10^(−8) less the 1.80. If the learning rate is bigger than 7 × 10^(−3), the linear regression would fail to find the right slope and intercept. After copying and pasting Cell 01 to 04 to your VS code notebook and running them, you will finish the linear regression project, and will find the two parameters of the model.

Using codes in Cell 05 to replace codes in Cell 04, we can see a trace of the loss function in a 3D digital space created by codes in Cell 06. From the trace of the loss function in the 3D digital valley shown in figure [1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig3), we can see how the program automatically finds the minimum point of the valley. Since this is a simple project model with only two parameters, it is possible to display the surface of the digital valley in a 3D space with the *x*\-axis for the intercept b, *y*\-axis for the slope *k*, and *z*\-axis for the loss values. Models in big machine learning projects have millions, even billions, of parameters, we can’t see their loss surfaces directly with our eyes. In the training function defined in Cell 05, a block memory is reserved for a floating array *Z* on the third line of the function. If the hyperparameter for epochs is equal to 20 000, the array *Z* will have 20 000 rows and three columns. In each training step or epoch, the slope, the intercept and a loss value would be stored in a row of the array *Z*. After model training, the function returns the array *Z* which recorded the trace of the loss values during model training.

![](images/bk978-0-7503-6244-3ch1uf6_pr.gif)

![Figure 1.3. The digital valley of the loss function and the trace (black line) of the loss function in 20 000 training steps.](images/bk978-0-7503-6244-3ch1f3_online.jpg)

**Figure 1.3.** The digital valley of the loss function and the trace (black line) of the loss function in 20 000 training steps.

Although codes in Cell 06 are a little complex, the outputs of the cell shown in figure [1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig3) are easy to understand. The colored surface is the digital valley's top surface, and the black zig-zag line is the loss function's trace in 20 000 epochs. If you choose a smaller learning rate, the learning trace would be a smooth line. To understand the code in Cell 06, you need a little more knowledge about the Python library *matplotlib.pyplot* for data visualization. You can learn what you need from many YouTube websites about this important library. The codes in the cell set a plot for a 3D projection and the plot figure size to be 16 × 6 square inches. Then a mesh grid is created for the digital valley. We know the intercept should be 32, and the slope should be 1.8. An array b\_col is set by *np.linspace(−2, 38, 801)*, and an array k\_row is set by *np.linspace(0,4,401)*. With a function *np.meshgrid*(), the above two 1D arrays were converted into two 2D arrays named b and k. Their sizes are the same: 401 × 801. If you add an extra cell in the VS code notebook and print them out, you will see that each column of array k is the same, and each row in array b is the same. The two for-loops in Cell 06 combine the two array elements at each mesh grid point into a 2 × 1 array for the weight array *w*. The Python function *enumerate*() to any 1D array can provide the array's index value and the array's element value at that index. With the weight array *w* and array *X* and *Y*, the loss function value can be calculated at each grid point. The digital valley surface is then plotted by *ax.plot\_surface()*, and the loss value trace is plotted by another function *ax.plot3D()*.

This simple project has a direct solution with ∇*L =* 0 in equation ([1.35](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn35)) to get *w* = (*X*^T·*X*)^(−1)·*X*^T·*Y*. Although it is easy to finish this simple project with this explicit formula in milliseconds, we should learn how to use the gradient descent algorithm to do this kind of work because we do not have direct solutions for many complex computer vision projects. Those complex projects have millions, or even billions of parameters to train, and we are not able to write down mathematics formulae for gradients of any loss function to model parameters. PyTorch can help us to calculate those gradients. PyTorch is an open-source machine learning framework based on its Torch library. It provides tensor computation with strong GPU supports, and deep neural networks built on a tape-based auto-grad system. PyTorch is developed by Facebook's AI Research lab and is widely used for computer vision and natural language processing tasks. TensorFlow is another open-source machine learning framework developed by Google. Pytorch is more popular than TensorFlow today.

### 1.3 Automatic gradient calculations and learning rate schedulers

In each computer vision project, we must calculate gradients for at least one loss function to parameters during model training. In a model with a billion parameters distributed in many neural layers, it is almost impossible to derive gradient formulae manually. PyTorch can be used to automatically calculate these gradients without providing gradient formulae. We know that the gradient of a scalar function *f*(*x,y,z*) to a vector *V* = \[*x,y,z*\] is still a vector whose components are partial derivatives: ∇*f* = \[∂*f*/∂*x*, ∂*f*/∂*y*, ∂*f*/∂*z*\]. For example, a function *f*(*x,y,z*) = *x*² *\+ y*² *\+ z*² at a point *V* = \[1,2,3\], the gradient is: ∇*f* = \[2*x*, 2*y*, 2*z*\] = \[2, 4, 6\]. The following VS Codes are used to calculate the gradients automatically by PyTorch. The torch package is imported on the first line of Cell 01. It supports data structures of multi-dimensional tensors, and provides mathematical operations for these tensors. Torch tensors are similar to NumPy's array, and they can be converted to each other. The main advantage of using torch tensors is that torch tensors can be moved to NVIDIA GPU for parallel computations to save time.

![](images/bk978-0-7503-6244-3ch1uf7_pr.gif)

 

To calculate gradients of a scalar function, a vector as a torch tensor must have its attribute ‘requires\_grad’ to be True (line 02). With this setting, all mathematics operations of the vector are recorded by PyTorch. In the for-loop of Cell 01, the *f* function must be inside the loop, and then the *f.backward*() function must be called to compute the gradients in all operations. The gradient of the function is then accumulated with *V.grad*. About the outputs of Cell 01, the gradient calculations in the first iteration are right, the other two are wrong. Only if you delete the hash tag symbol # in front line 08 are all the calculations correct. Every time you use PyTorch to calculate gradients automatically, you need to reset gradients to be zero by *grad.zero*\_() or use other methods mentioned later.

![](images/bk978-0-7503-6244-3ch1uf8_pr.gif)

 

For a scalar function with more than one variable, we may need to ignore one variable's contributions to the function's gradient. The codes in the above Cell 02 could be used for learning more about the *backward()* function and a *detach()* function of PyTorch for automatic gradient calculations. Here is another function *R* = *y* + *z*, where *y* = *x*[1]² + *x*[2]² + *x*[3]², *z* = *x*[1]³ + *x*[2]³ + *x*[3]³ at *x* = \[*x*[1], *x*[2], *x*[3]\] = \[1,2,3\]. We can calculate the gradient ∇[*x*]*R =* $\\frac{\\partial R}{\\partial y}\\frac{\\partial y}{\\partial x} + \\frac{\\partial R}{\\partial z}\\frac{\\partial z}{\\partial x}$inline-graphic style="height:1.9375em;" xlink:href="bk978-0-7503-6244-3ch1ieqn56.gif"/ with a formula \[2*x*[1] + 3*x*[1]², 2*x*[2] + 3*x*[2]², 2*x*[3] + 3*x*[3]²\]. Using PyTorch, we do not need to know the gradient formula. Just by calling the function *R*.backward(), all intermediate gradients of ∇[*x*]*R* will be recorded and tracked by a back propagation algorithm of PyTorch. Then by calling *x.grad*, ∇[*x*]*R* is obtained by an acumulation of all the intermediate gradients.

By setting ∂R/∂*y* = 0, we can ignore the contribution of *y* to ∇[*x*]*R*. In generative adversarial networks (GANs) projects in chapter [3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3), we will meet this kind of task. In this case, we have∇[*x*]*R* = \[3 × 1², 3 × 2², 3 × 3²\]. In the above Cell 02, *y*.detach() is used for ∂*R*/∂*y* = 0. You can change *y*.detach() to *z*.detach() to see the difference of the gradient outputs. Based on the knowledge of automatic gradient calculations in PyTorch, we can write codes of project [1.3.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn15) for the simple linear regression about the temperature conversion in a different way.

![](images/bk978-0-7503-6244-3ch1uf9_pr.gif)

 

More libraries or tools are imported in Cell 01. Torch is a PyTorch package for multi-dimensional tensors and their mathematical operations. Torch also provides many utilities for neural network construction and model training. We will use *torch.nn* to construct our linear regression model, and a module named *lr\_scheduler* for a variable learning rate. A pandas dataframe will be used to record model training history. Pandas is a Python package. A pandas dataframe is a 2D data structure with rows and columns. Did you notice that in Cell 02 for data input, variables *X* and *Y* are torch FloatTensors? A tensor is a data container which can be used to store a 1D, 2D, 3D and even more than 4D array or matrix. A batch of color photos with a batch size of 64 and an image resolution 256 × 256 can be stored in a 4D PyTorch tensor whose shape is 64 × 3 × 256 × 256. In Cell 02, data from the csv file are stored in a NumPy 2D array. Each of its two columns is then converted into a float32 tensor with a shape of 9 × 1 respectively. Here the ‘view(−1, 1)’ and ‘reshape(−1, 1)’ do the same work. We do not need to concatenate a ONES tensor with *X*. PyTorch will take care of the extra work. If you add an extra cell below Cell 01, and run CF.dtype or X.dtype in the extra cell, you will find that the data type of array CF is ‘floating64’, and the data type of tensor *X* is torch.float32. There are many kinds of tensor data type. Sometimes we need to convert one type into another type. Most times we will deal with torch.float32 in computer vision projects. Occasionally, we will us torch.float16 to save memory and model training time.

![](images/bk978-0-7503-6244-3ch1uf10_pr.gif)

 

The torch class *nn.Linear(1,1)* is used to create a fully connected neural network layer in a model with one variable input and one variable output. Mathematically, this model is designed to do the job of the linear regression model: *X*@*w*^(*T*)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch1ieqn57.gif"/. By default, the weight tensor *w* is a tensor with the shape 1 × 2. The first and the second element of the tensor is the slope and the intercept or bias respectively. This torch model does more work than the mathematical operation *X*@*w*^(*T*)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch1ieqn58.gif"/. It initializes the weight array *w*, and stores the weight parameters of the model. Please read the output of Cell 03 carefully. It prints out parameters of the optimizer. In Cell 04, we will use an item *optimizer.param\_groups\[0\]\[‘lr’\]* to get the learning rate during model training. By default, the class *nn.MSELoss()* does the job according to equation ([1.34](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn34)). The division by *n* can be avoided to reduce model training time with *nn.MSELoss(reduction = ‘sum’)*. After running the code in Extra-Cell-01 about the loss function, you would know the average loss is equal to 4.0 (*l**o**s**s* = \[3 × (2 − 0)²\]/3)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch1ieqn59.gif"/ in the example.

![](images/bk978-0-7503-6244-3ch1uf11_pr.gif)

 

There are many kinds of optimizers which are used to calculate gradients of the loss function, and update the model weight array automatically by *optimizer.step()* during model training. The Adam (adaptive moment estimation) optimizer is the most popular. It is not easy and not necessary to go through mathematical algorithms of optimizers.

![](images/bk978-0-7503-6244-3ch1uf12_pr.gif)

 

Learning rate is the most important hyperparameter for model training. PyTorch provides many learning rate schedulers to change learning rate during model training. The most versatile scheduler is the LambdaLR. You can define any function with the training epoch (*i*) as its variable. The initial learning rate (*lr*[0]) is usually set in Cell 01 for the optimizer, and the learning rate at epoch (*i*) is equal to *lr*[0] times the Lambda function value. In Extra-Cell-02, the first function is for a constant learning rate: *l**r*[*i*] = 0.5 × *l**r*[0]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch1ieqn60.gif"/. With the second lambda function, the learning rate decreases linearly during model training for 20 000 epochs. If the third or the fourth function is chosen, the learning rate decreases exponentially. The fifth lambda function is the same as *CosineAnnealingLR* scheduler in PyTorch. The sixth lambda function has three segments: for *i* < 10 000, for *i* between 10 000 and 17 000, and for *i* >17 000. The last lambda function is like *StepLR* scheduler in PyTorch. It picks out a number from a list named lr\_list at an index of *i*//5000.

![](images/bk978-0-7503-6244-3ch1uf13_pr.gif)

 

A pandas dataframe named df in Cell 04 is used to record the learning rate and loss function value for each epoch during model training. The dataframe can be obtained by calling the fit function on the last line of Cell 04. The model *nn.Linear(1,1)* takes care of all its parameters. In each training epoch, the gradients of the loss function to all its parameters are reset to be equal to zero by *optimizer.zero\_grad()* on line 10. Just as the *optimizer.step()* updates the model parameters for every epoch, *scheduler.step()* updates the optimizer's learning rate.

 

From figure [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig4)(A), we could not tell the difference between the model's prediction y\_hat and the original data Y by just looking. Running the codes in Cell 06, you would see the difference is less than 10^(−8) as shown in figure [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig4)(B). The learning rate graph shown in figure [1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig4)(C) is what we set by *my\_lambda* function in Cell 03. Pandas has powerful data visualization tools. You can use line 11 to replace line 10 in Cell 05 to plot the learning rate curve. PyTorch has smarter schedulers for us to change learning rates. One of them is the ReduceLROnPlateau(). It automatically reduces learning rate when a loss function's value or another value has stopped improving for a ‘patience’ number of epochs. There are two learning schedulers in Cell 03. By moving a hash tag symbol # in front of line 08 to line 07, and delete a # symbol in front of line 09 in Cell 03, you can try the smarter scheduler in Cell 07 for a 3D loss function surface.

![](images/bk978-0-7503-6244-3ch1uf14_pr.gif)

![Figure 1.4. Model training output graphs. (A) original data Y and predicted data y\_hat, (B): The difference between y\_hat and Y, (C): The learning rate curve with three segments set by a lambda learning scheduler.](images/bk978-0-7503-6244-3ch1f4_online.jpg)

**Figure 1.4.** Model training output graphs. (A) original data Y and predicted data y\_hat, (B): The difference between y\_hat and Y, (C): The learning rate curve with three segments set by a lambda learning scheduler.

We can use Cell 07 to replace Cell 04, and re-train the model for a 3D graph output. The option *loss.item()* in the *scheduler.step()* on line 19 in Cell 07 specifically instructs the scheduler to monitor the loss function's value. If the minimum of the loss function's value does not change in 2000 epochs (patience number), the learn rate will be halved (factor = 0.5). On line 06 of Cell 07, the model's parameters are assigned to a list named p. The values of two elements of the list, the slope and bias are recorded in the pandas dataframe during model training. After the model is trained, the dataframe is returned for plotting of a 3D Graph shown in figure [1.5](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig5). Inside the two for-loops of Cell 08, we must use *nn.Parameter()* to assign a tensor to a parameter of the model. You can try different initial learning rates and schedulers to see the trace of the loss function.

![](images/bk978-0-7503-6244-3ch1uf15_pr.gif)

![Figure 1.5. The digital valley (color) of the loss function and the trace (black) of the loss function during model training.](images/bk978-0-7503-6244-3ch1f5_online.jpg)

**Figure 1.5.** The digital valley (color) of the loss function and the trace (black) of the loss function during model training.

### 1.4 Dataset, dataloader, GPU and models saving

Data for model training in computer vision projects should be packed into datasets. Usually, sizes of datasets are huge. Many datasets are already packed into datasets by many selfless dataset creators. After downloading a dataset, we need to slice each dataset into a dataloader with many batches, because our computer memory is not big enough to handle all data of a dataset in a single batch. Just like eating a big cake, we have to cut it with a knife into small pieces so that each piece can fit into our mouths. We will learn how to pack the data in the temperature csv file into a dataset and slice it into a dataloader in project [1.4.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn22). They are all extra jobs for the simple project, but are essential steps for big datasets in computer vision projects.

![](images/bk978-0-7503-6244-3ch1uf16_pr.gif)

 

More Python and PyTorch libraries are imported in Cell 01 as tools for us to pack our data into a dataset and slice the dataset into a dataloader. How is data packed inside a dataset? Or what is the dataset structure? Codes in Cell 02 of project [1.4.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn22) are used as an example to show you how to pack data into a dataset. With a subclass Dataset imported from *torch.utils.data* in PyTorch, a class named C2F is defined. The \_\_init\_\_ function in the C2F class uses the *np.loadtxt* function to input date from the csv file with a string as its file name. The option ‘np.float32’ is important because we need it to convert the data into float32 tensors. Then each of the two columns and the length of each column are recorded. The second function in the C2F class named \_\_getitem\_\_ can be used to pick out a single pair of data in the dataset at a specific index. With the last function \_\_len\_\_ in the class C2F, we can find how many data pairs are in the dataset. In Cell 03, the csv file with a name string ‘d:/C2F.csv’ is used for an instance of the C2F class. You can see the class C2F does its jobs just as we want. In *my\_dataset\[0\]* of Cell 03, if you change the ‘0’ to ‘:’, you will print out all nine elements in the array x and all nine elements of the array y.

![](images/bk978-0-7503-6244-3ch1uf17_pr.gif)

 

It is easy to use a subclass DataLoader from *torch.utils.data* in PyTorch to slice a dataset into many small batches. With an option *shuffle = False* in Cell 04, the data sequence would not be changed. To an image dataloader for model training in the future, we need this option to be True to reduce ‘overfitting’. A for-loop in Cell 04 prints out the first batch of the dataloader. Of course, if you remove the ‘break’, you will print out all three batches.

![](images/bk978-0-7503-6244-3ch1uf18_pr.gif)

 

In sections [1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1s1-2) and [1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1s1-3), we defined a linear regression model as *X*@*w*, or *nn.Linear(1,1)*. In Cell 05 of this project, we write extra codes to define the simple model. Usually, computer vision projects use many neural layers in their neural network models. The *nn.Sequential()* in Cell 05 can contain many kinds of mathematical operations to process and extract information from data. This is the way to define all computer vision models in big projects of this book. The function ‘forward’ in the class accepts input data and returns output data. In the last line of Cell 05, a model was defined as an instance of the LinearRegression class, and the model was moved to the memory of a graphics processing unit (GPU) by ‘cuda()’. CUDA's ability of parallel computing can significantly reduce model training time. In Cell 06, a loss function (criterion), model optimizer and learning rate scheduler are defined. A learning rate scheduler OneCycleLR is used here. This scheduler changes learning rate along all iterations of all epochs. Since there are three batches in each epoch, the 20 000 epochs have 60 000 iterations for the model training.

![](images/bk978-0-7503-6244-3ch1uf19_pr.gif)

 

In Cell 07, each batch of data x and y coming from the dataloader is sent to GPU by *cuda*(), because the model is in GPU. Model parameters k and b are printed out by codes on the last two lines in Cell 07. With the codes in Cell 08, the model training results are shown in three graphs (figure [1.6](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig6)). For the y\_hat calculations on line 06 of Cell 08, Data X in the dataset must be sent to GPU. Using matplotlib to plot y\_hat in figure [1.6](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig6)(A), we have to send y\_hat back to CPU. It is no surprise that the running time for this project with GPU is much longer than the running time of project [1.2.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn10). Many extra codes added to the project take extra time. For huge datasets, it is guaranteed that GPU saves model training time significantly.

![](images/bk978-0-7503-6244-3ch1uf20_pr.gif)

![Figure 1.6. Model training output graphs. (A): original data Y and predicted data y\_hat. (B): loss curve, (C): learning rate curve with OneCycleLR learning rate scheduler.](images/bk978-0-7503-6244-3ch1f6_online.jpg)

**Figure 1.6.** Model training output graphs. (A): original data Y and predicted data y\_hat. (B): loss curve, (C): learning rate curve with OneCycleLR learning rate scheduler.

Training models with a huge amount of data takes hours, days or even weeks. After your computer is turned off, all those good parameters of your trained models disappear. It is painful to take a long time to train the model again. We need to save parameters of trained models so that we can use them for later applications. To save a trained model, you need a file name, for example: File\_name = ‘d:/model4LR.pth’, and then use the code ‘torch.save(model, File\_name)’. The trained linear regression model defined in Cell 05 would be saved by codes in Cell 09.

![](images/bk978-0-7503-6244-3ch1uf21_pr.gif)

To avoid confusion, I use ‘saved\_model’ as the name of the model loaded from the saved file in Cell 10. Before using the loaded model, we have to set the saved model for evaluation by the code *saved\_model.eval()* after the model is loaded. With the last line in Cell 10, the trained model's parameters are printed out. You can see that the two parameters are right, and the saved model is in GPU. Using codes in Cell 11, you will find that the loaded model works. There are more methods to save trained models. The second method is only saving the model parameters to a file. Just by reloading those parameters in the file to the model, we can reuse the trained model. You can try the second method by running Cell 12–14.

![](images/bk978-0-7503-6244-3ch1uf22_pr.gif)

 

The third method is to save a check-point of a trained model during training. Big computer vision projects need many days for model training. We have to restart model training from a check-point saved on a previous day. In Cell 15, you can see that the model's parameters, the optimizer's parameters, the loss function, and learning rate scheduler are all saved in a file. You can reload those parameters by running codes in Cell 16.

![](images/bk978-0-7503-6244-3ch1uf23_pr.gif)

### 1.5 Activation functions for nonlinear regressions

Our world is beautiful because many phenomena are nonlinear. In computer vision projects, we have to use multiple neural layers to handle nonlinear mathematical problems. However, multiple linear layers in a sequence of a model work just like a single linear layer. For example, in case our model has two fully connected linear layers: *Y*[1] = *w*[1]*X*+*b*[1] and *Y*[2] = *w*[2]*Y*[1]+*b*[2], we will get *Y*[2] = *w*[2]*w*[1]*X*+(*w*[2]*b*[1]\+ *b*[2]) which is still a linear layer. To avoid the mathematical issue, we have to add an activation function between two linear layers. There are many kinds of activation functions, and they are all nonlinear. The following are four commonly used classes for activating functions:

1.  sigmoid class nn.Sigmoid(): f(*x*) = $\\frac{1}{1 + e^{- x}}$inline-graphic style="height:1.8125em;" xlink:href="bk978-0-7503-6244-3ch1ieqn61.gif"/
2.  hyperbolic class class nn.Tanh(): f(*x*) = $\\frac{e^{x} - e^{- x}}{e^{x} + e^{- x}}$inline-graphic style="height:1.875em;" xlink:href="bk978-0-7503-6244-3ch1ieqn62.gif"/
3.  rectified linear unit class nn.ReLU(): f(*x*) = $\\left\\{ \\begin{matrix} {x\\ \\left( {x \\geqslant 0} \\right)} \\\\ {0\\ \\left( {x < 0} \\right)} \\\\ \\end{matrix} \\right.$inline-graphic style="height:3.0625em;" xlink:href="bk978-0-7503-6244-3ch1ieqn63.gif"/
4.  leaky ReLU class nn.LeakyReLU(0.1): f(*x*) = $\\left\\{ \\begin{matrix} {x\\ \\left( {x \\geqslant 0} \\right)} \\\\ {0.1x\\ \\left( {\\ x < 0} \\right)} \\\\ \\end{matrix} \\right.$inline-graphic style="height:3.0625em;" xlink:href="bk978-0-7503-6244-3ch1ieqn64.gif"/

 

We will use the sigmoid class for a activate function in a nonlinear regression for *y*(*x*) *\= e*^(*−*5*x*) in project [1.5.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn30). The variable *x* in all the activation functions can be a scalar or an array. If the input of the sigmoid function is an array or matrix, the sigmoid function element-wisely acts on the array. Each element's value of the sigmoid function's output is in the range \[0,1\]. In the project, a csv data file was created from the function *y*(*x*) *\= e*^(*−*5*x*), where *x* is between 0.0 and 1.0. The length of the *x* array is 51. We would like to use a model with two fully connected layers to simulate this exponential function.

![](images/bk978-0-7503-6244-3ch1uf24_pr.gif)

 

A csv file named ‘d:/nonlinearF.csv’ was input and converted into a dataset in Cell 03. With the batch size being set to be equal to 17, the dataset is sliced into three batches in a dataloader. The data in the dataset is shown in a graph by codes in Cell 04. A model in Cell 05 with two layers is defined. The first layer and the last layer are fully connected layers. Between them is a sigmoid activation class which has no parameters. A learning rate scheduler OneCycleLR is used in the project, and its option ‘anneal\_strategy’ is set to be ‘linear’, not ‘cos’ as before.

![](images/bk978-0-7503-6244-3ch1uf25_pr.gif)

 

Model training results are shown in figures [1.7](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig7). From figure [1.7](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig7)(A), we can see that the nonlinear regression is very good. Between the model outputs y\_hat and the target y, the absolute maximum difference is about 7.5 × 10^(−4). By using the code ‘p = list(model.parameters()); print(p)’ in Cell 08, we get four tensors. The first two are the weight p\[0\] and bias p\[1\] of the first fully connected layer. The last two are the weight p\[2\] and bias p\[3\] of the last fully connected layer. All of them are stored in GPU, and their ‘requires\_grad’ options are true. The following formula is what we obtained from the model training. Running codes in Cell 08, you would know how the model parameters are used in the following formula. Neural networks are very powerful to simulate any mathematical functions. In bigger projects, models have many neural layers and many parameters. We are not able to give the right side of the following formula, and it is not necessary.

  
*e*^( − 5*X*) = model(*X*) = \[*σ*(*X*@*p*\[0\]^(*T*)+*p*\[1\])\]@*p*\[2\]^(*T*) + *p*\[3\]  
graphic style="width:22.875em;" xlink:href="bk978-0-7503-6244-3ch1ueqn65.gif" position="float"/

![](images/bk978-0-7503-6244-3ch1uf26_pr.gif)

![Figure 1.7. Nonlinear regression results for y(x) = exp(−5x). (A) Ground truth Y and the predicted curve y\_hat. (B) Loss curve. (C) Learning rates of OneCycleLR with anneal\_strategy = ‘linear’.](images/bk978-0-7503-6244-3ch1f7_online.jpg)

**Figure 1.7.** Nonlinear regression results for y(x) = exp(−5x). (A) Ground truth Y and the predicted curve y\_hat. (B) Loss curve. (C) Learning rates of OneCycleLR with anneal\_strategy = ‘linear’.

### References

Dempster A P, Laird N M and Rubin D B 1977 Maximum likelihood from incomplete data via the EM algorithm *J. Royal Stat. Soc. Ser. B (Methodol.)* **39** 1–38

Hilt D E, Seegrist D W, United States Forest S and Northeastern Forest Experiment S 1977 *Ridge, a Computer Program for Calculating Ridge Regression Estimates* (Upper Darby, PA: Dept. of Agriculture, Forest Service, Northeastern Forest Experiment Station)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 2

## Image classifications by convolutional neural networks

This chapter is about constructing and using convolution neural networks (models) to classify images in two simple labeled datasets: MNIST and CIFAR-10. Transfer learning is introduced to use pre-trained models for the Vegetable Images dataset image classification. A confusion matrix obtained in the MNIST image classification project is used to show how to calculate some metrics of model training: recall, precision, f1\_score and intersection over union (IOU).

It is easy for human babies to know what they are seeing (image classification), even though they may be confused by their parents' ‘twin’. Image classification is a branch of computer vision which started in the 1960s. After more than 60 years, the intelligence of computers on image classification has surpassed human beings. Today, smart cameras beside traffic lights in cities can read the licence plates of moving cars; cell phones can recognize users’ faces. Image classification is used in a wide range of applications, including self-driving cars and biomedical diagnosis systems. We should attribute the successes of computer vision to the artificial intelligence theories of many pioneers, more powerful computer hardware, and many free datasets with huge amounts of data. Three datasets are used to train image classification algorithms or models in this chapter. They are MNIST, CIFAR-10 and Vegetable Images. These image datasets have labels with which we train our models for supervised learning. Just like showing animal pictures in a book to a three-year old child, you tell the child: ‘that is a dog, that is a cat, or that is a bird.’ The child's brain is trained by the labeled pictures. Later, the child is taken outside and shown real animals and is then asked many times: ‘What is the name of that animal?’ in different environments. The right percentage of the child's answers is a benchmark that indicates how well the child was trained. In the same way, after training of an image classification model with an image dataset, your model can predict if there is a cat, a dog, a bird or a digit ‘5’ on a photo in a dataset. A well-trained model may have a million parameters. These parameters and the structure of the model can be saved and written into integrated circuit (IC) chips for specific applications.

### 2.1 Classification of hand written digits in the MNIST database

MNIST (Modified National Institute of Standards and Technology) is the most famous database (LeCun *et al* [1998](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2bib4)) for computer vision. It is often used as a benchmark for testing machine learning algorithms. We should keep in mind that the MNIST dataset is a very simple dataset, even a model with two fully connected neural layers can achieve 98% accuracy. A model that performs well on MNIST does not mean it works well on other datasets. The MNIST dataset is often used as a starting point for testing and developing machine learning models. The MNIST dataset has a train dataset and a test dataset, and they have 60 000 and 10 000 black and white images, respectively. All images have a same resolution: 28 × 28. The train dataset is used to train a model, and the test dataset is used to check if the trained model has ‘overfitting’ issues. Having this issue, a trained model has higher predication accuracy for the train dataset, but lower accuracy for its test dataset. This phenomenon may happen because our computers are very powerful in remembering detailed structures (noises) in our train datasets. Those detailed structures could be different in different images. To avoid overfitting, we even slice the MNIST train dataset into a smaller train dataset with 50 000 images and a validation dataset with 10 000 images for model training.

Before the ancient Egyptians built their pyramids, they must have their tools ready for measuring, cutting and moving those big cubic stones. For our MNIST image classification codes in project [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn1), we also need tools ready. Those tools are the Python and PyTorch libraries. With them, we can load datasets into computers from the internet, slice a dataset into a dataloader, and display them on computer screens. Codes in Cell 01 of the following project provide these tools. Among those tools, Torchvision is new to us. Torchvision is a library and is a part of PyTorch. In this library, there are many popular datasets to download, many pre-trained models to use, and many image transformation operations to reduce overfitting issues. Torchvision was installed after PyTorch was installed in VS Code. Many hyperparameters such as batch size and learning rate are also set in Cell 01. How can our model be trained to read digitals in MNIST images? Our model really doesn’t read 2D images in the same way that our eyes read. In this project, our model has two fully connected layers. Those 28 × 28 pixels of each image are flattened into a 1D tensor with 784 elements. The simple model only extracts statistic information (probabilities) from these data. With the statistics information, the model's prediction accuracy will be more than 98%.

With codes in Cell 02, the MNIST database can be downloaded from the internet if the data path on your hard disk is empty and the MNIST option is set to be ‘download = True’ on line 01 and 04. The total size of compressed MNIST image files downloaded from the MNIST dataset source is about 116 MB. If the database is already downloaded on your computer, you should set the download option to be ‘False’, and the image data would then be read from a file path set on the last line of Cell 01. A dot in the data path string on the last line of Cell 01 means the current working directory of VS Code. You can find it by running ‘import os; os.getcwd()’ in an extra cell. You can also use an absolute data path. With the train option to be ‘True’, images of the train dataset inside the compressed file would be loaded; or if ‘train = False’, images of the test dataset inside the compressed file would be loaded. Each image pixel in the MNIST images is an 8-bit integer (0–255). With a transform function on line 02 and 05 in Cell 02, pixel values of each image are converted into float32 tensors in a range \[0.0, 1.0\].

![](images/bk978-0-7503-6244-3ch2uf1_pr.gif)

 

Using codes in Cell 03, we slice the two datasets into two dataloaders, respectively, by using a PyTorch DataLoader class. With a smaller batch size, we need a longer time for model training, and we get better training results. When you have GPU memory issues (out of memory), reducing the batch size parameter is a solution. To reduce the ‘overfitting’ issue of model training, we set the shuffle option to be True on the first line of Cell 03, so the train dataloader is constructed with samples randomly chosen from the dataset. The test dataloader is used to verify if the trained model has overfitting issues, and it does not need to be randomly packed. From the outputs of Cell 04, we can see that a batch of the train dataloader has 32 images, each image has one channel, and the resolution of each image is 28 × 28. An image with one channel is a black and white image, and an image with three channels is a color image. Also, each image in the dataset has a label which is the number shown by the photo. We can display the last image of the test dataset by using codes in an extra cell after Cell 04: ‘img, \_ = test\_dataset\[−1\]; plt.imshow(img.permute(1,2,0));’.

A function named ‘show\_images’ is defined in Cell 04. The input of the function is a batch of images from a dataloader. In a for-loop of Cell 03, only the first batch of images is picked out to display. Using a *torchvision.utils* module *make\_grid*, we combine all small images in the batch into a bigger image. The number of small images in each row of the bigger image is set by an option ‘nrow’ on line 03 of Cell 04. The space around each small image is set by another parameter ‘padding’. By default, ‘padding’ is equal to 2 pixels. Every time you run the function ‘show\_images’, you will see a different bigger image such as one shown in figure [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig1), because of the option s*huffle = True* setting for the train dataloader in Cell 02. By using the test dataloader as an input of the function, you will see that the bigger image does not change.

![Figure 2.1. MNIST images in a batch of the train dataloader with a batch size of 32. Reproduced from Deng (2012) CC BY 3.0.](images/bk978-0-7503-6244-3ch2f1_online.jpg)

**Figure 2.1.** MNIST images in a batch of the train dataloader with a batch size of 32. Reproduced from Deng ([2012](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2bib5)) CC BY 3.0.

Running the two following extra cells after Cell 04, you will know more about the *make\_grid* and *permute* operations for displaying images. In Extra Cell ONE, a tensor named ‘my\_imgs’ is generated by 16 integers from 0 to 15. These 16 integers are packed into a tensor with a shape of 4 × 1 × 2 × 2. We can say that the tensor has four rows and one column, and each element of the 4 × 1 tensor is a 2 × 2 tensor. In computer vision, we would say that the image tensor contains four images, each image has one channel and the image resolution is 2 × 2. It is a surprise to see that the bigger image named ‘big\_img’ in the Extra Cell ONE has the same three channels, and the shape of the bigger image is 3 × 4 × 4. If you change the padding parameter to 1 or 2, the shape of the bigger image would be changed to 3 × 7 × 7 or 3 × 10 × 10. Each element's value of those extra rows and columns is zero. Keeping the padding set to zero and changing the ‘nrow’ parameter from 1 to 5, you would see some things you would not know.

![](images/bk978-0-7503-6244-3ch2uf2_pr.gif)

  
$$\\begin{matrix} \\begin{bmatrix} 0 & 1 \\\\ 2 & 3 \\\\ \\end{bmatrix} \\\\ \\begin{bmatrix} 4 & 5 \\\\ 6 & 7 \\\\ \\end{bmatrix} \\\\ \\begin{bmatrix} 8 & 9 \\\\ 10 & 11 \\\\ \\end{bmatrix} \\\\ \\begin{bmatrix} 12 & 13 \\\\ 14 & 15 \\\\ \\end{bmatrix} \\\\ \\end{matrix}\\begin{bmatrix} 0 & 1 & 4 & 5 \\\\ 2 & 3 & 6 & 7 \\\\ 8 & 9 & 12 & 13 \\\\ 10 & 11 & 14 & 15 \\\\ \\end{bmatrix}\\begin{bmatrix} 0 & 1 & 4 & 5 \\\\ 2 & 3 & 6 & 7 \\\\ 8 & 9 & 12 & 13 \\\\ 10 & 11 & 14 & 15 \\\\ \\end{bmatrix}\\begin{bmatrix} 0 & 1 & 4 & 5 \\\\ 2 & 3 & 6 & 7 \\\\ 8 & 9 & 12 & 13 \\\\ 10 & 11 & 14 & 15 \\\\ \\end{bmatrix}$$  
graphic style="width:24.625em;" xlink:href="bk978-0-7503-6244-3ch2ueqn1.gif" position="float"/

 

Now we can explain why the shape of the bigger image is 3 × 62 × 482 in Cell 04. Any black and white image processed by module *make\_grid()* would become an image with the same three channels. By arranging 32 MNIST images into a 2 × 16 array with padding = 2 for a bigger image, the height and the width of the big image should be \[(28 + 2) × 2 + 2\] and \[(28 + 2) × 16 + 2\], respectively. Using the *imshow()* function from *matplotlib.pyplot* to show the big image with a shape 3 × 62 × 482, we have to permute the big image so that its shape is changed to 62 × 482 × 3. With codes in the above Extra Cell TWO, we practice how to view a 3D tensor at different angles by the permutation function. The permutation operation to a tensor does not change the tensor, but only the view shape of the tensor.

In the above Extra Cell TWO, 18 integers were reshaped into a 2 × 3 × 3 tensor. This 3D tensor has three axes Dim\_0, Dim\_1 and Dim\_2 as shown in figure [2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig2). The directions of the three axes follow a left-hand role: if the thumb, the index finger and the middle finger of your left hand are perpendicular to each other, the index finger points to Dim\_0, the middle finger points to Dim\_1, and the thumb points to Dim\_2. We view the tensor along the direction of the Dim\_0 axis; our noses are in the Dim\_1 direction; and the direction of a line linking your left eye to our right eye is in the direction of Dim\_2. The 3D tensor is sliced on planes perpendicular to the Dim\_0. This is the normal view angle to the 3D tensor. With the code *x.permute(1,2,0)*, we should look at the tensor from the top along Dim\_1. The tensor should be sliced by horizontal planes, and the top plane is shown in the figure. With our noses in the Dim\_2 direction, we obtain three sub-tensors and each of them has three rows and two columns.

![](images/bk978-0-7503-6244-3ch2uf3_pr.gif)

![Figure 2.2. (Left) A normal view for a 3D tensor created by codes in extra cell two: your eyes look along Dim\_0, your nose is along Dim\_1, and a line linked your two eyes is parallel with Dim\_2. (Right) Three sub-tensors of the permuted tensor are on three planes perpendicular to Dim 1.](images/bk978-0-7503-6244-3ch2f2_online.jpg)

**Figure 2.2.** (Left) A normal view for a 3D tensor created by codes in extra cell two: your eyes look along Dim\_0, your nose is along Dim\_1, and a line linked your two eyes is parallel with Dim\_2. (Right) Three sub-tensors of the permuted tensor are on three planes perpendicular to Dim 1.

In the model defined in Cell 05, there are two fully connected layers. One of them is *nn.Linear(784, 100)* and the other is *nn.Linear(100, 10)*. Between them is an activation class *nn.ReLU()*. It is not *nn.Sigmoid()*. You can still use the sigmoid class for an activation function, if you want. The ReLU activation function sets all negative numbers to be zero, and keeps any positive number as it is. It works well and takes less time for calculations. The model does not really analyze 2D images. Each 2D image's 28 × 28 pixels are converted into a 1D tensor with 784 elements in the forward function of the model. For each batch of the train dataloader with 32 images, the input of the model is a tensor with a shape of 32 × 784. The output of the first layer is a tensor of shape 32 × 100, and the output of the last layer is a tensor of shape 32 × 10.

In chapter [1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1), we used an MSE loss function for continuous variables. For the MNIST image classification project, the targets are discrete integers 0, 1, …, 9 about image class identities. A cross-entropy loss function is used for image classifications. Codes of the following Extra Cell THREE are used to show you how a cross-entropy loss function works. In the extra cell, a 1D tensor \[2,1,0\] named ‘targets’ is supposed to be a 1D tensor of image labels from a batch of a dataloader (line 03), and a 3 × 4 tensor named ‘y\_hat’ is supposed to be an output of a model (line 06). In this example, the batch size of a dataloader is three and the total number of image classes in the dataset is four. With them, the criterion or loss function nn.CrossEntropyLoss() directly gives you the loss function value on the last line of the extra cell. We should know that the cross-entropy loss function does some extra work to the outputs of any image classification model.

![](images/bk978-0-7503-6244-3ch2uf4_pr.gif)

  
$$s\\left( \\begin{bmatrix} {\\widehat{y}}\_{1,1} & {\\widehat{y}}\_{1,2} & \\ldots & {\\widehat{y}}\_{1,m} \\\\ {\\widehat{y}}\_{2,1} & {\\widehat{y}}\_{2,2} & \\ldots & {\\widehat{y}}\_{2,m} \\\\ \\ldots & \\ldots & \\ldots & \\ldots \\\\ {\\widehat{y}}\_{n,1} & {\\widehat{y}}\_{n,2} & \\ldots & {\\widehat{y}}\_{n,m} \\\\ \\end{bmatrix} \\right) = \\begin{bmatrix} \\frac{e^{{\\widehat{y}}\_{1,1}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{1,k}}} & \\frac{e^{{\\widehat{y}}\_{1,2}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{1,k}}} & \\ldots & \\frac{e^{{\\widehat{y}}\_{1,m}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{1,k}}} \\\\ \\frac{e^{{\\widehat{y}}\_{2,1}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{2,k}}} & \\frac{e^{{\\widehat{y}}\_{2,2}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{2,k}}} & \\ldots & \\frac{e^{{\\widehat{y}}\_{2,m}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{2,k}}} \\\\ \\ldots & \\ldots & \\ldots & \\ldots \\\\ \\frac{e^{{\\widehat{y}}\_{n,1}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{n,k}}} & \\frac{e^{{\\widehat{y}}\_{n,2}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{n,k}}} & \\ldots & \\frac{e^{{\\widehat{y}}\_{n,m}}}{\\sum\\limits\_{k = 1}^{m}e^{{\\widehat{y}}\_{n,k}}} \\\\ \\end{bmatrix} = \\widehat{Y}$$  
(2.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch2eqn2.gif" position="float"/

  
$$H\\left( { p,q} \\right) = - \\sum\\limits\_{i = 1}^{n}{\\sum\\limits\_{j = 1}^{m}{p\_{i,j}\\ \\ln\\ \\left( {\\widehat{Y}}\_{i,j} \\right)}}$$  
(2.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch2eqn3.gif" position="float"/

 

On the left hand side of equation ([2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn1)), a *ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn4.gif"/ tensor is an output of a model for a batch of images in a dataloader, where *n* is the batch size. In the example of the Extra Cell THREE, the batch size is three. The *ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn5.gif"/ tensor has *m* columns for *m* classes in the dataset. In the same example of the Extra Cell THREE, *m* is equal to 4. The first line of the Extra Cell FOUR uses a SoftMax function which acts on each element of each row of the *ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn6.gif"/ tensor with an option dim = 1 as shown in equation ([2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn1)). In this way, the sum of each row of the *Ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn7.gif"/ tensor on the right side of equation ([2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn1)) is equal to one. The tensor *Ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn8.gif"/ is used to represent the result of the SoftMax operation to the *ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn9.gif"/ tensor. Then the 1 × *n* tensor ‘targets = \[2,1,0\]’ is hot-coded into a (*n* × *m*) target tensor named ‘p’ on line 03 in Extra Cell FOUR. The values of most elements in tensor p are zeros, and only p\[0,2\], p\[1,1\], p\[2,0\] are set to be 1. The cross entropy is then calculated according to equation ([1.7](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn7)) which is modified as equation ([2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn2)). The only non-zero element on each row of tensor p is used to pick out an element at the same location of *Ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn10.gif"/ for cross-entropy calculations. Since these mathematical operations are automatically finished by the cross-entropy loss function, we do not need to mention the SoftMax operation in image classification models.

![](images/bk978-0-7503-6244-3ch2uf5_pr.gif)

 

In Cell 06, the ‘model.train()’ function sets the model for training, so that gradients of the loss function to model parameters will be calculates. In a for-loop, each batch of images and labels in the train dataloader are loaded into GPU memory by ‘*cuda*()’. After being processed by the SoftMax function on each row of the model's output, the *Ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch2ieqn11.gif"/ tensor has a maximum number on each row. With the *torch.argmax* function, we can find a column index on each row at which the maximum number can be found. These indices are stored in a 1 × 32 tensor named *predictions* on line 07 of Cell 06. On the next line, the sum of correct prediction numbers is found with *torch.sum(predictions = = targets)*. Running the codes in an extra cell ‘a = torch.tensor(\[1,0,3,2\]); b = torch.tensor(\[1,2,3,1\]); torch.sum(a = = b)’, you will know how to find the sum of matched elements in two 1D tensors. The remaining codes in Cell 06 are not new. Since the loss function has an option ‘reduction = ‘sum'’, the value of the variable named ‘total\_loss’ was divided by 60 000, the total images in the train dataset. Also, the variable ‘n\_correct’ records the number of correct predictions for labels in the dataset. The returned value of 100\*n\_correct/60000 gives an accurate prediction percentage. Cell 07 is used for ‘test\_dataloader’ to check if the trained model has overfitting issues. The code *model.eval()* in the cell sets the model for evaluation (without gradient calculations). The outputs of Cell 07 are test loss and test accuracy. In Cell 08, a pandas dataframe is used to record training history. A returned dataframe is used in Cell 09 to plot train results.

![](images/bk978-0-7503-6244-3ch2uf6_pr.gif)

 

We have to use a test dataset for model training to find the overfitting issues for the classification accuracies. The test accuracy should be lower than the train accuracy. Figure [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig3) shows that the prediction accuracy for the test dataset is about 2% lower than that of the train dataset. At the beginning of the model training, model parameters are randomly set by PyTorch, and the model was not well-trained, so the test accuracy may be higher than the train accuracy. The model training has some overfitting issues based on the accuracy and loss graphs. This is normal for model training. Both Adam and SGD optimizers could be used for the model training, and the test accuracies are about 98%. If the model only has one neural layer with code *nn.Linear(784,10)*, the test accuracy is over 92%. If the model has three fully connected layers and two activation functions, the test accuracy is still around 98%. From the output of Cell 10, you will find that the simple model has 79 510 parameters. To increase the test classification accuracy, we need to use a model with different algorithms and more parameters.

![Figure 2.3. Model training results with SGD optimizer. (Left) MNIST classification accuracies, (Right): Loss curves.](images/bk978-0-7503-6244-3ch2f3_online.jpg)

**Figure 2.3.** Model training results with SGD optimizer. (Left) MNIST classification accuracies, (Right): Loss curves.

In computer vision projects for image classification, image segmentation, and object detection, the first metrics used to evaluate model training is accuracy, but it is not enough. From a confusion matrix (table [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2t1)) obtained by codes in Cell 11 about the test dataset, four more metrics (table [2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2t2)) can be obtained for detailed information about model training results. In the confusion matrix table, class names in the left column are for labels of ground truth, and class names in the top row are for predicted labels from the trained model. We will only use the row with the class name ‘Five’ about the digit 5 as an example to explain the confusion matrix. Out of 892 images for the digit 5, only 870 predicted correctly. Two digit 5 were predicted as 0, eight digit 5 were predicted as 3, …, one digit 5 was predicted as 9. For a confusion table about the train dataset, all numbers are zeros except10 numbers on the diagonal. Those 10 numbers on the diagonal of the confusion matrix in table [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2t1) are true positive (TP) values of 10 classes. The summation of a row of the table has the name ‘support’ which is equal to the total ground truth of a class. A support has two parts: the true positive (TP) and false negative (FN) of the class. A metric named ‘**recall**’ is equal to the ratio of TP and (TP+FN). It is about the percentage of correct predictions out of the ground truth of a class.

![](images/bk978-0-7503-6244-3ch2uf7_pr.gif)

**Table 2.1.** A confusion matrix for test dataset.

| Class  || Prediction |
| --- | --- |
| Zero || One || Two || Three || Four || Five || Six || Seven || Eight || Nine |
| **Ground truth** || Zero || 969 || 1 || 1 || 0 || 2 || 2 || 2 || 1 || 1 || 1 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| One || 0 || 1122 || 3 || 2 || 0 || 1 || 2 || 1 || 3 || 1 |
| Two || 4 || 3 || 1006 || 4 || 3 || 1 || 2 || 4 || 5 || 0 |
| Three || 0 || 0 || 7 || 987 || 0 || 3 || 0 || 2 || 5 || 6 |
| Four || 1 || 0 || 2 || 0 || 962 || 0 || 4 || 4 || 1 || 8 |
| Five || 2 || 0 || 0 || 8 || 1 || 870 || 5 || 0 || 5 || 1 |
| Six || 3 || 2 || 1 || 1 || 5 || 6 || 939 || 1 || 0 || 0 |
| Seven || 1 || 2 || 7 || 1 || 0 || 0 || 0 || 1006 || 6 || 5 |
| Eight || 4 || 0 || 2 || 2 || 2 || 1 || 0 || 2 || 958 || 3 |
| Nine || 2 || 2 || 0 || 2 || 7 || 2 || 1 || 5 || 3 || 985 |

**Table 2.2.** Evaluation metrics for test dataset.

| Class || precision || recall || f1\_score || IOU || support |
| --- | --- | --- | --- | --- | --- |
| **Zero** || 0.983 || 0.989 || 0.986 || 0.972 || 980 |
| --- | --- | --- | --- | --- | --- |
| **One** || 0.991 || 0.989 || 0.990 || 0.980 || 1135 |
| **Two** || 0.978 || 0.975 || 0.976 || 0.954 || 1032 |
| **Three** || 0.980 || 0.977 || 0.979 || 0.958 || 1010 |
| **Four** || 0.980 || 0.980 || 0.980 || 0.960 || 982 |
| **Five** || 0.982 || 0.975 || 0.979 || 0.958 || 892 |
| **Six** || 0.983 || 0.980 || 0.982 || 0.964 || 958 |
| **Seven** || 0.981 || 0.979 || 0.980 || 0.960 || 1028 |
| **Eight** || 0.971 || 0.984 || 0.977 || 0.955 || 974 |
| **Nine** || 0.975 || 0.976 || 0.976 || 0.953 || 1009 |
| **macro\_avg** || 0.980 || 0.980 || 0.980 || 0.961 || 10 000 |
| **weighted\_avg** || 0.981 || 0.981 || 0.981 || 0.962 || Acc = 0.98 |

The summation of a column of the confusion matrix has the name ‘Prediction’ which also has two parts: the true positive (TP) and false positive (FP) of the class. A metric named ‘**precision**’ is equal to the ratio of TP and (TP+FP). It is the percentage of correct predictions in the predictions for a class. A harmonic mean of the precision and the recall is a metric called **F1 score**: 2TP/(2TP+FP+FN). The last metric is intersection over union (**IOU**) which also has another name: **Jaccard score**: TP/(TP+FP+FN). It is an important evaluation metric for object detection. The above four evaluation metrics are listed in table [2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2t2) for all 10 classes in the test dataset. They are the outputs of a function defined in Cell 12 applied to the test dataset. There are two kinds of average for the four metrics. The **macro average** of a metric is the average of 10 numbers of a class in a column of table [2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2t2). The metric value of each class has the same weight. The lower-right corner cell of the metrics table is for the accuracy of model training. Its value matches the last point of a corresponding accuracy curve shown in figure [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig3)(A). Above the cell of the accuracy number is the number of total samples in the test dataset: 10 000. A support number of a class in the right column divided by the total sample number is the weight of a class for the **weighted average** calculations.

![](images/bk978-0-7503-6244-3ch2uf8_pr.gif)

### 2.2 Mathematical operations of a 2D convolution

A convolutional neural network (CNN) uses a small 4D tensor to extract important local patterns on images, such as horizontal lines ‘-’, vertical lines ‘∣’, cross lines ‘ × ’, etc. The small 4D tensor is the kernel of a 2D convolution. Convolutional kernels are digital sensors. Before you know how a convolutional neural network works, I would like to show you how powerful a CNN is in the above MNIST classification project. Using the following codes to replace those codes in Cell 05 of project [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn1), you will find that the classification accuracy for the test dataset is up to 99.5%.

![](images/bk978-0-7503-6244-3ch2uf9_pr.gif)

 

In the above CNN model, a PyTorch class *nn.Conv2d*() is used. It has many options to set, such as: input channels, output channels, kernel size, stride, padding, bias, etc. There are many YouTube videos teaching the mathematics of convolution operators. I would like to use the following two examples to make it easier to understand the complex convolution operations. For mathematical convenience, we just use square tensors whose row number and column number are the same. The convolution class is also powerful to handle rectangular tensors

  
$$X = \\begin{bmatrix} 0 & 1 & 2 & 3 \\\\ 4 & 5 & 6 & 7 \\\\ 8 & 9 & 10 & 11 \\\\ 12 & 13 & 14 & 15 \\\\ \\end{bmatrix},\\ K = \\begin{bmatrix} \\underset{¯}{0} & \\underset{¯}{1} \\\\ \\underset{¯}{2} & \\underset{¯}{3} \\\\ \\end{bmatrix},{conv}2d\\left( {X,K} \\right) = \\begin{bmatrix} 24 & 30 & 36 \\\\ 48 & 54 & 60 \\\\ 72 & 78 & 84 \\\\ \\end{bmatrix}$$  
graphic style="width:28.625em;" xlink:href="bk978-0-7503-6244-3ch2ueqn12.gif" position="float"/

The sizes of the above tensor *X* and *K* are 4 × 4 and 2 × 2 respectively. The underlined digits in the tensor *K* are used to distinguish the digits from the digits in the tensor *X*. Two constants *n* and *f* are used to represent sizes of *X* and *K*, respectively (*n* = 4, *f* = 2). At the beginning of a manual convolution operation, the tensor *K* is moved on top of the tensor *X* with an element *K*($\\underset{}{0}$inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch2ieqn13.gif"/) and an element *X*(0) at the same position. Then each of the four elements of tensor *K* is multiplied by an element of tensor *X* in the same position. The sum of these products is the first element of the convolution: 24 = $\\underset{¯}{0}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn14.gif"/ × 0 + $\\underset{¯}{1}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn15.gif"/ × 1 + $\\underset{¯}{2}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn16.gif"/ × 4 + $\\underset{¯}{3}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn17.gif"/ × 5. Then tensor *K* is shifted to the right side by a step of one column with *K*(0) on the top of *X*(1). The moving distance (*s*) has a name ‘stride’. By default, *s* is equal to one. After calculations, tensor *K* is moved again with *K*($\\underset{}{0}$inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch2ieqn18.gif"/) on the top of *X*(2). The maximum steps that the tensor *K* can be moved horizontally is equal to \[(*n* − *f*)/*s* + 1\] which sets the size of the convolution operator's output to be three for this example. Then tensor *K* is moved to a position where *K*($\\underset{}{0}$inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch2ieqn19.gif"/) is on the top of *X*(4). These moving and calculation processes continue to the last block where *K*($\\underset{}{0}$inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch2ieqn20.gif"/) is on top of *X*(10): 84 =

$\\underset{¯}{0}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn21.gif"/ × 10 + $\\underset{¯}{1}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn22.gif"/ × 11 + $\\underset{¯}{2}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn23.gif"/ × 14 + $\\underset{¯}{3}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn24.gif"/ × 15. The following code is used to do the above job.

![](images/bk978-0-7503-6244-3ch2uf10_pr.gif)

 

If the value of \[(*n* − *f*)/*s* is a fraction, we just take the integer part of the fraction. To avoid an issue of image size shrinking from convolution operators, we can add extra rows and columns filled with zeros around tensor *X*. This operation is called ‘padding’. A constant named *p* is used for the padding. If *p* is set to be one for the above tensor *X*, then the sizes of the above convolution output should be \[(*n* − *f + 2 × 1*)/*s* + 1\]. By default, the stride is equal to one, but stride could be two, three or a bigger integer. Using a bigger stride number, we may reduce model training time, but would lose detailed information about images. Considering all these parameters, we have the output size of a convolution:

  
$$m = \\frac{n - f + 2p}{s} + 1$$  
(2.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch2eqn25.gif" position="float"/

It is not necessary for us to define our own convolution functions. PyTorch has a class *nn.Conv2d*() for image convolution operations, and we just need to know how to use it. The following example is about using a PyTorch convolution for another tensor *X* and another tensor *K*. The convolution results are also shown below. The names of subunits of these tensors are written on their lower-right corners for readers, not for Python codes. For example, the tensor *X* has two channels or subunits: *X*[0] and *X*[1]. The shape of tensor *X* is: X.shape = 1 × 2 × 4 × 4, and the shape of the kernel *K* is: K.shape = 3 × 2 × 2 × 2. The shape of the convolution output *Y* is: Y.shape = 1 × 3 × *m*², where *m* is set by equation ([2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn3)). The dimensional relationships of these tensors are: Y.shape\[0\] = X.shape\[0\], Y.shape\[1\] = K.shape\[0\] and X.shape\[1\] = K.shape\[1\]. Dimension ONE of X and K should be the same for convolutions. The last two dimensions of a kernel could be 1 × 1, 2 × 2, 3 × 3, 4 × 4 or even 7 × 7 for bigger images.

![](images/bk978-0-7503-6244-3ch2uf11_pr.gif)

  
$$X = \\begin{bmatrix} \\begin{bmatrix} 0 & 1 & 2 & 3 \\\\ 4 & 5 & 6 & 7 \\\\ 8 & 9 & 10 & 11 \\\\ 12 & 13 & 14 & 15 \\\\ \\end{bmatrix}\_{X\_{0}} & \\begin{bmatrix} 16 & 17 & 18 & 19 \\\\ 20 & 21 & 22 & 23 \\\\ 24 & 25 & 26 & 27 \\\\ 28 & 29 & 30 & 31 \\\\ \\end{bmatrix}\_{X\_{1}} \\\\ \\end{bmatrix}$$  
graphic style="width:19.4375em;" xlink:href="bk978-0-7503-6244-3ch2ueqn26.gif" position="float"/

  
$$K = \\begin{bmatrix} \\begin{bmatrix} \\underset{¯}{0} & \\underset{¯}{1} \\\\ \\underset{¯}{2} & \\underset{¯}{3} \\\\ \\end{bmatrix}\_{K\_{00}} & \\begin{bmatrix} \\underset{¯}{4} & \\underset{¯}{5} \\\\ \\underset{¯}{6} & \\underset{¯}{7} \\\\ \\end{bmatrix}\_{K\_{01}} \\\\ \\begin{bmatrix} \\underset{¯}{8} & \\underset{¯}{9} \\\\ \\underset{¯}{10} & \\underset{¯}{11} \\\\ \\end{bmatrix}\_{K\_{10}} & \\begin{bmatrix} \\underset{¯}{12} & \\underset{¯}{13} \\\\ \\underset{¯}{14} & \\underset{¯}{15} \\\\ \\end{bmatrix}\_{K\_{11}} \\\\ \\begin{bmatrix} \\underset{¯}{16} & \\underset{¯}{17} \\\\ \\underset{¯}{18} & \\underset{¯}{19} \\\\ \\end{bmatrix}\_{K\_{20}} & \\begin{bmatrix} \\underset{¯}{20} & \\underset{¯}{21} \\\\ \\underset{¯}{22} & \\underset{¯}{23} \\\\ \\end{bmatrix}\_{K\_{21}} \\\\ \\end{bmatrix}$$  
graphic style="width:13.1875em;" xlink:href="bk978-0-7503-6244-3ch2ueqn27.gif" position="float"/

  
$$Y = \\begin{bmatrix} \\begin{bmatrix} 440 & 468 & 496 \\\\ 552 & 580 & 608 \\\\ 664 & 692 & 720 \\\\ \\end{bmatrix}\_{C\_{0}} & \\begin{bmatrix} 1112 & 1204 & 1296 \\\\ 1480 & 1572 & 1664 \\\\ 1848 & 1940 & 2032 \\\\ \\end{bmatrix}\_{C\_{1}} & \\begin{bmatrix} 1784 & 1940 & 2096 \\\\ 2408 & 2564 & 2720 \\\\ 3032 & 3188 & 3344 \\\\ \\end{bmatrix}\_{C\_{2}} \\\\ \\end{bmatrix}$$  
graphic style="width:30.5em;" xlink:href="bk978-0-7503-6244-3ch2ueqn28.gif" position="float"/

 

On the third line of the Extra Cell TWO, 32 integers from 0 to 31 were packed into a 1 × 2 × 4 × 4 tensor *X*. Because the convolution class only accepts a 4D float32 tensor, tensor *X* has to be converted into this type by an option *to(torch.float)*. On the sixth line of the Cell, an instance named ‘conv’ is defined for the class *nn.Conv2d()*. Its ‘in\_channels’ option is set to be equal to X.shape\[1\] = 2, its ‘out\_channels’ option is set to be equal to K.shape\[0\] = 3, and the kernel size option (*f*) is set to be equal to K.shape\[−1\] = 2. Default values are used for other options of the convolution, such as *s* = 1, *p* = 0, and bias = True. With these settings, we get *m* = 3. PyTorch automatically initializes weights and biases of the class's instance with random numbers for kernels. These parameters are learnable. With codes on lines from 07 to 10, we manually set the kernel with 24 integers by *nn.Parameter()*. Also, a 1 × 2 zero tensor is assigned to the bias of the convolution instance.

Only after being able to manually calculate the above convolution results, would you be comfortable using the convolution class. To manually obtain the first element of the first channel of the convolution's output *C*[0](440), we move *K*[00] and *K*[01] on top of *X*[0] and *X*[1] respectively, with *K*[00](*0*) and *X*[0](0) in the same position, also with *K*[01](*4*) and *X*[1](16) in the same position. The sum of eight multiplications with elements on the same locations is: 440 = ($\\underset{¯}{0}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn29.gif"/ × 0 + $\\underset{¯}{1}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn30.gif"/ × 1 + $\\underset{¯}{2}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn31.gif"/ × 4 + $\\underset{¯}{3}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn32.gif"/ × 5) + ($\\underset{¯}{4}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn33.gif"/ × 16 + $\\underset{¯}{5}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn34.gif"/ × 17 + $\\underset{¯}{6}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn35.gif"/ × 20 + $\\underset{¯}{7}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn36.gif"/ × 21). After *K*[00] and *K*[01] synchronously scanning over *X*[0] and *X*[1] respectively, the subunit *C*[0] of the convolution is obtained. The second and the third channel of the kernel repeat the same operations of the first channel of *K* to *X*. Finally, with *K*[20](*16*), *X*[0](10) in the same position, and *K*[21](*20*), *X*[1](26) in the same position, the last element of the convolution is obtained in this way: *C*[2](3344) = ($\\underset{¯}{16}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn37.gif"/ × 10 + $\\underset{¯}{17}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn38.gif"/ × 11 + $\\underset{¯}{18}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn39.gif"/ × 14 + $\\underset{¯}{19}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn40.gif"/ × 15) + ($\\underset{¯}{20}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn41.gif"/ × 26 + $\\underset{¯}{21}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn42.gif"/ × 27 + $\\underset{¯}{22}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn43.gif"/ × 30 + $\\underset{¯}{23}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn44.gif"/ × 31).

Codes in the following Extra Cell THREE are used to show you how to use kernels to find local patterns in images. An image tensor *X* in the cell is constructed by four 3 × 3 patches. The first one is for a horizontal line ‘-’ pattern; the second one is for a vertical line ‘∣’ pattern; the third one is for a cross ‘ × ’ pattern; and the last one is for a pattern which is the combination of the above three patterns. Those 3 × 3 patches for the first three patterns in tensor *X* are used as three filters of a kernel tensor K with a shape of 3 × 1 × 3 × 3. The outputs of the convolution of *X* with *K* and a MaxPool2d are shown below.

![](images/bk978-0-7503-6244-3ch2uf12_pr.gif)

  
$$X\_{0,0} = \\begin{bmatrix} 0 & 0 & 0 & 0 & 1 & 0 \\\\ 1 & 1 & 1 & 0 & 1 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 0 \\\\ 1 & 0 & 1 & \\underset{¯}{1} & 1 & \\underset{¯}{1} \\\\ 0 & 1 & 0 & \\underset{¯}{1} & 1 & \\underset{¯}{1} \\\\ 1 & 0 & 1 & \\underset{¯}{1} & 1 & \\underset{¯}{1} \\\\ \\end{bmatrix}$$  
graphic style="width:10.75em;" xlink:href="bk978-0-7503-6244-3ch2ueqn45.gif" position="float"/

  
$$K = \\begin{bmatrix} \\begin{bmatrix} 0 & 0 & 0 \\\\ 1 & 1 & 1 \\\\ 0 & 0 & 0 \\\\ \\end{bmatrix}\_{K\_{0}} & \\begin{bmatrix} 0 & 1 & 0 \\\\ 0 & 1 & 0 \\\\ 0 & 1 & 0 \\\\ \\end{bmatrix}\_{K\_{1}} & \\begin{bmatrix} 1 & 0 & 1 \\\\ 0 & 1 & 0 \\\\ 1 & 0 & 1 \\\\ \\end{bmatrix}\_{K\_{2}} \\\\ \\end{bmatrix}^{T}$$  
graphic style="width:19.375em;" xlink:href="bk978-0-7503-6244-3ch2ueqn46.gif" position="float"/

  
$$Y = \\begin{bmatrix} \\begin{bmatrix} 0 & 0 & 0 & 1 & 1 & 1 \\\\ 2 & 3 & 2 & 2 & 1 & 1 \\\\ 0 & 0 & 0 & 1 & 1 & 1 \\\\ 1 & 2 & 2 & 3 & 3 & 2 \\\\ 1 & 1 & 2 & 2 & 3 & 2 \\\\ 1 & 2 & 2 & 3 & 3 & 2 \\\\ \\end{bmatrix}\_{C\_{0}} & \\begin{bmatrix} 1 & 1 & 1 & 0 & 2 & 0 \\\\ 1 & 1 & 1 & 0 & 3 & 0 \\\\ 2 & 1 & 2 & 1 & 3 & 1 \\\\ 1 & 1 & 1 & 2 & 3 & 2 \\\\ 2 & 1 & 2 & 3 & 3 & 3 \\\\ 1 & 1 & 1 & 2 & 2 & 2 \\\\ \\end{bmatrix}\_{C\_{1}} & \\begin{bmatrix} 1 & 2 & 1 & 2 & 1 & 1 \\\\ 1 & 1 & 1 & 2 & 1 & 2 \\\\ 1 & 4 & 2 & 4 & 3 & 2 \\\\ 2 & 0 & 3 & 3 & 3 & 3 \\\\ 0 & 5 & 0 & 5 & 5 & 3 \\\\ 2 & 0 & 3 & 2 & 3 & 0 \\\\ \\end{bmatrix}\_{C\_{2}} \\\\ \\end{bmatrix}^{T}$$  
graphic style="width:30.1875em;" xlink:href="bk978-0-7503-6244-3ch2ueqn47.gif" position="float"/

  
$${Maxpool}2D\\left( {Y,2} \\right) = \\begin{bmatrix} \\begin{bmatrix} 3 & 2 & 1 \\\\ 2 & 3 & 3 \\\\ 2 & 3 & 3 \\\\ \\end{bmatrix}\_{M\_{0}} & \\begin{bmatrix} 1 & 1 & 3 \\\\ 2 & 2 & 3 \\\\ 2 & 3 & 3 \\\\ \\end{bmatrix}\_{M\_{1}} & \\begin{bmatrix} 2 & 2 & 2 \\\\ 4 & 4 & 3 \\\\ 5 & 5 & 5 \\\\ \\end{bmatrix}\_{M\_{2}} \\\\ \\end{bmatrix}^{T}$$  
graphic style="width:26.875em;" xlink:href="bk978-0-7503-6244-3ch2ueqn48.gif" position="float"/

 

After running the codes in Extra Cell THREE, you will see the above results. Since the padding is set to be one, the sizes of the three channels of the convolution's output are the same as the sizes of tensor *X*. A sub-tensor *C*[1] is the convolution result of *X* with *K*[1]. The maximum value of elements in *C*[1] is 3.0. From the locations of the maximum value in *C*[1], you can find the locations of the vertical line ‘∣’ pattern in the tensor *X*. The local pattern information is then concentrated by a PyTorch function ‘max\_pool2d()’ with a stride option of size 2. A PyTorch class named ‘nn.MaxPool2d(2)’ is used in the ResNet6 model in Cell 05-2 in the last section. The sub-tensor M[1] of the output of the ‘max\_pool2d’ function came from *C*[1]. In machine learning, we do not need to find or search for patterns. By using the gradient decedent algorithm to loss functions, we can train our models to find local patterns automatically in images, and these patterns are recorded in filters of kernels of each CNN layer. The ResNet6 model defined in Cell 05-2 has five CCN layers and one fully connected layer or a dense layer. The PyTorch class *nn.BatchNorm2d()* in the function named ‘basic’ of the model normalizes its input of a 4D tensor. The basic function of ResNet6 has one CNN layer. A class in the model named ‘Rs\_Block()’ has two CNN layers.

### 2.3 Using ResNet9 for CIFAR-10 classification

In any computer vision project with CNN models, information flows through CNN layers sequentially in one direction. These types of models are ‘plain’ models. It is a common sense that the more layers a model has, the smarter the model will be. What is the limit of the maximum layers of a CNN model: 10, 100 or even more than 1000 layers? In 2015, Kaiming He and his three colleagues published a paper (He *et al* [2016](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2bib2)) titled ‘Deep residual learning for image recognition’. They found that a ‘plain’ model with 20 layers was more accurate than another ‘plain’ model with 56 layers. They found that this strange issue was caused by a mathematical issue called ‘gradient vanishing’, and they solved the problem by using residual neural networks (**ResNet**). With their solution, a ResNet model could have more than a thousand CNN layers.

The input of a computer vision project about image classification is a batch of images: a 4D tensor *X*. If a plain model has three layers, each layer works like a mathematical function. Using a ‘forward propagation’ algorithm, the output of the model is: *ŷ* = *f*[3](*f*[2](*f*[1](*X*)))inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch2ieqn49.gif"/. Values of a loss function are also obtained from another function *L* = *g*(*X*,*f*[1],*f*[2],*f*[3])inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch2ieqn50.gif"/. Using the gradient descent algorithm to optimize the model, we calculate the gradients of the loss function to the input tensor *X* with a ‘backward propagation’ algorithm: $\\nabla\_{X}L = \\frac{\\partial L}{\\partial f\_{3}}\\frac{\\partial f\_{3}}{\\partial f\_{2}}\\frac{\\partial f\_{2}}{\\partial f\_{1}}\\frac{\\partial f\_{1}}{\\partial X}$inline-graphic style="height:2.125em;" xlink:href="bk978-0-7503-6244-3ch2ieqn51.gif"/. In machine learning, we frequently handle float32 tensors. In cases where the values of all the partial gradients in ∇[*X*]*L*inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch2ieqn52.gif"/ are less than one, and the layers of the plain model are 100 or even 1000, the gradient of *L* to *X* will be very close to zero. This is the ‘gradient vanishing’ issue. In this case, the model parameters cannot be updated, and model training results will not be improved.

To avoid the ‘gradient vanishing’ issue, Kaiming He and his colleagues let information flow through model layers with branches. In the ResNet6 model of section [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-1), the third and fourth layers came from a class *Rs\_Block* which has two branches to process input information. One branch bypasses layer 03 and layer 04, another branch was processed by the two layers. Since the shapes of the tensors of the two branches are the same, they could be added together directly for the output of the *Rs\_Block*. From those examples of convolution operations in the last section, we saw that the element values of convolution outputs were bigger because of multiplication and sum operations in convolutions. The output of the second branch was reduced by half, and the reduced output was added to the first branch's output for the output of the *Rs\_Block* class.

In more complex ResNet models, we have to use *nn.Conv2d()* with kernels of filter size one and other PyTorch classes to modify data channels and resolutions in the two branches. Before jumping deeper in ResNet networks, let us to use the above knowledge to classify images in CIFAR-10 dataset (Krizhevsky and Hinton [2009](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2bib3)). This database was created by a Toronto research organization: Canadian Institute for Advanced Research. The CIFAR-10 database has 60 000 color images in 10 different classes. The resolution of these images is 32 × 32. The codes in Cell 01 are used to import Python and PyTorch libraries for the CIFAR-10 image classification project. Hyperparameters are also set in the cell. With codes in Cell 02, we input the CIFAR-10 database for two datasets. By using four image transformation operations, the difference between image classification accuracies about the train and validation datasets are small. Otherwise, the classification accuracy for the train dataset quickly increases to almost 100%, but the one for the validation datasets is much lower. These augmentations can significantly reduce the overfitting issue.

In Cell 02, a dataset with 50 000 images was randomly split into a train dataset and a validation dataset, and they have 40 000 and 10 000 images, respectively. These two datasets are used for model training and validation. The test dataset will be used at the end to evaluate the trained model. With codes in Cell 03, the three datasets are sliced into three dataloaders. Running codes in Cell 04, we can see 100 images in a batch of the train dataloader, but only the first 40 images are displayed in figure [2.4](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig4) to save page.

![](images/bk978-0-7503-6244-3ch2uf13_pr.gif)

![](images/bk978-0-7503-6244-3ch2uf14_pr.gif)

![](images/bk978-0-7503-6244-3ch2uf15_pr.gif)

![](images/bk978-0-7503-6244-3ch2uf16_pr.gif)

![Figure 2.4. CIFA-10 images (outputs of Cell 04). Reproduced with permission from Krizhevsky and Hinton (2009) courtesy of Alex Krizhevsky.](images/bk978-0-7503-6244-3ch2f4_online.jpg)

**Figure 2.4.** CIFA-10 images (outputs of Cell 04). Reproduced with permission from Krizhevsky and Hinton ([2009](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2bib3)) courtesy of Alex Krizhevsky.

![Figure 2.5. CIFAR-10 image classification results. (A) Accuracy curves. (B) Loss curves. (C) Learning rate curve. Model training time is 23 min.](images/bk978-0-7503-6244-3ch2f5_online.jpg)

**Figure 2.5.** CIFAR-10 image classification results. (A) Accuracy curves. (B) Loss curves. (C) Learning rate curve. Model training time is 23 min.

The structure of the model ResNet9 and the model NesRet6 are almost the same. The only difference is that ResNet9 has three more neural layers. There are two ResNet blocks in the ResNet9 model. From figure [2.5](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig5), outputs of Cell 08 and Cell 09, you can find that the image classification accuracies for the train dataset and the valuation dataset are over 99% and 92%, respectively. After running the code *evaluation(test\_dl)* on the second line of Cell 10, we will get the accuracy for the test dataset that is also over 92%.

### 2.4 Transfer learning with ResNet for a dataset of Vegetable Images

Inventing a CNN model to solve problems in a computer vision project is not an easy job. The architecture of the ResNet9 model came from [Jovian](https://jovian.ai/ffreller/fruits-resnet9/v/2). It is the simplest and the most efficient model for image datasets with lower resolutions. For datasets with high resolution images, we have to use more powerful models. Fortunately, there are many very smart models which had been trained with millions of images. We do not need to reinvent ‘wheels’. Transfer learning is about using pre-trained models to new datasets for image classifications or other computer vision projects. By running codes *import torchvision; import torchvision.models; dir(models)* in an extra cell before Cell 06 in Project [2.4](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn58), you will see more than a hundred pre-trained models, such as resnet18, resnet34, resnet50, resnet101, resnet152 and vgg16, etc. These pre-trained models were designed for bigger images (224×224). We will modify and use resnet18, resnet50 and resnet152 in the project for a dataset of [Vegetable Images](https://www.kaggle.com/datasets/misrakahmed/vegetable-image-dataset) classification. Using CC BY-SA 4.0 license, [Shahriyar Mahmud Mamun](https://www.facebook.com/shahriyar.m.mamun/) (the author of the dataset) in Bangladesh kindly gives people freedom to share and adapt the dataset.

The project for Vegetable Images classification has three parts. Cell 01 to 04 combined together is the first part. It imports datasets, slices datasets into dataloaders and displays a batch of images and their labels. The size of a zip file downloaded from [Kaggle](https://www.kaggle.com/datasets/misrakahmed/vegetable-image-dataset) is around 560 MB. After unzipping the file in my computer to a folder named ‘VegetableImgs’, I got three sub-folders named ‘train’, ‘test’ and ‘validation’. Under each of these sub-folders, there are 15 sub-folders. The name of each of the second level sub-folders is the name of a kind of vegetable. Using a torchvision datasets tool, *ImageFolder*, to pack these images into three datasets, I obtained the names of 15 classes in these datasets. By running *train\_dataset.classes* in an extra cell after the Cell 04, you will see a list of names of the 15 classes: Bean, Bitter\_Gourd, Bottle\_Gourd, Brinjal, Broccoli, Cabbage, Capsicum, Carrot, Cauliflower, Cucumber, Papaya, Potato, Pumpkin, Radish and Tomato. The sizes of images in the datasets are not the same. Image resolutions of most images are 224×224. We have to resize all images to the same resolution for datasets. To save the model training time, we can resize images from 224×224 to 128×128.

The three datasets were then sliced into three dataloaders, respectively, in Cell 03 with a batch size of 64. A quarter of images in the first batch of the train dataloader are displayed in figure [2.6](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig6). Some of the images are upside down in the figure. That is the effect of the *RandomVerticalFlip* in the image transform operations. Cell 05 is the second part, in which there is a pre-trained model, a criterion, an optimizer and a learning rate scheduler. The last part of the project (Cell 06 to Cell 09) is used to train the model and display training results.

![](images/bk978-0-7503-6244-3ch2uf17_pr.gif)

![](images/bk978-0-7503-6244-3ch2uf18_pr.gif)

![Figure 2.6. Sixteen vegetable images in a batch of the train\_dataloader (the output of Cell 04). Reproduced from Shahriyar Mahmud Mamun’s Vegetable Images Dataset, CC BY-SA 4.0 license,](images/bk978-0-7503-6244-3ch2f6_online.jpg)

**Figure 2.6.** Sixteen vegetable images in a batch of the train\_dataloader (the output of Cell 04). Reproduced from [Shahriyar Mahmud Mamun](https://www.facebook.com/shahriyar.m.mamun/)’s Vegetable Images Dataset, CC BY-SA 4.0 license,

By default, all these pre-trained models from torchvision are used for image datasets with 1000 classes. If you use *print(model)* on the second line of Cell 05, you will find that the last layer of the resnet18 model is a fully connected layer: *nn.Linear(1024,1000, bias=False)*. It was used for [ImageNet](https://www.image-net.org/) dataset with 1000 classes, so we have to change the parameters of the last layer for the vegetable image dataset with only 15 classes. The codes on line 06-07 of Cell 05 do the work. Then running the code *print(model)* in an extra cell after Cell 05, you will find the last fully connected layer is changed to *nn.Linear(1024, 15, bias=False)*. We can also import optimized parameters with an option *pretrained=True* on line 01 of Cell 05 for the pre-trained model. I tried with another option ‘False’, and found the classification accuracies were lower. If you remove hashtag # symbols in front of lines 04 and 05, the codes on the two lines will freeze all parameters coming with the trained model. Since the last fully connected layer is modified, only the parameters in the last layer will be updated during model training. In this case, the classification accuracies were not good enough. With codes in Cell 05 to update all parameters in the pre-trained resnet18 model, the classification accuracies were around 98% for the test dataloader (figure [2.7](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig7)). With resnet50 and resnet101, the accuracies would be improved a little more, but the training time would be doubled and tripled, respectively. Codes in Cell 10 can be used to classify a single image with an index in the test dataset. It prints out that image for you to verify the classification.

![](images/bk978-0-7503-6244-3ch2uf19a_pr.gif)

![](images/bk978-0-7503-6244-3ch2uf19b_pr.gif)

![Figure 2.7. Vegetable image classification results by ResNet18. (Left) accuracy curves (train dataset: 99.4%, validation dataset: 97.6%, test dataset: 97.9%). (Middle) loss curves. (Right) the learning rate curve. Model training time is 7 min.](images/bk978-0-7503-6244-3ch2f7_online.jpg)

**Figure 2.7.** Vegetable image classification results by ResNet18. (Left) accuracy curves (train dataset: 99.4%, validation dataset: 97.6%, test dataset: 97.9%). (Middle) loss curves. (Right) the learning rate curve. Model training time is 7 min.

What codes are inside those pre-trained ResNet models? From the flowing ResNet18 model, you would know other models with more than 100 layers, but it is not necessary. The function named ‘basic’ has two convolution layers. The input of the function is a 4D tensor, and the output of the function is also a 4D tensor, but its channels and resolution could be different from the input. A class titled ‘Id\_Block’ has two branches. Its basic branch's input and output have the same shape; another branch's output is the input tensor itself. The outputs from the two branches directly add together as the output of the class. A class named ‘Rs\_Block’ also has two branches. Comparing it with the shape of its input tensor, the output from the basic branch (stride = 2) has different channels and resolutions. A branch named ‘shortcut’ with a convolution of kernel size one is used to modify its input tensor, so the second branch's output shape can match with the output shape of the basic branch. These blocks are used to build the ResNet18 model.

![](images/bk978-0-7503-6244-3ch2uf20_pr.gif)

 

There are 17 convolution layers and a fully connected layer in the ResNet18 model. That is why it has the name ‘ResNet18’. Running *p\_list = \[p.numel*() *for p in model.parameters*()*\]; print(sum(p\_list),' = ', p\_list)*, you will find the total parameter number (11 181 642) in the resnet18, and also the numbers of parameters in each layer. Then changing to another pre-trained model and checking those parameter numbers, you will find that the parameter number in the resnet50 model is 23 528 522. We can print out all parameter names and their shapes by running the following short codes. From the first line of the outputs of the Extra Cell 01, we get a parameter named ‘conv1.weight’ and its shape: torch.size(\[64, 3, 7, 7\]). It is the weight tensor of the convolution operation in the first convolution layer of the ResNet18 model.

![](images/bk978-0-7503-6244-3ch2uf21_pr.gif)

 

The weight tensor of the convolution could be treated as a batch of images with 64 samples, three channels and a resolution of 7 × 7. We can display this batch of images with codes in the following Extra Cell 02. Each element's value of the weight tensor is sifted to \[0, 1\]. The left image in figure [2.8](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig8) came from the pre-trained ResNet18 model with optimized parameters; the right one also came from the same model but with randomly initialized parameters. In section [2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-2) we generated patterns with matrices for convolutions. Now we see real convolution patterns. A ResNet model with deeper layers would pick out more detail pattern information about images.

![](images/bk978-0-7503-6244-3ch2uf22_pr.gif)

![Figure 2.8. Images of the convolution kernel weights in layer 1 of resnet18. (Left): Pre-trained ResNet50 model with optimized parameters. (Right): Pre-trained model with randomly initialized parameters](images/bk978-0-7503-6244-3ch2f8_online.jpg)

**Figure 2.8.** Images of the convolution kernel weights in layer 1 of resnet18. (Left): Pre-trained ResNet50 model with optimized parameters. (Right): Pre-trained model with randomly initialized parameters

### References

Coates A, Ng A and Lee H 2011 An analysis of single-layer networks in unsupervised feature learning *J. Mach. Learn. Res.—Proc. Track* **15** 215–23

He K, Zhang X, Ren S and Sun J 2016 Deep residual learning for image recognition *Proc. of the IEEE Conf. on Computer Vision and Pattern Recognition* 770–8

Krizhevsky A and Hinton G 2009 Learning multiple layers of features from tiny images. Technical Report TR-2009, University of Toronto [https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf](https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf)

Lecun Y, Cortes C and Burges C J C 1998 The MNIST database of handwritten digits.

Deng L 2012 The MNIST database of handwritten digit images for machine learning research *IEEE Signal Process. Mag.* **29** 141–2

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 3

## Image generation by GANs

This chapter is about using generative adversarial networks (GANs) and conditional GANs to generate fake images similar to images in the six datasets: MNIST, Fashion MNIST, Anime Face, CelebA and Rock Paper Scissors. A simple quadratic curve dataset is used to make it is easy to understand the mathematical principle of GANs.

Image generation is more difficult than image classification. This is true both for human beings and for computers. After Ian Goodfellow and his colleagues published a paper (Goodfellow *et al* [2014](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib2)) titled ‘Generative adversarial nets’ in 2014, many algorithms were developed based on GANs. Today, computers can be trained to create photo-realistic images of human faces. Just by searching ‘this person does not exist’, you will find a website where you can see astonishing fake photos of human faces. A GAN has two neural networks or models: a generator and a discriminator. The generator creates fake data samples from pure noises. The discriminator uses fake samples and real samples as its inputs, and evaluates them to find the fake. During model training, the two networks compete with each other. The generator tries to produce data (images) to fool the discriminator and the discriminator manages to correctly identify the generated data. The training process continues until the generator creates data that is so realistic that the discriminator can't distinguish it from real data. At the end of model training, the GAN can find a PDF of image pixels in the dataset. Using parameters of the PDF, computers can generate fake images which are similar to real images.

### 3.1 The GAN theory

One GAN model is used as a generator (G) which is trained to generate fake images from 1D noisy vectors. The number of elements in a noisy vector could be 1, 2, or even more than 100. Those vectors came from a standard normal distribution function (section [1.1.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1s1-1-1)). Model G has many parameters (*θ*[*g*]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch3ieqn1.gif"/) to be trained. Another model is used as a discriminator (*D*) which is trained to distinguish fake images from real images in a dataset. It also has many parameters (*θ*[*d*]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch3ieqn2.gif"/) to be trained. Model G is just like an art student who is taught to paint by his teacher Leonardo da Vinci, the model D. After watching his teacher's many masterpieces, the student paints his first picture. The teacher tells his student what he has painted incorrectly, and how to improve his skill. The student then paints a second picture. The teacher checks the picture again and gives the student more advice; the process is repeated many times. Finally, the student is able to paint another Mona Lisa and nobody can say that it is a fake. This is an ideal result. However, what happens if the student is not smart enough to understand his master's ideas and suggestions, or if the teacher is not Leonardo da Vinci, but an ordinary man? The training will be a failure in both cases.

GAN model training is still a challenge. One big issue of GAN's model training is ‘mode collapse’. For example, you took 120 min to train your models to generate MNIST images for ten digits, but the outputs only had one digit. There are many parameters in the two models, and there are also many hyperparameters in your codes. How can you adjust them to get what you want in a short time? Before we face those model training challenges, we need to build our training machine for GANs. There are four parts to the machine. The first part is for data input, the second part is for constructions of the two models, the third part is for model training, and the fourth part is for data visualization. Only the second part is new for us. Model D and model G are trained in a for-loop for each batch of real images in a dataloader with a batch size *m*:

1.  From the dataloader, take a batch of image samples: {*x*[*1*], *x*[*2*]*…, x*[*m*]}.
2.  Using model D to convert *x*[*i*] into a scalar *ŷ*[*i*]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch3ieqn3.gif"/ = *D*(*x*[*i*])∈ \[0,1\], (*i* = 1, 2…, *m*).
3.  Set any real image's target as ONE: *y*[*i*] = 1, (*i* = 1, 2, …, *m*).
4.  Calculate BCE loss between the targets and the predictions by $\\frac{- 1}{m}\\sum\\limits\_{i = 1}^{m}{\\ \\ln\\ \\left( {D\\left( x\_{i} \\right)} \\right)}$inline-graphic style="height:3.0625em;" xlink:href="bk978-0-7503-6244-3ch3ieqn4.gif"/.
5.  Generate a batch of noise vectors from a standard normal distribution: {*z*[*1*], *z*[*2*]*…, z*[*m*]}.
6.  Create a batch of fake images from the noise vectors: *x̃*[*i*]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch3ieqn5.gif"/ = *G*(*z*[*i*]), (*i* = 1, 2…, *m*).
7.  Convert any fake image into a scalar *D*(*x̃*[*i*])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch3ieqn6.gif"/∈ \[0,1\] as a fake prediction.
8.  Set each fake image's target as ZERO.
9.  Calculate BCE loss by $\\frac{- 1}{m}\\sum\\limits\_{i = 1}^{m}{\\ \\ln\\ \\left( {1 - D\\left( {\\widetilde{x}}\_{i} \\right)} \\right)}$inline-graphic style="height:3.0625em;" xlink:href="bk978-0-7503-6244-3ch3ieqn7.gif"/ without updating model G.
10.  Calculate model D's loss:
     
       
     $$L\_{D}\\left( \\theta\_{d} \\right) = \\frac{- 1}{m}\\sum\\limits\_{i = 1}^{m}{\\ \\ln\\ \\left( {D\\left( x\_{i} \\right)} \\right) -}\\frac{1}{m}\\sum\\limits\_{i = 1}^{m}\\left( {1 - \\ln\\ \\left( {D\\left( {\\widetilde{x}}\_{i} \\right)} \\right)} \\right)$$  
     (3.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch3eqn8.gif" position="float"/
     
       
     *L*[*D*](*θ*[*d*]) =  − *E*\[ln(*D*(*X*))\] − *E*\[ln(1−*D*(*G*(*Z*)))\]  
     graphic style="width:19.6875em;" xlink:href="bk978-0-7503-6244-3ch3ueqn9.gif" position="float"/
     
       
     →−∫*p*[*r*](*x*)ln⁡\[*D*(*x*)\]*d**x*−∫*p*[*z*](*z*)ln⁡\[1−*D*(*G*(*z*))\]*d**z*  
     graphic style="width:21.1875em;" xlink:href="bk978-0-7503-6244-3ch3ueqn10.gif" position="float"/
     
       
     →−∫*p*[*r*](*x*)ln⁡\[*D*(*x*)\]*d**x*−∫*p*[*g*](*x*)ln⁡\[1−*D*(*x*)\]*d**x*  
     graphic style="width:20.0625em;" xlink:href="bk978-0-7503-6244-3ch3ueqn11.gif" position="float"/
     
       
      =  − ∫(*p*[*r*](*x*) ln\[*D*(*x*)\]+*p*[*g*](*x*) ln\[1−*D*(*x*)\])*d**x*  
     graphic style="width:18.75em;" xlink:href="bk978-0-7503-6244-3ch3ueqn12.gif" position="float"/
     
     This is the training criterion for the discriminator *D* with a given generator G. In the condition of *G* is given, it is possible to find an optimized discriminator *D*\* to minimize the loss function by $\\frac{d}{\\mathit{dD}\\left( x \\right)}\\left( {p\_{r}\\left( x \\right)\\ \\ln\\ \\left\\lbrack {D\\left( x \\right)} \\right\\rbrack + p\_{g}\\left( x \\right)\\ \\ln\\ \\left\\lbrack {1 - D\\left( x \\right)} \\right\\rbrack} \\right) = 0$inline-graphic style="height:1.9375em;" xlink:href="bk978-0-7503-6244-3ch3ieqn13.gif"/ at a fixed *x*. The optimized discriminator *D*^(\*) is found to be: $D\_{G}^{\*}\\left( x \\right) = \\frac{p\_{r}\\left( x \\right)}{p\_{r}\\left( x \\right) + p\_{g}\\left( x \\right)}$inline-graphic style="height:2.25em;" xlink:href="bk978-0-7503-6244-3ch3ieqn14.gif"/, where we have:
     
       
     *L*[*D*](*θ*[*d*]) = 2ln ⁡(2) − 2*D*[*J**S*](*p*[*r*] ∣ ∣*p*[*g*])  
     graphic style="width:12.625em;" xlink:href="bk978-0-7503-6244-3ch3ueqn15.gif" position="float"/
     
     Based on equation ([1.8](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn8)): 0 ≤ *D*[*J**S*](*p*[*r*] ∣ *p*[*g*] ≤ ln  (2))inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch3ieqn16.gif"/, we have 0 ≤ *L*[*D*](*θ*[*d*]) ≤ 2 ln  (2)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch3ieqn17.gif"/. In case *p*[*r*] = *p*[*g*]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch3ieqn18.gif"/, model D's loss achieves a maximum: 2 ln  (2)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch3ieqn19.gif"/.
     

1.  Update D's parameters *θ*[*d*]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch3ieqn20.gif"/ without changing *θ*[*g*]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch3ieqn21.gif"/: *θ*[*d*]←*θ*[*d*]−*η*∇[*θ*[*d*]]*L*[*D*](*θ*[*d*])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch3ieqn22.gif"/.
2.  Then with a new batch of noises from a normal distribution: {*z*[*1*], *z*[*2*]*…, z*[*m*]}.
3.  Create a new batch of fake images from the noises: *x̃*[*i*]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch3ieqn23.gif"/ = *G*(*z*[*i*]).
4.  Convert each *x̃*[*i*]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch3ieqn24.gif"/ into a scalar *D*(*x̃*[*i*])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch3ieqn25.gif"/∈ \[0,1\] as a real prediction.
5.  Set each fake image's target as ONE.
6.  Calculate BCE loss:
    
      
    $$L\_{G}\\left( \\theta\_{g} \\right) = \\frac{- 1}{m}\\sum\\limits\_{i = 1}^{m}{\\ \\ln\\ \\left( {D\\left( {\\widetilde{x}}\_{i} \\right)} \\right)}$$  
    (3.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch3eqn26.gif" position="float"/
    
7.  Update G's parameters with *θ*[*g*]←*θ*[*g*]−*η*∇[*θ*[*g*]]*L*[*G*](*θ*[*g*])inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch3ieqn27.gif"/.

#### 3.1.1 Implement a GAN for quadratic curve generation

It is better to implement GAN theory to a simple dataset in the beginning. In the following project [3.1.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3ueqn7), only two fully connected layers are used in the generator model (G) and the discriminator model (D) shown in figure [3.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig1)(A). These models handle data in three spaces. The first space is the observed space or real space with 21 dimensions for real quadratic curves. The data of each real curve in a batch of a dataloader come from a quadratic function *y = ax*^(*2*) *\+ b*, where *x* is a 1D array generated by a NumPy function: *np.linspace(−1, 1, 21)*. The factor ‘*a*’ in the function is also a 1D array generated by a uniform distribution function: *np.random.uniform(1, 2, size = 64)* and is reshaped into a 64 × 1 NumPy array. Another constant *b* in the function is set to be equal to (*a* −1). A batch in a dataloader generated by a function *training\_data()* defined in Cell 02 is a 64 × 21 array. The output of Cell 03 is a graph with 64 real quadratic curves. When printing out data of the last curve *y*\[63\] in an extra cell after Cell 01, we would see a 1D NumPy array with 21 floating numbers.

![Figure 3.1. (A) The information flow chart for the two models of a GAN. The real curves are outputs of Cell 03. (B) Fake curves at epoch = 20 000, the outputs of Cell 10. Model training time is 11 min.](images/bk978-0-7503-6244-3ch3f1_online.jpg)

**Figure 3.1.** (A) The information flow chart for the two models of a GAN. The real curves are outputs of Cell 03. (B) Fake curves at epoch = 20 000, the outputs of Cell 10. Model training time is 11 min.

The second space is a latent space with two dimensions (z\_dim = 2). Each batch of noise vectors in the latent space is generated by a standard normal distribution function *N*(0,I) as shown in figure [3.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig1)(A). In Cell 01, the shape of a batch of noise vectors named ‘latent\_noise’ is 64 × 2. The third space is a 1D space named ‘critical space’ created by the discriminator model D with elements of the batch size. Because the last activate function of model D is a Sigmoid activation function, the value of each element of the critical space is in the range \[0,1\]. Using a batch of curves (real or fake) as input, model D outputs a batch of scalars. In an extra cell after Cell 09 running the code *D(torch.cuda.FloatTensor(y)).T*, you will get a batch of scalars: tensor (\[\[0.5777, 0.5896, 0.5465, 0.5909, 0.5825, 0.5710, 0.5672, 0.5742, 0.5858, 0.5727, 0.5582, 0.5435, 0.5661, 0.5390, 0.5611, 0.5673, 0.5926, 0.5957, 0.5521, 0.5668, 0.5571, 0.5948, 0.5742, 0.5589, 0.5634, 0.5714, 0.5482, 0.5927, 0.5947, 0.5880, 0.5490, 0.5582, 0.5575, 0.5450, 0.5552, 0.5678, 0.5504, 0.5413, 0.5415, 0.5648, 0.5715, 0.5896, 0.5489, 0.5505, 0.5711, 0.5963, 0.5747, 0.5426, 0.5622, 0.5399, 0.5580, 0.5820, 0.5600, 0.5616, 0.5605, 0.5636, 0.5526, 0.5724, 0.5752, 0.5728, 0.5491, 0.5960, 0.5571, 0.5436\]\], device = 'cuda:0', grad\_fn = <PermuteBackward0>). Each scalar came from a real image.

Running code *D(G(latent noise)).T* after Cell 09, you will get another batch of scalar: tensor(\[\[0.5378, 0.5387, 0.5648, 0.5501, 0.5448, 0.5204, 0.5447, 0.5554, 0.5333, 0.5341, 0.5489, 0.5313, 0.5729, 0.5398, 0.5922, 0.5367, 0.5377, 0.5413, 0.5610, 0.5572, 0.5356, 0.5419, 0.5526, 0.5290, 0.5886, 0.5620, 0.5499, 0.5300, 0.5167, 0.5296, 0.5286, 0.5235, 0.5418, 0.5266, 0.5280, 0.5531, 0.5223, 0.5587, 0.5294, 0.5362, 0.5281, 0.5256, 0.5597, 0.5408, 0.5471, 0.5292, 0.5576, 0.5494, 0.5363, 0.5348, 0.5214, 0.5245, 0.5607, 0.5234, 0.5366, 0.5475, 0.5375, 0.5464, 0.5228, 0.5498, 0.5216, 0.5309, 0.5654, 0.5702\]\], device = 'cuda:0', grad\_fn = <PermuteBackward0>). Each scalar is for a fake image. Model D will be trained to increase the scalar of each real curve as close as possible to one, and decrease the scalar of each fake curve as close as possible to zero with a BCE loss function (equation ([3.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3eqn1))). While mode D is trained or model D's parameters are updated, model G's parameters are not touched. Then model G is trained with a new batch of noise vectors by another BCE loss function (equation ([3.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3eqn2))) which tries to increase the scalar of each fake curve as close as possible to one. Model D and model G are trained alternately many times until, and the results of the competition between the two models are D(X) = D(G(Z)) = 0.5.

![](images/bk978-0-7503-6244-3ch3uf1_pr.gif)

 

Running codes in Cell 01–03, we would see 64 beautiful quadratic curves (figure [3.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig1)(A)), just like the rings of Saturn through a telescope. The variable ‘z\_dim’ in Cell 01 is the dimension of each 2D noisy vector which goes through two layers of model G to generate 21 points for a fake curve. The input of model D defined in Cell 05 is a batch of 64 curves. Each curve with 21 points is processed by model D to become a positive scalar tensor whose value is in the range \[0,1\]. An activate function LeakyReLU(0.2) is used between those two fully connected layers. This function multiplies a factor 0.2 to each negative number, and keeps each positive number as it is for the outputs of the first layer. Both of these models are sent to GPU by ‘cuda()’.

![](images/bk978-0-7503-6244-3ch3uf2_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf3_pr.gif)

 

Cell 06 is reserved for future use. Since the project has two models, Cell 07 defines two Adam optimizers. The two models use the same criterion function: BCELoss(). A tensor named ‘noise’ in Cell 08 and Cell 09 is used as an input for model G to generate 64 fake curves. The codes for model D training were written following the GAN theory. There are three parts in this cell. The first part is used to calculate the real samples’ BCE loss, the second part is to calculate the fake samples’ BCE loss. The function ‘detach()’ in the calculations for ‘fake\_preds’ is very important. With this, only model D's parameters are updated in the third part of the cell, and model G's parameters are untouched. The outputs of the cell are model D's loss, real\_score (average of D(X)) and fake\_score (average of D(G(Z)). One cycle learning rate scheduler is better than a fixed learning rate scheduler for the project.

Codes in Cell 08–09 were written following the GAN theory. It is necessary to mention that the target to train model G in Cell 09 is a tensor with all elements equal to 1.0. In Cell 10, a pandas dataframe is used to record model training history. During the training for 20 000 epochs, only at the beginning and every 4000 epochs will the training results be shown. These results are 'Loss\_G', 'Loss\_D’, ‘D(X)’ and ‘D(G(Z))’. Fake curves are also shown. Cell 11 is used to display the pandas dataframe in graphs (figure [3.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig2)). The two dash lines in figure [3.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig2)(A) were drawn based on theoretical values of Loss\_D and Loss\_G. Those training loss curves are very close to their theory values respectively. The dashed line in (B) is for the theory value of average D(X) and average D(G(Z)). Training curves overlap with the theoretical line. Only for this simplest project we can train those models for 20 000 epochs in about 11 min.

![Figure 3.2. (A) Curves of two loss functions, the outputs of Cell 11. (B) Averages of D(X) and D(G(Z)). Three straight dashed lines were drawn based on theoretical values: 2ln(2), ln(2) and 0.5.](images/bk978-0-7503-6244-3ch3f2_online.jpg)

**Figure 3.2.** (A) Curves of two loss functions, the outputs of Cell 11. (B) Averages of D(X) and D(G(Z)). Three straight dashed lines were drawn based on theoretical values: 2ln(2), ln(2) and 0.5.

#### 3.1.2 Using a GAN with two fully connected layers to generate MINST Images

A GAN with the two simple models shown in section [3.1.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-1-1) will be used in the following project [3.1.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3ueqn10) to generate fake MNIST images. The two models are not powerful enough to handle data in this project. We cannot generate crystal clear fake images similar to real MNIST images. The easier project is used as a contrast to demonstrate the power of deep convolution GANs in the next section. In Cell 01 of project [3.1.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3ueqn10), tools for the project are imported from Python and PyTorch, also hyperparameters are set. Codes in Cell 02–04 are used to import the MNIST datasets, to slice datasets into dataloaders with a batch size 100, and to pick out and display the first batch images in figure [3.3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig3)(A). The values of image pixels were normalized to \[−1, 1\] in Cell 02. Pixel values of images generated by model G are also in the same range by an activation function Tanh(). Using *imgs.min()* or *imgs.max()* in an extra cell after Cell 04, you can verify these limits of pixel values. Although VS Code can display these kinds of images with a notice of ‘clipping input data to the valid range \[0,1\]’, it is better to shift those pixel values to \[0,1\] by using a function named *denorm()* in Cell 04. Cell 05 is reserved for future usage. In Cell 06 and Cell 07, model D and model G are defined with two fully connected layers. Their structures are almost the same as those in section [3.1.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-1-1). Only the input variable number of model D and output variable number of G were changed.

![](images/bk978-0-7503-6244-3ch3uf4_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf6_pr.gif)

![Figure 3.3. (A) Real MNIST images from the output of Cell 04. (B) Fake MNIST images generated by the simple GAN. Model training time is 11 min. The MNIST image dataset is from Deng (2012) with a license CC BY 3.0.](images/bk978-0-7503-6244-3ch3f3_online.jpg)

**Figure 3.3.** (A) Real MNIST images from the output of Cell 04. (B) Fake MNIST images generated by the simple GAN. Model training time is 11 min. The MNIST image dataset is from Deng ([2012](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib7)) with a license CC BY 3.0.

![](images/bk978-0-7503-6244-3ch3uf7_pr.gif)

 

Using *k* = 1 and a constant lambda function, we use a constant learning rate for both models, and find that model D is smarter than model G. A lambda learning rate scheduler *e*^(−0.046i) is used and is shown in figure [3.4](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig4)(C). With the ratio *k* to be 20, model G's learning rate is a function: G\_lr = *k × lr × e*^(−0.046i). Model training curves of Loss\_D, G\_loss, D(X) and D(G(Z)) are all tuned to their theory values. It is a trick to train the two models with their own learning rate scheduler. Please pay attention to *df.iloc\[i,4\]\*k* on line 18 of in Cell 11.

![Figure 3.4. (A) Loss curves for model D and G. (B) The D(X) curve and the D(G(Z)) curve. (C) A lambda learning rate scheduler with an exponential function for model D. Black dashed lines are drawn based on theory values.](images/bk978-0-7503-6244-3ch3f4_online.jpg)

**Figure 3.4.** (A) Loss curves for model D and G. (B) The D(X) curve and the D(G(Z)) curve. (C) A lambda learning rate scheduler with an exponential function for model D. Black dashed lines are drawn based on theory values.

### 3.2 Applications of deep convolutional GANs

The fake MNIST images shown in figure [3.3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig3)(B) are not crystal clear because model G and model D with only two fully connected layers are not smart enough. We will use a powerful deep convolutional GAN (DCGAN) to repeat the project. In a DCGAN, model D uses convolution neural layers to convert each image into a scalar, and model G uses transposed convolution neural layers to restore each image from a scalar. We need to know the mathematical operations of a transposed convolution.

#### 3.2.1 Mathematical operations of ConvTranspose2D

Using convolution operations, a DCGAN's discriminator model shrinks an image in a batch of a dataloader into a scalar tensor. From equation ([2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn3)), we know that the output size of a 2D convolution is: *m* = (*n* − *f* + 2*p*)/*s* + 1. A DCGAN's generator model uses transposed convolution operations to convert a scalar back to an image. This operation also has many options, such as: input channels, output channels, kernel size, stride, padding, bias, etc. The output size of a transposed convolution operation can be derived from equation ([2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2eqn3)), where *m* is the input tensor size, and *n* is the output tensor size of a transposed convolution operation.

  
*n* = (*m*−1)*s* + *f* − 2*p*  
(3.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch3eqn28.gif" position="float"/

Running codes in the following Extra Cell ONE, you will discover how a ConvTranspose2d class works. Nine integers from 0 to 8 are used to construct a 1 × 1 × 3 × 3 tensor *X* in which *m* = 3. Tensor *X* is an input of an instance of the ConvTranspose2d class. The input's batch size is one, the resolution of the only image in the batch is 3 × 3, and the image channel is one. The integer tensor is then converted into a float32 tensor, because the transposed convolution instance accepts this type of tensor, not an integer tensor. Usually, the weight and bias of the instance named ‘CT’ are randomly initialized by PyTorch. The weight of the operator is then assigned with a 1 × 1 × 3 × 3 ONES tensor by using *nn.Parameter()*, and the bias of the instance is assigned with a scalar ZERO tensor.

![](images/bk978-0-7503-6244-3ch3uf8_pr.gif)

  
$$X\_{00} = \\begin{bmatrix} 0 & 1 & 2 \\\\ 3 & 4 & 5 \\\\ 6 & 7 & 8 \\\\ \\end{bmatrix},\\ K\_{00} = \\begin{bmatrix} 1 & 1 & 1 \\\\ 1 & 1 & 1 \\\\ 1 & 1 & 1 \\\\ \\end{bmatrix},{ Y}\_{00}\\left( {s = 1} \\right) = \\begin{bmatrix} 0 & 1 & 3 & 3 & 2 \\\\ 3 & 8 & 15 & 12 & 7 \\\\ 9 & 21 & 36 & 27 & 15 \\\\ 9 & 20 & 33 & 24 & 13 \\\\ 6 & 13 & 21 & 15 & 8 \\\\ \\end{bmatrix}$$  
graphic style="width:29.8125em;" xlink:href="bk978-0-7503-6244-3ch3ueqn29.gif" position="float"/

  
$$Y\_{00}\\left( {s = 3} \\right) = \\begin{bmatrix} 0 & 0 & 0 & 1 & 1 & 1 & 2 & 2 & 2 \\\\ 0 & 0 & 0 & 1 & 1 & 1 & 2 & 2 & 2 \\\\ 0 & 0 & 0 & 1 & 1 & 1 & 2 & 2 & 2 \\\\ 3 & 3 & 3 & 4 & 4 & 4 & 5 & 5 & 5 \\\\ 3 & 3 & 3 & 4 & 4 & 4 & 5 & 5 & 5 \\\\ 3 & 3 & 3 & 4 & 4 & 4 & 5 & 5 & 5 \\\\ 6 & 6 & 6 & 7 & 7 & 7 & 8 & 8 & 8 \\\\ 6 & 6 & 6 & 7 & 7 & 7 & 8 & 8 & 8 \\\\ 6 & 6 & 6 & 7 & 7 & 7 & 8 & 8 & 8 \\\\ \\end{bmatrix},Y\_{00}\\left( {s = 2} \\right) = \\begin{bmatrix} 0 & 0 & 1 & 1 & 3 & 2 & 2 \\\\ 0 & 0 & 1 & 1 & 3 & 2 & 2 \\\\ 3 & 3 & 8 & 5 & 12 & 7 & 7 \\\\ 3 & 3 & 7 & 4 & 9 & 5 & 5 \\\\ 9 & 9 & 20 & 11 & 24 & 13 & 13 \\\\ 6 & 6 & 13 & 7 & 15 & 8 & 8 \\\\ 6 & 6 & 13 & 7 & 15 & 8 & 8 \\\\ \\end{bmatrix}$$  
graphic style="width:34.4375em;" xlink:href="bk978-0-7503-6244-3ch3ueqn30.gif" position="float"/

 

Taking *m* = 3, *f* = 3, *s* = 3 and *p* = 0 to equation ([3.3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3eqn3)), we get *n* = 9. It is true that the shape of the output *Y*(*s* = 3) of the above codes in Extra Cell ONE is 1 × 1 × 9 × 9. Each element of tensor *X* is converted into a 3 × 3 subunit in the output *Y*, and each subunit is equal to the *X*'s element times the kernel tensor *K*. With *p* = 1 or 2 in the above codes, the output is obtained by peeling off one or two outside layers from the *Y*(*s* = 3) tensor. In the following discussion, the padding parameter *p* is set to be equal to ZERO. It is a little difficult to understand those operations for stride settings (*s* = 2 and *s* = 1). We know that dimensional indices of a tensor in PyTorch starts from ZERO. To get the output tensor *Y*(*s* = 2), we combine rows 2 and 3, rows 5 and 6 in *Y*(*s* = 3) at first by a summation of two elements at the same column index, and then combine columns 2 and 3, columns 5 and 6 by adding operations to each pair of elements at the same row index. Since two rows and two columns are lost during these operations, the shape of the Y(*s* = 2) tensor is 1 × 1 × 7 × 7. The red and blue colors in the *Y*(*s* = 3) tensor are used to show elements on rows 2 and 3 and rows 5 and 6. To get *Y*(*s* = 1) from *Y*(*s* = 3), we combine rows 1 and 3, rows 2 and 4 at first to obtain a middle tensor with the shape 1 × 1 × 7 × 9. Then in the middle tensor, we combine rows 2 and 4, rows 3 and 5. Finally, we do the same combination operations for the columns. These operations are not easy to handle manually; fortunately, PyTorch takes cares of them.

Codes in Extra Cell TWO are for applications of a 2D transposed convolution operator in the second example. The input image's shape is *X*.shape = \[1,2,3,3\], the kernel tensor's shape is *K*.shape = \[2,3,2,2\], and the output tensor's shape of the transposed convolution is *Y*.shape = \[*X*.shape\[0\], *K*.shape\[1\], *n*, *n*\], where *n* is set by equation ([3.3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3eqn3)). Taking *m* = 3, *f* = 2, *s* = 2, *p* = 0 into the CT instance, we get *n* = 6. The *in\_channels* and the *out\_channels* of the CT instance are equal to X.shape\[1\] and K.shape\[1\], respectively. In the example, 18 integers are used to construct an input image tensor X which is then converted into a 1 × 2 × 3 × 3 float32 tensor. The kernel tensor K has two rows and three columns. The shape of each of its six subunits is 2 × 2. The shape of the output tensor is *Y*(*X*,*K*).shape = \[1,3,6,6\]. A sub-tensor in the middle of Y(*X*,*K*) is obtained by using summation results of two ConvTranspose2d operations for (X[0], K[01]) and (X[1], K[11]). For example, the element 17 in the middle sub-tensor of Y was obtained by 17 = 4 × 1 + 13 × 1.

  
$$X = \\begin{bmatrix} \\begin{bmatrix} 0 & 1 & 2 \\\\ 3 & 4 & 5 \\\\ 6 & 7 & 8 \\\\ \\end{bmatrix}\_{X\_{0}} \\\\ \\begin{bmatrix} 9 & 10 & 11 \\\\ 12 & 13 & 14 \\\\ 15 & 16 & 17 \\\\ \\end{bmatrix}\_{X\_{1}} \\\\ \\end{bmatrix}^{T},K = \\begin{bmatrix} \\begin{bmatrix} 0 & 0 \\\\ 0 & 0 \\\\ \\end{bmatrix}\_{K\_{00}} & \\begin{bmatrix} \\underset{¯}{1} & \\underset{¯}{1} \\\\ \\underset{¯}{1} & \\underset{¯}{1} \\\\ \\end{bmatrix}\_{K\_{01}} & \\begin{bmatrix} 2 & 2 \\\\ 2 & 2 \\\\ \\end{bmatrix}\_{K\_{02}} \\\\ \\begin{bmatrix} 1 & 0 \\\\ 0 & 1 \\\\ \\end{bmatrix}\_{K\_{10}} & \\begin{bmatrix} \\underset{¯}{1} & \\underset{¯}{0} \\\\ \\underset{¯}{0} & \\underset{¯}{1} \\\\ \\end{bmatrix}\_{K\_{11}} & \\begin{bmatrix} 1 & 0 \\\\ 0 & 1 \\\\ \\end{bmatrix}\_{K\_{12}} \\\\ \\end{bmatrix}$$  
graphic style="width:26.4375em;" xlink:href="bk978-0-7503-6244-3ch3ueqn31.gif" position="float"/

  
$$Y\\left( {X,K} \\right) = \\begin{bmatrix} \\begin{bmatrix} 9 & 0 & 10 & 0 & 11 & 0 \\\\ 0 & 9 & 0 & 10 & 0 & 11 \\\\ 12 & 0 & 13 & 0 & 14 & 0 \\\\ 0 & 12 & 0 & 13 & 0 & 14 \\\\ 15 & 0 & 16 & 0 & 17 & 0 \\\\ 0 & 15 & 0 & 16 & 0 & 17 \\\\ \\end{bmatrix} & \\begin{bmatrix} 9 & 0 & 11 & 1 & 13 & 2 \\\\ 0 & 9 & 1 & 11 & 2 & 13 \\\\ 15 & 3 & 17 & 4 & 19 & 5 \\\\ 3 & 15 & 4 & 17 & 5 & 19 \\\\ 21 & 6 & 23 & 7 & 25 & 8 \\\\ 6 & 21 & 7 & 23 & 8 & 25 \\\\ \\end{bmatrix} & \\begin{bmatrix} 9 & 0 & 12 & 2 & 15 & 4 \\\\ 0 & 9 & 2 & 12 & 4 & 15 \\\\ 18 & 6 & 21 & 8 & 24 & 10 \\\\ 6 & 18 & 8 & 21 & 10 & 24 \\\\ 27 & 12 & 30 & 14 & 33 & 16 \\\\ 12 & 27 & 14 & 30 & 16 & 33 \\\\ \\end{bmatrix} \\\\ \\end{bmatrix}$$  
graphic style="width:33.1875em;" xlink:href="bk978-0-7503-6244-3ch3ueqn32.gif" position="float"/

![](images/bk978-0-7503-6244-3ch3uf9_pr.gif)

#### 3.2.2 Applications of a DCGAN for MNIST and fashion MNIST

The DCGAN architecture for project [3.2.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3ueqn20) to generate fake MNIST images is based on the paper by Alec Radford and Luke Metz (Radford *et al* [2016](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib5)) published on 2016 with modification. Without instructions from the paper, it is almost impossible to adjust each hyperparameter of the DCGAN models for good results. Codes in that paper were written for color images with a resolution of 64 × 64. If images in the MNIST database were resized from 1 × 28 × 28 to 1 × 64 × 64, the training time of the model would be significantly longer. By keeping the original MNIST image resolution, both the generator model and the discriminator model only need four neural layers, not five neural layers. Since MNIST and Fashion MNIST have the same structure, the codes of the following project can be used for either of the two datasets by changing the dataset name on line 04 of Cell 01 and line 01 in Cell 02. Fake images in figures [3.5](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig5)(B) and (D) are outputs of the DCGAN project with a learning rate scheduler shown in figure [3.6](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig6)(C). The quality of these fake images is good, but not good enough, especially for the fake Fashion MNIST images. It is not easy to generate detailed patterns on those fake Fashion MNIST images with alphabets and trademarks.

![Figure 3.5. (A, C) Real MNIST and real Fashion MNIST images. (B, D) Fake MNIST and fake Fashion MNIST images generated by a DCGAN with a lambda learning rate for model D and lr\_G/lr\_D = 50. Model training time is 28 min. Reproduced from Deng (2012). CC BY 3.0.](images/bk978-0-7503-6244-3ch3f5_online.jpg)

**Figure 3.5.** (A, C) Real MNIST and real Fashion MNIST images. (B, D) Fake MNIST and fake Fashion MNIST images generated by a DCGAN with a lambda learning rate for model D and lr\_G/lr\_D = 50. Model training time is 28 min. Reproduced from Deng ([2012](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib7)). CC BY 3.0.

![](images/bk978-0-7503-6244-3ch3uf10_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf11_pr.gif)

![Figure 3.6. Model training history (A) MNIST dataset loss curves for model D and G. (B) Fashion MNIST dataset loss curves for model D and G. Reproduced from Xiao et al (2017) CC BY 3.0. (C) A lambda learning rate scheduler with three segments for D\_lr and G\_lr = 50\*D\_lr. Black dashed lines were drawn based on theory values.](images/bk978-0-7503-6244-3ch3f6_online.jpg)

**Figure 3.6.** Model training history (A) MNIST dataset loss curves for model D and G. (B) Fashion MNIST dataset loss curves for model D and G. Reproduced from Xiao *et al* ([2017](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib6)) CC BY 3.0. (C) A lambda learning rate scheduler with three segments for D\_lr and G\_lr = 50\*D\_lr. Black dashed lines were drawn based on theory values.

The generator model class defined in Cell 07 has four transposed convolution layers. Its last layer has no batch normalization operation according the DCGAN paper. Model G's input is a 2D tensor with size of *batch\_size × z\_dim*. According to the paper, the latent dimension *z\_dim* was set to be equal to 100. Noise tensors are generated during model training, and they will be filled with random numbers generated by a standard normal distribution. A 2D noise tensor was first converted into a 4D tensor in the ‘forward’ function by two *unsqueeze(dim = −1)* functions, and was then processed by the four transposed convolution layers. Because the activation function of the model is *Tanh()*, the pixel values of output images from model G is in the range \[−1,1\]. In another extra cell after Cell 07, running ‘D(G(fixed\_latent))’, you will verify that the two models are functional.

![](images/bk978-0-7503-6244-3ch3uf12_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf13_pr.gif)

In the DCGAN paper, a constant learning rate was set to be equal to 2 × 10^(−4) for both models. Although this setting works, I tried to tune the loss curves to match theoretical curves with a lambda learning rate scheduler shown in figure [3.6](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig6)(C). Since model D is smarter than model G, the learning rate of model G was set to be 50 × D\_lr. The following equation is the lambda function. If the initial learning rate and *k* were set to be 4 × 10^(−5) and 500, respectively, the loss curves of MNIST's model training could also be tuned to follow theoretical curves

  
$$\\mathit{lr} = lr\_{0} \\times \\left\\{ \\begin{matrix} {0.099i + 0.01\\left( {i < 10} \\right)} \\\\ {e^{- 0.184 \\times {({i - 10})}}\\left( {10 \\leqslant i < 40} \\right)} \\\\ {0.004\\left( {i \\geqslant 40} \\right)} \\\\ \\end{matrix} \\right.$$  
graphic style="width:16.1875em;" xlink:href="bk978-0-7503-6244-3ch3ueqn33.gif" position="float"/

For the epoch in the range \[0, 10), D\_lr linearly increases from 4 × 10^(−7) to 4 × 10^(−5); for the epoch in the range \[10, 40), the D\_lr exponentially decreases to 1.6 × 10^(−7), and then keeps the rate in the last ten epochs. The Loss\_D and Loss\_G curves are almost straight lines for the Fashion MNIST dataset. With bigger G\_lr, it is easier and faster to generate good MNIST images. Codes in Cell 13 can be used to generate and show a single fake MNIST image. Every time you run it, you will see a different image. Occasionally, we cannot find a digit in a noisy image.

#### 3.2.3 Using a DCGAN to generate fake anime-faces and fake CelebA images

Anime-faces Dataset (Chao [2019](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib1)) was created by Brian Chao with a Database Contents License (DbCL). After downloading a zip file and unzipping it (7.7 GB) in your computer, you will see 63 632 high-quality face images of carton characters. These color images have no labels, and their resolutions vary from 27 × 27 to 120 × 120. We used the tool named *ImageFolder* from Torchvision to pack these images into a dataset. All the images in the dataset were then resized to a resolution of 64 × 64, and the value of each pixel was shifted to a range \[−1, 1\]. Both model D and model G have five layers. The DCGAN codes for the Anime-faces dataset can also be used for the CelebFaces Attributes Dataset (CelebA) Dataset) (Liu *et al* [2015](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib3)) by just changing the image file path on the last line in Cell 01. This dataset contains 202 599 high resolution (178 × 218) color photos. Fake images generated by the DCGAN model are shown in figure [3.7](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig7). The model training time of the two datasets were around 44 and 150 min, respectively.

![](images/bk978-0-7503-6244-3ch3uf14_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf15_pr.gif)

![Figure 3.7. (A) Fake anime-faces dataset images generated by DCGAN at the 20th epoch of model training with a learning rate scheduler shown in figure 3.8(C). Real images for model training are reproduced from Churchill and Chao (2019) with a license DbCL v1.0. (B) Fake CelebA images generated by DCGAN at the 16th epoch of model training. The CelebA dataset is used with permission from Liu et al (2015) courtesy of Ziwei Liu.](images/bk978-0-7503-6244-3ch3f7_online.jpg)

**Figure 3.7.** (A) Fake anime-faces dataset images generated by DCGAN at the 20th epoch of model training with a learning rate scheduler shown in figure [3.8](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig8)(C). Real images for model training are reproduced from Churchill and Chao ([2019](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib1)) with a license DbCL v1.0. (B) Fake CelebA images generated by DCGAN at the 16th epoch of model training. The CelebA dataset is used with permission from Liu *et al* ([2015](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib9)) courtesy of Ziwei Liu.

According the GAN paper (Goodfellow *et al* [2014](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib2)), a constant learning rate (2 × 10^(−4)) is used for model training. During each training process with 20 epochs, model G's loss function values increase to above 5.0, and model D's loss decreases to below 0.2. The fake images generated by the system were worse and worse with the constant learning rate on my computer. Finally, you only get one kind of face with one eye in all fake images. That is a phenomenon called ‘model collapse’ in GAN's model training. It is caused by a weaker mode G and a smarter model D. Just as with a student who is not smart enough to understand his teacher's instruction to improve his homework, their teacher will find it easy to see mistakes in the student's homework. Still using constant learning rates, I adjusted model G's learning rate to 800% of the model D's learning rate. Although the quality of those fake images was improved, we could easily distinguish them by eye from those real images in the dataset. From figure [3.8](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig8), you can see that a lambda scheduler was used for training of model D. Its learning rate was 10^(−4) in the first five epochs, and then the learning rate exponentially decreased to 10^(−6) at the end of model training. Model G's learning rate was set to be 18 times model D's learning rate. Other ratios for G\_lr and D\_lr such as 10, 15, 20 and 21 were tested with good results.

![](images/bk978-0-7503-6244-3ch3uf16_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf17a_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf17b_pr.gif)

![Figure 3.8. Training loss curves with a Lambda learning rate scheduler for the Anime-faces Dataset. (A) Loss curves. (B) Average of D(X) and D(G(Z)). (C) Model D's Lambda learning rate scheduler with G\_lr = 18 × D\_lr. Black dash lines were drawn based one theory values.](images/bk978-0-7503-6244-3ch3f8_online.jpg)

**Figure 3.8.** Training loss curves with a Lambda learning rate scheduler for the Anime-faces Dataset. (A) Loss curves. (B) Average of D(X) and D(G(Z)). (C) Model D's Lambda learning rate scheduler with G\_lr = 18 × D\_lr. Black dash lines were drawn based one theory values.

In a project of the last section for MNIST image generation, lambda functions with three segments were used to fine tune model loss values. Changing the ratio *k* (= G\_lr/D\_lr) from 4, 8, 10, 20, 50, 200, 400, 500 and 1000, we could obtain crystal clear fake MNIST images. What is the best ratio of the two learning rates? Images from the anime-faces dataset are very good samples for us to search the best ratio *k*, because they contain more detailed information. From eye sizes, color, nose and mouth positions on fake images, our eyes can see very small differences. Twenty is a critical number for the ratio *k* with the initial learning rate set to be equal to 10^(−4), although the loss function curves of the two models are not straight lines. With small fluctuations on those loss values around theory values, the GAN models can generate fake images with detailed information. With higher ratio *k*, those loss curves could be tuned to straight lines, but the DCGAN models learnt slowly, and fake images were noisier, and even had ghost faces. With lower ratio *k*, the DCGAN's model D is smarter than its mode G, so the loss values of model G will increase epoch by epoch. If mode G’s loss value is above six, the GAN system will have ‘model collapse’ issues as shown in figure [3.9](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig9). Fake images from the lower ratio *k* are also noisier.

![Figure 3.9. Fake Anime-faces dataset images generated by the DCGAN with model collapse issues in four model training explorations. In each of the first three explorations, all 48 fake images were the same, and only images in the first row were shown.](images/bk978-0-7503-6244-3ch3f9_online.jpg)

**Figure 3.9.** Fake Anime-faces dataset images generated by the DCGAN with model collapse issues in four model training explorations. In each of the first three explorations, all 48 fake images were the same, and only images in the first row were shown.

### 3.3 Conditional deep convolutional GANs

Although DCGANs can generate high-quality fake images, it is impossible to generate fake images with a specific class or style set by us. After Mehdi Mirza and Simon Osindero published their paper (Mirza and Osindero [2014](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib4)) titled ‘Conditional generative adversarial nets’ in 2014, we have a powerful tool: conditional deep convolutional GANs (cDCGAN), which can generate fake images according to our requirements. We can even use text or sound prompts to instruct a cDCGAN to generate any kind of fake images similar to real images in a train dataset. In a project of the last section for MNIST image generation, we discarded label information. Now we will encode each label of each image as an extra channel of the image. Then, a batch of images with label information is packed into a 4D tensor as the input of model D in a cDCGAN. In the last section, we used a 1 × 100 noise tensor as the input of model G to generate a fake image. Now we will use a 1 × 110 tensor for model G to generate a fake image. The extra 10 elements come from a fake label in range \[0,9\] for MNIST dataset. The codes for training the two models are almost the same as those in DCGANs. Parameters of models will be updated during model training, so that our models are smart enough to generate realistic fake images with the specific digits we asked for. An embedding class of PyTorch is used to encode information of the label with its image.

On line 02 of the following Extra Cell ONE is a 1D tensor with five labels in a batch images of a MNIST dataloader. An instance of the embedding class on line 04 would embed the 1D tensor into a 5 × 3 tensor filled with random numbers before model training. The first parameter of the instance is the class number (10) of MNIST. The maximum value of the 1D tensor should be nine. The second parameter of the instance is the embedding output's column number. The embedding output's row number is equal to the length of the 1D label tensor. Since the first and the last elements in the 1D tensor are the same in the example, the first row and the last row of the embedding output are the same. The parameters of the embedding instance will be updated during model training.

![image](images/bk978-0-7503-6244-3ch3uf18_pr.gif)

#### 3.3.1 Applications of a cDCGAN to MNIST and fashion MNIST datasets

Fashion-MNIST (Xiao *et al* [2017](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib6)) is a dataset created by the German company Zalando. It has the same structure as the MNIST dataset: a training dataset and a test dataset containing 60 000 and 10 000 labeled black and white images, respectively. The resolution of those images is 28 × 28. The images are categorized into ten classes (0 to 9) for t-shirt/top, trouser, pullover, dress, coat, sandal, shirt, sneaker, bag and ankle boot. Running a code *train\_Dataset.classes* in an extra cell after Cell 04 in project [3.3.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3ueqn30), you will see these category names. Since the dataset structures of MNIST and Fashion MNIST are the same, the codes in the project can be used for the two datasets, respectively, by changing the dataset name in Cell 01 and Cell 02. Fake MNIST images and Fake fashion MNIST images generated by the cDCGAN are shown in figure [3.10](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig10). Their quality is good enough compared with real images.

![](images/bk978-0-7503-6244-3ch3uf19a_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf19b_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf20_pr.gif)

![Figure 3.10. Fake MNIST images (left) and Fake Fashion MNIST images (right) generated by cDCGAN. They are the outputs of Cell 11. Model training time is 11 min.](images/bk978-0-7503-6244-3ch3f10_online.jpg)

**Figure 3.10.** Fake MNIST images (left) and Fake Fashion MNIST images (right) generated by cDCGAN. They are the outputs of Cell 11. Model training time is 11 min.

The code on line 22 of Cell 06 is the embedding class's instance *nn.Embedding(10, 784)*. With the first line of the forward function in the model D, each image in a batch of a dataloader is reshaped into a 1D tensor with 784 elements. Using the embedding instance, the second line of the forward function encodes each label in the batch into a 1D tensor with 784 elements. Now we have two tensors, and they have the same shape: batch\_size × 784. These two tensors are concatenated along the row direction (dim = 1). The result is a longer tensor with a shape of batch\_size × 1568. Then, it is reshaped into a 4D tensor with a shape of batch\_size × 2 × 28 × 28, and it is then processed through the convolution network of model D as usual. The output of model D is an 1D tensor with batch size elements. Each of the elements is a positive number with a value between 0 and 1 because of the sigmoid activation function in model D. According the GAN paper, batch normalization in layer 01 and layer 04 is not used. With this setting, the bias options of the two convolutions are set to be ‘True’ by default.

![](images/bk978-0-7503-6244-3ch3uf21_pr.gif)

 

Model G's forward function needs two inputs. One is a tensor for a batch of latent vectors as usual, and another is a 1D fake label tensor which is then embedded into a tensor with a shape of batch\_size × 10. The two tensors are then concatenated along the row direction (dim = 1). The result is a tensor with a shape of batch\_size × 110. Then it is reshaped into a 4D tensor with a shape of batch\_size × 110 × 1 × 1, and is then processed through a transposed convolution network in model G as usual. The output of model G is a batch of images. Layer 04 of model G also has no batch normalization operation.

![](images/bk978-0-7503-6244-3ch3uf22_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf23_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf24_pr.gif)

 

Codes from Cell 08 to Cell 13 are almost the same as those in the last section. The only difference is that the label information is added to the system. On the last two lines of Cell 01, a 1D long tensor named ‘fixed\_labels’ is created by ‘\[*i* for *i* in range(10) for *j* in range(10)\])’. There are 100 digits in the 1D long tensor. This 1D tensor and another 100 × 100 tensor named ‘fixed\_latent’ in Cell 01 are used in Cell 11 to generate fake MNIST images during model training for us to check fake image quality. Training the two models is easy. Using a constant lambda scheduler (v = lambda i: 1) and the ratio *k* = 5, I obtained high-quality fake MNIST images in about 10 min. The cDCGAN uses a variable learning rate shown in figure [3.11](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig11)(F) for the fashion MNIST dataset. Those loss curves, D(X) and D(G(Z)) curves are almost straight lines.

![Figure 3.11. (Top) Training history of a cDCGAN for MNIST with two constant learning rates. (Bottom) for Fashion MNIST with a lambda learning rate scheduler shown in (F). Black dashed lines were based on theory values.](images/bk978-0-7503-6244-3ch3f11_online.jpg)

**Figure 3.11.** (Top) Training history of a cDCGAN for MNIST with two constant learning rates. (Bottom) for Fashion MNIST with a lambda learning rate scheduler shown in (F). Black dashed lines were based on theory values.

#### 3.3.2 Applications of a cDCGAN to generate fake Rock Paper Scissors images

There are many datasets with beautiful color photos, but they are very big and take very long time for model training by ordinary laptops. In the following project [3.3.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3ueqn36), the Rock Paper Scissors dataset is used. The dataset was created by Laurence Moroney. He kindly permits people to share and adapt the dataset for all uses: commercial or non-commercial under a license of Attribution 2.0 Canada. It is a small color image dataset with three classes. Images of three hand shapes from different races, ages and genders were saved in three folders: test, train and validation. In the train folder there are three sub-folders for hands in shapes of rock, paper and scissors, a game that originated in China. A hand in the ‘rock’ shape is a closed fist (label 1); a hand in the ‘paper’ shape is an open fist (label 0), and a hand in the ‘scissors’ shape is a fist with the thumb, the index finger and the middle finger extended (label 2). When Torchvision ImageFolder packs those images from the train folder into a dataset, the name of each sub-folder will be used to label images in the sub-folder. There are three classes in the train dataset, and each class contains 840 images with a resolution of 300 × 300. Codes in Cell 01 to 04 input and pack the dataset, slice images of the dataset into a dataloader, and display a batch of images shown figure [3.12](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig12)(A). Fake images generated by a cDCGAN in the project are shown in figure [3.12](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig12)(B), the outputs of Cell 11.

![](images/bk978-0-7503-6244-3ch3uf25_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf26_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf27_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf28_pr.gif)

![](images/bk978-0-7503-6244-3ch3uf29_pr.gif)

![Figure 3.12. (A) Real images in the Rock Paper Scissors dataset, the output of Cell 04. Model training time is 20 min. Reproduced from Moroney (2021) CC BY 3.0. (B) Fake images, images in each row belong to a class (0: paper, 1: rock, 2: scissors), the output of Cell 11.](images/bk978-0-7503-6244-3ch3f12_online.jpg)

**Figure 3.12.** (A) Real images in the Rock Paper Scissors dataset, the output of Cell 04. Model training time is 20 min. Reproduced from Moroney ([2021](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3bib10)) CC BY 3.0. (B) Fake images, images in each row belong to a class (0: paper, 1: rock, 2: scissors), the output of Cell 11.

The code structure for this project is almost the same as the one in section [3.3.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-3-1). This project is for color images with a resolution of 128 × 128 and three image classes. Model D in Cell 06 has six convolution layers, and model G in Cell 07 has five transposed convolution layers. Because of the layer number difference, model D is smarter than model G. In Cell 08, a multiplicative learning rate scheduler is used for model training. The learning rate function curve is shown in figure [3.13](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3fig13)(C). Starting from 4 × 10^(−4), the learning rate exponentially decreases according to a function: 4 × 10^(−4) × (0.91)^(epoch). The multiplicative learning rate scheduler prevents the issue of explosion of loss function values. Running codes in Cell 13, you will generate a single big fake color image with the desired label for an integer from 0 to 2 in the function: *generate\_image(G, 0)*, and you will find its quality is not good enough comparing with real images.

![Figure 3.13. Model training history. (A) Loss curves for model D and G. (B) D(X) curves and D(G(Z)) curves. (C) The learning rate scheduler for model D, and model G's learning is equal to 25\*lr\_D.](images/bk978-0-7503-6244-3ch3f13_online.jpg)

**Figure 3.13.** Model training history. (A) Loss curves for model D and G. (B) *D*(*X*) curves and *D*(*G*(Z)) curves. (C) The learning rate scheduler for model D, and model G's learning is equal to 25\*lr\_D.

### References

Churchill S and Chao B 2019 Anime face dataset: a collection of high-quality anime faces. [https://www.kaggle.com/datasets/splcher/animefacedataset](https://www.kaggle.com/datasets/splcher/animefacedataset)

Deng L 2012 The MNIST database of handwritten digit images for machine learning research 141–2 *IEEE Signal Process. Mag.* **29** 141–2

Goodfellow I, Pouget-Abadie J, Mehdi Mirza B X, Warde-Farley D, Ozair S, Courville A and Bengio Y 2014 Generative adversarial nets *Proc. of the Int. Conf. on Neural Information Processing Systems* 2672–80

Liu Z, Luo P, Wang X and Tang X 2015 Deep learning face attributes in the wild *Proc. of the IEEE Int. Conf. on Computer Vision* 3730–8

Liu Z, Luo P, Wang X and Tang X 2015 *Proc. of Int. Conf. on Computer Vision (ICCV)* [https://liuziwei7.github.io/papers/faceattributes\_poster.pdf](https://liuziwei7.github.io/papers/faceattributes_poster.pdf)

Mirza M and Osindero S 2014 Conditional generative adversarial nets *arXiv preprint arXiv:[1411.1784](http://arxiv.org/abs/1411.1784)*.

Moroney L 2021 Rock Paper Scissors Dataset [https://universe.roboflow.com/landada/rock-paper-scissors-hchrz](https://universe.roboflow.com/landada/rock-paper-scissors-hchrz) (accessed 29 November 2023)

Radford A, Metz L and Chintala S 2016 Unsupervised representation learning with deep convolutional generative adversarial networks *CoRR*, abs/1511.06434.

Xiao H, Rasul K and Vollgraf R 2017 Fashion-mnist: a novel image dataset for benchmarking machine learning algorithms *arXiv preprint arXiv:[1708.07747](http://arxiv.org/abs/1708.07747)*.

Xiao H, Rasul K and Vollgraf R 2017 Fashion-MNIST: a novel image dataset for benchmarking machine learning algorithms [https://github.com/zalandoresearch/fashion-mnist](https://github.com/zalandoresearch/fashion-mnist).

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 4

## Image generation by WGANs with gradient penalty

Wasserstein generative adversarial networks (WGANs) and WGANs with gradient penalty (WGAN-GP) are introduced in this chapter to solve model collapse issues in GAN model training. The quadratic curve dataset, MNIST, Anime Face, and CelebA datasets are used. A conditional WGAN-GP is implemented to the Rock Paper Scissors dataset to generate images according to our settings. Although model training time is longer, the quality of fake images generated in this chapter is higher.

Using GANs, we can generate photo-realistic fake images, but it is not easy to train GAN models because of model collapse issues. From our projects in previous chapters, we know that the discriminator model D is usually smarter than model G in most GANs. It is easy for model D to see the difference between fake images and real images, and model G is not powerful enough to improve its skill to fool model D. In model training of many GAN projects the values of model D's loss function would decrease step by step to zero and the values of model G's loss function would increase to above 6 in less than 20 epochs. We then have model collapse issues at the end of model training. By choosing different learning rate schedulers with different initial learning rates, we can tune models to prevent model collapse. However, it takes a long time (hours and days) to adjust model hyperparameters and learning rate schedulers for each GAN project.

In 2017, Martin Arjovsky (Arjovsky *et al* [2017](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib1)) and his colleagues introduced a WGAN to stablilize model training and to prevent issues such as model collapse. In a WGAN, a generator *G* and a discriminator *D* are used as usual in a GAN. A difference is that no activation function is used at the end of WGAN's discriminator *D*. The output of the discriminator *D* for an image in a batch of a dataloader is a real number which can be in a range from negative infinite to positive infinite (−∞, +∞). From a batch of real images (*X*), we obtain a batch of 1D vectors *D*(*X*). A batch of fake images *G*(*Z*) is generated from a batch of noise vectors (*Z*) in a latent space with *z\_dim* dimensions. Using the batch of fake images as input, model D outputs another batch of 1D vectors *D*(*G*(*Z*)). Model D's loss function is the average of *D*(*G*(*Z*)) subtracts the average of *D*(*X*) as shown in equation ([4.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4eqn1)), and model G's loss function is shown as equation ([4.2](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4eqn2))

  
$$L\_{D}\\left( \\theta\_{d} \\right) = \\frac{1}{n}\\sum\\limits\_{i = 1}^{n}{D\\left( {G\\left( z\_{i} \\right)} \\right)} - \\frac{1}{n}\\sum\\limits\_{i = 1}^{n}{D\\left( x\_{i} \\right)}$$  
(4.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch4eqn1.gif" position="float"/

  
$$L\_{G}\\left( \\theta\_{g} \\right) = - \\frac{1}{n}\\sum\\limits\_{i = 1}^{n}{D\\left( {G\\left( z\_{i} \\right)} \\right)}$$  
(4.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch4eqn2.gif" position="float"/

According to the WGAN paper (Arjovsky *et al* [2017](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib1)), there is a mathematical condition (1-Lipschitz continuity) to use the above loss functions in a WGAN: the absolute values of derivatives of model D's loss function should be less than 1.0. This condition could be fulfilled by clipping model D's weights in the range \[−0.01, 0.01\]. However, in the following project [4.1.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4ueqn4) the quality of fake images generated by WGAN is worse than DCGAN, even WGAN codes run a longer time with more epochs. In 2017, Ishaan Gulrajani and his colleagues improved WGAN with a new method published in their paper (Gulrajani *et al* [2017](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib2)) titled ‘Improved training of Wasserstein GANs’. The paper proposed an alternative way to enforce the 1-Lipschitz continuity by adding a penalty to model D's loss function as shown in equation ([4.3](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4eqn3)). This modified WGAN is called Wasserstein GAN with gradient penalty (WGAN-GP)

  
$$L\_{D}\\left( \\theta\_{d} \\right) = \\frac{1}{n}\\sum\\limits\_{i = 1}^{n}{D\\left( {\\widetilde{x}}\_{i} \\right)} - \\frac{1}{n}\\sum\\limits\_{i = 1}^{n}{D\\left( x\_{i} \\right)\\ + \\ }\\frac{\\lambda}{n}\\sum\\limits\_{i = 1}^{n}\\left\\lbrack \\left( {{\\mid\\mid}\\nabla\_{{\\widehat{x}}\_{i}}D{({\\widehat{x}}\_{i})}\\mid\\mid\_{2} - 1} \\right)^{2} \\right\\rbrack$$  
(4.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch4eqn3.gif" position="float"/

In the formula, *x*[*i*] is a real image in a batch of a dataloader, *x̃*[*i*]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch4ieqn4.gif"/ is a fake image generated by the generator model *G*(*z*[*i*]) from a noisy vector *z*[*i*], and *x̂*[*i*]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch4ieqn5.gif"/ is an interpolation between *x*[*i*] and *x̃*[*i*]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch4ieqn6.gif"/ by *x̂*[*i*] = *ε**x*[*i*] + (1−*ε*)*x̃*[*i*]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch4ieqn7.gif"/, where ε is a random number uniformly distributed within \[0,1), and λ is a penalty coefficient which was set to be equal to 10 in the WGAN-GP paper (Gulrajani *et al* [2017](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib2)). Before we introduce the WGAN-GP theory, we need to know how to calculate ∇[*x̂*[*i*]]*D*(*x̂*[*i*])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch4ieqn8.gif"/ which is a gradient of a scalar function to a vector. Suppose we have a 1D tensor *x* = \[0, 0.5, 1.5, 2.0\], and a scalar function *f* is defined as the sum of squares of the tensor's elements: *f*(*x*) = *x*[0]² + *x*[1]² + *x*[2]² + *x*[3]²inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch4ieqn9.gif"/. The gradient of the function to the vector *x* is ∇*f*(*x*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch4ieqn10.gif"/, and its norm  ∣  ∣ ∇*f*(*x*) ∣ ∣[2]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch4ieqn11.gif"/ to the given vector *x* at *x* = \[0, 0.5, 1.5, 2.0\] are listed below:

  
$$\\nabla f\\left( x \\right) = \\left\\lbrack {\\frac{\\partial f}{\\partial x\_{0}},\\frac{\\partial f}{\\partial x\_{1}},\\frac{\\partial f}{\\partial x\_{2}},\\frac{\\partial f}{\\partial x\_{3}}} \\right\\rbrack = \\left\\lbrack {2x\_{0},2x\_{1},2x\_{2},2x\_{3}} \\right\\rbrack = \\left\\lbrack {0,1,3,4} \\right\\rbrack$$  
graphic style="width:27.75em;" xlink:href="bk978-0-7503-6244-3ch4ueqn12.gif" position="float"/

  
 ∣ ∣∇*f*(*x*) ∣ ∣[2] = (0²+1²+3²+4²)^(1/2) = 5.1  
graphic style="width:16.5625em;" xlink:href="bk978-0-7503-6244-3ch4ueqn13.gif" position="float"/

The gradient norm  *∣* *∣*∇*f*(*x*) ∣ ∣[2]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch4ieqn14.gif"/ is the Euclidean norm for each row in a gradient tensor. Since there is only one row in the above gradient tensor ∇*f*(*x*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch4ieqn15.gif"/, there is one element in the norm. Each element of the norm is equal to the square root of the sum of each element's square in the gradient's row. Imported from PyTorch, an autograd.grad class in the following Extra Cell ONE can do the above job automatically. The output of the class's instance is a tuple with the gradient tensor as its only element. Using ‘\[0\]’ at the end of the output of the class instance, we picked out the gradient tensor from the tuple. According the last part of equation ([4.3](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4eqn3)), the gradient penalty of the following codes is: *λ*(5.1−1)² = 168inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch4ieqn16.gif"/.

![](images/bk978-0-7503-6244-3ch4uf1_pr.gif)

### 4.1 Using a WGAN or a WGAN-GP for generation of fake quadratic curves

The detailed mathematical principles of WGAN and WGAN-GP are very complex. Codes for the following project [4.1.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4ueqn4) about quadratic curve generation are used to help us understand them. Open a new Jupyter notebook in the VS Code, copy Cells 01-5 from section [3.1.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-1-1), and paste them in the new notebook. You should delete the activate class *nn.Sigmoid()* at the end of Cell 05 for the discriminator D. Some hyperparameters are added or modified specially for the new project. The following codes are for WGAN-GP. If you remove hash tag symbols # in front of line 04, 05 and 12 in Cell 08, and add # symbols in front of line 10 and 11 in the same Cell, the codes are modified for WGAN. Figure [4.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig1) shows the outputs of the project. You can see that the quality of fake curves generated by WGAN-GP with RMSprop optimizer is better.

![](images/bk978-0-7503-6244-3ch4uf2_pr.gif)

![Figure 4.1. (A) Fake curves generated by WGAN. (B) Fake curves generated by WGAN-GP with the RMSprop optimizer. (C) Fake curves generated by WGAN-GP with the Adam optimizer. Some hyperparameters are listed in graphs (12k = 12 000). Model training time is 24 min.](images/bk978-0-7503-6244-3ch4f1_online.jpg)

**Figure 4.1.** (A) Fake curves generated by WGAN. (B) Fake curves generated by WGAN-GP with the RMSprop optimizer. (C) Fake curves generated by WGAN-GP with the Adam optimizer. Some hyperparameters are listed in graphs (12*k* = 12 000). Model training time is 24 min.

![](images/bk978-0-7503-6244-3ch4uf3a_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf3b_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf4_pr.gif)

 

Within the seven cells of project 4.1.1, only Cell 06 is new. The function *gradient\_penalty* needs three inputs: the discriminator model D, a batch of real curves (64 × 21 tensor) and a batch of fake curves (64 × 21 tensor). The above Extra Cell TWO is used to help us to understand how to construct an interpolation curve from a real curve and a fake curve. The first three lines in the extra cell generate a 64 × 21 tensor for a batch of 64 real curves and a same size tensor for a batch of 64 fake curves. The code on the fourth line generates a 64 × 1 random tensor named ‘eps’ which is then expanded by the code on the sixth line into a 64 × 21 tensor. Each element in a row of the expanded eps tensor is a same random number. The *eps* \[63\] printed on screen is an example of the last row of the expanded tensor. With codes in the last four lines in the extra cell, you will know how to calculate the interpolation tensor. Each interpolation curve is obtained by element-wise calculations according to the formula on line 9: *interpolation = eps \* curves\_real + (1−eps) \* curves\_fake*. The output of line 13 is the result of manual calculations about the last element of the last interpolation curve. It is the same as the last element of the output of line 12. A batch of interpolations will be used as an input of model D which outputs a batch of scalars (line 07 in Cell 06). The batch of scalars has a name ‘interp\_logits’ and its gradients to the interpolation are obtained by codes on line 08 in Cell 06 for the gradient penalty.

![](images/bk978-0-7503-6244-3ch4uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf6_pr.gif)

 

According to the WGAN paper (Arjovsky *et al* [2017](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib1)), the RMSprop optimizer should be used. You can try the Adam optimizer in Cell 07, but there is not much difference about the quality of the fake curves generated by the WGAN. At the end of the Extra Cell TWO, if you add and run the following code *D(torch.FloatTensor(*y*).cuda()).T*, you will get a 1 × 64 tensor listed below, where *y* is a 64 × 21 numpy array generated by Cell 02 for real curves. Each real curve was compressed by model D into a real number in the 1D critical space

tensor(\[\[−0.0117, 0.0057, −0.0153, −0.0998, −0.1126, −0.0682, −0.0417, −0.0155,

−0.0779, −0.1115, 0.0053, 0.0025, 0.0029, −0.1112, −0.0124, −0.1099,

−0.0176, −0.0806, −0.0436, −0.0785, −0.0720, −0.0747, −0.0176, −0.0962,

−0.0622, −0.0094, −0.0295, −0.0681, −0.0810, −0.0414, −0.0492, −0.0683,

−0.0849, −0.0824, −0.0509, −0.0292, −0.1097, −0.0534, −0.0341, −0.1099,

−0.1024, −0.0659, −0.0413, −0.0531, 0.0039, −0.0964, −0.0046, −0.0288,

−0.0428, −0.0430, −0.0190, −0.0657, −0.1021, −0.0610, −0.0137, −0.0826,

−0.0550, −0.0018, −0.0918, −0.0722, −0.0053, −0.0519, −0.0776, −0.0334\]\],

device = ‘cuda:0’, grad\_fn = <PermuteBackward0>)

There is a probability distribution function hidden in these numbers in the 1D critical space. We only care about the mean of the PDF with a hypothesis that the PDF follows a normal distribution with a constant variance. Changing the ‘T’ in the above code to mean() for the above 64 numbers, you will get the average of those 64 numbers *D*(*X*) = −0.1803. It is a scalar tensor. WGAN uses the average number as a statistic location for these real curves in the 1D critical space. Using the code: *D (G(torch.randn(batch\_size, z\_dim, requires\_grad = True).cuda())).mean()*, you will get the average of another 1D tensor with 64 elements: *D*(*G*(*Z*)) = 0.0046. This is the statistic location of a batch of fake curves. The WGAN's model D wants to maximize the distance between *D*(*X*) and *D*(*G*(*Z*)), so it is possible for model D to distinguish true curves from fake curves. The distance is called the ‘Wasserstein distance’ or ‘Earth moving distance’. In computer vision projects, we always use a gradient descendent algorithm to find the minimum of a loss function during model training. We have to use the loss function shown in equation ([4.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4eqn1)) to minimize the negative Wasserstein distance for model D. The WGAN's model G wants to fool model D by maximizing *D*(*G*(*Z*)). With the same mathematical reasoning, we choose model G's loss function as shown in equation ([4.2](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4eqn2)).

The mathematical concept of Wasserstein distance is not easy to understand. Suppose you want to remove a pyramid from Giza in Egypt to Athens in Greece and build the exact same pyramid, there are many ways to move the stone blocks of the pyramid. One way is towards China, across the Pacific Ocean to America, and then across the Atlantic Ocean and Mediterranean Sea to Athens. A shorter path is north across the Mediterranean Sea to Athens. The shortest path is the ‘Earth moving distance’ on which we finish a project with the shortest time and the minimum cost. Jensen–Shannon divergence is used in the loss function of GAN's model D (section [3.1.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-1-1)). If real samples’ PDF and the fake samples’ PDF do not overlap, the value of the loss function will be a constant (zero), and the gradients of the loss function will also be zero. Model D will not be trained with vanished gradients. Wasserstein distance is introduced to solve this issue.

For stable model trainings, the WGAN paper instructed that the model D is trained more times (*n*[critic] = 5) than model G. In the first for-loop in Cell 08, each batch of real curves and fake curves are trained *n*[critic] times. These extra calculations significantly increase training time. But if we are sure that our model training will provide good results in hours or days, we would like to wait. Another for-loop in Cell 08 is used to limit model D's weights by clipping (*c* = 0.01) specifically for WGAN. The paper instructs us to do so for model D's 1-Lipschitz continuity. Figure [4.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig1) shows the outputs of the above codes in three conditions. The WGAN-GP paper (Gulrajani *et al* [2017](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib2)) instructs us to use the Adam optimizer. But from figure [4.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig1)(B), we can see the RMSprop optimizer is better than Adam for this project. Loss function curves and WGAN-GP's gradient penalty curves are shown in figure [4.2](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig2).

![Figure 4.2. Loss function curves for WGAN and GAN-GP. Hyper-parameter settings for these loss function curves are the same as those shown in figure 4.1.](images/bk978-0-7503-6244-3ch4f2_online.jpg)

**Figure 4.2.** Loss function curves for WGAN and GAN-GP. Hyper-parameter settings for these loss function curves are the same as those shown in figure [4.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig1).

### 4.2 Using a WGAN-GP for Fashion MNIST

Since projects with the MNIST dataset are too easy, we will focus on using WGAN-GP for the Fashion MNIST dataset. If you want, you can change dataset name in Cell 02 of the following project [4.2.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4ueqn9) to get a comparison of the results of the two datasets. Although Fashion MNIST and MNIST have the same structure, images in the first dataset have detailed patterns, such as trade marks on shoes and T-shirts. The detailed information is not easy to restore on fake images. Because ResNet9 did a good job for image classification in the projects in chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2), perhaps ResNet9 has the ability to keep detailed image structure information for fake image generation. Only after using a modified ResNet9 in model D could better fake images be generated, but they were still not good enough compared with real images. My model training time with ResNet9 was over two hours in 30 epochs. Fake fashion MNIST images are shown in figure [4.3](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig3).

![](images/bk978-0-7503-6244-3ch4uf7_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf8_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf9_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf10_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf11_pr.gif)

![Figure 4.3. Fake Fashion MNIST images generated by a WGAN-GP (epochs = 30, ncritic = 1, λ = 10, lr\_D = 2 × 10−4, lr\_G = 10−3, RMSprop optimizer, model training time = 124 min). The Fashion MNIST dataset is from Xiao et al (2017) with a license CC BY 3.0.](images/bk978-0-7503-6244-3ch4f3_online.jpg)

**Figure 4.3.** Fake Fashion MNIST images generated by a WGAN-GP (epochs = 30, *n*[critic] = 1, *λ* = 10, lr\_D = 2 × 10^(−4), lr\_G = 10^(−3), RMSprop optimizer, model training time = 124 min). The Fashion MNIST dataset is from Xiao *et al* ([2017](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib3)) with a license CC BY 3.0.

### 4.3 WGAN-GP for CelebA dataset and Anime Face dataset

By changing the dataset path name in Cell 01 of project [4.3.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4ueqn14), you can use the following WGAN-GP codes for the CelebA dataset or the anime-faces dataset. The model training time for the two datasets are 274 and 85 min, respectively, with epochs = 25 and n\_critic = 1. The model training time would be tripled if n\_critic = 5. Figure [4.4](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig4) shows fake CelebA images randomly generated by the following WGAN-GP codes. Their quality is much better than those generated by DCGAN in section [3.2.3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-2-3). Although the model training is much longer, WGAN-GP saves us a lot of time because we do not need to adjust many hyperparameters to avoid model collapse issues. After model training, you can use Cell 14 to generate a single fake image, and you will find its quality is still not good enough. It is possible to obtain high quality fake images by setting image size to be equal to 256 in Cell 01. In that case, model training time on a laptop with a single GPU would be very long.

![](images/bk978-0-7503-6244-3ch4uf12_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf13_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf14_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf15_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf16_pr.gif)

![Figure 4.4. Fake CelebA images generated by WGAN-GP at epoch = 25 with model training time of 274 min. They are outputs of Cell 12. CelebA dataset is used with permission from Liu et al (2015) courtesy of Ziwei Liu.](images/bk978-0-7503-6244-3ch4f4_online.jpg)

**Figure 4.4.** Fake CelebA images generated by WGAN-GP at epoch = 25 with model training time of 274 min. They are outputs of Cell 12. CelebA dataset is used with permission from Liu *et al* ([2015](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib4)) courtesy of Ziwei Liu.

### 4.4 Implementation of a cWGAN-GP for Rock Paper Scissors dataset

WGAN-GPs only randomly generate fake images. Using a conditional WGAN-GP (cWGAN-GP) system, we can generate fake images for a dataset with class labels set by us. To save model training time, the small Rock Paper Scissors dataset is chosen to demonstrate the application of cWGAN-GP for color images. The model training time of the following project [4.4.1](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4ueqn19) is about 64 min for 100 epochs. Figure [4.5](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig5) shows real images from the dataset, and fake images generated by the following cWGAN-GP codes. It is better to use *nn.InstanceNorm2d()* to replace *nn.BatchNorm()* in model D. Otherwise, the loss function values in figure [4.6](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4fig6) would be higher than 10 000, and the quality of the fake images would be poor. It seems that the Adam optimizer is better than the RMSprop optimizer for this project. When a gradient penalty is calculated in Cell 09, we must generate an interpolation image from a real image and a fake image. Should we use the real label of the real image, or the fake label of the fake image? It is found that using fake labels is the right choice. Using real labels to replace fake labels resulted in model collapse issues. Codes for applications of a cWGAN-GP system for MNIST or Fashion MNIST are listed in appendix [E](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-E).

![](images/bk978-0-7503-6244-3ch4uf17_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf18_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf19_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf20_pr.gif)

![](images/bk978-0-7503-6244-3ch4uf21_pr.gif)

![Figure 4.5. (A) Real images in the Rock Paper Scissors dataset. (B) Fake images generated by cWGAN-GP (images in row 1, 2, 3 are for paper: 0, rock: 1 and scissors: 2 respectively). The Rock Paper Scissors dataset is from Moroney (2021) with a license CC BY 3.0.](images/bk978-0-7503-6244-3ch4f5_online.jpg)

**Figure 4.5.** (A) Real images in the Rock Paper Scissors dataset. (B) Fake images generated by cWGAN-GP (images in row 1, 2, 3 are for paper: 0, rock: 1 and scissors: 2 respectively). The Rock Paper Scissors dataset is from Moroney ([2021](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4bib5)) with a license CC BY 3.0.

![Figure 4.6. Model raining history of cWGAN-GP. (A) Loss curves and the gradient penalty curve, outputs of Cell 13. (B) D(X), D(G(X)) curves. (C) A single fake image with label 0 generated by codes in Cell 14.](images/bk978-0-7503-6244-3ch4f6_online.jpg)

**Figure 4.6.** Model raining history of cWGAN-GP. (A) Loss curves and the gradient penalty curve, outputs of Cell 13. (B) *D*(*X*), *D*(*G*(*X*)) curves. (C) A single fake image with label 0 generated by codes in Cell 14.

### References

Arjovsky M, Chintala S and Bottou L 2017 Wasserstein generative adversarial networks *Int. Conf. on Machine Learning* (PMLR) pp 214–23

Gulrajani I, Ahmed F, Arjovsky M, Dumoulin V and Courville A C 2017 Improved training of wasserstein gans *Adv. Neural Inform. Process. Syst.* **30** 5769–79

Liu Z, Luo P, Wang X and Tang X 2015 Proc. of Int. Conf. on Computer Vision (ICCV) [https://liuziwei7.github.io/papers/faceattributes\_poster.pdf](https://liuziwei7.github.io/papers/faceattributes_poster.pdf)

Moroney L 2021 Rock Paper Scissors Dataset [https://universe.roboflow.com/landada/rock-paper-scissors-hchrz](https://universe.roboflow.com/landada/rock-paper-scissors-hchrz) (accessed 29 November 2023)

Xiao H, Rasu K and Vollgraf R 2017 Fashion-MNIST: a novel image dataset for benchmarking machine learning algorithms [https://github.com/zalandoresearch/fashion-mnist](https://github.com/zalandoresearch/fashion-mnist)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 5

## Image generation by VAEs

This chapter introduces variational autoencoders (VAEs) for unsupervised learning to generate fake quadratic curves and fake MNIST images. It is easy to train models in VAEs, but the quality of the images from VAEs is not as good as that from GANs. VAE-GANs are a hybrid of the two techniques, and they are implemented for MNIST, Fashion MNIST and Anime datasets.

In chapter [3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3), we used generative adversarial networks to generate fake images. Model training of DCGANs and cDCGANs is still a challenge because of model collapse and other issues. It takes a long time to adjust initial learning rates, learning rate schedulers and other hyperparameters to achieve successful model training. In chapter [4](#Chapter_4.xhtml#bk978-0-7503-6244-3ch4), WGAN-GPs were used to stablize model training. We can also use an unsupervised learning algorithm to generate images. Generative models (Kingma and Welling [2013](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5bib2)) based on the algorithm are variational autoencoders (VAEs) which are easy to train. They can be used to generate new data samples (images) that are similar to images in a given dataset by learning a compact representation of the dataset's underlying structure. There are also two models in a VAE system. An encoder model or network maps the input data to a low-dimensional representation (compresses each image into a lower dimensional latent vector). The latent vector can have 1D, 2D, 3D and even more than a hundred dimensions. For example, a MNIST image could be compressed into a vector with only two elements in a 2D latent space. Then a decoder network in the system uses the latent vector to generate an image similar to the original MNIST image. The image compression ratio is 392 (= 784/2). However, VAE is not designed for image compression, because the VAE algorithm is not as good as the JPEG algorithm. VAEs were invented earlier than GANs. The theory is more difficult to understand, and the quality of fake images generated by a VAE are usually not as sharp as those by GAN. So, why should we waste our time learning VAEs?

What we are interested is not the fake images, but those lower dimensional latent vectors generated by a VAE system. Each element in a latent vector is an image characteristic learnt by the VAE system. By tuning values of these elements in the latent vector, we can edit images to generate new images. For example, it is possible for us to change human facial expressions in images from angry to smiling, and change moon phases in images from full moon to new moon. With new techniques based on the VAE algorithm, such as vector quantized variational autoencoders (VQ-VAE), we can achieve state-of-the-art results in unsupervised learning. We can combine VAE with GAN to take advantage of the two techniques for model training. VAEs have been used in many areas, including image generation, anomaly detection, and reinforcement learning.

### 5.1 VAE and beta-VAE

In applications of a VAE system for image generation, each image in a dataset is a point in a high dimensional observed space. For example, each MNIST image is a point in a 784-dimensional space. Usually, our computer memory is not big enough to handle all images in a dataset. We have to slice an image dataset into a dataloader with many batches. Their batch size is a constant *n*. Images in a batch are observed data: *x*[1], *x*[2], …, *x*[*n*]. Each image is generated by a latent vector with elements: *z*[1], *z*[2], …, *z*[*m*], where *m* ≪ *n*. Table [5.1](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5t1) shows the unknown joint probabilities of the observed data points and the unknown latent vectors. The marginal possibilities of *p*(*x*[*j*]) are also unknown (*j* = 1, 2, …, *n*). We assume that the prior distribution *p*(*z*[*i*]) follows a standard normal distribution *N*(0,*I*), where *I* is an identity matrix. According to equation ([1.28](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn28)), we have $p\\left( x\_{j} \\right) = \\sum\\limits\_{i = 1}^{m}{p\\left( {x\_{j},z\_{i}} \\right)} = \\sum\_{z}{p\\left( {x\_{j},z} \\right)}$inline-graphic style="height:3.0625em;" xlink:href="bk978-0-7503-6244-3ch5ieqn1.gif"/. From the negative likelihood of the dataset, we have a loss function:

  
$$L = - {\\ln\\ }\\left( {P\\left( X \\right)} \\right) = - {\\ln\\ }\\prod\\limits\_{j = 1}^{n}{p\\left( x\_{j} \\right)} = - \\sum\\limits\_{j = 1}^{n}{\\ \\ln\\ \\left( {\\sum\_{z}{p\\left( {x\_{j},z} \\right)}} \\right)}$$  
(5.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch5eqn2.gif" position="float"/

**Table 5.1.** Unknown joint probabilities of a VAE system.

| *P*(*X*,*Z*) || *x*[1] || *x*[2] || … || *x*[*n*] || *P*(*Z*) |
| --- | --- | --- | --- | --- | --- |
| *z*[1] || p(*x*[1],*z*[1]) || *p*(*x*[2],*z*[1]) || … || *p*(*x*[*n*],*z*[1]) || *p*(*z*[1]) |
| --- | --- | --- | --- | --- | --- |
| *z*[2] || *p*(*x*[1],*z*[2]) || *p*(*x*[2],*z*[2]) || … || *p*(*x*[*n*],*z*[2]) || *p*(*z*[2]) |
| … || … || … || … || … || … |
| *z*[*m*] || *p*(*x*[1],*z*[*m*]) || p(x[2],z[m]) || … || *p*(*x*[*n*],*z*[*m*]) || *p*(*z*[*m*]) |
| *P*(*X*) || *p*(*x*[1]) || p(*x*[2]) || … || *p*(*x*[*n*]) || 1.00 |

Since the joint probabilities are unknown, we cannot do anything about the loss function directly with the above equation. Luckily, we can build an encoder network which uses each batch of images in a dataloader as the encoder's input to obtain a mean vector and a variance vector for each image in a batch of images. The mean vector and the variance vector are then used to construct a multivariate normal distribution *q*(*z*∣*x*) for each image. Each element of the latent vector of the image is then obtained by sampling from *q*(*z*∣*x*). With the VAE encoder's prior possibilities and Jensen's inequality about *g*(*x*) = −ln(*x*) in section [1.1.4](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1s1-1-4), we can indirectly find the minimum of the loss function of the VAE system. Inside the following minus logarithm function is the average of (*p*/*q*) about *z*, and it should be less than or equal to the average of −ln(*p*/*q*)

  
$$L = - \\sum\\limits\_{j = 1}^{n}{\\ \\ln\\ \\sum\_{z}{q\\left( {z\\mid x\_{j}} \\right)}\\frac{p\\left( {x\_{j},z} \\right)}{q\\left( {z\\mid x\_{j}} \\right)}} \\leqslant - \\sum\\limits\_{j = 1}^{n}{\\sum\_{z}{q(z\\mid x\_{j})\\ln\\ \\frac{p\\left( {x\_{j},z} \\right)}{q\\left( {z\\mid x\_{j}} \\right)}}}$$  
graphic style="width:26.25em;" xlink:href="bk978-0-7503-6244-3ch5ueqn3.gif" position="float"/

  
$$L \\leqslant \\sum\\limits\_{j = 1}^{n}\\left\\lbrack {\\sum\\limits\_{z}{q(z\\mid x\_{j})\\ln\\ \\frac{q(z\\mid x\_{j})}{p{(z)}}} - \\sum\\limits\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( { p(x\_{j}\\mid z)} \\right)}} \\right\\rbrack$$  
graphic style="width:24.125em;" xlink:href="bk978-0-7503-6244-3ch5ueqn4.gif" position="float"/

  
$$L \\leqslant \\sum\\limits\_{j = 1}^{n}\\left( {D\_{KL}(q(z\\mid x\_{j}){\\mid\\mid}p{(z)}) - Ε\_{z \\sim q(z\\mid x\_{j})}\\ln\\ \\left( { p(x\_{j}\\mid z)} \\right)} \\right)$$  
(5.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch5eqn5.gif" position="float"/

We can also build a decoder network (*P*) for the VAE system. The decoder uses latent vectors from the encoder's model *Q* to generate a fake image (*x̂*inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn6.gif"/). We train the decoder for a distribution *p*(*x*∣*z*) as a normal distribution with an identity variance: $p\\left( {x\_{j}\\mid z} \\right) = \\frac{1}{\\sqrt{\\left( {2\\pi} \\right)^{m}{\\mid I \\mid}}}e^{- \\frac{1}{2}{({x\_{j} - \\mu\_{\\theta}{(z)}})}^{T}I{({x\_{j} - \\mu\_{\\theta}{(z)}})}}$inline-graphic style="height:2.1875em;" xlink:href="bk978-0-7503-6244-3ch5ieqn7.gif"/, where *θ* is a group of parameters of the decoder, and *x̂*[*j*] = *μ*[*θ*](*z*)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch5ieqn8.gif"/ is the output of the decoder. With the above information, the loss function of the VAE system can be written as the following equation (constants are ignored):

  
$$L \\leqslant \\sum\\limits\_{j = 1}^{n}{\\sum\\limits\_{i = 1}^{m}\\left( {\\mu\_{i,j}^{2} + \\sigma\_{i,j}^{2} - \\ln\\ \\left( \\sigma\_{i,j}^{2} \\right) - 1} \\right)} + \\frac{1}{2}\\sum\\limits\_{j = 1}^{n}{\\parallel {x\_{j} - {\\widehat{x}}\_{j}} \\parallel}^{2}$$  
(5.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch5eqn9.gif" position="float"/

If we can minimize the right hand side of equation ([5.3](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn3)), it is logical that we can minimize the left hand size of the equation, because the left hand side is equal to or less than the right hand side. The first part of the right hand side in equation ([5.3](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn3)) is called ‘regularization loss’, and the second part is called ‘reconstruction loss’. In the above tables and equations, we treated the latent *z* as a discrete variable. In fact, the latent *z* could be a continuous variable in a VAE system. We can also get the same result about the VAE loss function from the following mathematical derivations with ∫[*z*]*q*(*z*∣*x*[*j*])*d**z* = 1inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch5ieqn10.gif"/ and *D*[KL] ⩾ 0

  
$$L = - {\\ln\\ }\\left( {P\\left( X \\right)} \\right) = - {\\ln\\ }\\prod\\limits\_{j = 1}^{n}{p\\left( x\_{j} \\right)} = - \\sum\\limits\_{j = 1}^{n}\\left\\lbrack \\ln\\ \\left( { p\\left( x\_{j} \\right)} \\right)\\int\_{z}\\left. q(z\\mid x\_{j})\\mathit{dz} \\right\\rbrack \\right.$$  
graphic style="width:27.25em;" xlink:href="bk978-0-7503-6244-3ch5ueqn11.gif" position="float"/

  
$$L = - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( { p\\left( x\_{j} \\right)} \\right)\\mathit{dz}}} = - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( \\frac{ p\\left( {z,x\_{j}} \\right)}{p\\left( {z\\mid x\_{j}} \\right)} \\right)\\mathit{dz}}}$$  
graphic style="width:27.4375em;" xlink:href="bk978-0-7503-6244-3ch5ueqn12.gif" position="float"/

  
$$L = - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( {\\frac{ p\\left( {z,x\_{j}} \\right)}{q\\left( {z\\mid x\_{j}} \\right)}\\frac{q\\left( {z\\mid x\_{j}} \\right)}{p\\left( {z\\mid x\_{j}} \\right)}} \\right)\\mathit{dz}}}$$  
graphic style="width:18.5625em;" xlink:href="bk978-0-7503-6244-3ch5ueqn13.gif" position="float"/

  
$$L = - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( \\frac{ p\\left( {z,x\_{j}} \\right)}{q\\left( {z\\mid x\_{j}} \\right)} \\right)\\mathit{dz}}} - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( \\frac{q\\left( {z\\mid x\_{j}} \\right)}{p\\left( {z\\mid x\_{j}} \\right)} \\right)\\mathit{dz}}}$$  
graphic style="width:28.6875em;" xlink:href="bk978-0-7503-6244-3ch5ueqn14.gif" position="float"/

  
$$L = - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( \\frac{ p\\left( {z,x\_{j}} \\right)}{q\\left( {z\\mid x\_{j}} \\right)} \\right)\\mathit{dz}}} - \\sum\\limits\_{j = 1}^{n}{D\_{KL}\\left( {q(z\\mid x\_{j}){\\mid\\mid}p(z\\mid x\_{j})} \\right)}$$  
graphic style="width:27.0625em;" xlink:href="bk978-0-7503-6244-3ch5ueqn15.gif" position="float"/

  
$$L \\leqslant - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( \\frac{ p\\left( {x\_{j}\\mid z} \\right)p\\left( z \\right)}{q\\left( {z\\mid x\_{j}} \\right)} \\right)\\mathit{dz}}}$$  
graphic style="width:16.6875em;" xlink:href="bk978-0-7503-6244-3ch5ueqn16.gif" position="float"/

  
$$L \\leqslant \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( \\frac{q\\left( {z\\mid x\_{j}} \\right)}{p\\left( z \\right)} \\right)\\mathit{dz}}} - \\sum\\limits\_{j = 1}^{n}{\\int\_{z}{q(z\\mid x\_{j})\\ln\\ \\left( { p\\left( {x\_{j}\\mid z} \\right)} \\right)\\mathit{dz}}}$$  
graphic style="width:27.375em;" xlink:href="bk978-0-7503-6244-3ch5ueqn17.gif" position="float"/

  
$$L \\leqslant \\sum\\limits\_{j = 1}^{n}\\left( {D\_{KL}(q(z\\mid x\_{j}){\\mid\\mid}p{(z)}) - Ε\_{z \\sim q{({z\\mid x\_{j}})}}\\ \\ln\\ \\left( { p\\left( {x\_{j}\\mid z} \\right)} \\right)} \\right)$$  
graphic style="width:21.75em;" xlink:href="bk978-0-7503-6244-3ch5ueqn18.gif" position="float"/

This is an issue about the two parts of the loss function ([5.3](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn3)). The values of the two parts are not the same scale. Higgins and his colleagues in 2017 proposed a solution in their paper (Higgins *et al* [2017](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5bib1)) with a hyperparameter *β* to balance the contributions of the two parts of the loss function. They named the VAE with a modified loss function (equation ([5.4](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn4))) ‘beta-VAE’. If *β* = 1.0, we have a regular VAE system; if *β* > 1.0, the regularization loss (*D*[KL]) would quickly decrease to zero, and we would have the ‘model collapse’ issue for fake image generations in the following projects; if *β* = 0.0, our VAE system becomes an autoencoder system. Using bigger *β*, we would have very blurred fake images, but we would have more power to tune new fake images in different phases.

  
$$L = \\beta\\sum\\limits\_{j = 1}^{n}{\\sum\\limits\_{i = 1}^{m}\\left( {\\mu\_{i,j}^{2} + \\sigma\_{i,j}^{2} - \\ln\\ \\left( \\sigma\_{i,j}^{2} \\right) - 1} \\right)} + \\frac{1}{2}\\sum\\limits\_{j = 1}^{n}{{\\mid\\mid}x\_{j} - {\\widehat{x}}\_{j}\\mid\\mid^{2}}$$  
(5.4)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch5eqn19.gif" position="float"/

### 5.2 Application of beta-VAE for fake quadratic curves

In the following project [5.2.1](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5ueqn12) for generation of fake quadratic curves, only two fully connected layers are used in both the encoder model (*Q*) and the decoder model (*P*) of a beta-VAE system. In Cell 01, the hyperparameter *z\_dim* is set to be equal to 2 for convenience of data visualization. That means that each curve with 21 points is generated from a 2D latent vector. The decoder of the system will use two numbers sampled from a 2D Gaussian distribution to restore each curve with 21 points. The hyperparameter beta is set to be equal to 0.5 so we can balance the contributions of the two parts in the loss function. Noises are added to the quadratic curves (line 04 of Cell 02). In figure [5.1](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig1)(A), the 64 real curves are not smooth because of the noises. We do not have a dataset for the project. The data for model training is generated whenever we need a batch of data in a dataloader, and the batch number per epoch is set to be 5.

![Figure 5.1. (A) VAE information flow chart (real curves are outputs of Cell 03). (B and C) fake quadratic curves generated by a beta-VAE with β = 0.5 (outputs of Cell 07). Model training time is 9 min](images/bk978-0-7503-6244-3ch5f1_online.jpg)

**Figure 5.1.** (A) VAE information flow chart (real curves are outputs of Cell 03). (B and C) fake quadratic curves generated by a beta-VAE with *β* = 0.5 (outputs of Cell 07). Model training time is 9 min

The architecture of a VAE system is shown in figure [5.1](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig1)(A). Each real curve in a batch with noise was processed by the encoder model *Q* to obtain two vectors for a multivariate Gaussian distribution: a mean vector (*μ*) and a standard deviation vector (*σ*). Then a latent vector *z* is generated by *z* = *μ*+*σε* for each real curve, where *ε* is a random number generated from a standard multivariate normal distribution *N*(0,I). In the following project codes, you will see a trick which shows how to calculate the standard deviation vector (*σ*) in which each element must be a positive number. The decoder's model P uses a batch of the latent vectors *Z* to generate a batch of fake images (*X̂*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch5ieqn20.gif"/). Those fake curves shown in figure [5.1](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig1)(A) are very noisy at the beginning of model training. Then at epoch 20 000, noises are filtered out and the fake curves shown in figure [5.1](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig1)(C) are smooth.

![](images/bk978-0-7503-6244-3ch5uf1_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf2_pr.gif)

 

The encoder class defined in Cell 04 uses a batch of real curves as its input which is processed by a fully connected layer. The encoder outputs a latent vector *z*, a mean (*μ*) tensor, and a log variance (ln  (*σ*²)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch5ieqn21.gif"/) tensor. The latent vector z is sampled from a normal distribution *N*(*μ*,*σ*²) by *z* = *μ* + *σ*ε, where ε is a random number generated by a standard normal distribution ∼*N*(0,I). This is the trick to calculate standard deviations (std) which must be positive numbers. From the log variance, we can get the standard deviation by $\\sigma = \\sqrt{e^{\\ln\\ {(\\sigma^{2})}}}$inline-graphic style="height:1.5em;" xlink:href="bk978-0-7503-6244-3ch5ieqn22.gif"/. The decoder P defined in Cell 05 has two fully connected layers as usual. It uses a batch of latent vectors as its input. The output of the decoder is a batch of fake curves. According to equation ([5.4](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn4)), the loss function is defined in Cell 06. If the two parts in the loss function are calculated with ‘mean’ instead of ‘sum’, we have to adjust the *β* value to be around 0.01. The Adam optimizer is used for model training. The training function defined in Cell 07 uses a pandas dataframe to record loss values during model training. In each epoch, five batches of real curves are generated for model training. Each batch of the training data is processed by the encoder model Q. The output *z* of model Q is the input of model P to generate fake curves. Then loss values are calculated, and the parameters of the two models are updated by the Adam optimizer. Loss function curves are shown in figure [5.2](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig2)(A).

![](images/bk978-0-7503-6244-3ch5uf3_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf4_pr.gif)

![Figure 5.2. Model training history and applications of trained models to generate fake curves from latent vectors. (A) Total-loss, Dkl loss and reconstruction loss curves (outputs of Cell 08). (B) Distribution of latent vectors in a 2D latent space (outputs of Cell 09). (C) Fake curves generated from latent vectors (z = \[−2, 0\], z = \[2, 0\], z = \[−2, 15\]) by mode P (outputs of Cell 10).](images/bk978-0-7503-6244-3ch5f2_online.jpg)

**Figure 5.2.** Model training history and applications of trained models to generate fake curves from latent vectors. (A) Total-loss, D[kl] loss and reconstruction loss curves (outputs of Cell 08). (B) Distribution of latent vectors in a 2D latent space (outputs of Cell 09). (C) Fake curves generated from latent vectors (*z* = \[−2, 0\], *z* = \[2, 0\], *z* = \[−2, 15\]) by mode P (outputs of Cell 10).

Codes in Cell 09 calculate the trained Q's outputs with five batches of training data for mu, std and *z*. The latent vectors (*z*) are then plotted in figure [5.2](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig2)(B), and their distribution pattern follows a 2D standard normal distribution function. If *β* = 4.0, each element of the mu array is very close to 0.0, and each element of the std array is very close to 1.0. If *β* = 0.0, the dots in figure [5.2](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig2)(B) are in a straight line, and each element of the std vectors is very close to zero. The hyperparameter *β* can be used to compress the latent vectors into an area following a standard normal distribution. That is the job of the autoencoder network. In figure [5.2](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig2)(B), coordinates of two latent vectors marked by ⊗ and ⊕ are \[−2,0\] and \[2,0\] respectively. From them, two smooth fake curves were generated by the decoder P, and are shown in figure [5.2](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig2)(C). The value *z*\[0\] of a latent vector can be used to tune vertical positions of fake curves. The value of *z*\[1\] gives us power to adjust the smoothness of fake curves. The zig-zag fake curve in figure [5.2](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig2)(C) was generated with a latent vector *z* = \[−2, 15\]. Every time you run the codes of the project, the controllers for fake curves would be different. Sometimes, value of *z*\[1\] could control the positions of fake curves on the *y*\-axis.

### 5.3 Application of beta-VAE for the MNIST dataset

The beta-VAE architecture for the MNIST project to generate fake images is almost the same as that one in the last section for fake quadratic curve generation. The main difference is the usage of deep convolution networks for the encoder Q and the decoder P. We know that neural networks with two fully connected layers are not powerful enough to handle MNIST images. The real and fake MNIST images (figure [5.3](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig3)(B)) generated by codes in project [5.3.1](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5ueqn16) should be the same. We can see that fake MNIST images are blurry and some digits are wrong. These issues were caused by the setting of *z\_dim* = 2 in Cell 02 for data visualization. When an MNIST image was compressed by the encoder from 784 pixels into a latent vector with only two elements, a fraction of information was lost, so the decoder could not correctly restore the original image information. Figure [5.4](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig4) shows other training results: a 2D latent space with points of latent vectors, loss curves and fake images generated by *p*(*x*∣*z*) with *z*\[0\]∈\[−10,10\] and *z*\[1\]∈\[−10,10\]. By tuning the *β* value from 0 to 10, you could see that the points in the latent space would be compressed from a big irregular area into a round area with a radius of about three. Our models could really be trained to force *q*(*z*∣*x*) into *N*(0, I) by a big value of *β*, but fake digital images generated by *p*(*x*∣*z*) would be too blurry to read. We need the power of Kullback–Leibler divergence in model training, but not too much. Changing *z\_dim* from 2 to 20 in Cell 01, we would get crystal clear fake MNIST images, but the latent space in figure [5.4](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig4)(A) cannot be shown. Using VAE, we are able to generate the desired fake images without label information from image datasets.

![](images/bk978-0-7503-6244-3ch5uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf6_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf7_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf8_pr.gif)

![Figure 5.3. (A) Real MNIST images. (B) Fake MNIST images generated by β-VAE with z\_dim = 2 and β = 0.01. These images are blurry and some digits are wrong. If z\_dim = 20, fake images are as good as real images, and there are no digital mistakes. Model training time is 9 min. The MNIST image dataset is from Deng (2012) with a license CC BY 3.0.](images/bk978-0-7503-6244-3ch5f3_online.jpg)

**Figure 5.3.** (A) Real MNIST images. (B) Fake MNIST images generated by *β*\-VAE with z\_dim = 2 and *β* = 0.01. These images are blurry and some digits are wrong. If z\_dim = 20, fake images are as good as real images, and there are no digital mistakes. Model training time is 9 min. The MNIST image dataset is from Deng ([2012](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5bib4)) with a license CC BY 3.0.

![Figure 5.4. Model training results of a beta-VAE with β = 0.01. (A) 2D latent space: the output of Cell 12. (B) Loss curves: the output of Cell 09 (total-loss, regularization loss Dkl and reconstruction loss MSE). (C) Fake images generated by p(x∣z): the output of cell 13 with −10⩽z\[0\]⩽10 and −10⩽z\[1\]⩽10.](images/bk978-0-7503-6244-3ch5f4_online.jpg)

**Figure 5.4.** Model training results of a beta-VAE with *β* = 0.01. (A) 2D latent space: the output of Cell 12. (B) Loss curves: the output of Cell 09 (total-loss, regularization loss *D*[kl] and reconstruction loss MSE). (C) Fake images generated by p(x∣z): the output of cell 13 with −10⩽*z*\[0\]⩽10 and −10⩽*z*\[1\]⩽10.

### 5.4 Using VAE-GAN for MNIST, Fashion MNIST & Anime-Face Dataset

Compares with GANs, VAE systems are easy to train. They can automatically find characteristics of images in datasets without labels. Those characteristics of images in a latent space with low dimensions can be tuned to generate new images. However, the quality of fake images generated by a VAE system is usually not as good as the quality of those generated by a GAN. The issue is caused by the VAE's reconstruction loss function based on element-wise errors, the second part of equation ([5.3](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn3)). For example, if pixels of an MNIST image are horizontally shifted one pixel to the left, the VAE's reconstruction loss values would be huge, but to our eyes there is no difference between the original image and shifted image. In 2016, Larsen and his colleagues published a paper (Larsen *et al* [2016](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5bib3)) titled ‘Autoencoding beyond pixels using a learned similarity metric’. With a hybridization of VAE and GAN, they ‘replace element-wise errors with feature-wise errors to better capture data distributions while offering invariance towards, e.g. translation.’ A VAE-GAN system is a generative model that combines the two popular generative systems: a VAE system and a GAN system. The VAE component of the system is used to learn a compact, continuous representation of a dataset, while the GAN component is used to generate new, synthetic data instances. Using the strengths of the two systems, VAE-GANs are able to generate high-quality fake images while also learning a compact, continuous representation of datasets. This makes VAE-GANs are useful in many areas, such as image synthesis, unsupervised representation learning, and data generation for deep reinforcement learning.

In the VAE-GAN system shown in figure [5.5](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig5), there are three models: an encoder model Q, a decoder model P and a discriminator model D. The first two models belong to a VAE system. The decoder also works as a generator for the GAN system which has the discriminator model D. Each real image (*x*) in a batch of a dataloader *X* is processed by the encoder Q to create a multivariate normal distribution *q*(*z*∣*x*) in a latent space with dimensions of *z\_dim*. Then by sampling from those multivariate normal distributions, a batch of latent vectors (*Z*) is generated as an input of the decoder *P*, which restores the batch of latent vectors *Z* to a batch of fake images (*X̃*inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch5ieqn23.gif"/) in the real image space, and the discriminator model D compresses each of the fake images into a scalar in range \[0,1\] as usual. The batch of real images can also be directly processed by model D as shown by the longest arrow in figure [5.5](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig5). A batch of noise (*Z*[p]) sampled from a multivariate standard normal distribution *N*(0,*I*) is processed by *P* and *D*. The model D's three scalar batches are used to calculate loss values (*L*[GAN]) with a BCE loss function

  
*L*[*G**A**N*] = ln  (*D*(*X*))  + ln  (1−*D*(*X̃*))  + ln  (1−*D*(*X*[*p*]))  
(5.5)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch5eqn24.gif" position="float"/

The VAE-GAN's model D does one more job than an ordinary GAN's model D. From a neural layer just before the last layer of the model D, the VAE-GAN's model D outputs two batches of vectors. The dimensions of each vector in a batch could be in thousands. A batch of vectors (*V*[*X*]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch5ieqn25.gif"/) from real images and a batch of vectors (*V*[*X̃*]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch5ieqn26.gif"/) from fake images are used to replace real images and fake images in the reconstruction loss function of a VAE system. This modified reconstruction loss function has the name *L*[*l**l**i**k**e*]^(*D**i**s*[*l*])inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn27.gif"/ according to the VAE-GAN paper, and it is a part of the decoder's loss function and also a part of the encoder's loss function. The *L*[prior] in equation ([5.7](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn7)) is the Kullback–Leibler divergence between the *q*(*Z*∣*X*) and the multivariate standard normal distribution *N*(0,*I*)

  
*L*[*P*]\= *L*[*l**l**i**k**e*]^(*D**i**s*[*l*]) − *L*[*G**A**N*] = *M**S**E**L**o**s**s*(*V*[*X*],*V*[*X̃*]) − *L*[*G**A**N*]  
(5.6)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch5eqn28.gif" position="float"/

  
*L*[*Q*]\= *L*[*l**l**i**k**e*]^(*D**i**s*[*l*]) + *L*[*p**r**i**o**r*] = *M**S**E**L**o**s**s*(*V*[*X*], *V*[*X̃*]) + *D*[*K**L*](*q*(*Z* ∣ *X*) ∣ ∣*p*(*Z*))  
(5.7)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch5eqn29.gif" position="float"/

Mode D, P and Q are trained with their own loss functions. The values of the three models’ loss functions are not to the same scale, especially if those values are calculated with summation in each batch. Many people calculate the values of the three loss functions by summation with average loss in each batch, and use *L*[*P*] = *γ**L*[*l**l**i**k**e*]^(*D**i**s*[*l*]) − *L*[*G**A**N*]inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn30.gif"/ and/or *L*[*Q*] = 5*L*[*l**l**i**k**e*]^(*D**i**s*[*l*]) + *L*[*p**r**i**o**r*]inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn31.gif"/ to balance those loss values, where *γ* = 15 or 25. In the following VAE-GAN project, loss function values are calculated with summation of each batch. Because values of *L*[GAN] and *L*[prior] are very small compared with *L*[*l**l**i**k**e*]^(*D**i**s*[*l*])inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn32.gif"/, the hyperparameter *γ* in front of *L*[*l**l**i**k**e*]^(*D**i**s*[*l*])inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn33.gif"/is set to be 1.0. The latent dimension is set to be two by z\_dim = 2, so that we can show the latent space in figure [5.7](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig7)(A). During model training in every five epochs, Cell 11 will output a batch of real images and a batch of fake images as shown in figure [5.6](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig6).

![](images/bk978-0-7503-6244-3ch5uf9_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf10_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf11_pr.gif)

![Figure 5.5. A VAE-GAN's architecture and its information flow chart with three models: an encoder Q, a decoder P and a discriminator D. Each quadric curve represents a real sample (x) in a batch (X) of a dataloader.](images/bk978-0-7503-6244-3ch5f5_online.jpg)

**Figure 5.5.** A VAE-GAN's architecture and its information flow chart with three models: an encoder Q, a decoder P and a discriminator D. Each quadric curve represents a real sample (x) in a batch (X) of a dataloader.

![Figure 5.6. (A and B) Real MNIST images (outputs of Cell 11). (C and D) Fake MNIST images generated by VAE-GAN with z\_dim = 2 and 20 respectively. (C) is noisy with wrong digits comparing with (A), and the fake images in (D) are as good as the real images in (B) without digital mistakes. Model training time is 36 min. The real images were reproduced from MNIST dataset of Deng (2012) with a license CC BY 3.0.](images/bk978-0-7503-6244-3ch5f6_online.jpg)

**Figure 5.6.** (A and B) Real MNIST images (outputs of Cell 11). (C and D) Fake MNIST images generated by VAE-GAN with z\_dim = 2 and 20 respectively. (C) is noisy with wrong digits comparing with (A), and the fake images in (D) are as good as the real images in (B) without digital mistakes. Model training time is 36 min. The real images were reproduced from MNIST dataset of Deng ([2012](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5bib4)) with a license CC BY 3.0.

![Figure 5.7. VAE\_GAN model training results. (A) 2D latent space: the output of Cell 14. (B) Curves of loss functions: the output of Cell 12. (C) Fake images generated by p(x∣z): the output of Cell 15 with −10⩽z\[0\]⩽10 and −10⩽z\[1\]⩽10.](images/bk978-0-7503-6244-3ch5f7_online.jpg)

**Figure 5.7.** VAE\_GAN model training results. (A) 2D latent space: the output of Cell 14. (B) Curves of loss functions: the output of Cell 12. (C) Fake images generated by *p*(*x*∣*z*): the output of Cell 15 with −10⩽z\[0\]⩽10 and −10⩽z\[1\]⩽10.

The discriminator D in Cell 07 is a little different from a GAN's model D in section [3.2.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-2-2). It has two outputs. One output is a batch of scalars in the range \[0,1\] as usual; another output is a batch of vectors from layer 04, and each vector has 1024 elements. The second output is used to replace images (real or fake) for reconstruction loss calculations. The higher the vector's element number is, the longer the time needed for model training, and the better the quality of fake images will be. Since we are using GAN again, we meet the same issue about choosing learning rates to balance the smartness between an image generator and an image discriminator. In Cell 01, an initial learning rate (lr) was set to be 10^(−3) for all three models. Model Q and P use the same learning rate. In model training for GANs, we usually use a smaller learning rate for model D. But in VAE-GAN we have to use a bigger learning rate (10 × lr) for model D to make the fake images sharper (line 05 of Cell 09).

![](images/bk978-0-7503-6244-3ch5uf12a_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf12b_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf13a_pr.gif)

![](images/bk978-0-7503-6244-3ch5uf13b_pr.gif)

 

Codes in Cell 11 are used to train the three models. A pandas dataframe with three columns records loss function values of model Q, P and D during training. Since D\_loss values are smaller comparing with values of Q\_loss and P\_loss, D\_loss values are multiplied by 100 just for plotting in figure [5.7](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig7)(B). There are four parts in Cell 11. Part one to three are used to train model D, P and Q, respectively. The last part is for recording and showing training results. During model training, two loss functions defined in Cell 10 would be called. A loss function named ‘loss\_gan’ is for the *L*[GAN]. There are three items in *L*[GAN]: loss\_real, loss\_fake and loss\_noises. Their calculations are based on BCE loss function as usual in GAN projects. The loss function named ‘loss\_rec’ is a modified reconstruction loss function *L*[*l**l**i**k**e*]^(*D**i**s*[*l*])inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn34.gif"/ according to equation ([5.6](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5eqn6)). This loss function has two inputs: one is a batch of real images, and the other is a batch of latent vectors of the real images. The two batches of data are processed by model D to output two batches of vectors, respectively. Then the two batches of vectors are used as the inputs of *L*[*l**l**i**k**e*]^(*D**i**s*[*l*])inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch5ieqn35.gif"/. Model training results are shown in figure [5.7](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig7). Comparing this with figure [5.4](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig4), you can see those digits in the 2D latent space are disentangled more.

The MNIST dataset is the simplest dataset widely used in computer vision projects. If your codes work for the dataset, it does not mean that your codes are functional for other datasets. By choosing the latent space dimensions to be 20, we can generate crystal clear fake MNIST images. Just change the dataset name from MNIST to Fashion MNIST, the results would be very different. Even z\_dim was set to be equal to 256, detailed patterns, such as Nike's trademark ‘√’ on shoes, ‘N.Y.’ on t-shirt could not be found on fake Fashion MNIST images. On the right hand side of a real image shown in figure [5.8](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig8)(A), there is a black square block which was blurred in a fake image at the same position.

![Figure 5.8. (A) Real fashion MNIST images. (B) Fake fashion MNIST images generated by VAE\_GAN with z\_dim = 256. Detailed patterns on real images were lost or blurred on the fake images. The Fashion MNIST dataset is from Xiao et al (2017) with a license CC BY 3.0.](images/bk978-0-7503-6244-3ch5f8_online.jpg)

**Figure 5.8.** (A) Real fashion MNIST images. (B) Fake fashion MNIST images generated by VAE\_GAN with z\_dim = 256. Detailed patterns on real images were lost or blurred on the fake images. The Fashion MNIST dataset is from Xiao *et al* ([2017](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5bib5)) with a license CC BY 3.0.

VAE-GANs were successfully applied to datasets with black and white images of lower resolutions. We need to see how VAE-GANs handle color image datasets. Codes in appendix [D](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-D) are used to generate color fake anime-faces dataset images. Because the image resolution of the Anime-face Dataset is higher, more neural layers are used in the three models of the VAE-GAN system. The model training time for each epoch is about 8 min on my laptop. With a batch size set of 64 and the training epoch number of 25, the model training time is about 210 min. Although the model training time is longer, we do save time because it is not necessary to waste time tuning hyperparameters for high-quality fake images. The quality of fake images shown figure [5.9](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5fig9) is not as good as the quality of real anime-face dataset images, but is good enough. Using Kaggle’s free GPU P100, the model training time is about 90 min.

![Figure 5.9. Fake anime-face dataset images generated VAE\_GAN codes with z\_dim = 128, lr = 1e-4 and epochs = 25.](images/bk978-0-7503-6244-3ch5f9_online.jpg)

**Figure 5.9.** Fake anime-face dataset images generated VAE\_GAN codes with z\_dim = 128, lr = 1e-4 and epochs = 25.

### References

Deng L 2012 The MNIST database of handwritten digit images for machine learning research *IEEE Signal Process. Mag.* **29** 141–1

Higgins I, Matthey L, Pal A, Burgess C P, Glorot X, Botvinick M M, Mohamed S and Lerchner A 2017 *beta-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework* (ICLR)

Kingma D P and Welling M 2013 Auto-encoding variational bayes. *arXiv preprint arXiv:*[1312.6114](http://arxiv.org/abs/1312.6114)

Larsen A B L, Sønderby S K, Larochelle H and Winther O 2016 Autoencoding beyond pixels using a learned similarity metric *Int. Conf. on Machine Learning* (PMLR) pp 1558–66

Xiao H, Rasul K and Vollgraf R M 2017 Fashion-MNIST: a novel image dataset for benchmarking machine learning algorithms [https://github.com/zalandoresearch/fashion-mnist](https://github.com/zalandoresearch/fashion-mnist)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 6

## Image generation by infoGANs

An information maximizing generative adversarial net (infoGAN) is also an unsupervised computer vision technique with which we can generate specific style images, similar to images in training datasets, without using labels. The quadratic curve dataset is used to explain the infoGAN principle at first, and then this technique is used for the MNIST, Anime-face and Rock Paper Scissors datasets.

Although it is important to randomly generate realistic fake images with vanilla GANs, it is more important to use conditional GANs to generate desired fake images. Since conditional GANs can encode label information with images in datasets, they have the ability to generate specific images with labels pre-set by ourselves. Unfortunately, many datasets are not labeled, because dataset labeling is very expensive. What can we do for unsupervised learning? Using variational autoencoders is a solution to generate desired fake images for datasets without labels. However, fake images generated by VAE systems are usually blurry, not crystal clear. In 2016, Xi Chen and his collaborators published a paper (Chen *et al* [2016](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6bib1)) titled ‘InfoGAN: Interpretable representation learning by information maximizing generative adversarial nets’. With an infoGAN system, our codes are smart enough to automatically find different characteristics of images in datasets during model training, and enable us to change some parameters linked with those characteristics, so we can generate fake images with desired classes and effects.

### 6.1 Using infoGAN to generate quadratic curves

In the infoGAN architecture shown in figure [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig1)(A), there are four models: model G, model D0, model D1 and model Q. The first one is the generator model G which has the same structure as a generator model in an ordinary GAN. The last one is an ‘auxiliary model’ Q. D0 and D1 are two parts of the discriminator model D of a GAN in section [3.1.1](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-1-1). There are two fully connected layers in the model D. Its last neural layer is taken away to construct model D1, and another neuron layer is used for model D0. The outputs of model D0 are shared by model D1 and model Q. The three outputs of model Q are named ‘logits’, ‘mu’ and ‘var’. The input of model G in the GAN of section 3.11 is a batch of noise vectors generated by a multivariate standard normal distribution, and each noise vector is represented by a lowercase letter *z* with *z\_dim* elements. In the infoGAN system, we use a capital letter *Z* to represent a noise vector for model G's input. The vector *Z* is a concatenation result of an incompressible noise vector, a label vector and a style vector. The incompressible noise vector is the noise vector (*z*) in a GAN system, and we cannot tune them to get any desired effect for fake images. The elements of the label vector are discrete numbers (integers) in a uniform distribution for the quadratic curve project. The element in the style vector is a continuous number uniformly distributed in the range \[−1,1\] for the quadratic curve project. In the infoGAN paper, the concatenation of the last two vectors is called latent code c with elements named c[1], c[2], …c[L]. The element number of the incompressible noise vector, the element number of labels and the element number of styles for the simple project were arbitrarily chosen as *z\_dim* = 13, *n\_class* = 2 and *n\_styles* = 1, respectively. As shown in figure [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig1)(A), the noise vector *Z*'s dimensional number is *Z\_dim* = (13 + 2 + 1). Each batch of *Z* vectors is generated by a function defined in Cell 09 of Project 6.1.

![Figure 6.1. (A) The four models and information flow of an infoGAN. (B) Fake curves at epoch = 2000. (C) Fake curves at epoch = 20 000. (D) Loss curves for model D and G. (E) Loss curves for model Q's outputs. (F) A fake curve generated with Z\[:,13\] = 0, Z\[:,14\] = 1 and Z\[:,15\] = −0.1. Model training time is 21 min.](images/bk978-0-7503-6244-3ch6f1_online.jpg)

**Figure 6.1.** (A) The four models and information flow of an infoGAN. (B) Fake curves at epoch = 2000. (C) Fake curves at epoch = 20 000. (D) Loss curves for model D and G. (E) Loss curves for model Q's outputs. (F) A fake curve generated with *Z*\[:,13\] = 0, *Z*\[:,14\] = 1 and *Z*\[:,15\] = −0.1. Model training time is 21 min.

We do the extra work described above to obtain desired fake curves or images. Just for another example of the MNIST dataset without using its label information, we want to use infoGAN to generate desired fake digital images. In that case, the number of the label vector is set to be *n\_class* = 10 for its 10 classes, and *n\_styles* = 2 for two image styles. Since each MNIST image has 28 × 28 pixels, we choose *z\_dim* = 62 for the element number of an incompressible noise vector *z*. For the simple quadratic curve project, each curve has 21 numbers, so we could set *z\_dim* = 13. We really have no information about labels and styles of those quadratic curves, and want to see what an infoGAN can learn from data of quadratic curves with *n\_class* = 2 and *n\_styles* = 1. Based on the infoGAN paper, the latent code name ‘c’ is used to denote the concatenation of all latent variables c[1], c[2] and c[3] for the quadratic curve project. We can use a factored probability distribution for the latent code

  
$$P(c\_{1},c\_{2},\\ldots,c\_{L}) = \\prod\\limits\_{i = 1}^{L = 3}{p(c\_{i}})$$  
(6.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch6eqn1.gif" position="float"/

Each batch of noise vectors (*Z*) is used by model G to generate a batch of fake images as shown in figure [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig1)(C). Model D0 uses a batch of fake curves or a batch of real curves as its input. The output of D0 is a *m* × *n\_hidden* tensor, where *m* = batch size and *n\_hidden* = 128. This output is shared by model D1 and model Q. Model D1 is trained to ensure that the fake images have good quality comparing with real images by using the following BCE loss function *L*[*D1*] which is the same of an ordinary GAN

  
$$L\_{D1} = \\frac{- 1}{m}\\sum\\limits\_{i = 1}^{m}{\\ \\ln\\ \\left\\lbrack {D1\\left( {D0\\left( x\_{i} \\right)} \\right)} \\right\\rbrack} - \\frac{1}{m}\\sum\\limits\_{i = 1}^{m}{\\ \\ln\\ \\left\\lbrack {1 - D1\\left( {D0\\left( {\\widetilde{x}}\_{i} \\right)} \\right)} \\right\\rbrack}$$  
(6.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch6eqn2.gif" position="float"/

 

The output tensor of model D0 is also used by model Q which has three outputs: a *m* × 2 logits tensor, a *m* × 1 mean tensor *μ*, and a *m* × 1 variance tensor *σ*². There are three parts in the loss function *L*[*G*] shown in the following equation ([6.3](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6eqn3)). The first part is a BCE loss function with which model G is trained to generate fake images as good as real images to fool model D1; the second part is a cross-entropy loss function about labels in the latent code and the logits of model Q's output; the third part is a Gaussian negative log-likelihood loss function which establishes a mathematical link between a batch of c[3] in *Z* vectors and model Q's two outputs (*μ* and *σ*²). As the infoGAN paper mentioned, a hyperparameter λ in equation ([6.3](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6eqn3)) should be a small number, because the loss function values from the style variable may be very big. A mathematical link between fake images and the latent code is the mutual information *I*(*c*, *G*(*z*, *c*))inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch6ieqn3.gif"/ mentioned in section 2.1.3. We can use the link just like a dial to tune model G to generate fake images with desired effects

  
$$L\_{G} = \\frac{- 1}{m}\\sum\\limits\_{i = 1}^{m}{\\ \\ln\\ \\left\\lbrack {D1\\left( {D0\\left( {\\widetilde{x}}\_{i} \\right)} \\right)} \\right\\rbrack} + {Cross}E\_{Loss}\\left( {\\text{logits},{labels}} \\right) + \\frac{\\lambda}{2m}\\sum\\limits\_{i = 1}^{m}\\left( {\\ln\\ \\sigma\_{i}^{2} + \\frac{\\left( {\\left( c\_{3} \\right)\_{i} - \\mu\_{i}} \\right)^{2}}{\\sigma\_{i}^{2}}} \\right)$$  
(6.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch6eqn4.gif" position="float"/

In the gambling machine mentioned in chapter [1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1), section 1.1.3, a fair coin and a fair dice are independent, so their mutual information is equal to zero. We cannot predict the coin's side from the digit of a dice tossed on a table. To use the latent code to tune the fake images with the desired effects, we should maximize the mutual information between the latent code c and the fake images: *I*(*c*,*G*(*z*,*c*)) = *H*(*c*)−*H*(c∣*G*(*z*,*c*)) according to equation ([1.18](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn18)). We know the PDF of c from equation ([6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6eqn1)), so we can calculate to find its entropy *H*(*c*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch6ieqn5.gif"/. But we do not know the PDF of fake images *G*(*z*,*c*), and it is impossible to directly calculate *I*(*c*,*G*(*z*,*c*)). By introducing the auxiliary model Q, the authors of the infoGAN paper circumvented the problem, and they found the low bound of the mutual information: *L*[*I*](*G*,*Q*)

  
*I*(*c*,*G*(*z*,*c*)) ≥ *L*[*I*](*G*,*Q*) = *E*[*x* ∼ *G*(*z*, *c*)]\[*E*[*c*′ ∼ *P*(*c*, ∼,*x*)]\[ln \[*Q*(*c*′,∼,*x*)\]\]\] + *H*(*c*)  
(6.4)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch6eqn6.gif" position="float"/

It is logical that you can maximize the mutual information by maximizing its low bound. With the gradient descent algorithm, we need to find the minimum of the negative of the low bound. That is why the Gaussian negative log-likelihood loss function is used in model G's loss function ([6.3](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6eqn3)). In the codes of the following infoGAN project 6.1 for the quadric curve project, most hyperparameters and all libraries are listed in Cell 01. As usual, Cell 02 generates data, and Cell 03 uses those data to draw real quadric curves. Figure [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig1)(B) and (C) show fake curves generated by the infoGAN codes. Values of model D1's loss function is very close to its theory numbers. But model G's loss curve is very noisy. These noises come from the Gaussian negative log-likelihood loss ‘loss\_con’ shown in figure [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig1)(E). The hyperparameter ‘lambda\_info’ is used to limit contribution of ‘loss\_con’ to model G's loss.

![](images/bk978-0-7503-6244-3ch6uf1_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf2_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf3_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf4_pr.gif)

 

In Cell 09, the noise tensor generator function named ‘noise4G\_input’ is new to us. It generates three random tensors and concatenates them into a *m* × 16 tensor Z which is the first output of the function. This tensor will be used to generate a batch of fake curves. The other two outputs (‘labels’ and ‘con\_c’) of this function will be updated during model training and can be used to tune those fake images for our desired effects. The ‘train\_D1’ function in Cell 10 is as usual in an ordinary GAN. In Cell 11 about a function named ‘train\_G’, the loss function has three parts. The first part is BCE loss used to fool model D1; the second part is the cross-entropy loss used to establish links between the logits output of model Q and latent labels; the third part is Gaussian negative log-likelihood loss. It is used to insure the styles in the latent code with a normal distribution *N*(c[3]; mu, *σ*²), where *mu* and *var* = *σ*² are two outputs of model Q. We use a class of Pytorch named ‘nn.GaussianNLLLoss’ to calculate of the loss values.

Codes from Cell 12 to 14 are used to train models and display the model training results. After model training, a single fake curve is generated which is shown in figure [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig1)(F). Its data was generated by *Z* = *torch.randn(1, Z\_dim)* and then set by *Z*\[:,13\] = 0, *Z*\[:,14\] = 1 and *Z*\[:,15\] = −0.1. With label code c[1] = 0 and c[2] = 1, the infoGAN system generates a fake curve whose lowest point is below *y* = 0.5; and with label c[1] = 1 and c[2] = 0, the infoGAN system generates a fake curve whose lowest point is above *y* = 0.5. The style variable c[3] can be used to tune the lowest point of a fake curve moving along the *y*\-axis continuously. If |c[3]| is too big (≫1), the fake curve will not be smooth. The extra work based on infoGAN theory gives us the power to tune fake images without label information in datasets.

### 6.2 Implementation of infoGAN for the MNIST dataset

With the knowledge about the DCGAN MNIST project in section [3.2.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-2-2) and the infoGAN structure about fake quadratic curve generation in the last section, it should be easy for us to understand the following codes in project 6.2.1 about using an infoGAN to generate fake MNIST images. What we should pay attention to is the parameter ‘k’ in Cell 01. It is the ratio between the learning rate of model G and that of model D1. In the infoGAN paper, it was set to be 5. As mentioned in section [3.2.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-2-2), we know that model G is not as smart as model D. We should use a bigger number (*k* = 25) for the ratio so the two models have the same intelligence to compete with each other. It took a long time to adjust both the initial learning rate (*lr*) and the ratio (*k*) to generate high quality fake images shown in figure [6.2](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig2)(A) which are outputs of Cell 15. These fake images are crystal clear and could not be distinguished from real images output by Cell 04. Each column of those fake images has the same digits. This means that our infoGAN algorithm works.

![Figure 6.2. (A) Fake MNIST images generated by an infoGAN at the end of model training, outputs of Cell 15. (B and C) Curves of Loss functions, the outputs of Cell 16 about the model training history (model training time: 21 min).](images/bk978-0-7503-6244-3ch6f2_online.jpg)

**Figure 6.2.** (A) Fake MNIST images generated by an infoGAN at the end of model training, outputs of Cell 15. (B and C) Curves of Loss functions, the outputs of Cell 16 about the model training history (model training time: 21 min).

![](images/bk978-0-7503-6244-3ch6uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf6_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf7_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf8_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf9_pr.gif)

 

With codes in Cell 12 to generate noise tensors for fake images, we use integer numbers from 0 to 9 as labels in the latent code to generate fake images. Each column of those fake images in figure [6.2](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig2)(A) has the same latent digital label. From left to right in figure [6.2](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig2)(A), the latent code labels on each row are 0, 1, …, 9. However, real labels of real images of each row are 1, 7, 3, 4, 6, 9, 8, 0, 5, 2, respectively. From the figure, we see that the latent code labels (0, 1…,9) are not the real labels of images in the MNIST dataset. After running codes from Cell 01 to 15, the models are trained. Then using the instructions of the infoGAN paper and with many tests, the following table [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6t1) was obtained to tune the fake images for desired results. Using Cell 17, we can generate fake images shown in figure [6.3](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig3)(A) with digits sorted from low to high in rows. The two continuous style variables in the latent code could be used to tune the image stride width and digit angles of fake images, respectively. Every time you run the codes of the project, the function of each element of the latent code to tune fake images is different.

**Table 6.1.** Latent code for tuning fake MNIST images.

| Latent code || c[1] || c[2] || c[3] || c[4] || c[5] || c[6] || c[7] || c[8] || c[9] || c[10] || c[11] || c[12] |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **MNIST label** || 1 || 7 || 3 || 4 || 6 || 9 || 8 || 0 || 5 || 2 || Angle || Width |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Z: noise for G** || Z[64] || Z[68] || Z[62] || Z[66] || Z[67] || Z[65] || Z[70] || Z[71] || Z[63] || Z[69] || Z[72] || Z[73] |

![Figure 6.3. By tuning latent code c1 to c12 to get desired fake MNIST images with codes in Cell 17. (A) Normal fake images in rows sorted from 0 to 9 by changing latent code label sequence with codes in Cell 17. (B) c11 = 1.5, tuning the stride width of fake images by codes in Cell 18. (C) c12 = −1.5, tuning the digital angles of fake images by codes in Cell 19.](images/bk978-0-7503-6244-3ch6f3_online.jpg)

**Figure 6.3.** By tuning latent code c1 to c12 to get desired fake MNIST images with codes in Cell 17. (A) Normal fake images in rows sorted from 0 to 9 by changing latent code label sequence with codes in Cell 17. (B) *c*[11] = 1.5, tuning the stride width of fake images by codes in Cell 18. (C) *c*[12] = −1.5, tuning the digital angles of fake images by codes in Cell 19.

In Cell 17, a list named ‘c’ is used to establish links between MNIST labels and their latent code shown in table [6.1](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6t1). The list was obtained by reading digits from left to right in any row of figure [6.2](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig2)(A). Then the noise generator in Cell 12 generated a 100 × 74 × 1 × 1 tensor Z. From column 62 to column 71, each element in these 10 columns is reset to zero. With a for-loop for every 10 rows of the tensor Z, the value of an element in a column is set to be one, and the column index is obtained according to table 6.1. For example, from row 0 to 9 at the beginning, each element of the noise tensor Z at column 71 is set to be one. All 10 fake images of the first 10 rows of the tensor are digital zero images. The *show\_imgs* function in Cell 04 display the 100 fake digital images of the tensor as a bigger image with those same 10 digits on each row. In this way, we can choose which digit should be in a row. We can also change the display angles and stride widths of those images with Z\[:,−2\] and Z\[:,−1\], respectively. Although the value of each element in the last two columns (Z[72], Z[73]) can be any real number, fake digital images are readable only if they are in the range \[−2,2\],

I have to admit that there is a cheat in the project. Ten integers were chosen for the latent code for labels because we know there are 10 classes in the MNIST dataset. If we do not have MNIST label information, and choose five digitals or 20 digitals for the latent code label, what will happen? If you change the variable ‘n\_class’ in Cell 01 to five, you will find that there will be more than one digit in each column of figure [6.2](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig2)(A), in that case you display five MNIST images on each of ten rows. You would see 7&1, 5&8, 0&3, 2&6 and 4&9 are in five different columns. If the variable ‘n\_class’ in Cell 01 is 20 and 20 digital images are displayed on each of five rows in figure [6.2](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig2)(A), you will see one digit in two or even three columns with slightly different styles. I also changed the variable ‘styles’ from 2 to 4, but could not get more than two control dials to tune fake images. Changing the dataset name in Cell 01, we can use the above infoGAN codes for the FashionMNIST dataset. You can see that the style variable c[11] could be used to tune the brightness of fake images, and another variable c[12] could be used to tune the contrast of those fake images.

### 6.3 infoGAN for fake Anime-face dataset images

The Anime-face dataset has no label information. From the outputs of Cell 03 in project 6.3.1, you will see all image labels are the same: 1. The variable for the number of latent labels *n\_class* in Cell 01 is arbitrarily set to be equal to 10. We will separate Anime-face images into 10 classes. The number of latent styles is set to be equal to 2, so we have two dials to tune fake images. With the dimension number of the incompressible noise (*z*) is set to be equal to 116, the number of dimensions of a noise vector (Z) for fake image generation is 128. Figure [6.4](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig4) shows some fake images. They are half of the outputs of Cell 14. The quality of fake images is good, but still not good enough comparing with real images. Each column of those fake images belongs to a class. Figure [6.5](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig5) shows loss curves and tuned fake images. The outputs of Cell 16 are 10 × 10 fake images, but only three rows are shown in figure [6.5](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig5)(C). Images in each row belong to a class. The last style variable c[12] can be used to tune the hue of fake images from yellow to blue by changing c[12] from positive to negative. Figure [6.5](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig5)(D) was generated by codes in Cell 17 with c[12] or *Z*\[:,−1\] = 1. The first style variable c[11] can be used to tune the light direction or the side in shadow of fake images. Shadows in the fake images in figure [6.5](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig5)(E) are on the right hand side. These images were generated by codes in Cell 18 with c[11] or *Z*\[:,−2\] = 3.

![Figure 6.4. Fake anime images, half of the outputs of Cell 14, and each column is a class (model training time: 48 min).](images/bk978-0-7503-6244-3ch6f4_online.jpg)

**Figure 6.4.** Fake anime images, half of the outputs of Cell 14, and each column is a class (model training time: 48 min).

![Figure 6.5. (A and B) Curves of Loss functions, the outputs of Cell 15. (C) Fake anime images, the first three rows of the outputs of Cell 16. (D) Fake images tuned by the last style variable Z\[:,−1\] which changes the fake image hue from yellow to blue, the output of Cell 17. (E) Fake images tuned by the first style variable Z\[:,−2\] which changes the image shadow from left side to right side, the output of Cell 18.](images/bk978-0-7503-6244-3ch6f5_online.jpg)

**Figure 6.5.** (A and B) Curves of Loss functions, the outputs of Cell 15. (C) Fake anime images, the first three rows of the outputs of Cell 16. (D) Fake images tuned by the last style variable *Z*\[:,−1\] which changes the fake image hue from yellow to blue, the output of Cell 17. (E) Fake images tuned by the first style variable *Z*\[:,−2\] which changes the image shadow from left side to right side, the output of Cell 18.

![](images/bk978-0-7503-6244-3ch6uf10_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf11_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf12_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf13_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf14_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf15_pr.gif)

### 6.4 Implementation of infoGAN to the rock paper scissors dataset

Project 6.4.1 is not easy. All those hyperparameters in Cell 01 were found by trying in a few days. Using a laptop with a few gigabytes of GPU memory (6 GB) to the dataset with bigger image size (128 × 128), I had to choose a small batch size (36). The incompressible noise dimensions (*z\_dim*), the initial learning rate (*lr*), and the ratio (k) of *lr\_G* to *lr\_D1* are all critical. The RMSprop optimizer is better than the Adam optimizer for this project. If model D in section [3.3.2](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-3-2) was modified for model D0 and Model D1 in this project, fake images would have broken fingers and swollen fingers. With the powerful residual neural network (ResNet9) in section [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-3), it is possible to generate fake images with good enough quality shown in figure [6.6](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig6)(B).

![Figure 6.6. (A) Real images are the outputs of Cell 04. (B) Fake images are the outputs of Cell 14, and each column is a class (model training time: 9 min). The real images were reproduced with permission from Laurence Moroney, the author of the rock paper scissors dataset.](images/bk978-0-7503-6244-3ch6f6_online.jpg)

**Figure 6.6.** (A) Real images are the outputs of Cell 04. (B) Fake images are the outputs of Cell 14, and each column is a class (model training time: 9 min). The real images were reproduced with permission from Laurence Moroney, the author of the rock paper scissors dataset.

We know that there are three classes in the dataset, but the hyperparameter (*n\_class*) for the number of classes was intentionally set to be six. In figure [6.6](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig6)(B), images in each column belong to a class. The column sequence is \[0,1,2,3,4,5\]. Two columns in the figure are for label rock, three columns are for label scissors, and one column is for label paper (open hand). With codes in Cell 16, fake images in column 1, 2, and 0 of figure [6.6](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig6)(B) were displayed in row 0, 1 and 2 of figure [6.7](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig7)(A). Using infoGAN, we can generate the desired images by tuning the latent labels. The dark fake images on rows 3 to 5 in figure [6.7](#Chapter_6.xhtml#bk978-0-7503-6244-3ch6fig7)(A) are the same as those on rows 0, 1 and 2 respectively. However, the style variable of the last three rows was set to be equal to 30. The only style variable in the project could be used to tune the contrast of fake images.

![Figure 6.7. (A) Fake images generated by tuning the latent label code and the style variable. (B) Curves of loss functions for model G and D1. (C) Loss function curves for model Q.](images/bk978-0-7503-6244-3ch6f7_online.jpg)

**Figure 6.7.** (A) Fake images generated by tuning the latent label code and the style variable. (B) Curves of loss functions for model G and D1. (C) Loss function curves for model Q.

![](images/bk978-0-7503-6244-3ch6uf16_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf17_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf18_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf19_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf20_pr.gif)

![](images/bk978-0-7503-6244-3ch6uf21_pr.gif)

### Reference

Chen X, Duan Y, Houthooft R, Schulman J, Sutskever I and Abbeel P 2016 Infogan: interpretable representation learning by information maximizing generative adversarial nets *Adv. Neural Inform. Process. Syst* **29** 2172–80

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 7

## Object detection by YOLOv1/YOLOv3 models

This is the hardest chapter in the book. YOLO is the most powerful computer vision technique for object detection, object counting, object tracking and image segmentation, etc. It will be helpful for you to understand models of later YOLO versions by YOLOv1 codes which are written from the ground up in this chapter with many help functions. You can skip YOLOv1 if it is too hard for you, because the latest YOLOv8 models are easy to use without knowing YOLOv1. Two Python functions for YOLOv3 in section [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7s7-5) are used in the rest of the book to display images or video frames processed by other computer vision models just by changing the model's name in the two functions.

Most of our information comes to us from our eyes, and most of our actions/behaviors are responses to what we see. With only a glance at an image, we instantly know the categories, locations and relationships of objects on the image. We are on the way to having our computers with artificial intelligence to do the same thing. In chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2), ResNet models were used to tell us what an object was on a photo. This kind of computer vision work is image classification: to identify the category of an object on an image. But the intelligence of those neural networks is only at the level of human babies. In practical applications of computer vision, such as the applications of auto-driving software, we not only need to identify multiple objects on each photographic frame, but also need to know where those objects are on the frame using bounding boxes. This kind of computer vision work is object detection: the combination of object classification and object location. The outputs for an object detection project provide spatial information about objects using bounding boxes. From that information, we will know what the coordinates of the top-left corner and the lower-right corner of each bounding box are, or the center coordinates plus width and height of each bounding box. We also will know what object is in each bounding box and what the probability is of that object in the bound box.

With neural networks for image classification, object detection should be a very easy job for us. Suppose the image resolution in an image dataset or a video camera is 640 × 480, we could use a 64 × 48 window to slide across an image from left to right and top to bottom, so the object detection job for the image is separated into 100 image classification jobs on these 10 × 10 small areas of the image. The location information of any area with an object is obtained from the location of the sliding window. But this simple algorithm has a number of issues to overcome. The first one is how to choose the size of the small window so that there is only one object within it. Different objects have different sizes. Even a same object has different sizes on an image depending on the distance between the object and the camera taking the image. The second issue is the height/width ratio of the window. Some objects, e.g. trees are taller and some objects, e.g. buses are wider. To consider these issues, we have to use multiple sliding windows with different sizes and different ratios. The computation job of the simple algorithm is too heavy to handle with contemporary computer hardware for real-time object detection. For example, a car driven by auto-driving software needs eight cameras to get a 3D view around the car, and each camera takes 24 images per second. Even if the computer in the car could finish object detection in one second for those 24 × 8 images, the car will have moved 10 meters at a speed of 36 km h^(−1) (the speed limit within a school zone). To avoid car accidents, we need the car's computer to do object detection calculations in a few milliseconds.

In 2014, Ross Girshick and his colleagues in UC Berkeley proposed a region-based convolutional network (R-CNN) algorithm (Girshick *et al* [2014](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib3)) for object detection. It is a two-stage detection algorithm: the first stage is used to find sub-regions on an image with objects, the second stage is then used with neural networks to classify each object in a sub-region that might contain objects. Computing time is saved by handling only those regions with probabilities of containing objects. Based on this algorithm, Fast R-CNN (Girshick [2015](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib2)) in 2015, Faster R-CNN (Ren *et al* [2015](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib8)) in 2016 were proposed to improve object detection speed and accuracy. Although Faster R-CNN's detection accuracy is higher, it is still not quick enough for real-time object detection. Then in 2016, we had algorithms of one-stage object detection: Single-Shot Detector (SSD) (Liu *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib5)) and You Only Look Once (YOLO) (Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6)). Using an image as an input, a model with either of the two algorithms uses a convolutional neural network to find objects on images. They are fast enough for real-time object detection with good enough accuracies. After Redmon *et al* introduced the first YOLO version, we then had YOLOv2, YOLOv3, YOLOv4, YOLOv5, YOLOv6, YOLOv7, YOLOv8 and YOLOv9.

### 7.1 Bounding boxes of Pascal VOC database for YOLOv1

To understand YOLOv1, we need to know the data structure of Pascal VOC 2012 database (Everingham *et al* [2012](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib1)). Images in the database were selected from Flickr, an image source contributed by many individuals with different licenses. The database can be used for object classification, detection, and segmentation. The images and labels can be downloaded from Kaggle. After setting up a Kaggle account from my Google account, I downloaded a 2 GB compressed file named ‘VOCtrainval\_11-May-2012.tar’, and then unzipped the file onto my laptop. The uncompressed files in five sub-folders occupied more than 5.6 GB in my laptop's hard driver. We only need to use two sub-folders for object detection. One sub-folder is named *JPEGImages*, and the other sub-folder is named *Annotations*. In the first sub-folder, there are 17 125 images in 20 classes. In the second sub-folder, there are 17 125 xml files containing information about bounding boxes for each image. The prefix of each JPEG image file name is the same as those for the XML file labeling the image (XML is the abbreviation of extensible markup language). XML files are also used for storing, transmitting and reconstructing arbitrary data. They can be opened and edited with any web browser or any text editor, e.g. Notepad in MS Windows. The code below is the structure of a XML file opened in a web browser. From the data in the XML file, we know the image's shape is 600 × 540 × 3. On the image, there are three objects: two people and a dog. The coordinates of two corners of each object are listed in the XML file. These coordinates are pixels relative to the top-left corner \[0,0\] of the image. To avoid copyright issues, many of the images used in chapters [7](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7)–[12](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12) are from my own camera.

![](images/bk978-0-7503-6244-3ch7uf1a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf1b_pr.gif)

 

To manipulate XML data in Python, we need to install a python module named *x**m**l**t**o**d**i**c**t*inline-graphic style="height:1em;" xlink:href="bk978-0-7503-6244-3ch7ieqn1.gif"/ to use as a tool. A function defined in the following Utility 01 can be used to read XML files for information about bounding boxes for any Pascal VOC image. The output of the *xmltodict* module on line 03 of the cell is a list with more than one element, and each element is an OrderedDict if there is more than one object in an image. But when there is only one object in an image, the output of the module is just an OrderedDict. Codes on line 05–06 of the cell were used to pack the output into a list for any image with only one object. Without these codes, our program would give error message and stop its work occasionally. You can change the index variable from 8 to 8888 on line 01 in the App-Cell after Utility 02 to see the issue. Running these codes in the free Kaggle GPU platform, I found the output of the *xmltodict* module was a Python dictionary, so the condition on line 05 of Utility 01 was changed for both cases. Codes on line 04–05 in the App-Cell are used to replace codes on line 02–03 to display my own image files. Figure [7.1](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig1) showed my image with its three bounding boxes for two people and a dog. The object class name of each bounding box was printed at its center. A 7 × 7 grid was also printed over the image. Different images have different resolutions in VOC dataset. The coordinates of the top-left corner and lower-right corner of each bounding box on an image are relative to the top-left corner \[0, 0\] of the image. Using codes on line 01-03 and deleting codes on line 04-05 in the App-Cell, you will see a VOC image (index = 54) with rider on a white horse.

![](images/bk978-0-7503-6244-3ch7uf2_pr.gif)

![Figure 7.1. An image and its three bounding boxes with their VOC class labels printed at their centers respectively (the outputs of the following App-Cell). Information of the three bounding boxes came from the above XML file.](images/bk978-0-7503-6244-3ch7f1_online.jpg)

**Figure 7.1.** An image and its three bounding boxes with their VOC class labels printed at their centers respectively (the outputs of the following App-Cell). Information of the three bounding boxes came from the above XML file.

According to the YOLOv1 paper (Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6)), grid cells in an array of 7 × 7 are used to encode bounding boxes on each image. In a Cartesian coordinate system, we usually use a pair of numbers (*x*, *y*) as coordinates of an object on a plane (2D space), and the positive direction of the *y*\-axis is bottom-up. For NumPy arrays and torch tensors, we also use a pair of numbers (row\_idx, column\_idx) to locate a matrix element. Both the row index and the column index start from zero, but the positive direction of the row-axis is upside down. You can find the center of the woman (person) in figure [7.1](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig1) is in the grid cell (2, 1) or \[2,1\], and the dog's center is in the grid cell \[5,2\]. There are 20 classes in the VOC dataset. The names of those classes can be found by searching web sites. In a list above the Utility 01 Cell are names of the 20 classes. If you count one by one, you will find the index of the category of ‘person’ is 14. You can verify your counting by a Python code's output of *classes\[14\]*. Sometimes we know the name of an object, for example ‘dog’, and Python can find its index is equal to 11 by the code's output: *classes.index(‘dog’)*.

### 7.2 Encode VOC images with bounding boxes for YOLOv1

Computers really do not know anything about image objects but only understand the digits ‘0’ and ‘1’. After model training, it appears that a computer has the intelligence to tell us something about our images in a dataset, because we trained models in the computer using data in a special format with special loss functions. Neural networks are so powerful that they remember many details about images so that they can fool us by ‘overfitting’. We have to do more work on image augmentations to avoid overfitting issues.

#### 7.2.1 VOC image augmentations with bounding boxes

When the image shown in figure [7.1](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig1) is resized to 448 × 448 for YOLOv1 model training, the coordinates of those three bounding boxes also need to be transformed accordingly. In the YOLOv1 model training, the width and height of each bounding box in a transformed image is normalized by 448. The coordinates of the center of each bounding box \[x\_c, y\_c\] are normalized by 64. Since the value of x\_c or y\_c could be any integer from 0 to 448, the normalization to 64 should be a number whose value is in the range 0–7. An integer part of the number is used as a grid cell's row index or column index; the value of the remainder of the normalization is less than 64 pixels. The remainder is then normalized by 64 again as a center coordinate of the bounding box relative to the top-left corner of the grid cell. In this way, all four parameters of each bounding box are positive numbers with their values less than one. We do these extra works to reduce the possibility of explosions of loss function values.

To fight overfitting issues in model training, we have to do a random horizontal flip, a random vertical flip, a random rotation and more augmentations to each image. The bounding boxes of each image with augmentations must also have the same transformations, so that each bounding box would not lose its target. By the end of those augmentations, the left and right sides of each bounding box should be vertical, and the top and bottom sides of the bounding box should be horizontal even if the image was rotated. This work employs very tedious mathematics. We can use a Python module named ‘albumentations’ to do these complex jobs automatically with a function defined in the following Utility 03. The augmentation function uses any VOC image and its bounding boxes from Utility 01 as inputs. The outputs of the function are the transformed image and its transformed bounding boxes. The format option of the augmentation transforms on line 15 of Utility 03 could be ‘pascal\_voc’, ‘coco’ or ‘yolo’ for different bounding box styles in different datasets. More augmentations could be added between line 01 to 15. Each augmentation would increase the model training time. Figure [7.2](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig2) shows a transformed image and it bounding boxes. Comparing this with figure [7.1](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig1), you will find that the original image is rotated and horizontally flipped.

![](images/bk978-0-7503-6244-3ch7uf3_pr.gif)

![Figure 7.2. Augmentations of an image with its bounding boxes by codes in Utility 03. The coordinates of the three bounding boxes are \[0, 0, 206, 404, 14\], \[307, 107, 418, 346, 14\] and \[154, 284, 305, 448, 11\] respectively. The centers of the three objects are in grid cell \[3, 1\], \[3, 5\] and \[5, 3\] respectively.](images/bk978-0-7503-6244-3ch7f2_online.jpg)

**Figure 7.2.** Augmentations of an image with its bounding boxes by codes in Utility 03. The coordinates of the three bounding boxes are \[0, 0, 206, 404, 14\], \[307, 107, 418, 346, 14\] and \[154, 284, 305, 448, 11\] respectively. The centers of the three objects are in grid cell \[3, 1\], \[3, 5\] and \[5, 3\] respectively.

#### 7.2.2 Encoding bounding boxes to grid cells for YOLOv1 model training

Figure [7.2](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig2) will be used as an example for encoding bounding boxes to grid cells on a transformed image by a function defined in the following Utility 04. The input of the function is the second output of Utility 03. First, a tensor named ‘label\_matrix’ is defined with a shape \[S, S, C + 5B\] for any transformed VOC image with a resolution 448 × 448, where S, C and B are equal to 7, 20 and 2 respectively. The value of each element in the label\_matrix tensor is initialized to be equal to zero. We can treat the label\_matrix tensor as a 3D object with S × S squares on a plane and behind each square there are 30 cubes. Cubes from 0 to 19 of a grid cell are used to hot-code the class label of an object whose center is in the grid cell. For example, we find the center of the boy (person) in figure [7.2](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig2) is in grid cell \[3, 1\]. Since the index for person in the VOC classes is 14, we then set: label\_matrix\[3, 1, 14\] = 1 by using a code on line 22 of Utility 04. Also, the dog class's index in the VOC classes is 11 and the dog is in grid cell \[5, 3\], so we set the value of a cube: label\_matrix \[5, 3, 11\] = 1. Cube 20 of each grid cell in the label\_matrix is used to record the probability of an object in the cell. For our training dataset, the probability is set to be one, so we have label\_matrix\[3, 1, 20\] = 1 and label\_matrix\[5, 3, 20\] = 1.

Any grid cell's cubes from 21 to 22 are used to record the center coordinates of an object relative to the top-left corner of the grid cell from which we can find the center of the object. The same grid cell's cubes from 23 to 24 are used to store the width and height of the bounding box relative to the transformed image. By reading the second outputs of Utility 03 with codes starting from line 04 in Utility 04, we get the boy's bounding box information \[0, 0, 206, 404, 14\]. They are x\_min, y\_min, x\_max, y\_max and class\_id respectively. The center coordinates (*X*[*c*], *Y*[*c*]), the width (*W*) and height (*H*) of the bounding box relative to the transformed images are easy to obtain with the following formulae in which the lower-case variables are parameters relative to the grid cell. The column index of the grid cell is the integer part of (*X*[*c*]/64), and the remainder of the division normalized by 64 again is *x*[c]. The row index and column index of the grid cell with the boy's center are 3 and 1 respectively. The coordinates of the boy's center relative to the top-left corner of the grid cell are \[0.61, 0.16\]. Now we can fill the cubes from 21 to 24 for grid cell \[3, 1\] with \[*x*[*c*], *y*[*c*], *w*, *h*inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch7ieqn2.gif"/\]. The value of each of the last five cubes of any grid cell is zero for any image in a training dataset. The encoding results of grid cell \[3, 1\] is a list: label\_matrix \[3, 1, :\] = \[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1.0, 0.61, 0.16, 0.46, 0.90,0, 0, 0, 0, 0\]inline-graphic style="height:3.3125em;" xlink:href="bk978-0-7503-6244-3ch7ieqn3.gif"/. The dog's bounding box information in the same image is \[154, 284, 305, 448, 11\]. You can use this to encode the grid cells \[5, 3\] for the dog. The function defined in Utility 04 does the above job automatically. A NumPy function *np.where()* can be used to find any grid cell with an object on an image. The function outputs two 1D arrays for those grid cells’ row indices and column indices. Codes from line 16 to line 22 are used to ensure that one grid cell on a VOC image only encodes one object. The maximum objects detected by a YOLOv1 model on any image is 49. This is a limit of YOLOv1 model.

  
$$\\begin{matrix} {X\_{c} = \\frac{1}{2}\\left( {x\_{\\max} + x\_{\\min\\ }} \\right)} \\\\ {Y\_{c} = \\frac{1}{2}\\left( {y\_{\\max} + y\_{\\min\\ }} \\right)} \\\\ {W = x\_{\\max} - x\_{\\min} = 206} \\\\ {H = y\_{\\max} - y\_{\\min} = 404} \\\\ \\end{matrix},\\begin{matrix} {X\_{c} = \\frac{1}{2}\\left( {206 + 0} \\right) = 103} \\\\ {Y\_{c} = \\frac{1}{2}\\left( {404 + 0} \\right) = 202} \\\\ {w = \\frac{W}{448} = 0.46\\ } \\\\ {h = \\frac{H}{448} = 0.90\\ } \\\\ \\end{matrix},\\ \\begin{matrix} {x\_{c} = \\left( {X\_{c}\\% 64} \\right)\\frac{1}{64} = 0.61\\ } \\\\ {y\_{c} = \\left( {Y\_{c}\\% 64} \\right)\\frac{1}{64} = 0.16\\ } \\\\ {{colum}n\_{idx} = {int}{(\\frac{X\_{c}}{64})} = 1} \\\\ {{ro}w\_{idx} = {int}{(\\frac{Y\_{c}}{64})} = 3\\ } \\\\ \\end{matrix}$$  
graphic style="width:28.875em;" xlink:href="bk978-0-7503-6244-3ch7ueqn4.gif" position="float"/

![](images/bk978-0-7503-6244-3ch7uf4_pr.gif)

#### 7.2.3 Chess pieces dataset from Roboflow

The Pascal VOC 2012 database is not a dataset. With the above auxiliary functions defined in Utility 01–04, it is possible for us to pack those images and their labels into a dataset for YOLOv1 model training. However, the Pascal VOC 2012 dataset is too big for my laptop to handle. According to Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6), the YOLOv1 model's first 20 convolutional layers were trained with ImageNet dataset in one week. Four more convolutional layers and two fully connected layers were then added, and the YOLOv1 model was trained by images from PASCAL VOC 2007 and 2012 with more time. To demonstrate YOLOv1 model training, I have to use a small dataset: Chess Pieces Dataset. In February 2021, Roboflow kindly released this dataset free on a public license. Inside a 17 MB zip file, there are 693 images in 13 classes for YOLOv7 model training. Bounding box information about chess piece images is in the text files, not in the XML files. From those files, you can see each object's class index, object center coordinates, its bounding box width and height normalized by 416. Here is an example of a label text file for the first test image about a white bishop chess piece: 7 0.5120192307692307 0.0829326923076923 0.04567307692307692 0.13341346153846154. All the image files and label files are in three sub-folders: train, test and valid in a folder named Chess. Codes in Utility 05 could be used to convert text files in each of the three sub-folders into XML files for YOLOv1 model training. Since the original file names are too long to remember, the file names were changed to integers with three digitals by a code on line 20 in the following Utility 05. The XML file converted from a text file about the white bishop is listed below. The XML file's structure is simpler than the one in the VOC dataset. Under the <object> item, there is no <bndbox> item. When we pack these files for a dataset, we have to delete \[‘bndbox’\] on line 10 to 11 in Utility 01 for the chess dataset. Please pay attention to an integer in *str(idx + I)* on line 20. Using Utility 05, all 693 samples in the train, valid and test sub-folders are converted and moved into a folder named chess4yolov1 with two sub-folders: *Annotations* and *JPEGimages*. File names of converted samples have three digitals from 000 to 692. If the root folder on line 03 of Utility 05 is set for the sub-folder train, the integer I in *str(idx + I)* on line 20 is equal to 0; for the sub-folder valid, the integer I is equal to 606; and for the sub-folder test, the integer I is equal to 664. A sample with name 688 was deleted because 688.xml is empty. With an object empty sample in the dataset, my codes had issues during model training. Codes in Utility 05 can run in VS Code with Python 3.9, not Python 3.6 which does not support writing a pandas DataFrame to an XML file.

![](images/bk978-0-7503-6244-3ch7uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf6_pr.gif)

 

After running codes in Utility 05 for files in the three sub-folders: train, test and valid, image files were obtained and moved to the sub-folder *JPEGimages*, and all XML files were moved to the *Annotations* folder. Before packing these files into a dataset in the following project [7.1](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn8), all modules or tools necessary for the project are imported in Cell 01, in which hyperparameters are also set. For my 6 GB memory in a RTX 2060 GPU, the maximum batch size is eight. With Kaggle's free 16 GB GPU memory, the maximum batch size could be 128. Usually, training results with a small batch size are better. The last two lines of Cell 01 are for a list of XML files and a list of image files respectively. I have to list the Utility 01 after Cell 01, because the Chess dataset's XML file structure is different from VOC dataset's XML file structure. The Chess dataset constructed in Cell 02 is randomly split into three datasets, and from them we have a train dataloader, a valid dataloader and a test dataloader. Their sample sizes are 560, 80 and 52 respectively. Codes in Cell 04 are used to display some images in a dataloader. A function named ‘grid2bboxes’ defined in the Cell 03 extracts encoded grid cells’ information of images for parameters of bounding boxes.

![](images/bk978-0-7503-6244-3ch7uf7_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf8_pr.gif)

### 7.3 ResNet18 model, IOU and a loss function

#### 7.3.1 Using ResNet18 to replace YOLOv1 model

There is no super power in the YOLOv1 model which is just a linear CNN model with 24 convolutional layers followed by two fully connected layers. In July 2022, we had YOLOv7 models (Wang *et al* [2022](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib9)). In January 2023, Ultralytics released a more powerful YOLOv8 models. The simple YOLOv1 is still useful for us to understand the YOLO algorithm. The original YOLOv1 model did not use batch normalizations because batch normalization (Ioffe and Szegedy [2015](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib4)) was invented a year later than YOLOv1. In Aladdin Persson's GitHub, the original YOLOv1 model was modified by adding a batch normalization after each convolutional operation. However, the modified YOLOv1 is still not powerful enough for the Pascal VOC dataset on my laptop, so a pre-trained ResNet18 (section [2.4](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-4)) is used as a model for the Chess dataset. On the first line of Cell 05, the pre-trained ResNet18 model was imported from models in torchvision. Then the number of output variables of the last fully connected layer in the ResNet18 was changed from 1000 to 1127 (= 7 × 7 × 23) for predicted values in 23 cubes of each 7 × 7 grid cells. I only used the pre-trained ResNet18 model in the first 100 eopochs of model training. At the end of the first 100 epochs of model training, I saved a trained model to a file named *Chess-Yolo-01.pth*, and moved the ‘‴inline-graphic style="height:0.5em;" xlink:href="bk978-0-7503-6244-3ch7ieqn5.gif"/’ symbols on line 09 to the front of line 01. In this way, I could use the trained model for the next 100 epochs. The trained model file name should be changed by increasing the last digital of the previous file name. With Python v3.6, model training takes about 54 min for every 100 epochs by running codes in Cell 09. With Python v3.9, the model training time for the same codes is 37 min. In about 20 h within two days, the model training gave me good enough results (figure [7.3](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig3)). It seems that the Adam optimizer is better than the SGD optimizer in the Chess project. During model training, the learning rate was changed by *ReduceLROnPlateau* scheduler. The mean average precision (mAP) is an important index of model training for object detection. If mAP is above 0.5, our model training is good enough; mAP around 0.7 is good; and mAP above 0.9 is excellent. For an excellent model training, the true and the predicted bounding boxes in figure [7.3](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig3) should be the same.

![](images/bk978-0-7503-6244-3ch7uf9_pr.gif)

![Figure 7.3. A test image with its true bounding boxes (yellow) and predicted bounding boxes (red) at the end of model training with 100 × 21 epochs. Final mAP for the train, validation and test dataloaders is 0.76, 0.62 and 0.66, respectively. Model training time is 37 min for every 100 epochs. The Chess Pieces Dataset is from Roboflow (2001) with a license CC BY 4.0.](images/bk978-0-7503-6244-3ch7f3_online.jpg)

**Figure 7.3.** A test image with its true bounding boxes (yellow) and predicted bounding boxes (red) at the end of model training with 100 × 21 epochs. Final mAP for the train, validation and test dataloaders is 0.76, 0.62 and 0.66, respectively. Model training time is 37 min for every 100 epochs. The Chess Pieces Dataset is from Roboflow ([2001](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib10)) with a license CC BY 4.0.

#### 7.3.2 Intersection over union (IOU) and the loss function

The bounding boxes for each image are encoded by 7 × 7 grid cells. For the Chess dataset with 13 classes, there are (13 + 5 × 2) cubes for each grid cell. The last five cubes (from 18 to 22) of each grid cell in a model prediction are used for the bounding box of another predicted object. Each grid cell of the model's predictions could predict two bounding boxes. However, we only use one bounding box which had a higher IOU value with a true bounding box in the same grid cell for calculations of loss function values. We have to recap IOU for image classification in chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2).

Suppose we have two pieces of paper, and they have the same size: 10 × 10 cm². If the paper on top covers 1/4 the area of the other paper, the intersection area of the two pieces of paper is 25 cm². Then we can calculate the IOU of the two pieces of paper: IOU = 25/(100 + 100 − 25) = 1/7. In the case when they completely overlap each other, the IOU value is one. Computers do the job in a different way. Using the code on line 17 of Cell 04, we get a batch of transformed images and their bounding boxes encoded in grid cells for a batch of samples in a train dataloader. The batch of bounding boxes are our targets. Taking the batch of transformed images into the ResNet18 model on line 15 of Cell 05, we can obtain the model's output y\_hat with a shape of N × 1127, where N is the batch size: 8. The y\_hat and the targets are then taken into a loss class defined in Cell 06 (line 07) in section 7.3.3. From the codes on line 10, 12 and 14 of Cell 06, we have a batch of true bounding boxes, two batches of predicted bounding boxes. The following IOU function defined in *Utility\_fn(1/5)* will use each bounding box's center coordinates (x\_c, y\_c), width (*w*) and height (*h*) to calculate IOU values according to the following formulae

  
$$\\begin{matrix} {x\_{1\\ \\min} = x\_{1c} - \\frac{1}{2}w\_{1}} \\\\ {y\_{1\\ \\min} = y\_{1c} - \\frac{1}{2}h\_{1}} \\\\ {x\_{1\\ \\max} = x\_{1c} + \\frac{1}{2}w\_{1,\\ }} \\\\ {y\_{1\\ \\max} = y\_{1c} + \\frac{1}{2}h\_{1}} \\\\ \\end{matrix}\\begin{matrix} {x\_{2\\ \\min} = x\_{2c} - \\frac{1}{2}w\_{2}} \\\\ {y\_{2\\ \\min} = y\_{2c} - \\frac{1}{2}h\_{2}} \\\\ {x\_{2\\ \\max} = x\_{2c} + \\frac{1}{2}w\_{2}} \\\\ {y\_{2\\ \\max} = y\_{2c} + \\frac{1}{2}h\_{2}} \\\\ \\end{matrix}$$  
graphic style="width:15.9375em;" xlink:href="bk978-0-7503-6244-3ch7ueqn6.gif" position="float"/

  
$$\\begin{matrix} {x\_{3\\ \\min} = {\\max\\ }\\left( {x\_{1\\ \\min},x\_{2\\ \\min\\ }} \\right)} \\\\ {y\_{3\\ \\min} = {\\max\\ }\\left( {y\_{1\\ \\min},y\_{2\\ \\min\\ }} \\right)} \\\\ {x\_{3\\ \\max} = {\\min\\ }\\left( {x\_{1\\ \\max},x\_{2\\ \\max\\ }} \\right)} \\\\ {y\_{3\\ \\max} = {\\min\\ }\\left( {y\_{1\\ \\max},y\_{2\\ \\max}} \\right)} \\\\ \\end{matrix},\\ \\begin{matrix} {w\_{3} = x\_{3\\ \\max} - x\_{3\\ \\min}} \\\\ {h\_{3} = y\_{3\\ \\max} - y\_{3\\ \\min}} \\\\ {A\_{12} = w\_{1}h\_{1} + w\_{2}h\_{2}} \\\\ {{IOU} = \\frac{w\_{3}h\_{3}}{A\_{12} - w\_{3}h\_{3}}} \\\\ \\end{matrix}$$  
graphic style="width:19.875em;" xlink:href="bk978-0-7503-6244-3ch7ueqn7.gif" position="float"/

 

The IOU function's inputs are the parameters of true bounding boxes and predicted bounding boxes. They have the same structure: \[…, x\_c, y\_c, w, h\]. The three dots indicate an image's index in a batch of dataloader, row index and column index of a grid cell on an image's 7 × 7 grid cells. The intersection area of two rectangles is still a rectangle. The coordinates of the top-left corner and the lower-bottom corner of the intersection could be obtained from the above formulae in which the variables’ subscript number 1, 2, and 3 are used for a predicted bounding box, a true bounding box and their intersections respectively. To use these formulae, we should have each bounding box's four parameters at the same scale. However, each bounding box's center coordinates are normalized by 64, and the width and height of the box are normalized by 448. A constant *self.S* on line 10, 12 and 14 in Cell 06 is used to set them to the same scalar. To calculate the IOU of two bounding boxes in different grid cells of an image, we also need to consider each grid cell's row index and column index to y\_c and x\_c respectively. Please pay attention to the data structure: ‘boxes\_preds\[…, 0:1\]’ in the IOU function. With this kind of tensor structure, we keep the original tensor's shape, so we can do calculations for 4D tensors without for-loops to save computation time. If the data structure is like this ‘boxes\_preds\[…, 0\]’, we will lose the last dimension of the original tensor, and waste time in many for-loops. The average IOU values of all classes on all images of a dataset is the mAP metrics or index. Aladdin Persson has very helpful YouTube videos about [IOU](https://www.youtube.com/watch?v=XXYG5ZWtjj0…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=3), [mAP](https://www.youtube.com/watch?v=FppOzcDvaDI…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=2), Non Max Suppression ([NMS](https://www.youtube.com/watch?v=YDkjWEN8jNA…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=4)) and [more](https://www.youtube.com/watch?v=n9_XyCGr-MI). Some of the following codes were inspired by his [GitHub](https://github.com/aladdinpersson/Machine-Learning-Collection/tree/a2ee9271b5280be6994660c7982d0f44c67c3b63/ML/Pytorch/object_detection/YOLO) codes with MIT license.

![](images/bk978-0-7503-6244-3ch7uf10a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf10b_pr.gif)

 

During model training, five parts of the following loss function (Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6)) are optimized by the mean squared error algorithm. It is easy to see that the first part is for errors of center coordinates of the bounding boxes, and the second part is for errors of square roots of sizes (widths and heights) of bounding boxes. The square roots of sizes are used to balance errors between bigger and smaller bounding boxes. Because the size values of bounding boxes are less than 1.0 in YOLO encoding, the square root operations will amplify size errors nonlinearly, and errors from smaller sizes are amplified more. From the values of (0.1)^(1/2) and (0.01)^(1/2), you would have an idea why not directly use the sizes of bounding boxes in the second part of the loss function. A bigger hyperparameter λ[coord] = 5 is used to enhance the bounding boxes' coordinate errors and size errors.

  
$$\\begin{matrix} {L = \\lambda\_{coord}\\sum\\limits\_{i = 0}^{48}{\\sum\\limits\_{j = 0}^{1}{1\_{ij}^{obj}\\left\\lbrack {\\left( {x\_{i} - {\\widehat{x}}\_{i}} \\right)^{2} + \\left( {y\_{i} - {\\widehat{y}}\_{i}} \\right)^{2}} \\right\\rbrack}} + \\lambda\_{coord}\\sum\\limits\_{i = 0}^{48}{\\sum\\limits\_{j = 0}^{1}{1\_{ij}^{obj}\\left\\lbrack {\\left( {\\sqrt{w\_{i}} - \\sqrt{{\\widehat{w}}\_{i}}} \\right)^{2} + \\left( {\\sqrt{h\_{i}} - \\sqrt{{\\widehat{h}}\_{i}}} \\right)^{2}} \\right\\rbrack}}} \\\\ {+ \\ \\sum\\limits\_{i = 0}^{48}{\\sum\\limits\_{j = 0}^{1}{1\_{ij}^{obj}\\left( {{\\widehat{C}}\_{i} - C\_{i}} \\right)^{2}}} + \\lambda\_{noobj}\\sum\\limits\_{i = 0}^{48}{\\sum\\limits\_{j = 0}^{1}{\\left( {1 - 1\_{ij}^{obj}} \\right)\\left( {{\\widehat{C}}\_{i} - C\_{i}} \\right)^{2}}} + \\sum\\limits\_{i = 0}^{48}{1\_{ij}^{obj}\\sum\\limits\_{c \\in {classes}}\\left( {p\_{i}\\left( c \\right) - {\\widehat{p}}\_{i}\\left( c \\right)} \\right)^{2}}} \\\\ \\end{matrix}$$  
graphic style="width:33.8125em;" xlink:href="bk978-0-7503-6244-3ch7ueqn8.gif" position="float"/

 

On each image, there are 7 × 7 grid cells (*i* = 0, 1, …, 48), and the model predicts two bounding boxes (*j* = 0, 1) for each grid cell. The two upper case sigma symbols are shorthand notation to indicate the sum of errors of all 49 × 2 bounding boxes. However, only a few grid cells on an image have objects. The variable 1[*i**j*]^(*o**b**j*)inline-graphic style="height:1.625em;" xlink:href="bk978-0-7503-6244-3ch7ieqn9.gif"/ in the loss function is equal to 1.0 only if a grid cell (*i*) has an object and a responsible bounding box (*j*) which has a higher IOU value to its ground truth bounding box. Otherwise, the variable in the loss function is equal to 0.0. We have to use codes in Cell 06 to explain the above ideas. An instance of the loss function class defined in the cell needs two inputs. The first one is a batch of predictions which came from a batch of images processed by the model: preds *ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch7ieqn10.gif"/. The second one is a batch of encoded bounding boxes: target y. On line 07 and 08, both of them are shaped to N × 49 × 23, where N is the batch size. Each of them is a 3D object with height N, width 49 and depth 23. Using codes on line 15 and 16 of Cell 06, we get IOU values of two predicted bounding boxes of an image on a grid cell to a ground truth, and then search to find the best (responsible) bounding box identity (*j*) on line 19 for each of the 49 grid cells on the image. The tensor named ‘bestbox’ on line 19 is used to do a part of the job for 1[*i**j*]^(*o**b**j*)inline-graphic style="height:1.625em;" xlink:href="bk978-0-7503-6244-3ch7ieqn11.gif"/ on line 21–23.

Taking a batch of images with only a white bishop image into the ResNet18 model by a code on line 15 of Cell 05, we will have the model's prediction *ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch7ieqn12.gif"/ whose shape is \[1, 1127\]. The prediction is then reshaped to \[1, 49, 23\]. We know the resized shape of the target of the white bishop in the batch is the same: \[1, 49, 23\]. In the 49 grid cells of the target, only one is not empty: *y[i]* = \[00000, 00100, 000, 1x[c]y[c]wh, 00000\]. Codes between line 09 to 22 of Cell 06 calculate values of IOU to set one predicted bounding box as a responsible bounding box for each of 49 grid cells. The tensor named ‘exists\_box’ on line 20 does another part of the job for 1[*i**j*]^(*o**b**j*)inline-graphic style="height:1.625em;" xlink:href="bk978-0-7503-6244-3ch7ieqn13.gif"/. It is a *N* × 49 × 1 tensor . The tensor is a map of grid cells with objects on an image. When this tensor is used to multiply another tensor, the result is about grid cells with objects. Using the targets of a batch of images generated on line 17 of Cell 04 and running the codes in an extra cell: *exists\_box = targets\[…, 13:14\]\[0\]; exists\_box.squeeze()*, you would see a 7 × 7 tensor with only a few elements that are not zeros. The exists\_box tensor is used as a mask to pick out responsible boxes as box\_preds on line 23. The value of box\_loss on line 28 is the sum of the first two parts of the loss function without λ[coord]. On line 28, a function torch.flatten(X, end\_dim = −2) changes the shape of a tensor X from 8 × 49 × 4 to 392 × 4. Lines 33, 39 and 43 are for object loss, no object loss and class loss respectively. Detailed information about the loss function can be found in the YOLOv1 paper (Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6)). You can use the following codes inside the quote markers to learn how to calculate 3D tensors in batches: 'x = torch.zeros(2,3,1); x\[0,1,0\]=1; print(x); y = torch.arange(24).reshape(2,3,4); print(y); x\*y'.

![](images/bk978-0-7503-6244-3ch7uf11a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf11b_pr.gif)

### 7.4 Utility functions for model training

Using codes in Cell 07 to 10, we can train the ResNet18 model with the chess dataset. Since these codes for model training have been used many times, it is not necessary to explain them again. It took me a long time to solve the overfitting issue by using those augmentations listed in Utility 03. Augmentations of image rotation and normalization are very helpful to fight the issue. With only resize transformation in Utility 03 for the Pascal VOC images, it was easy to get the train dataset's mAP above 99.8%, but never obtained the valid dataset’ mAP over 1%. The mAP metrics are the most important metrics used to evaluate how good a deep learning model is trained for object detection. The following Utility\_fn(2/5) to Utility\_fn(5/5) should be copied and pasted in front Cell 06 in VS Code.

![](images/bk978-0-7503-6244-3ch7uf12a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf12b_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf12c_pr.gif)

 

After model training, codes in Cell 11 save the trained model to a file which will be used for the next 100-epoch model training, and codes in Cell 12 are used to calculate mAP. A function defined in Utility\_fn(5/5) uses all true bounding boxes and predicted bounding boxes in a dataset to calculate mAP. Those bounding boxes come from a function defined in Utility\_fn(4/5): get\_bboxes. Each of the two outputs of Utility\_fn(4/5) is a list, and each element in the list is a list with seven elements: an image's index in a dataset, a class index, the probability of an object belonging to the class, center coordinates and sizes of a bounding box relative to sizes of a transformed image (448 × 448). For example, the valid dataset has 80 samples, so an image index of a bounding box would be an integer from 0 to 79. Using codes on line 08 and 11 of the mAP function in Utility\_fn(5/5), we could get predicted and true bounding boxes belonging to a class on all images in a dataset. With codes between lines 12 to 15 in Utility\_fn(5/5), numbers of true bounding boxes on each image are encoded by a tensor with elements of zeros. If the first and last images of the valid dataset have three and two true bounding boxes, a dictionary name ‘amount\_bboxes’ on line 15 in Utility\_fn(5/5) would be {0: torch.tensor(0,0,0), …, 79: torch.tensor(0,0)}.

Using the code on line 16 in Utility\_fn(5/5), we reverse sort all predicted bounding boxes in the dataset according to their probabilities: the bounding box with the maximum probability is on top. Then according to an IOU threshold of the mAP function, we would decide if a predicted bounding box is true positive (TP) or false positive (FP). The IOU threshold parameter of the mAP function could be 0.50 to 0.95. With a higher the IOU threshold, we would have a smaller number of TP of bounding boxes. Codes in a for-loop from line 22 to 39 make the decision for us. After picking out a predicted bounding box whose image index is detection\[0\], all true bounding boxes of the same class on the same image are used to find a best true bounding box having the highest IOU. If the IOU is bigger than the IOU threshold and the true bounding box has never been used, the predicted bounding box is a true positive. The used true bounding box is then marked as used on line 35 in Utility\_fn(5/5). Otherwise, the predicted bounding box is false positive. The results of these judgments are recorded by an 1D tensor TP and an 1D tensor FP respectively. Operations of cumulative sum are then acting on the two 1D tensors on line 40 and 41. For example, to a 1D tensor \[1,0,1,0,1\], the result of the cumulative sum operation on dimension zero is \[1,1,2,2,3\]. The results of the two cumulative sum operations are two 1D tensors: TP\_cumsum and FP\_cumsum. From them, we can calculate two more metrics for object detection: recall and precision on line 42 to 45 with the following formulae

  
$$\\mathit{recall} = \\frac{TP\_{cumsum}}{{Tota}l\_{truebboxes}}\\mspace{9mu}\\mathit{precision} = \\frac{TP\_{cumsum}}{TP\_{cumsum} + FP\_{cumsum}}$$  
graphic style="width:23.4375em;" xlink:href="bk978-0-7503-6244-3ch7ueqn14.gif" position="float"/

 

On a 2D plane with *recall* as its *x*\-axis and *precision* as its *y*\-axis, we add one point at \[0,1\] and draw a curve about the relationship between *recall* and *precision*. The area between the curve and the *x*\-axis for each class is recorded in a list, and the average of the areas of all classes is the mean average precision (mAP) at an IOU threshold.

The title of figure [7.3](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig3) told us that yellow rectangles were true bounding boxes, and the dashed red rectangles were predicted bounding boxes. From the trained model's prediction y\_hat = model(images) to each batch images (batch size N), we obtained two batches of predicted bounding boxes, but most of them are empty. A function defined in Utility\_fn(3/5) picks out *N* × 49 responsible bounding boxes for a batch of images. Each bounding box is a list with six elements. They are the class index of a responsible object, its probability, the center coordinates and sizes of the object's predicted bounding box. Then, a few of these bounding boxes are selected by a non-max suppression (NMS) function defined in Utility\_fn(2/5).

The title of figure [7.3](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig3) also indicated that the red boxes came from the model, the responsible\_boxes function and the NMS function. Codes on line 08 and 13 of Cell Utility\_fn(4/5) use the NMS function in Utility\_fn(2/5) to obtain true and predicted bounding boxes for mAP calculations. An input of the NMS function is those responsible bounding boxes on an image. Other inputs of the function are an IOU threshold (=0.5) and a probability threshold (=0.4). With the code on line 02 of the NMS function, only those responsible bounding boxes with probability higher than the probability threshold are selected, and then these selected boxes are sorted reversely according to their probabilities by the code on line 03. In a while loop for those sorted boxes, the first one is popped out as the chosen box. Other sorted boxes are used to reconstruct a shorter list of sorted boxes if any of these boxes is in a different class; or if in the same class of the chosen box, they should have lower IOU values to the chosen box. In this way, many similar bounding boxes of each class are discarded, and only those best boxes are kept.

![](images/bk978-0-7503-6244-3ch7uf15_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf16a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf16b_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf13b_pr.gif)

### 7.5 Applications of YOLOv3 for real-time object detection

It has been a long journey for us to finish the object detection project for the small chess dataset. From this simple project, we have ideas about grid cells, intersection over union, non max suppression, mean average precision and more for a YOLOv1 model. Now, it is possible for us to use more powerful YOLOv3 models without writing long codes from scratch, because YOLOv3 models have been packed in OpenCV (version ⩾ 3.4.2), a library of programming functions for real-time computer vision. Two years after the first YOLO paper, Joseph Redmon and Ali Farhadi published their YOLOv3 paper (Redmon and Farhadi [2018](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib7)). Compared with the YOLOv1 model's 24 convolutional layers, the YOLOv3 model has 106 convolutional layers. The new model is more accurate for object detection because of its three output branches at layer 79, 91 and 103 respectively. Each branch has three layers. Codes in Cell 01 of project [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn23) are used to import libraries and set hyperparameters for the project. MS COCO dataset's class names are obtained by reading a text file, as the YOLOv3 model was trained by the dataset which has more than 200 000 images in 80 classes. The model's configuration files and pre-trained weight files can be found and downloaded from [https://github.com/pjreddie/darknet](https://github.com/pjreddie/darknet) for free. These files save a lot of time for people to train YOLOv3 models. The YOLOv3 configuration file can be opened and edited in MS Notepad. It is about the structure of the YOLOv3 model and its parameters. The last line of Cell 02 is about the three ends of the YOLOv3 model’s three output branches: \[‘yolo\_82’, ‘yolo\_94’, ‘yolo\_106’\]. Each grid cell for YOLOv3 has three anchor boxes (predicted bounding boxes), and each anchor box has 85 cubes. Parameters in cubes 0 to 3 are for center coordinates, width and height of an object in a grid cell. A parameter in cube 04 is for the probability of the object in the grid cell, and the remaining 80 cubes are used to hot encode the COCO class of an object. The maximum number of objects on an image for the YOLOv3 model to detect could be 3 × (13 × 13 + 26 × 26 + 52 × 52). The maximum number of objects for a YOLOv1 model is 49. Although so many calculations are added for the YOLOv3 model, it is still fast enough. The pre-trained YOLOv3 model can use GPU for model training (line 04–05 of Cell 02). It can also be set to use CPU if you want.

A function defined in Cell 04 is used to add bounding boxes, class names and probabilities to an image. Figure [7.4](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig4) shows object detection results of a pre-trained YOLOv3 model for a single image. The code on line 02 of Cell 04 modifies the image to a special format (blob) for the YOLOv3 model. These modifications are normalization, resizing and more. The formatted image is then processed by the model with the code on line 03, and the outputs of the model are obtained from the code on line 04. From the outputs, we have information of many bounding boxes. Using a function defined in Cell 03, only some bounding boxes matching ground truth well are picked out by the NMS module on line 16 of Cell 03. These good bounding boxes are then added to the original image by the codes in Cell 03. We can use the codes in Cell 05 to show all VOC images one by one with bounding boxes, class names and possibilities. Each image will be shown for 1000 milliseconds if you did not press any key on your key board, once any key except the Esc key is pressed, the next image will appear. The title of the image window indicates that if you press the Esc key, the program will be terminated.

![](images/bk978-0-7503-6244-3ch7uf18a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf18b_pr.gif)

![Figure 7.4. Results of object detection by a pre-trained YOLOv3 model for a single image.](images/bk978-0-7503-6244-3ch7f4_online.jpg)

**Figure 7.4.** Results of object detection by a pre-trained YOLOv3 model for a single image.

Watching carefully, you will find that some objects are not detected in the slide show. The pre-trained YOLOv3 model is not perfect, but is good enough. Using the following codes in Cell 06 to replace Cell 05, images from your laptop camera or from a video file would be used for object detection in real-time. You could also record the video processed by the YOLOv3 model. However, there is an issue about video recording. The number 30.0 on line 10 of Cell 06 is a parameter of video frame per second (FPS). From a green digit on the top-left corner of each video frame, you will find that the real FPS of the video recording was about 1 or 2. Because the YOLOv3 model is slow to process images, only a few frames are recorded in an output video file. When the video file is played by a video player with a normal speed, the play speed of the recorded video looks very fast. One solution is to reduce the FPS parameter from 30 to 4, so that you can watch your recorded video normally. The best solution is to use the latest YOLO models. Codes in Cell 07 are for a simplified version of Cell 06, with which video files are not recorded.

![](images/bk978-0-7503-6244-3ch7uf19a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf19b_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf20a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf20b_pr.gif)

### References

Everingham M, Gool L V, Williams C, Winn J and Zisserman A 2012 The PASCAL visual object classes challenge 2012 (VOC2012) results [http://www.pascal-network.org/challenges/VOC/voc2012/workshop/index.html](http://www.pascal-network.org/challenges/VOC/voc2012/workshop/index.html)

Girshick R 2015 Fast R-CNN *Proc. of the IEEE Int. Conf. on Computer Vision* pp 1440–8

Girshick R, Donahue J, Darrell T and Malik J 2014 Rich feature hierarchies for accurate object detection and semantic segmentation *Proc. of the IEEE Conf. on Computer Vision and Pattern Recognition* pp 580–7

Ioffe S and Szegedy C 2015 Batch normalization: accelerating deep network training by reducing internal covariate shift *Int. Conf. on Machine Learning* (PMLR) pp 448–56

Liu W, Anguelov D, Erhan D, Szegedy C, Reed S, Fu C-Y and Berg A C 2016 Ssd: Single shot multibox detector *European Conf. on Computer Vision* (Berlin: Springer) pp 21–37

Redmon J, Divvala S, Girshick R and Farhadi A 2016 You only look once: unified, real-time object detection *Proc. of the IEEE Conf. on Computer Vision and Pattern Recognition* pp 779–88

Redmon J and Farhadi A 2018 Yolov3: an incremental improvement *arXiv preprint* arXiv:[1804.02767](http://arxiv.org/abs/1804.02767)

Ren S, He K, Girshick R and Sun J 2015 Faster R-CNN: towards real-time object detection with region proposal networks *Adv. Neural Inform. Process. Syst.* [**28** 91–9](http://dx.doi.org/10.5555/2969239.2969250)

Roboflow, 2001. Chess Pieces Dataset [https://public.roboflow.com/object-detection/chess-full](https://public.roboflow.com/object-detection/chess-full)

Wang C-Y, Bochkovskiy A and Liao H-Y M 2022 YOLOv7: trainable bag-of-freebies sets new state-of-the-art for real-time object detectors *arXiv preprint* arXiv:[2207.02696](http://arxiv.org/abs/2207.02696)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 8

## YOLOv7, YOLOv8, YOLOv9 and YOLO-World

The subjects covered in this chapter are YOLOv7 and YOLOv8. Because YOLOv8 is easy to install and very fast, readers can just focus on YOLOv8. For a project of reading digits on images in a custom dataset MNIST4yolo constructed in this chapter, the model training time with YOLOv8, YOLOv7 and YOLO-NAS is 0.5, 12 and 4.0 h respectively. Pre-trained YOLOv8 models are used for object detection, image segmentation, image classification, human pose estimation, object tracking and counting.

After Wang *et al* [2022](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8bib2) published their YOLOv7 paper in July of 2023, we have faster and more accurate tools for real-time object detection. We can implement them without writing codes because YOLOv7 source codes can be downloaded and cloned from WongKinYiu's GitHub website to our computers. Kin-Yiu Wong is the first author of the YOLOv7 paper. It is easy to set an environment in VS Code with Python v3.9 by installing libraries and modules listed in a text file named ‘requirements.txt’ from the website. Running the code in a VS Code cell: *!python detect.py --conf 0.4 --nosave --view-img --source 0*, you will see yourself on your computer's screen with a bounding box. Holding a cellphone in front of your camera, you will see two bounding boxes on your screen. If you wanting to save the object detection video to a file, just delete the *\--nosave* option from the code. When you want to terminate the video recording of your camera, just press the ‘q’ key on your keyboard. Replacing number 0 after the source by a video file name with its absolute path, such as *d:/traffic.mp4*, you will see cars with bounding boxes while you are playing the video file downloaded from YouTube. Of course, you can record the video with bounding boxes. On my laptop, YOLOv7 finishes these jobs about 10 times faster than YOLOv3. Changing the source to a single image file name or a batch of image files with an absolute path, such as d:/\*.jpg, you will see objects with bounding boxes on your images. There is a small issue for the image object detection. Images with bounding boxes disappear on your screen too soon. Since the YOLOv7 codes were written in PyTorch, we can open the detect.py file in our VS Code editor. By replacing the waiting time of 1 millisecond in the waitKey() with 3000 millisecond on line 138 of the file, you would be able to watch those images comfortably. You need to changed the waiting time in waitKey() back to 1 millisecond for video, otherwise, your video playing speed will be very slow.

### 8.1 YOLOv7 for object detection for a custom dataset: MNIST4yolo

It is no surprise that we get very good object detection results with YOLOv7 applied to many well-known datasets. We also need YOLOv7 models to have the same ability to give us excellent results for custom datasets. Although Hugging Face, Roboflow and Kaggle provide many free public computer vision datasets, I would like to create and use my own dataset: MNIST4yolo. The resolution of each black and white image in the MNIST4yolo dataset is 448 × 448. The codes in Cells 01–04 of project [8.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn1) can generate samples based on MNIST images for YOLOv7. As usual, Cell 01 is used to import libraries and set hyperparameters for the project. On the last line of Cell 01, A string named ‘xml\_path’ is just a folder name to save files of synthesized images and their plain text files for bounding boxes. Codes in Cell 02 should be familiar to us. From them, we get a MNIST train dataloader and a MNIST test dataloader.

Each batch of a MNIST dataloader has 256 MNIST images which are randomly picked out from a MNIST dataloader. In a 16 × 16 array, a total of 256 MNIST images are used to synthesize a bigger image with a resolution of 448 × 448 for the MNIST4yolov7 dataset. Then using a for-loop starting from line 06 in Cell 03, we mask around 245/256 MNIST images, and only about 10 digits are visible on a synthesized image in the new dataset. The location and the label of each visible MNIST digit are recorded for bounding box information: \[label, x\_c, y\_c, w, h\]. The image width and height of each MNIST image are the same: 28/448. A for-loop in Cell 05 calls the above functions to save 560 bigger images for a training dataset and 80 bigger images for a test dataset respectively. Of course, each image has a text file about bounding boxes. It is not necessary for us to encode those bigger images with their bounding boxes to construct datasets, because a pre-trained YOLOv7 model will take care of this work. Codes in Cells 01–05 should work in Python v3.6. Otherwise, each synthesized image would have a white border around it.

![](images/bk978-0-7503-6244-3ch8uf1_pr.gif)

![](images/bk978-0-7503-6244-3ch8uf2_pr.gif)

 

I created two sub-folders in a folder named ‘MNIST4yolov7’, one is named ‘train’ and the other is named ‘test’. Each of them has two sub-folders: images and labels. The synthesized images and their text files generated in Cell 05 (in the xml\_path folder) were moved to MNIST4yolov7's sub-folders respectively. The MNIST4yolov7 folder are then moved to a YOLOv7 folder cloned from WongKinYiu's GitHub website. Copy a data.yaml file in the YOLOv7 folder and paste it to the train folder of the MNIST4yolov7 folder. The file can be edited by MS Notepad or the VS Code with the following information.

*   train: C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/train/images
*   val: C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/test/images
*   nc: 10
*   names: \['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'\]

While we are training the YOLOv7 model with the custom dataset, the *data.yaml* file provides information about where our images are, the number of classes (nc) and the names of the classes. Open a new VS code terminal with Python v3.9 and change the folder to yolov7 by a DOS command *cd yolov7*, because the pre-trained weight file yolov7.pt is there. Then run the following DOS command to train the YOLOv7 model with the custom data

*   *python train.py --weight yolov7.pt --data MNIST4yolov7/data.yaml --batch-size 4*

There is an issue about the train.py, and many people have searched the internet to find a solution to the issue. For my computer, a solution is to add *os.environ\[“KMP\_DUPLICATE\_LIB\_OK”\] = “TRUE”* after *import os* on line 4 in the *train.py* file in the yolov7 folder. There is another issue which has also caused problems for many people. The default batch size of the model training is 16. My laptop's memory is not big enough, so I reduced the batch size to four. Once the second issue was solved, the long training process started.

The default training epochs are 300. After about 2.3 h of model training, I saw that the training results were bad. The values of the numbers on the diagonal of a confusion-matrix (figure [8.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig1)) were lower. The numbers for digit 3 and digit 5 were even less than 0.4. In an idea result, each number on the diagonal of the confusion-matrix should be equal to one. This means that every ground truth is predicted 100% right. I then used the best weight file *best.pt* from each previous training to train the model six more times and each time the epochs was set to be 200. The final results are shown in figure [8.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig1). The values of the 10 numbers on the diagonal of the confusion-matrix are above 0.9. It took 1.5 h to train the model with 200 epochs. The total training time was about 12 h. With the following command in a VS Code terminal, I got the black and white image with digits shown on the lower-right corner of figure [8.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig1)

*   *python detect.py --weights best6MNIST.pt --conf 0.4 --img-size 448 --view-img --source 0614.jpg*

The trained YOLOv7 model works for the MNIST4yolov7 dataset. Writing digits on paper and changing the source to 0 in the above DOS command, I was surprised that the trained model did not recognize any digits in my handwriting. Then I copied MNIST4yolov7 images to my cellphone and showed an image on my phone screen to the camera of my laptop, the trained model worked well. The Chess dataset is easy to train by the YOLOv7 model. With only in 300 epochs, the training results are very good. From a YouTube video published by Rob Mulla ([www.youtube.com/watch?v=RXbtSwZsoEU](https://www.youtube.com/watch?v=RXbtSwZsoEU)), you can learn more about how to train your own dataset with YOLOv7.

![Figure 8.1. Model training results of a pre-trained YOLOv7 model with the MNIST4yolo dataset. On the blank center of the Recall-Precision curve is a Confusion-matrix. The black and white image in the lower-right corner was obtained by using the last training weight file to detect an image (0614.jpg).](images/bk978-0-7503-6244-3ch8f1_online.jpg)

**Figure 8.1.** Model training results of a pre-trained YOLOv7 model with the MNIST4yolo dataset. On the blank center of the Recall-Precision curve is a Confusion-matrix. The black and white image in the lower-right corner was obtained by using the last training weight file to detect an image (0614.jpg).

### 8.2 YOLOv7 for instance segmentation

Image segmentation is a computer vision task to partition an image or a video frame into different regions or segments. It can be used to help us to understand and analyze the content of the image at a more granular level. There are three kinds of image segmentation. The first one is semantic segmentation which marks all pixels of objects of a same class with the same color, and even pixels of background (sky, grass, trees) on the image are also marked with colors. The second one is instance segmentation which only marks pixels of countable objects on an image, and each object in the same class on the image is distinguished by different mask colors. The third one is panoramic segmentation which is a combination of the above two segmentations. Using libraries from Detectron2, YOLOv7 models can do instance segmentation for us. Detectron2 is the next generation open-source object detection framework from Facebook (Meta AI) Research.

On the website of WongKinYiu's GitHub repository, there is a mask branch. Codes in the mask branch integrate some modules of Detectron2 with YOLOv7. We can download a zip file from the mask branch and unzip the file into a folder named ‘mask’ in our VS Code workspace. The virtual environment for YOLOv7 can be used for the mask codes. We also need to download a zip file from Detectron2's GitHub repository and unzip it into a folder named ‘detectron2’. The *detectron2* folder, the *mask* folder and the *yolov7* folder are on the same level in my VS code workspace. There are many YouTube videos to instruct us how to install Detectron2 on our computers. It is not an easy job, because Visual Studio 2022 is needed to compile some C++ files in the detectron2 folder. On my computer, most issues came from CUDA libraries. After solving issues of Detectron2 installation, we can stand on the shoulders of giants to do some great things. Open a new Jupyter notebook and save it using the name ‘mask’ in the mask folder in your VS code workspace, and then copy the following Cells 01–05 in project [8.2](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn3) to the notebook. Codes from line 04 to 06 in Cell 01 import libraries from files in the *../mask/utils* subfolder. Codes from line 07 to 10 import libraries from files in the *../detectron2* subfolder. A YOLOv7 model is then imported by codes in Cell 02 with pre-trained weights in a file: *yolov7-mask.pt*. From code on line 02 of Cell 02, many hyperparameters are also input from a file *hyp.scratch.mask.yaml*. You can check those parameters by using *print(hyp)* in an extra VS Code cell after Cell 02.

Codes in Cell 03 are used to do instance segmentation for any input image or video frame. These codes came from David Landup ([https://stackabuse.com/instance-segmentation-with-yolov7-in-python/](https://stackabuse.com/instance-segmentation-with-yolov7-in-python/)) and WongKinYiu's GitHub repository with modifications ([https://github.com/WongKinYiu/yolov7/tree/mask](https://github.com/WongKinYiu/yolov7/tree/mask)). Without those codes from the two websites, it is almost impossible to know the model's output data structure (line 10–12 of Cell 03). The ‘ROI Pooling’ module on line 17 is an abbreviation of ‘region of interest pooling’, and comes from Detectron2. The output of Cell 03 is an image with instance segmentation, and the size of the image is the original image size (figure [8.2](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig2)(A)). Codes on line 42–43 in Cell 03 are used to add colorful masks to objects on an image. You can deactivate them by adding a hash tag symbol in front of each of the two lines to see object detection results only (figure [8.2](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig2)(B)). We can re-use the functions in Cells 05–07 of project [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn23) to display YOLOv7's outputs for images in a folder or from video. In those display functions, ‘yolov3’ must be changed to ‘yolov7’. The video frame processing speed of the pre-trained YOLOv7 model is about 20 FPS. There is an issue about the yolov7 function defined in Cell 03, and I found a solution from David Landup’s [YouTube video](https://stackabuse.com/instance-segmentation-with-yolov7-in-python/). We need to deactivate line 157 but keep the line’s “)” in the file “C:\\Users\\xiaoc\\miniconda3\\Lib\\site-packages\\torch\\nn\\modules\\upsampling.py”. Of course, the user’s name in the file path will be different.

![](images/bk978-0-7503-6244-3ch8uf3_pr.gif)

![](images/bk978-0-7503-6244-3ch8uf4_pr.gif)

![Figure 8.2. (A) Instance segmentation of an image. (B) Instance segmentation without masks. The video frame processing speed is about 20 FPS.](images/bk978-0-7503-6244-3ch8f2_online.jpg)

**Figure 8.2.** (A) Instance segmentation of an image. (B) Instance segmentation without masks. The video frame processing speed is about 20 FPS.

### 8.3 Using YOLOv7 for human pose estimation (key point detection)

Human pose estimation is a computer vision task which is used to estimate the positions and orientations of human joints (key points) from images or video frames. There are numerous applications of pose estimation. By tracking the pose of a person over time, it is possible to analyze and recognize specific actions or gestures. Human key points are vital points in our bodies for movements. YOLOv7 traces 18 key points of our bodies. The human nose tip is point 0. The middle point of a line linking two shoulders is point 1. From left to right, six points are on joints of two arms and six points are on joints of two legs. Then two points are for two eyes and two points are for two ears. Usually, pose estimation needs expensive position tracking hardware. There is pose estimation software, such as Google DeepPose and MediaPipe. They work in two stages: person detection and key point detection. YOLOv7 pose is a one-stage multi-person key point detector. In WongKinYiu's YOLOv7 GitHub repository, there is a pose branch for us to download. After Unzipping a downloaded file from the branch to the ‘mask’ folder in our VS Code workspace, we can run a pre-trained key point detection model with a weight file *yolov7-w6-pose.pt* for human key point detection (Maji *et al* [2022](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8bib1)).

Codes on line 02–04 in Cell 01 of project [8.3.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn5) import functions from Python files *datasets.py*, *general.py* and *plots.py* respectively. These files are in the *../mast/utils/* folder. A function defined in Cell 02 loads a YOLOv7 pose model and a pre-trained weight file. If GPU is available, the model will be moved to GPU memory and half floating numbers (float16) will be used to save time. You can print out the model to see the structure of the model, and you can also print the *model.yaml* file to see some of the hyperparameters of the model. The code on line 02 of Cell 03 is used to keep the size of the input image, so the size of the output image with key points can be resized to the original image size by the code on line 18 of Cell 03. The Code on line 03 of Cell 03 uses the *letterbox* function to modify the input image to fit the model. One modification is to resize the input image to 960 × 960. The output of the *process\_img ()* function in Cell 03 is an image with key points. We can re-use Cells 04 and 05 in the last section to display images or video by changing *yolov7* to *process\_img*. An image with processed results is shown in figure [8.3](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig3). The image processing speed of the YOLOv7 pose mode is around 15 FPS, and a pre-trained Detectron2 pose model is around 3 FPS (appendix [F](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-F)).

![](images/bk978-0-7503-6244-3ch8uf5_pr.gif)

![Figure 8.3. Outputs of Cell 03 about a pre-trained YOLOv7 pose model applied to an image. The model's video processing speed is around 15 FPS.](images/bk978-0-7503-6244-3ch8f3_online.jpg)

**Figure 8.3.** Outputs of Cell 03 about a pre-trained YOLOv7 pose model applied to an image. The model's video processing speed is around 15 FPS.

Aarohi Singla has a very helpful [GitHub](https://github.com/AarohiSingla/Detectron2-Tutorial/blob/main/Detectron_fasterrcnn_pretrained_coco.ipynb) repository website to teach people how to use Detectron2. Based on her codes, I was able to import pre-trained Detectron2 models to my PyTorch codes for object detection, instance segmentation, panoptic segmentation and key point detection (codes are listed in appendix [F](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-F)). The image processing speed for object detection, instance segmentation, panoptic segmentation and key point detection are 3, 4, 2 and 3 respectively. Models based on YOLOv7 are faster. There are many other open-source libraries for image segmentation. [Pixellib](https://pixellib.readthedocs.io/en/latest/Image_instance.html) is one of them. With modules imported from Pixellib, codes with only five lines are needed for image and video segmentations, but you have to install tensorflow and keras. I tried to use a Pixellib model with a pre-trained weight file ‘deeplabv3\_xception65\_ade20k.h5’ for video semantic segmentation, and found its image processing speed was about 3 FPS. Using a Pixellib model for image instance segmentation with a pre-trained weight file named ‘mask\_rcnn\_coco.h5’, I saw that masks from the model are not as good as YOLOv7's masks. I also tried [Apache MXNet](https://cv.gluon.ai/tutorials/index.html) for image segmentation. Image processing speed for video with pre-trained models of MNNet libraries is about 1 FPS. Detectron2 provides the best masks for instance segmentation. [CVZONE](https://github.com/cvzone/cvzone) is a computer vision package that makes its easy to run image processing and AI functions. The core of cvzone uses OpenCV and mediapipe libraries. Using the following codes and Cell 07 of project [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn23), we can use a CVZONE pose detector to process video frames from a camera, ant the speed is about 35 FPS.

![](images/bk978-0-7503-6244-3ch8uf6_pr.gif)

### 8.4 Applications of YOLOv8, YOLOv9 and YOLO-World models

#### 8.4.1 Image object detection, segmentation, classification and pose estimation

On January 10, 2023, YOLOv8 was released by Glenn Jocher, the founder of Ultralytics who also launched YOLOv5 a few years ago. Built on the success of previous YOLO versions, YOLOv8 is designed to be faster, more accurate, and easier to use. If you had managed to install YOLOv3 in your computer, you would appreciate the work that YOLOv8 team have done for us. I spent one week compiling YOLOv3's darknet in my computer, because I had to find ways to coordinate VC++, OpenCV, Nvidia CUDA and other third-party software to share their libraries. For YOLOv8, just using a DOS command *pip install ultralytics* in a VS Code terminal, you can install YOLOv8 in a virtual environment of VS Code in a few minutes, depending on your internet speed to download files from YOLOv8 website. There are many models supported by pre-trained parameter files for us to download. Those files are not very big and are easy for people to use. On the home page of YOLOv8, there are detail instructions about how to install Ultralytics and use pre-trained models. DOS command line interface (CLI) of YOLOv8 lets us to train, validate or infer models on various tasks. The following is an example of a DOS code to take video for yourself by using your laptop's camera. Adding an exclamation mark ‘!’ in front of the DOS code, you can even run it in a VS Code cell. If you set the save option in the following DOS command to be True, your video will be saved in a file. I downloaded a traffic video from YouTube and save the video to a file named *d:/traffic.mp4*. Changing the DOS command's source option from 0 to the video file name, I can watch video frames with bounding boxes, labels and probabilities. The video processing speed is about 100 FPS. With YOLOv3 and YOLOv7 models, the speed was 2 and 20 FPS respectively. Changing the source to an image file named *d:/dog.jpg*, you can see object detection results from the pre-trained yolov8 model. However, the image disappears quickly on my computer's screen. Changing the model to 'yolov8n-seg.pt', 'yolov8n-cls.pt', 'yolov8n-pose.pt' and other pre-trained models, we can use the single line code for instance segmentation, image classification and pose estimation. An alphabet following yolov8 in a model's name could be *n*, *s*, *m*, *l* and *x* to denote the size of a pre-trained YOLOv8 mode from nano, small, medium, large to extreme large respectively.

*   *yolo task=detect mode=predict model=yolov8n.pt source=0 conf=0.25 iou=0.5 conf=0.15 show=True save=False*

It is more flexible to use YOLOv8 models in a Python environment of VS Code. Just using codes in 7 lines, the following project [8.4.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn7) could also be used for object detection, image semantic segmentation, image classification and pose estimation by changing the name of the pre-trained model on line 04 of Cell 01. Those models were trained with MS COCO dataset. Deleting \[2030:2040\] from line 05 in Cell 02, you would display all 17,125 VOC images one by one. It takes a long time to watch the slide-show. You can terminate the program at any time by pressing the Esc key on your keyboard, but be sure to let your computer to focus on the image window by click your mouse on the image window. By default, each image will be shown in 1000 milliseconds set by an option of the waitKey() on line 08. To accelerate the slid show, you can press any key (such as the space bar) other than the Esc key. Some objects ignored by yolo8n.pt could be detected by yolo8l.pt. Changing the code on line 04 of Cell 01 to ‘yolov8 = YOLO(‘yolov8n.pt’).track’, you would see each detected object on an image has an ID number. However, the object tracking function does not work for classification models. In February of 2024, Chien-Yao Wang and his collaborators (Wang *et al* [2024](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8bib4)) released YOLOv9 which was built on top of YOLOv7. After upgrading Ultralytics to the latest version (v8.1.24), I can test a pre-trained a YOLOv9 model by running codes in Project 8.4.1 by replacing 'yolov8n.pt' with 'yolov9c.pt' on line 04 of Cell 01. The video processing speed of the YOLOv9 model is 25 FPS. I also tested a pre-trained YOLO-World model 'yolov8s-world.pt' and found that its video processing speed was about 50 FPS. YOLO-World (Cheng *et al* [2024](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8bib3)) models enable us to detect any object within an image based on descriptive texts. Codes on line 05-6 are used for the YOLO-World model. A string list in line 06 is for the descriptive texts which instructs the model to find objects listed in the string list.

![](images/bk978-0-7503-6244-3ch8uf7_pr.gif)

#### 8.4.2 Object counting on an image or a video frame

In project [8.4.2](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn8), YOLOv8 models are used to count objects detected on a single image or video frame. An image in a NumPy array is used as a source of a YOLOv8 model in a function named ‘yolov8’ (line 06). You could use the code on line 07 to replace the code on line 06 to assign an object ID number to each detected object, and would find that many objects were not detected. It is convenient for us to obtain bounding box information from outputs of a YOLOv8 model (lines 08–10). Codes on lines 11–13 counter numbers of objects in a category of COCO dataset. The counting result is a dictionary using object names as its keys, and object numbers as its values. The dictionary is then converted to a text string by codes on lines 14–16. This string is then printed on the bottom of the image. The coordinates (*x*1, *y*1) and (*x*2, *y*2) of a bounding box are absolute pixel values relative to the top-left corner of an input image. We are able to write our own codes to add bounding boxes, class indices and probabilities on images. Codes in Cell 02 display a single image (figure [8.4](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig4)) with bounding boxes obtained by the pre-trained YOLOv8 model *yolov8l.pt*. On the bottom of the image, you will see that six kinds of objects were detected. Change the pre-trained model on line 02 to see the difference in object counting. We can re-use codes in Cells 05–07 of project [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn23) to display counting results for images from a folder or from video frames. The video processing speed of model 'yolov8n.pt' and 'yolov8l.pt' is 80 and 25 FPS respectively.

![](images/bk978-0-7503-6244-3ch8uf8_pr.gif)

![Figure 8.4. Object detection/counting by a pre-trained YOLOv8 model for an image. Video process speed is about 80 FPS.](images/bk978-0-7503-6244-3ch8f4_online.jpg)

**Figure 8.4.** Object detection/counting by a pre-trained YOLOv8 model for an image. Video process speed is about 80 FPS.

#### 8.4.3 Car tracking and counting for a video file

Object tracking and counting refer to processes of locating and monitoring objects in a video or an image sequence and then counting the number of objects belonging to a class of interest. Object tracking and counting find applications in many domains, such as surveillance, traffic monitoring, people counting, retail analytics, sports analysis, and wildlife monitoring, etc. There are three steps for this kind of computer vision task. The first one is object detection by YOLO or other object detection algorithms. The second is object tracking, and its aim is to associate objects detected in the current frame with the previously tracked objects on the previous frame. The final step is object counting. Applying the codes of the following project [8.4.3](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn9) to a video file, we will track and count cars running in opposite directions separately. Trucks running beside cars will be ignored in the video. The project codes are inspired by FREEDOM TECH's [YouTube](https://www.youtube.com/watch?v=DXqdjWndooI) and his [GitHub](https://github.com/freedomwebtech/yolov8counting-trackingvehicles/blob/main/tracker.py) repository.

![](images/bk978-0-7503-6244-3ch8uf9_pr.gif)

 

Before being processed by a pre-trained YOLOv8 model, each video frame is resized to 1024 × 512. A processed video frame shown in figure [8.5](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig5) is about vehicles running on a highway. The left-hand-side vehicles are moving towards the camera taking the video, and their directions are down: from the top to the bottom of the frame. The right-hand-side vehicles are moving away from the camera, and their directions are up: from the bottom to the top of the frame. Codes in Cell 01 import libraries and a small pre-trained YOLOv8 model. Seven hyperparameters are also set in the cell as usual. Two of them on line 03 and 04 set the *y*\-axis locations of a green line and a red line as shown in the figure. Corresponding to the green line's position at *y*\=340, a green zone on the frame with 340-dy ⩽ *y* ⩽ 340+d*y* is a detection zone for cars running up, where dy is set to be 6 pixels by a code on line 05. Also, the red line at *y*\=370 sets a red zone of the same size area to detect cars running down. Other four hyperparameters will be explained later.

![](images/bk978-0-7503-6244-3ch8uf10_pr.gif)

![Figure 8.5. Traffic tracking and counting for cars running down and up on video frames separately. The video file (∼9 MB) came from my cellphone at a crossing of highway 1 and 36 St of North East of Calgary, Canada.](images/bk978-0-7503-6244-3ch8f5_online.jpg)

**Figure 8.5.** Traffic tracking and counting for cars running down and up on video frames separately. The video file (∼9 MB) came from my cellphone at a crossing of highway 1 and 36 St of North East of Calgary, Canada.

We have to start to explain codes of the project from the last cell: Cell 04 which is almost the same as Cell 07 of project [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn23). Codes in this cell read a video file frame by frame. After a frame is processed by a function defined in Cell 03, information is added to the processed frame as shown on the above figure. The digit on the lower-left corner of the figure is the number of cars running down from the time of frame 0 to the time of current frame, and the digit on the lower-right corner is the number of cars running up. When a car is in a detection area, its bounding box center will be marked by a white dot, and its ID number will be shown beside the white dot. The color of the ID number is the color of the horizontal line for the detection zone. The top-left corner shows the image processing speed with a big variance. When there is no vehicle on the road, we may get a ‘divided by zero’ error. A small number (10^(−5)) is used in FPS calculations to prevent this issue. The current frame's sequence number and the total frames of the video are shown on the top-right corner of the figure. At the time of frame 140/572 as shown in the figure, four cars had been found running up and two cars had been found running down. The image processing speed of the model was 57 FPS. At that moment, a black car with ID 229 was running down and was in the red zone.

![](images/bk978-0-7503-6244-3ch8uf11_pr.gif)

 

The name of the function defined in Cell 03: *yolov8tc* means that the function based on a pre-trained YOLOv8 model is used for object tracking and counting. The function is a modification of the yolov8 function defined in Cell 01 of project [8.4.2](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn8). A code on line 02 resizes an original video frame into a new frame to a size of 1024 × 512. The new frame is then processed by the YOLOv8 model to get each object's bounding box coordinates (boxes), and the bounding box's COCO class identity number (labels). We use codes on line 07–11 to pick out cars and pack four coordinates of each car's bounding box into a list which is then appended to a list named ‘car\_list’. A bounding box's four coordinates are for the box's top-left corner (*x*,*y*) and the lower-right corner (*X*,*Y*). On line 12 of Cell 03, the car list is processed by a function of an instance of a class Tracker defined in Cell 02, and the output of the track function is still a list named ‘cxcyid’. The input list and the output list have the same length. However, each list inside the output list *cxcyid* has three elements: two center coordinates of a bounding box and an ID number assigned by the Tracker class. The two center coordinates are obtained by the two formulae: *cx=int((x*+*X)/2)* and *cy=int((y+Y)/2)*. The Tracker is smarter enough to know if an object detected on the current frame was on the previous frame. If a car is new object on the current frame, it will be assigned a bigger ID number assigned by the Tracker.

On the current frame, we know each car with an ID number and its center coordinates. Codes on line 13–30 are used to check *y*\-axis positions of cars. If a car is in the green zone (code on line 15), we will mark it with a white dot and print its ID number beside the dot on the current frame. The car is then registered in a dictionary named ‘vh\_down’ for cars running down. For a car whose ID in the vh\_down dictionary touches the red zone, and the car's ID is new (code on line 21) to a list named ‘n\_down’, the car's ID will be appended to the list. The length of the list is the number of cars running down from the time of frame 0 to the time of current frame. In the same way, the number of cars running up can also be obtained by codes on line 23 to 30. We then print the two numbers on the two lower corners of the frame as shown in the figure. Also, two lines for the green and red zones are printed on the frame. The function yolov8tc returns a frame with the above information.

![](images/bk978-0-7503-6244-3ch8uf12a_pr.gif)

![](images/bk978-0-7503-6244-3ch8uf12b_pr.gif)

 

When we use a code on the last line of Cell 02 to define an instance of the class Tracker, the instance is initialized by an empty dictionary named ‘center\_points’ and a scalar named ‘id\_count’. A code on line 12 of Cell 03 only calls the instance's function ‘tracker.update()’ to process the current video frame. Center coordinates of cars on the previous frame are kept in center\_points, and the maximum ID number on the previous frame was increased by 1 and saved in the *id\_count*. Suppose the pre-trained YOLOv8 model found three cars on the first frame, and the tracker.update() function is used to process the car list. In a for-loop starting from line 07 of Cell 02, the first car's center points are obtained at first, and the car's same object detected property is set to be False. Since the center\_points dictionary is empty at the time of the first frame, codes from line 12 to line 18 are skipped. The first car will be assigned with an ID number 1 by a code on line 20, and the *id\_count* will be 2 then. Now the *center\_points* dictionary has one element {1: (cx1, cy1)}, and the center\_ids will be \[\[cx1, cy1, 1\]\].

We are still in the loop started from line 07 to calculate the second car's center. A sub-loop starting from line 12 to line 18 checks the Euclidean distance between the second car and the first car. If the distance is less than 35 pixels, the two cars are the same object. If they are not the same, the second car will be assigned with an ID number 2, and the *center\_points* will have two elements {1: (cx1, cy1), 2:(cy2, cy2}}. After the third car is processed, we have the center\_points {1: (cx1, cy1), 2:(cx2, cy2), 3:(cx3,cy3)} if their distances are longer than 35, and the id\_count is 4. Occasionally, the distance between two cars is shorter than 35, so they have a same ID number. Codes from line 23 to 28 are used to keep only the latest car from many cars with a same ID number.

While the yolov8tc function is processing the second frame, the tracker.update() function will be called again. The *center\_points* dictionary and the *id\_count* scalar obtained from the first frame are kept in the *\_\_int\_\_()* function of the Tracker class. They are used for processing of the second frame. If the second frame only has the same three cars and each of them move a distance less than 35 pixels, the Tracker's update function will identify each of the three cars with an old ID number on the first frame. The *id\_count* will not be changed (=4), but the *center\_points* dictionary for the three cars will be updated. In a condition that a car's moving distance is longer than 35 pixels in the time interval between two frames, the car will be assigned a new ID as a new object. But this is not right. The number 35 is a critical distance, a hyperparameter for the project. It is dependent on camera resolutions and many other hardware settings. Codes for a new version of project [8.4.3](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn9) are listed in appendix [G](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-G). Codes in the new version can detect running objects in multiple COCO classes. Each object's COCO class label (an integer) detected by YOLOv8 is registered in the car list on line 07 of Cell 03 for codes of the new version. With the extra information, it is possible for us to count cars and trucks simultaneously.

#### 8.4.4 Fine tuning YOLOv8 for objection detection and annotation for a custom dataset

YOLOv8 and YOLOv7 models use the same format of annotation files, and even a yaml file of the MNIST4yolo dataset can be used for both of them. Using codes in the following project [8.4.4](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn13), we will implement the pre-trained *yolov8n.pt* model to the MNIST4yolo custom dataset. In model training with 100 epochs, codes on lines 03–04 are deactivated by adding a hash tag # in front each of them. Model training finished in 20 min, and a best trained model was saved in the path shown on line 04. This trained model could be used for the next 100 epochs by removing the hash tags in front of line 03–04, and adding a hash tag in front of line 02. But no more model training is needed. I was surprised to get very good results (figure [8.6](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig6)) just in 20 min. Those results shown in figure [8.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig1) from YOLOv7 took 12 h of model training for the same dataset.

![](images/bk978-0-7503-6244-3ch8uf13_pr.gif)

![Figure 8.6. Fine tuning a YOLOv8 model for the MNIST4yolo dataset. On the blank center of the Recall-Precision curve is a confusion-matrix. The black and white image on the lower-right corner was obtained during model training.](images/bk978-0-7503-6244-3ch8f6_online.jpg)

**Figure 8.6.** Fine tuning a YOLOv8 model for the MNIST4yolo dataset. On the blank center of the Recall-Precision curve is a confusion-matrix. The black and white image on the lower-right corner was obtained during model training.

The trained YOLOv8 model is very useful. In case we have 10 000 images we manually label 1000 images, and train a YOLOv8 model by the 1000 images. Then using the trained YOLOv8 model in the following Cells 2–3, we can automatically label the remaining 9000 images. A test image and its annotation table shown in figure [8.7](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig7) are outputs of Cell 03. The annotation table is predicted by the trained YOLOv8 model. Although the predicted and the ground truth are a little different, we can see that the prediction is very good, based on the bounding boxes on the left image of figure [8.7](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8fig7).

![](images/bk978-0-7503-6244-3ch8uf14a_pr.gif)

![](images/bk978-0-7503-6244-3ch8uf14b_pr.gif)

![Figure 8.7. Using a trained YOLOv8 model to annotate the MNIST4yolo test dataset. (Left) A test image with predicted bounding boxes. (Right) A table of the predicted bounding boxes (x and y are coordinates of a bounding box's top-left corner; w and h are weight and height of the bounding box; the ground truth w=h=0.625).](images/bk978-0-7503-6244-3ch8f7_online.jpg)

**Figure 8.7.** Using a trained YOLOv8 model to annotate the MNIST4yolo test dataset. (Left) A test image with predicted bounding boxes. (Right) A table of the predicted bounding boxes (*x* and *y* are coordinates of a bounding box's top-left corner; *w* and *h* are weight and height of the bounding box; the ground truth *w*\=*h*\=0.625).

We still need to label some images of our own datasets. I found that [labelImg](https://github.com/HumanSignal/labelImg#Hotkeys) is a very useful tool for image annotation. This tool was created by Tzutalin with the help of dozens of contributors. It is free software under MIT license. In a VS Code terminal running a DOS code: *pip install labelImg*, you can install the software in your computer in a few seconds. Then in the terminal running another DOS code: *labelImg*, you can use the software in a window interface. In June 2023, we have a new library tool Autodistill to label images automatically for YOLOv8. It is a Python package which allows us to transfer the knowledge of large foundation models to smaller models for building AI applications running in real-time. To use Autodistill, I tried a Roboflow project for milk bottle detection in Google Colab. Even 16 GB GPU memory in a Tesla T4 was not big enough to run the codes of the project.

In May 2023, Deci AI released YOLO-NAS models for object detection. The abbreviation NAS denotes ‘Neural Architecture Search,’ a technique invented by Deci to automate the design process of neural network architectures. On the GitHub repository of Deci/super-gradient, it is claimed that ‘The new YOLO-NAS delivers state-of-the-art (SOTA) performance with the unparalleled accuracy-speed performance, outperforming other models such as YOLOv5, YOLOv6, YOLOv7 and YOLOv8.’ SuperGradients is a PyTorch-based training library. Based on SuperGradients, Deci provides three pre-trained models: yolo\_nas\_s, yolo\_nas\_m, and yolo\_nas\_l under an open-source license with pre-trained weights available for non-commercial use. We can use ‘pip install super-gradients’ to install SuperGradients in a virtual environment of VS Code with Python v7-9 and PyTorch 1.9-1.10. The object detection speed of using the small, middle and large size model is 15, 10 and 10 PFS, respectively. From the last section, we know that the speed of model ‘yolov8n.pt’ and model ‘yolov8l.pt’ is 80 and 30 FPS, respectively. It is a surprise that YOLO-NAS is slower than YOLOv8 on my computer. A YouTube video from Nicolai Nielsen also shows that YOLOv8 is faster than YOLO-NAS. Inspired by codes from Aarohi Singla and Roboflow, I could write my codes to fine-tune the large YOLO-NAS model for my MNIST4yolov7 dataset. Model training of 100 epochs took more than four hours. YOLOv8 model's training time was 0.3 hour for 100 epochs, and codes for YOLOv8 model training were only a few lines. I do not show codes for fine-tuning the large YOLO-NAS model because they are very long.

### References

Maji D, Nagori S, Mathew M and Poddar D 2022 YOLO-pose: enhancing YOLO for multi person pose estimation using object keypoint similarity loss *Proc. of the IEEE/CVF Conf. on Computer Vision and Pattern Recognition* pp 2637–46

Wang C-Y, Bochkovskiy A and Liao H-Y M 2022 YOLOv7: trainable bag-of-freebies sets new state-of-the-art for real-time object detectors *arXiv preprint* arXiv:[2207.02696](http://arxiv.org/abs/2207.02696)

Cheng T, Song L, Ge Y, Liu W, Wang X and Shan Y 2024 YOLO-World: Real-time open-vocabulary object detection arXiv preprint arXiv:[2401.17270](http://arxiv.org/abs/2401.17270)

Wang C-Y, Yeh I-H and Liao H-Y M 2024 YOLOv9: Learning what you want to learn using programmable gradient information arXiv preprint arXiv:[2402.13616](http://arxiv.org/abs/2402.13616)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 9

## U-Nets for image segmentation and diffusion models for image generation

A U-Net is a kind of ResNet with a special architecture which is easy to train and needs few training samples. In section [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-1), a U-Net is used for retinal vessel segmentation. A WGAN-GP code using the U-Net as an image generator for the same task is listed in appendix [H](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-H). Hugging Face's pre-trained diffusion models based on U-Nets were used to generate photorealistic images for an Oxford flower dataset in section [9.3](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-3). The mathematical principle is explained using codes to generate quadratic curves in section [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-2). Using Hugging Face's Stable Diffusion models, we can even instruct a computer to generate beautiful images according our text prompts.

YOLOv8 is very powerful for object detection and segmentations, but those objects must be countable. Many objects such as blood vessel systems in our bodies and river systems on Earth have fractal structures. To segment images obtained from microscopes or satellites about uncountable objects with fractal structures, we can use a U-Net, a residual convolutional network proposed by Olaf Ronneberger, Philipp Fischer, and Thomas Brox in their paper (Ronneberger *et al* [2015](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib6)) published in 2015. The title of the paper is ‘U-Net: Convolutional Networks for Biomedical Image Segmentation’. The U-Net architecture has proven to be effective in various image segmentation tasks, especially when the available training data is limited. With less than 100 images to train a U-Net, we could quickly get excellent segmentation results. It allows for accurate and detailed segmentation results, capturing both local and global information in images. U-Nets are also used in diffusion models for image generation. The fake images from diffusion models are of photorealistic quality.

### 9.1 Retinal vessel segmentation by a U-Net for DRIVE dataset

The DRIVE Dataset is used to demonstrate the super power of a U-Net. The name of the dataset is an abbreviation of digital retinal images for vessel extraction (DRIVE). The dataset was introduced by Joes Staal *et al* in their paper (Staal *et al* [2004](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib7)) titled ‘Ridge-based vessel segmentation in color images of the retina’. We can download a zip file of the dataset from Kaggle. The size of the compressed file is less than 30 MB. After unzipping the file to a folder named ‘d:\\Retina’, we can find a ‘training’ sub-folder and a ‘test’ sub-folder. Each of the two sub-folders has an ‘images’ sub-folder containing 20 TIF color fundus images (figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(A)). The resolutions of all the color images are the same: 565 × 584 pixels with eight bits per channel (three channels). According to Staal, these images were obtained from a diabetic retinopathy screening program in the Netherlands, and 7 out of 40 images are about abnormal pathology cases. In the training sub-folder, there is a folder named ‘1st\_manual’ with 20 black and white GIF images (figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(B)). They were manual segmentation results by an ophthalmological expert, and were used as ground truth for model training. From the images shown in figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1), we have an idea about what we should to do with these images: to generate black and white images of blood vessels from those color fundus images automatically by a U-Net (figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(C)) in the following project [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn2). The U-Net architecture has several key features:

*   The contracting path (the left-hand-side of figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(C)) consists of a series of convolutional and pooling layers that progressively reduce the spatial resolution while increasing the number of feature channels. This path captures the context and extracts high-level features from the input image.
*   The expanding path (the right-hand-side of figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(C)) consists of a series of transposed convolutional and convolutional layers that increase the spatial resolution while decreasing the number of feature channels. It combines the low-level features from the contracting path with the high-level features to generate detailed segmentation maps.
*   Skip connections (the horizontal arrows in figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(C)) between the corresponding layers in the contracting and expanding paths enable the network to use both local and global information for accurate segmentation. The skip connections are residual connections.
*   Final layer: the last layer of the U-Net is a 1 × 1 convolutional layer.

As usual, we import libraries and set all hyperparameters in Cell 01 of project [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn2). A class defined in Cell 02 is used to pack images into a train dataset and a validation dataset. Only having 20 images in the train dataset for model training, we have to do many image augmentations: resize, rotation, horizontal flipping, vertical flipping and normalizations. The color image shown in figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(A) was vertically flipped, because a small color bulge on each original color image is at the position of 1:30 of an analog clock. The mask image of each color image should have the same augmentations. Codes starting from line 11 in Cell 02 do augmentations for both the color images and their masks simultaneously. The two datasets are then sliced into two dataloaders by codes in Cell 03. Codes in Cell 04 display a batch of images in the train dataloader. Because the image resolution is higher (512 × 512) in DRIVE, my computer can only handle a dataloader with a batch size of two.

![Figure 9.1. A color fundus image (A) and its mask (B) (cropped outputs of Cell 04). (C) The architecture of a U-Net.](images/bk978-0-7503-6244-3ch9f1_online.jpg)

**Figure 9.1.** A color fundus image (A) and its mask (B) (cropped outputs of Cell 04). (C) The architecture of a U-Net.

The architecture of the U-Net used for the project is shown in figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(C). It is a little different from Olaf Ronneberger's U-Net (Ronneberger *et al* [2015](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib6)) in which batch normalization (Ioffe and Szegedy [2015](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib2)) was not used because this operator was not invented at that time. The input of the U-Net is a batch of color images with the shape N × 3 × 512², and the output of the U-Net is a batch of black and white images with the shape N × 1 × 512², where N is the batch size. The output images will be forced to match with masks of those color images by a BCE loss function with logits during model training. In PyTorch, this loss function ‘combines a Sigmoid layer and the BCE Loss in one single class. This version is more numerically stable than using a plain sigmoid followed by a BCE Loss as, by combining the operations into one layer, we take advantage of the log-sum-exp trick for numerical stability.’ Codes in the ExtraCell ONE are used to demonstrate how to calculate values of the loss function automatically and manually by the formula $L = - \\frac{1}{N}\\sum\\limits\_{i = 1}^{N}\\left\\lbrack {y\_{i}\\ \\ln(\\sigma{({\\widehat{y}}\_{i})}) + (1 - y\_{i})\\ln(1 - \\sigma{({\\widehat{y}}\_{i})})} \\right\\rbrack$inline-graphic style="height:3.25em;" xlink:href="bk978-0-7503-6244-3ch9ieqn1.gif"/.

![](images/bk978-0-7503-6244-3ch9uf1_pr.gif)

 

The rectangles with different colors and sizes in figure [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig1)(C) represent image data of different shapes, and the arrows with different colors represent operators to the image data. The width of each rectangle is proportional to channels of every batch of processed image data, and the height of each rectangle is proportional to the resolution of the batch of processed image data. Images in the datasets are resized to the same widths and heights, and we define the size of these images as their width or height (line 13 of Cell 01). There are four encoders (E1 to E4) on the left side of the U-Net, and four decoders (D1 to D4) on the right side of the U-Net. Each encoder has one input and two outputs. For example, encoder E4's output skip4 will be used as an input for decoder D1, and another output of E4 is p4: the results of a 2 × 2 MaxPool2d operator acted on a copy of skip4. The second output of E4 is then used as an input for the bridge which connects with decoder D1.

Each decoder has two inputs and one output. For example, decoder D1's first input is skip4 with the shape N×512 × 64², its second input is b: the bridge's output with the shape N×1024 × 32². Decoder D1 first acts on the second input by a transposed convolution operator, so that the output shape of the transposed convolution matches with the shape of the first input's shape for a concatenation along the channel direction. The result of the concatenation is a tensor with the shape N×1024 × 64². The tensor is then processed by a basic block to get up1: D1's output with the shape N×512 × 64². From a Basic class defined in Cell 06, you can see that each basic block has two convolution layers. The basic block will change its input’s channels not its input's resolution. In the four encoders and the bridge, the basic block increases the image channels; in the four decoders, the basic block decreases the image channels. The four MaxPool2d operators in the four encoders halve image sizes. Using the four transposed convolutions in the four decoders, we get the resolution of the U-Net's output to match the input image's resolution. The channels of U-Net's output image could be any integers set by ourselves for our projects. For example, if our project is used to segment 10 objects in images of a dataset, the channels of the output image from our U-Net would be 10, and we must use a cross entropy loss function for model training.

![](images/bk978-0-7503-6244-3ch9uf2_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf3_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf4_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf6a_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf6b_pr.gif)

 

Using the functions defined in Cell 07 and 08, I trained the U-Net to segment blood vessels from those fundus images. The training results puzzled me for a few months; the results I got at that time are shown in figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(D). You can see that many tiny vessels could not be found in figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(D), compared with the ground truth shown in figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(B). I tried to use a residual net in the basic block, added one more encoder to the contracting path, and one more decoder to the expanding path, but I still could not see any significant improvement for my model. Then I tried to use the U-Net as a generator in a WGAN-GP. In the WGANs in Chapter [5](#Chapter_5.xhtml#bk978-0-7503-6244-3ch5), our generator creates images from noises. In the WGAN U-Net, the generator generates black and white images from color fundus images. I got a very good result shown in figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(F) (WGAN-GP codes are listed in appendix [H](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-H)). To compare the outputs of my U-Net and my WGAN-GP U-Net, I shifted pixel values of the U-Net's output images linearly (figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(C)) and nonlinearly (sigmoid, figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(E)). WGAN-GP U-Net took 100 min for model training, but we did not really need it because figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(E) is better than figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(F). It seems that figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(C) is the best (model training time 25 min). The U-Net model training metrics are shown in figure [9.3](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig3).

![Figure 9.2. Vessel segmentation results of the U-Net. (A) a color fundus image in the valid dataset. (B) Ground truth. (C) Pixel values of the U-Net's output were linearly shifted to \[0,1\]. (D) The U-Net's output was displayed by VS Code with automatic clipping. (E) Pixel values of the U-Net's output were shifted to \[0,1\] by a sigmoid function. (F) The output of a WGAN-GP using the U-Net as an image generator.](images/bk978-0-7503-6244-3ch9f2_online.jpg)

**Figure 9.2.** Vessel segmentation results of the U-Net. (A) a color fundus image in the valid dataset. (B) Ground truth. (C) Pixel values of the U-Net's output were linearly shifted to \[0,1\]. (D) The U-Net's output was displayed by VS Code with automatic clipping. (E) Pixel values of the U-Net's output were shifted to \[0,1\] by a sigmoid function. (F) The output of a WGAN-GP using the U-Net as an image generator.

![Figure 9.3. U-Net training metrics corresponding to sigmoid shift of figure 9.2(E).](images/bk978-0-7503-6244-3ch9f3_online.jpg)

**Figure 9.3.** U-Net training metrics corresponding to sigmoid shift of figure [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig2)(E).

### 9.2 Using an attention U-Net diffusion model for quadratic curve generation

Starting from noises, a denoizing diffusion probabilistic model (DDPM) can generate images, audios and even videos with good enough quality to fool us. A DDPM system is a type of generative model introduced by Jonathan Ho, Ajay Jain, and Pieter Abbeel in their paper (Ho *et al* [2020](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib1)) published in 2020. DDPMs are trained to find a conditional distribution function of clean images given noises and then to use the conditional distribution function for denoising tasks. The principle of DDPM is easy to understand. Suppose you have an image of the Mona Lisa at the bottom of a tank with clean water and you add black ink drop by drop to water in the tank. The ink drop is tiny, and the time interval between two drops is long enough to let each ink drop diffuse thoroughly in the tank. Drop by drop, your picture will be noised by the ink pigments, and finally at drop 1000, you picture disappears. This is a forward process. Then we use an advanced tool to take the ink out of the tank drop by drop. When all 1000 ink drops are removed from the water in the tank, we can see the Mona Lisa clearly again. This is a reverse process or denoising process. An advanced tool for image generation in the reverse process of DDPM is a U-Net model. After the model is trained with images in a dataset, the model can generate fake images from pure noises. These fake images are not the original images in the dataset, but are in the same style as the original images. For example, if you train your U-Net model with Pablo Picasso's paintings, you will obtain fake images in Picasso's painting style. Denoising diffusion probabilistic models have shown promising results in image denoising tasks. They provide a probabilistic framework for noise removal, allowing for effective handling of various types of noise and producing visually pleasing denoised images.

#### 9.2.1 The forward process in a DDPM

An original image *x*[0] (a quadratic curve or a digital Mona Lisa image) is a sample with an unknown PDF *q*: *x*[0]∼*q*(*x*). In a forward process or diffusion process, noises from a standard normal distribution are added to *x*[0] to get a latent image *x*[1] with a conditional PDF: *q*(*x*[1]*∣x*[0]). This forward process is going on step by step based on a variance schedule 0<*β*[1]<*β*[2]<⋯<*β*[*T*]≪ 1. The variance schedule could be linear, quadratic, cosine, etc, just like a learning rate schedule. If the time step *T* is big enough (∼1000), our final image *x*[*T*] would be an isotropic Gaussian noise: *q*(*x*[*T*]*∣x*[*T*−1]) = *N*(*x*[*T*];0,*I*). All the latent images *x*[1], …, *x*[*T*] have the dimensionality of the original image *x*[0]. At time step *t*, a latent image is obtained by $x\_{t} = \\sqrt{1 - \\beta\_{t}}x\_{t - 1} + \\sqrt{\\beta\_{t}}\\varepsilon$inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch9ieqn2.gif"/, where *ε* is a sample from a multivariant standard normal distribution *N*(0,*I*) with the dimensionality of *x*[0]. The PDF of the latent image at time step *t* is a normal distribution given by a latent image at a previous time step *t*−1

  
$$q(x\_{t}\\mid x\_{t - 1}) = q(x\_{t}\\mid x\_{t - 1},x\_{0}) = \\mathbb{N}(x\_{t};\\sqrt{1 - \\beta\_{t}}x\_{t - 1},\\beta\_{t}I)$$  
(9.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn3.gif" position="float"/

We know that the combination of two independent normal distributions is still a normal distribution. If the two independent normal distributions are *x* ∼ ℕ(*x**;*0,*σ*[1]²)inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch9ieqn4.gif"/ and *y* ∼ ℕ(*y**;*0,*σ*[2]²)inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch9ieqn5.gif"/, then we have *z* = *x* + *y* ∼ ℕ(*z**;*0,(*σ*[1]²+*σ*[2]²))inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch9ieqn6.gif"/. From that fact and with *α*[*t*] = 1 − *β*[*t*]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch9ieqn7.gif"/, ${\\overline{\\alpha}}\_{t} = \\prod\\limits\_{i = 1}^{t}\\alpha\_{i}$inline-graphic style="height:3.1875em;" xlink:href="bk978-0-7503-6244-3ch9ieqn8.gif"/, the latent image $x\_{t} = \\sqrt{{\\overline{\\alpha}}\_{t}}x\_{0} + \\sqrt{1 - {\\overline{\\alpha}}\_{t}}\\varepsilon$inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch9ieqn9.gif"/ at time step *t* can be directly obtained from *x*[0] by a PDF:

  
$$q\\left( {x\_{t}\\mid x\_{0}} \\right) = \\mathbb{N}\\left( {x\_{t};\\sqrt{{\\overline{\\alpha}}\_{t}}x\_{0},\\left( {1 - {\\overline{\\alpha}}\_{t}} \\right)I} \\right)$$  
(9.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn10.gif" position="float"/

The diffusion process is a Markov chain with an approximate posterior possibility distribution function shown in equation ([9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn2)). At the end of the forward process, we get *x*[*T*] ∼ *q*(*x*[*T*]∣*x*[0]) = ℕ(*x*[*T*];0,*I*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch9ieqn11.gif"/, a pure noise.

  
$$q(x\_{1:T}\\mid x\_{0}) = \\prod\\limits\_{t = 1}^{T}{q\\left( {x\_{t}\\mid x\_{t - 1}} \\right)} = q(x\_{T}\\mid x\_{T - 1})\\ldots q(x\_{2}\\mid x\_{1})q(x\_{1}\\mid x\_{0})$$  
(9.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn12.gif" position="float"/

 

The quadratic curves in figure [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(A) are used as original images to demonstrate DDMP's power to generate images from noise in project [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn7). Four thousand batches of quadratic curves are used to train a U-Net model in a DDMP system. A batch of quadratic curves in figure [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(A) were generated by codes in Cells 01–03; these codes have been used many times in the previous chapters. There are 64 curves in a batch, and there are 64 points on each curve. A function for the forward process is defined in Cell 04. Hyperparameters for the function are set in front of this function. The total forward steps are set to be *T* = 200 for this simple project. A time embedding dimension for model training is set to be 100 on line 2 of Cell 04. With a linear schedule, betas increase from 0.001 to 0.2 in 200 steps (line 03 in Cell 04). Many other hyperparameters are also listed there, such as *α*, $\\overline{\\alpha}$inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-6244-3ch9ieqn13.gif"/, $\\sqrt{\\overline{\\alpha}}$inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch9ieqn14.gif"/, and $\\sqrt{1 - \\overline{\\alpha}}$inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch9ieqn15.gif"/. Only one original curve is used to add noises at time step *t* = 1, 25, 50 and 199 for us to see the forward process in figure [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(B). At the end of the process, ${\\overline{\\alpha}}\_{199}$inline-graphic style="height:1em;" xlink:href="bk978-0-7503-6244-3ch9ieqn16.gif"/ = 4.2 × 10^(−10). According to equation ([9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn2)), the contribution of the original image to the last latent image *x*[199]inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch9ieqn17.gif"/ can be ignored. Only a standard Gaussian noise *ε* exists in the last latent image. From an empirical rule, we know that 99.7% of the Gaussian noise values lie withing three standard deviations. That is why the values of *x*[199] are between −3 and 3 along the *y*\-axis in figure [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(B). In the q\_sample function defined in Cell 04, a Pytorch function gather() is new to us. Running the following codes in an e*xt*ra VS code cell, you will know how the function picks out elements in a 1D tensor *z* according to another 1D tensor *t*: *z = torch.tensor(\[1, 2, 3, 4, 9\]); t = torch.tensor(\[2, 0\]); z.gather(dim = −1, index = t)*. The output of these e*xt*ra codes is \[3, 1\], or \[*z*\[*t*\[0\]\], *z*\[*t*\[1\]\]\].

![](images/bk978-0-7503-6244-3ch9uf7_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf7b_pr.gif)

![Figure 9.4. A DDPM's forward and backward processes. (A) A batch of quadratic curves (outputs of Cell 03). (B) Noised images or curves at time step 1, 25, 50 and 199 in a forward process (outputs of Cell 04). (C) Denoised images starting from t = 199 and ending at t = 0 (outputs of Cell 09).](images/bk978-0-7503-6244-3ch9f4_online.jpg)

**Figure 9.4.** A DDPM's forward and backward processes. (A) A batch of quadratic curves (outputs of Cell 03). (B) Noised images or curves at time step 1, 25, 50 and 199 in a forward process (outputs of Cell 04). (C) Denoised images starting from *t* = 199 and ending at *t* = 0 (outputs of Cell 09).

#### 9.2.2 The backward process in the DDPM

In the physical world, it is easier to mix two materials than to separate them once mixed. It is the same in the digital world for a DDPM. The forward process is much easier than the backward process. The reverse or backward process is another Markov chain starting from a pure noise *x*[*T*] ∼ *p*[*θ*](*x*[*T*]) = ℕ(*x*[*T*];0,*I*)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch9ieqn18.gif"/ and the process is going backwards to get denoised latent images step by step: *x*[*T* − 1]…, *x*[*t*], *x*[*t* − 1], …, *x*[0]inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch9ieqn19.gif"/, where *θ* represents parameters of a U-Net. Figure [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(C) shows the results of a backward process from a pure noise at *t* = 199. At time step *t*−1, the latent image *x*[*t*−1] has a PDF *p*[*θ*](*x*[*t* − 1]∣*x*[*t*]) = ℕ(*x*[*t* − 1];*μ*[*θ*](*x*[*t*],*t*),*β*[*t*]*I*)inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch9ieqn20.gif"/, where *μ*[*θ*](*x*[*t*],*t*)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch9ieqn21.gif"/ coming from the trained U-Net model.

The backward PDF *p*[*θ*](*x*[*t* − 1]∣*x*[*t*])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch9ieqn22.gif"/ corresponds to a reverse of the forward PDF, and it is equal to *q*(*x*[*t* − 1]∣*x*[*t*],*x*[0])inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch9ieqn23.gif"/, which is referred to as ‘forward process posterior distribution.’ Detailed derivations can be found in the DDPM paper (Ho *et al* [2020](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib1)). The following equations ([9.3](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn3)) and ([9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn4)) come from appendix [I](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-I) for completeness

  
$$q(x\_{t - 1}\\mid x\_{t},x\_{0}) = \\mathbb{N}(x\_{t - 1};\\widetilde{\\mu}(x\_{t},x\_{0}),{\\widetilde{\\beta}}\_{t}I) = q(x\_{t}\\mid x\_{t - 1},x\_{0})\\frac{q(x\_{t - 1}\\mid x\_{0})}{q(x\_{t}\\mid x\_{0})}$$  
(9.4)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn24.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = x\_{t} - \\frac{1 - \\alpha\_{t}}{\\sqrt{1 - {\\overline{\\alpha}}\_{t}}}\\varepsilon$$  
(9.5)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn25.gif" position="float"/

  
$${\\widetilde{\\beta}}\_{t} = \\frac{1 - {\\overline{\\alpha}}\_{t - 1}}{1 - {\\overline{\\alpha}}\_{t}}\\beta\_{t}$$  
(9.6)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn26.gif" position="float"/

The above formulae will be used for variational lower bound loss of model training. The joint probability distribution of the backward process is:

  
$$p\_{\\theta}\\left( x\_{0:T} \\right) = p\_{\\theta}\\left( x\_{T} \\right)\\prod\\limits\_{t = 1}^{T}{p\_{\\theta}\\left( {x\_{t - 1}\\mid x\_{t}} \\right)} = p\_{\\theta}\\left( {x\_{0}\\mid x\_{1}} \\right)p\_{\\theta}\\left( {x\_{1}\\mid x\_{2}} \\right)\\ldots p\_{\\theta}\\left( {x\_{T - 1}\\mid x\_{T}} \\right)p\_{\\theta}\\left( x\_{T} \\right)$$  
(9.7)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn27.gif" position="float"/

From the joint possibility distribution and∫*q*(*x*[0])*d**x*[0] = 1inline-graphic style="height:1.625em;" xlink:href="bk978-0-7503-6244-3ch9ieqn28.gif"/, we have the negative log likelihood (loss function) of the system for model training: *L* =  − log  (*p*[*θ*](*x*[0])) =  − log  ∫*p*[*θ*](*x*[0 : *T*])*d**x*[1 : *T*]inline-graphic style="height:1.625em;" xlink:href="bk978-0-7503-6244-3ch9ieqn29.gif"/

  
$$L = - \\left( {\\int q\\left( x\_{0} \\right)dx\_{0}} \\right){\\ \\log\\ }\\int{q\\left( {x\_{1:T}\\mid x\_{0}} \\right)}\\frac{p\_{\\theta}\\left( x\_{0:T} \\right)}{q\\left( {x\_{1:T}\\mid x\_{0}} \\right)}dx\_{1:T}$$  
(9.8)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn30.gif" position="float"/

Using Jensen's inequality, we can simplify the above formula to get the variational lower bound loss of the system (appendix [I](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-I))

  
$$L < - \\int q\\left( x\_{0} \\right)dx\_{0}\\int q\\left( {x\_{1:T}\\mid x\_{0}} \\right){\\ \\log\\ }\\frac{p\_{\\theta}\\left( x\_{0:T} \\right)}{q\\left( {x\_{1:T}\\mid x\_{0}} \\right)}dx\_{1:T} = L\_{VLB}$$  
graphic style="width:24.625em;" xlink:href="bk978-0-7503-6244-3ch9ueqn31.gif" position="float"/

  
$$L\_{VLB} = D\_{KL}(q(x\_{T}\\mid x\_{0}){\\mid\\mid}p\_{\\theta}{(x\_{T})}) + \\sum\\limits\_{t = 2}^{T}{D\_{KL}(q(x\_{t - 1}\\mid x\_{t},x\_{0}){\\mid\\mid}p\_{\\theta}(x\_{t - 1}\\mid x\_{t}))} - Ε\_{q}\\left\\lbrack {\\log\\ p\_{\\theta}(x\_{0}\\mid x\_{1})} \\right\\rbrack$$  
graphic style="width:35.0625em;" xlink:href="bk978-0-7503-6244-3ch9ueqn32.gif" position="float"/

  
$$L\_{VLB} = L\_{T} + \\sum\\limits\_{t = 2}^{T}L\_{t - 1} + L\_{0}$$  
graphic style="width:11.125em;" xlink:href="bk978-0-7503-6244-3ch9ueqn33.gif" position="float"/

The variational lower bound for this process is a sum of losses at each time step, *L* = *L*[0] + *L*[1] + … + *L*[T]. Each *D*[KL] term in the *L*[VLB] (except for *L*[0]) is about the difference between two Gaussian distributions and therefore they can be computed directly. *L*[T] can be ignored during model training because it is a constant, and *L*[0] is also ignored because the authors of the DDPM paper got better results without this item. Based on *q*(*x*[*t* − 1]∣*x*[*t*],*x*[0]) = ℕ(*x*[*t* − 1];*μ̃*(*x*[*t*],*x*[0]),*β̃*[*t*]*I*)inline-graphic style="height:1.9375em;" xlink:href="bk978-0-7503-6244-3ch9ieqn34.gif"/ and *p*[*θ*](*x*[*t* − 1]∣*x*[*t*]) = ℕ(*x*[*t* − 1];*μ*[*θ*](*x*[*t*],*t*),*σ*[*t*]²*I*)inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch9ieqn35.gif"/, we have the following formula, where *C* is a constant which does not relate to model training, and t = 2,3…, *T*

  
$$L\_{t - 1} = D\_{KL}(q(x\_{t - 1}\\mid x\_{t},x\_{0}){\\mid\\mid}p\_{\\theta}(x\_{t - 1}\\mid x\_{t})) = Ε\_{q}\\left( {\\frac{1}{2\\sigma\_{t}^{2}}{\\mid\\mid}{\\widetilde{\\mu}}\_{t}(x\_{t},x\_{0}) - \\mu\_{\\theta}(x\_{t},t)\\mid\\mid^{2}} \\right) + C$$  
graphic style="width:33.5em;" xlink:href="bk978-0-7503-6244-3ch9ueqn36.gif" position="float"/

The authors of the DDPM paper (Ho *et al* [2020](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib1)) set the predicted *μ*[*θ*](*x*[*t*],*t*)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch9ieqn37.gif"/ to have the same format of *μ̃*[*t*](*x*[*t*],*x*[0])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch9ieqn38.gif"/ shown in equation ([9.5](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn5)), and ignored all that baggage in the formula to get a reweighted version *L*[VLB] that emphasizes reconstruction quality, where *ε*[*θ*] is a function approximator intended to predict *ε* from *x*[*t*]

  
*L*[*t* − 1] = *E*[*x*[*o*], *ε*](∥*ε*−*ε*[*θ*](*x*[*t*],*t*)∥²)  
(9.9)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch9eqn39.gif" position="float"/

We train our U-Net model to predict noises *ε*[*θ*] at a time step *t*, and then calculate the difference between the predicted noises *ε*[*θ*] and noises *ε* inside $x\_{t} = \\sqrt{{\\overline{\\alpha}}\_{t}}x\_{0} + \\sqrt{1 - {\\overline{\\alpha}}\_{t}}\\varepsilon$inline-graphic style="height:1.4375em;" xlink:href="bk978-0-7503-6244-3ch9ieqn40.gif"/ with equation ([9.9](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn9)) in a MSE loss function. A function defined in Cell 06 is used to train the U-Net according to the above DDPM theory with a little modification. To save model training time, we do not use all time steps for each image in each batch. The code on line 10 of Cell 07 generates a batch of random integers from 0 to *T*\-1 (included) as the time steps. From the code on line 12, we get a batch of latent images *x*[*t*] at those time steps by adding a batch of noises *ε* generated by the code on line 11. The U-Net then predicts noises *ε*[*θ*] for us to calculate the MSE loss according to equation ([9.9](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn9)).

The first function defined in Cell 05 is used for time stamps. The backbone of the U-Net is the same as the one in section [9.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-1) with many modifications. We have to mark latent images with time stamps by time embedding in the basic block (class Basic of Cell 06). We used label information embedding in section [3.3](#Chapter_3.xhtml#bk978-0-7503-6244-3ch3s3-3) for conditional GANs. Time embedding can be done in many ways. Codes of the ‘sinusoidal\_embedding’ function defined in Cell 05 were inspired by codes in Brian Pulfer's [GitHub](https://medium.com/mlearning-ai/enerating-images-with-ddpms-a-pytorch-implementation-cef5a2ba8cb1) repository. A multi-head self-attention class (MHSA (Petit *et al* [2021](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib4))) is used for the bridge. There are four self-attention heads inside the instance of the class. The inputs Q, K and V of the instance are the same: a layer normalized and reshaped bridge. Detailed information about multi-head self-attention will be provided in chapter [10](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10). A single head cross attention class (Attention) is used to modify skips of the U-Net. I was able to write the single head cross attention codes after watching DigitalSreeni's [YouTube video](https://www.youtube.com/watch?v=KOF38xAvo8I) and reading an Attention U-Net paper (Oktay *et al* [2018](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib3)). A U-Net with attention gives the relevant parts of an images larger weights. In the Basic class in Cell 06, a shortcut is used to construct a residual network, and also layer normalization is used. It took a long time to get the smooth quadric curve shown in figure [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(C). The function defined in Cell 09 is based on equations ([9.5](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn5))–([9.6](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn6)) to generate images from pure noises.

![](images/bk978-0-7503-6244-3ch9uf8_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf9_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf10_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf11_pr.gif)

### 9.3 Using a pre-trained U-Net from Hugging Face to generate images

The attention U-Net in the last section is powerful enough for MNIST, but not smart enough for CIFAR10. To generate high-quality fake images for other datasets such as CelebA and STL10, we need more powerful U-Nets. Fortunately, Hugging Face provides a pre-trained U-Net model for different datasets. We just need to write a few code lines to generate beautiful images. Codes in the following project [9.3.1](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn16) are used to demonstrate the power of Hugging Face's diffusion model. Before running the codes, please use the DOS command pip install Hugging Face *diffusers* in a VS Code terminal of your workspace. The ‘model\_id’ on line 02 is the name of a file with pre-trained parameters for a specific dataset. After starting to run the codes for the first time, a file of about 500 MB will be downloaded for a U-Net to a DDPMPipeline. You can find more files with pre-trained parameters from Hugging Face. The names of a few such files are listed on lines 02–3. The output of an instance of the *DDPMPipeline* on line 05 is a dictionary with a key named ‘sample’. The value of the key is a list with only one element for an image generated from pure noises. The code on line 06 picks out and displays that image. Three fake images generated by three pre-trained U-Nets are shown in figure [9.5](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig5). I believe that the quality of the image generated by the program with only six lines can compete with the quality of images on a famous website: *This Person Does Not Exist*. You can try to run the short codes on your laptop or Google Colab. On my laptop with a RTX 2060 GPU, the program running time is about 2.5 min.

![](images/bk978-0-7503-6244-3ch9uf12_pr.gif)

![Figure 9.5. Fake images generated by pre-trained Hugging Face U-Net models: (A) ‘google/ddpm-celebahq-256’; (B) ‘google/ddpm-ema-church-256’; and (C) ‘google/ddpm-ema-cat-256’.](images/bk978-0-7503-6244-3ch9f5_online.jpg)

**Figure 9.5.** Fake images generated by pre-trained Hugging Face U-Net models: (A) ‘google/ddpm-celebahq-256’; (B) ‘google/ddpm-ema-church-256’; and (C) ‘google/ddpm-ema-cat-256’.

It is more flexible to use Hugging Face's powerful U-Nets in our Pytorch codes for custom datasets, such as flower dataset downloaded from Kaggle. The dataset is about 215 MB with five kinds of beautiful flowers: daisy, dandelion, rose, sunflower and tulip. This dataset was released by DPhi Data Sprint #25: Flower Recognition under the Creative Commons By-Attribution License. The outputs of the following project [9.3.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn17) are shown in figure [9.6](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig6). After every 25 epochs, a trained model was saved for the next 25 epochs. Model training with a total of 25 × 11 epochs took about 11 h. The results are good enough, but still not as good as the original images. The codes of the flower project are almost the same as the codes for the quadratic curve project in section [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-2). Using only three lines in Cell 06, we can import a pre-trained U-Net from Hugging Face. After each 25-epoch model training, the model is saved by codes in Cell 10. The saved model would be loaded by Codes in Cell 06.

![](images/bk978-0-7503-6244-3ch9uf13_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf14_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf15a_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf15b_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf16_pr.gif)

![Figure 9.6. (A) Original flower images from the Kaggle Flowers Dataset with a license CCO 1.0. (B) Fake flower images generated from pure noises by a DDMP U-Net of Hugging Face in about 11 h model training.](images/bk978-0-7503-6244-3ch9f6_online.jpg)

**Figure 9.6.** (A) Original flower images from the Kaggle [Flowers Dataset](https://www.kaggle.com/datasets/imsparsh/flowers-dataset) with a license CCO 1.0. (B) Fake flower images generated from pure noises by a DDMP U-Net of Hugging Face in about 11 h model training.

### 9.4 Generate photorealistic images from text prompts by stable diffusion

The flower images generated by the pre-trained Hugging Face U-Net model are really beautiful. However, it is impossible for us to control what kind of flower to generate. We could use a conditional DDMP model to generated images according to our settings. Even if our conditional DDMP model with codes in a thousand lines works very well, it only can generate images in categories limited by the dataset used to train our model. To obtain photorealistic images, model training time could be very long. How can we generate any high-quality images by using text prompts without model training?

We now (since 2022) have a generative model to generate any image from text prompts. It is Hugging Face's Stable Diffusion, a deep learning, text-to-image model with the name: latent diffusion model (LDM (Rombach *et al* [2022](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib5))). A dataset used to train Stable Diffusion is Laion-5B, an open-source dataset which provides more than 5.85 billion CLIP-filtered image-text pairs. Natural language processing (NLP) is a branch of computer science. Multi-head self-attention used in section [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-2) is an NLP method to obtain information from encoded text. Stable diffusion is an integration of computer vision and NLP. Hugging Face has a website for Stable Diffusion 2.1 Demo, in which there is a link to DreamStudio Beta. The second website generates images with higher loyalty to our text prompts. If you generate images of human faces, you will see a huge difference between the two websites. We can download libraries of Stable Diffusion and practice to generate images in VS Code. The file sizes of those libraries and pre-trained parameters are huge (>10 GB). To save computer hard disk space, you can run the following codes in Google Colab or Kaggle with free GPUs (figure [9.7](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig7)). On January of 2024, Microsoft’s Copilot and Google’s Bard let people to generate photorealistic image with text prompts.

![](images/bk978-0-7503-6244-3ch9uf17_pr.gif)

![Figure 9.7. An image generated with the text prompt ‘a girl in a rose garden’ by a pre-trained Stable Diffusion in project 9.4 running in Google Colab.](images/bk978-0-7503-6244-3ch9f7_online.jpg)

**Figure 9.7.** An image generated with the text prompt ‘a girl in a rose garden’ by a pre-trained Stable Diffusion in project [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn21) running in Google Colab.

### References

Ho J, Jain A and Abbeel P 2020 Denoising diffusion probabilistic models *Adv. Neural Inform. Process. Syst.* **33** 6840–51

Ioffe S and Szegedy C 2015 Batch normalization: accelerating deep network training by reducing internal covariate shift *Int. Conf. on Machine Learning* (PMLR) pp 448–56

Oktay O, Schlemper J, Folgoc L L, Lee M, Heinrich M, Misawa K, Mori K, Mcdonagh S, Hammerla N Y and Kainz B 2018 Attention u-net: learning where to look for the pancreas *arXiv preprint* arXiv:[1804.03999](http://arxiv.org/abs/1804.03999)

Petit O, Thome N, Rambour C, Themyr L, Collins T and Soler L 2021 U-net transformer: Self and cross attention for medical image segmentation *Int. Workshop on Machine Learning in Medical Imaging* (Berlin: Springer) pp 267–76

Rombach R, Blattmann A, Lorenz D, Esser P and Ommer B 2022 High-resolution image synthesis with latent diffusion models *Proc. of the IEEE/CVF Conf. on Computer Vision and Pattern Recognition* pp 10684–95

Ronneberger O, Fischer P and Brox T 2015 U-Net: convolutional networks for biomedical image segmentation *Int. Conf. on Medical Image Computing and Computer-Assisted Intervention* (Berlin: Springer) pp 234–41

Staal J, Abramoff M D, Niemeijer M, Viergever M A and Ginneken B V 2004 Ridge-based vessel segmentation in color images of the retina *IEEE Trans. Med. Imaging* [**23** 501–9](http://dx.doi.org/10.1109/TMI.2004.825627)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 10

## Applications of vision transformers

Using models based on transformers but not convolution networks, computers are smart enough to understand human languages. Transformers used for computer vision tasks are vision transformers. The first section introduces the architecture of a basic vision transformer. Then, pre-trained vision transformers were used in the following four sections for image classification and objection detection without model training (Zero-shot) for custom datasets.

The birth of ChatGPT (Generative Pre-trained Transformer) from OpenAI is a breakthrough in computer science. People can chat with computers to discuss any subject. It seems that ChatGPT knows everything, and can reply to many questions asked by people. On the interface of the ChatGPT website, I used the text prompts ‘please write Python codes about logistic regression for me’. Then in a few seconds, I was able to copy and paste codes from ChatGPT to a cell in VS Code and run the codes. Computers have passed the Turing Test, a method of inquiry in AI to determine whether or not a computer is capable of thinking like a human being. ChatGPT is a language model which uses a transformer (Vaswani *et al* [2017](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10bib4)) for natural language processing (NLP) tasks such as language translation, text classification, and text generation. In the transformer, there is an encoder and a decoder. Words in a text prompt written in a natural language are digitalized as tokens in a high-dimensional vector space. A token is a small unit of information. These tokens embedded with sequence information of words in the text prompt are used as inputs of an encoder of the transformer. Self-attention mechanisms are used in the transformer to capture dependencies between different tokens in the paper. The use of the transformer has led to revolutionary improvements in NLP tasks. Vision transformers (ViT) are modified NLP transformers for computer vision tasks such as image classification and object detection. Vision transformers were introduced by Dosovitskiy *et al* in their 2020 paper (Dosovitskiy *et al* [2020](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10bib1)) titled ‘An Image Is Worth 16 × 16 Words: Transformers for Image Recognition at Scale.’ Unlike traditional convolutional neural networks which use a series of convolutional and pooling layers to extract local features from images, a ViT based on a NLP transformer can capture spatial relationships among different parts of an image.

### 10.1 The architecture of a basic ViT model

In a basic ViT model based on the ViT paper (Dosovitskiy *et al* [2020](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10bib1)), there is only a modified encoder, no decoder. Any color image input to the ViT model should be resized to 3 × 224 × 224, and then split into a grid of patches with a specified patch size. If the patch size is 8 then the image is split into 784 (=224/8 × 28) patches. Each color patch is then flattened into a 1D array as a token which has 192 (=3 × 8 × 8) elements. The key idea of a ViT is to treat an image as a sequence of tokens and then process these tokens by using a transformer's encoder. This allows ViT to capture global information of an entire image, rather than just local information in specific regions from CNN networks. Vision transformers have achieved state-of-the-art performance. They have also been used in a variety of applications, including image captioning, image generation, and video classification. Codes in the following project [10.1.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn1) are used to explain the architecture of the basic ViT model.

As usual, codes in Cell 01 import libraries for the project and set hyperparameters in a dictionary named ‘config’. In a class defined in Cell 02, a tool or library named *einops* is used to reshape and permute an input image according to a text instruction: ‘b c (h h1) (w w1) -> b (h w) c h1 w1’, where b, c, h1 and w1 are batch size, image channels (=3), and patch size (= 8 pixels) in row and column directions respectively. Based on the known input image size (224), an instance of the class calculates another two parameters h and w (28 = 224/8). Einops is a powerful library for tensor operations in computer vision. The name ‘einops’ stands for ‘Einstein operations’ and is inspired by Einstein’s notation used in physics to express tensor operations in his Theory of Relativity. Two parameters in a pair of parentheses of the text instruction are used for a parameter's value which is equal to the production of the two parameters. For example, (h h1) is for a parameter about the image height 224 which is equal to 28 × 8. Although we can do the same job by using PyTorch tools such as *reshape* and *permute*, *einops* is easy to understand with text prompts. Each color patch of the image is then flattened to a tensor with 192 elements (D = 3 × 8 × 8). With the above operations, a 2D image *x* ∈ ℜ^(*C* × *H* × *W*)inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch10ieqn1.gif"/ is split into a series of flattened 2D patches *x*[*p*] ∈ *R*^(*N* × (*P*² ⋅ *C*))inline-graphic style="height:1.5em;" xlink:href="bk978-0-7503-6244-3ch10ieqn2.gif"/, where *H*×*W* is the resolution of the input image, *C* is the number of image channels, *P* is the patch size, and *N* (= *HW*/*P*²) is the number of patches. Each flattened patch is a token like a word token in NLP. The use of tokens enables ViT to learn relationships among different regions of an image and make predictions based on the overall context of the image (figure [10.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10fig1)).

![](images/bk978-0-7503-6244-3ch10uf1_pr.gif)

![Figure 10.1. (A) An image with a resolution 3 × 244 × 244 was directly divided into a grid with 28 × 28 patches by an einops operation in Cell 02. (B) The same image was split by a convolution operation and reshaped to \[1, 786, 3, 8, 8\].](images/bk978-0-7503-6244-3ch10f1_online.jpg)

**Figure 10.1.** (A) An image with a resolution 3 × 244 × 244 was directly divided into a grid with 28 × 28 patches by an einops operation in Cell 02. (B) The same image was split by a convolution operation and reshaped to \[1, 786, 3, 8, 8\].

With codes in the following Cell 03, a learnable token *z*[00] = *x*[class]inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch10ieqn3.gif"/ with a name ‘cls’ is then pre-pended to the sequence of the tokens for image classification. The dimensionality of the cls token is the same as that of a flattened patch. Since the sequence of image patches is as important as words in a paper, we need to add position embeddings to the tokens to retain positional information. The result of these operations is a tensor z[0] as an input of the ViT encoder shown in equation ([10.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn1)), where *Ε*[*p**o**s*] ∈inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch10ieqn4.gif"/ ℜ^((*N* + 1) × *D*)*E* ∈ *Ε*[*p**o**s*]inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch10ieqn5.gif"/ is a trainable position embedding tensor, and *Ε*[*p**o**s*] ∈inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch10ieqn6.gif"/ ℜ^((*P*² ⋅ *C*) × *D*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch10ieqn7.gif"/ is a learnable linear projection tensor from a convolution operation in the following Cell 02. The above Cell 02 with an einops operation is just used for visualization of image patches

  
*z*[0] = \[*x*[class],*x*[*p*[1]]*E*,*x*[*p*[2]]*E*,…,*x*[*p*[*N*]]*E*\]^(*T*) + *Ε*[*p**o**s*]  
(10.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch10eqn8.gif" position="float"/

In the forward function of a class defined in Cell 03, the input is a batch of images with the shape \[b, 3, 224, 224\], where the parameter b is batch size. From an instance of a class defined in the following Cell 02 with a convolution and a permute operations, the input image is split to a tensor with the shape \[b, 784, 192\]. A learnable *cls* token is created by the code on line 06 of Cell 03. It is then expanded for every image in a batch by the code on line 14. After the *cls* token is pre-pended to each image of the batch, we add a tensor for position embedding to each token of each image. PyTorch will take care of dimension difference between the two tensors by broadcasting. To reduce overfitting issues, we need a dropout operation for the output of Cell 03. By running codes inside the quotation makers ‘f2=Embeded\_Imgs(config);emb\_img=f2(my\_img); emb\_img.shape’ in an extra cell after Cell 03, we will know the shape of the output of Cell 03 is \[1, 785, 192\] for a batch with only one image.

![](images/bk978-0-7503-6244-3ch10uf2_pr.gif)

 

The architecture of a basic ViT model is shown on the left side of figure [10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10fig2). Those tokens from Cell 03 or equation ([10.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn1)) are processed by 12 transformer encoder layers connected in series. They refine the representation of input images. The structure of an encoder layer is shown in the middle of the figure. Inside the encoder layer, there is a multi-head attention block which has six self-attention heads connected in parallel to process each batch of tokens. The structure of a single self-attention head is shown on the right-hand-side of the figure. The shape of the input and the output of each self-attention head are the same \[b, 785, 192\]. According to equation ([10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn2)), we can write codes for the self-attention head in Cell 04. In the equation and the figure, a dot between two tensors means a dot product. Each of the three tensors *Q*, *K* and *V* is an output of three fully connected layers, respectively. The input of any fully connected layer is the same: a batch of tokens of images in a batch, and *D* is equal to 192 (the number of pixels of the color patch: 3 × 8 × 8). The outputs of all six self-attention blocks are then concatenated into a bigger size tensor with the shape \[b, 785, 192 × 6\] by the code on line 18 of Cell 05. Then a fully connected layer is used to project the big size tensor to a tensor with the shape \[b, 785, 192\] by the code on line 21. After a dropout operation acts on the result of the projection, the final result is output as a tuple with two elements. The first element is an attention tensor for a batch of tokens, and the second element of the tuple is for attention probs. We can run codes ‘f4=MultiHeadAttention(config); Y=f4(emb\_img)\[0\]; Y.shape’ to check if codes of the classes are functional

  
$$\\text{Attention}(Q,K,V) = \\text{softmax}\\left( \\frac{Q \\cdot K^{T}}{\\sqrt{D}} \\right) \\cdot V$$  
(10.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch10eqn9.gif" position="float"/

![](images/bk978-0-7503-6244-3ch10uf3_pr.gif)

![Figure 10.2. The architecture of a basic ViT model, an encoder layer or block inside the ViT model and a single self-attention head (right). The arrows indicate information flowing directions.](images/bk978-0-7503-6244-3ch10f2_online.jpg)

**Figure 10.2.** The architecture of a basic ViT model, an encoder layer or block inside the ViT model and a single self-attention head (right). The arrows indicate information flowing directions.

The input of a transformer encoder is a batch of tokens of images. Because each token of an image is embedded with position information, we should not use batch normalizations, but layer normalizations in the encoder. Also, two residual connections are used in the encoder block (line 19, 21 in Cell 06). In the MLP (multi-layer perceptron) block of an encoder layer, there are two fully connected layers, and between them is an activation class *nn.GELU()* (line 12 of Cell 06). Dropouts are also used in the MLP block.

Mathematical operations for each of the 12 (=L) encoder layers can be represented by equations ([10.3](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn3)) and ([10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn4)) for Cell 07. To the first layer for example, the output of the first layer normalization to the input tokens *z*[*0*] is LN(*z*[*0*]), which is then processed by a multi-head self-attention block to get MSA(LN(*z*[*0*])). Using equation ([10.3](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn3)), we obtain a temporary output *Φ*inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch10ieqn10.gif"/[0] of the first residual block in the first encoder layer. Using *Φ*inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch10ieqn11.gif"/[0] as an input for the second residual block in the first encoder layer and equation ([10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn4)), we get *z*[*1*], the output of the first encoder layer. The output of the last encoder layer is also a tuple with two elements about tokens and attention scores

  
*Φ*[𝓁 − 1] = *M**S**A*(*L**N*(*z*[𝓁 − 1])) + *z*[𝓁 − 1]𝓁 = 1, 2, ..., *L*  
(10.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch10eqn12.gif" position="float"/

  
*z*[𝓁] = *M**L**P*(*L**N*(*Φ*[𝓁 − 1]) + *Φ*[𝓁 − 1]𝓁 = 1, 2, ..., *L*  
(10.4)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch10eqn13.gif" position="float"/

  
*y* = MLP(*z*[*L*]\[:,0\])  
(10.5)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch10eqn14.gif" position="float"/

We only use *z*[*L*]\[b, 0, 192\] for image classification. The shape of *z[L]*\[:,0\] in equation ([10.5](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10eqn5)) is \[b, 192\]. A classification head is added on top of the final transformer layer to make predictions for image classification. We can make sure that codes in all the above classes are functional by run the codes ‘f6=Vit(config); f6(my\_img)’ in an extra cell after Cell 07. Using codes in Cell 10 in project [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn1) of chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2), you would find there were a total of 14,443,018 parameters in the ViT model defined in Cell 07.

![](images/bk978-0-7503-6244-3ch10uf4a_pr.gif)

![](images/bk978-0-7503-6244-3ch10uf4b_pr.gif)

### 10.2 Hugging Face ViT for CIFAR10 image classification

I would like to use the above ViT model for CIFAR10 image classification. Since the model's parameter number is more than 10 million, the computation job of the ViT model training is too heavy for my laptop to handle 50 thousand images resized to 224 × 224. I have to use a pre-trained Hugging Face ViT model to demonstrate the power of vision transformers. Because the pre-trained model has about 86 million parameters, I have to freeze them and only train a few parameters in the last layer for image classification to save time. From YouTube, GitHub, Kaggle and Google Colab, we can find codes to demonstrate how to fine tune Hugging Face ViT models for CIFAR10. My codes are inspired by those people's codes. The accuracies of image classification of the following project [10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn5) are 94.9%, 94.5% and 94.7% for the train, validation and test datasets respectively. Code running time is about 33 min in 10 epochs.

With a pre-trained Hugging Face ViT model named ‘*google/vit-base-patch16–224-in21k*’, it is easy for us to write codes for project [10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn5) where the code structure is almost the same as the one in project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22) of chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2). Hugging Face provides a library named ‘datasets’ to download datasets from internet (line 05 of Cell 01), and it is convenient to use. Datasets downloaded from internet are saved on my hard disk, and can be used without downloading again even when my laptop is restarted. In Kaggle and Google Colab, we have to download the codes again when we restart to use any of the two free GPU systems. Many libraries from Hugging Face work in Python with a version above 3.6. The codes for this project were tested and worked well in Python v3.9 of VS Code. If you print out *train\_ds\[0\]* after Cell 01, you will see a dictionary with two keys: ‘img’ and ‘label’, not a tuple as in chapters [1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1)–[9](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9).

A Hugging Face class named ‘*ViTImageProcessor*’ on line 09 of Cell 01 can be used to modify images to a specific format for the pre-trained ViT model. Printing out the processor or using a code on the last line of Cell 02, you will see many image augmentations, such as normalize, rescale, resize, etc. A function defined in Cell 03 packs processed image datasets into dataloaders, and codes in Cell 04 display a batch of images in a train dataloader. From a for-loop on the first line of in Cell 04, you will find that each sample in a dataloader is a dictionary with a ‘label’ key and a ‘pixel\_values’ key respectively.

![](images/bk978-0-7503-6244-3ch10uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch10uf6_pr.gif)

![](images/bk978-0-7503-6244-3ch10uf7_pr.gif)

### 10.3 Zero shot image classification by OpenAI CLIP

To understand what a ‘zero shot’ is, we need to recap image classification from chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2). To get good results for image classification projects, we have to use as many samples as possible to train a ResNet model. If the number of samples needed to train a model is *N*, the model needs N-shot learning. Zero shot image classification refers to the ability of a neural network system to classify images into categories without model training. How can OpenAI's CLIP (Radford *et al* [2021](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10bib3)) make zero shot learning possible? CLIP is an abbreviation of ‘contrastive language image pretraining’, a name for a transformer-based framework developed by OpenAI. In a CLIP system there are two models. The first is a text transformer to encode text into a space with 512 dimensions, and the second is a vision transformer (ViT) to encode images in the same space. OpenAI has trained CLIP on a dataset with 400-million text-image pairs. Each pair of an image and its caption are two close points in the space. From an image we can find its caption text, and vice versa. Zero shot image classification does not need to train models because OpenAI has trained the CLIP system for us. This zero shot capability is a significant advantage of CLIP, as it eliminates the need for fine-tuning or retraining on specific classes. However, CLIP has its limitations. The accuracy of the predictions depends on the quality and diversity of the training data. Additionally, CLIP may struggle to describe a single image with a few words because ‘a picture is worth a thousand words’.

The codes in the following two projects were inspired by codes from CLIP's GitHub repository. As usual, codes in Cell 01 of project [10.3.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn8) import the necessary libraries. Since there is no model training, there are no hyperparameter to set. CIFAR10's test dataset is used in the project. The code on line 06 of Cell 01 prints out the class labels of the dataset. We will use them to identify objects in the 10 000 images of the test dataset which has the same dataset structure in chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2). In an extra cell after Cell 01 running the code *clip.available\_models()*, you will see nine CLIP models. From model ‘ViT-B/32’ and ‘ViT-L/14’, I got accuracies of 88.79% and 95.32% with a program running time of 2 min and 3.5 min respectively. The *preprocess* code following *model* on the last line of Cell 01 is for image augmentations. In another extra cell, you can *print(preprocess)* to see many augmentations: resize(244), centerCrop((224,224)), to RGB, ToTensor and normalize. With a fitting function defined in Cell 02, images in the test dataset are checked one by one in a for-loop. Before the loop, the dataset's 10 labels are encoded by *clip.tokenize* into a 10 × 512 tensor. In front of each label, a text string ‘a photo of a’ is pre-pended. According to the CLIP paper (Radford *et al* [2021](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10bib3)), CLIP models have better performance with those extra words added to each label. The code on line 11 of Cell 02 encodes a single image in a batch into a 1 × 512 tensor. With a dot product on line 13 for the encoded image tensor and the encoded label tensor, we get the class identity of an object in a CIFAR10 image. The final results are shown in table [10.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10t1), and the average accuracy of the zero shot classification is 95.3%. In chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2) for same test dataset, the accuracy is 92%.

![](images/bk978-0-7503-6244-3ch10uf8a_pr.gif)

![](images/bk978-0-7503-6244-3ch10uf8b_pr.gif)

**Table 10.1.** Zero shot image classification for CIFAR10 by CLIP.

| Label || Airplane || Automobile || Bird || Cat || Deer || Dog || Frog || Horse || Ship || Truck || Acc (%) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Airplane || 952 || 2 || 19 || 2 || 0 || 0 || 1 || 4 || 17 || 3 || 95.2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Automobile || 0 || 965 || 0 || 0 || 0 || 0 || 0 || 0 || 0 || 35 || 96.5 |
| Bird || 1 || 0 || 957 || 8 || 24 || 1 || 1 || 8 || 0 || 0 || 95.7 |
| Cat || 1 || 1 || 13 || 947 || 7 || 23 || 2 || 5 || 0 || 1 || 94.7 |
| Deer || 0 || 0 || 9 || 4 || 957 || 3 || 1 || 26 || 0 || 0 || 95.7 |
| Dog || 0 || 0 || 4 || 35 || 3 || 954 || 0 || 4 || 0 || 0 || 95.4 |
| Frog || 0 || 0 || 47 || 39 || 30 || 8 || 867 || 8 || 1 || 0 || 86.7 |
| Horse || 0 || 0 || 5 || 1 || 5 || 3 || 0 || 985 || 1 || 0 || 98.5 |
| Ship || 11 || 11 || 5 || 0 || 0 || 3 || 0 || 0 || 965 || 5 || 96.5 |
| Truck || 1 || 13 || 0 || 0 || 1 || 0 || 0 || 1 || 1 || 983 || 98.3 |

The codes in project [10.3.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn8) work well for datasets with bigger color images. For small black and white images in MNIST dataset and Fashion MNIST dataset, the accuracies are around 60%. We can use a linear-probe evaluation classifier in the following project [10.3.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn9) to solve the issue. The classifier only uses CLIP to encode images in both the train dataset and the test dataset in Cell 02 of the project. Then in Cell 03, a logistic regression is performed for the train dataset's encoded images and their labels. A regression function obtained from the train dataset is then used to predict the class labels of images in the test dataset. If you print out the prediction results on line 04 in Cell 03, you will see a 1D array \[3, 8, 8, …, 5, 0, 7\]. Each integer in the array is a class index for an image in the test dataset. With model ‘ViT-B/32’ or ‘ViT-L/14’, the accuracy for CIFAR10 is 95% and 98%, and code running time is 6 min and 25 min respectively. In section [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-3), the accuracy for CIFAR10 was about 92%. You can also use other datasets to confirm the power of the zero shot classifier.

![](images/bk978-0-7503-6244-3ch10uf9a_pr.gif)

![](images/bk978-0-7503-6244-3ch10uf9b_pr.gif)

### 10.4 Zero shot object detection by Hugging Face's OWL-ViT

The state-of-the-art YOLOv8 models can be used for object detection, image classification, and instance segmentation. YOLOv8 is faster and more accurate than YOLOv7. No matter how advanced a YOLO model is, we have to spend a lot of time labeling images with bounding boxes. Suppose we have 10 000 pathological tissue slide photos from optical microscopes, and we want to construct a dataset to train an AI model for cancer diagnosis. You can guess how expensive it would be to hire at least two of the best pathologists to label those photos. Only after the long time (days even months) needed to train the model with a labeled dataset, would we get the model ready for applications. Later, we may need to add one or more classes to the dataset. For example, a new kind of cancer cell is found, so we must add an extra class label about this kind of cancer cells into the tissue slide dataset. In this scenario, we have to repeat the model training again.

Hugging Face provides us an alternative method for object detection. Using Hugging Face's OWL-ViT transformer library, we can detect objects without model training (zero shot). OWL-ViT is an abbreviation of ‘vision transformer for open-world localization’. The name came from a paper (Minderer *et al* [2022](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10bib2)) published by Matthias Minderer and his collaborators. With a pre-trained OWL-ViT model, it is not necessary to label datasets, and we also do not need to train models. Figure [10.3](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10fig3) shows a zero shot object detection result by a pre-trained OWL-ViT [model](https://colab.research.google.com/drive/1IMPWZcnlMy-tdnTDrUcOZU3oiGg-hTem?usp=sharing#scrollTo=WxDNWqSDzoao). My codes came from codes on Owl-Vit's Google Colab website with modifications. Because we do not need model training, we do not need hyperparameters in Cell 01 of project [10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn10). Among some libraries imported in Cell 01, *OwlViTProcessor*, *OwlViTForObjectDetection* are new. The first one is used to pack text prompts and images into a dictionary for data input to a pre-trained model, and the second is for the outputs of the model.

![Figure 10.3. Results of using Hugging Face's OWL-ViT for zero shot object detection about a butterfly image.](images/bk978-0-7503-6244-3ch10f3_online.jpg)

**Figure 10.3.** Results of using Hugging Face's OWL-ViT for zero shot object detection about a butterfly image.

Using an instance of OwlViTProcessor with a code on line 03 of Cell 03, we pack a list of class names and images for a dictionary named ‘inputs’ for the pre-trained OWL-ViT model with many augmentations. One of those augmentations is to resize each image into a new image with a resolution of 3 × 768 × 768. In the dictionary, there are three keys: ‘input\_ids’, ‘attention\_mask’ and ‘pixel\_values’. With a code *model(\*\*inputs)*, we get the model's outputs, which is also a dictionary. From *outputs\[‘pred\_boxes’\]* and *outputs\[‘logits’\]*, we obtain bounding boxes, labels and label scores (line 07–10 in Cell 03). In the photo shown in figure [10.3](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10fig3), there is a butterfly. But there is no such label in VOC and COCO classes. Just add ‘butterfly’ to the list of VOC classes in Cell 01, the OWL-ViT model can find and label the butterfly. Kaggle and Google Colab have an issue to dynamically show images with code *cv2.imshow()*.

I tried to install Hugging Face's transformer library on my laptop, but had an issue importing the OwlViTProcessor library. After a few days of exploration and searching, I discovered that the issue was caused by Python v3.6, and then installed the Hugging Face transformer library with OwlViTProcessor in a virtual environment using Python v3.9. The codes in project [10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn10) can be used to slide-show images with bounding boxes, to detect objects from a camera or a video file. VOC dataset's classes are used for the model's text queries. The labels ‘cup’ and ‘butterfly’ are added to the text queries, so the model can detect cups and butterflies. IOU and NMS thresholds are set on the last line of Cell 01. Codes in Cell 02 for IOU and NMS came from chapter [7](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7). Cell 03 takes an image as its input, and it outputs the image with bounding boxes/labels/probabilities. The H, W and C parameters on line 02 of Cell 03 are saved for bounding boxes. From the pre-trained model, we obtain 576 bounding boxes on each image. Each bounding box has its probability and class label. Those probabilities came from a SoftMax function (line 07 of Cell 03) acting on an output of the pre-trained model. Relative bounding boxes are lists from a list on line 16. Each element of the list in the list is a bounding box's xc, yc, w, h, label and probability. The four coordinates are relative numbers between 0 to 1. I pack them into a list so that I can use the two functions defined in chapter [7](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7) to pick out a few good bounding boxes from those 576 bounding boxes. OWL-Vit model is sensitive enough to detect many small objects in a background. The code on line 13 of Cell 03 is used to ignore very small objects. Codes in Cell 05–07 of project [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn23) are re-used to display images in a folder or video frames from a camera. The image processing speed is about 10 FPS. You can terminate the program at any time by pressing the Esc key while your computer is focused on the image window. The OWL-ViT object detection accuracy is lower than that of YOLOv8 models.

![](images/bk978-0-7503-6244-3ch10uf10_pr.gif)

![](images/bk978-0-7503-6244-3ch10uf11_pr.gif)

### 10.5 RT-DETR (a vision transformers-based real-time object detector)

On July 6 of 2023, Wenyu Lv and his colleagues in Baidu of China published a paper (Lv *et al* 2023) about the development of a vision transformers-based real-time object detector, RT-DETR, which does not need post-processing, such as non-maximum suppression (NMS). The detector's efficient hybrid encoder reduces computational costs for real-time object detection. They claimed that the detector ‘outperforms the state-of-the-art YOLO detectors of the same scale in both speed and accuracy.’ From the ultralytics website, we can download two pre-trained weight files for a large RT-DETR model and an extra-large RT-DETR model. Their file sizes are around 100 MB. Using codes in the following Project 10.5, we can apply a pre-trained RT-DETR model for objection detection about a single image file, multiple images in a folder, and video frames from a camera or a video file. If you delete the code on line 05, the label for each object displayed on an image will be an integer about an index of a COCO class. Re-using Cell 02-03 in Project 8.4.1 for this project, you need to change the model's name from ‘model’ to ‘baidu’ in those two cells. The extra-large model is better than the large model with a sacrifice of speed. The video frame processing speed is about 15 and 10 FPS for the large and the extra-large model, respectively. You would get four labels for three persons and three labels for three horses in the image shown in figure [10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10fig4) if the large model is used.

![](images/bk978-0-7503-6244-3ch10uf12_pr.gif)

![Figure 10.4. Object detection results for a single image by a pre-trained extra-large RT-DETR model from BAIDU of China. Video frame processing speed of the model is about 10 FPS.](images/bk978-0-7503-6244-3ch10f4_online.jpg)

**Figure 10.4.** Object detection results for a single image by a pre-trained extra-large RT-DETR model from BAIDU of China. Video frame processing speed of the model is about 10 FPS.

### References

Dosovitskiy A, Beyer L, Kolesnikov A, Weissenborn D, Zhai X, Unterthiner T, Dehghani M, Minderer M, Heigold G and Gelly S 2020 An image is worth 16x16 words: transformers for image recognition at scale *arXiv preprint* arXiv:[2010.11929](http://arxiv.org/abs/2010.11929)

Lv W, Xu S, Zhao Y, Wang G, Wei J, Cui C, Du Y, Dang Q and Liu Y 2023 Detrs beat yolos on real-time object detection *arXiv reprint* arXiv:[2304.08069](http://arxiv.org/abs/2304.08069)

Minderer M, Gritsenko A, Stone A, Neumann M, Weissenborn D, Dosovitskiy A, Mahendran A, Arnab A, Dehghani M and Shen Z 2022 Simple open-vocabulary object detection with vision transformers *arXiv preprint* arXiv:[2205.06230](http://arxiv.org/abs/2205.06230)

Radford A, Kim J W, Hallacy C, Ramesh A, Goh G, Agarwal S, Sastry G, Askell A, Mishkin P and Clark J 2021 Learning transferable visual models from natural language supervision *Int. Conf. on Machine Learning* (PMLR) pp 8748–63

Vaswani A, Shazeer N, Parmar N, Uszkoreit J, Jones L, Gomez A N, Kaiser Ł and Polosukhin I 2017 Attention is all you need *Adv. Neural Inform. Proces. Syst.* **30** 6000–10

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 11

## Knowledge distillation and its applications in DINO and SAM

In the year 2023, Facebook released many computer vision models based on vision transformers. Although they are very powerful, their sizes are too big for real-time usage on resource/power limited devices. Knowledge distillation is used to transfer intelligence from a pre-trained jumbo model to a small model. In section [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11s11-1) there is a demonstration of knowledge distillation from ResNet9 to ResNet6 used in chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2). Examples in sections [11.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11s11-2)–[4](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11s11-4) show the intelligence of Facebook's DINO, DINOv2 and SAM models in self-supervised learning to find object characteristics in images or video frames. Since SAM needs 8 GB GPU memory, I have to run it in CPU and it is very slow. A fastSAM model from China enables us to segment anything with a speed 50× faster than SAM.

### 11.1 Knowledge distillation for neural network compression

According to Moore's Law, the number of transistors in IC (integrated circuit) chips doubles approximately every two years. This has enabled the development of faster processors, increased memory capacity, and improved performance in various computing devices. The number of parameters of neural networks in computer vision projects and machine learning projects has also increased significantly for more powerful and functional models. In the model of a linear regression (project [1.3.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn15)), there are only two parameters; in the model of project [10.1.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn1) about a basic vision transformer model for image classification, there are 14,443,018 parameters. The model of ChatGPT (based o GPT 3.5) has 175 billion parameters. However, as the parameter number of a model increases from millions to billions, model training and deployment will be computationally more expensive. With the rise of smart mobile devices such as smart phones, smart watches, and various other devices, we need a small neural model (student) to have the functions of a jumbo model (teacher). Knowledge distillation (Hinton *et al* [2015](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib2)) refers to a technique in machine learning where a teacher model transfers its knowledge to a student model by using ‘soft targets’ during the training process for the student model. The goal of knowledge distillation is to compress the knowledge contained in a large model into a smaller model that can be deployed on resource-limited devices. Knowledge distillation has been successfully applied in many domains, including computer vision, natural language processing and speech recognition. It is a popular technique for model compression and transfer learning, allowing for the transfer of knowledge from large models to smaller models which can be used in real-world applications.

Soft targets are outputs of a teacher model. A pre-trained ResNet9 model from project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22) for CIFAR10 image classification was saved as a teacher model for the following project [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn1). Its prediction accuracies for the classification of images in the train, validation and test datasets are 99.5%, 92.6% and 92.3% respectively. From Cell 10 of project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22), we see that an output y\_hat of the trained ResNet9 to a batch of only one image in the test dataloader is \[\[−103.4488, −113.6267, −95.8173, −90.3314, −70.0091, −96.2804, −94.8856, −100.3270, −113.8334, −108.6170\]\]. Each of the 10 elements in y\_hat is a logit ![image](images/bk978-0-7503-6244-3ch11ieqn1.gif) which produces a soft target probability *p[i]* at a temperature *T* for the pre-trained teacher model, where *i* =0,1…,9

  
$$p\_{i} = \\frac{e^{v\_{i}/T}}{\\sum\\limits\_{j = 1}^{C}e^{v\_{j}/T}}$$  
(11.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch11eqn2.gif" position="float"/

A modified ResNet6 model from section [2.2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-2) will be used as a student model in project [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn1). Replacing ResNet9 by the modified ResNet6 in project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22), you will find the prediction accuracies for the train, validation and test datasets are 95.9%, 88.4% and 88.4% respectively. The output *z* of the modified ResNet6 applied to a batch of one image also produces probabilities *q* at a temperature *T*. Normally, the value of the temperature is set to be equal to 1. We will use a higher *T* value to produce a softer probability distribution over classes

  
$$q\_{i} = \\frac{e^{z\_{i}/T}}{\\sum\\limits\_{j = 1}^{C}e^{z\_{j}/T}}$$  
(11.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch11eqn3.gif" position="float"/

The student model is then trained with a loss function which has a hard loss and a soft loss. The hard loss is a cross-entropy about predicted probabilities of the student model at *T*\=1 and labels of the train dataloader. The soft loss is a cross-entropy about *p* and *q* at a high temperature: $L\_{soft} = - \\sum\\limits\_{j = 1}^{C}p\_{j}{\\ \\log}{(q\_{j})}$inline-graphic style="height:3.375em;" xlink:href="bk978-0-7503-6244-3ch11ieqn4.gif"/. Using some approximations (Hinton *et al* [2015](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib2)), the soft cross-entropy gradient ∂*L*[*s**o**f**t*]/∂*z*[*i*]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch11ieqn5.gif"/, with respect to each logit *z*[*i*] of the student model can be simplified to:

  
$$\\frac{\\partial L\_{soft}}{\\partial z\_{i}} = \\frac{1}{T}(q\_{i} - p\_{i}) \\approx \\frac{1}{NT^{2}}\\left( {z\_{i} - v\_{i}} \\right)$$  
(11.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch11eqn6.gif" position="float"/

At a high temperature, distillation is equivalent to minimizing 0.5(![image](images/bk978-0-7503-6244-3ch11ieqn7.gif))². Since the magnitudes of the gradients produced by the soft targets are proportional to 1/*T*², it is important to multiply them by *T*² when using both hard and soft targets to train the student model. According to equation ([1.7](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1eqn7)), we have *L*[*s**o**f**t*] = *D*[*K**L*](*p* *∣*  *∣* *q*) + *H*(*p*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch11ieqn8.gif"/. Because the Shannon entropy *H*(*p*) is a constant to *z*, we will use *L*[*s**o**f**t*] = *T*²*D*[*K**L*](*p* *∣*  *∣* *q*)inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch11ieqn9.gif"/ to train the student model. There is a PyTorch class nn.KLDivLoss for *D*[*K**L*](*p* *∣*  *∣* *q*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch11ieqn10.gif"/ calculations. How do we choose the value of *T*? One approximation to obtain equation ([11.3](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11eqn3)) is *e*^(*z*[*i*]/*T*) ≈ 1 + *z*[*i*]/*T*inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch11ieqn11.gif"/ in a condition  ∣ *z*[*i*] ∣  ≪ *T*inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch11ieqn12.gif"/. We can find the absolute element value of y\_hat from ResNet9 or ResNet6 is about 100, so we set *T*\=10 000. With the above information, we can write the codes for project [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn1). After running the codes to transfer knowledge from the pre-trained ResNet9 to ResNet6, we get that the prediction accuracies for the train, validation and test datasets are 94.3%, 90.1% and 90.2% respectively. The knowledge distillation increases the ResNet6 model's prediction accuracies by about 2% for the validation and test datasets. However, using *T* = 100 to train the student model, I found the results were almost the same as those shown in figure [11.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig1) for *T* = 10 000.

![](images/bk978-0-7503-6244-3ch11uf1a_pr.gif)

![](images/bk978-0-7503-6244-3ch11uf1b_pr.gif)

![](images/bk978-0-7503-6244-3ch11uf2a_pr.gif)

![](images/bk978-0-7503-6244-3ch11uf2b_pr.gif)

![](images/bk978-0-7503-6244-3ch11uf3_pr.gif)

![Figure 11.1. Model training results of knowledge distillation from ResNet9 to ResNet6.](images/bk978-0-7503-6244-3ch11f1_online.jpg)

**Figure 11.1.** Model training results of knowledge distillation from ResNet9 to ResNet6.

### 11.2 DINO: emerging properties in self-supervised vision transformers

Although the image classification results of using ViT model for CIFAR10 in section [10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10s10-2) are good enough compared with the results from CNN models in section [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-3), there is no benefit, because ViT model training is computationally expensive. To use the ViT model for data processing, we have to resize each CIFAR10 image from 32 × 32 to 224 × 224. It is almost impossible for a personal laptop to handle computational tasks of ViT model training. We had to use the pre-trained Hugging Face ViT Model for Project [10.2](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn5).

The multi-head self-attention class in Cell 05 of project [10.1.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn1) returns a tuple with two elements. One is ‘attention output’ and the other is ‘attention probs’. For image classification, we only use the first one. Using the second one, Mathilde Caron (Caron *et al* [2021](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib1)) and collaborators in Facebook found a unique property of vision transformers: self-supervised learning. To train a YOLOv8 model for objection detection and image segmentation in chapter [8](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8), we have to use labeled datasets. The traditional supervised learning approach requires a large amount of labeled data, which can be expensive and time-consuming to obtain. In contrast, self-supervised learning aims to learn representations by solving pre-text tasks on unlabeled data. This approach has gained attention in recent years due to its ability to leverage the vast amount of freely available unlabeled data.

DINO, which stands for ‘self DIstillation with NO labels,’ is a method that focuses on self-supervised learning for vision transformers. DINO models can discover and segment objects on an image or video frame without supervision and without being given any segmentation-targeted objects. This means that this kind of model is capable of a higher-level of image understanding. DINO technology is based on knowledge distillation between a teacher model and student model. Both models use the same ViT model, but with different parameters and each of them is trained in a different way. Any image input to a DINO system is cropped into two global patches and eight local patches. The global and local crop scales are above 40% and below 40% respectively. Global patches are resized to 224 × 224, and the local patches are resized to 96 × 96. All patches are processed by the student model, but only the two global patches are input to the teacher model. Figure [11.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig2)(A) shows an original image in which there is a rabbit scratching its chin. Two global patches and eight local patches are also shown in the figure. These patches were obtained by the codes in project [11.2.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn4). A class defined in Cell 02 came from Facebook's DINO GitHub repository. In a normalization transform of the class, Facebook's special numbers are not used for simplification.

![](images/bk978-0-7503-6244-3ch11uf4_pr.gif)

![Figure 11.2. An original image (A) is cropped and resized into two global patches (B) and eight local patches (C) for DINO model training.](images/bk978-0-7503-6244-3ch11f2_online.jpg)

**Figure 11.2.** An original image (A) is cropped and resized into two global patches (B) and eight local patches (C) for DINO model training.

It is not necessary to copy and paste Facebook's DINO codes here, and it is impossible for my laptop to train any DINO model. There are many GitHub and YouTube sources to explain DINO. I have to use a pre-trained Facebook DINO ViT model to demonstrate the power of DINO. Five pre-trained Facebook DINO models are listed in Cell 01 of project [11.2.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn6). The name of the model used in the project is ‘facebook/dino-vits8’ in which ‘s’ denotes a small model and 8 is the patch size. If an image's resolution is 480 × 480, the image is then split and embedded into (480/8)²+1 tokens for a ViT model similar to that in section [10.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10s10-1), and they are different from those global and local patches. To understand how the codes in project [11.2.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn6) work, we need to print out the ViT parameters in DINO by *print(model.config)*. There are 12 encoder layers in the DINO ViT and each layer has six self-attention blocks. The last layer of the DINO ViT outputs 3601 tokens and an ‘attentions’ tensor which is a 1 × 6 × 3601 × 3601 tensor for a batch of one image in Cell 02 in project [11.2.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn6). The shape of the attentions tensor is decided by the second output of Cell 05 in project [10.1.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn1) with operations of $\\text{softmax}\\left( {Q \\cdot K^{T}/\\sqrt{D}} \\right)$inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch11ieqn13.gif"/. We use attention scores related to the \[cls\] token selected by attentions\[0, :, 0, 1:\] in the following Cell 02. The selected attention score tensor with a shape 6 × 3600 is then reshaped into 6 × 60 × 60 and interpolated to 6 × 480 × 480 in Cell 03. Then, we can plot the six black and white images shown in figure [11.3](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig3). Each black and white image's resolution is 480 × 480. From the bright spots in the six images, we see that different self-attention heads focus on different objects in the image.

![](images/bk978-0-7503-6244-3ch11uf20_pr.gif)

![](images/bk978-0-7503-6244-3ch11uf5_pr.gif)

![Figure 11.3. (Left) Input: an image processed by the pre-trained DINO model. (Right) Outputs: the self-attention of the \[CLS\] token of the last layer. There are six multi-head self-attention blocks in each encoder layer of the ViT model.](images/bk978-0-7503-6244-3ch11f3_online.jpg)

**Figure 11.3.** (Left) Input: an image processed by the pre-trained DINO model. (Right) Outputs: the self-attention of the \[CLS\] token of the last layer. There are six multi-head self-attention blocks in each encoder layer of the ViT model.

### 11.3 DINOv2 for image retrieval, classification and feature visualization

In April 2023, Meta AI released four pre-trained DINOv2 models: a ViT-g model trained from scratch, and three models (ViT-s, ViT-b, ViT-l) distilled from the ViT-g. A large, curated, diverse dataset (LVD-142M) was used to train these models with a method described in a paper (Oquab *et al* [2023](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib8)): ‘DINOv2: Learning Robust Visual Features without Supervision’. Unlike other pre-training models whose algorithms rely on labeled data or manual captions to interpret image meanings, DINOv2 can learn from any image dataset without requiring accompanying metadata. By avoiding the omission of crucial background information, DINOv2 has a comprehensive grasp of image details to pixel level. DINOv2 stands out by eliminating the need for fine-tuning. Its outputs of high-performance features can be directly employed with classifiers as simple as linear layers on a variety of computer vision tasks. Each DINOv2 model takes an image as input and returns a class token and patch tokens. DINOv2 models can be used for image classification, image segmentation, image retrieval, object detection and object depth estimation.

With a pre-trained small DINOv2 model named ‘dinov2\_vits14’, the codes in project [11.3.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn7) can retrieve flower images in the flower dataset used in chapter [9](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9). From the outputs of the project, you would find that a caption with a few words is not enough to describe a photo, because ‘a picture is worth a thousand words’. Codes in Cell 04 output a batch of flower images from a train dataloader with a batch size of six (figure [11.4](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig4)(A)). By choosing an integer (n) between 0 to 5 in Cell 06, we can select a query image for a type of flower, and then the remaining codes of the project will pick out six flower images from a validation dataset. The retrieved flowers and the query flower should be the same type. In figure [11.4](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig4)(A), there are two dandelion images at *n* = 1 and 5. Using an image at any of these two positions as a query image, we got figures [11.4](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig4)(B) and (C). The pre-trained DINO2 model can distinguish images of dandelions at different life stages: yellow flowers and white seeds. One English word ‘dandelion’ is not enough to distinguish them.

![](images/bk978-0-7503-6244-3ch11uf6_pr.gif)

![Figure 11.4. Image instance retrieval by a small pre-trained DINOv2 model. (A) A batch of images in the train dataloader of the flower dataset. (B) Retrieved images with a query image (n=1). (C) Retrieved images with a query image (n=5). All retrieved images are in the validation dataset. Images in the first row reproduced from Flowers Dataset with a license CC0 1.0.](images/bk978-0-7503-6244-3ch11f4_online.jpg)

**Figure 11.4.** Image instance retrieval by a small pre-trained DINOv2 model. (A) A batch of images in the train dataloader of the flower dataset. (B) Retrieved images with a query image (*n*\=1). (C) Retrieved images with a query image (*n*\=5). All retrieved images are in the validation dataset. Images in the first row reproduced from [Flowers Dataset](https://www.kaggle.com/datasets/imsparsh/flowers-dataset) with a license CC0 1.0.

When you run the code in Cell 01 for the first time, the small pre-trained DINOv2 model will be downloaded from Facebook automatically. The file size is about 21 MB. The size of a large DINOv2 model is about 300 MB. Codes in Cell 06 process each image in the validation dataset to get a 1D tensor with 384 elements for detailed object information about the image. The shape of the output tensor of the cell is 701 × 384, because there are 701 images in the validation dataset. We use Cell 06 to select a query image, and then use the model to extract image features. A Facebook library faiss (Johnson *et al* [2019](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib4)) is used for image similarity search. It assumes that vectors of image features can be compared with L2 (Euclidean) distances or dot products. Vectors that are similar to a query vector are those that have the lowest L2 distance or the highest dot product with the query vector, according to the introduction on the faiss GitHub repository. The output of Cell 07 is a list with batch size elements. Each element is an integer for a position index (<701) of a retrieved image in the validation dataset. The retrieved images are then displayed by the codes in Cell 08. Codes of three small DINOv2 projects in this section were inspired by codes from Purnasai Gudikandula's GitHub repository. I met an issue from the FAISS library after my Python and Pytorch were updated. An improved version of Project [11.3.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn7) was listed in Appendix [J](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-J), in which Euclidean distances are calculated directly without using a third party library.

Since the DINOv2 models are so powerful that they are able to learn image features without human instructions, we can use these models for image classification with the codes listed in project [11.3.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn8). To save space, I re-use Cells 02–04 from project [9.3.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn17) for the flower image dataset, and Cells 06–09 from project [2.3](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn22) for model training without the learning rate scheduler. A class for the classification model is defined in Cell 05. The backbone of the model is the pre-trained big DINOv2 model. Two fully connected layers are appended to the DINOv2 model for image classification. In less than 8 min for model training of five epochs, image classification accuracies for the train dataset and the validation dataset are 99.5% and 95.5% respectively.

![](images/bk978-0-7503-6244-3ch11uf7_pr.gif)

DINOv2 models can extract image features which can be used for image retrieval and image classification. We can visualize the high dimensional features by using a mathematical tool PCA (principal component analysis) in project [11.3.3](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn9). A pre-trained large DINOv2 model ‘dinov2\_vitl14’ is used in the project, and the outputs of the project for a color image with four deer are shown in figure [11.5](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig5). The original size of the image is 800 × 533 × 3. A transformer function defined in Cell 02 processes the original image to get a tensor with a resolution of 1 × 3 × 518 × 518. Using a patch size of 14, the model splits the image into 1369 (=518/14 × 37) patches with an embedding dimension of 1024. The outputs of the model are a class token and 1369 patch tokens. Using *m**o**d**e**l**.**f**o**r**w**a**r**d**\_**f**e**a**t**u**r**e**s**(**i**m**g**\_**t**r**a**n**s**f**o**r**m**e**d**)* but not *m**o**d**e**l**.**(**i**m**g**\_**t**r**a**n**s**f**o**r**m**e**d**)*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch11ieqn14.gif"/ in Cell 02, we obtain a dictionary with four keys, but only one key's value is used in the project as a tensor *batch\_total\_features* of the image, and the tensor's shape is 1 × 1369 × 1024. Using PCA, codes in Cell 03 reduce the dimensions of a *total\_features* tensor with a shape of 1369 × 1024 to get a *pca\_features* NumPy array with a shape of 1369 × 3. Only the zeroth channel of the pca\_features array is normalized and displayed by Cell 04. To save space, I overlayed the first PCA image on the top-left corner of the original photo shown in figure [11.5](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig5).

![](images/bk978-0-7503-6244-3ch11uf8_pr.gif)

![Figure 11.5. Image feature visualization by using PCA to a pre-trained DINOv2 model's outputs.](images/bk978-0-7503-6244-3ch11f5_online.jpg)

**Figure 11.5.** Image feature visualization by using PCA to a pre-trained DINOv2 model's outputs.

The pixel values of the first PCA image are between 0.0 to 1.0 as shown by a gray bar of the gray image. The background is brighter than the foreground (deer). With a threshold value of 0.35, codes in Cell 05 convert the gray image into a black and white image shown on the top-right corner of figure [11.5](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig5). We name the black and white image ‘background’. The value of each white pixel in the background image is equal to 1, and the value of each dark pixel is equal to 0. We use Cell 06 to reverse the background image, and name a new image ‘foreground’. The foreground image is shown on the lower-left corner of figure [11.5](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig5).

A NumPy array *pca\_features\_fg* before being reshaped for the foreground image in Cell 06 is an 1D array with 1369 elements. Printing out the array's summation, you will see that it is equal to 580. This means that there are 580 ‘true’ values in the 1D array. The shape of the total\_features tensor is 1369 × 1024. The code on the first line of Cell 07 uses *pca\_features\_fg* to mask *total\_features*. The result is an array *f\_features0* with a shape of 580 × 1024. The criterion to pick out a row in the tensor *total\_features* is that with the index of the row, we should find ‘true’ in the 1D array *pca\_features\_fg*. Then we use the second PCA transformer to obtain an array *f\_features* with a shape of 580 × 3. This array is then linearly normalized by code on three lines starting from line 03 of Cell 07.

An array *attention\_rgb* on line 06 of Cell 07 is a copy of the array *pca\_features*, the output of the first PCA transformer, and the array is masked by the 1D array of the background image. The normalized second PCA output is then assigned to the array *attention\_rgb* which is displayed as a color image on the lower-right corner of figure [11.5](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig5). You can see the deer heads are shown in green, the necks are orange, their feet are blue, and bodies are pink. DINOv2 models can not only detect objects but also distinguish the components of each object.

### 11.4 Segment anything model: SAM and FastSAM

People with experience of using Photoshop to remove image backgrounds would be very happy to have a new tool: the segment anything model (SAM), which was released by Meta AI on April 15, 2023. Users without any computer code knowledge can upload their photos to Meta's SAM website, and use their mouse to click or draw a box on a photo. Objects on the photo selected by users with those mouse prompts would be segmented from the photo in a few milli-seconds, and the pixels of those objects are separated from the photo's background. People can then use the pixels of those objects to edit images and analyze photos. Figure [11.6](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig6)(A) shows a photo of a mother deer standing on ground covered by snow in my garden. The photo was segmented into 74 objects by codes in Cell 01 of project [11.4.1](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn10) with a model and pre-trained parameters loaded from a check point file *sam\_vit\_h\_4b8939*.*pth*. Because the size of the file is more than 2.5 GB, my laptop's 6 GB GPU memory is not big enough to handle the codes which needs 8 GB. Luckily, I can run the codes in CPU, but code run-time is about 130 seconds. With a free GPU from Google Colab, the code run-time is about 4 seconds. Although I can run my codes on my laptop's GPU with a smaller check point file *sam\_vit\_b\_01ec64.pth* (0.37 GB), the outputs of the codes are trashy. The biggest check point file from the SAM GitHub website is *sam\_vit\_l\_0b3195.pth*. I tried it with my codes, and couldn’t see a significant quality improvement comparing with the middle size one. My codes were inspired by Piotr Skalski's Colab codes, in which Roboflow supervision module (version ⩾ 5.0) is used to display SAM masks (figure [11.6](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig6)(B)).

![](images/bk978-0-7503-6244-3ch11uf9_pr.gif)

![Figure 11.6. (A) Original image. (B) Panoramic segmentation by SAM. (C) Objection detection by OWL-ViT.](images/bk978-0-7503-6244-3ch11f6_online.jpg)

**Figure 11.6.** (A) Original image. (B) Panoramic segmentation by SAM. (C) Objection detection by OWL-ViT.

The output of the SAM mask generator on the last line of Cell 01 is a list, and each element in the list is a dictionary for an object. Codes on the first two lines Cell 02 print out the number of objects segmented from the image, and the dictionary keys of each object are: ‘segmentation’, ‘area’, ‘bbox’, ‘predicted\_iou’, ‘point\_coords’, ‘stability\_score’, ‘crop\_box’. The ‘segmentation’ key is for a mask of a SAM segmentation, and the shape of the mask is the resolution of the original image: 480 × 480. The two keys ‘point\_coords’, and ‘crop\_box’ are mouse prompts set by users. Since we set SAM to use automatic mask generator in Cell 01, the values of the two keys are set by the model automatically. The key ‘stability\_score’ is used to pick out an object from its background. We can display 72 masks with a grid size (9, 8) by the code on the last line of Cell 02. You will see many masks are for the same object, and many meaningless shade spots are segmented as objects on the image. Codes in Cell 02 sort masks reversely according to their areas, and only display the first six masks as black and white images. Codes in Cell 03 show the original image and a processed image with only three major masks. The deer and the snow are separated from the background. Codes in Cell 04 use the major mask masks\[0\] to pick out the deer from the background.

SAM has no object detection function. By taking the output image from Cell 04 to project [8.4.2](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn8), we can use YOLOv8 to detect the object in the image: a cow with a percentage of 79%. It is wrong because YOLOv8 uses classes of COCO dataset to identify objects, but there is no deer class in COCO dataset. Then I used codes in project [10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn10) to analyze the image by Owl-Vit Zero shot object detection. After adding a ‘deer’ item in the class list of Cell 01 in project [10.4](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10ueqn10), the Owl-Vit program was able to find the deer in the image as shown in figure [11.6](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig6)(C). There is nothing special in SAM models (Kirillov *et al* [2023](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib5)), but a ViT as an image encoder, a prompt encoder for points, box and text, and a masks decoder. Meta AI trained SAM modes with 11 million images and 1 billion masks. People are saying that SAM from Meta AI will have the same impact on our world as ChatGPT from Open AI.

The SAM proposed by Meta AI is becoming a foundation for many computer vision tasks, such as image segmentation, image caption, and image editing. However, SAM needs heavy computation resources because SAM's architecture is based on the vision transformer mentioned in Section [10.1](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10s10-1). Xu Zhao and his collaborators in June 2023 proposed FastSAM (Zhao *et al* [2023](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11bib11)) based on YOLOv8. With FastSAM, they achieved a comparable performance with the SAM method at 50× higher run-time speed. They released their codes on their [GitHub website](https://github.com/CASIA-IVA-Lab/FastSAM). According to their instructions, I downloaded and unzipped their codes in a folder named ‘FastSAM’ into my current working folder named ‘Exercises’ in a VS Code virtual environment with Python v3.9. In a VS Code cell, running the codes in the quotation marks *‘import os; os.getcwd(); %cd fastsam’*, I can run codes in project [11.4.2](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11ueqn12) which uses some Python files in the FastSAM folder. With these setting, we can import some libraries with the code on line 03 of Cell 01: *from fastsam import FastSAM, FastSAMPrompt*.

![](images/bk978-0-7503-6244-3ch11uf10_pr.gif)

The original FastSAMPrompt library only accepts a string of an image file name path as an image source. To use FastSAM for camera frames, we have to modify codes from line 23 to 27 in FastSAM/fastsam/prompt.py, so a NumPy array can be used as an image source for the library FastSAMPrompt. I found this solution from Nicolai Nielsen's [YouTube video](https://www.youtube.com/watch?v=SslzS0AsiAw). Roboflow also has a helpful YouTube video about FastSAM. In Cell 02, codes deactivated on line 06–08 are for a box prompt, a point prompt and a text prompt. They work, but the results may not be what we expected. For example, with the text prompt ‘lady’, we only have one lady in the image of figure [11.7](#Chapter_11.xhtml#bk978-0-7503-6244-3ch11fig7) segmented. Re-use codes in Cell 05 and 07 and replace ‘yolov3’ by ‘fastsam’, we can use the function defined in Cell 02 to process images in a folder, frames from a camera or a video file. The speed of the video is about 3 FPS. Although FastSAM's quality of image segmentation is not as good as SAM's quality, we have to sacrifice a little quality for speed.

![](images/bk978-0-7503-6244-3ch11uf11_pr.gif)

![Figure 11.7. Implement of a pre-trained FastSAM model to a single image with a prompt for everything. (left) The original image with bounding boxes from the model. (right) Objects of the image were segmented by the model, and each object with a blue edge was marked with different colors.](images/bk978-0-7503-6244-3ch11f7_online.jpg)

**Figure 11.7.** Implement of a pre-trained FastSAM model to a single image with a prompt for everything. (left) The original image with bounding boxes from the model. (right) Objects of the image were segmented by the model, and each object with a blue edge was marked with different colors.

### References

Caron M, Touvron H, Misra I, Jégou H, Mairal J, Bojanowski P and Joulin A 2021 Emerging properties in self-supervised vision transformers *Proc. of the IEEE/CVF Int. Conf. on Computer Vision* pp 9650–60

Hinton G, Vinyals O and Dean J 2015 Distilling the knowledge in a neural network *arXiv preprint* arXiv:[1503.02531](http://arxiv.org/abs/1503.02531)

Johnson J, Douze M and Jegou H 2019 Billion-scale similarity search with {GPUs} *IEEE Trans. Big Data* [**7** 535–47](http://dx.doi.org/10.1109/TBDATA.2019.2921572)

Kirillov A, Mintun E, Ravi N, Mao H, Rolland C, Gustafson L, Xiao T, Whitehead S, Berg A C and Lo W-Y 2023 Segment anything *arXiv preprint* arXiv:[2304.02643](http://arxiv.org/abs/2304.02643)

Oquab M, Darcet T, Moutakanni T, Vo H, Szafraniec M, Khalidov V, Fernandez P, Haziza D, Massa F and El-nouby A 2023 DINOv2: learning robust visual features without supervision *arXiv preprint* arXiv:[2304.07193](http://arxiv.org/abs/2304.07193)

Zhao X, Ding W, An Y, Du Y, Yu T, Li M, Tang M and Wang J 2023 Fast segment anything *arXiv preprint* arXiv:[2306.12156](http://arxiv.org/abs/2306.12156)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 12

## Applications of NeRF and 3D Gaussian splatting for synthesis of 3D scenes

This chapter is about the latest computer vision development by the end of 2023 for synthesis of 3D scenes. In the first section, MiDaS is used for image depth estimation. From Nvidia instant NeRF in the second section, the principle of neural radiance field (NeRF) is introduced about how to synthesize 3D scenes from a set of images by ray tracing. In the last section, a 2D Gaussian splatting program is used to introduce 3D Gaussian splatting for real-time rendering of 3D scenes by rasterization.

We are in a great age to develop machine learning algorithms for computers to have 3D vision about our world. Image depth estimation is a fundamental task in computer vision that enables machines to perceive the 3D structure of a scene from 2D. By accurately extracting objects’ depth information on images or video frames, computers can understand the spatial layout of objects on each image, and make the right decisions for actuators to interact with the environment effectively. NeRF (Mildenhall *et al* [2020](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib7)) and 3D Gaussian splatting (Kerbl *et al* [2023](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib3)) are two different techniques for creating 3D models from 2D images. NeRF is a novel technique that uses deep learning to model 3D scenes from a set of photos. It represents a scene as a continuous 3D function that predicts the color and opacity of each point in 3D space. NeRF aims to capture complex 3D scenes by training a neural network model to learn the underlying scene representation from multiple 2D images, allowing for the synthesis of novel views of 3D scenes. It has gained popularity for its ability to generate high-quality 3D reconstructions and novel views of scenes. However, NeRF takes heavy computations to synthesize 3D scenes, and it is not quick enough for real-time projects. A technique called ‘3D Gaussian splatting’ allows us to create photo-realistic 3D models from a set of images. It works by representing any scene with millions of 3D Gaussian particles. Each particle has a rugby ball shape whose size and orientation are decided by a 3D Gaussian covariance matrix with nine parameters. Each rugby ball has its own 3D position coordinates, RGB colors and opacity. These particles are then projected onto a 2D plane and blended together to create an image. 3D Gaussian splatting has several advantages over other radiance field methods, such as faster training and rendering, higher visual quality, 3D editability and better handling of empty space. A limit of 3D Gaussian splatting is its model training need a huge amount of GPU memory (24 GB).

### 12.1 Using MiDaS for image depth estimation

Traditionally, depth estimation relied heavily on expensive hardware, such as stereo cameras. The advent of machine learning has revolutionized the field of computer vision, including image depth estimation. In recent years, researchers have invented many techniques for image depth estimation. Some techniques use supervised learning, such as [MiDaS](https://github.com/isl-org/MiDaS) (Ranftl *et al* [2020](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib9)), whose models have been trained on 10 distinct datasets using multi-objective optimization to ensure high quality on a wide range of inputs. Using self-supervised vision transformers, Facebook's DINOv2 models can be used for image classification, instance retrieval, video understanding as well as semantic segmentation and depth estimation.

Before using any complex AI model to estimate image depth information, I would like to demonstrate a simple project about measuring distance between your face and your laptop camera by using libraries of OpenCV, [cvzone](https://github.com/cvzone/cvzone) and [mediapipe](https://google.github.io/mediapipe/). We also need a keychain tape to do some measurements for calibrations. We treat a laptop camera as a thin lens with a focal length (*f*). Usually, the value of *f* is about a few millimeters, and the object distance (*u*) of my face to the camera is around 500 mm. For example, my cellphone's focal length is 3.5 mm. With a condition *u* >> *f*, we get the image distance of the object ![image](images/bk978-0-7503-6244-3ch12ieqn23.gif) = *f* according to the thin lens equation shown in figure [12.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig1). If the height or width of an object is *H*, and the image height or width is *h*, we have an equation tan(*θ*) = *H*/*u* = *h*/*f*, from which we have a formula to measure the object distance for my codes in Project [12.1.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro1).

  
$$u = \\frac{f}{h}H.$$  
(12.1)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn24.gif" position="float"/

I measured the distance (*H*) between my two eye pupils with the keychain tape in front of a mirror, and found *H* = 65 (mm). Using a cvzone module [FaceMeshModule](https://github.com/Teachny-Teams/Face-Mesh/blob/master/FaceMeshModule.py) in the following Python codes, I can measure the image width (*h*) of my two eye pupils in pixels. Of course, the value of *h* changes with the distance of my face to the camera. The cvzone module can measure coordinates of 468 points on a face. The left eye is point 145, and the right eye is point 374. If you change an option on line 06 from False to True, you can see all 468 points. With the keychain tape to set the distance (*u*) between my face and my laptop camera to 220 mm, I found the value of *h* was 155 pixels. From equation ([12.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn1)), it is easy to estimate the focal length of my camera *f* = 525 (pixel). Two of the three parameters on the right sight of equation ([12.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn1)) are known constants now, and it is possible to use equation ([12.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn1)) to automatically measure my face distance to my laptop camera. Running codes in Project [12.1.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro1) to measure the distance, I read the distance values on screen and compare them with my keychain tape's measurements. After the calibration, I need to adjust the focal length to 600 pixels on line 14. My codes were inspired by Murtaza's [YouTube](https://www.youtube.com/watch?v=jsoe1M2AjFk) video.

![](images/bk978-0-7503-6244-3ch12uf1_pr.gif)

![Figure 12.1. Parameters of a thin lens system for measuring face distance in front of a laptop camera.](images/bk978-0-7503-6244-3ch12f1_online.jpg)

**Figure 12.1.** Parameters of a thin lens system for measuring face distance in front of a laptop camera.

Codes of Project [12.1.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro1) work well to measure the absolute distance between your face and your webcam in real time, but make an issue. If I cover one eye while the codes are running, the program will crash, because the program cannot find the standard object to measure its length for calculations of the absolute distance. Using a monocular camera to extract image depth information is not an easy job. It is dependent on optical settings of cameras. [MiDaS](https://github.com/isl-org/MiDaS) models released by Intelligent Systems Lab [Organization](https://github.com/isl-org/MiDaS) give us power to estimate [relative image depth](https://colab.research.google.com/github/pytorch/pytorch.github.io/blob/master/assets/hub/intelisl_midas_v2.ipynb#scrollTo=prerequisite-greeting) information about images and videos from different sources for many kinds of objects. The right-side image in figure [12.2](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig2) is an output image of Project [12.1.2](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro2). The names of three pre-trained models are listed on line 04. Only a small-size model (82 MB) was used in the project. The size of a big model is more than 1.2 GB. There is no significant visual difference between the outputs of the two models in my laptop, and it is much slower to use the big model. The right leg of a woman on the right of the original image was close to my camera, so the pixels of the leg are brighter on the relative depth image. Since two women on the left side of the original image were far away from my camera, their pixels are not as bright as the pixels of the right woman on the relative depth image. Copy Cell 05 and 07 in Project [7.5](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn23) and paste them after Cell 02 (change function name ‘yolov3’ to ‘midas’), we can use the function defined in Cell 02 to process images in a folder or video frame from a camera. The speed for processing video is about 30 FPS. I met an issue in running codes in the project. After using *pip install timm* to install *safetensors* and *timm* in my VS Code virtual environment with Python v3.9, the codes then work well.

![](images/bk978-0-7503-6244-3ch12uf2_pr.gif)

![Figure 12.2. (Left) original image; (right) relative depth image extracted by a pre-trained small MiDaS model.](images/bk978-0-7503-6244-3ch12f2_online.jpg)

**Figure 12.2.** (Left) original image; (right) relative depth image extracted by a pre-trained small MiDaS model.

### 12.2 Neural Radiance Fields (NeRF) for synthesis of 3D scenes

There is another computer vision technique called Neural Radiance Fields (Li *et al* [2022](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib4)) (NeRF) which can also be used for image depth estimation. However, the most impressive function of NeRF is to synthesize a 3D model of objects from a set of 2D images taken around these objects, and the data of the 3D model can then be used by other software such as [Meshlab](https://www.meshlab.net/) for 3D print. From high school mathematics, we can derive formulae to extract 3D information of objects from two images taken by a camera in two positions. That is why many kinds of animals and insects have two eyes to get stereo vision of our world as a result of evolution. Using 20∼100 images taken by a camera around objects, NeRF has enough data to synthesize 3D scenes with smart algorithms. The original NeRF paper (Mildenhall *et al* [2020](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib7)) was published in August 2020. Since model training time of NeRF is very slow (many hours or even days), many models based on the original NeRF were proposed in recent years. Nvidia's instant NeRF (Müller *et al* [2022](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib8)) can synthesize 3D scenes from images in a few seconds. We do not even need to install Python files from Nvidia's [GitHub](https://github.com/NVlabs/instant-ngp) website, because Nvidia provides an executable binary file [instant-ngp.exe](https://github.com/NVlabs/instant-ngp/releases/download/continuous/Instant-NGP-for-RTX-2000.zip) to download for a Windows operating system. According to the instructions of the GitHub website, I used my cellphone to take 35 photos around a sculpture about a bull and a cow shown in figure [12.3](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig3). To save computer time, I resized the resolution of these images from 4096×2304 to 843×474. Using [Colmap](https://colmap.github.io/) and [colmap2nerf.py](https://github.com/NVlabs/instant-ngp/blob/master/scripts/colmap2nerf.py), I obtained a *transforms.json* file about *Intrinsic parameters* of my camera listed below. In the file, each image has a 4×4 *Transform Matrix* which is used to convert pixel coordinates of each image to 3D world coordinates for each object in the image.

![](images/bk978-0-7503-6244-3ch12uf3_pr.gif)

![Figure 12.3. One of 35 photos of a 3D sculpture for NeRF to synthesize 3D scenes.](images/bk978-0-7503-6244-3ch12f3_online.jpg)

**Figure 12.3.** One of 35 photos of a 3D sculpture for NeRF to synthesize 3D scenes.

#### 12.2.1 Camera intrinsic and extrinsic matrices

We used a lot of photos from digital cameras for model training in computer vision projects. A digital camera projects objects in our 3D world to its 2D photon sensor (a CCD or CMOS array) to create digital images. With NeRF techniques, we could use a set of images to reconstruct or synthesize 3D scenes of objects in the 3D world. To understand NeRF, we need to know four Cartesian coordinate systems in a digital camera. As shown in figure [12.4](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig4), they are the world coordinate system, the camera coordinate system, the image coordinate system and the sensor coordinate system. In the first one, the *z*[*w*]\-axis direction is upward and the *x*[*w*]*–y*[*w*] plane is horizontal. Relative to the fixed real-world coordinate system, a movable camera coordinate system's *z*[*c*]\-axis is parallel with the *y*[*w*]\-axis before the camera is moved and rotated, and its *x*[*c*]\-axis could be in any direction. For simplicity, I set the *x*[*c*]\-axis and the *x*[*w*]\-axis in opposite directions. To a 3D world vector *X⃗*[*w*] = \[1,1,1\]^(*T*)inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn25.gif"/, we are sure that the vector in the camera coordinate system is *X⃗*[*c*] = \[−1,1,101\]^(*T*)inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn26.gif"/ if the camera is at a position set by a real-world vector *C⃗*[*w*] = \[0,−100,0\]^(*T*)inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn27.gif"/. From the vector *C⃗*[*w*]inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn28.gif"/, we know the distance between the two coordinate systems is 100. The unit of these coordinates could be millimeter (mm). From the figure, we have an equation to calculate the coordinates of the 3D world point \[1,1,1\] in the camera system *X⃗*[*c*] = *R* ⋅ (*X⃗*[*w*]−*C⃗*[*w*]) = *R* ⋅ *X⃗*[*w*] + *t⃗*inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn29.gif"/, where *R* is an orthonormal matrix about rotation operations, and *t⃗* =  − *R* ⋅ *C⃗*[*w*] = \[0,0,100\]^(*T*)inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn30.gif"/ is about a transposition operation of the camera coordinate system to the real-world system. From the coordinates of *t⃗*inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn31.gif"/, we know the position of the origin of the world coordinate system in the camera system. We also have *R*^( − 1) = *R*^(*T*)inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn32.gif"/ and *R**R*^(*T*) = *R*^(*T*)*R* = 1inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn33.gif"/.

  
$$R = \\begin{bmatrix} r\_{11} & r\_{12} & r\_{13} \\\\ r\_{21} & r\_{21} & r\_{23} \\\\ r\_{31} & r\_{32} & r\_{33} \\\\ \\end{bmatrix} = \\begin{bmatrix} {{\\overrightarrow{x}}\_{c} \\cdot {\\overrightarrow{x}}\_{w}} & {{\\overrightarrow{x}}\_{c} \\cdot {\\overrightarrow{y}}\_{w}} & {{\\overrightarrow{x}}\_{c} \\cdot {\\overrightarrow{z}}\_{w}} \\\\ {{\\overrightarrow{y}}\_{c} \\cdot {\\overrightarrow{x}}\_{w}} & {{\\overrightarrow{y}}\_{c} \\cdot {\\overrightarrow{y}}\_{w}} & {{\\overrightarrow{y}}\_{c} \\cdot {\\overrightarrow{y}}\_{w}} \\\\ {{\\overrightarrow{z}}\_{c} \\cdot {\\overrightarrow{x}}\_{w}} & {{\\overrightarrow{z}}\_{c} \\cdot {\\overrightarrow{x}}\_{w}} & {{\\overrightarrow{z}}\_{c} \\cdot {\\overrightarrow{x}}\_{w}} \\\\ \\end{bmatrix} = \\begin{bmatrix} {- \\ 1} & 0 & 0 \\\\ 0 & 0 & 1 \\\\ 0 & 1 & 0 \\\\ \\end{bmatrix}$$  
(12.2)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn34.gif" position="float"/

For mathematical convenience, we use a 4D vector to represent a 3D vector in the world and camera coordinate systems: *χ̃*[*w*] = \[*x*[*w*],*y*[*w*],*z*[*w*],1\]^(*T*)inline-graphic style="height:1.6875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn35.gif"/ and *χ̃*[*c*] = \[*x*[*c*],*y*[*c*],*z*[*c*],1\]^(*T*)inline-graphic style="height:1.6875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn36.gif"/. The 4D vector is a homogeneous representation of a 3D vector, and the fourth coordinate is a fictitious number not equal to zero. A relationship between the two new vectors is set by equation ([12.3](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn3)), where the 4×4 matrix is called an *Extrinsic Matrix* of the camera for a photo.

  
$${\\widetilde{\\chi}}\_{c} = \\begin{bmatrix} x\_{c} \\\\ y\_{c} \\\\ z\_{c} \\\\ 1 \\\\ \\end{bmatrix} = \\begin{bmatrix} r\_{11} & r\_{12} & r\_{13} & t\_{x} \\\\ r\_{21} & r\_{22} & r\_{23} & t\_{y} \\\\ r\_{31} & r\_{32} & r\_{33} & t\_{x} \\\\ 0 & 0 & 0 & 1 \\\\ \\end{bmatrix}\\begin{bmatrix} x\_{w} \\\\ y\_{w} \\\\ z\_{w} \\\\ 1 \\\\ \\end{bmatrix} = \\begin{bmatrix} R\_{3 \\times 3} & t \\\\ 0\_{1 \\times 3} & 1 \\\\ \\end{bmatrix}{\\widetilde{\\chi}}\_{w}$$  
(12.3)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn37.gif" position="float"/

The vector *X⃗*[*c*]inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn38.gif"/ is then projected to the 2D image coordinate system by the camera, as shown in figure [12.4](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig4). Since the focus of the camera is only a few millimeters (*f << z*[*c*]), the image coordinate system is on the focal plane of the camera. Based on Optics, we have the coordinates of the image in the images coordinate system $x\_{i} = \\frac{x\_{c}}{z\_{c}}f$inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch12ieqn39.gif"/ and $y\_{i} = \\frac{y\_{c}}{z\_{c}}f$inline-graphic style="height:1.8125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn40.gif"/. A digital camera uses millions of tiny CCD or CMOS sensors to detect photons. The sensor densities on the *u*\-axis and the ![image](images/bk978-0-7503-6244-3ch12ieqn41.gif)\-axis are *m*[*x*] and *m*[*y*], respectively. The unit of sensor density is the number of sensors per millimeter. It is possible that *m*[*x*] and *m*[*y*] are not the same. The origin point of a digital image is usually set at the top-left corner of the image (view from the back of the 2D image sensor chip). In the sensor coordinate system, each pixel's coordinates (*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn42.gif)) are integers: $u = m\_{x}f\\frac{x\_{c}}{z\_{c}} + o\_{u} = f\_{x}\\frac{x\_{c}}{z\_{c}} + o\_{u}$inline-graphic style="height:1.75em;" xlink:href="bk978-0-7503-6244-3ch12ieqn43.gif"/, ![image](images/bk978-0-7503-6244-3ch12ieqn44.gif), where *f*[*x*], *f*[*y*], *o*[*u*], *o*[![image](images/bk978-0-7503-6244-3ch12ieqn45.gif)] are the camera's intrinsic parameters. They have a same unit: pixel. The coordinates of the principle center of the 2D image sensor chip are *O*(*o*[*u*], *o*[![image](images/bk978-0-7503-6244-3ch12ieqn46.gif)]) in the sensor coordinate system. If an image's resolution is 1024×768, the principle center of the image could be *O*(512 384).

![Figure 12.4. A digital camera's four Cartesian coordinate systems for NeRF. From right to left, they are the world coordinate system, the camera coordinate system, the image coordinate system and the sensor coordinate system.](images/bk978-0-7503-6244-3ch12f4_online.jpg)

**Figure 12.4.** A digital camera's four Cartesian coordinate systems for NeRF. From right to left, they are the world coordinate system, the camera coordinate system, the image coordinate system and the sensor coordinate system.

For the same reason, we use a 3D homogeneous representation for the 2D sensor coordinates in equation ([12.4](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn4)), where *M*[int] is the *Intrinsic Matrix* of the camera. With equation ([12.3](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn3)) and ([12.4](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn4)), we get equation ([12.5](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn5)), which is used to project a real-world vector to the sensor coordinate system, where *P* is the *Projection Matrix* of the camera with 12 unknown parameters.

  
$$\\widetilde{\\zeta} = \\begin{bmatrix} u \\\\ v \\\\ 1 \\\\ \\end{bmatrix} \\equiv \\begin{bmatrix} \\widetilde{u} \\\\ \\widetilde{v} \\\\ \\widetilde{w} \\\\ \\end{bmatrix} = \\begin{bmatrix} {uz\_{c}} \\\\ {vz\_{c}} \\\\ z\_{c} \\\\ \\end{bmatrix} = \\begin{bmatrix} f\_{x} & 0 & o\_{u} & 0 \\\\ 0 & f\_{y} & o\_{v} & 0 \\\\ 0 & 0 & 1 & 0 \\\\ \\end{bmatrix}\\begin{bmatrix} x\_{c} \\\\ y\_{c} \\\\ z\_{c} \\\\ 1 \\\\ \\end{bmatrix} = M\_{int} \\cdot {\\widetilde{\\chi}}\_{c}$$  
(12.4)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn47.gif" position="float"/

  
$$\\widetilde{\\widetilde{\\zeta}} = M\_{int} \\cdot {\\widetilde{\\chi}}\_{c} = M\_{int} \\cdot M\_{\\mathit{ext}} \\cdot {\\widetilde{\\chi}}\_{w} = \\begin{bmatrix} p\_{11} & p\_{12} & p\_{13} & p\_{14} \\\\ p\_{21} & p\_{22} & p\_{23} & p\_{24} \\\\ p\_{31} & p\_{32} & p\_{33} & p\_{34} \\\\ \\end{bmatrix}\\begin{bmatrix} x\_{w} \\\\ y\_{w} \\\\ z\_{w} \\\\ 1 \\\\ \\end{bmatrix} = P \\cdot {\\widetilde{\\chi}}\_{w}$$  
(12.5)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn48.gif" position="float"/

Using an image of an object with six (or more) known real-world coordinates, it is possible to get their pixel coordinates in the sensor coordinate system. For example, the first real-world coordinates \[*x*[*w*1], *y*[*w*1], *z*[*w*1]\]^(*T*) is projected to the sensor coordinate system as \[*u*[1],![image](images/bk978-0-7503-6244-3ch12ieqn49.gif)[1]\]^(*T*), and they are known by measurements. Taking them to equation ([12.4](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn4)) for all six points, we got the following equation *A* ⋅ *p* = 0inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn50.gif"/.

  
$$\\begin{bmatrix} x\_{w1} & y\_{w1} & z\_{w1} & 1 & 0 & 0 & 0 & 0 & {- \\ u\_{1}x\_{w1}} & {- \\ u\_{1}y\_{w1}} & {- \\ u\_{1}z\_{w1}} & {- \\ u\_{1}} \\\\ 0 & 0 & 0 & 0 & x\_{w1} & y\_{w1} & z\_{w1} & 1 & {- \\ v\_{1}x\_{w1}} & {- \\ v\_{1}y\_{w1}} & {- \\ v\_{1}z\_{w1}} & {- \\ v\_{1}} \\\\ x\_{w2} & y\_{w2} & z\_{w3} & 1 & 0 & 0 & 0 & 0 & {- \\ u\_{2}x\_{w2}} & {- \\ u\_{2}y\_{w2}} & {- \\ u\_{2}z\_{w2}} & {- \\ u\_{2}} \\\\ 0 & 0 & 0 & 0 & x\_{w2} & y\_{w2} & z\_{w2} & 1 & {- \\ v\_{2}x\_{w2}} & {- \\ v\_{2}y\_{w2}} & {- \\ v\_{2}z\_{w2}} & {- \\ v\_{2}} \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ x\_{w6} & y\_{w6} & z\_{w6} & 1 & 0 & 0 & 0 & 0 & {- \\ u\_{6}x\_{w6}} & {- \\ u\_{6}y\_{w6}} & {- \\ u\_{6}z\_{w6}} & {- \\ u\_{6}} \\\\ 0 & 0 & 0 & 0 & x\_{w6} & y\_{w6} & z\_{w6} & 1 & {- \\ v\_{6}x\_{w6}} & {- \\ v\_{6}y\_{w6}} & {- \\ v\_{6}z\_{w6}} & {- \\ v\_{6}} \\\\ \\end{bmatrix}\\begin{bmatrix} p\_{11} \\\\ p\_{12} \\\\ p\_{13} \\\\ p\_{14} \\\\ p\_{21} \\\\ p\_{22} \\\\ p\_{23} \\\\ p\_{24} \\\\ p\_{31} \\\\ p\_{32} \\\\ p\_{33} \\\\ p\_{34} \\\\ \\end{bmatrix} = \\begin{bmatrix} 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ 0 \\\\ \\end{bmatrix}$$  
graphic xlink:href="bk978-0-7503-6244-3ch12ueqn53.gif" position="float"/

This is a homogeneous least squares problem (Inkilä, [2005](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib2)). The 12 unknown parameters in the matrix *p* can be obtained by solving an eigenequation *A*^(*T*)*A**p* = *λ**p*inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch12ieqn52.gif"/ under two conditions:  ∥ *A* ⋅ *p*∥² = min inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch12ieqn53.gif"/ and *p*^(*T*) ⋅ *p* = 1inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch12ieqn54.gif"/. We can us [Colmap](https://colmap.github.io/) and [colmap2nerf.py](https://github.com/NVlabs/instant-ngp/blob/master/scripts/colmap2nerf.py) to calculate the 12 parameters for each image automatically.

#### 12.2.2 Using MLP with Gaussian Fourier feature mapping to reconstruct images

In any NeRF project, the hardest part is pre-processing image pixels \[*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn55.gif)\] to get 3D world coordinates \[*x*[*w*], *y*[*w*], *z*[*w*]\] of objects. NeRF models and model training are easy. We would like to work on easy jobs at first. A fully connected multi-layer neural network is called a multilayer perceptron (MLP). We have used MLPs in transformer models in chapter [10](#Chapter_10.xhtml#bk978-0-7503-6244-3ch10); two fully connected layers were used in chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2) for nonlinear regressions to numerically simulate any functions. Using an image's pixel coordinates (*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn56.gif)) and RGB colors (r, g, b) as two datasets, an MLP model can even simulate and reconstruct the image. Pre-processing raw input data is very important for any machine learning project, often crucial for model training results. If an image's resolution is 512×inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn57.gif"/512, we need to normalize each pixel's *u* and ![image](images/bk978-0-7503-6244-3ch12ieqn58.gif) values from \[0, 511\] to \[-1, 1\], and its RGB values from \[0, 255\] to \[0, 1\].

We have an issue about the quality of the reconstructed or predicted image, because a standard MLP model fails to learn image details in high frequencies (Tancik *et al* [2020](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib10)). Comparing the ground truth image shown in figure [12.5](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig5)A, you can see that it is impossible to find a single hair on the head of a tamias shown in figure [12.5](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig5)B, which is the output of Cell 10 in the following Project [12.2.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro4) without position encoding. By using Fourier features for positional encoding of the ground truth \[*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn59.gif)\] coordinates with codes in Cell 04, we have the output of the same MLP model shown in figure [12.5](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig5)C which is almost the same as the ground truth. We use a metrics PSNR (peak signal- to-noise ratio) to indicate the similarity of two images. In equation ([12.6](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn6)), MSE is the mean squared error of RGB colors between the reconstructed image and the ground truth, and the MSE loss function is used for model training.

  
*P**S**N**R* =  − 10 log [10](*M**S**E*)  
(12.6)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn60.gif" position="float"/

![](images/bk978-0-7503-6244-3ch12uf4a_pr.gif)

![](images/bk978-0-7503-6244-3ch12uf4b_pr.gif)

![Figure 12.5. (A) Ground truth image; (B) a predicted image without position encoding; (C) a predicted image with Gaussian Fourier feature mapping for image position encoding. Model training time is less than 10 min.](images/bk978-0-7503-6244-3ch12f5_online.jpg)

**Figure 12.5.** (A) Ground truth image; (B) a predicted image without position encoding; (C) a predicted image with Gaussian Fourier feature mapping for image position encoding. Model training time is less than 10 min.

Codes in Cell 01–02 are used to import libraries, set hyperparameters, input and display an image named ‘Tamias.jpg’. The [Kornia](https://kornia.readthedocs.io/en/latest/get-started/introduction.html) library is ‘a differentiable library that allows classical computer vision to be integrated into deep learning models’. A class defined in Cell 03 uses 75% pixels of the image for a train dataset, and 25% pixels for a validation dataset. Each of the datasets is then sliced into a dataloader with a batch size of 4096 pixels. Codes in Cell 04 are used to encode \[*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn61.gif)\] coordinates in each batch (υ) of a dataloader with Gaussian Fourier feature mapping according to the following formulae, in which the matrix B was sampled from an isotropic Gaussian distribution. The constant 10 on the first line of Cell 04 is a critical hyperparameter according to [Matthew Tancik](https://colab.research.google.com/github/tancik/fourier-feature-networks/blob/master/Demo.ipynb). You can try to use 1 or 100 to replace 10 to generate B to see the quality of the reconstructed image. The input for equation ([12.7](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn7)) is a batch of image coordinates with shape \[4096, 2\], and the output shape is \[4096, 256\]. A sin function and a cos function element-wisely acted on the output, respectively, and they are then concatenated into a matrix with shape \[4096, 512\] as shown in equation ([12.8](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn8)). The code ‘@property’ in Cell 04 is for a function named ‘out\_dim’ which will be used in the MLP model's first fully connected layer. If you do not want position encoding in the project, replace the code ‘x=pe(uv)’ by ‘x=uv’ in the forward function of the MLP model class defined in Cell 05, and also replace ‘n\_in=pe.out\_dim’ by ‘n\_in=2’ in the model instance. Codes in Cell 10 use all pixels in the image to construct a dataloader with only one batch. The trained model uses the batch to predict or reconstruct a predicted image shown in figure [12.5](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig5)C.

  
$$2\\pi\*\\upsilon \\cdot B = 2\\pi\*\\begin{bmatrix} u\_{1} & v\_{1} \\\\ u\_{2} & v\_{2} \\\\ {.\\ ..} & {.\\ ..} \\\\ u\_{4096} & v\_{4096} \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} B\_{1,1} & B\_{1,2} & {.\\ ..} & B\_{1,256} \\\\ B\_{2,1} & B\_{2,2} & {.\\ ..} & B\_{2,256} \\\\ \\end{bmatrix}$$  
(12.7)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn62.gif" position="float"/

  
*γ*(*υ*) = *c**a**t*\[sin(2*π*\**υ*⋅*B*),cos(2*π*\**υ*⋅*B*)\]  
(12.8)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn63.gif" position="float"/

![](images/bk978-0-7503-6244-3ch12uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch12uf6_pr.gif)

#### 12.2.3 The physics principle of render volume density in NeRF

In order to get compatible results with [Colmap](https://colmap.github.io/), I will use the coordinate systems shown in figure [12.6](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig6). There is a virtual ray starting from each pixel \[*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn64.gif)\] on an image. After passing through the camera center (the origin of the camera coordinate system), the ray penetrates through objects like an x-ray. There are infinite points on each ray. To save computer time, we have to set a near threshold (*L*[n]) and a far threshold (*L*[f]) on the *z*[*c*]\-axis, and choose *N* points on the line between the two thresholds. The sample number *N* could be 32, 64, 128, …, 1024, or any other integers. The bigger the sample number *N*, the better NeRF results would be, but the model training time would be longer. The distance between two neighbour points on the *z*[*c*]\-axis is *d* = (*L*[f] – *L*[n])/(*N* – 1). We will then get a point on the ray corresponding to a point on *z*[*c*]\-axis between *L*[n] and *L*[f]. Those points on the ray are query points. In the case where our image resolution is 100×100, and number of samples on each ray is 32, we would have 320 000 query points for each image in model training.

![Figure 12.6. NeRF coordinate systems in their initial orientations. The camera can move around the fixed world coordinate system. The angle of the camera moving around zw-axis has a name theta: \\mathbf{\\theta} \\in \\left\\lbrack 0,2\\mathbf{\\pi} \\right\\rbrack on the xw–yw plane, and the angle of the camera moving around the xw-axis has a name phi: \\mathbf{\\varphi} \\in \\left\\lbrack - \\mathbf{\\pi},\\mathbf{\\pi} \\right\\rbrack on the yw–zw plane. (r = 4; zc//yw: \\mathbf{\\theta} = 0, \\mathbf{\\varphi} = 0; zc//xw: \\mathbf{\\theta} = 90^{\\mathbf{o}}; zc//zw: \\mathbf{\\varphi} = {- 90}^{\\mathbf{o}}).](images/bk978-0-7503-6244-3ch12f6_online.jpg)

**Figure 12.6.** NeRF coordinate systems in their initial orientations. The camera can move around the fixed world coordinate system. The angle of the camera moving around *z*[*w*]\-axis has a name theta: **θ** ∈ \[0,2**π**\]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn1.gif"/ on the *x*[*w*]–*y*[*w*] plane, and the angle of the camera moving around the *x*[*w*]\-axis has a name phi: **φ** ∈ \[−**π**,**π**\]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn2.gif"/ on the *y*[*w*]–*z*[*w*] plane. (*r* = 4; *z*[*c*]//*y*[*w*]: **θ** = 0inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn3.gif"/, **φ** = 0inline-graphic style="height:1em;" xlink:href="bk978-0-7503-6244-3ch12ieqn4.gif"/; *z*[*c*]//*x*[*w*]: **θ** = 90^(**o**)inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn5.gif"/; *z*[*c*]//*z*[*w*]: **φ** =  − 90^(**o**)inline-graphic style="height:1em;" xlink:href="bk978-0-7503-6244-3ch12ieqn6.gif"/).

In Cell 05 of Project [12.2.2](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro5) listed in appendix [K](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-K), a tiny NeRF model's output has a name, *radiance\_field*, and the shape of the radiance field is \[100, 100, 32, 4\] for each of 10 000 pixels with 32 query points per ray. Each radiance field point on the ray corresponds to a query point. The four parameters of a radiance field point are for three colors (r, g, b) and a density (σ). Now we treat each radiance field point as a tiny LED light source with RGB colors. The light intensity emitted by a point with a density (σ) is proportional to *α* = 1 − *e*^( − *σ* ⋅ *d*)inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn65.gif"/. If there is nothing at the query point, a tiny space or volume around the point is transparent and its density is *σ* = 0inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn66.gif"/. This point will not emit light because of *α* = 0inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn67.gif"/. The contribution of the first radiance field point to a pixel on a predicted image is \[*α*[1]*r*[1], *α*[1]*g*[1], *α*[1]*b*[1]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch12ieqn68.gif"/\]. If *σ*[1]inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn69.gif"/ is a bigger positive number, the second radiance field point's light will be partially blocked by point 1. The blocking percentage is equal to *α*[1]inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn70.gif"/, and the remain percentage is equal to *β*[1] = 1 − *α*[1]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch12ieqn71.gif"/. The contribution of the second point to the pixel's color on the predicted image is \[*α*[2]*r*[2],*α*[2]*g*[2],*α*[2]*b*[2]\]*β*[1]inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn72.gif"/. The contribution of the last query point to the pixel's color is $\\left\\lbrack \\alpha\_{32}r\_{32},\\alpha\_{32}g\_{32},\\alpha\_{32}b\_{32} \\right\\rbrack\\prod\\limits\_{i = 1}^{31}\\beta\_{i}$inline-graphic style="height:2.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn73.gif"/. The following table is a summery of the above explanations. The sum of each color column in the table is a color of a pixel on the predicted image. A function *render\_volume\_density* defined in Cell 06 of the Project is used to do the above calculations. An MSE loss function is used in Cell 05 to compare color difference between ground truth and the predicted image during model training.

When we use *α*inline-graphic style="height:0.6875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn74.gif"/ or *β*inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn75.gif"/ to calculate light blockage of a query point to its neighbour query point on a ray, the distance of the two points should be along the ray. How can we find world coordinates of 32 points on each ray starting from an image pixel at \[*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn76.gif)\]? There are two steps. The first step is to convert \[*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn77.gif)\] of a pixel in the sensor coordinate system to \[*x*[*c*], *y*[*c*], *z*[*c*]\] in the camera coordinate system, and the second step is to convert \[*x*[*c*], *y*[*c*], *z*[*c*]\] to \[*x*[*w*], *y*[*w*], *z*[*w*]\] in the world coordinate system. For simplicity, we suppose that the principle center of the 2D image sensor chip is at *O*(*W*/2,*H*/2), where *W* and *H* are the width and height of the image sensor chip in a unit of pixel. The camera in figure [12.6](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig6) has a conjugate focal plane at *z*[*c*] = –*f*. We project the camera's focal plane at *z*[*c*] = *f* to the conjugate focal plane, on which the *u*\-axis is parallel with the *x*[*c*]\-axis and the ![image](images/bk978-0-7503-6244-3ch12ieqn78.gif)\-axis is in opposite direction to *y*[*c*]\-axis. An angle between the ray and the *x*[*c*]\-axis is equal to $\\arctan\\left\\lbrack \\left( u - \\frac{W}{2} + 0.5 \\right)/f \\right\\rbrack$inline-graphic style="height:2em;" xlink:href="bk978-0-7503-6244-3ch12ieqn79.gif"/, and an angle between the ray and the *y*[*c*]\-axis is equal to ![image](images/bk978-0-7503-6244-3ch12ieqn80.gif). At a plane with *z*[*c*] = –1 in the camera coordinate system, the \[*u*, ![image](images/bk978-0-7503-6244-3ch12ieqn81.gif)\] is converted to \[*x*[*c*], *y*[*c*], *z*[*c*]\] = \[$\\left( u - \\frac{W}{2} + 0.5 \\right)/f$inline-graphic style="height:2em;" xlink:href="bk978-0-7503-6244-3ch12ieqn82.gif"/, ![image](images/bk978-0-7503-6244-3ch12ieqn83.gif), -1\]. A set of these camera coordinates has a name ‘ray\_directions’ in the *get\_ray\_bundle* function defined in Cell 04. Each query point on the ray has a depth value: *d*[*i*] = *L*[*n*] + *i*\**d*, where *i* ∈ \[0,(*N*−1)\]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn84.gif"/. Using a query point's depth values to multiply the ray\_directions, we will get all the query point's camera coordinates: \[*x*[*c*], *y*[*c*], *z*[*c*]\] = \[$\\left. u - \\frac{W}{2} + 0.5 \\right)d\_{i}/f$inline-graphic style="height:2em;" xlink:href="bk978-0-7503-6244-3ch12ieqn85.gif"/, $\\left( u - \\frac{H}{2} + 0.5 \\right)d\_{i}/f$inline-graphic style="height:2em;" xlink:href="bk978-0-7503-6244-3ch12ieqn86.gif"/, - *d*[*i*]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn87.gif"/\]. To convert camera coordinates \[*x*[*c*], *y*[*c*], *z*[*c*]\] = \[1,1,–5\] in the figure, we need to use a formula: *X⃗*[*w*] = *R* ⋅ (*X⃗*[*c*] − *W⃗*[*c*]) = *R* ⋅ *X⃗*[*c*] − *R* ⋅ *W⃗*[*c*]  = *R* ⋅ *X⃗*[*c*] + *C⃗*[*w*]inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn88.gif"/, where *W⃗*[*c*]inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn89.gif"/ is a vector for the origin of the world coordinate system in the camera system, and *C⃗*[*w*]inline-graphic style="height:1.375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn90.gif"/ is a vector for the camera origin in the world coordinate system.

  
$$\\begin{bmatrix} x\_{w} \\\\ y\_{w} \\\\ z\_{w} \\\\ \\end{bmatrix} = \\begin{bmatrix} {{\\overrightarrow{x}}\_{w} \\cdot {\\overrightarrow{x}}\_{c}} & {{\\overrightarrow{x}}\_{w} \\cdot {\\overrightarrow{y}}\_{c}} & {{\\overrightarrow{x}}\_{w} \\cdot {\\overrightarrow{z}}\_{c}} \\\\ {{\\overrightarrow{y}}\_{w} \\cdot {\\overrightarrow{x}}\_{c}} & {{\\overrightarrow{y}}\_{w} \\cdot {\\overrightarrow{y}}\_{c}} & {{\\overrightarrow{y}}\_{w} \\cdot {\\overrightarrow{z}}\_{c}} \\\\ {{\\overrightarrow{z}}\_{w} \\cdot {\\overrightarrow{x}}\_{c}} & {{\\overrightarrow{z}}\_{w} \\cdot {\\overrightarrow{y}}\_{c}} & {{\\overrightarrow{z}}\_{w} \\cdot {\\overrightarrow{z}}\_{c}} \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} x\_{c} \\\\ y\_{c} \\\\ z\_{c} \\\\ \\end{bmatrix} = \\begin{bmatrix} {- \\ 1} & 0 & 0 \\\\ 0 & 0 & 1 \\\\ 0 & 1 & 0 \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} 0 \\\\ 0 \\\\ {- \\ r} \\\\ \\end{bmatrix}$$  
graphic xlink:href="bk978-0-7503-6244-3ch12ueqn50.gif" position="float"/

You would see that the world coordinates of the camera are equal to the last column of *R* multiplied by the distance (*r*) between the two coordinate systems. The set of the world coordinates of the camera has a name ‘ray\_origins’ in the ‘get\_ray\_bundle’ function defined in Cell 04. Because the image is virtually projected on the conjugate focal plane, we can ignore the focal plane, so that all rays of the image start from the camera's center (ray\_origins). In the initial NeRF coordinate systems shown in figure [12.6](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig6), the camera can move around the fixed world coordinate system. The angle of the camera moving around *z*[*w*]\-axis has a name theta: *θ* ∈ \[0,2*π*\]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn92.gif"/ on the *x*[*w*]–*y*[*w*] plane, and the angle of the camera moving around the *x*[*w*]\-axis has a name phi: *φ* ∈ \[−*π*,*π*\]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn93.gif"/ on the *y*[*w*]–*z*[*w*] plane (*z*[*c*]//*y*[*w*]: *θ* = 0inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn94.gif"/, *φ* = 0inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn95.gif"/; *z*[*c*]//*x*[*w*]: *θ* = *π*/2inline-graphic style="height:1em;" xlink:href="bk978-0-7503-6244-3ch12ieqn96.gif"/; *z*[*c*]//*z*[*w*]: *φ* =  − *π*/2inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn97.gif"/). In the case where the camera rotates an angle *φ*inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn98.gif"/ around the *x*[*w*]\-axis, and then an angle *θ*inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn99.gif"/ around the *z*[*w*]\-axis, the coordinates of the *X⃗*[*w*]inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn100.gif"/ in the world coordinate system can be found by a new rotation matrix *R*:

  
$$R = \\begin{bmatrix} {\\cos\\left( \\theta \\right)} & {\\sin\\left( \\theta \\right)} & 0 \\\\ {- \\ \\sin\\left( \\theta \\right)} & {\\cos\\left( \\theta \\right)} & 0 \\\\ 0 & 0 & 1 \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} 1 & 0 & 0 \\\\ 0 & {\\cos\\left( \\varphi \\right)} & {\\sin\\left( \\varphi \\right)} \\\\ 0 & {- \\ \\sin\\left( \\varphi \\right)} & {\\cos\\left( \\varphi \\right)} \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} {- \\ 1} & 0 & 0 \\\\ 0 & 0 & 1 \\\\ 0 & 1 & 0 \\\\ \\end{bmatrix}$$  
graphic xlink:href="bk978-0-7503-6244-3ch12ueqn51.gif" position="float"/

  
$$\\mathit{pose} = c2w(\\theta,\\varphi,r) = \\begin{bmatrix} {- \\ \\cos\\left( \\theta \\right)} & {\\sin\\left( \\theta \\right)\\sin\\left( \\varphi \\right)} & {\\sin\\left( \\theta \\right)\\cos\\left( \\varphi \\right)} & {r{\\ \\sin}\\left( \\theta \\right)\\cos\\left( \\varphi \\right)} \\\\ {\\sin\\left( \\theta \\right)} & {\\cos\\left( \\theta \\right)\\sin\\left( \\varphi \\right)} & {\\cos\\left( \\theta \\right)\\cos\\left( \\varphi \\right)} & {r{\\ \\cos}\\left( \\theta \\right)\\cos\\left( \\varphi \\right)} \\\\ 0 & {\\cos\\left( \\varphi \\right)} & {- \\ \\sin\\left( \\varphi \\right)} & {- \\ r{\\ \\sin}\\left( \\varphi \\right)} \\\\ 0 & 0 & 0 & 1 \\\\ \\end{bmatrix}$$  
graphic xlink:href="bk978-0-7503-6244-3ch12ueqn52.gif" position="float"/

The 3 × 3inline-graphic style="height:1em;" xlink:href="bk978-0-7503-6244-3ch12ieqn103.gif"/ sub-matrix on the top-left corner of the *pose* matrix is equal to the new rotation matrix *R*. From the top 3 × 1inline-graphic style="height:1em;" xlink:href="bk978-0-7503-6244-3ch12ieqn104.gif"/ sub-matrix in the last column of the *pose*, we get a ray origin, or the camera's world coordinates after the camera is rotated, where *r* is the distance between the two coordinate systems. We use the *pose* matrix to convert *X⃗*[*c*]inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn105.gif"/ to *X⃗*[*w*]inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn106.gif"/ for query points. During model training, all query points and ray origins are position-encoded by a function defined in the last function of Cell 04. A hyperparameter *L* is the number of encoding functions. The value of *L* for query points and ray origins is set to be 6 and 4, respectively. In the following equation, *q* is a batch of query points with a batch size *B*, where *L* = 6 is the number of encoding functions. After the coordinates of *q* are multiplied by 2*π*2⁰inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn107.gif"/, a sin function acts on them element-wisely, and a cos function also acts on them element-wisely. The operations of the two triangular functions are appended to *q* to construct a list with nine elements: \[*q*, sin (2*π*2⁰*q*)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn108.gif"/, cos (2*π*2⁰*q*)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn109.gif"/\] at frequency 2⁰inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn110.gif"/.

  
$${\\sin\\ }⁡(2\\pi 2^{i}\*q) = {\\sin\\ }⁡\\left( 2\\pi 2^{i}\*\\begin{bmatrix} q\_{x1} & q\_{y1} & q\_{z1} \\\\ q\_{x2} & q\_{y2} & q\_{z2} \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ q\_{\\mathit{xB}} & q\_{\\mathit{yB}} & q\_{\\mathit{zB}} \\\\ \\end{bmatrix} \\right)i \\in \\lbrack 0,(L - 1)\\rbrack$$  
graphic xlink:href="bk978-0-7503-6244-3ch12ueqn54.gif" position="float"/

The list of position encoding results of *q* are concatenated to get a tensor with shape *B* × (3+3×2×*L*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn112.gif"/ as one of two inputs of an MLP model defined in Cell 05. With the above background information, it should be easy to understand the codes of the tiny NeRF project listed in appendix [K](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-K). My codes are inspired by [Bmild](https://github.com/bmild/nerf/blob/master/tiny_nerf.ipynb). Model training time is about 125 min for 128 query points on each ray, and PSNR value is around 28.5. The trained MLP model is then saved by codes in Cell 13. The size of the saved model file is 301 kB. Running code in Cell 14, we can load the saved model to synthesize a Lego image at any *θ*inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn113.gif"/ and *φ*inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn114.gif"/ angles for a distance *r* around 4. The right image shown in figure [12.7](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig7) is the output of the following codes. You can change the values of theta, phi and *r* on the first line of following function to see different synthesized images. To improve the quality of the synthesized images, we need to increase the sample points on each ray, but we will have issues about the limit of GPU memory and model training time. Now we have many new NeRF algorithms enabling us to reconstruct photorealistic videos in real time. The development of computer vision is very fast. Some techniques in the book are obsolete when you are reading the book.

![](images/bk978-0-7503-6244-3ch12uf7_pr.gif)

 

| Point || Red color || Green color || Blue color || Density |
| --- | --- | --- | --- | --- |
| 01 || *α*[1]*r*[1]inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn7.gif"/ || *α*[1]*g*[1]inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-6244-3ch12ieqn8.gif"/ || *α*[1]*b*[1]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn9.gif"/ || *σ*[1]inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-6244-3ch12ieqn10.gif"/ |
| --- | --- | --- | --- | --- |
| 02 || *α*[2]*r*[2]*β*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn11.gif"/ || *α*[2]*g*[2]*β*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn12.gif"/ || *α*[2]*b*[2]*β*[1]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn13.gif"/ || *σ*[2]inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-6244-3ch12ieqn14.gif"/ |
| 03 || *α*[3]*r*[3]*β*[1]*β*[2]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn15.gif"/ || *α*[3]*g*[3]*β*[1]*β*[2]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn16.gif"/ || *α*[3]*b*[3]*β*[1]*β*[2]inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch12ieqn17.gif"/ || *σ*[3]inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn18.gif"/ |
| … || … || … || … || … |
| 32 || $\\alpha\_{32}r\_{128}\\prod\\limits\_{i = 1}^{31}\\beta\_{i}$inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn19.gif"/ || $\\alpha\_{32}g\_{32}\\prod\\limits\_{i = 1}^{31}\\beta\_{i}$inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn20.gif"/ || $\\alpha\_{32}b\_{32}\\prod\\limits\_{i = 1}^{31}\\beta\_{i}$inline-graphic style="height:1.5625em;" xlink:href="bk978-0-7503-6244-3ch12ieqn21.gif"/ || *σ*[32]inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-6244-3ch12ieqn22.gif"/ |

![Figure 12.7. Using a trained tiny NeRF model to synthesize a tiny Lego image at any θ and φ angles with a distance r around 4. (left) Image of the ground truth; (right) a synthesized tiny Lego image with theta, phi, r = 135o, -45o, 4.The tiny Lego image is reproduced with MIT license from Mildenhall et al (2020) (the authors of the original NeRF paper) and Yen-Chen Lin, the owner of ‘NeRF-pytorch’ GitHub repository.](images/bk978-0-7503-6244-3ch12f7_online.jpg)

**Figure 12.7.** Using a trained tiny NeRF model to synthesize a tiny Lego image at any θ and φ angles with a distance *r* around 4. (left) Image of the ground truth; (right) a synthesized tiny Lego image with theta, phi, *r* = 135^o, -45^o, 4.The tiny Lego image is reproduced with MIT license from Mildenhall *et al* ([2020](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib7)) (the authors of the original NeRF paper) and Yen-Chen Lin, the owner of ‘NeRF-pytorch’ GitHub [repository](https://github.com/yenchenlin/nerf-pytorch/tree/master/configs).

### 12.3 Introduce 3D Gaussian splatting by 2D Gaussian splatting

Model training for 3D Gaussian splatting is easy. In fact, there is no neural network model for the new technique. We just need to train a fitting function with many parameters which are updated during model training. You can start your 3D Gaussian splatting project by using a cellphone or a drone to take photos around something, such as a sculpture, an Egyptian pyramid, the Eiffel tower, or even buildings in downtown Vancouver. Then, you can use [Colmap](https://colmap.github.io/) or other free software to get a point cloud file from your photos about 3D points on the surface of your objects. The codes of a 3D Gaussian splatting project will initialize those points as 3D Gaussian rugby balls. During model training, millions of rugby balls will be projected to a confocal plane according to equation ([12.5](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn5)) for a camera at a position. This process is called ‘rasterization’. GPUs would be used to sort distance of all rugby balls to the confocal plane. Each ‘tile’ with 16x16 pixels on the confocal plane is a batch for GPUs to get a predicted image on a tile. An image taken by the camera at the position is used as a ground truth. An L1 loss function and a Structural Similarity Index (SSIM) loss function are used to calculate the difference between the predicted image and the ground truth. During model training, each rugby ball's position, size, orientation, color and opacity will be updated according to gradients of the loss function to some of the rugby balls’ parameters. If a rugby ball's opacity is low enough (or transparency is high enough), the rugby ball will be deleted; if the norm of the gradient of the loss function to the position coordinates of a rugby ball is big enough, the rugby ball will be cloned, and in the case when the cloned rugby balls’ sizes are big enough, the sizes of the two same rugby balls will be scaled down. This process will be repeated for all ground truth images to adjust each rugby ball's position, size, orientation, color and opacity. By the end, we can see photorealistic predicted images at any view angle around those objects.

The only problem is that model training needs a huge amount GPU memory for using millions of 3D Gaussians to reconstruct photorealistic 3D scenes. My RTX 2060 GPU with 6 GB memory can only handle 3536 2D Gaussians in the following Project [12.3.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro8). At the time while I am writing this chapter, [LUMA](https://lumalabs.ai/interactive-scenes) AI provides free web service for people to upload their photos so they can download 3D Gaussian splatting models trained by their photos. I have to use a 2D Gaussian splatting project to give you some ideas about the new technique. My codes were inspired by [OutofAi](https://github.com/OutofAi/2D-Gaussian-Splatting/blob/main/2D_Gaussian_Splatting.ipynb). A ground truth image in figure [12.8](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12fig8)A was processed by codes in Project [12.3.1](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12pro8) to obtain a synthesized image with 3536 2D Gaussians. It took me around 1x5 hours to get the good enough output with the structural similarity index (SSIM) to be equal to 0.882. SSIM was first introduced in the 2004 by an IEEE paper (Wang *et al* [2004](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib11)). It is better than PSNR used in the last section for image quality assessment, because its value is in the range \[0,1\]. A SSIM loss function defined in Cell 02 is based on an instance of a class in [kornia](https://kornia.readthedocs.io/en/latest/losses.html) library. The value of the loss function is equal to (1-SSIM)/2. In case a predicted image completely matches with its ground truth, we have SSIM = 1 and loss = 0. The maximum SSIM loss value is 0.5.

![Figure 12.8. (A) A ground image, the output of Cell 01; (B) a synthesized image with 3536 2D Gaussians, the output of Cell 06. Model training time is 1x5 hours (SSIM=0.882, PSNR=26.223).](images/bk978-0-7503-6244-3ch12f8_online.jpg)

**Figure 12.8.** (A) A ground image, the output of Cell 01; (B) a synthesized image with 3536 2D Gaussians, the output of Cell 06. Model training time is 1x5 hours (SSIM=0.882, PSNR=26.223).

On line 11 of Cell 02, 5000 pixels are randomly selected as cloud points for the squirrel image input in Cell 01. Using coordinates of these points, a function defined in the cell returns RGB colors and normalized coordinates of each cloud point. The values of these normalized coordinates are in the range \[–1, 1\]. With an inverse hyperbolic tangent function on line 16, the range of these cloud points' coordinates are extended to \[–∞, ∞\] in order to reduce gradients of a loss function to the coordinates for smooth model training. Otherwise, the splitting of Gaussians is too quick to get good model training results because of an ‘out of memory’ issue. Codes on line 12 to 14 of the cell randomly set each 2D Gaussian’s sigma, rho and color density. All these parameters are packed as a weight tensor with a shape \[5000,9\]. During model training, the weight tensor will be updated, so that some Gaussians will be cloned, deleted, resized, moved. In the process, these Gaussians' RGB colors will also be changed. For a 2D Gaussian with σ[*x*], σ[*y*] and a correlation coefficient ρ, the covariance matrix and its inverse of the 2D Gaussian will be set by equation ([12.9](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12eqn9)). These matrices are used in Cell 03 to calculate a batch of 2D Gaussians in Cell 03. PDF contours of three 2D Gaussians would be printed on screen as examples. The third Gaussian's PDF contours are ellipses because its *x* and *y* variables are not independent. The orientation of those ellipses is decided by the correlation coefficient ρ. The PDFs of the three 2D Gaussians are colorized and integrated into a color image by a function defined in Cell 04. A 2D affine matrices named ‘theta’ is used to transpose each Gaussian to its center (the coordinates of a cloud point) with colors. Using codes on the last three lines of Cell 04, we would see a color image just for the three 2D Gaussians. This model function will be used in model training to generate color images with thousands of Gaussians.

  
$$\\Sigma = \\begin{pmatrix} \\sigma\_{x}^{2} & {\\rho\\sigma\_{x}\\sigma\_{y}} \\\\ {\\rho\\sigma\_{x}\\sigma\_{y}} & \\sigma\_{y}^{2} \\\\ \\end{pmatrix}\\mspace{40mu}\\Sigma^{- 1} = \\frac{1}{\\sigma\_{x}^{2}\\sigma\_{y}^{2}(1 - \\rho)}\\begin{pmatrix} \\sigma\_{y}^{2} & {- \\ \\rho\\sigma\_{x}\\sigma\_{y}} \\\\ {- \\ \\rho\\sigma\_{x}\\sigma\_{y}} & \\sigma\_{x}^{2} \\\\ \\end{pmatrix}$$  
(12.9)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-6244-3ch12eqn115.gif" position="float"/

Codes in Cell 05 are used for model training. In the first 2000 epochs, model training speed is about 1.5 s per epoch. As more and more Gaussians are optimized for the synthesized image, the speed will be very slow. The program would be interrupted by an ‘out of memory’ issue. Or you can interrupt the program at any time if you find the program is very slow. Codes in Cell 05 save a check point for us in every 100 epochs if the number of Gaussians are more than 1000 in the output. By moving those three single quotation marks at the end of line 25 to the front of line 11 in Cell 02, we can train the model from a previous check point for the next 1000 epochs. At the time when we use the first check point, we need to change the *densification interval* parameter in Cell 01 to 100. Using a check point can accelerate model training speed. I tried to use float 16 to solve the ‘out of memory’ issue, but found the output image quality was poor. While 3D Gaussian splatting technique is still in its baby stage, its promise is undeniable in the domain of computer vision for 3D graphics. The original 3D Gaussian splatting can only handle static 3D scenes. Three months after Gaussian splatting was introduced, there are seven [papers](https://github.com/MrNeRF/awesome-3D-gaussian-splatting#dynamics-and-deformation) published with smart algorithms for animatable (Luiten *et al* [2023](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib6), Li *et al* [2023](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib5)) 3D Gaussian splatting. SuGaR (Guédon and Lepetit [2023](#Chapter_12.xhtml#bk978-0-7503-6244-3ch12bib1)) is a novel method for efficient 3D mesh reconstruction and high-quality mesh rendering from 3D Gaussian splatting representations. SuGaR enables easy editing, sculpting, rigging, animating, compositing and relighting of the Gaussians using traditional software by manipulating the mesh instead of the Gaussians themselves. Retrieving such an editable mesh for realistic rendering is done within minutes with SuGaR, while providing a better rendering quality. There is no limit for human intelligence. We are in a great age to build a digital Babel tower in the virtual world, from which we would know how to use atoms to synthesize big molecules, to construct nano-robots, to grow human organs, and even to build human bodies with intelligence.

![](images/bk978-0-7503-6244-3ch12uf8_pr.gif)

![](images/bk978-0-7503-6244-3ch12uf9_pr.gif)

![](images/bk978-0-7503-6244-3ch12uf10_pr.gif)

![](images/bk978-0-7503-6244-3ch12uf11_pr.gif)

![](images/bk978-0-7503-6244-3ch12uf12_pr.gif)

### References

Guédon A and Lepetit V 2023 SuGaR: Surface-aligned Gaussian splatting for efficient 3D mesh reconstruction and high-quality mesh rendering *arXiv preprint* arXiv:[2311.12775](http://arxiv.org/abs/2311.12775)

Inkilä K 2005 Homogeneous least squares problem *Photogramm. J. Finland* **19** 34–42

Kerbl B, Kopanas G, Leimkühler T and Drettakis G 2023 3d Gaussian splatting for real-time radiance field rendering *ACM Trans. Graph. (ToG)* [**42** 1–14](http://dx.doi.org/10.1145/3592433)

Li L, Shen Z, Wang Z, Shen L and Tan P 2022 Streaming radiance fields for 3d video synthesis *Adv. Neur. Inform. Process. Syst.* **35** 13485–98

Li Z, Zheng Z, Wang L and Liu Y 2023 Animatable Gaussians: learning pose-dependent Gaussian maps for high-fidelity human avatar modeling *arXiv preprint* arXiv:[2311.16096](http://arxiv.org/abs/2311.16096)

Luiten J, Kopanas G, Leibe B and Ramanan D 2023 Dynamic 3d Gaussians: tracking by persistent dynamic view synthesis *arXiv preprint* arXiv:[2308.09713](http://arxiv.org/abs/2308.09713)

Mildenhall B, Srinivasan P P, Tancik M, Barron J T, Ramamoorthi R and Ng R 2020 Nerf: Representing scenes as neural radiance fields for view synthesis *Commun. ACM* [**65** 99–106](http://dx.doi.org/10.1145/3503250)

Müller T, Evans A, Schied C and Keller A 2022 Instant neural graphics primitives with a multiresolution hash encoding *ACM Trans. Graph. (ToG)* [**41** 1–15](http://dx.doi.org/10.1145/3528223.3530127)

Ranftl R, Lasinger K, Hafner D, Schindler K and Koltun V 2020 Towards robust monocular depth estimation: mixing datasets for zero-shot cross-dataset transfer *IEEE Trans. Pattern Anal. Mach. Intell.* [**44** 1623–37](http://dx.doi.org/10.1109/TPAMI.2020.3019967)

Tancik M, Srinivasan P, Mildenhall B, Fridovich-Keil S, Raghavan N, Singhal U, Ramamoorthi R, Barron J and Ng R 2020 Fourier features let networks learn high frequency functions in low dimensional domains *Adv. Neur. Inform. Process. Syst.* **33** 7537–47

Wang Z, Bovik A C, Sheikh H R and Simoncelli E P 2004 Image quality assessment: from error visibility to structural similarity *IEEE Trans. Image Process.* [**13** 600–12](http://dx.doi.org/10.1109/TIP.2003.819861)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

## Appendix

### A Kullback–Leibler divergence of two multivariate normal distributions

  
$$p\\left( {X = x} \\right) = \\prod\\limits\_{i = 1}^{k}{\\frac{1}{\\sqrt{2\\pi\\sigma\_{i}^{2}}}e^{- \\frac{1}{2}{(\\frac{x\_{i} - \\mu\_{i}}{\\sigma\_{i}})}^{2}}} = \\frac{1}{\\left( {2\\pi} \\right)^{k/2}\\mid\\Sigma\\mid^{1/2}}e^{- \\frac{1}{2}{({x - \\mu})}^{T}\\Sigma^{- 1}{({x - \\mu})}}$$  
graphic style="width:27.5625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn1.gif" position="float"/

  
$$q(X = x) = \\frac{1}{\\left( 2\\pi \\right)^{k/2}\\mid I\\mid^{1/2}}e^{- \\frac{1}{2}{({x^{T}I^{- 1}x})}}$$  
graphic style="width:14.4375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn2.gif" position="float"/

  
*X* = \[*x*[1],*x*[2],…,*x*[*k*]\]^(*T*), *μ* = \[*u*[1],*u*[2],…,*u*[*k*]\]^(*T*), *μ*[2] = \[0,0,…,0\]^(*T*)  
graphic style="width:25.5em;" xlink:href="bk978-0-7503-6244-3ch13ueqn3.gif" position="float"/

  
$$\\Sigma = \\begin{bmatrix} \\sigma\_{1}^{2} & 0 & {.\\ ..} & 0 \\\\ 0 & \\sigma\_{2}^{2} & {.\\ ..} & 0 \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ 0 & 0 & {.\\ ..} & \\sigma\_{k}^{2} \\\\ \\end{bmatrix},\\Sigma^{- 1} = \\begin{bmatrix} \\sigma\_{1}^{- 2} & 0 & {.\\ ..} & 0 \\\\ 0 & \\sigma\_{2}^{- 2} & {.\\ ..} & 0 \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ 0 & 0 & {.\\ ..} & \\sigma\_{k}^{- 2} \\\\ \\end{bmatrix},\\Sigma\_{2} = I = \\begin{bmatrix} 1 & 0 & {.\\ ..} & 0 \\\\ 0 & 1 & {.\\ ..} & 0 \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ 0 & 0 & {.\\ ..} & 1 \\\\ \\end{bmatrix}$$  
graphic style="width:33.125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn4.gif" position="float"/

  
$$\\left( {x - \\mu} \\right)^{T}\\Sigma^{- 1}\\left( {x - \\mu} \\right) = \\begin{bmatrix} {x\_{1} - \\mu\_{1}} & {.\\ ..} & {x\_{k} - \\mu\_{k}} \\\\ \\end{bmatrix}\\begin{bmatrix} \\sigma\_{1}^{- 2} & 0 & {.\\ ..} & 0 \\\\ 0 & \\sigma\_{2}^{- 2} & {.\\ ..} & 0 \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ 0 & 0 & {.\\ ..} & \\sigma\_{k}^{- 2} \\\\ \\end{bmatrix}\\begin{bmatrix} {x\_{1} - \\mu\_{1}} \\\\ {x\_{2} - \\mu\_{2}} \\\\ {.\\ ..} \\\\ {x\_{k} - \\mu\_{k}} \\\\ \\end{bmatrix} = \\sum\\limits\_{i = 1}^{k}\\frac{\\left( {x\_{i} - \\mu\_{i}} \\right)^{2}}{\\sigma\_{i}^{2}}$$  
graphic style="width:32.9375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn5.gif" position="float"/

  
$$\\left. D\_{\\mathit{KL}}( p(X \\right){\\mid\\mid}q\\left( X \\right)) = \\iiint\\limits\_{x}{p\\left( x \\right)\\left\\lbrack {\\ln\\ p\\left( x \\right) - \\ln\\ q\\left( x \\right)} \\right\\rbrack\\mathit{dx}}$$  
graphic style="width:20.625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn6.gif" position="float"/

  
$$= \\iiint p\\left( x \\right)\\left\\lbrack {\\frac{1}{2}\\ \\ln\\ \\left( \\frac{\\mid\\Sigma\_{2}\\mid}{\\mid\\Sigma\\mid} \\right) + \\frac{1}{2}\\left( x - \\mu\_{2} \\right)^{T}\\Sigma\_{2}^{- 1}(x - \\mu\_{2}) - \\frac{1}{2}\\left( x - \\mu \\right)^{T}\\Sigma^{- 1}(x - \\mu)} \\right\\rbrack\\mathit{dx}$$  
graphic style="width:33.25em;" xlink:href="bk978-0-7503-6244-3ch13ueqn7.gif" position="float"/

  
$$= \\iiint p\\left( x \\right)\\left\\lbrack {\\frac{1}{2}\\ \\ln\\ \\left( \\frac{\\mid I\\mid}{\\mid\\Sigma\\mid} \\right) + \\frac{1}{2}{(x - 0)}^{T}I^{- 1}(x - 0) - \\frac{1}{2}\\sum\\limits\_{i = 1}^{k}\\frac{\\left( {x\_{i} - \\mu\_{i}} \\right)^{2}}{\\sigma\_{i}^{2}}} \\right\\rbrack\\mathit{dx}$$  
graphic style="width:26.875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn8.gif" position="float"/

  
$$= \\ - \\frac{1}{2}\\ \\ln\\ \\left( {\\mid \\Sigma \\mid} \\right) + \\frac{1}{2}\\iiint p\\left( x \\right)\\left\\lbrack {x^{T}x} \\right\\rbrack\\mathit{dx} - \\frac{1}{2}\\iiint p\\left( x \\right)\\sum\\limits\_{i = 1}^{k}\\frac{\\left( {x\_{i} - \\mu\_{i}} \\right)^{2}}{\\sigma\_{i}^{2}}\\mathit{dx}$$  
graphic style="width:27.5625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn9.gif" position="float"/

  
$$= - \\frac{1}{2}\\ \\ln\\ \\left( {\\mid \\Sigma \\mid} \\right) + \\frac{1}{2}\\iiint p\\left( x \\right)(x\_{1}^{2} + x\_{2}^{2} + \\ldots + x\_{k}^{2})\\mathit{dx} - \\frac{k}{2}$$  
graphic style="width:24.625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn10.gif" position="float"/

  
$$= - \\frac{1}{2}\\ \\ln\\ \\left( {\\prod\\limits\_{i = 1}^{k}\\sigma\_{i}^{2}} \\right) + \\frac{1}{2}\\iiint\\prod\\limits\_{i = 1}^{k}{p\_{i}\\left( x\_{i} \\right)\\left( x\_{1}^{2} + x\_{2}^{2} + \\ldots + x\_{k}^{2} \\right)}dx\_{1}dx\_{2}\\ldots dx\_{k} - \\frac{k}{2}$$  
graphic style="width:32.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn11.gif" position="float"/

  
$$= - \\frac{1}{2}\\sum\\limits\_{i = 1}^{k}{\\ \\ln\\ ⁡(\\sigma\_{i}^{2}}) - \\frac{k}{2} + \\frac{1}{2}\\iiint\\prod\\limits\_{i = 1}^{k}{p\_{i}\\left( x\_{i} \\right)}(x\_{1}^{2} + x\_{2}^{2} + \\ldots + x\_{k}^{2})dx\_{1}dx\_{2}\\ldots dx\_{k}$$  
graphic style="width:29.0625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn12.gif" position="float"/

  
$$= - \\frac{1}{2}\\sum\\limits\_{i = 1}^{k}{\\ \\ln\\ ⁡(\\sigma\_{i}^{2}}) - \\frac{k}{2} + \\frac{1}{2}\\int p\_{1}\\left( x\_{1} \\right)x\_{1}^{2}dx\_{1} + \\frac{1}{2}\\int p\_{2}\\left( x\_{2} \\right)x\_{2}^{2}dx\_{2} + \\ldots + \\frac{1}{2}\\int p\_{k}\\left( x\_{k} \\right)x\_{k}^{2}dx\_{k}$$  
graphic style="width:33.5625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn13.gif" position="float"/

  
$$= - \\frac{1}{2}\\sum\\limits\_{i = 1}^{k}{\\ \\ln(\\sigma\_{i}^{2}}) - \\frac{1}{2}\\sum\\limits\_{i = 1}^{k}1 + \\frac{1}{2}\\sum\\limits\_{i = 1}^{k}\\left( {\\mu\_{i}^{2} + \\sigma\_{i}^{2}} \\right)$$  
graphic style="width:18.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn14.gif" position="float"/

  
$$= \\frac{1}{2}\\sum\\limits\_{i = 1}^{k}{\\lbrack\\mu\_{i}^{2}} + \\sigma\_{i}^{2} - \\ln\\left( \\sigma\_{i}^{2} \\right) - 1\\rbrack$$  
graphic style="width:12.3125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn15.gif" position="float"/

### B Expectation-maximization algorithm

  
$$L = - \\ln\\ \\left( {P\\left( X \\right)} \\right) = - \\ln\\ \\prod\\limits\_{j = 1}^{n}{p\\left( x\_{j} \\right)} = - \\sum\\limits\_{j = 1}^{n}{\\ \\ln\\ \\left( {\\sum\\limits\_{i = 1}^{3}{p\\left( x\_{j}\\mid z\_{i} \\right)}p\\left( z\_{i} \\right)} \\right)}$$  
graphic style="width:26.375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn16.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial\\mu\_{1}} = - \\frac{\\partial}{\\partial\\mu\_{1}}\\sum\\limits\_{j = 1}^{n}{\\ \\ln\\ \\left( { p\\left( x\_{j} \\right)} \\right)} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial p\\left( x\_{j} \\right)}{\\partial\\mu\_{1}}} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial}{\\partial\\mu\_{1}}}\\sum\\limits\_{i = 1}^{3}{p\\left( x\_{j}\\mid z\_{i} \\right)}p\\left( z\_{i} \\right)$$  
graphic style="width:33.3125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn17.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial\\mu\_{1}} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial}{\\partial\\mu\_{1}}}\\sum\\limits\_{i = 1}^{3}{\\frac{1}{\\sqrt{2\\pi\\sigma\_{i}^{2}}}e^{- \\frac{1}{2}{(\\frac{x\_{j} - \\mu\_{i}}{\\sigma\_{i}})}^{2}}}p\\left( z\_{i} \\right) = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{p\\left( z\_{1} \\right)}{\\sqrt{2\\pi\\sigma\_{1}^{2}}}e^{- \\frac{1}{2}{(\\frac{x\_{j} - \\mu\_{1}}{\\sigma\_{1}})}^{2}}\\frac{x\_{j} - \\mu\_{1}}{\\sigma\_{1}^{2}}}$$  
graphic style="width:33.4375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn18.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial\\mu\_{1}} = - \\frac{1}{\\sigma\_{1}^{2}}\\sum\\limits\_{j = 1}^{n}{\\frac{p\\left( x\_{j},z\_{1} \\right)}{p\\left( x\_{j} \\right)}(x\_{j} - \\mu\_{1})} = - \\frac{1}{\\sigma\_{1}^{2}}\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)}(x\_{j} - \\mu\_{1}) = 0$$  
graphic style="width:25.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn19.gif" position="float"/

  
$$\\mu\_{1} = \\frac{\\sum\\limits\_{j = 1}^{n}{x\_{j}p\\left( z\_{1}\\mid x\_{j} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)}}$$  
graphic style="width:7.25em;" xlink:href="bk978-0-7503-6244-3ch13ueqn20.gif" position="float"/

  
$$\\mu\_{i} = \\frac{\\sum\\limits\_{j = 1}^{n}{x\_{j}p\\left( z\_{i}\\mid x\_{j} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{i}\\mid x\_{j} \\right)}}$$  
graphic style="width:7.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn21.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial v\_{1}} = - \\frac{\\partial}{\\partial v\_{1}}\\sum\\limits\_{j = 1}^{n}{\\ \\ln\\ \\left( { p\\left( x\_{j} \\right)} \\right)} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial p\\left( x\_{j} \\right)}{\\partial v\_{1}}} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial}{\\partial v\_{1}}}\\sum\\limits\_{i = 1}^{3}{p\\left( x\_{j}\\mid z\_{i} \\right)}p\\left( z\_{i} \\right)$$  
graphic style="width:33.125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn22.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial v\_{1}} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial}{\\partial v\_{1}}}\\sum\\limits\_{i = 1}^{3}{\\frac{1}{\\sqrt{2\\pi v\_{i}}}e^{- \\frac{1}{2v\_{i}}{(x\_{j} - \\mu\_{i})}^{2}}}p\\left( z\_{i} \\right) = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial}{\\partial v\_{1}}}\\left( {\\frac{1}{\\sqrt{2\\pi v\_{1}}}e^{- \\frac{1}{2v\_{1}}{(x\_{j} - \\mu\_{1})}^{2}}} \\right)p\\left( z\_{1} \\right)$$  
graphic style="width:34.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn23.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial v\_{1}} = - \\sum\\limits\_{j = 1}^{n}{\\frac{p\\left( z\_{1} \\right)}{p\\left( x\_{j} \\right)}\\left\\lbrack {\\frac{- 1}{2v\_{1}^{3/2}\\sqrt{2\\pi}}e^{- \\frac{1}{2v\_{1}}{(x\_{j} - \\mu\_{1})}^{2}} + \\frac{1}{\\sqrt{2\\pi v\_{1}}}e^{- \\frac{1}{2v\_{1}}{(x\_{j} - \\mu\_{1})}^{2}}\\frac{1}{2v\_{1}^{2}}\\left( x\_{j} - \\mu\_{1} \\right)^{2}} \\right\\rbrack}$$  
graphic style="width:31.125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn24.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial v\_{1}} = - \\sum\\limits\_{j = 1}^{n}{\\frac{p\\left( z\_{1} \\right)}{p\\left( x\_{j} \\right)}\\left\\lbrack {\\frac{- 1}{2v\_{1}}p(x\_{j}\\mid z\_{1}) + p(x\_{j}\\mid z\_{1})\\frac{1}{2v\_{1}^{2}}\\left( x\_{j} - \\mu\_{1} \\right)^{2}} \\right\\rbrack}$$  
graphic style="width:23.9375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn25.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial v\_{1}} = - \\sum\\limits\_{j = 1}^{n}{\\frac{p\\left( x\_{j}\\mid z\_{1} \\right)p\\left( z\_{1} \\right)}{p\\left( x\_{j} \\right)}\\left\\lbrack {\\frac{- 1}{2v\_{1}} + \\frac{1}{2v\_{1}^{2}}\\left( x\_{j} - \\mu\_{1} \\right)^{2}} \\right\\rbrack}$$  
graphic style="width:20.375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn26.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial v\_{1}} = \\frac{- 1}{2v\_{1}^{2}}\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)\\left\\lbrack {v\_{1} - \\left( x\_{j} - \\mu\_{1} \\right)^{2}} \\right\\rbrack} = 0$$  
graphic style="width:18.375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn27.gif" position="float"/

  
$$v\_{1} = \\sigma\_{1}^{2} = \\frac{\\sum\\limits\_{j = 1}^{n}{\\left( x\_{j} - \\mu\_{1} \\right)^{2}p\\left( z\_{1}\\mid x\_{j} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)}}$$  
graphic style="width:12.375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn28.gif" position="float"/

  
$$v\_{i} = \\sigma\_{i}^{2} = \\frac{\\sum\\limits\_{j = 1}^{n}{\\left( x\_{j} - \\mu\_{i} \\right)^{2}p\\left( z\_{i}\\mid x\_{j} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{i}\\mid x\_{j} \\right)}}$$  
graphic style="width:13.125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn29.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial p\\left( z\_{1} \\right)} = - \\frac{\\partial}{\\partial p\\left( z\_{1} \\right)}\\sum\\limits\_{j = 1}^{n}{\\ \\ln\\ \\left( { p\\left( x\_{j} \\right)} \\right)} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial p\\left( x\_{j} \\right)}{\\partial p\\left( z\_{1} \\right)}}$$  
graphic style="width:21.25em;" xlink:href="bk978-0-7503-6244-3ch13ueqn30.gif" position="float"/

  
*p*(*z*[3]) = 1 − *p*(*z*[1]) − *p*(*z*[2])  
graphic style="width:10.25em;" xlink:href="bk978-0-7503-6244-3ch13ueqn31.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial p\\left( z\_{1} \\right)} = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\frac{\\partial}{\\partial p\\left( z\_{1} \\right)}}\\sum\\limits\_{i = 1}^{3}{p\\left( x\_{j}\\mid z\_{i} \\right)}p\\left( z\_{i} \\right) = - \\sum\\limits\_{j = 1}^{n}{\\frac{1}{p\\left( x\_{j} \\right)}\\left\\lbrack { p\\left( x\_{j}\\mid z\_{1} \\right) - p\\left( x\_{j}\\mid z\_{3} \\right)} \\right\\rbrack} = 0$$  
graphic style="width:34.6875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn32.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial p\\left( z\_{1} \\right)} = - \\sum\\limits\_{j = 1}^{n}\\left\\lbrack {\\frac{ p\\left( z\_{1} \\right)}{p\\left( x\_{j} \\right)}\\frac{p\\left( {x\_{j} \\mid z\_{1}} \\right)}{p\\left( z\_{1} \\right)} - \\frac{p\\left( z\_{3} \\right)}{p\\left( x\_{j} \\right)}\\frac{p\\left( {x\_{j} \\mid z\_{3}} \\right)}{p\\left( z\_{3} \\right)}} \\right\\rbrack$$  
graphic style="width:19.5em;" xlink:href="bk978-0-7503-6244-3ch13ueqn33.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial p\\left( z\_{1} \\right)} = - \\sum\\limits\_{j = 1}^{n}\\left\\lbrack {\\frac{ p\\left( z\_{1}\\mid x\_{j} \\right)}{p\\left( z\_{1} \\right)} - \\frac{p\\left( z\_{3}\\mid x\_{j} \\right)}{p\\left( z\_{3} \\right)}} \\right\\rbrack$$  
graphic style="width:16.0625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn34.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial p\\left( z\_{1} \\right)} = - \\frac{1}{p\\left( z\_{1} \\right)}\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)\\ + \\ }\\frac{1}{p\\left( z\_{3} \\right)}\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)} = 0$$  
graphic style="width:21.875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn35.gif" position="float"/

  
$$p\\left( z\_{1} \\right) = p\\left( z\_{3} \\right)\\frac{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}}$$  
graphic style="width:9.375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn36.gif" position="float"/

  
$$p\\left( z\_{2} \\right) = p\\left( z\_{3} \\right)\\frac{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{2}\\mid x\_{j} \\right)}}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}}$$  
graphic style="width:10.25em;" xlink:href="bk978-0-7503-6244-3ch13ueqn37.gif" position="float"/

  
$$p\\left( z\_{3} \\right)\\frac{p\\left( z\_{1} \\right)}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}} + p\\left( z\_{3} \\right)\\frac{p\\left( z\_{2} \\right)}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}} + p\\left( z\_{3} \\right) = 1$$  
graphic style="width:20.3125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn38.gif" position="float"/

  
$$p\\left( z\_{3} \\right)\\frac{1}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}}\\left\\lbrack {\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)} + \\sum\\limits\_{j = 1}^{n}{p\\left( z\_{2}\\mid x\_{j} \\right)} + \\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}} \\right\\rbrack = 1$$  
graphic style="width:26.75em;" xlink:href="bk978-0-7503-6244-3ch13ueqn39.gif" position="float"/

  
$$p\\left( z\_{3} \\right)\\frac{1}{\\sum\\limits\_{j = 1}^{n}{p\\left( {z\_{3} \\mid x\_{j}} \\right)}}\\sum\\limits\_{j = 1}^{n}{\\sum\\limits\_{i = 1}^{3}{p\\left( {z\_{i} \\mid x\_{j}} \\right)}} = p\\left( z\_{3} \\right)\\frac{1}{\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}}\\sum\\limits\_{j = 1}^{n}1 = 1$$  
graphic style="width:23.625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn40.gif" position="float"/

  
$$p\\left( z\_{3} \\right) = \\frac{1}{n}\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{3}\\mid x\_{j} \\right)}$$  
graphic style="width:8.875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn41.gif" position="float"/

  
$$p\\left( z\_{2} \\right) = \\frac{1}{n}\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{2}\\mid x\_{j} \\right)}$$  
graphic style="width:8.875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn42.gif" position="float"/

  
$$p\\left( z\_{1} \\right) = \\frac{1}{n}\\sum\\limits\_{j = 1}^{n}{p\\left( z\_{1}\\mid x\_{j} \\right)}$$  
graphic style="width:8em;" xlink:href="bk978-0-7503-6244-3ch13ueqn43.gif" position="float"/

### C Gradients of MSE loss function to weights in a linear regression

  
$$\\begin{bmatrix} 1 & x\_{0,1} & {.\\ ..} & x\_{0,m} \\\\ 1 & x\_{1,1} & {.\\ ..} & x\_{1,m} \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ 1 & x\_{n,1} & {.\\ ..} & x\_{n,m} \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} w\_{0} \\\\ w\_{1} \\\\ {.\\ ..} \\\\ w\_{m} \\\\ \\end{bmatrix} = \\begin{bmatrix} {\\widehat{y}}\_{0} \\\\ {\\widehat{y}}\_{1} \\\\ {.\\ ..} \\\\ {\\widehat{y}}\_{n} \\\\ \\end{bmatrix},\\mathit{Y} = \\begin{bmatrix} y\_{0} \\\\ y\_{1} \\\\ {.\\ ..} \\\\ y\_{n} \\\\ \\end{bmatrix},(i = 0,1...n,j = 0,1...m)$$  
graphic style="width:33.8125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn44.gif" position="float"/

Model: *X* ⋅ *w* = *Ŷ*inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch13ieqn45.gif"/

Model prediction: ${\\widehat{y}}\_{i} = \\sum\\limits\_{j = 0}^{m}{x\_{i,j}w\_{j}}$inline-graphic style="height:3.25em;" xlink:href="bk978-0-7503-6244-3ch13ieqn46.gif"/

Loss function: $L\\left( X,w \\right) = \\frac{1}{\\left( n + 1 \\right)}\\sum\\limits\_{i = 0}^{n}\\left( {\\widehat{y}}\_{i} - y\_{i} \\right)^{2}$inline-graphic style="height:3.125em;" xlink:href="bk978-0-7503-6244-3ch13ieqn47.gif"/

  
$$J\_{i,j} = \\frac{\\partial{\\widehat{y}}\_{i}}{\\partial w\_{j}} = \\frac{\\partial}{\\partial w\_{j}}\\sum\\limits\_{k = 0}^{m}x\_{i,k}w\_{k} = x\_{i,j}$$  
graphic style="width:13.625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn48.gif" position="float"/

  
$$\\nabla L(X,w) = \\left( {\\frac{\\partial L}{\\partial w\_{0}},\\frac{\\partial L}{\\partial w\_{1}},...,\\frac{\\partial L}{\\partial w\_{m}}} \\right)^{T}$$  
graphic style="width:15em;" xlink:href="bk978-0-7503-6244-3ch13ueqn49.gif" position="float"/

  
$$\\frac{\\partial L}{\\partial w\_{j}} = \\frac{\\partial}{\\partial w\_{j}}\\frac{1}{\\left( n + 1 \\right)}\\sum\\limits\_{i = 0}^{n}\\left( {{\\widehat{y}}\_{i} - y\_{i}} \\right)^{2} = \\frac{2}{\\left( n + 1 \\right)}\\sum\\limits\_{i = 0}^{n}{\\left( {{\\widehat{y}}\_{i} - y\_{i}} \\right)\\frac{\\partial{\\widehat{y}}\_{i}}{\\partial w\_{j}} =}\\frac{2}{\\left( n + 1 \\right)}\\sum\\limits\_{i = 0}^{n}{x\_{i,j}\\left( {{\\widehat{y}}\_{i} - y\_{i}} \\right)}$$  
graphic style="width:32.9375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn50.gif" position="float"/

  
$$\\begin{bmatrix} \\frac{\\partial L}{\\partial w\_{0}} \\\\ \\frac{\\partial L}{\\partial w\_{1}} \\\\ {.\\ ..} \\\\ \\frac{\\partial L}{\\partial w\_{m}} \\\\ \\end{bmatrix} = \\frac{2}{n + 1}\\begin{bmatrix} 1 & 1 & {.\\ ..} & 1 \\\\ x\_{0,1} & x\_{1,1} & {.\\ ..} & x\_{n,1} \\\\ {.\\ ..} & {.\\ ..} & {.\\ ..} & {.\\ ..} \\\\ x\_{0,m} & x\_{1,m} & {.\\ ..} & x\_{n,m} \\\\ \\end{bmatrix} \\cdot \\begin{bmatrix} {{\\widehat{y}}\_{0} - y\_{0}} \\\\ {{\\widehat{y}}\_{1} - y\_{1}} \\\\ {.\\ ..} \\\\ {{\\widehat{y}}\_{n} - y\_{n}} \\\\ \\end{bmatrix}$$  
graphic style="width:21.8125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn51.gif" position="float"/

  
$$\\nabla L(X,w) = \\frac{2}{n + 1}X^{T} \\cdot (\\widehat{Y} - Y)$$  
graphic style="width:14.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn52.gif" position="float"/

### D Application of a VAE-GAN to generate fake Anime-faces dataset images

![](images/bk978-0-7503-6244-3app1uf1_pr.gif)

![](images/bk978-0-7503-6244-3app1uf2_pr.gif)

![](images/bk978-0-7503-6244-3app1uf3_pr.gif)

![](images/bk978-0-7503-6244-3app1uf4_pr.gif)

### E Applications of a cWGAN-GP system to MNIST or fashion MNIST

![](images/bk978-0-7503-6244-3app1uf5_pr.gif)

![](images/bk978-0-7503-6244-3app1uf6_pr.gif)

![](images/bk978-0-7503-6244-3app1uf7_pr.gif)

![](images/bk978-0-7503-6244-3app1uf8_pr.gif)

### F Four applications of pre-trained Detectron2 models

![](images/bk978-0-7503-6244-3app1uf10_pr.gif)

![](images/bk978-0-7503-6244-3app1uf11_pr.gif)

### G Traffic tracking and counting for objects in multiple COCO classes

![](images/bk978-0-7503-6244-3app1uf12_pr.gif)

![](images/bk978-0-7503-6244-3app1uf13_pr.gif)

### H U-Net Wasserstein generative adversarial networks for retina

![](images/bk978-0-7503-6244-3app1uf15_pr.gif)

![](images/bk978-0-7503-6244-3app1uf16_pr.gif)

![](images/bk978-0-7503-6244-3app1uf17_pr.gif)

![](images/bk978-0-7503-6244-3app1uf18_pr.gif)

![](images/bk978-0-7503-6244-3app1uf19_pr.gif)

### I DDPM forward process posterior distribution and *L*[VLB]

  
$$q(x\_{t - 1}\\mid x\_{t},x\_{0}) = \\frac{q\\left( x\_{t - 1},x\_{t},x\_{0} \\right)}{q\\left( x\_{t},x\_{0} \\right)} = \\frac{q\\left( x\_{t}\\mid x\_{t - 1},x\_{0} \\right)q\\left( x\_{t - 1},x\_{0} \\right)}{q\\left( x\_{t}\\mid x\_{0} \\right)q\\left( x\_{0} \\right)}$$  
graphic style="width:24.6875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn53.gif" position="float"/

  
$$q(x\_{t - 1}\\mid x\_{t},x\_{0}) = \\frac{q\\left( x\_{t}\\mid x\_{t - 1},x\_{0} \\right)q\\left( x\_{t - 1}\\mid x\_{0} \\right)q\\left( x\_{0} \\right)}{q\\left( x\_{t}\\mid x\_{0} \\right)q\\left( x\_{0} \\right)} = q(x\_{t}\\mid x\_{t - 1},x\_{0})\\frac{q\\left( x\_{t - 1}\\mid x\_{0} \\right)}{q\\left( x\_{t}\\mid x\_{0} \\right)}$$  
graphic style="width:31.6875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn54.gif" position="float"/

  
$$q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right) = \\mathbb{N}\\left( {x\_{t - 1};\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right),{\\widetilde{\\beta}}\_{t}I} \\right) = q\\left( {x\_{t} \\mid x\_{t - 1},x\_{0}} \\right)\\frac{q\\left( {x\_{t - 1} \\mid x\_{0}} \\right)}{q\\left( {x\_{t} \\mid x\_{0}} \\right)}$$  
graphic style="width:26.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn55.gif" position="float"/

  
$$\\propto \\exp\\ \\left( {- \\frac{1}{2}\\frac{\\left( {x\_{t} - \\sqrt{\\alpha\_{t}}x\_{t - 1}} \\right)^{2}}{\\beta\_{t}} - \\frac{1}{2}\\frac{\\left( {x\_{t - 1} - \\sqrt{{\\overline{\\alpha}}\_{t - 1}}x\_{0}} \\right)^{2}}{1 - {\\overline{\\alpha}}\_{t - 1}} + \\frac{1}{2}\\frac{\\left( {x\_{t} - \\sqrt{{\\overline{\\alpha}}\_{t}}x\_{0}} \\right)^{2}}{1 - {\\overline{\\alpha}}\_{t}}} \\right)$$  
graphic style="width:29.3125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn56.gif" position="float"/

  
$$= \\ \\exp\\ \\left( {- \\frac{1}{2}\\left\\lbrack {\\frac{x\_{t}^{2} - 2\\sqrt{\\alpha\_{t}}x\_{t}x\_{t - 1} + \\alpha\_{t}x\_{t - 1}^{2}}{\\beta\_{t}} + \\frac{x\_{t - 1}^{2} - 2\\sqrt{{\\overline{\\alpha}}\_{t - 1}}x\_{0}x\_{t - 1} + \\alpha\_{t}x\_{0}^{2}}{1 - {\\overline{\\alpha}}\_{t - 1}} - \\frac{\\left( {x\_{t} - \\sqrt{{\\overline{\\alpha}}\_{t}}x\_{0}} \\right)^{2}}{1 - {\\overline{\\alpha}}\_{t}}} \\right\\rbrack} \\right)$$  
graphic style="width:34.8125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn57.gif" position="float"/

  
$$= \\ \\exp\\ \\left( {- \\frac{1}{2}\\left\\lbrack {\\left( {\\frac{\\alpha\_{t}}{\\beta\_{t}} + \\frac{1}{1 - {\\overline{\\alpha}}\_{t - 1}}} \\right)x\_{t - 1}^{2} - \\left( {\\frac{2\\sqrt{\\alpha\_{t}}}{\\beta\_{t}}x\_{t} + \\frac{2\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t - 1}}x\_{0}} \\right)x\_{t - 1} + \\left( {\\frac{x\_{t}^{2}}{\\beta\_{t}} + \\frac{\\alpha\_{t}x\_{0}^{2}}{1 - {\\overline{\\alpha}}\_{t - 1}} - \\frac{\\left( {x\_{t} - \\sqrt{{\\overline{\\alpha}}\_{t}}x\_{0}} \\right)^{2}}{1 - {\\overline{\\alpha}}\_{t}}} \\right)} \\right\\rbrack} \\right)$$  
graphic style="width:33.5em;" xlink:href="bk978-0-7503-6244-3ch13ueqn58.gif" position="float"/

  
$$= \\ \\exp\\ \\left( {- \\frac{1}{2}\\left\\lbrack {\\left( {\\frac{\\alpha\_{t}}{\\beta\_{t}} + \\frac{1}{1 - {\\overline{\\alpha}}\_{t - 1}}} \\right)x\_{t - 1}^{2} - 2\\left( {\\frac{\\sqrt{\\alpha\_{t}}}{\\beta\_{t}}x\_{t} + \\frac{\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t - 1}}x\_{0}} \\right)x\_{t - 1} + C\_{0}\\left( {x\_{t},x\_{0}} \\right)} \\right\\rbrack} \\right)$$  
graphic style="width:33.0625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn59.gif" position="float"/

  
$$= \\ \\exp\\ \\left( {- \\frac{1}{2}\\left( {\\frac{\\alpha\_{t}}{\\beta\_{t}} + \\frac{1}{1 - {\\overline{\\alpha}}\_{t - 1}}} \\right)\\left\\lbrack {x\_{t - 1}^{2} - 2\\left( {\\frac{\\alpha\_{t}}{\\beta\_{t}} + \\frac{1}{1 - {\\overline{\\alpha}}\_{t - 1}}} \\right)^{- 1}\\left( {\\frac{\\sqrt{\\alpha\_{t}}}{\\beta\_{t}}x\_{t} + \\frac{\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t - 1}}x\_{0}} \\right)x\_{t - 1} + C\_{1}\\left( {x\_{t},x\_{0}} \\right)} \\right\\rbrack} \\right)$$  
graphic style="width:34.375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn60.gif" position="float"/

In the above formula, *C*(*x*[*t*],*x*[0])inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch13ieqn61.gif"/ is a function not involving *x*[*t-1*] and details are omitted. Following the standard Gaussian density function with *α*[*t*] = 1 − *β*[*t*]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-6244-3ch13ieqn62.gif"/, ${\\overline{\\alpha}}\_{t} = \\prod\\limits\_{i = 1}^{t}\\alpha\_{i}$inline-graphic style="height:3.1875em;" xlink:href="bk978-0-7503-6244-3ch13ieqn63.gif"/, the mean and variance of *q*(*x*[*t* − 1]∣*x*[*t*],*x*[0])inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-6244-3ch13ieqn64.gif"/ can be parameterized as follows:

  
$${\\widetilde{\\beta}}\_{t} = \\left( {\\frac{\\alpha\_{t}}{\\beta\_{t}} + \\frac{1}{1 - {\\overline{\\alpha}}\_{t - 1}}} \\right)^{- 1} = \\left( \\frac{\\alpha\_{t}\\left( {1 - {\\overline{\\alpha}}\_{t - 1}} \\right) + \\beta\_{t}}{\\beta\_{t}\\left( {1 - {\\overline{\\alpha}}\_{t - 1}} \\right)} \\right)^{- 1} = \\left( \\frac{1 - {\\overline{\\alpha}}\_{t}}{\\beta\_{t}\\left( {1 - {\\overline{\\alpha}}\_{t - 1}} \\right)} \\right)^{- 1}$$  
graphic style="width:28.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn65.gif" position="float"/

  
$${\\widetilde{\\beta}}\_{t} = \\frac{1 - {\\overline{\\alpha}}\_{t - 1}}{1 - {\\overline{\\alpha}}\_{t}}\\beta\_{t}$$  
graphic style="width:6.4375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn66.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = \\left( {\\frac{\\alpha\_{t}}{\\beta\_{t}} + \\frac{1}{1 - {\\overline{\\alpha}}\_{t - 1}}} \\right)^{- 1}\\left( {\\frac{\\sqrt{\\alpha\_{t}}}{\\beta\_{t}}x\_{t} + \\frac{\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t - 1}}x\_{0}} \\right)$$  
graphic style="width:22.3125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn67.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = \\left( {\\frac{\\sqrt{\\alpha\_{t}}}{\\beta\_{t}}x\_{t} + \\frac{\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t - 1}}x\_{0}} \\right)\\frac{1 - {\\overline{\\alpha}}\_{t - 1}}{1 - {\\overline{\\alpha}}\_{t}}\\beta\_{t}$$  
graphic style="width:18.875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn68.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = \\frac{\\sqrt{\\alpha\_{t}}\\left( {1 - {\\overline{\\alpha}}\_{t - 1}} \\right)}{\\left( {1 - {\\overline{\\alpha}}\_{t}} \\right)}x\_{t} + \\frac{\\beta\_{t}\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t}}x\_{0}$$  
graphic style="width:17.4375em;" xlink:href="bk978-0-7503-6244-3ch13ueqn69.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = \\frac{\\sqrt{\\alpha\_{t}}\\left( {1 - {\\overline{\\alpha}}\_{t - 1}} \\right)}{\\left( {1 - {\\overline{\\alpha}}\_{t}} \\right)}x\_{t} + \\frac{\\beta\_{t}\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t}}\\frac{1}{\\sqrt{{\\overline{\\alpha}}\_{t}}}\\left( {x\_{t} - \\varepsilon\\sqrt{1 - {\\overline{\\alpha}}\_{t}}} \\right)$$  
graphic style="width:25.1875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn70.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = \\frac{\\sqrt{\\alpha\_{t}}\\left( {1 - {\\overline{\\alpha}}\_{t - 1}} \\right)}{\\left( {1 - {\\overline{\\alpha}}\_{t}} \\right)}x\_{t} + \\frac{\\beta\_{t}\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t}}\\frac{x\_{t}}{\\sqrt{{\\overline{\\alpha}}\_{t}}} - \\frac{\\beta\_{t}\\sqrt{{\\overline{\\alpha}}\_{t - 1}}}{1 - {\\overline{\\alpha}}\_{t}}\\frac{\\varepsilon}{\\sqrt{{\\overline{\\alpha}}\_{t}}}\\sqrt{1 - {\\overline{\\alpha}}\_{t}}$$  
graphic style="width:28.75em;" xlink:href="bk978-0-7503-6244-3ch13ueqn71.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = \\left( {\\frac{\\sqrt{\\alpha\_{t}}\\left( {1 - {\\overline{\\alpha}}\_{t - 1}} \\right)}{\\left( {1 - {\\overline{\\alpha}}\_{t}} \\right)} + \\frac{1}{\\sqrt{\\alpha\_{t}}}\\frac{\\beta\_{t}}{1 - {\\overline{\\alpha}}\_{t}}} \\right)x\_{t} - \\frac{\\beta\_{t}}{\\sqrt{1 - {\\overline{\\alpha}}\_{t}}}\\frac{\\varepsilon}{\\sqrt{\\alpha\_{t}}}$$  
graphic style="width:26em;" xlink:href="bk978-0-7503-6244-3ch13ueqn72.gif" position="float"/

  
$$\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right) = \\frac{1}{\\sqrt{\\alpha\_{t}}}\\left( {\\frac{\\left( {\\alpha\_{t} - {\\overline{\\alpha}}\_{t}} \\right)}{\\left( {1 - {\\overline{\\alpha}}\_{t}} \\right)} + \\frac{1 - \\alpha\_{t}}{1 - {\\overline{\\alpha}}\_{t}}} \\right)x\_{t} - \\frac{\\beta\_{t}}{\\sqrt{1 - {\\overline{\\alpha}}\_{t}}}\\frac{\\varepsilon}{\\sqrt{\\alpha\_{t}}}$$  
graphic style="width:23.875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn73.gif" position="float"/

  
$${\\widetilde{\\mu}\\left( {x\_{t},x\_{0}} \\right)} = \\frac{1}{\\sqrt{\\alpha\_{t}}}\\left( {x\_{t} - \\frac{1 - \\alpha\_{t}}{\\sqrt{1 - {\\overline{\\alpha}}\_{t}}}\\varepsilon} \\right)$$  
graphic style="width:14.25em;" xlink:href="bk978-0-7503-6244-3ch13ueqn74.gif" position="float"/

**The variational lower bound loss L**[**VLB**]

  
$$L\_{VLB} = - \\int{q\\left( x\_{0} \\right)q\\left( x\_{1:T}\\mid x\_{0} \\right)}\\log\\ \\frac{p\_{\\theta}\\left( x\_{0:T} \\right)}{q\\left( x\_{1:T}\\mid x\_{0} \\right)}dx\_{0:T}$$  
graphic style="width:20.25em;" xlink:href="bk978-0-7503-6244-3ch13ueqn75.gif" position="float"/

  
$$L\_{VLB} = Ε\_{q{(x\_{0:T})}}\\left\\lbrack {\\log\\ \\frac{q\\left( {x\_{1:T} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( x\_{0:T} \\right)}} \\right\\rbrack = Ε\_{q}\\left\\lbrack {\\log\\ \\frac{\\prod\\limits\_{t = 1}^{T}{q\\left( {x\_{t} \\mid x\_{t - 1}} \\right)}}{p\_{\\theta}\\left( x\_{T} \\right)\\prod\\limits\_{t = 1}^{T}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}}} \\right\\rbrack$$  
graphic style="width:26.5em;" xlink:href="bk978-0-7503-6244-3ch13ueqn76.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\log\\ \\frac{\\prod\\limits\_{t = 1}^{T}{q\\left( {x\_{t} \\mid x\_{t - 1}} \\right)}}{\\prod\\limits\_{t = 1}^{T}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}}} \\right\\rbrack = Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 1}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t} \\mid x\_{t - 1}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}} \\right\\rbrack$$  
graphic style="width:33.5625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn77.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t} \\mid x\_{t - 1}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}} \\right\\rbrack + \\log\\ \\frac{q\\left( x\_{1}\\mid x\_{0} \\right)}{p\_{\\theta}\\left( x\_{0}\\mid x\_{1} \\right)}$$  
graphic style="width:23.5625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn78.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}\\frac{q\\left( {x\_{t} \\mid x\_{0}} \\right)}{q\\left( {x\_{t - 1} \\mid x\_{0}} \\right)} + \\log\\ \\frac{q\\left( x\_{1}\\mid x\_{0} \\right)}{p\_{\\theta}\\left( x\_{0}\\mid x\_{1} \\right)}} \\right\\rbrack{according\\ to\\ equation}\\left( 9.4 \\right)$$  
graphic style="width:34.125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn79.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}\\frac{q\\left( {x\_{t} \\mid x\_{0}} \\right)}{q\\left( {x\_{t - 1} \\mid x\_{0}} \\right)} + \\log\\ \\frac{q\\left( {x\_{1} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{0} \\mid x\_{1}} \\right)}} \\right\\rbrack$$  
graphic style="width:28.3125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn80.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)} + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t} \\mid x\_{0}} \\right)}{q\\left( {x\_{t - 1} \\mid x\_{0}} \\right)} + \\log\\ \\frac{q\\left( {x\_{1} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{0} \\mid x\_{1}} \\right)}} \\right\\rbrack$$  
graphic style="width:32.625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn81.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)} + \\log\\ \\prod\\limits\_{t = 2}^{T}\\frac{q\\left( {x\_{t} \\mid x\_{0}} \\right)}{q\\left( {x\_{t - 1} \\mid x\_{0}} \\right)} + \\log\\ \\frac{q\\left( {x\_{1} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{0} \\mid x\_{1}} \\right)}} \\right\\rbrack$$  
graphic style="width:33em;" xlink:href="bk978-0-7503-6244-3ch13ueqn82.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)} + \\log\\ \\frac{q\\left( {x\_{T} \\mid x\_{0}} \\right)}{q\\left( {x\_{1} \\mid x\_{0}} \\right)} + \\log\\ \\frac{q\\left( {x\_{1} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{0} \\mid x\_{1}} \\right)}} \\right\\rbrack$$  
graphic style="width:30.5625em;" xlink:href="bk978-0-7503-6244-3ch13ueqn83.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {- \\log\\ p\_{\\theta}\\left( x\_{T} \\right) + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)} + \\log\\ \\frac{q\\left( {x\_{T} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{0} \\mid x\_{1}} \\right)}} \\right\\rbrack$$  
graphic style="width:24.125em;" xlink:href="bk978-0-7503-6244-3ch13ueqn84.gif" position="float"/

  
$$= \\ Ε\_{q}\\left\\lbrack {\\log\\ \\frac{q\\left( {x\_{T} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( x\_{T} \\right)} + \\sum\\limits\_{t = 2}^{T}{\\ \\log\\ }\\frac{q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)} - \\log\\ p\_{\\theta}(x\_{0}\\mid x\_{1})} \\right\\rbrack$$  
graphic style="width:24.75em;" xlink:href="bk978-0-7503-6244-3ch13ueqn85.gif" position="float"/

  
$$= \\ \\int q\\left( x\_{0:T} \\right)\\log\\ \\frac{q\\left( {x\_{T} \\mid x\_{0}} \\right)}{p\_{\\theta}\\left( x\_{T} \\right)}dx\_{0:T} + \\sum\\limits\_{t = 2}^{T}{Ε\_{q}\\left\\lbrack {\\log\\ \\frac{q\\left( {x\_{t - 1} \\mid x\_{t},x\_{0}} \\right)}{p\_{\\theta}\\left( {x\_{t - 1} \\mid x\_{t}} \\right)}} \\right\\rbrack} - Ε\_{q}\\left\\lbrack {\\log\\ p\_{\\theta}\\left( x\_{0}\\mid x\_{1} \\right)} \\right\\rbrack$$  
graphic style="width:32.5em;" xlink:href="bk978-0-7503-6244-3ch13ueqn86.gif" position="float"/

  
$$= \\ D\_{KL}(q(x\_{T}\\mid x\_{0}){\\mid\\mid}p\_{\\theta}\\left( x\_{T} \\right)) + \\sum\\limits\_{t = 2}^{T}{D\_{KL}\\left( q\\left( x\_{t - 1}\\mid x\_{t},x\_{0} \\right){\\mid\\mid}p\_{\\theta}\\left( x\_{t - 1}\\mid x\_{t} \\right) \\right)} - Ε\_{q}\\left\\lbrack {\\log\\ p\_{\\theta}\\left( x\_{0}\\mid x\_{1} \\right)} \\right\\rbrack$$  
graphic style="width:35em;" xlink:href="bk978-0-7503-6244-3ch13ueqn87.gif" position="float"/

  
$$= \\ L\_{T} + \\sum\\limits\_{t = 2}^{T}L\_{t - 1} + L\_{0}$$  
graphic style="width:8.6875em;" xlink:href="bk978-0-7503-6244-3ch13ueqn88.gif" position="float"/

### J An Improved Version of Project 11.3.1 to Avoid a FAISS Issue

![](images/bk978-0-7503-6244-3app1uf26_pr.gif)

### K Tiny NeRF codes for lego 3D scene synthesis

![](images/bk978-0-7503-6244-3app1uf21_pr.gif)

![](images/bk978-0-7503-6244-3app1uf22_pr.gif)

![](images/bk978-0-7503-6244-3app1uf23_pr.gif)

![](images/bk978-0-7503-6244-3app1uf24_pr.gif)

![](images/bk978-0-7503-6244-3app1uf25_pr.gif)