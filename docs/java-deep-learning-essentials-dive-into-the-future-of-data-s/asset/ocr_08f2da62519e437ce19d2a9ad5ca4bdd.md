The parameters of the MLP are the weights w and bias b of the hidden layer, HiddenLayer, and the output layer, LogisticRegression. Since the output layer is the same as the one previously introduced, we won't look at the code here. The constructor of HiddenLayer is as follows:

```
```java
public HiddenLayer(int nIn, int nOut, double[][] W, double[] b, Random
rng, String activation) {

    if (rng == null) rng = new Random(1234);  // seed random

    if (W == null) {

        W = new double[nOut][nIn];
        double w_ = 1. / nIn;

        for(int j = 0; j < nOut; j++) {
            for(int i = 0; i < nIn; i++) {
                W[j][i] = uniform(-w_, w_, rng);  // initialize W with
uniform distribution
            }
        }

    }

    if (b == null) b = new double[nOut];

    this.nIn = nIn;
    this.nOut = nOut;
    this.W = W;
    this.b = b;
    this.rng = rng;

    if (activation == "sigmoid" || activation == null) {

        this.activation = (double x) -> sigmoid(x);
        this.dactivation = (double x) -> dsigmoid(x);

    } else if (activation == "tanh") {

        this.activation = (double x) -> tanh(x);
        this.dactivation = (double x) -> dtanh(x);

    } else {
```
```