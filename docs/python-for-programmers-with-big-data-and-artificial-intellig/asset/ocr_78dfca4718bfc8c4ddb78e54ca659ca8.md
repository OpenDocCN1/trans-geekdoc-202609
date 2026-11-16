Now, let’s get the top five trending topics for New York City (WOEID 2459115). The following code performs the same tasks as above, but for the different WOEID:

lick here to view code image

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

# 12.11.3 Create a Word Cloud from Trending Topics

In the “ atural Language Processing” chapter, we used the WordCloud library to create word clouds. Let’s use it again here, to visualize New York City’s trending topics that have more than 10,000 tweets each. First, let’s create a dictionary of key–value pairs consisting of the trending topic names and tweet_volumes:

lick here to view code image

```
In [47]: topics = {}
In [48]: for trend in nyc_list:
    ...:     topics[trend['name']] = trend['tweet_volume']
    ...:
```

Next, let’s create a WordCloud from the topics dictionary’s key-value pairs, then output the word cloud to the image file TrendingTwitter.png (shown after the code). The argument prefer_horizontal=0.5 suggests that 50% of the words should be horizontal, though the software may ignore that to fit the content:

lick here to view code image

```
In [49]: from wordcloud import WordCloud
```