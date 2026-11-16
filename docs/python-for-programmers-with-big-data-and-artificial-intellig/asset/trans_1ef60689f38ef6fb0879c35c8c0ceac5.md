
以及该用户的朋友——即该用户关注的其他账户。

每个 Twitter API 方法的文档都会讨论该方法一次调用最多可返回的项目数量——这称为结果的一个 **页**。当你请求的结果数量超过给定方法可返回的数量时，Twitter 的 JSON 响应会指示还有更多页面可获取。Tweepy 的 `Cursor` 类会为你处理这些细节。一个 `Cursor` 会调用指定方法，并检查 Twitter 是否指示还有另一页结果。如果是，`Cursor` 会自动再次调用该方法以获取那些结果。此过程将持续下去，受方法速率限制的约束，直到没有更多结果可处理。如果你将 API 对象配置为在达到速率限制时等待（如我们所做的），`Cursor` 将遵守速率限制，并在调用之间根据需要等待。以下小节讨论 `Cursor` 基础知识。有关更多详细信息，请参阅 `Cursor` 教程：

http://docs.tweepy.org/en/latest/cursor_tutorial.html

### 12.9.1 确定账户的关注者

让我们使用 Tweepy Cursor 调用 API 对象的 **followers 方法**，该方法调用 Twitter API 的 `followers/list` 方法¹ 以获取账户的关注者。Twitter 默认每次返回 20 个，但你一次最多可请求 200 个。为了演示，我们将获取 NASA 的 10 个关注者。

¹ https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-followers-list.

方法 `followers` 返回包含每个关注者信息的 `tweepy.models.User` 对象。让我们先创建一个列表来存储 `User` 对象：

```
In [14]: followers = []
```

## 创建 Cursor

接下来，让我们创建一个 `Cursor` 对象，它将为 NASA 的账户调用 `followers` 方法，该账户通过 `screen_name` 关键字参数指定：

点击此处查看代码图片

```
In [15]: cursor = tweepy.Cursor(api.followers, screen_name='nasa')
```

`Cursor` 的构造函数接收作为其参数要调用的方法的名称 — `api.followers` 表示 `Cursor` 将调用 `api` 对象的 `followers` 方法。如果 `Cursor` 构造函数接收任何额外的关键字参数，例如 `screen_name`，这些参数将传递给构造函数第一个参数中指定的方法。因此，这个 `Cursor` 专门获取 @nasa Twitter 账户的关注者。

## 获取结果

现在，我们可以使用 `Cursor` 获取一些关注者。以下 `for` 语句遍历表达式 `cursor.items(10)` 的结果。`Cursor` 的 `items` **方法** 启动对 `api.followers` 的调用并返回 `followers` 方法的结果。在这里，我们将 `10` 传递给 `items` 方法以仅请求 10 个结果：

点击此处查看代码图片

```
In [16]: for account in cursor.items(10):
    ....:     followers.append(account.screen_name)
    ....:
    ....:
In [17]: print('Followers:',
    ....:     ', '.join(sorted(followers, key=lambda s: s.lower())))
    ....:
    ....:
关注者：abhinavborra BHood1976 Eshwar12341 Harish90469614 heshamkisha H
```

前面的代码片段通过调用内置 `sorted` 函数以升序显示关注者。函数的第二个参数是用于确定 `followers` 元素排序方式的函数。在这里，我们使用了一个 `lambda`，它将每个关注者名称转换为小写字母，以便我们可以执行不区分大小写的排序。

## 自动分页

如果请求的结果数量超过一次调用 `followers` 所能返回的数量，`items` 方法将通过多次调用 `api.followers` 自动“分页”遍历结果。请回顾，`followers` 默认一次最多返回 20 个关注者，因此前面的代码只需调用一次 `followers`。要一次获取最多 200 个关注者，我们可以使用 `count` 关键字参数创建 `Cursor`，如下所示：

点击此处查看代码图片

```
cursor = tweepy.Cursor(api.followers, screen_name='nasa', count=200)
```

如果你不向 `items` 方法指定参数，`Cursor` 将尝试获取账户的 _所有_ 关注者。对于大量关注者，由于 Twitter 的速率限制，这可能需要相当长的时间。Twitter API 的 `followers/list` 方法一次最多可返回 200 个关注者，Twitter 每 15 分钟允许最多 15 次调用。因此，使用 Twitter 的免费 API，你每 15 分钟只能获取 3000 个关注者。请回顾，我们已将 API 对象配置为在触达速率限制时自动等待，因此如果你尝试获取所有关注者且账户拥有超过 3000 个关注者，Tweepy 将在每 3000 个关注者后自动暂停 15 分钟并显示一条消息。就撰写本文时，NASA 拥有超过 2950 万个关注者。每小时 12000 个关注者，获取 NASA 的所有关注者需要超过 100 天。

请注意，对于此示例，我们本可以直接调用 `followers` 方法，而不是使用 `Cursor`，因为我们只获取少量关注者。我们在这里使用 `Cursor` 来展示你通常会如何调用 `followers`。在一些后续示例中，我们将直接调用 API 方法来获取仅几个结果，而不是使用 Cursors。

## 获取关注者 ID 而不是关注者

虽然你一次最多可以获取 200 个关注者的完整 `User` 对象，但通过调用 API 对象的 `followers_ids` 方法，你可以获取更多 Twitter ID 号码。这将调用 Twitter API 的 `followers/ids` 方法，该方法一次最多可返回 5000 个 ID 号码（同样，这些速率限制可能会更改）。² 你每 15 分钟最多可调用此方法 15 次，因此每个速率限制间隔可以获取 75000 个账户 ID 号码。这在与 API 对象的 `lookup_users` 方法结合使用时特别有用。这将调用 Twitter API 的 `users/lookup` 方法³，该方法一次最多可返回 100 个 `User` 对象，每 15 分钟最多可调用 300 次。因此，使用这种组合，你每个速率限制间隔最多可获取 30000 个 `User` 对象。

² https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-followers-ids.

³ https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-lookup.

### 12.9.2 确定账户关注的账户

API 对象的 `friends` 方法调用 Twitter API 的 `friends/list` 方法⁴，以获取表示账户朋友的 `User` 对象列表。Twitter 默认每次返回 20 个，但你一次最多可请求 200 个，这与我们之前讨论的方法 `followers` 相同。Twitter 每 15 分钟允许你最多调用 `friends/list` 方法 15 次。让我们获取 NASA 的 10 个好友账户：

⁴ https://developer.twitter.com/en/docs/accounts-and-users/follow-

点击此处查看代码图片

```
In [18]: friends = []

In [19]: cursor = tweepy.Cursor(api.friends, screen_name='nasa')

In [20]: for friend in cursor.items(10):
    ...:     friends.append(friend.screen_name)
    ...:
    ...:

In [21]: print('Friends:',
    ...:     ' '.join(sorted(friends,  key=lambda s: s.lower())))
    ...:

朋友：AFSpace Astro2fish Astro_Kimiya AstroAnniman  AstroDuke NASA3DPrin
```

### 12.9.3 获取用户的最近推文

API 方法 `user_timeline` 返回特定账户时间线上的推文。时间线包括该账户的推文以及该账户朋友的推文。该方法调用 Twitter API 的 `statuses/user_timeline` 方法⁵，该方法返回最近 20 条推文，但一次最多可返回 200 条。该方法只能返回账户最近的 3200 条推文。使用此方法的应用程序每 15 分钟最多可调用它 1500 次。

⁵ https://developer.twitter.com/en/docs/tweets/timelines/api-reference/get-statuses-user_timeline.

方法 `user_timeline` 返回 Status 对象，每个对象代表一条推文。每个 Status 的 user 属性引用一个 `tweepy.models.User` 对象，其中包含发送该推文的用户的信息，例如该用户的 `screen_name`。Status 的 text 属性包含推文的文本。让我们显示来自 @nasa 的三条推文的 `screen_name` 和文本：

点击此处查看代码图片

```
In [22]: nasa_tweets = api.user_timeline(screen_name='nasa', count=3)

In [23]: for tweet in nasa_tweets:
    ...:     print(f'{tweet.user.screen_name}: {tweet.text}\\n')
    ...:

NASA: 你的肠道在太空中：肠道中的微生物群起着 esp https://t.co/uLOsUhwn5p
