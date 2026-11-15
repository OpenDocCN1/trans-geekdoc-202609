

In Chapter 43, Yuan Zhou and Leiting Dong established a Digital Twins drive framework to realize damage diagnosis and predict fatigue crack growth. In the example of a cyclic helicopter component, the uncertainty of the Digital Twins is significantly reduced, and the evolution of structural damage can be well predicted. The proposed method, using the ability of Digital Twins, will help to achieve condition-based maintenance.

Antonio Bono et al. proposed an integrated strategy for managing and checking infrastructure using drones and Digital Twins in Chapter 44. This strategy can provide the real-time status of buildings and perfectly process location information.

## 1.9 Digital Twins in Energy

Nikolai Fomin and Roman V. Meshcheryakov discuss the Digital Twins security of network physical water supply systems in Chapter 45. By using the safety assessment method based on Digital Twins, the safety system of the water supply company is improved.

In Chapter 46, Dirk Westermann understands Digital Twins as a real-time digital representation of physical components based on measurement data and analysis knowledge. It enables power suppliers to transform their operations through actionable insight to achieve better business decisions. In other words, grid operators can improve operations, reduce unplanned outages, and manage fluctuations in market conditions, fuel costs, and weather conditions.

In Chapter 47, Elena F. Sheka believes that with the increasing amount of modeling data, it is inevitable that the concept of Digital Twins will change from ordinary modeling. This chapter takes the material science of high-tech graphene materials as an example to introduce an example of this concept reflection.

Triboelectric nanogenerator (TENG) is a technology that transforms the changes of the physical world into electrical signals. Jiayue Zhang and Jie Wang introduce the mechanism of common TENG, common self-powered sensors based on TENG, and various scenarios of TENG in Digital Twins in Chapter 48. In addition, this section also discusses the future application potential of TENG in Digital Twins.

## 1.10 Digital Twins in Medicine and Life

In Chapter 49, João A. M. Santos et al. introduced the current paradigm of Digital Twins applied in the pharmaceutical industry, studied the Digital Twins applied in the pharmaceutical supply chain and pharmaceutical management more deeply, and proposed the future research direction.

Chenyu Tang et al. introduced the development status of human Digital Twins in Chapter 50. The success of Digital Twins technology in industrial application makes people more confident in building human Digital Twins models.

In Chapter 51, Sai Phanindra Venkatapurapu et al. describe the opportunities and challenges of Digital Twins for Proactive and Personalized Healthcare.

## Part 2

## Thinking about Digital Twins

![](img/0dd4397c67b063014553965e4f1cf7e4_32_0.png)

Taylor & Francis Group
http://taylorandfrancis.com

## 2 What Is Digital and What Are We Twinning?: A Conceptual Model to Make Sense of Digital Twins

Ashwin Agrawal and Martin Fischer
Stanford University

### 2.1 Motivation

We often find ourselves having some version of the following conversation when we meet a friend or colleague that we have not seen for a while:

> What are you working on these days?
> Digital Twins.
> Interesting! I have heard a lot about it. How do you define a Digital Twin?

A brief explanation is then followed by:

> I fail to make sense of Digital Twins. Some say it is a digital representation and others include Artificial Intelligence and Machine Learning. I honestly think it is a new buzzword people have created.

This confusion among researchers and practitioners regarding the Digital Twin (DT) concept motivates this work. We start by providing more context about the problem, then review the many ways the term “Digital Twin” has been used in the literature before proposing a conceptual model that unifies these existing perspectives and thus alleviates the confusion.

### 2.2 Introduction

In digital transformation, DTs have emerged as a key concept because they provide a bi-directional coordination between the virtual (digital) and the physical worlds. It provides a multi-dimensional view of asset performance through simulation, prediction, and decision-making based on real-world data (Autodesk 2021). According to a recent Gartner report, over two-thirds of the companies that have implemented sensor technology plan to deploy at least one DT in production by 2022 (Gartner 2019).

DT, however, is still ambiguous and has varied interpretations because of the wide spectrum of technologies and market needs. It is unable to distinguish itself from general computing and simulation models (Khajavi et al. 2019). The boundary between different digitalization approaches such as Building Information Modelling (BIM), Cyber Physical Systems (CPS), Industry 4.0, and DT is extremely blurry in practice (Agrawal et al. 2022). As a result of this confusion, practitioners may hold unrealistic hopes about DT, misalign their strategies, misallocate resources, and ultimately reject DT as hype (Agrawal, Fischer, and Singh 2022).

Researchers and practitioners have attempted to alleviate the confusion by defining DT in different ways. However, it appears that each definition has grown directly from the set of examples and applications that the definer had in mind. There are some people who believe that DT means a complex real-time updated digital model with prescriptive and predictive capabilities (Gabor et al. 2016; Glaessgen and Stargel 2012), while others think it means a simple digital representation (Canedo 2016; Schroeder et al. 2016). Further, Boje et al. (2020) note that there has been little research in this field, resulting in rebranding and reusing emerging technology capabilities like Prediction, Simulation, Artificial Intelligence (AI), and Machine Learning (ML) as necessary constituents of DTs, forcing the practitioners to adapt these technologies without really understanding their purported benefits (Love, Matthews, and Zhou 2020).

Further evidence of the practical importance of the problem is provided by Agrawal, Singh, and Fischer (2022), who analyse Google search trends for the keyword “Digital Twin”. They use a web tool to scrape the data for the most common user queries. Based on the analysis, the authors found very strong evidence of the existing confusion regarding DTs. For instance, some of the most searched queries about DTs are: “How is DT different from cyber physical systems?”, “How is DT different from the Information model?”, and “How to use AI in a DT?”, further confirming our observed problem and motivation for this work.

To alleviate the confusion, this work proposes a conceptual framework that can help researchers and

![](img/0dd4397c67b063014553965e4f1cf7e4_35_0.png)

**FIGURE 2.1**
Motivating questions for our conceptual framework.

practitioners to make sense of DTs, they need to address these two fundamental questions for every DT application because the meaning of ‘Digital’ and ‘Twin’ varies depending on the situation, use case, and context. Our proposed framework would aid them in answering these questions.

This work is organized as follows: A brief background about DTs is presented in Section 2.3. Our conceptual framework is described in Section 2.4, before its application is demonstrated in Section 2.5. Finally, the chapter is concluded in Section 2.6.

### 2.3 Background

This section is divided into three parts. The first section describes a brief history about DTs. In the second section, we use illustrative definitions of DTs from literature and examine them through the two fundamental questions we outlined earlier: What is digital and What are we twinning? This will help readers gain a better understanding of the variety present in DT definitions, and thus appreciate the need to ask our two fundamental questions. Finally, in the third section, we summarize the gap in the literature.

#### 2.3.1 History of DT

Let us have a quick look at the development timeline of DTs as demonstrated in Figure 2.2. As a part of NASA’s Apollo programme in the 1960s, at least two identical spacecrafts were constructed, and one remained on earth called the twin (Schleich et al. 2017). The twin was used extensively for training during flight preparation, run simulations, and assist astronauts in critical conditions. In this sense, every prototype that mimics real-world operating conditions can be seen as a twin.

However, constructing a physical twin of every asset/entity, like NASA did of its aircraft, is almost impractical (and costly). Therefore, the idea of “twinning” was extended to create a twin digitally, making a twin practical and cost effective. In this regard, Michael Grieves first introduced the concept of virtually twinning a physical object as a part of a university course

