# Example: Google Translate example for English to Czech.

Now for we consider our Google Translate example. Here we are translating English to Czech. Remember in Czech gender matters. By changing Boy into Girl in Czech we need to change gender related word. Here RNN works as follows:

+   - If it is Boy then Memory flows freely in the memory pipeline.
- If it is Girl (or female name 'Amanda') Sigmoid-layer-function can detect and Forget-value is closed. Old memory cannot pass through the memory pipeline. Then new memory added via Memory-value.
- In addition we have extracted gender and other data (Capitalized, singular/plural, no of letters etc).
- Output-value extract the information. For example. Gender is extracted and sends this output as the next LSTM-module, that next module can act according to this Gender (change the gender related word).

# 2.2.6 Additional Readings

In terms of additional reading, you could potentially reference the original paper by our two authors who created LSTMs.

# Additional Reading:

# Long Short-Term Memory

By Sepp Hochreiter & Jurgen Schmidhuber (1997)

![](bbox=[0.445, 0.465, 0.855, 0.595])

Link:

http://www.bioinf.jku.at/publications/older/2604.pdf

If you don't wanna get deep into mathematics and into the technical stuff there's the great blog by Christopher Olah,

# Additional Reading:

# Understanding LSTM Networks

By Christopher Olah (2015)

![](bbox=[0.465, 0.758, 0.835, 0.878])

Link:

http://colah.github.io/posts/2015-08-Understanding-LSTMs/