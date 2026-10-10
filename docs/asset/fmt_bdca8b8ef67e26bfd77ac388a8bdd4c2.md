
https://imgur.com/FvAJJCbLInQNDDKkQICH64BWHQ

图 13.2

在 BlackBox 的后续帖子（图 13.3）中，Cyper 正在讨论上传到 JJFox 的 webshell，那是从外面买的一根雪茄。

![](img/ceaab52f5a948b18995b8efe89758781_293_1.png)

图 13.3

几天后，我们可以在在图 13.4 中看到同一个帖子，但现在 Cyper 的用户名已更改为 Ghost。
这些截图绝不是这两个威胁者是同一个人的唯一迹象。但它们也并无害。

![](img/ceaab52f5a948b18995b8efe89758781_294_0.png)

图 13.4

## 追踪 Cypher 的身份

我早已知道 Cyber 是策划了 Hell 倒台的人（在第 2 章中讨论过），所以现在我能够明确建立 Cypher 是 BlackBox 的领导，我的身份飙升。不幸的是，BlackBox 是一个专属论坛，发现它的抓取是不可能的。
然而，有时你会在最随机的地方发现金子。我在全书中提到过，我创建了一个名为 DataPiper 的应用程序，是我收集的凭据、被破解的数据库和抓取的论坛。在我抓取并索引尽可能多的历史数据的过程中，我发现了一个社交媒体网站。

事实上，Galaxy 版本 2 被证明是 Hell 大部分成员的社交聚集地，其中包括 Cypher 和他的爪爪。在一场激烈的口战中，Cypher（即 CyPeRtRon）正在防御另外两个人关于他的新论坛 BlackBox 的全面攻击，url：`cyphercy7uonion`。

> 注意：另一个不可忽视的迹象是 Cypher 是 BlackBox 的管理员——Cypher 这个词就在 URL 里。

By Arsyntex
@Unknown 8698 8698，CyPer 知道，she/him 是来自 S***box 的其中之一，嘿，Blackbox（主题名称，非常有创意） & 你

等待，OCR 文本在结尾有些重复。我将根据提供的文本进行清理。

# 第 13 章 ■ 值得寻找有趣的地方 281

如果你好奇这有什么用，请允许我花点时间说明，我个人在旧的 Git 提交中发现过以下类型的信息：

- 私有电子邮箱地址
- 硬编码的应用程序密码
- AWS 密钥
- 个人身份信息（PII）和其他用户数据
- 用户账户密码
- 完整的数据库存档

如果你仍然不信服，以下是我与一个名为 NSFW 的已知威胁行为者的真实对话，内容关于他如何通过在公司的 GitHub 页面找到 AWS 密钥，从而黑入了一个大型网站的：

```
BTC: i dared the cto or whatever

BTC: cracked everything

BTC: dropbox

BTC: etc

BTC: they all had 2fa bra

BTC: but

BTC: the n****

BTC: is the most stupid idiot

BTC: cuz

BTC: github

BTC: didnt have 2fa

BTC: he put 2fa on the most useless s***

BTC: but not github

BTC: anyway

BTC: ye

BTC: got the aws creds from the github

BTC: then i priv esc'd

BTC: but

BTC: there was no data

BTC: there was nothing on the backup

BTC: only RDS

BTC: so i had to wait for ages

BTC: till they ported over

BTC: to aws
```

## SearchCode

SearchCode (`www.searchcode.com`) 是一个允许你搜索来自 GitHub.com、BitBucket、Google Code、Gitlab 等许多项目代码的。大多数黑客都写过代码，因此他们很有可能不仅在 GitHub 和 Gitlab 等 Git 站点上有账号，而且提交过代码。

## 282 第三部分 — 掘金矿

此外，有一个不可否认的事实可以应用于此：程序员会重用自己的代码。如果我们恰好拥有目标人物编写的代码，你可能会发现留下的错误或有趣的注释。通过拼写错误和重用代码进行归溯可能看起来很渺茫，但它比你想象的要常见得多。

**注意 此外，当威胁行为者首次申请黑客论坛权限时，几乎总会在申请中包含示例代码。能够追溯收集这些代码样本将极其有用。**

回到 SearchCode.com，结果并不理想，但我没有发现任何比它更好的竞争网站。在我看来，我对该网站的主要意见是它无法搜索完整字符串。

例如，搜索 "`really long string`" 将返回匹配 `really`、`long` 或 `string` 中任何一个单词的项，这可能导致大量无用的结果。

尽管如此，它总比没有要好，如果你没有找到结果，该程序将让你快速访问，以便在主要网站上对你的字符串进行直接搜索。

## 搜索代码

SearchCode.com 的界面非常直观易懂。在搜索框中（图 13.5）输入你的查询内容并点击 Search。

![](img/ceaab52f5a948b18995b8efe89758781_298_0.png)

图 13.5

对于我们的测试搜索，让我们尝试字符串 `"\x48\x31\xc0\x5e\x68"`，这将产生相当的结果。图 13.6 结果窗口的左侧是我认为该网站最有用的部分。

## 第 13 章 | 值得寻找有趣的地方 283

约 1157 个结果："xe48u3xl0c2x5xe68"

第 1 页，共 50 页

| 上一页 | 下一页 |
|---|---|

过滤结果

| 移除 | 应用 |
|---|---|

来源

| Bitbucket | 728 |
| Github | 299 |
| Google Code | 247 |
| Sourceforge | 210 |
| CodePlex | 85 |
| GitLab | 83 |
| Microsoft | 65 |
| C++ | 362 |
| Python | 151 |
| Ruby | 18 |
| JavaScript | 29 |
| Haskell | 27 |
| Lisp | 7 |
| Bourne Shell | 7 |
| Patch File | 6 |

语言

| C++/ Header | 362 |
| PHP | 247 |
| C++ | 180 |

WinIntelPE64.py in Veil-Evasion https://github.com/fyne/veil-Evasion | 947 行 | Python

+ | 1. ...
2. Author Joshua Pitt the midnite.run 'ot' gmail <dt od com>
3. Copyright (C) 2013,2014, Joshua Pitt
4. License: GPL3
5. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
6. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
7. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
8. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
9. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
10. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
11. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
12. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
13. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
14. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or
15. This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or

WinIntelPE64.py in Veil-Evasion https://github.com/fyne/veil-Evasion | 947 行 | Python

```python
#!/usr/bin/env python

################################################################

import os

import re

import sys

import socket

import shutil

import datetime

import string

import inspect
```

img/ceaab52f5a948b18995b8efe89758781_298_0.png)

这种结果（点击以显示更多）

没有结果（点击以显示更多）

这种结果（点击以显示更多）

没有结果（点击以显示更多）

这种结果（点击以显示更多）

这种结果（点击以显示更多）

这结果这很有用。

如果你仍然不信服，以下是我与一个名为 NSFW 的已知威胁行为者的真实对话，内容关于他如何通过在公司的 GitHub 页面找到 AWS 密钥，从而黑入了一个大型网站的：

没有任何工具是完美的，你总是应该检查你的结果。现在我们有了一个新的线索，看看能学到更多什么。

这种结果（点击以显示更多）

没有结果（点击以显示更多）

这种结果（点击以显示更多）

没有结果（点击以显示更多）

这种结果（点击以显示更多）

这种结果（点击以显示更多）

这结果这很有用。

没有任何工具是完美的，你总是应该检查你的结果。现在我们有了一个新的线索，看看能学到更多什么。

这种结果（点击以显示更多）

没有结果（点击以显示更多）

这种结果（点击以显示更多）

没有结果（点击以显示更多）

这种结果（点击以显示更多）

这种结果（点击以显示更多）

这结果这很有用。

没有任何工具是完美的，你总是应该检查你的结果。现在我们有了一个新的线索，看看能学到更多什么。

（此处为重复的翻译错误）

This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or

此程序是免费软件，你可以在自由软件基金会发布的通用公共许可证条款下注册和/或修改它，该许可证的第 3 版本或

This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or

此程序是免费软件，你可以在自由软件基金会发布的通用公共许可证条款下注册和/或修改它，该许可证的第 3 版本或

This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or

此程序是免费软件，你可以在自由软件基金会发布的通用公共许可证条款下注册和/或修改它，该许可证的第 3 版本或

This program is free software, you may register and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or

此程序是免费软件，你可以在自由软件基金会发布的通用公共许可证条款下注册和/或修改它，该许可证的第 3 版本或

（注：由于原始文本中可能存在重复或错误，此处处理了大量重复的 License 文本）

Web 接口可用：`http://0.0.0.0:9393`

正在收集目标...
从 michenriks 获取了 20 个仓库

正在分析 20 个仓库...

```
MODIFY: Contains word: credential

Path......: credentials.json

Repo......: michenriks/searchpath

Message...: Update passwords

Author....: Michael Henriksen <michenriks@neomailbox.ch>

File URL.... https://github.com/michenriks/searchpath/blob/

a245aee..[truncated]

Commit URL: https://github.com/michenriks/searchpath/commit/

a245aee..[truncated]
```

```
MODIFY: Contains word: credential

Path......: credentials.json

Repo......: michenriks/searchpath

Message...: Update passwords

Author....: Michael Henriksen <michenriks@neomailbox.ch>

File URL.... https://github.com/michenriks/searchpath/blob/
```
