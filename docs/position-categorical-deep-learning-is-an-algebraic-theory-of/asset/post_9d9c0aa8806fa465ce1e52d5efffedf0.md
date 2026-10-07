
# Categorical Deep Learning

We can run the analogous calculation with weight sharing. We consider the linear endofunction $w \in \mathbb{R}^{Z_2 \to \mathbb{R}^{Z_2}$ on a pair of pixels (represented as a matrix $W = \begin{bmatrix} w_1 & w_3 \\ w_2 & w_4 \end{bmatrix}$), and the group of translations $(\mathbb{Z}_2,+0)$ on the domain, this time we identify the endomorphism of the codomain. If $w$ is invariant to $\blacktriangleright$, see Example H.3 for any $[x_1, x_2] \in \mathbb{R}^2$ it has to hold

```
$\begin{bmatrix} x_1x_2+w_2x_1 \\ w_3x_2+w_4x_1 \end{bmatrix} = \begin{bmatrix} w_1x_1+w_2x_2 \\ w_3x_1+w_4x_2 \end{bmatrix} \quad (12)$
```

implying $w_1 = w_2$ and $w_3 = w_4$, the equivariance induced a particular tying scheme

```
$\begin{bmatrix} w_1 \\ w_3 \\ w_3 \end{bmatrix}$
```

in which the matrix has shared rows. Note this implies that each of the pixels in the output of $fw$ will be the same, and this layer could also be represented as a single product with $[w_1, w_3]$, eliminating the grid structure in the original set. A layer would not be an endofunction on $\mathbb{R}^{Z_2}$, however, was our initial focus of exploration.

# H.2. Examples from Automata Theory

## H.2.1. Streams

**Example H.4** (Streams). Let $O$ be a set, thought of as the set of outputs. Consider the endofunctor $O \times : Set \to Set$. Then the set $Stream(O)$ of $O^{\omega}$ with outputs $O$, together with the map $(output, next) : Stream(O) \to O \times Stream(O)$ forms a coalgebra of $O$. They have a representation the following datatype

```
data Stream o = MkStream {
  output :: o
  next :: Stream o
}
```

This datatype describes streams cohesively, and from which we can always extract one, and another stream. In Example I.3 we will use this how it is related to recurrent neural networks.

**Example H.5** (Streams to means coalgebra). Consider the endofunctor $(O \times -)$ from Example H.4, and a coalgebra homomorphism from any other $(O \times -)$-coalgebra $X, (o, n)$ into $(Stream(O), (output, next))$:

![](img/92dd63b8e10fefd3f3f227bf65a30b83_25_0.png)

Then the map $f_{o,n} : X \to Stream(O)$ is usually to a stream, comes from functional programming how a stream of values can be obtained from a single value. It is implemented by corecursion on the input:

```
$f_{o,n} : x \to Stream \ o\nff_{o,n} x = MkStream (o \ x) (f_{o,n} (n \ x))$
```

This recursion is structural in nature, meaning it satisfies the following two equations which arise from unpacking the algebra homomorphism equations elementwise:

```
$o(x) = output(f_{o,n}(x)) \quad (13)$
f_{o,n}(n(x)) = next(f_{o,n}(x)) \quad (14)$
```

> 15 An infinite sequence of outputs

# Categorical Learning

Here Equation (13) tells us that the output produced by $f_{o,n}$ at $x$ is $o(x)$, and Equation (14) tells us that the stream is produced by $f_{o,n}$ at $x$ is $f_{o,n}(x)$.

**Remark H.6.** Analogous to Remark 2.13, there can only be one *unfold* of this type. This is because streams are a terminal object in the category of $(O \times -)$-codgebras.

We can study the weight sharing between streams. Consider the category and coremonad $\mathcal{R} \times -$ given by the output set $(\mathcal{R}, o, n)$, and represent the coalgebra map with scalars $w_o$ and $w_n$, denoting the output and the next state, Then the universal coalgebra homomorphism is a linear map $f_{o,n}: \mathcal{R} \to \text{Stream}(\mathcal{R})$ satisfying Equations (13) and (14). If we represent this as an infinite-dimensional

```
$w_1 \quad w_2 \quad w_3 \quad w_4 \quad \dots$
```

then the induced weight sharing removes degrees of freedom: the matrix is completely determined by $w_o$ and $w_n$, and is of the form:

```
$[w_o \quad w_n \quad w_n^2 \quad w_n^3 \quad w_n^4 \dots]$
```

## H.2.2. Moore Machines.

**Example H.7** (Moore machines). Let $O$ and $I$ be sets, thought of as outputs and inputs, respectively. Consider the endofunctor $O \times (I \to -) : Set \to Set$. Then the $Moore_{O,I}$ of Moore Machines with $O$-labeled outputs and $I$-labeled inputs with the map $(output, next): Moore_{O,I} : O \times (I \to O)$ forms a coalgebra for this endofunctor. It can be represented by the following datatype:

```
data Moore o = MkStream {
  output :: o,
  next :: i -> Moore o
}
```

Like Mealy, this is deconstruction. From a Moore machine we can always extract an output and a function which an input produces another. In Example 5 we will see how this will be related to recurrent neural networks of a particular form.

**Example H.8** (Unfolds to Moore machines are terminal $(O \times -)$-codgebras). Consider the endofunctor $O \times (I \to -)$ from Example H.7, and any other $(O \times -), (output, next): Moore_{O,I}$:

![](img/92dd63b8e10fefd3f3f227bf65a30b83_26.png)

Then the map $f_{o,n}$ is necessarily an unfold to a Moore machine, describing how a Moore machine is obtained from a single value. It is a recursive function as follows:

```
$f_m : x \to Moore \ o \nf_m \ x = MkStream (1 \ x) (\lambda i \to f_m (i))$
```

which is natural in nature, it satisfies the following two equations which arise by unpacking the coalgebra equations elementwise:

```
$o(x) = output(f_{o
```

Here Equation (15) tells us that the output of the Moore machine produced by $f_{o,n}$ at $x$ is given by the output of $n$ at $x$, and Equation (16) tells us that $i$ is the one produced by $f_{o,n}$.

# I. Parametric 2-endofctors and their Algebras

Just like before, often at our disposal we have a more minimal structure. Instead of requiring strong 2-monad, we can insist merely a strong 2-endofctor. The data of an 2-endofctor will be the same as the algebra for endofunctor 2.8.

**Example 1.1** (Folding RNN cell), Consider the endofunctor $1 + A \times -$ from Example 9. Via strength from Example E10 we can form the 2-endofun $Para(1 + A \times -): Para(Set) \to Para(Set)$. Then a folding recurrent neural network arises as its algebra. More concretely, an algebra here consists of the carrier $S$ (chosen to denote *hidden state*) and a parametric map $(P, cell^{rst}) \in Para(Set)(1 + A \times S) \cong P + P \times A \times S$ we can break into two pieces: the choice of the initial hidden state $cell^S: P \to S$ and the recurrent neural network cell $cell^{rst}: P \times A \times S \to S$, as shown in the figure below. We will see how this construction will produce a recurrent neural network which consumes a sequence of inputs and iteratively updates its hidden state. 

Figure 5. An algebra for $Para(1 + A \times -)$ consists of a recurrent neural network and an initial hidden state.

starting state produces a stream of outputs.

$^{16}$We note that the hidden state is allowed to denote the parameter, which is not possible in the usual definition of a recurrent neural network cell.

From Example E10 we can form the 2-endofun $Para(A+(-)^2)$ on $Para(Set)$. Then a recurrent neural network arises as its algebra. More concretely, an algebra here consists of the carrier $S$ and a parametric map $(P, cell^{csv}) \in Para(Set)(A+S^2)$. Via the isomorphism $P \times (A+S^2) \cong P + P \times A \times S^2$ we can break into two pieces: the choice of the initial hidden state $cell^S$ and the recurrent neural network cell $cell^{csv}: P \times A \times S^2 \to S$, as shown in the figure below.

![](img/92dd63b8e10fefd3f3f227bf65a30b83_27_1.png)

Figure 6. An algebra for $Para(A+(-)^2)$ consists of a recurrent neural network and an initial hidden state.

**Example 1.3** (Folding RNN), Consider the endofunctor $O \times -$ from Example H.4. Via strength $\sigma_{P,X}: P \times (O \times X) \to O \times P \times X$ we can form the 2-endofun $Para(O \times -): Para(Set) \to Para(Set)$. Then an unfolding recurrent neural network arises as its algebra. More concretely, a coalgebra consists of the carrier $S$, and a parametric map $(P, (cell_o, cell_s)) \in Para(Set)(S \times O)$. Here $cell_o: P \times S \to O$ computes the output and $cell_s: P \times S \to S$ computes the next.$^{17}$ We will see how this construction will produce an unfolding recurrent neural network which is

![](img/92dd63b8e10fefd3f3f227bf65a30b83_27_2.png)

Figure 7. An algebra for $Para(O \times -)$ consists of an unfolding recurrent neural network.

$^{17}$By universal property of the carrier we can treat it as one type of $P \times S \to O \times S$ or as two cells.
