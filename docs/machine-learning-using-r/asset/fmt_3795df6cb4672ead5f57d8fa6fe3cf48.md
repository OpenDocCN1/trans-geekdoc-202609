
By default, `unnest_tokens()` converts the tokens to lowercase and punctuations are stripped. We can use `to_lower` and `strip_punct` parameters to change the default behaviour.

## Cleaning the Tweets

Before using the `unnest_tokens()` to split the data, let us understand some potential issues to deal with. We will use the below text to highlight all the issues discussed in this section and fix them sequentially.

![](images/page361-01.png)

**1.** One of the issues with twitter data is that most of the tweets will contain the twitter handle. We used #IndiaFightsCorona, @COVIDNewsByMIB, @covid19indiaorg, @ COVID19_INDIA to pull the tweets. So, the tweets will contain these words a lot, but will not carry much information. The below regex takes care of words starting with ‘#’ or ‘@’. We will drop such words from the tweets.

Regex did the job perfectly.

![](images/page362-01.png)

**2.** The URLs in the tweets may not be needed in analysis and such URLs and unwanted words need to be removed as well. The below regex takes care of URLs and removes them.

![](images/page362-02.png)

**3.** There are certain words which may not be hashtags and URLs but still may not carry much meaning in analysis. We also do not need digits and punctuations in the text data. Let us create an expression to remove such words. We may not be able to identify all the less informative words upfront. It may take several iterations to identify less informative words and remove them.

![](images/page362-03.png)

Most of the expressions were discussed earlier but let us look at the regex “COVID(-?19)?”:

![](images/page362-04.png)

We will apply all three regex on the text simultaneously and see the result.

![](images/page363-01.png)

The above output shows that we have fixed some issues in the text data after applying all regex. However, we see still find some unicode text in the above output. This unicode corresponds to emoji ![](images/pageIn_ch9-02.png)and ![](images/pageIn_ch9-03.png). We also see some text in another language. We will handle these two issues as well.

**4.** A major issue with twitter data or, in general, social media data is the use of glyph/emoticons, for example, ![](images/pageIn_ch9-04.png), etc. These are referred to as Unicode character. Unicode is a character set which aims to define all characters and glyph (graphical representation) from all languages. Based on the purpose of analysis, we may or may not want to keep the glyph in the data. To remove the glyph, we can use Unicode in regex as below:

![](images/page363-02.png)

\\p is used to match emoticons. The character following it denotes the class to which the emoticons belong. Emojis belong to class ‘Other_Symbol’ (So) and ‘Unassigned’ (Cn) class. ‘Math_Symbol’ (Sm) and ‘Currency_Symbol’ (Sc) also may be needed at times. The last expression in the above regex is to take care of emojis which are not being handled by \\p{xx} character class. For example, ![](images/pageIn_ch9-05.png)(question mark within square bracket) has an encoding of ‘\\U0001f3fd’ but is not being removed by \\p{xx}. In order to remove such special characters, we can use a range of Unicode character given by \[\\U{1F000}-\\U{1FFFF}\]. - ..

**5.** Twitter data is messy in terms of how users write the text. We will always see languages mixed up in the tweets. While dealing with the English language, we may need to remove words which are in non-English language. We can do the same by using regex as follows:

![](images/page363-03.png)

In ‘`remove_non_english_regex`’ the expression “\[∧\\x01-\\x7F\] +”, matches ASCII character set (0-127, i.e., 0x0 to 0x7F). In Unicode, the same expression will be written as “\[∧\\u0000-\\u007F\]+”. This expression not only removes non-English words but also helps remove special/invisible characters and emoticons as well. So, Step 4 may be redundant too.

**6.** The word ‘RT’ also will appear in most of the tweets, which signifies that it is a retweet. We will filter out the retweets by using the `filter()` and `str_detect()` function from `dplyr` and `stringr`.

**7.** We will remove these words by using an inbuilt BoW/lexicon of English grammar from the `tidytext` package by using `anti_join()`. `anti_join()` returns all rows from the tweet without a match in `stop_words`.

The regex used in the above seven steps may need modification based on the text data being analyzed. Let us consider the above seven steps and split the text column in `covid_twitter_df` using the `unnest_token()`. **[Table 9.13](#17_Chapter09.xhtml#tab9.13)** shows ten observations from the resulting table.

![](images/page364-01.png)![](images/page364-02.png)![](images/page365-01.png)

The vocabulary contains 4,444 words. Note that not applying regex before creating the token would have resulted in a vocabulary of 7,825 unique words. Thus, it would have created a vector of length 7,825 and consumed more memory.

## 9.7.3 Visualise – Unigrams/Words

Let us try to understand what the high-frequency words used in the corpus?. **[Table 9.14](#17_Chapter09.xhtml#tab9.14)** shows the top six words occurring the maximum number of times. **[Figure 9.8](#17_Chapter09.xhtml#fig9.8)** shows the plot of the data.

![](images/page365-02.png)

**TABLE 9.14** | High-frequency words

| Word || *n* |
| --- | --- |
| Follow || 316 |
| --- | --- |
| Active || 300 |
| Mask || 261 |
| deaths || 243 |
| Hands || 230 |
| swachhbharat || 228 |

We will plot the top 50 words in the `word_tokens` with a token count of more than 40. This slice of data is being pulled from ‘word_tokens’ by applying `filter()` and then `slice_max()` from `dplyr` package. Further, while plotting the data, we will show the frequency count of 100+ in the forward direction and a frequency count of less than 100 in the backward direction. This is done by setting the `y` parameter of `geom_segment` to 100. **[Figure 9.8](#17_Chapter09.xhtml#fig9.8)** shows the plot of the data.

![](images/page365-03.png)![](images/page366-01.png)

In the above code snippet, the `filter()` function is redundant as the top 50 words being pulled out using the `slice_max()` have all got a count of more than 40. However, this may not be true for any other dataset. From **[Figure 9.8](#17_Chapter09.xhtml#fig9.8)**, we can conclude that

**1.** General perception towards hygiene is evident with the use of words like mask, wear, hands, wash, social, distancing, clean, don’t, etc.

**2.** People seem to be talking a lot about swachh bharat, PM (prime minister).

**3.** People are talking about deaths and recovery. The use of these words in tweets may reflect a general mood of apprehension and a cautious approach while dealing with COVID-19.

**[Figure 9.9](#17_Chapter09.xhtml#fig9.9)** shows the plot of the last 50 words in the token with a count of 40 and more.

![](images/page367-01.png)![](images/page367-02.png)

The plots we saw so far were based on a simple count of words in the BoW (`twitter_words`). However, we can take the count of words by each user (`screenName`) as well. Here, the `screenName` may be thought of as a document (discussed in [Section 9.6.1](#17_Chapter09.xhtml#sec9.6.1)) by which we will want to get the count. Let us get the users (`screenName`) who have several tweets (total words in tweet more than 100) and understand the words being used by them. The data can be prepared using the following steps:

**1.** Using `twitter_words` dataframe:
– Select `screenName` and `word` column and get a count of all the words using `count()`.
– Group the data by `screenName` using `group_by()`.
– Create a new column which stores the total words written by the user. This can be done by `mutate()`.
– Filter the tweets with a total word count of more than 100. Use `filter()` function to achieve this.
– Select the top seven records from every user, using the `slice_max()`.
– Ungroup the data using `ungroup()`.
– Arrange the data `y` `screenName` and count of word using `arrange()`.
