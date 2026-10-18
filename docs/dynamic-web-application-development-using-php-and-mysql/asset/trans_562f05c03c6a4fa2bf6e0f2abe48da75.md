
我们将从一个简单但不够灵活的 DTD 开始，它仅处理资格。该 DTD 与我们的天气预报 DTD 非常相似：

```
<!ELEMENT qualification (certificate, diploma, degree)>
<!ELEMENT certificate (#PCDATA)>
<!ELEMENT diploma (#PCDATA)>
<!ELEMENT degree (#PCDATA)>
```

这里的问题在于，资格的不可预测性不如天气预报的结构（尽管也许比天气本身更可预测！）。目前的 DTD 假设每个候选人都会拥有证书、文凭和学位。这对于表示不具备全部三项的候选人来说是不合适的。幸运的是，DTD 语法包含许多运算符符号，可以提供我们指定实际需求所需的灵活性。

## DTD 运算符符号

我们可以通过使用竖线运算符 (|) 来解决当前必须要求全部三个资格的限制，在 DTD 语法中它表示“或”。在此版本的 DTD 第一行中，候选人可能在其 XML 文档中出现这些元素中的任意一个（证书、文凭或学位）。

```
<!ELEMENT qualification (certificate | diploma | degree) >
```

这是一些改进，但另一方面，每个候选人现在只能拥有这些资格中的任意一个，而不能多于一个。我们可以通过将 qualification 元素嵌套在另一个可能出现多次的元素（‘qualifications’）内部来解决这个问题。星号运算符 (*) 用于指定元素可以出现零次或多次，如本例所示，其中 ‘qualifications’ 元素由零个或多个 ‘qualification’ 元素组成：

```
<!ELEMENT qualifications (qualification*)>
```

这好多了。现在我们可以拥有任意数量的资格。然而，这仍然可能不理想，因为 qualification 元素可能出现零次，意味着候选人没有任何资格。为了确保文档中至少包含一个资格，我们可以使用 ‘+’ 运算符，它表示“一个或多个”，而不是 ‘*’ 运算符。在此版本中，必须有一个或多个资格。

```
<!ELEMENT qualifications (qualification+)>
```

另一个有用的规范是使元素可选，使其可以出现零次或一次（但不超过一次）。用于表示可选元素的运算符是问号。也许我们还关心候选人是否具有某种更高资格，但不需要知道他们是否拥有多个。我们可以添加一个 ‘higher qualification’ 元素，但使其可选：

```
<!ELEMENT qualifications (qualification+, higher-qualification?)>
```

从这些示例中我们可以看出，我们需要仔细设计 DTD 规范以匹配我们的需求。表 5.1 总结了我们为指定 DTD 中元素的特征而引入的各种运算符符号。

## 表 5.1 DTD 中使用的运算符符号

| 运算符符号 | 含义 |
|---|---|
| \| | 或 |
| * | 零个或多个 |
| + | 一个或多个 |
| ? | 可选（零个或一个） |

## 空元素

我们可以选择使元素专门为空，这意味着有效的 XML 文档不能为此类标签包含主体。我们已经看到，具有内容主体的标签使用 #PCDATA 类型指定。相比之下，空元素使用 EMPTY 定义。例如，‘higher-qualification’ 元素可能被声明为空：

```
<!ELEMENT higher-qualification EMPTY>
```

尽管可以拥有既没有属性的空元素，也许可作为文档中的某种“开关”来简单指示某事物是否存在或不存在，但大多数空标签确实包含属性。例如，‘higher-qualification’ 元素可能包含一个包含资格类型的属性。我们稍后将看到如何在 DTD 中包含属性。

以下示例（‘qualifications.dtd’）是一个纯粹由元素声明（无属性）组成的 DTD，其中包含我们迄今为止介绍的语法的示例。相比之前的示例，添加了一些额外的元素（year、institution 和 name）。

```
<!ELEMENT qualifications (qualification+, higher-qualification?, institution+)>
<!ELEMENT qualification (year, (certificate | diploma | degree)) >
<!ELEMENT higher-qualification EMPTY>
<!ELEMENT year (#PCDATA)>
<!ELEMENT certificate (#PCDATA)>
<!ELEMENT diploma (#PCDATA)>
<!ELEMENT degree (#PCDATA)>
<!ELEMENT institution (name)>
<!ELEMENT name (#PCDATA)>
```

在示例 DTD 中，第一行表示 ‘qualifications’（根）元素包含一个或多个 ‘qualification’ 类型的元素、一个可选的 ‘higher-qualification’ 以及一个或多个 ‘institution’ 元素，按此顺序。

第二行表示每个 ‘qualification’ 元素首先包含一个 ‘year’ 元素，然后是 ‘certificate’、‘diploma’ 或 ‘degree’ 元素中的一个。‘certificate’、‘diploma’ 和 ‘degree’ 元素仅包含字符数据。‘institution’ 元素包含一个 ‘name’ 元素。

DTD 越复杂，其有效 XML 文档的结构就越灵活。具有可选元素和可多次出现的元素的 DTD，可以有许多结构变体供有效 XML 使用。下一个示例是此 DTD 的有效 XML 文档。该文档包含两个 'qualification' 元素和两个 'institution' 元素，以及一个（空）'higher-qualification' 元素。

```
<?xml version='1.0'?>
<!-- File Example5-8.xml -->
<!DOCTYPE qualifications SYSTEM "qualifications.dtd">
<qualifications>
    <qualification>
        <year>2001</year>
        <diploma>Electronic Engineering</diploma>
    </qualification>
    <qualification>
        <year>2005</year>
        <degree>Computer Science</degree>
    </qualification>
    <higher-qualification/>
    <institution>
        <name>Oxford University</name>
    </institution>
    <institution>
        <name>MIT</name>
    </institution>
</qualifications>
```

下一个 XML 文档对 'qualifications.dtd' 也是有效的。请注意它要短得多，仅包含一个 'qualification' 和一个 'institution'，并且没有 'higher-qualification'。

```
<?xml version='1.0'?>
<!-- File Example5-9.xml -->
<!DOCTYPE qualifications SYSTEM "qualifications.dtd">
<qualifications>
    <qualification>
        <year>1999</year>
        <certificate>Baking</certificate>
    </qualification>
    <institution>
        <name>Springfield College</name>
    </institution>
</qualifications>
```

## DTD 中的属性声明

到目前为止，我们验证过的 XML 示例仅使用元素，但有时属性可以完成元素无法完成的事情。一旦我们开始根据 DTD 验证 XML，就会变得非常清楚，因为 DTD 可以提供有关属性的一些非常有用的数据和元数据。属性可以与 DTD 结合使用以：

- 定义默认值
- 定义一组有效值

## 其他属性类型

并非所有属性都是简单的字符数据（CDATA）。未声明为 CDATA 的属性可以包括具有默认值、枚举类型以及 NMTOKEN 类型的属性。

默认值在属性名后用引号声明。在此默认值示例中，‘qualification’ 元素具有 ‘years-of-study’ 属性，其默认值为 ‘3’：

```
<!ATTLIST qualification years-of-study "3">
```

使用枚举类型时，属性在使用于 XML 文档中时必须具有一组指定值中的一个。可能的值由竖线分隔（即‘或’字符）：

```
(value1|value2|..)
```

在此枚举类型示例中，‘is-university’ 属性只能是 ‘true’ 或 ‘false’。这里使用了 ‘false’ 的默认值，尽管提供默认值并非必需。

```
<!ATTLIST institution is-university (true | false) "false">
```

当提供默认值时，定义 REQUIRED 或 IMPLIED 就不相关了，否则就相关。可以为枚举类型提供任意数量的可能值。这里，使用一周中各天的名称作为 ‘day-name’ 属性：

```
<!ATTLIST calendar day-name (Monday | Tuesday | Wednesday | Thursday |
Friday | Saturday | Sunday) #REQUIRED>
```

由于未提供默认值，因此该属性已被标记为 required。

NMTOKEN 属性类型表示‘名称标记’。如果您使用此类型而不是 CDATA，它将限制属性可以包含的字符集为字母、数字、句点、连字符、下划线和冒号：

以下 DTD（‘qualifications2.dtd’）基于我们之前查看的 DTD，描述资格和机构，但已添加了多个属性：

```
<!ELEMENT qualifications (qualification+, higher-qualification?, institution+)*>
<!ELEMENT qualification (year, (certificate | diploma | degree) ) >
<!ATTLIST qualification level CDATA #REQUIRED
          internationally-recognised CDATA #IMPLIED
          years-of-study CDATA "3">
<!ELEMENT higher-qualification EMPTY>
<!ATTLIST higher-qualification type CDATA #REQUIRED>
<!ELEMENT year (#PCDATA)>
<!ELEMENT certificate (#PCDATA)>
<!ELEMENT diploma (#PCDATA)>
<!ELEMENT degree (#PCDATA)>
<!ATTLIST degree type CDATA #REQUIRED>
<!ELEMENT institution (name)>
<!ATTLIST institution is-university (true | false) "false">
<!ELEMENT name (#PCDATA)>
```
