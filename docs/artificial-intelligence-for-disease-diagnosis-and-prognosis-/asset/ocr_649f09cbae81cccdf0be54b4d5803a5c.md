The classification results of the implemented approaches are highlighted in Table 12.1. The ensembling approach achieved the highest accuracy of 95.94%. We aimed to improve sensitivity compared to specificity as misclassifying a T2D case is considered more severe than misclassifying a non-diabetic case. Our model detected all the T2D progressors (sensitivity, 100%) but misclassified 8.5% (specificity, 91.5%) healthy cases.

Our findings from this study are significant to identify whether individuals have a chance to be T2D progressors in the future. This advanced prediction will facilitate the prevention of T2D, or at least delay the onset of T2D by taking effective steps.

# 12.6.3 HbA1c Prediction for Enhanced Diabetes Management

Periodic monitoring of HbA1c is essential for the proper management of diabetes. An above-normal range of HbA1c levels increases the risk of developing diabetes-related complexities such as cardiovascular disease. To further facilitate diabetes management, we developed an HbA1c prediction model that can predict HbA1c levels two–three months in advance through applying ML techniques on time-series CGM data as summarized in Figure 12.4. The results presented in this study appear in the IEEE Sensor Journal [35].

We initiated a retrospective data collection with Sidra Medicine, Qatar, to collect BG data from 200 participants using CGM sensors. The Institutional Review Board (IRB) of Sidra Medicine approved our study (IRB Number, 1536761-1). We used CGM sensors known as Freestyle Libre for 90–120 days for each participant. The CGM sensor provides 96 measurements of BG levels per day. The HbA1c levels were collected separately at the laboratory and correlated with BG levels by extracting novel features such as time in range (TIR) based on:

```
TIR_{70-180} = \frac{\sum_{i=1}^N (C(x_i) \ge 70 \land \le 180)}{N} \quad (12.1)

TIR_{250-300} = \frac{\sum_{i=1}^N (C(x_i) \ge 250 \land \le 300)}{N} \quad (12.2)

TIR_{300-350} = \frac{\sum_{i=1}^N (C(x_i) \ge 300 \land \le 350)}{N} \quad (12.3)
```

where C represents overall counts, x stands for individual BG values, and N represents the sample size. TIR_{70-180} represents how much time a participant spends in the BG ranges of 70–180 mg/dL. A previous study shows that TIR and HbA1c are correlated significantly [36].

The proposed three-staged MSMC framework is highlighted in Figure 12.5. The framework predicts HbA1c levels two–three months in advance time frame using BG data. We split participants based on HbA1c ranges into four distinct patients groups. These patient groups belong to control group (class C1, ≤ 7.5%), medium control group (class C3, 7.5% <HbA1c ≤ 9%), low control group (class C5, 9% <HbA1c ≤ 12.5%), and uncontrolled group (class C6, >12.5%), respectively.