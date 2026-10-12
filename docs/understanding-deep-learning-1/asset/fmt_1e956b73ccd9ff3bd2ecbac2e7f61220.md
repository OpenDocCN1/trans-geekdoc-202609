
## Problems 4.8–4.11

***

[Figure 4.7a](#c004.xhtml#c4-fig-0007) shows how the maximum number of linear regions increases as a function of the number of parameters for networks mapping scalar input `x` to scalar output `y`. Deep neural networks create much more complex functions for a fixed parameter budget. This effect is magnified as the number of input dimensions `D[i]` increases ([figure 4.7b](#c004.xhtml#c4-fig-0007)), although computing the maximum number of regions is less straightforward.

![Figure 4.7 The maximum number of linear regions for neural networks increases rapidly with the network depth. a) Network with Di = 1 input. Each curve represents a fixed number of hidden layers K, as we vary the number of hidden units D per layer. For a fixed parameter budget (horizontal position), deeper networks produce more linear regions than shallower ones. A network with K = 5 layers and D = 10 hidden units per layer has 471 parameters (highlighted point) and can produce 161,051 regions. b) Network with Di = 10 inputs. Each subsequent point along a curve represents ten hidden units. Here, a model with K = 5 layers and D = 50 hidden units per layer has 10,801 parameters (highlighted point) and can create more than 10134 linear regions.](images/c4-fig-0007.jpg)

[Figure 4.7](#c004.xhtml#c4-fig-0007a) The maximum number of linear regions for neural networks increases rapidly with the network depth. a) Network with `D[i]` = 1 input. Each curve represents a fixed number of hidden layers `K`, as we vary the number of hidden units `D` per layer. For a fixed parameter budget (horizontal position), deeper networks produce more linear regions than shallower ones. A network with `K` = 5 layers and `D` = 10 hidden units per layer has 471 parameters (highlighted point) and can produce 161,051 regions. b) Network with `D[i]` = 10 inputs. Each subsequent point along a curve represents ten hidden units. Here, a model with `K` = 5 layers and `D` = 50 hidden units per layer has 10,801 parameters (highlighted point) and can create more than `10^(134)` linear regions.

This seems attractive, but the flexibility of the functions is still limited by the number of parameters. Deep networks can create extremely large numbers of linear regions, but these contain complex dependencies and symmetries. We saw some of these when we considered deep networks as "folding" the input space ([figure 4.3](#c004.xhtml#c4-fig-0003)). So, it's not clear that the greater number of regions is an advantage unless (i) there are similar symmetries in the real-world functions that we wish to approximate or (ii) we have reason to believe that the mapping from input to output really does involve a composition of simpler functions.

### 4.5.3 Depth efficiency

Both deep and shallow networks can model arbitrary functions, but some functions can be approximated much more efficiently with deep networks. Functions have been identified that require a shallow network with exponentially more hidden units to achieve an equivalent approximation to that of a deep network. This phenomenon is referred to as the *depth efficiency* of neural networks. This property is also attractive, but it's not clear that the real-world functions that we want to approximate fall into this category.

### 4.5.4 Large, structured inputs

We have discussed fully connected networks where every element of each layer contributes to every element of the subsequent one. However, these are not practical for large, structured inputs like images, where the input might comprise ~`10⁶` pixels. The number of parameters would be prohibitive, and moreover, we want different parts of the image to be processed similarly; there is no point in independently learning to recognize the same object at every possible position in the image.

The solution is to process local image regions in parallel and then gradually integrate information from increasingly large regions. This kind of local-to-global processing is difficult to specify without using multiple layers (see chapter 10).

### 4.5.5 Training and generalization

A further possible advantage of deep networks over shallow networks is their ease of fitting; it is usually easier to train moderately deep networks than to train shallow ones (see figure 20.2). It may be that over-parameterized deep models have a large family of roughly equivalent solutions that are easy to find. However, as we add more hidden layers, training becomes more difficult again, although many methods have been developed to mitigate this problem (see chapter 11).

Deep neural networks also seem to generalize to new data better than shallow ones. In practice, the best results for most tasks have been achieved using networks with tens or hundreds of layers. Neither of these phenomena are well understood, and we return to them in chapter 20.

## 4.6 Summary

In this chapter, we first considered what happens when we compose two shallow networks. We argued that the first network "folds" the input space, and the second network then applies a piecewise linear function. The effects of the second network are duplicated where the input space is folded onto itself.

We then showed that this composition of shallow networks is a special case of a deep network with two layers. We interpreted the `ReLU` functions in each layer as clipping the input functions in multiple places and creating more "joints" in the output function. We introduced the idea of hyperparameters, which for the networks we've seen so far, comprise the number of hidden layers and the number of hidden units in each.

Finally, we compared shallow and deep networks. We saw that (i) both networks can approximate any function given enough capacity, (ii) deep networks produce many more linear regions per parameter, (iii) some functions can be approximated much more efficiently by deep networks, (iv) large, structured inputs like images are best processed in multiple stages, and (v) in practice, the best results for most tasks are achieved using deep networks with many layers.

Now that we understand deep and shallow network models, we turn our attention to training them. In the next chapter, we discuss loss functions. For any given parameter values `ϕ`, the loss function returns a single number that indicates the mismatch between the model outputs and the ground truth predictions for a training dataset. In chapters 6 and 7, we deal with the training process itself, in which we seek the parameter values that minimize this loss.

## Notes

**Deep learning:** It has long been understood that it is possible to build more complex functions by composing shallow neural networks or developing networks with more than one hidden layer. Indeed, the term "deep learning" was first used by Dechter (1986). However, interest was limited due to practical concerns; it was not possible to train such networks well. The modern era of deep learning was kick-started by startling improvements in image classification reported by Krizhevsky et al. (2012). This sudden progress was arguably due to the confluence of four factors: larger training datasets, improved processing power for training, the use of the `ReLU` activation function, and the use of stochastic gradient descent (see chapter 6). LeCun et al. (2015) present an overview of early advances in the modern era of deep learning.
