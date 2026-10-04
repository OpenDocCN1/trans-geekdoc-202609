

# 附录 E：PHP 函数参考 495

| 函数 | 返回 | 作用 |
| :--- | :--- | :--- |
| mssql_field_name(int result_id [, int offset]) | string | 返回由 result_id 指定的结果集中由 offset 指定字段名称 |
| mssql_field_type(int result_id [, int offset]) | string | 返回字段类型 |
| mssql_field_seek(int result_id, int offset) | bool | 将指针移动到指定的字段偏移 |
| mssql_result(int result_id, int row, mixed field) | string | 返回 MS-SQL 结果集中一个单元格的内容 |
| mssql_min_error_severity(int severity) | void | 设置最低错误严重性 |
| mssql_min_message_severity(int severity) | void | 设置最低消息严重性 |

# E-35 兼容 PERL 的正则表达式函数

| 函数 | 返回 | 作用 |
| :--- | :--- | :--- |
| preg_match(string pattern, string subject [, array subpatterns]) | int | 执行 Perl 风格正则表达式匹配 |
| preg_match_all(string pattern, string subject, array subpatterns [, int order]) | int | 执行 Perl 风格全局正则表达式匹配 |
| preg_replace(string regex, string replace, string|array subject [, int limit]) | string | 执行 Perl 风格正则表达式替换 |
| preg_split(string pattern, string subject [, int limit [, int flags]]) | array | 使用 perl 风格正则表达式作为分隔符将字符串分割为数组

# 表 E-35 兼容 PERL 的正则表达式函数（续）

| 函数 | 返回 | 作用 |
| :--- | :--- | :--- |
| preg_quote(string str, string delim_char) | string | 转义正则表达式字符以及一个可选字符 |
| preg_grep(string regex, array input) | array | 搜索数组并返回匹配正则的项 |

# 表 E-36 POSTGRES 函数

| 函数 | 返回 | 作用 |
| :--- | :--- | :--- |
| pg_connect([string connection_string] | [string host, string options [, string tty.]]) string database | int | 打开一个 PostgreSQL 连接 |
| pg_pconnect([string connection_string] | [string host, string options [, string tty.]]) string | int | 打开一个持久的 PostgreSQL 连接 |
| pg_close([int connection]) | bool | 关闭 PostgreSQL 连接 |
| pg_dbname([int connection]) | string | 获取数据库名称 |
| pg_errormessage([int connection]) | string | 获取错误消息字符串 |
| pg_options([int connection]) | string | 获取与连接相关的选项 |
| pg_port([int connection]) | int | 返回与连接相关的端口号 |
| pg_tty([int connection]) | string | 返回与连接相关的 tty 名称 |
| pg_host([int connection]) | string | 返回与连接相关的主机 |

# 附录 E：PHP 函数参考

| 函数 | 返回 | 作用 |
| :--- | :--- | :--- |
| pg_exec([int connection,] string query) | int | 执行查询 |
| pg_numrows(int result) | int | 返回结果中的行数 |
| pg_numfields(int result) | int | 返回结果中的字段数 |
| pg_cmdtples(int result) | int | 返回受影响的元组数 |
| pg_fieldname([int connection,] int number) | string | 返回名称 |
| pg_fieldsize([int connection,] int number) | int | 返回大小 |
| pg_fieldtype([int connection,] int number) | string | 返回类型 |
| pg_fieldnum([int connection,] string name) | int | 返回数字 |
| pg_result([int connection], string query) | mixed | 返回结果 |
| pg_fetch_row([int connection]) | array | 获取行 |
| pg_fetch_array([int connection]) | array | 获取数组 |
| pg_fetch_object([int connection]) | object | 获取对象 |
| pg_fetch_all([int connection]) | array | 获取所有行 |
| pg_fetch_assoc([int connection]) | array | 获取关联数组 |
| pg_fetch_result([int connection]) | mixed | 获取结果 |
| pg_query_status([int connection]) | int | 返回查询状态 |
| pg_query_result([int connection]) | resource | 返回查询结果 |
| pg_query_error([int connection]) | string | 返回查询错误 |
| pg_query_warning([int connection]) | string | 返回查询警告 |
| pg_prepare([int connection], string name, string query) | bool | 准备语句 |
| pg_execute([int connection], string name, array params) | bool | 执行准备的语句 |
| pg_get_prepared([int connection], string name) | resource | 获取准备的语句 |
| pg_remove_prepared([int connection], string name) | bool | 移除准备的语句 |
| pg_prepare([int connection]) | bool | 开始事务 |
| pg_commit([int connection]) | bool | 提交事务 |
| pg_rollback([int connection]) | bool | 回滚事务 |
| pg_transaction_status([int connection]) | int | 返回事务状态 |
| pg_get_error([int connection]) | string | 获取错误 |
| pg_get_warning([int connection]) | string | 获取警告 |
| pg_get_result([int connection]) | resource | 获取结果 |
| pg_set_error([int connection], string error) | void | 设置错误 |
| pg_set_warning([int connection], string warning) | void | 设置警告 |
| pg_escape(int connection) | |
| pg_escape_string(int connection, string input) | string | 转义字符串 |
| pg_escape_literal(int connection, string input) | string | 转义字量 |
| pg_escape_query(int connection, string query) | string | 转义查询 |
| pg_escape_conn_string(int connection, string input) | string | 转义连接特定的字符串 |
| pg_get_client_encoding([int connection]) | string | 获取客户端编码 |
| pg_set_client_encoding([int connection], string encoding) | string | 设置客户端编码 |
| pg_get_server_encoding([int connection]) | string | 获取服务器编码 |
| pg_set_server_encoding([int connection], string encoding) | string | 设置服务器编码 |
| pg_get_datestyle([int connection]) | string | 获取日期格式 |
| pg_set_datestyle([int connection], string datestyle) | string | 设置日期格式 |
| pg_get_timezone([int connection]) | string | 获取时区 |
| pg_set_timezone([int connection], string timezone) | string | 设置时区 |
| pg_get_client_encoding([int connection]) | string | 获取客户端编码 |
| pg_set_client_encoding([int connection], string encoding) | string | 设置客户端编码 |
| pg_get_variable([int connection], string name) | mixed | 获取变量 |
| pg_set_variable([int connection], string name, mixed value) | bool | 设置变量 |
| pg_get_config([int connection], string name) | string | 获取配置 |
| pg_set_config([int connection], string name, string value) | bool | 设置配置 |
| pg_get_option([int connection], string name) | string | 获取选项 |
| pg_set_option([int connection], string name, string value) | bool | 设置选项 |
| pg_get_setting([int connection], string name) | string | 获取设置 |
| pg_set_setting([int connection], string name, string value) | bool | 设置设置 |
| pg_get_property([int connection], string name) | string | 获取属性 |
| pg_set_property([int connection], string name, string value) | bool | 设置属性 |
| pg_get_parameter([int connection], string name) | string | 获取参数 |
| pg_set_parameter([int connection], string name, string value) | bool | 设置参数 |
| pg_get_variable([int connection], string name) | string | 获取变量 |
| pg_set_variable([int connection], string name, string value) | bool | 设置变量 |
| pg_get_locks([int connection]) | array | 获取锁 |
| pg_lock([int connection], array locks) | bool | 设置锁 |
| pg_remove_lock([int connection], array locks) | bool | 移除锁 |
| pg_get_stats([int connection]) | array | 获取统计 |
| pg_add_stat([int connection], array stat) | bool | 添加统计 |
| pg_get_notifications([int connection]) | array | 获取通知 |
| pg_notify([int connection], string channel, string payload) | bool | 发送通知 |
| pg_listen([int connection], string channel) | bool | 监听通道 |
| pg_unlisten([int connection], string channel) | bool | 停止监听通道 |
| pg_get_advisory_locks([int connection]) | array | 获取建议性锁 |
| pg_set_advisory_lock([int connection], array locks) | bool | 设置建议性锁 |
| pg_unlock_advisory_lock([int connection], array locks) | bool | 移除建议性锁 |
| pg_try_set_advisory_lock([int connection], array locks) | bool | 尝试设置建议性锁 |
| pg_try_unlock_advisory_lock([int connection], array locks) | bool | 尝试解锁建议性锁 |
| pg_get_transaction_locks([int connection]) | array | 获取事务锁 |
| pg_set_transaction_lock([int connection], array locks) | bool | 设置事务锁 |
| pg_unlock_transaction_lock([int connection], array locks) | bool | 移除事务锁 |
| pg_try_set_transaction_lock([int connection], array locks) | bool | 尝试设置事务锁 |
| pg_try_unlock_transaction_lock([int connection], array locks) | bool | 尝试解锁事务锁 |
| pg_get_large_locks([int connection]) | array | 获取大锁 |
| pg_set_large_lock([int connection], array locks) | bool | 设置大锁 |
| pg_unlock_large_lock([int connection], array locks) | bool | 移除大锁 |
| pg_try_set_large_lock([int connection], array locks) | bool | 尝试设置大锁 |
| pg_try_unlock_large_lock([int connection], array locks) | bool | 尝试解锁大锁 |
| pg_get_table_locks([int connection]) | array | 获取表锁 |
| pg_set_table_lock([int connection], array locks) | bool | 设置表锁 |
| pg_unlock_table_lock([int connection], array locks) | bool | 移除表锁 |
| pg_try_set_table_lock([int connection], array locks) | bool | 尝试设置表锁 |
| pg_try_unlock_table_lock([int connection], array locks) | bool | 尝试解锁表锁 |
| pg_get_index_locks([int connection]) | array | 获取索引锁 |
| pg_set_index_lock([int connection], array locks) | bool | 设置索引锁 |
| pg_unlock_index_lock([int connection], array locks) | bool | 移除索引锁 |
| pg_try_set_index_lock([int connection], array locks) | bool | 尝试设置索引锁 |
| pg_try_unlock_index_lock([int connection], array locks) | bool | 尝试解锁索引锁 |
| pg_get_row_locks([int connection]) | array | 获取行锁 |
| pg_set_row_lock([int connection], array locks) | bool | 设置行锁 |
| pg_unlock_row_lock([int connection], array locks) | bool | 移除行锁 |
| pg_try_set_row_lock([int connection], array locks) | bool | 尝试设置行锁 |
| pg_try_unlock_row_lock([int connection], array locks) | bool | 尝试解锁行锁 |
| pg_get_page_locks([int connection]) | array | 获取页锁 |
| pg_set_page_lock([int connection], array locks) | bool | 设置页锁 |
| pg_unlock_page_lock([int connection], array locks) | bool | 移除页锁 |
| pg_try_set_page_lock([int connection], array locks) | bool | 尝试设置页锁 |
| pg_try_unlock_page_lock([int connection], array locks) | bool | 尝试解锁页锁 |
| pg_get_block_locks([int connection]) | array | 获取块锁 |
| pg_set_block_lock([int connection], array locks) | bool | 设置块锁 |
| pg_unlock_block_lock([int connection], array locks) | bool | 移除块锁 |
| pg_try_set_block_lock([int connection], array locks) | bool | 尝试设置块锁 |
| pg_try_unlock_block_lock([int connection], array locks) | bool | 尝试解锁块锁 |
| pg_get_function_locks([int connection]) | array | 获取函数锁 |
| pg_set_function_lock([int connection], array locks) | bool | 设置函数锁 |
| pg_unlock_function_lock([int connection], array locks) | bool | 移除函数锁 |
| pg_try_set_function_lock([int connection], array locks) | bool | 尝试设置函数锁 |
| pg_try_unlock_function_lock([int connection], array locks) | bool | 尝试解锁函数锁 |
| pg_get_trigger_locks([int connection]) | array | 获取触发器锁 |
| pg_set_trigger_lock([int connection], array locks) | bool | 设置触发器锁 |
| pg_unlock_trigger_lock([int connection], array locks) | bool | 移除触发器锁 |
| pg_try_set_trigger_lock([int connection], array locks) | bool | 尝试设置触发器锁 |
| pg_try_unlock_trigger_lock([int connection], array locks) | bool | 尝试解锁触发器锁 |
| pg_get_constraint_locks([int connection]) | array | 获取约束锁 |
| pg_set_constraint_lock([int connection], array locks) | bool | 设置约束锁 |
| pg_unlock_constraint_lock([int connection], array locks) | bool | 移除约束锁 |
| pg_try_set_constraint_lock([int connection], array locks) | bool | 尝试设置约束锁 |
| pg_try_unlock_constraint_lock([int connection], array locks) | bool | 尝试解锁约束锁 |
| pg_get_view_locks([int connection]) | array | 获取视图锁 |
| pg_set_view_lock([int connection], array locks) | bool | 设置视图锁 |
| pg_unlock_view_lock([int connection], array locks) | bool | 移除视图锁 |
| pg_try_set_view_lock([int connection], array locks) | bool | 尝试设置视图锁 |
| pg_try_unlock_view_lock([int connection], array locks) | bool | 尝试解锁视图锁 |
| pg_get_sequence_locks([int connection]) | array | 获取序列锁 |
| pg_set_sequence_lock([int connection], array locks) | bool | 设置序列锁 |
| pg_unlock_sequence_lock([int connection], array locks) | bool | 移除序列锁 |
| pg_try_set_sequence_lock([int connection], array locks) | bool | 尝试设置序列锁 |
| pg_try_unlock_sequence_lock([int connection], array locks) | bool | 尝试解锁序列锁 |

