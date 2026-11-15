Note that this is merely for demonstration purposes, but remember, you should use the APIs responsibly and at your own risk and responsibility.

# # Building our model

If you have a Twitter account and you would like to analyze your own history, you can follow the official instructions on their website (https://help.twitter.com/en/managing-your-account/how-to-download-your-twitter-archive) and you will receive a ZIP file with your own Tweet history.

We will use Pablo's Twitter data for demonstration.

# # Exploratory data analysis

As explained earlier in this chapter, one thing you can do is to look for an annotated lexicon per sentiment and try to do some basic analysis there, thanks to the package `tidytext`.

First, we import a few libraries that would come handy and load our Twitter history:

```
library(plyr)
library(dplyr)
library(tidytext)
library(ggplot2)
df <- read.csv("./data/Tweets.csv", stringsAsFactors = F)
text_df <- data_frame(tweet_id=df$tweet_id, tweet=df$text)
```

Now, we use the `unnest_tokens` function to bring the data into tidy format:

```
text_df <- text_df %>
unnest_tokens(word, tweet)
```

And remove the stop words:

```
data(stop_words)
head(stop_words)
text_df <- text_df %>% anti_join(stop_words)
```

Once this is done, we join it with, for instance, the `bing` lexicon:

```
bing <- get_sentiments("bing")
text_df %>% inner_join(bing)
```