![](images/cover.jpg)

![Cover: Entropy Randomization in Machine Learning, Chapman & Hall/CRC Machine Learning & Pattern Recognition, written by Yuri S. Popkov, Alexey Yu. Popkov, Yuri A. Dubnov, Translated into English by Alexander Yu. Mazurov, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York, CRC Press is an imprint of Taylor and Francis Group, an informa business, a Chapman and Hall book.](images/cover.jpg)

# Chapman & Hall/CRC Machine Learning & Pattern Recognition

**A First Course in Machine Learning**

Simon Rogers, Mark Girolami

**Statistical Reinforcement Learning: Modern Machine Learning Approaches**

Masashi Sugiyama

**Sparse Modeling: Theory, Algorithms, and Applications**

Irina Rish, Genady Grabarnik

**Computational Trust Models and Machine Learning**

Xin Liu, Anwitaman Datta, Ee-Peng Lim

**Regularization, Optimization, Kernels, and Support Vector Machines**

Johan A.K. Suykens, Marco Signoretto, Andreas Argyriou

**Machine Learning: An Algorithmic Perspective, Second Edition**

Stephen Marsland

**Bayesian Programming**

Pierre Bessiere, Emmanuel Mazer, Juan Manuel Ahuactzin, Kamel Mekhnacha

**Multilinear Subspace Learning: Dimensionality Reduction of Multidimensional Data**

Haiping Lu, Konstantinos N. Plataniotis, Anastasios Venetsanopoulos

**Data Science and Machine Learning: Mathematical and Statistical Methods**

Dirk P. Kroese, Zdravko Botev, Thomas Taimre, Radislav Vaisman

**Deep Learning and Linguistic Representation**

Shalom Lappin

**Artificial Intelligence and Causal Inference**

Momiao Xiong

**Introduction to Machine Learning with Applications in Information Security, Second Edition**

Mark Stamp

**Entropy Randomization in Machine Learning**

Yuri S. Popkov, Alexey Yu. Popkov, Yuri A. Dubnov

(*Translated into English by Alexander Yu. Mazurov*)

For more information on this series please visit: [https:/​/​www.routledge.com/​Chapman–HallCRC-Machine-Learning–Pattern-Recognition/​book-series/​CRCMACLEAPAT](https://www.routledge.com/Chapman–HallCRC-Machine-Learning–Pattern-Recognition/book-series/CRCMACLEAPAT)

First edition published 2023

by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2023 Yuri S. Popkov, Alexey Yu. Popkov, Yuri A. Dubnov

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged, please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or here-after invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978- 750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice:* Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

LCCN no. 2022007067

ISBN: 978-1-032-30628-5 (hbk)

ISBN: 978-1-032-30774-9 (pbk)

ISBN: 978-1-003-30656-6 (ebk)

DOI: [10.1201/9781003306566](https://doi.org/10.1201/9781003306566)

Typeset in LM Roman

by KnowledgeWorks Global Ltd.

*Publisher's note:* This book has been prepared from camera-ready copy provided by the authors.

# Preface

A fundamentally important attribute of civilization's development consists in accumulation of knowledge, with further transformation into solutions to extract new knowledge. This transformation is implemented in different ways, including knowledge extraction from accumulated data. A *model* with quantitatively measured characteristics serves as a basic tool to accumulate knowledge. However, besides quantitative (digital) data, there may exist non-quantitative ones, e.g., audio, video, graphical, text, and other data. In the final analysis, the problem of knowledge extraction and accumulation is reduced to the knowledge about the model that is formalized by *estimating* its characteristics. This process can be interpreted as *learning* of the model using data. Since model learning is performed by data processing using computing machines, the conceptual difference between the model and its computer implementation vanishes accordingly, causing a natural belief that the object of learning is computing machines. Such an approach explains the appearance of *Machine Learning* (*ML*), a term and even a science that proceeds from the theoretical grounds of mathematical statistics, optimization, numerical methods and information technology.

As a rule, the general problem of machine learning is broken down into three classes of problems as follows: classification (the allocation of objects to appropriate warehouses) clustering (the grouping of more or less homogeneous objects) and dynamic regression (the restoration of relations between cause data and effect data). A crucial stage of machine learning is the *prediction* of possible changes in the solutions of these problems. According to modern understanding, machine learning yields “learned” deterministic models that are equipped with empirical probabilistic reliability estimates. As a result, the matter concerns empirically probabilistic machine learning.

This book develops a new branch of machine learning called *Randomized Machine Learning* (*RML*),

Practical solution of these problems requires a tool kit with integrated mathematical and algorithmic methods (on the one hand) and software utilities oriented to high-performance computing systems (on the other hand). The resources and capabilities of computer machines are doubled annually. As a result, huge amounts of data are accumulated and stored, both in natural and digital formats, for example, the currently accumulated data amount to billions petaflops. There are large data centers intended to accumulate and store these data over very long periods of time. What is to be done with accumulated data besides storage? The scientific community is endeavoring to outline some ways to process and use these data.

One possible way was formulated in 1991 by G. Piatetsky-Shapiro as the concept of *Data Mining (DM)*; see \[[55](#refbib.xhtml#r55), [191](#refbib.xhtml#r191)\]. Within this concept it was suggested to integrate different methods of mathematical statistics and probability theory in a user-friendly information technology environment, whereas the statement of the fundamental problems associated with qualitative and, perhaps, quantitative descriptions of knowledge and adequate data arrays was left to a researcher. The pioneering data mining experiments discovered a whole bunch of negative features of data (errors, reliability, adequacy, use of different scales, temporal irregularity and others) that casted doubt on the resulting knowledge. These features become more essential for large amounts of heterogeneous data. The verification of such data in the wide sense turns out to be a serious challenge.

The data problem magnetized a part of the scientific community so much that the first volume of *Journal of Data Science* appeared in 2002, announcing a new branch of science called *Data Science* (*DS*). This branch was intended to absorb *all* sciences related to data usage and processing.

In 2008, *Nature* editor C. Lynch prepared a special issue \[[28](#refbib.xhtml#r28)\] devoted to the problem of large amounts of data, formulating the concept of *Big Data* (*BD*). It was expected to develop an information technology environment with processing methods for the large arrays of numerical, audio, video and text data.

The physical core of all concepts involving data is a computing machine implementing computational algorithms for data processing and knowledge extraction. The necessary tool kit forms the subject of the ML concept, which is based on the methods and algorithms of probability theory and statistics, optimization, automata theory and discrete mathematics, theory of dynamic systems, and more. Even this short list of related disciplines shows that the ML concept is to create a synthetic tool kit for solving data processing problems.

*ML* has a history of over 60 years and a rich experience in solution of many problems. The first publication on the subject dates back to 1957 when F. Rosenblatt created the MARK I perceptron; see \[[156](#refbib.xhtml#r156)\]. The notion of empirical risk, which is the basis for the *ML* procedures, was introduced by Ya. Tsypkin in the monograph \[176\]. A fundamental tool to form empirical risk is the so-called *Vapnik–Chervonenkis dimension* (*VC dimension*) suggested by the authors in \[[179](#refbib.xhtml#r179)\]. The method of potential functions for the classification and pattern recognition problems was published in 1970; see \[[12](#refbib.xhtml#r12)\]. We also refer to the monographs \[57, 21\] popular in the ML community.

The modern *ML* concept employs the *deterministic* parametrization of models and estimates using data arrays with hypothetical properties. The quality of estimation is characterized by empirical risk functions, and minimization yields the corresponding optimal estimates in terms of the chosen empirical risk; the details can be found in \[180\].

Generally, real problems solved by *ML* procedures are immersed in an *uncertain environment*. If the matter concerns data, they are obtained with errors, omissions and dubious validity. Model design and parametrization is a subjective non-formalizable process that depends on the individual knowledge of a researcher. Therefore, a mass application of *ML* procedures causes a rather high uncertainty. Empirical risk minimization gives parameter estimates for an existing data array within an adopted parameterized model; in other words, these estimates are conditional. There is no clarity about their behavior with other data arrays or within another parametrization model.

Due to the above-mentioned circumstances, it is necessary to simulate the uncertainty somehow. An approach involves *randomized* uncertainty simulation, which stems from a randomized representation of model parameters and data measurement errors. This means that model characteristics are assumed to be random whereas data are assumed to contain random errors. In contrast to the existing ML procedures, such randomized machine learning (RML) procedures give best estimates for the probability density functions (PDFs) of the random parameters and measurement noises under maximum uncertainty (entropy).

This book suggests using **information entropy** to characterize the quality of learning under uncertain conditions. In a series of works \[80, 157, [81](#refbib.xhtml#r81)\], E. Jaynes demonstrated two principal properties of entropy that were reflected by the RML procedures. First, by the first law of thermodynamics, entropy is a natural functional describing the processes of universal evolution. Second, by the second law of thermodynamics, entropy maximization yields the worst state of the evolutionary process under the worst external influences on it. Since randomization is a model of uncertainty, the RML procedures with entropy as Shannon's measure of uncertainty \[165\] allow us to obtain solutions under maximum uncertainty.

This book includes ten chapters covering the general issues of data generation and qualitative specifics, as well as the theoretical foundations of randomized machine learning and its applications to the problems of classification and dynamic regression.

[Chapter 1](#chapter1.xhtml) is of methodological character, discussing machine learning problems in general as a tool for knowledge extraction and further transformation into solutions. We consider the structure of a machine learning procedure that represents a man-machine system with feedback. The basic elements of this system are data blocks, parameterized models and algorithms. We introduce the main notions related to these blocks in a rigorous way. Data arrays are described by a fixed-dimension matrix consisting of the vectors of observable input variables or by a matrix containing a “sliding” set of vectors. A parameterized model is defined by a parameterized input–output mapping with a formal description in terms of a vector functional whose properties have a close relation to the qualitative peculiarities of a corresponding applied problem. In addition, we introduce the notions of deterministic and probabilistic ML algorithms that are used for model parameter estimation. In the former case, these are empirical risk minimization algorithms and in the latter case, likelihood maximization algorithms (or relative likelihood minimization algorithms). [Section 1.4](#chapter1.xhtml#sec1_4) presents the main material of this chapter, devoted to the concept of a randomized machine learning procedure based on maximization of an information entropy functional on a set configured by an existing data array. The information entropy functional is defined on the class of probability density functions for the characteristics of the parameterized model and measurement noises that simulate data errors. Finally, we discuss the relation between the maximization principle of the information entropy functional and the minimization principle of the log-likelihood ratio. Several examples illustrate the cognitive capabilities of randomized models.

[Chapter 2](#chapter2.xhtml) deals with data, to be more precise, data sources and primary data processing. We consider analog and digital data sources. Analog sources generate deterministic and also random functions. Some background on the classes of deterministic and random functions is given, with focus on analog-to-digital conversions. Such conversions (amplitude and time quantization) cause errors. According to standard assumptions, they are random with definite probability density functions. We also estimate quantization errors. Certain types of digital data are studied, namely, audio, graphical and text data as well as official government statistics. The technology used to generate data depends on their nature. In particular, audio data conversion is often performed by a pulse-code modulator with subsequent spectral representation using the discrete Fourier transform. There exist two methods to convert images into digital form—bit image graphics (arrays or matrices of pixels) and vector graphics (mathematical models of primitives). A special class of data is texts, as their digital representation contains word-usage frequency characteristics and also semantic features. Among important primary data processing methods, we mention restoration methods for missing data and reduction methods for data arrays. In the former group of methods, our analysis covers the methods of interpolation, design of auxiliary models and entropy decomposition.

An important stage to prepare data for model learning is to reduce their dimension. This stage is considered in [Chapter 3](#chapter3.xhtml). More specifically, common dimension reduction methods, such as the singular decomposition of data matrices, PCA and random projection, are overviewed therein. Particular attention in [Chapter 3](#chapter3.xhtml) is paid to the method of direct and inverse projections and its implementation in the form of sequential and parallel procedures. The projector matrices are optimized by minimizing the Kullback–Leibler divergence, taking into account the information capacity constraints imposed on the data matrix. A key issue in dimension reduction is to estimate its efficiency when solving RML problems. An efficiency estimation technique for linear models used for forecasting and binary classification is considered. The final paragraph of [Chapter 3](#chapter3.xhtml) is devoted to the entropy random projection method, in which the projector matrices are assumed to be random. The concept of a compactness indicator of a data matrix as the average distance between its rows is introduced. The problem of optimizing the probability density functions of the projector matrix is formulated as the problem of maximizing the corresponding entropy functional subject to constraints imposed on the compactness indicator of the projector matrix. A modification of the method with known projector matrices chosen randomly from a given set is considered.

[Chapter 4](#chapter4.xhtml) is devoted to randomized parametric models in the RML procedure. A distinguishing feature of randomized models that separates them into an independent class is their output in the form of an ensemble of random vectors or random trajectories. We consider two subclasses of randomized parametric models (RPMs), namely, the Single Input–Ensemble Output model and the (Single Input, Feedback)–Ensemble Output model. The RPMs of both subclasses are described using parameterized vector functionals whose properties (continuity, differentiability, boundedness and others) agree with the properties of a modeled object. We study their linear and nonlinear versions (power and polynomial nonlinearities) with interval-type parameters. Since the output of an RPM is an ensemble of random events, we introduce empirical probabilistic characteristics (empirical means, variances, PDFs, medians, *α*\-quantiles, confidence intervals and probabilities) as well as *k*\-moment and *k*\-mean characteristics for quantitative assessment.

After perusal of [Chapters 1](#chapter1.xhtml)–[4](#chapter4.xhtml), the reader moves on to [Chapter 5](#chapter5.xhtml) with a detailed treatment of the entropy-robust estimation problem for the PDFs of the model parameters and measurement noises. This problem is the core of the RML procedure. RPMs may have the so-called original parameters belonging to *n*\-dimensional parallelepipeds and also relative nonnegative parameters belonging to the *n*\-dimensional nonnegative unit cube. The same classification applies to the measurement errors. The parameters and noises are characterized by the corresponding PDFs. Output data arrays are in balance with the numerical characteristics of the output ensemble of an RPM, i.e., its *k*\-means. The entropy-robust estimation algorithm is formulated as a functional entropy-linear programming problem. We demonstrate that this problem belongs to the class of the Lyapunov-type optimization problems; hence, it can be solved using the Gateaux derivatives and Lagrange multipliers. We establish optimality conditions for the corresponding estimation problems, which yield a structural representation of the optimal PDFs parameterized by the Lagrange multipliers. The latter are defined by the solution of the balance equations written in universal forms. A peculiarity of these equations consists in the so-called integral terms, that is, the parameterized Riemann integrals determining the *k*\-mean characteristics of the output ensemble of an RPM.

[Chapter 6](#chapter6.xhtml) considers a special case of RPMs—the models with nonrandomized parameters. Recall that the uncertain model parameters and measurement noises lie within given intervals. Therefore, they can be transformed into nonnegative auxiliary variables belonging to the nonnegative unit cube. These variables are interpreted as the probabilities that the original parameters and noises belong to the corresponding original intervals. In other words, the auxiliary variables (the probabilities of belonging) are nonrandomized, and hence a parameterized model outputs a vector or trajectory defined by the values of these probabilities. The ML algorithm to estimate the probabilities of belonging is stated as a constrained maximization problem of the information entropy on a set defined by the empirical balance equations. The properties of the ML algorithm depend on the class of parameterized models under consideration. If the model is linear, then the ML algorithm is reduced to an entropy-linear programming problem. In the general case, it is reduced to an entropy-nonlinear programming problem.

[Chapter 7](#chapter7.xhtml) is focused on the computational methods of randomized machine learning that are intended for solving the functional entropy-linear programming problems of RPMs and also the entropy-nonlinear programming problems in order to estimate the probabilities of belonging of the nonrandomized model parameters to corresponding intervals. The optimality conditions of these problems are formulated as the nonlinear empirical balance equations. For the functional entropy-linear programming problems, these equations contain integral terms. Our idea is to solve the equations by minimizing a residual function, i.e., the solution is reduced to a minimization problem on a compact set. This problem has some specifics: the information about the objective residual function is available in the form of its values calculated algorithmically. A considerable part of calculations consists in the numerical integration of nonlinear exponential functions using the Monte Carlo method. We estimate the size of the random sequence required for achieving a given accuracy. The residual minimization problem is treated as a special case of the global minimization problem on a compact set defined by a system of inequalities with continuous functions. The solution procedure of this system also employs the Monte Carlo method, more precisely, the packet Monte Carlo iterations. This procedure generates packets of random vectors with the uniform distribution on the nonnegative unit cube, performs filtering of the resulting vectors to construct a packet of the vectors belonging to the admissible compact set, and selects the records for each packet. By analyzing the sequence of records, we estimate some numerical characteristics of the residual function (the Hölder constants). The described algorithm has almost sure convergence (with probability 1). Under a finite number of iterations, we calculate an *r*\-neighborhood of the exact global minimum and the probability that the iterative process reaches this neighborhood. The entropy-nonlinear programming problems are solved using multiplicative algorithms with *p*\-active variables. Finally, their convergence is studied (including the rate of convergence) and a series of examples are given.

The RML algorithms yield the entropy-optimal estimates for the PDFs of the model parameters and measurement errors. The next stage of the RML procedure is to generate the randomized parameters and measurement noises with the optimal PDFs. Generally speaking, this problem is traditional for the Monte Carlo method. There exists vast literature on the generation of random sequences with classical PDFs (Gaussian, uniform, etc.). Difficulties arise when it is necessary to generate random sequences and random vectors with a given PDF of arbitrary form. These difficulties are even more pronounced for the random vectors of high dimension.

[Chapter 8](#chapter8.xhtml) is devoted to the generation problems of random vectors with given PDFs of arbitrary form. In the beginning, this chapter surveys the existing generation methods of random sequences with some typical PDFs. Major attention is paid to the Metropolis–Hastings algorithm as a most popular method to generate random vectors with a given PDF. We suggest a new generation method based on the stepwise approximation of a given PDF and the subsequent formation of uniformly distributed random vectors using random mixing. The approximation stage includes two steps as follows. The first step is to choose an optimal size of the grid that covers the PDF support. Here optimization is implemented by calculating the Lipschitz constant of the PDF. The second step deals with the stepwise approximation problem, which is to choose the constant replacing the real values of the PDF on the grid nodes. We consider two options of this choice, namely, the constant minimizing the integral quadratic error functional and the average constant over the corner values of the grid nodes. Concluding [Chapter 7](#chapter7.xhtml), we demonstrate the experimental simulation results of the suggested method, comparing it with the Metropolis–Hastings algorithm on three lite PDF tests—the Gaussian distribution, the Laguerre distribution and the pseudo gamma distribution.

The RML problems are reduced to computationally intensive procedures that require considerable resources. [Chapter 9](#chapter9.xhtml) describes a general architecture of an information technology and software tools to develop a computational environment that implements the RML procedure. The suggested architecture is heterogeneous and guarantees an efficient utilization of computational devices of different types. We consider theinformation technology that implements the RML procedure and its software modules for the solution of global optimization problems, the generation of random vectors with a given PDF and the statistical processing of the randomized prediction ensembles.

[Chapter 10](#chapter10.xhtml) demonstrates how to use the RML procedure for the entropy classification. More specifically, we study the classification problems of heterogeneous objects into two classes in which classification is performed with the entropy-optimal probability for an existing data array. In some sense, soft classification represents an alternative to hard classification where the belonging to a certain class is uniquely defined. Under uncertain conditions (which are common for machine learning problems), hard classification often causes considerable errors. The randomized soft classification procedures use a neural network with random parameters as an RPM embedded in the additive model of measurements with errors described by a set of independent random vectors. The RML algorithm is formulated as a functional entropy-linear programming problem on the class of continuously differentiable PDFs for the neural network parameters and measurement errors. We suggest a procedure to find the probabilities of belonging of objects to appropriate classes based on the Monte Carlo method implementing the above entropy-optimal PDFs. Finally, several numerical examples are provided to illustrate the new method of soft classification.

[Chapter 11](#chapter11.xhtml) considers the application of the RML procedure to dynamic regression and randomized prediction. The restoration of the characteristics of dynamic relations between groups of variables is a widespread class of problems, both in context of theoretical studies and applications. A pragmatic goal of this research is to predict based on the dynamic relations between variables rather than to find the relations themselves. We study examples of dynamic regression problems arising in certain fields of demographic and macroeconomic research. Particular attention is given to randomized dynamic models of world population and forecasting of electrical load in the energy system.

The material for this book was accumulated over many years, following the development of information entropy maximization methods and their usage in different fields of science and engineering. The understanding that our studies are actually machine learning (more specifically, a new branch called randomized machine learning) has been formed recently. As information entropy is a natural functional that characterizes the PDFs of random parameters, it can be used as a functional for the variational principle in the following sense: the best PDF corresponds to the maximum information entropy. On the other hand, information entropy is interpreted as a measure of uncertainty. An integration of these two fundamental properties of information entropy has yielded the concept of randomized (entropy-optimal) solutions.

The authors are grateful to Professors B.T. Polyak and B.S.Darkhovsky for fruitful discussions that facilitated a system comprehension of the concept of randomized machine learning by the authors and (which is equally important) delivered the authors from potential delusions and mistakes. The book could not have appeared without support of Yugorsky Research Institute of Information Technologies and its director, Dr. S., Professor A.B. Melnikov. Special thanks to A.S. Aliev, Cand. Sci. (Eng.), for the experimental studies.

Finally, the authors express gratitude to A.Yu. Mazurov, Cand. Sci. (Phys.-Math.), for his careful translation of the Russian text, permanent feedback and negotiations with the publisher.

On behalf of the authors,

Yuri S. Popkov

Moscow, 2022

# CHAPTER 1 GENERAL CONCEPT OF MACHINE LEARNING

DOI: [10.1201/9781003306566-1](https://doi.org/10.1201/9781003306566-1)

Machine learning procedures are a backbone element of the toolkit to generate problem-oriented information for the support of different decisions. An important aspect in the formation of these procedures is their structuring under a considerable uncertainty caused by imperfect knowledge about the operation of real objects or phenomena and various data defects (errors, incompleteness, omissions, and so on). In this chapter, we classify three methodological approaches to the machine learning toolkit, each being based on fundamentally different principles—deterministic, probabilistic and randomized. The first approach involves deterministic models, measured data arrays and nonrandom parameter estimation. The second approach proceeds from the hypotheses about the random origin of the model parameters and measurement noises, and their probabilistic characteristics, which are used to construct nonrandom parameter estimates. Within both approaches, the learned models remain deterministic with the parameters whose values are the optimal estimates yielded by learning. Finally, the third approach stems from an artificial randomization of the model parameters and measurement noises and an estimation of their PDFs.

## 1.1Transformation of Knowledge into Decisions

A necessary, useful and, sometimes, favorite activity of an individual is to make short-, medium- and long-term decisions. At the same time, we want to know guidelines of an individual, i.e., his motivational background for a certain decision. Unfortunately, there exist no universal or scientifically grounded approaches to discover this background. Perhaps, such approaches are impossible in principle, as individual decisions are personalized and their motives are implicit. Even questioning procedures or opinion polling techniques do not guarantee that an individual is frank in his answers. To all appearance, one may consider some collective (average) decisions and their motives.

The decisions of an individual affect certain objects of the material, natural and spiritual worlds, thereby changing their spatiotemporal state. The motivational mechanisms of an individual evolve in parallel to these processes but in another time scale. As a result, new decisions occur, often being caused by other motives.

In other words, motivations and decisions based on them interact within a cyclic procedure *M*→*D* (*Motivations–Decisions*) with a feedback loop *FL* as a crucial element of its “structure”. The functional stages of the *M*→*D* procedure and their sequence are illustrated in [Fig. 1.1](#chapter1.xhtml#f1_1).

![Figure 1.1](images/fig1_1.jpg)

[Figure 1.1](#chapter1.xhtml#f1_1b)

Individual motivations (*IM*) form a basis for the decision-making process (*DM*) focused on the evolution of a studied object (*O*) or problem. This leads to the appearance of information in the object, particularly in the form of new data (*D*), which supplements the existing knowledge (*K*) about it. Let us accept a “daring” hypothesis that motivations rest on the knowledge accumulated by an individual. In the sequel, knowledge will be interpreted as an abstract intellectual basis that includes knowledge in the utilitarian understanding, intuition as a product of the subcortical processes of the brain, personal and public experience, data about the object, and so on. However, knowledge is a passive substance that does not activate motivations itself. Using knowledge, it is necessary to form a picture of the world, i.e., a model of a current situation for decision-making. A model arises from a combination of existing data and the beliefs of an individual about the character of this situation. Representing a causing factor of motivations, the situation is a set of certain measurable characteristics (*parameters*) of the model and relations among them.

For assigning a quantitative description to the model based on the available data, the model parameters have to be *estimated* numerically. In this case, it is possible to solve different problems and predict their future trends. The feedback loop of the *M*→*D* cycle is implemented by a machine learning (ML) procedure with a necessary toolkit to design quantitative models and organize informational support of motivated decision-making.

Therefore, the ML procedure finds a methodological, algorithmic and information technology-based content in the *M*→*D* transformation, as shown in [Fig. 1.1](#chapter1.xhtml#f1_1).

From the very beginning, note that this logical chain is merely a version of the motivational mechanism that is fruitful for this monograph and does not claim to be of universal value.

As an example, it seems appropriate to consider the *M*→*D* procedure intended for the transport behavior modeling of individuals \[[125](#refbib.xhtml#r125)\]. Numerous acts implementing this behavior actually form traffic flows in an urban transport network.

Here, two aspects of the transport behavior will be analyzed, namely, the individual and collective behavior. The former is based on the motivations of an individual regarding transport vehicles, the goals of trip and routes. These motivations can be related to the time and cost of trip, the level of comfort and other characteristics. There exist numerous factors that affect the motivations of an individual. They can be specific for each individual. Consequently, the environment of individual motivations becomes essentially uncertain.

On the other hand, there are very many users of transport vehicles (including private and public transport), and their motivations and transport decisions are independent. And so, the stochastic framework is suitable to model the corresponding uncertainty. Really, we cannot follow motivations and decisions of each individual, but their collective motivations can be characterized using some indicators of individual motivations. Due to the stochastic character of the uncertainty model, these characteristics are probabilistic, more specifically, the probability distribution functions of transport events. A widespread indicator of a transport event is trip time. In terms of this indicator, collective motivations are characterized by the so-called resettlement function that describes distributions of individuals by trip time. After normalization, this function can be treated as the probability distribution function of trip-time utilization.

The above-mentioned indicators reflect the collective motivations intrinsic to some average individual. But they have no relation to the real assessment of a current transport situation and its forecasting. However, the former and latter are the integral components of transport decision-making. It is impossible to consider the procedural part of these components for each individual. We can study collective decisions only, e.g., the choice of routes. If there exists a finite set of admissible routes from a certain location, then the probability of route choice can be an aggregated result of estimation and forecasting.

Another example of the *M*→*D* procedure is the interaction process of population and an economy that runs in a demoeconomic system ([Figs. 1.2(a)](#chapter1.xhtml#f1_2)–[c](#chapter1.xhtml#f1_2)). Due to intelligence, population is a tool of self-development, which results in generation of different types of human activity. Economic activity represents one of such types. By assumption, an economically motivated individual is the main tool of self-development.

![Figure 1.2](images/fig1_2.jpg)

[Figure 1.2](#chapter1.xhtml#f1_2b)

Being involved in economic activity, population depends on its results. A key role in this process is played by the assessment of economic situation and the forecasting of possible consequences for decisions. The internal status of population also changes accordingly.

There exists a some kind of closed loop containing population and economic activity, with assessment, forecasting and feedback. Note an obvious analogy with the interaction procedure of motivations and decisions; see the structural diagram in [Fig. 1.1](#chapter1.xhtml#f1_1).

An economy as a macroobject transforms resources into a product (see [Fig. 1.2(a)](#chapter1.xhtml#f1_2)). Labor, i.e., the labor activity of people in the economic sphere, is a resource. A certain product manufactured by an economy and consumed by population (in some form, see [Fig. 1.2(b)](#chapter1.xhtml#f1_2)) modifies the structure of population—its internal clustering and the quantitative form, and status of clusters (groups of population). As a result, other groups of different sizes are involved in economic processes at a new spiral of development.

Therefore, one can speak about an integral population-economy (*PE*) system consisting of the population (*P*) subsystem and the economy (*E*) subsystem that form a closed loop, as shown in [Fig. 1.2(c)](#chapter1.xhtml#f1_2). An important field of analysis of this integral system deals with the procedures of situation assessment (state estimation) and forecasting, i.e., the evolution with the course of time. For each subsystem, these problems are studied by corresponding sciences. For example, the structural dynamics of population is the subject of macrodemography. A whole bunch of economic disciplines (political economy, macro- and microeconomics, mathematical economics, etc.) consider the formation and evolution of economic structures. Note that the economic factors affecting different processes in the Population subsystem are treated in macrodemography as the external factors related to the impact of a metasystem. Actually, a similar situation occurs in economic disciplines. The behavior of the Economy subsystem is studied under the condition that the Population subsystem reproduces labor resources of a definite volume and structure.

In particular, a popular line of demographic research is the forecasting of population state indicators under a given economic scenario described in quantitative terms \[[40](#refbib.xhtml#r40)\]. Moreover, such scenarios reflect certain economic goals that (generally) have no relation to the potential changes of population within a forecasting period. But these changes considerably affect the indicators of economic development to be achieved. The above-mentioned feedback relation objectively exists, and an attempt to ignore it often causes unrealizable forecasts.

Also, note another peculiarity of this object, which is estimated and forecasted using ML procedures. Each of its parts has internal behavior (without the influence of a metasystem) and also disturbed behavior (under certain impacts applied by the metasystem). In this context, we mean states (equilibria, cycles, attractors, etc.), their stability and other properties. However, when the Population and Economy subsystems are united in an integral system, the latter may acquire new properties differing from the initial properties of these parts. Such a system effect particularly reveals itself in the case of nonlinear relations within each subsystem, and also in the case of nonlinearities in the channels used by one subsystem to influence the other. As a result, the integral system may have other equilibria and also other nonequilibrium processes. For such a system, state estimation and forecasting are actually not a trivial problem. Here additional difficulties arise due to a high level of uncertainty of the environment, for the separate subsystems and also for the entire system. The source of this uncertainty is an individual, the main component of both subsystems, with his motivations, social and professional characteristics, and behavioral responses.

Consequently, it seems that the situation here resembles the previous example. The Population–Economy system cannot be replicated, i.e., the internal processes running in this system never recur even for the same operation conditions. This system is self-developing, which eliminates the real repetitiveness of its processes. Therefore, the uncertainty that accompanies the operation of the Population–Economy system is reproduced by a simulation model with parameter estimation using available information.

## 1.2Structure of Machine Learning Procedure

Methods and algorithms embedded in the ML procedures are quite diverse. However, they all have the same methodological orientation and structure. The latter is understood as a sequence of functional stages to transform knowledge into informational decision support. The structure of this procedure is shown in [Fig. 1.3](#chapter1.xhtml#f1_3). The procedure includes four stages as follows.

![Figure 1.3](images/fig1_3.jpg)

[Figure 1.3](#chapter1.xhtml#f1_3b)

The first stage (PM) lies in the development of a mathematical model that describes the operation mechanisms of a studied object and a measurement model of its input and output. The mathematical model of the object transforms knowledge about it into a structure with a list of definite characteristics. This stage cannot be formalized in such a general statement. However, often there exists prior information about the class of objects and problems that have to be modeled using a mathematical framework. Here “class” means an aggregate of objects or problems that have a set of common properties. If this set is known, then it is possible to construct a conceptual model for a corresponding class \[[68](#refbib.xhtml#r68)\]. Such a model consists of a list of interconnected concepts that describe a given class, together with the properties, characteristics and classification of these concepts. An important component of conceptual modeling is to reflect the regularities of internal processes running within the objects of a given class \[[16](#refbib.xhtml#r16)\]. In other words, a conceptual model systematizes and structures the existing knowledge about a class of objects and problems under study. The formation of such classes is a nontrivial problem whose complexity essentially depends on the degree of abstraction in their description. For example, the general theory of systems operates abstract sets and their relations (hierarchical systems, feedback, etc.) \[[119](#refbib.xhtml#r119)\]. The classes produced by such a descriptive approach possess a rather high power (as they incorporate a large number of systems) but their conceptual models are often unconstructive. On the contrary, any attempt to add specific properties to an abstract class reduces the power of the new class, albeit yielding a better conceptual model in the sense of constructiveness. A good example is the class of controlled technical systems \[[91](#refbib.xhtml#r91)\].

In most cases, a conceptual model represents a graph where nodes correspond to its functional elements and arcs to the mutual relations among them. As a matter of fact, this comprehension of a conceptual model was first introduced in \[[54](#refbib.xhtml#r54)\]. Further complication and deeper specification of the properties intrinsic to different classes of systems outlined a gradual transition to a more efficient description, namely, to specially structured lists called ontologies \[[169](#refbib.xhtml#r169)\]. Still, the graphical and ontological descriptions of classes retained the level of functional elements. These elements are described using various mathematical tools, depending on the regularities embedded in their operation mechanisms and also on their characteristics. In the case of *parametric characteristics*, the mathematical models of the elements are functional relations (for the description of static elements) or the systems of differential equations of different types (for the description of dynamic elements) \[[50](#refbib.xhtml#r50), [161](#refbib.xhtml#r161)\]. A rather efficient parameterization approach to static relations involves neural networks \[[96](#refbib.xhtml#r96)\]. A relative simplicity of the basic elements and parameter tuning algorithms of these models allows to use neural networks for high-dimensional spaces.

Sometimes, for convenience the dynamics of an object are described using mathematical models with *functional characteristics*. For example, this class includes the models defined by integral equations or functional series \[[111](#refbib.xhtml#r111), [137](#refbib.xhtml#r137), [146](#refbib.xhtml#r146), [152](#refbib.xhtml#r152)\]. The role of functional characteristics in such models is played by the kernels of integral equations or functional series.

For a finite-state object, adequate models are automata \[[72](#refbib.xhtml#r72), [107](#refbib.xhtml#r107)\], nonlinear sequential machines \[[18](#refbib.xhtml#r18), [177](#refbib.xhtml#r177)\], and dynamic intelligent systems that operate in accordance with certain rules \[[126](#refbib.xhtml#r126)\].

An important element of this stage is to model measurements. The real measurements of the object's input and output incorporate errors, and hence it is necessary to simulate them somehow. By a standard hypothesis, an independent random process is a rather adequate simulation model for the source of measurement errors. There exist two structural representations of the influence exerted by the errors on the observable output of the object's model, namely, the additive and multiplicative ones. The choice of an appropriate representation depends on the design properties of the device used to measure the object's output and input.

The second stage (PE) of the ML procedure (see [Fig. 1.3](#chapter1.xhtml#f1_3)) serves to estimate the characteristics of the mathematical model using real data that are generated as a *learning* sequence. As a matter of fact, this stage can be implemented with numerous methods. If the model characteristics are uncertain parameters, the corresponding estimation methods form the subject of mathematical statistics \[[11](#refbib.xhtml#r11), [34](#refbib.xhtml#r34), [90](#refbib.xhtml#r90)\]. The estimation problems of increasing complexity arise when the mathematical model has functional characteristics, e.g., the kernel of an integral equation or the impulse-response characteristics of a functional series. Of course, in this case a finite-dimensional approximation of the estimation problems can be performed. But this approach often leads to a high dimension of the resulting approximation, thereby requiring greater volumes of data about the object's operation.

ML procedures consider the estimation problem as the minimization of the empirical risk functional with respect to the corresponding characteristics of the model, i.e., parameters or functions. Here the term “empirical” means that the functional is designed for a learning sequence. A prominent part is assigned to data packets for the object's input and output. Under fixed characteristics of the model, the input data are used to generate its output, which is then compared with the real output in terms of the empirical risk functional. This functional depends on the model characteristics so that their variation also affects the value of the functional. Empirical risk minimization yields the estimates of the model characteristics. The model together with its characteristics calculated in this way is *optimal* for the learning sequence and functional under consideration.

In the third stage (MT) of the ML procedure, the optimized (“learned”) model is tested on other packets of the retrospective input and output data. Testing lies in comparing the real output of the object with the output generated by the optimized model, in terms of an accepted criterion. If the optimized model demonstrates a satisfactory level of quality on the test data packets, the model can be used in the normal operation mode.

The last (fourth) stage of the ML procedure (the MI stage) is intended to accumulate experience, i.e., new knowledge for a structural correction of the parameterized model at the PM stage and also for a refinement of the estimation algorithms at the PE stage.

Note that this procedure runs under uncertainty caused by limited knowledge about a studied object and its mathematical model, a finite size of learning sequences that incorporate information about the object's operation, measurement errors, and so on. Therefore, each stage of the ML procedure proceeds from certain hypotheses on the character of uncertainty.

## 1.3Main Concepts of Machine Learning Procedure

As illustrated by the block diagram in [Fig. 1.3](#chapter1.xhtml#f1_3), the ML procedures consist of four stages, namely, the choice and parameterization of the model (the PM stage); the formation of input (cause) and output (effect) data arrays and model parameter estimation using these arrays (the PE stage); the formation of data arrays for optimized model testing (the MT stage); and the generation of the optimized model (the MI stage).

As mentioned earlier, the first stage—*the choice and parametrization of the model*—is nonformalizable and involves only the available knowledge about a studied object, phenomenon or problem. This choice gives the elements of the *n*\-dimensional input vectors $\\overset{\\rightarrow}{x}(t) \\in \\mathfrak{X},$ where 𝔛 denotes the space of input functions, and also the elements of the *m*\-dimensional output vectors $\\overset{\\rightarrow}{y}(t) \\in \\mathfrak{Y},$ where 𝔜 denotes the space of output functions; *t* is a scalar parameter.

The elements of these vectors can be measured in continuous time *t* ∈ 𝒯 = \[*t*[0], *T*\] and in discrete time with an arbitrary step, $\\left\\{ t\_{0},t\_{1},\\ldots,t\_{s} \\right\\} \\in \\widetilde{\\mathcal{T}},$ or with a fixed step *h*, $\\left\\{ t\_{0},t\_{0} + h,\\ldots,t\_{0} + sh \\right\\} \\in {\\widetilde{\\mathcal{T}}}\_{h}.$ For the time being, consider the last-mentioned measurement scheme, which yields the two-dimensional arrays of the input and output data of sizes (*n* × *s*) and (*m* × *s*), respectively, i.e.,

  
$$\\begin{array}{r} {\\mathbb{X} = \\left\\{ {\\overset{\\rightarrow}{x}}^{(0)},\\ldots,{\\overset{\\rightarrow}{x}}^{(s)} \\right\\},\\text{\\quad\\quad}\\mathbb{Y} = \\left\\{ {\\overset{\\rightarrow}{y}}^{(0)},\\ldots,{\\overset{\\rightarrow}{y}}^{(s)} \\right\\}.} \\\\ \\end{array}$$  
(1.1)

In addition, define the following input array that contains a current set of *ϱ* measured vectors:

  
$$\\begin{array}{r} {\\mathbb{X}\_{\\varrho}^{(j)} = \\left\\{ {\\overset{\\rightarrow}{x}}^{(j - \\varrho)},{\\overset{\\rightarrow}{x}}^{(j - \\varrho + 1)},\\ldots,{\\overset{\\rightarrow}{x}}^{(j)} \\right\\},\\text{\\quad\\quad}\\varrho \\leq j \\leq s.} \\\\ \\end{array}$$  
(1.2)

In the first stage, also choose a model with parameters $\\overset{\\rightarrow}{a} \\in R^{p}$ using a rather general description in terms of a vector functional *Ω̂*, that maps the input space 𝔛 into the output space $\\hat{\\mathfrak{Y}}$ as follows:

  
$$\\begin{array}{r} {{\\hat{\\overset{\\rightarrow}{y}}}^{(j)}(\\mathbb{X}\_{\\varrho}^{(j)},\\overset{\\rightarrow}{a}) = \\hat{\\Omega}\\left( {\\mathbb{X}\_{\\varrho}^{(j)},\\overset{\\rightarrow}{a}} \\right).} \\\\ \\end{array}$$  
(1.3)

In this expression, the variable *ϱ* is the number of the input vectors that affect the output vector. If 𝜚 > 0, then the functional under consideration characterizes the dynamic properties of a studied object, phenomenon or problem, i.e., their “memory” in some sense. In the case 𝜚 = 0, the output of the model in the *j*th observation (measurement) depends only on the input vector in the *j*th observation (measurement). Such relations are typical for static objects, phenomena or problems.

The parameters $\\overset{\\rightarrow}{a}$ of the model (1.3) are assumed to be *deterministic* but with unknown values. These values are estimated using ML algorithms on the basis of available data and certain hypotheses about their prior properties. ML algorithms perform minimization of some functionals with qualitative interpretations that proceed from the accepted hypotheses. Note that ML algorithms yield estimates for the deterministic characteristics of the model, regardless of the functional selected.

One of such hypotheses treats the data and parameters as *deterministic* sets of real or integer numbers, without making additional assumptions on their properties. Then the optimal estimation of the model parameters is performed in terms of a *vector loss function* of the form

  
$$\\begin{array}{r} \\left. {\\overset{\\rightarrow}{e}}^{(j)}(\\overset{\\rightarrow}{a}\\, \\middle| \\, X^{(j)},{\\overset{\\rightarrow}{y}}^{(j)}) = {\\overset{\\rightarrow}{y}}^{(j)} - {\\hat{\\overset{\\rightarrow}{y}}}^{(j)}(X^{(j)},\\overset{\\rightarrow}{a}),\\quad j = \\overline{1,s}, \\right. \\\\ \\end{array}$$  
(1.4)

and the closeness of the PM output to the output data of the object is characterized by its norm known as *the empirical risk*, i.e.,

  
$$\\begin{array}{r} \\left. \\mathcal{Q}\_{X,Y}(\\overset{\\rightarrow}{a}) = \\frac{1}{s}{\\sum\\limits\_{j = 1}^{s}{\\|{\\overset{\\rightarrow}{e}}^{(j)}(}}\\overset{\\rightarrow}{a}\\, \\middle| \\, X^{(j)},{\\overset{\\rightarrow}{y}}^{(j)})\\|. \\right. \\\\ \\end{array}$$  
(1.5)

The empirical risk minimization methods are defined by the family of ML algorithms \[[53](#refbib.xhtml#r53), [106](#refbib.xhtml#r106), [188](#refbib.xhtml#r188)\] in which

  
$$\\begin{array}{r} {\\hat{\\overset{\\rightarrow}{a}}(X,\\overset{\\rightarrow}{y}) = \\arg\\min\\mathcal{Q}\_{X,Y}(\\overset{\\rightarrow}{a}).} \\\\ \\end{array}$$  
(1.6)

An additional hypothesis about the properties of the data and parameters often lies in the assumption that the data *Z* = (*X*, *Y*) and the parameters $\\overset{\\rightarrow}{a}$ are *random objects* with a joint probability density function $P(Z,\\overset{\\rightarrow}{a}).$ Here *Z* denotes the universe of data and $\\overset{\\rightarrow}{a}$ is a random vector. In this case, the observable data arrays represent samples *Z*^((*j*)) from the universe *Z*. Note that each of them is random and independent with the PDF $P(Z^{(j)},\\overset{\\rightarrow}{a}).$

The joint probability density function

  
$$\\begin{array}{r} {L(Z^{(1)},\\ldots,Z^{(s)};\\overset{\\rightarrow}{a}) = {\\prod\\limits\_{j = 1}^{s}P}(Z^{(j)},\\overset{\\rightarrow}{a})} \\\\ \\end{array}$$  
(1.7)

is called the *likelihood* function for a sample {*Z*^((1)),…,*Z*^((*s*))} \[[41](#refbib.xhtml#r41), [51](#refbib.xhtml#r51)\]. Under a fixed sample, the likelihood function depends on the parameter $\\overset{\\rightarrow}{a}.$ A quite natural estimate of this parameter is the vector that maximizes the likelihood function. Instead of the likelihood function, a convenient approach is to use its logarithm *L̃* = log *L*, i.e.,

  
$$\\begin{array}{r} {\\hat{\\overset{\\rightarrow}{a}}(Z^{(1)},\\ldots,Z^{(s)}) = \\arg\\max\_{\\overset{\\rightarrow}{a}}\\widetilde{L}(Z^{(1)},\\ldots,Z^{(s)};\\overset{\\rightarrow}{a}).} \\\\ \\end{array}$$  
(1.8)

The hypothesis about the random origin of the pair (*Z*, $\\overset{\\rightarrow}{a}$) also has another interpretation related to the accumulation of information about this pair during experiments. Here, we mean its characteristics expected *before experiments* and the real characteristics obtained *after experiments*. To describe this evolution, Bayes suggested the concept of conditional probability, distinguishing between the *prior* and *posterior* probabilistic characteristics of the data and parameters. As a result, the posterior conditional probability density function (or simply posterior conditional density) $\\left. p({\\mathbb{Z}}\\, \\middle| \\,\\overset{\\rightarrow}{a}) \\right.$ of data under fixed parameters, the prior conditional probability density function $\\left. w(\\overset{\\rightarrow}{a}\\, \\middle| \\,{\\mathbb{Z}}) \\right.$ of parameters under fixed data, and the prior probability density function *g*(ℤ) were introduced accordingly. They have a clear relation defined by Bayes' formula

  
$$\\begin{array}{r} \\left. p({\\mathbb{Z}}\\, \\middle| \\,\\overset{\\rightarrow}{a}) = \\frac{\\left. w(\\overset{\\rightarrow}{a}\\, \\middle| \\,{\\mathbb{Z}})g({\\mathbb{Z}}) \\right.}{\\left. {\\int\\limits\_{\\mathbb{Z}}w}(\\overset{\\rightarrow}{a}\\, \\middle| \\,{\\mathbb{Z}})g({\\mathbb{Z}})d{\\mathbb{Z}} \\right.}. \\right. \\\\ \\end{array}$$  
(1.9)

The posterior conditional density maximization methods are defined by the family of Bayesian ML algorithms

  
$$\\begin{array}{r} \\left. \\hat{\\overset{\\rightarrow}{a}}({\\mathbb{Z}}) = \\max\_{\\overset{\\rightarrow}{a}}p({\\mathbb{Z}}\\, \\middle| \\,\\overset{\\rightarrow}{a}). \\right. \\\\ \\end{array}$$  
(1.10)

Both of the families (1.8, 1.10) employ the joint probability density functions of the data and parameters under the accepted hypotheses about the probabilistic properties of random objects.

## 1.4Principles of Randomized Machine Learning Procedure

The RML concept rests on two principles as follows. The first principle is the computer simulation principle for the *ensembles* of randomized decisions, vectors or trajectories caused by uncertainty. In other words, the existing uncertainty is compensated through the generation of an *ensemble* of decisions, vectors or trajectories. However, it is desirable to generate *optimal* ensembles in a certain sense, not any ensembles. This leads to the second principle known as the optimization principle for the generated ensembles, which *maximizes information entropy*.

The following examples illustrate the new properties arising in the randomized models.

Summarizing the aforesaid, one of the implementation principles of the RML concept lies in the generation of the ensembles of random events (decisions, vector or trajectories) with desired probabilistic characteristics. They are generated using the model (1.3) with the randomized parameters **a** obeying a desired PDF. In other words, it is necessary to generate an ensemble of the random vectors **a** with given PDFs.

The second fundamental principle of the RML concept is the optimization principle of the randomized model adopted to calculate the optimal PDFs of the model parameters. Here an important stage consists on the choice of an appropriate quality functional. In our case, this (often debatable) question has a well-justified answer. As emphasize earlier, the RML concept is a tool to obtain best decisions under maximum uncertainty. Recall that the uncertain knowledge about an object under study is described by randomized model parameters, uncertain data by additional noises and uncertain estimates by probability density functions.

In the sequel, **the information entropy functional** will be used to characterize the quality of a randomized model. The maximum of this entropy corresponds to the highest uncertainty of our knowledge about the object and noises intrinsic to measured data. An interpretation of information entropy as a measure of uncertainty (with the minus sign, as a measure of information) was first suggested by C. Shannon in his pioneering paper \[[165](#refbib.xhtml#r165)\], which motivated intensive research in mathematics, statistical thermodynamics, communication theory and other fields of science. A next surge of interest in information entropy is related to the name of E. Jaynes \[[80](#refbib.xhtml#r80)\], who proved that the entropy maximization principle yields best solutions under maximum uncertainty. In particular, this principle allows to find best solutions under the worst-case probabilistic characteristics of data measurement noises \[[66](#refbib.xhtml#r66), [88](#refbib.xhtml#r88), [109](#refbib.xhtml#r109), [141](#refbib.xhtml#r141), [153](#refbib.xhtml#r153), [157](#refbib.xhtml#r157)\]. This feature of the information entropy maximization principle is treated as the “entropy”-*robust* property of the resulting solutions.

# CHAPTER 2 DATA SOURCES AND MODELS

DOI: [10.1201/9781003306566-2](https://doi.org/10.1201/9781003306566-2)

For machine learning procedures, data is important, like their sources, degree of adequacy (measurement errors), volume, properties, and features. We comprehend data as sets of numbers that are associated with certain times and organized in arrays with appropriate properties. If a data source is not of natural origin (e.g., an analog oscillogram), then the data have to be transformed into a structured numerical array.

Although ML procedures involve numerical data, in many cases it is useful to consider information about the general properties of functions that describe data samples. The character of data has a close relation to the source objects whose states are measured in these data. There exist analog and digital data sources.

An analog source is characterized by the functions of continuous argument. They are measured using analog sensors and mostly represent the functions of time and/or space for spatially distributed objects. The classes of such functions and their common properties generate some properties of samples drawn from them.

A digital source contains a digital sensor that outputs all measured data with amplitude (level) and time quantization. A particular case is a binary digital source in which a digital quantizer has only two levels and the resulting data represent a sequence of zeros and ones associated with discrete times.

Depending on further usage, data can be transformed from one class to another. For example, analog data are transformed into digital data using analog-to-digital converters (ADCs) for further computer processing. Sometimes, it is necessary to transform digital data into analog data, which is performed by digital-to-analog converters (DACs). Such converters find wide application in the field of audio, video and graphical data processing.

A crucial problem consists in the adequacy and argument completeness of data. If argument is time, then complete data contain numbers for all times on a fixed time interval. Data adequacy relates to measurement errors, which are often described by random errors with appropriate properties.

## 2.1Analog Source of Data

An analog source is a measuring system (an analog sensor), i.e., a transducer that performs transformation of a certain indicator of a real process into a scalar function *x*(*t*) or a vector function $\\overset{\\rightarrow}{x}(t)$ defined on a time interval 𝒯 = \[*t*[0], *T*\]; times *t* within this interval are real numbers. Some examples of analog sensors include tachometers measuring speed, accelerometers measuring acceleration, spectrometers measuring the spectral composition of a substance, etc.

### 2.1.1Deterministic functions

First, consider in brief the general properties of deterministic functions.

1.  The identity axiom: *ρ*[𝒯](*t*[*i*], *t*[*j*]) = 0 only for *t*[*i*] = *t*[*j*].
    
2.  The symmetry axiom: *ρ*[𝒯](*t*[*i*], *t*[*j*]) = *ρ*[𝒯](*t*[*j*], *t*[*i*]).
    
3.  The triangle axiom: *ρ*[𝒯](*t*[*i*], *t*[*j*]) + *ρ*[𝒯](*t*[*j*], *t*[*k*]) ≥ *ρ*[𝒯](*t*[*i*], *t*[*k*]), where *t*[*i*] < *t*[*j*] < *t*[*k*].
    

Such a function can be always defined on a time interval 𝒯. Therefore, 𝒯 forms a metric space. This metric space (of real numbers) is of course very simple. However, the metric spaces of scalar and vector functions can be constructed by analogy. An element *t*^(\*) is the limit of a sequence *t*[0], *t*[1], … if *ρ*(*t*[*n*],*t*^(\*))→0 as *n*→∞.

Consider two metric spaces, 𝒴 and 𝒯, and a function *y* = *x*(*t*) taking values in 𝒴. A function *x*(*t*) is called *continuous at a point *t*^(\*) ∈ 𝒯* if for any *ε* > 0 there exists a *δ* > 0 such that *ρ*[𝒴](*x*(*t*), *x*(*t*^(\*))) < *ε* for any other point *t* ∈ 𝒯 satisfying the inequality *ρ*[𝒯](*t*, *t*^(\*)) < *δ*. By the definition of a continuous function *x*(*t*), the convergence *t*[*n*]→*t*^(\*) implies the convergence *x*(*t*[*n*])→*x*(*t*^(\*)).

If this property applies to all the points *t* ∈ 𝒯, then a corresponding function *x*(*t*) *is uniformly continuous on 𝒯*. Denote by *C*^((0)) the class of all these functions.

Continuity (and uniform continuity) can be extended to the derivatives of a function *x*(*t*), provided that they exist. And the classes of *smooth functions* with a definite degree of smoothness arise accordingly. The degree of smoothness is the maximum order of derivatives that exist for the functions of a given class. For example, the class *C*^((1)) contains the continuously differentiable functions (first-order derivatives) whereas the class *C*^((*r*)) the derivatives of order *r*. A substantial subclass of smooth functions denoted by *C*^((∞)) consists of *analytical functions*, which are differentiable infinitely many times on their domains of definition. In particular, an analytical function *x*(*t*) defined on a time interval 𝒯 has infinitely many derivatives *x*^((*k*))(*t*), *k* = 1, 2, ..., on this interval. At any point *t*[0] of the interval 𝒯, it can be expanded into the uniformly convergent Taylor series:

  
$$\\begin{array}{r} {x(t) = x(t\_{0}) + \\left. ~{\\sum\\limits\_{i = 1}^{\\infty}\\frac{d^{i}x(t)}{dt^{i}}} \\right|\_{t\_{0}}{(t\_{0} - t)}^{i},\\quad t\_{0} \\in \\mathcal{T}.} \\\\ \\end{array}$$  
(2.1)

A certain quantitative characteristic can be assigned to continuity as a qualitative property of functions. More specifically, it is possible to introduce the so-called *module of continuity*

  
$$\\begin{array}{r} \\left. \\omega(h) = \\max\_{|t\_{i} - t\_{j}| \\leq h} \\middle| x(t\_{i}) - x(t\_{j}) \\middle| . \\right. \\\\ \\end{array}$$  
(2.2)

If a function *x*(*t*) has a module of continuity

  
$$\\begin{array}{r} {\\omega(h) \\leq Hh^{s},\\quad(H,s) \\geq 0,} \\\\ \\end{array}$$  
(2.3)

then it belongs to the continuous Hölder functions, where *H* and *s* are the Hölder constants.

If a function *x*(*t*) has a module of continuity

  
$$\\begin{array}{r} {\\omega(h) \\leq Lh,\\quad L \\geq 0,} \\\\ \\end{array}$$  
(2.4)

then it belongs to the continuous Lipschitz functions, where *L* is the Lipschitz constant.

An important characteristic of any function is its variability on a time interval 𝒯, more specifically, whether such variability is finite or infinite. The functions with finite variability form the class of functions of bounded variation. To define this property, consider an arbitrary partition of the time interval 𝒯 into an ordered sequence of points *t*[0], *t*[1], …, *t*[*n*] and the increments (decrements) of a function *x*(*t*) at these points. If

  
$$\\begin{array}{r} \\left. \\left. \\sum\\limits\_{i = 0}^{n} \\right|x(t\_{i + 1}) - x(t\_{i}) \\middle| = X\_{\\mathcal{T}} < + \\infty \\right. \\\\ \\end{array}$$  
(2.5)

for any sequence of points on 𝒯, then *x*(*t*) belongs to the class of functions of *bounded variation*. The value *X*[𝒯] is called the total variation of the function *x*(*t*) on the time interval 𝒯.

The class of functions of bounded variation includes the functions that have additional properties. For example, the continuous functions and the functions with any degree of smoothness belong to the class of functions of bounded variation. If a function *x*(*t*) is monotonic, i.e., the expression

  
$$\\begin{array}{r} \\frac{x(t\_{i}) - x(t\_{j})}{t\_{i} - t\_{j}} \\\\ \\end{array}$$  

is of the same sign or vanishes for any *t*[*i*], *t*[*j*] from 𝒯, then it belongs to the class of functions of bounded variation, and its total derivative is given by *X*[𝒯] = *x*(*T*) − *x*(*t*[0]). Note that the class under consideration also contains the functions with jump (simple) discontinuities.

Different approximations are used to study the properties of the above-mentioned classes of functions and to generate the well-grounded sets of discrete data associated with them. The approximation methods operate the fundamental concepts of an approximation quality functional and an approximating function *x*[*a*](*t*) from a given class. The following functionals are widespread:

*   the Chebyshev functional
    
      
    $$\\begin{array}{r} \\left. C = \\max\_{\\mathcal{T}} \\middle| x(t) - x\_{a}(t) \\middle| ; \\right. \\\\ \\end{array}$$  
    (2.6)
    
*   the integral quadratic functional
    
      
    $$\\begin{array}{r} \\left. J\_{2} = \\left. \\int\\limits\_{\\mathcal{T}} \\right|x(t) - x\_{a}(t) \\middle| {}\_{2}dt; \\right. \\\\ \\end{array}$$  
    (2.7)
    
*   the normalized integral quadratic functional
    
      
    $$\\begin{array}{r} {\\Delta\_{2} = \\frac{\\left. \\left. \\int\\limits\_{\\mathcal{T}} \\right|x(t) - x\_{a}(t) \\middle| {}\_{2}dt \\right.}{{\\int\\limits\_{\\mathcal{T}}x^{2}}(t)dt + {\\int\\limits\_{\\mathcal{T}}x\_{a}^{2}}(t)dt}.} \\\\ \\end{array}$$  
    (2.8)
    

The elementary approximating functions that have a direct relation to discrete data are the piecewise constant (also called step) functions

  
$$\\begin{array}{r} {x\_{c}(t) = \\left\\{ \\begin{aligned} {x(t\_{0})} & {\\text{for}\\, t\_{0} \\leq t < t\_{0} + h,} \\\\ {x(t\_{0} + h)} & {\\text{for}\\, t\_{0} + h \\leq t < t\_{0} + 2h,} \\\\ \\cdots & \\cdots \\\\ {x(t\_{0} + (n - 1)h)} & {\\text{for}\\, t\_{0} + (n - 1)h \\leq t < T.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(2.9)

As their parameter the step functions incorporate the sampling time *h*, which can be chosen depending on an acceptable value of the functionals (2.6)–(2.8). For certain classes of functions (e.g., continuous or smooth), the step functions possess a fruitful property of asymptotic behavior,

  
$$\\begin{array}{r} {\\lim\\limits\_{h\\rightarrow 0}x\_{c}(t) = x(t).} \\\\ \\end{array}$$  
(2.10)

Note that this limit is interpreted depending on the properties of a corresponding function *x*(*t*).

### 2.1.2Random functions

An analog source may generate functions of random origin. Following \[[65](#refbib.xhtml#r65)\], two close concepts will be employed, namely, *a random function *x*(*t*) ( a random vector function $\\overset{\\rightarrow}{x}(t))$* and *a random process *X*(*t*) ( a vector random process $\\overset{\\rightarrow}{X}(t))$*. A process represents an ensemble of random functions *x*(*t*). Under certain conditions, a random process (r.p.) observable in some sense is called *a sample* (a sample function) or *a realization* of this random function. The scalar functions will be considered below.

For a fixed *t*, *x*(*t*) gives a value of a random variable whereas *X*(*t*) an ensemble of values of this random variable. A random function is completely defined by all possible probability-theoretical relations for any finite set of values of random variables:

  
$$\\begin{array}{r} {x(t\_{1}),x(t\_{2}),\\ldots,x(t\_{n}),\\quad t\_{i} \\in \\mathcal{T},\\, i = \\overline{1,n},\\, n = 1,2,\\ldots,} \\\\ \\end{array}$$  
(2.11)

i.e., by corresponding probability distributions. In other words, a random function *x*(*t*), *t* ∈ 𝒯, is described by a corresponding family of distributions

  
$$\\begin{array}{r} {P\_{t\_{1},\\ldots,t\_{n}}(\\eta\_{1},\\ldots,\\eta\_{n}),\\text{\\quad\\quad}t\_{i} \\in \\mathcal{T},\\, i = \\overline{1,n},\\, n = 1,2,\\ldots,} \\\\ \\end{array}$$  
(2.12)

where *η*[1], …, *η*[*n*] denote the values of the random variables.

Each probability distribution function is treated as a joint probability distribution function for a collection of the random variables (2.11). Such a treatment becomes justified under some necessary conditions, the so-called *consistency conditions* for the family of distributions (2.12) given by

  
$$\\begin{aligned} {P\_{t\_{1},\\ldots,t\_{n},t\_{(n + 1)},\\ldots,t\_{(n + p)}}(\\eta\_{1},\\ldots,\\eta\_{n},} & {+ \\infty,\\ldots, + \\infty) = P\_{t\_{1},\\ldots,t\_{n}}(\\eta\_{1},\\ldots,\\eta\_{n});} \\\\ {P\_{t\_{1},\\ldots,t\_{n}}(\\eta\_{1},\\ldots,\\eta\_{n})} & {= P\_{t\_{i\_{1}},\\ldots,t\_{i\_{n}}}(\\eta\_{i\_{1}},\\ldots,\\eta\_{i\_{n}}),} \\\\ \\end{aligned}$$  
(2.13)

where *i*[1], …, *i*[*n*] forms any permutation of the indexes 1, 2, …, *n*.

A set of functions *P*[*t*[1], …, *t*[*n*]](*η*[1], …, *η*[*n*]) is called *finite-dimensional distributions of a random function *x*(*t*)*.

Applications often lead to several random functions, which will be considered below as the elements of a random vector $\\overset{\\rightarrow}{x}(t) = \\left\\{ x\_{1}(t),\\ldots,x\_{m}(t) \\right\\}.$ A random vector is completely defined by a family of finite-dimensional probability distributions of the form

  
$$\\begin{aligned} {P\_{t\_{1},\\ldots,t\_{n}}(\\eta\_{11},} & {\\eta\_{12},\\ldots,\\eta\_{nm}) = \\mathbf{P}\\left\\{ x\_{1}(t\_{1}) < \\eta\_{11},x\_{2}(t\_{1}) < \\right.} \\\\ & {\\left. < \\eta\_{12},\\ldots,x\_{m}(t\_{n}) < \\eta\_{nm} \\right\\}.} \\\\ \\end{aligned}$$  
(2.14)

The finite-dimensional probability distributions of a random function *x*(*t*) can be defined by the finite-dimensional probability density functions *w*[*t*[1], …, *t*[*n*]](*η*[1], …, *η*[*n*]):

  
$$\\begin{array}{r} {P\_{t\_{1},\\ldots,t\_{n}}(\\eta\_{1},\\ldots,\\eta\_{n}) = {\\int\\limits\_{- \\infty}^{\\eta\_{1}}\\cdots}{\\int\\limits\_{- \\infty}^{\\eta\_{n}}\\,}w\_{t\_{1},\\ldots,t\_{n}}(y\_{1},\\ldots,y\_{n})dy\_{1}\\cdots dy\_{n}.} \\\\ \\end{array}$$  
(2.15)

In particular, this implies the formula

  
$$\\begin{aligned} {w\_{t\_{1},\\ldots,t\_{n}}(\\eta\_{1},\\ldots,\\eta\_{n})} & {= {\\int\\limits\_{- \\infty}^{\\infty}\\cdots}{\\int\\limits\_{- \\infty}^{\\infty}w\_{t\_{1},\\ldots,t\_{n},t\_{(n + 1)},\\ldots,t\_{(n + p)}}}(\\eta\_{1},\\ldots,} \\\\ & {\\eta\_{n},y\_{1},\\ldots,y\_{p})dy\_{1}\\cdots dy\_{p},} \\\\ \\end{aligned}$$  
(2.16)

which can be viewed as the consistency condition (2.1.2) of the finite-dimensional probability distributions.

A useful tool to analyze finite-dimensional probability density functions (or distributions) is their *characteristic function *Φ*[*t*[1], …, *t*[*n*]](*u*[1], …, *u*[*n*])*, which represents the Fourier transform \[[48](#refbib.xhtml#r48)\] of a probability density function:

  
$$\\begin{aligned} {\\Phi\_{t\_{1},\\ldots,t\_{n}}(u\_{1},\\ldots,u\_{n})} & {= {\\int\\limits\_{- \\infty}^{\\infty}\\cdots}{\\int\\limits\_{- \\infty}^{\\infty}\\exp}\\left( {j{\\sum\\limits\_{k = 1}^{n}\\eta\_{k}}\\, u\_{k}} \\right) \\times} \\\\ {\\times w\_{t\_{1},\\ldots,t\_{n}}} & {(\\eta\_{1},\\ldots,\\eta\_{n})\\, d\\eta\_{1}\\cdots d\\eta\_{n},} \\\\ & {j = \\sqrt{- 1}.} \\\\ \\end{aligned}$$  
(2.17)

The variables *u*[1], …, *u*[*n*] takes values in space *R*^(*n*). If a probability density function satisfies some analytical conditions (see \[48\]), then it can be restored through its characteristic function using the Fourier integral as follows:

  
$$\\begin{aligned} {w\_{t\_{1},\\ldots,t\_{n}}(\\eta\_{1},\\ldots,\\eta\_{n})} & {= \\frac{1}{{(2\\pi)}^{n}}{\\int\\limits\_{- \\infty}^{\\infty}\\cdots}{\\int\\limits\_{- \\infty}^{\\infty}\\exp}\\left( {- {\\sum\\limits\_{k = 1}^{n}\\eta\_{k}}\\, u\_{k}} \\right) \\times} \\\\ & {\\times \\Phi\_{t\_{1},\\ldots,t\_{n}}(u\_{1},\\ldots,u\_{n})\\, du\_{1}\\cdots du\_{n}.} \\\\ \\end{aligned}$$  
(2.18)

These definitions of a random function suffice if we are interested in the values of a random function at *n* points, i.e., the values of argument (*t*[1], …, *t*[*n*]) ∈ 𝒯. However, if the set 𝒯 contains all real values of time *t*, then even arbitrarily many finite-dimensional probability distributions of the form (2.12, 2.1.2) say nothing about the constructive properties of random functions such as continuity, differentiability, and others.

In some applications, the complete description of a random function in the form of finite-dimensional probability distributions becomes redundant. One needs only know its numerical characteristics—the moment functions

  
$$\\begin{array}{r} {m\_{i\_{1},\\ldots,i\_{s}}(t\_{1},\\ldots,t\_{s}) = \\mathcal{M}{\\prod\\limits\_{k = 1}^{s}\\left\\lbrack {x(t\_{k})} \\right\\rbrack^{i\_{k}}},\\quad i\_{k} \\geq 0,\\,\\, k = \\overline{1,s}.} \\\\ \\end{array}$$  
(2.19)

The value $q = {\\sum\\limits\_{k = 1}^{s}i\_{k}}$ is called the order of the moment function. In the class of moment functions, a special place belongs to the moment functions of orders 1 and 2, namely,

*   the mean
    
      
    $$\\begin{array}{r} {m(t\_{1}) = m\_{1}(t\_{1}) = \\mathcal{M}\\left\\{ x(t\_{1}) \\right\\};} \\\\ \\end{array}$$  
    (2.20)
    
*   the correlation function
    
      
    $$\\begin{array}{r} {R(t\_{1},t\_{2}) = m\_{11}(t\_{1},t\_{2}) = \\mathcal{M}\\left\\{ \\lbrack x(t\_{1}) - m(t\_{1})\\rbrack\\lbrack x(t\_{2}) - m(t\_{2})\\rbrack \\right\\}.} \\\\ \\end{array}$$  
    (2.21)
    

If *t*[1] = *t*[2] = *t*, then *R*(*t*, *t*) = *σ*² are the variances of a random variable *x*(*t*) with a fixed *t*. If *R*(*t*[1], *t*[2]) = 0, then the values *x*(*t*[1]) and *x*(*t*[2]) of a random function *x*(*t*) are uncorrelated. In a special case where the two-dimensional joint probability distribution of random variables *x*(*t*[1]) and *x*(*t*[2]) is Gaussian and the uncorrelatedness condition holds, the random variables *x*(*t*[1]) and *x*(*t*[2]) are independent.

Continuity is an important property of a function. For a random function, this property has the probabilistic sense formalized in terms of the distribution of all pairs *x*(*t*[1]), *x*(*t*[2]). Introduce the distance *ρ*(*t*[1],*t*[1])=|*t*[1]−*t*[2]| on the set 𝒯. A random function *x*(*t*), *t* ∈ 𝒯, is called *stochastically continuous* at a point *t*^(\*) if, for all *ε* > 0,

  
$$\\begin{array}{r} \\left. \\mathbf{P}\\left\\{ \\middle| x(t^{\*}) - x(t) \\middle| > \\varepsilon \\right\\}\\rightarrow 0\\quad\\text{as}\\,\\,\\rho(t^{\*},t)\\rightarrow 0. \\right. \\\\ \\end{array}$$  
(2.22)

If condition (2.22) holds for all values *t* ∈ 𝒯, then a corresponding function *x*(*t*) is stochastically continuous on 𝒯.

According to the definition (2.22), stochastic continuity is an “asymptotic” property to be declared only. A more constructive definition would operate some quantitative values. In fact, *uniform stochastic continuity* forms such a property. A random function is uniformly stochastically continuous on 𝒯 if, for an arbitrary *ε* > 0, there exists a *δ* > 0 such that

  
$$\\begin{array}{r} {\\mathbf{P}\\left\\{ \\middle| x(t) - x(\\widetilde{t}) \\middle| > \\varepsilon \\right\\} < \\varepsilon} \\\\ \\end{array}$$  
(2.23)

for all the pairs (*t*, *t̃*) satisfying the inequality *ρ*(*t*, *t̃*) < *ε*.

Since the set 𝒯 is compact, the stochastic continuity of a random function on 𝒯 implies its uniform stochastic continuity on 𝒯.

Consider some classes of random functions (processes).

**1. Gaussian random functions**

In many applications, a crucial role is played by the random functions with Gaussian finite-dimensional probability distributions. As the matter concerns the finite-dimensional distributions, a random function can be described by a random *n*\-dimensional vector $\\overset{\\rightarrow}{x} = \\left\\{ x(t\_{1}),\\ldots,x(t\_{n}) \\right\\}.$ A random vector $\\overset{\\rightarrow}{x}$ obeys the Gaussian distribution if its characteristic function can be represented in the form

  
$$\\begin{array}{r} {\\Phi(\\overset{\\rightarrow}{u}) = \\mathcal{M}\\left\\{ \\exp\\left( {j\\left\\langle \\overset{\\rightarrow}{u},\\overset{\\rightarrow}{x} \\right\\rangle} \\right) \\right\\} = \\exp\\left( {j\\left\\langle \\overset{\\rightarrow}{u},\\overset{\\rightarrow}{m} \\right\\rangle - \\frac{1}{2}\\left\\langle G\\,\\overset{\\rightarrow}{u},\\overset{\\rightarrow}{u} \\right\\rangle} \\right).} \\\\ \\end{array}$$  
(2.24)

Here $\\overset{\\rightarrow}{m}$ denotes the *n*\-dimensional vector of the means for the corresponding elements of a vector $\\overset{\\rightarrow}{x};$ $\\overset{\\rightarrow}{u}$ is the *n*\-dimensional vector of real variables defined on *R*^(*n*); *G* indicates a nonnegative definite real symmetric matrix (the correlation matrix); finally, ⟨•,•⟩ stands for the scalar product of appropriate vectors.

The moments of a Gaussian random function can be calculated by expanding its characteristic function. If the central moments (*m*[1](*t*[1]) = 0) suffice, then

  
$$\\begin{aligned} {\\Phi(\\overset{\\rightarrow}{u})} & {= \\exp\\left( {- \\frac{1}{2}\\left\\langle G\\,\\overset{\\rightarrow}{u},\\overset{\\rightarrow}{u} \\right\\rangle} \\right) = 1 - \\frac{1}{2}\\left\\langle G\\,\\overset{\\rightarrow}{u},\\overset{\\rightarrow}{u} \\right\\rangle + \\frac{1}{2^{2}2!}\\left\\langle G\\,\\overset{\\rightarrow}{u},\\overset{\\rightarrow}{u} \\right\\rangle^{2} - \\ldots} \\\\ & {+ {( - 1)}^{n}\\frac{1}{2^{n}n!}\\left\\langle G\\,\\overset{\\rightarrow}{u},\\overset{\\rightarrow}{u} \\right\\rangle^{n} + \\ldots.} \\\\ \\end{aligned}$$  
(2.25)

Hence, the odd-order moment functions are

  
$$\\begin{array}{r} {m\_{i\_{1},\\ldots,i\_{s}}(t\_{1},\\ldots,t\_{s}) = 0,\\text{\\quad\\quad}{\\sum\\limits\_{k = 1}^{s}i\_{k}} = 2n + 1;} \\\\ \\end{array}$$  
(2.26)

the even-order moment functions take the form

  
$$\\begin{aligned} {m\_{i\_{1},\\ldots,i\_{s}}(t\_{1},\\ldots,t\_{s})} & {= \\frac{\\partial^{2n}}{\\partial t\_{1}^{i\_{1}}\\cdots\\partial\_{s}^{i\_{s}}}\\left( {\\frac{1}{2^{n}n!}\\left\\langle G\\,\\overset{\\rightarrow}{u},\\overset{\\rightarrow}{u} \\right\\rangle} \\right),} \\\\ {\\sum\\limits\_{k = 1}^{s}i\_{k}} & {= 2n.} \\\\ \\end{aligned}$$  
(2.27)

The Gaussian random functions are of paramount importance in different (theoretical and applications-oriented) studies. Really, under rather nonrestricting conditions, the sum of a large number of independent random functions with small values can be approximated by a Gaussian random function, regardless of the probability-theoretic nature of the terms. This significant result—the normal correlation theorem—is a generalization of the central limit theorem \[[166](#refbib.xhtml#r166)\].

**2. Random processes with independent increments**

The research in the field of random processes with independent increments started with Brownian motion and the Wiener process as its appropriate mathematical model. At a later time, the generalized mathematical models with integration in the class of processes with independent increments were developed.

A random process $\\overset{\\rightarrow}{x}(t),\\, t \\in \\mathcal{T},$ taking values in *R*^(*n*) is called a process with independent increments if, for any *n*, *t*[0] ≤ *t*[1] ≤ ⋯ ≤ *t*[*n*] = *T*, the random vectors $\\overset{\\rightarrow}{x}(t\_{0}),\\overset{\\rightarrow}{x}(t\_{1}) - \\overset{\\rightarrow}{x}(t\_{0}),\\ldots,\\overset{\\rightarrow}{x}(t\_{n}) - \\overset{\\rightarrow}{x}(t\_{n - 1})$ are mutually independent.

The vector $\\overset{\\rightarrow}{x}(t\_{0})$ is called the initial state (value) of the process, and its probability distribution is called the initial distribution of the process. For defining a process with independent increments, it suffices to define an initial distribution $P\_{0}(\\mathcal{B}) = \\mathbf{P}\\left\\{ \\overset{\\rightarrow}{x}(t\_{0}) \\in \\mathcal{B} \\right\\},$ a collection of distributions $P(t,h,\\mathcal{B}) = \\mathbf{P}\\left\\{ \\Delta\\overset{\\rightarrow}{x}(t,h) \\in \\mathcal{B} \\right\\}$ for the vector $\\Delta\\overset{\\rightarrow}{x}(t,h) = \\overset{\\rightarrow}{x}(t + h) - \\overset{\\rightarrow}{x}(t),$ where *t* ∈ 𝒯, *h* > 0, and ℬ ∈ *R*^(*m*) is a set of elementary events.

If a distribution *P*(*t*, *h*, ℬ) does not depend on *t*, i.e., *P*(*t*, *h*, ℬ) = *P*(*h*, ℬ), then a corresponding process with independent increments is called *homogeneous*.

Consider examples of some processes with independent increments. Let us begin with **Brownian motion**. For this process, the probability distribution *P*(*t*, *h*, ℬ) is Gaussian. The physical model of the process is the motion of a small particle in a liquid, which can be observed using a high-power microscope. Such a particle has constant movements, and its path represents a very complicated polygonal line with chaotically directed segments. This motion is explained by the collisions of the particle with the molecules of the liquid. The particle has relatively large dimensions in comparison with the dimensions of each molecule and suffers from a huge number of collisions with them each second. The visible motion of the particle is called Brownian motion. In a rough approximation, the displacements of the particle caused by collisions can be considered mutually independent, and hence Brownian motion can be treated as a process with independent increments. Due to small displacements, we can hypothesize that their sum satisfies the central limit theorem; in other words, Brownian motion can be described by a Gaussian random process with independent increments.

In particular, a homogeneous Brownian random process is defined by two parameters *m* and *σ*:

  
$$\\begin{array}{r} {\\mathcal{M}\\left\\{ x(t) \\right\\} = mt,\\quad\\mathcal{M}\\left\\{ x^{2}(t) \\right\\} = \\sigma^{2}t.} \\\\ \\end{array}$$  
(2.28)

For *m* = 0 and *σ* = 1, the Brownian motion process is called *the standard Wiener process*.

Now consider *Poisson processes*. A stochastically continuous process with independent increments that takes nonnegative integer values is called a Poisson process if, for any (*s*, *t*) > 0 and *s* < *t*, the variable $\\overset{\\rightarrow}{x}(t) - \\overset{\\rightarrow}{x}(s)$ obeys the Poisson probability distribution.

Let *x*(*t*[0]) = 0. Then the variable *x*(*t*) has the probability distribution

  
$$\\begin{array}{r} {\\mathbf{P}\\left\\{ x(t) = m \\right\\} = \\frac{a^{m}(t)}{m!}\\exp( - a(t)),\\quad\\mathcal{M}\\left\\{ x(t) \\right\\} = a(t).} \\\\ \\end{array}$$  
(2.29)

Hence, it follows that

  
$$\\begin{aligned} {\\mathbf{P}\\left\\{ x(t) - x(s) = m \\right\\}} & {= \\frac{{\\lbrack a(t) - a(s)\\rbrack}^{m}}{m!}\\exp\\left( {- \\lbrack a(t) - a(s)\\rbrack} \\right),} \\\\ & {\\quad m = 0,1,2,\\ldots} \\\\ \\end{aligned}$$  
(2.30)

If the process is homogeneous, then

  
$$\\begin{aligned} & {a(t) = at,} \\\\ {\\mathbf{P}\\left\\{ x(t) - x(s) = m \\right\\}} & {= \\frac{a^{m}{(t - s)}^{m}}{m!}\\exp( - a(t - s)),} \\\\ {s < t,} & {m = 0,1,2,\\ldots} \\\\ \\end{aligned}$$  
(2.31)

**3. Markov processes**

The concept of a Markov process is based on the hypothesis about nonhereditary systems (also known as systems “without aftereffect”). At each time *t*, such a system has some state $\\overset{\\rightarrow}{x}(t),$ which depends on its state $\\overset{\\rightarrow}{x}(s)$ at a preceding time *s* < *t* only. All admissible states form a certain set *B* ∈ *X*, where *X* is the phase space of the system. Assume that the system evolves stochastically, i.e., its state at a time *t* is not uniquely defined by the state at a preceding time *s*, thereby being random. Denote by $P(s,\\overset{\\rightarrow}{x},t,B)$ the probability of the event $\\left\\{ \\overset{\\rightarrow}{x}(t) \\in B(s < t) \\right\\}$ under the condition $\\overset{\\rightarrow}{x}(s) = \\overset{\\rightarrow}{x},$ which is often called *the transition probability* or the conditional probability of the system state's belonging to a set *B* at a time *t* given its state $\\overset{\\rightarrow}{x}$ at a time *s* in the phase space *X*.

Suppose that there exists an intermediate state $\\overset{\\rightarrow}{x}(u)$ between the states $\\overset{\\rightarrow}{x}(s)$ and $\\overset{\\rightarrow}{x}(t),$ where *s* < *u* < *t*. Denote by $P(s,\\overset{\\rightarrow}{x},u,\\overset{\\rightarrow}{y},t,B)$ the conditional probability of the event $\\left\\{ \\overset{\\rightarrow}{x}(t) \\in B \\right\\}$ given $\\overset{\\rightarrow}{x}(s) = \\overset{\\rightarrow}{x}$ and $\\overset{\\rightarrow}{x}(u) = \\overset{\\rightarrow}{y}.$ Using the general properties of conditional probabilities, write

  
$$\\begin{array}{r} {P(s,\\overset{\\rightarrow}{x},t,B) = {\\int\_{X}P}(s,\\overset{\\rightarrow}{x},u,\\overset{\\rightarrow}{y},t,B)\\, P(s,\\overset{\\rightarrow}{x},u,\\overset{\\rightarrow}{y})\\, d\\overset{\\rightarrow}{y}.} \\\\ \\end{array}$$  
(2.32)

For a nonhereditary system, a natural assumption is

  
$$\\begin{array}{r} {P(s,\\overset{\\rightarrow}{x},u,\\overset{\\rightarrow}{y},t,B) = P(u,\\overset{\\rightarrow}{y},t,B).} \\\\ \\end{array}$$  
(2.33)

In this case, equality (2.34) takes the form

  
$$\\begin{array}{r} {P(s,\\overset{\\rightarrow}{x},t,B) = {\\int\_{X}P}(u,\\overset{\\rightarrow}{y},t,B)\\, P(s,\\overset{\\rightarrow}{x},u)\\, d\\overset{\\rightarrow}{y}.} \\\\ \\end{array}$$  
(2.34)

This is *the Chapman–Kolmogorov equation*, which underlies the theory of Markov processes \[[47](#refbib.xhtml#r47), 65, 166\].

A Markov process is called *homogeneous* if the transition probabilities depend on the difference of the arguments *t* and *s* only, i.e.,

  
$$\\begin{array}{r} {P(s,\\overset{\\rightarrow}{x},t,B) = P(t - s,\\overset{\\rightarrow}{x},B) = P\_{t - s}(\\overset{\\rightarrow}{x},B).} \\\\ \\end{array}$$  
(2.35)

For the homogeneous Markov processes, the Chapman–Kolmogorov equation (2.34) can be written in the simpler form

  
$$\\begin{array}{r} {P\_{u + v}(\\overset{\\rightarrow}{x},B) = {\\int\_{X}P\_{u}}(\\overset{\\rightarrow}{x})P\_{v}(\\overset{\\rightarrow}{y},B)\\, d\\overset{\\rightarrow}{y}.} \\\\ \\end{array}$$  
(2.36)

The definitions given in this section are wide, thereby embracing the Markov processes that differ in their sources and properties. In the sequel, we will discuss some classification principles and certain classes of Markov processes. The first attribute for classification consists in the phase space of the system in which a Markov process is observed. From this viewpoint the elementary Markov processes are the ones with finite or denumerable sets of admissible states. In the latter case, by imposing some analytical constraints on transition probabilities, we can linearize the Chapman–Kolmogorov equations and obtain their linearized counterparts. For general phase spaces, it is possible to define the classes of Markov processes in a wide sense, enduing transitional probabilities with more adequate properties in terms of real system behavior. This viewpoint allows introducing the following classes of Markov processes:

1.  *Jump processes.* They correspond to the idea of the processes that move to a certain point of a phase space, staying at this point during a random period of time, and then jump to another point of the space, and so on.
    
2.  *Processes with discrete interference of events.* These processes are generated by a dynamic system whose trajectories suffer from simple discontinuities with random jumps at random times.
    
3.  *Diffusion processes.* They represent the processes in finite-dimensional dynamic systems that have Brownian motion on small periods of time.
    
4.  *Markov processes with independent increments.* The sources of such processes are the finite-dimensional dynamic systems that behave as the processes with independent increments on small periods of time.
    

For the above-mentioned classes of Markov processes, it is also possible to perform linearization of the Chapman–Kolmogorov equation, transforming it to a linear partial differential equation or an integro-differential equation.

## 2.2Digital Source of Data

As a matter of fact, digital data are represented by arrays of decimal or binary numbers. They are generated using digital measuring devices. However, we often deal with an analog measuring device. Then these arrays are the result of a digital transformation of initial analog information about a studied object or phenomenon. In other words, an analog-to-digital converter (ADC) is placed after the studied object or phenomenon, as illustrated in [Fig. 2.1](#chapter2.xhtml#f2_1). For example, if the studied object operates on a given time interval 𝒯, thereby generating a certain continuous process, an ADC transforms this process into digital arrays. An ADC performs the amplitude and time quantization of an initial continuous process. A photograph is another example in which a visual image acts as an analog source. However, a photograph is transformed into a digital array using a slightly different ADC with scanning.

![Figure 2.1](images/fig2_1.jpg)

[Figure 2.1](#chapter2.xhtml#f2_1b)

### 2.2.1Amplitude and time quantization

Amplitude quantization decomposes a certain set of values of a function into a finite number of subsets. If the function under consideration is scalar, then the matter concerns quantization intervals. For a vector function, the concept of quantization has a close relation to the decomposition of the set of values of its components into elementary volumes. The simplest type of quantization is the division of a range *Δ**ϕ* = *ϕ*[*m**a**x*] − *ϕ*[*m**i**n*] of an analog function by an integer number, with rounding up or down to the nearest integer number. As a rule, quantization runs in binary code. The range *Δ**ϕ* is divided by 2^(*n*), where *n* denotes the register length (or the digit count). Each amplitude is coded by a sequence of zeros and ones of length *n*.

Time quantization, further termed time sampling (in our case, the argument of a function is time), is performed using a pulse generator. Note that sampling rate must be at least twice as large as the maximum frequency of the function spectrum.

Consequently, values of an analog function (information, signal) are represented by a sequence of binary numbers that corresponds to the values of this function at discrete times.

Amplitude quantization is a nonlinear transformation for the values of an analog function \[[197](#refbib.xhtml#r197)\]. [Figure 2.2](#chapter2.xhtml#f2_2) shows the characteristic of a nonlinear element that performs the amplitude quantization of an analog function. Amplitude quantization can be uniform and nonuniform. In the former case, the quantization step *h*[*k*] = *y*[*k* + 1] − *y*[*k*] is a constant *h*. Under nonuniform amplitude quantization, this step depends on the amplitude. Nonuniform amplitude quantization reduces the relative error of digital data generation. [Figures 2.3(a)](#chapter2.xhtml#f2_3)–[2.3(c)](#chapter2.xhtml#f2_3) demonstrate the characteristics of quantizers with different rounding rules: *a*—rounding up to the nearest integer number, *b*—rounding down to the nearest integer and *c*—rounding to the middle of the elementary interval.

![Figure 2.2](images/fig2_2.jpg)

[Figure 2.2](#chapter2.xhtml#f2_2b)

![Figure 2.3](images/fig2_3.jpg)

[Figure 2.3](#chapter2.xhtml#f2_3b)

Time sampling causes no measurement errors whereas amplitude quantization is accompanied by an error *ε* due to rounding. For estimating this error, a certain model has to be chosen. Consider two models, namely, deterministic and stochastic ones. Within the framework of the first model, the above-mentioned rounding rules lead to the maximum error

  
$$\\begin{array}{r} {\\varepsilon\_{max} = h.} \\\\ \\end{array}$$  
(2.37)

In other words, it coincides with the quantization step *h*. Assuming the quantization error to be a random variable, we have to declare its probability density function (PDF). For example, let this variable obey the uniform distribution on the interval $\\lbrack - \\frac{h}{2},\\frac{h}{2}\\rbrack,$ i.e.,

  
$$\\begin{array}{r} {p(\\varepsilon) = \\left\\{ \\begin{aligned} \\frac{1}{h} & {\\text{for}\\,\\left| \\varepsilon \\middle| \\leq \\frac{h}{2}, \\right.} \\\\ 0 & {\\text{for}\\,\\left| \\varepsilon \\middle| > \\frac{h}{2}. \\right.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(2.38)

Since the PDF has symmetry, the mean of the quantization error is zero whereas its variance is given by

  
$$\\begin{array}{r} {\\sigma^{2} = \\frac{1}{h}{\\int\\limits\_{- h/2}^{h/2}\\varepsilon^{2}}d\\varepsilon = \\frac{h^{2}}{12}.} \\\\ \\end{array}$$  
(2.39)

Interestingly, the derived estimate is considerably smaller than the one of the deterministic model (2.37). However, recall that this estimate of the quantization error proceeds from the hypotheses of uniform distribution and uncorrelatedness with the analog function.

### 2.2.2Audio data

The digital conversion of sound signals is performed by an ADC, which transforms an analog signal into digital audio data. These transformations use different types of digital modulation. Pulse code modulation (PCM) and delta modulation (DM) are most widespread.

PCM transforms a sequence of the instantaneous amplitudes of an analog signal *x*(*t*) ([Fig. 2.4(a)](#chapter2.xhtml#f2_4)) into the quantized values with a fixed step *h* that correspond to discrete times *n**Δ* ([Fig. 2.4(b)](#chapter2.xhtml#f2_4)). Each value *x*[PC]\[*n**Δ*\] is transformed into a binary code, as illustrated in [Fig. 2.4(c)](#chapter2.xhtml#f2_4). Such a modulator outputs packets of 0's and 1's with time binding.

![Figure 2.4](images/fig2_4.jpg)

[Figure 2.4](#chapter2.xhtml#f2_4b)

The accuracy of PCM depends on the step *h* and the number *N* of quantization amplitudes. The largest quantized value is (*N* − 1)*h*. The number of binary code combinations makes up *n* = \[log[2](*N* − 1)*h*\], where \[ ⋅ \] denotes the integer part operator.

DM is a special type of PCM that also represents an analog signal in the form of discrete samples of time with amplitude quantization. By assumption, there exists a relation between the samples in an audio signal. Therefore, it is possible to use only one digit for quantization of neighbor samples. [Figures 2.5(a)](#chapter2.xhtml#f2_5)–[2.5(b)](#chapter2.xhtml#f2_5) illustrate operation of a delta modulator. As its output this modulator (see [Fig. 2.5(a)](#chapter2.xhtml#f2_5)) generates a binary sequence of pulses,  + 1 for positive difference and  − 1 for negative difference.

![Figure 2.5](images/fig2_5.jpg)

[Figure 2.5](#chapter2.xhtml#f2_5b)

The digital representation of sound signals is used in two ways as follows. First, for improving the quality of sound and further conversion back to the analog form. Second, for forming quantitatively measured attributes that characterize sound signals \[[124](#refbib.xhtml#r124)\]. In this context, above all attributes, note the spectral composition of a signal and its basic parameters.

Consider again an analog signal described by a continuous function *x*(*t*). Let this function be defined and square integrable on the infinite interval ( − ∞,  + ∞). Then the Fourier transform of the function is given by

  
$$\\begin{aligned} {\\Phi\_{1}(\\nu)} & {= {\\int\\limits\_{- \\infty}^{+ \\infty}x}(t)\\exp( - 2\\pi\\iota\\nu t)dt = \\Phi(2\\pi\\nu),} \\\\ {\\Phi\_{2}(\\omega)} & {= \\frac{1}{\\sqrt{2\\pi}}{\\int\\limits\_{- \\infty}^{+ \\infty}x}(t)\\exp( - \\iota\\omega t)dt = \\sqrt{2\\pi}\\Phi(\\omega),} \\\\ {\\Phi(\\omega)} & {= {\\int\\limits\_{- \\infty}^{+ \\infty}x}(t)\\exp( - \\iota\\omega t)dt.} \\\\ \\end{aligned}$$  
(2.40)

Here $\\iota = \\sqrt{- 1}$, *ν* denotes linear frequency (in Hz), and *ω* = 2*π**ν* is angular frequency (in rad/s). Formulas (2.40) incorporate the complex exponents

  
$$\\begin{array}{r} {\\exp( - \\iota\\omega t) = \\cos(\\omega t) - \\iota\\sin(\\omega t).} \\\\ \\end{array}$$  
(2.41)

The function *Φ*(*ω*) is continuous for *ω* ∈ ( − ∞,  + ∞).

A real analog signal is defined on a finite time interval 𝒯 = \[0, *T*\]. A digital transformation of this signal yields a sequence of quantized values called samples of the form

  
$$\\begin{array}{r} {x\\lbrack n\\Delta\\rbrack = {\\int\\limits\_{- \\infty}^{+ \\infty}x}(\\tau)\\,\\delta(n\\Delta - \\tau)d\\tau,} \\\\ \\end{array}$$  
(2.42)

where *δ*( • ) denotes the delta-function, $\\Delta = \\frac{T}{N - 1},$ and *N* is the number of samples. Therefore, the digital representation of an analog signal on a finite time interval 𝒯 is described by an *N*\-dimensional vector **x** with the elements *x*\[*n**Δ*\] (2.42). According to (2.40), the Fourier transform of this signal is given by

  
$$\\begin{aligned} {\\Psi(\\omega) = \\Psi\\left( {\\frac{2\\pi}{T}k} \\right)} & {= \\Psi(k) = {\\sum\\limits\_{n = 0}^{N - 1}x}\\lbrack n\\Delta\\rbrack\\,\\exp\\left( {- \\iota\\frac{2\\pi}{T}k\\, n} \\right) =} \\\\ {= {\\sum\\limits\_{n = 0}^{N - 1}x}\\lbrack n\\Delta\\rbrack} & {\\left\\lbrack {\\cos\\left( {\\frac{2\\pi}{T}kn} \\right) - \\sin\\left( {\\frac{2\\pi}{T}kn} \\right)} \\right\\rbrack,} \\\\ & {\\quad k = \\overline{0,N-1},} \\\\ \\end{aligned}$$  
(2.43)

and called the discrete Fourier transform (DFT). Clearly, the DFT as the discrete spectrum of a digital signal is characterized by a vector $\\overline{\\Psi}$ with the elements *Ψ*(*k*) (2.2.2). Note that the dimension of this vector coincides with that of the vector **x** composed of the digital samples (2.42); see [Figs. 2.6(a)](#chapter2.xhtml#f2_6) and [2.6(b)](#chapter2.xhtml#f2_6).

![Figure 2.6](images/fig2_6.jpg)

[Figure 2.6](#chapter2.xhtml#f2_6b)

The vector $\\overline{\\Psi}$ determines the frequency distribution of the energy of the sound signal under consideration. As a rule, the interval Δ is sufficiently small to preserve the informational characteristics of the analog signal on the time interval 𝒯. Subsequently, the vector $\\overline{\\Psi}$ has a rather high dimension, which complicates the use of the discrete spectrum in applications. On the basis of this vector, it is necessary to obtain a reduced vector **z** with an essentially smaller dimension in comparison with the initial vector $\\overline{\\Psi}.$ A simple (albeit, not most objective and informative) solution is to assign a small number of intervals \[0, *k*[1]\], \[*k*[1] + 1, *k*[2]\], …, \[*k*[*s*] + 1, *N* − 1\] and to construct the so-called energy spectrum, i.e., a vector **z** with the elements

  
$$\\begin{array}{r} {z\_{j} = {\\sum\\limits\_{i = 0}^{k\_{1}}\\Psi}(i) + {\\sum\\limits\_{i = k\_{(j - 1)} + 1}^{k\_{j}}\\Psi}(i),\\text{\\quad\\quad}j = \\overline{2,m},\\quad m \\ll (N - 1).} \\\\ \\end{array}$$  
(2.44)

Then the total energy takes the form

  
$$\\begin{array}{r} {E = {\\sum\\limits\_{k = 0}^{N - 1}\\Psi}(k).} \\\\ \\end{array}$$  
(2.45)

### 2.2.3Graphical data

Graphical data are the result of digitizing 2D analog monochrome or color images. The examples of such images include paintings, manuscripts, photo and video images, etc. The images are transformed into graphical data in two ways, using bit image (raster) graphics and vector graphics.

*Bit image* graphical data represent a matrix of fixed-size *pixels*. The digitization of analog images is performed through spatial discretization. More specifically, an image is split into separate elements (pixels) and each pixel is associated with 2D coordinates and a grey gradation (for monochrome images) or a color palette (for color images). The coordinates and palettes have digital form. Spatial discretization expresses graphical data as a matrix of finite dimensions in which each row contains a definite number of pixels with an appropriate color in a digital scale. At the hardware level, the bit image conversion of an analog image is implemented by a scanner. An example of bit image graphical data is given in [Fig. 2.7(a)](#chapter2.xhtml#f2_7).

![Figure 2.7](images/fig2_7.jpg)

[Figure 2.7](#chapter2.xhtml#f2_7b)

*Vector* graphical data involve a mathematical description of the elementary graphical objects called *primitives*. Among such objects, note points, straight lines, some curves, splines, circles, polygons, etc. An example of vector graphics primitives is shown in [Fig. 2.7(b)](#chapter2.xhtml#f2_7). The major advantage of vector data over bit image data consists in a rather simple scalability without compromise to the original quality of an image.

In most cases, analog images are transformed into digital for further automatic processing using digital devices such as computers, smartphones, video and photo cameras, and so on. Consider the images of standard (fixed-form) documents, e.g., billing and banking documents, fiscal documents, voting ballots and questionnaires. These documents have a definite structure with fields to be filled. In other words, useful graphical data is contained only in corresponding boxes. Hence, there is no need to scan the entire document, just the requisite fields only. Therefore, the bit image representation of such a document has a fixed structure and a bit image representation of its fields.

Note that vector formats are often transformed into bit image ones. At the same time, the converse transformation is computationally intensive.

### 2.2.4Text data

Text is a peculiar object for digitization that essentially differs from the above-mentioned ones. Information about audio, video and graphical objects is completely reflected by physical measurements. In contrast, text is the result of integration of some rules and human perceptions of these rules. Subsequently, text has meaning as its distinctive attribute, unlike the objects of the other types. As a matter of fact, the notion of meaning is ambiguous, which causes its implicit description in terms of numerical characteristics.

Therefore, text data are numerical data yielded by some model of text \[[167](#refbib.xhtml#r167)\]. We will comprehend a model of text as a set of numerical indicators used for its characterization. Besides easily calculated indicators, there exist the so-called syntax trees (or diagrams) and semantic networks with construction procedures of giant computational complexity.

Text modeling involves different types of information about text, i.e., text-relevant information and external information. The following types of text-relevant information are widespread:

*   the frequency characteristics of text elements (in the elementary case, the presence or absence of words (terms) from a given list in a document);
    
*   the mutual position of words in a document. Words have a definite order in accordance with the syntax rules of a given language, thereby forming groups and sentences. The mutual position of words contain some useful information;
    
*   formatting of a document. As a rule, before publication a text is appropriately formatted. Separate words, sentences or even paragraphs can be set in different types (bold, italic, etc.) or aligned;
    
*   the logical structure of a document. A document often consists of chapters, sections, subsection and paragraphs. Such a logical structure of a document reflects the meaning of text;
    
*   references to other documents. Documents often refer to other documents (e.g., in the form of hypertext links or bibliographic citations).
    

External information includes information about the source, author, date of creation or modification of a document, subject classification, user's behavior with respect to a document (e.g., user's access rate, etc.).

The frequency characteristics of a document are most widely used, in the first place, the histogram of homogeneous attributes, e.g., the vector of entries of keywords \[[160](#refbib.xhtml#r160)\]. In this case, a common glossary of terms has to be managed for all documents analyzed. Each document is represented as a vector whose elements show the occurrence of corresponding terms in the document. This vector has a very large dimension that matches the total number of terms in the glossary.

In the general setting, an element of this vector represents an informational weight of a term in a document. Actually, the informational weight of a term is treated in a wider sense with additional attributes, e.g., the informational weight of a short sequence of letters (e.g., a combination of two letters), syllables, words, or normal-form word combinations \[[175](#refbib.xhtml#r175)\]. The weight of an element is often defined using some statistical characteristics of its occurrence in text, with certain coefficients that reflect the format and position of this element in a given document.

In the first stage of a numerical characterization of text, the extended term weight allows to separate out a set (bag) of most adequate words for a document. The bag-of-words model was suggested in 1975, still remaining a commonly used model of text \[[170](#refbib.xhtml#r170)\]. Within the framework of this model, text is represented as a set of words, regardless of their order. A certain weight is assigned for each word in this set. Therefore, the model of a document consists of a finite set of word-weight pairs. Note that weights can be assigned to words (terms) or stems. There exist the following standard methods to assign weights \[[93](#refbib.xhtml#r93)\]:

*   *the binary method (BI)*. This method defines only the presence or absence of certain terms in a document;
    
*   *the number of term entries in a document*. If a term appears many times in text, the document under consideration is likely to have a semantic relation to this term;
    
*   *the term frequency (TF)*. The term frequency is calculated as the number of term entries divided by the total number of words in a document;
    
*   *the logarithmical term frequency (LOGTF)*. This method defines the weight of a term as 1 + log (TF), where TF is the term frequency. Due to the logarithmical scale of informational weight assignment, the model has higher stability against overestimation of documents; *the inverse document frequency (IDF)*. This parameter is the inversion of the term frequency.
    

A conventional approach is to analyze texts using a collection of documents described by a term-weight matrix.

### 2.2.5Government statistical data

There exist many objects that are assessed by government statistics services using problem-oriented registers associated with definite time scales. In the first place, note the measurements and state assessments for the economic system (macroindices, labour resources, GDP, finances, etc.), the demographic system (fertility, mortality and migration rates), and the environmental system (atmosphere, earth, water, soil, and so on). A considerable part of statistical measurements are performed for different regions of a country.

A government statistics system implements the acquisition, analysis and structuring of all measured parameters, as well as their further transformation into data in accordance with an accepted register. Each of these stages, from the acquisition of information from existing sources to data structuring in tabular form, is accompanied by inevitable errors, also causing *errors* in government statistical data. There exist two types of errors, namely, *systematic errors* and *coverage errors*. The former occur due to imperfect methods for transforming initial information into data, whereas the latter due to the mismatch between the target object and the elements actually observed.

To elucidate this point, let us consider an example of data formation to calculate per capita national income. This problem seems trivial: just divide the annual GDP in monetary terms by the amount of able-bodied population. However, the annual GDP in monetary terms is calculated using generalized prices that are defined by certain models. The input variables and characteristics (parameters) of these models are measured and estimated with errors (often interpreted as random variables). Therefore, the annual GDP is the arithmetical mean by month with the estimated variance. A similar situation takes place for able-bodied population, as its size varies unpredictably in the course of a year. In other words, the calculated value of the annual GDP incorporates both types of errors.

Consider the following mathematical model of this situation. Denote by *x* an index of interest that is associated with a time *t*. Assume that this index depends on *n* factors, *y*[1], …, *y*[*n*]. Such an assumption leads to coverage errors: there is no evidence that the accepted set of factors (i.e., their number and meaning) is complete for defining the index *x*.

The next stage in formation of the index *x* is to model a parameterized relation between the factors and *x*, that is,

  
$$\\begin{array}{r} {x = F(\\mathbf{y},\\mathbf{a}),} \\\\ \\end{array}$$  
(2.46)

where **a** = {*a*[1],…,*a*[*p*]} act as parameters. The function *F* and its parameterization are chosen via expertise. Exactly this stage introduces systematic errors due to limited, incomplete and subjective knowledge of experts.

As a matter of fact, a government statistics system has a distributed structure and involves various primary processing methods for initial information. In combination with the human factor, these features almost rule out the possibility of adequate estimation for the government statistics errors. A remaining alternative is to use expert appraisals, which have a rather large spread from 5% to 20%.

The existing errors essentially affect (a) the estimated characteristics of relations between the input and output data and also (b) the solutions of other problems involving government statistical data.

## 2.3Restoration Methods for Missing Data

Digital sources generate sequences of data that are bound to time scales. A common situation in practice is the existence of different time scales or omissions for a certain time scale. However, for further usage of data sequences, one often needs to perform their synchronization (reduction to the same scale) or to restore missing data. As a matter of fact, data synchronization and restoration are close problems and their solution employs similar methods. Consider some of the methods in detail.

### 2.3.1Interpolation

A digital source of data generates a sequence of values of an analog function *x*(*t*) for a finite set of values of its argument. As a rule, these values are associated with a certain time scale with a step *h*. Take another function *y*(*t*) with a generated sequence of values in a different time scale with a step *s* < *h* such that {*h*/*s*} is an integer. Then we naturally arrive at the synchronization of these functions, i.e., it is necessary to restore the values of *x*(*t*) within the intervals \[*i**h*, (*i* + 1)*h*\] with the step *s* (the so-called data interpolation problem). The classical approach to solve this problem is to construct a rather simple function *z*(*t*) so that its values in the *h*\-scale coincide with the values of the function *x*(*t*) in the same scale, that is, *z*\[0\] = *x*\[0\], ⋯, *z*\[*i**h*\] = *x*\[*i**h*\].

Consider an arbitrary real function *x*(*t*) ∈ *R* defined on an interval 𝒯 = \[0, *T*\]. In space *R* choose a finite collection of elementary (simple) functions {*φ*[*k*](*t*)}[0]^(*n*) so that they are linearly independent. In most cases, this is a sequence of power functions 1, *t*, *t*², …; or trigonometric functions 1, sin *t*, cos *t*, sin 2*t*, cos 2*t*, …; or exponential functions 1, exp (*α*[1]*t*), exp (*α*[2]*t*), …, where {*α*[*i*]} denotes a number sequence.

Using the first *n* + 1 functions {*φ*[*k*](*t*)}[0]^(*n*), construct all possible linear combinations

  
$$\\begin{array}{r} {a\_{0}\\varphi\_{0}(t) + a\_{1}\\varphi\_{1}(t) + \\cdots + a\_{n}\\varphi\_{n}(t) = \\psi(t)} \\\\ \\end{array}$$  
(2.47)

with real coefficients *a*[0], …, *a*[*n*]. In interpolation theory, these coefficients are calculated in the following way. Choose *n* + 1 values of the variable *t*, i.e., *t*[0], …, *t*[*n*], which are called interpolation nodes. Let the function *x*(*t*) and its interpolating function *ψ*(*t*) have the same values at these nodes. This leads to the system of linear equations

  
$$\\begin{array}{r} {x(t\_{j}) = a\_{0}\\varphi\_{0}(t\_{j}) + a\_{1}\\varphi\_{1}(t\_{j}) + \\cdots + a\_{n}\\varphi\_{n}(t\_{j}),\\text{\\quad\\quad}j = \\overline{0,n}.} \\\\ \\end{array}$$  
(2.48)

The nodes should be chosen so that the determinant

  
$$\\begin{array}{r} {\\Delta = \\left| \\begin{array}{lll} {\\varphi\_{0}(t\_{0})} & \\cdots & {\\varphi\_{n}(t\_{0})} \\\\ \\cdots & \\cdots & \\cdots \\\\ {\\varphi\_{0}(t\_{n})} & \\cdots & {\\varphi\_{n}(t\_{n})} \\\\ \\end{array} \\right| \\neq 0.} \\\\ \\end{array}$$  
(2.49)

Then the system possesses the unique solution

  
$$\\begin{array}{r} {a\_{i} = \\frac{{\\sum\\limits\_{j = 0}^{n}x}(t\_{j})\\Delta\_{ij}}{\\Delta},\\text{\\quad\\quad}i = \\overline{0,n},} \\\\ \\end{array}$$  
(2.50)

where *Δ*[*i**j*] gives the algebraic complement of element (*i**j*). Thus, according to (2.47),

  
$$\\begin{array}{r} {\\psi(t) = x(t\_{0})\\Phi\_{0}(t) + x(t\_{1})\\Phi\_{1}(t) + \\ldots + x(t\_{n})\\Phi\_{n}(t).} \\\\ \\end{array}$$  
(2.51)

The functions *Φ*[*i*](*t*) are linear combinations of the functions *ϕ*[*i*](*t*) and do not depend on the function *x*(*t*). Since the equalities *x*(*t*[*j*]) = *ψ*(*t*[*j*]) hold at the interpolation nodes, the functions *Φ*[*i*](*t*) satisfy the following conditions:

  
$$\\begin{array}{r} {\\Phi\_{i}(t\_{j}) = \\left\\{ \\begin{aligned} 0 & {\\text{for}\\, i \\neq j,} \\\\ 1 & {\\text{for}\\, i = j.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(2.52)

See, e.g., the monograph \[[17](#refbib.xhtml#r17)\] for a discussion of refined interpolation procedures and their properties.

As background information consider some classes of interpolating functions that are widely used in applications. First, *the Lagrange interpolating polynomial*. Consider a sequence of power functions 1, *t*, *t*², ...., *t*^(*n*), ... as a basic one. This sequence is linearly independent on any interval. For defining the function *ψ*(*t*) (2.47), find the functions *Φ*[*i*](*t*) that are linear combinations of the functions *ϕ*[0](*t*), …, *ϕ*[*n*](*t*) and satisfy conditions (2.52). In other words, using the elements of the basic sequence, it is required to construct a polynomial that vanishes at the points *t*[0], …, *t*[*i* − 1] and takes value 1 at the point *t*[*i*]. Such a polynomial has the form

  
$$\\begin{array}{r} {\\Phi\_{i}(t) = A(t - t\_{0})(t - t\_{1})\\cdots(t - t\_{i - 1})(t - t\_{i + 1})\\cdots(t - t\_{n}).} \\\\ \\end{array}$$  
(2.53)

Since *Φ*[*i*](*t*[*i*]) = 1, it follows that

  
$$\\begin{array}{r} {1 = A(t\_{i} - t\_{0})(t\_{i} - t\_{1})\\cdots(t\_{i} - t\_{i - 1})(t\_{i} - t\_{i + 1})\\cdots(t\_{i} - t\_{n}).} \\\\ \\end{array}$$  
(2.54)

Subsequently,

  
$$\\begin{array}{r} {\\Phi\_{i}(t) = \\frac{(t - t\_{0})(t - t\_{1})\\cdots(t - t\_{i - 1})(t - t\_{i + 1})\\cdots(t - t\_{n})}{(t\_{i} - t\_{0})(t\_{i} - t\_{1})\\cdots(t\_{i} - t\_{i - 1})(t\_{i} - t\_{i + 1})\\cdots(t\_{i} - t\_{n})}.} \\\\ \\end{array}$$  
(2.55)

And the Lagrange interpolating polynomial is given by

  
$$\\begin{aligned} {\\psi(t) = L\_{n}(t)} & {= x(t\_{0})\\frac{(t - t\_{1})\\cdots(t - t\_{n})}{(t\_{0} - t\_{1})\\cdots(t\_{0} - t\_{n})} +} \\\\ & {+ x(t\_{1})\\frac{(t - t\_{0})(t - t\_{2})\\ldots(t - t\_{n})}{(t\_{1} - t\_{0})(t\_{1} - t\_{2})\\ldots(t\_{1} - t\_{n})} + \\cdots +} \\\\ & {+ x(t\_{n})\\frac{(t - t\_{0})\\ldots(t - t\_{n - 1})}{(t\_{n} - t\_{0})(t\_{n} - t\_{1})\\ldots(t\_{n} - t\_{n - 1})}.} \\\\ \\end{aligned}$$  
(2.56)

Introduce the function

  
$$\\begin{array}{r} {\\omega\_{n}(t) = {\\prod\\limits\_{i = 0}^{n}{(t - t\_{i})}}} \\\\ \\end{array}$$  
(2.57)

and write the Lagrange interpolating polynomial as

  
$$\\begin{array}{r} {L\_{n}(t) = {\\sum\\limits\_{i = 0}^{n}x}(t\_{i})\\frac{\\omega\_{n}(t)}{(t - t\_{i})\\omega\_{n}^{\\prime}(t\_{i})}.} \\\\ \\end{array}$$  
(2.58)

In the sense of applications, the Lagrange interpolating polynomial is somewhat inconvenient, as adding a new node requires forming a new polynomial. This drawback takes no place for the interpolating polynomial in the Newton representation. More specifically, *the Newton interpolating polynomial* involves the notion of divided differences \[17\] as follows.

Consider (*n* + 1) nodes and as many values of a function *x*(*t*), i.e., *x*(*t*[0]), …, *x*(*t*[*n*]). The first divided difference of the function *x*(*t*) at nodes *t*[*i* − 1], *t*[*i*] is the value

  
$$\\begin{array}{r} {\\Delta\_{i - 1,i} = \\frac{x(t\_{i}) - x(t\_{i - 1})}{t\_{i} - t\_{i - 1}}.} \\\\ \\end{array}$$  
(2.59)

The higher-order divided differences are calculated recursively. The divided difference of order *m* has the general formula

  
$$\\begin{array}{r} {\\Delta\_{i - 1,i,i + 1,\\ldots,i + m} = \\frac{\\Delta\_{i,i + 1,\\ldots,i + m} - \\Delta\_{i - 1,i,i + 1,\\ldots,i + m - 1}}{t\_{i + m} - t\_{i}}.} \\\\ \\end{array}$$  
(2.60)

Express the the Lagrange interpolating polynomial as

  
$$\\begin{array}{r} {L\_{n}(t) = L\_{0}(t) + (L\_{1}(t) - L\_{0}(t)) + \\ldots + (L\_{n}(t) - L\_{n - 1}(t)).} \\\\ \\end{array}$$  
(2.61)

Clearly, this is the identity *L*[*n*](*t*) = *L*[*n*](*t*). It is possible to show \[17\] that

  
$$\\begin{array}{r} {L\_{i}(t) - L\_{i - 1}(t) = \\Delta\_{0,\\ldots,i}\\omega\_{i}(t),} \\\\ \\end{array}$$  
(2.62)

where *ω*[*i*](*t*) = (*t* − *t*[0])⋯(*t* − *t*[*i*]). Then the Newton representation *N*[*n*](*t*) of the Lagrange interpolating polynomial can be written as

  
$$\\begin{aligned} & {L\_{n}(t) = N\_{n}(t) = x(t\_{0}) + \\Delta\_{0,1}(t - t\_{1}) + \\ldots +} \\\\ & {\\text{\\quad\\quad} + \\Delta\_{0,\\ldots,n}(t - t\_{0})(t - t\_{1})\\cdots(t - t\_{n - 1}).} \\\\ \\end{aligned}$$  
(2.63)

Once again, note that an interested reader may derive deep knowledge of the interpolating polynomials from the monograph \[17\].

### 2.3.2Auxiliary dynamic models

In this subsection, we describe a restoration method for missing data (in a time scale) that is based on mathematical models of a data source. Let 𝒳[*h*]^(*N*) = {*x*\[0\],*x*\[*h*\],…,*x*\[*N**h*\]} be a packet of numerical data bound to a time scale with a step *h*. Using these data, construct a step function *x̃*(*t*) of the form

  
$$\\begin{array}{r} {\\widetilde{x}(t) = x\\lbrack ih\\rbrack\\quad\\text{for~}ih \\leq t < (i + 1)h,\\quad i = \\overline{0,N-1}.} \\\\ \\end{array}$$  
(2.64)

Consider a dynamic system with the above step function as its input and an output *y*(*t*) of the form

  
$$\\begin{array}{r} \\left. y\\lbrack nh\\rbrack = \\mathcal{L}(x\\lbrack ih\\rbrack,\\mathbf{a}\\, \\middle| \\, 0 \\leq i < n). \\right. \\\\ \\end{array}$$  
(2.65)

In this expression, ℒ denotes a functional that characterizes the dynamic properties of the system with parameters **a** ∈ *R*^(*m*), where *m* is the dimension of the parameter vector. The parameters **a** actually affect the function *y*(*t*), i.e., *y*(*t*, **a**). For some values of the elements of the vector **a**, the system outputs a packet 𝒴[*h*]^(*N*) = {*y*\[0,**a**\],*y*\[*h*,**a**\],…,*y*\[(*N*−1)*h*,**a**\]} at discrete times *ih*.

Define the total residual between packets 𝒳[*h*]^(*N*), 𝒴[*h*]^(*N*) as

  
$$\\begin{array}{r} {J(\\mathbf{a}) = {\\sum\\limits\_{i = 0}^{N}{(x\\lbrack ih\\rbrack - y\\lbrack ih,\\mathbf{a}\\rbrack)}^{2}}.} \\\\ \\end{array}$$  
(2.66)

The minimum of this residual gives the optimal parameters under which the difference between the above-mentioned packets at the nodes of the *h*\-scale is as small as possible (in terms of the functional *J* (2.66)), i.e.,

  
$$\\begin{array}{r} {\\mathbf{a}^{\*} = \\arg\\min J(\\mathbf{a}).} \\\\ \\end{array}$$  
(2.67)

Substituting the optimal parameters into (2.65) yields the packet 𝒴[*s*]^(*N**r*) = {*y*^(\*)\[0\],*y*^(\*)\[*s*\],…,*y*^(\*)\[(*l*−1)*s*\],*y*^(\*)\[*h*\],*y*\[*h*+*s*\],…,*y*^(\*)\[*h*+(*l*−1)*s*\];*y*^(\*)\[2*h*\],*y*^(\*)\[2*h*+*s*\],…,*y*^(\*)\[*N**h*\]}, where *s* < *h*, *h*/*s* = *r* and *r* is an integer.

This method will be illustrated using an example of a linear dynamic system with a pulse response *w*(*t*, **a**), *t* ≥ 0. Let

  
$$\\begin{array}{r} {w(t) = a\_{1}\\exp( - a\_{2}t),} \\\\ \\end{array}$$  
(2.68)

where *a*[1], *a*[2] are interval-type unknown parameters, i.e., the ones belonging to some intervals 0 < *a*[1] ≤ *a*[1]^+ and *a*[2]^− ≤ *a*[2] ≤ *a*[2]^+, respectively. Generally speaking, the limits of these intervals are unknown. A possible way to find them consists in the global minimization of *J* (2.66) in *a*[1]^+, *a*[2]^− and *a*[2]^+ (or calculation of an admissible small value if the global minimum does not exist).

Supply the step function *x̃*(*t*) to the input of this system to generate the output

  
$$\\begin{array}{r} {y(t) = a\_{1}{\\int\\limits\_{0}^{t}\\exp}( - a\_{2}(t - \\tau))\\widetilde{x}(\\tau)d\\tau.} \\\\ \\end{array}$$  
(2.69)

The interval \[0,*t\]* contains an integer number of subintervals *N* = {*t*/*h*} and *t* = *N**h* + *μ*, where 0 ≤ *μ* < (*N* + 1)*h*. Then the expression (2.69) can be written as

  
$$\\begin{array}{r} {y(t) = \\frac{a\_{1}}{a\_{2}}\\exp( - a\_{2}t)\\,{\\sum\\limits\_{i = 0}^{N}x}\\lbrack ih\\rbrack\\exp(a\_{2}ih)\\left( {\\exp(a\_{2}h) - 1} \\right).} \\\\ \\end{array}$$  
(2.70)

The system output at the nodes of the *h*\-scale is given by

  
$$\\begin{array}{r} {y\\lbrack ih\\rbrack = \\frac{a\_{1}}{a\_{2}}\\left( {\\exp(a\_{2}h) - 1} \\right)\\exp( - a\_{2}ih)\\,{\\sum\\limits\_{j = 0}^{i}x}\\lbrack jh\\rbrack\\exp(a\_{2}jh).} \\\\ \\end{array}$$  
(2.71)

Consequently, the total residual functional (2.66) takes the form

  
$$\\begin{array}{r} \\left. J(a\_{1},a\_{2}) = {\\sum\\limits\_{i = 0}^{N}{\\sum\\limits\_{j = 0}^{i}\\left( {A\_{i,j}(a\_{1},a\_{2})x\\lbrack jh\\rbrack} \\right)^{2}}}\\Rightarrow\\min, \\right. \\\\ \\end{array}$$  
(2.72)

where

  
$$\\begin{array}{r} {A\_{i,j} = \\left\\{ \\begin{aligned} {\\frac{a\_{1}}{a\_{2}}\\left( {\\exp(a\_{2}h) - 1} \\right)\\exp(a\_{2}h(j - i))} & {\\text{for}\\, j < i,} \\\\ {\\frac{a\_{1}}{a\_{2}}\\left( {\\exp(a\_{2}h) - 1} \\right) - 1} & {\\text{~for}\\, j = i.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(2.73)

Note that the functional (2.72) possesses a rather complicated structure for an analytical study of its properties such as unique minimum, convexity (concavity), and so on. Therefore, in applications the missing data should be restored (or synchronized with other data packets) using numerical global minimization methods.

As soon as the parameters *a*[1] and *a*[2] are calculated, the missing data with the step *s* can be restored by

  
$$\\begin{aligned} {y\\lbrack ih + ks\\rbrack} & {= \\frac{a\_{1}}{a\_{2}}\\exp( - a\_{2}(ih + ks))\\,{\\sum\\limits\_{i = 0}^{N}x}\\lbrack ih\\rbrack\\exp(a\_{2}ih)\\left( {\\exp(a\_{2}h) - 1} \\right),} \\\\ i & {= \\overline{0,N},\\,\\, k = \\overline{0,M},\\,\\, M = \\left\\{ h/s \\right\\}.} \\\\ \\end{aligned}$$  
(2.74)

### 2.3.3Spatial entropy decomposition

As emphasized earlier, the data formed by government statistics services are associated with certain spatial units (regions), each having a set of attributes, i.e., indicators. The dimensions of such regions and information about the values of these indicators are often related to each other. In many cases, the smaller is a region under consideration, the less accessible is information about its indicators. This leads to a rather topical problem of “spreading” the available state indicators of large regions to small districts within them using some indirect information about the latter.

Consider an economic space 𝔼 consisting of *I* regions. Each region *i* contains *M*[*i*] districts, as shown in [Fig. 2.8](#chapter2.xhtml#f2_8). Let the regions *i* and districts within them (*i*, *j*) be characterized by unique homogeneous indicators *S*[*i*] and *S*[*i**j*], respectively. For example, the list of possible indicators includes population size, production density, service endowment, and so on. The regional and district indicators, *S*[*i*] and *S*[*i**j*], satisfy the balance constraints

  
$$\\begin{array}{r} {S\_{i} = {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}},\\text{\\quad\\quad}i = \\overline{1,I}.} \\\\ \\end{array}$$  
(2.75)

![Figure 2.8](images/fig2_8.jpg)

[Figure 2.8](#chapter2.xhtml#f2_8b)

Each region and hence district produces the goods of *r* types or disposes of *r* types of resources. Assume that, for each type *k* of goods (resources), the production functions of region *i* depend on the state indicators of all regions, i.e., $\\overset{\\rightarrow}{S} = \\left\\{ S\_{1},\\ldots,S\_{I} \\right\\}.$ Denote these functions by $Q\_{ik}(\\overset{\\rightarrow}{S}),\\, i = \\overline{1,I},\\, k = \\overline{1,r}.$ The same hypothesis also applies to the districts; denote their production functions by *q*[*i**j**k*](𝕊), where 𝕊 = {*S*[11],…,*S*[1, *M*[1]];…;*S*[*I*, 1],…,*S*[*I*, *M*[*I*]]}. Then the resource constraints have the form

  
$$\\begin{array}{r} {{\\sum\\limits\_{j = 1}^{M\_{i}}q\_{ijk}}(\\mathbb{S}) = Q\_{ik}(\\mathbf{S}),\\text{\\quad\\quad}i = \\overline{1,I},\\,\\, k = \\overline{1,r}.} \\\\ \\end{array}$$  
(2.76)

Suppose that the regional indicators **S** are known whereas the district ones 𝕊 are unknown. The problem is to find the district indicators taking into account the balance and resource constraints given by (2.75) and (2.76). The total number of the district indicators makes up $m = {\\sum\\limits\_{i = 1}^{I}M\_{i}},$ as by assumption each district and region has a single indicator. In addition, the problem includes (*r* + 1)*I* balance and resource constraints totally, and *m* > (*r* + 1)*I*. Therefore, numerous collections of district indicators satisfy equalities (2.75, 2.76).

An approach to obtain a unique collection of district indicators proceeds from the entropy maximization principle. As a matter of fact, entropy is a measure of uncertainty in the distribution of regional indicators over corresponding districts \[[138](#refbib.xhtml#r138)\], i.e.,

  
$$\\begin{array}{r} {H(\\mathbb{S}) = - {\\sum\\limits\_{i = 1,j = 1}^{I,M\_{i}}S\_{ij}}\\ln\\frac{S\_{ij}}{a\_{ij}e},} \\\\ \\end{array}$$  
(2.77)

where 𝕊 is a matrix with entries *S*[*i**j*] that characterizes the distribution of district indicators. The distribution of highest uncertainty, **S**, answers the maximum value of the entropy *H* under the balance and resource constraints (2.75, 2.76). Any prior information about the districts within the regions of interest can be incorporated into the parameters *a*[*i**j*] of the entropy function *H*.

Thus, the distribution of the regional indicators over the districts, called *entropy decomposition*, is the solution of the optimization problem

  
$$\\begin{array}{r} \\left. H(\\mathbb{S})\\Rightarrow\\max,\\quad\\mathbb{S} \\in D, \\right. \\\\ \\end{array}$$  
(2.78)

where

  
$$\\begin{array}{r} {D = \\left\\{ S\_{ij} \\middle| {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}} = S\_{i};\\,\\,{\\sum\\limits\_{j = 1}^{M\_{i}}q\_{ijk}}(\\mathbb{S}) = Q\_{ik}(S),\\quad i = \\overline{1,I},\\,\\, k = \\overline{1,r} \\right\\}.} \\\\ \\end{array}$$  
(2.79)

In this general statement, all regions and districts are related to each other through corresponding production functions. Another extreme case is when all regions and districts are isolated, i.e., the regional and district production functions depend only on the state indicators of their own regions or districts:

  
$$\\begin{array}{r} {q\_{ijk}(\\mathbb{S}) = q\_{ijk}(S\_{ij}),\\quad Q\_{ik}(\\mathbf{S}) = Q\_{ik}(S\_{i});\\,\\, i = \\overline{1,I}\\,\\, k = \\overline{1,r}.} \\\\ \\end{array}$$  
(2.80)

For the isolated regions, the entropy decomposition problem (2.78) is reduced to *I* optimization problems of the form

  
$$\\begin{array}{r} \\left. H\_{i}(\\mathbb{S}\_{i})\\Rightarrow\\max,\\quad\\mathbb{S}\_{i} \\in D\_{i}, \\right. \\\\ \\end{array}$$  
(2.81)

where

  
$$\\begin{array}{r} {H\_{i}(\\mathbb{S}\_{i}) = - {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}}\\ln\\frac{S\_{ij}}{a\_{ij}e},} \\\\ \\end{array}$$  
(2.82)

  
$$\\begin{array}{r} {D\_{i} = \\left\\{ S\_{ij} \\middle| {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}} = S\_{i},\\,\\,{\\sum\\limits\_{j = 1}^{M\_{i}}q\_{ijk}}(S\_{ij}) = Q\_{ik}(S\_{i}),\\quad i = \\overline{1,I},\\,\\, k = \\overline{1,r} \\right\\}.} \\\\ \\end{array}$$  
(2.83)

The production functions *q*[*i**j**k*] of these districts form nonlinear functions of their state indicators. However, if an economy is in a neighborhood of an equilibrium, then the linear representation of the production functions becomes a completely adequate description of these functions, i.e.,

  
$$\\begin{array}{r} {q\_{ijk}(S\_{ij}) = c\_{ijk}S\_{ij},\\text{\\quad\\quad}i = \\overline{1,I},\\,\\, k = \\overline{1,r}.} \\\\ \\end{array}$$  
(2.84)

Here *c*[*i**j**k*] indicate the specific outputs of good *k* in district (*i*, *j*). In this case, the admissible set *D*[*i*] (2.83) is given by the system of linear equalities

  
$$\\begin{array}{r} {D\_{i} = \\left\\{ S\_{ij} \\middle| {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}} = S\_{i};\\,\\,\\,{\\sum\\limits\_{j = 1}^{M\_{i}}c\_{ijk}}S\_{ij} = Q\_{ik}(S\_{i}),\\quad i = \\overline{1,I},\\,\\, k = \\overline{1,r} \\right\\}.} \\\\ \\end{array}$$  
(2.85)

Consider the specifics of the entropy decomposition procedure with the linear production functions for one region (*I* = 1) and one type of resources (*r* = 1):

  
$$\\begin{aligned} {H\_{1}(\\mathbb{S}\_{1})} & \\left. = - {\\sum\\limits\_{j = 1}^{M\_{1}}S\_{1j}}\\ln\\frac{S\_{1j}}{a\_{1j}e}\\Rightarrow\\max, \\right. \\\\ {\\sum\\limits\_{j = 1}^{M\_{1}}S\_{1j}} & {= S\_{1},\\quad{\\sum\\limits\_{j = 1}^{M\_{1}}c\_{1j1}}S\_{1j} = Q\_{11}(S\_{1}).} \\\\ \\end{aligned}$$  
(2.86)

This problem is characterized by the following parameters: the prior probabilities *a*[1*j*]; the state indicator *S*[1] of the region; the specific productivities *c*[1*j*1] and production function *Q*[11] of the region. The solution of the problem, i.e., the entropy-optimal distribution of the regional state indicators over their districts depends on these parameters.

Introduce new variables in order to slightly reduce the number of parameters in the problem. Denote

  
$$\\begin{array}{r} {w\_{1j} = \\frac{S\_{1j}}{S\_{1}},\\text{\\quad\\quad}h\_{1j1} = \\frac{c\_{1j1}}{Q\_{11}(S\_{1})},\\,\\, j = \\overline{1,M\_{1}}.} \\\\ \\end{array}$$  
(2.87)

If the regional indicator *S*[1] is given, then the variables *h*[1*j*1] are also fixed. With these notations, the entropy decomposition problem can be written as

  
$$\\begin{aligned} {H(\\mathbf{w})} & \\left. = - {\\sum\\limits\_{j = 1}^{M}w\_{j}}\\ln\\frac{w\_{j}}{a\_{j}e}\\Rightarrow\\max, \\right. \\\\ {\\sum\\limits\_{j = 1}^{M}w\_{j}} & {= 1;\\quad{\\sum\\limits\_{j = 1}^{M}h\_{j}}\\, w\_{j} = q,} \\\\ \\end{aligned}$$  
(2.88)

where *q* = 1/*S*[1] and the subscripts *i* = *k* = 1 are omitted.

Solve the problem using the Lagrange method of multipliers. The Lagrange function has the form

  
$$\\begin{array}{r} {L(\\mathbf{w},\\mu,\\lambda) = H(\\mathbf{w}) + \\mu(1 - {\\sum\\limits\_{j = 1}^{M}w\_{j}}) + \\lambda(q - {\\sum\\limits\_{j = 1}^{M}h\_{j}}\\, w\_{j}).} \\\\ \\end{array}$$  
(2.89)

The first-order optimality conditions of the Lagrange function yield the equations

  
$$\\begin{aligned} w\_{j} & {= a\_{j}\\exp( - \\mu - \\lambda\\, h\_{j}) = a\_{j}\\, u\\, z^{h\_{j}};} \\\\ & {u = \\exp( - \\mu),\\, z = \\exp( - \\lambda).} \\\\ \\end{aligned}$$  
(2.90)

Taking into account the balance and resource constraints in (2.88), write the following equation for the Lagrange multiplier *λ*:

  
$$\\begin{array}{r} {{\\sum\\limits\_{j = 1}^{M}a\_{j}}\\, z^{h\_{j}}\\,(h\_{j} - q) = 0,\\text{\\quad\\quad}j = \\overline{1,M}.} \\\\ \\end{array}$$  
(2.91)

Set

  
$$\\begin{array}{r} {c\_{j} = a\_{j}(h\_{j} - q),\\text{\\quad\\quad}j = \\overline{1,M},} \\\\ \\end{array}$$  
(2.92)

and transform equation (2.91) to

  
$$\\begin{array}{r} {f(z) = {\\sum\\limits\_{j = 1}^{M}c\_{j}}z^{h\_{j}} = 0,\\quad z > 0.} \\\\ \\end{array}$$  
(2.93)

Order the parameters *h*[*j*] so that

  
$$\\begin{array}{r} {0 < h\_{1} < h\_{2} < \\cdots < h\_{l} < q < h\_{l + 1} < \\cdots < h\_{M}.} \\\\ \\end{array}$$  
(2.94)

As a result,

  
$$\\begin{array}{r} {c\_{j} < 0\\quad\\text{for~}j = \\overline{1,l}\\quad\\text{and}\\quad c\_{j} > 0\\quad\\text{~for~}j = \\overline{l+1,M}.} \\\\ \\end{array}$$  
(2.95)

Consider equation (2.93) with the coefficients *c*[*j*] of arbitrary sign. Note that it has the root *z*[0] = 0. Hence, this equation can be written as

  
$$\\begin{array}{r} {f(z) = z^{h\_{1}}f\_{1}(z) = 0,\\,\\,\\, z > 0,} \\\\ \\end{array}$$  
(2.96)

where the function

  
$$\\begin{array}{r} {f\_{1}(z) = c\_{1} + {\\sum\\limits\_{j = 2}^{M}c\_{j}}z^{h\_{j} - h\_{1}}} \\\\ \\end{array}$$  
(2.97)

has no zero roots.

Now consider equations (2.96, 2.97) in which the coefficients *c*[*j*] are ordered in accordance with (2.95), i.e.,

  
$$\\begin{array}{r} {c\_{j} < 0\\,\\,\\text{for}\\,\\, j = 1,\\ldots,l,\\text{\\quad\\quad}c\_{j} > 0\\,\\,\\text{for}\\,\\, j = l + 1,\\ldots,M.} \\\\ \\end{array}$$  
(2.99)

Thus, it has been shown that equation (2.98) possesses a unique positive solution under conditions (2.95).

 [Table 2.1:](#chapter2.xhtml#t2_1b) Regional state indicators. 

 
|  |
| --- |
| no. || *c̃*[*j*] || *S*[*j*] || *S̃*[*j*] |
| 1 || 0.035 || 0.0098 || 0.0144 |
| --- | --- | --- | --- |
| 2 || 0.018 || 0.0251 || 0.0247 |
| 3 || 0.035 || 0.0098 || 0.0149 |
| 4 || 0.018 || 0.0253 || 0.0245 |
| 5 || 0.028 || 0.0145 || 0.0213 |
| 6 || 0.015 || 0.0296 || 0.0259 |
| 7 || 0.038 || 0.0083 || 0.0142 |
| 8 || 0.029 || 0.0137 || 0.0222 |
| 9 || 0.039 || 0.0079 || 0.0144 |
| 10 || 0.047 || 0.0051 || 0.0102 |
| 11 || 0.035 || 0.0098 || 0.0175 |
| 12 || 0.026 || 0.0161 || 0.0238 |
| 13 || 0.036 || 0.0093 || 0.0168 |
| 14 || 0.028 || 0.0145 || 0.0214 |
| 15 || 0.032 || 0.0116 || 0.0193 |
| 16 || 0.038 || 0.0083 || 0.0126 |
| 17 || 0.045 || 0.0057 || 0.0098 |
| 18 || 0.037 || 0.0088 || 0.0151 |
| 19 || 0.028 || 0.0145 || 0.0185 |
| 20 || 0.038 || 0.0083 || 0.0097 |
| 21 || 0.038 || 0.0104 || 0.0079 |
| 22 || 0.020 || 0.0225 || 0.0292 |
| 23 || 0.024 || 0.0181 || 0.0243 |
| 24 || 0.038 || 0.0084 || 0.0097 |
| 25 || 0.007 || 0.0459 || 0.0433 |
| 26 || 0.028 || 0.0145 || 0.0169 |
|  |

### 2.3.4Randomized restoration method for missing data

**1. Structure of randomized restoration procedure for missing data**

Consider components and properties of the informational support (infoware) of machine learning problems. A learning collection consists of some data on the functioning of an object *O* ([Fig. 2.10](#chapter2.xhtml#f2_10)) as well as on the measured input **x**(*t*) ∈ *R*^(*m*) and output **y**(*t*) ∈ *R*^(*n*) of the object *O*. The variables **x**(*t*) and **y**(*t*) contain measurement errors *η*(*t*) ∈ *R*^(*m*) and *ξ*(*t*) ∈ *R*^(*n*), respectively. As a rule, information about them have a hypothetical character. A common assumption is that they figure in a learning collective additively:

  
$$\\begin{array}{r} {\\mathbf{x}(t) = \\mathbf{x}^{0}(t) + \\eta(t);\\text{\\quad\\quad}\\mathbf{y}(t) = \\mathbf{y}^{0}(t) + \\xi(t),} \\\\ \\end{array}$$  
(2.100)

![Figure 2.10](images/fig2_10.jpg)

[Figure 2.10](#chapter2.xhtml#f2_10b)

where **x**⁰(*t*) and **y**⁰(*t*) are pure variables.

Suppose that the input and output are measured in the same time scale *t* = *k**h* with a step *h* and on the same time interval 𝒯 = \[0, *T*\]. Hence, a real learning collection consists of a data matrix describing the input and output of the object *O*.

Data arrays for the input and output may have omissions; see the interval \[*k*^−, *k*^+\] in [Fig. 2.11](#chapter2.xhtml#f2_11). There are three possible cases of such omissions: omissions in output data, omissions in input data and omissions in both types of data (not necessarily at the same time instants).

![Figure 2.11: Example of missing data ensemble (MDE).](images/fig2_11.jpg)

[Figure 2.11:](#chapter2.xhtml#f2_11b) Example of missing data ensemble (MDE).

The main idea of randomized restoration of missing data is to replace the existing omissions by a missing data ensemble (MDE), i.e., the random values of the input and output components (see [Fig. 2.11](#chapter2.xhtml#f2_11)) optimized taking into account the available measurements. This is done using a randomized parametric model (RPM) of the object, whose probabilistic characteristics (the probability density functions (PDFs) of its parameters) are obtained through maximum entropy estimation (MEE). Details will be presented in [Appendix A](#appA.xhtml#appA).

The optimized MDE is generated by the sampling of the optimal PDFs \[[64](#refbib.xhtml#r64)\]. This MDE can be directly used for solving different machine learning problems. Also, it is possible to determine numerical characteristics of the optimized MDE, such as mean, median, variance pipe, interquantile data sets, etc. [Figure 2.11](#chapter2.xhtml#f2_11) gives an illustration of this approach.

If omissions occur in output data, the procedure employs the input data **x**\[*k**h*\], the RPM-O model and the output data with omissions $\\widetilde{\\mathbf{y}}\\lbrack kh\\rbrack$ for calculating the entropy-optimal PDFs ([Fig. 2.12(a)](#chapter2.xhtml#f2_12)) and also for generating the ensemble 𝒴 of the restored input data.

![Figure 2.12: Diagrams of RPMs.](images/fig2_12.jpg)

[Figure 2.12:](#chapter2.xhtml#f2_12b) Diagrams of RPMs.

The existing omissions in input data are restored using an additional RPM-I model with the input represented by an optimized sequence of independent random vectors *η*\[*k**h*\] and the input data with omissions $\\widetilde{\\mathbf{x}}\\lbrack kh\\rbrack.$ The PDFs of the parameters and this sequence are obtained through MEE. These functions are then used to generate the ensembles ℰ of the random vectors *η*\[*k**h*\] and an ensemble 𝒳 of the restored input data; see [Fig. 2.12(b)](#chapter2.xhtml#f2_12).

Finally, consider the case of omissions both in the input and output data. First, the ensembles ℰ of the random vectors *η*\[*k**h*\] and the ensemble 𝒳 of the input data are restored. Second, they are adopted for restoring the ensembles 𝒴 of the output data ([Fig. 2.12(c)](#chapter2.xhtml#f2_12)).

The set of randomized restoration methods for missing data will be denoted by *RRMD* (Random Restored Missing Data).

**2. Optimization algorithms for MDE**

**a. Omissions in output data**

Consider a discrete observation time interval *τ* = \[0, *N*\] On this interval, there are a set of input data **x** ∈ *R*^(*m*) without omissions, **x**\[0\], …, **x**\[*N*\], and a set of output data **y** ∈ *R*^(*n*) with omissions, **y**\[0\], …, **y**\[*k*^− − 1\], **y**\[*k*^+ + 1\], …, **y**\[*N*\]. The data **y**\[*k*^−\], …, **y**\[*k*^+\] are missing.

Construct the matrix

  
$$\\begin{array}{r} {X\_{(k - \\varrho)} = \\left\\lbrack {\\mathbf{x}\\lbrack k - \\varrho\\rbrack,\\mathbf{x}\\lbrack k - \\varrho + 1\\rbrack,\\ldots,\\mathbf{x}\\lbrack k\\rbrack} \\right\\rbrack} \\\\ \\end{array}$$  
(2.101)

from the input data set, where *ρ* < *N* is a parameter.

The output data contain additive errors *ξ*\[*k*\] ∈ *R*^(*n*) of the interval type:

  
$$\\begin{array}{r} {\\xi\\lbrack k\\rbrack \\in \\Xi\_{k} = \\lbrack\\xi^{-},\\xi^{+}\\rbrack.} \\\\ \\end{array}$$  
(2.102)

The probabilistic properties of errors are characterized by PDFs *Q*[*k*](*ξ*\[*k*\]), $k = \\overline{0,N},$ which are assumed to be continuously differentiable.

In the general case, the relation between the input and output of the object *O* is described by a randomized parametric dynamic model RDM-O of the form

  
$$\\begin{array}{r} {\\hat{\\mathbf{y}}\\lbrack k\\rbrack = \\mathbb{B}\\left( {\\mathbf{a},X\_{(k - \\varrho)}} \\right),} \\\\ \\end{array}$$  
(2.103)

where 𝔹 is a nonlinear functional with random parameters **a** ∈ *R*^(*r*) of the interval type:

  
$$\\begin{array}{r} {\\mathbf{a} \\in \\mathcal{A} = \\lbrack\\mathbf{a}^{-},\\mathbf{a}^{+}\\rbrack.} \\\\ \\end{array}$$  
(2.104)

The probabilistic properties of these parameters are characterized by a PDF *P*(**a**), which is assumed to be continuously differentiable.

The observed output of RDM-O is given by

  
$$\\begin{array}{r} {\\mathbf{v}\\lbrack k\\rbrack = \\hat{\\mathbf{y}}\\lbrack k\\rbrack + \\xi\\lbrack k\\rbrack,\\text{\\quad\\quad}k = \\overline{0,N}.} \\\\ \\end{array}$$  
(2.105)

For determining the optimal PDFs, apply the randomized machine learning (RML) algorithm suggested in \[[148](#refbib.xhtml#r148)\]. In the case under consideration, it has the form

  
$$\\begin{aligned} & {\\quad\\mathcal{H}\\lbrack P(\\mathbf{a}),Q(\\xi)\\rbrack = - {\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\ln P(\\mathbf{a})d\\mathbf{a} -} \\\\ & \\left. - {\\sum\\limits\_{k = 0}^{T}{\\int\_{\\Xi\_{k}}Q\_{k}}}(\\xi\\lbrack k\\rbrack)\\ln Q\_{k}(\\xi\\lbrack k\\rbrack)d\\xi\\lbrack k\\rbrack\\Rightarrow\\max, \\right. \\\\ & {\\quad{\\int\_{\\mathcal{A}}P}(\\mathbf{a})d\\mathbf{a} = 1;\\quad{\\int\_{\\Xi\_{k}}Q\_{k}}(\\xi\\lbrack k\\rbrack)d\\xi\\lbrack k\\rbrack = 1,\\,\\, k = \\overline{0,N},} \\\\ & {\\quad{\\int\_{A}P}(\\mathbf{a})\\mathbb{B}\\left( {\\mathbf{a},X\_{(k - \\varrho)}} \\right)d\\mathbf{a} + {\\int\_{\\Xi\_{k}}Q\_{k}}(\\xi\\lbrack k\\rbrack)\\xi\\lbrack k\\rbrack d\\xi\\lbrack k\\rbrack = \\mathbf{y}\\lbrack k\\rbrack,} \\\\ & {\\quad k \\neq k^{-},\\ldots,k^{+};k = \\overline{0,N}.} \\\\ \\end{aligned}$$  
(2.106)

The PDFs are continuously differentiable, and the problem (2.106) belongs to the class of Lyapunov-type functional optimization problems \[[77](#refbib.xhtml#r77)\]. Hence, it is possible to construct an analytical solution parameterized by the Lagrange multipliers {*θ*^((0)),…,*θ*^(*k*^− − 1),*θ*^(*k*^+ + 1),…,*θ*^((*N*))}:

  
$$\\begin{aligned} & {P^{\*}(\\mathbf{a},\\theta) = \\frac{\\exp\\left\\lbrack {- {\\sum\\limits\_{k = 0}^{N}\\langle}\\theta^{(k)},\\mathbb{B}\\left( \\left. \\mathbf{a},X\_{(k - \\varrho)} \\right\\rangle \\right)} \\right\\rbrack}{\\mathcal{P}(\\theta)},} \\\\ & {\\text{\\quad\\quad}Q\_{k}^{\*}(\\xi\\lbrack k\\rbrack,\\theta^{(k)}) = \\frac{\\exp\\left( {- \\left\\langle \\theta^{(k)},\\xi\\lbrack k\\rbrack \\right\\rangle} \\right)}{\\mathcal{Q}\_{k}(\\theta^{(k)})},} \\\\ & {\\quad\\text{\\quad\\quad}k \\neq k^{-},\\ldots,k^{+};\\quad k = \\overline{0,N}.} \\\\ \\end{aligned}$$  
(2.107)

Here

  
$$\\begin{aligned} & {\\mathcal{P}(\\theta) = {\\int\_{\\mathcal{A}}\\exp}\\left\\lbrack {- {\\sum\\limits\_{k = 0}^{N}\\langle}\\theta^{(k)},\\mathbb{B}\\left( \\left. \\mathbf{a},X\_{(k - \\varrho)} \\right\\rangle \\right)} \\right\\rbrack d\\mathbf{a},} \\\\ & {\\text{\\quad\\quad}\\mathcal{Q}\_{k}(\\theta^{(k)}) = {\\int\_{\\Xi\_{k}}\\exp}\\left( {- \\left\\langle \\theta^{(k)},\\xi\\lbrack k\\rbrack \\right\\rangle} \\right)d\\xi\\lbrack k\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\quad k \\neq k^{-},\\ldots,k^{+};\\quad k = \\overline{0,N}.} \\\\ \\end{aligned}$$  
(2.108)

The Lagrange multipliers are determined from the system of equations

  
$$\\begin{array}{r} {\\frac{\\mathbf{M}\_{k}(\\theta)}{\\mathcal{P}(\\theta)} + \\frac{\\mathbf{N}\_{k}(\\theta^{(k)})}{\\mathcal{Q}\_{k}(\\theta^{(k)})} = \\mathbf{y}\\lbrack k\\rbrack,\\text{\\quad\\quad}k \\neq k^{-},\\ldots,k^{+};k = \\overline{0,N},} \\\\ \\end{array}$$  
(2.109)

where

  
$$\\begin{aligned} {\\mathbf{M}\_{k}(\\theta) = \\int\_{\\mathcal{A}}} & {\\exp\\left\\lbrack {- {\\sum\\limits\_{k = 0}^{T}\\left\\langle \\theta^{(k)},\\mathbb{B}\\left( {\\mathbf{a},X\_{(k - \\varrho)}} \\right) \\right\\rangle}} \\right\\rbrack\\mathbb{B}\\left( {\\mathbf{a},X\_{(k - \\varrho)}} \\right)d\\mathbf{a},} \\\\ \\end{aligned}$$  
(2.110)

  
$$\\begin{aligned} & {\\mathbf{N}\_{k}(\\theta^{(k)}) = {\\int\_{\\Xi\_{k}}\\exp}\\left( {- \\left\\langle \\theta^{(k)},\\xi\\lbrack k\\rbrack \\right\\rangle} \\right)\\xi\\lbrack k\\rbrack d\\xi\\lbrack k\\rbrack.} \\\\ \\end{aligned}$$  
(2.111)

**b. Omissions in input data**

Restoring omissions in input data is more difficult than the ones in output data. Really, the origin mechanism of input data and the source of its excitation are both unknown. In terms of the approach adopted here, this means that the model generating input data and also the process exciting it are unknown. All these factors increase the level of uncertainty in the problem, motivating the choice of randomization.

The randomized approach consists in using a sequence of independent random vectors $\\zeta\\lbrack k\\rbrack \\in R^{q}\\,\\,(k\\overline{0,N})$ with special probabilistic characteristics, and a randomized parametric model, the choice of which is determined by its complexity.

Well, consider the observation interval *τ* = \[0, *N*\] and an input data set **x** ∈ *R*^(*m*) with omissions **x**\[0\], …, **x**\[*k*^− − 1\], **x**\[*k*^+ + 1\], …, **x**\[*T*\]. The data **x**\[*k*^−\], …, **x**\[*k*^+\] are missing.

To restore the missing input data, assume that they are the result of transforming a sequence of independent random vectors *ζ*\[*k*\] ∈ *R*^(*q*), *k* ∈ *τ*. Let the vectors *ζ*\[*k*\] be of the interval type, i.e.,

  
$$\\begin{array}{r} {\\zeta\\lbrack k\\rbrack \\in \\mathcal{Z}\_{k} = \\lbrack\\zeta^{-}\\lbrack k\\rbrack,\\zeta^{+}\\lbrack k\\rbrack\\rbrack,\\text{\\quad\\quad}k = \\overline{0,N},} \\\\ \\end{array}$$  
(2.112)

Due to the uncertainty and insufficient knowledge about the process and its transformation, choose the randomized parametric (RPM-I) model

  
$$\\begin{array}{r} {\\hat{\\mathbf{x}}\\lbrack k\\rbrack = \\mathbb{F}\\left( {\\mathbf{c},Z\_{(k - \\rho)}} \\right),} \\\\ \\end{array}$$  
(2.113)

where 𝔽 is a nonlinear vector functional with random parameters **c** ∈ *R*^(*s*) and *Z*[(*k* − *ρ*)] is the input matrix of dimensions (*q* × *ρ*) composed of the column vectors *ζ*\[*k*\] ∈ *R*^(*q*), i.e.,

  
$$\\begin{array}{r} {Z\_{(k - \\rho)} = \\left\\lbrack {\\zeta\\lbrack k - \\rho\\rbrack,\\zeta\\lbrack k - \\rho + 1\\rbrack,\\ldots,\\zeta\\lbrack k\\rbrack} \\right\\rbrack.} \\\\ \\end{array}$$  
(2.114)

Introduce the matrix

  
$$\\begin{array}{r} {Z = \\left\\lbrack {Z\_{( - \\rho)},Z\_{(1 - \\rho)},\\ldots,Z\_{(N - \\rho)}} \\right\\rbrack,} \\\\ \\end{array}$$  
(2.115)

which characterizes the input of the RPM-I model (2.113) on the time interval $k = \\overline{0,N}.$ The matrix *Z* is random and of the interval type:

  
$$\\begin{array}{r} {Z \\in \\mathcal{Z} = {\\underset{k = 0}{\\overset{N}{\\cup}}\\mathcal{Z}\_{k}} = \\lbrack Z^{-},Z^{+}\\rbrack.} \\\\ \\end{array}$$  
(2.116)

The random parameters of this model are

  
$$\\begin{array}{r} {\\mathbf{c} \\in \\mathcal{C} = \\lbrack\\mathbf{c}^{-},\\mathbf{c}^{+}\\rbrack.} \\\\ \\end{array}$$  
(2.117)

The probabilistic properties of the parameters **c** and matrix *Z* (2.115) are characterized by a joint probability density function (PDF) *W*(**c**, *Z*) with the domain of definition

  
$$\\begin{array}{r} {\\mathcal{F} = \\mathcal{C}{\\cup \\mathcal{Z}}.} \\\\ \\end{array}$$  
(2.118)

This function is assumed to be continuously differentiable.

Let the available input data **x**\[*k*\] contain errors *η*\[*k*\] ∈ *R*^(*m*) of the interval type:

  
$$\\begin{array}{r} {\\eta\\lbrack k\\rbrack \\in \\mathcal{E}\_{k} = \\lbrack\\eta^{-},\\eta^{+}\\rbrack.} \\\\ \\end{array}$$  
(2.119)

The probabilistic properties of the errors are characterized by PDFs $G\_{k}(\\eta\\lbrack k\\rbrack),k = \\overline{0,N},$ which are assumed to be continuously differentiable as well.

The observed output of the RPM-I model is given by

  
$$\\begin{array}{r} {\\mathbf{z}\\lbrack k\\rbrack = \\hat{\\mathbf{x}}\\lbrack k\\rbrack + \\eta\\lbrack k\\rbrack,\\text{\\quad\\quad}k = \\overline{0,N}.} \\\\ \\end{array}$$  
(2.120)

Clearly, the missing input data are restored using a model similar to RDM-O, but with the random input *ζ*\[*k*\].

Apply the RML algorithm \[148\] for determining the PDFs *W*(**c**, *Z*) and $G\_{k}(\\zeta\\lbrack k\\rbrack),\\, k = \\overline{0,N}.$ In the case under consideration, this algorithm has the form

  
$$\\begin{aligned} & {\\quad\\mathcal{H}\\lbrack W(\\mathbf{c},Z),G(\\eta)\\rbrack = - {\\int\_{\\mathcal{F}}W}(\\mathbf{c},Z)\\ln W(\\mathbf{c},Z)\\, d\\mathbf{c}\\, dZ -} \\\\ & \\left. - {\\sum\\limits\_{k \\in \\mathcal{K}}{\\int\_{\\mathcal{E}\_{k}}G\_{k}}}(\\eta\\lbrack k\\rbrack)\\ln G\_{k}(\\eta\\lbrack k\\rbrack)d\\eta\\lbrack k\\rbrack\\Rightarrow\\max, \\right. \\\\ & {\\quad{\\int\_{\\mathcal{F}}W}(\\mathbf{c},Z)\\, d\\mathbf{c}\\, dZ = 1;\\quad{\\int\_{\\mathcal{E}\_{k}}G\_{k}}(\\eta\\lbrack k\\rbrack)d\\eta\\lbrack k\\rbrack = 1,} \\\\ & {\\quad{\\int\_{\\mathcal{F}}W}(\\mathbf{c},Z)\\mathbb{F}\\left( {\\mathbf{c},Z\_{(k - \\rho)}} \\right)d\\mathbf{c}\\, dZ + {\\int\_{\\mathcal{E}\_{k}}G\_{k}}(\\eta\\lbrack k\\rbrack)\\eta\\lbrack k\\rbrack d\\eta\\lbrack k\\rbrack = \\mathbf{x}\\lbrack k\\rbrack,} \\\\ & {\\quad k \\in \\mathcal{K},} \\\\ \\end{aligned}$$  
(2.121)

where the indexing set $\\mathcal{K} = \\overline{0,N}$ does not include *k* = *k*^−, …, *k*^+.

This problem belongs to the same class as (2.106). Its solution is given by

  
$$\\begin{array}{rll} & {W^{\*}(\\mathbf{c},Z,\\lambda) = \\frac{\\exp\\left\\lbrack {- {\\sum\\limits\_{k \\in \\mathcal{K}}\\langle}\\lambda^{(k)},\\mathbb{F}\\left( \\left. \\mathbf{c},Z\_{(k - \\rho)} \\right\\rangle \\right)} \\right\\rbrack}{\\mathcal{W}(\\lambda)},} & \\\\ & {G\_{k}^{\*}(\\eta\\lbrack k\\rbrack,\\lambda^{(k)}) = \\frac{\\exp\\left( {- \\left\\langle \\lambda^{(k)},\\eta\\lbrack k\\rbrack \\right\\rangle} \\right)}{\\mathcal{G}\_{k}(\\lambda^{(k)})},} & \\\\ & {k \\in \\mathcal{K},} & \\\\ \\end{array}$$  
(2.122)

where

  
$$\\begin{aligned} {\\mathcal{W}(\\lambda) = \\int\_{\\mathcal{F}}} & {\\exp\\left\\lbrack {- \\sum\\left\\langle \\lambda^{(k)},\\mathbb{F}\\left( \\left. \\mathbf{c},Z\_{(k - \\rho)} \\right\\rangle \\right) \\right.} \\right\\rbrack d\\mathbf{c},\\quad\\mathcal{G}\_{k}(\\lambda^{(k)}) =} \\\\ & {\\,\\, = int\_{\\mathcal{E}\_{k}}\\exp\\left( {- \\left\\langle \\lambda^{(k)},\\eta\\lbrack k\\rbrack \\right\\rangle} \\right)d\\eta\\lbrack k\\rbrack.} \\\\ \\end{aligned}$$  
(2.123)

In the equalities presented above, *λ*^((*k*)) is the vector of Lagrange multipliers corresponding to the *k*th balance constraint. This vector satisfies the system of equations

  
$$\\begin{array}{r} {\\frac{{\\widetilde{\\mathbf{M}}}\_{k}(\\lambda)}{\\mathcal{W}(\\lambda)} + \\frac{{\\widetilde{\\mathbf{S}}}\_{k}(\\lambda^{(k)})}{\\mathcal{G}\_{k}(\\lambda^{(k)})} = \\mathbf{x}\\lbrack k\\rbrack,\\quad k \\neq k^{-},\\ldots,k^{+};k \\in \\mathcal{K},} \\\\ \\end{array}$$  
(2.124)

where

  
$$\\begin{aligned} & {{\\widetilde{\\mathbf{M}}}\_{k}(\\lambda) = {\\int\_{\\mathcal{F}}\\exp}\\left\\lbrack {- {\\sum\\limits\_{k \\in \\mathcal{K}}\\langle}\\lambda^{(k)},\\mathbb{F}\\left( \\left. \\mathbf{c},Z\_{(k - \\rho)} \\right\\rangle \\right)} \\right\\rbrack\\mathbb{F}\\left( {\\mathbf{c},Z\_{(k - \\rho)}} \\right)d\\mathbf{c}dZ,} \\\\ & {{\\widetilde{\\mathbf{S}}}\_{k}(\\lambda^{(k)}) = {\\int\_{\\mathcal{E}\_{k}}\\exp}\\left( {- \\left\\langle \\lambda^{(k)},\\eta\\lbrack k\\rbrack \\right\\rangle} \\right)\\eta\\lbrack k\\rbrack d\\eta\\lbrack k\\rbrack.} \\\\ \\end{aligned}$$  
(2.125)

**3. Omissions in input and output data**

In this case, the procedures described in the previous paragraphs have to be used sequentially: first, the algorithm (2.121), and then the algorithm (2.106).

The algorithms, applied either separately or sequentially, yield:

*   the entropy-optimal PDFs of parameters of the corresponding models, *P*^(\*)(**a**) and *W*^(\*)(**c**);
    
*   the entropy-optimal PDFs of the measurement noises, *Q*[*k*]^(\*)(*ξ*\[*k*\]) and *G*[*k*]^(\*)(*η*\[*k*\]), where $k = \\overline{1,N};$
    
*   the entropy-optimal PDF of the randomized input sequence, $K\_{k}^{\*}(\\zeta\\lbrack k\\rbrack),\\, k = \\overline{1,N}.$
    

**3. Sampling of optimal PDFs**

Sampling transforms a PDF into an appropriate sequence of random vectors. In the procedure under consideration, this is a way of realizing the ensembles of random vectors on the segments of missing data.

The general method for generating sequences of random vectors with a given PDF was described in \[[36](#refbib.xhtml#r36)\]. It is intended to sample the sequences of the corresponding random-parameter vectors of the RPM-O and RPM-I models and the sequences of the measurement noise vectors, as well as to generate the ensembles of restored data using the Monte Carlo method \[[159](#refbib.xhtml#r159)\].

Some useful characteristics of ensembles are as follows:

*   —the empirical PDFs $\\mathcal{P}\_{k}({\\hat{\\mathbf{v}}}\_{rst}\\lbrack k\\rbrack)$ and $\\mathcal{W}\_{k}({\\hat{\\mathbf{z}}}\_{rst}\\lbrack k\\rbrack)$ for the restored output and input data, respectively;
    
*   —the empirical probability distributions
    
      
    $$\\begin{aligned} {\\mathfrak{P}\_{k}({\\hat{\\mathbf{v}}}\_{rst}^{(i)}\\lbrack k\\rbrack)} & {= {\\sum\\limits\_{j = 1}^{i}\\mathcal{P}\_{k}}({\\hat{\\mathbf{v}}}\_{rst}^{(j)}\\lbrack k\\rbrack)\\quad\\text{(for~the~output~data)}} \\\\ {\\mathfrak{W}\_{k}({\\hat{\\mathbf{z}}}\_{rst}^{(i)}\\lbrack k\\rbrack)} & {= {\\sum\\limits\_{j = 1}^{i}\\mathcal{W}\_{k}}({\\hat{\\mathbf{v}}}\_{rst}^{(j)}\\lbrack k\\rbrack)\\quad\\text{(for~the~input~data)}.} \\\\ \\end{aligned}$$  
    (2.126)
    

The sets of restored data representing the integral characteristics of an ensemble of random trajectories can be used for solving machine learning problems.

*1. Data maximizing the PDFs of parameters and noises* (max-pn)

*   —The restored output data:
    
      
    $$\\begin{aligned} {{\\hat{\\mathbf{y}}}\_{rst}\\lbrack k\\rbrack} & {= \\mathbb{B}(\\mathbf{a}^{\*},X\_{(k - \\rho)}),\\quad\\mathbf{a}^{\*} = \\arg\\max P^{\*}(\\mathbf{a}),} \\\\ {\\xi\_{rst}\\lbrack k\\rbrack} & {= \\arg\\max Q\_{k}^{\*}(\\xi\\lbrack k\\rbrack),} \\\\ {{\\hat{\\mathbf{v}}}\_{rst}\\lbrack k\\rbrack} & {= {\\hat{\\mathbf{y}}}\_{rst}\\lbrack k\\rbrack + \\xi\_{rst}\\lbrack k\\rbrack,\\text{\\quad\\quad}k = \\overline{0,N}.} \\\\ \\end{aligned}$$  
    (2.127)
    
*   —The restored input data:
    
      
    $$\\begin{aligned} {{\\hat{\\mathbf{x}}}\_{rst}\\lbrack k\\rbrack} & {= \\mathbb{F}(\\mathbf{c}^{\*},Z\_{(k - \\rho)}^{\*}),\\quad\\mathbf{c}^{\*} = \\arg\\max W^{\*}(\\mathbf{a}),} \\\\ Z\_{(k - \\rho)}^{\*} & {= \\lbrack\\zeta^{\*}\\lbrack k - \\rho\\rbrack,\\ldots,\\zeta^{\*}\\lbrack k\\rbrack\\rbrack,\\quad\\zeta^{\*}\\lbrack k\\rbrack = \\arg\\max K\_{k}^{\*}(\\zeta\\lbrack k\\rbrack),} \\\\ {\\eta\_{rst}\\lbrack k\\rbrack} & {= \\arg\\max G\_{k}^{\*}(\\eta\\lbrack k\\rbrack),} \\\\ {{\\hat{\\mathbf{z}}}\_{rst}\\lbrack k\\rbrack} & {= {\\hat{\\mathbf{x}}}\_{rst}\\lbrack k\\rbrack + \\eta\_{rst}\\lbrack k\\rbrack,\\text{\\quad\\quad}k = \\overline{0,N}.} \\\\ \\end{aligned}$$  
    (2.128)
    

*2. Data maximizing the empirical PDFs of observed trajectories for $k = \\overline{0,N}$* (max-ePDF)

*   —The restored output data:
    
      
    $$\\begin{array}{r} {{\\check{\\mathbf{v}}}\_{rst}\\lbrack k\\rbrack = \\arg\\max\\mathcal{P}\_{k}({\\hat{\\mathbf{v}}}\_{rst}\\lbrack k\\rbrack),\\text{\\quad\\quad}k = \\overline{0,N}.} \\\\ \\end{array}$$  
    (2.129)
    
*   —The restored input data:
    
      
    $$\\begin{array}{r} {{\\check{\\mathbf{z}}}\_{rst}\\lbrack k\\rbrack = \\arg\\max\\mathcal{W}\_{k}({\\hat{\\mathbf{z}}}\_{rst}\\lbrack k\\rbrack),\\text{\\quad\\quad}k = \\overline{0,N};} \\\\ \\end{array}$$  
    (2.130)
    

*3. Data corresponding to the mean trajectory* (mean)

*   —The restored output data:
    
      
    $$\\begin{array}{r} {{\\overline{\\mathbf{v}}}\_{rst}\\lbrack k\\rbrack = \\frac{1}{M}{\\sum\\limits\_{i = 1}^{M}{\\hat{\\mathbf{v}}}\_{rst}^{(i)}}\\lbrack k\\rbrack,\\text{\\quad\\quad}k = \\overline{0,N}.} \\\\ \\end{array}$$  
    (2.131)
    
*   —The restored input data:
    
      
    $$\\begin{array}{r} {{\\overline{\\mathbf{z}}}\_{rst}\\lbrack k\\rbrack = \\frac{1}{M}{\\sum\\limits\_{i = 1}^{M}{\\hat{\\mathbf{z}}}\_{rst}^{(i)}}\\lbrack k\\rbrack,\\text{\\quad\\quad}k = \\overline{0,N}.} \\\\ \\end{array}$$  
    (2.132)
    
    (Here *M* denotes the number of trajectories in an ensemble.)
    

*4. Data corresponding to the median trajectory* (med)

*   —The restored output data:
    
      
    $$\\begin{array}{r} \\left. {\\hat{\\mathbf{v}}}\_{rst}^{(j^{\*})}\\lbrack k\\rbrack\\Rightarrow{\\sum\\limits\_{j = 1}^{j^{\*}}\\mathfrak{P}\_{k}}({\\hat{\\mathbf{v}}}\_{rst}^{(j)}\\lbrack k\\rbrack) = {\\sum\\limits\_{j = j^{\*} + 1}^{M}\\mathfrak{P}\_{k}}({\\hat{\\mathbf{v}}}\_{rst}^{(j)}\\lbrack k\\rbrack). \\right. \\\\ \\end{array}$$  
    (2.133)
    
*   —The restored input data:
    
      
    $$\\begin{array}{r} \\left. {\\hat{\\mathbf{z}}}\_{rst}^{(j^{\*})}\\lbrack k\\rbrack\\Rightarrow{\\sum\\limits\_{j = 1}^{j^{\*}}\\mathfrak{W}\_{k}}({\\hat{\\mathbf{z}}}\_{rst}^{(j)}\\lbrack k\\rbrack) = {\\sum\\limits\_{j = j^{\*} + 1}^{M}\\mathfrak{W}\_{k}}({\\hat{\\mathbf{z}}}\_{rst}^{(j)}\\lbrack k\\rbrack). \\right. \\\\ \\end{array}$$  
    (2.134)
    
    (Here *M* denotes the number of trajectories in an ensemble.)
    

Useful restored data can be of assistance when solving applied problems.

# CHAPTER 3 DIMENSION REDUCTION METHODS

DOI: [10.1201/9781003306566-3](https://doi.org/10.1201/9781003306566-3)

## 3.1Review of Dimension Reduction Methods

The arrays of problem-oriented data described in the previous sections may contain information of little significance. This hypothesis underlies dimension reduction methods. Although any reduction causes loss of information about a studied object, it is reasonable to consider reduction with “minimum loss.” The experience accumulated by solving different machine learning problems indicates that the dimension reduction problems and the problems solved on resulting reduced data are related to each other. Therefore, there exists no universal efficient approach applicable to any problem. Note that dimension reduction becomes a rather topical problem for RML procedures due to the specific properties of the equations yielding the optimal “randomized” estimates. This feature explains the choice of the reduction methods below.

As a matter of fact, the dimension reduction methods employ one of the three basic ideas as follows. The first idea is related to the matrix that describes data of unspecified origin. By assumption, this matrix has a certain core of smaller dimension that concentrates main information about a studied object. In this case, a reduction tool is the singular decomposition of the data matrix and ordering of its singular values in absolute magnitude.

The second idea is to treat existing data as random, sometimes with additional statistical properties. Then, further analysis is focused on covariance matrix using one of two standard approaches. Following the first approach, one should assign some connectivity threshold for variables and eliminate one of two variables whose coefficient of correlation exceeds this threshold. The second approach is based on the singular decomposition of the covariance matrix.

Finally, the third idea for dimension reduction consists in direct and inverse projection. Direct projection is performed onto a space of smaller dimension (on choice). As the name implies, inverse projection is the same operation back onto the original space, yielding the so-called inverse vector. Naturally enough, the inverse vector differs from the original one. Hence, it is necessary to choose an appropriate functional of distance between the original and inverse vectors to be minimized over corresponding projection operators.

### 3.1.1Singular decomposition method for data matrix

Consider a rectangular data matrix *A* of dimensions (*m* × *s*) and recall some definitions from \[[60](#refbib.xhtml#r60)\]. The left singular vectors $\\overset{\\rightarrow}{u}$ of this matrix *A* are the eigenvectors of the matrix *A**A*^′ of dimensions (*m* × *m*). The right singular vectors $\\overset{\\rightarrow}{u}$ of this matrix *A* are the eigenvectors of the matrix *A*^′*A* of dimensions (*s* × *s*). A nonnegative real value *β* is a singular value of *A* if there exist two unit-length vectors $\\overset{\\rightarrow}{u} \\in R^{m}$ and $\\overset{\\rightarrow}{v} \\in R^{s}$ such that

  
$$\\begin{array}{r} {A\\overset{\\rightarrow}{v} = \\beta\\overset{\\rightarrow}{u},\\text{\\quad\\quad}A^{\\prime}\\overset{\\rightarrow}{u} = \\beta\\overset{\\rightarrow}{v}.} \\\\ \\end{array}$$  
(3.1)

A singular decomposition of the matrix *A* is given by the representation

  
$$\\begin{array}{r} {A = USV^{\\prime},} \\\\ \\end{array}$$  
(3.2)

where the diagonal matrix *S* of dimensions (*m* × *s*) contains the singular values of *A*, whereas the matrices *U* and *V* of dimensions (*m* × *m*) and (*s* × *s*), respectively, are unitary

By this definition of singular decomposition, the matrices *U* and *V* are not unique and hence can be chosen so that the diagonal elements of the matrix *S* have the form

  
$$\\begin{array}{r} {\\beta\_{1} \\geq \\beta\_{2} \\geq \\cdots \\geq \\beta\_{r} > \\beta\_{r + 1} = \\cdots = \\beta\_{m} = 0,} \\\\ \\end{array}$$  
(3.3)

where *r* denotes the rank of the matrix *S*.

The chain of inequalities (3.3) plays a key role in principal component analysis. The first principal component is the one with the maximum singular value (in the current notation, *β*[1]). The second successive component corresponds to the singular value *β*[2], and so on. The last principal component is associated with the last nonzero singular value *β*[*r*] and its index (subscript) coincides with the rank of the matrix *A*.

The singular values are calculated by solving the following problem. Consider an approximate linear representation of the matrix *A* of the form

  
$$\\begin{array}{r} {A = USV^{\\prime} + C.} \\\\ \\end{array}$$  
(3.4)

Minimize

  
$$\\begin{array}{r} {\\varepsilon^{2} = \\text{tr}(CC^{\\prime})} \\\\ \\end{array}$$  
(3.5)

subject to the normalization conditions

  
$$\\begin{array}{r} {U^{\\prime}U = VV^{\\prime} = I.} \\\\ \\end{array}$$  
(3.6)

If the matrix *A* has a rank *r* > min (*m*, *s*), then *C* ≈ 0. The minimum value *r* that satisfies equality (3.2) is the rank of the matrix *A*. To find the left and right singular vectors ${\\overset{\\rightarrow}{u}}\_{k}$, ${\\overset{\\rightarrow}{v}}\_{k}$ for *k* = 1, …, *r*, introduce auxiliary normalized vectors ${\\overset{\\rightarrow}{a}}\_{k},{\\overset{\\rightarrow}{b}}\_{k}$ and define vectors ${\\overset{\\rightarrow}{u}}\_{k}$, ${\\overset{\\rightarrow}{v}}\_{k}$ as

  
$$\\begin{array}{r} {{\\overset{\\rightarrow}{u}}\_{k} = \\frac{{\\overset{\\rightarrow}{a}}\_{k}}{\\|{\\overset{\\rightarrow}{a}}\_{k}\\|},\\text{\\quad\\quad}{\\overset{\\rightarrow}{v}}\_{k} = \\frac{{\\overset{\\rightarrow}{b}}\_{k}}{\\|{\\overset{\\rightarrow}{b}}\_{k}\\|}.} \\\\ \\end{array}$$  
(3.7)

Then the singular value is

  
$$\\begin{array}{r} {\\lambda\_{k} = \\|{\\overset{\\rightarrow}{a}}\_{k}{\\|\\|}{\\overset{\\rightarrow}{b}}\_{k}\\|.} \\\\ \\end{array}$$  
(3.8)

The auxiliary vectors are given by the equalities

  
$$\\begin{array}{r} {{\\overset{\\rightarrow}{a}}\_{k} = \\frac{A\\,{\\overset{\\rightarrow}{b}}\_{k}}{{\\overset{\\rightarrow}{b}}\_{k}\\,{\\overset{\\rightarrow}{b}}\_{k}^{\\prime}},\\quad{\\overset{\\rightarrow}{b}}\_{k + 1} = \\frac{{\\overset{\\rightarrow}{a}}\_{k}^{\\prime}}{{\\overset{\\rightarrow}{a}}\_{k}^{\\prime}\\,{\\overset{\\rightarrow}{a}}\_{k}},\\quad k = 1,2,\\ldots} \\\\ \\end{array}$$  
(3.9)

At step *k* = 1, the row ${\\overset{\\rightarrow}{b}}\_{1}$ of the matrix *A* has the maximum norm. At steps *k* = 2, 3, …, this procedure is iteratively applied to the matrix $A\_{k + 1} = A\_{k} - {\\overset{\\rightarrow}{u}}\_{k}\\lambda\_{k}{\\overset{\\rightarrow}{v}}\_{k}.$ To construct the matrix *Â*[*r*] = *U*[*r*]*S*[*r*]*V*^′, it suffices to calculate only *r* columns of the matrix *U* and *r* rows of the matrix *V*^′.

### 3.1.2Principal component analysis

Apparently, principal component analysis is the most commonly used dimension reduction method for data arrays \[[10](#refbib.xhtml#r10), [84](#refbib.xhtml#r84), [127](#refbib.xhtml#r127)\]. There exist at least three basic versions of this method, namely, data approximation by linear smaller-dimension manifolds; searching for smaller-dimension subspaces with the maximum data spread (variance) in the orthogonal projection onto them; searching for smaller-dimension subspaces with the maximum root-mean-square distance between points in the orthogonal projection onto them. The basic versions involve a data matrix $X = \\lbrack{\\overset{\\rightarrow}{x}}^{(1)},\\ldots,{\\overset{\\rightarrow}{x}}^{(m)}\\rbrack$ whose column vectors ${\\overset{\\rightarrow}{x}}^{(i)}$ have dimension *s*.

To clarify the idea of this method, first consider the case *s* = 2. Consider a data matrix composed of two-dimensional columns whose elements are the measured values of some variables (attributes of interest). Interpret them as points {*x*[1]^((*i*)),*x*[2]^((*i*))} on the plane; see [Fig. 3.1(a)](#chapter3.xhtml#f3_1). Draw a line *AB* so that the *maximum* variation of data occurs along it. The line *AB* is the first principal component. Perform the projection of the initial points on this line and use it as a new coordinate axis ([Fig. 3.1(b)](#chapter3.xhtml#f3_1)). Take the points representing the difference between the initial points and their projections on axis *AB* and again draw a line *CD* so that the maximum variation of these differences occurs along it, as shown in [Fig. 3.1(c)](#chapter3.xhtml#f3_1). The line *CD* is the second principal component and so on.

![Figure 3.1](images/fig3_1.jpg)

[Figure 3.1](#chapter3.xhtml#f3_1b)

In the general multidimensional case, principal component analysis is performed in accordance with the following procedure:

*   identify the center of the existing data set and place the origin (i.e., the zeroth principal component) to this center;
    
*   find the direction of the maximum data variation (the first principal component);
    
*   find the data projections onto the first principal component as well as their variance;
    
*   if the variance is large, find the new principal direction of maximum variations that is orthogonal to the first one, and so on.
    

This procedure allows to replace the initial data matrix *X* of dimensions (*s* × *m*) by two matrices *T* and *P* of dimensions (*s* × *k*) and (*k* × *s*), respectively, where *k* < *m*. This representation is obtained using the new variables

  
$$\\begin{array}{r} {{\\overset{\\rightarrow}{t}}^{\\mspace{2mu}(j)} = {\\overset{\\rightarrow}{p}}^{\\mspace{2mu}(j,1)}{\\overset{\\rightarrow}{x}}^{(1)} + \\cdots + {\\overset{\\rightarrow}{p}}^{\\mspace{2mu}(j,m)}{\\overset{\\rightarrow}{x}}^{(m)},\\quad j = \\overline{1,k},} \\\\ \\end{array}$$  
(3.10)

where ${\\overset{\\rightarrow}{t}}^{\\mspace{2mu}(j)}$ and ${\\overset{\\rightarrow}{p}}^{\\mspace{2mu}(j,i)},\\, i = \\overline{1,m},$ denote the columns of the matrices *T* and *P*, respectively. The new variables (3.10) are called the *principal components*, and the matrix *T* is called the principal component matrix. An important property of the principal components consists in their orthogonality. Therefore, the matrix *T* is not reconfigured as we increase the number of principal components.

With these variables, the matrix *X* can be written as

  
$$\\begin{array}{r} {X = \\hat{X} + E = {\\sum\\limits\_{j = 1}^{k}{\\overset{\\rightarrow}{t}}^{(j)}}{\\lbrack{\\overset{\\rightarrow}{p}}^{(j)}\\rbrack}^{\\prime} + E,\\text{\\quad\\quad}\\hat{X} = T\\, P^{\\prime}.} \\\\ \\end{array}$$  
(3.11)

Here *E* stands for the residue matrix of dimensions (*s* × *m*). The residual error is assessed in terms of some numerical characteristic of the residue matrix, e.g., the relative variance

  
$$\\begin{array}{r} {D = 1 - \\frac{\\sum\\limits\_{j = 1}^{s}{\\sum\\limits\_{i = 1}^{m}e\_{ji}^{2}}}{\\sum\\limits\_{j = 1}^{s}{\\sum\\limits\_{i = 1}^{m}x\_{ji}^{2}}},\\quad e\_{ji} = x\_{ji} - {\\hat{x}}\_{ji}.} \\\\ \\end{array}$$  
(3.12)

There exist many recursive algorithms to calculate the principal components, which are oriented towards the specifics of initial information and employ different data processing methods. First, the matrix *X* is centered, i.e., for each column the average value

  
$$\\begin{array}{r} {{\\overline{x}}\_{j} = \\frac{1}{s}{\\sum\\limits\_{i = 1}^{m}x\_{i}^{(j)}}} \\\\ \\end{array}$$  
(3.13)

and the standard deviation

  
$$\\begin{array}{r} {\\sigma\_{j} = \\frac{1}{s}\\sqrt{\\sum\\limits\_{i = 1}^{m}{(x\_{ji} - {\\overline{x}}\_{j})}^{2}}.} \\\\ \\end{array}$$  
(3.14)

are calculated. The modified data matrix *X̃* that is used to calculate the principal components consists of the elements

  
$$\\begin{array}{r} {{\\widetilde{x}}\_{ij} = \\frac{x\_{ij} - {\\overline{x}}\_{j}}{\\sigma\_{j}}.} \\\\ \\end{array}$$  
(3.15)

The algorithm for searching the principal components includes the following steps.

1.  Choose an initial vector $\\overset{\\rightarrow}{t}$ (3.10).
    
2.  Calculate ${\\overset{\\rightarrow}{p}}^{\\mspace{2mu}\\prime} = \\frac{{\\overset{\\rightarrow}{t}}^{\\mspace{2mu}\\prime}E\_{j}}{{\\overset{\\rightarrow}{t}}^{\\prime}\\overset{\\rightarrow}{t}}.$
    
3.  Calculate $\\overset{\\rightarrow}{p} = \\frac{\\overset{\\rightarrow}{p}}{{({\\overset{\\rightarrow}{p}}^{\\prime}\\overset{\\rightarrow}{p})}^{1/2}}.$
    
4.  Calculate $\\overset{\\rightarrow}{t} = \\frac{E\_{j}\\overset{\\rightarrow}{p}}{{\\overset{\\rightarrow}{p}}^{\\prime}\\overset{\\rightarrow}{p}}.$
    
5.  Find *D* using (3.12) and get back to Step 2.
    

The number of the principal components is defined by comparing the relative variance (3.12) with the admissible error.

As mentioned earlier, the singular decomposition (3.2) of a rectangular matrix and principal component analysis are related to one another. This relation has the form

  
$$\\begin{array}{r} {T = US,\\quad P = V.} \\\\ \\end{array}$$  
(3.16)

Principal component analysis and its modifications were considered in a vast literature, mostly with applications to the problems of classification and regression \[188\].

### 3.1.3Random projection method

Like principal component analysis, dimension reduction by means of random projections involves a linear transformation *f*:ℝ^(*n*)→ℝ^(*k*) of a data matrix and is applied in problems where objects are represented by points of the multidimensional Euclidean space \[[20](#refbib.xhtml#r20)\].

The idea of the random projection method is based on the Johnson–Lindenstrauss lemma \[[83](#refbib.xhtml#r83)\]: for a set *X* of points in a multidimensional space of a high dimension, there exists a subspace of a smaller, albeit rather high, dimension such that projection onto this subspace will save, on average, the relative distances between all points from the given set. The error of transformation is described by a value *ε* ∈ (0, 1):

  
$$\\begin{array}{r} {\\left( {1 - \\varepsilon} \\right)\\left\\| {x\_{1} - x\_{2}} \\right\\|^{2} \\leq \\left\\| {f(x\_{1}) - f(x\_{2})} \\right\\|^{2} \\leq \\left( {1 + \\varepsilon} \\right)\\left\\| {x\_{1} - x\_{2}} \\right\\|^{2}} \\\\ \\end{array}$$  
(3.17)

for all vectors *x*[1], *x*[2] ∈ *X*.

Moreover, the original lemma also gives a lower bound on *k*, i.e., the dimension of the subspace onto which the objects are projected. For example, for a set of *N* points, the value *k* must satisfy the condition

  
$$\\begin{array}{r} {k > \\frac{8\\ln N}{\\varepsilon^{2}}.} \\\\ \\end{array}$$  
(3.18)

In other words, the minimum possible dimension of the subspace for projection does not depend on the dimension of the original space, but depends only on the number of projected objects and the error of transformation. In various special cases, the lower bound on the value *k* was refined in \[[82](#refbib.xhtml#r82), [86](#refbib.xhtml#r86)\].

Consider a linear transformation *f*:ℝ^(*n*)→ℝ^(*k*) for projecting objects from a set *X*. It is defined by a rectangular matrix *R* of dimensions \[*k* × *n*\] (*k* <  < *n*) and has the form

  
$$\\begin{array}{r} {X\_{k \\times N}^{RP} = R\_{k \\times n}X\_{n \\times N}.} \\\\ \\end{array}$$  
(3.19)

As it turned out, the elements of the matrix *R* for such a transformation can consist of random variables, which makes the projection random. In early works devoted to the random projection method \[[30](#refbib.xhtml#r30), [76](#refbib.xhtml#r76), [108](#refbib.xhtml#r108)\], it was proposed to use random variables with the standard Gaussian distribution *N*(0, 1), and to construct the matrix *R* so that its row vectors are orthogonal and have unit length.

Later in \[[8](#refbib.xhtml#r8)\], it was demonstrated that the matrix *R* can be obtained using the uniform distribution, under certain constraints dictated by storing information in databases, due to integer calculations. In this case, it was suggested to compose the matrix *R* from random elements *r*[*i**j*] of the form

  
$$\\begin{array}{r} {r\_{ij} = \\sqrt{3} \\times \\left\\{ \\begin{aligned} {+ 1} & {\\text{with~probability~}\\frac{1}{6},} \\\\ 0 & {\\text{with~probability~}\\frac{2}{3},} \\\\ {- 1} & {\\text{with~probability~}\\frac{1}{6}.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(3.20)

Thus, for calculating the projection *X*^(*R**P*), it is necessary to multiply the matrices *R* and *X*, and this transformation has the complexity 𝒪(*k**n**N*). In principal component analysis, the matrix for projection is square with dimensions \[*n* × *n*\], and the transformation to projections has the complexity 𝒪(*n*²*N*). Hence, for dimensionality reduction, the random projection method is preferable to principal component analysis in terns of computational efficiency.

Also, note the existing studies to speed up the transformation to projections. One line of research is focused on sparse matrices: as it was shown in \[20\], if the data matrix *X* has at most *c* nonzero components in each column, then the complexity of transformation is reduced to 𝒪(*c**k**N*). The influence of data sparsity on the efficiency of the random projection method was studied in the papers \[[38](#refbib.xhtml#r38), [87](#refbib.xhtml#r87)\]. Another approach to accelerating projection is based on the Fast Johnson–Lindenstrauss Transform (FJLT) \[[9](#refbib.xhtml#r9)\], a randomized Fourier transform.

The range of possible applications of the random projection method for dimension reduction includes a wide class of problems with multidimensional data. Since the relative distances between different objects of a given set are preserved in the smaller dimension space, the structure of this set is also preserved, which is especially important when dividing objects into groups, e.g., in classification and clustering. Therefore, random projections become an effective dimension reduction solution in metric data analysis methods, such as the *k*\-Nearest Neighbor (kNN) for clustering \[30\], support vector machine (SVM) for classification \[[27](#refbib.xhtml#r27)\], and the least squares (LS) method for regression \[[116](#refbib.xhtml#r116)\].

Random projections turn out to be especially effective when dealing with large collections of multidimensional sparse data, such as images, text, audio and video data, etc. In the field of signal processing, a separate line of research devoted to the use of random projections for data analysis and restoration is called Compressed Sensing; for example, see \[[29](#refbib.xhtml#r29), [46](#refbib.xhtml#r46)\].

Regardless of the field of application, the nature and dimension of the original data represented by a set of points in a multidimensional space, the use of random projections allows reducing the dimension while preserving the data structure. Moreover, the random projection method is easily interpreted and does not require significant computing resources, even in the case of high and ultrahigh-dimensional data, in contrast to alternative dimension reduction methods such as PCA and SVD.

However, note that random projections are intended only for the problems in which analysis and calculations are performed on data of reduced dimension, but the data are not used for visualization or restoration. For example, in the case of images, dimension reduction with random projections can lead to visual degradation of the image, for both the human eye and computer vision systems.

### 3.1.4Direct and inverse projection

Consider the space *R*^(*N**M*) of all real matrices *A*[(*N* × *M*)] whose elements take random values.

The transition from the original space *R*^(*N**M*) to the smaller-dimension one *R*^(*N**m*) causes the losses of information contained in the former's elements. For estimating these losses, it is necessary to return to the original space by means of *inverse projection*: *R*^(*N**m*)⇒*R*^(*N**M*). This operation is performed using a projector matrix *J*[(*m* × *M*)], which gives the matrix *X*[(*N* × *M*)] = *D*[(*N* × *m*)]*J*[(*m* × *M*)] ∈ *R*^(*N**M*). The matrices *X*[(*N* × *M*)] and *A*[(*N* × *M*)] are elements of the same space. Hence, the quality of compression of the original matrix can be estimated in terms of an appropriate criterion.

In the sequel, the quality of data compression, which depends on the projector matrices *S*[(*N* × *m*)] and *J*[(*m* × *M*)], will be estimated in entropy terms. More specifically, introduce the information entropy \[[139](#refbib.xhtml#r139)\] of a matrix *X*[(*N* × *M*)] with respect to a matrix *A*[(*N* × *M*)],

  
$$\\begin{array}{r} \\left. H(X\\, \\middle| \\, A) = - {\\sum\\limits\_{i = 1}^{N}{\\sum\\limits\_{j = 1}^{M}x\_{ij}}}\\ln\\frac{x\_{ij}}{a\_{ij}} = tr\\left( {X^{\\intercal}Y} \\right), \\right. \\\\ \\end{array}$$  
(3.21)

where *tr* denotes the matrix trace and *Y* is a matrix of dimensions (*N* × *M*) consisting of the elements

  
$$\\begin{array}{r} {y\_{ij} = \\ln\\frac{x\_{ij}}{a\_{ij}}.} \\\\ \\end{array}$$  
(3.22)

Hereinafter, this entropy will be called *the information cross-entropy*\[[158](#refbib.xhtml#r158)\]. The direct-inverse projection method described above is the core of the compression method of random data matrices. Consider a nonnegative data matrix *U* of dimensions (*m* × *s*). It is required to compress the matrix to a matrix *Z* of dimensions (*n* × *r*), where *r* < *s* and *n* < *m*. This problem will be solved sequentially, in two stages as follows. First, reduce the matrix *U*[(*m* × *s*)] to a matrix *Y*[(*m* × *r*)], and then compress the latter to a matrix *Z*[(*n* × *r*)]. The approach presented below will be called *the entropy dimension reduction (EDR) method*.

*Stage 1* Introduce a matrix *Q*[(*s* × *r*)] and perform direct projection for obtaining the column-compressed matrix

  
$$\\begin{array}{r} {Y\_{(m \\times r)} = U\_{(m \\times s)}Q\_{(s \\times r)}.} \\\\ \\end{array}$$  
(3.23)

Next, introduce a matrix *T*[(*r* × *s*)] and perform inverse projection, which yields the matrix

  
$$\\begin{array}{r} {X\_{(m \\times s)} = U\_{(m \\times s)}Q\_{(s \\times r)}T\_{(r \\times s)}.} \\\\ \\end{array}$$  
(3.24)

The matrix *X*[(*m* × *s*)] has the same dimension as the original matrix *U*[(*m* × *s*)] and characterizes the effect (losses) of direct and inverse projections in Stage 1.

The reduction of a data matrix is accompanied by the losses of information contained in it or by an increase of the relative information entropy \[139\]. For Stage 1 of this method, the information cross-entropy of a matrix *X*[(*m* × *s*)] with a fixed original matrix *U*[(*m* × *s*)] is given by

  
$$\\begin{aligned} \\left. H\_{1}(X\\, \\middle| \\, U) \\right. & \\left. = - {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}x\_{ij}}}(Q,T\\, \\middle| \\, U)\\ln\\frac{\\left. x\_{ij}(Q,T\\, \\middle| \\, U) \\right.}{u\_{ij}} = \\right. \\\\ & \\left. \\quad = H\_{1}(Q,T\\, \\middle| \\, U)\\Rightarrow\\max\_{(Q,T) \\geq 0}, \\right. \\\\ \\end{aligned}$$  
(3.25)

where, according to (3.24),

  
$$\\begin{array}{r} \\left. x\_{ij}(Q,T\\, \\middle| \\, U) = {\\sum\\limits\_{\\mu = 1}^{r}{\\sum\\limits\_{\\nu = 1}^{s}t\_{\\mu,j}}}q\_{\\nu,\\mu}u\_{i\\nu}. \\right. \\\\ \\end{array}$$  
(3.26)

The maximization of the function (3.1.4) finally yields the entropy-optimal projector matrix *Q*[(*s* × *r*)]^(\*) and the compressed first-stage matrix

  
$$\\begin{array}{r} {Y\_{(m \\times r)}^{\*} = U\_{(m \\times s)}Q\_{(s \\times r)}^{\*}.} \\\\ \\end{array}$$  
(3.27)

*Stage 2* The second-stage data matrix *Y*[(*m* × *r*)] has a reduced number *r* < *s* of columns. It is required to compress this matrix to a given number *n* < *m* of rows. Introduce matrices *B*[(*n* × *m*)] and *A*[(*m* × *n*)] for performing the direct and inverse projection operations, respectively, by analogy with Stage 1:

  
$$\\begin{array}{r} {Z\_{(n \\times r)} = B\_{(n \\times m)}Y\_{(m \\times r)},\\text{\\quad\\quad}G\_{(m \\times r)} = A\_{(m \\times n)}Z\_{(n \\times r)}.} \\\\ \\end{array}$$  
(3.28)

The matrix *G*[(*m* × *r*)] has the same dimension as the original second-stage matrix *Y*[(*m* × *r*)] and characterizes the effect (losses) of direct and inverse projections in Stage 2. These losses are estimated by the information cross-entropy

  
$$\\begin{aligned} \\left. H\_{2}(G\\, \\middle| \\, Y^{\*}) \\right. & \\left. = - {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}g\_{ij}}}(B,A\\, \\middle| \\, Y)\\ln\\frac{\\left. g\_{ij}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{y\_{ij}} = \\right. \\\\ & \\left. \\quad H\_{2}(B,A\\, \\middle| \\, Y^{\*})\\Rightarrow\\max\_{(B,A) \\geq 0}, \\right. \\\\ \\end{aligned}$$  
(3.29)

where

  
$$\\begin{array}{r} \\left. g\_{ij}(B,A\\, \\middle| \\, Y^{\*}) = {\\sum\\limits\_{\\beta = 1}^{n}{\\sum\\limits\_{\\alpha = 1}^{m}a\_{i,\\beta}}}b\_{\\beta,\\alpha}y\_{\\alpha,j}^{\*} \\right. \\\\ \\end{array}$$  
(3.30)

and

  
$$\\begin{array}{r} {y\_{\\alpha,j}^{\*} = {\\sum\\limits\_{eta = 1}^{s}u\_{\\alpha,\\eta}}q\_{\\eta,j}^{\*}.} \\\\ \\end{array}$$  
(3.31)

## 3.2Entropy Optimization of Sequential Procedure

The first stage of the sequential procedure is to determine the optimal elements of the nonnegative matrices *Q* and *T*:

  
$$\\begin{array}{r} \\left. (Q^{\*},T^{\*}) = \\arg\\max\_{(Q,T) \\geq 0}H\_{1}(Q,T\\, \\middle| \\, U). \\right. \\\\ \\end{array}$$  
(3.32)

This problem will be solved numerically using an iterative algorithm based on projected gradient descent, which represents a combination of the standard gradient descent method and the truncation of all negative elements.

### 3.2.1Optimality conditions and algorithm

The gradient of the function *H*[1](*Q*,*T* | *U*) with respect to the elements of the matrices *Q* and *T* has the components

  
$$\\begin{aligned} \\frac{\\left. \\partial H(Q,T\\, \\middle| \\, U) \\right.}{\\partial q\_{\\nu,\\mu}} & {= {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\left. \\partial h\_{ij}(Q,T\\, \\middle| \\, U) \\right.}{\\partial x\_{ij}}}}\\frac{\\left. \\partial x\_{ij}(Q,T\\, \\middle| \\, U) \\right.}{\\partial q\_{\\nu,\\mu}},} \\\\ & {\\quad\\nu = \\overline{1,s},\\,\\mu = \\overline{1,r},} \\\\ \\end{aligned}$$  
(3.33)

  
$$\\begin{aligned} \\frac{\\left. \\partial H(Q,T\\, \\middle| \\, U) \\right.}{\\partial t\_{\\mu,j}} & {= {\\sum\\limits\_{i = 1}^{s}{\\sum\\limits\_{j = 1}^{m}\\frac{\\left. \\partial h\_{ij}(Q,T\\, \\middle| \\, U) \\right.}{\\partial x\_{ij}}}}\\frac{\\left. \\partial x\_{ij}(Q,T\\, \\middle| \\, U) \\right.}{\\partial t\_{\\mu,j}},} \\\\ & {\\quad\\mu = \\overline{1,r},\\, j = \\overline{1,s},} \\\\ \\end{aligned}$$  
(3.34)

where

  
$$\\begin{aligned} & \\left. h\_{ij}(T,Q\\, \\middle| \\, X) = x\_{ij}\\ln\\frac{x\_{ij}}{u\_{ij}}, \\right. \\\\ & {\\frac{\\left. \\partial h\_{ij}(T,Q\\, \\middle| \\, X) \\right.}{\\partial x\_{ij}} = \\ln\\frac{x\_{ij}}{u\_{ij}} + 1,\\text{\\quad\\quad}i = \\overline{1,m},\\, j = \\overline{1,s};} \\\\ \\end{aligned}$$  
(3.35)

  
$$\\begin{aligned} \\frac{\\left. \\partial x\_{ij}((Q,T\\, \\middle| \\, U)) \\right.}{\\partial q\_{\\nu,\\mu}} & {= t\_{\\mu,j}\\, u\_{i,\\nu},\\text{\\quad\\quad}\\nu = \\overline{1,s},\\mu = \\overline{1,r};} \\\\ \\frac{\\left. \\partial x\_{ij}((Q,T\\, \\middle| \\, U)) \\right.}{\\partial t\_{\\mu,j}} & {= {\\sum\\limits\_{\\nu = 1}^{s}q\_{\\nu,\\mu}}u\_{i,\\nu},\\text{\\quad\\quad}\\mu = \\overline{1,r};} \\\\ i & {= \\overline{1,m},\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(3.36)

Perform the *vectorization* of the matrices *Q* and *T* (see \[[115](#refbib.xhtml#r115)\]) to obtain the corresponding vectors **q** and **t**. Denote by ∇[*Q*](**q**, **t**) the gradient of the information cross-entropy functional *H*(*Q*,*T* | *U*) with the components (3.2.2), and by ∇[*T*](**q**, **t**) the gradient of the information cross-entropy functional *H*(*Q*,*T* | *U*) with the components (3.33–3.36).

The algorithm **max *H*[1]** has the following structure.

*   *a). Initial step:*
    
      
    $$\\begin{array}{r} {\\mathbf{q}^{0} > \\mathbf{0},\\quad\\mathbf{t}^{0} > \\mathbf{0}.} \\\\ \\end{array}$$  
    
*   *b). nth iterative step:*
    
      
    $$\\begin{array}{r} {X^{n} = U\\, Q^{n}\\, T^{n},} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. H(Q^{n},T^{n}\\, \\middle| \\, U) = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}x\_{ij}^{n}}}\\ln\\frac{x\_{ij}^{n}}{u\_{ij}} = H^{n}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{q}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{q}^{n} + \\gamma\_{\\mathbf{q}}\\nabla\_{Q}(\\mathbf{q}^{n},\\mathbf{t}^{n})\\text{if}\\,\\mathbf{q}^{(n + 1)} \\geq \\mathbf{0},} \\\\ {\\mathbf{q}^{n}\\text{if}\\,\\mathbf{q}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{q}^{(n + 1)}\\Rightarrow Q^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{t}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{t}^{n} + \\gamma\_{\\mathbf{t}}\\nabla\_{T}(\\mathbf{q}^{n},\\mathbf{t}^{n})\\text{if}\\,\\mathbf{t} \\geq \\mathbf{0},} \\\\ {\\mathbf{t}^{n}\\text{if}\\,\\mathbf{t}^{(n + 1)} < \\mathbf{0}.} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{t}^{(n + 1)}\\Rightarrow T^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {X^{(n + 1)} = U\\, Q^{(n + 1)}\\, T^{(n + 1)};} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. H(Q^{(n + 1)},T^{(n + 1)}\\, \\middle| \\, U) = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}x\_{ij}^{(n + 1)}}}\\ln\\frac{x\_{ij}^{(n + 1)}}{u\_{ij}} = H^{(n + 1)}. \\right. \\\\ \\end{array}$$  
    
*   *c). Stopping condition:*
    
      
    $$\\begin{array}{r} {\\text{If}\\,\\, H^{(n + 1)} - H^{(n)} \\leq \\delta,\\,\\text{then}\\, STOP.} \\\\ \\end{array}$$  
    

### 3.2.2Approximation of information cross-entropy functional

In some cases, the elements of the reduced matrix *Q* can be determined with sufficient accuracy using the logarithmic function approximation in the neighborhood of a point *x*[0] = *a*, where *a* ≥ *a*[*m**i**n*]:

  
$$\\begin{array}{r} {\\ln x < \\ln a + \\frac{1}{a\_{min}}(x - a).} \\\\ \\end{array}$$  
(3.37)

For *a* = *x*[*i**j*], this formula gives the following approximate expression for the information cross-entropy functional:

  
$$\\begin{aligned} \\left. H\_{1}(Q,T\\, \\middle| \\, U) \\approx \\sum\_{i = 1}^{s}\\sum\_{j = 1}^{m} \\right. & {\\left\\lbrack x\_{ij}^{2}(Q,T\\, \\middle| \\, U) - x\_{ij}(Q,T\\, \\middle| \\, U)u\_{ij} \\right\\rbrack =} \\\\ & \\left. \\widetilde{H}(Q,T\\, \\middle| \\, U). \\right. \\\\ \\end{aligned}$$  
(3.38)

This equality can be written in the matrix form

![](images/math3_159.jpg)

where ⌈*A*, *B*⌋ denotes the Frobenius inner product \[115\],

![](images/math3_161.jpg)

The elements of the matrices *Q* and *T* will be found by minimizing the functional *H̃*[1](*Q*,*T* | *U*) on the set of all nonnegative matrices *Q* and *T* under a fixed data matrix *U*, i.e.,

  
$$\\begin{array}{r} \\left. ({\\widetilde{Q}}^{\*},{\\widetilde{T}}^{\*}) = \\arg\\min\_{(Q,T) \\geq 0}{\\widetilde{H}}\_{1}(Q,T\\, \\middle| \\, U). \\right. \\\\ \\end{array}$$  
(3.41)

This problem is solved by an algorithm involving the components of the gradient of the functional *H̃*[1](*Q*,*T* | *U*) with respect to the matrices *Q* and *T*.

Using the matrix differentiation rules described above, derive the following expressions for the gradients of the functional *H̃*[1](*Q*,*T* | *U*) (3.41):

  
$$\\begin{array}{r} {\\bigtriangleup\_{Q}(Q,T) = \\frac{\\left. \\partial{\\widetilde{H}}\_{1}(Q,T\\, \\middle| \\, U) \\right.}{\\partial X}\\frac{\\partial X}{\\partial Q} = 2TPQT - TP,} \\\\ \\end{array}$$  
(3.42)

  
$$\\begin{array}{r} {\\bigtriangleup\_{T}(Q,T) = \\frac{\\left. \\partial{\\widetilde{H}}\_{1}(Q,T\\, \\middle| \\, U) \\right.}{\\partial X}\\frac{\\partial X}{\\partial T} = 2Q^{\\intercal}PQT - Q^{\\intercal}P,} \\\\ \\end{array}$$  
(3.43)

where *P* = *X**X*^⊺ and △[*Q*](*Q*, *T*) and △[*T*](*Q*, *T*) mean the gradients with respect to the matrices *Q* and *T*, respectively. According to (3.42, 3.43), the gradients of the function *H̃*(*Q*,*T* | *U*) with respect to the matrices *Q* and *T* are matrices of dimensions (*s* × *r*).

For maximizing the functional *H̃*[1](*Q*,*T* | *U*), apply gradient descent with the nonnegativity check of the matrices *U* and *T*.

The algorithm **max *H̃*[1]** has the following structure.

*   *a) Initial step:*
    
      
    $$\\begin{array}{r} {T^{0} > 0,\\quad Q^{0} > 0.} \\\\ \\end{array}$$  
    
*   *b) nth iterative step:*
    
      
    $$\\begin{array}{r} {X^{n} = U\\, Q^{n}\\, T^{n},} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. H(Q^{n},T^{n}\\, \\middle| \\, U) = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}x\_{ij}^{n}}}\\ln\\frac{x\_{ij}^{n}}{u\_{ij}} = H^{n}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {Q^{(n + 1)} = \\left\\{ \\begin{aligned} \\left. Q^{n} + \\gamma\_{Q} \\bigtriangleup\_{Q}(\\widetilde{H}(Q^{n},T^{n}\\, \\middle| \\, U) \\geq 0 \\right. & {\\text{if~}Q^{(n + 1)} \\geq 0,} \\\\ Q^{n} & {\\text{if~}Q^{(n + 1)} < 0;} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {T^{(n + 1)} = \\left\\{ \\begin{aligned} \\left. T^{n} + \\gamma\_{T} \\bigtriangleup\_{T}(\\widetilde{H}(Q^{n},T^{n}\\, \\middle| \\, U) \\geq 0 \\right. & {\\text{if~}T^{(n + 1)} \\geq 0,} \\\\ T^{n} & {\\text{if~}T^{(n + 1)} < 0;} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {X^{(n + 1)} = U\\, Q^{(n + 1)}\\, T^{(n + 1)};} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. H(Q^{(n + 1)},T^{(n + 1)}\\, \\middle| \\, U) = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}x\_{ij}^{(n + 1)}}}\\ln\\frac{x\_{ij}^{(n + 1)}}{u\_{ij}} = H^{(n + 1)}. \\right. \\\\ \\end{array}$$  
    
*   *c) Stopping condition:*
    
      
    $$\\begin{array}{r} {\\text{If}\\,\\, H^{(n + 1)} - H^{n} \\leq \\delta,\\,\\,\\text{then}\\, STOP.} \\\\ \\end{array}$$  
    

The algorithm **max *H*[1]** or **max *H̃*[1]** yields the entropy-optimal projector matrix *Q*[(*s* × *r*)]^(\*). Hence, it is possible to determine the matrix *Y*[(*m* × *r*)]^(\*) (1.5) for passing to the second stage of the compression procedure of the matrix *U*, which is characterized by the projector matrices *B*[(*n* × *m*)] and *A*[(*m* × *n*)].

The optimal elements of the nonnegative matrices *B* and *A* are given by

  
$$\\begin{array}{r} \\left. (B^{\*},A^{\*}) = \\arg\\max\_{(B,A) \\geq 0}H\_{2}(B,A\\, \\middle| \\, Y^{\*}). \\right. \\\\ \\end{array}$$  
(3.44)

By analogy with Stage 1, this problem will be solved using the iterative algorithm based on projected gradient descent (a combination of gradient descent and the truncation of all negative elements).

The gradient of the function *H*[2](*B*,*A* | *Y*^(\*)) with respect to the elements of the matrices *B* and *A* has the components

  
$$\\begin{aligned} \\frac{\\left. \\partial H\_{2}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{\\partial a\_{i,\\beta}} & {= {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}\\frac{\\left. \\partial s\_{ij}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{\\partial g\_{ij}}}}\\frac{\\left. \\partial g\_{ij}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{\\partial a\_{i,\\beta}},} \\\\ & {\\quad i = \\overline{1,n},\\, j = \\overline{1,r},\\,\\beta = \\overline{1,n},} \\\\ \\end{aligned}$$  
(3.45)

  
$$\\begin{aligned} \\frac{\\left. \\partial H\_{2}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{\\partial b\_{\\beta,\\alpha}} & {= {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}\\frac{\\left. \\partial s\_{ij}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{\\partial g\_{ij}}}}\\frac{\\left. \\partial g\_{ij}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{\\partial b\_{\\beta,\\alpha}},} \\\\ {i =} & {\\overline{1,n},\\, j = \\overline{1,r},\\,\\beta = \\overline{1,n},\\,\\alpha = \\overline{1,m},} \\\\ \\end{aligned}$$  
(3.46)

where

  
$$\\begin{array}{r} {\\frac{\\left. \\partial s\_{ij}(B,A\\, \\middle| \\, Y^{\*}) \\right.}{\\partial g\_{ij}} = \\ln\\frac{g\_{ij}}{y\_{ij}^{\*}} + 1,\\text{\\quad\\quad}i = \\overline{1,n},\\, j = \\overline{1,r};} \\\\ \\end{array}$$  
(3.47)

  
$$\\begin{aligned} \\frac{\\left. \\partial g\_{ij}((B,A\\, \\middle| \\, Y^{\*})) \\right.}{\\partial a\_{i,\\beta}} & {= {\\sum\\limits\_{\\alpha = 1}^{m}b\_{\\beta,\\alpha}}y\_{\\alpha,j}^{\*},\\text{\\quad\\quad}\\beta = \\overline{1,n};} \\\\ \\frac{\\left. \\partial g\_{ij}((B,A\\, \\middle| \\, Y^{\*})) \\right.}{\\partial b\_{\\beta,\\alpha}} & {= a\_{i,\\beta}y\_{\\alpha,j}^{\*},\\text{\\quad\\quad}\\beta = \\overline{1,n},\\alpha = \\overline{1,m};} \\\\ i & {= \\overline{1,m},\\quad j = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(3.48)

Perform the *vectorization* of the matrices *B* and *A*, and introduce the corresponding vectors **b** and **a**. Denote by ∇[*B*](**b**, **a**) the gradient of the relative information entropy *H*[2](*B*,*A* | *Y*^(\*)) with the components (3.46–3.48), and by ∇[*A*](**q**, **t**) the gradient of the relative entropy functional *H*[2](*B*,*A* | *Y*^(\*)) with the components (3.48).

The algorithm **max *H*[2]** has the following structure.

*   *a) Initial step:*
    
      
    $$\\begin{array}{r} {\\mathbf{b}^{0} > \\mathbf{0},\\quad\\mathbf{a}^{0} > \\mathbf{0}.} \\\\ \\end{array}$$  
    
*   *b) nth iterative step:*
    
      
    $$\\begin{array}{r} {G^{n} = A^{n}B^{n}Y^{\*},} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. H(B^{n},A^{n}\\, \\middle| \\, Y^{\*}) = {\\sum\\limits\_{i = 1}^{n}{\\sum\\limits\_{j = 1}^{r}g\_{ij}^{n}}}\\ln\\frac{g\_{ij}^{n}}{y\_{ij}^{\*}} = H^{n}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{b}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{b}^{n} + \\gamma\_{\\mathbf{b}}\\nabla\_{B}(\\mathbf{b}^{n},\\mathbf{a}^{n})\\text{if}\\,\\mathbf{b}^{(n + 1)} \\geq \\mathbf{0},} \\\\ {\\mathbf{b}^{n}\\text{if}\\,\\mathbf{b}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{b}^{(n + 1)}\\Rightarrow Q^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{a}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{a}^{n} + \\gamma\_{\\mathbf{a}}\\nabla\_{A}(\\mathbf{b}^{n},\\mathbf{a}^{n})\\text{if}\\,\\mathbf{a} \\geq \\mathbf{0},} \\\\ {\\mathbf{a}^{n}\\text{if}\\,\\mathbf{a}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{a}^{(n + 1)}\\Rightarrow A^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {G^{(n + 1)} = A^{(n + 1)}B^{(n + 1)}Y^{\*};} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. H(B^{(n + 1)},A^{(n + 1)}\\, \\middle| \\, Y^{\*}) = {\\sum\\limits\_{i = 1}^{n}{\\sum\\limits\_{j = 1}^{r}g\_{ij}^{(n + 1)}}}\\ln\\frac{g\_{ij}^{(n + 1)}}{y\_{ij}^{\*}} = H^{(n + 1)}. \\right. \\\\ \\end{array}$$  
    
*   *c) Stopping condition:*
    
      
    $$\\begin{array}{r} {\\text{If}\\,\\, H^{(n + 1)} - H^{(n)} \\leq \\delta,\\,\\text{then}\\, STOP.} \\\\ \\end{array}$$  
    

## 3.3Entropy Optimization of Parallel Procedure

### 3.3.1Definition and structure

The parallel implementation of the direct-inverse projection procedure leads to the matrix equalities

  
$$\\begin{array}{r} {U\_{(m \\times s)}Q\_{s \\times r} = Y\_{(m \\times r)},\\quad B\_{(n \\times m)}Y\_{(m \\times r)} = Z\_{(n \\times r)},} \\\\ {Z\_{(n \\times r)}W\_{(r \\times s)} = D\_{(n \\times s)},\\quad E\_{(m \\times n)}D\_{(n \\times s)} = X\_{(m \\times s)}.} \\\\ \\end{array}$$  
(3.49)

The first chain in these formulas, related to the direct projection with a matrix *Q*[(*s* × *r*)] and the inverse projection with a matrix *B*[(*n* × *m*)], yields a reduced matrix *Z*[(*n* × *r*)]. The second chain, related to the direct projection with a matrix *W*[(*r* × *s*)] and the inverse projection with a matrix *E*[(*m* × *n*)], yields a matrix *X*[(*m* × *s*)].

From equalities (3.49), it follows that

  
$$\\begin{array}{r} {X\_{(m \\times s)} = E\_{(m \\times n)}\\left\\{ {\\left\\lbrack {B\_{(n \\times m)}\\left( {U\_{(m \\times s)}Q\_{(s \\times r)}} \\right)} \\right\\rbrack W\_{(r \\times s)}} \\right\\}.} \\\\ \\end{array}$$  
(3.50)

Here the round, square and curly brackets indicate the sequence of the projection operations. The elements of the matrix *X*[(*m* × *s*)] have the form

  
$$\\begin{array}{r} {x\_{ij} = {\\sum\\limits\_{\\mu = 1}^{n}e\_{i,\\mu}}{\\sum\\limits\_{\\nu = 1}^{r}w\_{\\nu,j}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},\\text{\\quad\\quad}i = \\overline{1,m},\\, j = \\overline{1,s}.} \\\\ \\end{array}$$  
(3.51)

### 3.3.2Optimality conditions and algorithm

For measuring the deviation of the transformed matrix *X*[(*m* × *s*)] from the original one *U*[(*m* × *s*)], choose *the information cross-entropy*

  
$$\\begin{array}{r} \\left. \\mathcal{H}(X\\, \\middle| \\, U) = - {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}s\_{ij}}}(X\\, \\middle| \\, U), \\right. \\\\ \\end{array}$$  
(3.52)

where

  
$$\\begin{array}{r} {s\_{ij} = x\_{ij}\\ln\\frac{x\_{ij}}{u\_{ij}}.} \\\\ \\end{array}$$  
(3.53)

Due to (3.51), the information cross-entropy (3.52) is a scalar function of the matrices (*Q*, *B*, *W*, *E*) ≥ 0, i.e.,

  
$$\\begin{array}{r} {\\mathcal{H} = \\mathcal{H}(Q,B,W,E).} \\\\ \\end{array}$$  
(3.54)

The optimal elements of the matrices are obtained by maximizing the function ℋ:

  
$$\\begin{array}{r} {(Q^{\*},B^{\*},W^{\*},E^{\*}) = \\arg\\max\_{(Q,B,W,E) \\geq 0}\\mathcal{H}(Q,B,W,E).} \\\\ \\end{array}$$  
(3.55)

This problem will be solved using the coordinate-wise scheme of projected gradient descent.

In the parallel procedure, there are a pair of matrices (*Q*, *B*) for reducing the original matrix *U* with respect to the first variable (*r* < *s*) and a pair of matrices (*W*, *E*) for compressing the matrix *U* with respect to the second variable (*n* < *m*). Each iterative step in the coordinate-wise scheme of projected gradient descent consists of two sub-steps, related to iterations over the (*Q*, *B*)\-gradients and over the (*W*, *E*)\-gradients, respectively.

According to (3.51–3.53), the gradient of the function ℋ(*Q*, *B*, *W*, *E*) has the components

  
$$\\begin{array}{r} {\\frac{\\partial\\mathcal{H}}{\\partial q\_{\\alpha,\\nu}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial q\_{\\alpha,\\nu}},} \\\\ {\\frac{\\partial\\mathcal{H}}{\\partial b\_{\\mu,\\beta}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial b\_{\\mu,\\beta}},} \\\\ {\\frac{\\partial\\mathcal{H}}{\\partial w\_{\\nu,j}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial w\_{\\nu,j}},} \\\\ {\\frac{\\partial\\mathcal{H}}{\\partial e\_{i,\\mu}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial e\_{i,\\mu}},} \\\\ \\end{array}$$  
(3.56)

where

  
$$\\begin{aligned} & {\\frac{\\partial s\_{ij}}{\\partial x\_{ij}} = \\ln\\frac{x\_{ij}}{u\_{ij}} + 1,} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial q\_{\\alpha,\\nu}} = w\_{\\nu,j}{\\sum\\limits\_{\\mu = 1}^{n}e\_{i,\\mu}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}u\_{\\beta,\\alpha},\\text{\\quad\\quad}\\alpha = \\overline{1,s},\\,\\nu = \\overline{1,r};} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial b\_{\\mu,\\beta}} = e\_{i,\\mu}{\\sum\\limits\_{\\nu = 1}^{r}w\_{\\nu,j}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},\\text{\\quad\\quad}\\mu = \\overline{1,n},\\,\\beta = \\overline{1,s};} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial w\_{\\nu,j}} = {\\sum\\limits\_{\\mu = 1}^{n}e\_{i,\\mu}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial e\_{i,\\mu}} = {\\sum\\limits\_{\\nu = 1}^{r}w\_{\\nu,j}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},\\text{\\quad\\quad}\\mu = \\overline{1,n}.} \\\\ \\end{aligned}$$  
(3.57)

Applying *matrix vectorization*, pass to the corresponding vectors **q**, **b**, **w** and **e**. Denote by ∇[**q**], ∇[**b**], ∇[**w**] and ∇[**e**] the components of the gradient with respect to these vectors.

The algorithm **max ℋ** has the following structure.

*   *a) Initial step:*
    
      
    $$\\begin{array}{r} {\\mathbf{q}^{0} > \\mathbf{0},\\quad\\mathbf{b}^{0} > \\mathbf{0},\\quad\\mathbf{w}^{0} > 0,\\quad\\mathbf{e}^{0} > 0.} \\\\ \\end{array}$$  
    
*   *b) nth iterative step:*
    
      
    $$\\begin{array}{r} {X^{n} = E^{n}\\left\\{ {\\left\\lbrack {B^{n}\\left( {UQ^{n}} \\right)} \\right\\rbrack W^{n}} \\right\\},} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathcal{H}^{n} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}x\_{ij}^{n}}}\\ln\\frac{x\_{ij}^{n}}{u\_{ij}};} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{q}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{q}^{n} + \\gamma\_{\\mathbf{q}}\\nabla\_{\\mathbf{q}}(\\mathbf{q}^{n},\\mathbf{b}^{n},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{q} \\geq \\mathbf{0},} \\\\ {\\mathbf{q}^{n}\\,\\text{if}\\,\\mathbf{q}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{q}^{(n + 1)}\\Rightarrow Q^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{b}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{b}^{n} + \\gamma\_{\\mathbf{b}}\\nabla\_{\\mathbf{b}}(\\mathbf{q}^{n},\\mathbf{b}^{n},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{b}^{(n + 1)} \\geq \\mathbf{0},} \\\\ {\\mathbf{b}^{n}\\text{if}\\,\\mathbf{b}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{b}^{(n + 1)}\\Rightarrow B^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{w}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{w}^{n} + \\gamma\_{\\mathbf{w}}\\nabla\_{\\mathbf{w}}(\\mathbf{q}^{(n + 1)},\\mathbf{b}^{(n + 1)},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{w} \\geq \\mathbf{0},} \\\\ {\\mathbf{w}^{n}\\text{if}\\,\\mathbf{w}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{w}^{(n + 1)}\\Rightarrow W^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{e}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{e}^{n} + \\gamma\_{\\mathbf{e}}\\nabla\_{\\mathbf{e}}(\\mathbf{q}^{(n + 1)},\\mathbf{b}^{(n + 1)},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{e}^{(n + 1)} \\geq \\mathbf{0},} \\\\ {\\mathbf{e}^{n}\\text{if}\\,\\mathbf{e}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{e}^{(n + 1)}\\Rightarrow E^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {X^{(n + 1)} = E^{(n + 1)}\\left\\{ {\\left\\lbrack {B^{(n + 1)}\\left( {UQ^{(n + 1)}} \\right)} \\right\\rbrack W^{(n + 1)}} \\right\\};} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathcal{H}^{(n + 1)} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}x\_{ij}^{(n + 1)}}}\\ln\\frac{x\_{ij}^{(n + 1)}}{u\_{ij}}.} \\\\ \\end{array}$$  
    
*   *c) Stopping condition:*
    
      
    $$\\begin{array}{r} {\\text{If}\\,\\,\\mathcal{H}^{(n + 1)} - \\mathcal{H}^{(n)} \\leq \\delta,\\,\\text{then}\\, STOP.} \\\\ \\end{array}$$  
    

## 3.4Entropy Reduction under Matrix Norm and Information Capacity Constraints

When applying the entropy reduction of a data matrix, it is desirable to obtain a reduced matrix with definite properties. In terms of the EDR method, this means introducing some restrictions on the class of projector matrices, which indirectly affect the resulting reduced matrix. Consider some useful characteristics of projector matrices.

**1. Frobenius norms of matrices** Above, it has been supposed that the direct *Q* and inverse *T* projector matrices have nonnegative elements. Such an assumption is due to the use of cross-entropy to characterize the “distance” between them. However, in applications-relevant machine learning problems, it often makes sense to narrow the class of projector matrices. This can be achieved by considering the Frobenius matrix norm:

![](images/math3_268.jpg)

**2. Information capacity of data matrix** In the course of reduction, some information contained in a data matrix is lost. Therefore, it should be measured somehow. Introduce the concept of *the information capacity ℐ(*A*)* of a nonnegative matrix *A*[*n* × *q*], which is given by

  
$$\\begin{array}{r} {\\mathcal{I}(A) = {\\sum\\limits\_{i = 1}^{n}{\\sum\\limits\_{j = 1}^{q}a\_{ij}}}\\ln a\_{ij}.} \\\\ \\end{array}$$  
(3.59)

Clearly, the information capacity corresponds to the entropy taken with the opposite sign.

**3. Cross-entropy reduction algorithm** The dimension reduction procedure of a data matrix is to minimize the cross-entropy:

  
$$\\begin{array}{r} \\left. H(Q,T\\, \\middle| \\, U)\\Rightarrow\\min\\limits\_{Q,T}, \\right. \\\\ \\end{array}$$  
(3.60)

where

  
$$\\begin{array}{r} \\left. H(Q,T\\, \\middle| \\, U) = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}x\_{ij}}}(Q,T\\, \\middle| \\, U)\\ln\\frac{\\left. x\_{ij}(Q,T\\, \\middle| \\, U) \\right.}{u\_{ij}}, \\right. \\\\ \\end{array}$$  
(3.61)

  
$$\\begin{array}{r} \\left. x\_{ij}(Q,T\\, \\middle| \\, U) = {\\sum\\limits\_{\\mu = 1}^{r}{\\sum\\limits\_{\\nu = 1}^{s}t\_{\\mu,j}}}q\_{\\nu,\\mu}u\_{i,\\nu},\\text{\\quad\\quad}i = \\overline{1,m};\\, j = \\overline{1,s}, \\right. \\\\ \\end{array}$$  
(3.62)

subject to the following constraints:

*   —the nonnegative values of the projector matrices,
    
      
    $$\\begin{array}{r} {Q \\geq 0,\\text{\\quad\\quad}T \\geq 0;} \\\\ \\end{array}$$  
    (3.63)
    
*   —the upper bounds (*a*, *b*) on the norm of the projector matrices,
    
      
    $$\\begin{array}{r} {n\_{Q}(Q) = {\\sum\\limits\_{i = 1}^{s}{\\sum\\limits\_{j = 1}^{r}q\_{ij}^{2}}} \\leq a,\\quad n\_{T}(T) = {\\sum\\limits\_{i = 1}^{r}{\\sum\\limits\_{j = 1}^{s}t\_{ij}^{2}}} \\leq b;} \\\\ \\end{array}$$  
    (3.64)
    
*   —the *δ*\-admissible decrease of the information capacity,
    
      
    $$\\begin{array}{r} {\\frac{\\left. \\mathcal{I}(U) - \\mathcal{I}(Y(Q \\middle| U)) \\right.}{\\mathcal{I}(U)} \\leq \\delta.} \\\\ \\end{array}$$  
    (3.65)
    

In this inequality,

  
$$\\begin{array}{r} \\left. \\mathcal{I}(Y(Q\\, \\middle| \\, U)) = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}y\_{ij}}}(Q\\, \\middle| \\, U)\\ln y\_{ij}(Q\\, \\middle| \\, U), \\right. \\\\ \\end{array}$$  
(3.66)

  
$$\\begin{array}{r} \\left. y\_{ij}(Q\\, \\middle| \\, U) = {\\sum\\limits\_{\\nu = 1}^{s}u\_{i,\\nu}}q\_{\\nu,j}. \\right. \\\\ \\end{array}$$  
(3.67)

Due to the properties of the objective function (an entropy-bilinear form) and the constraints specified by quadratic entropy inequalities, the cross-entropy reduction problem (3.60)–(3.64) is nonconvex; for details, see \[[134](#refbib.xhtml#r134), [171](#refbib.xhtml#r171)\]. Therefore, there exists a certain (a priori unknown) number of local optimums, and this problem should be treated as a global optimization one.

Consider the problem (3.60)–(3.64) as a local minimization problem on the nonnegative orthant *R*[+]^(2*s**r*). Here the variables are the elements of the matrices *Q* and *T* each containing *rs* entries. Using *matrix vectorization*, i.e., the transition to a complex vector through the sequential joining of rows, construct the vectors **q**, **t** and **u**, corresponding to the matrices *Q*, *T* and *U*, respectively. Then the cross-entropy minimization problem can be represented as

  
$$\\begin{array}{r} \\left. \\mathcal{H}(\\mathbf{q},\\mathbf{t}\\, \\middle| \\,\\mathbf{u})\\Rightarrow\\min, \\right. \\\\ \\end{array}$$  
(3.68)

  
$$\\begin{aligned} & {(\\mathbf{q},\\mathbf{t}) \\in R\_{+}^{(2sr)},} \\\\ & {N\_{Q}(\\mathbf{q}) = - {\\widetilde{N}}\_{Q}(\\mathbf{q}) + a \\geq 0,\\quad N\_{T}(\\mathbf{t}) = - {\\widetilde{N}}\_{T}(\\mathbf{t}) + b \\geq 0,} \\\\ & \\left. \\mathcal{I}\_{Y}(\\mathbf{q}) = I\_{Y}(\\mathbf{q}\\, \\middle| \\,\\mathbf{u}) - \\gamma(\\delta) \\geq 0,\\quad\\gamma(\\delta) = (1 - \\delta)I\_{U}. \\right. \\\\ \\end{aligned}$$  
(3.69)

Recall that the problem (3.68) is considered as a local optimization one, for which the Karush–Kuhn–Tucker conditions are necessary. The Lagrange function for this problem has the form

  
$$\\begin{array}{r} {L(\\mathbf{q},\\mathbf{t},\\alpha,\\beta,\\gamma) = \\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) - \\left\\langle \\alpha,\\mathbf{q} \\right\\rangle - \\left\\langle \\beta,\\mathbf{t} \\right\\rangle,} \\\\ \\end{array}$$  
(3.70)

where *α* = {*α*[1],…,*α*[*r**s*]}, *β* = {*β*[1],…,*β*[*r**s*]}, and *γ* = {*γ*[1],*γ*[2],*γ*[3]} are the Lagrange multipliers related to the corresponding constraints.

The function

  
$$\\begin{array}{r} {\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) = \\mathcal{H}(\\mathbf{q},\\mathbf{t}) - \\gamma\_{1}N\_{Q}(\\mathbf{q}) - \\gamma\_{2}N\_{T}(\\mathbf{t}) - \\gamma\_{3}\\mathcal{I}\_{Y}(\\mathbf{q})} \\\\ \\end{array}$$  
(3.71)

will be called the truncated Lagrange function.

Assume that there exists a local minimum point (**q**^(\*), **t**^(\*)) in the problem (3.68, 3.70) and a neighborhood

  
$$\\begin{array}{r} {\\mathcal{O}\_{(\\mathbf{q}^{\*},\\mathbf{t}^{\*})}(\\mathbf{q},\\mathbf{t}) \\in \\|\\mathbf{q}^{\*} - \\mathbf{q}\\|^{2} + \\|\\mathbf{t}^{\*} - \\mathbf{t}\\|^{2} \\leq \\varrho} \\\\ \\end{array}$$  
(3.72)

such that the problem (3.68), (3.70) becomes convex on the set (3.72). Then the Kuhn–Tucker conditions \[134\] are satisfied on the set (3.72) in terms of the truncated Lagrange function (3.71), i.e.,

  
$$\\begin{aligned} & {\\nabla\_{\\mathbf{q}}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) \\geq \\mathbf{0},\\text{\\quad\\quad}\\nabla\_{\\mathbf{t}}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) \\geq \\mathbf{0},} \\\\ & {\\mathbf{q} \\otimes \\nabla\_{\\mathbf{q}}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) \\geq \\mathbf{0},\\text{\\quad\\quad}\\mathbf{t} \\otimes \\nabla\_{\\mathbf{t}}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) \\geq \\mathbf{0},} \\\\ & {\\mathbf{q}^{\*} \\geq \\mathbf{0},\\text{\\quad\\quad}\\mathbf{t}^{\*} \\geq \\mathbf{0},} \\\\ & {\\nabla\_{\\gamma}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) \\leq \\mathbf{0},\\text{\\quad\\quad}\\gamma \\otimes \\nabla\_{\\gamma}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma) = \\mathbf{0},} \\\\ & {\\gamma \\geq \\mathbf{0}.} \\\\ \\end{aligned}$$  
(3.73)

This system of equations and inequalities can be solved using the multiplicative algorithm \[[143](#refbib.xhtml#r143)\]. Introduce the following notations:

  
$$\\begin{aligned} & {\\mathbf{G}\_{\\mathbf{q}}(\\mathbf{q},\\mathbf{t},\\gamma) = \\mathbf{1} - \\theta\\nabla\_{\\mathbf{q}}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma),} \\\\ & {\\mathbf{G}\_{\\mathbf{t}}(\\mathbf{q},\\mathbf{t},\\gamma) = \\mathbf{1} - \\theta\\nabla\_{\\mathbf{t}}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma),} \\\\ & {\\mathbf{K}\_{\\gamma}(\\mathbf{q},\\mathbf{t},\\gamma) = \\mathbf{1} + \\theta\\nabla\_{\\gamma}\\mathcal{L}(\\mathbf{q},\\mathbf{t},\\gamma).} \\\\ \\end{aligned}$$  
(3.74)

The multiplicative algorithm, further referred to as **Minimum Cross-Entropy with constraints (MCEC)**, has the following structure.

*   *a) Initial step:*
    
      
    $$\\begin{array}{r} {\\mathbf{q}^{0} > \\mathbf{0},\\quad\\mathbf{t}^{0} > \\mathbf{0}.} \\\\ \\end{array}$$  
    
*   *b) nth iterative step:*
    
      
    $$\\begin{array}{r} {\\mathbf{q}^{(n + 1)} = \\mathbf{q}^{n} \\otimes \\mathbf{G}\_{\\mathbf{q}}(\\mathbf{q}^{n},\\mathbf{t}^{n},\\gamma^{n}),} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathbf{t}^{(n + 1)} = \\mathbf{t}^{n} \\otimes \\mathbf{G}\_{\\mathbf{t}}(\\mathbf{q}^{n},\\mathbf{t}^{n},\\gamma^{n});} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\mathbf{t}^{(n + 1)}\\rightarrow T^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\gamma^{n + 1} = \\gamma^{n} \\otimes \\mathbf{K}\_{\\gamma}(\\mathbf{q}^{n},\\mathbf{t}^{n},\\gamma^{n})} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\mathbf{q}^{(n + 1)}\\rightarrow Q^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. \\mathbf{t}^{(n + 1)}\\rightarrow T^{(n + 1)}; \\right. \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {X^{(n + 1)} = U\\, Q^{(n + 1)}\\, T^{(n + 1)};} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} \\left. H(Q^{(n + 1)},T^{(n + 1)}\\, \\middle| \\, U) = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{r}x\_{ij}^{(n + 1)}}}\\ln\\frac{x\_{ij}^{(n + 1)}}{u\_{ij}} = H^{(n + 1)}. \\right. \\\\ \\end{array}$$  
    
*   *c) Stopping condition:*
    
      
    $$\\begin{array}{r} {H^{(n + 1)} - H^{(n)} \\leq \\Delta.} \\\\ \\end{array}$$  
    

This algorithm converges to a local minimum if the initial point is positive \[143\].

## 3.5Estimating Efficiency of Dimension Reduction for Linear Model Learning

Linear static models are widely used to describe objects in RML problems. Consider this description in detail for the original and reduced input learning collections.

### 3.5.1Linear model

A linear static object has a single output *z* and *s* inputs **u** ∈ *R*^(*s*). The state of this object is characterized by *s* attributes with parametric weights **a**. The object's mathematical model is randomized, i.e., parameters **a** are random of the interval type:

  
$$\\begin{array}{r} {\\mathbf{a} \\in \\mathcal{A} = \\left\\{ \\mathbf{a}^{-} \\leq \\mathbf{a} \\leq \\mathbf{a}^{+} \\right\\}.} \\\\ \\end{array}$$  
(3.75)

The probabilistic properties of these parameters are characterized by a probability density function (PDF) *P*(**a**). Since the object is linear and static, the output *z* of its model has a linear relation to the inputs:

  
$$\\begin{array}{r} {z = \\left\\langle \\mathbf{u},\\mathbf{a} \\right\\rangle,} \\\\ \\end{array}$$  
(3.76)

where ⟨,⟩ denotes the scalar product of vectors.

Suppose that there is an input learning collection 𝒰 of *m* such objects, whose state is characterized by vectors **u**^((1)), …, **u**^((*m*)) from the attribute space *R*^(*s*) and output is characterized by a vector **y** = {*y*[1],…,*y*[*m*]}. Due to the object's linearity, the output of the model has the form

  
$$\\begin{array}{r} {\\mathbf{z} = U\\mathbf{a},\\text{\\quad\\quad}\\mathbf{z} = \\left\\{ z\_{1},\\ldots,z\_{m} \\right\\},} \\\\ \\end{array}$$  
(3.77)

where *U* = *U*[(*m* × *s*)] is a nonnegative matrix of dimensions (*m* × *s*) and

  
$$\\begin{array}{r} {\\mathbf{z} \\in \\mathcal{Z} = \\lbrack\\mathbf{z}^{-},\\mathbf{z}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{z}^{-} = U\\mathbf{a}^{-};\\,\\,\\mathbf{z}^{+} = U\\mathbf{a}^{+}.} \\\\ \\end{array}$$  
(3.78)

A common assumption is that the outputs of the objects contain measurement errors described by a random vector $\\overline{\\xi} = \\left\\{ \\xi\_{1},\\ldots,\\xi\_{m} \\right\\}$ of the interval type, i.e.,

  
$$\\begin{array}{r} {\\overline{\\xi} \\in \\mathcal{K} = \\left\\{ {\\overline{\\xi}}^{-} \\leq \\overline{\\xi} \\leq {\\overline{\\xi}}^{+} \\right\\},} \\\\ \\end{array}$$  
(3.79)

with a probability density function $L(\\overline{\\xi}).$ In addition, let the PDFs of the model parameters and measurement noises be continuously differentiable.

The observed output of the model is distorted by some noises and has the form

  
$$\\begin{array}{r} {\\mathbf{v} = \\mathbf{z} + \\overline{\\xi} = U\_{(m \\times s)}\\,\\mathbf{a} + \\overline{\\xi}.} \\\\ \\end{array}$$  
(3.80)

The vector **v** belongs to the *m*\-dimensional parallelepiped

  
$$\\begin{array}{r} {\\mathcal{V} = \\lbrack\\mathbf{v}^{-},\\mathbf{v}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{v}^{-} = \\mathbf{z}^{-} + {\\overline{\\xi}}^{-};\\,\\,\\mathbf{v}^{+} = \\mathbf{z}^{+} + {\\overline{\\xi}}^{+}.} \\\\ \\end{array}$$  
(3.81)

RML procedures produce the estimates *P̂*(**a**) and $\\hat{L}(\\overline{\\xi})$ of the corresponding PDFs. This is done using the learning collection (𝒰,**y**) and the randomized model (3.80). The resulting estimates serve for implementing this model, i.e., for generating an ensemble 𝒱 of the random vectors **v** ∈ *R*^(*m*). The generation of such ensembles is one of the randomized machine-learning problems \[[145](#refbib.xhtml#r145)\], further referred to as *the s-problem of RML*.

In many cases, the dimension *s* of the attribute space turns out to be very high for the existing computational capabilities. Therefore, it makes sense to reduce this space to a given dimension *r* < *s*.

Introduce an input data matrix *W*[(*m* × *r*)], which will characterize a collection 𝒲 of *m* objects in the reduced attribute space *R*^(*r*), and a randomized model with parameters **b** = {*b*[1],…,*b*[*r*]} ∈ *R*^(*r*):

  
$$\\begin{array}{r} {\\mathbf{w} = W\_{(m \\times r)}\\mathbf{b},\\text{\\quad\\quad}\\mathbf{b} \\in R^{r},\\,\\,\\mathbf{w} \\in R^{m}.} \\\\ \\end{array}$$  
(3.82)

The parameter vector **b** consists of random components of the interval type, i.e.,

  
$$\\begin{array}{r} {\\mathbf{b} \\in \\mathcal{B} = \\lbrack\\mathbf{b}^{-},\\mathbf{b}^{+}\\rbrack,} \\\\ \\end{array}$$  
(3.83)

with a PDF *B*(**b**). The observed vector has the form

  
$$\\begin{array}{r} {\\mathbf{t} = \\mathbf{w} + \\overline{\\zeta},\\text{\\quad\\quad}\\overline{\\zeta} \\in R^{m}.} \\\\ \\end{array}$$  
(3.84)

The random vector $\\overline{\\zeta}$ describes measurement errors and is of the interval type, i.e.,

  
$$\\begin{array}{r} {\\overline{\\zeta} \\in \\mathcal{J} = \\lbrack{\\overline{\\zeta}}^{-},{\\overline{\\zeta}}^{+}\\rbrack,} \\\\ \\end{array}$$  
(3.85)

with a PDF $Q(\\overline{\\zeta}).$ Finally,

  
$$\\begin{array}{r} {\\mathbf{t} \\in \\mathcal{T} = \\lbrack\\mathbf{t}^{-},\\mathbf{t}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{t}^{-} = W\\mathbf{b}^{-} + {\\overline{\\zeta}}^{-},\\,\\,\\mathbf{t}^{+} = W\\mathbf{b}^{+} + {\\overline{\\zeta}}^{+}.} \\\\ \\end{array}$$  
(3.86)

All the PDFs characterizing the model parameters and measurement noises are assumed to be continuously differentiable functions. The estimation of the PDF *B*(**b**) and the generation of a corresponding ensemble 𝒯 is another randomized machine-learning problem, called *the r-problem of RML*.

### 3.5.2Comparing *s*\- and *r*\-problems of RML

These problems will be compared via a three-stage method as follows. In the first stage, the *s*\- and *r*\-problems solved by the RML procedures using the learning collections (𝒰,**y**) and (𝒲,**y**), respectively. This stage yields the entropy-optimal PDFs of the model parameters and measurement noises, *P*^(\*)(**a**) and $L^{\*}(\\overline{\\xi})$ for the *s*\-problem as well as *B*^(\*)(**b**) and $Q^{\*}(\\overline{\\zeta})$ for the *r*\-problem, respectively. In the second stage, the linear models (3.80, 3.84) are used for calculating the PDFs *F*[*s*](**v**) and *F*[*r*](**t**) normalized on the set 𝒞 = 𝒱 ∩ 𝒯. Finally, in the third stage, the Kullback–Leibler relative entropy \[[102](#refbib.xhtml#r102)\] is calculated, which characterizes the absolute divergence between the PDFs *F*[*s*](**v**) and *F*[*r*](**t**). This method will be called *the *s* \\&*r* comparison* (SRC).

Consider *the first stage*, and recall the RML procedure for solving the *s*\-problem; see the model described by (3.80).

For obtaining the best estimates under maximum uncertainty (the highest quality of learning), maximize the entropy functional defined on the PDFs *P*(**a**) and $L(\\overline{\\xi}),$

  
$$\\begin{array}{r} \\left. \\mathcal{H}\\lbrack P(\\mathbf{a}),L(\\overline{\\xi})\\rbrack = - {\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\,\\ln P(\\mathbf{a})d\\mathbf{a} - {\\int\_{\\mathcal{K}}L}(\\overline{\\xi})\\ln L(\\overline{\\xi})d\\overline{\\xi}\\Rightarrow\\max, \\right. \\\\ \\end{array}$$  
(3.87)

subject to the constraints

  
$$\\begin{array}{r} {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})d\\mathbf{a} = 1,\\text{\\quad\\quad}{\\int\_{\\mathcal{K}}L}(\\overline{\\xi})d\\overline{\\xi} = 1,} \\\\ \\end{array}$$  
(3.88)

and

  
$$\\begin{array}{r} {\\mathcal{M}\\left\\{ \\mathbf{z} \\right\\} = {\\int\_{\\mathcal{A}}U}P(\\mathbf{a})d\\mathbf{a} + {\\int\_{\\mathcal{K}}\\overline{\\xi}}L(\\overline{\\xi})d\\overline{\\xi} = \\mathbf{y}.} \\\\ \\end{array}$$  
(3.89)

This is an entropy-linear functional programming problem \[138\]. Its solution has the form

  
$$\\begin{aligned} & {P^{\*}(\\mathbf{a}) = \\pi^{- 1}(\\overline{\\theta})\\exp\\left\\langle - \\overline{\\theta},U\\,\\mathbf{a} \\right\\rangle,} \\\\ & {L^{\*}(\\overline{\\xi}) = \\varpi^{- 1}(\\overline{\\theta})\\exp\\left\\langle - \\overline{\\theta},\\overline{\\xi} \\right\\rangle,} \\\\ \\end{aligned}$$  
(3.90)

where

  
$$\\begin{aligned} {\\pi(\\overline{\\theta})} & {= {\\int\_{\\mathcal{A}}\\exp}\\left\\langle - \\overline{\\theta},U\\,\\mathbf{a} \\right\\rangle d\\mathbf{a},} \\\\ {\\varpi(\\overline{\\theta})} & {= {\\int\_{\\mathcal{K}}\\exp}\\left\\langle - \\overline{\\theta},\\overline{\\xi} \\right\\rangle d\\overline{\\xi}.} \\\\ \\end{aligned}$$  
(3.91)

The Lagrange multipliers $\\overline{\\theta}$ are found from the balance equations (3.89):

  
$$\\begin{array}{r} {{\\int\_{\\mathcal{A}}U}P^{\*}(\\mathbf{a})d\\mathbf{a} + {\\int\_{\\mathcal{K}}\\overline{\\xi}}L^{\*}(\\overline{\\xi})d\\overline{\\xi} = \\mathbf{y}.} \\\\ \\end{array}$$  
(3.92)

Thus, the solution of the *s*\-problem of RML gives the two entropy-optimal PDFs *P*^(\*)(**a**) (model parameters) and $L^{\*}(\\overline{\\xi})$ (measurement noises).

In *the second stage*, the linear model (3.80) is used, which has independent parameters and measurement noises. The probability density function *F*(**v**) of the observed vector **v** has the form

  
$$\\begin{array}{r} {F(\\mathbf{v}) = {\\int\_{\\mathcal{K}}G}(\\mathbf{v} - \\overline{\\xi})L^{\*}(\\overline{\\xi})d\\overline{\\xi},} \\\\ \\end{array}$$  
(3.93)

where *G*( • ) is the density of the vector **z** (3.80). According to this equality,

  
$$\\begin{array}{r} {\\mathbf{a} = {(U^{\\intercal}U)}^{- 1}\\, U^{\\intercal}\\mathbf{z}.} \\\\ \\end{array}$$  
(3.94)

Therefore,

  
$$\\begin{array}{r} {P^{\*}({(U^{\\intercal}U)}^{- 1}\\, U^{\\intercal}\\mathbf{z}) = \\eta(\\mathbf{z}),} \\\\ \\end{array}$$  
(3.95)

where the vector **z** is defined on the set 𝒵 (3.78). Normalizing this function, obtain the PDF

  
$$\\begin{array}{r} {G(\\mathbf{z}) = \\frac{\\eta(\\mathbf{z})}{{\\int\_{\\mathcal{Z}}\\eta}(\\mathbf{z})}d\\mathbf{z}} \\\\ \\end{array}$$  
(3.96)

of the vector **z**, which is normalized on the set 𝒵 (3.78).

Well, equality (3.93) gives the PDF *F*(**v**), **v** ∈ 𝒱 (3.81) for the randomized model of the *s*\-problem. Denote it by *F*[*s*](**v**).

Using a similar procedure for the *r*\-problem (3.82–3.84) with the reduced data matrix *W* (3.75), find the PDF *F*[*r*](**t**) normalized on the set 𝒯 (3.86).

For comparing the PDFs *F*[*s*](**v**) and *F*[*r*](**t**), introduce the set

  
$$\\begin{array}{r} {\\mathcal{C} = \\mathcal{V}{\\cap \\mathcal{T}},} \\\\ \\end{array}$$  
(3.97)

and normalize these functions on it. The normalized PDFs have the form

  
$$\\begin{array}{r} {{\\widetilde{F}}\_{s}(\\mathbf{c}) = \\frac{F\_{s}(\\mathbf{c})}{{\\int\_{\\mathcal{C}}F\_{s}}(\\mathbf{c})d\\mathbf{c}},} \\\\ {{\\widetilde{F}}\_{r}(\\mathbf{c}) = \\frac{F\_{r}(\\mathbf{c})}{{\\int\_{\\mathcal{C}}F\_{r}}(\\mathbf{c})d\\mathbf{c}}.} \\\\ \\end{array}$$  

In *the third stage*, the PDFs will be compared using the Kullback–Leibler divergence as a measure of *the absolute information error Δ* between the PDFs *F̃*[*r*](**c**) and *F̃*[*s*](**c**):

  
$$\\begin{array}{r} {KL({\\widetilde{F}}\_{s},{\\widetilde{F}}\_{r}) = {\\int\_{\\mathcal{C}}{\\widetilde{F}}\_{r}}(\\mathbf{c})\\ln\\frac{{\\widetilde{F}}\_{r}(\\mathbf{c})}{{\\widetilde{F}}\_{s}(\\mathbf{c})} = \\Delta \\geq 0.} \\\\ \\end{array}$$  
(3.98)

Note that the minimum *Δ* = 0 is achieved at *F̃*[*r*](**c**) = *F̃*[*s*](**c**).

In addition, introduce *the relative information error δ* in the form

  
$$\\begin{array}{r} {\\delta = \\frac{\\Delta}{H\_{s} + H\_{r}},} \\\\ \\end{array}$$  
(3.99)

where

  
$$\\begin{aligned} H\_{s} & {= {\\int\_{\\mathcal{C}}{\\widetilde{F}}\_{s}}(\\mathbf{c})\\ln{\\widetilde{F}}\_{s}(\\mathbf{c})d\\mathbf{c},} \\\\ H\_{r} & {= {\\int\_{\\mathcal{C}}{\\widetilde{F}}\_{r}}(\\mathbf{c})\\ln{\\widetilde{F}}\_{r}(\\mathbf{c})d\\mathbf{c}.} \\\\ \\end{aligned}$$  
(3.100)

These equalities are the information entropies of the PDFs *F̃*[*s*] and *F̃*[*r*] defined on the support 𝒞 (3.97).

## 3.6Estimating Efficiency of EDR for Binary Classification Problems

The EDR method will be characterized and compared by efficiency with principal component analysis (PCA) and the random projection (RP) method using a computational experiment on real data for the binary classification problem with a linear classifier.

### 3.6.1Linear classifier

### 3.6.2Scheme of computational experiment

Following \[[162](#refbib.xhtml#r162), [190](#refbib.xhtml#r190)\], the EDR method was experimentally studied by solving the binary classification problem in the original and reduced attribute spaces, with subsequent comparison of this method with PCA and the RP method in terms of the classification accuracy (3.107). For making the results stable, Monte Carlo simulations and cross-validation were used.

The experiment consisted of several stages:

1.  solving the classification problem in the original space;
    
2.  solving the classification problem in the PCA-reduced spaces;
    
3.  solving the classification problem in the RP-reduced spaces;
    
4.  solving the classification problem in the EDR-reduced spaces.
    

Stages 2–4 were sequentially implemented for the dimension reduced by 1, i.e., *r* = *s* − 1, …, 1, where *r* denotes the dimension of the reduced spaces. Stage 4 was implemented for various values of *δ* (an admissible decrease of information capacity).

The Python program for the experimental study was developed in OS Linux using the numpy 1.14.3, scipy 1.1.0, sklearn 0.19.1 libraries. Dimension reduction by principal component analysis and the random projection method was carried out using the corresponding classes of the scikit-learn library \[[128](#refbib.xhtml#r128)\], PCA and GaussianRandomProjection. The classification problem was solved using support vector machines \[[70](#refbib.xhtml#r70)\], i.e., the SVC class with the linear kernel.

The experimental study was based on two data sets as follows. The first one (*simulation*) was a synthetic data set of 100 objects with 10 attributes. The data were generated by the make\_classification function \[[26](#refbib.xhtml#r26)\] with the parameters n\_classes=2, n\_clusters\_per\_class=2, n\_informative=10, n\_redundant=0 and class\_sep=1.0. This function generates points in the space of the dimension n\_informative that are normally distributed (with zero mean and unit variance) around the edges of a hypercube with sides 2 \* class\_sep with some noise added.

The second data set (*heart*) consisted of the real data collected during heart disease research \[[2](#refbib.xhtml#r2)\]. This data set contains 270 objects with 13 attributes.

In all experiments, the data were normalized to the interval \[0,1\].

### 3.6.3Results of experiment

All experiments involved cross-validation using the bootstrap method \[70\]. More specifically, 30 objects were randomly selected 2 times from the original data set; 20 of them were used to learn the classifier, whereas the remaining 10 were used for testing; the results for each sample were averaged. Then the experiment was repeated 10 times, the results were also averaged. Dimension reduction at each stage was carried out for the entire learning sample (30 objects).

The problem (3.32)–(3.35) was solved using the constrained optimization method SLSQP \[[97](#refbib.xhtml#r97)\] on the nonnegative orthant, implemented in the scipy library by the minimize function with the parameters ftol=1e-4 and maxiter=1000. Note that for some values of *δ* the method yielded no solution for the given optimization parameters. In such cases, the last solution found was used.

*1. Dependence of *ε* on number of objects (sample size m)* It is important to study this dependence for the three reduction methods in order to identify the areas of their application. As is well known, entropy maximization methods and their derivatives, in particular, the EDR method, are usually used with a limited amount of data compared to the dimension of the attribute space. In the case of “big data,” there exist no fundamental restrictions on their application, but the computational difficulties will significantly increase. As for PCA, for large amounts of data (sufficiently great *m*) and their heterogeneity, the method becomes unstable \[[136](#refbib.xhtml#r136)\].

The dependence of the classification accuracy on small sample sizes for the *simulation* data set was examined. The results are presented in [Table 3.1](#chapter3.xhtml#t3_1), [Table 3.2](#chapter3.xhtml#t3_2), [Table 3.3](#chapter3.xhtml#t3_3) for $m = \\overline{5,10}.$ For each of these sets, the attribute space was reduced to the size $r = \\overline{5,10}.$

 [Table 3.1:](#chapter3.xhtml#t3_1b) Classification accuracy for data set *simulation* with PCA-based dimension reduction for different learning sample sizes *m*. 

 
|  |
| --- |
| *m / r* || 10 || 9 || 8 || 7 || 6 || 5 |
| 10 || 0.60 || 0.60 || 0.60 || 0.60 || 0.67 || 0.67 |
| --- | --- | --- | --- | --- | --- | --- |
| 9 || 0.48 || 0.48 || 0.48 || 0.48 || 0.48 || 0.52 |
| 8 || 0.46 ||  || 0.46 || 0.46 || 0.46 || 0.46 |
| 7 || 0.48 ||  ||  || 0.48 || 0.48 || 0.48 |
| 6 || 0.44 ||  ||  ||  || 0.44 || 0.44 |
| 5 || 0.40 ||  ||  ||  ||  || 0.40 |
|  |

 

[Table 3.2:](#chapter3.xhtml#t3_2b) Classification accuracy for data set *simulation* with RP-based dimension reduction for different learning sample sizes *m*.

 
|  |
| --- |
| *m / r* || 10 || 9 || 8 || 7 || 6 || 5 |
| 10 || 0.60 || 0.67 || 0.57 || 0.77 || 0.60 || 0.57 |
| --- | --- | --- | --- | --- | --- | --- |
| 9 || 0.48 || 0.48 || 0.59 || 0.41 || 0.52 || 0.48 |
| 8 || 0.46 || 0.46 || 0.46 || 0.46 || 0.46 || 0.54 |
| 7 || 0.48 || 0.48 || 0.52 || 0.38 || 0.43 || 0.52 |
| 6 || 0.44 || 0.28 || 0.39 || 0.39 || 0.39 || 0.39 |
| 5 || 0.40 || 0.40 || 0.40 || 0.40 || 0.40 || 0.40 |
|  |

 

[Table 3.3:](#chapter3.xhtml#t3_3b) Classification accuracy for data set *simulation* with EDR-based dimension reduction for different learning sample sizes *m* and *δ* = 0.5.

 
|  |
| --- |
| *m / r* || 10 || 9 || 8 || 7 || 6 || 5 |
| 10 || 0.60 || 0.70 || 0.70 || 0.63 || 0.50 || 0.53 |
| --- | --- | --- | --- | --- | --- | --- |
| 9 || 0.48 || 0.37 || 0.52 || 0.59 || 0.37 || 0.37 |
| 8 || 0.46 || 0.46 || 0.46 || 0.46 || 0.46 || 0.50 |
| 7 || 0.48 || 0.43 || 0.43 || 0.48 || 0.48 || 0.57 |
| 6 || 0.44 || 0.44 || 0.28 || 0.39 || 0.44 || 0.39 |
| 5 || 0.40 || 0.53 || 0.47 || 0.53 || 0.60 || 0.40 |
|  |

According to [Table 3.1](#chapter3.xhtml#t3_1), [Table 3.2](#chapter3.xhtml#t3_2), [Table 3.3](#chapter3.xhtml#t3_3), the EDR and RP methods are operable under any ratios of the sample size and dimension of the attribute space. At the same time, PCA does not work for *m* < *r*.

*2. Classification accuracy for *m* ≫ *r** [Tables 3.4](#chapter3.xhtml#t3_4) and [3.5](#chapter3.xhtml#t3_5), as well as [Fig. 3.2](#chapter3.xhtml#f3_2), show the classification accuracy for different dimensions of the reduced space. This accuracy was estimated for two data sets, *simulation* and *heart*, in order to analyze its stability with respect to the data sets.

 

[Table 3.4:](#chapter3.xhtml#t3_4b) Classification accuracy for data set *simulation*.

 
|  |
| --- |
| r || 10 || 9 || 8 || 7 || 6 || 5 |
| PCA || 0.65 || 0.64 || 0.63 || 0.65 || 0.65 || 0.64 |
| --- | --- | --- | --- | --- | --- | --- |
| RP || 0.65 || 0.58 || 0.54 || 0.58 || 0.62 || 0.48 |
| EDR || 0.65 || 0.62 || 0.62 || 0.47 || 0.48 || 0.49 |
|  |

 

[Table 3.5:](#chapter3.xhtml#t3_5b) Classification accuracy for data set *heart*.

 
|  |
| --- |
| r || 13 || 12 || 11 || 10 || 9 || 8 |
| PCA || 0.76 || 0.76 || 0.76 || 0.76 || 0.76 || 0.76 |
| --- | --- | --- | --- | --- | --- | --- |
| RP || 0.76 || 0.79 || 0.79 || 0.73 || 0.76 || 0.78 |
| EDR || 0.76 || 0.70 || 0.78 || 0.74 || 0.76 || 0.69 |
|  |

![Figure 3.2: Classification accuracy for data sets simulation and heart.](images/fig3_2.jpg)

[Figure 3.2:](#chapter3.xhtml#f3_2b) Classification accuracy for data sets *simulation* and *heart*.

*3. Dependence of *ε* on admissible decrease *δ* of information capacity (EDR method)* [Table 3.6](#chapter3.xhtml#t3_6) gives the classification accuracy for different values *δ* and the data set *simulation*, whereas [Fig. 3.3](#chapter3.xhtml#f3_3) demonstrates the corresponding graphs. In addition, [Table 3.7](#chapter3.xhtml#t3_7) and [Fig. 3.3](#chapter3.xhtml#f3_3) present the same characteristics for the data set *heart*.

 

[Table 3.6:](#chapter3.xhtml#t3_6b) Dependence *ε*(*δ*) for data set *simulation* (EDR method).

 
|  |
| --- |
| *δ / r* || 9 || 8 || 7 || 6 || 5 |
| 0.1 || 0.60 || 0.65 || 0.50 || 0.50 || 0.50 |
| --- | --- | --- | --- | --- | --- |
| 0.2 || 0.70 || 0.60 || 0.55 || 0.45 || 0.45 |
| 0.3 || 0.75 || 0.75 || 0.40 || 0.45 || 0.50 |
| 0.4 || 0.55 || 0.50 || 0.45 || 0.50 || 0.55 |
| 0.5 || 0.50 || 0.60 || 0.45 || 0.50 || 0.45 |
|  |

![Figure 3.3: Dependence \\varepsilon(\\delta) for data sets simulation and heart.](images/fig3_3.jpg)

[Figure 3.3:](#chapter3.xhtml#f3_3b) Dependence *ε*(*δ*) for data sets *simulation* and *heart*.

 

[Table 3.7:](#chapter3.xhtml#t3_7b) Dependence *ε*(*δ*) for data set *heart* (EDR method).

 
|  |
| --- |
| *δ* / r || 12 || 11 || 10 || 9 || 8 |
| 0.1 || 0.65 || 0.85 || 0.80 || 0.80 || 0.55 |
| --- | --- | --- | --- | --- | --- |
| 0.2 || 0.60 || 0.70 || 0.70 || 0.60 || 0.65 |
| 0.3 || 0.75 || 0.75 || 0.75 || 0.80 || 0.75 |
| 0.4 || 0.75 || 0.85 || 0.80 || 0.80 || 0.70 |
| 0.5 || 0.75 || 0.75 || 0.65 || 0.80 || 0.80 |
|  |

*4. Information losses caused by reduction* As has been emphasized above, the reduction of the attribute space leads to information losses.

The relative value of such losses can be described by

  
$$\\begin{array}{r} {I = \\frac{\\mathcal{I}(U) - \\mathcal{I}(Y)}{\\mathcal{I}(U)},} \\\\ \\end{array}$$  
(3.108)

where *Y* is the reduced data matrix. In the course of the experiment, the information losses caused by dimension reduction using PCA, the RP and EDR methods were estimated for the data sets *simulation* and *heart*.

[Tables 3.8](#chapter3.xhtml#t3_8)–[3.9](#chapter3.xhtml#t3_9) illustrate the relative information losses *I* (3.108). For the EDR method, the values were averaged over *δ*.

 

[Table 3.8:](#chapter3.xhtml#t3_8b) Relative information losses for data set *simulation*.

 
|  |
| --- |
| *r* || 9 || 8 || 7 || 6 || 5 |
| PCA || 0.6691 || 0.6979 || 0.7298 || 0.7616 || 0.7973 |
| --- | --- | --- | --- | --- | --- |
| RP || 0.6630 || 0.6818 || 0.7844 || 0.7618 || 0.8777 |
| EDR || 0.2688 || 0.2911 || 0.3034 || 0.3501 || 0.4125 |
|  |

 

[Table 3.9:](#chapter3.xhtml#t3_9b) Relative information losses for data set *heart*.

 
|  |
| --- |
| *r* || 12 || 11 || 10 || 9 || 8 || 7 |
| PCA || 0.2935 || 0.3317 || 0.3857 || 0.4399 || 0.4941 || 0.5671 |
| --- | --- | --- | --- | --- | --- | --- |
| RP || 0.1444 || 0.3708 || 0.5190 || 0.6051 || 0.6736 || 0.8167 |
| EDR || 0.3083 || 0.3013 || 0.3184 || 0.2772 || 0.2589 || 0.2792 |
|  |

[Figure 3.4](#chapter3.xhtml#f3_4) shows the graphs of the relative information losses for the data sets *simulation* and *heart*.

![Figure 3.4: Relative information losses for data sets simulation and heart.](images/fig3_4.jpg)

[Figure 3.4:](#chapter3.xhtml#f3_4b) Relative information losses for data sets *simulation* and *heart*.

The relative information losses caused by the EDR method for different values *δ* are combined in [Tables 3.10](#chapter3.xhtml#t3_10)–[3.11](#chapter3.xhtml#t3_11).

 

[Table 3.10:](#chapter3.xhtml#t3_10b) Dependence *I*(*δ*) for data set *simulation* (EDR method).

 
|  |
| --- |
| *δ / r* || 9 || 8 || 7 || 6 || 5 |
| 0.1 || 0.0959 || 0.0997 || 0.1594 || 0.2795 || 0.3996 |
| --- | --- | --- | --- | --- | --- |
| 0.2 || 0.2000 || 0.1932 || 0.1982 || 0.2656 || 0.3880 |
| 0.3 || 0.2896 || 0.2896 || 0.2952 || 0.2943 || 0.3805 |
| 0.4 || 0.3615 || 0.3887 || 0.3933 || 0.3981 || 0.3992 |
| 0.5 || 0.3971 || 0.4842 || 0.4707 || 0.5130 || 0.4954 |
|  |

![Figure 3.5: Dependence I(\\delta) for data sets simulation and heart (EDR method).](images/fig3_5.jpg)

Figure 3.5: Dependence *I*(*δ*) for data sets *simulation* and *heart* (EDR method).

 

[Table 3.11:](#chapter3.xhtml#t3_11b) Dependence *I*(*δ*) for data set *heart* (EDR method).

 
|  |
| --- |
| *δ / r* || 12 || 11 || 10 || 9 || 8 || 7 |
| 0.1 || 0.1071 || 0.0478 || 0.0821 || 0.1244 || 0.1065 || 0.1254 |
| --- | --- | --- | --- | --- | --- | --- |
| 0.2 || 0.5947 || 0.0898 || 0.0676 || 0.0568 || 0.1435 || 0.1428 |
| 0.3 || 0.3344 || 0.7126 || 0.6659 || 0.3530 || 0.2961 || 0.2992 |
| 0.4 || 0.2921 || 0.3878 || 0.3833 || 0.4066 || 0.2814 || 0.3974 |
| 0.5 || 0.2134 || 0.2683 || 0.3932 || 0.4452 || 0.4670 || 0.4310 |
|  |

The results of the computational experiment allow drawing the following conclusions:

*   The EDR method is operable for any amounts of data in the learning and testing data collections; PCA does not work when the amount of data is smaller than the dimension of the attribute space; the operability of the RP method requires additional research.
    
*   The level of information losses when applying the EDR method is retained up to the two-fold reduction of the attribute space; for PCA and the RP method, the level of information losses grows significantly with decreasing the dimension of the attribute space.
    
*   Thanks to the control parameter *δ* in the EDR method, the level of relative information losses can be regulated. At the same time, this possibility is absent in PCA and the RP method.
    

## 3.7Entropy Methods for Random Projection

### 3.7.1Statements of Entropy Randomized Projection Problems

**1. Point-set representation of data matrices: indicator of compactness**

Consider a data matrix describing some objects and their attributes:

  
$$\\begin{array}{r} {U\_{(m \\times s)} = \\left( \\begin{array}{l} \\mathbf{u}^{(1)} \\\\ \\cdots \\\\ \\mathbf{u}^{(m)} \\\\ \\end{array} \\right),\\text{\\quad\\quad}\\mathbf{u}^{(i)} = \\left\\{ u\_{1}^{(i)},\\ldots,u\_{s}^{(i)} \\right\\} \\in R^{s},\\,\\, i = \\overline{1,m}.} \\\\ \\end{array}$$  
(3.109)

Here *m* and *s* are the numbers of objects and their attributes, respectively; *R*^(*s*) denotes the attribute space. Assume that the elements of this data matrix are standardized, i.e., $u\_{ij} \\in \\lbrack 0,1\\rbrack,\\, i = \\overline{1,m},\\, j = \\overline{1,s}.$

*The point-set representation of a matrix *U*[(*m* × *s*)] in the attribute space *R*[(*m*)]^(*s*) is the set 𝔘[*m*]^(*s*) of the points {**u**^((1)),…,**u**^((*m*))}*.

For example, the set 𝔘[100]² of 100 two-dimensional points represents a matrix *U*[(100 × 2)].

The spread of points in a set 𝔘[*m*]^(*s*) can be characterized by *the indicator of compactness* *ρ*[*U*], which will be defined as the arithmetic average of the distances between the points:

  
$$\\begin{array}{r} {\\rho\_{U} = \\frac{2}{m(m - 1)}{\\sum\\limits\_{(\\alpha,\\beta) = 1,\\mspace{2mu}\\alpha \\neq \\beta}^{m}\\varrho}(\\mathbf{u}^{(\\alpha)},\\mathbf{u}^{(\\beta)}),} \\\\ \\end{array}$$  
(3.110)

where 𝜚(**u**^((*α*)), **u**^((*β*))) gives the distance between the points **u**^((*α*)) and **u**^((*β*)). If the elements of the data matrix are standardized, then

  
$$\\begin{array}{r} {0 \\leq \\varrho(\\mathbf{u}^{(\\alpha)},\\mathbf{u}^{(\\beta)}) \\leq \\sqrt{2}\\text{\\quad\\quad}\\text{for~all}\\,\\,(\\alpha,\\beta) = \\overline{1,m},} \\\\ {0 \\leq \\rho\_{U} \\leq 1.} \\\\ \\end{array}$$  
(3.111)

Introduce the following classes of transformations for data matrices:

*   (*m**r*) *\-class*: *U*[(*m* × *s*)]→*Y*[(*m* × *r*)], the set 𝔜[*m*]^(*r*) is in the space *R*[(*m*)]^(*r*);
    
*   (*n**s*) *\-class*: *U*[(*m* × *s*)]→*B*[(*n* × *s*)], the set 𝔅[*n*]^(*s*) is in the space *R*[(*n*)]^(*s*);
    
*   (*n**r*) *\-class*: *U*[(*m* × *s*)]→*Z*[(*n* × *r*)], the set ℨ[*n*]^(*r*) is in the space *R*[(*n*)]^(*r*).
    

**2. Random projector matrices and their probabilistic characteristics**

*1. Projection onto the space *R*[(*m*)]^(*r*) (generation of the set 𝔜[*m*]^(*r*))* This operation will be performed using a projector matrix *Q*[(*s* × *r*)]:

  
$$\\begin{aligned} & {Y\_{(m \\times r)} = \\left( \\begin{array}{l} \\mathbf{y}^{(1)} \\\\ \\cdots \\\\ \\mathbf{y}^{(m)} \\\\ \\end{array} \\right) = U\_{(m \\times s)}Q\_{(s \\times r)};} \\\\ & {\\quad y\_{j}^{(i)} = {\\sum\\limits\_{k = 1}^{s}u\_{ik}}q\_{kj},\\,\\, i = \\overline{1,m};\\, j = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(3.112)

The projector matrix *Q*[(*s* × *r*)] is random and of the interval type, i.e.,

  
$$\\begin{array}{r} {Q\_{(s \\times r)} \\in \\mathcal{Q} = \\lbrack Q^{-},Q^{+}\\rbrack.} \\\\ \\end{array}$$  
(3.113)

The probabilistic properties of the projector matrix are characterized by a continuously differentiable probability density function (PDF) *P*(*Q*), defined on 𝒬.

The vectors **y**^((*i*)) form the set 𝒴[*m*]^(*r*) of *r*\-dimensional points, *m* in total. Define the distance 𝜚(**y**^((*α*)),**y**^((*β*)) | *Q*[(*s* × *r*)]) between them and the indicator of compactness

  
$$\\begin{array}{r} \\left. \\rho\_{Y}(Q) = \\frac{2}{m(m - 1)}{\\sum\\limits\_{(\\alpha,\\beta) = 1,\\mspace{2mu}\\alpha \\neq \\beta}^{m}\\varrho}(\\mathbf{y}^{(\\alpha)},\\mathbf{y}^{(\\beta)}\\, \\middle| \\, Q\_{(s \\times r)}). \\right. \\\\ \\end{array}$$  
(3.114)

Since the elements of the projector matrix have random values, the average distance (3.114) is random as well.

Hence, define the mathematical expectation of the indicator of compactness:

  
$$\\begin{array}{r} {{\\overline{\\rho}}\_{Y} = {\\int\_{\\mathcal{Q}}P}(Q)\\rho\_{Y}(Q)dQ.} \\\\ \\end{array}$$  
(3.115)

*2. Projection onto the space *R*^((*n* × *s*)) (generation of the set 𝔅[*n*]^(*s*))* This operation will be performed using a projector matrix *T*[(*n* × *m*)] with random elements:

  
$$\\begin{aligned} B\_{(n \\times s)} & {= \\left( \\begin{array}{l} \\mathbf{b}^{(1)} \\\\ \\cdots \\\\ \\mathbf{b}^{(n)} \\\\ \\end{array} \\right) = T\_{(n \\times m)}U\_{(m \\times s)};\\quad b\_{j}^{(i)} = {\\sum\\limits\_{k = 1}^{m}t\_{ik}}\\, u\_{kj},} \\\\ & {\\quad i = \\overline{1,n};\\, j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(3.116)

The projector matrix *T*[(*n* × *m*)] is random and of the interval type, i.e.,

  
$$\\begin{array}{r} {T\_{(n \\times m)} \\in \\mathcal{T} = \\lbrack T^{-},T^{+}\\rbrack.} \\\\ \\end{array}$$  
(3.117)

Its probabilistic properties are characterized by a PDF *W*(*T*) defined on 𝒯.

The vectors **b**^((*i*)) form the set 𝔅[*n*]^(*s*) of *s*\-dimensional points, *n* < *m* in total. Define the indicator of compactness

  
$$\\begin{array}{r} \\left. \\rho\_{B}(T) = \\frac{2}{n(n - 1)}{\\sum\\limits\_{(\\alpha,\\beta),\\mspace{2mu}\\alpha \\neq \\beta}^{n}\\varrho}(\\mathbf{b}^{(\\alpha)},\\mathbf{b}^{(\\beta)}\\, \\middle| \\, T) \\right. \\\\ \\end{array}$$  
(3.118)

and its mathematical expectation

  
$$\\begin{array}{r} {{\\overline{\\rho}}\_{B} = {\\int\_{\\mathcal{T}}W}(T)\\rho\_{B}(T)dT.} \\\\ \\end{array}$$  
(3.119)

*3. Projection onto the space *R*[(*n*)]^(*r*) (generation of the set ℨ[*n*]^(*r*))* This operation will be performed using random projector matrices *T*[*n* × *m*] and *Q*[(*s* × *r*)]:

  
$$\\begin{aligned} Z\_{(n \\times r)} & {= \\left( \\begin{array}{l} \\mathbf{z}^{(1)} \\\\ \\cdots \\\\ \\mathbf{z}^{(n)} \\\\ \\end{array} \\right) = T\_{(n \\times m)}U\_{(m \\times s)}Q\_{(s \\times r)};} \\\\ z\_{j}^{(i)} & {= {\\sum\\limits\_{p = 1}^{m}t\_{ip}}\\,{\\sum\\limits\_{k = 1}^{s}u\_{pk}}\\, q\_{kj},\\text{\\quad\\quad}i = \\overline{1,n};\\, j = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(3.120)

These projector matrices are of the interval type:

  
$$\\begin{array}{r} {T\_{(n \\times m)} \\in \\mathcal{T} = \\lbrack T^{-},T^{+}\\rbrack,} \\\\ {Q\_{(s \\times r)} \\in \\mathcal{Q} = \\lbrack Q^{-},Q^{+}\\rbrack.} \\\\ \\end{array}$$  
(3.121)

The probabilistic properties of the projector matrices are characterized by a joint PDF *F*(*T*, *Q*) defined on the set

  
$$\\begin{array}{r} {\\mathcal{F} = \\mathcal{T} \\otimes \\mathcal{Q}.} \\\\ \\end{array}$$  
(3.122)

The vectors **z**^((*i*)) form the set ℨ[*n*]^(*r*) of *r*\-dimensional points. The indicator of compactness for this set is given by

  
$$\\begin{array}{r} \\left. \\rho\_{Z}(T,Q) = \\frac{2}{n(n - 1)}{\\sum\\limits\_{(\\alpha,\\beta),\\mspace{2mu}\\alpha \\neq \\beta}^{n}\\varrho}(\\mathbf{z}^{\\alpha},\\mathbf{z}^{\\beta}\\, \\middle| \\, T,Q). \\right. \\\\ \\end{array}$$  
(3.123)

The mathematical expectation of the indicator of compactness has the form

  
$$\\begin{array}{r} {{\\overline{\\rho}}\_{Z} = {\\int\_{\\mathcal{F}}F}(T,Q)\\rho\_{Z}(T,Q)dTdQ.} \\\\ \\end{array}$$  
(3.124)

Depending on the relations between the dimensions (*m*, *s*) of the original data matrix and the dimensions (*m*, *r*), (*n*, *s*) and (*n*, *r*) of the projector matrices, the former is compressed (if *r* < *s* and *n* < *m*) or expanded (if *r* > *s* and *n* > *m*).

### 3.7.2Algorithms for Entropy Randomized Projection

Consider projection onto the space *R*[(*n*)]^(*r*), which transforms a data matrix simultaneously by both parameters.

The entropy randomized projection (ERP) algorithm consists in the maximum entropy estimation (*M**E**E*) of the PDF *F*(*T*, *Q*) with the additional condition that the data matrix *U*[(*m* × *s*)] and the projection *Z*[(*n* × *r*)] have equal values of their indices of compactness.

The *MEE*\-estimate of the function *F*(*B*, *Q*) (see [Chapter A](#appA.xhtml)) is calculated as

  
$$\\begin{aligned} {\\mathcal{H}\\lbrack F(T,Q)\\rbrack} & \\left. = - {\\int\_{\\mathcal{F}}F}(T,Q)\\,\\ln\\, F(T,Q)\\, dTdQ\\Rightarrow\\max, \\right. \\\\ & {{\\int\_{\\mathcal{F}}F}(T,Q)dTdQ = 1,} \\\\ & {{\\int\_{\\mathcal{F}}F}(T,Q)\\rho\_{Z}(T,Q)dTdQ = \\rho\_{U}.} \\\\ \\end{aligned}$$  
(3.125)

The problem (3.125) is a functional constrained optimization problem of the Lyapunov type: all components of such problems are integral functionals \[77\].

Due to the integral form of this problem, the optimality conditions involve the following Lagrange functional with scalar Lagrange multipliers:

  
$$\\begin{aligned} {\\mathcal{L}\\lbrack F(T,Q)\\rbrack} & {= \\mathcal{H}\\lbrack F(T,Q)\\rbrack + \\mu(\\left( {1 - {\\int\_{\\mathcal{F}}F}(T,Q)dTdQ} \\right) +} \\\\ & {+ \\lambda\\left( {\\rho\_{U} - {\\int\_{\\mathcal{F}}F}(T,Q)\\rho\_{Z}(T,Q)dTdQ} \\right).} \\\\ \\end{aligned}$$  
(3.126)

The first-order optimality conditions for this functional in terms of the Gâteaux derivative \[77\] (𝔊[*F*]) have the form

  
$$\\begin{array}{r} {\\mathfrak{G}\_{F}\\mathcal{L}\\lbrack F(T,Q)\\rbrack = 0.} \\\\ \\end{array}$$  
(3.127)

The entropy-optimal PDF of the projector matrices is given by

  
$$\\begin{aligned} \\left. F^{\*}(T,Q\\, \\middle| \\,\\lambda) \\right. & {= \\frac{\\exp\\left( {- \\lambda\\,\\,\\rho\_{Z}(T,Q)} \\right)}{\\mathbb{F}(\\lambda)},} \\\\ {\\mathbb{F}(\\lambda)} & {= {\\int\_{\\mathcal{F}}\\exp}\\left( {- \\lambda\\,\\,\\rho\_{Z}(T,Q)} \\right)dTdQ.} \\\\ \\end{aligned}$$  
(3.128)

According to (3.128), the structure of the PDF depends on the distance (3.123) and is independent of the parameter *λ*. This parameter satisfies the balance equation for the indicators of compactness:

  
$$\\begin{array}{r} {\\Phi(\\lambda) = {\\int\_{\\mathcal{F}}\\exp}\\left( {- \\lambda\\,\\rho\_{Z}(T,Q)} \\right)\\left( {\\rho\_{Z}(T,Q) - \\rho\_{U}} \\right)dTdQ = 0.} \\\\ \\end{array}$$  
(3.129)

Since *λ* is a scale parameter, it may be sufficient to find its approximate value from the linearized equation (3.129):

  
$$\\begin{array}{r} {\\widetilde{\\lambda} = \\frac{{\\int\_{\\mathcal{F}}\\left( {\\rho\_{Z}(T,Q) - \\rho\_{U}} \\right)}dTdQ}{{\\int\_{\\mathcal{F}}\\rho\_{Z}}(T,Q)\\left( {\\rho\_{Z}(T,Q) - \\rho\_{U}} \\right)dTdQ}.} \\\\ \\end{array}$$  
(3.130)

### 3.7.3Implementation of random projectors and their numerical characteristics

A standard approach to implement random projectors is to sample the entropy-optimal PDFs *P*(*Q*), *W*(*T*) and *F*(*T*, *Q*), which preserve the inter-vector distance of the data matrix in its projector matrices. As the result of sampling, the PDFs are transformed into a sequence of random projector matrices:

  
$$\\begin{array}{r} \\left. F^{\*}(T,Q)\\Rightarrow(T^{(1)},Q^{(1)}),(T^{(2)},Q^{(2)}),\\ldots,(T^{(N)},Q^{(N)}),\\ldots \\right. \\\\ \\end{array}$$  
(3.134)

A general method for generating random sequences with a given PDF was proposed in \[36\]. The balance property (see above) may be not satisfied for each separate element of this sequence, but it will surely hold “on the average.” Therefore, the empirical projector for implementation can be the matrix

  
$$\\begin{array}{r} {\\overline{T} \\approx \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}T^{(i)}},\\text{\\quad\\quad}\\overline{Q} \\approx \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}Q^{(i)}}.} \\\\ \\end{array}$$  
(3.135)

The exact values of the “average” projector matrices are given by

  
$$\\begin{array}{r} {\\overline{T} = {\\int\_{\\mathcal{F}}T}\\, F(T,Q)dTdQ,\\text{\\quad\\quad}\\overline{Q} = {\\int\_{\\mathcal{F}}Q}\\, F(T,Q)dTdQ.} \\\\ \\end{array}$$  
(3.136)

Although the integrals in these equalities are multidimensional, integrands are exponentials of polynomials. This often provides analytical formulas for calculating multidimensional integrals.

In addition, the problem of calculating multidimensional integrals can be solved by approximate methods, such as the Monte Carlo simulations and the polynomial approximation of integrands.

The PDF *F*^(\*)(*T*, *Q*) is defined on the bounded set ℱ (3.122). Therefore, the projector for implementation can be the pair of matrices

  
$$\\begin{array}{r} {(T^{\*},Q^{\*}) = \\arg\\max\_{\\mathcal{F}}F(T,Q).} \\\\ \\end{array}$$  
(3.137)

### 3.7.4Random projector matrices with given values of elements

**1. The set of (0, 1)\-projector matrices and its ordering**

Consider a projection procedure onto the space *R*[(*m*)]^(*r*) performed by a projector matrix *Q*[(*s* × *r*)] with random elements taking values 0 or 1.

Write this matrix as a row vector of length *sr*. The number of different sequences composed of zeros and ones, i.e., the number of different row vectors, is *N* = 2^(*r**s*). For example, for *s* = 3 and *r* = 1, there are 8 vectors of this type:

  
$$\\begin{array}{r} {000,100,010,001,110,011,101,111;} \\\\ \\end{array}$$  

for *s* = 4 and *r* = 1, 16 vectors of this type:

  
$$\\begin{array}{r} {0000,1000,0100,0010,0001,1100,0110,0011,} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {1001,0101,1010,1111,1110,0111,1011,1101.} \\\\ \\end{array}$$  

For a projector matrix *Q*[(*s* × *r*)], there exists a finite set *ℚ* of its (0, 1)\-realizations:

  
$$\\begin{array}{r} {{\\mathbb{Q}} = \\left\\{ Q^{(1)},\\ldots,Q^{(N)} \\right\\},\\text{\\quad\\quad}N = 2^{sr}.} \\\\ \\end{array}$$  
(3.138)

Suppose that the realizations are random, then their probabilistic properties can be characterized by a discrete distribution function (DDF) *W*(*α*) with a discrete support *α* ∈ 𝒜 = \[1, *N*\], where

  
$$\\begin{array}{r} {W(\\alpha) = \\mathbf{w} = \\left\\{ w\_{\\alpha}\\,\\alpha = \\overline{1,N} \\right\\}.} \\\\ \\end{array}$$  
(3.139)

The projector matrix is given by

  
$$\\begin{aligned} {Y\_{(m \\times r)}^{(\\alpha)} = \\left( \\begin{array}{l} \\mathbf{y}\_{(1)}^{(\\alpha)} \\\\ \\cdots \\\\ \\mathbf{y}\_{(m)}^{(\\alpha)} \\\\ \\end{array} \\right)} & {= U\_{(m \\times s)}Q\_{(s \\times r)}^{(\\alpha)};\\quad y\_{j}^{(\\alpha,i)} = {\\sum\\limits\_{k = 1}^{s}u\_{ik}}q\_{kj}^{(\\alpha)},} \\\\ & {\\quad i = \\overline{1,m};\\, j = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(3.140)

The indicator of compactness of the set 𝔜^((*α*)) has the form

  
$$\\begin{array}{r} \\left. \\rho\_{Y}^{(\\alpha)}(Q) = \\frac{2}{m(m - 1)}{\\sum\\limits\_{(\\kappa,\\beta) = 1,\\mspace{2mu}\\kappa \\neq \\beta}^{m}\\varrho^{(\\alpha)}}(\\mathbf{y}^{(\\kappa)},\\mathbf{y}^{(\\beta)}\\, \\middle| \\, Q\_{(s \\times r)}^{(\\alpha)}). \\right. \\\\ \\end{array}$$  
(3.141)

Order the sequence (3.138) in accordance with the sequence of inequalities

  
$$\\begin{array}{r} {0 < \\rho\_{Y}^{(1)}(Q) < \\rho\_{Y}^{(2)}(Q) < \\cdots < \\rho\_{Y}^{(N)}(Q).} \\\\ \\end{array}$$  
(3.142)

**2. *MEE*\-estimate of DDFs**

The *MEE*\-estimate of the DDF *W*(*α*) is calculated as

  
$$\\begin{array}{r} \\left. H(\\mathbf{w}) = - {\\sum\\limits\_{\\alpha = 1}^{N}w\_{\\alpha}}\\ln w\_{\\alpha}\\Rightarrow\\max, \\right. \\\\ \\end{array}$$  
(3.143)

subject to the following constraints:

*   —the normalization conditions
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{\\alpha = 1}^{N}w\_{\\alpha}} = 1;} \\\\ \\end{array}$$  
    (3.144)
    
*   —the balance conditions for the indicators of compactness
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{\\alpha = 1}^{N}w\_{\\alpha}}\\,\\rho\_{Y}^{(\\alpha)}(Q) = \\rho\_{U}.} \\\\ \\end{array}$$  
    (3.145)
    

The problem (3.143)–(3.145) is a finite-dimensional constrained optimization problem with a concave objective function (information entropy) and linear equality constraints.

Consider the Lagrange function

  
$$\\begin{array}{r} {L(\\mathbf{w},\\lambda) = H(\\mathbf{w}) + \\mu\\left( {1 - {\\sum\\limits\_{\\alpha = 1}^{N}w\_{\\alpha}}} \\right) + \\lambda\\left( {\\rho\_{U} - {\\sum\\limits\_{\\alpha = 1}^{N}w\_{\\alpha}}\\rho\_{Y}^{(\\alpha)}(Q)} \\right).} \\\\ \\end{array}$$  
(3.146)

From the first-order optimality conditions, for this function, it follows that the entropy-optimal discrete probability distribution is given by

  
$$\\begin{array}{r} {w\_{\\alpha}^{\*} = \\frac{\\exp\\left( {- \\lambda\\rho\_{Y}^{(\\alpha)}(Q)} \\right)}{{\\sum\\limits\_{\\alpha = 1}^{N}\\exp}\\left( {- \\lambda\\rho\_{Y}^{(\\alpha)}(Q)} \\right)},\\text{\\quad\\quad}\\alpha = \\overline{1,N},} \\\\ \\end{array}$$  
(3.147)

where the parameter *λ* satisfies the equation

  
$$\\begin{array}{r} {{\\sum\\limits\_{\\alpha = 1}^{N}\\exp}( - \\lambda\\rho\_{Y}^{(\\alpha)}(Q))(\\rho\_{Y}^{(\\alpha)}(Q) - \\rho\_{U}) = 0,\\text{\\quad\\quad} - \\infty < \\lambda < \\infty.} \\\\ \\end{array}$$  
(3.148)

Introduce the change of variable *z* = exp ( − *λ*). Then equation (3.148) can be written as

  
$$\\begin{array}{r} {\\varphi(z) = {\\sum\\limits\_{\\alpha = 1}^{N}z^{h\_{\\alpha}}}\\, c\_{\\alpha} = 0,\\,\\,\\, z \\geq 0;\\quad c\_{\\alpha} = (h\_{\\alpha} - \\rho\_{U}),\\,\\, h\_{\\alpha} = \\rho\_{Y}^{(\\alpha)}.} \\\\ \\end{array}$$  
(3.149)

### 3.7.5Choice of appropriate projector matrix from *ℚ* (3.138)

The entropy-optimal DDF $W^{\*}(\\alpha) = w\_{\\alpha}^{\*},\\,\\alpha = \\overline{1,N},$ (3.149) characterizes the probabilities of implementing the elements (projector matrices) from the set *ℚ* (3.138). However, for obtaining a particular projector matrix *Y*[(*m* × *r*)], a particular projector matrix from the set *ℚ* is needed. Particular matrices can be chosen using different strategies as follows.

*1. Projector matrix with maximum probability* Let the difference *Δ*[*ρ*] = *ρ*[*Y*]^((*N*)) − *ρ*[*Y*]^((1)) in (3.142) be sufficiently large. This means that the maximum value of probability in the DDF (3.149) is appreciably greater than the minimum one. Then the implemented projector matrix has the number

  
$$\\begin{array}{r} {\\alpha^{\*} = \\arg\\max\_{1 \\leq \\alpha \\leq N}w\_{\\alpha}^{\*}.} \\\\ \\end{array}$$  
(3.156)

*2. Average projector matrix* If *Δ*[*ρ*] = *ρ*[*Y*]^((*N*)) − *ρ*[*Y*]^((1)) is small, the sequence {*ρ*^((*α*))} increases with a low rate. In this case, the projector matrix for implementation should be obtained by averaging:

![](images/math3_601.jpg)

where ⌊ • ⌋ denotes the integer part of a number  • .

*3. Median projector matrix* is given by

  
$$\\begin{array}{r} {{\\sum\\limits\_{\\alpha = 1}^{\\alpha^{\*}}w\_{\\alpha}^{\*}} = {\\sum\\limits\_{\\alpha = \\alpha^{\*} + 1}^{N}w\_{\\alpha}^{\*}}.} \\\\ \\end{array}$$  
(3.158)

*4. Averaging of projector matrices* This strategy consists of the following stages. In the first stage, subsets of projector matrices with definite properties are selected. In the second stage, a subset of the corresponding projector matrices is formed. Then the average projector matrix is calculated.

Whereas the second and third stages are related to standard calculations for mathematical statistics, the first one requires additional comments. The subsets of projector matrices are selected in accordance with rules reflecting their desired properties. Depending on the rule for selecting such subsets, the so-called variance and interquartile subsets of projector matrices will be studied below.

First, consider *the variance subsets*. For this, find the root mean square (RMS) value of the variable *α*:

![](images/math3_605.jpg)

Define the variance interval

  
$$\\begin{array}{r} {\\mathcal{I}\_{\\alpha} = \\lbrack\\alpha^{\*} - \\sigma\_{\\alpha}^{\*},\\alpha^{\*} + \\sigma\_{\\alpha}^{\*}\\rbrack.} \\\\ \\end{array}$$  
(3.160)

The variance subset has the form

  
$$\\begin{array}{r} {\\widetilde{\\mathbb{Q}} = \\left\\{ Q^{(\\alpha^{\*} - \\sigma\_{\\alpha}^{\*})},\\ldots,Q^{(\\alpha^{\*} + \\sigma\_{\\alpha}^{\*})} \\right\\}.} \\\\ \\end{array}$$  
(3.161)

For each element of this subset, calculate the corresponding projector matrices:

  
$$\\begin{array}{r} {\\widetilde{\\mathcal{Y}} = \\left\\{ Y\_{(m \\times r)}^{(\\alpha^{\*} - \\sigma\_{\\alpha}^{\*})},\\ldots,Y\_{(m \\times r)}^{(\\alpha^{\*} + \\sigma\_{\\alpha}^{\*})} \\right\\}.} \\\\ \\end{array}$$  
(3.162)

In the last stage, find the average projector matrix on the variance set:

  
$$\\begin{array}{r} {{\\overline{Y}}\_{(m \\times r)}^{D} = \\frac{1}{2\\sigma\_{\\alpha}^{\*}}{\\sum\\limits\_{\\alpha = \\alpha^{\*} - \\sigma\_{\\alpha}^{\*}}^{\\alpha^{\*} + \\sigma\_{\\alpha}^{\*}}Y\_{(m \\times r)}^{(\\alpha)}}.} \\\\ \\end{array}$$  
(3.163)

Now analyze the formation of *the interquantile subsets*. The entropy-optimal probability distribution function (see (3.147)) has the form

  
$$\\begin{array}{r} {F^{\*}(\\kappa) = {\\sum\\limits\_{\\alpha = 1}^{\\kappa}w\_{\\alpha}^{\*}},\\text{\\quad\\quad}\\kappa \\in \\lbrack 0,1\\rbrack.} \\\\ \\end{array}$$  
(3.164)

Recall that the *κ*^(\*)\-quartile of a random variable *α* is the set 𝒜^((*κ*^(\*))) of its values \[1, *κ*^(\*)\].

Consider two quartile sets, 𝒜^((*κ*[1]^(\*))) and 𝒜^((*κ*[2]^(\*))), where *κ*[1]^(\*) > *κ*[2]^(\*). The subsets of projector matrices are associated with each of these sets:

  
$$\\begin{array}{r} {{\\mathbb{Q}}(\\kappa\*\_{1}) = \\left\\{ Q^{(1)},\\ldots,Q^{(\\alpha(\\kappa\_{1}^{\*}))} \\right\\},} \\\\ {{\\mathbb{Q}}(\\kappa\*\_{2}) = \\left\\{ Q^{(1)},\\ldots,Q^{(\\alpha(\\kappa\_{2}^{\*}))} \\right\\}.} \\\\ \\end{array}$$  
(3.165)

Construct the subset of projector matrices

  
$$\\begin{array}{r} {{\\mathbb{Q}}(\\kappa\_{1}^{\*} - \\kappa\_{2}^{\*}) = \\left\\{ Q^{(\\alpha(\\kappa\_{2}^{\*}))},\\ldots,Q^{(\\alpha(\\kappa\_{1}^{\*}))} \\right\\},} \\\\ \\end{array}$$  
(3.166)

which is the (*κ*[1]^(\*) − *κ*[2]^(\*))\-interquantile subset ℐ^((*κ*[1]^(\*) − *κ*[2]^(\*))) of the entropy-optimal projector matrices. The number of elements in this subsets is *M*[(*κ*[1]^(\*) − *κ*[2]^(\*))] = *α*(*κ*[1]^(\*)) − *α*(*κ*[2]^(\*)).

For each element of the subset 𝒬(*κ*[1]^(\*) − *κ*[2]^(\*)) (3.166), calculate the corresponding projector matrices

  
$$\\begin{array}{r} {\\mathcal{Y}(\\kappa\_{1}^{\*} - \\kappa\_{2}^{\*}) = \\left\\{ Y\_{(m \\times r)}^{\\alpha(\\kappa\_{2}^{\*})},\\ldots,Y\_{(m \\times r)}^{\\alpha(\\kappa\_{1}^{\*})} \\right\\}.} \\\\ \\end{array}$$  
(3.167)

The average projector matrix on the subset ℐ^((*κ*[1]^(\*) − *κ*[2]^(\*))) is given by

  
$$\\begin{array}{r} {{\\overline{Y}}\_{(m \\times r)}^{K} = \\frac{1}{M\_{(\\kappa\_{1}^{\*} - \\kappa\_{2}^{\*})}}{\\sum\\limits\_{\\alpha = \\alpha(\\kappa\_{2}^{\*})}^{\\alpha(\\kappa\_{1}^{\*})}Y\_{(m \\times r)}^{\\alpha}}.} \\\\ \\end{array}$$  
(3.168)

Averaging over interquantile sets yields projector matrices with given (*κ*[1], *κ*[2])\-quantiles.

# CHAPTER 4 RANDOMIZED PARAMETRIC MODELS

DOI: [10.1201/9781003306566-4](https://doi.org/10.1201/9781003306566-4)

An important component of the RML procedures is a model with random parameters, which will be called *the randomized parametric model (RPM)*. In this way, we emphasize that the random parameters in this model are artificial and have optimal probabilistic characteristics. The optimality of the probabilistic characteristics of the RPM parameters is considered in terms of an quality functional and a set of admissible parameter values in a specific problem. As the RML procedures are used for a wide range of machine learning problems, we will study static and dynamics RPMs.

## 4.1Definition, Characteristics and Classification

A randomized parametric model (RPM) transforms input data into an *ensemble* of output data, which is generated by the model in accordance with given probability density functions (PDFs) of its parameters.

Consider a case in which the input data represent a one-dimensional array, i.e., a vector **x** ∈ *R*^(*n*), as illustrated in [Fig. 4.1(a)](#chapter4.xhtml#f4_1). Its elements are some characteristics *x*[1], …, *x*[*n*] of a studied object. An RPM has randomized parameters **a** ∈ *R*^(*r*) whose probabilistic properties are described by a PDF *P*(**a**). An RPM generates an ensemble 𝒴 of vectors **y** ∈ *R*^(*m*) with the given PDF *P*(**a**).

Next, let the input data be defined by a two-dimensional array, i.e., a matrix *X* composed of column vectors $\\mathbf{x}^{(j)},\\, j = \\overline{1,s}$ (see [Fig. 4.1(b)](#chapter4.xhtml#f4_1)). For example, such an array results from measuring the object's state vector at *s* different times. For each measured vector **x**^((*j*)) from the input array, an RPM with the above-mentioned properties generates an ensemble 𝒴^((*j*)) of random vectors **y**^((*j*)) ∈ *R*^(*m*) with the given PDF *P*(**a**).

![Figure 4.1](images/fig4_1.jpg)

[Figure 4.1](#chapter4.xhtml#f4_1b)

As a last example, consider a set 𝒳[*τ*] composed of three-dimensional input data arrays containing measurements of a vector function $\\mathbf{x}^{(j)}(\\tau),\\, j = \\overline{1,s},$ where *τ* ∈ 𝒯 = \[0, *T*\]. Here, for each measurement, an RPM generates three-dimensional ensembles 𝒴^((*j*)) of random vector functions **y**^((*j*))(*t*), *t* ≥ *τ*, with the given PDF *P*(**a**).

In all examples above, an RPM transforms deterministic input data into an ensemble of randomized output data. Such a transformation will be characterized by a mapping

  
$$\\begin{array}{r} {\\mathbb{M}(P(\\mathbf{a}),\\tau,t,T) = :\\mathcal{X}\_{\\tau}\\overset{P(\\mathbf{a})}{\\rightarrow}\\hat{\\mathcal{Y}},} \\\\ \\end{array}$$  
(4.1)

and a corresponding RPM will be assigned the “*input–output ensemble*” *\[I–OE\]* class; see [Fig. 4.2(a)](#chapter4.xhtml#f4_2).

![Figure 4.2](images/fig4_2.jpg)

[Figure 4.2](#chapter4.xhtml#f4_2b)

Sometimes, it is useful to structure the mapping 𝕄(*P*(**a**), *τ*, *T*). In particular, we can represent it as two mappings 𝕄[1](*P*[1](**a**^((1))), *τ*, *λ*, *t*, *T*) and 𝕄[2](*P*[2](**a**^((2))), *t*, *λ*) within a feedback loop (see [Fig. 4.2(b)](#chapter4.xhtml#f4_2)), i.e.,

  
$$\\begin{aligned} {\\mathbb{M}\_{1}(P\_{1}(\\mathbf{a}^{(1)}),\\tau,\\lambda,t,T)} & {= :(X\_{\\tau},{\\hat{\\mathcal{Z}}}\_{\\lambda})\\overset{P\_{1}(\\mathbf{a}^{(1)})}{\\rightarrow}\\mathcal{Y};} \\\\ {\\mathbb{M}\_{1}(P\_{2}(\\mathbf{a}^{(2)}),t,\\lambda)} & {= :\\hat{\\mathcal{Y}}\\overset{P\_{2}(\\mathbf{a}^{(2)})}{\\rightarrow}{\\hat{\\mathcal{Z}}}\_{\\lambda}.} \\\\ \\end{aligned}$$  
(4.2)

Here (*λ*, *τ*, *t*) ∈ 𝒯 = \[0, *T*\]. The models described by the mappings (4.1, 4.2) will be classified as the “*(input, feedback)–output ensemble*” *\[(I,FB)–OE\]* RPMs.

These RPMs have randomized interval-time parameters, that is,

  
$$\\begin{array}{r} {\\mathbf{a} \\in \\mathcal{A} = \\lbrack\\mathbf{a}^{-},\\mathbf{a}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{a}^{\\pm} = \\left\\{ a\_{1}^{\\pm},\\ldots,a\_{r}^{\\pm} \\right\\}.} \\\\ \\end{array}$$  
(4.3)

In addition, the RPMs of both classes will be divided into subclasses, in terms of their temporal properties and mathematical modeling methods. Based on the first classification attribute, there exist static and dynamic RPMs. For the static models, *τ* = *t* in the mapping (4.1), i.e., an ensemble generated by such a model at a time *t* depends on the data at this time only. In the dynamic RPMs, an ensemble $\\hat{\\mathcal{Y}}$ depends on the data *X*[*τ*], where *t*[0] ≤ *τ* ≤ *t*.

For further classification in terms of mathematical modeling methods, we will employ a standard approach by considering linear and nonlinear models, functions and functionals, differential and integral equations, and different approximations of nonlinearities. The classification tree is demonstrated in [Fig. 4.3](#chapter4.xhtml#f4_3).

![Figure 4.3](images/fig4_3.jpg)

[Figure 4.3](#chapter4.xhtml#f4_3b)

## 4.2“Single Input–Ensemble Output” Randomized Parametric Model

### 4.2.1Static models

For this class of models, an ensemble of output data at a time *t* depends on the input data at this time and also on a realization of the randomized parameters. Therefore, the index *t* can be omitted, and such mappings can be described using vector functions of the random argument **a**.

Consider an input data array, which is characterized by a matrix $\\left. X = \\lbrack x\_{ij}\\, \\middle| \\, i = \\overline{1,n},\\, j = \\overline{1,s}\\rbrack. \\right.$ This array consists of *s* measurements of an input vector **x**^((*j*)) = {*x*[1]^((*j*)),…,*x*[*n*]^((*j*))}, where $j = \\overline{1,s}.$ The elements of this vector are the elements of column *j* in the matrix *X*.

A static RPM transforms the input matrix *X* into an output matrix $\\left. \\hat{Y} = \\lbrack{\\hat{y}}\_{kj}\\, \\middle| \\, k = \\overline{1,m},\\, j = \\overline{1,s}\\rbrack. \\right.$ The columns of this matrix are the elements of the *j*th vector ${\\hat{\\mathbf{y}}}^{(j)} = \\left\\{ {\\hat{y}}\_{1}^{(j)},\\ldots,{\\hat{y}}\_{m}^{(j)} \\right\\},$ where $j = \\overline{1,s}.$

Introduce a matrix $\\left. A = \\lbrack a\_{hp}\\, \\middle| \\, h = \\overline{1,m},p = \\overline{1,n}\\rbrack, \\right.$ composed of randomized parameters. The elements of this matrix are random variables taking values within the intervals

  
$$\\begin{array}{r} {\\mathcal{A}\_{hp} = \\lbrack a\_{hp}^{-},a\_{hp}^{+}\\rbrack,} \\\\ \\end{array}$$  
(4.4)

which form the (*m* × *s*)\-dimensional parallelepiped

  
$$\\begin{array}{r} {\\mathcal{A} = \\otimes\_{h = 1}^{m} \\otimes\_{p = 1}^{n}\\mathcal{A}\_{hp}.} \\\\ \\end{array}$$  
(4.5)

By assumption, there exists a continuously differentiable PDF *P*(*A*) on this set.

A relation between the input *X* and the output ensemble $\\hat{\\mathcal{Y}}$ of a static RPM is described by a vector function ℱ that has the randomized parameters *A* with the PDF *P*(*A*), i.e.,

  
$$\\begin{array}{r} {\\hat{\\mathcal{Y}} = \\mathcal{F}\\left( {X,A,P(A)} \\right).} \\\\ \\end{array}$$  
(4.6)

In other words, for a fixed input data array *X*, a static RPM generates an ensemble $\\hat{\\mathcal{Y}}$ of random matrices *Ŷ* with the above-mentioned properties.

An important special case of the RPMs (4.6) is the model with *n* inputs and one output. In this case, the model generates a vector $\\hat{\\mathbf{y}} = \\left\\{ y\_{1}^{(1)},\\ldots,y\_{m}^{(s)} \\right\\},$ and its randomized parameters are characterized by a vector **a** = {*a*[1],…,*a*[*r*]} with interval-type elements

  
$$\\begin{array}{r} {a\_{h} \\in \\mathcal{A}\_{h} = \\lbrack a\_{h}^{-},a\_{h}^{+}\\rbrack,\\text{\\quad\\quad}\\mathcal{A} = \\otimes\_{h = 1}^{r}\\mathcal{A}\_{h}.} \\\\ \\end{array}$$  
(4.7)

Then equality (4.6) takes the form

  
$$\\begin{array}{r} {\\hat{\\mathcal{Y}} = \\mathcal{F}\\left( {X,\\mathbf{a},P(\\mathbf{a})} \\right),} \\\\ \\end{array}$$  
(4.8)

where $\\hat{\\mathcal{Y}}$ denotes an ensemble of random vectors $\\hat{\\mathbf{y}}.$

1. Linear static RPMs. This class of the models involves a linear vector function **F** (4.6) of the form

  
$$\\begin{array}{r} {\\hat{\\mathcal{Y}} = A\\, X,} \\\\ \\end{array}$$  
(4.9)

where *A* is a matrix of dimensions (*m* × *n*) with the randomized elements (4.4, 4.5) and the probabilistic properties characterized by a PDF *P*(*A*).

If the RPM (4.6) has *n* inputs and one output, then the output ensemble consists of the values of a random variable

  
$$\\begin{array}{r} {\\hat{y} = \\left\\langle \\mathbf{x},\\mathbf{a} \\right\\rangle.} \\\\ \\end{array}$$  
(4.10)

2.Nonlinear static RPMs. The nonlinear RPMs form a significantly wider class than the linear ones. The nonlinear processes that occur in nature are modeled using appropriate laws. If a certain relation between an input and output of an object surely exists but its form is unknown, then a more of less universal approach lies in approximation. Here it is necessary to define a structure and parameters of an approximating function. As a result, to design a nonlinear static RPM means to search for appropriate parameter values. Consider some types of approximations and also the underlying hypotheses on the properties of the “Single Input–Ensemble Output” relations.

*2.1. Analytical nonlinearities.* By a prevailing hypothesis, there exists an analytical relation between the input and output matrices, *X* and *Y*. This hypothesis allows us to perform approximation using the *Taylor monomial*

  
$$\\begin{array}{r} {\\hat{\\mathcal{Y}} = {\\sum\\limits\_{h = 1}^{R}B^{(h)}}\\, Z^{(h)}.} \\\\ \\end{array}$$  
(4.11)

Here *B*^((*h*)) denotes a matrix of dimensions (*s* × *φ*(*h*)) with interval-type randomized elements, and *Z*^((*h*)) is a matrix of dimensions (*φ*(*h*)) × *r* whose entries represent the products of degree *h* from the elements of the input matrix *X*. The matrices *B*^((*h*)) are defined on the intervals

  
$$\\begin{array}{r} {\\mathcal{B}\_{h} = \\lbrack\\mathcal{B}\_{h}^{-},\\mathcal{B}\_{h}^{+}\\rbrack,\\text{\\quad\\quad}h = \\overline{1,R}.} \\\\ \\end{array}$$  
(4.12)

For a one-dimensional static object (with one input and one output), equality (4.11) takes the simpler form

  
$$\\begin{array}{r} {\\hat{y} = {\\sum\\limits\_{h = 1}^{R}b\_{h}}x^{h},} \\\\ \\end{array}$$  
(4.13)

where the parameters *b*[1], …, *b*[*R*] are randomized and independent. The domain of definition of the parameters *b*[1], …, *b*[*R*] is given by

  
$$\\begin{array}{r} {b\_{h} \\in \\mathcal{B}\_{h} = \\lbrack b\_{h}^{-},b\_{h}^{+}\\rbrack,\\text{\\quad\\quad}h = \\overline{1,R}.} \\\\ \\end{array}$$  
(4.14)

*2.2. Continuous nonlinearities.* In fact, the existence of an analytical relation between an input and output of a static nonlinearity is a bold hypothesis. Following a more realistic approach, assume that the input is bounded and the nonlinearity *Φ*(*x*) has no discontinuities of the second kind (infinite jumps). Numerous approximation methods with orthogonal polynomials were developed on the basis of these hypotheses.

Recall some fundamental concepts of the corresponding methods. Consider a one-dimensional static object with a bounded input and a nonlinear characteristic that has no discontinuities of the second kind:

  
$$\\begin{array}{r} {x^{-} \\leq x \\leq x^{+}.} \\\\ \\end{array}$$  

By assumption, there exists a certain function *w*(*x*) on this interval, which is often interpreted as a weight characteristic for the values of the variable *x*. Since the nonlinearity *Φ*(*x*) of the static object is considered on the same interval without discontinuities of the second kind,

  
$$\\begin{array}{r} {{\\int\_{x^{-}}^{x^{+}}w}(x)\\Phi^{2}(x)dx < \\infty.} \\\\ \\end{array}$$  

To obtain orthogonal polynomials, choose a system of power functions 1, *x*, *x*², … and apply the following orthogonalization procedure:

  
$$\\begin{array}{r} {\\psi\_{0}(x) = c\_{0},} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {\\psi\_{1}(x) = c\_{0} + c\_{1}x,} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {\\psi\_{2}(x) = c\_{0} + c\_{1}x + c\_{2}x^{2},} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {\\cdots = \\cdots + \\cdots + \\cdots} \\\\ \\end{array}$$  

The coefficients *c*[0], *c*[1], *c*[2], … in these formulas are adjusted so that

  
$$\\begin{array}{r} {{\\int\_{x^{-}}^{x^{+}}w}(x)\\psi\_{i}^{2}(x)dx = 1,\\text{\\quad\\quad}i = 0,1,2,\\ldots} \\\\ \\end{array}$$  

and

  
$$\\begin{array}{r} {{\\int\_{x^{-}}^{x^{+}}w}(x)\\psi\_{i}(x)\\psi\_{i - 1}(x)dx = 0,\\text{\\quad\\quad}i = 1,2,\\ldots} \\\\ \\end{array}$$  

This procedure yields a system of orthogonal polynomials. The weight function *w*(*x*) defines the class of a corresponding orthonormal polynomial. Some classes are presented in [Table 4.1](#chapter4.xhtml#t4_1).

 [Table 4.1:](#chapter4.xhtml#t4_1b) Orthonormal polynomials. 

 
|  |
| --- |
| Class || Interval || *w*(*x*) || Polynomial |
| Lagerra || \[0, ∞) || *e*^( − *x*) || 1, 1 − *x*, 1 − 2*x* + *x*²/2, ... |
| --- | --- | --- | --- |
| Hermit || ( − ∞, ∞) || *e*^( − *x*²) || 1, 2*x*, 4*x*² − 2, ... |
| Legendre || \[ − 1, 1\] || 1 || 1, *x*, (3*x*² − 1)/2, ... |
| Chebyshev || \[ − 1, 1\] || $1/\\sqrt{1 - x^{2}}$ || 1, *x*, 2*x*² − 1, ... |
|  |

Using the system of orthonormal polynomials, construct an approximating polynomial with the parameters *a*[0], …, *a*[*R*] by

  
$$\\begin{array}{r} {\\hat{\\Phi}(x) = {\\sum\\limits\_{i = 0}^{R}a\_{i}}\\psi\_{i}(x).} \\\\ \\end{array}$$  
(4.15)

In contrast to the classical approach to approximation, the parameters of an approximating function will be treated as randomized ones taking values within an interval \[**a**^−, **a**^+\].

### 4.2.2Functional description of dynamic models

An output ensemble of dynamic models at a time *t* is characterized by a mapping 𝕄\[*P*(**a**), *τ*, *t*\] of the form (4.1) and depends on the input data on a time interval \[*t* − *τ*, *t*\] and a realization of the randomized parameters.

Denote by **x**(*τ*) an input vector composed of independent observations *x*[1](*τ*), …, *x*[*n*](*τ*) that are defined on a time interval 𝒯[*t*] = \[0, *t*\], where *τ* ∈ 𝒯[*t*]. At each time *t* > 0, the model outputs a vector $\\hat{\\mathbf{y}}(t)$ composed of observations *ŷ*[1](*t*), …, *ŷ*[*m*](*t*), where *t* ∈ 𝒯 = \[0, *T*\]. A relation between the input **x**(*τ* | *τ*∈𝒯[*t*]) and the output $\\hat{\\mathbf{y}}(t)$ is described by a functional ℬ, i.e.,

  
$$\\begin{array}{r} \\left. \\hat{\\mathbf{y}}(t) = \\mathcal{B}(\\mathbf{x}(\\tau),\\mathbf{a}\\, \\middle| \\,\\tau \\in \\mathcal{T}\_{t}),\\text{\\quad\\quad}t \\in \\mathcal{T} = \\lbrack 0,T\\rbrack. \\right. \\\\ \\end{array}$$  
(4.16)

Assume that this functional is parameterized by a vector **a** = {*a*[1],…,*a*[*r*]} of random elements that belong to intervals

  
$$\\begin{aligned} \\mathcal{A}\_{i} & {= \\lbrack a\_{i}^{-},a\_{i}^{+}\\rbrack,\\text{\\quad\\quad}i \\in \\lbrack 1,r\\rbrack;} \\\\ \\mathcal{A} & {= {\\prod\\limits\_{i = 1}^{r}\\mathcal{A}\_{i}}.} \\\\ \\end{aligned}$$  
(4.17)

Three classes of the dynamic “Single Input–Ensemble Output” RPMs will be considered, namely, the linear ones, as well as the nonlinear ones with the power and polynomial nonlinearities.

### 4.2.3Linear dynamic models

Consider a dynamic RPM with an input **x**(*τ*), *τ* ∈ 𝒯[*t*] and an output $\\hat{\\mathbf{y}}(t),\\, t \\in \\mathcal{T}.$ The input vector elements $x\_{i}(\\tau),\\, i = \\overline{1,n},$ are *continuous time-varying functions*. A relation between the input and output of this RPM is described by a *linear* functional ℬ with the parameters **a** (4.16), i.e.,

  
$$\\begin{array}{r} {\\hat{\\mathbf{y}}(t) = {\\int\_{0}^{t}B}(t,\\tau,\\,\\mathbf{a})\\mathbf{x}(\\tau)d\\tau.} \\\\ \\end{array}$$  
(4.18)

In this formula, the matrix *B*(*t*, *τ*, **a**) of dimensions (*m* × *n*) consists of pulse characteristics $\\left. \\lbrack b\_{ij}(t,\\tau\\, \\middle| \\,\\mathbf{a}^{(ij)}),\\, \\middle| \\, i = \\overline{1,m},\\, j = \\overline{1,n}\\rbrack \\right.$ with random parameters **a**^((*i**j*)) = {*a*[1]^((*i**j*)),…,*a*[*k*[*i**j*]]^((*i**j*))}, where *k*[*i**j*] is the number of parameters for a pulse characteristic *b*[*i**j*](*t*, *τ*).

According to a general concept, the parameters **a**^((*i**j*)) are interval-type, i.e.,

  
$$\\begin{array}{r} {\\mathbf{a}^{(ij)} \\in \\mathcal{A}^{(ij)} = \\lbrack\\mathbf{a}\_{-}^{(ij)},\\mathbf{a}\_{+}^{(ij)}\\rbrack,\\quad\\mathbf{a} \\in \\mathcal{A} = {\\prod\\limits\_{i = 1}^{m}{\\prod\\limits\_{j = 1}^{n}\\mathcal{A}^{(ij)}}}.} \\\\ \\end{array}$$  
(4.19)

The model (4.19) generates an ensemble ${\\hat{\\mathcal{Y}}}\_{\\mathcal{T}}$ of random trajectories $\\hat{\\mathbf{y}}(t),\\, t \\in \\mathcal{T}.$ These pulse characteristics can be parameterized in different ways. Some of them will be discussed below.

*1.1. Given functions with unknown parameters.* As a rule, pulse characteristics are exponential functions or harmonic functions with exponential decay, i.e.,

  
$$\\begin{array}{r} {b\_{ij}(t,\\tau) = \\alpha\_{ij}(t)\\exp\\left( {- \\beta\_{ij}(t)\\tau} \\right)\\text{or}b\_{ij}(t,\\tau)\\exp\\left( {- \\beta\_{ij}\\tau} \\right)\\,\\sin(\\omega\_{ij}(t)\\tau + \\phi\_{ij}(t)),} \\\\ \\end{array}$$  
(4.20)

where, e.g., time-varying parameters have the form

  
$$\\begin{aligned} {\\alpha\_{ij}(t)} & {= \\alpha\_{ij}^{0} + \\alpha\_{ij}^{1}t;\\quad\\beta\_{ij}(t) = \\beta\_{ij}^{0} + \\beta\_{ij}^{1}t,} \\\\ {\\omega\_{ij}(t)} & {= \\omega\_{ij}^{0}\\ln t;\\text{\\quad\\quad}\\phi\_{ij}(t) = \\phi\_{ij}^{0} + \\phi\_{ij}^{1}t.} \\\\ \\end{aligned}$$  
(4.21)

In these expressions, *α*[*i**j*]⁰, *α*[*i**j*]¹, *β*[*i**j*]⁰, *β*[*i**j*]¹, *ω*[*i**j*]⁰, *ϕ*[*i**j*]⁰ and *ϕ*[*i**j*]¹ are random variables that take values within corresponding intervals.

*1.2. Approximation by given family of functions with unknown weights.* Consider a family ℛ[*v*] of *v* deterministic functions, further referred to as the *basis* functions:

  
$$\\begin{array}{r} {\\mathcal{R}\_{v} = \\left\\{ \\phi\_{1}(t,\\tau),\\ldots,\\phi\_{v}(t,\\tau) \\right\\}.} \\\\ \\end{array}$$  
(4.22)

Then the pulse characteristics are written as

  
$$\\begin{array}{r} {b\_{ij}(t,\\tau) = {\\sum\\limits\_{k = 1}^{K\_{ij}}b\_{k}^{(ij)}}\\,\\phi\_{k}(t,\\tau),} \\\\ \\end{array}$$  
(4.23)

where the coefficients *b*[*k*]^((*i**j*)) are randomized independent variables that take values within some intervals.

To a large extent, a proper choice of basis functions depends on the properties of an object under study. Here a widespread approach is to employ the families of basis functions formed by the exponential functions exp (*α*(*t*, *τ*)), the polynomial-exponential functions *β**t*^(*p*)exp (*α*(*t*, *τ*)) (with integers *p*), or the polynomial-exponential-harmonic functions *β**t*^(*p*)exp (*α*(*t*, *τ*) sin (*ω*(*t*, *τ*)).

If the elements of the matrix *B* have random time-invariable parameters, the expression (4.18) takes the form

  
$$\\begin{array}{r} {\\mathbf{y}(t) = {\\int\_{0}^{t}B}(t - \\tau)\\,\\mathbf{x}(\\tau)d\\tau.} \\\\ \\end{array}$$  
(4.24)

The elements of the matrix *B*, which has dimensions (*m* × *n*), are the pulse characteristics *b*[*i**j*](*τ*) with the independent randomized time-invariable parameters.

![Figure 4.5](images/fig4_5.jpg)

[Figure 4.5](#chapter4.xhtml#f4_5b)

*1.3.Discrete input functions.* In most cases, the input and output of an object are measured at discrete times with a fixed step *Δ*. An object operates on finite time intervals, and hence the available information about its input and output is represented as one-dimensional numerical data arrays. These arrays are used to form the vectors of lattice functions, **x**\[*k**Δ*\] = **x**\[*k*\] and $\\hat{\\mathbf{y}}\\lbrack k\\Delta\\rbrack = \\hat{\\mathbf{y}}\\lbrack k\\rbrack$ for the object's input and output, respectively. For details, the reader is referred to \[[176](#refbib.xhtml#r176)\].

In a linear approximation, a dynamic relation between the input and output lattice function vectors, **x**\[*k*\] and $\\hat{\\mathbf{y}}\\lbrack k\\rbrack,$ can be described by a matrix *B\[k*,*q\]* composed of the lattice pulse characteristics *b*[*i**j*]\[*k*, *q*\] for the RPM with time-varying parameters or by a matrix composed of the lattice pulse characteristics *b*[*i**j*]\[*q*\] for the RPM with constant parameters. In both statements, the RPM contain independent random parameters taking values within given intervals. The pulse characteristics are assumed to have the so-called finite memory. For the RPMs with time-varying parameters, this means that

  
$$\\begin{array}{r} {b\_{ij}\\lbrack k,q\\rbrack = \\left\\{ \\begin{aligned} {b\_{ij}\\lbrack k,q\\rbrack} & {\\text{if}\\, 0 \\leq l \\leq L\_{ij}\\,\\text{and}\\, k \\geq 0,} \\\\ 0 & {\\text{if}\\, l > L\_{ij}\\,\\text{and}\\, k \\geq 0;} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(4.25)

for the RPM with constant parameters,

  
$$\\begin{array}{r} {b\_{ij}\\lbrack q\\rbrack = \\left\\{ \\begin{aligned} {b\_{ij}\\lbrack q\\rbrack} & {\\text{if}\\, 0 \\leq l \\leq L\_{ij},} \\\\ 0 & {\\text{if}\\, l > L\_{ij}.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(4.26)

Then the RPM with discrete inputs and outputs is described by the following formulas:

*   for the time-varying parameters,
    
      
    $$\\begin{array}{r} {\\hat{\\mathbf{y}}\\lbrack k\\rbrack = {\\sum\\limits\_{q = 0}^{L^{\*}}B}\\lbrack k,q\\rbrack\\,\\mathbf{x}\\lbrack q\\rbrack,\\text{\\quad\\quad}k \\geq L^{\*};} \\\\ \\end{array}$$  
    (4.27)
    
*   for the constant parameters,
    
      
    $$\\begin{array}{r} {\\hat{\\mathbf{y}}\\lbrack k\\rbrack = {\\sum\\limits\_{q = 0}^{L^{\*}}B}\\lbrack q\\rbrack\\,\\mathbf{x}\\lbrack k - q\\rbrack,\\text{\\quad\\quad}k \\geq L^{\*}.} \\\\ \\end{array}$$  
    (4.28)
    

Here *L*^(\*) = max[*i**j*] *L*[*i**j*].

In contrast to the linear RPMs with continuous input functions, in this case the parameters can be the ordinates of the corresponding pulse characteristics.

 [Table 4.2](#chapter4.xhtml#t4_2b) 

 
|  |
| --- |
| *k* || 1 || 2 || 3 || 4 || 5 || 6 || 7 || 8 || 9 || 10 |
| *x\[k\]* || 2.5 || 3.5 || 5.7 || 2.8 || 2.1 || 1.9 || 1.7 || 2.1 || 3.1 || 4.4 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| *x*\[*k* − 1\] || 1.8 || 2.5 || 3.5 || 5.7 || 2.8 || 2.1 || 1.9 || 1.7 || 2.1 || 3.1 |
|  |

![Figure 4.6](images/fig4_6.jpg)

[Figure 4.6](#chapter4.xhtml#f4_6b)

![Figure 4.7](images/fig4_7.jpg)

[Figure 4.7](#chapter4.xhtml#f4_7b)

### 4.2.4Nonlinear dynamic models with power nonlinearities

Most of real objects are intrinsically nonlinear. A nonlinear object may demonstrate “almost” linear properties under a small variation of its input. An approach to describe the nonlinear properties of real objects in terms of the “Single Input–Ensemble Output” models is based on their approximation using functional power series. The elements of such series represent power functionals of different structure that depends on the nonlinear properties of an object and also on the properties of input functions. Particularly, if the object's nonlinearities are *continuous functions* and the object's input signals are *continuous time-varying functions*, then the RPM of such an object can be defined by a functional Volterra series \[177, [184](#refbib.xhtml#r184)\].

Consider a dynamic system that operates on a time interval 𝒯[*t*] = \[0, *t*\] and is characterized by a continuous functional ℬ(**x**(*τ*)) | *τ*∈𝒯[*t*]). Let the input vector **x**(*τ*) = {*x*[1](*τ*),…,*x*[*n*](*τ*)} be belonging to the space 𝒳[𝒯[*T*]] of continuous time-varying functions. According to \[[100](#refbib.xhtml#r100), 146, 184, [185](#refbib.xhtml#r185)\], the functional ℬ(**x**(*τ*)) (equivalently, the RPM output $\\hat{\\mathbf{y}}(t)$) can be represented as a convergent functional series, i.e.,

  
$$\\begin{aligned} {\\hat{\\mathbf{y}}(t)} & \\left. = \\mathcal{B}(\\mathbf{x}(\\tau))\\, \\middle| \\,\\tau \\in \\mathcal{T}\_{t}) = \\right. \\\\ {= {\\sum\\limits\_{h = 1}^{\\infty}{\\int\_{0}^{t}\\cdots}}} & {{\\int\_{0}^{t}W^{(h)}}(t - \\tau\_{1},\\ldots,t - \\tau\_{h}) \\times} \\\\ {\\times \\mathbf{x}^{(h)}} & {(\\tau\_{1},\\ldots,\\tau\_{h})d\\tau\_{1}\\cdots d\\tau\_{h}.} \\\\ \\end{aligned}$$  
(4.29)

Here **x**^((*h*))(*τ*[1], …, *τ*[*h*]) denotes the vector composed of the lexicographically ordered products {*x*[*i*[1]](*τ*[*j*[1]])⋯*x*[*i*[*n*]](*τ*[*j*[*h*]])}, where $(i\_{1},\\ldots,i\_{n}) \\in \\overline{1,n}$ and $(j\_{1},\\ldots,j\_{h}) \\in \\overline{1,h}.$ The dimension of the vector **x**^((*h*)) is

  
$$\\begin{array}{r} {l(n,h) = n^{h}.} \\\\ \\end{array}$$  
(4.30)

The matrix *W*^((*h*))(*t*[1], …, *t*[*h*]) has dimensions (*m* × *l*(*m*, *h*)), and its elements are multidimensional weight functions (pulse characteristics) *w*[*k*[*h*]]^((*h*))(*t*[1], …, *t*[*h*]), where $k\_{h} = \\overline{1,l(n,h)}$.

[Figure 4.8](#chapter4.xhtml#f4_8) illustrates the structure of the functional series (4.28). The blocks ∏[*h*] in [Fig. 4.8](#chapter4.xhtml#f4_8) indicate the lexicographical ordered products from the elements of the vector **x** of power *h*.

![Figure 4.8](images/fig4_8.jpg)

[Figure 4.8](#chapter4.xhtml#f4_8b)

The weight functions contain random parameters **a**^((*h*)) of the interval type, i.e.,

  
$$\\begin{array}{r} {\\mathbf{a}^{(h)} \\in \\mathcal{A}^{(h)} = \\left\\{ \\mathbf{a}\_{-}^{(h)} \\leq \\mathbf{a}^{(h)} \\leq \\mathbf{a}\_{+}^{(h)} \\right\\}.} \\\\ \\end{array}$$  
(4.31)

Since the parameters are random, they have a PDF *P*^(*h*)(**a**^((*h*))) on corresponding intervals.

The functional ℬ (4.2.4) can be often written as a functional series with structured weight matrices (pulse characteristics). Under structuring we mean a sequence of linear dynamic and nonlinear static operations. The block diagram of an RPM in which each channel represents a serial connection of a linear dynamic block and a power nonlinearity is shown in [Fig. 4.11(a)](#chapter4.xhtml#f4_11). The output of this model is defined by the following modification of the functional Volterra series:

  
$$\\begin{aligned} {\\hat{\\mathbf{y}}(t)} & \\left. = \\mathcal{B}(\\mathbf{x}(\\tau))\\, \\middle| \\,\\tau \\in \\mathcal{T}\_{t}) = \\right. \\\\ & {= {\\sum\\limits\_{h = 1}^{\\infty}\\left( {{\\int\_{0}^{t}W^{(h)}}(t - \\tau)\\,\\mathbf{x}(\\tau)\\, d\\tau} \\right)^{h}}.} \\\\ \\end{aligned}$$  
(4.32)

For the one-dimensional RPM, the last-mentioned equality takes the form

  
$$\\begin{array}{r} {\\hat{y}(t) = {\\sum\\limits\_{h = 1}^{\\infty}{\\int\_{0}^{t}\\cdots}}{\\int\_{0}^{t}{\\prod\\limits\_{i = 1}^{h}\\,}}\\left( {w(t - \\tau\_{i})\\, x(\\tau\_{i})d\\tau\_{i}} \\right).} \\\\ \\end{array}$$  
(4.33)

The block diagram in [Fig. 4.11(b)](#chapter4.xhtml#f4_11) corresponds to an RPM with the inverse sequence of the linear and nonlinear operations in each channel: first the input undergoes a power transformation and then a dynamic linear transformation. The RPM output is described by another modification of the functional Volterra series:

  
$$\\begin{array}{r} {\\hat{\\mathbf{y}}(t) = {\\sum\\limits\_{h = 1}^{\\infty}{\\int\_{0}^{t}W}}(t - \\tau)\\mathbf{x}^{(h)}(\\tau)\\, d\\tau.} \\\\ \\end{array}$$  
(4.34)

Here, the vector **x**^((*h*))(*τ*) consists of the lexicographically ordered elements formed by all possible products of the elements of the vector **x**(*τ*).

![Figure 4.11](images/fig4_11.jpg)

[Figure 4.11](#chapter4.xhtml#f4_11b)

Consider an RPM with a finite memory *K*; the input and output of this model are measured at discrete times *t*[*k*] with step *Δ*. Letting *k* = \[*t*[*k*]/*Δ*\], 

  
$$\\begin{aligned} {\\hat{\\mathbf{y}}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{\\infty}{\\sum\\limits\_{(n\_{1},\\ldots,n\_{h}) = 0}^{K}W^{(h)}}}\\lbrack n\_{1},\\ldots,} & {n\_{h}\\rbrack\\,\\mathbf{x}^{(h)}\\lbrack k - n\_{1},\\ldots,k - n\_{h}\\rbrack,} \\\\ {k \\geq} & {K.} \\\\ \\end{aligned}$$  
(4.35)

The vector **x**^((*h*))\[*k* − *n*[1], …, *k* − *n*[*h*]\] has the elements *x*[*i*[1]]\[*k* − *n*[1]\]⋯*x*[*i*[*n*]]\[*k* − *n*[*h*]\], which are the lexicographically ordered all possible products of $(i\_{1},\\ldots,i\_{n}) = \\overline{1,n}$ elements of the vector **x** at the times $(n\_{1},\\ldots,n\_{h}) = \\overline{0,K}.$ The dimension of the vector **x**^((*h*))\[*k* − *n*[1], …, *k* − *n*[*h*]\] is

  
$$\\begin{array}{r} {l(n,h) = \\frac{(n\\, K + h - 1)!}{h!(n\\, k - 1)!}.} \\\\ \\end{array}$$  
(4.36)

The parameter *K* defines the memory capacity of the RPM, i.e.,

  
$$\\begin{array}{r} {W^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack = \\left\\{ \\begin{aligned} {W^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {\\text{if~all}\\,(n\_{1},\\ldots,n\_{h}) \\leq K,} \\\\ 0 & {\\text{if~at~least~one}\\, n\_{j} > K.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(4.37)

The elements of the matrix *W*^((*h*))\[*n*[1], …, *n*[*h*]\] are discrete random weight functions (pulse characteristics) $w\_{i,k\_{h}}^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack,\\,\\, i = \\overline{1,m};\\,\\, k\_{h} = \\overline{1,l(n,h)}.$ They reflect the dynamic and nonlinear properties of the RPM. Note that the nonlinear properties are formulated in terms of multidimensional functions (pulse characteristics), not in terms of structurally representable nonlinear elements.

The pulse characteristics *w*[*i*, *k*[*h*]]^((*h*))\[*n*[1], …, *n*[*h*]\] have the interval type, i.e.,

  
$$\\begin{array}{r} {w\_{i,k\_{h}}^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack \\in \\mathcal{W}\_{i,k\_{h}}^{(h)} = \\left\\lbrack {{\\widetilde{w}}\_{i,k\_{h}}^{(h, - )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack,\\,{\\widetilde{w}}\_{i,k\_{h}}^{(h, + )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} \\right\\rbrack.} \\\\ \\end{array}$$  
(4.38)

In this expression, *w̃*[*i*, *k*[*h*]]^((*h*,  ± ))\[*n*[1], …, *n*[*h*]\] are given functions that describe the left and right limits of the above intervals. For example, they can be defined as the exponential functions

  
$$\\begin{aligned} {{\\widetilde{w}}\_{i,k\_{h}}^{(h, - )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {= {\\prod\\limits\_{j = 1}^{h}\\beta\_{(i,k\_{h})}^{(h, - )}}(j)\\,\\exp\\left( {- \\alpha\_{(i,k\_{h})}^{(h, - )}(j)\\, n\_{j}} \\right),} \\\\ {{\\widetilde{w}}\_{i,k\_{h}}^{(h, + )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {= {\\prod\\limits\_{j = 1}^{h}\\beta\_{(i,k\_{h})}^{(h, + )}}(j)\\,\\exp\\left( {- \\alpha\_{(i,k\_{h})}^{(h, + )}(j)\\, n\_{j}} \\right).} \\\\ \\end{aligned}$$  
(4.39)

A convenient approach is to treat their ordinates as the RPM parameters. This allows us to transform the nonlinear RPM to its linear analog of considerably higher dimension. The transformation procedure for the one-dimensional RPM (with one input and one output) is given by

  
$$\\begin{array}{r} {\\hat{y}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{H}\\sum\\limits^{K}}(n\_{1},\\ldots,n\_{h}) = 0w^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack\\,{\\prod\\limits\_{i = 1}^{h}x}\\lbrack k - n\_{i}\\rbrack,\\text{\\quad\\quad}k \\geq K.} \\\\ \\end{array}$$  
(4.40)

Introduce a lexicographical ordering of the variables {*n*[1],…,*n*[*h*]} by reassigning numbers from 0 to *t*[*h*] = (*K* + 1)^(*h*) − 1 to the resulting sets. Then

  
$$\\begin{array}{r} \\left. \\left\\{ n\_{1},\\ldots,n\_{h} \\right\\}\\rightarrow i^{(h)},\\text{\\quad\\quad}i^{(h)} \\in \\lbrack 0,t\_{h}\\rbrack. \\right. \\\\ \\end{array}$$  
(4.41)

In accordance with this numbering scheme, define the following indexes for the random parameters that correspond to the values of the pulse characteristics at the discrete times 0, 1, …, *K*:

  
$$\\begin{array}{r} \\left. a\_{i^{(h)}}^{(h)}\\rightarrow w^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack,\\text{\\quad\\quad}i^{(h)} \\in \\lbrack 0,t\_{h}\\rbrack. \\right. \\\\ \\end{array}$$  
(4.42)

Construct a random vector

  
$$\\begin{array}{r} {\\mathbf{a}(h) = \\left\\{ a\_{0}^{(h)},\\ldots,a\_{t\_{h}}^{(h)} \\right\\}.} \\\\ \\end{array}$$  
(4.43)

The elements of the vector **a**(*h*) —see (4.38)—take values within the intervals

  
$$\\begin{array}{r} {\\mathcal{A}^{(h)}(i^{(h)}) = \\left\\lbrack {a\_{-}^{(h)}(i^{(h)}),\\, a\_{+}^{(h)}(i^{(h)})} \\right\\rbrack.} \\\\ \\end{array}$$  
(4.44)

By analogy with (4.41), introduce a lexicographical ordering of the variables *k* − *n*[1], …, *k* − *n*[*h*], where *k* is a fixed parameter and the indexes *n*[1], …, *n*[*h*] take values within the interval \[0,*K\]*.

For each fixed *k*, renumber the resulting sets as follows:

  
$$\\begin{array}{r} \\left. \\left\\{ k - n\_{1},\\ldots,k - n\_{h} \\right\\}\\rightarrow(k,i^{(h)}). \\right. \\\\ \\end{array}$$  
(4.45)

Then the lexicographically ordered products of the variables *x*\[*k* − *n*[1]\], …, *x*\[*k* − *n*[*h*]\] with fixed *k* form the vector

  
$$\\begin{array}{r} {\\mathbf{x}^{(h)}\\lbrack k\\rbrack = \\left\\{ {x\_{k,0}^{(h)},\\ldots,x\_{k,t\_{h}}^{(h)}} \\right\\}.} \\\\ \\end{array}$$  
(4.46)

Consequently, the expression (4.40) can be written as

  
$$\\begin{array}{r} {\\hat{y}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{H}\\left\\langle \\mathbf{a}^{(h)},\\,\\mathbf{x}^{(h)}\\lbrack k\\rbrack \\right\\rangle},} \\\\ \\end{array}$$  
(4.47)

where ⟨•, •⟩ denotes the scalar product of vectors ∙ and  • .

Consider a one-dimensional RPM with structured nonlinearities (see [Fig. 4.11(a)](#chapter4.xhtml#f4_11)) and the following discrete time-varying functions as its input:

  
$$\\begin{array}{r} {\\hat{y}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{H}\\left( {{\\sum\\limits\_{n = 0}^{K}w^{(h)}}\\lbrack n\\rbrack x\\lbrack k - n\\rbrack} \\right)^{h}},\\text{\\quad\\quad}k \\geq K.} \\\\ \\end{array}$$  
(4.48)

The pulse characteristics *w*^((*h*))\[*n*\] have a finite memory *K* and random parameters. Again, as the latter choose their ordinates, i.e.,

  
$$\\begin{array}{r} {w^{(h)}\\lbrack n\\rbrack = a\_{n}^{(h)},\\quad n = \\overline{0,K}.} \\\\ \\end{array}$$  
(4.49)

Construct the vector

  
$$\\begin{array}{r} {\\mathbf{a}^{(h)} = \\left\\{ a\_{0}^{(h)},\\ldots,a\_{K}^{(h)} \\right\\}.} \\\\ \\end{array}$$  
(4.50)

The parameters *a*[*n*]^((*h*)) are random, independent, and take their values within the intervals

  
$$\\begin{array}{r} {\\mathcal{A}\_{n}^{(h)} = \\lbrack - A\_{n}^{(h)},\\, A\_{n}^{(h)}\\rbrack,\\quad A\_{n}^{(h)} = \\beta\_{n}^{(h)}\\exp( - \\alpha\_{n}^{(h)}).} \\\\ \\end{array}$$  
(4.51)

The PDFs $p\_{n}^{(h)}(a\_{n}^{(h)}),\\,\\, n = \\overline{0,K},$ are defined on these intervals.

Get back to equality (4.48) and introduce the following notations:

*   the index set
    
      
    $$\\begin{array}{r} {\\mathcal{I}\_{h}(K) = \\left\\{ i\_{n}:\\,{\\sum\\limits\_{n = 0}^{K}i\_{n}} = h,\\, i\_{n} = \\overline{0,K} \\right\\};} \\\\ \\end{array}$$  
    (4.52)
    
*   the vector
    
      
    $$\\begin{array}{r} {\\mathbf{i} = \\left\\{ i\_{0},\\ldots,i\_{K} \\right\\};} \\\\ \\end{array}$$  
    (4.53)
    
*   the function
    
      
    $$\\begin{array}{r} {C\_{(k,i\_{n})}(x) = \\frac{1}{i\_{n}!}\\, x^{i\_{n}}\\lbrack k - n\\rbrack.} \\\\ \\end{array}$$  
    (4.54)
    

Then formula (4.48) can be written as

  
$$\\begin{aligned} {\\hat{y}\\lbrack k\\rbrack} & {= {\\sum\\limits\_{h = 1}^{H}V\_{k}^{(h)}}(\\mathbf{a}^{(h)},x),} \\\\ {V\_{k}^{(h)}(\\mathbf{a}^{(h)},x)} & {= {\\sum\\limits\_{\\mathbf{i} \\in \\mathcal{I}\_{h}(K)}\\,}{\\prod\\limits\_{n = 0}^{K}\\,}C\_{(k,i\_{n})}(x)\\,{\\lbrack a\_{n}^{(h)}\\rbrack}^{i\_{n}}.} \\\\ \\end{aligned}$$  
(4.55)

Hence, unlike the RPM (4.40), the model under consideration is nonlinear with power nonlinearities.

### 4.2.5Nonlinear dynamic models with polynomial nonlinearities

In machine learning problems, it is often necessary to deal with dynamic objects whose observable output has jumps at certain times or under certain values of its input. In other cases, there exists prior information about the object's properties that defines its structure as illustrated in [Fig. 4.13(a)](#chapter4.xhtml#f4_13) or [Fig. 4.13(b)](#chapter4.xhtml#f4_13). The nonlinear blocks in these diagrams are described by orthonormal polynomials of different classes (see [Table 4.1](#chapter4.xhtml#t4_1)).

![Figure 4.13](images/fig4_13.jpg)

[Figure 4.13](#chapter4.xhtml#f4_13b)

Consider an RPM with the structure presented in [Fig. 4.13(a)](#chapter4.xhtml#f4_13). Using orthogonal polynomials *g*[*k*](*x*), let us write this RPM in the following form:

  
$$\\begin{array}{r} \\left. \\hat{y}(t) = {\\sum\\limits\_{k = 0}^{K}c\_{k}}{\\int\_{0}^{t}w}(t - \\tau\\, \\middle| \\mathbf{b})\\, g\_{k}(x(\\tau))d\\tau, \\right. \\\\ \\end{array}$$  
(4.56)

where the coefficients *c*[0], …, *c*[*K*] are independent random variables of the interval type, i.e.,

  
$$\\begin{array}{r} {c\_{k} \\in \\mathcal{C}\_{k} = \\lbrack c\_{k}^{-},c\_{k}^{+}\\rbrack,\\text{\\quad\\quad}k = \\overline{0,K}.} \\\\ \\end{array}$$  
(4.57)

The parameters **b** of the pulse characteristic *w*(*t* |**b**) are randomized and belong to the intervals

  
$$\\begin{array}{r} {\\mathbf{b} \\in \\mathcal{B} = \\lbrack\\mathbf{b}^{-},\\mathbf{b}^{+}\\rbrack.} \\\\ \\end{array}$$  
(4.58)

Now get back to the block diagram in [Fig. 4.13(b)](#chapter4.xhtml#f4_13). Obviously, the linear and nonlinear dynamic elements of the object have interchanged their places. The object's input is a function *x*(*t*). Let us construct the RPM of this object using the pulse characteristic with random parameters *w*(*τ* | **b**) for the linear element and a collection of orthogonal polynomials with random coefficients for the nonlinear element. Then the RPM can be written as

  
$$\\begin{aligned} {\\hat{y}(t) = \\sum\_{k = 1}^{K}\\,\\sum\_{i = 0}^{k}} & \\left. c\_{k}a\_{ki}\\int\_{0}^{t}\\cdots\\int\_{0}^{t}w(t - \\tau\_{0} \\middle| \\mathbf{b})\\cdots w(t - \\tau\_{i} \\middle| \\mathbf{b}) \\times \\right. \\\\ & {\\times x(\\tau\_{0})\\cdots x(\\tau\_{i})d\\tau\_{1}\\cdots d\\tau\_{i}.} \\\\ \\end{aligned}$$  
(4.59)

In this equation, *a*[*k**i*] denote the coefficients of the orthonormal polynomials (see [Table 4.1](#chapter4.xhtml#t4_1)); *c*[1], …, *c*[*K*] are the independent random coefficients of the randomized model of the nonlinear element. They are of the interval type (4.57).

If the input and output of this RPM is characterized by the lattice functions, then the following equations hold:

*   for the RPM in [Fig. 4.13(a)](#chapter4.xhtml#f4_13),
    
      
    $$\\begin{array}{r} \\left. \\hat{y}\\lbrack n\\rbrack = {\\sum\\limits\_{k = 0}^{K}\\,}{\\sum\\limits\_{i = 0}^{k}c\_{k}}a\_{ki}{\\sum\\limits\_{m = 0}^{n}w}\\lbrack n - m\\, \\middle| \\,\\mathbf{b}\\rbrack\\, x^{i}\\lbrack m\\rbrack; \\right. \\\\ \\end{array}$$  
    (4.60)
    
*   for the RPM in [Fig. 4.13(b)](#chapter4.xhtml#f4_13),
    
      
    $$\\begin{array}{r} \\left. \\hat{y}\\lbrack n\\rbrack = {\\sum\\limits\_{k = 1}^{K}{\\sum\\limits\_{i = 0}^{k}c\_{k}}}a\_{ki}{\\sum\\limits\_{(m\_{0},\\ldots,m\_{i}) = 0}^{n}{\\prod\\limits\_{j = 0}^{i}w}}\\lbrack n - m\_{j}\\, \\middle| \\,\\mathbf{b}\\rbrack\\, x\\lbrack m\_{j}\\rbrack. \\right. \\\\ \\end{array}$$  
    (4.61)
    

In these formulas, the coefficients *c*[*k*] are the independent random variables distributed on the corresponding intervals (4.57) in accordance with the given PDFs. The parameters *b*[1], …, *b*[*s*] of the pulse characteristic are also random, independent and take values within the corresponding intervals with the given PDF.

### 4.2.6Randomized neural networks

Neural networks are a kind of parameterized models used in machine learning procedures. A structural foundation of a neural network is the Kolmogorov theorem \[[94](#refbib.xhtml#r94)\], which states that a continuous function of *n* variables on the nonnegative unit cube can be written as the superposition of one-variable functions with summation:

  
$$\\begin{array}{r} {f(x\_{1},\\ldots,x\_{n}) = {\\sum\\limits\_{k = 1}^{(2n + 1)}h\_{k}}\\left( {{\\sum\\limits\_{i = 1}^{n}\\phi\_{ik}}(x\_{i})} \\right);} \\\\ \\end{array}$$  
(4.62)

here the variables *h*[1], …, *h*[2*n* + 1] depend on the function *f*, whereas the functions *ϕ*[*i**k*](*x*[*i*]) do not. This theorem claims the existence of such a representation but gives no technical details to find it.

On the one hand, the universalism of neural networks can be explained by a structural analogy with the Kolmogorov theorem; on the other, by a simplified (statistical) analogy with operation of a biological neuron \[[122](#refbib.xhtml#r122)\]. The general structure of the neuron's statistical model is illustrated in [Fig. 4.16(a)](#chapter4.xhtml#f4_16). It consists of three serially connected blocks, namely, synaptic coefficients **w** = {*w*[1],…,*w*[*n*]}, an adder and a nonlinear transformation block with an activation function *ϕ*(*u*, **b**), where **b** are the activation function parameters. [Figure 4.16(b)](#chapter4.xhtml#f4_16) shows an example of this model, in which the nonlinear transformation block has an activation function *ϕ*(*u*, *Δ*) with a threshold *Δ*. In the general case, the activation function *ϕ*(*u*) may contain several parameters, further denoted by *b*[1], …, *b*[*q*]. Besides the function *ϕ*(*u*) in [Fig. 4.16(b)](#chapter4.xhtml#f4_16), the following activation functions are widespread:

*   —the linear activation function (see [Fig. 4.17(a)](#chapter4.xhtml#f4_17))
    
      
    $$\\begin{array}{r} {\\phi(u) = \\left\\{ \\begin{aligned} 0 & {\\text{if}\\, u \\leq \\Delta,} \\\\ u & {\\text{if}\\, u \\geq \\Delta;} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
    (4.63)
    
*   —the sigmoidal activation function (see [Fig. 4.17(b)](#chapter4.xhtml#f4_17))
    
      
    $$\\begin{array}{r} {\\phi(u) = \\frac{1}{1 + \\exp(u - \\Delta)};} \\\\ \\end{array}$$  
    (4.64)
    
*   —the tangent activation function (see [Fig. 4.17(c)](#chapter4.xhtml#f4_17))
    
      
    $$\\begin{array}{r} {\\phi(u) = \\tan(u).} \\\\ \\end{array}$$  
    (4.65)
    

A network with the structure presented in [Fig. 4.16(b)](#chapter4.xhtml#f4_16) is called a single-layer neural network. A serial connection of single-layer neural networks yields a multilayer neural network. Its internal layers are called hidden whereas the last one is called the output layer. Most applications involve one hidden layer, as illustrated in [Fig. 4.18](#chapter4.xhtml#f4_18). The input layer has a set of synaptic coefficients *w*[11], …*w*[*n**h*]; the hidden layer, *g*[11], …, *g*[*h**s*].

Thus, single- and multilayer neural networks ([Figs. 4.16](#chapter4.xhtml#f4_16) and [4.18](#chapter4.xhtml#f4_18)) are statistical systems, i.e., the network's input at a current time theoretically depends on its input at this time. For example, the output of a single-layer neural network has the form

![Figure 4.16](images/fig4_16.jpg)

[Figure 4.16](#chapter4.xhtml#f4_16b)

![Figure 4.17](images/fig4_17.jpg)

[Figure 4.17](#chapter4.xhtml#f4_17b)

![Figure 4.18](images/fig4_18.jpg)

[Figure 4.18](#chapter4.xhtml#f4_18b)

  
$$\\begin{array}{r} {y(t) = S\\left( \\mathbf{x}(t)\\, \\middle| \\,\\mathbf{w},\\mathbf{b} \\right),} \\\\ \\end{array}$$  
(4.66)

where **w** and **b** are network parameters.

By assumption, a randomized neural network incorporates random parameters that take values within given intervals, i.e.,

  
$$\\begin{array}{r} {\\mathbf{w} \\in \\mathcal{W} = \\lbrack\\mathbf{w}^{-},\\mathbf{w}^{+}\\rbrack;\\text{\\quad\\quad}\\mathbf{b} \\in \\mathcal{B} = \\lbrack\\mathbf{b}^{-},\\mathbf{b}^{+}\\rbrack.} \\\\ \\end{array}$$  
(4.67)

The probabilistic properties of the parameters on these intervals are characterized by probability density functions *P*[*w*](**w**) and *P*[*b*](**b**). The output of a randomized neural network represents an ensemble of the values of the random variable *y*.

![Figure 4.19](images/fig4_19.jpg)

[Figure 4.19](#chapter4.xhtml#f4_19b)

## 4.3“(Single Input, Feedback)–Ensemble Output” Dynamic Randomized Parametric Model

### 4.3.1Definition and structure

For a structural design of many dynamic RPMs, it is insufficient to define an input-output relation. In such cases, we have to reflect some internal mechanisms of the processes or objects under modeling. A mathematical framework that can be used to describe these mechanisms involves different classes of equations. Their general structure is represented by a certain block with a parameterized mapping 𝔾 and a feedback loop characterized by a parameterized mapping ℂ, see [Fig. 4.20](#chapter4.xhtml#f4_20).

![Figure 4.20](images/fig4_20.jpg)

[Figure 4.20](#chapter4.xhtml#f4_20b)

In this figure, **x** ∈ *R*^(*n*) denotes the model input; **y** ∈ *R*^(*m*) is the model output; finally, **z** ∈ *R*^(*d*) gives the feedback block output.

The mappings 𝔾 and *ℂ* describe the internal mechanisms of the processes running in an object. Using a functional description for these mappings, introduce the following notations:

  
$$\\begin{aligned} \\mathbb{G} & {= \\mathcal{G}\\left( \\mathbf{x}(\\tau),\\mathbf{z}(\\tau),\\, \\middle| \\,\\mathbf{a};\\,\\tau \\in \\mathcal{T} \\right),} \\\\ {\\mathbb{C}} & {= \\mathcal{C}\\left( \\mathbf{y}(\\tau),\\, \\middle| \\,\\mathbf{c};\\,\\tau \\in \\mathcal{T} \\right).} \\\\ \\end{aligned}$$  
(4.68)

The functionals 𝒢 and 𝒞 contain random parameters **a** ∈ *R*^(*r*) and **c** ∈ *R*^(*h*), respectively, with independent elements that belong to the intervals

  
$$\\begin{array}{r} {\\mathbf{a} \\in \\mathcal{A} = \\lbrack\\mathbf{a}^{-},\\mathbf{a}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{c} \\in \\mathcal{S} = \\lbrack\\mathbf{c}\_{-},\\mathbf{c}^{+}\\rbrack.} \\\\ \\end{array}$$  
(4.69)

Consequently, the \[(SI,FB)–EO\] RPM can be written as

  
$$\\begin{aligned} {\\mathbf{y}(t)} & {= \\mathcal{G}\\left( \\mathbf{x}(\\tau),\\mathbf{z}(\\tau)),\\, \\middle| \\,\\mathbf{a};\\,\\tau \\in \\mathcal{T} \\right),} \\\\ {\\mathbf{z}(t)} & {= \\mathcal{C}\\left( \\mathbf{y}(\\tau),\\, \\middle| \\,\\mathbf{c};\\, \\middle| \\,\\tau \\in \\mathcal{T} \\right).} \\\\ \\end{aligned}$$  
(4.70)

The functionals in these equations may have different mathematical models, depending on the declared properties of objects under analysis.

### 4.3.2Linear dynamic models

The linear \[(SI,FB)–EO\] RPM have the structure illustrated in [Fig. 4.20](#chapter4.xhtml#f4_20), except for its blocks are described by *linear functionals 𝒢 and 𝒞 with random parameters*. Assume that the input vector consists of *continuous time-varying functions* and the parameters are time-invariable. Then *the integral form of the linear \[(SI,FB)–EO\] RPM* can be written as

  
$$\\begin{aligned} {\\mathbf{y}(t)} & \\left. = {\\int\_{\\mathcal{T}}G}(t - \\tau\\, \\middle| \\,\\mathbf{a})\\,\\mathbf{x}(\\tau)\\, d\\tau + {\\int\_{\\mathcal{T}}F}(t - \\tau\\, \\middle| \\,\\mathbf{b})\\,\\mathbf{z}(\\tau)\\, d\\tau, \\right. \\\\ {\\mathbf{z}(t)} & {= {\\int\_{\\mathcal{T}}C}(t - \\tau)\\,\\mathbf{y}(\\tau)\\, d\\tau.} \\\\ \\end{aligned}$$  
(4.71)

Recall that these equalities involve vectors **x** ∈ *R*^(*n*), **y** ∈ *R*^(*m*) and **z** ∈ *R*^(*d*), as well as the matrices $\\left. G(t\\, \\middle| \\,\\mathbf{a}) = \\lbrack g\_{ij}(t\\, \\middle| \\,\\mathbf{a}),\\, i = \\overline{1,m},\\, j = \\overline{1,n}\\rbrack;\\, F(t\\, \\middle| \\,\\mathbf{b}) = \\lbrack f\_{il}(t\\, \\middle| \\,\\mathbf{b}),\\, i = \\overline{1,m}\\rbrack,\\, l = \\overline{1,d};\\, C(t\\, \\middle| \\,\\mathbf{b}) = \\lbrack c\_{h,k}(t\\, \\middle| \\,\\mathbf{c}),\\, h = \\overline{1,d},\\, k = \\overline{1,m}\\rbrack. \\right.$ As their elements the matrices contain the pulse characteristics *g*[*i**j*](*t* | **a**), *f*[*i**l*](*t* | **b**) and *c*[*h*, *k*](*t* | **c**) with random parameters described by the vectors **a**, **b** and **c**; the elements of these vectors are independent and take values within the intervals

  
$$\\begin{array}{r} {\\mathbf{a} \\in \\mathcal{A} = \\lbrack\\mathbf{a}^{-},\\mathbf{a}^{+}\\rbrack,\\quad\\mathbf{b} \\in \\mathcal{B} = \\lbrack\\mathbf{b}^{-},\\mathbf{b}^{+}\\rbrack,\\quad\\mathbf{c} \\in \\mathcal{C} = \\lbrack\\mathbf{c}^{-},\\mathbf{c}^{+}\\rbrack.} \\\\ \\end{array}$$  
(4.72)

The \[(SI,FB)–EO\] RPM can be transformed into the \[SI–EO\] RPM. In our case, a most convenient approach is to employ the Fourier transform. First, eliminate the vector **z** in (4.71) to get the equation

  
$$\\begin{array}{r} \\left. \\mathbf{y} = {\\int\_{\\mathcal{T}}G}(t - \\tau\\, \\middle| \\,\\mathbf{a})\\,\\mathbf{x}(\\tau)\\, d\\tau + {\\int\_{\\mathcal{T}}F}(t - \\tau\\, \\middle| \\,\\mathbf{b})\\,{\\int\_{\\mathcal{T}\_{\\tau}}C}(t - \\lambda\\, \\middle| \\,\\mathbf{c})\\,\\mathbf{y}(\\lambda)\\, d\\tau d\\lambda. \\right. \\\\ \\end{array}$$  
(4.73)

Using the Fourier transform \[[43](#refbib.xhtml#r43)\], write the solution of this equation in the frequency domain (i.e., in terms of image functions):

  
$$\\begin{aligned} & \\left. \\mathbf{Y}(s) = K(s\\, \\middle| \\,\\mathbf{a},\\mathbf{b},\\mathbf{c})\\,\\mathbf{X}(s), \\right. \\\\ & \\left. K(s\\, \\middle| \\,\\mathbf{a},\\mathbf{b},\\mathbf{c}) = \\left( I - F(s\\, \\middle| \\,\\mathbf{b})C(s\\, \\middle| \\,\\mathbf{c}) \\right)^{( - 1)}G(s\\, \\middle| \\,\\mathbf{a}). \\right. \\\\ \\end{aligned}$$  
(4.74)

Here *s* = *α* + *ι**ω* and $\\iota = \\sqrt{- 1},$ whereas *α* and *ω* are real variables. Transition from the frequency domain to the time domain yields the following integral equation for an equivalent \[SI–EO\] RPM:

  
$$\\begin{array}{r} \\left. \\mathbf{y}(t) = {\\int\_{\\mathcal{T}}K}(t - \\tau\\, \\middle| \\,\\mathbf{a},\\mathbf{b},\\mathbf{c})\\,\\mathbf{x}(\\tau)\\, d\\tau, \\right. \\\\ \\end{array}$$  
(4.75)

where the matrix

  
$$\\begin{array}{r} \\left. K(t\\, \\middle| \\,\\mathbf{a},\\mathbf{b},\\mathbf{c}) = \\mathcal{L}^{( - 1)}\\left\\{ K(s\\, \\middle| \\,\\mathbf{a},\\mathbf{b},\\mathbf{c}) \\right\\}. \\right. \\\\ \\end{array}$$  
(4.76)

### 4.3.3Nonlinear dynamic models with power nonlinearities

Consider an object whose \[(SI,FB)–EO\] RPM has the structure shown in [Fig. 4.20](#chapter4.xhtml#f4_20). Let the functionals 𝒢 and 𝒞 be continuous. Then they can be represented using the framework of functional Volterra series \[184\]; see [Section 3.1](#chapter3.xhtml#sec3_1).

This framework will be adopted for the one-dimensional \[(SI,FB)–EO\] RPM ([Fig. 4.20](#chapter4.xhtml#f4_20)), which is described by the system of equations

  
$$\\begin{aligned} {y(t)} & {= \\mathcal{G}\\left( \\varepsilon(\\tau)),\\, \\middle| \\,\\mathbf{a};\\,\\tau \\in \\mathcal{T} \\right),} \\\\ {z(t)} & {= \\mathcal{C}\\left( y(\\tau),\\, \\middle| \\,\\mathbf{c};\\, \\middle| \\,\\tau \\in \\mathcal{T} \\right),} \\\\ {\\varepsilon(t)} & {= x(t) - z(t).} \\\\ \\end{aligned}$$  
(4.84)

Assume that the time-varying functions *x*(*t*), *z*(*t*), and *y*(*t*), as well as the functionals 𝒢(*ε*, | **a**) and 𝒞(*y*, | **c**), are continuous. In this case, they can be expressed as the functional series with the corresponding weight functions (pulse characteristics), i.e.,

  
$$\\begin{aligned} {y(t) = {\\sum\\limits\_{i = 1}^{\\infty}{\\int\_{\\tau\_{1} \\in \\mathcal{T}}\\cdots}}} & \\left. {\\int\_{\\tau\_{i} \\in \\mathcal{T}}\\,}g\_{i}(t - \\tau\_{1},\\ldots,t - \\tau\_{i}\\, \\middle| \\,\\mathbf{a}^{(i)}) \\times \\right. \\\\ {\\varepsilon(\\tau\_{1})} & {\\cdots\\varepsilon(\\tau\_{i})\\, d\\tau\_{1}\\cdots d\\tau\_{i},} \\\\ {z(t) = {\\sum\\limits\_{j = 1}^{\\infty}{\\int\_{\\lambda\_{1} \\in \\mathcal{T}}\\cdots}}} & \\left. {\\int\_{\\lambda\_{j} \\in \\mathcal{T}}\\,}c\_{j}(t - \\lambda\_{1},\\ldots,t - \\lambda\_{j}\\, \\middle| \\,\\mathbf{c}^{(j)}) \\times \\right. \\\\ {\\times y(\\lambda\_{1})} & {\\cdots y(\\lambda\_{j})\\, d\\lambda\_{1}\\cdots d\\lambda\_{j},} \\\\ \\end{aligned}$$  
(4.85)

  
$$\\begin{array}{r} {\\varepsilon(t) = x(t) - z(t).} \\\\ \\end{array}$$  

Here the pulse characteristics have random parameters, namely, the random independent vectors **a**^((*i*)) and **c**^((*j*)) with independent elements taking values within the intervals

  
$$\\begin{aligned} {\\mathbf{a}^{(i)} \\in \\mathcal{A}^{(i)}} & {= \\lbrack\\mathbf{a}\_{-}^{(i)},\\,\\mathbf{a}\_{+}^{(i)}\\rbrack,\\text{\\quad\\quad}i \\in \\lbrack 1,\\infty),} \\\\ {\\mathbf{c}^{(j)} \\in \\mathcal{S}^{(j)}} & {= \\lbrack\\mathbf{c}\_{-}^{(j)},\\,\\mathbf{c}\_{+}^{(j)}\\rbrack,\\text{\\quad\\quad}j \\in \\lbrack 1,\\infty).} \\\\ \\end{aligned}$$  
(4.86)

As a matter of fact, there exists a certain relation between the \[(SI,FB)–EO\] RPM (4.3.3) and the \[SI–EO\] RPM (4.2.4) with continuous nonlinearities. Recall that the latter model is described by a continuous functional ℬ, which can be also written as a functional Volterra series, i.e.,

  
$$\\begin{aligned} {\\mathbf{y}(t)} & \\left. = \\mathcal{B}(\\mathbf{x}(\\tau),\\, \\middle| \\,\\tau \\in \\mathcal{T}) = \\right. \\\\ {+ {\\sum\\limits\_{k}^{\\infty}{\\int\_{\\tau\_{1} \\in \\mathcal{T}}\\cdots}}} & {{\\int\_{\\tau\_{k} \\in \\mathcal{T}}\\,}w\_{k}(t - \\tau\_{1},\\ldots,t - \\tau\_{k}) \\times} \\\\ \\times & {x(\\tau\_{1})\\cdots x(\\tau\_{k})\\, d\\overline{\\tau}.} \\\\ \\end{aligned}$$  
(4.87)

Define the pulse characteristics in this formula so that equations (4.3.3) turn into identities \[146\]. First, substitute the last-mentioned equation into the first one to obtain an integral equation in the variable *y*(*t*):

  
$$\\begin{aligned} & \\left. y(t) = {\\int\_{\\tau\_{1} \\in \\mathcal{T}}g\_{1}}(t - \\tau\_{1}\\, \\middle| \\,\\mathbf{a})\\lbrack x(\\tau\_{1}) - {\\int\_{\\lambda\_{1} \\in \\mathcal{T}}\\,}c\_{1}(\\tau\_{1} - \\lambda\_{1}\\, \\middle| \\,\\mathbf{c})\\, y(\\lambda\_{1})\\, d\\lambda\_{1} + \\right. \\\\ & \\left. \\quad + {\\int\_{\\lambda\_{1} \\in \\mathcal{T}}{\\int\_{\\lambda\_{2} \\in \\mathcal{T}}\\,}}c\_{2}(t - \\lambda\_{1},t - \\lambda\_{2}\\, \\middle| \\,\\mathbf{c})\\, y(\\lambda\_{1})y(\\lambda\_{2})\\, d\\lambda\_{1}d\\lambda\_{2} + \\ldots \\right. \\\\ \\end{aligned}$$  
(4.88)

Then construct the solution in the form of the functional series (4.3.3): substitute it into the left- and right-hand sides of equation (4.3.3), collecting and comparing the terms with the same powers of the variable *x*. These manipulations lead to the following system of integral equations for the cores *w*[*k*](*τ*[1],…,*τ*[*k*])=*w*[*k*](*τ*[1],…,*τ*[*k*] | **a**,**c**) of (4.3.3):

  
$$\\begin{aligned} \\left. {\\int\_{\\tau\_{1} \\in \\mathcal{T}}w\_{1}}(t - \\tau\_{1}\\, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\right. & \\left. x(\\tau\_{1})\\, d\\tau\_{1} = {\\int\_{\\tau\_{1} \\in \\mathcal{T}}g\_{1}}(t - \\tau\_{1}\\, \\middle| \\,\\mathbf{a})\\,\\lbrack x(\\tau\_{1})\\, d\\tau\_{1} - \\right. \\\\ {- {\\int\_{\\lambda\_{1} \\in \\mathcal{T}\_{\\tau\_{1}}}\\,}c\_{1}(\\tau\_{1}} & \\left. - \\lambda\_{1}\\, \\middle| \\,\\mathbf{c})\\,{\\int\_{\\mu\_{1} \\in \\mathcal{T}\_{\\lambda\_{1}}}\\,}w\_{1}(\\lambda\_{1} - \\mu\_{1}\\, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\times \\right. \\\\ & {\\times x(\\mu\_{1})\\, d\\tau\_{1}d\\lambda\_{1}d\\mu\_{1},} \\\\ \\end{aligned}$$  
(4.89)

  
$$\\begin{aligned} & \\left. \\int\_{\\tau\_{1} \\in \\mathcal{T}}\\int\_{\\tau\_{2} \\in \\mathcal{T}}\\, w\_{2}(t - \\tau\_{1},t - \\tau\_{2}\\, \\middle| \\,\\mathbf{a},\\mathbf{c})\\, x(\\tau\_{1})x(\\tau\_{2})\\, d\\tau\_{1}d\\tau\_{2} = \\right. \\\\ {- \\int\_{\\tau\_{1} \\in \\mathcal{T}}} & \\left. g\_{1}(t - \\tau\_{1} - \\tau\_{2}\\, \\middle| \\,\\mathbf{a})\\int\_{\\lambda\_{1} \\in \\mathcal{T}\_{\\tau\_{1}}}\\int\_{\\lambda\_{2} \\in \\mathcal{T}\_{\\tau\_{2}}}\\, c\_{2}(\\tau\_{1} - \\lambda\_{1},\\tau\_{2} - \\lambda\_{2}\\, \\middle| \\,\\mathbf{c}) \\times \\right. \\\\ \\times & \\left. \\int\_{\\mu\_{1} \\in \\mathcal{T}\_{\\lambda\_{1}}}\\int\_{\\mu\_{2} \\in \\mathcal{T}\_{\\lambda\_{2}}}\\, w\_{1}(\\lambda\_{1} - \\mu\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c})w\_{1}(\\lambda\_{2} - \\mu\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\times \\right. \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad} \\times x(\\mu\_{1})x(\\mu\_{2})\\, d\\tau\_{1}d\\tau\_{2}d\\lambda\_{1}d\\lambda\_{2}d\\mu\_{1}d\\mu\_{2} -} \\\\ & \\left. \\text{\\quad\\quad}\\text{\\quad\\quad} - \\int\_{\\tau\_{1} \\in \\mathcal{T}}\\int\_{\\tau\_{2} \\in \\mathcal{T}}\\, g\_{2}(t - \\tau\_{1},t - \\tau\_{2}, \\middle| \\,\\mathbf{a}) \\times \\right. \\\\ & \\left. \\text{\\quad\\quad} \\times \\int\_{\\lambda\_{1} \\in \\mathcal{T}\_{\\tau\_{1}}}\\int\_{\\lambda\_{2} \\in \\mathcal{T}\_{\\tau\_{2}}}c\_{1}(\\tau\_{1} - \\lambda\_{1})c\_{1}(\\tau\_{2} - \\lambda\_{2}, \\middle| \\,\\mathbf{c})\\, \\times \\right. \\\\ & \\left. \\text{\\quad\\quad}\\text{\\quad\\quad} \\times \\int\_{\\mu\_{1} \\in \\mathcal{T}\_{\\lambda\_{1}}}\\int\_{\\mu\_{2} \\in \\mathcal{T}\_{\\lambda\_{2}}}\\, w\_{1}(\\lambda\_{1} - \\mu\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\times \\right. \\\\ & \\left. \\text{\\quad\\quad}w\_{1}(\\lambda\_{2} - \\mu\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c})\\, d\\tau\_{1}d\\tau\_{2}d\\lambda\_{1}d\\lambda\_{2}d\\mu\_{1}d\\mu\_{2},\\cdots. \\right. \\\\ \\end{aligned}$$  

This system consists of homogeneous (with respect to the powers of *x*) integral equations with a recursive structure. Using the multidimensional Fourier transform (see the details in \[[42](#refbib.xhtml#r42), [178](#refbib.xhtml#r178)\]), write the final expressions

  
$$\\begin{aligned} & \\left. \\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}W(s\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c}) = \\frac{\\left. G\_{1}(s\_{1}, \\middle| \\,\\mathbf{a}) \\right.}{\\left. 1 + G\_{1}(s\_{1}, \\middle| \\,\\mathbf{a})C(s\_{1}, \\middle| \\,\\mathbf{c}) \\right.}, \\right. \\\\ & \\left. \\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}W(s\_{1},s\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c}) = \\right. \\\\ & {\\quad = \\frac{\\left. - G\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{a})\\, C\_{2}(s\_{1},s\_{2}, \\middle| \\,\\mathbf{c})\\, W\_{1}(s\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c})W\_{1}(s\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\right.}{\\left. 1 + .G\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{a})C\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{c}) \\right.} +} \\\\ & {+ \\frac{\\left. G\_{2}(s\_{1},s\_{2}, \\middle| \\,\\mathbf{a})W\_{1}(s\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c})\\lbrack C\_{1}(s\_{2}, \\middle| \\,\\mathbf{c})W\_{1}(s\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c}) - 2C\_{1}(s\_{2}, \\middle| \\,\\mathbf{c})\\rbrack \\right.}{\\left. 1 + G\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{a})C\_{1}(s\_{1} + s\_{2}), \\middle| \\,\\mathbf{c} \\right.},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\cdots} \\\\ \\end{aligned}$$  
(4.90)

Here *s*[1], …, *s*[*i*] are the complex parameters of the multidimensional Fourier transform.

Therefore, the \[(SI,FB)–EO\] RPM (4.3.3) can be written as the \[SI–EO\] RPM (4.2.4). This transformation may be fruitful in machine learning problems for randomized dynamic regression models.

### 4.3.4Nonlinear dynamic models with polynomial nonlinearities

In the previous subsection, we have studied the procedure of using the orthogonal polynomials in the \[SI–EO\] RPMs. Now consider this procedure subject to the \[(SI,FB)–EO\] RPMs. For the \[(SI,FB)–EO\] RPM with the structure shown in [Fig. 4.21(a)](#chapter4.xhtml#f4_21),

  
$$\\begin{aligned} {y(t)} & {= {\\int\_{\\mathcal{T}}w}(t - \\tau)\\,{\\sum\\limits\_{k = 0}^{K}w\_{k}}g\_{k}(\\varepsilon(\\tau))\\, d\\tau,} \\\\ {z(t)} & {= {\\int\_{\\mathcal{T}}c}(t - \\tau)\\,{\\sum\\limits\_{m = 0}^{M}v\_{m}}c\_{m}(y(\\tau))\\, d\\tau,} \\\\ {\\varepsilon(t)} & {= x(t) - z(t).} \\\\ \\end{aligned}$$  
(4.91)

![Figure 4.21](images/fig4_21.jpg)

[Figure 4.21](#chapter4.xhtml#f4_21b)

Another \[(SI,FB)–EO\] RPM (see [Fig. 4.21(b)](#chapter4.xhtml#f4_21)) is described by the following system of equations:

  
$$\\begin{aligned} {y(t)} & {= {\\sum\\limits\_{k = 0}^{K}w\_{k}}g\_{k}(u(\\tau))\\, d\\tau,} \\\\ {u(t)} & {= {\\int\_{\\mathcal{T}}w}(t - \\tau)\\,\\varepsilon(\\tau)\\, d\\tau,} \\\\ {e(t)} & {= {\\int\_{\\mathcal{T}}c}(t - \\tau)\\, y(\\tau)\\, d\\tau,} \\\\ \\end{aligned}$$  
(4.92)

  
$$\\begin{aligned} {z(t)} & {= {\\sum\\limits\_{m = 0}^{M}v\_{m}}c\_{m}(e(\\tau))\\, d\\tau,} \\\\ {\\varepsilon(t)} & {= x(t) - z(t).} \\\\ \\end{aligned}$$  
(4.93)

The parameters of these RPMs, **w** and **v**, are random, independent and take values within the intervals

  
$$\\begin{array}{r} {\\mathbf{w} \\in \\mathcal{W} = \\lbrack\\mathbf{w}^{-},\\mathbf{w}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{v} \\in \\mathcal{V} = \\lbrack\\mathbf{v}^{-},\\mathbf{v}^{+}\\rbrack.} \\\\ \\end{array}$$  
(4.94)

Recall that the orthogonal polynomials can be applied for approximating the continuous nonlinear functions and, moreover, the discontinuous nonlinearities, which forms their distinctive feature. However, the orthogonal property of the polynomials holds only on a certain set (the domain of definition) and in a certain functional space.

The usage procedure of the orthogonal polynomials from [Section 3.2](#chapter3.xhtml#sec3_2) is naturally extended to the \[(SI,FB)–EO\] RPMs.

## 4.4Probabilistic Characteristics of Randomized Parameters and Ensembles

The models used in the RML procedures have realizations of *randomized parameters*, which generate the *ensembles* of random objects (vectors, trajectories, events) at the output of these models. The properties of both are described in terms of appropriate probabilistic characteristics.

**1. Probabilistic characteristics of randomized parameters**

The RPMs under study involve randomized interval-type parameters with desired probabilistic properties. We will discriminate between

*   the *original* parameters **a** = {*a*[1],…,*a*[*n*]}, which take values within the *n*\-dimensional parallelepiped 𝒜 with arbitrary-size faces, i.e.,
    
      
    $$\\begin{array}{r} {\\mathcal{A} = \\lbrack\\mathbf{a}^{-},\\mathbf{a}^{+}\\rbrack = \\otimes\_{i = 1}^{n}\\mathcal{A}\_{i} = \\lbrack a\_{i}^{-},a\_{i}^{+}\\rbrack,\\text{\\quad\\quad}\\text{and}} \\\\ \\end{array}$$  
    (4.95)
    
*   the *relative nonnegative* parameters **u** = {*u*[1],…,*u*[*n*]}, which take values within the *n*\-dimensional nonnegative parallelepiped 𝒰 with the unit faces, i.e.,
    
      
    $$\\begin{array}{r} {\\mathcal{U} = \\lbrack\\mathbf{0},\\mathbf{1}\\rbrack.} \\\\ \\end{array}$$  
    (4.96)
    

The relative nonnegative parameters are related to the original ones by

  
$$\\begin{aligned} a\_{i} & {= a\_{i}^{-} + u\_{i}\\delta\_{i},\\quad\\delta\_{i} = a\_{i}^{+} - a\_{i}^{-},\\text{\\quad\\quad}i = \\overline{1,n},} \\\\ \\mathbf{a} & {= \\mathbf{a}^{-} + \\Delta\\mathbf{u},\\text{\\quad\\quad}\\Delta = \\text{diag}\\lbrack(a\_{i}^{+} - a\_{i}^{-})\\,,\\, i = \\overline{1,n}\\rbrack.} \\\\ \\end{aligned}$$  
(4.97)

The model parameters of these types undergo randomization in accordance with the desired probabilistic characteristics, more specifically, in accordance with the PDFs, *P*(**a**) for the original parameters **a** and *W*(**u**) for the relative nonnegative parameters **u**. In the general case, the elements of the vectors **a** and **u** can be related to each other. Their PDFs represent multivariable functions of general form. If the parameters are independent, then the corresponding PDFs have the multiplicative structure:

  
$$\\begin{array}{r} {P(\\mathbf{a}) = {\\prod\\limits\_{i = 1}^{n}P\_{i}}(a\_{i}),\\text{\\quad\\quad}W(\\mathbf{u}) = {\\prod\\limits\_{i = 1}^{n}w\_{i}}(u\_{i}).} \\\\ \\end{array}$$  
(4.98)

For making presentation compact, let us introduce the following terminological abbreviations:

*   RPM-Orig for the randomized parametric models with the original parameters **a** and the *PDF* *P*(**a**);
    
*   RPM-Rel for the randomized parametric models with the relative nonnegative parameters **u** and the *PDF* *W*(**u**).
    

**2. Empirical probabilistic characteristics of ensembles**

The randomized models output the ensembles of random vectors (static models), the ensembles of time-varying functions, i.e., trajectories (dynamic models), or the ensembles of random events. For each model, these ensembles appear as the result of generating its the randomized parameters. The ensembles can be described in quantitative terms using the well-known probabilistic characteristics of mathematical statistics.

Consider an arbitrary ensemble ${\\hat{\\mathcal{Y}}}\_{T}$ of trajectories *ŷ*(*t*) on a finite time interval 𝒯 = \[0, *T*\], that is, generated by the one-dimensional RPM-Orig model with a given PDF. An example of such an ensemble is presented in [Fig. 4.23](#chapter4.xhtml#f4_23). Assume that it contains *N* trajectories. Denote by *ŷ*(*t*^(\*)) its cutset under a fixed value *t* = *t*^(\*). This cutset forms a collection of values (realizations) of the random variable *ŷ*(*t*^(\*)), which will be used for empirical estimation.

![Figure 4.23](images/fig4_23.jpg)

[Figure 4.23](#chapter4.xhtml#f4_23b)

*A) The evolution of mean trajectory*. The mean value of the random variable *ŷ*(*t*^(\*)) is given by

  
$$\\begin{array}{r} {\\overline{y}(t^{\*}) = \\frac{1}{N}{\\sum\\limits\_{k = 1}^{N}{\\hat{y}}^{(k)}}(t^{\*}),} \\\\ \\end{array}$$  
(4.99)

where *ŷ*^((*k*))(*t*^(\*)) denote the realizations of the random variable *ŷ*(*t*^(\*)).

Calculating these means for different times *t*^(\*) ∈ 𝒯, we obtain a collection of empirical estimates $\\overline{y}(t\_{u}^{\*}),\\, u \\in \\overline{1,U}.$ They can be approximated using a continuous curve $\\overline{y}(t),$ which forms the mean trajectory \[[104](#refbib.xhtml#r104)\].

*B) The evolution of the empirical variance pipe*. Take the ensemble ${\\hat{\\mathcal{Y}}}\_{T}$ illustrated in [Fig. 4.23](#chapter4.xhtml#f4_23), and consider its cutset *ŷ*(*t*^(\*)). Define the random variable

  
$$\\begin{array}{r} {D(t^{\*}) = {\\lbrack\\hat{y}(t^{\*}) - \\overline{y}(t^{\*})\\rbrack}^{2}.} \\\\ \\end{array}$$  
(4.100)

The mean of this random variable (i.e., the variance of the random variable *ŷ*(*t*^(\*))) is given by

  
$$\\begin{array}{r} {\\overline{D}(t^{\*}) = \\frac{1}{N - 1}{\\sum\\limits\_{k = 1}^{N}D^{(k)}}(t^{\*}),} \\\\ \\end{array}$$  
(4.101)

where *D*^((*k*))(*t*^(\*)) denote the realizations of the random variable *D*(*t*^(\*)) (4.100).

Introduce the standard deviation of the random variable *ŷ*(*t*^(\*)) from its mean $\\overline{y}(t^{\*})$:

  
$$\\begin{array}{r} {\\sigma(t^{\*}) = \\sqrt{\\overline{D}(t^{\*})}.} \\\\ \\end{array}$$  
(4.102)

Under an assumption that *t*^(\*) takes values within the interval 𝒯, let us approximate the resulting points using a continuous curve—the standard deviation trajectory *σ*(*t*).

Define two trajectories, $\\delta\_{\\pm} = \\overline{y}(t) \\pm \\sigma(t).$ The domain

  
$$\\begin{array}{r} {\\mathcal{D} = \\left\\{ \\hat{y}:\\delta\_{-}(t) \\leq \\hat{y}(t) \\leq \\delta\_{+}(t) \\right\\}} \\\\ \\end{array}$$  
(4.103)

will be called *the standard deviation pipe*. [Figure 4.23](#chapter4.xhtml#f4_23) demonstrates the standard deviation pipe 𝒟 about the mean trajectory $\\overline{y}(t).$

*C) The evolution of the empirical probability density function*. The empirical estimates of the PDFs can be constructed using the random variable realizations *ŷ*(*t*^(\*)) at a fixed time *t*^(\*).

The empirical PDF, i.e., the histogram *p*\[*ŷ*(*t*^(\*))\], is constructed in accordance with the well-known rules \[104\]. Denote by *ŷ*^−(*t*^(\*)) and *ŷ*^+(*t*^(\*)) the left and right limits, respectively, for the random variable *ŷ*(*t*^(\*)). Next, divide the interval \[*ŷ*^−(*t*^(\*)), *ŷ*^+(*t*^(\*))\] into *J* subintervals $\\eta\_{j},\\,(j = \\overline{1,J})$ of the length (*ŷ*^+(*t*^(\*)) − *ŷ*^−(*t*^(\*)))/*J*. The empirical probability density function is the frequency with which the values of the random variable *ŷ*(*t*^(\*)) get into the subinterval $\\eta\_{j},\\,(j = \\overline{1,J}),$ i.e.,

  
$$\\begin{array}{r} {p\_{j} = \\frac{M\_{j}}{M},} \\\\ \\end{array}$$  
(4.104)

where *M*[*j*] gives the number of values *ŷ*(*t*^(\*)) within the subinterval *η*[*j*] and *M* is the total number of trajectories in the ensemble. [Figure 4.24](#chapter4.xhtml#f4_24) provides an example of the histogram *p*\[*ŷ*(*t*^(\*))\]. The evolution of the histogram can be observed by varying the time *t*^(\*). As a rule, an ensemble contains very many trajectories. Therefore, the histogram can be approximated with good accuracy using a continuous curve *P̂*\[*ŷ*(*t*^(\*))\].

![Figure 4.24](images/fig4_24.jpg)

[Figure 4.24](#chapter4.xhtml#f4_24b)

*D). The evolution of the empirical median trajectory*. Often the empirical PDF has no symmetry. In such cases, the median trajectory seems to be more informative. Consider the PDF *P̂*\[*ŷ*(*t*^(\*))\], and define a value *z*(*t*^(\*)) such that

  
$$\\begin{array}{r} {{\\int\_{{\\hat{y}}^{-}(t^{\*})}^{z(t^{\*})}\\hat{P}}(x)dx = {\\int\_{z(t^{\*})}^{{\\hat{y}}^{-}(t^{\*})}\\hat{P}}(x)dx.} \\\\ \\end{array}$$  
(4.105)

The value *z*(*t*^(\*)) of the random variable *ŷ*(*t*^(\*)) is called the median for the time *t*^(\*). Performing these calculations for all *t*^(\*) ∈ 𝒯, obtain a continuous curve, which will be called the median trajectory of the ensemble.

*E). The evolution of the *α*\-quantiles of the empirical PDF*. For a fixed time *t*^(\*), introduce the empirical probability density function

  
$$\\begin{array}{r} {{\\hat{F}}\_{t^{\*}}(y) = {\\int\_{{\\hat{y}}^{-}(t^{\*})}^{y}{\\hat{P}}\_{t^{\*}}}(v)dv.} \\\\ \\end{array}$$  
(4.106)

According to the definition given in \[104\], the *α*[*t*^(\*)]\-quantile (*α*[*t*^(\*)] ∈ \[0, 1\]) of the distribution *F̂*[*t*^(\*)](*y*) of a random variable *y* is the number *y*[*α*[*t*^(\*)]] satisfying the inequalities

  
$$\\begin{array}{r} {Pb\\left\\{ y \\leq y\_{\\alpha\_{t^{\*}}} \\right\\} \\leq \\alpha\_{t^{\*}}} \\\\ \\end{array}$$  
(4.107)

and

  
$$\\begin{array}{r} {Pb\\left\\{ y > y\_{\\alpha\_{t^{\*}}} \\right\\} \\leq 1 - \\alpha\_{t^{\*}},} \\\\ \\end{array}$$  
(4.108)

where *Pb* denotes probability. The *α*[*t*^(\*)]\-quantile is illustrated in [Fig. 4.25(b)](#chapter4.xhtml#f4_25). By analogy with items A)–C), consider different cutsets *t*^(\*) ∈ 𝒯 of the ensemble to get the *α*[*t*]\-quantile trajectory, see [Fig. 4.25(b)](#chapter4.xhtml#f4_25).

*F). The evolution of the empirical confidence intervals and confidence levels*. The *α*[*t*^(\*)]\-quantile allows us to define an interval (known as *the confidence interval*) that covers the values of the random variable *ŷ*(*t*^(\*)) with the probability *α*[*t*^(\*)] (*the confidence level*).

By definition, the confidence interval

  
$$\\begin{array}{r} {C\_{t^{\*}} = \\lbrack y\_{1 - \\alpha\_{t^{\*}}/2},y\_{1 + \\alpha\_{t^{\*}}/2}\\rbrack} \\\\ \\end{array}$$  
(4.109)

covers the values of the random variable *ŷ*(*t*^(\*)) with the confidence level

  
$$\\begin{array}{r} {P\\lbrack\\hat{y}(t^{\*}) \\in C\_{t^{\*}}\\rbrack = \\alpha\_{t^{\*}}.} \\\\ \\end{array}$$  
(4.110)

Letting *t*^(\*) = *t* ∈ 𝒯 in both formulas, construct the confidence domain *C*(*t*), as illustrated in [Fig. 4.25(c)](#chapter4.xhtml#f4_25).

![Figure 4.25](images/fig4_25.jpg)

[Figure 4.25](#chapter4.xhtml#f4_25b)

**3. The moment characteristics of the ensemble**

Consider a one-dimensional ensemble ${\\hat{\\mathcal{Y}}}\_{T}$ consisting of random trajectories *ŷ*(*t* | **a**), where *t* ∈ 𝒯. The parameters **a** are randomized with a given PDF *P*(**a**). Let *t* = *t*^(\*) be fixed. Then *ŷ*(*t*^(\*) | **a**) represents a function of the random argument **a**.

Define its *kth moments* by

  
$$\\begin{array}{r} \\left. M\_{k}(t^{\*}) = \\mathcal{M}\\left\\{ y(t^{\*}\\, \\middle| \\,\\mathbf{a}) \\right\\} = {\\int\_{\\mathcal{A}}y^{k}}(t^{\*}\\, \\middle| \\,\\mathbf{a})P(\\mathbf{a})d\\mathbf{a}. \\right. \\\\ \\end{array}$$  
(4.111)

Introduce *the k-means* of these moments in the form

  
$$\\begin{array}{r} {m\_{k}(t^{\*}) = M\_{k}^{1/k}(t^{\*}).} \\\\ \\end{array}$$  
(4.112)

For *k* = 1, the moment coincides with its mean, i.e., *M*[1] = *m*[1].

Assuming *t*^(\*) to be a variable that takes values within the interval 𝒯, find the *k*th moment trajectory *M*[*k*](*t*) and the *k*\-mean trajectory *m*[*k*](*t*).

In some applications, the object's output vector consists of the elements acting as the average functionals with random parameters. For example, consider option trading \[[15](#refbib.xhtml#r15), [182](#refbib.xhtml#r182)\]. Each of *r* financial derivatives contains *p* random parameters *a*[1], …, *a*[*p*], which are realized in the course of trading with some PDF *P*(**a**). The relations between the financial derivatives and parameters are described by functionals 𝒢[1](**a**), …, 𝒢[*r*](**a**). As a rule, they belong to the class of power functionals; in the elementary statement, these functionals have the form

  
$$\\begin{array}{r} {\\mathcal{G}\_{1}(\\mathbf{a}) = {\\sum\\limits\_{k = 1}^{p}c\_{k}}a\_{k},} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {\\mathcal{G}\_{2}(\\mathbf{a}) = {\\sum\\limits\_{k = 1}^{p}c\_{k}}a\_{k} + {\\sum\\limits\_{k\_{1} = 1}^{r}{\\sum\\limits\_{k\_{2} = 1}^{r}c\_{k\_{1}k\_{2}}}}a\_{k\_{1}}a\_{k\_{2}},} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} \\ldots \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {\\mathcal{G}\_{r}(\\mathbf{a}) = {\\sum\\limits\_{k = 1}c\_{k}}a\_{k} + {\\sum\\limits\_{k\_{1},k\_{2}}c\_{k\_{1},k\_{2}}}a\_{k\_{1}}a\_{k\_{2}} + \\ldots + {\\sum\\limits\_{k\_{1},\\ldots,k\_{r}}c\_{k\_{1},\\ldots,k\_{r}}}a\_{k\_{1}}\\cdots a\_{k\_{r}}.} \\\\ \\end{array}$$  

The more efficient models that are used to predict future mean prices involve the integral power functionals; their cores depend on the time variables, *c*(*τ*), *c*(*τ*[1], *τ*[2]), ….

In both statements, the relations under consideration give the mean prices of the financial derivatives, i.e.,

  
$$\\begin{array}{r} {{\\int\_{\\mathcal{A}}\\mathcal{G}\_{1}}(\\mathbf{a})P(\\mathbf{a})d\\mathbf{a},\\,{\\int\_{\\mathcal{A}}\\mathcal{G}\_{2}}(\\mathbf{a})P(\\mathbf{a})d\\mathbf{a},.....} \\\\ \\end{array}$$  

These mean price formulas represent the combinations of the weighted moments of the random vector **a**. In the option trading models, the object's output **y** is the predicted mean prices for the corresponding financial derivatives.

# CHAPTER 5 ENTROPY-ROBUST ESTIMATION PROCEDURES FOR RANDOMIZED MODELS AND MEASUREMENT NOISES

DOI: [10.1201/9781003306566-5](https://doi.org/10.1201/9781003306566-5)

The main stage of each randomized machine learning procedure is to estimate the probability density functions. Estimation involves input and output data arrays. According to a common hypothesis, output arrays contain errors due to imperfect measurements. The core of the estimation procedures consists in a model with *randomized* interval-type parameters, which can be *original or relative*. A static model with randomized parameters generates an ensemble of random vectors, whereas a dynamic model an ensemble of random trajectories. They are characterized in terms of different-order moments, which serve for balancing the model's output with its input data.

The PDF estimation problem is formulated as the problem to find the “best” functions under maximum uncertainty. The latter is measured using the information entropy of the model and measurement noises. Maximizing the entropy, we construct the entropy-optimal PDFs of the model parameters and the “worst” PDFs of the noises in the sense of this criterion.

## 5.1Structure of Entropy-Robust Estimation Procedure

Consider the general phenomenological structure of the estimation procedure. It represents a sequence of stages shown in [Fig. 5.1](#chapter5.xhtml#f5_1). This procedure yields the estimated PDFs of the model parameters and noises—*P*^(\*)(**a**) and $Q(\\overline{\\xi}),$ respectively.

![Figure 5.1](images/fig5_1.jpg)

[Figure 5.1](#chapter5.xhtml#f5_1b)

**1. Data source (DS)** generates an array of input data vectors **x**(*t*[1]), …, **x**(*t*[*s*]) and a corresponding array of output data vectors **y**(*t*[1]), …, **y**(*t*[*s*]), where *s* denotes the number of measurements, **x** ∈ *R*^(*n*) and **y** ∈ *R*^(*m*). Sometimes, it seems convenient to write these data arrays in the form of matrices $\\left. X = \\lbrack\\, x\_{ij}\\, \\middle| \\, i = \\overline{1,n};\\, j = \\overline{1,s}\\,\\rbrack \\right.$ and $\\left. Y = \\lbrack\\, y\_{ij}\\, \\middle| \\, i = \\overline{1,m};\\, j = \\overline{1,s}\\,\\rbrack. \\right.$ By a standard assumption, input data are measured perfectly and output data with errors, and this aspect should be taken in account for estimation procedure design.

**2. Randomized parametric model (RPM)** generally represents a dynamic system with randomized *original* parameters **a** ∈ *R*^(*r*) that take values within the *r*\-dimensional parallelepiped

  
$$\\begin{array}{r} {\\mathbf{a} \\in \\mathcal{A} = \\lbrack\\mathbf{a}^{-},\\mathbf{a}^{+}\\rbrack \\in R^{r},\\quad\\mathcal{A} = {\\underset{i = 1}{\\overset{r}{\\cup}}\\mathcal{A}\_{i}},\\text{\\quad\\quad}\\mathcal{A}\_{i} = \\lbrack a\_{i}^{-},a\_{i}^{+}\\rbrack.} \\\\ \\end{array}$$  
(5.1)

The probabilistic properties of the randomized original parameters are described by the PDF *P*(**a**). The models of this class will be referred to as the *RPM-Orig* models.

In many cases, it is reasonable to use nonnegative *relative* randomized parameters **u** ∈ ℐ = \[**0**, **1**\]; ℐ ∈ *R*[+]^(*r*). Recall that they have the following relation to the original parameters:

  
$$\\begin{array}{r} {\\mathbf{a} = \\mathbf{a}^{-} + A\\,\\mathbf{u},\\quad\\mathbf{u} \\in \\mathcal{I},} \\\\ \\end{array}$$  
(5.2)

where

  
$$\\begin{array}{r} {A = \\text{diag}\\,\\lbrack a\_{i}^{+} - a\_{i}^{-}\\, i = \\overline{1,r}\\rbrack.} \\\\ \\end{array}$$  
(5.3)

The probabilistic properties of the randomized relative parameters are characterized in terms of the PDF *W*(**u**). The models of this class will be mentioned as the *RPM-Rel* models.

For *each realization* of the randomized parameters, the models generate trajectories with the given PDFs, which have the following functional descriptions:

*   for the RPM-Orig model,
    
      
    $$\\begin{aligned} \\left. \\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, P(\\mathbf{a})\\rbrack \\right. & {= \\mathcal{B}\\lbrack\\mathbf{x}(t\_{j},\\tau),\\mathbf{a},P(\\mathbf{a});(t\_{j},\\tau) \\in \\mathcal{T}\\rbrack,} \\\\ & {\\text{\\quad\\quad}j = \\overline{1,s};} \\\\ \\end{aligned}$$  
    (5.4)
    
*   for the RPM-Rel model,
    
      
    $$\\begin{array}{r} \\left. \\mathbf{z}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack = \\mathcal{D}\\lbrack\\mathbf{x}(t\_{j},\\tau),\\,\\mathbf{a}^{-} + A\\,\\mathbf{u},\\, W(\\mathbf{u});(t\_{j},\\tau) \\in \\mathcal{T}\\rbrack,j = \\overline{1,s}. \\right. \\\\ \\end{array}$$  
    

In formulas (5.4, 5.5), ℬ and 𝒟 are integral functionals.

At the discrete measurement times, the randomized models output the ensembles of corresponding trajectories, i.e.,

*   for the RPM-Orig model,
    
      
    $$\\begin{array}{r} \\left. \\mathcal{Y}\\lbrack t\_{j}\\, \\middle| \\, P(\\mathbf{a})\\rbrack = \\left\\{ \\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, P(\\mathbf{a}) \\right\\},\\text{\\quad\\quad}t\_{j} \\in \\mathcal{T},\\, j = \\overline{1,s}, \\right. \\\\ \\end{array}$$  
    (5.5)
    
*   for the RPM-Rel model,
    
      
    $$\\begin{array}{r} \\left. \\mathcal{Z}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack = \\left\\{ \\mathbf{z}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack,\\text{\\quad\\quad}t\_{j} \\in \\mathcal{T},\\, j = \\overline{1,s}. \\right. \\right. \\\\ \\end{array}$$  
    (5.6)
    

**3. Measurement error generator (MEG)** is intended to simulate the measurement errors in output data. This device produces the ensembles of random vectors with certain probabilistic properties. It consists of a vector randomizer (*VR*) with a standard PDF and a converter (*C*) of these vectors into the ones with the given PDFs. The standard PDF is the density of the random vectors that have the uniform distribution on the unit nonnegative *m*\-dimensional cube. The converter transforms these vectors into the random vectors with a PDF that is defined by the machine learning of the model.

Thus, the MEG outputs the random noise vectors $\\overline{\\xi}(t\_{j}) = {\\overline{\\xi}}^{(j)},\\,(j = \\overline{1,s}\\,),$ where ${\\overline{\\xi}}^{(j)} \\in R^{m}.$ In the same way, describe the noise arrays that appear as the result of data accumulation using a matrix $\\left. \\Xi = \\lbrack\\,\\xi\_{ij}\\, \\middle| \\, i = \\overline{1,m};\\, j = \\overline{1,s}\\,\\rbrack. \\right.$

The elements of the noise vectors are assumed to be independent and belonging to the intervals

  
$$\\begin{aligned} {\\overline{\\xi}}^{(j)} & {\\in \\mathcal{K}\_{j} = \\lbrack{\\overline{\\xi}}\_{-}^{(j)},{\\overline{\\xi}}\_{+}^{(j)}\\rbrack,\\quad j = \\overline{1,s},} \\\\ \\Xi & {\\in \\mathcal{K} = \\otimes\_{j = 1}^{s}\\mathcal{K}\_{j}.} \\\\ \\end{aligned}$$  
(5.7)

It is often useful to introduce the relative nonnegative vectors ${\\overline{\\eta}}^{(j)}$ that take values within the unit nonnegative *m*\-dimensional cube ℰ[*j*] = \[**0**, **1**\]. In addition, define the auxiliary variable matrix $\\left. E = \\lbrack\\,\\eta\_{ij}\\, \\middle| \\, i = \\overline{1,m};\\, j = \\overline{1,s}\\,\\rbrack. \\right.$ The transformation of the random vectors ${\\overline{\\xi}}^{(j)}$ into the vectors *η*^((*j*)) runs as follows:

  
$$\\begin{aligned} {{\\overline{\\xi}}^{(j)} = {\\overline{\\xi}}\_{-}^{(j)} +} & {K\_{j}\\,{\\overline{\\eta}}^{(j)},\\quad K\_{j} = \\text{diag}\\,\\lbrack\\xi\_{i, +}^{(j)} - \\xi\_{i, -}^{(j)}\\rbrack,} \\\\ & {\\, i = \\overline{1,m};j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.8)

The probabilistic properties of the noises are characterized by the PDF $Q\_{j}({\\overline{\\xi}}^{(j)})$ defined on 𝒦[*j*] (5.7) or by the PDF $G\_{j}({\\overline{\\eta}}^{(j)})$ defined on the unit cube ℰ. If these density functions are specified, then the MEG produces the ensembles of random vectors that simulate

*   the original noises
    
      
    $$\\begin{array}{r} {\\mathcal{Q}\_{j}\\lbrack Q\_{j}({\\overline{\\xi}}^{(j)})\\rbrack = \\left\\{ {\\overline{\\xi}}^{(j)}\\lbrack Q\_{j}({\\overline{\\xi}}^{(j)})\\rbrack \\right\\},\\text{\\quad\\quad}j = \\overline{1,s};} \\\\ \\end{array}$$  
    (5.9)
    
*   the nonnegative relative noises
    
      
    $$\\begin{array}{r} {\\mathcal{G}\_{j}\\lbrack G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack = \\left\\{ {\\overline{\\eta}}^{(j)}\\lbrack G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack \\right\\},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
    (5.10)
    

**4. Measurement model (MM)** simulates the influence of the measurement errors on the estimation results. By assumption, this influence is described well by the additive measurement model. The ensembles of the measurement model outputs have the following form:

*   for the RPM-Orig model,
    
      
    $$\\begin{aligned} {\\mathcal{V}\_{j}\\lbrack P(\\mathbf{a}),Q\_{j}({\\overline{\\xi}}^{(j)})\\rbrack} & {= \\mathcal{Y}\_{j}\\lbrack P(\\mathbf{a})\\rbrack + \\mathcal{Q}\_{j}\\lbrack Q\_{j}({\\overline{\\xi}}^{(j)})\\rbrack,} \\\\ & {j = \\overline{1,s};} \\\\ \\end{aligned}$$  
    (5.11)
    
*   for the RPM-Rel model,
    
    ![](images/math5_39.jpg)

**5. Moment evaluator (ME)** performs online calculations for the moment characteristics of the ensembles generated by the measurement model.

For the randomized models, the ensembles consist of the following random trajectories:

*   for the RPM-Orig model,
    
      
    $$\\begin{array}{r} \\left. \\mathbf{v}(t\_{j}) = \\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, P(\\mathbf{a})\\rbrack + {\\overline{\\xi}}^{(j)}\\lbrack Q\_{j}({\\overline{\\xi}}^{(j)})\\rbrack; \\right. \\\\ \\end{array}$$  
    (5.12)
    
*   for the RPM-Rel model,
    
      
    $$\\begin{array}{r} \\left. \\mathbf{f}(t\_{j}) = \\mathbf{z}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack + {\\overline{\\xi}}\_{-}^{(j)} + K\_{j}{\\overline{\\eta}}^{(j)}\\lbrack G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack. \\right. \\\\ \\end{array}$$  
    (5.13)
    

As the numerical characteristics of the ensembles 𝒱[*j*] and ℱ[*j*], adopt the vectors composed of the *k*\-means of the *k*th moments (see (4.111, 4.112)), i.e.,

*   for the RPM-Orig model,
    
      
    $$\\begin{aligned} {\\mathbf{m}^{(k)}\\lbrack P(\\mathbf{a}),Q\_{j}({\\overline{\\xi}}^{(j)}),j\\rbrack} & {= \\left\\{ {\\lbrack M\_{i}^{(k)}(j)\\rbrack}^{1/k},\\, \\middle| \\, i = \\overline{1,m} \\right\\},} \\\\ & {j = \\overline{1,s};} \\\\ \\end{aligned}$$  
    (5.14)
    
*   for the RPM-Rel model,
    
      
    $$\\begin{aligned} {\\mathbf{n}^{(k)}\\lbrack W(\\mathbf{u}),G\_{j}({\\overline{\\eta}}^{(j)},j)\\rbrack} & {= \\left\\{ {\\lbrack N\_{i}^{(k)}(j)\\rbrack}^{1/k},\\, \\middle| \\, i = \\overline{1,m} \\right\\},} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
    (5.15)
    

In these formulas, the *k*th moments of the corresponding vector elements are given by

  
$$\\begin{aligned} {M\_{i}^{(k)}(j) =} & \\left. \\int\_{\\mathcal{A}}y\_{i}^{k}(t\_{j},\\, \\middle| \\,\\mathbf{a})P(\\mathbf{a})d\\mathbf{a} + \\int\_{\\Xi\_{j}}{\\lbrack\\xi\_{i}^{(j)}\\rbrack}^{k}Q\_{j}({\\overline{\\xi}}^{(j)})d\\xi\_{i}^{(j)}, \\right. \\\\ N\_{i}^{(k)} & \\left. (j) = \\int\_{\\mathcal{U}}z\_{i}^{k}(t\_{j},\\, \\middle| \\,\\mathbf{u})W(\\mathbf{u})d\\mathbf{u} + {\\lbrack\\xi^{(j})}\_{-}\\rbrack\_{i}^{k} + \\right. \\\\ & {+ K\_{ji}\\int\_{\\mathcal{E}}{\\lbrack\\eta\_{i}^{(j)}\\rbrack}^{k}G\_{j}({\\overline{\\eta}}^{(j)})d\\eta\_{i}^{(j)}.} \\\\ \\end{aligned}$$  
(5.16)

**6. Balancing model (BM)** is used to compare available output data **y** with the accepted characteristics of ensembles 𝒱 or ℱ.

For the randomized models, the balance constraints have the form

  
$$\\begin{array}{r} {\\mathbf{m}^{(k)}\\lbrack P(\\mathbf{a}),Q\_{j}({\\overline{\\xi}}^{(j)}),j\\rbrack = \\mathbf{y}(t\_{j}),\\text{\\quad\\quad}j = \\overline{1,s};} \\\\ \\end{array}$$  
(5.17)

  
$$\\begin{array}{r} {\\mathbf{n}^{(k)}\\lbrack W(\\mathbf{u}),G\_{j}({\\overline{\\eta}}^{(j)},j)\\rbrack = \\mathbf{y}(t\_{j}),\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(5.18)

**7. Machine learning algorithm (ML-A)** is intended to form optimal estimates for the PDFs of the parameters and measurement noises. As repeatedly mentioned earlier, the randomized machine learning procedure has to estimate the PDFs under the maximum uncertainty characterized by information entropy. Thus, the ML-A is searching for its constrained maximum on an admissible set in the form of the balance constraints (5.17, 5.18).

The information entropy functional ℋ is defined over the class of continuously differentiable PDFs $P(\\mathbf{a}),Q\_{1}({\\overline{\\xi}}^{(1)}),\\ldots,Q\_{s}({\\overline{\\xi}}^{(s)}),$ which describe the probabilistic properties of the randomized parameters and noises simulating the measurement errors, respectively. The entropy functional generalizes the finite-dimensional concept of information entropy.

In 1865, German physicist R. Clausius introduced a physical quantity to characterize a thermodynamic system, called *entropy*.

  
$$\\begin{array}{r} {S = \\frac{\\Delta Q}{\\Delta T}.} \\\\ \\end{array}$$  

In 1877, L. Boltzmann established a relation between the thermodynamic entropy *S* (or the physical entropy *E*) and the statistical weight *Z* for the macrostate (*Δ**Q*, *T*) of a thermodynamic system. Later on, using the hypothesis of equiprobable microstates, M. Planck wrote this relation in the form

  
$$\\begin{array}{r} {S = k\\ln Z = E.} \\\\ \\end{array}$$  

Here *k* = 1.38 ⋅ 10^( − 23) denotes the Boltzmann constant. The statistical weight of the macrostate (*Δ**Q*, *T*) is measured by the number of all possible microstates (combinations) that make up this macrostate. Recall that these terms apply to the so-called (mono- or polyatomic) gas model, which considers a system (macrosystem) of very many indistinguishable particles (molecules). The space of the system's macrostates consists of *m* nonintersecting subsets with given capacities *G*[1], …, *G*[*m*] (i.e., the number of states that can be occupied by the particles). Behaving stochastically, the particles are distributed in a random way over the states in these subsets, with the same probability and independently of each other. Let each particle be uniquely labeled, and list the resulting subsets for all labeled particles; in fact, this list is the system's microstate. Of course, the list under consideration is of a huge volume. The sublists with the same number of particles *N*[*k*] in the *k*th subset can be extracted. The number of particles *N*[*k*] is an element of the system's macrostate **N** = {*N*[1],…,*N*[*m*]}. The number of elements in a sublist (the number of microstates that induce a given macrostate) is called its statistical weight *Z* = *Z*(*N*[*k*]).

To find a relation between the statistical weight *Z* and the macrostate characteristic *N*[*k*] (the number of particles that fill the *k*th subset), we will need a certain generalization of the macrosystem model. This generalization involves information about the prior probabilities *a*[1], …, *a*[*m*] with which the particles are distributed over the subsets of the macrostate space, as well as information about the properties of states in these subsets. Note that in the gas model the prior probabilities are assumed to be equal and the state properties are not described.

Consider a macrosystem in which each state can be occupied by one particle only (otherwise, the state is unfilled). The numbers of such states in the subsets are *G*[1], …, *G*[*m*]. The distribution mechanism has the following organization. Each particle may *occupy *N*[*k*] states in the kth subset with the prior probability *a*[*k*]* randomly and independently of the other particles; hence, (*G*[*k*] − *N*[*k*]) *states remain free with the prior probability (1 − *a*[*k*])*. Denote this event by {*N*[*k*],(*G*[*k*]−*N*[*k*])}. Due to the independence of all particles in this distribution mechanism, the probability of the event makes up

  
$$\\begin{array}{r} {a\_{k}^{N\_{k}}\\,{(1 - a\_{k})}^{(G\_{k} - N\_{k})}.} \\\\ \\end{array}$$  

The number of filled states *N*[*k*] can be achieved in different distributions of the particles over the *k*th subset, i.e., different microstates. The number of such microstates *Z*(*N*[*k*]) is the number of *N*[*k*]\-combinations of *G*[*k*] particles:

  
$$\\begin{array}{r} {C\_{N\_{k}}^{G\_{k}} = \\frac{G\_{k}!}{N\_{k}!\\,(G\_{k} - N\_{k})!}.} \\\\ \\end{array}$$  

The event {*N*[*k*],(*G*[*k*]−*N*[*k*])} can be realized *either* by the 1st microstate, *or* by the 2nd microstate, …, *or* by the *C*[*N*[*k*]]^(*G*[*k*]) th microstate. Therefore, the event {*N*[*k*],(*G*[*k*]−*N*[*k*])} occurs with the probability

  
$$\\begin{array}{r} {P\_{k}(N\_{k}) = \\frac{G\_{k}!}{N\_{k}!\\,(G\_{k} - N\_{k})!}\\, a\_{k}^{N\_{k}}\\,{(1 - a\_{k})}^{(G\_{k} - N\_{k})}.} \\\\ \\end{array}$$  

Because all participants of the distribution mechanism are independent, the probability of the corresponding macrostate of this macrosystem is given by

  
$$\\begin{array}{r} {P(\\mathbf{N}) = {\\prod\\limits\_{k = 1}^{m}P\_{k}}(N\_{k}) = {\\prod\\limits\_{k = 1}^{m}\\frac{G\_{k}!}{N\_{k}!\\,(G\_{k} - N\_{k})!}}\\, a\_{k}^{N\_{k}}\\,{(1 - a\_{k})}^{(G\_{k} - N\_{k})}.} \\\\ \\end{array}$$  

According to Planck's definition, physical entropy is proportional to the logarithm of the probability distribution function, since the statistical weight is an unnormalized distribution. Therefore,

  
$$\\begin{array}{r} {\\left. S \\right.\\sim lnP(\\mathbf{N}).} \\\\ \\end{array}$$  

Then it follows that

  
$$\\begin{array}{r} {\\left. S \\right.\\sim{\\sum\\limits\_{k = 1}^{m}\\ln}G\_{k}! - \\ln(G\_{k} - N\_{k})! - \\ln N\_{k}! + N\_{k}\\ln a\_{k} + (G\_{k} - N\_{k})\\ln(1 - a\_{k}).} \\\\ \\end{array}$$  

As the values *N*[*k*] are large, employ Stirling's approximation

  
$$\\begin{array}{r} {\\ln N! = N(\\ln N - 1).} \\\\ \\end{array}$$  

In this case, the right-hand side of the expression for *S* can be written as the sum of a constant and a function of the macrostate:

  
$$\\begin{array}{r} {\\left. S \\right.\\sim C + H\_{F}(\\mathbf{N}).} \\\\ \\end{array}$$  

The function

  
$$\\begin{array}{r} {H\_{F}(\\mathbf{N}) = - {\\sum\\limits\_{k = 1}^{m}\\left\\lbrack {\\, N\_{k}\\frac{N\_{k}}{{\\widetilde{a}}\_{k}} + (G\_{k} - N\_{k})\\ln(G\_{k} - N\_{k})\\,} \\right\\rbrack},\\quad{\\widetilde{a}}\_{k} = \\frac{a\_{k}}{1 - a\_{k}},} \\\\ \\end{array}$$  

is called *the generalized Fermi information entropy*. For this function, the domain of definition is the *m*\-dimensional parallelepiped 𝒩 = \[**0**, **G**\], i.e., the set of admissible macrostates. If the parameters **a** and **G** satisfy the conditions

  
$$\\begin{array}{r} {G\_{k}a\_{k} = \\text{const},\\text{\\quad\\quad}N\_{k} \\ll G\_{k},} \\\\ \\end{array}$$  

then *H*[*F*](**N**) can be transformed into the entropy function

  
$$\\begin{array}{r} {H\_{B}(\\mathbf{N}) = - {\\sum\\limits\_{k = 1}^{m}N\_{k}}\\ln\\frac{N\_{k}}{a\_{k}G\_{k}e},} \\\\ \\end{array}$$  

which is called *the generalized Boltzmann information entropy*. This function is defined on the nonnegative orthant 𝒩 ∈ *R*[+]^(*m*), which represents the set of admissible macrostates.

The random distribution of the indistinguishable particles over the subsets in the state space consumes *r* types of resources (energy, time, finances, etc.). The available quantities of these resources are *q*[1], …, *q*[*r*]. Resource consumption is characterized by consumption functions *Φ*[1](**t**, **N**), …, *Φ*[*r*](**t**, **N**), which have parameters **t** (specific consumption rates) and depend on the macrostate vector **N**.

As the distribution process requires resources, it is possible to realize only those macrostates that satisfy the conditions

  
$$\\begin{array}{r} {\\Phi\_{i}(\\mathbf{t},\\mathbf{N}) = q\_{i},\\quad i = \\overline{1,s};\\text{\\quad\\quad}\\Phi\_{i + s}(\\mathbf{t},\\mathbf{N}) = q\_{i + s},\\quad i = \\overline{1,r-s}.} \\\\ \\end{array}$$  

These constraints define the so-called resource set 𝒟. The intersection of this set with the corresponding sets of admissible macrostates gives *the admissible set*

  
$$\\begin{array}{r} {\\mathcal{F} = \\mathcal{N}{\\cap \\mathcal{D}}.} \\\\ \\end{array}$$  

Using the above concepts and terminology, we can state *the generalized variational principle* as follows. *The macrostate that is realized in the macrosystem corresponds to the constrained maximum of the generalized information entropy*, i.e.,

  
$$\\begin{array}{r} \\left. H(\\mathbf{N})\\Rightarrow\\max\\text{~subject~to~}\\,\\,\\mathbf{N} \\in \\mathcal{F}. \\right. \\\\ \\end{array}$$  

## 5.2Entropy-Robust Estimation Algorithms for Probability Density Functions

The estimation algorithms of the PDFs form the core of the randomized machine learning procedure. They are oriented towards the corresponding classes of the randomized parametric models, the RPM-Orig and RPM-Rel models. The two classes of randomized models have technical differences. First, some estimation algorithms for the RPM-Orig model will be considered, including the general problem statement and the structure of the resulting solutions. Then these estimation algorithms will be adapted to the RPM-Rel model.

### 5.2.1Estimation algorithms for RPM-Orig model

According to (5.4, 5.12), the observable output of the RPM-Orig model at a time instant *t*[*j*] is described by

  
$$\\begin{aligned} {\\mathbf{v}(t\_{j}) = \\mathbf{y}\\lbrack t\_{j}} & \\left| \\, P(\\mathbf{a})\\rbrack + {\\overline{\\xi}}^{(j)}\\lbrack Q\_{j}({\\overline{\\xi}}^{(j)})\\rbrack, \\right. \\\\ \\left. \\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, P(\\mathbf{a})\\rbrack = \\mathcal{B}\\lbrack\\mathbf{x} \\right. & \\left. ((t\_{j},\\tau\_{l}),\\, \\middle| \\, l = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack, \\right. \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.19)

Here, ℬ denotes a matrix functional of dimensions (*m* × *n*) that characterizes an existing relation between the model's output **y**(*t*[*j*]) and the array composed of the input vectors **x**(*t*[*j*], *τ*[1]), …, **x**(*t*[*j*], *τ*[(*j* − 1)]). The measurement errors are simulated by the noise vectors ${\\overline{\\xi}}^{(j)}.$ The RPM-Orig model output (5.2.1) depends on the randomized parameters **a** with a PDF *P*(**a**) and also on the randomized noise vectors ${\\overline{\\xi}}^{(j)}$ with a PDF $Q\_{j}({\\overline{\\xi}}^{(j)});$ see (5.2.1). The available prior information about these PDFs (if any) is represented in the form of prior PDFs *P*[0](**a**) and $Q\_{j}^{0}({\\overline{\\xi}}^{(j)}).$ By assumption, the PDFs belong to the class *ℂ*¹ of all continuously differentiable functions.

*For the RPM-Orig model (5.4), the entropy-robust estimation problem of the PDFs of its parameters and measurement noises* is formulated as follows:

*   maximize the generalized Boltzmann information entropy functional \[[149](#refbib.xhtml#r149)\]
    
      
    $$\\begin{aligned} {\\mathcal{H}\\lbrack P(\\mathbf{a}),\\overline{Q}(\\xi)\\rbrack =} & {- {\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\,\\ln\\frac{P(\\mathbf{a})}{P\_{0}(\\mathbf{a})}\\, d\\,\\mathbf{a} -} \\\\ {- {\\sum\\limits\_{j = 1}^{s}\\,}{\\int\_{\\Xi\_{j}}Q\_{j}}({\\overline{\\xi}}^{(j)})} & \\left. \\ln\\frac{Q\_{j}({\\overline{\\xi}}^{(j)})}{Q\_{j}^{0}({\\overline{\\xi}}^{(j)})}d{\\overline{\\xi}}^{(j)}\\Rightarrow\\min\_{P,Q\_{1},...,Q\_{s}} \\right. \\\\ \\end{aligned}$$  
    (5.20)
    
*   subject to:
    
    *   –the normalization conditions for the PDFs, i.e.,
        
          
        $$\\begin{array}{r} {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})d\\mathbf{a} = 1,\\quad{\\int\_{\\Xi\_{j}}Q\_{j}}({\\overline{\\xi}}^{(j)})\\, d{\\overline{\\xi}}^{(j)} = 1,\\quad j = \\overline{1,s},} \\\\ \\end{array}$$  
        (5.21)
        
        and
        
    *   –the balance constraints for the *k*\-means of the output of the RPM-Orig model (5.14) and the measurements of the object's output, i.e.,
        
          
        $$\\begin{array}{r} {\\mathbf{m}^{(k)}\\lbrack P(\\mathbf{a}),Q\_{j}({\\overline{\\xi}}^{(j)}),j\\rbrack = \\mathbf{y}(t\_{j}),\\quad j = \\overline{1,s}.} \\\\ \\end{array}$$  
        (5.22)
        
        Due to (5.13), the vector $\\mathbf{m}^{(k)}\\lbrack P(\\mathbf{a}),Q\_{j}({\\overline{\\xi}}^{(j)}),j\\rbrack$ in these equality constraints has the components
        
          
        $$\\begin{aligned} & {m\_{i}^{(k)}\\lbrack j\\rbrack = \\left\\lbrack {\\int\_{\\mathcal{A}}P}(\\mathbf{a})y\_{i}^{k}\\lbrack t\_{j}\\, \\middle| \\, P(\\mathbf{a})\\rbrack\\, d\\mathbf{a} \\right\\rbrack^{1/k} +} \\\\ & {\\text{\\quad\\quad} + \\left\\lbrack {{\\int\_{\\Xi\_{j}}\\,}Q\_{j}({\\overline{\\xi}}^{(j)})\\,{\\lbrack\\xi\_{i}^{(j)}\\rbrack}^{k}\\, d\\xi\_{i}^{(j)}} \\right\\rbrack^{1/k},} \\\\ & {\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}i = \\overline{1,m},\\, j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
        (5.23)
        

Consider the case in which the balance constraints involve the 1-mean of the RPM-Orig model output:

  
$$\\begin{aligned} \\left\\lbrack {\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, P(\\mathbf{a})\\rbrack\\, d\\mathbf{a} \\right\\rbrack & {+ \\left\\lbrack {{\\int\_{\\Xi\_{j}}\\,}Q\_{j}({\\overline{\\xi}}^{(j)})\\,{\\overline{\\xi}}^{(j)}\\, d{\\overline{\\xi}}^{(j)}} \\right\\rbrack = \\mathbf{y}(t\_{j}),} \\\\ & {\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.24)

In this optimization problem, the functional constraints extract the subset $\\Omega\\lbrack P(\\mathbf{a}),Q(\\overline{\\xi})\\rbrack$ of all admissible functions, where $Q(\\overline{\\xi}) = \\left\\{ Q\_{1}({\\overline{\\xi}}^{(1)}),\\ldots,Q\_{s}({\\overline{\\xi}}^{(s)}) \\right\\},$ from the class ℂ¹. In fact, the problem (5.2.1)–(5.24) is a functional entropy-linear programming problem \[149\]. It belongs to the class of the Lyapunov-type optimization problems \[77, [174](#refbib.xhtml#r174)\], in which the admissible set of functions is described by a system of linear integral functionals.

*For the RPM-Orig model, the entropy-robust RML algorithm* has the form

  
$$\\begin{array}{r} {\\left\\lbrack {P(\\mathbf{a}),Q(\\overline{\\xi})} \\right\\rbrack^{\*} = \\arg\\max\_{\\lbrack P(\\mathbf{a}),Q(\\overline{\\xi})\\rbrack}\\left\\{ \\mathcal{H},\\, \\middle| \\,\\lbrack\\mathcal{P}(\\mathbf{a}),\\mathcal{Q}(\\overline{\\xi})\\rbrack \\in \\Omega \\right\\},} \\\\ \\end{array}$$  
(5.25)

where the admissible set Ω is given by the normalization conditions (5.21) and the empirical balance constraints (5.24).

### 5.2.2Estimation algorithms for RPM-Rel model

In the RPM-Rel model, the randomized parameters include the nonnegative relative parameters **u** and the measurement noises $\\left\\{ {\\overline{\\eta}}^{(1)},\\ldots,{\\overline{\\eta}}^{(s)} \\right\\}.$ According to (5.13), the observable output of the RPM-Rel model at a time instant *t*[*j*] is described by

  
$$\\begin{aligned} \\left. \\mathbf{f}(t\_{j}) = \\mathbf{z}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack \\right. & {+ {\\overline{\\xi}}\_{-}^{(j)} + K\_{j}{\\overline{\\eta}}^{(j)}\\lbrack G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack,} \\\\ \\left. \\mathbf{z}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack = \\mathcal{D}\\lbrack\\mathbf{x}(t\_{j},\\tau), \\right. & {\\mathbf{a}^{-} + A\\,\\mathbf{u},\\, W(\\mathbf{u});(t\_{j},\\tau) \\in \\mathcal{T}\\rbrack,} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.26)

Here, 𝒟 denotes a matrix functional of dimensions (*m* × *n*) that characterizes an existing relation between the model's output **z**(*t*[*j*]) and the array composed of the input vectors **x**(*t*[*j*], *τ*[1]), …, **x**(*t*[*j*], *τ*[(*j* − 1)]). The RPM-Rel model output (5.2.2) depends on the randomized relative parameters **u** with a PDF *W*(**u**) and also on the randomized relative noise vectors ${\\overline{\\eta}}^{(j)}$ with a PDF $G\_{j}({\\overline{\\eta}}^{(j)});$ see (5.2.2). The available prior information about these PDFs (if any) is represented in the form of prior PDFs *W*[0](**u**) and $G\_{j}^{0}({\\overline{\\eta}}^{(j)}).$ By assumption, the PDFs belong to the class *ℂ*¹ of all continuously differentiable functions.

*For the RPM-Rel model (5.1), the entropy-robust estimation problem of the PDFs of its parameters and measurement noises* is formulated as follows:

*   maximize the generalized Boltzmann information entropy functional
    
      
    $$\\begin{aligned} & {\\quad\\mathcal{H}\\lbrack W(\\mathbf{u}),\\overline{G}(\\eta)\\rbrack = - {\\int\_{\\mathcal{U}}W}(\\mathbf{u})\\,\\ln\\frac{W(\\mathbf{u})}{W\_{0}(\\mathbf{u})}\\, d\\,\\mathbf{u} -} \\\\ & \\left. - {\\sum\\limits\_{j = 1}^{s}\\,}{\\int\_{\\mathcal{E}\_{j}}G\_{j}}({\\overline{\\eta}}^{(j)})\\,\\ln\\frac{G\_{j}({\\overline{\\eta}}^{(j)})}{G\_{j}^{0}({\\overline{\\eta}}^{(j)})}d{\\overline{\\eta}}^{(j)}\\Rightarrow\\min\_{W,\\overline{G}} \\right. \\\\ \\end{aligned}$$  
    (5.27)
    
*   subject to:
    
    *   –the normalization conditions for the PDF, i.e.,
        
          
        $$\\begin{array}{r} {{\\int\_{\\mathcal{U}}W}(\\mathbf{u})d\\mathbf{u} = 1,\\text{\\quad\\quad}{\\int\_{\\mathcal{E}\_{j}}G\_{j}}({\\overline{\\eta}}^{(j)})\\, d{\\overline{\\eta}}^{(j)} = 1,\\quad j = \\overline{1,s},} \\\\ \\end{array}$$  
        (5.28)
        
        and
        
    *   –the balance constraints for the *k*\-means of the output of the RPM-Rel model (5.15) and the measurements of the object's output, i.e.,
        
          
        $$\\begin{array}{r} {\\mathbf{n}^{(k)}\\lbrack W(\\mathbf{u}),G\_{j}({\\overline{\\eta}}^{(j)}),j\\rbrack = \\mathbf{y}(t\_{j}),\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
        (5.29)
        
    
    Due to (5.15), the vector $\\mathbf{n}^{(k)}\\lbrack W(\\mathbf{u}),G\_{j}({\\overline{\\eta}}^{(j)}),j\\rbrack$ in these equality constraints has the components
    
      
    $$\\begin{aligned} {n\_{i}^{(k)}\\lbrack j\\rbrack} & {= \\left\\lbrack {\\int\_{\\mathcal{U}}W}(\\mathbf{u})z\_{i}^{k}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack\\, d\\mathbf{u} \\right\\rbrack^{1/k} +} \\\\ & {\\left\\lbrack {{\\int\_{\\mathcal{E}\_{j}}\\,}G\_{j}({\\overline{\\eta}}^{(j)})\\,{\\lbrack\\eta\_{i}^{(j)}\\rbrack}^{k}\\, d\\eta\_{i}^{(j)}} \\right\\rbrack^{1/k},} \\\\ & {\\text{\\quad\\quad}\\quad i = \\overline{1,m},\\, j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
    (5.30)
    

Consider the case in which the balance constraints involve the 1-mean of the RPM-Rel model output:

  
$$\\begin{aligned} {\\left\\lbrack {\\int\_{\\mathcal{U}}W}(\\mathbf{u})\\mathbf{z}\\lbrack t\_{j}\\, \\middle| \\, W(\\mathbf{u})\\rbrack\\, d\\mathbf{u} \\right\\rbrack +} & {\\left\\lbrack {{\\int\_{\\mathcal{E}\_{j}}\\,}G\_{j}({\\overline{\\eta}}^{(j)})\\,{\\overline{\\eta}}^{(j)}\\, d{\\overline{\\eta}}^{(j)}} \\right\\rbrack = \\mathbf{y}(t\_{j}),} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.31)

Like in the optimization problem presented above, the functional constraints extract the subset $\\Psi\\lbrack W(\\mathbf{u}),G(\\overline{\\eta})\\rbrack$ of all admissible functions, where $G(\\overline{\\eta}) = \\left\\{ G\_{1}({\\overline{\\eta}}^{(1)}),\\ldots,G\_{s}({\\overline{\\eta}}^{(s)}) \\right\\},$ from the class ℂ¹. The problem (5.27-5.31) is also of the Lyapunov type.

*For the RPM-Rel model, the entropy-robust RML algorithm* has the form

  
$$\\begin{array}{r} {\\left\\lbrack {W(\\mathbf{u}),\\overline{G}(\\overline{\\eta})} \\right\\rbrack^{\*} = \\arg\\max\_{\\lbrack W(\\mathbf{u}),\\overline{G}(\\overline{\\eta})\\rbrack}\\left\\{ \\mathcal{H},\\, \\middle| \\,\\lbrack W(\\mathbf{u}),G(\\overline{\\eta})\\rbrack \\in \\Psi \\right\\},} \\\\ \\end{array}$$  
(5.32)

where the admissible set Ψ is given by the normalization conditions (5.28) and the empirical balance constraints (5.31).

### 5.2.3Estimation algorithms for RPM-F model with measurement errors of input and output

The previous sections have studied cases of measurement errors figuring in the output only. However, in many applications, there are input data collections containing errors as well. Hence, the general RML procedure should be modified accordingly.

If errors occur in the input data, the observed output of the RPM-F model takes the following form:

  
$$\\begin{array}{r} \\left. \\mathbf{v}(t\_{j}) = \\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, F(\\mathbf{a},{\\overline{\\mu}}^{(j)})\\rbrack + \\overline{\\xi}\\lbrack Q\_{j}({\\overline{\\xi}}^{(j)})\\rbrack, \\right. \\\\ \\left. \\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, F(\\mathbf{a},{\\overline{\\mu}}^{(t\_{j})})\\rbrack = \\mathcal{B}\\lbrack\\mathbf{x}(t\_{j},\\tau) + {\\overline{\\mu}}^{(t\_{j})}\\rbrack. \\right. \\\\ \\end{array}$$  
(5.33)

Here ${\\overline{\\mu}}^{(j)}$ denotes the vector of input noises at a time instant *t*[*j*], which are of the interval type:

  
$$\\begin{array}{r} {{\\overline{\\mu}}^{(j)} \\in \\mathcal{M} = \\lbrack\\mu^{-},\\mu^{+}\\rbrack\\quad\\text{for~all}\\, t\_{j}.} \\\\ \\end{array}$$  
(5.34)

From the RPM-F model equations (5.33) it follows that the random elements are the parameters **a** and the input noise $\\overline{\\mu}.$ Their probabilistic properties are characterized by a joint probability density function $F(\\mathbf{a},{\\overline{\\mu}}^{(t\_{j})}).$ If there exists some information about this function, it is represented in the form of a prior PDF $F\_{0}(\\mathbf{a},{\\overline{\\mu}}^{(t\_{j})}).$

*For the RPM-F model (5.33), the entropy-robust estimation problem of the PDFs of its parameters and input and output measurement noises* is formulated as follows:

*   maximize the generalized Boltzmann information entropy functional
    
      
    $$\\begin{aligned} {\\mathcal{H}\\lbrack F(\\mathbf{a},\\overline{\\mu}),\\overline{Q}(\\overline{\\xi})\\rbrack} & {= - \\int\_{\\mathcal{R}}F(\\mathbf{a},\\overline{\\mu})\\,\\ln\\frac{F(\\mathbf{a},\\overline{\\mu})}{F\_{0}(\\mathbf{a},\\overline{\\mu})}\\, d\\,\\mathbf{a}\\, d\\,\\overline{\\mu} -} \\\\ {- \\sum\_{j = 1}^{s}\\,\\int\_{\\Xi\_{j}}} & \\left. Q\_{j}({\\overline{\\xi}}^{(j)})\\,\\ln\\frac{Q\_{j}({\\overline{\\xi}}^{(j)})}{Q\_{j}^{0}({\\overline{\\xi}}^{(j)})}d{\\overline{\\xi}}^{(j)}\\Rightarrow\\max\_{F,\\overline{Q}} \\right. \\\\ \\end{aligned}$$  
    (5.35)
    
*   subject to:
    
    *   —the normalization conditions for the PDFs, i.e.,
        
          
        $$\\begin{array}{r} {{\\int\_{\\mathcal{R}}F}(\\mathbf{a},\\overline{\\mu})\\, d\\mathbf{a}\\, d\\,\\overline{\\mu} = 1,\\text{\\quad\\quad}{\\int\_{\\Xi\_{j}}Q\_{j}}({\\overline{\\xi}}^{(j)})\\, d{\\overline{\\xi}}^{(j)} = 1,\\quad j = \\overline{1,s};} \\\\ \\end{array}$$  
        (5.36)
        
    *   —the balance constraints for the *k*\-means of the observed output (5.33) and the real data, i.e.,
        
          
        $$\\begin{array}{r} {\\mathbf{m}^{(k)}\\lbrack F(\\mathbf{a},\\overline{\\mu}),Q\_{j}({\\overline{\\xi}}^{(j)}),j\\rbrack = \\mathbf{y}(t\_{j}),\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
        (5.37)
        
    
    Due to (5.15), the vector $\\mathbf{m}^{(k)}\\lbrack F(\\mathbf{a},\\overline{\\mu}),Q\_{j}({\\overline{\\xi}}^{(j)}),j\\rbrack$ in these equality constraints has the components
    
      
    $$\\begin{aligned} {m\_{i}^{(k)}\\lbrack j\\rbrack =} & {\\left\\lbrack {\\int\_{\\mathcal{R}}F}(\\mathbf{a},\\overline{\\mu})\\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, F(\\mathbf{a},{\\overline{\\mu}}^{(t\_{j})})\\rbrack\\, d\\mathbf{a}d\\overline{\\mu} \\right\\rbrack^{1/k} +} \\\\ & {\\left\\lbrack {{\\int\_{\\Xi\_{j}}\\,}Q\_{j}({\\overline{\\xi}}^{(j)})\\,{\\lbrack\\xi\_{i}^{(j)}\\rbrack}^{k}\\, d\\xi\_{i}^{(j)}} \\right\\rbrack^{1/k},} \\\\ & {\\text{\\quad\\quad}\\quad i = \\overline{1,m},\\, j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
    (5.38)
    

Consider the case in which the balance constraints involve the 1-mean of the RPM-F model output:

  
$$\\begin{aligned} {m\_{i}^{(1)}\\lbrack j\\rbrack =} & \\left. {\\int\_{\\mathcal{R}}F}(\\mathbf{a},\\overline{\\mu})\\mathbf{y}\\lbrack t\_{j}\\, \\middle| \\, F(\\mathbf{a},{\\overline{\\mu}}^{(t\_{j})})\\rbrack\\, d\\mathbf{a}d\\overline{\\mu} + \\right. \\\\ & {{\\int\_{\\Xi\_{j}}\\,}Q\_{j}({\\overline{\\xi}}^{(j)})\\,\\lbrack\\xi\_{i}^{(j)}\\rbrack d\\xi\_{i}^{(j)},} \\\\ & {\\quad i = \\overline{1,m},\\, j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.39)

Like in the optimization problem presented above, the functional constraints extract the subset $\\Gamma\\lbrack F(\\mathbf{a},\\overline{\\mu}),Q(\\overline{\\xi})\\rbrack$ of all admissible functions, where $Q(\\overline{\\xi}) = \\left\\{ Q\_{1}({\\overline{\\xi}}^{(1)}),\\ldots,Q\_{s}({\\overline{\\xi}}^{(s)}) \\right\\},$ from the class ℂ¹. The problem (5.2.3—5.2.3) is also of the Lyapunov type.

*For the RPM-F model with input and output data errors, the entropy-robust RML algorithm* has the form

  
$$\\begin{array}{r} {\\left\\lbrack {F(\\mathbf{a},\\overline{\\mu}),\\overline{Q}(\\overline{\\xi})} \\right\\rbrack^{\*} = \\arg\\max\_{\\lbrack F(\\mathbf{a},\\overline{\\mu}),\\overline{Q}(\\overline{\\xi})\\rbrack}\\left\\{ \\mathcal{H},\\, \\middle| \\,\\lbrack F(\\mathbf{a},\\overline{\\mu}),\\overline{Q}(\\overline{\\xi})\\rbrack \\in \\Gamma \\right\\},} \\\\ \\end{array}$$  
(5.40)

where the admissible set Γ is given by the normalization conditions (5.36) and the empirical balance constraints (5.2.3).

## 5.3Optimality Conditions for Lyapunov-Type Problems

A comprehensive study of the Lyapunov-type functional programming problems, including a possible application of Lagrange's method of multipliers, can be found in the monographs \[77, 174\]. This section will briefly describe a mathematical framework based on the cited results and the Gateaux derivative \[[114](#refbib.xhtml#r114)\].

A minimization problem with integral nonlinear functionals (a Lyapunov-type problem) can be written as

  
$$\\begin{array}{r} \\left. \\mathcal{J}\\lbrack f(\\mathbf{x})\\rbrack = {\\int\_{\\mathcal{X}}\\Phi}\\left\\lbrack {f(\\mathbf{x})} \\right\\rbrack d\\mathbf{x}\\Rightarrow\\min\_{f(\\mathbf{x})} \\right. \\\\ \\end{array}$$  
(5.41)

subject to the constraints

  
$$\\begin{array}{r} {\\mathcal{G}\_{i}\\lbrack f(\\mathbf{x})\\rbrack = {\\int\_{\\mathcal{X}}\\Psi\_{i}}\\left\\lbrack {f(\\mathbf{x})} \\right\\rbrack d\\mathbf{x} = 0,\\text{\\quad\\quad}i = \\overline{1,m}.} \\\\ \\end{array}$$  
(5.42)

Here **x** ∈ *R*^(*n*), the functions *Φ*\[ • \], *Ψ*[1]\[ • \], …, *Ψ*[*m*]\[ • \] and also the desired function *f*( • ) that minimizes the functional 𝒥\[ • \] belong to the class *ℂ*¹ of all continuously differentiable functions.

Define the Lagrange functional by

  
$$\\begin{array}{r} {\\mathcal{L}\\lbrack f(\\mathbf{x})\\rbrack = {\\int\_{\\mathcal{X}}\\mathcal{J}}\\lbrack f(\\mathbf{x})\\rbrack - {\\sum\\limits\_{i = 1}^{m}\\lambda\_{i}}{\\int\_{\\mathcal{X}}\\Psi\_{i}}\\left\\lbrack {f(\\mathbf{x})} \\right\\rbrack d\\mathbf{x}.} \\\\ \\end{array}$$  
(5.43)

The first-order optimality condition claims that the variation of this functional with respect to the function *f*(**x**) is zero, i.e.,

  
$$\\begin{array}{r} {\\delta\\mathcal{L} = 0.} \\\\ \\end{array}$$  
(5.44)

Because the function under variation belongs to the class ℂ¹, condition (5.44) is equivalent to the zero value of the Gateaux derivative of the functional ℒ.

Recall the definition of the Gateaux derivative. Consider a functional ℰ\[*w*(**u**)\], where *w*(**u**) ∈ ℂ¹ is a scalar function, **u** ∈ *R*^(*n*). Take an arbitrary function *h*(**u**) ∈ ℂ¹, and introduce a linear combination *w*^(\*)(**u**) + *α**h*(**u**), where *α* denotes a real variable and *w*^(\*)(**u**) is a certain fixed function from *ℂ*¹ that possesses some necessary properties (e.g., minimizes the functional ℰ). For a chosen function *h*(**u**), the functional ℰ becomes a function of the real variable *α*. The Gateaux derivative of the functional ℰ is given by

  
$$\\begin{array}{r} \\left. D\\mathcal{E} = \\frac{d}{d\\alpha}\\mathcal{E}\\lbrack w^{\*}(\\mathbf{u}) + \\alpha h(\\mathbf{u})\\rbrack \\middle| {}\_{\\alpha = 0}. \\right. \\\\ \\end{array}$$  
(5.45)

Getting back to the Lagrange functional (5.43), consider an arbitrary function *h*(**x**) from the class *ℂ*¹ and the real variable *α*. Denote by *f*^(\*)(**x**) the function that yields minimum in the problem (5.41, 5.42). Represent an arbitrary function *f*(**x**) as the linear combination

  
$$\\begin{array}{r} {f(\\mathbf{x}) = f^{\*}(\\mathbf{x}) + \\alpha h(\\mathbf{x}).} \\\\ \\end{array}$$  
(5.46)

Under fixed *f*^(\*)(**x**) and *h*(**x**), the Lagrange functional (5.43) turns out to be a function of the real variable *α*, i.e.,

  
$$\\begin{array}{r} {\\mathcal{L} = {\\int\_{X}\\Phi}\\left\\lbrack {f^{\*}(\\mathbf{x}) + \\alpha h(\\mathbf{x})} \\right\\rbrack d\\mathbf{x} - {\\sum\\limits\_{i = 1}^{m}\\lambda\_{i}}{\\int\_{X}\\Psi\_{i}}\\left\\lbrack {f^{\*}(\\mathbf{x}) + \\alpha h(\\mathbf{x})} \\right\\rbrack d\\mathbf{x}.} \\\\ \\end{array}$$  
(5.47)

Then the first-order optimality condition for the Lagrange functional takes the form

  
$$\\begin{array}{r} {D\\mathcal{L} = {\\int\_{X}h}(\\mathbf{x})\\left( {\\frac{d\\Phi(y)}{dy} - {\\sum\\limits\_{i = 1}^{m}\\lambda\_{i}}\\,\\frac{d\\Psi\_{i}(y)}{dy}} \\right)d\\mathbf{x} = 0,} \\\\ \\end{array}$$  
(5.48)

where *y* is a scalar argument of the functions Φ and *Ψ*[1], …, *Ψ*[*m*]. For this integral expression to vanish, a necessary condition is that its integrand takes zero value for any function *h*(**x**) ∈ ℂ¹.

Consequently, *the first-order optimality condition in the problem (5.41, 5.42)* can be written as

  
$$\\begin{array}{r} {\\frac{d\\Phi(y)}{dy} = {\\sum\\limits\_{i = 1}^{m}\\lambda\_{i}}\\frac{d\\Psi\_{i}(y)}{dy}.} \\\\ \\end{array}$$  
(5.49)

Here the derivatives of the functions *Φ*, *Ψ*[1], …, *Ψ*[*m*] depend on *f*^(\*)(**x**), the function that minimizes the functional (5.41), i.e.,

  
$$\\begin{array}{r} {d\\Phi(y)dy = \\phi\\lbrack f^{\*}(\\mathbf{x})\\rbrack,\\text{\\quad\\quad}d\\Psi\_{i}(y)dy = \\psi\_{i}\\lbrack f^{\*}(\\mathbf{x})\\rbrack,\\quad i = \\overline{1,m}.} \\\\ \\end{array}$$  
(5.50)

Hence, equality (5.49) can be transformed into

  
$$\\begin{array}{r} {\\phi\\lbrack f^{\*}(\\mathbf{x})\\rbrack = {\\sum\\limits\_{i = 1}^{m}\\lambda\_{i}}\\psi\_{i}\\lbrack f^{\*}(\\mathbf{x})\\rbrack.} \\\\ \\end{array}$$  
(5.51)

This equality defines a parameterization of the optimal function *f*^(\*)(**x**) by the Lagrange multipliers *λ*[1], …, *λ*[*m*]. In some cases, the parameterization can be expressed in an analytical form. Particularly, let the function Φ in (5.41, 5.42) be quadratic, i.e.,

  
$$\\begin{array}{r} {\\Phi\\lbrack f(\\mathbf{x})\\rbrack = a\_{0} + a\_{1}f(\\mathbf{x}) + a\_{2}f^{2}(\\mathbf{x}),} \\\\ \\end{array}$$  
(5.52)

and also let the functions *Ψ*[1], …, *Ψ*[*m*] be linear, i.e.,

  
$$\\begin{array}{r} {\\Psi\_{i}\\lbrack f(\\mathbf{x})\\rbrack = b\_{0}^{i} + b\_{1}^{i}f(\\mathbf{x}),\\text{\\quad\\quad}i = \\overline{1,m},} \\\\ \\end{array}$$  
(5.53)

which leads to the functional quadratic programming problem. Then

  
$$\\begin{array}{r} {\\phi\\lbrack f^{\*}(\\mathbf{x})\\rbrack = a\_{1} + a\_{2}f^{\*}(\\mathbf{x}),\\text{\\quad\\quad}\\psi\_{i}\\lbrack f^{\*}(\\mathbf{x})\\rbrack = b\_{1}^{i},} \\\\ \\end{array}$$  
(5.54)

and the optimality conditions (5.51) yield the following parametric representation for the optimal function *f*^(\*):

  
$$\\begin{array}{r} {f^{\*}(\\mathbf{x}) = {\\sum\\limits\_{i = 1}^{m}\\lambda\_{i}}b\_{1}^{i}.} \\\\ \\end{array}$$  
(5.55)

The role of parameters is played by the Lagrange multipliers *λ*[1], …, *λ*[*m*].

## 5.4Optimality Conditions and Structure of Entropy-Optimal Probability Density Functions

The entropy-robust estimation problems (5.2.1–5.22) and (5.27–5.29) are constrained maximization problems of an integral functional in functions from the class *ℂ*¹ on an admissible set defined by integral equalities. To establish optimality conditions and perform a structural analysis of the resulting solution (optimal PDFs), we will take advantage of Lagrange's method of multipliers and the Gateaux derivatives.

### 5.4.1Randomized models of the RPM-Orig class with output errors

Consider the problem (5.2.1–5.22). Define the Lagrange functional in the form

  
$$\\begin{aligned} {\\mathcal{L}\\lbrack P(\\mathbf{a}),Q(\\overline{\\xi})\\rbrack} & {= \\mathcal{H}\\lbrack P(\\mathbf{a}),Q(\\overline{\\xi})\\rbrack + \\lambda p\\lbrack P(\\mathbf{a})\\rbrack + \\left\\langle \\overline{\\mu},\\mathbf{q}\\lbrack Q(\\overline{\\xi}\\rbrack \\right\\rangle +} \\\\ & {+ \\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{l}^{(j)}\\lbrack P(\\mathbf{a}),Q(\\overline{\\xi})\\rbrack \\right\\rangle,} \\\\ \\end{aligned}$$  
(5.56)

where *λ*, *μ*[1], …, *μ*[*s*], and *θ*[1], …, *θ*[*s*] denote the Lagrange multipliers for the corresponding constraints, i.e.,

  
$$\\begin{array}{r} {p\\lbrack P(\\mathbf{a})\\rbrack = 1 - {\\int\_{\\mathcal{A}}P}(\\mathbf{a})d\\mathbf{a} = 0,} \\\\ \\end{array}$$  
(5.57)

![](images/math5_212.jpg)

  
$$\\begin{aligned} {\\mathbf{l}^{(j)}\\lbrack P(\\mathbf{a}),Q(\\overline{\\xi})\\rbrack =} & {\\mathbf{y}^{(j)} - \\left\\lbrack {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\hat{\\mathbf{y}}(t\_{j},\\mathbf{a})\\, d\\mathbf{a}} \\right\\rbrack +} \\\\ {+ {\\int\_{\\Xi\_{j}}\\,}Q\_{j}} & {({\\overline{\\xi}}^{(j)})\\,{\\overline{\\xi}}^{(j)}\\, d{\\overline{\\xi}}^{(j)} = 0,} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.59)

To obtain optimality conditions for the Lagrange functional, use the Gateaux derivative-based method described in [Section 4.3](#chapter4.xhtml#sec4_3).

Let the PDFs *P*^(\*)(**a**) and $Q\_{1}^{\*}({\\overline{\\xi}}^{(1)}),\\ldots,Q\_{s}^{\*}({\\overline{\\xi}}^{(s)})$ satisfy the first-order optimality conditions for the functional (5.56). Consider arbitrary functions *h*(**a**) and $g\_{1}({\\overline{\\xi}}^{(1)}),\\ldots,g\_{s}({\\overline{\\xi}}^{(s)}),$ all from the class ℂ¹, as well as real variables *α* and *β*[1], …, *β*[*s*]. Write the PDFs in (5.56) in the form

  
$$\\begin{aligned} {P(\\mathbf{a}) = P^{\*}(\\mathbf{a}) + \\alpha h(\\mathbf{a});} & {Q\_{j}({\\overline{\\xi}}^{(j)}) = Q\_{j}^{\*}({\\overline{\\xi}}^{(j)}) + \\beta\_{j}g\_{j}({\\overline{\\xi}}^{(j)}),} \\\\ & {\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.60)

Then the Lagrange functional becomes a function of the real variables 𝕎 = {*α*;*β*[1],…,*β*[*s*]}. The Gateaux derivatives in these variables are given by

  
$$\\begin{aligned} \\left. \\frac{\\partial\\mathcal{L}}{\\partial\\alpha} \\middle| {}\_{\\mathbb{W} = 0} = \\right. & {- {\\int\_{\\mathcal{A}}h}(\\mathbf{a})(\\ln\\frac{P^{\*}(\\mathbf{a})}{P\_{0}(\\mathbf{a})} + 1 + \\lambda +} \\\\ {+ {\\sum\\limits\_{j = 1}^{s}\\langle}{\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}} & {\\left. \\lbrack\\mathbf{x}(t\_{j},\\tau\_{h},\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle)d\\mathbf{a},} \\\\ \\left. \\frac{\\partial\\mathcal{L}}{\\partial\\beta\_{j}} \\middle| {}\_{\\mathbb{W} = 0} = - {\\int\_{\\Xi\_{j}}g\_{j}}({\\overline{\\xi}}^{(j)}) \\right. & {\\left\\lbrack {\\ln\\frac{Q\_{j}^{\*}({\\overline{\\xi}}^{(j)})}{Q\_{j}^{0}({\\overline{\\xi}}^{(j)})} + 1 + \\mu\_{j} + \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\xi}}^{(j)},} \\\\ & {\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.61)

For these integrals to vanish for any functions $h(\\mathbf{a}),g\_{1}({\\overline{\\xi}}^{(j)}),\\ldots,g\_{s}({\\overline{\\xi}}^{(j)}) \\in {\\mathbb{C}}^{1},$ a necessary condition is that the bracketed expressions all take zero value, i.e.,

  
$$\\begin{aligned} & {\\left. \\ln\\frac{P^{\*}(\\mathbf{a})}{P\_{0}(\\mathbf{a})} + 1 + \\lambda + {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}( \\right.}\\tau\_{h},\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle = 0,} \\\\ & {\\ln\\frac{Q\_{j}^{\*}({\\overline{\\xi}}^{(j)})}{Q\_{j}^{0}({\\overline{\\xi}}^{(j)})} + 1 + \\mu\_{j} + \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle = 0,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.62)

The solution of these equations within the Lagrange multipliers *λ*, *μ*[1], …, *μ*[*s*], and ${\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}$ has the form

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\,\\,\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}P^{\*}(\\mathbf{a}) = P\_{0}(\\mathbf{a}) \\times} \\\\ & {\\times \\exp\\left\\lbrack \\left. - 1 - \\lambda - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}Q\_{j}^{\*}({\\overline{\\xi}}^{(j)}) = Q\_{j}^{0}({\\overline{\\xi}}^{(j)})\\exp\\left\\lbrack {- 1 - \\mu\_{j} - \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.63)

The Lagrange multipliers *λ* and *μ*[1], …, *μ*[*s*] can be eliminated using the normalization conditions (5.21). Then formulas (5.4.1) yield the following entropy-optimal estimates for the PDFs of the RPM-Orig model parameters and measurement noises:

  
$$\\begin{aligned} & {P^{\*}(\\mathbf{a}) = P\_{0}(\\mathbf{a})\\frac{\\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack}{\\mathcal{P}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)})},} \\\\ & {Q\_{j}^{\*}({\\overline{\\xi}}^{(j)}) = Q\_{j}^{0}({\\overline{\\xi}}^{(j)})\\frac{\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack}{\\mathcal{Q}\_{j}({\\overline{\\theta}}^{(j)}),}\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.64)

Here

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathcal{P}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}) = {\\int\_{\\mathcal{A}}P\_{0}}(\\mathbf{a}) \\times} \\\\ & {\\times \\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack d\\mathbf{a},} \\\\ & {\\quad\\text{\\quad\\quad}\\mathcal{Q}\_{j}({\\overline{\\theta}}^{(j)}) = {\\int\_{\\Xi}Q\_{j}^{0}}({\\overline{\\xi}}^{(j)})\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\xi}}^{(j)},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.65)

Clearly, the entropy-optimal PDFs are parameterized by the Lagrange multipliers and represent exponential functions. However, they may have any form, depending on the parameters **a**. [Figure 5.2](#chapter5.xhtml#f5_2), [Figure 5.3](#chapter5.xhtml#f5_3), [Figure 5.4](#chapter5.xhtml#f5_4), [Figure 5.5](#chapter5.xhtml#f5_5) demonstrate some examples of the estimated PDFs of the model parameters. For the linear RPM-Orig model, the estimated PDFs are always exponential functions; see [Fig. 5.2](#chapter5.xhtml#f5_2). Note that their form is affected by the input and output measurements.

![Figure 5.2: p(a\_{1},a\_{2}) = \\exp( - 0.3a\_{1} + 2.5a\_{2}).](images/fig5_2.jpg)

[Figure 5.2:](#chapter5.xhtml#f5_2b) *p*(*a*[1], *a*[2]) = exp ( − 0.3*a*[1] + 2.5*a*[2]).

![Figure 5.3: p(a\_{1},a\_{2}) = exp(4a\_{1} - a\_{1}^{2} + a\_{2}).](images/fig5_3.jpg)

[Figure 5.3:](#chapter5.xhtml#f5_3b) *p*(*a*[1], *a*[2]) = *e**x**p*(4*a*[1] − *a*[1]² + *a*[2]).

![Figure 5.4: p(a\_{1},a\_{2}) = exp(4a\_{1} - a\_{1}^{2} + 6a\_{2} - a\_{2}^{2}).](images/fig5_4.jpg)

[Figure 5.4:](#chapter5.xhtml#f5_4b) *p*(*a*[1], *a*[2]) = *e**x**p*(4*a*[1] − *a*[1]² + 6*a*[2] − *a*[2]²).

![Figure 5.5: p(a\_{1},a\_{2}) = exp(0.5a\_{1} + 3.5a\_{2} + 2a\_{1}^{2} - a\_{1}^{3} - 0.2a\_{2}^{2} - 0.2a\_{2}^{3}).](images/fig5_5.jpg)

[Figure 5.5:](#chapter5.xhtml#f5_5b) *p*(*a*[1], *a*[2]) = *e**x**p*(0.5*a*[1] + 3.5*a*[2] + 2*a*[1]² − *a*[1]³ − 0.2*a*[2]² − 0.2*a*[2]³).

For the nonlinear RPMs, the estimates have a wider variety of structural forms. For example, the estimated PDFs for the RPM-Orig models with the quadratic, quadratic-linear and cubic nonlinearities are shown in [Fig. 5.3](#chapter5.xhtml#f5_3), [Fig. 5.4](#chapter5.xhtml#f5_4), [Figure 5.5](#chapter5.xhtml#f5_5).

### 5.4.2Randomized models of the RPM-Rel class with output errors

To construct optimality conditions for this class of the randomized models, introduce similar notations as (5.57–5.4.1), i.e.,

*   the Lagrange multiplier *λ* for the first constraint in (5.21), writing it in the form
    
      
    $$\\begin{array}{r} {w\\lbrack W(\\mathbf{u})\\rbrack = 1 - {\\int\_{\\mathcal{U}}W}(\\mathbf{u})d\\mathbf{u};} \\\\ \\end{array}$$  
    (5.66)
    
*   the vector $\\overline{\\mu} = \\left\\{ \\mu\_{1},\\ldots,\\mu\_{s} \\right\\}$ composed of the Lagrange multipliers for the second group of constraints in (5.21), writing them in the form
    
      
    $$\\begin{aligned} & {\\mathbf{g}\\lbrack G(\\overline{\\eta})\\rbrack = \\left\\{ g^{(1)}\\lbrack G\_{1}({\\overline{\\eta}}^{(1)})\\rbrack,\\ldots,g^{(s)}\\lbrack G\_{s}({\\overline{\\eta}}^{(s)})\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}g^{(j)}\\lbrack G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack = 1 - {\\int\_{\\mathcal{E}}G\_{j}}({\\overline{\\eta}}^{(j)})\\, d{\\overline{\\eta}}^{(j)},} \\\\ & {\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s};} \\\\ \\end{aligned}$$  
    (5.67)
    
*   the vectors ${\\overline{\\theta}}^{(j)} = \\left\\{ \\theta\_{1}^{(j)},\\ldots,\\theta\_{m}^{(j)} \\right\\},\\, j = \\overline{1,s},$ composed of the Lagrange multipliers for the constraints (5.22), writing them in the form
    
      
    $$\\begin{aligned} & {\\text{\\quad\\quad}\\mathbf{h}^{(j)}\\lbrack W(\\mathbf{u}),G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack = \\mathbf{y}(t\_{j}) -} \\\\ & \\left. - {\\int\_{\\mathcal{U}}W}(\\mathbf{u})\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}),\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}^{-} + A\\,\\mathbf{u}\\rbrack\\, d\\mathbf{u} - \\right. \\\\ & {+ {\\int\_{\\mathcal{E}\_{j}}\\,}G\_{j}({\\overline{\\eta}}^{(j)})\\,{\\overline{\\eta}}^{(j)}\\, d{\\overline{\\eta}}^{(j)},\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
    (5.68)
    

Using these notations, define the Lagrange functional

  
$$\\begin{aligned} {\\mathcal{L}\\lbrack W(\\mathbf{u}),G(\\overline{\\eta})\\rbrack} & {= \\mathcal{H}\\lbrack W(\\mathbf{u}),G(\\overline{\\eta})\\rbrack + \\lambda w\\lbrack W(\\mathbf{u})\\rbrack + \\left\\langle \\overline{\\mu},\\mathbf{g}\\lbrack G(\\overline{\\eta})\\rbrack \\right\\rangle +} \\\\ & {\\left. + {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{h}^{(j)}\\lbrack W(\\mathbf{u}),G\_{j}( \\right.}{\\overline{\\eta}}^{(j)})\\rbrack \\right\\rangle.} \\\\ \\end{aligned}$$  
(5.69)

To get optimality conditions for the Lagrange functional, we will again employ the Gateaux derivative-based method; see (5.60, 5.4.1). The corresponding first-order optimality conditions have the form

  
$$\\begin{aligned} {\\ln\\frac{W^{\*}(\\mathbf{u})}{W\_{0}(\\mathbf{u})}} & {+ 1 + \\lambda +} \\\\ \\left. + {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{j},\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},\\, \\middle| \\, h = \\right. & {\\left. \\overline{1,(j-1)}),\\mathbf{a}^{-} + A\\,\\mathbf{u}\\rbrack \\right\\rangle = 0,} \\\\ {\\ln\\frac{G\_{j}^{\*}({\\overline{\\eta}}^{(j)})}{G\_{j}^{0}({\\overline{\\eta}}^{(j)})} + 1 + \\mu\_{j}} & {+ \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\eta}}^{(j)} \\right\\rangle = 0,} \\\\ {j =} & {\\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.70)

The solution of these equations within the Lagrange multipliers *λ*, *μ*[1], …, *μ*[*s*], and ${\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}$ is given by

  
$$\\begin{aligned} {W^{\*}(\\mathbf{u}) = W\_{0}} & {(\\mathbf{u})\\exp\\lbrack - 1 - \\lambda -} \\\\ {{\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{j},\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},} & {\\,\\left| \\, r = \\overline{1,(j-1)}),\\mathbf{a}^{-} + A\\,\\mathbf{u}\\rbrack \\right\\rangle\\rbrack,} \\\\ {G\_{j}^{\*}({\\overline{\\eta}}^{(j)}) = G\_{j}^{0}({\\overline{\\eta}}^{(j)})} & {\\exp\\left\\lbrack {- 1 - \\mu\_{j} - \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\eta}}^{(j)} \\right\\rangle} \\right\\rbrack,} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.71)

The Lagrange multipliers *λ* and *μ*[1], …, *μ*[*s*] can be eliminated using the normalization conditions (5.28). Then formulas (5.4.2) yield the following entropy-optimal estimates for the PDFs of the RPM-Rel model parameters and measurement noises:

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}W^{\*}(\\mathbf{u}) = W\_{0}(\\mathbf{u}) \\times} \\\\ & {\\times \\frac{\\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{j},\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{r}) \\right.},\\, \\middle| \\, r = \\overline{1,(j-1)}),\\mathbf{a}^{-} + \\Delta\\,\\mathbf{u}\\rbrack \\right\\rangle \\right\\rbrack}{\\mathcal{W}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)})},} \\\\ & {\\text{\\quad\\quad}\\quad\\quad G\_{j}^{\*}({\\overline{\\eta}}^{(j)}) = G\_{j}^{0}({\\overline{\\eta}}^{(j)})\\frac{\\exp\\left\\lbrack {- {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\eta}}^{(j)} \\right\\rangle}} \\right\\rbrack}{\\mathcal{G}\_{j}({\\overline{\\theta}}^{(j)})},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s},} \\\\ \\end{aligned}$$  
(5.72)

where

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathcal{W}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}) = {\\int\_{\\mathcal{U}}W\_{0}}(\\mathbf{u}) \\times} \\\\ & {\\times \\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{r}) \\right.},\\, \\middle| \\, r = \\overline{1,(j-1)}),\\mathbf{a}^{-} + \\Delta\\,\\mathbf{u}\\rbrack \\right\\rangle \\right\\rbrack d\\mathbf{u},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\mathcal{G}\_{j}({\\overline{\\theta}}^{(j)}) = {\\int\_{\\mathcal{E}}G\_{j}^{0}}({\\overline{\\eta}}^{(j)})\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\eta}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\eta}}^{(j)},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.73)

Like for the randomized models of the RPM-Orig class (see (5.4.1)), the entropy-optimal PDFs are parameterized by the Lagrange multipliers and represent exponential functions.

### 5.4.3Randomized models of the RPM-Orig class with input and output errors

Consider the problem (5.2.3, 5.36, 5.2.3) and write out the Lagrange functional:

  
$$\\begin{aligned} {\\mathcal{L}\\lbrack F(\\mathbf{a},\\mu),\\overline{Q}(\\overline{\\xi})\\rbrack} & {= \\mathcal{H}\\lbrack F(\\mathbf{a},\\mu),\\overline{Q}(\\overline{\\xi})\\rbrack + \\lambda w\\lbrack F(\\mathbf{a},\\mu)\\rbrack + \\left\\langle \\overline{\\eta},\\mathbf{q}\\lbrack\\overline{Q}(\\overline{\\xi}\\rbrack \\right\\rangle +} \\\\ & {+ \\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{c}^{(j)}\\lbrack F(\\mathbf{a},\\mu),\\overline{Q}(\\overline{\\xi})\\rbrack \\right\\rangle,} \\\\ \\end{aligned}$$  
(5.74)

where $\\lambda;\\overline{\\eta};\\overline{\\theta}$ —Lagrange multipliers for corresponding constraints:

  
$$\\begin{array}{r} {w\\lbrack P(\\mathbf{a})\\rbrack = 1 - {\\int\_{\\mathcal{R}}F}(\\mathbf{a},\\mu)d\\mathbf{a}d\\mu = 0,} \\\\ \\end{array}$$  
(5.75)

![](images/math5_252.jpg)

  
$$\\begin{aligned} & {\\mathbf{c}^{(j)}\\lbrack F(\\mathbf{a},\\mu),\\overline{Q}(\\overline{\\xi})\\rbrack = \\mathbf{y}^{(j)} - \\left\\lbrack {{\\int\_{\\mathcal{R}}F}(\\mathbf{a},\\mu)\\hat{\\mathbf{y}}(t\_{j},\\mathbf{a},\\mu)\\, d\\mathbf{a}\\, d\\mu} \\right\\rbrack +} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad} + {\\int\_{\\Xi\_{j}}\\,}Q\_{j}({\\overline{\\xi}}^{(j)})\\,{\\overline{\\xi}}^{(j)}\\, d{\\overline{\\xi}}^{(j)} = 0,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.77)

To get optimality conditions for the Lagrange functional, we will again employ the Gâteaux derivative-based method. The corresponding first-order optimality conditions have the form

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}F^{\*}(\\mathbf{a},\\mu) = F\_{0}(\\mathbf{a},\\mu) \\times} \\\\ & {\\times \\frac{\\left. \\exp\\lbrack - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.} + \\mu(t\_{j},\\tau\_{h}),\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle\\rbrack}{\\mathcal{F}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)})},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}Q\_{j}^{\*}({\\overline{\\xi}}^{(j)}) = Q\_{j}^{0}({\\overline{\\xi}}^{(j)})\\frac{\\exp\\lbrack - \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle\\rbrack}{\\mathcal{Q}\_{j}({\\overline{\\theta}}^{(j)})},\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.78)

where

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathcal{F}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}) = {\\int\_{\\mathcal{R}}F\_{0}}(\\mathbf{a},\\mu) \\times} \\\\ & {\\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.} + \\mu(t\_{j},\\tau\_{h}),\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack d\\mathbf{a},} \\\\ & {\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathcal{Q}\_{j}({\\overline{\\theta}}^{(j)}) = {\\int\_{\\Xi}Q\_{j}^{0}}({\\overline{\\xi}}^{(j)})\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\xi}}^{(j)},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(5.79)

The obtained PDF functions are parameterized by the Lagrange multipliers $\\overline{\\theta},$ which are determined from the balance equations.

## 5.5Equations for Lagrange Multipliers

All entropy-optimal PDFs belong to the class of exponential functions parameterized by the Lagrange multipliers ${\\overline{\\theta}}^{1},\\ldots,{\\overline{\\theta}}^{s};$ see the formulas derived in the previous section. For calculating the Lagrange multipliers, we have to solve the equations that are obtained from the balance constraints (5.24, 5.31) with the entropy-optimal PDFs (5.64, 5.4.2).

**1. RPM-Orig model with output errors**

To form the corresponding equations, introduce the following auxiliary notations.

*   the mean output of the model with the entropy-optimal randomized parameters
    
      
    $$\\begin{aligned} & {\\text{\\quad\\quad}\\mathbb{Y}\_{j}(\\overline{\\theta}) = \\mathcal{P}^{( - 1)}(\\overline{\\theta}){\\int\_{\\mathcal{A}}P\_{0}}(\\mathbf{a}) \\times} \\\\ {\\times \\exp} & {\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathcal{B}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.}\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack \\times} \\\\ & \\left. \\quad \\times \\mathcal{B}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h})\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack d\\mathbf{a}; \\right. \\\\ \\end{aligned}$$  
    (5.80)
    
*   the mean entropy-“worst” measurement noises
    
      
    $$\\begin{aligned} {{\\mathbb{Q}}\_{j}({\\overline{\\theta}}^{(j)}) = \\mathcal{Q}\_{j}^{( - 1)}({\\overline{\\theta}}^{(j)})\\int\_{\\Xi\_{j}}} & {Q\_{j}^{0}({\\overline{\\xi}}^{(j)})\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\xi}}^{(j)},} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
    (5.81)
    

In these expressions, $\\overline{\\theta} = \\lbrack{\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}\\rbrack.$

Using the balance constraints (5.24), write the equations of the Lagrange multipliers in the form

  
$$\\begin{array}{r} {\\mathbb{Y}\_{j}(\\overline{\\theta}) + {\\mathbb{Q}}\_{j}({\\overline{\\theta}}^{(j)}) = \\mathbf{y}^{(j)},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(5.82)

**2. RPM-Rel model with output errors**

By analogy with the previous case, introduce the following auxiliary notations:

*   the mean output of the model with the entropy-optimal randomized parameters
    
      
    $$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad{\\mathbb{Z}}\_{j}(\\overline{\\theta}) = \\mathcal{W}^{( - 1)}(\\overline{\\theta}){\\int\_{\\mathcal{U}}W\_{0}}(\\mathbf{u}) \\times} \\\\ & \\left. \\times \\exp\\lbrack - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathcal{D}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.}\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}^{-} + \\right. \\\\ & {\\left. \\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad} A\\,\\mathbf{u}\\rbrack \\right\\rangle\\rbrack \\times} \\\\ & \\left. \\times \\mathcal{D}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h})\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}^{-} + A\\,\\mathbf{u}\\rbrack d\\mathbf{u}; \\right. \\\\ \\end{aligned}$$  
    (5.83)
    
*   the mean entropy-“worst” measurement noises
    
      
    $$\\begin{aligned} {\\mathbb{G}\_{j}({\\overline{\\theta}}^{(j)}) = \\mathcal{G}\_{j}^{( - 1)}({\\overline{\\theta}}^{(j)})\\int\_{\\mathcal{E}}} & {G\_{j}^{0}({\\overline{\\eta}}^{(j)})\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\eta}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\eta}}^{(j)},} \\\\ & {\\, j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
    (5.84)
    

Using the balance constraints (5.31), write the equations of the Lagrange multipliers in the form

  
$$\\begin{array}{r} {{\\mathbb{Z}}\_{j}(\\overline{\\theta}) + \\mathbb{G}\_{j}({\\overline{\\theta}}^{(j)}) = \\mathbf{y}^{(j)},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(5.85)

**3. RPM-Orig model with input and output errors**

To form the corresponding equations, introduce the following auxiliary notations.

*   the mean output of the model with the entropy-optimal randomized parameters
    
      
    $$\\begin{aligned} & {\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathbb{Y}\_{j}(\\overline{\\theta}) = \\mathcal{F}^{( - 1)}(\\overline{\\theta}){\\int\_{\\mathcal{R}}F\_{0}}(\\mathbf{a},\\mu) \\times} \\\\ & {\\times \\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathcal{B}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.} + \\mu(t\_{j},\\tau\_{h})\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack \\times} \\\\ & \\left. \\text{\\quad\\quad} \\times \\mathcal{B}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) + \\mu(t\_{j},\\tau\_{h})\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack d\\mathbf{a}d\\mu. \\right. \\\\ \\end{aligned}$$  
    (5.86)
    
*   the mean entropy-“worst” measurement noises
    
      
    $$\\begin{aligned} {{\\mathbb{Q}}\_{j}({\\overline{\\theta}}^{(j)}) = \\mathcal{Q}\_{j}^{( - 1)}({\\overline{\\theta}}^{(j)})\\int\_{\\Xi\_{j}}} & {Q\_{j}^{0}({\\overline{\\xi}}^{(j)})\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\xi}}^{(j)},} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
    (5.87)
    

Then, write the equations of the Lagrange multipliers in the form

  
$$\\begin{array}{r} {\\mathbb{Y}\_{j}(\\overline{\\theta}) + {\\mathbb{Q}}\_{j}({\\overline{\\theta}}^{(j)}) = \\mathbf{y}^{(j)},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(5.88)

As a matter of fact, equations (5.82, 5.85, 5.88) possess some specifics. They incorporate functions that depend on the Lagrange multipliers; in turn, the latter are calculated by integration over the multidimensional domains of definition of the parameters and measurement noises. To be fair, these domains have a simple structure, representing multidimensional parallelepipeds. In the sequel, they will be called *the parameterized integral components (PICs)* in order to underline their specifics. PICs calculation and solution of the balance equations are separate and nontrivial problems. Some approaches to solve these problems will be considered in detail in [Chapter 6](#chapter6.xhtml).

# CHAPTER 6 ENTROPY-ROBUST ESTIMATION METHODS FOR PROBABILITIES OF BELONGING IN MACHINE LEARNING PROCEDURES

DOI: [10.1201/9781003306566-6](https://doi.org/10.1201/9781003306566-6)

The constrained maximization of entropy functionals represents an efficient tool for solving various problems, including the estimation of the probabilities of belonging to certain intervals for the model parameters and measurement noises. The original model parameters and measurement noises of the interval type are transformed into auxiliary nonnegative variables lying within the unit interval, which are treated as the probabilities of belonging \[[67](#refbib.xhtml#r67)\]. Such a probabilistic interpretation of the auxiliary parameters and measurement noises justifies the applicability of entropy functionals to find best values of the auxiliary and original variables. The estimation algorithms for the probabilities of belonging are machine learning algorithms. The estimation problem is formulated as an entropy-linear programming problem with an admissible set that is constructed using available learning data arrays.

## 6.1Entropy-Robust Estimation Algorithms for Probabilities of Belonging

An important class of the parameterized models used in ML procedures consists of the models with the interval-type *quasi randomized* parameters; their values are defined by the probabilities of belonging to corresponding intervals. Denote this class of models by *RPM-QuaRand* and their parameters by **c**. These models have deterministic parameters with unknown values. Hence, the RPM-QuaRand models can be considered as randomized models with the PDFs *R*(**c**) = *R**δ*(**c**^(\*) − **c**).

The parameters **c** are of the interval type, i.e.,

  
$$\\begin{array}{r} {\\mathbf{c} \\in \\mathcal{C} = \\otimes\_{i = 1}^{n}\\mathcal{C}\_{i} = \\lbrack c\_{i}^{-},c\_{i}^{+}\\rbrack.} \\\\ \\end{array}$$  
(6.1)

Introduce the probability *p*[*i*] that the parameter *c*[*i*] takes some value within the interval 𝒞[*i*]. The values *p*[*i*] will be called *the probabilities of belonging (PO)*. Then a parameter *c*[*i*] can be written as

  
$$\\begin{array}{r} \\left. c\_{i} = c\_{i}^{-} + (c\_{i}^{+} - c\_{i}^{-})\\, p\_{i},\\text{\\quad\\quad}\\mathbf{c} = \\mathbf{c}^{-} + C\\,\\mathbf{p},\\quad C = \\text{diag}\\lbrack(c\_{i}^{+} - c\_{i}^{-})\\, \\middle| \\, i = \\overline{1,n}\\rbrack. \\right. \\\\ \\end{array}$$  
(6.2)

The probabilities of belonging are

  
$$\\begin{array}{r} {\\mathbf{p} \\in \\mathcal{I} = \\lbrack\\mathbf{0} \\leq \\mathbf{p} \\leq \\mathbf{1}\\rbrack.} \\\\ \\end{array}$$  
(6.3)

Some statements also involve an additional constraint known as the complete set condition (the normalization condition), i.e.,

  
$$\\begin{array}{r} {{\\sum\\limits\_{i = 1}^{n}p\_{i}} = 1.} \\\\ \\end{array}$$  
(6.4)

The definition of the probabilities of belonging and their properties (6.3, 6.4) formally match the definition of the relative parameters (4.96, 4.97). However, there exist some differences of principle between them. The relative parameters **u** are the randomized variables characterized by a given PDF. In contrast, the probabilities of belonging **p** are nonrandom variables taking values within the unit nonnegative cube.

A dynamic model of the RPM-QuaRand class generates a unique trajectory, that is, described by the following equality at discrete times $j = \\overline{0,s} = \\mathcal{T}\_{s}$:

  
$$\\begin{aligned} {\\mathbf{s}\\lbrack j,\\mathbf{p}\\rbrack} & {= \\mathcal{S}\\lbrack\\mathbf{x}(j,\\tau),\\,\\mathbf{c}^{-} + C\\,\\mathbf{p};(j,\\tau) \\in \\mathcal{T}\_{s}\\rbrack,} \\\\ \\mathbf{c} & {= \\mathbf{c}^{-} + C\\,\\mathbf{p}.} \\\\ \\end{aligned}$$  
(6.5)

Here 𝒮 means an integral functional.

This problem has an additive model of measurements: in each *j*th measurement, the noises are characterized by an interval-type vector

  
$$\\begin{array}{r} {{\\overline{\\zeta}}^{(j)} \\in \\mathcal{Z}^{(j)} = \\otimes\_{i = 1}^{m}\\mathcal{Z}\_{i}^{(j)},\\text{\\quad\\quad}\\mathcal{Z}\_{i}^{(j)} = \\lbrack\\zeta\_{-}^{(j)}(i),\\zeta\_{+}^{(j)}(i)\\rbrack,\\quad j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.6)

Introduce the probability of belonging *q*[*i*]^((*j*)) that the element *ζ*[*i*]^((*j*)) of the noise vector takes some value from the interval 𝒵[*i*]^((*j*)). The probabilities *q*[*i*]^((*j*)) lie within the unit nonnegative interval and the probability vector is

  
$$\\begin{array}{r} {\\mathbf{q}^{(j)} \\in \\mathcal{I} = \\lbrack\\mathbf{0} \\leq \\mathbf{q}^{(j)} \\leq \\mathbf{1}\\rbrack,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.7)

In some cases, like for the probabilities of belonging of the model parameters, it is necessary to consider the normalization conditions

  
$$\\begin{array}{r} {{\\sum\\limits\_{i = 1}^{m}q\_{i}^{(j)}} = 1,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.8)

The noise vector can be written as

  
$$\\begin{array}{r} \\left. {\\overline{\\zeta}}^{(j)} = {\\overline{\\zeta}}\_{-}^{(j)}(i) + L\_{j}\\mathbf{q}^{(j)},\\text{\\quad\\quad}L\_{j} = \\text{diag}\\,\\lbrack\\zeta\_{+}^{(j)}(i) - \\zeta\_{-}^{(j)}(i),\\, \\middle| \\, i = \\overline{1,m}\\rbrack. \\right. \\\\ \\end{array}$$  
(6.9)

The measurable output of the RPM-QuaRand model (6.5) is a unique trajectory **w**\[*j*, **p**, **q**\] composed of an additive mix of the vectors **s**\[*j*, **p**\] (6.5) and ${\\overline{\\zeta}}^{(j)}$ (6.9), i.e.,

  
$$\\begin{array}{r} {\\mathbf{w}\\lbrack j,(\\mathbf{p},\\mathbf{q}^{(j)}\\rbrack = \\mathbf{s}\\lbrack j,\\mathbf{p}\\rbrack + {\\overline{\\zeta}}^{(j)} - + L\_{j}\\,\\mathbf{q}^{(j)},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.10)

Therefore, as its variables the RPM-QuaRand model incorporates the probabilities of belonging $\\mathbf{p},\\mathbf{q}^{j},\\, j = \\overline{1,s}.$

### 6.1.1ML algorithm for RPM-QuaRand model with normalized probabilities of belonging

Consider the case in which the vectors **p** and **q**^((1)), …, **q**^((*s*)) are normalized and there exists information about the prior probabilities of belonging, **p**[0] and **q**[0]^((1)), …, **q**[0]^((*s*)).

Throughout the book, it has been repeatedly mentioned that the ML procedures operate under uncertainty measured in terms of entropy. Therefore, we will characterize the quality of estimation using the entropy approach. Since the measurement noises are additive, let us adopt the generalized Boltzmann information entropy \[141\]

  
$$\\begin{array}{r} {H\_{B}(\\mathbf{p},Q) = - \\left\\langle \\mathbf{p},\\mathbf{ln}\\frac{\\mathbf{p}}{\\mathbf{p}\_{0}} \\right\\rangle - {\\sum\\limits\_{j = 1}^{s}\\left\\langle \\mathbf{q}^{(j)},\\mathbf{ln}\\frac{\\mathbf{q}^{(j)}}{\\mathbf{q}\_{0}^{(j)}} \\right\\rangle},Q = \\lbrack\\mathbf{q}^{(1)},\\ldots,\\mathbf{q}^{(s)}\\rbrack.} \\\\ \\end{array}$$  
(6.11)

Here **l****n**( • ) denotes a vector with corresponding elements  • . Recall that the variables in this expression are nonnegative. Then *the entropy-robust estimation problem for the RPM-QuaRand model with the normalized probabilities of belonging* can be written as follows:

*   maximize the entropy function (6.11)
    
      
    $$\\begin{array}{r} \\left. H\_{B}(\\mathbf{p},Q)\\Rightarrow\\max\_{\\mathbf{p},Q} \\right. \\\\ \\end{array}$$  
    (6.12)
    
*   subject to
    
    *   –the normalization conditions
        
          
        $$\\begin{array}{r} {\\left\\langle \\mathbf{p},\\mathbf{1} \\right\\rangle = 1,\\text{\\quad\\quad}\\left\\langle \\mathbf{q}^{(j)},\\mathbf{1} \\right\\rangle = 1,\\quad j = \\overline{1,s},} \\\\ \\end{array}$$  
        (6.13)
        
        and
        
    *   –the balance constraints
        
          
        $$\\begin{array}{r} {\\mathcal{S}\\lbrack\\mathbf{x}\\lbrack j,\\tau\\rbrack,\\,\\mathbf{c}^{-} + C\\,\\mathbf{p};(j,\\tau) \\in \\mathcal{T}\_{s}\\rbrack + {\\overline{\\zeta}}\_{-}^{(j)} + L\_{j}\\,\\mathbf{q}^{(j)} = \\mathbf{y}\\lbrack j\\rbrack,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
        (6.14)
        

The constraints (6.13, 6.14) extract an admissible set Υ from the unit nonnegative (*m* + *r*)\-dimensional cube ℐ.

In the general case, this problem is an entropy-nonlinear programming problem. Its nonlinear properties follow from the balance constraints (6.14), which contain a nonlinear functional 𝒮 of the parameters. Note that the randomized approach to estimation leads to the optimization problems of entropy-linear functional programming.

Consequently, *the entropy-robust ML algorithm for the RPM-QuaRand model with the normalized probabilities of belonging* has the form

  
$$\\begin{array}{r} \\left. {(\\mathbf{p},Q)}^{\*} = \\arg\\max\_{(\\mathbf{p},Q)}\\lbrack H\_{B},\\, \\middle| \\,(\\mathbf{p},Q) \\in \\Upsilon\\rbrack. \\right. \\\\ \\end{array}$$  
(6.15)

### 6.1.2ML algorithm for RPM-QuaRand model with interval-type probabilities of belonging

For the models of this class, the probabilities of belonging take values within the nonnegative *r*\-dimensional cube—the normalization condition is not imposed. The estimation problems arising for these RPM-QuaRand models have two modifications depending on entropy choice, namely, the statements with the Boltzmann or Fermi entropies \[149\].

When using the generalized Boltzmann information entropy (6.11), *the Boltzmann entropy-robust estimation problem for the RPM-QuaRand model with the interval-type probabilities of belonging* can be written as follows:

*   maximize the entropy function (6.11)
    
      
    $$\\begin{array}{r} \\left. H\_{B}(\\mathbf{p},Q)\\Rightarrow\\max\_{\\mathbf{p},Q} \\right. \\\\ \\end{array}$$  
    (6.16)
    
*   subject to:
    
    *   –the interval-type conditions
        
          
        $$\\begin{array}{r} {\\mathbf{p} \\in \\mathcal{I},\\text{\\quad\\quad}\\mathbf{q}^{(j)} \\in \\mathcal{I},\\quad j = \\overline{1,s},} \\\\ \\end{array}$$  
        (6.17)
        
        and
        
    *   –the balance constraints
        
          
        $$\\begin{array}{r} {\\mathcal{S}\\lbrack\\mathbf{x}\\lbrack j,\\tau\\rbrack,\\,\\mathbf{c}^{-} + C\\,\\mathbf{p};(j,\\tau) \\in \\mathcal{T}\_{s}\\rbrack + {\\overline{\\zeta}}\_{-}^{(j)} + L\_{j}\\,\\mathbf{q}^{(j)} = \\mathbf{y}^{(j)},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
        (6.18)
        

The constraints (6.17, 6.18) extract an admissible set Γ from the unit nonnegative *r*\-dimensional cube ℐ.

*The Boltzmann entropy-robust ML algorithm for the RPM-QuaRand model with the interval-type probabilities of belonging* has the form

  
$$\\begin{array}{r} \\left. {(\\mathbf{p},Q)}^{\*} = \\arg\\max\_{(\\mathbf{p},Q)}\\lbrack H\_{B},\\, \\middle| \\,(\\mathbf{p},Q) \\in \\Gamma\\rbrack. \\right. \\\\ \\end{array}$$  
(6.19)

In some applications, it is necessary to choose the generalized Fermi information entropy in order to eliminate the interval-type conditions:

  
$$\\begin{aligned} & {\\text{\\quad\\quad}H\_{F}(\\mathbf{p},Q) = - \\left\\langle \\mathbf{p},\\mathbf{ln}\\frac{\\mathbf{p}}{\\mathbf{p}\_{0}} \\right\\rangle - \\left\\langle (\\mathbf{1} - \\mathbf{p}),\\mathbf{ln}(\\mathbf{1} - \\mathbf{p}) \\right\\rangle -} \\\\ & {- {\\sum\\limits\_{j = 1}^{s}\\left( {\\left\\langle \\mathbf{q}^{(j)},\\mathbf{ln}\\frac{\\mathbf{q}^{(j)}}{\\mathbf{q}\_{0}^{(j)}} \\right\\rangle + \\left\\langle (\\mathbf{1} - \\mathbf{q}^{(j)}),\\mathbf{ln}(\\mathbf{1} - \\mathbf{q}^{(j)}) \\right\\rangle} \\right)},} \\\\ \\end{aligned}$$  
(6.20)

where *Q* = \[**q**^((1)), …, **q**^((*s*))\].

Clearly, the definition of this function explicitly considers the interval property of the variables. The admissible set is characterized by the balance constraints only.

*The Fermi entropy-robust estimation problem for the RPM-QuaRand model with the interval-type probabilities of belonging* can be written as follows:

*   maximize the entropy function (6.1.2)
    
      
    $$\\begin{array}{r} \\left. H\_{F}(\\mathbf{p},Q)\\Rightarrow\\max\_{\\mathbf{p},Q} \\right. \\\\ \\end{array}$$  
    (6.21)
    
*   subject to the balance constraints
    
      
    $$\\begin{array}{r} {\\mathcal{S}\\lbrack\\mathbf{x}\\lbrack j,\\tau\\rbrack,\\,\\mathbf{c}^{-} + C\\,\\mathbf{p};(j,\\tau) \\in \\mathcal{T}\_{s}\\rbrack + {\\overline{\\zeta}}\_{-}^{(j)} + L\_{j}\\,\\mathbf{q}^{(j)} = \\mathbf{y}\\lbrack j\\rbrack,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
    (6.22)
    

The constraints (6.22) extract an admissible set Θ from the unit nonnegative *n*\-dimensional cube ℐ.

*The Fermi entropy-robust ML algorithm for the RPM-QuaRand model with the interval-type probabilities of belonging* has the form

  
$$\\begin{array}{r} \\left. {(\\mathbf{p},Q)}^{\*} = \\arg\\max\_{(\\mathbf{p},Q)}\\lbrack H\_{F},\\, \\middle| \\,(\\mathbf{p},Q) \\in \\Theta\\rbrack, \\right. \\\\ \\end{array}$$  
(6.23)

where Θ is the set defined by the balance constraints. Note that the problem (6.21, 6.22) contains (*r* + *m**s*) less constraints than the problem (6.16–6.18). Due to this feature, the computational complexity of the estimation problem (6.21, 6.22) is smaller in comparison with its counterpart (6.16–6.18).

## 6.2Functional Description of Dynamic RPM-QuaRand Models

As established in the previous section, the estimation problems for the probabilities of belonging generally represent finite-dimensional nonlinear programming problems with entropy objective functions. The nonlinearity of these problems is caused by the nonlinearity of the functional 𝒮 that characterizes the model (6.5). Consider the models with one input and one output that are measured at discrete times from the interval 𝒯.

**1. Dynamic models with unstructured power nonlinearities**

A functional description of such a model has the following form

  
$$\\begin{aligned} {s\\lbrack j\\rbrack = {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{(n\_{1},\\ldots,n\_{h}) = 0}^{K\_{h}}w\_{h}}}} & {\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack x\\lbrack j - n\_{1}\\rbrack\\cdots x\\lbrack j - n\_{h}\\rbrack,} \\\\ & {j \\geq maxK\_{h}.} \\\\ \\end{aligned}$$  
(6.24)

(Also, see [Fig. 4.8](#chapter4.xhtml#f4_8).)

Its dynamic and nonlinear properties are reflected by the multidimensional pulse characteristics $w\_{h}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack,\\, h = \\overline{1,R},$ with a finite “memory” *K*[*h*], i.e.,

  
$$\\begin{aligned} {w\_{h}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {\\neq 0,\\quad\\text{for}\\,\\, 0 \\leq (n\_{1},\\ldots,n\_{h}) \\leq K\_{h};} \\\\ {w\_{h}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {= 0,\\quad\\text{for}\\,\\,(n\_{1},\\ldots,n\_{h}) > K\_{h}.} \\\\ \\end{aligned}$$  
(6.25)

As the model parameters consider the ordinates of its pulse characteristics. A lexicographical ordering of the variables yields

  
$$\\begin{array}{r} \\left. (n\_{1},\\ldots,n\_{h})\\rightarrow v,\\text{\\quad\\quad}v = \\overline{1,V\_{h}},\\,\\, V\_{h} = (K\_{h} + 1)\\, h, \\right. \\\\ \\end{array}$$  
(6.26)

Define a vector **c**^((*h*)) = {*c*[1]^((*h*)),…,*c*[*V*[*h*]]^((*h*))} composed of the ordinates of the pulse characteristic *w*[*h*]\[*n*[1], …, *n*[*h*]\]. Perform a similar operation with the products *x*\[*j* − *n*[1]\]⋯*x*\[*j* − *n*[*h*]\]. Introduce another vector

  
$$\\begin{array}{r} {\\mathbf{X}^{(h)}\\lbrack j\\rbrack = \\left\\{ x\_{1}^{(h)}\\lbrack j\\rbrack,\\ldots,x\_{V\_{h}}^{(h)}\\lbrack j\\rbrack \\right\\}} \\\\ \\end{array}$$  
(6.27)

composed of the lexicographically ordered products *x*\[*j* − *n*[1]\]⋯*x*\[*j* − *n*[*h*]\]. Then the model equation (6.1.2) can be transformed into

  
$$\\begin{array}{r} {s\\lbrack j\\rbrack = {\\sum\\limits\_{h = 1}^{R}\\left\\langle \\mathbf{c}^{(h)},\\mathbf{X}^{(h)}\\lbrack j\\rbrack \\right\\rangle}.} \\\\ \\end{array}$$  
(6.28)

As the result of all these manipulations, the original nonlinear model (6.1.2) has been reduced to its linear analog (6.28) of considerably higher dimension.

Using the probabilities of belonging **p** from [Section 6.3](#chapter6.xhtml#sec6_3), let us write the parameter vector **c**^((*h*)) as

  
$$\\begin{aligned} {\\mathbf{c}^{(h)} = \\mathbf{c}\_{-}^{(h)} + C^{(h)}\\mathbf{p}^{(h)},\\,\\, C\_{h} =} & \\left. \\text{diag}\\,\\lbrack(c\_{i}^{(h, + )} - c\_{i}^{(h, - )})\\, \\middle| \\, i = \\overline{1,V\_{h}}\\rbrack, \\right. \\\\ & {h = \\overline{1,R}.} \\\\ \\end{aligned}$$  
(6.29)

Substituting (6.29) into (6.28) gives the equation

  
$$\\begin{aligned} {s\\lbrack j\\rbrack} & {= \\hat{s}\\lbrack j\\rbrack + {\\sum\\limits\_{h = 1}^{R}\\left\\langle C\_{h}\\,\\mathbf{p}^{(h)},\\mathbf{X}^{(h)}\\lbrack j\\rbrack \\right\\rangle},} \\\\ {.\\hat{s}\\lbrack j\\rbrack} & {= {\\sum\\limits\_{h = 1}^{R}\\left\\langle \\mathbf{c}\_{-}^{(h)},\\mathbf{X}^{(h)}\\lbrack j\\rbrack \\right\\rangle}.} \\\\ \\end{aligned}$$  
(6.30)

**2. Dynamic models with structured power nonlinearities**

For this class of dynamic models, a functional description has the following form:

  
$$\\begin{array}{r} {s\\lbrack j\\rbrack = {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{n = 0}^{K\_{h}}\\left( {w\_{h}\\lbrack n\\rbrack x\\lbrack j - n\\rbrack} \\right)^{h}}},\\text{\\quad\\quad}j > K.} \\\\ \\end{array}$$  
(6.31)

(Also, see [Fig. 4.11a](#chapter4.xhtml#f4_11).) Here the dynamic properties are reflected by the pulse characteristics $w\_{h}\\lbrack n\\rbrack,\\, h = \\overline{1,R},$ with a finite “memory” *K*[*h*], i.e.,

  
$$\\begin{array}{r} {w\_{h}\\lbrack n\\rbrack \\neq 0,\\quad\\text{for}\\,\\, 0 \\leq n \\leq K\_{h};\\text{\\quad\\quad}r\_{h}\\lbrack n\\rbrack = 0,\\quad\\text{for}\\,\\, n > K\_{h}.} \\\\ \\end{array}$$  
(6.32)

As the model parameters consider the ordinates of the pulse characteristics. In other words, the parameters make the vector

  
$$\\begin{array}{r} {\\mathbf{c}^{(h)} = \\left\\{ c\_{1}^{(h)},\\ldots,c\_{K\_{h}}^{(h)} \\right\\},} \\\\ \\end{array}$$  
(6.33)

where

  
$$\\begin{array}{r} {c\_{n}^{(h)} = w\_{h}\\lbrack n\\rbrack,\\text{\\quad\\quad}n = \\overline{0,K\_{h}}.} \\\\ \\end{array}$$  
(6.34)

Using the probabilities of belonging **p**, write the parameter vector **c**^((*h*)) in the form (6.29). Substituting these equalities into (6.31) yields the model equation

  
$$\\begin{array}{r} {s\\lbrack j\\rbrack = {\\sum\\limits\_{h = 1}^{R}\\left( {\\left\\langle \\mathbf{c}\_{-}^{(h)},\\mathbf{x}\\lbrack j\\rbrack \\right\\rangle + \\left\\langle C\_{h}\\,\\mathbf{p}^{(h)},\\mathbf{x}\\lbrack j\\rbrack \\right\\rangle} \\right)^{h}},} \\\\ \\end{array}$$  
(6.35)

where **x**\[*j*\] = {*x*\[*j*\],…,*x*\[*j*−*K*[*h*]\]}.

Thus, the relation between the model's output and parameters is essentially nonlinear (more specifically, a power function).

**3. Dynamic models with structured power nonlinearities**

For this class of dynamic models, a functional description has the following form:

  
$$\\begin{array}{r} {s\\lbrack j\\rbrack = {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{n = 0}^{K\_{h}}w\_{h}}}\\lbrack n\\rbrack x^{h}\\lbrack j - n\\rbrack,\\text{\\quad\\quad}j > K.} \\\\ \\end{array}$$  
(6.36)

(Also, see [Fig. 4.11b](#chapter4.xhtml#f4_11).) Its dynamic properties are described by the pulse characteristics $w\_{h}\\lbrack n\\rbrack,\\, h = \\overline{1,R},$ with a finite “memory” *K*[*h*] (6.32). As the parameters of this model adopt the ordinates of its pulse characteristics, i.e., the parameter vector is **c**^((*h*)) (6.34). Define a vector ${\\widetilde{\\mathbf{X}}}^{h}\\lbrack j\\rbrack$ composed of *x*^(*h*)\[*j*\], …, *x*^(*h*)\[*j* − *K*[*h*]\]. Then the model equation (6.36) can be transformed into

  
$$\\begin{array}{r} {s\\lbrack j\\rbrack = {\\sum\\limits\_{h = 1}^{R}\\left\\langle \\mathbf{c},{\\widetilde{\\mathbf{X}}}^{(h)}\\lbrack j\\rbrack \\right\\rangle},\\text{\\quad\\quad}j > K.} \\\\ \\end{array}$$  
(6.37)

Using the expression (6.29) in this equality, write

  
$$\\begin{aligned} {s\\lbrack j\\rbrack} & {= \\hat{s}\\lbrack j\\rbrack + {\\sum\\limits\_{h = 1}^{R}\\left\\langle C\_{h}\\,\\mathbf{p}^{(h)},{\\widetilde{\\mathbf{X}}}^{(h)}\\lbrack j\\rbrack \\right\\rangle},} \\\\ {\\hat{s}\\lbrack j\\rbrack} & {= {\\sum\\limits\_{h = 1}^{R}\\left\\langle \\mathbf{c}\_{-}^{(h)},{\\widetilde{\\mathbf{X}}}^{(h)}\\lbrack j\\rbrack \\right\\rangle}.} \\\\ \\end{aligned}$$  
(6.38)

Thus, the models of this structural class are linear in their parameters.

## 6.3Optimality Conditions and Structure of Entropy-Optimal Probabilities of Belonging

The entropy-robust estimation problems for the RPM-QuaRand models are classified as finite-dimensional entropy-nonlinear programming problems. Their nonlinear properties fully depend on the nonlinearity of the RPM-QuaRand model. In particular, if the dynamic model is represented by a functional Volterra series with the structure shown in [Fig. 4.11a](#chapter4.xhtml#f4_11), then the admissible set in the estimation problems is described by a system of equalities with power nonlinearities. In this case, the admissible set often has a nonconvex configuration, and the optimality conditions turn out to be local and therefore can be used only numerically. As a result, we fail in extracting common structural properties of the solutions (the probabilities of belonging) from these conditions. On the other hand, for the one-dimensional RPM-QuaRand models that are reducible to the linear form (6.30, 6.38), we can establish global optimality conditions and analyze the structural properties of the solutions.

**1. Normalized probabilities of belonging**

The general problem within the functional model framework is characterized by equalities (6.12–6.14). It will be adapted to the case in which the functional model is one-dimensional and reducible to the linear form (6.30):

  
$$\\begin{aligned} {s\\lbrack j\\rbrack} & {= \\hat{s}\\lbrack j\\rbrack + {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{i = 1}^{V\_{h}}p\_{i}^{(h)}}}z\_{i}^{(h)}\\lbrack j\\rbrack + \\zeta\_{j}^{-} + Z\_{j}q\_{j},} \\\\ \\end{aligned}$$  
(6.39)

  
$$\\begin{aligned} {\\hat{s}\\lbrack j\\rbrack} & {= {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{i = 1}^{V\_{h}}c\_{-}^{(h)}}}(i)z\_{i}^{(h)}\\lbrack j\\rbrack,} \\\\ {z\_{i}^{(h)}\\lbrack j\\rbrack} & {= \\delta\_{i}^{(h)}x\_{i}^{(h)}\\lbrack j\\rbrack,\\text{\\quad\\quad}\\delta\_{i}^{(h)} = c\_{i}^{(h, + )} - c\_{i}^{(h, - )},\\quad i = \\overline{1,V\_{h}},} \\\\ Z\_{j} & {= \\zeta\_{j}^{+} - \\zeta\_{j}^{-},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(6.40)

Then the constraints (6.13, 6.14) in the estimation problem (6.12) take the following form.

*   The normalization conditions for the probabilities of belonging of the model parameters in the power blocks of the functional model are
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{i = 1}^{V\_{h}}p\_{i}^{(h)}} = 1,\\quad h = \\overline{1,R};} \\\\ \\end{array}$$  
    (6.41)
    
*   The normalization conditions for the probabilities of belonging of the measurement noises are
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{j = 1}^{s}q\_{j}} = 1;} \\\\ \\end{array}$$  
    (6.42)
    
*   The empirical balance conditions are
    
      
    $$\\begin{aligned} & {\\widetilde{s}\\lbrack j\\rbrack + {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{i = 1}^{V\_{h}}p\_{i}^{(h)}}}z\_{i}^{(h)}\\lbrack j\\rbrack + Z\_{j}q\_{j} - y\\lbrack j\\rbrack = 0,\\quad j = \\overline{1,s},} \\\\ & {\\widetilde{s}\\lbrack j\\rbrack = \\hat{s}\\lbrack j\\rbrack + \\zeta\_{j}^{-}.} \\\\ \\end{aligned}$$  
    (6.43)
    

The entropy function is given by

  
$$\\begin{array}{r} {H\_{B}(P,Q) = - {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{i = 1}^{V\_{h}}p\_{i}^{(h)}}}\\,\\ln\\frac{p\_{i}^{(h)}}{{\\widetilde{p}}\_{i}^{(h)}} - {\\sum\\limits\_{j = 1}^{s}q\_{j}}\\,\\ln\\frac{q\_{j}}{{\\widetilde{q}}\_{j}}.} \\\\ \\end{array}$$  
(6.44)

Thus, the estimation problem can be written as

  
$$\\begin{array}{r} \\left. H\_{B}(P,Q)\\Rightarrow\\max \\right. \\\\ \\end{array}$$  
(6.45)

subject to the constraints (6.41, 6.42, 6.43).

In this problem, the admissible set Υ is described by a system of equalities and hence it represents a constrained optimization problem. To obtain optimality conditions, let us define the Lagrange function

  
$$\\begin{aligned} L\_{B} & {= H\_{B}(P,Q) + {\\sum\\limits\_{h = 1}^{R}\\lambda\_{h}}\\left( {1 - {\\sum\\limits\_{i = 1}^{V\_{h}}p\_{i}^{(h)}}} \\right) + \\mu\\left( {1 - {\\sum\\limits\_{j = 1}^{s}q\_{j}}} \\right)} \\\\ & {+ {\\sum\\limits\_{j = 1}^{s}\\theta^{(j)}}\\left( {y\\lbrack j\\rbrack - \\widetilde{s}\\lbrack j\\rbrack - {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{i = 1}^{V\_{h}}p\_{i}^{(h)}}}\\delta\_{i}^{(h)}x\_{i}^{(h)}\\lbrack j\\rbrack + Z\_{j}q\_{j}} \\right).} \\\\ \\end{aligned}$$  
(6.46)

Here *λ*[1], …, *λ*[*R*]; *μ*; *θ*[1], …, *θ*[*s*] denote the Lagrange multipliers for the corresponding constraints (6.41, 6.42, 6.43). The first-order optimality conditions in the direct variables (*P*, *Q*) yield the following system of equations:

  
$$\\begin{aligned} \\frac{\\partial L}{\\partial p\_{i}^{(h)}} & {= - \\ln\\frac{p\_{i}^{(h)}}{{\\widetilde{p}}\_{i}^{(h)}} - 1 - \\lambda\_{h} - {\\sum\\limits\_{j = 1}^{s}\\theta\_{j}}z\_{i}^{(h)}\\lbrack j\\rbrack = 0,} \\\\ h & {= \\overline{1,s};\\text{\\quad\\quad}i = \\overline{1,V\_{h}}.} \\\\ \\end{aligned}$$  
(6.47)

  
$$\\begin{array}{r} {\\frac{\\partial L}{\\partial q\_{j}} = \\ln\\frac{(1 - q\_{j}){\\widetilde{q}}\_{j}}{q\_{j}} - \\mu - Z\_{j} = 0,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.48)

In combination with the normalization conditions (6.41, 6.42), equations (6.47, 6.48) lead to the following expressions for the entropy-optimal probabilities of belonging of the model parameters and measurement noises that are parameterized by the Lagrange multipliers *θ*[1], …, *θ*[*s*]:

  
$$\\begin{aligned} {\\lbrack p\_{i}^{(h)}\\rbrack}^{\*} & {= \\frac{{\\widetilde{p}}\_{i}^{(h)}\\exp\\left( {- {\\sum\\limits\_{j = 1}^{s}\\theta\_{j}}z\_{i}^{(h)}\\lbrack j\\rbrack} \\right)}{{\\sum\\limits\_{k = 1}^{V\_{h}}{\\widetilde{p}}\_{k}^{(h)}}\\exp\\left( {- {\\sum\\limits\_{m = 1}^{s}\\theta\_{j}}z\_{k}^{(h)}\\lbrack m\\rbrack} \\right)},} \\\\ q\_{j}^{\*} & {= \\frac{{\\widetilde{q}}\_{j}\\exp( - \\theta\_{j}Z\_{j})}{{\\sum\\limits\_{m = 1}^{s}{\\widetilde{q}}\_{m}}\\exp( - \\theta\_{m}Z\_{m})}.} \\\\ \\end{aligned}$$  
(6.49)

  
$$\\begin{array}{r} {h = \\overline{1,R},\\quad i = \\overline{1,V\_{h}},\\quad j = \\overline{1,s}} \\\\ \\end{array}$$  

Introduce *V*[*h*] functions of integer argument $P^{(h)}\\lbrack i\\rbrack,\\, i = \\overline{}1,V\_{h},$ whose values are defined by the entropy-optimal probabilities of belonging. By this definition, $P^{(h)}\\lbrack i\\rbrack,\\, i = \\overline{}1,V\_{h},$ represent distribution functions for the probabilities of belonging. According to (6.49), they are exponential functions.

The Lagrange multipliers *θ*[1], …, *θ*[*s*] are calculated from the empirical balance constraints (6.43) after substitution of the entropy-optimal probabilities of belonging (6.49). For notational convenience, introduce

  
$$\\begin{aligned} {S\\lbrack j\\rbrack} & {= \\hat{s}\\lbrack j\\rbrack + \\zeta\_{j}^{-} - y\\lbrack j\\rbrack,} \\\\ {\\varphi^{(h)}(\\theta\_{1},\\ldots,\\theta\_{s})} & {= {\\sum\\limits\_{k = 1}^{(V\_{h})}{\\widetilde{p}}\_{k}^{(h)}}\\,\\exp( - {\\sum\\limits\_{l = 1}^{s}\\theta\_{l}}z\_{k}^{(h)}\\lbrack l\\rbrack),} \\\\ {\\psi\_{j}^{(h)}(\\theta\_{1},\\ldots,\\theta\_{s})} & {= {\\sum\\limits\_{k = 1}^{(V\_{h})}{\\widetilde{p}}\_{k}^{(h)}}\\, z\_{k}^{(h)}\\lbrack j\\rbrack\\,\\exp( - {\\sum\\limits\_{l = 1}^{s}\\theta\_{l}}z\_{k}^{(h)}\\lbrack l\\rbrack),} \\\\ \\end{aligned}$$  
(6.50)

and

  
$$\\begin{aligned} {\\mu(\\theta\_{1},\\ldots,\\theta\_{s}) = {\\sum\\limits\_{l = 1}^{s}{\\widetilde{q}}\_{l}}} & {\\exp( - \\theta\_{l}Z\_{l}),\\quad\\nu\_{j}(\\theta\_{j}) = {\\widetilde{q}}\_{j}Z\_{j}\\exp( - \\theta\_{j}Z\_{j}),} \\\\ & {\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(6.51)

With these notations, the empirical balance constraints take the form

  
$$\\begin{array}{r} {{\\sum\\limits\_{h = 1}^{R}\\frac{\\psi\_{j}^{(h)}(\\theta\_{1},\\ldots,\\theta\_{s})}{\\varphi^{(h)}(\\theta\_{1},\\ldots,\\theta\_{s})}} + \\frac{\\nu\_{j}(\\theta\_{j})}{\\mu(\\theta\_{1},\\ldots,\\theta\_{s})} + S\\lbrack j\\rbrack = 0,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.52)

**2. Interval-type probabilities of belonging**

The entropy-optimal estimation problem for the RPM-QuaRand model can be stated using the generalized Boltzmann information entropy (6.16–6.18). This form of the estimation problem involves a considerably larger number of constraints than the previous one (some of them are inequalities). Therefore, it moves to the class of finite-dimensional mathematical programming problem, and optimality conditions are defined by the Kuhn–Tucker theorem \[134\].

The solution procedure of the entropy-optimal estimation problem can be significantly simplified if we use the generalized Fermi information entropy (6.1.2) as the objective function. The interval properties of the probabilities of belonging for the model parameters and measurement noises are embedded in the entropy function, which makes the estimation problem a constrained optimization problem. Like before, optimality conditions can be derived using Lagrange's method of multipliers.

The Lagrange function for the problem (6.21, 6.22) takes the form

  
$$\\begin{array}{r} {L\_{F} = H\_{F}(P,Q) + {\\sum\\limits\_{j = 1}^{s}\\theta^{(j)}}\\left( {y\\lbrack j\\rbrack - \\hat{s}\\lbrack j\\rbrack - {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{i = 1}^{V\_{h}}p\_{i}^{(h)}}}z\_{i}^{(h)}\\lbrack j\\rbrack + \\zeta\_{j}^{-} + Z\_{j}q\_{j}} \\right).} \\\\ \\end{array}$$  
(6.53)

The first-order optimality conditions are given by the system of inequalities

  
$$\\begin{aligned} \\frac{\\partial L}{\\partial p\_{i}^{(h)}} & {= \\ln\\, p\_{i}^{(0,h)}\\frac{1 - p\_{i}^{(h)}}{p\_{i}^{(h)}} - {\\sum\\limits\_{j = 1}^{s}\\theta\_{j}}z\_{i}^{(h)}\\lbrack j\\rbrack,} \\\\ h & {= \\overline{1,R},\\, i = \\overline{1,V\_{h}};} \\\\ \\end{aligned}$$  
(6.54)

  
$$\\begin{array}{r} {\\frac{\\partial L}{\\partial q\_{j}} = \\ln\\, q\_{j}^{0}\\frac{1 - q\_{j}}{q\_{j}} - \\theta\_{j}Z\_{j} = 0,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.55)

Then the entropy-optimal probabilities of belonging of the model parameters and measurement noises that are parameterized by the Lagrange multipliers have the form

  
$$\\begin{aligned} p\_{i}^{(h),\*} & {= \\frac{p\_{i}^{(h,0)}}{p\_{i}^{(h,0)} + \\exp\\left( {{\\sum\\limits\_{j = 1}^{s}\\theta\_{j}}z\_{i}^{(h)}\\lbrack j\\rbrack} \\right)},} \\\\ h & {= \\overline{1,R},\\quad i = \\overline{1,V\_{h}},} \\\\ q\_{j}^{\*} & {= \\frac{q\_{j}^{0}}{q\_{j}^{0} + \\exp(\\theta\_{j}Z\_{j})},\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(6.56)

Clearly, the entropy-optimal probabilities of belonging lie within the unit intervals. To find the Lagrange multipliers, substitute the expressions (6.56) into the empirical balance constraints (6.22). By analogy with the previous case, introduce the following notations:

  
$$\\begin{aligned} {S\\lbrack j\\rbrack} & {= \\hat{s}\\lbrack j\\rbrack + \\zeta\_{j}^{-} - y\\lbrack j\\rbrack,} \\\\ {\\varphi\_{j}(\\theta\_{j})} & {= Z\_{j}\\frac{q\_{j}^{0}}{q\_{j}^{0} + \\exp(\\theta\_{j}Z\_{j}},} \\\\ {\\psi\_{j}^{(h)}(\\theta\_{1},\\ldots,\\theta\_{s})} & {= {\\sum\\limits\_{i = 1}^{V\_{h}}\\frac{p\_{i}^{(h,0)}}{p\_{i}^{(h,0)} + \\exp\\left( {{\\sum\\limits\_{l = 1}^{s}\\theta\_{l}}z\_{i}^{(h)}\\lbrack l\\rbrack} \\right)}}.} \\\\ \\end{aligned}$$  
(6.57)

Then the empirical balance equations can be written as

  
$$\\begin{array}{r} {{\\sum\\limits\_{h = 1}^{R}\\psi\_{j}^{(h)}}(\\theta\_{1},\\ldots,\\theta\_{s}) + \\varphi\_{j}(\\theta\_{j}) + S\\lbrack j\\rbrack = 0,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(6.58)

The left-hand sides of equations (6.52, 6.58) incorporate strictly monotonically decreasing functions, which guarantees the existence of a unique solution. (The proof of this fact is left to the interested reader). [Chapter 7](#chapter7.xhtml) below describes an algorithm for solving such multiplicative-type equations.

# CHAPTER 7 COMPUTATIONAL METHODS OF RANDOMIZED MACHINE LEARNING

DOI: [10.1201/9781003306566-7](https://doi.org/10.1201/9781003306566-7)

The general randomized machine learning problem is formulated in terms of functional entropy-linear programming, which allows us to obtain the optimal solution structure parameterized by the Lagrange multipliers. To calculate their values, we have to solve the nonstandard nonlinear equations with the so-called parameterized integral components, which can be found only numerically. Therefore, it is impossible to analytically estimate such important parameters of computational procedures as the Lipschitz constant, the Hölder constant, the degree of smoothness, and others. For solving these equations, our idea is to extend the randomization approach to the computational algorithms intended for solving the RML problems. The randomization approach itself was declared and repeatedly used before; see \[[135](#refbib.xhtml#r135)\]. However, the major properties of the randomized problem-oriented algorithms arise in the course of their implementation. In what follows, we will develop the algorithms for solving the empirical balance equations and calculating the multidimensional integrals on the basis of “packet” Monte Carlo simulations, which are implemented using heterogeneous-structure computing aids.

An important special class of the RML problems includes the machine learning problems with the probabilities of belonging and linear models. For this class, it is possible to obtain a structural representation of the optimal solutions parameterized by the Lagrange multipliers. The resulting balance constraints have a nonlinear form but without the integral components. For solving these equations, the multiplicative algorithms \[[140](#refbib.xhtml#r140), [142](#refbib.xhtml#r142)\] will be employed.

## 7.1Classes of Balance Equations in RML and ML Procedures

In [Chapters 4](#chapter4.xhtml) and [5](#chapter5.xhtml), we have derived the empirical balance equations for the RPM-Orig, RPM-Rel and RPM-CauRand models, in which the role of variables is played by the Lagrange multipliers. An analysis of these equations (more specifically, of the functions that form their components) allows us to separate out two classes of the nonlinear equations for further study.

**1. Equations with integral components**

The equations of this class arise in the RML procedures with the RPM-Orig and RPM-Rel models (5.74–5.76). Recall that the equations under consideration contain the definite multidimensional integrals that are parameterized by the Lagrange multipliers. For example, for the RPMs with the original parameters (RPM-Orig), the integral components have the form

  
$$\\begin{array}{r} {\\mathbb{M}\_{j}(\\theta) - \\mathbf{y}^{(j)} = 0,\\text{\\quad\\quad}j = \\overline{1,s},} \\\\ \\end{array}$$  
(7.1)

where

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\mathbb{M}\_{j}(\\theta) = \\mathcal{P}^{( - 1)}(\\theta){\\int\_{\\mathcal{A}}P\_{0}}(\\mathbf{a}) \\times} \\\\ & {\\times \\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathcal{B}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.}\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack \\times} \\\\ & \\left. \\quad \\times \\mathcal{B}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h})\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack d\\mathbf{a} + {\\mathbb{Q}}\_{j}({\\overline{\\theta}}^{(j)}), \\right. \\\\ {j = \\overline{1,s}.} & \\\\ \\end{aligned}$$  
(7.2)

In these equalities, the matrix $\\theta = \\lbrack{\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}\\rbrack$ and the functions $\\mathcal{P}(\\overline{\\theta})$ and ${\\mathbb{Q}}\_{j}({\\overline{\\theta}}^{(j)})$ are given by (5.4.1) and (5.75), respectively.

A similar situation also occurs for the randomized parametric models with the relative parameters (RPM-Rel). The balance equations for this class of models can be written as

  
$$\\begin{array}{r} {{\\mathbb{N}}\_{j}(\\overline{\\theta}) - \\mathbf{y}^{(j)} = 0,\\text{\\quad\\quad}j = \\overline{1,s},} \\\\ \\end{array}$$  
(7.3)

where

  
$$\\begin{aligned} {{\\mathbb{N}}\_{j}(\\theta) = \\mathcal{W}^{( - 1)}(\\theta){\\int\_{\\mathcal{U}}W\_{0}}(\\mathbf{u}) \\times} & \\\\ {\\times \\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathcal{D}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.}\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}^{-} + \\Delta\\mathbf{u}\\rbrack \\right\\rangle \\right\\rbrack \\times} & \\\\ \\left. \\times \\mathcal{D}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h})\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}^{-} + \\Delta\\mathbf{u}\\rbrack d\\mathbf{u} + \\mathbb{G}\_{j}({\\overline{\\theta}}^{(j)}), \\right. & \\\\ {j = \\overline{1,s}.} & \\\\ \\end{aligned}$$  
(7.4)

These expressions include 𝒲(*θ*) (5.4.2) and $\\mathbb{G}\_{j}({\\overline{\\theta}}^{(j)})$ (5.4.3). Note that the functionals ℬ and 𝒟 are of the power type.

Equations (7.1, 7.3) have a similar structure; using them, construct a class of nonlinear equations of the following form:

  
$$\\begin{array}{r} {\\mathbf{B}(\\mathbf{u}) = \\mathbf{B}\\left\\lbrack {{\\mathbb{C}}(\\mathbf{f})} \\right\\rbrack = \\mathbf{0},} \\\\ \\end{array}$$  
(7.5)

with the integral components

  
$$\\begin{array}{r} {{\\mathbb{C}}(\\mathbf{f}) = {\\int\_{\\mathcal{E}}\\exp}\\left( {- E(\\mathbf{f},\\mathbf{e})} \\right)d\\mathbf{e},} \\\\ \\end{array}$$  
(7.6)

or

  
$$\\begin{array}{r} {{\\mathbb{C}}(\\mathbf{f}) = {\\int\_{\\mathcal{E}}E}(\\mathbf{f},\\mathbf{e})\\exp\\left( {- \\mathcal{E}(\\mathbf{f},\\mathbf{e})} \\right)d\\mathbf{e},} \\\\ \\end{array}$$  
(7.7)

where

  
$$\\begin{array}{r} {E(\\mathbf{f},\\mathbf{e}) = {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{(n\_{1},\\ldots,n\_{h}) = 1}^{m}A\_{(n\_{1},\\ldots,n\_{h})}}}(\\mathbf{f})\\,{\\prod\\limits\_{k = 1}^{h}e\_{n\_{k}}}.} \\\\ \\end{array}$$  
(7.8)

The notations are as follows: **f** ∈ *R*^(*s*) as the vector of the desired variables, i.e., the parameters of the integral components; **B**(**u**) as a vector function that contains the vectors of the integral components (7.6) or (7.7); **e** ∈ *E* ⊂ *R*^(*r*) as the vector of the integration variables in (7.6, 7.7); finally, *E* as the *r*\-dimensional parallelepiped.

A numerical solution procedure for equation (7.5) consists of the following steps: (a) calculating the integral components ℂ(**f**) under fixed variables **f** and (b) calculating the new vector of the variables that is the solution of the corresponding balance equations. This procedure corresponds to an iterative process with the structure illustrated in [Fig. 7.1](#chapter7.xhtml#f7_1). It has the main iterative loop (see double lines) intended for solving equation (7.5) using the algorithm

![Figure 7.1](images/fig7_1.jpg)

[Figure 7.1](#chapter7.xhtml#f7_1b)

  
$$\\begin{array}{r} {\\mathbf{f}^{(k + 1)} = \\Omega\\left( {\\mathbf{f}^{k},\\mathbf{B}\\left\\lbrack {{\\mathbb{C}}(\\mathbf{f}^{k})} \\right\\rbrack} \\right),} \\\\ \\end{array}$$  
(7.9)

and also the secondary loop (see single lines) intended for calculating the function **B** with the integral components (7.6, 7.7).

Get back to equation (7.5), reducing it to a more convenient form for calculations. Introduce a change of variables that maps the space *R*^(*s*) and the domain ℰ ∈ *R*^(*r*) into the unit nonnegative cubes of proper dimensions. Since the domain ℰ is the *r*\-dimensional parallelepiped, this transformation can be performed with the linear change of variables

  
$$\\begin{aligned} {\\mathbf{w} = L\\,\\mathbf{e} - \\mathbf{e}^{-},} & \\left. \\quad L = \\text{diag}\\,\\lbrack 1/(e\_{i}^{+} - e\_{i}^{-}),\\, \\middle| \\, i = \\overline{1,r}\\rbrack, \\right. \\\\ & {\\mathbf{w} \\in I^{r} \\subset R\_{+}^{r} = \\lbrack\\mathbf{0},\\mathbf{1}\\rbrack.} \\\\ \\end{aligned}$$  
(7.10)

The space *R*^(*s*) can be mapped into the unit nonnegative *s*\-dimensional cube by nonlinear transformations, e.g.,

  
$$\\begin{array}{r} {\\mathbf{z} = \\left\\{ \\frac{1}{1 + \\exp f\_{i}},\\, \\middle| \\, i = \\overline{1,s} \\right\\},\\text{\\quad\\quad}\\mathbf{z} \\in I^{s}.} \\\\ \\end{array}$$  
(7.11)

Using these transformations in (7.5), write

  
$$\\begin{array}{r} {\\mathbf{W}(\\mathbf{z}) = \\mathbf{0},\\text{\\quad\\quad}\\mathbf{z} \\in I^{s}.} \\\\ \\end{array}$$  
(7.12)

The integral components in this equation are

  
$$\\begin{array}{r} {\\mathbf{C}(\\mathbf{z}) = {\\int\_{I^{r}}\\exp}\\left( {- E(\\mathbf{z},\\mathbf{w})} \\right)d\\mathbf{w} = \\mathbf{0},\\text{\\quad\\quad}\\mathbf{z} \\in I^{s},\\quad\\mathbf{w} \\in I^{r},} \\\\ \\end{array}$$  
(7.13)

or

  
$$\\begin{aligned} {\\mathbf{G}(\\mathbf{z}) = \\int\_{I^{r}}} & {\\exp\\left( {- E(\\mathbf{z},\\mathbf{w})} \\right)\\exp\\left( {- E(\\mathbf{z},\\mathbf{w})} \\right)d\\mathbf{w} = \\mathbf{0},} \\\\ & {\\text{\\quad\\quad}\\mathbf{z} \\in I^{s},\\quad\\mathbf{w} \\in I^{r},} \\\\ \\end{aligned}$$  
(7.14)

where

  
$$\\begin{array}{r} {E(\\mathbf{z},\\mathbf{w}) = {\\sum\\limits\_{h = 1}^{R}{\\sum\\limits\_{(n\_{1},\\ldots,n\_{h}) = 1}^{m}A\_{(n\_{1},\\ldots,n\_{h})}}}(\\mathbf{z})\\,{\\prod\\limits\_{k = 1}^{h}w\_{n\_{k}}}.} \\\\ \\end{array}$$  
(7.15)

Equation (7.12) will be solved by minimizing the residual function

  
$$\\begin{array}{r} \\left. F(\\mathbf{z}) = \\|\\mathbf{W}(\\mathbf{z})\\|\\Rightarrow\\min\_{\\mathbf{z}},\\text{\\quad\\quad}\\mathbf{z} \\in I^{s}. \\right. \\\\ \\end{array}$$  
(7.16)

Note that it is impossible to establish any characteristics of the residual function analytically due to its integral components. Thus, we have to hypothesize several local minima of the function *F*(**z**) on the admissible set *I*^(*s*). Hence, the problem (7.16) comes to a global minimization of this function.

**2. Equations with analytical functions**

The balance equation of this class arise in the ML problems with the RPM-QuaRand models. The probabilities of belonging that characterize the parameters of these models can be normalized or interval-type. In the former case, the ML-based estimation algorithm is formulated as a constrained maximization problem for the generalized Boltzmann information entropy. In the latter case, it seems more convenient to choose the generalized Fermi information entropy.

Write the empirical balance equations for the normalized probabilities of belonging (6.52) in the form

  
$$\\begin{array}{r} {m\_{j}(\\mathbf{v}) = {\\sum\\limits\_{h = 1}^{R}\\frac{\\beta^{(h)}(v\_{1},\\ldots,v\_{s};\\, j)}{\\alpha^{(h)}(v\_{1},\\ldots,v\_{s})}} + \\gamma\_{j}(v\_{1},\\ldots,v\_{s}) = 0,\\quad j = \\overline{1,s},} \\\\ \\end{array}$$  
(7.17)

where

  
$$\\begin{aligned} {\\alpha^{(h)}(v\_{1},\\ldots,v\_{s})} & {= {\\sum\\limits\_{k = 1}^{V\_{h}}p\_{k}^{(h,0)}}{\\prod\\limits\_{l = 1}^{V\_{h}}v\_{l}^{z\_{k}^{(h)}\\lbrack l\\rbrack}},} \\\\ {\\beta\_{k}^{(h)}(v\_{1},\\ldots,v\_{s};\\, j)} & {= {\\sum\\limits\_{k = 1}^{V\_{h}}z\_{k}^{(h)}}\\lbrack j\\rbrack p\_{k}^{(h,0)}{\\prod\\limits\_{l = 1}^{V\_{h}}v\_{l}^{z\_{k}^{(h)}\\lbrack l\\rbrack}},} \\\\ {\\gamma\_{j}(v\_{1},\\ldots,v\_{s})} & {= S\\lbrack j\\rbrack + \\frac{q\_{j}^{0}Z\_{j}v\_{j}^{Z\_{j}}}{{\\sum\\limits\_{l = 1}^{s}q\_{j}^{0}}v\_{j}^{Z\_{l}}} - y\\lbrack j\\rbrack,} \\\\ v\_{l} & {= \\exp( - \\theta\_{l}),\\text{\\quad\\quad}l = \\overline{1,s}.} \\\\ \\end{aligned}$$  
(7.18)

The variables in these equations are defined on the nonnegative orthant *R*[+]^(*s*). Sometimes, they are called the exponential Lagrange multipliers.

Consider the empirical balance equations for the interval probabilities of belonging (6.58) and represent them in terms of the variables (*v*[1], …, *v*[*s*]) ≥ 0 (7.18). Introduce the following notations:

  
$$\\begin{aligned} {\\varrho\_{j}^{(h)}(v\_{1},\\ldots,v\_{s})} & {= {\\sum\\limits\_{i = 1}^{V\_{h}}\\frac{p\_{i}^{(h,0)}}{p\_{i}^{(h,0)} + {\\prod\\limits\_{l = 1}^{s}v\_{l}^{z\_{i}^{(h)}\\lbrack l\\rbrack}}}},} \\\\ {\\vartheta\_{j}(v\_{j})} & {= Z\_{j}\\frac{q\_{j}^{0}}{q\_{j}^{0} + v\_{j}^{Z\_{j}}},} \\\\ {\\omega\\lbrack j\\rbrack} & {= \\vartheta\_{j}(v\_{j}) + \\hat{s}\\lbrack j\\rbrack + \\zeta\_{j}^{-} - y\\lbrack j\\rbrack.} \\\\ \\end{aligned}$$  
(7.19)

Write equations (6.58) as

  
$$\\begin{array}{r} {n\_{j}(\\mathbf{v}) = {\\sum\\limits\_{h = 1}^{R}\\varrho\_{j}^{(h)}}(v\_{1},\\ldots,v\_{s}) + \\omega\\lbrack j\\rbrack = 0,\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  
(7.20)

The final forms of the empirical balance equations allow us to identify some general properties of these equations, which can be fruitful for choosing appropriate computational methods.

## 7.2Monte Carlo Packet Iterations for Global Optimization

The RML algorithms for the RPM-Orig and RPM-Rel models are intended for solving the empirical balance equations, in which the role of variables is played by the Lagrange multipliers or by the auxiliary variables taking their values within the unit nonnegative cube. An approach to design numerical methods proceeds from minimization of a residual function (generally, a quadratic norm). In an RML problem, there exists an algorithmically defined relation between the residual function and variables, and this feature of the problem finally reduces it to a global minimization problem. Under such conditions, the Monte Carlo method seems to be an suitable design tool for RML algorithms.

Vast amounts of literature have been published dealing with applications of the Monte Carlo method in different global optimization problems. Some insight into these problems and methods to solve them can be gained from \[135, 158, 171–[173](#refbib.xhtml#r173), [196](#refbib.xhtml#r196), [199](#refbib.xhtml#r199)\].

In contrast to the existing methods, the idea put forward here is to use *simple Monte Carlo simulations*, i.e., the generation of independent random vectors with the uniform distribution on the nonnegative unit cube.

### 7.2.1Canonical form of global optimization problem

Consider the global minimization problem

  
$$\\begin{aligned} & \\left. f(\\mathbf{x})\\Rightarrow\\text{globmin} \\right. \\\\ & \\text{subject~to~the~following~constraints:} \\\\ & {\\mathbf{x} \\in \\mathcal{G}\_{\\mathbf{x}} = \\left\\{ \\mathbf{x}:\\mathbf{g}(\\mathbf{x}) \\leq \\mathbf{0},\\,\\mathbf{x} \\in R^{d} \\right\\},\\quad\\mathbf{g} \\in R^{r},\\, r < d.} \\\\ \\end{aligned}$$  
(7.21)

The objective function *f*(**x**) satisfies the Hölder condition with constants *H* > 0 and *w* > 0, i.e., its modulus of continuity has the form

  
$$\\begin{array}{r} \\left. \\omega(t) = \\max\_{(\\widetilde{\\mathbf{v}},\\widetilde{\\mathbf{y}}) \\in R^{d}\\mspace{2mu}:\\|\\widetilde{\\mathbf{v}} - \\widetilde{\\mathbf{y}}\\| \\leq t} \\middle| f(\\widetilde{\\mathbf{v}}) - f(\\widetilde{\\mathbf{y}}) \\middle| \\leq Ht^{w}. \\right. \\\\ \\end{array}$$  
(7.22)

The functions **g**(**x**) in (7.22) are assumed to be continuous.

Write *the canonical form* of the problem (7.21) as

  
$$\\begin{aligned} & \\left. F(\\mathbf{z})\\Rightarrow\\text{globmin} \\right. \\\\ \\end{aligned}$$  
(7.23)

  
$$\\begin{aligned} & \\text{subject~to~the~following~constraints:} \\\\ & {\\mathbf{z} \\in \\mathcal{K}\_{\\mathbf{z}} = \\mathcal{G}\_{\\mathbf{z}}{\\cap Z\_{+}^{d}},} \\\\ & {Z\_{+}^{d} = \\left\\{ \\mathbf{z}:\\mathbf{0} \\leq \\mathbf{z} \\leq \\mathbf{1} \\right\\} \\subset R^{d},} \\\\ & {\\mathcal{G}\_{\\mathbf{z}} = \\left\\{ \\mathbf{z}:\\mathbf{w}(\\mathbf{z}) \\leq \\mathbf{0},\\,\\mathbf{z} \\in Z\_{+}^{d} \\right\\},\\quad\\mathbf{w} \\in R^{r},\\, r < d.} \\\\ \\end{aligned}$$  
(7.24)

A relation between the original problem and its canonical form is defined by a continuously differentiable bijective transformation of the variables, i.e.,

  
$$\\begin{array}{r} {\\mathbf{z} = \\mathcal{T}(\\mathbf{x}),\\text{\\quad\\quad}\\mathbf{x} = \\mathcal{T}^{( - 1)}(\\mathbf{z}).} \\\\ \\end{array}$$  
(7.25)

In fact, quite a few transformations answer these conditions, e.g.,

  
$$\\begin{aligned} & {\\mathbf{z} = \\left\\{ \\frac{1}{1 + exp( - a\_{i}x\_{i})},\\, \\middle| \\, i = \\overline{1,d} \\right\\},} \\\\ & {\\mathbf{x} = \\left\\{ \\frac{1}{a\_{i}}\\ln\\frac{z\_{i}}{1 - z\_{i}},\\, \\middle| \\, i = \\overline{1,d} \\right\\}.} \\\\ \\end{aligned}$$  
(7.26)

Due to the continuity of the transformation (7.26), the function *F*(**z**) is bounded below on 𝒦[**z**], i.e., there exists a constant *c* such that

  
$$\\begin{array}{r} {F^{\*} \\geq c.} \\\\ \\end{array}$$  
(7.30)

The constant *c* is generally unknown but equals 0 in some special global minimization problems. For example, this takes place for the problems in which the function *F*(**z**) is defined as the residual between the left- and right-hand sides of a certain system of equations.

The function *F*(**z**) also satisfies the Hölder condition with other constants *L* and *p*, i.e.,

  
$$\\begin{array}{r} \\left. \\omega(h) = \\max\_{(\\mathbf{v},\\mathbf{y}) \\in \\mathcal{K}\_{\\mathbf{x}}\\mspace{2mu}:\\|\\mathbf{v} - \\mathbf{y}\\| \\leq h} \\middle| F(\\mathbf{v}) - F(\\mathbf{y}) \\middle| \\leq Lh^{s}. \\right. \\\\ \\end{array}$$  
(7.31)

Denote by *ℤ*^(\*) the set of all global minimum points **z**^(\*) and by *F*(**z**^(\*)) = *F*^(\*) the global minimum value in the problem (7.23). In other words, assume that a global minimum is achieved not at a unique point but on a finite set ℤ^(\*).

How should we comprehend the *solution* of the problem (7.23)? This issue is of crucial importance, as its obviousness disappears for real computational processes. Actually, it is impossible to achieve an exact value of the global minimum *F*^(\*) even with an arbitrarily high accuracy of calculations. We can speak about getting into some *r*\-neighborhood of the exact global minimum value. In other words, the matter concerns an *approximate* global minimum value *F̃*^(\*) within the *r*\-neighborhood. At the very beginning, we have declared to employ the Monte Carlo method for global minimization. Hence, the value *F̃*^(\*) gets into the *r*\-neighborhood with a certain probability, less or equal to 1.

Also note that computations are implemented through iterative procedures that represent a sequence of steps with numbers *k*. Each step yields an intermediate result. In the problem (7.23), the intermediate results are the values $\\widetilde{F\_{1}^{\*},\\ldots,\\widetilde{F\_{k}^{\*},\\ldots}}.$ Assume that at some step *k*^(\*) an approximate global minimum value *F̃*[*k*^(\*)]^(\*) has entered an *r*\-neighborhood. Nevertheless, this event is random and it may happen that at step (*k*^(\*) + 1), the value leaves the neighborhood. For increasing the reliability of approximate global minimization, introduce a positive number *ϱ* that characterizes the number of steps during which the values *F̃*[*k*^(\*)]^(\*), *F̃*[(*k*^(\*) + *k*[1])]^(\*), …, *F̃*[(*k*^(\*) + *k*[𝜚])]^(\*) stay within the *r*\-neighborhood after first getting into it at step *k*^(\*).

### 7.2.2Idea of method and concept of solution

Consider a simplified statement of the problem (7.23) in which the admissible set is the *d*\-dimensional cube *Z*[+]^(*d*). This problem is solved by an algorithm that represents an iterative procedure to construct a sequence of records

At step *k*, the algorithm generates a batch 𝒵[*k*] of the *N*[*k*] = *M*[*k*]^(*d*) independent random vectors **z**¹, …, **z**^(*N*[*k*]) obeying the uniform distribution on *Z*[+]^(*d*). Here *M*[*k*] denotes the number of independent uniformly distributed random variables on the interval \[0, 1\] that are produced at step *k* by a random generator for each of the *d* coordinates.

For the *k*th batch, the algorithm calculates the values of the function $F(\\mathbf{z}^{j}),\\, j = \\overline{1,N\_{k}},$ as well as its minimum value *F*[*k*]^(\*) (the *k*th record) and argument **z**[*k*]^(\*). Due to a random character of the Monte Carlo simulations, the value *F*[*k*]^(\*) is also random.

Transition to step (*k* + 1) consists in increasing the number of random vectors by the rule

  
$$\\begin{array}{r} {M\_{k + 1} = \\alpha M\_{k},\\text{\\quad\\quad}\\alpha > 1,} \\\\ \\end{array}$$  
(7.32)

and calculating a new record *F*[*k* + 1]^(\*) for the (*k* + 1) th packet. This yields a monotonically decreasing sequence

  
$$\\begin{array}{r} {\\mathcal{F} = \\left\\{ F\_{0}^{\*} \\geq \\ldots, \\geq F\_{k}^{\*},\\ldots \\right\\}.} \\\\ \\end{array}$$  
(7.33)

In addition to the records sequence (7.33), the algorithm constructs a sequence of their decrements

  
$$\\begin{array}{r} {\\mathcal{U} = \\left\\{ u\_{1},\\ldots,\\, u\_{k},\\ldots \\right\\},} \\\\ \\end{array}$$  
(7.34)

where *u*[*k*]\=|*F*[*k*]^(\*)−*F*[*k* + 1]^(\*)|.

The algorithm stops when the sequence of random variables *u*[*k*] stays within a given *δ*\-neighborhood of the origin during *ρ* successive steps, i.e., the number of steps till its termination is

  
$$\\begin{array}{r} {\\tau = \\min\\left\\{ k:\\max\_{k - \\rho \\leq s \\leq k}u\_{s} \\leq \\delta \\right\\}.} \\\\ \\end{array}$$  
(7.35)

In the sequel, this algorithm will be called the *GFS algorithm (Generation, Filtration, Selection)*.

*The solution of the problem (7.23)* is represented by the quadruple

  
$$\\begin{array}{r} {S = \\left\\{ F\_{\\tau}^{\*},\\mathbf{z}\_{\\tau}^{\*},r\_{\\tau}^{\*},\\mathbf{P}(\\mathcal{E}\_{r\_{\\tau}}) \\right\\},} \\\\ \\end{array}$$  
(7.36)

where

*   *F*[*τ*]^(\*), **z**[*τ*]^(\*) indicate an approximate global minimum value and its argument, respectively, at the stop time *τ*;
    
*   *r*[*τ*]^(\*) is the estimated size of the neighborhood of the exact global minimum value at the stop time *τ*;
    
*   the event
    
      
    $$\\begin{array}{r} {\\mathcal{E}\_{r\_{\\tau}^{\*}} = \\left\\{ F\_{\\tau}^{\*} - F^{\*} \\leq r\_{\\tau} \\right\\},} \\\\ \\end{array}$$  
    (7.37)
    
    where *F*^(\*) gives the exact global minimum value on the set *Z*[+]^(*d*);
    
*   **P**(ℰ[*r*[*τ*]^(\*)]) denotes an estimated probability of the event (7.37).
    

A real algorithm involves a strictly monotonically decreasing subsequence

  
$$\\begin{array}{r} {\\mathbb{F}^{\*} = \\left\\{ F\_{1}^{\*} > \\ldots, > F\_{k}^{\*},\\ldots \\right\\}} \\\\ \\end{array}$$  
(7.38)

of the sequence ℱ^(\*) (7.33). A theoretical analysis below is based on exploring the properties of the sequence ℱ^(\*). As 𝔽^(\*) forms a subsequence of ℱ^(\*), in qualitative terms the analysis results remain the same for the subsequence 𝔽^(\*).

### 7.2.3Probabilistic characteristics of random sequences ℱ and 𝒰

A study of the random sequences generated by the packets of simple Monte Carlo simulations is an important stage to investigate the fundamental properties of the GFS algorithm in terms of computations. These properties include convergence analysis (in particular, convergence conditions) and estimation of the numerical characteristics of a resulting solution \[[35](#refbib.xhtml#r35)\].

**1. Probabilistic characteristics of packets 𝒵[*k*]**

In each stage *k*, the algorithm generates a packet 𝒵[*k*] of *N*[*k*] independent random vectors with the uniform distribution on the *d*\-dimensional cube. The source of the packet 𝒵[*k*] is a random generator: for each of the *d* coordinates at step *k* it produces an array of *M*[*k*] independent uniformly distributed random variables on the interval \[0, 1\] (simple Monte Carlo simulations). As a result, at step *k* we have a packet of (*M*[*k*])^(*d*) random vectors obeying the uniform distribution on the unit cube.

Consider the unit cube *Z*[+]^(*d*) (7.23) and its partition into elementary cubes using a *virtual* uniform lattice with the step

  
$$\\begin{array}{r} {\\eta\_{k} = M\_{k}^{- q}} \\\\ \\end{array}$$  
(7.39)

for each of the *d* coordinates. Here *q* specifies a lattice parameter such that

  
$$\\begin{array}{r} {0 < \\gamma \\leq q \\leq \\beta < 1.} \\\\ \\end{array}$$  
(7.40)

Denote by *P*(*M*[*k*], *d*, *q*) the probability that there exists an elementary *virtual* cube containing none of the random (*M*[*k*])^(*d*) vectors generated at step *k*. This probability can be estimated as follows.

**2. Probabilistic properties of sequence ℱ^(\*)**

Consider a sequence of “quasi global” minimum values ℱ^(\*) = {*F*[0]^(\*),…,*F*[*k*]^(\*),…} and a sequence of the corresponding arguments 𝒵^(\*) = {**z**[0]^(\*),…,**z**[*k*]^(\*),…}.

Denote by *ℤ*^(\*) the set of all global minimum points of the function *F*( ⋅ ) on the unit cube. Introduce the distance *l*( ⋅ ) between an arbitrary point **z** and the compact set *ℤ*^(\*) in the form

  
$$\\begin{array}{r} {l(\\mathbf{z},{\\mathbb{Z}}^{\*}) = \\min\_{\\mathbf{y} \\in {\\mathbb{Z}}^{\*}}\\|\\mathbf{z} - \\mathbf{y}\\|.} \\\\ \\end{array}$$  
(7.46)

Note that the upper bounds (7.53)–(7.54) depend on the parameter *q*, which affects the volume of the *virtual* elementary cube with the side (7.39) for each coordinate. The constants *β* and *γ* in (7.40) should be adjusted for reaching an acceptable result in terms of the size of the desired neighborhood and the corresponding probability.

### 7.2.4Convergence of GFS algorithm

Using the probabilistic characteristics of the records sequence ℱ[*k*]^(\*), we can establish the following result on its convergence.

### 7.2.5Study of decrements sequence 𝒰

For the Hölder-type functions, the upper bound (7.53) holds with the probability 1 − *Q*(*M*[*k*], *d*, *q*); see Corollary 2. Because *r*[*k* + 1](*q*) < *r*[*k*](*q*),

  
$$\\begin{array}{r} \\left. u\_{k} = \\middle| F\_{k + 1}^{\*} - F\_{k}^{\*} \\middle| \\leq DM\_{k}^{- p}. \\right. \\\\ \\end{array}$$  
(7.66)

Then it follows that, for sufficiently large *k*,

  
$$\\begin{array}{r} {u\_{k} \\approx DM\_{k}^{- p}.} \\\\ \\end{array}$$  
(7.67)

Let us take the logarithm of both sides of this approximate expression:

  
$$\\begin{array}{r} {v\_{k} = \\log u\_{k} \\approx \\log D - p\\log M\_{k}.} \\\\ \\end{array}$$  
(7.68)

An example of the relation *v*[*k*](*n*[*k*]) for a computational process is illustrated in [Fig. 7.2](#chapter7.xhtml#f7_2).

![Figure 7.2](images/fig7_2.jpg)

[Figure 7.2](#chapter7.xhtml#f7_2b)

Consider a sequence of independent random variables *ζ*[*k*] with zero mean and a finite variance *σ*². Add this sequence to the right-hand side of the approximate expression to simulate a random character of the sequence of *v*[*k*]'s, i.e.,

  
$$\\begin{array}{r} {v\_{k} = A - Bn\_{k} + \\zeta\_{k},} \\\\ \\end{array}$$  
(7.69)

where

  
$$\\begin{array}{r} {A = \\log D,\\text{\\quad\\quad}B = p,\\quad n\_{k} = \\log M\_{k}.} \\\\ \\end{array}$$  
(7.70)

The parameters *A* and *B* related to the Hölder constants and *σ*² are unknown. Their estimates *Â*(*k*), *B̂*(*k*) and *σ̂*²(*k*) will be constructed using the least-squares method based on the available information about the elements of the sequence {*F*[*k*]^(\*)}. This is easy to implement, since (7.69) represents a *linear* model (in this context, note once again that the linear regression (7.69) in *the log-log scale* directly follows from the upper bound (7.53)).

With these estimates, we can also estimate the size *r*[*k*](*q*) of the corresponding neighborhood of the exact global minimum. According to (7.53),

  
$$\\begin{array}{r} {r\_{k}(q) = \\log{\\hat{A}}^{(k)}M\_{k}^{(\\frac{{\\hat{B}}^{(k)}}{q})}.} \\\\ \\end{array}$$  
(7.71)

Clearly, the relation *r*[*k*](*q*) is monotonically decreasing on the interval \[*γ*, *β*\] (7.40). Hence, it achieves minimum at *q* = *β*. The estimated size of the neighborhood at the stop time *τ* is

  
$$\\begin{array}{r} {r\_{\\tau}(\\beta) = \\log{\\hat{A}}^{(\\tau)}M\_{\\tau}^{(\\frac{{\\hat{B}}^{(\\tau)}}{\\beta})},} \\\\ \\end{array}$$  
(7.72)

and a lower bound for its probability (7.54) (see Corollary 2) has the form

  
$$\\begin{array}{r} {P\\left\\{ 0 \\leq F\_{\\tau}^{\*} - F^{\*} \\leq r\_{\\tau} \\right\\} \\geq M\_{\\tau}^{\\beta d}\\exp\\left( {- M\_{\\tau}^{(1 - \\beta)d}} \\right).} \\\\ \\end{array}$$  
(7.73)

### 7.2.6Admissible set 𝒦(**z**) of general form

Up to this point, we have considered the global minimization problem in which the domain of definition of variables **z** and the admissible set coincide. Now let us address the general case, where the admissible set 𝒦(**z**) (7.23) represents a part of the unit cube 𝒵[+]^(*d*). More specifically, it forms an intersection of the unit cube and a subset 𝒢 described by a system of inequalities with continuous functions.

The admissible set under study has a smaller volume, and hence the number of elementary cubes in its virtual partition is decreased. However, this number necessarily does not exceed the number of such cubes in the unit cube partition. Therefore, the derived probability estimates (ergo, the propositions on the algorithm convergence) remain valid for a compact set that is defined by a system of continuous functions and has a positive Lebesgue measure.

Consider the admissible domain 𝒦[**z**] (7.23) in the unit cube. Assume that it contains no isolated points and its *d*\-dimensional Lebesgue measure *ν* is nonzero, i.e., 0 < *ν*[0] ≤ *ν* ≤ 1.

First, analyze the case in which the value *ν* is known. Then the probability that a specific vector from a generated sequence of independent random vectors with the uniform distribution on the unit cube gets into the admissible domain is *ν*. Let *N*[*k*] independent random vectors be generated at step *k* with the uniform distribution on *Z*[+]^(*d*), including *N̂*[*k*] vectors within the admissible domain. Denote by *κ*[*N*[*k*]] the frequency with which the generated vectors occur within the admissible set 𝒦[**z**], i.e.,

  
$$\\begin{array}{r} {\\kappa\_{N\_{k}} = \\frac{{\\hat{N}}\_{k}}{N\_{k}}.} \\\\ \\end{array}$$  
(7.74)

By the law of large numbers, for any (sufficiently small) *ϵ* > 0, *η* > 0 and the given value *ν*, there exists a number *N*[0](*ϵ*, *η*, *ν*) such that, for all *N*[*k*] > *N*[0](*ϵ*, *η*, *ν*), the deviation |*κ*[*N*[*k*]]−*ν*| is less than *ϵ* *ν* with a probability not smaller than (1 − *η*).

Thus, for *N*[*k*] > *N*[0](*ϵ*, *η*, *ν*), the inequality

  
$$\\begin{array}{r} {\\kappa\_{N\_{k}} \\geq (1 - \\epsilon)\\nu} \\\\ \\end{array}$$  
(7.75)

holds with a probability not smaller than (1 − *η*). Hence, the number *N̂*[*k*] of admissible vectors in a packet composed of *N*[*k*] vectors satisfies the inequality

  
$$\\begin{array}{r} {{\\hat{N}}\_{k} \\geq N\_{k}(1 - \\epsilon)\\nu} \\\\ \\end{array}$$  
(7.76)

with a probability not smaller than (1 − *η*).

Consequently, in all the formulas incorporating the number *N*[*k*] of generated vectors, we should replace it (for *N*[*k*] > *N*[0](⋅)) by the number *N̂*[*k*] = (1 − *ϵ*)*ν**N*[*k*].

Now let us estimate the number *N*[0](*ϵ*, *η*, *ν*). For *η* > 0, define a function *c*(*η*) using the condition

  
$$\\begin{array}{r} {\\frac{1}{\\sqrt{2\\pi}}{\\int\_{- c(\\eta)}^{c(\\eta)}\\exp}( - x^{2}/2)dx = 1 - \\eta.} \\\\ \\end{array}$$  
(7.77)

Then the number *N*[0](*ϵ*, *η*, *ν*) can be found from the relation

  
$$\\begin{array}{r} {N\_{0}(\\epsilon,\\eta,\\nu) \\geq \\frac{c^{2}(\\eta)(1 - \\nu)}{\\epsilon^{2}\\nu}.} \\\\ \\end{array}$$  
(7.78)

Second, consider the case in which the value *ν* is unknown but we know a value *ν*[0] such that 0 < *ν*[0] ≤ *ν*. Replacing *ν* by *ν*[0] in (7.78) yields an estimate for the minimum number of generated vectors under which the frequency of admissible vectors differs from the unknown value *ν* at most by *ϵ* *ν* with a probability not smaller than (1 − *η*). In this case, for *N* > *N*[0](*ϵ*, *η*, *ν*), the value *ν* can be estimated as

  
$$\\begin{array}{r} {\\hat{\\nu} = \\kappa\_{N},} \\\\ \\end{array}$$  
(7.79)

and, with a probability not smaller than (1 − *η*), |*κ*[*N*]−*ν*|≤*ϵ* *ν*, i.e.,

  
$$\\begin{array}{r} {\\frac{\\kappa\_{N}}{1 - \\epsilon} \\geq \\nu \\geq \\frac{\\kappa\_{N}}{1 + \\epsilon}.} \\\\ \\end{array}$$  
(7.80)

The lower bound from this estimate can be used instead of *ν* in formula (7.78).

### 7.2.7Logical structure of GFS algorithm

The GFS algorithm is intended for calculating a global minimum in the canonical form of the problem (7.23). It comprises two procedures, SeqLocMin and EstProb. The SeqLocMin procedure yields a sequence of records and their decrements and includes a stopping rule. The EstProb procedure estimates a minimum size for the neighborhood of the exact global minimum and also calculates a lower bound for the probability of getting into this neighborhood.

The procedures consist of a sequence of *k* steps, each performing *t* operations. Therefore, paired indexes (*k*, *t*) will be associated with the stages of each procedure.

**SeqLocMin procedure**

1.  *Generation*—creation of a packet of random vectors:
    
    1.  (*k*, 1) generate a sequence of *N*[*k*] independent random vectors with the uniform distribution on the unit cube;
        
    2.  (*k*, 2) form a packet 𝒵[*k*] = {**z**¹,…,**z**^(*N*[*k*])} of these random vectors.
        
2.  *Filtration*—choice of admissible vectors:
    
    1.  (*k*, 3) choose vectors from the packet 𝒵[*k*] that belong to the admissible set 𝒦[**z**] and form an admissible packet ${\\widetilde{\\mathcal{Z}}}\_{k}$ of size *Ñ*[*k*].
        
3.  *Selection*—definition of the quasi global minimum for the packet and calculation of the decrements:
    
    1.  (*k*, 4) calculate the values $F({\\widetilde{\\mathbf{z}}}^{i}),\\, i = \\overline{1,{\\widetilde{N}}\_{k}},$ of the objective function for the vectors from the packet ${\\widetilde{\\mathcal{Z}}}\_{k};$
        
    2.  (*k*, 5) choose the minimum value $F\_{k}^{\*} = \\min F({\\widetilde{\\mathbf{z}}}^{i}),\\, 1 \\leq i \\leq {\\widetilde{N}}\_{k};$
        
    3.  (*k*, 6) calculate the decrements *u*[*k*]\=|*F*[*k* + 1]^(\*)−*F*[*k*]^(\*)| and the decrement logarithms *v*[*k*] = log *u*[*k*] and *n*[*k*] = log *N*[*k*]; form the sequences 𝒰 = {*u*[*k*]}, 𝒱 = {*v*[*k*]}, 𝒩 = {*n*[*k*]}.
        

If *v*[*k*] ≤ log *δ*, the value *v*[*k*] is included in the sequence $\\widetilde{\\mathcal{V}}.$ As soon as the sequence ${\\overset{\\text{˜}}{\\mathcal{V}}}\_{k}$ accumulates *ρ* elements, *k* = *τ* and the algorithm stops. Then a transition to the EstProb procedure is performed.

**EstProb procedure**

The computational scheme of this procedure consists in the following.

1.  *Parameter estimation for the regression model of decrements*:
    
    1.  (*τ*, 1) using sequences 𝒩 and 𝒱, estimate parameters *Â*[*τ*] and *B̂*[*τ*] by the least-squares method.
        
2.  *Estimation of solution characteristics (quality indicators)*:
    
    1.  (*τ*, 2) estimate the size *r*[*τ*] (7.72) for the neighborhood of the global minimum value;
        
    2.  (*τ*, 3) calculate the lower bound for the probability *P̂*[*τ*] (7.73).
        

The logical structure of the GFS algorithm is presented in [Fig. 7.3](#chapter7.xhtml#f7_3).

![Figure 7.3](images/fig7_3.jpg)

[Figure 7.3](#chapter7.xhtml#f7_3b)

### 7.2.8Experimental study of GFS algorithm

According to the previous subsections, the probabilistic properties of the GFS algorithm established by analytical study possess an asymptotical character. In other words, they hold for a sufficiently large number of iterations. Even the estimates derived under a finite number of steps assume that it is great enough. The aim of an experimental study, which always has a finite number of steps, is to test the operability of this algorithm in typical problems. More specifically, we will check the estimates for the size of the exact global minimum neighborhood and the probability of getting into it. Recall that these estimates have been obtained using the least-squares-based estimation of the Hölder constants for the objective function. Therefore, in the course of a computational experiment, we will confirm or doubt the hypothesis about the linear regression in the log-log scale.

In the general statement, the GFS algorithm is intended for solving the global minimization problems in which it is possible to calculate the values of the associated functions (the objective function and constraints). Below we will consider the entropy estimation problem for the PDFs of the parameters of a randomized model that possesses these properties. Let us begin the experimental study of the GFS algorithm with test problems using analytical functions.

**1. Analytical tests**

Our testing employs some minimization problems from \[[4](#refbib.xhtml#r4), [5](#refbib.xhtml#r5), [58](#refbib.xhtml#r58), 173\], in which the admissible domain is the *d*\-dimensional parallelepiped *Π*[**z**].

*A1. The Shekel function*

  
$$\\begin{aligned} {F(\\mathbf{x}) =} & {- {\\sum\\limits\_{i = 1}^{m}\\left( {c\_{i} + {\\sum\\limits\_{j = 1}^{d}{(x\_{j} - a\_{ji})}^{2}}} \\right)^{- 1}},\\quad m = 10,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathbf{x}^{\*} = \\mathbf{4}.\\mathbf{0},} \\\\ & {\\text{\\quad\\quad}F^{\*} = - 10.5364,\\quad d = 4,} \\\\ & {\\text{\\quad\\quad}F^{\*} = - 11.0216,\\quad d = 2,} \\\\ \\end{aligned}$$  
(7.81)

where

  
$$\\begin{array}{r} {A = \\left( \\begin{array}{llllllllll} 4 & 1 & 8 & 6 & 3 & 2 & 5 & 8 & 6 & 7 \\\\ 4 & 1 & 8 & 6 & 7 & 9 & 3 & 1 & 2 & 3 \\\\ 4 & 1 & 8 & 6 & 3 & 2 & 5 & 8 & 6 & 7 \\\\ 4 & 1 & 8 & 6 & 7 & 9 & 3 & 1 & 2 & 3 \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

and

  
$$\\begin{array}{r} {c = \\frac{1}{10}(1,2,2,4,4,6,3,7,5,5).} \\\\ \\end{array}$$  

*A2. The Rosenbrock function*

  
$$\\begin{aligned} {F(\\mathbf{x})} & {= {\\sum\\limits\_{i = 1}^{d}1}00{(x\_{i + 1} - x\_{i})}^{2} + {(x\_{i} - 1)}^{2},} \\\\ & {\\mathbf{x}^{\*} = \\mathbf{1},\\, F^{\*} = 0\\,\\text{for~any}\\, d.} \\\\ \\end{aligned}$$  
(7.82)

*A3. The Powell function*

  
$$\\begin{aligned} {F(\\mathbf{x})} & {= {\\sum\\limits\_{i = 1}^{d - 2}{(x\_{i - 1} + 10x\_{i})}^{2}} + 5{(x\_{i + 1} - x\_{i + 2})}^{2} +} \\\\ & {+ {(x\_{i} - 2x\_{i + 1})}^{4} + 10{(x\_{i - 1} - x\_{i + 2})}^{4},} \\\\ & {\\text{\\quad\\quad}\\mathbf{x}^{\*} = \\mathbf{0},\\, F^{\*} = 0\\,\\text{for~any}\\, d.} \\\\ \\end{aligned}$$  
(7.83)

*A4. The trigonometric function*

  
$$\\begin{aligned} {F(\\mathbf{x})} & {= 1 + {\\sum\\limits\_{i = 1}^{d}8}\\sin^{2}7{(x\_{i} - 0.9)}^{2} + 6\\sin^{2}14{(x\_{i} - 0.9)}^{2} + x\_{i} - 0.9,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathbf{x}^{\*} = \\mathbf{0}.\\mathbf{9},\\, F^{\*} = 1\\,\\text{for~any}\\, d.} \\\\ \\end{aligned}$$  
(7.84)

*A5. The Griewank function*

  
$$\\begin{aligned} {F(\\mathbf{x})} & {= 1 + {\\sum\\limits\_{i = 1}^{d}\\frac{x\_{i}^{2}}{4000}} - {\\prod\\limits\_{i = 1}^{d}\\cos}\\left( \\frac{x\_{i}}{\\sqrt{i + 1}} \\right),} \\\\ & {\\mathbf{x}^{\*} = \\mathbf{0},\\, F^{\*} = 0\\,\\text{for~any}\\, d.} \\\\ \\end{aligned}$$  
(7.85)

For all computations, *N*[0] = 10, *α* = 10, *δ* = 0.01, *a* = 10, *ρ* = 2, *τ* = 13, and *ε*[*τ*]\=|*F*^(\*)−*F*[*τ*]^(\*)|. The results of computations are illustrated in [Table 7.1](#chapter7.xhtml#t7_1), where *t* denotes the solution time (in s), *r*[*τ*] and *P*[*τ*] give the estimated size of the exact global minimum neighborhood and the corresponding estimated probability, respectively. Clearly, the approximate solutions in all the tests belong to the estimated neighborhoods of the exact global minimum with a probability close to 1.

 [Table 7.1:](#chapter7.xhtml#t7_1b) Results of computations. 

 
|  |
| --- |
| Function || *Π*[**z**] || *F*[*τ*]^(\*) || **z**[*τ*]^(\*) || *ε*[*τ*] || *r̂*[*τ*] || *P̂*[*τ*] || *t*, s |
| A1 || \[0,10\] || \-11.0225 || 4.0031 || 0.0010 || 0.0265 ||  ≈ 1.0 || 1286 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| *d* = 2 ||  ||  || 3.9983 ||  ||  ||  ||  |
| A1 || \[0,10\] || \-10.1242 || 4.0475 || 0.4122 || 0.8810 ||  ≈ 1.0 || 2262 |
| *d* = 4 ||  ||  || 4.0160 ||  ||  ||  ||  |
|  ||  ||  || 4.0135 ||  ||  ||  ||  |
|  ||  ||  || 3.9590 ||  ||  ||  ||  |
| A2 || \[ − 10, 10\] || 0.000016 || 0.9966 || 0.000016 || 0.0221 ||  ≈ 1.0 || 2656 |
| *d* = 2 ||  ||  || 0.9930 ||  ||  ||  ||  |
| A2 || \[ − 0.5, 1.5\] || 0.0288 || 0.9852 || 0.0288 || 3.3406 ||  ≈ 1.0 || 3186 |
| *d* = 5 ||  ||  || 0.9843 ||  ||  ||  ||  |
|  ||  ||  || 0.9706 ||  ||  ||  ||  |
|  ||  ||  || 0.9357 ||  ||  ||  ||  |
|  ||  ||  || 0.8773 ||  ||  ||  ||  |
| A3 || \[ − 0.5, 0.5\] || 0.000013 || 0.0405 || 0.000013 || 0.0479 ||  ≈ 1.0 || 1715 |
| *d* = 4 ||  ||  || \-0.0043 ||  ||  ||  ||  |
|  ||  ||  || 0.0183 ||  ||  ||  ||  |
|  ||  ||  || 0.0181 ||  ||  ||  ||  |
| A4 || \[0,1\] || 1.0000 || 0.9000 || 2 ⋅ 10^( − 9) || 0.0000041 ||  ≈ 1.0 || 222 |
| *d* = 2 ||  ||  || 0.9000 ||  ||  ||  ||  |
| A4 || \[0,1\] || 1.0001 || 0.9002 || 0.0001 || 1.4970 ||  ≈ 1.0 || 599 |
| *d* = 5 ||  ||  || 0.8918 ||  ||  ||  ||  |
|  ||  ||  || 0.9007 ||  ||  ||  ||  |
|  ||  ||  || 0.8989 ||  ||  ||  ||  |
|  ||  ||  || 0.8923 ||  ||  ||  ||  |
| A5 || \[ − 5, 5\] || 0.0000 || \-0.0004 || 8 ⋅ 10^( − 8) || 0.00007 ||  ≈ 1.0 || 281 |
| *d* = 2 ||  ||  || 0.0000 ||  ||  ||  ||  |
| A5 || \[ − 5, 5\] || 0.0018 || \-0.0294 || 0.0018 || 0.2533 ||  ≈ 1.0 || 584 |
| *d* = 5 ||  ||  || \-0.0140 ||  ||  ||  ||  |
|  ||  ||  || \-0.0206 ||  ||  ||  ||  |
|  ||  ||  || \-0.0036 ||  ||  ||  ||  |
|  ||  ||  || \-0.1094 ||  ||  ||  ||  |
| A5 || \[ − 5, 5\] || 0.1245 || 3.0566 || 0.1245 || 0.1889 ||  ≈ 1.0 || 1594 |
| *d* = 10 ||  ||  || \-4.4010 ||  ||  ||  ||  |
|  ||  ||  || \-0.3254 ||  ||  ||  ||  |
|  ||  ||  || \-0.0586 ||  ||  ||  ||  |
|  ||  ||  || 0.2304 ||  ||  ||  ||  |
|  ||  ||  || 0.3659 ||  ||  ||  ||  |
|  ||  ||  || 0.1528 ||  ||  ||  ||  |
|  ||  ||  || \-0.9495 ||  ||  ||  ||  |
|  ||  ||  || 0.6693 ||  ||  ||  ||  |
|  ||  ||  || 0.1680 ||  ||  ||  ||  |
|  |

A feature of this algorithm consists in the estimation method for the Hölder constants based on the records sequence. The results of computations using this method can be observed in the graphs of [Fig. 7.5](#chapter7.xhtml#f7_5), including the sequences of the records *F*[*k*]^(\*) and the estimates of the Hölder constants *L̂* and *ŝ* that are yielded by approximating the decrements sequences.

![Figure 7.4](images/fig7_4.jpg)

Figure 7.4

![Figure 7.5](images/fig7_5.jpg)

[Figure 7.5](#chapter7.xhtml#f7_5b)

For this collection of tests, the GFS algorithm was implemented in C++ on hybrid architecture computers with NVIDIA accelerators. Our computing system consists of two nodes with CPUs Intel Xeon X5650 and E5-2650 and two accelerators Tesla M2050 and K20Xm.

**2. Algorithmic test (entropy-based estimation for PDFs of randomized model parameters \[149\])**

Consider an array of input and output data for some dynamic nonlinear object. Denote by **y** = {*y*\[*m*\],…,*y*\[*m*+*s*\]} the vector (packet) of output data and by **x**{*x*\[0\],…,*x*\[*m*\],…,*x*\[*m*+*s*\]} the vector (packet) of input data. Assume that the input measurements are perfect whereas the output measurements have errors that are simulated by a random vector $\\overline{\\xi} = \\left\\{ \\xi\\lbrack m\\rbrack,\\ldots,\\xi\\lbrack m + s\\rbrack \\right\\}$ with independent elements. Let the elements of this vector be of the interval type, i.e.,

  
$$\\begin{array}{r} {\\xi\\lbrack j + m\\rbrack \\in \\Xi\_{j} = \\lbrack\\xi\_{j}^{-},\\xi\_{j}^{+}\\rbrack,\\,\\,\\text{for~all}\\, j = \\overline{0,s}.} \\\\ \\end{array}$$  
(7.86)

In addition, there exist PDFs $q\_{j}(\\xi\\lbrack j + m\\rbrack),\\, j = \\overline{0,s},$ on these intervals.

The relation between the input and output packets is described by a discrete dynamic randomized model with second-order structured nonlinearities and an additive random noise of the form

  
$$\\begin{array}{r} {v\\lbrack j + 1\\rbrack = {\\sum\\limits\_{h = 1}^{R}\\left( {{\\sum\\limits\_{n = 0}^{m}w^{(h)}}\\lbrack n\\rbrack x\\lbrack j + m - n\\rbrack} \\right)^{h}} + \\xi\\lbrack j + m\\rbrack,\\quad j = \\overline{0,s},} \\\\ \\end{array}$$  
(7.87)

which has memory of capacity *m* = 1, *s* = 1 and *R* = 2.

The discrete random weight functions (random pulse characteristics) *w*^((1))\[*n*\] = *w*^((2))\[*n*\] = 0, *n* > 1, reflect the dynamic properties of the linear and nonlinear blocks of this model. Introduce the notations

  
$$\\begin{aligned} & {a\_{0}^{(1)} = w^{(1)}\\lbrack 0\\rbrack,\\, a\_{1}^{(1)} = w^{(1)}\\lbrack 1\\rbrack;\\quad\\mathbf{a}^{(1)} = \\left\\{ a\_{0}^{(1)},a\_{1}^{(1)} \\right\\};} \\\\ & {a\_{0}^{(2)} = w^{(2)}\\lbrack 0\\rbrack,\\, a\_{1}^{(2)} = w^{(2)}\\lbrack 1\\rbrack;\\quad\\mathbf{a}^{(2)} = \\left\\{ a\_{0}^{(2)},a\_{1}^{(2)} \\right\\};} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathbf{x}\\lbrack j\\rbrack = \\left\\{ x\\lbrack j + 1\\rbrack,x\\lbrack j\\rbrack \\right\\}.} \\\\ \\end{aligned}$$  
(7.88)

Choose **x**\[0\] = {0.39;0.19} and **x**\[1\] = {0.93;0.39}.

The random parameters *a*[*n*]^((*h*)) take their values within the intervals

  
$$\\begin{array}{r} {\\mathcal{A}\_{n}^{(h)} = \\lbrack - A\_{n}^{(h)},A\_{n}^{(h)}\\rbrack,\\quad A\_{n}^{(h)} = \\beta\_{n}^{(h)}\\exp( - \\alpha\_{n}^{(h)}\\, n).} \\\\ \\end{array}$$  
(7.89)

The parameters of the above-mentioned intervals are given in [Table 7.2](#chapter7.xhtml#t7_2).

 

[Table 7.2:](#chapter7.xhtml#t7_2b) Parameters of intervals.

 
|  |
| --- |
| Parameters || *α*[0]^((1)) || *α*[1]^((1)) || *β*[0]^((1)) || *β*[1]^((1)) |
| Values || 0.5 || 1.0 || 1.0 || 2.0 |
| --- | --- | --- | --- | --- |
|  |

The PDFs *P*^((1))(**a**^((1))) and *P*^((2))(**a**^((2))) are defined on the intervals (7.89).

According to the RML algorithm, the entropy-optimal PDFs of the model parameters and measurement noises have the form

  
$$\\begin{aligned} {{\\widetilde{P}}^{(h)}\\left( \\mathbf{a} \\right)} & {= \\frac{1}{\\mathcal{R}^{(h)}(\\theta)}\\,\\exp\\left( {- {\\sum\\limits\_{j = 0}^{s}\\,}\\theta\_{j}\\, V\_{j}^{(h)}\\left( {\\mathbf{a}^{(h)},\\mathbf{x}\\lbrack j\\rbrack} \\right)} \\right),\\quad h = \\overline{1,R};} \\\\ {{\\widetilde{q}}\_{j}(\\xi)} & {= \\frac{1}{\\mathcal{Q}\_{j}(\\theta\_{j})}\\,\\exp\\left( {- \\theta\_{j}\\,\\xi} \\right),\\, j = \\overline{0,s},} \\\\ \\end{aligned}$$  
(7.90)

where

  
$$\\begin{aligned} {\\mathcal{R}^{(h)}(\\mathbf{\\theta})} & {= {\\int\\limits\_{\\mathcal{A}^{(h)}}\\exp}\\left( {- {\\sum\\limits\_{j = 0}^{s}\\,}\\theta\_{j}\\, V\_{j}^{(h)}\\left( {\\mathbf{a}^{(h)},\\mathbf{x}\\lbrack j\\rbrack} \\right)} \\right)d\\mathbf{a}^{(h)},} \\\\ {\\mathcal{Q}\_{j}(\\theta)} & {= {\\int\\limits\_{\\Xi\_{j}}\\exp}\\left( {- \\theta\_{j}\\,\\xi\_{j}} \\right)d\\xi\_{j},\\quad j = \\overline{0,s},} \\\\ \\end{aligned}$$  
(7.91)

and

  
$$\\begin{aligned} {V\_{j}^{(1)}(\\mathbf{a},\\mathbf{x})} & {= a\_{0}^{(1)}x\\lbrack j + 1\\rbrack + a\_{1}^{(1)}x\\lbrack j\\rbrack,} \\\\ {V\_{j}^{(2)}(\\mathbf{a},\\mathbf{x}) =} & {\\left( {a^{(2)}x\\lbrack j + 1\\rbrack} \\right)^{2} + \\left( {a^{(2)}x\\lbrack j\\rbrack} \\right)^{2} +} \\\\ & {+ 2a\_{0}^{(2)}a\_{1}^{(2)}x\\lbrack j + 1\\rbrack x\\lbrack j\\rbrack.} \\\\ \\end{aligned}$$  
(7.92)

The Lagrange multipliers *θ*[0] and *θ*[1] are calculated by solving the system of equations

  
$$\\begin{array}{r} {\\Phi\_{j}(\\theta) = \\sum\\limits\_{h = 1}^{R}\\frac{{\\overset{\\text{˜}}{\\mathcal{R}}}\_{j}^{(h)}(\\theta)}{\\mathcal{R}^{(h)}(\\theta)} + \\frac{{\\overset{\\text{˜}}{\\mathcal{B}}}\_{j}(\\theta\_{j})}{\\mathcal{B}\_{j}(\\theta\_{j})} - y\\lbrack j + 1\\rbrack = 0,\\quad j = \\overline{0,s},} \\\\ \\end{array}$$  
(7.93)

where the integral components have the form

  
$$\\begin{aligned} {{\\overset{\\text{˜}}{\\mathcal{R}}}\_{j}^{(h)}(\\theta)} & {= \\int\\limits\_{\\mathcal{A}^{(h)}}V\_{j}^{(h)}\\left( {\\mathbf{a}^{(h)},\\mathbf{x}\\lbrack j\\rbrack} \\right)\\exp\\left( {- \\sum\\limits\_{i = 0}^{1}\\theta\_{i}V\_{i}^{(h)}\\left( {\\mathbf{a}^{(h)},\\mathbf{x}\\lbrack j\\rbrack} \\right)} \\right)d\\mathbf{a}^{(h)},} \\\\ {{\\overset{\\text{˜}}{\\mathcal{B}}}\_{j}(\\theta)} & {= \\int\\limits\_{\\Xi\_{j}}\\,\\xi\_{j}\\exp\\left( {- \\theta\_{j}\\,\\xi\_{j}} \\right)d\\xi\_{j}.} \\\\ \\end{aligned}$$  
(7.94)

The measured values of the object's output vector are *y*\[1\] = 0.5 and *y*\[2\] = 2.2.

For solving equations (7.93), minimize the residual function

  
$$\\begin{array}{r} {J(\\theta) = \\|\\Phi(\\theta)\\|\_{L\_{2}}} \\\\ \\end{array}$$  
(7.95)

on the cube *Π*[*θ*].

The results of computations are presented in [Table 7.3](#chapter7.xhtml#t7_3) and also illustrated in [Fig. 7.6](#chapter7.xhtml#f7_6). Due to the existing integral components (7.94), the objective function was defined algorithmically. For this collection of tests, the algorithm was implemented in MATLAB using Parallel Computing Toolbox. The integral components (7.94) were calculated by integral2 function whereas the minimum value by the GFS algorithm. All computations were performed with 32 working processors (often called workers) on the same computing system as in the case of analytical tests. The solution of equations (7.95) was obtained for the two search domains *Π*[*θ*]: *θ* ∈ \[ − 10, 10\] × \[ − 10, 10\] for Variant 1, and *θ* ∈ \[ − 3,  − 2\] × \[ − 0.5, 0.5\] for Variant 2; see [Table 7.3](#chapter7.xhtml#t7_3).

 

[Table 7.3:](#chapter7.xhtml#t7_3b) Results of computations.

 
|  |
| --- |
| Var || *J*[*τ*]^(\*) || *θ*[*τ*]^(\*) || *ε*[*τ*] || *r̂*[*τ*] || *P̂*[*τ*] || *t*, s |
| 1 || 0.0025 || \-2.4457\-0.0537 || 0.0025 || 0.1200 ||  ≈ 1.0 || 1576 |
| --- | --- | --- | --- | --- | --- | --- |
| 2 || 0.0001 || \-2.4042\-0.0634 || 0.0001 || 0.0051 ||  ≈ 1.0 || 1573 |
|  |

![Figure 7.6](images/fig7_6.jpg)

[Figure 7.6](#chapter7.xhtml#f7_6b)

## 7.3On Calculation of Multidimensional Integrals Using Monte Carlo Method

The equations of the Lagrange multipliers that are induced by the empirical balance constraints contain the integral components (7.13, 7.14) on the domains with unit volumes.

These integrals will be calculated using the Monte Carlo method with a random generator as follows. For each element of a vector **w** ∈ *I*^(*n*) ⊂ *R*^(*n*), it produces sequences of random numbers of length *M* to form *N* = *M*^(*n*) random vectors (points) $\\mathbf{w}^{(i)},\\, i = \\overline{1,N}.$ The details can be found in \[[147](#refbib.xhtml#r147)\].

A major difficulty of the Monte Carlo method is to estimate the length *M* of the sequence of random numbers (the number *N* of random points) that is sufficient for integrals calculation with a given error *δ*. Obviously, such an estimate has a random character and should be equipped with a corresponding probability.

For obtaining these estimates, two implementation strategies of the Monte Carlo method will be compared with one another. The first strategy involves a *uniform orthogonal lattice S* constructed in *I*^(*n*) from the uniform lattices 𝕊[*k*] for each element *w*[*k*] with the step

  
$$\\begin{array}{r} {h = \\frac{1}{M}.} \\\\ \\end{array}$$  
(7.96)

The elementary cubes in *I*^(*n*) have the same volumes

  
$$\\begin{array}{r} {v = h^{n} = \\left( \\frac{1}{M} \\right)^{n}.} \\\\ \\end{array}$$  
(7.97)

Then equalities (7.13, 7.14) can be written as

  
$$\\begin{aligned} {\\widetilde{\\mathbb{B}}(\\mathbf{z})} & {\\approx v{\\sum\\limits\_{i = 1}^{N}\\phi}(\\mathbf{w}^{i},\\mathbf{z}),} \\\\ {\\widetilde{\\mathbb{G}}(\\mathbf{z})} & {\\approx v{\\sum\\limits\_{i = 1}^{N}\\varphi}(\\mathbf{w}^{i},\\mathbf{z}),} \\\\ \\end{aligned}$$  
(7.98)

where

  
$$\\begin{aligned} {\\phi(\\mathbf{w}^{i},\\mathbf{z})} & {= \\exp\\left( {- E(\\mathbf{z},\\mathbf{w}^{(i)})} \\right),} \\\\ {\\varphi(\\mathbf{w}^{i},\\mathbf{z})} & {= E(\\mathbf{z},\\mathbf{w}^{(i)})\\exp\\left( {- E(\\mathbf{z},\\mathbf{w}^{(i)})} \\right).} \\\\ \\end{aligned}$$  
(7.99)

The second strategy is based on a *nonuniform (random) orthogonal lattice $\\hat{\\mathbb{S}}$* constructed from the product of nonuniform (random) lattices ${\\hat{\\mathbb{S}}}\_{k}$ for each *k*th element of the vector **w**. In contrast to the uniform lattice, the step of the nonuniform one makes up

  
$$\\begin{array}{r} {h\_{k}^{(i)} = w\_{k}^{(i + 1)} - w\_{k}^{(i)},} \\\\ \\end{array}$$  
(7.100)

thereby representing a *random variable*. The elementary cubes in the lattice $\\hat{\\mathbb{S}}$ have *random* volumes *v*^((1)), …, *v*^((*N*)), i.e.,

  
$$\\begin{array}{r} {v^{(i)} = {\\prod\\limits\_{k = 1}^{n}h\_{k}^{(i)}},\\text{\\quad\\quad}i = \\overline{1,N}.} \\\\ \\end{array}$$  
(7.101)

According to the mean value theorem, the *exact* values of the integrals on the nonuniform lattice (7.100, 7.101) are given by

  
$$\\begin{array}{r} {\\mathbb{B}(\\mathbf{z}) = {\\sum\\limits\_{i = 1}^{N}v^{(i)}}\\phi(\\zeta^{(i)},\\mathbf{z}),} \\\\ {\\mathbb{G}(\\mathbf{z}) = {\\sum\\limits\_{i = 1}^{N}v^{(i)}}\\varphi(\\xi^{(i)},\\mathbf{z}),} \\\\ \\end{array}$$  
(7.102)

where *ζ*^((*i*)) and *ξ*^((*i*)) denote the mean points of the elementary cubes of the lattice $\\hat{\\mathbb{S}}$ for the integrals (7.13) and (7.14), respectively.

Define the error between the exact (7.102) and approximate (7.98) values of these integrals as

  
$$\\begin{aligned} \\left| \\mathbb{B}(\\mathbf{z}) - \\widetilde{\\mathbb{B}}(\\mathbf{z}) \\right| & \\left. = \\middle| \\sum\_{i = 1}^{N}v^{(i)}\\phi(\\zeta^{(i)},\\mathbf{z}) - v\\sum\_{i = 1}^{N}\\phi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| \\leq \\right. \\\\ & \\left. \\leq \\sum\_{i = 1}^{N} \\middle| v^{(i)} - v \\middle| \\middle| \\phi(\\zeta^{(i)},\\mathbf{z} \\middle| + \\right. \\\\ {v\\sum\_{i = 1}^{N}} & \\left| \\phi(\\zeta^{(i)},\\mathbf{z}) - \\phi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| = \\epsilon(N), \\right. \\\\ \\end{aligned}$$  
(7.103)

and

  
$$\\begin{aligned} \\left| \\mathbb{G}(\\mathbf{z}) - \\widetilde{\\mathbb{G}}(\\mathbf{z}) \\right| & \\left. = \\middle| \\sum\_{i = 1}^{N}v^{(i)}\\varphi(\\zeta^{(i)},\\mathbf{z}) - v\\sum\_{i = 1}^{N}\\varphi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| \\leq \\right. \\\\ & \\left. \\leq \\sum\_{i = 1}^{N} \\middle| v^{(i)} - v \\middle| \\middle| \\varphi(\\zeta^{(i)},\\mathbf{z}) \\middle| + \\right. \\\\ {v\\sum\_{i = 1}^{N}} & \\left| \\varphi(\\zeta^{(i)},\\mathbf{z}) - \\varphi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| = \\kappa(N). \\right. \\\\ \\end{aligned}$$  
(7.104)

First, let us derive upper bounds *ϵ̃*(*N*, *n*) and *κ̃*(*N*, *n*) for *ϵ*(*N*) and *κ*(*N*), and then solve the inequalities

  
*ϵ*(*N*) ≤ *ϵ̃*(*N*) ≤ *δ*,  *κ*(*N*) ≤ *κ̃*(*N*) ≤ *δ*.  
(7.105)

Here *δ* is a given error. We should bear in mind that *ϵ*(*N*) and *κ*(*N*) are random variables. Therefore, inequalities (7.105) may hold with some probability only.

**1.** Consider inequality (7.3) and estimate the first term:

  
$$\\begin{array}{r} \\left. \\left. \\sum\\limits\_{i = 1}^{N} \\right|v^{(i)} - v \\middle| \\middle| \\phi(\\zeta^{(i)},\\mathbf{z}) \\middle| \\leq \\max\_{\\zeta \\in I^{n}} \\middle| \\phi(\\zeta,\\mathbf{z}) \\middle| \\left. \\sum\\limits\_{i = 1}^{N} \\right|v^{(i)} - v \\middle| . \\right. \\\\ \\end{array}$$  
(7.106)

By the definition of the function *ϕ*(**w**, **z**), under fixed **z** (7.98) write

  
$$\\begin{array}{r} \\left| \\phi(\\mathbf{w},\\mathbf{z}) \\middle| \\leq \\max\_{\\mathbf{w} \\in I^{n}}\\exp( \\middle| E(\\mathbf{w},\\mathbf{z}) \\middle| ) \\leq \\exp(G), \\right. \\\\ \\end{array}$$  
(7.107)

where

  
$$\\begin{array}{r} \\left. G = {({\\sum\\limits\_{t = 1}^{T}A^{(t)}})}^{2},\\text{\\quad\\quad}A^{(t)} = \\max\\left. \\sum\\limits\_{(n\_{1},\\ldots,n\_{t}) = 1}^{n} \\right|A\_{n\_{1},\\ldots,n\_{t}} \\middle| . \\right. \\\\ \\end{array}$$  
(7.108)

Next, estimate the difference between the random elementary volume *v*^((*i*)) (7.101) and the elementary volume *v* of the uniform lattice.

  
$$\\begin{array}{r} \\left| v^{i} - v \\middle| = \\middle| {\\prod\\limits\_{k = 1}^{n}h\_{k}^{i}} - h^{n} \\middle| \\leq h^{(n - 1)}\\,\\max\_{i} \\middle| h\_{k}^{i} - h \\middle| . \\right. \\\\ \\end{array}$$  
(7.109)

Note that the variable *h*[*k*]^(*i*) is random. Consider the event

  
$$\\begin{array}{r} {\\mathcal{V}^{k} = \\left\\{ \\max\_{i} \\middle| h\_{k}^{i} - h \\middle| < \\gamma \\right\\},} \\\\ \\end{array}$$  
(7.110)

and also the union of the events 𝒱[1], ..., 𝒱[*m*],

  
$$\\begin{array}{r} {\\mathcal{V} = {\\underset{k = 1}{\\overset{n}{\\cup}}\\mathcal{V}^{k}}.} \\\\ \\end{array}$$  
(7.111)

Here *γ* specifies a small positive value. A lower bound for the probability of the event 𝒱 will be established below.

Choosing *γ* = *h*², write

  
$$\\begin{array}{r} \\left. \\max\_{i} \\middle| v^{i} - v \\middle| \\leq h^{(m - 1)}\\gamma = h^{(m + 1)}. \\right. \\\\ \\end{array}$$  
(7.112)

Thus, by (7.106–7.108) the inequality

  
$$\\begin{array}{r} \\left| {\\sum\\limits\_{i = 1}^{N}{(v\_{i} - v)}}\\phi(\\zeta^{i},\\mathbf{z}) \\middle| \\leq N\\left( \\frac{l}{N} \\right)^{n + 1}\\,\\exp(G). \\right. \\\\ \\end{array}$$  
(7.113)

holds with the probability of the event (7.111).

**2.** Find a lower bound for the probability of the event (7.111). Consider the difference |*h*[*k*]^((*i*))−*h*| and take a small positive value *γ* such that |*h*[*k*]^((*i*))−*h*|>*γ* for all steps *h*[*k*]^((*i*)) of the random lattice $\\hat{\\mathbb{S}}.$ Calculate the probability of this event. If the number of random points is large (small *h*) and they have a uniform spread, then the distance between these points must be close to *h*.

The event max[*i*]|*h*[*k*]^((*i*))−*h*|>*γ* means that it is possible to find a pair of random variables (*ξ*, *η*) ∈ \[0, 1\] with the following property: if one of them (e.g., *ξ*) takes a value *y* ∈ \[0, 1\], then the other *η* ≠ ℒ = \[*y* + *h* − *γ*, *y* + *h* + *γ*\]. Hence, the interval ℒ of length 2*γ* that has center at the point *y* + *h* is empty. Actually, assume the random variable *η* gets into the interval ℒ, i.e., *η* = *ξ* − *h* ± *δ*, where 0 < *δ* < *γ*; in this case, it follows that |*h*[*k*]^((*i*))−*h*|<*γ*.

Due to the independence of the uniformly distributed random variables, the probability of the event max[*i*]|*h*[*k*]^((*i*))−*h*|>*γ* is the same for all elements of the vector **a** and does not exceed \[1 − 2*γ* + *ψ*(*N*)\]^(*N*), where *ψ*(*N*) gives an empirical probability correction for a specific random generator, which is found experimentally. An analysis of the standard random generators indicates that the function *ψ*(*N*) almost vanishes starting from *N* = 1000. Therefore,

  
$$\\begin{array}{r} \\left. \\widetilde{P}(\\max\_{i} \\middle| h\_{k}^{(i)} - h \\middle| > \\gamma) = \\widetilde{P}(\\mathcal{V}^{k}) = {(1 - 2\\gamma)}^{N}. \\right. \\\\ \\end{array}$$  
(7.114)

The probability of the event 𝒱 (7.111) has the form

  
$$\\begin{array}{r} {\\widetilde{P}(\\mathcal{V}) = \\widetilde{P}(N,n) = {(1 - 2\\gamma)}^{Nn}.} \\\\ \\end{array}$$  
(7.115)

The probability of the opposite event $\\underset{k = 1}{\\overset{m}{\\cup}}\\left. (\\max\_{i} \\middle| h\_{k}^{(i)} - h \\middle| < \\gamma) \\right.$ makes up

  
$$\\begin{array}{r} {P(\\mathcal{V}) = 1 - {(1 - 2\\gamma)}^{Nn}.} \\\\ \\end{array}$$  
(7.116)

Choosing *γ* = *h*², from (7.116) we establish that the probability of the event (7.111) is

  
$$\\begin{array}{r} {P(\\mathcal{V}) > 1 - ({\\lbrack - 2\\left( \\frac{l}{N} \\right)^{2}\\rbrack}^{Nn}) = P(N,n).} \\\\ \\end{array}$$  
(7.117)

Consequently, inequality (7.113) holds with a probability not smaller than *P*(*N*, *m*).

**3.** Consider the second term in (7.3). The following estimate is valid:

  
$$\\begin{array}{r} \\left. v\\left. \\sum\\limits\_{i = 1}^{N} \\right|\\phi(\\zeta^{i},\\mathbf{z}) - \\phi(\\mathbf{w}^{i},\\mathbf{z}) \\middle| \\leq \\left( \\frac{1}{N} \\right)^{n}\\,\\max\_{(\\zeta,\\mathbf{w}) \\in I^{n}} \\middle| \\phi(\\zeta,\\mathbf{z}) - \\phi(\\mathbf{w},\\mathbf{z}) \\middle| . \\right. \\\\ \\end{array}$$  
(7.118)

The expression under the summation sign defines the modulus of continuity of the function *ϕ*(**w**, **z**); see \[[61](#refbib.xhtml#r61)\]. Since this function is differentiable,

  
$$\\begin{array}{r} \\left. \\max\_{(\\zeta,\\mathbf{w}) \\in I^{n}} \\middle| \\phi(\\zeta,\\mathbf{z}) - \\phi(\\mathbf{w},\\mathbf{z}) \\middle| \\leq \\max\_{\\mathbf{w} \\in I^{n};\\mspace{2mu} k \\in \\lbrack 1,n\\rbrack} \\middle| \\frac{\\partial\\phi(\\mathbf{w},\\mathbf{z})}{\\partial w\_{k}} \\middle| \\,\\max\_{(\\zeta,\\mathbf{w}) \\in I^{n}}\\|\\zeta - \\mathbf{w}\\|. \\right. \\\\ \\end{array}$$  
(7.119)

The distance between any random point and its nearest neighbors does not exceed the diagonal of the elementary cube, i.e.,

  
$$\\begin{aligned} {\\max\_{(\\zeta^{i},\\mathbf{w}^{i}) \\in I^{n};i \\in \\lbrack 1,N\\rbrack}\\|\\zeta^{i} - \\mathbf{w}^{i}\\|} & {\\leq \\sqrt{\\sum\\limits\_{k = 1}^{n}{(\\zeta\_{k}^{i} - w\_{k}^{i})}^{2}} \\leq \\sqrt{n}\\max\_{k}\\delta\_{k}^{i},} \\\\ & {\\delta\_{k}^{i} = \\zeta\_{k}^{i} - w\_{k}^{i}.} \\\\ \\end{aligned}$$  
(7.120)

Take a sufficiently small positive value *γ*. According to (7.100) and the definition of *ζ*^(*i*) as the mean point of the elementary cube of the nonuniform random lattice, consider the chain of inequalities

  
$$\\begin{array}{r} {\\max\_{k}\\delta\_{k}^{i} < \\max\_{k}h\_{k}^{i} < \\gamma.} \\\\ \\end{array}$$  
(7.121)

Let *γ* = *h*², where *h* is the step of the uniform lattice. The latter inequality holds with the probability *P*(*N*) (7.117).

Estimate the value

  
$$\\begin{array}{r} {\\frac{\\partial\\phi}{\\partial w\_{k}} = - E(\\mathbf{w},\\mathbf{z})\\exp( - E(\\mathbf{w},\\mathbf{z}))\\frac{\\partial E}{\\partial w\_{k}},} \\\\ \\end{array}$$  
(7.122)

where

  
$$\\begin{array}{r} {\\frac{\\partial E}{\\partial w\_{k}} = {\\sum\\limits\_{t = 1}^{T}{\\sum\\limits\_{(n\_{1},\\ldots,n\_{t}) = 1}^{n}A\_{(n\_{1},\\ldots,n\_{t})}}}(\\mathbf{z}){\\prod\\limits\_{r = 1,n\_{r} \\neq k}^{t}x\_{n\_{r}}}.} \\\\ \\end{array}$$  
(7.123)

Using (7.106–7.108), write

  
$$\\begin{array}{r} \\left. \\max\_{\\mathbf{w} \\in I^{n}}\\max\_{k} \\middle| \\frac{\\partial\\phi}{\\partial w\_{k}} \\middle| \\leq G^{2}\\exp(G). \\right. \\\\ \\end{array}$$  
(7.124)

Then the estimate (7.119) takes the form

  
$$\\begin{array}{r} \\left. \\max\_{(\\zeta,\\mathbf{w}) \\in I^{n}} \\middle| \\phi(\\zeta,\\mathbf{z}) - \\phi(\\mathbf{w},\\mathbf{z}) \\middle| \\leq \\sqrt{m}\\left( \\frac{l}{N} \\right)^{2 + n}G^{2}\\exp(G) = \\frac{n}{N}\\sqrt{n}G^{2}\\exp(G). \\right. \\\\ \\end{array}$$  
(7.125)

Substitute (7.107) and (7.119) into (7.3) to establish that the inequality

  
$$\\begin{array}{r} \\left| \\mathbb{B}(\\mathbf{z}) - \\widetilde{\\mathbb{B}}(\\mathbf{z}) \\middle| \\leq N\\exp(G)\\left( \\frac{l}{N} \\right)^{m}\\left\\lbrack {1 + \\sqrt{m}\\left( \\frac{l}{N} \\right)^{2}G^{2}} \\right\\rbrack = \\widetilde{\\epsilon}(N,m) \\right. \\\\ \\end{array}$$  
(7.126)

holds with a probability not smaller than *P*(*N*, *m*) (7.117).

**4.** Now switch to inequalities (7.3). They are structurally similar to inequalities (7.3), and the only difference consists in the function *φ*(**w**, **z**) (7.98). Hence,

  
$$\\begin{array}{r} \\left. \\left. \\sum\\limits\_{i = 1}^{N} \\right|v^{i} - v \\middle| \\middle| \\varphi(\\zeta,\\mathbf{z}) \\middle| \\leq \\max\_{\\zeta \\in I^{n}} \\middle| \\varphi(\\zeta,\\mathbf{z}) \\middle| \\left. \\sum\\limits\_{i = 1}^{N} \\right|v^{i} - v \\middle| \\leq N\\left( \\frac{l}{N} \\right)^{n + 1}\\max\_{\\zeta \\in I^{n}} \\middle| \\varphi(\\zeta,\\mathbf{z}) \\middle| . \\right. \\\\ \\end{array}$$  
(7.127)

By the definition of the function *φ*(**a**, **z**) (7.98),

  
$$\\begin{array}{r} \\left. \\max\_{\\zeta \\in I^{n}} \\middle| \\varphi(\\zeta,\\mathbf{z}) \\middle| \\leq \\max\_{\\mathbf{w} \\in I^{n}} \\middle| E(\\mathbf{w},\\mathbf{z}) \\middle| \\exp(E(\\mathbf{w},\\mathbf{z})) = G\\exp(G), \\right. \\\\ \\end{array}$$  
(7.128)

where *G* is given by equalities (7.108). For the second term in (7.3), the estimate takes the form

  
$$\\begin{array}{r} \\left. \\max\_{(\\zeta,\\mathbf{w})} \\middle| \\varphi(\\zeta,\\mathbf{z}) - \\varphi(\\mathbf{w},\\mathbf{z}) \\middle| \\leq \\max\_{\\mathbf{w} \\in I^{n},\\mspace{2mu} k \\in \\lbrack 1,n\\rbrack}\\, \\middle| \\frac{\\partial\\varphi}{\\partial w\_{k}} \\middle| \\max\_{(\\zeta,\\mathbf{w}) \\in I^{n}}\\|\\zeta - \\mathbf{w}\\|. \\right. \\\\ \\end{array}$$  
(7.129)

According to the definition of the function *φ*(**w**, **z**) (7.98), also write

  
$$\\begin{array}{r} {\\frac{\\partial\\varphi}{\\partial w\_{k}} = \\frac{\\partial E(\\mathbf{w},\\mathbf{z})}{\\partial w\_{k}}\\exp( - E(\\mathbf{w},\\mathbf{z}))(1 - E^{2}(\\mathbf{w},\\mathbf{z})),} \\\\ \\end{array}$$  
(7.130)

which yields the estimate

  
$$\\begin{array}{r} \\left. \\max\_{\\mathbf{w} \\in I^{n},\\mspace{2mu} k \\in \\lbrack 1,n\\rbrack}\\, \\middle| \\frac{\\partial\\varphi}{\\partial w\_{k}} \\middle| \\leq G(1 + G^{2})\\,\\exp(G). \\right. \\\\ \\end{array}$$  
(7.131)

Thus, the inequality

  
$$\\begin{array}{r} \\left| \\mathbb{G}(\\mathbf{z}) - \\widetilde{\\mathbb{G}}(\\mathbf{z}) \\middle| \\leq N\\left( \\frac{l}{N} \\right)^{n + 1}G\\exp(G)\\left\\lbrack {1 + \\frac{l}{N}(1 + G^{2})} \\right\\rbrack = \\widetilde{\\kappa}(N,n) \\right. \\\\ \\end{array}$$  
(7.132)

takes place with a probability not smaller than *P*(*N*, *m*) (7.117).

An upper bound for the value *N* (or *M*) can be calculated from the condition

  
$$\\begin{array}{r} {N^{\*} = \\max(\\widetilde{\\epsilon}(N,n) = \\delta;\\,\\,\\widetilde{\\kappa}(N,n) = \\delta).} \\\\ \\end{array}$$  
(7.133)

## 7.4Multiplicative Algorithms with *p*\-Active Variables

Many problems arising in RML and ML procedures are reduced to systems of nonlinear equations, e.g., the balance equations (7.9–7.12). Let us illustrate a method for solving such equations that are associated with the entropy maximization problems on polyhedrons \[140\].

Consider a system of equalities that are interpreted as the balance constraints between data **q** ∈ *R*^(*r*) and an output **y** ∈ *R*^(*n*) of some linear parametric model:

  
$$\\begin{array}{r} {T\\mathbf{y} = \\mathbf{q},\\quad(T,\\mathbf{y}) \\geq 0,\\,\\,\\mathbf{q} \\geq \\varepsilon > 0,\\text{\\quad\\quad}r < n.} \\\\ \\end{array}$$  
(7.134)

Here *T* denotes a matrix of full rank *r*. For the system (7.134), there exists a set of solutions and a unique solution among them that maximizes the entropy

  
$$\\begin{array}{r} {H(\\mathbf{y}) = - {\\sum\\limits\_{i = 1}^{n}y\_{i}}\\ln\\frac{y\_{i}}{ea\_{i}},\\text{\\quad\\quad}e = 2.71,} \\\\ \\end{array}$$  
(7.135)

with *a*[1], …, *a*[*n*] acting as parameters.

Consider the following constrained optimization problem for the entropy (7.135):

  
$$\\begin{aligned} & \\left. H(\\mathbf{y})\\Rightarrow\\max, \\right. \\\\ & {T\\,\\mathbf{y} = \\mathbf{q}.} \\\\ \\end{aligned}$$  
(7.136)

The corresponding Lagrange function has the form

  
$$\\begin{array}{r} {L(\\mathbf{y},\\overline{\\lambda}) = H(\\mathbf{y}) + {\\sum\\limits\_{k = 1}^{r}\\lambda\_{k}}\\left( {q\_{k} - {\\sum\\limits\_{i = 1}^{n}t\_{ki}}y\_{i}} \\right).} \\\\ \\end{array}$$  
(7.137)

The first-order optimality conditions are given by

  
$$\\begin{aligned} {\\nabla\_{y\_{i}}L(\\mathbf{y},\\overline{\\lambda})} & {= \\frac{\\partial H(\\mathbf{y})}{\\partial y\_{i}} - {\\sum\\limits\_{k = 1}^{r}\\lambda\_{k}}t\_{ki} = 0,\\quad i = \\overline{1,n};} \\\\ {\\nabla\_{\\lambda\_{k}}L(\\mathbf{y},\\overline{\\lambda})} & {= q\_{k} - {\\sum\\limits\_{i = 1}^{n}t\_{ki}}y\_{i} = 0,\\quad k = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(7.138)

The first group of equations yields a relation between the variables **y** and the Lagrange multipliers $\\overline{\\lambda}$ in the form

  
$$\\begin{array}{r} {y\_{i}(\\overline{\\lambda}) = \\frac{a\_{i}}{{\\sum\\limits\_{k = 1}^{r}\\exp}(t\_{k}i\\lambda\_{k})},\\text{\\quad\\quad}i = \\overline{1,n}.} \\\\ \\end{array}$$  
(7.139)

This relation allows us to eliminate the primal variables **y** from the definition of the Lagrange function (7.137), leading to the following expression for the dual function (which depends on the dual variables—the Lagrange multipliers):

  
$$\\begin{array}{r} {\\widetilde{L}(\\overline{\\lambda}) = L\\lbrack\\mathbf{y}(\\overline{\\lambda}),\\overline{\\lambda}\\rbrack.} \\\\ \\end{array}$$  
(7.140)

The elements of its gradient are

  
$$\\begin{array}{r} {\\nabla\_{\\lambda\_{k}}\\widetilde{L}(\\overline{\\lambda}) = q\_{k} - {\\sum\\limits\_{i = 1}^{n}y\_{i}}(\\overline{\\lambda}),\\text{\\quad\\quad}k = \\overline{1,r}.} \\\\ \\end{array}$$  
(7.141)

In terms of the dual function, the second group of the optimality conditions (7.138) can be written as

  
$$\\begin{array}{r} {\\nabla\_{\\lambda\_{k}}\\widetilde{L}(\\overline{\\lambda}) = 0,\\text{\\quad\\quad}k = \\overline{1,r}.} \\\\ \\end{array}$$  
(7.142)

Hence, the balance constraints take the form

  
$$\\begin{array}{r} {{\\widetilde{B}}\_{k}(\\overline{\\lambda}) = \\frac{1}{q\_{k}}{\\sum\\limits\_{i = 1}^{n}t\_{ki}}\\frac{a\_{i}}{{\\sum\\limits\_{j = 1}^{r}\\exp}\\left( {\\lambda\_{j}t\_{ji}} \\right)} = 1,\\quad\\overline{\\lambda} \\in R^{r},\\text{\\quad\\quad}k = \\overline{1,r}.} \\\\ \\end{array}$$  
(7.143)

Often it seems convenient to transform these equations using the nonnegative variables $z\_{k} = \\exp(\\lambda\_{k}),\\, k = \\overline{1,r},$ known as the exponential Lagrange multipliers. Then equations (7.143) are reduced to

  
$$\\begin{array}{r} {B\_{k}(\\mathbf{z}) = \\frac{1}{q\_{k}}{\\sum\\limits\_{i = 1}^{n}t\_{ki}}a\_{i}\\left( {\\prod\\limits\_{j = 1}^{r}z\_{k}^{- t\_{ji}}} \\right) = 1,\\quad\\mathbf{z} \\in R\_{+}^{r},\\text{\\quad\\quad}k = \\overline{1,r}.} \\\\ \\end{array}$$  
(7.144)

Now, for the dual function (7.140), the Hessian matrix has the form

  
$$\\begin{array}{r} \\left. \\Gamma(\\overline{\\lambda}) = \\lbrack\\nabla\_{\\lambda\_{j},\\lambda\_{l}}\\widetilde{L}(\\overline{\\lambda})\\, \\middle| \\,(j,l) = \\overline{1,r}\\rbrack, \\right. \\\\ \\end{array}$$  
(7.145)

where

  
$$\\begin{array}{r} {\\nabla\_{\\lambda\_{j},\\lambda\_{l}}\\widetilde{L}(\\overline{\\lambda}) = - {\\sum\\limits\_{i = 1}^{n}t\_{kj}}\\frac{\\partial y\_{j}}{\\partial\\lambda\_{l}}.} \\\\ \\end{array}$$  
(7.146)

The primal variables expression (7.139) implies the inequality

  
$$\\begin{array}{r} {\\frac{\\partial y\_{j}}{\\partial\\lambda\_{l}} \\leq 0,} \\\\ \\end{array}$$  
(7.147)

holding for all *λ* ∈ *R*^(*r*). Therefore, the Hessian matrix (7.143) consists of nonnegative elements. Taking into account (7.145), the quadratic form $K = \\left\\langle \\Gamma\\overline{\\lambda},\\,\\overline{\\lambda} \\right\\rangle$ is strictly positive definite for any $\\overline{\\lambda} \\in R^{r}.$ This means that the dual function *L̃* is strictly convex. The system of equations 7.143 guarantees boundedness of its solution, i.e., there exists a constant *c* > 0 such that $\\left| \\overline{\\lambda} \\middle| \\leq c < \\infty. \\right.$ Consequently, *L̃* ≥ *L*[min].

For solving equations (7.138), utilize the multiplicative algorithm with *p*\-active variables as follows.

*Initial step:*

  
$$\\begin{array}{r} {\\mathbf{z}^{0} > \\mathbf{0}.} \\\\ \\end{array}$$  

*Iterative step:*

  
$$\\begin{aligned} z\_{k\_{1}(s)}^{(s + 1)} & {= z\_{k\_{1}(s)}^{s}B\_{k\_{1}(s)}^{\\gamma}(\\mathbf{z}^{s}),} \\\\ \\cdots & {= \\cdots\\cdots\\cdots,} \\\\ z\_{k\_{p}(s)}^{(s + 1)} & {= z\_{k\_{p}(s)}^{s}B\_{k\_{p}(s)}^{\\gamma}(\\mathbf{z}^{s})} \\\\ z\_{k}^{(s + 1)} & {= z\_{k}^{s},\\quad k \\neq k\_{1}(s),\\ldots,k\_{p}(s),} \\\\ & {(k,k\_{1}(s),\\ldots,k\_{p}(s)) \\in \\overline{1,n}.} \\\\ \\end{aligned}$$  
(7.148)

Further analysis will need an additive form of the algorithm (7.148) in the variables *λ*[*k*] = ln *z*[*k*]. This form is written in the following way.

*Initial step:*

  
$$\\begin{array}{r} {{\\overline{\\lambda}}^{0} \\in R^{n}.} \\\\ \\end{array}$$  

*Iterative step:*

  
$$\\begin{aligned} \\lambda\_{k\_{1}(s)}^{(s + 1)} & {= \\lambda\_{k\_{1}(s)}^{s} + \\gamma\\ln{\\widetilde{B}}\_{k\_{1}(s)}({\\overline{\\lambda}}^{s}),} \\\\ \\cdots & {= \\cdots\\cdots\\cdots,} \\\\ \\lambda\_{k\_{p}(s)}^{(s + 1)} & {= \\lambda\_{k\_{p}(s)}^{s} + \\gamma\\ln{\\widetilde{B}}\_{k\_{p}(s)}({\\overline{\\lambda}}^{s})} \\\\ \\lambda\_{k}^{(s + 1)} & {= \\lambda\_{k}^{s},\\quad k \\neq k\_{1}(s),\\ldots,k\_{p}(s),} \\\\ & {(k,k\_{1}(s),\\ldots,k\_{p}(s)) \\in \\overline{1,n},} \\\\ \\end{aligned}$$  
(7.149)

where ${\\widetilde{B}}\_{k}(\\overline{\\lambda}) = B\_{k}(\\exp(\\overline{\\lambda})),\\, k = \\overline{1,r}.$

A major difficulty for such algorithms is to select active variables. This selection can be organized by a cyclical rule, e.g., for *p* = 1,

  
$$\\begin{array}{r} {k\_{1}(s) = s(\\text{mod}\\, n + 1).} \\\\ \\end{array}$$  
(7.150)

A more efficient approach involves residual feedback, i.e.,

  
$$\\begin{array}{r} \\left. \\vartheta\_{k}(\\mathbf{z}^{s}) = \\middle| 1 - B\_{k}(\\mathbf{z}^{s}) \\middle| ,\\text{\\quad\\quad}k = \\overline{1,n}. \\right. \\\\ \\end{array}$$  
(7.151)

Introduce the following notations:

  
$$\\begin{aligned} \\frac{r}{p} & {= I + \\delta,\\text{\\quad\\quad}\\rho = s\\lbrack\\text{(}mod)\\,(I + 1)\\rbrack,} \\\\ I & {= \\left\\lbrack \\frac{r}{p} \\right\\rbrack,\\text{\\quad\\quad}0 \\leq \\delta \\leq p - 1.} \\\\ \\end{aligned}$$  
(7.152)

Here \[ ⋅ \] indicates the integer part of value  ⋅ . Consider the index sets

  
$$\\begin{array}{r} {K = \\left\\{ 1,\\ldots,r \\right\\},\\text{\\quad\\quad}K\_{m}(s) = \\left\\{ k\_{1}(s),\\ldots,k\_{m}(s) \\right\\},} \\\\ \\end{array}$$  
(7.153)

where

  
$$\\begin{array}{r} {m = \\left\\{ \\begin{array}{r} {1,\\ldots,p\\text{if}\\,\\rho < I;} \\\\ {1,\\ldots,\\delta\\text{if}\\,\\rho = I.} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
(7.154)

Let

  
$$\\begin{aligned} {P\_{m - 1}(s)} & {= \\left\\lbrack {{\\underset{v = 1}{\\overset{\\rho}{\\cup}}K\_{p}}(s - v)} \\right\\rbrack{\\cup K\_{m - 1}}(s),} \\\\ {G\_{m - 1}(s)} & {= K\\smallsetminus P\_{m - 1}(s),} \\\\ \\end{aligned}$$  
(7.155)

where *K*[0](*s*) = *P*[0](*s*) = *G*[0](*s*) = ⌀.

Now we can state the selection rule of active variables: *the packet of active variables is formed by the p variables whose indexes correspond to the maximum residuals*, i.e.,

  
$$\\begin{array}{r} {k\_{m}(s) = \\arg\\max\_{i \\in G\_{m - 1}(s)}\\vartheta\_{i}(\\mathbf{z}^{s}).} \\\\ \\end{array}$$  
(7.156)

This rule yields the chain of inequalities

  
$$\\begin{array}{r} {\\vartheta\_{k\_{p}(s)}(\\mathbf{z}^{s}) < \\vartheta\_{k\_{p - 1}(s)}(\\mathbf{z}^{s}) < \\cdots\\vartheta\_{k\_{1}(s)}(\\mathbf{z}^{s}).} \\\\ \\end{array}$$  
(7.157)

Application of the rule (7.156, 7.157) makes all variables active in (*I* + 1) iterations, and this situation occurs again and again with period (*I* + 1).

Our convergence analysis of the algorithm (7.149) will begin with an important notion as follows.

The convergence conditions of the iterative process (7.149) are defined by **Theorem 1**. *Assume that:*

*(a) the functions $\\Phi\_{k}(\\overline{\\lambda}) = \\ln{\\widetilde{B}}\_{k}(\\overline{\\lambda}),\\,(k = \\overline{1,n}),$ are continuously differentiable;*

*(b) the Jacobian matrix $J({\\overline{\\lambda}}^{\*}) = \\left\\lbrack \\frac{\\partial\\Phi\_{k}(\\overline{\\lambda})}{\\partial\\lambda\_{i}} \\right\\rbrack\_{{\\overline{\\lambda}}^{\*}}$ is a Hurwitz matrix;*

*(c) the set *G*[*λ*] is compact;*

*(d) there exists *ε* > 0 such that the inequality $\\|\\overline{\\lambda}(t) - {\\overline{\\lambda}}^{\*}\\| \\leq \\varepsilon,$ where $\\overline{\\lambda}(t)$ is the solution of the system (7.156) with the initial condition $\\overline{\\lambda}(0) = {\\overline{\\lambda}}^{0},$ holds for all ${\\overline{\\lambda}}^{0} \\in G\_{\\lambda}$ starting from some *t* > 0.*

*Then the process generated by the algorithm (7.4) is *G*[*λ*]\-convergent.*

Under the hypotheses of this theorem, the algorithm (7.149) gives a Euler polygon approximation for the solution of the system (7.158).

*Proof.* Choose a countable everywhere dense set of points {*ζ*[*s*]} in *G*[*λ*]. Let *t*[1] be the first time when the solution of equation (7.158) with the initial condition *ζ*[1] gets into the *ε*/2\-neighborhood of the point ${\\overline{\\lambda}}^{\*};$ this time *t*[1] exists by condition (*d*). Choose a neighborhood 𝒢[1] of the point *ζ*[1] so that the points from it will reach the 3*ε*/4\-neighborhood of the point ${\\overline{\\lambda}}^{\*}$ along the trajectory of the system (7.158) after the time *t*[1]. Note that condition (*a*) guarantees that the solution is continuously dependent on the initial conditions.

Choose a point *ζ*[2] among the ones not belonging to 𝒢[1]. Like for the point *ζ*[1], define *t*[2] and a neighborhood 𝒢[2] for the point *ζ*[2]. Continue this process to obtain a cover of the set *G*[*λ*] by open sets 𝒢[1], 𝒢[2], ... Due to condition (*c*), from these sets it is possible to choose a finite subcover 𝒢[*i*[1]], …, 𝒢[*i*[*m*]]. Let *T* = min {*t*[*i*[1]],…,*t*[*i*[*m*]]}. Finally, using condition (*a*), take a sufficiently small value *γ* > 0 so that on the interval 0, *T* the solution of the system (7.158) is approximated by the Euler polygons with the accuracy *ε*/4.

# CHAPTER 8 GENERATION METHODS FOR RANDOM VECTORS WITH GIVEN PROBABILITY DENSITY FUNCTIONS OVER COMPACT SETS

DOI: [10.1201/9781003306566-8](https://doi.org/10.1201/9781003306566-8)

The final stage of the RML procedure is to generate an ensemble of random vectors or trajectories using the entropy-optimal randomized model. Here of crucial importance are the methods that allow to generate these random objects with given PDFs of arbitrary form. In the general statement, the generation problem of random sequences and random vectors is classical for the Monte Carlo method. There exist many methods for generating “standard” sequences of random numbers with given probabilistic characteristics (uniform, Gaussian, Poisson distributions, etc. \[159, [168](#refbib.xhtml#r168)\]). However, when the matter concerns the sequences obeying arbitrary-form PDFs and also the sequences of high-dimensional random vectors, just a few methods can be suggested. At the beginning of this chapter, we will give a brief survey of generation methods, which does not claim to be exhaustive and provides an insight into the main concepts underlying these methods. Our attention will be focused on a method for generating random vectors with PDFs defined on compact sets. It approximates a given PDF by *n*\-dimensional piecewise constant functions, in which the step depends on the Lipschitz constant of this PDF. A major aspect of random object generation is to perform a statistical check whether the probabilistic properties of the generated objects match the given PDF.

## 8.1A Survey of Generation Methods for Random Objects

The problem to generate random variables, vectors and trajectories has a growing significance because the Monte Carlo method is a real tool for solving different problems of numerical integration, optimization, control and machine learning, including randomized machine learning. Therefore, it would be useful for the reader to get acquainted with some generation methods that are frequently mentioned in the literature. This survey consists of two parts, the first being devoted to the generation of random variables and the second to the generation of random vectors.

### 8.1.1Random variables

### 8.1.2Random vectors

## 8.2Direct Generation Method for Random Vectors with Given Probability Density Function

This method uses an approximation of a given PDF by a step function, with a subsequent generation of the uniformly distributed independent random vectors inside a randomly chosen elementary cube. Consider a PDF *w*(**x**), **x** ∈ *Q* ⊂ *R*^(*n*).

### 8.2.1Unit cube *Q*

Introduce a uniform lattice with step *h* for each coordinate of the unit cube *Q*. Then this cube is partitioned into the elementary cubes of volumes *V*[*i*] = *h*^(*n*). Let (1/*h*) be an integer value. Then the number of elementary cubes is *N* = (1/*h*)^(*n*) and $i = \\overline{1,N}.$ For each elementary cube, introduce another lattice with step *η*. As a result, each elementary cube consists of inner subcubes of volumes *v*[*i*]^(*j*) = *η*^(*n*). Denote their number by *M* = (1/*η*)^(*n*), $j = \\overline{1,M}.$ Assume that the total volume of all elementary cubes coincides with the total volume of all their subcubes. Choose an arbitrary point **x**[*i*]^(*j*) in each inner subcube and define the value

  
$$\\begin{array}{r} {C\_{i} = \\frac{1}{M}{\\sum\\limits\_{j = 1}^{M}w}(\\mathbf{x}\_{i}^{j}).} \\\\ \\end{array}$$  
(8.15)

For a sufficiently large number *M*,

  
$$\\begin{array}{r} {\\left. C\_{i} \\right.\\sim\\frac{1}{V\_{i}}{\\int\_{V\_{i}}w}(\\mathbf{x})d\\mathbf{x}.} \\\\ \\end{array}$$  
(8.16)

Therefore,

  
$$\\begin{array}{r} {\\left. C\_{i} \\right.\\sim w(\\mathbf{x})\\quad\\text{if}\\,\\mathbf{x} \\in V\_{i}.} \\\\ \\end{array}$$  
(8.17)

Denote by ${\\overline{\\xi}}^{i},\\, i = \\overline{1,N},$ the independent random vectors obeying the uniform distribution on the elementary cubes. The density of such a vector is 1/*V*[*i*] inside an elementary cube and 0 outside it. These vectors can be generated using the method (8.6, 8.7).

Let *β* be an integer random variable that does not depend on $\\left\\{ {\\overline{\\xi}}^{i} \\right\\}$ and takes values 1, …, *N* with the probabilities *p*[*i*] = *C*[*i*]*V*[*i*]. Then the generated vectors have the form

  
$$\\begin{array}{r} {\\mathbf{x} = {\\sum\\limits\_{i = 1}^{N}{\\overline{\\xi}}^{i}}\\Lambda(\\beta = i),} \\\\ \\end{array}$$  
(8.18)

where *Λ*(*A*) means the indicator function of a set *A*. The PDF of the vector **x** can be written as

  
$$\\begin{aligned} & \\left. P(\\mathbf{x} = d\\mathbf{x}) = {\\sum\\limits\_{i = 1}^{N}P}(\\mathbf{x} = d\\mathbf{x}\\, \\middle| \\,\\beta = i)P(\\beta = i) = \\right. \\\\ & {\\left. \\text{\\quad\\quad}{\\sum\\limits\_{i = 1}^{N}C\_{i}}d\\mathbf{x}\\Lambda(V\_{i}) \\right.\\sim{\\sum\\limits\_{i = 1}^{N}w}(\\mathbf{x})d\\mathbf{x}\\Lambda(V\_{i}).} \\\\ \\end{aligned}$$  
(8.19)

### 8.2.2Compact set *Q*

**1. *Q*—parallelepiped Π**

Consider the set *P**i* = {**x**:**a**≤**x**≤**b**}, where **a** and **b** are given vectors. Denote the lengths of their edges by $l\_{i} = b\_{i} - a\_{i},\\, i = \\overline{1,n}.$ Introduce a nonuniform lattice on this set, which can be designed either with a fixed number *K* of elements for each coordinate or with a fixed step *h*. In the former case, there are different steps for all coordinates, i.e.,

  
$$\\begin{array}{r} {h\_{i} = l\_{i}/K;} \\\\ \\end{array}$$  
(8.20)

in the latter case, different numbers of elements for all lattices, i.e.,

  
$$\\begin{array}{r} {K\_{i} = l\_{i}/h.} \\\\ \\end{array}$$  
(8.21)

In fact, the fixed-step statement has been considered above. Hence, we will study the former case with a variable step. Because the lattice has the same number of elements for each coordinate, the number of all elementary parallelepipeds *Π*[*i*] is *N* = *K*^(*n*). The elementary parallelepipeds have the same volume

  
$$\\begin{array}{r} {V = {\\prod\\limits\_{i = 1}^{n}h\_{i}}.} \\\\ \\end{array}$$  
(8.22)

Inside each parallelepiped, introduce another lattice with *M* elements for each coordinate. Then for each coordinate the lattice step is

  
$$\\begin{array}{r} {\\eta\_{i} = h\_{i}/M,} \\\\ \\end{array}$$  
(8.23)

and the volume of the *j*th inner subparallelepiped *π*[*i*]^(*j*) makes up

  
$$\\begin{array}{r} {v = {\\prod\\limits\_{i = 1}^{n}\\eta\_{i}}.} \\\\ \\end{array}$$  
(8.24)

(here *j* denotes the index of an inner subparallelepiped inside the *i*th elementary parallelepiped). The number of all inner subparallelepipeds *π*[*i*]^(*j*) inside the elementary parallelepiped *Π*[*i*] is

  
$$\\begin{array}{r} {L = M^{n}.} \\\\ \\end{array}$$  
(8.25)

Choose an arbitrary point **x**[*i*]^(*j*) in *π*[*i*]^(*j*) and calculate the value

  
$$\\begin{array}{r} {C\_{i} = \\frac{1}{M}{\\sum\\limits\_{j = 1}^{M}w}(\\mathbf{x}\_{i}^{j}).} \\\\ \\end{array}$$  
(8.26)

Under a sufficiently large number *M*,

  
$$\\begin{array}{r} {\\left. C\_{i} \\right.\\sim\\frac{1}{V\_{i}}{\\int\_{V\_{i}}w}(\\mathbf{x})d\\mathbf{x}.} \\\\ \\end{array}$$  
(8.27)

The remainder of this generation procedure is organized in the same way as for the unit cube; see above.

**2. Arbitrary compact set *Q***

In this case, put the set *Q* into the parallelepiped *Π* = {**x**:**a**≤**x**≤**b**}. The edges can be defined arbitrarily, but in such a way that *Q* ⊂ *Π*. A more efficient approach to generate random vectors is putting the set *Q* into *a hull in form of the parallelepiped *Π*^(\*)*. These possibilities are illustrated in [Figs. 8.1(a)](#chapter8.xhtml#f8_1) and [8.1(b)](#chapter8.xhtml#f8_1) (*a*—arbitrary parallelepiped *Π*, *b*—hull). Clearly, hull construction requires a preliminary calculation of the extreme points (*A*, *B*, *C*, *D*).

![Figure 8.1](images/fig8_1.jpg)

[Figure 8.1](#chapter8.xhtml#f8_1b)

Recall that the PDF *w*(**x**) is defined on the set *Q*. Introduce an auxiliary PDF of the form

  
$$\\begin{array}{r} {W(\\mathbf{x}) = \\left\\{ \\begin{aligned} {w(\\mathbf{x})} & {\\text{if}\\,\\mathbf{x} \\in Q,} \\\\ 0 & {\\text{if}\\,\\mathbf{x} \\in \\Pi\\smallsetminus Q.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  
(8.28)

It is immediately obvious that the parallelepiped Π forms the domain of definition of the PDF *W*(**x**). We will use the generation procedure of item 2 for the PDF *W*(**x**). Note that *W*(**x**) = 0 on the elementary parallelepipeds *Π*[*i*] and also on the inner subparallelepipeds *π*[*i*]^(*j*) inside the set *Π*^(\*) ∖ *Q*. Hence, *P*(**x** = *d***x**) = 0 by (8.2.1).

## 8.3Approximation of Given Probability Density Function

The suggested generation procedure for random vectors with a given probability density function has such important aspects as approximation *accuracy* and lattice *step*.

**1. Estimation of approximation accuracy**

Consider a PDF *w*(**x**), where **x** ∈ *Q* ⊂ *R*^(*n*). The set *Q* is compact, i.e., has a nonzero volume *V*[*Q*] ≠ 0. Assume that the set *Q* is put into an *n*\-dimensional parallelepiped *Π*. The function *w*(**x**) is square integrable.

To generate random vectors with the PDF *w*(**x**), it will be approximated by a piecewise constant function *g*(**x**), **x** ∈ *Π*. The quality of this approximation will be measured by the functional

  
$$\\begin{array}{r} \\left. J(A) = \\middle| {\\int\_{A}\\left( {w(\\mathbf{x}) - g(\\mathbf{x})} \\right)}d\\mathbf{x} \\middle| , \\right. \\\\ \\end{array}$$  
(8.29)

where *A* indicates an arbitrary set in *Π*.

Define a uniform lattice with a step $h\_{k},\\, k = \\overline{1,n},$ for each coordinate on the set Π of the volume *V*[*Π*]. Each element of this lattice is an elementary parallelepiped $\\Pi\_{i},\\, i = \\overline{1,N},$ with the sides *h*[*k*]. Without loss of generality, assume that

  
$$\\begin{array}{r} {N = \\frac{V\_{\\Pi}}{V\_{\\Pi\_{i}}} = \\frac{V\_{\\Pi}}{\\prod\\limits\_{k = 1}^{n}h\_{k}}.} \\\\ \\end{array}$$  
(8.30)

Moreover, let this value be integer. Note that all the elementary parallelepipeds *Π*[*i*] have the same volumes. In each set *Π*[*i*], replace the function *w*(**x**) with a constant *B*[*i*]. Performing this operation for all the elementary parallelepipeds, obtain a piecewise constant linear approximating function *g*(**x**).

Consider a certain set *A* ∈ *Π*. It is covered by the union of the elementary parallelepipeds, i.e.,

  
$$\\begin{array}{r} {A = {\\underset{i = 1}{\\overset{N}{\\cup}}\\Pi\_{i}}.} \\\\ \\end{array}$$  
(8.31)

Then, using the Cauchy–Bunyakovsky–Schwarz inequality, write the upper bound

  
$$\\begin{array}{r} {J(A) \\leq \\sqrt{{\\int\_{A}\\left( {w(\\mathbf{x}) - g(\\mathbf{x})} \\right)^{2}}d\\mathbf{x}{\\int\_{A}\\Lambda}(A)d\\mathbf{x}}.} \\\\ \\end{array}$$  
(8.32)

Here *Λ*(*A*) denotes the indicator function of the set *A*. It follows from (8.32) that

  
$$\\begin{array}{r} {{\\int\_{A}\\left( {w(\\mathbf{x}) - g(\\mathbf{x})} \\right)^{2}}d\\mathbf{x} \\leq {\\sum\\limits\_{i = 1}^{N}{\\int\_{\\Pi\_{i}}\\left( {w(\\mathbf{x}) - B\_{i}} \\right)^{2}}}d\\mathbf{x}.} \\\\ \\end{array}$$  
(8.33)

Hence,

  
$$\\begin{array}{r} {\\sup\\limits\_{A}J(A) \\leq {\\sum\\limits\_{i = 1}^{N}{\\int\_{\\Pi\_{i}}\\left( {w(\\mathbf{x}) - B\_{i}} \\right)^{2}}}d\\mathbf{x}.} \\\\ \\end{array}$$  
(8.34)

As a result, the best estimates of the constants *B*[1], …, *B*[*N*] can be derived by minimizing the functional

  
$$\\begin{array}{r} \\left. {\\sum\\limits\_{i = 1}^{N}{\\int\_{\\Pi\_{i}}\\left( {w(\\mathbf{x}) - B\_{i}} \\right)^{2}}}d\\mathbf{x}\\Rightarrow\\min\_{B\_{1},\\ldots,B\_{N}} \\right. \\\\ \\end{array}$$  
(8.35)

subject to the condition

  
$$\\begin{array}{r} {V\_{\\Pi\_{i}}{\\sum\\limits\_{i = 1}^{N}B\_{i}} = 1.} \\\\ \\end{array}$$  
(8.36)

This equality expresses the normalization condition of the PDF. The solution of the minimization problem is given by

  
$$\\begin{array}{r} {B\_{i}^{\*} = \\frac{1}{V\_{\\Pi\_{i}}}{\\int\_{\\Pi\_{i}}w}(\\mathbf{x})d\\mathbf{x}.} \\\\ \\end{array}$$  
(8.37)

Thus, the described approximation procedure yields the optimal piecewise constant PDF *g*^(\*)(**x**) with the approximation accuracy

  
$$\\begin{array}{r} {\\sup\\limits\_{A}J(A) \\leq \\sqrt{V\_{\\Pi}}\\sqrt{{\\sum\\limits\_{i = 1}^{N}{\\int\_{\\Pi\_{i}}\\left( {w(\\mathbf{x}) - B\_{i}^{\*}} \\right)^{2}}}d\\mathbf{x}} \\leq \\delta.} \\\\ \\end{array}$$  
(8.38)

**2. Optimization of lattice step (estimation of Lipschitz constant)**

The procedure suggested below employs an estimate of the Lipschitz constant for the function *w*(**x**), which is assumed to be continuous. We have *B*[*i*]^(\*) = *w*(**x**[*i*]^(\*)), where **x**[*i*]^(\*) ∈ *Π*[*i*] but the point **x**[*i*]^(\*) is unknown. Let the function *w*(**x**) satisfy the Lipschitz condition with a constant *L*, i.e.,

  
$$\\begin{array}{r} {\\max\_{\\mathbf{x} \\in \\Pi\_{i}}\\left( {w(\\mathbf{x}) - B\_{i}^{\*}} \\right)^{2} \\leq L^{2}\\|\\mathbf{x} - \\mathbf{x}\_{i}^{\*}\\|.} \\\\ \\end{array}$$  
(8.39)

The integral form of this inequality on the intervals \[0, *h*[1]\] × \[0, *h*[2]\] × ⋯ × \[0, *h*[*n*]\] can be written as

  
$$\\begin{array}{r} {{\\int\_{|pi\_{i}}\\left( {w(\\mathbf{x}) - B\_{i}^{\*}} \\right)^{2}}d\\mathbf{x} \\leq L^{2}{\\int\_{0}^{h\_{1}}\\cdots}{\\int\_{0}^{h\_{n}}\\left( {x\_{1}^{2} + \\cdots + x\_{n}^{2}} \\right)}dx\_{1}\\cdots dx\_{n} =} \\\\ {L^{2}\\left( {\\frac{h\_{1}^{3}}{3}h\_{2}h\_{3}\\cdots h\_{n} + \\frac{h\_{2}^{3}}{3}h\_{1}h\_{3}\\cdots h\_{n} + \\cdots + \\frac{h\_{n}^{3}}{3}h\_{1}h\_{2}\\cdots h\_{n - 1}} \\right) = L^{2}\\varrho.} \\\\ \\end{array}$$  
(8.40)

The variable *ϱ* is independent of the index *i* of an elementary parallelepiped because all of them have the same sizes. Taking into account (8.40), transform inequality (8.34) into

  
$$\\begin{array}{r} {\\sup J(A) \\leq L\\sqrt{V\_{\\Pi}{\\sum\\limits\_{i = 1}^{N}\\varrho}} = L\\sqrt{V\_{\\Pi}N\\varrho}.} \\\\ \\end{array}$$  
(8.41)

Then

  
$$\\begin{array}{r} {V\_{\\Pi} = NV\_{\\Pi\_{i}} = N{\\prod\\limits\_{j = 1}^{n}h\_{j}}.} \\\\ \\end{array}$$  
(8.42)

Hence, using (8.40), the right-hand side of inequality (8.41) can be reduced to

  
$$\\begin{array}{r} {L\\sqrt{V\_{\\Pi}N\\varrho} = L\\sqrt{V\_{\\Pi}}N\\varrho = L\\sqrt{V\_{\\Pi}^{2}}\\frac{\\varrho}{\\prod\\limits\_{j = 1}^{n}h\_{j}} = \\frac{L}{\\sqrt{3}}V\_{\\Pi}\\sqrt{\\sum\\limits\_{j = 1}^{n}h\_{j}^{2}}.} \\\\ \\end{array}$$  
(8.43)

Denote *h* = max[1 ≤ *j* ≤ *n*]*h*[*j*]. Then it follows from (8.41, 8.43) that

  
$$\\begin{array}{r} {\\sup J(A) \\leq L\\sqrt{n/3}hV\_{\\Pi}.} \\\\ \\end{array}$$  
(8.44)

For a given approximation accuracy *δ* of the PDF *w*(**x**), the corresponding maximum lattice step is

  
$$\\begin{array}{r} {h = \\frac{\\delta}{L\\sqrt{\\frac{n}{3}}V\_{\\Pi}}.} \\\\ \\end{array}$$  
(8.45)

The maximum step for the longest edge of the parallelepiped allows us to find the number *N* of points and, using it, the steps *h*[*j*] for all other coordinates.

**3. Rough estimate of step**

The estimation method of the Lipschitz constant *L* and the maximum step *h* for elementary parallelepipeds design rests on the assumption that the integral in (8.37) can be calculated analytically (without errors). Unfortunately, this is not always the case. A given PDF often has a complex structure, which requires numerical calculation of the integral in formula (8.37). Such calculations are performed using an inner lattice with a step *η*[*i*] that is considerably smaller than the step *h*[*i*] of the main lattice.

The step *η*[*i*] can be chosen using a simple technique as follows. First, specify a certain step *η*[*i*]^(*j*), and calculate the number *M*[*i*]^(*j*) = *l*[*i*]/*η*[*i*]^(*j*) of points in the integral sum *S*[*i*]^(*j*). Then repeat these operations, and check the variability of the resulting integral sums. If |*S*[*i*]^(*j*)−*S*[*i*]^((*j* − 1))|≤*δ*, where *δ* is a given accuracy, then stop further partition of the inner lattice. The integral can be estimated by

  
$$\\begin{array}{r} {{\\int\_{\\Pi\_{i}}\\left( {w(\\mathbf{x}) - {\\hat{B}}\_{i}^{\*}} \\right)^{2}}d\\mathbf{x} \\leq {\\hat{J}}\_{i} = S\_{i}^{j^{\*}} + \\delta/2.} \\\\ \\end{array}$$  
(8.46)

Here *j*^(\*) denotes the index of the inner lattice for which the calculations are stopped. Then, according to (8.38),

  
$$\\begin{array}{r} {\\sup\\limits\_{A}J(A) \\leq \\sqrt{V\_{\\Pi}}\\sqrt{{\\sum\\limits\_{i = 1}^{N}{\\hat{J}}\_{i}} + N\\delta/2}.} \\\\ \\end{array}$$  
(8.47)

The constants *B̂*[1]^(\*), …, *B̂*[*N*]^(\*) and the estimates *Ĵ*[1], …, *Ĵ*[*N*] are obtained numerically.

Because all the calculations have a rough character, it makes sense to consider an accuracy estimate based on another metric. Let $A \\subseteq {\\underset{i = 1}{\\overset{N}{\\cup}}Q\_{i}}.$ Since *V*[*Q*[*i*]] is independent of *i*,

  
$$\\begin{array}{r} \\left. \\sup\\limits\_{A}J(A) \\leq V\_{Q}{\\sum\\limits\_{i = 1}^{N}\\max\_{\\mathbf{x} \\in Q\_{i}}} \\middle| w(\\mathbf{x} - C\_{i}) \\middle| . \\right. \\\\ \\end{array}$$  
(8.48)

The optimal constants $C\_{i},i = \\overline{1,N},$ are yielded by solving the optimization problem

  
$$\\begin{array}{r} \\left. {\\sum\\limits\_{i = 1}^{N}\\max\_{\\mathbf{x} \\in Q\_{i}}} \\middle| w(\\mathbf{x} - C\_{i}) \\middle| \\Rightarrow\\max\_{C\_{1},\\ldots,C\_{N}}. \\right. \\\\ \\end{array}$$  
(8.49)

The solution has the form

  
$$\\begin{array}{r} {{\\widetilde{C}}\_{i} = \\frac{\\max\_{\\mathbf{x} \\in Q\_{i}}w(\\mathbf{x}) + \\min\_{\\mathbf{x} \\in Q\_{i}}w(\\mathbf{x})}{2}.} \\\\ \\end{array}$$  
(8.50)

Recall that these constants are used to construct an approximating function for the PDF. Hence, they must be normalized in the following way:

  
$$\\begin{array}{r} {C\_{i}^{\*} = \\frac{{\\widetilde{C}}\_{i}}{V\_{Q}{\\sum\\limits\_{i = 1}^{N}{\\widetilde{C}}\_{i}}}.} \\\\ \\end{array}$$  
(8.51)

In the final analysis, the error can be estimated as

  
$$\\begin{array}{r} \\left. \\sup\\limits\_{A}J(A) \\leq V\_{Q}{\\sum\\limits\_{i = 1}^{N}\\max\_{\\mathbf{x} \\in Q\_{i}}} \\middle| w(\\mathbf{x} - C\_{i}^{\*}) \\middle| . \\right. \\\\ \\end{array}$$  
(8.52)

Consequently, we have derived two estimates for the approximation error, (8.47) and (8.52). In applications, it is necessary to calculate both estimates and compare them with a given accuracy. If at least one of the estimates fails, calculations should be repeated with a smaller lattice step.

# CHAPTER 9 INFORMATION TECHNOLOGIES OF RANDOMIZED MACHINE LEARNING

DOI: [10.1201/9781003306566-9](https://doi.org/10.1201/9781003306566-9)

By now the computer systems of various performance levels have evolved towards a heterogeneous structure that is characterized by an availability of computing devices of different types. A standard system includes a universal multi-core processor in combination with a massive-parallel architecture accelerator (also called a computational processor or a coprocessor). An overwhelming majority of modern high-performance systems is based on the concept of horizontal scaling, integrating thousands of heterogeneous computation modules within a uniform organization.

The heterogeneous architecture of computation modules considerably complicates an efficient utilization of computer systems, which is often comprehended as an almost 100% load of all computing devices. Here a main difficulty consists in architectural features and, in many cases, in significant distinctions of the application programming interfaces (API) available for computing devices of different types. For massive-parallel accelerators, the former factor causes the need for parallel data processing and use of corresponding algorithms. The latter factor predetermines a high complexity of the software tools implementing different models of programming, in terms of their development and integration.

Therefore, a topical problem of contemporary computer science is to suggest new approaches to the development and implementation of the algorithms and technologies intended for a wide range of heterogeneous computer systems.

In the recent times, machine learning has achieved a definite level of maturity, being now applicable to many practical problems that had been considered unsolvable or far too computationally intensive. Much of the current advancements in this science lie in the field of software engineering, due to a high computational complexity of most real problems. These are high-dimensional optimization problems that demand efficient computational algorithms.

In some aspects, randomized machine learning imposes even tougher requirements to computational efficiency, which is associated with the difficult mathematical problems in the foundation of this theory. Thus, an efficient implementation of RML methods comes to parallel calculations using heterogeneous structure computing systems.

## 9.1Architecture of Modern Computer Systems

The present-day computer systems based on von Neumann's architecture may have different configuration depending on the number and type of processors, the capacity and structure of memory, and the presence of accelerators (coprocessors). These systems can be classified using a logical structure of memory, which defines memory access rules for the program codes executed by a processor. Such an approach discriminates between two classes of the systems, namely, the ones with shared and distributed memory. Of course, this classification suffers from certain drawbacks but yields a convenient and efficient representation of computer systems for the development and analysis of system-oriented algorithms.

Within this classification, the address space of memory accessed by processors is either uniform or separate. This property predetermines an appropriate *programming model* for utilization of computer system resources.

Note that the classification under study is not unique. There exist technologies allowing a user to treat a computer system with physically distributed memory as a system with a uniform address space. Conversely, a system with distributed memory can be emulated on a system with shared memory.

Two standard programming models have become widespread in these classes to date, namely, the model based on *shared memory* and the model based on *message passing*. The former model has the advantages of a uniform address space owing to a direct usage of shared memory for data transmission between processors. The latter model incorporates a data blocking mechanism, and data blocks are sent to other processors in the form of messages. For the time being, a detailed organization of these mechanisms is not so important: note that message transfer is a slower operation than direct memory access. This property must be taken into account in the course of algorithm development.

First and foremost, further advancement of computer systems aims at reducing the time required to solve the existing problems or at formulating and solving new (or current) of larger scale. Historically, computer performance has been improved using two approaches that finally formed the concepts of *vertical* and *horizontal scaling*. Vertical scaling is implemented by increasing the performance of one computation module whereas horizontal scaling by increasing the number of computation modules.

As a rule, a computation module represents a single- or multi-processor system with shared memory, i.e., a computer system with a uniform address space that can be accessed by any processor. Such a general description covers common single-processor workstations and also rather large multi-processor computer systems.

At the initial phase, the computation modules were developed within the concept of vertical scaling, since a rapid progress of microelectronics yielded faster and faster processors and memory modules. As soon as the physical limits were achieved, making further speed-up of a single processor impossible, the evolution moved towards horizontal scaling, i.e., multi-core processors. Note that horizontal scaling was also used for increasing the number of processors with identical access to shared memory.

An accumulated experience in the design of large multi-processor systems with shared memory demonstrated that many processors cannot be utilized with good efficiency within the framework of a common memory model. Therefore, the only way for a theoretically unrestricted growth of computer performance is horizontal scaling applied to the computation modules operating in the shared memory model. Obviously, at the upper level a system with this architecture represents a system with distributed memory. Most modern high-performance computer systems are designed using this principle and architecture.

As a result, a parallel execution of programs at different levels of computer systems became a basic approach to improve their performance. A real feasibility of program code parallelization led to the uprise of a new science called parallel computing. This science studies hardware tools for a parallel execution of programs and also a wide circle of issues related to the efficient exploitation of such systems.

The modern computer systems have a support of program parallelism, at the level of hardware and also at the level of system software (operating system). Users of such a computer system are developing programs that are implemented and executed using a functionality provided by its operating system. Thus, we can identify three main layers for a program that implements a given algorithm; see [Fig. 9.1](#chapter9.xhtml#f9_1).

![Figure 9.1](images/fig9_1.jpg)

[Figure 9.1](#chapter9.xhtml#f9_1b)

The lower layer answers for hardware support (*hardware layer*); in accordance with von Neumann's architecture, this layer can be described by a command handling node (processor) and storage memory for commands and data. Of course, the real systems have a more complicated organization, but this simple diagram suffices for our level of detail. The second layer, called the *system layer*, forms system software required for an abstract operation of all hardware tools by a user regardless of their functionality. Finally, user (or application software) occupies the upper level of the architecture, which is known as the *user layer*.

Now let us discuss the elements of this architecture in more depth, as illustrated in [Fig. 9.2](#chapter9.xhtml#f9_2). The commands executed by a processor have a certain organization and are coming sequentially, thereby forming *a thread of execution*. This is a major concept for parallelization at the hardware level of a computer system \[[45](#refbib.xhtml#r45)\].

![Figure 9.2](images/fig9_2.jpg)

[Figure 9.2](#chapter9.xhtml#f9_2b)

Parallelism is implemented through a simultaneous execution of several commands or threads. Here a widespread approach is the so-called *simultaneous multi-threading* (SMT), in particular, the Hyper-Threading Technology developed by Intel. This approach allows to execute several threads on a single processor (processor core), thereby implementing not physical but logical parallelization. Nevertheless, a considerable increase in performance can be gained because in most programs the execution process also includes latent operations (working with memory and storage devices). Waiting for their completion, a processor may execute several commands from another thread. If there exist many available processors or cores (*processing elements* (PEs) in the terminology of large-scale computer systems), then it is possible to organize a real parallelism for threads.

A user manages hardware tools (in our case, processor threads) through an application programming interface (API) provided by corresponding software tools. Therefore, for a user processor threads as physical objects are represented in the form of logical objects independent of hardware support. These objects implement a program code created by a user of a computer system. The main objects of this class are threads and processes of an operating system.

A *process* is a basic element of execution for an operating system that is implemented by a special program object. All contemporary operating systems can run several processes via a simultaneous execution. A program code is executed in a processor, and a real parallelism is impossible for a single processor. However, in this case, a logical parallelism can be organized.

For safe execution, the processes of an operating system are isolated from each other in computer memory. In particular, this feature imposes some restrictions on their interaction, which are implemented using special mechanisms. A concrete form of these mechanisms bears computational cost, as it is necessary to guarantee a safe functioning of all processes. Thus, a process is a “heavy” object consuming considerable computational resources for their creation, functioning and elimination. At the same time, a *thread* is a “light” program object that operates within the framework of the resource sharing model of a process (memory, file descriptors, etc.). Hence, threads do not need much resources for their functioning. A process contains at least one thread.

Being fundamental objects at the system level, the threads and processes also define an abstraction level for a user-friendly development of algorithms and programs. Therefore, the system-level architecture of a computer system that is implemented by an operating system has a hierarchical organization. In accordance with this architecture, a major task for the system level is *to map* system objects into hardware ones, i.e., to support an execution of the system (logical) threads within the hardware threads directly on a processor.

The contemporary operating systems are multitasking, which means that they can support many simultaneously running processors by sharing the address space of memory among them to guarantee their safe execution. This leads to a parallel execution of *tasks* and hence a logical parallelism. A physical parallelism can be achieved if a computing device (processor) features a real execution of a process or thread. Consequently, for a successful parallelization of several processes a computer system must have several computing devices (processors or cores).

Note that multitasking can be implemented with a single computing device, e.g., based on time sharing: an operating system executes each process during a fixed period of time, then suspends it and switches to another process. Clearly, this approach gives no real increase in performance, and the advantages of parallelism are not gained.

## 9.2Universal Multithreaded Architecture

An important aspect of software development consists in the design and analysis of corresponding algorithms that are implemented by software products. The general architecture of a computer system described above (particularly, the system level) predetermines possible methods to analyze and develop application software at the user level. The development of efficient algorithms becomes even a more topical problem for the computer systems that support parallelism \[45, [69](#refbib.xhtml#r69), [183](#refbib.xhtml#r183)\].

Historically, the algorithms intended for parallel computer systems were analyzed by considering the lowest level of implementation, i.e., the decomposition of “calculations” into elementary operations with direct analogs in a programming language. After such a detailed specification, further analysis was focused on hardware tools (the hardware level) with a detailed specification down to processors and their internal structure in order to find a most efficient utilization of a concrete computer system.

The detailed approach to the development and analysis of algorithms led to the appearance of different theories, with a main goal to suggest a universal analysis procedure for parallel algorithms. In this context, note an original method with a *model of computations* or a *model of programs*, which employs graph theory techniques for modeling and analysis \[[62](#refbib.xhtml#r62), 183\].

The progress of the computer systems in a wide sense, i.e., the whole range of hardware and software technologies, has achieved a stage in which many algorithms and approaches become standard. In other words, there exist efficient implementations for them in form of software tools or technologies supported by all basic architectures of modern computer systems. Also note that a large number of such technologies are commercial, which guarantees a high level of quality, reliability and efficiency.

As indicated by the history of many fields of science, owing to the development of tools it is possible to consider new problems on a new layer of abstraction defined by these tools. Therefore, “higher-level” approaches are needed to develop and analyze the algorithms intended for modern computer systems. In view of the general architecture of a computer system (see [Section 8.1](#chapter8.xhtml#sec8_1)), we believe that the desired approaches should involve the user layer: in this case, the algorithms can be efficiently formulated and further analyzed under an available level of abstraction.

The computations within an algorithm are the result of operation of a corresponding program. In literature there is almost no separation between the concepts of program and algorithm. Nevertheless, we will discriminate between them, treating an algorithm as an abstract thing that includes abstract operations and operands, whereas a program implementing this algorithm deals with real operations provided by its execution environment.

Consider a virtual thread as a basic abstract object that implements computations. This object lies at the user level of the computer system architecture. Here all computations have an abstract sense. It is also possible to further specify and study these concepts and associated objects, depending on the level of detail of a given algorithm.

By assumption, the user layer of a computer system provides a certain set of such virtual threads and also the feasibility of a parallel execution for them within the shared memory model, thereby defining a virtual *multithread execution environment*. Depending on the specifics of a task (algorithm), such a general parallelism-oriented representation of a computational environment facilitates a more efficient analysis of different characteristics of the algorithms on its basic elements (on the one hand) and also an efficient mapping of the user layer into the system layer (on the other hand).

Interestingly, nowadays similar ideas are prevailing in different technologies, and hence the abstractions are “bound” to the corresponding implementation objects. For example, note well-known program platforms such as Java, MPI, OpenMP, and others. Here the abstractions, which can be treated as the virtual threads under consideration, have a unique correspondence to the program objects implementing them. Particularly, this applies to the Java and OpenMP threads as well as to the MPI processes. The suggested approach yields necessary and sufficient tools with various implementation capabilities owing to its abstraction.

This approach can be easily scaled, vertically (with an increase in the volume of computations in a thread, causing a higher granularity of computations) and also horizontally (with an increase in the number of threads). In addition, it is possible to model a computer system with different memory structure, e.g., distributed memory, by considering several virtual execution environments.

The described architecture of a virtual computer system, further referred to as *the universal multithread architecture (UMA)*, is high-level and can be efficiently implemented on all computer systems using the existing technologies. Due to this universalism, the architecture may serve for the development and analysis of parallel algorithms (see [Fig. 9.3](#chapter9.xhtml#f9_3)).

![Figure 9.3](images/fig9_3.jpg)

[Figure 9.3](#chapter9.xhtml#f9_3b)

Modern computer systems often have a heterogeneous structure, i.e., their computation modules contain computing devices of different types. The main types of such devices are universal central processors and computational coprocessors (accelerators) with a massive-parallel architecture. However, all these devices involve threads as a basic element of command execution; for a user, threads represent virtual (logical) objects that are mapped into hardware threads during execution.

It is possible to work with an accelerator in several modes, which have logical and physical aspects dictated by implementations on concrete devices or families of devices. For example, the well-known massive-parallel architectures, MIC \[[7](#refbib.xhtml#r7)\] or CUDA \[[6](#refbib.xhtml#r6)\], utilize a processor in the offload mode as follows: a current computation job is “offloaded” to a processor and performed on it, and then the results are sent back to a calling program. Such an organization allows for an asynchronous operation of a device from different threads of a calling program.

For the systems designed as an aggregate of computation modules with a heterogeneous architecture, there are three levels to implement parallelism (see [Fig. 9.4](#chapter9.xhtml#f9_4)), namely,

*   the level of computation modules, which is implemented on the system layer by the processes of an operating system;
    
*   the level of central processor, which is implemented by the processor threads;
    
*   the level of accelerator, which is implemented by the accelerator threads.
    

![Figure 9.4](images/fig9_4.jpg)

[Figure 9.4](#chapter9.xhtml#f9_4b)

Consequently, parallelism has a hierarchical three-level structure, which is typical for modern computer systems. The universal multithread architecture lies at a higher level of abstraction, providing a universal abstract interface for the development and analysis of parallel algorithms. In addition, the main objects of this interface can be implemented (described) by the objects occupying different levels in the three-level architecture.

## 9.3Information Technologies of Randomized Machine Learning

Information technologies include computer methods and tools that are intended for data storage, handling, extraction and transmission \[[103](#refbib.xhtml#r103)\]. The matter concerns hardware tools (computers, storage devices, telecommunication equipment) and also software tools if they form a complete technology with a requisite user functionality. Hardware tools are often divided into computer hardware and communication hardware; software tools, into system and application software. According to this structural classification, the information technologies of RML occupy the application software level.

Any technology aims at solving some practical tasks or problems. We will comprehend solution in a general sense because in many cases initial problems are associated with an abstract subject area. This state of the things arises in fundamental research, as subject areas are mostly defined by an abstract framework (e.g., different mathematical constructions). The expected results—the solution of a problem—must also belong to the same subject area.

The implementation results of an information technology are obviously related to the subject area of computer systems, representing artifacts of this subject area. Thus, the information technologies intended for solving definite problems can be treated as tools for a corresponding subject area, supplementing the basic tools (on the one part) and forming an intermediate layer for a higher-level technology (on the other part).

A machine learning procedure (see [Chapter 1](#chapter1.xhtml) and [Fig. 1.3](#chapter1.xhtml#f1_3)) can be described as an abstract technology with the following stages:

1.  development of parameterized model (PM);
    
2.  parameter estimation (PE);
    
3.  model testing (MT);
    
4.  model implementation (MI).
    

The second and third stages together form *model learning (ML)*.

This technology rests on the abstract mathematical methods introduced above, which are the basic tools. Hence, there exists a correspondence between mathematical tools and abstract technological stages, as illustrated in [Fig. 9.5](#chapter9.xhtml#f9_5). At the level of mathematical tools, the PM stage is associated with the mathematical modeling methods discussed earlier. The model learning stage is implemented through the statement of corresponding optimization problems. According to the diagram, the model implementation stage has no counterpart in mathematical tools. Also, note that for real problems, the resulting optimization problems cannot be solved analytically, and the only alternative consists in a numerical solution.

![Figure 9.5](images/fig9_5.jpg)

[Figure 9.5](#chapter9.xhtml#f9_5b)

The solution of these problems lies in the subject area of computer (information) technologies, which supplement the necessary tools for solving an initial problem. In particular, they implement the stages of model learning and implementation.

Consider these tools in detail, as demonstrated in [Fig. 9.6](#chapter9.xhtml#f9_6). The elements of the technology under study are implemented through the program objects of an execution environment, depending on the architecture of a current or target computer system. There exist a rich variety of concrete technologies available for modern computer systems. Hence, the approach with a maximum possible abstraction from their specifics seems most productive here.

![Figure 9.6](images/fig9_6.jpg)

[Figure 9.6](#chapter9.xhtml#f9_6b)

**1. Model Development (MD)**

This block constructs a parameterized model in accordance with the existing ideas of a modeled phenomenon. As mentioned earlier, it is possible to outline a narrow circle of model types for a successful solution of real problems. This block outputs a developed model (M).

**2. Model Learning (ML)**

The model learning block receives the model M as its input data. The main tasks of this block are to estimate the model parameters (block PE) and to test the model itself (block MT). Both blocks operate using data (D), which are represented in computer form at the implementation stage of the technology and can be divided into learning data (LD) and test data (TD). This block outputs optimal PDFs (F), namely, the PDFs F[*P*] of the model parameters and the PDFs F[*Q*] of the measurement noises.

The ML block is most “loaded” due to its tasks, in the first place, solution of the optimization problem. We have discussed the inherent difficulties of this problem in the previous chapters of the book. Hence, the ML block must incorporate efficient global optimization algorithms or have access to them.

**3. Model Implementation (MI)**

The model implementation block yields a learned model, i.e., the model M equipped with the functions F[*P*] and F[*Q*] calculated in the preceding stage. Model implementation consists in generating an output ensemble (EG block), with further calculation of its characteristics in the ensemble analysis (EA) block. For model implementation and testing (see the preceding stage), the ensemble is generated by producing a large number of realizations of the random variables (sampling) with given PDFs. Therefore, these blocks must have access to the corresponding generation algorithms of random variables with arbitrary PDFs.

The described technology of RML can be implemented in the form of separate program modules communicating with each other in a manual mode or through a larger-scale technology. Such technologies are implemented within *information systems* intended for solving specific practical tasks. A comprehensive treatment of all issues related to the architecture of information systems goes beyond the scope of this book. We will dwell on some theoretical aspects only, considering them in a most general statement.

An information system (IS) is often defined as a system that integrates different resources (human, technical, financial) and serves for data storage, retrieval and processing \[[3](#refbib.xhtml#r3), [39](#refbib.xhtml#r39)\]. A major component of an information system consists in software resources, which can be classified by analogy with the architecture of computer systems. Since the system-level software is standardized and widespread, the most significant part of an IS subject to its tasks is implemented on the user level as application software. Note that users will be understood in an abstract sense, as an information system can be utilized by humans or other systems. Such an approach is conventional in program system design and development \[[59](#refbib.xhtml#r59), [78](#refbib.xhtml#r78)\].

A user interacts with an IS through a user interface (see [Fig. 9.7](#chapter9.xhtml#f9_7)), which will be accordingly considered in an abstract sense. This interface determines a collection of admissible operations for system users, i.e., represents an abstract “control panel” of a given system. Thus, system functionality is separated from control functionality, at the logical level and, as a rule, at the physical level.

![Figure 9.7](images/fig9_7.jpg)

[Figure 9.7](#chapter9.xhtml#f9_7b)

A user interface controls a program system and, obviously, demonstrates the results of operation in a requisite user-friendly form. Once again, we will adhere to an abstract consideration as follows. If a user is a human, then a user-friendly interface consists of images, graphs, numbers displayed in an appropriate way; this also applies to the “control panels,” which are now organized, e.g., through a window interface with control elements such as push buttons, checkboxes, entry fields, etc. For external systems, window interfaces are not required but we still have the same principles as for human users: data are represented in a form dictated by the input specifications of an external system, and control is implemented by linking control elements on both sides.

Under the described approach, it is necessary to achieve the logical (and often physical) separation of a system functionality into loosely coupled modules for a higher reliability and smaller complexity of program system design. There exist several efficient methods for solving this problem, e.g., the Model-View-Controller (MVC) design. This software architectural pattern identifies three abstract subsystems (components) communicating through corresponding interfaces, namely, Model, View, and Controller \[[99](#refbib.xhtml#r99)\]; see the diagram in [Fig. 9.7](#chapter9.xhtml#f9_7). Here the main idea is that a user controls a program system with a functionality provided by Controller and reads information about the system operation with View. This architectural pattern implies a possible multiplicity of information representations (views) and control devices, depending on problem specifics. The conceptual functionality of a program system is mostly concentrated in Model.

The described general scheme is prevailing in almost all fields associated with program systems. Due to abstractiveness, it can be implemented on any computer systems using software technologies.

A significant feature of the approach is its universalism with respect to system components. In other words, the approach works well for the whole system and also for its components whenever they are designed and implemented in an intelligent way. Particularly, the RML technology implemented as a program component can be a component for a larger system, being integrated into the latter through the interfaces of its control and view subsystems.

Speaking most generally, the RML component can be represented as an object that receives data and “knowledge” at its input and then implements a randomized model (RM). In this context, all the things mentioned are considered as the program realizations of the corresponding abstract objects: the knowledge is encapsulated into the model object (see [Fig. 9.6](#chapter9.xhtml#f9_6)) whereas the randomized model into the learned model object, with the optimal PDFs defined by the RML program component.

For the structural diagram of the RML technology in [Fig. 9.6](#chapter9.xhtml#f9_6), the most resource-intensive operations are

*   optimization;
    
*   generation of the random variables with given PDFs;
    
*   analysis of the output ensemble of the randomized model.
    

Therefore, these operations should be implemented using high-performance computer systems with the potential of parallel computing. Still they may have structural differences due to the architectural properties of computer systems, which predetermine a universal approach to their operation for users. We will accordingly separate out the basic configurations of computer systems as follows:

*   a workstation, which is equipped with a single multi-core central processor and a single massive-parallel accelerator (in modern conditions, a graphics adaptor);
    
*   a multi-processor computing module or several such modules, each containing several central processors and possibly several accelerators;
    
*   a computer system of the supercomputer class, which contains thousands or tens of thousands of computing modules.
    

This approach leads to the implementation problem of program modules for realizing the potential of parallel computing for different configurations of computer systems (see [Fig. 9.8](#chapter9.xhtml#f9_8)). The universal multithread architecture serves as a base for the efficient algorithms for solving these issues; moreover, it would reduce the program complexity of such algorithms and related technologies under an intelligent implementation using the system-level software technologies.

![Figure 9.8](images/fig9_8.jpg)

[Figure 9.8](#chapter9.xhtml#f9_8b)

## 9.4Implementation of Packet Iterations

As mentioned earlier, a major difficulty to implement the RML technology is to solve the global optimization problem for the entropy-optimal PDFs of a randomized model. Consider some general implementation aspects of the global optimization method described in [Chapter 6](#chapter6.xhtml).

The method of packet iterations calls for a large amount of computations. However, they are similar and involve very many *data elements*, for which it is necessary to calculate the values of definite functions. Therefore, *parallelism by data* seems natural here. Our idea is to implement the calculations for each data element using a virtual thread in accordance with the UMA.

The data elements in each stage of the algorithm are implemented through different objects. In the generation stage, they have the serial number (index) of a random point; in the stages of filtration and selection, the data elements are these points themselves (see [Fig. 9.9](#chapter9.xhtml#f9_9)).

![Figure 9.9](images/fig9_9.jpg)

[Figure 9.9](#chapter9.xhtml#f9_9b)

While implementing the algorithm on specific equipment, it is possible to map virtual threads into hardware threads in different ways; some of them are illustrated in [Fig. 9.9](#chapter9.xhtml#f9_9). The mapping process consists in implementing virtual threads in the real system-level objects of a computer system, i.e., threads and processes. There exists different methods for such an implementation, e.g., a “manual” control of this process involving some characteristics of a desired mapping of virtual threads into real ones. Another approach employs an automatic mapping, which is performed either with system-level software or intermediate user-level software that implements the algorithm.

Universal processors support a small number of threads; in this case, an execution of virtual threads in real ones (through their implementation in the form of processes or threads) can be organized in groups so that the virtual threads of each group are executed sequentially. Massive-parallel accelerators support a simultaneous execution of hundreds of threads but virtual threads are mapped into the real threads of an accelerator in a similar way, despite that their number is extremely higher. In practice the mapping mechanism is completely automated and thread scheduling is performed by the system-level software of a computer system.

Under the multithread approach, the global optimization algorithm involves very many virtual threads related to a corresponding number of data elements in each stage of the algorithm. The algorithm was successfully implemented on the OpenMP and CUDA platforms, which demonstrated an efficiency of this approach. Note that its major advantage lies in good scalability.

# CHAPTER 10 ENTROPY CLASSIFICATION

DOI: [10.1201/9781003306566-10](https://doi.org/10.1201/9781003306566-10)

Classification forms a central problem in machine learning and data analysis. An object is classified by associating it with one of two or several categories depending on its characteristics (attributes). The binary (two-class) classification problem acts as a basic statement for further generalization to the case of several classes in real applications.

This chapter is devoted to a solution of the binary classification problem within the randomized machine learning framework. We will briefly survey the existing classification methods (as well as some of their drawbacks) and then describe in detail the entropy classification method, in particular, the application of this method, for a series of numerical examples.

## 10.1Standard Classification Methods

Object classification is a learning problem with a “learner.” In other words, there exists a learning sample with marked answers that is used by an algorithm for identifying most significant attributes and associating their values with an appropriate class.

Classification algorithms may differ by their treatment of a learning sample, representation of classification errors, convergence rate, and so on. In this section, we will outline most widespread classification algorithms, namely,

*   Decision Tree (DT);
    
*   *k*\-Nearest Neighbor (kNN);
    
*   Naive Bayes;
    
*   linear classifiers (Logistic Regression, Support Vector Machines, etc.).
    

The interested reader may find more information about these and other classification methods in the classical books on machine learning, e.g., \[10, [118](#refbib.xhtml#r118), [180](#refbib.xhtml#r180), [194](#refbib.xhtml#r194)\] in Russian and \[21, 57\] in English.

### 10.1.1Decision Tree

Decision Tree is a branching hierarchical structure of attribute values for an object. Branching stops as soon as further division of attribute values into groups does not refine information, i.e., does not yield different classes. Therefore, in the final analysis each leaf on the last layer of a decision tree contains the members of the same class.

The concept of Decision Tree was pioneered by Breiman and his colleagues \[[23](#refbib.xhtml#r23)\]. With the course of time, the original algorithm has been continuously developed and modified. Nowadays, Decision Tree is a most popular classification method in the world, and its modification C4.5 ranks first among the top-10 data analysis algorithms \[[193](#refbib.xhtml#r193)\].

For decision tree design, a major difficulty is to choose an proper branching criterion, i.e., a sequence in which the attributes should be considered. Since optimal decision tree design represents an NP-complete problem \[[75](#refbib.xhtml#r75)\], branching criteria are often based on “greedy” heuristics, e.g., information gain \[[117](#refbib.xhtml#r117)\] and Gini impurity \[23, 57\].

Decision trees have an clear meaning and a simple interpretation of results. Moreover, they do not require special data preparation and are applicable to large amounts of data without auxiliary tools. However, decision tree design suffers from considerable disadvantages as follows.

In the first place, decision trees can be relearned due to an excessively detailed partition. This effect may take place even for relatively simple problems \[[110](#refbib.xhtml#r110)\]. Second, decision tree design is very sensitive to input data: even small changes in a learning sample may dramatically modify the resulting structure of a decision tree, especially in the case of data spreads.

Thus, decision trees are easy to implement and often serve as a rough approximation of solution but other classification algorithms yield better results.

### 10.1.2*k*\-Nearest Neighbor

As a matter of fact, *k*\-Nearest Neighbor (kNN) belongs to the group of metric classifiers that are based on a distance between the objects of a learning sample. This method employs the following ideology: each new object is associated with a most widespread class of its neighbors. Note that one or several neighbors can be considered (e.g., *k* neighbors), with equal weights or different weights depending on the distance to a classified object \[[37](#refbib.xhtml#r37), 194\].

Like other metric classifiers, *k*\-Nearest Neighbor proceeds from the hypothesis of compactness, which claims that similar objects tend to the same class rather than to different classes under an appropriately selected measure of similarity. That is, classes form compactly localized subsets in the space of objects \[[14](#refbib.xhtml#r14)\].

In applications the distance between objects is often defined as the Euclidean distance, which has a high efficiency for numerical attributes. On the other hand, for the problems with categorial (particularly, binary) attributes, *k*\-Nearest Neighbor may give worse results than other classification algorithms, e.g., Decision Tree \[[33](#refbib.xhtml#r33)\].

Another significant factor restricting the applicability of this classifier is related to the curse of dimensionality \[[19](#refbib.xhtml#r19)\]. If a problem has a high dimension and the distance between objects is calculated as the sum of deviations over all attributes, then by the law of large numbers these sums take close values with a high probability. In other words, in a multidimensional space all objects are almost at the same distance from each other, which complicates the choice of an optimal number *k* of neighbors.

In terms of convergence rate, *k*\-Nearest Neighbor demonstrates good results only for relatively small samples. Because the solution rests on known classes for nearest neighbors, for classification of each new object it is necessary to store and calculate distances from this object to all other objects in a learning sample, an extremely difficult procedure for very large amounts of data (*N* >  > 10³) \[[198](#refbib.xhtml#r198)\].

Consequently, despite an intuitive interpretation and a high efficiency in the space of numerical attributes, *k*\-Nearest Neighbor (as well as the other metric classifiers) can be used for a narrow range of classification problems.

### 10.1.3Naive Bayes

The naive Bayesian classifier (in short, Naive Bayes or Simple Bayes) is a special case from a general group of the Bayesian classifiers based on well-known Bayes' theorem and the posterior probability maximization principle \[10, 180\]. For each object under classification, first it is necessary to calculate likelihood functions over each possible class. Using these functions and the probabilities of occurrence for the representatives of different classes, the next step is to calculate the posterior probabilities of the classes themselves. In the final analysis, an object is associated with the class that has the highest posterior probability \[[44](#refbib.xhtml#r44), 57\].

In contrast to the algorithms considered earlier, the Bayesian classifiers allow one to construct a probabilistic model *p*(*c*|*x*[1],*x*[2]…*x*[*n*]) for a variable of class *c* that depends on the variable attributes *x*[1], *x*[2]…*x*[*n*]. Bayes' theorem can be formally stated in the following way:

  
$$\\begin{array}{r} \\left. p(c \\middle| x\_{1},x\_{2}\\ldots x\_{n}) = \\frac{\\left. p(c)p(x\_{1},x\_{2}\\ldots x\_{n} \\middle| c) \\right.}{p(x\_{1},x\_{2}\\ldots x\_{n})}, \\right. \\\\ \\end{array}$$  
(10.1)

where the numerator *p*(*c*)*p*(*x*[1],*x*[2]…*x*[*n*]|*c*) gives the joint probability of the model *p*(*c*, *x*[1], *x*[2]…*x*[*n*]); the denominator *Z* = *p*(*x*[1], *x*[2]…*x*[*n*]), a normalization constant independent of the variable *c*.

Naive Bayes derived its name because it involves the hypothesis of independent object's attributes: in this case, their joint probability can be written as a simple product of all components. Under this hypothesis, formula (10.1) gets simplified to

  
$$\\begin{array}{r} \\left. p(c \\middle| x\_{1},x\_{2}\\ldots x\_{n}) = \\frac{1}{Z}p(c){\\prod\\limits\_{i = 1}^{n}p}(x\_{i}). \\right. \\\\ \\end{array}$$  
(10.2)

Naive Bayes is a classification rule that chooses the class with the maximum posterior probability, i.e.,

  
$$\\begin{array}{r} \\left. C\_{naive} = \\arg\\max\_{c}p(c \\middle| x\_{1},x\_{2}\\ldots x\_{n}). \\right. \\\\ \\end{array}$$  
(10.3)

Therefore, each new object is classified using information about the whole learning sample, more specifically, the likelihood function and the prior probabilities of classes. However, in practice an analytical form of these functions turns out to be unknown, and the likelihood function and the probabilities of classes are empirically restored by a learning sample (note that generally the classes may have different probabilities).

Despite a deviation from the optimal Bayesian classifier \[44\] and the need for an empirical restoration of the functions, Naive Bayes still remains a widespread and efficient classification algorithm, although it tends to be relearned (especially for small learning samples) \[[155](#refbib.xhtml#r155)\].

### 10.1.4Linear classifiers

A linear classifier is a classification algorithm that constructs a linear separating surface in the space of attributes. For a binary classification of two-dimensional objects (two attributes), the separating surface represents a line; for three-dimensional ones, a plane; in the general case, a hypersurface \[57, 180\].

Let the objects from a set *X* be described by numerical attributes *f*[*j*]:*X*→*R*,*j*\=1,…,*n*, in space *R*^(*n*). Denote by *Y* = {−1,1} the set of class labels in the case of binary classification. Then a linear classifier is a classification algorithm *a*:*X*→*Y* of the form

  
$$\\begin{array}{r} {a(x,w) = sign\\left( {{\\sum\\limits\_{j = 1}^{n}w\_{j}}f\_{j}(x) - w\_{0}} \\right) = sign{< {x,w} >},} \\\\ \\end{array}$$  
(10.4)

where  < *x*, *w*\> gives the scalar product of an object's attribute description and a weight vector *w* = (*w*[0], *w*[1], …, *w*[*n*]).

Accordingly, a major goal of machine learning is to “adjust” the weight vector: given a learning sample *X*^(*m*) = {(*x*[1],*y*[1]),…,(*x*[*m*],*y*[*m*])}, it is necessary to construct an algorithm of the above form that minimizes the empirical risk functional

  
$$\\begin{array}{r} \\left. Q(w) = {\\sum\\limits\_{i = 1}^{m}\\left\\lbrack {a(x\_{i},w) \\neq y\_{i}} \\right\\rbrack}\\rightarrow min\_{w}. \\right. \\\\ \\end{array}$$  
(10.5)

For solving the optimization problem (10.5), introduce the margin

  
$$\\begin{array}{r} {M(x\_{i}) = y\_{i}{< {x\_{i},w} >}.} \\\\ \\end{array}$$  
(10.6)

This is a numerical value that characterizes the level of object's immersion into a corresponding class. The smaller is the value *M*(*x*[*i*]), the closer is the object *x*[*i*] to the separating surface of the classes and hence the higher is the probability of classification errors. Since the margin *M*(*x*[*i*]) takes negative values only in case of errors, the empirical risk functional can be written as

  
$$\\begin{array}{r} {Q(w) = {\\sum\\limits\_{i = 1}^{m}\\left\\lbrack {M(x\_{i}) < 0} \\right\\rbrack}.} \\\\ \\end{array}$$  
(10.7)

Therefore, for solving the problem (10.5), we have to find a maximum feasible subsystem in a given system of inequalities. This problem is NP-complete and may possess infinitely many solutions because even a minimum number of errors can be realized on different subsets of objects. However, in most applications there is no practical sense to obtain an exact solution of this problem (to say nothing of all solutions). For proper learning of a classifier, it suffices to get an approximate solution near enough to exact value \[[187](#refbib.xhtml#r187)\].

For a rough solution the threshold loss function is replaced with different continuous approximations

  
$$\\begin{array}{r} {\\left\\lbrack {M < 0} \\right\\rbrack \\leq L(M),} \\\\ \\end{array}$$  
(10.8)

with a subsequent minimization of an upper bound for the empirical risk functional, i.e.,

  
$$\\begin{array}{r} {Q(w) \\leq \\widetilde{Q}(w) = {\\sum\\limits\_{i = 1}^{m}L}\\left( {M(x\_{i}) < 0} \\right).} \\\\ \\end{array}$$  
(10.9)

Introducing a continuous approximation for the loss function, we can employ well-known numerical optimization methods, such as gradient descent and convex programming techniques, which considerably speeds up the learning process. Moreover, in a series of cases, with a continuous approximation it is possible to improve the generalizing capability of a linear classifier \[[105](#refbib.xhtml#r105)\].

Let us mention the common approximation functions *L*(*M*) and the associated methods.

*   **Fisher's Linear Discriminant** is a quadratic approximation of the form
    
      
    $$\\begin{array}{r} {L(M) = {(1 - M)}^{2}.} \\\\ \\end{array}$$  
    (10.10)
    
    Used under the condition that the center vector of a corresponding class is subtracted from the attribute vector of each object \[[52](#refbib.xhtml#r52)\].
    
*   **Single-Layer Perceptron** is an approximation by the sigmoidal function
    
      
    $$\\begin{array}{r} {L(M) = \\frac{2}{1 + e^{\\alpha M}}.} \\\\ \\end{array}$$  
    (10.11)
    
    Often used in neural networks but requires additional heuristics in order to avoid relearning \[122, 187\].
    
*   **Logistic Regression** is a logarithmic approximation of the form
    
      
    $$\\begin{array}{r} {L(M) = \\log(1 + e^{- M}).} \\\\ \\end{array}$$  
    (10.12)
    
    Allows to calculate the probabilities of belonging to different classes. Under rather strong hypotheses on the likelihood functions of the classes, empirical risk minimization with this loss function is equivalent to likelihood maximization \[[73](#refbib.xhtml#r73), 187\].
    
*   **Support Vector Machines** is a piecewise linear approximation of the form
    
      
    $$\\begin{array}{r} {L(M) = \\left( {1 - M} \\right)\_{+}.} \\\\ \\end{array}$$  
    (10.13)
    
    Used together with quadratic regularization. The corresponding optimization problem is solved by special quadratic programming methods \[57, 180\].
    
*   **Exponential Approximation** is given by
    
      
    $$\\begin{array}{r} {L(M) = \\exp( - M).} \\\\ \\end{array}$$  
    (10.14)
    
    Used in boosting algorithms, e.g., AdaBoost \[[56](#refbib.xhtml#r56)\]. Suffers from accentuating on large negative margins, i.e., has a strong sensitivity to data spreads.
    

## 10.2Composition Algorithms

As evidenced by the development of machine learning subject to applications, still there is no unique classification algorithm that would yield best results for any size of learning samples, any dimensionality of the attribute space and any form of the separating surface. This conclusion has motivated research in the field of ensemble machine learning methods, also called composition algorithms.

The key idea of composition algorithms is to unite the forecasts of several basic classifiers, each constructed using an available learning sample \[[163](#refbib.xhtml#r163)\]. Perhaps, a first example of this approach was the Condorcet jury theorem (1784), which states the following: the probability of a correct majority voting-based decision by a jury in which each individual juror has an independent opinion and chooses a correct outcome with a probability greater than 0.5 in increasing with the number of jurors and tends to 1.

Another example of the ensemble approach is the wisdom of crowds (1906), a principle discovered by F. Galton as the result of the following contest. The crowd at a county (nearly 800 people) fair accurately guessed the weight of an ox when their individual guesses were averaged. The average was closer to the ox's true butchered weight than the estimates of most crowd members.

Consider the most widespread methods to construct composition algorithms for classification problems, namely, bagging \[[22](#refbib.xhtml#r22)\] stacking \[[192](#refbib.xhtml#r192)\] and boosting \[56\].

### 10.2.1Bagging

The idea of bagging (bootstrap aggregating) is to reproduce a small learning sample by generating a collection of new random data arrays for further learning. Each sample is then used for the learning of several independent classifiers, and the results are aggregated for obtaining a final high-accuracy forecast.

Bagging algorithms may differ in the methods used to generate subsamples and in the methods used to aggregate or weight the results of basic classifiers. Traditional aggregation methods include simple majority voting, mean and median values, weighted averaging for extracting high-accuracy classifiers, and others \[[79](#refbib.xhtml#r79)\].

A necessary prerequisite for bagging is the choose different basic classifiers with uncorrelated errors. In this case, the errors of the basic classifiers compensate each other, which yields a much better forecast \[22\].

In this context, also note the random subspace method (RSM) \[163\], which differs from standard bagging in the following feature: random samples are generated also using random subsets from an attribute description of objects. This method has a high efficiency under redundant spurious attributes and a relatively small size of a learning sample.

### 10.2.2Stacking

The concept of stacking further develops the idea of an aggregated generalization for the results yielded by basic classifiers, but with a separate auxiliary model that is learned on their forecasts.

As a rule, for stacking a learning sample is divided into two subsamples, the first being intended for the learning of independent basic classifiers whereas the second for their testing. After that, the forecasts of the basic classifiers and the true answers are used as input data for the learning of a meta-classification model \[192\].

Among the benefits of stacking, we mention a possible design of nonlinear combinations of basic classifiers for high-accuracy forecasting.

### 10.2.3Boosting

Boosting is an iterative sequential improvement procedure for a composition of basic classifiers by constructing a weighted learning subsample using an initial sample. At each new iteration, higher weights are assigned to the replicates yielding incorrect results for a previous composition. The algorithm is therefore accentuated on most difficult replicates from a learning sample.

The concept of boosting also employs basic classifiers but, unlike bagging, at each successive iteration a learning sample is defined by the classification results at the previous iterations (not randomly). Such an approach turns out to be much more efficient even with weak basic classifiers \[[25](#refbib.xhtml#r25)\].

Due to simple implementation, universalism and, above all, good capability for generalization, boosting algorithms still remain most popular machine learning methods, together with Support Vector Machines (SVM) and neural networks. A drawback of boosting is traditionally tough requirements applied to the size of a learning sample (10⁴–10⁶ replicates) \[187\].

## 10.3Entropy Classification

Now let us describe the entropy-robust approach to the learning of classifiers. This approach differs from the traditional machine learning problems in the optimization statement and also fruitfully combines the advantages of the classical individual classifiers and ensemble methods.

### 10.3.1Problem formulation

Consider a given collection of objects to be distributed between two classes. Divide all available data into two samples, namely, a learning sample ℰ = {*e*[1],…,*e*[*h*]} and a testing sample 𝒯 = {*t*[1],…*t*[*r*]}. The percentage of objects in these samples (subcollections) will be discussed below.

The objects in both subcollections have a vector representation; for each object, the elements of a corresponding vector are variables-attributes characterizing it, i.e.,

  
$$\\begin{array}{r} {\\mathcal{E} = \\left\\{ \\mathbf{e}^{(1)},\\ldots,\\mathbf{e}^{(h)} \\right\\},\\text{\\quad\\quad}\\mathcal{T} = \\left\\{ \\mathbf{t}^{(1)},\\ldots,\\mathbf{t}^{(r)} \\right\\}.} \\\\ \\end{array}$$  
(10.15)

Our analysis will be confined to the quantitative attributes only but the suggested method can be extended to the case of categorial attributes.

The vectors of both subcollections have the same dimension: (**e**^((*i*)), **t**^((*j*))) ∈ *R*^(*n*). The subcollection ℰ is used for learning whereas the subcollection 𝒯 for testing.

The objects in both subcollections are labeled in accordance with their belonging to an appropriate class: if an object *e*[*l*] or *t*[*k*] is a member of the first (second) class, then it has label 1 (label 0, respectively). Hence, the learning subcollection is characterized by a vector of answers **y** = {*y*[1],…,*y*[*h*]} composed of ones and zeros; the testing subcollection, by an answer vector **z** = {*z*[1],…,*z*[*r*]}. The indexes of elements in these vectors correspond to the indexes of objects in the learning and testing samples.

The classifier learning problem is to design an algorithm *a*:ℰ→*y* that restores the class of an object using its attribute description based on a learning sample.

### 10.3.2Learning stage

Due to the availability of a learning subcollection, we can hypothesize the existence of a function (some decision rule) *F*:ℰ→**y**. The learning problem consists in choosing an appropriate form and parameters of an approximate function *F̂*(**a**). The function *F̂*(**a**) represents a decision rule model.

Following the entropy classification concept, a decision rule is described by a randomized parametric model (RPM), i.e., a model with randomized parameters **a**. It has the input vectors {**e**^((1)),…,**e**^((*h*))} and the output $\\hat{\\mathbf{y}}(\\mathbf{a})$ that depends on the randomized parameters **a**.

As such a model choose a single-layer perceptron \[[63](#refbib.xhtml#r63)\], i.e.,

  
$$\\begin{array}{r} {{\\hat{y}}^{(i)}(\\mathbf{a}) = \\text{sigm}\\,\\left( \\left\\langle \\mathbf{e}^{(i)},\\mathbf{a} \\right\\rangle \\right),\\text{\\quad\\quad}i = \\overline{1,n},} \\\\ \\end{array}$$  
(10.16)

where

  
$$\\begin{aligned} {\\text{sigm}(x\_{i})} & {= \\frac{1}{1 + \\exp\\lbrack - \\alpha(x\_{i} - \\Delta)\\rbrack},} \\\\ x\_{i} & {= \\left( \\left\\langle \\mathbf{e}^{(i)},\\mathbf{b} \\right\\rangle \\right),} \\\\ \\mathbf{a} & {= \\left\\{ \\mathbf{b},\\alpha,\\Delta \\right\\}.} \\\\ \\end{aligned}$$  
(10.17)

A graph of the sigmoidal function with the slope *α* and threshold Δ parameters is shown in [Fig. 10.1](#chapter10.xhtml#f10_1). The values of the function sigm(*x*) within the interval \[1/2, 1\] correspond to the first class; within the interval \[0, 1/2), to the second class.

![Figure 10.1: Structure of single-layer neural network.](images/fig10_1.jpg)

[Figure 10.1:](#chapter10.xhtml#f10_1b) Structure of single-layer neural network.

In the randomized model (10.16, 10.17), the parameters **a** = {*a*[1],…,*a*[(*n* + 2)]} are of the interval type and their probabilistic properties are characterized by a joint probability density function *P*(**a**) on a set 𝒜, i.e.,

  
$$\\begin{aligned} a\_{k} & {\\in \\mathcal{A}\_{k} = \\lbrack a\_{k}^{-},a\_{k}^{+}\\rbrack,\\text{\\quad\\quad}k = \\overline{1,n+2},} \\\\ \\mathcal{A} & {= \\otimes\_{k = 1}^{n + 2}\\mathcal{A}\_{k}.} \\\\ \\end{aligned}$$  
(10.18)

Since the parameters **a** have a random character, for each object *e*[*i*] there is an ensemble ${\\hat{\\mathcal{Y}}}^{(i)}$ of random numbers *ŷ*^((*i*))(**a**) from the interval \[0,1\]. Define its mean value as

  
$$\\begin{array}{r} {\\mathcal{M}\\left\\{ {\\hat{y}}^{i}(\\mathbf{a}) \\right\\} = {\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\text{sigm}\\,\\left( \\left\\langle \\mathbf{e}^{(i)},\\mathbf{a} \\right\\rangle \\right)d\\mathbf{a},\\text{\\quad\\quad}i = \\overline{1,h}.} \\\\ \\end{array}$$  
(10.19)

Consequently, according to the general RML procedure \[[144](#refbib.xhtml#r144), [150](#refbib.xhtml#r150)\], the classification problem can be written as follows:

  
$$\\begin{array}{r} \\left. \\mathcal{H}\\lbrack P(\\mathbf{a})\\rbrack = - {\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\,\\ln P(\\mathbf{a})d\\mathbf{a}\\Rightarrow\\max \\right. \\\\ \\end{array}$$  
(10.20)

subject to

*   the PDF normalization conditions
    
      
    $$\\begin{array}{r} {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})d\\mathbf{a} = 1} \\\\ \\end{array}$$  
    (10.21)
    
    and
    
*   the output balance constraints
    
      
    $$\\begin{array}{r} {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\text{sigm}\\,\\left( \\left\\langle \\mathbf{e}^{(i)},\\mathbf{a} \\right\\rangle \\right)d\\mathbf{a} = y\_{i},\\text{\\quad\\quad}i = \\overline{1,h},} \\\\ \\end{array}$$  
    (10.22)
    

where *P*(**a**) belongs to the class *ℂ*¹ of all continuously differentiable functions.

Equations (10.20–10.22) make up a functional entropy-linear programming problem, which possesses an analytical solution—the entropy-optimal PDF *P*^(\*)(**a** | *θ*) parameterized by the Lagrange multipliers *θ*, i.e.,

  
$$\\begin{array}{r} \\left. P^{\*}(\\mathbf{a}\\, \\middle| \\,\\theta) = \\frac{\\exp\\left\\lbrack {- {\\sum\\limits\_{i = 1}^{h}\\theta\_{i}}{\\hat{y}}^{(i)}(\\mathbf{a})} \\right\\rbrack}{\\mathcal{P}(\\theta)}, \\right. \\\\ \\end{array}$$  
(10.23)

where *ŷ*^((*i*))(**a**) is given by (10.2) and

  
$$\\begin{array}{r} {\\mathcal{P}(\\theta) = {\\int\_{\\mathcal{A}}\\exp}\\left\\lbrack {- {\\sum\\limits\_{i = 1}^{h}\\theta\_{i}}{\\hat{y}}^{(i)}(\\mathbf{a})} \\right\\rbrack.} \\\\ \\end{array}$$  
(10.24)

The Lagrange multipliers are calculated from the balance constraints (10.22). Here a possible approach lies in the *L*²\-norm minimization of a general residual function for equations (10.22).

### 10.3.3Testing stage

This stage utilizes the testing subcollection 𝒯 of objects that are characterized by the answer vector **z** = {*z*[1],…,*z*[*r*]} with a known classification (their belonging to the first or second class). The vector **z** will be used for a quality assessment of the testing procedure. The latter itself involves the subcollection 𝒯 and also the decision rule model yielded by the learning stage.

It is necessary to test the randomized decision rule (10.16, 10.17) with the entropy-optimal PDF of the model parameters according to formulas (10.23, 10.24). The procedure performs a sequence of Monte Carlo simulations of size *N*, generating in each simulation a random vector **a** that obeys the entropy-optimal PDF *P*^(\*)(**a**).

Assume that, as the result of such simulations, the first object from the testing subcollection has been assigned *N*[1] times to the first class and *N* − *N*[1] times to the second class, …, the *k*th object has been assigned *N*[*k*] times to the first class and *N* − *N*[*k*] times to the second class, and so on. Under a sufficiently large number of simulations, define the empirical probabilities

  
$$\\begin{aligned} p\_{1}^{(1)} & {= \\frac{N\_{1}}{N},\\ldots,p\_{1}^{(k)} = \\frac{N\_{k}}{N},\\ldots,...} \\\\ p\_{2}^{(1)} & {= \\frac{N - N\_{1}}{N},\\ldots,p\_{2}^{(k)} = \\frac{N - N\_{k}}{N},\\ldots,...} \\\\ \\end{aligned}$$  
(10.25)

Therefore, for each object *i* from the testing sample, the testing algorithm can be written in the following form.

*Step 1-i.* In accordance with the optimal PDF, generate a set of output values for the entropy-optimal decision rule model (10.23, 10.24), which contains *N* random numbers from the interval {0,1}.

*Step 2-i.* For each realization of the model (i.e., for each parameter vector from the ensemble of size *N*), calculate the decision rule values using formulas (10.16, 10.17). If the resulting value exceeds 1/2, then the object *t*^((*i*)) is assigned to the first class; otherwise, to the second class.

*Step 3-i.* Find the empirical probabilities of belonging to these classes by formula (10.25).

With this procedure each object can be assigned to one of the two classes with a definite probability, which reflects an inherent uncertainty of the available data and also of the approximate decision rule model.

Note that, as a rule, the objects of the learning and testing subcollections are considered to be independent replicants. Under this assumption, Step 1-i can be organized as a common preliminary procedure to generate a set of random variables, which will be used in the same way for all testing objects.

Transition to hard classification can be performed by introducing a threshold probability above which an object is assigned to a corresponding class. The number of objects for a correct hard classification depends on this threshold. As easily established, some objects are not classified for the thresholds exceeding 0.5 but the results of classification have a higher reliability. On the other hand, for the thresholds less than 0.5, all objects are classified (as the sum of both probabilities is 1) but the results may resemble guessing if the probabilities of belonging are close to each other.

### 10.3.4Numerical examples

**1. Classification of four-dimensional objects**

Consider the objects characterized by four attributes, i.e., the elements of the vectors **e** and **t**.

Let the learning sample consist of three objects, each being described by four attributes (see [Table 10.1](#chapter10.xhtml#t10_1)).

 [Table 10.1](#chapter10.xhtml#t10_1b) 

 
|  |
| --- |
| *i* || *e*[1]^((*i*)) || *e*[2]^((*i*)) || *e*[3]^((*i*)) || *e*[4]^((*i*)) |
|  |
| --- |
| 1 || 0.11 || 0.75 || 0.08 || 0.21 |
| 2 || 0.91 || 0.65 || 0.11 || 0.81 |
| 3 || 0.57 || 0.17 || 0.31 || 0.91 |
|  |

The randomized decision rule model (10.16, 10.17) has the parameters *α* = 1.0 and *Δ* = 0. The learning answer vector is **y** = {0.18; 0.81; 0.43} (as before, *y*[*i*] < 0.5 corresponds to the second class and *y*[*i*] ≥ 0.5 to the first class). The Lagrange multipliers for the entropy-optimal PDF (10.23) take the values ${\\overline{\\theta}}^{\*} = \\left\\{ 0.2524;\\, 1.7678;\\, 1.6563 \\right\\}.$ The parameters belong to the intervals $a\_{i} \\in \\lbrack - 10,10\\rbrack,\\, i = \\overline{1,4}.$

For this learning subcollection, the entropy-optimal PDF has the form

  
$$\\begin{aligned} & {\\quad P^{\*}(\\mathbf{a},\\overline{\\theta}) = \\frac{\\exp\\left( {- {\\sum\\limits\_{i = 1}^{3}\\theta\_{i}}y\_{i}(\\mathbf{a})} \\right)}{\\mathcal{P}(\\overline{\\theta})},} \\\\ & {y\_{i}(\\mathbf{a}) = \\left( {1 + \\exp( - {\\sum\\limits\_{k = 1}^{4}e\_{k}^{(i)}},a\_{k})} \\right)^{( - 1)}.} \\\\ \\end{aligned}$$  
(10.26)

The two-dimensional cutset of the PDF $P^{\*}(\\mathbf{a},{\\overline{\\theta}}^{\*})$ with fixed values of the third and fourth dimensions is illustrated in [Fig. 10.2](#chapter10.xhtml#f10_2).

![Figure 10.2: Two-dimensional cutset of entropy-optimal PDF P^{\*}(\\mathbf{a},{\\overline{\\theta}}^{\*}).](images/fig10_2.jpg)

[Figure 10.2:](#chapter10.xhtml#f10_2b) Two-dimensional cutset of entropy-optimal PDF $P^{\*}(\\mathbf{a},{\\overline{\\theta}}^{\*})$.

Let us demonstrate the mechanism to obtain forecasts for new objects using the learned model. At this stage, utilize a subcollection 𝕋 = {*t*[1],…,*t*[*r*]} of objects in which each element is characterized by a vector **t**^((*j*)) ∈ *R*^((4)). First, generate an array of dimensions (500 × 4) consisting of four-dimensional random vectors $\\mathbf{t}^{(i)},\\, i = \\overline{1,500},$ with independent uniformly distributed elements on the interval \[0, 1\]. Then apply the classification algorithm described in the testing stage subsection.

The empirical probabilities *p*[1]^((*i*)), *p*[2]^((*i*)) of belonging of an object *t*[*i*] to the first and second classes are presented in [Fig. 10.3](#chapter10.xhtml#f10_3).

![Figure 10.3: Empirical probabilities of belonging to different classes for Example 1.](images/fig10_3.jpg)

[Figure 10.3:](#chapter10.xhtml#f10_3b) Empirical probabilities of belonging to different classes for Example 1.

For each replicant, the soft classification procedure has assigned the probabilities of object's belonging to the first and second classes. Note that the sum of these probabilities is 1 for each object.

Further decision-making (hard classification, i.e., assignment of each object to an appropriate class) is possible by introducing some threshold of “reliable classification.” For example, choose a threshold of 0.75; then all objects belonging to the first class with a probability higher than 0.75 (or the ones belonging to the second class with a probability less than 0.25) are assigned to the former class with some level of reliability.

The level of reliability is specified for each new classification problem individually. It represents one of the hyperparameters of the algorithm and is often adjusted using cross validation or sliding control \[118, 187\].

**2. Classification of two-dimensional objects**

Consider a more visual example of classification of two-dimensional random objects.

Let the objects of the learning sample from Example 1 be characterized by the first two components of their attribute description. The learning sample consists of three objects, each being described by two attributes (see [Table 10.1](#chapter10.xhtml#t10_1)). The values of the parameters *α* and *Δ*, as well as the intervals of the random parameters **a**, are the same as in Example 1.

Solving the system of equations (10.22) with the entropy-optimal PDF (10.23) yields the Lagrange multipliers ${\\overline{\\theta}}^{\*} = \\left\\{ 9.6316, - 18.5996 \\right.$, 16.7502}. For this learning subcollection, the entropy-optimal PDF $\\left. P^{\*}(\\mathbf{a}\\, \\middle| \\,\\overline{\\theta}) \\right.$ has the form

  
$$\\begin{aligned} & {\\quad P^{\*}(\\mathbf{a}) = \\frac{\\exp\\left( {- {\\sum\\limits\_{i = 1}^{3}\\theta\_{i}}y\_{i}(\\mathbf{a})} \\right)}{\\mathcal{P}(\\overline{\\theta})},} \\\\ & {y\_{i}(\\mathbf{a}) = \\left( {1 + \\exp( - {\\sum\\limits\_{k = 1}^{2}e}{(i)}\_{k},a\_{k})} \\right)^{( - 1)}.} \\\\ \\end{aligned}$$  
(10.27)

The entropy-optimal PDF $P^{\*}(\\mathbf{a},{\\overline{\\theta}}^{\*})$ is shown in [Fig. 10.4](#chapter10.xhtml#f10_4).

![Figure 10.4: Two-dimensional entropy-optimal PDF P^{\*}(\\mathbf{a},{\\overline{\\theta}}^{\*}).](images/fig10_4.jpg)

[Figure 10.4:](#chapter10.xhtml#f10_4b) Two-dimensional entropy-optimal PDF $P^{\*}(\\mathbf{a},{\\overline{\\theta}}^{\*})$.

By analogy with Example 1, use a sample of 500 random objects described by a two-dimensional vector with the independent uniform distribution on the interval \[0, 1\]. The other parameters are the same as in Example 1. The empirical probabilities *p*[1]^((*i*)), *p*[2]^((*i*)) of belonging of an object *t*[*i*] to the first and second classes are presented in [Fig. 10.5](#chapter10.xhtml#f10_5).

![Figure 10.5: Empirical probabilities of belonging to different classes for Example 2.](images/fig10_5.jpg)

[Figure 10.5:](#chapter10.xhtml#f10_5b) Empirical probabilities of belonging to different classes for Example 2.

Like for Example 1, the graphs in [Fig. 10.5](#chapter10.xhtml#f10_5) have a considerable spread of the empirical probabilities of belonging. This is caused by an intentionally small size of the learning sample. However, these results are much better than random guessing.

To show this, place all random objects under classification on the same diagram and choose a level of reliability for their hard classification. Red color will be used for all objects related to the first class and green color for the ones related to the second class. In addition, color intensity will indicate how large has been the empirical probability for a given object in the case of soft classification. The hard classification results of the objects are presented in [Fig. 10.6](#chapter10.xhtml#f10_6) for thresholds 0.5 (top) and 0.4 (bottom).

![Figure 10.6: Classification diagram for Example 2.](images/fig10_6.jpg)

[Figure 10.6:](#chapter10.xhtml#f10_6b) Classification diagram for Example 2.

The classification results on this diagram testify that the limits between the groups of objects from the same class are refined depending on the level of reliability. This allows us to separate out the domains of the bright red- and green-color points (the first and second classes). In both cases, the objects of a corresponding class are located around the learning objects inside the black circles.

Consequently, a proper variation of the level of reliability gives a possible mechanism for the statistical treatment of entropy soft classification results.

# CHAPTER 11 RANDOMIZED MACHINE LEARNING IN PROBLEMS OF DYNAMIC REGRESSION AND PREDICTION

DOI: [10.1201/9781003306566-11](https://doi.org/10.1201/9781003306566-11)

The restoration of relations between two groups of variables is a basic class of problems arising in econometric research. Generally, these problems are treated as *static regression problems*, which involve retrospective data. In many cases one needs to restore a relation and also to forecast its future dynamics. As “future” data are unavailable for some period of time, such forecasts assist in making more or less reasonable decisions. An obvious recommendation here is to use *dynamic regressions*, which have a remarkable property of looking into the future. In other words, given some initial conditions at a time *t*[0], a dynamic regression generates trajectories on a time interval \[*t*[0], *t*\], where *t* > *t*[0]. A dynamic regression rests on a parameterized dynamic model with a two-stage procedure as follows. First, like for a static regression, it is necessary to estimate regression parameters based on retrospective data on a time interval \[*t*[−], *t*[0]\], where *t*[−] < *t*[0]. In fact, this stage implements machine learning of the model. Then, the resulting model acts as a generator of forecasted trajectories on a second time interval \[*t*[0], *t*[+]\].

In this chapter, we will apply RML procedures for estimating the probabilistic characteristics of parameterized dynamic models. Recall that the general concept of randomized machine learning employs randomized parameters with entropy-optimal PDFs. Due to this circumstance, a randomized dynamic model generates an ensemble of entropy-optimal

## 11.1Restoration of Dynamic Relationships in Applications

Many real processes are dynamic in the sense that at each time their state depends on the past states on some time interval, often considered as memory. Researchers often discriminate between processes with finite and infinite memory. The latter case is convenient for mathematical analysis whereas the hypothesis about finite memory is efficient for a numerical study of a process. In the sequel, the term “processes” will indicate dynamic processes.

A process *Y*(*t*) is generated by some object in accordance with an internal transformation mechanism of observable input actions *X*(*τ*), *τ* ∈ 𝒯 and unobservable factors *F*(*t*) with hypothetical properties. Recall that a rather general descriptive formalism for a dynamic process is a functional ℬ\[*X*(*τ*), *F*(*τ*); *τ* ∈ 𝒯\] that characterizes a relation between the object's output at a time *t* and its input *x*(*τ*) and factors *F*(*τ*) on a time interval 𝒯 = \[*t*[−], *t*\], i.e.,

  
$$\\begin{array}{r} {Y(t) = \\mathcal{B}\\lbrack X(\\tau),F(\\tau);\\,\\tau \\in \\mathcal{T}\\rbrack,\\text{\\quad\\quad}t \\geq t\_{-}.} \\\\ \\end{array}$$  
(11.1)

The need to model the relation (11.1) occurs in many applications. Consider some of them in detail.

## 11.2Randomized Model of World Population Dynamics

The state of World population is characterized by its size *E*(*t*) measured in *billions of people* on a calendar time. The population size $v(t) = \\frac{dE(t)}{dt}$ varies due to the impact of fertility and mortality processes, since World population is an isolated system. Fertility and mortality are measured by the numbers of newborns *B* and decedents *M* per unit time (the flows of newborns and decedents, respectively):

  
$$\\begin{array}{r} {B(E) = bE,\\text{\\quad\\quad}M(E) = mE.} \\\\ \\end{array}$$  
(11.2)

The birth *b* and mortality *m* coefficients change during observation, i.e., are time-varying functions

  
$$\\begin{array}{r} {b = b(t),\\text{\\quad\\quad}m = m(t).} \\\\ \\end{array}$$  
(11.3)

As a first approximation, consider the linear functions

  
$$\\begin{array}{r} {b(t) = b\_{0} + b\_{1}t,\\text{\\quad\\quad}m(t) = m\_{0} + m\_{1}t.} \\\\ \\end{array}$$  
(11.4)

Consequently, the flows of fertility and mortality depend on time:

  
$$\\begin{array}{r} {B(t) = (b\_{0} + b\_{1}t)E(t),\\text{\\quad\\quad}M(t) = (m\_{0} + m\_{1}t)E(t).} \\\\ \\end{array}$$  
(11.5)

The difference between these flows, the so-called reproduction flow, determines the dynamics of the population size, which are described by the following differential equation with variable coefficients:

  
$$\\begin{array}{r} {\\frac{dE(t)}{dt} = (r + ut)E(t),\\text{\\quad\\quad}r = b\_{0} - m\_{0},\\quad u = b\_{1} - m\_{1};\\,\\,\\, E(t\_{0}) = E\_{0}.} \\\\ \\end{array}$$  
(11.6)

Here *t*[0] and *E*[0] denote the initial time and initial population size, respectively; the parameter *r* characterizes the constant component of the population reproduction rate and parameter *u* its rate of change over time.

Equation (11.6) with the initial condition *E*[0] has the solution

  
$$\\begin{array}{r} {E(t) = E\_{0}\\exp\\left( {(r + ut)t} \\right).} \\\\ \\end{array}$$  
(11.7)

The measurements of population size are performed on a calendar time with a step *h*. According to the UN standard, *h* = 5 years. Then *t* = *t*[0] + *n**h*, and

  
$$\\begin{array}{r} \\left. E\\lbrack t\_{0} + nh\\rbrack = E\_{0}\\exp\\left( {(r + uhn)nh} \\right) = E\\lbrack t\_{0} + nh\\, \\middle| \\, r,u,E\_{0}\\rbrack,\\quad n = 0,1,.... \\right. \\\\ \\end{array}$$  
(11.8)

The fertility and mortality coefficients are estimated through indirect measurements that contain errors. Thus, the resulting flow rate and its change over time are supposed to be random variables defined on the intervals

  
$$\\begin{array}{r} {\\mathcal{J}\_{r} = \\lbrack r^{-},r^{+}\\rbrack,\\text{\\quad\\quad}\\mathcal{J}\_{u} = \\lbrack u^{-},u^{+}\\rbrack.} \\\\ \\end{array}$$  
(11.9)

The values inside these intervals are characterized by a joint probability density function (PDF) *P*(*r*, *u*) defined on the rectangle

  
$$\\begin{array}{r} {\\mathcal{J} = \\mathcal{J}\_{r}{\\cup \\mathcal{J}\_{u}}.} \\\\ \\end{array}$$  
(11.10)

The parameters of the model (11.8) are estimated by measuring the real population size *E*[*r**e**a**l*]\[*n**h*\] on some time interval. These measurements have errors simulated by random noises *ξ*\[*n**h*\] = *ξ*[*n*], which are specified on the corresponding intervals *Ξ*[*n*] = \[*ξ*[*n*]^−, *ξ*[*n*]^+\]. The noises are supposed to be independent with a PDF *q*[*n*](*ξ*[*n*]), i.e., their joint PDF on the observation interval \[0,*N\]* is given by

  
$$\\begin{array}{r} {Q(\\overline{\\xi}) = {\\prod\\limits\_{n = 0}^{N}q\_{n}}(\\xi\\lbrack nh\\rbrack).} \\\\ \\end{array}$$  
(11.11)

Therefore, the *randomized* model of World population dynamics can be described by

  
$$\\begin{array}{r} \\left. v\\lbrack t\_{0} + nh\\rbrack = E\\lbrack t\_{0} + nh\\, \\middle| \\, r,u,E\_{0}\\rbrack + \\xi\\lbrack nh\\rbrack,\\text{\\quad\\quad}n = 0,1,... \\right. \\\\ \\end{array}$$  
(11.12)

This RM is a basis of RML procedures for estimating the PDFs *P*(*r*, *u*) (parameters) and $Q(\\overline{\\xi})$ (noises), testing and randomized forecasting of World population. In all stages, retrospective data are used:

*   on the estimation interval 𝒯[*e**s**t*] = \[1960 − 1995\] (see [Table 11.1](#chapter11.xhtml#t11_1));
    
*   on the testing interval 𝒯[*t**s**t*] = \[1995 − 2015\] (see [Table 11.2](#chapter11.xhtml#t11_2)). These are the UN forecast data announced in 1985 (*E*[1985]^(*p**r**n*)).
    
*   on the forecasting interval 𝒯[*f**r**c*] = \[2015 − 2050\] (see [Table 11.3](#chapter11.xhtml#t11_3)).
    
     [Table 11.1:](#chapter11.xhtml#t11_1b) Estimation interval 𝒯[*e**s**t*]. 
    
     
    |  |
    | --- |
    | *n* || 0 || 1 || 2 || 3 || 4 || 5 || 6 |
    | year || 1960 || 1965 || 1970 || 1975 || 1980 || 1985 || 1990 |
    | --- | --- | --- | --- | --- | --- | --- | --- |
    | *E*[*r**e**a**l*]^(*e**s**t*) || 3.026 || 3.358 || 3.691 || 4.070 || 4.449 || 4.884 || 5.320 |
    |  |
    
     
    
    [Table 11.2:](#chapter11.xhtml#t11_2b) Testing interval 𝒯[*t**s**t*].
    
     
    |  |
    | --- |
    | *n* || 0 || 1 || 2 || 3 || 4 |
    | year || 1995 || 2000 || 2005 || 2010 || 2014 |
    | --- | --- | --- | --- | --- | --- |
    | *E*[*r**e**a**l*]^(*t**s**t*) || 5.724 || 6.128 || 6.514 || 6.916 || 7.260 |
    | *E*[1985]^(*p**r**n*) || 5,400 || 5,968 || 6,596 || 7,284 || 8,056 |
    |  |
    
     
    
    [Table 11.3:](#chapter11.xhtml#t11_3b) Forecasting interval 𝒯[*f**r**c*].
    
     
    |  |
    | --- |
    | *n* || 0 || 1 || 2 || 3 || 4 || 5 || 6 |
    | year || 2015 || 2020 || 2025 || 2030 || 2040 || 2050 || 2060 |
    | --- | --- | --- | --- | --- | --- | --- | --- |
    | *E*[*U**N*]^(*f**r**c*) || 7.324 || 7.644 || 7.964 || 8.284 || 8.924 || 9.564 || 9.884 |
    |  |
    
    In all stages, the simulated data were generated with the corresponding initial values:
    
    *   on the estimation interval,
        
          
        $$\\begin{array}{r} \\left. v\\lbrack 1960 + nh\\rbrack = E\\lbrack 1960 + 5n\\, \\middle| \\, r,u,E\_{real}^{est}\\lbrack 0\\rbrack\\rbrack + \\xi\\lbrack 5n\\rbrack,\\text{\\quad\\quad}n = \\lbrack 0,7\\rbrack; \\right. \\\\ \\end{array}$$  
        (11.13)
        
    *   on the testing interval,
        
          
        $$\\begin{array}{r} \\left. v\\lbrack 1995 + nh\\rbrack = E\\lbrack 1995 + 5n\\, \\middle| \\, r,u,E\_{real}^{tst}\\lbrack 0\\rbrack\\rbrack + \\xi\\lbrack 5n\\rbrack,\\text{\\quad\\quad}n = \\lbrack 0,4\\rbrack; \\right. \\\\ \\end{array}$$  
        (11.14)
        
    *   on the forecasting interval,
        
          
        $$\\begin{array}{r} \\left. v\\lbrack 2015 + nh\\rbrack = E\\lbrack 2015 + 5n\\, \\middle| \\, r,u,E\_{real}^{prn}\\lbrack 0\\rbrack\\rbrack + \\xi\\lbrack 5n\\rbrack,\\text{\\quad\\quad}n = \\lbrack 0,5\\rbrack. \\right. \\\\ \\end{array}$$  
        (11.15)
        
    
    ### 11.2.1RML procedure for learning of World Population Dynamics Model
    
    According to the concept of Randomized Machine Learning entropy-optimal PDFs of parameters and noises will have the following form:
    
    *   PDF of the reproduction coefficient *r* and its speed *u*
        
          
        $$\\begin{aligned} & \\left. P^{\*}(r,u) = \\frac{1}{\\mathcal{R}(\\overline{\\theta})}{\\prod\\limits\_{n = 0}^{7}p\_{n}^{\*}}(r,u \\middle| \\theta\_{n}), \\right. \\\\ \\left. p\_{n}^{\*}(r,u \\middle| \\theta\_{n}) = \\right. & {\\exp\\left( - \\theta\_{n}E\\lbrack 1960 + nh\\, \\middle| \\, r,u,E\_{real}^{est}\\lbrack 0\\rbrack\\rbrack \\right);} \\\\ \\end{aligned}$$  
        (11.16)
        
    *   PDF of the noise
        
          
        $$\\begin{array}{r} \\left. Q^{\*}(\\overline{\\xi}) = \\frac{1}{\\mathcal{Q}(\\overline{\\theta})}{\\prod\\limits\_{n = 0}^{7}q\_{n}^{\*}}(\\xi\\lbrack nh\\rbrack \\middle| \\theta\_{n}),\\quad q\_{n}^{\*}(\\xi\\lbrack nh\\rbrack \\middle| \\theta\_{n}) = \\exp\\left( {- \\theta\_{n}\\xi\\lbrack nh\\rbrack} \\right), \\right. \\\\ \\end{array}$$  
        (11.17)
        
        where
        
          
        $$\\begin{aligned} {\\mathcal{R}(\\overline{\\theta})} & {= {\\int\_{\\mathcal{J}}{\\prod\\limits\_{n = 0}^{7}\\exp}}( - \\theta\_{n}E\\lbrack 1960 +} \\\\ & \\left. + nh\\, \\middle| \\, r,u,E\_{real}^{est}\\lbrack 0\\rbrack\\rbrack)drdu, \\right. \\\\ {\\mathcal{Q}(\\overline{\\theta}) =} & {{\\prod\\limits\_{n = 0}^{7}\\int^{\\Xi\_{n}}}\\exp( - \\theta\_{n}\\xi\\lbrack nh\\rbrack)d\\xi\\lbrack nh\\rbrack =} \\\\ {= {\\prod\\limits\_{n = 0}^{7}\\frac{1}{\\theta\_{n}}}} & {\\left( {\\exp( - \\theta\_{n}\\xi\_{n}^{-}) - \\exp( - \\theta\_{n}\\xi\_{n}^{+})} \\right).} \\\\ \\end{aligned}$$  
        (11.18)
        
    
    Lagrange multipliers are determined by the system of balance equations (1.9, 1.10):
    
      
    $$\\begin{aligned} & \\left. \\text{\\quad\\quad}\\text{\\quad\\quad}\\frac{1}{\\mathcal{R}(\\overline{\\theta})}{\\int\_{\\mathcal{J}}E}\\lbrack 1960 + nh\\, \\middle| \\, r,u,E\_{real}^{est}\\lbrack 0\\rbrack\\rbrack \\times \\right. \\\\ & {\\quad \\times {\\prod\\limits\_{n = 0}^{7}\\exp}\\left( - \\theta\_{n}E\\lbrack 1960 + nh\\, \\middle| \\, r,u,E\_{real}^{est}\\lbrack 0\\rbrack\\rbrack \\right)\\, dr\\, du +} \\\\ & {\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad + \\frac{1}{\\mathcal{Q}(\\overline{\\theta})}{\\int\_{\\Xi\_{n}}\\xi}\\lbrack nh\\rbrack \\times} \\\\ & {\\times {\\prod\\limits\_{n = 0}^{7}\\exp}\\left( {- \\theta\_{n}\\xi\\lbrack nh\\rbrack} \\right)d\\xi\\lbrack nh\\rbrack - E\_{real}^{est}\\lbrack nh\\rbrack = G\_{n}(\\overline{\\theta}) = 0,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}n = \\overline{0,7}.} \\\\ \\end{aligned}$$  
    (11.19)
    
    To solve this system, the method of minimizing the residual is used.
    
      
    $$\\begin{array}{r} \\left. J(\\overline{\\theta}) = \\|\\mathbf{G}(\\overline{\\theta})\\|\\Rightarrow\\min. \\right. \\\\ \\end{array}$$  
    (11.20)
    
    ### 11.2.2Numerical results
    
    **1. General conditions**
    
    All stages of estimation, testing and forecasting are implemented on intervals for coefficients of reproduction and trend, which simulate both the growth and the fall of the values of these parameters
    
      
    $$\\begin{array}{r} {\\mathcal{J}\_{r} = \\lbrack - 0.025, - 0.075\\rbrack,\\text{\\quad\\quad}\\mathcal{J}\_{u} = \\lbrack 0.002,0.001\\rbrack.} \\\\ \\end{array}$$  
    (11.21)
    
    It is assumed that the values of the measurement noise for each observation are the same and belong to the interval
    
      
    $$\\begin{array}{r} {\\Xi\_{n} = \\lbrack - 0.5,0.5\\rbrack,\\text{\\quad\\quad}n = \\overline{0,7}.} \\\\ \\end{array}$$  
    (11.22)
    
    After the entropy-optimal PDFs of parameters and noise have been found, trajectories *E*(*t*) with random parameters and noises with that PDFs are generated.
    
    **2. Estimation**
    
    To implement the RML procedure, the data of the world population dynamics are used (see [Table 11.1](#chapter11.xhtml#t11_1)). The residual function $J(\\overline{\\theta})$ (11.20) is a function of 8 variables and contains two-dimensional integral components, the values of which can be estimated only numerically. To calculate them, we used the \[[164](#refbib.xhtml#r164)\] quadrature formulas, implemented in MATLAB *guad2d* function. The residual was minimized using the *lsqnonlin* function from MATLAB Optimization Toolbox. The obtained values of the Lagrange multipliers are given in the [Table 11.4](#chapter11.xhtml#t11_4).
    
     [Table 11.4:](#chapter11.xhtml#t11_4b) Lagrange multipliers. 
    
     
    |  |
    | --- |
    |  || 0 || 1 || 2 || 3 || 4 || 5 || 6 |
    | $\\overline{\\theta}$ || 0.0002 || \-0.8127 || \-1.1151 || \-1.3610 || \-0.8435 || \-0.1806 || 1.4985 |
    | --- | --- | --- | --- | --- | --- | --- | --- |
    |  |
    
    The entropy-optimal PDFs of the parameters *P*^(\*)(*r*, *u*) and noises $q\_{n}^{\*}(\\xi\\lbrack 5n\\rbrack),n = \\overline{0,7}$ are shown in [Fig. 11.1](#chapter11.xhtml#f11_1)–[11.2](#chapter11.xhtml#f11_2).
    
    ![Figure 11.1: Entropy-optimal PDF P^{\*}(r,u)](images/fig11_1.jpg)
    
    [Figure 11.1:](#chapter11.xhtml#f11_1b) Entropy-optimal PDF *P*^(\*)(*r*, *u*)
    
    ![Figure 11.2: Entropy-optimal PDFs q\_{n}^{\*}(\\xi\\lbrack 5n\\rbrack),n = \\overline{0,7}.](images/fig11_2.jpg)
    
    [Figure 11.2:](#chapter11.xhtml#f11_2b) Entropy-optimal PDFs $q\_{n}^{\*}(\\xi\\lbrack 5n\\rbrack),n = \\overline{0,7}$.
    
    **3. Testing**
    
    The model has been tested using the data from [Table 11.2](#chapter11.xhtml#t11_2) on the interval 1995–2015. Population size has been evaluated by formula (11.14), where *r* and *u* are randomized parameters with the PDFs *P*^(\*)(*r*, *u*) and *q*[*n*]^(\*)(*ξ*\[5*n*\]), $n = \\overline{0,4}.$ To generate an ensemble of random variables, we used the 2-dimensional modification of the Ulam–von Neumann method (Acceptance-Rejection method) \[159\].
    
    Each pair of the random values *r* and *u* defines a separate exponential growth curve; moreover, for each point *\[nh\]* a random value of the noise is added according to its PDF. As a result, the constructed trajectory of world population dynamics is not an exponential function. In the testing stage,
    
      
    $$\\begin{array}{r} {E^{tst}\\lbrack 0\\rbrack = E\_{real}^{tst}\\lbrack 0\\rbrack.} \\\\ \\end{array}$$  
    (11.23)
    
    The ensemble is shown in [Figure 11.3](#chapter11.xhtml#f11_3), where 1—the mean trajectories the mean trajectories of population dynamics; 2—real population dynamics on the testing interval 11.3, 3—population dynamics on the testing interval according to the UN forecast; 4—the boundaries of the variance.
    
    ![Figure 11.3: Ensemble of testing trajectories.](images/fig11_3.jpg)
    
    [Figure 11.3:](#chapter11.xhtml#f11_3b) Ensemble of testing trajectories.
    
    Testing quality is assessed by the root-mean-square error (RMSE) between the mean and predicted trajectories
    
      
    $$\\begin{array}{r} {\\delta = \\sqrt{\\sum\\limits\_{i = 0}^{4}{(E\_{real}^{tst}\\lbrack ih\\rbrack - E^{tst}\\lbrack ih\\rbrack)}^{2}},} \\\\ \\end{array}$$  
    (11.24)
    
    and relative error
    
      
    $$\\begin{array}{r} {\\varepsilon = \\frac{\\delta}{\\| E\_{real}^{tst}\\lbrack ih\\rbrack\\| + \\| E^{tst}\\lbrack ih\\rbrack\\|}.} \\\\ \\end{array}$$  
    (11.25)
    
    For instance, for the UN forecast
    
      
    $$\\begin{array}{r} {\\delta\_{1985} = 0.9520,\\text{\\quad\\quad}\\varepsilon\_{1985} = 0.0321.} \\\\ \\end{array}$$  
    (11.26)
    
    For the testing ensemble,
    
      
    $$\\begin{array}{r} {\\delta\_{RM} = 0.079,\\text{\\quad\\quad}\\varepsilon\_{RM} = 0.003.} \\\\ \\end{array}$$  
    (11.27)
    
    **Forecasting**
    
    The entropy-optimal randomized model was used to forecast the world population dynamics in the interval 2015–2050 years. [Table 11.3](#chapter11.xhtml#t11_3) shows the UN-forecast data for the same period. [Fig. 11.4](#chapter11.xhtml#f11_4) shows the ensemble of the predicted trajectories and (1)—the mean trajectory over the ensemble, (2)—the trajectory of the UN forecast, (3)—the variance boundaries.
    
    ![Figure 11.4: Ensemble of predicted trajectories.](images/fig11_4.jpg)
    
    [Figure 11.4:](#chapter11.xhtml#f11_4b) Ensemble of predicted trajectories.
    

## 11.3Randomized Forecasting of Daily Electrical Load in Power System

The daily electrical load *L* of a power system depends on many various factors. The analysis below is restricted to one of the most significant external factors—the ambient temperature *T*. The daily temperature variations are fluctuating. These fluctuations affect electrical load, but with some time delay due the inertia of a power network supplying electrical energy from the generator to consumers.

### 11.3.1Electrical Load Model

The electrical load model (the *LT* model) describes the dynamic relation between electrical load and ambient temperature while the ambient temperature model (the *T**ξ* model) describes the daily dynamics of ambient temperature. There exist quite a few versions of the *LT* model, albeit all being static, i.e., describing the relation between electrical load and ambient temperature at current time instants \[[49](#refbib.xhtml#r49)\]. The daily temperature dynamics are fluctuating, and such fluctuations are described, in particular, by the periodic autoregressive model \[[13](#refbib.xhtml#r13)\].

Note that the effect of ambient temperature on electrical load is dynamic, i.e., the change in load due to temperature at a given time instant depends on its value at a previous time instant. A similar property applies to ambient temperature fluctuations.

Therefore, following the general randomized approach, the *LT* model is designed as a first-order dynamic regression model with random parameters; the *T**ξ* model, as a second-order dynamic regression with a random parameter and a random input *ξ*. Then the *L**T**ξ* model is the composition of the two models above.

In the class of linear models, the randomized dynamic regression load–temperature model (*LT* model) of the first order can be written in the form

  
$$\\begin{array}{r} {L\\lbrack n\\rbrack = aL\\lbrack n - 1\\rbrack + bT\\lbrack n\\rbrack,} \\\\ {v\\lbrack n\\rbrack = L\\lbrack n\\rbrack + \\mu\\lbrack n\\rbrack,\\text{\\quad\\quad}n = \\overline{1,24}.} \\\\ \\end{array}$$  
(11.28)

where random independent parameters *a* and *b* take values within intervals

  
$$\\begin{array}{r} {a \\in \\mathcal{A} = \\lbrack a^{-},a^{+}\\rbrack,\\,\\, b \\in \\mathcal{B} = \\lbrack b^{-},b^{+}\\rbrack.} \\\\ \\end{array}$$  
(11.29)

The probabilistic properties are characterized by PDFs *P*(*a*) and *F*(*b*) defined on the sets 𝒜 and ℬ, respectively. The random noise *μ*\[*n*\] that simulates electrical load measurement errors is of the interval type as well. In the general case, for each time instant the intervals may have different limits, i.e.,

  
$$\\begin{array}{r} {\\mu\\lbrack n\\rbrack \\in \\mathcal{M}\_{n} = \\lbrack\\mu^{-}\\lbrack n\\rbrack\\rbrack,\\mu^{+}\\lbrack n\\rbrack\\rbrack,} \\\\ \\end{array}$$  
(11.30)

with PDFs *M*[*n*](*μ*\[*n*\]), \], $n = \\overline{n^{-},n^{+}}.$

Consider the *T**ξ* model. The fluctuating character of the daily temperature variations is described by the randomized dynamic regression model of the second order

  
$$\\begin{aligned} {\\tau\\lbrack n\\rbrack} & {= c\\left( {2,1\\tau\\lbrack n - 1\\rbrack - 1,1\\tau\\lbrack n - 2\\rbrack} \\right),\\quad c = \\frac{1}{1 + \\omega^{2}},} \\\\ {T\\lbrack n\\rbrack} & {= t + \\tau\\lbrack n\\rbrack + \\xi\\lbrack n\\rbrack,} \\\\ \\end{aligned}$$  
(11.31)

where *ω* is the temperature fluctuation frequency, *t* is the mean daily temperature. These parameters are random and take values within given intervals, i.e.

  
$$\\begin{array}{r} {\\omega \\in \\Omega = \\lbrack\\omega^{-},\\omega^{+}\\rbrack,\\text{\\quad\\quad}c \\in \\mathcal{C} = \\lbrack c^{-},c^{+}\\rbrack,} \\\\ {c^{-} = \\frac{1}{1 + {(\\omega^{+})}^{2}} > 0,\\quad c^{+} = \\frac{1}{1 + {(\\omega^{-})}^{2}} > c^{-} > 0.} \\\\ \\end{array}$$  
(11.32)

The probabilistic properties of the parameters are characterized by PDFs *W*(*c*) defined on corresponding intervals.

Equation (11.3.1) contains random noises described by independent random variables *ξ*\[*n*\]; in each measurement *n*, their values may lie in different intervals, i.e.,

  
$$\\begin{array}{r} {\\xi\\lbrack n\\rbrack \\in \\Xi\_{n} = \\lbrack\\xi\_{n}^{-},\\xi\_{n}^{+}\\rbrack.} \\\\ \\end{array}$$  
(11.33)

The probabilistic properties of the random variable *ξ*\[*n*\] are characterized by a PDF $Q\_{n}(\\xi\\lbrack n\\rbrack),\\, n = \\overline{n^{-},n^{+}}.$

Thus, equations (11.28, 11.31) describing electrical load dynamics in a power system are characterized by the following PDFs:

*   the *LT* model, by the PDFs *P*(*a*) and *F*(*b*) of the model parameters and the PDF *M*[*n*](*μ*\[*n*\]), of the measurement noises, $n = \\overline{n^{-},n^{+}};$
    
*   the *T**ξ* model, by the PDFs *W*(*c*) of the model parameters and the PDFs *Q*[*n*](*ξ*\[*n*\]) of the measurement noises, $n = \\overline{n^{-},n^{+}}.$
    

### 11.3.2Learning dataset

For estimating the PDFs, the normalized real data from the GEFCom2014 dataset (see \[[71](#refbib.xhtml#r71)\]) on daily electrical load variations 0 ≤ *L*[*r*]^((*i*))\[*n*\] ≤ 1, mean daily temperature variations 0 ≤ *t*[*r*]^((*i*)) ≤ 1 and temperature deviations 0 ≤ *τ*[*r*]^((*i*))\[*n*\] ≤ 1 from the mean daily value can be used. (Here normalization means the reduction to the unit interval.)

The normalization procedure is performed in the following way:

  
$$\\begin{aligned} {L\_{r}^{(i)}\\lbrack n\\rbrack} & {= \\frac{{\\hat{L}}\_{r}^{(i)}\\lbrack n\\rbrack - {\\hat{L}}\_{min}^{(i)}}{{\\hat{L}}\_{max}^{(i)} - {\\hat{L}}\_{min}^{(i)}},} \\\\ {\\tau\_{r}^{(i)}\\lbrack n\\rbrack} & {= \\frac{{\\hat{\\tau}}\_{r}^{(i)}\\lbrack n\\rbrack - {\\hat{\\tau}}\_{min}^{(i)}}{{\\hat{\\tau}}\_{max}^{(i)} - {\\hat{\\tau}}\_{min}^{(i)}},} \\\\ t\_{r}^{(i)} & {= \\frac{1}{24}{\\sum\\limits\_{n = 1}^{24}\\tau\_{r}^{(i)}}\\lbrack n\\rbrack,} \\\\ \\end{aligned}$$  
(11.34)

where${\\hat{L}}\_{min}^{(i)} = \\min\\limits\_{n}{\\hat{L}}^{(i)}\\lbrack n\\rbrack$, ${\\hat{L}}\_{max}^{(i)} = \\max\\limits\_{n}{\\hat{L}}^{(i)}\\lbrack n\\rbrack$, ${\\hat{\\tau}}\_{min}^{(i)} = \\min\\limits\_{n}{\\hat{\\tau}}^{(i)}\\lbrack n\\rbrack$, ${\\hat{\\tau}}\_{max}^{(i)} = \\max\\limits\_{n}{\\hat{\\tau}}^{(i)}\\lbrack n\\rbrack.$

[Figure 11.5](#chapter11.xhtml#f11_5) shows graphs of the load *L*[*r*]^((*i*))\[*n*\], the temperature deviation *τ*[*r*]^((*i*))\[*n*\] and data on daily-average temperature *t*[*r*]^((*i*)) at 03.07.2016 (*i* = 1), 04.07.2016 (*i* = 2), 05.07.2016 (*i* = 3) as learning collection. Let us denote *learning interval* 𝒯[*l*] = \[*n*^−, *n*^+\] = \[1, 24\].

![Figure 11.5: Load L\_{r}^{(i)}\\lbrack n\\rbrack and temperature deviation \\tau\_{r}^{(i)}\\lbrack n\\rbrack.](images/fig11_5.jpg)

[Figure 11.5:](#chapter11.xhtml#f11_5b) Load *L*[*r*]^((*i*))\[*n*\] and temperature deviation *τ*[*r*]^((*i*))\[*n*\].

According to (11.28), (11.31), the model variables and the corresponding real data on the learning interval *n* ∈ 𝒯[*l*] are described by the vectors

  
$$\\begin{aligned} {\\mathbf{L}^{(i)}(\\mathcal{T}\_{l}) =} & {\\left\\{ L^{(i)}\\lbrack 1\\rbrack,\\ldots,L^{(i)}\\lbrack 24\\rbrack \\right\\},\\mathbf{L}\_{r}^{(i)}(\\mathcal{T}\_{l}) = \\left\\{ L\_{r}^{(i)}\\lbrack 1\\rbrack,\\ldots,L\_{r}^{(i)}\\lbrack 24\\rbrack \\right\\},} \\\\ & {\\quad\\mathbf{L}^{(i)}(\\mathcal{T}\_{l} - 1) = \\left\\{ L^{(i)}\\lbrack 0\\rbrack,\\ldots,L^{(i)}\\lbrack 23\\rbrack \\right\\},} \\\\ & {\\quad\\mathbf{L}\_{r}^{(i)}(\\mathcal{T}\_{l} - 1) = \\left\\{ L\_{r}^{(i)}\\lbrack 0\\rbrack,\\ldots,L\_{r}^{(i)}\\lbrack 23\\rbrack \\right\\},} \\\\ {\\mathbf{V}^{(i)}(\\mathcal{T}\_{l}) =} & {\\left\\{ v^{(i)}\\lbrack 1\\rbrack,\\ldots,v^{(i)}\\lbrack 24\\rbrack \\right\\},\\mathbf{V}\_{r}^{(i)}(\\mathcal{T}\_{l}) = \\left\\{ v\_{r}^{(i)}\\lbrack 1\\rbrack,\\ldots,v\_{r}^{(i)}\\lbrack 24\\rbrack \\right\\},} \\\\ {\\mathbf{T}^{(i)}(\\mathcal{T}\_{l}) =} & {\\left\\{ \\tau^{(i)}\\lbrack 1\\rbrack,\\ldots,\\tau^{(i)}\\lbrack 24\\rbrack \\right\\},\\mathbf{T}\_{r}^{(i)}(\\mathcal{T}\_{l}) = \\left\\{ \\tau\_{r}^{(i)}\\lbrack 1\\rbrack,\\ldots,\\tau\_{r}^{(i)}\\lbrack 24\\rbrack \\right\\},} \\\\ \\end{aligned}$$  

  
$$\\begin{aligned} {{\\widetilde{\\mathbf{T}}}^{(i)}(\\mathcal{T}\_{l} - 1,} & {\\mathcal{T}\_{l} - 2) = \\left\\{ 2,1\\tau^{(i)}\\lbrack 0\\rbrack - 1,1\\tau^{(i)}\\lbrack - 1\\rbrack,\\ldots, \\right.} \\\\ & {\\left. 2,1\\tau^{(i)}\\lbrack 23\\rbrack - 1,1\\tau^{(i)}\\lbrack 22\\rbrack \\right\\},} \\\\ {{\\widetilde{\\mathbf{T}}}\_{r}^{(i)}(\\mathcal{T}\_{l} - 1,} & {\\mathcal{T}\_{l} - 2) = \\left\\{ 2,1\\tau\_{r}^{(i)}\\lbrack 0\\rbrack - 1,1\\tau\_{r}^{(i)}\\lbrack - 1\\rbrack,\\ldots, \\right.} \\\\ & {\\left. 2,1\\tau\_{r}^{(i)}\\lbrack 23\\rbrack - 1,1\\tau\_{r}^{(i)}\\lbrack 22\\rbrack \\right\\},} \\\\ \\end{aligned}$$  

  
$$\\begin{array}{r} {\\mu^{(i)}(\\mathcal{T}\_{l}) = \\left\\{ \\mu^{(i)}\\lbrack 1\\rbrack,\\ldots,\\mu^{(i)}\\lbrack 24\\rbrack \\right\\},\\quad\\xi^{(i)}(\\mathcal{T}\_{l}) = \\left\\{ \\xi^{(i)}\\lbrack 1\\rbrack,\\ldots,\\xi^{(i)}\\lbrack 24\\rbrack \\right\\}.} \\\\ \\end{array}$$  

In terms of ([11.3.2](#chapter11.xhtml#sec11_3_2)), the *LT*\- and *T**ξ*\-models on the learning interval 𝒯[*l*] have the form

  
$$\\begin{aligned} & {\\mathbf{L}^{(i)}(\\mathcal{T}\_{l}) = a\\mathbf{L}^{(i)}(\\mathcal{T}\_{l} - 1) + b\\mathbf{T}^{(i)}(\\mathcal{T}\_{l}),} \\\\ & {\\mathbf{V}^{(i)}(\\mathcal{T}\_{l}) = \\mathbf{L}^{(i)}(\\mathcal{T}\_{l}) + \\mu^{(i)}(\\mathcal{T}\_{l}),} \\\\ & {\\mathbf{T}^{(i)}(\\mathcal{T}\_{l}) = c\\,{\\widetilde{\\mathbf{T}}}^{(i)}(\\mathcal{T}\_{l} - 1,\\mathcal{T}\_{l} - 2),} \\\\ & {\\mathbf{T}^{(i)}(\\mathcal{T}\_{l}) = t + {\\widetilde{\\mathbf{T}}}^{(i)}(\\mathcal{T}\_{l}) + \\xi^{(i)}(\\mathcal{T}\_{l}).} \\\\ \\end{aligned}$$  
(11.35)

The random parameters take values within the intervals

  
$$\\begin{array}{r} {\\mathcal{A} = \\lbrack 0,05;0,15\\rbrack,\\quad\\mathcal{B} = \\lbrack 0,5;1,0\\rbrack,\\quad\\mathcal{C} = \\lbrack 0,75;0,85\\rbrack.} \\\\ \\end{array}$$  
(11.36)

The measurement noises take values within the intervals

  
$$\\begin{array}{r} {\\mathcal{M}\_{n} = \\lbrack - 0.1;0,1\\rbrack,\\quad\\Xi\_{n} = \\lbrack - 0,1;0,1\\rbrack.} \\\\ \\end{array}$$  
(11.37)

### 11.3.3Entropy-optimal probability density functions of parameters and noises

According to the approach described in Section 5, for the *LT* model (11.28)–(11.30) the PDFs parameterized by the Lagrange multipliers *θ*^((*i*)) = {*θ*[1]^((*i*)),…,*θ*[24]^((*i*))} have the form

  
$$\\begin{aligned} & {P\_{i}^{\*}(a,\\theta^{(i)}) = \\frac{l\_{r}^{(i)}(\\theta)\\exp\\left( {- al\_{r}^{(i)}(\\theta)} \\right)}{\\exp( - a^{-}l\_{r}^{(i)}(\\theta)) - \\exp( - a^{+}l\_{r}^{(i)}(\\theta))},} \\\\ & {F\_{i}^{\*}(b,\\theta^{(i)}) = \\frac{h\_{r}^{(i)}(\\theta)\\exp\\left( {- bh\_{r}^{(i)}(\\theta)} \\right)}{\\exp( - b^{-}h\_{r}^{(i)}(\\theta)) - \\exp( - b^{+}h\_{r}^{(i)}(\\theta))},} \\\\ & {M\_{i,n}^{\*}(\\mu\\lbrack n\\rbrack) = \\frac{\\theta\_{n}^{(i)}\\exp\\left( {- \\theta\_{n}^{(i)}\\mu\\lbrack n\\rbrack} \\right)}{\\exp( - \\mu^{-}\\lbrack n\\rbrack\\theta\_{n}^{(i)}) - \\exp( - \\mu^{+}\\lbrack n\\rbrack\\theta\_{n}^{(i)})},\\quad n = \\overline{1,24}.} \\\\ \\end{aligned}$$  
(11.38)

where

  
$$\\begin{array}{r} {l\_{r}^{(i)}(\\theta) = {\\sum\\limits\_{n = 1}^{24}\\theta\_{n}}L\_{r}^{(i)}\\lbrack n - 1\\rbrack,\\quad h\_{r}^{(i)}(\\theta) = {\\sum\\limits\_{n = 1}^{24}\\theta\_{n}}T\_{r}^{(i)}\\lbrack n\\rbrack.} \\\\ \\end{array}$$  
(11.39)

The Lagrange multipliers *θ*^((*i*)) are calculated by solving the system of balance equations

  
$$\\begin{array}{r} {L^{(i)}(\\theta^{(i)}) + T^{(i)}(\\theta^{(i)}) + M\_{n}^{(i)}(\\theta\_{n}^{(i)}) = L\_{r}^{(i)}\\lbrack n\\rbrack,\\text{\\quad\\quad}n = \\overline{1,24},} \\\\ \\end{array}$$  
(11.40)

where

  
$$\\begin{aligned} & {L^{(i)}(\\theta^{(i)}) = \\frac{1}{\\exp( - a^{-}l^{(i)}(\\theta^{(i)})) - \\exp( - a^{+}l^{(i)}(\\theta^{(i)}))} \\times} \\\\ & {\\text{\\quad\\quad}\\quad \\times (\\exp( - a^{-}l\_{r}^{(i)}(\\theta^{(i)}))(a^{-}l^{(i)}(\\theta^{(i)}) + 1) -} \\\\ & {\\text{\\quad\\quad}\\quad - \\exp( - a^{+}l\_{r}^{(i)}(\\theta^{(i)}))(a^{+}l^{(i)}(\\theta^{(i)}) + 1)),} \\\\ & {T^{(i)}(\\theta^{(i)}) = \\frac{1}{\\exp( - b^{-}h^{(i)}(\\theta^{(i)})) - \\exp( - b^{+}h^{(i)}(\\theta^{(i)}))} \\times} \\\\ & {\\text{\\quad\\quad}\\quad \\times (\\exp( - b^{-}h\_{r}^{(i)}(\\theta^{(i)}))(b^{-}h^{(i)}(\\theta^{(i)}) + 1) -} \\\\ & {\\text{\\quad\\quad}\\quad - \\exp( - b^{+}h\_{r}^{(i)}(\\theta^{(i)}))(b^{+}h^{(i)}(\\theta^{(i)}) + 1)),} \\\\ & {M\_{n}^{(i)}(\\theta\_{n}^{(i)}) = \\frac{1}{\\theta\_{n}^{(i)}\\left( {\\exp( - \\mu^{-}\\lbrack n\\rbrack\\theta\_{n}^{(i)}) - \\exp( - \\mu^{+}\\lbrack n\\rbrack\\theta\_{n}^{(i)})} \\right)} \\times} \\\\ & {\\quad\\quad\\text{\\quad\\quad} \\times (\\exp( - \\mu^{-}\\lbrack n\\rbrack\\theta\_{n}^{(i)})(\\mu^{-}\\lbrack n\\rbrack\\theta\_{n}^{(i)}) + 1) -} \\\\ & {\\quad\\quad\\text{\\quad\\quad} - \\exp( - \\mu^{+}\\lbrack n\\rbrack\\theta\_{n}^{(i)})(\\mu^{+}\\lbrack n\\rbrack\\theta\_{n}^{(i)}) + 1)).} \\\\ \\end{aligned}$$  
(11.41)

Consider the *T**ξ* model. The corresponding entropy-optimal PDFs parameterized by the Lagrange multipliers have the form

  
$$\\begin{aligned} & {W\_{i}^{\*}(c,\\eta^{(i)}) = \\frac{{\\widetilde{h}}\_{r}^{(i)}(\\eta)\\exp\\left( {- c{\\widetilde{h}}\_{r}^{(i)}(\\eta)} \\right)}{\\exp( - a^{-}{\\widetilde{h}}\_{r}^{(i)}(\\eta)) - \\exp( - a^{+}{\\widetilde{h}}\_{r}^{(i)}(\\eta))},} \\\\ & {Q\_{i,n}^{\*}(\\xi\\lbrack n\\rbrack) = \\frac{\\eta\_{n}^{(i)}\\exp\\left( {- \\eta\_{n}^{(i)}\\xi\\lbrack n\\rbrack} \\right)}{\\exp( - \\xi^{-}\\lbrack n\\rbrack\\eta\_{n}^{(i)}) - \\exp( - \\xi^{+}\\lbrack n\\rbrack\\eta\_{n}^{(i)})},\\quad n = \\overline{1,24}.} \\\\ \\end{aligned}$$  

where

  
$$\\begin{array}{r} {{\\widetilde{h}}\_{r}^{(i)}(\\eta) = {\\sum\\limits\_{n = 1}^{24}\\eta\_{n}}(2T\_{r}^{(i)}\\lbrack n - 1\\rbrack - T\_{r}^{(i)}\\lbrack n - 2\\rbrack),\\quad q^{(i)}(\\eta^{(i)}) = {\\sum\\limits\_{n = 1}^{24}\\eta\_{n}^{(i)}}.} \\\\ \\end{array}$$  
(11.42)

The Lagrange multipliers *η*^((*i*)) are calculated by solving the system of balance equations

  
$$\\begin{array}{r} {D^{(i)}(\\eta^{(i)}) + N^{(i)}(\\eta^{(i)}) + K\_{n}^{(i)}(\\eta\_{n}^{(i)}) = T\_{r}^{(i)}\\lbrack n\\rbrack,\\text{\\quad\\quad}n = \\overline{1,24},} \\\\ \\end{array}$$  
(11.43)

where

  
$$\\begin{aligned} & {D^{(i)}(\\eta^{(i)}) = \\frac{1}{\\exp( - t^{-}q^{(i)}(\\eta^{(i)})) - \\exp( - t^{+}q^{(i)}(\\eta^{(i)}))} \\times} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad} \\times (\\exp( - t^{-}q^{(i)}(\\eta^{(i)}))(t^{-}q^{(i)}(\\eta^{(i)}) + 1) -} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad} - \\exp( - t^{+}q^{(i)}(\\eta^{(i)}))(t^{+}q^{(i)}(\\eta^{(i)}) + 1)),} \\\\ & {N^{(i)}(\\eta^{(i)}) = \\frac{1}{\\exp( - c^{-}{\\widetilde{h}}^{(i)}(\\eta^{(i)})) - \\exp( - c^{+}{\\widetilde{h}}^{(i)}(\\eta^{(i)}))} \\times} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad} \\times (\\exp( - c^{-}{\\widetilde{h}}\_{r}^{(i)}(\\eta^{(i)}))(c^{-}{\\widetilde{h}}^{(i)}(\\eta^{(i)}) + 1) -} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad} - \\exp( - c^{+}{\\widetilde{h}}\_{r}^{(i)}(\\eta^{(i)}))(c^{+}{\\widetilde{h}}^{(i)}(\\eta^{(i)}) + 1)),} \\\\ & {K\_{n}^{(i)}(\\eta\_{n}^{(i)}) = \\frac{1}{\\eta\_{n}^{(i)}\\left( {\\exp( - \\xi^{-}\\lbrack n\\rbrack\\eta\_{n}^{(i)}) - \\exp( - \\xi^{+}\\lbrack n\\rbrack\\eta\_{n}^{(i)})} \\right)} \\times} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad \\times (\\exp( - \\xi^{-}\\lbrack n\\rbrack\\eta\_{n}^{(i)})(\\xi^{-}\\lbrack n\\rbrack\\eta\_{n}^{(i)}) + 1) -} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad - \\exp( - \\xi^{+}\\lbrack n\\rbrack\\eta\_{n}^{(i)})(\\xi^{+}\\lbrack n\\rbrack\\eta\_{n}^{(i)}) + 1)).} \\\\ \\end{aligned}$$  
(11.44)

### 11.3.4Results of model learning

Using the available data on daily variations of electrical load and ambient temperature for the three days indicated above, the balance equations (11.40), (11.3.3), (11.43)–(11.3.3) were formed. Their solution was determined by minimizing the quadratic residual between the left- and right-hand sides of the equations. Since the equations are significantly nonlinear, the resulting values of the Lagrange multipliers (see [Table 11.5](#chapter11.xhtml#t11_5)) correspond to a local minimum of the residual. All calculations were implemented in MATLAB; optimization was performed using the fsolve function.

 [Table 11.5:](#chapter11.xhtml#t11_5b) Lagrange multipliers *θ*, *η*. 

 
|  |
| --- |
| Time || *θ*^((1)) || *θ*^((2)) || *θ*^((3)) || *η*^((1)) || *η*^((2)) || *η*^((3)) |
| 1 || \-29.72 || 7009.28 || 1038.07 || 14.63 || 21.22 || 17.34 |
| --- | --- | --- | --- | --- | --- | --- |
| 2 || 1.58 || 230.89 || 35.35 || 19.52 || 26.71 || 28.32 |
| 3 || \-4.09 || 369.96 || 26.23 || 35.91 || 31.60 || 26.33 |
| 4 || \-4.68 || 29.93 || 11.96 || 55.83 || 127.82 || 52.08 |
| 5 || \-7.21 || 24.25 || 1.03 || 96.85 || 642.35 || 110.94 |
| 6 || \-9.26 || 13.72 || \-15.76 || 592.99 || 7009.28 || 4729.52 |
| 7 || \-59.09 || \-5.96 || \-7009.28 || 7009.28 || 183.92 || 7009.28 |
| 8 || \-7009.28 || \-33.99 || \-767.99 || 48.21 || 39.94 || 23.16 |
| 9 || \-766.00 || \-1409.28 || \-22.91 || 66.58 || 12.28 || \-1.26 |
| 10 || \-50.90 || \-4229.90 || \-4.27 || 37.38 || 2.35 || \-19.78 |
| 11 || \-18.97 || \-45.22 || 3.72 || 22.51 || \-8.82 || \-22.73 |
| 12 || \-11.42 || \-15.07 || 9.17 || 7.16 || \-27.06 || \-23.06 |
| 13 || \-13.94 || 2.59 || 17.38 || 5.72 || \-172.25 || \-27.06 |
| 14 || \-17.62 || 5.82 || 14.94 || 2.83 || \-65.29 || \-23.02 |
| 15 || \-18.18 || 9.33 || 17.74 || \-0.30 || \-57.45 || \-23.15 |
| 16 || \-27.28 || 11.35 || 21.85 || \-1.24 || \-482.69 || \-47.78 |
| 17 || \-49.55 || 4.50 || 22.68 || \-5.49 || \-889.02 || \-130.49 |
| 18 || \-25.41 || \-7.09 || 29.39 || \-0.89 || \-28.12 || \-60.71 |
| 19 || \-8.20 || \-4.66 || 98.03 || \-4.23 || \-14.20 || \-270.17 |
| 20 || 0.95 || \-4.89 || 52.27 || 3.70 || \-6.41 || \-31.47 |
| 21 || 1.01 || \-16.37 || 8.15 || 21.16 || 2.48 || \-1.23 |
| 22 || 22.00 || \-8.24 || 7.45 || 17.85 || 12.15 || 14.86 |
| 23 || 2881.43 || 17.00 || 902.73 || 26.78 || 9.98 || 26.39 |
| 24 || 512.14 || 36.30 || 355.47 || 27.32 || 24.65 || 121.44 |
| *l*[*r*]^((*i*))(*θ*^(\*)) || 9.71 || 6.04 || 6.09 ||  ||  ||  |
| *h*[*r*]^((*i*))(*θ*^(\*)) || 0.06 || 0.58 || 0.81 ||  ||  ||  |
| *h̃*[*r*]^((*i*))(*η*^(\*)) ||  ||  ||  || 0.41 || 0.05 || 0.19 |
|  |

Because the parameters of the *LT* model are independent, the joint PDFs *U*[*i*]^(\*)(*a*, *b*) = *P*[*i*]^(\*)(*a*)*F*[*i*]^(\*)(*b*) of the parameters and noises have the form

  
$$\\begin{aligned} {U\_{1}^{\*}(a,b)} & {= 53,09\\exp( - 9,72a)\\,\\exp(0,06b),} \\\\ {U\_{2}^{\*}(a,b)} & {= 55,49\\exp( - 6,04a)\\,\\exp(0,58b),} \\\\ {U\_{3}^{\*}(a,b)} & {= 65,81\\exp( - 6,09a)\\,\\exp( - 0,81b),} \\\\ \\end{aligned}$$  
(11.45)

  
$$\\begin{array}{r} {(a,b) \\in \\lbrack 0,05;0,15\\rbrack \\cup \\lbrack 0,5;1,0\\rbrack,\\quad\\mu \\in \\lbrack - 0,1,0,1\\rbrack,\\quad i = \\overline{1,24}.} \\\\ \\end{array}$$  

Clearly, the PDFs are of exponential type. For *i* = 1, the graphs are shown in [Fig. 11.6](#chapter11.xhtml#f11_6).

![Figure 11.6](images/fig11_6.jpg)

[Figure 11.6](#chapter11.xhtml#f11_6b)

For the *T**ξ* model, the PDFs of the parameters and noises have the form

  
$$\\begin{aligned} {W\_{1}^{\*}(c)} & {= 13,90\\exp( - 0,41c),} \\\\ {W\_{2}^{\*}(c)} & {= 10,43\\exp( - 0,05c),} \\\\ {W\_{3}^{\*}(c)} & {= 11,65\\exp( - 0,19c),} \\\\ \\end{aligned}$$  

  
$$\\begin{array}{r} {c \\in \\lbrack 0,75;0,85\\rbrack,\\quad\\xi \\in \\lbrack - 0,1;0,1\\rbrack,\\quad i = \\overline{1,24}.} \\\\ \\end{array}$$  

For *i* = 1, the graphs can be seen in [Fig. 11.7](#chapter11.xhtml#f11_7).

![Figure 11.7](images/fig11_7.jpg)

[Figure 11.7](#chapter11.xhtml#f11_7b)

Thus, the randomized *L**T**ξ* model generates random trajectories with the entropy-optimal PDFs of the model parameters and measurement noises:

  
$$\\begin{aligned} {L\\lbrack n\\rbrack} & {= aL\\lbrack n - 1\\rbrack + bT\\lbrack n\\rbrack,\\quad\\left( {P^{\*}(a),F^{\*}(b)} \\right),} \\\\ {v\\lbrack n\\rbrack} & {= L\\lbrack n\\rbrack + \\mu\\lbrack n\\rbrack,\\quad M\_{n}^{\*}(\\mu\\lbrack n\\rbrack);} \\\\ {\\tau\\lbrack n\\rbrack} & {= c\\left( {2\\tau\\lbrack n - 1\\rbrack - \\tau\\lbrack n - 2\\rbrack} \\right),\\quad W^{\*}(c),\\,\\, i = \\overline{1,3},} \\\\ {T\\lbrack n\\rbrack} & {= t + \\tau\\lbrack n\\rbrack + \\xi\\lbrack n\\rbrack,\\quad Q\_{n}^{\*}(\\xi\\lbrack n\\rbrack).} \\\\ \\end{aligned}$$  
(11.46)

The corresponding ensembles are generated by the sampling procedure of the resulting PDFs of the parameters and noises using the acceptance-rejection (AR) method (also known as rejection sampling (RS); see \[[186](#refbib.xhtml#r186)\]). During calculations, 100 samples for each parameter and 100 samples for each noise were used; in other words, the ensemble consisted of 10⁴ trajectories.

### 11.3.5Model testing

The adequacy of the model was analyzed by the self- and cross-testing of the *LT* and *T**ξ* models on the real load–temperature data for July 3–5, 2016 (*i* = 1, 2, 3). Self-testing means generating an ensemble of trajectories with the entropy-optimal parameters and noises for day *i*, calculating the mean (*mean*) and median (*med*) trajectories and also the variance pipe (*std±*) of the ensemble, and comparing the mean trajectory with the real counterparts by electrical load and ambient temperature *for the same day i*. The quality of approximation is characterized by relative errors,

  
$$\\begin{array}{r} {\\delta\_{L}^{(i)} = \\frac{\\sum\\limits\_{n = 1}^{24}\\left( {L\_{mean}^{(i)}\\lbrack n\\rbrack - L\_{r}^{(i)}\\lbrack n\\rbrack} \\right)^{2}}{{\\sum\\limits\_{n = 1}^{24}{(L\_{mean}^{(i)}\\lbrack n\\rbrack)}^{2}} + {\\sum\\limits\_{n = 1}^{24}{(L\_{r}^{(i)}\\lbrack n\\rbrack)}^{2}}},\\quad i = \\overline{1,3},} \\\\ \\end{array}$$  
(11.47)

in electrical load and

  
$$\\begin{array}{r} {\\delta\_{T}^{(i)} = \\frac{\\sum\\limits\_{n = 1}^{24}\\left( {T\_{mean}^{(i)}\\lbrack n\\rbrack - T\_{r}^{(i)}\\lbrack n\\rbrack} \\right)^{2}}{{\\sum\\limits\_{n = 1}^{24}{(T\_{mean}^{(i)}\\lbrack n\\rbrack)}^{2}} + {\\sum\\limits\_{n = 1}^{24}{(T\_{r}^{(i)}\\lbrack n\\rbrack)}^{2}}},\\quad i = \\overline{1,3}.} \\\\ \\end{array}$$  
(11.48)

in ambient temperature.

Cross-testing represents a similar procedure in which the mean trajectories are compared with the real counterparts in terms of electrical load and ambient temperature for days *j* ≠ *i*. The quality of approximation is characterized by relative errors,

  
$$\\begin{array}{r} {\\delta\_{L}^{(i,j)} = \\frac{\\sum\\limits\_{n = 1}^{24}\\left( {L\_{mean}^{(i)}\\lbrack n\\rbrack - L\_{r}^{(j)}\\lbrack n\\rbrack} \\right)^{2}}{{\\sum\\limits\_{n = 1}^{24}{(L\_{mean}^{(i)}\\lbrack n\\rbrack)}^{2}} + {\\sum\\limits\_{n = 1}^{24}{(L\_{r}^{(j)}\\lbrack n\\rbrack)}^{2}}},\\quad i = \\overline{1,3},\\, i \\neq j,} \\\\ \\end{array}$$  
(11.49)

in electrical load and

  
$$\\begin{array}{r} {\\delta\_{T}^{(i,j)} = \\frac{\\sum\\limits\_{n = 1}^{24}\\left( {T\_{mean}^{(i)}\\lbrack n\\rbrack - T\_{r}^{(j)}\\lbrack n\\rbrack} \\right)^{2}}{{\\sum\\limits\_{n = 1}^{24}{(T\_{mean}^{(i)}\\lbrack n\\rbrack)}^{2}} + {\\sum\\limits\_{n = 1}^{24}{(T\_{r}^{(j)}\\lbrack n\\rbrack)}^{2}}},\\quad i = \\overline{1,3},i \\neq j.} \\\\ \\end{array}$$  
(11.50)

in ambient temperature.

*Self-testing*. For the *LT* model, the real ambient temperature data *T*[*r*]^((*i*))\[*n*\], as well as the entropy-optimal PDFs *P*[*i*]^(\*)(*a*) and *F*[*i*]^(\*)(*b*) of the parameters (*a*, *b*) and the PDFs *M*[1]^(\*)(*μ*\[1\]), …, *M*[24]^(\*)(*μ*\[24\]) of the measurement noises *μ*\[*n*\], were used. The ensembles 𝕃^((*i*)) were generated using the *sampling procedure* of the above PDFs. The mean trajectory *L*[*m**e**a**n*]^((*i*))\[*n*\], the median trajectory *L*[*m**e**d*]^((*i*))\[*n*\] and also the trajectories *L*[*s**t**d*±]^((*i*))\[*n*\] corresponding to the limits of the variance graph were found. The errors *δ*[*L*]^((*i*)) were calculated. The resulting ensembles and relative errors *δ*[*L*]^((*i*)) for the three indicated days are demonstrated in [Fig. 11.8](#chapter11.xhtml#f11_8).

![Figure 11.8: Ensembles of LT model.](images/fig11_8.jpg)

[Figure 11.8:](#chapter11.xhtml#f11_8b) Ensembles of *LT* model.

The *T**ξ* model was tested by generating the ensemble 𝕋^((*i*)) of random trajectories *T*^((*i*))\[*n*\], $n = \\overline{1,24}$ with the entropy-optimal PDFs *W*^((*i*))(*c*) and *Q*[1]^(\*)(*ξ*\[1\]), …, *Q*[24]^(\*)(*ξ*\[24\]) through sampling. The mean trajectory *T*[*m**e**a**n*]^((*i*))\[*n*\], the median trajectory *T*[*m**e**d*]^((*i*))\[*n*\] and the trajectory *T*[*s**t**d*±]^((*i*))\[*n*\] corresponding to the limits of the variance pipe are calculated. The resulting ensembles and relative errors *δ*[*T*]^((*i*)) for the three days are shown in [Fig. 11.9](#chapter11.xhtml#f11_9)

![Figure 11.9: Ensembles of T\\xi-model.](images/fig11_9.jpg)

[Figure 11.9:](#chapter11.xhtml#f11_9b) Ensembles of *T**ξ*\-model.

*Cross-testing.* For cross-testing, the *LT* and *L**T**ξ* models learned on the data for day *i* were used, and their mean trajectories were compared with the data for days *j* ≠ *i*. The resulting errors are combined in [Table 11.6](#chapter11.xhtml#t11_6), [Table 11.7](#chapter11.xhtml#t11_7), [Table 11.8](#chapter11.xhtml#t11_8).

 [Table 11.6:](#chapter11.xhtml#t11_6b) Values *δ*[*L*] obtained by cross-testing of *LT* model. Mean value *δ*[*L*] = 0.0530. 

 
|  |
| --- |
| *i*/*j* || 1 || 2 || 3 |
| 1 ||  || 0.0495 || 0.1052 |
| --- | --- | --- | --- |
| 2 || 0.0858 ||  || 0.1428 |
| 3 || 0.0569 || 0.0364 ||  |
|  |

 

[Table 11.7:](#chapter11.xhtml#t11_7b) Values *δ*[*T*] obtained by cross-testing of *T**ξ* model. Mean value *δ*[*L*] = 0.0757.

 
|  |
| --- |
| *i*/*j* || 1 || 2 || 3 |
| 1 ||  || 0.1051 || 0.1079 |
| --- | --- | --- | --- |
| 2 || 0.1506 ||  || 0.1185 |
| 3 || 0.1315 || 0.0676 ||  |
|  |

 

[Table 11.8:](#chapter11.xhtml#t11_8b) Values *δ*[*T*] obtained by cross-testing of *L**T**ξ* model. Mean value *δ*[*L*] = 0.1478.

 
|  |
| --- |
| *i*/*j* || 1 || 2 || 3 |
| 1 ||  || 0.1437 || 0.2659 |
| --- | --- | --- | --- |
| 2 || 0.1756 ||  || 0.2322 |
| 3 || 0.3475 || 0.1655 ||  |
|  |

### 11.3.6Randomized prediction of *N*\-daily load

In the randomized prediction of the *N*\-daily load, the *L**T**ξ* model learned on the interval 𝒯[*l*] was used. The quality of the forecast was characterized using the *L**T**ξ* model with the entropy-optimal PDFs obtained on the real data for the *first* (*i* = 1) day.

The 1-day (*n* ∈ \[1, 24\]), 2-day (*n* ∈ \[1, 48\]) and 3-day (*n* ∈ \[1, 72\]) ensembles were constructed by the sampling procedure of the above PDFs. For these ensembles, the mean trajectories *L*[*m**e**a**n*]\[*n*\], the median trajectories *L*[*m**e**d*]\[*n*\] and also the limiting trajectories *L*[*s**t**d*±]\[*n*\] of the variance pipe were found. The forecast results were compared with the real data for July 3–7, 2006 ($i = \\overline{1,4}$). The forecasting quality was characterized by the relative errors calculated similar to (11.49)–(11.50).

The resulting 24-h, 48-h and 72-h randomized forecasts of electrical load and their probabilistic characteristics (the mean and median trajectories, the limit trajectories of the variance pipes) are presented in [Fig. 11.10](#chapter11.xhtml#f11_10). The errors, i.e., the deviations between the model forecasts and real data, can be seen in [Table 11.9](#chapter11.xhtml#t11_9).

![Figure 11.10: 24-h, 48-h and 72-h forecasts using LT\\xi model.](images/fig11_10.jpg)

[Figure 11.10:](#chapter11.xhtml#f11_10b) 24-h, 48-h and 72-h forecasts using *L**T**ξ* model.

 [Table 11.9:](#chapter11.xhtml#t11_9b) Accuracy of 24-h, 48-h and 72-h forecasts using *L**T**ξ* model. 

 
|  |
| --- |
| *δ*[*L*]^((2)) || *δ*[*L*]^((3)) || *δ*[*L*]^((4)) |
| 0,1509 || 0,2515 || 0,2133 |
| --- | --- | --- |
|  |

An important feature of the described method is the formation of predictive trajectories under “entropy-worst” measurement errors.

## 11.4Entropy Randomized Modelling and Forecasting of Thermokarst Lake Area Evolution in Western Siberia

### 11.4.1Thermokarst lakes and climate change

Permafrost zones, occupying a significant part of the earth's surface, are the localization of thermokarst lakes, which accumulate greenhouse gases (methane and carbon dioxide). These gases have a considerable contribution to global climate change. Climate warming may cause a positive inverse reaction: an increase in temperature will lead to melting of frozen rocks and additional release of methane and carbon dioxide produced by the vital activity of microorganisms that process thawed organic matter.

A thorough understanding of this global cycle and its catastrophic consequences motivates researchers to study the origin, evolution and transformation of thermokarst lakes in permafrost zones \[[92](#refbib.xhtml#r92), [200](#refbib.xhtml#r200)\]. The source data in such studies are acquired by the remote sensing of the earth surface and measurements of meteorological parameters \[[24](#refbib.xhtml#r24), [89](#refbib.xhtml#r89), [112](#refbib.xhtml#r112), [113](#refbib.xhtml#r113), [129](#refbib.xhtml#r129), [154](#refbib.xhtml#r154)\].

The available historical data allow tracing the past spatiotemporal evolution of thermokarst lakes. However, to forecast the spatiotemporal evolution, one needs *environmental models* (EnMd) adapted to historical data. For this purpose, EnMd are first trained through machine learning algorithms and then used to obtain forecasts.

The processes of formation and evolution of thermokarst lakes have been underinvestigated. Moreover, historical data about these processes, especially those acquired from satellites, contain significant errors. Due to all these factors, the predictive EnMd must operate under conditions of sufficiently high uncertainty. So, we consider *randomized forecasting* (RF) approach, an alternative approach compared to the traditional machine learning methods.

### 11.4.2Thermokarst lakes of Western Siberia, tools and problems of their study

Remote studies of the spatiotemporal dynamics of thermokarst lakes (their number and size) in permafrost zones of Western Siberia are based on sensing of the earth surface using combinations of images of medium (30 m) and high resolution (from fractions of a meter to several meters). This combination allows detecting shallow lakes, which produce significantly more greenhouse gases than large ones.

The territory in the permafrost zone of Western Siberia studied in this paper has an area of about 1.05 million km². This territory includes three typical zones ([Fig. 11.11](#chapter11.xhtml#f11_11)): insular (*I*, southern), discontinuous (*D*, middle) and continuous (*C*, northern). Lakes in permafrost zones are characterized by an extremely wide range of their sizes, from several m² to hundreds of thousands of hectares. To explore this space, we use medium-resolution optical and radar images (Landsat, ERS-2, and ENVISAT), high-resolution images (Kanopus-V, BKA, and Alos), and ultra-high-resolution images (Resurs-P, QuickBird, and GeoEye-1). To minimize the seasonal fluctuations in the water level of the lakes, we select the images for a fairly short period of the summer season, from July to August. During this period, the ice cover on the lakes completely disappears, and the lakes can be identified when decoding images. We process the images using the standard means of geographic information systems, ArcGIS and ENVI.

![Figure 11.11: Diagram of test regions.](images/fig11_11.jpg)

[Figure 11.11:](#chapter11.xhtml#f11_11b) Diagram of test regions.

According to \[24\], for lakes with an area of 2 *ha* and more, the remote measurement error of lake areas based on satellite images does not exceed 5%. As reference images, we take the ultra-high resolution QuickBird images (0.7 *m* ²). For illustration, a fragment of the Landsat-5 satellite image (July 13, 2007) is presented below. It shows the system of thermokarst lakes ([Fig. 11.12(a)](#chapter11.xhtml#f11_12)) and the result of its decoding ([Fig. 11.12(b)](#chapter11.xhtml#f11_12)).

![Figure 11.12: Satellite images.](images/fig11_12.jpg)

[Figure 11.12:](#chapter11.xhtml#f11_12b) Satellite images.

An important problem for the evolution of thermokarst lakes is identifying the climatic parameters that affect their number and area. As is indicated by 1973–2007 data for 30 test domains in different permafrost zones, the average annual temperature and the annual precipitation have the greatest impact on the evolution of thermokarst lakes. For the Western Siberia territory under study, these climatic parameters were obtained using the ERA-40, ERA-INTERIM and APHRODITE JMA meteorological field reanalysis systems; for details, see \[[131](#refbib.xhtml#r131), [133](#refbib.xhtml#r133)\]. For the territory considered in this paper, the average annual temperature and the annual precipitation have a multidirectional relationship: an increase in the former is accompanied by a decrease in the latter precipitation \[131\]. A similar relationship was established in Alaska \[154\] and Eastern Siberia \[[130](#refbib.xhtml#r130), [132](#refbib.xhtml#r132), [195](#refbib.xhtml#r195)\].

The total number of lakes in the permafrost zone of Western Siberia reaches 8.7 million, with a total area of about 6.4 million *ha*. Of these, nearly one half (44%) is occupied by ultra-small lakes (less than 500 *m* ²), which form merely 0.1% of the total area of all thermokarst lakes. Large lakes (more than 2 × 10⁴ *m* ²) make up 86.6% of the total area, but their number does not exceed 3.6% of the total number of all thermokarst lakes.

### 11.4.3Structures of randomized models of thermokarst lakes state

An important stage in the technology of randomized forecasting is to construct randomized models of thermokarst lakes area evolution as well as randomized models of the average annual temperature and the annual precipitation affecting this evolution. These variables will be modeled using linear dynamic randomized regressions \[10\] with random parameters (LDRR).

The temporal evolution of the lakes area *S\[n\]* (*LDRR-LA*) is described by the following dynamic randomized regression equation with two influencing factors, the average annual temperature *T\[n\]* and the annual sum of precipitation *R\[n\]*:

  
$$\\begin{aligned} {S\\lbrack n\\rbrack} & {= a\_{0} + {\\sum\\limits\_{k = 1}^{p}a\_{k}}S\\lbrack n - k\\rbrack + a\_{(p + 1)}T\\lbrack n\\rbrack + a\_{(p + 2)}R\\lbrack n\\rbrack,} \\\\ {v\\lbrack n\\rbrack} & {= S\\lbrack n\\rbrack + \\xi\\lbrack n\\rbrack.} \\\\ \\end{aligned}$$  
(11.51)

The parameters

  
$$\\begin{aligned} & {a\_{k} \\in \\mathcal{A}\_{k} = \\lbrack a\_{k}^{-},a\_{k}^{+}\\rbrack,\\quad k = \\overline{0,(p+2)},} \\\\ & {\\mathbf{a} = \\left\\{ a\_{0},\\ldots,a\_{p},a\_{p + 1},a\_{p + 2} \\right\\} \\in \\mathcal{A} = {\\underset{k = 0}{\\overset{p + 2}{\\cup}}\\mathcal{A}\_{k}}} \\\\ \\end{aligned}$$  
(11.52)

are random with a PDF *P*(**a**).

The variable *v\[n\]* is the observed output of the model, and the values of the random measurement noise *ξ*\[*n*\] at different time instants *n* may belong to different ranges:

  
$$\\begin{array}{r} {\\xi\\lbrack n\\rbrack \\in \\Xi\_{n} = \\lbrack\\xi^{-}\\lbrack n\\rbrack,\\xi^{+}\\lbrack n\\rbrack\\rbrack,} \\\\ \\end{array}$$  
(11.53)

with a PDF $Q\_{n}(\\xi\\lbrack n\\rbrack),\\, n = \\overline{0,N}.$

To train this model (estimate the PDFs *P*(**a**) and *Q*[*n*](*ξ*\[*n*\])), we utilize the existing collections of historical data on the lakes area, the average annual temperature, and the annual precipitation.

However, at the stage of lakes area forecasting, data on temperature and precipitation are not available. To generate necessary data at this stage, we construct auxiliary models of temperature (*LDRR-T*) and precipitation (*LDRR-P*) and supply random sequences *μ*\[*n*\] and *ζ*\[*n*\], respectively, to their inputs.

Consider the temperature model (*LDRR-T*):

  
$$\\begin{aligned} {T\\lbrack n\\rbrack} & {= b\_{0} + {\\sum\\limits\_{k = 1}^{p}b\_{k}}T\\lbrack n - k\\rbrack + \\mu\\lbrack n\\rbrack,} \\\\ {t\\lbrack n\\rbrack} & {= T\\lbrack n\\rbrack + \\eta\\lbrack n\\rbrack.} \\\\ \\end{aligned}$$  
(11.54)

The random parameters of this model are of the interval type:

  
$$\\begin{aligned} & {b\_{k} \\in \\mathcal{B}\_{k} = \\lbrack b\_{k}^{-},b\_{k}^{+}\\rbrack,\\quad k = \\overline{0,p},} \\\\ & {\\mathbf{b} = \\left\\{ b\_{0},\\ldots,b\_{p} \\right\\},\\quad\\mathbf{b} \\in \\mathcal{B} = {\\underset{k = 0}{\\overset{p}{\\cup}}\\mathcal{B}\_{k}}.} \\\\ \\end{aligned}$$  
(11.55)

The random input sequence is

  
$$\\begin{aligned} & {\\mu\\lbrack n\\rbrack \\in \\mathcal{M}\_{n} = \\lbrack\\mu^{-}\\lbrack n\\rbrack,\\mu^{+}\\lbrack n\\rbrack\\rbrack,\\,\\, n = \\overline{0,N},} \\\\ & {\\mu = \\left\\{ \\mu\\lbrack 0\\rbrack,\\ldots,\\mu\\lbrack N\\rbrack \\right\\},\\quad\\mu \\in \\mathcal{M} = {\\underset{n = 0}{\\overset{N}{\\cup}}\\mathcal{M}\_{n}}.} \\\\ \\end{aligned}$$  
(11.56)

The random parameters and the input sequence are characterized by a joint PDF *W*(**b**, *μ*).

The variable *t\[n\]* is the observed output of the model, and the measurement noise *η*\[*n*\] ∈ ℰ[*n*] = \[*η*^−\[*n*\], *η*^+\[*n*\]\] is of the interval type with PDFs *E*[*n*](*η*\[*n*\]).

The precipitation model (*LDRR-P*) has the form:

  
$$\\begin{aligned} {R\\lbrack n\\rbrack} & {= c\_{0} + {\\sum\\limits\_{k = 1}^{p}c\_{k}}R\\lbrack n - k\\rbrack + \\zeta\\lbrack n\\rbrack,} \\\\ {r\\lbrack n\\rbrack} & {= R\\lbrack n\\rbrack + \\chi\\lbrack n\\rbrack.} \\\\ \\end{aligned}$$  
(11.57)

The random parameters of this model are independent and of the interval type:

  
$$\\begin{aligned} & {c\_{k} \\in \\mathcal{C}\_{k} = \\lbrack c\_{k}^{-},c\_{k}^{+}\\rbrack,\\quad k = \\overline{0,p},} \\\\ & {\\mathbf{c} = \\left\\{ c\_{0},\\ldots,c\_{p} \\right\\},\\quad\\mathbf{c} \\in \\mathcal{C} = {\\underset{k = 0}{\\overset{p}{\\cup}}\\mathcal{C}\_{k}}.} \\\\ \\end{aligned}$$  
(11.58)

The random input sequence is

  
$$\\begin{aligned} & {\\zeta\\lbrack n\\rbrack \\in \\mathcal{Z}\_{n} = \\lbrack\\zeta^{-}\\lbrack n\\rbrack,\\zeta^{+}\\lbrack n\\rbrack\\rbrack,\\quad\\, n = \\overline{0,N},} \\\\ & {\\zeta = \\left\\{ \\zeta\\lbrack 0\\rbrack,\\ldots,\\zeta\\lbrack N\\rbrack \\right\\},\\quad\\zeta \\in \\mathcal{Z} = {\\underset{n = 0}{\\overset{N}{\\cup}}\\mathcal{Z}\_{n}}.} \\\\ \\end{aligned}$$  
(11.59)

The random parameters and the input sequence are characterized by a joint PDF *F*(**c**, *ζ*).

The variable *r\[n\]* is the observed output of the model, and the measurement noise *χ*\[*n*\] ∈ 𝒢[*n*] = \[*χ*^−\[*n*\], *χ*^+\[*n*\]\] is of the interval type with PDFs *G*[*n*](*χ*\[*n*\]).

The variation in the average annual temperature and the annual precipitation are the input variables for *LDRR-A*. The general model of thermokarst lakes area evolution (LDRR) is shown in [Fig. 11.13](#chapter11.xhtml#f11_13).

![Figure 11.13: Structural diagram of LDRR.](images/fig11_13.jpg)

[Figure 11.13:](#chapter11.xhtml#f11_13b) Structural diagram of LDRR.

### 11.4.4Data on the state of thermokarst lakes

The state of regional thermokarst lakes is characterized by their total area *S*^((*r*))\[*n*\] in region *r*, measured in (*ha*), and the factors influencing thermokarst formations—the average annual temperatures *T*^((*r*))\[*n*\], measured in (*C*^∘), and the annual sums precipitation *R*^((*r*))\[*n*\], measured in (*mm*), where *n* denotes calendar year.

[Figure 11.11](#chapter11.xhtml#f11_11) shows a fragment of the Western Siberia map covering the range 65⁰*N* to  − 70⁰*N* and 65⁰*E* to  − 95⁰*E*, including test domains in which temperature and precipitation were measured, and the areas of lakes were calculated based on the cosmic sensing of the earth surface.

The distribution of test regions by zones is as follows:

*   zone *C*: 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 30;
    
*   zone *D*: 9, 10, 11, 12, 13, 14, 15, 16, 25, 26;
    
*   zone *I*: 1, 2, 3, 4, 5, 6, 7, 8.
    

The data characterizing the state of these test domains were presented in \[[1](#refbib.xhtml#r1)\]. To eliminate the scale effect, they are normalized, i.e., reduced to the interval \[0,1\], using the relations

  
$$\\begin{aligned} {S\_{t}^{\\prime}\\lbrack n\\rbrack} & {= \\frac{S\_{t}^{(r)}\\lbrack n\\rbrack - S\_{t}^{min}}{S\_{t}^{max} - S\_{t}^{min}},\\,\\, T\_{t}^{\\prime}\\lbrack n\\rbrack = \\frac{T\_{t}^{(r)}\\lbrack n\\rbrack - T\_{t}^{min}}{T\_{t}^{max} - T\_{t}^{min}},} \\\\ & {\\text{\\quad\\quad}R\_{t}^{\\prime}\\lbrack n\\rbrack = \\frac{R\_{t}^{(r)}\\lbrack n\\rbrack - R\_{t}^{min}}{R\_{t}^{max} - T\_{t}^{min}},} \\\\ & {\\text{\\quad\\quad}\\quad t = \\overline{1,30},\\quad n = \\overline{0,34}.} \\\\ \\end{aligned}$$  
(11.60)

According to the tabulated data in \[1\], the data on lakes' surface area have many omissions. We restore them by the randomized reconstruction method of missing data described in \[[151](#refbib.xhtml#r151)\].

Since the test domains are located in their zones rather compactly, the collections of normalized means for each data zone are formed, which will be used for training, testing, and forecasting:

*   —for zone *C*,
    
      
    $$\\begin{aligned} {{\\overline{S}}^{(r)}\\lbrack n\\rbrack} & {= \\frac{1}{12}{\\sum\\limits\_{t \\in C}S\_{t}^{\\prime}}\\lbrack n\\rbrack,\\,\\,{\\overline{T}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{12}{\\sum\\limits\_{t \\in C}T\_{t}^{\\prime}}\\lbrack n\\rbrack,} \\\\ & {\\quad{\\overline{R}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{12}{\\sum\\limits\_{t \\in C}R\_{t}^{\\prime}}\\lbrack n\\rbrack;} \\\\ \\end{aligned}$$  
    (11.61)
    
*   —for zone *D*,
    
      
    $$\\begin{array}{r} {{\\overline{S}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{10}{\\sum\\limits\_{t \\in D}S\_{t}^{\\prime}}\\lbrack n\\rbrack,\\,\\,{\\overline{T}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{10}{\\sum\\limits\_{t \\in D}T\_{t}^{\\prime}}\\lbrack n\\rbrack,{\\overline{R}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{10}{\\sum\\limits\_{t \\in D}R\_{t}^{\\prime}}\\lbrack n\\rbrack;} \\\\ \\end{array}$$  
    
*   —for zone *I*,
    
      
    $$\\begin{array}{r} {{\\overline{S}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{8}{\\sum\\limits\_{t \\in I}S\_{t}^{\\prime}}\\lbrack n\\rbrack,\\,\\,{\\overline{T}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{8}{\\sum\\limits\_{t \\in I}T\_{t}^{\\prime}}\\lbrack n\\rbrack,{\\overline{R}}^{(r)}\\lbrack n\\rbrack = \\frac{1}{8}{\\sum\\limits\_{t \\in I}R\_{t}^{\\prime}}\\lbrack n\\rbrack.} \\\\ \\end{array}$$  
    

We use these data to calculate the structural characteristics of the LDRR model, namely, the order *p* as well as the lower and upper limits of the ranges for the model parameters and measurement noises. The algorithm takes the form:

![Algorithm 1 Parameters and measurement noises ranges.](images/comp11_1.jpg)

Algorithm 1 Parameters and measurement noises ranges.

 [Table 11.10:](#chapter11.xhtml#t11_10b) Structural characteristics of LDRR. 

 
|  |
| --- |
| **Zone C** |
| Model || Order || Parameter || Parameter range || Noise range |
| --- | --- | --- | --- | --- |
| *p* || lower limit || upper limit || lower limit || upper limit |
| *S* || 4 || *a*[0] || \-0.5022 || 0.0747 || \-0.4280 || 0.4280 |
| *a*[1] || \-0.1366 || 0.5221 |
| *a*[2] || \-0.4877 || 0.1982 |
| *a*[3] || \-0.5277 || 0.1906 |
| *a*[4] || \-0.4412 || 0.1905 |
| *a*[5] || 0.4605 || 1.1440 |
| *a*[6] || 0.1877 || 0.8777 |
| *T* || 3 || *b*[0] || \-0.0555 || 0.7512 || \-0.6920 || 0.6920 |
| *b*[0] || \-0.4863 || 0.6904 |
| *b*[1] || \-0.2523 || 0.8608 |
| *b*[2] || \-0.7525 || 0.4532 |
| *R* || 6 || *c*[0] || 0.2200 || 0.7412 || \-0.5489 || 0.5489 |
| *c*[1] || \-0.0420 || 1.1450 |
| *c*[1] || \-0.5680 || 0.8050 |
| *c*[2] || \-0.1511 || 1.1894 |
| *c*[3] || \-0.9627 || 0.3813 |
| *c*[4] || \-0.7177 || 0.7271 |
| *c*[5] || \-1.0302 || 0.3402 |
|  |

 

[Table 11.11:](#chapter11.xhtml#t11_11b) Structural characteristics of LDRR

 
|  |
| --- |
| **Zone D** |
| Model || Order || Parameter || Parameter range || Noise range |
| --- | --- | --- | --- | --- |
| *p* || lower limit || upper limit || lower limit || upper limit |
| *S* || 4 || *a*[0] || \-0.2180 || 0.4536 || \-0.3041 || 0.3041 |
| *a*[1] || \-0.2899 || 0.3146 |
| *a*[2] || \-0.0934 || 0.5434 |
| *a*[3] || \-0.3397 || 0.2687 |
| *a*[4] || \-0.3727 || 0.2104 |
| *a*[5] || 0.5365 || 1.1209 |
| *a*[6] || \-0.3038 || 0.1809 |
| *T* || 4 || *b*[0] || 0.0064 || 0.9432 || \-0.6100 || 0.6100 |
| *b*[1] || \-0.6889 || 0.5007 |
| *b*[1] || \-0.1742 || 1.0105 |
| *b*[2] || \-0.8446 || 0.3379 |
| *b*[3] || \-0.7874 || 0.4332 |
| *R* || 4 || *c*[0] || \-0.4305 || 0.6808 || \-0.5006 || 0.5006 |
| *c*[1] || 0.2060 || 1.3253 |
| *c*[1] || \-0.7124 || 0.6210 |
| *c*[2] || \-0.3067 || 1.0510 |
| *c*[3] || \-0.9575 || 0.3755 |
|  |

 

[Table 11.12:](#chapter11.xhtml#t11_12b) Structural characteristics of LDRR.

 
|  |
| --- |
| **Zone I** |
| Model || Order || Parameter || Parameter range || Noise range |
| --- | --- | --- | --- | --- |
| *p* || lower limit || upper limit || lower limit || upper limit |
| *S* || 5 || *a*[0] || \-0.3191 || 0.1600 || \-0.2210 || 0.2210 |
| *a*[1] || \-0.2690 || 0.0804 |
| *a*[2] || \-0.1893 || 0.1498 |
| *a*[3] || \-0.1686 || 0.1679 |
| *a*[4] || \-0.2009 || 0.1333 |
| *a*[5] || \-0.2527 || 0.0863 |
| *a*[6] || 0.9226 || 1.2945 |
| *a*[7] || \-0.2073 || 0.2157 |
| *T* || 4 || *b*[0] || 0.0341 || 0.4649 || \-0.7110 || 0.7110 |
| *b*[1] || \-0.6822 || 0.4936 |
| *b*[1] || \-0.1626 || 0.9894 |
| *b*[2] || \-0.8443 || 0.3193 |
| *b*[3] || \-0.8135 || 0.3945 |
| *R* || 4 || *c*[0] || \-0.3217 || 0.4938 || \-0.4661 || 0.4661 |
| *c*[1] || 0.1180 || 1.2049 |
| *c*[1] || \-0.5728 || 0.6302 |
| *c*[2] || \-0.3641 || 1.1894 |
| *c*[3] || \-0.6541 || 0.4912 |
|  |

Consequently, there are three time series for each zone, each containing 35 values. We divide them into two groups as follows:

*   the training collections ($n = \\overline{0,24}$)
    
      
    $$\\begin{array}{r} {{\\mathfrak{C}}\_{tn}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)}\\lbrack n\\rbrack,R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathfrak{D}\_{tn}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)\\lbrack n\\rbrack},R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  
    
    and
    
      
    $$\\begin{array}{r} {\\Im\_{tn}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)\\lbrack n\\rbrack},R^{(r)}\\lbrack n\\rbrack} \\right)} \\\\ \\end{array}$$  
    
    for zones *C*, *D* and *I*, respectively;
    
*   the testing collections ($n = \\overline{25,34}$)
    
      
    $$\\begin{array}{r} {{\\mathfrak{C}}\_{ts}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)}\\lbrack n\\rbrack,R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{r} {\\mathfrak{D}\_{ts}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)\\lbrack n\\rbrack},R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  
    
    and
    
      
    $$\\begin{array}{r} {\\Im\_{ts}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)}\\lbrack n\\rbrack,R^{(r)}\\lbrack n\\rbrack} \\right)} \\\\ \\end{array}$$  
    
    for zones *C*, *D*, and *I*, respectively.
    

### 11.4.5Entropy-Randomized machine learning of *LDRR*

#### 11.4.5.1Formation of data sets to train *LDRR*

The available dataset is divided in a proportion of 70% to 30% for model training and testing, respectively. The training procedure will be performed separately for *LDRR-LA*, *LDRR-T* and *LDRR-P*.

To train the model, we use the data from the training collection (${\\mathfrak{C}}\_{tn}\\lbrack n\\rbrack,\\,\\mathfrak{D}\_{tn}\\lbrack n\\rbrack,\\,\\Im\_{tn}\\lbrack n\\rbrack,\\,\\, n = \\overline{0,24}$).

From the historical data we construct the column vectors

  
$$\\begin{aligned} & {\\mathbf{S}\_{(n - p)}^{(r)} = \\left\\{ 1,S^{r}\\lbrack n - 1\\rbrack,\\ldots,S^{(r)}\\lbrack n - p\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\mathbf{S}\_{(p)}^{(r)} = \\left\\{ S^{(r)}\\lbrack p\\rbrack,\\ldots,S^{(r)}\\lbrack 24\\rbrack \\right\\},} \\\\ & {\\mathbf{T}\_{(n - p)}^{(r)} = \\left\\{ 1,T^{(r)}\\lbrack n - 1\\rbrack,\\ldots,T^{(r)}\\lbrack n - p\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\mathbf{T}\_{(p)}^{(r)} = \\left\\{ T^{(r)}\\lbrack p\\rbrack,\\ldots,T^{(r)}\\lbrack 24\\rbrack \\right\\},} \\\\ \\end{aligned}$$  
(11.62)

  
$$\\begin{aligned} & {\\mathbf{R}\_{(n - p)}^{(r)} = \\left\\{ 1,R^{(r)}\\lbrack n - 1\\rbrack,\\ldots,R^{(r)}\\lbrack n - p\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\mathbf{R}\_{(p)}^{(r)} = \\left\\{ R^{(r)}\\lbrack p\\rbrack,\\ldots,R^{(r)}\\lbrack 24\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}n = \\overline{p,24},} \\\\ \\end{aligned}$$  
(11.63)

and the matrices

  
$$\\begin{array}{r} {S\_{p}^{(r)} = \\left( \\begin{array}{l} \\mathbf{S}\_{(0)} \\\\ \\cdots \\\\ \\mathbf{S}\_{(24 - p)} \\\\ \\end{array} \\right),\\quad T\_{p}^{(r)} = \\left( \\begin{array}{l} \\mathbf{T}\_{(0)} \\\\ \\cdots \\\\ \\mathbf{T}\_{(24 - p)} \\\\ \\end{array} \\right),\\quad R\_{p}^{(r)} = \\left( \\begin{array}{l} \\mathbf{R}\_{(0)} \\\\ \\cdots \\\\ \\mathbf{R}\_{(24 - p)} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
(11.64)

#### 11.4.5.2ERML algorithm

We apply the randomized machine learning method (see Section 3) to estimate the PDFs of the model parameters and measurement noises. The ERML algorithm for *LDRR-LA* has the form

  
$$\\begin{aligned} & {\\mathcal{H}\\lbrack P(\\mathbf{a},Q(\\xi)\\rbrack = - {\\int\_{\\mathcal{A}}\\,}P(\\mathbf{a})\\,\\ln P(\\mathbf{a})\\, d\\mathbf{a} -} \\\\ & \\left. {\\sum\\limits\_{n = p}^{24}{\\int\_{\\Xi\_{n}}\\,}}Q\_{n}(\\xi\\lbrack n\\rbrack)\\,\\ln Q\_{n}(\\xi\\lbrack n\\rbrack)\\, d\\xi\\lbrack n\\rbrack\\Rightarrow\\max \\right. \\\\ \\end{aligned}$$  
(11.65)

subject to the constraints

  
$$\\begin{aligned} {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\, d\\mathbf{a} = 1,} & {\\quad{\\int\_{\\Xi\_{n}}Q\_{n}}(\\xi\\lbrack n\\rbrack)\\, d\\xi\\lbrack n\\rbrack = 1,} \\\\ {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})D\_{(n - p)}^{(r)}\\,\\mathbf{a}\\, d\\mathbf{a} +} & {{\\int\_{\\Xi\_{n}}Q}(\\xi\\lbrack n\\rbrack)\\xi\\lbrack n\\rbrack\\, d\\xi\\lbrack n\\rbrack = S^{(r)}\\lbrack n\\rbrack,} \\\\ & {\\text{\\quad\\quad}n = \\overline{p,24},} \\\\ \\end{aligned}$$  
(11.66)

with the block matrix

  
$$\\begin{array}{r} {D\_{(n - p)}^{(r)} = \\left\\lbrack {\\mathbf{S}\_{(n - p)}^{(r)},\\, T\_{(p)}^{(r)}\\lbrack n\\rbrack,\\, R\_{(p)}^{(r)}\\lbrack n\\rbrack} \\right\\rbrack.} \\\\ \\end{array}$$  
(11.67)

The solution of this problem, parametrized by the Lagrange multipliers *θ* = {*θ*[*p*],…,*θ*[24]}, is given by

  
$$\\begin{aligned} & {P^{\*}(\\mathbf{a},\\theta) = \\frac{\\exp\\left( {- \\left\\langle \\theta,D\_{(n - p)}^{(r)}\\,\\mathbf{a} \\right\\rangle} \\right)}{\\mathcal{P}(\\theta)},} \\\\ & {\\mathcal{P}(\\theta) = {\\int\_{\\mathcal{A}}\\exp}\\left( {- \\left\\langle \\theta,D\_{(n - p)}^{(r)}\\,\\mathbf{a} \\right\\rangle} \\right)\\, d\\mathbf{a}.} \\\\ \\end{aligned}$$  
(11.68)

The measurement noise for *LDRR-LA* has the entropy-optimal PDFs

  
$$\\begin{aligned} & {Q\_{n}^{\*}(\\xi\\lbrack n\\rbrack,\\theta\_{n}) = \\frac{\\exp( - \\xi\\lbrack n\\rbrack\\theta\_{n})}{\\mathcal{Q}\_{n}(\\theta\_{n})},} \\\\ & {\\mathcal{Q}\_{n}(\\theta\_{n}) = {\\int\_{\\Xi\_{n}}\\exp}( - \\xi\\lbrack n\\rbrack\\,\\theta\_{n})d\\,\\xi\\lbrack n\\rbrack.} \\\\ \\end{aligned}$$  
(11.69)

The Lagrange multipliers *θ* are calculated from the system of equations

  
$$\\begin{aligned} {\\mathcal{P}^{- 1}(\\theta)\\int\_{\\mathcal{A}}\\exp} & {\\left( {- \\left\\langle \\theta,D\_{(n - p)}^{(r)}\\,\\mathbf{a} \\right\\rangle} \\right)\\, D\_{(n - p)}^{(r)}\\mathbf{a}\\, d\\,\\mathbf{a} +} \\\\ {+ \\mathcal{Q}\_{n}^{- 1}(\\theta)\\int\_{\\Xi}} & {\\exp( - \\xi\\lbrack n\\rbrack\\,\\theta\_{n})\\, d\\xi\\lbrack n\\rbrack = S^{(r)}\\lbrack n\\rbrack,} \\\\ & {\\quad n = \\overline{p,24}.} \\\\ \\end{aligned}$$  
(11.70)

For *LDRR-T* and *LDRR-P*, the RML algorithm differs from (11.4.5.2, 11.4.5.2): it is necessary to estimate the joint PDFs *W*(**b**, *μ*) and *F*(**c**, *ζ*) of the model parameters and random input sequences as well as the PDFs *E*(*η*) and *G*(*χ*) of the measurement noises.

Adapting the ERML algorithm for *LDRR-T*, we obtain the following optimization problem:

  
$$\\begin{aligned} & {\\mathcal{H}\\lbrack W(\\mathbf{b},\\mu),E(\\eta)\\rbrack = - {\\int\_{\\mathcal{B}{\\cap \\mathcal{M}}}\\,}W(\\mathbf{b},\\mu)\\,\\ln W(\\mathbf{b},\\mu)\\, d\\mathbf{b}\\, d\\mu -} \\\\ & \\left. \\text{\\quad\\quad} - {\\sum\\limits\_{n = p}^{24}{\\int\_{\\mathcal{E}\_{n}}\\,}}E\_{n}(\\eta\\lbrack n\\rbrack)\\,\\ln E\_{n}(\\eta\\lbrack n\\rbrack)\\, d\\eta\\lbrack n\\rbrack\\Rightarrow\\max \\right. \\\\ \\end{aligned}$$  
(11.71)

subject to the constraints

  
$$\\begin{aligned} & {{\\int\_{\\mathcal{B}{\\cap \\mathcal{M}}}W}(\\mathbf{b},\\mu)\\, d\\mathbf{b}d\\mu = 1,\\quad{\\int\_{\\mathcal{E}\_{n}}E\_{n}}(\\eta\\lbrack n\\rbrack)\\, d\\,\\eta\\lbrack n\\rbrack = 1,} \\\\ & {\\text{\\quad\\quad}{\\int\_{\\mathcal{B}{\\cap \\mathcal{M}}}\\,}W(\\mathbf{b},\\mu)\\left\\lbrack {T\_{(n - p)}^{(r)}\\mathbf{b} + \\mu\\lbrack n\\rbrack} \\right\\rbrack\\, d\\,\\mathbf{b}\\, d\\,\\mu\\lbrack n\\rbrack +} \\\\ & {\\text{\\quad\\quad}\\quad + {\\int\_{\\mathcal{E}\_{n}}E\_{n}}(\\eta\\lbrack n\\rbrack)\\eta\\lbrack n\\rbrack\\, d\\,\\eta\\lbrack n\\rbrack = T^{(r)}\\lbrack n\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}n = \\overline{p,24}.} \\\\ \\end{aligned}$$  
(11.72)

The expressions (11.4.5.2, 11.4.5.2) incorporate the vector *μ* = {*μ*\[*p*\],…,*μ*\[24\]}.

Let *ϑ* = {*ϑ*[*p*],…,*ϑ*[7 + *p*]} be the Lagrange multipliers for this problem. The linear model has random parameters and the auxiliary random sequence on the input. The solution of this problem, representing the optimal PDFs, can be therefore written as

  
$$\\begin{aligned} {W^{\*}(\\mathbf{b},\\mu,\\vartheta) =} & {L^{\*}(\\mathbf{b},\\vartheta)\\, M^{\*}(\\mu,\\vartheta),\\quad M^{\*}(\\mu,\\vartheta) = {\\prod\\limits\_{n = p}^{24}M\_{n}^{\*}}(\\mu\\lbrack n\\rbrack,\\vartheta\_{n})} \\\\ & {\\quad L^{\*}(\\mathbf{b},\\vartheta) = \\frac{\\exp\\left( {- \\left\\langle \\vartheta,T\_{(n - p)}^{(r)}\\,\\mathbf{b} \\right\\rangle} \\right)}{\\mathcal{L}(\\vartheta)},} \\\\ & {\\quad\\mathcal{L}(\\vartheta) = {\\int\_{\\mathcal{B}}\\exp}\\left( {- \\left\\langle \\vartheta,T\_{(n - p)}^{(r)}\\,\\mathbf{b} \\right\\rangle} \\right)\\, d\\,\\mathbf{b},} \\\\ & {\\quad M\_{n}^{\*}(\\mu\\lbrack n\\rbrack,\\,\\vartheta\_{n}) = \\mathbb{M}\_{n}^{- 1}(\\vartheta\_{n})\\exp\\left( {- \\vartheta\_{n}\\mu\\lbrack n\\rbrack} \\right),} \\\\ & {\\quad\\mathbb{M}\_{n}(\\vartheta\_{n}) = {\\int\_{\\mathcal{M}\_{n}}\\,}\\exp\\left( {- \\vartheta\_{n}\\mu\\lbrack n\\rbrack} \\right)d\\,\\mu\\lbrack n\\rbrack,} \\\\ & {\\quad E\_{n}^{\*}(\\eta\\lbrack n\\rbrack,\\vartheta\_{n}) = \\mathbb{E}\_{n}^{- 1}(\\vartheta\_{n})\\exp\\left( {- \\eta\\lbrack n\\rbrack\\,\\vartheta\_{n}} \\right),} \\\\ & {\\quad\\mathbb{E}\_{n}(\\vartheta\_{n}) = {\\int\_{\\mathcal{E}\_{n}}\\exp}\\left( {- \\eta\\lbrack n\\rbrack\\,\\vartheta\_{n}} \\right)d\\,\\eta\\lbrack n\\rbrack,} \\\\ \\end{aligned}$$  
(11.73)

where the Lagrange multipliers *ϑ* satisfy the system of equations

  
$$\\begin{aligned} & {\\text{\\quad\\quad}\\mathcal{L}^{- 1}(\\vartheta)\\,{\\int\_{\\mathcal{B}}\\,}\\exp\\left( {- \\left\\langle \\vartheta,T\_{(n - p)}^{(r)}\\,\\mathbf{b} \\right\\rangle} \\right)T\_{(n - p)}^{(r)}\\,\\mathbf{b}\\, d\\mathbf{b} +} \\\\ & {\\quad\\text{\\quad\\quad} + \\mathbb{M}\_{n}^{- 1}(\\vartheta\_{n}){\\int\_{\\mathcal{M}\_{n}}M\_{n}^{\*}}(\\mu\\lbrack n\\rbrack,\\,\\vartheta\_{n})\\,\\mu\\lbrack n\\rbrack d\\mu\\lbrack n\\rbrack +} \\\\ & {+ \\mathbb{E}\_{n}^{- 1}(\\vartheta\_{n}){\\int\_{\\mathcal{E}\_{n}}E\_{n}^{\*}}(\\eta\\lbrack n\\rbrack,\\vartheta\_{n})\\,\\eta\\lbrack n\\rbrack d\\eta\\lbrack n\\rbrack = T^{(r)}\\lbrack n\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}n = \\overline{p,24}.} \\\\ \\end{aligned}$$  
(11.74)

For *LDRR-P*, the RML algorithm has a form similar to (11.4.5.2, 11.4.5.2):

  
$$\\begin{aligned} {F^{\*}(\\mathbf{c},\\zeta,\\lambda) =} & {V^{\*}(\\mathbf{c},\\lambda)\\, Z^{\*}(\\zeta,\\lambda),\\quad Z^{\*}(\\zeta,\\lambda) = {\\prod\\limits\_{n = p}^{24}Z\_{n}^{\*}}(\\zeta\\lbrack n\\rbrack,\\lambda\_{n}),} \\\\ & {V^{\*}(\\mathbf{c},\\lambda) = \\frac{\\exp\\left( {- \\left\\langle \\lambda,R\_{(n - p)}^{(r)}\\,\\mathbf{c} \\right\\rangle} \\right)}{\\mathcal{V}(\\lambda)},} \\\\ & {\\mathcal{V}(\\lambda) = {\\int\_{\\mathcal{C}}\\exp}\\left( {- \\left\\langle \\lambda,R\_{(n - p)}^{(r)}\\,\\mathbf{c} \\right\\rangle} \\right)\\, d\\,\\mathbf{c},} \\\\ & {Z\_{n}^{\*}(\\zeta\\lbrack n\\rbrack,\\lambda\_{n}) = {\\mathbb{Z}}\_{n}^{- 1}(\\lambda\_{n})\\exp\\left( {- \\lambda\_{n}\\,\\zeta\\lbrack n\\rbrack} \\right),} \\\\ & {{\\mathbb{Z}}\_{n}(\\lambda\_{n}) = {\\int\_{\\mathcal{Z}\_{n}}\\,}\\exp\\left( {- \\lambda\_{n}\\,\\zeta\\lbrack n\\rbrack} \\right)d\\,\\zeta\\lbrack n\\rbrack,} \\\\ & {G\_{n}^{\*}(\\chi\\lbrack n\\rbrack,\\lambda\_{n}) = \\mathbb{G}\_{n}^{- 1}(\\lambda)\\exp\\left( {- \\chi\\lbrack n\\rbrack\\lambda\_{n}} \\right),} \\\\ \\end{aligned}$$  
(11.75)

  
$$\\begin{aligned} & {\\mathbb{G}\_{n}(\\lambda\_{n}) = {\\int\_{\\mathcal{G}\_{n}}\\exp}\\left( {- \\chi\\lbrack n\\rbrack\\,\\lambda\_{n}} \\right)d\\,\\chi\\lbrack n\\rbrack,} \\\\ \\end{aligned}$$  
(11.76)

where the Lagrange multipliers *λ* = {*λ*[*p*],…,*λ*[24]} are determined from the system of equations

  
$$\\begin{array}{r} {\\text{\\quad\\quad}\\mathcal{V}^{- 1}(\\lambda)\\,{\\int\_{\\mathcal{C}}\\,}\\exp\\left( {- \\left\\langle \\lambda,R\_{(n - p)}^{(r)}\\,\\mathbf{c} \\right\\rangle} \\right)\\, R\_{(n - p)}^{(r)}\\,\\mathbf{c}\\, d\\mathbf{c} +} \\\\ {\\text{\\quad\\quad}\\text{\\quad\\quad}{\\mathbb{Z}}\_{n}^{- 1}(\\lambda\_{n}){\\int\_{\\mathcal{Z}\_{n}}Z\_{n}^{\*}}(\\zeta\\lbrack n\\rbrack,\\lambda\_{n})\\,\\zeta\\lbrack n\\rbrack d\\zeta\\lbrack n\\rbrack +} \\\\ {+ \\mathbb{G}\_{n}^{- 1}(\\lambda\_{n}){\\int\_{\\mathcal{G}\_{n}}G\_{n}^{\*}}(\\chi\\lbrack n\\rbrack,\\lambda\_{n})\\,\\chi\\lbrack n\\rbrack\\, d\\chi\\lbrack n\\rbrack = R^{(r)}\\lbrack n\\rbrack,} \\\\ {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}n = \\overline{p,24}.} \\\\ \\end{array}$$  
(11.77)

According to (11.4.5.2, 11.4.5.2, 11.4.5.2, 11.4.5.2), the entropy-optimal PDFs belong to the exponential class parametrized by the corresponding Lagrange multipliers, which are given by the balance equations (11.4.5.2, 11.4.5.2, 11.4.5.2).

Algorithms 2 and 3 are oriented to calculation residual for balance equations and restoration of entropy-optimal PDFs.

![Algorithm 2 Residual for balance equations.](images/comp11_2.jpg)

Algorithm 2 Residual for balance equations.

![Algorithm 3 Restoration of entropy-optimal PDFs.](images/comp11_3.jpg)

Algorithm 3 Restoration of entropy-optimal PDFs.

### 11.4.6Testing procedure, data and accuracy estimates

The testing procedure is applied to the following combination of the trained models:

*   *LDRR-LA*, with the testing collection ℭ[*t**s*]\[*n*\], 𝔇[*t**s*]\[*n*\], ℑ[*t**s*]\[*n*\];
    
*   *LDRR-T*, with *T*^((*r*))\[*n*\] from the testing collection;
    
*   *LDRR-P*, with *R*^((*r*))\[*n*\] from the testing collection.
    

When testing *LDRR-LA*, all components of the testing collections are used, and the model generates an output ensemble (the values of the lake areas) through sampling the entropy-optimal PDFs of its parameters and measurement noises.

![Algorithm 4 Sampling algorithm for PDFs.](images/comp11_4.jpg)

Algorithm 4 Sampling algorithm for PDFs.

When testing the trained *LDRR-T* and *LDRR-P* models, only the temperature and precipitation data from the testing collections are used. These models generate ensembles of the corresponding outputs for temperature and precipitation through sampling the entropy-optimal PDFs of their parameters and input sequences.

The accuracy of testing is characterized by the following indicators:

*   —the absolute mean squared error (in natural units)
    
      
    $$\\begin{array}{r} {AbsErr = \\Delta = \\sqrt{\\frac{1}{10}{\\sum\\limits\_{n = 25}^{34}\\left( {\\bullet^{(r)}\\lbrack n\\rbrack - \\hat{\\bullet}\\lbrack n\\rbrack} \\right)^{2}}};} \\\\ \\end{array}$$  
    (11.78)
    
*   —the relative mean squared error
    
      
    $$\\begin{aligned} {RelErr =} & {\\frac{\\Delta}{\\Delta\_{1} + \\Delta\_{2}},} \\\\ {\\Delta\_{1} = \\sqrt{\\frac{1}{10}{\\sum\\limits\_{n = 25}^{34}{( \\bullet^{(r)}\\lbrack n\\rbrack)}^{2}}},} & {\\Delta\_{2} = \\sqrt{\\frac{1}{10}{\\sum\\limits\_{n = 25}^{34}{(\\hat{\\bullet}\\lbrack n\\rbrack)}^{2}}}.} \\\\ \\end{aligned}$$  
    (11.79)
    

### 11.4.7Randomized forecasting of thermokarst lakes area evolution

The temporal evolution of the thermokarst lakes area is forecasted on time intervals exceeding the time interval for which the necessary data on the area and climatic parameters are available. In the case under consideration, the beginning of each forecasting interval refers to year 2008. We consider three time intervals as follows:

*   —short-term one, between years 2008 and 2013 ($n = \\overline{35,40}$);
    
*   —mid-term one, between years 2008 and 2018 ($n = \\overline{35,45}$);
    
*   —long-term one, between years 2008 and 2023 ($n = \\overline{35,50}$).
    

The temporal evolution of the thermokarst lakes area is forecasted using a composition of the trained randomized models (see [Fig. 11.13](#chapter11.xhtml#f11_13)) on the forecasting intervals specified above. The models from this composition are characterized by the entropy-optimal PDFs of their parameters, auxiliary random sequences, and measurement noises. The PDFs of the measurement noises are different for the time instants on the training interval: they depend on the time instant and the corresponding Lagrange multiplier. For example, the measurement noises for *LDRR-LA* have the PDF $Q\_{n}^{\*}(\\xi\\lbrack n\\rbrack,\\theta\_{n}),\\, n = \\overline{0,34}.$ For the forecasting procedure, we apply the PDFs averaged over the Lagrange multipliers.

Well, the blocks of the composite model are characterized by the following PDFs:

*   for *LDRR-LA*, *P*^(\*)(**a**) and $Q^{\*}(\\xi,\\overline{\\theta}),\\,\\,\\overline{\\theta} = \\frac{1}{34 - p}{\\sum\\limits\_{n = p}^{34}\\theta\_{n}};$
    
*   for *LDRR-T*, *L*^(\*)(**b**), $M^{\*}(\\mu,\\overline{\\vartheta}),$ and $E^{\*}(\\eta,\\overline{\\vartheta}),\\,\\overline{\\vartheta} = \\frac{1}{34 - p}{\\sum\\limits\_{n = p}^{34}\\vartheta\_{n}};$
    
*   for *LDRR-P*, *V*^(\*)(**c**), $Z^{\*}(\\zeta,\\overline{\\lambda}),$ and $G^{\*}(\\chi,\\overline{\\lambda}),\\,\\overline{\\lambda} = \\frac{1}{34 - p}{\\sum\\limits\_{n = p}^{34}\\lambda\_{n}}.$
    

These PDFs are sampled on the corresponding forecasting intervals, and the predictive ensembles of trajectories (lakes area variations) are generated via Monte Carlo simulations.

### 11.4.8Results of training, testing and forecasting the temporal evolution of thermokarst lakes area in Western Siberia

#### 11.4.8.1Randomized training (1973–1997)

Using ERML, we found the entropy-optimal PDFs of the model parameters, auxiliary random sequences, and measurement noises. The latter PDFs are parametrized by Lagrange multipliers.

LDRR-LA The analytical expressions for the corresponding parametrized PDFs are given by (11.4.5.2, 11.4.5.2). Since *LDRR-LA* is linear, these PDFs belong to the exponential class:

  
$$\\begin{aligned} {P^{\*}(\\mathbf{a},\\theta) =} & {{\\prod\\limits\_{k = 0}^{(p + 2)}P\_{k}^{\*}}\\left( a\_{k} \\right),\\,\\, P\_{k}^{\*}(a\_{k}) = \\frac{\\exp( - q\_{k}\\, a\_{k})}{\\mathcal{P}\_{k}},} \\\\ & {\\mathcal{P}\_{k} = \\int\_{\\mathcal{A}\_{k}}\\,\\exp( - q\_{k}\\, a\_{k})\\, da\_{k},} \\\\ {q\_{0} = \\sum\_{n = p}^{24}\\,\\theta\_{n},} & {q\_{k} = \\sum\_{n = p}^{24}\\,\\theta\_{n}\\, S^{(r)}\\lbrack n - k\\rbrack,\\quad k = \\overline{1,p},} \\\\ {q\_{p + 1} = \\sum\_{n = p}^{24}} & {\\theta\_{n}\\, T^{(r)}\\lbrack n\\rbrack,\\,\\, q\_{p + 2} = \\sum\_{n = p}^{24}\\,\\theta\_{n}\\, R^{(r)}\\lbrack n\\rbrack,} \\\\ {Q^{\*}(\\xi,\\overline{\\theta}) = \\frac{\\exp( - \\overline{\\theta}\\,\\xi)}{\\mathcal{Q}},} & {\\mathcal{Q} = \\int\_{\\Xi}\\,\\exp( - \\overline{\\theta}\\,\\xi)\\, d\\,\\xi,\\,\\,\\overline{\\theta} = \\frac{q\_{0}}{24 - p}.} \\\\ \\end{aligned}$$  
(11.80)

[Table 11.13](#chapter11.xhtml#t11_13) contains the values of the PDF parameters for *LDRR-LA* and zones *C, D* and *I*. These values can be used in the expressions for the entropy-optimal PDFs to obtain the same results as presented below.

 [Table 11.13:](#chapter11.xhtml#t11_13b) *LDRR-LA*: values of PDF parameters. 

 
|  |
| --- |
| Zones || *q*[0] || *q*[1] || *q*[2] || *q*[3] |
|  |
| --- |
| *C* || 0.1174 || 0.1331 || 0.0214 || \-0.0723 |
| *D* || \-0.0969 || 0.1077 || 0.1712 || 0.0296 |
| *I* || \-0.0176 || \-0.1560 || 0.0892 || \-0.0678 |
|  |
| Zones || *q*[4] || *q*[5] || *q*[6] || *q*[7] |
|  |
| *C* || \-0.0034 || \-0.0100 || \-0.0761 || \- |
| *D* || 0.0847 || \-0.1910 || \-0.0671 || \- |
| *I* || \-0.0716 || 0.0191 || \-0.0002 || 0.0120 |
|  |

[Figure 11.14](#chapter11.xhtml#f11_14) demonstrates some examples of the entropy-optimal PDFs *P*^(\*)(*a*[2], *a*[4]) (11.14(a)) (the model parameters) and *Q*^(\*)(*ξ*) (11.14(b)) (the measurement noise), which were restored through learning for zone *C*.

![Figure 11.14: Examples of restored PDFs.](images/fig11_14.jpg)

[Figure 11.14:](#chapter11.xhtml#f11_14b) Examples of restored PDFs.

A similar learning procedure is performed for the temperature and precipitation models for all zones *C, D* and *I*.

LDRR-T The analytical expressions for the corresponding PDFs are given by (11.4.5.2, 11.4.5.2). Due to the linearity of the model, we have:

  
$$\\begin{aligned} & {W^{\*}(\\mathbf{b},\\mu,\\vartheta) = L^{\*}(\\mathbf{b},\\vartheta)\\, M^{\*}(\\mu,\\vartheta),\\,\\, M^{\*}(\\mu,\\vartheta) = {\\prod\\limits\_{n = p}^{(24)}M\_{n}^{\*}}(\\mu\\lbrack n\\rbrack,\\vartheta\_{n}),} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}L^{\*}(\\mathbf{b},\\vartheta) = {\\prod\\limits\_{k = 0}^{p}L\_{k}^{\*}}\\left( b\_{k} \\right),\\,\\, L\_{k}^{\*}(b\_{k}) = \\frac{\\exp( - w\_{k}\\, b\_{k})}{\\mathcal{L}\_{k}},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathcal{L}\_{k} = {\\int\_{\\mathcal{B}\_{k}}\\,}\\exp( - w\_{k}\\, b\_{k})\\, db\_{k},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}w\_{0} = {\\sum\\limits\_{n = p}^{24}\\,}\\vartheta\_{n},\\,\\, w\_{k} = {\\sum\\limits\_{n = p}^{24}\\,}\\vartheta\_{n}\\, T^{(r)}\\lbrack n - k\\rbrack,\\quad k = \\overline{1,p},} \\\\ & {M\_{n}^{\*}(\\mu\\lbrack n\\rbrack,\\vartheta\_{n}) = \\frac{\\exp( - \\vartheta\_{n}\\,\\mu\\lbrack n\\rbrack)}{\\mathfrak{M}\_{n}},\\quad\\mathfrak{M}\_{n} = {\\int\_{\\mathcal{M}\_{n}}\\exp}( - \\vartheta\_{n}\\,\\mu\\lbrack n\\rbrack)\\, d\\mu\\lbrack n\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}E^{\*}(\\eta,\\overline{\\vartheta}) = \\frac{\\exp( - \\overline{\\vartheta}\\,\\eta)}{\\mathfrak{E}},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathfrak{E} = {\\int\_{\\mathcal{E}}\\,}\\exp( - \\overline{\\vartheta}\\,\\eta)\\, d\\,\\eta,\\,\\,\\overline{\\vartheta} = \\frac{w\_{0}}{24 - p}.} \\\\ \\end{aligned}$$  
(11.81)

[Table 11.14](#chapter11.xhtml#t11_14) shows the values of the PDF parameters for *LDRR-T* and zones *C, D* and *I*.

 

[Table 11.14:](#chapter11.xhtml#t11_14b) *LDRR-T*: values of PDF parameters.

 
|  |
| --- |
| Zones || *w*[0] || *w*[1] || *w*[2] || *w*[3] || *w*[4] |
|  |
| --- |
| *C* || 0.0431 || 0.0379 || 0.1703 || \-0.0864 || \- |
| *D* || \-0.0237 || \-0.0373 || 0.1839 || \-0.1296 || 0.1612 |
| *I* || \-0.0002 || 0.0040 || 0.0677 || \-0.0912 || 0.1426 |
|  |

LDRR-P The analytical expressions for the corresponding PDFs are given by (11.4.5.2, 11.4.5.2). Due to the linearity of the model, we have:

  
$$\\begin{aligned} & {F^{\*}(\\mathbf{c},\\zeta,\\chi) = V^{\*}(\\mathbf{c},\\lambda)\\, Z^{\*}(\\zeta,\\lambda),\\,\\, Z^{\*}(\\zeta,\\lambda) = {\\prod\\limits\_{n = p}^{(24)}Z\_{n}^{\*}}(\\zeta\\lbrack n\\rbrack,\\lambda\_{n}),} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}V^{\*}(\\mathbf{c},\\lambda) = {\\prod\\limits\_{k = 0}^{p}V\_{k}^{\*}}(c\_{k}),\\,\\, V\_{k}^{\*}(b\_{k}) = \\frac{\\exp( - s\_{k}\\, c\_{k})}{\\mathcal{V}\_{k}},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathcal{V}\_{k} = {\\int\_{\\mathcal{C}\_{k}}\\,}\\exp( - s\_{k}\\, c\_{k})\\, dc\_{k},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}s\_{0} = {\\sum\\limits\_{n = p}^{24}\\,}\\lambda\_{n},\\,\\, s\_{k} = {\\sum\\limits\_{n = p}^{24}\\,}\\lambda\_{n}\\, R^{(r)}\\lbrack n - k\\rbrack,\\quad k = \\overline{1,p},} \\\\ & {Z\_{n}^{\*}(\\zeta\\lbrack n\\rbrack,\\lambda\_{n}) = \\frac{\\exp( - \\lambda\_{n}\\,\\zeta\\lbrack n\\rbrack)}{{\\mathfrak{Z}}\_{n}},\\quad{\\mathfrak{Z}}\_{n} = {\\int\_{\\mathcal{Z}\_{n}}\\exp}( - \\lambda\_{n}\\,\\zeta\\lbrack n\\rbrack)\\, d\\zeta\\lbrack n\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}G^{\*}(\\chi,\\overline{\\lambda}) = \\frac{\\exp( - \\overline{\\lambda}\\,\\chi)}{\\mathfrak{G}},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathfrak{G} = {\\int\_{\\mathcal{G}}\\,}\\exp( - \\overline{\\lambda}\\,\\chi)\\, d\\,\\chi,\\,\\,\\overline{\\lambda} = \\frac{w\_{0}}{24 - p}.} \\\\ \\end{aligned}$$  
(11.82)

[Table 11.15](#chapter11.xhtml#t11_15) contains the values of the PDF parameters for *LDRR-P* and zones *C, D* and *I*.

 

[Table 11.15:](#chapter11.xhtml#t11_15b) *LDRR-P*: values of PDF parameters.

 
|  |
| --- |
| Zones || *s*[0] || *s*[1] || *s*[2] || *s*[3] || *s*[4] || *s*[5] || *s*[6] |
|  |
| --- |
| *C* || \-0.0287 || 0.0089 || 0.0264 || 0.0006 || \-0.0200 || \-0.0214 || 0.0431 |
| *D* || 0.0876 || \-0.1451 || \-0.0841 || \-0.0709 || 0.1307 || \- || \- |
| *I* || 0.0571 || \-0.0890 || \-0.0166 || 0.1140 || \-0.0794 || \- || \- |
|  |

#### 11.4.8.2Testing (1998–2007)

The testing procedure is applied to the combination of the trained models with the testing data collections.

This procedure is based on sampling of the optimal PDFs and further generation of the ensembles of random trajectories on the testing interval.

For zone *C*, the following ensembles are shown below:

*   the lakes area ensembles generated by *LDRR-LA* ([Fig. 11.15](#chapter11.xhtml#f11_15));
    
*   the temperature ensembles generated by *LDRR-T* ([Fig. 11.16](#chapter11.xhtml#f11_16));
    
*   the precipitation ensembles generated by *LDRR-P* ([Fig. 11.17](#chapter11.xhtml#f11_17)).
    

![Figure 11.15: Simulation modeling of lakes area.](images/fig11_15.jpg)

[Figure 11.15:](#chapter11.xhtml#f11_15b) Simulation modeling of lakes area.

![Figure 11.16: Simulation modeling of temperature.](images/fig11_16.jpg)

[Figure 11.16:](#chapter11.xhtml#f11_16b) Simulation modeling of temperature.

![Figure 11.17: Simulation modeling of precipitation.](images/fig11_17.jpg)

[Figure 11.17:](#chapter11.xhtml#f11_17b) Simulation modeling of precipitation.

[Table 11.16](#chapter11.xhtml#t11_16) presents the indicators of testing accuracy for all zones *C, D* and *I*.

 [Table 11.16:](#chapter11.xhtml#t11_16b) Absolute and relative testing errors. 

 
|  |
| --- |
| *LDRR-LA* |
| Zone || *C* || *D* || *I* |
| --- | --- | --- | --- |
| *AbsErr* || 0.3446 || 0.5354 || 1.3534 |
| *RelErr* || 0.0089 || 0.0135 || 0.014 |
|  |
| *LDRR-T* |
| *AbsErr* || 1.2863 || 1.1239 || 1.0284 |
| *RelErr* || 0.0801 || 0.1084 || 0.2215 |
|  |
| *LDRR-P* |
| *AbsErr* || 107.64 || 118.97 || 86.66 |
| *RelErr* || 0.1675 || 0.137 || 0.0947 |
|  |

#### 11.4.8.3Randomized forecasting (2008–2023)

All forecasts are constructed using the composite model ([Fig. 11.13](#chapter11.xhtml#f11_13)) consisting of *LDRR-LA*, *LDRR-T* and *LDRR-P*. The entropy-optimal PDFs generate the ensembles of trajectories describing the temporal evolution of the thermokarst lakes area on the forecasting interval. The difference between the forecasting and testing intervals is that in this case, all data points are used to train the models, and the structural characteristics of the models correspond to [Table 11.10](#chapter11.xhtml#t11_10), [Table 11.11](#chapter11.xhtml#t11_11), [Table 11.12](#chapter11.xhtml#t11_12).

For each point, the mean value (*mean*) and standard deviation (*std*) are calculated over the entire ensemble. The resulting forecasts for all zones are combined in [Table 11.17](#chapter11.xhtml#t11_17), [Table 11.18](#chapter11.xhtml#t11_18), [Table 11.19](#chapter11.xhtml#t11_19), starting from year 2007 for 5, 10 and 15 years, respectively.

 [Table 11.17:](#chapter11.xhtml#t11_17b) Forecasted evolution of thermokarst lakes area up to year 2012. 

 
|  |
| --- |
| Year || 2007 || 2008 || 2009 || 2010 || 2011 || 2012 |
|  |
| --- |
| *C* − *m**e**a**n* || 19.9252 || 19.2820 || 19.4881 || 19.4444 || 19.7255 || 19.8765 |
| *C* − *s**t**d* || \- || 0.5193 || 0.5509 || 0.5462 || 0.5623 || 0.5694 |
|  |
| *D* − *m**e**a**n* || 21.3674 || 18.8605 || 20.7156 || 19.0790 || 20.1559 || 19.3715 |
| *D* − *s**t**d* || \- || 1.2405 || 1.2599 || 1.1607 || 1.2085 || 1.0924 |
|  |
| *I* − *m**e**a**n* || 53.2158 || 43.1694 || 50.1471 || 44.7717 || 48.9104 || 46.3077 |
| *I* − *s**t**d* || \- || 2.3760 || 2.3276 || 2.2961 || 2.2025 || 2.1959 |
|  |

 

[Table 11.18:](#chapter11.xhtml#t11_18b) Forecasted evolution of thermokarst lakes area up to year 2017.

 
|  |
| --- |
| Year || 2013 || 2014 || 2015 || 2016 || 2017 |
|  |
| --- |
| *C* − *m**e**a**n* || 20.0226 || 19.9603 || 19.9349 || 19.8134 || 19.7374 |
| *C* − *s**t**d* || 0.6205 || 0.6542 || 0.6878 || 0.6878 || 0.6713 |
|  |
| *D* − *m**e**a**n* || 19.922 || 19.5528 || 19.8171 || 19.6082 || 19.7359 |
| *D* − *s**t**d* || 1.1424 || 1.0787 || 1.1133 || 1.0887 || 1.1053 |
|  |
| *I* − *m**e**a**n* || 48.6890 || 47.3009 || 48.2036 || 47.4963 || 47.8111 |
| *I* − *s**t**d* || 2.0383 || 2.0673 || 2.0253 || 2.0554 || 2.0402 |
|  |

 

[Table 11.19:](#chapter11.xhtml#t11_19b) Forecasted evolution of thermokarst lakes area up to year 2022.

 
|  |
| --- |
| Year || 2018 || 2019 || 2020 || 2021 || 2022 |
|  |
| --- |
| *C* − *m**e**a**n* || 19.6453 || 19.5491 || 19.4576 || 19.3742 || 19.3070 |
| *C* − *s**t**d* || 0.6367 || 0.5969 || 0.5569 || 0.5215 || 0.4901 |
|  |
| *D* − *m**e**a**n* || 19.6215 || 19.6897 || 19.6372 || 19.6780 || 19.6546 |
| *D* − *s**t**d* || 1.0913 || 1.0979 || 1.0885 || 1.0911 || 1.0867 |
|  |
| *I* − *m**e**a**n* || 47.5081 || 47.6778 || 47.6040 || 47.6912 || 47.6729 |
| *I* − *s**t**d* || 2.0584 || 2.0421 || 2.0484 || 2.0405 || 2.0443 |
|  |

[Figure 11.18](#chapter11.xhtml#f11_18) demonstrates the ensembles of forecasts for zones *C, D* and *I*. Here the trajectories of the mean values and standart deviation area are indicated by (*mean*) and (*std*), respectively.

![Figure 11.18: Forecast for 15 years.](images/fig11_18.jpg)

[Figure 11.18:](#chapter11.xhtml#f11_18b) Forecast for 15 years.

The evolution of the lakes area forecasted in this paper is characterized by mean values ([Table 11.17](#chapter11.xhtml#t11_17), [Table 11.18](#chapter11.xhtml#t11_18), [Table 11.19](#chapter11.xhtml#t11_19)) and standard deviations from 2 to 4.5%. Also, the graphs for zones *D* and *I* ([Fig. 11.17](#chapter11.xhtml#f11_17)) have an oscillatory process, reaching a constant level after year 2018.

# APPENDIX A MAXIMUM ENTROPY ESTIMATE (MEE) AND ITS ASYMPTOTIC EFFICIENCY

DOI: [10.1201/9781003306566-A](https://doi.org/10.1201/9781003306566-A)

## A.1Statement of Maximum Entropy Estimation Problem

Consider a scalar continuous function *φ*(*x*, *θ*) with parameters *θ* = {*θ*[1],…,*θ*[*n*]}. Assume that this function is a characteristic of an object's model with an input *x* and an output *y*. Let **x**^((*r*)) = {*x*\[1\],…,*x*\[*r*\]} and **y**^((*r*)) = {*y*\[1\],…,*y*\[*r*\]} be given measurements. Note that the latter are obtained with random errors *ξ* = {*ξ*\[1\],…,*ξ*\[*r*\]}, in the general case, different for different time instants.

Thus, after *r* measurements the model and observations are described by the equations

  
$$\\begin{aligned} \\hat{\\mathbf{y}} & {= \\Gamma(\\mathbf{x}^{(r)},\\theta),} \\\\ \\hat{\\mathbf{v}} & {= \\hat{\\mathbf{y}} + \\xi,} \\\\ \\end{aligned}$$  
(A.1)

where the vector function *Γ*(**x**^((*r*)), *θ*) has the components $\\varphi(x\\lbrack t\\rbrack,\\theta),\\, t = \\overline{1,r};$ $\\hat{\\mathbf{v}}$ denotes the observed output of the model containing measurement noises of the object's output.

The estimation problem is stated as follows: *find the maximum entropy estimates of the PDFs *P*^(\*)(*θ*) and *Q*^(\*)(*ξ*) that maximize the generalized information entropy functional*

  
$$\\begin{aligned} & {\\mathcal{H}\\lbrack P(\\theta),Q(\\xi)\\rbrack = - {\\int\_{Q}P}(\\theta)\\ln P(\\theta)d\\theta -} \\\\ & \\left. \\quad - {\\sum\\limits\_{t = 1}^{r}{\\int\_{\\Xi\_{t}}Q\_{t}}}(\\xi\\lbrack t\\rbrack)\\ln Q\_{t}(\\xi\\lbrack t\\rbrack)\\Rightarrow\\max \\right. \\\\ \\end{aligned}$$  
(A.5)

*subject to*

*   *—the normalization conditions of the PDFs given by*
    
      
    $$\\begin{array}{r} {{\\int\_{\\Theta}P}(\\theta)d\\theta = 1;\\quad{\\int\_{\\Xi\_{t}}Q\_{t}}(\\xi\\lbrack t\\rbrack)d\\xi\\lbrack t\\rbrack = 1,\\, t = \\overline{1,r}.} \\\\ \\end{array}$$  
    (A.6)
    
    and
    
*   *—the empirical balance conditions*
    
      
    $$\\begin{aligned} & {\\Phi\\lbrack P(\\theta),Q(\\xi)\\rbrack = \\mathbf{y}^{(r)},} \\\\ {\\Phi\\lbrack P(\\theta),Q(\\xi)\\rbrack =} & \\left\\{ \\Phi\_{1}\\lbrack P(\\theta),Q(\\xi)\\rbrack,\\ldots,\\Phi\_{r}\\lbrack P(\\theta),Q(\\xi)\\rbrack \\right\\} \\\\ {\\Phi\_{t}\\lbrack P(\\theta),Q(\\xi)\\rbrack = \\int\_{\\Theta}} & {\\varphi(x\\lbrack t\\rbrack,\\theta)P(\\theta)d\\theta + \\int\_{\\Xi\_{t}}Q\_{t}(\\xi\\lbrack t\\rbrack)\\xi\\lbrack t\\rbrack d\\xi\\lbrack t\\rbrack,} \\\\ & {\\text{\\quad\\quad}\\quad t = \\overline{1,r}.} \\\\ \\end{aligned}$$  
    (A.7)
    

The optimization problem (A.1–A.1) is of the Lyapunov type \[77, 174\]: such problems have an integral functional and also integral constraints. Hence, the entropy-optimal PDFs of the model parameters and measurement noises have the form

  
$$\\begin{aligned} \\left. P^{\*}(\\theta\\, \\middle| \\,\\mathbf{y}^{(r)}\\,\\mathbf{x}^{(r)}) \\right. & {= \\frac{\\exp\\left( {- {\\sum\\limits\_{j = 1}^{r}\\lambda\_{j}}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\varphi(x\\lbrack j\\rbrack,\\theta)} \\right)}{\\mathcal{P}(\\lambda(\\mathbf{y}^{(r)}),\\mathbf{x}^{(r)})},} \\\\ \\left. Q\_{t}^{\*}(\\xi\\lbrack t\\rbrack\\, \\middle| \\,\\mathbf{y}^{(r)}\\,\\mathbf{x}^{(r)}) \\right. & {= \\frac{\\exp\\left( {\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\xi\\lbrack t\\rbrack} \\right)}{\\mathcal{Q}\_{t}(\\lambda\_{t}(\\mathbf{y}^{(r)}),\\mathbf{x}^{(r)})},\\quad t = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(A.8)

where

  
$$\\begin{aligned} {\\mathcal{P}(\\lambda(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}) = \\int\_{\\Theta}} & {\\exp\\left( {- \\sum\_{j = 1}^{r}\\lambda\_{j}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\varphi(x\\lbrack j\\rbrack,\\theta)} \\right)d\\theta,} \\\\ {\\mathcal{Q}\_{t}(\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})} & {= \\int\_{\\Xi\_{t}}\\exp\\left( {\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\xi\\lbrack t\\rbrack} \\right)d\\xi\\lbrack t\\rbrack,} \\\\ & {\\quad t = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(A.9)

Due to equalities (A.1) and (A.1), the entropy-optimal PDFs are parameterized by the Lagrange multipliers *λ*[1], …, *λ*[*r*], which represent the solutions of the empirical balance equations

  
$$\\begin{array}{r} {\\frac{\\mathcal{G}(\\lambda(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}))}{\\mathcal{P}(\\lambda(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}))} + \\frac{\\mathcal{E}\_{t}(\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}))}{\\mathcal{Q}\_{t}\\left( {\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})} \\right)} = y\\lbrack t\\rbrack,\\quad t = \\overline{1,r},} \\\\ \\end{array}$$  
(A.10)

where

  
$$\\begin{aligned} {\\mathcal{G}(\\lambda(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})) = \\int\_{\\Theta}} & {\\varphi(x\\lbrack t\\rbrack,\\theta)\\exp\\left( {- \\sum\_{j = 1}^{r}\\lambda\_{j}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\varphi(x\\lbrack j\\rbrack,\\theta)} \\right)d\\theta,} \\\\ {\\mathcal{E}\_{t}(\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}))} & {= \\int\_{\\Xi\_{t}}\\exp\\left( {- \\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\xi\\lbrack t\\rbrack} \\right)d\\xi\\lbrack t\\rbrack,} \\\\ & {\\quad t = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(A.11)

The solution *λ*^(\*)(**y**^((*r*))), **x**^((*r*))) of these equations depends on the sample (**y**^((*r*))), **x**^((*r*)) used for constructing the maximum entropy estimates of the PDFs.

## A.2Existence of Implicit Function $\\theta({\\widetilde{\\mathbf{y}}}^{(r)},\\mathbf{x}^{(r)})$

According to the balance equations (A.10), (A.1), their second term is the mean value of the noise in each measurement *t*. The noises and also their characteristics are often assumed to be independent of the measurements, i.e., in the expression (A.3),

  
$$\\begin{array}{r} {\\Xi\_{t} = \\Xi = \\lbrack\\xi^{-},\\xi^{+}\\rbrack.} \\\\ \\end{array}$$  
(A.12)

Therefore, the mean value of the noise is given by

  
$$\\begin{array}{r} {\\overline{\\xi} = \\frac{\\mathcal{E}\_{t}(\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}))}{\\mathcal{Q}\_{t}\\left( {\\lambda\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})} \\right)} \\in \\Xi.} \\\\ \\end{array}$$  
(A.13)

The balance equations can be written as

  
$$\\begin{aligned} & \\left. \\quad W\_{t}(\\lambda\\, \\middle| \\,\\widetilde{y}\\lbrack t\\rbrack,\\mathbf{x}^{(r)}) = {\\int\_{\\Theta}\\left( {\\varphi(x\\lbrack t\\rbrack,\\theta) - \\widetilde{y}\\lbrack t\\rbrack} \\right)} \\times \\right. \\\\ & {\\times \\exp\\left( {- {\\sum\\limits\_{j = 1}^{r}\\lambda\_{j}}({\\widetilde{\\mathbf{y}}}^{(r)},\\mathbf{x}^{(r)})\\varphi(x\\lbrack j\\rbrack,\\theta)} \\right)d\\theta = 0,} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}t = \\overline{1,r},} \\\\ \\end{aligned}$$  
(A.14)

where

  
$$\\begin{array}{r} {\\widetilde{y}\\lbrack t\\rbrack = y\\lbrack t\\rbrack - \\overline{\\xi},\\text{\\quad\\quad}{\\widetilde{\\mathbf{y}}}^{(r)} = \\left\\{ \\widetilde{y}\\lbrack 1\\rbrack,\\ldots,\\widetilde{y}\\lbrack r\\rbrack \\right\\}.} \\\\ \\end{array}$$  
(A.15)

In the vector form, equations (A.2) are described by

  
$$\\begin{array}{r} \\left. \\mathbf{W}(\\lambda\\, \\middle| \\,{\\widetilde{\\mathbf{y}}}^{(r)},\\mathbf{x}^{(r)}) = \\mathbf{0}. \\right. \\\\ \\end{array}$$  
(A.16)

Equation (A.16) defines an implicit function $\\lambda({\\widetilde{\\mathbf{y}}}^{(r)},\\mathbf{x}^{(r)}).$ The existence and properties of this implicit function depend on the properties of the Jacobian matrix

  
$$\\begin{array}{r} \\left. J\_{\\lambda}(\\lambda\\, \\middle| \\,\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}) = \\left\\lbrack \\frac{\\partial W\_{t}}{\\partial\\lambda\_{i}},\\, \\middle| \\,(t,i) = \\overline{1,r} \\right\\rbrack, \\right. \\\\ \\end{array}$$  
(A.17)

which has the elements

  
$$\\begin{aligned} & {\\frac{\\partial W\_{t}}{\\partial\\lambda\_{i}} = {\\int\_{Q}\\left( {\\varphi(x\\lbrack t\\rbrack,\\theta) - \\widetilde{y}\\lbrack t\\rbrack} \\right)}\\varphi(x\\lbrack i\\rbrack,\\theta) \\times} \\\\ & {\\quad \\times {\\sum\\limits\_{j = 1}^{r}\\exp}\\left( {- {\\sum\\limits\_{j = 1}^{r}\\lambda\_{j}}\\varphi(x\\lbrack j\\rbrack,\\theta)} \\right)d\\theta.} \\\\ \\end{aligned}$$  
(A.18)

## A.3Asymptotic efficiency of maximum entropy estimates

MEE yields the entropy-optimal PDFs (A.1) for the arrays of input and output data, each of size *r*. For the sake of convenience, consider the PDFs parameterized by the exponential Lagrange multipliers *z* = exp ( − *λ*). Then equalities (A.1) take the form

  
$$\\begin{aligned} {P^{\*}\\left( {\\theta,\\,\\mathbf{z}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})} \\right)} & {= \\frac{\\prod\_{j = 1}^{r}{\\lbrack z\_{j}(\\mathbf{y}^{(r)},\\mathbf{x}^{r})\\rbrack}^{\\varphi(x\\lbrack j\\rbrack,\\theta)}}{\\int\_{\\Theta}\\prod\_{j = 1}^{r}{\\lbrack z\_{j}(\\mathbf{y}^{(r)},\\mathbf{x}^{r})\\rbrack}^{\\varphi(x\\lbrack j\\rbrack,\\theta)}d\\theta},} \\\\ {Q\_{t}^{\*}(\\xi\\lbrack t\\rbrack,\\, z\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)}))} & {= \\frac{{\\lbrack z\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\rbrack}^{\\xi\\lbrack t\\rbrack}}{\\int\_{\\Xi\_{t}}{\\lbrack z\_{t}(\\mathbf{y}^{(r)},\\mathbf{x}^{(r)})\\rbrack}^{\\xi\\lbrack t\\rbrack}d\\xi\\lbrack t\\rbrack},} \\\\ \\end{aligned}$$  
(A.21)

  
$$\\begin{aligned} & {\\quad t = \\overline{1,r}.} \\\\ \\end{aligned}$$  
(A.22)

Consequently, the structure of the PDF significantly depends on the values of the exponential Lagrange multipliers **z**, which in turn depend on the data arrays **y**^((*r*)) and **x**^((*r*)).

Lemma 1 can be applied to the norm $\\|\\left\\lbrack \\frac{\\partial\\Phi}{\\partial\\mathbf{z}} \\right\\rbrack^{- 1}\\|$ of the inverse matrix. As a result,

  
$$\\begin{array}{r} {\\left( {\\|\\frac{\\partial\\Phi}{\\partial\\mathbf{z}}\\|} \\right)^{- 1} \\leq \\|\\left\\lbrack \\frac{\\partial\\Phi}{\\partial\\mathbf{z}} \\right\\rbrack^{- 1}\\| \\leq \\alpha\\left( {\\|\\frac{\\partial\\Phi}{\\partial\\mathbf{z}}\\|} \\right)^{- 1}.} \\\\ \\end{array}$$  
(A.31)

where

  
$$\\begin{array}{r} \\left. \\|\\frac{\\partial\\Phi}{\\partial\\mathbf{z}}\\| = r\\max\_{t,j} \\middle| \\frac{\\partial\\Phi\_{t}}{\\partial z\_{j}} \\middle| . \\right. \\\\ \\end{array}$$  
(A.32)

# APPENDIX B APPROXIMATE ESTIMATION OF STRUCTURAL CHARACTERISTICS OF LINEAR DYNAMIC REGRESSION MODEL (LDR)

DOI: [10.1201/9781003306566-B](https://doi.org/10.1201/9781003306566-B)

Consider a linear dynamic regression model (LDR) of the form

  
$$\\begin{array}{r} {\\hat{x}\\lbrack n\\rbrack = a\_{0} + {\\sum\\limits\_{k = 1}^{p}a\_{k}}\\,\\hat{x}\\lbrack n - k\\rbrack + a\_{p + 1}f\\lbrack n\\rbrack + \\varepsilon\\lbrack n\\rbrack,\\quad n = \\overline{p,N},} \\\\ \\end{array}$$  
(B.1)

where *x̂*\[*n*\] and *f\[n\]* denote the model's output and input, respectively; *p* is the order of this model; *ε*\[*n*\] gives a measurement noise; finally, $a\_{k},k = \\overline{0,p+1},$ are some model parameters.

Let

  
$$\\begin{array}{r} {f\\lbrack 0\\rbrack,f\\lbrack 1\\rbrack,\\ldots,f\\lbrack N\\rbrack,\\text{\\quad\\quad}x\\lbrack 0\\rbrack,x\\lbrack 1\\rbrack,\\ldots,x\\lbrack N\\rbrack} \\\\ \\end{array}$$  
(B.2)

be some available data on the input *f\[n\]* and output *x\[n\]* of the object under study.

Using these data and equations (B.1), we write the following regression equation in the vector-matrix form:

  
$$\\begin{array}{r} {\\mathbf{x} = X\_{(p + 2)}\\mathbf{a} + \\varepsilon,} \\\\ \\end{array}$$  
(B.3)

where:

*   the vectors **x** = {*x*\[*p*\],…,*x*\[*N*\]}, **a** = {*a*[0],…,*a*[(*p* + 1)]}, and *ε* = {*ε*\[*p*\],…,*ε*\[*N*\]};
    
*   the matrix
    
      
    $$\\begin{array}{r} {X\_{(p + 2)} = \\left( \\begin{array}{llllll} 1 & {x\\lbrack p - 1\\rbrack} & {x\\lbrack p - 2\\rbrack} & \\cdots & {x\\lbrack 0\\rbrack} & {f\\lbrack p\\rbrack} \\\\ 1 & {x\\lbrack p\\rbrack} & {x\\lbrack p - 1\\rbrack} & \\cdots & {x\\lbrack 1\\rbrack} & {f\\lbrack p + 1\\rbrack} \\\\ \\cdots & \\cdots & \\cdots & \\cdots & \\cdots & \\cdots \\\\ 1 & {x\\lbrack N - 1\\rbrack} & {x\\lbrack N - 2\\rbrack} & \\cdots & {x\\lbrack N - p\\rbrack} & {f\\lbrack N\\rbrack} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    (B.4)
    

The vector **x** and matrix *X*[(*p* + 2)] consist of the data (B.2).

## B.1ORDER *p*

The order *p* of this model is chosen by calculating the autocorrelation function *r*(*k*) for the variable *x* based on the data (B.2):

  
$$\\begin{aligned} {r(k)} & {= \\frac{c\_{k}}{\\sigma^{2}},\\quad c\_{k} = \\frac{1}{N + 1}{\\sum\\limits\_{n = 0}^{N + 1 - k}\\left( {x\\lbrack n\\rbrack - \\overline{x}} \\right)}\\left( {x\\lbrack n + k\\rbrack - \\overline{x}} \\right),} \\\\ \\sigma^{2} & {= \\frac{1}{N}{\\sum\\limits\_{n = 0}^{N}x^{2}}\\lbrack n\\rbrack.} \\\\ \\end{aligned}$$  
(B.5)

The order *p* is the maximum value *k* for which *r*(*k*) > *δ* = 0.1.

## B.2PARAMETERS RANGES

The approximate intervals for the PDFs of the LDR parameters are found by calculating the LS estimates and sample variance of the residual deviations. The LS estimates for (B.3) have the form

  
$$\\begin{array}{r} {\\hat{\\mathbf{a}} = \\left( {X\_{(p + 2)}^{\\intercal}X\_{(p + 2)}} \\right)^{- 1}X^{\\intercal}\\mathbf{x}.} \\\\ \\end{array}$$  
(B.6)

The residual deviations are described by the vector

  
$$\\begin{array}{r} {\\mathbf{e}\_{ls} = \\mathbf{x} - X\_{(p + 2)}\\hat{\\mathbf{a}},} \\\\ \\end{array}$$  
(B.7)

and the sample variance of the residual deviations is given by

  
$$\\begin{array}{r} {\\sigma^{2} = \\frac{1}{N - p}{\\sum\\limits\_{n = p}^{N}e^{2}}\\lbrack n\\rbrack.} \\\\ \\end{array}$$  
(B.8)

The standard deviations for the model parameters are

  
$$\\begin{array}{r} {s\_{a\_{k}} = \\sqrt{\\sigma^{2}Q\_{kk}},\\quad k = \\overline{0,p+1},} \\\\ \\end{array}$$  
(B.9)

where *Q*[*k**k*] denote the diagonal elements of the covariance matrix *Q* = (*X*[(*p* + 2)]^⊺*X*[(*p* + 2)])^( − 1).

In view of the asymptotic normality of the LS estimates, the parameters ranges are selected by the rule

  
$$\\begin{array}{r} {\\left\\{ a\_{k}^{-},a\_{k}^{+} \\right\\} = \\left\\{ {a\_{k} - 3s\_{a\_{k}},a\_{k} + 3s\_{a\_{k}}} \\right\\},\\quad k = \\overline{0,p+1}.} \\\\ \\end{array}$$  
(B.10)

# Bibliography

*   [\[1\]](#chapter11.xhtml#r1b) Dataset.
*   [\[2\]](#chapter3.xhtml#r2b) KEEL Dataset repository. [https:/​/​sci2s.ugr.es/​keel/​datasets.php](https://sci2s.ugr.es). Accessed: 2019-07-03.
*   [\[3\]](#chapter9.xhtml#r3b) ISO/IEC 2382:2015 information technology—vocabulary., 2015. URL: [https:/​/​www.iso.org/​obp/​ui/​#iso:std:iso-iec:2382:ed-1:v1:en](https://www.iso.org) (Accessed April 6, 2017).
*   [\[4\]](#chapter7.xhtml#r4b) Test functions for optimization, 2015. (Accessed November 2, 2015).
*   [\[5\]](#chapter7.xhtml#r5b) Virtual library of simulation experiments: Test functions and datasets, 2015. (Accessed November 2, 2015).
*   [\[6\]](#chapter9.xhtml#r6b) About CUDA, 2017. URL: [https:/​/​developer.nvidia.com/​about-cuda](https://developer.nvidia.com) (Accessed April 6, 2017).
*   [\[7\]](#chapter9.xhtml#r7b) Intel many integrated core architecture, 2017. URL: [http:/​/​www.intel.com/​content/​www/​us/​en/​architecture-and-technology/​many-integrated-core/​intel-many-integrated-core-archit-ecture.html](http://www.intel.com) (Accessed April 6, 2017).
*   [\[8\]](#chapter3.xhtml#r8b) D. Achlioptas. Database-friendly random projections. In PODS'01, pages 274–281. Amer. Math. Soc., 2001.
*   [\[9\]](#chapter3.xhtml#r9b) N. Ailon and B. Chazelle. Approximate nearest neighbors and the fast johnson–lindenstrauss transform. In *Proceedings of the 38th Annual ACM Symposium on Theory of Computing*, pages 557–563, 2006.
*   [\[10\]](#chapter3.xhtml#r10b) S. A. Aivazyan and V. S. Mkhitaryan. Applied statistics. Classification and dimension reduction. Finansy i Statistika, Moscow, 1989.
*   [\[11\]](#chapter1.xhtml#r11b) S. A. Aivazyan and V. S. Mkhitaryan. Applied statistics and foundations of econometrics. Yuniti, 1998.
*   [\[12\]](#preface.xhtml#r12b) M. A. Aizerman, E. M. Braverman, and L. I. Rozonoer. The method of potential functions in the theory of machine learning. Nauka, Moscow, 1970.
*   [\[13\]](#chapter11.xhtml#r13b) L. F. Amaral, R. C. Souza, and M. Stevenson. A smooth transition periodic autoregressive (stpar) model for short-term load forecasting. International Journal of Forecasting, 24(4):603–615, 2008.
*   [\[14\]](#chapter10.xhtml#r14b) A. G. Arkadiev and E. M. Braverman. Image recognition and machine learning. Nauka, Moscow, 1964.
*   [\[15\]](#chapter4.xhtml#r15b) M. Avellaneda. Minimum-relative-entropy calibration of asset-pricing models. International Journal of Theoretical and Applied Finance, 1(04):447–472, 1998.
*   [\[16\]](#chapter1.xhtml#r16b) A. N. Averkin, M. G. Gaaze-Rapoport, and D. A. Pospelov. Defining dictionary on artificial intelligence. Radio i Svyaz, 1992.
*   [\[17\]](#chapter2.xhtml#r17b) N. S. Bakhvalov, N. P. Zhidkov, and G. M. Kobel'kov. Numerical methods. BINOM, 2003.
*   [\[18\]](#chapter1.xhtml#r18b) A. S. Bernstein, I. V. Pyshkin, Yu. S. Popkov, and R. G. Faradzhev. Analytic description of binary nonlinear sequential machines. Automation and Remote Control, 32(12):1920–1927, 1971.
*   [\[19\]](#chapter10.xhtml#r19b) K. Beyer, J. Goldstein, R. Ramakrishnan, and U. Shaft. When is “nearest neighbor” meaningful? In *International conference on database theory*, pages 217–235. Springer, 1999.
*   [\[20\]](#chapter3.xhtml#r20b) E. Bingham and H. Mannila. Random projection in dimensionality reduction: applications to image and text data. In *Proceedings of the 7th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*, pages 245–250. ACM, 2001.
*   [\[21\]](#chapter3.xhtml#r21b) C. Bishop. *Pattern recognition and machine learning (Information Science and Statistics)*, *1st* *ed*. 2006\. corr. 2nd ed. Springer, New York, 2007.
*   [\[22\]](#chapter10.xhtml#r22b) L. Breiman. Bagging predictors. Machine Learning, 24(2):123–140, 1996.
*   [\[23\]](#chapter10.xhtml#r23b) L. Breiman, J. H. Friedman, R. A. Olshen, and C. J. Stone. Classification and regression trees. *1993*. Chapman Hall, New York, 1984.
*   [\[24\]](#chapter11.xhtml#r24b) NA Bryksina and Yu M Polishchuk. Analysis of changes in the number of thermokarst lakes in permafrost of western siberia on the basis of satellite images. Earth Cryosphere, 19:100–105, 2015.
*   [\[25\]](#chapter10.xhtml#r25b) P. Bühlmann and T. Hothorn. Boosting algorithms: Regularization, prediction and model fitting. Statistical Science, pages 477–505, 2007.
*   [\[26\]](#chapter3.xhtml#r26b) L. Buitinck, G. Louppe, M. Blondel, F. Pedregosa, A. Mueller, O. Grisel, V. Niculae, P. Prettenhofer, A. Gramfort, R. Grobler, J. Layton, J. VanderPlas, A. Joly, B. Holt, and G. Varoquaux. API design for machine learning software: experiences from the scikit-learn project. In ECML PKDD Workshop: Languages for Data Mining and Machine Learning, pages 108–122, 2013.
*   [\[27\]](#chapter3.xhtml#r27b) R. Calderbank, S. Jafarpour, and R. Schapire. Compressed learning: Universal sparse dimensionality reduction and learning in the measurement domain. Technical report, 2009.
*   [\[28\]](#preface.xhtml#r28b) P. Campbell. Editorial on special issue on big data: Community cleverness required. Nature, 455(7209):1, 2008.
*   [\[29\]](#chapter3.xhtml#r29b) E. J. Candes and T. Tao. Near-optimal signal recovery from random projections: Universal encoding strategies? IEEE Transactions on Information Theory, 52(12):5406–5425, 2006.
*   [\[30\]](#chapter3.xhtml#r30b) M. S. Charikar. Similarity estimation techniques from rounding algorithms. In *Proceedings of the 34th Annual ACM Symposium on Theory of Computing*, pages 380–388, 2002.
*   [\[31\]](#chapter8.xhtml#r31b) S. Chib and E. Greenberg. Understanding the metropolis–hastings algorithm. The American Statistician, 49(4):327–335, 1995.
*   [\[32\]](#chapter8.xhtml#r32b) S. Chib and I. Jeliazkov. Marginal likelihood from the metropolis–hastings output. Journal of the American Statistical Association, 96(453):270–281, 2001.
*   [\[33\]](#chapter10.xhtml#r33b) T. Cover and P. Hart. Nearest neighbor pattern classification. IEEE Transactions on Information Theory, 13(1):21–27, 1967.
*   [\[34\]](#chapter1.xhtml#r34b) H. Cramer. Mathematical methods of statistics. Princeton University Press, 1962.
*   [\[35\]](#chapter7.xhtml#r35b) B. S. Darkhovskii, A. Yu. Popkov, and Yu. S. Popkov. Monte carlo method of batch iterations: Probabilistic characteristics. Automation and Remote Control, 76(5):776–785, 2015.
*   [\[36\]](#chapter2.xhtml#r36b) B. S. Darkhovsky, Yu. S. Popkov, A. Yu. Popkov, and A. S. Aliev. Method of generating random vectors with a given probability density function. Automation and Remote Control, 79(9):1569–1581, 2018.
*   [\[37\]](#chapter10.xhtml#r37b) B. V. Dasarathy. Nearest neighbor ({NN}) norms:{NN} pattern classification techniques. 1991.
*   [\[38\]](#chapter3.xhtml#r38b) A. Dasgupta, R. Kumar, and T. Sarlos. A sparse johnson–lindenstrauss transform. In *Proceedings of the 42nd ACM Symposium on Theory of Computing*, pages 341–350, 2010.
*   [\[39\]](#chapter9.xhtml#r39b) W. Davis and D. Yen. The information system consultant's handbook. Systems analysis and design. CRC Press, 1998.
*   [\[40\]](#chapter1.xhtml#r40b) J. De Beer and L. van Wissen. Europe: one continent, different worlds. population scenarios for the 21st century. Technical report, ISBN 0-7923-5840-6, 1999.
*   [\[41\]](#chapter1.xhtml#r41b) A. P. Dempster, N. M. Laird, and D. B. Rubin. Maximum likelihood from incomplete data via the em algorithm. Journal of the Royal Statistical Society. Series B (Methodological), pages 1–38, 1977.
*   [\[42\]](#chapter4.xhtml#r42b) V. A. Ditkin and A. P. Prudnikov. Operational calculus in two variables. Fizmatgiz, Moscow, 1953.
*   [\[43\]](#chapter4.xhtml#r43b) V. A. Ditkin and A. P. Prudnikov. Integral transformations and operational calculus. Fizmatgiz, Moscow, 1961.
*   [\[44\]](#chapter10.xhtml#r44b) P. Domingos and M. Pazzani. On the optimality of the simple bayesian classifier under zero-one loss. Machine Learning, 29(2):103–130, 1997.
*   [\[45\]](#chapter9.xhtml#r45b) J. J. Dongarra. Sourcebook of parallel computing. Morgan Kaufmann Publishers, San Francisco, 2003.
*   [\[46\]](#chapter3.xhtml#r46b) D. L. Donoho. Compressed sensing. IEEE Transactions on Information Theory, 52(4):1289–1306, 2006.
*   [\[47\]](#chapter2.xhtml#r47b) E. B. Dynkin. Theory of Markov processes. Prentice-Hall, 1961.
*   [\[48\]](#chapter2.xhtml#r48b) W. Feller. An introduction to probability theory and its applications. Vol. 2. John Wiley & Sons, 2nd ed. edition, 1971.
*   [\[49\]](#chapter11.xhtml#r49b) G. Fiedner. Hierarchical forecasting: Issues and use guidelines. Industrial Management and Data Systems, 101(1):5–12, 2001.
*   [\[50\]](#chapter1.xhtml#r50b) A. F. Filippov. Introduction to theory of differential equations. URSS, 2010.
*   [\[51\]](#chapter1.xhtml#r51b) R. A. Fisher. Two new properties of mathematical likelihood. *Proceedings of the Royal Society of London. Series A*, Containing Papers of a Mathematical and Physical Character, 144(852):285–307, 1934.
*   [\[52\]](#chapter10.xhtml#r52b) R. A. Fisher. The use of multiple measurements in taxonomic problems. Annals of Human Genetics, 7(2):179–188, 1936.
*   [\[53\]](#chapter1.xhtml#r53b) P. Flach. Machine learning: the art and science of algorithms that make sense of data. Cambridge University Press, 2012.
*   [\[54\]](#chapter1.xhtml#r54b) J. W. Forrester et al. World dynamics. Waltham, MA, 2nd ed. edition, 1973.
*   [\[55\]](#preface.xhtml#r55b) W. J. Frawley, G. Piatetsky-Shapiro, and C. J. Matheus. Knowledge discovery in databases: An overview. AI magazine, 13(3):57, 1992.
*   [\[56\]](#chapter10.xhtml#r56b) Y. Freund, R. Schapire, and N. Abe. A short introduction to boosting. Journal of Japanese Society For Artificial Intelligence, 14(771-780):1612, 1999.
*   [\[57\]](#chapter3.xhtml#r57b) J. Friedman, T. Hastie, and R. Tibshirani. The elements of statistical learning: Springer Series in Statistics, volume 1. Springer series in statistics Springer, Berlin, 2001.
*   [\[58\]](#chapter7.xhtml#r58b) M. C. Fu, J. Hu, and S. I. Marcus. Model-based randomized methods for global optimization. In *Proceedings of the 17th international symposium on mathematical theory of networks and systems*, pages 355–363, 2006.
*   [\[59\]](#chapter9.xhtml#r59b) E. Gamma, R. Helm, R. Johnson, and J. Vlissides. Design patterns: Elements of reusable object-oriented software. Addison-Wesley, USA, 1994.
*   [\[60\]](#chapter3.xhtml#r60b) F. R. Gantmakher. Matrix theory, 1966.
*   [\[61\]](#chapter7.xhtml#r61b) I. M. Gelfand, R. A. Silverman, et al. Calculus of variations. Courier Corporation, 2000.
*   [\[62\]](#chapter9.xhtml#r62b) V. P. Gergel and R. G. Strongin. Foundations of parallel computing for multiprocessor computer systems. Lobachevsky State University press, Nizhny Novgorod, 2003.
*   [\[63\]](#chapter10.xhtml#r63b) W. Gerstner and W. Kistler. Spiking neuron models, 2002.
*   [\[64\]](#chapter2.xhtml#r64b) J. Geweke and H. Tanizaki. Note on the sampling distribution for the metropolis–hastings algorithm. Communications in Statistics—Theory and Methods, 32(4):775–789, 2003.
*   [\[65\]](#chapter2.xhtml#r65b) I. I. Gikhman and A. V. Skorokhod. Introduction to theory of random processes. Nauka, 1977.
*   [\[66\]](#chapter1.xhtml#r66b) A. Golan et al. Information and entropy econometrics—a review and synthesis. Foundations and Trends® in Econometrics, 2(1–2):1–145, 2008.
*   [\[67\]](#chapter6.xhtml#r67b) A. Golan, G. Judge, and D. Miller. Maximum entropy econometrics: robust estimation with limited data. John Wiley & Sons, New York, 1996.
*   [\[68\]](#chapter1.xhtml#r68b) A. V. Gorokhov and V. A. Putilov. System dynamics of regional development. Pazori, 2002.
*   [\[69\]](#chapter9.xhtml#r69b) A. Grama, A. Gupta, and G. Karypis. Introduction to parallel computing. Addison-Wesley, Harlow, England, 2nd ed. edition, 2003.
*   [\[70\]](#chapter3.xhtml#r70b) T. Hastie, R. Tibshirani, and J. Friedman. The Elements of statistical learning: data mining, inference, and prediction. Springer New York, 2009.
*   [\[71\]](#chapter11.xhtml#r71b) T. Hong, P. Pinson, S. Fan, H. Zareipour, A. Troccoli, and R. J. Hyndman. Probabilistic energy forecasting: Global energy forecasting competition 2014 and beyond. International Journal of Forecasting, 32(3):896–913, 2016.
*   [\[72\]](#chapter1.xhtml#r72b) J. Hopcroft, R. Motwani, and J. Ullman. Introduction to automata theory, languages, and computation. Addison-Wesley, 3rd ed. edition, 2007.
*   [\[73\]](#chapter10.xhtml#r73b) David W. Hosmer J., S. Lemeshow, and R. X. Sturdivant. Applied logistic regression, volume 398. John Wiley & Sons, 2013.
*   [\[74\]](#chapter1.xhtml#r74b) P. J. Huber. Robust statistics. Springer, 2011.
*   [\[75\]](#chapter10.xhtml#r75b) L. Hyafil and R. L. Rivest. Constructing optimal binary decision trees is np-complete. Information Processing Letters, 5(1):15–17, 1976.
*   [\[76\]](#chapter3.xhtml#r76b) P. Indyk and R. Motwani. Approximate nearest neighbors: towards removing the curse of dimensionality. In *Proceedings of the 30th Annual ACM Symposium on Theory of Computing*, pages 604–613, 1998.
*   [\[77\]](#chapter2.xhtml#r77b) A. D. Ioffe and V. M. Tikhomirov. Theory of extremum problems. 1974.
*   [\[78\]](#chapter9.xhtml#r78b) I. Jacobson, G. Booch, and J. Rumbaugh. The unified software development process. Addison-Wesley Longman, USA, 1999.
*   [\[79\]](#chapter10.xhtml#r79b) A. K. Jain, R. P. W. Duin, and J. Mao. Statistical pattern recognition: A review. IEEE Transactions on Pattern Analysis and Machine Intelligence, 22(1):4–37, 2000.
*   [\[80\]](#chapter1.xhtml#r80b) E. T. Jaynes. Information theory and statistical mechanics. Physical Review, 106(4):620–630, 1957.
*   [\[81\]](#preface.xhtml#r81b) E. T. Jaynes. Probability theory: the logic of science. Cambridge University Press, 2003.
*   [\[82\]](#chapter3.xhtml#r82b) T. S. Jayram and D. P. Woodruff. Optimal bounds for johnson–lindenstrauss transforms and streaming problems with subconstant error. ACM Transactions on Algorithms (TALG), 9(3):1–17, 2013.
*   [\[83\]](#chapter3.xhtml#r83b) W. B. Johnson and J. Lindenstrauss. Extensions of lipshitz mapping into hilbert space. In Modern Analysis and Probability, volume 26, pages 189–206. Amer. Math. Soc., 1984.
*   [\[84\]](#chapter3.xhtml#r84b) I. T. Jolliffe. Principal component analysis and factor analysis. In Springer Series of Statistics. Springer, New York, 2002.
*   [\[85\]](#chapter4.xhtml#r85b) M. A. Kaashoek, S. Seatzu, and C. van der Mee. Recent advances in operator theory and its applications: The Israel Gohberg anniversary volume, volume 160. Springer Science & Business Media, 2006.
*   [\[86\]](#chapter3.xhtml#r86b) D. Kane, R. Meka, and J. Nelson. Almost optimal explicit johnson–lindenstrauss families. In Approximation, randomization, and combinatorial optimization. Algorithms and techniques, pages 628–639. Springer, 2011.
*   [\[87\]](#chapter3.xhtml#r87b) D. M. Kane and J. Nelson. Sparser johnson–lindenstrauss transforms. Journal of the ACM (JACM), 61(1):1–23, 2014.
*   [\[88\]](#chapter1.xhtml#r88b) J. N. Kapur. Maximum-entropy models in science and engineering. John Wiley & Sons, 1989.
*   [\[89\]](#chapter11.xhtml#r89b) Johanna Mård Karlsson, Steve W Lyon, and Georgia Destouni. Temporal behavior of lake size-distribution in a thawing permafrost landscape in northwestern siberia. Remote sensing, 6(1):621–636, 2014.
*   [\[90\]](#chapter1.xhtml#r90b) M. Kendall and A. Stuart. The advanced theory of statistics. Vol. 2: Inference and relationship. Griffin, London, 1977.
*   [\[91\]](#chapter1.xhtml#r91b) N. P. Kirillov. Conceptual models of technical systems with controllable states (a survey and analysis). Artificial Intelligence and Decision Making, 4:81–91, 2011.
*   [\[92\]](#chapter11.xhtml#r92b) S.N. Kirpotin, Yu Polishchuk, and N. Bryksina. Abrupt changes of thermokarst lakes in western siberia: impacts of climatic warming on permafrost melting. International Journal of Environmental Studies, 66(4):423–431, 2009.
*   [\[93\]](#chapter2.xhtml#r93b) M. V. Kiselev, V. S. Pivovarov, and M. M. Shmulevich. A text clustering method considering the co-occurrence of key terms, with application to the dynamical analysis of thematic structure of news flow. 2005.
*   [\[94\]](#chapter4.xhtml#r94b) A. N. Kolmogorov. On representation of continuous multivariable functions using superpositions of continuous multivariable functions of smaller dimension. 114(5):953–956, 1957.
*   [\[95\]](#chapter2.xhtml#r95b) A.N. Kolmogorov and S. V. Fomin. Elements of theory of functions and functional analysis, volume 1. Fizmatlit, Moscow, 1999.
*   [\[96\]](#chapter1.xhtml#r96b) L. G. Komartsova and A. V. Maksimov. Neurocomputers. Bauman Moscow State Technical University Press, 2004.
*   [\[97\]](#chapter3.xhtml#r97b) D. Kraft. A software package for sequential quadratic programming. Technical Report DFVLR-FB 88-28, DLR German Aerospace Center—Institute for Flight Mechanics, Koln, Germany, 1988.
*   [\[98\]](#chapter2.xhtml#r98b) S. G. Krantz. A handbook of real variables: with applications to differential equations and Fourier analysis. Springer Science & Business Media, 2011.
*   [\[99\]](#chapter9.xhtml#r99b) G. E. Krasner, S. T. Pope, et al. A description of the model-view-controller user interface paradigm in the smalltalk-80 system. Journal of Object Oriented Programming, 1(3):26–49, 1988.
*   [\[100\]](#chapter4.xhtml#r100b) M. A. Krasnoselskii, G. M. Vainikko, P. P. Zabreiko, Ya. B. Rutitskii, and V. Ya. Stetsenko. Approximate solution of operator equations. Nauka, Moscow, 1969.
*   [\[101\]](#appA.xhtml#r101b) M. A. Krasnosel'skii and P. P. Zabreiko. Geometrical methods of nonlinear analysis, volume 263. Springer, 1984.
*   [\[102\]](#chapter3.xhtml#r102b) S. Kullback and R. A. Leibler. On information and sufficiency. The Annals of Mathematical Statistics, 22(1):79–86, 1951.
*   [\[103\]](#chapter9.xhtml#r103b) S. D. Kuznetsov. Great Russian Encyclodepia, volume 11, chapter Information technology, page 493. 2008.
*   [\[104\]](#chapter4.xhtml#r104b) M. B. Lagutin. Visual mathematical statistics. 2013.
*   [\[105\]](#chapter10.xhtml#r105b) J. Langford. Tutorial on practical prediction theory for classification. Journal of Machine Learning Research, 6(Mar):273–306, 2005.
*   [\[106\]](#chapter1.xhtml#r106b) A. V. Lapko, S. V. Chentsov, S. I. Krokhov, and L. A. Fel'dman. Learning systems for data processing and decision making. Nauka, Novosibirsk, 1996.
*   [\[107\]](#chapter1.xhtml#r107b) M. V. Lawson. Finite automata. CRC Press, 2003.
*   [\[108\]](#chapter3.xhtml#r108b) M. Ledoux. *The concentration of measure phenomenon*. Number 89. American Mathematical Soc., 2001.
*   [\[109\]](#chapter1.xhtml#r109b) R. D. Levine and M. Tribus. Maximum entropy formalism. In Maximum Entropy Formalism Conference (1978: Massachusetts Institute of Technology). MIT Press, 1979.
*   [\[110\]](#chapter10.xhtml#r110b) A. V. Levitin. Algorithms: Introduction to design and analysis. Vil'yams, 2006.
*   [\[111\]](#chapter1.xhtml#r111b) P. Lévy. Specific problems of functional analysis. 1967.
*   [\[112\]](#chapter11.xhtml#r112b) Qianqian Liu, Mark D. Rowe, Eric J. Anderson, Craig A. Stow, Richard P. Stumpf, and Thomas H. Johengen. Probabilistic forecast of microcystin toxin using satellite remote sensing, in situ observations and numerical modeling. Environmental Modelling & Software, 128:104705, 2020.
*   [\[113\]](#chapter11.xhtml#r113b) Miska Luoto and Matti Seppala. Thermokarst ponds as indicators of the former distribution of palsas in finnish lapland. Permafrost and periglacial processes, 14(1):19–27, 2003.
*   [\[114\]](#chapter5.xhtml#r114b) L. A. Lusternik and V. I. Sobolev. Elements of functional analysis. 1965.
*   [\[115\]](#chapter3.xhtml#r115b) J. R. Magnus and H. Neudecker. Matrix differential calculus with applications in statistics and econometrics. *Wiley series in probability and mathematical statistics*, 1988.
*   [\[116\]](#chapter3.xhtml#r116b) O. Maillard and R. Munos. Compressed least-squares regression. In Advances in neural information processing systems, pages 1213–1221, 2009.
*   [\[117\]](#chapter10.xhtml#r117b) J. K. Martin. An exact probability metric for decision tree splitting and stopping. Machine Learning, 28(2):257–291, 1997.
*   [\[118\]](#chapter10.xhtml#r118b) A. B. Merkov. Image recognition. Introduction to statistical learning methods. URSS, Moscow, 2010.
*   [\[119\]](#chapter1.xhtml#r119b) M. D. Mesarovic, D. Macko, and Y. Takahara. Theory of hierarchical, multilevel, systems. Academic Press, 1970.
*   [\[120\]](#chapter8.xhtml#r120b) N. Metropolis and S. Ulam. The monte carlo method. Journal of the American Statistical Association, 44(247):335–341, 1949.
*   [\[121\]](#chapter8.xhtml#r121b) D. D. L. Minh and Do Le Minh. Understanding the hastings algorithm. Communications in Statistics—Simulation and Computation, 44(2):332–349, 2015.
*   [\[122\]](#chapter4.xhtml#r122b) M. Minsky and S. Papert. Perceptrons: An introduction to computational geometry. MIT Press, Cambridge, 1969.
*   [\[123\]](#chapter4.xhtml#r123b) J. Neyman. Outline of a theory of statistical estimation based on the classical theory of probability. Philosophical Transactions of the Royal Society of London. Series A, Mathematical and Physical Sciences, 236(767):333–380, 1937.
*   [\[124\]](#chapter2.xhtml#r124b) A. V. Oppenheim. Discrete-time signal processing. Pearson Education India, 1999.
*   [\[125\]](#chapter1.xhtml#r125b) J. de D. Ortuzar and L.G. Willumsen. Modelling Transport. Wiley, 1995.
*   [\[126\]](#chapter1.xhtml#r126b) G. S. Osipov. Artificial intelligence methods. Fizmatlit, 2011.
*   [\[127\]](#chapter3.xhtml#r127b) K. Pearson. On lines and planes of closest fit to systems of points in space. Philosophical Magazine, 2(6):559–572, 1901.
*   [\[128\]](#chapter3.xhtml#r128b) F. Pedregosa, G. Varoquaux, A. Gramfort, V. Michel, B. Thirion, O. Grisel, M. Blondel, P. Prettenhofer, R. Weiss, V. Dubourg, J. Vanderplas, A. Passos, D. Cournapeau, M. Brucher, M. Perrot, and E. Duchesnay. Scikit-learn: Machine learning in Python. Journal of Machine Learning Research, 12:2825–2830, 2011.
*   [\[129\]](#chapter11.xhtml#r129b) Michiel Pezij, Denie CM Augustijn, Dimmie MD Hendriks, and Suzanne JMH Hulscher. Applying transfer function-noise modelling to characterize soil moisture dynamics: a data-driven approach using remote sensing data. Environmental Modelling & Software, 131:104756, 2020.
*   [\[130\]](#chapter11.xhtml#r130b) O.S. Pokrovsky, L.S. Shirokova, S.N. Kirpotin, S. Audry, J. Viers, and B. Dupre. Effect of permafrost thawing on organic carbon and trace element colloidal speciation in the thermokarst lakes of western siberia. Biogeosciences, 8(3):565–583, 2011.
*   [\[131\]](#chapter11.xhtml#r131b) V Polishchuk and Yu Polishchuk. Modeling and prediction of dynamics of thermokarst lake fields using satellite images. In Permafrost: Distribution, Composition and Impacts on Infrastructure and Ecosystems, pages 205–234. Nova Science Publisher, NY, 2014.
*   [\[132\]](#chapter11.xhtml#r132b) YuM Polishchuk, AN Bogdanov, IN Muratov, VYu Polishchuk, A Lim, RM Manasypov, LS Shirokova, and OS Pokrovsky. Minor contribution of small thaw ponds to the pools of carbon and methane in the inland waters of the permafrost-affected part of the western siberian lowland. Environmental Research Letters, 13(4):045002, 2018.
*   [\[133\]](#chapter11.xhtml#r133b) Yury M. Polishchuk, Alexander N. Bogdanov, Vladimir Yu Polishchuk, Rinat M. Manasypov, Liudmila S. Shirokova, Sergey N. Kirpotin, and Oleg S. Pokrovsky. Size distribution, surface coverage, water, carbon, and metal storage of thermokarst lakes in the permafrost zone of the western siberia lowland. Water, 9(3):228, 2017.
*   [\[134\]](#chapter3.xhtml#r134b) B. T. Polyak. Introduction to optimization. Nauka, 1983.
*   [\[135\]](#chapter7.xhtml#r135b) B. T. Polyak and E. N. Gryazina. Hit-and-run: new design technique for stabilization, robustness and optimization of linear systems. IFAC Proceedings Volumes, 41(2):376–380, 2008.
*   [\[136\]](#chapter3.xhtml#r136b) B. T. Polyak and M. V. Khlebnikov. Principle component analysis: Robust versions. Automation and Remote Control, 78(3):490–506, 2017.
*   [\[137\]](#chapter1.xhtml#r137b) A. D. Polyanin and A. V. Manzhirov. Handbook of integral equations. CRC press, 2008.
*   [\[138\]](#chapter2.xhtml#r138b) Yu. Popkov and A. Popkov. New methods of entropy-robust estimation for randomized models under limited data. Entropy, 16(2):675–698, 2014.
*   [\[139\]](#chapter3.xhtml#r139b) Yu. S. Popkov. Macrosystems theory and its applications (Lecture Notes in Control and Information Sciences, vol. 203). Springer, 1995.
*   [\[140\]](#chapter7.xhtml#r140b) Yu. S. Popkov. On convergence of direct multiplicative methods in constrained entropy maximization problems. Automation and Remote Control, 59(4):534–544, 1998.
*   [\[141\]](#chapter1.xhtml#r141b) Yu. S. Popkov. Theory of macrosystems. Equilibrium models. URSS, Moscow, 1999.
*   [\[142\]](#chapter7.xhtml#r142b) Yu. S. Popkov. New class of multiplicative algorithms for solving of entropy-linear programs. European Journal of Operational Research, 174(3):1368–1379, 2006.
*   [\[143\]](#chapter3.xhtml#r143b) Yu. S. Popkov. Theory of macrosystems. Equilibrium models. URSS, Moscow, 2012.
*   [\[144\]](#chapter10.xhtml#r144b) Yu. S. Popkov, Yu. A. Dubnov, and A. Yu. Popkov. New method of randomized forecasting using entropy-robust estimation: Application to the world population prediction. Mathematics, 4(1):1–16, 2016.
*   [\[145\]](#chapter3.xhtml#r145b) Yu. S. Popkov, Yu. A. Dubnov, and A. Yu. Popkov. Randomized machine learning: Statement, solution, applications. In *Intelligent Systems (IS), 2016 IEEE 8th International Conference on*, pages 27–39. IEEE, 2016.
*   [\[146\]](#chapter1.xhtml#r146b) Yu. S. Popkov, O. N. Kiselev, N. P. Petrov, and B. L. Shmulyan. Identification and optimization of nonlinear stochastic systems. Energiya, 1976.
*   [\[147\]](#chapter7.xhtml#r147b) Yu. S. Popkov, A. Yu. Popkov, and B. S. Darkhovsky. Parallel monte carlo for entropy robust estimation. Mathematical Models and Computer Simulations, 8(1):27–39, 2016.
*   [\[148\]](#chapter2.xhtml#r148b) Yu. S. Popkov, A. Yu. Popkov, and Yu. A. Dubnov. Randomized machine learning: from empirical probability to entropy randomization. LENAND, Moscow, 2019.
*   [\[149\]](#chapter5.xhtml#r149b) Yu. S. Popkov, A. Yu. Popkov, and Yu. N. Lysak. Estimation of characteristics of randomized static models of data (entropy-robust approach). Automation and Remote Control, 74(11):1863–1877, 2013.
*   [\[150\]](#chapter10.xhtml#r150b) Yu. S. Popkov, Z. Volkovich, Yu. A. Dubnov, R. Avros, and E. Ravve. Entropy 2-soft classification of objects. Entropy, 19(4):178, 2017.
*   [\[151\]](#chapter11.xhtml#r151b) Yuri S. Popkov, Vladimir Y. Polishchuk, Evgeny S. Sokol, Yury M. Polishchuk, and Andrey V. Melnikov. A randomized algorithm for restoring missing data in the time series of lake areas using information on climatic parameters. In *8th Scientific Conference on Information Technologies for Intelligent Decision Making Support (ITIDS 2020)*, pages 186–190. Atlantis Press, 2020.
*   [\[152\]](#chapter1.xhtml#r152b) K. A. Pupkov, V. I. Kapalin, and A. S. Yushchenko. Functional series in theory of nonlinear systems. Nauka, 1976.
*   [\[153\]](#chapter1.xhtml#r153b) J. S. Racine and E. Maasoumi. A versatile and robust metric entropy test of time-reversibility, and other hypotheses. Journal of Econometrics, 138(2):547–567, 2007.
*   [\[154\]](#chapter11.xhtml#r154b) Brian Riordan, David Verbyla, and A. David McGuire. Shrinking ponds in subarctic alaska based on 1950–2002 remotely sensed images. Journal of Geophysical Research: Biogeosciences, 111(G4), 2006.
*   [\[155\]](#chapter10.xhtml#r155b) I. Rish. An empirical study of the naive bayes classifier. In *IJCAI 2001 Workshop on Empirical Methods in Artificial Intelligence*, volume 3, pages 41–46. IBM, 2001.
*   [\[156\]](#preface.xhtml#r156b) F. Rosenblatt. The perceptron, a perceiving and recognizing automaton Project Para. Cornell Aeronautical Laboratory, 1957.
*   [\[157\]](#chapter1.xhtml#r157b) R. D. Rosenkrantz. E.T. Jaynes: Papers on probability, statistics, and statistical physics. Kluwer Academic Publishers, 1989.
*   [\[158\]](#chapter3.xhtml#r158b) R. Y. Rubinstein and D. P. Kroese. The cross-entropy method: a unified approach to combinatorial optimization, monte-carlo simulation and machine learning, 2004.
*   [\[159\]](#chapter2.xhtml#r159b) R. Y. Rubinstein and D. P. Kroese. Simulation and the Monte Carlo method, volume 707. John Wiley & Sons, 2007.
*   [\[160\]](#chapter2.xhtml#r160b) G. Salton and M. J. McGill. Introduction to modern information retrieval. 1986.
*   [\[161\]](#chapter1.xhtml#r161b) A. A. Samarskii and A. P. Mikhailov. Mathematical modeling. 1997.
*   [\[162\]](#chapter3.xhtml#r162b) L. K. Saul and S. T. Roweis. Think globally, fit locally: unsupervised learning of low dimensional manifolds. Journal of Machine Learning Research, 4:119–155, 2003.
*   [\[163\]](#chapter10.xhtml#r163b) M. Sewell. Ensemble learning. RN, 11(02), 2008.
*   [\[164\]](#chapter11.xhtml#r164b) L. F. Shampine. Matlab program for quadrature in 2d. Applied Mathematics and Computation, 202(1):266–274, 2008.
*   [\[165\]](#chapter1.xhtml#r165b) C. E. Shannon. Communication theory of secrecy systems. Bell Labs Technical Journal, 28(4):656–715, 1949.
*   [\[166\]](#chapter2.xhtml#r166b) A. N. Shiryaev. Stochastic financial mathematics. Nauka, Moscow, 2002.
*   [\[167\]](#chapter2.xhtml#r167b) A. S. Sigachev. Model of text as a set of numerical attributes. Intellectual Technologies and Systems, 16:127–135, 2006.
*   [\[168\]](#chapter8.xhtml#r168b) I. M. Sobol. Numerical Monte Carlo methods. Nauka, Moscow, 1973.
*   [\[169\]](#chapter1.xhtml#r169b) V. D. Soloviev, B. V. Dobrov, V. V. Ivanov, and N. V. Lukashevich. Ontologies and thesauri: A tutorial, 2006.
*   [\[170\]](#chapter2.xhtml#r170b) G. Solton. Dynamic library information systems, 1979.
*   [\[171\]](#chapter3.xhtml#r171b) A. S. Strekalovskii. Elements of nonconvex optimization. Nauka, Novosibirsk, 2003.
*   \[172\] R. G. Strongin, V. P. Gergel, V. A. Grishagin, and K. A. Barkalov. Parallel computing in global optimization problems. *Moscow State University Press*, 2013.
*   [\[173\]](#chapter7.xhtml#r173b) R. G. Strongin and Ya. D. Sergeyev. Global optimization with non-convex constraints: Sequential and parallel algorithms. Springer Science & Business Media, 2000.
*   [\[174\]](#chapter5.xhtml#r174b) V. M. Tikhomirov, V. N. Alekseev, and S. V. Fomin. Optimal control. Nauka, Moscow, 1979.
*   [\[175\]](#chapter2.xhtml#r175b) I.G. Tsyganov. Neural network methods for automated analysis of information flows in real time. *Proceedings of International Youth Scientific and Technical Conference “Science Intensive Technologies and Intelligent Systems”*, pages 19–24, 2002.
*   [\[176\]](#chapter4.xhtml#r176b) Ya. Z. Tsypkin. Foundations of the theory of learned systems. Nauka, Moscow, 1970.
*   [\[177\]](#chapter1.xhtml#r177b) Ya. Z. Tsypkin and Yu. S. Popkov. Theory of nonlinear impulsive systems. 1973.
*   [\[178\]](#chapter4.xhtml#r178b) H. L. van Trees. Synthesis of optimum nonlinear control systems. MIT press, 1962.
*   [\[179\]](#preface.xhtml#r179b) V. N. Vapnik and A. Ya. Chervonenkis. Theory of image recognition. Nauka, Moscow, 1974.
*   [\[180\]](#chapter10.xhtml#r180b) V. N. Vapnik and A. Ya. Chervonenkis. Restoration of relations using empirical data. Nauka, Moscow, 1979.
*   [\[181\]](#chapter3.xhtml#r181b) S. S. Vempala. The random projection method, volume 65. American Mathematical Soc., 2005.
*   [\[182\]](#chapter4.xhtml#r182b) S. Vine. Options: A complete course for professionals. Alpina Publishers, 2015.
*   [\[183\]](#chapter9.xhtml#r183b) V. V. Voevodin and Vl. V. Voevodin. Parallel computing. BKhV-Peterburg, St. Petersburg, 2004.
*   [\[184\]](#chapter4.xhtml#r184b) V. Volterra. Theory of functionals and integrals and integro-differential equations. Blackie, 1931.
*   [\[185\]](#chapter4.xhtml#r185b) V. Volterra, J. Pérès. *Théorie générale des fonctionnelles* Tome 1. Généralités sur les fonctionnelles. Théorie des équations intégrales. Gauthier-Villars, 1936.
*   [\[186\]](#chapter11.xhtml#r186b) J. von Neumann. Various techniques used in connection with random digits. Appl. Math Ser., 12:36–38, 1951.
*   [\[187\]](#chapter10.xhtml#r187b) K. V. Vorontsov. Machine learning (a course of lectures), 2013. URL=[http:/​/​www.machinelearning.ru](http://www.machinelearning.ru).
*   [\[188\]](#chapter1.xhtml#r188b) K. V. Vorontsov. Mathematical methods of learning by precedents. a course of lectures (faculty of control and applied mathematics, moscow institute of physics and technology), 2013.
*   [\[189\]](#chapter2.xhtml#r189b) W. Weidlich and G. Haag. An integrated model of transport and urban evolution: with an application to a metropole of an emerging nation. Springer, 1999.
*   [\[190\]](#chapter3.xhtml#r190b) K. Q. Weinberger and L. K. Saul. Unsupervised learning of image manifolds by semidefinite programming. International Journal of Computer Vision, 70(1):77–90, 2006.
*   [\[191\]](#preface.xhtml#r191b) I. H. Witten and E. Frank. Data Mining: Practical machine learning tools and techniques. Morgan Kaufmann, 2005.
*   [\[192\]](#chapter10.xhtml#r192b) D. H. Wolpert. Stacked generalization. Neural Networks, 5(2):241–259, 1992.
*   [\[193\]](#chapter10.xhtml#r193b) X. Wu, V. Kumar, J. R. Quinlan, J. Ghosh, Q. Yang, H. Motoda, G. J. McLachlan, A. Ng, B. Liu, S. Yu. Philip, et al. Top 10 algorithms in data mining. Knowledge and Information Systems, 14(1):1–37, 2008.
*   [\[194\]](#chapter10.xhtml#r194b) N. G. Zagoruiko. Applied methods of data and knowledge analysis. Sobolev Institute of Mathematics, Novosibirsk, 1999.
*   [\[195\]](#chapter11.xhtml#r195b) M.N. Zheleznyak. Geotemperature field and permafrost in the southeast of the Siberian platform. Nauka, Novosibirsk, 2005.
*   [\[196\]](#chapter7.xhtml#r196b) A. Zhigljavsky and A. Zilinskas. Stochastic global optimization, volume 9. Springer Science & Business Media, 2007.
*   [\[197\]](#chapter2.xhtml#r197b) E. G. Zhilyakov. Quatization errors in estimation of autocorrelation functions of gaussian processes. Problems of Information Transmission, 18(3):90–94, 1982.
*   [\[198\]](#chapter10.xhtml#r198b) Yu. I. Zhuravlev, V. V. Ryazanov, and O. V. Sen'ko. Image recognition: mathematical methods, program system, applications. FAZIS, 2006.
*   [\[199\]](#chapter7.xhtml#r199b) A. V. Zorin and M. A. Fedotkin. Monte Carlo methods for parallel computing. Moscow State University Press, 2013.
*   [\[200\]](#chapter11.xhtml#r200b) Frieda S Zuidhoff and Else Kolstrup. Changes in palsa distribution in relation to climate change in laivadalen, northern sweden, especially 1960–1997. Permafrost and periglacial processes, 11(1):55–69, 2000.

# Index

A

*   Absolute information error, [91](#chapter3.xhtml#p91)
*   Abstract subsystems, [262](#chapter9.xhtml#p262)
*   Acceptance-Rejection method, [291](#chapter11.xhtml#p291)
*   ADCs, *see* [Analog-to-digital converters](#index.xhtml#ieidx_41)
*   Algorithmic test, [221](#chapter7.xhtml#p221)
*   Algorithms 
    *   bagging algorithms, [274](#chapter10.xhtml#p274)
    *   Bayesian ML algorithms, [12](#chapter1.xhtml#p12)
    *   composition, [273](#chapter10.xhtml#p273)–[274](#chapter10.xhtml#p273) 
        *   bagging, [274](#chapter10.xhtml#p274)
        *   boosting, [275](#chapter10.xhtml#p275)
        *   stacking, [274](#chapter10.xhtml#p274)–[275](#chapter10.xhtml#p274)
    *   for entropy randomized projection, [103](#chapter3.xhtml#p103)–[106](#chapter3.xhtml#p103)
    *   machine learning (ML), [10](#chapter1.xhtml#p10)–[11](#chapter1.xhtml#p10)
    *   max, [76](#chapter3.xhtml#p76)–[80](#chapter3.xhtml#p76), [83](#chapter3.xhtml#p83)
    *   multiplicative, [198](#chapter7.xhtml#p198) 
        *   with *P*\-active variables, [230](#chapter7.xhtml#p230)–[235](#chapter7.xhtml#p230)
    *   multiplicative algorithms with *P*\-active variables, [230](#chapter7.xhtml#p230)–[235](#chapter7.xhtml#p230)
    *   optimization 
        *   omissions in input and output data, [61](#chapter2.xhtml#p61)
        *   omissions in input data, [58](#chapter2.xhtml#p58)–[61](#chapter2.xhtml#p58)
        *   omissions in output data, [56](#chapter2.xhtml#p56)–[58](#chapter2.xhtml#p56)
    *   for probability density functions, [165](#chapter5.xhtml#p165) 
        *   estimation algorithms for RPM-F model, [169](#chapter5.xhtml#p169)–[171](#chapter5.xhtml#p169)
        *   estimation algorithms for RPM-Orig model, [165](#chapter5.xhtml#p165)–[167](#chapter5.xhtml#p165)
        *   estimation algorithms for RPM-Rel model, [167](#chapter5.xhtml#p167)–[169](#chapter5.xhtml#p167)
    *   recursive, [69](#chapter3.xhtml#p69)
*   Amplitude and time quantization, [30](#chapter2.xhtml#p30)–[32](#chapter2.xhtml#p30)
*   Analog 
    *   data source, [17](#chapter2.xhtml#p17)
    *   function, [30](#chapter2.xhtml#p30)
    *   sensors, [17](#chapter2.xhtml#p17)–[18](#chapter2.xhtml#p17)
    *   signal, [34](#chapter2.xhtml#p34)
    *   source of data, [18](#chapter2.xhtml#p18) 
        *   deterministic functions, [18](#chapter2.xhtml#p18)–[21](#chapter2.xhtml#p18)
        *   random functions, [21](#chapter2.xhtml#p21)–[29](#chapter2.xhtml#p21)
*   Analog-to-digital converters (ADCs), [17](#chapter2.xhtml#p17), [29](#chapter2.xhtml#p29)
*   Analytical functions, [19](#chapter2.xhtml#p19)
*   API, *see* [Application programming interfaces](#index.xhtml#ieidx_44)
*   Application programming interfaces (API), [249](#chapter9.xhtml#p249), [254](#chapter9.xhtml#p254)
*   Appropriate projector matrix, [110](#chapter3.xhtml#p110)–[112](#chapter3.xhtml#p110)
*   Approximate estimation of structural characteristics of linear dynamic regression (LDR) model, [343](#appB.xhtml#p343)–[344](#appB.xhtml#p343) 
    *   order *p*, [344](#appB.xhtml#p344)
    *   parameters ranges, [344](#appB.xhtml#p344)–[345](#appB.xhtml#p344)
*   Approximation, [121](#chapter4.xhtml#p121), [304](#chapter11.xhtml#p304) 
    *   accuracy, [244](#chapter8.xhtml#p244)
    *   of information cross-entropy functional, [77](#chapter3.xhtml#p77)–[80](#chapter3.xhtml#p77)
    *   quality functional, [20](#chapter2.xhtml#p20)
*   Audio data, [32](#chapter2.xhtml#p32)–[35](#chapter2.xhtml#p32)
*   Auxiliary dynamic models, [43](#chapter2.xhtml#p43)–[45](#chapter2.xhtml#p43)
*   Auxiliary variable matrix, [160](#chapter5.xhtml#p160)
*   Auxiliary vectors, [67](#chapter3.xhtml#p67)

B

*   Bagging algorithms, [274](#chapter10.xhtml#p274)
*   Balancing model (BM), [162](#chapter5.xhtml#p162)
*   Bayes' formula, [12](#chapter1.xhtml#p12)
*   Bayes' theorem, [270](#chapter10.xhtml#p270)
*   Binary classification problem, [267](#chapter10.xhtml#p267)
*   Binary digital source, [17](#chapter2.xhtml#p17)
*   Binary method (BI), [38](#chapter2.xhtml#p38)
*   Bit image, [35](#chapter2.xhtml#p35)
*   Boltzmann, L., [163](#chapter5.xhtml#p163)
*   Boltzmann constant, [163](#chapter5.xhtml#p163)
*   Boltzmann entropies, [187](#chapter6.xhtml#p187) 
    *   Boltzmann information entropy, [166](#chapter5.xhtml#p166), [168](#chapter5.xhtml#p168), [170](#chapter5.xhtml#p170), [186](#chapter6.xhtml#p186), [201](#chapter7.xhtml#p201)
    *   robust estimation, [187](#chapter6.xhtml#p187)
    *   robust ML algorithm, [187](#chapter6.xhtml#p187)
*   Boosting, [275](#chapter10.xhtml#p275)
*   Bounded variation, [20](#chapter2.xhtml#p20)
*   Brownian motion process, [26](#chapter2.xhtml#p26)–[27](#chapter2.xhtml#p26)
*   Brownian random process, [27](#chapter2.xhtml#p27)

C

*   Cauchy–Bunyakovsky–Schwarz inequality, [245](#chapter8.xhtml#p245)
*   Chain of inequalities, [67](#chapter3.xhtml#p67)
*   Chapman–Kolmogorov equations, [28](#chapter2.xhtml#p28)–[29](#chapter2.xhtml#p28)
*   Chebyshev functional, [21](#chapter2.xhtml#p21)
*   Choice and parameterization, PM, [6](#chapter1.xhtml#p6)–[10](#chapter1.xhtml#p6)
*   Classification; *see also* [EDR for binary classification problems](#index.xhtml#ieidx_221); [Entropy classification](#index.xhtml#ieidx_223)
*   accuracy, [94](#chapter3.xhtml#p94)–[97](#chapter3.xhtml#p94)
*   binary classification problem, [267](#chapter10.xhtml#p267)
*   four-dimensional objects, [280](#chapter10.xhtml#p280)–[282](#chapter10.xhtml#p280)
*   two-dimensional objects, [282](#chapter10.xhtml#p282)–[285](#chapter10.xhtml#p282)
*   Coefficient of proportionality, [52](#chapter2.xhtml#p52)
*   Collective motivations, [4](#chapter1.xhtml#p4)
*   Column-compressed matrix, [74](#chapter3.xhtml#p74)
*   Compact set 
    *   arbitrary compact set *Q*, [243](#chapter8.xhtml#p243)–[244](#chapter8.xhtml#p243)
*   Compressed sensing, [72](#chapter3.xhtml#p72)
*   Computational methods of RML, [197](#chapter7.xhtml#p197)–[198](#chapter7.xhtml#p197) 
    *   classes of balance equations, [198](#chapter7.xhtml#p198) 
        *   equations with analytical functions, [201](#chapter7.xhtml#p201)–[202](#chapter7.xhtml#p201)
        *   equations with integral components, [198](#chapter7.xhtml#p198)–[201](#chapter7.xhtml#p198)
    *   Monte Carlo packet iterations for global optimization, [202](#chapter7.xhtml#p202) 
        *   admissible set of general form, [213](#chapter7.xhtml#p213)–[215](#chapter7.xhtml#p213)
        *   canonical form of global optimization problem, [203](#chapter7.xhtml#p203)–[205](#chapter7.xhtml#p203)
        *   convergence of GFS algorithm, [209](#chapter7.xhtml#p209)–[213](#chapter7.xhtml#p209)
        *   experimental study of GFS algorithm, [217](#chapter7.xhtml#p217)–[223](#chapter7.xhtml#p217)
        *   idea of method and concept of solution, [205](#chapter7.xhtml#p205)–[206](#chapter7.xhtml#p205)
        *   logical structure of GFS algorithm, [215](#chapter7.xhtml#p215)–[216](#chapter7.xhtml#p215)
        *   probabilistic characteristics of random sequences, [206](#chapter7.xhtml#p206)–[209](#chapter7.xhtml#p206)
    *   multidimensional integrals using Monte Carlo method, [223](#chapter7.xhtml#p223)–[230](#chapter7.xhtml#p223)
    *   multiplicative algorithms with *P*\-active variables, [230](#chapter7.xhtml#p230)–[235](#chapter7.xhtml#p230)
*   Computational processor, [249](#chapter9.xhtml#p249)
*   Computer memory, [254](#chapter9.xhtml#p254)
*   Computer simulation principle, [12](#chapter1.xhtml#p12)
*   Computer systems 
    *   advancement of, [251](#chapter9.xhtml#p251)
    *   multi-core processor, [249](#chapter9.xhtml#p249)
    *   multi-processor, [251](#chapter9.xhtml#p251)
    *   supercomputer class, [264](#chapter9.xhtml#p264)
    *   user layer, [256](#chapter9.xhtml#p256)
    *   utilization, [250](#chapter9.xhtml#p250)
*   Conditional density maximization, [12](#chapter1.xhtml#p12)
*   Conditional probability, [12](#chapter1.xhtml#p12)
*   Condorcet jury theorem, [273](#chapter10.xhtml#p273)
*   Consistency conditions, [22](#chapter2.xhtml#p22)
*   Continuity, [19](#chapter2.xhtml#p19)
*   Continuous at a point, [19](#chapter2.xhtml#p19)
*   Continuous functions, [126](#chapter4.xhtml#p126)
*   Continuous nonlinearities, [118](#chapter4.xhtml#p118)
*   Continuous time-varying functions, [120](#chapter4.xhtml#p120), [126](#chapter4.xhtml#p126)
*   Convergent Taylor series, [19](#chapter2.xhtml#p19)
*   Coprocessor, [249](#chapter9.xhtml#p249)
*   Covariance matrix, [66](#chapter3.xhtml#p66)
*   Coverage errors, [39](#chapter2.xhtml#p39)
*   Cross-entropy, [84](#chapter3.xhtml#p84) 
    *   minimization, [85](#chapter3.xhtml#p85)
    *   reduction algorithm, [84](#chapter3.xhtml#p84)–[87](#chapter3.xhtml#p84)
*   Cross-testing, [305](#chapter11.xhtml#p305)
*   CUDA, [257](#chapter9.xhtml#p257), [265](#chapter9.xhtml#p265)

D

*   Data, [17](#chapter2.xhtml#p17) 
    *   adequacy, [18](#chapter2.xhtml#p18)
    *   approximation, [68](#chapter3.xhtml#p68)
    *   elements, [264](#chapter9.xhtml#p264)
    *   interpolation problem, [40](#chapter2.xhtml#p40)
    *   maximizing, [62](#chapter2.xhtml#p62)
*   Data matrix, [65](#chapter3.xhtml#p65), [84](#chapter3.xhtml#p84), [104](#chapter3.xhtml#p104) 
    *   classes of transformations, [101](#chapter3.xhtml#p101)
    *   information capacity of, [84](#chapter3.xhtml#p84)
    *   point-set representation, [100](#chapter3.xhtml#p100)–[101](#chapter3.xhtml#p100)
    *   singular decomposition method, [66](#chapter3.xhtml#p66)–[68](#chapter3.xhtml#p66)
*   Data set simulation, [98](#chapter3.xhtml#p98)–[99](#chapter3.xhtml#p98)
*   Data source (DS), [17](#chapter2.xhtml#p17)–[18](#chapter2.xhtml#p17), [158](#chapter5.xhtml#p158)–[159](#chapter5.xhtml#p158) 
    *   analog source of data, [18](#chapter2.xhtml#p18) 
        *   deterministic functions, [18](#chapter2.xhtml#p18)–[21](#chapter2.xhtml#p18)
        *   random functions, [21](#chapter2.xhtml#p21)–[29](#chapter2.xhtml#p21)
    *   digital source of data, [29](#chapter2.xhtml#p29) 
        *   amplitude and time quantization, [30](#chapter2.xhtml#p30)–[32](#chapter2.xhtml#p30)
        *   audio data, [32](#chapter2.xhtml#p32)–[35](#chapter2.xhtml#p32)
        *   government statistical data, [38](#chapter2.xhtml#p38)–[40](#chapter2.xhtml#p38)
        *   graphical data, [35](#chapter2.xhtml#p35)–[36](#chapter2.xhtml#p35)
        *   text data, [36](#chapter2.xhtml#p36)–[38](#chapter2.xhtml#p36)
    *   restoration methods for missing data, [40](#chapter2.xhtml#p40) 
        *   auxiliary dynamic models, [43](#chapter2.xhtml#p43)–[45](#chapter2.xhtml#p43)
        *   interpolation, [40](#chapter2.xhtml#p40)–[43](#chapter2.xhtml#p40)
        *   randomized restoration method, [52](#chapter2.xhtml#p52)–[63](#chapter2.xhtml#p52)
        *   spatial entropy decomposition, [45](#chapter2.xhtml#p45)–[52](#chapter2.xhtml#p45)
*   Decision-making (DM), [2](#chapter1.xhtml#p2), [*3*](#chapter1.xhtml#p3)
*   Decision tree (DT), [267](#chapter10.xhtml#p267)–[268](#chapter10.xhtml#p267)
*   Degree of abstraction, [7](#chapter1.xhtml#p7)
*   Degree of smoothness, [19](#chapter2.xhtml#p19)–[20](#chapter2.xhtml#p19), [197](#chapter7.xhtml#p197)
*   Delta-function, [34](#chapter2.xhtml#p34)
*   Delta modulation (DM), [32](#chapter2.xhtml#p32)
*   Demoeconomic system, [4](#chapter1.xhtml#p4)
*   Density functions, [160](#chapter5.xhtml#p160)
*   Dependent elements, [240](#chapter8.xhtml#p240)
*   Deterministic functions, [18](#chapter2.xhtml#p18)–[21](#chapter2.xhtml#p18)
*   Deterministic sets, [10](#chapter1.xhtml#p10)–[11](#chapter1.xhtml#p10)
*   Differential equations, [8](#chapter1.xhtml#p8)
*   Diffusion processes, [29](#chapter2.xhtml#p29)
*   Digital data source, [17](#chapter2.xhtml#p17)
*   Digital source of data, [29](#chapter2.xhtml#p29) 
    *   amplitude and time quantization, [30](#chapter2.xhtml#p30)–[32](#chapter2.xhtml#p30)
    *   audio data, [32](#chapter2.xhtml#p32)–[35](#chapter2.xhtml#p32)
    *   government statistical data, [38](#chapter2.xhtml#p38)–[40](#chapter2.xhtml#p38)
    *   graphical data, [35](#chapter2.xhtml#p35)–[36](#chapter2.xhtml#p35)
    *   text data, [36](#chapter2.xhtml#p36)–[38](#chapter2.xhtml#p36)
*   Digital-to-analog converters (DACs), [18](#chapter2.xhtml#p18)
*   Dimensionality reduction, [72](#chapter3.xhtml#p72)
*   Dimension reduction methods, [65](#chapter3.xhtml#p65)–[66](#chapter3.xhtml#p65) 
    *   dimension reduction for linear model learning, [87](#chapter3.xhtml#p87)
    *   direct and inverse projection, [73](#chapter3.xhtml#p73)–[75](#chapter3.xhtml#p73)
    *   EDR for binary classification problems, [92](#chapter3.xhtml#p92)
    *   entropy methods for random projection 
        *   algorithms for entropy randomized projection, [103](#chapter3.xhtml#p103)–[106](#chapter3.xhtml#p103)
        *   appropriate projector matrix [110](#chapter3.xhtml#p110)–[112](#chapter3.xhtml#p110)
        *   implementation of random projectors and numerical characteristics, [106](#chapter3.xhtml#p106)–[107](#chapter3.xhtml#p106)
        *   random projector matrices, [107](#chapter3.xhtml#p107)–[109](#chapter3.xhtml#p107)
        *   statements, [100](#chapter3.xhtml#p100)–[103](#chapter3.xhtml#p100)
    *   entropy optimization of parallel procedure 
        *   definition and structure, [81](#chapter3.xhtml#p81)
        *   optimality conditions and algorithm, [81](#chapter3.xhtml#p81)–[83](#chapter3.xhtml#p81)
    *   entropy optimization of sequential procedure, [75](#chapter3.xhtml#p75) 
        *   approximation of information cross-entropy functional, [77](#chapter3.xhtml#p77)–[80](#chapter3.xhtml#p77)
        *   optimality conditions and algorithm, [75](#chapter3.xhtml#p75)–[77](#chapter3.xhtml#p75)
    *   entropy reduction under matrix norm and information capacity constraints, [84](#chapter3.xhtml#p84)–[87](#chapter3.xhtml#p84) 
        *   cross-entropy reduction algorithm, [84](#chapter3.xhtml#p84)–[87](#chapter3.xhtml#p84)
        *   Frobenius norms of matrices, [84](#chapter3.xhtml#p84)
        *   information capacity of data matrix, [84](#chapter3.xhtml#p84)
    *   linear model learning, [87](#chapter3.xhtml#p87)
    *   principal component analysis, [68](#chapter3.xhtml#p68)–[70](#chapter3.xhtml#p68)
    *   random projection method, [70](#chapter3.xhtml#p70)–[73](#chapter3.xhtml#p70)
    *   singular decomposition method for data matrix, [66](#chapter3.xhtml#p66)–[68](#chapter3.xhtml#p66)
*   Direct-inverse projection, [73](#chapter3.xhtml#p73), [81](#chapter3.xhtml#p81)
*   Direct projection, [73](#chapter3.xhtml#p73)
*   Discrete distribution function (DDF), [107](#chapter3.xhtml#p107)
*   Discrete Fourier transform (DFT), [34](#chapter2.xhtml#p34)
*   Discrete input functions, [123](#chapter4.xhtml#p123)
*   DS, *see* [Data source](#index.xhtml#ieidx_145)
*   Dynamic intelligent systems, [8](#chapter1.xhtml#p8)
*   Dynamic models 
    *   with structured power nonlinearities, [190](#chapter6.xhtml#p190)–[191](#chapter6.xhtml#p190)
    *   with unstructured power nonlinearities, [189](#chapter6.xhtml#p189)
*   Dynamic regression; *see also* [Randomized machine learning in dynamic regression and prediction](#index.xhtml#ieidx_672)
*   first-order, [295](#chapter11.xhtml#p295)–[296](#chapter11.xhtml#p295)
*   second-order, [295](#chapter11.xhtml#p295)–[296](#chapter11.xhtml#p295)

E

*   Economic activity, [4](#chapter1.xhtml#p4)–[5](#chapter1.xhtml#p4)
*   EDR, *see* [Entropy dimension reduction](#index.xhtml#ieidx_250)
*   EDR for binary classification problems, [92](#chapter3.xhtml#p92)
*   Electrical load model, [295](#chapter11.xhtml#p295)–[296](#chapter11.xhtml#p295)
*   Elementary approximating functions, [21](#chapter2.xhtml#p21)
*   Empirical risk, [11](#chapter1.xhtml#p11) 
    *   minimization, [9](#chapter1.xhtml#p9)
*   Energy spectrum, [35](#chapter2.xhtml#p35)
*   Ensemble analysis (EA) block, [261](#chapter9.xhtml#p261)
*   Ensemble of decisions, [12](#chapter1.xhtml#p12)
*   Entropy, [163](#chapter5.xhtml#p163) 
    *   decomposition, [47](#chapter2.xhtml#p47), [52](#chapter2.xhtml#p52)
    *   expression, [52](#chapter2.xhtml#p52)
    *   function, [164](#chapter5.xhtml#p164), [192](#chapter6.xhtml#p192)
*   Entropy classification, [267](#chapter10.xhtml#p267) 
    *   composition algorithms, [273](#chapter10.xhtml#p273)–[274](#chapter10.xhtml#p273) 
        *   bagging, [274](#chapter10.xhtml#p274)
        *   boosting, [275](#chapter10.xhtml#p275)
        *   stacking, [274](#chapter10.xhtml#p274)–[275](#chapter10.xhtml#p274)
    *   problem formulation, [275](#chapter10.xhtml#p275)–[276](#chapter10.xhtml#p275)
    *   standard classification methods, [267](#chapter10.xhtml#p267)–[268](#chapter10.xhtml#p267) 
        *   decision tree, [268](#chapter10.xhtml#p268)
        *   exponential approximation, [273](#chapter10.xhtml#p273)
        *   Fisher's linear discriminant, [272](#chapter10.xhtml#p272)
        *   *k*\-nearest neighbor, [269](#chapter10.xhtml#p269)
        *   linear classifiers, [271](#chapter10.xhtml#p271)–[273](#chapter10.xhtml#p271)
        *   logistic regression, [273](#chapter10.xhtml#p273)
        *   naive Bayes, [270](#chapter10.xhtml#p270)–[271](#chapter10.xhtml#p270)
        *   single-layer perceptron, [272](#chapter10.xhtml#p272)
        *   support vector machines, [273](#chapter10.xhtml#p273)
    *   testing stage, [278](#chapter10.xhtml#p278)–[280](#chapter10.xhtml#p278)
*   Entropy dimension reduction (EDR), [74](#chapter3.xhtml#p74), [98](#chapter3.xhtml#p98), [100](#chapter3.xhtml#p100)
*   Entropy-linear programming problem, [184](#chapter6.xhtml#p184)
*   Entropy maximization principle, [16](#chapter1.xhtml#p16)
*   Entropy methods for random projection 
    *   algorithms for entropy randomized projection, [103](#chapter3.xhtml#p103)–[106](#chapter3.xhtml#p103)
    *   appropriate projector matrix, [110](#chapter3.xhtml#p110)–[112](#chapter3.xhtml#p110)
    *   implementation of random projectors and numerical characteristics, [106](#chapter3.xhtml#p106)–[107](#chapter3.xhtml#p106)
    *   random projector matrices, [107](#chapter3.xhtml#p107)–[109](#chapter3.xhtml#p107)
    *   statements, [100](#chapter3.xhtml#p100)–[103](#chapter3.xhtml#p100)
*   Entropy-nonlinear programming, [186](#chapter6.xhtml#p186)
*   Entropy-optimal, [105](#chapter3.xhtml#p105)–[106](#chapter3.xhtml#p105) 
    *   DDF, [110](#chapter3.xhtml#p110)
    *   discrete probability distribution, [109](#chapter3.xhtml#p109)
    *   distribution, [48](#chapter2.xhtml#p48)
    *   PDFs, [61](#chapter2.xhtml#p61), [89](#chapter3.xhtml#p89), [104](#chapter3.xhtml#p104), [175](#chapter5.xhtml#p175), [180](#chapter5.xhtml#p180), [222](#chapter7.xhtml#p222), [278](#chapter10.xhtml#p278), [282](#chapter10.xhtml#p282), [*292*](#chapter11.xhtml#p292)
    *   projector matrix, [74](#chapter3.xhtml#p74), [79](#chapter3.xhtml#p79)
    *   randomized model, [181](#chapter5.xhtml#p181), [237](#chapter8.xhtml#p237), [294](#chapter11.xhtml#p294)
    *   robability distribution function, [111](#chapter3.xhtml#p111)
*   Entropy optimization 
    *   of parallel procedure 
        *   definition and structure, [81](#chapter3.xhtml#p81)
        *   optimality conditions and algorithm, [81](#chapter3.xhtml#p81)–[83](#chapter3.xhtml#p81)
    *   of sequential procedure, [75](#chapter3.xhtml#p75) 
        *   approximation of information cross-entropy functional, [77](#chapter3.xhtml#p77)–[80](#chapter3.xhtml#p77)
        *   optimality conditions and algorithm, [75](#chapter3.xhtml#p75)–[77](#chapter3.xhtml#p75)
*   Entropy-randomized machine learning of *LDRR*, [317](#chapter11.xhtml#p317)–[321](#chapter11.xhtml#p317)
*   Entropy randomized modelling and forecasting 
    *   data on state of thermokarst lakes, [314](#chapter11.xhtml#p314)–[317](#chapter11.xhtml#p314)
    *   entropy-randomized machine learning of *LDRR*, [317](#chapter11.xhtml#p317)–[321](#chapter11.xhtml#p317)
    *   randomized forecasting of thermokarst lakes area evolution, [324](#chapter11.xhtml#p324)
    *   results of training, testing and forecasting, [324](#chapter11.xhtml#p324)–[332](#chapter11.xhtml#p324)
    *   structures of randomized models of thermokarst lakes state, [311](#chapter11.xhtml#p311)–[314](#chapter11.xhtml#p311)
    *   testing procedure, data and accuracy estimates, [321](#chapter11.xhtml#p321)–[323](#chapter11.xhtml#p321)
    *   thermokarst lakes and climate change, [309](#chapter11.xhtml#p309)
    *   thermokarst lakes of Western Siberia, [309](#chapter11.xhtml#p309)–[311](#chapter11.xhtml#p309)
*   Entropy randomized projection 
    *   algorithm, [103](#chapter3.xhtml#p103)
    *   problem, [101](#chapter3.xhtml#p101)–[102](#chapter3.xhtml#p101)
*   Entropy reduction under matrix norm and information capacity constraints, [84](#chapter3.xhtml#p84)–[87](#chapter3.xhtml#p84) 
    *   cross-entropy reduction algorithm, [84](#chapter3.xhtml#p84)–[87](#chapter3.xhtml#p84)
    *   Frobenius norms of matrices, [84](#chapter3.xhtml#p84)
    *   information capacity of data matrix, [84](#chapter3.xhtml#p84)
*   Entropy-robust estimation methods, [183](#chapter6.xhtml#p183)–[184](#chapter6.xhtml#p183) 
    *   dynamic RPM-quarand models, [188](#chapter6.xhtml#p188) 
        *   structured power nonlinearities, [190](#chapter6.xhtml#p190)–[191](#chapter6.xhtml#p190)
        *   unstructured power nonlinearities, [189](#chapter6.xhtml#p189)–[190](#chapter6.xhtml#p189)
    *   entropy-optimal probabilities of belonging, [191](#chapter6.xhtml#p191) 
        *   interval-type probabilities of belonging, [194](#chapter6.xhtml#p194)–[195](#chapter6.xhtml#p194)
        *   normalized probabilities of belonging, [191](#chapter6.xhtml#p191)–[194](#chapter6.xhtml#p191)
    *   probabilities of belonging, [184](#chapter6.xhtml#p184)–[185](#chapter6.xhtml#p184) 
        *   ML algorithm for RPM-QuaRand model with interval-type probabilities of belonging, [187](#chapter6.xhtml#p187)–[188](#chapter6.xhtml#p187)
        *   ML algorithm for RPM-QuaRand model with normalized probabilities of belonging, [185](#chapter6.xhtml#p185)–[186](#chapter6.xhtml#p185)
*   Entropy-robust estimation problem, [186](#chapter6.xhtml#p186)
*   Entropy-robust estimation procedures, [157](#chapter5.xhtml#p157)–[158](#chapter5.xhtml#p157) 
    *   algorithms for probability density functions, [165](#chapter5.xhtml#p165)
    *   Lagrange multipliers, equations for 
        *   RPM-Orig model with input and output errors, [182](#chapter5.xhtml#p182)
        *   RPM-Orig model with output errors, [180](#chapter5.xhtml#p180)–[181](#chapter5.xhtml#p180)
        *   RPM-Rel model with output errors, [181](#chapter5.xhtml#p181)–[182](#chapter5.xhtml#p181)
    *   optimality conditions and structure of entropy-optimal PDF, [173](#chapter5.xhtml#p173) 
        *   randomized models of RPM-Orig class with input and output errors, [179](#chapter5.xhtml#p179)–[180](#chapter5.xhtml#p179)
        *   randomized models of RPM-Orig class with output errors, [173](#chapter5.xhtml#p173)–[175](#chapter5.xhtml#p173)
        *   randomized models of RPM-Rel class with output errors, [175](#chapter5.xhtml#p175)–[179](#chapter5.xhtml#p175)
    *   optimality conditions for Lyapunov-type problems, [171](#chapter5.xhtml#p171)–[173](#chapter5.xhtml#p171)
    *   structure, [158](#chapter5.xhtml#p158)–[165](#chapter5.xhtml#p158)
*   Entropy-robust ML algorithm, [186](#chapter6.xhtml#p186)
*   Entropy-robust RML algorithm, [167](#chapter5.xhtml#p167)
*   Entropy-“worst” measurement noises, [181](#chapter5.xhtml#p181)–[182](#chapter5.xhtml#p181)
*   Errors, [39](#chapter2.xhtml#p39) 
    *   coverage errors, [39](#chapter2.xhtml#p39)
    *   systematic errors, [39](#chapter2.xhtml#p39)
*   Estimation algorithms 
    *   for RPM-F model, [169](#chapter5.xhtml#p169)–[171](#chapter5.xhtml#p169)
    *   for RPM-Orig model, [165](#chapter5.xhtml#p165)–[167](#chapter5.xhtml#p165)
    *   for RPM-Rel model, [167](#chapter5.xhtml#p167)–[169](#chapter5.xhtml#p167)
*   Estimation of solution characteristics, [216](#chapter7.xhtml#p216)
*   EstProb, [215](#chapter7.xhtml#p215)–[216](#chapter7.xhtml#p215)
*   Euclidean distances, [104](#chapter3.xhtml#p104)–[105](#chapter3.xhtml#p104), [269](#chapter10.xhtml#p269)
*   Euclidean space, [70](#chapter3.xhtml#p70)
*   Euler polygon approximation, [235](#chapter7.xhtml#p235)
*   Even-order moment functions, [25](#chapter2.xhtml#p25)
*   Evolution of empirical 
    *   confidence intervals and confidence levels, [154](#chapter4.xhtml#p154)
    *   median trajectory, [153](#chapter4.xhtml#p153)
    *   probability density function, [152](#chapter4.xhtml#p152)
    *   variance pipe, [151](#chapter4.xhtml#p151)
*   Evolution of mean trajectory, [151](#chapter4.xhtml#p151)
*   Evolution of *α*\-quantiles of the empirical PDF, [153](#chapter4.xhtml#p153)
*   Exponential approximation, [273](#chapter10.xhtml#p273)
*   Exponential Lagrange multipliers, [232](#chapter7.xhtml#p232), [234](#chapter7.xhtml#p234)
*   External information, [37](#chapter2.xhtml#p37)

F

*   Fast Johnson–LindenstraussTransform (FJLT), [72](#chapter3.xhtml#p72)
*   Feedback loop (FL), [2](#chapter1.xhtml#p2)
*   Fermi entropies, [187](#chapter6.xhtml#p187)
*   Fermi entropy-robust estimation, [188](#chapter6.xhtml#p188)
*   Fermi information entropy, [164](#chapter5.xhtml#p164), [201](#chapter7.xhtml#p201)
*   Fertility and mortality coefficients, [287](#chapter11.xhtml#p287)
*   Finite-dimensional approximation, [8](#chapter1.xhtml#p8)
*   Finite-dimensional concept of information entropy, [162](#chapter5.xhtml#p162)
*   Finite-dimensional distributions of random function, [22](#chapter2.xhtml#p22)
*   Finite-dimensional probability density functions, [22](#chapter2.xhtml#p22)–[23](#chapter2.xhtml#p22)
*   Finite-dimensional probability distributions, [22](#chapter2.xhtml#p22)–[24](#chapter2.xhtml#p22)
*   Finite-state object, [8](#chapter1.xhtml#p8)
*   First-order differential equation, [12](#chapter1.xhtml#p12)–[13](#chapter1.xhtml#p12)
*   First-order dynamic regression model, [295](#chapter11.xhtml#p295)–[296](#chapter11.xhtml#p295)
*   First-order optimality, [171](#chapter5.xhtml#p171)–[172](#chapter5.xhtml#p171), [231](#chapter7.xhtml#p231)
*   First-order system, [13](#chapter1.xhtml#p13)
*   Fisher's linear discriminant, [272](#chapter10.xhtml#p272)
*   Forecasting, [5](#chapter1.xhtml#p5), [294](#chapter11.xhtml#p294)
*   Four-dimensional objects, classification, [280](#chapter10.xhtml#p280)–[282](#chapter10.xhtml#p280)
*   Fourier integral, [23](#chapter2.xhtml#p23)
*   Fourier transform, [23](#chapter2.xhtml#p23), [33](#chapter2.xhtml#p33)–[34](#chapter2.xhtml#p33), [142](#chapter4.xhtml#p142)
*   Frequency distribution, [34](#chapter2.xhtml#p34)
*   Frobenius inner product, [77](#chapter3.xhtml#p77)
*   Frobenius matrix, [84](#chapter3.xhtml#p84)
*   Frobenius norms, [78](#chapter3.xhtml#p78) 
    *   of matrices, [84](#chapter3.xhtml#p84)
*   Functional characteristics, [8](#chapter1.xhtml#p8)
*   Functional entropy-linear programming, [167](#chapter5.xhtml#p167)
*   Functional series, [8](#chapter1.xhtml#p8)
*   Functional Volterra series, [126](#chapter4.xhtml#p126), [129](#chapter4.xhtml#p129)

G

*   Gâteaux derivative-based method, [171](#chapter5.xhtml#p171), [173](#chapter5.xhtml#p173)–[174](#chapter5.xhtml#p173), [178](#chapter5.xhtml#p178), [180](#chapter5.xhtml#p180)
*   Gaussian condition, [24](#chapter2.xhtml#p24)
*   Gaussian distribution, [71](#chapter3.xhtml#p71), [106](#chapter3.xhtml#p106)
*   Gaussian finite-dimensional probability distributions, [25](#chapter2.xhtml#p25)
*   Gaussian PDF, [239](#chapter8.xhtml#p239)
*   Gaussian random functions, [25](#chapter2.xhtml#p25)–[26](#chapter2.xhtml#p25)
*   Gaussian random process, [27](#chapter2.xhtml#p27)
*   Gaussian random variable, [239](#chapter8.xhtml#p239)
*   Gauss principle, [50](#chapter2.xhtml#p50)–[51](#chapter2.xhtml#p50)
*   Generalized Boltzmann information entropy, [165](#chapter5.xhtml#p165)
*   Generalized Fermi information entropy, [164](#chapter5.xhtml#p164)
*   Generation methods for random vectors with PDF, [237](#chapter8.xhtml#p237) 
    *   approximation, [244](#chapter8.xhtml#p244)–[248](#chapter8.xhtml#p244)
    *   direct generation method, [241](#chapter8.xhtml#p241) 
        *   compact set, [242](#chapter8.xhtml#p242)–[244](#chapter8.xhtml#p242)
        *   unit cube, [241](#chapter8.xhtml#p241)–[242](#chapter8.xhtml#p241)
    *   survey, [238](#chapter8.xhtml#p238) 
        *   random variables, [238](#chapter8.xhtml#p238)–[239](#chapter8.xhtml#p238)
        *   random vectors, [240](#chapter8.xhtml#p240)–[241](#chapter8.xhtml#p240)
*   GFS algorithm (Generation, Filtration, Selection), [206](#chapter7.xhtml#p206), [215](#chapter7.xhtml#p215), [223](#chapter7.xhtml#p223)
*   Gini impurity, [268](#chapter10.xhtml#p268)
*   Government statistical data, [38](#chapter2.xhtml#p38)–[40](#chapter2.xhtml#p38)
*   Government statistics system, [39](#chapter2.xhtml#p39)
*   Graphical data, [35](#chapter2.xhtml#p35)–[36](#chapter2.xhtml#p35)
*   Griewank function, [218](#chapter7.xhtml#p218)
*   *G*[*λ*]*\-convergent*, [234](#chapter7.xhtml#p234)

H

*   Hermite polynomials, [134](#chapter4.xhtml#p134), [136](#chapter4.xhtml#p136), [149](#chapter4.xhtml#p149)
*   Hessian matrix, [232](#chapter7.xhtml#p232)
*   Hierarchical systems, [7](#chapter1.xhtml#p7)
*   Hölder condition, [209](#chapter7.xhtml#p209)
*   Hölder constants, [197](#chapter7.xhtml#p197), [212](#chapter7.xhtml#p212), [217](#chapter7.xhtml#p217)
*   Hölder functions, [20](#chapter2.xhtml#p20), [204](#chapter7.xhtml#p204)
*   Homogeneous Markov processes, [28](#chapter2.xhtml#p28)
*   Homogeneous process, [26](#chapter2.xhtml#p26)
*   Hyper-threading technology, [253](#chapter9.xhtml#p253)

I

*   Identity axiom, [18](#chapter2.xhtml#p18)
*   Independent elements, [240](#chapter8.xhtml#p240)
*   Independent random process, [8](#chapter1.xhtml#p8)
*   Indicator of compactness, [100](#chapter3.xhtml#p100)–[102](#chapter3.xhtml#p100)
*   Individual motivations (IM), [2](#chapter1.xhtml#p2), [*3*](#chapter1.xhtml#p3)
*   Inequalities, [154](#chapter4.xhtml#p154)
*   Information 
    *   capacity, [84](#chapter3.xhtml#p84)
    *   cross-entropy, [73](#chapter3.xhtml#p73), [77](#chapter3.xhtml#p77), [81](#chapter3.xhtml#p81)
    *   entropy, [16](#chapter1.xhtml#p16) 
        *   functional, [16](#chapter1.xhtml#p16)
        *   maximization principle, [16](#chapter1.xhtml#p16)
    *   gain, [268](#chapter10.xhtml#p268)
*   Information system (IS), [261](#chapter9.xhtml#p261)–[262](#chapter9.xhtml#p261)
*   Information technologies of randomized machine learning, [249](#chapter9.xhtml#p249)–[250](#chapter9.xhtml#p249), [258](#chapter9.xhtml#p258)–[260](#chapter9.xhtml#p258) 
    *   architecture of modern computer systems, [250](#chapter9.xhtml#p250)–[255](#chapter9.xhtml#p250)
    *   implementation of packet iterations, [264](#chapter9.xhtml#p264)–[266](#chapter9.xhtml#p264)
    *   model development (MD), [260](#chapter9.xhtml#p260)
    *   model implementation (MI), [261](#chapter9.xhtml#p261)–[264](#chapter9.xhtml#p261)
    *   model learning (ML), [260](#chapter9.xhtml#p260)–[261](#chapter9.xhtml#p260)
    *   universal multithreaded architecture, [255](#chapter9.xhtml#p255)–[258](#chapter9.xhtml#p255)
*   Initial distribution, [26](#chapter2.xhtml#p26)
*   (Input, feedback)–output ensemble, [115](#chapter4.xhtml#p115)
*   Integral equations, [8](#chapter1.xhtml#p8)
*   Integral quadratic functional, [21](#chapter2.xhtml#p21)
*   Integro-differential equation, [29](#chapter2.xhtml#p29)
*   Interpolation, [40](#chapter2.xhtml#p40)–[43](#chapter2.xhtml#p40)
*   Interquantile subsets, [111](#chapter3.xhtml#p111)
*   Interval-type probabilities of belonging, [194](#chapter6.xhtml#p194)–[196](#chapter6.xhtml#p194)
*   Inverse document frequency (IDF), [38](#chapter2.xhtml#p38)
*   Inverse functions, [238](#chapter8.xhtml#p238)
*   Inverse projection, [66](#chapter3.xhtml#p66), [73](#chapter3.xhtml#p73)
*   Inverse vector, [66](#chapter3.xhtml#p66)

J

*   Jacobian matrix, [235](#chapter7.xhtml#p235)
*   Java, [256](#chapter9.xhtml#p256)
*   Jaynes, E., [16](#chapter1.xhtml#p16)
*   Johnson–Lindenstrauss lemma, [70](#chapter3.xhtml#p70)
*   Jump processes, [29](#chapter2.xhtml#p29)

K

*   Karush–Kuhn–Tucker conditions, [85](#chapter3.xhtml#p85)
*   *k*\-Nearest Neighbor (kNN), [72](#chapter3.xhtml#p72), [267](#chapter10.xhtml#p267), [269](#chapter10.xhtml#p269)
*   Kolmogorov theore, [138](#chapter4.xhtml#p138)
*   Kuhn–Tucker conditions, [86](#chapter3.xhtml#p86)
*   Kullback–Leibler divergence, [91](#chapter3.xhtml#p91)

L

*   Labor activity, [5](#chapter1.xhtml#p5)
*   Lagrange function, [86](#chapter3.xhtml#p86), [108](#chapter3.xhtml#p108), [171](#chapter5.xhtml#p171)–[172](#chapter5.xhtml#p171), [178](#chapter5.xhtml#p178), [193](#chapter6.xhtml#p193), [231](#chapter7.xhtml#p231)
*   Lagrange interpolating polynomial, [41](#chapter2.xhtml#p41)–[42](#chapter2.xhtml#p41)
*   Lagrange multipliers, [49](#chapter2.xhtml#p49), [58](#chapter2.xhtml#p58), [86](#chapter3.xhtml#p86), [90](#chapter3.xhtml#p90), [104](#chapter3.xhtml#p104), [174](#chapter5.xhtml#p174), [178](#chapter5.xhtml#p178), [182](#chapter5.xhtml#p182), [193](#chapter6.xhtml#p193), [198](#chapter7.xhtml#p198), [202](#chapter7.xhtml#p202), [222](#chapter7.xhtml#p222)–[223](#chapter7.xhtml#p222), [231](#chapter7.xhtml#p231), [278](#chapter10.xhtml#p278), [282](#chapter10.xhtml#p282), [290](#chapter11.xhtml#p290), [300](#chapter11.xhtml#p300) 
    *   equations for 
        *   RPM-Orig model with input and output errors, [182](#chapter5.xhtml#p182)
        *   RPM-Orig model with output errors, [180](#chapter5.xhtml#p180)–[181](#chapter5.xhtml#p180)
        *   RPM-Rel model with output errors, [181](#chapter5.xhtml#p181)–[182](#chapter5.xhtml#p181)
    *   method of, [171](#chapter5.xhtml#p171), [173](#chapter5.xhtml#p173)
*   Lattice functions, [144](#chapter4.xhtml#p144)
*   Layer of abstraction, [255](#chapter9.xhtml#p255)–[256](#chapter9.xhtml#p255)
*   Learning data (LD), [260](#chapter9.xhtml#p260)
*   Learning dataset, [296](#chapter11.xhtml#p296)–[299](#chapter11.xhtml#p296)
*   Learning sequence, [8](#chapter1.xhtml#p8)
*   Least-squares-based estimation, [217](#chapter7.xhtml#p217)
*   Least squares (LS) method, [72](#chapter3.xhtml#p72)
*   Lebesgue measure, [213](#chapter7.xhtml#p213)
*   Likelihood function, [12](#chapter1.xhtml#p12)
*   Linear activation function, [138](#chapter4.xhtml#p138)
*   Linear approximation, [124](#chapter4.xhtml#p124)
*   Linear block, [127](#chapter4.xhtml#p127)
*   Linear classifiers, [92](#chapter3.xhtml#p92)–[93](#chapter3.xhtml#p92), [268](#chapter10.xhtml#p268), [271](#chapter10.xhtml#p271)–[273](#chapter10.xhtml#p271)
*   Linear dynamic block, [128](#chapter4.xhtml#p128)
*   Linear dynamic element, [134](#chapter4.xhtml#p134)
*   Linear dynamic models, [44](#chapter2.xhtml#p44), [122](#chapter4.xhtml#p122), [142](#chapter4.xhtml#p142)–[144](#chapter4.xhtml#p142)
*   Linear functionals, [142](#chapter4.xhtml#p142)
*   Linear model, [88](#chapter3.xhtml#p88)–[89](#chapter3.xhtml#p88), [91](#chapter3.xhtml#p91), [212](#chapter7.xhtml#p212)
*   Linear static models, [87](#chapter3.xhtml#p87)
*   Lipschitz condition, [246](#chapter8.xhtml#p246)
*   Lipschitz constant, [20](#chapter2.xhtml#p20), [197](#chapter7.xhtml#p197), [238](#chapter8.xhtml#p238), [246](#chapter8.xhtml#p246)–[247](#chapter8.xhtml#p246)
*   Lipschitz functions, [20](#chapter2.xhtml#p20)
*   *L*²\-norm minimization, [278](#chapter10.xhtml#p278)
*   Logarithmical term frequency (LOGTF), [38](#chapter2.xhtml#p38)
*   Logistic regression, [273](#chapter10.xhtml#p273)
*   Lyapunov-type functional programming problems, [171](#chapter5.xhtml#p171)
*   Lyapunov-type optimization, [57](#chapter2.xhtml#p57)–[58](#chapter2.xhtml#p57), [103](#chapter3.xhtml#p103)–[104](#chapter3.xhtml#p103), [167](#chapter5.xhtml#p167), [170](#chapter5.xhtml#p170)

M

*   Machine learning algorithm (ML-A), [162](#chapter5.xhtml#p162)–[165](#chapter5.xhtml#p162)
*   Machine learning (ML), [1](#chapter1.xhtml#p1), [*3*](#chapter1.xhtml#p3), [250](#chapter9.xhtml#p250) 
    *   algorithms, [10](#chapter1.xhtml#p10)–[11](#chapter1.xhtml#p10)
    *   concepts, [9](#chapter1.xhtml#p9)–[12](#chapter1.xhtml#p9)
    *   first stage (choice and parameterization, PM), [6](#chapter1.xhtml#p6)–[10](#chapter1.xhtml#p6)
    *   fourth stage (generation of the optimized model, MI), [9](#chapter1.xhtml#p9)
    *   methodological approaches, [1](#chapter1.xhtml#p1)
    *   methods and algorithms, [6](#chapter1.xhtml#p6)
    *   minimization, [9](#chapter1.xhtml#p9)
    *   principles of randomized machine learning procedure, [12](#chapter1.xhtml#p12)–[16](#chapter1.xhtml#p12)
    *   second stage (formation of input (cause) and output, PE), [8](#chapter1.xhtml#p8)–[9](#chapter1.xhtml#p8)
    *   structure, [6](#chapter1.xhtml#p6)–[9](#chapter1.xhtml#p6)
    *   third stage (formation of data arrays, MT), [9](#chapter1.xhtml#p9)–[10](#chapter1.xhtml#p9)
    *   transformation of knowledge into decisions, [2](#chapter1.xhtml#p2)–[6](#chapter1.xhtml#p2)
*   Macrodemography, [5](#chapter1.xhtml#p5)
*   Manhattan distances, [104](#chapter3.xhtml#p104)–[105](#chapter3.xhtml#p104)
*   Mapping, [115](#chapter4.xhtml#p115), [265](#chapter9.xhtml#p265)
*   Markov processes, [27](#chapter2.xhtml#p27)–[29](#chapter2.xhtml#p27) 
    *   diffusion processes, [29](#chapter2.xhtml#p29)
    *   with independent increments, [29](#chapter2.xhtml#p29)
    *   jump processes, [29](#chapter2.xhtml#p29)
    *   processes with discrete interference of events, [29](#chapter2.xhtml#p29)
*   Massive-parallel architecture accelerator, [249](#chapter9.xhtml#p249), [257](#chapter9.xhtml#p257)
*   Mathematical modeling, [6](#chapter1.xhtml#p6), [*7*](#chapter1.xhtml#p7), [115](#chapter4.xhtml#p115)
*   Matrix vectorization, [78](#chapter3.xhtml#p78), [83](#chapter3.xhtml#p83), [85](#chapter3.xhtml#p85)
*   Maximum entropy estimate (MEE) 
    *   asymptotic efficiency of maximum entropy estimates, [339](#appA.xhtml#p339)–[341](#appA.xhtml#p339)
    *   existence of implicit function, [335](#appA.xhtml#p335)–[339](#appA.xhtml#p335)
    *   statement, [333](#appA.xhtml#p333)–[335](#appA.xhtml#p333)
*   Maximum entropy estimation (*MEE*), [103](#chapter3.xhtml#p103)
*   MDE, *see* [Missing data ensemble](#index.xhtml#ieidx_524)
*   *M→D* (*Motivations–Decisions*) cycle, [2](#chapter1.xhtml#p2)–[4](#chapter1.xhtml#p2)
*   Mean trajectory, [13](#chapter1.xhtml#p13)
*   Measurement error generator (MEG), [160](#chapter5.xhtml#p160)–[161](#chapter5.xhtml#p160)
*   Measurement model (MM), [161](#chapter5.xhtml#p161)
*   *MEE*\-estimate of DDFs, [108](#chapter3.xhtml#p108)
*   Message passing, [250](#chapter9.xhtml#p250)
*   Metropolis-Hastings (MH) method, [241](#chapter8.xhtml#p241)
*   Minimum Cross-Entropy with constraints (MCEC), [87](#chapter3.xhtml#p87)
*   Missing data ensemble (MDE), [55](#chapter2.xhtml#p55), [*55*](#chapter2.xhtml#p55) 
    *   optimization algorithms 
        *   omissions in input and output data, [61](#chapter2.xhtml#p61)
        *   omissions in input data, [58](#chapter2.xhtml#p58)–[61](#chapter2.xhtml#p58)
        *   omissions in output data, [56](#chapter2.xhtml#p56)–[58](#chapter2.xhtml#p56)
    *   sampling of optimal PDFs, [61](#chapter2.xhtml#p61)–[63](#chapter2.xhtml#p61)
*   ML, *see* [Machine learning](#index.xhtml#ieidx_486)
*   Model-based distribution, [52](#chapter2.xhtml#p52)
*   Model development (MD), [260](#chapter9.xhtml#p260)
*   Model implementation (MI), [259](#chapter9.xhtml#p259), [261](#chapter9.xhtml#p261)–[264](#chapter9.xhtml#p261)
*   Model learning (ML), [259](#chapter9.xhtml#p259)–[261](#chapter9.xhtml#p259)
*   Model measurements, [8](#chapter1.xhtml#p8)
*   Model testing (MT), [259](#chapter9.xhtml#p259)
*   Model-view-controller (MVC) design, [262](#chapter9.xhtml#p262)
*   Module of continuity, [19](#chapter2.xhtml#p19)–[20](#chapter2.xhtml#p19)
*   Moment evaluator (ME), [161](#chapter5.xhtml#p161)–[162](#chapter5.xhtml#p161)
*   (Mono- or polyatomic) gas model, [163](#chapter5.xhtml#p163)
*   Monte Carlo method, [61](#chapter2.xhtml#p61), [204](#chapter7.xhtml#p204), [224](#chapter7.xhtml#p224), [237](#chapter8.xhtml#p237)
*   Monte Carlo packet iterations for global optimization, [202](#chapter7.xhtml#p202) 
    *   admissible set of general form, [213](#chapter7.xhtml#p213)–[215](#chapter7.xhtml#p213)
    *   canonical form of global optimization problem, [203](#chapter7.xhtml#p203)–[205](#chapter7.xhtml#p203)
    *   convergence of GFS algorithm, [209](#chapter7.xhtml#p209)–[213](#chapter7.xhtml#p209)
    *   experimental study of GFS algorithm, [217](#chapter7.xhtml#p217)–[223](#chapter7.xhtml#p217)
    *   idea of method and concept of solution, [205](#chapter7.xhtml#p205)–[206](#chapter7.xhtml#p205)
    *   logical structure of GFS algorithm, [215](#chapter7.xhtml#p215)–[216](#chapter7.xhtml#p215)
    *   probabilistic characteristics of random sequences, [206](#chapter7.xhtml#p206)–[209](#chapter7.xhtml#p206)
*   Monte Carlo simulations, [93](#chapter3.xhtml#p93), [107](#chapter3.xhtml#p107), [197](#chapter7.xhtml#p197), [202](#chapter7.xhtml#p202), [205](#chapter7.xhtml#p205)–[206](#chapter7.xhtml#p205)
*   MPI, [256](#chapter9.xhtml#p256)
*   Multidimensional AR method, [240](#chapter8.xhtml#p240)–[241](#chapter8.xhtml#p240)
*   Multidimensional Euclidean space, [70](#chapter3.xhtml#p70)
*   Multidimensional integrals using Monte Carlo method, [223](#chapter7.xhtml#p223)–[230](#chapter7.xhtml#p223)
*   Multidimensional sparse data, [72](#chapter3.xhtml#p72)
*   Multidimensional weight functions, [127](#chapter4.xhtml#p127)
*   Multilayer neural network, [138](#chapter4.xhtml#p138)
*   Multiplicative algorithms, [198](#chapter7.xhtml#p198) 
    *   with *P*\-active variables, [230](#chapter7.xhtml#p230)–[235](#chapter7.xhtml#p230)
*   Multi-processor computing module, [264](#chapter9.xhtml#p264)
*   Multithread execution environment, [256](#chapter9.xhtml#p256)

N

*   Naive Bayes, [268](#chapter10.xhtml#p268), [270](#chapter10.xhtml#p270)–[271](#chapter10.xhtml#p270)
*   Neural networks, [137](#chapter4.xhtml#p137)–[140](#chapter4.xhtml#p137), [275](#chapter10.xhtml#p275) 
    *   Kolmogorov theorem, [137](#chapter4.xhtml#p137)
    *   structural foundation, [137](#chapter4.xhtml#p137)
    *   universalism of, [138](#chapter4.xhtml#p138)
*   Newton interpolating polynomial, [42](#chapter2.xhtml#p42)
*   Noise arrays, [160](#chapter5.xhtml#p160)
*   Noises, [183](#chapter6.xhtml#p183)
*   Nonhereditary systems, [27](#chapter2.xhtml#p27)–[28](#chapter2.xhtml#p27)
*   Nonlinear block, [128](#chapter4.xhtml#p128)
*   Nonlinear dynamic models 
    *   with polynomial nonlinearities, [147](#chapter4.xhtml#p147)–[149](#chapter4.xhtml#p147)
    *   with power nonlinearities, [145](#chapter4.xhtml#p145)–[147](#chapter4.xhtml#p145)
*   Nonlinear equations, [199](#chapter7.xhtml#p199)
*   Nonnegative data matrix, [73](#chapter3.xhtml#p73)
*   Nonnegative orthant, [201](#chapter7.xhtml#p201)
*   Nonnegative real-valued function, [18](#chapter2.xhtml#p18)
*   Non-random variables, [239](#chapter8.xhtml#p239)
*   Normalization, [4](#chapter1.xhtml#p4), [67](#chapter3.xhtml#p67), [184](#chapter6.xhtml#p184), [297](#chapter11.xhtml#p297)
*   Normalized integral quadratic functional, [21](#chapter2.xhtml#p21)
*   NVIDIA accelerators, [218](#chapter7.xhtml#p218)

O

*   Odd-order moment functions, [25](#chapter2.xhtml#p25)
*   One-dimensional RPM, [131](#chapter4.xhtml#p131)
*   One-dimensional static object, [118](#chapter4.xhtml#p118)
*   Ontologies, [8](#chapter1.xhtml#p8)
*   OpenMP, [256](#chapter9.xhtml#p256), [265](#chapter9.xhtml#p265)
*   Operating system, [254](#chapter9.xhtml#p254)
*   Optimality conditions and algorithm, [75](#chapter3.xhtml#p75)–[77](#chapter3.xhtml#p75)
*   Optimality conditions and structure of entropy-optimal PDF, [173](#chapter5.xhtml#p173) 
    *   randomized models 
        *   of RPM-Orig class with input and output errors, [179](#chapter5.xhtml#p179)–[180](#chapter5.xhtml#p179)
        *   of RPM-Orig class with output errors, [173](#chapter5.xhtml#p173)–[175](#chapter5.xhtml#p173)
        *   of RPM-Rel class with output errors, [175](#chapter5.xhtml#p175)–[179](#chapter5.xhtml#p175)
*   Optimization principle, [12](#chapter1.xhtml#p12)
*   Order of moment function, [24](#chapter2.xhtml#p24)
*   Orthogonal polynomials, [148](#chapter4.xhtml#p148)
*   Orthonormal polynomials, [119](#chapter4.xhtml#p119)

P

*   Packet iterations, [264](#chapter9.xhtml#p264)–[266](#chapter9.xhtml#p264)
*   Parallel computing, [252](#chapter9.xhtml#p252)
*   Parallel Computing Toolbox, [223](#chapter7.xhtml#p223)
*   Parallelism, [253](#chapter9.xhtml#p253), [258](#chapter9.xhtml#p258) 
    *   by data, [264](#chapter9.xhtml#p264)
    *   oriented representation, [256](#chapter9.xhtml#p256)
*   Parameter estimation (PE), [216](#chapter7.xhtml#p216), [259](#chapter9.xhtml#p259)
*   Parameterized integral components (PICs), [182](#chapter5.xhtml#p182), [197](#chapter7.xhtml#p197)
*   Parameterized model (PM), [259](#chapter9.xhtml#p259)
*   Parametric characteristics, [8](#chapter1.xhtml#p8)
*   PCA, *see* [Principal component analysis](#index.xhtml#ieidx_623)
*   PDF, *see* [Probability density functions](#index.xhtml#ieidx_630)
*   Physical entropy, [164](#chapter5.xhtml#p164)
*   Piecewise constant functions, [21](#chapter2.xhtml#p21)
*   Point-set representation of matrix, [100](#chapter3.xhtml#p100)
*   Poisson probability distribution, [27](#chapter2.xhtml#p27)
*   Poisson processes, [27](#chapter2.xhtml#p27)
*   Polynomial-exponential functions, [121](#chapter4.xhtml#p121)
*   Polynomial-exponential-harmonic functions, [121](#chapter4.xhtml#p121)
*   Population-economy (*PE*) system, [5](#chapter1.xhtml#p5)–[6](#chapter1.xhtml#p5), [8](#chapter1.xhtml#p8)
*   Population subsystem, [5](#chapter1.xhtml#p5)
*   Powell function, [218](#chapter7.xhtml#p218)
*   Power nonlinearity, [128](#chapter4.xhtml#p128)
*   Primitives, [35](#chapter2.xhtml#p35)
*   Principal component analysis (PCA), [68](#chapter3.xhtml#p68)–[70](#chapter3.xhtml#p68), [72](#chapter3.xhtml#p72), [92](#chapter3.xhtml#p92)
*   Principal component matrix, [69](#chapter3.xhtml#p69)
*   Principal components, [69](#chapter3.xhtml#p69)
*   Probabilistic characteristics, [149](#chapter4.xhtml#p149)–[156](#chapter4.xhtml#p149) 
    *   empirical probabilistic characteristics, [150](#chapter4.xhtml#p150)–[154](#chapter4.xhtml#p150)
    *   moment characteristics of the ensemble, [154](#chapter4.xhtml#p154)–[156](#chapter4.xhtml#p154)
*   Probabilities of belonging (PO), [184](#chapter6.xhtml#p184)
*   Probability density functions (PDF), [11](#chapter1.xhtml#p11)–[13](#chapter1.xhtml#p11), [16](#chapter1.xhtml#p16), [23](#chapter2.xhtml#p23), [31](#chapter2.xhtml#p31), [58](#chapter2.xhtml#p58), [88](#chapter3.xhtml#p88)–[89](#chapter3.xhtml#p88), [113](#chapter4.xhtml#p113), [140](#chapter4.xhtml#p140), [157](#chapter5.xhtml#p157), [288](#chapter11.xhtml#p288) 
    *   entropy-optimal, [158](#chapter5.xhtml#p158)
    *   estimation problem, [158](#chapter5.xhtml#p158)
    *   optimal, [261](#chapter9.xhtml#p261)
*   Probability distribution function, [4](#chapter1.xhtml#p4), [22](#chapter2.xhtml#p22), [26](#chapter2.xhtml#p26), [164](#chapter5.xhtml#p164), [238](#chapter8.xhtml#p238)
*   Probability-theoretical relations, [22](#chapter2.xhtml#p22)
*   Probability vector, [185](#chapter6.xhtml#p185)
*   Problem-oriented data, [65](#chapter3.xhtml#p65)
*   Processes with discrete interference of events, [29](#chapter2.xhtml#p29)
*   Processing elements (PEs), [253](#chapter9.xhtml#p253)
*   Programming model, [250](#chapter9.xhtml#p250)
*   Projector matrices, [101](#chapter3.xhtml#p101)–[102](#chapter3.xhtml#p101), [105](#chapter3.xhtml#p105)–[106](#chapter3.xhtml#p105) 
    *   average, [110](#chapter3.xhtml#p110)
    *   with maximum probability, [110](#chapter3.xhtml#p110)
    *   median, [110](#chapter3.xhtml#p110)
    *   subset, [111](#chapter3.xhtml#p111)
*   Pulse code modulation (PCM), [32](#chapter2.xhtml#p32)
*   Pulse generator, [30](#chapter2.xhtml#p30)

Q

*   Quadratic block, [127](#chapter4.xhtml#p127)
*   Quadratic entropy inequalities, [85](#chapter3.xhtml#p85)
*   Quantization error, [32](#chapter2.xhtml#p32)
*   Quasi randomized parameters, [184](#chapter6.xhtml#p184)

R

*   Random coefficients for nonlinear element, [136](#chapter4.xhtml#p136)
*   Random functions, [21](#chapter2.xhtml#p21)–[29](#chapter2.xhtml#p21)
*   Random generator, [206](#chapter7.xhtml#p206)
*   Randomization approach, [197](#chapter7.xhtml#p197)
*   Randomized forecasting, [288](#chapter11.xhtml#p288)
*   Randomized forecasting of daily electrical load in power system, [294](#chapter11.xhtml#p294) 
    *   electrical load model, [295](#chapter11.xhtml#p295)–[296](#chapter11.xhtml#p295)
    *   entropy-optimal PDF, [299](#chapter11.xhtml#p299)–[301](#chapter11.xhtml#p299)
    *   learning dataset, [296](#chapter11.xhtml#p296)–[299](#chapter11.xhtml#p296)
    *   model testing, [304](#chapter11.xhtml#p304)–[305](#chapter11.xhtml#p304)
    *   randomized prediction of *N*\-daily load, [305](#chapter11.xhtml#p305)–[308](#chapter11.xhtml#p305)
    *   results of model learning, [301](#chapter11.xhtml#p301)–[304](#chapter11.xhtml#p301)
*   Randomized forecasting of thermokarst lakes area evolution, [324](#chapter11.xhtml#p324)
*   Randomized machine learning (RML), [12](#chapter1.xhtml#p12), [65](#chapter3.xhtml#p65) 
    *   algorithm, [57](#chapter2.xhtml#p57)
    *   defined, [16](#chapter1.xhtml#p16)
    *   implementation principles, [16](#chapter1.xhtml#p16)
    *   optimization principle, [16](#chapter1.xhtml#p16)
    *   *r*\-problem, [89](#chapter3.xhtml#p89)–[92](#chapter3.xhtml#p89)
    *   *s*\-problem, [89](#chapter3.xhtml#p89)
*   Randomized machine learning in dynamic regression and prediction, [285](#chapter11.xhtml#p285)–[286](#chapter11.xhtml#p285) 
    *   entropy randomized modelling and forecasting 
        *   data on state of thermokarst lakes, [314](#chapter11.xhtml#p314)–[317](#chapter11.xhtml#p314)
        *   entropy-randomized machine learning of *LDRR*, [317](#chapter11.xhtml#p317)–[321](#chapter11.xhtml#p317)
        *   randomized forecasting of thermokarst lakes area evolution, [324](#chapter11.xhtml#p324)
        *   results of training, testing and forecasting, [324](#chapter11.xhtml#p324)–[332](#chapter11.xhtml#p324)
        *   structures of randomized models of thermokarst lakes state, [311](#chapter11.xhtml#p311)–[314](#chapter11.xhtml#p311)
        *   testing procedure, data and accuracy estimates, [321](#chapter11.xhtml#p321)–[323](#chapter11.xhtml#p321)
        *   thermokarst lakes and climate change, [309](#chapter11.xhtml#p309)
        *   thermokarst lakes of Western Siberia, [309](#chapter11.xhtml#p309)–[311](#chapter11.xhtml#p309)
    *   randomized forecasting of daily electrical load in power system, [294](#chapter11.xhtml#p294) 
        *   electrical load model, [295](#chapter11.xhtml#p295)–[296](#chapter11.xhtml#p295)
        *   entropy-optimal PDF, [299](#chapter11.xhtml#p299)–[301](#chapter11.xhtml#p299)
        *   learning dataset, [296](#chapter11.xhtml#p296)–[299](#chapter11.xhtml#p296)
        *   model testing, [304](#chapter11.xhtml#p304)–[305](#chapter11.xhtml#p304)
        *   randomized prediction of *N*\-daily load, [305](#chapter11.xhtml#p305)–[308](#chapter11.xhtml#p305)
        *   results of model learning, [301](#chapter11.xhtml#p301)–[304](#chapter11.xhtml#p301)
    *   randomized model of world population dynamics, [286](#chapter11.xhtml#p286)–[289](#chapter11.xhtml#p286) 
        *   learning, [289](#chapter11.xhtml#p289)–[290](#chapter11.xhtml#p289)
        *   numerical results, [290](#chapter11.xhtml#p290)–[294](#chapter11.xhtml#p290)
    *   restoration of dynamic relationships in applications, [286](#chapter11.xhtml#p286)
*   Randomized model of world population dynamics 
    *   learning, [289](#chapter11.xhtml#p289)–[290](#chapter11.xhtml#p289)
    *   numerical results, [290](#chapter11.xhtml#p290)–[294](#chapter11.xhtml#p290)
*   Randomized models of RPM-Orig class 
    *   with input and output errors, [179](#chapter5.xhtml#p179)–[180](#chapter5.xhtml#p179)
    *   with output errors, [173](#chapter5.xhtml#p173)–[175](#chapter5.xhtml#p173)
*   Randomized models of RPM-Rel class, with output errors, [175](#chapter5.xhtml#p175)–[179](#chapter5.xhtml#p175)
*   Randomized neural networks, [137](#chapter4.xhtml#p137)–[140](#chapter4.xhtml#p137)
*   Randomized parameters, [149](#chapter4.xhtml#p149) 
    *   probabilistic characteristics, [149](#chapter4.xhtml#p149)–[150](#chapter4.xhtml#p149)
*   Randomized parametric models (RPM), [55](#chapter2.xhtml#p55), [*56*](#chapter2.xhtml#p56), [113](#chapter4.xhtml#p113), [159](#chapter5.xhtml#p159)–[160](#chapter5.xhtml#p159), [198](#chapter7.xhtml#p198), [276](#chapter10.xhtml#p276) 
    *   definition, characteristics and classification, [113](#chapter4.xhtml#p113)–[116](#chapter4.xhtml#p113)
    *   probabilistic characteristics, [149](#chapter4.xhtml#p149)–[156](#chapter4.xhtml#p149) 
        *   empirical probabilistic characteristics, [150](#chapter4.xhtml#p150)–[154](#chapter4.xhtml#p150)
        *   moment characteristics of ensemble, [154](#chapter4.xhtml#p154)–[156](#chapter4.xhtml#p154)
    *   RPM-I model, [55](#chapter2.xhtml#p55)
    *   RPM-O model, [55](#chapter2.xhtml#p55), [61](#chapter2.xhtml#p61)
    *   (single input, feedback)–ensemble output 
        *   definition and structure, [140](#chapter4.xhtml#p140)–[142](#chapter4.xhtml#p140)
        *   linear dynamic models, [142](#chapter4.xhtml#p142)–[144](#chapter4.xhtml#p142)
        *   nonlinear dynamic models with polynomial nonlinearities, [147](#chapter4.xhtml#p147)–[149](#chapter4.xhtml#p147)
        *   nonlinear dynamic models with power nonlinearities, [145](#chapter4.xhtml#p145)–[147](#chapter4.xhtml#p145)
    *   single input–ensemble output 
        *   functional description of dynamic models, [120](#chapter4.xhtml#p120)
        *   linear dynamic models, [120](#chapter4.xhtml#p120)–[125](#chapter4.xhtml#p120)
        *   nonlinear dynamic models with polynomial nonlinearities, [133](#chapter4.xhtml#p133)–[137](#chapter4.xhtml#p133)
        *   nonlinear dynamic models with power nonlinearities, [125](#chapter4.xhtml#p125)–[133](#chapter4.xhtml#p125)
        *   randomized neural networks, [137](#chapter4.xhtml#p137)–[140](#chapter4.xhtml#p137)
        *   static models, [116](#chapter4.xhtml#p116)–[120](#chapter4.xhtml#p116)
*   Randomized parametric (RPM-I) model, [58](#chapter2.xhtml#p58)–[59](#chapter2.xhtml#p58)
*   Randomized restoration method, [52](#chapter2.xhtml#p52)–[63](#chapter2.xhtml#p52) 
    *   omissions in input and output data, [61](#chapter2.xhtml#p61)
    *   optimization algorithms for MDE, [56](#chapter2.xhtml#p56)–[61](#chapter2.xhtml#p56)
    *   sampling of optimal PDFs, [61](#chapter2.xhtml#p61)–[63](#chapter2.xhtml#p61)
    *   structure, [52](#chapter2.xhtml#p52)–[56](#chapter2.xhtml#p52)
*   Random noise, [221](#chapter7.xhtml#p221)
*   Random parameters, [15](#chapter1.xhtml#p15), [142](#chapter4.xhtml#p142)
*   Random processes, [22](#chapter2.xhtml#p22) 
    *   with independent increments, [26](#chapter2.xhtml#p26)–[27](#chapter2.xhtml#p26)
*   Random projection method, [70](#chapter3.xhtml#p70)–[73](#chapter3.xhtml#p70)
*   Random projection (RP), [92](#chapter3.xhtml#p92)
*   Random projector matrices, [107](#chapter3.xhtml#p107)–[109](#chapter3.xhtml#p107)
*   Random projectors and numerical characteristics, [106](#chapter3.xhtml#p106)–[107](#chapter3.xhtml#p106)
*   Random subspace method (RSM), [274](#chapter10.xhtml#p274)
*   Random time-invariable parameters, [122](#chapter4.xhtml#p122)
*   Random vectors, [22](#chapter2.xhtml#p22) 
    *   dependent elements, [240](#chapter8.xhtml#p240)
    *   function, [22](#chapter2.xhtml#p22)
    *   independent elements, [240](#chapter8.xhtml#p240)
    *   Metropolis-Hastings (MH) method, [241](#chapter8.xhtml#p241)
    *   multidimensional AR method, [240](#chapter8.xhtml#p240)–[241](#chapter8.xhtml#p240)
*   Realization of random function, [22](#chapter2.xhtml#p22)
*   Recursive algorithms, [69](#chapter3.xhtml#p69)
*   Regional state indicators, [**53**](#chapter2.xhtml#p53)
*   Regularities of internal processes, [7](#chapter1.xhtml#p7)
*   Relative information error, [91](#chapter3.xhtml#p91)
*   Relative nonnegative parameters, [150](#chapter4.xhtml#p150)
*   Reproduction flow, [287](#chapter11.xhtml#p287)
*   Resettlement function, [4](#chapter1.xhtml#p4)
*   Residue matrix, [69](#chapter3.xhtml#p69)
*   Resource set, [165](#chapter5.xhtml#p165)
*   Restoration methods for missing data, [40](#chapter2.xhtml#p40) 
    *   auxiliary dynamic models, [43](#chapter2.xhtml#p43)–[45](#chapter2.xhtml#p43)
    *   interpolation, [40](#chapter2.xhtml#p40)–[43](#chapter2.xhtml#p40)
    *   randomized restoration method, [52](#chapter2.xhtml#p52)–[63](#chapter2.xhtml#p52)
    *   spatial entropy decomposition, [45](#chapter2.xhtml#p45)–[52](#chapter2.xhtml#p45)
*   RML, *see* [Randomized machine learning](#index.xhtml#ieidx_665)
*   Root-mean-square error (RMSE), [293](#chapter11.xhtml#p293)
*   Root mean square (RMS), [110](#chapter3.xhtml#p110)
*   Rosenbrock function, [218](#chapter7.xhtml#p218)
*   RPM-CauRand model, [198](#chapter7.xhtml#p198)
*   RPM-Orig models, [150](#chapter4.xhtml#p150), [159](#chapter5.xhtml#p159)–[160](#chapter5.xhtml#p159) 
    *   with input and output errors, [182](#chapter5.xhtml#p182)
    *   output, [166](#chapter5.xhtml#p166)
    *   with output errors, [180](#chapter5.xhtml#p180)–[181](#chapter5.xhtml#p180)
*   RPM-QuaRand models, [184](#chapter6.xhtml#p184)–[187](#chapter6.xhtml#p184), [201](#chapter7.xhtml#p201)
*   RPM-Rel model, [150](#chapter4.xhtml#p150), [159](#chapter5.xhtml#p159)–[160](#chapter5.xhtml#p159), [167](#chapter5.xhtml#p167), [169](#chapter5.xhtml#p169), [198](#chapter7.xhtml#p198) 
    *   with output errors, [181](#chapter5.xhtml#p181)–[182](#chapter5.xhtml#p181)
*   RPMs with the original parameters (RPM-Orig), [198](#chapter7.xhtml#p198)

S

*   Sample, [22](#chapter2.xhtml#p22)
*   Sampling procedure, [305](#chapter11.xhtml#p305)
*   Scalar functions, [78](#chapter3.xhtml#p78)
*   Scalar functions of matrices, [78](#chapter3.xhtml#p78)
*   Second-order differential equation, [14](#chapter1.xhtml#p14)
*   Second-order dynamic regression, [295](#chapter11.xhtml#p295)–[296](#chapter11.xhtml#p295)
*   Second-order system, [15](#chapter1.xhtml#p15)
*   Self-testing, [305](#chapter11.xhtml#p305)
*   Shannon, C., [16](#chapter1.xhtml#p16)
*   Shared memory, [250](#chapter9.xhtml#p250)
*   Shekel function, [217](#chapter7.xhtml#p217)
*   Sigmoidal activation function, [138](#chapter4.xhtml#p138)
*   Simultaneous multi-threading (SMT), [253](#chapter9.xhtml#p253)
*   (Single input, feedback)–ensemble output 
    *   definition and structure, [140](#chapter4.xhtml#p140)–[142](#chapter4.xhtml#p140)
    *   linear dynamic models, [142](#chapter4.xhtml#p142)–[144](#chapter4.xhtml#p142)
    *   nonlinear dynamic models with polynomial nonlinearities, [147](#chapter4.xhtml#p147)–[149](#chapter4.xhtml#p147)
    *   nonlinear dynamic models with power nonlinearities, [145](#chapter4.xhtml#p145)–[147](#chapter4.xhtml#p145)
*   Single input–ensemble output 
    *   functional description of dynamic models, [120](#chapter4.xhtml#p120)
    *   linear dynamic models, [120](#chapter4.xhtml#p120)–[125](#chapter4.xhtml#p120)
    *   nonlinear dynamic models with polynomial nonlinearities, [133](#chapter4.xhtml#p133)–[137](#chapter4.xhtml#p133)
    *   nonlinear dynamic models with power nonlinearities, [125](#chapter4.xhtml#p125)–[133](#chapter4.xhtml#p125)
    *   randomized neural networks, [137](#chapter4.xhtml#p137)–[140](#chapter4.xhtml#p137)
    *   static models, [116](#chapter4.xhtml#p116)–[120](#chapter4.xhtml#p116)
*   Single-layer neural network, [*277*](#chapter10.xhtml#p277)
*   Single-layer perceptron, [272](#chapter10.xhtml#p272), [276](#chapter10.xhtml#p276)
*   Situation assessment, [5](#chapter1.xhtml#p5)
*   Smooth functions, [19](#chapter2.xhtml#p19)
*   Software development, [255](#chapter9.xhtml#p255)
*   Spatial discretization, [35](#chapter2.xhtml#p35)
*   Spatial entropy decomposition, [45](#chapter2.xhtml#p45)–[52](#chapter2.xhtml#p45)
*   Spatiotemporal state, [2](#chapter1.xhtml#p2)
*   Stacking, [274](#chapter10.xhtml#p274)–[275](#chapter10.xhtml#p274)
*   Standard Wiener process, [27](#chapter2.xhtml#p27)
*   Statistical weight, [163](#chapter5.xhtml#p163)
*   Step functions, [21](#chapter2.xhtml#p21)
*   Stirling's approximation, [164](#chapter5.xhtml#p164)
*   Stochastic continuity, [24](#chapter2.xhtml#p24)
*   Stochastic framework, [3](#chapter1.xhtml#p3)–[4](#chapter1.xhtml#p3)
*   Support vector machines (SVM), [72](#chapter3.xhtml#p72), [273](#chapter10.xhtml#p273), [275](#chapter10.xhtml#p275)
*   Symmetry axiom, [18](#chapter2.xhtml#p18)
*   Synchronization, [40](#chapter2.xhtml#p40)
*   Syntax trees, [37](#chapter2.xhtml#p37)
*   System layer, [252](#chapter9.xhtml#p252)
*   Systems “without aftereffect,” [27](#chapter2.xhtml#p27)

T

*   Tangent activation function, [138](#chapter4.xhtml#p138)
*   Taylor monomial, [118](#chapter4.xhtml#p118)
*   Taylor series, [19](#chapter2.xhtml#p19), [78](#chapter3.xhtml#p78)
*   Term entries in document, [38](#chapter2.xhtml#p38)
*   Term frequency (TF), [38](#chapter2.xhtml#p38)
*   Test data (LD), [260](#chapter9.xhtml#p260)–[261](#chapter9.xhtml#p260)
*   Text data, [36](#chapter2.xhtml#p36)–[38](#chapter2.xhtml#p36) 
    *   formatting of document, [37](#chapter2.xhtml#p37)
    *   frequency characteristics, [37](#chapter2.xhtml#p37)
    *   logical structure of document, [37](#chapter2.xhtml#p37)
    *   mutual position of words, [37](#chapter2.xhtml#p37)
    *   references to other documents, [37](#chapter2.xhtml#p37)
*   Thermodynamic system, [163](#chapter5.xhtml#p163)
*   Thread of execution, [253](#chapter9.xhtml#p253)
*   Time-varying parameters, [124](#chapter4.xhtml#p124)
*   Total energy, [35](#chapter2.xhtml#p35)
*   Total variation, [20](#chapter2.xhtml#p20)
*   Transport behavior 
    *   collective, [3](#chapter1.xhtml#p3)
    *   individual, [3](#chapter1.xhtml#p3)
*   Transport decision-making, [4](#chapter1.xhtml#p4)
*   Triangle axiom, [18](#chapter2.xhtml#p18)
*   Trigonometric function, [218](#chapter7.xhtml#p218)
*   Trip-time utilization, [4](#chapter1.xhtml#p4)
*   Truncated Lagrange function, [86](#chapter3.xhtml#p86)
*   Two-dimensional array, [113](#chapter4.xhtml#p113)
*   Two-dimensional entropy-optimal PDF, [*283*](#chapter10.xhtml#p283)
*   Two-dimensional objects, classification, [282](#chapter10.xhtml#p282)–[285](#chapter10.xhtml#p282)

U

*   Ulam–von Neumann method, [291](#chapter11.xhtml#p291)
*   Uncertainty model, [4](#chapter1.xhtml#p4)
*   Uncorrelatedness condition, [24](#chapter2.xhtml#p24)
*   Uniform continuity, [19](#chapter2.xhtml#p19)
*   Uniformly continuous, [19](#chapter2.xhtml#p19)
*   Uniform orthogonal lattice, [224](#chapter7.xhtml#p224)
*   Uniform stochastic continuity, [24](#chapter2.xhtml#p24)
*   Unit cube, [241](#chapter8.xhtml#p241)–[242](#chapter8.xhtml#p241)
*   Universal multithread architecture (UMA), [257](#chapter9.xhtml#p257)
*   Universal multithreaded architecture, [255](#chapter9.xhtml#p255)–[258](#chapter9.xhtml#p255)
*   User layer, [252](#chapter9.xhtml#p252)

V

*   Vector function, [117](#chapter4.xhtml#p117)
*   Vector graphical data, [35](#chapter2.xhtml#p35)
*   Vectorization, [75](#chapter3.xhtml#p75), [80](#chapter3.xhtml#p80)
*   Vector loss function, [11](#chapter1.xhtml#p11)
*   Vector randomizer (VR), [160](#chapter5.xhtml#p160)
*   Vector random process, [22](#chapter2.xhtml#p22)
*   Virtual elementary cube, [207](#chapter7.xhtml#p207)
*   Visual degradation, [73](#chapter3.xhtml#p73)
*   Volterra series, [129](#chapter4.xhtml#p129)

W

*   Western Siberia, thermokarst lake area evolution 
    *   climate change, [309](#chapter11.xhtml#p309)
    *   data on state, [314](#chapter11.xhtml#p314)–[317](#chapter11.xhtml#p314)
    *   entropy-randomized machine learning of *LDRR* 
        *   ERML algorithm, [318](#chapter11.xhtml#p318)–[321](#chapter11.xhtml#p318)
        *   formation of data sets, [317](#chapter11.xhtml#p317)–[318](#chapter11.xhtml#p317)
    *   results of training, testing and forecasting 
        *   randomized forecasting (2008–2023), [328](#chapter11.xhtml#p328)–[332](#chapter11.xhtml#p328)
        *   randomized training (1973–1997), [324](#chapter11.xhtml#p324)–[327](#chapter11.xhtml#p324)
        *   testing (1998–2007), [327](#chapter11.xhtml#p327)–[328](#chapter11.xhtml#p327)
    *   structures of randomized models, [311](#chapter11.xhtml#p311)–[314](#chapter11.xhtml#p311)
    *   testing procedure, data and accuracy estimates, [321](#chapter11.xhtml#p321)–[324](#chapter11.xhtml#p321)
    *   tools and problems, [309](#chapter11.xhtml#p309)–[311](#chapter11.xhtml#p309)
*   Wiener process, [26](#chapter2.xhtml#p26)
*   With independent increments, [29](#chapter2.xhtml#p29)