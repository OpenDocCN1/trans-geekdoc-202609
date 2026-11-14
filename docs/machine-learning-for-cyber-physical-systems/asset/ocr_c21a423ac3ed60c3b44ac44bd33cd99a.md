# Table 2. No adjustment necessary. Highlighted in gray are the process parameters already known.

| process step | process 1 ST [mm] | process 1 STemp [°C] | process 2 TT [s] | process 3 QF [kN] | process 3 QT [s] | process 3 Sp [mm] | quality P1H [HV] | quality P2ST [mm] |
|---|---|---|---|---|---|---|---|---|
| process 1 - default | 1.5 | 900 | 5 | 2,000 | 2 | 1.05 | 483.8 | 1.47 |
| process 1 - adjusted | 1.5 | 900 | 5 | 2,000 | 2 | 1.05 | 483.8 | 1.47 |
| process 2 - start | 1.5 | 900 | 10 | 2,000 | 2 | 1.05 | 452.3 | 1.47 |
| process 2 - adjusted | 1.5 | 900 | 10 | 2,000 | 2 | 1.05 | 452.3 | 1.47 |

# 4.2 Parameter Adjustment

If the ST is 1.45 mm instead of 1.5 mm with an identical STemp of 900°C the estimated P2ST is too low. If the process is not adjusted, this cycle will likely produce a rejected part. However, the proposed approach allows an adjustment of the parameters in process step 2 and 3 in order to produce an accepted part. The model suggests a TT of 19.8 s instead of 5 s, a maximum QF of 2,500 kN and a slightly increased Sp of 1.2 mm in order to obtain a part with the required sheet thickness (Table 3, row 2). If the suggested TT of 19.8 s is slightly longer with 20.5 s, P1H is outside the feasible interval and an adjustment in process 3 is necessary (Table 3, row 3). Here, the QT is increased to 12.8 s and the Sp is increased to 1.71 mm in order to obtain a part with accepted quality (Tabe 3, row 4).

# Table 3. Parameter adjustment. Written in bold are violated quality criteria.

| process step | process 1 ST [mm] | process 1 STemp [°C] | process 2 TT [s] | process 3 QF [kN] | process 3 QT [s] | process 3 Sp [mm] | quality P1H [HV] | quality P2ST [mm] |
|---|---|---|---|---|---|---|---|---|
| process 1 - default | 1.45 | 900 | 5 | 2,000 | 2 | 1.05 | 480.8 | 1.42 |
| process 1 - adjusted | 1.45 | 900 | 19.8 | 2,500 | 2 | 1.2 | 390.0 | 1.43 |
| process 2 - start | 1.45 | 900 | 20.5 | 2,500 | 2 | 1.2 | 385.9 | 1.43 |
| process 2 - adjusted | 1.45 | 900 | 20.5 | 2,500 | 12.8 | 1.71 | 390.0 | 1.43 |

# 4.3 Limited Adjustment

For an even lower sheet thickness of 1.44 mm and STemp of 900°C the quality criterion P2ST is violated with 1.41 mm instead of 1.43 mm. An adjustment of the process parameters of process 2 and 3 is not possible without violating some of the constraints as the optimization approach aims for keeping both quality criteria within their intervals and at the same time all process parameters within their boundaries. Thus, a limited adjustment is performed in order to obtain a part as close as possible to accepted quality (Table 4, row 2). The parameters of process 2 and 3 are altered such that P1H is just at the lower limit and P2ST