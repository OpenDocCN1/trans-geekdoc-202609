
### 3.5.1 HARDWARE IMPLEMENTATION OF TWO STAGE SINGLE PHASE LCL-T INVERTER

Figure 3.25 shows that the waveform of current is sinusoidal and less harmonic which makes turn-off switching loss as reduced component.

The inverter current and voltage of the grid are in phase and has power factor = 1. The grid inductor current ($L_G$) and grid side capacitor voltage ($V_{CF}$) along grid are shown in Figures 3.25 and 3.26, respectively, using FFT spectrum analysis.

![](img/93c6e2919cb9917d1bdd8f6271e04df4_67_0.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_67_1.png)
FIGURE 3.23 (a) Experimental model with solar panel. (b) Assembled parts and recording of outputs using oscilloscope.

![](img/93c6e2919cb9917d1bdd8f6271e04df4_67_2.png)
FIGURE 3.24 Driving pulses.

![](img/93c6e2919cb9917d1bdd8f6271e04df4_68_0.png)
**FIGURE 3.25** CH1: Grid current (Amp. Scale: 10A/div.), and CH2: Inverter output voltage (Volt. Scale: 15V/div.)

![](img/93c6e2919cb9917d1bdd8f6271e04df4_68_1.png)
**FIGURE 3.26** CH1: Grid voltage (Volt. Scale: 15V/div.), and CH2: inverter voltage (Volt. Scale: 15V/div.).

The inductor current waveform shown in Figure 3.27 is taken using Agilent Mixed Signal Storage Oscilloscope. The Figure 3.28 shows the FFT spectrum of the current across the inductor. It is clearly observed from Figure 3.29 the inductor current and capacitor voltage possess little oscillation and sinusoidal shape is improved. The grid side inductor current contains the harmonics of 3.22%.

The proposed FANN controller performance along output voltage of inverter with grid disturbance is shown in Figure 3.29. During the working of inverter, the grid contains 5 percentages of third order harmonics at 0.06 seconds. The settling time is 0.08s for closed loop system and overshoot is 0.84 V with better accuracy. Figure 3.30 shows the inverter output current with FFT analysis.

![](img/93c6e2919cb9917d1bdd8f6271e04df4_69_0.png)
**FIGURE 3.27** CH2: Grid inductor current (Amp. Scale: 2A/div.).

![](img/93c6e2919cb9917d1bdd8f6271e04df4_69_1.png)
**FIGURE 3.28** FFT for grid inductor current.

![](img/93c6e2919cb9917d1bdd8f6271e04df4_70_0.png)
**FIGURE 3.29** CH2: Output current of the inverter with FANN controller, grid disturbance at 0.06 seconds (Amp. Scale: 0.5A/div.).

![](img/93c6e2919cb9917d1bdd8f6271e04df4_70_1.png)
**FIGURE 3.30** FFT for output current of the inverter.

Figure 3.31 shows the grid connected steady state error of the inverter output voltage. The graph representing the peak overshoot output voltage is about 1.2%, and the total harmonic distortion is about 4.25%.

The transformer primary and secondary voltages are presented in Figures 3.32 and 3.33, respectively. When voltage and current are minimum, power loss occurs during ON period and maintained low during inverter operation.

![](img/93c6e2919cb9917d1bdd8f6271e04df4_71_0.png)
**FIGURE 3.31** CH2: Steady state error for output voltage (Volt. Scale: 20V/div.).

![](img/93c6e2919cb9917d1bdd8f6271e04df4_71_1.png)
**FIGURE 3.32** CH1: Transformer voltage on primary side (Volt. Scale: 10V/div.).

The grid inverter output current response under light load and over load conditions are shown in Figure 3.34 and Figure 3.35 respectively. The grid connected inverter operating under both conditions are tested with proposed FANN controller and presented in Figure 3.35.

A 2 $\Omega$ resistive load is chosen for maximum load conditions. The oscillation and settling time of the current is better with minimum steady state error. The Table of

![](img/93c6e2919cb9917d1bdd8f6271e04df4_72_0.png)
**FIGURE 3.33 CH1: Transformer voltage on secondary side (Volt. Scale: 20V/div.)**

![](img/93c6e2919cb9917d1bdd8f6271e04df4_72_1.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_72_2.png)
**FIGURE 3.34 CH1: Grid output current under load conditions (FANN Controller) (Amp. Scale: 2.0A/div.)**

LCL-T filter in Table 3.4 shows that the control characteristics match with theoretical values. The Table 3.5 shows the performance of the simulation and experimental results under various load conditions. The results prove the efficiency of the controller.

Table 3.5 representing elimination of percentage overshoot and THD is less using FANN control system based on LCL-T filter design under single phase grid connected mode.

![](img/93c6e2919cb9917d1bdd8f6271e04df4_73_0.png)
**FIGURE 3.35** CH1: Inverter output current under load conditions (FANN Controller) (Amp. Scale: 2.0A/div.)

**TABLE 3.4** **Comparative analysis of the LCL-T filter inverter during grid connected mode**

| Performance Measures | Simulation Result | | Experimental Results | |
| :--- | :---: | :---: | :---: | :---: |
| | Light Load | Over Load | Light Load | Over Load |
| Inverter Current in RMS | 7.35 | 7.35 | 7.46 | 7.46 |
| Grid Current in RMS | 1.8 | 6.9 | 1.8 | 12.68 |
| Load Current in RMS | 5.4 | 13.9 | 5.68 | 6.25 |

**TABLE 3.5** **Performance measures of simulation and experimental results**

| Performance Measures | Simulation Results | | | Experimental Results | | |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| | No Load | Light Load | Over Load | No Load | Light Load | Over Load |
| Settling Time in s | 0.005 | 0.005 | 0.005 | 0.06 | 0.069 | 0.081 |
| Rise Time in Sec | 0.02 | 0.03 | 0.035 | 0.05 | 0.052 | 0.054 |
| Percentage overshoot in Volt | 0.49 | 0.5 | 0.51 | 0.72 | 0.84 | 0.89 |
| Steady state error in Volt | 0.2 | 0.23 | 0.25 | 0.89 | 0.9 | 1 |
| THD | 2.0 | 2.4 | 2.42 | 3.9 | 4.21 | 4.3 |

### 3.6 CONCLUSION

An analytical and design methodology of the Fuzzy tuned Artificial Neural Network (FANN) controller for grid connected two stage single phase inverter with LCL-T filter has been presented using closed loop operation.

The performance of inverter was found to be better for fuzzy tuned Artificial Neural Network LCL-T designed filter inverter, and it gives better results compared to the traditional inverter using PID controller.

Harmonic distortion in total (THD) for output inverter voltage was about 5%.

The steady state stability analysis of the proposed system was analyzed using state space equations and simulation was done using MATLAB. The controller performance was compared with conventional controller (PID). Finally, the simulated results showed that the closed loop controller based Fuzzy tuned Artificial Neural Network (FANN) yielded better control strategies. A model of single phase 300 W, 50 Hz inverter was designed and demonstrated. The harmonics spectrum analysis was presented, and the conclusion is that the Fuzzy tuned Artificial Neural Network (FANN) controller performance was better under both conditions.

# REFERENCES

- [1]. Chen Chen, Jian Xiong & Zhiqiang Wan 2017, ‘A Time Delay Compensation Method Based on Area Equivalence for Active Damping of an LCL-Type Converter’, IEEE Transactions on Power Electronics, vol. 32, no. 1, pp. 762–772.

- [2]. Mahesh Kumar, Suresh Chandra Srivastava & Sri Niwas Singh 2015, ‘Control Strategies of a DC Microgrid for Grid Connected and Islanded Operations’, IEEE Transactions on Smart Grid, vol. 6, no. 4, pp. 1588–1601.

- [3]. Claudio A. Busada, Sebastian Gomez Jorge & Jorge A Solsona 2015, ‘Full-State Feedback Equivalent Controller for Active Damping in LCL-Filtered Grid-Connected Inverters Using a Reduced Number of Sensors’, IEEE Transactions on Industrial Electronics, vol. 62, no 10, pp. 5993–6002.

- [4]. Ammar Hussein Mutlag, Hussain Shareef, Azah Mohamed, Mohammed Abdul Hannan & Jamal Abd Ali 2014, ‘An Improved Fuzzy Logic Controller Design for PV Inverters Utilizing Differential Search Optimization’, International Journal of Photo Energy, vol. 2014, Article ID 469313, pp. 1–14.

- [5]. Remus Narcis Beres, Xionggie Wang, Marco Liserre, Frede Blaabjerg & Claus LethBak 2016, ‘A Review of Passive Power Filters for Three-Phase Grid-Connected Voltage-Source Converters’, IEEE Journal of Emerging and Selected Topics in Power Electronics, vol. 4, no. 1, pp. 54–69.

- [6]. Xu Renzhong, Xia Lie, Zhang Junjun & Ding Jie 2013, ‘Design and Research on the LCL Filter in Three-Phase PV Grid-Connected Inverters’, International Journal of Computer and Electrical Engineering, vol. 5, no. 3, pp. 322–325.

- [7]. Lin Chen, Ahmadreza Amirahmadi, Qian Zhang, Nasser Kutil & Issa Batareseh 2014, ‘Design and Implementation of Three-Phase Two-Stage Grid-Connected Module Integrated Converter’, IEEE Transactions on Power Electronics, vol. 29, no. 8, pp. 3881–3892.

- [8]. Paul Sergio Nascimento Filho, Tarcio Barros Dos Santos Barros, Marcos Vilalva & E Ruppert Filho 2014, ‘Design methodology of P-res controllers with harmonic compensation for three-phase DC-AC grid-tie inverters with LCL output filter’, 2014 IEEE 15th Workshop on Control and Modeling for Power Electronics (COMPEL), Santander-Spain.
