![](bbox=[0.203, 0.123, 0.517, 0.303])

![](bbox=[0.558, 0.123, 0.897, 0.303])

(a) Hypersphere Outlier Detection

(b) Attack on a Hypersphere

**Figure 4.1** Depictions of the concept of hypersphere outlier detection and the vulnerability of naive approaches. **(a)** A bounding hypersphere centered at **c** of fixed radius *R* is used to encapsulate the empirical support of a distribution by excluding outliers beyond its boundary. Samples from the "normal" distribution are indicated by ⊕’s with three outliers on the exterior of the hypersphere. **(b)** An attack against a hypersphere outlier detector that shifts the detector’s "normal" region toward the attacker’s goal **x**⁴. It will take several iterations of attacks to sufficiently shift the hypersphere before it encompasses **x**⁴ and classifies it as benign.

The novelty detection learning algorithm considered throughout this chapter is a mean-centered hypersphere of fixed radius *R*. For this basic model for novelty detection, we analyze a contamination scenario whereby the attacker poisons the learning algorithm to subvert the learner’s ability to adapt to a tool the adversary uses to accomplish its objective. The specific scenario we consider is that the adversary wants the novelty detector to misclassify a malicious target point, **x**⁴, as a normal instance. However, the initial detector would correctly classify **x**⁴ as malicious so the adversary must manipulate the learner to achieve its objective. Initially, the attacker’s target point, **x**⁴, is located a distance *D<sub>R</sub>* radii from the side of the hypersphere (or a total distance of *R* (*D<sub>R</sub>* + 1) from the initial center). Further, it is assumed that the initial hypersphere was already trained using *N* initial benign data points, and the adversary has *M* total attack points it can deploy during the attack, which takes place over the course of *T* retraining iterations of the hypersphere model. Analyzing this simple attack scenario yields a deeper understanding into the impact of data contamination on learning agents and quantifies the relationship between the attacker’s effort (i.e., *M*, the number of attack points used by the attacker) and the attacker’s impact (i.e., the number of radii, *D<sub>R</sub>*, by which the hypersphere is shifted).

# 4.1 Causative Attacks on Hypersphere Detectors

Learning bounding hyperspheres is a basic technique for anomaly detection that can be accomplished by learning a hypersphere centered at the empirical mean of a training set or that encloses the (majority of the) training data (e.g., see Shawe-Taylor & Cristianini 2004, Chapter 5). These novelty detection models classify all data that lie within the