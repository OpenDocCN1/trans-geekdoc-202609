use a binary feature indicating whether or not the user is an adult, rather than their exact age. Thus, bucketization is a powerful feature engineering technique that helps data scientists and machine learning engineers build more efficient models. In another example, if we would like to plot a histogram given a list of values, we can first assign the continuous values in a predefined list of buckets, and then use `np.unique` to count the number of occurrences of each bin. We can also use bucketization operations to downsample float values into lower-precision integer values to compress the size of the model weights, for example. This is known as **quantization** and is a key technique to speed up model inference by sacrificing output quality due to reduced precision. Both Tensorflow [Abadi et al., 2023] and PyTorch [Paszke et al., 2023] have dedicated operations and quantization integer representations (`qint8`, `qint32`, etc.) to help the parameter quantization and model compression processes.

# ## 9.5 Segment-wise Aggregation

Although Pandas is the best-known library for the groupby-aggregate-apply pattern, more basic numerical libraries including NumPy as well as deep-learning-oriented ones like Tensorflow and PyTorch also implement operations to facilitate the use of this pattern for data transformation. More specifically, these are called segment operations, where, in general,

+   \* Sequences of elements of variable lengths are arranged along a single dimension.
+   \* An array of integers labels the group identity of the segments.
+   \* Elements within the group are aggregated together by a reduction operation, such as summation.

See Figure 9.12 for an illustration of an example of segment-wise summation operations. Table 9.2 provides a list of segment operations in NumPy, Tensorflow, and PyTorch.

![](bbox=[0.13, 0.7, 0.65, 0.85])

**Figure 9.12** Illustration of segment-wise summation operation, with each color indicating a segment/group of values. There are two ways to denote the segment, either through sequence index or segment id.