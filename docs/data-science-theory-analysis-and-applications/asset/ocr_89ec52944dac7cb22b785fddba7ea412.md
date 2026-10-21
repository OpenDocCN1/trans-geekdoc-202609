An initial data analysis using 4,240 patients of the framingham.csv [8] dataset was undertaken to understand the quality of the patient health data and to correct any errors if found. Using frequency counts, it was found that 582 (13.7%) patients had some missing data. As missing data was only 13.7%, patients who had missing data were excluded from the study analysis. The study now consisted of 3,658 patients with 2,035 (56%) females and 1,623 (44%) males.

Further, the predictive model input data was standardized to enable all input variables in the model to have a fair chance of being significant. Predictive modeling is a process that uses data mining and probability to forecast outcomes. Each model is made up of a number of risk factors, which are variables that are likely to influence Ten Year CHD, the target variable of interest [9]. Once data has been collected for the relevant risk factors, a statistical model is formulated.

The dataset had four types of risk factors:

+   - Demographic Risk Factors
+   - Behavior Risk Factors
+   - Medical History Risk Factors
+   - Risk Factors from First Examination

The Demographic Risk Factors included:

+   - Male: sex of the patient (44%)
+   - Age: age in years at first examination (32–70 years)
+   - Education:
+     - Some high school (1) (42%),
+     - High school/GED (General Education Development) (2) (30%),
+     - Some college/vocational school (3) (17%),
+     - College (4) (11%)

The Behavior (Smoking Behavior) Risk Factors included:

+   - Current smoker (49%)
+   - cigsPerDay (1–70 cigarettes per day)

Medical History Risk Factors included:

+   - BPmeds: On blood pressure medication at the time of first examination (3%)
+   - prevalentStroke: Previously had a stroke (1%)
+   - prevalentHyp: Currently Hypertensive (31%)
+   - diabetes: Currently has diabetes (3%)

Risk Factors from First Examination included:

+   - totChol: Total cholesterol (mg/dL) (113–600 mg/dL)
+   - sysBP: Systolic blood pressure (83.5–295)
+   - diaBP: Diastolic blood pressure (48–142.5)