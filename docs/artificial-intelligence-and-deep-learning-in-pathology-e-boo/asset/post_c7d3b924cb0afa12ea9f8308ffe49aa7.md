
![](img/ec668102bd6cbe5645156f246a7c2e8b_11_0.png)

### FIGURE 1.1

Circle bounded by inscribed and circumscribed polygons. The area of the circle lies between the areas of these bounds. As the number of polygon sides increases, the approximation becomes better and better.

Wikipedia commons; Public domain.

To how many decimal places we require. For a more “modern” approach, we can use a computer to sum a very large number of terms of an infinite series that converges to pi. There are many such series, the first of which having been described in the 14th century.

These rules-based programs are also capable of simulations; as an example, pi can be computed by simulation. For example, if we have a circle quadrant of radius = 1 embedded in a square target board with sides = 1 units, and throw darts at the board so that they randomly land somewhere within the board, the probability of a hit within the circle segment is the ratio of the area of that segment to the area of the whole square, which by simple geometry is pi/4. We can simulate this experiment by computer, by having it pick pairs of random numbers (each between zero and one) and using these as X-Y coordinates to compute the location of a simulated hit. The computer can keep track of both the ratio of the number of hits landing within the circle quadrant and the total number of hits anywhere on the board, and this ratio is then equal to pi/4. This is illustrated in Fig. 1.2.

![](img/ec668102bd6cbe5645156f246a7c2e8b_11_1.png)

### FIGURE 1.2

Simulation of random dart toss. Here the number of tosses within the segment of the circle is 5 and the total number of tosses is 6.

From Wikipedia commons; public domain.

In the example shown in Fig. 1.2, the value of pi is approximately 3.3, based on only 6 tosses. With only a few more tosses we can beat Archimedes, and with a very large number of tosses we can come close to the best value of pi obtained by other means. Because this involves random processes, it is known as Monte Carlo simulation.

Machine learning is quite different. Consider a program that is created to distinguish between squares and circles. For machine learning, all we have to do is present a large number of known squares and circles, each labeled with its correct identity. From this labeled data the computer creates its own set of rules, which are not given to it by the programmer. The machine uses its accumulated experience to ultimately correctly classify an unknown image. There is no need for the programmer to explicitly define the parameters that make the shape into a circle or square. There are many different kinds of machine learning strategies that can do this.

In the most sophisticated forms of machine learning such as neural networks (deep learning), the internal representations by which the computer arrives at a classification are not directly observable or understandable by the programmer. As the program gets more and more labeled samples, it gets better and better at distinguishing the “roundness,” or “squareness” of new data that it has never seen before. It is using prior experience to improve its discriminative ability, and the data itself need not be tightly constrained. In this example, the program can arrive at a decision that is independent of the size, color, and even regularity of the shape. We call this artificial intelligence (AI), since it seems more analogous to the way human beings behave than traditional computing.

## Varieties of machine learning

The age of machine learning essentially began with the work of pioneers such as Marvin Minsky and Frank Rosenblatt who described the earliest neural networks. However, this approach languished for a number of reasons including the lack of algorithms that could generalize to most real-world problems, the primitive nature of input storage, and computation in that period. The major conceptual innovations that moved the field forward were backpropagation and convolution, which we will discuss in detail in a later chapter. Meanwhile, other learning algorithms that were being developed also went beyond simply rule-based calculation and involved inferences from large amounts of data. These all address the problem of classifying an unknown instance based upon the previous training of the algorithm with a known dataset.

Most, but not all, algorithms fall into three categories. Classification can be based on clustering of data points in an abstract multidimensional space (support vector machines), probabilistic considerations (Bayesian algorithms), or stratification of the data through a sequential search in decision trees and random forests. Some methods utilizing these techniques are shown in Fig. 1.3.

![](img/ec668102bd6cbe5645156f246a7c2e8b_13_0.png)

### FIGURE 1.3

Varieties of machine learning.

*Reprinted from https://medium.com/sciforce/top-ai-algorithms-for-healthcare-aa5007ffa330, with permission of Dr. Max Ved, Co-founder, SciForce.*

All of those latter approaches, in addition to neural networks, are collectively known as “machine learning.” In recent years, however, neural networks have come to dominate the field because of their near-universal applicability and their ability to create high-level abstractions from the input data. Neural network-based programs are often defined as “deep learning.” Contrary to common belief, this is not because of the complexity of the learning that takes place in such a network, but simply due to the multilayer construction of a neural network as will be discussed below. For simplicity, in this book we will refer to the other kinds of machine learning as “shallow learning.”

The evolution of the neural network class of machine learning algorithms has been broadly but crudely based upon the workings of biological neural networks in the brain. The neural network does not “think”; rather it utilizes information to improve its performance. This is learning, rather thans by the opponent. This brute force approach evaluated billions of possible moves, but it was successful in defeating expert chess players. Machine learning algorithms, on the other hand, can develop strategically best lines of play based upon the experiences of learning from many other games played previously, much as prior examples improved a simple classification problem as described in the previous section. Early machine learning models took only 72 h of play to match the best rules-based chess programs in the world. Networks such as these learn to make judgment without implicit input as to the rules to be invoked in making those judgments.

What most machine learning programs have in common is the need for large amounts of known examples as the data with which to train them. In an abstract sense, the program uses data to create an internal model or representation that encapsulates the properties of those data. When it receives an unknown sample, it determines whether it fits that model to classify them. A neural network is one of the best approaches toward generating such internal models, but in a certain sense, every machine learning algorithm does this. For example, a program might be designed to distinguish between cats and dogs. The training set consists of many examples of dogs and cats. Essentially, the program starts by making guesses, and the guesses are refined through multiple known examples. At some point, the program can classify an unknown example correctly as a dog or a cat. It has generated an internal model of “cat-ness” and “dog-ness.” The dataset composed of known examples is known as the “training set.” Before using this model on unlabeled, unknown examples, one must test the program to see how well it works. For this, one also needs a set of known examples that are NOT used for training, but rather to test whether the machine has learned to identify examples that it has never seen before. The algorithm is analyzed for its ability to characterize this “test set.”

Although many papers quantitate the results of this test in terms of accuracy, this is an incomplete measure, and in cases where there is an imbalance between the two classes that are to be distinguished, it is completely useless. As an example, overall cancer incidence for the period 2011–15 was less than 500 cases per 100,000 men and women. I can create a simple algorithm for predicting whether a random individual has cancer or not, by simply having the algorithm report that everyone is negative. This model will be wrong less than only 500 times, and so its accuracy is approximately 99.5%! Yet this model is clearly useless, as it will not identify any patient with cancer.
