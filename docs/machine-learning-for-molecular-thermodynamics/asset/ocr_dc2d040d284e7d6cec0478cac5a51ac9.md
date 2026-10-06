# Chinese Journal of Chemical Engineering 31 (2021) 227–239

Contents lists available at ScienceDirect

# Chinese Journal of Chemical Engineering

journal homepage: www.elsevier.com/locate/CjChe

ELSEVIER

![](bbox=[0.843, 0.073, 0.952, 0.166])

# Review

# Machine learning for molecular thermodynamics

Jiaqi D¹, Nan Xu¹, Manh Hien Nguyen², Qi Qiao², Yao Shi¹,³, Yi He¹,⁴*, Qing Shao²*

^¹College of Chemical and Biological Engineering, Zhejiang University, Hangzhou 310027, China
²Chemical and Materials Engineering Department, University of Kentucky, Lexington, KY 40506, USA
³Key Laboratory of Chemical Engineering Ministry of Education, Zhejiang University, Hangzhou 310027, China
⁴Department of Chemical Engineering, University of Washington, Seattle, WA 98195, USA

![](bbox=[0.843, 0.203, 0.952, 0.283])

ARTICLE INFO

ABSTRACT

Article history

Received 21 August 2020

Received in form 2 October 2020

Accepted 28 October 2020

Available online 8 January 2021

Keywords

Thermodynamics
Molecular engineering
Molecular simulation

Force field

Thermodynamic properties of complex systems play an essential role in driving chemical engineering research. It remains a challenge to predict the thermodynamic properties of complex systems in a wide range and describe the behavior of ions and molecules in complex systems. Machine learning emerges as a powerful tool to resolve this issue it can describe complex properties beyond the capacity of traditional mathematical functions. This review will summarize the discovery of traditional machine learning methods and explore the different aspects of machine learning using several examples. The first aspect is to apply machine learning to predict the thermodynamic properties of a broad spectrum of systems based on known data. The second aspect is to integrate machine learning and molecular simulations to accelerate the discovery of new materials. The third aspect is to develop machine learning models that handle both harmonic and all-atom molecular dynamics simulations. The applications in these three aspects illustrate the potential of machine learning in thermodynamics of chemical engineering. We will also discuss the perspective of the broad applications of machine learning in chemical engineering.

© 2021 The Chemical Industry and Engineering Society of China, and The Chemical Industry Press, Co., Ltd. All rights reserved.

# Introduction

Machine learning has emerged as a versatile tool to predict and investigate the thermodynamics of complex systems. One task for molecular thermodynamics is to predict the thermodynamic properties of complex systems with high accuracy. The theoretical or semi-theoretical models have been used for learning of various systems [1–11]. However, it remains a challenge to develop robust models that can predict the thermodynamic properties of complex systems at the molecular level using the traditional mathematical framework. Machine learning offers to computer algorithms that can learn from [12,13]. The machine learning methods are known for their extraordinary performance in self-driving vehicles and games against humans [14–16]. Due to the ability of learning to describe complex relationship between variables, we have witnessed growing accuracy of these models in the material and chemical engineering

fields, ranging from [17–22], exploration to molecular thermodynamics prediction [28–34].

Machine learning has helped the research of molecular dynamics from three aspects (Fig. 1). First, it can help develop robust molecular models for complex systems. Obtaining accurate thermodynamic properties of a system is essential for developing processes. Nevertheless, theoretical or empirical models have been developed for predicting thermodynamic properties of various systems. These models use although consist of mathematical functions using hypothesis-driven functions and the parameters derived from theory or experiment. Most of the limitations of these methods rely heavily on the intuition of a "trial-and-error" approach. Deep machine learning methods provide a new way of learning and predicting the thermodynamic properties of complex systems. Many learning methods such as the neural network and decision tree can quantify the relationship between the targeted properties with the selected molecular database provide opportunity to develop such machine learning models [39–42].

*Corresponding authors at: College of Chemical and Biological Engineering Zhejiang University, Hangzhou 310027, China (Y. He). E-mail: yhe@zju.edu.cn (Y. He), qhao@zju.edu.cn (Q. Shao).

https://doi.org/10.1016/j.jce.2020.101044

1004-9541/2021 The Chemical Industry and Engineering Society of China, and The Chemical Industry Press, Co., Ltd. All rights reserved.

* Name*