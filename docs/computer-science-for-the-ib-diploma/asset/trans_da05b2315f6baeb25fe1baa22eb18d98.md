

## 对数据进行排序

按单个字段排序：
SELECT * FROM Employees
ORDER BY LastName;

按单个字段升序排列：
SELECT * FROM Employees
ORDER BY LastName ASC;

按单个字段降序排列：
SELECT * FROM Employees
ORDER BY LastName DESC;

按多个字段排序：
SELECT * FROM Employees
ORDER BY DepartmentID, Salary DESC;

## A3.3.3 SQL 更新查询

| SQL 语句 | 说明 | 示例 |
| :--- | :--- | :--- |
| INSERT | 添加新记录 | INSERT INTO table_name (field1, field2, ...) VALUES (value1, value2, ...); |
| DELETE | 删除记录 | DELETE FROM table_name WHERE condition; |
| UPDATE | 修改记录 | UPDATE table_name SET field1 = value1, field2 = value2, ... WHERE condition; |

索引列可优化查询性能，但更新索引列中的数据可能会影响性能。当对索引列执行更新时，索引也需要随之更新，这可能会减慢操作速度。此外，索引更新可能会阻止其他需要访问特定记录的事务。为克服这些挑战，你可以批量更新以减少索引更改的次数；经常重建或重组索引以减少碎片；或使用部分索引或筛选索引，将索引范围仅限于最相关的记录。

## A3.3.4 SQL 的聚合函数（HL）

聚合函数用于根据给定字段对多条记录进行计算。此类函数包括 AVERAGE、COUNT、MAX、MIN、SUM。

聚合函数：用于根据给定字段对多条记录进行计算的函数，例如 AVERAGE、COUNT、MAX、MIN、SUM。

| 聚合函数 | 示例 |
| :--- | :--- |
| SUM 返回数值字段的总值 | SELECT SUM(Salary) FROM Employees; |
| COUNT 返回满足给定条件的记录数 | SELECT COUNT(EmployeeID) FROM Employees; |
| AVERAGE 返回数值字段的平均值 | SELECT AVG(Salary) FROM Employees; |
| MIN 返回字段中的最小值 | SELECT MIN(Salary) FROM Employees; |
| MAX 返回字段中的最大值 | SELECT MAX(Salary) FROM Employees; |

### 对分组数据使用聚合函数

在分组数据上使用聚合函数有助于报告和决策。例如，显示每个部门的员工人数：

```
SELECT Department.DepartmentName, COUNT(Employees.EmployeeID)
AS ECount
FROM Employees
JOIN Department ON Department.DepartmentID = Employees.DepartmentID
GROUP BY Department.DepartmentName;
```

另一个示例是当你想要显示每个部门的平均工资时：

```
SELECT Department.DepartmentName, AVG(Employees.Salary) AS AvgSalary
FROM Employees
JOIN Department ON Employees.DepartmentID = Department.DepartmentID
GROUP BY Department.DepartmentName;
```

另一个示例是显示每个部门的最低和最高工资：

```
SELECT DepartmentID, MIN(Salary) AS MinSal, MAX(Salary) AS MaxSal
FROM Employees
GROUP BY DepartmentID;
```

> 视图：基于 SELECT 查询结果集的虚拟表。它们本身不存储数据，但提供了一种以自定义方式呈现一个或多个表中数据的方法。

## A3.3.5 数据库视图（HL）

视图是基于 SELECT 查询结果集的虚拟表。它们本身不存储数据，但提供了一种以自定义方式呈现一个或多个表中数据的方法。多个视图可向不同用户展示不同的数据子集，并根据用户需求以不同方式呈现数据。

使用视图的几个优势：

- 数据复杂性隐藏：视图可以封装复杂查询，简化用户查询数据的过程，无需了解底层 SQL。
- 数据一致性：即使底层表被修改，视图也可以以一致的方式呈现数据。
- 数据独立性：可以更改数据库架构而不影响用户视图。
- 性能：视图可以通过简化复杂查询、将连接操作抽象为单个可重用对象（即视图）来提高性能。
- 查询简化：可以通过将查询分解为更小的部分、隐藏不必要的细节、应用筛选器和计算并在视图中显示结果来简化查询。
- 只读或可更新视图：更新视图时，只有在满足特定条件时，更改才会传递到创建视图的基表。如果满足这些条件，则视图可更新；否则，它是只读的。视图可更新有三个条件：它必须是单个表或另一个可更新视图的子集；视图定义中排除的所有基表字段应允许 NULL 值；并且视图的 SELECT 语句不应包含子查询（DISTINCT 谓词、HAVING 子句、聚合函数、连接的表、用户定义函数或存储过程）。
- 安全性：视图可以限制对特定属性或记录的访问，从而提供一种控制用户可访问哪些数据的方法。

数据库视图有不同类型。其中一些类型包括简单视图、复杂视图或物化（快照）视图。

### 简单视图

简单视图是基于单个表且不包含复杂查询（如聚合函数或连接）的视图。

简单视图的示例是显示表中的某些字段。在此示例中，从 Employees 表中显示三个字段（EmployeeID、FirstName 和 LastName）。

```
CREATE VIEW EmpNames AS
SELECT EmployeeID, FirstName, LastName
FROM Employees;
```

### 复杂视图

复杂视图是包含多个表和复杂查询（如聚合函数或连接）的视图。

复杂视图的示例是显示 Employees 和 Department 表中的数据。

```
CREATE VIEW EmpDepartment AS
SELECT Employees.EmployeeID, Employees.LastName,
Department.DepartmentName
FROM Employees
JOIN Department ON Employees.DepartmentID = Department.DepartmentID;
```

### 物化（快照）视图

物化视图是可以频繁刷新的视图，它们存储从 SELECT 查询派生的预计算数据集并供以后使用。由于它避免了重新运行查询（常规视图中使用的做法），因此通常能更快地交付数据。以下代码是一个显示 Employees 表中每个员工的员工 ID 和工资的视图示例。

### 创建快照视图：

```
CREATE MATERIALIZED VIEW TotalSalaries AS
SELECT EmployeeID, SUM(Salary) AS TotalSal
FROM Employees
GROUP BY EmployeeID;
```

### 查询快照视图：

```
SELECT * FROM TotalSalaries;
```

## A3.3.6 事务如何维护数据库中的数据完整性（HL）

### ACID

事务是作为一个工作单元执行的 SQL 操作序列，确保数据完整性和一致性。

ACID 是定义事务的四个属性的首字母缩写：

- 原子性

  事务具有原子性（不可分割且视为一个整体）。事务中的所有操作要么全部成功完成，要么全部不执行。如果事务的任何部分失败，整个事务将回滚，数据库保持不变。

- 一致性

  事务确保数据遵循预定义的规则或约束。事务完成后，数据库必须处于有效且预期的状态。

- 隔离性

  事务彼此隔离以防止干扰。这确保了多个事务的并发执行不会导致数据不一致。

- 持久性

  一旦事务被提交并成功完成，其更改即为永久。即使系统失败，已提交事务所做的更改也会被保留。持久性很重要，因为即使数据库出现故障，事务数据更改也必须可用。

### 小贴士！

应对考试问题时，请确保有效使用术语。通常，考生似乎理解概念，但他们提供泛泛的回答，答案往往缺乏精确性。撰写回答时必须精确使用术语，才能获得满分。

### 事务控制语言（TCL）命令

SQL 中的 TCL 命令用于管理事务。其中一些命令包括：

- BEGIN TRANSACTION：用于在 SQL 中启动新事务。

- COMMIT：用于将当前事务期间所做的所有更改保存到数据库。

  执行此操作后，更改即为永久性，并对其他用户可见。

```
BEGIN TRANSACTION;
UPDATE Employees SET Salary = Salary + 100 WHERE EmployeeID = 1;
UPDATE Employees SET Salary = Salary - 100 WHERE EmployeeID = 5;
COMMIT;
```

在上面的示例中，针对两条记录的 UPDATE 语句被写入，一旦达到 COMMIT 语句，它们都会被保存。

