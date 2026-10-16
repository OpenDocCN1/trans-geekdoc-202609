
-   [另一种使用社交网络进行社会工程的方式是通过他人可能已经窃取的凭据来 compromise 一个账户。账户被 compromise 后，攻击者可以逐步接管该账户，修改密码和其他信息，同时保留联系人/好友列表。这最近发生在我在 LinkedIn 上的时候。我收到一条来自某人的推荐请求，我回复说我不认识他们。在几条来自（据称被 compromise 的）账户的不同消息中，出现了图 10.6 所示的消息。

![FIGURE 10.6 LinkedIn message](images/c10f006.png)

[**FIGURE 10.6**](#c10.xhtml#R_c10-fig-0006) LinkedIn message

攻击者会利用被 compromise 账户的联系人来尝试获取某些东西。这种类型的社会工程有很多不同的实现方式。攻击者可以使用新获取的“好友”来尝试出售商品或服务，例如。他们还可以尝试获取凭据。一旦社交工程攻击的不信任屏障被移除，几乎所有的社交工程攻击的结果都有可能出现，因为这些消息或请求是来自受信任的人。

## 网站攻击

即使你使用钓鱼攻击，也可能需要第二个元素。你可以在钓鱼攻击中加入恶意软件，这可以让你获得目标系统的访问权限。这可能比你想要的更复杂，因为它依赖于用户打开附件，或者附件利用系统中的漏洞。相比于让用户打开附件，让用户点击链接要容易得多。尤其是当电子邮件看起来合法，链接也看起来合法时。这意味着，你需要有一个网站供用户连接。如果你以钓鱼为入口，可能会先使用站点克隆，即创建一个看起来像合法站点的复制品，这样当用户连接时不会产生怀疑。

### 克隆

站点克隆是一个非常容易实现的操作。事实上，你甚至不需要克隆整个站点。你只需要克隆使页面渲染成为可能的 HTML 代码。将任何媒体文件保持在原始位置即可，因为如果它们发生变化，你可以利用这些更新。这样会让克隆站点看起来更可信。如果有人仔细观察，就会看到请求实际上是发送到合法站点而不是你的恶意站点。唯一从你的恶意站点发出的文件是控制页面渲染的 HTML。这并不意味着你不能抓取文件并本地托管。使用像 WinHTTrack 这样的工具，这是可配置的选项，如图 10.7 所示。

![FIGURE 10.7 WinHTTrack options](images/c10f007.png)

[**FIGURE 10.7**](#c10.xhtml#R_c10-fig-0007) WinHTTrack options

这些选项当然是可选的。默认情况下，WinHTTrack 不会抓取媒体文件，只会抓取 HTML。它会克隆整个站点，这意味着它会遍历所有链接。WinHTTrack 使用项目来克隆站点，因此这是一个多步骤的过程。在图 10.8 中，你可以看到在输入 URL 的那一步。你也可以输入多个 URL 以一次性下载多个站点。你需要将操作改为“Download All Sites In Pages”。你也可以使用 WinHTTrack 来测试站点而非下载它们，这意味着你可以检查书签列表以确认它们是否仍然有效。

如果你更喜欢命令行工具，也有几个可以使用的选择。其中一个是 `wget`，它用于发起网络请求并获取文件。你可以在命令行中使用 `wget` 下载文件。在 Linux 系统上，你可以获取源代码 tarball、包文件或任何不需要渲染的文件。你可以使用 `wget` 进行递归的 GET 请求，这正是镜像站点所需要的。这意味着 `wget` 会下载站点顶部的 HTML 页面并保存它，然后查找页面中的所有锚标签并逐个跟踪它们以获取这些页面或文件。在下面的代码片段中，你可以看到使用 `‑m` 参数运行 `wget` 的示例，该参数指示 `wget` 对站点进行镜像，即抓取整个站点。

![FIGURE 10.8 Site cloning with WinHTTrack](images/c10f008.png)

[**FIGURE 10.8**](#c10.xhtml#R_c10-fig-0008) Site cloning with WinHTTrack

**使用 wget 镜像网站**

```
root@quiche:~# wget -m https://www.wiley.com
 --2023-01-23 07:05:43--  https://www.wiley.com/
 Resolving www.wiley.com (www.wiley.com)… 143.204.29.19, 143.204.29.108, 143.204.29.24, …
 Connecting to www.wiley.com (www.wiley.com)|143.204.29.19|:443… connected.
 HTTP request sent, awaiting response… 301 Moved Permanently
 Location: /en-us [following]
 --2023-01-23 07:05:43--  https://www.wiley.com/en-us
 Reusing existing connection to www.wiley.com:443.
 HTTP request sent, awaiting response… 200 OK
 Length: unspecified [text/html]
 Saving to: 'www.wiley.com/index.html'
 
 www.wiley.com/index     [ <=>                ] 85.83K --.-KB/s in 0.08s
 
 Last-modified header missing -- time-stamps turned off.
 2023-01-23 07:05:44 (1.08 MB/s) - 'www.wiley.com/index.html' saved [87888]
 
 Loading robots.txt; please ignore errors.
 --2023-01-23 07:05:44--  https://www.wiley.com/robots.txt
 Reusing existing connection to www.wiley.com:443.
 HTTP request sent, awaiting response… 200 OK
 Length: 817 [text/plain]
 Saving to: 'www.wiley.com/robots.txt'
 
 www.wiley.com/robot 100%[===================>] 817 --.-KB/s in 0s
 
```

如果你想让网站在离线状态下可用，可以使用命令行开关让链接相对。为了我们的目的，我们只需要镜像站点，保持原样，通过我们自己的 web 服务器提供访问。另一个与 `wget` 类似的命令行程序是 `cURL`。不幸的是，`cURL` 没有内置功能来下载完整的网站，尽管它功能强大。你可以编写一个短脚本来拉取站点，网上也有供使用 `cURL` 而不是 `wget` 的脚本。

获取站点页面后，你需要对源代码进行相应的调整。这包括插入恶意代码以便下载，并在站点中的某个页面中加入对该代码的引用。获取站点后，你可以将某个页面的 URL 发送给目标，可能在电子邮件中。在社交工程攻击中，有时会出现多层攻击。

### 伪装攻击

伪装网站是指用户可能认为是合法的，但实际上具有恶意目的的网站。这可能是一个看起来与合法站点完全相同的站点，使用前面提到的站点克隆技术，但其完全限定域名（URL）与通常的 URL 不同。攻击者可以注册常见拼写错误的域名并等待人们访问。这种手法称为 *typosquatting*（拼写错误劫持）。例如，你可以注册 `gogle.com` 并克隆 `google.com`，在托管该站点的服务器上提供页面。你也可以称之为 *URL 劫持*。

