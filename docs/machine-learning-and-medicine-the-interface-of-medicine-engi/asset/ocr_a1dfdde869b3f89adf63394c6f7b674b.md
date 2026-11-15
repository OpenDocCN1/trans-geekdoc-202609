# Table 1. Cont.

| Authors | Population | Country | Sample Size | Sex (%M) | Age (yrs) | Method LVH | Definition LVH | Variables | Machine Learning |
|---|---|---|---|---|---|---|---|---|---|
| Lim et al., 2021 [39] | Military | Singapore | 17,310 | 100 | 18 | Echocardiogram | >95 g/m² (women) >115 g/m² (men) 0.8% | 26 chosen ECG-derived features clinical variables were: body weight, height, body fat percentage, and systolic blood pressure | Random Forest Logistic Regression, GLMNet, Random Forest, Gradient Boosting Machines |
| Zhao et al., 2022 [40] | Hospital based | China | 3120 | 42 | 65 | Echocardiogram | >115 g/m² (men) 56% | ECG variables included: QT interval, mean QRS duration and R wave in lead I | CNN |
| Sammani et al., 2022 [41] | Hospital based | The Netherlands | 2456 | 55 | 61 | Echocardiogram | >95 g/m² (women) >115 g/m² (men) 0.8% | Lab: Hgb, PLT, lipids, creatinine, Na, K age, systolic blood pressure and body surface area | XGBoost |
| | | | | | | | | 20 ECG data: p, QRS and T wave axes, pr, QRS, QT and QTe durations, peak amplitudes of p, Q, R, S and T waves | |
| Kokubo et al., 2022 [42] | Hospital based | Japan | 12,008 | 64 | 57 | Echocardiogram | >95 g/m² (women) >101 g/m² for men 16.5% | 19 factors—clinical (age, sex, height and weight) and ECG features (heart rate, rhythm, pr interval, QT interval, QRS axis, p wave axis | ENN |
| Naderi et al., 2023 [43] | UK data base | UK | 37,534 | 48 | 64 | MRI | >70 g/m² (men) 1.5% | Clinical—V2, V5 and V6 as well as QRS voltages in leads V1, V2 blood pressure | LR, RF |
| | | | | | | Echocardiogram | >55 g/m² (women) | 23 ECG variables from leads I, II, V1-6 | LR, SVM, RF |
| Liu et al., 2023 [44] | Military Hospital | Tawain | 952 | 90 | | Echocardiogram | >115 g/m² (men) 18% | 24 features which consisted of R peak and S valley amplitudes automatically obtained from the output of ECG signal | Decision tree SVM and Back propagated Neural Network |