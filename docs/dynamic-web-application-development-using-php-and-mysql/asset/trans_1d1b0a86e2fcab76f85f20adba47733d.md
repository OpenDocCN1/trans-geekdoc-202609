

## 4.3 样式表

仅在标签内使用内联样式，与使用标准HTML中的表现元素和属性相比，并无实际优势。虽然我们使用了不同的语法，但实际上并未将结构和内容与表现分离，也没有获得将通用样式应用于文档的任何好处。只有当样式也应用于整个文档时才有用，这样我们就可以，例如，将标准样式应用于文档中的所有H1元素，而不是逐一对每个元素进行设置。在这种情况下，内联样式适用于微调表现，但不应用来为整个文档设置样式。更广泛地应用样式是通过样式表完成的，样式表可以位于HTML页面内部，也可以作为外部文档，通过LINK元素链接到HTML页面。首先，我们看看如何在HTML页面中包含样式表。

### 内部样式表

内部样式表是包含在HTML文档的HEAD元素中，通过STYLE元素定义的样式表。此类样式表仅应用于该文档。对于CSS，STYLE元素的“type”属性值设为“text/css”，这与使用META元素进行内联样式时相同。

```
<STYLE type="text/css">
...styles defined here
</STYLE>
```

在STYLE元素中定义样式的语法与内联样式类似，不同之处在于我们还需要指定样式应用于哪些元素类型。样式表的每个组件由三部分组成：

- HTML元素类型的名称
- 该元素的表现属性名称
- 要应用的属性值。

属性和它的值出现在花括号内（与内联样式一样，用冒号分隔）：

```
element {property: value}
```

例如，如果我们想将所有H1（主标题）元素改为蓝色样式，可以添加以下样式元素：

```
<STYLE type="text/css">
 h1 {color: blue}
</STYLE>
```

请注意，在CSS中我们将使用小写字母作为元素名称，因为之后会将其应用于XHTML页面。在XHTML中，元素名称必须使用小写。对于不区分大小写的HTML，样式表中使用的大小写无关紧要。

我们的内联样式示例与这种样式之间的区别在于，后者将应用于正在格式化的页面中的所有“h1”元素。有时我们会想对特定元素类型应用多种样式，在这种情况下，我们可以将不同的样式分隔开

### 图4.2（续）

![](img/b2471264f405d17994ef173e4b9cec92_116_0.png)

### 图4.3 由 a) Mozilla Firefox 2、b) Opera 9 和 c) Internet Explorer 7 显示的 Times New Roman、Arial 和 Courier 字体

![](img/b2471264f405d17994ef173e4b9cec92_116_1.png)

![](img/b2471264f405d17994ef173e4b9cec92_116_2.png)

```
<P>You may not realise just how much the stuff you have would cost to replace.
If the burglars move in while you're on holiday, could you afford to replace the TV, the stereo, the chairs, the cupboards, the crockery, etc?
</P>
<P>Not only that, our contents cover means that if you have your bike stolen, drop the vase your mother-in-law gave you as a wedding present, lose your camera, leave your glasses on the train or have your mobile phone stolen, you'll be fully compensated.
</P>
</BODY>
</HTML>
```

图4.4显示了该页面在 Internet Explorer 7 中的外观。

### 设置字体大小

字体大小可以使用多种不同的度量单位来设置，包括英寸、厘米、毫米、磅或派卡等绝对度量单位。然而，在不同浏览器环境中，将大小设置为特定度量值并不十分灵活，只应应用于目标客户端设备已知的专门应用程序中。大多数Web应用程序并非如此，因此更好的方法是使用相对的方法来调整文本大小。即使在这里，也不止一种选择：我们可以使用百分比度量（%）、像素度量（px）、字体的“x高度”（x）或“em”

### 图4.4 应用于多个标题和段落的样式

![](img/b2471264f405d17994ef173e4b9cec92_118_0.png)

要将此样式表应用于HTML页面，我们需要在页面的HEAD元素中添加相应的LINK元素。此LINK示例指定了“webhomecover.css”文件：

```
<LINK href="webhomecover.css" rel="stylesheet" type="text/css">
```

该示例假定CSS文件与HTML文件位于同一文件夹中（无论是在本地还是在Web服务器上）。否则，可以根据情况将“href”属性的值写成包含目录路径或完整URL。

下面是我们之前的示例HTML页面，但使用的是外部样式表而不是内部样式表。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
<HEAD>
    <LINK href="webhomecover.css" rel="stylesheet" type="text/css">
    <TITLE>Our Insurance Cover</TITLE>
</HEAD>
<BODY>
    <!-- File: example4-3.htm -->
    <H1>We provide the following types of insurance</H1>
    <H2>Buildings Cover</H2>
    <P>You may think you're "safe as houses" but you'd be surprised how many things can damage the building you live in. Fires, earthquakes, subsidence, runaway trucks, cricket balls through windows or the occasional meteor. Best to be covered!
    </P>
    <H2>Contents Cover</H2>
    <P>You may not realise just how much the stuff you have would cost to replace. If the burglars move in while you're on holiday, could you afford to replace the TV, the stereo, the chairs, the cupboards, the crockery, etc?
    </P>
    <P>Not only that, our contents cover means that if you have your bike stolen, drop the vase your mother-in-law gave you as a wedding present, lose your camera, leave your glasses on the train or have your mobile phone stolen, you'll be fully compensated.
    </P>
</BODY>
</HTML>
```

一旦我们有了独立的样式表，就可以在多个HTML页面中使用它。这里，我们将同一个样式表应用于另一个页面：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
<HEAD>
    <LINK href="webhomecover.css" rel="stylesheet" type="text/css">
    <TITLE>Our Promise to You</TITLE>
</HEAD>
<BODY>
```

```
<!-- File: example4-4.htm -->
<H1>Our Promise to You</H1>
<H2>No Unreasonable Exclusions</H2>
<P>
Many insurance companies include many exclusions in their policies, making it difficult to claim for events such as 'acts of God', terrorism or subsidence. We have the smallest set of exclusions of any fictional insurance company.
</P>
<H2>Rapid Response</H2>
<P>
If you make a claim, we promise to respond to you within 24 hours, either by settling immediately or putting you in contact with one of our insurance assessors.
</P>
<H2>Low, Low, Rates</H2>
<P>
We constantly monitor our prices against our competitors and guarantee that we provide the best-value insurance that you can't actually buy.
</P>
</BODY>
</HTML>
```

图4.5显示了与图4.4中相同的样式已被应用。

### 图4.5 在另一个页面中重用相同的样式

![](img/b2471264f405d17994ef173e4b9cec92_121_0.png)

## 4.4 使用“class”和“id”属性应用样式

到目前为止，我们已经了解了如何将样式应用于特定的HTML元素，如H1、H2和P。在许多情况下这很有用，但有时我们希望：

- 将同一样式应用于多种类型的HTML元素。
- 将样式应用于特定HTML元素的部分（但不是全部）实例。
- 将样式应用于元素的某个特定实例。

为此，我们需要某种方式来标记HTML的各个部分，以便将样式应用于通过这些标签识别的元素。我们可以通过两种方式做到这一点：

- 我们可以使用“class”属性。这使我们能够将多个元素分组为属于同一个类。然后我们可以将样式应用于该类的所有成员。
- 我们可以使用“id”属性。这可以用于为元素提供唯一的id。该id可用于应用文档中其他任何地方都不使用的样式。

### 使用“class”属性

class属性可以应用于许多元素。此外，一个给定的元素可以属于多个类。作为在一系列不同元素中应用样式的一种方式，class属性非常有用。例如，假设我们希望主标题（H1）和副标题（H2）都居中。当然，我们可以在样式表中分别将相同的样式应用于H1和H2元素。然而，更灵活且更易于维护的方法是使用class属性。第一步是将H1和H2元素都标识为属于同一个类。类的名称由页面作者决定。在下一个示例中，我们将类名“heading”应用于H1和H2元素的所有实例。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
<HEAD>
    <LINK href="webhomecover.css" rel="stylesheet" type="text/css">
    <TITLE>Our Insurance Cover</TITLE>
</HEAD>
<BODY>
    <!-- File: example4-5.htm -->
    <H1 class="heading">We provide the following types of insurance</H1>
    <H2 class="heading">Buildings Cover</H2>
    <P>You may think you're "safe as houses" but you'd be surprised how many
things can damage the building you live in. Fires, earthquakes, subsidence, runaway trucks, cricket balls through windows or the occasional meteor. Best to be
covered!
    </P>
    <H2 class="heading">Contents Cover</H2>
    <P>You may not realise just how much the stuff you have would cost to replace.
If the burglars move in while you're on holiday, could you afford to replace the
TV, the stereo, the chairs, the cupboards, the crockery, etc?
    </P>
```

