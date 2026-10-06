# TABLE 5.2. Classification accuracy (%) of baseline CLIP models and our method on 4 subsets of BaselineBed datasets. The baseline methods include ViT-L from CLIP, ViT-g from EVA, VQA, and Vanilla FT.

| | | VLCS | | | | PACS | | | |
|---|---|---|---|---|---|---|---|---||
| | Method | 0 | 1 | 2 | 3 | 0 | 1 | 2 | 3 |
| ViT-L | CLIP | 74.9 | 83.5 | 80.3 | 74.5 | 97.8 | 97.4 | 97.5 | 99.4 |
| | Vanilla FT | 78.8 | 85.2 | 83.4 | 77.0 | 98.0 | 97.6 | 97.7 | 99.6 |
| | MVT | 83.9 | 89.0 | 87.2 | 80.3 | 97.6 | 97.5 | 98.0 | 99.4 |
| | +FT | 84.2 | 89.8 | 87.9 | 82.5 | 94.2 | 98.0 | 98.0 | 99.8 |
| ViT-g | EVA | 72.5 | 80.0 | 79.8 | 72.8 | 99.0 | 98.8 | 98.9 | 99.8 |
| | Vanilla FT | 75.5 | 82.3 | 81.1 | 75.5 | 98.0 | 98.0 | 98.0 | 99.8 |
| | MVT | 81.2 | 86.6 | 86.1 | 79.5 | 98.2 | 98.0 | 98.0 | 99.4 |
| | +FT | 83.7 | 89.5 | 86.9 | 82.0 | 99.1 | 98.9 | 99.9 | 100.0 |
| | | OfficeHome | | | | DomainNet | | | |
| | | Method | 0 | 1 | 2 | 3 | 0 | 1 | 2 | 3 | Avg |
| ViT-L | | CLIP | 87.7 | 92.7 | 85.7 | 85.6 | 61.1 | 62.0 | 78.4 | 51.1 | 80.6 |
| | | Vanilla FT | 87.9 | 93.1 | 87.1 | 86.9 | 62.0 | 62.5 | 70.5 | 51.9 | 81.6 |
| | | MVT | 87.7 | 93.4 | 89.0 | 88.5 | 61.3 | 62.1 | 70.7 | 53.4 | 82.8 |
| | | +FT | 90.7 | 95.0 | 90.9 | 90.8 | 62.1 | 63.8 | 62.2 | 81.0 | 54.0 | 84.0 |
| ViT-g | | EVA | 90.5 | 94.2 | 88.6 | 81.6 | 61.4 | 64.7 | 62.1 | 81.6 | 54.9 | 81.6 |
| | | Vanilla FT | 90.6 | 94.5 | 89.2 | 89.0 | 61.5 | 64.9 | 61.3 | 81.8 | 54.8 | 82.3 |
| | | MVT | 89.7 | 93.8 | 89.7 | 89.1 | 62.2 | 65.0 | 61.6 | 82.3 | 56.1 | 83.3 |
| | | +FT | 91.6 | 95.1 | 90.7 | 90.6 | 61.9 | 64.8 | 63.2 | 81.9 | 56.6 | 84.4 |

**Models and baseline.** For vision backbone, we employ CLIP models [2225] and use ViT-L/14 and ViT-g [303] from EVA [298] as the vision model to be enhanced. For the LLM backbone, we consider two existing works MMCL [280] and Otter [052] that possess multimodal ability. Additionally, we conduct Visual Question Answering (VQA) to directly map LLMs to the class of query images. Moreover, we conduct vanilla fine-tuning (Vanilla FT) using $D^{inp}$ as a baseline. The performance of using LLM prediction is denoted as MVT and our fine-tuning result is denoted as FT.

**Settings.** For model evaluation, we randomly select 5000 images independently from the ImageNet validation set (In-Val), ImageNet-V2 (IN-V2), ImageNet-A (IN-A), ImageNet-R (IN-R), ImageNet-Sketch (IN-SK), ImageNet-V (IN-V) and 10000 images independently from CIFAR10, CIFAR100, MNIST to conduct the test samples. Additionally we select