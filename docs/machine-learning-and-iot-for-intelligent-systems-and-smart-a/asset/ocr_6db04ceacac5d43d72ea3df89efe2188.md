linear and nonlinear loads. It was found on comparison about performance of controllers with simulation and experimental results were not matched.

Ammar Hussein Mutlag et al. [4] designed Adative Fuzzy Logic Controller design method with PV system using Differential Search Algorithm. The amplitude and frequency were improved using optimized output of DSA. The design and accuracy results of the fuzzy logic controller were not accurately discussed. Remus Narcis Beres et al. [5] have developed and implemented three-phase grid tied inverter operated as Voltage Source Inverter. Switching sequence of the inverter was operated using PWM controller.

Xu Renzhong et al. [6] have presented the three phase PV based grid tied LCL filter. The design and modeled equations were used to calculate the L and LCL component values. The static and dynamic performances of the LCL filter connected inverter were not presented. Lin Chen et al. [7] have described the three phase two stage grid connected with an LC filter. The proposed technique was used to reduce the charge per watt and boost the scalability of the system. The developed ZVS technique with two stage grid connected system did not provide better consistency results.

Nascimento Filho et al. [8] have designed new methodology for current controller and DC tied voltage controller with LCL output filter. Only the dynamic behavior of the inverter was presented, because it failed to present the static results. Sandeep et al. [9] have demonstrated the design of single-phase grid tied PV based system. The inverter was operated using current feedback controller for active damping. The design procedure of the current injected in grid was presented. The current and voltage controller are used for the closed loop operation. Also, active and passive filter with LCL filter were given. Panda et al. [10] have discussed the single-phase grid connected system. PLL controller is applicable for the closed loop operation and Dual Transport Delay Based PLL (DTDPLL) technique was used. [11–14]

It was inferred that due to switching, sufficient accuracy results were also not obtained. Voltage regulation plays a significant role in single-phase inverter with LCL output filter [15–18].

# 3.3 PROPOSED SYSTEM

In the first stage, the PV panel provides DC power supply and it is fed to the converter. The converter boosts the PV power which is fed to the single-phase full bridge inverter. In the next stage, using inverted gate switching pulse, conversion of DC to AC voltage happens. The phase output voltage of inverter is coupled with LCL-T filter, as shown in Figure 3.1.

The switching frequency can control the output voltage as the phase difference varies between the inverters. Instantaneous power from PV panel is found by Maximum Power Point Tracking Algorithm. (Trabelsi et al. 2011). When PV panel voltage is greater than reference voltage, the DC-link regulator output voltage gets increased which results in large current flow.

Figure 3.2 shows inverter fed grid. The resonant converter circuit consists of inductance $L_{S1}$, capacitor $C_{P}$ and series inductance $L_{S2}$. $M_{1}$–$M_{4}$ is switching device