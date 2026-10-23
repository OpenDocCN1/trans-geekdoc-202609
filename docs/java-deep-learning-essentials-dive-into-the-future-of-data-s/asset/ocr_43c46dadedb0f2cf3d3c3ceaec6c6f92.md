Compared to RBM, the implementation of DA is also quite simple. When you test (reconstruct) the model, you don't need to corrupt the data. As in standard neural networks, you just need to forward propagate the given inputs based on the weights of the networks:

```
public double[] reconstruct(double[] x) {
    double[] z = getHiddenValues(x);
    double[] y = getReconstructedInput(z);
    return y;
}
```

# Stacked Denoising Autoencoders (SDA)

SDA is deep neural networks with piled up DA layers. In the same way that DBN consists of RBMs and logistic regression, SDA consists of DAs and logistic regression:

![](bbox=[0.29, 0.42, 0.71, 0.75])

The flow of implementation is not that different between DBN and SDA. Even though there is a difference between RBM and DA in pre-training, the content of fine-tuning is exactly the same. Therefore, not much explanation might be needed.