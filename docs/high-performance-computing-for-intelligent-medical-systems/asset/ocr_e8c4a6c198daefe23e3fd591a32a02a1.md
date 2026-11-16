![](bbox=[0.29, 0.11, 0.84, 0.27])

Figure 4.5. The proposed architecture for the first approach based on the LSTM networks to estimate BPs.

Table 4.1. The LSTM based model performance metrics.

| Blood pressure | R | ME | MAE | RMSE | STD | Subjects # | AAMI |
|---|---|---|---|---|---|---|---|
| Systolic BP | 0.32 | -3.57 | 15.84 | 21.92 | 21.63 | 200 | × |
| Diastolic BP | 0.12 | -1.45 | 8.71 | 12.26 | 12.17 | 200 | × |

The definition of the Pearson's correlation coefficient is given in equation (4.11). It indicates the relative covariance of the predicted ($Y_{est}$) and target values ($Y_{tar}$).

```
$$R = \frac{cov(Y_{est}, Y_{tar})}{\sigma_{Y_{est}} \times \sigma_{Y_{tar}}}$$
(4.11)
```

The table indicates that the algorithm does not meet the Association for the Advancement of Medical Instrumentation (AAMI) standard requirements. This protocol has been used to evaluate various BP monitoring devices. According to this standard, the number of patients must be higher than 85, and the ME and STD should be lower than five mmHg and eight mmHg, respectively [20]. Our results show that the LSTM network is not accurate enough according to the standard.

Another considerable point about the reported results in table 4.1 is the higher value of the Pearson's correlation coefficient for systolic BP compared with diastolic BP despite the reality that the MAE is much higher for systolic BP. To interpret these seemingly contradictory results, we should consider that the correlation coefficient is based on the relative variations instead of absolute values. Therefore, since systolic BP commonly has much higher amplitudes than diastolic BP, the coefficient is bigger for systolic estimations.

Figure 4.6 provides more visual cues about the low performance of the LSTM network. The figure demonstrates the high degree of error in both estimation procedures.

+   * **Curse of dimensionality:** When the input dimension increases, machine-learning problems become exceedingly difficult. It is because the range of input configurations will increase exponentially. This problematic phenomenon is known as the curse of dimensionality [17].