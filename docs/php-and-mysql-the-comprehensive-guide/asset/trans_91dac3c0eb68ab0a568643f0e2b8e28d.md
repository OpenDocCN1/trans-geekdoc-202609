

$start = $end;
}

$pdf->Output('output.pdf', 'I');

## 列表 31.4 PDF 中的饼图 ("tcpdf_draw_diagram.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_855_0.png)

## 图 31.4 饼图

### 31.2.5 编写 HTML

TCPDF 在处理 HTML 方面的优势（您在上一节中已看到）也是 HTML2PDF 使用此 PDF 库作为基础的原因。

TCPDF 本身具有编写 HTML 的方法。然而，HTML2PDF 更加方便且功能更全面。为此，只需导入 HTML2PDF 库并实例化 Html2Pdf 类的对象：

```
require __DIR__.'./vendor/autoload.php';
use Spipu\Html2Pdf\Html2Pdf;
$html2pdf = new Html2Pdf();
```

其余所有工作随后由 writeHTML(HTML) 方法处理。它将包含 HTML 代码的字符串作为中心参数。这甚至可以包含 CSS 以及表格等复杂元素。

列表 31.5 和图 31.5 展示了一些可能性的概览。

```
$html2pdf = new HTML2Pdf();
$html2pdf->writeHTML('<
<style type="text/css">
table {
    border-collapse: collapse;
}
th, td {
    width: 200px;
    border: 1px solid gray;
    padding: 5px;
}
</style>
<h1>Heading</h1>
<p>An output in a paragraph with a little text and even more text. A
output in a paragraph with a little text and <strong>even</strong> more text. A
output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<hr/>
<h2 style="color: red">Heading 2</h2>
<p>An output in a paragraph with a little text and even more text. One
output in a paragraph with a little text and <strong>even</strong> more text.
more text. An output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<table>
<tr>
<th>cell heading1</th>
<th>cell heading2</th>
</tr>
<tr>
<td>Cell 1</td>
<td>Cell 2</td>
</tr>
</table>');
$html2pdf->output();
```

## **列表 31.5 带 HTML2PDF 的 HTML 输出 ("html2pdf.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_857_0.png)

## 图 31.5 HTML 输出转换为 PDF

## 31.3 FPDF

FPDF 中的第一个 "F" 代表免费。这也是该库的真正动力——因为老实说，大多数 Web 项目都是商业性质。即使是爱好网站，通常也有一两个广告横幅，因此将不属于非商业网站的定义。然而，尤其是小型网站，往往不愿意在 PDF 库上花钱。这足以成为仔细了解 FPDF 的理由。

> **注意**
> 在 www.fpdf.org，您不仅可以找到 FPDF 本身，还可以找到一份有用的手册。

### 31.3.1 基础

由于 FPDF 基于 PHP，您只需集成相应的类。操作是面向对象的，而且非常简单。您使用 FPDF 对象定义 PDF 文档，并将格式指定为参数：

```
$pdf = new FPDF("P", "pt", "A5");
```

然后继续使用该对象的方法：

```
$pdf->AddPage();
$pdf->SetFont("Helvetica", "", 48);
$pdf->Cell(20,10, "Your statement!");
```

最后，使用 `Output()` 方法输出整个内容。列表 31.6 显示了完整示例，您可以在图 31.6 中看到其输出。

```
<?php
define("FPDF_FONTPATH", "font/");
require "fpdf/fpdf.php";

$pdf=new FPDF("P", "pt", "A5");
$pdf->AddPage();
$pdf->SetFont("Helvetica", "", 48);
$pdf->Cell(20,10, "Your statement!");
$data = $pdf->Output();
header("Content-type: application/pdf");
header("Content-disposition:inline;filename=output.pdf");
print $data;
?>
```

## 列表 31.6 带 FPDF 的首个文档 ("fpdf_basics.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_858_0.png)

## 图 31.6 首个文档

> **注意**
>
> FPDF 有一些特殊功能。例如，与大多数图形程序一样，默认情况下原点位于左上角。您还可以非常灵活地选择单位。

### 31.3.2 绘图

使用 FPDF 进行绘图也非常简单。下面列表中的两行代码足以在背景中创建一个填充的矩形（参见图 31.7）。

```
$pdf->SetFillColor(51, 0, 255);
$pdf->Rect(0, 0, 421, 70, "F");
```

## 列表 31.7 绘制矩形（摘自 "fpdf_draw.php"）

同样重要的是，在第一步中设置填充颜色，它将用于后续操作。在第二步中，使用坐标、宽度和高度创建矩形。

> **注意**
> 您可以在 FPDF 网站 www.fpdf.org/en/script/index.php 上找到许多其他与绘图相关任务的有用示例和脚本。

![](img/ae7820c36e8f24c1623d26668b28e80e_859_0.png)

## 图 31.7 带 FPDF 的背景矩形

## 31.4 结论

生成 PDF 文档可能非常复杂，因为您需要手动绘制元素和对象。但基础知识很简单，在不同的库中也很相似。因此，您偏好哪个库是个人口味的问题。在基于开源的库中，我们主要使用 TCPDF，因为它与 HTML2PDF 相连，而这个选项使快速创建输出变得非常容易。

## 第 VII 部分

## 管理与安全

## 第 32 章

### 安全

据说十分之九的网站存在安全漏洞。本章帮助您尽可能避免安全漏洞。

普遍观点认为，Web 应用程序最大的不确定因素是操作系统或 Web 服务器软件（或服务器端技术）。不幸的是，这是错误的。Web 服务器和操作系统由其制造商维护，安全漏洞会被修补——有时快，有时慢。服务器技术的新版本，尤其是 PHP，也会定期发布。例如，在 PHP 8.3.0 发布后大约四周，发布了修复错误的版本 8.3.1，随后又在大约四周后发布了 PHP 8.3.2。在 2024 年 11 月底，为 PHP 8.1 到 8.3 版本发布了带有安全相关修正的新版本。管理团队肯定有责任保持警惕并保持系统安全。

然而，主要问题既不是管理员，也不是软件提供商。问题通常在于 Web 应用程序自身背后的开发团队。同样的错误总会被犯下，而且其中大部分可以毫不费力地避免。

PHP 安全主题足以填满半本百科全书，因此我们在此仅介绍最重要的要点。但请放心：如果您遵循本章中的建议，您的网站将更加安全，并且对大多数攻击免疫。然而，不存在“完全安全的网站”这种东西。请不断检查您的代码并分析 Web 服务器的日志文件，以了解您的敌人（或脚本小子）的攻击方法。

首先，值得访问开放 Web 应用安全项目（OWASP）的网页。这个项目背后是一群志愿者，他们处理 Web 安全主题。OWASP 以其定期发布（即大约每三到四年一次；参见图 32.1）的网站前 10 项安全漏洞列表而闻名。

您可以在 https://owasp.org/Top10 查看此列表。2021 年的列表（截至 2025 年初仍是最新版本，但当年晚些时候的继任者计划已经在进行中）包含以下项目：

- 1. 访问保护不足
- 2. 加密错误
- 3. 注入和跨站点脚本（XSS）
- 4. 不安全的设计
- 5. 配置不安全
- 6. 使用过时或不安全的组件
- 7. 不安全的识别和身份验证
- 8. 软件和数据完整性不足
- 9. 日志记录和监控不足
- 10. 服务器端请求伪造（SSRF）

![](img/ae7820c36e8f24c1623d26668b28e80e_864_0.png)

## 图 32.1 OWASP 十大

我们将在后面转向此列表中更有趣的要点，但列表本身已经非常有信息量。列表上的几乎所有要点主要与粗心编程有关。无论服务器被管理员保护得多么好，都有可能通过粗心编程破坏整个概念。服务器可能配置得使得外部人员没有权限。但是，如果攻击者接管了一个网站呢？Web 应用程序可能有足够的权限将服务器用于邪恶目的。所以，请小心编程，做好最坏的打算——并继续阅读！

### 32.1 用户输入

几乎所有安全漏洞都与从外部向 Web 应用程序传输信息（这会严重干扰它）有关。这可以通过 a

