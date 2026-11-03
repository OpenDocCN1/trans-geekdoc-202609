
The short url in [Table 9.33](#17_Chapter09.xhtml#tab9.33) can be expanded using the below code snippet. [Table 9.34](#17_Chapter09.xhtml#tab9.34) shows the expanded url.

![](images/page393-02.png)

TABLE 9.34 | First six observations of expanded URLs

| `url` || `status_code` |
| --- | --- |
| [https://twitter.com/MoHFW_INDIA/status/1316278631321100289/photo/1](https://twitter.com/MoHFW_INDIA/status/1316278631321100289/photo/1) || 400 |
| --- | --- |
| [https://twitter.com/mygovindia/status/1316602805818257410/photo/1](https://twitter.com/mygovindia/status/1316602805818257410/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1315610983793008640/photo/1](https://twitter.com/mygovindia/status/1315610983793008640/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1315616867776491520/photo/1](https://twitter.com/mygovindia/status/1315616867776491520/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1316596832928055297/photo/1](https://twitter.com/mygovindia/status/1316596832928055297/photo/1) || 400 |
| [https://twitter.com/MoHFW_INDIA/status/1317424639295909888/photo/1](https://twitter.com/MoHFW_INDIA/status/1317424639295909888/photo/1) || 400 |

Let us bind the URL links with the short URLs. [Table 9.35](#17_Chapter09.xhtml#tab9.35) shows the short URL and the corresponding URL link.

![](images/page394-01.png)

We will extract the domain from URL link and count the domains. The use of `gsub()` and `regex` explained in previous sections will be used to extract the URL links. [Table 9.36](#17_Chapter09.xhtml#tab9.36) shows the domain name and number of times it appeared.

![](images/page394-02.png)

### 9.7.10 Visualize URL

[Figure 9.19](#17_Chapter09.xhtml#fig9.19) shows the plot for common domains in tweets using `ggplot`.

![](images/page394-03.png)![](images/page394-04.png)

TABLE 9.36 | Domain count

| `domain` || `domain_count` |
| --- | --- |
| twitter.com || 448 |
| --- | --- |
| pledge.mygov.in || 24 |
| livemint.com || 16 |
| blog.mygov.in || 8 |

![](images/page395-01.png)

[Figure 9.19](#17_Chapter09.xhtml#fig9.19) shows that in a majority of the cases, information for tweets link to the twitter source itself. We may also want to understand the hashtags used by users while retweeting. We leave it for the readers to try it out.

## 9.8 Sentiment Analysis

After having created the `BoW` model and with the understanding of basic word embed-dings, let us delve into the other topic which is of interest in text analytics. Sentiment of the users regarding a particular topic is of great interest. In this case, we want to know the emotions of the users on topics related to COVID-19. Through human intelligence, one can read through the tweets and get an understanding of the emotion reflected by the user. It could be a positive/negative tweet or a happy/neutral/sad tweet, etc. But it will be overwhelming for a human being to read through all the tweets and tag the tweets to reflect emotional intent.

`tidytext` comes with inbuilt lexicon (available through `textdata` package) which can help categorize the tweet into one of the predefined tags of emotion. Four general-purpose lexicons in `tidytext` are as follows:

1. `Afinn` – This lexicon from Finn Årup Nielsen (Nielsen, 2011) categorizes 2,477 unique unigrams on a score of −5 (negative sentiment) to 5 (positive sentiment). This is licensed under Open Database License (ODbL) v1.0. [Table 9.37](#17_Chapter09.xhtml#tab9.37) shows six observations from afinn lexicon.

![](images/page395-02.png)

TABLE 9.37 | First six observations from afinn lexicon

| `Word` || `value` |
| --- | --- |
| Abandon || −2 |
| --- | --- |
| Abandoned || −2 |
| abandons || −2 |
| abducted || −2 |
| abducted || −2 |
| abducted || −2 |

TABLE 9.38 | First six words from nrc lexicon

| `Word` || `sentiment` |
| --- | --- |
| abacus || trust |
| --- | --- |
| abandon || fear |
| abandon || negative |
| abandon || sadness |
| abandoned || anger |
| abandoned || fear |

1. `Nrc` – This lexicon from Saif Mohammad and Peter Turney (2013) categorizes words under the labels ‘trust’, ‘fear’, ‘negative’, ‘sadness’, ‘anger’, ‘surprise’, ‘positive’, ‘disgust’, ‘joy’, and ‘anticipation’. It is by far the most comprehensive, having categorized 6,468 unigrams under these labels. A word can have a mapping to more than one label. This dataset requires license for commercial use. [Table 9.38](#17_Chapter09.xhtml#tab9.38) shows six observations from nrc lexicon.

![](images/page396-01.png)

2. `Bing` – This lexicon from Bing Liu (2015) and collaborators categorizes words in binary fashion, that is, positive/negative, that is, two unique labels. It has categorized 6,783 unigrams under these labels. By default, only this lexicon is available as a part of the `tidytext`. [Table 9.39](#17_Chapter09.xhtml#tab9.39) shows six observations from bing lexicon (S Biguzzi, 2020).

![](images/page396-02.png)

3. `lougharn` – This lexicon from Loughran-McDonald (2019) categorizes words under the labels ‘negative’, ‘positive’, ‘uncertainty’, ‘litigious’, ‘constraining’, and ‘superfluous’. The lexicon has categorized 3,917 English words under these emotional intents. Words may have a mapping under more than one label. This lexicon requires license for commercial use. [Table 9.40](#17_Chapter09.xhtml#tab9.40) shows six observations from lougharn lexicon.

![](images/page396-03.png)

We need to install `textdata` package to access ‘afinn’, ‘nrc’, and ‘lougharn’ lexicon. The `get_sentiments()` function internally uses `textdata::lexicon_afinn()`, `textdata::lexicon_nrc()`, `textdata::lexicon_loughran()` to download these lexicons and make it available for use. All the above lexicons were constructed and validated by the authors of the lexicons, using crowd-sourcing platforms. The advantage of using these lexicons is that we can quickly arrive at the sentiments from a corpus. The disadvantage is that the accuracy of the sentiments may be questionable if the style of writing in a corpus is very different (say, a book which is 100 years old and we use the above lexicon to decide on the sentiments being expressed in the book).

TABLE 9.39 | First six words from bing lexicon

| `Word` || `sentiment` |
| --- | --- |
| 2-faces || negative |
| --- | --- |
| abnormal || negative |
| abolish || negative |
| abominable || negative |
| abominably || negative |
| abominate || negative |

TABLE 9.40 | First six words from lougharn lexicon

| `Word` || `sentiment` |
| --- | --- |
| abandon || negative |
| --- | --- |
| abandoned || negative |
| abandoning || negative |
| abandonment || negative |
| abandonments || negative |
| abandons || negative |

These lexicons are based on unigrams and thus the emotions are at unigram level. The sentiment of the tweet (represented as a `BoW`) may be arrived at by combining the sentiment of the unigrams. We will use the ‘nrc’ lexicon to perform sentiment analysis on the covid data. We will understand the sentiments expressed by users (`screenName`) who tweeted multiple times with 50 to 100 words in tweets. The ‘`twitter_word_count`’ object from [Section 9.7.3](#17_Chapter09.xhtml#sec9.7.3) contains the unigrams created using `unnest_token()`. [Table 9.41](#17_Chapter09.xhtml#tab9.41) shows the top 20 rows by users who tweeted between 50 and 100 words.

![](images/page397-01.png)![](images/page397-02.png)

There are 45 unique users in the tweet sentiment df.

![](images/page398-01.png)

Let us get the emotions of the user. The labels in `nrc` lexicon are as follows: ‘trust, ‘fear, ‘negative, ‘sadness, ‘anger, ‘surprise, ‘positive, ‘disgust, ‘joy, and ‘anticipation’. Let us look at the tweets which reflect ‘sadness, We will follow the following steps:

1. Get words from ‘nrc’ lexicon which reflect sadness and store them in a variable ‘`nrc_sad`’.
