Considering that several of the works for load disaggregation use wavelet transform and neural networks, these two themes will be addressed in the following sections. Then, a bibliographic review of the breakdown techniques will be presented.

# ## 9.2.6 Wavelet Transform

To extract information from signals and reveal signal dynamics, an appropriate processing technique is necessary. Typically, signal processing transforms a signal from the time domain to another domain, since the characteristic information incorporated in the time domain cannot be easily observed in its original form [47,48].

The wavelet transform is a tool that converts a signal into a different shape. This conversion reveals the characteristics hidden in the original signal. The wavelet is a small wave that has an oscillating waveform characteristic, and its energy is concentrated in time [48,49].

The first reference to the wavelet goes back to the beginning of the 20th century. Haar’s research on orthogonal function systems led to the development of a set of rectangular-based functions. The Haar wavelet was named after this set of functions, and it is also the simplest of the wavelet family developed to date [49,50].

The wavelet transform allows window sizes and variables to analyze different frequency components within a signal. Through scale variations and time shifts of the base wavelet function, the wavelet transform can extract components across its entire spectrum, using small scales for the decomposition of high-frequency parts and large scales for analyzing low-frequency components [49–51].

# ## 9.2.7 Neural Networks and Load Estimation

Neural networks represent an important resource for the analysis of the electric sector in different applications, mainly for the prediction of an electric load to be demanded by a region of consumers [52,53].

Neural networks are computational models inspired by an animal’s central nervous system (in particular, the brain) that is capable of machine learning as well as pattern recognition. Artificial neural networks are often presented as systems of “interconnected neurons that can compute values from inputs.” For example, a neural network for handwriting recognition is defined by a set of input neurons that can be activated by the pixels in an input image. The activations of these neurons are then passed on, weighted, and transformed by a function determined by the network designer to other neurons. This process is repeated until, finally, an output neuron is activated. This determines which character was read [53,54].

Like other methods of machine learning (artificial intelligence), systems that learn from data, neural networks have been used to solve a wide variety of tasks that are difficult to solve using programming based on common rules, including computer vision and recognition of voice [54,55].

The oldest example of neural networks is perceptron networks, with a layer of output nodes, connected to the inputs by sets of weights. This topology can be considered the simplest form of a forwarding network. The sum of the products of the weights by the inputs is calculated for each output node, and if the calculated value exceeds a