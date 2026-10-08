
# 15.4 NUMERICAL ILLUSTRATION

In this section, we offer numerical validation for the suggested measure. To test the validity of the proposed measure we shall carry out calculations for the proposed distance measure with the help of an example.

Let $\mathbb{Q}, \mathbb{P}$ and $\mathbb{O}$ be three IFS in $A=\{a_{1},a_{2},\ldots,a_{n-1},a_{n}\}$ then

$$
\begin{split}
\mathbb{Q} &= \langle 0,0.6,0.2 \rangle \langle 0,0.4,0.6 \rangle \langle 0.5,0.3 \rangle \\
\mathbb{P} &= \langle 0,0.8,0.1 \rangle \langle 0,0.7,0.3 \rangle \langle 0,0.6,0.1 \rangle \\
\mathbb{O} &= \langle 0,0.9,0.1 \rangle \langle 0,0.8,0.2 \rangle \langle 0.7,0.3 \rangle
\end{split}
$$

$$
\begin{split}
\hat{d}_{11}(\mathbb{Q},\mathbb{P}) &= 1 - \sum_{i=1}^{n} w_{i} \frac{\pi}{2} - \sin\frac{\pi}{2} \\
\hat{d}_{10}(\mathbb{Q},\mathbb{O}) &= 1 - \sum_{i=1}^{n} w_{i} \frac{\pi}{2} - \sin\frac{\pi}{2} \\
&= 0.014268
\end{split}
$$

Similarly, we can prove for $\hat{D}_{9}(\mathbb{Q}, \mathbb{P}), \hat{D}_{10}(\mathbb{Q}, \mathbb{O}), \hat{D}_{11}(\mathbb{Q}, \mathbb{O})$.

Numerical Rationale: From the above computations, it can be concluded as follows.

1. $0 \leq \hat{D}_{i} (\mathbb{Q}, \mathbb{O}) \leq 1$.
2. $\hat{D}_{i} (\mathbb{Q}, \mathbb{O}) = 0 \iff \mathbb{Q} \equiv \mathbb{O}$.
3. $\hat{D}_{i} (\mathbb{Q}, \mathbb{O}) = \hat{D}_{i} (\mathbb{O}, \mathbb{Q})$.
4. $\hat{D}_{i} (\mathbb{Q}, \mathbb{P}) \leq \hat{D}_{i} (\mathbb{Q}, \mathbb{O}) + \hat{D}_{i} (\mathbb{O}, \mathbb{P})$.

Table 15.1 shows the value of proposed distance measure and weighted distance measure.

**TABLE 15.1** Proposed Distance Measure for $\mathbb{Q}, \mathbb{O},$ and $\mathbb{P}$

| Distance Measure | $\hat{d}_{10}(\mathbb{Q}, \mathbb{O})$ | $\hat{d}_{10}(\mathbb{O}, \mathbb{P})$ | $\hat{d}_{10}(\mathbb{Q}, \mathbb{P})$ |
|---|---|---|---|
| $\hat{d}_{10}(\mathbb{Q}, \mathbb{O})$ | 0.001614 | 0.014157 | 0.014268 |
| $\hat{d}_{10}(\mathbb{Q}, \mathbb{O})$ | 0.667305 | 0.670701 | 0.670644 |

### 15.5 APPLICATIONS

Here, we have presented the applications related to the proposed distance measure to show the reliability of the proposed measure.

#### 15.5.1 PATTERN RECOGNITION

Suppose there are three patterns $\mathbb{Q}, \mathbb{P}$, and $\mathbb{O}$ and we wish to determine which among the following is closest to $\mathbb{Y}$ where

$$
\mathbb{Q} = \langle 1.0/a_{1} \rangle, \langle 0.8,0/a_{2} \rangle, \langle 0.7,0.1/a_{3} \rangle, \quad \mathbb{P} = \langle 0.8,0.1/a_{1} \rangle, \langle 1.0/a_{2} \rangle, \langle 0.9,0.1/a_{3} \rangle,
$$

$$
\mathbb{O} = \langle 0.6,0.2/a_{1} \rangle, \langle 0.8,0/a_{2} \rangle, \langle 1.0/a_{3} \rangle.
$$

and let $\mathbb{Y} = \langle 0.5,0.3/a_{1} \rangle, \langle 0.6,0.2/a_{2} \rangle, \langle 0.8,0.1/a_{3} \rangle$.

Let the weights $w_{i}$ are 0.5, 0.3, and 0.2, respectively.

Table 15.2 indicates that $\mathbb{P}$ exhibits the closest proximity to $\mathbb{Y}$, as it shows the least distance, suggesting that $\mathbb{Y}$ is the acknowledged and nearest pattern.

**TABLE 15.2** Distance Measure Between $\mathbb{Q}, \mathbb{P},$ and $\mathbb{O}$

| Distance Measure | $\hat{d}(\mathbb{Q}, \mathbb{Y})$ | $\hat{d}(\mathbb{P}, \mathbb{Y})$ | $\hat{d}(\mathbb{O}, \mathbb{Y})$ |
| :--- | :--- | :--- | :--- |
| $\hat{d}_{10}(\mathbb{Q}, \mathbb{P})$ | 0.07 | **0.02** | 0.04 |
| $\hat{d}_{11}(\mathbb{Q}, \mathbb{P})$ | 0.08 | **0.02** | 0.03 |

#### 15.5.2 MEDICAL DIAGNOSIS

Suppose a patient has been examined by a medical consultant on the basis of five symptoms like body temperature ($a_1$), tiredness ($a_2$), stomach issues ($a_3$), headache ($a_4$), and chest pain ($a_5$) and set of diagnosis $O = \{Viral Fever, Typhoid, Stomach problems, Malaria, and chest problem\}$. Using the feedback provided by patients, we aim to identify the disease that most closely aligns with their symptoms or conditions.

$$
\begin{array}{l}
\mathbb{Q}_{1}=\left\{\left\langle\frac{0.4,0}{a_{1}}\right\rangle,\left\langle\frac{0.3,0.5}{a_{2}}\right\rangle,\left\langle\frac{0.1,0.7}{a_{3}}\right\rangle,\left\langle\frac{0.4,0.3}{a_{4}}\right\rangle,\left\langle\frac{0.1,0.7}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{2}=\left\{\left\langle\frac{0.7,0}{a_{1}}\right\rangle,\left\langle\frac{0.2,0.6}{a_{2}}\right\rangle,\left\langle\frac{0.0,0.9}{a_{3}}\right\rangle,\left\langle\frac{0.7,0}{a_{4}}\right\rangle,\left\langle\frac{0.1,0.8}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{3}=\left\{\left\langle\frac{0.3,0.3}{a_{1}}\right\rangle,\left\langle\frac{0.6,0.1}{a_{2}}\right\rangle,\left\langle\frac{0.2,0.7}{a_{3}}\right\rangle,\left\langle\frac{0.2,0.6}{a_{4}}\right\rangle,\left\langle\frac{0.1,0.9}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{4}=\left\{\left\langle\frac{0.1,0.7}{a_{1}}\right\rangle,\left\langle\frac{0.2,0.4}{a_{2}}\right\rangle,\left\langle\frac{0.8,0}{a_{3}}\right\rangle,\left\langle\frac{0.2,0.7}{a_{4}}\right\rangle,\left\langle\frac{0.2,0.7}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{5}=\left\{\left\langle\frac{0.1,0.8}{a_{1}}\right\rangle,\left\langle\frac{0.0,0.8}{a_{2}}\right\rangle,\left\langle\frac{0.2,0.8}{a_{3}}\right\rangle,\left\langle\frac{0.2,0.8}{a_{4}}\right\rangle,\left\langle\frac{0.8,0.1}{a_{5}}\right\rangle\right\}
\end{array}
$$

and let $\mathbb{O} = \{<0.8,0.1>, <0.6,0.1>, <0.2,0.8>, <0.6,0.1>, <0.1,0.6>\}$.

Let the weights $w_i$ are 0.15, 0.2, 0.1, 0.25, and 0.3, respectively.

Table 15.3 gives that $\mathbb{O}$ is closest to $\mathbb{Q}_{1}$ as it has the least distance, which implies person is likely to be suffering from viral fever.

**TABLE 15.3** Distance Measure Between Medical Diagnosis and Patient

| Distance Measure | $\hat{d}(\mathbb{O}, \mathbb{Q}_{1})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{2})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{3})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{4})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{5})$ |
|:------------------|:-------------------------------:|:-------------------------------:|:-------------------------------:|:-------------------------------:|:-------------------------------:|
| $\hat{D}10(\mathbb{Q}_{j}, \mathbb{P})$ | 0.01 | 0.01 | 0.01 | 0.12 | 0.13 |
| $\hat{D}11(\mathbb{Q}_{j}, \mathbb{P})$ | 0.01 | 0.01 | 0.02 | 0.07 | 0.14 |

### 15.6 COMPARATIVE ANALYSIS

Comparative analysis serves as a valuable tool by allowing for the examination and assessment of similarities, differences, patterns, and relationships between different variables, subjects, or phenomena. In this article, our objective is to assess the dependability of the proposed measure by applying it to real-world scenarios such as pattern recognition and medical diagnosis.

Comparison between proposed distance measures by some renowned researchers has been done and the result obtained from them is unified for pattern recognition and medical diagnosis. Tables 15.4 and 15.5 show the result obtained for pattern recognition and medical diagnosis, respectively, for all the distance measure listed in this article.

**TABLE 15.4** Comparative Analysis of Distance Measure Between $\mathbb{Q}_{j}, \mathbb{P}$, $\mathbb{O}$ with $\mathbb{G}$ for Pattern Recognition

| Distance Measure | $\hat{d}(\mathbb{Q}_{j}, \mathbb{G})$ | $\hat{d}(\mathbb{P}, \mathbb{G})$ | $\hat{d}(\mathbb{O}, \mathbb{G})$ |
|:------------------|:-------------------------:|:----------------------:|:-----------------------:|
| $\hat{D}1(\mathbb{Q}_{j}, \mathbb{P})$ | 0.37 | 0.35 | 0.15 |
| $\hat{D}2(\mathbb{Q}_{j}, \mathbb{P})$ | 1 | 1 | 1 |
| $\hat{D}3(\mathbb{Q}_{j}, \mathbb{P})$ | 0.56 | 0.56 | 0.25 |
| $\hat{D}4(\mathbb{Q}_{j}, \mathbb{P})$ | 0.5 | 0.5 | 0.22 |
| $\hat{D}5(\mathbb{Q}_{j}, \mathbb{P})$ | 0.40 | 0.40 | 0.18 |
| $\hat{D}6(\mathbb{Q}_{j}, \mathbb{P})$ | 0.37 | 0.35 | 0.15 |
| $\hat{D}7(\mathbb{Q}_{j}, \mathbb{P})$ | 0.55 | 0.52 | 0.23 |
| $\hat{D}8(\mathbb{Q}_{j}, \mathbb{P})$ | 0.39 | 1.07 | 0.53 |
| $\hat{D}9(\mathbb{Q}_{j}, \mathbb{P})$ | 0.20 | 0.10 | 0.14 |
| $\hat{D}10(\mathbb{Q}_{j}, \mathbb{P})$ | 0.07 | 0.02 | 0.04 |
| $\hat{D}11(\mathbb{Q}_{j}, \mathbb{P})$ | 0.08 | 0.02 | 0.03 |
