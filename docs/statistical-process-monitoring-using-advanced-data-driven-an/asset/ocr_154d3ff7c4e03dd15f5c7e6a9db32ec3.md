| Model | SNR=10 | SNR=20 | SNR=50 |
|---|---|---|---|
| PLS | 2.183 | 1.111 | 0.4510 |
| PCR | 2.223 | 1.127 | 0.4565 |
| RR | 2.288 | 1.148 | 0.4584 |
| OLS | 3.849 | 1.955 | 0.7853 |

![](bbox=[0.15, 0.25, 0.86, 0.48])

FIGURE 2.11 The prediction MSEs of the studied models under different SNR levels.

in LVR models allows removing a portion of the noise in the data and thus improving the prediction quality. From Table 2.1, we can see that the PCR and PLS models provide comparable prediction performance, which is in agreement with the literature [145,146].

# 2.6.2 Monitoring influent measurements at water resource recovery facilities

Wastewater treatment plants (WWTPs) provide sustainable solutions to water scarcity. As initial conditions offered to WWTPs, influent characteristics (ICs) affect treatment units’ states, ongoing processes mechanisms, and product quality. Anomalies in ICs, often raised by abnormal events, need to be monitored and detected promptly to improve system resilience. In this section, the ability of the PCA-based approach to monitor influent measurements at WWTPs is investigated. For this purpose, historical ICs from the WWTP based in King Abdullah University of Science and Technology (KAUST), Thuwal, Saudi Arabia (Fig. 2.12) were engaged.

In this datafram, operators have kept seven years of records of 21 features (Table 2.2). Measurements were performed on samples taken from the headwork of the WWTP in order to maintain compliance with regulations and standards. This plant has a sustainability mission to provide all treated effluents for irriga-