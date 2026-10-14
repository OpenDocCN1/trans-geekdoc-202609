![](bbox=[0.17, 0.09, 0.79, 0.44])

Figure 11-6. The TokenAndPositionEmbedding layer adds the token embeddings to the sinusoidal position embeddings to produce the overall embedding for the sequence

# Multiple Inputs and Outputs

We now have two input streams (notes and durations) and two output streams (predicted notes and durations). We therefore need to adapt the architecture of our Transformer to cater for this.

There are many ways of handling the dual stream of inputs. We could create tokens that represent each note–duration pair and then treat the sequence as a single stream of tokens. However, this has the downside of not being able to represent note–duration pairs that have not been seen in the training set (for example, we may have seen a G#2 note and a 1/3 duration independently, but never together, so there would be no token for G#2:1/3.

Instead, we choose to embed the note and duration tokens separately and then use a concatenation layer to create a single representation of the input that can be used by the downstream Transformer block. Similarly, the output from the Transformer block is passed to two separate dense layers, which represent the predicted note and duration probabilities. The overall architecture is shown in Figure 11-7. Layer output shapes are shown with batch size b and sequence length l.