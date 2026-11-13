

## A3.2.3 关系型数据库中使用的数据类型

| 属性的数据类型 | 描述 |
|---|---|
| CHARACTER | 固定长度文本 |
| VARCHAR(n) | 可变长度文本（n 表示字符的最大数量） |
| INTEGER | 整数 |
| REAL | 带有小数部分的数字 |
| DATE | 格式为 YYYY-MM-DD 的日期 |
| TIME | 格式为 HH:MM:SS 的时间 |
| BOOLEAN | 真或假 |

选择正确的数据类型对于确保高效索引非常重要。例如，对于 UserID 等固定长度数据，使用 CHARACTER (8) 比使用 VARCHAR (8) 更高效，因为可变长度存储可能导致查询执行期间额外的时间开销。此外，数据类型指示允许的操作类型。例如，如果将数量和价格存储为固定长度文本，则在使用数据之前，需要在应用程序中将文本转换为整数或实数值，以便进行计算。

使用适当数据类型的另一个方面是能够将数据库中的数据存储到相应的字段中。如果数据的类型与数据库中属性的数据类型不匹配，插入尝试将引发错误。

数据一致性确保用户可以访问最新且准确的信息，其中所有副本或实例在所有系统和数据库表中都相同。在不同平台（数据库和应用系统）上使用不同的数据类型来引用同一属性，会导致诸如无法执行特定于所需数据类型的操作、更新或查询不正确等问题。

## A3.2.4 构建关系型数据库表

在数据库中正确定义表，有助于设计合适的 ERD，并确保数据完整性。

以学校管理系统为例，可能包含以下表格：

- STUDENT (StudentID, FirstName, LastName, DateOfBirth, Email)
- CLUB (StudentID, ClubTitle, TeacherName)
- TEACHER (TeacherClub, Location)

| StudentID | FirstName | LastName | DateOfBirth | Email |
|---|---|---|---|---|
| 101 | Fatema | Kada | 02/01/2010 | f.kada@email.com |
| 105 | Alexandru | Buchidau | 05/11/2009 | a.buchidau@email.com |
| 202 | Kada | Hussein | 07/25/2011 | k.hussein@email.com |

在 STUDENT 表中，StudentID 充当主键，用于唯一标识表中的每条记录。

| StudentID | ClubTitle | TeacherName |
|---|---|---|
| 105 | Robotics | Bobby Williams |
| 202 | Taekwondo | Dima White |
| 101 | Robotics | Bobby Williams |
| 105 | Arts and Crafts | Jane Doe |

在 CLUB 表中，StudentID 是外键（因为它是 STUDENT 表中的主键）。但是，该表中没有任何字段可以充当主键，因为它们都有重复值。但是，您可以将主键设置为由属性 StudentID 和 ClubTitle 组成的复合键。另一方面，您可以添加一个新属性 ClubID 来充当主键。如果需要单个字段充当主键，可以将多个属性的数据合并为一个，以充当连接键。

| TeacherClub | Location |
|---|---|
| Jane Doe Arts and Crafts | L101 |
| Bobby Williams Robotics | H203 |
| Dima White Taekwondo | B353 |

在 TEACHER 表中，主键是连接键，由属性 TeacherName 和 ClubTitle 组成。

## A3.2.5 范式之间的区别

- 规范化：以减少数据冗余并提高数据完整性的方式组织关系型数据库中数据的过程。
- 第一范式：关系型数据库的一种状态，其中实体不包含重复的属性组。
- 原子性：表中每个属性包含不可分割的值（无法分解为更详细子值的值）。

数据规范化是以减少数据冗余并提高数据完整性的方式组织关系型数据库中数据的过程。由于数据库中的每个数据项只出现在一个位置，因此数据冗余减少。这可以减少更新异常发生的可能性，并更高效地利用内存。规范化会导致表更小，每行包含的信息更少，从而减少输入/输出传输，因此 CPU 可以全速运作，因为 CPU 活动被挂起的可能性降低。规范化通过一系列称为“范式”的阶段来实现，每个范式都有特定要求，表必须满足这些要求才被视为在该级别上规范化。

### 第一范式 (1NF)

在第一范式中，表：

- 具有主键
- 不包含同一表中的重复属性
- 不包含重复的属性组。

因此，您需要为每组相关数据创建单独的表，使用主键标识每条记录，主键由单个属性或一组属性（复合键或组合键）组成，并确保实体不包含重复的属性组。

在 1NF 中，每个字段中的数据必须是原子的。这意味着每个属性包含不可分割的值（无法分解为更详细子值的值）。例如，TEACHER 表中名为 TeacherName 的属性不是原子字段，因为这可能
- **函数依赖**：属性之间存在的一种关系，其中一组属性（决定因素）决定另一组属性（因属性）的值。
- **完全函数依赖**：因属性由决定因素属性决定。
- **部分函数依赖**：因属性部分由决定因素属性决定。
- **传递依赖**：一种函数依赖，当非主属性依赖于另一个非主属性，而非主键时发生。
- **第二范式**：关系型数据库的一种状态，其中实体处于 1NF，且任何非键属性都依赖于主键。
- **第三范式**：关系型数据库的一种状态，其中实体处于 2NF，且所有非键属性相互独立。

be further split into two different attributes called LastName and FirstName. Once this is achieved, the fields are atomic.

可进一步拆分为名为 LastName 和 FirstName 的两个不同属性。一旦实现此目标，字段即为原子字段。

原子性确保表中的每个单元格只包含一个值，而不是数组或列表等复杂结构。

**函数依赖**是属性之间存在的一种关系，其中一组属性（决定因素）决定另一组属性（因属性）的值。通常，这是主键属性与非键属性之间的关系。例如，在 STUDENT 表中，StudentID（主键和决定因素）决定 FirstName、LastName、DateOfBirth 和 Email 值（因属性）。这意味着，给定 StudentID 的值，您可以查找其他详细信息，但反之则不行。要确保 1NF 中的函数依赖，需要确保实体原子性并删除重复的属性组。

存在不同类型的函数依赖：

- **完全函数依赖**：因属性由决定因素属性决定。例如，StudentID 完全确定学生的 FirstName、LastName、DateOfBirth 和 Email。
- **部分函数依赖**：因属性部分由决定因素属性决定。例如，StudentID 可能部分确定学生的 FirstName、LastName 和 DateOfBirth，但不能确定其社团的课程指导教师。
- **传递依赖**：因属性由不包含在决定因素属性中的一组属性决定。例如，在 EMPLOYEES 表中，EmployeeID 可能确定 EmployeeDepartment，而 EmployeeDepartment 反过来决定其薪水。

### 第二范式 (2NF)

在第二范式 (2NF) 中：

- 实体处于 1NF
- 任何非键属性都完全函数依赖于主键；不存在部分依赖。

部分键依赖发生在表的主键为复合键，且一个或多个非键属性仅依赖于复合主键的一个子集，而不是整个复合键时。例如，在 CLUB 表中，非键属性 TeacherName 依赖于 ClubTitle，但不依赖于 StudentID。由于该表中的主键是由 ClubTitle 和 StudentID 字段组成的复合键，因此 TeacherName 应完全函数依赖于这两个字段。

### 第三范式 (3NF)

在第三范式 (3NF) 中：

- 实体处于 2NF
- 所有非键属性相互独立（删除不完全函数依赖于主键的列）；表中不包含非键依赖。

非键或传递依赖是一种函数依赖，当非主属性依赖于另一个非主属性，而非主键时发生。

