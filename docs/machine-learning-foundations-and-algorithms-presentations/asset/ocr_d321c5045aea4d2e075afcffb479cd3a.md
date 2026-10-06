# # Recap: Recurrent Models as Attention Models

![](bbox=[0.171, 0.175, 0.793, 0.626])

+   - Encoder recurrently produces hidden representations of input word sequence
- Decoder recurrently generates output word sequence

+     - For each output word the decoder uses a weighted average of the hidden input representations as input “context”, along with the recurrent hidden state and the previous output word