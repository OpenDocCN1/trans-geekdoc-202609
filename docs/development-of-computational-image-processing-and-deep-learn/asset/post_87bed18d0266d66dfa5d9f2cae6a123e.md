

![img/332d06e0447dbfd85ea7d2fb553468f3_230_0.png](img/332d06e0447dbfd85ea7d2fb553468f3_230_0.png)

**Figure 4.18:** Effect of the median blur applied to a CT scan slice of a CF-PA6 specimen. HSV color image without median filter visible in (a) and with median filter in (b).

and individual fibers are no longer included in the orientation detection at all. Since the detected fiber orientation in the CF-reinforced plates is dominated by the bundles anyway and, as will be shown later, this corresponds well with the mechanical tests, it can be assumed that this provides the more accurate solution.

The other quantitative, indirect type of validation mentioned above is the use of the extracted orientation information in mechanical homogenization models. The resulting stiffnesses or strengths can then be compared with those measured experimentally. As these experimentally measured stiffnesses were carried out with samples taken from the plates at different angles, the accuracy of the stiffness values for different orientations can be used to draw conclusions about the quality of the orientation information used in the modeling. However, since tensor interpolation was used for the orientation information of the modeling, which will not be described until the next section, the procedure and the result will be explained in more detail in Section 4.6.4 and debated in the Discussion in Section 5.4.4.5.

### 4.5.2 Characteristics of the FOD across the z-axis

The mere display of fiber orientation tensors does not appear to be useful for obtaining a comprehensive understanding of the behavior of the fiber orientation. The results over the plate (x-y plane) are therefore taken up in the visualization form of the tensor glyphs in the context of the fiber orientation interpolation in the next section. However, the behavior over the z-axis is thereby difficult to recognize, which is why characteristic curves of the three main components of the fiber orientation tensors of individual specimens were plotted in Figure 4.19 instead.

![img/332d06e0447dbfd85ea7d2fb553468f3_231_0.png](img/332d06e0447dbfd85ea7d2fb553468f3_231_0.png)

![img/332d06e0447dbfd85ea7d2fb553468f3_231_1.png](img/332d06e0447dbfd85ea7d2fb553468f3_231_1.png)

![img/332d06e0447dbfd85ea7d2fb553468f3_231_2.png](img/332d06e0447dbfd85ea7d2fb553468f3_231_2.png)

![img/332d06e0447dbfd85ea7d2fb553468f3_231_3.png](img/332d06e0447dbfd85ea7d2fb553468f3_231_3.png)

**Figure 4.19:** Main components over thickness (in slices) of specimens C2 (a) and F2 (b) of Plate 3 (CF-PA6) and of specimens C2 (c) and F3 (d) of Plate 4 (GF-PA6).

The two upper graphs show the results of CF-reinforced specimens, while the lower graphs show the results of GF-reinforced specimens. In addition, the two left-hand plots are each from a specimen in the batch area and the two right-hand plots are each from a specimen in the flow area of the plate. Clearly, an edge effect is visible in both samples in the charge region. The A22 component appears to increase at the edge of the specimen and the A11 component, which is dominant in the center of the specimen, decreases. In contrast, the curves of the main components in the flow area tend to be constant and are clearly A11-dominant. The question of whether this effect can be called the "shell-core effect", because it is reminiscent of the phenomenon of orientation components changing across the thickness in injection molding, is addressed in the Discussion in Section 5.4. It is also discussed where this changed surface orientation could stem from and, particularly, why it only occurs in the charge area but not in the flow area.

## 4.6 Interpolation of fiber orientation tensors

The results of the three methods for the interpolation of fiber orientation tensors of second-order are presented below, in the form of the tensors generated in each case, as well as a quantitative evaluation by determining individual tensors that have been measured previously. The specimens of Plate 1 were used (cf. Figure 3.4). These results have already been published in the paper [17]. The results of the slightly modified decomposition method for tensors of fourth-order are presented in the following. However, the use of these results in homogenization methods and the comparison with the experimental stiffness values is included in the Discussion (Section 5.4.4.5).

### 4.6.1 Component averaging

The set of measured orientation tensors T_in via CT scan and subsequent calculation via structure tensor is represented by the blue tensor glyphs in Figure 4.20, the set of interpolated tensors T_i = { T_xy ∀ x ∈ 1, ..., 13 ∩ y ∈ 1, ..., 13 } by the orange tensor glyphs.

The origin of the global coordinate system is located in the lower left corner of the plate. The original LFT charge covered almost the entire left side of the 400 mm x 400 mm mold with a width of about x = 90 mm (to the right), a length of about y = 350 mm (up) and a height of about z = 60 mm. Thus, when the press closes, one would expect a quasi 1D flow to the right. However, in Figure 4.20 a clear progression can be seen in the measured (blue) fiber orientation.

![img/332d06e0447dbfd85ea7d2fb553468f3_233_0.png](img/332d06e0447dbfd85ea7d2fb553468f3_233_0.png)

**Figure 4.20:** Visualization of interpolated (orange) and measured (blue) tensors when using the component averaging interpolation method described in this thesis. Extracted from Barr et al. [17].

After a clear preferred direction in the left region resulting from the plastificate, i.e., from the last extrusion step in the LFT-D process, a turn to a rather dominant orientation in the x-axis seems to have towards the middle of the plate (apart from the top region). At the right side another turn to an again more y-direction-dominant orientation happens (apart from the lowest tensor glyph, which in general seems to be more isotropic than the other tensors). Considering these measured tensors, the interpolated tensors should follow some kind of curve. In fact, the interpolation does not seem to cover this behavior smoothly but instead rather accomplished the orientation changes through rounding the tensors. Following the literature, this behavior was expected (cf. swelling effect in the State of Art (Section 2.2.3.3)) and can be confirmed.

In order to be able to approach quantitative error analyses and to better assess the interpolation behavior, one measured tensor of T_m was omitted in each case and instead also determined with the interpolation method. The visualization results are shown in the nine pictures in Figure 4.21.

To obtain a quantitative error value, the Frobenius norm of the measured tensors and their respective interpolated substitutes was formed. The result of the difference between the Frobenius norm of the interpolated and the original tensor can be seen as an error map in Figure 4.22. The method seems to predict the MM, LM and LL tensors the worst. It is difficult to judge whether the Frobenius norm is suitable as a quantitative assessment, but it will be discussed further in the Discussion.

Therefore, a third possibility of error analysis is considered, namely the direct component comparison between interpolated and measured tensors. Figure 4.23 shows this for the component averaging method.

The nine graphs in Figure 4.23 correlate to the nine different tensor components of a 3 x 3 tensor. Each graph shows the component value of the measured tensors in blue and of the interpolated tensors in orange on the y-axis for each of the nine measured tensors (depicted on the x-axis, starting with UL). While the differences are largest for the components with the largest values and fluctuations

![img/332d06e0447dbfd85ea7d2fb553468f3_235_0.png](img/332d06e0447dbfd85ea7d2fb553468f3_235_0.png)

**Figure 4.21:** The graphic shows the measured (blue) and interpolated (orange) fiber orientation tensor glyphs when leaving one measured tensor out of the calculation and interpolating it instead with the component averaging method respectively. Extracted from Blarr et al. [17].

(mainly $A_{11}$ and $A_{22}$), the character of the component averaging method is also clearly evident in this type of error analysis. Thus, the components of the interpolated tensors almost resemble a moving average of the components of the measured tensors.

