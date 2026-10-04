
[Figure 30.3: Experimental results of closed loop sliding mode controller for trajectory tracking.](#ch30.xhtml#R_fig30_3)

Hence, `SMC` control law need to be modified for better control signal.

### 3.2. Power rate reaching law

As compared to the classical `SMC`, reaching the law is as per equation 6, which has lot of chattering as shown in [Figure 30.4](#ch30.xhtml#fig30_4). By introducing the `α`, `0 ≤ α ≤ 1`, the states reach the sliding surface in the non-linear path, which increases the settling time and reduces chattering. The control law with power rate reaching law is as per equation.

![Figure 30.4: Experimental results of closed loop power rate reaching law sliding mode controller for trajectory tracking.](images/fig30_4_C.jpg)

[Figure 30.4: Experimental results of closed loop power rate reaching law sliding mode controller for trajectory tracking.](#ch30.xhtml#R_fig30_4)

$$F = \\left( - k\\overset{˙}{s} = - k \\middle| s \\middle| {}\_{\\infty}{sgn}(s) + \\frac{\\text{UA}\\left( {\\text{Tr} - \\text{Tj}\_{j}} \\right)}{\\text{mjCpj} - \\text{Td}\_{\\text{j}}} \\times \\frac{mj\\text{Cpj}}{\\text{Cpc}\\left( {T\_{j} - Tc} \\right)} \\right.$$

[Figure 30.4](#ch30.xhtml#fig30_4) response of trajectory tracking resulted with slight oscillations throughout the trajectory tracking with high consumption of the coolant flow rate. This shows `SMC` control algorithm need to be revised to improve the closed loop response.

### 3.3. PI sliding surface

The switching control law is designed, where the sliding surface is selected as the proportional derivative controller, which eliminated the offset and provides good tracking. Since the application of the batch reactor, is to track the temperature, the error equation is the sliding variable. The use of power rate reaching laws is used as the reaching equation, for fast convergence. The equation of `PI` controller

`K = kpep + kpki∫epdt + P1(0)`

Therefore selecting the error `ep = Td - Tj`

Substituting in `PI` equation, the sliding surface is as below

$$\\overset{˙}{s} = kp\\left( {{\\overline{\\text{T}}}\_{\\text{d}} - {\\overset{˙}{\\text{T}}}\_{\\text{j}}} \\right) + \\text{kpki}\\left( {\\text{Td} - \\text{T}\_{\\text{j}}} \\right)$$

by taking the derivative of the sliding surface, we get

$$\\overset{˙}{s} = kp(\\overset{˙}{T}d - \\overset{˙}{T}j) + kpki(Td - Tj)$$

to ensure state reach the sliding surface, equating or the reaching law equation

$$\\begin{array}{l} \\left. \\overset{˙}{\\text{s}} = - \\text{k} \\middle| \\text{s} \\middle| {}\_{\\infty}{sgn}(\\text{s}) \\right. \\\\ {\\overset{˙}{s} = kp\\left( {{\\overset{˙}{T}}\_{d} - \\left( U\_{A}\\left( {T\_{r} - T\_{j} - \\frac{FC\_{p}c\\left( {T\_{j} - T\_{c)}} \\right)}{m\_{j}C\_{pj}}} \\right) + kpk\_{i}\\left( {T\_{d} - T\_{i}} \\right) = - k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) \\right.} \\right.} \\\\ \\left. - k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) = kp{\\overset{˙}{T}}\_{d} - \\frac{kpU\_{A}\\left( {T\_{r} - T\_{i}} \\right)}{m\_{j}C\_{pj}} - \\frac{k\_{p}FC\_{pc}\\left( {T\_{j} - T\_{c}} \\right)}{m\_{j}C\_{pj}} + kpk\_{i}\\left( {T\_{d} - T\_{j}} \\right) \\right. \\\\ \\left. \\frac{k\_{p}FC\_{pc}\\left( {T\_{j} - T\_{c}} \\right)}{m\_{j}C\_{pj}} = kp{\\overset{˙}{T}}\_{d} - \\frac{kpU\_{A}\\left( {T\_{r} - T\_{i}} \\right)}{m\_{j}C\_{pj}} + kpk\_{i}\\left( {T\_{d} - T\_{i}} \\right) + - k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) \\right. \\\\ \\end{array}$$

by arranging terms we get the control law as follows:

$$F = \\left( kp{\\overset{˙}{T}}\_{d} - \\frac{kpU\_{A}\\left( {T\_{r} - T\_{j}} \\right)}{m\_{j}C\_{pj}} + kpk\_{i}\\left( {T\_{d} - T\_{i}} \\right) + k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) \\right)\\left( \\frac{m\_{j}C\_{pj}}{k\_{p}C\_{pc}\\left( {T\_{j} - T\_{c}} \\right)} \\right)$$

[Figure 30.5](#ch30.xhtml#fig30_5) shows the proper tracking with reduced oscillations compared to previous other two `SMC` results shown in [Figures 30.3](#ch30.xhtml#fig30_3) and [30.4](#ch30.xhtml#fig30_4). The coolant flow rate consumption is also optimal compared to other two `SMC`s.

![Figure 30.5: Experimental results of closed loop PI sliding surface based sliding mode controller for trajectory tracking.](images/fig30_5_C.jpg)

[Figure 30.5: Experimental results of closed loop PI sliding surface based sliding mode controller for trajectory tracking.](#ch30.xhtml#R_fig30_5)

The improvement in the results of the paper can be compared with the experimental results of conventional `PID` controllers carried out on the same batch reactor setup. It was observed that the control signal of `NPID` [[12](#ch30.xhtml#ref30_12), [13](#ch30.xhtml#ref30_13) and [14](#ch30.xhtml#ref30_14)] was very much oscillatory compared to the experimental results of the `SMC` results shown in [Figure 30.3](#ch30.xhtml#fig30_3), [Figure 30.4](#ch30.xhtml#fig30_4) and [Figure 30.5](#ch30.xhtml#fig30_5)

### 3.4. Jetson board for control signal computation

Presently the authors are working to execute the advanced control algorithm using `Jetson` developer kit with real time batch rector. Proper signal conditioning of sensors and actuators needs to be carried using current to voltage convertor and voltage to current convertor. `Jetson` board does not have the analog to digital convertor (`ADC`), hence additional `ADC` need to be used for interfacing sensor and actuator signals. The advanced control algorithm is developed using `Python` code. The `GPIO` pins needs to be configured for the sensor and actuator signals interface. The advantage of using this `Jetson` will increase the computation time of control signals for the highly nonlinear control algorithms with hard constraints to interface with the batch reactor ([Figure 30.6](#ch30.xhtml#fig30_6)).

![Figure 30.6: Jetson developer kit for control algorithm execution in advanced process control lab, MIT, Manipal for batch reactor.](images/fig30_6_C.jpg)

[Figure 30.6: Jetson developer kit for control algorithm execution in advanced process control lab, MIT, Manipal for batch reactor.](#ch30.xhtml#R_fig30_6)

## 4. Conclusions

In this article class of `SMC` has been designed using the non-linear model equations of batch reactor. Three different types of controller were simulated and validated on the experimental setup for the temperature. The experimental results show that the `PI` sliding surface based `SMC` gives the least manipulated variable action, it means the lowest amount cooling water is utilized for temperature tracking. On other hand if we look that the tracking error, basic `SMC` helps, but in this case the optimal control signal was not obtained. Hence, based on the tracking error or the optimal control signal is needed has to be decided for the selection of control algorithms.

## 5. Acknowledgement

The authors would like to thank Manipal Academy of Higher Education, Manipal for the seed money grant received toward the coolant flow station establishment for the batch reactor under Grant ID: `00000220` dated `01/01/2020` and Grant ID: `00000860` dated `09/10/2023` towards the machine learning concept implementation on batch reactor.

## References

1. [Shettigar J. P.](#ch30.xhtml#R_ref30_1), Lochan, K., Jeppu, G., Palanki, S., and Indiran, T. (2021). Development and validation of advanced nonlinear predictive control algorithms for trajectory tracking in batch polymerization. ACS Omega, 6, 22857–22865.

2. [Shettigar J](#ch30.xhtml#R_ref30_2), P., Kumbhare, J., Yadav, E. S., and Indiran, T. (2022). Wiener neural network-based modeling and validation of generalized predictive control on a laboratory-scale batch reactor. ACS Omega, 7, 16341−16351.

3. [Urmila, D. and Pahola, T. B.](#ch30.xhtml#R_ref30_3) (2011). Optimal control of biodiesel production in a batch reactor Part II: Stochastic control. Fuels, 94, 218-226.

4. [Palanki, S.](#ch30.xhtml#R_ref30_4) (2005). Optimal operations of semi-batch processes with a single reaction. Int. J. Chem. React. Engg., 3(1), 1-9.
