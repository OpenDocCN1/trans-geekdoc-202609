
One way to model unknown words is to modify the training corpus by replacing infrequent words with a special symbol, traditionally `<UNK>`. We could decide in advance to keep only, say, the 50,000 most common words, or all words with frequency greater than 0.0001%, and replace the others with `<UNK>`. Then compute `n-gram` counts for the corpus as usual, treating `<UNK>` just like any other word. When an unknown word appears in a test set, we look up its probability under `<UNK>`. Sometimes different unknown-word symbols are used for different types. For example, a string of digits might be replaced with `<NUM>`, or an email address with `<EMAIL>`. (We note that it is also advisable to have a special symbol, such as `<S>`, to mark the start (and stop) of a text. That way, when the formula for bigram probabilities asks for the word before the first word, the answer is `<S>`, not an error.)

Even after we’ve handled unknown words, we have the problem of unseen `n-gram`s. For example, a test text might contain the phrase “colorless aquamarine ideas,” three words that we may have seen individually in the training corpus, but never in that exact order. The problem is that some low-probability `n-gram`s appear in the training corpus, while other equally low-probability `n-gram`s happen to not appear at all. We don't want some of them to have a zero probability while others have a small positive probability; we want to apply smoothing to all the similar `n-gram`s—reserving some of the probability mass of the model for never-seen `n-gram`s, to reduce the variance of the model.

### Smoothing
The simplest type of smoothing was suggested by Pierre-Simon Laplace in the 18th century to estimate the probability of rare events, such as the sun failing to rise tomorrow. Laplace’s (incorrect) theory of the solar system suggested it was about `N` = 2 million days old. Going by the data, there were zero out of two million days when the sun failed to rise, yet we don't want to say that the probability is exactly zero. Laplace showed that if we adopt a uniform prior, and combine that with the evidence so far, we get a best estimate of `1 / (N + 2)` for the probability of the sun's failure to rise tomorrow—either it will or it won't (that's the 2 in the denominator) and a uniform prior says it is as likely as not (that's the 1 in the numerator). Laplace smoothing (also called add-one smoothing) is a step in the right direction, but for many natural language applications it performs poorly.

Another choice is a backoff model, in which we start by estimating `n-gram` counts, but for any particular sequence that has a low (or zero) count, we back off to (`n – 1`)-grams. Linear interpolation smoothing is a backoff model that combines trigram, bigram, and unigram models by linear interpolation. It defines the probability estimate as

### Backoff model
### Linear interpolation smoothing
`P̂(c[i]|c[i-2:i-1]) = λ[3]P(c[i]|c[i-2:i-1]) + λ[2]P(c[i]|c[i-1]) + λ[1]P(c[i])`
where `λ3 + λ2 + λ1 = 1`. The parameter values `λi` can be fixed, or they can be trained with an expectation–maximization algorithm. It is also possible to have the values of `λi` depend on the counts: if we have a high count of trigrams, then we weigh them relatively more; if only a low count, then we put more weight on the bigram and unigram models.

One camp of researchers has developed ever more sophisticated smoothing techniques (such as Witten-Bell and Kneser-Ney), while another camp suggests gathering a larger corpus so that even simple smoothing techniques work well (one such approach is called “stupid backoff”). Both are getting at the same goal: reducing the variance in the language model.

## 24.1.5 Word representations
`N-gram`s can give us a model that accurately predicts the probability of word sequences, telling us that, for example, “a black cat” is a more likely English phrase than “cat black a” because “a black cat” appears in about 0.000014% of the trigrams in a training corpus, while “cat black a” does not appear at all. Everything that the `n-gram` word model knows, it learned from counts of specific word sequences.

But a native speaker of English would tell a different story: “a black cat” is valid because it follows a familiar pattern (article-adjective-noun), while “cat black a” does not.

Now consider the phrase “the fulvous kitten.” An English speaker could recognize this as also following the article-adjective-noun pattern (even a speaker who does not know that “fulvous” means “brownish yellow” could recognize that almost all words that end in “-ous” are adjectives). Furthermore, the speaker would recognize the close syntactic connection between “a” and “the,” as well as the close semantic relation between “cat” and “kitten.” Thus, the appearance of “a black cat” in the data is evidence, through generalization, that “the fulvous kitten” is also valid English.

The `n-gram` model misses this generalization because it is an atomic model: each word is an atom, distinct from every other word, with no internal structure. We have seen throughout this book that factored or structured models allow for more expressive power and better generalization. We will see in [Section 25.1](#Chapter25-01.xhtml#sec25-1) that a factored model called word embeddings gives a better ability to generalize.

One type of structured word model is a dictionary, usually constructed through manual labor. For example, `WordNet` is an open-source, hand-curated dictionary in machine-readable format that has proven useful for many natural language applications[1](#Chapter24-08.xhtml#sup24-1) Below is the `WordNet` entry for “kitten:”

### Dictionary
### WordNet
“kitten” `<noun.animal>` (“young domestic cat“) IS A: `young_mammal`
“kitten” `<verb.body>` (“give birth to kittens“)
EXAMPLE: “our cat kittened again this year”

`WordNet` will help you separate the nouns from the verbs, and get the basic categories (a kitten is a young mammal, which is a mammal, which is an animal), but it won’t tell you the details of what a kitten looks like or acts like. `WordNet` will tell you that two subclasses of cat are Siamese cat and Manx cat, but won’t tell you any more about the breeds.

## 24.1.6 Part-of-speech (POS) tagging
One basic way to categorize words is by their part of speech (POS), also called lexical category or tag: noun, verb, adjective, and so on. Parts of speech allow language models to capture generalizations such as “adjectives generally come before nouns in English.” (In other languages, such as French, it is the other way around (generally)).

### Part of speech (POS)
Everyone agrees that “noun” and “verb” are parts of speech, but when we get into the details there is no one definitive list. [Figure 24.1](#Chapter24-01.xhtml#fig24-1) shows the 45 tags used in the Penn Treebank, a corpus of over three million words of text annotated with part-of-speech tags. As we will see later, the Penn Treebank also annotates many sentences with syntactic parse trees, from which the corpus gets its name. Here is an excerpt saying that “from” is tagged as a preposition (`IN`), “the” as a determiner (`DT`), and so on:

Description
The thirteen words are arranged inside a square. The words car, bicycle, and truck appear together at the lower left position inside the square. The words banana, pizza, and apple appear together at the lower middle position inside the square. The words nephew, uncle, niece, and aunt appear together at the middle right position inside the square. The words France, Germany, and Greece appear together at the upper left position inside the square.

×![](images/Fig-338.jpg)

Figure 24.1 Part-of-speech tags (with an example word for each tag) for the Penn Treebank corpus (Marcus et al., 1993). Here “3rd-sing” is an abbreviation for “third person singular present tense.”
