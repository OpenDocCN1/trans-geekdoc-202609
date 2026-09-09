![](images/coverpage.jpg)

![Cover: Swarm Intelligence and Evolutionary Computation, Theory, Advances and Applications in Machine Learning and Deep Learning, written by Georgios N. Kouziokas, published by CRC Press.](images/coverpage.jpg)

First edition published 2023

by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2023 Taylor & Francis Group, LLC

*CRC Press is an imprint of Taylor & Francis Group, LLC*

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice:* Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

*Library of Congress Cataloging-in-Publication Data (applied for)*

ISBN: 978-1-032-16250-8 (hbk)

ISBN: 978-1-032-16251-5 (pbk)

ISBN: 978-1-003-24774-6 (ebk)

DOI: [10.1201/9781003247746](https://dx.doi.org/10.1201/9781003247746)

Typeset in Times New Roman

by Radiant Productions

# Preface

The application of Artificial Intelligence (AI) has been greatly developed in many scientific sectors the last years, with the development of new AI-based algorithms and optimization techniques. Swarm intelligence and evolutionary computation are generally utilized as advanced methods to solve several kinds of computational optimization problems especially when there is only a small amount of relevant information.

Swarm intelligence was inspired by studying the swarm behavior of animals in nature. The social intelligence of natural swarm behavior was suitably transformed to develop computational optimization algorithms. Swarm optimization algorithms have a stochastic nature where the swarm individuals are traversing a predefined search space while the swarm algorithm evaluates the individual and the global best fitness function values in every step so as to estimate the next positions of the individuals in the space depending also on predefined hyperparameters and conditions.

Evolutionary computational optimization was inspired by the natural biological evolution. Evolutionary algorithms produce improved optimization solutions in many kinds of optimization problems in several scientific sectors such as: engineering applications, computer science and electrical engineering problems, environmental forecasting, mechanical engineering, education, transportation, scheduling optimization, machine learning and deep learning model optimization.

Machine learning methods use training algorithms to create AI-based prediction models. According to numerous studies in the literature, swarm intelligence and evolutionary computation can be utilized with increased success in order to enhance the predictability and the generalization ability of the machine learning models.

One of the main advantages of metaheuristics in optimization problems is that they do not require gradient information and can be implemented on problems where the gradient cannot be acquired. Another advantage is that they can be applied on optimization problems where the objective or fitness function is unknown or when the objective function is not differentiable. Furthermore, metaheuristics can provide an optimal solution by using less computational power compared to other optimization algorithms.

There are several common characteristics among the metaheuristic models, such as the exploration and the exploitation processes. The exploration represents the capability of the optimization algorithm to investigate the search space globally by performing a wide search for feasible solutions, whereas exploitation represents the capability of improving the current solution by searching intensively in local regions for a better solution and it is generally performed at the last iterations of the algorithm.

The book is focused on presenting, discussing, categorizing and clarifying various aspects of swarm and evolutionary intelligence such as, boundary handling approaches, swarm topology variations, mutation, crossover and selection operators, termination conditions, hyper-parameter optimization, topology and weight optimization of machine learning and deep learning models.

The book comprises nine chapters. In addition, each chapter includes the most important modifications of the swarm and evolutionary algorithms, according to the literature, which were developed to improve their performance in several optimization problems. In [Chapter 1](#ch1.xhtml), a theoretical introduction in computational optimization is performed regarding some basic concepts such as, minimization, maximization, constrained and unconstrained optimization, convex and non-convex optimization. Also, several important computational optimization techniques are discussed, regarding gradient and non-gradient-based methods and also some important machine learning training algorithms such as, Levenberg–Marquardt algorithm, scaled conjugate gradient, RMSProp, stochastic gradient descent. Furthermore, some significant new machine learning and deep learning optimizers are discussed such as: Adam optimizer, Adagrad and Adadelta. [Chapter 2](#ch2.xhtml) is devoted to the theoretical foundation of evolutionary computation and genetic algorithm. The standard genetic algorithm and advanced aspects are discussed, such as: mutation, crossover, selection operators and stopping criteria, bringing to the reader a complete aspect of the genetic algorithm and its latest operators. Furthermore, an important evolutionary algorithm is presented: the differential evolution and its variation, chaotic differential evolution. Also, an illustrative application example is presented to help the reader understand the differential evolution process. [Chapter 3](#ch3.xhtml) presents the theoretical foundation of particle swarm optimization (PSO), the latest PSO algorithm advances, and illustrative examples. The standard bio-inspired particle swarm algorithm is explained and analyzed and some important algorithm variations such as: Quantum PSO, Chaotic PSO and mutation-based PSO algorithms. Advanced aspects and variants of particle swarm optimization are discussed, such as: swarm topologies, boundary approaches, swarm initialization techniques, stopping criteria and swarm mutation operators. Illustrative application examples are presented regarding unimodal, multimodal, convex and non-convex function approximation. [Chapter 4](#ch4.xhtml) is devoted to the most important colony-based optimization algorithms: Ant colony optimization (ACO) and Artificial Bee Colony (ABC). Furthermore, several important ant-based algorithms are discussed such as, Ant System, Ant Colony System, Rank-based Ant System, Max-min Ant System and Population-based ACO. The standard Artificial Bee Algorithm is presented and also advanced aspects are discussed, such as: ABC selection methods, and boundary handling approaches of the artificial bee agent movement in the search space. [Chapter 5](#ch5.xhtml) discusses the Cuckoo Search (CS) and the Bat Algorithm (BA). The standard Cuckoo Search based on the Lévy Flights is discussed and some important variations such as: Chaotic Cuckoo Search, Discrete Cuckoo Search and Discrete Binary Cuckoo Search. In addition, the Bat Algorithm and its variants are discussed including Chaotic Bat Algorithm, Binary Bat Algorithm, Discrete Bat Algorithm and also two recent variants: Bat Algorithm with double mutation (2020) and Self-adaptive bat algorithm (2019). [Chapter 6](#ch6.xhtml) present and explain the swarm optimization algorithms: Firefly algorithm, Harmony Search and Cat Swarm Optimization algorithm. The standard algorithms are discussed and some important variants like firefly algorithm with Lévy flights, chaotic firefly algorithm, improved harmony search, chaotic harmony search, binary discreate cat swarm optimization, improved cat swarm optimization, chaotic bat algorithm, discreate bat algorithm and binary bat algorithm. [Chapter 7](#ch7.xhtml) is devoted to the latest bio-inspired swarm algorithms such as: Grey Wolf Optimization (GWO) Algorithm (2014), Whale Optimization Algorithm (WOA) (2016) and Grasshopper Optimization Algorithm (GOA) (2017). The original algorithms are discussed and also some important recent variants including Binary Grey Wolf Optimization (2016), Grey Wolf with Lévy flight (2017), Whale Optimization with Lévy Flight (2017), Binary Whale Optimization Algorithm (2020), Improved Grasshopper Optimization Algorithm (2018) and Chaotic Grasshopper Optimization (2019). In [Chapter 8](#ch8.xhtml) machine learning optimization applications are illustrated focusing on artificial neural network optimization. A neural network can be optimized by using swarm and evolutionary optimization methods in several ways, such as: weight optimization, structure optimization, or feature selection. Illustrative real-world comparative examples are presented by using genetic algorithm, particle swarm optimization and ant colony optimization. [Chapter 9](#ch9.xhtml) is devoted to deep learning topology and weight optimization by utilizing swarm intelligence and evolutionary computation, including deep unidirectional and bi-directional long short-term memory (LSTM and Bi-LSTM) network optimization and also deep Convolutional Neural Networks (CNN) optimization. The experimental part includes deep learning optimization applications such as covid19 diagnosis from chest x-ray images.

The book presents some state-of-the-art research involving swarm intelligence and evolutionary algorithms together with their variants with pseudo-codes aiming at delivering a more robust and comprehensive knowledge of the recent advances and its applications in machine learning and deep learning.

Dr. Georgios N. Kouziokas

University of Thessaly Greece

# Chapter 1 Computational Optimization

In this chapter a theoretical introduction of computational optimization is discussed regarding minimization, maximization, constrained and unconstrained optimization, convex and non-convex optimization. Also, several important computational optimization techniques are discussed, such as: Gauss-Newton and quasi-Newton methods, gradient-based methods such as steepest descent, conjugate gradient, and also non-gradient methods such as genetic algorithm and swarm intelligence algorithms. Also, several important optimizers used in machine learning are presented such as: Levenberg–Marquardt algorithm, Scaled Conjugate Gradient, RMSProp, Stochastic Gradient Descent. Furthermore, several important and relatively new optimizers are discussed such as: Adam optimizer (2014), which is an important optimizer, frequently used in machine learning and deep learning, Adagrad (2012) and Adadelta (2012).

## Computational optimization

### Introduction

A computational optimization problem can be formulated as a minimization or maximization problem. Let us consider a computational minimization problem:

(1.1)  
min *i**m**i**z**e* *f*[*i*](*x*), (*i*\=1,2,…,*M*)  

subject to the following constraints:

(1.2)  
*h*[*i*](*x*) = *c*[*j*] ,  *f**o**r*  *j* = 1, 2, …, *J*  

(1.3)  
*g*[*k*](*x*) ≤ *d*[*k*], *f**o**r* *k* = 1, 2, …, *K*  

(1.4)  
*x* = (*x*[1],*x*[2],…,*x*[*n*])  

where, *h[j]*(*x*) = *c[j]*, for *j* = 1, 2, ..., *J* and *g[k]*(*x*) ≤ *d[k]*, for *k* = 1, 2, ..., *K* are constraints that must be satisfied. The functions *f[i]*(*x*), *h[j]*(*x*) and *g[k]*(*x*) are nonlinear in general. *h[j]*(*x*) represents the equality constraints of an optimization problem, *g[k]*(*x*) represents the inequality constraints of an optimization problem.

The vector *x* can be either continuous or discrete or mixed in a multidimensional search space. The *f[i]*(*x*) functions are nominated as objective or fitness or cost functions. When the parameter *M >* 1, then we deal with a multi-objective optimization problem. Every minimization problem can be expressed as a maximization problem by substituting *f[i]*(*x*) with −*f[i]*(*x*)*.*

When the functions *f[i]*(*x*), *h[j]*(*x*) and *g[k]*(*x*) are linear then linear programming techniques can be used. When the variables of an optimization problem take only discrete values then we have a discrete optimization problem. When the variables of an optimization problem are continuous then we have to solve a continuous optimization problem. When some variables are continuous, and some other discrete then the optimization problem is mixed. When an objective function to be minimized is convex then we have a convex optimization problem which has a globally optimal solution ([Koziel and Yang, 2011](#ch1.xhtml#ref1_9)).

## Optimization methods

### Gauss-Newton method

Gauss-Newton method can be derived from a second order Taylor expansion of the fitness function to define the search direction, expressed by the equation:

(1.5)  
*p* =  − *H*[*e*]^( − 1)*g*  

where ***H**[e]* represents the exact Hessian matrix from the second derivatives and ***g*** represents the gradient vector. The gradient vector is calculated by the equation:

(1.6)  
*g* = *J*^(*H*)(*u*[*c*](*θ*)−*u*[*m*])  

The Hessian matrix is calculated by the equation:

(1.7)  
*H* = *J*^(*H*)*J*  

where,

*   *J* = ∂*u[c]*/∂*θ* represents the Jacobian matrix with dimensions 3n × M
*   3*n* represents the number of entries in ***u**[c]*
*   *M* represents the number of unknowns in *θ*

The *i*\-th column in the Jacobian matrix is calculated by the equation:

(1.8)  
$$J\_{i} = K^{- 1}\\left\\lbrack {\\frac{\\partial K}{\\partial\\theta\_{i}}u\_{c}} \\right\\rbrack$$  

where ***K*** represents the stiffness matrix. The Gauss-Newton method converges faster than the gradient-based optimization algorithms because it utilizes second derivative information, but it has an increased computational cost because of the Jacobian matrix formation and the Hessian matrix factorization.

(1.9)  
*H*[*r*] = *H* + *γ*[*r*]*I*  

The error vector is expressed by the equation:

(1.10)  
*e* = \[*e*[1, 1]*e*[1, 2]⋅⋅*e*[1, *m*]⋅⋅*e*[*p*, 1]⋅⋅*e*[*p*, *m*]\]^(*T*)  

The update rule for the Gauss-Newton algorithm can be expressed by the following equation:

(1.11)  
*W*[*k* + 1] = *W*[*k*] − (*J*[*k*]^(*T*)*J*[*k*])^( − 1)*J*[*k*]*e*[*k*]  

### Quasi-Newton method

The Quasi-Newton method utilizes an update approximation of Hessian matrix in each iteration. The equation that calculates the inversion of the Hessian matrix is expressed by the following equation:

(1.12)  
$$H\_{k + 1}^{- 1} = H\_{k}^{- 1} + \\frac{\\left( {s\_{k}^{T}y\_{k} + y\_{k}^{T}H\_{k}^{- 1}y\_{k}} \\right)\\left( {s\_{k}s\_{k}^{T}} \\right)}{\\left( {s\_{k}^{T}y\_{k}} \\right)^{2}} - \\frac{H\_{k}^{- 1}y\_{k}s\_{k}^{T} + s\_{k}y\_{k}^{T}H\_{k}^{- 1}}{s\_{k}^{T}y\_{k}}$$  

where,

*   ***s**k* = −θ θ*k k*−1
*   ***y**k* = −***g**k **g**k*−1

The inverted Hessian can be utilized to calculate the search direction:

(1.13)  
*p*[*k*] =  − *H*[*k* + 1]^( − 1)*g*[*k*]  

## Gradient-based optimization

Let us consider a function *f*(*x*). The gradient of this function is defined by the partial derivatives vector for each of the independent variables:

(1.14)  
$$\\nabla f\\left( x \\right) \\equiv g\\left( x \\right) \\equiv \\begin{bmatrix} \\frac{\\partial f}{\\partial x\_{1}} \\\\ \\frac{\\partial f}{\\partial x\_{2}} \\\\ \\ldots \\\\ \\frac{\\partial f}{\\partial x\_{n}} \\\\ \\end{bmatrix}$$  

The gradient of a function with *n* variables is a *n*\-dimensional vector. The second derivative of a *n* dimensional function is determined by *n*² partial derivatives:

(1.15)  
$$\\frac{\\partial^{2}f}{\\partial x\_{i}\\partial x\_{i}},\\, with\\, i \\neq j\\, and\\,\\frac{\\partial^{2}f}{\\partial x\_{i}^{2}}\\, with\\, i = j$$  

The partial derivatives are expressed as:

(1.16)  
$$\\frac{\\partial f}{\\partial x\_{i}},\\frac{\\partial f}{\\partial x\_{j}},\\frac{\\partial^{2}f}{\\partial x\_{i}\\partial x\_{j}}$$  

If these partial derivatives are continuous and the *f function* is single valued, then:

(1.17)  
$$\\frac{\\partial^{2}f}{\\partial x\_{i}\\partial x\_{j}} = \\frac{\\partial^{2}f}{\\partial x\_{j}\\partial x\_{i}}$$  

Consequently, the second-order partial derivatives can be expressed by a square symmetric matrix called the *Hessian matrix*:

(1.18)  
$$H\\left( x \\right) = \\begin{bmatrix} \\frac{\\partial^{2}f}{\\partial x\_{1}^{2}} & \\frac{\\partial^{2}f}{\\partial x\_{1}\\partial x\_{2}} & \\ldots & \\frac{\\partial^{2}f}{\\partial x\_{1}\\partial x\_{N}} \\\\ \\frac{\\partial^{2}f}{\\partial x\_{2}\\partial x\_{1}} & \\frac{\\partial^{2}f}{\\partial x\_{2}^{2}} & \\ldots & \\frac{\\partial^{2}f}{\\partial x\_{2}\\partial x\_{N}} \\\\ \\ldots & \\ldots & \\ldots & \\ldots \\\\ \\frac{\\partial^{2}f}{\\partial x\_{N}\\partial x\_{1}} & \\frac{\\partial^{2}f}{\\partial x\_{N}\\partial x\_{2}} & \\ldots & \\frac{\\partial^{2}f}{\\partial x\_{N}^{2}} \\\\ \\end{bmatrix}$$  

which contains n (n + 1)/2 elements.

### Steepest or gradient descent algorithm

In the Steepest Descent Algorithm, also known as gradient Descent Algorithm proposed by Cauchy ([Cauchy, 1847](#ch1.xhtml#ref1_1)) let us consider a step size learning constant *α* (learning rate), an N-dimensional vector:

(1.19)  
*w* = \[*w*[1],…,*w*[*N*]\]^(*T*)  

The N-dimensional vector represents the parameters, and *E*(*x*, *w*) the objective function. The gradient can be calculated by the equation:

(1.20)  
$$g = \\frac{\\partial E\\left( {x,w} \\right)}{\\partial w} = \\left\\lbrack {\\frac{\\partial E}{\\partial w\_{1}}\\frac{\\partial E}{\\partial w\_{2}}\\ldots\\frac{\\partial E}{\\partial w\_{N}}} \\right\\rbrack^{T}$$  

The gradient-descent update rule of the steepest descent algorithm can be calculated from the gradient (*g*) by using the following equation:

(1.21)  
*w*[*k* + 1] = *w*[*k*] − *α**g*[*k*]  

where, *α* represents the step size learning constant.

### Conjugate gradient algorithms

The conjugate gradient method ([Fletcher, 1976](#ch1.xhtml#ref1_5)) is a modification of the steepest descent method. Steepest Descent suffers from very slow convergence. During the optimization the conjugate vectors are generating but a new vector p[k] is computed only by using the previous p[k−1] vectors, and not all the previous vectors of the conjugate set. Due to this mechanism the method requires less storage and computation.

Conjugate gradient method improves the steepest descent by developing a set of search directions as the following equation shows:

(1.22)  
*p*[*k*] =  − *g*[*k*] + *β*[*k*]*p*[*k* − 1]  

where,

*   *p[k]* represents the current direction and *p*[*k*−1] the previous direction
*   ***g**[k]* represents the current residual parameter
*   *β[k]* is given by the Polak-Ribére formula ([Polak and Ribiere, 1969](#ch1.xhtml#ref1_14)) or the Hestenes–Stiefel formula, or the Fletcher–Reeves formula:

The Hestenes–Stiefel formula ([Hestenes and Stiefel, 1952](#ch1.xhtml#ref1_7)) is given by the equation:

(1.23)  
$$\\beta\_{k}^{HS} = \\frac{g\_{k}^{T}y\_{k}}{d\_{k - 1}^{T}y\_{k}}$$  

The Fletcher–Reeves formula ([Fletcher and Reeves, 1964](#ch1.xhtml#ref1_4)) is given by the equation:

(1.24)  
$$\\beta\_{k}^{FR} = \\frac{g\_{k}^{T}g\_{k}}{g\_{k - 1}^{T}g\_{k - 1}}$$  

The Polak–Ribière formula ([Polak and Ribiere, 1969](#ch1.xhtml#ref1_14)) is given by the equation:

(1.25)  
$$\\beta\_{k}^{PR} = \\frac{g\_{k}^{T}y\_{k}}{g\_{k - 1}^{T}g\_{k - 1}}$$  

where:

(1.26)  
*y*[*k*] = *g*[*k*] − *g*[*k* − 1]  

The Conjugate gradient method can be more efficient compared to the Gauss-Newton method. The Conjugate gradient method requires less memory storage resources because of the simple vector computations.

Conjugate gradient algorithms are considered as optimization methods between the steepest descent and Newton methods. Another advantage is that there is no need to store any matrices as in the Newton method, and in the quasi-Newton methods, and also, they converge faster compared to the steepest descent method.

## Optimizers for machine learning

### Stochastic gradient descent

Stochastic gradient descent is an efficient optimization algorithm especially when the dataset is very large because of the low computational cost in each iteration. Several applications of stochastic gradient descent are studied in the literature in several scientific areas such as machine learning and signal processing ([Murphy, 2012](#ch1.xhtml#ref1_12)). Stochastic gradient descent estimates a gradient in each iteration on a randomly selected sample (mini-batch) and updates the model variable.

In machine learning the conventional gradient descent algorithm updates the weights and biases in order to minimize the selected loss function and is calculated by using the negative gradient of the loss function:

(1.27)  
*θ*[ℓ + 1] = *θ*[ℓ] − *α*∇*E*(*θ*[ℓ])  

where,

*   *ℓ* represents the iteration number
*   *α* > 0 represents the learning rate
*   *θ* represents the vector parameter,
*   *E*(*θ*) represents the loss function.

In the conventional gradient descent algorithm, the loss function gradient E(*θ*), is calculated by using the whole training set of the dataset at once, but the *stochastic* gradient descent algorithm calculates the loss function gradient and updates the parameters by using only a subset (mini-batch) of the training data at each iteration.

### Stochastic gradient descent with momentum

One disadvantage of the stochastic gradient descent algorithm is that it can oscillate in the path of the gradient descent in the direction of the optimum. The Stochastic Gradient Descent with Momentum uses a momentum parameter in the parameter update equation in order to reduce the oscillation ([Murphy, 2012](#ch1.xhtml#ref1_12)). The stochastic gradient descent with momentum update equation is expressed as:

(1.28)  
*θ*[ℓ + 1] = *θ*[ℓ] − *α*∇*E*(*θ*[ℓ]) + *γ*(*θ*[ℓ]−*θ*[ℓ − 1])  

where,

*   *γ* \[0,1) represents the momentum of the previous iteration of the gradient to the current iteration
*   *ℓ* represents the iteration number
*   *α* > 0 represents the learning rate
*   *θ* represents the vector parameter,
*   *E*(*θ*) represents the loss function.

### Levenberg–Marquardt algorithm

The Levenberg-Marquardt algorithm is considered as one of the fastest supervised back propagation algorithms ([Marquardt, 1963](#ch1.xhtml#ref1_10)). Levenberg– Marquardt algorithm is used as a technique to solve non-linear problems. Levenberg–Marquardt algorithm is a combination of the steepest descent method and the Newton algorithm. The Levenberg–Marquardt algorithm update rule is expressed by the following equation:

(1.29)  
*Δ**w* = (*J*^(*T*)*J*+*μ**I*)^( − 1)*J*^(*T*)*e*  

where,

*   ***w*** represents the weight vector
*   ***I*** represents the identity matrix
*   *μ* represents the combination coefficient
*   ***J*** represents the Jacobian matrix
*   ***e*** represents the error vector

The dimensions of the Jacobian matrix are (P × M) × N and the dimensions of the error vector are (P × M) × 1 and they are calculated by the following equations:

(1.30)  
$$J = \\begin{bmatrix} \\frac{\\partial e\_{1,1}}{\\partial w\_{1}} & \\frac{\\partial e\_{1,1}}{\\partial w\_{2}} & \\cdots & \\frac{\\partial e\_{1,1}}{\\partial w\_{N}} \\\\ \\frac{\\partial e\_{1,2}}{\\partial w\_{1}} & \\frac{\\partial e\_{1,2}}{\\partial w\_{2}} & \\cdots & \\frac{\\partial e\_{1,2}}{\\partial w\_{N}} \\\\ \\cdots & \\cdots & \\cdots & \\cdots \\\\ \\frac{\\partial e\_{1,M}}{\\partial w\_{1}} & \\frac{\\partial e\_{1,M}}{\\partial w\_{2}} & \\cdots & \\frac{\\partial e\_{1,M}}{\\partial w\_{N}} \\\\ \\cdots & \\cdots & \\cdots & \\cdots \\\\ \\frac{\\partial e\_{P,1}}{\\partial w\_{1}} & \\frac{\\partial e\_{P,1}}{\\partial w\_{2}} & \\cdots & \\frac{\\partial e\_{P,1}}{\\partial w\_{N}} \\\\ \\frac{\\partial e\_{P,2}}{\\partial w\_{1}} & \\frac{\\partial e\_{P,2}}{\\partial w\_{2}} & \\cdots & \\frac{\\partial e\_{P,2}}{\\partial w\_{N}} \\\\ \\cdots & \\cdots & \\cdots & \\cdots \\\\ \\frac{\\partial e\_{P,M}}{\\partial w\_{1}} & \\frac{\\partial e\_{P,M}}{\\partial w\_{2}} & \\cdots & \\frac{\\partial e\_{P,M}}{\\partial w\_{N}} \\\\ \\end{bmatrix}$$  

(1.31)  
$$e = \\begin{bmatrix} e\_{1,1} \\\\ e\_{1,2} \\\\ \\cdots \\\\ e\_{1,M} \\\\ \\cdots \\\\ e\_{P,1} \\\\ e\_{P,2} \\\\ \\cdots \\\\ e\_{P,M} \\\\ \\end{bmatrix}$$  

where,

*   *P* represents the number of training patterns
*   *M* represents the number of outputs
*   *N* represents the number of weights.

The error vector ***e*** is estimated by the following equation:

(1.32)  
*e*[*p*, *m*] = *d*[*p*, *m*] − *o*[*p*, *m*]  

where,

*   *d[p,m]* represents the desired (real) output
*   *o[p,m]* represents the output vector
*   *m* represents the neural network outputs
*   *p* represents the training patterns.

During the algorithm process, the Jacobian matrix ***J*** is estimated and stored and then the multiplications of the Jacobian matrix are calculated to update the weights by using the equation (1.29). For large sized problems, there is a memory storage limitation problem for the Jacobian matrix ***J***.

[Wilamowski and Yu (2010](#ch1.xhtml#ref1_16)), proposed an improved computation method for Levenberg–Marquardt used to optimize the neural network training process, where the gradient vector and Quasi-Hessian matrix are calculated without using the Jacobian matrix multiplication, as shown below.

The sum of squared errors (SSE) is utilized to evaluate the training process as expressed with the equation:

(1.33)  
$$E\\left( w \\right) = \\frac{1}{2}{\\sum\\limits\_{p = 1}^{P}{\\sum\\limits\_{m = 1}^{M}e\_{p,m}^{2}}}$$  

where *e[p]*[,*m*] represents the error of output *m* under a training pattern *p*, defined by the equation (1.32).

The Hessian matrix ***H*** with dimensions *N* × *N* is expressed by the following:

(1.34)  
$$H = \\begin{bmatrix} \\frac{\\partial^{2}E}{\\partial w\_{1}^{2}} & \\frac{\\partial^{2}E}{\\partial w\_{1}\\partial w\_{2}} & \\cdots & \\frac{\\partial^{2}E}{\\partial w\_{1}\\partial w\_{N}} \\\\ \\frac{\\partial^{2}E}{\\partial w\_{2}\\partial w\_{1}} & \\frac{\\partial^{2}E}{\\partial w\_{2}^{2}} & \\cdots & \\frac{\\partial^{2}E}{\\partial w\_{2}\\partial w\_{N}} \\\\ \\cdots & \\cdots & \\cdots & \\cdots \\\\ \\frac{\\partial^{2}E}{\\partial w\_{N}\\partial w\_{1}} & \\frac{\\partial^{2}E}{\\partial w\_{N}\\partial w\_{2}} & \\cdots & \\frac{\\partial^{2}E}{\\partial w\_{N}^{2}} \\\\ \\end{bmatrix}$$  

where *N* represents the number of weights.

By combining the two previously mentioned equations the Hessian matrix ***H*** can be calculated by the following equation:

(1.35)  
$$\\frac{\\partial^{2}E}{\\partial w\_{i}\\partial w\_{j}} = {\\sum\\limits\_{p = 1}^{P}{\\sum\\limits\_{m = 1}^{M}\\left( {\\frac{\\partial e\_{p,m}}{\\partial w\_{i}}\\frac{\\partial e\_{p,m}}{\\partial w\_{j}} + \\frac{\\partial^{2}e\_{p,m}}{\\partial w\_{i}\\partial w\_{j}}e\_{p,m}} \\right)}}$$  

where *i* and *j* represent the weight indexes.

The previous equation of Levenberg–Marquardt algorithm can be approximated ([Hagan and Menhaj, 1994](#ch1.xhtml#ref1_6); [Peng et al., 2008](#ch1.xhtml#ref1_13)) as:

(1.36)  
$$\\frac{\\partial^{2}E}{\\partial w\_{i}\\partial w\_{j}} \\approx {\\sum\\limits\_{p = 1}^{P}{\\sum\\limits\_{m = 1}^{M}\\left( {\\frac{\\partial e\_{p,m}}{\\partial w\_{i}}\\frac{\\partial e\_{p,m}}{\\partial w\_{j}}} \\right)}} = q\_{ij}$$  

where *q[ij]* represents the quasi-Hessian matrix element with a row *i* and a column *j*.

By combining the previous equation with equations (1.30) and (1.31), the quasi-Hessian matrix ***Q*** can be estimated by using the Hessian matrix with the following equation:

(1.37)  
*H* ≈ *Q* = *J*^(*T*)*J*  

The gradient vector ***g*** can be calculated by the equation:

(1.38)  
$$g = \\left\\lbrack {\\frac{\\partial E}{\\partial w\_{1}}\\frac{\\partial E}{\\partial w\_{2}}\\cdots\\frac{\\partial E}{\\partial w\_{N}}} \\right\\rbrack^{T}$$  

Each element of the gradient vector g can be estimated by the equation:

(1.39)  
$$g\_{i} = \\frac{\\partial E}{\\partial w\_{i}} = {\\sum\\limits\_{p = 1}^{P}{\\sum\\limits\_{m = 1}^{M}\\left( {\\frac{\\partial e\_{p,m}}{\\partial w\_{i}}e\_{p,m}} \\right)}}$$  

Consequently, the gradient vector ***g*** can be expressed by using the Jacobian matrix ***J*** according to the equation:

(1.40)  
*g* = *J*^(*T*)*e*  

The Levenberg–Marquardt algorithm update rule can be expressed by the following equation:

(1.41)  
*Δ**w* = (*Q*+*μ**I*)^( − 1)*g*  

[Wilamowski and Yu (2010](#ch1.xhtml#ref1_16)), showed that the last equation produces the same results with the initial equation (1.29) of the Levenberg–Marquardt algorithm. The difference in the proposed method is that the quasi-Hessian matrix and the gradient vector are estimated directly without calculating and storing the Jacobian matrix as in equations (1.30) and (1.31).

The authors also proposed an improved computation of the quasi-Hessian matrix by introducing a quasi-Hessian submatrix *q[pm]*. The quasi-Hessian matrix Q can be estimated as the sum of all the submatrices *q[pm]*, with the following equation:

(1.42)  
$$Q = {\\sum\\limits\_{p = 1}^{P}{\\sum\\limits\_{m = 1}^{M}q\_{p,m}}}$$  

Furthermore, [Wilamowski and Yu (2010](#ch1.xhtml#ref1_16)), proposed an improved calculation of the gradient vector by introducing a Gradient sub vector *η[pm]* with dimensions: *N* × 1. The gradient vector *g* can be estimated as the sum of all the gradient sub vectors *η[pm]* with the following equation:

(1.43)  
$$g = {\\sum\\limits\_{p = 1}^{P}{\\sum\\limits\_{m = 1}^{M}\\eta\_{p,m}}}$$  

where *η[pm]* is calculated by the following equation:

(1.44)  
$$\\eta\_{pm} = \\left\\lbrack \\begin{array}{l} {\\frac{\\partial e\_{p,m}}{\\partial\_{w\_{1}}}e\_{pm}} \\\\ {\\frac{\\partial e\_{p,m}}{\\partial\_{w\_{2}}}e\_{pm}} \\\\ \\cdots \\\\ {\\frac{\\partial e\_{p,m}}{\\partial\_{w\_{N}}}e\_{p,m}} \\\\ \\end{array} \\right\\rbrack = \\left\\lbrack \\begin{array}{l} \\frac{\\partial e\_{p,m}}{\\partial\_{w\_{1}}} \\\\ \\frac{\\partial e\_{p,m}}{\\partial\_{w\_{2}}} \\\\ \\cdots \\\\ \\frac{\\partial e\_{p,m}}{\\partial\_{w\_{N}}} \\\\ \\end{array} \\right\\rbrack \\times e\_{p,m}$$  

### Scaled conjugate gradient algorithm

A Scaled Conjugate Gradient Algorithm was proposed in 1993 to deal with large-scale optimization problems in a more effective way (Moller, 1993). The Scaled Conjugate Gradient (SCG) algorithm is used as an optimizer in the neural network training process which requires less memory compared to other optimizers such as Levenberg Marquardt and the Bayesian Regularization (BR) algorithms ([Møller, 1993](#ch1.xhtml#ref1_11)). Scaled Conjugate Gradient Algorithm uses second order information in neural network training, and has low memory requirements because of the reduced complexity of the gradient calculations ([Møller, 1993](#ch1.xhtml#ref1_11)).

The steps of the SCG algorithm are summarized below ([Møller, 1993](#ch1.xhtml#ref1_11)):

1.  Choose the initial weight vector, and set the values of scalars *σ, λ*[1], and $\\overline{\\lambda\_{k}}.$
    
    Set the initial solution *p*[1], and the direction of the steepest descent *r*[1], equal to the estimated error surface gradient: *p*[1] = *r*[1] = – ∇*f*(*x*[1]) and *k =* 1.
    
    Set *success = true*.
    
2.  If *success = true*, then calculate the second order information, $\\overline{k\_{k}}:$
    
    (1.45)  
    $$\\sigma\_{k} = \\frac{\\sigma}{\\left| p\_{k} \\right|}$$  
    
    (1.46)  
    $${\\overline{s}}\_{k} = \\frac{\\Delta f\\left( {x\_{k} + \\sigma\_{k}p\_{k}} \\right) - \\Delta f\\left( x\_{k} \\right)}{\\sigma\_{k}}$$  
    
    (1.47)  
    $$\\delta\_{k} = p\_{k}^{T}{\\overline{s}}\_{k}$$  
    
3.  Scale *δ[k]*:
    
    (1.48)  
    $$\\delta\_{k} = \\delta\_{k} + \\left( {\\lambda\_{k} - {\\overline{\\lambda}}\_{k}} \\right)\\left| p\_{k} \\right|^{2}$$  
    
4.  If *δ[k]* ≤ 0, then make the Hessian matrix positive definite:
    
    (1.49)  
    $${\\overline{\\lambda}}\_{k} = 2\\left( {\\lambda\_{k} - \\frac{\\delta\_{k}}{\\left| p\_{k} \\right|^{2}}} \\right)$$  
    
    (1.50)  
    *δ*[*k*] =  − *δ*[*k*] + *λ*[*k*]|*p*[*k*]|²  
    
    (1.51)  
    $$\\lambda\_{k} = {\\overline{\\lambda}}\_{k}$$  
    
5.  Estimate the *μ[k]* step size:
    
    (1.52)  
    *μ*[*k*] = *p*[*k*]^(*T*)*r*[*k*]  
    
    (1.53)  
    $$\\alpha\_{k =}\\frac{\\mu\_{k}}{\\delta\_{k}}$$  
    
6.  Estimate the Δ[*k*] comparison parameter:
    
    (1.54)  
    $$\\Delta\_{k} = \\frac{2\\delta\_{k}\\left( {f\\left( x\_{k} \\right) - f\\left( {x\_{k} + \\alpha\_{k}p\_{k}} \\right)} \\right)}{\\mu\_{x}^{2}}$$  
    
7.  If Δ[*k*] ≥ 0, then a successful reduction in error can be made:
    
    Update the weight vectors, *x*[*k*+1], and the steepest descent direction, *r*[*k*+1]. $\\overline{\\lambda\_{k}}$ = 0, *success = True*
    
    If *k mod N =* 0 then restart the algorithm
    
    (1.55)  
    *p*[*k* + 1] = *r*[*k* + 1]  
    
    else, create a new conjugate direction:
    
    (1.56)  
    $$\\beta\_{k} = \\frac{\\left| r\_{k + 1} \\right|^{2} - r\_{k + 1}^{T}r\_{k}}{\\mu\_{k}}$$  
    
    (1.57)  
    *p*[*k* + 1] = *r*[*k* + 1] + *β*[*k*]*p*[*k*]  
    
    If Δ[*k*] ≥ 0.75 then reduce the scale parameter *λ[k]* = (1/4)*λ[k]*, else $\\overline{\\lambda\_{k}}$ = *λ[κ]*, success = false
    
8.  If Δ[*k*] < 0.25, then increase the scale parameter
    
    (1.58)  
    *λ*[*k*] = *λ*[*k*] + (*δ*[*k*](1−*Δ*[*k*])/|*p*[*k*]|²)  
    
9.  If the steepest descent direction is *r[k]* ≠ 0, then set *k* = *k*+1 and go to step 2. Else, terminate optimization and return *x*[*k*+1] as the desired minimum.

### Adagrad

The Adagrad is a gradient-based optimization algorithm which adjusts the learning rate for each parameter ([Dean et al., 2012](#ch1.xhtml#ref1_2)). Adagrad implements a different learning rate for each parameter in a time step. Let *g[i]^t* represent the gradient at a time step (iteration) *t*. Then for the steps (iterations) 0,1,*…, t−*1 the corresponding gradients are g [i]⁰, g[i] ¹,…,g[i] ^s. The sum of squares *G* of the gradients is calculated by the equation:

(1.59)  
*G* = (*g*[*i*]⁰)² + (*g*[*i*]¹)² + ⋯ + (*g*[*i*]^(*t* − 1))²  

The update rule in Adagrad adjusts the global learning rate at each time step for every parameter from the past gradients based on the equation:

(1.60)  
$$x\_{i} = x\_{i} - \\frac{\\alpha}{G^{\\frac{1}{2}}}g\_{i}^{t}$$  

where,

*   *α* represents the global learning rate, which is adjusted for each parameter.
*   *x[i]* denotes the parameter

Adagrad algorithm improves the robustness of SGD and can be applied with success on large-scale datasets for training neural networks ([Dean et al., 2012](#ch1.xhtml#ref1_2); [Duchi et al., 2011](#ch1.xhtml#ref1_3)).

### RMSProp

The stochastic gradient descent with momentum implements a single learning rate factor for all parameters. Several optimization algorithms use different learning rates for every parameter automatically adapting the loss function in order to improve training. In a similar way, RMSProp (Initials from root mean square propagation) implements a moving average of the squares of the parameter gradients ([Riedmiller and Braun, 1993](#ch1.xhtml#ref1_15)):

(1.61)  
*v*[ℓ] = *β*[2]*v*[ℓ − 1] + (1−*β*[2])\[∇*E*(*θ*[ℓ])\]²  

where *β*[2] represents the decay rate of the moving average.

The RMSProp algorithm implements the moving average in the updates rule for each parameter according to the equation,

(1.62)  
$$\\theta\_{\\ell + 1} = \\theta\_{\\ell} - \\frac{\\alpha\\nabla E\\left( \\theta\_{\\ell} \\right)}{\\sqrt{v\_{\\ell}} + \\in}$$  

where,

*   *ε* is a small constant in order to avoid division by zero.

The RMSProp algorithm decreases the learning rates when the parameters have large gradients and increases the learning rates when the parameters have small gradients.

### Adadelta

[Zeiler (2012](#ch1.xhtml#ref1_17)), proposed the Adadelta algorithm, in order to improve the two drawbacks of the Adagrad optimizer: the continual decay of the individual learning rates during training, and the need for choosing a learning rate globally. In the Adagrad optimizer the squared gradients for every iteration are accumulated and consequently, the learning rate is shrinking on every dimension and finally becomes very small. In order to deal with these problems, the proposed main update rule for the Adadelta algorithm is expressed by the following equation ([Zeiler, 2012](#ch1.xhtml#ref1_17)):

(1.63)  
$$x\_{i} = x\_{i} - \\frac{RMS\\left\\lbrack {\\Delta x\_{i}} \\right\\rbrack^{t - 1}}{RMS\\left\\lbrack g\_{i} \\right\\rbrack^{t}}g\_{i}^{t}$$  

where,

*   *RMS x*\[∆ \]^(*t*−1) represents the root-mean-square updates of *x*.
*   t represents the time step.

### Adam optimizer

Adam optimizer is an algorithm that uses an adaptive learning rate ([Kingma and Ba, 2014](#ch1.xhtml#ref1_8)). Adam optimizer has been applied in several deep learning techniques. During the algorithm process it finds single adaptive learning rates for the individual parameters. The algorithm name is derived by the adaptive moment calculation process of the algorithm. The first and second moments are the mean and the variance, accordingly. Adam optimizer implements exponentially moving averages for moment calculation in each mini batch for every iteration. The update rules for Adam optimizer gradient moving averages and the squared gradient accordingly, are expressed by the following equations:

(1.64)  
*m*[*t*] = *β*[1]*m*[*t* − 1] + (1−*β*[1])*g*[*t*]  

(1.65)  
*v*[*t*] = *β*[2]*v*[*t* − 1] + (1−*β*[2])*g*[*t*]²  

where,

*   *m* and *v* are the moving averages of the gradient and the squared gradient accordingly.
*   *g* represents the gradient in the current batch
*   *t* represents the number of iterations
*   *β*[1] and *β*[2] represent the hyper-parameters of the algorithm regarding the gradient and the squared gradient accordingly.

The Bias-corrected calculators for the first and second moments are given by the following equations:

(1.66)  
$${\\hat{m}}\_{t} = \\frac{m\_{t}}{1 - \\beta\_{1}^{t}}$$  

(1.67)  
$${\\hat{v}}\_{t} = \\frac{v\_{t}}{1 - \\beta\_{2}^{t}}$$  

At the final stage of the algorithm the moving averages are scaled to the individual learning rates for every parameter and the weight update is computed by the following equation:

(1.68)  
$$w\_{t} = w\_{t - 1} - \\alpha\\frac{{\\hat{m}}\_{t}}{\\sqrt{{\\hat{v}}\_{t}} + \\text{є}}$$  

where,

*   *w* represents weight of every model.
*   *α* represents learning rate.
*   *t* represents the number of the iteration.
*   *ε* represents a parameter used to prevent division by zero.

## Non-gradient methods

The gradient-based algorithms are efficient in several optimization problems: convex problems, non-linearly constrained problems, but the most gradient-based algorithms have problems in optimizing discontinuous, multi-modal, mixed discrete-continuous functions. Also, gradient-based algorithms have problems in multiple local minima, or when an objective function is non-differentiable.

Several gradient-free or non-gradient methods are based on the natural behavior of animals or insects or use heuristic methods. These methods include: genetic algorithms, evolution strategies, heuristic methods and several kinds of swarm intelligence methods that will be discussed in this book such as: Particle swarm optimization, Firefly algorithm, Harmony search, Cat swarm optimization, Grey Wolf Optimization Algorithm, Whale Optimization, Grasshopper Optimization, Ant colony optimization and Artificial Bee Colony, Cuckoo search and Bat algorithm.

## References

*   [Cauchy, A.](#ch1.xhtml#R_ref1_1) (1847). Méthode générale pour la résolution des systemes d’équations simultanées. Comp. Rend. Sci. Paris, 25(1847): 536–538.
*   [Dean, J., Corrado, G., Monga, R., Chen, K., Devin, M. et al.](#ch1.xhtml#R_ref1_2) (2012). Large scale distributed deep networks. pp. 1232–1240. In: Conf. on Neural Information Processing Systems (NeurIPS).
*   [Duchi, J., Hazan, E. and Singer, Y.](#ch1.xhtml#R_ref1_3) (2011). Adaptive subgradient methods for online learning and stochastic optimization. Journal of Machine Learning Research, 12(7).
*   [Fletcher, R. and Reeves, C. M.](#ch1.xhtml#R_ref1_4) (1964). Function minimization by conjugate gradients. The Computer Journal, 7(2): 149–154.
*   [Fletcher, R.](#ch1.xhtml#R_ref1_5) (1976). Conjugate gradient methods for indefinite systems. pp. 73–89. In: Numerical Analysis. Springer, Berlin, Heidelberg.
*   [Hagan, M. T. and Menhaj, M. B.](#ch1.xhtml#R_ref1_6) (1994). Training feedforward networks with the Marquardt algorithm. IEEE Transactions on Neural Networks, 5(6): 989–993.
*   [Hestenes, M. R. and Stiefel, E.](#ch1.xhtml#R_ref1_7) (1952). Methods of Conjugate Gradients for Solving Linear Systems (Vol. 49, No. 1). Washington, DC: NBS.
*   [Kingma, D. P. and Ba, J.](#ch1.xhtml#R_ref1_8) (2014). Adam: A method for stochastic optimization. arXiv preprint arXiv:1412.6980.
*   [Koziel, S. and Yang, X. S.](#ch1.xhtml#R_ref1_9) (eds.). (2011). Computational Optimization, Methods and Algorithms (Vol. 356). Springer.
*   [Marquardt, D. W.](#ch1.xhtml#R_ref1_10) (1963). An algorithm for least-squares estimation of nonlinear parameters. Journal of the Society for Industrial and Applied Mathematics, 11: 431–441.
*   [Møller, M. F.](#ch1.xhtml#R_ref1_11) (1993). A scaled conjugate gradient algorithm for fast supervised learning. Neural Networks, 6(4): 525–533.
*   [Murphy, K. P.](#ch1.xhtml#R_ref1_12) (2012). Machine Learning: A Probabilistic Perspective. MIT press.
*   [Peng, J. X., Li, K. and Irwin, G. W.](#ch1.xhtml#R_ref1_13) (2008). A new Jacobian matrix for optimal learning of single-layer neural networks. IEEE Transactions on Neural Networks, 19(1): 119–129.
*   [Polak, E. and Ribiere, G.](#ch1.xhtml#R_ref1_14) (1969). Note sur la convergence de méthodes de directions conjuguées. ESAIM: Mathematical Modelling and Numerical Analysis-Modélisation Mathématique et Analyse Numérique, 3(R1): 35–43.
*   [Riedmiller, M. and Braun, H.](#ch1.xhtml#R_ref1_15) (1993, March). A direct adaptive method for faster backpropagation learning: The RPROP algorithm. pp. 586–591. In: IEEE International Conference on Neural Networks. IEEE.
*   [Wilamowski, B. M. and Yu, H.](#ch1.xhtml#R_ref1_16) (2010). Improved computation for Levenberg–Marquardt training. IEEE Transactions on Neural Networks, 21(6): 930–937. doi:[10.1109/TNN.2010.2045657](http://doi.org/10.1109/TNN.2010.2045657).
*   [Zeiler, M. D.](#ch1.xhtml#R_ref1_17) (2012). Adadelta: an adaptive learning rate method. arXiv preprint arXiv:1212.5701.

# Chapter 2 Evolutionary Computation and Genetic Algorithm

This chapter is devoted to the theoretical foundation of evolutionary computation and genetic algorithm. The standard genetic algorithm is presented and discussed. Advanced aspects of genetic algorithm are discussed, such as: mutation, crossover and selection operators and stopping criteria, bringing to the reader a complete aspect of the genetic algorithm and its latest operators. Furthermore, an important evolutionary algorithm is presented: the differential evolution and its variation: chaotic differential evolution. Also, an illustrative application example is presented to help the reader understand the differential evolution process.

## Evolutionary strategy

Evolutionary strategy algorithm proposed to be used in technical optimization problems where there is no specific objective function and no other conventional optimization method could be applied ([Alavi and Henderson, 1981](#ch2.xhtml#ref2_1); [Rechenberg, 1965](#ch2.xhtml#ref2_20); [Schwefel, 1981](#ch2.xhtml#ref2_23)). Compared to genetic algorithm, in the evolutionary strategy there is only a mutation operator.

The main steps in the evolutionary strategy algorithm are described below ([Negnevitsky, 2005](#ch2.xhtml#ref2_19)):

1.  **Step 1:** Select the number of variables N to idealize the problem, and then define the range for every variable.
2.  **Step 2:** Choose randomly a set of these variables for the initialization of the parent population.
3.  **Step 3:** Estimate the solutions corresponding to these parent variables.
4.  **Step 4:** Produce a new (offspring) variable by adding a normally distributed random variable with zero mean and pre-selected deviation to every parent variable, which reflect the natural evolution process with smaller changes.
5.  **Step 5:** Estimate the solution related to the offspring variables.
6.  **Step 6:** Compare the solution related to the offspring variables with the one related to the parent variables. If the offspring solution is better than the parent solution, then substitute the parent population with the population of the offsprings. Otherwise, maintain the parent variables.
7.  **Step 7:** Go to the 4th step, and repeat the procedure until the termination criterion is reached, or until the maximum number of generations or a desirable value of the solution is attained.

Evolution strategies can be used to solve several kinds of optimization problems and produce improved results compared to many conventional optimization techniques ([Back, 1996](#ch2.xhtml#ref2_2); [Schwefel, 1995](#ch2.xhtml#ref2_24)). The basic difference of evolution strategy compared to the genetic algorithm is that it utilizes only mutation, while the genetic algorithm utilizes both crossover and mutation.

## Genetic algorithm

Genetic algorithm is a population-based algorithm similar to other evolutionary algorithms. The main operators of genetic algorithm are: selection, crossover, and mutation. Genetic algorithm proposed by John [Holland (1975](#ch2.xhtml#ref2_15)) in the book “Adaptation in Natural and Artificial System” which discusses the principles in natural evolution and how they can be applied on optimization problems. Genetic algorithm was used in several optimization problems such as vehicle routing problem ([Baker and Ayechew, 2003](#ch2.xhtml#ref2_3); [Berger and Barkaoui, 2004](#ch2.xhtml#ref2_5); May et al.) autonomous mobile robot path planning ([Lamini et al., 2018](#ch2.xhtml#ref2_16)), economic load dispatch (Sahay, 2018), and optimization in wireless sensor networks ([Ferentinos and Tsiligiridis, 2007](#ch2.xhtml#ref2_13); [Rodriguez et al., 2015](#ch2.xhtml#ref2_21)).

The main steps in the genetic algorithm are described below ([Negnevitsky, 2005](#ch2.xhtml#ref2_19)):

1.  **Step 1:** Idealize the problem as a chromosome problem, select the size of a chromosome population, the probability of the crossover and the mutation.
2.  **Step 2:** Determine a fitness function.
3.  **Step 3:** Generate randomly the initial chromosome population N.
4.  **Step 4:** Estimate the fitness function value of each chromosome.
5.  **Step 5:** Choose a pair of chromosomes for mating from the population. The parent chromosomes are chosen with a probability according to their fitness. The increased fit chromosomes have an increased probability for being selected for mating than the other chromosomes.
6.  **Step 6:** Create a pair of children (offspring) chromosomes by implementing crossover and mutation operators.
7.  **Step 7:** Put the new children (offspring) chromosomes in the new chromosome population.
8.  **Step 8:** Repeat Step 5 until the new population size of chromosomes is equal to the initial population size.
9.  **Step 9:** Replace the initial population of chromosomes with the new children (offspring) population.
10.  **Step 10:** Go to Step 4, and repeat until the termination criterion is met.

The algorithm includes three basic parameters:

**Selection:** A selection process of the best individuals for reproduction based on their fitness value.

**Crossover:** Mechanism of individual genetic data merging.

**Mutation:** The mutation mechanism is based on the alteration of a percentage (mutation rate) of the genes in a chromosome.

### Initialization

The genetic algorithm begins with a random population. Each chromosome has a set of parameters simulating the genes. The main scope of initialization is to sparse the positions (solutions) in the search space uniformly to increase the population diversity.

## Selection methods

The main genetic algorithm utilizes a roulette wheel method to set the probabilities to the individuals and select them for the next generation according to their fitness values. Several selection methods are presented in the next sections.

### Tournament selection

Tournament selection is the most utilized selection method for the Genetic Algorithm. In this selection, a set of ‘n’ individuals are selected from the population in a random way. The individual with the best fitness value is selected for the next stage of the genetic algorithm ([Goldberg and Deb, 1991](#ch2.xhtml#ref2_14)). The main advantages of this selection method are: less algorithm process time and easy implementation.

### Linear ranking selection

In the linear ranking selection technique ([Baker, 1985](#ch2.xhtml#ref2_4)), individuals are ranked according to their fitness value and then the rank value is assigned to each one. The best individual is the one with rank ‘N’ and the worst one with rank ‘1’. The linear selection probability is expressed by the equation:

(2.1)  
$$P\_{i} = \\frac{1}{N}\\left( {n^{-} + \\left( {n^{+} - n^{-}} \\right)\\frac{i - 1}{N - 1}} \\right);i \\in \\left\\{ {1,\\ldots,N} \\right\\}$$  

where,

*   *P[i]* represents the selection probability of the *i[th]* individual.
*   $\\frac{n^{-}}{N}$ represents the selection probability of the worst individual solution
*   $\\frac{n^{+}}{N}$ represents the selection probability of the best individual solution.

### Proportionate roulette wheel selection

When the selection probability is proportional in the roulette wheel regarding each sector of a partitioned wheel then it is called proportionate roulette wheel selection.

The proportion of individual fitness values against the total fitness values (solutions) of the population defines the probability of selection in the next generation. This consequently decides the area occupied by that individual on the wheel (Jinghui et al., 2005).

The selection probability of an individual is based on the equation:

(2.2)  
$$ps\\left( a\_{i} \\right) = \\frac{f\\left( a\_{i} \\right)}{\\sum\\limits\_{i = 1}^{n}{f\\left( a\_{j} \\right)}};j = 1,2,\\ldots,n$$  

where,

*   ‘n’ represents the size of the population.
*   *f*(*a[i]*) represents the fitness value of the individual solution.

### Exponential ranking selection

The exponential ranking selection differs from the linear ranking selection technique since the probability selection is formed exponentially. The exponent base is c, where 0 < c < 1.

(2.3)  
$$p\_{i} = \\frac{c^{N - i}}{\\sum\\limits\_{j = 1}^{N}c^{N - j}};i \\in \\left\\{ {1,\\ldots,N} \\right\\},\\, where\\, 0\\, < \\, c\\, < \\, 1$$  

where, *c* expresses the exponent base.

## Crossover (recombination) operators

The crossover operator is based on the exchange of randomized information among parent chromosomes ([Singh and Gupta, 2022](#ch2.xhtml#ref2_25)).

### Crossover operators for binary encoding

The most common crossover operators regarding binary genetic algorithms are presented in the following sections.

#### Single-point crossover

In the single-point crossover a point is randomly selected in the parent chromosomes as a crossover point. The bits on the right of the point are swapped among the parent chromosomes. The generated offsprings, have genetic information from both the parents.

#### k-point crossover

In the k-point crossover *k* points are randomly selected in the parent chromosomes as crossover points. The process is equivalent to the two single-point crossovers. The generated offsprings, have genetic information from both the parents.

#### Uniform crossover

Uniform crossover is implemented by a uniform bit combination of the parents. Each bit is selected from every parent with an equal probability.

#### Discrete crossover

Discrete crossover operator is similar to the uniform crossover regarding a random number uniformly generated, but the difference is that only one child is generated

### Crossover operators for real-coded genetic algorithms

In the following sections, several crossover operators for real-coded genetic algorithms are presented.

#### Arithmetic crossover

In this crossover operator, an arithmetic operation is utilized to generate a single offspring. The offspring is expressed by the equation:

(2.4)  
*x*[*i*] = *a**a*[*i*] + (1−*α*)*b*[*i*], *a* ∈ \[0,1\]  

where,

*   *a[i]*, *b[i]* and *x[i]* illustrate the *i*th gene for the parent *A*, the parent *B* and the offspring *X* accordingly.
*   *a* (alpha) represents a parameter.

#### Linear crossover

In the linear crossover, two of the three offsprings are chosen for the next generation. This operator is similar to the arithmetic operation. The equations that express the three offsprings are ([Wolpert and Macready, 1997](#ch2.xhtml#ref2_29)):

(2.5)  
*x*[*i*]¹ =  − 0.5*a*[*i*] + 1.5*b*[*i*]  

(2.6)  
*x*[*i*]¹ =  − 0.5*a*[*i*] + 1.5*b*[*i*]  

(2.7)  
*x*[*i*]³ = 1.5*a*[*i*] − 0.5*b*[*i*]  

#### Blend crossover

In the blend crossover operator, the offspring is produced by the two parents and for each position, the new gene of the offspring is developed by ([Eshelman and Schaffer, 1993](#ch2.xhtml#ref2_12)):

(2.8)  
*x*[*i*]¹ = *a*[*i*] − *α*(*b*[*i*]−*a*[*i*])  

(2.9)  
*x*[*i*]² = *b*[*i*] + *α*(*b*[*i*]−*a*[*i*]), *b*[*i*] > *a*[*i*]  

#### Simulated binary crossover

The simulated binary crossover ([Deb and Agrawal, 1995](#ch2.xhtml#ref2_7)) is similar to the one-point crossover. The relevant equation for calculating the parameter β is:

(2.10)  
$$\\beta = \\left\\{ \\begin{matrix} {\\left( {2u} \\right)^{\\frac{1}{\\eta\_{c} + 1}},} & {if\\, u \\leq 0.5} \\\\ {\\left( \\frac{1}{2\\left( {1 - u} \\right)} \\right)^{\\frac{1}{\\eta\_{c} + 1}},} & {otherwise} \\\\ \\end{matrix} \\right.$$  

where,

*   *a* and *b* represent the two parents.
*   *u* ∈ \[0,1) expresses a random number.
*   *η[c]* represents the distribution index.

The offsprings are calculated by the equations:

(2.11)  
*x*¹ = 0.5\[(1+*β*)*a*+(1−*β*)*b*\]  

(2.12)  
*x*² = 0.5\[(1−*β*)*a*+(1+*β*)*b*\]  

#### Three-parent crossover

In the three-parent crossover operator, only one offspring is created by three parent chromosomes.

## Mutation operators

In the next sections the most common mutation operators are examined.

### Gaussian mutation

The Gaussian mutation operator utilizes a random number generated from a Gaussian distribution. The Gaussian distribution equation is expressed by the equation:

(2.13)  
$$f\_{G{({0,\\sigma^{2}})}}\\left( \\alpha \\right) = \\frac{1}{\\sqrt{2\\pi\\sigma^{2}}}e^{\\frac{\\alpha^{2}}{2\\sigma^{2}}}$$  

where,

*   σ represents the standard deviation.
*   *σ*² represents the variance.
*   *α* represents a random number from a Gaussian distribution in the range \[0,1\].

### Cauchy mutation

The Cauchy mutation operator is based on the Cauchy distribution function to generate the random number. The one-dimensional Cauchy probability density function is expressed by the equation:

(2.14)  
$$f\\left( x \\right) = \\frac{t^{2}}{\\pi\\left( {x^{2} + t^{2}} \\right)}, - \\infty < x < \\infty$$  

where *t* is a positive variable. The Cauchy cumulative distribution function is expressed by the equation:

(2.15)  
$$F\_{t}\\left( x \\right) = \\frac{1}{2} + \\frac{1}{\\pi}\\arctan\\left( \\frac{x}{t} \\right)$$  

The shape of the Cauchy distribution is similar to Gaussian distribution, but the probability is increased in the tails.

### Diversity mutation

Diversity mutation was proposed by [Deb and Deb (2014](#ch2.xhtml#ref2_8)). Diversity mutation can improve the exploration properties of any algorithm. An exponential distribution was used:

(2.16)  
*p*(*i*) = *t**e*^( − *t**i*), *w**i**t**h* *i* ∈ \[0,*n*−1\]  

the roots of the above probability distribution are given by the equation:

(2.17)  
*t**e*^( − *n**t*) − *e*^( − *t*) − *t* + 1 = 0  

For n = 15, parameter t = 0.169, for n = 20, t = 0.136. The mutation equation according to the above c is,

(2.18)  
$$m\\left( t \\right) = \\frac{1}{t}\\log\\left( {1 - u\\left( {1 - e^{- nt}} \\right)} \\right)$$  

### Lévy flight mutation

The Lévy flight provides a random walk and the random step length is expressed by the Lévy distribution which is a heavy-tailed:

(2.19)  
*L**e**v**y* ∼ *u* = *t*^( − *λ*), 1 < *λ* ≤ 3  

The equation for Lévy flight mutation is given by ([Yang and Deb, 2010](#ch2.xhtml#ref2_32)):

(2.20)  
$$L\\left( x \\right) = 0.01 \\times \\frac{r\_{1} \\times \\sigma}{\\left| r\_{2} \\right|^{\\frac{1}{\\beta}}}\\, r\_{1},r\_{2} \\in \\left\\lbrack {0,1} \\right\\rbrack;\\beta = 1.5$$  

(2.21)  
$$\\sigma = \\left( \\frac{\\Gamma\\left( {1 + \\beta} \\right) \\times \\sin\\left( \\frac{\\pi\\beta}{2} \\right)}{\\Gamma\\left( \\frac{1 + \\beta}{2} \\right) \\times \\beta \\times 2\\left( \\frac{\\beta - 1}{2} \\right)} \\right)^{\\frac{1}{\\beta}}$$  

(2.22)  
*Γ*(*x*) = (*x*−1)!  

*   *L*(*x*) represents the Lévy distributed random number with variable size *x*,
*   α, β, γ represent random numbers.

### Power mutation

[Deep and Thakur (2007](#ch2.xhtml#ref2_9)), proposed the power mutation operator which is based on the power distribution. The distribution function of the power distribution is expressed by the equation:

(2.23)  
*f*(*x*) = *p**x*^(*p* − 1), 0 ≤ *x* ≤ 1  

The density function is expressed by the equation:

(2.24)  
*F*(*x*) = *x*^(*p*), 0 ≤ *x* ≤ 1  

where *p* represents the distribution index.

## Termination conditions

### Fitness limit

The algorithm stops if the best fitness value is less than or equal to the value preset as the fitness limit.

### Maximum number of generations

The algorithm execution stops when the iteration number reaches a predefined maximum number.

### Maximum stall time

This condition forces the genetic algorithm execution to stop when the best value of the fitness function does not change in the last predefined maximum stall time (E.g., in seconds).

### Maximum runtime

The algorithm execution stops when a predefined maximum runtime is reached (E.g., in seconds).

### Best fitness value

The algorithm execution stops when the value of the fitness function reaches a predefined best value.

## Adaptive genetic algorithm

The crossover probability *p*[c] and the mutation probability *p*[m] are very important factors in genetic algorithm. Finding the optimal values for *p*[c] and *p*[m] is important for improving the genetic algorithm convergence performance ([Dey, 2014](#ch2.xhtml#ref2_10); [Wu et al., 1998](#ch2.xhtml#ref2_30); [Wu, 2019](#ch2.xhtml#ref2_31)).

[Srinivas and Patnaik (1994](#ch2.xhtml#ref2_26)), proposed an adaptive strategy, where the crossover probability *p*[c] and the mutation probability *p*[m] are calculated adaptively by the equations:

(2.25)  
$$p\_{c} = k\_{1}\\frac{f\_{\\max} - f\_{c}}{f\_{\\max} - f},k\_{1} \\leq 1.0$$  

(2.26)  
$$p\_{c} = k\_{2}\\frac{f\_{\\max} - f\_{c}}{f\_{\\max} - f},k\_{2} \\leq 1.0$$  

with the constraints,

(2.27)  
$$p\_{c} = k\_{3},f\_{c} \\leq \\overline{\\overline{f}}$$  

(2.28)  
$$p\_{n} = k\_{4},f\_{i} \\leq \\overline{\\overline{f}}$$  

where,

*   *k*[1], *k*[2], *k*[3] and *k*[4] should be less than 1.0.
*   *p*[c] represents the crossover probability.
*   *p*[m] represents the mutation probability.
*   *p*[c] and *p*[m] are in the range 0.0 to 1.0.
*   *f*[c] represents the best fitness values of the selected individuals.
*   *f[i]* represents the fitness value of the *i*[th] chromosome with probability
*   $\\frac{p\_{m}}{f}$ represents the average fitness value.

## Differential evolution

Differential evolution is proposed as a simple and efficient heuristic algorithm in global optimization problems ([Storn, 1996](#ch2.xhtml#ref2_27); [Storn and Price, 1997](#ch2.xhtml#ref2_28)). Differential evolution algorithm (DE) is a populationbased algorithm used in optimization. Differential evolution algorithm is based on an arithmetic operator combined with evolutionary operators: mutation, crossover and selection. Differential evolution can be effective in solving non-convex optimization problems. According to the algorithm, the parameters are initialized, and then mutation, crossover, and selection are performed in every iteration.

The population of differential evolution contains *NP D*\-dimensions vectors for each generation:

(2.29)  
*X*[*i*, *g*] = (*x*[*i**l*, *g*],*x*[*i*2, *g*],...,*x*[*i**D*, *g*]), (*i*\=1,2,...,*N**P*)  

where,

*   *i* represents the index of individual
*   *g* represents the number of generations

After initialization, the basic stages of the differential evolution algorithm are: mutation, crossover, and selection ([Storn and Price, 1997](#ch2.xhtml#ref2_28)).

### Mutation

For each parameter vector *X[i,g]* in the population, a mutation vector *V[i]*,[*g*] is produced according to the following equation:

(2.30)  
*V*[*i*, *g* + 1] = *X*[*r*[1], *g*] + *F*(*X*[*r*[2], *g*]−*X*[*r*[3], *g*]); *i* = 1, 2, ..., *N**P*  

where,

*   random numbers *r*[1], *r*[2] and *r*[3] are produced with in the range of \[1, 2, …,*NP*\], and are mutually different.
*   mutation factor or scaling factor *F* \[0, 2\] is a real constant and controls the differential variation amplification.

### Crossover

Differential evolution uses a crossover operation in order to increase the diversity of the population. A trial vector is produced by recombining discretely the parent *X[i,g]* and its corresponding mutant vector *V[i,g]* using the equations:

(2.31)  
*U*[*i*, *g*], *U*[*i*, *g*] = (*u*[*i*1, *g*],*u*[*i*2, *g*],...,*u*[*i**D*, *g*])  

(2.32)  
$$u\_{ij,g} = \\left\\{ {\\begin{matrix} {v\_{ij,g},} \\\\ {x\_{ij,g},} \\\\ \\end{matrix}\\begin{matrix} {\\,\\, if\\left( {Rand\\left( j \\right) \\leq R} \\right)\\, or\\, j = Rnd\\left( i \\right)} \\\\ {otherwise} \\\\ \\end{matrix}} \\right.i = 1,2,3,...,NP;\\, j = 1,2,...,D$$  

where,

*   *Rand*(*j*) represents the *j-*th evaluation of a uniform random number generator between \[0, 1\].
*   *Rnd*(*i*) represents a randomly chosen value in the range \[1, *D*\], which is used to ensure that *U[i,g]* will select at least one vector from the *V[i,g]*. in order to help the population evolve.
*   *CR* represents the crossover factor within the range \[0, 1\], which is used to control the recombination.

### Selection

The trial vector is compared to the target vector by using greedy selection. The one with the best fitness value will be chosen for the next generation.

The selection operation is performed according to the equation:

(2.33)  
$$X\_{i,g + 1} = \\left\\{ {\\begin{matrix} U\_{i,g} \\\\ {X\_{i,g},} \\\\ \\end{matrix}\\begin{matrix} {\\,\\, if\\, U\_{i,g}\\, yields\\, better\\, fitness\\, value\\, than\\, X\_{i,g}} \\\\ {otherwise} \\\\ \\end{matrix}} \\right.i = 1,2,3,...,NP$$  

## Chaotic differential evolution

Several researchers have proposed Chaotic differential evolution algorithms to enhance the optimization ability of the original differential evolution algorithm. [Lu et al. (2011](#ch2.xhtml#ref2_17)). The performance of differential evolution is affected by the value of mutation factor *F* and the crossover factor (*CR*). The use of chaotic sequences to adapt the parameter value settings can enhance differential evolution and enhance the convergence capability of the algorithm.

[Lu et al. (2011](#ch2.xhtml#ref2_17)), proposed Tent equation to be used to adjust the values of *F* and *CR* in a dynamical way. The Tent equation is expressed by the equation:

(2.34)  
$$cx\_{i}^{k + 1} = \\left\\{ {\\begin{matrix} {2cx\_{i}^{k}} & {0 \\leq cx\_{i}^{k} \\leq 0.5} \\\\ {2\\left( {1 - cx\_{i}^{k}} \\right)} & {0.5 \\leq cx\_{i}^{k} \\leq 1} \\\\ \\end{matrix}i = 1,2,\\ldots,D;k = 1,2,\\ldots,k\_{\\max}} \\right.$$  

where,

*   *k* represents the number of the iteration
*   *k*[max] represents the maximum iteration of the chaotic sequences
*   *cx[i]^k* represents the *i*\-th chaotic parameter with values within the range \[0, 1\].

The conditions are: the initial *cx[i]*⁰ ∈ (0, 1) and *cx[i]*⁰ ∉ {1/4, 1/2, 2/3, 3/4}.

[Lu et al. (2011](#ch2.xhtml#ref2_17)), proposed the following equation for mutation factor *F* in order to improve the differential evolution efficiency:

(2.35)  
*F*⁰ ∈ (0,1), *F*⁰ ∉ {1/4,1/2,2/3,3/4}  

(2.36)  
$$F^{g + 1} = \\left\\{ {\\begin{matrix} {2F^{g}} & {0 < F^{g} < 0.5} \\\\ {2\\left( {1 - F^{g}} \\right)} & {0.5 < F^{g} < 1} \\\\ \\end{matrix}g = 1,2,\\ldots,g\_{\\max}} \\right.$$  

Similarly, [Lu et al. (2011](#ch2.xhtml#ref2_17)), proposed the following equations for crossover factor *CR* in order to improve the differential evolution efficiency:

(2.37)  
*C**R*⁰ ∈ (0,1), *C**R*⁰ ∉ {1/4,1/2,2/3,3/4}  

(2.38)  
$$CR^{g + 1}\\left\\{ {\\begin{matrix} {2CR^{g}} & {0 < CR^{g} < 0.5} \\\\ {2\\left( {1 - CR^{g}} \\right)} & {0.5 < CR^{g} < 1} \\\\ \\end{matrix}g = 1,2,\\ldots,g\_{\\max}} \\right.$$  

[Coelho and Mariani (2006](#ch2.xhtml#ref2_6)), proposed the utilization of the logistic map as a chaotic map for dynamically adapting the mutation factor *F*:

(2.39)  
*y*(*t*) = *μ* ⋅ *y*(*t*−1) ⋅ \[1−*y*(*t*−1)\]  

[dos Santos et al. (2012)](#ch2.xhtml#ref2_11), proposed a chaotic differential evolution algorithm based on Ikeda map which generates chaotic sequences in order to tune the *CR* and the *F* parameters. The Ikeda map is expressed by the equations:

(2.40)  
*X*(*k*+1) = 1 + *λ* ⋅ \[*X*(*k*)cos(*c*(*k*))−*Y*(*k*)sin(*c*(*k*)\]  

(2.41)  
*Y*(*k*+1) = *λ* ⋅ \[*X*(*k*)sin(*c*(*k*))+*Y*(*k*)cos(*c*(*k*)\]  

where,

*   *λ* is a parameter with the value 0.9
*   *c*(*k*) is expressed by the equation:

(2.42)  
$$c\\left( k \\right) = 0.4 - \\frac{6}{1 + X\\left( k \\right)^{2} + Y\\left( k \\right)^{2}}$$  

## Differential evolution example

### Ackley function approximation

#### Mathematical equation

The equation that represents the Ackley function is the following.

(2.43)  
$$f\\left( {x\_{1},\\ldots,x\_{n}} \\right) = - a \\cdot \\exp\\left( {- b\\sqrt{\\frac{1}{n}{\\sum\\limits\_{i = 1}^{n}x\_{i}^{2}}} - \\exp\\left( {\\frac{1}{n}{\\sum\\limits\_{i = 1}^{n}{\\cos\\left( {cx\_{i}} \\right)}}} \\right) + a + \\exp(1} \\right)$$  

where the a, b and c are constant values. For the experiments we set: a = 20, b = 0.2 and c = 2π. The Ackley function is continuous, non-convex, multimodal and differentiable.

### Input search space

The function is evaluated with *x[i]* \[−20, 20\], and i = 1, 2, . . . , n.

### Differential evolution parameters

Maximum Number of Iterations: 2000

Population Size: 50

Decision Variables Minimum Bound: –20

Decision Variables Maximum Bound: 20

Crossover Probability: 0.2

Lower Bound of Scaling Factor: 0.2

Upper Bound of Scaling Factor: 0.8

The optimization results illustrated in [Figure 2.1](#ch2.xhtml#fig2_1) are very good. The function minimization stops improving at about 2000 iterations.

![Figure 2.1. Ackley function approximation by using Differential Evolution.](images/fig2_1_B.jpg)

[Figure 2.1. Ackley function approximation by using Differential Evolution.](#ch2.xhtml#R_fig2_1)

## References

*   [Alavi, M. and Henderson, J. C.](#ch2.xhtml#R_ref2_1) (1981). An evolutionary strategy for implementing a decision support system. Management Science, 27(11): 1309–1323.
*   [Back, T.](#ch2.xhtml#R_ref2_2) (1996). Evolutionary Algorithms in Theory and Practice: Evolution Strategies, Evolutionary Programming, Genetic Algorithms. Oxford University Press.
*   [Baker, B. M. and Ayechew, M. A.](#ch2.xhtml#R_ref2_3) (2003). A genetic algorithm for the vehicle routing problem. Computers & Operations Research, 30(5): 787–800. doi:[https://doi.org/10.1016/S0305-0548(02)00051-5](https://doi.org/10.1016/S0305-0548\(02\)00051-5).
*   [Baker, J. E.](#ch2.xhtml#R_ref2_4) (1985, July). Adaptive selection methods for genetic algorithms. In: Proceedings of an International Conference on Genetic Algorithms and their Applications (Vol. 1).
*   [Berger, J. and Barkaoui, M.](#ch2.xhtml#R_ref2_5) (2004). A parallel hybrid genetic algorithm for the vehicle routing problem with time windows. Computers & Operations Research, 31(12): 2037–2053.
*   [Coelho, L. S. and Mariani, V. C.](#ch2.xhtml#R_ref2_6) (2006). Combining of chaotic differential evolution and quadratic programming for economic dispatch optimization with valvepoint effect. IEEE Transactions on Power Systems, 21(2): 989–996. doi:[10.1109/TPWRS.2006.873410](http://doi.org/10.1109/TPWRS.2006.873410).
*   [Deb, K. and Agrawal, R. B.](#ch2.xhtml#R_ref2_7) (1995). Simulated binary crossover for continuous search space. Complex Systems, 9(2): 115–148.
*   [Deb, K. and Deb, D.](#ch2.xhtml#R_ref2_8) (2014). Analysing mutation schemes for real-parameter genetic algorithms. International Journal of Artificial Intelligence and Soft Computing, 4(1): 1–28.
*   [Deep, K. and Thakur, M.](#ch2.xhtml#R_ref2_9) (2007). A new mutation operator for real coded genetic algorithms. Applied Mathematics and Computation, 193(1): 211–230.
*   [Dey, D. K.](#ch2.xhtml#R_ref2_10) (2014). Mathematical study of adaptive genetic algorithm (AGA) with mutation and crossover probabilities. Compusoft, 3(5): 765.
*   [dos Santos, G. S., Luvizotto, L. G. J., Mariani, V. C. and Coelho, L. d. S.](#ch2.xhtml#R_ref2_11) (2012). Least squares support vector machines with tuning based on chaotic differential evolution approach applied to the identification of a thermal process. Expert Systems with Applications, 39(5): 4805–4812. doi:[https://doi.org/10.1016/j.eswa.2011.09.137](https://doi.org/10.1016/j.eswa.2011.09.137).
*   [Eshelman, L. J. and Schaffer, J. D.](#ch2.xhtml#R_ref2_12) (1993). Real-coded genetic algorithms and intervalschemata. pp. 187–202. In: Foundations of Genetic Algorithms (Vol. 2). Elsevier.
*   [Ferentinos, K. P. and Tsiligiridis, T. A.](#ch2.xhtml#R_ref2_13) (2007). Adaptive design optimization of wireless sensor networks using genetic algorithms. Elsevier, Computer Networks, 51(4): 1031–1051.
*   [Goldberg, D. E. and Deb, K.](#ch2.xhtml#R_ref2_14) (1991). A comparative analysis of selection schemes used in genetic algorithms. pp. 69–93. In: Foundations of Genetic Algorithms (Vol. 1). Elsevier.
*   [Holland, J. H.](#ch2.xhtml#R_ref2_15) (1975). Adaptation in Natural and Artificial Systems. An Introductory Analysis with Applications to Biology, Control and Artificial Intelligence. Ann Arbor: University of Michigan Press.
*   [Lamini, C., Benhlima, S. and Elbekri, A.](#ch2.xhtml#R_ref2_16) (2018). Genetic algorithm based approach for autonomous mobile robot path planning. Procedia Computer Science, 127: 180–189.
*   [Lu, Y., Zhou, J., Qin, H., Wang, Y., Zhang, Y. et al.](#ch2.xhtml#R_ref2_17) (2011). Chaotic differential evolution methods for dynamic economic dispatch with valve-point effects. Engineering Applications of Artificial Intelligence, 24(2): 378–387. doi:[https://doi.org/10.1016/j.engappai.2010.10.014](https://doi.org/10.1016/j.engappai.2010.10.014).
*   May, A. T., Jariyavajee, C. and Polvichai, J. (2021, December). An improved genetic algorithm for vehicle routing problem with shard time windows. pp. 1–6. In 2021 International Conference on Electrical, Computer and Energy Technologies (ICECET). IEEE.
*   [Negnevitsky, M.](#ch2.xhtml#R_ref2_19) (2005). Artificial Intelligence: a Guide to Intelligent Systems. Pearson Education.
*   [Rechenberg, I.](#ch2.xhtml#R_ref2_20) (1965). Cybernetic solution path of an experimental problem. Royal Aircraft Establishment Library Translation 1122.
*   [Rodriguez, A., Falcarin, P. and Ordonez, A.](#ch2.xhtml#R_ref2_21) (2015, November). Energy optimization in wireless sensor networks based on genetic algorithms. pp. 470–474. In 2015 SAI Intelligent Systems Conference (IntelliSys). IEEE.
*   Sahay, K. B., Sonkar, A. and Kumar, A. (2018, October). Economic load dispatch using genetic algorithm optimization technique. pp. 1–5. In 2018 International Conference and Utility Exhibition on Green Energy for Sustainable Development (ICUE). IEEE.
*   [Schwefel, H. P.](#ch2.xhtml#R_ref2_23) (1981). Numerical Optimization of Computer Models. John Wiley & Sons, Inc.
*   [Schwefel, H. P.](#ch2.xhtml#R_ref2_24) (1995). Evolution and Optimum Seeking. John Wiley and Sons. New York.
*   [Singh, G. and Gupta, N.](#ch2.xhtml#R_ref2_25) (2022). A study of crossover operators in genetic algorithms. pp. 17–32. In: Frontiers in Nature-Inspired Industrial Optimization. Springer, Singapore.
*   [Srinivas, M. and Patnaik, L. M.](#ch2.xhtml#R_ref2_26) (1994). Adaptive probabilities of crossover and mutation in genetic algorithms. IEEE Transactions on Systems, Man, and Cybernetics, 24(4): 656–667.
*   [Storn, R.](#ch2.xhtml#R_ref2_27) (1996, June). On the usage of differential evolution for function optimization. pp. 519–523. In: Proceedings of North American Fuzzy Information Processing. IEEE.
*   [Storn, R. and Price, K.](#ch2.xhtml#R_ref2_28) (1997). Differential evolution—a simple and efficient heuristic for global optimization over continuous spaces. Journal of Global Optimization, 11(4): 341–359.
*   [Wolpert, D. H. and Macready, W. G.](#ch2.xhtml#R_ref2_29) (1997). No free lunch theorems for optimization. IEEE Transactions on Evolutionary Computation, 1(1): 67–82.
*   [Wu, Q. H., Cao, Y. J. and Wen, J. Y.](#ch2.xhtml#R_ref2_30) (1998). Optimal reactive power dispatch using an adaptive genetic algorithm. International Journal of Electrical Power & Energy Systems, 20(8): 563–569. doi:[https://doi.org/10.1016/S0142–0615(98)00016–7](https://doi.org/10.1016/S0142%E2%80%930615\(98\)00016%E2%80%937).
*   [Wu, X.](#ch2.xhtml#R_ref2_31) (2019, July). Research on the influence of crossover probability and mutation probability in GA-SVM Model. pp. 1–7. In: 2019 IEEE 9th International Conference on Electronics Information and Emergency Communication (ICEIEC). IEEE.
*   [Yang, X. S. and Deb, S.](#ch2.xhtml#R_ref2_32) (2010). Engineering optimisation by cuckoo search. International Journal of Mathematical Modelling and Numerical Optimisation, 1(4): 330–343.

# Chapter 3 Swarm Intelligence and Particle Swarm Optimization

This chapter is devoted to the theoretical foundation of particle swarm optimization, the latest PSO algorithm advances, neural network optimization methods and illustrative examples. The standard bio-inspired particle swarm algorithm is presented and some important variations of the PSO algorithm are explained and analyzed such as: Quantum PSO algorithm with delta potential well and harmonic oscillator, Chaotic PSO, mutation-based PSO and multi-objective PSO. Advanced aspects and variants of particle swarm optimization are discussed, such as: swarm topologies, boundary approaches, swarm initialization techniques, stopping criteria and swarm mutation operators, bringing to the reader a complete presentation of the PSO algorithm and its latest variations. Illustrative application examples are presented regarding unimodal, multimodal, convex and non-convex function approximation.

## Particle swarm optimization algorithm

The Particle Swarm Optimization (PSO) was initially proposed by Eberhart and Kennedy in 1995 ([Eberhart and Kennedy, 1995](#ch3.xhtml#ref3_17)). The PSO algorithm was inspired by studying the swarm behavior of animals in nature. The natural social intelligence techniques were suitably transformed in order to develop a computational optimization algorithm. Particle Swarm Optimization is an evolutionary algorithm with a stochastic nature where the swarm particles are traversing a predefined search space to evaluate the fitness function. Each swarm particle is characterized by its position and velocity.

 Each particle velocity is updated according to the equation ([Eberhart, 1995](#ch3.xhtml#ref3_17); [Eberhart et al., 2001](#ch3.xhtml#ref3_16)):

(3.1)  
*ν*[*i*](*t*+1) = *w**ν*[*i*](*t*) + *c*[*i*]*r*[1]\[*x̂**i**b**e**s**t*[*i*](*t*)−*x*[*i*](*t*)\] + *c*[2]*r*[2]\[*g**b**e**s**t*(*t*)−*x*[*i*](*t*)\]  

where,

> *t* represents the time
> 
> *v*[*i*](*t*) illustrates the particle velocity at time t
> 
> *v*[*i*](*t* + 1) illustrates the particle velocity at time t+1
> 
> *x*[*i*](*t*) illustrates the particle position at time t
> 
> *x*̂*ibest*[*i*](*t*) illustrates the particle individual best objective value solution as of time t
> 
> *r*[1]*, r*[2] represents random numbers uniformly distributed in the interval (0,1)
> 
> *gbest*(*t*) represents the swarm’s global best objective value solution as of time t
> 
> *c*[1] illustrates the coefficient parameter of personal learning
> 
> *c*[2] illustrates the coefficient parameter of global learning
> 
> *w* illustrates the inertia weight coefficient parameter

Also, the particle position in the next time step *t+*1 is calculated by using the following equation:

(3.2)  
*x*[*i*](*t*+1) = *x*[*i*](*t*) + *v*[*i*](*t*+1)  

The standard particle swarm optimization algorithm consists of the following basic steps:

1.  Initialization process:
    
    1.  Initialize the particle swarm population
    2.  Initialize the particle topology and positions
    3.  Initialize the particle velocities
    4.  Evaluate each particle’s fitness function and initialize global best solution
2.  Execute the following steps until the stopping criterion of the algorithm is met:
    
    1.  Set the coefficient numbers: r[1], r[2] randomly in the space (0,1)
    2.  Update the particle velocity according to eq. (1)
    3.  Update the particle position according to eq. (2)
    4.  Evaluate each particle’s fitness function
    5.  If the particle’s personal best is better, update the current personal best
    6.  If the swarm global best is better, update the current global best
3.  Stop the algorithm process and show the global best solution

## Hyper-parameters

### Acceleration coefficients

The *c*[1] and *c*[2] coefficients of personal and global learning, are also called as acceleration coefficients. These coefficients are combined with the random parameters r[1] and r[2] in eq. (1) to control the influence of the personal and the social factors on the particle swarm velocity vector. The constant c[1] expresses the amount of influence of the personal particle cognition and the constant c[2] expresses the amount of influence of the social neighborhood affection on the swarm particle. Also, the acceleration coefficients are combined with the random parameters r[1] and r[2], and control the cognitive and social influence on the particle velocity.

In the standard PSO algorithm, constant values of acceleration coefficients were proposed during the whole optimization process in the search space. Later several researchers have proposed adaptive acceleration coefficients. For example, [Chen et al. (2014](#ch3.xhtml#ref3_8)), have proposed an adaptive acceleration coefficient in order to improve the algorithm search capability. The *c*[1] coefficient decreases from the *c*[1*i*] initial value to the final value *c*[1*f*] , and the *c*[2] coefficient increases from the *c*[2*i*] initial value to *c*[2*f*] final value by applying the following equations:

(3.3)  
$$c\_{1} = \\left( {c\_{1f} - c\_{1i}} \\right)\\frac{t}{t\_{\\max}} + c\_{1i}$$  

(3.4)  
$$c\_{2} = \\left( {c\_{2f} - c\_{2i}} \\right)\\frac{t}{t\_{\\max}} + c\_{2i}$$  

where *t* represents the current iteration, and *t*[max] represents the maximum number of iterations.

### Inertia weight

The inertia weight is used to control the speed of the flying swarm particles. When the swarm particle speed is very big the optimal fitness solution can be easily skipped although the swarm convergence is very quick. On the other hand, when the particle speed is very slow, the swarm convergence is also slow and can be trapped easily in a local minimum.

[Van den Bergh and Engelbrecht (2006](#ch3.xhtml#ref3_43)), have proved that all inertia weight values which are larger than a critical value, guarantee convergent particle swarm trajectories. This critical value is calculated by the equation:

(3.5)  
$$w > \\frac{1}{2}\\left( {c\_{1} + c\_{2}} \\right) - 1$$  

Initially, a static value of inertia weight was proposed during the entire optimization in the search space for all swarm particles. Later several researchers proposed adaptive or dynamically changing inertia weight. Several variations of inertia weight were proposed to improve the search ability and convergence of the PSO algorithm ([Chen et al., 2014](#ch3.xhtml#ref3_8); [Shi and Eberhart, 1998](#ch3.xhtml#ref3_38); [Tian 2021](#ch3.xhtml#ref3_42)). [Shi and Eberhart (1998](#ch3.xhtml#ref3_38)), proposed another type of inertia weight, called time-varying inertia weight. The proposed inertia weight decreases through time and the experimental results have shown a significant improvement in the performance of the standard PSO.

[Tian (2021](#ch3.xhtml#ref3_42)), has proposed an adaptive inertia weight expressed by the following equation:

(3.6)  
$$\\omega = \\left\\{ \\begin{matrix} {\\omega\_{\\min} - \\left( {\\omega\_{\\max} - \\omega\_{\\min}} \\right)\\exp\\left\\lbrack \\left( {- n\\left( {f - f\_{\\min}} \\right)} \\right) \\right\\rbrack,f \\leq f\_{avg}} \\\\ {\\omega\_{\\max},f > f\_{avg}} \\\\ \\end{matrix} \\right.$$  

where,

*   *n* is the iteration number
*   *f* represents the current fitness function value
*   *f[avg]* represents the average fitness function value of all particles.

The modified inertia weight has the advantage of better adaptation during the optimization process since its value changes in every iteration compared to the constant weight of the standard PSO algorithm.

[Chen et al. (2014](#ch3.xhtml#ref3_8)), have proposed another adaptive inertia weight where the weight value is reducing during the iterations. This way the PSO algorithm can investigate specific areas in the local search space. The inertia weight *wt* is calculated by using the following equation:

(3.7)  
$$wt = wt\_{\\min} + \\left( {wt\_{\\max} - wt\_{\\min}} \\right)\\frac{\\left( {t\_{\\max} - t} \\right)}{t\_{\\max}}$$  

where,

*wt*[max] is a predefined maximum inertia weight value

*wt*[min] represents a predefined minimum inertia weight value

*t* is the current iteration of the algorithm

*t*[max] is the maximum number of iterations.

## Stopping criteria

In this section, the stopping criteria of the PSO algorithm are examined. The stopping criteria are specific conditions which are set in order to terminate the PSO algorithm process when the swarm convergence is met. The stopping criteria are as follows.

### Maximum generation number

The algorithm execution stops when the iteration number reaches a predefined maximum number.

### Maximum stall time

This condition forces PSO algorithm execution to stop when the best value of the fitness function does not change in the last predefined maximum stall time (E.g., in seconds).

### Maximum runtime

The algorithm execution stops when a predefined maximum runtime is reached (E.g., in seconds).

### Best fitness value

The algorithm execution stops when the value of the fitness function reaches a predefined best value.

### Population convergence

This criterion stops the algorithm execution when the difference between the maximum and minimum values of all the particles in the population is less than the limit tolerance value.

### Fitness convergence

This criterion stops the algorithm execution when the difference between the maximum and minimum fitness values is less than the limit tolerance value.

[Figure 3.1](#ch3.xhtml#fig3_1), illustrates an example of how the swarm particles traverse the search space in order to find the best value of an objective function.

![Figure 3.1. Example of PSO algorithm for minimizing the rastrigin function. The swarm particles traverse the search space in order to minimize the objective function. The population size was set to 200.](images/fig3_1_B.jpg)

[Figure 3.1. Example of PSO algorithm for minimizing the rastrigin function. The swarm particles traverse the search space in order to minimize the objective function. The population size was set to 200.](#ch3.xhtml#R_fig3_1)

## Swarm topologies

In this section, the most important PSO topologies are discussed. The swarm topology is a very important factor which affects the swarm convergence. The swarm topologies the are discussed are static topologies which do not alter during the optimization process such as: Global or Fully connected topology, local or ring, Von Neumann, Star, Mesh, Random, Tree or Hierarchical topology and also dynamic topologies which change during the convergence process, such as: multi-ring and clan topologies.

![Figure 3.2. Illustration of swarm topologies: (1) Global or Fully connected, (2) Ring, (3) Von Neumann, (4) Star, (5) Mesh, (6) Random, (7) Tree or Hierarchical.](images/fig3_2_B.jpg)

Figure 3.2. Illustration of swarm topologies: (1) Global or Fully connected, (2) Ring, (3) Von Neumann, (4) Star, (5) Mesh, (6) Random, (7) Tree or Hierarchical.

### Global or fully connected

In a global topology, the swarm individuals are fully connected. Each particle is connected and exchange information with all the other particles. Consequently, in this structure, faster convergence is achieved compared to other topologies since particles in the swarm can communicate with all the other particles faster to find the global best solution, but the convergence process can be trapped in local best.

### Local or ring topology

The ring swarm topology corresponds to a local best architecture of PSO. In this structure, every individual particle interacts with its *N* adjacent neighbor particles. This means that each individual particle searches for the best objective value locally, only in its neighborhood. When *N* = 2 there are two adjacent neighbor particles as illustrated in the figure for ring topology. In this topology, a local neighborhood could converge in different local optima as opposed to another local neighborhood which could be still searching for the best local solution. The advantage of this structure is that different local search spaces of the global search space can be explored simultaneously ([Kennedy and Mendes, 2002](#ch3.xhtml#ref3_23)).

### Von Neumann

In Von Neumann topology, each swarm particle is communicating with four other individual particles, the two prior and the two following particles. Some studies, have shown that this topology can produce better results compared to others ([Bratton and Kennedy, 2007](#ch3.xhtml#ref3_7); [Kennedy and Mendes, 2002](#ch3.xhtml#ref3_23)).

### Star topology

In star topology, the communication of the individual particles is accomplished through only one particle. This central particle is affected by all the other swarm particles. The star structure, leads to particle isolation since all the information about the best objective value is exchanged through the central swarm particle. The central particle fathers and compares the local bests of each swarm particle and adjusts its new best position.

### Mesh topology

In this topology, one swarm particle is connected to four neighbouring particles. The swarm particles on the edges are connected with two adjacent swarm particles. This means that there are overlapping particle neighbors which create redundancy during the convergence process. The mesh architecture of the swarm particles remains during the algorithm execution process.

### Random topology

In random topology, the swarm individuals are connected with a random number of swarm particles other than them. Each particle is connected and exchanges information only with the connected particles. This structure does not change in all the convergence processes.

### Tree or hierarchical topology

In the hierarchical or tree topology there are hierarchic levels of swarm particles. Also, there is a central particle which functions as a root in the top level and it is connected with the particles of the next lower level in the hierarchy. The tree topology is similar to the binary tree architecture. The root particle is selected randomly in the swarm and searches for the best solution obtained by the next lower level in the hierarchy.

### Dynamic or adaptive topologies

All the previous topologies are static since they cannot be changed in all the optimization processes. Another category of topologies is based on a dynamic mode. More recently, dynamics topologies have been proposed. These neighborhood topologies vary during the optimization process. Some of them are: Multi-Ring and Clan topology. In Multi-Ring topology ([Bastos-Filho et al., 2008](#ch3.xhtml#ref3_6)), which is constructed by several layers placed one over the other with each having a ring topology. In Clan topology (Carvalho et al., 2009), where the particle swarm is separated into sub-swarms named as ‘clans’ and every clan has a fully-connected architecture. Also, there are other adaptive topologies such as: adaptive population-based PSO ([Almasi and Khooban, 2018](#ch3.xhtml#ref3_1)), complementary Cyber Swarm ([Yin et al., 2011](#ch3.xhtml#ref3_45)), stochastic star PSO ([Miranda et al., 2008](#ch3.xhtml#ref3_28)).

## Boundary handling approaches

In this section, several boundary handling approaches are discussed which affect the performance of the PSO algorithm. These techniques are very important since they can restrict the swarm particle movement in the predefined search space ([Helwig et al., 2013](#ch3.xhtml#ref3_20); [Mostaghim et al., 2006](#ch3.xhtml#ref3_31); [Padhye et al., 2013](#ch3.xhtml#ref3_35)). Therefore, these methods can help the algorithm achieve convergence faster to a global solution.

### Hyperbolic method

In this technique, the swarm particle cannot leave the feasible space ([Clerc, 2006](#ch3.xhtml#ref3_10)). This is achieved by normalizing the velocity of the swarm particle according to the equations:

(3.8)  
$$v\_{i,j}^{t + 1} = \\left\\{ \\begin{matrix} \\frac{v\_{i,j}^{t + 1}}{1 + \\left| {v\_{i,j}^{t + 1}/\\left( {X\_{\\max} - x\_{i,j}^{t}} \\right)} \\right|} & {whenv\_{ij}^{t + 1} > 0} \\\\ \\frac{v\_{i,j}^{t + 1}}{1 + \\left| {v\_{i,j}^{t + 1}/\\left( {x\_{i,j}^{t} - X\_{\\min}} \\right)} \\right|} & {whenv\_{ij}^{t + 1} \\leq 0} \\\\ \\end{matrix} \\right.$$  

where, the X[max] and X[min] parameters represent the upper and lower boundaries in the jth dimension. The new normalized particle velocity secures the new swarm particle position such that it cannot be out of bounds. This method restricts the velocity of the swarm particle in the feasible space and converges faster.

### Infinity or invisible wall

In this method the only modification is that the personal best and the global best particle positions should be in the search space ( [Bratton and Kennedy, 2007](#ch3.xhtml#ref3_7); [Robinson and Rahmat-Samii, 2004](#ch3.xhtml#ref3_36)). This means that, if the particles leave the search space, their local and global best attractors will be within search bounds. The infinity technique does not modify the particle velocity or position, and as a sequence the algorithm is not affected by the boundary handling method.

### Nearest or boundary or absorb

In this technique, the swarm particle that violates the boundary is moved back to the boundary of the violated parameter. The result when applying this method, is that the swarm particles are moved near the problem solutions that are close to the search space boundary.

### Random

In this method if a particle is out of bounds then the position is reinitialized uniformly in a valid position within the problem search space. This way the diversity of swarm particle solutions is increased by randomly placing the particles in positions that would have been unlikely to be placed otherwise.

### Random-half

In this method if a particle is out of bounds, then the position is reinitialized uniformly to a valid position within half the search space nearest to the violated point.

### Periodic

This method provides an infinite space, which includes periodic copies of the original search space ([Zhang et al., 2004](#ch3.xhtml#ref3_47)). Each particle which violates the boundaries is placed to a location composed of copies of the original search space. The Periodic technique handles the particle variables and allows the particle to enter the search space again opposite to the place where it has left. This method has the advantage of eliminating particle swarm disorganization compared to other conventional methods such as mutation-based boundary handling methods. The performance of particle swarm optimization with the Periodic boundary handling method has shown improved optimization results compared to Random and Boundary methods, especially when the local optimums are located close to the boundary.

### Exponential

This method provides a correction of the particle position parameter in every dimension by placing the swarm particle to a location among the previous particle positions and the violated boundary position (AlvarezBenitez et al., 2005). The new position is defined by implementing a truncated exponential distribution, in order to have increased probability of being placed in a position closer to the boundary. The exponential method preserves search data regarding the best solutions close to the boundaries compared to the random and random-half methods.

### Mutation

This method includes a mutation that has been utilized so that the violated particle parameter can be perturbed in order to be placed back into the problem search region.

### Reflect methods

In the reflect technique, the positions of the violated particle parameters are reflected in the closer boundary into the search space. In the reflected position the new velocity can be set with several methods in the violated variables:

*   Unmodified velocity
*   Velocity set to zero
*   Velocity adjusted according to the equation: V[new] = V[new,bounded] − V[old,unbounded]

### Random damping

[Huang and Mohan (2005](#ch3.xhtml#ref3_22)), have proposed a hybrid boundary condition in particle swarm optimization. If a swarm particle violates the boundary, then the particle velocity is partially absorbed and partially reflected. This way the particle is forced to return into valid space with decreased velocity. The fraction of the reflected and absorbed velocity is random.

## PSO with mutation

In the standard PSO algorithm there are no evolution parameters like mutation and crossover. Although, several researchers in the literature have proposed PSO algorithms with mutation operators  ([Assarzadeh and Naghsh-Nilchi, 2015](#ch3.xhtml#ref3_5); [Lin and Zhang, 2017](#ch3.xhtml#ref3_26); [Stacey et al., 2003](#ch3.xhtml#ref3_39)) they can contribute to overcome early convergence into local minimums that could appear in the standard particle swarm optimization algorithm. In this section, a review of researches that have improved the standard PSO algorithm by adding a mutation strategy have been discussed.

### Gaussian mutation PSO

[Higashi and Iba (2003](#ch3.xhtml#ref3_21)), have applied a mutation operator which alters the value of a particle swarm dimension by using a random number from a Gaussian distribution. The equation which changes the particle position dimensions, x[id], is expressed by:

  
*m**u**t**a**t**e*(*x*[*i**d*]) = *x*[*i**d*](1+*g**a**u**s**s**i**a**n*(*σ*))  

where,

*   σ represents the standard deviation
*   gaussian(σ) represents the function which draws a random number from a Gaussian distribution

### Cauchy mutation PSO

[Stacey et al. (2003](#ch3.xhtml#ref3_39)), have proposed a similar mutation operator by implementing the Cauchy probability distribution. The Cauchy mutation is applied on the particle with the global best value in every generation. The one-dimensional Cauchy probability density function is expressed by the equation:

(3.9)  
$$f\\left( x \\right) = \\frac{t^{2}}{\\pi\\left( {x^{2} + t^{2}} \\right)}, - \\infty < x < \\infty$$  

where t is a positive parameter. The Cauchy cumulative distribution function is expressed by the equation:

(3.10)  
$$F\_{t}\\left( x \\right) = \\frac{1}{2} + \\frac{1}{\\pi}\\arctan\\left( \\frac{x}{t} \\right)$$  

The shape of the Cauchy distribution is similar to the Gaussian distribution, but the probability is more in the tails. The *x[id]* particle position dimensions, are updated by the equation:

(3.11)  
*m**u**t**a**t**e*(*x*[*i**d*]) = *x*[*i**d*] + *c**a**u**c**h**y*(*a*)  

where *a* represents a parameter similar to the *σ* parameter of Gaussian distribution that affects the shape of the distribution.

### Michalewicz non-uniform mutation

[Esquivel and Coello (2003](#ch3.xhtml#ref3_18)), have studied a non-uniform mutation operator for PSO developed by Michalewicz to be used in genetic algorithms ([Michalewicz, 1998](#ch3.xhtml#ref3_27); [Dasgupta and Michalewicz, 2013](#ch3.xhtml#ref3_13)). The Michalewicz’s non-uniform mutation operator uses random numbers non-uniformly to mutate values and it is useful when the PSO algorithm is trapped in local optima and when highly multimodal functions are being optimized. In the Michalewicz’s non-uniform operator, the particle position dimension, *x[id]*, is mutated by using the equation:

(3.12)  
$$mutate\\left( x\_{id} \\right) = \\left\\{ \\begin{matrix} {x\_{id} + delta\\left( {it,U - x\_{id}} \\right):rb = 1} \\\\ {x\_{id} + delta\\left( {it,U - x\_{id}} \\right):rb = 1} \\\\ \\end{matrix} \\right.$$  

where,

*   *it* illustrates the iteration number
*   *U* represents the upper bound
*   *L* represents the lower bound
*   *rb* the generated random bit
*   delta (*t,y*) is calculated by the equation:

(3.13)  
*d**e**l**t**a*(*t*,*y*) = *y*(1−*r*^((1 − *t*/*T*)^(*b*)))  

where *r* represents a randomly generated number in the range \[0,1\], *T* the maximum iteration number of the algorithm, and *b* represents a parameter usually set to the value 5 ([Michalewicz, 1998](#ch3.xhtml#ref3_27)).

### Chaotic PSO with Michalewicz mutation

In the swarm optimization algorithms, which are modified based on the chaos theory, the basic application technique is to use chaotic parameters instead of the usual random variables of the PSO algorithm. [Assarzadeh and Naghsh-Nilchi (2015](#ch3.xhtml#ref3_5)), have proposed the application of a mutation method to a chaotic particle swarm optimization for classification problems. The study proposes the implementation of logistic maps as chaotic sequences by combining also the Michalewicz’s nonuniform mutation. In this research, the random parameters in PSO are replaced by the chaotic sequences generated by the logistic map. The random parameters are given by the logistic map chaotic equation:

(3.14)  
*C**r*[(*t* + 1)] = *k**C**r*[(*t*)](1−*C**r*[(*t*)])  

where n = 0,1,2,3... and k = 4. The Cr(t) parameter is controlled by the k parameter of the chaotic logistic map. Considering the above assumptions the particle velocity update equation of the chaotic particle swarm optimization can be expressed as:

(3.15)  
*v*[*i*](*t*+1) = *w* *v*[*i*](*t*) + *c*[1]*C*[*r*]\[*P**b**e**s**t*(*t*)−*x*[*i*](*t*)\] + *c*[2](1−*C*[*r*]) + *c*[2](1−*C*[*r*])\[*G**b**e**s**t*(*t*)−*x*[*i*](*t*)\]  

Final results of the research have shown an improved performance of Chaotic PSO with Michalewicz mutation in high dimensional spaces as a global search optimization algorithm.

### Random mutation PSO

In this kind of mutation, the operator initializes the particle swarm position with a randomly uniformly generated value in the range ([Andrews, 2006](#ch3.xhtml#ref3_4)).

### Constant mutation PSO

In this type of mutation, the mutation rate remains the same during the optimization iterations.

### Stagnant mutation

This kind of mutation is applied when the global best of the particle population remains the same for a fixed number of iterations.

### Quantum PSO

Quantum PSO (QPSO) was introduced in 2004 ([Sun et al., 2004](#ch3.xhtml#ref3_40)). Quantum-behaved PSO is a very interesting variation of the standard PSO algorithm. The QPSO algorithm incorporates quantum mechanics in the PSO algorithm. In classical mechanics, the swarm particle is defined by the vectors regarding the position *x[i]* and the velocity *v[i]* of the particle in the swarm. In quantum mechanics, the position *x[i]* and the velocity *v[i]* of the particle cannot be defined simultaneously because of the uncertainty principle ([Sun et al., 2011](#ch3.xhtml#ref3_41)). Consequently, in a quantum system the PSO particles will have a quantum behavior, which means that the particles will be defined by their state and not by their position and velocity. The state of the swarm particle is expressed by the using the wavefunction *ψ*(*x,t*) of quantum mechanics. In the QPSO algorithm the swarm is a quantum system and every particle is identified by a quantum state. In the following sections, two quantum PSO algorithms are discussed: Delta well quantum PSO and Harmonic quantum PSO.

### Delta well quantum PSO

In the delta well quantum PSO principle ([Sun et al., 2011](#ch3.xhtml#ref3_41)) the swarm particle is moving to a position p in a one-dimensional delta potential field. The delta potential well field is expressed by the equation:

(3.16)  
$$V(x) = \\left\\{ \\begin{matrix} \\infty & {if\\, x\\, is\\, 0} \\\\ 0 & {if\\, x\\, is \\neq \\, 0} \\\\ \\end{matrix} \\right.$$  

By solving the Schrödinger equation in a one-dimensional delta potential well, the probability density function can be found.

(3.17)  
$$D(x\_{i,j}(t + 1))\\frac{1}{L\_{i,j}(t)}e^{- 2|P\_{i,j}(t) - x\_{i,j}(t + 1)|/L\_{i,j}(t)}$$  

(3.18)  
*F*(*x*[*i*, *j*](*t* + 1)) = *e*^( − 2|*P*[*i*, *j*](*t*) − *x*[*i*, *j*](*t* + 1)|/*L*[*i*, *j*](*t*))  

where,

*   D represents the normalized probability density function
*   *L*(*t*) represents the characterization potential well length

Then the Monte Carlo method is implemented to find the particle position according to the equation principle ([Sun et al., 2011](#ch3.xhtml#ref3_41)):

(3.19)  
$$\\left\\{ \\begin{matrix} {x\_{i}\\left( {t + 1} \\right) = p\_{i} + \\beta.\\left| {Pbest\_{i} - x\_{i}\\left( t \\right)} \\right|.\\ln\\left( {1/u} \\right)} \\\\ {x\_{i}\\left( {t + 1} \\right) = p\_{i} + \\beta.\\left| {Pbest\_{i} - x\_{i}\\left( t \\right)} \\right|.\\ln\\left( {1/u} \\right)} \\\\ \\end{matrix} \\right.$$  

*   where β is the contraction-expansion parameter ([Sun et al., 2011](#ch3.xhtml#ref3_41));
*   u is a random number in the uniformly distributed space \[0,1\]
*   *Pbest[i]* is mean of the pbest swarm positions
*   *p[i]* is the best position of the ith swarm particle

The global mean best particle (*Pbest*) of the swarm is expressed by the mean of all the particle best positions:

(3.20)  
$$Pbest\_{i} = \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}{p\_{k,i}\\left( t \\right)}}$$  

where k illustrates the best particle index in the swarm of N particles.

The Delta well quantum PSO algorithm includes the following steps:

*   **Step 1.** Particle swarm initialization of the population and random particle positions uniformly distributed in the search space.
*   **Step 2.** Particle fitness function evaluation.
*   **Step 3.** Comparison of personal best value of the fitness function. If the current fitness function value is better, then set the personal best value equal to the current fitness function value in the search space.
*   **Step 4.** Compare the current global best solution with the previous global best solution. If the current value is better then set it as the global best.
*   **Step 5.** Update the global best point by estimating the Pbest according to relevant equation.
*   **Step 6.** Update the particles’ positions.
*   **Step 7.** Repeat the process from step 2 until a stop criterion is achieved, e.g., the maximum number of iterations.

### Harmonic quantum PSO

Several other potential fields were proposed. In the harmonic quantum PSO ([Sabat et al., 2010](#ch3.xhtml#ref3_37)) the harmonic oscillator is utilized as a potential field. In the Harmonic potential distribution, the potential well energy of the swarm particle in a one-dimensional harmonic potential well is expressed by the equation:

(3.21)  
$$V\\left( x \\right) = \\frac{1}{2}kx^{2}$$  

where, *k* represents the harmonic well depth.

The *D* probability density function is given by the equation:

(3.22)  
*D*(*x*)=|*ψ*(*x*)|[2]\=*L*exp(−0.5*α*²*x*²)  

(3.23)  
$$L = \\frac{\\alpha}{\\sqrt{\\pi}}$$  

where L is the characteristic well length. The new quantum particle position can be found by using the equation (Sabat et al., 2010):

(3.24)  
$$x\_{i,j}\\left( {t + 1} \\right) = p\_{i.j}\\left( t \\right) \\pm \\alpha.\\frac{1}{0.4769g}\\left| {x\_{i,j}\\left( t \\right) - mpbest\_{j}\\left( t \\right)} \\right|\\sqrt{\\ln\\frac{1}{u}}$$  

where,

*   mpbest is the mean swarm best of particles
*   *g* is a parameter set to 2.0.

Similarly, with delta well quantum PSO, the implementation involves the Monte Carlo method. The Harmonic QPSO algorithm implementation is similar to the delta well quantum PSO.

**Multi-objective PSO**

A multi-objective optimization problem with several conflicting objectives can be defined as follows:

(3.25)  
min *i**m**i**z**e* *F*(*x*) = (*f*[1](*x*), *f*[2](*x*), ...., *f*[*m*](*x*))^(*T*)  

(3.26)  
*s**u**b**j**e**c**t* *t**o* *x* ∈ *Ω*  

where Ω represents the feasible set with:

(3.27)  
*Ω* ⊆ ℝ^(*n*) ≠ ⌀  

and

(3.28)  
*f*[*i*]:ℝ^(*n*)→ℝ  

represents the *m* objective functions for *i* = 1, 2*, . . . , m*, and *m ≥* 2. The objective space is the image of the feasible set*:*

(3.29)  
*y* = {*F*(*x*)∈ℝ^(*m*):*x*∈*Ω*}  

The sets *R^n* and *R^m* represent the *decision space* and the *objective space* respectively.

In multi-objective optimization problems, the dominance defines the degree of the goodness of a solution. The concept of dominance is explained generally as: A point x dominates another point y in the objective function vector *f* when:

(3.30)  
*f*[*i*](*x*) ≤ *f*[*i*](*y*)*f**o**r* *a**l**l* *i*  

(3.31)  
*f*[*j*](*x*) ≤ *f*[*j*](*y*)*f**o**r* *s**o**m**e* *j*  

A nondominated set of solutions (points) among a set of solutions *P* represents the set of solutions *Q* in set of solutions *P* that are not dominated by any other solution in *P*.

A particle solution *x*′ *X* represents a non-dominated solution if no other particle solution *x* *X* exists such that:

(3.32)  
*f*[*i*](*x*) ≤ *f*[*i*](*x*′)*f**o**r* *a**l**l* *i* = 1, ..., *m*  

and at least one index *i* exists such that:

(3.33)  
*f*[*i*](*x*) ≤ *f*[*i*](*x*′)  

In a given set of swarm particle solutions, the non-dominated solution set represents the set of all the swarm particle solutions which are not dominated by any other solution of the set. The non-dominated set of the whole feasible decision space represents the Pareto optimal set of the swarm particle solutions. The decision boundary determined by the set of all points (solutions) mapped from the Pareto optimal set represents the Pareto optimal front ([Deb, 2011](#ch3.xhtml#ref3_15)).

In multi-objective problems, when a solution is not dominated by another solution it is a Pareto optimal solution. The discovered non-dominated particle solutions are stored in the external global memory or repository. The steps of the multi-objective PSO algorithm ([Coello and Lechuga, 2002](#ch3.xhtml#ref3_11); [Coello et al., 2004](#ch3.xhtml#ref3_12)) are described as follows:

1.  Initialize the particle population positions *POPi*, where i = \[1, 2,...,N\] and N represents the particle population size.
2.  Initialize velocity *VELi* of each swarm particle
3.  Evaluate each swarm particle in the *POPi*.
4.  Save the positions of the particles which express the non-dominated solutions in the repository (*REP*).
5.  Generate the search space hypercubes so far and use them to locate the swarm particles where every swarm particle has its objective functions as coordinates.
6.  Initialize each particle memory and save them in the repository as the best particle positions found so far.
7.  Estimate the new velocity of every particle by using the equation:
    
    (3.34)  
    VEL[*i*](*t*+1) = *w*VEL[*i*](*t*) + *c*[1]*r*[1](*t*)(POP[*i*, *p**b**e**s**t*](*t*)−POP[*i*](*t*)) + *c*[2]*r*[2](*t*)(*R**E**P*[\[*h*\]](*t*)−POP[*i*](*t*))  
    
    where *w* represents the inertia weight, *r[1]* and *r[2]* represent random numbers in the range \[0,1\], *POP[i,pbest]* represents the best position of the swarm particle *i*, *REP[\[h\]]* represents a value taken from the repository with index *h*. Roulette-wheel selection is performed to select the hypercube from which the swarm particle will be taken. Then a swarm particle is chosen randomly from the selected hypercube. *POP[i]* represents the current fitness value of the swarm particle.
    
8.  Estimate the new positions of each particle by using the equation:
    
    (3.35)  
    POP[*i*](*t*+1) = POP[*i*](*t*) + VEL[*i*](*t*)  
    
9.  Maintain the swarm particles within the search space in case of going out of boundaries.
10.  Evaluate the swarm particles in *POP[i]*.
11.  Update the values stored in REP and the coordinates within the hypercubes by adding the current non-dominated solutions. When the repository space is full the swarm particles in the less populated regions have more priority compared to the swarm particles in highly populated areas.
12.  Update each swarm particle personal best position in the memory when the current position is better than the particle position in the memory by applying Pareto dominance, by using the equation:
     
     (3.36)  
     POP[*i*, *p**b**e**s**t*](*k*+1) = POP[*i*](*k*)  
     
13.  If the termination condition is met (E.g., the maximum number of iterations), then stop the algorithm, otherwise go to step 7.

## Geometric PSO

Geometric PSO (GPSO) proposed by [Moraglio et al. (2007](#ch3.xhtml#ref3_30)). Geometric PSO algorithm has been used in the literature similarly to the standard PSO and also for feature selection ([Namous et al., 2020](#ch3.xhtml#ref3_32); [Yeoh et al., 2015](#ch3.xhtml#ref3_44)). GPSO differs from the standard PSO algorithm in several points: there is no velocity, the equation of position update is a convex combination and mutation is utilized. The basic equation which is utilized in GPSO is expressed by the formula:

(3.37)  
*x*[*i*] = *C**X*((*x*[*i*],*w*[1]),(*g*,*w*[2]),(*x*[*i*],*w*[3]))  

where:

*   *x[i]* expresses the position of particle *i.*
*   *g* indicates the global best, the best swarm position found so far.
*   *w[1], w[2]*, and *w[3]* express the scalar coefficients.
*   *CX* expresses a randomized convex combination.

The parameters w[1], w[2], and w[3] are correlated based on the equation:

(3.38)  
*w*[1] + *w*[2] + *w*[3] = 1  

with the condition:

(3.39)  
*w*[1], *w*[2], *w*[3] > 1  

w[1] coefficient is calculated by the equation: *w*[1] = 1 – *w*[2] – *w*[3]. These coefficients represent the attraction to the previous position of the particle, the particle’s best position (personal learning), and the swarm best position (global learning).

Geometric PSO uses a three-parent mask-based crossover operator instead of the velocity parameter to calculate the new position of the particle ([Moraglio et al., 2007](#ch3.xhtml#ref3_30)). The geometric crossover guides the swarm particles in the search space in a way that they cannot be outside the convex hull of the initial swarm population. The requirements for a convex combination of w[1], w[2], and w[3] in a metric space are ([Moraglio et al., 2007](#ch3.xhtml#ref3_30)): Convex weights: a convex combination where w[1], w[2], w[3] > 0 and w[1] + w[2] + w[3] = 1, convexity: a convex combination returns a point within the metric convex hull, coherence between weights and distances, symmetry: when the same values are assigned to the w[1], w[2], or w[3] parameters the effect is same. The Geometric PSO algorithm is described as follows ([Moraglio et al., 2007](#ch3.xhtml#ref3_30)).

**Geometric PSO algorithm**

## PSO in neural network optimization

PSO algorithm has been applied in several researches as an artificial neural network (ANN) optimizer. The main reason for applying PSO in the ANN optimization is its advantages over other ANN optimization methods: the PSO does not require gradient information, the computation ability is improved compared to other optimization techniques such as genetic algorithm and also the PSO algorithm requires very few parameters to be defined compared to other computational optimization methods ([Chen et al., 2006](#ch3.xhtml#ref3_9); [Hassan et al., 2005](#ch3.xhtml#ref3_19); [Kouziokas, 2020](#ch3.xhtml#ref3_25); [Ou and Lin, 2006](#ch3.xhtml#ref3_34)).

### PSO as weight optimizer

PSO can be implemented to optimize several parameters of a neural network. An objective function should be found when a neural network is trained by PSO. The most common objective function that is used is an error metric. For example, in regression problems the mean squared error (MSE) or root mean squared error (RMSE) or mean absolute error (MAE) of a neural network can be used as an objective function. In classification problems other metrics can be utilized, such as: accuracy, precision, recall, F1, kappa. After the selection of the objective function, the swarm topology should be developed. Each particle represents a solution to the optimization of the objective function and the neural network weight vector is optimized until the swarm finds the best solution for the objective function.

### PSO as topology optimizer

PSO can be implemented to optimize several parameters of a neural network such as the number of hidden neurons. In this case, each particle represents the number of hidden neurons in the hidden layer of the neural network. The objective function should be set for the PSO. As it was mentioned above, the most common objective function that is used is an error metric. Adequately, in regression problems and in classification problems several error metrics can be used as objective functions ([Zhang and Shao, 2000](#ch3.xhtml#ref3_46)).

According to several researches, the particle swarm optimization has a better performance in artificial neural network optimization than other optimization algorithms, such as genetic algorithm ([Anand and Suganthi, 2020](#ch3.xhtml#ref3_3); [Moayedi et al., 2019](#ch3.xhtml#ref3_29)), imperialist competitive algorithm and artificial bee colony ([Koopialipoor et al., 2019](#ch3.xhtml#ref3_24)), and non-dominated sorting genetic algorithm II (NSGA-II) ([Anand and Suganthi, 2020](#ch3.xhtml#ref3_3); [Nourbakhsh et al., 2011](#ch3.xhtml#ref3_33)). [Koopialipoor et al. (2019](#ch3.xhtml#ref3_24)), have studied the forecasting of a safety factor by applying several optimization techniques in artificial neural networks such as: imperialist competitive algorithm, the artificial bee colony and particle swarm optimization. The experimental outcomes have shown that PSO has a better optimization ability on the ANN compared to the other optimization algorithms. [Nourbakhsh et al. (2011](#ch3.xhtml#ref3_33)), have studied the application of two optimization methods in the group method of data handling neural network optimization: PSO and non-dominated sorting genetic algorithm II. The PSO optimized neural network had a better performance compared to the neural network that was optimized with the NSGA-II algorithm.

## Swarm optimization examples

Some example applications of PSO in convex and non-convex optimization are illustrated in this section, regarding function approximation. The experimental set up of the PSO algorithm was applied on convex, nonconvex, unimodal and multimodal functions such as: Sphere, Griewank Function, Ackley, Schwefel, Rastrigin. In all the experiments, the chosen dimension was 30. Several particle swarm architectures were investigated with different values of the acceleration coefficients c[1] and c[2]. The generation (iteration) number was set to 1000.

### Sphere function

#### Mathematical equation

The equation that represents the Sphere function is as follows:

(3.40)  
$$f\\left( x \\right) = f\\left( {x\_{1},x\_{2},....,x\_{n}} \\right) = {\\sum\\limits\_{i = 1}^{n}x\_{i}^{2}}$$  

#### Description

The Sphere function is:

*   Continuous.
*   Convex.

![3.3a. Sphere function minimization.](images/fig3_3a_C.jpg)

3.3a. Sphere function minimization.

![3.3b. Griewank function minimization.](images/fig3_3b_C.jpg)

3.3b. Griewank function minimization.

![3.3c. Rastrigin function minimization.](images/fig3_3c_C.jpg)

3.3c. Rastrigin function minimization.

![3.3d. Ackley function minimization.](images/fig3_3d_C.jpg)

3.3d. Ackley function minimization.

![3.3e. Schwefel function minimization.](images/fig3_3e_C.jpg)

3.3e. Schwefel function minimization.

**Figure 3.3.** Benchmark functions minimized by PSO by testing different architectures. The particles traverse the search space in order to minimize the functions. The population size was set to 20.

*   Unimodal.
*   Differentiable.

*Input search space*

The function is evaluated with xi \[−5.12, 5.12\] with i = 1, 2, …, n.

#### Global minima

f(x\*) = 0, x\* = (0,…,0).

#### Function approximation with PSO

Several PSO architectures were tested. The best optimization results were achieved when the coefficient c[1] = 2.0 and coefficient c[2] = 1.0 as illustrated in [Figure 3.3](#ch3.xhtml#fig3_3).

### Griewank function

#### Mathematical equation

The equation that represents the Griewank function is as follows.

(3.41)  
$$f\\left( x \\right) = f\\left( {x\_{1},\\ldots,x\_{n}} \\right) = 1 + {\\sum\\limits\_{i = 1}^{n}{\\frac{x\_{i}^{2}}{4000} - {\\prod\\limits\_{i = 1}^{n}{\\cos\\left( \\frac{x\_{i}}{\\sqrt{i}} \\right)}}}}$$  

#### Description

The Griewank function is:

*   Continuous.
*   Non-convex.
*   Unimodal.
*   Differentiable.

#### Input search space

The function is evaluated with xi \[−600, 600\] with i = 1, 2, …, n.

#### Global minima

f(x\*) = 0, x\* = (0,…,0).

#### Function approximation with PSO

Several PSO architectures were tested. The best optimization results were achieved when the coefficient c[1] = 1.0 and coefficient c[2] = 1.0 as illustrated in [Figure 3.3](#ch3.xhtml#fig3_3).

### Rastrigin function

#### Mathematical equation

The equation that represents the Rastrigin function is as follows.

(3.42)  
$$f(x) = 10d + {\\sum\\limits\_{i = 1}^{d}\\left\\lbrack {x\_{i}^{2} - 10\\cos\\left( {2\\pi x\_{i}} \\right)} \\right\\rbrack}$$  

where *d* represents the *dimension.*

#### Description

The Rastrigin function is:

*   Continuous.
*   Convex.
*   Multimodal.
*   Differentiable.

*Input search space*

The function is evaluated with xi \[−5.12, 5.12\] , i = 1, 2, . . . , n.

#### Global minima

x\* = (0, …, 0), f(x\*) = 0.

#### Function approximation with PSO

Several PSO architectures were tested. The best optimization results were achieved when the coefficient c[1] = 1.0 and coefficient c[2] = 2.0 as illustrated in the [Figure 3.3](#ch3.xhtml#fig3_3). Thus, the personal cognition is smaller than the social cognition.

### Ackley function

#### Mathematical equation

The equation that represents the Ackley function is the following.

(3.43)  
$$f(x) = f\\left( {x\_{1},\\ldots,x\_{n}} \\right) = - a.\\exp\\left( {- b\\sqrt{\\frac{1}{n}{\\sum\\limits\_{i = 1}^{n}x\_{i}^{2}}}} \\right) - \\exp\\left( {\\frac{1}{n}{\\sum\\limits\_{i = 1}^{n}{\\cos\\left( {cx\_{i}} \\right)}}} \\right) + a + \\exp\\left( 1 \\right)$$  

where a, b and c are constants which are set to the most common values for the experiments: a = 20, b = 0.2 and c = 2π.

#### Description

The Ackley function is:

*   Continuous.
*   Non-convex.
*   Multimodal.
*   Differentiable.

#### Input search space

The function is evaluated with xi \[−20, 20\], and i = 1, 2, . . . , n.

#### Global minima

x\* = (0, …, 0), f(x\*) = 0.

#### Function approximation with PSO

Several PSO architectures were tested. The best optimization results were achieved when the coefficient c[1] = 3.0 and coefficient c[2] = 1.0 as illustrated in the [Figure 3.3](#ch3.xhtml#fig3_3). Thus, the personal cognition is bigger than the social cognition.

### Schwefel function

#### Mathematical equation

The equation that represents the Schwefel function is the following.

(3.44)  
$$f(x) = - {\\sum\\limits\_{i = 1}^{n}{x\_{i}\\sin\\left( \\sqrt{\\left| x\_{i} \\right|} \\right)}}$$  

### Description

The Schwefel function is:

*   Continuous.
*   Non-convex.
*   Multimodal.1
*   Non-differentiable.

#### Input search space

The function is evaluated in the search space: *x[i]* \[−500, 500\] with i = 1, 2, …, n.

#### Global minima

*f*(*x*) = –*n*•418.9829, *x*(*i*) = 420.9687.

#### Function approximation with PSO

Several PSO architectures were tested. The best optimization results were achieved when the coefficient c[1] = 1.0 and coefficient c[2] = 2.0 as illustrated in the [Figure 3.3](#ch3.xhtml#fig3_3). Thus, the personal cognition is smaller than the social cognition.

## References

*   [Almasi, O. N. and Khooban M. H.](#ch3.xhtml#R_ref3_1) (2018). A parsimonious SVM model selection criterion for classification of real-world data sets via an adaptive population-based algorithm. Neural Computing and Applications, 30(11): 3421–3429.
*   Alvarez-Benitez, J. E., Everson, R. M. and Fieldsend, J. E. (2005). A MOPSO algorithm based exclusively on pareto dominance concepts. pp. 459–473. *In*: Coello Coello, C. A., Hernández Aguirre, A. and Zitzler, E. (eds.). EMO 2005. LNCS, vol. 3410. Springer, Heidelberg. [https://doi.org/10.1007/978-3-540-31880-4\_32](https://doi.org/10.1007/978-3-540-31880-4_32).
*   [Anand, A. and Suganthi, L.](#ch3.xhtml#R_ref3_3) (2020). Forecasting of electricity demand by hybrid ANNPSO models. pp. 865–882. In:. Deep Learning and Neural Networks: Concepts, Methodologies, Tools, and Applications, IGI Global.
*   [Andrews, P. S.](#ch3.xhtml#R_ref3_4) (2006). an investigation into mutation operators for particle swarm optimization. IEEE International Conference on Evolutionary Computation, Vancouver, BC, Canada, 2006, pp. 1044–1051. doi: [https://10.1109/CEC.2006.1688424](https://doi.org/10.1109).
*   [Assarzadeh, Z. and Naghsh-Nilchi, A. R.](#ch3.xhtml#R_ref3_5) (2015). Chaotic particle swarm optimization with mutation for classification. Journal of Medical Signals and Sensors, 5(1): 12–20, Jan–Mar, 2015.
*   [Bastos-Filho, C. J. A., Caraciolo M. P., Miranda P. B. C. and Carvalho D. F.](#ch3.xhtml#R_ref3_6) (2008). Multi-ring particle swarm optimization. 2008 10th Brazilian Symposium on Neural Networks, 26–30 Oct. 2008.
*   [Bratton, D. and Kennedy, J.](#ch3.xhtml#R_ref3_7) (2007). Defining a standard for particle swarm optimization. pp. 120–127. *In*: Proceedings of the IEEE Swarm Intelligence Symposium. IEEE Computer Society. [https://doi.org/10.1109/SIS.2007.368035](https://doi.org/10.1109/SIS.2007.368035).
*   [Chen, H. l., Yang, B., Wang, S. j., Wang, G., Liu, D. y. et al.](#ch3.xhtml#R_ref3_8) (2014). Towards an optimal support vector machine classifier using a parallel particle swarm optimization strategy. Applied Mathematics and Computation, 239: 180–197. doi:[https://doi.org/10.1016/j.amc.2014.04.039](https://doi.org/10.1016/j.amc.2014.04.039).
*   [Chen, Y., Yang, B. and Dong, J.](#ch3.xhtml#R_ref3_9) (2006). Time-series prediction using a local linear wavelet neural network,. Neurocomputing, 69: 449–465.
*   [Clerc, M.](#ch3.xhtml#R_ref3_10) (2006). Confinements and biases in particle swarm optimisation. [https://hal. archives-ouvertes.fr/hal-00122799/](https://hal.).
*   [Coello, C. C. and Lechuga, M. S.](#ch3.xhtml#R_ref3_11) (2002). MOPSO: A proposal for multiple objective particle swarm optimization. pp. 1051–1056. In Proceedings of the 2002 Congress on Evolutionary Computation. CEC'02 (Cat. No. 02TH8600) (Vol. 2). IEEE.
*   [Coello, C. A. C., Pulido, G. T. and Lechuga, M. S.](#ch3.xhtml#R_ref3_12) (2004). Handling multiple objectives with particle swarm optimization. IEEE Transactions on Evolutionary Computation, 8(3): 256–279.
*   [Dasgupta, D. and Michalewicz, Z.](#ch3.xhtml#R_ref3_13) (eds.). (2013). Evolutionary Algorithms in Engineering Applications. Springer Science & Business Media.
*   de Carvalho, D. F. and Bastos-Filho, C. J. A. (2009). Clan particle swarm optimization. International Journal of Intelligent Computing and Cybernetics.
*   [Deb, K.](#ch3.xhtml#R_ref3_15) (2011). Multi-objective optimisation using evolutionary algorithms: an introduction. pp. 3–34. In Multi-objective Evolutionary Optimisation for Product Design and Manufacturing. Springer, London.
*   [Eberhart, R. C. and Shi, J. Y.](#ch3.xhtml#R_ref3_16) (2001). Kennedy,. Swarm Intelligence: Elsevier.
*   [Eberhart, R. and Kennedy, J.](#ch3.xhtml#R_ref3_17) (1995). A new optimizer using particle swarm theory. MHS’95. Proceedings of the Sixth International Symposium on Micro Machine and Human Science \[4–6 Oct. 1995\].
*   [Esquivel, S. C. and Coello, C. C.](#ch3.xhtml#R_ref3_18) (2003). On the use of particle swarm optimization with multimodal functions. pp. 1130–1136.
*   [Hassan, R., Cohanim, B., de Weck, O. and Venter, G.](#ch3.xhtml#R_ref3_19) (2005). A comparison of particle swarm optimization and the genetic algorithm. pp. 1–13. *In*: 46th AIAA/ASME/ASCE/ AHS/ASC Structures, Structural Dynamics and Materials Conference, American Institute of Aeronautics and Astronautics.
*   [Helwig, S., Branke, J. and Mostaghim, S.](#ch3.xhtml#R_ref3_20) (2013). Experimental analysis of bound handling techniques in particle swarm optimization. IEEE Trans. Evol. Comput. 17(2): 259–271. [https://doi.org/10.1109/TEVC.2012.2189404](https://doi.org/10.1109/TEVC.2012.2189404).
*   [Higashi, N. and Iba H.](#ch3.xhtml#R_ref3_21) (2003). Particle swarm optimization with gaussian mutation. pp. 72–79. *In*: Proceedings of the IEEE Swarm Intelligence Symphosium 2003. IEEE Press.
*   [Huang, T. and Mohan, A. S.](#ch3.xhtml#R_ref3_22) (2005). A hybrid boundary condition for robust particle swarm optimization. IEEE Antennas Wirel. Propag. Lett. 4: 112–117. [https://doi.org/10.1109/LAWP.2005.846166](https://doi.org/10.1109/LAWP.2005.846166).
*   [Kennedy, J.](#ch3.xhtml#R_ref3_23) (2002). Article swarm performance. pp. 1671–1676. In Proceedings of the 2002 Congress on Evolutionary Computation. CEC'02 (Cat. No. 02TH8600) (Vol. 2). IEEE.
*   [Koopialipoor, M., Armaghani, D. J., Hedayat, A., Marto, A., Gordan, B et al.](#ch3.xhtml#R_ref3_24) (2019). Applying various hybrid intelligent systems to evaluate and predict slope stability under static and dynamic conditions. Soft Computing, 23: 5913–5929.
*   [Kouziokas, G. N.](#ch3.xhtml#R_ref3_25) (2020). A new W-SVM kernel combining PSO-neural network transformed vector and Bayesian optimized SVM in GDP forecasting. Engineering Applications of Artificial Intelligence, 92: 103650. doi: [https://doi.org/10.1016/j.engappai.2020.103650](https://doi.org/10.1016/j.engappai.2020.103650).
*   [Lin, Z. and Zhang, Q.](#ch3.xhtml#R_ref3_26) (2017). An effective hybrid particle swarm optimization with Gaussian mutation. Journal of Algorithms & Computational Technology, 11(3): 271–280.
*   [Michalewicz, Z.](#ch3.xhtml#R_ref3_27) (1998). Genetic Algorithms + Data Structures = Evolution Programs: Springer Science & Business Media.
*   [Miranda, V., Keko, H. and Junior, A. J.](#ch3.xhtml#R_ref3_28) (2008). Stochastic star communication topology in evolutionary particle swarms (EPSO).
*   [Moayedi, H., Moatamediyan, A., Nguyen, H., Bui, X.-N., Bui, D. T. et al.](#ch3.xhtml#R_ref3_29) (2019). Prediction of ultimate bearing capacity through various novel evolutionary and neural network models. Engineering with Computers, 1–17.
*   [Moraglio, A., Chio, C. D. and Poli, R.](#ch3.xhtml#R_ref3_30) (2007, April). Geometric particle swarm optimisation. pp. 125–136. *In*: European Conference on Genetic Programming. Springer, Berlin, Heidelberg.
*   [Mostaghim, S., Mostaghim, S., Halter, W. and Wille, A.](#ch3.xhtml#R_ref3_31) (2006). Linear multi-objective particle swarm optimization. pp. 209–238. *In*: Ajith, A., Crina, G. and Vitorino, R. (eds.). Stigmergic Optimization, vol. 31. Springer, Heidelberg. [https://doi.org/10.1007/978-3-540-34690-6\_9](https://doi.org/10.1007/978-3-540-34690-6_9).
*   [Namous, F., Faris, H., Heidari, A. A., Khalafat, M., Alkhawaldeh, R. S. and Ghatasheh, N.](#ch3.xhtml#R_ref3_32) (2020). Evolutionary and swarm-based feature selection for imbalanced data classification. pp. 231–250. *In*: Evolutionary Machine Learning Techniques. Springer, Singapore.
*   [Nourbakhsh, A., Safikhani, H. and Derakhshan, S.](#ch3.xhtml#R_ref3_33) (2011). The comparison of multiobjective particle swarm optimization and NSGA II algorithm: applications in centrifugal pumps. EnOp, 43: 1095–1113.
*   [Ou, C. and Lin, W.](#ch3.xhtml#R_ref3_34) (2006). Comparison between PSO and GA for parameters optimization of PID controller. pp. 2471–2475. *In*: 2006 International Conference on Mechatronics and Automation, IEEE.
*   [Padhye, N., Deb, K. and Mittal, P.](#ch3.xhtml#R_ref3_35) (2013). Boundary handling approaches in particle swarm optimization. pp. 287–298. *In*: Bansal, J. C., Singh, P. K., Deep, K., Pant, M. and Nagar, A. K. (eds.). Proceedings of Seventh International Conference on Bio-Inspired Computing: Theories and Applications, vol. 1. Springer, India (2013). [https://doi.org/10.1007/978-81-322-1038-2\_25](https://doi.org/10.1007/978-81-322-1038-2_25).
*   [Robinson, J. and Rahmat-Samii, Y.](#ch3.xhtml#R_ref3_36) (2004). Particle swarm optimization in electromagnetics. IEEE Trans. Antennas Propag. 52(2): 397–407. [https://doi.org/10.1109/TAP.2004.823969](https://doi.org/10.1109/TAP.2004.823969).
*   [Sabat, S. L., Udgata, S. K. and Murthy, K. P. N.](#ch3.xhtml#R_ref3_37) (2010). Small signal parameter extraction of MESFET using quantum particle swarm optimization. Microelectronics Reliability, 50(2): 199–206, 2010/02/01/.
*   [Shi, Y. and Eberhart, R.](#ch3.xhtml#R_ref3_38) (1998). A Modified Particle Swarm Optimizer. Paper presented at the 1998 IEEE International Conference On Evolutionary Computation Proceedings. IEEE World Congress on Computational Intelligence (Cat. No. 98TH8360).
*   [Stacey, A., Jancic, M. and Grundy, I.](#ch3.xhtml#R_ref3_39) (2003). Particle swarm optimization with mutation. IEEE Congress on Evolutionary Computation, Dec. 2003, pp. 1425–1430.
*   [Sun, J., Feng, B. and Xu, W.](#ch3.xhtml#R_ref3_40) (2004). Particle swarm optimization with particles having quantum behavior. p. 325–331. *In*: Proceedings of the IEEE Congress on Evolutionary Computation 2004 (IEEE CEC’04), Portland (OR).
*   [Sun, J, Lai, C.-H. and Wu, X.-J.](#ch3.xhtml#R_ref3_41) (2011). Particle Swarm Optimisation: Classical and Quantum Perspectives. CRC Press, Boca Raton.
*   [Tian, Z.](#ch3.xhtml#R_ref3_42) (2021). Modes decomposition forecasting approach for ultra-short-term wind speed. Applied Soft Computing, 107303. doi:[https://doi.org/10.1016/j.asoc.2021.107303](https://doi.org/10.1016/j.asoc.2021.107303).
*   [Van den Bergh, F. and Engelbrecht, A. P.](#ch3.xhtml#R_ref3_43) (2006). A study of particle swarm optimization particle trajectories. Information Science, 176(8): 937–971.
*   [Yeoh, T. W., Zapotecas-Martínez, S., Akimoto, Y., Aguirre, H. E. and Tanaka, K.](#ch3.xhtml#R_ref3_44) (2015, September). Feature selection in gait classification using geometric PSO assisted by SVM. pp. 566–578. *In*: International Conference on Computer Analysis of Images and Patterns. Springer, Cham.
*   [Yin, P.-Y., Glover, F., Laguna, M. and Zhu, J.-X.](#ch3.xhtml#R_ref3_45) (2011). A complementary cyber swarm algorithm. International Journal of Swarm Intelligence Research (IJSIR), 2(2): 22–41.
*   [Zhang, C. and Shao, H.](#ch3.xhtml#R_ref3_46) (2000). An ANN’s evolved by a new evolutionary system and its application. Proceedings of the 39th IEEE Conference on Decision and Control (Cat. No. 00CH37187), 4: 3562–3563.
*   [Zhang, W. J., Xie, X. F. and Bi, D. C.](#ch3.xhtml#R_ref3_47) (2004). Handling boundary constraints for numerical optimization by particle swarm flying in periodic search space. pp. 2307–2311. In:. Proceedings of Congress on Evolutionary Computation.

# Chapter 4 Ant Colony Optimization and Artificial Bee Colony

This chapter is devoted to the most important colony-based optimization algorithms: Ant colony optimization (ACO) and Artificial Bee Colony (ABC). The standard Ant colony optimization (ACO) is presented and some important ant-based algorithms are explained such as: Ant System, Ant Colony System, Rank-based Ant System, Max-min Ant System and Population-based ACO. Then the standard Artificial Bee Algorithm is presented by explaining also the bee colony foraging behavior. Furthermore, advanced aspects are discussed, such as: ABC selection methods including: disruptive selection, tournament selection, exponential and linear rank-based selection and also, boundary handling approaches which can restrict the artificial bee colony movement in the predefined search space.

## Ant colony optimization (ACO)

### Introduction

Ant colony optimization algorithm was inspired by the natural foraging behavior of ants. The ants communicate with each other in order to find the shortest path between their nest and the food resources by using pheromone trails. This is the main idea that was used to build an ant colony-based optimization algorithm in order to solve several kinds of optimization problems ([Chandra Mohan and Baskaran, 2012](#ch4.xhtml#ref4_10); [Colorni et al., 1991](#ch4.xhtml#ref4_11); [Dorigo, 1992](#ch4.xhtml#ref4_13); [Dorigo et al., 1996](#ch4.xhtml#ref4_14); [Dorigo et al., 2006](#ch4.xhtml#ref4_17); [Dorigo and Blum, 2005](#ch4.xhtml#ref4_16); [Dorigo and Gambardella, 1997](#ch4.xhtml#ref4_15); [Blum, 2005](#ch4.xhtml#ref4_6); [López-Ibáñez et al., 2018](#ch4.xhtml#ref4_33)). Several modifications have been developed in order to improve the performance of the originally proposed ACO algorithm such as, chaotic random spare ACO ([Zhao et al., 2021](#ch4.xhtml#ref4_49)), knowledge-based ACO ([Xing et al., 2010](#ch4.xhtml#ref4_45)), parallel ACO ([Pedemonte et al., 2010](#ch4.xhtml#ref4_35)), Rank-Based Version of the Ant system ([Bullnheimer et al., 1997](#ch4.xhtml#ref4_8)), hyper-cube framework ACO ([Blum et al., 2001](#ch4.xhtml#ref4_5)), population-based ACO ([Scheuermann et al. 2004](#ch4.xhtml#ref4_36)).

![Figure 4.1. Illustration of the ant foraging behavior. The ant colony will find the shortest path from the nest to the food communicating with each other by using pheromone trails.](images/fig1_1_B.jpg)

Figure 4.1. Illustration of the ant foraging behavior. The ant colony will find the shortest path from the nest to the food communicating with each other by using pheromone trails.

ACO was initially proposed for discrete optimization problems, such as the travelling salesman problem and routing problems. Later, ant colony optimization was also proposed for continuous optimization problems ([Socha and Dorigo, 2008](#ch4.xhtml#ref4_39)). For example, ACO was used to train a feed-forward neural network ([Socha and Blum, 2007](#ch4.xhtml#ref4_38)). Furthermore, ACO algorithm was applied on several kinds of problems and domains such as, routing in ad hoc wireless networks ([Sharvani et al., 2012](#ch4.xhtml#ref4_37)), automatic pressurized water reactor loading pattern design ([Lin and Lin, 2012](#ch4.xhtml#ref4_32)), construction site layout planning ([Lam et al., 2007](#ch4.xhtml#ref4_31)), solving symmetric and asymmetric TSPs ([Gambardella and Doringo, 1996](#ch4.xhtml#ref4_19)), strongly constrained optimization ([Maniezzo and Milandri, 2002](#ch4.xhtml#ref4_34)).

ACO algorithm use pheromone updates, evaporation, and daemon (optional). ACO can optimize a problem by using an updated pheromone trail and directing the artificial ants in the search space according to the transition probability and the total pheromone in the area.

The continuous ant colony optimization ([Socha and Dorigo, 2008](#ch4.xhtml#ref4_39)) applies both local and global search. The local artificial ants move toward the area with the best solution  according to the transition probability of area *a*, expressed by the equation:

(4.1)  
$$P\_{a}\\left( t \\right) = \\frac{t\_{a}\\left( t \\right)}{\\sum\_{j = 1}^{n}{t\_{j}\\left( t \\right)}}$$  

where,

*   *t[a]*(*t*) represents the total pheromone in *a* area
*   *n* represents the total number of ants.

The pheromone is updated by using the following mathematical equation:

(4.2)  
*t*[*i*](*t*+1) = (1−*r*)*t*[*i*](*t*)  

where *r* represents the pheromone evaporation rate.

In the following sections, the most important ant-based algorithms are examined.

### Ant system (AS)

The Ant System algorithm was proposed by [Colorni et al. (1991](#ch4.xhtml#ref4_11)). This approach uses locally interacting simple agents called ants which deposit pheromone when they travel from a node *i* (Or town in the Travelling Salesman Problem) to a node *j* ()*.*

The intensity on the (i,j) trail path according to the amount of pheromone is defined by the equation:

(4.3)  
*τ*[*i**j*](*t*) = (1−*p*)*τ*[*i**j*](*t*−1) + *Δ**τ*[*i**j*](*t*)  

*   where τ[ij](t) represents the amount of pheromone on the (i,j) path at time t
*   ρ denotes the evaporation coefficient and 0 < ρ < 1
*   Δτ[ij](t) denotes the increase in the pheromone amount on the (i,j) path between time instants (t−1) and t.

The Δ*τ[ij]*(*t*) represents the total pheromone increase by all the ants which have travelled in this time interval and is calculated by the equation:

(4.4)  
$$\\Delta\\tau\_{ij}\\left( t \\right) = {\\sum\\limits\_{k}{\\Delta\\tau\_{ijk}\\left( t \\right)}}$$  

where Δτ[*ijk*](*t*) is the amount of pheromone deposited by the k-th ant on the (i,j) path in the time step.

The transition probability regarding the choice from a node *i* (e.g., town in the TSP) to another node *j*, by an ant at node *i* at time t is defined by the equation:

(4.5)  
$$p\_{ij}\\left( t \\right) = \\frac{\\left\\lbrack {\\tau\_{ij}\\left( t \\right)} \\right\\rbrack^{a}\\left\\lbrack \\eta\_{ij} \\right\\rbrack^{\\beta}}{\\sum\\limits\_{z \\in N\_{i}}{\\left\\lbrack {\\tau\_{il}\\left( t \\right)} \\right\\rbrack^{\\alpha}\\left\\lbrack \\eta\_{iz} \\right\\rbrack^{\\beta}}}$$  

where,

*   α and β are parameters used to let the user to set the relative importance of trail versus visibility
*   η[ij] represents the *visibility* parameter, the inverse of the distance between node i and node j, calculated as: $\\eta\_{ij} = \\frac{1}{d\_{ij}}$

The visibility parameter η[ij] was introduced in order to enhance the efficiency of the optimization algorithm by enabling the nearest nodes to be selected with a higher probability than the distant nodes.

[Colorni et al. (1991](#ch4.xhtml#ref4_11)), proposed three different methods for calculating the value of *Δ[τijk]*(*t*), named as ANT-density, ANT-quantity and ANT-cycle. In the Ant Density and the Ant Quantity models the pheromone update is applied when an ant moves from one location to another. In the Ant Cycle model, the pheromone update is applied when all ants have finished their tour.

In the ANT-quantity model ([Colorni et al., 1991](#ch4.xhtml#ref4_11)) a constant pheromone quantity Q[1] is left when the ant travels from *i* to *j* and in the ANT-density model when an ant travels from *i* to *j* leaves pheromone quantity units Q[2] for each unit of length. The value of the *Δτ[ijk]*(*t*) is given by the equation:

(4.6)  
$$\\Delta\\tau\_{ijk}\\left( t \\right) = \\left\\{ \\begin{array}{l} {\\frac{Q\_{1}}{d\_{ij}},if\\left( {i,j} \\right) \\in T\_{k},} \\\\ {0,otherwise} \\\\ \\end{array} \\right.$$  

where *d[ij]* is the distance between i and j, *T[k]* represents the path finished by the k-th ant and *Q*[1] is a constant. In the Ant quantity model, the path length distance *d[ij]* between i and j is taken into account.

In the *Ant density model*, the *Q*[2] constant value, shows that the final pheromone left on the path is proportional to the number of ants selecting it. This model doesn’t take into account the path length distance *d[ij]*. The value of *Δτ[ijk]*(*t*) is given by the equation:

(4.7)  
$$\\Delta\\tau\_{ijk}\\left( t \\right) = \\left\\{ \\begin{array}{l} {Q\_{2},if\\left( {i,j} \\right) \\in T\_{k},} \\\\ {0,otherwise,} \\\\ \\end{array} \\right.$$  

In the *ant cycle model (Or online delayed)*, the pheromone update is implemented when all the ants have finished their tour.

The updating of the trail value of the next time step *τ[ij]*(*t* + 1) can be calculated by the equation:

(4.8)  
*τ*[*i**j*](*t*+1) = *p**τ*[*i**j*](*t*) + *Δ**τ*[*i**j**k*](*t*)  

The value of *Δτ[ijk]*(*t*) after a complete tour is calculated by:

(4.9)  
$$\\Delta\\tau\_{ijk}\\left( t \\right) = \\left\\{ \\begin{array}{l} {\\frac{Q\_{3}}{L\_{k}},if\\left( {i,j} \\right) \\in T\_{k}} \\\\ {0,otherwise} \\\\ \\end{array} \\right.$$  

where,

*   *T[k]* represents the path finished by the k-th ant
*   *L[k]* represents the path length
*   Q[3] represents a constant.

The ANT-cycle model has showed the best performance compared to the other models.

The ant system algorithm is summarized in the following pseudo code.

where N represents the number of total iterations.

### Ant colony system (ACS)

The basic differences of Ant colony system compared to the Ant system are ([Dorigo and Gambardella, 1997](#ch4.xhtml#ref4_15)): the state transition rule is altered in order to accomplish a balance between exploring new paths compared to the already accumulated ant knowledge, the local pheromone updating rule is calculated when artificial ants create a tour and the global pheromone updating rule is applied only to paths of the best tour.

#### State transition rule

The state transition rule is developed by using two different strategies, exploitation and exploration. The exploitation strategy always selects the path with the greatest amount of pheromone visibility and intensity. The exploration process is a stochastic rule according to Eq. 4.5. When an ant decides which node (Or city) *j* to visit next, it chooses the node (Or city) to move to defined by the following rule:

(4.10)  
$$j = \\left\\{ \\begin{array}{l} {\\arg\\max\\limits\_{z \\in N\_{i}}\\tau\_{iz}\\left( t \\right) \\cdot \\left( \\eta\_{iz} \\right)^{\\alpha},ifq \\leq q\_{0}\\left( {\\exp loitation} \\right)} \\\\ {S,otherwise\\left( {\\exp loration} \\right)} \\\\ \\end{array} \\right.$$  

where,

*   q represents a pre-defined variable which expresses the distribution ratio of the two strategies
*   q represents a uniformly and randomly generated value distributed in the interval \[0,1\]
*   S expresses the transition probability rule calculated by the Eq. 4.5.

*Global pheromone updating rule*

In the Ant colony system, in the optimization process, only the ant with the globally best value is permitted to deposit pheromone on the path. This makes the ant search more focused: ants search in the near neighborhood of the best tour found in the current iteration. The Global updating is implemented when all the ants have completed their tours in the search space. The pheromone amount is updated by using the following updating rule:

(4.11)  
*τ*[*i**j*](*t*) = (1−*a*) ⋅ *τ*[*i**j*](*t*−1) + *a* ⋅ *Δ**τ*[*i**j*](*t*)  

where,

(4.12)  
$$\\Delta\\tau\_{ij} = \\left\\{ \\begin{array}{l} {\\left( L\_{Global} \\right)^{- 1},if\\left( {i,j} \\right) \\in T\_{G}} \\\\ {0,otherwise} \\\\ \\end{array} \\right.$$  

where,

*   0 & α & 1 represents the global pheromone decay parameter
*   *L[Global]* represents the length of the globally best ant tour from the initial start point.

*Local pheromone updating rule*

After finishing a tour, the pheromone level is updated on each ant path according to the equation:

(4.13)  
*τ*[*i**j*](*r*,*s*) = (1−*p*) ⋅ *τ*[*i**j*](*r*,*s*) + *p* ⋅ *Δ**τ*[*i**j*](*r*,*s*)  

where,

*   0 & r & 1 represents the local decay rate parameter.
*   ρ denotes the evaporation coefficient rate and 0 & ρ & 1.

The value of Δ*τ[ij]*(*t*) is either specified based on the results of Q-learning or assigned the value of the initial pheromone level.

### Rank-based ant system (RB-AS)

Rank-based Ant System (RB-AS) was proposed by [Bullnheimer et al. (1999](#ch4.xhtml#ref4_9)). It basically consists of an ant-based solution development and pheromone update in every iteration.

According to the proposed method, during the solution search, an artificial ant assembles the solution as a sequence of solution components by using probabilistic theory. At every step, the selection of a solution from a set of probable solutions is produced by using the transition probability which is calculated by the equation:

(4.14)  
$$p\\left( {i,s} \\right) = \\frac{\\left\\lbrack {\\tau\\left( {i,s} \\right)} \\right\\rbrack^{\\alpha}\\left\\lbrack {\\eta\\left( {i,s} \\right)} \\right\\rbrack^{\\beta}}{\\sum\_{k}{\\left\\lbrack {\\tau\\left( {i,k} \\right)} \\right\\rbrack^{\\alpha}\\left\\lbrack {\\eta\\left( {i,k} \\right)} \\right\\rbrack^{\\beta}}}\\forall s \\in N\\left( s \\right)$$  

where,

> *p* (*i*, *s*) represents the probability of choosing a solution for position *i* from the solution set
> 
> *   *N*(*s*), contains the solutions to be placed at each solution development step
> *   *τ*(*i*, *s*) represents the pheromone concentration of solutions at position
> *   *η*(*i*, *s*) represents an optional weighting function.
> *   *α* and *β* represent the weights of the pheromone concentration (*τ*) and heuristic information (*η*).

The pheromone update rule is composed of two parts, the pheromone evaporation and the pheromone increase. The pheromone evaporation decreases all the pheromone concentrations. The best solution is the one with the highest pheromone concentration. The pheromone increase permits the solutions from the current or earlier iterations to be used to increase the solution of the component pheromone concentration. The pheromone update can be calculated by the following equation:

(4.15)  
$$\\left. \\tau\\left( {i,s} \\right)\\leftarrow\\left( {1 - p} \\right)\\tau\\left( {i,s} \\right) + p{\\sum\\limits\_{l \\in S\_{update}}{\\Delta\\tau\_{l}\\left( {i,s} \\right)}}\\forall s \\in N\\left( s \\right) \\right.$$  

(4.16)  
$$\\Delta\\tau\_{l}\\left( {i,s} \\right) = \\left\\{ \\begin{array}{l} {\\frac{w\_{1}}{Q\_{1}}if\\left( {i,s} \\right) \\in l} \\\\ {0if\\left( {i,s} \\right) \\notin l} \\\\ \\end{array} \\right.$$  

where,

*   *τ*(*i*, *s*) represents the pheromone concentration,
*   0 & *ρ* ⩽ 1 represents the evaporation rate,
*   *Q[l]* represents the quality function value,
*   *w[l]* represents the weighting factor of the quality function value,
*   *S[update]* represents a solution set used to update the solution components’ pheromone.

### Max-min ant system (MMAS)

Max-min Ant System was proposed by [Stützle and Hoos (2000](#ch4.xhtml#ref4_40)). It is based on the idea of limiting the range of the pheromone in the main ant algorithm. The artificial ants deposit pheromones on the optimal route or on the optimal route in the current iteration but this can lead to an excessive growth of pheromones. To avoid this excessive growth, Max-min Ant System limits the range of values of pheromones within the interval of the lower and the upper bound \[*τ*[lb] , *τ* [ub]\]. Consequently, the Max-Min Ant System algorithm, updates the pheromones according to the equation:

(4.17)  
*τ*[*i*, *j*] = \[(1−*ρ*)*τ*[*i*, *j*]+*Δ**τ*[*i*, *j*]^(*b**e**s**t*)\][*τ*[*l**b*]]^(*τ**u**b*)  

where,

*   Δ*τ^(best)[i,j]* represents the total quantity of pheromone deposited on the *i*, *j* route by the optimal ant
*   *τ[ub]* represents the upper bound of pheromones
*   *τ[lb]* represents the lower bound of pheromones, [The] \[ \]^(*x* τ)[τ]^(*ub*[*lb*]) is estimated by the following equation:

(4.18)  
$$\\left\\lbrack x \\right\\rbrack\_{\\tau\_{lb}}^{\\tau\_{ub}} = \\left\\{ \\begin{matrix} {ub} & {x > ub} \\\\ {lb} & {x < lb} \\\\ x & \\text{otherwise} \\\\ \\end{matrix} \\right.$$  

The total quantity of pheromone deposited by the best ant is estimated by the following equation:

(4.19)  
$$\\Delta\\tau\_{ij}^{best} = \\left\\{ \\begin{matrix} \\frac{1}{L\_{best}} & {\\text{if}\\left( \\text{i,j} \\right) \\in \\text{Best-solution}} \\\\ 0 & \\text{otherwise} \\\\ \\end{matrix} \\right.$$  

where *L[best]* represents the distance of the best route.

The initial level of the pheromone is set to *τ*[max] to make the artificial ants search for multiple optimal routes at the initial stage. Also, when the algorithm does not find a better path for a predefined number of iterations, the pheromone levels are reinitialized so as to reduce the prematurity potential risk.

### Population-based ACO

In regular ACO, the solutions found by the artificial ants are discarded when the pheromone update is implemented. In the PB-ACO algorithm the solutions are kept and eventually the solutions are removed according to a rule (age, quality, prob, elitism) and the pheromone values are updated in the table.

The population update strategies proposed by Guntch (2004) and Guntch and Middendorf (2002) are summarized as: the age-based strategy, the quality-based strategy, the prob strategy and the elitist-based strategy.

**Age-based strategy.** In this strategy the oldest solution is removed after *k* iterations and a new candidate solution replaces it. This means that every solution has an influence for exactly *k* iterations.

**Quality-based strategy.** In this strategy, the best k solutions found for all past iterations are stored (not only the best solutions of the last k iterations). If the solution of a current iteration is better than the previous best then it is replaced.

**Prob strategy.** The prob strategy improves the *quality* strategy by introducing a probabilistic selection of which element from *P* unified with the candidate solution will be discarded and will not be part of *P* in the next algorithm iteration. Otherwise, the artificial ants would be trapped to search in a small section of the search space.

**Elitism strategy.** In this strategy, elitism is implemented on the population based ACO algorithm, so the update strategy used by the algorithm will be applied only to the population of the elitist solutions (best solutions found so far). The elitist solution is updated only when a better candidate solution is found.

## Artificial bee colony (ABC)

### Bee colony foraging behavior

Several researchers have studied the honeybee colony foraging behavior. They have developed a model by expressing this behavior by the reaction–diffusion equations ([Tereshko, 2000](#ch4.xhtml#ref4_42); [Tereshko and Lee, 2002](#ch4.xhtml#ref4_43); [Tereshko and Loengarov, 2005](#ch4.xhtml#ref4_44)). This model which expresses the collective intelligence of honeybee swarms is composed of three essential factors: food sources, employed foragers, and unemployed foragers. [Tereshko and Loengarov (2005](#ch4.xhtml#ref4_44)) explain these three essential factors of their proposed model:

**Food Sources:** The food source is very valuable to an insect. The criteria of the forager bee for selecting a food source are basically: how close is the food source to the nest, concentration of energy and how difficult it is for the bee to extract this energy. [Tereshko and Loengarov (2005](#ch4.xhtml#ref4_44)) group all these parameters with the term “profitability” of a food source, a single quantity parameter.

**Employed foragers:** The employed forager bees are related to a specific food source which they are currently exploiting. The employed foragers carry information about this specific source, regarding the distance and the direction from the nest, and also about the profitability of the food source. The employed forager bees share this information with a specific probability which depends on the profitability of the food source. If the profitability of the food source is bigger, then the probability of the honeybee to do a waggle dance and share the information will be higher.

**Unemployed foragers:** The unemployed foragers are searching for food sources in order to exploit them. There are two types of unemployed forager bees, the scout bees, who are responsible for searching the closer environment around the nest for new food sources and onlooker bees just wait in the nest and find a new food source according to the information shared by the employed forager bees.

### ABC algorithm

The artificial bee colony (ABC) algorithm was proposed by [Karaboga in 2005](#ch4.xhtml#ref4_25). Since then, several variations of the original ABC algorithm have been proposed such as, Chaotic ABC ([Xu et al., 2010](#ch4.xhtml#ref4_24)), ABC for clustering ([Zhang et al., 2010](#ch4.xhtml#ref4_47)), tournament selection based ABC algorithm with elitist strategy ([Zhang et al., 2014](#ch4.xhtml#ref4_48)), global best-guided ABC ([Zhu and Kwong, 2010](#ch4.xhtml#ref4_50)), improved ABC ([Kang et al., 2010](#ch4.xhtml#ref4_24)), ABC algorithm based on Boltzmann selection policy ([Ding and Feng, 2009](#ch4.xhtml#ref4_12)), ABC with new versions of onlooker bee ([Awadallah et al., 2019](#ch4.xhtml#ref4_3)). The artificial bee colony can be used to find solutions in constrained and unconstrained optimization problems ([Karaboga and Basturk, 2007](#ch4.xhtml#ref4_26); [Sulaiman et al., 2012](#ch4.xhtml#ref4_41)). In the artificial bee colony (ABC) algorithm, the optimization process was inspired by the intelligence of the natural foraging behavior of bee colonies. In the proposed ABC algorithm, three kinds of artificial bees are employed to search for food sources, employed bee, onlooker bee, and scout bee. Correspondingly, there are three stages according to the bee kinds, employed bee stage, onlooker bee stage, and scout bee stage. A food source represents a candidate solution to an optimization problem.

![Figure 4.2. Artificial bee colony taxonomy.](images/fig4_2_B.jpg)

Figure 4.2. Artificial bee colony taxonomy.

**Initialization stage:** The ABC algorithm begins the search process by setting an initial bee population randomly distributed SN solutions (food source places). SN represents the size of the population. Each food source represents a solution and is initialized by using the following equation:

(4.20)  
*x*[*i*, *j*] = *x*[*j*]^(min) + *r**a**n**d*(0,1) ⋅ (*x*[*j*]^(max)−*x*[*j*]^(min))  

where,

*   *x[i,j]* represents the solution for the i[th] employed artificial bee in the j[th] dimension
*   *X*[1] = (*x[i]*[,1], *x[i]*[,2],..., *x[i,D]*) represents the *i*[th] food source,
*   *D* represents the dimension size of the optimization problem.
*   \[*x^(min)[j]* , *x^(max)[j]* \] represents the upper and lower bounds for the *j*[th] dimension.
*   *rand*(0, 1) represents a random number uniformly distributed in the range \[0, 1\].

**Employed bee stage.** In this stage, the swarm of employed bees are searching for food resources in order to make honey. The employed artificial bees create a new food source *v[i,j]* (new solution) for each *x[i,j]* parent food source according to the following equation:

(4.21)  
*v*[*i*, *j*] = *x*[*i*, *j*] + *ϕ*[*i*, *j*] ⋅ (*x*[*i*, *j*]−*x*[*k*, *j*])  

where,

*   *v[i,j]* is a new solution for
*   *x[i,j]* represents the solution for the i[th] employed artificial bee in the j[th] dimension
*   *j* represents a randomly selected dimension from the set \[1,…D\].
*   *ϕ[i,j]* represents a random number uniformly distributed in the range \[–1, 1\].

The set *V[i]* = (*v[i]*[,1], *v[i]*[,2],..., *v[i,D]*) represents the *i*th new food source. *X[k]* = (*x[k]*[,1], *x[k]*[,2],..., *x[k,D]*) represents a parent food source randomly chosen.

The fitness function value for a food source is estimated by the following equation:

(4.22)  
$$fitness\\left( X\_{i} \\right) = \\left\\{ \\begin{array}{l} {\\frac{1}{1 + f\\left( X\_{i} \\right)}\\text{if}\\text{f}\\left( X\_{i} \\right) \\geq 0} \\\\ {1 + \\left| {f\\left( X\_{i} \\right)} \\right|\\text{otherwise}} \\\\ \\end{array} \\right.$$  

where,

*   *fitness*(*X[i]*) is the fitness function value of the food source.
*   *f*(*X[i]*) is a specific objective function.
*   | *f*(*X[i]*)| denotes the absolute value of the specific objective function.

**Onlooker bee stage.** In this stage, a swarm of SN onlooker bees is sent to select a food source based on the its quality. If the quality of food sources is high then they attract more onlooker bees, otherwise if the quality is low then the onlooker bees are not attracted. The quality of food sources is determined according to the fitness function of the solutions. The onlooker bees receive information by the employed bees about the food sources, and then the onlooker bees choose the high-quality food sources to search and produce new food sources (new solutions) based on a selection method (e.g., roulette selection method). The selection probability is calculated by the equation:

(4.23)  
$$p\_{i} = \\frac{fitness\\left( X\_{i} \\right)}{\\sum\\limits\_{j = 1}^{SN}{fitness\\left( X\_{i} \\right)}}$$  

where,

*   *p[i]* is the selection probability of the ith solution for the food source
*   *fitness*(*X[i]*) is the fitness value of the ith solution

**Scout bee stage.** The role of scout bees is to reinitialize the food sources. When a food source has not been improved for an amount of time which can be set as a threshold value parameter, then the food source should be abandoned and the scout bees are searching for new food sources. The abandoned food source (solution) is replaced by a randomly created new food source (new solution) by using the equation (4.20).

### Selection methods

The selection method of the individuals according to their fitness values in the search space is very important in the ABC algorithm. The most suitable selection method can improve the efficiency of the algorithm ([Bao and Zeng, 2009](#ch4.xhtml#ref4_4); [Kumar et al., 2016](#ch4.xhtml#ref4_29)).

#### Disruptive selection

This method uses a normalized-by-mean fitness function in order to improve the population diversity ([Kuo and Hwang, 1996](#ch4.xhtml#ref4_30)). The selection probability is calculated by the equation:

(4.24)  
$$p\_{i} = \\frac{fit\_{i}}{\\sum\_{j = 1}^{N}{fit\_{j}}}$$  

where,

*   *fit[i]*, represents the fitness value of the i^(th) solution
*   *P[i]* represents the selection probability of the i^(th) solution.

The fitness function is calculated by the equation:

(4.25)  
$$fit\_{i} = \\left| {f\_{i} - \\overline{f}} \\right|$$  

where,

*   *f* [i] is the objective function
*   *f̅* is the average of the objective values for the individuals in the population.

This method was implemented by several researches to improve the optimization results ([Alzaqebah and Abdullah, 2011](#ch4.xhtml#ref4_2); [Karaboga, 2009](#ch4.xhtml#ref4_27)). For example, [Alzaqebah and Abdullah (2011](#ch4.xhtml#ref4_2)), have used disruptive selection to calculate the selection probability of the onlooker bees.

#### Tournament selection

This selection method randomly selects k individuals from the population, where k is taken as the tournament size and the fitness values of the individuals are compared. A score is assigned to the one with the best fitness value. The individuals are chosen according to the probability calculated by the following equation:

(4.26)  
$$p\_{i} = \\frac{S\_{i}}{\\sum\_{i = 1}^{K}S\_{i}}$$  

where,

*   S represents the score assigned to the individual with the best fitness value
*   k represents the number of individuals from the population

#### Linear rank selection

In this method, the individuals are ranked according to their fitness values. They are ranked from the worst fitness value to the best fitness value. The selection probability is calculated according to the equations ([Aiguo and Jiren, 1999](#ch4.xhtml#ref4_1); [Bao and Zeng, 2009](#ch4.xhtml#ref4_4)):

(4.27)  
$$p{}\_{k} = \\frac{1}{n} + a\\left( t \\right)\\frac{n + 1 - 2k}{n\\left( {n + 1} \\right)}k = \\left( {1,2, \\cdot \\cdot \\cdot ,n} \\right)$$  

(4.28)  
$$a\\left( t \\right) = 0.2 + \\frac{3t}{4N}t = \\left( {1,2, \\cdot \\cdot \\cdot ,N} \\right)$$  

where,

*   *a*(*t*) represents a self-adaptive parameter
*   *N* represents the maximum iterations.

#### Exponential rank selection

In this method, the individuals are ranked according to the exponential weighing of ranked individuals and the selection probability is calculated according to the equation:

(4.29)  
$$p\_{i} = \\frac{c - 1}{c^{N} - 1}c^{N - 1},i \\in \\left\\{ {1,....,N} \\right\\}$$  

where indicative parameter c & 1.

### Boundary handling approaches

Several boundary handling approaches have been proposed. These techniques are very important since they can restrict the artificial bee colony movement in the predefined search space. In the previous chapter several boundary handlings have been presented in detail for PSO algorithm such as: nearest or boundary or absorb, hyperbolic method, infinity or invisible wall, random, random-half, periodic, exponential, mutation, reflect methods, random damping. These methods can also be applied in the ABC algorithm.

Furthermore, there are other approaches that have been proposed by researchers for the ABC algorithm. [Brajevic (2015](#ch4.xhtml#ref4_7)), proposed the application of a mechanism used by [Kukkonen and Lampinen (2006](#ch4.xhtml#ref4_28)) in generalized differential evolution. [Brajevic (2015](#ch4.xhtml#ref4_7)), used the [Kukkonen and Lampinen (2006](#ch4.xhtml#ref4_28)) mechanism as a boundary constraint-handling method. During the algorithm process of the mutation and crossover, the trial vector *u[j,i,G]* is compared with the old vector *x[j,i,G].*This correction is based on the following mathematical equation which is used in the case of boundary violation values which were reflected back from the violated boundary by using following rule:

(4.30)  
$$u\_{j,i,G} = \\left\\{ \\begin{array}{l} {2 \\cdot x\_{j}^{low} - u\_{ji},\\text{if}\\text{u}\_{j,i,G} < x\_{j}^{low}} \\\\ {2 \\cdot x\_{j}^{up} - u\_{ji},\\text{if}\\text{u}\_{j,i,G} < x\_{j}^{up}} \\\\ {u\_{j,i,G},\\text{otherwise}} \\\\ \\end{array} \\right.$$  

where,

*   *u[j,i,G]* represents the trial vector for the variable *j* of the candidate solution *i*,
*   *x[j]^(low)* represents the lower bound of the decision variable *x*
*   *x[j]^(up)* represents the upper bound of the decision variable *x[j]*
*   *G* represents the generation

## References

*   [Aiguo, S. and Jiren, L.](#ch4.xhtml#R_ref4_1) (1999). A ranking based adaptive, evolutionary operator genetic algorithm \[J\]. ACTA, Electronica Sinica, 27(1): 85–88.
*   [Alzaqebah, M. and Abdullah, S.](#ch4.xhtml#R_ref4_2) (2011). Hybrid Artificial Bee Colony Search Algorithm Based on Disruptive Selection for Examination Timetabling Problems. Paper presented at the Combinatorial Optimization and Applications, Berlin, Heidelberg.
*   [Awadallah, M. A., Al-Betar, M. A., Bolaji, A. L. a., Alsukhni, E. M. et al.](#ch4.xhtml#R_ref4_3) (2019). Natural selection methods for artificial bee colony with new versions of onlooker bee. Soft Computing, 23(15): 6455–6494. doi: [10.1007/s00500–018–3299–2](http://doi.org/10.1007/s00500%E2%80%93018%E2%80%933299%E2%80%932).
*   [Bao, L. and Zeng, J. C.](#ch4.xhtml#R_ref4_4) (2009, August). Comparison and analysis of the selection mechanism in the artificial bee colony algorithm. pp. 411–416. In: 2009 Ninth International Conference on Hybrid Intelligent Systems (Vol. 1). IEEE.
*   [Blum, C., Roli, A. and Dorigo, M.](#ch4.xhtml#R_ref4_5) (2001). HC–ACO: The hyper-cube framework for ant colony optimization. pp. 399–403. In: Proceedings of MIC’2001—Metaheuristics International Conference (Vol. 2). Porto, Portugal, July 16–20, 2001.
*   [Blum, C.](#ch4.xhtml#R_ref4_6) (2005). Ant colony optimization: Introduction and recent trends. Physics of Life Reviews, 2(4): 353–373. doi:[https://doi.org/10.1016/j.plrev.2005.10.001](https://doi.org/10.1016/j.plrev.2005.10.001).
*   [Brajevic, I.](#ch4.xhtml#R_ref4_7) (2015). Crossover-based artificial bee colony algorithm for constrained optimization problems. Neural Computing and Applications, 26(7): 1587–1601. doi: [10.1007/s00521–015–1826-y](http://doi.org/10.1007/s00521%E2%80%93015%E2%80%931826-y).
*   [Bullnheimer, B., Hartl, R. F. and Strauss, C.](#ch4.xhtml#R_ref4_8) (1997). A New Rank-Based Version of the Ant System—A Computational Study. Technical report. Austria: Institute of Management Science, University of Vienna, Austria.
*   [Bullnheimer, B., Hartl, R. F. and Strauss, C.](#ch4.xhtml#R_ref4_9) (1999). An improved ant System algorithm for the vehicle Routing Problem. Annals of Operations Research, 89: 319–328.
*   [Chandra Mohan, B. and Baskaran, R.](#ch4.xhtml#R_ref4_10) (2012). A survey: Ant colony optimization based recent research and implementation on several engineering domains. Expert Systems with Application, 39: 4618–4627.
*   [Colorni, A., Dorigo, M. and Maniezzo, V.](#ch4.xhtml#R_ref4_11) (1991, December). Distributed optimization by ant colonies. pp. 134–142. In: Proceedings of the First European Conference on Artificial Life (Vol. 142).
*   [Ding, H. J. and Feng, Q. X.](#ch4.xhtml#R_ref4_12) (2009). Artificial bee colony algorithm based on Boltzmann selection policy. Computer Engineering and Applications, 45(31): 53–55.
*   [Dorigo, M.](#ch4.xhtml#R_ref4_13) (1992). Optimization, Learning, and Natural Algorithms. Ph.D. Thesis. Politecnico di Milano, Milan, Italy.
*   [Dorigo, M., Maniezzo, V. and Colorni, A.](#ch4.xhtml#R_ref4_14) (1996). Ant system: optimization by a colony of cooperating agents. IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), 26(1): 29–41.
*   [Dorigo, M. and Gambardella, L. M.](#ch4.xhtml#R_ref4_15) (1997). Ant colony system: a cooperative learning approach to the traveling salesman problem. IEEE Transactions on Evolutionary Computation, 1(1): 53–66.
*   [Dorigo, M. and Blum, C.](#ch4.xhtml#R_ref4_16) (2005). Ant colony optimization theory: A survey. Theoretical Computer Science, 344(2–3): 243–278.
*   [Dorigo, M., Birattari, M. and Stuzle, T.](#ch4.xhtml#R_ref4_17) (2006). Ant Colony Optimisation. Artificial Ants as a computational Intelligence Technique. Technical Report, IRDIA, 1–12, 1781–3794, 2006.
*   Dorigo, M., Birattari, M. and Stutzle, T. (2006). Ant colony optimization. IEEE Computational Intelligence Magazine, 1(4): 28–39.
*   [Gambardella, L. M. and Dorigo, M.](#ch4.xhtml#R_ref4_19) (1996, May). Solving symmetric and asymmetric TSPs by ant colonies. pp. 622–627. In: Proceedings of IEEE International Conference on Evolutionary Computation. IEEE.
*   Gao, W., Liu, S. and Huang, L. (2012). A global best artificial bee colony algorithm for global optimization. Journal of Computational and Applied Mathematics, 236(11): 2741–2753.
*   Guntsch, M. and Middendorf, M. (2002, April). A population-based approach for ACO. pp. 72–81. In: Workshops on Applications of Evolutionary Computation. Springer, Berlin, Heidelberg.
*   Guntsch, M. and Middendorf, M. (2002, September). Applying population based ACO to dynamic optimization problems. pp. 111–122. In: International Workshop on Ant Algorithms. Springer, Berlin, Heidelberg.
*   Guntsch, M. (2004). Ant Algorithms in Stochastic and Multi-criteria Environments (Doctoral dissertation, Karlsruhe Institute of Technology).
*   [Kang, F., Li, J., Li, H., Ma, Z., Xu, Q. et al.](#ch4.xhtml#R_ref4_24) (2010, May). An improved artificial bee colony algorithm. pp. 1–4. In: 2010 2nd International Workshop on Intelligent Systems and Applications. IEEE.
*   [Karaboga, D.](#ch4.xhtml#R_ref4_25) (2005). An Idea Based on Honey Bee Swarm for Numerical Optimization (Vol. 200, pp. 1–10). Technical report-tr06, Erciyes University, Engineering Faculty, Computer Engineering Department.
*   [Karaboga, D. and Basturk, B.](#ch4.xhtml#R_ref4_26) (2007). A powerful and efficient algorithm for numerical function optimization: artificial bee colony (ABC) algorithm. Journal of Global Optimization, 39(3): 459–471.
*   [Karaboga, N.](#ch4.xhtml#R_ref4_27) (2009). A new design method based on artificial bee colony algorithm for digital IIR filters. Journal of the Franklin Institute, 346(4): 328–348.
*   [Kukkonen, S. and Lampinen, J.](#ch4.xhtml#R_ref4_28) (2006, July). Constrained real-parameter optimization with generalized differential evolution. pp. 207–214. In: 2006 IEEE International Conference on Evolutionary Computation. IEEE.
*   [Kumar, A., Kumar, D. and Jarial, S. K.](#ch4.xhtml#R_ref4_29) (2016). A comparative analysis of selection schemes in the artificial bee colony algorithm. Computación y Sistemas, 20(1): 55–66.
*   [Kuo, T. and Hwang, S. Y.](#ch4.xhtml#R_ref4_30) (1996). A genetic algorithm with disruptive selection. IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), 26(2): 299–307.
*   [Lam, K. C., Ning, X. and Ng, T.](#ch4.xhtml#R_ref4_31) (2007). The application of the ant colony optimization algorithm to the construction site layout planning problem. Construction Management and Economics, 25(4): 359–374. doi: [10.1080/01446190600972870](http://doi.org/10.1080/01446190600972870).
*   [Lin, C. and Lin, B.-F.](#ch4.xhtml#R_ref4_32) (2012). Automatic pressurized water reactor loading pattern design using ant colony algorithms. Annals of Nuclear Energy, 43: 91–98. doi:[https://doi.org/10.1016/j.anucene.2011.12.002](https://doi.org/10.1016/j.anucene.2011.12.002).
*   [López-Ibáñez, M., Stützle, T. and Dorigo, M.](#ch4.xhtml#R_ref4_33) (2018). Ant colony optimization: a component-wise overview. pp. 371–407. In: Martí, R., Pardalos, P. M. and Resende, M. G. C. (Eds.), Handbook of Heuristics. Cham: Springer International Publishing.
*   [Maniezzo, V. and Milandri, M.](#ch4.xhtml#R_ref4_34) (2002). An ant-based framework for very strongly constrained problems. In: Dorigo, M., Di Caro, G. and Sampels, M. (eds.). Proceedings of ANTS 2002—From Ant Colonies to Artificial ANTS: Third International.
*   [Pedemonte, M., Nesmachnow, S. and Cancela, H.](#ch4.xhtml#R_ref4_35) (2011). A survey on parallel ant colony optimization. Applied Soft Computing, 11(8): 5181–5197.
*   [Scheuermann, B., So, K., Guntsch, M., Middendorf, M., Diessel, O. et al.](#ch4.xhtml#R_ref4_36) (2004). FPGA implementation of population-based ant colony optimization. Applied Soft Computing.
*   [Sharvani, G. S., Ananth, A. G. and Rangaswamy, T. M.](#ch4.xhtml#R_ref4_37) (2012). Analysis of different pheromone decay techniques for ACO based routing in ad hoc wireless networks. International Journal of Computer Applications, 56(2).
*   [Socha, K. and Blum, C.](#ch4.xhtml#R_ref4_38) (2007). An ant colony optimization algorithm for continuous optimization: application to feed-forward neural network training. Neural Computing and Applications, 16(3): 235–247.
*   [Socha, K. and Dorigo, M.](#ch4.xhtml#R_ref4_39) (2008). Ant colony optimization for continuous domains. European Journal of Operational Research, 185(3): 1155–1173.
*   [Stützle, T. and Hoos, H. H.](#ch4.xhtml#R_ref4_40) (2000). MAX–MIN ant system. Future Generation Computer Systems, 16(8): 889–914.
*   [Sulaiman, M. H., Mustafa, M. W., Shareef, H. and Khalid, S. N. A.](#ch4.xhtml#R_ref4_41) (2012). An application of artificial bee colony algorithm with least squares support vector machine for real and reactive power tracing in deregulated power system. International Journal of Electrical Power & Energy Systems, 37(1): 67–77.
*   [Tereshko, V.](#ch4.xhtml#R_ref4_42) (2000, September). Reaction-diffusion model of a honeybee colony’s foraging behaviour. pp. 807–816. In: International Conference on Parallel Problem Solving from Nature. Springer, Berlin, Heidelberg.
*   [Tereshko, V. and Lee, T.](#ch4.xhtml#R_ref4_43) (2002). How information-mapping patterns determine foraging behaviour of a honey bee colony. Open Systems & Information Dynamics, 9(2): 181–193.
*   [Tereshko, V. and Loengarov, A.](#ch4.xhtml#R_ref4_44) (2005). Collective decision making in honey-bee foraging dynamics. Computing and Information Systems, 9(3): 1.
*   [Xing, L. N., Chen, Y. W., Wang, P., Zhao, Q. S., Xiong, J. et al.](#ch4.xhtml#R_ref4_45) (2010). A knowledgebased ant colony optimization for flexible job shop scheduling problems. Applied Soft Computing, 10(3): 888–896.
*   Xu, C., Duan, H. and Liu, F. (2010). Chaotic artificial bee colony approach to Uninhabited Combat Air Vehicle (UCAV) path planning. Aerospace Science and Technology, 14(8): 535–541.
*   [Zhang, C., Ouyang, D. and Ning, J.](#ch4.xhtml#R_ref4_47) (2010). An artificial bee colony approach for clustering. Expert Systems with Applications, 37(7): 4761–4767.
*   [Zhang, M. D., Zhan, Z. H., Li, J. J. and Zhang, J.](#ch4.xhtml#R_ref4_48) (2014, November). Tournament selection based artificial bee colony algorithm with elitist strategy. pp. 387–396. In: International Conference on Technologies and Applications of Artificial Intelligence. Springer, Cham.
*   [Zhao, D., Liu, L., Yu, F., Heidari, A. A., Wang, M., Liang, G. et al.](#ch4.xhtml#R_ref4_49) (2021). Chaotic random spare ant colony optimization for multi-threshold image segmentation of 2D Kapur entropy. Knowledge-Based Systems, 216: 106510. doi:[https://doi.org/10.1016/j.knosys.2020.106510](https://doi.org/10.1016/j.knosys.2020.106510).
*   [Zhu, G. and Kwong, S.](#ch4.xhtml#R_ref4_50) (2010). Gbest-guided artificial bee colony algorithm for numerical function optimization. Applied Mathematics and Computation, 217(7): 3166–3173.

# Chapter 5 Cuckoo Search and Bat Swarm Algorithm

This chapter is devoted to the swarm optimization algorithms: Cuckoo Search (CS) and Bat Algorithm (BA). The standard Cuckoo Search based on the Lévy Flights and some important variations of the Cuckoo Search algorithm are presented such as: Chaotic Cuckoo Search, Discrete Cuckoo Search and Discrete Binary Cuckoo Search. Also, the Bat Algorithm and some important variations of the algorithm are discussed such as: Chaotic Bat Algorithm, Binary Bat Algorithm, Discrete Bat Algorithm and also two recent variants: Bat Algorithm with double mutation (2020) and Self-adaptive bat algorithm (2019).

## Cuckoo search

Cuckoo search is a meta-heuristic swarm algorithm proposed by [Yang and Deb (2009](#ch5.xhtml#ref5_30)) for several kinds of continuous optimization problems. The algorithm is focused on the natural behavior of the cuckoo species.

### Cuckoo breeding behavior and Lévy flights

Cuckoo birds are well known for their aggressive reproduction strategy and for their beautiful sounds. Some of the cuckoo species like *ani* and *Guira* cuckoos are communal breeders. Cuckoo birds are communally nesting birds, and usually female birds lay their eggs into a shared—common nest and then provide parental care cooperatively in a mixed clutch ([Grieves and Quinn, 2018](#ch5.xhtml#ref5_8)).

They lay their eggs in nests and they are capable of discriminating among parasitic and non-parasitic eggs ([Hauber et al., 2018](#ch5.xhtml#ref5_9); [Macedo, 1992](#ch5.xhtml#ref5_15); [Payne and Sorensen, 2005](#ch5.xhtml#ref5_22)). Cuckoo birds are known for their breeding habits which are parasitic, taking into consideration that female birds lay eggs in host nests and abandon their parenthood responsibilities. Most cuckoo species remove the host eggs from the nest in a few days after hatching ([Hughes, 1996](#ch5.xhtml#ref5_10)). There are several types of brood parasitisms such as: intraspecific, cooperative breeding, and nest take over.

Several studies have shown that the flight behavior of many birds and insects is characterized by Lévy flights ([Brown et al., 2007](#ch5.xhtml#ref5_2); [Pavlyukevich, 2007](#ch5.xhtml#ref5_21); [Reynolds and Frye, 2007](#ch5.xhtml#ref5_24)). This natural behavior has already been idealized and applied on computational optimization and the results are very promising ([Boudjemaa et al., 2020](#ch5.xhtml#ref5_1); [Sharma et al., 2013](#ch5.xhtml#ref5_25); [Zhou et al., 2018](#ch5.xhtml#ref5_34)).

### Cuckoo search algorithm

[Yang and Deb (2009](#ch5.xhtml#ref5_30)) developed three idealized rules regarding the description of the behavior of the Cuckoo species:

*   Each cuckoo lays one egg each time and then dumps its laid egg in a randomly selected nest.
*   The best nests with the optimal egg quality will carry over to the following generations.
*   The number of available cuckoo host nests is constant, and the laid egg is discovered by the cuckoo host bird with a probability *p[a]* ∈ \[0, 1\]. A fraction *p[a]* of the cuckoo nests is substituted by the new ones.

[Yang and Deb (2009](#ch5.xhtml#ref5_30), [2010](#ch5.xhtml#ref5_33)) used simple representations, every egg in the cuckoo nest represents a solution, and a new laid cuckoo egg represents a new solution but the proposed algorithm can be extended to the more complex optimization problems by defining that each bird nest has many eggs representing a whole set of solutions.

The basic steps of the Cuckoo Search (CS) algorithm as proposed by [Yang and Deb (2009](#ch5.xhtml#ref5_30)) is expressed by the next pseudo code:

## Cuckoo Search algorithm via Levy Flights

The Cuckoo search algorithm utilizes a combination of a local random walk (exploitation) and a global random walk (exploration) in a balanced way, and it is controlled by the variable *Pa*. The local random walk (exploitation) is expressed by the equation:

(5.1)  
X[*i*]^((*t* + 1)) = X[*i*]^((*t*)) + *α**s* ⊗ *H*(*P**a*−∈) ⊗ (x[*j*]^((*t*))−x[*k*]^((*t*)))  

where,

*   *x*^([*j*]^(*t*)) and *x*^([*k*]^(*t*)) represent two separate solutions randomly selected.
*   *H*(*u*) represents a Heaviside function.
*   ∊ represents a random number uniformly distributed in \[0,1\].
*   s represents the step size.
*   ⊗ represents the entry-wise product.
*   *Pa* represents a variable for balancing the exploitation and exploration.

During the algorithm process, when generating new solutions x(*t*+1) in time step t+1 for a cuckoo *i*, then the Lévy flight is implemented by using the following equation:

(5.2)  
*x*[*i*]^((*t* + 1)) = *x*[*i*]^((*t*)) + *α* ⊗ Levy(*λ*)  

where,

*   *α* > 0 represents the step size which is related to the problem. In most problems, the value of *α* is close to 1.
*   The product ⊗ represents the entry wise multiplication.

This equation is basically the stochastic equation used in random walk. This entry wise product is similar to those used in PSO algorithm. The Lévy flight is considered more efficient for exploring the search space in each step.

The Lévy flight basically provides a random walk and the random step length is expressed by the Lévy distribution

(5.3)  
Levy ∼ *u* = *t*^( − *λ*), (1<*λ*≤3)  

This distribution has an infinite variance and infinite mean. The steps basically are from a random walk. Several new solutions are generated by Lévy walk close to the best solution so far which speed ups the search at a local level. Although several new solutions are randomly generated in locations far from the current best solution, this facilitates the process so that it will not be trapped in a local best solution.

The Cuckoo Search is a population-based optimization algorithm which uses elitism and selection methods similar to the harmony search, the randomization is considered as more efficient since the step length can be also very large and the number of parameters that have to be tuned is smaller than the genetic algorithm and particle swarm optimization.

## Cuckoo search variants

### Chaotic cuckoo search

[Wang et al. (2016](#ch5.xhtml#ref5_27)), proposed a chaotic cuckoo search optimization algorithm by incorporating the chaos theory into the cuckoo search algorithm. Also, twelve chaotic maps were tested to tune the step size of the cuckoos in the original search algorithm. Twenty-seven benchmark functions were used to investigate the efficiency of the proposed chaotic cuckoo search algorithm.

The chaos has the property that a value cannot be repeated and the search speeds are higher compared to stochastic searches which are based on probabilities. The main parameters of the standard cuckoo search algorithm which have an increased influence on the convergence performance are: the step size called *α* and the discovery rate *p*[a]. The authors have used the value 0.25 for parameter *p*a for the standard cuckoo search algorithm according to the literature ([Yang, 2010](#ch5.xhtml#ref5_32) b).

In the standard cuckoo search algorithm, the step size remains constant. On the contrary in the chaotic cuckoo search algorithm the step size *α is a* chaotic variable which can accelerate the algorithm convergence. Furthermore, all chaotic maps are normalized in the interval \[0, 2\]. The pseudo-code of chaotic CS algorithm proposed by [Wang et al. (2016](#ch5.xhtml#ref5_27)) is the following:

### Chaotic Cuckoo Search algorithm

The following chaotic maps were used by [Wang et al., 2016](#ch5.xhtml#ref5_27) to test the performance of the chaotic CS:

1.  **Chebyshev map**
    
    (5.4)  
    *x*[*k* + 1] = cos (*k*cos^( − 1)(*x*[*k*]))  
    
2.  **Circle map** which generates a chaotic sequence in the interval (0, 1), with a = 0.5 and b = 0.2,
    
    (5.5)  
    *x*[*k* + 1] = *x*[*k*] + *b* − (*a*/2*π*)sin (2*π**k*)*m**o**d*(1)  
    
3.  **Gaussian map**
    
    (5.6)  
    $$x\_{k + 1} = \\left\\{ {\\begin{matrix} {0x\_{k} = 0} \\\\ {1/{x\_{k}{mod}\\left( 1 \\right)\\text{otherwise}}} \\\\ \\end{matrix},{1/x\_{k}}{mod}\\left( 1 \\right) = \\frac{1}{x\_{k}} - \\left\\lbrack \\frac{1}{x\_{k}} \\right\\rbrack} \\right.$$  
    
4.  **Intermittency map**
    
    (5.7)  
    $$x\_{k + 1} = \\left\\{ \\begin{matrix} {\\varepsilon + x\_{k} + cx\_{k}^{n}0 < x\_{k} \\leq P} \\\\ {\\frac{x\_{k} - P}{1 - P}P < x\_{k} < 1} \\\\ \\end{matrix} \\right.$$  
    
5.  **Iterative map**
    
    (5.8)  
    $$x\_{k + 1} = \\sin\\left( \\frac{a\\pi}{x\_{k}} \\right),a \\in \\left( {0,1} \\right)$$  
    
6.  **Liebovitch map**
    
    (5.9)  
    $$x\_{k + 1} = \\left\\{ \\begin{matrix} {\\alpha x\_{k}0 < x\_{k} \\leq P} \\\\ {\\frac{P - a\_{k}}{P\_{2} - P\_{1}}P\_{1} < x\_{k} \\leq P2,} \\\\ {1 - \\beta\\left( {1 - x\_{k}} \\right)P\_{2} < x\_{k} \\leq 1} \\\\ \\end{matrix} \\right.$$  
    
7.  **Logistic map**
    
    (5.10)  
    *x*[*k* + 1] = *a**x*[*k*](1−*x*[*k*])  
    
8.  **Piecewise map**
    
    (5.11)  
    $$x\_{k + 1} = \\left\\{ \\begin{matrix} {\\frac{x\_{k}}{P}o \\leq x\_{k} < P} \\\\ {\\frac{x\_{k} - P}{0.5 - P}P \\leq x\_{k} < \\frac{1}{2}} \\\\ {\\frac{1 - P - x\_{k}}{0.5 - P}\\frac{1}{2} \\leq x\_{k} < 1 - P} \\\\ {\\frac{1 - x\_{k}}{P}1 - P \\leq x\_{k} < 1} \\\\ \\end{matrix} \\right.$$  
    
9.  **Sine map**
    
    (5.12)  
    $$x\_{k + 1} = \\frac{a}{4}\\sin\\left( {\\pi x\_{k}} \\right),0 < a \\leq 4$$  
    
10.  **Singer map**
     
     (5.13)  
     *x*[*k* + 1] = *μ*(7.86*x*[*k*]−23.31*x*[*k*]³−13.302875*x*[*k*]⁴)  
     
11.  **Sinusoidal map**
     
     (5.14)  
     *x*[*k* + 1] = *a**x*[*k*]²sin (*π**x*[*k*])  
     
12.  **Tent map**
     
     This chaotic map is similar to the logistic map and is expressed by the following equation:
     
     (5.15)  
     $$x\_{k + 1} = \\left\\{ \\begin{matrix} \\frac{x\_{k}}{0.7} & {x\_{k} < 0.7} \\\\ \\frac{10}{3} & {x\_{k} \\geq 0.7} \\\\ \\end{matrix} \\right.$$  
     

According to the results in several benchmark functions, [Wang et al. (2016](#ch5.xhtml#ref5_27)), have concluded that the chaotic CS algorithm was improved with the incorporation of the chaotic sinusoidal map instead of α. Also, they have concluded that the tuned CS algorithm improves the global search ability.

### Discrete binary cuckoo search

[Gherboudj et al. (2012](#ch5.xhtml#ref5_7)) proposed a discrete binary cuckoo search optimization algorithm that can be used in binary optimization problems. The solutions are represented as a set of real numbers in a continuous search space (Continuous optimization) or by an integer set in a discrete search space (discrete optimization). Some discrete optimization problems are: the job shop scheduling ([Pongchairerks, 2009](#ch5.xhtml#ref5_23)), and the flow shop scheduling problems ([Liao et al., 2007](#ch5.xhtml#ref5_11)).

The standard CS algorithm for continuous optimization problems is based on *Lévy* flights. Consequently, the algorithm solutions constitute a set of real numbers in a continuous search space. In order to use CS in discrete binary problems the solutions should be converted to binary values. The binary CS is composed of the following basic modules:

*   The Levy flights which are used to obtain a new cuckoo solution.
*   The binary solution representation used to compute the flipping chances for every cuckoo by using the sigmoid function.
*   The objective function and the selection operator.

In the conversion process from a continuous to a binary area, if *x[i]* is a continuous solution in the space \[0, 1\] and *x[i]'* is a binary solution representation, the sigmoid function is used to convert the solution values according to the following equation:

(5.16)  
$$S\\left( x\_{i} \\right) = \\frac{1}{1 = e^{- x\_{i}}}$$  

where *S*(*x[i]*) is the flipping chance of the binary solution ![](images/inline5_95_1_B.jpg)

In order to calculate the binary solution, *S*(*x[i]*) is compared to the value of the random number generated in the interval \[0, 1\] for every dimension *i* of the solution *x* according to the following equation:

(5.17)  
$${x^{\\prime}}\_{i} = \\left\\{ \\begin{matrix} 1 & {\\gamma < < S\\left( x\_{i} \\right)} \\\\ 0 & {otherwise} \\\\ \\end{matrix} \\right.$$  

Where *γ* represents the random number in the space \[0,1\].

### Hybrid self-adaptive cuckoo search

[Mlakar et al. (2016](#ch5.xhtml#ref5_18)), proposed a hybrid self-adaptive cuckoo search algorithm by modifying some mechanisms of the original cuckoo search algorithm. The authors proposed balancing the exploration techniques, self-adapting the cuckoo search parameters, and adapting the cuckoo population.

*Balance to the exploration strategies*

An efficient balancing between the exploration and the exploitation strategies is proposed by setting the algorithm parameters appropriately. The exploration can be classified into three categories according to the distance: the randomly guided long-distance, short-distance and moderate-distance explorations. The first strategy regards the global random walk, the second strategy exploits the neighborhood by using the local random walk and the third exploration strategy can be found in the differential evolution algorithm ([Storn and Price, 1997](#ch5.xhtml#ref5_26)) and has two parameters: the distance from the current best solution and the distance from two solutions randomly selected.

The proposed differential evolution mutation strategy can be expressed by the following equation:

(5.18)  
*u*[*i*]^((*t*)) = *x*[*i*]^((*t*)) + *F*[*i*](*u*[*b**e**s**t*]^((*t*))−*u*[*i*]^((*t*))) + (*u*[*r*1]^((*t*))−*u*[*r*2]^((*t*))),  

where,

*   *F[i]* represents a scaling factor regarding the measure of change
*   **x**^((*t*))[*best*] represents the current best solution
*   **x**^((*t*))[*r*1] and **x**^((*t*))[*r*2] represent the solutions selected randomly from the population.

The authors proposed a crossover operator which can be expressed by the following equation:

(5.19)  
$$u\_{i,j}^{(t)} = \\left\\{ \\begin{matrix} u\_{i,j}^{(t)} & {rand\_{j}\\left( {0,1} \\right) \\leq CRj \\vee = j\_{rand}} \\\\ u\_{i,j}^{(t)} & {otherwise,} \\\\ \\end{matrix} \\right.,$$  

where,

*   *CR* ∈ \[0.0, 1.0\] represents the crossover rate which controls the rate of the parameters copied to the new solution.
*   *j* = *j[rand]* represents a condition which guarantees that the new vector differs from the original solution **x**^((*t*))[*i*] at least in one element.

The substitution of the solution which is randomly selected can be expressed by the following equation:

(5.20)  
$$x\_{i,j}^{(t)} = \\left\\{ \\begin{matrix} w\_{i}^{(t)} & {iff\\left( w\_{i}^{(t)} \\right) \\leq f\\left( x\_{k}^{(t)} \\right) \\land k \\neq i} \\\\ x\_{i}^{(t)} & {otherwise,} \\\\ \\end{matrix} \\right.$$  

where, *k* = *rand*(0, *P*) represents a randomly selected number uniformly distributed in the range \[0, *P*) and *P* represents the population size parameter.

The following equation was proposed for balancing the search strategies controlled by the balancing probability factor *p[b]* in the hybrid self-adaptive cuckoo search algorithm:

(5.21)  
$$f\\left\\{ \\begin{matrix} {U\\left( {0,1} \\right) \\leq p\_{b},then{mod}eratedis\\tan cestrategy} \\\\ {otherwise,thenshortdis\\tan cestrategy} \\\\ \\end{matrix} \\right.$$  

where *U*(0, 1) represents a random value uniformly produced between 0 and 1.

#### Self-adaptation of the control parameters

[Mlakar et al. (2016](#ch5.xhtml#ref5_18)), proposed a self-adaptation strategy for the parameters of the cuckoo search. The solutions are represented by the following equation:

(5.22)  
*u*[*i*]^((*t*)) = (*x*[*j*, *l*]^((*t*)),...,*x*[*i*, *D*]^((*t*)),*α*[*i*]^((*t*)),*λ*[*i*]^((*t*)),*F*[*i*]^((*t*)),*C**R*[*i*]^((*t*)))^(*T*), *f**o**r**i* = 1, ..., *P*.  

where,

*   *α* represents the scaling factor for the short-distance exploration.
*   *λ* represents the stability factor for the short-distance exploration.
*   *F* represents scaling factor for the moderate-distance exploration.
*   *CR* represents crossover rate for the moderate-distance exploration.
*   *P* represents the population size.

The parameters of the short-distance exploration search strategy are selfadapted based on the following equations:

(5.23)  
$$\\alpha\_{i}^{({t + 1})} = \\left\\{ \\begin{matrix} {r\_{1},} & {ifr\_{2} < \\tau\_{0},} \\\\ {\\alpha\_{i}^{(t)},} & {otherwise,} \\\\ \\end{matrix} \\right.$$  

(5.24)  
$$\\lambda\_{i}^{({t + 1})} = \\left\\{ \\begin{matrix} {r\_{3},} & {ifr\_{4} < \\tau\_{1},} \\\\ {\\lambda\_{i}^{(t)},} & {otherwise,} \\\\ \\end{matrix} \\right.$$  

(5.25)  
*F*[*i*]^((*t* + 1)) = *F*[*i*]^((*t*)), *C**R*[*i*]^((*t* + 1)) = *C**R*[*i*]^((*t*))  

The moderate-distance self-adaptation is performed by the equation:

(5.26)  
$$F\_{i}^{({t + 1})} = \\left\\{ \\begin{matrix} {r\_{5},} & {ifr\_{6} < \\tau\_{2},} \\\\ {F\_{i}^{(t)},} & {otherwise,} \\\\ \\end{matrix} \\right.$$  

(5.27)  
$$CR\_{i}^{({t + 1})} = \\left\\{ \\begin{matrix} {r\_{7},} & {ifr\_{8} < \\tau\_{3},} \\\\ {CR\_{i}^{(t)},} & {otherwise,} \\\\ \\end{matrix} \\right.$$  

(5.28)  
*α*[*i*]^((*t* + 1)) = *α*[*i*]^((*t*)), *s*[*i*]^((*t* + 1)) = *s*[*i*]^((*t*)),  

where *τ*[0],..., *τ*[3] represent the learning rates when the self-adaptive parameters change, and *r*[1],..., *r[s]* represent random numbers distributed uniformly within the range \[0,1\] and *s* represents the solution in a time step.

#### Population reduction

Small Cuckoo populations have faster convergence but can be trapped in a local optimum, and larger populations have slower convergence but improved exploration. The authors proposed a linear population reduction. [Mlakar et al. (2016](#ch5.xhtml#ref5_18)), proposed the population size to be reduced based on the following equation:

(5.29)  
$$P^{({t + 1})} = round\\left\\lbrack {\\left( \\frac{P\_{\\max} - P\_{\\min}}{MAX\\\_ Eval} \\right)\*Eval + P\_{\\min}} \\right\\rbrack,$$  

where,

*   *P*[max] represents the initial Cuckoo population size (maximum).
*   *P*[min] represents the specified minimal Cuckoo population size.
*   *Eval* and *MAX*\_*Eval* represent the current and maximum number of function evaluations, correspondingly.

## Bat algorithm

### Bat algorithm inspiration

There are several types of bats in nature with similarities. Bats use a sonar when navigating and hunting. They have the ability to decrease the loudness and increase the emittance rate of ultrasonic sound when hunting for prey. [Yang (2010](#ch5.xhtml#ref5_31) a) proposed bat-inspired algorithm idealizing some characteristics of microbats by using the following idealized rules:

1.  All the bats use echo-location to sense the distance, and they ‘know’ the difference between food and background barriers.
2.  Bats fly randomly with the velocity *v[i]* at position *x[i]* with a constant frequency *f[min]*, with a varying wavelength λ and loudness A[0] to search for the prey. They can automatically adjust the frequency depending on the closeness of the target.
3.  Although the loudness A[0] can vary in many ways, it is assumed that the loudness range is from a large A[0] value to a minimum constant value A[min].

The pseudocode of the algorithm according to [Yang (2010](#ch5.xhtml#ref5_31) a) is the following:

## Bat Algorithm

### Bat movement

In the bat algorithm the vectors with their frequencies, positions ***x**[i]*, and velocities ***v**[i]* in a *d*\-dimensional search space are calculated according to the following equations ([Yang, 2010](#ch5.xhtml#ref5_31) a):

(5.30)  
*F*[*i*] = *F*[min] + (*F*[max]−*F*[min])*β*  

where,

*   *F[i]* represents the frequency of the *i*\-*th* bat which is updated in each iteration.
*   *β* represents a random number of a uniform distribution in \[0,1\].
    
    (5.31)  
    *v*[*i*]^((*t* + 1)) = *v*[*i*]^((*t*)) + (*x*[*i*]^((*t*))−*x*^(\*))*F*[*i*]  
    
    (5.32)  
    *x*[*i*]^((*t* + 1)) = *x*[*i*]^((*t*)) + *v*[*i*]^((*t* + 1))  
    

where,

*   **x**^(*t+*1) represents the new position (solution)
*   **v**^(*t+*1) represents the new velocity
*   **x\*** represents the global best solution so far

[Yang (2010](#ch5.xhtml#ref5_32) b) proposed a local search, when a solution is chosen among the current best positions/solutions. Consequently, a new bat solution is generated locally by using random walk according to the following equation:

(5.33)  
*X*[*n**e**w*] = *X*[*o**l**d*] + *ε**A*^(*t*)  

where,

*   *• ε* represents a random number in the interval \[−1,1\],
*   *A* is the loudness parameter of the emitted sound that bats utilize to perform exploration instead of exploitation.

The loudness *A[i]* and the rate *r[i]* of the pulse emission are updated as the iterations proceed according to the following equations:

(5.34)  
*A*[*i*]^((*t* + 1)) = *α**A*[*i*]^((*t*))  

(5.35)  
*r*[*i*]^((*t* + 1)) = *r*[*i*]^((0))\[1−exp(−*γ**t*)\]  

where,

*   *α* represents a constant and represents a cooling factor similar to simulated annealing.
*   *γ* represents a constant.

## Bat algorithm variants

Several modifications of the Bat algorithm were proposed in the literature such as, binary bat algorithm ([Nakamura et al., 2012](#ch5.xhtml#ref5_19)), chaotic bat algorithm ([Gandomi and Yang, 2014](#ch5.xhtml#ref5_4)), self-adaptive bat algorithm ([Lyu et al., 2019](#ch5.xhtml#ref5_14)) bat algorithm with double mutation operators ([Liu et al., 2020](#ch5.xhtml#ref5_12)), bat algorithm for constrained optimization tasks ([Gandomi et al., 2013](#ch5.xhtml#ref5_3)), enhanced Bat algorithm with mutation operator ([Ghanem and Jantan, 2019](#ch5.xhtml#ref5_6)) and discrete bat algorithm ([Luo et al., 2014](#ch5.xhtml#ref5_13)).

### Binary bat algorithm

[Nakamura et al. (2012](#ch5.xhtml#ref5_19)), have proposed a binary bat algorithm for feature selection. In the standard bat algorithm the bat swarm moves in a continuous search space. In a feature selection problem, the search space is constructed as a *n*\-dimensional (n expresses the number of features) Boolean search space since it should be decided whether a feature should be selected or not.

The bat’s positions (solutions) should be represented as binary vectors. [Nakamura et al. (2012](#ch5.xhtml#ref5_19)), have used a sigmoid function to express the bat positions in binary values:

(5.36)  
$$S\\left( v\_{i}^{j} \\right) = \\frac{1}{1 + e^{- v\_{i}^{j}}}$$  

The bat position is calculated according to the following equation:

(5.37)  
$$S\_{i}^{j} = \\left\\{ \\begin{matrix} {ifS\\left( v\_{i}^{j} \\right) > \\sigma} \\\\ {otherwise} \\\\ \\end{matrix} \\right.$$  

where *σ* ~ *U*(0,1). Therefore, only binary values can be provided for each bat coordinates.

According to [Nakamura et al. (2012](#ch5.xhtml#ref5_19)), the proposed binary bat algorithm outperformed other similar techniques used on several datasets.

[Mirjalili et al. (2014](#ch5.xhtml#ref5_17)), have proposed a different approach of a binary bat algorithm. Since the sigmoid function forces the bats to take the values of 0 and 1, their velocity increases but the positions remain the same.

[Mirjalili et al. (2014](#ch5.xhtml#ref5_17)), proposed a v-shaped transfer function for position updating to oblige the bats which have high velocity to switch their positions:

(5.38)  
$$V\\left( {v\_{i}^{k}\\left( t \\right)} \\right) = \\left| \\frac{2}{\\pi} \\right.\\arctan\\left. \\left( {\\frac{\\pi}{2}v\_{i}^{k}\\left( t \\right)} \\right) \\right|$$  

(5.39)  
$$x\_{i}^{k}\\left( {t + 1} \\right) = \\left\\{ \\begin{matrix} \\begin{matrix} \\left( {x\_{i}^{k}\\left( t \\right)} \\right)^{- 1} & {If} & {rand < V\\left( {v\_{i}^{k}\\left( {t + 1} \\right)} \\right)} \\\\ \\end{matrix} \\\\ \\begin{matrix} {x\_{i}^{k}\\left( t \\right)} & {rand \\geq V\\left( {v\_{i}^{k}\\left( {t + 1} \\right)} \\right)} \\\\ \\end{matrix} \\\\ \\end{matrix} \\right.$$  

where *x[i]^k*(*t*) and *v[i]^k* indicate the position and velocity of the *i*[th] particle at iteration *t* in the *k*[th] dimension, and (*x[i]^k*(*t*))^(–1) is the complement of *x[i]^k*(*t*).

The authors have tested their approach in twenty-two benchmark functions and the results were compared with Binary PSO and the genetic algorithm. The results have shown an increased efficiency of the proposed algorithm.

### Chaotic bat algorithm

[Gandomi and Yang (2014](#ch5.xhtml#ref5_4)), proposed a Chaotic Bat Algorithm by using several chaotic maps in order to tune the Bat Algorithm parameters and improve the experimental results and the algorithm performance. The Chaotic maps that were used in the experiments are the following: Chebyshev map, Circle map, Gauss/Mouse map, Intermittency map, Iterative map, Liebovitch map, Logistic map, Piecewise map, Sawtooth map, Sine map, Singer map, Sinusoidal map, Tent map. Most of the equations of these chaotic maps are presented in the chaotic CS section.

The proposed chaotic Bat algorithms are the following:

#### 1st Chaotic bat algorithm

[Gandomi and Yang (2014](#ch5.xhtml#ref5_4)), proposed the modification of the parameter *β* in the frequency update equation by using chaotic maps expressed by the following equation:

(5.40)  
*f*[*i*] = *f*[min] + (*f*[max]−*f*[min])*C**M*[*i*]  

where CM represents a chaotic map. In the conventional bat algorithm, *β* represents a random number from 0 to 1 and in the 1st chaotic version of the bat algorithm it is a chaotic number between 0 and 1 according to the selected chaotic map. The experimental results have shown an improved performance of the chaotic bat algorithm compared to the conventional bat algorithm.

#### 2nd Chaotic bat algorithm

Also, [Gandomi and Yang (2014](#ch5.xhtml#ref5_4)), proposed the modification of the parameter *λ[i]* in the velocity update equation by using chaotic maps expressed by the following equation

(5.41)  
*v*[*i*]^(*t*) = *v*[*i*]^(*t* − 1) + (*x*[*i*]^(*t*)−*x*^(\*))*C**M*[*i*]*f*[*i*]  

where CM represents a chaotic map.

#### 3rd Chaotic bat algorithm

Also, [Gandomi and Yang (2014](#ch5.xhtml#ref5_4)), proposed the modification of the loudness (*A*) parameter in the bat algorithm by replacing it with chaotic maps in order to improve the bat algorithm performance.

### Self-adaptive bat algorithm

[Lyu et al. (2019](#ch5.xhtml#ref5_14)), proposed a self-adaptive bat algorithm by incorporating a step-control and a mutation mechanism based on the observations and the algorithm global search should be adapted to according to the loudness parameter *A* and the local search process should be adapted according to the pulse emission rate parameter *R*.

#### Step-control mechanism

[Lyu et al. (2019](#ch5.xhtml#ref5_14)), proposed a step-control mechanism to control the step sizes used in every iteration in the global and local search. The proposed algorithm utilizes two frequencies *f*[1] and *f*[2], for the individual bats and for the bat swarm, accordingly.

First, during the global search, the new solutions are expressed by the following equations:

(5.42)  
*v*[*i*]^(*t*) = *ω**v*[*i*]^(*t* − 1) + *f*[*i*]*r*[*i*](*h*[*i*\*]−*x*[*i*]^(*t* − 1)) + *f*[2]*f*[2](*x*[\*]−*x*[*t*]^(*t* − 1))  

(5.43)  
*f*[1] = *α*(1−*e*^( − |*F*[*a**v**g*] − *F*[*b**e**s**t*]|)) + *γ*(1−*k*) + *f*[min]  

(5.44)  
*C*[*w*] = *f*[1] + *f*[2]  

(5.45)  
*x*[*i*]^(*t*) = *x*[*i*]^(*t* − 1) + *μ**v*[*i*]^(*t*)  

where,

*   *ω* represents a decreasing weight coefficient.
*   *h[i\*]* represents the optimal position for bat *i*.
*   *x*[\*] represents the current global optimum.
*   *f*[1] and *f*[2] represent the frequencies as described above.
*   *r*[1] and *r*[2] represent random numbers uniformly distributed in (0.5, 1.5).
*   *F[avg]* represents the average fitness of the current optimal individual positions.
*   *F[best]* represents the best fitness of the current global optimum solution.
*   *k* = *t*/*tmax* represents an evaluation index with *k* (0, 1\].
*   *tmax* represents the maximum number of iterations.
*   *fmin* represents the minimum value of *f*[1].
*   *μ* represents the step weight coefficient in the range (0, 1\].
*   α and *γ* are weights.

This search is conducted according to the following equations:

If the evaluation index is: *k* < 0.4, then

(5.46)  
*x*[*i*]^(*t*) = *x*[\*] + *A*^(*t*)*s**δ* × *g*(*k*)  

If the evaluation index is: *k* ≥ 0.4, then

(5.47)  
*x*[*i*]^(*t*) = *x*[\*] + *A*^(*t*)*s**δ* × 0.1^(*g*(*k*))  

where,

*   *A^t* represent the bat swarm current average loudness.
*   *δ* ∈ \[−1, 1\] represent a random number uniformly distributed.
*   *s* represents among the upper bound and the lower bound of the obtainable solution and the number of bat agents in the swarm group.
*   *g*(*k*) is a function related to the search steps.

#### Mutation mechanism

[Lyu et al. (2019](#ch5.xhtml#ref5_14)), proposed a step-control mechanism which improved the algorithm global search capability. Also, the authors proposed a mutation mechanism that integrates the loudness *A* to improve the algorithm’s capability to avoid local optima.

The loudness *A* in the standard bat algorithm reduces gradually to 0 in the later steps, and the pulse emission rate *R* increases gradually to *Rmax*. The proposed equations for the updates of the *A* and *R* parameters are expressed by the equations:

(5.48)  
$$A\_{i}^{t + 1} = \\frac{f\_{1}}{f\_{\\max}}$$  

(5.49)  
$$R\_{i}^{t + 1} = \\frac{f\_{2}}{f\_{\\max}}$$  

where *fmax* represents the upper limit of the frequency.

The frequencies *f*[1] and *f*[2] are adaptively updated according to the bat swarm fitness and accordingly the *A* and *R* parameters are adapted according to the above equations.

### Bat algorithm with double mutation

The standard bat algorithm shows a poor performance in problems with a complex nature due to its early convergence. [Liu et al. (2020](#ch5.xhtml#ref5_12)), proposed a bat algorithm with double mutation operators where a modified factor related to time and two mutation operators is incorporated. The proposed algorithm appears to improve the bat algorithm performance in nonlinear optimization problems according to the experimental results.

[Liu et al. (2020](#ch5.xhtml#ref5_12)), proposed three modifications of the standard bat algorithm by introducing: a time factor parameter, a Cauchy mutation operator and a Gaussian mutation operator.

#### Time factor modification

In the standard bat algorithm, the new bat positions are updated by utilizing the sum of the previous iteration and the current velocity. During the algorithm implementation the distance between the bats and the best solution globally decreases and also the bat flight time decreases.

The authors introduced a constant as a time factor in the original equation which calculates the next bat position. The time factor *λ[t]* is close to 1 at the beginning of the algorithm in order to increase speed of the convergence, and when the algorithm arrives close to the selected number of iterations which was set as a limit the time factor *λ[t]* is close to “0” to enhance the local search. The proposed time factor is calculated by the following equation:

(5.50)  
$$\\lambda\_{t} = 1 - e^{({- {(\\frac{it\_{\\max} - it}{it\_{\\max} + 0.6it})}^{10}})}$$  

where,

*   *it[max]* represents the maximum number of iterations.
*   *it* represents the number of current iterations.

The new position equation with the time factor *λ[t]* is expressed by the formula:

(5.51)  
*X*[*i*]^(*t*) = *X*[*i*]^(*t* − 1) + *λ*[*t*]*V*[*i*]^(*t*)  

#### Cauchy mutation operator modification

[Liu et al. (2020](#ch5.xhtml#ref5_12)), proposed a third modification to the original bat algorithm by integrating a Cauchy mutation operator which can help the bat algorithm to escape from a local optimum according to the literature ([Yang and Huang, 2012](#ch5.xhtml#ref5_29)).

The function of the one-dimensional Cauchy density is expressed by the following equation ([Paiva et al., 2017](#ch5.xhtml#ref5_20)):

(5.52)  
$$c\\left( x \\right) = \\frac{1}{\\pi}\\frac{k}{k^{2} + x^{2}}$$  

where,

*   *• x* ∈ \[–∞, ∞\]
*   parameter *k* > 0 is a scale factor.

The Cauchy distribution function is expressed by the following equation ([Paiva et al., 2017](#ch5.xhtml#ref5_20)):

(5.53)  
$$C\_{t}\\left( x \\right) = \\frac{1}{2} + \\frac{1}{\\pi}\\arctan\\left( \\frac{x}{k} \\right)$$  

The modifying position update equation with Cauchy mutation operator is integrated into the original bat algorithm and expressed with the following formula:

(5.54)  
*X*[*i*]^(*t*) = *X*[*i*]^(*t*) + *X*[*i*]^(*t*)*C**a**u**c**h**y*(0,1)  

where *Cauchy* (0,1) is a random number which follows the Cauchy distribution function. The *k* parameter was set to 1.

#### Gaussian mutation operator

[Liu et al. (2020](#ch5.xhtml#ref5_12)), proposed the Gaussian mutation operator to be used in the exploitation of the algorithm in the last iterations since the Gaussian mutation operator size is smaller than the Cauchy mutation operator size.

The one-dimensional Gaussian density function is expressed by the equation:

(5.55)  
$$g\\left( x \\right) = \\frac{1}{\\sigma\\sqrt{2\\pi}}e^{\\lbrack\\frac{- {({x - \\mu})}^{2}}{2\\sigma^{2}}\\rbrack}$$  

When *μ* = 0 and *σ =* 1, the function that follows the Gaussian distribution is expressed by the equation ([Melo and Watada, 2016](#ch5.xhtml#ref5_16)):

(5.56)  
$$g\\left( x \\right) = \\frac{1}{\\sqrt{2\\pi}}e^{\\lbrack\\frac{- {(x)}^{2}}{2}\\rbrack}$$  

The Gaussian mutation operator was incorporated into the original bat algorithm to implement the mutation of the global best position according to the equation:

(5.57)  
*X*[*b**e**s**t*]^(\*) = *X*[*b**e**s**t*] + *X*[*b**e**s**t*]*G**a**u**s**s*(0.1)  

where *Gauss(0,1)* represents a random number which follows the Gaussian distribution.

## References

*   [Boudjemaa, R., Oliva, D. and Ouaar, F.](#ch5.xhtml#R_ref5_1) (2020). Fractional Lévy flight bat algorithm for global optimisation. International Journal of Bio-Inspired Computation, 15(2): 100–112.
*   [Brown, C. T., Liebovitch, L. S. and Glendon, R.](#ch5.xhtml#R_ref5_2) (2007). Lévy flights in Dobe Ju/’hoansi foraging patterns. Human Ecology, 35(1): 129–138.
*   [Gandomi, A. H., Yang, X. S., Alavi, A. H. and Talatahari, S.](#ch5.xhtml#R_ref5_3) (2013). Bat algorithm for constrained optimization tasks.. Neural Computing and Applications, 22(6): 1239–1255.
*   [Gandomi, A. H. and Yang, X.-S.](#ch5.xhtml#R_ref5_4) (2014). Chaotic bat algorithm.. Journal of Computational Science, 5(2): 224–232. doi: [https://doi.org/10.1016/j.jocs.2013.10.002](https://doi.org/10.1016/j.jocs.2013.10.002).
*   Gao, S., Gao, Y., Zhang, Y. and Xu, L. (2019). Multi-strategy adaptive cuckoo search algorithm.. IEEE Access, 7: 137642–137655. doi: [10.1109/ACCESS.2019.2916568](http://doi.org/10.1109/ACCESS.2019.2916568).
*   [Ghanem, W. A. H. M. and Jantan, A.](#ch5.xhtml#R_ref5_6) (2019). An enhanced Bat algorithm with mutation operator for numerical optimization problems.. Neural Computing and Applications, 31(1): 617–651. doi: [10.1007/s00521–017–3021–9](http://doi.org/10.1007/s00521%E2%80%93017%E2%80%933021%E2%80%939).
*   [Gherboudj, A., Layeb, A. and Chikhi, S.](#ch5.xhtml#R_ref5_7) (2012). Solving 0–1 knapsack problems by a discrete binary version of cuckoo search algorithm.. International Journal of BioInspired Computation, 4(4): 229–236.
*   [Grieves, L. A. and Quinn, J. S.](#ch5.xhtml#R_ref5_8) (2018). Group size, but not manipulated whole-clutch egg color, contributes to ovicide in joint-nesting Smooth-billed Anis.. The Wilson Journal of Ornithology, 130(2): 479–484.
*   [Hauber, M. E., Dainson, M., Baldassarre, D. T., Hossain, M., Holford, M. and Riehl, C.](#ch5.xhtml#R_ref5_9) (2018). The perceptual and chemical bases of egg discrimination in communally nesting greater anis Crotophaga major.. Journal of Avian Biology, 49(8): e01776.
*   [Hughes, J. M.](#ch5.xhtml#R_ref5_10) (1996). Phylogenetic analysis of the Cuculidae (Aves, Cuculiformes) using behavioral and ecological characters.. The Auk, 113(1): 10–22.
*   [Liao, C. J., Tseng, C. T. and Luarn, P.](#ch5.xhtml#R_ref5_11) (2007). A discrete version of particle swarm optimization for flowshop scheduling problems.. Computers & Operations Research, 34(10): 3099–3111.
*   [Liu, Q., Li, J., Wu, L., Wang, F. and Xiao, W.](#ch5.xhtml#R_ref5_12) (2020). A novel bat algorithm with double mutation operators and its application to low-velocity impact localization problem. Engineering Applications of Artificial Intelligence, 90: 103505. doi:[https://doi.org/10.1016/j.engappai.2020.103505](https://doi.org/10.1016/j.engappai.2020.103505).
*   [Luo, Q., Zhou, Y., Xie, J., Ma, M. and Li, L.](#ch5.xhtml#R_ref5_13) (2014). Discrete bat algorithm for optimal problem of permutation flow shop scheduling.. The Scientific World Journal, 2014.
*   [Lyu, S., Li, Z., Huang, Y., Wang, J. and Hu, J.](#ch5.xhtml#R_ref5_14) (2019). Improved self-adaptive bat algorithm with step-control and mutation mechanisms.. Journal of Computational Science, 30: 65–78. doi:[https://doi.org/10.1016/j.jocs.2018.11.002](https://doi.org/10.1016/j.jocs.2018.11.002).
*   [Macedo, R. H.](#ch5.xhtml#R_ref5_15) (1992). Reproductive patterns and social organization of the communal Guira Cuckoo (Guira guira) in central Brazil.. The Auk, 109(4): 786–799.
*   [Melo, H. and Watada, J.](#ch5.xhtml#R_ref5_16) (2016). Gaussian-PSO with fuzzy reasoning based on structural learning for training a Neural Network.. Neurocomputing, 172: 405–412.
*   [Mirjalili, S., Mirjalili, S. M. and Yang, X.-S.](#ch5.xhtml#R_ref5_17) (2014). Binary bat algorithm.. Neural Computing and Applications, 25(3): 663–681. doi: [10.1007/s00521–013–1525–5](http://doi.org/10.1007/s00521%E2%80%93013%E2%80%931525%E2%80%935).
*   [Mlakar, U., Fister, I. and Fister, I.](#ch5.xhtml#R_ref5_18) (2016). Hybrid self-adaptive cuckoo search for global optimization.. Swarm and Evolutionary Computation, 29: 47–72. doi:[https://doi.org/10.1016/j.swevo.2016.03.001](https://doi.org/10.1016/j.swevo.2016.03.001).
*   [Nakamura, R. Y. M., Pereira, L. A. M., Costa, K. A., Rodrigues, D., Papa, J. P. and Yang, X. S.](#ch5.xhtml#R_ref5_19) (2012, 22–25 Aug. 2012). BBA: A Binary Bat Algorithm for Feature Selection. Paper presented at the 2012 25th SIBGRAPI Conference on Graphics, Patterns and Images.
*   [Paiva, F. A., Silva, C. R., Leite, I. V., Marcone, M. H. and Costa, J. A.](#ch5.xhtml#R_ref5_20) (2017, November). Modified bat algorithm with cauchy mutation and elite opposition-based learning. pp. 1–6. In: 2017 IEEE Latin American Conference on Computational Intelligence (LA-CCI). IEEE.
*   [Pavlyukevich, I.](#ch5.xhtml#R_ref5_21) (2007). Cooling down Lévy flights.. Journal of Physics A: Mathematical and Theoretical, 40(41): 12299.
*   [Payne, R. B. and Sorensen, M. D.](#ch5.xhtml#R_ref5_22) (2005). The Cuckoos (Vol. 15). Oxford University Press.
*   [Pongchairerks, P.](#ch5.xhtml#R_ref5_23) (2009). Particle swarm optimization algorithm applied to scheduling problems.. Science Asia, 35: 89–94. doi: [10.2306/scienceasia1513–1874.2009.35.089](http://doi.org/10.2306/scienceasia1513%E2%80%931874.2009.35.089).
*   [Reynolds, A. M. and Frye, M. A.](#ch5.xhtml#R_ref5_24) (2007). Free-flight odor tracking in Drosophila is consistent with an optimal intermittent scale-free search.. PloS One, 2(4): e354.
*   [Sharma, H., Bansal, J. C. and Arya, K. V.](#ch5.xhtml#R_ref5_25) (2013). Opposition based lévy flight artificial bee colony.. Memetic Computing, 5(3): 213–227.
*   [Storn, R. and Price, K.](#ch5.xhtml#R_ref5_26) (1997). Differential evolution—a simple and efficient heuristic for global optimization over continuous spaces.. Journal of Global Optimization, 11(4): 341–359.
*   [Wang, G.-G., Deb, S., Gandomi, A. H., Zhang, Z. and Alavi, A. H.](#ch5.xhtml#R_ref5_27) (2016). Chaotic cuckoo search.. Soft Computing, 20(9): 3349–3362. doi: [10.1007/s00500–015–1726–1](http://doi.org/10.1007/s00500%E2%80%93015%E2%80%931726%E2%80%931).
*   Yang, D., Li, G. and Cheng, G. (2007). On the efficiency of chaos optimization algorithms for global optimization.. Chaos, Solitons & Fractals, 34(4): 1366–1375.
*   [Yang, X. J. and Huang, Z. G.](#ch5.xhtml#R_ref5_29) (2012). Opposition-based artificial bee colony with dynamic cauchy mutation for function optimization.. International Journal of Advancements in Computing Technology, 4(4): 56–62.
*   [Yang, X. S. and Deb, S.](#ch5.xhtml#R_ref5_30) (2009, December). Cuckoo search via Lévy flights. pp. 210–214. In: 2009 World Congress on Nature & Biologically Inspired Computing (NaBIC). IEEE.
*   [Yang, X. S.](#ch5.xhtml#R_ref5_31) (2010 a). A new metaheuristic bat-inspired algorithm. pp. 65–74. In: Nature Inspired Cooperative Strategies for Optimization (NICSO 2010). Springer, Berlin, Heidelberg.
*   [Yang, X. S.](#ch5.xhtml#R_ref5_32) (2010 b). Nature-inspired Metaheuristic Algorithms. Luniver Press.
*   [Yang, X. S. and Deb, S.](#ch5.xhtml#R_ref5_33) (2010). Engineering optimisation by cuckoo search.. International Journal of Mathematical Modelling and Numerical Optimisation, 1(4): 330–343.
*   [Zhou, Y., Ling, Y. and Luo, Q.](#ch5.xhtml#R_ref5_34) (2018). Lévy flight trajectory-based whale optimization algorithm for engineering optimization.. Engineering Computations.

# Chapter 6 Firefly Algorithm, Harmony Search and Cat Swarm Algorithm

This chapter is devoted to the swarm optimization algorithms: Firefly algorithm, Harmony Search and Cat Swarm Optimization algorithm. The standard swarm optimization algorithms and some significant variations are discussed such as: Firefly algorithm with Lévy Flights Chaotic Firefly algorithm, Improved Harmony Search, Chaotic Harmony Search and Binary Discreate Cat Swarm Optimization and Improved Cat Swarm Optimization. Also, some important variations of the Bat Algorithm are discussed such as: Chaotic Bat Algorithm, Discreate Bat Algorithm and Binary Bat Algorithm.

## Firefly algorithm

The firefly algorithm was developed by idealizing the flashing characteristics of natural fireflies in order to develop a computational optimization algorithm ([Yang, 2009b](#ch6.xhtml#ref6_24), [2010b](#ch6.xhtml#ref6_26)). The following rules were used to idealize the natural behavior of fireflies:

*   All the fireflies are unisex so that one firefly will be attracted to other fireflies regardless of sex.
*   The attractiveness is proportional to their brightness (light intensity), so in any pair of flashing fireflies, the lesser bright one will be attracted by the brighter one. When the distance increases the attractiveness between them decreases. If a firefly cannot find a brighter one then it will move in a random way.
*   The firefly brightness depends on the value of the objective function.

For simplicity reasons, it is assumed that the firefly attractiveness is defined by its brightness which is associated with the fitness function. The attractiveness *β* will be dependant on the distance *r[ij]* between the firefly *i* and the firefly *j*. The firefly light intensity *I*(*r*) decreases according to the distance from its source, and also the light varies according to the degree of absorption.

In the firefly algorithm, there are four important issues: the light intensity, the attractiveness, the firefly distance and the firefly movement.

**Light intensity:** In the firefly algorithm as proposed by Yang (2010), the firefly light intensity *I*(*r*) which expresses a solution, for a given light absorption coefficient γ, varies with the distance r according to the equation:

(6.1)  
*I*(*r*) = *I*[0]*e*^( − *γ**r*²)  

where,

*   *I*[0]
*   *r* represents the distance between two fireflies
*   *γ* represents a constant light absorption coefficient.

**Attractiveness:** The firefly attractiveness *β*(*r*) is proportional to the light intensity and is expressed by the following equation:

(6.2)  
*β*(*r*) = *β*[0]*e*^( − *γ**r*²)  

where *β*[0] represents the attractiveness when the distance r = 0.

**Distance:** The distance *r[i, j]* between two fireflies *i* and *j* at *X[i]* and *X[j]* locations can be estimated according to the standard equation of the Cartesian distance:

(6.3)  
$$r\_{i,j} = \\left\\| {X\_{i} - X\_{j}} \\right\\| = \\sqrt{\\sum\_{k = 1}^{d}\\left( {x\_{j,k} - x\_{j,k}} \\right)^{2}}$$  

where,

*   *x[i, k]* represents the *k*\-th element of the *i*\-th firefly
*   *d* represents the dimension of the objective function that has to be optimized.

**Movement:** The movement of an *i* firefly attracted to another brighter - more attractive firefly *j*, can be calculated by the following equation:

(6.4)  
*X*[*i*] = *X*[*i*] + *β*[0]*e*^( − *γ**r*[*i*, *j*]²)(*X*[*j*]−*X*[*i*]) + *α**ε*[*ι*]  

where,

*   α represents a randomized parameter
*   *ε[t]* represents a vector of random numbers with a Gaussian or uniform distribution.

According to Yang (2010), the simplest form of *ε[t]* is expressed by:

(6.5)  
$$\\varepsilon\_{\\iota} = random - \\frac{1}{2}$$  

where *random* is a randomly generated number uniformly distributed in the range \[0,1\]. So, the movement of an *i* firefly in this case can be expressed as:

(6.6)  
$$X\_{i} = X\_{i} + \\beta\_{0}e^{- \\gamma r\_{i,j}^{2}}\\left( {X\_{j} - X\_{i}} \\right) + \\alpha\\left( {rand - \\frac{1}{2}} \\right)$$  

The Firefly Algorithm is presented below (Yang, 2009, [2010b](#ch6.xhtml#ref6_26)).

### Firefly Algorithm

## Firefly algorithm variants

Several modifications of the Firefly algorithm were proposed in the literature such as, Firefly algorithm with Lévy Flights ([Yang, 2010b](#ch6.xhtml#ref6_26)), chaotic Firefly algorithm ([Coelho et al., 2011](#ch6.xhtml#ref6_8); [Gandomi et al., 2013](#ch6.xhtml#ref6_9)), Firefly algorithm with neighborhood attraction ([Wang et al., 2017](#ch6.xhtml#ref6_22)), Firefly algorithm for clustering ([Senthilnath et al., 2011](#ch6.xhtml#ref6_20))

### Firefly algorithm with Lévy flights

[Yang (2010b](#ch6.xhtml#ref6_26)), proposed Firefly algorithm with Lévy Flights. The pseudocode of the proposed algorithm is described below:

### Firefly Algorithm

The movement of a firefly i with Lévy Flights which is attracted to a brighter firefly j is defined by the equation:

(6.7)  
$$X\_{i} = X\_{i} + \\beta\_{0}e^{- \\gamma r\_{i,j}^{2}}\\left( {X\_{j} - X\_{i}} \\right) + \\alpha sign\\left( {rand - \\frac{1}{2}} \\right) \\oplus Lévy$$  

*   the third term of the equation expresses is randomization parameter via Levy flights.
*   the product ⊕ expresses the entry-wise multiplication operator.
*   The $sign\\left( {rand - \\frac{1}{2}} \\right)$ expresses a random sign or direction and the random step length is calculated by a Levy distribution. Where *rand* ∈ \[0,1\].

In the firefly algorithm with Lévy Flights, the firefly motion is a random walk process performed to prevent the algorithm from sticking into a local optimum, where the step length of the search process is improved and the deviation is expressed by the equation:

(6.8)  
*L**e**v**y* ∼ *u* = *t*^( − *λ*), 0 < *λ* < 3  

where,

*   *t* represents a random parameter in the range of (0, 1\],
*   *λ* represents a stability index.

### Chaotic firefly algorithms

[Coelho et al. (2011](#ch6.xhtml#ref6_8)), proposed a chaotic firefly algorithm by using Logistic map chaotic sequences in order to tune the parameters, *α* and *γ*.

Consequently, the basic equation of the firefly algorithm altered to:

(6.9)  
$$x\_{i} = x\_{i} + \\beta\_{0}e^{- \\gamma{(t)} \\cdot r\_{ij}^{2}}\\left( {x\_{j} - x\_{i}} \\right) + \\alpha\\left( t \\right)\\left( {rand - \\frac{1}{2}} \\right)$$  

*   *γ*(*t*) is calculated by the equation:
    
    (6.10)  
    *γ*(*t*) = *μ*[1] ⋅ *γ*(*t*−1) ⋅ \[1−*γ*(*t*−1)\]  
    
*   *α*(*t*) is calculated by the equation:
    
    (6.11)  
    *α*(*t*) = *μ*[2] ⋅ *γ*(*t*−1) ⋅ \[1−*α*(*t*−1)\]  
    

where,

*   *t* represents the sample,
*   *μ*[1] and *μ*[2] represent the control parameters, with 0 ≤ *μ*[1] and *μ*[2] ≤ 4.

The authors referred that the proposed chaotic firefly algorithm outperformed the original firefly algorithm.

[Yang (2013](#ch6.xhtml#ref6_27)), proposed a chaos-enhanced firefly algorithm by also using automatic parameter tuning. In this research, a logistic map was used as a chaotic parameter for the attractiveness and the absorption coefficient replacing the Gaussian and the Lévy flight randomly distributed parameters. The proposed algorithm was an applied function optimization.

[Arul et al. (2013](#ch6.xhtml#ref6_2)), proposed a chaotic firefly algorithm to solve economic load dispatch problems by using the chaotic tent map in order to produce new values for the parameters, *α* and *β*[0]. The equation for the Tent map is as follows:

(6.12)  
$$\\alpha\_{n + 1} = \\left\\{ \\begin{matrix} {2\\alpha\_{n}} & {\\alpha\_{n} < 0.5} \\\\ {2\\left( {1 - \\alpha\_{n}} \\right)} & {\\alpha\_{n} \\geq 0.5} \\\\ \\end{matrix} \\right.$$  

## Harmony search algorithm

Harmony Search was proposed as a heuristic optimization algorithm ([Geem, 2000](#ch6.xhtml#ref6_10); [Geem et al., 2001](#ch6.xhtml#ref6_11)). It was inspired by music harmony which is a combination of individual sounds aesthetically pleasant to the ear. It mimics a music orchestra while composing music in order to achieve the most harmonious melody. The procedure of searching for better harmony can be analogous to the process of finding an optimal solution to a computational optimization problem. Harmony Search has been applied on many kinds of optimization problems such as water and groundwater management, economic and emission dispatch, engineering, robotics, vehicle routing, structural design, energy, stock price prediction, medical diagnosis, and others ([Ayvaz, 2009](#ch6.xhtml#ref6_3); [Ceylan and Ceylan, 2009](#ch6.xhtml#ref6_4); [Chatterjee et al., 2012](#ch6.xhtml#ref6_5); [Guha et al., 2020](#ch6.xhtml#ref6_12); [Jiang et al., 2020](#ch6.xhtml#ref6_13); [Kayabekir et al., 2021](#ch6.xhtml#ref6_14); [Mousavi et al., 2021](#ch6.xhtml#ref6_17)).

As a musical orchestra tries to find the best state of harmony (fantastic harmony) which is defined aesthetically, an optimization algorithm searches for a global optimum by evaluating an objective function. As an aesthetic evaluation is defined by the set of sounds played by the individual instruments of the orchestra, an objective function evaluation is defined by the set of values generated. Each practice of the orchestra for a better sound is analogous to each iteration of an optimization algorithm in order to improve the objective function evaluation ([Geem et al., 2001](#ch6.xhtml#ref6_11)).

The main steps of the initially proposed algorithm are as follows ([Geem et al., 2001](#ch6.xhtml#ref6_11))

**1st Step.** Initialize a Harmony Memory.

**2nd Step.** Create a new harmony from Harmony Memory.

**3rd Step.** If the new created harmony (solution) is improved compared to the minimum harmony in the Harmony Memory, then include it in the Harmony Memory, and remove the previous minimum harmony from it.

**4th Step.** If the predefined stopping criteria are not met, go to Step 2.

The Harmony Search holds the history of past vectors (solutions) (Harmony Memory) and can alter the adaptation rate by using the harmony memory accepting rate.

The harmony memory (HM) is used to store the best harmonies of new solution vectors. The harmony memory acceptance (or considering) rate (*r[accept]* \[0,1\]) is used to effectively manipulate it. The pitch adjustment is accomplished by using pitch bandwidth *b[range]* and also the pitch adjusting rate *r[pitch]*. The pitch can be adjusted according to the following equation:

(6.13)  
*x*[*n**e**w*] = *x*[*o**l**d*] + *b*[*r**a**n**g**e*] × *ε*  

where,

*   *x[old]* represents the existing pitch in the harmony memory,
*   *x[new]* represents the new pitch after the pitch adjustment.
*   *b[range]* is the pitch bandwidth distance (Also, expressed as bw in the literature).
*   *ε* represents a random number uniformly distributed in the range \[–1, 1\].

The pitch adjusting rate *r[pitch]* controls the degree of adjustment. The most common values of *r[pitch]* are in the range 0.1 ~ 0.5 and *r[accept]* in the range 0.7 ~ 0.95 ([Yang, 2009a](#ch6.xhtml#ref6_23)). According to [Yang (2009a](#ch6.xhtml#ref6_23)) the harmony search is described by the following algorithm:

## Harmony search algorithm

### Harmony search example

#### Ackley function approximation

Mathematical equation

The equation that represents the Ackley function is as follows:

(6.14)  
$$f\\left( {x\_{1},...,x\_{n}} \\right) = - a.\\exp\\left( {- b\\sqrt{\\frac{1}{n}{\\sum\\limits\_{i = 1}^{n}x\_{i}^{2}}}} \\right) - \\exp\\left( {\\frac{1}{n}{\\sum\\limits\_{i - 1}^{n}{\\cos\\left( {cx\_{1}} \\right)}}} \\right) + a + \\exp\\left( 1 \\right)$$  

where a, b and c are constants. For the experiments we set: a = 20, b = 0.2 and c = 2π. The Ackley function is continuous, non-convex, multimodal and differentiable.

Input search space

The function is evaluated with *x[i]* \[−20,20\], and i = 1, 2, . . . , n.

Harmony Search Parameters

Maximum Number of Iterations: 10000

Harmony Memory Size: 25

Number of New Harmonies: 20

![Figure 6.1. Ackley function approximation by using Harmony Search.](images/fig6_1_B.jpg)

Figure 6.1. Ackley function approximation by using Harmony Search.

 

Harmony Memory Accepting Rate: *r[accept]* = 0.9

Pitch Adjustment Rate: *r[pitch]* = 0.1

Decision Variables Minimum Bound (DVMinB): –20

Decision Variables Maximum Bound (DVMaxB): 20 Pitch Bandwidth:

(6.15)  
*b* = 0.02^(\*)(*D**V**M**a**x**B* − *D**V**M**i**n**B*)  

The optimization results illustrated in the next figure are very good. The function minimization stops improving at about 6000 iterations.

## Harmony search variants

### Improved harmony search algorithm

Several researches have tried to improve the convergence of the Harmony Search algorithm. [Mahdavi et al. (2007](#ch6.xhtml#ref6_16)), proposed an improved harmony search algorithm. According to the authors, in the improved harmony search algorithm the pitch adjusting rate *PAR* (Or *r[pitch]*) is dynamically updated by using the following equation:

(6.16)  
$$PAR\\left( t \\right) = PAR\_{\\min} + \\frac{\\left( {PAR\_{\\max} - PAR\_{\\min}} \\right)}{NI} \\times t$$  

where,

*   *PAR*(*t*) represents the pitch adjusting rate for the iteration *t.*
*   *PAR*[min] represents the minimum adjusting rate.
*   *PAR*[max] represents the maximum adjusting rate.
*   *NI* represents the number of the iteration.
*   *t* represents the iteration number.

Also, in the improved harmony search algorithm, the bandwidth distance parameter *bw* (Or *b[range]*) is dynamically updated by using the following equation:

(6.17)  
$$bw\\left( t \\right) = bw\_{\\max}e^{({\\frac{\\ln{(\\frac{bw\_{\\min}}{bw\_{\\max}})}}{NI} \\times t})}$$  

where,

*   *bw*(*t*) represents the bandwidth distance for iteration *t*.
*   *bw*[min] represents the minimum bandwidth.
*   *bw*[max] represents the maximum bandwidth.

Four new parameters are introduced in the improved harmony search algorithm: *PAR*[min], *PAR*[max], *bw*[min], and *bw*[max].

### Chaotic harmony search

In the Harmony Search algorithm, there are parameters with constant values during the algorithm process. [Alatas (2010](#ch6.xhtml#ref6_1)), proposed some methods to apply chaotic sequences in order to substitute the random values of the parameters in order to improve the global convergence and prevent the algorithm from being trapped in a local minimum.

In the proposed algorithm, pitch adjusting rate *PAR* (Or *r[pitch]*) value is not constant in the parameter initialization stage and it has been substituted by chaotic maps as in the following equation:

(6.18)  
*P**A**R*(*t* + 1) = *f*(*P**A**R*(*t*)), 0 < *P**A**R*(*t*) < 1, *t* = 0, 1, 2, ...  

where the function *f* is a chaotic map.

Also, [Alatas (2010](#ch6.xhtml#ref6_1)), proposed that bandwidth distance *b[w]* (Or *b[range]*) value can be substituted in the parameter initialization stage by chaotic maps according to the following equation:

(6.19)  
*b**w*(*t* + 1) = *f*(*b**w*(*t*)), 0 < *b**w*(*t*) < 1, *t* = 0, 1, 2, ...  

where the function *f* is a chaotic map.

The authors have used seven chaotic maps for the experiments:

Logistic map, expressed by the equation:

(6.20)  
*X*[*n* + 1] = *a**X*[*n*](1−*X*[*n*])  

Tent map, expressed by the equations:

(6.21)  
$$X\_{n + 1} = \\left\\{ \\begin{matrix} {X\_{n}/0.7,} & {X\_{n} < 0.7,} \\\\ {10/3X\_{n}(1 - X\_{n}),} & {otherwise.} \\\\ \\end{matrix} \\right.$$  

Sinusoidal iterator, expressed by the equation:

(6.22)  
*X*[*n* + 1] = *a**x*[*n*]²sin (*π**x*[*n*])  

with a = 2.3 and *X*[0] = 0.7

Gauss map is expressed by the equations:

(6.23)  
$$X\_{n + 1} = \\left\\{ \\begin{matrix} {0,} & {X\_{n} = 0,} \\\\ {1/{X\_{n}\\,{mod}\\,\\left( 1 \\right)}} & {X\_{n} \\in \\left( {0,1} \\right),} \\\\ \\end{matrix} \\right.$$  

(6.24)  
$${1/{X\_{n}\\,{mod}\\,\\left( 1 \\right)}} = \\frac{1}{X\_{n}} - \\frac{1}{X\_{n}}$$  

Circle map is expressed by the equation:

(6.25)  
*X*[*n* + 1] = *X*[*n*] + *b* − (*a*/2*π*)sin (2*π**X*[*n*])*m**o**d*(1)  

with a = 0.5 and b = 0.2.

Sinus map is expressed by the equation:

(6.26)  
*X*[*n* + 1] = 2.3(*X*[*n*])^(2sin (*π**X*[*n*]))  

Henon map is expressed by the equations:

(6.27)  
*X*[*n* + 1] = 1 − *a**X*[*n*]² + *b**Y*[*n*]  

(6.28)  
*Y*[*n* + 1] = *X*[*n*]  

(6.29)  
*X*[*n* + 1] = 1 − *a**X*[*n*]² + *b**X*[*n* − 1]  

with parameter values a = 1.4 and b = 0.3.

## Cat swarm optimization

### Cat swarm algorithm

The Cat Swarm Algorithm was introduced by [Chu et al. (2006)](#ch6.xhtml#ref6_6). The authors studied the behavior of cats in order to introduce a new optimization algorithm. They have proposed that cats have two modes: the seeking mode and the tracing mode. They observed that cats spend most of their time resting and observing. In their resting and observing time, they move slowly and carefully. This can be called the seeking mode. Cats spend little time in chasing things. This is called tracing mode, where cats move according to their own velocities ([Chu et al., 2006](#ch6.xhtml#ref6_6); [Chu and Tsai, 2007](#ch6.xhtml#ref6_7)).

#### Seeking mode

Seeking mode has four basic parameters: the seeking memory pool (SMP), the seeking range of the selected dimension (SRD), the counts of dimension to change (CDC), and the self-position considering (SPC).

*   **SMP** is utilized to determine the size of the seeking memory for each cat.
*   **SRD** represents the mutation ratio for the selected dimensions.
*   **CDC** represents how many dimensions will be changed.
*   **SPC** represents a Boolean parameter, which is used as a decision variable to define if the current cat point will be one of the candidate points (solutions) to move to.

The seeking mode consists of five simple steps ([Chu et al. 2006](#ch6.xhtml#ref6_6)):

**Step 1:** Make *j* copies of the current position of cat[k], with *j = SMP*. If the SPC value is true (Equal to one), *j* = (*SMP* − 1), then retain the current position as one of the candidate solutions.

**Step 2:** For every copy, according to the counts of dimension to change (CDC), randomly add or subtract the selected dimension SRD percentages from the current values and replace the old values.

**Step 3:** Estimate the fitness values of all candidate solutions.

**Step 4:** If all fitness function values are not the same, estimate the selection probability of every candidate by using the following equation, otherwise set each candidate selection probability to 1.

(6.30)  
$$P\_{i} = \\frac{FS\_{i} - FS\_{b}}{FS\_{\\max} - FS\_{\\min}}$$  

where,

*   *FS[i]* is the fitness of the *ith* cat
*   *FS[b]* = *FS[max]* if the minimum solution should be found
*   *FS[b]* = *FS[min]* if the maximum solution should be found.

**Step 5:** Pick in a random way the point to move to from the candidate position, and replace the current position of cat[k] with the selected candidate.

#### Tracing mode

In tracing mode, the cat is tracing targets. In this mode, the next position of every cat is defined by the individual cat velocity and the cat swarm best position. This mode can be summarized in the following steps.

**Step 1:** Update the cat velocities for every dimension (*v[k,d]*) according to the equation:

(6.31)  
*v*[*k*, *d*] = *v*[*k*, *d*] + *r*[1]*c*[1](*x*[*g**b**e**s**t*, *d*]−*x*[*x*, *d*]), *w**i**t**h* *d* = 1, ..., *M*  

where,

*   *x[gbest,d]* represents the position of the cat with the best fitness value
*   *x[k]*[,*d*] represents the current position of the cat, in d*th* dimension
*   *c*[1] represents a fix value in the interval \[0, 2\]
*   *r*[1] represents a uniformly distributed random value in the space \[0, 1\].

**Step 2:** Check if the velocities are within the range bounds of the maximum velocity. If the new velocity is out of the range, then define it as equal to the maximum velocity.

**Step 3:** Update the current position of cat[*k*] using the following equation:

(6.32)  
*x*[*k*, *d*] = *x*[*k*, *d*] + *v*[*k*, *d*]  

### Basic description of Cat Swarm Algorithm

The Cat Swarm Algorithm has two modes, the seeking mode and the tracing mode. In order to combine these two processes, a mixture ratio is defined which sets the rate of cats in seeking mode and the rest of the cats in tracing mode. According to [Chu et al. (2006)](#ch6.xhtml#ref6_6), the Cat Swarm Algorithm consists of the following stages:

**Stage 1:** Create *N* cats.

**Stage 2:** Scatter the cats into a *M*\-dimensional solution space randomly and set random values, within the range of the maximum velocity for every cat. Then randomly pick a number of cats and set them into tracing process according to the mixture ratio and other cats into seeking process.

**Stage 3:** Evaluate the fitness value of every cat by applying the positions (solutions) *x[i]* of cats into the fitness function, and keep the best cat into memory (The best solution so far).

**Stage 4:** Move the cats according to their categorization. If a cat is in seeking mode, follow the seeking mode procedure, otherwise follow the tracing mode procedure.

**Stage 5:** Pick again a number of cats and put them into tracing mode according to the mixture ratio and the others into seeking mode.

**Stage 6:** Check the termination criterion, if it is met, terminate, otherwise repeat Step 3 to Step 5.

## Cat algorithm variants

### Binary discrete Cat algorithm

The original Cat Swarm Algorithm was developed for continuous optimization problems. [Sharafi et al. (2013](#ch6.xhtml#ref6_21)), proposed a binary discrete cat algorithm. In the proposed binary discrete cat algorithm, the cat position vector consists of ones and zeros. In the Seeking Mode of Binary CSO, all of the values are zero and one the current position of the cat can be determined as a binary mutation. In Binary CSO the parameter probability of the mutation operation (PMO) substitutes the parameter SRD of the original CSO. In the tracing mode of Binary CSO, the main difference is in the velocity definition. The velocity vector in Binary CSO represents the probability of change and is updated as follows. The two velocity vectors, one for every cat, are determined as *V*¹[*kd*] and *V*⁰[*kd*] . *V*¹[*kd*] representing the probability of the bits to invert from one to zero and *V*⁰[*kd*] represents the probability of the bits to invert from zero to one.

The velocities *V*¹[*kd*] and *V*⁰[*kd*] are calculated by the following equations:

(6.33)  
*V*[*k**d*]¹ = *w**V*[*k**d*]¹ + *d*[*k**d*]¹  

(6.34)  
*V*[*k**d*]⁰ = *w**V*[*k**d*]⁰ + *d*[*k**d*]⁰    *d* = 1, ...*M*  

*d[kd]* and *d [kd]* are updated according to the following equations:

(6.35)  
*i**f* *X*[*g**b**e**s**t*, *d*] = 1 *t**h**e**n* *d*[*k**d*]¹ = *r*[1]*c*[1] *a**n**d* *d*[*k**d*]⁰ =  − *r*[1]*c*[1]  

(6.36)  
*i**f* *X*[*g**b**e**s**t*, *d*] = 0 *t**h**e**n* *d*[*k**d*]¹ = *r*[1]*c*[1] *a**n**d* *d*[*k**d*]⁰ =  − *r*[1]*c*[1]  

where,

*   *r*[1] represents random value in the interval \[0, 1\].
*   *w* represents the inertia weight.
*   *c*[1] represents a fixed value determined by the user.

The velocity of the cat[*k*] is estimated by the following equation:

(6.37)  
$${V^{\\prime}}\_{kd} = \\left\\{ \\begin{matrix} {V\_{kd}^{1}\\ if\\ X\_{kd} = 0} \\\\ {V\_{kd}^{0}\\ if\\ X\_{kd} = 1} \\\\ \\end{matrix} \\right.$$  

The mutation probability in every dimension is determined by the variable *t* which is estimated by the following equation.

(6.38)  
$$t\_{kd} = sig\\left( {V^{\\prime}}\_{kd} \\right) = \\frac{1}{1 + e^{- {V^{\\prime}}\_{kd}}}$$  

where *t[kd]* takes values in the range \[0, 1\]. The new cat position of every dimension is updated according to the following equation.

(6.39)  
$$X\_{kd} = \\left\\{ \\begin{matrix} {X\_{gbest,d}\\ if\\ rand < t\_{kd}} \\\\ {x\_{kd}\\text{~~~}if\\ t\_{kd} < rand^{d = 1,...M}} \\\\ \\end{matrix} \\right.$$  

If the value of *V*¹[*kd*]' has a value larger than the maximum velocity (out of maximum bound), then maximum velocity is selected as the velocity value.

### Improved cat swarm optimization

[Kumar and Singh (2018](#ch6.xhtml#ref6_15)), proposed an improved cat swarm algorithm in order to solve global optimization problems. The CSO algorithm suffers from several problems, such as: premature convergence ([Orouskhani et al., 2011](#ch6.xhtml#ref6_18), [2013](#ch6.xhtml#ref6_19)), it cannot explore all good solutions because of the lack of an information mechanism about the global best cat position.

In order to improve the CSO algorithm, the following modifications are proposed by [Kumar and Singh (2018](#ch6.xhtml#ref6_15)):

The global best cat position is used in order to explore better solutions and improve the convergence rate and lead the cats in the tracing mode. The new proposed modified equation in tracing mode of the algorithm includes the global best cat position:

(6.40)  
*X*[j new]^(*d* + 1) = (1−*β*) \* *X*[*j*]^(*d*) + *β* \* *P*[*g*] + *V*[*j*]^(*d*)  

The authors, proposed a new velocity update equation, in order to improve the cat swarm optimization algorithm diversity, in tracing mode:

(6.41)  
*V*[j new]^(*d* + 1) = *V*[*j*]^(*d*) + *β*(*P*[*g*]−*X*[*j*]^(*d*)) + *α* \* *ε*  

where,

*   *ε* represents a vector randomly and uniformly distributed in the space \[0, 1\].
*   *α* and *β* represent the acceleration parameters for directing the cat position into a local and global best.
*   *P[g]* represents the global best position of a cat.

The values of both α and β acceleration parameters for directing the cat position in a local and global best are adaptive and calculated by the following equations:

(6.42)  
$$a\\left( t \\right) = a\_{\\max} - \\left\\{ \\frac{a\_{\\max} - a\_{\\min}}{t\_{\\max}} \\right\\}\*t$$  

where,

*   *α* [max] and *α* [min] represent the upper and lower limits.
*   *t[max]* represents the maximum number of the iterations.
*   *t* represents the current number of the iteration.

(6.43)  
$$\\beta\\left( t \\right) = \\beta\_{\\min} + \\left( {\\beta\_{\\max} - \\beta\_{\\min}} \\right)\\sin\\left\\{ \\frac{\\pi t}{t\_{\\max}} \\right\\}$$  

where,

*   *β* [min] and *β* [max] represent the minimum and maximum values of the first and the last iterations respectively.
*   *t[max]* represents the maximum number of iterations.
*   *t* represents the current number of the iteration.

## References

*   [Alatas, B.](#ch6.xhtml#R_ref6_1) (2010). Chaotic harmony search algorithms. Applied Mathematics and Computation, 216(9): 2687–2699. doi:[https://doi.org/10.1016/j.amc.2010.03.114.](https://doi.org/10.1016/j.amc.2010.03.114.)
*   [Arul, R., Velusami, S. and Ravi, G.](#ch6.xhtml#R_ref6_2) (2013, December). Chaotic firefly algorithm to solve economic load dispatch problems. 458–464. In 2013 International Conference on Green Computing, Communication and Conservation of Energy (ICGCE). IEEE.
*   [Ayvaz, M. T.](#ch6.xhtml#R_ref6_3) (2009). Identification of groundwater parameter structure using harmony search algorithm. pp. 129–140. In Music-inspired Harmony Search Algorithm. Springer, Berlin, Heidelberg.
*   [Ceylan, H. and Ceylan, H.](#ch6.xhtml#R_ref6_4) (2009). Harmony search algorithm for transport energy demand modeling. Music-Inspired Harmony Search Algorithm, 163–172.
*   [Chatterjee, A., Ghoshal, S. P. and Mukherjee, V.](#ch6.xhtml#R_ref6_5) (2012). Solution of combined economic and emission dispatch problems of power systems by an opposition-based harmony search algorithm. International Journal of Electrical Power & Energy Systems, 39(1): 9–20.
*   [Chu, S. C., Tsai, P. W. and Pan, J. S.](#ch6.xhtml#R_ref6_6) (2006, August). Cat swarm optimization. pp. 854–858. In Pacific Rim International Conference on Artificial Intelligence. Springer, Berlin, Heidelberg.
*   [Chu, S. C. and Tsai, P. W.](#ch6.xhtml#R_ref6_7) (2007). Computational intelligence based on the behavior of cats. International Journal of Innovative Computing, Information and Control, 3(1): 163–173.
*   [Coelho, L. d. S., Bernert, D. L. d. A. and Mariani, V. C.](#ch6.xhtml#R_ref6_8) (2011, 5–8 June 2011). A Chaotic Firefly Algorithm Applied to Reliability-Redundancy Optimization. Paper presented at the 2011 IEEE Congress of Evolutionary Computation (CEC).
*   [Gandomi, A. H., Yang, X. S., Talatahari, S. and Alavi, A. H.](#ch6.xhtml#R_ref6_9) (2013). Firefly algorithm with chaos. Communications in Nonlinear Science and Numerical Simulation, 18(1): 89–98. doi:[https://doi.org/10.1016/j.cnsns.2012.06.009.](https://doi.org/10.1016/j.cnsns.2012.06.009.)
*   [Geem, Z. W.](#ch6.xhtml#R_ref6_10) (2000). Optimal Design of Water Distribution Networks using Harmony Search. Ph.D. Thesis, Korea University.
*   [Geem, Z. W., Kim, J. H. and Loganathan, G. V.](#ch6.xhtml#R_ref6_11) (2001). A new heuristic optimization algorithm: harmony search. Simulation, 76(2): 60–68.
*   [Guha, S., Das, A., Singh, P. K., Ahmadian, A., Senu, N. and Sarkar, R.](#ch6.xhtml#R_ref6_12) (2020). Hybrid feature selection method based on harmony search and naked mole-rat algorithms for spoken language identification from audio signals. IEEE Access, 8: 182868–182887.
*   [Jiang, M., Jia, L., Chen, Z. and Chen, W.](#ch6.xhtml#R_ref6_13) (2020). The two-stage machine learning ensemble models for stock price prediction by combining mode decomposition, extreme learning machine and improved harmony search algorithm. Annals of Operations Research, 1–33.
*   [Kayabekir, A. E., Bekdas, G., Yücel, M., Nigdeli, S. M. and Geem, Z. W.](#ch6.xhtml#R_ref6_14) (2021). Harmony search algorithm for structural engineering problems. Nature-Inspired Metaheuristic Algorithms for Engineering Optimization Applications, 13.
*   [Kumar, Y. and Singh, P. K.](#ch6.xhtml#R_ref6_15) (2018). Improved cat swarm optimization algorithm for solving global optimization problems and its application to clustering. Applied Intelligence, 48(9): 2681–2697.
*   [Mahdavi, M., Fesanghary, M. and Damangir, E.](#ch6.xhtml#R_ref6_16) (2007). An improved harmony search algorithm for solving optimization problems. Applied Mathematics and Computation, 188(2): 1567–1579.
*   [Mousavi, S. M., Abdullah, S., Niaki, S. T. A. and Banihashemi, S.](#ch6.xhtml#R_ref6_17) (2021). An intelligent hybrid classification algorithm integrating fuzzy rule-based extraction and harmony search optimization: Medical diagnosis applications). Knowledge-based Systems, 220: 106943.
*   [Orouskhani, M., Mansouri, M. and Teshnehlab, M.](#ch6.xhtml#R_ref6_18) (2011). Average-inertia weighted cat swarm optimization. pp. 321–328. In International Conference in Swarm Intelligence. Springer, Berlin, Heidelberg.
*   [Orouskhani, M., Orouskhani, Y., Mansouri, M. and Teshnehlab, M.](#ch6.xhtml#R_ref6_19) (2013). A novel cat swarm optimization algorithm for unconstrained optimization problems. International Journal of Information Technology and Computer Science, 5(11): 32–41.
*   [Senthilnath, J., Omkar, S. N. and Mani, V.](#ch6.xhtml#R_ref6_20) (2011). Clustering using firefly algorithm: Performance study. Swarm and Evolutionary Computation, 1(3): 164–171. doi:[https://doi.org/10.1016/j.swevo.2011.06.003.](https://doi.org/10.1016/j.swevo.2011.06.003.)
*   [Sharafi, Y., Khanesar, M. A. and Teshnehlab, M.](#ch6.xhtml#R_ref6_21) (2013, 25–26 Sept. 2013). Discrete Binary Cat Swarm Optimization Algorithm. Paper presented at the 2013 3rd IEEE International Conference on Computer, Control and Communication (IC4).
*   [Wang, H., Wang, W., Zhou, X., Sun, H., Zhao, J., Yu, X. and Cui, Z.](#ch6.xhtml#R_ref6_22) (2017). Firefly algorithm with neighborhood attraction. Information Sciences, 382–383: 374–387. doi:[https://doi.org/10.1016/j.ins.2016.12.024.](https://doi.org/10.1016/j.ins.2016.12.024.)
*   [Yang, X. S.](#ch6.xhtml#R_ref6_23) (2009a). Harmony search as a metaheuristic algorithm. pp. 1–14. In Musicinspired Harmony Search Algorithm. Springer, Berlin, Heidelberg.
*   [Yang, X. S.](#ch6.xhtml#R_ref6_24) (2009b). Firefly algorithms for multimodal optimization. pp. 169–178. In International Symposium on Stochastic Algorithms. Springer, Berlin, Heidelberg.
*   Yang, X. S. (2010a). Nature-inspired Metaheuristic Algorithms. Luniver Press.
*   [Yang, X. S.](#ch6.xhtml#R_ref6_26) (2010b). Firefly algorithm, Levy flights and global optimization. pp. 209–218. In: Research and Development in Intelligent Systems XXVI. Springer, London.
*   [Yang, X. S.](#ch6.xhtml#R_ref6_27) (2013). Chaos-enhanced firefly algorithm with automatic parameter tuning. pp. 135–136. In Recent Algorithms and Applications in Swarm Intelligence Research. IGI Global.

# Chapter 7 Grey Wolf, Whale and Grasshopper Optimization

This chapter is devoted to the latest bio-inspired swarm algorithms such as: Grey Wolf Optimization (GWO) Algorithm (2014), Whale Optimization Algorithm (WOA) (2016) and Grasshopper Optimization Algorithm (GOA) (2017). The original algorithms and some recent important variants are discussed such as: Binary Grey Wolf Optimization (2016), Grey Wolf with Lévy flight (2017), Whale Optimization with Lévy Flight (2017), Binary Whale Optimization Algorithm (2020), Improved Grasshopper Optimization Algorithm (2018) and Chaotic Grasshopper Optimization (2019).

## Grey wolf optimization

The grey wolf optimizer was introduced by [Mirjalili et al. (2014](#ch7.xhtml#ref7_15)). The grey wolf swarm algorithm was inspired by the natural behavior of grey wolves in group hunting. The grey wolf optimizer is relatively simple compared to the swarm intelligence algorithm with fewer hyper-parameters to be set, compared to other optimization algorithms and also the implementation of the algorithm is relatively easy.

The grey wolf optimizer was applied on several kinds of optimization problems such as: economic dispatch ([Jayabarathi et al., 2016](#ch7.xhtml#ref7_10); [Wong et al., 2014](#ch7.xhtml#ref7_21)), feature selection ([Emary et al., 2015](#ch7.xhtml#ref7_3); [Emary et al., 2016](#ch7.xhtml#ref7_4); [Hu et al., 2020](#ch7.xhtml#ref7_8)), engineering ([Nadimi-Shahraki et al., 2021](#ch7.xhtml#ref7_17)), forecasting electric loads ([Zhang and Hong, 2021](#ch7.xhtml#ref7_22)), wind speed forecasting ([Altan et al., 2021](#ch7.xhtml#ref7_1)), human activity recognition ([Helmi et al., 2021](#ch7.xhtml#ref7_7)), building energy optimization ([Ghalambaz et al., 2021](#ch7.xhtml#ref7_5)), energy consumption prediction and optimization ([Li et al., 2021](#ch7.xhtml#ref7_11)), power quality improvement ([Thakur et al., 2021](#ch7.xhtml#ref7_19)) and others.

 ![Figure 7.1. Grey wolves pack hierarchy.](images/fig7_1_B.jpg)

Figure 7.1. Grey wolves pack hierarchy.

Grey wolves are predators, and prefer to live in a pack. The social hierarchy of the Grey wolf pack is shown on the next figure. Alpha (α) is the highest level in the Grey wolf pack hierarchy.

Inspired by this pack hierarchy and the natural behavior of the grey wolf pack, [Mirjalili et al. (2014](#ch7.xhtml#ref7_15)) proposed the grey wolf optimizer where the population of grey wolves is separated into four groups: alpha, beta, delta and omega. The group separation is according to the wolf social hierarchy. Alpha represents the leader (The dominant wolf), the top wolf in the hierarchy, which represents the best solution. The second-best solution is represented by beta (β), third best solution is represented by delta (δ). Τhe rest of the solutions are represented as omega (ω).

The hunting behavior of grey wolves consists of three main stages:

*   searching for prey
*   encircling the prey
*   attacking the prey.

### Encircling prey

The grey wolf pack is encircling the prey in the hunting process. [Mirjalili et al. (2014](#ch7.xhtml#ref7_15)) proposed the following mathematical equations to model the encircling behavior:

(7.1)  
$$\\overset{\\rightarrow}{D} = \\left| {\\overset{\\rightarrow}{C} \\cdot {\\overset{\\rightarrow}{X}}\_{p}\\left( t \\right) - \\overset{\\rightarrow}{X}\\left( t \\right)} \\right|$$  

(7.2)  
$$\\overset{\\rightarrow}{X}\\left( {t + 1} \\right) = {\\overset{\\rightarrow}{X}}\_{p}\\left( t \\right) - \\overset{\\rightarrow}{A} \\cdot \\overset{\\rightarrow}{D}$$  

where,

*   *t* represents the current iteration.
*   *$\\overset{\\rightarrow}{A}$* and *$\\overset{\\rightarrow}{C}$* represent the coefficient vectors.
*   *$\\overset{\\rightarrow}{X}$ [p]* represents the prey position vector.
*   *$\\overset{\\rightarrow}{X}$* represents the grey wolf position vector.

The *$\\overset{\\rightarrow}{A}$* and *$\\overset{\\rightarrow}{C}$* vectors are estimated according to the following mathematical equations:

(7.3)  
$$\\overset{\\rightarrow}{A} = 2\\overset{\\rightarrow}{a} \\cdot {\\overset{\\rightarrow}{r}}\_{1} - \\overset{\\rightarrow}{a}$$  

(7.4)  
$$\\overset{\\rightarrow}{C} = 2 \\cdot {\\overset{\\rightarrow}{r}}\_{2}$$  

where,

*   *a* is linearly decreased from 2 to 0 during the algorithm iterations
*   *r*[1], *r*[2] represent random vectors in the interval \[0, 1\].

### Hunting

Alpha (α), beta (β) and delta (δ) wolves participate in the hunting process and alpha (α) represents the best solution in the pack, beta (β) the secondbest solution and delta (δ) the third best solution. The first three best solutions are saved and the other wolves update their current positions randomly in the search space. [Mirjalili et al. (2014](#ch7.xhtml#ref7_15)), proposed the following equations in order to simulate the Grey wolf hunting behavior.

(7.5)  
$${\\overset{\\rightarrow}{D}}\_{\\alpha} = \\left| {{\\overset{\\rightarrow}{C}}\_{2} \\cdot {\\overset{\\rightarrow}{X}}\_{\\alpha} - \\overset{\\rightarrow}{X}} \\right|$$  

(7.6)  
$${\\overset{\\rightarrow}{D}}\_{\\beta} = \\left| {{\\overset{\\rightarrow}{C}}\_{2} \\cdot {\\overset{\\rightarrow}{X}}\_{\\beta} - \\overset{\\rightarrow}{X}} \\right|$$  

(7.7)  
$${\\overset{\\rightarrow}{D}}\_{\\delta} = \\left| {{\\overset{\\rightarrow}{C}}\_{3} \\cdot {\\overset{\\rightarrow}{X}}\_{\\delta} - \\overset{\\rightarrow}{X}} \\right|$$  

(7.8)  
$${\\overset{\\rightarrow}{X}}\_{1} = {\\overset{\\rightarrow}{X}}\_{\\alpha} - {\\overset{\\rightarrow}{A}}\_{1} \\cdot \\left( {\\overset{\\rightarrow}{D}}\_{\\alpha} \\right)$$  

(7.9)  
$${\\overset{\\rightarrow}{X}}\_{2} = {\\overset{\\rightarrow}{X}}\_{\\beta} - {\\overset{\\rightarrow}{A}}\_{2} \\cdot \\left( {\\overset{\\rightarrow}{D}}\_{\\beta} \\right)$$  

(7.10)  
$${\\overset{\\rightarrow}{X}}\_{3} = {\\overset{\\rightarrow}{X}}\_{\\delta} - {\\overset{\\rightarrow}{A}}\_{3} \\cdot \\left( {\\overset{\\rightarrow}{D}}\_{\\delta} \\right)$$  

(7.11)  
$$\\overset{\\rightarrow}{X}\\left( {t + 1} \\right) = \\frac{{\\overset{\\rightarrow}{X}}\_{1} + {\\overset{\\rightarrow}{X}}\_{2} + {\\overset{\\rightarrow}{X}}\_{3}}{3}$$  

where,

*   *$\\overset{\\rightarrow}{X}$* [1], *$\\overset{\\rightarrow}{X}$* [2] , *$\\overset{\\rightarrow}{X}$* [3] represent the of alpha (α), beta (β) and delta (δ) wolf positions
*   *$\\overset{\\rightarrow}{X}$* (*t* + 1) represents the updated next wolf position.
*   *$\\overset{\\rightarrow}{X}$[α]*, *$\\overset{\\rightarrow}{X}$[β]*, *$\\overset{\\rightarrow}{X}$[γ]* are the first three best solutions.
*   *$\\overset{\\rightarrow}{A}$* [1], *$\\overset{\\rightarrow}{A}$* [2], *$\\overset{\\rightarrow}{A}$* [3] are calculated by using equation(7.3).
*   *$\\overset{\\rightarrow}{C}$* [1], *$\\overset{\\rightarrow}{C}$* [2], *$\\overset{\\rightarrow}{C}$* [3] are defined by using equation(7.4).

### Attacking prey (exploitation)

The hunting process of grey wolves finishes when the prey stops moving. Then the grey wolves start to attack. This is modelled by [Mirjalili et al. (2014](#ch7.xhtml#ref7_15)), by decreasing the value of *$\\overset{\\rightarrow}{a}$* linearly during the iterations.

### Search for prey (exploration)

Grey wolves search for solutions near the position of the alpha, beta, and delta. [Mirjalili et al. (2014](#ch7.xhtml#ref7_15)), use *$\\overset{\\rightarrow}{A}$* with random values, bigger than 1 or less than –1 so as to force the grey wolves to diverge and enhance exploration in order to allow the algorithm to search globally in the search space.

The pseudocode of the Grey Wolf Optimization Algorithm as proposed by [Mirjalili et al. (2014](#ch7.xhtml#ref7_15)), is presented below.

### Grey Wolf Optimization Algorithm

## Grey wolf algorithm variants

### Binary grey wolf optimization

[Emary et al. (2016](#ch7.xhtml#ref7_4)), proposed the binary grey wolf optimization (bGWO) method for feature selection. The original grey wolf optimization is defined for continuous optimization problems in a continuous search space. In optimization problems with a binary nature the solutions of the algorithm are binary with values 0 and 1.

In the original grey wolf optimization algorithm, the wolves update their positions according to the first three best solutions *$\\overset{\\rightarrow}{X}$[α]*, *$\\overset{\\rightarrow}{X}$[β]*, *$\\overset{\\rightarrow}{X}$[γ]*. In the binary grey wolf optimization, the solutions are only binary.

[Emary et al. (2016](#ch7.xhtml#ref7_4)), proposed two binary grey wolf optimization methods.

## Binary grey wolf optimization method I

In binary grey wolf optimization, the equation for the position update can be expressed as under,

(7.12)  
*X*[*i*]^(*t* + 1) = *C**r**o**s**s**o**v**e**r*(*x*[1],*x*[2],*x*[3])  

where,

*   *Crossover*(*x*, *y*, *z*) is the cross over operation among the solutions *x*, *y*, *z*
*   *x*[1], *x*[2], *x*[3] represent binary vectors expressing the impact of the movement of a wolf in the direction of α, β, δ wolves, calculated by using the following equations:

(7.13)  
$$x\_{1}^{d} = \\left\\{ \\begin{matrix} 1 & {if\\left( {x\_{\\alpha}^{d} + bstep\_{\\alpha}^{d}} \\right) \\geq 1} \\\\ 0 & {othewise} \\\\ \\end{matrix} \\right.$$  

where,

*   *x^d[α]* represents the solution vector of the *α* wolf in dimension *d*,
*   *bstep^d[α]* represents a binary step in the *d* dimension calculated as by using the following equation:

(7.14)  
$$bstep\_{\\alpha}^{d} = \\left\\{ \\begin{matrix} 1 & {if\\, cstep\_{\\alpha}^{d} \\geq rand} \\\\ 0 & {othewise} \\\\ \\end{matrix} \\right.$$  

where,

*   *rand* represents a random number uniformly distributed in the range \[0,1\].
*   *cstep^d[α]* represents a continuous step value for the *d* dimension and can be estimated by using the following equation:

(7.15)  
$$cstep\_{\\alpha}^{d} = \\frac{1}{1 + e^{- 10{({A\_{1}^{d}D\_{\\alpha}^{d} - 0.5})}}}$$  

where,

*   *A^d*[1] *D^d[α]* are estimated by using the equations: (7.3) (7.5) in the *d* dimension.

(7.16)  
$$x\_{2}^{d} = \\left\\{ \\begin{matrix} 1 & {if\\left( {x\_{\\beta}^{d} + bstep\_{\\beta}^{d}} \\right) \\geq 1} \\\\ 0 & {othewise} \\\\ \\end{matrix} \\right.$$  

where,

*   *x^d[β]* represents the position (solution) vector of the *β* wolf in the *d* dimension,
*   *bstep^d[β]* represents a binary step in the *d* dimension calculated by the equation:

(7.17)  
$$bstep\_{\\beta}^{d} = \\left\\{ \\begin{matrix} 1 & {if\\, cstep\_{\\beta}^{d} \\geq rand} \\\\ 0 & {othewise} \\\\ \\end{matrix} \\right.$$  

where,

*   *rand* represents a random number uniformly distributed in the range \[0,1\].
*   *cstep^d[β]* represents a continuous step value for the *d* dimension and can be estimated by using the following equation:

where,

(7.18)  
$$cstep\_{\\beta}^{d} = \\frac{1}{1 + e^{- 10{({A\_{1}^{d}D\_{\\beta}^{d} - 0.5})}}}$$  

*   *A^d*[1] *D^d[β]* are estimated by using the equations (7.3) and (7.5) in the *d* dimension.

(7.19)  
$$x\_{3}^{d} = \\left\\{ \\begin{matrix} 1 & {if\\left( {x\_{\\delta}^{d} + bstep\_{\\delta}^{d}} \\right) \\geq 1} \\\\ 0 & {otherwise} \\\\ \\end{matrix} \\right.$$  

where,

*   *x^d[δ]* represents the position (solution) vector of the *δ* wolf in the *d* dimension.
*   *bstep^d[δ]* represents a binary step in the *d* dimension calculated by the following equation:

(7.20)  
$$bstep\_{\\delta}^{d} = \\left\\{ \\begin{matrix} 1 & {i\\text{fsctep}\_{\\delta}^{d} \\geq rand} \\\\ 0 & {otherwise} \\\\ \\end{matrix} \\right.$$  

where,

*   *rand* represents a random number uniformly distributed in the range \[0,1\].
*   *cstep^d[δ]* represents a continuous step value for the *d* dimension and can be estimated by using the following equation:
    
    (7.21)  
    $$cstep\_{\\delta}^{d} = \\frac{1}{1 + e^{- 10{({A\_{1}^{d}D\_{\\delta}^{d} - 0.5})}}}$$  
    
    where,
    
*   *A^d*[1] *D^d[δ]* are estimated by using the equations: (7.3), (7.5) in the *d* dimension.

The crossover method is expressed by the following equation:

(7.22)  
$$x\_{d} = \\left\\{ \\begin{matrix} {a\_{d}\\, if\\, rand < \\frac{1}{3}} \\\\ {b\_{d}\\,\\frac{1}{3} \\leq rand < \\frac{2}{3}} \\\\ {c\_{d}\\, otherwise} \\\\ \\end{matrix} \\right.$$  

where,

*   *a[d]*, *b[d]*, *c[d]* represent the binary values of the first, the second and the third variable in the *d* dimension
*   *x[d]* represents the output of the crossover
*   *rand* represents a random number uniformly distributed in the range \[0,1\].

## Binary grey wolf optimization method II

[Emary et al. (2016](#ch7.xhtml#ref7_4)), proposed a second binary grey wolf optimization method where the updated grey wolf position vector is converted to binary according to the equation:

(7.23)  
$$x\_{d}^{t + 1}\\left\\{ \\begin{array}{l} {1\\, i\\text{f}\\,\\text{sigmoid}\\left( \\frac{x\_{1} + x\_{2} + x\_{3}}{3} \\right) \\geq rand} \\\\ {0\\, otherwise} \\\\ \\end{array} \\right.$$  

where,

*   *rand* represents a random number uniformly distributed in the range \[0,1\].
*   *x^t[d]*^(+1) represents the position (solution) vector of the next time step in the *d* dimension.
*   *t* represents the iteration number.
*   *sigmoid*(*a*) is calculated by the following equation: 1

(7.24)  
$$sigmoid\\left( a \\right) = \\frac{1}{1 + e^{- 10{({x - 0.5})}}}$$  

### Grey wolf with Lévy flight

[Heidari and Pahlavani (2017](#ch7.xhtml#ref7_6)), proposed a modified grey wolf optimizer with Lévy flight to solve the immature convergence problem of the original algorithm. The authors proposed three modifications to the conventional GWO algorithm:

*   the role of the δ wolves in the hierarchy can be played by other grey wolves.
*   the Lévy flight is incorporated into the modified GWO algorithm.
*   the greedy selection is applied on the proposed Lévy flight GWO.

In Lévy flight GWO, the hierarchy includes three types of wolves including alpha, beta, and omega. The position of the grey wolves in the Lévy flight GWO is estimated based on alpha and beta grey wolves by using the following equation:

(7.25)  
$$\\overset{\\rightarrow}{X}\\left( t \\right) = 0.5 \\times \\left( {{\\overset{\\rightarrow}{X}}\_{\\alpha} - {\\overset{\\rightarrow}{A}}\_{1}{\\overset{\\rightarrow}{D}}\_{\\alpha} + {\\overset{\\rightarrow}{X}}\_{\\beta} - {\\overset{\\rightarrow}{A}}\_{2}{\\overset{\\rightarrow}{D}}\_{\\beta}} \\right).$$  

The Lévy function can be expressed by the equation:

(7.26)  
*L*(*s*) ∼ |*s*|^( − 1 − *β*), 0 < *β* ≤ 2  

where,

*   *s* represents a variable.
*   *β* represents the Lévy index for the stability.

The Lévy distribution can be expressed by the equation:

(7.27)  
$$L\\left( {s,\\gamma,\\mu} \\right) = \\left\\{ {\\begin{matrix} \\sqrt{\\frac{\\gamma}{2\\pi}} \\\\ 0 \\\\ \\end{matrix}exp\\left\\lbrack {- \\frac{\\gamma}{2\\left( {s - \\mu} \\right)}} \\right\\rbrack\\frac{1}{\\left( {s - \\mu} \\right)^{3/2}}} \\right.\\begin{matrix} {0 < \\mu < s < \\infty} \\\\ {s \\leq 0} \\\\ \\end{matrix}$$  

where,

*   *μ* represents a shift parameter
*   *gamma parameter γ* > 0 represents a scale parameter

Lévy distribution can also be expressed by using the Fourier transformation:

(7.28)  
*F*(*k*) = exp \[−*α*|*k*|^(*β*)\], 0 < *β* ≤ 2  

where α represents the scale factor in the range \[−1, 1\].

[Heidari and Pahlavani (2017](#ch7.xhtml#ref7_6)), proposed another modification to the original GWO, regarding the new positions’ equation:

(7.29)  
$${\\overset{\\rightarrow}{X}}\_{new}\\left( t \\right) = \\left\\{ \\begin{matrix} {0.5 \\times \\left( {{\\overset{\\rightarrow}{X}}\_{\\alpha} - {\\overset{\\rightarrow}{A}}\_{1}{\\overset{\\rightarrow}{D}}\_{\\alpha} + {\\overset{\\rightarrow}{X}}\_{\\beta} - {\\overset{\\rightarrow}{A}}\_{2}{\\overset{\\rightarrow}{D}}\_{\\beta}} \\right) + \\alpha \\oplus Levi\\left( \\beta \\right)} \\\\ {0.5 \\times \\left( {{\\overset{\\rightarrow}{X}}\_{\\alpha} - {\\overset{\\rightarrow}{A}}\_{1}{\\overset{\\rightarrow}{D}}\_{\\alpha} + {\\overset{\\rightarrow}{X}}\_{\\beta} - {\\overset{\\rightarrow}{A}}\_{2}{\\overset{\\rightarrow}{D}}\_{\\beta}} \\right)} \\\\ \\end{matrix} \\right.\\begin{matrix} {\\left| A \\right| > 0.5} \\\\ {\\left| A \\right| < 0.5} \\\\ \\end{matrix}$$  

where,

*   α represents the step size.
*   *β* represents the Lévy index inside \[0, 2\].
*   represents the entry wise multiplication.

When the parameter |*A| >* 0.5, then the operator is expressed by the equation:

(7.30)  
$${\\overset{\\rightarrow}{X}}\_{new}\\left( t \\right) = 0.5 \\times \\left( {{\\overset{\\rightarrow}{X}}\_{\\alpha} - {\\overset{\\rightarrow}{A}}\_{1}{\\overset{\\rightarrow}{D}}\_{\\alpha} + {\\overset{\\rightarrow}{X}}\_{\\beta} - {\\overset{\\rightarrow}{A}}\_{2}{\\overset{\\rightarrow}{D}}\_{\\beta}} \\right) + rand\\left( {size\\left( D \\right)} \\right) \\oplus Levi\\left( \\beta \\right)$$  

where *D* is the dimension.

[Heidari and Pahlavani (2017](#ch7.xhtml#ref7_6)), proposed, the Mantegna method [Mantegna (1994](#ch7.xhtml#ref7_14)) to be used to produce Lévy flight during the algorithm process. Consequently, the previous equation can be expressed as: *u* ^α

(7.31)  
$$\\left. rand\\left( {size\\left( {Dim} \\right)} \\right) \\oplus Levi\\left( \\beta \\right) \\right.\\sim 0.01\\frac{u}{v^{- \\beta}}\\left( {\\overset{\\rightarrow}{X}\\left( t \\right) - \\overset{\\rightarrow}{X^{\\alpha}}\\left( t \\right)} \\right)$$  

where *u* and *v* are attained from normal distributions as follows:

(7.32)  
*u* ∼ *N*(0,*σ*[*u*]²),*v* ∼ *N*(0,*σ*[*u*]²)  

with,

(7.33)  
$$\\sigma\_{u} = \\left\\lbrack \\frac{\\Gamma\\left( {1 + \\beta} \\right)\\sin\\left( \\frac{\\pi\\beta}{2} \\right)}{\\Gamma\\left( \\frac{1 + \\beta}{2} \\right)\\beta \\times 2^{\\frac{\\beta - 1}{2}}} \\right\\rbrack^{\\frac{1}{\\beta}},\\sigma\_{v} = 1$$  

where,

*   *Γ* represents the conventional gamma function.
*   *β* parameter is a random value inside the \[0, 2\] interval

The *β* variable can improve both the exploitation and exploration processes.

The Lévy-flight search can prevent the GWO from stagnation.

The greedy selection is adopted with *p* probability. The operator is expressed by the equation:

(7.34)  
$$\\overset{\\rightarrow}{X}\\left( {t + 1} \\right) = \\left\\{ \\begin{array}{l} {\\overset{\\rightarrow}{X}\\left( t \\right)\\, f\\left( {{\\overset{\\rightarrow}{X}}\_{new}\\left( t \\right)} \\right) > f\\left( {\\overset{\\rightarrow}{X}\\left( t \\right)} \\right)and\\, r\_{new} < p} \\\\ {{\\overset{\\rightarrow}{X}}\_{new}\\left( t \\right)\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{otherwise}} \\\\ \\end{array} \\right.$$  

where,

*   *r[new]* and *p* represent random values in the interval (0, 1),
*   *f*(*X(t*)) represents the final position fitness value.
*   *X[new]*(*t*) represents the new position.
*   The *p* value is defined randomly in the interval \[0, 1\].

## Whale optimization algorithm

[Mirjalili and Lewis (2016](#ch7.xhtml#ref7_16)), proposed a new nature-inspirated algorithm called whale optimization algorithm. There are seven different whale species: killer, humpback, Minke, Sei, right, finback, and blue. The authors focused on the humpback whales’ hunting strategy. This hunting behavior is named bubble-net feeding method.

[Mirjalili and Lewis (2016](#ch7.xhtml#ref7_16)), mathematically modeled the encircling prey and the spiral bubble-net movement, and the search for prey in order to develop the whale optimization algorithm.

### Encircling prey

Humpback whales are able to recognize the prey location and then encircle it. The best whale search agent position (solution) is determined at the beginning as the target prey, then the other whale search agents are trying to update their positions (solutions) with a direction towards the best whale. The authors proposed the following equations to model this behavior:

(7.35)  
$$\\overset{\\rightarrow}{D} = \\left| {\\overset{\\rightarrow}{C}.\\overset{\\rightarrow}{X^{\*}}\\left( t \\right) - \\overset{\\rightarrow}{X}\\left( t \\right)} \\right|$$  

(7.36)  
$$\\overset{\\rightarrow}{X}\\left( {t + 1} \\right) = \\overset{\\rightarrow}{X^{\*}}\\left( t \\right) - \\overset{\\rightarrow}{A} \\cdot \\overset{\\rightarrow}{D}$$  

where,

*   *t* represents the current iteration.
*   *$\\overset{\\rightarrow}{A}$* and *$\\overset{\\rightarrow}{C}$* represent the coefficient vectors.
*   *X*^(\*) represents the best solution position vector so far.
*   *$\\overset{\\rightarrow}{X}$* represents the position vector.
*   | | represents the absolute value.
*   represents an element-wise multiplication.

The *$\\overset{\\rightarrow}{A}$* and *$\\overset{\\rightarrow}{C}$* vectors are estimated by using the following equations:

(7.37)  
$$\\overset{\\rightarrow}{A} = 2\\overset{\\rightarrow}{a} \\cdot \\overset{\\rightarrow}{r} - \\overset{\\rightarrow}{a}$$  

(7.38)  
$$\\overset{\\rightarrow}{C} = 2 \\cdot \\overset{\\rightarrow}{r}$$  

where,

*   *$\\overset{\\rightarrow}{a}$* represents a parameter linearly decreased from the value 2 to the value 0 during the iterations.
*   *$\\overset{\\rightarrow}{r}$* represents a random vector in the space \[0,1\].

The humpback whales also use a Bubble-net attacking strategy. This method can be modelled as follows:

### Bubble-net attacking strategy (exploitation phase)

The authors modeled the humpback whales’ bubble-net attacking method strategy by proposing two methods:

#### Shrinking encircling method

This behavior is achieved by decreasing the value of *$\\overset{\\rightarrow}{a}$* in the equation(2.3). The parameter *$\\overset{\\rightarrow}{A}$* (fluctuation range) is also decreased by *$\\overset{\\rightarrow}{a}$* according to the above equation. *$\\overset{\\rightarrow}{A}$* expresses a random vector which takes values in the space \[−*a,a*\].

#### Spiral updating position

The spiral updating position is performed by calculating the distance between the whale agent located at point (*X, Y*) and prey located at point (*X*^(\*), *Y*^(\*)). The authors proposed a spiral equation to model the helix-shaped humpback whale movement as follows:

(7.39)  
$$\\overset{\\rightarrow}{X}\\left( {t + 1} \\right) = \\overset{\\rightarrow}{D^{\\prime}} \\cdot e^{bl} \\cdot \\cos\\left( {2\\pi l} \\right) + \\overset{\\rightarrow}{X^{\*}}\\left( t \\right)$$  

where,$\\overset{\\rightarrow}{D'} = \\left| {\\overset{\\rightarrow}{X^{\*}}\\left( t \\right) - \\overset{\\rightarrow}{X}\\left( t \\right)} \\right|$ represents the distance of the *i*th whale from the prey

*   *$\\overset{\\rightarrow}{X}$*\* represents the best solution position so far.
*   *$\\overset{\\rightarrow}{X}$* represents the position vector.
*   *b* represents a constant related to the logarithmic spiral shape
*   *l* represents a random number in the interval \[−1,1\]
*   represents an element-wise multiplication

According to the natural behavior of humpback whales, they swim within a shrinking circle around the prey and also in a spiral shape at the same time. The authors, proposed a probability of 50 percent to choose between either method in order to update the whale position by using the equation:

(7.40)  
$$\\overset{\\rightarrow}{X}\\left( {t + 1} \\right) = \\left\\{ \\begin{matrix} {\\overset{\\rightarrow}{X^{\*}}\\left( t \\right) - \\overset{\\rightarrow}{A} \\cdot \\overset{\\rightarrow}{D}} & {if\\, p < 0.5} \\\\ {\\overset{\\rightarrow}{D^{\\prime}} \\cdot e^{bl} \\cdot \\cos\\left( {2\\pi l} \\right) + \\overset{\\rightarrow}{X^{\*}}\\left( t \\right)} & {if\\, p > 0.5} \\\\ \\end{matrix} \\right.$$  

where *p* represents a random number in the interval \[0,1\].

#### Search for prey (exploration stage)

Furthermore, the humpback whales search for prey randomly. A similar method based on the variation of the *$\\overset{\\rightarrow}{A}$* vector can be applied in the exploration phase in order to search for prey.

In this phase the position of a whale search agent is updated according to a randomly selected whale search agent, in contradiction to the exploration phase where the best search agent so far matters in the process. *$\\overset{\\rightarrow}{A}$* > 1 is utilized in order to allow the whale optimization algorithm to execute a global search. The proposed equations of the model are as follows:

(7.41)  
$$\\overset{\\rightarrow}{D} = \\left| {\\overset{\\rightarrow}{C} \\cdot \\overset{\\rightarrow}{X\_{rand}} - \\overset{\\rightarrow}{X}} \\right|$$  

(7.42)  
$$\\overset{\\rightarrow}{X}\\left( {t + 1} \\right) = \\overset{\\rightarrow}{X\_{rand}} - \\overset{\\rightarrow}{A} \\cdot \\overset{\\rightarrow}{D}$$  

where *$\\overset{\\rightarrow}{X\_{rand}}$[rand]* represents a random whale position (solution) vector selected from the current population.

According to the proposed WOA algorithm ([Mirjalili and Lewis, 2016](#ch7.xhtml#ref7_16)), the population whales are initialized with random positions (solutions), the best whale solution, the algorithm parameters and the maximum number of iterations. The whale search agents update their positions according to the two proposed mechanisms: a randomly chosen whale search agent or the best whale position (solution) so far. Parameter "*a*" is decreased from the value 2 to the value 0 so as to enhance the exploration and the exploitation, accordingly. When the parameter *$\\overset{\\rightarrow}{A}$* > 1 a the random whale search agent is selected. When *$\\overset{\\rightarrow}{A}$* < 1 the best position (solution) is selected for the position update. The value of the *p* parameter is used to permit WOA algorithm to switch between the two mechanisms: the spiral or the circular movement. Finally, the algorithm terminates when it reaches the termination criterion.

The pseudo code of the WOA algorithm is presented below:

#### Whale optimization algorithm

## Whale optimization variants

### Whale optimization with Lévy flight

[Ling et al. (2017](#ch7.xhtml#ref7_12)), proposed a Lévy flight whale optimization algorithm in order to improve the performance of the algorithm in multi-modal and high-dimensional optimization problems. The authors proposed the incorporation of Lévy flight in the whale optimization algorithm to improve the whale optimization algorithm exploration and the exploitation processes. Also, Lévy flight can improve the diversification of the whale search agents, so as to explore the search space more efficiently. The authors implement Lévy flight to update the humpback whale positions (solutions) according to the following equation:

(7.43)  
$$\\overset{\\rightarrow}{X\_{rand}}$$  

where,

*   *$\\overset{\\rightarrow}{X}$* (*t*) represents the position (solution) vector *$\\overset{\\rightarrow}{X}$* at iteration *t*.
*   *μ* represents a uniformly distributed random number.
*   ⊕ represents the entry-wise multiplication.
*   rand represents a random number in the space \[0, 1\].
*   *sign*\[*rand* – 1/2\] takes only three values: 1, 0, −1.

The Lévy flight provides a random walk and the random step length is expressed by the Lévy distribution which is heavy-tailed:

(7.44)  
*L**e**v**y* ∼ *u* = *t*^( − *λ*), 1 < *λ* ≤ 3  

The authors used the Mantegna algorithm ([Mantegna, 1994](#ch7.xhtml#ref7_14)) to simulate a λ distribution by producing random steps with length *s* with the same behavior as the Lévy-flights, according to the equation:

(7.45)  
$$s = \\frac{\\mu}{\\left| v \\right|^{1/\\beta}}$$  

where,

*   *s* is the step length of the Lévy flight, which is *Levy*(*λ*)
*   *λ* = 1 + *β**w**h**e**r**e**β* = 1.5, *μ* = *N*(0,*σ*[*μ*]²)*a**n**d**v* = *N*(0,*σ*[*μ*]²) represent normal stochastic distributions with

(7.46)  
$$\\sigma\_{\\mu} = \\left\\lbrack \\frac{\\Gamma\\left( {1 + \\beta} \\right) \\times \\sin\\left( {\\pi \\times \\beta/2} \\right)}{\\Gamma\\left( {\\left( \\left( {1 + \\beta/2} \\right) \\right) \\times \\beta \\times 2^{{({\\beta - 1})}/2}} \\right)} \\right\\rbrack^{1/\\beta}\\, and\\,\\sigma\_{v} = 1$$  

Lévy flight can improve the search capability of the whale optimization algorithm and prevent it from being trapped in a local minimum. The proposed algorithm, improved the experimental results in unimodal and multimodal benchmark functions that were tested.

The pseudocode of the Lévy flight whale optimization algorithm is presented below ([Ling et al., 2017](#ch7.xhtml#ref7_12)):

### Lévy Flight Whale optimization algorithm

### Binary whale optimization algorithm

[Hussien et al. (2020](#ch7.xhtml#ref7_9)), proposed a binary version of the whale optimization algorithm by using zero or one to update the whale agent position. The authors proposed changing the whale agent position (solution) according to the distance probability and utilized a transfer function in order to map the distance values to probability values for updating the positions. The sigmoid (S-shaped) and hyperbolic tan (V-shaped) functions to transform the original equations:

(7.47)  
$$S\\left( {x\_{i}^{k}\\left( t \\right)} \\right) = \\frac{1}{1 + e^{- d\_{i}^{k}}\\left( t \\right)}$$  

(7.48)  
*V*(*x*[*i*]^(*k*)(*t*)) = |tanh(*x*[*i*]^(*k*)(*t*))|  

where *d^k[i]* (*t*) is the particle distance.

(7.49)  
*x*[*i*]^(*k* + 1)(*t*+1) = {[1    *o**t**h**e**r**w**i**s**e*]^(0 *i**f* *r**a**n**d* < *S*(*x*[*i*]^(*k*)(*t*)))  

*otherwise*

(7.50)  
*x*[*i*]^(*k* + 1)(*t*+1) = {[*x*[*i*]^(*k*)(*t*)    *o**t**h**e**r**w**i**s**e*]^((*x*[*i*]^(*k*)(*t*))^( − 1)  *i**f* *r**a**n**d* < *V*(*x*[*i*]^(*k*)(*t*)))  

where,

*   *x^k[i]* (*t*) represents the position of the *i*th particle at iteration t.
*   (*x^k[i]* (*t*))^(–1) represents the complement of *x^k[i]* (*t*).

[Hussien et al. (2020](#ch7.xhtml#ref7_9)), tested the performance of the proposed binary version of the whale optimization algorithm by using several benchmark functions and engineering design problems. The experimental results showed that the proposed algorithm has a better performance than other optimization algorithms.

## Grasshopper optimization algorithm

[Saremi et al. (2017](#ch7.xhtml#ref7_18)), proposed the Grasshopper optimization algorithm, another nature-inspired algorithm. Grasshoppers are insects. The main feature of the Grasshopper swarm in the larval stage is their small steps which make them move slowly. Also, the Grasshopper swarm, moves abruptly in a long-range when the swarm is in its adulthood. There is attraction or repulsion among the Grasshoppers. When a grasshopper is at a specific distance from another grasshopper, there is no attraction or repulsion. This zone is named comfort zone.

Generally, the proposed nature-inspired algorithms use two search strategies: exploration and exploitation. These two operations are performed by grasshoppers in nature.

The authors proposed the following mathematical model to simulate the swarm behavior of the grasshoppers ([Topaz et al., 2008](#ch7.xhtml#ref7_20)):

(7.51)  
*X*[*i*] = *S*[*i*] + *G*[*i*] + *A*[*i*]  

where,

*   *X[i]* represents the position (solution) of the *i[th]* grasshopper.
*   *S[i]* represents the social interaction.
*   *G[i]* represents the gravitational force exercised on the *i[th]* grasshopper.
*   *A[i]* represents the wind advection.

By incorporating random behavior to the previous equation, it can be expressed as:

(7.52)  
*X*[*i*] = *r*[1]*S*[*i*] + *r*[2]*G*[*i*] + *r*[3]*A*[*i*]  

where, *r*[1], *r*[2], and *r*[3] represent random numbers in the range \[0,1\].

(7.53)  
$$S\_{i} = {\\sum\\limits\_{{}\_{j \\neq 1}^{j = 1}}^{N}{s\\left( d\_{ij} \\right){\\hat{d}}\_{ij}}}$$  

where,

*   *d[ij]* represents the distance between *i[th]* and *j[th]* grasshopper: *d[ij]* = |*x[j]* − *x[i]*|
*   *s* represents a function for the strength of social forces. *x^j* − *x^i*
*   ${\\hat{d}}\_{ij} = \\frac{x\_{j} - x\_{i}}{d\_{ij}}$ represents the vector from *i*[th] to *j*[th] grasshopper.

The *s*(*r*) function, expresses the social forces:

(7.54)  
$$s\\left( r \\right) = fe^{\\frac{- r}{l}} - e^{- r}$$  

where,

*   *f* represents the attraction intensity
*   *l* represents the attraction length scale.

The *G* parameter in equation(7.51) is estimated by the formula:

(7.55)  
*G*[*i*] =  − *g**ê*[*g*]  

where,

*   *g* represents the gravitational constant.
*   *e*̂[*g*] represents a unitary vector with the direction to the center of earth. The *A* parameter in equation(7.51) is estimated by the formula:

(7.56)  
*A*[*i*] = *u**ê*[*w*]  

where,

*   *u* represents a constant drift.
*   *e*̂[*w*] represents a unitary vector in the wind direction.

By combining the previous equations and substituting the s, G, A parameters in equation(7.51), it can be expressed as follows:

(7.57)  
$$X\_{i} = {\\sum\\limits\_{{}\_{j \\neq 1}^{j = 1}}^{N}s}\\left( \\left| {x\_{j} - x\_{i}} \\right| \\right)\\frac{x\_{j} - x\_{i}}{d\_{ij}} - g{\\hat{e}}\_{g} + u{\\hat{e}}\_{w}$$  

where,

*   $s\\left( r \\right) = fe^{\\frac{- r}{l}} - e^{- r}$
*   *N* represents the number of grasshoppers.

The authors proposed a modified version of the above equation, because in the previous model the grasshopper swarm cannot converge, as follows:

(7.58)  
$$X\_{i}^{d} = c\\left( {\\sum\\limits\_{{}\_{j \\neq 1}^{j = 1}}^{N}{c\\frac{ub\_{d} - lb\_{d}}{2}s\\left( \\left| {x\_{j}^{d} - x\_{i}^{d}} \\right| \\right)\\frac{x\_{j} - x\_{i}}{d\_{ij}}}} \\right) + {\\hat{T}}\_{d}$$  

where,

*   *ub[d]* represents the upper bound in the *d*th dimension,
*   *lb[d]* represents the lower bound in the *d*th dimension
*   $s\\left( r \\right) = fe^{\\frac{- r}{l}} - e^{- r}$
*   *T*̂[*d*] represents the best solution found so far in the *d*th dimension.
*   *c* represents a decreasing coefficient parameter to reduce the comfort repulsion and attraction zones.

The first term in the equation simulates the interaction between the grasshoppers and the second term, simulates the inclination of the grasshoppers towards the food source. The adaptive parameter *c* is similar to the inertial weight (*w*) in the particle swarm optimization algorithm. This adaptive parameter is used to facilitate the balance between exploration and exploitation. The parameter *s*(|*x[j]* − *x[i]*|) shows whether a grasshopper must be repelled (exploration) or attracted (exploitation) to the target.

In order to balance the exploration and the exploitation, the parameter *c* will be decreased while the number of iterations increase to promote exploitation:

(7.59)  
$$c = c\_{\\max} - l\\frac{c\_{\\max} - c\_{\\min}}{L}$$  

where,

*   *c[max]* represents the maximum value
*   *c[min]* represents the minimum value
*   *l* represents the current iteration,
*   *L* represents the maximum number of iterations.

Consequently, repulsion makes the grasshopper agents explore the search space, and attraction makes the grasshopper agents exploit regions of the search space. The balance between these two operations: exploration and exploitation, is performed by the adaptive coefficient. The pseudo code of the grasshopper optimization algorithm is as follows ([Saremi et al., 2017](#ch7.xhtml#ref7_18)):

### Grasshopper Optimization Algorithm

## Grasshopper optimization variants

### Chaotic grasshopper optimization algorithm

[Arora and Anand (2019](#ch7.xhtml#ref7_2)), proposed a Chaotic grasshopper optimization algorithm. The authors proposed the use of c[1], c[2] instead of the c coefficient, according to the following equation:

(7.60)  
$$X\_{i}^{d} = c\_{1}\\left( {\\sum\\limits\_{j = 1,j \\neq i}^{N}{c\_{2}\\frac{ub\_{d} - lb\_{d}}{2}s\\left( \\left| {x\_{j}^{d} - x\_{i}^{d}} \\right| \\right)\\frac{x\_{j} - x\_{i}}{d\_{ij}}}} \\right) + {\\hat{T}}\_{d}$$  

The coefficient c[1] is used to balance the exploration and exploitation, and coefficient c[2] is utilized to decrease the attraction, comfort and repulsion zones between the grasshoppers.

Chaotic maps have been used in several optimization algorithms to improve their performance. [Arora and Anand (2019](#ch7.xhtml#ref7_2)), proposed adapting the c[1] and c[2] coefficients by using several chaotic maps.

#### Adapting c[1] coefficient with chaotic maps

The coefficient c[1] is used to balance the exploration and exploitation. [Arora and Anand (2019](#ch7.xhtml#ref7_2)), proposed several chaotic maps to adapt the c[1] coefficient in the interval \[0, 1\] according to the equation:

(7.61)  
$$X\_{i}^{d} = c\_{1}\\left( t \\right)\\left( {\\sum\\limits\_{j = 1,j \\neq i}^{N}{c\_{2}\\frac{ub\_{d} - lb\_{d}}{2}s\\left( \\left| {x\_{j}^{d} - x\_{i}^{d}} \\right| \\right)\\frac{x\_{j} - x\_{i}}{d\_{ij}}}} \\right) + {\\hat{T}}\_{d}$$  

where,

*   *c[1]*(*t*) represents the chaotic map value in the *t[th]* iteration
*   *X[i]* represents the i[th] grasshopper.

#### Adapting c[2] coefficient with chaotic maps

The coefficient c[2] is utilized to decrease the attraction, comfort and repulsion zones between the grasshoppers. The c[2] coefficient is adapted in the interval \[0, 1\] by using chaotic maps according to the equation:

(7.62)  
$$X\_{i}^{d} = c\_{1}\\left( {\\sum\\limits\_{j = 1,j \\neq i}^{N}{c\_{2}\\left( t \\right)\\frac{ub\_{d} - lb\_{d}}{2}s\\left( \\left| {x\_{j}^{d} - x\_{i}^{d}} \\right| \\right)\\frac{x\_{j} - x\_{i}}{d\_{ij}}}} \\right) + {\\hat{T}}\_{d}$$  

where,

*   *c*[2](*t*) represents the chaotic map value in the *t[th]* iteration.
*   *X[i]* represents the *i[th]* grasshopper.

### Improved grasshopper optimization algorithm

[Luo et al. (2018](#ch7.xhtml#ref7_13)), proposed an improved grasshopper optimization algorithm, by using three methods: Levy flight, opposition-based learning, and Gaussian mutation. These strategies were used for better balancing the two main operations: exploration and exploitation.

#### Gaussian mutation

The Gaussian mutation method was proposed by [Luo et al. (2018](#ch7.xhtml#ref7_13)), in order to increase the grasshopper optimization algorithm population diversity in order to increase the search capability of the algorithm for finding the global optimum. The modified equation of the original grasshopper optimization algorithm is:

(7.63)  
$$X\_{i}^{d} = c\\left( {\\sum\\limits\_{\\begin{array}{l} {j = 1} \\\\ {j \\neq i} \\\\ \\end{array}}^{N}{c\\frac{ub\_{d} - lb\_{d}}{2}s\\left( \\left| {x\_{j}^{d} - x\_{i}^{d}} \\right| \\right)\\frac{x\_{j} - x\_{i}}{d\_{ij}}}} \\right) \\oplus G\\left( \\alpha \\right) + {\\hat{T}}\_{d}$$  

#### Levy flight

After the grasshopper position update, Levy flight method is proposed by the authors to produce a new solution, by using the following equations:

(7.64)  
*X*[*i*]^(*l**e**v**y*)  = *X*[*i*]^(\*) + *r**a**n**d*(*d*) ⊕ *l**e**v**y*(*β*)  

(7.65)  
$$X\_{i}^{t + 1} = \\left\\{ \\begin{matrix} X\_{i}^{levy} & {fitness\\left( X\_{i}^{levy} \\right) > fitness\\left( X\_{i}^{\*} \\right)} \\\\ X\_{i}^{\*} & {otherwise} \\\\ \\end{matrix} \\right.$$  

where,

*   *X*\*[*i*] represents the new position (solution) of the *i*[th] grasshopper.
*   rand(*d*) represents a *d*\-dimensional vector randomly generated in \[0,1\].

#### Opposition-based learning

The authors, also used the opposition-based learning method in order to produce the oppositional population which corresponds to the current grasshopper population after the positions of the grasshopper are updated. This method helps the algorithm to search more effectively and enhance the algorithm exploration ability. The grasshopper oppositional population can be produced by the following equation:

(7.66)  
*X*[*i*]^(*o**p*) = *L**B* + *U**B* − *T* + *r*(*T*−*X*[*i*])  

where,

*   *X^(op)[i]* represents the position of the *i*[th] opposite grasshopper.
*   *LB* and *UB* represent the lower and the upper bounds correspondingly.
*   *T* represents the position (solution) of the best grasshopper.
*   *r* represents a random vector in the space (0,1).
*   *X[i]* represents the position (solution) vector of the *i*[th] grasshopper.

The proposed method for improving the original grasshopper optimization algorithm by using these three strategies was tested in several benchmark functions. The experimental results showed an improved accuracy compared to other swarm optimization algorithms such as particle swarm optimization and differential evolution.

## References

*   [Altan, A., Karasu, S. and Zio, E.](#ch7.xhtml#R_ref7_1) (2021). A new hybrid model for wind speed forecasting combining long short-term memory neural network, decomposition methods and grey wolf optimizer. Applied Soft Computing, 100: 106996.
*   [Arora, S. and Anand, P.](#ch7.xhtml#R_ref7_2) (2019). Chaotic grasshopper optimization algorithm for global optimization. Neural Computing and Applications, 31(8): 4385–4405. doi:[10.1007/s00521-018-3343-2.](http://doi.org/10.1007/s00521-018-3343-2)
*   [Emary, E., Zawbaa, H. M., Grosan, C. and Hassenian, A. E.](#ch7.xhtml#R_ref7_3) (2015). Feature subset selection approach by gray-wolf optimization. pp. 1–13. *In* Afro-European Conference for Industrial Advancement. Springer, Cham.
*   [Emary, E., Zawbaa, H. M. and Hassanien, A. E.](#ch7.xhtml#R_ref7_4) (2016). Binary grey wolf optimization approaches for feature selection. Neurocomputing, 172: 371–381.
*   [Ghalambaz, M., Yengejeh, R. J. and Davami, A.H.](#ch7.xhtml#R_ref7_5) (2021). Building energy optimization using Grey Wolf Optimizer (GWO). Case Studies in Thermal Engineering, 27: 101250.
*   [Heidari, A. A. and Pahlavani, P.](#ch7.xhtml#R_ref7_6) (2017). An efficient modified grey wolf optimizer with Lévy flight for optimization tasks. Applied Soft Computing, 60: 115–134. doi:[https://doi.org/10.1016/j.asoc.2017.06.044.](https://doi.org/10.1016/j.asoc.2017.06.044.)
*   [Helmi, A. M., Al-Qaness, M. A., Dahou, A., Damaševičius, R., Krilavičius, T. et al.](#ch7.xhtml#R_ref7_7) (2021). A novel hybrid gradient-based optimizer and grey wolf optimizer feature selection method for human activity recognition using smartphone sensors. Entropy, 23(8): 1065.
*   [Hu, P., Pan, J. S. and Chu, S. C.](#ch7.xhtml#R_ref7_8) (2020). Improved binary grey wolf optimizer and its application for feature selection. Knowledge-Based Systems, 195: 105746.
*   [Hussien, A. G., Hassanien, A. E., Houssein, E. H., Amin, M., Azar, A. T. et al.](#ch7.xhtml#R_ref7_9) (2020). New binary whale optimization algorithm for discrete optimization problems. Engineering Optimization, 52(6): 945–959. doi:[10.1080/0305215X.2019.1624740.](http://doi.org/10.1080/0305215X.2019.1624740)
*   [Jayabarathi, T., Raghunathan, T., Adarsh, B. R. and Suganthan, P. N.](#ch7.xhtml#R_ref7_10) (2016). Economic dispatch using hybrid grey wolf optimizer. Energy, 111: 630–641.
*   [Li, L., Fu, Y., Fung, J. C., Qu, H., Lau, A. K. et al.](#ch7.xhtml#R_ref7_11) (2021). Development of a backpropagation neural network and adaptive grey wolf optimizer algorithm for thermal comfort and energy consumption prediction and optimization. Energy and Buildings, 253: 111439.
*   [Ling, Y., Zhou, Y. and Luo, Q.](#ch7.xhtml#R_ref7_12) (2017). Lévy flight trajectory-based whale optimization algorithm for global optimization. IEEE Access, 5: 6168–6186. doi:[10.1109/ACCESS.2017.2695498.](http://doi.org/10.1109/ACCESS.2017.2695498)
*   [Luo, J., Chen, H., Zhang, Q., Xu, Y., Huang, H. et al.](#ch7.xhtml#R_ref7_13) (2018). An improved grasshopper optimization algorithm with application to financial stress prediction. Applied Mathematical Modelling, 64: 654–668. doi: [https://doi.org/10.1016/j.apm.2018.07.044.](https://doi.org/10.1016/j.apm.2018.07.044.)
*   [Mantegna, R. N.](#ch7.xhtml#R_ref7_14) (1994). Fast, accurate algorithm for numerical simulation of Levy stable stochastic processes. Physical Review E, 49(5): 4677.
*   [Mirjalili, S., Mirjalili, S. M. and Lewis, A.](#ch7.xhtml#R_ref7_15) (2014). Grey Wolf Optimizer. Advances in Engineering Software, 69: 46–61. doi:[https://doi.org/10.1016/j.advengsoft.2013.12.007.](https://doi.org/10.1016/j.advengsoft.2013.12.007.)
*   [Mirjalili, S. and Lewis, A.](#ch7.xhtml#R_ref7_16) (2016). The whale optimization algorithm. Advances in Engineering Software, 95: 51–67.
*   [Nadimi-Shahraki, M. H., Taghian, S. and Mirjalili, S.](#ch7.xhtml#R_ref7_17) (2021). An improved grey wolf optimizer for solving engineering problems. Expert Systems with Applications, 166: 113917.
*   [Saremi, S., Mirjalili, S. and Lewis, A.](#ch7.xhtml#R_ref7_18) (2017). Grasshopper optimisation algorithm: theory and application. Advances in Engineering Software, 105: 30–47.
*   [Thakur, N., Awasthi, Y. K. and Siddiqui, A. S.](#ch7.xhtml#R_ref7_19) (2021). Reliability analysis and power quality improvement model using enthalpy based grey wolf optimizer. Energy Systems, 12(1): 31–59.
*   [Topaz, C. M., Bernoff, A. J., Logan, S. and Toolson, W.](#ch7.xhtml#R_ref7_20) (2008). A model for rolling swarms of locusts. The European Physical Journal Special Topics, 157(1): 93–109.
*   [Wong, L. I., Sulaiman, M. H., Mohamed, M. R. and Hong, M. S.](#ch7.xhtml#R_ref7_21) (2014, December). Grey Wolf Optimizer for solving economic dispatch problems. 150–154. *In* 2014 IEEE International Conference on Power and Energy (PECon). IEEE.
*   [Zhang, Z. and Hong, W.-C.](#ch7.xhtml#R_ref7_22) (2021). Application of variational mode decomposition and chaotic grey wolf optimizer with support vector regression for forecasting electric loads. Knowledge-Based Systems, 228: 107297. doi:[https://doi.org/10.1016/j.knosys.2021.107297.](https://doi.org/10.1016/j.knosys.2021.107297.) 

# Chapter 8 Machine Learning Optimization Applications

This chapter is devoted to machine learning optimization applications, such as artificial neural network optimization. A neural network can be optimized by using swarm and evolutionary optimization methods in several ways, such as: weight optimization, structure optimization, feature selection with evolutionary algorithms. Illustrative real-world examples are presented with real datasets, by using several methods to optimize a neural network such as: genetic algorithm, particle swarm optimization and ant colony optimization.

## Artificial neural networks

The Artificial Neural Networks (ANNs) are artificial computational systems that simulate the neural architecture of a human brain. A neural network elaborates the data from the input variables. The input data traverse through the neuron connections and after being processed, the output results are estimated according to the input parameters ([Basheer and Hajmeer, 2000](#ch8.xhtml#ref8_3); [Panchal et al., 2011](#ch8.xhtml#ref8_21)).

In a feed forward multilayer neural network, the neurons are connected only to a forward direction and the typical architecture consists of an input layer, one or more hidden layers and an output layer. Each layer is developed by a number of neurons ([Castro et al., 2000](#ch8.xhtml#ref8_9); [Honik, 1991](#ch8.xhtml#ref8_13); [Yam and Chow, 2001](#ch8.xhtml#ref8_26)).

Several kinds of activation functions can be utilized in a multilayer perceptron. When the sigmoid function is implemented, then the output of the hidden layer neuron *j* can be estimated by using the following equation:

(8.1)  
$$s\_{j} = {\\sum\\limits\_{i = 1}^{n}w\_{ij}}I\_{i} + \\beta\_{j}$$  

(8.2)  
$$f\_{j}(x) = \\frac{1}{1 + e^{- S\_{j}}}$$  

where,

*   *S[j]* represents the weighted summation of the input hidden layer neuron *j*
*   *I[i]* represents the input variable *i*
*   *w[ij]* represents the connection weights between *I[i]* and the hidden neuron *j*.

After estimating the output of every neuron in the hidden layer, the output of the neural network can be found by the following equation:

(8.3)  
$${\\hat{y}}\_{k} = {\\sum\\limits\_{i = 1}^{m}W\_{kj}}f\_{i} + \\beta\_{k}$$  

### Weight optimization of a neural network

The weight optimization can be implemented by using swarm and evolutionary optimization methods ([Ilonen et al., 2003](#ch8.xhtml#ref8_14); [Socha and Blum, 2007](#ch8.xhtml#ref8_22)). A fitness function is set in order to be used to train the neural network. The most common objective function that is used is an error metric. In regression problems the most common metrics are: the mean squared error (MSE) or root mean squared error (RMSE) or mean absolute error (MAE) which can be utilized as objective functions.

In classification problems other metrics can be utilized, such as: accuracy, precision, recall, F1and kappa. After the selection of the objective function, the swarm topology is developed. Each particle position represents a solution to the objective function optimization problem and the neural network weight vector is optimized until the swarm finds the best solution for the objective function.

### Topology optimization of a neural network

Swarm intelligence strategies can be also implemented to optimize several parameters of a neural network such as the number of the hidden neurons in the hidden layer. Each particle represents the number of hidden neurons in the hidden layer.

The objective function should be set for the swarm intelligence method or for the genetic algorithm in order to optimize the neural network. The most common objective function that is utilized is an error metric. In regression problems and in classification problems several error metrics can be used as objective functions ([Benardos and Vosniakos, 2007](#ch8.xhtml#ref8_4); [Mirjalili et al., 2012](#ch8.xhtml#ref8_17); [Zhang and Shao, 2000](#ch8.xhtml#ref8_27)).

According to several researches, swarm intelligence techniques have a better performance in artificial neural network optimization than other optimization algorithms, such as genetic algorithm ([Anand and Suganthi, 2020](#ch8.xhtml#ref8_1); [Moayedi et al., 2019](#ch8.xhtml#ref8_18)), or artificial bee colony ([Koopialipoor et al., 2019](#ch8.xhtml#ref8_15)), and non-dominated sorting genetic algorithm II (NSGA-II) ([Anand and Suganthi, 2020](#ch8.xhtml#ref8_1); [Nourbakhsh et al., 2011](#ch8.xhtml#ref8_20)).

## Neural network training with PSO, ACO, GA

In this experiment, the iris dataset is utilized in order to train an artificial neural network (ANN) with 9 hidden neurons in the hidden layer. The Iris dataset was used for the experiments. The neural network has four inputs. The Iris dataset has five attributes, sepal length, sepal width, petal width and petal length, and an attribute which is corresponding to the class of the flower: Iris setosa, Iris virginica and Iris versicolor.

### Experimental setup

#### Genetic algorithm parameters

 
| Maximum Number of generations (Iterations) MaxIt: || 1000 |
| --- | --- |
| Chromosome Population: || 200 |
| Number of genes in each chromosome: || 75 |
| Selection: Roulette wheel ||  |
| Crossover type: single point Crossover probability || 1 |
| Mutation: || Uniform |
| Mutation probability: || 0.01 |
| *PSO parameters* ||  |
| Maximum Number of Iterations MaxIt: || 1000 |
| Swarm topology: Fully connected ||  |
| Swarm Population: || 200 |
| Inertia weight: || 0.33 |
| coefficient parameter of personal learning: || *c*[1] = 1.0 coefficient parameter of global learning *c*[2] = 1.5 |
| *ACO parameters* ||  |
| Maximum Number of generations (Iterations) MaxIt: || 1000 |
| Ant Population: || 200 |
| Initial pheromone value: || Initial\_pher = 1e-6 |
| pheromone update quantity constant: || Q = 20 |
| Exploration constant: || q = 1 |
| Global pheromone decay rate: || α = 0.9 |
| Local pheromone decay rate: || r = 0.5 |
| Evaporation Rate: || ρ = 0.05 |

#### Experimental results

According to the results the best models were the PSO-ANN and the GA-ANN models compared to the ACO-ANN model. The PSO-ANN model has much faster convergence compared to the other models.

![Figure 8.1. Convergence curves and classification accuracies of the models.](images/fig8_1_B.jpg)

Figure 8.1. Convergence curves and classification accuracies of the models.

 

## Feature selection with swarm intelligence and genetic algorithm

### Problem definition

The application of machine learning techniques has been studied by several researchers in the field of energy forecasting ([Azadeh et al., 2013](#ch8.xhtml#ref8_2); [Candanedo et al., 2017](#ch8.xhtml#ref8_8); [Ekonomou, 2010](#ch8.xhtml#ref8_12); [Kouziokas, 2019](#ch8.xhtml#ref8_16)). [Candanedo et al. (2017](#ch8.xhtml#ref8_8)) proposed data driven prediction models regarding the energy use of appliances in low-energy houses by implementing machine learning models such as support vector machines, random forest and gradient boosting machines. [Moldovan and Slowik (2021](#ch8.xhtml#ref8_19)), developed forecasting models for the energy consumptions of appliances by combining multiobjective binary grey wolf optimization method with machine learning methods such as: support vector machines, random forest, extra trees and K-nearest neighbours.

In this section, the appliances energy prediction in smart houses with IoT devices is performed, by using artificial neural network models combined with particle swarm optimization and genetic algorithm.

### Data analysis in machine learning

The data analysis methodology in machine learning mainly includes several stages such as: data collection, data cleansing, normalization and preparation, feature selection, development of the machine learning models by testing several architectures and finally model evaluation by using the appropriate evaluation metrics.

### Energy consumption dataset

The appliances’ energy prediction dataset was acquired by the machine learning repository[¹](#fn1)

### Data pre-processing

The data was pre-processed so as to erase incoherencies and null values. The output parameter for the machine learning methods is the “appliances’ energy consumption”. The input vector is all the other variables of the dataset. The dataset was normalized by using the min-max normalization method.

### Normalization

The min-max normalization method was used to transform the values of the dataset in the interval \[0,1\], according to the following equation:

(8.4)  
$$n\_{i} = \\frac{x\_{i} - \\min\\left( x \\right)}{\\max\\left( x \\right) - \\min\\left( x \\right)}$$  

where,

*   *n[i]* illustrates the ith normalized value.
*   *x[i]* illustrates the ith sample value.
*   min(*x*) illustrates the minimum value in the dataset.
*   *max*(*x*) illustrates the maximum value in the dataset.

 

Table 8.1. Data variables and description.

  
| Data variables || Units || Number of Variable |
| --- | --- | --- |
| Appliances’ energy consumption || Wh || 1 |
| --- | --- | --- |
| Light energy consumption || Wh || 2 |
| T1, Temperature in kitchen area || °C || 3 |
| RH1, Humidity in kitchen area || % || 4 |
| T2, Temperature in living room area || °C || 5 |
| RH2, Humidity in living room area || % || 6 |
| T3, Temperature in laundry room area || °C || 7 |
| RH3, Humidity in laundry room area || % || 8 |
| T4, Temperature in office room || °C || 9 |
| RH4, Humidity in office room || % || 10 |
| T5, Temperature in bathroom || °C || 11 |
| RH5, Humidity in bathroom || % || 12 |
| T6, Temperature outside the building (north side) || °C || 13 |
| RH6, Humidity outside the building || % || 14 |
| T7, Temperature in ironing room || °C || 15 |
| RH\_7, Humidity in ironing room || % || 16 |
| T8, Temperature in teenager room 2 || °C || 17 |
| RH\_8, Humidity in teenager room 2 || % || 18 |
| T9, Temperature in parents room || °C || 19 |
| RH\_9, Humidity in parents room || % || 20 |
| To, Temperature outside (from Chievres weather station) || °C || 21 |
| Pressure (from Chievres weather station) || mm Hg || 22 |
| RH\_out, Humidity outside (from Chievres weather station) || % || 23 |
| Wind speed (from Chievres weather station) || m/s || 24 |
| Visibility (from Chievres weather station) || km || 25 |
| Tdewpoint (from Chievres weather station) || °C || 26 |
| rv1, Random variable 1 || nondimensional || 27 |
| rv2, Random variable 2 || nondimensional || 28 |

## Processing dataset outliers

The selected dataset appears extremely high and low values which can affect the generalization ability of the machine learning models. The best method for developing improved machine learning models is to remove the extreme values. In order to discover the dataset outliers regarding the output, some statistic measures will be used such as, the sample mean, the standard deviation, the kurtosis and the skewness. The sample mean *X̄* is calculated, according to the following equation:

(8.5)  
$$\\overline{X} = \\frac{\\sum\_{i = 1}^{n}X\_{i}}{n}$$  

The sample standard deviation is calculated, according to the following equation:

(8.6)  
$$S = \\left\\lbrack {\\sum\_{i = 1}^{n}{\\left( {X\_{i} - \\overline{X}} \\right)^{2}/\\left( {n - 1} \\right)}} \\right\\rbrack^{1/2}$$  

The skewness is a statistical measure of symmetry of the probability distribution. The larger the absolute value of the skewness is, the greater deviation has from the normal distribution. The skewness is calculated by the following equation ([Wang et al., 2018](#ch8.xhtml#ref8_25)):

(8.7)  
$$Skewness = \\frac{\\sum\\limits\_{i = 1}^{N}\\left( {X\_{i} - \\overline{X}} \\right)^{3}}{\\left( {n - 1} \\right)S^{3}}$$  

The Kurtosis is a statistical measure which shows if the data are heavy-tailed or light-tailed compared to a normal distribution and it is calculated, according to the following equation:

(8.8)  
$$Kurtosis = \\frac{\\sum\\limits\_{i = 1}^{N}\\left( {X\_{i} - \\overline{X}} \\right)^{4}}{\\left( {n - 1} \\right)S^{4}}$$  

The kurtosis for the standard normal distribution is equal to 3. Some sources in the literature propose the following equation for calculating kurtosis, referred also as “excess kurtosis” ([Wang et al., 2018](#ch8.xhtml#ref8_25)):

(8.9)  
$$Kurtosis = \\frac{\\sum\\limits\_{i = 1}^{N}\\left( {X\_{i} - \\overline{X}} \\right)^{4}}{\\left( {n - 1} \\right)S^{4}} - 3.$$  

If the distribution is normal then the rule 1.5\*IQR can be used, where IQR represent the interquartile range between *Q[1]* and *Q[2]* quartiles of the distribution. The lower and the upper bounds can be calculated by using the formulas:

(8.10)  
*l**o**w**e**r* *b**o**u**n**d* = *Q*[1] − 1.5 \* *I**Q**R*  

(8.11)  
*u**p**p**e**r* *b**o**u**n**d* = *Q*[2] + 1.5 \* *I**Q**R*  

In this case, the kurtosis of the sample is –0.0023 and the skewness is positive 0.7903 and differs from the normal distribution. So, the 2*\*S* rule will be used to remove the outliers. According to this rule, the sample standard deviation *S* of the target values is estimated and the data outlier instances are removed by calculating the lower and the upper bounds according to the formulas:

(8.12)  
$$lower\\, bound = \\overline{X} - 2\*S$$  

(8.13)  
$$upper\\, bound = \\overline{X} + 2\*S$$  

where

*   *X̄* represents the sample mean.
*   *S* illustrates the sample standard deviation.

The sample mean was 24.75 and the sample standard deviation was 64.68, so according to the above equations the lower bound was 15.18 and the upper bound 114.18.

## Cost-based feature selection with swarm intelligence

The cost function is generally utilized to evaluate the performance of a Machine Learning model. There are several cost functions such as, Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), Root Mean Squared Logarithmic Error (RMSLE). The cost-based feature subset selection by using swarm and evolutionary intelligence is based on the combination of a classifier or regressor which is evaluated for its performance by a cost function, like MSE, RMSE in regression or accuracy, F1 score, etc. in classification and a swarm or evolutionary optimization method which operates as an optimization stochastic method exploring the search space in order to find the optimal subset of features which yield the best results. The mean squared error (MSE) is expressed by the equation:

(8.14)  
$$\\text{MSE=}\\frac{\\sum\_{n}^{i - 1}\\left( {Y\_{i} - \\overset{\\land}{Y\_{i}}} \\right)^{2}}{n}$$  

where

*   *Y[i]* represents the actual value.
*   *Ŷ*[*i*] represents the predicted value.
*   *n* represents the number of measurements (instances).

## Correlation-based feature selection with swarm intelligence

Since, cost-based methods are much more expensive and highly time-consuming methods to be used in combination with swarm intelligence subset search methods, usually a correlation-based feature subset selection method is utilized. Hall (1999), proposed *Merit*, as a measure of correlation. The Merit is similar to Pearson’s correlation equation, and can be used to evaluate the correlation-based feature selection (CFS) algorithm. In order to define the subsets containing the highly class-correlated features and not uncorrelated to each other, the merit measure was proposed by (Hall, 1999):

(8.15)  
$$\\text{MSE=}\\frac{\\sum\_{n}^{i - 1}\\left( {Y\_{i} - \\overset{\\land}{Y\_{i}}} \\right)^{2}}{n}$$  

where:

*   *M* *erit*[*s*] expresses the merit of a subset *S* which contains *k* features
*   *r*[cf] indicates the average correlation with the class
*   *r*[*ff*] indicates the average intercorrelation.

The subset which has the highest value of merit is selected. Swarm intelligence algorithms are applied as subset search methods in combination with CFS to improve the efficiency of the CFS algorithm.

### Experimental setup

In this experiment, the CFS merit was selected as the fitness function for the swarm and evolutionary algorithms. Several swarm and evolutionary-based feature selection methods were utilized: genetic algorithm, geometric particle swarm optimization, evolutionary algorithm, chaotic harmony search and chaotic Cuckoo search.

### Genetic algorithm

#### GA algorithm parameters

 
| Population size: || 20 |
| --- | --- |
| Number of generations: || 20 |
| Selection: || Roulette wheel |
| Crossover type: || single point |
| Mutation: || Uniform |
| Probability of crossover: || 0.6 |
| Probability of mutation: || 0.033 |

#### Genetic Algorithm results

The fitness values of the chromosomes in the last generation of the genetic algorithm are illustrated in the next table.

Table 8.2. Genetic algorithm results of the 20th generation.

  
| Chromosome || Fitness value || Subset |
| --- | --- | --- |
| **1** || **0.43273** || **1 4 16 17** |
| --- | --- | --- |
| 2 || 0.43273 || 1 4 16 17 |
| 3 || 0.39589 || 1 2 4 10 16 17 22 |
| 4 || 0.33461 || 1 16 17 21 24 |
| 5 || 0.39 || 1 4 16 17 24 |
| 6 || 0.43273 || 1 4 16 17 |
| 7 || 0.43273 || 1 4 16 17 |
| 8 || 0.35691 || 1 4 10 14 16 17 21 |
| 9 || 0.38071 || 1 4 14 16 17 19 |
| 10 || 0.37789 || 1 4 15 16 17 |
| 11 || 0.37649 || 1 2 3 4 16 17 |
| 12 || 0.42288 || 1 4 16 17 22 |
| 13 || 0.43273 || 1 4 16 17 |
| 14 || 0.32487 || 1 4 16 25 |
| 15 || 0.40494 || 1 4 16 17 21 |
| 16 || 0.43273 || 1 4 16 17 |
| 17 || 0.39774 || 1 4 16 |
| 18 || 0.33358 || 1 4 8 11 15 17 |
| 19 || 0.42155 || 1 4 17 |
| 20 || 0.37404 || 1 2 4 16 17 22 25 |

According to the best fitness value (the biggest) the selected attributes in the feature selection with genetic algorithm were five: 1, 4, 16, 17:

*   Lights
*   T2
*   T8
*   RH\_8

### Geometric PSO

#### GPSO parameters

Geometric PSO (GPSO) was used for the feature selection as proposed by Moraglio et al. (2007). The parameters for the experiments were the following.

 
| Population size: || 20 |
| --- | --- |
| Swarm topology: || Fully connected |
| Number of iterations: || 20 |
| Coefficient *w*[1]: || *w*[1] = 0.33 |
| Coefficient *w*[2]: || *w*[2] = 0.33 |
| Coefficient *w*[3]: || *w*[3] = 0.34 |
| Crossover type: || three-parent mask-based |
| Mutation type: || bit-flip |
| Probability of mutation: || 0.01 |

#### GPSO results

The fitness values of the GPSO particles in the last generation of the GPSO algorithm are illustrated in the next table.

According to the best fitness value (the biggest) the selected attributes in the feature selection with GPSO algorithm were: 1, 2, 16, 17, 22

*   Lights
*   T1
*   T8

 

Table 8.3. GPSO algorithm results of the 20th iteration.

  
| Particle || Fitness value || Subset |
| --- | --- | --- |
| 1 || 0.41967 || 1 2 16 17 22 |
| --- | --- | --- |
| 2 || 0.41967 || 1 2 16 17 22 |
| 3 || 0.41967 || 1 2 16 17 22 |
| 4 || 0.41967 || 1 2 16 17 22 |
| 5 || 0.41967 || 1 2 16 17 22 |
| 6 || 0.41967 || 1 2 16 17 22 |
| 7 || 0.41967 || 1 2 16 17 22 |
| 8 || 0.41967 || 1 2 16 17 22 |
| 9 || 0.41967 || 1 2 16 17 22 |
| 10 || 0.41967 || 1 2 16 17 22 |
| 11 || 0.41967 || 1 2 16 17 22 |
| 12 || 0.38319 || 1 2 6 11 16 17 22 |
| 13 || 0.39684 || 1 2 6 17 22 |
| 14 || 0.41967 || 1 2 16 17 22 |
| 15 || 0.41967 || 1 2 16 17 22 |
| 16 || 0.41967 || 1 2 16 17 22 |
| 17 || 0.41967 || 1 2 16 17 22 |
| 18 || 0.41967 || 1 2 16 17 22 |
| 19 || 0.3875 || 1 2 7 16 17 22 |
| 20 || 0.41967 || 1 2 16 17 22 |

*   RH\_8
*   RH\_out

### Chaotic harmony search

#### Algorithm parameters

 

 
| Initial population size of new harmonies: || 20 |
| --- | --- |
| Number of iterations: || 20 |
| Mutation: bit-flip ||  |
| Mutation probability: || 0.01 |
| Harmony Memory Size: || 25 |
| Harmony Memory Accepting Rate: || *r[accept]* = 0.9 |
| Initial Pitch Adjustment Rate (PAR): || *r[pitch]* = 0.4 |
| Chaotic method for PAR: || Logistic map |
| Logistic map coefficient: || 4.0 |
| PAR Minimum Bound (*PAR*[*min*]): || 0.4 |
| PAR Maximum Bound (*PAR*[*max*]): || 0.9 |
| Pitch Bandwidth: || b = 0.02\*(*PAR*[*max*] – *PAR*[*min*]) |

#### Chaotic harmony search results

The fitness values of the harmonies in the last generation of the chaotic harmony search algorithm with mutation algorithm are illustrated in the next table.

Table 8.4. Chaotic harmony search with mutation algorithm results of the 20th iteration which had the optimal results.

  
| Harmony || Fitness value || Subset |
| --- | --- | --- |
| 1 || 0.27533 || 7 8 9 12 17 22 24 |
| --- | --- | --- |
| 2 || 0.33034 || 1 3 4 12 17 21 |
| **3** || 0.35268 || 1 4 8 10 13 17 |
| 4 || 0.32453 || 1 4 6 8 15 21 22 27 |
| 5 || 0.32449 || 1 4 12 17 18 21 26 |
| 6 || 0.36828 || 1 4 8 12 15 16 17 21 |
| 7 || 0.33535 || 1 4 8 12 17 18 21 24 |
| 8 || 0.33596 || 4 13 17 21 |
| 9 || 0.33432 || 4 13 17 |
| **10** || **0.40103** || **1 4 12 17** |
| 11 || 0.30418 || 1 12 18 |
| 12 || 0.28135 || 1 8 18 |
| 13 || 0.3508 || 4 12 17 |
| 14 || 0.31567 || 1 4 12 17 25 |
| 15 || 0.33251 || 1 3 4 12 17 22 24 |
| 16 || 0.3482 || 4 12 17 22 |
| 17 || 0.37476 || 1 4 6 8 17 21 22 |
| 18 || 0.31707 || 1 4 12 18 |
| 19 || 0.32146 || 4 8 12 14 17 |
| 20 || 0.34047 || 4 8 12 17 |

According to the best fitness value (the highest), the selected attributes in the feature selection with Chaotic Harmony Search with mutation algorithm were: 1, 4, 12, 17:

*   Lights
*   T2
*   T6
*   RH\_8

### Chaotic Cuckoo Search

#### Algorithm parameters

 
| Initial population size: || 20 |
| --- | --- |
| Number of iterations: || 20 |
| Mutation: || bit-off |
| Mutation probability: || 0.01 |
| Chaotic method for Pa: || logistic map |
| Logistic map coefficient: || 4.0 |
| Initial discovery rate Pa: || 0.25 |
| Sigma Rate: || 0.70 |

#### Chaotic Cuckoo Search results

The fitness values of the harmonies in the best generation (20th) of the chaotic Cuckoo Search algorithm with mutation are illustrated in the next table.

According to the best fitness value (the highest), the selected attributes in the feature selection with Chaotic Cuckoo Search with mutation algorithm were: 1,16,22:

*   Lights
*   T8
*   RH\_out

 

Table 8.5. Chaotic Cuckoo search with mutation algorithm results of the 20th iteration which had the optimal results.

  
| Harmony || Fitness value || Subset |
| --- | --- | --- |
| **1** || 0.3874 || 1 10 16 22 |
| --- | --- | --- |
| 2 || 0.41886 || 1 16 22 |
| **3** || 0.41886 || 1 16 22 |
| 4 || 0.41886 || 1 16 22 |
| 5 || 0.41886 || 1 16 22 |
| 6 || 0.41886 || 1 16 22 |
| 7 || 0.41886 || 1 16 22 |
| 8 || 0.41886 || 1 16 22 |
| 9 || 0.36199 || 1 16 18 22 |
| 10 || 0.41886 || 1 16 22 |
| 11 || 0.3649 || 1 14 16 22 |
| 12 || 0.38557 || 1 6 16 22 |
| 13 || 0.3874 || 1 10 16 22 |
| 14 || 0.41886 || 1 16 22 |
| 15 || 0.41886 || 1 16 22 |
| 16 || 0.41886 || 1 16 22 |
| 17 || 0.38557 || 1 6 16 22 |
| 18 || 0.41886 || 1 16 22 |
| 19 || 0.39074 || 1 5 16 22 |
| 20 || 0.41886 || 1 16 |

### Evolutionary algorithm

#### EA parameters

 
| Population size: || 20 |
| --- | --- |
| Number of generations: || 20 |
| Mutation: || bit-flip |
| Mutation probability: || 0.10 |
| Crossover: || Simplex crossover ([Tsutsui et al., 1999](#ch8.xhtml#ref8_23)) |
| Crossover probability: || 0.60 |
| Selection operator: || tournament selection |

#### EA results

The fitness values of the chromosomes in the 18th generation of the evolutionary algorithm with mutation algorithm are illustrated in the next table.

Table 8.6. Evolutionary algorithm results of the 18th generation.

  
| Chromosome || Fitness value || Subset |
| --- | --- | --- |
| **1** || 0.3860 || 1 2 4 5 10 12 16 17 19 22 |
| --- | --- | --- |
| 2 || 0.3771 || 1 2 4 10 12 16 17 19 22 26 |
| 3 || 0.3127 || 1 2 3 4 10 11 12 13 14 16 17 21 22 25 26 27 |
| 4 || 0.3327 || 1 2 4 5 6 10 12 14 16 17 18 19 22 23 24 26 |
| 5 || 0.3513 || 1 2 4 5 10 12 16 17 19 23 26 |
| 6 || 0.3414 || 1 4 10 11 12 13 15 16 17 19 26 |
| 7 || 0.3501 || 1 2 4 12 13 16 17 21 22 25 26 |
| 8 || 0.3425 || 1 2 3 4 11 12 13 16 17 20 21 22 24 26 |
| 9 || 0.3442 || 1 2 6 10 11 12 13 16 17 19 22 23 26 |
| 10 || 0.3562 || 1 4 5 12 16 17 18 21 22 26 |
| **11** || **0.3929** || **1 2 4 5 12 16 17 19 22** |
| 12 || 0.3663 || 1 2 4 5 12 16 17 19 21 26 |
| 13 || 0.3249 || 1 2 4 5 6 7 11 12 13 17 20 22 25 |
| 14 || 0.3470 || 2 4 5 12 13 16 17 21 22 26 |
| 15 || 0.3684 || 1 2 4 10 12 16 17 19 20 22 26 |
| 16 || 0.3191 || 1 6 12 16 17 19 22 23 25 26 |
| 17 || 0.3367 || 1 2 4 5 10 11 12 14 16 19 21 22 25 |
| 18 || 0.3616 || 1 2 4 12 13 15 16 17 21 22 26 |
| 19 || 0.3434 || 1 2 4 5 10 12 13 16 17 18 22 24 26 |
| 20 || 0.3156 || 1 2 9 10 12 13 16 17 18 19 21 25 |

According to the best fitness value, the evolutionary algorithm selected the features: 1, 2, 4, 5, 12, 16, 17, 19, 22:

*   Lights
*   T1
*   T2
*   RH\_2
*   T6
*   T8
*   RH\_8
*   RH\_9
*   RH\_out

## Predictions with reduced features, SVM and random forest

The Random Forest ([Breiman, 1996](#ch8.xhtml#ref8_5), [1999](#ch8.xhtml#ref8_6), [2001](#ch8.xhtml#ref8_7)) and the Support Vector Machines were used to predict the output, the energy appliances measured by IoT devices by using the input vector of 27 features and compare the predictability with the models produced by using the reduced features as inputs according to the swarm intelligence and evolutionary models. The 10-fold cross validation as a validation technique in order to discover the best model. The RMSE was used as error metric.

The Support Vector Machines were proposed by [Vapnik (1995](#ch8.xhtml#ref8_24)). Support Vector Machines for Regression or Support Vector Regression (SVR) use an *ε*\-insensitive loss function for solving the regression problems. The generic estimating SVM function in regression is expressed by the following equation:

(8.16)  
$$Merit\_{s} = \\frac{k{\\overline{r}}\_{cf}}{\\sqrt{k + k\\left( {k - 1} \\right){\\overline{r}}\_{ff}}}$$  

where *w* ⊂ *R^n*, *b* ⊂ *R* and the Φ represents a non-linear transformation from *R^n* to high dimensional space. There are several types of kernel functions in Support Vector Machines, such as, linear, Gaussian, polynomial and RBF kernel.

The Lib-SVM library ([Chang and Lin, 2001](#ch8.xhtml#ref8_10), 2011) was utilized which implements the SMO (Sequential Minimal Optimization) algorithm for the support vector machines (SVMs). The epsilon-Support Vector Regression was implemented and the hyperparameters were: RBF kernel, cost C = 100, gamma γ = 0.01, and epsilon e = 0.001. In the random forest method, the number of trees were 100 and the maximum depth 0.

The comparison table of the comparative results shows that the best swarm intelligence-based method used for feature selection was the evolutionary algorithm with nine input features which has achieved forecasting results very close to the ones with all 27 input features.

 

Table 8.7. Model results.

  
| Model || Features || Random Forest RMSE error using 10-Fold Cross-Validation || Lib-SVM C = 100, γ = 0.01, e = 0.001, RBF kernel RMSE error using 10-Fold Cross-Validation |
| --- | --- | --- | --- |
| Genetic algorithm || (1, 4, 16, 17) || 14.59 || 19.16 |
| --- | --- | --- | --- |
| Geometric PSO || (1, 2, 16, 17, 22) || 13.63 || 19.20 |
| Chaotic Harmony Search || (1, 4, 12, 17) || 14.89 || 19.18 |
| Chaotic Cuckoo Search || (1, 16, 22) || 19.04 || 19.34 |
| Evolutionary Algorithm || (1, 2, 4, 5, 12, 16, 17, 19, 22) || 12.04 || 18.84 |
| Lib-SVM || All features || \- || 17.58 |
| Random Forest || All features || 11.47 || \- |

## Crime forecasting with PSO-SVM

The forecasting models were developed by using Support Vector Machines optimized by PSO. The crime dataset acquired by the official site of the City of Chicago: (data.cityofchicago.org). The Crime Rate represents the number of crimes committed in a day per 200.000 residents. The unemployment data for the city acquired by the official site of the United States Department, Bureau of Labor Statistics ([www.bls.gov](http://www.bls.gov)).

The 10-fold cross validation was used prevent the models from overfitting and every fold has the same sequence of the data instances of the original dataset since it is a time series problem. Daily crime data was utilized for the city of Chicago from 2012 till 2015. Also, unemployment data was taken as an input factor since unemployment affects the crime rates.

The input vector *X[t]* of the forecasting model in time *t* includes: the unemployment rate *UN*[*t*–1], and the Crime Rate *CR*[*t*–1], of the previous day. The time step is the day.

(8.17)  
*X*[*t*] = (*C**R*[*t* − 1],*U**N*[*t* − 1])  

The target vector *T[t]* of the machine learning model in time t is the one step ahead value of the input vector parameters:

(8.18)  
*T*[*t*] = *C**R*[*t*]  

The PSO was used as a hyperparameter optimization method. The Root Mean Square Error (RMSE) was used in order to evaluate the prediction error and to measure the performance of the PSO optimized machine learning model.

The most common PSO hyperparameters were utilized: population size: *P* = 50, inertia weight *w* = 0.99, personal learning coefficient *c*[1] = 2.0, global learning coefficient *c*[2] = 2.0 and the fully connected topology. The PSO algorithm was utilized to investigate the search space in order to find the best hyperparameter values. The RBF SVM kernel was used since, generally, it is considered to produce the optimal results. The hyperparameters that were tuned were: the cost C, the gamma (γ) parameter, the epsilon parameter and the choice if the input vector was standardized or not. Hyperparameters search ranges are presented in the next table.

The optimal SVM hyperparameter architecture found by the PSO algorithm within 30 iterations was: Cost C = 1.1426, gamma γ = 3.5907, epsilon ε = 0.023833, standardize data: false. The RMSE was 5.4882.

Table 8.8. Hyperparameters search range by applying PSO.

  
| Hyperparameter || Lower bound || Upper bound |
| --- | --- | --- |
| Cost C || 0.001 || 1000 |
| --- | --- | --- |
| gamma γ || 0.001 || 1000 |
| epsilon ε || 0.010 || 100 |
| standardize || true || false |

![Figure 8.2. Convergence curve of the PSO optimization of the SVM hyperparameters.](images/fig8_2_B.jpg)

Figure 8.2. Convergence curve of the PSO optimization of the SVM hyperparameters.

![Figure 8.3. Comparison plot of the true and the predicted value of the crime rate (number of crimes per 200.000 residents).](images/fig8_3_B.jpg)

Figure 8.3. Comparison plot of the true and the predicted value of the crime rate (number of crimes per 200.000 residents).

 

## References

*   [Anand, A. and Suganthi, L.](#ch8.xhtml#R_ref8_1) (2020). Forecasting of electricity demand by hybrid ANNPSO models. pp. 865-882 In: Deep Learning and Neural Networks: Concepts, Methodologies, Tools, and Applications. IGI Global.
*   [Azadeh, A., Babazadeh, R. and Asadzadeh, S. M.](#ch8.xhtml#R_ref8_2) (2013). Optimum estimation and forecasting of renewable energy consumption by artificial neural networks. Renewable and Sustainable Energy Reviews, 27: 605-612.
*   [Basheer, I. A. and Hajmeer, M.](#ch8.xhtml#R_ref8_3) (2000). Artificial neural networks: fundamentals, computing, design, and application. Journal of Microbiological Methods, 43(1): 3-31.
*   [Benardos, P. G. and Vosniakos, G. C.](#ch8.xhtml#R_ref8_4) (2007). Optimizing feedforward artificial neural network architecture. Engineering Applications of Artificial Intelligence, 20(3): 365-382.
*   [Breiman, L.](#ch8.xhtml#R_ref8_5) (1996). Bagging predictors. Machine learning, 24(2): 123-140.
*   [Breiman, L.](#ch8.xhtml#R_ref8_6) (1999). Random Forests-Random Features (# 567). Technical report, Dept. of Statistics, Univ. of California, Berkeley.
*   [Breiman, L](#ch8.xhtml#R_ref8_7). (2001). Random forests. Machine learning, 45(1): 5-32.
*   [Candanedo, L. M., Feldheim, V. and Deramaix, D.](#ch8.xhtml#R_ref8_8) (2017). Data driven prediction models of energy use of appliances in a low-energy house. Energy and Buildings, 140: 81-97.
*   [Castro, J. L., Mantas, C. J. and Benıtez, J. M.](#ch8.xhtml#R_ref8_9) (2000). Neural networks with a continuous squashing function in the output are universal approximators. Neural Networks, 13(6): 561-563.
*   [Chang, C. C. and Lin, C. J.](#ch8.xhtml#R_ref8_10) (2001). Training v-support vector classifiers: theory and algorithms. Neural computation, 13(9): 2119-2147.
*   Chang, C.-C. and Lin, C.-J. (2011). LIBSVM: A library for support vector machines. ACM Trans. Intell. Syst. Technol., 2(3): Article 27. doi: [https://doi.org/10.1145/1961189.1961199.](https://doi.org/10.1145/1961189.1961199.)
*   [Ekonomou, L.](#ch8.xhtml#R_ref8_12) (2010). Greek long-term energy consumption prediction using artificial neural networks. Energy, 35(2): 512-517.
*   [Honik, K.](#ch8.xhtml#R_ref8_13) (1991). Approximation capabilities of multilayer feedforward network. Neural Networks, 4(2): 251-257.
*   [Ilonen, J., Kamarainen, J. K. and Lampinen, J.](#ch8.xhtml#R_ref8_14) (2003). Differential evolution training algorithm for feed-forward neural networks. Neural Processing Letters, 17(1): 93-105.
*   [Koopialipoor, M. Armaghani, D. J. Hedayat, A. Marto, A. Gordan, B.](#ch8.xhtml#R_ref8_15) (2019). Applying various hybrid intelligent systems to evaluate and predict slope stability under static and dynamic conditions. Soft Computing, 23: 5913-5929.
*   [Kouziokas, G. N.](#ch8.xhtml#R_ref8_16) (2019). Long Short-Term Memory (LSTM) deep neural networks in energy appliances prediction. pp. 1-5. In: 2019 Panhellenic Conference on Electronics & Telecommunications (PACET). IEEE. doi: [https://doi.org/10.1109/PACET48583.2019.8956252.](https://doi.org/10.1109/PACET48583.2019.8956252.)
*   [Mirjalili, S., Hashim, S. Z. M. and Sardroudi, H. M.](#ch8.xhtml#R_ref8_17) (2012). Training feedforward neural networks using hybrid particle swarm optimization and gravitational search algorithm. Applied Mathematics and Computation, 218(22): 11125-11137.
*   [Moayedi, H., Moatamediyan, A., Nguyen, H., Bui, X.-N., Bui, D. T. and Rashid, A. S. A.](#ch8.xhtml#R_ref8_18) (2019). Prediction of ultimate bearing capacity through various novel evolutionary and neural network models. Engineering with Computers, 1-17.
*   [Moldovan, D. and Slowik, A.](#ch8.xhtml#R_ref8_19) (2021). Energy consumption prediction of appliances using machine learning and multi-objective binary grey wolf optimization for feature selection. Applied Soft Computing, 111: 107745.
*   [Nourbakhsh, A., Safikhani, H. and Derakhshan, S.](#ch8.xhtml#R_ref8_20) (2011). The comparison of multiobjective particle swarm optimization and NSGA II algorithm: applications in centrifugal pumps. EnOp, 43: 1095-1113.
*   [Panchal, G., Ganatra, A., Kosta, Y. P. and Panchal, D.](#ch8.xhtml#R_ref8_21) (2011). Behaviour analysis of multilayer perceptrons with multiple hidden neurons and hidden layers. International Journal of Computer Theory and Engineering, 3(2): 332-337.
*   [Socha, K. and Blum, C.](#ch8.xhtml#R_ref8_22) (2007). An ant colony optimization algorithm for continuous optimization: application to feed-forward neural network training. Neural Computing and Applications, 16(3): 235-247.
*   [Tsutsui, S., Yamamura, M. and Higuchi, T.](#ch8.xhtml#R_ref8_23) (1999). Multi-parent recombination with simplex crossover in real coded genetic algorithms. pp. 657-664. In Proceedings of the 1st Annual Conference on Genetic and Evolutionary Computation-Volume 1.
*   [Vapnik, V. N.](#ch8.xhtml#R_ref8_24) (1995). The nature of statistical learning. Theory. Springer-Verlag New York.
*   [Wang, H., Cui, Z., Chen, Y., Avidan, M., Abdallah, A. B. and Kronzer, A.](#ch8.xhtml#R_ref8_25) (2018). Predicting hospital readmission via cost-sensitive deep learning. IEEE/ACM Transactions on Computational Biology and Bioinformatics, 15(6): 1968-1978.
*   [Yam, J. Y. and Chow, T. W.](#ch8.xhtml#R_ref8_26) (2001). Feedforward networks training speed enhancement by optimal initialization of the synaptic coefficients. IEEE Transactions on Neural Networks, 12(2): 430-434.
*   [Zhang, C. and Shao, H.](#ch8.xhtml#R_ref8_27) (2000). An ANN’s evolved by a new evolutionary system and its application. Proceedings of the 39th IEEE Conference on Decision and Control (Cat. No. 00CH37187), 4: 3562-3563.

# Chapter 9 Swarm and Evolutionary Intelligence in Deep Learning

This chapter is devoted to deep learning optimization applications. A theoretical background discussion of deep unidirectional, bi-directional long short-term memory (LSTM and Bi-LSTM) and Convolutional Neural Networks (CNN) is presented and also topology and weight swarm and evolutionary optimization methods applied on those deep learning methods. The experimental part of this chapter is involved with swarm intelligence and evolutionary computation examples implemented on deep learning models including an illustrative example of covid19 diagnosis from chest x-ray images.

## Deep LSTM and Bi-LSTM networks

In the recent past deep unidirectional Long Short-Term Memory (LSTM) networks and Bi-directional LSTM (Bi-LSTM) have been applied in several scientific problems as forecasting networks. The LSTM and Bi-LSTM networks have a topology similar to the Recurrent Neural Networks (RNNs) but the main advantage of LSTM and Bi-LSTM networks over the typical RNNs is that they overcome the vanishing gradients problem which is a very important drawback of the normal RNNs ([Cortez et al., 2018](#ch9.xhtml#ref9_6)). Several researchers have investigated the application of LSTM and Bi-LSTM models in many scientific fields ([Behera et al., 2021](#ch9.xhtml#ref9_2); [Chadha et al., 2020](#ch9.xhtml#ref9_3); Kouziokas, 2019).

The LSTM network consists of four major kinds of gates: input gate, forget gate, cell candidate and output gate. The equations which represent the estimation of every component at time step t are as follows.

The equation for the input gate is expressed by the mathematical formula:

(9.1)  
*i*[t] = *σ*[g](W[i]x[t]+R[i]h[t]\_1+b[i])  

The equation for the forget gate is expressed by the mathematical formula:

(9.2)  
f[t] = *σ*[g](W[f]x[t]+R[f]h[t]\_1+b[f])  

The equation for the cell candidate is expressed by the mathematical formula:

(9.3)  
g[t] = *σ*[c](W[g]x[t]+R[g]h[t]\_1+b[g])  

The equation for the output gate is expressed by the mathematical formula:

(9.4)  
o[t] = *σ*[g](W[o]x[t]+R[o]h[t]\_1+b[o])  

where,

*   *i*, *f*, *g*, *o* represent the input gate, the forget gate, the cell candidate, and the output gate, correspondingly,
*   *W* represents the input weights
*   *R* represents the recurrent weights
*   b represents the bias
*   *h[t]* the hidden state at time step *t*
*   σ[c] the state activation function.

The cell state in time *t* is expressed by the mathematical formula:

(9.5)  
c[t] = f[t] ⊙ c[t-1] + i[t] ⊙ g[t]  

where: ⊙ represents the Hadamard product.

The hidden state in a given time *t* can be expressed by the mathematical formula:

(9.6)  
c[t] = f[t] ⊙ c[t-1] + i[t] ⊙ g[t]  

In the bidirectional LSTM (Bi-LSTM) topology, the network has two directions: forwards and backwards, and it’s capable of using data from both sides unlike standard unidirectional LSTM ([Schuster and Paliwal, 1997](#ch9.xhtml#ref9_15)). This helps Bi-LSTM networks to achieve improved forecasting results according to the literature ([Shahid et al., 2020](#ch9.xhtml#ref9_16); [Zhang et al., 2020](#ch9.xhtml#ref9_19)).

## Deep CNN (Convolutional Neural Networks)

CNN is a frequently-used deep learning method in the literature in tasks which have to do with images. Convolutional neural networks are mostly used in image classification and computer vision. Before CNNs, difficult feature extraction methods were utilized to classify objects and images. Convolutional neural networks have improved performance when the inputs are: images or audio signals compared to the other types of neural networks. CNNs have several types of layers, such as: convolutional layers, pooling layers, activation layers, dropout layers, fully-connected layers with several hyperparameters such as number and size of filters, types of pooling (Max pooling or average pooling). The convolutional and pooling layers usually utilize ReLu activation functions, fully-connected layers usually implement a SoftMax activation function in order to classify the inputs ([LeCun et al., 2010](#ch9.xhtml#ref9_12)). An example of the convolutional layer operation is illustrated in [Figure 9.1](#ch9.xhtml#fig9_1).

![Figure 9.1. Example of convolution function.](images/fig9_1_B.jpg)

[Figure 9.1. Example of convolution function.](#ch9.xhtml#R_fig9_1)

The role of the pooling layer is to reduce the complexity of the CNN by down sampling feature maps. The maximum and average poolings are most utilized. A simple example of average pooling is illustrated in [Figure 9.2](#ch9.xhtml#fig9_2).

![Figure 9.2. Example of convolution function.](images/fig9_2_B.jpg)

[Figure 9.2. Example of convolution function.](#ch9.xhtml#R_fig9_2)

A pooled feature map is then flattened into a column as shown in [Figure 9.3](#ch9.xhtml#fig9_3) in order to be used as a single input vector for the artificial neural network. The role of the neural network in the fully connected layer is to process the input features and predict the result in the output, so that the convolutional network can finally classify the input images.

![Figure 9.3. Example of a simple flattening operation.](images/fig9_3_B.jpg)

[Figure 9.3. Example of a simple flattening operation.](#ch9.xhtml#R_fig9_3)

There are several pre-trained models for several kinds of problems that can be used in transfer learning, such as ResNet18 (18 layers), ResNet50 (50 layers), AlexNet, GoogleNet and Darknet19 ([LeCun et al., 2015](#ch9.xhtml#ref9_13)).

## CNN and LSTM optimization

### Topology optimization

Swarm intelligence and evolutionary strategies can be also implemented to optimize the topology of deep learning models regarding the number of hidden neurons in the hidden layer, the number of filters in the convolutional layers, the pooling type and others.

The objective function should be set for the swarm intelligence or evolutionary method in order to optimize the deep learning model. The most commonly used objective function according to the literature is an error metric. For regression problems the mean squared error or the mean absolute error can be utilized and for classification problems error metrics such as accuracy, sensitivity and F-score are used.

According to the literature, swarm intelligence methods have a better performance in deep learning optimization than other optimization algorithms ([Kim and Cho, 2019](#ch9.xhtml#ref9_8); [Ren et al., 2021](#ch9.xhtml#ref9_14); [Wang et al., 2020](#ch9.xhtml#ref9_18)). The deep learning methods can be also optimized in other ways, such as optimizing the training option parameters: Maximum epochs, initial learning rate, optimization algorithm, *l*[2] regularization value, minibatch size, momentum and others.

### Weight optimization

The weight optimization of deep learning methods can be also implemented by using swarm and evolutionary optimization methods ([Ilonen et al., 2003](#ch9.xhtml#ref9_7); [Socha and Blum, 2007](#ch9.xhtml#ref9_17)). Similarly with topology optimization, a suitable fitness function for the swarm intelligence of the evolutionary method should be set in order to train the deep learning model such as: the mean squared error (MSE) or root mean squared error (RMSE) or mean absolute error (MAE) in regression problems and accuracy, precision, recall, F-score in classification problems.

In the deep learning model weight optimization, the computational complexity is increased. Generally, in fine tuning using transfer learning models such as ResNet18, DarkNet19 the optimization method is applied on the last trainable layer ([Koppu et al., 2020](#ch9.xhtml#ref9_9)). Each particle position represents a solution to the optimization problem of the objective function and the deep learning weight vector is optimized by the swarm particles in order to get the best solution for the fitness function.

## Experiments

### Bi-LSTM optimization

#### Dataset

The Japanese Vowels Data Set was utilized for the experiments. The dataset was acquired by the machine learning repository[²](#fn2)

### Objective function

The percentage error was utilized as the objective function. The accuracy measures the number of correct predictions divided by the total number of the predictions. The percentage error is expressed by the equation:

#### Correctly predictedintances

(9.7)  
$$\\text{Percentatge~error=1-Accuracy=1-}\\frac{Correctly\\, predicted\\, intances}{\\text{Total}\\,\\text{number}\\,\\text{of}\\, intances}$$  

Total number *of intances*

### Experimental setup

Two methods were utilized as optimization techniques in order to optimize the deep Bidirectional LSTM: adaptive inertia weight particle swarm optimization (Adaptive w-PSO) and genetic algorithm (GA).

#### Genetic algorithm parameters

| **Parameter** || **Value** |
| --- | --- |
| Population size: ||  50 |
| Number of generations: ||  48 |
| Selection: || roulette wheel |
| Crossover type: || single point |
| Mutation: || gaussian |
| Probability of crossover: ||  0.6 |
| Probability of mutation: ||  0.033 |

#### Adaptive w-PSO parameters

| Parameter || Value |
| --- | --- |
| Population size: ||  50 |
| Swarm topology: || Fully connected |
| Swarm particle initialization || random uniform distribution |
| Number of iterations: ||  48 |
| Adaptive inertia weight range: || \[0.2, 1.1\] |
| Initial inertia weight || max(Inertia Range) = 1.1 |
| Coefficient parameter of personal learning: || *c*[1] = 2.0 |
| Coefficient parameter of global learning: || *c*[2] = 2.0 |

#### Bidirectional LSTM training parameters

| **Parameter** || **Value** |
| --- | --- |
| Minibatch size: ||  32 |
| epochs: ||  30 |
| momentum: ||  0.9 |
| optimizer || adam |
| Gradient Threshold ||  1 |
| layers || sequence input layer |
|  || bilstm layer |
|  || fully connected layer |
|  || softmax layer |
|  || classification layer |
| input feature size ||  12 |
| number of classes ||  9 |

The hyperparameters which were selected to be optimized are: hidden layer neurons, initial learning Rate, L2 regularization value. In the next table the hyperparameter lower and upper bounds in the search space are illustrated.

Table 9.1. Hyperparameter lower and upper bounds in a continuous search space.

 
| Hyperparameter || Lower bound || Upper bound |
| --- | --- | --- |
| Hidden layer neurons ||  100 ||  250 |
| --- | --- | --- |
| Initial Learning Rate ||  0.01 ||  0.09 |
| L2 Regularization ||  0.0001 ||  0.0009 |

The results of the hyperparameter values and percentage error during adaptive w-PSO-Bi-LSTM optimization are presented in the next table.

Table 9.2. Hyperparameter values and percentage error during adaptive w-PSO-BiLSTM optimization.

 
| Iteration || Hidden Layer Size || Initial Learning Rate || L2 Regularization || Percentage Errors || Accuracy || Best Pe Error So Far || Best Accuracy So Far |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  1 ||  189 ||  0.0823 ||  0.00064155 ||  0.0811 ||  0.9189 ||  0.0811 ||  0.9189 |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  2 ||  225 ||  0.0458 ||  0.00079433 ||  0.1027 ||  0.8973 ||  0.0811 ||  0.9189 |
|  3 ||  106 ||  0.0178 ||  0.00073525 ||  0.0405 ||  0.9595 ||  0.0405 ||  0.9595 |
|  4 ||  175 ||  0.0882 ||  0.00029546 ||  0.1432 ||  0.8568 ||  0.0405 ||  0.9595 |
|  5 ||  202 ||  0.0796 ||  0.00060226 ||  0.0649 ||  0.9351 ||  0.0405 ||  0.9595 |
|  6 ||  138 ||  0.049 ||  0.00012304 ||  0.0757 ||  0.9243 ||  0.0405 ||  0.9595 |
|  7 ||  221 ||  0.036 ||  0.00048475 ||  0.0784 ||  0.9216 ||  0.0405 ||  0.9595 |
|  8 ||  153 ||  0.0862 ||  0.00049437 ||  0.1216 ||  0.8784 ||  0.0405 ||  0.9595 |
|  9 ||  128 ||  0.0477 ||  0.00029818 ||  0.0595 ||  0.9405 ||  0.0405 ||  0.9595 |
|  10 ||  233 ||  0.0876 ||  0.00020224 ||  0.2162 ||  0.7838 ||  0.0405 ||  0.9595 |
|  11 ||  198 ||  0.0694 ||  0.00088528 ||  0.0919 ||  0.9081 ||  0.0405 ||  0.9595 |
|  12 ||  219 ||  0.0201 ||  0.00048803 ||  0.0405 ||  0.9595 ||  0.0405 ||  0.9595 |
|  13 ||  112 ||  0.0189 ||  0.00019942 ||  0.0351 ||  0.9649 ||  0.0351 ||  0.9649 |
|  14 ||  203 ||  0.0632 ||  0.00043017 ||  0.1432 ||  0.8568 ||  0.0351 ||  0.9649 |
|  15 ||  122 ||  0.0156 ||  0.00089184 ||  0.1135 ||  0.8865 ||  0.0351 ||  0.9649 |
|  16 ||  183 ||  0.0508 ||  0.00087723 ||  0.0892 ||  0.9108 ||  0.0351 ||  0.9649 |
|  17 ||  145 ||  0.0342 ||  0.00080962 ||  0.0514 ||  0.9486 ||  0.0351 ||  0.9649 |
|  18 ||  185 ||  0.0761 ||  0.00016918 ||  0.1703 ||  0.8297 ||  0.0351 ||  0.9649 |
|  19 ||  124 ||  0.0895 ||  0.00026703 ||  0.0649 ||  0.9351 ||  0.0351 ||  0.9649 |
|  20 ||  104 ||  0.0605 ||  0.00084476 ||  0.0946 ||  0.9054 ||  0.0351 ||  0.9649 |
|  21 ||  125 ||  0.0169 ||  0.00074574 ||  0.0595 ||  0.9405 ||  0.0351 ||  0.9649 |
|  22 ||  170 ||  0.0239 ||  0.00037608 ||  0.0676 ||  0.9324 ||  0.0351 ||  0.9649 |
|  23 ||  120 ||  0.0386 ||  0.00027356 ||  0.0514 ||  0.9486 ||  0.0351 ||  0.9649 |
|  24 ||  236 ||  0.0653 ||  0.00081053 ||  0.0865 ||  0.9135 ||  0.0351 ||  0.9649 |
|  25 ||  207 ||  0.0531 ||  0.00060504 ||  0.1459 ||  0.8541 ||  0.0351 ||  0.9649 |
|  26 ||  223 ||  0.0701 ||  0.00030383 ||  0.0973 ||  0.9027 ||  0.0351 ||  0.9649 |
|  27 ||  217 ||  0.0284 ||  0.00062058 ||  0.0568 ||  0.9432 ||  0.0351 ||  0.9649 |
|  28 ||  119 ||  0.0662 ||  0.00020829 ||  0.0622 ||  0.9378 ||  0.0351 ||  0.9649 |
|  29 ||  122 ||  0.0818 ||  0.00017933 ||  0.0405 ||  0.9595 ||  0.0351 ||  0.9649 |
|  30 ||  134 ||  0.0411 ||  0.00080546 ||  0.0541 ||  0.9459 ||  0.0351 ||  0.9649 |
|  31 ||  191 ||  0.0151 ||  0.00051611 ||  0.0351 ||  0.9649 ||  0.0351 ||  0.9649 |
|  32 ||  150 ||  0.0339 ||  0.00039142 ||  0.0784 ||  0.9216 ||  0.0351 ||  0.9649 |
|  33 ||  135 ||  0.0537 ||  0.00024335 ||  0.0973 ||  0.9027 ||  0.0351 ||  0.9649 |
|  34 ||  113 ||  0.0423 ||  0.00013362 ||  0.0649 ||  0.9351 ||  0.0351 ||  0.9649 |
|  35 ||  226 ||  0.0725 ||  0.00016819 ||  0.2568 ||  0.7432 ||  0.0351 ||  0.9649 |
|  36 ||  219 ||  0.0634 ||  0.00031599 ||  0.1486 ||  0.8514 ||  0.0351 ||  0.9649 |
|  37 ||  113 ||  0.0113 ||  0.00014789 ||  0.0405 ||  0.9595 ||  0.0351 ||  0.9649 |
| 38 ||  153 ||  0.0602 ||  0.00079502 ||  0.0595 ||  0.9405 ||  0.0351 ||  0.9649 |
|  39 ||  202 ||  0.0147 ||  0.00042565 ||  0.0378 ||  0.9622 ||  0.0351 ||  0.9649 |
|  40 ||  243 ||  0.0524 ||  0.00052815 ||  0.0351 ||  0.9649 ||  0.0351 ||  0.9649 |
|  41 ||  104 ||  0.0678 ||  0.00085988 ||  0.0703 ||  0.9297 ||  0.0351 ||  0.9649 |
|  42 ||  193 ||  0.0466 ||  0.00066194 ||  0.1784 ||  0.8216 ||  0.0351 ||  0.9649 |
|  43 ||  215 ||  0.034 ||  0.00019361 ||  0.0757 ||  0.9243 ||  0.0351 ||  0.9649 |
|  44 ||  170 ||  0.03 ||  0.00024958 ||  0.0919 ||  0.9081 ||  0.0351 ||  0.9649 |
|  45 ||  146 ||  0.0199 ||  0.00070955 ||  0.0324 ||  0.9676 ||  0.0324 ||  0.9676 |
|  46 ||  210 ||  0.0348 ||  0.00088012 ||  0.0297 ||  0.9703 ||  0.0297 ||  0.9703 |
|  47 ||  180 ||  0.0209 ||  0.00070588 ||  0.0703 ||  0.9297 ||  0.0297 ||  0.9703 |
|  48 ||  123 ||  0.0627 ||  0.0002885 ||  0.0676 ||  0.9324 ||  0.0297 ||  0.9703 |

![Figure 9.4. Best so far classification error plot during the iterations by using PSO to optimize Bi-LSTM hyperparameters.](images/fig9_4_C.jpg)

Figure 9.4. Best so far classification error plot during the iterations by using PSO to optimize Bi-LSTM hyperparameters.

The results of the hyperparameter values and percentage error during adaptive w-GA-Bi-LSTM optimization are presented in the next table.

As we can observe from the results the PSO optimization of Bi-LSTM network is much faster than the GA-Bi-LSTM model. Within 3 iterations PSO achieves a percentage error of about 0.04 much smaller than the GA which achieves about 0.05 in the same iteration number, although, the results are similar in 48 iterations.

Table 9.3. . Hyperparameter values and classification error during GA-BiLSTM optimization.

 
| Iteration || Hidden Layer Size || Initial Learning Rate || L2 Regularization || Percent Errors || Accuracy || Best % error so far || Best Accuracy so far |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  1 ||  100 ||  0.01 ||  0.0009 ||  0.07027 ||  0.92973 ||  0.07027 ||  0.92973 |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  2 ||  212 ||  0.053998 ||  0.00084847 ||  0.062162 ||  0.93784 ||  0.062162 ||  0.937838 |
|  3 ||  187 ||  0.019514 ||  0.00055323 ||  0.048649 ||  0.95135 ||  0.048649 ||  0.951351 |
|  4 ||  190 ||  0.071739 ||  0.00087868 ||  0.062162 ||  0.93784 ||  0.048649 ||  0.951351 |
|  5 ||  249 ||  0.059428 ||  0.00030971 ||  0.33784 ||  0.66216 ||  0.048649 ||  0.951351 |
|  6 ||  214 ||  0.080309 ||  0.00013372 ||  0.072973 ||  0.92703 ||  0.048649 ||  0.951351 |
|  7 ||  129 ||  0.072257 ||  0.00056525 ||  0.078378 ||  0.92162 ||  0.048649 ||  0.951351 |
|  8 ||  142 ||  0.040555 ||  0.00053645 ||  0.059459 ||  0.94054 ||  0.048649 ||  0.951351 |
|  9 ||  140 ||  0.035934 ||  0.00075752 ||  0.054054 ||  0.94595 ||  0.048649 ||  0.951351 |
|  10 ||  237 ||  0.075581 ||  0.00077861 ||  0.13514 ||  0.86486 ||  0.048649 ||  0.951351 |
|  11 ||  210 ||  0.028916 ||  0.00057152 ||  0.064865 ||  0.93514 ||  0.048649 ||  0.951351 |
|  12 ||  221 ||  0.050018 ||  0.00010082 ||  0.051351 ||  0.94865 ||  0.048649 ||  0.951351 |
|  13 ||  144 ||  0.087712 ||  0.00070494 ||  0.13784 ||  0.86216 ||  0.048649 ||  0.951351 |
|  14 ||  122 ||  0.028447 ||  0.00075638 ||  0.054054 ||  0.94595 ||  0.048649 ||  0.951351 |
|  15 ||  230 ||  0.043063 ||  0.00080923 ||  0.091892 ||  0.90811 ||  0.048649 ||  0.951351 |
|  16 ||  225 ||  0.088903 ||  0.00060577 ||  0.045946 ||  0.95405 ||  0.045946 ||  0.954054 |
|  17 ||  161 ||  0.064449 ||  0.00063802 ||  0.032432 ||  0.96757 ||  0.032432 ||  0.967568 |
|  18 ||  225 ||  0.022482 ||  0.00076005 ||  0.043243 ||  0.95676 ||  0.032432 ||  0.967568 |
|  19 ||  122 ||  0.060157 ||  0.00011498 ||  0.051351 ||  0.94865 ||  0.032432 ||  0.967568 |
|  20 ||  220 ||  0.052159 ||  0.00087828 ||  0.11351 ||  0.88649 ||  0.032432 ||  0.967568 |
|  21 ||  247 ||  0.052241 ||  0.00072428 ||  0.07027 ||  0.92973 ||  0.032432 ||  0.967568 |
|  22 ||  106 ||  0.020415 ||  0.00038129 ||  0.027027 ||  0.97297 ||  0.027027 ||  0.972973 |
|  23 ||  146 ||  0.04792 ||  0.00027676 ||  0.086486 ||  0.91351 ||  0.027027 ||  0.972973 |
|  24 ||  216 ||  0.067964 ||  0.00057967 ||  0.1027 ||  0.8973 ||  0.027027 ||  0.972973 |
|  25 ||  247 ||  0.020178 ||  0.00033221 ||  0.1000 ||  0.9 ||  0.027027 ||  0.972973 |
|  26 ||  129 ||  0.01191 ||  0.00026627 ||  0.043243 ||  0.95676 ||  0.027027 ||  0.972973 |
|  27 ||  182 ||  0.044048 ||  0.0001073 ||  0.032432 ||  0.96757 ||  0.027027 ||  0.972973 |
|  28 ||  237 ||  0.067764 ||  0.00055862 ||  0.11892 ||  0.88108 ||  0.027027 ||  0.972973 |
|  29 ||  124 ||  0.039579 ||  0.00020074 ||  0.083784 ||  0.91622 ||  0.027027 ||  0.972973 |
|  30 ||  193 ||  0.061625 ||  0.00072365 ||  0.056757 ||  0.94324 ||  0.027027 ||  0.972973 |
|  31 ||  139 ||  0.054479 ||  0.00017531 ||  0.07027 ||  0.92973 ||  0.027027 ||  0.972973 |
|  32 ||  243 ||  0.02894 ||  0.00049466 ||  0.067568 ||  0.93243 ||  0.027027 ||  0.972973 |
|  33 ||  132 ||  0.03971 ||  0.00044401 ||  0.045946 ||  0.95405 ||  0.027027 ||  0.972973 |
|  34 ||  181 ||  0.027902 ||  0.00054813 ||  0.048649 ||  0.95135 ||  0.027027 ||  0.972973 |
|  35 ||  162 ||  0.081133 ||  0.00082185 ||  0.091892 ||  0.90811 ||  0.027027 ||  0.972973 |
|  36 ||  102 ||  0.07662 ||  0.00036034 ||  0.14865 ||  0.85135 ||  0.027027 ||  0.972973 |
|  37 ||  237 ||  0.054978 ||  0.00068724 ||  0.035135 ||  0.96486 ||  0.027027 ||  0.972973 |
| 38 ||  240 ||  0.043808 ||  0.00044434 ||  0.054054 ||  0.94595 ||  0.027027 ||  0.972973 |
|  39 ||  158 ||  0.080646 ||  0.00086454 ||  0.072973 ||  0.92703 ||  0.027027 ||  0.972973 |
|  40 ||  224 ||  0.076497 ||  0.00036992 ||  0.15405 ||  0.84595 ||  0.027027 ||  0.972973 |
|  41 ||  108 ||  0.037876 ||  0.00020802 ||  0.037838 ||  0.96216 ||  0.027027 ||  0.972973 |
|  42 ||  208 ||  0.051865 ||  0.00031076 ||  0.089189 ||  0.91081 ||  0.027027 ||  0.972973 |
|  43 ||  116 ||  0.059506 ||  0.00015485 ||  0.062162 ||  0.93784 ||  0.027027 ||  0.972973 |
|  44 ||  249 ||  0.061759 ||  0.00042695 ||  0.11622 ||  0.88378 ||  0.027027 ||  0.972973 |
|  45 ||  241 ||  0.075807 ||  0.0004411 ||  0.15676 ||  0.84324 ||  0.027027 ||  0.972973 |
|  46 ||  122 ||  0.079736 ||  0.00013518 ||  0.067568 ||  0.93243 ||  0.027027 ||  0.972973 |
|  47 ||  146 ||  0.086798 ||  0.00030496 ||  0.081081 ||  0.91892 ||  0.027027 ||  0.972973 |
|  48 ||  154 ||  0.03394 ||  0.00024518 ||  0.043243 ||  0.95676 ||  0.027027 ||  0.972973 |

![Figure 9.5. Best so far classification error plot during the iterations by using GA-BiLSTM model.](images/fig9_5_C.jpg)

Figure 9.5. Best so far classification error plot during the iterations by using GA-BiLSTM model.

## CNN optimization

### CNN – PSO model

In the experiments, the CNN model consists of a convolutional layer, ReLU activation function and a pooling layer, a second convolutional layer, and ReLU activation and a second pooling layer and a dropout layer. The fully connected layer consists of an input layer, a hidden layer, a ReLU activation function and an output layer with the softmax function as the activation function. The kernel size of pooling layers was 2 × 2. All the PSO parameters are randomly initialized. The initial learning rate was 0.001 with the Adam optimizer. The hyperparameters to be optimized by the adaptive PSO where: Number of filters in every convolutional layer (1–100), size of trainable filters in every convolutional layer (3–10), type of pooling in every pooling layer (average pooling and max-pooling), probability of dropout in every convolutional layer (0.1–0.9), batch size (16–128), maximum epochs (30–50), and number of hidden neurons in the hidden layer of the fully connected layer (50–400).

### Evaluation metrics

This section lists the evaluation metrics used to measure the classification performance of the experimental models.

#### Precision

The precision metric evaluates the prediction accuracy and it is expressed by the following equation:

(9.8)  
$$precision = \\frac{TP}{TP + FP}$$  

where,

*   TP represents the true positive cases
*   FP for the false positive cases.

#### Recall or sensitivity

The recall metric, also referred to as sensitivity, evaluates the results completeness of classification and it is calculated by the following equation:

(9.9)  
$${Re}call = \\frac{TP}{TP + FN}$$  

where,

*   TP represents the true positive cases
*   FN represents the false negative cases.

#### F-measure

The F-Measure metric evaluates the prediction performance of a classification algorithm, by combining precision and recall measures and is calculated by the following equation:

(9.10)  
$$Fmeasure = 2 \\ast \\frac{precision \\ast recall}{precision + recall}$$  

By combining the previous equations, the F-Measure can be expressed by the following equation:

(9.11)  
$$Fmeasure = 2 \\ast \\frac{TP}{2 \\ast TP + FP + FN}$$  

#### Matthews correlation coefficient (MCC)

The Matthews Correlation Coefficient is considered as a balanced classification measure and it is estimated by the following mathematical equation:

(9.12)  
$$MCC = \\frac{TP \\ast TN - FP \\ast FN}{\\left\\lbrack {\\left( {TP + FP} \\right) \\ast \\left( {FN + TN} \\right) \\ast \\left( {FP + TN} \\right) \\ast \\left( {TP + FN} \\right)} \\right\\rbrack^{\\frac{1}{2}}}$$  

where TN represents the true negative cases.

#### Receiver operating characteristic (ROC)

A receiver operating characteristic curve, is a graphical plot that illustrates the ability of a classifier. The ROC curve is designed by plotting the true positive rate against the false positive rate instances for various threshold configurations.

#### Precision-recall curve (PRC)

A precision-recall curve is a plot designed between the precision metric (y-axis) and the recall metric (x-axis) for various threshold configurations, similar to the ROC curve.

### Covid-19 chest X-ray dataset

The chest x-ray images of the ieee8023 dataset were utilized ([Cohen et al., 2020](#ch9.xhtml#ref9_5)). The chest x-ray images were preprocessed by using dynamic histogram equalization for image contrast enhancement ([Abdullah-Al-Wadud et al., 2007](#ch9.xhtml#ref9_1)). The dataset was split to training and test sets. The test set has 66 images from every class: normal, covid19 and other diseases.

![Figure 9.6. Some x-ray images of patients with covid-19 from the ieee8023 dataset (Cohen et al., 2020).](images/fig9_6_B.jpg)

Figure 9.6. Some x-ray images of patients with covid-19 from the ieee8023 dataset (Cohen et al., 2020).

### Experimental results

#### CNN without PSO

In the CNN model the overall correctly classified instances in the test set were 167 (84.34%) and the incorrectly classified instances were 31 (15.65%). The classification metrics for the CNN model without PSO optimization are presented in the[Table 9.4](#ch9.xhtml#tab9_4). The confusion matrix is illustrated in[Table 9.5](#ch9.xhtml#tab9_5).

[Table 9.4. Results for the CNN without PSO optimization.](#ch9.xhtml#R_tab9_4)

 
| Class || TP Rate || FP Rate || Precision || Recall || F-Measure || MCC || ROC Area || PRC Area |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| COVID-19 ||  0,788 ||  0,038 ||  0,912 ||  0,788 ||  0,846 ||  0,781 ||  0,922 ||  0,917 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Normal ||  0,909 ||  0,068 ||  0,870 ||  0,909 ||  0,889 ||  0,832 ||  0,954 ||  0,819 |
| Other diseases ||  0,833 ||  0,129 ||  0,764 ||  0,833 ||  0,797 ||  0,690 ||  0,922 ||  0,859 |
| Weighted Avg. ||  0,843 ||  0,078 ||  0,849 ||  0,843 ||  0,844 ||  0,768 ||  0,933 ||  0,865 |

 [Table 9.5. Confusion matrix for the CNN without PSO optimization.](#ch9.xhtml#R_tab9_5) 

 
|  ||  || PREDICTED |
| --- | --- | --- |
|  ||  || **COVID-19** || **Normal** || **Other diseases** |
| --- | --- | --- | --- | --- |
| ACTUAL || **COVID-19** ||  52 ||  3 ||  11 |
|  || **Normal** ||  0 ||  60 ||  6 |
|  || **Other diseases** ||  5 ||  6 ||  55 |

#### CNN optimized with PSO

Adaptive PSO parameters

The adaptive inertia weight PSO parameters for the experiments were the following:

| **Parameter** || **Value** |
| --- | --- |
| Population size: ||  50 |
| Swarm topology: || Fully connected |
| Swarm particle initialization || random uniform distribution |
| Number of iterations: ||  50 |
| Adaptive inertia weight range: || \[0.2, 1.1\] |
| Initial inertia weight || max(Inertia Range) = 1.1 |
| Coefficient parameter of personal learning: || *c*[1] = 2.0 |
| Coefficient parameter of global learning: || *c*[2] = 2.0 |

In the CNN model optimized with PSO, the overall correctly classified instances in the test set were 183 (92.42%) and the incorrectly classified instances were 15 (7.58%). The classification metrics for the CNN model without PSO optimization are presented in the[Table 9.6](#ch9.xhtml#tab9_6). The confusion matrix is illustrated in[Table 9.7](#ch9.xhtml#tab9_7).

[Table 9.6. Results for the CNN - PSO model.](#ch9.xhtml#R_tab9_6)

 
| Class || TP Rate || FP Rate || Precision || Recall || F-Measure || MCC || ROC Area || PRC Area |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| COVID-19 ||  0,879 ||  0,015 ||  0,967 ||  0,879 ||  0,921 ||  0,886 ||  0,932 ||  0,890 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Normal ||  0,970 ||  0,045 ||  0,914 ||  0,970 ||  0,941 ||  0,911 ||  0,962 ||  0,897 |
| Other diseases ||  0,924 ||  0,053 ||  0,897 ||  0,924 ||  0,910 ||  0,865 ||  0,936 ||  0,854 |
| Weighted Avg. ||  0,924 ||  0,038 ||  0,926 ||  0,924 ||  0,924 ||  0,887 ||  0,943 ||  0,880 |

 [Table 9.7. Confusion matrix for the CNN - PSO model.](#ch9.xhtml#R_tab9_7) 

 
|  ||  || PREDICTED |
| --- | --- | --- |
|  ||  || **COVID-19** || **Normal** || **Other diseases** |
| --- | --- | --- | --- | --- |
| ACTUAL || **COVID-19** ||  58 ||  3 ||  5 |
|  || **Normal** ||  0 ||  64 ||  2 |
|  || **Other diseases** ||  2 ||  3 ||  61 |

As we can observe the PSO optimized CNN network produced much better results than the CNN model without any optimization.

This is a simple experiment of the application of swarm intelligence on deep learning To achieve more accurate results other optimized deep learning models can be used. For example, transfer learning can be utilized to train the last layers of pre-trained models like ResNet18, ResNet50, AlexNet, GoogleNet and Darknet19 ([LeCun et al., 2015](#ch9.xhtml#ref9_13)) and swarm intelligence models can be used to optimize either the layer weights or the hyperparameters of the deep learning models such as: hidden layer neurons of the fully connected layer, the initial learning rate, the L2 regularization factor, the number and size of filters in the convolutional layers, the maximum epochs, the batch size or other parameters. Furthermore, other techniques can be applied to improve the results by changing: the network weight initialization method, the normalization method, the validation method (E.g., by using 10-Fold Cross-Validation), the training algorithm, the feature selection method or use a feature extraction technique. In addition data handling methods can be used to create a balanced dataset from an imbalanced dataset like the Synthetic Minority Oversampling Technique (SMOTE) ([Chawla et al., 2002](#ch9.xhtml#ref9_4)). Also, data augmentation methods can be implemented to increase the dataset instances and improve the generalization and the accuracy of the deep learning models.

## References

*   [Abdullah-Al-Wadud, M., Kabir, M. H., Dewan, M. A. A. and Chae, O.](#ch9.xhtml#R_ref9_1) (2007). A dynamic histogram equalization for image contrast enhancement. IEEE Transactions on Consumer Electronics, 53(2): 593-600. doi: [10.1109/TCE.2007.381734](http://doi.org/10.1109/TCE.2007.381734).
*   [Behera, S., Misra, R. and Sillitti, A.](#ch9.xhtml#R_ref9_2) (2021). Multiscale deep bidirectional gated recurrent neural networks based prognostic method for complex non-linear degradation systems. Information Sciences, 554: 120-144.
*   [Chadha, G. S., Panambilly, A., Schwung, A. and Ding, S. X.](#ch9.xhtml#R_ref9_3) (2020). Bidirectional deep recurrent neural networks for process fault classification. ISA Transactions, 106: 330-342.
*   [Chawla, N. V., Bowyer, K. W., Hall, L. O. and Kegelmeyer, W. P.](#ch9.xhtml#R_ref9_4) (2002). SMOTE: synthetic minority over-sampling technique. Journal of Artificial Intelligence Research, 16: 321-357.
*   [Cohen, J. P., Morrison, P. and Dao, L.](#ch9.xhtml#R_ref9_5) (2020). COVID-19 image data collection. arXiv preprint arXiv:2003.11597. [https://github.com/ieee8023/covid-chestxray-dataset.](https://github.com)
*   [Cortez, B., Carrera, B., Kim, Y. J. and Jung, J. Y.](#ch9.xhtml#R_ref9_6) (2018). An architecture for emergency event prediction using LSTM recurrent neural networks. Expert Systems with Applications, 97: 315-324.
*   [Ilonen, J., Kamarainen, J. K. and Lampinen, J.](#ch9.xhtml#R_ref9_7) (2003). Differential evolution training algorithm for feed-forward neural networks. Neural Processing Letters, 17(1): 93-105.
*   [Kim, T. Y. and Cho, S. B.](#ch9.xhtml#R_ref9_8) (2019). Particle swarm optimization-based CNN-LSTM networks for forecasting energy consumption. pp. 1510-1516. In: 2019 IEEE Congress on Evolutionary Computation (CEC). IEEE.
*   [Koppu, S., Maddikunta, P. K. R. and Srivastava, G.](#ch9.xhtml#R_ref9_9) (2020). Deep learning disease prediction model for use with intelligent robots. Computers & Electrical Engineering, 87: 106765.
*   Kouziokas, G. N. (2021). Deep bidirectional and unidirectional LSTM neural networks in traffic flow forecasting from environmental factors. Advances in Mobility-as-aService Systems, 1278: 171-180. doi: [https://doi.org/10.1007/978-3-030-61075-3\_17.](https://doi.org/10.1007/978-3-030-61075-3_17.)
*   [Kudo, M., Toyama, J. and Shimbo, M.](#ch9.xhtml#R_ref9_11) (1999). Multidimensional curve classification using passing-through regions. Pattern Recognition Letters, 20(11-13): 1103-1111.
*   [LeCun, Y., Kavukcuoglu, K. and Farabet, C.](#ch9.xhtml#R_ref9_12) (2010). Convolutional networks and applications in vision. pp. 253-256. In: Proceedings of 2010 IEEE International Symposium on Circuits and Systems. IEEE.
*   [LeCun, Y., Bengio, Y. and Hinton, G.](#ch9.xhtml#R_ref9_13) (2015). Deep learning. Nature, 521(7553): 436-444.
*   [Ren, X., Liu, S., Yu, X. and Dong, X.](#ch9.xhtml#R_ref9_14) (2021). A method for state-of-charge estimation of lithium-ion batteries based on PSO-LSTM. Energy, 234: 121236.
*   [Schuster, M. and Paliwal, K. K.](#ch9.xhtml#R_ref9_15) (1997). Bidirectional recurrent neural networks. IEEE Transactions on Signal Processing, 45(11): 2673-2681.
*   [Shahid, F., Zameer, A. and Muneeb, M.](#ch9.xhtml#R_ref9_16) (2020). Predictions for COVID-19 with deep learning models of LSTM, GRU and Bi-LSTM. Chaos, Solitons & Fractals, 140: 110212.
*   [Socha, K. and Blum, C.](#ch9.xhtml#R_ref9_17) (2007). An ant colony optimization algorithm for continuous optimization: application to feed-forward neural network training. Neural Computing and Applications, 16(3): 235-247.
*   [Wang, P., Zhao, J., Gao, Y., Sotelo, M. A. and Li, Z.](#ch9.xhtml#R_ref9_18) (2020). Lane work-schedule of toll station based on queuing theory and PSO-LSTM model. IEEE Access, 8: 84434-84443.
*   [Zhang, B., Zhang, H., Zhao, G. and Lian, J.](#ch9.xhtml#R_ref9_19) (2020). Constructing a PM2. 5 concentration prediction model by combining auto-encoder with Bi-LSTM neural networks. Environmental Modelling & Software, 124: 104600.

# Index

## A

*   ABC Algorithm [77](#ch4.xhtml#p77), [78](#ch4.xhtml#p78), [80](#ch4.xhtml#p80), [82](#ch4.xhtml#p82)
*   absorption coefficient [112–114](#ch6.xhtml#p112), [116](#ch6.xhtml#p116)
*   Acceleration coefficients [39](#ch3.xhtml#p39), [58](#ch3.xhtml#p58)
*   acceleration parameters [127](#ch6.xhtml#p127)
*   accepting rate [118](#ch6.xhtml#p118), [120](#ch6.xhtml#p120), [170](#ch8.xhtml#p170)
*   accuracy [57](#ch3.xhtml#p57), [154](#ch7.xhtml#p154), [158](#ch8.xhtml#p158), [165](#ch8.xhtml#p165), [183](#ch9.xhtml#p183), [184](#ch9.xhtml#p184), [186–190](#ch9.xhtml#p186), [194](#ch9.xhtml#p194)
*   Ackley function [32](#ch2.xhtml#p32), [33](#ch2.xhtml#p33), [60](#ch3.xhtml#p60), [62](#ch3.xhtml#p62), [119](#ch6.xhtml#p119), [120](#ch6.xhtml#p120)
*   activation function [158](#ch8.xhtml#p158), [180](#ch9.xhtml#p180), [181](#ch9.xhtml#p181), [189](#ch9.xhtml#p189), [190](#ch9.xhtml#p190)
*   activation layers [181](#ch9.xhtml#p181)
*   Adadelta [1](#ch1.xhtml#p1), [15](#ch1.xhtml#p15), [16](#ch1.xhtml#p16)
*   Adagrad [1](#ch1.xhtml#p1), [14](#ch1.xhtml#p14), [15](#ch1.xhtml#p15)
*   Adam optimizer [1](#ch1.xhtml#p1), [16](#ch1.xhtml#p16), [190](#ch9.xhtml#p190)
*   adaptive genetic algorithm [28](#ch2.xhtml#p28)
*   adaptive inertia weight [40](#ch3.xhtml#p40), [184](#ch9.xhtml#p184), [185](#ch9.xhtml#p185), [193](#ch9.xhtml#p193)
*   adaptive parameter [81](#ch4.xhtml#p81), [97](#ch5.xhtml#p97), [150](#ch7.xhtml#p150)
*   Age-based strategy [76](#ch4.xhtml#p76)
*   Algorithms [1](#ch1.xhtml#p1), [3](#ch1.xhtml#p3), [5](#ch1.xhtml#p5), [7](#ch1.xhtml#p7), [8](#ch1.xhtml#p8), [10–17](#ch1.xhtml#p10), [19–24](#ch2.xhtml#p19), [26](#ch2.xhtml#p26), [28](#ch2.xhtml#p28), [29](#ch2.xhtml#p29), [31](#ch2.xhtml#p31), [32](#ch2.xhtml#p32), [37–42](#ch3.xhtml#p37), [44–58](#ch3.xhtml#p44), [67–71](#ch4.xhtml#p67), [74–78](#ch4.xhtml#p74), [80](#ch4.xhtml#p80), [82](#ch4.xhtml#p82), [87–91](#ch5.xhtml#p87), [94–96](#ch5.xhtml#p94), [98–103](#ch5.xhtml#p98), [105–107](#ch5.xhtml#p105), [111–118](#ch6.xhtml#p111), [120](#ch6.xhtml#p120), [121](#ch6.xhtml#p121), [123–127](#ch6.xhtml#p123), [131](#ch7.xhtml#p131), [133](#ch7.xhtml#p133)\- [135](#ch7.xhtml#p135), [139–141](#ch7.xhtml#p139), [143–148](#ch7.xhtml#p143), [150–154](#ch7.xhtml#p150), [157](#ch8.xhtml#p157), [159](#ch8.xhtml#p159), [161](#ch8.xhtml#p161), [166–176](#ch8.xhtml#p166), [183](#ch9.xhtml#p183), [184](#ch9.xhtml#p184), [191](#ch9.xhtml#p191), [194](#ch9.xhtml#p194)
*   Alpha wolves [133](#ch7.xhtml#p133), [136](#ch7.xhtml#p136), [139](#ch7.xhtml#p139)
*   Ant Colony Optimization [17](#ch1.xhtml#p17), [67](#ch4.xhtml#p67), [68](#ch4.xhtml#p68), [157](#ch8.xhtml#p157)
*   Ant density [70](#ch4.xhtml#p70)
*   ant population [160](#ch8.xhtml#p160)
*   Ant System [67–69](#ch4.xhtml#p67), [71–75](#ch4.xhtml#p71)
*   ANT-cycle [70](#ch4.xhtml#p70), [71](#ch4.xhtml#p71)
*   ANT-density [70](#ch4.xhtml#p70)
*   ANT-quantity [70](#ch4.xhtml#p70)
*   appliances energy consumption [162](#ch8.xhtml#p162), [163](#ch8.xhtml#p163)
*   arithmetic crossover [24](#ch2.xhtml#p24)
*   Artificial Bee Colony [17](#ch1.xhtml#p17), [58](#ch3.xhtml#p58), [67](#ch4.xhtml#p67), [76](#ch4.xhtml#p76), [77](#ch4.xhtml#p77), [81](#ch4.xhtml#p81), [159](#ch8.xhtml#p159)
*   Attacking prey [134](#ch7.xhtml#p134)
*   attraction intensity [149](#ch7.xhtml#p149)
*   attraction length scale [149](#ch7.xhtml#p149)
*   attraction zone [150](#ch7.xhtml#p150)
*   attractiveness [111](#ch6.xhtml#p111), [112](#ch6.xhtml#p112), [114–116](#ch6.xhtml#p114)
*   average pooling [181](#ch9.xhtml#p181), [190](#ch9.xhtml#p190)

## B

*   bandwidth distance [118](#ch6.xhtml#p118), [121](#ch6.xhtml#p121)
*   Bat Movement [100](#ch5.xhtml#p100)
*   Bat Swarm Algorithm [87](#ch5.xhtml#p87)
*   Best Fitness Value [22](#ch2.xhtml#p22), [28–30](#ch2.xhtml#p28), [41](#ch3.xhtml#p41), [80](#ch4.xhtml#p80), [81](#ch4.xhtml#p81), [124](#ch6.xhtml#p124), [168](#ch8.xhtml#p168), [171](#ch8.xhtml#p171), [173](#ch8.xhtml#p173)
*   beta wolves [133](#ch7.xhtml#p133), [136](#ch7.xhtml#p136), [139](#ch7.xhtml#p139)
*   bias [7](#ch1.xhtml#p7), [16](#ch1.xhtml#p16), [180](#ch9.xhtml#p180)
*   Bidirectional LSTM [180](#ch9.xhtml#p180), [184](#ch9.xhtml#p184), [185](#ch9.xhtml#p185)
*   BiLSTM [185](#ch9.xhtml#p185), [186](#ch9.xhtml#p186), [188](#ch9.xhtml#p188)
*   bilstm layer [185](#ch9.xhtml#p185)
*   Binary bat algorithm [87](#ch5.xhtml#p87), [101](#ch5.xhtml#p101), [102](#ch5.xhtml#p102), [111](#ch6.xhtml#p111)
*   binary discrete cat algorithm [125](#ch6.xhtml#p125)
*   Binary grey wolf optimization [131](#ch7.xhtml#p131), [135](#ch7.xhtml#p135), [138](#ch7.xhtml#p138), [161](#ch8.xhtml#p161)
*   binary solution [94](#ch5.xhtml#p94), [95](#ch5.xhtml#p95)
*   Binary Whale Optimization [131](#ch7.xhtml#p131), [147](#ch7.xhtml#p147)
*   blend crossover [25](#ch2.xhtml#p25)
*   Boundary Handling [45](#ch3.xhtml#p45), [46](#ch3.xhtml#p46), [67](#ch4.xhtml#p67), [81](#ch4.xhtml#p81), [82](#ch4.xhtml#p82)
*   boundary violation [82](#ch4.xhtml#p82)
*   Bubble-net attacking strategy [142](#ch7.xhtml#p142)

## C

*   cat position [125–127](#ch6.xhtml#p125)
*   cat swarm algorithm [111](#ch6.xhtml#p111), [123–126](#ch6.xhtml#p123)
*   cat swarm optimization [17](#ch1.xhtml#p17), [111](#ch6.xhtml#p111), [123](#ch6.xhtml#p123), [126](#ch6.xhtml#p126), [127](#ch6.xhtml#p127)
*   cat velocity [124](#ch6.xhtml#p124)
*   Cauchy distribution [26](#ch2.xhtml#p26), [48](#ch3.xhtml#p48), [106](#ch5.xhtml#p106), [107](#ch5.xhtml#p107)
*   Cauchy distribution function [26](#ch2.xhtml#p26), [106](#ch5.xhtml#p106), [107](#ch5.xhtml#p107)
*   Cauchy mutation [26](#ch2.xhtml#p26), [48](#ch3.xhtml#p48), [105–107](#ch5.xhtml#p105)
*   Cauchy mutation operator [26](#ch2.xhtml#p26), [105–107](#ch5.xhtml#p105)
*   Cauchy Mutation PSO [48](#ch3.xhtml#p48)
*   cell candidate [179](#ch9.xhtml#p179), [180](#ch9.xhtml#p180)
*   Chaotic Bat Algorithm [87](#ch5.xhtml#p87), [101–103](#ch5.xhtml#p101), [111](#ch6.xhtml#p111)
*   Chaotic cuckoo search [87](#ch5.xhtml#p87), [91](#ch5.xhtml#p91), [166](#ch8.xhtml#p166), [171](#ch8.xhtml#p171), [172](#ch8.xhtml#p172), [175](#ch8.xhtml#p175)
*   chaotic differential evolution [19](#ch2.xhtml#p19), [31](#ch2.xhtml#p31), [32](#ch2.xhtml#p32)
*   chaotic firefly [111](#ch6.xhtml#p111), [114](#ch6.xhtml#p114), [116](#ch6.xhtml#p116)
*   Chaotic Grasshopper Optimization [131](#ch7.xhtml#p131), [152](#ch7.xhtml#p152)
*   chaotic harmony search [111](#ch6.xhtml#p111), [121](#ch6.xhtml#p121), [166](#ch8.xhtml#p166), [169–171](#ch8.xhtml#p169), [175](#ch8.xhtml#p175)
*   Chaotic PSO [37](#ch3.xhtml#p37), [49](#ch3.xhtml#p49), [50](#ch3.xhtml#p50)
*   chaotic sequences [31](#ch2.xhtml#p31), [32](#ch2.xhtml#p32), [49](#ch3.xhtml#p49), [116](#ch6.xhtml#p116), [121](#ch6.xhtml#p121)
*   Chebyshev map [92](#ch5.xhtml#p92), [102](#ch5.xhtml#p102)
*   Chromosome [20](#ch2.xhtml#p20), [21](#ch2.xhtml#p21), [23](#ch2.xhtml#p23), [25](#ch2.xhtml#p25), [29](#ch2.xhtml#p29), [159](#ch8.xhtml#p159), [167](#ch8.xhtml#p167), [173](#ch8.xhtml#p173)
*   chromosome population [20](#ch2.xhtml#p20), [21](#ch2.xhtml#p21), [159](#ch8.xhtml#p159)
*   circle map [92](#ch5.xhtml#p92), [102](#ch5.xhtml#p102), [122](#ch6.xhtml#p122)
*   classification [49](#ch3.xhtml#p49), [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [159](#ch8.xhtml#p159), [161](#ch8.xhtml#p161), [165](#ch8.xhtml#p165), [181](#ch9.xhtml#p181), [183](#ch9.xhtml#p183), [185](#ch9.xhtml#p185), [187–193](#ch9.xhtml#p187)
*   classification layer [185](#ch9.xhtml#p185)
*   classification metric [192](#ch9.xhtml#p192), [193](#ch9.xhtml#p193)
*   CNN optimization [189](#ch9.xhtml#p189)
*   combination coefficient [8](#ch1.xhtml#p8)
*   comfort zone [148](#ch7.xhtml#p148)
*   computational cost [3](#ch1.xhtml#p3), [7](#ch1.xhtml#p7)
*   computational optimization [1](#ch1.xhtml#p1), [37](#ch3.xhtml#p37), [57](#ch3.xhtml#p57), [88](#ch5.xhtml#p88), [111](#ch6.xhtml#p111), [117](#ch6.xhtml#p117)
*   confusion matrix [192](#ch9.xhtml#p192), [193](#ch9.xhtml#p193)
*   connection weights [158](#ch8.xhtml#p158)
*   Constant Mutation PSO [50](#ch3.xhtml#p50)
*   constrained optimization [68](#ch4.xhtml#p68), [101](#ch5.xhtml#p101)
*   Continuous [2](#ch1.xhtml#p2), [4](#ch1.xhtml#p4), [17](#ch1.xhtml#p17), [32](#ch2.xhtml#p32), [58](#ch3.xhtml#p58), [61–63](#ch3.xhtml#p61), [68](#ch4.xhtml#p68), [87](#ch5.xhtml#p87), [94](#ch5.xhtml#p94), [101](#ch5.xhtml#p101), [119](#ch6.xhtml#p119), [125](#ch6.xhtml#p125), [135–137](#ch7.xhtml#p135), [185](#ch9.xhtml#p185)
*   continuous optimization [2](#ch1.xhtml#p2), [68](#ch4.xhtml#p68), [87](#ch5.xhtml#p87), [94](#ch5.xhtml#p94), [125](#ch6.xhtml#p125), [135](#ch7.xhtml#p135)
*   Convex [1](#ch1.xhtml#p1), [2](#ch1.xhtml#p2), [17](#ch1.xhtml#p17), [37](#ch3.xhtml#p37), [55](#ch3.xhtml#p55), [56](#ch3.xhtml#p56), [58](#ch3.xhtml#p58), [62](#ch3.xhtml#p62)
*   Convex combination [55](#ch3.xhtml#p55), [56](#ch3.xhtml#p56)
*   convex optimization [2](#ch1.xhtml#p2)
*   convolutional layers [181](#ch9.xhtml#p181), [182](#ch9.xhtml#p182), [194](#ch9.xhtml#p194)
*   convolutional neural networks [179](#ch9.xhtml#p179), [181](#ch9.xhtml#p181)
*   cooling factor [101](#ch5.xhtml#p101)
*   crossover [19–21](#ch2.xhtml#p19), [23–25](#ch2.xhtml#p23), [28–31](#ch2.xhtml#p28), [33](#ch2.xhtml#p33), [47](#ch3.xhtml#p47), [56](#ch3.xhtml#p56), [82](#ch4.xhtml#p82), [96](#ch5.xhtml#p96), [97](#ch5.xhtml#p97), [135](#ch7.xhtml#p135), [138](#ch7.xhtml#p138), [159](#ch8.xhtml#p159), [160](#ch8.xhtml#p160), [167](#ch8.xhtml#p167), [168](#ch8.xhtml#p168), [172](#ch8.xhtml#p172), [184](#ch9.xhtml#p184)
*   crossover factor [30](#ch2.xhtml#p30), [31](#ch2.xhtml#p31)
*   crossover probability [28](#ch2.xhtml#p28), [29](#ch2.xhtml#p29), [33](#ch2.xhtml#p33), [160](#ch8.xhtml#p160), [172](#ch8.xhtml#p172)
*   crossover type [159](#ch8.xhtml#p159), [167](#ch8.xhtml#p167), [168](#ch8.xhtml#p168), [184](#ch9.xhtml#p184)
*   Cuckoo breeding behavior [87](#ch5.xhtml#p87)
*   Cuckoo search [17](#ch1.xhtml#p17), [87–91](#ch5.xhtml#p87), [94–97](#ch5.xhtml#p94), [166](#ch8.xhtml#p166), [171](#ch8.xhtml#p171), [172](#ch8.xhtml#p172), [175](#ch8.xhtml#p175)

## D

*   decay rate [15](#ch1.xhtml#p15), [73](#ch4.xhtml#p73), [160](#ch8.xhtml#p160)
*   Decision space [53](#ch3.xhtml#p53), [54](#ch3.xhtml#p54)
*   decreasing coefficient parameter [150](#ch7.xhtml#p150)
*   deep learning [1](#ch1.xhtml#p1), [16](#ch1.xhtml#p16), [179](#ch9.xhtml#p179), [181–183](#ch9.xhtml#p181), [194](#ch9.xhtml#p194)
*   Delta well quantum PSO [51–53](#ch3.xhtml#p51)
*   delta wolves [133](#ch7.xhtml#p133), [136](#ch7.xhtml#p136), [139](#ch7.xhtml#p139)
*   density function [26](#ch2.xhtml#p26), [27](#ch2.xhtml#p27), [48](#ch3.xhtml#p48), [51](#ch3.xhtml#p51), [52](#ch3.xhtml#p52), [107](#ch5.xhtml#p107)
*   Differentiable [32](#ch2.xhtml#p32), [60–62](#ch3.xhtml#p60), [119](#ch6.xhtml#p119)
*   differential evolution [19](#ch2.xhtml#p19), [29–33](#ch2.xhtml#p29), [82](#ch4.xhtml#p82), [95](#ch5.xhtml#p95), [96](#ch5.xhtml#p96), [154](#ch7.xhtml#p154)
*   differential variation amplification [30](#ch2.xhtml#p30)
*   Discrete Binary cuckoo search [87](#ch5.xhtml#p87), [94](#ch5.xhtml#p94)
*   discrete crossover [24](#ch2.xhtml#p24)
*   discrete optimization [2](#ch1.xhtml#p2), [68](#ch4.xhtml#p68), [94](#ch5.xhtml#p94)
*   Disruptive Selection [67](#ch4.xhtml#p67), [80](#ch4.xhtml#p80)
*   Distance [70](#ch4.xhtml#p70), [71](#ch4.xhtml#p71), [75](#ch4.xhtml#p75), [77](#ch4.xhtml#p77), [95–98](#ch5.xhtml#p95), [105](#ch5.xhtml#p105), [111](#ch6.xhtml#p111), [112](#ch6.xhtml#p112), [114](#ch6.xhtml#p114), [115](#ch6.xhtml#p115), [118](#ch6.xhtml#p118), [121](#ch6.xhtml#p121), [142](#ch7.xhtml#p142), [147–149](#ch7.xhtml#p147), [151](#ch7.xhtml#p151)
*   distribution function [26](#ch2.xhtml#p26), [27](#ch2.xhtml#p27), [48](#ch3.xhtml#p48), [106](#ch5.xhtml#p106), [107](#ch5.xhtml#p107)
*   distribution index [25](#ch2.xhtml#p25), [27](#ch2.xhtml#p27)
*   diversity mutation [26](#ch2.xhtml#p26)
*   Dominance [53](#ch3.xhtml#p53), [55](#ch3.xhtml#p55)
*   Dominated solution [54](#ch3.xhtml#p54), [55](#ch3.xhtml#p55)
*   double mutation [87](#ch5.xhtml#p87), [101](#ch5.xhtml#p101), [105](#ch5.xhtml#p105)
*   dropout layers [181](#ch9.xhtml#p181)
*   Dynamic or Adaptive Topologies [44](#ch3.xhtml#p44)

## E

*   Elitism strategy [76](#ch4.xhtml#p76)
*   Employed bee [77–79](#ch4.xhtml#p77)
*   Employed foragers [76](#ch4.xhtml#p76), [77](#ch4.xhtml#p77)
*   Encircling prey [132](#ch7.xhtml#p132), [141](#ch7.xhtml#p141)
*   energy prediction [161](#ch8.xhtml#p161), [162](#ch8.xhtml#p162)
*   entry-wise multiplication [115](#ch6.xhtml#p115), [145](#ch7.xhtml#p145)
*   epochs [183](#ch9.xhtml#p183), [185](#ch9.xhtml#p185), [190](#ch9.xhtml#p190), [194](#ch9.xhtml#p194)
*   error metric [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [159](#ch8.xhtml#p159), [174](#ch8.xhtml#p174), [182](#ch9.xhtml#p182), [183](#ch9.xhtml#p183)
*   evaporation coefficient rate [73](#ch4.xhtml#p73)
*   evaporation rate [69](#ch4.xhtml#p69), [74](#ch4.xhtml#p74), [160](#ch8.xhtml#p160)
*   evolutionary algorithms [19](#ch2.xhtml#p19), [20](#ch2.xhtml#p20), [37](#ch3.xhtml#p37), [157](#ch8.xhtml#p157), [166](#ch8.xhtml#p166), [172–175](#ch8.xhtml#p172)
*   evolutionary computation [19](#ch2.xhtml#p19), [179](#ch9.xhtml#p179)
*   evolutionary strategy [19](#ch2.xhtml#p19)
*   exploitation [72](#ch4.xhtml#p72), [89](#ch5.xhtml#p89), [90](#ch5.xhtml#p90), [95](#ch5.xhtml#p95), [100](#ch5.xhtml#p100), [107](#ch5.xhtml#p107), [134](#ch7.xhtml#p134), [140](#ch7.xhtml#p140), [142](#ch7.xhtml#p142), [144](#ch7.xhtml#p144), [145](#ch7.xhtml#p145), [148](#ch7.xhtml#p148), [150–153](#ch7.xhtml#p150)
*   exploration [26](#ch2.xhtml#p26), [72](#ch4.xhtml#p72), [89](#ch5.xhtml#p89), [90](#ch5.xhtml#p90), [95](#ch5.xhtml#p95), [97](#ch5.xhtml#p97), [98](#ch5.xhtml#p98), [100](#ch5.xhtml#p100), [134](#ch7.xhtml#p134), [140](#ch7.xhtml#p140), [143–145](#ch7.xhtml#p143), [148](#ch7.xhtml#p148), [150–154](#ch7.xhtml#p150), [160](#ch8.xhtml#p160)
*   exploration constant [160](#ch8.xhtml#p160)
*   exploration process [72](#ch4.xhtml#p72), [140](#ch7.xhtml#p140)
*   exploration strategies [95](#ch5.xhtml#p95)
*   Exponential [23](#ch2.xhtml#p23), [26](#ch2.xhtml#p26), [47](#ch3.xhtml#p47), [67](#ch4.xhtml#p67), [81](#ch4.xhtml#p81), [82](#ch4.xhtml#p82)
*   Exponential Rank Selection [81](#ch4.xhtml#p81)
*   exponential ranking selection [23](#ch2.xhtml#p23)
*   External global memory [54](#ch3.xhtml#p54)

## F

*   F1 [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [165](#ch8.xhtml#p165)
*   false negative [190](#ch9.xhtml#p190)
*   false positive [190](#ch9.xhtml#p190), [191](#ch9.xhtml#p191)
*   Feasible set [53](#ch3.xhtml#p53)
*   feature extraction [181](#ch9.xhtml#p181), [194](#ch9.xhtml#p194)
*   feature maps [181](#ch9.xhtml#p181)
*   feature selection [101](#ch5.xhtml#p101), [131](#ch7.xhtml#p131), [135](#ch7.xhtml#p135), [157](#ch8.xhtml#p157), [161](#ch8.xhtml#p161), [162](#ch8.xhtml#p162), [165](#ch8.xhtml#p165), [166](#ch8.xhtml#p166), [168](#ch8.xhtml#p168), [171](#ch8.xhtml#p171), [174](#ch8.xhtml#p174), [194](#ch9.xhtml#p194)
*   filters [181](#ch9.xhtml#p181), [182](#ch9.xhtml#p182), [190](#ch9.xhtml#p190), [194](#ch9.xhtml#p194)
*   firefly algorithm [17](#ch1.xhtml#p17), [111–116](#ch6.xhtml#p111)
*   Fitness Convergence [42](#ch3.xhtml#p42)
*   fitness function [2](#ch1.xhtml#p2), [20](#ch2.xhtml#p20), [21](#ch2.xhtml#p21), [28](#ch2.xhtml#p28), [37–41](#ch3.xhtml#p37), [52](#ch3.xhtml#p52), [79](#ch4.xhtml#p79), [80](#ch4.xhtml#p80), [89](#ch5.xhtml#p89), [112](#ch6.xhtml#p112), [123](#ch6.xhtml#p123), [125](#ch6.xhtml#p125), [134](#ch7.xhtml#p134), [135](#ch7.xhtml#p135), [158](#ch8.xhtml#p158), [166](#ch8.xhtml#p166), [183](#ch9.xhtml#p183)
*   fitness limit [28](#ch2.xhtml#p28)
*   Fletcher-Reeves formula [6](#ch1.xhtml#p6)
*   flipping cha [94](#ch5.xhtml#p94), [95](#ch5.xhtml#p95)
*   F-measure [191–193](#ch9.xhtml#p191)
*   food resources [67](#ch4.xhtml#p67), [78](#ch4.xhtml#p78)
*   Foraging behavior [67](#ch4.xhtml#p67), [68](#ch4.xhtml#p68), [76](#ch4.xhtml#p76), [77](#ch4.xhtml#p77)
*   forget gate [179](#ch9.xhtml#p179), [180](#ch9.xhtml#p180)
*   Fourier transformation [139](#ch7.xhtml#p139)
*   Frequencies [100](#ch5.xhtml#p100), [103–105](#ch5.xhtml#p103)
*   F-score [183](#ch9.xhtml#p183)
*   fully-connected layers [181](#ch9.xhtml#p181)
*   function [2](#ch1.xhtml#p2), [4](#ch1.xhtml#p4), [5](#ch1.xhtml#p5), [7](#ch1.xhtml#p7), [8](#ch1.xhtml#p8), [15](#ch1.xhtml#p15), [17](#ch1.xhtml#p17), [19–21](#ch2.xhtml#p19), [26–28](#ch2.xhtml#p26), [32](#ch2.xhtml#p32), [33](#ch2.xhtml#p33), [37–42](#ch3.xhtml#p37), [44](#ch3.xhtml#p44), [48–54](#ch3.xhtml#p48), [57–63](#ch3.xhtml#p57), [74](#ch4.xhtml#p74), [79](#ch4.xhtml#p79), [80](#ch4.xhtml#p80), [89](#ch5.xhtml#p89), [91](#ch5.xhtml#p91), [94](#ch5.xhtml#p94), [95](#ch5.xhtml#p95), [98](#ch5.xhtml#p98), [99](#ch5.xhtml#p99), [101](#ch5.xhtml#p101), [102](#ch5.xhtml#p102), [104](#ch5.xhtml#p104), [106](#ch5.xhtml#p106), [107](#ch5.xhtml#p107), [112–114](#ch6.xhtml#p112), [116–121](#ch6.xhtml#p116), [123](#ch6.xhtml#p123), [125](#ch6.xhtml#p125), [134](#ch7.xhtml#p134), [135](#ch7.xhtml#p135), [139](#ch7.xhtml#p139), [140](#ch7.xhtml#p140), [146–149](#ch7.xhtml#p146), [154](#ch7.xhtml#p154), [158](#ch8.xhtml#p158), [159](#ch8.xhtml#p159), [165](#ch8.xhtml#p165), [166](#ch8.xhtml#p166), [174](#ch8.xhtml#p174), [180–184](#ch9.xhtml#p180), [189](#ch9.xhtml#p189), [190](#ch9.xhtml#p190)

## G

*   gamma function [140](#ch7.xhtml#p140)
*   gamma parameter [139](#ch7.xhtml#p139)
*   gauss map [122](#ch6.xhtml#p122)
*   Gaussian distribution [26](#ch2.xhtml#p26), [48](#ch3.xhtml#p48), [107](#ch5.xhtml#p107)
*   Gaussian map [92](#ch5.xhtml#p92)
*   gaussian mutation [26](#ch2.xhtml#p26), [48](#ch3.xhtml#p48), [105](#ch5.xhtml#p105), [107](#ch5.xhtml#p107), [153](#ch7.xhtml#p153)
*   Gaussian Mutation PSO [48](#ch3.xhtml#p48)
*   Gauss-Newton [1–3](#ch1.xhtml#p1), [6](#ch1.xhtml#p6)
*   Generation [20–22](#ch2.xhtml#p20), [24](#ch2.xhtml#p24), [28–30](#ch2.xhtml#p28), [41](#ch3.xhtml#p41), [42](#ch3.xhtml#p42), [48](#ch3.xhtml#p48), [58](#ch3.xhtml#p58), [82](#ch4.xhtml#p82), [88](#ch5.xhtml#p88), [89](#ch5.xhtml#p89), [91](#ch5.xhtml#p91), [113](#ch6.xhtml#p113), [114](#ch6.xhtml#p114), [159](#ch8.xhtml#p159), [160](#ch8.xhtml#p160), [167](#ch8.xhtml#p167), [168](#ch8.xhtml#p168), [170–173](#ch8.xhtml#p170), [184](#ch9.xhtml#p184)
*   genetic algorithm [1](#ch1.xhtml#p1), [17](#ch1.xhtml#p17), [19–24](#ch2.xhtml#p19), [28](#ch2.xhtml#p28), [49](#ch3.xhtml#p49), [57](#ch3.xhtml#p57), [58](#ch3.xhtml#p58), [90](#ch5.xhtml#p90), [102](#ch5.xhtml#p102), [157](#ch8.xhtml#p157), [159](#ch8.xhtml#p159), [161](#ch8.xhtml#p161), [166–168](#ch8.xhtml#p166), [175](#ch8.xhtml#p175), [184](#ch9.xhtml#p184)
*   Geometric PSO [55](#ch3.xhtml#p55), [56](#ch3.xhtml#p56), [168](#ch8.xhtml#p168), [175](#ch8.xhtml#p175)
*   global best position [107](#ch5.xhtml#p107), [127](#ch6.xhtml#p127)
*   global learning [14](#ch1.xhtml#p14), [38](#ch3.xhtml#p38), [39](#ch3.xhtml#p39), [56](#ch3.xhtml#p56), [160](#ch8.xhtml#p160), [176](#ch8.xhtml#p176), [185](#ch9.xhtml#p185), [193](#ch9.xhtml#p193)
*   global learning rate [14](#ch1.xhtml#p14)
*   Global Minima [60–63](#ch3.xhtml#p60)
*   Global or Fully Connected [42](#ch3.xhtml#p42), [43](#ch3.xhtml#p43)
*   global pheromone decay [73](#ch4.xhtml#p73), [160](#ch8.xhtml#p160)
*   global pheromone decay rate [160](#ch8.xhtml#p160)
*   Global pheromone updating rule [72](#ch4.xhtml#p72)
*   globally optimal solution [2](#ch1.xhtml#p2)
*   gradient methods [5](#ch1.xhtml#p5), [6](#ch1.xhtml#p6)
*   gradient subvector [12](#ch1.xhtml#p12)
*   gradient threshold [185](#ch9.xhtml#p185)
*   gradient vector [2](#ch1.xhtml#p2), [10–12](#ch1.xhtml#p10)
*   Grasshopper Optimization [17](#ch1.xhtml#p17), [131](#ch7.xhtml#p131), [148](#ch7.xhtml#p148), [151–154](#ch7.xhtml#p151)
*   Grasshopper Optimization Algorithm [131](#ch7.xhtml#p131), [148](#ch7.xhtml#p148), [151–154](#ch7.xhtml#p151)
*   gravitational constant [149](#ch7.xhtml#p149)
*   greedy selection [30](#ch2.xhtml#p30), [139](#ch7.xhtml#p139), [141](#ch7.xhtml#p141)
*   Grey Wolf Optimization [17](#ch1.xhtml#p17), [131](#ch7.xhtml#p131), [134](#ch7.xhtml#p134), [135](#ch7.xhtml#p135), [138](#ch7.xhtml#p138), [161](#ch8.xhtml#p161)
*   Griewank Function [58](#ch3.xhtml#p58), [59](#ch3.xhtml#p59), [61](#ch3.xhtml#p61)

## H

*   Hadamard product [180](#ch9.xhtml#p180)
*   Harmonic quantum PSO [51](#ch3.xhtml#p51), [52](#ch3.xhtml#p52)
*   harmony memory [117–120](#ch6.xhtml#p117), [169](#ch8.xhtml#p169), [170](#ch8.xhtml#p170)
*   harmony search [17](#ch1.xhtml#p17), [90](#ch5.xhtml#p90), [111](#ch6.xhtml#p111), [117–121](#ch6.xhtml#p117), [166](#ch8.xhtml#p166), [169–171](#ch8.xhtml#p169), [175](#ch8.xhtml#p175)
*   Heaviside function [89](#ch5.xhtml#p89)
*   Henon map [122](#ch6.xhtml#p122)
*   Hessian matrix [2](#ch1.xhtml#p2), [3](#ch1.xhtml#p3), [5](#ch1.xhtml#p5), [10–13](#ch1.xhtml#p10)
*   Hestenes-Stiefel formula [6](#ch1.xhtml#p6)
*   heuristic information [74](#ch4.xhtml#p74)
*   hidden layer [57](#ch3.xhtml#p57), [157–159](#ch8.xhtml#p157), [182](#ch9.xhtml#p182), [185–190](#ch9.xhtml#p185), [194](#ch9.xhtml#p194)
*   hidden layer neurons [158](#ch8.xhtml#p158), [185](#ch9.xhtml#p185), [194](#ch9.xhtml#p194)
*   hidden neurons [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [159](#ch8.xhtml#p159), [182](#ch9.xhtml#p182), [190](#ch9.xhtml#p190)
*   histogram equalization [191](#ch9.xhtml#p191)
*   humpback whales [141–143](#ch7.xhtml#p141), [145](#ch7.xhtml#p145)
*   hunting process [132–134](#ch7.xhtml#p132)
*   Hyperbolic Method [45](#ch3.xhtml#p45), [82](#ch4.xhtml#p82)
*   Hypercube [54](#ch3.xhtml#p54), [55](#ch3.xhtml#p55)
*   hyperparameters [174–176](#ch8.xhtml#p174), [181](#ch9.xhtml#p181), [185–188](#ch9.xhtml#p185), [190](#ch9.xhtml#p190), [194](#ch9.xhtml#p194)

## I

*   Ikeda map [32](#ch2.xhtml#p32)
*   improved harmony search [111](#ch6.xhtml#p111), [120](#ch6.xhtml#p120), [121](#ch6.xhtml#p121)
*   individual solution [22](#ch2.xhtml#p22), [23](#ch2.xhtml#p23)
*   inequality constraints [2](#ch1.xhtml#p2)
*   Inertia weight [38–41](#ch3.xhtml#p38), [54](#ch3.xhtml#p54), [126](#ch6.xhtml#p126), [160](#ch8.xhtml#p160), [176](#ch8.xhtml#p176), [184](#ch9.xhtml#p184), [185](#ch9.xhtml#p185), [193](#ch9.xhtml#p193)
*   Infinity or invisible wall [45](#ch3.xhtml#p45), [82](#ch4.xhtml#p82)
*   initial learning rate [183](#ch9.xhtml#p183), [185–190](#ch9.xhtml#p185), [194](#ch9.xhtml#p194)
*   initial pheromone [73](#ch4.xhtml#p73), [160](#ch8.xhtml#p160)
*   initialization [19](#ch2.xhtml#p19), [21](#ch2.xhtml#p21), [29](#ch2.xhtml#p29), [37](#ch3.xhtml#p37), [38](#ch3.xhtml#p38), [52](#ch3.xhtml#p52), [78](#ch4.xhtml#p78), [91](#ch5.xhtml#p91), [121](#ch6.xhtml#p121), [184](#ch9.xhtml#p184), [193](#ch9.xhtml#p193), [194](#ch9.xhtml#p194)
*   input gate [179](#ch9.xhtml#p179), [180](#ch9.xhtml#p180)
*   Input search space [32](#ch2.xhtml#p32), [60–63](#ch3.xhtml#p60), [119](#ch6.xhtml#p119)
*   input weights [180](#ch9.xhtml#p180)
*   intensity [69](#ch4.xhtml#p69), [72](#ch4.xhtml#p72), [111–115](#ch6.xhtml#p111), [149](#ch7.xhtml#p149)
*   Intermittency map [92](#ch5.xhtml#p92), [102](#ch5.xhtml#p102)
*   iris dataset [159](#ch8.xhtml#p159)
*   Iterative map [93](#ch5.xhtml#p93), [102](#ch5.xhtml#p102)

## J

*   Jacobian matrix [3](#ch1.xhtml#p3), [8–12](#ch1.xhtml#p8)
*   Japanese vowels dataset [183](#ch9.xhtml#p183)

## K

*   Kappa [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158)
*   k-point crossover [23](#ch2.xhtml#p23)

## L

*   L2 regularization [185–189](#ch9.xhtml#p185), [194](#ch9.xhtml#p194)
*   Layers [45](#ch3.xhtml#p45), [57](#ch3.xhtml#p57), [157–159](#ch8.xhtml#p157), [181–183](#ch9.xhtml#p181), [185–190](#ch9.xhtml#p185), [194](#ch9.xhtml#p194)
*   learning constant [5](#ch1.xhtml#p5)
*   Levenberg Marquardt algorithm [1](#ch1.xhtml#p1), [8](#ch1.xhtml#p8), [11](#ch1.xhtml#p11)
*   Lévy distribution [27](#ch2.xhtml#p27), [90](#ch5.xhtml#p90), [115](#ch6.xhtml#p115), [139](#ch7.xhtml#p139), [145](#ch7.xhtml#p145)
*   Lévy flight mutation [27](#ch2.xhtml#p27)
*   Lévy Flights [87–89](#ch5.xhtml#p87), [91](#ch5.xhtml#p91), [94](#ch5.xhtml#p94), [111](#ch6.xhtml#p111), [114](#ch6.xhtml#p114), [115](#ch6.xhtml#p115), [146](#ch7.xhtml#p146)
*   Liebovitch map [93](#ch5.xhtml#p93), [102](#ch5.xhtml#p102)
*   light [111–115](#ch6.xhtml#p111), [163](#ch8.xhtml#p163), [164](#ch8.xhtml#p164)
*   light intensity [111–115](#ch6.xhtml#p111)
*   linear crossover [24](#ch2.xhtml#p24)
*   Linear rank selection [81](#ch4.xhtml#p81)
*   linear ranking selection [22](#ch2.xhtml#p22), [23](#ch2.xhtml#p23)
*   local decay rate [73](#ch4.xhtml#p73)
*   local minima [17](#ch1.xhtml#p17)
*   local optima [43](#ch3.xhtml#p43), [49](#ch3.xhtml#p49), [105](#ch5.xhtml#p105)
*   Local or Ring Topology [43](#ch3.xhtml#p43)
*   local pheromone decay rate [160](#ch8.xhtml#p160)
*   Local pheromone updating rule [72](#ch4.xhtml#p72), [73](#ch4.xhtml#p73)
*   Logistic map [32](#ch2.xhtml#p32), [49](#ch3.xhtml#p49), [50](#ch3.xhtml#p50), [93](#ch5.xhtml#p93), [94](#ch5.xhtml#p94), [102](#ch5.xhtml#p102), [116](#ch6.xhtml#p116), [122](#ch6.xhtml#p122), [170](#ch8.xhtml#p170), [171](#ch8.xhtml#p171)
*   long short - term memory networks [179](#ch9.xhtml#p179)
*   loss function [7](#ch1.xhtml#p7), [8](#ch1.xhtml#p8), [15](#ch1.xhtml#p15), [174](#ch8.xhtml#p174)
*   loudness [98–100](#ch5.xhtml#p98), [103–105](#ch5.xhtml#p103)

## M

*   machine learning [1](#ch1.xhtml#p1), [7](#ch1.xhtml#p7), [157](#ch8.xhtml#p157), [161](#ch8.xhtml#p161), [162](#ch8.xhtml#p162), [164](#ch8.xhtml#p164), [165](#ch8.xhtml#p165), [175](#ch8.xhtml#p175), [176](#ch8.xhtml#p176), [183](#ch9.xhtml#p183)
*   machine learning optimizers [157](#ch8.xhtml#p157)
*   matrix factorization [3](#ch1.xhtml#p3)
*   Matthews Correlation Coefficient [191](#ch9.xhtml#p191)
*   max pooling [181](#ch9.xhtml#p181), [190](#ch9.xhtml#p190)
*   maximization [1](#ch1.xhtml#p1), [2](#ch1.xhtml#p2)
*   Maximum Generation Number [41](#ch3.xhtml#p41)
*   maximum number of generations [20](#ch2.xhtml#p20), [28](#ch2.xhtml#p28), [159](#ch8.xhtml#p159), [160](#ch8.xhtml#p160)
*   Maximum runtime [28](#ch2.xhtml#p28), [41](#ch3.xhtml#p41)
*   Maximum Stall Time [28](#ch2.xhtml#p28), [41](#ch3.xhtml#p41)
*   Max-min Ant System [67](#ch4.xhtml#p67), [74](#ch4.xhtml#p74), [75](#ch4.xhtml#p75)
*   mean absolute error [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [165](#ch8.xhtml#p165), [183](#ch9.xhtml#p183)
*   mean squared error [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [165](#ch8.xhtml#p165), [166](#ch8.xhtml#p166), [182](#ch9.xhtml#p182), [183](#ch9.xhtml#p183)
*   Mesh Topology [44](#ch3.xhtml#p44)
*   Michalewicz Mutation [49](#ch3.xhtml#p49), [50](#ch3.xhtml#p50)
*   Michalewicz Non-Uniform Mutation [49](#ch3.xhtml#p49)
*   minibatch [183](#ch9.xhtml#p183), [185](#ch9.xhtml#p185)
*   minimization [1](#ch1.xhtml#p1), [2](#ch1.xhtml#p2), [33](#ch2.xhtml#p33), [59](#ch3.xhtml#p59), [60](#ch3.xhtml#p60), [120](#ch6.xhtml#p120)
*   min-max normalization [162](#ch8.xhtml#p162), [184](#ch9.xhtml#p184)
*   moderate-distance exploration [95](#ch5.xhtml#p95), [97](#ch5.xhtml#p97)
*   momentum [7](#ch1.xhtml#p7), [8](#ch1.xhtml#p8), [15](#ch1.xhtml#p15), [183](#ch9.xhtml#p183), [185](#ch9.xhtml#p185)
*   momentum parameter [8](#ch1.xhtml#p8)
*   movement [45](#ch3.xhtml#p45), [67](#ch4.xhtml#p67), [81](#ch4.xhtml#p81), [100](#ch5.xhtml#p100), [112](#ch6.xhtml#p112), [113](#ch6.xhtml#p113), [115](#ch6.xhtml#p115), [136](#ch7.xhtml#p136), [141](#ch7.xhtml#p141), [142](#ch7.xhtml#p142), [144](#ch7.xhtml#p144)
*   moving average [15–17](#ch1.xhtml#p15)
*   multilayer perceptron [158](#ch8.xhtml#p158)
*   multi-objective optimization [2](#ch1.xhtml#p2), [53](#ch3.xhtml#p53)
*   Multi-objective PSO [37](#ch3.xhtml#p37), [53](#ch3.xhtml#p53), [54](#ch3.xhtml#p54)
*   Mutation [19–21](#ch2.xhtml#p19), [25–32](#ch2.xhtml#p25), [37](#ch3.xhtml#p37), [46–50](#ch3.xhtml#p46), [55](#ch3.xhtml#p55), [82](#ch4.xhtml#p82), [87](#ch5.xhtml#p87), [96](#ch5.xhtml#p96), [101](#ch5.xhtml#p101), [103](#ch5.xhtml#p103), [105–107](#ch5.xhtml#p105), [123](#ch6.xhtml#p123), [125](#ch6.xhtml#p125), [126](#ch6.xhtml#p126), [153](#ch7.xhtml#p153), [160](#ch8.xhtml#p160), [167–173](#ch8.xhtml#p167), [184](#ch9.xhtml#p184)
*   Mutation mechanism [21](#ch2.xhtml#p21), [103](#ch5.xhtml#p103), [105](#ch5.xhtml#p105)
*   mutation operation [125](#ch6.xhtml#p125)
*   mutation operator [19](#ch2.xhtml#p19), [21](#ch2.xhtml#p21), [25–27](#ch2.xhtml#p25), [37](#ch3.xhtml#p37), [47–49](#ch3.xhtml#p47), [101](#ch5.xhtml#p101), [105–107](#ch5.xhtml#p105)
*   mutation probability [28](#ch2.xhtml#p28), [29](#ch2.xhtml#p29), [126](#ch6.xhtml#p126), [160](#ch8.xhtml#p160), [169](#ch8.xhtml#p169), [171](#ch8.xhtml#p171), [172](#ch8.xhtml#p172)

## N

*   Nearest or Boundary or Absorb [46](#ch3.xhtml#p46), [82](#ch4.xhtml#p82)
*   negative gradient [7](#ch1.xhtml#p7)
*   neural network [10](#ch1.xhtml#p10), [12](#ch1.xhtml#p12), [15](#ch1.xhtml#p15), [37](#ch3.xhtml#p37), [57](#ch3.xhtml#p57), [58](#ch3.xhtml#p58), [68](#ch4.xhtml#p68), [157–159](#ch8.xhtml#p157), [161](#ch8.xhtml#p161), [179](#ch9.xhtml#p179), [181](#ch9.xhtml#p181)
*   Non-convex [1](#ch1.xhtml#p1), [29](#ch2.xhtml#p29), [32](#ch2.xhtml#p32), [37](#ch3.xhtml#p37), [58](#ch3.xhtml#p58), [61–63](#ch3.xhtml#p61), [119](#ch6.xhtml#p119)
*   non-convex optimization [1](#ch1.xhtml#p1), [29](#ch2.xhtml#p29), [58](#ch3.xhtml#p58)
*   Non-dominated solution [54](#ch3.xhtml#p54), [55](#ch3.xhtml#p55)
*   non-gradient methods [1](#ch1.xhtml#p1), [17](#ch1.xhtml#p17)
*   normal distributions [140](#ch7.xhtml#p140), [164](#ch8.xhtml#p164), [165](#ch8.xhtml#p165)

## O

*   objective function [2](#ch1.xhtml#p2), [5](#ch1.xhtml#p5), [17](#ch1.xhtml#p17), [19](#ch2.xhtml#p19), [42](#ch3.xhtml#p42), [53](#ch3.xhtml#p53), [54](#ch3.xhtml#p54), [57](#ch3.xhtml#p57), [79](#ch4.xhtml#p79), [80](#ch4.xhtml#p80), [89](#ch5.xhtml#p89), [94](#ch5.xhtml#p94), [99](#ch5.xhtml#p99), [112–114](#ch6.xhtml#p112), [117](#ch6.xhtml#p117), [118](#ch6.xhtml#p118), [158](#ch8.xhtml#p158), [159](#ch8.xhtml#p159), [182–184](#ch9.xhtml#p182)
*   Objective space [53](#ch3.xhtml#p53)
*   offspring [20](#ch2.xhtml#p20), [21](#ch2.xhtml#p21), [23–25](#ch2.xhtml#p23)
*   Onlooker bee [77–80](#ch4.xhtml#p77)
*   Opposition-based learning [153](#ch7.xhtml#p153)
*   Optimizer [1](#ch1.xhtml#p1), [7](#ch1.xhtml#p7), [12](#ch1.xhtml#p12), [15](#ch1.xhtml#p15), [16](#ch1.xhtml#p16), [57](#ch3.xhtml#p57), [131](#ch7.xhtml#p131), [132](#ch7.xhtml#p132), [139](#ch7.xhtml#p139), [185](#ch9.xhtml#p185), [190](#ch9.xhtml#p190)
*   oscillation [8](#ch1.xhtml#p8)
*   output gate [179](#ch9.xhtml#p179), [180](#ch9.xhtml#p180)

## P

*   pack hierarchy [132](#ch7.xhtml#p132)
*   Pareto [54](#ch3.xhtml#p54), [55](#ch3.xhtml#p55)
*   Pareto dominance [55](#ch3.xhtml#p55)
*   Pareto optimal front [54](#ch3.xhtml#p54)
*   Pareto optimal set [54](#ch3.xhtml#p54)
*   Particle swarm optimization [17](#ch1.xhtml#p17), [37](#ch3.xhtml#p37), [38](#ch3.xhtml#p38), [46–50](#ch3.xhtml#p46), [58](#ch3.xhtml#p58), [90](#ch5.xhtml#p90), [150](#ch7.xhtml#p150), [154](#ch7.xhtml#p154), [157](#ch8.xhtml#p157), [161](#ch8.xhtml#p161), [166](#ch8.xhtml#p166), [184](#ch9.xhtml#p184)
*   percentage error [184–187](#ch9.xhtml#p184)
*   Periodic [46](#ch3.xhtml#p46), [82](#ch4.xhtml#p82)
*   personal learning [38](#ch3.xhtml#p38), [56](#ch3.xhtml#p56), [160](#ch8.xhtml#p160), [176](#ch8.xhtml#p176), [185](#ch9.xhtml#p185), [193](#ch9.xhtml#p193)
*   pheromone [67–75](#ch4.xhtml#p67), [160](#ch8.xhtml#p160)
*   pheromone concentration [74](#ch4.xhtml#p74)
*   pheromone evaporation [69](#ch4.xhtml#p69), [74](#ch4.xhtml#p74)
*   pheromone evaporation rate [69](#ch4.xhtml#p69)
*   pheromone trails [67](#ch4.xhtml#p67), [68](#ch4.xhtml#p68)
*   pheromone update [68](#ch4.xhtml#p68), [70](#ch4.xhtml#p70), [71](#ch4.xhtml#p71), [73–75](#ch4.xhtml#p73), [160](#ch8.xhtml#p160)
*   Piecewise map [93](#ch5.xhtml#p93), [102](#ch5.xhtml#p102)
*   pitch adjusting rate [118](#ch6.xhtml#p118), [120](#ch6.xhtml#p120), [121](#ch6.xhtml#p121)
*   pitch bandwidth [118](#ch6.xhtml#p118), [120](#ch6.xhtml#p120), [170](#ch8.xhtml#p170)
*   Polak-Ribière formula [6](#ch1.xhtml#p6)
*   pooling layers [181](#ch9.xhtml#p181), [189](#ch9.xhtml#p189), [190](#ch9.xhtml#p190)
*   Population Convergence [41](#ch3.xhtml#p41)
*   Population reduction [98](#ch5.xhtml#p98)
*   population size [21](#ch2.xhtml#p21), [32](#ch2.xhtml#p32), [42](#ch3.xhtml#p42), [54](#ch3.xhtml#p54), [60](#ch3.xhtml#p60), [96–98](#ch5.xhtml#p96), [167–169](#ch8.xhtml#p167), [171](#ch8.xhtml#p171), [172](#ch8.xhtml#p172), [176](#ch8.xhtml#p176), [184](#ch9.xhtml#p184), [193](#ch9.xhtml#p193)
*   Population-Based ACO [67](#ch4.xhtml#p67), [68](#ch4.xhtml#p68), [75](#ch4.xhtml#p75)
*   position vector [125](#ch6.xhtml#p125), [133](#ch7.xhtml#p133), [138](#ch7.xhtml#p138), [142](#ch7.xhtml#p142), [143](#ch7.xhtml#p143)
*   power distribution [27](#ch2.xhtml#p27)
*   power mutation [27](#ch2.xhtml#p27)
*   precision [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [183](#ch9.xhtml#p183), [190–193](#ch9.xhtml#p190)
*   precision-recall curve [191](#ch9.xhtml#p191)
*   prematurity potential risk [75](#ch4.xhtml#p75)
*   Prob strategy [76](#ch4.xhtml#p76)
*   probability of crossover [167](#ch8.xhtml#p167), [184](#ch9.xhtml#p184)
*   probability of mutation [167](#ch8.xhtml#p167), [168](#ch8.xhtml#p168), [184](#ch9.xhtml#p184)
*   proportionate roulette wheel selection [22](#ch2.xhtml#p22)
*   PSO Neural Network Optimization [37](#ch3.xhtml#p37), [57](#ch3.xhtml#p57), [58](#ch3.xhtml#p58)
*   PSO Topology Optimizer [57](#ch3.xhtml#p57)
*   PSO Weight Optimizer [57](#ch3.xhtml#p57)
*   pulse emission [100](#ch5.xhtml#p100), [103](#ch5.xhtml#p103), [105](#ch5.xhtml#p105)

## Q

*   Q-learning [73](#ch4.xhtml#p73)
*   quality function [74](#ch4.xhtml#p74)
*   Quality-based strategy [76](#ch4.xhtml#p76)
*   Quantum PSO [37](#ch3.xhtml#p37), [50–53](#ch3.xhtml#p50)
*   quasi-Hessian matrix [10–12](#ch1.xhtml#p10)
*   quasi-Hessian submatrix [12](#ch1.xhtml#p12)
*   Quasi-Newton [1](#ch1.xhtml#p1), [3](#ch1.xhtml#p3), [7](#ch1.xhtml#p7)

## R

*   Random [20–22](#ch2.xhtml#p20), [24–27](#ch2.xhtml#p24), [30](#ch2.xhtml#p30), [38](#ch3.xhtml#p38), [39](#ch3.xhtml#p39), [42–44](#ch3.xhtml#p42), [46–52](#ch3.xhtml#p46), [54](#ch3.xhtml#p54), [68](#ch4.xhtml#p68), [78](#ch4.xhtml#p78), [82](#ch4.xhtml#p82), [89](#ch5.xhtml#p89), [90](#ch5.xhtml#p90), [95–97](#ch5.xhtml#p95), [100](#ch5.xhtml#p100), [103](#ch5.xhtml#p103), [104](#ch5.xhtml#p104), [107](#ch5.xhtml#p107), [112](#ch6.xhtml#p112), [113](#ch6.xhtml#p113), [115](#ch6.xhtml#p115), [116](#ch6.xhtml#p116), [118](#ch6.xhtml#p118), [119](#ch6.xhtml#p119), [121](#ch6.xhtml#p121), [124–126](#ch6.xhtml#p124), [133](#ch7.xhtml#p133), [134](#ch7.xhtml#p134), [136–138](#ch7.xhtml#p136), [140–147](#ch7.xhtml#p140), [149](#ch7.xhtml#p149), [154](#ch7.xhtml#p154), [161](#ch8.xhtml#p161), [163](#ch8.xhtml#p163), [174](#ch8.xhtml#p174), [175](#ch8.xhtml#p175), [184](#ch9.xhtml#p184), [193](#ch9.xhtml#p193)
*   Random Damping [47](#ch3.xhtml#p47), [82](#ch4.xhtml#p82)
*   Random Mutation PSO [50](#ch3.xhtml#p50)
*   Random Topology [44](#ch3.xhtml#p44)
*   random walk [27](#ch2.xhtml#p27), [89](#ch5.xhtml#p89), [90](#ch5.xhtml#p90), [95](#ch5.xhtml#p95), [100](#ch5.xhtml#p100), [115](#ch6.xhtml#p115), [145](#ch7.xhtml#p145)
*   Random-Half [46](#ch3.xhtml#p46), [47](#ch3.xhtml#p47), [82](#ch4.xhtml#p82)
*   Rank-based Ant System [67](#ch4.xhtml#p67), [73](#ch4.xhtml#p73)
*   Rastrigin Function [42](#ch3.xhtml#p42), [59](#ch3.xhtml#p59), [61](#ch3.xhtml#p61), [62](#ch3.xhtml#p62)
*   real-coded genetic algorithms [24](#ch2.xhtml#p24)
*   recall [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [183](#ch9.xhtml#p183), [190–193](#ch9.xhtml#p190)
*   receiver operating characteristic [191](#ch9.xhtml#p191)
*   recurrent weights [180](#ch9.xhtml#p180)
*   Reflect Methods [47](#ch3.xhtml#p47), [82](#ch4.xhtml#p82)
*   regression [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [159](#ch8.xhtml#p159), [165](#ch8.xhtml#p165), [174](#ch8.xhtml#p174), [182](#ch9.xhtml#p182), [183](#ch9.xhtml#p183)
*   ReLU activation function [181](#ch9.xhtml#p181), [189](#ch9.xhtml#p189), [190](#ch9.xhtml#p190)
*   Repository [54](#ch3.xhtml#p54), [55](#ch3.xhtml#p55), [162](#ch8.xhtml#p162), [183](#ch9.xhtml#p183)
*   repulsion zone [152](#ch7.xhtml#p152)
*   RMSProp [1](#ch1.xhtml#p1), [15](#ch1.xhtml#p15)
*   root mean square propagation [15](#ch1.xhtml#p15)
*   root mean squared error [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [165](#ch8.xhtml#p165), [183](#ch9.xhtml#p183)

## S

*   scale parameter [14](#ch1.xhtml#p14), [139](#ch7.xhtml#p139)
*   scaled conjugate gradient [1](#ch1.xhtml#p1), [12](#ch1.xhtml#p12)
*   scaling factor [30](#ch2.xhtml#p30), [33](#ch2.xhtml#p33), [96](#ch5.xhtml#p96), [97](#ch5.xhtml#p97)
*   Schwefel Function [60](#ch3.xhtml#p60), [63](#ch3.xhtml#p63)
*   Scout bee [77–79](#ch4.xhtml#p77)
*   search space [2](#ch1.xhtml#p2), [21](#ch2.xhtml#p21), [32](#ch2.xhtml#p32), [37](#ch3.xhtml#p37), [39](#ch3.xhtml#p39), [40](#ch3.xhtml#p40), [42](#ch3.xhtml#p42), [43](#ch3.xhtml#p43), [45–47](#ch3.xhtml#p45), [52](#ch3.xhtml#p52), [54–56](#ch3.xhtml#p54), [60–63](#ch3.xhtml#p60), [67](#ch4.xhtml#p67), [68](#ch4.xhtml#p68), [72](#ch4.xhtml#p72), [76](#ch4.xhtml#p76), [80](#ch4.xhtml#p80), [82](#ch4.xhtml#p82), [90](#ch5.xhtml#p90), [94](#ch5.xhtml#p94), [100](#ch5.xhtml#p100), [101](#ch5.xhtml#p101), [119](#ch6.xhtml#p119), [133–135](#ch7.xhtml#p133), [144](#ch7.xhtml#p144), [145](#ch7.xhtml#p145), [147](#ch7.xhtml#p147), [151](#ch7.xhtml#p151), [165](#ch8.xhtml#p165), [176](#ch8.xhtml#p176), [185](#ch9.xhtml#p185)
*   seeking mode [123–125](#ch6.xhtml#p123)
*   seeking range [123](#ch6.xhtml#p123)
*   selection operators [19](#ch2.xhtml#p19), [94](#ch5.xhtml#p94), [172](#ch8.xhtml#p172)
*   Self-adaptation [97](#ch5.xhtml#p97)
*   Self-adaptive bat algorithm [87](#ch5.xhtml#p87), [101](#ch5.xhtml#p101), [103](#ch5.xhtml#p103)
*   self-adaptive cuckoo search [95](#ch5.xhtml#p95), [96](#ch5.xhtml#p96)
*   sensitivity [183](#ch9.xhtml#p183), [190](#ch9.xhtml#p190)
*   sequence input layer [185](#ch9.xhtml#p185)
*   shift parameter [139](#ch7.xhtml#p139)
*   short-distance exploration [97](#ch5.xhtml#p97)
*   Shrinking encircling method [142](#ch7.xhtml#p142)
*   simulated binary crossover [25](#ch2.xhtml#p25)
*   Sine map [93](#ch5.xhtml#p93), [102](#ch5.xhtml#p102)
*   Singer map [93](#ch5.xhtml#p93), [102](#ch5.xhtml#p102)
*   single-point crossover [23](#ch2.xhtml#p23), [24](#ch2.xhtml#p24)
*   sinus map [122](#ch6.xhtml#p122)
*   sinusoidal iterator [122](#ch6.xhtml#p122)
*   Sinusoidal map [93](#ch5.xhtml#p93), [94](#ch5.xhtml#p94), [102](#ch5.xhtml#p102)
*   social forces [149](#ch7.xhtml#p149)
*   social hierarchy [132](#ch7.xhtml#p132)
*   SoftMax activation function [181](#ch9.xhtml#p181)
*   SoftMax layer [185](#ch9.xhtml#p185)
*   Sphere Function [58](#ch3.xhtml#p58), [59](#ch3.xhtml#p59)
*   Spiral updating position [142](#ch7.xhtml#p142)
*   squared gradient [15](#ch1.xhtml#p15), [16](#ch1.xhtml#p16)
*   stability index [116](#ch6.xhtml#p116)
*   Stagnant Mutation [50](#ch3.xhtml#p50)
*   Star Topology [44](#ch3.xhtml#p44)
*   State transition rule [72](#ch4.xhtml#p72)
*   steepest descent [1](#ch1.xhtml#p1), [5–8](#ch1.xhtml#p5), [13](#ch1.xhtml#p13), [14](#ch1.xhtml#p14)
*   Step-control mechanism [103](#ch5.xhtml#p103), [105](#ch5.xhtml#p105)
*   stochastic gradient descent [1](#ch1.xhtml#p1), [7](#ch1.xhtml#p7), [8](#ch1.xhtml#p8), [15](#ch1.xhtml#p15)
*   Stopping Criteria [19](#ch2.xhtml#p19), [37](#ch3.xhtml#p37), [41](#ch3.xhtml#p41), [117](#ch6.xhtml#p117)
*   structure optimization [157](#ch8.xhtml#p157)
*   sum squared error [10](#ch1.xhtml#p10)
*   swarm particle initialization [184](#ch9.xhtml#p184), [193](#ch9.xhtml#p193)
*   swarm population [38](#ch3.xhtml#p38), [56](#ch3.xhtml#p56), [160](#ch8.xhtml#p160)
*   Swarm Topologies [37](#ch3.xhtml#p37), [42](#ch3.xhtml#p42), [43](#ch3.xhtml#p43), [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [160](#ch8.xhtml#p160), [168](#ch8.xhtml#p168), [184](#ch9.xhtml#p184), [193](#ch9.xhtml#p193)

## T

*   Taylor expansion [2](#ch1.xhtml#p2)
*   Tent map [94](#ch5.xhtml#p94), [102](#ch5.xhtml#p102), [116](#ch6.xhtml#p116), [117](#ch6.xhtml#p117), [122](#ch6.xhtml#p122)
*   termination criterion [20](#ch2.xhtml#p20), [21](#ch2.xhtml#p21), [125](#ch6.xhtml#p125), [144](#ch7.xhtml#p144)
*   three-parent crossover [25](#ch2.xhtml#p25)
*   Time factor [105](#ch5.xhtml#p105), [106](#ch5.xhtml#p106)
*   topology optimization [159](#ch8.xhtml#p159), [182](#ch9.xhtml#p182), [183](#ch9.xhtml#p183)
*   Tournament Selection [22](#ch2.xhtml#p22), [67](#ch4.xhtml#p67), [77](#ch4.xhtml#p77), [80](#ch4.xhtml#p80), [172](#ch8.xhtml#p172)
*   tracing mode [123–125](#ch6.xhtml#p123), [127](#ch6.xhtml#p127)
*   trainable filters [190](#ch9.xhtml#p190)
*   trainable layer [183](#ch9.xhtml#p183)
*   transfer functions [102](#ch5.xhtml#p102), [147](#ch7.xhtml#p147)
*   transfer learning [182](#ch9.xhtml#p182), [183](#ch9.xhtml#p183), [194](#ch9.xhtml#p194)
*   transition probability rule [72](#ch4.xhtml#p72)
*   travelling salesman problem [68](#ch4.xhtml#p68), [69](#ch4.xhtml#p69)
*   Tree or Hierarchical Topology [43](#ch3.xhtml#p43), [44](#ch3.xhtml#p44)
*   true positive [190](#ch9.xhtml#p190), [191](#ch9.xhtml#p191)
*   U
*   unconstrained optimization [1](#ch1.xhtml#p1), [77](#ch4.xhtml#p77)
*   Unemployed foragers [76](#ch4.xhtml#p76), [77](#ch4.xhtml#p77)
*   uniform crossover [24](#ch2.xhtml#p24)
*   uniform distribution [100](#ch5.xhtml#p100), [113](#ch6.xhtml#p113), [184](#ch9.xhtml#p184), [193](#ch9.xhtml#p193)
*   Unimodal [37](#ch3.xhtml#p37), [58](#ch3.xhtml#p58), [60](#ch3.xhtml#p60), [61](#ch3.xhtml#p61), [146](#ch7.xhtml#p146)
*   update rule [3](#ch1.xhtml#p3), [5](#ch1.xhtml#p5), [8](#ch1.xhtml#p8), [11](#ch1.xhtml#p11), [14](#ch1.xhtml#p14), [16](#ch1.xhtml#p16), [74](#ch4.xhtml#p74)

## V

*   velocity [37–39](#ch3.xhtml#p37), [45–47](#ch3.xhtml#p45), [50](#ch3.xhtml#p50), [54–56](#ch3.xhtml#p54), [98](#ch5.xhtml#p98), [100](#ch5.xhtml#p100), [102](#ch5.xhtml#p102), [103](#ch5.xhtml#p103), [105](#ch5.xhtml#p105), [124–127](#ch6.xhtml#p124)
*   velocity update [50](#ch3.xhtml#p50), [103](#ch5.xhtml#p103), [127](#ch6.xhtml#p127)
*   visibility [70](#ch4.xhtml#p70), [72](#ch4.xhtml#p72), [163](#ch8.xhtml#p163)
*   visibility parameter [70](#ch4.xhtml#p70)
*   Von Neumann [42–44](#ch3.xhtml#p42)

## W

*   weight optimization [157](#ch8.xhtml#p157), [158](#ch8.xhtml#p158), [183](#ch9.xhtml#p183)
*   weight vector [8](#ch1.xhtml#p8), [13](#ch1.xhtml#p13), [14](#ch1.xhtml#p14), [57](#ch3.xhtml#p57), [158](#ch8.xhtml#p158), [183](#ch9.xhtml#p183)
*   weighting factor [74](#ch4.xhtml#p74)
*   Whale Optimization Algorithm [131](#ch7.xhtml#p131), [141](#ch7.xhtml#p141), [143–148](#ch7.xhtml#p143)
*   wind advection [149](#ch7.xhtml#p149)

* * *

1.  [¹](#ch8.xhtml#R_fn1) Website: [https://archive.ics.uci.edu](https://archive.ics.uci.edu)[↩](#fnref1)
2.  [¹](#ch9.xhtml#R_fn2) [https://archive.ics.uci.edu/ml/datasets/Japanese+Vowels](https://archive.ics.uci.edu)[↩](#fnref2)