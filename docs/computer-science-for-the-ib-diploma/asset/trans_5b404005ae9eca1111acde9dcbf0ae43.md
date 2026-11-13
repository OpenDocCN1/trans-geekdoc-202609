
要求，以及维护和更新操作中复杂性的增加。因此，需要在两者之间找到平衡，这需要：

- 分析应用程序的具体要求（重点是读取或检索数据，还是更新数据？）
- 评估反规范化数据库的收益是否高于数据冗余和复杂性的风险（有时部分反规范化模式可能是一种解决方案）
- 实施适当的策略以降低风险并优化性能（实施强大的数据验证，监控查询性能和存储要求，等等）。

### ACTIVITY

独立学习：独立反思与改进目标——找出你的强项和弱项，并为取得成功设定短期目标。在分析你的强项和弱项时，请考虑：技术技能和软技能；来自同伴和教师的建设性或积极反馈；成功的项目；形成性评估；以及知识差距或技术差距。短期目标会让你保持专注；它们将使你能够制定可逐步监控和评估的行动计划。

### TOK

**功利主义，最大多数人的最大幸福。目的可以证明手段的正当性。**

功利主义是一种伦理理论，认为最佳行动是能最大化整体幸福或福祉的行动。这种方法通常用“最大多数人的最大幸福”这一短语来概括。根据这一观点，行为的道德价值由其结果或后果决定，而非由行为本身的任何内在特质决定。例如，如果牺牲少数人的福祉能为社会带来更大的整体利益，功利主义者将认为这种牺牲是正当的。

在管理数据库时，尤其是包含个人信息的数据库，隐私与实用性之间通常存在权衡。功利主义方法可能会证明在未经明确同意的情况下使用个人数据是合理的，如果这能带来更大的益处，例如通过数据驱动的洞察改善公共卫生。在大流行期间，卫生当局可能会访问和分析大量个人健康信息数据集以追踪病毒传播。从功利主义角度来看，对社会的潜在益处（例如，控制大流行）可能会超越个人隐私担忧。功利主义“最大数人的最大幸福”原则为关于如何管理、使用和保护数据库的决策提供了框架。

讨论如何将这种方法与其他伦理考量（例如个人权利和公平性）相平衡，这些考量可能并不总是与纯粹的功利主义视角一致。

### REVIEW QUESTIONS

1. 定义术语“模式”。
2. 讨论规范化数据库的特征。
3. 找出数据冗余导致的两个问题。
4. 说明以下内容的特征：
   a. 1NF
   b. 2NF
   c. 3NF
5. 区分概念模式和逻辑模式。

## 大纲内容

本章学习结束后，你应能够：

- A3.3.1 概述结构化查询语言（SQL）中数据语言类型之间的区别
- A3.3.2 在 SQL 中构建两个表之间的查询
- A3.3.3 解释如何使用 SQL 更新数据库中的数据
- A3.3.4 使用 SQL 聚合函数在数据库中构建计算（HL）
- A3.3.5 描述不同的数据库视图（HL）
- A3.3.6 描述事务如何在数据库中维护数据完整性（HL）

## A3.3.1 SQL 中的数据语言类型

数据语言类型包括数据定义语言（DDL）和数据操纵语言（DML）。

数据定义语言：用于从关系数据库中创建、修改和删除数据结构的语言。

### 数据定义语言（DDL）

数据定义语言（DDL）用于从关系数据库中创建、修改和删除数据结构。

| SQL DDL 指令 | 说明 |
|---|---|
| CREATE | 创建新的数据库对象（表、视图、索引） |
| PRIMARY KEY | 将字段设置为主键 |
| FOREIGN KEY ... REFERENCES ... | 通过指定字段及其关联的表，将字段设置为外键 |
| ALTER | 更改现有数据库对象的结构：通过添加或删除列或添加约束来更改表结构 |
| DROP | 删除数据库对象（表、索引、视图） |

```
CREATE statements
CREATE DATABASE:
CREATE DATABASE HOSPITAL
CREATE TABLE:
CREATE TABLE Employees (
EmployeeID INT,
DepartmentID INT PRIMARY KEY,
LastName VARCHAR(20)
);
CREATE VIEW:
CREATE VIEW EmployeeDetails AS
SELECT EmployeeID, LastName
FROM Employees
JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
CREATE INDEX:
CREATE INDEX idx_last_name ON Employees(LastName);

ALTER statements
Add primary key:
ALTER TABLE Employees
ADD PRIMARY KEY (EmployeeID);

Add foreign key:
ALTER TABLE Employees
ADD FOREIGN KEY DepartmentID REFERENCES Departments(DepartmentID);

Add a column:
ALTER TABLE Employees
ADD Email VARCHAR(25);

Drop a column:
ALTER TABLE Employees
DROP COLUMN Email;

Add a constraint:
ALTER TABLE Employees
ADD CONSTRAINT FK_DepartmentID
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID);

DROP statements
Drop table:
DROP TABLE Employees;

Drop index:
DROP INDEX idx_last_name;

Drop view:
DROP VIEW EmployeeData;
```

### 数据操纵语言（DML）

数据操纵语言用于添加、修改、删除和检索存储在关系数据库中的数据。

> 数据操纵语言：用于添加、修改、删除和检索存储在关系数据库中的数据的语言。

| SQL DML 指令 | 说明 |
|---|---|
| SELECT | 从一个或多个表中检索数据 |
| INSERT | 向表中添加记录 |
| DELETE | 从表中删除记录 |
| UPDATE | 修改表中的现有记录 |

## A3.3.2 SQL 中两个表之间的查询

在 SELECT 语句中包含 JOIN 允许你从多个表中聚合数据。例如，考虑员工表和部门表，下面的脚本按部门检索工资开支。

### SELECT 语句中的 JOIN

```sql
SELECT Employees.DepartmentName, SUM(Employees.Salary) AS TotalSalary
FROM Employees
JOIN Department ON Employees.DepartmentID = Department.DepartmentID
GROUP BY Department.DepartmentName;
```

### SELECT 语句中的 DISTINCT

当你想要检索唯一记录并忽略重复项时，可以使用关键字 DISTINCT。

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

### HAVING 子句与 WHERE 子句

HAVING 子句用于过滤由 GROUP BY 子句创建的记录组，例如在需要检索每个部门的部门 ID 和平均工资且平均工资高于 10,000 的情况下。
WHERE 子句用于在分组之前过滤记录，而 HAVING 子句用于在聚合之后过滤组。

```sql
SELECT DepartmentID, Salary
FROM Employees
GROUP BY DepartmentID
HAVING Salary > 10000;
```

### 关系运算符

关系运算符可用于获取符合特定条件的数据。

| 运算符 | 示例 |
|---|---|
| 等于 | SELECT * FROM Employees WHERE DepartmentID = 1; |
| 不等于 | SELECT * FROM Employees WHERE DepartmentID <> 1; |
| 大于 | SELECT * FROM Employees WHERE Salary > 10000; |
| 小于 | SELECT * FROM Employees WHERE Salary < 10000; |
| 大于或等于 | SELECT * FROM Employees WHERE Salary >= 10000; |
| 小于或等于 | SELECT * FROM Employees WHERE Salary <= 10000; |

### 筛选

| 运算符 | 示例 |
|---|---|
| BETWEEN 筛选范围内的值 | SELECT * FROM Employees WHERE Salary BETWEEN 50000 AND 100000; |
| IN 筛选与给定列表中任何值匹配的值 | SELECT * FROM Employees WHERE DepartmentID IN (1, 2, 3); |
| IS NULL 筛选具有空值的记录 | SELECT * FROM Employees WHERE ManagerID IS NULL; |
| IS NOT NULL 筛选具有非空值的记录 | SELECT * FROM Employees WHERE ManagerID IS NOT NULL; |
| 使用逻辑运算符组合条件 | SELECT * FROM Employees WHERE (DepartmentID = 5 AND Salary > 50000) OR (DepartmentID = 1 AND Salary > 10000); |

### 模式匹配

- LIKE 基于模式筛选值。
- % 用于任何字符序列（零个或多个）。
- _ 用于单个字符。

这将检索以字母 D 开头的记录：

```sql
SELECT * FROM Employees
WHERE LastName LIKE 'D%';
```

这将检索以字母 d 结尾的记录：

```sql
SELECT * FROM Employees
WHERE LastName LIKE '%d';
```

这将检索匹配特定模式（以字母 D 开头，后跟一个字符，后跟字母 m，再后跟零个或多个字符）的记录：

```sql
SELECT * FROM Employees
WHERE LastName LIKE 'D_m%';
```

这将检索由三个字符组成的记录：

```sql
SELECT * FROM Employees
WHERE LastName LIKE '_ _ _';
```
