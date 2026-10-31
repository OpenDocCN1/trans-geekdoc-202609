
![](img/2fa0633d317c0872f05788febf717c11_295_0.png)

FIGURE 16.2: The language of arrays

## 16.7 Authentication and universal hashing

In Section 16.1 orthogonal arrays were interpreted from a probabilistic point of view. Its rows are elements of a probability space, and each column describes a random variable with values in the set of entries. The basic parameter t, the strength of the OA, guarantees a certain statistical independence condition for this family of random variables.

In this section we will look at an array from the point of view introduced in Chapter 6, as a family of mappings. We index the columns with the elements of a set (the ground set) and interpret each row as a mapping from the ground set to the set of entries. Recall from Definition 6.1 that an (n, M)_q array (or (n, M)_q hash family) is an array (a matrix) with n rows and M columns, where each entry is taken from an alphabet Y of size q. Now we interpret each row of the array as a mapping f : X ⟶ Y, where |X| = M (the elements of X parametrize the columns).

In Chapter 6 an (n, M)_q hash family was defined to be ε universal if, for any choice of two different elements in the ground set, the probability of collision is bounded by ε (see Definition 6.3). It turned out that ε universal hash families are equivalent to error-correcting codes. An application to error detection was given.

Our next area of application is authentication. Before getting into this, let us define the type of hash families that we want to use now.

![](img/2fa0633d317c0872f05788febf717c11_296_0.png)

ground set X      image set Y

FIGURE 16.3: Equivalently, families of mappings

### 16.26 Definition. An $(n,M)_q$ hash family is $\epsilon$ strongly universal for some $0 < \epsilon < 1$ if the following are satisfied:

- For any $x \in X$ and $y \in Y$, the number of mappings $f \in \mathcal{F}$ such that $f(x) = y$ is precisely $n/q$.
- For any two distinct elements $x_1,x_2 \in X$ and for any two (not necessarily distinct) elements $y_1,y_2 \in Y$, the number $\nu$ of functions $f \in \mathcal{F}$ such that $f(x_1)=y_1$, $f(x_2)=y_2$ satisfies $\frac{\nu}{n/q} \le \epsilon$.

The first condition says that in the corresponding array each entry occurs with the same frequency in each column (equivalently, the array is an orthogonal array of strength 1). This facilitates the probabilistic interpretation of this structure: we know that there are precisely $n/q$ mappings $f$ satisfying $f(x_1)=y_1$. Restrict attention to these functions only. Choose one of them at random. The second condition says that the chance of finding a function which satisfies $f(x_2)=y_2$, is $\le \epsilon$. This means that $\epsilon$ is an upper bound on a conditional probability: $Pr(f(x_2)=y_2 \mid f(x_1)=y_1) \le \epsilon$ (the probability that $f(x_2)=y_2$ provided that $f(x_1)=y_1$ is bounded by $\epsilon$).

## Authentication

Let $\mathcal{A}$ be an $\epsilon$ strongly universal ($\epsilon$ SU) hash family. We want to show how to use it as an authentication system. Identify $\mathcal{A}$ with the corresponding array. A source produces messages to be sent from the originator (the **transmitter**) to a remote **receiver**, via a public channel. In order to be able to distinguish two types of messages, those produced by the source and those (possibly encrypted or otherwise changed) sent via the channel, we denote the messages produced by the source as **source states**, and those sent over the channel as **messages**. Identify the source states with the columns of the array (the elements of the ground set $X$). Our concern here is not with secrecy (protecting the knowledge as to which source state is being transmitted) nor with error correction (the channel may be noisy and we may wish to use an error-correcting code), but with **authentication**. This means that we want to devise schemes which enable the receiver to verify if the message really originated from the proper transmitter and has not been altered on the way. This is where the defining properties of an $\epsilon$ SU family come in. Use the mappings $f \in \mathcal{A}$ as **keys**. The elements $y \in Y$ are **authenticators**. Assume $x \in X$ is the source state to be transmitted. Transmitter and receiver will agree, via a secure private channel, on a key $f \in \mathcal{A}$ to be used. Then the message (consisting of $x$, possibly in encrypted form, and encoded for error correction purposes) will contain the **authentication tag** $f(x) = y$. Upon receiving a message which decodes to $x' \in X$, with authentication tag $y' \in Y$, the receiver will accept it as authentic if and only if $f(x') = y'$. Observe that, if no problems occurred, then $x' = x, y' = y = f(x)$, and the message will be accepted as authentic.

Why would we want to use an $\epsilon$ SU hash family, and what is the meaning of $\epsilon$? Imagine an opponent has access to the communication channel. His or her aim is to disturb the system, more precisely, to have nonauthentic messages accepted as authentic. Everything hinges upon the assumptions concerning the power of this opponent. Consider two types of attack:

### The impersonation attack

It is always assumed that the opponent knows the system. His only problem is that he has no access to the secure channel, and so has no a priori information on the key used. Assume the opponent forges a message and sends it to the receiver, claiming it originated from the transmitter. He tries to maximize his chances of success. However, the first property of Definition 16.26 shows that his probability of success is precisely $1/q$, where $q = |Y|$ is the number of authenticators.

### The substitution attack

Assume the opponent is able not only to read messages but also to alter them and send the altered version to the receiver. Knowledge of the message gives him some information on the key used. Assume he knows the source state x (we do not want to assume anything concerning secrecy). Then the secret key is one of the mappings f satisfying f(x) = y. How can the opponent use this knowledge to improve his chances of cheating? He wishes to have a different message, corresponding to a source state x' ≠ x, accepted as authentic. He has to choose an authentication tag y' such that, with high probability, y' = f(x'). However, the second property of Definition 16.26 shows that his probability of success will always be ≤ ε. Observe that, when x' ≠ x has been chosen, then the opponent's probability of success can be written as a conditional probability: Pr(f(x') = y' | f(x) = y). Here x, x', y, y' are given (x' ≠ x), and the probability refers to the choice of f ∈ A.

### The problem of efficiency

We have seen how an ε SU hash family can be interpreted as an authentication system (often called **authentication code**) with the property that an opponent's probability of success with a substitution attack is provably limited by ε. It should be observed that, for each transmission of a source state, a new key has to be generated at random and this information transmitted to the receiver beforehand, via a secure channel. In order to obtain a system which can be used in practice, we have to limit the amount of time and space required by authentication.

If, for example, there are n = 2^100 keys and q = 2^40, then the authenticator tag will have 40 bits and the information on the key, to be sent via the secure channel, will be a bit string of length 100. It would not make much sense to use such a system when the number of messages is M = |X| = 2^100. We cannot afford to spend half the transmission time for authentication purposes. This leads to the problem of efficiency.

The parameters M (the number of source states) and ε (the level of security) can be thought of as given. We want to construct authentication systems, equivalently ε-SU hash families, such that the number n of keys and the number q of authenticators are as small as possible. The most reasonable measure seems to be log2(n) + log2(q) = log2(nq). This is the parameter we wish to minimize, where M and ε are given.
