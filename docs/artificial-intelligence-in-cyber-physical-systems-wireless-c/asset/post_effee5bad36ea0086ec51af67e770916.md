
![](img/56cfba5af06305175d6488aec4d55ab0_257_0.png)

FIGURE 13.2 Resultant permutations after applying the composition in two different ways.

### 13.3.1 PERMUTATION GROUP

A set of permutations P is said to be a group if it contains any two permutations α and β; and a binary composition operation * such that α*β is again a permutation which is an element of P. The permutation group also satisfies the conditions of identity, and inverse elements as well as associativity [12]. There exist an identity element e ∈ P, and inverse element α⁻¹ ∈ P for each permutation group.

The permutation group satisfies three conditions of the group. If permutation group P consists of more than two permutations, it is a non-abelian group, i.e., α*β ≠ β*α for all α, β ∈ P. The permutation group P is a finite group if it contains a finite number of elements, i.e., it consists of n! permutations for a set N of n elements (customers). The permutation group P is also a symmetric group because each permutation is the bijection of itself. A subset ⟨P⟩ of P exists, which is a group under the composition operator (*) and ⟨P⟩ is known as the generating set if all elements of P can be generated using the elements of ⟨P⟩ and their inverses. The group P and the generating set ⟨P⟩ can be characterized by a connected directed graph known as the Cayley graph. The Cayley graph Γ = ⟨⟨P⟩, P⟩ is a directed graph with the following properties.

- Every element α ∈ P is a node in the graph.
- Every ρ ∈ ⟨P⟩ is assigned a color c_ρ.
- For each α ∈ P and ρ ∈ ⟨P⟩, there exists a directed edge of color c_ρ to the node α*ρ ∈ P.

### 13.3.2 ABSTRACT ALGEBRAIC OPERATIONS

In numerical evolutionary algorithms like PSO and DE, the operations are applied on vectors to generate a new vector representing the new solution for the problem under consideration. The numerical evolutionary algorithms require decoding methods to convert the continuous-value vector into permutation, representing the solution. For combinatorial permutation spaces, it is necessary to define addition, subtraction, and scalar multiplication operators such that the resultant solution remains a permutation. For combinatorial permutation space, it has been proved in the research works [12–15] that the abstract addition (⊕), abstract subtraction (⊖), and abstract scalar multiplication (⊙) can be defined in terms of composition operator (*) such that these operations hold the same properties analogous to the numerical operations in Euclidean vector space.

As proved in [12], the algebraic abstract addition (⊕) and subtraction (⊖) operators are independent of the generators and generating set given as

γ = α ⊕ β = α * β      ∀α, β ∈ P      (13.10)
γ = α ⊖ β = β⁻¹ * α      ∀α, β ∈ P      (13.11)

The β⁻¹ represents the inverse permutation which is defined as

β⁻¹ = (k_i, k_j, k_l …)  s.t., β(k_i) < β(k_j) < β(k_l)  ∀k_i are indices of β      (13.12)

It is to be noted that abstract addition and subtraction operators are both non-commutative due to the non-commutative property of composition operator (*), i.e., α ⊕ β ≠ β ⊕ α, and α ⊖ β ≠ β ⊖ α.

To define the abstract scalar multiplication, it is required to choose a generating set forming the symmetric permutation group P. The set consisting of all permutations that swap the elements of adjacent positions is known as the set of all simple transpositions ⟨P_ST⟩. The generating set ⟨P_ST⟩ consists of n−1 elements, and its search space diameter is (n choose 2). In this work, the generating set of all simple transpositions ⟨P_ST⟩ has been chosen due to its simple search space structure, i.e., the composition of α ∈ P and ρ_i ∈ ⟨P_ST⟩ results in the swapping of elements at indices i and i+1 in α. The successive application of this simple property is helpful to transforming permutation ρ_i ∈ ⟨P_ST⟩ into the desired permutation.

The analogy for abstract scalar multiplication is similar to scalar numerical multiplication in Euclidean vector space. The multiplication of a scalar φ with permutation α ∈ P changes the length of permutation α as per the value of scalar φ. For given φ ≥ 0 and α ∈ P, the abstract scalar multiplication (φ ⊙ α) fulfills the following three conditions to simulate the scalar numerical multiplication in Euclidean vector space [12].

C1: α ⊙ φ = α^{|φ|};   C2: α ⊙ φ ≤ α      ∀φ ∈ [0,1];   C3: α ⊙ φ ≥ α      ∀φ > 1

There may be more than one permutation in P due to applications of C1–C3 and non-unique minimal decompositions of each permutation. The diameter also restricts the value of scalar φ, i.e., the scalar value must be a fraction of diameter. Due to the above restrictions, abstract scalar multiplication can be realized in many different ways. To implement the abstract scalar operation (⊙) on permutations, the following four cases are considered based on properties C1–C3.

α ⊙ φ = e if φ = 0      (13.13)
α ⊙ φ = α if φ = 1      (13.14)
α ⊙ φ ≤ α if 0 < φ < 1      (13.15)
α ⊙ φ ≥ α if φ > 1      (13.16)

Equations (13.13–13.16) follow the analogy of scalar numerical multiplication in Euclidean vector space. The abstract scalar multiplication can be computed using eqs. (13.13 and 13.14) and stochastic bubble sort algorithm [12–15].

### 13.4 THE PROPOSED ALGORITHM

PSO algorithm is encouraged by the collective swarms’ intelligence, and it is capable of solving complex optimization problems [16]. Every particle is characterized by position and velocity, which are continuous-valued vectors. The following equations are employed to update the kth particle’s position and velocity.

$v_k^{t+1} = \omega * v_k^t + c_1 * \mathrm{rand}[0,1] * (zb_k - z_k^t) + c_2 * \mathrm{rand}[0,1] * (zb^t - z_k^t)$  (13.17)

$\bar{z}_k^{t+1} = z_k^t + v_k^{t+1}$  (13.18)

where $v_k^t$ and $v_k^{t+1}$ are kth particles’ velocities in iteration $t$ and $t+1$, respectively; $z_k^t$ and $z_k^{t+1}$ are the kth particles’ positions in iteration $t$ and $t+1$, respectively; and $zb^t$ and $zb_k$ are the position of the best particle at iteration $t$ and the best position of the kth particle so far, respectively. The $\mathrm{rand}[0,1]$ characterizes a random number in $[0,1]$, and $c_1$ and $c_2$ correspond to the learning factors, while $\omega$ denotes the inertia weight.

The goal of the PSO is to find out a vector $z_k^t = [z_1 z_2 z_3 \dots z_y]$ that optimizes the fitness function $f(z_k^t)$ of the problem under consideration. The dimensions of the position vector depend on the dimensions of the problem. In PSO, position and velocity vectors consist of continuous values for discrete and continuous optimization problems. For CVRP, the position vectors must convert into permutations using RK, angle modulation, or other methods.

### 13.4.1 INITIAL POPULATION AND FITNESS VALUE

For APS, the population of size $\eta$ is initialized with random permutations of given customers in the CVRP. Figure 13.3a shows the random particle (permutation) consisting of nine customers.

The particle $\alpha$ can be decomposed into routes using the cluster-first and route-second method. This method assigns customers to the first vehicle in the same order as they appear in the particle until the capacity is exhausted. Next, the remaining particles’ remaining customers are allocated to the next vehicle until the second vehicles’ capacity is exhausted. This method is employed to decide routes for all customers.

![](img/56cfba5af06305175d6488aec4d55ab0_259_0.png)

FIGURE 13.3 (a) A particle (permutation) for CVRP with nine customers. (b) Routes.

$I_2^{t+1} = c_1 \times \mathrm{rand}(0,1) \odot (ZB_k \ominus Z_k^t)$  (13.20)

$I_3^{t+1} = c_2 \times \mathrm{rand}(0,1) \odot (ZB^t \ominus Z_k^t)$  (13.21)

Now, the velocity of $k$th particle for iteration $t+1$ is computed as follows:

$V_k^{t+1} = I_1^{t+1} \oplus I_2^{t+1} \oplus I_3^{t+1}$  (13.22)

To compute the velocity, the highest precedence is given to abstract scalar multiplication ($\odot$), and the abstract addition ($\oplus$) and abstract subtraction ($\ominus$) have the same priority. For these three operators, associativity is considered from left to right.

The position of the $k$th particle for iteration $t+1$ is computed as follows:

$Z_k^{t+1} = Z_k^t \oplus V_k^{t+1}$  (13.23)

Similarly, the remaining particles of the population for iteration $t+1$ are computed. Next, the fitness value of each particle is calculated using eq. (13.2) and cluster-first and route-second approach as discussed in Section 13.4.1.

Simulated annealing improves the convergence speed and avoids trapping in the local optimum, based on local search operators, i.e., 2-opt*, exchange, and relocate operators [24–26]. In the beginning, SA requires the best particle $ZB^{t+1}$ of the population at $t+1$ iteration and then searches the neighborhoods of the given best particle. Initially, the temperature's value $\tau$ is initialized to a constant value. Next, the neighborhood particles (solutions) are searched by the stochastic application of 2-opt*, exchange, and relocate operators. An operator is selected randomly, and a neighborhood solution is generated. The better-quality neighborhood solution is accepted; otherwise, the worst solution with some probability value based on Boltzmann’s constant is accepted. It is obtained as follows:

$\mathrm{Prob}_A = \begin{cases} 1 & \Delta C \le 0 \\ e^{-\Delta C / \tau} & \Delta C > 0 \end{cases}$  (13.24)

$\tau = \tau^* (1 - \phi)$  (13.25)

where the $\Delta C$ represents the change in objective values and $\phi$ is the rate of temperature change.

All steps of the loop are repeated for a fixed iteration. At last, the APS algorithm returns the global best particle. Every particle saves its own best positions and adjusts the velocity considering its own best performance and best performing particle. The particles are using their personal best, socially best particle followed by the application of SA to search the neighborhood of the given particle. Eventually, the swarm will converge to near-optimal positions with good convergence speed.

### 13.5 SIMULATION STUDY

To compare the performance, the proposed APS and classical RK-PSO algorithms have been implemented in Python 3.9.6 on DESKTOP-L9O54PJ, Intel(R) Core™
