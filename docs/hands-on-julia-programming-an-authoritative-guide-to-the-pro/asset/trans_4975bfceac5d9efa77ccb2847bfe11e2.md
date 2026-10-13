

# PDFIO API

## 函数：`getPDFText`

**参数：**
- `src` - 要从中提取文本的输入 PDF 文件路径
- `out` - 将写入输出的输出 TXT 文件路径

**返回：** 包含文档元数据的字典

```julia
function getPDFText(src, out)
    doc = pdDocOpen(src)
    docinfo = pdDocGetInfo(doc)
    open(out, "w") do io
        npage = pdDocGetPageCount(doc)
        for i = 1:npage
            page = pdDocGetPage(doc, i)
            pdPageExtractText(io, page)
        end
    end
    pdDocClose(doc)
    return docinfo
end
```

**示例：**
```julia
julia> getPDFText("sample-google-doc.pdf", "sample-google-doc.txt")
Dict{String,Union{CDDate, String, CosObject}} with 1 entry:
  "Producer" => "Skia/PDF m79"
```

该 API 也可用于密码保护的 PDF 文件。它还可用于验证 PDF 文档中的数字签名。

# Microsoft Office 文档

Microsoft Office 文档是常见的文档形式。虽然文档格式是一个名为 **Office Open XML** (**OOXML**) 的开放标准[^9]，最初由 Microsoft 支持，但庞大的规范给文档消费者直接在其应用程序中使用它们带来了重大挑战。基于 *Apache Tika*、*Apache POI* 和 *Apache FOP* 编写的 Taro[^10] 提供了基于 JavaCall 的与 Julia 的集成。同一系统还支持 PDF 文件的读取和写入。界面相当简单，具有以下功能：

- 从 Word 文档中提取文本
- 访问 Excel 文档的表格数据
- 使用 XSL-FO 生成 PDF 报告

```julia
julia> docxfile = joinpath(pathof(Taro), "..", "..", "test", "WhyJulia.docx");
julia> meta, text = Taro.extract(docxfile);
julia> meta["meta:author"]
"Avik Sengupta"
julia> text[1:54]
"Why we created Julia\n\nIn short, because we are greedy."
```

让我们从测试目录访问一个 Excel 文件。

```julia
julia> xlsxfile = joinpath(pathof(Taro), "..", "..", "test", "df-test.xlsx");
julia> df = DataFrame(Taro.readxl(xlsxfile, "Sheet1", "B2:F8"))
6×5 DataFrame
│ Row │ H1     │ H2     │ H3     │ H4     │ H5   │
│     │ Any    │ Any    │ Any    │ Any    │ Any  │
├─────┼────────┼────────┼────────┼────────┼──────┤
│ 1   │ a      │ 1.0    │ 1.0    │ 1.0    │ a a  │
│ 2   │ b      │ 2.0    │ 2.0    │ 1.0    │ b b  │
│ 3   │ c      │ missing│ 3.0    │ 0.0    │ c c  │
│ 4   │ d      │ 4.0    │ missing│ missing│ d d  │
│ 5   │ e      │ 5.0    │ 5.0    │ 1.0    │ e e  │
│ 6   │ missing│ 6.0    │ 6.0    │ 1.0    │      │
```

我们将在后面的章节讨论 `DataFrames`[^11]。就我们的理解而言，它们有助于轻松访问表格数据。由于 MS Excel 用于表格数据，因此已经开发了许多用于此目的的包。其中之一是 `XLSX.jl`[^12]。该包用纯 Julia 编写，不需要配置 Java 的开销。`XLSX.jl` 是使用 ECMA-376 标准编写的。这也使其能够灵活地使用类似 WorkSheet、Cell IDs 等文件结构来访问 MS Excel 文件。

```julia
julia> using XLSX
julia> xlsx = XLSX.readxlsx("df-test.xlsx")
XLSXFile("df-test.xlsx") containing 1 Worksheet
  sheetname size    range
-------------------------------------------------
      Sheet1 9x5     B2:F10
julia> sheet = xlsx["Sheet1"]
9×5 XLSX.Worksheet: ["Sheet1"](B2:F10)
```

可以使用 Excel 单元格 ID 范围访问数据中的单元格。结果将是一个矩阵。

```julia
julia> sheet["B2"]
"H1"
julia> sheet["C4:E9"]
6×3 Matrix{Any}:
 2        2        1.0
 missing  3        0.0
 4        missing  missing
 5        5        1.0
 6        6        1.0
 7        7        1.0
```

可以使用 `XLSX.jl` 接口获得 `DataFrame`，如下所示：

```julia
julia> DataFrame(XLSX.readtable("df-test.xlsx", "Sheet1")…)
8 rows × 5 columns
 H1 H2 H3 H4 H5
 Any Any Any Any Any
 1 a 1 1 1.0 a a
 2 b 2 2 1.0 b b
 3 c missing 3 0.0 c c
 4 d 4 missing missing d d
 5 e 5 5 1.0 e e
 6 missing 6 6 1.0
 7 g 7 7 1.0 g g
 8 h 8 8 1.0 h h
```

# 图像数据

光栅图像存储为数字数组。这些数字排列为矩阵。它们可以表示为分离通道或交织通道，如图 15.1 所示。

**图 15.1：** 作为数字矩阵的图像 (a) H 和 W 为图像的高度和宽度，C 为通道数。例如，RGBA 图像将有 4 个通道。(b) 同一图像处于交织模式，像素分量水平依次放置。因此得到一个 2-D 矩阵而不是 3-D 数组。

虽然内存似乎按 2 维或 3 维排列，但实际并非如此。这意味着在图像中所有红色分量在一起，随后是绿色强度值，依此类推。图像文件格式不一定以这种方式存储数据。它们应用多种变换并压缩数据，将其作为数字二进制流存储。然而，几乎所有图像应用在消费或渲染图像前，都会将数据转换为上述排列之一。在 FileIO 部分，我们加载了一个 tiff 文件，创建的图像对象类型为 `Array{ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}},2}`。如果我们暂且不考虑复杂的类型，它只是一个 2 维数组。由于灰度图像只有一个分量，因此分量类型的第三个维度不相关。类型 `ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}}` 本身就相当复杂。传统上，图像分量被归一化为 0.0 到 1.0 的浮点值。由于浮点数需要更大的存储空间，可以用一个字节的数据表示，其中 0 映射到 0.0，255 映射到 1.0；因此是数字的定点表示。在一个字节的数据中，甚至所有 8 位可能不都被一个值消耗。可能只使用 4 位。因此，一个字节可用于存储两个像素强度。`ImageCore`[^13] 包有许多此类图像表示，建议读者参考以了解各种图像格式。您也可以使用 JuliaImages[^14] 进行图像处理。OpenCV 库提供了一个教程[^15]，用于与 Julia 前端集成。

# 表格数据

表格数据在许多数据应用中非常常见。RDBMS 的使用充当了表格数据的广泛来源。此外，我们看到像 R 和 Python Pandas 这样的语言将表格数据作为其维护记录的基础。我们已经看到了带有 CSV 等分隔文件的表格数据源。我们之前也使用 Taro 将 Excel 文件作为 `DataFrame` 加载。Julia 创建了一个名为 `Tables.jl`[^16] 的抽象接口，可用于访问表格数据。

**图 15.2：** (a) 表格数据就像不同类型的向量，可以通过行和列访问器访问 (b) 复合类型的向量，每个属性并排存储。

`Tables.jl` 接口提供了更简单的界面来访问列并抽象行，以便轻松访问数据。

```julia
julia> using Tables
julia> rows = Tables.rows(df)
6×5 DataFrameRows
  H1   H2   H3   H4   H5
  Any  Any  Any  Any  Any
1 a    1.0  1.0  1.0  a a
2 b    2.0  2.0  1.0  b b
3 c    missing 3.0  0.0  c c
4 d    4.0  missing missing d d
5 e    5.0  5.0  1.0  e e
6 missing 6.0  6.0  1.0
```

创建了一种新的 `DataFrameRows` 类型，本质上是原始 `DataFrame` 的一个视图。您可以访问表的列名。您也可以使用列名索引表。

```julia
julia> Tables.columnnames(df)
5-element Array{Symbol,1}:
 :H1
 :H2
 :H3
 :H4
 :H5

julia> cols = Tables.columns(df);
julia> cols[:H1]
6-element Array{Any,1}:
 "a"
 "b"
 "c"
 "d"
 "e"
 missing
```

虽然 Matrix 不是表，但可以使用 `DataFrames` 将它们转换为表。

```julia
julia> rows = Tables.rows(DataFrame([1 2 3; 4 5 6; 7 8 9]))
3×3 DataFrameRows
x1 x2 x3
Int64 Int64 Int64
1 1 2 3
2 4 5 6
3 7 8 9
```

可以使用 `Tables.schema` 方法查找模式信息。

```julia
julia> Tables.schema(df)
Tables.Schema:
:H1  Any
:H2  Any
:H3  Any
:H4  Any
:H5  Any
```

此外，您可以使用 `TableOperations` 包对表格数据进行 `select`、`map` 和 `filter` 等操作。Julia 还提供了一个名为 `JuliaDB`[^17] 的高性能数据库。建议读者将了解其功能作为练习的一部分。

# 数据可视化

视觉反馈是人们从数据中获得的最直观的洞察。虽然在可视化表示数据方面存在维度限制，但绘图迄今为止是用于数据可视化最常用的方法之一。

```julia
julia> using Plots
julia> x = 1:10; y = rand(10); z = rand(10);
julia> plot(x, [y, z])
```

您将看到如下内容渲染在新窗口中（REPL 的情况）或 Jupyter 屏幕上（图 15.3）。

**图 15.3：** 多系列数据的绘图。

然而，向 plot 函数传递 3 个参数（如 `plot(x, y, z)`）可以绘制数据的 3-D 图（图 15.4）。

**图 15.4：** 一个 3-D 图。

`Plots`[^18] 是一个抽象绘图聚合库，它利用 `GR`、`pyplot`、`Plotly` 等其他包来渲染图表。这些也被称为 `backends`（后端）。GR 是用于绘图的最快库之一，在大多数 Julia 安装中作为默认值使用，而 `pyplot (matplotlib)` 是功能最丰富的后端。Plots 将函数转换为相关后端并显示结果。建议读者阅读 Plots 文档和教程以获得更好的理解和使用场景。

# 总结

我们浅略地介绍了 Julia 中可用的各种数据表示和转换工具，为您提供一个概览以便探索。不幸的是，列表详尽且广泛。我们可能无法对所有这些类别的工具提供详细视图。我们假设您将利用这个机会深入研究这些包，并致力于解决一些实际用例。

# 练习

1.  假设您想使用 `FileIO` 接口读取并从 PDF 文件中提取文本内容。您将如何实现此功能？您可以在实现中使用 PDFIO 提取文本内容。
2.  使用 Taro 编辑 Microsoft Excel 文件。
3.  使用 `matplotlib` 渲染示例，而不是 `GR`。
4.  JuliaDB 提供持久数据集。在您的应用程序中使用 JuliaDB 来持久化应用程序所需的数据。
5.  为您拥有的 Julia 安装设置 OpenCV 绑定。
6.  使用 `XLSX.jl` 从 Microsoft Excel 文件读取表格数据并在您的应用程序中使用该数据。

---

[^1]: ImageMagick、MeshIO、Netpbm 等支持的文件类型。 <https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md>
[^2]: 当前 FileIO 注册表中支持的文件类型。它们也可以通过代码动态更新。 <https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md>
[^3]: LightXML，基于 libxml2 的轻量级 Julia XML 包， <https://github.com/JuliaIO/LightXML.jl>
[^4]: EzXML，灵长类动物的 XML/HTML 处理工具， <https://github.com/JuliaIO/EzXML.jl>
[^5]: LibExpat，Expat XML 解析器库的 Julia 接口， <https://github.com/JuliaIO/LibExpat.jl>
[^6]: Gumbo，围绕 Google 的 gumbo C 库的 Julia 包装器，用于解析 HTML， <https://github.com/JuliaWeb/Gumbo.jl>
[^7]: AbstractTrees.jl，树状数据结构的抽象树接口， <https://juliacollections.github.io/AbstractTrees.jl/stable/>
[^8]: PDFIO，原生 Julia 的 PDF 阅读器库， <https://github.com/sambitdash/PDFIO.jl>
[^9]: ECMA-376，也发布为 ISO/IEC 29500， <https://www.ecma-international.org/publications-and-standards/standards/ecma-376/>
[^10]: Taro.jl，在 Julia 中处理 Excel、Word 和 PDF 文件， <https://aviks.github.io/Taro.jl/>
[^11]: `DataFrames.jl`，Julia 中的内存表格数据， <https://github.com/JuliaData/DataFrames.jl>
[^12]: `XLSX.jl`，Julia 语言的 Excel 文件读写器， <https://github.com/felipenoris/XLSX.jl>
[^13]: ImageCore.jl，表示图像的 Julia 类型， <https://github.com/JuliaImages/ImageCore.jl>
[^14]: JuliaImaging，Julia 的图像处理和机器视觉， <https://juliaimages.org/stable/>
[^15]: Julia OpenCV 绑定简介， <https://docs.opencv.org/4.5.1/d8/da4/tutorial_julia.html>
[^16]: Tables，Julia 中表格的接口， <https://github.com/JuliaData/Tables.jl>
[^17]: `JuliaDB`，纯 Julia 并行分析数据库， <https://juliadb.org/>
[^18]: Plots，强大的 Julia 可视化和数据分析便利工具， <https://github.com/JuliaPlots/Plots.jl>

# 第 16 章：自然语言处理

在上一章中，我们学习了获取数据的技术。我们将尝试为 **自然语言处理** (`NLP`) 任务进行有意义的信息提取。虽然 NLP 是一个不断增长且活跃研究的领域，但本章将介绍 Julia 中可用的一些工具，以满足您的文本分析需求。

## 涵盖主题

- 文本处理管道
- 预处理
    - 分词
    - 词表示
    - 嵌入
- 语义分析
- 分类器
- 抽取式摘要
    - 评估指标
- 命名实体识别
- ULMFiT

## 学习目标

读者将能够理解各种文档语料库模型，理解文本分词、向量表示、语义分析技术的使用、命名实体识别、一些标准文本分类模型如 `ULMFit`。

## 文本处理管道

文本分析领域的研究发展如此迅速，以至于几年前仍然相关的许多概念正在不断地通过更新的概念和知识得到增强。神经计算已显著渗透到大多数文本处理任务中。相关的传统统计方法正与深度学习技术一起被实验。我们将讨论几个常用的文本分析包，并建议读者在拓展视野的过程中探索和学习更新的技术。此处描述的代码或文本是为了便于学习和理解，比较简单。不应将其视为生产性能的参考。

**图 16.1：** 典型的文本处理管道。

大多数文本处理任务可以被视为图 16.1 所示的活动简化管道。然而，这相对于您的实际用例是一种过度简化，可能存在某些重叠的任务。我们将管道组件描述如下：

- **获取**：我们在此讨论的文本获取是指从网络抓取、从磁盘读取 MS Word 或 PDF 等各种格式的文件、社交媒体源等获得的非结构化文本。虽然我们在上一章讨论了部分任务，但挑战在于创建文档的粒度级别。例如，文档可以短至一条 Twitter 动态，也可以大至一整本书。这种区分需要从您试图解决的问题中理解。
- **分词**：文本块需要被分词为构建块，以便进行有意义的解释。例如，文档可以包含多个段落，每个段落可能包含句子，句子可以由单词组成。而单词以特定方式排列将形成有意义的文档。不仅是单词，甚至某些子词也可能有含义；例如 *unforgettable* 作为一个单词与 *forget* 有有意义的关联。尽管读者从未见过这个单词，但他会将其分析为 *un-forget-able* 这样的子词，并能推导出有意义的关联。
- **表示**：最终，计算机中的所有内容都需要表示为数字或符号的集合，以便进行后续分析。通过分词创建的标记需要表示为数字数组，该数组考虑标记的上下文及其相互关系。它们应具有所代表语言的某些固有属性。虽然最初是作为词矩阵或独热向量开始的，但它们被表示为较大维度的稠密向量（300 维很典型），甚至如 GPT-2 那样具有极大参数量的语言模型。
- **模型**：这些不是上一节的语言模型，而是我们想要解决的实际任务。假设我们有单词的合理语言模型表示，比如词向量，我们想用它们来找出特定句子可能代表的情感。如果问题是情感分析，模型将把词向量作为输入并完成分类任务。这个分类任务可以是逻辑回归、神经网络或条件随机场等。同样，构建文本摘要任务的人可能会利用文本生成神经模型。

如果您仔细观察，前三个任务是无监督或半监督的，目的是更好地理解语言。为什么？例如，在训练词向量时，会根据周围的单词估计一个单词的概率。在某些任务中，从句子中随机删除单词，以便语言模型正确猜测这些单词。此外，训练是在包含数万亿单词的大型语料库上进行的，这些语料库来自网络抓取或维基百科内容等，且不对单词进行标记。因此，关于单词及其与其他单词关联的信息被捕获为数学向量表示的一部分。由于训练表示可能耗时且资源密集，可能由利用云端专用资源进行数月训练的研究团队完成。

让我们看看这句话："Can you pass me the can?" 这里的同形异义词 *can* 代表两种不同的含义。因此，单词仅仅存在于句子中是不够的，除非周围的上下文也被捕获。同音词会使情况变得更糟。由于 NLP 中文本和语音相关技术很多时候是相似的，将标记表示为中间形式绝对增加了显著的好处。经典句子："Tell me a tale about a tail" 将为发音相似的语音标记生成实质上不同的特征。越来越多的研究集中在从语言模型中获取表示，并将其作为任务模型的输入。

Julia 包生态系统为所有四个管道任务[^1]提供了解决方案。一个贯穿管道的包是 `TextAnalysis`[^2]。我们将详细讨论它。还有其他包我们也会涉及。不过，可以使用像 `Flux` 这样的建模工具来实际开发特定任务的模型。我们将在下一章详细讨论 Flux。

## 预处理

我们可以宽泛地将管道中的前三步称为预处理。`TextAnalysis` 包和 JuliaText GitHub 组织维护的几个相关包提供了此类功能。Julia 中的文档可以是各种类型。`TextAnalysis` 提供以下文档类型：

- **StringDocument**：文档被视为 Julia 字符串。
- **FileDocument**：文档作为文件驻留在操作系统的文件系统上。
- **NGramDocument**：文档被视为单词或词对或三元组的袋或集合，取决于 N。单词的顺序和上下文不保留。
- **TokenDocument**：文档作为标记序列存储。标记可以是单词，也可以是单词的衍生形式。

每种文档类型都有特定用途。例如，`NGramDocument` 不能用于单词序列重要的操作。根据定义，序列标注要求数据以正确的语言序列呈现。然而，N-gram 在垃圾邮件分类中非常有用，其中文档中单词的存在足以区分 HAM（好文档）和 SPAM。文档可以作为一组处理；也称为语料库。

通常，语料库中的文档将具有相似的属性；因此可以对语料库应用通用转换。`TextAnalysis` 有一个 `Corpus` 类型，能有效捕捉这一概念。`CorpusLoader`[^3] 包可以下载标准文本语料库并按需惰性加载。

### 分词

分词是将文档细分为有用文本块的过程。文档可以在段落、句子、单词甚至字符级别进行分词。`MultiresolutionIterator`[^4] 包提供了一个迭代器框架来访问这种级别的分词。然而，有一个 `WordTokenizer`[^5] 包提供了各种分词单词和句子的方法。每种分词方案都有特定的局限性，需要审慎使用。

```julia
using WordTokenizers
s1 = """This is a multi-line text. And the sentence splitter
may not do a great job on this. But if no line ending
is provided it works like a charm. Even keeps Dr. Smith intact."""

split_sentences(s1)
```

```
7-element Array{SubString{String},1}:
 "This is a multi-line text."
 "And the sentence splitter"
 "may not do a great job on this."
 "But if no line ending"
 "is provided it works like a charm."
 "Even keeps Dr. Smith"
 "intact."
```

没有行分隔符的相同句子：

```julia
s2 = "This is a multi-line text. And the sentence splitter " *
     "is provided it works like a charm. Even keeps Dr. Smith " *
     "intact."

split_sentences(s2)
```

```
3-element Array{SubString{String},1}:
 "This is a multi-line text."
 "And the sentence splitter is provided it works like a charm."
 "Even keeps Dr. Smith intact."
```

单词分词也类似。穷人的单词分词器表现得有些不完美。

```julia
s3 = "I won't be able to attend the meeting. This isn't possible."
set_tokenizer(poormans_tokenize);
println("Poorman: \t", tokenize(s3))
set_tokenizer(nltk_word_tokenize);
println("NLTK: \t", tokenize(s3))
```

```
Poorman:  SubString{String}["I", "wont", "be", "able", "to", "attend", "the", "meeting", "This", "isnt", "possible"]
NLTK:     ["I", "wo", "n't", "be", "able", "to", "attend", "the", "meeting.", "This", "is", "n't", "possible", "."]
```

### 词表示

虽然我们讨论了分词，但并非所有单词都相同。让我们比较句子：*Educate to add value to a person* 与 *Education is valued for a person*。两个句子含义相似，但分词后的单词 *education* 与 *educated* 是不同的。*value* 和 *valued* 也是如此。它们可能被截断为可能没有相关含义但可用于比较目的的形式。这些截断表示称为 **词干**。单词 *is*、*to*、*a* 和 *for* 存在于大多数句子中，并不给交流增加显著上下文。它们被称为 **停用词**。同样，消除大小写可以改善比较。

```julia
doc1 = StringDocument("Educate to add value to a person")
prepare!(doc1, strip_case | strip_stopwords | stem_words)
println(doc1.text)

doc2 = StringDocument("Education is valued for a person")
prepare!(doc2, strip_case | strip_stopwords | stem_words)
println(doc2.text)
```

```
---
educ add valu person
educ valu person
```

现在，两个句子更容易比较。让我们看看一个称为 `cos_similarity` 的相似度度量。在此之前，我们使用语料库来简化字符串。

```julia
using LinearAlgebra
doc1 = StringDocument("Educate to add value to a person")
doc2 = StringDocument("Education is valued for a person")
doc3 = StringDocument("Education is valuable asset for a human")
c = Corpus([doc1, doc2, doc3])
prepare!(c, strip_case | strip_stopwords | stem_words)
update_lexicon!(c)
```

这产生输出：`("educ add valu person", "educ valu person", "educ valuabl asset human")`。

现在，我们可以计算文档术语矩阵并将其转换以获得 `tf-idf` 或词频-逆文档频率。`tf-idf` 特别有用，因为它找出一个术语的频率，但惩罚所有文档中最常用的单词；因此是文档的一个有用特征。如果您使用余弦相似度矩阵[^6]，您会发现 `doc1` 和 `doc2` 比 `doc3` 更相似。`educ` 作为词干被忽略，因为它存在于所有文档中。

```julia
tfm = tf_idf(dtm(c))
cs = Matrix(tfm * tfm')
d = sqrt.(diag(cs))
cs ./ (d * d')
```

```
3×3 Array{Float64,2}:
 1.0        0.462709  0.0
 0.462709   1.0       0.0
 0.0        0.0       1.0
```

### 嵌入

虽然 `tf-idf` 是一种有用的表示，独热向量也是，但它们有特定的局限性。它们是稀疏的，且考虑文档中单词的计数。它们不考虑单词的局部上下文。例如，单词 *Apple* 可以指水果或科技公司。因此，周围的单词对于识别同形异义词的相关上下文至关重要。

文本嵌入提供稠密的固定大小的词到向量转换，考虑了单词及其与其他单词的关联或关系。因此，它们比经典 NLP 技术具有更好的上下文信息。在某种意义上，它们已成为当今事实上的代表性语言模型。`Embeddings`[^7] 包提供了各种语言中常用的嵌入。我们将在下面的示例中使用最简单、最古老的 `Word2Vec` 嵌入。

```julia
using Embeddings
const et = load_embeddings(Word2Vec)
const w2idx = Dict((w => i for (i, w) in enumerate(et.vocab)))
embedding(w) = et.embeddings[:, w2idx[w]]
res = embedding("king") - embedding("man") + embedding("woman")
cosdist = vec(sum(res .* et.embeddings, dims=1))
ids = partialsortperm(cosdist, 1:5, rev=true)
[(et.vocab[ii], cosdist[ii]) for ii in ids]
```

```
5-element Array{Tuple{String,Float32},1}:
 ("king", 0.8990531)
 ("queen", 0.80069506)
 ("monarch", 0.69625)
 ("princess", 0.6639391)
 ("prince", 0.6048718)
```

虽然，通常的假设是结果应最接近 `queen`，但可能并非如此。余弦相似度有效但不万无一失。因此，最好考虑几个最接近预期结果的单词。余弦相似度仅在由 `Word2Vec`、`GloVe` 或 `Transformers` 等技术进行的通用大型语料库无监督训练范围内有效。它们可以通过监督学习进一步针对特定任务进行微调。

## 语义分析

`TextAnalysis` 包支持的语义分析方法是 **潜在语义分析** (**LSA**) 和 **潜在狄利克雷分布** (**LDA**)。这两种技术都是降维技术，特别适用于在语料库中查找主题。这两种模型的基本假设是，在文档中独特确立主题的单词仅仅是少数。

同样，文档集合中存在的主题也只有少数。LSA 在 Julia 中的计算利用奇异值分解 (SVD) 将主题与单词相关联，而在 LDA 中则进行吉布斯采样以模拟预测结果。建议读者查阅一些关于这两个主题的权威文本，以正式理解 LSA 和 LDA 中使用的技术。

```julia
using LinearAlgebra
doc1 = StringDocument("Educate to add value to a person")
doc2 = StringDocument("Education is valued for a person")
doc3 = StringDocument("Education is valuable asset for a human")
c = Corpus([doc1, doc2, doc3])
prepare!(c, strip_case | strip_stopwords | stem_words)
update_lexicon!(c)
println((c[1].text, c[2].text, c[3].text))
lsa(c)
```

直观上可以看到第三个文档与其他两个大致不同。此外，`educ` 作为一个常见词干存在于所有文档中，不贡献于任何特定主题分类的归属。`SVD` 输出将验证结果中显示的类似发现。

```
("educ add valu person", "educ valu person", "educ valuabl asset human")
SVD{Float64,Float64,Array{Float64,2}}
U factor:
3×3 Array{Float64,2}:
 0.0  -0.931471  -0.363815
 0.0  -0.363815   0.931471
 1.0   0.0        0.0
singular values:
3-element Array{Float64,1}:
 0.47571307544817304
 0.3266291290597002
 0.16072253690428198
Vt factor:
3×7 Array{Float64,2}:
 -3.63e-17  0.57735  0.0  0.57735  4.92e-17  4.92e-17  0.57735
 -0.783248  0.0      0.0  0.0      -0.439615  -0.439615  0.0
 -0.62171   0.0      0.0  0.0       0.55384   0.55384   0.0
 # add      asset    educ human    person     valu      valuabl
```

相同的发现也将在 LDA 结果中重现。

```julia
m = DocumentTermMatrix(c)
lda(m, 2, 2000, 0.1, 0.1)
```

```
(
 [2, 1] = 0.142857
 [1, 2] = 0.25
 [1, 3] = 0.25
 [2, 3] = 0.285714
 [1, 4] = 0.25
 [2, 5] = 0.285714
 [2, 6] = 0.285714
 [1, 7] = 0.25, [0.0 0.0 1.0; 1.0 1.0 0.0])
```

当我们为 LDA 创建 2 个主题时，第三个文档与其他两个截然不同地被分类。

## 分类器

`TextAnalysis` 包实现了朴素贝叶斯分类器。朴素贝叶斯假设分类独立地取决于单词。因此，它仅与词袋或标记模型相关，对 seq2seq 任务无用。这是一个使用我们之前用过的句子的示例。

```julia
using TextAnalysis
m = NaiveBayesClassifier([:g1, :g2])
fit!(m, "Education is valued for a person", :g1)
fit!(m, "Education is valuable asset for a human", :g2)
predict(m, "Education is valued for a man")
```

```
Dict{Symbol,Float64} with 2 entries:
 :g2 => 0.278623
 :g1 => 0.721377
```

句子 "Education is valued for a man" 属于 `:g1` 而非 `:g2`。

## 抽取式摘要

虽然不完全是预处理步骤，但 Julia 中的摘要基于 `TextRank`[^8] 算法，这是从 `PageRank` 算法修改而来的。拥有最多不同单词的句子排名较高或作为领导者，其他句子链接到它们。链接的句子以一定概率从领导者处跟随。此练习作为模拟进行多个深度。被跟随次数最多的句子排名较高，并作为摘要的一部分。文本处理管道第一段的摘要可能如下所示：

```julia
s = "Research in the text analysis space has been so rapid… real life use cases and there may be certain tasks that are overlapping."
summary = *(summarize(StringDocument(s), ns=4)…)
```

```
"Neural computing has made significant inroads into most text processing tasks. The traditional statistical approaches though relevant are being experimented alongside deep learning techniques. The codes or texts described here are for the ease of learning and understanding and should not be considered for a production performance. However, it is an over simplification from your real-life use cases and there may be certain tasks that are overlapping."
```

由于句子是从段落中挑选的，它们不是生成式的。

### 评估指标

**面向回顾的替补评估** (`ROUGE`) 可用于针对人工创建的参考摘要测试指标质量。

```julia
ref = ["Text analysis research has been rapid. ",
       "Neural computing is being used alongwith statistical techniques. ",
       "Deep learning is gaining popularity as well. ",
       "Code and text provides here are for ease of learning and should not be used for production performance."]

julia> rouge_n(ref, summary, 2, avg=true)
0.3645833333333333

julia> rouge_n(ref, summary, 1, avg=true)
0.956140350877193
```

虽然就单个单词而言有很多重叠，但 2-gram 得分不如单词重叠那样重叠。

## 命名实体识别

`TextModels`[^9] 包抽象出一些建模任务，并为它们提供预定义模型。其中一个模型是 **命名实体识别** (`NER`) 标注。这类问题也称为 **端到端序列标注**[^10]。**词性标注** (`POS`) 是另一个类似的问题。虽然我们将快速浏览示例代码，但详细模型已在论文中讨论。由于名字在句子中很常见，在 NLU 任务中识别它们至关重要，以便执行后续操作，如在聊天机器人中；例如，问候某人或为她的航空旅行查找订票目的地等。

```julia
using TextModels
ner = NERTagger()
s1 = "Kumar is from Bangalore and works for Julia Computing."
println(ner(s1))
s2 = "Julia language is easy to learn."
println(ner(s2))
```

```
["PER", "O", "O", "LOC", "O", "O", "O", "ORG", "ORG", "O"]
["PER", "O", "O", "O", "O", "O", "O"]
```

虽然第一句能轻松识别人名、地点和组织，但第二句中的 Julia 被映射为人名。NER 标注中会有一些误识别，尽管通常在大多数情况下匹配得相当合理。其次，NER API 仅支持 5 类实体：人名(PER)、地点(LOC)、组织(ORG)、杂项(MISC) 和其他(O)。第三，该模型还通过 CNN 嵌入捕获子词信息（详细解释请参阅论文）。

## ULMFiT

**通用语言模型微调** (**ULMFiT**)[^11] 用于文本分类，最初用于文本分类任务。然而，学到的相同权重可被重新用于其他下游文本任务。`TextModels` 包对此有实现，可用于一些高级文本处理任务。模型使用分四步：

1.  数据加载和预处理
2.  语言模型预训练
3.  微调语言模型
4.  为下游任务微调分类器

也可以向模型添加特定目的的 dropout 作为层。我们建议读者查阅 `TextModels` 文档，以详细了解和使用 ULMFiT 模型。

## 总结

文本分析是一个广阔的探索领域，需要合适的工具以获得最佳结果。大多数 Julia 包的重点是解决手头的特定问题，而不是投资大型语言模型开发。虽然这并不难，但利用迁移学习并微调嵌入以解决领域问题对许多从业者更具吸引力。当我们浏览了一些开发该领域认知的技术后，细节留给读者持续开发和积累专业知识。

# 练习

1.  词干提取与词形还原有什么区别？使用其中一个相比另一个有什么好处？为什么词形还原比词干提取更难实现？
2.  TF-IDF 作为语言表示已使用很长时间。为什么它不用于大规模语言模型？您是否仍然看到 TF-IDF 的应用？它有哪些优势？
3.  有许多著名的嵌入可用于 NLP 任务。Word2vec 和 GLOVE 是相当流行的嵌入。然而，它们有特定的局限性。其中一些是什么？
4.  NER 标注以特定方式对单词进行分词。是否可以将分词器修改为其他方式？您能找到一个您想使用不同分词方案的用例吗？
5.  在您的实际用例中使用 ULMFit。您在这样做时面临哪些挑战？

---

[^1]: 建议读者观看视频：Ayush Kaushal, Natural Language Processing in Julia, JuliaCon 2020, <https://www.youtube.com/watch?v=hHCi8ojazqk>
[^2]: TextAnalysis，文本分析的 Julia 包， <https://github.com/JuliaText/TextAnalysis.jl>
[^3]: CorpusLoader，各种 NLP 语料库的多种加载器， <https://github.com/JuliaText/CorpusLoaders.jl>
[^4]: MultiResolutionsIterators，用于处理迭代器的迭代器的工具……， <https://github.com/oxinabox/MultiResolutionIterators.jl>
[^5]: WordTokenizers，用于自然语言处理和其他相关任务的高性能分词器， <https://github.com/JuliaText/WordTokenizers.jl>
[^6]: `cos_similarity` 方法已在 `TextAnalysis` 包的主分支中可用，但本书使用了 v0.7.2 发布版本。
[^7]: Embeddings，加载各种词嵌入的函数和数据依赖， <https://github.com/JuliaText/Embeddings.jl>
[^8]: Rada Mihalcea and Paul Tarau, 2004: TextRank: Bringing Order into Texts, Department of Computer Science University of North Texas, <https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf>
[^9]: TextModels，基于神经网络的自然语言处理模型， <https://github.com/JuliaText/TextModels.jl>
[^10]: Xuezhe Ma and Eduard Hovy, End-to-end Sequence Labeling via Bi-directional LSTM-CNNs-CRF, 2016, Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), <http://dx.doi.org/10.18653/v1/P16-1101>
[^11]: Jeremy Howard and Sebastian Ruder, Universal Language Model Fine-tuning for Text Classification, ACL 2018, <https://www.aclweb.org/anthology/P18-1031.pdf>

# 第 17 章：使用 Flux 进行深度学习

在上一章中，我们学习了 NLP 任务的包。我们在某些任务中使用了神经计算。在本章中，我们将使用神经网络原语对 Flux 进行建模。我们假设您对深度学习有基本的理解，并正在探索如何使用 Julia 进行建模。本章不旨在作为深度学习的介绍。

## 涵盖主题

- 深度学习
- 什么是 Flux？
- 模型动物园
- 神经网络类型
    - 全连接
    - CNN
    - RNN

## 学习目标

在本章中，读者将能够通过示例理解全连接、**卷积神经网络** (**CNN**) 和 **循环神经网络** (**RNN**)。示例选自 Flux 包的模型动物园样本。这将帮助用户理解建模框架，并帮助他们构建复杂模型或理解用 Flux 构建的模型。

## 深度学习

数字代理帮助我们更好或更快地完成任务；例如聊天机器人助手。学习过程提高了此类代理的效率。当代理学习时，随着时间的推移，它要么更快、要么更准确地执行相同任务。**人工神经网络** (`ANN`) 是用于解决许多分类问题的此类学习技术。

给定一组输入，我们想知道哪一组属于它。手写黑白图像的 MNIST 数据集是一个很好的例子。

**图 17.1：** 来自 MNIST 数据集[^2] 的样本图像[^1]。图像被分类为它们代表的数字。数据集包含 60,000 个训练图像和 10,000 个测试图像。图像为黑白，大小为 。手写数据来自近 500 位不同的书写者。

此处的示例是监督学习的情况，其中提供了输入和输出类。系统将使用 ANN 进行训练。它将从数据集预测值，并将与图 17.2 进行比较。

**图 17.2：** 数字 2 的输入图像作为二进制值向量进入神经网络。它与每个连接的权重 wij 相乘。所有值在进入中间层时相加。ANN 在传递到输出层之前可以有多个中间层。输出层具有与预期输出类相同数量的节点。本例中为 10 个。应用非线性激活函数将值转换为更接近 0 或 1 的二进制值。

这可以用以下数学方程解释。非线性激活函数 (σ)[^3] 可应用于每一层。

**图 17.2 方程** (参见图像)。

如上所示，神经网络主要是值的加权和。我们有兴趣找到最适合将输入 X 拟合到输出 Y 的权重值。激活函数为系统引入了所需的非线性。在输出层，激活函数 (`softmax`) 将较小的值推向零，较大的值推向 1。`softmax`、`sigmoid` 和 `tanh` 是分类任务中常用的激活函数。

系统运作以找到使损失最小化的最佳 值。使用梯度下降的反向传播是更新权重[^4] 的最常用技术。我们将不在此详述神经网络概念，但期望读者参考更权威的文本，以获得该主题所需的详尽数学处理。然而，本章的重点将是向读者介绍 `Flux`[^5] 包，它为深度学习或其他机器学习应用提供了详尽的建模原语。

## 什么是 Flux？

Flux 是一个设计用于建模机器学习问题的平台。建模能力可被认为类似于 *Tensorflow*[^6] 或 *PyTorch*。Flux 利用许多标准 Julia 能力，如宏、带有 `Zygote` 的 **自动微分** (`AD`)、带有 `CUDA` 包的 GPU 计算。它还利用 `DataLoader` 来惰性加载和批处理计算所需的数据。虽然 Flux 看起来像一个简单的包，但它有许多有趣的宏用法，可作为理解高级 Julia 编程的良好示例代码。

我们将尝试使用 Flux 解决一个线性回归问题。让我们看看以下方程组。我们采用一个线性方程，添加一点高斯噪声来模拟我们的数据集。这是数据科学中非常常见的技术，用于模拟人工数据以解决一些简单任务或展示依赖真实世界数据的概念。

```julia
x = 5 * rand(100)
y = 3 * x .+ 4 .+ randn(100);
```

**图 17.3：** x 和 y 的绘图。y1 表示原始数据的散点图。y2 是方程的线图，y3 是线性回归线的线图。

回归方程的系数使用公式计算（参见图像）。

代码如下所示，带有结果输出。

```julia
using Statistics
xy = x .* y
xm = mean(x)
ym = mean(y)
xym = mean(xy)
x2 = x .^ 2
x2m = mean(x2)
ac = (xym - xm * ym) / (x2m - xm * xm)
bc = ym - ac * xm
ac, bc
```

```
(3.040366776530602, 3.7358219564957356)
```

在 `Flux` 中，我们可以建模类似的回归方程，并使用梯度下降法估计 `a` 和 `b`。最初，我们将定义参数 `a` 和 `b` 并使用参数计算模型。

```julia
using Flux
a, b = rand(1), rand(1)
ps = params([a, b])
model(x) = a .* x .+ b
```

我们将定义一个损失函数，并通过计算参数 `a` 和 `b` 的适当值来最小化它。

```julia
function loss(x, y)
    yp = model(x)
    sum((y .- yp) .^ 2)
end
```

损失是误差平方和；我们使用梯度下降优化器并更新参数。

```julia
data = zip(x, y)
opt = Descent(0.02)
for d in data
    gs = Flux.gradient(ps) do
        loss(d...)
    end
    Flux.Optimise.update!(opt, ps, gs)
    @info ps
end
```

模型、损失函数、优化器和数据获取技术可能因问题而异。

**图 17.4：** x 和 y 的绘图。y1 表示原始数据的散点图。y2 是 Flux 模型输出的散点图。y3 是线性回归线的线图。

模型输出是线性回归方程的近似。模型可能无法找到确切的最优值，因为随机梯度下降只是沿参数空间中损失函数梯度的搜索技术。可能需要更好的收敛策略来确保搜索达到最优值。以下图像显示了优化一次运行的结果。此处省略了绘图细节。然而，完整代码可在 Jupyter 笔记本 `Chapter-17/Chapter-17 Deep Learning.ipynb` 中获得。

**图 17.5：** 随机梯度下降搜索沿着由参数 a 和 b 参考的损失函数创建的表面的梯度进行。因此获得的最佳结果仍远离从分析方法计算出的绝对最优值。

## 模型动物园

机器学习是一个耗时且费力的过程。开发高质量模型、相关数据集和参数调优以展示结果，即使对于高级数据科学家也可能非常繁重。因此，拥有一组高质量的样本作为开发其他模型的参考非常重要。`Flux` 的模型动物园[^7] 正是基于这一前提启动的。有一类代表性问题的样本，数据科学家可以查看它们来设计自己的模型。请注意，这些问题仅具有代表性，仅用于学习目的。它们可能不是性能最优的代码。`Flux` 提供了一个通用建模框架。对于特定的图像分类问题，可以查看 `Metalhead`[^8] 等包。

## 神经网络类型

在深度学习中，我们讨论了 ANN。然而，ANN 有各种类型。类型大致基于计算单元或节点如何相互交互，或节点的拓扑结构。我们将通过从模型动物园改编的示例讨论三类神经网络。

- 全连接 (Dense) 网络
- 卷积网络 (CNN)
- 循环网络 (RNN)

### 全连接网络

我们解决如图 17.1 所示的 MNIST 手写数字分类问题。我们使用类似于图 17.2 的全连接 ANN 层，具有以下细节：

- 具有 784 个节点的输入层
- 具有 32 个节点和 ReLU 激活的中间层
- 具有 10 个节点和 softmax 激活的输出层

使用全连接层的一个缺点是参数数量。由于节点全连接，总参数数量将为：784 × 32 + 32 × 10 = 25,408 个参数。我们建议您查看随附 Jupyter 笔记本中的完整代码。

图像被展平为向量。它们被加载到数据加载器中，以 1024 的批次大小采样数据。

```julia
function getdata(args)
    ...
    xtrain, ytrain = MLDatasets.MNIST.traindata(Float32)
    # Flatten images to vector
    xtrain = Flux.flatten(xtrain)
    # One-hot-encode the labels
    ytrain = onehotbatch(ytrain, 0:9)
    # Batching
    train_data = DataLoader(xtrain, ytrain, batchsize=args.batchsize, shuffle=true)
    ...
    return train_data, test_data
end
```

这可以使用原语层轻松设计。

```julia
function build_model(; imgsize=(28,28,1), nclasses=10)
    return Chain(Dense(prod(imgsize), 32, relu),
                 Dense(32, nclasses))
end
```

作为训练的一部分，将执行以下代码：

```julia
function train(; kws...)
    # Initializing Model parameters
    args = Args(; kws...)
    # Load Data
    train_data, test_data = getdata(args)
    # Construct model
    m = build_model()
    train_data = args.device.(train_data)
    test_data = args.device.(test_data)
    m = args.device(m)
    loss(x, y) = logitcrossentropy(m(x), y)
    ## Training
    evalcb = () -> @show(loss_all(train_data, m))
    opt = ADAM(args.η)
    @epochs args.epochs Flux.train!(loss, params(m), train_data, opt, cb = evalcb)
    @show accuracy(train_data, m)
    @show accuracy(test_data, m)
end
```

高亮部分是 `Flux` 中实际的训练代码。数据按批次加载到模型中。使用 `ADAM` 作为优化器，在每批计算后更新梯度。您还需要使用优化器设置学习率。进度将使用 `evalcb` 回调间歇性报告。`train!` 函数仅接受一个回调作为输入，并在每批后调用它。训练将执行 `args.epochs` 次。这意味着整个训练数据将被用于训练模型 10 次。`logitcrossentropy` 用作损失函数。运行结束时，经过 10 个 epoch 可达到 91.77% 的分类准确率。MNIST 数据集的最先进准确率接近 99.9%。虽然我们不热衷于尝试最先进的准确率，但我们将看看 CNN，这是图像处理常用的网络。

### 卷积网络 (CNN)

CNN 基本源于经典卷积和图像处理特征工程的概念。图像处理工程师会设计卷积核并将其应用于图像以从图像中提取特征。例如，使用 Sobel 滤波器进行边缘提取。神经网络可用作自动计算滤波器参数[^9] 的手段；从而成为 CNN 模型的基础。

**图 17.6：** 一个卷积核将在图像两侧各截断一个像素。您可以使用填充，使这种缩减不受影响。卷积核实际上是 3 维的，这给输出图像引入了额外的通道。如果一个 3 通道图像与一个 3×3×8 的卷积核卷积，将需要 3×3×3×8 个参数。这些参数是相同的，并应用于像素的每个位置。参数共享减少了 CNN 中使用的总体参数。

虽然 CNN 重用参数，但卷积核在多个分辨率下应用。例如，maxpool 操作取图像的 2×2 像素网格，并用最高像素值替换这 4 个像素。由于这种子采样，maxpool 操作将图像的宽度和高度减半。

`getdata` 函数与之前看到的非常相似，只是我们取更小的图像批次 (CNN 中为 128)，并引入一个额外维度，使图像大小为 28×28×1。模型设计为原语层。

```julia
function build_model(args; imgsize = (28,28,1), nclasses = 10)
    return Chain(
    # Input image 28x28x1 image
    Conv((3, 3), imgsize[3]=>4, relu),
    #Output: 26x26x4 Params: 3x3x1x4=36
    BatchNorm(4),
    Conv((3, 3), 4=>4, relu),
    #Output: 24x24x4 Params: 3x3x4x4=144
    BatchNorm(4),
    MaxPool((2,2)), #Output: 12x12x4
    Dropout(0.1),
    Conv((3, 3), 4=>8, relu),
    #Output: 10x10x8 Params: 3x3x4x8=288
    BatchNorm(8),
    Conv((3, 3), 8=>8, relu),
    #Output: 8x8x8 Params: 3x3x8x8=576
    BatchNorm(8),
    MaxPool((2,2)), #Output: 4x4x8
    Dropout(0.1),
    Conv((3, 3), 8=>32, pad=(1, 1), relu),
    #Output: 4x4x32 Params: 3x3x8x32=2304
    BatchNorm(32),
    Conv((3, 3), 32=>nclasses, relu),
    #Output: 2x2x10 Params: 3x3x32x10=2880
    BatchNorm(10),
    AdaptiveMeanPool((1, 1)), #Output: 1x1x10
    flatten #Output: 10
    )
end
```

它是卷积、批量归一化、最大池化和 dropout 的层。`Flux` 提供简单的层，如原语，以非常类似于 *Keras* 等框架的方式建模 DNN 层。模型本身表现得像一个可调用对象。因此，您可以像 `model(x)` 这样调用以获得预测值。

训练代码与前一个类似，增加了在达到 99% 测试准确率后停止执行的功能。为提供最大测试准确率的运行保存模型。加载保存的模型以打印测试结果。

```julia
function train(; kws...)
    ...
    best_acc = 0.0
    last_improvement = 0
    for epoch_idx in 1:args.epochs
        Flux.train!(loss, params(model), train_set, opt)
        acc = accuracy(test_set, model)
        if acc >= best_acc
            BSON.@save joinpath(args.savepath, "mnist_conv.bson")
                model=cpu(model) epoch_idx acc
            best_acc = acc
            last_improvement = epoch_idx
        end
        acc >= 0.99 && break
        if epoch_idx - last_improvement >= 5 && opt.eta > 1e-6
            opt.eta /= 10.0
            last_improvement = epoch_idx
        end
    end
end
```

当模型准确率在 5 个 epoch 内没有提高时，学习率会动态更新。如果您运行此模型约 10 次迭代，您将能够为测试数据达到 99% 的准确率，比全连接模型有显著提升。CNN 代码在 GPU 或 TPU 上执行得更好。如果您使用基于 CPU 的系统，可能会发现示例执行速度比您预期的慢。

### 循环网络 (RNN)

RNN[^10] 用于解决序列问题。例如，文本和语音涉及单词或字符或语音音素的序列。由于标记出现的顺序，它们具有有意义的上下文。同样，输出也可以是序列化的。例如，给定一个单词序列猜测下一个单词，如填空练习。

**图 17.7：** RNN 随序列的每个输入更新状态。节点在时间尺度上的展开如上图所示。

RNN 的前向传递可能有如下方程：

```
s[t] = tanh(U * x[t] + W * s[t-1])
o[t] = softmax(V * s[t])
```

在求解 RNN 参数时，网络按时间尺度展开，如图所示。由于序列可以是任意大小，要么将它们视为一个大尺寸序列，用空输入填充有限的大序列，要么使用序列结束标记来结束序列。通常，对展开的网络进行反向传播。状态参数存储在宽度为 H 的向量中。U、W 和 V 向量独立于时间。虽然它们作为反向传播步骤的一部分被更新，但更新的值将用于后续的前向传递。

在我们尝试解决的问题中，我们采用 5 种语言的字符序列并将它们输入循环网络。我们想推断字符序列代表的语言。由于我们使用字符序列并忽略所有重音和大小写敏感字符，我们的词汇量大小为 39。输出类别数为 5 (`:en`, `:fr`, `:it`, `:da` 和 `:es`)。因此矩阵将具有以下维度：

- U - 5 × 39
- W - 5 × 5
- V - 5 × 5 (V 在 `Flux RNNCell` 中被忽略)

虽然 RNN 是一个有用的工具，但可能不是大序列的最佳选择。随着序列变长，梯度可能消失，反向传播可能无法有效更新权重。因此，网络会慢慢遗忘序列中较早的输入。**长短期记忆** (`LSTM`)[^11] 和 **门控循环单元** (`GRU`) 等网络提供额外的门来选择性地忽略输入、输出或之前的状态值。我们使用 LSTM 为语言标识器建模。模型可能如下所示。完整代码可从相关的 Jupyter 笔记本获得。

```julia
function build_model(args)
    return LSTM(args.alphabet_len, args.langs_len)
end

function model(x, scanner)
    return scanner.(x.data)[end]
end
```

`build_model` 创建一个扫描器，扫描字符序列并产生输出序列。然而，我们只对序列的最后一个值感兴趣，并将其用于损失计算。训练约 5 个 epoch 后获得的最佳测试准确率为 0.78。虽然对于这样一个简单的模型这很合理，但最先进水平在 8 种语言的 USENET 组上接近 99.8%[^12]。此外，就像其他原语一样，RNN、LSTM 或 GRU 可以堆叠成层以形成复杂的深度网络。它们也可以与 CNN 和 Dense 网络堆叠。Transformers[^13] 是有用的序列建模原语，广泛用于语言建模。BERT 和 GPT 是一些著名的基于 Transformer 的架构。

## 总结

`ANN` 如今在工业中被广泛使用。应用目前可见于所有可能的领域。我们快速回顾了作为模型动物园一部分提供的示例。虽然示例提供了关于 Flux 建模能力的一些见解，但您需要进一步探索深度学习理论的细节，并尝试使用 Flux 解决实际问题，才能有效地构建模型。

# 练习

1.  在全连接网络的示例中，softmax 未用作最后一层的激活函数。然而，这已通过某种替代方式得到适应。您能识别出来吗？
2.  什么是批量归一化？为什么它在 CNN 中使用？
3.  我们看到 CNN 与 2-D 卷积核和图像一起使用。CNN 可以用于文本吗？您必须引入什么样的变化才能将它们用于文本？
4.  计算基于 LSTM 的语言识别问题所需的参数。参数数量的增加是否合理？
5.  回顾语言识别模型的综述论文，并使用 Flux 实现其中一个模型，使其在测试集上提供 99% 或更高的准确率。

---

[^1]: Seung-Hwan Lim, Steven Robert Young, and Robert Patton, An analysis of image storage systems for scalable training of deep neural networks, The Seventh workshop on Big Data Benchmarks, Performance Optimization, and Emerging Hardware (in conjunction with ASPLOS'16), 2016.
[^2]: Lecun et al., THE MNIST DATABASE of handwritten digits, <http://yann.lecun.com/exdb/mnist/index.html>
[^3]: 非线性函数的选择取决于问题。在 CNN 中，线性整流单元，*LU(x) = x if x > 0 else 0*，常用作激活函数。
[^4]: Goodfellow et al., The Deep Learning Book, page 200, <https://www.deeplearningbook.org/contents/mlp.html#pf25>
[^5]: Flux, The Elegant Machine Learning Stack, <https://fluxml.ai/>
[^6]: TensorFlow, Julia 的 TensorFlow 包装器，该包处于最低维护模式，没有添加新功能，并绑定到较旧版本的 `libtensorflow` <https://github.com/malmaud/TensorFlow.jl>
[^7]: model-zoo, Do not feed the models, <https://github.com/FluxML/model-zoo>
[^8]: `Metalhead.jl`, Flux 的计算机视觉模型, <https://github.com/FluxML/Metalhead.jl>
[^9]: Dan Ciresan, Ueli Meier, Jurgen Schmidhuber, Multi-column Deep Neural Networks for Image Classification, Technical Report No. IDSIA-04-12
[^10]: 要详细了解 RNN 概念，您可以参考 Denny Britz 于 2015 年 9 月的博客文章：<http://www.wildml.com/2015/09/recurrent-neural-networks-tutorial-part-1-introduction-to-rnns/>
[^11]: Christpher Olah, Understanding LSTM Networks, August 2015. <http://colah.github.io/posts/2015-08-Understanding-LSTMs/>
[^12]: Tommi Jauhiainen et al, Automatic language identification in texts: a survey, JAIR, May 2019, <https://doi.org/10.1613/jair.1.11675>
[^13]: Transformers, Transformer 模型的 Julia 实现, <https://github.com/chengchingwen/Transformers.jl/>

# 索引

**符号**

- 8-queens problem

**A**

- about
  - functions [55](#n4upl4fndax)
  - operators
- abstract array types, [122](#n4upl4fnday)
- AbstractChar
- AbstractString, [145](#n4upl4fndaz)
- Abstract Syntax Trees (AST) [149](#n4upl4fnda0), [150](#n4upl4fnda1)
- abstract type [28](#n4upl4fnda2)
- accessor method [218](#n4upl4fnda3)
- Amazon Web Services [304](#n4upl4fnda4), [305](#n4upl4fnda5)
- American National Standard Institute (ANSI) [129](#n4upl4fnda6)
- American Standard Code for Information Interchange (ASCII) [129](#n4upl4fnda6)
- anonymous function [57](#n4upl4fnda7)
- Any type, [33](#n4upl4fnda8)
- area method [71](#n4upl4fnda9)
- array [85](#n4upl4fndba)
- array inner product
- Artificial Neural Networks (ANN)
- aspect_ratio method [71](#n4upl4fnda9)
- assignment
- associative collection
  - about [92](#n4upl4fndbb)
  - dict object [92](#n4upl4fndbb), [93](#n4upl4fndbc)
  - set object
- asynchronous programming
  - about [174](#n4upl4fndbd), [175](#n4upl4fndbe)
  - channel, [178](#n4upl4fndbf)
  - lock [178](#n4upl4fndbf)
  - task [176](#n4upl4fndbg)
- Atom, [256](#n4upl4fndbh)
- Automated Differentiation (AD) [340](#n4upl4fndbi)
- Azure Kubernetes Services (AKS)
  - about [301](#n4upl4fndbj)
  - orchestrating, from Julia [302](#n4upl4fndbk)–[304](#n4upl4fnda4)

**B**

- backends [321](#n4upl4fndbl)
- benchmarking [226](#n4upl4fndbm)–[229](#n4upl4fndbn)
- Binary Coded Decimal Interchange Code (EBCDIC) [129](#n4upl4fnda6)
- binary dependencies
  - about [289](#n4upl4fndbo)
  - native binaries, using [290](#n4upl4fndbp)
- bit type
- Bool [27](#n4upl4fndbq)
- broadcast
  - about, [117](#n4upl4fndbr)
  - performance [118](#n4upl4fndbs)
  - versus map [118](#n4upl4fndbs)

**C**

- C encoding
- character array [143](#n4upl4fndbt)
- character (Char)
- characters, [129](#n4upl4fnda6)
- cloud environment [296](#n4upl4fndbu)
- code generation tools
  - about [229](#n4upl4fndbn)
  - allocations [234](#n4upl4fndbv), [235](#n4upl4fndbw)
  - code, removing [236](#n4upl4fndbx)
  - parametric data types [235](#n4upl4fndbw), [236](#n4upl4fndbx)
  - type stability [229](#n4upl4fndbn), [231](#n4upl4fndby), [233](#n4upl4fndbz), [234](#n4upl4fndbv)
- code-run-fix, [262](#n4upl4fndb0)
- Command Line Interface (CLI) [301](#n4upl4fndbj)
- Comma separated values (CSV) [186](#n4upl4fndb1)
- compound statements
  - about [40](#n4upl4fndb2)
  - begin end [40](#n4upl4fndb2)
- comprehensions [101](#n4upl4fndb3), [102](#n4upl4fndb4)
- compressed sparse column (CSC) [124](#n4upl4fndb5)
- conditional statements
  - about [40](#n4upl4fndb2)
  - if else [40](#n4upl4fndb2), [41](#n4upl4fndb6)
  - switch case [41](#n4upl4fndb6)–
  - unstructured branching, [44](#n4upl4fndb7)
- constants, [190](#n4upl4fndb8), [191](#n4upl4fndb9)
- constructors
  - about, [70](#n4upl4fndca), [87](#n4upl4fndcb), [88](#n4upl4fndcc)
  - return value [70](#n4upl4fndca)
- container [106](#n4upl4fndcd), [107](#n4upl4fndce)
- continuous integration
  - about [283](#n4upl4fndcf)–[287](#n4upl4fndcg)
  - code coverage, visualizing [288](#n4upl4fndch)
- convolutional network (CNN) [346](#n4upl4fndci)–[349](#n4upl4fndcj)
- custom string literals [158](#n4upl4fndck), [159](#n4upl4fndcl)
- custom strings
  - about
  - AbstractChar
  - AbstractString, [145](#n4upl4fndaz)

**D**

- data environment
  - setting up [308](#n4upl4fndcm)
- data types
  - about [68](#n4upl4fndcn)
  - multiple dispatch
- data visualization [319](#n4upl4fndco)–[321](#n4upl4fndbl)
- debugging
  - about [258](#n4upl4fndcp)
  - assert
  - line debugging, in IDE [260](#n4upl4fndcq)
  - log
  - print
  - REPL tool, using, [260](#n4upl4fndcq)
  - unit tests
- decreasing ranges, [85](#n4upl4fndba)
- deep learning –[340](#n4upl4fndbi)
- default streams
  - about
  - binary I/O [184](#n4upl4fndcr)
  - file I/O [184](#n4upl4fndcr)–[186](#n4upl4fndb1)
  - text I/O, [183](#n4upl4fndcs)
- Defined Languages (UDL) [254](#n4upl4fndct)
- delegation, [218](#n4upl4fnda3)
- dict object
  - about [92](#n4upl4fndbb), [93](#n4upl4fndbc)
  - get method [93](#n4upl4fndbc), [94](#n4upl4fndcu)
  - hashing [94](#n4upl4fndcu)
  - setindex method [94](#n4upl4fndcu)
- dimension [107](#n4upl4fndce), [108](#n4upl4fndcv)
- distributed computing [175](#n4upl4fndbe), [181](#n4upl4fndcw)
- documentation
  - about [278](#n4upl4fndcx), [279](#n4upl4fndcy)
  - configuring [279](#n4upl4fndcy)–[283](#n4upl4fndcf)
- Document Object Models (DOM) [309](#n4upl4fndcz)

**E**

- editor integration
  - about [250](#n4upl4fndc0)
  - emacs [251](#n4upl4fndc1)–[253](#n4upl4fndc2)
  - Notepad++ [253](#n4upl4fndc2), [254](#n4upl4fndct)
  - vim (vi) [250](#n4upl4fndc0)
- efficiency [125](#n4upl4fndc3)
- Elastic Kubernetes Services (EKS) [301](#n4upl4fndbj)
- emacs [251](#n4upl4fndc1)–[253](#n4upl4fndc2)
- encoding
  - about [129](#n4upl4fnda6), [141](#n4upl4fndc4), [142](#n4upl4fndc5)
  - function [142](#n4upl4fndc5), [143](#n4upl4fndbt)
- end-to-end sequence labeling
- exception handling
  - about
  - exception information, [51](#n4upl4fndc6)
  - finally
  - rethrow [49](#n4upl4fndc7)
  - throw [49](#n4upl4fndc7)
  - try catch [49](#n4upl4fndc7)
- extractive summarization
  - about [333](#n4upl4fndc8)
- evaluation metrics

**F**

- FileIO [308](#n4upl4fndcm), [309](#n4upl4fndcz)
- Filesystem [172](#n4upl4fndc9)–[174](#n4upl4fndbd)
- floating point numbers [27](#n4upl4fndbq)
- Flux [340](#n4upl4fndbi)–[343](#n4upl4fndda)
- font and glyphs [132](#n4upl4fnddb)
- for loop [96](#n4upl4fnddc), [97](#n4upl4fnddd)
- for statement
  - about [44](#n4upl4fndb7), [45](#n4upl4fndde)
  - continue and break [45](#n4upl4fndde)
  - do while
  - for in
  - multiple range objects, [47](#n4upl4fnddf)
  - while [47](#n4upl4fnddf)
- fully connected network
- function
  - about [55](#n4upl4fndax), [156](#n4upl4fnddg)
  - collect
  - constructors [87](#n4upl4fndcb), [88](#n4upl4fndcc)
  - fill and similar
  - hcat [91](#n4upl4fnddh), [92](#n4upl4fndbb)
  - hvcat [91](#n4upl4fnddh), [92](#n4upl4fndbb)
  - reshape, [91](#n4upl4fnddh)
  - true and false
  - vcat [91](#n4upl4fnddh), [92](#n4upl4fndbb)
  - zeros and ones
- functional programming principles
  - about [207](#n4upl4fnddi)
  - declarative programming
  - functions, with no side effects
  - higher-order functions
  - immutability, [211](#n4upl4fnddj)
- function do [97](#n4upl4fnddd), [98](#n4upl4fnddk)

**G**

- Gated Recurrent Units (GRU) [350](#n4upl4fnddl)
- generated functions [159](#n4upl4fndcl), [160](#n4upl4fnddm)
- generators [101](#n4upl4fndb3), [102](#n4upl4fndb4)
- GitHub
  - registration [273](#n4upl4fnddn)
- Git Repositories [265](#n4upl4fnddo)
- Google Clouds Platform (GCP) [305](#n4upl4fnda5)
- Google Kubernetes Engine (GKE) [301](#n4upl4fndbj)
- Graphical User Interfaces (GUI) [222](#n4upl4fnddp)

**H**

- high-performance code
  - global variables [243](#n4upl4fnddq)–[245](#n4upl4fnddr)
  - guidelines [240](#n4upl4fndds)
  - memoization [240](#n4upl4fndds)–[243](#n4upl4fnddq)

**I**

- idle loop processing [223](#n4upl4fnddt)
- image data, [317](#n4upl4fnddu)
- Imperative Programming [207](#n4upl4fnddi)
- indexing,
- index types
  - assignment
  - Boolean index [112](#n4upl4fnddv)
  - Cartesian index [111](#n4upl4fnddw), [112](#n4upl4fnddv)
  - interface, [114](#n4upl4fnddx)
  - linear index [111](#n4upl4fnddw)
  - ranges, [110](#n4upl4fnddy)
  - scalars
  - special indices
  - vectors [110](#n4upl4fnddy), [111](#n4upl4fnddw)
- inline evaluation [152](#n4upl4fnddz)
- Input and Output (I/O)
  - about
  - default streams
  - delimited files [186](#n4upl4fndb1)
  - memory and I/O [189](#n4upl4fndd0), [190](#n4upl4fndb8)
  - network communication –[189](#n4upl4fndd0)
- input arguments
  - about [57](#n4upl4fnda7)
  - default values [59](#n4upl4fndd1)
  - fixed arguments length [57](#n4upl4fnda7), [58](#n4upl4fndd2)
  - slurping
  - splatting
  - variable number of arguments [58](#n4upl4fndd2), [59](#n4upl4fndd1)
- integral type [27](#n4upl4fndbq)
- integrated development environment (IDE)
  - about, [254](#n4upl4fndct)
  - Atom, [256](#n4upl4fndbh)
  - Visual Studio Code (VS Code), [258](#n4upl4fndcp)
- Interactive Julia (IJulia) [16](#n4upl4fndd3)
- interface
  - about, [114](#n4upl4fnddx), [211](#n4upl4fnddj), [212](#n4upl4fndd4)
  - holy traits [214](#n4upl4fndd5)–[216](#n4upl4fndd6)
  - super type [212](#n4upl4fndd4)–[214](#n4upl4fndd5)
- interned strings [150](#n4upl4fnda1), [151](#n4upl4fndd7)
- interpolation [152](#n4upl4fnddz), [154](#n4upl4fndd8)–[156](#n4upl4fnddg)
- ISO-8859
- iterate methods [99](#n4upl4fndd9)
- iteration
  - about [96](#n4upl4fnddc)
  - for loop [96](#n4upl4fnddc), [97](#n4upl4fnddd)
  - function do [97](#n4upl4fnddd), [98](#n4upl4fnddk)
- iteration framework
  - about [98](#n4upl4fnddk), [99](#n4upl4fndd9)
  - example [100](#n4upl4fndea), [101](#n4upl4fndb3)
- iterative statements
  - about [44](#n4upl4fndb7)
  - for statement [44](#n4upl4fndb7), [45](#n4upl4fndde)

**J**

- Julia
  - Azure Kubernetes Services (AKS), orchestrating [302](#n4upl4fndbk)–[304](#n4upl4fnda4)
  - deploying, [298](#n4upl4fndeb)
  - Docker container [299](#n4upl4fndec), [300](#n4upl4fnded)
  - REST-based web services [298](#n4upl4fndeb), [299](#n4upl4fndec)
- Julia built-in types
  - about [26](#n4upl4fndee)
  - character (Char)
  - nothing [26](#n4upl4fndee)
  - numeric type [27](#n4upl4fndbq)
  - string
- Julia concepts
  - about
  - active community [6](#n4upl4fndef)
  - advantage
  - design for researcher [3](#n4upl4fndeg), [4](#n4upl4fndeh)
  - development toolset [4](#n4upl4fndeh)
  - enterprise-friendly architecture [6](#n4upl4fndef)
  - flexible licensing
  - integration, with platforms [3](#n4upl4fndeg)
  - metaprogramming [4](#n4upl4fndeh)
  - modern programming language, [3](#n4upl4fndeg)
  - open source
  - package ecosystem
  - performance
  - server platform
- Julia language
  - about
  - arrays [9](#n4upl4fndei)
  - collections [9](#n4upl4fndei)
  - conditions
  - control flow
  - data types
  - functions and methods, [9](#n4upl4fndei)
  - installer binaries, downloading
  - installer binaries, for Linux
  - installer binaries, for Windows, [15](#n4upl4fndej)
  - iterations
  - metaprogramming [10](#n4upl4fndek)
  - modules –[169](#n4upl4fndel)
  - overview
  - runtime environment, elaborating
  - setting up
  - standard libraries [10](#n4upl4fndek)
  - standard modules [169](#n4upl4fndel), [170](#n4upl4fndem)
  - strings [9](#n4upl4fndei)
  - version
- Julia language, development environment
  - about [10](#n4upl4fndek)
  - debugging
  - deployment
  - IDE
  - package management
  - performance management
  - programming guidelines [10](#n4upl4fndek)
- Julia language, packages
  - about
  - data transformation
  - deep learning
  - text analytics
- Julia performance
  - about [222](#n4upl4fnddp)
  - algorithm [224](#n4upl4fnden), [225](#n4upl4fndeo)
  - cloud computing resources [224](#n4upl4fnden)
  - optimization [225](#n4upl4fndeo)
  - optimizing [222](#n4upl4fnddp)–[224](#n4upl4fnden)
  - runtime, comparing [225](#n4upl4fndeo), [226](#n4upl4fndbm)
- Julia programs [18](#n4upl4fndep)
- Julia type
  - about
  - constants
  - literals
  - tuples [25](#n4upl4fndeq)
  - variables, [23](#n4upl4fnder)
- Jupyter
  - about [16](#n4upl4fndd3)
  - configuring [17](#n4upl4fndes)
- Just-in-Time (JIT) compilation,

**K**

- Kubernetes [300](#n4upl4fnded)–[302](#n4upl4fndbk)

**L**

- Latent Dirichlet Allocation (LDA)
- Latent Semantic Analysis (LSA)
- linear algebra [125](#n4upl4fndc3), [126](#n4upl4fndet)
- linear index [111](#n4upl4fnddw)
- literals
- Long Short Term Memory (LSTM) [350](#n4upl4fnddl)
- long-term support (LTS) [6](#n4upl4fndef)
- l-valued expressions

**M**

- macros
  - about [156](#n4upl4fnddg), [160](#n4upl4fnddm)
  - assert [162](#n4upl4fndeu)
  - calling convention, [158](#n4upl4fndck)
  - eval [161](#n4upl4fndev)
  - source locations [160](#n4upl4fnddm), [161](#n4upl4fndev)
  - time [163](#n4upl4fndew)
- maintainability guidelines
  - about –[204](#n4upl4fndex)
  - coding style [204](#n4upl4fndex)–[207](#n4upl4fnddi)
- map
  - versus broadcast [118](#n4upl4fndbs)
- mapreduce [120](#n4upl4fndey)
- members
- memoization [240](#n4upl4fndds)
- memory layout
- metaprogramming, [149](#n4upl4fnda0)
- Microsoft Azure [305](#n4upl4fnda5)
- Microsoft office documents [313](#n4upl4fndez)–[315](#n4upl4fnde0)
- model zoo
- module
  - about
  - usage
- multiline expression [152](#n4upl4fnddz)–[154](#n4upl4fndd8)
- multithreading [175](#n4upl4fndbe), [178](#n4upl4fndbf)–[180](#n4upl4fnde1)
- mutable struct

**N**

- Naïve Bayes Classifier [332](#n4upl4fnde2)
- Named Entity Recognition (NER), [335](#n4upl4fnde3)
- nested quotes [154](#n4upl4fndd8)–[156](#n4upl4fnddg)
- network
- neural network, types
  - about
  - convolutional network (CNN) [346](#n4upl4fndci)–[349](#n4upl4fndcj)
  - fully connected network –[346](#n4upl4fndci)
  - recurrent neural network (RNN) [349](#n4upl4fndcj)–[351](#n4upl4fnde4)
- notable modules
  - about [191](#n4upl4fndb9)
  - dates [191](#n4upl4fndb9)–[193](#n4upl4fnde5)
  - logging –[196](#n4upl4fnde6)
  - random number [196](#n4upl4fnde6), [197](#n4upl4fnde7)
  - statistics [196](#n4upl4fnde6)
- Notepad++ [253](#n4upl4fndc2), [254](#n4upl4fndct)
- N-queens, [268](#n4upl4fnde8)
- NTuple [79](#n4upl4fnde9)
- numeric type
  - about [27](#n4upl4fndbq)
  - abstract type [28](#n4upl4fnda2)
  - bit type
  - Bool [27](#n4upl4fndbq)
  - floating point numbers [27](#n4upl4fndbq)
  - integral type [27](#n4upl4fndbq)
  - primitive type
  - rational and complex type

**O**

- Office Open XML (OOXML) [313](#n4upl4fndez)
- open source
  - about [219](#n4upl4fndfa)
  - contributing, to Julia [220](#n4upl4fndfb)
- operation types
  - about [34](#n4upl4fndfc)
  - isa
  - supertype
  - typeof
- optional methods [99](#n4upl4fndd9), [100](#n4upl4fndea)

**P**

- package
  - about [265](#n4upl4fnddo)
  - creating [268](#n4upl4fnde8)
  - functionality, developing [272](#n4upl4fndfd), [273](#n4upl4fnddn)
  - initializing –[272](#n4upl4fndfd)
  - problem statement
  - usage
- package architecture
  - about –[293](#n4upl4fndfe)
- package module
  - REPL command [293](#n4upl4fndfe)
- package, characteristics
  - environment [266](#n4upl4fndff)
  - folder structure [266](#n4upl4fndff)
  - Git Repositories [265](#n4upl4fnddo)
  - module [266](#n4upl4fndff)
- paging effect
- parallel programming
  - about, [174](#n4upl4fndbd)
  - asynchronous programming [175](#n4upl4fndbe)
  - distributed computing [181](#n4upl4fndcw)
  - multithreading [178](#n4upl4fndbf)–[180](#n4upl4fnde1)
- parametric data type
  - about [33](#n4upl4fnda8), [34](#n4upl4fndfc), [71](#n4upl4fnda9)
  - dispatch interface [71](#n4upl4fnda9), [72](#n4upl4fndfg)
- Part of Speech (POS)
- patterns
  - about [211](#n4upl4fnddj)
  - accessor method [218](#n4upl4fnda3)
  - delegation, [218](#n4upl4fnda3)
  - interface [211](#n4upl4fnddj)
  - point coincident tolerance
- polymorphic method
  - about [68](#n4upl4fndcn)
  - constructors, [70](#n4upl4fndca)
  - data types [68](#n4upl4fndcn)
  - parametric data type [71](#n4upl4fnda9)
- predefined data structures
- primitive type
- printing data types
  - about, [37](#n4upl4fndfh)
  - print [37](#n4upl4fndfh)
  - show [37](#n4upl4fndfh)
  - string [37](#n4upl4fndfh)
- profiling –[240](#n4upl4fndds)
- project
  - about [265](#n4upl4fnddo)
  - usage
- project environment [290](#n4upl4fndbp)
- public cloud infrastructures
  - about [304](#n4upl4fnda4)
  - Amazon Web Services [304](#n4upl4fnda4)
  - Google Clouds Platform (GCP) [305](#n4upl4fnda5)
- pull requests (PR) [220](#n4upl4fndfb)

**R**

- ranges
  - about [83](#n4upl4fndfi), [110](#n4upl4fnddy)
  - decreasing ranges, [85](#n4upl4fndba)
  - StepRange
  - UnitRange
- rational and complex type
- Read-Eval-Print Loop (REPL) [15](#n4upl4fndej), [16](#n4upl4fndd3)
- Recall Oriented Understudy for Gisting Evaluation (ROUGE)
- recurrent neural network (RNN) [349](#n4upl4fndcj)–[351](#n4upl4fnde4)
- recursion
  - about –[64](#n4upl4fndfj)
  - code, computing [65](#n4upl4fndfk)–[67](#n4upl4fndfl)
- reduction operations
  - about
  - associativity, [120](#n4upl4fndey)
  - mapreduce [120](#n4upl4fndey)
  - slices [120](#n4upl4fndey)
- return value
  - about
  - multiple values
  - type safety

**S**

- scalars
- semantic analysis, [332](#n4upl4fnde2)
- set object
  - about
  - union and intersection [96](#n4upl4fnddc)
- short form
- single dispatch interface
- singleton [83](#n4upl4fndfi)
- slicing [114](#n4upl4fnddx), [115](#n4upl4fndfm)
- slurping
- sparse array
  - about
  - efficiency [125](#n4upl4fndc3)
- sparse matrix storage [124](#n4upl4fndb5), [125](#n4upl4fndc3)
- sparse vector storage
- sparse matrix storage [124](#n4upl4fndb5), [125](#n4upl4fndc3)
- sparse vector storage
- special indices
- stack traces [51](#n4upl4fndc6)
- standard library (stdlib) [186](#n4upl4fndb1)
- StepRange
- string, [132](#n4upl4fnddb), [133](#n4upl4fndfn)
- string method
  - about [133](#n4upl4fndfn)
  - case conversion [138](#n4upl4fndfo)
  - comparison [133](#n4upl4fndfn), [134](#n4upl4fndfp)
  - iteration [134](#n4upl4fndfp), [135](#n4upl4fndfq)
  - pattern matching
  - regular expression, [141](#n4upl4fndc4)
  - split and concatenate [136](#n4upl4fndfr)–[138](#n4upl4fndfo)
- struct
- symbol [150](#n4upl4fnda1), [151](#n4upl4fndd7)
- system shell
  - accessing [171](#n4upl4fndfs), [172](#n4upl4fndc9)

**T**

- tabular data [317](#n4upl4fnddu)–[319](#n4upl4fndco)
- Tail Call Optimization (TCO) [67](#n4upl4fndfl)
- test automation
  - about [274](#n4upl4fndft)–[276](#n4upl4fndfu)
  - coverage [276](#n4upl4fndfu)–[278](#n4upl4fndcx)
- TextAnalysis
  - embeddings [329](#n4upl4fndfv), [330](#n4upl4fndfw)
  - preprocessing [326](#n4upl4fndfx)
  - tokenization [327](#n4upl4fndfy), [328](#n4upl4fndfz)
  - word representation [328](#n4upl4fndfz), [329](#n4upl4fndfv)
- TextAnalysis, document types
  - FileDocument [326](#n4upl4fndfx)
  - NGramDocument [326](#n4upl4fndfx)
  - StringDocument [326](#n4upl4fndfx)
  - TokenDocument [326](#n4upl4fndfx)
- text data
  - about [309](#n4upl4fndcz)
  - delimited files [309](#n4upl4fndcz)
  - HTML files [311](#n4upl4fndf0), [312](#n4upl4fndf1)
  - Microsoft office documents [313](#n4upl4fndez)–[315](#n4upl4fnde0)
  - PDF files [312](#n4upl4fndf1), [313](#n4upl4fndcz)
  - XML files [309](#n4upl4fndcz)–[311](#n4upl4fndf0)
- text processing pipeline
  - about [324](#n4upl4fndf2), [325](#n4upl4fndf3), [326](#n4upl4fndfx)
  - acquisition [324](#n4upl4fndf2)
  - models [325](#n4upl4fndf3)
  - representation [325](#n4upl4fndf3)
  - tokenization [325](#n4upl4fndf3)
- Tuple
  - about, [79](#n4upl4fnde9)
  - as collection [79](#n4upl4fnde9)
  - integers type parameter [80](#n4upl4fndf4), [81](#n4upl4fndf5)
  - integer type parameter
  - NTuple [79](#n4upl4fnde9)
  - value parameter, [83](#n4upl4fndfi)
- tuples [25](#n4upl4fndeq)
- type interaction
  - about [72](#n4upl4fndfg), [73](#n4upl4fndf6)
  - conversion [73](#n4upl4fndf6), [74](#n4upl4fndf7)
  - promotion [74](#n4upl4fndf7), [75](#n4upl4fndf8)

**U**

- Unicode
  - about
  - in Julia [132](#n4upl4fnddb)
- Unicode transformation [131](#n4upl4fndf9), [132](#n4upl4fnddb)
- UnitRange
- Universal Coded Character Set (UCS)
- Universal Language Model Fine Tuning (ULMFiT) [335](#n4upl4fnde3)
- user-defined types
  - about
  - members
  - mutable struct
  - struct

**V**

- variables
  - about, [23](#n4upl4fnder)
  - definition, versus initialization [23](#n4upl4fnder)
- vectors [110](#n4upl4fnddy), [111](#n4upl4fnddw)
- vim (vi) [250](#n4upl4fndc0)
- Visual Studio Code (VS Code) [250](#n4upl4fndc0), [258](#n4upl4fndcp)

**W**

- walkdir() method [173](#n4upl4fndga)
- word stems [328](#n4upl4fndfz)

