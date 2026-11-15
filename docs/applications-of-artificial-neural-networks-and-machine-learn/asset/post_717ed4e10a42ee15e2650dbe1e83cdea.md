
![](img/4048998719320644ee88964326fd7995_92_0.png)

Fig. 3.1 Schematic illustration of the SA-EVPS algorithm [1]

## 3.3 An Overview of Artificial Neural Networks (ANNs)

Biological neural networks are the basis of artificial neural networks, which can learn patterns and predict results in high dimensional spaces of problems. Artificial neural networks are intelligence tools inspired by biological neural networks. In a noisy and complex dataset, they can map a set of inputs to a set of outputs. In recent years, artificial neural networks, which were inspired by the biological nervous system, have evolved from being a theoretical concept to becoming a widely used technology applied to a variety of problems. They can provide appropriate solutions to problems that cannot be solved conventionally. An artificial neural network (ANN) is an intelligence tool that has been used extensively in various applications such as

![](img/4048998719320644ee88964326fd7995_93_0.png)

Fig. 3.2 A schematic of an ANN structure showing an input, an output, and a hidden layer

function approximation, classification, time series prediction, etc. In fact, an ANN can model almost any complex relationship between inputs and outputs. A large part of the performance of neural networks is determined by the training process, which determines the weights and biases of the network. This can result in a good estimation of the actual output of the problem based on the weights and biases of the network.

It is seen in Fig. 3.2 that within each neuron, a weighted sum of inputs is calculated, and this value, along with a bias value, is transformed by an activation function. This value is then transferred to the nearby neurons. During training, the weights and biases of the network are adjusted in such a way that the minimal error between target values (actual values) and output values (network values) is achieved.

## 3.4 A Brief Overview of Taguchi's Method

The Taguchi method is a statistical technique that improves product quality, and has been applied to engineering, biotechnology, marketing, and advertising in recent years [8, 9]. There are three basic and simple concepts that comprise Taguchi's philosophy. Concepts such as these include:

- During the production process, quality should be designed, not checked.
- The best way to achieve quality is to minimize the deviation from the specified value.
- A product must be designed to be safe against uncontrollable environmental conditions.

In the Taguchi method, two groups of factors are considered in the design of experiments. First, there are the controllable factors that have certain levels in the design and are under control; In the Taguchi method, it is described as a signal. Another category is disturbance factors, which affect the reaction of a process but cannot be controlled; they are called noise in the Taguchi method. Taguchi experiments are designed in a way so that disturbance factors are minimized [9, 10].

In addition, this method has the advantage of determining how each factor contributes to the test results. As a result of the ANOVA table for the test data, the decision maker has the capability of ranking the factors in order of their importance. As a result of this ranking, the decision maker may be persuaded to combine two or more controllable factors in order to reduce the costs associated with the experimental design. The ANOVA study determines the relative effects of factors in different sections.

## 3.5 Numerical Example

In this article, first, the compressive strength of five basic designs was determined by changing the amount of aggregates of different sizes while keeping the amount of water, cement, and additives constant. According to the aggregate size, the aggregates were classified into six sizes, so the six factors influencing the compressive strength of the samples are the same as the six values of the six types of aggregate granulation size. Thus, the design variables and the effectors are the same six components. From five basic designs, 81 proposed designs were selected using Taguchi method, and all 81 samples were made in the laboratory and their compressive strength was determined. As a matter of fact, without the Taguchi method, it would be necessary to obtain a large number of samples with combinations of 5 basic designs in order to analyze the sensitivity of the effect of the six influencing factors mentioned, a process that would be practically impossible to determine in the laboratory for their compressive strength. In accordance with Taguchi method results, an artificial neural network was trained (with input data from the six variables mentioned above) and the results of the ANN were compared to the experimental data obtained in the lab, Fig. 3.3.

![](img/4048998719320644ee88964326fd7995_95_0.png)

Fig. 3.3 Comparison of laboratory compressive strength (at 28 days) results with those obtained from a trained artificial neural network for proposed Taguchi method designs

With the knowledge of the compressive strength of the samples, proposed by the Taguchi method and the training of the artificial neural network, the optimal design has been determined by using the EVPS and SA-EVPS metaheuristic algorithms from the ANN as the objective function. The optimization process consists of 30 independent runs with a population size of 20. In the EVPS algorithm, p, w1, w2, HMCR, PAR, Neighbor and Memory_size are respectively 0.05, 0.2, 0.3, 0.3, 0.95, 0.1, 0.1, and 4. The SA-EVPS algorithm parameters that are self-adaptive are shown in Table 3.1. Figure 3.4 illustrates the convergence curves for EVPS and SA-EVPS. As shown in Fig. 3.4, the objective function is equal to the inverse of the compressive strength derived from the ANN.

Table 3.1 SA-EVPS algorithm parameters that are self-adaptive (optimized)

| No. | Parameter | Value |
|---|---|---|
| 1 | α | 0.065411 |
| 2 | p | 0.35474 |
| 3 | w₁ | 0.732654 |
| 4 | w₂ | 0.21554 |
| 5 | HMCR | 0.0845451 |
| 6 | PAR | 0.83211 |
| 7 | Neighbor | 0.85484 |
| 8 | Memory_size | 1 |

In order to clarify the results, the aggregates were divided into two categories: gravel and sand, so that according to the ASTM D 422-63, the boundary between gravel and sand sieve size is 4.75 mm. So, the retained amount on the sieve is 4.75 mm in the range of gravel, and the passed amount is considered sand. According to Table 3.2, the five basic designs with the best compressive strength were derived from the Taguchi method, along with the optimal solution derived from the EVPS and SA-EVPS algorithms. In Table 3.2, the laboratory results are compared with the ANN results for compressive strength for five basic designs, the best of Taguchi method, and the best EVPS algorithm and SA-EVPS algorithm design. Based on this table, the best answer can be attributed to the SA-EVPS algorithm.

Comparing the laboratory results and the trained artificial neural network, it can be concluded that the ANN has performed with acceptable and appropriate accuracy. In addition, the SA-EVPS algorithm provided the best answer, although the EVPS algorithm also performed well in this example. Compared to the five basic designs, Taguchi’s method produced better results, but it was weaker than the EVPS and SA-EVPS algorithms.

![](img/4048998719320644ee88964326fd7995_96_0.png)

Fig. 3.4 The EVPS and SA-EVPS convergence curves

Table 3.2 Comparison of the five basic design, laboratory results, and results from EVPS and SA-EVPS algorithms for compressive strength

| No. | Type of design | Gravel | Sand | Cement | Water | Additive | The ANN prediction | Experimental results |
|---|---|---|---|---|---|---|---|---|
| 1 | Basic design 1 | 433 | 1411 | 397 | 159 | 5.4 | 414 | 420 |
| 2 | Basic design 2 | 323 | 1520 | 397 | 159 | 5.4 | 422 | 431 |
| 3 | Basic design 3 | 215 | 1593 | 397 | 159 | 5.4 | 448 | 428 |
| 4 | Basic design 4 | 494 | 1322 | 397 | 159 | 5.4 | 423 | 405 |
| 5 | Basic design 5 | 529 | 1258 | 397 | 159 | 5.4 | 420 | 433 |
| 6 | Taguchi's best design | 588 | 1198 | 397 | 159 | 5.4 | 452 | 444 |
| 7 | EVPS's best design | 503 | 1304 | 397 | 159 | 5.4 | 490 | 481 |
| 8 | SA-EVPS's best design | 412 | 1372 | 397 | 159 | 5.4 | 491.5 | 487 |
