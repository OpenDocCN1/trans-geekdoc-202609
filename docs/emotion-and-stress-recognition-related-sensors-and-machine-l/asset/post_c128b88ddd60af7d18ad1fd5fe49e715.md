
# Table 7. Comparison with models featuring a DNN algorithm.

| | [12] | [13] | Proposed |
|---|---|---|---|
| Window | 10 s | - | 10 s |
| Input | Raw ECG | Raw HR and SC | Raw ECG |
| Accuracy AUC | 87.39%, 73.96% | 0.918 | 90.19%, 0.938 |

We propose a novel end-to-end architecture that uses raw ECG signals for stress detection and validated its performance with two data sets. We believe that our model could replace the conventional machine learning-based methods in several ways.

First, in terms of simplicity, our model has an advantage over conventional methods, which require few additional steps, such as preprocessing, feature selection, and feature extraction, before classification. As our model was built with an end-to-end architecture, it does not necessarily require such additional steps. The end-to-end architecture enables the detection of stress by automatically extracting features without feature selection. We observed that the successive deep layers extract distinguishable features, as shown in Figure 4.

In the same regard, our model shows better performance than conventional methods. The methods that use HR parameters depend highly on the quality of R-peak detection. Considering stress management in daily life, records in real-world environments may require additional steps, as shown in [33]. In addition to the limitations of the conventional methods [9–11], as shown in Figure 5 and Table 5. With raw ECG signals, conventional machine learning methods do not show acceptable performance in detecting stress, can rarely be trained with non-linear inputs (i.e, raw signals). Whereas the HR parameters require at least a short-term (5 m) or long-window (24 h) to properly reflect the stress response, our model used much shorter windows (10 s, 30 s, and 60 s). As it takes an average of 2.4 minutes to detect stress state inputs of raw ECGs, it is possible to apply the proposed model in real-world to detect stress in real-life.

Despite the advantages above, the performance of the DNN depends highly on the size of the data set used to train a neural network. To investigate the effect of data set size on stress detection, we compared three types of models with different strategies. As expected, the model Type I, which was trained using a larger data set, showed better performance than the model Type II, trained using a smaller data set. There was a size difference of more than four times between the Type II and Type III training. Type III, which used the pretrained model, showed an improvement over Type II, which although the size of the arithmetic data set might not be large enough to train the neural network, it is possible to achieve a fine-tuned model, based on pretraining with a larger data set. However, it could not reach the performance of the Type-I model, trained using a larger data set. While other domains of data, such as speech or image, sufficient amount of physiological data may not be easily acquired or obtained, our approach can be utilized to train a DNN with a smaller data set, based on the pretrained model.

In this study, we used two data sets (i.e. crying and mental arithmetic) for model development and validation. The ambulatory and laboratory environments for model development and validation. Mental arithmetic is one of the representative test paradigms used to assess stress. It was proved, by two questionnaires (self-assessment manif and stress thermometer), that mental arithmetic induced a level of the participants.

However, to develop a stress management method for daily life, there is a need to validate the method out-of-laboratory, as well. Thus, we also chose the driving data set to assess stress out-of-laboratory. Although these data sets cannot represent all of the stress situations that can occur in everyday life, such as workload stress, stress anxiety, and so, we demonstrated an end-to-end architecture to detect mental stress for both in- and out-of-laboratory environments.

However, there were limitations in this study. Although the two sensors used in the two data sets were individual, in view of generalization, the model needs to be validated by using ECG from different sensors, including other electrode configurations. We have other data sets, which were different from those using during training, to allow the model to detect specific type of stress sensor density. Even through bias or dependency remains, transfer learning from one data set to other may provide a solution to address the limited applicability in real-world scenarios. As mentioned above, ECGs during daily activities are necessary for considering other stress events, such as workload or anxiety, and we will apply it to multi-class problems or continuous level recognition. Additionally, we will investigate how physiological signals to train a neural network to overcome the limitations of the data set.

**Authors Contributions:** Contextualization; H-M-C, S-Y-D, and I-Y; data curation; S-Y-D, H.P, and H-M-C; funding; investigation; H.P. and H-M-C; methodology; H-M-C and S-Y-D; supervision; H-M-C; supervision; S-Y-D and I-Y; writing-original draft; H-M-C; writing-review and editing; S-Y-D, and I-Y.

**Funding:** This research was supported in part by the Bio Medical Technology Development Program of the National Health Technology & R&D Project through the Korea Health Technology Development Institute (KHID), a grant of the Korea Health Technology Development Institute (KHID),), funded by the Ministry of Health & Welfare, Republic of Korea (grant number: HI14C347); and the National Research Council of Science & Technology (NST) (No. Cap-18-01).

**Conflicts of Interest:** The authors declare no conflict of interest.

# Appendix A
*Table A1.* More detailed information about the proposed architecture. "conv" denotes "conv filter channel)". Similar to "conv", "maxpool16" refers to max pooling with 16 lengths of the filter.

| Order | Operation | Output | Stride | # Parameters |
|---|---|---|---|---|
| 0 | input | (?, 2560, 1) | | |
| 1-1 | conv16-8 | (?, 2560, 8) | 1 | |
| 1-2 | conv16-8 | (?, 1280, 8) | 2 | 1024 |
| 1-2 | maxpool16 | (?, 1280, 8) | 2 | - |
| 1-3 | concatenating | (?, 1280, 16) | | |
| 1-4 | batch normalization | (?, 1280, 16) | | 32 |
| 1-5 | activation & dropout | (?, 1280, 16) | 2 | - |
| 2-1 | conv16-8 | (?, 1280, 8) | 1 | 2048 |
| 2-2 | conv16-8 | (?, 640, 8) | 2 | 1024 |
| 2-2 | maxpool16 | (?, 640, 8) | 2 | - |
| 2-3 | concatenating | (?, 640, 16) | | |
| 2-4 | batch normalization | (?, 640, 16) | | 32 |
| 2-5 | activation & dropout | (?, 640, 16) | 2 | - |
| 3-1 | conv16-16 | (?, 320, 16) | 1 | 4096 |
| 3-2 | conv16-16 | (?, 320, 32) | 2 | 4096 |
| 3-2 | maxpool16 | (?, 320, 32) | 2 | - |
| 3-3 | concatenating | (?, 320, 32) | | |
| 3-4 | batch normalization | (?, 320, 32) | | 64 |
| 3-5 | activation & dropout | (?, 320, 32) | 2 | - |
| 4-1 | conv16-16 | (?, 320, 16) | 1 | 8192 |
| 4-2 | conv16-16 | (?, 160, 16) | 2 | 4096 |
| 4-2 | maxpool16 | (?, 160, 16) | 2 | - |
| 4-3 | concatenating | (?, 160, 32) | | |
| 4-4 | batch normalization | (?, 160, 32) | | 64 |
| 4-5 | activation & dropout | (?, 160, 32) | 2 | - |
| 5-1 | conv16-32 | (?, 80, 32) | 1 | 16384 |
| 5-2 | conv16-32 | (?, 80, 64) | 2 | 16384 |
| 5-2 | maxpool16 | (?, 80, 64) | 2 | - |
| 5-3 | concatenating | (?, 80, 64) | | |
| 5-4 | batch normalization | (?, 80, 64) | | 128 |
| 5-5 | activation & dropout | (?, 80, 64) | 2 | - |
| 6-1 | conv16-32 | (?, 40, 32) | 1 | 32768 |
| 6-2 | conv16-32 | (?, 40, 64) | 2 | 16384 |
| 6-2 | maxpool16 | (?, 40, 64) | 2 | - |
| 6-3 | concatenating | (?, 40, 64) | | |
| 6-4 | batch normalization | (?, 40, 64) | | 128 |
| 6-5 | activation & dropout | (?, 40, 64) | 2 | - |
| 7-1 | conv16-64 | (?, 20, 64) | 1 | 65536 |
| 7-2 | conv16-64 | (?, 20, 64) | 2 | 65536 |
| 7-2 | maxpool16 | (?, 20, 64) | 2 | - |
| 7-3 | concatenating | (?, 20, 128) | | |
| 7-4 | batch normalization | (?, 20, 128) | | 256 |
| 7-5 | activation & dropout | (?, 20, 128) | 2 | - |
| 8-1 | conv16-64 | (?, 10, 64) | 1 | 131072 |
| 8-2 | conv16-64 | (?, 10, 128) | 2 | 65536 |
| 8-2 | maxpool16 | (?, 10, 128) | 2 | - |
| 8-3 | concatenating | (?, 10, 128) | | | |
| 8-4 | batch normalization | (?, 10, 128) | 2 | 256 |
| 8-5 | activation & dropout | (?, 10, 128) | 2 | - |
| Total | | | | 435K |
