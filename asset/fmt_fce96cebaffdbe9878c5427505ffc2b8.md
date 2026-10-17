
julia> using PDFIO

julia> """

```
`getPDFText(src, out) -> Dict`
```

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

### Microsoft Office 文档

Microsoft Office 文档是常见的文档形式。虽然文档格式是一个名为 **Office Open XML** (**OOXML**) 的开放标准[⁹]，最初由 Microsoft 支持，但庞大的规范给文档消费者直接在其应用程序中使用它们带来了重大挑战。基于 `Apache Tika`、`Apache POI` 和 `Apache FOP` 编写的 `Taro`[¹⁰] 提供了基于 `JavaCall` 的与 Julia 的集成。同一系统还支持 PDF 文件的读取和写入。界面相当简单，具有以下功能：

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

我们将在后面的章节讨论 `DataFrames`[¹¹]。就我们的理解而言，它们有助于轻松访问表格数据。由于 MS Excel 用于表格数据，因此已经开发了许多用于此目的的包。其中之一是 `XLSX.jl`[¹²]。该包用纯 Julia 编写，不需要配置 Java 的开销。`XLSX.jl` 是使用 ECMA-376 标准编写的。这也使其能够灵活地使用类似 `WorkSheet`、`Cell IDs` 等文件结构来访问 MS Excel 文件。

```julia
julia> using XLSX
julia> xlsx = XLSX.readxlsx("df-test.xlsx")
XLSXFile("df-test.xlsx") containing 1 Worksheet
  sheetname size    range
-------------------------------------------------
      Sheet1 9x5     B2:F10
julia> sheet = xlsx["Sheet1"]
9×5 XLSX.Worksheet: "Sheet1"
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

虽然内存似乎按 2 维或 3 维排列，但实际并非如此。这意味着在图像中所有红色分量在一起，随后是绿色强度值，依此类推。图像文件格式不一定以这种方式存储数据。它们应用多种变换并压缩数据，将其作为数字二进制流存储。然而，几乎所有图像应用在消费或渲染图像前，都会将数据转换为上述排列之一。在 FileIO 部分，我们加载了一个 tiff 文件，创建的图像对象类型为 `Array{ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}},2}`。如果我们暂且不考虑复杂的类型，它只是一个 2 维数组。由于灰度图像只有一个分量，因此分量类型的第三个维度不相关。类型 `ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}}` 本身就相当复杂。传统上，图像分量被归一化为 0.0 到 1.0 的浮点值。由于浮点数需要更大的存储空间，可以用一个字节的数据表示，其中 0 映射到 0.0，255 映射到 1.0；因此是数字的定点表示。在一个字节的数据中，甚至所有 8 位可能不都被一个值消耗。可能只使用 4 位。因此，一个字节可用于存储两个像素强度。`ImageCore`[¹³] 包有许多此类图像表示，建议读者参考以了解各种图像格式。您也可以使用 `JuliaImages`[¹⁴] 进行图像处理。OpenCV 库提供了一个教程[¹⁵]，用于与 Julia 前端集成。

# 表格数据

表格数据在许多数据应用中非常常见。RDBMS 的使用充当了表格数据的广泛来源。此外，我们看到像 R 和 Python Pandas 这样的语言将表格数据作为其维护记录的基础。我们已经看到了带有 CSV 等分隔文件的表格数据源。我们之前也使用 Taro 将 Excel 文件作为 `DataFrame` 加载。Julia 创建了一个名为 `Tables.jl`[¹⁶] 的抽象接口，可用于访问表格数据。

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

此外，您可以使用 `TableOperations` 包对表格数据进行 `select`、`map` 和 `filter` 等操作。Julia 还提供了一个名为 `JuliaDB`[¹⁷] 的高性能数据库。建议读者将了解其功能作为练习的一部分。

# 数据可视化

视觉反馈是人们从数据中获得的最直观的洞察。虽然在可视化表示数据方面存在维度限制，但绘图迄今为止是用于数据可视化最常用的方法之一。

```julia
julia> using Plots
julia> x = 1:10; y = rand(10); z = rand(10);
julia> plot(x, [y, z])
```
