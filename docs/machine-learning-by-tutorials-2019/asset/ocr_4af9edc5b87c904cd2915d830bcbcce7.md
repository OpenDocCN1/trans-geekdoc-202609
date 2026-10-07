# Machine Learning

# Chapter 16: Natural Language Transformation, Part 2

+   - Pre-trained word embeddings are often produced for lower-case tokens. That means you'll need to convert your input sequences to lower case prior to translating, then figure out what to capitalize in the output. You can use specific rules or heuristic-based approaches, or you might training a separate neural network to capitalize text.

+   - As mentioned earlier, tokenize input text the same way you did during. You didn't have to worry about that when working with characters, because there's no ambiguity about what token in a case

+   - Be sure to replace OOV tokens with the proper <UNK> token(s). You just dropped OOV tokens when working with characters, but you'll lose too much information if you do that with whole words.

+   - After running your model — maybe with a nice search — you'll be left with a list of tokens that might look like this: ['i', 'do', 'n't', '<UNK>', 'or', 'bugs', '.']. You'll need to perform post-processing to properly capitalize words, insert spaces appropriately and connect contractions. You'll also need a plan for dealing with any <UNK> tokens. One option is to align the sentence in some way and carry over words that seem to match. For example, if there is an <UNK> token in each of the input and output, just copy the original unknown input token directly into the output. Translating between some language pairs requires a reordering of terms, and sometimes the numbers of missing terms won't match. Even when things seem to line up, that won't always produce a good result. Dealing with OOV tokens is an open area of research and there isn't

To conclude this introduction using word tokens, keep these tips in mind:

+   - Pre-trained embeddings learn the biases of the data they are trained on. For example, embeddings trained on internet data usually place the word "apple" closer to their companies, like Microsoft, than to fruit, like bananas.

+   - Each embedding represents the average of all uses for that word. That means words used in multiple ways have diluted embeddings that don't always represent any of their uses. There have been attempts to deal with this issue using context-sensitive embeddings. These are more complex but may be worth looking into some

+   - Try running a spell checker on your sequences prior to looking for OOV tokens. That should help reduce the number of tokens you can't find in your vocabulary.

+   - When you encounter an OOV token during preprocessing, you might want to

![](bbox=[0.152, 0.923, 0.345, 0.958])

552