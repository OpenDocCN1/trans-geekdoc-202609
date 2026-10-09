![](bbox=[0.14, 0.08, 0.9, 0.46])

**Fig. 3.10:** Recognition rate in the YALE library.

recognition algorithm, the recognition efficiency of symplectic group classification algorithm is high.

In the process of recognising the image, we use the symplectic group classification algorithm to use multiple images as the training samples. Here, we give the recognition rate of the symplectic group classification algorithm using only one image as the training sample and other images as the test sample. Through the recognition process, we find that, even with only one image as a training example, the symplectic group classifier algorithm has a higher recognition accuracy. This is because, for an image, the image processed by the symplectic classification algorithm obtains the feature vector of the image, and the feature vector is stable for different images of the same face. Tables 3.3 and 3.4 give the performance comparison of several classification algorithms on the ORL and YALE libraries in the case of only one training sample [36, 37].

**Tab. 3.3:** Performance comparison of several algorithms on ORL Library.

| Classification algorithm | Number of training samples | Average recognition accuracy (%) |
| :--- | :--- | :--- |
| Symplectic group | 1 | 92.6 |
| Spectroface | 1 | 90.8 |
| Linear subspace | 1 | 84.2 |