computed, and the length of the latent factors is \( k \)). Rearrangement of the third term can reduce the time complexity to \( O(kn) \), which is linear.

\(\sum_{i=1}^n \sum_{j=i+1}^n \langle \mathbf{v}_i, \mathbf{v}_j \rangle x_i x_j\)
\(= \frac{1}{2} \sum_{i=1}^n \sum_{j=i+1}^n \langle \mathbf{v}_i, \mathbf{v}_j \rangle x_i x_j - \frac{1}{2} \sum_{i=1}^n \langle \mathbf{v}_i, \mathbf{v}_i \rangle x_i x_i \text{ (upper triangle – diagonal entry)}\)
\(= \frac{1}{2} \left( \sum_{i=1}^n \sum_{j=1}^n \sum_{f=1}^k v_{i,f} v_{j,f} x_i x_j - \sum_{i=1}^n \sum_{f=1}^k v_{i,f} v_{i,f} x_i x_i \right) \text{ (expanding the dot product)}\)
\(= \frac{1}{2} \sum_{f=1}^k \left( \left( \sum_{i=1}^n v_{i,f} x_i \right) \left( \sum_{j=1}^n v_{j,f} x_j \right) - \sum_{i=1}^n v_{i,f}^2 x_i^2 \right) \text{ (factor out the feature summation)}\)
\(= \frac{1}{2} \sum_{f=1}^k \left( \left( \sum_{i=1}^n v_{i,f} x_i \right)^2 - \sum_{i=1}^n v_{i,f}^2 x_i^2 \right)\)

For sparse features, only nonzero elements need to be computed so that the overall complexity is linear to the number of nonzero features.

The final model can be written as

\(\hat{y}(x) = w_0 + \sum_{i=1}^n w_i x_i + \frac{1}{2} \sum_{f=1}^k \left( \left( \sum_{i=1}^n v_{i,f} x_i \right)^2 - \sum_{i=1}^n v_{i,f}^2 x_i^2 \right) \quad (6.1)\)

# 6.5.3 Implementation of Deep Factorization Machine in Tensorflow

# Warning

I used the following versions of the Python packages on M1 MacBookPro 2021 to build the exercise on DeepFM. Specifically, older versions of `pandas` may throw errors when loading the data or may handle the unicode characters incorrectly.

```
python==3.10.6
numpy==1.24.3
pandas==2.1.1
tensorflow==2.13.0
keras==2.13.1
```

We use Keras API in Tensorflow to implement the Deep Factorization Machine (DeepFM) [Guo et al., 2017] algorithm. This is a simple modification of the FM algorithm by adding a deep neural network component to help predict the final