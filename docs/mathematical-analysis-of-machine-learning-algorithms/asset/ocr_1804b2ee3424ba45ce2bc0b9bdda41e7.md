{f(w,X): w ∈ Ω}, with which it competes. More generally, one may also consider improper online learning, where f̂_{t-1}(x) may not belong to the function class {f(w,x): w ∈ Ω}. We do not differentiate the two situations in our discussion.

To differentiate from online learning, the standard supervised learning setting is often referred to as batch learning in the machine learning literature. Regret bound analysis can be considered as a generalization of the oracle inequality in batch learning. We will show later that a regret bound directly implies an oracle inequality using a simple technique called online to batch conversion.

# 14.2 Perceptron Algorithms

In this section, we will study a simple online learning algorithm called the perceptron algorithm, which is a precursor to modern neural networks.

Consider the binary classification problem with Y ∈ {±1}, and linear functions

f(w,X) = w^T X,

with prediction rule

{
1    f(w,X) ≥ 0,
-1  otherwise.
}

The loss function is a binary classification error: 𝟙(f(w,X)Y ≤ 0). The perceptron algorithm (Rosenblatt, 1957, 1962) is an online learning algorithm that takes data sequentially, as in Algorithm 14.1. It is mistake-driven, which means it only updates the model weight vector when the prediction makes a mistake. The algorithm belongs to the family of linear classifiers. In many applications, one needs to design the linear features by hand.

```
Algorithm 14.1 Perceptron Algorithm
Input: Sequence (X1,Y1),..., (XT,YT)
Output: w_s
1 Let w0 = 0
2 for t = 1,2,...,T do
3   Observe Xt and predict label sign(w_{t-1}^T Xt)
4   Observe Yt and compute mistake 𝟙(w_{t-1}^T Xt Yt ≤ 0)
5   if w_{t-1}^T Xt Yt > 0 then
6     // No mistake
7     Let wt = w_{t-1}
8   else
9     // A mistake is observed
10    Let wt = w_{t-1} + Xt Yt
11 Randomly pick s from 0 to T − 1
Return: w_s
```