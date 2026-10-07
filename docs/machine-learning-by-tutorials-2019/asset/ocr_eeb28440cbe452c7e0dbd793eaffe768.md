# Machine Learning Chapter 15: Natural Language Transformation, Part 1

It shows encoder_in feeds into encoder_mask, which feeds into encoder_lstm, and the final layer outputs two 256 vectors. These are all layers you created earlier to train seq2seq_model, just repurposed in a new Model object.

You've isolated the encoder, so now do so for the decoder. Run the following code:

```
# 1
inf_dec_h = Input(shape=(latent_dim),name="decoder_h_in"
inf_dec_c = Input(shape=(latent_dim),name="decoder_c_in"
# 2
inf_dec_lstm_out, inf_dec_h_out, inf_dec_c_out = decoder_lstm(
decoder_in, initial_state=[inf_dec_h_in, inf_dec_c_in])
# 3
inf_dec_out = decoder_dense(inf_dec_lstm_out)
# 4
inf_model = Model(
[decoder_in, inf_dec_h_in, inf_dec_c_in],
[inf_dec_out, inf_dec_h_out, inf_dec_c_out])
```

This looks a lot more complicated than you did for the encoder, it's really a little more complicated. Go through it by step:

+   1. You create two new inputs the same shapes as the decoder's two outputs — inf_dec_h_in and inf_dec_c_in.(The names are getting longer so we're abbreviating heavily now). Remember how in the full seq2seq model, the decoder's initial state came directly from the encoder. For this new model, you'll provide the initial state programmatically, and you'll use these inputs to do it.

+   2. Here, you connect the new inputs as the initial state for your trained LSTM layer, along with the original decoder_in that gives you the decoder one-hot encoded sequence. You passed entire decoders to decoder_in while training seq2seq_model, but during inference you'll only get the most predicted character for each prediction. You also grab the LSTM's state outputs as inf_dec_h_out and inf_dec_c_out, rather than discard them like you did in seq2seq_model. You'll pass these outputs from one prediction to the next one.

+   3. This line connects the new output from the LSTM to the dense layer you trained earlier, giving you a new output layer for the decoder model.

+   4. Finally, you build the new decoder Model. Notice it includes outputs from different layers in the network — the dense layer's character probabilities and the LSTM's output states. There's nothing about neural networks that says the outputs can only come from the last layer!

![](bbox=[0.166, 0.92, 0.833, 0.953])