
## Chapter 3

The Use of Artificial Neural Networks and Metaheuristic Algorithms to Optimize the Compressive Strength of Concrete

**Abstract** In this chapter, five basic designs are obtained by changing the amount of aggregates used with different sizes while maintaining the amounts of water, cement, and additives constant. New samples are then proposed using the Taguchi method and are tested in the laboratory. Following the training of an Artificial Neural Network (ANN) with the obtained results, the EVPS and SA-EVPS algorithms are utilized to determine the highest compressive strength. The obtained results are then tested in the laboratory and their experimental compressive strength are compared with those of the ANN results.

### 3.1 Introduction

In this chapter the use of artificial neural networks and metaheuristic algorithms is presented to optimize the compressive strength of concrete [1]. As one of the most widely used engineering materials in the world, concrete is the most commonly used substance after water. Concrete has a distinctly compressive strength, which is the most important indicator of its quality. Concrete is obtained by combining cement, water, fine aggregates, and coarse aggregates. In addition to these cases, concrete additives have also received considerable attention in recent years. The compressive strength of concrete is one of the most important properties of hardened concrete as a building material. As a result of the compressive strength of concrete, many different properties of concrete can be determined from it and are related to this characteristic, including tensile strength, shear strength, specific weight, durability, erosion resistance, sulfate resistance, and other concrete properties. It is a challenge in the direction of concrete production to increase the compressive strength of concrete solely by modifying the characteristics of the aggregate used and without altering the amount of water and cement used. The construction of concrete has been the subject of numerous research studies, some of which are briefly discussed below.

Using the methodology of Life Cycle Assessment, Habert et al. [2] evaluated the environmental impact of geopolymer concrete production. In their research, they found that the production of geopolymer concrete has a lower impact on global warming than the production of standard Ordinary Portland Cement (OPC) concrete, but a higher impact on other environmental categories than global warming. It was also noted that industrial waste could be used to produce geopolymer concrete, as well as that the use of activated clays and blast furnace slag as a mix-design technology could reduce the need for binder.

A review by Imbabi et al. [3] examined the current state-of-the-art in cement production and presented some emerging green alternatives, such as energy-efficient, low carbon production methods, geopolymers, carbon negative cements and novel concrete designs.

Sabbaghian and Kheyroddin [4] investigated HPFRCC’s splitting tensile strength, compressive strength, and bulk density. 108 cylinders and cube specimens were tested at 7 and 28 days following the formulation of 18 HPFRCC mix proportions with 1% steel fibers (30 mm length) and a mathematical exponential function between STS and CS was proposed, along with three distinct fractions of steel fibers in volume.

To predict the resistance of UHPC to chloride ion penetration at ages up to 28 days under a variety of curing regimes, Khaksefidi et al. developed a simple and non-destructive surface electrical resistivity (ER) method. ER, CS and density increased with age, but chloride environments posed greater damage than sulphate environments.

In order to reduce laboratory work and predict concrete’s compressive strength, artificial neural networks (ANNs) can be used. ANNs are intelligent systems that can solve problems in a wide range of applications, including optimization, prediction, modeling, clustering, pattern recognition, simulation, and many others. These are some of the research studies in which ANNs have been used as a powerful tool:

Göthals et al. investigated the development and application of artificial neural networks for the prediction of macroinvertebrate communities. It revealed that the applied model training and validation methodologies can often be improved, and moreover crucial steps in the modelling process are often inadequately documented.

Sinha and Wang developed Artificial Neural Network (ANN) prediction models for permeability, maximum dry density, and optimal moisture content of soils using the results of classification, compaction, and permeability tests.

According to Palavar et al. [5], the effect of aging parameters on the wear behavior of PM Inconel 706 (IN 706) superalloy was experimentally investigated and an ANN model was developed to predict weight loss after wear tests.

In both prediction and classification, neural networks have been widely used. Therefore, Laguna and Marti [6] compared a training procedure that achieves a high degree of accuracy within a short timeframe with several variants of a commercial training program.

In terms of improving energy efficiency in building energy management systems, building energy prediction is a promising research area. One of the best approaches is to use artificial neural networks. A review of twelve ANN architectures for building energy prediction is provided by Lu et al. [7], along with a discussion of three challenges and open issues.

Shariati et al. aimed to predict the compressive strength of concrete incorporating furnace slag and fly ash as partial replacements for cement in their study, which used a hybrid artificial neural network and genetic algorithm. The results of the study indicated that the ANN-GA model was superior to the ANN-BP model in terms of predicting compressive strength.

For ANN to be utilized efficiently and in a targeted manner, metaheuristic algorithms can be applied. Recent research has indicated a substantial interest in metaheuristic algorithms from a wide range of fields, particularly engineering. Metaheuristic algorithms are practical optimization methods in addition to their ability to obtain near-optimal solutions to any problem.

In this study, five basic designs were obtained by changing the amount of aggregates used with different sizes while maintaining the amounts of water, cement, and additives constant. New samples were then proposed using the Taguchi method and were tested in the laboratory. Following the training of an Artificial Neural Network (ANN) with the obtained results, the EVPS and SA-EVPS algorithms were used to determine the highest compressive strength. The obtained results were then tested in the laboratory and their experimental compressive strength was compared with the ANN results.

This chapter is organized as follows: Section one contains an introduction. In the second section, EVPS and SA-EVPS algorithms are briefly explained. The third and fourth sections provide an overview of ANNs and Taguchi methods, respectively. In the fifth section, a numerical problem is presented, and in the last section, a conclusion is presented.

### 3.2 A Brief Explanation of the EVPS and SA-EVPS Algorithms

The EVPS algorithm, which is an improved version of the VPS algorithm, is widely used in optimizing structural engineering problems. While the EVPS algorithm uses eight variables that are experimentally determined, these parameters are considered specific values by default and are responsible for controlling search accuracy, exploration and exploit phases, convergence speed, as well as overall algorithm behavior. Thus, in the SA-EVPS algorithm, all of these parameters have a significant impact and all eight parameters mentioned above are also optimized before the main optimization is performed. In the SA-EVPS algorithm, all eight parameters are first optimized using the EVPS algorithm, and then the main optimization is performed. The flowchart of the SA-EVPS algorithm is presented in Fig. 3.1 in order to provide greater clarity.
