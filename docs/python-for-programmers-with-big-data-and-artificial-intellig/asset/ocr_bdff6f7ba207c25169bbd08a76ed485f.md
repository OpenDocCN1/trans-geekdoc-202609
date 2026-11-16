```
n [50]: wordcloud = WordCloud(width=1600, height=900, 
...	 prefer_horizontal=0.5, min_font_size=10, colormap='prism', 
...	 background_color='white')
...
In [51]: wordcloud = wordcloud.fit_words(topics)
In [52]: wordcloud = wordcloud.to_file('TrendingTwitter.png')
```

The resulting word cloud is shown below—yours will differ based on the trending topics
the day you run the code:

![](bbox=[0.125, 0.265, 0.94, 0.6])

# 12.12 CLEANING/PREPROCESSING TWEETS FOR ANALYSIS

Data cleaning is one of the most common tasks that data scientists perform. Depending on
how you intend to process tweets, you’ll need to use natural language processing to
normalize them by performing some or all of the data cleaning tasks in the following table.
Many of these can be performed using the libraries introduced in the “ atural Language
rocessing (NLP)” chapter:

| Tweet cleaning tasks |
| --- |
| Converting all text to the same case |
| Removing stop words |