

## 换行符和水平分隔线

换行符（BR）和水平分隔线（HR）是空元素的示例。HTML 中的空元素没有独立的开始标签和结束标签，而是由单个标签组成，既不要求闭合标签，也不隐含闭合标签。HTML 中空元素的一个示例是换行符，它最早出现在 HTML 2.0 规范中：

```
<BR>
```

该元素没有开始标签和结束标签，而是由单个标签组成，强制文档换行。与段落元素不同（段落元素会另起一行并在段落前留出空白），BR 元素会另起一行，但不会强制插入空行。

水平分隔线是另一个源自 HTML 2.0 的空元素示例。该标签如下所示：

```
<HR>
```

浏览器通常将水平分隔线显示为一条图形线。当然，人们可能会质疑 HR 元素究竟是结构性的，还是仅仅用于呈现。它在各种 HTML 规范中的定义经历了一个演变过程：从“文本各部分之间的分隔线”，到“用于表示主题的转换”，再到“由可视化用户代理渲染的水平分隔线”，因此两种解释都有其道理（Korpela 2002）。

## 引用和块引用

HTML 中有许多结构元素，有些比其他的更常用。虽然 CITE 和 BLOCKQUOTE 并不常用，但它们是有用的示例，展示了一些带有语义的元素；它们传达的是文本的含义以及文本与周围文档其他部分的关系，而非层级结构或呈现方式。

在文档中，较长的引文和引用通常采用与正文不同的结构。HTML 包含用于长引文的 <BLOCKQUOTE> 元素和用于引用的 <CITE> 元素。下一个示例与上一个类似，但进行了修改，加入了 <CITE> 和 <BLOCKQUOTE> 元素。您应该注意，BLOCKQUOTE 元素不应直接包含文本，而应包含段落或标题等结构元素，文本位于这些元素内部。这里我们使用一个段落元素。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
<HEAD>
<TITLE>Versions of HTML</TITLE>
</HEAD>
<BODY>
<!-- File: example3-2.htm -->
<H1>Versions of HTML</H1>
<H2>HTML 1.0</H2>
<P>The first version of HTML dates from 1991, and was developed by Tim
Berners-Lee. It was very different from the HTML we know today.
```

在特定浏览器中，不应仅仅为了获得那种呈现效果而使用它。BLOCKQUOTE 元素表示应对该元素的主体进行特殊处理，以识别出它是一个长引文。无论元素的实际内容如何，都不应将其用作实现特定格式的便捷方式。也许更明显的是，使用 CITE 元素不应仅仅被视为使文本变为斜体的一种方式。

## 惯用（短语）元素

CITE 是*惯用*或*短语*元素之一。这些元素涉及我们在书面表达中的常见用法类型。例如，我们会寻找强调文本特定部分的方法。为了支持这些惯用法，HTML 包含了一些元素，如用于强调的 EM 和用于更强强调的 STRONG。浏览器通常将 EM 文本渲染为斜体，将 STRONG 文本渲染为粗体，但与 CITE 元素一样，浏览器选择渲染这些元素的实际方式与我们如何使用标签无关。我们使用它们来表示一种表达类型，而不是为文本选择特定的外观。

## 下标和上标

SUB（下标）元素使用较小的字体，并向常规字符高度的底部对齐；SUP（上标）元素使用较小的字体，并向常规字符高度的顶部对齐。这些元素似乎介于结构性与呈现性之间的灰色地带。然而，内容的这些方面有一些重要的公认用途，例如在科学记数法或某些语言的渲染中。上标通常用于表示参考文献、脚注或商标，以及用于数学公式；而下标用于化学公式。HTML 4 规范中包含了这两个关于上标和下标的实用示例：

```
H<SUB>2</SUB>O  to represent H₂O (the chemical symbol for water)
E = mc<SUP>2</SUP>  to represent E = mc² (Einstein's formula for relativity)
```

由于这些特定的应用，只要 <SUB> 和 <SUP> 元素用于这些普遍接受的场景而非仅仅为了追求效果，就可以将它们的用法视为结构性的。

## 特殊字符

由于 HTML 页面使用标记语法，某些符号（尤其是 < 和 >）对于处理它们的应用程序（如浏览器）具有特殊含义。HTML

### 表 3.1 HTML 字符引用

| HTML 字符引用 | 等效字符 | 含义 |
|---|---|---|
| `&lt;` | `<` | 小于 |
| `&gt;` | `>` | 大于 |
| `&quot;` | `"` | 引号 |
| `&amp;` | `&` | 与号 |
| `&nbsp;` | （一个空格） | 不间断空格 |
| `&reg;` | ® | 注册商标 |
| `&copy;` | © | 版权 |

字符引用是数字或符号名称，可在 HTML 文档中用来代替字面字符。它们适用于表示字符集中常规数字和字母范围之外的特殊字符，或那些在标记语言中具有其他含义、因而可能导致浏览器出现处理问题的字符。所有 HTML 字符引用都以 & 符号开头，以分号结尾。表 3.1 显示了一些 HTML 字符引用的示例。

## 3.6 列表

列表是组织 HTML 文档中某些类型内容的适当方式。列表可以以易于阅读的布局呈现简短、相关的信息项，并且可以嵌套（即列表中的列表）以生成目录、索引或文档大纲等结构。HTML 中有三种类型的列表：

- 无序列表
- 有序列表
- 定义列表

### 无序列表

无序列表是一种具有列表结构、但没有编号或字母来表示有意义顺序的列表。在其他语境中，这种类型的列表称为项目符号列表。浏览器通常会在列表中的每个项目前显示项目符号前缀。无序列表元素的标签名是 UL，它可以包含任意数量的嵌套 LI（列表项）元素：

```
<UL>
    <LI> a list item </LI>
    <LI> another list item </LI>
    ...
</UL>
```

### 有序列表

在有序列表中，列表项带有编号或字母标记。这对于具有有意义顺序的列表非常有用，例如说明、章节、食谱或联赛排名表。有序列表的标签名是 OL，同样使用 LI 作为嵌套的列表项元素：

```
<OL>
    <LI> the first list item </LI>
    <LI> the second list item </LI>
    ...
</OL>
```

### 嵌套有序列表和无序列表

列表可以根据内容需要嵌套并组合在一起。但在这样做时，有一件重要的事情需要牢记：任何嵌套在另一个列表中的列表都必须放在自己的列表项（LI）元素中，使用如下结构：

```
<UL>
    <LI> an item in the main list</LI>
    <LI> Here comes a nested list...
        <OL>
            <LI> an item in the nested list</LI>
            <LI> another item in the nested list</LI>
            ...
        </OL>
    </LI>
    <LI> another item in the main list</LI>
    ...
</UL>
```

在这个来自家庭保险系统领域的示例中，我们同时使用了有序列表和无序列表：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
    <HEAD>
        <TITLE> Making a Claim</TITLE>
    </HEAD>
    <BODY>
        <!-- File: example3-3.htm -->
        <H1>Useful Tips</H1>
        <UL>
            <LI> Making a Claim
            <OL>
                <LI>Find as much documentation as you can (photos, receipts, etc.)
                </LI>
                <LI> Fill in the on-line claim form</LI>
                <LI> Don't do anything until an assessor has contacted you</LI>
            </OL>
            </LI>
            <LI>Changing your policy
            <OL>
                <LI> Log in to your user account </LI>
                <LI> Select 'update policy details' from the list of options </LI>
                <LI> Follow the on-screen instructions to make the required changes
                </LI>
            </OL>
            </LI>
        </UL>
    </BODY>
</HTML>
```

图 3.3 显示了该页面在 Opera 9 中的外观。您会注意到，主无序列表使用圆形项目符号，嵌套的有序列表使用阿拉伯数字标记。这是浏览器的行为，并非由我们的列表元素所指定。

