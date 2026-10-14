X-axis represents gray value on location (x, y) and Y-axis represents (x + 1, y + 1). The corresponding value of correlation coefficient and volatility, calculated by (3.18) and (3.22) respectively, are shown in Table 3.1. It can be seen that correlation distribution of plain text images changed to diffusion distribution after encryption.

In terms of quantity criteria, the magnitude of correlation coefficient corresponding to plain text for test A–D are at 10⁻¹ level, and the minimum magnitude of volatility criterions are at 10⁵, for each channel (RGB) respectively. The coefficients and volatility of ciphered results are much less. The minimum magnitude of criterions is down to 10⁻⁵ for correlation coefficient and 10⁰ for volatility.

From these results taken together, the effectiveness of BC and BLE is higher than that of the other two, both in view of direct observing flaws appeared in correlation distribution and calculating analysis criterions. Comparatively, the encrypted results with the proposed BLE method exhibit better comprehensive performance than those with BC method to the extent of both diffusion in correlation distribution and uniform in a frequency distribution. Especially in test B–D that data are in gray level form, it can be seen that BLE possesses less volatility than BC even with approximate coefficient distribution.

What is remarkable is an interesting phenomenon that can be seen in Figure 3.12. When dealing with an extreme situation as test D, which possesses data of prominent contrast, 3DES-C fails to mix the correlation into well distribution (see second column in Figure 3.12b, 3.12g, 3.12l), and even though LC and BC scheme give mixture answer to HA (see Figure 3.12c and 3.12d) and DA (see Figure 3.12m and 3.12n) but appears to consist of regularity in VA (see Figure 3.12h and 3.12i). Only results of proposed BLE show a stable performance in HA, VA, and DA (see Figure 3.12e, 3.12j, 3.12o) but also reach the minimum volatility in test D, which is nearly 6.0162 × 10⁻⁵ of original data, almost the same with uniform distributed noise.

Form this phenomenon; it can be seen that proposed compounded strategy is a uniform distributed cipher. Especially when facing a data with intensive contrast information, BLE scheme has better adaptiveness and stability for encryption, whether in view of HA, VA, and DA correlation distribution or volatility criteria.

# 3.6 Discussion

# 3.6.1 Effectiveness

From the correlation analysis, the correlation distribution of the encrypted result from the proposed BLE method is more fairly uniform with diffusion and mixture than those from 3DES, Logistic chaotic, and single dynamic Bernoulli mapping,