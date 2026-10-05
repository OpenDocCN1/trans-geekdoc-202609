# CHAPTER 3

# Multivariate pattern recognition
by machine learning methods

Parvin Razzaghi$^a$, Karim Abbasi$^b$, and Jahan B. Ghasemi$^c$

$a$Department of Computer Science and Information Technology, Institute for Advanced Studies in Basic Sciences (IASAS), Zanjan, Iran
$^b$Laboratory of System Biology, Bioinformatics & Artificial Intelligent in Medicine (LBB&AI), Faculty of Mathematics and Computer Science, Kharazmi University, Tehran, Iran
$^c$Faculty of Chemistry, University of Tehran, Tehran, Iran

# 1. Introduction

In pattern recognition, the goal is to identify patterns and regularities of data with minimal intervention (Bishop, 2006). Finding the patterns and regularities is done using machine learning algorithms. In other words, pattern recognition is the engine learning backbone in computer science. Machine learning algorithms map the input data to the output, and they consist of two main steps: the training step and the inference step. In the training step, the training data is utilized to learn a model, and in the inference step, the learned model is used to map unseen data to the output space. Machine learning algorithms are divided into four categories from the view of the available training data: (1) unsupervised learning, (2) semi-supervised learning, (3) weakly supervised learning, and (4) unsupervised learning. In supervised learning, all the training data are fully annotated (labeled) as compared to unsupervised learning in which none of the training data is labeled. In semi-supervised learning, some portion of training data is unlabeled. If the whole training data is not fully labeled (i.e., partially labeled), then it is weakly supervised learning. In this chapter, we focus on supervised learning and each section.

Given $\{(x^{(i)}, y^{(i)}\}_{i=1}^N$ denotes the training samples where $x^{(i)} \in \mathcal{X}$ and $y^{(i)} \in \mathcal{Y}$ show the input and output of the $i^{th}$ sample, respectively. The main goal is to learn a model which maps an unseen data $x^*$ from the input space to the output space. The overall schematic of the machine learning approaches is shown in Fig. 3.1. As it is represented, the first step of machine learning algorithms is feature extraction in which and discriminative knowledge from the raw data is extracted. After extracting features for