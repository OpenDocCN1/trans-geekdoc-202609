through sampling convex combinations of existing data points within the minority class.⁴⁰

Both SMOTE and Tomek links have only been proven effective in low-dimensional data. Many of the sophisticated resampling techniques, such as Near-Miss and one-sided selection,⁴¹ require calculating the distance between instances or between instances and the decision boundaries, which can be expensive or infeasible for high-dimensional data or in high-dimensional feature space, such as the case with large neural networks.

When you resample your training data, never evaluate your model on resampled data, since it will cause your model to overfit to that resampled distribution.

Undersampling runs the risk of losing important data from removing data. Oversampling runs the risk of overfitting on training data, especially if the added copies of the minority class are replicas of existing data. Many sophisticated sampling techniques have been developed to mitigate these risks.

One such technique is two-phase learning.⁴² You first train your model on the resampled data. This resampled data can be achieved by randomly undersampling large classes until each class has only N instances. You then fine-tune your model on the original data.

Another technique is dynamic sampling: oversample the low-performing classes and undersample the high-performing classes during the training process. Introduced by Pouyanfar et al.,⁴³ the method aims to show the model less of what it has already learned and more of what it has not.

# Algorithm-level methods

If data-level methods mitigate the challenge of class imbalance by altering the distribution of your training data, algorithm-level methods keep the training data distribution intact but alter the algorithm to make it more robust to class imbalance.

40 “Convex” here approximately means “linear.”

41 Jianping Zhang and Inderjeet Mani, “kNN Approach to Unbalanced Data Distributions: A Case Study involving Information Extraction” (Workshop on Learning from Imbalanced Datasets II, ICML, Washington, DC, 2003), https://oreil.ly/qnpra; Miroslav Kubat and Stan Matwin, “Addressing the Curse of Imbalanced Training Sets: One-Sided Selection,” 2000, https://oreil.ly/8phe.

42 Hansang Lee, Minseok Park, and Junmo Kim, “Plankton Classification on Imbalanced Large Scale Database via Convolutional Neural Networks with Transfer Learning,” 2016 IEEE International Conference on Image Processing (ICIP), 2016, https://oreil.ly/YiA8p.

43 Samira Pouyanfar, Yudong Tao, Anup Mohan, Haiman Tian, Ahmed S. Kaseb, Kent Gauen, Ryan Dailey, et al., “Dynamic Sampling in Convolutional Neural Networks for Imbalanced Data Classification,” 2018 IEEE Conference on Multimedia Information Processing and Retrieval (MIPR), 2018, https://oreil.ly/D3Ak5.