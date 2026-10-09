![](bbox=[0.35, 0.09, 0.74, 0.1])

Please run the code and answer the following questions:

+   In MaxPool2D(2,2), what are the parameters used for? .

+   After running line 8, what is the resulting tensor shape? .

+   Why does line 20 exist at all? .

+   In line 9, there is a MaxPool2D(2,2) operation, followed by yet a second MaxPool2D(2,2). What is the resulting tensor shape after running line 9? and line 10?

+   A friend who saw the PyTorch implementation, suggests that lines 9 and 10 may be replaced by a single MaxPool2D(4,4,) operation while producing the exact same results. Do you agree with him? Amend the code and test your assertion .

Batch normalization, Gaussian PDF

Recommended readings for this topic are “ *Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift* ” [16] and “ *Delving deep into rectifiers: Surpassing human-level performance on imagenet classification* ” [14] .

A discussion of batch normalization (BN) would not be complete without a discussion of the Gaussian normal distribution. Though it would be instructive to develop the forward and backwards functions for a BN operation from scratch, it would also be quite complex. As an alternative we discuss several aspects of the BN operation while expanding on the Gaussian distribution.

The Gaussian distribution

# PRB-241 CH.PRB- 8.65.

+   What is batch normalization? .