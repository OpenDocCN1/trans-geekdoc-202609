![](bbox=[0.08, 0.12, 0.92, 0.32])

FIGURE 14.2 An FDCNN model.

This can be calculated as follows:

$C(x_{u,v}) = \sum_{i=-\frac{n}{2}}^{\frac{n}{2}} \sum_{j=-\frac{m}{2}}^{\frac{m}{2}} f_k(i,j) x_{u-i,v-j} \quad (14.1)$

where $f_k$ is a filter, $n \times m$ the kernel size, and the input image is $x$.

# 14.3.3.2 Subsampling Layers

Subsampling or pooling layers shrink the map size into a smaller size. Figure 14.3 shows the example of a max-pooling layer. The following four steps implement the pooling function:

+   - Pick a window size (usually 2 or 3)
+   - Pick a stride (usually 2)
+   - Move your window across your filtered images.
+   - The maximum value is taken from each window.

![](bbox=[0.3, 0.92, 0.7, 0.96])

FIGURE 14.3 Example of max-pooling.