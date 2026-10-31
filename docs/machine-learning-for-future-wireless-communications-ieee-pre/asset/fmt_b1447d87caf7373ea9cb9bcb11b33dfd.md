
### Loop Unrolling
Loop unrolling creates multiple copies of the loop body and adjusts the loop iteration counter accordingly. For example, if a loop is processed with an unrolling factor (`UF`) equal to 2 (i.e. two subsequent operations in the same clock cycle, as shown in [Figure 13.4](#c13.xhtml#c13-fig-0004)), it may reduce a loop's latency by a factor of ![images](images/c13-i0162.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mn>50</mn><mo>%</mo></mrow></math>, since a loop will execute in half the iterations usually needed. Higher `UF` and `II` may help achieve low latency but at the cost of higher hardware resource consumption. Thus, the trade‐off between latency and hardware consumption should be thoroughly explored.

![Figure 13.3 Loop pipelining.](images/c13f003.jpg)

[Figure 13.3](#c13.xhtml#R_c13-fig-0003) Loop pipelining.

![Figure 13.4 Loop unrolling.](images/c13f004.jpg)

[Figure 13.4](#c13.xhtml#R_c13-fig-0004) Loop unrolling.

### 13.4.3.2 Design Steps
Our framework presents several design and development steps, which are illustrated in [Figure 13.5](#c13.xhtml#c13-fig-0005). Steps that involve hardware, middleware (i.e. `HDL`), and software have been depicted with different shades of grey.

The first major step of the framework is to take an existing `DL` model and convert it into `HLS` language, so it can be optimized and later synthesized in hardware. Another critical challenge is how to make the hardware implementation fully reconfigurable, i.e. the weights of the `DL` model may need to be changed by the `Controller` according to the specific training. To address these issues, we distinguish between (i) the `DL` model architecture, which is the set of layers and hyperparameters that compose the model itself; and (ii) the parameters of each layer, i.e. the neurons' and filters' weights.

To generate the `HLS` code describing the software‐based `DL` model, an `HLS` library provides a set of `HLS` functions that parse the software‐based `DL` model architecture and generates the `HLS` design corresponding to the desired architecture. The `HLS` library supports the generation of a convolutional, fully connected, rectified linear unit, and pooling layers, and operates on fixed‐point arithmetic for better latency and hardware resource consumption. The `HLS` code is subsequently translated to `HDL` code by an automated tool that takes into account optimization directives such as loop pipelining and loop unrolling. At this stage, the `HDL` describing the `DL` core can be simulated to (i) calculate the amount of `PL` resources consumed by the circuit (i.e. flip‐flops, `BRAM` blocks, etc) and (ii) estimate the circuit latency in terms of clock cycles. After a compromise between space and latency as dictated by the application has been found, the `DL` core can be synthesized and integrated with the other `PL` components, and thus total space constraints can be verified. After implementation (i.e. placing/routing), the `PL` timing constraints can be verified, and finally the whole system can be deployed on the `SoC` and its functionality tested.

![Figure 13.5 A hardware design framework for RF deep learning.](images/c13f005.jpg)

[Figure 13.5](#c13.xhtml#R_c13-fig-0005) A hardware design framework for RF deep learning.

## 13.5 Open Problems
In this section, we discuss a set of open challenges, the overcoming of which will accelerate the induction of `ML` techniques into future wireless communications and networking.

### 13.5.1 Lack of Large‐Scale Wireless Signal Datasets
It is well known that learning algorithms require a considerable amount of data to be able to effectively learn from a training dataset. Moreover, to compare the performance of different learning models and algorithms, it is imperative to use the same sets of data. More mature learning fields, such as computer vision and natural language processing (`NLP`), already have standardized datasets for these purposes (Deng, [2012](#c13.xhtml#c13-bib-0013); Deng et al., [2009](#c13.xhtml#c13-bib-0012)). However, the still lacks large‐scale datasets for `RF` `ML`.

This is not without a reason. Although the wireless domain allows the synthetic generation of signals having the desired characteristics (e.g. modulation, frequency content, and so on), problems such as `RF` fingerprinting and jamming detection require data that captures the unique characteristics of devices and wireless channels. Therefore, significant research effort must be put forth to build large‐scale wireless signal datasets to be shared with the research community at large.

### 13.5.2 Choice of I/Q Data Representation Format
It is still a subject of debate within the research community what the best data representation is for `RF` `DL` applications. For example, an `I/Q` sample can be represented as a tuple of real numbers or a single complex number, while a set of `I/Q` samples can be represented as a matrix or a single set of numbers represented as a string. It is a common belief that there is no one‐size‐fits‐all data representation solution for every learning problem and that the right format might depend, among others, on the learning objective, choice of the loss function, and learning problem considered (O'Shea et al., [2018](#c13.xhtml#c13-bib-0046)).

### 13.5.3 Choice of Learning Model and Architecture
While there is a direct connection between images and tensors, the same cannot be concluded for wireless signals. For example, while `3-D` tensors have been proven to effectively model images (i.e. red, green, and blue channels), and kernels in convolutional layers are demonstrably powerful tools to detect edges and contours in a given image, it is still unclear if and how these concepts can be applied to wireless signals. Another major difference is that, while images can be considered stationary data, `RF` signals are inherently stochastic, non‐stationary, and time‐varying. This peculiar aspect poses significant issues in determining the right learning strategy in the wireless `RF` domain. For example, while `CNN` seems to be able to effective at solving problems such as modulation recognition (West and O'Shea, [2017](#c13.xhtml#c13-bib-0063); Karra et al., [2017](#c13.xhtml#c13-bib-0034); O'Shea et al., [2018](#c13.xhtml#c13-bib-0046)), it is still unclear if this is the case for complex problems such as `RF` fingerprinting. Moreover, `DL` has traditionally been used in static contexts (Krizhevsky et al., [2012](#c13.xhtml#c13-bib-0036); Hinton et al., [2012](#c13.xhtml#c13-bib-0023)), where the model latency is usually not a concern. Another fundamental issue absent in traditional `DL` is the need to satisfy strict constraints on resource consumption. Indeed, models with high number of neurons/layers/parameters will necessarily require additional hardware and energy consumption, which are clearly scarce resources in embedded systems. Particular care must be devoted, therefore, when designing learning architectures to solve learning problems in the `RF` domain.

## 13.6 Conclusion
