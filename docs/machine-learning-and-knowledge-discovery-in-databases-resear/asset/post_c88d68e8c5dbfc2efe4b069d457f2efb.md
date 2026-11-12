
[16]. CODE contains over 2 million ECGs from Minas Gerais, Brazil, annotated by cardiologists for six cardiac abnormalities: first-degree atrioventricular block (1st AVB), right bundle branch block (RBBB), left bundle branch block (LBBB), sinus bradycardia (SB), atrial fibrillation (AF), and sinus tachycardia (ST). These conditions indicate an increased risk for cardiovascular events, including stroke, heart failure, and sudden death, and require targeted clinical interventions. CODE-15 comprises 345,779 exams from 233,770 patients and has been widely adopted in ECG research, serving as a benchmark dataset for developing and evaluating deep learning models [15] [17].

We evaluated our model using the publicly available CODE-TEST dataset, also collected by the Telehealth Network of Minas Gerais (TNM). CODE-TEST comprises 827 ECGs labeled by consensus among two or three cardiologists, covering the same six cardiac abnormalities. The high-quality, expert-consensus labels provide a robust benchmark for performance assessment.

For developing and validating the LGA-ECG model, the dataset is divided into four subsets by patient IDs: 90% of CODE-15 is used as the training set to train the model, while 5% of CODE-15 serves as the validation set for early stopping. An additional 5% of CODE-15 is designated as the development set, which is utilized for hyperparameter tuning and ablation studies. Finally, the entire CODE-TEST dataset is used as the test set to evaluate the final model performance against baseline methods.

## 4.2 Implementation Details and Benchmarks

For comparison, we assessed LGA-ECG against a suite of baseline models spanning diverse architectural families, including traditional CNN and transformer-based architectures. This selection ensured a rigorous and comprehensive evaluation across distinct modeling paradigms. The baselines were implemented using their original authors' codebases, with training settings configured according to their recommendations. All models were trained on the same Training Set and evaluated on the Test Set to ensure consistent comparisons. We employed standard classification metrics to evaluate the models: accuracy, F1-score, precision, and recall. These metrics were computed for each cardiac condition individually to provide a detailed understanding of model performance across different diseases, as well as averaged (macro).

The training process utilized the AdamW optimizer [12] and employed a cosine annealing learning rate schedule [13]. The initial learning rate was set to 0.0001 and was decreased cosine-wise to 0.00001 throughout the training. Additionally, early stopping was implemented, which terminates training if the validation error does not decrease for seven consecutive epochs. The training was conducted in parallel using 4 NVIDIA V100 GPUs.

## 5 Results

In this section, we analyze our model by comparing its performance to state-of-the-art models in ECG abnormality classification.

### Table 1. Average performance of LGA-ECG when compared to other SOTA methods.

| Metrics | ResNet-1 | ResNet-2 | ECG-Transform | BAT | ECG-DETR | HiT | LGA-ECG |
|---|---|---|---|---|---|---|---|
| Accuracy | 0.991 | 0.989 | 0.981 | 0.991 | 0.9842 | 0.991 | **0.994** |
| Precision | 0.875 | 0.908 | 0.711 | **0.918** | 0.7768 | 0.0909 | 0.907 |
| Recall | 0.778 | 0.743 | 0.687 | 0.799 | 0.6614 | 0.798 | **0.872** |
| F1-Score | 0.814 | 0.811 | 0.677 | 0.848 | 0.699 | 0.841 | **0.885** |

We first compare our model, LGA-ECG, with state-of-the-art methods for classifying six ECG abnormalities: AVB, RBBB, LBBB, SB, AF, and ST. The evaluated models include ResNet-1 [15], ResNet-2 [6], BAT [8], ECG-DETR [7], and HiT [2]. Due to class imbalance, accuracy may be inflated; thus, recall, precision, and particularly the F1-score will be our primary comparison metrics.

Analyzing recall first, LGA-ECG achieves 0.862, surpassing BAT (0.799) and becoming the first to exceed the 0.8 threshold. This marks a significant improvement in identifying positive cases, which is particularly critical in medical applications, where missing a diagnosis due to low recall (high false negatives) can lead to delayed treatments and severe consequences for patients. However, despite this substantial increase in recall, our model maintains a competitive precision of 0.907 – only slightly lower than BAT's 0.918. This demonstrates that the boost in recall did not come at the cost of a drastic drop in precision, ensuring a balanced performance that enhances overall reliability. This balance underscores its robustness for practical deployment in high-stakes scenarios.

### Table 2. Per class F1-score of LGA-ECG and baseline methods in the test set.

| Abnormality | ResNet-1 | ResNet-2 | ECG-Transform | BAT | ECG-DETR | HiT | LGA-ECG |
|---|---|---|---|---|---|---|---|
| 1st AVB | 0.661 | 0.719 | 0.489 | 0.689 | 0.631 | 0.682 | **0.8** |
| RBBB | **0.924** | 0.890 | 0.909 | 0.922 | 0.747 | 0.886 | 0.923 |
| LBBB | 0.927 | 0.843 | 0.886 | 0.945 | 0.826 | 0.909 | **0.983** |
| SB | 0.767 | 0.821 | 0.535 | **0.836** | 0.588 | 0.824 | 0.778 |
| AF | 0.703 | 0.758 | 0.478 | 0.818 | 0.563 | 0.833 | **0.880** |
| ST | 0.897 | 0.833 | 0.763 | 0.870 | 0.838 | 0.914 | **0.946** |
| Avg. F1 | 0.814 | 0.811 | 0.677 | 0.848 | 0.699 | 0.841 | **0.885** |

Beyond recall and precision, F1-score provides a comprehensive measure of performance by balancing both metrics. LGA-ECG achieves a new record F1-score of 0.885, surpassing BAT, which reached 0.848, ensuring robust classification across all ECG abnormalities. Despite the class imbalance, our model also achieves a higher accuracy, scoring 0.994 compared to 0.991 from the closest competitor (BAT). By outperforming all baseline methods in all metrics, our approach demonstrates superior overall performance in distinguishing abnormal ECG patterns. All comparisons can be seen in Table 1.

Now, focusing solely on the F1-score, we can directly compare performance across different abnormalities. As shown in Table 2, LGA-ECG outperforms the baselines in four categories: ST, LBBB, AF, and 1st AVB. For RBBB, although the F1-score is slightly lower, it remains virtually equivalent to that of ResNet-1. The only class in which our model underperforms is SB. We hypothesize that this occurs due to the model's difficulty in accurately detecting longer intervals between consecutive R peaks (the prominent upward deflections in the ECG that indicate ventricular contractions). Further evaluation is necessary to confirm this limitation and guide appropriate improvements.

![](img/f56761e6196132d5b74909d98468408f_356_0.png)

### Fig. 4. Comparison of the average Precision, Recall, and F1 Score between the proposed LGA-ECG model and human performance.

The CODE-TEST dataset includes labels provided by cardiologists at different levels of training: (i) 4th-year cardiology residents (cardio.), (ii) 3rd-year emergency residents (emerg.), and (iii) 5th-year medical students (stud.). The reference labels used for calculating the evaluation metrics were determined by consensus among three experienced specialist cardiologists, who were excluded from the analysis. Using this expert consensus as the ground truth, we compared the labels assigned by professionals at different training levels with the predictions generated by the proposed LGA-ECG model. The results, presented in Fig. 4, shows that the model outperformed all groups of cardiologists across all key metrics, demonstrating superior performance compared to individuals with varying levels of cardiology expertise.

## 6 Ablations

To assess the effectiveness of our proposed local-global attention mechanism, we perform a series of ablation studies to isolate its contributions and better understand its impact on ECG feature extraction.

### 6.1 Alternative Attention Mechanisms

First, we compare the proposed LGA against alternative attention strategies. Our goal is to evaluate how different query, key, and value configurations influence the model's ability to capture fine-grained ECG morphology and global contextual dependencies.

- **ViT-like:** We begin by examining a standard ViT-like approach, which applies global self-attention across the entire sequence using linear projections for queries, keys, and values. While this method captures the global context effectively, it lacks local inductive biases.

- **Swin-like:** Next, we compare our method with a local attention mechanism inspired by Swin Transformer [11], where self-attention is restricted to non-overlapping windows. This approach captures local features while progressively integrating global context through stacked local attention and inter-block pooling.

- **Global Q, K, V:** We also analyze a global attention variant, which follows the standard attention mechanism but replaces linear projections with convolutional and average pooling layers. In this configuration, queries are computed in the same manner as keys and values, ensuring that all positions attend to each other globally. Although this setup preserves global context awareness, it may fail to efficiently encode localized waveform structures.

- **Local Q, K, V:** Finally, we examine a fully localized variant, where the query Q is the mean of the embeddings within a window, while the keys K and values V correspond only to the embeddings of that window, without global context. We extract overlapping windows, ensuring that each window is condensed into a single embedding after the attention operation. This progressively reduces the data by half at each stage, establishing a hierarchical processing framework.

### Table 3. Per class F1-score comparison between different attention mechanisms.

| Abnormality | ViT-like | Swin-like | Global Q, K, V | Local Q, K, V | LGA-ECG |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1st AVB | 0.653 | 0.682 | 0.809 | 0.782 | **0.800** |
| RBBB | 0.862 | 0.886 | 0.925 | **0.955** | 0.923 |
| LBBB | 0.875 | 0.909 | 0.909 | 0.982 | **0.983** |
| SB | 0.768 | **0.824** | 0.733 | 0.750 | 0.778 |
| AF | 0.792 | 0.833 | 0.833 | 0.782 | **0.880** |
| ST | 0.887 | 0.914 | 0.870 | 0.885 | **0.946** |
| **Avg. F1** | 0.806 | 0.841 | 0.847 | 0.856 | **0.885** |

The results in Table 3 show that LGA-ECG achieves the highest F1-score (0.885), outperforming all alternative attention mechanisms. By integrating local convolutional inductive biases with global context, LGA-ECG surpasses both fully global (ViT-like, global QKV) and fully local (Swin-like, local QKV) approaches, demonstrating superior feature extraction for ECG classification.
