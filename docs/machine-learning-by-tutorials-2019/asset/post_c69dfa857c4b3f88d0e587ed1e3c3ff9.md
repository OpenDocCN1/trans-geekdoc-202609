
# Inference with sequence-to-sequence models

The model you've trained so far isn't actually useful for inference — at least, not in
Current current form. Why is that? Because the decoder portion of the model requires the correctly translated text as one of its inputs! What good is a translation model that needs you to do the translations?

But don't worry: You won't have to throw out all your hard work. The model has learned something useful, you just have to access it a different way.

First, separate the encoder and decoder into two models. Keras makes this easy. declare a new Model and pass the input and output layers you want to use, like this:

```
inf_encoder = Model(encoder_in, [encoder_h, encoder_c])
```

Running a cell with the above code creates a new encoder model called inf_encoder, for "inference encoder". It uses the same input layer and encoder state output layers that you created earlier: encoder_in, encoder_h and encoder_c. Keras maintains a graph of layer connections, so it automatically adds to this Model any existing layers to connect these inputs and outputs. This means you're actually using the same LSTM and Masking layers that you trained as part of seq2seq_model, too. In essence, inf_encoder accesses only the encoder portion of your trained model.

You can run the summary function to see what Keras actually built:

```
inf_encoder.summary()
```

Which produces the following output:

| Layer (type) | Output Shape | Param # |
|---|---|---|
| encoder_in (InputLayer) | (None, None, 101) | 0 |
| encoder_mask (Masking) | (None, None, 101) | 0 |
| encoder_lstm (LSTM) | ((None, 256), (None, 256)) | 366592 |
| Total params: 366,592 | | |
| Trainable params: 366,592 | | |
| Non-trainable params: 0 | | |

Keras encoder model for inference

# Machine Learning Chapter 15: Natural Language Transformation, Part 1

It shows encoder_in feeds into encoder_mask, which feeds into encoder_lstm, and the final layer outputs two 256 vectors. These are all layers you created earlier to train seq2seq_model, just repurposed in a new Model object.

You've isolated the encoder, so now do so for the decoder. Run the following code:

```
# 1
inf_dec_h = Input(shape=(latent_dim),name="decoder_h_in")
inf_dec_c = Input(shape=(latent_dim),name="decoder_c_in")
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

- 1. You create two new inputs the same shapes as the decoder's two outputs — inf_dec_h_in and inf_dec_c_in.(The names are getting longer so we're abbreviating heavily now). Remember how in the full seq2seq model, the decoder's initial state came directly from the encoder. For this new model, you'll provide the initial state programmatically, and you'll use these inputs to do it.
- 2. Here, you connect the new inputs as the initial state for your trained LSTM layer, along with the original decoder_in that gives you the decoder one-hot encoded sequence. You passed entire decoders to decoder_in while training seq2seq_model, but during inference you'll only get the most predicted character for each prediction. You also grab the LSTM's state outputs as inf_dec_h_out and inf_dec_c_out, rather than discard them like you did in seq2seq_model. You'll pass these outputs from one prediction to the next one.
- 3. This line connects the new output from the LSTM to the dense layer you trained earlier, giving you a new output layer for the decoder model.
- 4. Finally, you build the new decoder Model. Notice it includes outputs from different layers in the network — the dense layer's character probabilities and the LSTM's output states. There's nothing about neural networks that says the outputs can only come from the last layer!

![](img/5720be5c3cca252e12448e68d25607b5_503_0.png)

# Machine Learning Chapter 15: Natural Language Transformation, Part 1

Once again, the summary function shows you how Keras connected the model's layers:

```
inf_decoder.summary()
```

Which outputs this:

| Layer (type) | Output Shape | Param # | Connected to |
|---|---|---|---|
| decoder_in (InputLayer) | (None, 87) | 0 | |
| decoder_h_in (InputLayer) | (None, 256) | 0 | |
| decoder_c_in (InputLayer) | (None, 256) | 0 | |
| decoder_lstm (LSTM) | (None, 256) | 352256 | decoder_in[0][0], decoder_h_in[0][0], decoder_c_in[0][0] |
| decoder_out (Dense) | (None, 87) | 22359 | decoder_lstm[1][0] |
Total params: 374,615
Trainable params: 374,615
Non-trainable params: 0

Keras decoder model for inference

As you can see, decoder_in, decoder_h_in and decoder_c_in all flow into decoder_lstm, which in turn leads to decoder_out. Once again, the summary doesn't display all the values in the Output column, but you get the idea. You're going to write a function that translates sequences using the separate encoder and decoder models you created. Before you do, run the following code to define a few constants:

```python
max_out_seq_len = max(len(seq) for seq in samples)
start_token_idx = int2int[start_token]
stop_token_idx = int2int[stop_token]
```

The values for these three constants are all specific to this project, you'll need to think about them as well. Here's what they're for:

- max_out_seq_len: This value defines the maximum length of translation. Ideally, your decoder will predict a STOP token at some point, but this specifies how long you're willing to wait before giving up. You could choose any value here — the model has no limit to the length of sequence it can process — but this line uses the length of the longest English sentence in the training set. Because the model never got any practice creating sequences longer than this, it seems as good as any to call it.

![](img/5720be5c3cca252e12448e68d25607b5_504_0.png)

start_token_idx: This is the integer encoding of the START token. You'll need to know this to signal the decoder to start translating a new sequence.

stop_token_idx: This is the integer encoding of the STOP token. You'll need to know this because it's how the decoder signals to you that it's translating a sequence.

With these constants defined, you're ready to actually use your model to translate text. Define the following function in your notebook. It takes a one-hot encoded sequence, an encoder-decoder model pair, and returns the sequence's translation:

```python
def translate_sequence(one_hot_seq, encoder, decoder):
    # 1
    encoding = encoder.predict(one_hot_seq)
    # 2
    decoder_in = np.zeros((1, 1, vocab_size), dtype=float32)
    # 3
    translated_text = ""
    done_decoding = False
    decoded_idx = start_token_idx
    while not done_decoding:
        # 4
        decoder_in[0, 0, decoded_idx] = 1
        # 5
        decoding, h, c = decoder.predict([decoder_in] + encoding)
        encoding = [h, c]
        # 7
        decoder_in[0, 0, decoded_idx] = 0
        # 8
        decoded_idx = np.argmax(decoding[0, -1], axis=-1)
        # 9
        if decoded_idx == stop_token_idx:
            done_decoding = True
        else:
            translated_text += int2token[decoded_idx]
        # 10
        if len(translated_text) >= max_out_seq_len:
            done_decoding = True
    return translated_text
```

This logic drives the translation process, so let's go over it carefully:

- 1. The function receives a NumPy array containing a one-hot encoded sequence — one_hot_seq — and passes it to encoder's predict function to process it. The encoder model passed to this function should output its LSTM's h and c states as a list, which you save as encoding.
- 2. Next, you create a NumPy array to store a one-hot encoder that you'll give the decoder. Remember from the diagrams earlier in the chapter, you'll call the decoder repeatedly with the most recently predicted character as input.
- 3. These variables keep track of so far and control the decoding loop. You'll set decoded_idx to the one-hot encoding of the decoder's most recently predicted character. However, you initialize it to the START token's index, because you trained the decoder to start decoding sequences using the encoder's output and START as the initial token.
- 4. The loop starts by one-hot encoding the current character, indicated by decoded_idx. Important: this must initially equal the index of the START token.
- 5. It predicts on the decoder, passing in the most recently predicted character and the most recent cell state. Remember, the first time through this loop, decoder_in contains the START token and encoding contains outputs from the encoder.
- 6. Next, you save the decoder's h and c states as encoding. You'll pass these back to the decoder as inputs to predict the next character.
- 7. Finally, you clear the one-hot index, now decoder_in contains all zeros once again.
- 8. The decoder doesn't return a character. Instead, it returns a probability distribution over all possible characters. So which one do you choose? Here you take a greedy approach and always choose the character predicted with the highest probability. This isn't necessarily the best approach, which you'll read about later.
- 9. Given the index of the predicted character, you check to see if it's the STOP token. If so, the translation is complete and you stop the loop. Otherwise, you convert the index to text and add it to the translation.
- 10. The final check ensures the loop doesn't go forever, by stopping it if the translation length reaches its limit.

![](img/5720be5c3cca252e12448e68d25607b5_506_0.png)
