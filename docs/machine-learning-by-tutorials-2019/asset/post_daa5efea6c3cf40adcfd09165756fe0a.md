
trained earlier in the chapter, without training with more data or making any other changes, would it help?

Consider when it translates this sentence: "Entonces esta película te sorprenderá." By choosing the character with the highest prediction probability at each step, currently outputs "So this movie will surprise you." This sentence has a normalized sum of log probabilities of -0.341630.

However, the correct translation – according to Google Translate – is, "This movie will surprise you. And this sentence has a normalized sum of log probabilities of -0.300456.

Producing this better translation requires making three choices that are not the highest probability character for these steps – the fourth highest for two others. Depending on how you implement it the beam width you use, beam search could find this correct translation. That means the current model can produce better translations with the help of some smarter decoding.

> Note: This chapter's bidirectional model can translate a few of the review and test sentences correctly if occasionally choose lower-probability characters. For example, choosing "u" instead of "o" when translating, "Hay un gato debajo de la mesa," "There is a cat on the table," instead of, "There is a cat on the table." Just adding beam search mean you'll get these translations. That's because they end up with lower total probabilities than the model finds using greedy search.

However, that's because of the training data more than the model or the algorithm; training with larger datasets means better language usage statistics, once you have a model trained with a lot of data, coupling it with beam search gives you the best chance of producing high quality results.

## Attention

The previous chapter mentioned an important problem with the encoder portion of your seq2seq model: It needs to encode the sequence into a single, fixed-length vector. That limits the length of the input sequences it can successfully handle, because each new token essentially dilutes the stored information.

To combat this issue, you can use a technique called attention. The most basic implementation of attention works like this: Instead of using one vector to represent the entire sequence, the encoder encodes a vector per input token. The decoder learns to apply different weights to each vector at each output timestep, essentially paying attention to specific combinations of words. The weights are often visualized as attention maps, like in the following image:

There's a column for each token in the input sequence — in this case, the tokens are words, not characters — and a row for each output token. The colors in the rows indicate how each column's input token was considered for that timestep, black=0 to white=1.

Notice how it doesn't necessarily focus on the word aligned with the same timestep. For example, it needs to look at out of order when translating "the European Economic Area" to "la zone économique européenne." Using attention, models learn to relate specific parts of output with specific parts of their input, which produces better results than the basic seq2seq you've built, especially on longer sequences. It has proven so powerful that it's now used in state-of-the-art models for NLP, as well as for other tasks like computer vision problems.

There's a variation of attention called self-attention that gives even better results. Whereas regular attention works between the encoder and decoder, self-attention gains additional information by allowing the encoder to apply attention between the input tokens, and it lets the decoder apply attention between its output tokens. That is, regular attention only relates the input to output tokens, but self-attention relates tokens within each sequence to other tokens in the same sequence, as.

Self-attention performs even better than regular attention because it lets the encoder fine tune its encodings on relationships it finds between input tokens, such as noun-verb agreement or whom a pronoun refers in a sentence. In fact, self-attention is so good that current state-of-the-art models, often based on a network architecture called a Transformer, do away with the recurrent portions of the encoder and decoder rely entirely on self-attention. Not only do they perform better, but they faster, too!

These state-of-the-art models are large, that they usually run in the cloud. However, you can take advantage of these techniques in smaller models, too, depending on the task and the details of your implementation. If you decide to explore adding attention to your own networks, you may want to look at some of the important papers related to:

- "Neural Machine Translation by Jointly Learning to Align and Translate" arxiv.org/abs/1409.0473
- “A Structured Self-attentive Sentence Embedding, arxiv.org/abs/1703.03130
- “Attention Is All You Need, arxiv.org/abs/1706.03762

We glossed over the previous image showed whole word tokens, not characters like you you use in your models. The next section discusses the choice to work with characters instead of words in these chapters.

## Why use characters at all?

The seq2seq models you've made in this book with sequences at the character level, but why? How much information does a model get from each token when it views sequences this way? People can easily read and correctly interpret sentences where every word is mispelled, but replacing a few words characters doesn't add much information to a sentence, where most words do, so wouldn't translation models consider words instead?

The answer to that is yes — also maybe not.

Researchers are always exploring different options, e.g., combining words into phrases or the way we are and breaking them into substwords. There are hybrid approaches that look at tokens in multiple ways, e.g., as words and characters, which can help when dealing with OOV tokens. They have even made models that work with sequences of bytes! Working with words is probably the most common approach, but there are some difficulties involved that you should be aware of before attempting to build models.

First, there's vocabulary size. It may not be obvious if you haven't dealt much with these models, but vocabulary size matters quite a bit, for three reasons:

- 1. The model's output layer performs a softmax calculation across the entire vocabulary to produce the probabilities for each token — the more tokens, the longer that calculation. A byte-level model has a vocabulary of 256 values and is capable of representing anything; a character-level model for a restricted character set, like ASCII, will vary but in the hundreds or low thousands; full Unicode support would include over 1.1 million characters; and using word tokens means a potential vocabulary size of many millions.

In, working with words requires limiting the vocabulary to some subset of common words, and then you need to add in ways to deal with OOV tokens.

![](img/5720be5c3cca252e12448e68d25607b5_541_0.png)

- 2. The larger vocabulary, the larger the model. Because that increases the width of your input and output layers (at least), these layers end up contributing most of your model's trainable parameters. Mobile devices don't have the resources to deal with very large models, so it may not be feasible to support large vocabularies on.

- 3. The dreaded cursed of dimensionality. You'll hear this term lot in machine learning. It refers to the fact that, as you increase the number of input features, the possible combinations of inputs grow exponentially. (As each specific training sample covers a smaller percentage of those possibilities. The primary result: As you add features, you need to increase the size of your training set — exponentially. Now consider that each token in the vocabulary is a unique input dimension, and you will see need more training data as the size of grows.

> Note: Here's an example of the curse of dimensionality. Consider a model that takes only one input feature — an integer from 1 to 10. There are only 10 possible inputs, so each training sample essentially covers 10% of all possible inputs this model can ever see.

Adding a second input feature — again an integer from 1 to 10 — gives you a two-dimensional input with 100 possible combinations, so each training sample now covers 1% of the possible inputs. And adding a third dimension brings the possible combinations up to 1,000, which would mean each sample covers only one tenth of 1%.

As the number of dimensions goes up, a model must train on drastically data in order to learn an accurate representation of the input space.

Secondly, with subword tokens makes it easier to deal with OOV tokens. At the byte level, you can remove the problem entirely — there will only be of 256 possible values; with characters you can delete OOV tokens and rarely lose information. With words, it becomes a difficult problem that's still an open area of research. You'll read more about it in the next section.

![](img/5720be5c3cca252e12448e68d25607b5_542_0.png)
