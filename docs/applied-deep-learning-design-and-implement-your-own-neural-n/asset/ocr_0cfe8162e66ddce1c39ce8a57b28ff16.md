Figures 4.163 and 4.164 shows the entire CNN model that classifies X or O:

![](bbox=[0.12, 0.13, 0.87, 0.3])

![](bbox=[0.12, 0.31, 0.87, 0.5])

# Backpropagation

The last and most useful component of CNN is Backpropagation. The difference between machine learning and deep learning is that in deep learning, the filters are automatically trained (changes), and objects are classified, but in machine learning, filters remain fixed. But how do these magic numbers (filters) appear? The answer is backpropagation. All of these filters are learned themselves, and you do not have to know them. The deep neural network does this on its own. So the underlying principle in the backpropagation is that the error in the final answer is used to determine how much the network adjusts and changes.

For example, in this case, if we know that we are putting in X and we obtain 0.92 votes for X, then the error is 0.08, and if we get 0.51 votes for O, then we know that there is an error of 0.49 as shown in figures 4.165 to 4.168. The error of 0.49 should be zero. If we add all the obtained errors, then we get the total error as (0.08 + 0.49 = 0.57), as shown in figure 4.169. So what happens with this error of 0.57? This error helps the process called as gradient descent (backpropagation), as discussed in Chapter 3: Intuition of Neural Networks.

So, for each of these filters (magic numbers), each of the voting weights is adjusted up and down by small amounts (learning rates) to see how the error changes. Using