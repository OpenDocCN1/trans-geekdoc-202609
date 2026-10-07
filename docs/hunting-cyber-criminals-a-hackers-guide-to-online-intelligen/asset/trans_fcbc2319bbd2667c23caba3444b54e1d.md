

# 第 16 章 搜索社交媒体

OSINT.rest (www.osint.rest) 是一个巨大的 API，允许你收集有关目标的媒体信息。你可以在命令行中使用 CURL 命令查询该 API，或者使用像 Postman (https://www.getpostman.com) 这样的工具。这是一个付费服务——你可以批量购买 API 密钥和查询。OSINT.rest 支持针对以下内容的 API 搜索：

- 通过电话或邮箱搜索
- Facebook（照片、页面、视频、用户、帖子、点赞、地点）
- Instagram（通过别名搜索）
- 图像搜索
- Twitter 搜索
- Foursquare
- SL DB
- VK.com
- MySpace

在查看 OSINT.rest API 文档时，你会发现一个名为“Run in Postman”的按钮。点击此按钮可以将 API 直接加载到你的 Postman 应用中（目前支持 Windows 或 Mac）。
左侧的菜单将填充来自 OSINT.rest 的搜索项。图 16.1 显示了加载了 OSINT.rest API 连接的 Postman 应用，并高亮了“Search Information by Phone”（通过手机搜索信息）选项。

![](img/ceaab52f5a948b18995b8efe89758781_365_0.png)

图 16.1

在我们的测试中，我输入了自己的手机号。图 16.2 中的窗口显示了此搜索的成功结果。
此 API 仅适用于美国号码，但如果你需要反向查询电话号码的帮助，这些结果显然非常有用。

![](img/ceaab52f5a948b18995b8efe89758781_366_0.png)

图 16.2

OSINT.rest 在 Facebook 搜索方面有近百种不同的选项，包括搜索用户、用户朋友、对帖子进行评论的人、视频、页面等功能。

对于我们的第一次搜索，让我们使用 Nathan Wyatt 的个人资料，此人在 2017 年因为黑入 Pippa Middleton 的个人资料被定罪并判处监狱。截至 2019 年，Nathan Wyatt 正在争取反对与 [The Dark Overload](https://www.dailymail.co.uk/news/article-6578213/Stay-home-father-hacked-hacking-fights-extradition-US.html) 犯罪相关的美国引渡。

在 Facebook 上简单搜索将显示他的公开 Facebook 个人资料。图 16.3 显示了他的 Facebook 页面以及 URL 栏中为 100010064775327 的个人 ID。

拥有目标的 Facebook ID 为我们省去了查找的步骤。大多数搜索都需要该 ID，因此你最终需要找到它。让我们深入研究 OSINT.rest 的功能。

知道目标已连接是识别其他威胁行为者或其他有共同联系的人非常简单的方法。获取某人朋友的 JSON 列表只需在查询参数中输入他们的 Facebook ID。图 16.4 显示了此查询的输出。

![](img/ceaab52f5a948b18995b8efe89758781_367_0.png)

图 16.3

- 新集合 (New Collection)

| KEY | VALUE | DESCRIPTION |
| --- | --- | --- |
| query | 10000164775327 | Facebook 用户 ID |
| limit | 1000 | 列表限制 (max=1000) |
| offset | Description | 描述 |

图 16.4

> 注意：这里有一个关于了解某人的朋友可能重要的特定例子。之前我正在寻找一个特定的威胁行为者（我知道他的真实姓名）。我正在查看他的朋友列表，其中有几个人引起了我的注意。在查看他们的 Facebook 个人资料和朋友列表后，我注意到他们实际上是目标的朋友！这是一个立即的切入点，但如果我没有花时间查看他的朋友列表，就不会发现。

我们可以从输出可以看出 Nathan Wyatt 有 77 个 Facebook 朋友。此输出还给了我们朋友的姓名、ID 和直接 URL。使用 Maltego 可以让这个过程变得更容易，我们在文中演示这一点。

我们知道别名 "Craftyockey" 与 Nathan Wyatt 的所有公开新闻来源直接相关联，所以这是一个很好的开始。对于此列表，让我们尝试左侧的 Instagram 选项。图 16.5 显示了 "Craftyockey" 的查询结果。

![](img/ceaab52f5a948b18995b8efe89758781_368_0.png)

图 16.5

此 API 返回了 Instagram 上所有 Craftyockey 的信息。我们只有 20 个结果，所以查看所有结果是值得的。再尝试一个。

# 另一个目标 (Another Subject)

在下一个例子中，让我们查找朋友 Christopher Meunier。由于 Facebook 的搜索结果大部分是离线的，我故意拼错了了他的名字，结果出现了一个名为 Chris Maunier 的个人资料。为了执行任何搜索，我们需要知道他的 ID。我们要做的只是在 "Get Facebook ID by Profile" API 搜索中输入用户名（图 16.6）。

| Parameters | Authorization (8) | Body | Pre-request Tests | Cookies (0) |
| --- | --- | --- | --- | --- |
| Query | | christopher.maunier.923 | | |
| KEY | | Alias | | |
| alias | | Value | | |
| Body | Headers (10) | Results: 200 OK Time: 161 ms Size: 374 B | | |
| Pretty | | Raw | | |
| | {"id":"1000325741589"} | | | |

图 16.6

运行搜索后即可轻松获得他的 Facebook ID 1000325741589。遗憾的是，Chris 的资料大部分私密的，但我们仍然可以从中获得大量信息。开始，“Get Facebook User Profile by ID”（图 16.7）将返回目标的 Facebook 个人资料摘要，包括最近的帖子、全名和照片。从这些结果中我们可以立即看到照片的 URL。使用 OSINT.rest 还包括反向搜索。让我们首先导航到这个 URL。用户 1000325741589 的公开帖子（图 16.8）包含说明。现在有了个人资料，我们可以以后保存它或复制 URL 并进行反向搜索。

| History | Collections | API Beta |
| --- | --- | --- |
| + Get Facebook User Profile by ID | Examples (1) | |
| + New Collection | | |
| + Facebook Video | GET https://api.facebook.com/search/user?q=christ.maunier_923 | Save |
| + Facebook Photos | Params (Headers) Body Pre-request Tests Code (0) | |
| + Facebook Users | Query Parameters | Bulk Edit |
| | query VALUE | | |
| | christ.maunier_923 Facebook User ID | | |
| | Key Value | Description Status: 200 OK Time: 8.9ms Size: 8 KB | | |
| | Body Collections (10) Results | Download | | |
| | Preview JSON | | | |
| 1 | "id": "135089327415693", | | | |
| 2 | "name": "Christopher Maunier", | | | |
| 3 | "type": "user", | | | |
| 4 | "location": "Temporary account for hunting people" | | | |
| 5 | "gender": "female", | | | |
| 6 | "featured_count": null, | | | |
| 7 | "profile_pic_square": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 8 | "image": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 9 | "photo_id": "135089327415693", | | | |
| 10 | "album": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 11 | "id": "13190933440671", | | | |
| 12 | "name": "Christopher Maunier", | | | |
| 13 | "type": "user", | | | |
| 14 | "location": "Profile pictures", | | | |
| 15 | "gender": "female", | | | |
| 16 | "featured_count": null, | | | |
| 17 | "profile_pic_square": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 18 | "image": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518-m.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
| 19 | "photo_id": "13190933440671", | | | |
| 20 | "album": "https://look-aside.fbcdn.net/v3/r/u1-b/163/d1b/c3/580604332715709555529509406549518.jpg_cat_content=fr1-3.xdb00002e4c", | | | |
 }

