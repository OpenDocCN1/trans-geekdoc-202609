

在新的任务界面中，设置 URI 爬虫（URI Spider），并将初始主机目标设置为我们的目标。选项中包含的设置还包括爬取深度（默认为 10）以及最大爬取页数的限制。默认配置将从页面内容提取 DNS 记录类型、电话号码（PhoneNumbers）和电子邮件地址（EmailAddress）实体。当想要提取元数据时，将 `extract-uris` 选项设置为 true 非常重要。图 12.8 显示了此类设置选项的 URI 爬虫界面。

# 开始

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

爬虫可以识别数百种文件类型并解析其内容元数据。Intrigue 支持超过 300 种文件格式，包括 DOC、DOCX 和 PDF 等常见格式，以及 application/ogg 这样的特殊类型和许多视频格式。

当任务执行时，屏幕将切换到任务结果页（图 12.9）。该页面将显示正在运行的实体列表。左侧的终端窗口也将显示扫描和提取过程的进度。

![](img/ceaab52f5a948b18995b8efe89758781_275_0.png)

图 12.9

任务完成后，终端窗口将显示“task complete”（任务完成）。要查看扫描结果，点击导航栏中的“Entities”（实体）按钮。在实体页面上，统计区域（图 12.10）将汇总从文档元数据中发现并提取的所有不同实体。

查看结果摘要，这确实非常令人印象深刻。结果包括 31 个域名、1 个电话号码、5 个名称和 2 个 AWS S3 存储桶（buckets）！

Intrigue 还将自动连接到发现的存储桶。要查看有关事件的信息，请点击统计区域中的 AWS Bucket 链接。图 12.11 显示了实体列表。

从这里，点击你想探索的桶。图 12.12 显示了单个实体页面，其中列出了从 AWS 存储桶中发现（并下载）的项列表。

# 统计

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
别名 (Alias): 326
Aws3Bucket:

# FOCA

在 Windows 上，发现 PDF、DOC、JPG、FOCA。

FOCA 是一种用于 Windows 的开源工具，用于发现元数据。FOCA 还可以分析各种格式，但不限于 PDF、XLS、PPT 等。FOCA 的一个非常实用的功能是它可以根据域名组织项目（可以在 domains 部分找到）。

# 开始项目

当 FOCA 打开时，第一步是设置项目。图 12.13 显示了将项目设置为 Microsoft 的界面。这对经常分析元数据的研究人员来说特别有用。

在 FOCA 创建项目后，元数据发现的下一步是元数据树项。图 12.14 显示了点击树项后的元数据区域。FOCA 会自动选择所有扩展。在屏幕上，你可以通过在右上角的“搜索引擎”部分选择 Bing 和 DuckDuckGo 来扩大搜索范围，不仅限于 Google。

第 12 章 ■ 文元数据 263

![](img/ceaab52f5a948b18995b8efe89758781_279_0.png)

图 12.14

注意：不要忘记在设置中指定 API 密钥。这种类型的搜索需要对 Google 以及其他搜索引擎的访问，这几乎会被会被标记或阻止。使用 API 密钥运行 Google 或 Bing 搜索将缓解某些限制。

当你准备好启动扫描时，点击全部搜索按钮。任何发现的文档将显示在网格区域。
所有发现的文档最初在下载列中标记为 x。这表示文件尚未下载。右键点击任何文档将显示一个可以对文档执行的操作菜单（如图 12.15）。
OCA 要求你在分析或提取任何元数据之前先下载文档。OCA 还可以发现隐藏子域名。如果文档尚未下载，下载列将显示 x。下载文档后，x 将变为 ●，表示文件已成功下载（见图 12.16）。

# 提取元数据

下载文档后，你将能够提取存储在其中的任何元数据。要分析存储在文件中的元数据，首先点击提取元数据，然后分析元数据（参考图 12.15）。如果文件中发现了元数据，元数据文件夹将相应更新。

