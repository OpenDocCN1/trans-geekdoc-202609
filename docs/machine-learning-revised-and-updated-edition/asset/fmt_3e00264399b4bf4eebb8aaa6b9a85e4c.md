
In the last half century, we have seen that as computers find new applications in our lives, they have also changed our lives to make computation easier. Similarly, as our devices get smarter, the environment in which we live, and our lives in it, will change. Each age uses its current technology, which defines an environment with its constraints, and these propel new inventions and new technologies. If we can go back two thousand years and somehow give Romans the cell phone technology, I doubt that it would greatly enhance their quality of life, when they were still riding horses, that is, when the rest of their lives did not match up. The world when we will need human-level intelligence in machines will be a very different world.

When will we reach that level of intelligence and how much processing and training will be required are yet to be seen. Currently machine learning seems to be the most promising way to achieve it, so stay tuned.

# Glossary

## Adversarial example

A slightly perturbed example that causes a big change at the output. `Adversarial examples` are an indicator that the model’s response is very much specialized to the training examples, and that the model has not correctly generalized.

## Anonymization

Removal or hiding of information such that the source cannot be uniquely identified. It is not as straightforward as one would think.

## Artificial intelligence

Programming computers to do things, which, if done by humans, would be said to require “intelligence.” It is a human-centric and ambiguous term: calling computers “artificially intelligent” is like calling driving “artificial running.”

## Association rules

`If-then rules` associating two or more items in `basket analysis`. For example, “People who buy diapers frequently also buy beer.”

## Autoencoder network

A type of `neural network` that is trained to reconstruct its input at its output. Because there are fewer intermediary hidden units than inputs, the network is forced to learn a short, compressed representation at the hidden units, which can be interpreted as a process of abstraction.

## Backpropagation

A learning algorithm for artificial neural networks used for `supervised learning`, where connection weights are iteratively updated to decrease the approximation error at the output units.

## Bag of words

A method for document representation where we preselect a lexicon of `N` words and we represent each document by a list of length `N` where element `i` is 1 if word `i` exists in the document and is 0 otherwise.

## Basket analysis

A basket is a set of items purchased together (e.g., in a supermarket). `Basket analysis` is finding items frequently occurring in the same basket. Such dependencies between items are represented by `association rules`.

## Bayes’ rule

One of the pillars of probability theory where for two or more random variables that are not independent, we write conditional probability in one direction in terms of the conditional probability in the other direction:

`P(B|A) = P(A|B)P(B)/P(A)`.

It is used, for example, in diagnosis where we are given `P(A|B)` and `B` is the cause of `A`. Calculating `P(B|A)` allows a diagnostics—that is, the calculation of the probability of the cause `B` given the symptoms `A`.

## Bayesian estimation

A method for parameter estimation where we use not only the sample, but also the prior information about the unknown parameters given by a `prior distribution`. This is combined with the information in the data to calculate a `posterior distribution` using `Bayes’ rule`.

## Bayesian network

See `graphical model`.

## Behavioral cloning

One way of doing `imitation learning` where we observe how a human is solving the task step by step and each step is learned in a supervised manner; the robot learns to copy the human behavior exactly—that is, what the correct action is for each intermediate stage.

## Bioinformatics

Computational methods, including those that use machine learning, for analyzing and processing biological data.

## Biometrics

Recognition or authentication of people using their physiological characteristics (e.g., face, fingerprint) and behavioral characteristics (e.g., signature, gait).

## Character recognition

Recognizing printed or handwritten text. In optical recognition, the input is visual and is sensed by a camera or scanner. In pen-based recognition, the writing is done on a touch-sensitive surface and the input is a temporal sequence of coordinates of the pen tip.

## Class

A set of instances having the same identity. For example, ‘A’ and ‘A’ belong to the same class. In machine learning, for each class we learn a `discriminant` from the set of its examples.

## Classification

Assignment of a given instance to one of a set of `classes`.

## Cloud computing

A recent paradigm in computing where data and computation are not local but handled in some remote off-site data center. Typically there are many such data centers, and the tasks of different users are distributed over them in a way invisible to the user. This was previously called `grid computing`.

## Clustering

Grouping of similar instances into clusters. This is an `unsupervised learning` method because the instances that form a cluster are found based on their similarity to each other, as opposed to a `classification` task where the supervisor assigns instances to classes by explicitly labeling them.

## Connectionism

A neural network approach in cognitive science where mind is modeled as the operation of a network of many simple processing units running in parallel. Also known as `parallel distributed processing`.

## Cyber-physical systems

Computational elements directly interacting with the physical world. Some may be mobile. They may be organized as a network to handle the task in a collaborative manner. Also known as `embedded systems`.

## Data analysis

Computational methods for extracting information from large amounts of data. `Data mining` uses machine learning and is more data-driven; `OLAP` is more user-driven.

## Data mining

Machine learning and statistical methods for extracting information from large amounts of data. For example, in `basket analysis`, by analyzing large number of transactions, we find `association rules`.

## Data science

A recently proposed field in computer science and engineering composed of machine learning, high performance computing, and social, ethical, and legal aspects of data collection and analysis. `Data science` is proposed to handle in a systematic way the “big data” problems that face us today in many different scenarios.

## Data warehouse

A subset of data selected, extracted, and organized for a specific data analysis task. The original data may be very detailed and may lie in several different operational databases. The warehouse merges and summarizes them. The warehouse is read-only; it is used to get a high-level overview of the process that underlies the data either through `OLAP` and visualization tools, or by `data mining` software.

## Database

Software for storing and processing digitally represented information efficiently.

## Decision tree

A hierarchical model composed of decision nodes and leaves. The decision tree works fast, and it can be converted to a set of `if-then rules`, and as such allows `knowledge extraction`.

## Deep learning

Methods that are used to train models with several levels of abstraction from the raw input to the output. For example, in visual recognition, the lowest level is an image composed of pixels. In layers as we go up, a deep learner combines them to form strokes and edges of different orientations, which can then be combined to detect longer lines, arcs, corners, and junctions, which in turn can be combined to form rectangles, circles, and so on. The units of each layer may be thought of as a set of primitives at a different level of abstraction.

## Deep Q-Network

A deep neural network trained end to end with `Q-learning`.

## Dimensionality reduction
