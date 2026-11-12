# Table 3. Rules on the CAD dataset. The predicates in green boxes are direct indicators, and those in blue boxes are indirect indicators.

| Model | Rule | Weight | Correctness |
| :--- | :--- | :--- | :--- |
| TELLER | Respiratory Rate High → Dead | 0.2859 | Correct |
| TELLER | Arterial Blood Pressure diastolic Low → Dead | 0.2202 | Correct |
| TELLER | Heart Rate High → Dead | 0.1614 | Correct |
| TELLER | Arterial Blood Pressure mean Low → Dead | 0.1400 | Correct |
| TELLER | O2 saturation pulseoxymetry Low → Dead | 0.1283 | Incorrect |
| CLNN | c.Glucose High → c.Dead > -0.25 | 1.03 | Correct |
| CLNN | c.BUN High → c.Dead > -0.63 | 1.01 | Correct |
| CLNN | c.INR Low → c.BUN High > 0.01 | 0.99 | Incorrect |
| CLNN | c.Glucose High → c.AST Low > -0.08 | 0.99 | Incorrect |
| CLNN | c.Albumin High → c.Glucose High > 0.02 | 0.97 | Correct |
| CLNN | c.BUN High → c.C-Reactive-Protein High > -0.14 | 0.96 | Correct |
| CLNN | c-Brain Natriuretic Peptide High → c-BUN High > 0.41 | 0.94 | Correct |
| CLUSTER | BUN Low equal Lactic Acid Low | - | Incorrect |
| CLUSTER | Hemoglobin High equal Hematocrit High | - | Incorrect |
| CLUSTER | Brain Natriuretic Peptide High after ALT Low | - | Correct |
| CLUSTER | Heart Rate High → before AST Low | - | Correct |
| CLUSTER | Calcium ionized High equal Total Bilirubin High | - | Incorrect |
| CLUSTER | CK-MB fraction High equal Calcium ionized Low | - | Correct |
| CLUSTER | Calcium ionized Low equal Cholesterol High | - | Correct |
| CLUSTER | Temperature Low equal Hemoglobin High | - | Correct |
| CLUSTER | Hematocrit Low equal Total Bilirubin Low | - | Incorrect |
| CLUSTER | Glucose Low before Anion gap Low | - | Incorrect |
| HRTPP | Heart Rate Low equal Arterial Blood Pressure diastolic High → Dead | 2.4073 | Correct |
| HRTPP | Anion gap High before Heart Rate Low → Dead | 1.7742 | Correct |
| HRTPP | Heart Rate Low equal Potassium High → Dead | 1.6257 | Correct |
| HRTPP | Potassium Low before O2 saturation pulseoxymetry Low → Dead | 1.3959 | Correct |
| HRTPP | Respiratory Rate Low before Potassium High → Dead | 1.1533 | Correct |
| HRTPP | Arterial Blood Pressure mean Low → before Arterial Blood Pressure diastolic Low → Dead | 1.1312 | Correct |
| HRTPP | Anion gap Low equal O2 saturation pulseoxymetry Low → Dead | 1.1303 | Correct |
| HRTPP | Glucose Low equal Arterial Blood Pressure systolic Low → Dead | 0.5603 | Correct |
| HRTPP | Heart Rate Low equal INR High → Dead | 0.4213 | Correct |
| HRTPP | Temperature High and Respiratory Rate High → Dead | 0.3194 | Correct |

mortality, while other indicators influence mortality through them. Hence, we classify the rules into direct or indirect rules according to their relationships. Table 3 shows direct indicators in green and indirect indicators in blue. HRTPP identifies the most direct rules, showing strong ability in capturing key CAD mortality factors. HRTPP also balances direct and indirect rules well, focusing on major factors without omitting minor details, thus enhancing its applicability in medical decision-making.