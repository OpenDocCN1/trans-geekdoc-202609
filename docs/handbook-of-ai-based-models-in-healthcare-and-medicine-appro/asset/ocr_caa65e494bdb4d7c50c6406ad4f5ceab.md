![](bbox=[0.11, 0.1, 0.92, 0.56])

# FIGURE 4.2 a. Triglycerides. b. Copper. c. Cholesterol. d. Bilirubin

is encoded as 0, in Ascites, Hepatomegaly, and Spiders, yes is encoded as 1 and no is encoded as 0, in Drug, D-penicillamine is encoded as 0 and placebo as 1, and ordinal encoding is applied on Edema. Status is shown by mapping Y as 0, N as 1, and S as 2, where Y means edema is present despite diuretic therapy, N means there is no edema and no diuretic therapy for edema, and S means edema is present without diuretics, or else edema was resolved by diuretics. For the attribute Status, D (death) is encoded as 0, C (censored) as 1, and CL (censored due to liver transplant) as 2. The bivariate analysis of the attributes, which explains the pairwise relationship between attributes, is shown in Figure 4.3.

It has been observed from the pair plot that there is no linear relationship between the variables. The attributes are scaled further using StandardScaler and then feature selection is performed. Different feature selection methods are applied and in each method, the ten best essential features are selected. First, the Pearson correlation method, the ten best essential features are selected. First, the Pearson correlation is applied to the cirrhosis dataset and is visualized using a heatmap, as shown in Figure 4.4.

It has been identified that there are no highly correlated features. Spearman correlation analysis is done and the features with their corresponding p-values are given in Table 4.2.

The chi-squared test is applied and the ten best features (Sex, Drug, Alk-Phos, SGOT, Albumin, Prothrombin, Triglycerides, Bilirubin, Copper, Hepatomegaly) are selected. A supervised feature selection algorithm, extra trees classifier with ten estimators, and criterion entropy are applied, and the selected features are: Age, Bilirubin, Albumin, Cholesterol, Triglycerides, SGOT, Platelets, Prothrombin,