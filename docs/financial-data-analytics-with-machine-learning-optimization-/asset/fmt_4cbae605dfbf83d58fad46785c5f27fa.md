
14. By the design of `K`‐means clustering, the locations of the artificial clusters are driven by those of the balls `B Subscript k`'s. Indeed, when `L less-than K`, by the pigeonhole principle, there is at least one artificial cluster that encloses parts of more than one ball, justifying the non‐emptyness of `script upper A 3`. Furthermore, such an artificial cluster resulting from `K`‐means clustering usually contains a decent proportion of both balls, that is why `p overTilde Subscript k l` and `p overTilde Subscript k prime l` are assumed to have a lower bound with a probability approaching 1 as `n right-arrow infinity`.

# CHAPTER 15  

Applications of Deep Learning in Finance

Binary logistic regression, multinomial logits and classification trees as introduced in previous chapters are common statistical classifiers. A completely different approach is based on Neural Networks (NNs) which aim to mimic the functioning mechanism of human brains. Although how a human brain memorizes, recognizes patterns and generalizes concepts is still not thoroughly understood, some of its aspects are well‐known to neuroscientists, which helps to build a workable model for our brains as a NN.

In 1943, McCulloch and Pits [\[18\]](#c15.xhtml#c15-bib-0018) postulated a simple mathematical model to explain how biological neurons work. From then there was not much progress until 1970 when the modern computer was first invented. In the 1970s, *Linnainmaa Seppo* invented the *backpropagation* algorithm to train neural networks so as to match as much as possible the fitted output with the observed response [\[13](#c15.xhtml#c15-bib-0013), [14\]](#c15.xhtml#c15-bib-0014). There followed many successful examples and applications in the laboratories. In the 1980s, research moved from the labs to the commercial world, with typical applications being the detection of fraudulent credit card transactions, real estate appraisal, and data mining. Before we dive into NNs, we introduce some typical structures of our brains.

## 15.1 HUMAN BRAINS AND ARTIFICIAL NEURONS

Our brains consist of approximately 86 billion special cells known as neurons. Each of these neurons is typically connected with thousands of other neurons. Most importantly, unlike other cells, these neurons will not regenerate. It is widely accepted that these neurons are responsible for our ability for memorizing, learning, generalizing concepts and thinking. Within each neuron, there are four basic components: *dendrites*, the *cell body*, the *axon* and *synapses*; see [Figure 15.1](#c15.xhtml#c15-fig-0001). These neurons are connected to form a huge network. Though the exact function of these neurons is still a mystery, a simple mathematical model that mimics these neurons provides a surprisingly good performance in pattern recognition, classification and prediction problems in image processing and text mining.

![FIGURE 15.1 An illustration of the analogy between actual neurons and abstract ones. (Source: https://stock.adobe.com/in/images/cerebral-cortex-pyramidal-neuron/653658834)](images/c15f001.png)

[**FIGURE 15.1**](#c15.xhtml#R_c15-fig-0001) An illustration of the analogy between actual neurons and abstract ones. (Source: [https://stock.adobe.com/in/images/cerebral-cortex-pyramidal-neuron/653658834](https://stock.adobe.com/in/images/cerebral-cortex-pyramidal-neuron/653658834))

![FIGURE 15.2 An artificial neuron.](images/c15f002.png)

[**FIGURE 15.2**](#c15.xhtml#R_c15-fig-0002) An artificial neuron.

Dendrites are responsible for receiving information from other neurons; a cell body is for processing information collected; an axon amplifies the signal carried by the processed information to other neurons; and a synapse is the junction between axon end and those dendrites of other neurons. To mimic the functioning of a neuron, we refer to the artificial neuron as illustrated in [Figure 15.2](#c15.xhtml#c15-fig-0002).

Here `x 1 comma ellipsis comma x Subscript p Baseline` are the inputs received from other neurons or the outside environment. The total input `h` is formed from a linear combination of these inputs with weights `w 1 comma ellipsis comma w Subscript p Baseline` together with `w 0` serving as a *bias* term. The *transfer function* (or *activation function*) converts the input `h` of `bold-italic x` to the output `h prime equals f left-parenthesis h right-parenthesis`. In turn, this output `h prime` may go to other neurons as input. Some commonly used transfer functions for the axon are shown in [Figure 15.3](#c15.xhtml#c15-fig-0003).

![FIGURE 15.3 Commonly used activation functions for an axon.](images/c15f003.png)

[**FIGURE 15.3**](#c15.xhtml#R_c15-fig-0003) Commonly used activation functions for an axon.

Very often, a logistic transfer function is used; that is why artificial neural network is considered as a significant extension of logistic regression.

## 15.2 FEEDFORWARD NETWORK

These artificial neurons are connected from one layer to another to form a network.

![FIGURE 15.4 Illustration of a 4‐3‐2 ANN.](images/c15f004.png)

[**FIGURE 15.4**](#c15.xhtml#R_c15-fig-0004) Illustration of a 4‐3‐2 ANN.

Referring to [Figure 15.4](#c15.xhtml#c15-fig-0004), there are three layers: input, hidden and output layers. The numbers of neurons in the input, hidden and output layers are 4, 3 and 2 respectively; and so it is known as a 4‐3‐2 Artificial Neural Network (ANN).

1. For a standard ANN, there is only one hidden layer. With more than one hidden layer, it is called a Multilayer Perceptron (MLP); see [Section 15.7](#c15.xhtml#c15-sec-0008) for a more detailed discussion on the latter.

2. The numbers of neurons in the input and output layers are determined by the nature of the problem, while the number of neurons in the hidden layer is user‐defined.
