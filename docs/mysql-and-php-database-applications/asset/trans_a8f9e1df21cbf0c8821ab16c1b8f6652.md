

# 第五部分：附录

## 表 E-15 字符串处理函数

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| bin2hex(string data) | string | 将数字的二进制表示转换为十六进制 |
| strspn(string str, string mask) | int | 查找完全由 mask 中存在的字符组成的起始段的长度 |
| strcspn(string str, string mask) | int | 查找完全由 mask 中不存在的字符组成的起始段的长度 |
| rtrim(string str) | string | chop() 的别名 |
| chop(string str) | string | 去除末尾空白 |
| trim(string str) | string | 去除字符串开头和结尾的空白 |
| ltrim(string str) | string | 去除字符串开头的空白 |
| wordwrap(string str [, int width [, string break]]) | string | 使用指定的宽度将缓冲区换行到指定的字符数。使用第三个参数中的字符或 '\' 进行断行。如果没有给出宽度，字符串将在 75 个字符处断开 |
| explode(string separator, string str [, int limit]) | array | 根据分隔符分割字符串并返回组件数组 |
| implode(array src, string glue) | string | 通过在项目之间插入 glue 来连接数组元素并返回一个字符串 |
| join(array src, string glue) | string | implode() 的别名 |
| strtok([string str, string token]) | string | 对字符串进行分词 |
| strupper(string str) | string | 将字符串转换为大写 |
| strtolower(string str) | string | 将字符串转为小写 |
| basename(string path) | string | 返回路径的文件名部分 |

## 附录 E：PHP 函数参考 459

| 函数 | 返回值 | 操作 |
| --- | --- | -- |
| dirname(string path) | string | 返回路径的目录名部分 |
| strstr(string haystack, string needle) | string | 在另一个字符串中找到字符串的第一次出现 |
| strchr(string haystack, string needle) | string | strstr() 的别名 |
| strstr(string haystack, string needle) | string | 在另一个字符串中找到字符串的第一次出现（不区分大小写） |
| strpos(string needle [, int offset]) | int | 找到字符串在另一个字符串中第一次出现的位置 |
| strrpos(string haystack, string needle) | int | 找到字符在另一个字符串中最后出现的位置 |
| strchr(string haystack, string needle) | string | 找到字符在另一个字符串中最后出现的位置 |
| chunk_split(string str [, int hunklen [, string ending]]) | string | 通过插入 \n（默认每 76 个字符一次）来分割行。可以指定分块的长度和分隔字符串 |
| substr(string str, int start [, int length]) | string | 根据指定的起始位置和长度返回字符串的一部分。如果长度为负数，则位置从字符串末尾确定 |
| substr_replace(string str, string repl, int start [, int length]) | string | 用另一个字符串替换字符串的部 |
| quotemeta(string str) | string | 返回一个字符串，在以下字符前加上反斜杠：.+\*?\[\]\(\) |
| ord(string character) | int | 返回字符的 ASCII 值 |
| chr(int ascii) | string | 将 ASCII 代码转换为字符 |

## 表 E-15 字符串处理函数（续）

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| ucfirst(string str) | string | 将字符串的首字母转为大写 |
| ucwords(string str) | string | 将字符串中每个单词的首字母转为大写 |
| strtr(string str, string from, string to) | string | 翻译 str 中的字符 |
| strrev(string str) | string | 反转字符串 |
| similar_text(string str1, string str2 [, int]) | int | 使用第三个参数计算两个字符串的相似度 |
| addcslashes(string str, charset) | string | 使用字符集对字符串进行转义 |
| addslashes(string str) | string | 转字符串中的单引号、双引号和反斜杠 |
| stripslashes(string str) | string | 去除字符串中的反斜杠 |
| str_replace(string needle, string haystack) | string | 替换 haystack 中所有 needle 出现的位置 |
| Hebrew(string str) | string | 将 Hebrew 转换为视觉文本 |
| nl2br(string str) | string | 在换行符后插入 HTML 行 |
| strip_tags(string str) | string | 去除 HTML 标签 |
| setlocale(string category, locale) | string | 设置区域信息 |

## 附录 E：PHP 函数

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| parse_str) | 解析 GET/POST 数据 |
| str_repeat(string input, int mult) | string | input 重复 mult 次 |
| str_count(string haystack, string needle) | int | needle 在 haystack 中出现的次数 |
| strnatcmp(string s1, string s2) | int | 使用自然顺序比较字符串的结果 |
| strnatcase(string s1, string s2) | int | 使用自然顺序不区分大小写比较字符串的结果 |
| str_pad(string input, int length [, pad]) | string | 在左侧填充 input |
| sscanf(string format) | | 实现 sscanf |

## 表 E-16 URL 函数

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| urlencode(string str) | string | 编码字符串 |
| urldecode(string str) | string | 解码 URL 字符串 |
| rawurlencode(string str) | string | 编码字符串。参见与 urlencode 的区别 |
| rawurldecode(string str) | string | 解码 URL 字符串 |

## 表 E-17 变量序列化函数

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| serialize(mixed variable) | string | 返回变量的字符串表示（可以反序列） |
| unserialize(string variable_representation) | mixed | 取字符串表示重建变量 |

## 表 E-18 杂项函数

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| ip2long(string ip_address) | int | 将包含 (IPv4) Internet点地址的字符串转换为整数 |
| long2ip(int proper_address) | string | 将 (IPv4) 网络地址转换为点格式字符串 |
| getenv(string varm) | string | 获取环境变量的值 |
| putenv(string setting) | void | 使用格式 putenv("ENV_VAR=$foo"); 设置环境变量的值 |

| 函数 | 返回值 | 操作 |
| --- | --- | --- |
| flush(void) | void | 刷新输出缓冲区 |
| sleep(int seconds) | void | 等待指定的秒数 |
| usleep(int micro seconds) | void | 等待指定的微秒 |
| get_current_user(void) | string | 获取当前 脚本的所有者名称 |
| get_cfg_var(string option_name) | string | 获取 PHP 配置选项的值 |
| is_resource(mixed var) | bool | 如果变量是资源则返回真 |
| error_log(string message, int message_type string destination [, string extra_headers]) | int | 将错误发送到错误日志、TCP端口或文件 |
| call_user_func(string function_name [, mixed parameter]) | mixed | 调用作为参数的用户函数 |
| call_user_method(string method_name, object object [, mixed parameter ...]) | mixed | 在特定对象上调用用户方法，第一个参数是方法名，第二个参数是对象，后续参数是参数 |
| register_shutdown_function(function_name) | void | 注册在请求终止时调用的用户函数 |
| highlight_file(string file_name) | void | 输出带有语法高亮的 PHP 源文件 |
| highlight_string(string string) | void | 字符串语法高亮 |
| ini_get(string varname) | string | 获取配置选项 |
| ini_set(string varname, string value) | string | 设置配置选项，失败时返回 false，成功时返回旧值的字符串 | 

