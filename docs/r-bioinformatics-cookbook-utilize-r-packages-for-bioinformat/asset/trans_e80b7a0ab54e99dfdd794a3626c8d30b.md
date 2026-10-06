

# 准备工作

我们需要一个由 `rbioinfcookbook` 包提供的示例 R Markdown 文档，因此如果你还没有安装它们，请安装 `fs` 包和 `ggplot2` 包。此外，你还需要按照章节开头的说明安装 Quarto。请确保你也安装了 TinyTeX，这是 Quarto 所必需的，这在章节开头也有讨论过。

# 如何操作...

我们可以按照以下步骤准备一个标记过的文档以渲染为各种格式：

- 保存可访问的示例文件：

```
qmd_path <- fs::path_package("extdata", "mtcars.qmd",
package=rbioinfcookbook)
file.copy(qmd_path, 'somewhere/on/your/system/mtcars.qmd')

bib_path <- fs::path_package("extdata", "mtcars.bib",
package=rbioinfcookbook)
file.copy(bib_path, 'somewhere/on/your/system/mtcars.bib')
```

- 在你的编辑器中，为 HTML 添加一个 YAML 头部：

```yaml
---
title: "mtcars Analysis"
subtitle: "an analysis in many formats"
author: "anrwizard@email.com"
date-modified: "%format(Sys.time(), '%d %B, %Y')"
email-obfuscation: javascript
execute:
  echo: true
  warning: false
format:
  html:
    theme: cyborg
    toc: true
    toc-location: left
    html-math-method: katex
    css: styles.css
    number-sections: true
    cap-location: top
    code-fold: true
    code-line-numbers: true
    citations-hover: false
---
```

- 3. 在命令行上运行它：

```
quarto render mtcars.qmd --to html
```

- 4. 获取引用样式语言 (CSL) 文件来确定参考文献的格式化：

```
csl_path <- fs::path_package("extdata", "bioinformatics.csl",
package="rbioinfcookbook")
file.copy(csl_path, 'somewhere/on/your/system/bioinformatics.csl')
```

- 5. 扩展 YAML 以包含一个 PDF 块；注意——添加现有的 HTML 代码：

```yaml
pdf:
  pdf-engine: xelatex
  papersize: A4
  class: report
  toc: true
  toc-title: "Workflow"
lof: true
  mainfont: Arial
  monofont: Courier
  fontsize: "24"
  colorlinks: true
  cap-location: margin
  csl: bioinformatics.csl
```

- 6. 渲染文档：

```
quarto render mtcars.qmd --to html,pdf
```

- 7. 获取一个 Microsoft Word .docx 文件作为 Microsoft Word 文档的样式模板：

```
docx <- fs::path_package("extdata", "custom-reference-doc.docx",
package="rbioinfcookbook")
file.copy(docx_path, 'somewhere/on/your/system/custom-reference-doc.docx')
```

- 8. 为 .docx 输出扩展 YAML：

```yaml
docx:
  reference-doc: custom-reference-doc.docx
  fig-align: center
  fig-width: 20
  number-sections: true
  citeproc: true
```

- 9. 执行最终渲染：

```
quarto render mtcars.qmd --to html,pdf,docx
```

这将为我们从输入生成 html、pdf 和 docx 输出文件。

# 工作原理...

虽然这个配方很长，但它相对简单；我们所做的只是设置全局格式并从支持包中提取一些预备的文件来协助。在第 1 步中，我们使用了机器上某个可访问的 `mtcars.qmd` 文件。我们对参考文献文件 .bib 执行了同样的操作，它设置了参考文献的路径。HTML 特有的选项应用在 `format HTML` 下。在这里，我们使用值从内置主题之一（cyborg）中设置主题。这是一个独特的特性，当我们开启目录并通过 `toc-location` 将其设置为左侧时它会被应用，还有渲染数学公式的选项，并提供了一个可选的 CSS 文件用于自定义样式。尝试这些值以了解它们的作用。在第 3 步中，我们转到命令行渲染文档；结果应该是 `mtcars.html` 和其他文件。

在第 4 步中，我们开始 PDF 格式化文档，首先提取描述参考文献的 `bioinformatics.csl` 文件并将其放在你的某处。在第 5 步中，我们设置了 PDF 输出选项，选择了 `pdf-engine`、某些文档类型、更多内容选项以及某些特定字体。当你浏览文档时，这些应该是清晰的。请注意 `csl` 键已添加到 YAML 中，其缩进应与 HTML 块匹配。在第 6 步中，我们同时渲染这两种格式。比较输出以观察特定格式的选项如何影响它们。

对于 Word 文档，样式是由 .docx 文件定义的。同样，支持包中有一个，但你可以通过进入 Word 并设置你喜欢的样式，然后将文件保存为模板来创建自己的。在第 7 步中，我们复制了示例文档。在第 8 步中，我们设置了一些选项。最重要的是 `reference-doc`，它获取你的样式引用的路径。同样重要的是 `citeproc` 键，它开启了参考文献格式化器。最后，在第 9 步中，我们渲染所有格式。

