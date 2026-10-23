What upsample does is just transfer the delta to the convolutional layer:

```
```java
public double[][][][] upsample(double[][][][] X, double[][][][] Y,
double[][][][] dY, int minibatchSize) {

    double[][][][] dX = new double[minibatchSize][nKernel]
    [convolvedSize[0]][convolvedSize[1]];

    for (int n = 0; n < minibatchSize; n++) {

        for (int k = 0; k < nKernel; k++) {
            for (int i = 0; i < pooledSize[0]; i++) {
                for (int j = 0; j < pooledSize[1]; j++) {

                    for (int s = 0; s < poolSize[0]; s++) {
                        for (int t = 0; t < poolsize[1]; t++) {

                            double d_ = 0.;

                            if (Y[n][k][i][j] == X[n][k]
[poolSize[0]*i+s][poolSize[1]*j+t]) {
                                d_ = dY[n][k][i][j];
                            }

                            dX[n][k][poolSize[0]*i+s][poolSize[1]*j+t]
= d_;
                        }
                    }
                }
            }
        }
    }

    return dX;
}
```
```

In deconvolve, we need to update the model parameter. Since we train the model with mini-batches, we calculate the summation of the gradients first:

```
```java
// calc gradients of W, b
for (int n = 0; n < minibatchSize; n++) {
    for (int k = 0; k < nKernel; k++) {

        for (int i = 0; i < convolvedSize[0]; i++) {
```
```