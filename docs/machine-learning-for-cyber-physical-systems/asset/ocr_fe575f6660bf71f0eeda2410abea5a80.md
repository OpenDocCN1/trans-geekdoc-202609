is improved as much as possible (1.423 mm instead of 1.41 mm and close to accepted quality). For this purpose, TT is increased from 5 s to 19.8 s, QF is at its maximum and Sp is increased to 1.99 mm.

# Table 4. Limited adjustment / no adjustment possible. Again, violated quality criteria are written in bold. Marked with a star are improved by still violated qualities.

| process step | process 1 ST STemp [mm] [°C] | process 2 TT [s] | process 3 QF QT Sp [kN] [s] [mm] | quality P1H P2ST [HV] [mm] |
| :--- | :--- | :--- | :--- | :--- |
| process 1 - default | 1.44 900 | 5 | 2,000 2 1.05 | 480.2 1.41 |
| process 1 - adjusted | 1.44 900 | 19.8 | 2,500 2 1.99 | 390.0 1.423* |
| process 2 - start | 1.45 900 | 20.5 | 2,500 2 1.99 | **385.4 1.423** |
| process 2 - adjusted | 1.45 900 | 20.5 | 2,500 2 1.99 | **385.4 1.423** |

# 4.4 No Adjustment Possible

Sometimes the quality prognosis after process step 1 indicates that the produced part will not meet the final product quality requirements. Given the fact, that the prognosis is accurate, this is a very valuable information this early on in a production line because defective parts can be removed early in the production process with the additional benefit of cost and energy savings. Table 4 shows an example where after process step 2 no parameter adjustment is possible without violating the constraints. HP1 and P2ST will both be too low no matter how the process parameters in process 3 are altered.

# 5 Discussion and Conclusions

A combination of linear regression and least squares optimization can be employed to reproduce a bidirectional relation between the process parameters and quality parameters in a fast and reliable manner. The proposed system is capable of estimating the quality outcome at any step of a production line. It allows adjustment of the controllable variables one or more process steps further on and identifies defective parts early in the production process.

If more than one quality criterion is considered, conflicting relations between them have to be expected. The goal of the parameter optimization is that parameter adjustments are found such that all quality criteria are satisfied. This constraint may result in an unsolvable optimization problem. The unsolvability of the problem after the first production step (or later in the process) indicates that the final product might not satisfy at least one quality criterion. The quality prognosis this early on in the production process is a valuable information, as potentially defective parts can be sorted out early. This saves resources, machine time and energy.