# **Algorithm 14.3:**

**Input**: The data set contains two categories of samples $(x_i, y_i, x_i \in R^n, y_i \in \{+1, -1\})$ represents class markup

**Output**: $W$

+   (1) Initialises edge detection by the edge detection operator:
$e = \{e_{i,j} | i, j \in L\}$ represents the response intensity obtained by the edge detection operator based on the grey image $Z$. Based on the differential algorithm, edge detection depends only on the grey information.

$$ S_{i,j} = \begin{cases} 1, & \text{if } p\left(z_{i,j} | x_{i,j} = 1\right) \geq p\left(z_{i,j} | x_{i,j} = 0\right) \\ 0, & \text{if } p\left(z_{i,j} | x_{i,j} = 1\right) < p\left(z_{i,j} | x_{i,j} = 0\right) \end{cases} $$

+   (2) Estimate the model parameters by the Boltzmann machine:
With the results of the initial edge detection as learning samples, according to the Boltzmann machine learning rule, estimate parameters $\alpha_k$ such that $P(s)$ is maximum. The problem of parameter estimation is transformed into a global optimisation problem.

+   (3) Search algorithm of edge relaxation based on a Boltzmann machine:
Owing to the adoption of a 24-neighbourhood system, when the edge fault distance is greater than a 5*5 neighbourhood, the search algorithm is difficult to deal with; a larger neighbourhood system can be adopted, but it will increase the algorithm complexity.

The limitation of the algorithm is that the learning samples of the learning algorithm are initial edge detection results. Although they have some fault tolerance, it is difficult to carry out the algorithm when there is excessive noise. The learning algorithm can obtain the main local edge features, but it has some limitations. The image effect is better only with some regularity on the edges (i.e., when some local edge features are more obvious), and it is more suitable for texture image edge detection. The improved scheme uses standard learning samples for parameter estimation and is applicable to non-learning samples, but the learning samples and non-learning samples must be of the same type of image.

# ### 14.1.4 Fuzzy edge detection algorithm based on the qualification function

The procedure of the traditional image edge detection fuzzy algorithm, referred to as the Pal–King algorithm [5], is as follows: (1) The membership function is used to map the image $f(x, y)$ into fuzzy membership matrix $G(i, j)$. (2) Multiple nonlinear transformations $T_r$ are performed on degree matrix $G(i, j)$ to enhance the edge information and weaken the non-edge information. (3) Perform reverse changes to the fuzzy membership matrix $G(i, j)$ to obtain enhanced images. (4) Extract the edge with ‘Min’ or ‘Max’.

However, this algorithm has many shortcomings. Therefore, improvements are required. We introduce the qualification function on the basis of the original image, com-