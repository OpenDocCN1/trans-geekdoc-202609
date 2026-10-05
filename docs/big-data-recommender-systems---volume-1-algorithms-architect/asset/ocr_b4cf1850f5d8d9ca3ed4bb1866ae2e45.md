# 94 Big recommender systems, volume 1

Table 5.5 Determination of fuzzy data type of the blood pressure level and its breakdown that ensure the fuzzy description logic [43]

| Category | Systolic | Diastolic |
|---|---|--|
| Hypertension | <90 mmHg And/or | <60 mmHg |
| Optimal | <120 mmHg And | <80 mmHg |
| Normal | 120–129 mmHg And/or | 80–84 mmHg |
| High normal | 130–139 mmHg And/or | 85–89 mmHg |
| Level one (Mid) | 140–159 mmHg And/or | 90–99 mmHg |
| Level two (Moderate) | 160–179 mmHg And/or | 100–109 mmHg |
| Level three (Seveere) | ≥180 mmHg And | ≥110 mmHg |
| Isolated systolic hypertension | ≥140 mmHg And | <90 mmHg |

Table 5.6 Fuzzy data types determined and identified in the hypertension fuzzy description logic

| Fuzzy data type | Definition | Vague data modelled |
|---|---|--|
| MidSystolic = LeftShoulderSystolic (0,200,140,159) | Denoting the numeric value of the Mid should with leftshoulder membership function LeftShoulderSystolic (0,200,149) and | Hypertension with its Systolic value range 0–159 mmHg and Diastolic 0–99 mmHg could be regarded as small to some value. The value distribution complies with a leftshoulder membership function |
| MidDiastolic = LeftShoulderDiastolic (0,120,90,99) | Denoting the numeric value of the Mid with leftshoulder membership function LeftShoulderDiastolic (0,120,90,99) | |
| ModerateStageSystolic = TrapezoidalSystolic (130,139,160,190) | Denoting the value of the Moderate should comply with trapezoidal membership function | Hypertension with its Systolic value range 130–179 mmHg and Diastolic 90–109 mmHg could be regarded as small to some value. The value distribution complies with a trapezoidal membership function |
| ModerateStageDiastolic = TrapezoidalDiastolic (100,99,100,109) | Denoting the value of the Moderate comply with trapezoidal membership function (130,139,160,179) and trapezoidalDiastolic (90,99,100,109) | | |
| SevereSystolic = RightShoulderSystolic (160,179,180,200) | Denoting the numeric value of the Severe should comply with RightShoulder membership function | Hypertension with its Systolic value range 160–200 mmHg and Diastolic 100–120 mmHg could be regarded as small to some value. The value distribution complies with a RightShoulder membership function |
| SevereDiastolic = RightShoulderDiastolic (100,109,110,120) | RightShoulderSystolic (160,179,180,200) and RightShoulderDiastolic (100,109,110,120) | |

the fuzzy concept data and provide in corresponding order. As an example, in fuzzy data a numeric representation has to be linked to linguistic representation like Stage_one hypertension diagnosis and also to generate a probabilistic linguistic specification of hypertension risk level mid stage. It princes that the fuzzy