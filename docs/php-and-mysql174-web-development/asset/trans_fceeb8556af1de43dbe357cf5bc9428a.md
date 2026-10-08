

# 存储过程

```
SHOW CREATE FUNCTION Add_Tax;
```

你可以使用以下命令删除它们：

```
DROP PROCEDURE Total_Orders;
```

或者

```
DROP FUNCTION Add_Tax;
```

存储过程具有使用控制结构、变量、`DECLARE` 处理器（如异常）以及一个重要概念——游标（cursors）的能力。我们将在接下来的章节中简要介绍这些每一个项。

# 局部变量

你可以在 `BEGIN...END` 块内部使用 `DECLARE` 语句声明局部变量。例如，你可以声明 `Add_Tax` 函数使用一个局部变量来存储税率，如列表 13.3 所示。

### 列表 13.3 basic_function_with_variables.sql—带变量的存储函数

```sql
# 创建函数的基本语法

DELIMITER /

CREATE FUNCTION Add_Tax (Price FLOAT) RETURNS FLOAT NO SQL
BEGIN
DECLARE Tax FLOAT DEFAULT 0.10;
RETURN Price*(1+Tax);
END
//
DELIMITER ;
```

可以看出，你使用 `DECLARE` 声明变量，后面是变量名和类型。`DEFAULT` 子句是可选的，用于指定变量的初始值。然后按照预期使用该变量。

# 游标和控制结构

让我们考虑一个更复杂的示例。在这个示例中，你将编写一个存储过程，找出最大的金额并返回 OrderID。（显然，可以使用单个查询轻松计算此金额，但这个简单的示例说明了如何使用游标和控制结构。）该存储过程的代码在列表 13.4。

### 列表 13.4 control_structures_cursors.sql—使用游标和循环处理结果集

```sql
# 查找最大金额的过程

DELIMITER //

CREATE PROCEDURE Largest_Order (OUT Largest_ID INT)
BEGIN
    DECLARE This_ID INT;
    DECLARE This_Amount FLOAT;
    DECLARE L_Amount DEFAULT 0.0;
    DECLARE L_ID INT;

    DECLARE C1 CURSOR FOR SELECT OrderID, Amount FROM Orders;
    DECLARE CONTINUE HANDLER FOR SQLSTATE '02000' SET Done = 1;

    OPEN C1;
    REPEAT
        FETCH C1 INTO This_ID, This_Amount;
        IF NOT FOUND THEN
            IF This_Amount > L_Amount THEN
                SET L_Amount = This_Amount;
                SET L_ID = This_ID;
            END IF;
        END IF;
    UNTIL Done REPEAT;
    CLOSE C1;

    SET Largest_ID=L_ID;
//
DELIMITER ;
```

这使用了控制结构（条件和循环）、游标和处理器。让我们逐行考虑它。

在过程的开头，你声明了一些局部变量。`This_ID` 和 `This_Amount` 变量存储当前行的 `OrderID` 和 `Amount` 值。`L_Amount` 和 `L_ID` 用于存储最大的金额和对应的 ID。将这些变量初始化为零。

下一个定义的变量是 `Done`，初始化为 0（假）。这是你的循环标记。当没有更多行需要处理时，会将此变量设置为 1（真）。下一件事是游标。游标与数组不同；它检索查询的结果集（如 `fetch_row()`），并允许你一次处理一行。考虑这个游标：

```sql
DECLARE C1 CURSOR FOR SELECT OrderID, Amount FROM Orders;
```

这个游标被称为 `C1`。这只是定义了它将包含的内容。查询尚未执行。

```sql
DECLARE CONTINUE HANDLER FOR SQLSTATE '02000' SET Done = 1;
```

这是一个 `DECLARE` 处理器。它类似于存储过程中的异常。此外，还有继续处理器和退出处理器。所示的继续处理器会执行指定的动作，然后继续执行最近的 `BEGIN...END` 块。

`DECLARE` 处理器的后续部分指定了处理器何时被调用。在这种情况下，当未找到行时调用。你可能会奇怪这意味着什么，因为看起来很晦涩。你按行处理结果集，当没有更多行可以处理时，此处理器会被调用。你也可以同样指定 `FOR NOT FOUND`。

下一行

```
OPEN C1

为了获取每一行数据，必须运行 `FETCH` 语句。你在 `REPEAT` 循环中执行此。在这种情况下，循环如下：

```sql
REPEAT
UNTIL DONE REPEAT;
```

注意条件（`UNTIL DONE`）在最后检查。存储过程支持 `WHILE` 循环。

```sql
WHILE condition DO
...
END WHILE;
```

还有 `LOOP` 循环，形式如下：

```sql
LOOP
END LOOP;
```

这些循环没有内置条件，但可以通过 `LEAVE` 语句退出。注意没有 `FOR` 循环。

继续示例，下一行获取一行数据：

```sql
FETCH C1 INTO This_ID, This_Amount;
```

这一行从游标中检索一行。查询检索的属性存储在指定的局部变量中。你检查是否检索了行，然后通过两个 `IF` 语句将当前金额与最大金额进行比较：

```sql
IF NOT DONE THEN
    IF This_Amount > L_Amount THEN
        SET L_Amount=This_Amount;
        SET L_ID=This_ID;
    END IF;
END IF;
```

注意变量值是通过 `SET` 语句设置的。除了 `IF...THEN` 外，存储过程还支持以下形式的 `IF...THEN...ELSE` 结构：

```sql
IF condition THEN
    ELSEIF condition THEN
    ELSE
    ...
END IF
```

还有一个 `CASE` 语句，其形式如下：

```sql
CASE value
    WHEN value THEN statement
    [WHEN value THEN statement ...]
    [ELSE statement]
END CASE
```

回到示例，循环终止后，你有一些清理工作要做：

```
CLOSE C1;SET Largest_ID=L_ID;
```

`CLOSE` 语句关闭游标。注意：不能将参数作为临时变量，仅用于存储值。这种用法类似于某些编程语言，如 Ada。

如果你按照描述创建此过程，可以像调用其他过程一样调用它：

```sql
CALL Largest_Order(@l);
SELECT @l;
```

你应该得到类似下面的输出：

```
+------+
| @l |
+------+
|  3 |
+------+
```

1行 (0.00 sec)

你可以自己检查计算是否正确。

# 触发器

触发器是一种事件驱动的存储例，或者如果你愿意，称为回调。它们是与表关联的代码，当在该表上执行特定操作时被触发。

触发器的基本形式如下：

```sql
CREATE TRIGGER trigger_name
{BEFORE | AFTER} {INSERT | UPDATE | DELETE} ON table
[order]
FOR EACH ROW
BEGIN

END
```

第一行命要创建的触发器。时机（BEFORE 或 AFTER）和触发触发器的事件（对指定表的 INSERT、UPDATE 或 DELETE）的组合决定了触发器主体执行的代码。

可选的 `order` 子句允许在特定的时间/事件组合上运行多个触发器。该子句的形式为

```sql
{FOLLOWS | PRECEDES} other_trigger
```

`EACH ROW` 子句意味着触发器为触发查询的每一行执行一次。

让我们看一个简单的示例。此代码在列表 13.5 中。

### 列表 13.5 trigger.sql—删除订单

```sql
# 触发器示例

DELIMITER //

# 在删除前删除订单以避免引用完整性错误
CREATE TRIGGER Delete_Order_Items
BEFORE DELETE ON Orders EACH ROW
BEGIN
DELETE FROM Order_Items WHERE OrderId = OLD.OrderId;
END
/

DELIMITER ;
```

