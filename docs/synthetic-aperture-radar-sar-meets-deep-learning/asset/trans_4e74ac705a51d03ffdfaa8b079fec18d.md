
The training time $T_{all}$ for a mini-batch is:

$$T_{all}=\sum_{0}^{q}T_{fi}+\sum_{0}^{q}T_{bi}+T_{ta}+T_{tb}\tag{8}$$

The equation for calculating the equipment utilization index is as follows:

$$E=-ln\frac{\sum\left(\frac{T_{tx2}^{n}}{T_{all}}-\frac{1}{n}\right)^{2}}{n}\tag{9}$$

The process of CWB searching for the best partition point is formally presented in Algorithm 2. After network partitioning, each partition is assigned to the DHP system for distributed training. The detailed implementation of CWB is recorded in Figure 13.

```
Algorithm 2. CWB search for the best partition point
Step 1: CWB performs memory workload balancing
Step 2: CWB performs time equalization
1: Assign {$M_{w1},M_{w2}\cdots,M_{wq}$} and {$M_{l1},M_{l2}\cdots,M_{lq}$} to {$TX2_1,TX2_2\cdots,TX2_n$}
2: Assume 3 TX2s can satisfy memory allocation, then 2 sets of candidate partition point that satisfy memory workload balancing are recorded as [[a,a+1...],[b,b+1...]]
3: for a in [a,a+1...] do
4: for b in [b,b+1...] do
5: Partition point 1 adopts a
6: Denote the running time of $TX2_1$ as $T_{tx2}^1=\sum_{0}^{a}T_{fi}+\sum_{0}^{a}T_{bi}$
7: Denote the running time of $TX2_2$ as $T_{tx2}^2=\sum_{a}^{b}T_{fi}+\sum_{a}^{b}T_{bi}$
8: Denote the running time of $TX2_3$ as $T_{tx2}^3=\sum_{b}^{q}T_{fi}+\sum_{b}^{q}T_{bi}$
9: The training time $T_{all}$ for a mini-batch is
$T_{all}=\sum_{0}^{q}T_{fi}+\sum_{0}^{q}T_{bi}+T_{ta}+T_{tb}$
10: The partition point uses [a,b], the ratio of running time to waiting time of $TX2_n$ is $\frac{T_{tx2}^n}{T_{all}}$
11: Calculate the equipment utilization indices $E$ using Equation (9)
$E=-ln\frac{\sum\left(\frac{T_{tx2}^n}{T_{all}}-\frac{1}{n}\right)^{2}}{n}$
12: end for
13: end for
14: The partition point of $E$ with the highest score is the best partition point
```

### 3.3.2. 动态链系统

Figure 4a shows our hybrid parallel distributed training baseline schematic, where each node in the chain is fixedly linked to its front and back nodes, and the later nodes in the chain have to wait for the front nodes to finish forward and backward propagation. Overlap network computation time with transmission time is a common method to improve efficiency in distributed training [52], which can improve training efficiency. Our modified dynamic chain is shown in Figure 4b, where three nodes are responsible for the computation of partition 1, two for the computation of partition 2, and one for the computation of partition 3 of the model. We add a communication scheduler module to our distributed training framework, enabling the node that first completes the computation to search for the available nodes in the next layer. Each mini-batch will form a dynamic chain that performs forward and backward propagation, and after each node completes its current backward propagation, it will automatically leave the current chain and construct a new chain with the node that is waiting. Dynamic chain system has higher training efficiency than baseline, improving node utilization without reducing training accuracy. The dynamic chain system can be well generalized for different training demands, and we have conducted additional experiments for different training computations as detailed in Section 6.2.

![](img/828a5d28a36454f7b3332df93f35492f_303_0.png)

Figure 4. Illustration of our proposed distributed hybrid parallel training baseline and dynamic chain system. (a) Distributed hybrid parallel training baseline. (b) Dynamic chain system. In iteration 1, Devices 1, 4, and 6 form a computation chain, while Devices 3 and 5 are in a waiting state. During this time, Device 5 completes the forward computation from Device 2. At the end of iteration 1, Device 6 disconnects from Device 4, automatically links to Device 5, and immediately performs the third part of the training, Device 4 links to Device 3 and waits to link with Device 6. In iteration 3, Device 4 links to Device 6, and the rest nodes also link to available nodes. Subsequent iterations follow the same procedure.

## 4. 实验设置

### 4.1. 数据集描述

For SAR images, we use the OpenSARUrban [14] dataset and the WHU-SAR6 [11] dataset for experiments. We use a small number of training samples to predict a large number of test samples in our experiments, the training proportions for OpenSARUrban dataset are 10% and 20%, and for WHU-SAR6 dataset we set training proportions as 10% and 20%.

- The OpenSARUrban [14] dataset consists of 10 categories of urban scene images collected from Sentinel-1; its scene images cover 21 major cities in China. Each category contains about 40 to 2000 images with a size of 100 × 100 pixels, and the resolution of the images is about 20 m;
- The WHU-SAR6 [11] dataset consists of six categories of scene images collected from Sentinel-1 and GF-3. Each category contains about 250 to 420 images with ranging in size from 500 to 600 pixels. Since the total number of WHU-SAR6 images is relatively small, to increase the dataset volume we crop the images into small patches of 256 × 256 pixels without destroying the scene semantic information.

For optical images, we use the NWPU-RESISC45 [3] dataset and the Aerial Image dataset (AID) [15]. The training proportions for NWPU-RESISC45 dataset are 10% and 20%, which are more challenging since they both require using a small number of training samples to predict labels for many test data. For the AID dataset, we set training proportions as 10%, 20%, and 50%. Detailed information is shown in Table 1.

- The NWPU-RESISC45 [3] dataset is the current largest open benchmark dataset for scene classification task, consisting of 45 categories of scene images. Each category contains 700 images with a size of 256 × 256 pixels, and the spatial resolution of the images is about 0.2 to 30 m.
- The AID [15] dataset consists of 30 categories of scene images; each category containing about 200 to 400 images, for a total of 10,000 samples, each with a size of 600 × 600 pixels.

### 表 1. 数据集描述和训练比例。

| Datasets | Images Number | Categories Number | Training Proportions |
|---|---|---|---|
| OpenSARUrban ¹ [14] | 16679 | 10 | 10%, 20% |
| WHU-SAR6 ² [11] | 17590 | 6 | 10%, 20% |
| NWPU-RESISC45 [3] | 31500 | 45 | 10%, 20% |
| AID [15] | 10000 | 30 | 10%, 20%, 50% |

¹ OpenSARUrban dataset has VH and VV polarizations, we used the VH data. ² For WHU-SAR6 dataset, we cropped the images into small patches of 256 × 256 pixels to increase the dataset volume.

### 4.2. 数据增强

By performing random crop and resize on target image, the receptive field of the network can achieve both global and local prediction, which is crucial for RSSC task. We perform spatial transformations such as random crop, flip, rotate, and resize to enable the model to learn rotation invariants and scaling invariant simultaneously. Further, we simulate temporal transformations with Gaussian blur, color jitter, and random grayscale. The augmentation strategies differ between SAR images and optical images. Detailed data augmentation result is shown in Figure 5.

![](img/828a5d28a36454f7b3332df93f35492f_304_0.png)

Figure 5. Illustration of data augmentations.

### 4.3. 实现细节

The input images were normalized to 224 × 224 and used the data augmentation settings shown in Figure 5. The batch size was set to 64, and all methods were trained for 400 epochs. For all competitive algorithms, we used ResNet-18 [53] as the backbone and removed the fully connected layer after AvgPooling in ResNet-18. Since the loss functions and optimizers of these competitive methods are different, the experimental results are obtained under the individual methods’ respective optimal hyperparameter settings. All competitive algorithms were implemented using PyTorch 1.7, Python 3.7. The proposed Lite-SRL method used an SGD optimizer with a momentum of 0.9 and a weight decay of 1 × 10^{-4}, the initial learning rate was 0.05, and the learning rate decreased using the cosine decay.

The experimental section consists of two parts.

- Experiments of self-supervised learning. In this part we use workstations to compare the proposed Lite-SRL with other advanced self-supervised methods comprehensively. The two workstations are identically configured with NVIDIA RTX 3090 GPU, Intel Xeon CPU E5-1650, and 64 GB RAM.
- Experiments for on-board deployment of Lite-SRL algorithm. We used the proposed distributed training modules and provided detailed records for the deployment process. The experimental on-board computing platform consists of NVIDIA Jetson TX2 nodes and a high-speed switch.

## 5. 实验结果

The flowchart of self-supervised learning experiments is shown in Figure 6. Encoders obtained by self-supervised training are used both as (i) frozen feature extractors (Freeze experiment), and as (ii) initial fine-tune model (Fine-tune experiment). For both the freeze and fine-tune experiments, we connected a linear classifier after the encoder and used an Adam optimizer with a batch size of 64, the learning rate reduced in a cosine manner within 200 epochs.

![](img/828a5d28a36454f7b3332df93f35492f_305_0.png)

Figure 6. The flowchart of self-supervised learning experiments.

### 5.1. 在更少计算下保证精度

We compare (i) overall accuracy, (ii) number of parameters, (iii) memory consumption, and (iv) average training latency with competitive self-supervised algorithms. The memory consumption during network training consists of the following elements. The memory occupied by the model: including the consumption of parameters, gradients and optimizer momentum. The memory occupied by the network intermediate layers’ outputs: including the inputs and outputs of each layer.

Considering that on-board scenario is highly sensitive to the computation workload, the algorithm is required to achieve higher accuracy and less computation simultaneously. Experiments show that Lite-SRL can achieve optimal classification accuracy with minimum computation. As shown in Figure 7, Lite-SRL shows the best accuracy in the RSSC task, while Lite-SRL has a clear advantage in terms of computation consumption. Thus Lite-SRL provides a lightweight yet effective solution for on-board self-supervised representation learning.
