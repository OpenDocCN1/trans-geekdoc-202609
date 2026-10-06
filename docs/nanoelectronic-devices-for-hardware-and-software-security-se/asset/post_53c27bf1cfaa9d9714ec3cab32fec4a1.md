
# 3 Heterojunction Tunnel-Effect Transistor 63

One of the scaling theory's most relevant principles is that vertical and horizontal dimensions should be measured by a common scaling factor in order to prevent the leakage current and deliver efficient channel reliability. This helps to decrease the supply voltages effectively. To retain the similar features of the devices during scaling process, the doping concentration should be increased. In 1925, Lienfeld discovered the insulated gate field effect (IGFET) for the first time in the world of innovation technology. It was effectively substitute for vacuum tube technology and paved for the production of low-power semiconductor devices of small scale [11]. Kahn and Atilla were the first to provide a MOSFET made up of silicon, which was practically demonstrated in 1960 [12]. In 1958, an IC evaluation was done by Jack Rabaey and Robert Noy at Texas Instruments. The first IC was for SET-RESET (SR) flip-flop memory [13]. In 1959, Richard Feynman found in his research that “there is plenty of space at the edge” that can be efficiently further using scale in small semiconductor devices [14]. Finally, in 1965, Gordon Moore came up with the new law regulating the packing density Moore's law. He is also the cofounder of the Intel Company. To him, the device density on a microchip would double every year. In addition, the overall production cost would be halved. Moore also predict that the future technology will be enhanced following the scale in linearity. In 1962, the first logic family with TTL units was favored [14]. Intel introduced the first microprocessor, which consisted of more than 1,800 PMOS transistors, in 1972. After Intel's microprocessor, many different series of processors soon disappeared due to their heavy power consumption because of the exponential rise in chip density. However, to resolve the issue of high power consumption, CMOS technology was introduced, which was well suited for low power consumption devices. Therefore, the device technology jumped from small scale integration (SSI) to very large scale integration (VLSI). With CMOS technology, one of the most beneficial aspects was to decrease the scaling of the device to nanoscale dimensions. The International Development Roadmap for Semiconductors (ITRS) has established a scaling concept with complicated power consumption and manufacturing cost at the production stage. The roadmap by the ITRS is shown in Figure 3.1.

In addition, a wafer having the capacity of 1 TB, having more than 800 billion transistors, made by Intel called static random access memory (SRAM) [15]. Different researchers have come together in terms of reducing the dimension. In 1972, Denn and his colleagues proposed the scaling measurements [16]. New projects such as the International Roadmap for Devices and Systems (IRDS) have gained publicity following the dissolution of ITRS, as shown in Figure 3.2.

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_75_0.png)

FIGURE 3.1 Scaling for the gate length variations with respect to the ITRS years.

# 64 NanoElectronic Devices for Security

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_76_0.png)

FIGURE 3.2 IRDS 2018 projected scaling of key ground rules.

To overcome these limits, more disruptive technologies have to be developed by unconventional mechanisms and novel materials. In addition, creative circuit and system designs may take advantage of some novel features of devices unavailable in Si MOSFETs.

# 3.1.2 Challenging Issue of Scaling

The numerous explanations for carrying out miniaturization of the devices are as follows:

- Cost per transistor because nano devices occupy a small region.
- Added transistors that perform complex functions can be integrated on the same chip.
- Another low capacitance value, which reduces the power consumption required to turn the device.

Despite these benefits, scaling poses significant challenges during product manufacturing.

- Initially, the power consumption at high operating frequency is rising, which causes the chip to generate a significant amount of heat. Due to this, it is so challenging for the manufacturer to keep the IC cool for low power application. Scaling down the supply voltage ($V_{dd}$) will reduce the speed of the device. Consequently, the key goal of the system is to reduce the power consumption in a regulated way [17].
- MOSFET switching delay can be minimized by synchronizing the subthreshold voltage ($V_{th}$) of the device with the supply voltage ($V_{dd}$). However, this leads to an increase in leakage current. Therefore, scaling in the oxide thickness ($t_{ox}$) is one of the ways of reducing subthreshold voltage. Ultimately, we have to maintain the relation between the operating speed and the power consumption [18].
- Second, the scaling drawbacks due to characteristics such as subthreshold voltage, subthreshold slope, and induced barrier lowering (DIBL). It also observed from a literature survey by reducing oxide thickness, the gate-controlled-depletion-depth ($d$) will be influenced [17–19]. Below 90 nm channel, the device will not regulate the $t_{ox}$ length less than 1.2 nm, which is approximately 6 atomic layers of $SiO_2$.

# 3.1.2 Next to more than Moore's Law

With reference to the International Technology Roadmap (ITRS) data, the collective graph of digital specification and nondigital specification is shown in Figure 3.3, called 'More-than-Moore'. Downscaling offers benefits; thus, this phenomenon, known as 'More Moore', must be sustained. Therefore, the potential of nondigital technologies is significantly improved in both processing technologies and design growth.

It will also cover the nondigital analogue applications into a single package. The fully integrated systems can therefore communicate skillfully with people as well as the world. This drifting is beneficial in so-called More-than-Moore device functionality substantial [20].

# 3.1.3 Engineering Methods of the Device

# 3.1.3.1 Shallow at Source and Drain Junction

In order to reduce the barrier coupling of source and drain side, the junction depth adjacent to the gate is reduced. However, to sustain the sheet resistance, the density concentration of the source and drain side will be increased. On the other hand, doping density cannot be increased after a limit because the solid solubility of doping particles is ~10^-20 cm^-3. After execution of an annealing process to gain very low resistivity, it is not possible to have the source-drain junction by triggering the dopants [21]. The leakage current will be increases due to the abrupt junction of source and drain due to band-to-band tunneling (BTBT), which will degrade the overall performance of device.

# 3.1.3.2 Halo Doping

Several researchers are working upon the single halo (SH) and double halo (DH) technique for device modification. Although this technique improves the device performance, it is more suitable for lateral channel (LAC) devices [22]. By embedding this technique, a pinch-region is formed

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_77_0.png)

FIGURE 3.3 Graph of digital device called 'More Moore' with respect to 'More-than-Moore'.

# 66 Nanoelectronic Devices for Security

near the drain gate of the device with greater subthreshold voltage. This will improve the device drain current.

# 3.1.3.3 Strain Method

Due to scaling, the source and drain overlap each other due to reductions in the device dimensions. However, it will increase the electric field drastically. In order to overcome this problem, doping needs to be increased. But with the increase in the doping concentration in the channel, the charge particle scattering will lead to reducing the mobility. In order to reduce the mobility degradation due to charge scattering, one technique called strain technology, improves the mobility of carriers. Second, it ensures carrier traps are formed by band structure alignment, which ultimately increases the mobility [9]. By increasing the lower band gap materials are used to increase the mobility like silicon-germanium. The germanium content, will increase.

# 3.1.3.4 Multi-Material Gate

A multi-material gate is one of the most effective techniques in reducing the hot electron effect (HEE) used for the channel engineering method. The two different materials of different work function after each other; these are called tunneling gate length ($L_g$) and auxiliary gate length ($L_s$). The $M_2$ (material) of the drain side has lower work function, and the $M_1$ toward the source side has higher work function, as shown in Figure 3.4. This technique is effective for channel length less than 25 nm. In 1999, the double-material-gate design (DMG) was proposed, and in 2008, the triple-material-gate design (TMG) was proposed [23]. Dissimilar work functions at the source side and the drain side will lead to a high electric field. This will result in improving the transport efficiency of the charges of device.

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_78_0.png)

FIGURE 3.4 Dual material gate structure, where $\phi_{m1}$ > $\phi_{m2}$.
