

; 2htdp/itunes 库文档，第 1 部分：

; LTracks 是以下之一：
; -- '()
; -- (cons Track LTracks)

(define-struct track
    [name artist album time track# added play# played])

; Track 是一个结构：
;   (make-track String String String N N Date N Date)
; 解释：实例按顺序记录：曲目标题、制作艺术家、所属专辑、
; 播放时间（以毫秒计）、在专辑中的位置、添加日期、
; 播放次数以及上次播放日期

(define-struct date [year month day hour minute second])
; Date 是一个结构：
;   (make-date N N N N N N N)
; 解释：实例记录六条信息：
; 日期的年份、月份（1 到 12 之间，包含 1 和 12）、
; 日期（1 到 31 之间）、小时（0 到 23 之间）、
; 分钟（0 到 59 之间）和秒（也在 0 到 59 之间）。

### 图 75：将 iTunes 曲目表示为结构（结构）

; Any Any Any Any Any Any Any Any -> Track 或 #false
; 为合法输入创建一个 Track 实例
; 否则生成 #false
(define (create-track name artist album time
                      track# added play# played)
  ...)

; Any Any Any Any Any Any Any -> Date 或 #false
; 为合法输入创建一个 Date 实例
; 否则生成 #false
(define (create-date y mo day h m s)
  ...)

; String -> LTracks
; 从文件名（iTunes 的 XML 导出）中的文本创建曲目列表表示
(define (read-itunes-as-tracks file-name)
  ...)

### 图 76：将 iTunes 曲目表示为结构（函数）

_2htdp/itunes_ 库描述的最后一个元素是一个函数，它读取 iTunes XML 库描述并提供曲目列表（LTracks）。当你从某个 iTunes 应用导出 XML 库后，可以运行以下代码片段来检索所有记录：

```
; modify the following to use your chosen name
(define ITUNES-LOCATION "itunes.xml")

; LTracks
(define itunes-tracks
  (read-itunes-as-tracks ITUNES-LOCATION))
```

将代码片段保存在与 iTunes XML 导出文件相同的文件夹中。请记住不要将 itunes-tracks 用于示例；它太大了，不适合此目的。确实，它可能非常大，以至于每次在 DrRacket 中运行 BSL 程序时读取文件都需要花费大量时间。因此，在设计函数时，你可能希望将第二行注释掉。只有在需要计算 iTunes 库相关信息时才取消注释。

**练习 199.** 虽然重要的数据定义已提供，但设计配方的第一步仍不完整。编造 Dates、Tracks 和 LTracks 的示例。这些示例在后续练习中作为输入非常有用。

**练习 200.** 设计函数 total-time，它接收一个 LTracks 元素并生成总的播放时间。程序完成后，计算你 iTunes 库的总播放时间。

**练习 201.** 设计 select-all-album-titles。该函数接收一个 LTracks 并生成一个专辑标题列表（字符串列表）。

同时设计函数 create-set。它接收一个字符串列表并构造一个包含给定列表中每个字符串且仅出现一次的列表。**提示** 如果字符串 s 位于给定列表的开头，且在列表其余部分也出现，则 create-set 不保留 s。

最后设计 select-album-titles/unique，它接收一个 LTracks 并生成一个唯一专辑标题列表。使用此函数确定你 iTunes 库中的所有专辑标题，并找出它包含多少个不同的专辑。

**练习 202.** 设计 select-album。该函数接收一个专辑标题和一个 LTracks。它从后者中提取属于给定专辑的曲目列表。

**练习 203.** 设计 `select-album-date`。该函数接收一个专辑标题、一个日期和一个 LTracks。它从后者中提取属于给定专辑且在给定日期后播放过的曲目列表。**提示** 你必须设计一个函数，它接收两个 Date 并判断第一个是否在第二个之前发生。

**练习 204.** 设计 `select-albums`。该函数接收一个 LTracks 元素。它生成一个 LTracks 列表，每个专辑一个。每个专辑由其标题唯一标识，在结果中仅出现一次。**提示** (1) 你希望使用前面练习的一些解决方案。(2) 该分组函数接收两个列表：专辑标题列表和曲目列表；它将后者视为原子，直到将其交给辅助函数。参见练习 196。

**术语** 名称以 `select-` 开头的函数被称为 _数据库查询_。有关更多详细信息，请参见第 23.7 章。**结束**

图 77 显示了 _2htdp/itunes_ 库如何使用列表表示曲目。LLists 是曲目表示的列表，每个表示都是一个配对字符串与四种值的列表列表。函数 `read-itunes-as-lists` 读取 iTunes XML 库并生成一个 LLists 元素。因此，如果你将以下定义添加到程序中，就可以访问所有曲目信息：

```
; modify the following to use your chosen name
(define ITUNES-LOCATION "itunes.xml")

; LLists
(define list-tracks
 (read-itunes-as-lists ITUNES-LOCATION))
```

### 图 77：将 iTunes 曲目表示为列表

然后将其保存在存储 iTunes 库的同一文件夹中。

**练习 205.** 开发 LAssoc 和 LLists 的示例，即曲目的列表表示和此类曲目列表的列表。

**练习 206.** 设计函数 find-association。它接收三个参数：一个名为 key 的字符串、一个 LAssoc 和一个名为 default 的 Any 元素。它生成第一个第一项等于 key 的 Association，如果没有这样的 Association，则生成 default。

**注意** 设计此函数后，再阅读有关 assoc 的内容。

**练习 207.** 设计 total-time/list，它接收一个 LLists 并生成总的播放时间。**提示** 首先解决练习 206。

完成设计后，计算你 iTunes 库的总播放时间。将此结果与练习 200 中 total-time 函数计算的时间进行比较。为什么会有差异？

**练习 208.** 设计 boolean-attributes。该函数接收一个 LLists 并生成与布尔属性关联的字符串。**提示** 使用练习 201 中的 create-set。

完成后，确定你的 iTunes 库为其曲目使用了多少个布尔值属性。它们合理吗？

**注意** 基于列表的表示比基于结构的表示稍逊一筹。在这种语境下，偶尔会使用“半结构化”一词。此类列表表示容纳那些很少出现且因此不适合结构类型的属性。人们经常使用此类表示来探索未知信息，并在格式众所周知后再引入结构。设计函数 track-as-struct，在可能时将 LAssoc 转换为 Track。**结束**

## 12.3 文字游戏，组合示例

你们中的一些人会在报纸和杂志上解决文字谜题。试试这个：

**示例问题** 给定一个单词，找出所有由相同字母组成的单词。例如，“cat”也可以拼成“act”。

让我们通过一个示例进行讲解。假设给定“dear”。这四个字母有二十四种可能的排列：

| ader | aedr | aerd | adre | arde | ared |
| --- | --- | --- | --- | --- | --- |
| daer | eadr | eard | dare | rade | raed |
| dear | edar | erad | drae | rdae | read |
| dera | edra | erda | drea | rdea | reda |

在这个列表中，有三个合法单词：“read”、“dear”和“dare”。

**注意** 如果一个单词包含两次相同的字母，那么所有重新排列的集合中可能包含多个相同字符串的副本。就我们的目的而言，这是可以接受的。对于实际程序，你可能希望通过使用集合而不是列表来避免重复条目。参见第 9.6 章。**结束**

系统地枚举所有可能的排列显然是一个程序的任务，在英语词典中搜索也是如此。本节介绍搜索函数的设计，将另一个问题的解决留给下一节。通过分离这两个问题，第一部分可以专注于系统程序设计的高层次概念。

有关处理真实词典的内容，请参见第 12.1 章。

让我们想象一下如何手动解决这个问题。如果你有足够的时间，你可能会枚举给定单词中所有字母的所有可能排列，然后只挑选出那些在词典中也出现的变体。显然，程序也可以以这种方式进行，这暗示了一种通过组合进行的自然设计，但，一如既往，我们将系统地进行，并首先为我们的输入和输出选择数据表示。

乍一看，将单词表示为 Strings 并将结果表示为单词列表或 List-of-strings 是自然的。基于这一选择，我们可以制定
