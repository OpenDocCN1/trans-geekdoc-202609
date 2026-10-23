
## 15 Neural networks for sequences

### 15.1 Introduction

In this chapter, we discuss various kinds of neural networks for sequences. We will consider the case where the input is a sequence, the output is a sequence, or both are sequences. Such models have many applications, such as machine translation, speech recognition, text classification, image captioning, etc.

### 15.2 Recurrent neural networks (RNNs)

A recurrent neural network or RNN is a neural network which maps from an input space of sequences to an output space of sequences in a stateful way. That is, the prediction of output y_t depends not only on the input x_t, but also on the hidden state of the system, h_t, which gets updated over time, as the sequence is processed. Such models can be used for sequence generation, sequence classification, and sequence translation, as we explain below.

#### 15.2.1 Vec2Seq (sequence generation)

In this section, we discuss how to learn functions of the form f_θ : ℝ^D → ℝ^{N×C}, where D is the size of the input vector, and the output is an arbitrary-length sequence of vectors, each of size C. We call these vec2seq models, since they map a vector to a sequence.

The output sequence y_{1:T} is generated one token at a time. At each step we sample ŷ_t from the hidden state h_t of the model, and then “feed it back in” to the model to get the new state h_{t+1} (which also depends on the input x). See Fig. 15.1 for an illustration. In this way the model defines a conditional generative model of the form p(y_{1:T}|x), which captures dependencies between the output tokens. We explain this in more detail below, but first we give some example applications.

##### 15.2.1.1 Applications

RNNs can be used to generate sequences unconditionally (by setting x = ∅) or conditionally on x. Unconditional sequence generation is often called language modeling; this refers to learning joint probability distributions over sequences of discrete tokens, i.e., models of the form p(y_1, ..., y_T). (See also Sec. 3.8.1.2, where we discuss using Markov chains for language modeling.) Fig. 15.2 shows some samples from a character-level RNN that was trained on Shakespeare. We see that the generated sequence looks plausible, even though it is not very meaningful. RNNs give state-of-the-art performance on this task [CNB17]. We can also make the generated sequence depend on some kind of input vector x. For example, consider the task of image captioning: in this case, x is some embedding of the image computed by a CNN, as illustrated in Fig. 15.3. (In this example, D = H × W × 3 is the size of the image and C is the size of the vocabulary.) See e.g., [Hos+18] for a review of image captioning methods.

It is also possible to use RNNs to generate sequences of real-valued feature vectors, such as pen strokes for hand-written characters [Gra13] and hand-drawn shapes [HE18]. This can also be useful for time series forecasting real-value sequences.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_500_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_500_1.png)

##### 15.2.1.2 Models

p(y_{1:T}|x) = \sum_{h_{1:T}} p(h_{1:T}|x) p(y_1|h_1) \prod_{t=2}^T p(y_t|h_t) p(h_t | h_{t-1}, y_{t-1}, x) \quad (15.1)

> 1. In the language modeling community, performance is usually measured by perplexity. This is explained in Sec. 6.1.5, but it suffices to know that low perplexity means high log likelihood.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_501_0.png)

Figure 15.3: Illustration of a CNN-RNN model for image captioning. The pink boxes labeled "LSTM" refer to a specific kind of RNN that we discuss in Sec. 15.2.6.2. The pink boxes labeled W_emb refer to embedding matrices for the (sampled) one-hot tokens, so that the input to the model is a real-valued vector. From https://bit.ly/2FKnqHm. Used with kind permission of YunJey Choi.

where **h**_t is the hidden state. The output distribution is usually given by

p(**y**_t|**h**_t) = Cat(**y**_t|S(**W**_{hy}**h**_t + **b**_y))  (15.2)

where **W**_{hy} are the hidden-to-output weights, and **b**_y is the bias term. However, for real-valued outputs, we can use

p(**y**_t|**h**_t) = N(**y**_t|**W**_{hy}**h**_t + **b**_y, σ²**I**)  (15.3)

We assume the hidden state is computed deterministically as follows:

p(**h**_t|**h**_{t-1}, **y**_{t-1}, **x**) = 𝕀(**h**_t = f(**h**_{t-1}, **y**_{t-1}, **x**))  (15.4)

for some deterministic function f. The update function f is usually given by

**h**_t = φ(**W**_{xh}[**x**; **y**_{t-1}] + **W**_{hh}**h**_{t-1} + **b**_h)  (15.5)

where **W**_{hh} are the hidden-to-hidden weights, **W**_{xh} are the input-to-hidden weights, and **b**_h are the bias terms. See Fig. 15.1 for an illustration.

Note that **y**_t depends on **h**_t, which depends on **y**_{t-1}, which depends on **h**_{t-1}, and so on. Thus **y**_t implicitly depends on all past observations (as well as the optional fixed input **x**). Thus an RNN overcomes the limitations of standard Markov models, in that they can have unbounded memory. This makes RNNs theoretically as powerful as a Turing machine [SS95; PMB19]. In practice, however, the memory length is determined by the size of the latent state and the strength of the parameters; see Sec. 15.2.6 for further discussion of this point.

When we generate from an RNN, we sample from \tilde **y**_t ~ p(**y**_t|**h**_t), and then “feed in” the sampled value into the hidden state, to deterministically compute **h**_{t+1} = f(**h**_t, \tilde **y**_t, **x**), from which we sample \tilde **y**_{t+1} ~ p(**y**_{t+1}|**h**_{t+1}), etc. Thus the only stochasticity in the system comes from the noise in the observation (output) model, which is fed back to the system in each step. (However, there is a variant, known as a variational RNN [Chu+15], that adds stochasticity to the dynamics of **h**_t independent of the observation noise.)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_502_0.png)

##### 15.2.1.3 Teacher forcing

The likelihood of a training sequence is given by

p(y_{1:T}|x) = p(y_1) \prod_{t=2}^T p(y_t | y_{1:t-1}, x)   (15.6)

Note that we condition on the ground truth labels from the past, y_{1:t-1}, not labels generated from the model. This is called teacher forcing, since the teacher's values are “force fed” into the model as input at each step. (In the context of robotics, teacher forcing is called behavioral cloning.)

Unfortunately, teacher forcing (which is equivalent to MLE training) can sometimes result in models that perform poorly at test time. The reason is that the model has only ever been trained on inputs that are “correct”, so it may not know what to do if, at test time, it encounters an input y_{t-1} generated from the previous step that deviates from what it saw in training.

A common solution to this is known as scheduled sampling [Ben+15a]. This starts off using teacher forcing, but at random time steps, feeds in samples from the model instead; the fraction of time this happens is gradually increased.

An alternative solution is to use other kinds of models where MLE training works better, such as 1d CNNs (Sec. 15.3) and transformers (Sec. 15.5).

#### 15.2.2 Seq2Vec (sequence classification)

In this section, we assume we have a single fixed-length output vector y we want to predict, given a variable length sequence as input. Thus we want to learn a function of the form f_θ : R^{T D} → R^C. We call this a seq2vec model. We will focus on the case where the output is a class label, y ∈ {1,…,C}, for notational simplicity.

The simplest approach is to use the final state of the RNN as input to the classifier:

p(y|x_{1:T}) = Cat(y|S(W h_T))   (15.7)

See Fig. 15.4a for an illustration.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_503_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_503_1.png)

Figure 15.5: (a) RNN for transforming a sequence to another, aligned sequence. (b) Bi-directional RNN for the same task.

We can often get better results if we let the hidden states of the RNN depend on the past and future context. To do this, we create two RNNs, one which recursively computes hidden states in the forwards direction, and one which recursively computes hidden states in the backwards direction. This is called a bidirectional RNN [SP97].

More precisely, the model is defined as follows:

h→_t = φ(W→_xh x_t + W→_hh h→_{t-1} + b→_h) (15.8)

h←_t = φ(W←_xh x_t + W←_hh h←_{t+1} + b←_h) (15.9)

We can then define h_t = [h→_t, h←_t] to be the representation of the state at time t, taking into account past and future information. Finally we average pool over these hidden states to get the final classifier:

p(y|x_{1:T}) = Cat( y|W S ( 1/T ∑_{t=1}^T h_t ) ) (15.10)

See Fig. 15.4b for an illustration. (This is similar to the 1d CNN text classifier in Sec. 15.3.1.)

#### 15.2.3 Seq2Seq (sequence translation)

In this section, we consider learning functions of the form f_θ : ℝ^{T D} → ℝ^{T' C}. We consider two cases: one in which T' = T, so the input and output sequences have the same length (and hence are aligned), and one in which T' ≠ T, so the input and output sequences have different lengths. This is called a seq2seq problem.

##### 15.2.3.1 Aligned case

In this section, we consider the case where the input and output sequences are aligned. We can also think of it as dense sequence labeling, since we predict one label per location. It is straightforward to modify an RNN to solve this task, as shown in Fig. 15.5a. This corresponds to

p(y_{1:T}|x_{1:T}) = ∑_{h_{1:T}} 𝕀(h_1 = f(x_1)) p(y_1|h_1) ∏_{t=2}^T 𝕀(h_t = f(h_{t-1}, x_t)) p(y_t|h_t) (15.11)
