in this study. Furthermore, a cut-off of <120 mg dl$^{-1}$ is generally indicative of insulin sensitivity. For the purpose of this paper, we defined non-insulin sensitivity of individuals (those with SSPG $\ge$ 120 mg dl$^{-1}$) as insulin resistance (IR). This includes individuals with moderate and severe IR, all of whom have been shown to respond to treatments known to improve insulin sensitivity (both lifestyle and medications).

# Quantifying the relative deviance for each physiologic measure for metabolic subphenotype assignment

To classify each participant to their most 'abnormal' physiologic process, we calculated a standardized deviance score (that is, a Z-score) for each metabolic measure for each participant (equation 5), where msp$^j_i$ is the $i$th metabolic measure of participant $j$ and mean(msp$^i$) is the average of $i$th metabolic measure among the cohort's participants and sd(msp$^i$) is the standard deviation. High positive deviance indicates a more abnormal score and stronger phenotype for that measure in a given individual; high negative deviance indicates a healthier metabolic measure, and thus relative absence of the unhealthy phenotype as compared with the average population. DI and IE% were negated before applying equation (5), since higher DI and IE% indicate healthier $\beta$-cell function and incretin function, respectively. As shown in the heat map in Fig. 2, it is possible to see in a given individual the relative deviance for each metabolic measure: some individuals had a single dominant (most deviant) measure, whereas others had two or more that were equally dominant.

# (2) β-cell function (DI).

To quantify the status of β-cell function, we first calculated insulin secretion rate using the C-peptide deconvolution method, using C-peptide concentrations measured during OGTT tests at 0, 15 and 30 min. The Insulin SEcretion (ISEC) software$^{42}$ was used to calculate prehepatic insulin secretion from plasma C-peptide measurements with adjustment for age, sex and BMI$^{43}$. The ISEC software can be obtained from the author Roman Hovorka of the Metabolic Modelling Group, Centre for Measurement and Information in Medicine, Department of System Science, City University, London, United Kingdom. We required an error coefficient of variation of 5% and 15-min intervals. As the programme uses a population model of C-peptide kinetics, we classified individuals as diabetic ('niddm') if they had either fasting plasma glucose >126 mg dl$^{-1}$, 2 h glucose during OGTT >200, or HbA1c >6.5; or as 'obese' if they were non-diabetic with BMI > 30. The remaining individuals were classified as 'normal'. Because insulin secretion is best interpreted relative to insulin resistance (insulin-resistant individuals need to secrete more insulin to maintain normoglycaemia), we then calculated DI$^{44,45}$, as previously described, which adjusts the insulin secretion rate for degree of insulin resistance to generate an overall measure of B-cell function. DI was calculated as the area under the insulin secretion rate, divided by the SSPG (equation 1). DI thus describes β-cell function relative to insulin resistance.

```
DI = \(\left( \frac{\int_{t=0}^{t=30} \text{Insulin Secretion Rate}_t^{OGTT} \ dt}{\text{SSPG}} \right)\) (1)
```

```
deviance(msp$^j_i$) = \(\frac{\text{msp}^j_i - \text{mean(msp}^i\text{)}}{\text{sd(msp}^i\text{)}}\) (5)
```

where $i \in$ {MuscleIR, BetaCellDysfunction, IncretinDysfunction, HepaticIR}.

For each participant, the dominant metabolic subphenotype was identified on the basis of the one exhibiting the highest deviance score. When the difference in deviance scores between the two highest metabolic subphenotypes was less than 0.5, the participant was classified as having co-dominant subphenotypes. If more than one subphenotype exhibited deviance scores within 0.5 of the highest score, the participant was classified as having neither dominant nor co-dominant subphenotypes. This method is not intended for the clinical diagnosis of metabolic abnormalities. Instead, it focuses on identifying individuals with deviations in metabolic profiles relative to a reference cohort. Further validation in diverse populations is required to assess its generalizability.

# (3) Incretin effect (IE%).

We quantified the incretin effect as previously described$^{46}$ using equation (2). IE was calculated on the basis of the difference in the C-peptide concentrations during a frequently sampled OGTT and IIGI (0–180 min) that by design induce nearly identical plasma glucose concentrations. The difference in C-peptide in response to oral versus intravenous glucose loading reflects the contribution of incretin hormones from the gut that stimulate pancreatic β-cell insulin secretion. A higher incretin effect may indicate either increased secretion of incretin hormones (for example, GLP-1 and GIP) and/or β-cell responsiveness to these hormones. Lower incretin effect may be due to deficiency in incretin hormone secretion and/or relative inability to stimulate insulin secretion from the β-cell.

```
IE% = \(\left( \frac{\int_{t=0}^{t=180} \text{cpeptide}_t^{OGTT} \ dt - \int_{t=0}^{t=180} \text{cpeptide}_t^{IIGI} \ dt}{\int_{t=0}^{t=180} \text{cpeptide}_t^{OGTT} \ dt} \right) \times 100\) (2)
```

# (4) Hepatic IR index.

Liver insulin resistance was inferred using a surrogate index as shown in equation (3) (ref. 47), where insulin is measured in (microU ml$^{-1}$), plasma HDL cholesterol is measured in (mg dl$^{-1}$) and BMI is measured in kg m$^{-2}$. In adults, body fat % (BF%) can be estimated using the Deurenberg Index as shown in equation (4)$^{37}$, where BMI is measured in kg m$^{-2}$, age in years, and sex = 1 for male and sex = 0 for female.

```
Hepatic IR = $-0.091 + 0.4 \times \log\left(\int_{t=0}^{t=180} \text{insulin}_t^{OGTT} \ dt\right) + 0.346 \times \log(\text{BF\%}) - 0.408 \times \log(\text{HDL}) + 0.435 \times \log(\text{BMI})$ (3)
```

# Genotyping and T2D polygenic risk score calculation

DNA was extracted from whole-blood peripheral blood mononuclear cells (PBMC). The concentration of the extracted DNA was measured using Qubit, normalized to 50 ng μl$^{-1}$, and 10 μl was used for each sample for genotyping. All samples were genotyped using the Illumina Infinium Omni2.5Exome array with ~2.6 million single nucleotide variants (SNV) sites measured. Genotyping data underwent standard quality control using PLINK$^{38}$, including filtering of SNVs with excess missing genotypes (>2%), filtering of SNVs out of Hardy–Weinberg equilibrium ($P < 1 \times 10^{-6}$) and removal of samples with either excess missing genotypes (>3%) or discordant genetic vs recorded sex. Coordinates were aligned to the positive strand on genome build GRCh38 and the data were imputed against the TOPMed R2 reference panel$^{59–61}$. After quality control and imputation, 11.8 million high-quality SNVs ($R^2 > 0.3$) were obtained. T2D polygenic risk score (PRS$_{T2D}$) was generated as an additive model using 338 index variants and corresponding weights from the DIAMANTE multi-ancestry meta-analysis study$^{49}$. Of the 338 variants, 16 were not available, for which mean population scores were added using the TOPMed Bravo platform reference frequencies (2 × weight × population allele frequency)$^{61}$.

```
BF% = $-5.4 + 1.2 \times \text{BMI} + 0.23 \times \text{Age} - 10.8 \times \text{Sex}$ (4)
```

# Machine-learning framework to identity metabolic subtypes from OGTT glucose time series

# Preprocessing.

Glucose time series were preprocessed by imputing missing data using linear interpolation.

# Features extraction.

We extracted features for the machine-learning framework using two feature extraction approaches (1) OGTT glucose time-series features (OGTT_G_Features) and (2) reduced representation