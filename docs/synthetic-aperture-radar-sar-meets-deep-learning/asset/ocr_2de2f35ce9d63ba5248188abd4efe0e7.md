In particular, our proposed algorithm consists of three parts: (1) parallel pseudo-label training sample generation, (2) model optimization for TCD-Net, and (3) binary change map generation. Therefore, the main contribution of this study can be summarized as:

+   1. Developing a new unsupervised DL-based model with three channels for deep feature extraction and evaluating the effectiveness of an intermediate channel by comparing this algorithm with a dual-channel deep network;
+   2. Introducing an adaptive formula for determining the number of filters in the multi-scale block due to the dependence of the deep features on the kernel size;
+   3. Proposing high confidence automatic pseudo-label training sample generation framework using a probabilistic parallel scheme based on a pre-trained neural network model and FCM algorithm;
+   4. Providing highly robust results for PolSAR CD compared with the state-of-the-art (SOTA) unsupervised methods.

The rest of the paper is organized as follows. The methodology is described in Section 2. Section 3 presents the case study. Section 4 presents the experimental results and analyses. Section 5 provides the discussion. Finally, the conclusions and future work is presented in Section 6.

# 2. Methodology

In this section, we describe the details of the proposed method for CD. According to Figure 1, the general scheme of the proposed method consists of three main steps, including (1) pre-processing, (2) automatic training sample generation, and (3) end-to-end CD learning. We describe these three steps in detail in the following three sub-sections.

![](bbox=[0.25, 0.73, 0.75, 0.92])

Figure 1. General scheme of the proposed unsupervised binary change detection (CD) method. CNN is convolutional neural network.