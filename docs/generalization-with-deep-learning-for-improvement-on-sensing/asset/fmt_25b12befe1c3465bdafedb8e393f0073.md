
The objective of this book is to disseminate inspiring research results and exemplary best practices of deep learning approaches to tackle the technical challenges in various sensing applications. The book will cover the fundamentals of deep learning techniques and their applications in real-world problems including activity sensing, remote sensing and medical sensing. It will demonstrate how different deep learning techniques help to improve the sensing capabilities and enable scientists and practitioners to make insightful observations and invaluable discoveries from data.

## Organization of the Book

This book consists of 12 chapters, which are organized into four major parts: Introduction of Deep Learning Algorithms ([Part I](#part1.xhtml)), Deep Learning for Activity Sensing ([Part II](#part2.xhtml)), Deep Learning for Remote Sensing ([Part III](#part3.xhtml)) and Deep Learning for Medical Sensing ([Part IV](#part4.xhtml)).

[Part I](#part1.xhtml) is composed of [Chapter 1](#chap1.xhtml). In [Chapter 1](#chap1.xhtml), we first briefly introduce various deep learning algorithms for improving sensing capability. We also discuss their advantages and disadvantages for different applications.

[Part II](#part2.xhtml) is composed of [Chapters 2](#chap2.xhtml)–[6](#chap6.xhtml) and introduces deep learning for activity sensing. In particular, [Chapter 2](#chap2.xhtml) presents a new hierarchically aggregated convolutional neural network (`CNN`) architecture that can more effectively deal with long-term dynamics presented in action videos. In particular, the proposed network takes a long term video as input and exploits temporal information at multiple levels of the network hierarchy capturing more complex dynamics of the input sequence. [Chapter 3](#chap3.xhtml) proposes to combine domain knowledge and deep learning in order to improve activity recognition models, where the domain knowledge focuses on the topological structure of on-body sensor-deployments and the mutual interactions among the sensors. [Chapter 4](#chap4.xhtml) introduces how deep learning and unsupervised domain adaptation method further empower WiFi-based sensing. [Chapter 5](#chap5.xhtml) focuses on how to weaken the accuracy differences among individuals in human activity recognition and improves the robustness in a single indoor environment. [Chapter 6](#chap6.xhtml) introduces a spatial temporal graph convolutional network (`GCN`)-based prediction network for skeleton-based video anomaly detection.

[Part III](#part3.xhtml) is composed of [Chapters 7](#chap7.xhtml)–[9](#chap9.xhtml) and presents deep learning for remote sensing applications. Particularly, [Chapter 7](#chap7.xhtml) reviews the current approaches and discusses ways forward to develop new deep learning methods for Earth sciences. [Chapter 8](#chap8.xhtml) presents an empirical evaluation for built-up area detection from remote sensing images using deep learning methods including double-stream `CNN` (`DSCNN`), lightweight multi-branch `CNN` (`LMB-CNN`) and fully convolutional networks (`FCN`). [Chapter 9](#chap9.xhtml) presents `GCN` variants by combining `GCN` with manifold assumptions to exactly acquire the spatial structure information of graph-structured data for remote sensing image recognition. In particular, the `GCN` variants include two-order `GCN`, Hypergraph p-Laplacian `GCN`, manifold regularized dynamic `GCN`.

[Part IV](#part4.xhtml) is composed of [Chapters 10](#chap10.xhtml)–[12](#chap12.xhtml) and focuses on deep learning for medical sensing applications. In particular, [Chapter 10](#chap10.xhtml) proposes a deep learning-based retinal image non-uniform illumination removal called `NuI-Go`, which combines the powerful capabilities of `CNN` with the characteristics of retinal images with non-uniform illumination. [Chapter 11](#chap11.xhtml) presents and evaluates deep learning models (e.g., `SqueezeNet` and `GoogLeNet`) to classify brain tumor MRI images. In [Chapter 12](#chap12.xhtml), the deep learning algorithms with long short-term memory (`LSTM`) and bi-directional `LSTM` are unitized to recognize dementia-related wandering patterns based on the orientation data available in mobile devices.

In this book, we have introduced deep learning algorithms and their applications to improve the sensing capabilities, including activity sensing, remote sensing and medical sensing. Taking human activity recognition as an example, it is a crucial technology for many real-world human-centric applications, especially in the areas of eldercare, healthcare, smart home, security, pervasive and mobile computing, etc. However, it is a challenging task to achieve very accurate prediction results, due to device heterogeneity, environment changes and difficulties to recognize concurrent activities and group activities. Similarly, for remote sensing and medical sensing applications, they usually require domain knowledge and could also be affected by environment changes. We have thus covered representative latest research outcomes and practices in this book that could be very useful for addressing the challenging research problems in the above sensing applications.

We would like to take this opportunity to thank all the authors who contributed to the exciting and important research topics of developing deep learning approaches for various sensing applications. Our heartfelt thanks also go to our book reviewers who have provided very useful comments and valuable feedback, and to the publishing team at World Scientific for providing invaluable contributions and guidance throughout the whole process from inception of the initial idea to the final publication of this book.

## Contents

[*About the Editors*](#about.xhtml)

[*Preface*](#preface.xhtml)

[**Part I Introduction of Deep Learning Algorithms**](#part1.xhtml)

[Chapter 1 An Introduction of Deep Learning Methods for Sensing Applications](#chap1.xhtml)

*Keyu Wu, Wei Cui, Vuong Nhu Khue and Efe Camci*

[**Part II Deep Learning for Activity Sensing**](#part2.xhtml)

[Chapter 2 Hierarchically Aggregated Deep Convolutional Neural Networks for Action Recognition](#chap2.xhtml)

*Le Zhang, Jagannadan Varadarajan, Yong Pei and Zhenghua Chen*

[Chapter 3 Combining Domain Knowledge and Deep Learning to Improve HAR Models](#chap3.xhtml)

*Massinissa Hamidi and Aomar Osmani*

[Chapter 4 Deep Learning and Unsupervised Domain Adaptation for WiFi-based Sensing](#chap4.xhtml)

*Jianfei Yang, Han Zou, Lihua Xie and Costas J. Spanos*

[Chapter 5 Deep Learning for Device-free Human Activity Recognition Using WiFi Signals](#chap5.xhtml)

*Linlin Guo, Hang Zhang, Weiyu Guo, Jian Fang, Bingxian Lu, Chenfei Ma, Guanglin Li, Chuang Lin and Lei Wang*

[Chapter 6 Graph Convolutional Neural Network for Skeleton-based Video Abnormal Behavior Detection](#chap6.xhtml)

*Weixin Luo, Wen Liu and Shenghua Gao*

[**Part III Deep Learning for Remote Sensing**](#part3.xhtml)

[Chapter 7 Perspective on Deep Learning for Earth Sciences](#chap7.xhtml)

*Gustau Camps-Valls*

[Chapter 8 Accurate Detection of Built-Up Areas in Remote Sensing Image via Deep Learning](#chap8.xhtml)

*Yihua Tan, Shengzhou Xiong and Pei Yan*

[Chapter 9 Recent Advances of Manifold-based Graph Convolutional Networks for Remote Sensing Images Recognition](#chap9.xhtml)

*Sichao Fu and Weifeng Liu*

[**Part IV Deep Learning for Medical Sensing**](#part4.xhtml)

[Chapter 10 Deep Retinal Image Non-Uniform Illumination Removal](#chap10.xhtml)

*Chongyi Li, Huazhu Fu, Miao Yang, Runmin Cong and Chunle Guo*

[Chapter 11 A Comparative Analysis of Efficient CNN-based Brain Tumor Classification Models](#chap11.xhtml)

*Tanveer Hussain, Amin Ullah, Umair Haroon, Khan Muhammad and Sung Wook Baik*

[Chapter 12 Classification of Travel Patterns Including Wandering Based on Bi-directional Long Short-Term Memory Networks](#chap12.xhtml)

*Nhu Khue Vuong, Yong Liu, Syin Chan, Chiew Tong Lau, Zhenghua Chen, Min Wu and Xiaoli Li*

[*Index*](#index.xhtml)

## Part I
