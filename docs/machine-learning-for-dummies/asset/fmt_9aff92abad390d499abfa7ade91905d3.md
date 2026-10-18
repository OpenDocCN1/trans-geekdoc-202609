
Before a computer can do anything with text, it must be able to read the text in some manner. [Chapter 11](#c11.xhtml) shows how you can prepare data to deal with categorical features, such as a feature representing a color (for instance, representing whether an example relates to the colors red, green, or blue). Categorical data is a type of short text that you represent using binary features, that is, features coded using one or zero values according to whether a certain value is present in the categorical feature. Not surprisingly, you can represent complex text using the same logic.

![Remember](images/remember.png)Text data is usually represented as strings, but strings are also typical of categorical data and of structured data such as addresses or directory entries. What makes textual data different is the richness of meaning and information presented in an unstructured way.

[Chapter 13](#c13.xhtml) presents a technique named `one-hot encoding` that shows how you can transform a categorical color feature, having values such as red, green, and blue, into three binary features, each one representing one of the three colors. In a similar way, you can transform a phrase like “The quick brown fox jumps over the lazy dog” using nine binary features, one for each word that appears in the text (“The” is considered distinct from “the” because of its initial capital letter). This is the BoW form of representation. In its simplest form, BoW shows whether a certain word is present in the text by flagging a specific feature in the dataset. The following sections show an example using Python and its Scikit-learn package.

### Defining the input data

The input data is three phrases, `text_1`, `text_2`, and `text_3`, placed in a list, `corpus`. A `corpus` is a set of homogenous documents put together for NLP analysis:

```
text_1 = 'The quick brown fox jumps over the lazy dog.'
text_2 = 'My dog is quick and can jump over fences.'
text_3 = 'Your dog is so lazy that it sleeps all the day.'
corpus = [text_1, text_2, text_3]
```

![Tip](images/tip.png)When you need to analyze text using a computer, you load the documents from disk or scrape them from the web and place each of them into a string feature. If you have multiple documents, you store them all in a list, the corpus. When you have a single document, you can split it using chapters, paragraphs, or simply the end of each line. After splitting the document, place all its parts into a list and apply analysis as if the list were a corpus of documents.

Now that you have a corpus, you use a class from the `feature_extraction` module in Scikit-learn, `CountVectorizer`, which easily transforms texts into BoW like this:

```
from sklearn.feature_extraction import text
vectorizer = text.CountVectorizer(binary=True)
vectorizer.fit(corpus)
vectorized_text = vectorizer.transform(corpus)
print(vectorized_text.todense())
[[0 0 1 0 0 1 0 1 0 0 0 1 1 0 1 1 0 0 0 1 0]
 [0 1 0 1 0 1 1 0 1 0 1 0 0 1 1 1 0 0 0 0 0]
 [1 0 0 0 1 1 0 0 1 1 0 0 1 0 0 0 1 1 1 1 1]]
```

The `CountVectorizer` class learns the corpus content using the `fit` method and then turns it (using the `transform` method) into a list of lists. As discussed in [Chapter 7](#c07.xhtml), a list of lists is nothing more than a matrix in disguise, so what the class returns is actually a matrix made of three rows (the three documents, in the same order as the corpus) and 21 columns representing the content.

The BoW representation turns words into the column features of a document matrix, and these features have a nonzero value when present in the processed text. For instance, consider the word `dog`. The following code shows its representation in the BoW:

```
print(vectorizer.vocabulary_)
{'the': 19, 'quick': 15, 'brown': 2, 'fox': 7,'jumps': 11,'over': 14, 'lazy': 12, 'dog': 5, 'my': 13,'is': 8, 'and': 1, 'can': 3, 'jump': 10, 'fences': 6,'your': 20, 'so': 17, 'that': 18, 'it': 9, 'sleeps': 16,'all': 0, 'day': 4}
```

It uses the `CountVectorizer()` function to print the vocabulary learned from text reports, where it associates `dog` with the number five, which means that `dog` is the fifth element in the BoW representations. In fact, in the obtained BoW, the fifth element of each document list always has a value of 1 because `dog` is the only word present in all the tree documents.

![Remember](images/remember.png)Storing documents in a document matrix form can be memory intensive because you must represent each document as a vector of the same length as the dictionary that created it. The dictionary in this example is quite limited, but when you use a larger corpus, you discover that a dictionary of the English language contains well over a million terms. The solution is to use sparse matrices. A sparse matrix is a way to store a matrix in your computer's memory without having zero values occupying memory space. You can read more about sparse matrices in Python here: [`https://cmdlinetips.com/2018/03/sparse-matrices-in-python-with-scipy/`](https://cmdlinetips.com/2018/03/sparse-matrices-in-python-with-scipy/).

### Processing and enhancing text

Marking whether a word is present or not in a text is indeed a good start, but sometimes it’s not enough. The BoW model has its own limits. As if you were putting stuff randomly into a bag, in a BoW, words lose their order relationship with each other. For instance, in the phrase `My dog is quick and can jump over fences`, you know that `quick` refers to `dog` because it is glued to it by the form `is` of the verb `to be`. In a BoW, however, everything is mixed and some internal references are lost. Further processing can help prevent such a situation. The following sections discuss how to process and enhance text.

#### Considering basic processing tasks

Instead of marking the presence or absence of an element of the phrase (technically called a `token`), you can instead count how many times it occurs, as shown in the following code:

```
text_4 = 'A black dog just passed by but my dog is brown.'
corpus.append(text_4)
vectorizer = text.CountVectorizer()
vectorized.fit(corpus)
vectorized_text = vectorizer.transform(corpus)
print(vectorized_text.todense()[-1])
[[0 0 1 1 1 1 0 0 2 0 0 1 0 0 0 1 0 1 0 1 0 0 0 0 0 0]]
```

This code modifies the previous example by adding a new phrase with the word `dog` repeated two times. The code appends the new phrase to the `corpus` and retrains the `vectorizer`, but it omits the `binary=True` setting this time. The resulting vector for the last inserted document clearly shows a `2` value in the ninth position, thus the `vectorizer` counts the word `dog` twice. Note that dog is now word number 8, instead of number 5, because the BoW has changed.

Counting tokens helps make important words stand out. Yet, it's easy to repeat phrase elements, such as articles, that aren’t important to the meaning of the expression. In the next section, you discover how to exclude less important elements, but for the time being, the example underweights them using the Term Frequency-Inverse Document Frequency (TF-IDF) transformation.

The TF-IDF transformation is a technique that, after counting how many times a token appears in a phrase, divides the value by the number of documents in which the token appears. Using this technique, the `vectorizer` deems a word less important, even if it appears many times in a text, when it also finds that word in other texts. In the example corpus, the word `dog` appears in every text. In a classification problem, you can’t use the word to distinguish between texts because it appears everywhere in the corpus. The word `fox` appears in only one phrase, making it an important classification term.
