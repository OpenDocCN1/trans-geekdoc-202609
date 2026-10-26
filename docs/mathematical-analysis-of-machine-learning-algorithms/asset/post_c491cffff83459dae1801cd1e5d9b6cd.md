
## MATHEMATICAL ANALYSIS OF MACHINE LEARNING ALGORITHMS

![](img/49407831b69246276f2b471882509fb2_0_0.png)

TONG ZHANG

## Mathematical Analysis of Machine Learning Algorithms

The mathematical theory of machine learning not only explains current algorithms but can also motivate principled approaches for the future. This self-contained textbook introduces students and researchers of AI to the main mathematical techniques used to analyze machine learning algorithms, with motivations and applications. Topics covered include analysis of supervised learning algorithms in the iid setting, analysis of neural networks (e.g. neural tangent kernel and mean-field analysis), and analysis of machine learning algorithms in the sequential decision setting (e.g. online learning, bandit problems, and reinforcement learning). Students will learn the basic mathematical tools used in the theoretical analysis of these machine learning problems and how to apply them to the analysis of various concrete algorithms.

This textbook is perfect for readers who have some background knowledge of basic machine learning methods, but want to gain sufficient technical knowledge to understand research papers in theoretical machine learning.

TONG ZHANG is Chair Professor of Computer Science and Mathematics at the Hong Kong University of Science and Technology where his research focuses on machine learning, big data, and their applications. A Fellow of the IEEE, the American Statistical Association, and the Institute of Mathematical Statistics, Zhang has served as chair or area chair at major machine learning conferences such as NeurIPS, ICML, and COLT, and he has been an associate editor for several top machine learning publications including *PAMI*, *JMLR*, and *Machine Learning*.

## Mathematical Analysis of Machine Learning Algorithms

Tong Zhang

*Hong Kong University of Science and Technology*

![](img/49407831b69246276f2b471882509fb2_4_0.png)

Shaftesbury Road, Cambridge CB2 8EA, United Kingdom  
One Liberty Plaza, 20th Floor, New York, NY 10006, USA  
477 Williamstown Road, Port Melbourne, VIC 3207, Australia  
314–321, 3rd Floor, Plot 3, Splendor Forum, Jasola District Centre, New Delhi – 110025, India  
103 Penang Road, #05–06/07, Visioncrest Commercial, Singapore 238467

Cambridge University Press is part of Cambridge University Press & Assessment, a department of the University of Cambridge.

We share the University's mission to contribute to society through the pursuit of education, learning and research at the highest international levels of excellence.

www.cambridge.org  
Information on this title: www.cambridge.org/9781009098380  
DOI: 10.1017/9781009093057

© Tong Zhang 2023

This publication is in copyright. Subject to statutory exception and to the provisions of relevant collective licensing agreements, no reproduction of any part may take place without the written permission of Cambridge University Press & Assessment.

First published 2023

*A catalogue record for this publication is available from the British Library.*

*A Cataloguing-in-Publication data record for this book is available from the Library of Congress.*

ISBN 978-1-009-09838-0 Hardback

Cambridge University Press & Assessment has no responsibility for the persistence or accuracy of URLs for external or third-party internet websites referred to in this publication and does not guarantee that any content on such websites is, or will remain, accurate or appropriate.

## Contents

- Preface ........................................................ xi
- **1 Introduction** .............................................. 1
  - 1.1 Standard Model for Supervised Learning .................... 2
  - 1.2 Online Learning and Sequential Decision-Making ............ 3
  - 1.3 Computational Consideration ............................... 5
  - 1.4 Basic Concepts in Generalization Analysis .................. 5
  - 1.5 Historical and Bibliographical Remarks ..................... 7
- **2 Basic Probability Inequalities for Sums of Independent Random Variables** ................................................................ 9
  - 2.1 Normal Random Variable ..................................... 9
  - 2.2 Markov’s Inequality ........................................ 11
  - 2.3 Exponential Tail Inequality ................................ 11
  - 2.4 Sub-Gaussian Random Variable ............................... 16
  - 2.5 Hoeffding’s Inequality ..................................... 17
  - 2.6 Bennett’s Inequality ........................................ 20
  - 2.7 Bernstein’s Inequality ...................................... 22
  - 2.8 Nonidentically Distributed Random Variables ................ 23
  - 2.9 Tail Inequality for χ² ...................................... 24
  - 2.10 Historical and Bibliographical Remarks ..................... 26
  - Exercises ...................................................... 26
- **3 Uniform Convergence and Generalization Analysis** ............ 27
  - 3.1 Probabilistic Approximately Correct Learning ............... 27
  - 3.2 Analysis of PAC Learning ................................... 29
  - 3.3 Empirical Process .......................................... 33
  - 3.4 Covering Number ............................................. 36
  - 3.5 A Simple Example ............................................ 39
  - 3.6 Uniform Bernstein’s Inequality .............................. 40
  - 3.7 General Bracketing Number .................................. 45
  - 3.8 Historical and Bibliographical Remarks ..................... 47
  - Exercises ...................................................... 48
- **4 Empirical Covering Number Analysis and Symmetrization** ....... 49
  - 4.1 Metric and Empirical Covering Numbers ....................... 49
  - 4.2 Symmetrization .............................................. 51
  - 4.3 Uniform Convergence with Uniform L₁ Covering Number ......... 55
  - 4.4 Vapnik–Chervonenkis Dimension ............................. 58
  - 4.5 Uniform L₂ Covering Number Analysis ....................... 60
  - 4.6 Uniform L∞ Covering Number Analysis ....................... 61
  - 4.7 Historical and Bibliographical Remarks .................... 65
  - Exercises ...................................................... 66
- **5 Covering Number Estimates** .................................. 68
  - 5.1 Packing Number ............................................. 68
  - 5.2 Lipschitz Function in Finite Dimension .................... 69
  - 5.3 Empirical Lₚ Covering Numbers of VC Class ................. 70
  - 5.4 VC Subgraph Class .......................................... 72
  - 5.5 Convex Hull Class .......................................... 73
  - 5.6 Regularized Linear Function Classes ....................... 76
  - 5.7 Historical and Bibliographical Remarks .................... 78
  - Exercises ...................................................... 79
- **6 Rademacher Complexity and Concentration Inequalities** ....... 80
  - 6.1 Rademacher Complexity ...................................... 80
  - 6.2 Offset Rademacher Complexity ............................... 82
  - 6.3 Concentration Inequality ................................... 87
  - 6.4 Estimating Rademacher Complexity .......................... 92
  - 6.5 Local Rademacher Complexity Analysis ...................... 98
  - 6.6 Historical and Bibliographical Remarks ................... 109
  - Exercises ..................................................... 110
- **7 Algorithmic Stability Analysis** ........................... 112
  - 7.1 Algorithmic Stability .................................... 112
  - 7.2 Regularized Empirical Risk Minimization ................. 116
  - 7.3 Stochastic Gradient Descent .............................. 121
  - 7.4 Gibbs Algorithm for Nonconvex Problems ................... 124
  - 7.5 Stochastic Gradient Langevin Dynamics ................... 128
  - 7.6 Concentration of Uniformly Stable Algorithm ............. 130
  - 7.7 Historical and Bibliographical Remarks .................. 134
  - Exercises ..................................................... 135
- **8 Model Selection** ......................................... 136
  - 8.1 Model Selection Problem .................................. 136
  - 8.2 Model Selection on Validation Data ...................... 138
  - 8.3 Model Selection on Training Data ........................ 141
  - 8.4 Bayesian Model Selection and Averaging .................. 147
  - 8.5 Historical and Bibliographical Remarks .................. 148
  - Exercises ..................................................... 150
- **9 Analysis of Kernel Methods** ............................... 151
  - 9.1 Introduction to Kernel Learning ......................... 151
  - 9.2 Universal Approximation .................................. 157
  - 9.3 Generalization Analysis .................................. 161
  - 9.4 Vector-Valued Functions .................................. 166
  - 9.5 Refined Analysis: Ridge Regression ...................... 170
  - 9.6 G-Optimal Design in RKHS ................................ 175
  - 9.7 Historical and Bibliographical Remarks .................. 179
  - Exercises ..................................................... 180
- **10 Additive and Sparse Models** .............................. 182
  - 10.1 Sparse Model Combination ................................ 182
  - 10.2 L1 Regularization ...................................... 186
  - 10.3 Information Theoretic Analysis ......................... 193
  - 10.4 Boosting and Greedy Algorithms ......................... 201
  - 10.5 Sparse Recovery Analysis ................................ 207
  - 10.6 Historical and Bibliographical Remarks ................. 214
  - Exercises ..................................................... 216
- **11 Analysis of Neural Networks** .............................. 218
  - 11.1 Introduction to Neural Networks ......................... 218
  - 11.2 Function Approximation .................................. 220
  - 11.3 Random Feature Method ................................... 222
  - 11.4 Neural Tangent Kernel ................................... 225
  - 11.5 Mean-Field Formulation .................................. 230
  - 11.6 Analysis of Deep Neural Networks ....................... 236
  - 11.7 Double Descent and Benign Overfitting ................... 237
  - 11.8 Historical and Bibliographical Remarks ................. 242
  - Exercises ..................................................... 245
- **12 Lower Bounds and Minimax Analysis** ........................ 246
  - 12.1 Lower Bounds for Empirical Processes ................... 246
  - 12.2 Minimax Analysis for Statistical Estimation ............ 249
  - 12.3 Lower Bounds Using Fano's Inequality .................. 251
  - 12.4 Minimax Analysis for Least Squares Regression .......... 254
  - 12.5 Minimax Analysis for Density Estimation ................ 260
  - 12.6 Lower Bounds Using Assouad's Lemma ..................... 261
  - 12.7 Historical and Bibliographical Remarks ................. 264
  - Exercises ..................................................... 265
- **13 Probability Inequalities for Sequential Random Variables** . 267
  - 13.1 Martingale Exponential Inequalities .................... 268
  - 13.2 Self-Normalizing Vector Martingale Inequalities ........ 272
  - 13.3 Uniform Convergence .................................... 275
  - 13.4 Minimax Analysis for Sequential Estimation ............. 279
  - 13.5 Historical and Bibliographical Remarks ................ 285
  - Exercises ..................................................... 286
- **14 Basic Concepts of Online Learning** ....................... 289
  - 14.1 Online Learning Model .................................. 289
  - 14.2 Perceptron Algorithms .................................. 290
  - 14.3 Online to Batch Conversion ............................. 293
