
## A.4.3 Mutual information

In information theory, the *mutual information* of two random variables measures the amount of information we gain on one random variable with the prior knowledge on observing the other random variable. Given two random variables \( X \) and \( Y \), the mutual information \( I(X; Y) \) of random variables \( X \) and \( Y \) is summarized as follows:

\( I(X; Y) = \mathbb{E}_{(x,y) \sim p_{XY}} [\log \frac{p_{XY}(x, y)}{p_X(x) p_Y(y)} ] \
= \begin{cases} \sum_{(x,y)} p_{XY}(x, y) \log \frac{p_{XY}(x,y)}{p_X(x)p_Y(x)}, & \quad X, Y \text{ are discrete r.v.} \\ \int_{(x,y) \sim p_{XY}} p_{XY}(x, y) \log \frac{p_{XY}(x,y)}{p_X(x)p_Y(x)} dx dy, & \quad X, Y \text{ are continuous r.v.} \end{cases} \) (A.74)

where \( p_{XY} \) is the joint distribution of the joint random variable \( (X, Y) \), \( p_X \) is the marginal distribution of random variable \( X \), and \( p_Y \) is the marginal distribution of random variable \( Y \).

### Relationship between mutual information and KL-divergence

In terms of KL-divergence, mutual information \( I(X; Y) \) of two random variables \( X \) and \( Y \) is equivalent to the KL-divergence between the joint distribution \( p_{XY} \) and the product of their marginal distributions \( p_X \otimes p_Y \). The relationship between mutual information and KL-divergence is summarized as follows:

\( I(X; Y) = D_{KL}(p_{XY} || p_X \otimes p_Y). \) (A.75)

### Relationship between mutual information and entropy

In terms of entropy, mutual information of two random variables measures how much uncertainty we lose in one random variable by observing the other random variable. The relationship between mutual information and entropy is summarized as follows:

\( I(X; Y) = H(X) - H(X|Y) = H(Y) - H(Y|X) = H(X) + H(Y) - H(X, Y), \) (A.76)

where the last equality holds by applying the chain rule of entropy.

### Conditional mutual information

Given three random variables \( X \), \( Y \), and \( Z \), the conditional mutual information of the random variables \( X \) and \( Y \) given the random variable \( Z \) is summarized as follows:

\( I(X; Y|Z) = \mathbb{E}_{(x,y,z) \sim p_{XYZ}} [\log \frac{p_{X,Y|Z}(x, y|z)}{p_{X|Z}(x|z) p_{Y|Z}(y, z)}] = H(X|Z) - H(X|Y, Z). \) (A.77)

## Properties of mutual information.

- Mutual information is nonnegative, that is, \( I(X; Y) \ge 0, \forall X, Y \).
- Mutual information is symmetric, that is, \( I(X; Y) = I(Y; X) \).
- Mutual information of a random variable with itself is the entropy of that random variable, that is, \( I(X; X) = H(X) \).
- Mutual information of two independent random variables is 0, that is, \( I(X; Y) = 0 \) if \( X \) is independent to \( Y \).
- Mutual information follows the chain rule, that is, \( I(X; Y, Z) = I(X; Y) + I(X; Z|Y) \), where \( I(X; Y, Z) \) is the mutual information of \( X \), and joint random variable \( (Y, Z) \).
- Data processing inequality. Suppose the random variable \( Y \) is obtained by applying some function \( f \) on the random variable \( X \) (i.e., \( Y = f(X) \)) and the random variable \( Z \) is obtained by processing the random variable \( Y \) (e.g., applying some function \( g \) on the random variable \( Y \) to have \( Z = g(Y) \)). Data processing inequality guarantees that the mutual information between \( X \) and \( Z \) can never be larger than the mutual information between \( X \) and \( Y \). Mathematically, given a Markov chain \( X \rightarrow Y \rightarrow Z \) of three random variables, we have

\( I(X; Z) \le I(X; Y), \)

where the equality holds if and only if \( I(X; Y|Z) = 0 \).

- The *variation of information* of two random variables, which is a metric, can be inferred by their mutual information and joint entropy, that is, \( d(X, Y) = H(X, Y) - I(X; Y) \).

## A.4.4 Discrete Fourier transform (DFT) and fast Fourier transform (FFT)

Unless otherwise specified, we use sequence to represent discrete-time sequence in this section and use \( N \) to represent the length of a finite discrete-time sequence or the length of a period of a periodic discrete-time sequence.

### Finite sequence

A *finite sequence* \( x[n] \) of length \( N \) is the sequence of the following form³:

\( x[n] = \begin{cases} \text{some number}, & 0 \le n \le N - 1 \\ 0, & \text{otherwise.} \end{cases} \)

### Relationship between finite sequence and periodic sequence

It is intuitive that any finite sequence \( x[n] \) is associated with a corresponding periodic sequence \( \tilde{x}[n] \), that is,

\( \tilde{x}[n] = \sum_{t=-\infty}^{+\infty} x[n - tN] = x[(n \text{ mod. } N)], \)

where mod. is the modulo operation.

Similarly, a finite sequence \( x[n] \) can always be extracted from its corresponding periodic sequence \( \tilde{x}[n] \), that is,

\( x[n] = \begin{cases} \tilde{x}[n], & n \in \{0, \dots, N - 1\} \\ 0, & \text{otherwise.} \end{cases} \)

## Discrete Fourier series (DFS) of a periodic sequence.

Given a periodic sequence \(\tilde{x}[n]\) with period \(N\), the analysis and synthesis equations of the DFS \(\tilde{X}[k]\) (\(k \in \{0, \dots, N-1\}\)) of the periodic sequence \(\tilde{x}[n]\) is summarized as follows⁴:

Analysis equation: \(\tilde{X}[k] = \sum_{n=0}^{N-1} e^{-i(2\pi/N)kn} \tilde{x}[n]\)

Synthesis equation: \(\tilde{x}[n] = \sum_{k=0}^{N-1} e^{i(2\pi/N)kn} \tilde{X}[k]\).

## DFT of a finite sequence.

Since a finite sequence \(x[n]\) is one period of a periodic sequence \(\tilde{x}[n]\), in order to maintain the duality between time and frequency domains, the DFT \(X[k]\) of the finite sequence \(x[n]\) corresponds to one period of DFS \(\tilde{X}[k]\) of its corresponding periodic sequence \(\tilde{x}[n]\). As a result, the analysis and synthesis equations of the DFT \(X[k]\) of a finite sequence \(x[n]\) is summarized as follows:

Analysis equation: \(X[k] = \sum_{n=0}^{N-1} e^{-i(2\pi/N)kn} x[n]\)

Synthesis equation: \(x[n] = \sum_{k=0}^{N-1} e^{i(2\pi/N)kn} X[k]\).

It is worth mentioning that the matrix \(\mathbf{W}\) with \(\mathbf{W}[i, j] = e^{-i(2\pi/N)ij}\) is called the *DFT matrix*.

## Properties of DFT.

- Linearity. Given two finite sequences \(x_1[n], x_2[n]\) and their associated DFT \(X_1[k], X_2[k]\), if \(x_3[n] = ax_1[n] + bx_2[n]\), the DFT of \(x_3[n]\) is

\(X_3[k] = aX_1[k] + bX_2[k]\).

- Given a finite sequence \(x[n]\) and its DFT \(X[k]\), if we have a circular shift of length \(m\) in the time window and get the new finite sequence \(x_1[n] = x((n - m) \text{ mod. } N))\), the DFT of the new finite sequence \(x_1[k]\) is

\(X_1[k] = e^{-i(2\pi/N)km} X[k]\).

- The vector \(\mathbf{u}_k = [e^{-i(2\pi/N)k0}, e^{-i(2\pi/N)k1}, \dots, e^{-i(2\pi/N)k(N-1)}]\) forms an orthogonal basis over the set of \(N\)-dimensional complex vectors, i.e., \(\mathbf{u}_k^T \mathbf{u}_k^* = N\).

- Parseval's theorem. Given two sequences \(x_1[n]\) and \(x_2[n]\) and their associated DFT \(X_1[k]\) and \(X_2[k]\), we have

\(\sum_{n=0}^{N-1} x_1[n]x_2^*[n] = \frac{1}{N} \sum_{k=0}^{N-1} X_1[k]X_2^*[k]\),

where \(x_2^*[n]\) is the conjugate transpose of the sequence \(x_2[n]\) and \(X_2^*[k]\) is the conjugate transpose of \(X_2[k]\).

- Duality. Given a sequence \(x[n]\) and its DFT \(X[k]\), the DFT of \(X[k]\) is \(Nx[(-k \text{ mod. } N)]\)

- For a finite sequence \(x[n]\) and its DFT \(X[k]\), if all values are real numbers, we have

\(X[k] = X^*[(-k \text{ mod. } N)],\) (A.87)

which is called *even symmetry*. Here, \(X^*[k]\) is the conjugate transpose of \(X[k]\); if all values are imaginary numbers, we have

\(X[k] = -X^*[(-k \text{ mod. } N)],\) (A.88)

which is called *odd symmetry*.

- Given three finite sequences \(x_1[n]\), \(x_2[n]\), and \(x_3[n]\) and their corresponding DFT \(X_1[k]\), \(X_2[k]\), and \(X_3[k]\), if \(X_3[k] = X_1[k]X_2[k]\), we have

\(x_3[n] = \sum_{m=0}^{N-1} x_2[m]x_1[((n-m) \text{ mod. } N)].\) (A.89)

### FFT

FFT is a set of algorithms that efficiently compute the DFT of a finite sequence, based on theories ranging from arithmetic to number theory. FFT is widely applied in many real world scenarios like mathematics, engineering and music. The key principle of FFT is to decompose the computation of the DFT of a length-\(N\) sequence into computing several smaller subsequences. Some representative FFT algorithms include the prime-factor algorithm (PFA), the Cooley-Tukey algorithm, the Goertzel's algorithm, and the Winograd's algorithm. For details of FFT algorithms, please refer to the bibliographic notes.

## A.5 Bibliographic notes

Probability density function (PDF) and significance test are introduced in many statistic books (Larsen and Marx [LM05] and Casella and Berger [CB21]). For MLE and MAP, they are covered in many machine learning books (Bishop [Bis06b] and James, Witten, Hastie, and Tibshirani [JWHT]). Cross-validation is described by Bishop [Bis06b], and Jackknife is introduced by Barber, Candes, Ramdas, and Tibshirani [BCRT21]. GD, SGD, variants of GD, coordinate descent, and Newton's method are introduced in many primary and advanced books such as Goodfellow, Bengio, and Courville [GBC16] and Boyd, Boyd, and Vandenberghe [BBV04]. Dennis and Moré provide a detailed survey of Quasi-Newton methods [DM77]. For quadratic programming (QP), it is systematically introduced by Boyd, Boyd, and Vandenberghe [BBV04]. The solutions for QP are versatile such as active set methods (Murty and Yu [MY88]), Interior-point methods (Wright [Wri97]), and many more. For basic concepts, theories, and applications of linear algebra, they are comprehensively introduced by Strang [Str93, Str19] and Leon, Bica, and Hohn [LBH06].

Density estimation, which aims to approximate the underlying probability density function, has been an essential topic in statistics textbooks (Silverman [Sil18] and Devroye and Lugosi [DL12]). Density estimation using kernel tricks is extensively investigated in related research works (Botev, Grotowski,
