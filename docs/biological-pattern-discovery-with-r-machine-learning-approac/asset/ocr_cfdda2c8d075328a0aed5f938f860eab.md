# Optimised Peptide Pattern Discovery 383

$$c = \theta_2\mu\theta_1\rho$\quad (8.4)$

Figure 8.19 shows a new RPN chromosome for the RPN chromosome shown in the upper panel of Figure 8.13. Figure 8.20 shows the resulting tree.

# 8.3.2.6 The training of a GP model

A GP training process is implemented in an iterated process. To start a GP learning process, a pool of randomised RPN chromosomes are generated. Within each iteration of a learning process, the first job is to measure the fitness of each RPN chromosome to a given data set. The fitness measurement is composed of two parts. They are the model accuracy and the length of an RPN chromosome. in terms of their fitness measurements to a data set. The latter is used to award more parsimonious RPN chromosomes.

Suppose a problem is a regression question. The target variable or the dependent variable of a regression model is denoted by $y$ and the output of a model described by an RPN chromosome is denoted by $\hat{y}$. The sum of the squared errors between them is defined as below, where $N$ is the total number of the observed target values, $y_i$ and $\hat{y}_i$ stand for the $i^{th}$ observed target value and the $i^{th}$ predicted value from a model defined by an RPN chromosome,

$$\varepsilon = \frac{1}{N}\sum_{i=1}^{N}(\hat{y}_i - y_i)^2$\quad (8.5)$

Suppose the length of an RPN chromosome is denoted by $\ell_m$. The fitness measurement is defined as below, where $m$ is the $m^{th}$ model described by an RPN chromosome, $0 < \alpha < 1$ for the trade-off constant, $\varepsilon_m$ stands for the sum of the squared errors for the $m^{th}$ RPN chromosome,

$$\varepsilon_m = \alpha\times\varepsilon_m + (1 - \alpha)\times\ell_m$\quad (8.6)$

The two terms of the above fitness measurements need to be as small as possible. The best model is determined by the following equation,