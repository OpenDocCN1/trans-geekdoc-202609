
Considering that several of the works for load disaggregation use wavelet transform and neural networks, these two themes will be addressed in the following sections. Then, a bibliographic review of the breakdown techniques will be presented.

### 9.2.6 Wavelet Transform

To extract information from signals and reveal signal dynamics, an appropriate processing technique is necessary. Typically, signal processing transforms a signal from the time domain to another domain, since the characteristic information incorporated in the time domain cannot be easily observed in its original form [47,48].

The wavelet transform is a tool that converts a signal into a different shape. This conversion reveals the characteristics hidden in the original signal. The wavelet is a small wave that has an oscillating waveform characteristic, and its energy is concentrated in time [48,49].

The first reference to the wavelet goes back to the beginning of the 20th century. Haar’s research on orthogonal function systems led to the development of a set of rectangular-based functions. The Haar wavelet was named after this set of functions, and it is also the simplest of the wavelet family developed to date [49,50].

The wavelet transform allows window sizes and variables to analyze different frequency components within a signal. Through scale variations and time shifts of the base wavelet function, the wavelet transform can extract components across its entire spectrum, using small scales for the decomposition of high-frequency parts and large scales for analyzing low-frequency components [49–51].

### 9.2.7 Neural Networks and Load Estimation

Neural networks represent an important resource for the analysis of the electric sector in different applications, mainly for the prediction of an electric load to be demanded by a region of consumers [52,53].

Neural networks are computational models inspired by an animal’s central nervous system (in particular, the brain) that is capable of machine learning as well as pattern recognition. Artificial neural networks are often presented as systems of “interconnected neurons that can compute values from inputs.” For example, a neural network for handwriting recognition is defined by a set of input neurons that can be activated by the pixels in an input image. The activations of these neurons are then passed on, weighted, and transformed by a function determined by the network designer to other neurons. This process is repeated until, finally, an output neuron is activated. This determines which character was read [53,54].

Like other methods of machine learning (artificial intelligence), systems that learn from data, neural networks have been used to solve a wide variety of tasks that are difficult to solve using programming based on common rules, including computer vision and recognition of voice [54,55].

The oldest example of neural networks is perceptron networks, with a layer of output nodes, connected to the inputs by sets of weights. This topology can be considered the simplest form of a forwarding network. The sum of the products of the weights by the inputs is calculated for each output node, and if the calculated value exceeds a certain threshold (usually 0), the neuron fires and sets the output to a value of 1; if the calculated value is less than the threshold, the output is set to –1. Neurons with this behavior are called McCulloch–Pitts neurons or threshold neurons. At the same time, a learning algorithm calculates the difference between the calculated output and the input data and uses the difference value to adjust the network weights [55,56].

Perceptron is a simple neural network. It consists of an input layer and an output layer. For each entry, there is a related weight, the output value being the sum of the products of each entry by their respective weight. Thus, the neuron has an all or nothing behavior, so it will be necessary to establish a threshold function that drains when the neuron is active or at rest. The perceptron can learn everything it can represent [56,57]. The perceptron with only two layers can represent all linearly separable functions.

The performance of the backpropagation learning algorithm is conditioned both to the modeling adopted in the artificial neural network and to the dataset used in the process of adjusting the synaptic weights between the network connections [56,57].

The perceptron had its validity proven in the backpropagation model, which made it possible to implement the third layer necessary for learning XOR. Using a network of neurons like those used in the perceptron, backpropagation performs a backpropagation of the output error to the previous layers. The error is the result of the comparison between the desired (predefined) output and the actual network output. With this backpropagation, together with a threshold function of fractional values (escaping from all or nothing), it is possible to represent nonlinear functions, allowing the training of the XOR function. For this reason, backpropagation has become one of the most used networks, given its wide spectrum of possible representations [57,58].

Several other models have been created since then, although these previously mentioned were the most prominent because they were the precursors and they defined the paradigms of neural network models existing today.

## 9.3 MATERIALS AND METHODS

This chapter discusses the methodology used to acquire the signals of the loads used in this work, the methodology to analyze these signals, and also the tests and results. Then, a discussion is made about the results found and implications for the creation of a commercial prototype.

### 9.3.1 Acquisition of Signals

It was necessary to create a database of waveforms with different loads of electronic devices for domestic use since a database with free and reliable distribution was not found. From this, an Agilent® 1146A claw-shaped oscilloscope probe was purchased, which has a sensitivity given by the manufacturer to 100mA. The oscilloscope used was one from Agilent: Agilent DSO-254A model that has a Windows operating system. The signals were then visualized and recorded, using the rate of 20 kSa/s (kilosamples per second), which represents 333.3 samples for each 60-Hz cycle acquired.

Some of the main electronic devices for the creation of the base were then chosen: 15, 40, and 60W incandescent lamps, 15W electronic lamp, air conditioning, blender, refrigerator, microsystem radio, electric shower, portable fan, toaster, laptop, and 14" television, as listed in Table 9.1. We chose to use the equipment in different configurations, that is, different temperature settings in the case of the shower, different speeds in the case of the fan and blender, and in the case of the microsystem, operating by open radio and playing a CD, the television on standby and in operation.

Current signals were extracted from each device working independently and also some combinations of signals from two loads or more loads working simultaneously. The latter allowed us to observe the effect of harmonics in the measurement of loads. Besides, it allowed comparing current signals provided by various loads in the network and the sum of the loads working individually.

In Figures 9.1–9.24, small-time intervals of the waveforms found for each case are presented, aligning with the sampling rate of 20 kSa/s. The acquired signals had a total of 131,072 points, which is equivalent to approximately 6.55 seconds.

As expected, electronic equipment (electronic lamp, microsystem, laptop, television, and blender), represented in Figures 9.1–9.10, has harmonic components. The same behavior occurs when these nonlinear loads work together with the linear ones, Figures 9.11–9.14. On the other hand, the incandescent lamps, refrigerator, fan, toaster, shower, and the sum of some of these loads showed only the predominant component of 60 Hz, as depicted in Figures 9.15–9.24. In Figures 9.25 and 9.26, two examples of loads with harmonic components are shown, through the graphs of the discrete Fourier transform of the signal.

### TABLE 9.1
Equipment Used in the Tests

| Equipment | Wattage |
| :--- | :--- |
| Compact fluorescent lamp—Taschibra | 15W |
| Laptop—Positivo | 65W |
| Microsystem working with CD—Philco | 12.5W |
| Microsystem working with radio at high volume—Philco | |
| Microsystem working with radio at low volume—Philco | |
| 14" Television on—LG | 65W |
| 14" Television on standby—LG | |
| Blender at speed 1—Walita | 350W |
| Blender at speed 2—Walita | |
| Blender at speed 3—Walita | |
| Incandescent lamp—Philips | 15W |
| Incandescent lamp—Philips | 40W |
| Incandescent lamp—Philips | 60W |
| Refrigerator—Consul | 300W |
| Fan at maximum speed—Arno | 50W |
| Fan at minimum speed—Arno | |
| Toaster—British | 850W |
| Shower in the summer position—Lorenzetti | 4,600W |
| Shower in the winter position—Lorenzetti | 5,500W |
| Air conditioner—York | 7,000BTU |
