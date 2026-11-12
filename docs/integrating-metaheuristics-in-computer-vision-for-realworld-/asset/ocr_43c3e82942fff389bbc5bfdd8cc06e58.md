L1-regularization put together the sparse coefficients. Here, associated convolution model is developed and holds traditional structure of the neural network. More number of hidden layers can be chosen for the network but for the deeper perception five-layer network is used. Therefore, no. of nodes is same as the no. of features in the input unit. The window is set to initialize the parameters for the equal distribution and the result is verified whether the distributed data is given out properly. The window in all the layer is established as a normal distribution and sigmoid activation function is used in the input layer, hidden layer, and softmax in the output layer [22]. Since the behavior of multiclass data can be analyzed effectively using softmax. So, the no. of clusters in the dataset.

The proposed model takes an input vector x = [x₁, x₂, x₃, ..... xₙ] all the input values are matrix multiplied by its corresponding weight [23]. Therefore, the weight vector for the input data is displayed as w = [w₁, w₂, w₃, ..... wₙ] and finally the bias b is added to the weighted input vectors. To yield the efficient intervening probabilistic results all the layers are evaluated using sigmoid function which is given in Equation 19.8.

Sᵢ = f(∑ᵢ₌₁ⁿ wᵢ.xᵢ + b)

where Sᵢ - dependent variable to be predicted, wᵢ is the weight matrix, xᵢ is the feature vectors, and f is the sigmoid activation function.

f(x) = 1 / (1 + e⁻⁽ˣ·ʷᵢ⁾)

Equation 19.10 gives the evaluation result of softmax activation function

P(y = j|x) = (eˣᵀʷʲ) / (∑ₖ₌₁ᴷ eˣᵀʷⁱ)

where k {1,2,3,..n} ranges for all the clusters and xᵀwᵢ- the inner product of every feature and weight.

# 19.4 Results and Discussion

Performance metric is evaluated using MATLAB --- Deep learning framework furnished with an Intel i5 CPU. Deep learning network is used with inception v3 and parameters that were trained with our thyroid nodule image dataset. Each assortment size is 128, and each image size is 299 x 299. The optimizer used for training is adaptive moment estimation (adam). Every observation is performed for ten times, and mean value is calculated. Like the other convolution network models VGG-16 [15], LR [14], and KNN [16], voting strategy [17], Feature fusion VGG-16 [14] and Feature fusion ResNet [14] have also been utilized for comparison with the proposed method in this work.