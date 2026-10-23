
On the other hand, with unsupervised learning, a machine uses unlabeled data. In this case, only input data is given. Then, what the machine learns is patterns and rules that the dataset includes and contains. The purpose of unsupervised learning is to grasp the structure of the data. It can include a process called **clustering**, which classifies a data constellation in each group that has a common character, or the process of extracting the correlation rule. For example, imagine there is data relating to a user's age, sex, and purchase trend for an online shopping website. Then, you might find out that the tastes of men in their 20s and women in their 40s are close, and you want to make use of this trend to improve your product marketing. We have a famous story here—it was discovered from unsupervised training that a large number of people buy beer and diapers at the same time.

You now know there are big differences between supervised learning and unsupervised learning, but that's not all. There are also different learning methods and algorithms for each learning method, respectively. Let's look at some representative examples in the following section.

## Support Vector Machine (SVM)

You could say that SVM is the most popular supervised training method in machine learning. The method is still used for broad fields in the data mining industry. With SVM, data from each category located the closest to other categories is marked as the standard, and the decision boundary is determined using the standard so that the sum of the Euclidean distance from each marked data and the boundary is maximized. This marked data is called **support vectors**. Simply put, SVM sets the decision boundary in the middle point where the distance from every pattern is maximized. Therefore, what SVM does in its algorithm is known as **maximizing the margin**. The following is the figure of the concept of SVM:

![](img/9315e45972ec0fbaf15f9144035bca79_45_0.png)

Decision boundary  
Support vector  
Maximizing the margin  
Support vector

If you only hear this statement, you might think “is that it?” but what makes SVM the most valuable is a math technique: the kernel trick, or the kernel method. This technique takes the data that seems impossible to be classified linearly in the original dimension and intentionally maps it to a higher dimensional space so that it can be classified linearly without any difficulties. Take a look at the following figure so you can understand how the kernel trick works:

![](img/9315e45972ec0fbaf15f9144035bca79_46_0.png)

We have two types of data, represented by circles and triangles, and it is obvious that it would be impossible to separate both data types linearly in a two-dimensional space. However, as you can see in the preceding figure, by applying the kernel function to the data (strictly speaking, the feature vectors of training data), whole data is transformed into a higher dimensional space, that is, a three-dimensional space, and it is possible to separate them with a two-dimensional plane.

While SVM is useful and elegant, it has one demerit. Since it maps the data into a higher dimension, the number of calculations often increases, so it tends to take more time in processing as the calculation gets more complicated.

## Hidden Markov Model (HMM)

HMM is an unsupervised training method that assumes data follows the **Markov process**. The Markov process is a stochastic process in which a future condition is decided solely on the present value and is not related to the past condition. HMM is used to predict which state the observation comes from when only one observation is visible.

The previous explanation alone may not help you fully understand how HMM works, so let's look at an example. HMM is often used to analyze a base sequence. You may know that a base sequence consists of four nucleotides, for example, A, T, G, C, and the sequence is actually a string of these nucleotides. You won't get anything just by looking through the string, but you do have to analyze which part is related to which gene. Let's say that if any base sequence is lined up randomly, then each of the four characters should be output by one-quarter when you cut out any part of the base sequence.

However, if there is a regularity, for example, where C tends to come next to G or the combination of ATT shows up frequently, then the probability of each character being output would vary accordingly. This regularity is the probability model and if the probability of being output relies only on an immediately preceding base, you can find out genetic information (= state) from a base sequence (= observation) using HMM.

Other than these bioinformatic fields, HMM is often used in fields where time sequence patterns, such as syntax analysis of **natural language processing (NLP)** or sound signal processing, are needed. We don't explore HMM deeper here because its algorithm is less related to deep learning, but you can reference a very famous book, *Foundations of Statistical Natural Language Processing*, from MIT Press if you are interested.

## Neural networks

Neural networks are a little different to the machine learning algorithms. While other methods of machine learning take an approach based on probability or statistics, neural networks are algorithms that imitate the structure of a human brain. A human brain is made of a neuron network. Take a look at the following figure to get an idea of this:

![](img/9315e45972ec0fbaf15f9144035bca79_48_0.png)

One neuron is linked to the network through another neuron and takes electrical stimulation from the synapse. When that electricity goes above the threshold, it gets ignited and transmits the electrical stimulation to the next neuron linked to the network. Neural networks distinguish things based on how electrical stimulations are transmitted.

Neural networks have originally been the type of supervised learning that represents this electrical stimulation with numbers. Recently, especially with deep learning, various types of neural networks algorithms have been introduced, and some of them are unsupervised learning. The algorithm increases the predictability by adjusting the weight of the networks through the process of learning. Deep learning is an algorithm based on neural networks. More details on neural networks will be explained later, with implementations.

## Logistic regression

Logistic regression is one of the statistical regression models of variables with the Bernoulli distribution. While SVM and neural networks are classification models, logistic regression is a regression model, yet it certainly is one of the supervised learning methods. Although logistic regression has a different base of thinking, as a matter of fact, it can be thought of as one of the neural networks when you look at its formula. Details on logistic regression will also be explained with implementations later.

As you can see, each machine learning method has unique features. It's important to choose the right algorithm based on what you would like to know or what you would like to use the data for. You can say the same of deep learning. Deep learning has different methods, so not only should you consider which the best method among them is, but you should also consider that there are some cases where you should not use deep learning. It's important to choose the best method for each case.

## Reinforcement learning

Just for your reference, there is another method of machine learning called **reinforcement learning**. While some categorize reinforcement learning as unsupervised learning, others declare that all three learning algorithms, supervised learning, unsupervised learning, and reinforcement learning, should be divided into different types of algorithms, respectively. The following image shows the basic framework of reinforcement learning:

![](img/9315e45972ec0fbaf15f9144035bca79_49_0.png)
