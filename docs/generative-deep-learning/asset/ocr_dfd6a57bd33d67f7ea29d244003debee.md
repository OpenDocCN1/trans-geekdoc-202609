![](bbox=[0.15, 0.08, 0.82, 0.58])

Figure 9-13. An encoder-decoder Transformer model: each gray box is a Transformer block (source: Vaswani et al., 2017)

Much of this diagram is already familiar to us—we can see the Transformer blocks being repeated and positional embedding being used to capture the ordering of the input sequences. The two key differences between this model and the GPT model that we built earlier in the chapter are as follows:

+   - On the lefthand side, a set of *encoder* Transformer blocks encode the sequence to be translated. Notice that there is no causal masking on the attention layer. This is because we are not generating further text to extend the sequence to be translated; we just want to learn a good representation of the sequence as a whole that can be fed to the decoder. Therefore, the attention layers in the encoder can be completely unmasked to capture all the cross-dependencies between words, no matter the order.