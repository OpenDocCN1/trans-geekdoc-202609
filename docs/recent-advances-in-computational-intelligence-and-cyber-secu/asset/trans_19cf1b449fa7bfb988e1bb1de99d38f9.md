

$$\varepsilon_{reff} = \frac{\varepsilon_{r} + 1}{2} + \frac{\varepsilon_{r} - 1}{2}\left[ {1 + 12\frac{h}{W_{p}}} \right]^{1/2}$$

贴片的长度可以计算为：

(3)

*L*[*p*] = *L*[*e**f**f*] − 2*Δ**L*

其中 *L[eff]*，是贴片的有效长度，给出为

(4)

$$L_{\text{eff~}} = \frac{c}{2f_{o}\sqrt{\varepsilon_{\text{reff~}}}}$$

而 ∆*L* 是由于边缘效应引起的长度延伸，给出为

(5)

$$\Delta L = 0.412h\frac{\left( {\varepsilon_{\text{reff~}} + 0.3} \right)\left( {\frac{W_{p}}{h} + 0.264} \right)}{\left( {\varepsilon_{\text{reff~}} + 0.258} \right)\left( {\frac{W_{p}}{h} + 0.8} \right)}$$

基板的长度和宽度 `L[sub]` 和 `W[sub]` 等于参考地面的 `L[g]` 和 `W[g]`，给出为

(6)

`L[g]` = 6*h* + `L[p]`

(7)

`W[e]` = 6h + `W[P]`

[Figure 26.2](#ch26.xhtml#fig26_2) 展示了模拟天线的反射系数。该图清楚地显示天线以五频带谐振，具有良好的阻抗带宽，并且具有更好的增益和驻波比。谐振频率为 1.6 GHz、2.4 GHz、5.8 GHz、7.2 GHz 和 9.9 GHz，非常适合 GNSS、WiMAX、LTE、无线 LAN、C 波段和 X 波段应用。

![Figure 26.2 The simulated reflection coefficient of the prototype antenna.](images/fig26_2_C.jpg)

[Figure 26.2 The simulated reflection coefficient of the prototype antenna.](#ch26.xhtml#R_fig26_2)

## 3. Antenna Evolution

原型天线是使用三个连续步骤绘制的，这些步骤在 [Figure 26.3](#ch26.xhtml#fig26_3) 中清楚地显示。第一步被视为“ANTENNA 1”，只是带有微带馈电线和四分之一波长变压器以及完整地面结构的矩形贴片。如 [Figure 26.4](#ch26.xhtml#fig26_4) 所示，“ANTENNA 1” 在 4.9 GHz 和 11.9 GHz 两个频率上谐振，这并不满足有用多频带应用的标准。“ANTENNA 1” 的两个谐振频率之间可以看到一些凹口，这导致了进化的第二步。在第二步中，进行参数分析，地面取如图所示的长度，并在其中有一些缺陷，即地面上有一条长条带和一个方形切口。该天线被命名为“ANTENNA 2”。该天线提供三个谐振频率，分别为 2.5 GHz、6.9 GHz 和 9.9 GHz，但回波损耗较低。因此，为了使该拟议天线适用于更多多频带应用，在贴片上方添加了触手状结构，如图所示，以便将该天线作为多频带天线运行。最后，“ANTENNA 3” 产生五个频段 (1.4 – 1.8)/1.6 GHz、(2.1–3.5)/2.4 GHz、(5.4–6.3)/5.8 GHz、(7.0–7.3)/7.2 GHz 和 (9.2–11.6)/9.9 GHz，具有良好的谐振和带宽，并且也覆盖了良好的无线应用。

![Figure 26.3 Evolution of antenna design.](images/fig26_3_C.jpg)

[Figure 26.3 Evolution of antenna design.](#ch26.xhtml#R_fig26_3)

![Figure 26.4 Return losses of the antenna evolution.](images/fig26_4_C.jpg)

[Figure 26.4 Return losses of the antenna evolution.](#ch26.xhtml#R_fig26_4)

## 4. Results and Discussions

原型由 36 × 30 × 1.6 mm³ 的尺寸组成。天线为低剖面，产生五个谐振，具有非常好的阻抗带宽，并且增益和驻波比也更好。该天线覆盖的频段为 (1.4–1.8)/1.6 GHz、(2.1–3.5)/2.4 GHz、(5.4–6.3)/5.8 GHz、(7.0–7.3)/7.2 GHz 和 (9.2–11.6)/9.9 GHz。

### 4.1 Parametric analysis

模拟参数分析显示了接地长度 “`L[g]`” 从 12 mm 变到 15 mm 的变化，如 [Figure 26.5](#ch26.xhtml#fig26_5) 所示。在该图中显示，当 `L[g]` 的值为 12 mm 时，该天线产生四个谐振，回波损耗较低。`L[g]` = 14 mm 产生四个谐振频率，并且除第二谐振频率外回波损耗也较低。当 `L[g]` 为 15 mm 时，如图所示，天线仅提供三个频率。因此，`L[g]` 为 13 mm 时结果最佳，具有五个谐振、良好的带宽和增益。

![Figure 26.5 S11 vs. frequency plot for variation in Lg.](images/fig26_5_C.jpg)

[Figure 26.5 S11 vs. frequency plot for variation in `L[g]`.](#ch26.xhtml#R_fig26_5)

[Figure 26.6](#ch26.xhtml#fig26_6) 展示了当贴片长度 `L[p]` 从 11 mm 变到 14 mm 时，所提天线的 `S11` 参数。对参数分析进行，并当 `L[p]` 的值为 11 mm 时，天线仅提供三个谐振频率，回波损耗较低。`L[p]` 取 12 mm 时也仅提供三个谐振频率，回波损耗相同，并且带宽也更小。当 `L[p]` 取为 14 mm 时，该天线在四个频率上谐振，但在某些频率上回波损耗更大，在某些频率上更小。因此，`L[p]` 为 13 mm 在各方面均提供最佳结果。

![Figure 26.6 S11 vs. frequency plot for variation in Lp.](images/fig26_6_C.jpg)

[Figure 26.6 S11 vs. frequency plot for variation in `L[p]`.](#ch26.xhtml#R_fig26_6)

馈电结构宽度从 2 mm 变到 4 mm 时的回波损耗如 [Figure 26.7](#ch26.xhtml#fig26_7) 所示。图中非常清楚地显示，当 `WF1` 为 2 mm 时，所提天线仅在四个频率上谐振，回波损耗和带宽较低。当 `WF1` 取为 4 mm 时，天线在五个频率上谐振，但在某些频率上谐振较少，在某些频率上较多，但 `WF1` = 3 mm 的值提供了良好且更好的谐振和带宽，并且增益也更好。

![Figure 26.7 S11 vs. frequency plot for variation WF1.](images/fig26_7_C.jpg)

[Figure 26.7 S11 vs. frequency plot for variation WF1.](#ch26.xhtml#R_fig26_7)

### 4.2 Surface current distribution

所提天线的表面电流分布在所有谐振频率下均显示在 [Figure 26.8](#ch26.xhtml#fig26_8)a–e。在 1.6 GHz，如 [Figure 26.8](#ch26.xhtml#fig26_8)a 所示，表面电流主要分布在馈电结构和四分之一波长变压器上，并且也通过地面平面中的方形切口。当我们查看 [Figure 26.8](#ch26.xhtml#fig26_8)b 时，这里在 2.4 GHz 时，主表面电流也通过馈线和四分之一波长变压器的左上部以及地面中的方形切口。在 [Figure 26.8](#ch26.xhtml#fig26_8)c 中，很明显 5.8 GHz 时的主要电流分布通过馈电结构、变压器、贴片的下部、触手臂 `S1`、`S2`、`S3` 并且也通过 `S5`。[Figure 26.8](#ch26.xhtml#fig26_8)d 展示了 7.2 GHz 时的电流，其中清楚地显示电流主要分布在馈线的下部、触手臂 `S3` 并且也在地面平面中通过条带和方形槽的全长。9.9 GHz 时的电流分布主要通过馈电结构、变压器和贴片的下部，并且也通过条带切口和地面平面中的方形切口的中部。

![Figure 26.8 Surface current of the antenna at (a) 1.6 GHz, (b) 2.4 GHz, (c) 5.8 GHz, (d) 7.2 GHz and (e) 9.9 GHz.](images/fig26_8_C.jpg)

[Figure 26.8 Surface current of the antenna at (a) 1.6 GHz, (b) 2.4 GHz, (c) 5.8 GHz, (d) 7.2 GHz and (e) 9.9 GHz.](#ch26.xhtml#R_fig26_8)

### 4.3 Radiation pattern

