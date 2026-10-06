
## 4 EXPLORING VARIANT METHODS FOR INVARIANT LEARNING

TABLE 4.1. Comparison between OOD generalization methods and our EVIL realization on some methods. Test accuracies on seven OOD generalization benchmarks from DomainBase. Best results and second best are highlighted. † denotes results from [139].

| Algorithm | CMINIST | MNIST | PACS | VLCS | Office | Home | DomainNet | Average | FLOPs |
|---|---|---|---|---|---|---|---|---|---|
| I-Mixup† | 31.3 | 97.8 | 84.6 | 77.4 | 68.1 | 47.9 | 39.2 | 63.7 | |
| MLDG† | 36.9 | 98.0 | 85.2 | 76.8 | 66.8 | 47.8 | 41.2 | 64.6 | |
| MMD† | 42.6 | 98.1 | 83.7 | 78.6 | 65.9 | 42.2 | 23.4 | 62.1 | |
| DANN | 29.0 | 81.3 | 87.8 | 65.9 | 46.7 | 38.3 | 58.3 | 62.5 | |
| Mixstyle† | 31.1 | 96.3 | 85.2 | 77.5 | 66.7 | 45.8 | 58.3 | 62.5 | |
| MTL† | 30.4 | 97.2 | 84.6 | 77.2 | 66.4 | 45.6 | 40.6 | 63.1 | |
| ARM† | 32.6 | 98.1 | 86.2 | 77.6 | 68.1 | 48.6 | 40.3 | 64.5 | |
| RSC† | 35.2 | 96.3 | 85.2 | 77.1 | 65.5 | 46.6 | 38.9 | 63.5 | |
| ERM | 38.5 | 97.2 | 85.2 | 77.9 | 64.0 | 44.0 | 34.0 | 62.4 | 1x |
| EVIL | 34.2 | 98.0 | 84.1 | 76.7 | 66.0 | 43.2 | 33.3 | 61.9 | 1x |
| (±0.1) | (±0.1) | (±0.1) | (±0.2) | (±0.2) | (±0.1) | (±0.3) | | 0.42x |
| DRO | 34.2 | 98.2 | 85.7 | 76.6 | 66.4 | 47.6 | 33.9 | 63.3 | 1x |
| EVIL-Rex | 41.2 | 98.7 | 86.0 | 79.1 | 68.0 | 49.1 | 35.5 | 65.1 | 0.42x |
| (±0.1) | (±0.1) | (±0.1) | (±0.2) | (±0.3) | (±0.1) | (±0.3) | | 1.4x |
| IRM† | 36.3 | 97.7 | 83.5 | 78.8 | 64.2 | 47.6 | 62.1 | 63.1 | |
| EVIL-IRM | 39.1 | 98.3 | 85.1 | 79.8 | 66.4 | 48.3 | 36.0 | 64.6 | 0.42x |
| (±0.2) | (±0.2) | (±0.1) | (±0.2) | (±0.3) | (±0.3) | | 1.5x |
| SWAD | 38.3 | 98.1 | 88.1 | 79.1 | 71.6 | 50.0 | 46.5 | 67.2 | 1x |
| EVIL-SWAD | 38.7 | 98.3 | 88.3 | 79.7 | 71.7 | 51.2 | 46.9 | 67.7 | 0.43x |
| (±0.3) | (±0.3) | (±0.1) | (±0.2) | (±0.2) | (±0.3) | | (±0.5) |
| MIRO | 39.4 | 97.5 | 85.4 | 79.0 | 70.5 | 44.3 | 66.6 | 1x |
| EVIL-MIRO | 40.2 | 98.6 | 85.8 | 79.4 | 71.2 | 50.9 | 45.0 | 67.3 | 0.45x |
| (±0.3) | (±0.3) | (±0.1) | (±0.2) | (±0.2) | (±0.3) | | (±0.7) |
| SAM | 38.5 | 98.1 | 85.8 | 79.4 | 69.6 | 43.3 | 44.3 | 65.6 | 2x |
| EVIL-SAM | 40.4 | 98.8 | 87.8 | 80.1 | 70.3 | 50.5 | 45.0 | 67.5 | 0.89x |
| (±0.3) | (±0.3) | (±0.1) | (±0.1) | (±0.2) | (±0.3) | | | |

### 4.5.2 Experimental Setup

Evaluation Protocol. We follow the experimental setting of DomainBed [176] to evaluate OOD generalization performance. Specifically, DomainBed contains several benchmark datasets: CMMNIST [69] (60,000 images, 10 classes, and 3 domains), MNIST [211] (60,000 images, 10 classes, and 6 domains), PACS [177] (9,991 images, 7 classes, 4 domains), VLCS [212] (10,729 images, 5 classes, and 4 domains), OfficeHome [213] (15,588 images, 65 classes, and 4 domains), TerraIncognita [214] (24,788 images, 10 classes, and 4 domains), DomainNet [147] (586,575 images, 345 classes, and 6 domains), WILDS [215] (a testbed with significant shift, here we use two typical datasets: WildCam and FarmW), ImageNet [104] (1000 images, here we use ImageNet for fine-tuning, and many of its variant for OOD evaluation, including ImageNetV2 [216], ImageNetR [217], ImageNetA [218], ImageNetSketch [219], and ObjectNet [220]). For each benchmark dataset, we leave one out of the training dataset and use it as OOD test dataset. Moreover, we use pre-trained ResNet-50 [3] as our backbone and train it for 5,000 iterations on all datasets, which requires 15,000 iterations to converge. To avoid randomness, three independent trials are conducted to provide the results.

### 4.5.3 Improving Invariant Learning Using EVIL

In this section, we deploy our EVIL framework to some well-known invariant learning methods and compare them with other baseline methods. To conduct a comparison, we only consider end-to-end training on a single model, so other methods that conduct ensembles or averaging [139, 221, 223] are not considered. Moreover, we use floating point operations per second (FLOPs) to denote the computational efficiency by denoting the FLOPs of ERM as $1 \times$. Practically, we set the sparsity ratio $R=60\%$, parameter $\alpha=0.2$, and $\Delta T=30$ to implement EVIL. The results are shown in Table 4.1. We can see that EVIL can effectively improve the performance of all chosen backbone methods. Particularly, on ERM, DRO, and SAM, EVIL can increase their test accuracies by 2.4%, 1.9%, and 1.9%, respectively.

TABLE 4.2. Comparison between existing sparse methods and EVIL varying sparsity levels. The test accuracies on OOD generalization benchmarks from DomainBase. We highlight the best and second best results.

| Algorithm | CMINIST | MNIST | PACS | VLCS | OfficeHome | Terra | DomainNet | Average | FLOPs |
|---|---|---|---|---|---|---|---|---|---|
| MRM | 31.5 (±2.4) | 89.3 (±0.3) | 78.3 (±0.2) | 70.0 (±0.1) | 63.6 (±0.1) | 42.7 (±0.3) | 59.0 | 0.82× |
| SparseM | 31.5 (±2.4) | 95.8 (±0.2) | 71.2 (±0.2) | 66.2 (±0.1) | 63.7 (±0.1) | 39.6 (±0.3) | 60.3 | 0.81× |
| EVIL | 34.1 (±2.7) | 95.8 (±0.2) | 82.2 (±0.3) | 73.7 (±0.2) | 66.3 (±0.1) | 45.3 (±0.1) | 62.7 | 0.82× |
| EVIL-SAM | 35.2 (±2.3) | 96.3 (±0.2) | 88.6 (±0.1) | 74.2 (±0.1) | 65.6 (±0.1) | 45.6 (±0.1) | 63.2 | 1.62× |
| MRM | 36.2 (±2.4) | 95.8 (±0.2) | 81.9 (±0.3) | 73.5 (±0.1) | 63.1 (±0.1) | 45.6 (±0.1) | 62.2 | 0.62× |
| SparseM | 35.7 (±2.4) | 96.4 (±0.2) | 82.5 (±0.2) | 74.2 (±0.1) | 66.8 (±0.1) | 47.8 (±0.1) | 63.7 | 0.62× |
| EVIL | 38.9 (±2.4) | 97.2 (±0.1) | 84.7 (±0.2) | 75.3 (±0.1) | 66.4 (±0.1) | 47.1 (±0.1) | 64.8 | 0.62× |
| EVIL-SAM | 38.8 (±2.4) | 97.9 (±0.1) | 83.6 (±0.3) | 77.4 (±0.2) | 66.9 (±0.1) | 48.1 (±0.1) | 65.6 | 1.33× |
| MRM | 38.2 (±2.4) | 97.0 (±0.1) | 83.6 (±0.2) | 76.8 (±0.1) | 66.5 (±0.1) | 46.7 (±0.1) | 64.2 | 0.41× |
| SparseM | 37.9 (±2.4) | 94.9 (±0.2) | 84.3 (±0.2) | 76.5 (±0.1) | 65.1 (±0.1) | 48.8 (±0.1) | 64.8 | 0.42× |
| EVIL | 39.4 (±2.4) | 96.4 (±0.1) | 89.5 (±0.2) | 80.2 (±0.1) | 68.2 (±0.1) | 49.1 (±0.2) | 66.3 | 0.42× |
| EVIL-SAM | 40.4 (±2.2) | 98.8 (±0.1) | 97.8 (±0.1) | 80.1 (±0.1) | 70.3 (±0.1) | 50.5 (±0.1) | 67.0 ( 0.2) | |
| MRM | 37.7 (±2.4) | 96.3 (±0.1) | 83.6 (±0.2) | 72.0 (±0.1) | 61.2 (±0.1) | 42.7 (±0.1) | 60.8 | 0.81× |
| SparseM | 37.8 (±2.4) | 97.2 (±0.1) | 82.9 (±0.2) | 71.6 (±0.1) | 65.4 (±0.1) | 43.8 (±0.1) | 66.7 | 0.81× |
| EVIL | 38.5 (±2.4) | 98.1 (±0.1) | 89.7 (±0.2) | 80.2 (±0.1) | 68.7 (±0.1) | 50.1 (±0.1) | 71.7 | 0.62× |
| EVIL-SAM | 40.1 (±2.2) | 98.3 (±0.1) | 97.8 (±0.2) | 85.3 (±0.1) | 75.7 (±0.1) | 52.4 (±0.1) | 75.4 | 0.57× |

### 4.5.4 Comparing Ours to Sparse Invariant Learning

Furthermore, to show that our method is robust for OOD generalization, we compare it with existing sparse learning methods. Specifically, under sparsity ratio to 20%, 40%, 60%, and 80%, the results are shown in Table 4.2. Generally, we can see that EVIL and EVIL-SAM surpass MRM and SparseIRM in almost all scenarios. Moreover, over all sparsity levels, EVIL and the other methods achieve the best results under 60%. Specifically, EVIL-SAM shows the best performance under 60% on all datasets, and it surpasses the second-best opponent for 2.8% on average accuracy. Beside, EVIL implementation with JER can also improve the second-best methods by 1.5% on the averaged results. As for the computational efficiency, our EVIL is comparable to other sparse training methods, except EVIL-SAM, which requires an extra backward pass to compute the parameter perturbation.

### 4.5.5 Performance on Additional Invariant Learning Methods

We have discussed several invariant learning methods in the main paper, we conduct extra experiments on PACS dataset using additional invariant learning methods to show how EVIL affect their OOD generalization results. Moreover, we conduct experiments using different network architectures to show the effect of EVIL on various learning models.

## 4.5 EXPERIMENT

TABLE 4.3. Results on additional learning methods.

| Method | MMD | SagNet | Mixstyle | ARM |
|---|---|---|---|---|
| w/o EVIL | 84.7 | 86.3 | 85.2 | 85.1 |
| with EVIL | **85.3** | **87.1** | **86.5** | **86.6** |
