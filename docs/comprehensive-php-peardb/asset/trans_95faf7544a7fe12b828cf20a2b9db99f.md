

## 结论

PEAR::DB 是一个功能强大的面向对象抽象层，由 PHP 核心开发团队成员支持和维护。PEAR::DB 是任何支持数据库的 PHP 应用的正确工具，无论其规模大小。使用 PEAR::DB 的主要原因是通过代码复用实现快速（或更快速）应用开发和应用可维护性。虽然 PEAR::DB 可以实现数据库可移植性，但大多数中大型应用将会依赖底层数据库，以至于很可能会使用特定于引擎的 SQL。

随着 PHP 的成熟，PEAR::DB 也将随之成熟。认真考虑应用长期可维护性的开发者，应该认真考虑将 PEAR::DB 作为其数据库抽象层。

## 附录 A：图表清单

### 表格

| 项目 | 页码 |
| --- | --- |
| 表 1：PEAR::DB 支持的数据库 | 19 |
| 表 2：数据库类的默认选项 | 20 |
| 表 3：DB 类方法 | 30 |
| 表 4：DSN 数组元素 | 36 |
| 表 5：代码清单 18 的结果（为本书重新格式化） | 46 |
| 表 6：query() 方法中使用的占位符 | 60 |
| 表 7：每个数据库后端在 getSpecialQuery 中支持的类型 | 107 |
| 表 8：DB_result 类方法 | 109 |
| 表 9：DB_storage 类方法 | 125 |

### 图

| 项目 | 页码 |
| --- | --- |
| 图 1：系统属性页面 | 4 |
| 图 2：环境变量对话框 | 5 |
| 图 3：将路径添加到 PEAR.BAT 文件 | 5 |
| 图 4：ErrorPopup 函数创建的弹出窗口 | 52 |
| 图 5：代码清单 58 的基于浏览器的输出 | 117 |
| 图 6：DB_storage 概览代码的输出 | 124 |

### 代码清单

| 项目 | 页码 |
| --- | --- |
| 代码清单 1：创建示例数据库的 MySQL 语句 | 10 |
| 代码清单 2：示例员工数据库的 SQL 查询 | 11 |
| 代码清单 3：过程式数据库访问 | 12 |
| 代码清单 4：PEAR::DB 数据库访问 | 13 |
| 代码清单 5：PEAR::DB 数据库访问（第二次尝试） | 16 |
| 代码清单 6：完整 DSN 格式 | 18 |
| 代码清单 7：DSN 格式的变体 | 18 |
| 代码清单 8：DB::connect() 示例 | 22 |
| 代码清单 9：使用序列 | 23 |
| 代码清单 10：自定义序列表名称格式 | 25 |
| 代码清单 11：使用 prepare() 和 execute() 概述 | 27 |
| 代码清单 12：使用 autoPrepare | 28 |
| 代码清单 13：DB::factory | 32 |
| 代码清单 14：DB::connect 的几个示例 | 34 |
| 代码清单 15：DB::assertExtension 示例 | 37 |
| 代码清单 16：DB_common::toString 示例 | 42 |
| 代码清单 17：DB_common::quote 示例 | 43 |
| 代码清单 18：DB_common::provides 示例 | 45 |
| 代码清单 19：DB_common::errorCode、DB_common::errorMessage、DB_common::errorNative() 示例 | 47 |
| 代码清单 20：使用 DB_Error | 52 |
| 代码清单 21：DB_common::setFetchMode - DB_FETCHMODE_ORDERED（默认） | 53 |
| 代码清单 22：DB_common::setFetchMode - DB_FETCHMODE_ASSOC | 55 |
| 代码清单 23：DB_common::setFetchMode - DB_FETCHMODE_OBJECT | 56 |
| 代码清单 24：DB_common::setFetchMode - 使用 object_class 参数的 DB_FETCHMODE_OBJECT | 58 |
| 代码清单 25：使用 prepare() -- 简单示例 | 61 |
| 代码清单 26：创建 uploadedfiles 表的 SQL 语句 | 62 |
| 代码清单 27：使用 '&' 占位符的 prepare() 方法 | 63 |
| 代码清单 28：使用 autoPrepare() - INSERT | 64 |
| 代码清单 29：使用 autoPrepare() - UPDATE | 65 |
| 代码清单 30：使用 autoExecute() | 67 |
| 代码清单 31：使用 buildManipSQL() | 68 |
| 代码清单 32：executeEmulateQuery() 示例 | 70 |
| 代码清单 33：使用 executeMultiple() | 71 |
| 代码清单 34：使用 query() | 73 |
| 代码清单 35：使用 SQL 限制 MySQL 查询... | 74 |

### 输出清单

| 项目 | 页码 |
| --- | --- |
| 输出 1：在无命令行参数的情况下运行 PEAR 命令 | 7 |
| 输出 2：PEAR list 的输出 | 7 |
| 输出 3：序列示例（代码清单 9）的结果 | 24 |
| 输出 4：序列示例第二次运行的结果 | 24 |
| 输出 5：DB::assertExtension 示例输出 | 37 |
| 输出 6：DB_common::toString 输出 | 42 |
| 输出 7：DB_common::quote 示例输出 | 44 |
| 输出 8：fetchMode 设为 DB_FETCHMODE_ORDERED 时的输出 | 54 |
| 输出 9：fetchMode 设为 DB_FETCHMODE_ASSOC 时的输出 | 55 |
| 输出 10：fetchMode 设为 DB_FETCHMODE_OBJECT 时的输出 | 56 |
| 输出 11：fetchMode 设为 DB_FETCHMODE_OBJECT 并设置了 object_class 时的输出 | 58 |
| 输出 12：使用 buildManipSQL() 的示例 | 68 |
| 输出 13：executeEmulateQuery() 示例的输出 | 70 |
| 输出 14：getRow() 方法的输出 | 79 |
| 输出 15：getCol() 方法的输出 | 81 |
| 输出 16：与代码清单 40 相关的 getAssoc() 输出 | 83 |
| 输出 17：与代码清单 41 相关的 getAssoc() 输出 | 84 |
| 输出 18：与代码清单 42 相关的 getAssoc() 输出 | 85 |
| 输出 19：与代码清单 43 相关的 getAssoc() 输出 | 86 |
| 输出 20：与代码清单 44 相关的 getAssoc() 输出 | 88 |
| 输出 21：与代码清单 45 相关的 getAssoc() 输出 | 89 |
| 输出 22：与代码清单 46 相关的 getAll() 输出 | 91 |
| 输出 23：与代码清单 47 相关的 getAll() 输出 | 93 |
| 输出 24：使用 commit() 的示例 | 96 |
| 输出 25：使用 rollback() 的示例 | 98 |
| 输出 26：在用户权限不足的 MySQL 数据库上执行 createSequence() 的输出 | 102 |
| 输出 27：tableInfo() 方法的输出 | 104 |
| 输出 28：与 getTables 示例（代码清单 54）相关的输出 | 106 |
| 输出 29：getListOf() 示例（代码清单 55）的输出 | 108 |
| 输出 30：代码清单 56 中 fetchRow() 的结果 | 112 |
| 输出 31：fetchInto 示例（代码清单 57）的结果 | 114 |
| 输出 32：tableInfo() 方法的 MODE 参数 | 120 |
| 输出 33：setUp() 示例的输出 | 126 |
| 输出 34：DB_storage::toString() 的输出 | 129 |
| 输出 35：使用 set() 和 get() 以及回调验证函数 | 133 |

