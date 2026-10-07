# Introduction to Cognitive Radio 7

One particularly successful method to solve the multiobjective cognitive radio problems is the implementation of a highly flexible genetic algorithm. The operation of the genetic algorithm optimization system easily allows updates and additions to the optimization problem space as well as the dynamic creation of chromosomes to represent the waveform, and thus, it provides a solution independent of the search space and communications system.

As a way to augment the optimization process, we also introduce the use of case-based decision theory. This is a memory feedback system that learns and improves the cognitive radio behavior.

The cognitive radio design we will be discussing throughout this book covers all of these topics. We graphically summarize our approach in Figure 1.3 from the sensing to the monitoring feedback system.

+   * Model system Taking in surrounding radio environment and user/ network requirements
* Remember models and apply case-based decision theory to determine best course of action to take
* Use genetic algorithms to update and optimize the new radio parameters
* Monitor feedback from radio to understand system performance Penalize knowledge base for poor performance

Figure 1.3 Overview of the major functions in our cognitive engine approach.

Although we provide both theory and a practical implementation of methods to build cognitive radios, we also understand that there is a lot of research left to do to fully understand the cognitive radio behavior and optimization processes. Because of this, we have designed a mechanism that allows for easy introduction of new cognitive radio methods and components to test, experiment, and compare different solutions. The process also has the benefit of allowing easy distribution and sharing of cognitive components throughout a network, enabling knowledge sharing and distributed processing among cognitive radios.

We then provide experimental results of the cognitive engine on a real software radio platform. These experiments serve two purposes. First, they provide a scientific analysis of the theory we have developed. Second, we move the experiments between a simulated environment and real radios. Both