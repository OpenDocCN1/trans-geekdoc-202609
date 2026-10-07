
## 12.1 Additional reading

The original works by Sepp Hochreiter and Yoshua Bengio are good to read.
So, this is Sepp's paper in 1991. It's completely in German. If you understand and can read German, then this could be a good read for you.

### Additional Reading:

Untersuchungen zu dynamischen neuronalen Netzen

By Sepp (Josef) Hochreiter (1991)

Link:
http://people.idsia.ch/~juergen/SeppHochreiter1991ThesisAdvisorSchmiduber.pdf

There's Yoshua Bengio's paper which is called Learning Long Term Dependencies with Gradient Descent is Difficult, 1994.

### Additional Reading:

Learning Long-Term Dependencies with Gradient Descent is Difficult

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_383_0.png)

By Yoshua Bengio et al. (1994)

Link:
http://www-dsi.ing.unifi.it/~paolo/ps/tnn-94-gradient.pdf

We also recommend looking into this paper called On The Difficulty Of Training Recurrent Neural Networks by Razvan Pascanu.

### Additional Reading:

On the difficulty of training recurrent neural networks

By Razvan Pascanu et al. (2013)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_383_1.png)

Link:
http://www.jmlr.org/proceedings/papers/v28/pascanu13.pdf

## Chapter 12 : Part 2

## Deep Learning

## RNN: LSTM - Long Short-Term Memory

long short-term memory Introduction

### 1.2.1 LSTM

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_384_0.png)

- We've got vanishing gradient problem. As a result of thumb, if $W_{rec}$ is small, then we have Vanishing Gradient; if $W_{rec}$ is large, then we have Exploding Gradient. To solve this problem there are couple of solutions. But here we only focus on LSTM.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_384_1.png)

- The first thing that comes to mind is to make $W_{rec}$ equal one, $W_{rec}=1$, and that's exactly what was done in the LSTMs.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_384_2.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_384_3.png)

Here we've got a recurrent neural network. With unraveled temporal loop.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_385_0.png)

This is what it looks like if you dig inside the RNN. The images are taken from Christopher Olah.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_385_1.png)

Here is his blog Very well-written blog with amazing images.

### Understanding LSTM Networks
Posted on August 27, 2015

Traditional neural networks can't do this, and it seems like a major shortcoming. For example, imagine you are trying to predict the next word in a sentence. A traditional neural network could have no reasoning about previous events in the past.

Recurrent neural networks address this issue. They are networks with loops, allowing information to persist.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_385_2.png)

All recurrent neural networks have the form of a chain of repeating modules of neural network. In standard RNN, this module will have a very simple structure, like a single layer.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_385_3.png)

The repeating module in a standard RNN contains a single layer. LSTM is a more complex type of recurrent neural network with four interacting layers instead of a single layer, these four interact in a very special way.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_385_4.png)

The repeating module in an LSTM contains four interacting layers. Don't worry about the details of what goes on. We will walk through the LSTM diagram later.

### 2.2.2 RNN vs LSTM-RNN

In following images the first one represents the Simple RNN and 2nd image represents "RNN with LSTM". Here LSTM is a special kind of network applied to RNN.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_386_0.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_386_1.png)

Above is a simple representation of LSTM. Following is detailed representation. Image: arxiv.org/pdf/1503.04069.pdf

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_386_2.png)

### 2.2.3 How LSTM works

So we've got the inside-look of our simple-RNN. And this is the problem. This operation that happens here is neural-network-layer. In simple RNN: outputs coming into this module and operation applied then goes into next module's applied. When back propagate, it goes through all of those operation, that's where weights are applied (that's where $W_{rec}$ is sitting). Through this back propagation, the gradient vanishes, which means that weights cannot be updated properly or fast enough to train the network. This is the standard RNN.

Now Following is LSTM version.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_387_0.png)

Notice the main point here was setting $W_{rec}=1$. Well that's this line flows here (the upper line), at top of LSTM version of RNN.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_387_1.png)

There's not much going on, just two pointwise operations (removal & addition) and no Complex Network Layer Operations in this line.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_387_2.png)

Actually LSTMs have this pipeline as memory cell or call it memory pipeline. This pipeline flows through time, sometimes it faces pointwise operations to remove/add. But mostly it flows through freely and therefore when you back propagate through these LSTMs, you don't face vanishing gradient. However, all complex-operations are brought to this part (image on the Right).

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_387_3.png)

### 12.2.4 LSTM operations

Now's focus on just one time-step or a single module/block of LSTM. In following representation we have:

## Long Short-Term Memory

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_388_0.png)

The VARIABLES in this Diagram:

- $C_t$ stands for memory or memory-cell.
- $C_t$ represents the memory-cell for current LSTM-module/block.
- $C_{t-1}$ is the memory-cell coming from previous LSTM-block.
- $h_t$ is output. Here we can see $h_t$ and $h_{t-1}$
- One $h_t$ (goes up) goes out into the world, and- another $h_t$ (on the Right) goes to the next LSTM-module/block.
- $h_{t-1}$ represents the output from the previous module.
- $X_t$ represents the input for current LSTM-block
- So an LSTM module takes three inputs: input data $X_t$, previous modules output-data $h_{t-1}$, memory-cell $C_{t-1}$
- And it produces two outputs: current memory-cell $C_t$ and output-data $h_t$ (one copy of $h_t$ goes to next LSTM-module).
- All variables are vectors: The important thing is that everything is a vector. i.e. $C_t$, $h_t$, and $X_t$ are all vectors.
 Each of them doesn't represent single value, they are actually vectors containing multiple values.

The LEGENDS in this Diagram: And let's go through the legend.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_388_1.png)

Copy: In this drawn LSTM-module, if see there is one line splitting into two (or more).

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_389_0.png)

It means the memories go straight ahead and just copy it when the line splits.

Pointwise operations: We've got a couple of pointwise operations here (pointwise operations are used in this diagram).

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_389_1.png)

Valves: The X's valves and they all have names. There are three kind of valves.

Forget valve, F.
Memory valve, V.
Output valve, O.

Forget valve is basically controlled by the layer operation σ represents sigmoid function because is from 0 to 1. 0 stands for close, 1 stands for open. Based on the decision made by the layer operation forget will close/open.

If it's open, memory flows freely through memory-pipeline.

If it's close then memory is cut off. Therefore it is not transferred further.

Memory valve, which is also controlled by layer operation σ represents sigmoid activation. The value of Tanh - layer operation, is added (somewhat added) or not-added to the memory-pipeline based on the decision of the memory-valve V.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_389_2.png)

T-shaped joint: And then we've got T-shaped joint, which connects the memory coming from memory-valve to the memory-pipeline. Here additional memories get added if the memory-valve is opened.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_389_4.png)

Tangent operation: Tangent operation, with values between minus one and one. It's another pointwise operation (layer operation).

The neural network layer operations: Above we talked about pointwise operations. (Pointwise is like element by element vector, if you multiply a vector by zero, you multiply every element by zero. Or multiply a vector by certain amount is multiply each element of the vector with that amount).

But the things going on inside these NN-layer operations are bit more complex than pointwise operations.
