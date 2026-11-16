+   • **Sentiment analysis**—determining whether text has positive, neutral or negative sentiment.

+   • **Inter-language translation** and **language detection** powered by Google Translate.

+   • **Inflection** 3 —pluralizing and singularizing words. There are other aspects of inflection that are not part of TextBlob.

3 https://en.wikipedia.org/wiki/Inflection.

+   • **Spell checking and spelling correction.**

+   • **Stemming**—reducing words to their stems by removing prefixes or suffixes. For example, the stem of “varieties” is “varieti.”

+   • **Lemmatization**—like stemming, but produces real words based on the original words’ context. For example, the lemmatized form of “varieties” is “variety.”

+   • **Word frequencies**—determining how often each word appears in a corpus.

+   • **WordNet integration** for finding word definitions, synonyms and antonyms.

+   • **Stop word elimination**—removing common words, such as a, an, the, I, we, you and more to analyze the important words in a corpus.

+   • **n-grams**—producing sets of consecutive words in a corpus for use in identifying words that frequently appear adjacent to one another.

Many of these capabilities are used as part of more complex NLP tasks. In this section, we’ll perform these NLP tasks using TextBlob and NLTK.

# Installing the TextBlob Module

To install TextBlob, open your Anaconda Prompt (Windows), Terminal (macOS/Linux) or shell (Linux), then execute the following command:

lick here to view code image

```
conda install -c conda-forge textblob
```

Windows users might need to run the Anaconda Prompt as an Administrator for proper software installation privileges. To do so, right-click Anaconda Prompt in the start menu and select More > Run as administrator.

Once installation completes, execute the following command to download the NLTK corpora used by TextBlob:

lick here to view code image

```
ipython -m textblob.download_corpora
```