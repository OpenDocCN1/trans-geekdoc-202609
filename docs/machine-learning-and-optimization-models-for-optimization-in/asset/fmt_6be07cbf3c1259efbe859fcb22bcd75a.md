
# 5.5 Whale Optimization Algorithm (WOA)

WOA was proposed by Jalili and Lewis for optimizing numerical problems (Mir Jalili & Lewis, 2016). It is a meta-heuristic algorithm that functions like humpback whales. The foraging behavior is known as bubble-net feeding. The prey are small fishes close to the surface. The foraging is done by creating distinctive bubbles along a circle. The whole process is done in three stages: Coral loop (encircling prey), lobtail (bubble-net attacking method (exploitation phase)) and capture loop (search for prey (exploration phase)).

![Image 42](index-103_1.jpg)

**Figure 5.6** Proposed model for the hybrid algorithm.

## 5.5.1 Mathematical Model

### 5.5.1.1 Stage 1: Encircling Prey

The first stage is to recognize the location of prey and mark them. The current best search agent is considered to be the target prey. After deciding the current best solution, the other solutions will try to update their position towards the current best solution. This process is formulated as:

```
D = C × X*(t) - X(t)
X(t+1) = X*(t) - A × D
```

where

- `t` indicates the current iteration.
- `X*` is the position vector of the best solution obtained so far at iteration `t`.
- `X` is the position vector of each agent.

The coefficient vectors `A` and `C` are calculated as:

```
A = 2a × r - a
C = 2r
```

where

- `a` is linearly decreased from 2 to 0 over the course of the iteration.
- `r` is a random vector number [0,1].

### 5.5.1.2 Stage 2: Bubble-Net Attacking (Exploitation Phase)

The exploitation phase is a combination of two approaches.

#### a) Shrinking Encircling Mechanism

This mechanism is achieved by decreasing the value of `a`; the fluctuation range of `A` is also decreased by `a`. We can say, `A` is a random value in the interval `[-a, a]` where `a` is decreased from 2 to 0 over the process of iterations.

#### b) Spiral Updating Position

In this step an equation is created between the position of whale and the target to create a helix-shaped movement; the equation is as follows:

```
D' = X*(t) - X(t)
X(t+1) = D' × e^(bl) × cos(2πl) + X*(t)
```

where

- `D'` is the distance between the whale and target.
- `b` is a constant that defines the logarithmic shape.
- `l` is random in [-1,1].

A humpback whale moves along a spiral-shaped path while shrinking the circle at the same time. If we assume there are 50-50 chances to choose between shrinking encircling or spiral model movement during an iteration, then:

```
X(t+1) = X*(t) - A·D          if p < 0.5
X(t+1) = D' × e^(bl) × cos(2πl) + X*(t)  if p ≥ 0.5
```

where `p` is a random number in [0,1].

### 5.5.1.3 Stage 3: Capture Loop (Search for Prey (Exploration Phase))

In the bubble-net method the target is not defined; hence the prey is searched randomly. The variation of `A` can be used, where `|A| > 1`, that forces the search agent to move far away from the reference location (whale). The position of the search agent will update according to the random chosen solution, instead of the best solution so far.

This can be formulated as:

```
D = C × X_rand - X
X(t+1) = X_rand - A·D
```

Where `X_rand` is a random position vector.

## WOA Algorithm (Pseudo Code)

In the beginning there is a set of random solutions. In each iteration the search agent updates its position according to either the best solution or a randomly chosen agent. To explore and exploit the parameter `a` is decreased from 2 to 0.

If `|A| > 1`, choose a random agent, and if `|A| < 1`, choose the best solution so far to update the position of search agents.

**Pseudo code**:

```
Input: data, max_iteration, population
Initialize whales population Xi (i = 1,2,3……..n)
Initialize A, C, l, a and p
Calculate the fitness of each search agent
X* = best agent at the beginning
While (It < max_iteration)
    for each search_agent
        if (p < 0.5)
            if (|A| < 1)
                update search agent with X(t+1) = X*(t) - A×D
            else if (|A| >= 1)
                select random search agent (X_rand)
                update the current search agent with X(t+1) = X_rand - A×D
            end
        else if (p >= 0.5)
            update the position of current search agent with X(t+1) = D' × e^(bl) × cos(2πl) + X*(t)
        Calculate fitness of each search agent
        Update X* if better agent found
    It = It+1
    Update A, C, l, a and p
end while
return X*
```

We are going to propose an improvised whale optimization with ANN to achieve higher accuracy and minimum response time (Figure 5.7).

**Figure 5.7** Proposed model architecture WOA and ANN.

WOA takes the VM list and fitness function as input with other parameters. Then it generates an optimal solution for each iteration. This list is passed to the ANN algorithm for learning purposes, and a test dataset will be passed into ANN for further prediction. Hence it will increase the accuracy and efficiency as well.

## Table 5.2 Related Work Analysis with Cloud- and ANN-Based Approaches

| Authors | Approach | Result/Conclusion |
| :--- | :--- | :--- |
| [1] Reshmi, R. and Saravanan | Gaussian-based adaptive least mean square filter (DoG–ALMS) | This approach improved the overall resource optimization of the network |
| [2] Akki, P. and Vijayarajan, V. | Optimized neural network/convolutional neural network with improvised BAT algorithm | Proposed approach is more power efficient in comparison with traditional BAT |
| [3] Jeddi, S. and Sharifian, S. | Proposed a model to predict highly fluctuating workloads based on wavelet transform and GMDH method | Better CPU scaling and resizing |
| [4] Chudasama, V. and Bhavsar | A bi-directional LSTM-based approach, predictor algorithm | This model was closer to the actual demand for resources than the other models. It is capable of optimizing the SLA violation |
| [5] AbdElminaam, D.S. and Toony | A double chain quantum technology integrated into a genetic algorithm | This optimization model improved the resource optimization accuracy |
| [6] Chen, S. and Fang, S | ANN-based approach for real-time scheduling | It optimized the response time for the real time scheduling |
| [7] Hasan, M. and Almamun, M. | Novel self-adaptive resource allocation architecture | The model is QoS satisfactory as well as energy efficient |
| [8] Kholidy, H.A. | Swarm intelligence-based prediction approach (SIBPA) | Achieved higher accuracy with good response and throughput time for better scaling decision |
| [9] Lang, K. and Zhao | Cloud computing resource method based on an improved ANN model | Predicated reasonable resource scheduling accuracy |
| [10] Saravanan, S. and Anbalagan | Integrated deep reinforcement learning and lion | Proper resource allocation |
