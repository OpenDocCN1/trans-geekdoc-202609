$$C_{x} = \frac {1}{2}\| y(x) - o(x, w, b) \| ^ {2} \tag {8.20}$$

7 *Complete the sentence: Due to the time-consuming nature of computing * 
 * 
*gradients for each entry in the training corpus, modern DL libraries * 
 *utilize a technique that gauges the gradient by first randomly sampling a * 
 *subset from the training corpus, and then averaging only this subset in * 
 *every epoch. This approach is known as [...] . The actual number of * 
 *randomly chosen samples in each epoch is termed [...] . The gradient * 
 * 
*itself is obtained by an algorithm known as [...] .*



# PRB-208 CH.PRB-8.32.

*The following questions refer to the MLP depicted in (9.1) . The inputs to * 
 * 
*the MLP in (9.1) are $x_1 = 0.9$ and $x_2 = 0.7$ respectively, and the weights $w_1* 
 *= -0.3$ and $w_2 = 0.15$ respectively. There is a single hidden node, $H_1$. The * 
 * 
*bias term, $B1$ equals 0.001.*

![](bbox=[0.31, 0.49, 0.69, 0.69])

+   1. *We examine the mechanism of a single hidden node, $H_1$. The inputs and * 
 * 
*weights go through a linear transformation. What is the value of the * 
 * 
*output (out 1) observed at the sum node?*

+   2. *What is the value resulting from the application the sum operator?*

+   3. *Verify the correctness of your results using PyTorch .*