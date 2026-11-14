
### false negative
An erroneous prediction that a positive instance is negative. See 27, 31, 32, 34, 36, 51, 114, 115, 119, 134, 156, 157.

### false positive
An erroneous prediction that a negative instance is positive. See 27, 32, 34, 35, 71, 114–117, 156, 157.

### false-negative rate
The frequency at which a predictor makes false negatives. In machine learning and statistics, this is a common performance measure for assessing a predictor along with the false-positive rate. See 27, 52, 96, 105, 120, 134, 137, 151, 157, 162, see also false negative.

### false-positive rate
The frequency at which a predictor makes false positives. In machine learning and statistics, this is a common performance measure for assessing a predictor along with the false-negative rate. See 27, 28, 102, 105, 109, 120, 131, 134, 151, 157, 162, 243, see also false positive.

### feature
An element of a data point; typically a particular measurement of the overall object that the data point represents. See 22, 30, 31, 38, 46, 47, 52, 63, 113, 212, 213, 219, 234, 246.

### feature deletion attack
An attack proposed by Globerson & Roweis (2006) in which the adversary first causes a learning agent to associate intrusion instances with irrelevant features and subsequently removes these spurious features from its intrusion instances to evade detection. See 41, 46.

### feature selection
The second phase of data collection in which the data are mapped to an alternative space \(\hat{\mathcal{X}}\) to select the most relevant representation of the data for the learning task. In this book, we do not distinguish between the feature selection and measurement phases; instead they are considered to be a single step, and \(\mathcal{X}\) is used in place of \(\hat{\mathcal{X}}\). See 24, 30, 31, 41, 46, 47, 246, 247.

### feature selection map (\(\phi\))
The (data-dependent) function used by feature selection to map from the original input space \(\mathcal{X}\) to a second feature space \(\hat{\mathcal{X}}\) of the features most relevant for the subsequent learning task. See 21, 24, 46, 72, 236, 247.

### Gaussian distribution (N (\(\mu\), \(\sigma\)))
A (multivariate) continuous probability distribution with support on \(\Re^D\) parameterized by a center \(\mu \in \Re^D\) and a scale \(\sigma \in \Re_+\) that has a probability density function given by \(P(\mathbf{x}) = \frac{1}{\sqrt{2\pi\sigma}} \exp \left( -\frac{||\mathbf{x}-\mu||_2^2}{2\sigma^2} \right)\). See 25, 136, 159, 160, 235.

### good word attack
A spam attack studied by Wittel & Wu (2004) and Lowd & Meek (2005b), in which the spammer adds words associated with non-spam messages to its spam to evade a spam filter. More generally, any attack where an adversary adds features to make intrusion instances appear to be normal instances. See 41, 42.

### gross-error model (\(\mathcal{P}_{\epsilon} (F_Z)\))
A family of distributions about the known distribution \(F_Z\) parameterized by the fraction of contamination \(\epsilon\) that combine \(F_Z\) with a fraction \(\epsilon\) of contamination from distributions \(H_Z \in \mathcal{P}_Z\). See 57.

### gross-error sensitivity
The supremum, or smallest upper bound, on the magnitude of the influence function for an estimator; this serves as a quantitative measure of a procedure or estimator. See 58.

### Hilbert space (H)
An inner-product space that is complete with respect to the metric induced by its inner product; i.e., the metric \(\|\mathbf{x}\|_{\mathcal{H}} \triangleq \sqrt{\langle \mathbf{x}, \mathbf{x} \rangle}\) for all \(\mathbf{x} \in \mathcal{H}\). See 102, 178, 188.

- **reproducing kernel Hilbert space**: A Hilbert space \(\mathcal{H}\) of real-valued functions on the space \(\mathcal{X}\), which includes, for each point \(\mathbf{x} \in \mathcal{X}\), a point-evaluation function \(k(\cdot, \mathbf{x})\) having the reproducing kernel property \(\langle f, k(\cdot, \mathbf{x}) \rangle_{\mathcal{H}} = f(\mathbf{x})\) for all \(f \in \mathcal{H}\). See 177–179, 185, 186, 188, 189, 197, 198, 233.

### hypothesis (f)
A function \(f\) mapping from the data space \(\mathcal{X}\) to the response space \(\mathcal{Y}\). The task for a learner is to select a hypothesis from its hypothesis space to best predict the response variables based on the input variables. See 21, 22, 24–27, _see also_ classifier.

### hypothesis space (F)
The set of all possible hypotheses, \(f\), that are supported by the learning model. While this space is often infinite, it is indexed by a parameter \(\boldsymbol{\theta}\) that maps to each hypothesis in the space. See 24–26.

### IDS
See 31, 40, 41, 45, 47, 53, 201, _Glossary_: intrusion detection system.

### index set
A set \(\mathbb{I}\) that is used as an index to the members of another set \(\mathbb{X}\) such that there is a mapping from each element of \(\mathbb{I}\) to a unique element of \(\mathbb{X}\). See 256.

### indicator function
The function \(\mathbb{I}[\cdot]\) that is 1 when its argument is true and is 0 otherwise. See 256.

### inductive bias
A set of (implicit) assumptions used in inductive learning to bias generalizations from a set of observations. See 22, 24.

### inductive learning
A task where the learner generalizes a pattern from training examples; e.g., finding a linear combination of features that empirically discriminates between positive and negative data points. See 22.

### influence function (IF \((z; H, F_{\mathcal{Z}})\))
A functional used extensively in robust statistics that quantifies the impact of an infinitesimal point contamination at \(z\) on an asymptotic estimator \(H\) on distribution \(F_{\mathcal{Z}}\); see Section 3.5.4.3. See 56, 57, 249.

### input space (\(\mathcal{X}\))
The space of all data points. See 23, _see also_ data point.

### intrusion detection system
A detector that is designed to identify suspicious activity that is indicative of illegitimate intrusions. Typically these systems are either host-based or network-based detectors. See 31.

### intrusion instance
A data point that corresponds to an illegitimate activity. The goal of malfeasance detection is to properly identify normal and intrusion instances and prevent the intrusion instances from achieving their intended objective. See 26.

### intrusion prevention system
A system tasked with detecting intrusions and taking automatic actions to prevent detected intrusions from succeeding. See 31, *see also* intrusion detection system.

### iterated game
In game theory, a game in which players choose moves in a series of repetitions of the game. See 58, 71.

### kernel function (_k_)
A bivariate real-valued function on the space $\mathcal{X} \times \mathcal{X}$, which implicitly represents an inner product in some Hilbert space so long as it is a positive semi-definite function. See 69, 102, 177–180, 182, 186, 187, 189, 191, 192, 197, 198.

- **RBF kernel**: A commonly used kernel function for numeric-valued data. The radial basis function (RBF) kernel is defined here as $k(\mathbf{x}^{(i)}, \mathbf{x}^{(j)}) = \exp \left( - \frac{\|\mathbf{x}^{(i)} - \mathbf{x}^{(j)}\|^2_2}{2\sigma^2} \right)$ where $\sigma > 0$ is the kernel's bandwidth parameter. See 174, 182, 197, *see also* Gaussian distribution.

### label
A special aspect of the world that is to be predicted in a classification problem or past examples of this quantity associated with a set of data points that are jointly used to train the predictor. See 23, 25–28, 33, 55, 58, 59, 63, 106, 107, 109, 110, 114, 115, 120, 130, 201, 235.

### labeled dataset
A dataset in which each data point has an associated label. See 23.

### Laplace distribution ($\text{Laplace}(\boldsymbol{\mu}, \lambda)$)
A (multivariate) continuous probability distribution with support on $\Re^D$ parameterized by a center $\boldsymbol{\mu} \in \Re^D$ and a scale $\lambda \in \Re_+$ that has a probability density function given by $P(\mathbf{x}) = \frac{1}{2\lambda} \exp \left( - \frac{\|\mathbf{x} - \boldsymbol{\mu}\|}{\lambda} \right)$. See 173, 182.

### Laplace noise
A random variable drawn from a $\mathbf{0}$-centered Laplace distribution and added to a nonrandom quantity. Laplace noise is used extensively in Chapter 7 through the Laplace mechanism to provide privacy properties to nonprivate learners. See 173, 179, 186, 188, 198, 244, *see also* Laplace distribution.

### learner
An agent or algorithm that performs actions or makes predictions based on past experiences or examples of how to properly perform its task. When presented with new examples, the learner should adapt according to a measure of its performance. See 24.

### learning algorithm
Any algorithm that adapts to a task based on past experiences of the task and a performance measure to assess its mistakes. See 25.

### loss function ($\ell$)
A function, commonly used in statistical learning, that assesses the penalty incurred by a learner for making a particular prediction/action compared to the best or correct one according to the *true* state of the world; e.g., the squared loss for real-valued prediction is given by $\ell(y, \hat{y}) \triangleq (\hat{y} - y)^2$. See 21, 25–27, 40, 50, 58, 59, 111, 112, 174, 177, 179, 180, 182–184, 186, 187, 192.
