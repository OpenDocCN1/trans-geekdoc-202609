
Consider the \(k^{th}\) input vector \(\mathbf{x}_k\) and output vector \(\hat{y}(k)\). The hyper-plane function is:

\(\begin{aligned} y^i(k) &= f_i(\mathbf{x}_k, \Theta_i) \\ &= a_0^i + a_1^i x_1(k) + \cdots + a_n^i x_n(k) \\ &= \begin{bmatrix} 1 & \mathbf{x}_k \end{bmatrix} \Theta_i^T, \quad i=1, \cdots, c \end{aligned} \tag{4}\)

where \(\Theta_i\) is the row vector of parameters for the \(i^{th}\) fuzzy rule consequent part.

The fitness function of the FCRM clustering algorithm is defined as:

\(J_m = f(\Theta_i) = \sum_{i=1}^c \sum_{k=1}^N (u_{ik})^m E_{ik}^2(\Theta_i) \tag{5}\)

where, \(E_{ik}(\Theta_i) = |f_i(\mathbf{x}_k, \Theta_i) - y(k)| = |\begin{bmatrix} 1 & \mathbf{x}_k \end{bmatrix} [\Theta_i]^T - y(k)|\) is the distance (measure of error) between \(f_i(\mathbf{x}_k, \Theta_i)\), and the modeling output \(y(k)\). The membership function \(u_{ik}\) and consequent parameters \(a_j^i\), shown in (6) and (7), cannot be trained toward the direction that minimizes the fitness function; therefore, an improved FCRM algorithm [29] is adopted in this paper. Based on the modified FCRM algorithm, the membership function \(u_{ik}\) and the consequent parameters \(a_j^i\) can refresh and vary towards the direction that minimizes the fitness function.

\(u_{ik} = \left( \sum_{s=1}^c \left( \frac{E_{ik}(\Theta_i)}{E_{sk}(\Theta_s)} \right)^{\frac{-2}{m-1}} \right)^{-1}, \quad 1 \le i \le c, \quad 1 \le k \le N \tag{6}\)

\(a_j^i = \frac{\sum_{k=1}^n (u_{ik})^m (y^i(k) - \sum_{p \ne j} a_p^i \hat{x}_p(k)) \hat{x}_p(k)}{\sum_{k=1}^n (u_{ik})^m}, \quad 0 \le j \le n \tag{7}\)

where \([\hat{x}_0(k), \hat{x}_1(k), \dots, \hat{x}_n(k)] = \begin{bmatrix} 1 & \mathbf{x}_k \end{bmatrix} = [1, x_1(k), \dots, x_n(k)]\).

## C. A MODIFIED CLUSTER VALIDITY CRITERION

In the process of system identification, the number of clusters is always decided by the user. The number of rules will affect the number of parameters and the effectiveness of the cluster. Therefore, different approaches [12], [30], [31] have been proposed for searching for an appropriate cluster number. However, most of the methods are more suitable for hyper-spherical-shaped clustering algorithms. Since the FCRM is a hyper-plane-shaped algorithm, a modified cluster validity criterion [32] is adopted in this paper to search for the appropriate rule number. The cluster validity criterion is defined by the compactness-to-separation ratio, the numerator reflects the compactness of the hyperplane-shaped clusters, and the denominator indicates the separation of the hyperplane-shaped clusters. The optimal rule number \(c\) is obtained when \(F_{NEW}\) reaches its minimum.

\(F_{NEW} \equiv \frac{\sum_{i=1}^c \sum_{k=1}^N (u_{ik})^m E_{ik}^2(\Theta_i)}{N \min_{\substack{i=1, \dots, c \\ j=1, \dots, c \\ i \ne j}} \frac{a_{ij} + k_2}{<|\mathbf{u}_i, \mathbf{u}_j>| + k_1}} \tag{8}\)

where \(a_{ij} = \frac{|a_0^j - a_0^i|}{\Delta a_{max}}\), for \(i, j = 1, \dots, c, i \ne j\), \(\Delta a_{max} = \max_{i=1, \dots, c \\ j=1, \dots, c} |a_0^i - a_0^j|\), \(a_{ij} \in [0, 1]\) is normalized, \(\mathbf{u}_i = \mathbf{n}_i / \|\mathbf{n}_i\|\), \(<,>\) represents the inner product, \(\mathbf{n}_i = [a_1^i \cdots a_n^i - 1]^T\), \(k_1, k_2\) are small real positive constants to avoid the function from being zero or infinity.

## D. IMPROVED ANT COLONY OPTIMIZATION ALGORITHM

Ant colony optimization (ACO) [33]-[35] is a metaheuristic approach that is widely utilized to find an approximation solution for optimization problems. The ACO was inspired by observations of the foraging behavior of real ants. Similar to the behavior of ants seeking a path between their colony and a source of food, the ACO algorithm was first aimed at searching for an optimal path in a graph. Based on the ACO algorithm, the optimization problem can be transformed into the problem of finding the best path on a weighted graph. The ants (hereafter, ants) incrementally build solutions by moving on the graph. The solution construction process is stochastic and depends on the pheromone model, whose values are modified at runtime by the ants. The combination of fuzzy logic and ACO have been widely applied to solving the combinatorial optimization problem, such as the traveling salesman problem (TSP) [36], vehicle routing problem [37], railroad-blocking problem [38], optimal reconfiguration for distribution systems [39], fuzzy controller design [40], and so on. The ACO algorithm shows the advantage of solving the optimization problem; however, for continuous cases, the solution for the optimization problem is not as clear and straightforward. Some studies have adopted the concept of the ACO to find a solution to the optimization problem for continuous domain, but they often do not follow its steps exactly. From an examination of the fuzzy identification problem, many unknown parameters need to be found and the interval for each parameter is unknown. In addition, a lot of iterations are needed to obtain the optimal solution; therefore, few studies have explored the fuzzy identification problem using the combination of fuzzy logic and the ACO algorithm. Therefore, in this study, an improved ACO [41] is adopted to obtain the sifted initial membership function and consequent parameter matrices to establish a T-S fuzzy model with fewer iterations. The improved ACO algorithm is briefly described as follows.

- 1) Initialize the solutions in the pheromone table, shown in Fig. 1, and substitute the solutions into the fitness function (5).

- 2) Sort the solutions by fitness function and calculate the weight of each solution by (9).

\(\bar{\omega}_v = \frac{1}{\zeta T \sqrt{2\pi}} e^{-\frac{(v-1)^2}{2\zeta^2 T^2}} \tag{9}\)

where \(v\) is \(v^{th}\) solution, \(\zeta T\) is standard deviation, \(T\) is population size, and \(\zeta\) is a parameter of ACO. When \(\zeta\) is small, the best-ranked solutions are strongly preferred; otherwise, the probability becomes more uniform.

![](img/7a2a4261fbc1474308250e4dcaab8af5_3_0.png)

- 3) The probability \(P_v\) is calculated by (10) and select the solution by probability formula (10) with the roulette method.

\(\begin{array}{ c }
P_v = \frac{\bar{\omega}_v}{\sum_{t=1}^T \bar{\omega}_t} \\
(10)
\end{array}\)

- 4) Set the selected solution in Step 3 as mean \(\mu^i\), and calculate the standard deviation \(\sigma_v^i\) by the following equation.

\(\begin{array}{ c }
\sigma_v^i = \xi \sum_{\epsilon=1}^T \frac{|S_\epsilon^i - S_v^i|}{T - 1} \\
(11)
\end{array}\)

where \(\xi\) is the evaporation rate of pheromone, \(\sigma_v^i = \zeta T\), \(S_\epsilon^i\) is the \(i^{th}\) variable of \(\epsilon^{th}\) solution in Fig. 1, and \(S_v^i\) is the \(i^{th}\) variable of \(v^{th}\) solution in Fig. 1.

- 5) If the condition \(|f^{(l+1)}(\mu^i) - f^{(l+1)}(S_i)| < 0\) is satisfied, then set \(S_i = \mu^i\); otherwise, keep the original \(S_i\).

- 6) If the terminal condition \(|f^{(l+1)}(S_i) - f^{(l)}(S_i)| < \delta\) with \(\delta > 0\) is satisfied, then stop the algorithm; otherwise, go back to Step 2.

## III. PROPOSED IDENTIFICATION METHOD

The proposed identification method, which combines a modified cluster validity criterion index and ACO and OLS algorithms, is introduced in this section. The purpose of the proposed fuzzy identification is to establish the T-S fuzzy model with the minimal error variance between the established model and the original nonlinear model. The following steps are followed:

### Identification of the premise parameters

- 1) Determination of the number of fuzzy rules.
- 2) Identification of the membership function parameters.

### Identification of the consequent parameters

- 1) Establishment of the consequent structure for each local model.
- 2) Optimization of the initial consequent parameters.
- 3) Identification of the consequent parameters.

## A. PROPOSED IDENTIFICATION ALGORITHM

In general, the initial value and the number of rules are set randomly before the cluster algorithm is applied to identify the parameters of the established model. However, since the initial premise structure, consequent parameters, and number of rules might lead to an inappropriate premise structure and identification results, this study develops an algorithm that utilizes the ACO algorithm to find a better initial value and adopts a modified cluster validity criterion index to determine the appropriate rule number. In addition, by utilizing improved FCRM and OLS algorithms, the final premise structure and consequent parameters are obtained. The proposed identification algorithm is described below in detail.

- Step 1: Set the number of clusters \(c = 2\) and \(c_{max}\), and find the appropriate number of clusters using (8). Set the parameters in the ACO algorithm and initialize the solution \(S_i, i = 1, ..., T\) and substitute \(S_i\) into fitness function (5) with \(\Theta_i = S_i\).

- Step 2: Sort the solution by fitness function, and then arrange these solutions in ascending order. According to (9) and (10), we can obtain the probability value for renewing solutions as \(S_i (i = 1, ..., T)\).

- Step 3: Calculate the mean \(\mu^i\) using the probability value obtained by Step 2 and the roulette method, and set standard deviation \(\sigma_v^i\) using (11). If the condition \(|f^{(l+1)}(\mu^i) - f^{(l+1)}(S_i)| < 0\) is satisfied, then set \(S_i = \mu^i\); otherwise, keep the original \(S_i\).

- Step 4: If the condition \(|f^{(l+1)}(S_i) - f^{(l)}(S_i)| < \delta\) is satisfied, then define \(S_i \equiv \Theta_i\); otherwise set \(l = l + 1\) and return to Step 2.

- Step 5: Search for the minimum fitness value using (5) until the condition \(\|\mathbf{U}^{(l+1)} - \mathbf{U}^{(l)}\| < \varepsilon\) is satisfied, where \(\mathbf{U}^{(l)} = \begin{bmatrix} u_{11}^{(l)} & \cdots & u_{1N}^{(l)} \\ \vdots & \ddots & \vdots \\ u_{c1}^{(l)} & \cdots & u_{cN}^{(l)} \end{bmatrix}\) .

The center of the bell-shaped membership function \(\alpha_q^i\) and the standard deviation of the bell-shaped membership function \(\beta_q^i\) can be obtained by the following formulas:

\(\begin{array}{ c }
\alpha_q^i = \frac{\sum_{k=1}^n u_{ik}x_q}{\sum_{k=1}^n u_{ik}} \\
(12)
\end{array}\)

\(\begin{array}{ c }
\beta_q^i = \sqrt{\frac{2 \sum_{k=1}^n u_{ik} \left( x_q - \alpha_q^i \right)^2}{\sum_{k=1}^n u_{ik}}} \\
(13)
\end{array}\)

The grade of the membership function \(A_q^i(x_q(k))\) can be obtained by (3), and weight \(w_i(k)\) and output \(\hat{y}\) can be obtained as \(w_i(k) = \prod_{q=1}^n A_q^i(x_q(k))\), and \(\hat{y}(k) = \frac{\sum_{i=1}^c w_i(k)\hat{y}^i}{\sum_{i=1}^c w_i(k)}\) .

- Step 6: Substitute the input-output data and \(\hat{y}(k)\) obtained from Step 5 into (14).

\(\begin{array}{ c }
\mathbf{y} = \bar{\Phi}\hat{\Theta}^T + \mathbf{e} \\
(14)
\end{array}\)

where \(\mathbf{e} = \mathbf{y} - \hat{\mathbf{y}}\), real model \(\mathbf{y} = [y(1) \ ... \ y(N)]^T\), the established model \(\hat{\mathbf{y}} = [\hat{y}(1) \ ... \ \hat{y}(N)]^T\), \(\bar{\Phi}\) is shown in the
