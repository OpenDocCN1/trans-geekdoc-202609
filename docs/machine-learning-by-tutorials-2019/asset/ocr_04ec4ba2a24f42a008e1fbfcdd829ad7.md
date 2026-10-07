trained earlier in the chapter, without training with more data or making any other changes, would it help?

Consider when it translates this sentence: "Entonces esta película te sorprenderá." By choosing the character with the highest prediction probability at each step, currently outputs "So this movie will surprise you." This sentence has a normalized sum of log probabilities of -0.341630.

However, the correct translation – according to Google Translate – is, "This movie will surprise you. And this sentence has a normalized sum of log probabilities of -0.300456.

Producing this better translation requires making three choices that are not the highest probability character for these steps – the fourth highest for two others. Depending on how you implement it the beam width you use, beam search could find this correct translation. That means the current model can produce better translations with the help of some smarter decoding.

> Note: This chapter's bidirectional model can translate a few of the review and test sentences correctly if occasionally choose lower-probability characters. For example, choosing "u" instead of "o" when translating, "Hay un gato debajo de la mesa," "There is a cat on the table," instead of, "There is a cat on the table." Just adding beam search mean you'll get these translations. That's because they end up with lower total probabilities than the model finds using greedy search.

However, that's because of the training data more than the model or the algorithm; training with larger datasets means better language usage statistics, once you have a model trained with a lot of data, coupling it with beam search gives you the best chance of producing high quality results.

# Attention

The previous chapter mentioned an important problem with the encoder portion of your seq2seq model: It needs to encode the sequence into a single, fixed-length vector. That limits the length of the input sequences it can successfully handle, because each new token essentially dilutes the stored information.