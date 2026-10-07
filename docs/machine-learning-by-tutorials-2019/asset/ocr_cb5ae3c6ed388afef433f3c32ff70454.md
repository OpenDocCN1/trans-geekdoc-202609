Machine Learning

Chapter 16: Natural Language Transformation, Part 2

cell states. Instead, they only have hidden states, which makes them a bit less complicated to work with when you have to manage states directly — like you do with the decoder in a seq2seq model

So now you will try a new version of the model you trained in the previous chapter — one that includes a bidirectional encoder. The Python code for this section is nearly identical to what you wrote for your first seq2seq model. As such, your chapter's resources include a first-populated jupyter notebook to run at notebooks/Bidir-Char-Seq2seq-Starter.ipynb. Or, you can just review the contents of notebooks/Bidir-Char-Seq2seq-Complete.ipynb, which shows the output from the run used to build the pre-trained bidirectional model included in the notebooks/pre-trained/Bidir-CharModel/folder.

The rest of this section goes over the important differences between this and the previous model built.

The first difference isn't out of necessity, but this model uses a larger latent_dim value:

```
latent_dims = 512
```

The previous model used 256 dimensions, which meant produced 256 features from your encoder to your decoder — the LSTM produced 256-length vectors, one for the hidden state and one for the cell state. GRU layers don't have a cell state, so they return only a single vector of length latent_dim. Rather than send half the amount of information to the decoder, the author chose to double the size of the GRUs.

The biggest differences for this model are in the encoder, let's go over its definition:

```
# 1
encoder_in = Input(
shape=(None
```

![](bbox=[0.1617, 0.9135, 0.2035, 0.9535])

raywender.com

529