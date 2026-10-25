# Figure 3. Average score

```
Random Forest
In [71]: score = cross_val_score(ensemble.RandomForestClassifier(random_state = 41),
features, labels, cv = 10, scoring='accuracy')
print({'Scores for each fold are: (score)'})
print({'Average scores ('{:.2f}'.format(score.mean()))'})
```

up random forest models. Several trees are used in Random Forest to construct a forest and each tree is then continuously assessed. The Figure 3 show the executed steps for random forest algorithm.

# Cross Validation

Cross-validation is used to evaluate and choose the optimal model. Cross-validation is applied to two models: Random Forest and XBoost. With the highest average score of 0.97, Random Forest is chosen to construct the final model.

# 4. PERFORMANCE ANALYSIS

The dataset includes 150 patients, ages 60 to 96, with longitudinal MRI data. At least one scan was performed on each individual. Everybody has a right hand. Throughout the investigation, 72 of the individuals were classified as “Nondemented.” During the course of the study, 64 of the individuals were classified as “Demented” at the time of their first visits. At their first appointment, 14 participants were classified as “Nondemented,” however at a later visit, they were classified as “Demented.” These are classified as “Converted.”According to the figure 4 in the graph below, men are more likely than women to have dementia.

The following Figure 5 in graph indicates that the Nondemented group outperformed the Demented group on the Mini Mental State Examination (MMSE) by a significant margin. The most popular test for evaluating memory and other cognitive function issues is the MMSE. The MMSE has a range of values from 0 to The atlas scaling factor, the estimated total intracranial volume, the normalized whole brain volume, and the mini-mental state exam (MMSE) score are examples of clinical variables. 30, with scores of 25 or above often being regarded as normal. Severe impairment is typically indicated by a score of less than 10, and moderate dementia is indicated by a score between 10 and 20. Early-stage Alzheimer’s patients typically have scores between 20 and 25. Figures 5-8 describe about ASF analysis, eTIV and nWBV analysis.

According to the chart, the brain volume ratio of the non-demented group is higher than that of the demented group. This is thought to be the result of diseases that cause the brain’s tissue to shrink.

We have taken two approaches to addressing this problem. The first is to simply remove the rows that have null values. ‘Imputation’, or substituting the missing values with the corresponding values, is the other method. We believe that imputation would improve our model’s performance because we only have 150 data points.