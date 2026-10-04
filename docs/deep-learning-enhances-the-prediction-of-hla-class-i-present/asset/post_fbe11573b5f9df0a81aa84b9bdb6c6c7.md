
# Article

## Comparison of average precision

## Comparison of ROC-AUC

## Average precisions

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_0.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_1.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_2.png)

Test/epitope overlap (%):
71 72 75 67 77.5

Test/epitope overlap (%):
71 72 75 67 77.5

## 8-mers

## 9-mers

## 10-mers

## 11-mers

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_3.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_4.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_5.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_6.png)

## 8-mers

## 9-mers

## 10-mers

## 11-mers

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_7.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_8.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_9.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_3_10.png)

Fig. 2 | MUNIS outperforming existing predictors in HLA-A binders across 8–11mers. a. Average precision (AP) and ROC-AUC (AUC) of all predictors on current-state-of-the-art tools like MHCflpred-2.2, NetMHCpan4.1, MHCFlurry-2.0, TranPhLA and BigMHC on predicting ligands (fragments) from muss peptide binders, n=24 HLA-1 alleles. b. Percentages of overlap with the training data of each tool all in the benchmark presentation show what is possible. c. Average pairwise comparisons between MUNIS and other predictors

Each point is the performance on one allele. d. Average precision (AP) and ROC-AUC (AUC) of all predictors on non-binding binders by epitope length, n=24 HLA+1 alleles. P values for pairwise comparisons between MUNIS and Mann test (***P<10). Box plots are presented with median values, 25th and 75th percentiles as upper and lower quartiles, and 5 times the interquartile range as the quartiles (outliers not shown).

Nature Intelligence | Volume 7 | 2025 | 223-243

235

# Article

https://doi.org/10.1038/s41466-024-0097-y

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_4_0.png)

**Fig. 3 | Motif analysis of misclassified binders reveals inconsistent reality of existing models on canonical HLA-1 binding motifs.** Motifs for elicited ligands (from mass spectrometry experiments) and non-binding peptides (from 724 and 208 and 609 binders). Boxplots are presented with median lines, 25th and 75th percentiles as upper and lower quartile, and interquartile range from the quartiles as whiskers (outliers not shown).
**b.** Binding for 9-mers for all classified binders (true positive) and misclassified binders (false positive) for each representative model.

allele HLA-B*40:01 residues are highlighted in yellow. Motifs for MUNIS positives are false positive because 25 incorrectly elicited ligands were identified as binding. Model-S000 was used for both positive and negative cases. Shannon HLA anchor residues (positions in two and a nine-mer) (true positive/false positive) HLA-I binders are highlighted by each point. Shannon entropy at an anchor residue provides for peptides that are true positive mispredicted for one HLA allele. P-values for comparison were calculated using Wilcoxon rank-sum test (p < 10^{-3}).

and BigMHC. PRIME2 was benchmarked on immunology testing sets by allele-peptide pair identity using “Rank allele” as a readout of performance. We found that MUNIS outperforms all other algorithms in presented epochs across the 5 datasets, with a median average performance of 0.289, which is a 6% relative improvement in performance compared to the next-best model (MHCflurry2). We also evaluated the performance of various models across different HLA alleles predicting immunogenic epitopes for each allele (see Fig. 4). In fact, the models with higher average precision scores than MUNIS were the ones with substantial imbalance between evaluation and training sets, as well as those with only non-immunogenic HLA-I binders as (Extended Data Fig. 2a). We identified in increased average over several experiments, indicating the tendency of models to predict, immunogenic epitopes while ignoring the relationship between increased threshold of presentation and downstream T-cell recognition and also revealed the unsolved gap to achieve high accuracy for immunogenicity when filtered on HLA binders.

response for each epitope. MUNIS has a pearson correlation coefficient of 0.33 with 0.34 and 0.29 for the next-best models (BigMHC, IM, and NetMHCpan) for epitopes identified in the active infected HIV subgroup (Fig. 4) and epitopes identified in the chronically infected HIV subgroup (Fig. 4). BigMHC and MHCflurry2 predicted 0.22 and 0.33 with 0.34 and 0.28 respectively for the epitopes identified in the chronically infected HIV subgroup (Extended Data Fig. 4b). BigMHC was benchmarked for HIV epitopes, which were selected from the MUNIS training set. We also stratified on an allele-based basis and found that MUNIS outperforms others in both the active (Extended Data Fig. 2b) and chronic (Extended Data Fig. 2c) HIV-infection cases.

Variations in immunogenicity prediction for individual epitopes were not observed, so we explored whether MUNIS could predict immunogenicity hierarchies, as effective T-cells would ideally elicit epitopes across many individuals. We tested the immunogenicity hierarchies for HLA-I alleles —*specifically*, we used a dataset of 119 HIV epitopes for T-cell responses in 527 individuals with HIV virus acute and chronic infection groups, with each epitope elicited a T-cell response on top of the corresponding matching HLA-I alleles.

We evaluated by using the Spearman rank correlation coefficient between the MUNIS-predicted score and

To decode features to enhance model performance, we performed an ablation analysis with competing models (Extended Data Fig. 3). We selectively identified input features to capture the potential of the evaluated Scaling Modeling (ESM-2) Transformer protein language model, size of the language model, flanking residues, negative sampling, which attempt to

Nature Intelligence | January 2025 | 232–243

# Article

https://doi.org/10.1038/s41466-024-0097-y

## a Influenza dataset Binders

## b Influenza dataset Immunogenic epitopes

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_5_0.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_5_1.png)

Test/epitope overlap (%):
Test/epitope overlap (%):

## c Acute HIV dataset Immundance

## d Chronic HIV dataset Immundance

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_5_2.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_5_3.png)

Test/epitope overlap (%):
Test/epitope overlap (%):

## e Acute HIV dataset Immundance

## f Chronic HIV dataset Immundance

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_5_4.png)

![](img/1a4107427b120f5fd0ae04fe5f7f7f10_5_5.png)

> Fig. 4 MUNIS exhibits existing immundance hierarchies. A comparison of MUNIS against existing tools like MHored2, NetMHCpan.1, Mimry2.0, TransHLA, BigMHC and Prime2.0 on leading epitopes (binders) from infection shows that MUNIS distinguishes binders from non-binders. Some significantly enriched peptides and ligands (and all other peptides (decys)) are identified as binder. Proteins with at least one epitope presented on MHC class I are identified as binder. Proteins with peptides and ligands from negative codons are identified as binder.

show the existing datasets and error bars show the error across the five cases. Epitope overlap with the datasets of each tool over the five influenza benchmarks are shown below. Parity comparisons between MUNIS and other tools show a value-of 0. Precision and frequency of recall across all epitope-allele pairs in acute (c) and chronic (d) HIV. Epitope overlap with the datasets of each tool over the HIV benchmarks are shown below. The model score is a standard error of the metrics reported. normalize model scores across HLA alleles (Extended Data Fig. 30). LASER-2 (35 million parameters) performed slightly worse than a smaller model (3 million), with an average precision of 0.959 with 0.953, respectively. Pretraining the model of HLA-I peptide presentation from an average precision of 0.946 to 0.953. Introducing flanking

enhanced HLA-I peptide presentation from an average precision of 0.947 to 0.953. Many of these features (namely, pretrainingtraining and incorporating flanking residues) reduced the average precision on immunogenicity prediction. With regard to immundominance, where the results are not stratified by allele, the performance of MUNIS using the

Nature Intelligence | Volume 7 | February 2025 | 232–243
