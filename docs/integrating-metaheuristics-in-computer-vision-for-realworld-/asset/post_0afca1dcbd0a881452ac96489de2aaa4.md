
## Ex6.2: What is the likelihood that it will endure a crucial 10³ hours?

```
R (t) = e^-(10^-5)(10^3)
Sol: R (t) = e^-0.01
=.990
F(t) = 1 - R (t)
= 1 - .990
= .010
```

## Ex6.3: Five electronics sub-systems failed from a sample of 1200 which were used constantly for 90 days. What is the failure rate?

```
Sol: failure rate = 1 / MTBF
i.e. λ(t) = 1 / T = R / T = 5 / 1200*90*24 = .00001929 failure hours
```

## 10.2.5 Fault Tree Analysis

This is a commonly used method in industry to assess reliability of a system. Fault tree analysis starts by identifying the top event, known as the undesirable event of the system. The top event of the system is caused by events created and connected by logic gates, such as AND, OR, etc. A fault tree is a logical diagram used to show the interrelationships between potential basic events (catastrophes) in a structure and the conditions leading to this occurrence [14]. The causes might be environmental conditions, human errors, routine events (events expected to occur during the system's life), and explicit component failures. A fault tree analysis may be qualitative, quantitative, or both, depending on the objectives of the analysis. The following basic steps are involved in performing fault tree analysis:

- set up system description
- build up the fault tree
- calculate the fault tree qualitatively
- Collect basic data such as apparatus failure rates, repair rates and failure occurrence probability
- estimate fault tree quantitatively
- suggest corrective measures

## 10.2.6 Fault Tree Symbols Logic Gate

### 10.2.6.1 OR-Gate

The OR-gate demonstrates that the output event A occurs if any of the input events E_i occur. Figure 10.1 shows the diagrammatic representation of OR-Gate.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_205_0.png)

Figure 10.1 OR-Gate.

### 10.2.6.2 AND-Gate

The AND-gate demonstrates that the output event A occurs only when all the input events E_i occur simultaneously. Figure 10.2 shows the diagrammatic representation of AND-Gate.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_205_1.png)

Figure 10.2 AND-Gate.

## 10.2.7 Regulations for Fault Tree Structure

Let fault event signify any event in the fault tree, whether it is a basic event or an event higher up in the tree. Figure 10.3 shows an example of a simple fault tree.

### 10.2.7.1 Illustrate the Fault Actions

Each basic event should be carefully described (what, where, when) in a “remark box.”

### 10.2.7.2 Estimate the Fault Events

The fault events may be various types, such as technical failures, human errors, or environmental loads. Each event should be carefully assessed. As explained above, technical failures can be divided into three categories: primary failures, secondary failures, and command issues. Primary failures of components are normally classified as basic events, while secondary failures and command deficiencies are named intermediate events that require further analysis to identify root causes. While assessing a fault event, we ask: “Can this be a primary failure?” If the answer is yes, we classify the fault event as a “normal” basic event. If the answer is no, we classify the fault event as either an intermediate event that must be further developed or as a “secondary” basic event. The secondary basic event is often called an inadequate event and represents at least an event that is not examined further because data is unavailable or because its consequence is irrelevant [15].

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_206_0.png)

Figure 10.3 A simple fault tree.

### 10.2.7.3 Including the Gates

All inputs to a particular gate should be fully defined and described before proceeding to the next gate. The fault tree should be completed in stages, and each stage should be completed before starting the next.

## 10.3 Conclusion

This paper addresses reliability and mean time to failure (MTTF) assessment of a complex system under waiting, combining the concept of equipment failure and human error. Failure rates of the complex system follow exponential time distributions, while repair follows general repair time distribution. According to the study, using the fewest possible components in mean time to system failure will improve performance.

## References

- Hagen, F.W. (Ed.), Human reliability analysis, in: *Nucl Safety*, vol. 17, pp. 315–326, 1976.
- Deuermeyer, B.L., A new approach for network reliability analysis. *IEEE Trans. Reliab.*, R-31, 350–354, 1982.
- Alven W. Reliability engineering. Prentice-Hall; 1964.
- Frederickson, A.A., Comparison of fault tolerant controllers used in safety applications. *Proc. of the Eighth Annual Control Engineering Conf.*, Rosemont, IL, May 1989.
- Bukowski, J.V. and Goble, W.M., The reliability analysis of PES safety-systems. *Proc. of the Food and Pharmaceutical Industries Symposium*, Instrument Society of America, Toronto, Canada, 1992.
- Goble, W.M. and Spaeder, W.J., Eliminating common cause failures - the bane of reliable control systems. *Proc. of the ISA 91 Conf. and Exhibit*, ISA, 1991.
- JESD85 JS. Methods for Calculating Failure Rates in Units of FITs, JEDEC Publication, 2001.
- Huang, L. and Xu, Q., Lifetime reliability for load-sharing redundant systems with arbitrary failure distributions. *IEEE Trans. Reliab.*, 59, 2, 319–330, June 2010.
- Wilkins, D.J., The Bathtub curve and product failure behavior part one – the bathtub curve, infant mortality and burn-in, (Accessed: 2016-01-15).
- Berretton, J.N., Practical application of the Weibull distribution, in: *Industrial Quality Control*, vol. 21, pp. 71–79, 1964.
- Kaur, H. and Sharma, S.K., Exploration on reliability theory using LGCM model in neural network. *Adv. Math.: Sci. J.*, 9, 8, 5349–5359, 2020, ISSN: 1857-8365.
- Barlow, Richard E., and Proschan, F., Mathematical theory of reliability. Society for Industrial and Applied Mathematics, 1996.
- Wang, D., Jiang, C., Park, C., Reliability analysis of load-sharing systems with memory. *Lifetime Data Anal.*, 25, 2, 341–360, 2019.
- Burton, R.M. and Howard, G.T., Optimal system reliability for a mixed series and parallel structure. *J. Math. Anal. Appl.*, 28, 2, 370–382, 1969.
- Kaur, H. and Sharma, S.K., Measures of a Series System’s Reliability for One or Two Decimal Random Data Points, in: *2022 3rd International Conference on Issues and Challenges in Intelligent Computing Techniques (ICICT)*, pp. 1–7, Ghaziabad, India, 2022, doi: 10.1109/ICICT55121.2022.10064557.

## A Detailed Description on Various Techniques of Edge Detection Algorithms

Pritha A. 1* and G. Fathima 2+

1 Science and Humanities, Anna University, Chennai, India
2 Department of CSE, Adhiyamaan College of Engineering, Hosur, India

### Abstract

Edge detection plays a dominant part in image processing, image recognition and computer vision. This paper discusses various edge detection algorithms such as Sobel, Robert, Canny and Prewitt detectors that expose the complete performance of image information. Architecture, block diagram, accuracy parameters of edge detection help reduce noise in the image and filter out unwanted information. Edge detection depends on valid and definite numbers of contiguous data. Pixels are individually defined to improve edge quality and efficiency. Exaggeration and noise reduction are maintained. Finally, the output of the aforementioned edge detection techniques is shown in detail and compared with experimental results using MATLAB.

Keywords: Noise reduction, filtering, accuracy, PSNR, MSE, MATLAB

### 11.1 Introduction

Images consist of various attributes of an entity, such as size, shape, color, and orientation. The output of changes in light, color, shade, and texture is called an edge. Edge detection methods are one of the major techniques in image processing. Their applications are broadly used in pattern recognition, medical image processing, etc. There are two types: Gaussian-based and Gradient-based edge detection techniques [9]. There are distinct variables that influence edge detection, such as noise environment, edge structure, edge orientation, and luminance [10]. Edge detection is helpful for data compression, segmentation, and image reconstruction [2]. Section 11.2 presents edge detection techniques. Section 11.3 presents experimental results. Conclusions are given in Section 11.4.
