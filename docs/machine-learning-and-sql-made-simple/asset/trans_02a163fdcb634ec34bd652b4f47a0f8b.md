
在此示例中，子查询 `(SELECT AVG(salary) FROM employees)` 计算所有员工的平均工资。外部查询检索员工姓名并将平均工资作为单独的列包含在内。

### 2.2 行子查询：

行子查询返回单行，可用于表达式或条件中。它通常放置在 SELECT、WHERE 或 HAVING 子句中。

示例：

```sql
SELECT employee_name
FROM employees
WHERE (department, salary) = (SELECT department, MAX(salary) FROM employees WHERE department = 'Sales');
```

在此示例中，子查询 `(SELECT department, MAX(salary) FROM employees WHERE department = 'Sales')` 检索销售部门的最大工资和对应的部门。外部查询选择具有与子查询结果相同部门和工资的员工的员工姓名。

### 2.3 表子查询：

表子查询返回多行，并在 FROM 子句中用作派生表。它可以被视为主查询中的临时表。

示例：

```sql
SELECT t1.employee_name, t2.department
FROM (SELECT employee_name, department FROM employees WHERE salary > 50000) AS t1
JOIN (SELECT department, location FROM departments WHERE location = 'New York') AS t2
ON t1.department = t2.department;
```

在此示例中，子查询 `(SELECT employee_name, department FROM employees WHERE salary > 50000)` 和 `(SELECT department, location FROM departments WHERE location = 'New York')` 分别创建派生表 t1 和 t2。外部查询基于部门连接这些派生表，并检索在纽约地点工资超过 50000 的员工的员工姓名和部门。

## 第 3 节：使用运算符和函数的子查询

子查询可以与各种运算符和函数一起使用以执行更高级的操作。让我们探索一些示例：

### 3.1 使用比较运算符的子查询：

```sql
SELECT employee_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

在此示例中，子查询 `(SELECT AVG(salary) FROM employees)` 计算所有员工的平均工资。外部查询检索工资高于平均值的员工的员工姓名和工资。

### 3.2 使用 EXISTS 运算符的子查询：

```sql
SELECT department_name
FROM departments d
WHERE EXISTS (SELECT * FROM employees e WHERE e.department_id = d.department_id);
```

在此示例中，子查询 `(SELECT * FROM employees e WHERE e.department_id = d.department_id)` 检查每个部门是否有员工。外部查询检索至少有一名员工的部门的部门名称。

### 3.3 使用 IN 运算符的子查询：

```sql
SELECT product_name
FROM products
WHERE product_id IN (SELECT product_id FROM orders WHERE order_date >= '2023-01-01');
```

在此示例中，子查询 `(SELECT product_id FROM orders WHERE order_date >= '2023-01-01')` 检索 2023 年 1 月 1 日之后下单的订单的产品 ID。外部查询检索在指定时间范围内已被订购的产品产品名称。

## 第 4 节：子查询最佳实践

为了在 SQL 查询中充分利用子查询，请考虑以下最佳实践：

- 保持子查询简单：避免过于复杂的子查询，这会使查询难以理解和维护。将复杂需求分解为更小、更易管理的子查询。
- 优化子查询：评估子查询的性能并确保其得到适当优化。使用适当的索引和查询优化技术来提高效率。
- 测试子查询：在将子查询应用于较大数据集之前，先在小数据集上测试子查询，以确保其返回预期结果并性能良好。
- 将子查询与连接结合使用：在可能的情况下，考虑使用连接代替子查询以获得更好的性能。连接有时可以提供更高效的查询执行计划。
- 记录子查询：清楚地记录子查询的目的和逻辑，以增强代码的可读性和可维护性。

## 第 5 节：结论

子查询是 SQL 中的一种强大工具，允许您将查询嵌套在其他查询中，从而实现高级数据检索和操作。通过了解不同类型的子查询及其应用，您可以利用此功能编写更复杂和高效的 SQL 查询。

在下一章中，我们将探索 SQL 函数。函数提供了一种执行计算、操作数据和从数据库检索信息的方法。我们将介绍各种类型的函数及其在 SQL 中的用法。准备好通过函数提升您的 SQL 技能吧！

## 第 10 章：SQL 函数

在前几章中，我们学习了在 SQL 中查询和操作数据。在本章中，我们将深入探讨 SQL 函数。函数是强大的工具，可让您执行计算、操作数据并从数据库检索信息。它们提供了一种封装逻辑和重用代码的方式。在本章中，我们将探索不同类型的 SQL 函数及其用法。

## 第 1 节：SQL 函数简介

函数是一个命名操作，它接受一个或多个参数，执行特定任务并返回结果。SQL 提供了广泛的内置函数供您在查询中使用。函数可用于各种 SQL 语句，例如 SELECT、WHERE、GROUP BY 和 HAVING 子句。它们可以操作数据、执行计算、转换数据类型、检索信息等等。

## 第 2 节：标量函数

标量函数对单个值进行操作并返回单个值。让我们探索一些常用的标量函数：

### 2.1 字符串函数：

- CONCAT：连接两个或多个字符串。
- LENGTH：返回字符串的长度。
- UPPER：将字符串转换为大写。
- LOWER：将字符串转换为小写。
- SUBSTRING：根据指定的起始位置和长度从字符串中提取子字符串。

示例：

```sql
SELECT CONCAT(first_name,' ',last_name) AS full_name,
  LENGTH(email) AS email_length,
  UPPER(city) AS capital_city,
  LOWER(address) AS lowercase_address,
  SUBSTRING(description, 1, 50) AS short_description
FROM customers;
```

在此示例中，我们使用各种字符串函数来操作字符串值。我们连接名字和姓氏，计算电子邮件的长度，将城市转换为大写，将地址转换为小写，并从描述列中提取简短描述。

### 2.2 数字函数：

- ABS：返回数字的绝对值。
- ROUND：将数字四舍五入到指定的小数位数。
- CEILING：将数字向上舍入到最接近的整数。
- FLOOR：将数字向下舍入到最接近的整数。
- SQRT：返回数字的平方根。

示例：

```sql
SELECT employee_id,
    ABS(salary) AS absolute_salary,
    ROUND(commission_rate, 2) AS rounded_commission,
    CEILING(rating) AS rounded_rating,
    FLOOR(years_of_service) AS service_years,
SQRT(total_sales) AS square_root_sales
FROM employees;
```

在此示例中，我们应用数字函数来操作数值。我们计算工资的绝对值，将佣金率四舍五入到两位小数，将评级向上舍入，将服务年限向下舍入，并计算总销售额的平方根。

## 第 3 节：聚合函数

聚合函数对一组值执行计算并返回单个值。它们通常与 GROUP BY 子句一起使用以汇总数据。让我们探索一些常用的聚合函数：

- 3.1 SUM：计算列的总和。
- 3.2 AVG：计算列的平均值。
- 3.3 COUNT：计算列中行数或非空值的数量。
- 3.4 MIN：返回列中的最小值。
- 3.5 MAX：返回列中的最大值。
