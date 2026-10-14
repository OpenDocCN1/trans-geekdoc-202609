
```
wine review : germany :
pfalz:        51.53%
mosel:        41.21%
rheingau:     4.27%
rheinhessen:  2.16%
franken:      0.44%
--------
```
```
wine review : germany : rheingau : riesling : this is a ripe , full - bodied
riesling:     46.56%
, :          27.78%
wine:         16.88%
and:          4.58%
yet:          1.33%
--------
```
```
wine review : germany : rheingau : riesling : this is a ripe , full - bodied riesling
with a touch of residual sugar . it's a slightly
sweet:        94.23%
oily:         1.25%
viscous:      1.09%
bitter:       0.88%
honeyed:      0.66%
--------
```

Figure 9-11. Distribution of word probabilities following various sequences

In the first example, the model attends closely to the country (germany) in order to decide on the word that relates to the region. This makes sense! To pick a region, it needs to take lots of information from the words that relate to the country, to ensure they match. It doesn’t need to pay as much attention to the first two tokens (wine review) because they don’t hold any useful information regarding the region.

In the second example, it needs to refer back to the grape (riesling), so it pays attention to the first time that it was mentioned. It can pull this information by directly attending to the word, no matter how far back it is in the sentence (within the upper limit of 80 words). Notice that this is very different from a recurrent neural network, which relies on a hidden state to maintain all interesting information over the length of the sequence so that it can be drawn upon if required—a much less efficient approach.

The final sequence shows an example of how our GPT model can choose an appropriate adjective based on a combination of information. Here the attention is again on the grape (riesling), but also on the fact that it contains residual sugar. As Riesling is typically a sweet wine, and sugar is already mentioned, it makes sense that it should be described as slightly sweet rather than slightly earthy, for example.

It is incredibly informative to be able to interrogate the network in this way, to understand exactly where it is pulling information from in order to make accurate decisions about each subsequent word. I highly recommend playing around with the input prompts to see if you can get the model to attend to words really far back in the sentence, to convince yourself of the power of attention-based models over more traditional recurrent models!

## Other Transformers

Our GPT model is a *decoder Transformer*—it generates a text string one token at a time and uses causal masking to only attend to previous words in the input string. There are also *encoder Transformers*, which do not use causal masking—instead, they attend to the entire input string in order to extract a meaningful contextual representation of the input. For other tasks, such as language translation, there are also *encoder-decoder Transformers* that can translate from one text string to another; this type of model contains both encoder Transformer blocks and decoder Transformer blocks.

Table 9-1 summarizes the three types of Transformers, with the best examples of each architecture and typical use cases.

Table 9-1. The three Transformer architectures

| Type | Examples | Use cases |
|---|---|---|
| Encoder | BERT (Google) | Sentence classification, named entity recognition, extractive question answering |
| Encoder-decoder | T5 (Google) | Summarization, translation, question answering |
| Decoder | GPT-3 (OpenAI) | Text generation |

A well-known example of an encoder Transformer is the *Bidirectional Encoder Representations from Transformers* (BERT) model, developed by Google (Devlin et al., 2018) that predicts missing words from a sentence, given context from both before and after the missing word in all layers.

![](img/f0f0f5d89818fdddf117bbe758ac8143_281_0.png)

## Encoder Transformers

Encoder Transformers are typically used for tasks that require an understanding of the input as a whole, such as sentence classification, named entity recognition, and extractive question answering. They are not used for text generation tasks, so we will not explore them in detail in this book—see Lewis Tunstall et al.’s *Natural Language Processing with Transformers* (O’Reilly) for more information.

In the following sections we will explore how encoder-decoder transformers work and discuss extensions of the original GPT model architecture released by OpenAI, including ChatGPT, which has been specifically designed for conversational applications.

## T5

An example of a modern Transformer that uses the encoder-decoder structure is the T5 model from Google.5 This model reframes a range of tasks into a text-to-text framework, including translation, linguistic acceptability, sentence similarity, and document summarization, as shown in Figure 9-12.

![](img/f0f0f5d89818fdddf117bbe758ac8143_282_0.png)

Figure 9-12. Examples of how T5 reframes a range of tasks into a text-to-text framework, including translation, linguistic acceptability, sentence similarity, and document summarization (source: Raffel et al., 2019)

The T5 model architecture closely matches the encoder-decoder architecture used in the original Transformer paper, shown in Figure 9-13. The key difference is that T5 is trained on an enormous 750 GB corpus of text (the Colossal Clean Crawled Corpus, or C4), whereas the original Transformer paper was focused only on language translation, so it was trained on 1.4 GB of English–German sentence pairs.

![](img/f0f0f5d89818fdddf117bbe758ac8143_283_0.png)

Figure 9-13. An encoder-decoder Transformer model: each gray box is a Transformer block (source: Vaswani et al., 2017)

Much of this diagram is already familiar to us—we can see the Transformer blocks being repeated and positional embedding being used to capture the ordering of the input sequences. The two key differences between this model and the GPT model that we built earlier in the chapter are as follows:

- On the lefthand side, a set of *encoder* Transformer blocks encode the sequence to be translated. Notice that there is no causal masking on the attention layer. This is because we are not generating further text to extend the sequence to be translated; we just want to learn a good representation of the sequence as a whole that can be fed to the decoder. Therefore, the attention layers in the encoder can be completely unmasked to capture all the cross-dependencies between words, no matter the order.

- On the righthand side, a set of *decoder* Transformer blocks generate the translated text. The initial attention layer is *self-referential* (i.e., the key, value, and query come from the same input) and causal masking is used to ensure information from future tokens is not leaked to the current word to be predicted. However, we can then see that the subsequent attention layer pulls the key and value from the encoder, leaving only the query passed through from the decoder itself. This is called *cross-referential* attention and means that the decoder can attend to the encoder representation of the input sequence to be translated. This is how the decoder knows what meaning the translation needs to convey!

Figure 9-14 shows an example of cross-referential attention. Two attention heads of the decoder layer are able to work together to provide the correct German translation for the word the, when used in the context of the street. In German, there are three definite articles (der, die, das) depending on the gender of the noun, but the Transformer knows to choose die because one attention head is able to attend to the word street (a feminine word in German), while another attends to the word to translate (the).

![](img/f0f0f5d89818fdddf117bbe758ac8143_284_0.png)

Figure 9-14. An example of how one attention head attends to the word “the” and another attends to the word “street” in order to correctly translate the word “the” to the German word “die” as the feminine definite article of “Straße”
