
We can create the sentiment score using `nrc` on similar lines to `bing` lexicon. The below code is used to generate **[Table 9.50](#17_Chapter09.xhtml#tab9.50)** for sentiment using `nrc`.

![](images/page405-02.png)

**TABLE 9.50** | First 10 users and the sentiment score using nrc

| `screenName` || `sentiment_nrc` |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 1 |
| DistrictAdm_FBD || 0 |
| drmubl || 3 |
| esichq || 6 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 3 |
| FOBUdhampur || 5 |
| HealthwireMedia || 8 |

*Note:* Positive value reflects positive sentiment, negative value reflects negative sentiment, and a value of zero reflects neutral sentiment.

**TABLE 9.51** | First 10 users and the sentiment score using afinn

| `screenName` || `sentiment_afinn` |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 3 |
| DistrictAdm_FBD || −1 |
| Drmubl || 8 |
| Esichq || 0 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 6 |
| FOBUdhampur || 10 |
| HealthwireMedia || 6 |

*Note:* Positive value reflects positive sentiment, negative value reflects negative sentiment, and a value of zero reflects neutral sentiment.

**[Table 9.51](#17_Chapter09.xhtml#tab9.51)** for sentiment using `afinn`. Note that since the sentiment scores in affin lexicon are on a numeric scale, we did not use `spread()` and `mutate()`.

![](images/page406-01.png)

We will merge the sentiment scores obtained by `bing`, `nrc`, and `afinn` to create **[Table 9.52](#17_Chapter09.xhtml#tab9.52).**

![](images/page406-02.png)![](images/page406-03.png)

**[Table 9.52](#17_Chapter09.xhtml#tab9.52)** shows the sentiment score using the three lexicons. **[Figure 9.22](#17_Chapter09.xhtml#fig9.22)** shows the plot of affin score from **[Table 9.52](#17_Chapter09.xhtml#tab9.52).** If we compare the three scores, the `nrc` and `bing` seem to give similar sentiment (either positive or negative) for a user. However, there are instances of `afinn` sentiment being different to the `nrc` or `bing`. We can use either of the scores to access the sentiment of a user. The other option could be to use a voting mechanism (similar to ensemble techniques) and come up with a combined score and sentiment. We encourage readers to try the voting strategy to aggregate the outcome of the three lexicons and plot the same.

![](images/page407-01.png)![](images/page407-02.png)

### 9.9 | Sentiment Analysis with Negative Words

In the previous section, we arrived at the sentiment by counting the positive and negative words. However, one of the drawbacks of counting single words is that words on their own may not convey a positive or negative emotion.

**1.** I am not happy – This sentence may convey a positive emotion if we look at the words in unigram fashion. However, ‘not happy’ means a negative emotion.

One of the ways to deal with such sentiments is to look at the n-gram (bigrams/tri-grams) to arrive at the sentiment score. We already created bigrams (`separated_bigram` variable) in [Section 9.7.6](#17_Chapter09.xhtml#sec9.7.6). Let us look at all the words which were preceded by ‘not.

![](images/page408-01.png)

From **[Table 9.53](#17_Chapter09.xhtml#tab9.53)**, we can see that the most common words used with not were ‘discriminate’, ‘over’, ‘forget, ‘attend, etc. We also see that there are `stop_words` (like, to, a, etc.) appearing in the table but which do not convey an emotion. Let us use the AFINN lexicon to identify words preceded with negation words (‘not, ‘no, ‘never, ‘without, ‘dont’) and conveying emotion. **[Table 9.54](#17_Chapter09.xhtml#tab9.54)** shows the words and the sentiment score. Of course, these sentiment scores need to be interpreted in contrary. A negative score denotes a positive sentiment and a positive score denotes a negative sentiment.

![](images/page408-02.png)

From **[Table 9.54](#17_Chapter09.xhtml#tab9.54)**, we see that the most common word associated with not was forget, which actually should have a score of +1 (as it is preceded by ‘not’). We can calculate how much a word has contributed in the wrong direction. We will multiply `value` and `n` columns in **[Table 9.54](#17_Chapter09.xhtml#tab9.54)** to get the contribution. Contribution intuitively suggests that a word with a value of say +2 occurring five times has as much impact as a word with a sentiment value of + 1 occurring 10 times. **[Table 9.55](#17_Chapter09.xhtml#tab9.55)** shows the contribution of each word.

![](images/page408-03.png)![](images/page409-01.png)![](images/page409-02.png)![](images/page409-03.png)![](images/page410-01.png)

**[Figure 9.23](#17_Chapter09.xhtml#fig9.23)** visualizes the sentiment of words with negation aspects.

![](images/page410-02.png)

### 9.10 | Document Term Matrix

In all the previous sections, we processed and arranged text in a tabular format such that it was ‘one token per document (tweets by a user/`screenName` here) per row’. The benefit of doing so was a quick summarization and visualization of text data as well as in sentiment analysis. However, this tabular structure of data may not be compatible with packages which apply other NLP models on the data.

One of the most common structures text mining packages work with is the document-term matrix (or DTM). DTM matrix has the following structure (Silge and Robinson, 2017):

**1.** Each row represents one document (such as tweet by the user/`screenName`).

**2.** Each column represents one token (unigram/bigram, etc.).

**3.** Each value (typically) contains the number of appearances of that term in that document.

This structure is exactly the same as in **[Tables 9.5](#17_Chapter09.xhtml#tab9.5)** and **[9.6](#17_Chapter09.xhtml#tab9.6)** from [Section 9.6.1](#17_Chapter09.xhtml#sec9.6.1). Intuitively, we can visualize that DTM will be a sparse matrix, that is, most pairings of document and word will have a value of zero. However, DTMs are created in efficient ways by different packages. The `cast()` from tidytext package can be used to convert a tabular data from previous sections in a DTM format. Tidytext provides three variations of cast function:

**1.** `cast_sparse()` – converts to a sparse matrix which can be used with `Matrix` package.

**2.** `cast_dtm()` – converts to DTM object to be used in operations from `tm` package.

**3.** `cast_dfm()` – converts to a Document Feature Matrix (DFM) object which can work with `quanteda` package. DFM is just another name for DTM.

Given a DTM, tidytext also provides `tidy()` function which will convert the DTM to a tabular format (one token per document per row) for easy summarization and visualization of data.

We will use the `cast()` to create a DTM and merge it with the original tweet data-frame, that is, `covid_twitter_df`. Before we create the DTM and merge, a few things to keep in mind are as follows:

**1.** We will create `twitter_word` dataframe as done in [Section 9.7.2](#17_Chapter09.xhtml#sec9.7.2). However, it will be without deleting the retweets while performing the text preprocessing.

**2.** Rather than using the `screenName` as a synonym to document ID, we will create a `doc_id` to keep track of the individual tweets.

Treating `screenName` as document ID in all the previous sections was not an issue since we wanted to summarize, visualize and do sentiment analysis for the users, that is, at `screenName` level. Let us understand why the second point becomes important from a DTM perspective. The `covid_twitter_df` is shown in **[Table 9.56](#17_Chapter09.xhtml#tab9.56).**

![](images/page411-01.png)![](images/page411-02.png)![](images/page412-01.png)
