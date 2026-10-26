
## Dynamic Declaration: Problems

- Dynamic declaration sacrifices efficiency for flexibility
- Graph construction overhead grows linearly with # of samples
- Only single-instance computation can be performed – no batching!
- Hard to incorporate graph-level optimization

```
/* (b) dynamic declaration */
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  for k = 1 → K:
    declare a data flow graph 𝒟_i^t for x_i^t.
    single-instance computation: 𝒟_i^t(x_i^t).
```

## Problem #1: Graph Construction and Optimization

```
/* (a) static declaration */
// all samples must share one graph
declare a static data flow graph 𝒟.
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  batched computation: 𝒟({x_i^t}_{i=1}^K).
```

```
/* (b) dynamic declaration */
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  for k = 1 → K:
    declare a data flow graph 𝒟_i^t for x_i^t.
    single-instance computation: 𝒟_i^t(x_i^t).
```

- Graph construction literally takes 80% of time in TensorFlow Fold
- Curve (left axis): absolute time; bar (right): percentage time

![](img/cb490ed30bca4eda5fbba81c52a2c173_226_0.png)

## Problem #2: Batching will be Very Hard

```
/* (a) static declaration */
// all samples must share one graph
declare a static data flow graph 𝒟.
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  batched computation: 𝒟({x_i^t}_{i=1}^K).
```

In static declaration: batching is natural

```
/* (b) dynamic declaration */
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  for k = 1 → K:
    declare a data flow graph 𝒟_i^t for x_i^t.
    single-instance computation: 𝒟_i^t(x_i^t).
```

In dynamic declaration: batching is difficult

- Manual batching of dynamic graphs?
- Users have to write code to do batching by themselves
  - In fact, until 2017, the famous tree-LSTM (a typical dynamic NN) model is trained with batchsize=1
- And it is not always available!

![](img/cb490ed30bca4eda5fbba81c52a2c173_228_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_228_1.png)

## Problem #3: Unavailable to Graph Optimizations

- Graph optimization itself has a overhead (growing with the size of the graph)
- In static declaration, we optimize the graph only once, and apply for all input data points – graph optimization overhead is constant, and the gain is mostly positive
- In dynamic declaration, if we want to incorporate these optimization, we need to optimize for each declared graph
- Therefore, linear graph optimization overhead
- As a result: the optimization overhead might cost more than gained

```
/* (b) dynamic declaration */
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  for k = 1 → K:
    declare a data flow graph 𝒟_i^t for x_i^t.
    single-instance computation: 𝒟_i^t(x_i^t).
```

Graph optimization happens here: inside the loops!

## Introducing Cavs: Design Goals

- Simple Interface, rich expressiveness
  - Keep the flexibility of symbolic programming and dynamic declaration
- At the same time, address the three aforementioned problems:
  - Minimize graph construction overhead
  - Allow for efficient computation and batching
  - (Re-)open the opportunities for graph optimization techniques

## Cavs: Motivation

- Observation: Most dynamic NNs has *recurrent/recursive* structures
  - The dynamics come from the sample-dependent structure
  - Not the "neural network" itself

![](img/cb490ed30bca4eda5fbba81c52a2c173_232_0.png)

## Think Like a Vertex

- “Think like a vertex”
  - Originally from the graph computing community
- Key idea: *express “global” through “local”*
  - User implements a vertex function, specifying how a node will interact with its neighboring nodes
  - The system will compile the local vertex function and figure out the overall computing pattern over the whole graph

## Cavs: A Vertex-centric Representation

- The key idea: separate out static ML model declaration from the data-dependent dynamics of input samples

Dynamics come from here

Computation specified here

![](img/cb490ed30bca4eda5fbba81c52a2c173_235_0.png)

## Cavs: Four APIs

- *Gather & Scatter* for internal data path
- *Pull & Push* for external data path

![](img/cb490ed30bca4eda5fbba81c52a2c173_236_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_237_0.png)

- An example: expressing Tree-LSTM using the four APIs

```
def F():
    S = gather()               # gather states of child vertices
    for k in range(N):
        c_k, h_k = split(S[k], 2)  # get hidden states c and h
    x = pull({0})              # pull the first external input x

    # specify the computation
    h = ∑_{k=0}^{N-1} h_k
    i = sigmoid(W^{(i)} × x + U^{(i)} × h + b^{(i)})
    for k in range(N):
        f_k = sigmoid(W^{(f)} × x + U^{(f)} × h_k + b^{(f)})
    o = sigmoid(W^{(o)} × x + U^{(o)} × h + b^{(o)})
    u = tanh(W^{(u)} × x + U^{(u)} × h + b^{(u)})
    c = i ⊗ u + ∑_{k=0}^{N-1} f_k ⊗ c_k
    h = o ⊗ tanh(c)

    scatter(concat([c, h], 1))  # scatter c, h to parent vertices
    push(h)                     # push to external connectors
```

## Expressing Backpropagation

![](img/cb490ed30bca4eda5fbba81c52a2c173_238_0.png)

- It transforms the forward-backward computation on batch of dataflow graphs as
  - Forward: schedule the execution of the vertex function F through a batch of input graphs
  - Backward: schedule the execution of ∂F through the same batch of input graphs, in a reverse order

```
/* (c) our proposed vertex-centric model */
declare a symbolic vertex function ℱ.
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  read their associated graphs {𝒢_i^t}_{i=1}^K.
  compute ℱ over {𝒢_i^t}_{i=1}^K with inputs {x_i^t}_{i=1}^K.
```

## Cavs Bypass Graph Construction Overhead

![](img/cb490ed30bca4eda5fbba81c52a2c173_239_0.png)

- No repeated graph construction overhead!
- The graph construction overhead is constant – we only need to construct F, which is usually a small-scale dataflow graph
- Bypass the repeated dataflow graph construction
- Instead, read the input graph G, which could be achieved by an I/O function

```
/* (c) our proposed vertex-centric model */
declare a symbolic vertex function ℱ.
for t = 1 → T:
  read the tth data batch {x_i^t}_{i=1}^K.
  read their associated graphs {𝒢_i^t}_{i=1}^K.
  compute ℱ over {𝒢_i^t}_{i=1}^K with inputs {x_i^t}_{i=1}^K.
```

Declare only once → constant graph construction cost

Read through I/O, no graph construction involved any more.

## Empirical Results: Graph Construction Cost

- Cavs has constant graph construction time
- Curve (left axis): absolute time; bar (right): percentage time
- Cavs outperforms TensorFlow-Fold by a large margin

![](img/cb490ed30bca4eda5fbba81c52a2c173_240_0.png)

## Cavs Enables Batched Computation

![](img/cb490ed30bca4eda5fbba81c52a2c173_241_0.png)

- Batched computation is key to deep learning
- Recall the Dynamic Declaration problem #2
- Batched computation on dynamic graphs are difficult:
  - Difficult to find batching opportunities
    - need to analyze the graph
    - need to manually write code to do extra processing
  - Given batching opportunities, difficult to re-order memory contents
    - For the batched computation to be efficient, their input/output need to coalesce on memory
    - How to efficiently re-arrange memory layout to guarantee continuity?

![](img/cb490ed30bca4eda5fbba81c52a2c173_242_0.png)

- Batched computation is natural and automatic in Cavs
  - Cavs transforms the backpropagation as **evaluating F on nodes of a batch of input graphs**, see the figure below.
- Then, batched computation can be realized by
  - Figure out a set of vertices that we are ready to evaluate F on
  - Batch the evaluation of F on this set of vertices
  - Pass the output of F to their parent vertices

