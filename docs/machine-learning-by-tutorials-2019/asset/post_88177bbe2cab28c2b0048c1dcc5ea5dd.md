
# Machine Learning

## Chapter 15: Natural Language Transformation, Part 1

```
['\é', '\'1', '\'2', '\'3', '\'4', '\'5', '\'6', '\'7', '\'8', '\'9', \
  '\\'', '\'0', '\'A', '\'B', '\'C', '\'D', '\'E', '\'F', '\'G', '\'H', '\'I', '\'J', '\'K', \
  '\'M', '\'N', '\'O', '\'P', '\'Q', '\'R', '\'S', '\'T', '\'U', '\'V', '\'W', '\'X', '\'Y', \
  \''Z', '\'z', '\'a', '\'b', '\'c', '\'d', '\'e', '\'f', '\'g', '\'h', '\'i', '\'j', '\'k', \
  \''l', '\'m', '\'n', '\'o', '\'p', '\'q', '\'r', '\'s', '\'t', '\'u', '\'v', '\'w', '\'x', \
  \''y', '\'z', '\'é', '\'í', '\'ñ', '\'ö', '\'ü', '\'ù', '\'ý', '\'ç', '\'€']
```

And running a similar line for out_vocab displays these characters:

```
['\t', '\n', '\'', \
  \''0', '\'1', '\'2', '\'3', '\'4', '\'5', '\'6', '\'7', '\'8', '\'9', '\'/', \
  \''A', '\'B', '\'C', '\'D', '\'E', '\'F', '\'G', '\'H', '\'I', '\'J', '\'K', '\'M', \
  \''N', '\'O', '\'P', '\'Q', '\'R', '\'S', '\'T', '\'U', '\'V', '\'W', '\'X', '\'Y', '\'Z', \
  \''a', '\'b', '\'c', '\'d', '\'e', '\'f', '\'g', '\'h', '\'i', '\'j', '\'k', '\'l', '\'m', \
  \''n', '\'o', '\'p', '\'q', '\'r', '\'s', '\'t', '\'u', '\'v', '\'w', '\'x', '\'y', '\'z', \
  \''à', '\'á', '\'â', '\'é', '\'í', '\'ó', '\'ù', '\'ý']
```

It likes the data contains a good selection of characters, but not how there are differences between the input and output vocabularies. This isn't surprising; after all, these are vocabularies for two different languages.

However, it's important to understand: This vocabulary defines every character model will ever handle. That means it will never know what to do with an input character not found in in_vocab and will never produce a sentence using a character not in out_vocab.

For example, the Spanish set contains parenthesis but the English one does not. You know parenthesis should be valid characters in English, but your model will never produce an output that includes them, no matter how many might appear in a given sequence.

Now that you know tokens your model can handle, any other tokens are considered OOV. There are different ways to handle OOV tokens, but none work perfectly and it's for your model, you'll take the most basic approach and remove OOV tokens from any inputs before processing them. For the validation set — and test set, if you had one — you'll need to remove them from the inputs and target outputs.

> Note: This chapter's model processes sequences at the character level, removing OOV tokens should not remove much information from a sequence. In the next chapter, you'll learn about working with full word tokens, dealing with OOV tokens becomes much more difficult.

When you use your model in iOS, you'll preprocess each sequence before passing it to the model. You'll test it against your validation set every epoch while training, it's more efficient to preprocess all of them beforehand. Run a cell with the following to remove OOV tokens from the validation set:

```python
tmp_samples = []
for in_seq, out_seq in valid_samples:
    tmp_in_seq = [c for c in in_seq if c in in_vocab]
    tmp_out_seq = [c for c in out_seq if c in out_vocab]
    tmp_samples.append(("".join(tmp_in_seq), "".join(tmp_out_seq)))
valid_samples = tmp_samples
```

Here, you iterated over the validation samples and created new sequences that only include characters that are found in the appropriate vocabulary — in_vocab for the Spanish inputs and out_vocab for the English outputs.

> Note: If you compare your validation samples before and after removing the OOV tokens, you might find little or no difference. That's happen on random split you split earlier from train_test_split, the premise here holds true; your model doesn't handle tokens while training, so you need to do some preprocessing when working with sequences containing OOV tokens. This is true while testing and at runtime in your iOS app.

## Build your model

In this section, you'll use Keras to define the seq2seq model that translates Spanish into English. First, you'll need the following code:

```python
import keras
from keras.layers import Dense, Input, LSTM, Masking
from keras.models import Model

# 1
latent_dim = 256
# 2
encoder_in = Input(shape=(None, vocab_size), name="encoder_in")
# 3
encoder_mask = Masking(name="encoder_mask")(encoder_in)
# 4
encoder_lstm = LSTM(latent_dim, return_state=True, recurrent_dropout=0.3, name="encoder_lstm")
# 5
encoder_h, encoder_c = encoder_lstm(encoder_mask)
```

It likes the data contains a good selection of characters, but not how there are differences between the input and output vocabularies. This isn't surprising; after all, these are vocabularies for two different languages.

However, it's important to understand: This vocabulary defines every character model will ever handle. That means it will never know what to do with an input character not found in in_vocab and will never produce a sentence using a character not in out_vocab.

For example, the Spanish set contains parenthesis but the English one does not. You know parenthesis should be valid characters in English, but your model will never produce an output that includes them, no matter how many might appear in a given sequence.

Now that you know tokens your model can handle, any other tokens are considered OOV. There are different ways to handle OOV tokens, but none work perfectly and it's for your model, you'll take the most basic approach and remove OOV tokens from any inputs before processing them. For the validation set — and test set, if you had one — you'll need to remove them from the inputs and target outputs.

> Note: This chapter's model processes sequences at the character level, removing OOV tokens should not remove much information from a sequence. In the next chapter, you'll learn about working with full word tokens, dealing with OOV tokens becomes much more difficult.

When you use your model in iOS, you'll preprocess each sequence before passing it to the model. You'll test it against your validation set every epoch while training, it's more efficient to preprocess all of them beforehand. Run a cell with the following to remove OOV tokens from the validation set:

```python
tmp_samples = []
for in_seq, out_seq in valid_samples:
    tmp_in_seq = [c for c in in_seq if c in in_vocab]
    tmp_out_seq = [c for c in out_seq if c in out_vocab]
    tmp_samples.append(("".join(tmp_in_seq), "".join(tmp_out_seq)))
valid_samples = tmp_samples
```

Here, you iterated over the validation samples and created new sequences that only include characters that are found in the appropriate vocabulary — in_vocab for the Spanish inputs and out_vocab for the English outputs.

> Note: If you compare your validation samples before and after removing the OOV tokens, you might find little or no difference. That's happen on random split you split earlier from train_test_split, the premise here holds true; your model doesn't handle tokens while training, so you need to do some preprocessing when working with sequences containing OOV tokens. This is true while testing and at runtime in your iOS app.

## Build your model

In this section, you'll use Keras to define the seq2seq model that translates Spanish into English. First, you'll need the following code:

```python
import keras
from keras.layers import Dense, Input, LSTM, Masking
from keras.models import Model

# 1
latent_dim = 256
# 2
encoder_in = Input(shape=(None, vocab_size), name="encoder_in")
# 3
encoder_mask = Masking(name="encoder_mask")(encoder_in)
# 4
encoder_lstm = LSTM(latent_dim, return_state=True, recurrent_dropout=0.3, name="encoder_lstm")
# 5
encoder_h, encoder_c = encoder_lstm(encoder_mask)
```

tensors have specific dimensions. But your model can handle variable length sequences, right? So do you store variable length sequences in a fixed dimension? You'll see the details later, but you'll end padding shorter sequences with zeros—essentially meaningless timesteps added to make all the sequences same. The Masking tells Keras not to train on those timestamps. This layer isn't absolutely necessary, but with the use of Note explaining a bit more the the choice to use a Masking layer.

- 4. You create an LSTM layer to process the input sequence, passing latent_dim to the size of its output. Setting return_state=True makes the LSTM output its hidden and cell states along with its regular output; you use these as the initial for the decoder. Refer back to the discussion of the seq2seq model inline if you don't recall the role of the encoder's outputs. You also use the recurrent_dropout parameter to add dropout between timesteps in the LSTM. This can help your model generalize better to unseen data. There are many parameters available to the LSTM initializer, so you should explore the Keras documentation as you dig deeper into it.

> Note: You'll likely come across examples of networks that do not use Masking layers but still pad sequences to store them in batches. These still work, but there's a subtle issue with them: These networks considering the padding tokens to be as important as the real tokens. This causes three problems.

First, they appear to have lower values when training, but that's only because such a large percentage of the tokens they test are the same padded token and it learns to output a lot of them.

The second, more important issue, is that it dilutes the information stored by the encoder because the weights are modified by essentially meaningless
