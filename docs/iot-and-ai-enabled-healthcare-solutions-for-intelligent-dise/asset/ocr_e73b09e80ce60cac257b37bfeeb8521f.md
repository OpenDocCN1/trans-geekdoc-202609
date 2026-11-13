# Convolutional Layers

# 1. Function:

+   CNN’s fundamental building components are called convolutional layers.
+   They carry out convolution operations, which generate feature maps by
+   swiping a filter (or kernel) across the input data.

# 2. Operation:

+   Filters: Small matrices (such as 3 × 3 or 5 × 5) that are applied to the input
+   data are known as filters or kernels. Unique features, including edges, textures,
+   or patterns, are detected by different filters.

+   Stride: The filter’s step size as it passes through the input. Greater steps
+   decrease the resulting feature map’s spatial dimensions.

+   Padding: Increasing the number of pixels surrounding the input border to
+   regulate the output’s spatial dimensions. “Same” (padding to retain input size)
+   and “valid” (no padding) are common kinds [11].

# 3. Output:

+   The result of a convolution operation is a feature map, which highlights the
+   presence of specific features detected by the filters.

# Pooling Layers

# 1. Function:

+   Pooling layers reduce the spatial dimensions of the feature maps, retaining
+   the most significant information while decreasing the computational load and
+   reducing overfitting.

# 2. Types of Pooling:

+   Max Pooling: Selects the maximum value from each region of the feature
+   map. Commonly used for its ability to capture the most prominent features.

+   Average Pooling: Computes the average value of each region. Less common
+   than max pooling but useful in certain contexts.

# 3. Operation:

+   Pooling Size: The dimensions of the pooling window (e.g., 2 × 2, 3 × 3).

+   Stride: The step size for moving the pooling window across the feature map.

# 4. Output:

+   A down sampled feature map that retains the most notable features while
+   reducing spatial dimensions.

# Fully Connected Layers

# 1. Function:

+   Fully connected (FC) layers connect every neuron in one layer to every neuron
+   in the next layer. They are used at the end of the CNN to perform high-level
+   reasoning and classification.