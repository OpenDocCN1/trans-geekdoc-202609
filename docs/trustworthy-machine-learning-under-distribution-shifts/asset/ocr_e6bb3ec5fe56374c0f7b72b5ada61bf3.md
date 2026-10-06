# TABLE 5.4. Classification accuracy (%) of baseline CLIP models and our method with MMICL [280] and Otter [250] as the VLMs on 4 subsets of DomainBase datasets, including VLCS, PACS, OfficeHome, and DomainNet. We compare the performance of our method and the fine-tuned models supervised by our method with the baseline models, ViT-L from CLIP [225]. Fine-tuning with both MMICL and Otter improves the classification accuracy.

| LLM | Datasets | VLCS | | | | PACS | | | |
|---|---|---|---|---|---|---|---|---||
| | Method | 0 | 1 | 2 | 3 | 0 | 1 | 2 | 3 |
| None | CLIP | 74.9 | 83.5 | 80.3 | 74.5 | 97.8 | 97.4 | 97.5 | 99.4 |
| MMIC | MVT | 83.8 | 89.0 | 87.2 | 80.3 | 97.6 | 97.5 | 98.0 | 99.4 |
| | +FT | 84.2 | 89.8 | 87.9 | 82.5 | 98.0 | 98.0 | 98.8 | 99.8 |
| Otter | MVT | 67.5 | 77.4 | 73.7 | 66.6 | 97.0 | 96.3 | 96.5 | 99.0 |
| | +FT | 76.8 | 87.7 | 82.3 | 77.4 | 98.0 | 97.7 | 98.0 | 99.8 |

| LLM | Datasets | OfficeHome | | | | | DomainNet | | | | Avg |
|---|---|---|---|---|---|---|---|---|---||
| | Method | 0 | 1 | 2 | 3 | 0 | 1 | 2 | 3 | Avg |
| None | CLIP | 87.7 | 92.7 | 85.7 | 86.5 | 61.1 | 60.2 | 78.4 | 51.1 | 80.6 |
| MMIC | MVT | 87.7 | 93.4 | 89.0 | 88.5 | 61.3 | 62.1 | 60.4 | 78.7 | 53.4 | 82.8 |
| | +FT | 90.9 | 95.0 | 90.9 | 90.8 | 62.5 | 63.8 | 62.4 | 80.1 | 54.0 | 82.4 |
| Otter | MVT | 85.6 | 89.9 | 83.6 | 83.3 | 58.6 | 56.3 | 74.1 | 46.5 | 77.0 |
| | +FT | 88.7 | 93.4 | 87.7 | 87.1 | 62.0 | 63.0 | 61.3 | 79.7 | 53.4 | 82.0 |

“FT” achieves better in most settings. Specifically, on “IN-V”, our method with fine-tuning can significantly boost CLIP and Otter for 17% and 6%, respectively. Moreover, on “IN-A”, our method achieves 4.3% and 2.8% performance improvement over the second-best method on both ViT-L and ViT-g backbone, respectively. We can observe that even without fine-tuning, the prediction accuracy of MMIC denoted by “MVT” can still surpass all baselines on many scenarios, which denotes the strong performance enhancement of our MVT fine-tuning on vision models. Note that we did not provide fine-tuning on WildCam because predictions are uncertain. Though MVT can still achieve the best result, the vision encoders can be misled by erroneous decisions during the fine-tuning process.

Furthermore, we consider domain shift by leveraging DomainBase datasets. Specifically, for each dataset, we leave out one dataset as a test and fine-tune on rest remains by.