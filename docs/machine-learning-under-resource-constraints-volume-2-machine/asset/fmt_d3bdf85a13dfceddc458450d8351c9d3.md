
This view of epistemology fits well with the physics view, where there is no absolute space, no absolute time, and no absolute truth. Due to thermodynamical and quantum effects necessarily coupled to the electromagnetic interactions in the detection processes, even a fixed combination of theory parameters in top-down calculations cannot lead to any desired degree of precision and unambiguity in the measurement results. We improve our knowledge relative to the existing knowledge, which is itself relative to its context in the same sense.

The insight that uncertainty needs to be made explicit to allow for an ongoing process of modeling points to the probabilistic view of science, as put forward by Dempster[[142]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_142), Shafer, and Pearl[[347]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_347). The conference *Uncertainty in Artificial Intelligence* has been held every year since 1985. From a philosophical point of view, some machine learning approaches adopted a probabilistic view early on, e.g.,[[280]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_280).

This brings us to probabilistic representations of theories as Bayesian networks and graphical models. For our discussion, the most important characteristics of the Bayesian methods are i) that they combine knowledge in the form of a priori probabilities with learning from data and ii) that several hypotheses can be combined for the output of a prediction that is expressed as a probability of the outcome. Bayesian reasoning and learning both build on Bayes' law:

```
(1.1) $P(h \mid D) = \frac{P(D \mid h)P(h)}{P(D)}\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 1.1 \right)$
```

The hypothesis `h` that has the highest probability given the data, i.e., the Maximum A Posteriori (MAP) hypothesis is the resulting hypothesis. For a fixed data set, this is

```
(1.2) arg max[h ∈ H] P(D ∣ h)P(h)                  (1.2)
```

If we regard only the probability of the hypothesis conditioned on the data and we assume equal probability for all hypotheses, `P(h)` is omitted because it is the maximum likelihood. For all hypotheses in the space of possible hypotheses, e.g., all classes that are to be predicted, the probabilities are calculated, and the one with the highest is chosen. The network structure of Bayesian networks and graphical models in general is determined by the conditional independence of two variables (or network nodes) given the third one. This, together with prior knowledge, reflects the scientific knowledge.

Bayesian models may characterize other learning models and, hence, give them a sound basis. Actually, the output of many machine learning algorithms is the MAP hypothesis. It is a very general description of learning. Although the minimization of the least square error—computed in a statistical manner—is usually not performed according to the Bayes law, it delivers the MAP if the prior probabilities are the same for all classes, which is then the maximum likelihood. Understanding neural networks, giving them a sound theoretical basis, also employs Bayesian statistics. One instance is to show that a neural network's inference with dropout approximates a deep Gaussian process in a Bayesian sense[[174]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_174).

Causal reasoning is once again a hot topic in machine learning[[301]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_301) and has also been investigated in a Bayesian manner[[222]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_222). Current approaches may well be described as probabilistic rationalism.

### 1.2.4 The Big Data Move

The third reason why the early methods are not sufficient anymore comes from a fundamentally different situation in today's knowledge acquisition in physics, where the data volume and granularity demand novel methods, as stated in the following.

**Volume** We are no longer dealing with a few individual observations or measurements, but with the collection of data volumes so large and complex that the compilation of a few individual statements classifiable by humans is no longer possible. The analysis of a massive amount of data makes such different qualitative demands on its epistemological treatment that the whole can no longer be described effectively as a sum of its purely logically interpretable single statements.

**Granularity** What is electronically recorded or measured in such large numbers is simple. It consists of charges, times, and positions—and nothing else. The measurements are only indirectly related to the dependencies (e.g., energy spectra, angular distributions, mass distributions, or regularities in their temporal fluctuations), which are to be investigated in the language of physical theories. Usually, most of the measured data is not only entirely irrelevant for the investigated phenomenon; it can also be disturbing. In spite of the large amount of data recorded, the measurement space can be very sparsely occupied. Therefore, in addition to mapping the data onto the theory, the selection of the subset of the data relevant to the physical problem to be analyzed has to be investigated first. In this view, phenomenon and measurement are linked by probability distributions, and may be suspended at a few measuring points (like e. g. in radio astronomy).

**Background knowledge and model checking** We already have a very sophisticated and successful model conception of the world fixed in mathematical theories. So the task is not to conclude from "something observed" to an explanatory relationship for the first time, but it consists in checking whether a model

Modern scalable machine learning methods have been developed as a response to the situation of big data. The research question of how the levels of cognition can be integrated is still open. Neural networks model the low-level processes of recognition and action, which are not conscious, and have been tremendously successful in image or vision understanding. Explaining the recognition patterns and allowing for a critical inspection of the trained neural network is not only attractive for the human supervision of computational learning; it also aims at a model of the interaction of neural and semantic cognition[[358]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_0357). Again, the exploitation of contradictions plays a crucial role.

In order to apply these general insights to the relationship between experimental data recording and physical theory, we will first introduce the generic cycle of knowledge acquisition based on big data in physics. The key issues in data analysis will first be outlined per se in this framework before presenting recent methodological developments in the remainder of the book.

## 1.3 From the Physical Theory to the Physical Observable

The core of the statistical methods used in modern physics, together with the machine learning methods developed in computer science, consists of determining the probability densities needed to establish connections between the world of registered values and the world of formulas in theoretical physics. The principle of this form of knowledge acquisition is `top down` (in the forward direction); the aim is to derive phenomena from causes in simulations based on all existing physical knowledge by creating a complete virtual reality, including all known fluctuations and oscillations. On the one hand, the predictions of the measurement results calculated this way can be directly compared with experimental measurements.
