# Recap: Convolutional Neural Networks (CNNs) on Grids

Single CNN layer with 3x3 filter:

![](bbox=[0.093, 0.355, 0.258, 0.673])

Update for a single pixel:

+   - Transform messages individually $W_i h_i$
- Add everything up $\sum_i W_i h_i$

$h_0 \quad h_1 \quad \dots$
$h_i$

$h_i \in \mathbb{R}^F$ are (hidden layer) activations of a pixel/node