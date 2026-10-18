can compromise eight sensor measurements with a 30% threshold. A similar scenario can be seen from the real test bed, as in Figure 18.7.

![](bbox=[0.11, 0.15, 0.46, 0.35])

![](bbox=[0.49, 0.15, 0.83, 0.35])

FIGURE 18.7 Performance analysis of SHChecker framework for identifying attack vectors w.r.t. attacker’s capability for (Left) synthetic dataset and (Right) UQVS dataset.

# 18.5.3 Frequency of Sensors in the Attack Vectors

The proposed attack analyzer inspects the set of all possible attack vectors and figure out the involvement of the individual sensor measurements in the attack vectors. Figure 18.8 shows the sensor measurements’ frequency with respective attack vectors for both datasets. The evaluation figures that almost all sensor measurements contribute similarly (with a few exceptions like systolic sensor measurement) in all attack vectors, while the attack threshold is around 30%. The study provides an insight into prioritizing the protection of sensor measurements for designing a defense tool based on their contributions in attack vectors. If the frequency of a sensor measurement exceeds that of the others, the sensor associated with that certain measurement should be enhanced for securing the SHS architecture. Thus our analyzer can effectively provide a design guide.

![](bbox=[0.11, 0.66, 0.46, 0.82])

![](bbox=[0.48, 0.66, 0.83, 0.82])

FIGURE 18.8 Frequency of the different sensors in the attack vectors for (Left) synthetic dataset and (Right) UQVS dataset.