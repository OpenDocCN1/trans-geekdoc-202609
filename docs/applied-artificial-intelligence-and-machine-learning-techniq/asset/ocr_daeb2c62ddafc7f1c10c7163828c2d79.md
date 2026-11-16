stability analysis method, we aim to provide insights into the behavior of such networks, shedding light on their stability properties and potential implications for information processing in biological and artificial systems. This investigation holds promise for elucidating fundamental principles underlying neural computation and may inform the design and optimization of neural-inspired algorithms for diverse applications ranging from pattern recognition to short-term memory (Sengupta et al., 2024; Vindhya et al., 2024).

While previous studies have focused on various applications of stability analysis methods to different forms of recurrent neural networks (Cohen and Grossberg, 1983), there remains a gap in the application of such methods to networks with sigmoid-like activation functions, particularly in the context of shunting models. Shunting recurrent networks, with their inherent balance between excitatory and inhibitory interactions, present a unique challenge for stability analysis, especially under complex input conditions like sequential and transient inputs. These networks are crucial for simulating cognitive functions such as working memory and attention, where dynamic responses to stimuli over time play a key role. Our work aims to address this gap by integrating both classical analytical stability conditions and Lyapunov-based approaches to provide a more robust understanding of the network’s stability. This is especially important in scenarios where large input sets may drive networks toward instability, as in the case of additive models prone to catastrophic inhibition. The findings from this study will contribute to a deeper understanding of the dynamic behavior of shunting networks and their relevance to modeling biological memory and cognitive systems.

# 9.2 METHODS

A recurrent on-center off-surround shunting neural network with N nodes can be described by the following dynamical equation:

```
dot{x} = \frac{dx_i}{dt} = -Ax_i + (B - x_i)\left(\sum_{k=1}^N C_{ki}f(x_k) + I_i\right) - (D + x_i)\sum_{k \neq i}^N E_{ki}f(x_k) \quad (9.1)
```

+   - x_i : Represents the membrane potential or activation level of the i -th neuron in the network. It is a function of time t .
+   - A: Represents the decay rate of the membrane potential of neuron i. It influences how fast the membrane potential of neuron i returns to its resting state in the absence of external input. It is generally kept at 1 to simulate biological neurons (Usher and Cohen, 1999).
+   - B: Represents the baseline or resting level of activation potential that neuron i tends to approach in the absence of external input.
+   - C_{ki} : Represents the weight of the excitatory connection from neuron k to neuron i. It influences how much the activation level of neuron i is influenced by the activation levels of other neurons in the network.
+   - f(x_k) : Represents the activation function of neuron k, which is applied to its membrane potential x_k . This function typically introduces nonlinearity into the network dynamics.