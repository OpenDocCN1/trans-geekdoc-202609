
## 6.2 Positional Encoding

We further evaluate whether convolutional biases introduced by the adapted projections sufficiently capture positional information, which is crucial in ECG analysis due to the diagnostic relevance of intervals between waves and heartbeats. Specifically, we investigate three positional encoding strategies:

**Absolute Sinusoidal Positional Encoding:** Predefined sinusoidal functions of varying frequencies are computed based on absolute positions and directly summed to the embeddings after the convolutional projection, explicitly embedding absolute positional information into each token.

**Absolute Learnable Positional Encoding:** A trainable embedding vector for each absolute position is learned during training and summed to the embeddings immediately after convolutional projection, enabling the model to adaptively capture position-specific patterns.

**Relative Positional Encoding:** A learnable relative position matrix, matching the attention matrix dimensions, is added directly to the attention scores before the softmax operation. This matrix encodes pairwise relative distances between token positions, allowing the model to flexibly emphasize or suppress interactions based on relative position.

Table 4. Per class F1-score comparison between positional encoding strategies.

| Abnormality | Sinusoidal APE | Learnable APE | RPE | Without PE |
|---|---|---|---|---|
| 1st AVB | 0.681 | 0.526 | 0.667 | **0.800** |
| RBBB | 0.857 | 0.844 | 0.928 | **0.923** |
| LBBB | 0.966 | 0.947 | 0.909 | **0.983** |
| SB | 0.743 | 0.643 | **0.800** | 0.778 |
| AF | 0.769 | 0.667 | 0.621 | **0.880** |
| ST | 0.873 | 0.899 | 0.853 | **0.946** |
| **Avg. F1** | 0.815 | 0.754 | 0.796 | **0.885** |

The results in Table 4 indicate that LGA-ECG achieves the highest performance without explicit positional encoding, suggesting that the convolutional projections effectively encode spatial dependencies inherent in ECG signals. While relative positional encoding improves certain classes, neither absolute nor relative positional encodings consistently enhance performance, reinforcing the effectiveness of the learned convolutional inductive biases in capturing diagnostic temporal structures. Notably, relative positional encoding (RPE) improved SB detection, likely aiding R-R interval analysis for bradycardia and rhythm abnormalities. A similar trend in the Swin-like attention, which also uses RPE, highlights its role in enhancing rhythm irregularity detection.

## 6.3 Window Size Analysis

We investigate the impact of varying the window size on the proposed LGA-ECG architecture. This hyperparameter controls both the kernel size of convolutional projections and the temporal length of local segments used to compute the local queries. By testing different window sizes, we aim to evaluate the sensitivity of the model's performance to the temporal scale at which local morphological features are captured.

![](img/f56761e6196132d5b74909d98468408f_359_0.png)

Fig. 5. F1-score comparison across different window sizes.

As shown in Fig. 5, the best performance was achieved with a window size of 64. This setting provides a trade-off between capturing fine-grained waveform details and maintaining sufficient temporal context for effective local-global feature integration.

## 7 Conclusion and Future Work

This study introduced LGA-ECG, a novel deep learning model for ECG classification that integrates local convolutional inductive biases with global self-attention mechanisms. Our approach effectively captures both fine-grained morphological features and broader temporal dependencies, leading to significant improvements over state-of-the-art methods. LGA-ECG achieved the highest F1-score among all evaluated models, demonstrating the benefits of local-global attention in medical signal analysis.

A promising and important future direction is extending LGA-ECG with self-supervised learning techniques to pretrain the model on large unlabeled ECG datasets before fine-tuning it for classification. This approach could enhance generalization and robustness, particularly for rare abnormalities with limited labeled data. Additionally, exploring domain adaptation methods may further improve model performance across diverse populations and recording settings, increasing its clinical applicability.

**Acknowledgments.** This work is partially supported by CNPq, CAPES, Fapemig, as well as projects CIA-Saúde and IAIAÃ~ÂâINCTÃãoÃâAI.

**Ethical Considerations.** While LGA-ECG demonstrates superior classification performance, its deployment in clinical settings must be approached with caution. AI-driven models should support, rather than replace, expert decision-making, ensuring that automated predictions are interpreted in the context of a professional medical evaluation. Additionally, to mitigate ethical concerns related to data privacy and patient confidentiality, all datasets used in this study are publicly available, properly anonymized, and handled following ethical guidelines. No personally identifiable information was accessible or used, ensuring compliance with data protection regulations while promoting responsible AI research in healthcare.

## References

- 1. Dai, Z., Liu, H., Le, Q.V., Tan, M.: Coatnet: marrying convolution and attention for all data sizes. In: Advances in Neural Information Processing Systems, vol. 34, pp. 3965–3977 (2021). https://proceedings.neurips.cc/paper/2021/hash/20568692db622456cc42a2e853ca21f8-Abstract.html
- 2. Dutenhefner, P.R., Rezende, T.A.V., Pappa, G.L., de Matos Paixão, G.M., Ribeiro, A.L.P., Meira, W., Jr.: Um transformador hierárquico para classificação e diagnóstico de eletrocardiograma. J. Health Inform. **16**(Especial) (2024)
- 3. Ebrahimi, Z., Loni, M., Daneshtalab, M., Gharehbaghi, A.: A review on deep learning methods for ECG arrhythmia classification. Expert Syst. Appl.: X **7**, 100033 (2020)
- 4. El-Ghaish, H., Eldele, E.: Ecgtransform: empowering adaptive ECG arrhythmia classification framework with bidirectional transformer. Biomed. Signal Process. Control **89**, 105714 (2024)
- 5. Fujita, N., Sato, A., Kawarasaki, M.: Performance study of wavelet-based ECG analysis for ST-segment detection. In: 2015 38th International Conference on Telecommunications and Signal Processing (TSP), pp. 430–434. IEEE (2015)
- 6. Hannun, A.Y., et al.: Cardiologist-level arrhythmia detection and classification in ambulatory electrocardiograms using a deep neural network. Nat. Med. **25**(1), 65–69 (2019). https://doi.org/10.1038/s41591-018-0268-3
- 7. Hu, R., Chen, J., Zhou, L.: A transformer-based deep neural network for arrhythmia detection using continuous ECG signals. Comput. Biol. Med. **144**, 105325 (2022)
- 8. Li, X., et al.: Bat: beat-aligned transformer for electrocardiogram classification. In: 2021 IEEE International Conference on Data Mining (ICDM), pp. 320–329. IEEE (2021)
- 9. Lima, E.M., et al.: Deep neural network-estimated electrocardiographic age as a mortality predictor. Nat. Commun. **12**(1), 5117 (2021)
- 10. Liu, X., Wang, H., Li, Z., Qin, L.: Deep learning in ECG diagnosis: a review. Knowl.-Based Syst. **227**, 107187 (2021)
- 11. Liu, Z., et al.: Swin transformer: hierarchical vision transformer using shifted windows. In: Proceedings of the IEEE/CVF International Conference on Computer Vision, pp. 10012–10022 (2021)
- 12. Loshchilov, I.: Decoupled weight decay regularization. arXiv preprint arXiv:1711.05101 (2017)
- 13. Loshchilov, I., Hutter, F.: SGDR: stochastic gradient descent with warm restarts. arXiv preprint arXiv:1608.03983 (2016)
- 14. Rajpurkar, P., Hannun, A., Haghpanahi, M., Bourn, C., Ng, A.: Cardiologist-level arrhythmia detection with convolutional neural networks. arXiv 2017. arXiv preprint arXiv:1707.01836 (2017)
- 15. Ribeiro, A.H., et al.: Automatic diagnosis of the 12-lead ECG using a deep neural network. Nat. Commun. **11**(1), 1–9 (2020)
- 16. Ribeiro, A.L.P., et al.: Tele-electrocardiography and bigdata: the code (clinical outcomes in digital electrocardiography) study. J. Electrocardiol. **57**, S75–S78 (2019)
- 17. Tuler, D., et al.: Leveraging cardiologists prior-knowledge and a mixture of experts model for hierarchically predicting ECG disorders. Comput. Cardiol. (2024)
- 18. Wang, J., Li, W.: Atrial fibrillation detection and ECG classification based on CNN-BiLSTM. arxiv 2020. arXiv preprint arXiv:2011.06187 (2020)
- 19. World Health Organization: Cardiovascular diseases (2024). https://www.who.int/health-topics/cardiovascular-diseases#tab=tab_1. Accessed 16 Aug 2024
- 20. Zhou, J., Wang, P., Wang, F., Liu, Q., Li, H., Jin, R.: ELSA: enhanced local self-attention for vision transformer. arXiv preprint arXiv:2112.12786 (2021)
