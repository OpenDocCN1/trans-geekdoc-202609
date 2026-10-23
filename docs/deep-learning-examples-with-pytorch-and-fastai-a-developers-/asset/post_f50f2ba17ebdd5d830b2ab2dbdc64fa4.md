
though several faces will be familiar. The entire cast does an excellent job with the script. But it is hard to watch, because there is no good end to a situation like the one presented. It is now fashionable to blame the British for setting Hindus and Muslims against each other and then cruelly separating them into two countries. There is some merit in this view, but it’s also true that no one forced Hindus and Muslims in the region to mistreat each other as they did around the time of partition. It seems more likely that the British simply saw the tensions between the religions and were clever enough to exploit them to their own ends. The result is that there is much cruelty and inhumanity in the situation and this is very unpleasant to remember and to see on the screen. But it is never painted as a black-and-white case. There is baseness and nobility on both sides, and also the hope for change in the younger generation. There is redemption of a sort in the end, when Puro has to make a hard choice between a man who has ruined her life, but also truly loved her, and her family which has disowned her, then later come looking for her. But by that point, she has no option that is without great pain for her. This film carries the message that both Muslims and Hindus have their grave faults, and also that both can be dignified and caring people. The reality of partition makes that realisation all the more wrenching, since there can never be real reconciliation across the India/Pakistan border. In that sense, it is similar to “Mr & Mrs Iyer”. In the end, we were glad to have seen the film, even though the resolution was heartbreaking. If the UK and US could deal with their own histories of racism with this kind of frankness, they would certainly be better off.’

## 28.1.1 Data Pipeline

Well before models like BERT came into play, fastai had already implemented transfer learning with NLU. The main idea of transfer learning with text is to first train a language-model for the given language that more or less understands the language. You could use this language model to predict the next word of a given couple of words. But we are using this model as a kind of encoder for our classification model. This concept is called ULM-FiT.

So the first thing we want to build is this language model. Our training data contains the text and the label (positive/negative). But for creating the
language model we do not care about the label. We just need the text.
Therefore we grab the text column with a dataloader.

We do not need the datablock API for this level because we can just use the from_csv method. With the TextDataLoaders we can pass in a parameter is_lm that indicates if we want to create a language model. Then our y-values will just be the next word (respectively the next token).

```
data_lm = TextDataLoaders.from_csv(path, 'texts.csv',  text_col='text',
is_lm=True)
```

### What is this thing called Tokenization?

Well, even for text we have to break down everything to numbers to work with neural nets. Tokenizing helps us with this task.

Tokenizing takes all of our text and splits the sentences into these tokens. A token can be a word, a group of words, etc. that has some kind of meaning to us. Tokenization usually takes care of punctuation, contraction, HTML tags, etc. The default tokenizer with fastai is spacy but you can also use the sentence piece tokenizer.

Here are some examples of what spacy did while tokenizing:

- ‘s’ are grouped together
- contractions are separated like so “did”, “n’t”
- Any HTML symbol has been cleaned
- Everything is converted to lower-case
- there are several special tokens (all those that begin by xx), to replace unknown tokens (see below) or to introduce different text fields

The next step is to convert everything into numbers. This process is called **numericalization**. This means that we create a dictionary with a numerical value for each of our tokens.

If we want to use another tokenizer we have to create the dataloaders with the datablock api.

First we install sentencepiece and load the tokenizer.

```
!pip install sentencepiece
```

```
```python
tokenizer = SentencePieceTokenizer
```
```

Now we can create our datablock and pass in the custom tokenizer:

```
```python
sp_lm = DataBlock(blocks=TextBlock.from_df('text',
is_lm=True, tok_func=tokenizer),
```
```

```
```python
get_x=ColReader('text'),
splitter=RandomSplitter(0.1)
dls = sp_lm.dataloaders(df, bs=64, seq_len=72)
```
```

PROCESSING

## 28.1.2 Training our Language Model

Ideally we would train our model with the full dataset but to speed things up we keep with the small subset. The pre-trained model we are using is wikitext-103. This is a model that was trained on the English wikipedia articles.

```
```python
dls = sp_lm.dataloaders(df, bs=64, seq_len=72)
learn = language_model_learner(dls, AWD_LSTM, drop_mult=0.3)
```
```

Now let’s look at the architecture of the model that we are working with:

![](img/d5454da46c702784893ef8b0b539e5b9_384_0.png)

We start with the embeddings followed by three RNNs before going through the decoder to get our outputs.

For the training process we can switch to mixed-precision to speed up training time. To do this, we need everything in multiples of 8, hence our BS is 8. This helps use the CUDA cores (tensor cores) to the best of their ability.

```
```python
learn = learn.to_fp16()
learn.lr_find()
```
```

SuggestedLRs(lr_min=0.19054607152938843,
lr_steep=0.04786301031708717)

![](img/d5454da46c702784893ef8b0b539e5b9_385_0.png)

learn.fit_one_cycle(1, 1e-2)
epoch train_loss valid_loss time
0 6.790908 6.128580 00:11

For our language model we need an accuracy of about 30-40 percent. We do not need to train the model for a higher accuracy because we won’t use it to predict the next word of a sentence but for transfer learning.

So now we can unfreeze and train a bit more:
learn.unfreeze()
learn.fit_one_cycle(5, 1e-3)
epoch train_loss valid_loss time

0 5.972351 5.723276 00:14
1 5.709247 5.377630 00:14
2 5.475660 5.233379 00:14
3 5.308859 5.180630 00:14
4 5.217210 5.166652 00:14

learn.save('27-language-model-fine_tuned')
Remember the only thing we can do with this model is predict the next word

of a sentence. We try this:

```
text = 'I liked this movie because'
n_words = 20
n_sentences=3
print('\n'.join(learn.predict(text, n_words) for _ in
→ range(n_sentences)))
```

We have to save the encoder for the later use with our classifier!

```
learn.save_encoder('27-fine-tuned-encoder')
```

Let’s look at the architecture of the model that we are working with.

## 28.1.3 Create the Classifier

Now that we have our language model trained we can start building our classifier. This is how the process of building our classifier with transfer learning looks like:

![](img/d5454da46c702784893ef8b0b539e5b9_386_0.png)

PROCESSING

We have started with a pre-trained language model and trained this along on our corpus text. Next step is to create the classifier based on this fine-tuned language model.

We build our datablock and we want to make sure that it has the same sequence length because we are using one model for the other.

```
blocks = (TextBlock.from_df('text',
seq_len=dls.seq_len,
vocab=dls.vocab),
```

```
CategoryBlock()
```

```
imdb_clas = DataBlock(blocks=blocks,
 get_x=ColReader('text'),
 get_y=ColReader('label'),
 splitter=ColSplitter())
```

```
dls = imdb_clas.dataloaders(df, bs=64)
```

Now we can train our final model. The backbone architecture for ULMfit is an AWD_LSTM. In order to make use of our pre-trained weights we are going to load this encoder back in.

```
learn = text_classifier_learner(dls,
 AWD_LSTM,
 drop_mult=0.5,
 metrics=accuracy).to_fp16()
```

```
learn.load_encoder('27-fine-tuned-encoder');
learn.fine_tune(5)
epoch train_loss
```

0 0.849227 valid_loss 0.687484 accuracy time 0.550000 00:03

epoch train_loss

0 0.750340
1 0.706977
2 0.676277
3 0.649858
4 0.626770
valid_loss

0.662187
0.631181
0.586847
0.570621
0.569212
