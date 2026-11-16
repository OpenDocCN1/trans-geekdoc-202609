
https://developer.twitter.com/en/docs/trends/locations-with-trending-topics/api-reference/get-trends-closest.

### 12.11.2 Getting a List of Trending Topics

The Tweepy API's `trends_place` method calls the Twitter Trends API's `trends/place` method¹ to get the top 50 trending topics for the location with the specified WOEID. You can get the WOEIDs from the `woeid` attribute in each dictionary returned by the `trends_available` or `trends_closest` methods discussed in the previous section, or you can find a location's Yahoo! Where on Earth ID (WOEID) by searching for a city/town, state, country, address, zip code or landmark at

¹ https://developer.twitter.com/en/docs/trends/trends-for-location/api-reference/get-trends-place.

```
http://www.woeidlookup.com
```

You can also look up WOEIDs programmatically using Yahoo!’s web services via Python libraries like `woeid`²:

² You'll need a Yahoo! API key as described in the `woeid` module's documentation.

```
https://github.com/Ray-SunR/woeid
```

### Worldwide Trending Topics

Let's get today's worldwide trending topics (your results will differ):

Click here to view code image

```
In [35]: world_trends = api.trends_place(id=1)
```

The `trends_place` method returns a one-element list containing a dictionary. The dictionary's `'trends'` key refers to a list of dictionaries representing each trend:

Click here to view code image

```
In [36]: trends_list = world_trends[0]['trends']
```

Each trend dictionary has `name`, `url`, `promoted_content` (indicating the tweet is an advertisement), `query` and `tweet_volume` keys (shown below). The following trend is in Spanish—`#BienvenidoSeptiembre` means “Welcome September”:

Click here to view code image

```
In [37]: trends_list[0]
Out[37]:
{'name': '#BienvenidoSeptiembre',
 'url': 'http://twitter.com/search?q=%23BienvenidoSeptiembre',
 'promoted_content': None,
 'query': '%23BienvenidoSeptiembre',
 'tweet_volume': 15186}
```

For trends with more than 10,000 tweets, the `tweet_volume` is the number of tweets; otherwise, it's `None`. Let's use a list comprehension to filter the list so that it contains only trends with more than 10,000 tweets:

Click here to view code image

```
In [38]: trends_list = [t for t in trends_list if t['tweet_volume']]
```

Next, let's sort the trends in descending order by `tweet_volume`:

Click here to view code image

```
In [39]: from operator import itemgetter

In [40]: trends_list.sort(key=itemgetter('tweet_volume'), reverse=True)
```

Now, let's display the names of the top five trending topics:

Click here to view code image

```
In [41]: for trend in trends_list[:5]:
    ...:     print(trend['name'])
    ...:
#HBDJanaSenaniPawanKalyan
#BackToHogwarts
Khalil Mack
#ItalianGP
Alisson
```

### New York City Trending Topics

Now, let’s get the top five trending topics for New York City (WOEID 2459115). The following code performs the same tasks as above, but for the different WOEID:

Click here to view code image

```
In [42]: nyc_trends = api.trends_place(id=2459115) # New York City WOEID
In [43]: nyc_list = nyc_trends[0]['trends']
In [44]: nyc_list = [t for t in nyc_list if t['tweet_volume']]
In [45]: nyc_list.sort(key=itemgetter('tweet_volume'), reverse=True)
In [46]: for trend in nyc_list[:5]:
    ...:     print(trend['name'])
    ...:
#IDOL100M
#TuesdayThoughts
#HappyBirthdayLiam
NAFTA
#USOpen
```

### 12.11.3 Create a Word Cloud from Trending Topics

In the “Natural Language Processing” chapter, we used the WordCloud library to create word clouds. Let's use it again here, to visualize New York City’s trending topics that have more than 10,000 tweets each. First, let's create a dictionary of key–value pairs consisting of the trending topic names and `tweet_volumes`:

Click here to view code image

```
In [47]: topics = {}
In [48]: for trend in nyc_list:
    ...:     topics[trend['name']] = trend['tweet_volume']
    ...:
```

Next, let's create a `WordCloud` from the `topics` dictionary's key-value pairs, then output the word cloud to the image file `TrendingTwitter.png` (shown after the code). The argument `prefer_horizontal=0.5` suggests that 50% of the words should be horizontal, though the software may ignore that to fit the content:

Click here to view code image

```
In [49]: from wordcloud import WordCloud
In [50]: wordcloud = WordCloud(width=1600, height=900, 
    ...     prefer_horizontal=0.5, min_font_size=10, colormap='prism', 
    ...     background_color='white')
In [51]: wordcloud = wordcloud.fit_words(topics)
In [52]: wordcloud = wordcloud.to_file('TrendingTwitter.png')
```

The resulting word cloud is shown below—yours will differ based on the trending topics the day you run the code:

![](img/34b7fc2f1ee27beb73bca14927d42340_523_0.png)

## 12.12 CLEANING/PREPROCESSING TWEETS FOR ANALYSIS

Data cleaning is one of the most common tasks that data scientists perform. Depending on how you intend to process tweets, you'll need to use natural language processing to normalize them by performing some or all of the data cleaning tasks in the following table. Many of these can be performed using the libraries introduced in the “Natural Language Processing (NLP)” chapter:

| Tweet cleaning tasks |
| --- |
| Converting all text to the same case |
| Removing stop words |
| Removing # symbol from hashtags |
| Removing RT (retweet) and FAV (favorite) |
| Removing @-mentions |
| Removing URLs |
| Removing duplicates |
| Stemming |
| Removing excess whitespace |
| Lemmatization |
| Removing hashtags |
| Tokenization |
| Removing punctuation |

### tweet-preprocessor Library and TextBlob Utility Functions

In this section, we'll use the tweet-preprocessor library

https://github.com/s/preprocessor

to perform some basic tweet cleaning. It can automatically remove any combination of:

- URLs,
- @-mentions (like @nasa),
- hashtags (like #mars),
- Twitter reserved words (like, RT for retweet and FAV for favorite, which is similar to a “like” on other social networks),
- emojis (all or just smileys) and
- numbers

The following table shows the module’s constants representing each option:

| Option | Option constant |
| --- | --- |
| @-Mentions (e.g., @nasa) | OPT.MENTION |
| Emoji | OPT.EMOJI |
| Hashtag (e.g., #mars) | OPT.HASHTAG |
| Number | OPT.NUMBER |
| Reserved Words (RT and FAV) | OPT.RESERVED |
| Smiley | OPT.SMILEY |
| URL | OPT.URL |

### Installing tweet-preprocessor

To install tweet-preprocessor, open your Anaconda Prompt (Windows), Terminal (macOS/Linux) or shell (Linux), then issue the following command:

```
pip install tweet-preprocessor
```

Windows users might need to run the Anaconda Prompt as an administrator for proper software installation privileges. To do so, right-click Anaconda Prompt in the start menu and select More > Run as administrator.

### Cleaning a Tweet

Let's do some basic tweet cleaning that we'll use in a later example in this chapter. The tweet-preprocessor library's module name is `preprocessor`. Its documentation recommends that you import the module as follows:

Click here to view code image

```
In [1]: import preprocessor as p
```

To set the cleaning options you'd like to use, call the module's `set_options` function. In this case, we'd like to remove URLs and Twitter reserved words:

Click here to view code image

```
In [2]: p.set_options(p.OPT.URL, p.OPT.RESERVED)
```

Now let's clean a sample tweet containing a reserved word (RT) and a URL:

Click here to view code image

```
In [3]: tweet_text = 'RT A sample retweet with a URL https://nasa.gov'
In [4]: p.clean(tweet_text)
Out[4]: 'A sample retweet with a URL'
```

## 12.13 TWITTER STREAMING API

Twitter's free Streaming API sends to your app randomly selected tweets dynamically as they occur—up to a maximum of one percent of the tweets per day. According to InternetLiveStats.com, there are approximately 6000 tweets per second, which is over 500 million tweets per day.³ So the Streaming API gives you access to approximately five million tweets per day. Twitter used to allow free access to 10% of streaming tweets, but this service—called the fire hose—is now available only as a paid service. In this section, we'll use a class definition and an IPython session to walk through the steps for processing streaming tweets. Note that the code for receiving a tweet stream requires creating a custom class that inherits from another class. These topics are covered in Chapter 10.

³ http://www.internetlivestats.com/twitter-statistics/.

### 12.13.1 Creating a Subclass of StreamListener

The Streaming API returns tweets as they happen that match your search criteria. Rather than connecting to Twitter on each method call, a stream uses a persistent connection to push (that is, send) tweets to your app. The rate at which those tweets arrive varies tremendously, based on your search criteria. The more popular a topic is, the more likely it is that the tweets will arrive quickly.

You create a subclass of Tweepy's `StreamListener` class to process the tweet stream. An object of this class is the listener that's notified when each new tweet (or other
