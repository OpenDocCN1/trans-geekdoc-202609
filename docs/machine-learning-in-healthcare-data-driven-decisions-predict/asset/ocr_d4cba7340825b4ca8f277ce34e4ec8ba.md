well in real-world scenarios because they are hyperparameter-sensitive, lack data variation robustness, and lack the ability to offer interpretability. Bayesian and RL-based optimizers are computationally intensive and require careful implementation. The necessity of overcoming these hurdles drives the development of novel optimization platforms that are not only driven by performance but also meet the legal, operational, and ethical requirements of today's healthcare systems.

# 3.1 Datasets Used

We employed three publicly available benchmark healthcare datasets: the Wisconsin Breast Cancer Diagnostic Dataset, the UCI Heart Disease Dataset, and the MIMIC-III Critical Care Database to evaluate and verify the proposed AGBO-CP framework. The unique features each dataset displays regarding clinical factors, diversity of patients, and prediction tasks make it possible to perform an in-depth analysis of the system's adaptability and performance.

# 3.1.1 MIMIC-III Clinical Database

Over 60,000 ICU admissions from Beth Israel Deaconess Medical Center during 2001–2012 are contained within the Medical Information Mart for Intensive Care (MIMIC-III) database, which was developed at MIT and comprises extensive de-identified health information. Individuals 16 years of age and older are represented in the dataset, and the composition of male and female patients is roughly equal. We pulled a vetted cohort of 32,763 intensive care unit admissions from MIMIC-III, targeting patients who were admitted to cardiac, surgical, and medical intensive care units. There are over 40 clinical factors in each patient record, including demographics such as age, sex, and ethnicity. Table 1 shows the features of MIMIC-III dataset.

Table 1: MIMIC-III dataset features.

| Feature name | Description | Type | Value range / Categories |
|---|---|---|---|
| Age | Age of the patient | Numeric | 16 to 90+ years (de-identified) |
| Gender | Sex of the patient | Binary | 0 = Female, 1 = Male |
| Admission type | Type of hospital admission | Categorical | Emergency, elective, urgent |
| ICU length of stay | Duration of ICU stay (days) | Numeric | 0 to >50 days |