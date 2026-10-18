| Name | Description | URL |
|---|---|---|
| Caret | A set of functions that attempt to streamline the process for creating ML models in R | https://topepo.github.io/caret/ |
| COMBO | Highly scalable common Bayesian optimization library, written in Python | https://github.com/tsudalab/combo |
| DeepChem | Open-source library for the use of deep learning in chemistry, written in Python | https://deepchem.io/ |
| Deeplearning4j | Generates deep neural nets from various shallow nets, written in Java | https://deeplearning4j.konduit.ai/ |
| H2O.ai | ML platform written in Java, and compatible with Python and R | https://www.h2o.ai/ |
| Keras | A high-level neural network API (Application programming interface), written in Python and capable of running on top of TensorFlow, CNTK, or Theano | https://keras.io/ |
| Mlpack | A fast, flexible machine learning library, written in C++ | https://mlpack.org/ |
| NSGA-II | A fast sorting and elite multiobjective genetic algorithm | http://www.mathworks.com/matlabcentral/fileexchange/10429-nsga-ii-amulti-objective-optimization-algorithm |
| Pytorch | An open-source machine learning framework, having Python and C++ interfaces, developed by Facebook | https://pytorch.org/ |
| Scikit-learn | A free software machine learning library for Python, featuring various classification, regression, and clustering algorithms | https://scikit-learn.org/stable/ |
| TensorFlow | A free and open-source software library for ML, developed by Google | https://www.tensorflow.org/ |
| TensorMol | A package of neural network models for chemistry | https://github.com/jparkhill/TensorMol |
| Weka | Free software containing a collection of visualization tools and algorithms for data analysis and predictive modeling, written in Java | https://www.cs.waikato.ac.nz/ml/weka/ |

# 2.3.7. Other Algorithms.

# 2.3.7.1 k-Nearest Neighbor (KNN).

KNN is widely used in pattern recognition because of its simplicity. Given a training set with n descriptors and an unknown sample, KNN identifies k nearest neighbors of the unknown sample in the n-dimensional space. The parameter k is defined by the users, and the distance between each pair of unknown and training set data points is calculated by the Euclidean distance in n-dimensional space. This algorithm is fast because it only stores the training set rather than modeling it, so new data can be seamlessly added to the model. Nevertheless, KNN has low efficiency when the training set is very large, or the data points are in very high-dimensional spaces. It is also sensitive to noise, missing values, and outliers, so deep preprocessing of the data is essential. In addition, all the descriptors must be normalized or standardized to balance the contributions of each. Because of its simplicity and interpretability, KNN is used in many areas of materials science, such as the prediction of molecular atomization energies and catalyst screening.

# 2.3.7.2. Kernel Ridge Regression (KRR).

KRR is an extension of ridge regression. KRR is an extension of ridge regression to tackle the nonlinearity. KRR is similar to SVR, except that KRR uses the squared error penalty, whereas the loss function of SVR is the ε-insensitive loss. Fitting a KRR model is faster than fitting an SVR model on a medium-sized data set (<1000 samples), but it is slower than SVR in fitting data and predicting when the data set is large. Currently, KRR models are used in materials ML modeling, e.g., analyzing crystal structures, optimizing catalysts, and learning the quantum chemical properties of molecules. 261-263

# 2.3.7.3. Genetic Algorithms.

Genetic algorithms are inspired by natural evolution. Materials are represented as genomes (encoded as a bits string) that contain information on composition, structure, synthesis conditions, etc. Given an initial pool of materials chosen randomly or by prior experience that have their fitness assessed, the fittest members of the pool are mutated using genetic operators such as crossover and mutation to form the next generation (progeny) of materials. Fitness functions are application dependent, e.g., catalytic activity, bioactivity, or quantum efficiency. Experiments are conducted to identify the fitness of materials pools in each iteration of the genetic optimization process.

# 2.3.7.4 Active Learning.

Active learning (sometimes called adaptive experimental design) is an iterative type of supervised learning well suited to large data sets whose output values (target property values) are scarce or expensive to obtain. A model (M₀) is first trained on the subset with labeled data. A small quantity of unlabeled data with high predicted uncertainty or high diversity is provided by M₀, and then experiments or calculations are used subsequently to find the output values (discrete values in classification, or continuous values in regression) for these data. Subsequently, a new model (M₁) is trained by using all the labeled data. This process can be iterated until all the data are labeled or the prediction errors are acceptably low. The aim of active learning is to achieve high accuracy by using as few labeled data as possible. For example, a Bayesian NN model built on a small training set labeled by accurate DFT calculations accurately predicted the bandgap of ~2.2 million 2D heterostructures. 276 Active learning is robust in electro/photocatalyst discovery and optimization, and electro/photocatalytic mechanism research with limited data. 129,148,277,278