![](bbox=[0.126, 0.022, 0.944, 0.139])

hese tweets were truncated (as indicated by ), meaning that they probably use the newer 280-character tweet limit. We'll use the extended_tweet property shortly to access full text for such tweets.

In the preceding snippets, we chose to call the user_timeline method directly and use the count keyword argument to specify the number of tweets to retrieve. If you wish to get more than the maximum number of tweets per call (200), then you should use a Cursor to call user_timeline as demonstrated previously. Recall that a Cursor automatically pages through the results by calling the method multiple times, if necessary.

# Grabbing Recent Tweets from Your Own Timeline

You can call the API method home_timeline, as in:

```
api.home_timeline()
```

to get tweets from your home timeline 6—that is, your tweets and tweets from the people you follow. This method calls Twitter's statuses/home_timeline method. 7 By default, home_timeline returns the most recent 20 tweets, but can get up to 200 at a time. Again, for more than 200 tweets from your home timeline, you should use a Tweepy Cursor to call home_timeline.

6 Specifically for the account you used to authenticate with Twitter.

7 ttps://developer.twitter.com/en/docs/tweets/timelines/api-reference/get-statuses-home_timeline.

# 12.10 SEARCHING RECENT TWEETS

The Tweepy API method search returns tweets that match a query string. According to the method's documentation, Twitter maintains its search index only for the previous seven days' tweets, and a search is not guaranteed to return all matching tweets. Method search calls Twitter's search/tweets method 8 , which returns 15 tweets at a time by default, but can return up to 100.

8 ttps://developer.twitter.com/en/docs/tweets/search/api-