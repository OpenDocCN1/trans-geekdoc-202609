

SQL:2003 标准引入了 is document 谓词，用于测试 XML 表达式是否为文档。基本语法是：

```
xmlexpression is [ not ] document
```

虽然该谓词的语法自 SQL:2003 以来保持不变，但由于 SQL/XML:2006 与 XQuery 数据模型重新对齐，其含义发生了一定程度的转变。新增了三个谓词：is content、xmlexists 和 is valid。is content 谓词用于测试 XML 表达式是否为合法的 XML 内容，语法如下：

```
xmlexpression is [ not ] content
```

若要测试表达式是否包含有效的 XML，可以使用 xmlexists 谓词。语法（稍作简化）如下：

```
xmlexists ( XQuery-expression
    [ passing value-expression
    [ as identifier ] { by ref | by value } ] [...] )
```

如果 XQuery 求值结果为 null（可能作为参数从 SQL 传递），则谓词结果为未知。对于非 null 值，如果 XQuery 求值返回空序列，则谓词值为 false；否则结果为 true。以下示例展示了如何在 select 语句中使用 xmlexists，以检索给定城市中客户的 "id" 值，客户详细信息存储在 xml 类型的列中。

```
select c.custid from customer as c
    where xmlexists ( ' $d/*:customerinfo/*:addr [ *:city = "Salt Lake City" ] '
    passing info as "d" )
```

is valid 谓词用于检查 XML 值是否符合给定的 XML 架构。有效性评估的细节较为复杂，此处不再赘述。简化的语法是：

```
xml-value-expression is [ not ] valid
    [ identity-constraint-option ]
    [ according to xmlschema { uri | registered-name } ]
    [ valid-element-clause ]
```

xml-value-expression 将根据所选命名空间标识的架构进行检查。如果未指定，则每个元素将根据其命名空间关联的架构进行验证。如果指定了，架构可以通过 URI 或其注册名称来标识。可选的 identity-constraint-option 和 valid-element-clause 参数允许对架构检查应如何执行进行更详细的指定。

SQL:2003 标准引入了多个内置 XML 运算符。其中一个运算符 xmlroot 可用于修改 XML 表达式的版本和 standalone 属性，但该运算符已在 SQL/XML:2006 中移除，因此此处不再介绍。

我们将首先介绍的两个 SQL/XML 操作是 xmlparse 和 xmlserialize，它们在 XML 的结构化表示和字符串表示之间进行双向转换。xmlparse 操作接收一个 SQL 字符串表达式并生成等效的 XML 结构。一个参数定义该字符串表达式是预期表示文档还是内容。自 SQL:2003 以来，基本语法一直保持一致。

```
xmlparse ( { document | content } stringexpression
[ { preserve | strip } whitespace ] )
```

该操作的结果可以赋值给 xml 类型的变量，或存储在 xml 列中。xmlparse 处理空白字符的精确方式受详细规则约束，此处不再讨论。

xmlserialize 操作执行 xmlparse 的逆操作，生成给定 XML 表达式的字符串版本。SQL 标准不强制规定生成字符串的精确格式，但要求对 xmlserialize 生成的字符串再次执行 xmlparse 应能还原原始 XML 表达式。换句话说，给定名为 myXmlData 的 XML 文档，以下结构：

```
xmlparse ( document ( xmlserialize ( document myXmlData as varchar ( max ) ) ) )
```

应生成与 myXmlData 相等的结果。xmlserialize 的原始 SQL:2003 语法在 SQL/XML:2006 中进行了扩展。

```
xmlserialize ( { document | content } xmlexpression as SQL datatype
[ version string ]
[ including xmldeclaration | excluding xmldeclaration ] )
```

结果的 SQL 数据类型可以是任何 SQL 字符串类型（例如 char、varchar），但序列化后的 XML 通常很长，因此字符大对象 (clob) 类型可能是常见的选择。可选地，including xmldeclaration 会在结果前加上 XML 声明 `<?xml version="1.0" encoding="UTF-8"?>`；默认值为 excluding xmldeclaration。XML 版本也可以单独指定；目前仅限于 "1.0"。

SQL:2003 中引入的 xmlconcat 操作在 SQL/XML:2006 中得到了保留。它只是连接一组 XML 表达式，生成一个新的 XML 表达式。

```
xmlconcat ( xmlexpression [, ...] [ returning { content | sequence } ] )
```

可选的 returning 子句是在 SQL/XML:2006 中添加的。如果省略，返回 content 还是 sequence 是隐式的，取决于具体实现。

SQL:2003 标准定义了多个“发布”函数，用于从 SQL 表达式生成 XML 表达式。这些函数在 SQL/XML:2006 中得到了扩展，并新增了函数。此处，我们仅介绍 SQL/XML:2006 中的函数定义。

**xmlelement** 函数用于从给定参数集创建 XML 元素。请回顾，XML 元素的基本形式为：

```
<tagname optionalAttributes> optionalElementContent </tagname>
```

例如，表示客户的元素可能如下所示：

```
<cust custid = "1234"> Widgets Inc </cust>
```

如有需要，可以通过为 tagname 添加命名空间前缀来进一步限定，此时还必须指定命名空间 URI。**xmlelement** 函数根据提供的参数构造单个 XML 元素，并将其作为 **xml** 值返回。此处显示的是字符串的基本语法。还有一个用于二进制字符串的变体，此处不予考虑。

内嵌的 xmlnamespaces 和 xmlattributes 函数可在给定元素的上下文中选用，用于向元素添加所需的命名空间声明或属性。元素内容由一个可选的表达式列表定义，因此可以创建空元素。同样可选的是 returning 子句，我们之前已经见过。

```
xmlelement ( name xmlelementname
 [ , xmlnamespaces (namespace-declaration-item [...] ) ]
 [ , xmlattributes ( attributevalue [as attributename ] [,...] )
 [ , elementcontent [...
 [ option { null on null | empty on null | absent on null | nil on null | nil on no content } ]
 [ returning { content | sequence } ] )
```

content 选项需要进一步说明。在 SQL 中，缺失的可选值会被明确标记为 **null**。这不是 XML 认识的值，尽管 null 对于 SQL xml 数据类型是合法的。根据所需结果，缺失的值可以在 XML 中通过简单省略相关元素，或包含不含值的元素开始/结束标签来指示。如果需要等效于 null 的显式指示器，进一步的选项是“XML Schema For Instances”命名空间中规定的“nil”机制。该命名空间通常通过如下声明引入：

```
xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
```

按照惯例使用 xsi 前缀，但也可以替换为其他前缀。定义此前缀后，XMLSchema-instance 中定义的 nil 属性可以设置为 True。

```
<myElement xsi:nil = "true"></myElement>
```

以这种方式标记的元素可能没有任何元素内容，但仍可携带其他属性。SQL:2003 标准承认了 xsi:nil 选项，但未规定如何在与 **xmlelement** 等操作结合使用时指定它。SQL/XML:2006 对这些选择提供了严格控制，如表 16.4 所总结。

### 表 16.4 处理 null 和 nil 的选项。

| 选项 | 对 SQL null 应用函数时的结果 |
|---|---|
| null on null | null SQL 值导致 null XML 值 |
| empty on null | null SQL 值导致空 XML 元素 |
| absent on null | null SQL 值导致没有元素（即空序列） |
| nil on null | null SQL 值导致标记为 xsi:nil = "true" 的 XML 元素 |
| nil on no content | 正在创建且没有子项的元素标记为 xsi:nil = "true" |

作为 **xmlelement** 使用的一个简单示例，请考虑一个纯关系型的 Customers 表（其中不含 XML）。我们可以以下述方式生成包含关系数据和表示所选客户信息的 XML 的混合结果表：

```
select c.id,
xmlelement( name "cust", xmlattributes (c.id as "custid"), custName) as Xcust
from Customers as c where custid = 1234
```

这将生成如下结果：

| id | Xcust |
|---|---|
| 1234 | <cust custid = "1234"> Widgets Inc </cust> |

其中 Xcust 列包含的数据为 xml 类型。对 xmlelement 的调用可以嵌套，从而在元素中创建元素，产生 XML 特有的层次结构。

xmlforest 函数是将 xmlconcat 应用于 xmlelement 结果序列的一种便捷方式：它从表达式列表生成一组元素。元素可以显式或隐式命名。与 xmlelement 类似，对 xmlforest 的调用也可以嵌套。基本语法如下：

```
xmlforest ( [ xmlnamespaces ( namespace-declaration-item , ), ]
elementvalue [ as elementname ] [,...]
[ option { null on null | empty on null | absent on null | nil on null | nil on no content } ] ]
[ returning { content | sequence } ])
```

参数的使用方式与 xmlelement 相同。例如，

```
select o.orderId,
xmlelement( name "order", xmlforest ( o.custName as "customer", o.date ) ) as Xorder
from Orders as o
where orderid > 9800
```

