
在查看网站的缓存版本时，尝试点击标记为“纯文本版本（Text-only version）”的链接。这能更好地展示 Google 看到的内容。我已经数不来通过这个技巧发现了多少隐藏链接了。

关于使用缓存的重要性，我最喜欢的例子之一是我在 SEOmoz 的前同事与一家餐厅评论网站 `yelp.com` 合作时。Yelp 正在实施一套基于 IP 地址和 Cookie 的复杂地理定位系统，自动将用户重定向到相应的 `yelp.com` 城市版本。由于某种原因，Yelp 在 Google 搜索结果遇到了问题。检查缓存后，我的同事发现，每当 `Googlebot` 爬取 Yelp 时，Yelp 都会被自动重定向到加利福尼亚州 Mountain View（Google 总部所在地）版本的站点。哎呀！在我的同事指出这一点后，该问题很快得到解决，Yelp 的流量随之增长。

*   **站点 (site)**：`site` 指令用于将搜索查询限制在特定站点。这对于诊断索引问题非常有帮助。我通常开始单独使用 `site` 指令（`site:techmeme.com`）。这个简单的查询可以告诉你两个重要的点：
    *   首先，它让你对网站的主要板块有一个大致的了解。它还让你了解 Google 索引了多少个页面。如果你知道某个站点只有 100 个页面，而此查询返回了 100,000 个结果，你就知道自己存在重复内容问题。
    *   此外，它让你意识到该站点上的一些子域名。这对于理解 Google 如何认为一个站点是如何组织的非常有帮助。

*   **URL 中包含 (inurl)**：该指令将搜索结果限制为查询词出现在 URL 中的结果。这在与 `site` 指令结合使用时最有用（`site:www.seomoz.org inurl:"Rand Fishkin"`）。大多数 SEO 专业人士发现这种技术对于识别由 URL 参数引起的重复内容最有用（`site:www.example.com inurl:"sessionid"`）。当我在识别出一个有问题的参数后，我会使用它来找到该参数出现的所有地方。

*   **标题中包含 (intitle)**：与 `inurl` 指令类似，`intitle` 指令将结果限制为查询词出现在标题标签（title tag）中的结果。这对于许多事情都有帮助，包括盗版（`intitle:"index of mp3"`）、虚荣搜索（`intitle:"danny dover"`）以及与 SEO 相关的内容，如重复标题标签检测（`intitle:"my company: Best product ever page"`）。

*   **+**：加号直接放在术语之前，告诉 Google 搜索精确的术语，而不是同义词。例如，搜索 `ghw bush` 将返回假设你指的是“George Herbert Walker Bush”的结果。然而，搜索 `+ghw bush` 将返回假设你想要在结果中特定引用“GHW”的结果。

*   **-**：减号是过滤查询的极大助手，它可以与特定的查询词连用（`cubs -chicago -baseball` 将向你显示不包含 Chicago 或 baseball 的“cubs”结果），或与本节讨论的特定运算符结合使用。搜索 `"danny sullivan" -site:searchengineland.com` 将返回关于 Danny Sullivan 的结果，这些结果出现在 `SearchEngineLand.com` 之外的任何地方。该运算符的作用与过滤标题内容（`music -intitle:mp2`）和 URL 内容类似（`site:nytimes.com –inurl:pagemode=print` 显示来自 `nytimes.com` 的所有不是“打印友好”版本的已索引页面）。

*   **|**：管道符号代表“或（OR）”搜索，可以与普通查询词或本节列出的指令一起使用，特别是当你要在给定数据集中寻找多个项目时。例如，`site:example.com inurl:sessionid|jsessionid` 将在 `example.com` 的索引 URL 中找到包含“sessionid”或“jsessionid”的 URL。同样，`site:seomoz.org danny|rand` 将返回 `SEOmoz.org` 中正文中包含“danny”或“rand”的页面（该运算符也会包含同时包含“danny”和“rand”的页面，因此它是一个真正的“和/或”运算符，而不是“异或”运算符）。

Google 中的搜索引擎指令必须以小写字母开头，否则它们无法正常工作。

### 这些查询可以回答的常见问题

正如我之前提到的，你可以使用这些查询快速回答一些关键问题。

#### 此页面是否被索引？

要回答这个问题，你只需要搜索带有 `inurl` 指令的 URL 即可。例如，查询 `inurl:"digg.com/users/jayadelson"` 会检查 Digg CEO 的个人资料是否被索引。提示：是的。

#### 此页面是否存在重复内容问题？

如果你不得不问这个问题，答案很可能是肯定的。为了确定，你可以使用之前讨论过的任何搜索引擎指令进行检查。或者，你可以使用我首选的方法，使用 `site` 指令搜索页面上的完整句子。例如，查询 `site:google.com "Gmail stores, processes and maintains your messages, contact lists and other data related to your account in order to provide"` 显示 Google 将其隐私政策发布在两个 URL 上。啧，啧。

#### 忽略的结果 (Omitted Results)

有时 Google 会在搜索时掩盖相似的结果。当它这样做时，它会通过一个显示“省略的结果（omitted results）”的链接来提供指示。在这种情况下，点击此链接以查看 Google 认为重复的页面是非常重要的。

#### 关于此域名上有多少页面被索引

这个问题可能是危险的，因为返回的数字并不总是准确的。主要的搜索引擎在世界各地设有数据中心，这些中心包含不同 URL 数量的不同索引版本。这意味着如果你检查一个站点的索引页面数量，它可能会取决于你当时访问的是哪个数据中心。（注意：你正在访问的数据中心在搜索结果页面并不公布。）如果客户向你索索引数量，你可以通过搜索 `site:example.com` 并使用结果数量来生成粗略估计。

## 搜索引擎提供的工具

正如我已经暗示过的，你可以使用这些查询来快速回答一些关键问题。

随着 SEO 变得流行并成为一个行业，搜索引擎开始提供更多关于其数据的信息。它从前节列出的查询开始，最终变成了为了让我们 SEO 人员工作工作的工具。Bing 提供了一套名为 Webmaster Tools 的工具，但它远没有 Google 的 Webmaster Central 有用。两个最流行且预计长期存在的搜索引擎提供的工具是 Google Webmaster Central 和 Google AdWords Keyword Tool。（Bing，请赶上来。我们需要你的帮助。）

注意：另外，我应该指出，曾经存在过名为 Yahoo! Site Explorer 的工具，但由于微软收购了雅虎搜索，加上该工具的前景不确定，我将不再本书的这一版中介绍该工具。

*   `Google AdWords Keyword Tool`：该工具可以在 [`adwords.google.com/select/KeywordToolExternal`](https://adwords.google.com/select/KeywordToolExternal) 访问，并在图 3-4 中显示。

通过 `Google AdWords Keyword Tool`，你可以看到 Google 关于特定术语每月搜索次数的特定信息。这对于进行关键词研究以及决定特定页面应该针对哪个词非常有帮助。

注意：如果你没有 AdWords 账户（完全访问该工具的数据需要该账户），`Google Insights for Search` 是另一个极佳的工具，它可以让你识别关键词趋势并同时比较多五个短语的相对流行程度：`www.google.com/insights/search/`。

图 3-4： Google AdWords Keyword Tool

![f0304.tif](img/f0304_fmt.jpg)

*   `Google Webmaster Central`：该工具可以在 `www.google.com/webmasters/` 访问，并在图 3-5 中显示，下一节将讨论特定的 Web 站长工具报告。

图 3-5： Google Webmaster Central

![f0305.tif](img/f0305_fmt.jpg)

`Google Webmaster Central` 允许你为网站设置特定设置，并查看 Google 如何看待你网站的特定指标。这些指标包括链接概况详情和爬取统计数据。

我会在以下情况下使用这些工具：

*   查看关键词的相对竞争力（`Google AdWords Keyword Tool`）
*   检查 Google 是否已经识别出客户网站的任何问题（`Google Webmaster Central`）
*   更改网站的 Google 特定设置（`Google Webmaster Central`）

### 关键数据点

在使用这些工具时，以下是你需要密切关注的关键数据点：

*   `Google AdWords Keyword Tool`：`Global Monthly Search Volume`（全球每月搜索量）：此指标显示了给定单词或短语的全球搜索近似次数。目前还不清楚该指标的准确性如何，但经验证据表明所有数据都接近真实。遗憾的是，这是我们目前所能做的。SEO 专家使用这些数据来帮助确定关键词的选择。

#### 检查单词的变体

使用此工具比较同一个单词的不同变体之间的相对价值非常有益。例如，在写作时，查询“music video”（音乐视频）在全球的搜索次数比“music videos”多出 11,100,000 次。在这种情况下，以及许多其他情况下，增加一个“s”就会产生巨大的差异。

*   `Google AdWords Keyword Tool`：`Advertiser Competition`（广告商竞争）：对我们来说的是，这个指标比上一个更不准确。它被描为一个绿色条，而不是人工四舍五入的数字。拜托，Google！这些信息对于广告商竞争力的粗略估算有用。这仅适用于对 Google 关键词竞价的广告商，并且仅与自然搜索结果的竞争力相关。专业的 SEO 专家将其与全球搜索量结合使用，寻找高流量、低竞争的关键词。这不是一门精确的科学，但再次强调，这是我们目前拥有的。

#### 这些工具可以回答的常见问题

这两个 Google 工具可以帮助你回答两个重要问题。

##### 编写特定关键词的最佳方法是什么？

回答这个问题的最佳方法是使用 `Google AdWords Keyword Tool`，同时提交关键词的多个变体并勾选 `Use Synonyms`（使用同义词）复选框。正如我在本节早前的音乐视频示例中提到的，一个字母就能对流量产生巨大的影响。

### Google 站长工具 (Google Webmaster Tools)

Google 站长工具集 (`GWT`) 是收集有关你网站性能的 Google 特定数据以及发现 Google 正确查看网站的潜在障碍的极佳方法。某些报告包含不特别具有操作性的数据，而另一些报告显示了你可以立即修复并获得即时收益的错误。接下来的章节将从高层次讨论 `GWT`，然后逐条报告 `GWT` 讨论的问题——以及你应该寻找什么（如果有的话）。

## 关键数据点

*   `Google Webmaster Central`：对于所有站长来说，这是一个极其重要的资源。它本质上是 Google 索引中网站的控制面板。在写作时，此界面提供了迁移域名、设置位置偏好、检查常见 SEO 问题、分析链接概况和导出重要 SEO 工具。我强烈建议每位 SEO 专家都注册此工具并验证他们客户的网站。通过这样做，他们可能会对自己的网站以及 Google 如何解读这些网站获得新的见解。

#### 站长工具可以回答的常见问题

这些工具可以帮助你回答以下问题。

#### Google 如何看待我的网站？

这是一个大问题，本章中随后的各个报告结合在一起，提供了关于 Google 如何解读你网站内容的相当全面视角。

#### 如果我被惩罚了，如何请求 Google 重新收录？

Google 认为其索引和服务是私有的，并保留出于任何理由排除任何人的权利。当 Google 搜索质量人员发现某个网站违反了 Google 站长指南 时，他们可以降低相关链接权重、手动惩罚网站的排名能力或从 Google 索引中完全删除网站。导致惩罚的常见示例包括买卖链接、欺骗（向搜索引擎显示一种内容向普通访问者显示另一种内容）、关键词填充和操纵重定向。幸运的是，如果你认为你的网站受到了不公正的，你可以请求 Google 重新收录。

注意：要请求重新收录进 Google 索引，请访问 `www.google.com/webmasters/tools/reconsideration`。确保导致你惩罚的问题已经修复，并准备好解释它是发生的。这份道歉表单可能回答起来并不舒服，但它通常是让被封禁网站返回 Google 索引的唯一方法。

据报道 Google 会手动阅读收到的每份重新收录请求。从提交到采取（假设 Google 确实采取行动）大约三个月。在提交重新收录请求之前，最好检查相关网站是否有任何违反 Google 站长指南的迹象。一旦你确定客户网站对搜索引擎友好并遵守 Google 站长指南，你就可以在 Webmaster Central 仪表板中提交重新收录请求。这样做之后，敲敲木头，往肩膀后撒撒盐，并跳七天以求好运。你需要能得到的所有运气。

交叉引用 你可以在第 5 章中找到重新收录请求示例。

以下是对 Google Webmaster Tools（网站管理员工具）报告的深入探讨。书中的章节标题与 Webmaster Tools 左侧栏中的特定章节名称对应。虽然某些报告对你网站的解释相当是二元化的（例如，`XML` 站点地图要么有效要么无效），但许多数据是技术性的，不会被简单地标记为“好”或“坏”，也不会提供具体的建议。相反，在大多数情况下，Google 只是向你展示数据，而由你来进行解读并采取行动。后续章节目的是帮助你决定哪些报告是需要关注的，以及在改进网站各个方面时应该采取行动的阈值。

## Dashboard（仪表板）

`GWT` 仪表板提供了网站性能的快速快照，显示以下问题的顶层数据：

*   热门搜索查询
*   爬取错误类型及其计数
*   指向你网站的链接
*   关键词
*   站点地图

每个报告快照都有指向其完整报告的链接，将在后续章节中讨论。

仪表板最适合快速发现异常情况，例如搜索查询激增或爬取错误，以及发现 `XML` 站点地图无效的迹象。

## Messages（消息）

此页面列出了 Google 发给你的消息，专门关于你的网站的消息。消息包括新验证的所有者通知、`Sitelinks`（站点链接）的变化，以及如果你的网站含有恶意软件或可能违反 Google 质量准则的重要通知。每个客户的网站每周至少检查一次此区域。

`GWT` 左侧导航中的 `Message center`（消息中心）显示特定域的消息。如果你在 `GWT` 中验证了多个网站，最好在 `GWT` 的主页 `www.google.com/webmasters/tools/home` 查看所有消息。此页面汇总了你 `GWT` 组合中所有域的所有消息。

## Site Configuration（站点设置）

`Site Configuration` 报告显示了 Google 如何与你的网站交互。以下章节讨论了网站和 Google 之间发送的优化用户体验的特定信号。

### Sitemaps（站点地图）

`Sitemaps` 报告显示你（或任何已验证网站的其他人）提交的每个站点地图，以及最近的抓取日期、状态（有效或无效）和类型（通用、移动端等）。

它还显示了索引的 URL 数量，并与 `XML` 文件中的 URL 数量进行对比。这是查看站点地图 URL 有多少比例实际进入 Google 索引的有效方法。

最后，你也可以从此报告提交站点地图，前提是实际文件位于你的域名服务器上。（也就是说，你不能从计算机上传站点地图文件。）

### Crawler Access（爬虫访问）

此多功能报告允许你对网站执行并诊断各种与机器人相关的爬取规则：

*   测试你的 `robots.txt` 文件：此面板显示你当前 `robots.txt` 文件的 `HTTP` 状态码和最后下载时间。如果出现 `Parse results`（解析结果）部分将逐行检查你的文件，识别你在文件中声明任何站点地图位置，解释你添加的任何 `disallow` 或 `user agent` 行，并识别任何编码错误。要测试对 `robots.txt` 文件的假设性更改，请更改 `Text of http://www.example.com/robots.txt` 字段的内容，向 `URLs` 字段添加特定 URL，并选择特定的 `user agent`。

### Robots.txt Errors（robots.txt 错误）

`robots.txt` 有几点需要注意：

*   `robots.txt` 报告显示 `XML` 错误：首先，`robots.txt` 显示 `XML` 错误。
*   `robots.txt` 报告显示 `XML` 错误：`robots.txt` 显示 `XML` 错误。
*   `robots.txt` 报告显示 `XML` 错误：`robots.txt` 将它们从索引中移除。
*   生成自定义 `robots.txt` 文件：此工具帮助你根据需要创建自定义 `robots.txt` 文件。
*   移除 URL：如果你有某些 URL 出现，请使用此工具。

## 参数处理
