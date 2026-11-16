
![](img/79e1fe8e9526bd305f03debed54bb01f_6_0.png)

Figure 1: Outline

This manuscript covers a wide spectrum of topics in deep reinforcement learning. Although we have tried our best for excellence, there are inevitably shortcomings or even mistakes. Comments and criticisms are welcome.

## 2 BACKGROUND

In this chapter, we briefly introduce concepts and fundamentals in artificial intelligence (Russell and Norvig, 2009), machine learning, deep learning (Goodfellow et al., 2016), and reinforcement learning (Sutton and Barto, 2018).

We do not give detailed background introduction for artificial intelligence, machine learning and deep learning; these are too broad to discuss in details here. Instead, we recommend the following recent Nature/Science survey papers: Jordan and Mitchell (2015) for machine learning, and LeCun et al. (2015) for deep learning. For reinforcement learning, we cover some basics as a mini tutorial, and recommend the textbook, Sutton and Barto (2018), two courses, RL course by David Silver at UCL (Silver, 2015) and Deep RL course by Sergey Levine at UC Berkeley (Levine, 2018), and a recent Nature survey paper (Littman, 2015). We present some resources for deep RL in Section 2.5.

In Figure 2, we illustrate relationship among several concepts in AI and machine learning. Deep reinforcement learning, as the name indicates, is at the intersection of deep learning and reinforcement learning. We usually categorize machine learning as supervised learning, unsupervised learning, and reinforcement learning. Deep learning can work with/as supervised learning, unsupervised learning, reinforcement learning, and other machine learning approaches. 3 Deep learning is part of machine learning, which is part of AI. Note that all these fields are evolving, e.g. deep learning and deep reinforcement learning are addressing classical problems, like logic, reasoning, and knowledge representation. Reinforcement learning can be important for all AI problems, as quoted from Russell and Norvig (2009), “reinforcement learning might be considered to encompass all of AI: an agent is placed in an environment and must learn to behave successfully therein”, and “reinforcement learning can be viewed as a microcosm for the entire AI problem”.

### 2.1 ARTIFICIAL INTELLIGENCE

Artificial intelligence (AI) is a very broad area. Even an authoritative AI textbook like Russell and Norvig (2009) does not give a precise definition. Russell and Norvig (2009) discuss definitions of AI from four perspectives in two comparisons: 1) thought process and reasoning vs. behaviour, and 2) success in terms of fidelity to human performance vs. rationality, an ideal performance measure. We follow the discussions of Russell and Norvig (2009), list four ways to define AI, quoting directly from Russell and Norvig (2009).

Definition 1, “acting humanly”, follows the Turing Test approach. “The art of creating machines that perform functions that require intelligence when performed by people.” (Kurzweil, 1992) “The study of how to make computers do things at which, at the moment, people are better.” (Rich and Knight, 1991)

A computer passes a Turing Test, if a human interrogator can not tell if the written responses to some written question are from a computer or a human. The computer needs the following capabilities: natural language processing (NLP) for successful communication in English, knowledge representation for storage of what it knows or hears, automated reasoning for answering questions and drawing new conclusions from the stored information, and machine learning for adaptation to new scenarios and detection and extrapolation of patterns. In a total Turing Test, video signals are involved, so that a computer needs more capabilities, computer vision for object perception, and robotics for object manipulation and motion control. AI researchers have been devoting most efforts to the underlying principles of intelligence, mostly covered by the above six disciplines, and less on passing the Turing Test, since, duplicating an exemplar is usually not the goal, e.g., an airplane may not simply imitate a bird.

Definition 2, “thinking humanly”, follows the cognitive modeling approach. “The exciting new effort to make computers think ... machines with minds, in the full and literal sense.” (Haugeland,

3 Machine learning includes many approaches: decision tree learning, association rule learning, artificial neural networks, inductive logic programming, support vector machines, clustering, Bayesian networks, reinforcement learning, representation learning, similarity and metric learning, sparse dictionary learning, genetic algorithms, and rule-based machine learning, according to Wikipedia, https://en.wikipedia.org/wiki/Machine_learning. Also check textbooks like Russell and Norvig (2009), Mitchell (1997), and Zhou (2016).

![](img/79e1fe8e9526bd305f03debed54bb01f_8_0.png)

Figure 2: Relationship among deep reinforcement learning, deep learning, reinforcement learning, supervised learning, unsupervised learning, machine learning, and artificial intelligence. Deep learning and deep reinforcement learning are addressing many classical AI problems.

1989) "[The automation of] activities that we associate with human thinking, activities such as decision-making, problem solving, learning ..." (Bellman, 1978)

Definition 3, "thinking rationally", follows the "law of thought" approach. "The study of mental faculties through the use of computational models." (Charniak and McDermott, 1985) "The study of the computation that make it possible to perceive, reason, and act." (Winston, 1992)

Definition 4, "acting rationally", follows the rational agent approach. "Computational Intelligence is the study of the design of intelligent agents." (Poole et al., 1998) "AI ... is concerned with intelligent behavior in artifacts." (Nilsson, 1998) The rational agent approach is more amenable to scientific development than those based on human behavior or human thought. Russell and Norvig (2009) thus focus on general principles of rational agents and their building components.

We list the foundations and the questions they attempt to answer as in Russell and Norvig (2009): philosophy, for questions like, "Can formal rules be used to draw valid conclusions?", "How does the mind arise from a physical brain?", "Where does knowledge come from?", and "How does knowledge lead to action?"; mathematics, for questions like, "What are the formal rules to draw valid conclusions?", "What can be computed?", and "How do we reason with uncertain information?"; economics, for questions like, "How should we make decisions so as to maximize payoff?", "How should we do this when others may not go along?", and "How should we do this when the payoff may be far in the future?"; neuroscience, for questions like, "How do brains process information?"; psychology, for questions like, "How do humans and animals think and act?"; computer engineering, for questions like, "How can we build an efficient computer?"; control theory and cybernetics, for questions like, "How can artifacts operate under their own control?"; and linguistics, for questions like, "How does language relate to thought?"

Russell and Norvig (2009) present the history of AI as, the gestation of artificial intelligence (1943-1955), the birth of artificial intelligence (1956), early enthusiasm, great expectations (1952 - 1969), a dose of reality (1966 - 1973), knowledge-based systems: the key to power? (1969 - 1979), AI becomes an industry (1980 - present), the return of neural networks (1986 - present), AI adopts the scientific method (1987 - present), the emergence of intelligent agents (1995 - present), and the availability of very large data sets (2001 - present).

### 2.2 MACHINE LEARNING

Machine learning is about learning from data and making predictions and/or decisions. Quoting from Mitchell (1997), "A computer program is said to learn from experience \(E\) with respect to some class of tasks \(T\) and performance measure \(P\) if its performance at tasks in \(T\), as measured by \(P\), improves with experience \(E\)."

Usually we categorize machine learning as supervised, unsupervised, and reinforcement learning. In supervised learning, there are labeled data; in unsupervised learning, there are no labeled data. Classification and regression are two types of supervised learning problems, with categorical and numerical outputs respectively.

Unsupervised learning attempts to extract information from data without labels, e.g., clustering and density estimation. Representation learning is a classical type of unsupervised learning. However, training deep neural networks with supervised learning is a kind of representation learning. Representation learning finds a representation to preserve as much information about the original data as possible, and at the same time, to keep the representation simpler or more accessible than the original data, with low-dimensional, sparse, and independent representations.

Deep learning, or deep neural networks, is a particular machine learning scheme, usually for supervised or unsupervised learning, and can be integrated with reinforcement learning, for state representation and/or function approximator. Supervised and unsupervised learning are usually one-shot, myopic, considering instant rewards; while reinforcement learning is sequential, far-sighted, considering long-term accumulative rewards.

Reinforcement learning is usually about sequential decision making. In reinforcement learning, in contrast to supervised learning and unsupervised learning, there are evaluative feedbacks, but no supervised labels. Comparing with supervised learning, reinforcement learning has additional challenges like credit assignment, stability, and exploration. Reinforcement learning is kin to optimal control (Bertsekas, 2012; Sutton et al., 1992), and operations research and management (Powell, 2011), and is also related to psychology and neuroscience (Sutton and Barto, 2018).

Machine learning is the basis for big data, data science (Blei and Smyth, 2017; Provost and Fawcett, 2013), predictive modeling (Kuhn and Johnson, 2013), data mining (Han et al., 2011), information retrieval (Manning et al., 2008), etc, and becomes a critical ingredient for computer vision, natural language processing, robotics, etc. Probability theory and statistics (Hastie et al., 2009; Murphy, 2012; Vapnik, 1998) and optimization (Boyd and Vandenberghe, 2004; Bottou et al., 2018) are important for statistical machine learning. Machine learning is a subset of AI; however, it is evolving to be critical for all fields of AI.

A machine learning algorithm is composed of a dataset, a cost/loss function, an optimization procedure, and a model (Goodfellow et al., 2016). A dataset is divided into non-overlapping training, validation, and testing subsets. A cost/loss function measures the model performance, e.g., with respect to accuracy, like mean square error in regression and classification error rate.

The concept of entropy is important for the definition of loss functions. For a random variable \(X\) with distribution \(p\), the entropy is a measure of its uncertainty, denoted by \(\mathbb{H}(X)\) or \(\mathbb{H}(p)\),

```
\(\mathbb{H}(X) \triangleq - \sum_{k=1}^K p(X = k) \log_2 p(X = k).\)
```

For binary random variables, \(X \in \{0, 1\}\), we have \(p(X = 1) = \theta\) and \(p(X = 0) = 1 - \theta\),

```
\(\mathbb{H}(X) = -[\theta \log_2 \theta + (1 - \theta) \log_2(1 - \theta)].\)
```
