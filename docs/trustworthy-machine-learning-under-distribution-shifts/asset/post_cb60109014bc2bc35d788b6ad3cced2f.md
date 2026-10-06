
based on the theoretical framework proposed by Xie et al. [297], we show that when MLLM achieving the most probable $z$ based on the given prompt $S_n$ and query image-text pair $x_q y_q$ under a concept $\phi^*$, the corresponding $y$ is the same as the one found from $p_{prompt}$, which is $y_q$ that matches with $x_q$.

# ASSUMPTION 3 (Distribution consistency). $\forall(x_q y_q) \sim p_{prompt}, p(x_q, y_q) = p_{prompt}(x_q, y_q)$.

Moreover, the assumptions from Xie et al. [297] also hold, then we have:

THEOREM 4. *Assume that the above assumptions hold, if $\phi \in \Phi, \phi \neq \phi^*$, the concept $\phi^*$ satisfies the distinguishability condition:* $\sum_{j=1}^n KL(\phi^*|\phi) > e_{start} + e_{delim}$, then as $n \to \infty$, the prediction according to the pretraining distribution

$$\max_y p(y|S_n, x_q, \phi^*) \to \max_y p_{prompt}(y|x_q).$$

Thus, the in-context predictor $f_n$ achieves the optimal $0-1$ risk: $\lim_{n \to \infty} \mathcal{L}_{0-1}(f_n) = \inf f \mathcal{L}_{0-1}(f)$.

LEMMA 1. *Under the same condition of Theorem 4, the prediction $z$ according to the pretraining distribution*

$$\max_z p(z|S_n, x_q, y_q, \phi^*) \to \max_z p_{prompt}(z|x_q, y_q).$$

THEOREM 5. *Assume that the above assumptions hold, as $n \to \infty$, when achieving the largest prediction probability of $z$ given prompt under concept $\phi^*$, the corresponding class description $y$ follows the same $y$ obtained from the prompt distribution:*

$$\max_z p(z|S_n, x_q, y_q, \phi^*) \to \max_z p_{prompt}(z|x_q, y_q).$$

We can see that if $n$ is large enough, the MLLM prediction $z$ achieves the largest value when $y_q$ is the exact match to $x_q$. As a result, we can justify that only when we find the positive image-text pair to the MLLM, the prediction $z$ is the largest among all combinations between $x_q$ and $y_q \in \mathcal{Y}$, and $y_q \neq y_t$.

## 5.4 EXPERIMENT

In this section, we first provide our experimental details. Then we conduct quantitative comparisons with the state-of-the-art vision models. Finally, we conduct ablation studies and analyses to qualitatively validate our...

### 5.4.1 Experimental Setup

**Datasets.** In use we well-known ID datasets including ImageNet-1K [281] validation dataset, ImageNet-V2 [216], CIFAR10 [107], CIFAR100 [107] and MNIST [299]. We evaluate OOD generalization that are commonly considered OOD cases, ImageNet-A [218], ImageNet-R [217], ImageNet-Sketch [219], ImageNet-V [300], iWild-Cam [301], and DomainNet [302].

**Settings.** For model evaluation, we randomly select 5000 images from the ImageNet validation set (In-Val), ImageNet-V2 (IN-V2), ImageNet-A (IN-A), ImageNet-R (IN-R), ImageNet-Sketch (IN-SK), ImageNet-V (IN-V) and 10000 images independently from CIFAR10, CIFAR100, MNIST per category to construct a support set to provide in-content exemplars. We evaluate iWildCam from WILDS and VLCS, OfficeHome, and DomainNet from DomainBed. For the details of implementation, we use the top-6 noisy choices to conduct MVT. Specifically, we set the threshold $\delta=0.6$ to diagnose incorrect predictions, then we retrieve exemplars from the support set based on the most similar logic prediction to query images.

**Models and baseline.** For vision backbone, we employ CLIP models [225] and use ViT-L and ViT-g [298] as the vision model to be enhanced. For the LLM backbone, we consider two existing works CLIP [280] and Otter [252] that possess multimodal ability. Additionally, we conduct Visual Questionswering (VQA) to directly map LLMs to the class of query images. Moreover, we conduct vanilla-tuning (Vanilla FT) using $D^{inp}$ as a baseline. The performance using LLM prediction is denoted as MVT and our fine-tuning result is denoted as FT.

TABLE 5.1. Classification accuracy (%) of baseline CLIP models and our method on 5 ID datasets and 5 OOD datasets. The baseline methods include ViT-L CLIP [225] and ViT-g from EVA [298], VQA, and Vanilla FT.

| Arch | Method | IN-Val | IN-V2 | CIFAR10 | MNIST | IN-A | IN-R | IN-K | IN-V | iWildcam |
|---|---|---|---|---|---|---|---|---|---|---|
| RN50 | CLIP | 59.7 | 52.6 | 71.5 | 41.9 | 58.5 | 23.9 | 60.7 | 35.4 | 31.1 | 8.2 |
| RN101 | CLIP | 61.7 | 52.6 | 80.8 | 48.8 | 51.6 | 30.2 | 66.7 | 40.9 | 35.4 | 12.3 |
| ViT-B | CLIP | 62.6 | 59.1 | 89.9 | 65.0 | 47.9 | 32.2 | 67.9 | 59.4 | 51.8 | 10.9 |
| | VQA | 75.8 | 70.2 | 95.6 | 78.2 | 76.4 | 69.3 | 87.3 | 59.6 | 56.2 | 13.3 |
| ViT-L | VQA | 71.6 | 70.8 | 96.1 | 83.2 | 53.7 | 56.7 | 64.6 | 87.4 | 60.3 | 15.2 |
| | MVT | 75.2 | 70.2 | 78.9 | 80.3 | 75.7 | 70.8 | 87.5 | 81.2 | 59.1 | 25.0 |
| | +FT | 71.6 | 70.5 | 92.2 | 82.2 | 82.2 | 71.2 | 79.5 | 61.4 | 68.4 | |
| ViT-g | EVA | 78.8 | 71.2 | 98.3 | 84.5 | 62.2 | 71.9 | 91.4 | 67.4 | 64.9 | 21.9 |
| | VQA | 64.3 | 59.6 | 97.9 | 84.5 | 55.7 | 64.6 | 87.4 | 58.2 | 59.2 | 19.7 |
| | Vanilla FT | 78.9 | 71.8 | 98.7 | 89.1 | 62.9 | 72.7 | 91.6 | 68.1 | 65.6 | 22.4 |
| | MVT | **79.1** | 71.6 | 98.1 | 89.0 | 63.2 | 73.2 | 91.4 | 67.9 | 66.3 | **25.1** |
| | +FT | 79.0 | 72.2 | 98.9 | **91.2** | **65.7** | **75.5** | **92.8** | **68.6** | **78.6** | **70.6** |

TABLE 5.2. Classification accuracy (%) of baseline CLIP models and our method on 4 subsets of datasets. The baseline methods include ViT-L from CLIP, ViT-g from EVA, VQA, and Vanilla FT.

| Method | VLCS | PACS | OfficeHome | DomainNet | Avg |
|---|---|---|---|---|---|
| ViT-L | CLIP | 74.9 | 83.5 | 80.3 | 74.5 | 78.3 |
| | Vanilla FT | 78.8 | 85.2 | 83.4 | 77.0 | 81.1 |
| | MVT | 83.9 | 89.0 | 87.2 | 80.3 | 85.1 |
| | +FT | 84.2 | 89.8 | 87.9 | 82.5 | 88.6 |
| ViT-g | EVA | 72.5 | 80.0 | 79.8 | 72.8 | 76.3 |
| | Vanilla FT | 75.5 | 82.3 | 81.1 | 75.5 | 78.6 |
| | MVT | 81.2 | 86.6 | 86.1 | 79.5 | 83.4 |
| | +FT | 83.7 | 89.5 | 89.9 | 82.0 | 88.8 |

TABLE 5.3. Classification accuracy (%) of baseline CLIP models and our method with MMICL [280] and Otter [252] as the VLMs on 5 ID datasets and 5 OOD datasets. We compare the performance of our method, and the fine-tuned models supervised by our method with the baseline models, i.e., Vit-L from CLIP [225]. Fine-tuning with both MMICL and Otter improves the classification accuracy.

| MLLM | Method | IN-Val | IN-V2 | CIFAR10 | CIFAR100 | MNIST |
|---|---|---|---|---|---|---|
| None | CLIP | 75.8 | 70.2 | 95.6 | 78.2 | 76.4 |
| MMICL | MVT | 75.2 | 70.8 | 97.9 | 78.9 | 53.0 |
| | +FT | 74.2 | 70.5 | 96.7 | 82.0 | 79.2 |
| Otter | MVT | 74.2 | 67.4 | 94.7 | 70.1 | 52.0 |
| | +FT | 76.3 | 70.1 | 96.6 | 81.8 | 81.3 |

| MLLM | Method | IN-A | IN-R | IN-SK | IN-V | iWildCam | Avg (ID+OOD) |
|---|---|---|---|---|---|---|
| None | CLIP | 69.3 | 86.6 | 59.4 | 51.8 | 13.4 | 61.7 |
| MMICL | MVT | 71.2 | 88.1 | 59.0 | 62.1 | 25.0 | 64.3 |
| | +FT | 75.1 | 89.5 | 61.4 | 68.8 | | 75.6 |
| Otter | MVT | 64.1 | 85.2 | 59.5 | 51.9 | 16.2 | 60.3 |
| | +FT | 73.5 | 88.7 | 60.0 | 55.7 | | 73.0 |

## 5.4.2 Quantitative Comparison

First, we compare our MVT method with well-known vision models under both ID and OOD scenarios. As shown in Table 5.1, we can see that our method fine-tuning denoted as
