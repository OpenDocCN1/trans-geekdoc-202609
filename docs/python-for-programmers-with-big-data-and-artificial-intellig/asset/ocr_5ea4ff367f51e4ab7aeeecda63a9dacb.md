module's download function:

lick here to view code image

```
In [1]: import nltk

In [2]: nltk.download('stopwords')
[nltk_data] Downloading package stopwords to
[nltk_data]     C:\Users\PaulDeitel\AppData\Roaming\nltk_data...
[nltk_data]   Unzipping corpora\stopwords.zip.
Out[2]: True
```

For this example, we'll load the 'english' stop words list. First import stopwords from the nltk.corpus module, then use stopwords method words to load the 'english' stop words list:

lick here to view code image

```
In [3]: from nltk.corpus import stopwords

In [4]: stops = stopwords.words('english')
```

Next, let's create a TextBlob from which we'll remove stop words:

lick here to view code image

```
In [5]: from textblob import TextBlob
In [6]: blob = TextBlob('Today is a beautiful day.')
```

Finally, to remove the stop words, let's use the TextBlob's words in a list comprehension that adds each word to the resulting list only if the word is not in stops:

lick here to view code image

```
In [7]: [word for word in blob.words if word not in stops]
Out[7]: ['Today', 'beautiful', 'day']
```

# 11.2.14 n-grams

An n-gram 1 is a sequence of n text items, such as letters in words or words in a sentence. In natural language processing, n-grams can be used to identify letters or words that frequently appear adjacent to one another. For text-based user input, this can help predict the next letter or word a user will type—such as when completing items in IPython with tab-completion or when entering a message to a friend in your favorite smartphone messaging app. For speech-to-text, n-grams might be used to improve the quality of the transcription. N-grams are a form of co-occurrence in which words or letters appear near each other in a body of text.

1 https://en.wikipedia.org/wiki/N-gram.

TextBlob's ngrams method produces a list of WordList n-grams of length three by