# Biological Pattern Discovery with R

The interpretation capability is certainly important to all computational models in all disciplines. For instance, a protein function prediction model may need to know which genotype variable is a major factor initiating a specific protein function from a constructed machine learning model [Schietgat, et al., 2010]. A linear model can provide a good interpretation function, but is unable to model complex data. A nonlinear algorithm such as MLP or RBFNN or SVM can model complex data, but has less power of explaining what has been done in a model.

Data handling is also a key issue of the concern when modelling a data set. Data types can be very different from applications to applications. For instance, they might be categorical data or non-numerical data. The protease cleavage pattern discovery problem always deals with non-numerical data, i.e., the amino acids. Without an encoding process, the aforementioned machine learning algorithms can do nothing for the protease cleavage pattern discovery problem. This challenges the aforementioned machine learning algorithms.

Moreover, the problem of model construction complexity has been a great concern in some of the aforementioned machine learning algorithms. This is because they require the lengthy model construction time and a long process of the generalisation test to overcome the model uncertainty problem, such as the MLP algorithms.

Finally, dimensionality is also a concern when employing the aforementioned machine learning algorithms. Some of these algorithms are unable to handle data in which the dimension is greater than the number of samples. This is because the statistical significance cannot be guaranteed during a learning process.

# 3.6.7.1 The working principle of inductive learning

The inductive learning approaches have been well recognised to have a unique feature to overcome these limitations which occur to the aforementioned machine learning algorithms. The most commonly researched inductive learning approaches include the decision tree algorithm (DT) [Quinlan, 1986] and the classification and regression tree algorithm (CART) [Breiman, et al., 1984]. These algorithms have also been employed in many biological/medical pattern analysis projects.

The basic principle of DT and CART is “divide and conquer”, which is an old concept exercised in the computer sciences since 1970s