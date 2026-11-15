# 4. Results

This section presents the results in four key aspects that highlight the effectiveness of our proposed approach. First, we present the minimal miRNA biomarker set identified from the ensemble feature selection method. Second, we highlight the best model selected during the training phase and its performance metrics. Third, evaluation of selected best model and its performance on validation sets. Finally, we present the biological pathway analysis based on the selected miRNA features.

# 4.1. Selected Minimal miRNA Feature Set

We identified a minimal set consisting of 10 miRNAs through the ensemble feature selection method combined with nested cross-validation. These miRNAs significantly contribute to the classification of Usher syndrome when compared to control samples. The selected miRNAs are: hsa-miR-148a-3p, hsa-miR-183-5p, hsa-miR-146a-5p, hsa-miR-28-5p, hsa-miR-30c-5p, hsa-miR-551b-3p, hsa-miR-642a-5p, hsa-miR-181a-5p, hsa-miR-28-3p, hsa-miR-182-5p.

The SHAP summary plot shown in Figure 3, illustrates the contribution of specific miRNAs to the model's output for distinguishing between Usher syndrome and control samples. Each dot represents a SHAP value for a given miRNA in a sample, with color indicating the miRNA's expression level (blue for low and red for high). The position on the x-axis shows the impact of the feature on the model's prediction: positive values push the model towards predicting Usher syndrome, while negative values push towards control. The feature importance plot (in Figure 4) reveals the contribution of individual miRNAs to the classification decision between Usher syndrome patients and control samples.

![](bbox=[0.168, 0.475, 0.83, 0.795])

Figure 3. SHAP summary plot with selected miRNA features.

Key observations for each miRNA: hsa-miR-148a-3p: Highly ranked in SHAP feature importance, contributing significantly toward USH prediction with high SHAP values. In other words, higher expression levels (red) increase the SHAP value positively, strongly contributing to Usher syndrome prediction.