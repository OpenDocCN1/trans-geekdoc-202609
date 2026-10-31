
| 函数 | 返回值 | 动作 |
|---|---|---|
| pg_exec([int connection,] string query) | int | 执行查询 |
| pg_numrows(int result) | int | 返回结果中的行数 |
| pg_numfields(int result) | int | 返回结果中的字段数 |
| pg_cmdtuples(int result) | int | 返回受影响的元组数 |
| pg_fieldname(int result, int field_number) | string | 返回字段的名称 |
| pg_fieldsize(int result, int field_number) | int | 返回字段的内部大小 |
| pg_fieldtype(int result, int field_number) | string | 返回给定字段的类型名称 |
| pg_fieldnum(int result, string field_name) | int | 返回命名字段的字段编号 |
| pg_result(int result, int row_number, mixed field_name) | mixed | 从结果标识符返回值 |
| pg_fetch_row(int result, int row) | array | 以枚举数组形式获取一行 |
| pg_fetch_array(int result, int row [, int result_type]) | array | 以数组形式获取一行 |
| pg_fetch_object(int result, int row [, int result_type]) | object | 以对象形式获取一行 |
| pg_fieldprntlen(int result, int row, mixed field_name_or_number) | int | 返回打印长度 |
| pg_fieldisnull(int result, int row, mixed field_name_or_number) | int | 测试字段是否为 NULL |

## 表 E-36 PostgreSQL 函数（续）

| 函数 | 返回值 | 动作 |
|---|---|---|
| pg_freeresult(int result) | int | 释放结果内存 |
| pg_getlastoid(int result) | int | 返回最后一个对象标识符 |
| pg_trace(string filename [, string mode [, resource connection]]) | bool | 启用 PostgreSQL 连接的跟踪 |
| pg_untrace([int connection]) | bool | 禁用 PostgreSQL 连接的跟踪 |
| pg_locreate(int connection) | int | 创建大对象 |
| pg_lounlink([int connection,] int large_obj_id) | void | 删除大对象 |
| pg_loopen([int connection,] int objoid, string mode) | int | 打开大对象并返回 fd |
| pg_loclose(int fd) | void | 关闭大对象 |
| pg_loread(int fd, int len) | string | 读取大对象 |
| pg_lowrite(int fd, string buf) | int | 写入大对象 |
| pg_loreadall(int fd) | void | 读取大对象并直接发送到浏览器 |
| pg_loimport(string filename [, resource connection]) | int | 从文件系统直接导入大对象 |
| pg_loexport(int objoid, string filename [, resource connection]) | bool | 直接将大对象导出到文件系统 |
| pg_setclientencoding ([int connection,] string encoding) | int | 设置客户端编码 |
| pg_clientencoding ([int connection]) | string | 获取当前客户端编码 |

![](img/de0823012275cf4ceebdb822a56e6b71_525_0.png)

使用这些函数要求 PHP 编译时带 --with-postgres。

## 表 E-37 会话函数

| 函数 | 返回值 | 动作 |
|---|---|---|
| session_set_cookie_params(int lifetime [, string path [, string domain]]) | void | 设置会话 cookie 参数 |
| session_get_cookie_params(void) | array | 返回会话 cookie 参数 |
| session_name([string newname]) | string | 返回当前会话名称；如果给出 newname，则会话名称将被替换为 newname |
| session_module_name([string newname]) | string | 返回用于访问会话数据的当前模块名称；如果给出 newname，则模块名称将被替换为 newname |
| session_set_save_handler(string open, string close, string read, string write, string destroy, string gc) | void | 设置用户级函数 |
| session_save_path([string newname]) | string | 返回传递给 module_name 的当前保存路径；如果给出 newname，则保存路径将被替换为 newname |
| session_id([string newid]) | string | 返回当前会话 ID；如果给出 newid，则会话 ID 将被替换为 newid |
| session_register(mixed var_names [, mixed ...]) | bool | 将变量名添加到会话存储的变量列表中 |

续

## 表 E-37 会话函数（续）

| 函数 | 返回值 | 动作 |
|---|---|---|
| `session_unregister(string varname)` | bool | 从会话存储的变量列表中移除 `varname` |
| `session_is_registered(string varname)` | bool | 检查变量是否已在会话中注册 |
| `session_encode(void)` | string | 序列化当前设置并返回序列化表示 |
| `session_decode(string data)` | bool | 反序列化数据并重新初始化变量 |
| `session_start(void)` | bool | 开始会话—重新初始化冻结变量、注册浏览器等 |
| `session_destroy(void)` | bool | 销毁当前会话及其所有关联数据 |
| `session_unset(void)` | void | 取消设置所有已注册变量 |

![](img/de0823012275cf4ceebdb822a56e6b71_526_0.png)

会话函数在第 14 章中有更详细的描述。

## 表 E-38 DNS 函数

| 函数 | 返回值 | 动作 |
|---|---|---|
| `gethostbyaddr(string ip_address)` | string | 获取给定 IP 地址对应的 Internet 主机名 |
| `gethostbyname(string hostname)` | string | 获取给定 Internet 主机名对应的 IP 地址 |
| `gethostbyname1(string hostname)` | array | 返回给定主机名解析到的 IP 地址列表 |

| 函数 | 返回值 | 动作 |
|---|---|---|
| checkdnsrr(string host [, string type]) | int | 检查与给定 Internet 主机名或 IP 地址对应的 DNS 记录 |
| getmxrr(string hostname, array mxhosts [, array weight]) | int | 获取与给定 Internet 主机名对应的 MX 记录 |

## 表 E-39 数学函数

| 函数 | 返回值 | 动作 |
|---|---|---|
| abs(int number) | int | 返回该数字的绝对值 |
| ceil(double number) | int | 返回该数字的下一个最高整数值 |
| floor(double number) | int | 返回该数字的下一个最低整数值 |
| round(double number [, int precision]) | double | 返回四舍五入到指定精度的数字 |
| sin(double number) | double | 返回该数字（弧度）的正弦值 |
| cos(double number) | double | 返回该数字（弧度）的余弦值 |
| tan(double number) | double | 返回该数字（弧度）的正切值 |
| asin(double number) | double | 返回该数字的反正弦值（弧度） |
| acos(double number) | double | 返回该数字的反余弦值（弧度） |
| atan(double number) | double | 返回该数字的反正切值（弧度） |

## 表 E-39 数学函数（续）

| 函数 | 返回值 | 动作 |
|---|---|---|
| atan2(double y, double x) | double | 返回 y/x 的反正切值，其结果象限由 y 和 x 的符号决定 |
| pi(void) | double | 返回 pi 的近似值 |
| pow(double base, double exponent) | double | 返回底数以指数为幂的值 |
| exp(double number) | double | 返回 e 的 number 次幂 |
| log(double number) | double | 返回该数字的自然对数 |
| log10(double number) | double | 返回该数字以 10 为底的对数 |
| sqrt(double number) | double | 返回该数字的平方根 |
| deg2rad(double number) | double | 将角度数转换为弧度等价值 |
| rad2deg(double number) | double | 将弧度数转换为角度等价值 |
| bindec(string binary_number) | int | 返回二进制数的十进制等价值 |
| hexdec(string hexadecimal_number) | int | 返回十六进制数的十进制等价值 |
| octdec(string octal_number) | int | 返回八进制字符串的十进制等价值 |
| decbin(int decimal_number) | string | 返回包含该数字二进制表示的字符串 |
| decoct(int decimal_number) | string | 返回包含给定数字八进制表示的字符串 |
| dechex(int decimal_number) | string | 返回包含给定数字十六进制表示的字符串 |
