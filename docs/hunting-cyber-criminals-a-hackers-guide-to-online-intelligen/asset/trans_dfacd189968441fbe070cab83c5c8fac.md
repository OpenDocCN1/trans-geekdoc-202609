

# 412 第四部分 ■ 狩猎人类

此外，由于该账户的用户名是 m4l1h4ck3r，这同样适用于任何具有该用户名的账户。

![](img/ceaab52f5a948b18995b8efe89758781_424_0.png)

图 18.4

看来我们的朋友在 000WebHost.com 上有很多账户。图 18.4 显示了另一个具有相同密码的账户，但电子邮件和用户名不同。这可能是另一个完全不同的人。然而，考虑到验证邮件的地址中出现了 "Luka" 这个词，结合密码相同的这一事实，有很大可能是可能是同一个人。

图 18.5 为这个人提供了最后的棺棺之击——再次，又是另一个在 000WebHost.com 上开通的账户，且使用了相同的密码。这次我们实际上可以看到他的全名，以及我们已经知道的那个 kunt.lx@gmail.com 邮箱地址。

![](img/ceaab52f5a948b18995b8efe89758781_424_1.png)

图 18.5

此时，这只是处理收尾工作并尽可能收集信息的问题。我们可以利用姓名、IP、邮箱地址和密码来搜索更多账户，这将开始揭开他所有的在线轨迹。

# 一个重要的错误弯路

我之前提到过几次，但还是想再说一次以防万一：据我所知，示例中使用的 F3tywap 与 The Dark Overlord (TDO) 没有任何关系。

# 第 18 章 密码、转储与 Data Viper 413

记住，经验丰富的威胁者会重用属于其他活跃威胁者的别名。这对于 Crook（又名 Ping）来说并不是 uncommon move。

对我来说，这是一个重要的教训——我希望这也能引起你的共鸣。仅仅因为我们找到了这组 F3tywap 的所有者，并不意味着他与 TDO 关联的同一个 F3tywap。重要的区别在于，这些账户（以任何方式）都没有关联到 Siphon 暗网上的 F3tywap（他和 Arnie 都在那里广告出售 TDO 被盗的医疗数据）。

我们将在本章晚些时候介绍更多使用重用密码来识别目标的示例。首先，让我们后退一步，看看这些数据是如何收集的。

# 获取你的数据

泄露的数据集和密码转储随处可见。你可以在 RaidForms.com 等论坛上使用“credits”下载它们，或者你可以从 Adobe、LinkedIn、Mattel 和 Ashley Madison 等大型网站下载数千个转储。如果你想开始，databases.com 和 RaidForms.com 可能会让你达到 50% 的进度。

假设从 databases.com 和 RaidForms.com 开始，那里随处充斥着“collections”。你也可以从 pastebin 等网站收集数十亿条用户名/密码组合。

> 注意：Data Viper 的数据策划花费了 18 个月，在我看来，它比任何平台的数据质量都要。这是一个 bold claim，尤其是当你听到“我们有更好的数据”时。这是一个 hard statement，但在去重文件后，我开发了这个工具以实现一个非常特定的目标。我非常自豪，因为这种努力是值得的，因为它能够识别 TDO 成员的目标。

# 数据质量与 Collections 1–5

有时在 2019 年初，大规模收集引起了媒体的关注。“Collection 1”包含了超过数十亿条。

# 414 第四部分 — 狩猎人类

在其他情况下，从各种泄露中收集用户名/密码组合，数据是冗余的。Troy（Pwned）写了一篇关于数据的长文。Troy 和我们都在处理数据，以看到 Collection 4 和 5。每个文件夹大约有 10 到 20 个记录。通过 Linux 命令，我们最终从两个 collections 中得到了一个唯一的文件。

# Collection 4:

- 原始大小约为 300 GB。
- 经过去重并合并后，得到了 60 GB。

# Collection 5:

- 原始大小约为 220 GB。
- 经过排序和去重，最终大小为 72 GB。
- 包含了 2.1 亿条条目。
- 合并这些数据集，删除了另外 30% 的条目。

# 第 18 章 密码、转储与 Data Viper

# 始终手动数据

乍看之下，这似乎是一个不错的结果；2.1 亿条用户名/密码组合将是一个极大的补充。不幸的是，我们必须花点时间验证数据。当我们这样做时，我们很快发现这些数据是垃圾。最后的文件包含了几百条条目。列出了地址和密码：

```
ddd54000@hotmail.fr", "54000"
ddd54008@hotmail.fr", "cat6564"
ddd54008@hotmail.fr", "cat6564"
ddd54008@hotmail.fr", "Cat65540"
ddd54008@hotmail.fr, "ddd-54000"
ddd54008@hotmail.fr, "ddd54000"
ddd54008@hotmail.fr, "revoltec"
ddd54008@hotmail.ru, "cat65450"
ddd54008@rambler.ru, "cat65450"
ddd54009@yandex.ru, "cat65450"
ddd54001@mail.ru, "cat65450"
ddd54002@mail.ru, "cat65450"
ddd54009@mail.ru, "cat65450"
ddd54000@mail.ru, "qwerty"
ddd54001@mail.ru, "letrewq"
ddd54001@mail.ru, "5403123"
ddd54001@mail.ru, "qwerty"
ddd54001@mail.ru, "qwerty"
ddd54001@mail.ru, "qwerty1123"
ddd54002@mail.ru, "letrewq"
ddd54002@mail.ru, "5403123"
ddd54002@mail.ru, "qwerty"
ddd54002@mail.ru, "qwerty"
ddd54002@mail.ru, "qwerty10"
ddd54003@mail.ru, "letrewq"
ddd54003@mail.ru, "5403123"
ddd54003@mail.ru, "qwerty"
ddd54003@mail.ru, "qwerty"
ddd54003@mail.ru, "Qwerty"
ddd54003@mail.ru, "qwerty10"
```

```
ddd54003@mail.ru, "qwerty1123"
ddd540422@yahoo.com, "n88599"
ddd54048@mail.ru, "letrewq"
ddd54048@mail.ru, "5403123"
ddd54049@mail.ru, "qwerty"
ddd54049@mail.ru, "qwerty10"
ddd54049@mail.ru, "qwerty1123"
ddd5405b@bk.ru, "qwerty"
ddd5405b@inbox.ru, "qwerty"
ddd54055@mail.ru, "letrewq"
ddd54055@mail.ru, "5403123"
ddd54055@mail.ru, "qwerty"
ddd54055@mail.ru, "qwerty10"
```
