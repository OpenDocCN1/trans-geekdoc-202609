TABLE 5.3. Classification accuracy (%) of baseline CLIP models and our method with MMICL [280] and Otter [250] as the VLMs on 5 ID datasets and 5 OOD datasets. We compare the performance of our method, and the fine-tuned models supervised by our method with the baseline models, i.e., Vit-L from CLIP [225]. Fine-tuning with both MMICL and Otter improves the classification accuracy.

| MLLM | Method | IN-Val | IN-V2 | CIFAR10 | CIFAR100 | MNIST |
|---|---|---|---|---|---||
| None | CLIP | 75.8 | 70.2 | 95.6 | 78.2 | 76.4 |
| MMICL | MVT | 75.2 | 70.8 | 97.9 | 78.9 | 53.0 |
| | +FT | 74.2 | 70.5 | 96.7 | 82.0 | 79.2 |
| Otter | MVT | 74.2 | 67.4 | 94.7 | 70.1 | 52.0 |
| | +FT | 76.3 | 70.1 | 96.6 | 81.8 | 81.3 |

| MLLM | Method | IN-A | IN-R | IN-SK | IN-V | iWildCam | Avg (ID+OOD) |
|---|---|---|---|---|---|---|---||
| None | CLIP | 69.3 | 86.6 | 59.4 | 51.8 | 13.4 | 61.7 |
| MMICL | MVT | 71.2 | 88.1 | 59.0 | 62.1 | 25.0 | 64.3 |
| | +FT | 75.1 | 89.5 | 61.4 | 68.8 | | 75.6 |
| Otter | MVT | 64.1 | 85.2 | 59.5 | 51.9 | 16.2 | 60.3 |
| | +FT | 73.5 | 88.7 | 60.0 | 55.7 | | 73.0 |

images per category to construct a support set to provide in-content exemplars. We evaluate iWildCam from WILDS and VLCS, OfficeHome, and DomainNet from DomainBed. For the details of implementation, we use the top-6 noisy choices to conduct MVT. Specifically, we set the threshold $\delta=0.6$ to diagnose incorrect predictions, then we retrieve exemplars from the support set based on the most similar logic prediction to query images. For each round of DICL, we repeat the process for 3 times and average the model predictions. Fine-tuning, we optimize the vision models for 3 epochs using Adam and SGD optimizers for ViT-L and ViT-G, respectively.

#  5.4.2 Quantitative Comparison

First, we compare our MVT method with well-known vision models under both ID and OOD scenarios. As shown in Table 5.1, we can see that our method fine-tuning denoted as