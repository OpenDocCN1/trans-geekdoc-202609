![](bbox=[0.22, 0.12, 0.77, 0.43])

FIGURE 4.2
Evaluating the distance between two-dimensional features. The reference image is positioned on the pixel $I(r, s)$.

The maximum of the differences:

$$d_M(r, s) = \max_{(i,j) \in R} |I(r+i, s+j) - R(i, j)| \quad \text{(4.2)}$$

The sum of the squared distances:

$$d_E(r, s) = \sqrt{\sum_{(i,j) \in R} ((I(r+i, s+j) - R(i, j))^2} \quad \text{(4.3)}$$

In order to illustrate the effects of each index on images, we test each of them when they are used to determine the best matching points. For this experiment, the image $I(x, y)$ and pattern $R(i, j)$ are considered as shown in Figure 4.3.

# 4.1.1.1 Sum of Differences

For each index, a MATLAB® program is implemented. The implementation vmethodology of these indexes exemplifies the way to develop more complex algorithms to identify patterns using techniques that use distance measures as similarity criteria. Program 4.1 shows how to calculate the sum of differences between an image and a reference pattern.