# 290 Hardware architectures for deep learning

![](bbox=[0.155, 0.093, 0.765, 0.313])

![](bbox=[0.075, 0.355, 0.865, 0.573])

(a) CA and (b) MSE of inverter-based memristive neuromorphic circuits in presence of process variation, input noise, and considering limited write precision of the memristor

# 11.4.4.2 Input noise

Tolerance to electrical noise is one of the important characteristics of analog circuits. To assess the effect of the electrical noise on the analog parts of the circuit, we injected a random noise with $\sigma = 30$ mV at the analog inputs of the circuit (outputs of the DAC stage) and measured the accuracy of the circuit under this condition. The results, which are shown in Figure 11.14, reveal that even in the presence of the injected noise the accuracy of the circuit remains higher than 93%. Also, the MSE remains below 0.008 for all of the applications.

# 11.4.4.3 Limited write precision

After the weights of the ANN (conductance of memristors in ANN) are determined by the training algorithm, they should be uploaded to the memristive crossbar using