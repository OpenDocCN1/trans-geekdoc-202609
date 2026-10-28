
在日期和时间类型中，DATE类型用于在不需要存储时间时存储日期，TIME类型用于在不需要存储日期时存储时间，DATETIME类型用于同时存储日期和时间。MySQL还提供了TIMESTAMP类型，但此处不加以介绍，因为它无法存储2038年之后的日期。

在继续之前，你应该知道本章只介绍一些最常见的MySQL数据类型。然而，MySQL还提供了许多其他数据类型。例如，MySQL提供了用于存储超大和超小浮点数、二进制大对象（BLOB）、枚举和集合的数据类型。因此，如果此图中列出的数据类型不能满足你的需求，请参阅在线MySQL参考手册以获取更多信息。你可以先搜索“数据类型”或“数据类型概述”。

## 如何创建表

图17-3展示了CREATE TABLE语句的简化语法。由于该语句及本章介绍的其他语句语法较为复杂，本章不展示完整的语法图，而是展示简化的示意图，以说明常用子句的用法。要查看任何语句的完整语法，你可以在线查阅MySQL参考手册中的相应语句。

默认情况下，CREATE TABLE语句会在当前数据库中创建新表。因此，在执行该语句之前，必须确保已选择正确的数据库。

CREATE TABLE语句最简单的形式是：新表名后紧跟各列的名称和数据类型。此图中的第一个示例对此进行了说明。但在大多数情况下，你会为每一列编写一个或多个属性，如第二个示例所示。例如，若要表明某列不接受NULL值，可以编写NOT NULL属性。如果省略该属性，则该列将允许NULL值。

若要表明列中的每个值都必须唯一，可以编写UNIQUE属性。由于两个NULL值不被视为相同，因此唯一列可以包含NULL值。不过，通常使用NOT NULL和UNIQUE属性来定义一个既不能包含NULL值、又要求列中每个值都必须唯一的列。

若要为列指定默认值，可以使用DEFAULT属性。当向数据库添加行时，如果未指定其他值，则使用该默认值。指定的默认值必须与列的数据类型对应。例如，paymentTotal列的默认值设置为0。

在继续之前，你应该意识到，如果针对my_guitar_shop2数据库运行此图中显示的语句，这些语句将会失败。这是因为my_guitar_shop2数据库中已存在名为customers和orders的表。因此，如果你想测试这些语句，需要创建另一个数据库并针对该数据库运行它们。

### CREATE TABLE 语句的语法

```sql
CREATE TABLE [IF NOT EXISTS] tableName
(
    columnName1 dataType [columnAttributes][,
    columnName2 dataType [columnAttributes]][,
    columnName3 dataType [columnAttributes]]...
)
```

### 三个常见的列属性

| 属性 | 说明 |
|---|---|
| UNIQUE | 指定列中存储的每个值都必须唯一，但允许该列存储NULL值。 |
| NOT NULL | 表示该列不接受NULL值。如果省略，则该列可以接受NULL值。 |
| DEFAULT default_value | 为该列指定一个默认值。 |

### 不带列属性的表

```sql
CREATE TABLE customers
(
    customerID    INT,
    firstName     VARCHAR(60),
    lastName      VARCHAR(60)
);
```

### 带列属性的表

```sql
CREATE TABLE customers
(
    customerID    INT           NOT NULL     UNIQUE,
    firstName     VARCHAR(60)   NOT NULL,
    lastName      VARCHAR(60)   NOT NULL
);
```

### 另一个带列属性的表

```sql
CREATE TABLE orders
(
    orderID       INT           NOT NULL     UNIQUE,
    customerID    INT           NOT NULL,
    orderNumber   VARCHAR(50)   NOT NULL,
    orderDate     DATE          NOT NULL,
    orderTotal    DECIMAL(9,2)  NOT NULL,
    paymentTotal  DECIMAL(9,2)               DEFAULT 0
);
```

### 说明

- CREATE TABLE语句根据你指定的列定义和列属性创建表。
- 由于NOT NULL和UNIQUE属性限制了列可以存储的数据类型，因此它们被称为约束。
- 要查看CREATE TABLE语句的完整语法，你可以查阅在线MySQL参考手册。

图17-3 — 如何创建表

## 如何编写主键

无论你是否意识到，NOT NULL和UNIQUE关键字都是约束的示例。*约束*限制了列中可以存储的数据类型。例如，NOT NULL关键字防止NULL值存储在列中，而UNIQUE关键字只允许唯一值。

现在，图17-4展示了如何编写另一种称为*主键*的约束。此外，还展示了如何编写通常与主键一起使用的AUTO_INCREMENT属性。

定义主键最简单的方法是在列的数据类型后面编写PRIMARY KEY关键字，如第一个示例所示。然后，如果你希望MySQL自动生成主键值，还可以为该列编写AUTO_INCREMENT关键字。

当你将某列标识为主键时，该列的两个属性会自动更改。第一，该列被强制为NOT NULL。第二，该列被强制为每行包含唯一值。此外，系统会自动基于该列创建索引。

在第一个示例中，主键编写在列名之后，因此称为*列级主键*。不过，你也可以像第二个示例那样在表级别编写主键，此时该主键称为*表级主键*。在此图中，前两个示例的主键作用相同。因此，在何处编写主键很大程度上取决于个人偏好。

然而，表级主键确实提供了一种列级主键不具备的能力：它可以引用表中的多个列。因此，如果需要引用多个列，则必须使用表级主键。在第三个示例中，orderItems表的主键引用了orderID列和productID列。

在表级别编写主键时，必须在前一个列定义的末尾编写逗号。否则，在尝试运行该语句时会出错。

### 与主键一起使用的两个列属性

| 属性 | 说明 |
|---|---|
| `PRIMARY KEY` | 指定该列是表的主键。 |
| `AUTO_INCREMENT` | 自动为该列生成整数值。默认情况下，该值从1开始，每次递增1。 |

### 具有列级主键的表

```sql
CREATE TABLE customers (
    customerID       INT             NOT NULL    PRIMARY KEY AUTO_INCREMENT,
    emailAddress     VARCHAR(255)    NOT NULL    UNIQUE
);
```

### 具有表级主键的表

```sql
CREATE TABLE customers (
    customerID       INT             NOT NULL    AUTO_INCREMENT,
    emailAddress     VARCHAR(255)    NOT NULL    UNIQUE,

    PRIMARY KEY (customerID)
);
```

### 具有两列主键的表

```sql
CREATE TABLE orderItems (
    orderID          INT             NOT NULL,
    productID        INT             NOT NULL,
    itemPrice        DECIMAL(10,2)   NOT NULL,
    discountAmount   DECIMAL(10,2)   NOT NULL,
    quantity         INT             NOT NULL,

    PRIMARY KEY (orderID, productID)
);
```

### 说明

- *主键*要求每一行用于主键的列或列组合具有唯一值，并且不允许NULL值。
- *列级主键*作为列定义的一部分编写。编写*表级主键*时，要像编写独立的列定义那样，并在该定义中指定其列或列组合。

图17-4 — 如何编写主键

