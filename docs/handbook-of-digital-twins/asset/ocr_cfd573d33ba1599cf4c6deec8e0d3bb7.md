# TABLE 46.1
Accuracy of the Artificial Neural Networks-Based Digital Twin for State Estimation

| Voltage | Error in % | Bus 5 | Bus 7 | Bus 9 |
|---|---|---|---|---|
| Amplitude | Maximum | 0.22 | 0.18 | 0.23 |
| | Average | 0.08 | 0.06 | 0.07 |
| Angle | Maximum | 0.32 | 0.39 | 0.38 |
| | Average | 0.09 | 0.05 | 0.07 |

state estimation. Table 46.1 shows that the maximal error is at angle estimation of bus 7, which is smaller than 0.4%.

An ANNs-based DT for state estimation is presented in this section. The result shows that training with enormous measurement data in appropriate architectural setup ANNs, we can gain an accurate and reliable DT for fast state estimation. Compared to the DT in the last section, which is constructed based on the differential equations, the training effort in the ANNs-based DT is significantly reduced. However, the DT introduced in this section is remarkable for the state estimation. Another type of DT is presented in the next section, which is used to design its corresponding controller.

# 46.3.2 Data-Driven DT for Controller Design

As known, a DT can also be applied in designing a controller for smart grid devices. This section introduces a data-driven DT construction of a basic DC/DC boost converter, and its controller is designed accordingly based on this DT. Power converters are becoming critical in smart grids with the penetration of renewable energy in the electrical grid. A boost converter is required to increase the input voltage to the desired output voltage to connect a fuel cell or a photovoltaic into a power network. A DC/DC converter consists of an input dc voltage source Vin, an inductor L, a controlled switch S with switching period T, a diode, a capacitor C for filtering and a resistor R representing a load. The switching characteristics cause non-linearity in the converter model, leading to a complexity in the control design. The first step should be the construction of the converter model to derive a proper control technique. Due to the complexity of the interconnections between the components within the commercial DC/DC converter and the fact that some important parameters are kept unknown to protect the manufacturer’s profits, its modelling is also considered a challenging task. Therefore, the local model network (LMN) technique for the converter’s data-driven DT is introduced.

# 46.3.2.1 Local Model Networks

LMN is a notion for the integration of multiple local linear models (LLMs). It represents a globally complex non-linear model and provides a flexible