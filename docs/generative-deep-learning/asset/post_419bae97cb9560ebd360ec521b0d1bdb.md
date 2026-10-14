
![](img/f0f0f5d89818fdddf117bbe758ac8143_169_0.png)

Figure 5-6. An LSTM cell

- 1. $f_t = \sigma(W_f \cdot [h_{t-1}, x_t] + b_f)$
- 2. $i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i)$
- 3. $\tilde{C}_t = \tanh(W_C \cdot [h_{t-1}, x_t] + b_C)$
- 4. $C_t = f_t * C_{t-1} + i_t * \tilde{C}_t$
- 5. $o_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o)$
- 6. $h_t = o_t * \tanh(C_t)$

2. The concatenated vector is also passed through an *input* gate that, like the forget gate, is a dense layer with weights matrix $W_i$, bias $b_i$, and a sigmoid activation function. The output from this gate, $i_t$, has length equal to the number of units in the cell and contains values between 0 and 1 that determine how much new information will be added to the previous cell state, $C_{t-1}$.

3. The concatenated vector is passed through a dense layer with weights matrix $W_C$, bias $b_C$, and a tanh activation function to generate a vector $\tilde{C}_t$ that contains the new information that the cell wants to consider keeping. It also has length equal to the number of units in the cell and contains values between -1 and 1.

4. $f_t$ and $C_{t-1}$ are multiplied element-wise and added to the element-wise multiplication of $i_t$ and $\tilde{C}_t$. This represents forgetting parts of the previous cell state and then adding new relevant information to produce the updated cell state, $C_t$.

5. The concatenated vector is passed through an *output* gate: a dense layer with weights matrix $W_o$, bias $b_o$, and a sigmoid activation. The resulting vector, $o_t$, has length equal to the number of units in the cell and stores values between 0 and 1 that determine how much of the updated cell state, $C_t$, to output from the cell.

6. oₜ is multiplied element-wise with the updated cell state, Cₜ, after a tanh activation has been applied to produce the new hidden state, hₜ.

![](img/f0f0f5d89818fdddf117bbe758ac8143_170_0.png)

## The Keras LSTM Layer

All of this complexity is wrapped up within the LSTM layer type in Keras, so you don’t have to worry about implementing it yourself!

## Training the LSTM

The code to build, compile, and train the LSTM is given in Example 5-8.

### Example 5-8. Building, compiling, and training the LSTM

```
inputs = layers.Input(shape=(None,), dtype="int32") ①
x = layers.Embedding(10000, 100)(inputs) ②
x = layers.LSTM(128, return_sequences=True)(x) ③
outputs = layers.Dense(10000, activation = 'softmax')(x) ④
lstm = models.Model(inputs, outputs) ⑤

loss_fn = losses.SparseCategoricalCrossentropy()
lstm.compile("adam", loss_fn) ⑥
lstm.fit(train_ds, epochs=25) ⑦
```

① The Input layer does not need us to specify the sequence length in advance (it can be flexible), so we use None as a placeholder.

② The Embedding layer requires two parameters, the size of the vocabulary (10,000 tokens) and the dimensionality of the embedding vector (100).

③ The LSTM layers require us to specify the dimensionality of the hidden vector (128). We also choose to return the full sequence of hidden states, rather than just the hidden state at the final timestep.

④ The Dense layer transforms the hidden states at each timestep into a vector of probabilities for the next token.

⑤ The overall Model predicts the next token, given an input sequence of tokens. It does this for each token in the sequence.

⑥ The model is compiled with SparseCategoricalCrossentropy loss—this is the same as categorical cross-entropy, but is used when the labels are integers rather than one-hot encoded vectors.

⑦ The model is fit to the training dataset.

```
Epoch 1/25
628/629 [===========================>.] - ETA: 0s - loss: 4.4536
generated text:
recipe for mold salad are high 8 pickled to fold cook the dish into and warm in baking reduced but halves beans and cut

629/629 [==============================] - 29s 43ms/step - loss: 4.4527
Epoch 2/25
628/629 [===========================>.] - ETA: 0s - loss: 3.2339
generated text:
recipe for racks – up-don with herb fizz | serve checking thighs onto sanding butter and baking surface in a heavy heavy large saucepan over blender ; stand overnight . [UNK] over moderate heat until very blended , garlic , about 8 minutes . cook airtight until cooked are soft seeds , about 145 minutes . sugar , until s is brown , 5 to sliced , parmesan , until browned and add extract . wooden crumb to outside of out sheets . flatten and preheated return to the paste . add in pecans oval and let transfer day .

629/629 [==============================] - 30s 48ms/step - loss: 2.3336
Epoch 3/25
629/629 [==============================] - ETA: 0s - loss: 2.6229
generated text:
recipe for grilled chicken | preheat oven to 400°F . cook in large 8 – caramel grinder or until desired are firm , about 6 minutes

629/629 [==============================] - 27s 42ms/step - loss: 2.6229
Epoch 4/25
629/629 [==============================] - ETA: 0s - loss: 2.3426
generated text:
recipe for pizza salad with sweet red pepper and star fruit | combine all ingredients except lowest ingredients in a large skillet . working with batches and deglair , cook until just cooked through , about 1 minute . meanwhile , boil potatoes and paprika in a little oil over medium – high heat , stirring it just until crisp , about 3 minutes . stir in bell pepper , onion and cooked paste and jalapeno until clams well after most – reggiano , about 5 minutes . transfer warm 2 tablespoons flesh of eggplants to medium bowl . serve .
```

Figure 5-7. The first few epochs of the LSTM training process

![](img/f0f0f5d89818fdddf117bbe758ac8143_171_0.png)

Figure 5-8. The cross-entropy loss metric of the LSTM training process by epoch

## Analysis of the LSTM

Now that we have compiled and trained the LSTM, we can start to use it to generate long strings of text by applying the following process:

- 1. Feed the network with an existing sequence of words and ask it to predict the following word.
- 2. Append this word to the existing sequence and repeat.

The network will output a set of probabilities for each word that we can sample from. Therefore, we can make the text generation stochastic, rather than deterministic. Moreover, we can introduce a temperature parameter to the sampling process to indicate how deterministic we would like the process to be.

![](img/f0f0f5d89818fdddf117bbe758ac8143_172_0.png)

## The Temperature Parameter

A temperature close to 0 makes the sampling more deterministic (i.e., the word with the highest probability is very likely to be chosen), whereas a temperature of 1 means each word is chosen with the probability output by the model.

This is achieved with the code in Example 5-9, which creates a callback function that can be used to generate text at the end of each training epoch.

### Example 5-9. The TextGenerator callback function

```
class TextGenerator(callbacks.Callback):
    def __init__(self, index_to_word, top_k=10):
        self.index_to_word = index_to_word
        self.word_to_index = {
            word: index for index, word in enumerate(index_to_word)
        } ①

    def sample_from(self, probs, temperature): ②
        probs = probs ** (1 / temperature)
        probs = probs / np.sum(probs)
        return np.random.choice(len(probs), p=probs), probs

    def generate(self, start_prompt, max_tokens, temperature):
        start_tokens = [
            self.word_to_index.get(x, 1) for x in start_prompt.split()
        ] ③
        sample_token = None
        info = []
        while len(start_tokens) < max_tokens and sample_token != 0: ④
            x = np.array([start_tokens])
            y = self.model.predict(x) ⑤
```

```
sample_token, probs = self.sample_from(y[0][-1], temperature)
info.append({'prompt': start_prompt, 'word_probs': probs})
start_tokens.append(sample_token)
start_prompt = start_prompt + ' ' + self.index_to_word[sample_token]
print(f"\ngenerated text:\n{start_prompt}\n")
return info

def on_epoch_end(self, epoch, logs=None):
    self.generate("recipe for", max_tokens = 100, temperature = 1.0)
```

- 1. Create an inverse vocabulary mapping (from word to token).
- 2. This function updates the probabilities with a temperature scaling factor.
- 3. The start prompt is a string of words that you would like to give the model to start the generation process (for example, recipe for). The words are first converted to a list of tokens.
- 4. The sequence is generated until it is max_tokens long or a stop token (0) is produced.
- 5. The model outputs the probabilities of each word being next in the sequence.
- 6. The probabilities are passed through the sampler to output the next word, parameterized by temperature.
- 7. We append the new word to the prompt text, ready for the next iteration of the generative process.

Let's take a look at this in action, at two different temperature values (Figure 5-9).

```
temperature = 1.0
generated text:
recipe for sour japanese potatoes julienne | in a bowl stir together the yeast mixture with the milk and the peanut butter crumbs , the sour cream , and the butter mixture with a fork , gently fold in the prunes gently or until incorporated . lightly stir the oil and yeast until it just holds soft peaks , but not runny , on bottom of a 7 - sided sheet of aluminum foil , top it with a round , and a pinch of each brownies into a goblet , or with the baking dish . serve each with sorbet
```

```
temperature = 0.2
generated text:
recipe for grilled chicken with mustard - herb sauce | combine first 6 ingredients in medium bowl . add chicken to pot . add chicken and turn to coat . cover and refrigerate at least 1 hour and up to 1 day . preheat oven to 450°F . place turkey on rock in roasting pan . roast until thermometer inserted into thickest part of thigh registers 175°F , about 1 hour longer . transfer to rack in center of oven and preheat to 450°F . brush chicken with oil . sprinkle with salt and pepper . roast until thermometer inserted into
```

Figure 5-9. Generated outputs at temperature = 1.0 and temperature = 0.2
