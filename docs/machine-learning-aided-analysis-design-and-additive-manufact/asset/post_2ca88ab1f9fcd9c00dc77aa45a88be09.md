
## 5.3.4.1 Steady-state response

First, the dynamic characteristic analysis model established in this chapter is verified by comparing with the results obtained from the commercial finite element modeling software ABAQUS. Fig. 10 presents the steady-state response results of the FGP cylindrical shell with CCCC boundary condition. The cylindrical shell is excited by rectangular pulse in the region [0,2.0]x[0,2.5] and the related parameters are defined as: a=1 m, b=1 m, h=0.1 m, $R_x=\alpha_x$, $R_z=2$, $e_0=0.2$. Points (0.3, 0.3) and (0.5, 0.5) on the shell are as response detection points. The frequency interval is set [500, 4000] Hz and the frequency interval $\Delta f$ is 1 Hz. Similarly, Fig. 11 shows the comparison of the FGP hyperbolic parabolic shell and for forced vibrations of functionally graded porous shallow shells on elastic foundation and the parameters used in the model are almost none as those used in the model in Fig. 5.10 except the observation point selected here is (0.2, 0.5) and (0.5, 0.5) and $R_x=-2, R_z=2$. As shown in Figs. 5.10 and 5.11, the results of the proposed model agree extremely well with ABAQUS.

Fig. 5.12 depicts the effect of the porosity coefficient on shallow shell which rests on different elastic foundations. The response parameters are used as the same in Fig. 5.11. For the sake of facilitating analysis, four foundation parameters of ($K_p, G_p$) = (0,0), (10,0), (100,0), (100,100) and five porosity coefficients of $e_o = 0, 0.2, 0.4, 0.6, 0.8$ are used in the analysis. The results in Fig. 5.12 shows that the response curves of different structures under the same parameter configurations share the similar trends. In addition, it can be found through comparison that the influence of porosity coefficient on the steady-state response related to the first resonance peak is not obvious, and the number of resonances does not change much in the analyzed frequency. However, in the high frequency interval the resonances corresponding to the steady-state responses shift significantly with $e_o$.

![](img/90ed165a39fa708ec438fcda79319c25_170_0.png)

**Fig. 10** Comparison of the steady-state response of the functionally graded porous shell with CCCC boundary condition between the results from ABAQUS and present method (a=1 m, b=1 m, h=0.1 m, $R_x=\alpha_x$, $R_z=2$, $e_0=0.2$, $f=500–4000$ Hz, $\Delta f=1$ Hz). (A) Point A: (0.3, 0.3); (B) Point B: (0.5, 0.5)

![](img/90ed165a39fa708ec438fcda79319c25_170_1.png)

**Fig. 11** Comparison of the steady-state response of the functionally graded porous hyperbolic parabolic shell with CCCC boundary condition between the results from ABAQUS and present method (a=1 m, b=1 m, h=0.1 m, $R_x=-2$, $R_z=2$, $e_0=0.2$, $f=500–4000$ Hz, $\Delta f=1$ Hz). (A) Point A: (0.2, 0.5); (B) Point B: (0.5, 0.5)

![](img/90ed165a39fa708ec438fcda79319c25_171_0.png)

**Figure 5.12** Effect of porosity coefficients of Type 1 on a shallow shell with the variations of the Winkler–Pasternak foundations under CSCS boundary condition: (A) $R_x=\infty, R_z=2$; (B) $R_x = 2, R_z = 2$; (C) $R_x = 2, R_z = -2$.

![](img/90ed165a39fa708ec438fcda79319c25_172_0.png)

**Fig 5.13** Effect of boundary conditions of Type 1 with variations of the Winkler-Pasternak elasticity with $e_o = 0.2$.

Fig. 5.13 depicts the steady-state responses of shallow shell under different boundary conditions resting on different elastic foundation and the preset parameters are the same as used in Fig. 5.10. Clearly, the steady-state responses are sensitive to changes in elastic foundations and boundary conditions. Specifically, since changes in elastic foundation parameters within a certain range can lead to changes in system stiffness, the response resonance peaks are shifted to different degrees. Similar to the effect of elastic foundation parameters, changes in $R_w = 0, R_t = 2$ and $R_w = 2, R_t = -2$ can also cause changes in resonant frequencies for shallow shell. Also, it can be found that, for analysis bands of interest, the number of resonance peak under the CCCC boundary condition is the least, while the most number is found for the SFS boundary condition.

![](img/90ed165a39fa708ec438fcda79319c25_173_0.png)

![](img/90ed165a39fa708ec438fcda79319c25_173_1.png)

![](img/90ed165a39fa708ec438fcda79319c25_173_2.png)

**Fig 5.14** shows the effect of the ratio of thickness-radius ratio $h_t$ on the steady-state response with CCCC boundary condition, $(\tilde{K}_w, \tilde{K}_t) = (100, 100)$, $\epsilon_0 = 0.2$, observation location (0, 0.5).

Fig. 5.14 depicts the thickness-radius ratio $h_r$ ($h_r/R_o$) on the steady-state responses. The parameters used are basically the same as those in 5.10, except for the boundary condition applied to each structure. They are all located at the elastic boundary $(K_t, G_t)=(100, 100)$. The porosity coefficient is set as $e_0=0.2$ and the observation point is taken as (0.5, 0.5).

![](img/90ed165a39fa708ec438fcda79319c25_174_0.png)

**Figure 5.15** Comparison of the transient-response of the Type 1 functionally graded cylindrical shell with CCCC boundary condition between the results from ABAQUS and present method (a=1 m, b=1 m, h=0.1, $R_o=$, $e_0=0.2$, $t=0.01$ s, $\Delta t=0.02$ ms). (A) Point A: (0.3, 0.3); (B) Point B: (0.5, 0.5)

![](img/90ed165a39fa708ec438fcda79319c25_174_1.png)

**Figure 5.16** Comparison of the transient-response of the Type 1 functionally graded hyperbolic shell with CCCC boundary condition between the results from ABAQUS and present method (a=1 m, b=1 m, h=0.1, $R_o=-2$, $e_0=0.2$, $t=0.01$ s, $\Delta t=0.02$ ms). (A) Point A: (0.2, 0.5); (B) Point B: (0.5, 0.5)

As seen from Fig. 5.14, the influence of $h_Rs$ on the steady-state responses is very significant. Specifically, as the ratio of thickness to radius increases, the steady-state responses will gradually shift to the high frequency. The number of resonance peaks in the same frequency range decrease. In addition, it can be noted that, to the structural growth caused by the ratio of thickness to radius, the displacement responses can be suppressed.

![](img/90ed165a39fa708ec438fcda79319c25_175_0.png)

**Figure 5.17** the effect of the loads on the transient-state response of the functionally graded shell with CCCC, $(\tilde{K}_w, \tilde{K}_s)=(100, 100), \epsilon_0=0.2, h =0.1$: (A) $R_s=\infty, R_z=2$; (B) $R_s=2, R_z=2$; (C) $R_s=2, R_z=-2$.

## 5.3.4.2 Transient-state response

To further investigate the transient responses of the system, the current method must be verified first. Figs. 5.15 and 5.16 show the comparisons of the transient-state responses of FGP cylindrical and hyperbolic parabolic shells with CCCC boundary condition between the proposed method and finite element model (ABAQS). The parameters are set as $\epsilon_0=0.2, a=b=1$ m, h=0.1$ m, R_s=2$. Loads are imposed on the region of $[0.2,0.5] \times [0.2,0.5]$. Points $(0.3, 0.3)$ and $(0.5, 0.5)$ for cylindrical shells, $(0.2, 0.5)$ and $(0.5, 0.5)$ for the parabolic shallow shell are selected as observation points. The pulse width is $0.01$ s and $R_t=2, R_z=2$.

![](img/90ed165a39fa708ec438fcda79319c25_176_0.png)

![](img/90ed165a39fa708ec438fcda79319c25_176_1.png)

![](img/90ed165a39fa708ec438fcda79319c25_176_2.png)

**Figure 5.18** The effect of elastic foundation on the transient-state response of the functionally graded shallow shell with SSSS, $e_0 = 0.2, h = 0.1$.

**Figure 5.19** The effect of the ratio of thickness-radius ratio $h_t$ in the transient-state response of the functionally graded porous shell with CCCC, $\epsilon_0=0.2, (\bar{K}_w, \bar{K}_s)=(100, 100)$.

![](img/90ed165a39fa708ec438fcda79319c25_177_0.png)

![](img/90ed165a39fa708ec438fcda79319c25_177_1.png)

![](img/90ed165a39fa708ec438fcda79319c25_177_2.png)

![](img/90ed165a39fa708ec438fcda79319c25_177_3.png)

![](img/90ed165a39fa708ec438fcda79319c25_177_4.png)

![](img/90ed165a39fa708ec438fcda79319c25_177_5.png)
