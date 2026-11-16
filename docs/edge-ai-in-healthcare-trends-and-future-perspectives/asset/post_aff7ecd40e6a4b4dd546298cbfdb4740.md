
### TABLE 12.2 Solution format

| Images | F¹ | F² | F³ | F⁴ | ... | F²² |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| l₁ | 0 | 0 | 1 | 0 | ... | 1 |
| l₂ | 1 | 0 | 0 | 1 | ... | 0 |
| ... | ... | ... | ... | ... | ... | ... |
| lₗ | 0 | 1 | 0 | 1 | ... | 0 |

this scheme, every single solution is called a “Lion”. The initial solution format is shown in Table 12.2.

Among the N number of solutions, some of the solutions are randomly generated, as nomad lions. The remaining population is randomly divided into P prides. Every solution in this algorithm is a specific gender, which remained constant during the optimisation process. Over the searching process, every lion marks its best-visited position. According to these marked positions, every pride’s territory is formed. So, for each pride, marked positions (“best-visited positions”) by its members form that pride’s territory.

### Step 2: Fitness calculation.

After solution initialisation, the fitness of each lion is calculated. The classification accuracy is regarded as the fitness function. The fitness function is given in Eqn. 12.3.

```
Fitness = Max (Accuracy) (12.3)
```

```
Accuracy = (Tᴾ + Tᴺ) / (Tᴾ + Tᴺ + Fᴾ + Fᴺ) × 100 (12.4)
```

### Step 3: Hunting process.

For the hunting process, the hunters are divided randomly into three sub-branches. The group with highest fitness is considered to be the middle and the other groups are considered as the right and left wings. Throughout hunting, if a hunter improves its own fitness, **PREY** (P) will escape from hunter and new position of **PREY** (P’) is obtained as follows:

```
P' = P + rand(0,1) × PI × (P - H) (12.5)
```

Where;
P→ current position of prey,
H→ position of hunter who attack to prey and PI is the percentage of improvement in the fitness of hunter.

The new position of the hunter which are having a place in both left and right wings,

```
\( H' = \left\{ \begin{array}{ll} rand(H, P), & H < P \\ rand(P, H), & H > P \end{array} \right. \) (12.6)
```

where (H,P) indicates the random value

The new position of the female lion is calculated as follows:

```
\( P_F^i = P_F + 2d \times rand(0,1)\{SP_1\} + U(-1,1) \times tan(\theta) \times D_d \times \{SP_2\} \) (12.7)
```

```
\(\{SP_1\} \cdot \{SP_2\} = 0, \| \| \{SP_2\} \| \| = 1 \) (12.8)
```

- \( P_F \rightarrow \) Position of female lion,
- \( D_d \rightarrow \) Distance between the female lion and the point chosen by tournament selection among the pride territory,
- \(\{SP_1\} \rightarrow \) Previous location of female lion and its direction is towards the selected point,
- \(\{SP_2\} \rightarrow \) Perpendicular to \(\{SP_1\}\).

### Step 4: Roaming operation.

Roaming is a solid local search and helps the lion optimisation algorithm to search for a solution to enhance it. The lion pushes towards the chosen region of region by ’n’ units, where ’n’ is a random number with uniform distribution.

```
\( n \sim U_d(0, 2 \times D) \) (12.9)
```

'D' indicates the distance between male lion position and the selected area of territory.

Also, nomad lions move haphazardly in search of space. The new position of nomad lions is produced as follows:

```
\( L_{ij} = \left\{ \begin{array}{ll} L_{ij} \text{ if } rand_j > prob_i \\ RAND_j \text{ otherwise} \end{array} \right. \) (12.10)
```

Where \( L_{ij} \) is the current position of the nomad lions and \( rand_j \) is the uniform random number between [0, 1].

\( rand(j) \) is the random generated vector and \( prob_i \) is the probability value.

The probability value is calculated for every nomad lion independently as described in 12.11:

```
\( prob_i = 0.1 + min \left( 0.5, \frac{(N_{O_i} - Bst_{N_{O_i}})}{Bst_{N_{O_i}}} \right) i = 1, 2, ... M \) (12.11)
```

where
\( N_{O_i} \) and \( Bst_{N_O} \) represents the minimum delay of the current position of the \( i^{th} \) lion of the nomads
M represents the number of lion nomads

### Step 5: Mating operation.

Mating is the vital operation that guarantees the lions’ survival. The mating operator is a direct blend of guardians for delivering two new offspring. The new cubs are created subsequently to choosing the female and male lions involved in mating,

```
\(\text{Offspring}_{1} = \chi \times F_j + \sum_{i=1}^{N_R} \frac{1-\chi}{SU_i} \times M_j \times SU_i \quad \text{(12.12)}\)
```

```
\(\text{Offspring}_{2} = (1-\chi) \times F_j + \sum_{i=1}^{N_R} \frac{\chi}{N_R} \times M_j \times SU_i \quad \text{(12.13)}\)
```

Here, ‘j’ is the dimension. If male of ‘i’ is selected for mating, then \(SU_i=1\), otherwise \(SU_i=0\).

\(N_R\) represents the resident males in a pride, \(\chi\) is a random number with a uniform distribution with mean value is 0.5, and standard deviation is 0.1.

By mating, the lion algorithm shares the data between genders, while the new cubs acquire characters from the two parents.

### Step 6: Updating using PSO.

To enhance the performance of the lion optimisation algorithm, the position of each lion is further updated, using the PSO algorithm. The position of each lion is updated in the search space using 12.14.

```
\(LP_i^{New} = LP_i + V_i^{New} \quad \text{(12.14)}\)
```

```
\(V_i^{new} = V_i + \phi_1.r_1.(pbest_i - LP_i) + \phi_2.r_2.(gbest_i - LP_i) \quad \text{(12.15)}\)
```

- where
- \(\phi_1, \phi_2\) = learning rate,
- \(r_1, r_2\) = random numbers in the range of [0, 1],
- \(V_i\) = current velocity, and
- \(LP_i\) = current position.

The overall flow diagram of the proposed MLO algorithm is shown in Figure 12.2.

### Step 7: Termination criterion.

In the long run, the best solution is selected. The maximum fitness value is considered to be the best solution. The corresponding feature of the selected solution is given to the input of the DNN classifier to classify an image as either normal or abnormal.

## 12.3.4 DEEP-NEURAL-NETWORK-BASED HEART DISEASE PREDICTION

After the feature selection process, the selected features are given to the DNN classifier to classify data as either normal or abnormal. The DNN classifier is a typical structure that follows an ANN, which is a complex network model. But it can represent hierarchies in a simple form to create the model. Having ‘n’ hidden layers, it processes the elements of data from the previous layer, that is the input layer. After each epoch, with the help of the learning rate “alpha”, the error of the input will be reduced gradually by weight adjustment of each node. This continued by back-propagation of the network when there is an error followed by fine-tuning until better results are achieved. Input can have any number of input nodes and there is no limit because the increase in input nodes will increase the learning process. As there are output nodes in the output layer, the number of outputs can be known individually. The step-by-step process of the deep neural network classifier is as follows:

- Step 1: Read the number of ‘n’ input nodes (F1, F2, F3 ... Fn) for the input layer. The number of input nodes is the same as the number of selected features.
- Step 2: Assign the number of layers in the hidden layer that need to be trained with data. The input layer and the hidden layer connected with the help of the weighted value which is represented as Wij^H . Similarly, the weight between hidden layer and output layer is represented as Wij^o .
- Step 3: Initialise the bias and learning rate values for each node and the weighting will be selected arbitrarily in forward-propagation.
- Step 4: Define the number of epochs to make values of the back-propagation from the output to the input direction.
- Step 5: In the first hidden layer, the weighted values of input are provided to the summing function with the bias of the neuron as in Equation 12.16.

```
C_{H_1}(i=1,2..,K) = \left( \sum_{m=1}^{M} W_{ij}^h R_m \right) + b_x \quad (12.16)
```

- Step 6: The activation function is applied to the output of the first hidden layer as:

```
F \left( C_{H_1}(i) \right) = \frac{1}{\left( 1 + e^{-C_{H_1}(i)} \right)} \quad (12.17)
```

where F(*) is the sigmoid activation function.

- Step 7: Similarly, the operation of n^th hidden layer output is calculated as follows:

```
C_{H_n}(i) = \left( \sum_{z=1}^{K} W_{ij}^o F \left( C_{H_{n-1}}(z) \right) \right) + b_p \quad (12.18)
```
