# Green and Blue Coordinate Pairs

![](bbox=[0.15, 0.17, 0.85, 0.47])

FIGURE 9.5 Green and Blue Coordinate Pairs.

We can simply distinguish between these two classes using a straight line, because the space is only two-dimensional. However, there may be more than one line to divide these classes. Consider Figure 9.6.

A linear or nonlinear classifier, often known as an SVM, is a mathematical function that can distinguish between two different object classes. These items fall under the category of classes and should not be confused with Java classes. The following pseudocode in code block 9.1 shows how to train an SVM.

```
Train an SVM with the labelled points. o_i ← w·x_i + b.
Assign y_i ← 1 to the largest o_i; −1 to the others.
C~ ← 10−5 C*

While C~ < C* do
repeat
Minimizing (1) with {y_i} fixed and C* is replaced by C~.
if ∃ ←(i, j) satisfying (6)
then
Swapping the labels of y_i and y_j
end if
until No labels have been swapped C~ ← min (9.5C, C*)
end while

Code block 9.1: Code Presents Algorithm for Training an SVM.
```

where ‘E’ denotes the probability of expectation under the probabilities p_u. The lesser of the two losses, V (1, o_i) and V, results from the fact that at optimality with regard to p_u, p_i must concentrate all of its mass on y_i = sign (wTx_i + b) (−1, o_i).