
Modeling of lab scale batch reactor can be made based on a) Data driven modeling b) First principle modeling c) Hybrid modeling. Batch reactors are made of solid vessel with 316SS to avoid corrosion during various chemical reactions. It also has an integral heating and cooling systems for trajectory tracking. With respect to modeling, in general heater current will kept constant and coolant flow rate will be varied as a manipulated signal to record the open loop reaction temperature. It is mandatory to charge the batch reactor with actual chemical feed meant for the closed loop operation in order to capture the reaction dynamics properly.

Data driven modeling covers the linear and nonlinear modeling. Autoregressive recursive exogenous (`ARX`) uses the input and output data collected to form the output equation by defining the number of input and output orders If one considers the cross correlation between the input and output with defined order of input–output along with the error term, it results with Non-linear autoregressive recursive exogenous (`NARX`) modeling by Billing et al. \[[6](#ch30.xhtml#ref30_6)\]. For the data driven modeling, one must not necessarily known with the thorough knowledge of the system under consideration.

For the first principle modeling, one must know the exact dynamics of the system under study to model precisely. If there exist a model mismatch, closed loop performance validation will degrade. In order to overcome this, one can use the known parameter data from the physical batch reactor system and carry out the parameter estimation once again using data driven approach, error residuals ensure the model parameters accuracy. [Figure 30.1](#ch30.xhtml#fig30_1) shows the lab scale batch reactor and [Figure 30.2](#ch30.xhtml#fig30_2) illustrates its schematic diagram used for the controller validation.

![Figure 30.1: Experimental setup of batch reactor in advanced process control lab, ICE Dept., MIT, Manipal \[1, 2\].](images/fig30_1_C.jpg)

[Figure 30.1: Experimental setup of batch reactor in advanced process control lab, ICE Dept., MIT, Manipal](#ch30.xhtml#R_fig30_1) \[[1](#ch30.xhtml#ref30_1), [2](#ch30.xhtml#ref30_2)\].

![Figure 30.2: Schematic diagram of the batch reactor experimental setup.](images/fig30_2_C.jpg)

[Figure 30.2: Schematic diagram of the batch reactor experimental setup.](#ch30.xhtml#R_fig30_2)

### 2.3. Controller design

Control domain researchers use any random non-linear profile for simulation in closed loop for proposed control algorithms. While validating the control algorithms on a lab scale batch reactor, one must use the actual chemical feed to have a exothermic reaction, hence the optimal temperature profile formation is essential along with the terminal time. Validation of conventional controllers like proportional integral (`PI`) and its classification will result with abrupt changes in control signal. Hence, non-linear control algorithms such as non-linear model-based control (`NMBC`), non-linear model predictive control (`NMPC`) \[[6](#ch30.xhtml#ref30_6)\], `SMC` \[[8](#ch30.xhtml#ref30_8), [9](#ch30.xhtml#ref30_9), [10](#ch30.xhtml#ref30_10) and [11](#ch30.xhtml#ref30_11)\], etc. are preferred for the batch reactor trajectory tracking problems

## 3. Sliding Mode Controllers

The non-linear systems are highly affected by the disturbances and uncertainities. To control the non-linear systems, the robust controller is to be designed. The model based controller which is insensitive to parametric uncertainities and disturbance is `SMC`.

In control systems, `SMC` is a non-linear control method that alters the dynamics of a non-linear system by applying a discontinuous control signal (or more rigorously, a set-valued control signal) forces the system to “slide” along a cross-section of the system’s normal behavior. The switching control law, forces the states on the stable sliding surface. Once on this sliding surface, the states become insensitive to the disturbances and uncertainities. The `SMC` is applied for the following reasons:

*   It is a non-linear controller
*   It is insensitive to parametric uncertainties
*   It is robust controller once the states are on the sliding surface

In this work, the batch reactor systems is considered. The temperature control problem in the cooling water inlet temperature is the disturbance which may affect the batch process.

Considering the dynamic equation of the batch reactor

System equations \[[1](#ch30.xhtml#ref30_1)\]

$$\\begin{array}{l} {\\frac{d\\lbrack I\\rbrack}{dt} = - A\_{d}\\lbrack I\\rbrack e^{( - E\_{d}/R(T\_{r} + 273.15)}} \\\\ {\\frac{d\\lbrack M\\rbrack}{dt} = - A\_{d}\\left\\lbrack I \\right\\rbrack^{\\varepsilon}e^{( - E\_{d}/R(T\_{r} + 273.15)}} \\\\ {m\_{r}C\_{pr}\\frac{dT\_{r}}{dt} = R\_{p}V( - \\Delta H\_{p}) - UA(T\_{r} - T\_{J}) + Q\_{b} + Q\_{s} - Q\_{loss~}} \\\\ {m\_{r}C\_{pr}\\frac{dT\_{J}}{dt} = UA(T\_{r} - T\_{i}) - F\_{C}C\_{pc}(T\_{j} - T\_{c})} \\\\ \\end{array}$$  

Since the reactor problem is a tracking problem let us choose the sliding surface as the error equation given by

(1)

*s* = *T*[*d*] − *T*[*j*]

To reach the sliding surface

(2)

$$\\overset{˙}{s} = 0$$

Taking the derivative of (1)

(3)

$$\\overset{˙}{s} = {\\overset{˙}{T}}\_{d} - {\\overset{˙}{T}}\_{j}$$

Substituting in (2) from batch rector equation

(4)

$$\\begin{array}{l} {\\overset{˙}{s} = {\\overset{˙}{T}}\_{d} - (UA \\times (Tr - Tj) - F \\times Cpc \\times (Tj - Tc))/mjCpj} \\\\ {Td\\\_ dot - UA \\times (Tr - Tj)/mjCpj + F \\times Cpc \\times (Tj - Tc)/mjCpj = 0} \\\\ {F \\times Cpc \\times (Tj - Tc)/mjCpj = UA \\times (Tr - Tj)/mjCpj - Td\\\_ dot} \\\\ {F = \\left( {UA \\times (Tr - Tj)/mjCpj - Td\\\_ dot} \\right) \\times mjCpj/Cpc \\times (Tj - Tc)} \\\\ \\end{array}$$

The sliding surface mode control law is given by

(5)

*u* = *u*[equi ] + *u*[dicontinuous ]

Here *F* = *u[equi]*

As per the classical `SMC`, the discontinuous control is

*u*[dicon ] =  − *k**s**g**n*(*s*)

*k* is the tuning parameter

So the control law for `SMC` is

(6)

*u* = (−*k**s**i**g**n*(*s*)+*U**A*×(*T**r*−*T**j*)/*m**j**C**p**j*−*T**d*[−]*d**o**t*) × *m**j**C**p**j*/*C**p**c* × (*T**j* − *T**c*)

### 3.1. Stability of the sliding surface

The converge to the equilibrium point, the stability of the sliding surface is to be guaranteed.

Theorem: For the batch reactor of equation, the control law is given (6), which maintains the desired temperature of the reactor, in the presence of disturbances and uncertainties.

Proof: The stability of the sliding surface is proved using direct Lypunov function which is given by

(7)

$$V = \\frac{1}{2}s^{2}.$$

As the per the Lypunov stability theorem the first derivative of ([7](#ch30.xhtml#ref30_7))

(8)

$$\\overset{˙}{V} = s\\overset{˙}{s} \\leq 0$$

For the stable sliding surface

Substituting (1)(2) in (8)

(9)

$$\\begin{array}{l} {\\left( {T\_{d} - T\_{j}} \\right)\\left( {{\\overset{˙}{T}}\_{d} - (UA \\times (Tr - Tj) - u \\times Cpc \\times (Tj - Tc))/mjCpj \\leq 0} \\right.} \\\\ {\\left( {T\_{d} - T\_{j}} \\right)\\left( {{\\overset{˙}{T}}\_{d} - \\left( \\begin{array}{l} {UA \\times (Tr - Tj) - ( - ksign(s) + UA \\times (Tr - Tj)/mjCpj - Td} \\\\ {\\times mjCpj/Cpc \\times (Tj - Tc) \\times Cpc \\times (Tj - Tc)} \\\\ \\end{array} \\right)/mjCpj \\leq 0} \\right.} \\\\ \\left( {\\left( {T\_{d} - T} \\right)( - k{sign}(s)) \\leq 0} \\right. \\\\ \\end{array}$$

To satisfy the Lypunov stability condition, *k* > 0

This completes the proof.

[Figure 30.3](#ch30.xhtml#fig30_3) show the tracking of reactor temperature with coolant flow rate varying with oscillations. Objective is to reduce the control signal oscillations for energy saving in batch reactor process.

![Figure 30.3: Experimental results of closed loop sliding mode controller for trajectory tracking.](images/fig30_3_C.jpg)
