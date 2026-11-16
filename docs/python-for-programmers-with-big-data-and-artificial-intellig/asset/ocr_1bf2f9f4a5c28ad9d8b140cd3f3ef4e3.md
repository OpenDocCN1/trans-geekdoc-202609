```
# ignore tweet if the topic is not in the tweet  text
if self.topic.lower() not in tweet_text.lower():
    return

# update self.sentiment_dict with the polarity
blob = TextBlob(tweet_text)
if blob.sentiment.polarity > 0:
    sentiment = '+'
    self.sentiment_dict['positive'] += 1
elif blob.sentiment.polarity == 0:
    sentiment = ''
    self.sentiment_dict['neutral'] += 1
else:
    sentiment = '-'
    self.sentiment_dict['negative'] += 1

# display the tweet
print(f'{sentiment} {status.user.screen_name}: {tweet_text}\\n')

self.tweet_count += 1 # track number of tweets processed

# if TWEET_LIMIT is reached, return False to terminate streamir
return self.tweet_count != self.TWEET_LIMIT
```

# ain Application

The main application is defined in the function main (lines 62–87; discussed after the
following code), which is called by lines 90–91 when you execute the file as a script. So
sentiment–listener.py can be imported into IPython or other modules to use class
SentimentListener as we did with TweetListener in the previous section:

click here to view code image

```
def main():
    # configure the OAuthHandler
    auth = tweepy.OAuthHandler(keys.consumer_key, keys.consumer_secret)
    auth.set_access_token(keys.access_token, keys.access_token_secret)

    # get the API object
    api = tweepy.API(auth, wait_on_rate_limit=True,
                     wait_on_rate_limit_notify=True)

    # create the StreamListener subclass object
    search_key = sys.argv[1]
    limit = int(sys.argv[2]) # number of tweets to tally
    sentiment_dict = {'positive': 0, 'neutral': 0, 'negative': 0}
    sentiment_listener = SentimentListener(api,
                                            sentiment_dict, search_key, limit)
```