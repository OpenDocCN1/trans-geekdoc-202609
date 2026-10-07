# Machine Learning Chapter 15: Natural Language Transformation, Part 1

output. Those features are really just the output activations from a specific layer in the network. Then you trained a new model to accept those output values as inputs and produce some new output, like a healthy/unhealthy label prediction.

The seq2seq model works in a similar way, with the encoder acting as the feature extractor and the decoder acting as the classification model. The difference here is that you're going to build and train the encoder and decoder together from scratch.

Digging a little deeper, the seq2seq model works with sequences for both inputs and outputs. That's where it gets its name - it transforms a sequence to another sequence. To accomplish this, the encoder and decoder usually rely on recurrent layers — specifically, this chapter uses the LSTM layer introduced in the sequence classification chapter.

These LSTMs aren't shown in these diagrams, but keep in mind that the boxes labeled Encoder and Decoder each represent neural networks that include such layers.

The following image gives some more details about how your model will work, showing how it will predict its first output character "H" when translating "Hola." to "Hello."

![](bbox=[0.273, 0.517, 0.726, 0.666])

Inference with seq2seq, through the first output token

As you can see, the encoder will process its input as a sequence of individual characters. Each character is labeled in the image with its timestep so it's clear what the order sees model should be. After ingesting the entire sequence, then will it pass its output on to the decoder.

You learned in the sequence classification project where LSTMs maintain that state lets them keep track of information between timesteps in a sequence. The decoder will take advantage of that fact and use the final state from the encoder's LSTM layer as the initial state for its own LSTM layer. Along with that, the decoder will also take input as a special START token. The decoder will then produce a single character