To our knowledge, we present a pioneering (hitherto unexplored in previous research) decentralized zeroth-order dual averaging algorithm, uniquely embodying the aforementioned benefits.

# 6.1.3 Organization and notation

Organization: In Section 6.2, we delineate the problem of decentralized online optimization with constraints and provide a foundational definition of differential privacy. In Section 6.3, we introduce a novel decentralized algorithm titled ZO-DDA. In Section 6.4, we conduct thorough analyses of both the convergence properties and privacy guarantees of ZO-DDA. Section 6.5 presents simulation scenarios to validate the efficacy of ZO-DDA. Lastly, in Section 6.6, we summarize our findings and engage in discussions about potential avenues for future extensions and improvements.

Notation: The scalar product between two vectors is formulated as \(\langle \cdot, \cdot \rangle\). We designate \(||\cdot||_1\) and \(||\cdot||\) to signify the 1-norm and Euclidean norm, respectively. The superscript \((\cdot)^\mathsf{T}\) symbolizes the transpose of a vector or a matrix. We assign \(\mathbb{E}[q]\) and \(\mathbb{P}[q]\) to represent the expected value and the probability of a random variable \(q\), correspondingly. The notations \(\mathbb{B}^m = \{x \in \mathbb{R}^m |||x|| \le 1\}\) and \(\mathbb{S}^m = \{x \in \mathbb{R}^m |||x|| = 1\}\) define the unit ball and the unit sphere, respectively. The subdifferential, denoted as \(\partial f(x) \subseteq \mathbb{R}^m\), comprises all subgradients \(g(x) \in \partial f(x)\) of the function \(f\) evaluated at \(x \in \mathbb{R}^m\).

# 6.2 Problem description

In this section, we delve into the intricacies of a decentralized approach to online constrained optimization, outlining the essence of the issue. Following this, we offer a foundational exposition of the concept of differential privacy.

# 6.2.1 Problem description

Given that each node \(i\), where \(i\) ranges from 1 to \(n\), is associated with a collection of local convex loss functions, denoted as \(\{f_t^i\}\) for \(t\) spanning from 1 to \(T\), and without specifying their exact formulations, the collective objective of the nodes interconnected in the network, at each instant \(t\) within the period 1 to \(T\), is to jointly tackle the minimization of the subsequent optimization task spanning the entire time horizon \(T\):

```
\(\min_{x \in \Omega} \sum_{t=1}^T f_t(x), \quad f_t(x) = \sum_{i=1}^n f_t^i(x), \tag{6.1}\)
```

where \(\Omega \subseteq \mathbb{R}^m\) is characterized as being non-empty, closed, and convex. Within this set, \(x\) represents a global decision vector. Now, let us envision a scenario involving online and bandit feedback mechanisms, where each node \(i\) is only permitted to inquire about the value of its loss function \(f_t^i\) after making a decision \(x_t^i\) at any given