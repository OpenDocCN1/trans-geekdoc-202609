
# Figure 12.22 CNT-based PUF design

Even though the CNTFET has various advantages over the silicon transistors and allows more scalability, fabricating the CNTFET gives high difficulties. The planar geometry of the graphene makes it easier compared to the CNTs during fabrication and is also comparatively cheaper to silicon devices. Graphene is also compatible with the CMOS technology, which gives additional advantage of scaling and performance. Therefore, high-density SoC and higher performance can be achieved by combining the CMOS fabrication technologies with the graphene’s unique properties.

## 12.10.2 Graphene-based PUF

[Figure 12.23](#Chapter12.html#c12_fig23) shows the design of a graphene nanoribbon transistor. Graphene has high electron mobility which has an added advantage to be used as a channel in case of FETs ([Khan *et al*., 2014](#Chapter12.html#c12_bib27)). It is a two-dimensional carbon atom network which is arranged like a honeycomb lattice. Graphene is a single layer of graphite structure which is interconnected in a lattice structure. It is highly strong in all the directions. A CNT structure can be formed by rolling a graphene nanoribbon and one with 12 pentagon defects will give a fullerene structure. Properties of graphene which makes it more suitable than silicon for future technology are two-dimensional one atom crystal, light and thin material with high flexibility and strength. It is transparent and nonflammable and highly conductive.

![image](OEBPS/images/PBCS0600-12-f23.jpg)

Figure 12.23 Graphene transistor

Besides these advantages, there are also some challenges in this graphene technology: it is highly sensitive to environmental changes and does not work easily with discrete electronic signals as there is a no band gap in the semiconducting graphene structure. Unlike a silicon transistor, the graphene-based transistor cannot be turned off as the bandgap is low. But the high bandgap makes it more suitable for use in RF applications, which controls the gate current in digital logic environment. Off-state leakage currents are high, which results in smaller I[ON]/I[OFF] ratio. Saturation of drain voltage current is not readily available.

A measurement circuit is usually present in a PUF-based security modules. This can be used for measurement of the property of graphene devices such as resistance, capacitance, and voltages for deriving the output of PUF which can be used for cryptographic applications ([Dimitrakopoulos *et al*., 2012](#Chapter12.html#c12_bib12)). There are some points that should be used for graphene-based PUF designs:

1. Properties of graphene-based PUFs should be stable over a wide range of time, temperature, and other environmental variables.

2. During the fabrication process under extremely controlled conditions, there will be variations in the properties of the devices because of chemical processing, the presence of terrace edges, and growth process during growth of graphene. This results in device-to-device variations on the wafer. For the introduction of additional variations, different methods can be employed:

   * (a) Molecular doping, hydrogen inhalation, width/length scaling, contact treatments, and contact metal variation.

   * (b) Laser annealing can be introduced during the fabrication where beam width, energy, pulse duration, and wavelength can be varied.

   * (c) Contact treatment and contact metal variations.

   * (d) Different ambient conditions such as varied dopant quantities and types, oxygen levels, and so on can also introduce variations.

   * (d) For increasing the variability, a single graphene device can be packed with more layers. Which will vary the electrical properties of device.

3. For an improved stability, passivation layers can be employed, which also does not affect the security of the device during attacks based on scanning electron microscopy (SEM). A higher yield can be achieved using the passivated graphene. Resistance is inversely related to temperature in case of an unpassivated graphene device, which can reduce the resistance with the increase in temperature.

4. Array of devices that can be used for the implementation of PUF has a very low variability range almost close to threshold values of the core device used. In this case, reliability decreases with time and so will the temperature variation. This can cause to read errors while reading the output bits from the PUF module. There are also various solutions that can be implemented in this case. Some of them are:

   * (a) Error correction schemes can be employed but by sacrificing security.

   * (b) Average values of device in the array can be considered for setting the threshold value for digital fingerprint.

   * (c) Temperature-compensating algorithms can be used along with the temperature sensors for mitigating the temperature variance issues.

5. Robustness against attacks can be increased by implementing the following:

   * (a) The device location in a large array can be changed randomly which makes it difficult for the attacker to correctly give the challenge input to get an appropriate response.

   * (b) A measurement circuit can be employed on the circuitry to make it difficult for the attacker to use probes for accessing the devices.

   * (c) Delayering the measurement circuits can also be implemented, which makes the circuit more robust. This makes it difficult for the attacker to convert the read values to digital outputs. Attempting to remove the delayering will render the device useless.

## 12.11 Microprocessor-based PUF

Until now, this chapter discussed different PUF circuits that were designed for security and need to be fabricated. This section discusses different components such as microprocessor, power rail, and so on for designing PUF circuits. [Figure 12.24](#Chapter12.html#c12_fig24) shows the design of a microprocessor-based PUF ([Kumar *et al*., 2017](#Chapter12.html#c12_bib32)). Two 32-bit multiplexers and two PUF counters are used for designing the module. The output of the multiplier is connected to MUX as shown in the figure. The MUX will choose which PUF module will be driven by the bits of the multiplier. PUF counter is 32-bit long and the general-purpose registers of the microprocessor will store the 9th bit to 24th bit output from PUF counters. A 32-bit long output is generated from the two different PUF counters as shown in the figure ([Kumar *et al*., 2017](#Chapter12.html#c12_bib32)).

![image](OEBPS/images/PBCS0600-12-f24.jpg)

Figure 12.24 Microprocessor-based PUF

There are five select lines for each of the MUX for selecting the output of the multiplier. Part of the challenge input to the PUF module will be the select lines that go into the MUX. Different paths of the multiplier are selected using the assembly program, which becomes the later part of the challenge input to the PUF module. Response from the counters gets stored in the registers of the microprocessor. For an efficient CRP generation, the assembly program development is an important task. The interconnects will add delays with the manufacturing variations introduced during the fabrication stage.

In the design presented by [Kumar *et al*. (2017)](#Chapter12.html#c12_bib32), the openmsp430 design has been modified into two different modes of operation, normal and PUF. I/O pins of the microprocessor are given the 10 select lines and “En” pin. Multiplier output has been modified for generating the addition of multiplexer and PUF counter. Additional circuitry in the module will become active when the PUF mode is selected and during the normal operation, they will be separated from the microprocessor.

## 12.12 Magnetic PUF
