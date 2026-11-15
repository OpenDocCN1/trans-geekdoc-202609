
For the decoder model, BERT was selected due to its proven effectiveness across various natural language processing (NLP) tasks [34,40,41]. However, we diverge from the standard configuration by employing only three layers with a hidden size of 1024, rather than the original 12 layers. Moreover, our investigation includes the analysis of two distinct decoders: one word-based, with a vocabulary of approximately 9.8k words, and another subword-based, featuring a vocabulary of 30k subwords. The integration of the vision model with the decoder model is facilitated through cross-attention layers, enabling the introduction of visual features extracted from the radiograph into the decoder. This integration allows for the autoregressive generation of reports.

Following this approach, the proposed VED models for chest RRG analysis are SwinB+BERT9k, SwinB+BERT30k, SwinS+BERT9k, and SwinS+BERT30k.

## 2.2. Training Workflows

In radiological contexts, multiple images (such as anterior–posterior and lateral views) are commonly generated per patient study. We employ a multi-image approach to address this, restricting it to three images per study. This involves concatenating features extracted by the Swin encoder for each image and processing them in the decoder. Furthermore, we apply random transformations—including translation, scaling, rotation, and adjustments to brightness and contrast—to augment training images.

Our training process comprises two stages, as illustrated in Figure 1. In the initial stage, the NLL loss function is employed, utilizing teacher forcing to train the model based on the generated hypothesis and the reference report. This stage typically encompasses approximately twelve training epochs. Subsequently, in the second stage, RL is introduced using the self-critical sequence training (SCST) algorithm [42]. SCST performs two forward passes of the VED: greedy decoding and beam-search multinomial sampling (sampling decoding). The first pass involves inference through greedy decoding to obtain the report Yg without calculating gradients. Meanwhile, the second pass employs sampling decoding, calculating gradients to obtain the sampling report Ys.

RL aims to optimize specific metrics by using them as rewards. In our approach, we propose utilizing two metrics: BERTScore [13] and RadGraph [14]. BERTScore effectively improves grammar and semantics within models, while F1RGER aids the model in prioritizing pathology-related entities and relationships.

After obtaining the reports Yg and Ys, we must calculate a loss for each metric to optimize (Lossmetric). This Lossmetric is subsequently used to compute a weighted sum to obtain the final LossRL and update the model weights. Equation (1) outlines the process to derive the Lossmetric, where the metric rewards are computed for Ys and Yg using the reference report Yref. These rewards are then subtracted and multiplied by the logarithm of the probabilities calculated during the generation of the Ys report.

```
Loss_metric(Y_s, Y_g, Y_ref) = -(r_metric(Y_s, Y_ref) - r_metric(Y_g, Y_ref)) log(Pr(Y_s)) (1)
```

Each Lossmetric contributes as a distinct weighted term to the final RL loss, as presented in Equation (2). To obtain the LossRL for updating the model weights, LossBERTScore, LossF1RGER, and the same loss utilized in the initial training stage, the LossNLL, are summed. In our experiments, we set α = β = 0.495 and γ = 0.010 as the weighting factors.

```
Loss_RL = αLoss_BERTScore + βLoss_F1RGER + γLoss_NLL (2)
```

## 2.3. Text Augmentation

Data augmentation (DA) is the most prevalent technique for addressing machine learning problems with limited data. This approach significantly contributes to enhanced generalization and improved data utilization. However, regarding RRG, the focus has primarily been on augmenting input images. To the best of our knowledge, no prior approach has investigated the impact of augmenting radiology reports, a technique known as text augmentation (TA). In chest RRG, reports are often drafted by different individuals in diverse manners, lacking specific templates, which results in significant variability inherent to natural language. Presently, state-of-the-art RRG algorithms encounter this data scarcity issue, often generating highly repetitive and monotonous reports.

In this study, we introduce a TA technique designed to enhance the quality and diversity of generated reports. Our TA approach involves splitting the reference report into phrases, considering the typical structure of reports with multiple sentences. These phrases are then randomly reorganized to create new reports while maintaining the original diagnosis, as depicted in Figure 1. This method mitigates overfitting concerns and promotes a more targeted learning of the mentioned pathologies. Furthermore, our TA significantly improves the quality, factual accuracy, and comprehensiveness of the generated reports, as demonstrated subsequently.

![](img/46da2aabc253ed283db238584dfa3d21_105_0.png)

Figure 1. Our training workflow using RL and TA to enhance report quality. In the initial stage, training with NLL employs teacher forcing. Subsequently, during RL training, the SCST algorithm computes rewards utilizing two different reports from two distinct decoding strategies: greedy search and beam-search multinomial sampling. Inference on validation and test sets is conducted using beam search in both stages.

## 2.4. Datasets and Metrics

To evaluate the competitiveness of our models, we employed two publicly available datasets: MIMIC-CXR [43] and Open-i [44]. Due to the relatively small size of the Open-i dataset, containing 3.3k reports, it was exclusively utilized for testing. The MIMIC-CXR dataset comprises 152k reports for training, 2.3k for validation, and 2.3k for testing. The workflow involves training with the 152k reports, saving the model weights based on the best performance on the validation set, and finally using these weights to perform inference on both the MIMIC-CXR and Open-i test sets. It is important to note that in this study, the models were specifically designed to generate the findings section of the reports. Additionally, samples with empty findings sections were excluded from consideration.

Metrics play a crucial role in comparing models, with BLEU4 [45] and ROUGE-L [46] currently considered as the most widely used natural language generation (NLG)-oriented metrics for reports. Additionally, two chest-RRG-oriented metrics, specifically designed to evaluate the quality of radiology reports, have been employed: F1CheXbert (F1cXb) [47] and F1RGER [12,14]. These metrics leverage neural networks to assess the quality of generated reports, offering a higher semantic evaluation. F1cXb utilizes CheXbert, a transformer model capable of identifying the presence of the 14 CheXpert [48] pathologies (atelectasis, cardiomegaly, consolidation, edema, enlarged cardiomediastinum, fracture, lung lesion, lung opacity, pleural effusion, pneumonia, pneumothorax, pleural other, support devices, and no finding) in a hypothesis report, and calculates the F1-score based on the pathologies present in the reference report. On the other hand, F1RGER employs a transformer model to analyze reports, generating graphs for entities and relationships. It evaluates comparisons between entity and relationship structures in hypotheses and reference graphs to compute the F1-score.

## 3. Results

This section details the experiments carried out to develop models for chest RRG. We analyze the proposed architectures and then conduct an ablation study on effective training techniques and strategies. Finally, we assess the competitiveness of our proposal by comparing it with state-of-the-art models. All experiments were conducted using a computer equipped with an NVIDIA RTX 4090 GPU.

### 3.1. Analysis of Our Architectures

This study proposes four VED models, distinguished primarily by the number of trainable parameters in each component. Table 1 illustrates how SwinB+BERT30k is the largest model, while SwinS+BERT9k is the smallest. The remaining two models fall within a similar parameter range. Comparing architecture sizes is interesting because the RRG task operates in a data-limited environment due to the high variability of medical reports and their scarcity. Therefore, training models with high parameter counts can become challenging to tune efficiently. The number of parameters, along with the nature and size of the dataset, are crucial factors for effective learning that avoids underfitting and overfitting. Furthermore, the results presented in Table 1 encourage analysis of which components of the architectures may be more critical for obtaining meaningful reports.

In addition to the number of parameters, Table 1 showcases BLEU4, ROUGE-L, F1cXb, and F1RGER metrics. These metrics were obtained following the same workflow and hyperparameters across all four models. During the first stage, involving training with NLL, we conduct training for 12 epochs with a learning rate of 3 × 10−4. Subsequently, in the second stage, corresponding to RL training, we train for 15 epochs with a learning
