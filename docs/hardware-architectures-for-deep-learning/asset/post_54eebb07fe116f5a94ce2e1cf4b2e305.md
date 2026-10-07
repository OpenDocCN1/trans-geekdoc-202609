
## 268 Hardware architectures for deep learning

realize the synapses of an ANN by performing a weighted sum of its inputs. This is equivalent to a weighted lookup and matrix multiply in digital ANN alternatives. This implementation enjoys from low power consumption and plasticity in research [19].

Memristor, as the fourth passive two-terminal electrical component, relates the electric charge (q) and magnetic flux (φ) [20]. Initially physically realized in 2008 [21] by analyzing a titanium dioxide thin film, memristors are particularly well suited for the design of ANNs where matrix multiplications can be performed by consuming ultra-low amount of power. From that time, different teams have been working on the development of memristor based on a variety of other materials (e.g., [22,23]). In general, the memristor, also known as a resistance switch, is an electronic device whose internal states depend on the history of its experienced currents and voltages. The resistance of the memristor could be altered in a range between a minimum (e.g., 12.5 KΩ) and maximum value (e.g., 8.3 MΩ) by applying voltage pulses. The amplitudes and durations of the voltage pulses determine the amount of change in the resistance. Generally, the amplitude of the applied voltage should be larger than a threshold voltage (denoted as the write threshold voltage of the memristor, e.g., 4 V) to alter the resistance of the memristor [24]. The programming of a memristor (i.c., changing its conductance) requires only a small amount of energy, as the device can be extremely small (<2 nm) [25], and the switching speed can be very fast (<1 ns) [26]. Organized into large arrays, or three-dimensionally (3D), the intermediate computing results (such as weights in a neural network) can be stored locally as conductance values in single nonvolatile memristor during the computation.

Analog neurons: The activation function of the neuromorphic circuits with memristor crossbar could be implemented with different elements as analog comparators [27], operational amplifiers (op-amps) and CMOS inverters [28]. Among these implementations, the inverter-based network has the lowest power consumption and smallest delay due to its simplest structure. Table 11.1 compares the design parameters of the neurons in these implementations in a 90-nm technology. The reported numbers are achieved by simulating a single neuron with a 500 KΩ resistive load.

Memristive multilayer network: The results of extensive numerical simulations reported in prior work shows that memristive neural networks would provide orders of magnitude higher speed-energy efficiency compared with the traditional CMOS hardware platforms.

Table 11.1 Comparison of delay, power, and energy of different implementations of a single neuron

| Implementation | Number of transistors | Delay (ns) | Power consumption (mW) | Energy per operation (pJ) |
| :--- | :--- | :--- | :--- | :--- |
| Op-amp Comparator | 24 × 2 | 3.394 | 2.455 | 44.85 |
| Inverter | 13 | 2.219 | 0.1996 | 4.294 |
| | 2 × 2 | 0.032 | 0.0031 | 0.0007 |

## Inverter-based memristive neuromorphic circuit

The authors in [30] demonstrated pattern classification using a TiO2-based memristive crossbar by building a single-layer perceptron network. They trained the perceptron network by both in-situ and ex-situ methods. For ex-situ method, the synaptic weights were calculated using a software for in-situ method, the synaptic weights were adjusted simultaneously in the memristive crossbar. The ex-situ method, which is easy to implement, may require a shorter training time and have a lower efficiency in synaptic weight update. A 128 x 81 1IR (1-Transistor-1-Resistor) array of HfAlO_x/TaO devices was the first experimental implementation for face recognition [31], and a 128 x 64 Ta/HfO2 1IR array was built and for efficient analog signal processing and machine learning [32,33]. A 10 x 6 portion in an array of Al2O3/TiO memristors was used to recognize 3x3 black/white images [34]. The experimental demonstrations, however were limited to very small arrays which could solve relatively simple problems. The reasons for using small arrays were mainly non-idealities in device properties (such as variability) and challenges in the integration of large array [35].

ADCs and DACs: The neural operations in the memristive crossbar circuit are basically performed using the analog signals of current and conductance. This requires ADCs and DACs for coupling the neuromorphic circuit to digital devices. The conversions, however, make up a large portion of the total power consumption (e.g., see Figure 11.2) and chip area of the neuromorphic accelerator [6,36]. This mandates the use of efficient ADCs and DACs for different tasks, such as synapse readout in the mixed signal system. There are prior works (e.g., [37,38]) in which the capability of memristive structures for implementing the ADC and DAC has been shown. The neural network approach for implementing the ADC and DAC has some advantages over the conventional structures in terms of the area, power efficiency, and flexibility [37]. Some problems including spurious spikes and table however reduce the efficacy of such converters. To overcome these problems, by relying on inverter-based neuromorphic circuits, a DAC structure which employs memristors to generate the corresponding analog outputs is also discussed. This structure could be merged to the memristive crossbar of the neuromorphic circuit. In addition, a modified backpropagation algorithm which comply with the proposed structure is described. This structure is faster and more power efficient compared with the conventional DAC structure considered for using in neuromorphic circuits. Additionally, a neural network-based ADC which has the flexibility of converting input voltages with different ranges and resolutions is presented. It should be mentioned that the feedforward structure of the proposed ADC also eliminates the problem of spurious states of the conventional Hopfield ADCs.

![](img/e6e752b99eb1621488c89445a57e2a86_294_0.png)

Figure 11.2 The power consumption breakdown of a neuromorphic circuit proposed in [36].

## 11.3 Inverter-based memristive neuromorphic circuit

The block diagram of a two-layer ANN implemented by the proposed memristive neuromorphic structure is shown in Figure 11.3. This structure comprises an input interface, an output interface, a programming interface, and two layers of analog inverter-based memristive neural network. The weights of the ANN are calculated using our proposed training framework which is realized using a software in an off-chip machine. Before the first usage of the circuit, the calculated weights are written

![](img/e6e752b99eb1621488c89445a57e2a86_295_0.png)

Figure 11.3 The block diagram of the inverter-based memristive neuromorphic circuit with its interfaces

the memristive crossbar through the programming interface also initializes the input and output interfaces. The weights are written to the crossbar and the input/output interfaces are initialized, the programming interface is turned off and its outputs become float, the ANN is powered on, and normal operation mode of the circuit begins. The programming interface also includes switches (row and column selectors in Figure 11.3) to select the proper memristor to write and protect other memristors from unwanted write. In the rest of this section, the details of these components, as well as the method for training the neural network are discussed.

### 11.3.1 Neuron circuit with memristive synapse

Assume a neural network layer with $V_{ip}, V_{in} (i = 1, \dots, N)$ inputs and $w_{jip}, w_{jin}$ synaptic weights. In this neural network layer, the input of the $j$th neuron, is

$net_{j} = \sum_{i=1}^{N} (V_{ip}w_{jip} + V_{in}w_{jin}) \quad (11.1)$

Based on (11.1), we propose to consider the circuit of Figure 11.4 to implement a single neuron and its synaptic weights with two CMOS inverters and a column of the memristive crossbar. Each input of this circuit (e.g., $x_i$) is differential which contains inverted ($V_{in}$) and non-inverted ($V_{ip}$) signals. In this circuit, the voltage of the node $net_{j}$ (the input of the inverter of column $j$) is

$V_{net_{j}} = \zeta \sum_{i=1}^{N} (V_{ip}\sigma_{jip} + V_{in}\sigma_{jin}) \quad (11.2)$

![](img/e6e752b99eb162148c89445a57e2a86_296_0.png)

Figure 11.4 Implementation of synaptic weights for each neuron
