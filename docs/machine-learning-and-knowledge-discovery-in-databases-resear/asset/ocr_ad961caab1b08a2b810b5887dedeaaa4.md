# ## 5.2 Detection Effectiveness and Efficiency

To answer RQ1, we conducted extensive experiments under various transfer settings and summarize the results in Tables 1 and 2.

**Compared to Supervised Methods:** Generally, *BotTrans* consistently outperforms and achieves significant performance improvements of around 3% in both F1 and AUC. Remarkably, in the Low-*m* transfer tasks with less similar source domains, *BotTrans* maintains superior performance, unlike other baselines like AdaGCN or *M³*SDA which exhibit a performance drop of up to 8% from High-*m* to Low-*m* tasks. This demonstrates *BotTrans*'s robust capability in transferring knowledge even under challenging conditions. Furthermore, key observations from Table 1 include: 1) *BotTrans* significantly surpasses single-source GDA models and multi-source graph transfer learning models, highlighting the effectiveness of our approach in alleviating source network heterophily and embedding over-smoothing, and selective knowledge-transfer strategy when leveraging multiple source domains, 2) Graph OOD models typically underperform in multi-source domain tasks. This limitation is likely attributed to the absence of specific knowledge of target domain, which hinders the model's ability to bridge the distribution gap between source and target domains, and 3) CDAD models underperform in social bot detection, likely due to their inability to adequately transfer bot-related knowledge and limited generalizability to the social bot detection task.

**Table 1.** Multi-source transfer results (second best underlined). For 2 or 4 sources, we report the averaged F1-score over all 20 tasks and the High/Low-*m* F1-score over 10 corresponding tasks. For 9 sources, we report the averaged F1-score over all 10 tasks. We also report AUC-ROC scores averaged over all tasks.

| | 2 sources | | | | 4 sources | | | | 9 sources |
|---|---|---|---|---|---|---|---|---|---|---|
| | F1-avg | High-mF1-avg | Low-mF1-avg | AUC-avg | F1-avg | High-mF1-avg | Low-mF1-avg | AUC-avg | F1-avg | AUC-avg |
| GCN | 0.6463 | 0.6904 | 0.6021 | 0.7047 | 0.6738 | 0.6991 | 0.6485 | 0.7245 | 0.7054 | 0.7544 |
| GraphSAGE | 0.6486 | 0.7116 | 0.5856 | 0.7187 | 0.6989 | 0.7156 | 0.6853 | 0.7552 | 0.7098 | 0.7802 |
| EERM | 0.6308 | 0.6686 | 0.5931 | 0.6842 | 0.6464 | 0.6525 | 0.6403 | 0.7164 | 0.6767 | 0.7482 |
| ISGIB | 0.6521 | 0.6880 | 0.6162 | 0.7265 | 0.6786 | 0.6933 | 0.6640 | 0.7523 | 0.688 | 0.7628 |
| AdaGCN | 0.7206 | <u>0.7682</u> | <u>0.6821</u> | 0.7501 | <u>0.7536</u> | <u>0.7644</u> | 0.7246 | 0.7748 | <u>0.7768</u> | <u>0.8246</u> |
| Grade | 0.7280 | 0.7258 | | 0.7202 | 0.7417 | 0.7338 | 0.7460 | | 0.7224 | 0.7382 | 0.6544 | 0.7563 |
| UDAGCN | 0.7090 | 0.7344 | 0.6836 | <u>0.7806</u> | 0.7481 | 0.7579 | <u>0.7483</u> | <u>0.7892</u> | 0.762 | 0.824 |
| Commander | 0.6501 | 0.6611 | 0.6411 | 0.7060 | 0.6546 | 0.6894 | 0.6411 | 0.7370 | 0.6530 | 0.7543 |
| ACT | 0.4148 | 0.4100 | 0.4197 | 0.4794 | 0.4270 | 0.4218 | 0.4313 | 0.4908 | 0.3960 | 0.4761 |
| M³SDA | 0.7014 | 0.7415 | 0.6613 | 0.7519 | 0.7098 | 0.7227 | 0.6993 | 0.7409 | 0.7014 | 0.7309 |
| MSDS | 0.6579 | 0.6606 | 0.6552 | 0.6713 | 0.6572 | 0.6650 | 0.6494 | 0.6793 | 0.6732 | 0.7043 |
| NESTL | 0.5427 | 0.6058 | 0.4796 | 0.7261 | 0.5502 | 0.6188 | 0.4941 | 0.7261 | 0.5283 | 0.7262 |
| BotTrans | **0.7569** | **0.7819** | **0.7319** | **0.7983** | **0.7851** | **0.7926** | **0.7789** | **0.8260** | **0.8000** | **0.8524** |

**Compared to Unsupervised Methods:** we compare model performance on each domain *d* with *BotTrans*'s result, which is given by the best result among all multi-source adaptation tasks with *d_ as target domain. The results in Table 2 demonstrate that even the best baseline DGI+IF is significantly inferior to *BotTrans*, with a performance decrease of 18.34% ~ 36.82%. These results prove the necessity of knowledge transfer for detecting social bots.