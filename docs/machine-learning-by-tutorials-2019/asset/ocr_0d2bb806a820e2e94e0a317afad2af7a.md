# Machine Learning Chapter 16: Natural Language Transformation, Part 2

tokens. There are some tricks you can implement to reduce the computations required at this softmax level to speed up training — look up terms like "adaptive softmax" and "hierarchical softmax" for some ideas — but it's still easier to deal with fewer items.

+   2. The larger vocabulary, the larger the model. Because that increases the width of your input and output layers (at least), these layers end up contributing most of your model's trainable parameters. Mobile devices don't have the resources to deal with very large models, so it may not be feasible to support large vocabularies on.

+   3. The dreaded cursed of dimensionality. You'll hear this term lot in machine learning. It refers to the fact that, as you increase the number of input features, the possible combinations of inputs grow exponentially. (As each specific training sample covers a smaller percentage of those possibilities. The primary result: As you add features, you need to increase the size of your training set — exponentially. Now consider that each token in the vocabulary is a unique input dimension, and you will see need more training data as the size of vocabulary grows.

> Note: Here's an example of the curse of dimensionality. Consider a model that takes only one input feature — an integer from 1 to 10. There are only 10 possible inputs, so each training sample essentially covers 10% of all possible inputs this model can ever see.

Adding a second input feature — again an integer from 1 to 10 — gives you a two-dimensional input with 100 possible combinations, so each training sample now covers 1% of the possible inputs. And adding a third dimension brings the possible combinations up to 1,000, which would mean each sample covers only one tenth of 1%.

As the number of dimensions goes up, a model must train on drastically data in order to learn an accurate representation of the input space.

Secondly, with subword tokens makes it easier to deal with OOV tokens. At the byte level, you can remove the problem entirely — there will only be of 256 possible values; with characters you can delete OOV tokens and rarely lose information. With words, it becomes a difficult problem that's still an open area of research. You'll read more about it in the next section.

![](bbox=[0.159, 0.923, 0.836, 0.956])