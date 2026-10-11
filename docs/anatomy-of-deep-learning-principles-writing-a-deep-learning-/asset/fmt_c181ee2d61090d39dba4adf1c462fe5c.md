
#### 3. Training character-level Seq2Seq model

According to the training sample set pair obtained after data processing and the training code of the previous Seq2Seq model, the Seq2Seq model of character-level machine translation can be trained. The following code defines the encoder and decoder objects `encoder`, `decoder`, and corresponding optimizer `encoder_optimizer`, `decoder_optimizer`. And divide the sample set `pairs` into two sets `train_pairs` and `valid_pairs` for training and verification, and then call the training function `trainIters()` of the Seq2Seq model to train the model:

```
from train import *
from Layers import *
from rnn import *
import util

hidden_size = 50 #256 
num_layers = 1
clip = 5.#50.
learning_rate = 0.1
decoder_learning_ratio = 1.0 
teacher_forcing_ratio =0.5

encoder = EncoderRNN(in_verb.n_chars, hidden_size)
decoder = DecoderRNN(out_verb.n_chars,hidden_size,out_verb.n_chars,num_layers,teacher_forcing_ratio)

momentum = 0.5
decay_every  =1000

encoder_optimizer = SGD(encoder.parameters(), learning_rate, momentum,decay_every)
decoder_optimizer = SGD(decoder.parameters(), learning_rate*decoder_learning_ratio, momentum,decay_every)

reg= None#1e-2

if True:
    pairs = pairs[:80000]

np.random.shuffle(pairs)

train_n = (int)(len(pairs)*0.98)
train_pairs = pairs[:train_n]
valid_pairs = pairs[train_n:]

n_iters = 50000
print_every, plot_every = 100,100  #10,10

idx_train_pairs = [tensorsFromPair(random.choice(train_pairs))      for i in range(n_iters)]
idx_valid_pairs  =  [tensorsFromPair(pair)  for pair in valid_pairs]

trainIters(encoder, decoder,encoder_optimizer,decoder_optimizer,idx_train_pairs,idx_valid_pairs,True,print_every, plot_every,reg)
```

![Figure 8-54 Loss curve of the Seq2Seq model for character sequences](EPUB/media/file168.png)

From the separation of the training loss curve and the verification loss curve, it can be seen that the training is unstable, and the loss curve tends to be flat and rises slightly after 40,000 times.

The trained model can be used for language translation. The word sequence (sentence) of the language to be translated is input to the `encoder` to generate an output context information, which is input to the `decoder`. Produce translated word sequences (sentences).

```
def evaluate(encoder,decoder,in_vocab,out_vocab,sentence,\
             max_length=MAX_LENGTH,last_Hidden = True): 
    encode_input = tensorFromSentence(in_vocab,sentence)
    encoder_output, encoder_hidden = encoder(encode_input, None)   
    if last_Hidden:
        output_sentence =  decoder.evaluate(encoder_hidden,max_length) 
    else:
        output_sentence =  decoder.evaluate(encoder_output,max_length) 
    output_sentence = indexToSentence(out_vocab,output_sentence)
    return output_sentence
```

Among them, `last_Hidden` indicates whether the input of the `decoder` is the output (hidden vector) of the `encoder` at the last moment or the output at all moments.

Randomly select several input sentences and use `evaluate` to predict the translated sentences:

```
indices = np.random.randint(len(pairs), size=3)
for i in indices:
    pair = pairs[i]
    print(pair)
    sentence = pair[0]   
    sentence = evaluate(encoder, decoder,in_verb,out_verb, sentence,MAX_LENGTH)
    print(sentence)
```

```
['es tu jalouse ?', 'are you jealous ?']
are you a see  ??

['continue a courir .', 'keep running .']
come a         .

['lis ton livre !', 'read your book .']
be care it .
```
