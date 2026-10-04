

# 附录 E：PHP 函数引用

imap_header_decode (string str) array 根据 RFC 2047 解码 MIME 头部元素并返回包含字符集编码和解码后文本的对象数组

![](img/245156cc770929860a3ede93c01f9981_515_0.png)

使用 IMAP 函数需要安装 IMAP 库和编译了 `--with-imap` 选项的 PHP。这些可以像在 POP3 服务器上一样工作。

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| ibase_connect(string database [, string username] [, string password] [, string charset] [, int dialect] [, string role]) | int | 打开到 InterBase 数据库的连接并返回连接标识 |
| ibase_connect(string database [, string username] [, string password] [, string charset] [, int dialect] [, string role]) | int | 打开到 InterBase 数据库的持久连接 |
| ibase_close([int link_identifier]) | int | 关闭 InterBase 连接 |
| ibase_commit([int link_identifier,] int trans_number) | int | 提交事务 |

# 表 E-31 INTERBASE 函数（续表）

| 函数 | 返回值 | 操作 |
|---|---|---|
| ibase_rollback([int link_identifier,] int trans_number) | int | 回滚事务 |
| ibase_query([int link_identifier.] string query [. int_bind])]) | int | 执行查询 |
| ibase_prepare([int link_identifier.] string query) | int | 准备稍后执行的查询 |
| ibase_fetch_row(int [, int blob_flag]) | array | 从查询结果中获取一行 |
| ibase_fetch_object(int result [, int blob_flag]) | object | 从查询结果中获取一个对象 |
| ibase_free_result(int result) | int | 释放结果使用的内存 |
| ibase_execute(int query [, int bind_args int ...]) | int | 执行之前准备的查询 |
| ibase_free_query(int query) | int | 释放查询使用的内存 |
| ibase_timefmt(string format) | int | 设置查询返回的时间戳、日期和时间列的格式 |
| ibase_num_fields(int result) | int | 获取结果中的字段数量 |
| ibase_field_info(int result, int field_number) | array | 获取字段信息 |
| ibase_blob_add(int blob_id, string data) | int | 向创建的 blob 中添加数据 |

PHP 必须安装 `--with-ibase` 以使这些函数工作。请检查 PHP interbase 函数的当前文档，因为在编写本文时，该 API 处于频繁变动中。

![](img/245156cc770929860a3ede93c01f9981_516_0.png)

# 附录 E：PHP 函数引用

## 表 E-32 MHASH 函数

| 函数 | 返回值 | 操作 |
|---|---|---|
| mhash_count() | int | 获取可用的哈希数量 |
| mhash_get_block_size(int hash) | int | 获取哈希的块大小 |
| mhash_get_hash_name(int hash) | string | 获取哈希名称 |
| mhash(int hash, string data) | string | 使用第一个参数中的哈希对数据计算哈希函数 |

![](img/245156cc770929860a3ede93c01f9981_517_0.png)

使用这些函数需要来自 http://mhash.sourceforge.net/ 的 mhash 库。PHP 必须编译了 `--with-mash`。

mSQL 数据库是另一个开源 SQL 数据库服务器。它没有被积极维护，具有一些局限性，与 MySQL、PostgreSQL 或 Interbase 相比，是一个糟糕的选择。请注意 msqp 和 MySQL 具有几乎相同的函数集。

## 表 E-33 MSQL 函数

| 函数 | 返回值 | 操作 |
|---|---|---|
| msql_connect([string hostname[:port]], . string username [, string password]) | int | 打开到 mSQL 服务器的连接 |
| msql_pconnect([string hostname[:port]], . string username [, string password]) | int | 打开到 mSQL 服务器的持久连接 |

# 表 E-33 MSQL 函数（续表）

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| msql_close([int link_identifier]) | int | 关闭 MSQL 连接 |
| msql_select_db(string database_name [, int link_identifier]) | int | 选择 MSQL 数据库 |
| msql_create_db(string database_name [, int link_identifier]) | int | 创建 MSQL 数据库 |
| msql_drop_db(string database_name [, int link_identifier]) | | 删除（删除）MSQL 数据库 |
| msql_query(string [, int link_identifier]) | int | 向 MSQL 发送 SQL 查询 |
| msql_list_dbs([int link_identifier]) | int | 列出 MSQL 服务器上可用的数据库 |
| msql_list_tables(int link_identifier) | int | 列出 MSQL 服务器上可用的数据库（注：原文此处应为表） |
| msql_list_tables(string database_name [, int link_identifier]) | int | 列出 MSQL 服务器上可用的表 |
| msql_error([int link_identifier]) | string | 返回 MSQL 服务器的错误信息 |
| msql_result(int query [, mixed]) | int | 获取结果数据 |
| msql_num_rows(int query) | int | 获取行数 |
| msql_num_fields(int query) | int | 获取字段数 |
| msql_fetch_row(int query) | array | 以数组形式返回一行 |
| msql_fetch_object(int query [, int type]) | object | 以对象形式获取一行 |
| msql_fetch_array(int query [, int type]) | array | 获取关联数组行 |

# 附录 E：PHP 函数引用

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| msql_data_seek(int result, int offset) | int | 移动内部行指针 |
| msql_fetch_field(int result_id [, int offset]) | object | 获取查询结果中某个字段的信息 |
| msql_field_info(int result, int offset) | int | 设置结果指针到特定行 |
| msql_field_name(int result_id, int offset) | string | 获取字段名称 |
| msql_field_table(int query, int offset) | string | 获取表名 |
| msql_field_length(int result_id [, int offset]) | int | 获取 MSQL 字段的长度 |
| msql_field_type(int query, int offset) | string | 获取字段的类型 |
| msql_field_flags(int query, int offset) | string | 获取与字段关联的标志 |
| msql_free_result(int query) | int | 释放结果 |
| msql_affected_rows(int query) | int | 受影响行数 |

## 表-34 MSSQL 函数

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| msql_connect([string hostname[:port]], string username [, string password]) | int | 建立到 mSQL 服务器的连接，返回连接标识 |
| msql_pconnect([string hostname[:port]], string username [, string password]) | int | 建立到 mSQL 服务器的持久连接 |
| msql_close([int link_identifier]) | int | 关闭到 MSQL 服务器的连接 |
| msql_select_db(string database_name [, int link_identifier]) | int | 选择 MSQL 数据库 |
| msql_query(string [, int link_identifier]) | int | 在 MSQL 服务器数据库上执行 SQL 查询 |
| msql_free_result(string result_index) | int | 释放 MSQL 结果索引 |
| msql_get_last_message(void) | string | 获取 MSQL 服务器的最后消息 |
| msql_num_rows(int msql_result_index) | int | 返回从结果获取的行数 |
| msql_num_fields(int msql_result_index) | int | 返回结果中获取的字段数 |
| msql_fetch_row(int result_id) | array | 返回 result_id 指定结果集中当前行的数组形式 |
| msql_fetch_object(int result_id) | object | 获取 result_id 指定结果集中当前行的对象形式 |
| msql_fetch_array(int result_id) | array | 返回 result_id 指定结果集中当前行的关联数组 |

