# Autoregressive Models

# Chapter Goals

In this chapter you will:

+   - Learn why autoregressive models are well suited to generating sequential data such as text.
+   - Learn how to process and tokenize text data.
+   - Learn about the architectural design of recurrent neural networks (RNNs).
+   - Build and train a long short-term memory network (LSTM) from scratch using Keras.
+   - Use the LSTM to generate new text.
+   - Learn about other variations of RNNs, including gated recurrent units (GRUs) and bidirectional cells.
+   - Understand how image data can be treated as a sequence of pixels.
+   - Learn about the architectural design of a PixelCNN.
+   - Build a PixelCNN from scratch using Keras.
+   - Use the PixelCNN to generate images.

So far, we have explored two different families of generative models that have both involved latent variables—variational autoencoders (VAEs) and generative adversarial networks (GANs). In both cases, a new variable is introduced with a distribution that is easy to sample from and the model learns how to *decode* this variable back into the original domain.