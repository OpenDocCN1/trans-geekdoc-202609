
Table 2: Structured clinical data from MIMIC-III.

| ID | Age | Gender | Admission_type | Diagnosis_code | Glucose (mg/dL) | Medication_history |
|---|---|---|---|---|---|---|
| 1 | 65 | M | Emergency | I21.9 | 178 | Aspirin and atorvastatin |
| 2 | 48 | F | Elective | E11.65 | 210 | Metformin and insulin |
| 3 | 76 | M | Emergency | J44.1 | 134 | Salbutamol and prednisone |
| 4 | 59 | F | Urgent | I10 | 125 | Lisinopril and amlodipine |
| 5 | 70 | M | Emergency | N17.9 | 98 | Furosemide |

Table 3: Simulated IoT vital signs and clinical notes.

| Patient_ID | HR(t) (bpm) | BP(t) (mmHg) | T(t) (°C) | Clinical_notes |
|---|---|---|---|---|
| 1 | 102 | 145/92 | 38.1 | "Chest pain on exertion, elevated troponin." |
| 2 | 88 | 130/85 | 37.2 | "Type 2 diabetes with poor glycemic control." |
| 3 | 96 | 138/88 | 38.5 | "COPD exacerbation, productive cough noted." |
| 4 | 110 | 165/100 | 37.8 | "Hypertensive crisis, non-compliant with meds." |
| 5 | 75 | 120/80 | 36.9 | "Acute kidney injury likely secondary to sepsis." |

age, disease codes, blood glucose level, and prescription medication, information vital for treatment planning and clinical decision-making. This is similarly shown in Table 3, where ongoing monitoring through simulated IoMT streams is displayed with dynamic metrics including body temperature, blood pressure, and heart rate. Clinical notes provide context-rich, unstructured data that improves AI-powered prediction and interpretation models. These datasets augment each other perfectly to create smart healthcare applications that facilitate real-time patient-centered interventions, remote monitoring, and early diagnosis.

## 3.2 Data Preprocessing

To preprocess structured and unstructured medical data from the MIMIC-III dataset and simulated IoMT streams for parallel analysis, structured preprocessing was used in the DigiCure system. Mode imputation was used initially to deal with categorical variables like medication history, and linear interpolation was used to deal with missing values in numerical time-series data like temperature, blood pressure, and heart rate for continuity. Severe physiological values beyond ±3 standard deviations, that is, heart rate > 180 bpm, were removed or substituted with clinical measures for data quality check. Measures based on Z-scores were used to identify outliers in analysis. Min-max scaling was applied to scale all quantitative features, such as vital signs and blood glucose, into a common [0, 1] range suitable for ML processes.

Clinical free-text preprocessing was carried out using the BioBERT tokenizer, transforming free-text data to semantically informative embeddings. One-hot encoding was used to encode categorical features such as gender, admission type, and diagnosis codes to allow effective model input. To preserve temporal trends, the continuous IoMT streams were segmented into 5-min fixed windows. Mean and first-order derivatives (e.g., heart rate change rate) were computed. A Savitzky-Golay filter was used to eliminate high-frequency noise and preserve signal trends and reduce the impact of noise on real-time sensor readings. ICD-9 diagnosis codes were also label encoded to make them compatible with multiclass classification models. Input data was tidy, well-structured, and optimized for precise diagnostic prediction and dynamic patient tracking because of our powerful preparation pipeline. Tables 4 and 5 show the raw data sample. Tables 6 and 7 show the preprocessed data sample.

Table 4: Raw clinical data from MIMIC-III dataset.

| ID | Heart rate (bpm) | Systolic BP | BP | Temperature (°C) | Gender | Glucose (mg/dL) | Admission type | Clinical notes |
|---|---|---|---|---|---|---|---|---|
| 1 | 192 | 85 | NULL | NULL | M | 330 | EMERGENCY | "pt c/o chest pain. ECG abnormal. immediate attn." |
| 2 | NULL | 140 | 90 | 39.1 | F | -20 | ELECTIVE | "No complications. Meds started. Observed stable." |
| 3 | 80 | 300 | 190 | 36.5 | M | 88 | EMERGENCY | "Patient diabetic. Check insulin, BP irregular." |
| 4 | 60 | NULL | 70 | 34.9 | F | 122 | EMERGENCY | "Low temp. Weakness reported. Monitor vitals closely." |
| 5 | 110 | 160 | 95 | NULL | M | NULL | ELECTIVE | "Pre-op. schedule confirmed. Stable prior to surgery." |

Table 5: Cleaned and imputed data.

| ID | Heart rate | Systolic BP | Diastolic BP | Temp (°C) | Gender | Glucose | Admission type |
|---|---|---|---|---|---|---|---|
| 1 | 192 | 85 | 60 (mean) | 37.0 | M | 330 | EMERGENCY |
| 2 | 86 | 140 | 90 | 39.1 | F | 80 | ELECTIVE |
| 3 | 80 | 180 | 110 | 36.5 | M | 88 | EMERGENCY |
| 4 | 60 | 120 | 70 | 34.9 | F | 122 | EMERGENCY |
| 5 | 110 | 160 | 95 | 36.8 | M | 100 | ELECTIVE |

Table 6: Encoded and normalized structured data.

| ID | HR (norm) | SBP | DBP | Temp | Gender M | Gender F | Glucose (norm) | Admit_Emerg | Admit_Elect |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 1.00 | 85 | 60 | 37.0 | 1 | 0 | 1.00 | 1 | 0 |
| 2 | 0.62 | 140 | 90 | 39.1 | 0 | 1 | 0.24 | 0 | 1 |
| 3 | 0.42 | 180 | 110 | 36.5 | 1 | 0 | 0.36 | 1 | 0 |
| 4 | 0.25 | 120 | 70 | 34.9 | 0 | 1 | 0.66 | 1 | 0 |
| 5 | 0.57 | 160 | 95 | 36.8 | 1 | 0 | 0.53 | 0 | 1 |

Table 7: NLP processed clinical notes (truncated embeddings).

| ID | Cleaned text | BERT embedding (first five dims) |
|---|---|---|
| 1 | Chest pain ecg abnormal immediate attention | [0.72, -0.14, 0.06, 0.18, 0.11] |
| 2 | No complications meds started observed stable | [0.51, 0.11, -0.05, 0.23, 0.09] |
| 3 | Patient diabetic check insulin bp irregular | [0.67, 0.07, -0.09, 0.30, 0.15] |
| 4 | Low-temp weakness reported monitor vitals closely | [0.48, -0.08, 0.04, 0.12, 0.07] |
| 5 | Pre-op schedule confirmed stable prior surgery | [0.53, 0.16, 0.02, 0.19, 0.08] |

## 3.3 Proposed DigiCure Framework

- Step 1: The MIMIC-III dataset is used to extract structured data including patient demographics, lab results, medication history, and diagnostic records. This dataset contains over 53,000 patient records and serves as the backbone for simulation.

- Step 2: Simulated IoMT sensor data is applied to generate continuous real-time readings of vital signs such as heart rate, blood pressure, and temperature using

```
HR(t), BP(t) = (Systolic(t), Diastolic(t)), T(t)
```

- Step 3: Missing values in lab test results and vitals are handled using mean imputation. This is applied using

```
X_{imputed} = \frac{1}{n} \sum_{i=1}^{n} X_i
```

For categorical fields like gender or admission type, mode imputation is used.

- Step 4: Outliers in continuous data are removed using z-score normalization. This is applied where values beyond ±3 standard deviations are considered outliers:

```
Z = \frac{x - \mu}{\sigma}
```

## Detailed Prediction Model Flowchart

![](img/106ef0dba620d314f9842503e8ef40c8_37_0.png)

Figure 1: Proposed framework.

- Step 5: All continuous features are normalized using min-max scaling to [0, 1] to ensure equal weight across AI models:

```
$$x' = \frac{x - X_{min}}{X_{max} - X_{min}}$$
```

- Step 6: One-hot encoding is used for categorical data such as gender and ethnicity. For example, male = [1,0] and female = [0,1].

- Step 7: Clinical notes are preprocessed using an NLP pipeline. Tokenization, stop-word removal, and lemmatization are applied, and then clinical text is embedded using a pretrained BERT model:

```
E = BERT(T(clinical note))
```

- Step 8: Structured and unstructured data are fused into a unified patient-level feature vector. This is used as the input feature:

```
F = [HR', BP', T', Labvalues, E]
```

- Step 9: Sliding windows are applied to IoMT time-series data with window size w = 30 s and stride s = 5 s. This is used to extract temporal dynamics for input into time-aware models.

- Step 10: From each time window, statistical features are extracted. This includes mean, variance, slope, and rate of change, calculated as

```
Slope = \frac{X_{t+w} - X_t}{w}, \mu = \frac{1}{w} \sum x_i
```

- Step 11: A hybrid AI model is applied using random forest for structured data and Bi-LSTM for time-series data. The model is trained to predict risk labels (e.g., high-risk = 1 and low-risk = 0) using binary cross-entropy loss:

```
L = -[y log(p) + (1 - y)log(1 - p)]
```

- Step 12: The random forest model is initialized and trained on the preprocessed structured data. Each decision tree T<sub>i</sub> in the forest is trained using bootstrapped samples. For each split, the Gini impurity is minimized:

```
Gini(D) = 1 - \sum_{i=1}^{k} p_i^2
```

where p<sub>i</sub> is the proportion of class i in dataset D. The prediction is based on the mode of the class outputs across all trees.

- Step 13: The time-series data is split into windows of fixed size w, and each window becomes an input sequence to the Bi-LSTM model.

- Step 14: For each time window, the forward LSTM computes

```
h_forward(t) = \sigma(W_forward h_forward(t - 1) + U_forward X_t + b_forward)
```

The backward LSTM computes

```
h_backward(t) = \sigma(W_backward h_backward(t + 1) + U_backward X_t + b_backward)
```
