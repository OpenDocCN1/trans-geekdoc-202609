# 194 Hardware architectures for deep learning

# 9.2 Background on CNN

CNNs are constructed from multiple computational layers formed as directed acyclic graph (DAG) [8,9]. Each layer extracts an abstraction of data provided in the previous layer, called a feature map (fmap). Most common layers are pooling (POOL), convolution (CONV) and FC.

In CONV layers, as illustrated in Figure 9.3, two-dimensional (2-D) filters slide over the input images/feature-maps (Ifmaps) performing convolution operation to extract feature characteristics from local regions and generating images/feature-maps (Ofmaps).

Equation (9.1) illustrates how the CONV layer is being computed:

```
$$(C-1) (R-1) (R-1)\nOf[z]u[x][y] = Bias[u] + \sum_{k=0}^{C-1} \sum_{i=0}^{R-1} \sum_{j=0}^{R-1} f[z][k][Ux+i][Uy+j]W[u][k][l][j]$$
```

```
$0 \le z \le N; 0 \le u \le M; 0 \le x, y \le E; E = \frac{H-R+U}{U}$$
```

where Of is the Ofmap, If is the Ifmap, W is the filter weight vector and Bias is a 1-D bias that is added to the results.

Computation of CONV layer in popular CNNs accounts for more than 90% of the overall operations and requires a large amount of data movement and memory operations [10]. In addition, the large size of Ifmaps, Ofmaps and partial results, which are generated during the CONV processing, increases the memory requirements and requires large portion of the accelerator hardware

![](bbox=[0.082, 0.613, 0.967, 0.873])

Figure 9.3 Computing one CONV layer using input Ifmap/image and filters to produce the output (Ofmaps)