# # Experimental Work

All the experimental tests were performed on a CNC lathe machine and under dry conditions. To decrease the variation of cutting speed across the cutting edge, a large diameter work piece were used. In order to establish the genetic equation, different values of cutting speed, V, and cutting time, t, were selected while feed rate and depth of cut were selected constant values of 0.07 mm/rev and 1.5 mm respectively. The values of cutting speed selected were 65 (m/min), 75 (m/min) and 85 (m/min) and cutting times were 1 (min), 3 (min), 5 (min) and 7 (min). In addition to 12 mentioned experiments which were performed to train the genetic equation, 5 extra experiments were done to test the equation quantitatively which are according to conditions shown in Table 1.

Commercially available uncoated cemented carbide insert (Tizit, TNMA 220408, grade P20) were used in these tests. AISI 4104 with hardness about 187 BHN were selected as a work piece material because of its widespread application and acceptable machinability. For the measurement of the wear parameters, cutting inserts were examined carefully using an optical microscope equipped with image processing software.

The radii of obtained chips were measured by vernier caliper, however, profile projector were used to measure accurately chips with bigger radius.

The accuracy of developed equations was analyzed in terms of two statistical measures. These measures are the root mean square error, RMSE, and absolute friction of variance, R^2, which are defined as below:

```
RMSE = \sqrt{\sum_{m=1}^{n} \frac{(Y_{predicted,m} - Y_{experimental,m})^2}{n}}
```

```
R^2 = 1 - \frac{\sum_{m=1}^{n}(Y_{predicted,m} - Y_{experimental,m})^2}{\sum_{m=1}^{n}(Y_{experimental,m})^2}
```

# Table 1. Cutting parameters for testing step of GP

| | Test 1 | Test 2 | Test 3 | Test 4 | Test 5 |
|---|---|---|---|---|---|
| V(m/min) | 80 | 60 | 50 | 60 | 70 |
| t (min) | 3 | 2 | 4 | 4 | 3 |