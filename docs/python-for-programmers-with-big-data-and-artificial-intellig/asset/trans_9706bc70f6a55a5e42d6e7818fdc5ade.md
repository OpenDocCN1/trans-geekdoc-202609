

![](img/34b7fc2f1ee27beb73bca14927d42340_514_0.png)

这些推文被截断了（如 ）所示，意味着它们可能使用较新的 280 字符推文限制。我们将很快使用 `extended_tweet` 属性来访问此类推文的完整文本。

在前面的代码片段中，我们选择直接调用 `user_timeline` 方法，并使用 `count` 关键字参数来指定要检索的推文数量。如果您希望获取每次调用的最大推文数量（200）以上的推文，则应该使用 `Cursor` 来调用 `user_timeline`，如前面所示。请回顾，如果需要，`Cursor` 会通过多次调用该方法自动分页浏览结果。

## 从您自己的时间轴获取最近的推文

您可以调用 API 方法 `home_timeline`，如下所示：

```
api.home_timeline()
```

以获取您主页时间轴上的推文 6——即您的推文和您关注的人的推文。此方法调用 Twitter 的 `statuses/home_timeline` 方法。7 默认情况下，`home_timeline` 返回最近的 20 条推文，但一次最多可获取 200 条。同样，如果要从主页时间轴获取超过 200 条推文，则应使用 Tweepy `Cursor` 来调用 `home_timeline`。

6 特指您用于向 Twitter 进行身份验证的账户。

7 https://developer.twitter.com/en/docs/tweets/timelines/api-reference/get-statuses-home_timeline.

## 12.10 搜索最近的推文

Tweepy API 的 `search` 方法返回与查询字符串匹配的推文。根据该方法的文档，Twitter 仅为过去七天的推文维护搜索索引，并且搜索不保证返回所有匹配的推文。方法 `search` 调用 Twitter 的 `search/tweets` 方法 8，默认一次返回 15 条推文，但最多可返回 100 条。

8 https://developer.twitter.com/en/docs/tweets/search/api-reference/get-search-tweets.

## 来自 tweetutilities.py 的实用函数 print_tweets

在本节中，我们创建了一个名为 `print_tweets` 的实用函数，它接收对 API 方法 `search` 调用的结果，并对每条推文显示用户的 `screen_name` 和推文的 `text`。如果推文不是英文，且 `tweet.lang` 不是 `'und'`（未定义），我们还将使用 TextBlob 将推文翻译成英文，就像您在“自然语言处理（NLP）”章节中所做的那样。要使用此函数，请从 `tweetutilities.py` 导入它：

单击此处查看代码图像

```
In [24]: from tweetutilities import print_tweets
```

仅显示该文件中 `print_tweets` 函数的定义如下：

单击此处查看代码图像

```
def print_tweets(tweets):
    """For each Tweepy Status object in tweets, display the
    user's screen_name and tweet text. If the language is not
    English, translate the text with TextBlob."""
    for tweet in tweets:
        print(f'{tweet.screen_name}:', end=' ')

        if 'en' in tweet.lang:
            print(f'{tweet.text}\n')
        elif 'und' not in tweet.lang:  # translate to English first
            print(f'\n ORIGINAL: {tweet.text}')
            print(f'TRANSLATED: {TextBlob(tweet.text).translate()}\n')
```

## 搜索特定单词

让我们搜索关于 NASA 火星机会号探测器的三条最近推文。`search` 方法的 `q` 关键字参数指定查询字符串，指示要搜索的内容，而 `count` 关键字参数指定要返回的推文数量：

单击此处查看代码图像

```
In [25]: tweets = api.search(q='Mars Opportunity Rover', count=3)

In [26]: print_tweets(tweets)
Jacker760: NASA set a deadline on the Mars Rover opportunity! As the dust c...
https://t.co/KQ7xaFgrzr

hivak32637174: RT @Gadgets360: NASA 'Cautiously Optimistic' of Hearing Bac
https://t.co/OIiTTwRvFq

ladyanakina: NASA's Opportunity Rover Still Silent on #Mars. https://t.co/r
```

与其他方法一样，如果您计划请求的结果超过单次 `search` 调用可返回的数量，则应使用 `Cursor` 对象。

### 使用 Twitter 搜索运算符进行搜索

您可以在查询字符串中使用各种 Twitter 搜索运算符来细化搜索结果。下表显示了几个 Twitter 搜索运算符。可以组合多个运算符来构建更复杂的查询。要查看所有运算符，请访问

```
https://twitter.com/search-home
```

并单击 **operators** 链接。

| 示例 | 查找包含的推文 |
|---|---|
| python twitter | 隐式逻辑 *和* 运算符—查找包含 *python 和 twitter* 的推文。 |
| python OR twitter | 逻辑 *或* 运算符—查找包含 *python 或 twitter 或两者* 的推文。 |
| python ? | ?（问号）—查找询问关于 *python* 问题的推文。 |
| planets -mars | -（减号）—查找包含 *行星* 但不包含 *火星* 的推文。 |
| python :) | :)（笑脸）—查找包含 python 的 *积极情绪* 推文。 |
| python :( | :|（悲伤脸）—查找包含 python 的消极情绪推文。 |

让我们使用 `from` 和 `since` 运算符获取自 2018 年 9 月 1 日以来来自 NASA 的三条推文——执行此代码时，您应该使用七天前的日期：

单击此处查看代码图像

```
In [27]: tweets = api.search(q='from:nasa since:2018-09-01', count=3)
In [28]: print_tweets(tweets)
NASA: @WYSIOW Our missions detect active burning fires, track the transport https://t.co/jx2iUoMlIy
NASA: Scarring of the landscape is evident in the wake of the Mendocino Co https://t.co/Nboo5GD90m
NASA: RT @NASAglenn: To celebrate the #NASA60th anniversary, we're explori
```

### 搜索话题标签

推文通常包含以 # 开头的话题标签，用于表示重要事物，例如热门话题。让我们获取包含话题标签 #collegefootball 的两条推文：

单击此处查看代码图像

```
In [29]: tweets = api.search(q='#collegefootball', count=2)

In [30]: print_tweets(tweets)
dmcreek: So much for #FAU giving #OU a game. #Oklahoma #FloridaAtlantic #C

theangrychef: It's game day folks! And our BBQ game is strong. #bbq #atlan
```

## 12.11 发现趋势：Twitter 趋势 API

如果一个话题“病毒式传播”，您可能会有成千上万甚至数百万人同时在推特上发帖讨论。Twitter 将这些称为 **趋势话题**，并维护全球趋势话题列表。通过 Twitter 趋势 API，您可以获取带有趋势话题的地点列表以及每个地点的前 50 个趋势话题列表。

### 12.11.1 带有趋势话题的地点

Tweepy API 的 `trends_available` 方法调用 Twitter API 的 `trends/available` 9 方法，以获取 Twitter 拥有趋势话题的所有地点列表。方法 `trends_available` 返回一个表示这些地点的 _字典列表_。当我们执行此代码时，有 467 个地点带有趋势话题：

9 https://developer.twitter.com/en/docs/trends/locations-with-trending-topics/api-reference/get-trends-available.

单击此处查看代码图像

```
In [31]: trends_available = api.trends_available()
In [32]: len(trends_available)
Out[32]: 467
```

`trends_available` 返回的每个列表元素中的字典包含各种信息，包括位置的 `name` 和 `woeid`（将在下文讨论）：

单击此处查看代码图像

```
In [33]: trends_available[0]
Out[33]:
{'name': 'Worldwide',
 'placeType': {'code': 19, 'name': 'Supername'},
 'url': 'http://where.yahooapis.com/v1/place/1',
 'parentid': 0,
 'country': '',
 'woeid': 1,
 'countryCode': None}

In [34]: trends_available[1]
Out[34]:
{'name': 'Winnipeg',
 'placeType': {'code': 7, 'name': 'Town'},
 'url': 'http://where.yahooapis.com/v1/place/2972',
 'parentid': 23424775,
 'country': 'Canada',
 'woeid': 2972,
 'countryCode': 'CA'}
```

Twitter 趋势 API 的 `trends/place` 方法（稍后讨论）使用 **Yahoo! Where on Earth IDs (WOEIDs)** 来查找趋势话题。WOEID 1 代表 *全球*。其他位置具有大于 1 的唯一 WOEID 值。我们将在接下来的两个子部分中使用 WOEID 值来获取全球趋势话题和特定城市的趋势话题。下表显示了几个地标、城市、州和大陆的 WOEID 值。请注意，虽然这些都是有效的 WOEID，但 Twitter 不一定为所有这些位置提供趋势话题。

| 地点 | WOEID | 地点 | WOEID |
|---|---|---|---|
| 自由女神像 | 23617050 | 伊瓜苏瀑布 | 468785 |
| 洛杉矶，加利福尼亚州 | 2442047 | 美国 | 23424977 |
| 华盛顿特区 | 2514815 | 北美洲 | 24865672 |
| 法国巴黎 | 615702 | 欧洲 | 24865675 |

您也可以搜索与您使用纬度和经度值指定的位置相近的位置。为此，请调用 Tweepy API 的 `trends_closest` 方法，它会调用 Twitter API 的 `trends/closest` 方法。10

