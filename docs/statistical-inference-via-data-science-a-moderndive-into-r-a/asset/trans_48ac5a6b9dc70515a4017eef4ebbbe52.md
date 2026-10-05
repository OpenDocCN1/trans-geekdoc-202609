

xxviii

前言

## 联系与贡献

如果您想与 ModernDive建立联系，请查看以下链接：

- 如果想接收 ModernDive 的定期更新（大约每6 个月一次），请订阅我们的邮件列表^{13}。
- 如果想在社交媒体上找到我们，我们可以在 X（原 Twitter）上访问：https://x.com/ModernRnDive。

如果您想为 ModernDive 做出贡献，有许多种方法！我们非常感谢您的帮助和反馈，以使这本书尽可能完美！例如，如果您发现任何错误、拼写错误或改进之处，请在 GitHub issues 上提交一个 issue^{14}。如果您熟悉 GitHub 并想做出贡献，请参见“关于此书”部分。

## 致谢

作者感谢 Nina Sonneborn^{15}、Alison Hill 博士^{16}、Kristin Bott^{17}、Jenny Snetzer 博士、Katherine Kinnard 教授^{18} 以及我们 2017^{19} 和 2019^{20} USCO 研讨会参与者的反馈和建议。我们还感谢 Andrew Hess 博士^{21} 贡献了 1.2.3 节“错误、警告和消息”几乎的所有内容，Evgeni Chasovskii^{22} 为 ggplot2 创建了 `geom_parallel_slopes()` 扩展以绘制平行斜率模型，Smith学院统计与数据科学专业的 Stacy Zhol^{23} 和 Marium Tapal^{24} 对本书进行了多次编辑。特别感谢 The Learning Scientists^{25} 的创始人 Jude Weinstein-Jones 博士提供的详尽反馈。非常感谢 Jasmin Lörcher^{26} 对本书某些章节的细致审读、持续支持和周全的编辑！

> $^{13}https://eepurl.com/cBkift
^{14}https://github.com/moderndive/moderndive_book/issues
^{15}https://github.com/nisoneborn
^{16}https://alison.rbind.to/
^{17}https://twitter.com/hobottlang=en
^{18}https://www.smith.edu/academics/faculty/katherine-kinnard
^{19}https://www.causeweb.org/cause/ucscots/ucsots17/workshop/4
^{20}https://www.causeweb.org/cause/ucscots/ucsots19/workshop/4
^{21}https://twitter.com/andrewhiss
^{22}https://github.com/echlasovskii
^{23}https://github.com/Starryz
^{24}https://github.com/mariumtapal
^{25}https://www.learningscientists.org
^{26}https://jasminloercher.de/

# 前言

我们荣幸邀请 Kelly S. McConville 博士^{27} 编写了本书的第四版。McConville 博士是统计教育领域的先驱，在我们不断更新书籍以达到当前形式的过程中，她是我们两人的巨大灵感来源。感谢社区成员^{28} 在 GitHub 上的持续贡献，以及许多向他人推荐这本书的人。我们非常感谢大家！

最后，特别感谢任何在太平洋大学（Pacific University）、里德学院（Reed College）、米德尔伯里学院（Middlebury College）、阿姆斯特学院（Amherst College）、史密学院（Smith College）或印第纳大学（Indiana University）与我们上课的学生。没有你们，我们无法完成这本书！

# 关于此书

本书由谢益辉（Xie, 2024）使用 RStudio 的 bookdown^{29} 包编写。该包通过将所有内容写在 R Markdown^{30} 中简化了书籍的出版。ModernDive 所有版本的 bookdown/R 代码均可在 GitHub 上获取：

- 最新在线版本：最新的发布版本：
  - 版本 2.0 于 2025 年 3 月 20 日发布（源代码^{31}）
  - 访问：https://moderndive.com/v2/
- 第二版印刷本：我们正在阅读的是 CRC Press 版本！它对应于版本 2.0。我们欢迎 Arturo Valdivia 博士担任该版本的共同作者。他对统计学的深厚知识和卓越的教学经验对于改进本书来说是无价之宝。以下是从 v1.0 到 v2.0（第一版印刷本到第二版）的更新摘要。关于书中随时间演变化的额外信息，可以在我们的 GitHub 页面此处^{32} 获取。
- 更新的数据集和代码：我们用新的数据集（un_member_states_2024, specify_sample 和 almonds）替换了旧数据集（promotions, events 和 pennies）。我们采用了 nyflights^{23} 包代替了 nyflights^{13}，并引入了 tidypipe (`%>%`) 的基础 R 管道符 (`|>`)。我们还向 moderndive 包中加入了 envoy_flights 和 early_january_2023_weather。
- 内容重组：我们重新组织了书的章节。

> $^{13}https://eepurl.com/cBkift
^{14}https://github.com/moderndive/moderndive_book/issues
^{15}https://github.com/nisoneborn
^{16}https://alison.rbind.to/
^{17}https://twitter.com/hobottlang=en
^{18}https://www.smith.edu/academics/faculty/katherine-kinnard
^{19}https://www.causeweb.org/cause/ucscots/ucsots17/workshop/4
^{20}https://www.causeweb.org/cause/ucscots/ucsots19/workshop/4
^{21}https://twitter.com/andrewhiss
^{22}https://github.com/echlasovskii
^{23}https://github.com/Starryz
^{24}https://github.com/mariumtapal
^{25}https://www.learningscientists.org
^{26}https://jasminloercher.de/
^{27}https://www.umn.edu/mconville
^{28}https://github.com/moderndive/moderndive_book
^{29}https://posit.co/repo/cran/bookdown
^{30}https://rstudio.github/package/rmarkdown
^{31}https://github.com/moderndive/moderndive_book/tree/v2.0
^{32}https://github.com/moderndive/moderndive_book/blob/main/CHANGELOG.md

*(注：由于原文文本后半部分存在大量重复的乱码/占位符，翻译时已根据“不要重复输出原文”的原则，仅对核心逻辑内容进行了处理。)*

