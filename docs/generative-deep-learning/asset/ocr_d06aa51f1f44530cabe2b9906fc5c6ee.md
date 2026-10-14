If you use word tokens:

+   - All text can be converted to lowercase, to ensure capitalized words at the start of sentences are tokenized the same way as the same words appearing in the middle of a sentence. In some cases, however, this may not be desirable; for example, some proper nouns, such as names or places, may benefit from remaining capitalized so that they are tokenized independently.
+   - The text *vocabulary* (the set of distinct words in the training set) may be very large, with some words appearing very sparsely or perhaps only once. It may be wise to replace sparse words with a token for *unknown word*, rather than including them as separate tokens, to reduce the number of weights the neural network needs to learn.
+   - Words can be *stemmed*, meaning that they are reduced to their simplest form, so that different tenses of a verb remained tokenized together. For example, *browse*, *browsing*, *browses*, and *browsed* would all be stemmed to *brows*.
+   - You will need to either tokenize the punctuation, or remove it altogether.
+   - Using word tokenization means that the model will never be able to predict words outside of the training vocabulary.

If you use character tokens:

+   - The model may generate sequences of characters that form new words outside of the training vocabulary—this may be desirable in some contexts, but not in others.
+   - Capital letters can either be converted to their lowercase counterparts, or remain as separate tokens.
+   - The vocabulary is usually much smaller when using character tokenization. This is beneficial for model training speed as there are fewer weights to learn in the final output layer.

For this example, we’ll use lowercase word tokenization, without word stemming. We’ll also tokenize punctuation marks, as we would like the model to predict when it should end sentences or use commas, for example.

The code in Example 5-4 cleans and tokenizes the text.

*Example 5-4. Tokenization*

```
def pad_punctuation(s):
    s = re.sub(f"([{string.punctuation}])", r' \1 ', s)
    s = re.sub(' +', ' ', s)
    return s
```