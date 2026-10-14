
The DL architecture is applied as a base in this research to evaluate audio recordings from depressed and normal individuals. Using the privacy protected FL system the audio waves are then split across four clients for IID settings. A vocal descriptor that is frequently used to identify depression is Mel Frequency Cepstral Coefficients (MFCC). Consequently, 162 features have been retrieved from the audio dataset using MFCC.

To see the outcomes in many scenarios with the highest performance, DL algorithms are implemented in the audio file after pre-processing information. In order to classify depressed and non-depressed participants, DL algorithms such as LSTM, CNN, and Bi-LSTM were implemented. Moreover, these algorithms are used to develop a base model and find the best algorithm to work with FL.

[Table 71.1](#ch71.xhtml#tab71_1) and [Figure 71.2](#ch71.xhtml#fig71_2) shows the results of base DL model algorithms in which using CNN, LSTM, and Bi-LSTM validation results reached 85%, 89%, and 91%, respectively. So, the Bi-LSTM algorithm outperformed other algorithms with 91% highest validation accuracy.

[Table 71.1 Training and validation results of DL models for depression detection](#ch71.xhtml#R_tab71_1)

| Parameters || Bi LSTM || CNN || LSTM |
| --- | --- | --- | --- |
| Accuracy || 99.08333 || 99.66667 || 99.33333 |
| Validation accuracy || 91 || 85 || 89 |
| Precision || 99.08333 || 99.66667 || 99.33333 |
| Validation precision || 91 || 85 || 89 |
| Recall || 99.08333 || 99.66667 || 99.33333 |
| Validation recall || 91 || 85 || 89 |
| Loss || 0.032376 || 0.012926 || 0.015737 |
| Validation loss || 0.349078 || 0.439554 || 0.347897 |

![Figure 71.2 Training and validation accuracy and loss results for depression detection using Bi-LSTM, CNN and LSTM algorithms](images/fig71_2_C.jpg)

[Figure 71.2 Training and validation accuracy and loss results for depression detection using Bi-LSTM, CNN and LSTM algorithms](#ch71.xhtml#R_fig71_2)

The FL method and Bi-LSTM method are combined to analyze the IID data for the purpose of diagnosing depressed patients while maintaining their privacy. For the 4 clients, the training and validation sets are divided as IID data. Further, all client data is tested at the server site to aggregate all the client models. Finally, the server developed model is updated at all clients’ sites.

According to [Table 71.2](#ch71.xhtml#tab71_2) and [Figure 71.3](#ch71.xhtml#fig71_3), [Figure 71.4](#ch71.xhtml#fig71_4) and [Figure 71.5](#ch71.xhtml#fig71_5), privacy protected FL model achieved 94.25% accuracy for training IID data over the client site. Further, validation accuracy for IID data at the client site is slightly lower at 85.66% and validation accuracy for IID data is 86.66% at the server site. Although the FL model has a little less accuracy than the DL model for privacy protected systems it’s really needed. Because hospital’s data is private and many patients don’t want to disclose their information so, FL is the best way to train a secure diagnosis system.

[Table 71.2 Training and validation results of FL models for depression detection using IID data](#ch71.xhtml#R_tab71_2)

| Parameters || Client IID training || Client IID validation || Server IID validation |
| --- | --- | --- | --- |
| Accuracy || 94.25 || 85.66667 || 86.66667 |
| Precision || 94.25 || 85.66667 || 86.66667 |
| Recall || 94.25 || 85.66667 || 86.66667 |
| Loss || 0.160396 || 0.356732 || 0.32788 |

![Figure 71.3 Client training results for depression detection using IID data](images/fig71_3_C.jpg)

[Figure 71.3 Client training results for depression detection using IID data](#ch71.xhtml#R_fig71_3)

![Figure 71.4 Client validation results for depression detection using IID data](images/fig71_4_C.jpg)

[Figure 71.4 Client validation results for depression detection using IID data](#ch71.xhtml#R_fig71_4)

![Figure 71.5 Server validation results for depression detection using IID data](images/fig71_5_C.jpg)

[Figure 71.5 Server validation results for depression detection using IID data](#ch71.xhtml#R_fig71_5)

In this article, we introduce a system for identifying and categorizing depressed and healthy individuals from audio data. The creation of an automated diagnostic system will aid clinicians in providing a fast diagnosis of depression. So, firstly we developed a base DL model using CNN, LSTM, and Bi-LSTM algorithms in which Bi-LSTM outperformed other algorithms with the highest 91% validation accuracy. After that, an automated privacy-protected FL-based depression detection framework is proposed using an audio dataset. Therefore, the suggested FL framework obtained accuracy for IID data of 94.25% during training 85.66% during validation on the client site, and 86.66% validation accuracy on the server site. Thus, in the future, this method could be applied to diverse datasets to check its reliability and robustness.

## References

*   [Adarsh, V., P. Arun Kumar, V. Lavanya, and G. R. Gangadharan](#ch71.xhtml#R_ref71_1). (2023). Fair and explainable depression detection in social media. Information Processing & Management, 60(1): 103168 [https://doi.org/10.1016/j.ipm.2022.103168](https://dx.doi.org/10.1016/j.ipm.2022.103168).

*   [Cai, Hanshu, Yiwen Gao, Shuting Sun, Na Li, Fuze Tian, Han Xiao, Jianxiu Li et al.](#ch71.xhtml#R_ref71_2) (2020). Modma dataset: a multi-modal open dataset for mental-disorder analysis. arXiv preprint arXiv:2002.09283 [https://doi.org/10.48550/arXiv.2002.09283](https://dx.doi.org/10.48550/arXiv.2002.09283).

*   [Cai, Hanshu, Jiashuo Han, Yunfei Chen, Xiaocong Sha, Ziyang Wang, Bin Hu, Jing Yang et al.](#ch71.xhtml#R_ref71_3) (2018). A pervasive approach to EEG-based depression detection. Complexity 2018: 1–13.

*   [Cui, Y., Li, Z., Liu, L., Zhang, J., and Liu, J.](#ch71.xhtml#R_ref71_4) (2022). Privacy-preserving speech-based depression diagnosis via federated learning. Proc. Ann. Int. Conf. IEEE Engg. Med. Biol. Ssc. EMBS, 1371–1374. Institute of Electrical and Electronics Engineers Inc. [https://doi.org/10.1109/EMBC48229.2022.9871861](https://dx.doi.org/10.1109/EMBC48229.2022.9871861).

*   [Elbeltagi, A., Aslam, M. R., Malik, A., Mehdinejadiani, B., Srivastava, A., Bhatia, A. S., and Deng, J.](#ch71.xhtml#R_ref71_5) (2020). The impact of climate changes on the water footprint of wheat and maize production in the Nile delta, Egypt. Sci. Total Environ., 743, 140770. [https://doi.org/10.1016/j.scitotenv.2020.140770](https://doi.org/10.1016/j.scitotenv.2020.140770).

*   [Fan, Z., Su, J., Gao, K., Peng, L., Qin, J., Shen, H., Hu, D., and Zeng, L.-L.](#ch71.xhtml#R_ref71_6) (2021). Federated learning on structural brain MRI scans for the diagnostic classification of major depression. Biol. Psych., 89(9), S183. [www.sobp.org/journal](https://dx.doi.org/www.sobp.org/journal).

*   [Gupta, Chetna, and Vikas Khullar](#ch71.xhtml#R_ref71_7). (2022). Contemporary Intelligent Technologies for Electroencephalogram-Based Brain Computer Interface. In 2022 10th International Conference on Reliability, Infocom Technologies and Optimization (Trends and Future Directions) (ICRITO), 1–6. IEEE.

*   [Khullar, Vikas, Raj Gaurang Tiwari, Ambuj Kumar Agarwal, and Soumi Dutta](#ch71.xhtml#R_ref71_8). (2022). Physiological signals based anxiety detection using ensemble machine learning. In Cyber Intelligence and Information Retrieval: Proceedings of CIIR 2021, 597–608. Springer Singapore.

*   [Khullar, Vikas, and Harjit Pal Singh](#ch71.xhtml#R_ref71_9). (2022). Privacy protected internet of unmanned aerial vehicles for disastrous site identification. Concurrency and computation: practice and experience. 34(19): e7040 [https://doi.org/10.1002/cpe.7040](https://doi.org/10.1002/cpe.7040).
