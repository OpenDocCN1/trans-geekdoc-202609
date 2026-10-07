# Iterative convolutional neural network 227

than 5. In the second case, proceeding to the next iteration does not increase the top-
accuracy and ICNN is terminated, while the confidence threshold is not reached.

The effect of this early termination is 2-fold: on the one hand, it identifies images
would never reach a high classification confidence, and for which processing of
more iterations is a waste of resources, reducing computation with no accuracy.

On the other hand, prematurely terminates the processing of images that could
reached high confidences in the proceeding iteration, negatively affecting the
accuracy. Hence, the selection of the best combination of $D_{ci}$ and $S_{it}$ is an optimization
problem.

Figure 9.25 shows when the value of $S_{it}$ at each iteration is selected to
s slightly higher than $D_{ci}$ of the next iteration, reductions in FLOP and parameter
counts have the least impact on accuracy (see T4-P5 hybrid policy).

It should be noted that the inverse impact of aggressive pruning and thresholding
on parameter and FLOP count mentioned for Figure 9.24 is observed for Figure 9.25
t too (see red bars in both the figures).

# 9.11.3 Run-time and overall accuracy

# 9.11.3.1 Pruning and/or thresholding

Adopting the pruning or TP creates a trade-off between average delay of classification,
 the accuracy of the classification. The pruning policy reduces the parameter,
and the TP reduces the average FLOP count. However, based on the results (Figures
9.21 and 9.22), increased resources does not always translate into higher accuracy.
The hybrid policies, which combine both pruning and thresholding, exhibit the same
behavior, which higher number of parameters and FLOPs does not always contribute
to higher classification accuracy. Consequently, finding the optimal strategy in the
target accuracy is reached with minimal resources (in this case execution time),
requires thorough exploration and tuning of the thresholding and pruning parameters.

Figure 9.26 captures the design space of the ICNN when trading the accuracy
to reduce run-time through 5k combination of thresholding and pruning policies.

![](bbox=[0.078, 0.653, 0.856, 0.853])

Figure 9.26 The accuracy vs. average run-time per image of iterative AlexNet with
a batch size of 1 for 50k validation images on K80 GPU. The diamond
 the original AlexNet. The policies on the top border of the
diagram mark the most efficient ones in terms of accuracy and
execution time