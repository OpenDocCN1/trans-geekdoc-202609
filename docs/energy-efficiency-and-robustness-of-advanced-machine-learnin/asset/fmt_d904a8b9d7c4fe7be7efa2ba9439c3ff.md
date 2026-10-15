
A neuron is considered the simplest computational knob in an SNN. When a spike coming from a presynaptic neuron arrives at the input of the postsynaptic neuron, the spiking current injected into the neuron's body, associated with the synaptic weight, is integrated into the membrane, thus contributing to raising its membrane potential. Several neuron models have been proposed in the literature, and this section provides an on the most common models employed for SNNs.

The `McCulloch-Pitts neuron` \[[169](#refbib.xhtml#refbib169)\] is the predecessor model for the neural networks. It simply computes the sum of the incoming spikes and emits the boolean output 1 (fires) if the sum is higher than its threshold or 0 otherwise. Its main drawback consists of its inability to learn. To overcome this issue, the `perceptron` model \[[230](#refbib.xhtml#refbib230)\] was proposed. It introduces the concept of learnable weights that are multiplied by the boolean outputs of the McCulloch-Pitts neuron. A network of perceptrons represents the first generation of neural networks, while the second generation uses the same perceptron model but with a more complex activation function. For the third generation, which corresponds to the SNNs, different neuron models can be employed, leveraging the trade-off between biological plausibility and implementation cost:

*   The `Hodgkin-Huxley model` \[[90](#refbib.xhtml#refbib90)\] represents the most biologically plausible but also the most complex neuron model. It involves several differential equations, which make the development of large SNNs using this model impractical and inefficient.

*   The `Izhikevich model` \[[95](#refbib.xhtml#refbib95)\] can reproduce different spiking patterns as well as spike shapes of biological cortical neurons while being less compute-intensive than the Hodgkin-Huxley neuron. Its functionality is described through Equation (2.3) to (2.5), where *v* is the membrane potential, *I* is the input current, *u* is the membrane recovery variable, and *a, b, c, d* are constants that set the spike shape.

    $$\\begin{array}{l} {\\frac{dv}{dt} = 0.04v^{2}(t) + 5v(t) + 140 - u(t) + I(t)} \\\\ \\end{array}$$  

    (2.3)

    $$\\begin{array}{l} {\\frac{du}{dt} = a(bv(t) - u(t))} \\\\ \\end{array}$$  

    (2.4)

    $$\\begin{array}{l} {{if}\\ v \\geq V\\_{th},{then}\\ \\left\\{ \\begin{matrix} {v\\leftarrow c} \\\\ {u\\leftarrow u + d} \\\\ \\end{matrix} \\right.} \\\\ \\end{array}$$  

    (2.5)

*   The `Integrate-and-Fire (IF) model` \[[61](#refbib.xhtml#refbib61)\] is the simplest model from the computational perspective. For this reason, it is widely used in the SNN community. The model is based on a resistance-capacitance (RC) circuit, similar to a low-pass filter. Equation (2.6) describes how the membrane potential of the postsynaptic neuron evolves over time, from which the time constant *τ*[*m*] = *R**C* can be derived as in Equation (2.7).

    $$\\begin{array}{l} {I(t) = \\frac{v(t)}{R} + C\\frac{dv}{dt}} \\\\ \\end{array}$$  

    (2.6)

    $$\\begin{array}{l} {\\tau\_{m}\\frac{dv}{dt} = - v(t) + RI(t)} \\\\ \\end{array}$$  

    (2.7)

    When the membrane potential reaches a certain threshold *V*[*t**h*] at the firing time *t*[*f*], the postsynaptic neuron produces a spike *δ*(*t* − *t*[*f*]), after which the membrane potential is reset to a value *v*[*r**e**s**t*] (often set to 0 as a common assumption \[[207](#refbib.xhtml#refbib207)\]), obviously lower than *V*[*t**h**].

*   The `Leaky-Integrate-and-Fire (LIF)` \[[278](#refbib.xhtml#refbib278)\] is a modified version of the IF model that introduces the concept of refractory period. It represents the time period after a spike in which the membrane potential cannot increase even if a train of spikes is received at the input. The evolution over time of the membrane potential of a LIF neuron is described by Equation (2.8).

    $$\\begin{array}{l} {\\tau\_{m}\\frac{dv}{dt} = - v(t) + \\left( i\_{0}(t) + \\sum w\_{j}i\_{j}(t) \\right)} \\\\ \\end{array}$$  

    (2.8)

    A synaptic current *i*[*j*](*t*) is generated when a spike is received. It is then modulated by its correspondent synaptic weight *w*[*j*] and added to the bias current *i*[0](*t*). Compared to the Hodgkin-Huxley model, the lower computational complexity of the LIF neuron comes at the price of a lower biological plausibility. The LIF model assumes that the shape of the action potentials is uniform for each spike. This assumption limits the ability to reproduce biological spike patterns and shapes. However, such a low complexity allows for creating large SNNs and their implementation on neuromorphic hardware.

### 2.3.2 Spike Coding Techniques

The input information of SNNs is represented and propagated to the output through spike trains. Different methods for encoding the information into spikes \[[210](#refbib.xhtml#refbib210)\] are shown in [Figure 2.10](#chapter2.xhtml#fig2_10):

*   `Rate Coding`: The intensity corresponds to the probability of firing a spike, which translates into the mean firing rate when multiple spikes are counted within an observation period. It is the most commonly used method due to its simplicity, but it might be power-consuming compared to other coding techniques due to the high spiking rate.

*   `Inter-Spike-Interval (ISI) Coding`: The intensity is temporally coded as the precise delay between consecutive spikes.

*   `Time-to-First-Spike (TTFS) Coding`: The intensity *I* is coded as the time difference *Δ**t** between the stimulus and the first spike of a neuron. Such delay can be either the inverse of the intensity (*Δ**t** = 1/*I*) or a linear relation, such as *Δ**t** = 1 − *I*. This encoding approach assumes that a neuron generates only one spike for any given stimulus. Hence, eventual subsequent spikes that follow from that neuron are simply ignored \[[199](#refbib.xhtml#refbib199)\]. The main advantage is that the processing can proceed fast since the information is already transmitted when the first spike is received.

![Figure 2.10: Comparison between Rate, Inter-spike interval (ISI), and Time to first spike (TTFS) encoding techniques.](images/fig2_10.jpg)

[Figure 2.10:](#chapter2.xhtml#b2fig2_10) Comparison between Rate, Inter-spike interval (ISI), and Time to first spike (TTFS) encoding techniques.

### 2.3.3 SNN Learning Techniques

Different methods for training SNNs can be adopted based on the topology of learning. For unsupervised learning, the possible approaches are based on Hebbian learning \[[235](#refbib.xhtml#refbib235)\], the Spike-Driven Synaptic Plasticity (SDSP) \[[56](#refbib.xhtml#refbib56)\], and the Spike-Time-Dependent Plasticity (STDP) \[[255](#refbib.xhtml#refbib255)\]. The STDP, the most commonly used method in the community, is based on strengthening (or weakening) the synaptic weights depending on the degree of correlation between the presynaptic and postsynaptic neuronal spikes in spatial and temporal domains.

The supervised DNN learning methods, based on the gradient backpropagation, cannot be directly applied to SNNs since the spiking loss function is not differentiable \[[232](#refbib.xhtml#refbib232)\]. The possible solutions to overcome this challenge are either (1) using DNN-to-SNN conversion after learning the weights in the DNN domain or (2) approximating the spiking derivative w.r.t. the loss function by using a surrogate gradient.
