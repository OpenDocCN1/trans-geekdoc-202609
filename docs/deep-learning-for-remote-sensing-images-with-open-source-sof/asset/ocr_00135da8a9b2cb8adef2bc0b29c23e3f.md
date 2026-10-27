After this step, you should have the following data that will be referred as *the validation dataset*:

+   - *Sentinel-2_B4328_10m_patches_B.tif*
+   - *Sentinel-2_B4328_10m_labels_B.tif*

# A note on pixel interleave

To keep things simple, sampled patches are stored in one single big image that stacks all patches in rows. There are multiple advantages to this. First, accessing one unique big file is more efficient than working on thousands of separate small files stored in the file system, or accessing sparsely located patches in large images. Secondly, we can visualize/process patches as any image: for instance, we can import the big patch image in QGIS and check that our patches look good. Thirdly, the interleave of the sampled source is preserved, which guarantees good performance during data access.

# 5.3 Training

How do you train a deep net? To begin with something easy, we will train a small existing model. We focus on a CNN that inputs our 16 × 16 × 4 patches and produces the prediction of an output class among 6 labels ranging from 0 to 5 (see table 4.2 for class descriptions).

# 5.3.1 Principle

In this section, we supply a short overview of the basic concepts for the training of deep learning models. Model training usually involves a gradient descent (in the network weights space) of a loss function that typically expresses the gap between estimated and reference data. The **batch** size defines the number of samples that will be propagated through the network to average the gradient at each step. Suppose that we have *N* training samples and we want to use a batch size of *n*. During learning, the first *n* samples (from 1 to *n*) will be used to train the network. Then, the second *n* samples (from *n* + 1 to 2*n*) will be used to train the network again. This procedure is repeated until all samples are propagated through the network (this is called one **epoch**). At each step, the gradient is computed over the batch, and the network weights are updated accordingly to the chosen optimization method.

Using a batch size that is smaller than the number of samples enables the overall training procedure to require less memory, which is useful for a big dataset. Also, the network weights are updated after each propagation.