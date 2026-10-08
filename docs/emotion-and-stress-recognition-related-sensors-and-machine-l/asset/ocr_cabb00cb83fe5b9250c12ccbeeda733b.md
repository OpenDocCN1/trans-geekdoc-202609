# 2.3.1. A: Foot Pressure

The forefoot pressure was calculated by adding the pressure of 12 sensor points located at the forefoot area of the insole. To calculate rear-foot pressure, the sensor readings of 4 sensors located at the heel area were added together. The sensor layout is depicted in Figure 2.

```
$P_F = \sum_{i=1}^{12} P_i$
```

```
$P_R = \sum_{i=13}^{16} P_i$
```

Before summing the raw data, we applied a moving average filter of a 1 s window size to filter out high frequency noises. Finally, we calculated the total foot pressure by summing up all pressure.

```
$P_T = \sum_{i=1}^{16} P_i$
```

Since the features are independent from previous data, all pressure features were segmented into 10 10 s non-overlapping windows. The mean of each window is used for the model training.

![](bbox=[0.358, 0.425, 0.642, 0.545])

# 2.3.2. B: Centre of Pressure

Literature has shown the Centre of Pressure (CoP) as an interesting feature to understand different postures and motion while standing [23], as well as sitting [77]. Therefore, we calculated the CoP for both dimensions (X-axis and Y-axis—see also Figure 3B) by a weighted average calculation as mentioned in prior work [23]. The CoP was also calculated over 10 s of non-overlapping windows since it is independent from the previous window.

```
$Y_{CoP} = \frac{\sum_{i=1}^{12} P_i Y_i + \sum_{i=13}^{16} P_i Y_i}{P_F + 3P_R}$
```

```
$X_{CoP} = \frac{\sum_{i=1}^{12} P_i X_i + \sum_{i=13}^{16} P_i X_i}{P_F + 3P_R}$
```