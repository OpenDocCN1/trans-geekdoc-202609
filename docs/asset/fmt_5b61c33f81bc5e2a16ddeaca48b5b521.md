
[recon-ng](default) > `search pushpin`

[*] Searching for 'pushpin'...

`recon/locations-pushpins/flickr`

`recon/locations-pushpins/shodan`

`recon/locations-pushpins/twitter`

`recon/locations-pushpins/youtube`

`reporting`

每个模块都有自己的参数集和描述，你可以通过加载模块并使用 `show info` 命令来查看。让我们获取 Flickr 模块的信息：

```
[recon-ng](default) > use flickr

[recon-ng](default)[flickr] > show info
```

### Name: Flickr 地理定位搜索
Path: `modules/locations-pushpins/flickr.py`
Author: Tim
Keys: `flickr_api`
Description: 搜索指定位置范围内的媒体。

| Name | Value | Description |
| :--- | :--- | :--- |
| RADIUS | 1 | 以公里为单位是 |
| SOURCE | default | 是（详情请见 'show info'） |

Options:
```sql
SELECT DISTINCT latitude || ',' || longitude FROM locations WHERE latitude IS NOT NULL AND longitude IS NOT NULL representing a single input path to a file containing a list of inputs
```

Comments:
* 半径必须大于 0 小于 32 公里。

我们可以从模块页面看到，在使用该模块之前，我们还需要拥有地址的坐标。有很多免费工具可以实现此功能。例如是 https://www.mapdevelopers.com/geocode.php。访问该网站后，输入你所需的地址，它将返回你的经纬度。例如，我使用了密苏里州圣路易斯的市坐标。MapDevelopers.com 返回了以下内容：

```
Latitude 38.63716

Longitude -90.241648
```

现在我们有了位置坐标，让我们看看在 Pushpin 模块中能找到什么信息。首先，我们需要使用 `add locations` 命令将位置添加到 Recon-NG：

```
[recon-ng](default)[geocode] > add locations

latitude (TEXT): 38.63716

longitude (TEXT): -90.24168

street_address (TEXT):
```

这些是可以完全运行的内容。圣路易斯的经纬度已作为位置数据输入——看看该地区是否有人发推特。使用以下命令搜索 Twitter Pushpin 模块：

```
use recon/locations-pushpins/twitter
```

图 12.6 显示了运行模块后的结果示例。

```
[recon-ng](default) > recon/locations-pushpins/twitter

[recon-ng](default) > run 38.63716,-90.24164

* Collecting data for an unknown number of tweets...

* Latitude: 38.692538

* Longitude: -90.223393

* Media_Url: https://twitter.com/Bethany185/statuses/1143343913629683

* Message: What a face! Fantastic! The fabulous facts in this

* Profile_Name: Bethany

* Profile_Url: https://twitter.com/Bethany185

* School: University

* Source: Twitter

* Image: https://pbs.twimg.com/media/110285472642378593/Qj3SwXe_normal.jpg

* Date: 2019-04-06 01:47:47

* Latitude: 38.6368437

* Longitude: -90.2508463

* Media_Url: https://twitter.com/AJ_Bjacobs/statuses/11433185359900747680

* Message: #legendary #shoutout queens especially in the iu ..danella_monae_Cedes_Baby

* Profile_Name: AJ_Bjacobs

* Profile_Url: https://twitter.com/AJ_Bjacobs

* School_Name: AJ_Bjacobs

* Source: Twitter

* Image: https://pbs.twimg.com/media/86b849714642378593/II
```

在新的任务界面中，设置 URI 爬虫（URI Spider），并将初始主机目标设置为我们的目标。选项中包含的设置还包括爬取深度（默认为 10）以及最大爬取页数的限制。默认配置将从页面内容提取 DNS 记录类型、电话号码（PhoneNumbers）和电子邮件地址（EmailAddress）实体。当想要提取元数据时，将 `extract-uris` 选项设置为 true 非常重要。图 12.8 显示了此类设置选项的 URI 爬虫界面。

## 开始

| 任务 | URI 爬虫 |
|---|---|
| 实体类型 | Urn |
| 实体名称 | http://www... |
| limit | 100 |
| max_depth | 10 |
| spider_whitelist | (current domain) |
| extract_dns_records | true |
| extract_dns_record_pattern | (current domain) |
| extract_email_addresses | true |
| extract_phone_numbers | true |
| parse_file_metadata | true |
| extract_uris | true |
| user_agent | Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWeb |
| Machine | Org Asset Discovery (Active) 'Machine' 指定了每个新实体的后处理器。 |
| Iterations | 3 Iterations 'iterations' 指定了机器运行的深度。自动增强 (Auto Enrich) |

图 12.8

# 第 12 章 ■ 文元数据 259

爬虫可以识别数百种文件类型并解析其内容元数据。Intrigue 支持超过 300 种文件格式，包括 DOC、DOCX 和 PDF 等常见格式，以及 `application/ogg` 这样的特殊类型和许多视频格式。

当任务执行时，屏幕将切换到任务结果页（图 12.9）。该页面将显示正在运行的实体列表。左侧的终端窗口也将显示扫描和提取过程的进度。

![](img/ceaab52f5a948b18995b8efe89758781_275_0.png)

图 12.9

任务完成后，终端窗口将显示“task complete”（任务完成）。要查看扫描结果，点击导航栏中的“Entities”（实体）按钮。在实体页面上，统计区域（图 12.10）将汇总从文档元数据中发现并提取的所有不同实体。

查看结果摘要，这确实非常令人印象深刻。结果包括 31 个域名、1 个电话号码、5 个名称和 2 个 AWS S3 存储桶（buckets）！

Intrigue 还将自动连接到发现的存储桶。要查看有关事件的信息，请点击统计区域中的 AWS Bucket 链接。图 12.11 显示了实体列表。

从这里，点击你想探索的桶。图 12.12 显示了单个实体页面，其中列出了从 AWS 存储桶中发现（并下载）的项列表。

## 统计

总实体：101 个实体

- NetworkService: 2
- NetBlock: 3
- SoftwarePackage: 6
- PhoneNumber: 1
- Domain: 31
- AwsS3Bucket: 2
- IpAddress: 9
- Uid: 20
- SslCertificate: 1
- DnsRecord: 9
- Persons: 5
- Organization: 2

图 12.10

| 导出 CSV |
| 导出 JSON |
| 搜索: |
| 提示 (Hint): |
| 上一页 (previous) | 页面 (Page): 9 | 结果 |
| 名称 (name) |
| [Aws3Bucket: | |
| [Aws3Bucket: |
| 上一页 (previous) |
| 下页 (next): |
| 类型 (Types): |
| Intrigue:AutonomousSystem |
| Intrigue:Credential |
| Intrigue:Aws3Bucket |
| Intrigue:Credential |
| Intrigue:Record |
| Intrigue:Document |
| Intrigue:Domain |
| Intrigue:EmailAddress |
| Intrigue:File |
| Intrigue:Account |
| Intrigue:Repository |
| Intrigue:Info |
| Intrigue:Address |
| Intrigue:NetBlock |
| Intrigue:NetworkService |
| 显示 (Show) |
| 隐藏 (Hidden) |

图 12.11

在这里，点击你想要探索的桶。图 12.12 显示了从 AWS 存储桶中发现（并下载）的项列表的单个实体页面。

第 12 章 ■ 文元数据 261

Aws3Bucket:
范围 (Scoped): false
# 详情 (Details)

```
{
  "uri": "https://...",
  "interesting_files": [
    {
      "authenticated": false
    },
    "downloadable_files": [
      {
        "uri": "https://...",
        "code": "200"
      },
      {
        "uri": "https://...",
        "code": "200"
      },
      {
        "uri": "https://...",
        "code": "200"
      },
      {
        "uri": "https://...",
        "code": "200"
      }
    ]
  ]
}
```
