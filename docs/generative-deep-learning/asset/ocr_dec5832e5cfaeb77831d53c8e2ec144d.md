+   3. The encoding is passed through a TransformerBlock.
+   4. The transformed output is passed through a Dense layer with softmax activation to predict a distribution over the subsequent word.
+   5. The Model takes a sequence of word tokens as input and outputs the predicted subsequent word distribution. The output from the Transformer block is also returned so that we can inspect how the model is directing its attention.
+   6. The model is compiled with SparseCategoricalCrossentropy loss over the predicted word distribution.

# Analysis of GPT

Now that we have compiled and trained our GPT model, we can start to use it to generate long strings of text. We can also interrogate the attention weights that are output from the TransformerBlock, to understand where the Transformer is looking for information at different points in the generation process.

# Generating text

We can generate new text by applying the following process:

+   1. Feed the network with an existing sequence of words and ask it to predict the following word.
+   2. Append this word to the existing sequence and repeat.

The network will output a set of probabilities for each word that we can sample from, so we can make the text generation stochastic, rather than deterministic.

We will use the same TextGenerator class introduced in Chapter 5 for LSTM text generation, including the temperature parameter that specifies how deterministic we would like the sampling process to be. Let’s take a look at this in action, at two different temperature values (Figure 9-10).