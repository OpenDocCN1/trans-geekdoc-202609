
You commonly apply a number of transformations when applying TF-IDF, with the most important transformation normalizing the text length. Clearly, a longer text has more chances to have more words that are distinctive when compared to a shorter text. For example, when the word `fox` appears in a short text, it can be relevant to the meaning of that expression because `fox` stands out among few other words. However, when the word `fox` appears once in a long text, its presence might not matter much because it’s a single word among many others. For this reason, the transformation divides the count of each token by the total number of tokens for each phrase. Treating a phrase like this turns token counting into a token percentage, so TF-IDF no longer considers how many times the word `fox` appears, but instead considers the percentage of times the word `fox` appears among all the tokens. The following example demonstrates how to complete the previous example using a combination of normalization and TF-IDF.

```
TfidF = text.TfidfTransformer(norm='l1')
tfidf_mtx = TfidF.fit_transform(vectorized_text)
phrase = 3 # choose a number from 0 to 3
total = 0
for word in vectorizer.vocabulary_:
    pos = vectorizer.vocabulary_[word]
    value = list(tfidf_mtx.toarray()[phrase])[pos]
    if value != 0:
        print ("%10s: %0.3f" % (word, value))
        total += value
print('\nSummed values of a phrase: %0.1f' % total)
```

Using this new TF-IDF model rescales the values of important words and makes them comparable between each text in the corpus. To recover part of the ordering of the text before the BoW transformation, adding n-grams is also useful. An `n-gram` is a continuous sequence of tokens in the text that you use as a single token in the BoW representation. For instance, in the phrase `The quick brown fox jumps over the lazy dog,` a `bigram —` that is, a sequence of two tokens — transforms `brown fox` and `lazy dog` into single tokens. A `trigram` may create a single token from `quick brown fox.` An n-gram is a powerful tool, but it has a drawback because it doesn’t know which combinations are important to the meaning of a phrase. N-grams create all the contiguous sequences of size N. The TF-IDF model can underweight the less useful n-grams, but only projects like Google’s NGram viewer (you learn more about this viewer later in the chapter) can tell you which n-grams are useful in NLP with any certainty. The following example uses `CountVectorizer` to model n-grams in the range of (2, 2), that is, bigrams.

```
bigrams = text.CountVectorizer(ngram:range=(2, 2))
print(bigrams.fit(corpus).vocabulary_)
{'the quick': 30, 'quick brown': 24, 'brown fox': 3,'fox jumps': 9, 'jumps over': 15, 'over the': 21,'the lazy': 29, 'lazy dog': 17, 'my dog': 19, 'dog is': 7,'is quick': 11, 'quick and': 23, 'and can': 1,'can jump': 6, 'jump over': 14, 'over fences': 20,'your dog': 31, 'is so': 12, 'so lazy': 26,'lazy that': 18, 'that it': 27, 'it sleeps': 13,'sleeps all': 25, 'all the': 0, 'the day': 28,'black dog': 2, 'dog just': 8, 'just passed': 16,'passed by': 22, 'by but': 5, 'but my': 4, 'is brown': 10}
```

![Tip](images/tip.png)Setting different ranges lets you use both `unigrams` (single tokens) and n-grams in your NLP analysis. For instance the setting `ngram:range=(1,3)` creates all tokens, all bigrams, and all trigrams. You usually never need more than trigrams in an NLP analysis. Increasing the number of n-grams is slightly beneficial after trigrams and sometimes even just after bigrams, depending on the corpus size and the NLP problem.

### Stemming and removing stop words

`Stemming` is the process of reducing words to their stem (or root) word. This task isn't the same as understanding that some words come from Latin or other roots, but instead makes similar words equal to each other for the purpose of comparison or sharing. For example, the words `cats, catty,` and `catlike` all have the stem `cat.` The act of stemming helps you analyze sentences when tokenizing them because words having the same stem should have the same meaning (represented by a single feature).

Creating stem words by removing suffixes to make tokenizing sentences easier isn’t the only way to make the document matrix simpler. Languages include many glue words that don’t mean much to a computer but have significant meaning to humans, such as `a, as, the, that,` and so on in English. They make the text flow and concatenate in a meaningful way. Yet, the BoW approach doesn’t care much about how you arrange words in a text. Thus, removing such words is legitimate. These short, less useful words are called `stop words.`

The act of stemming and removing stop words simplifies the text and reduces the number of textual elements so that only the essential elements remain. In addition, you keep just the terms that are nearest to the true sense of the phrase. By reducing the number of tokens, a computational algorithm can work faster and process the text more effectively when the corpus is large.

This example requires the use of the Natural Language Toolkit (NLTK), which Anaconda doesn’t normally install by default. (You can check for an NLTK installation by opening an Anaconda prompt, typing `conda list nltk`, and pressing Enter. If the output doesn’t show that you have version 3.5 or above installed, then you must install it.) To use this example, you must download and install the NLTK using the instructions found at [`http://www.nltk.org/install.html`](http://www.nltk.org/install.html) for your platform. Make certain that you install the NLTK for whatever version of Python you’re using for this book when you have multiple versions of Python installed on your system. After you install the NLTK, you must also install the packages associated with it. The instructions at [`http://www.nltk.org/data.html`](http://www.nltk.org/data.html) tell you how to perform this task. (Install all the packages to ensure that you have everything.)

The following example demonstrates how to perform stemming and remove stop words from a sentence. It begins by training an algorithm to perform the required analysis using a test sentence. Afterward, the example checks a second sentence for words that appear in the first.

```
from sklearn.feature_extraction import text
import nltk
from nltk import word_tokenize
from nltk.stem.porter import PorterStemmer
from nltk.corpus import stopwords
nltk.download('punkt')
nltk.download('stopwords')
stemmer = PorterStemmer()
stop_words = stopwords.words('english')
def stem:tokens(tokens, stemmer):
    stemmed = []
    for item in tokens:
        stemmed.append(stemmer.stem(item))
    return stemmed
def tokenize(text):
    # Tokenizing
    tokens = word_tokenize(text)
    # Removing stopwords
    tokens = [token for token in tokens if token not in stop_words]
    # Stemming
    stems = stem:tokens(tokens, stemmer)
    return stems
vocab = ['Sam loves swimming so he swims all the time']
vect = text.CountVectorizer(tokenizer=tokenize)
vec = vect.fit(vocab)
sentence1 = vec.transform(['George loves swimming too!'])
print(vec.get_feature_names())
print(sentence1.toarray())
```
