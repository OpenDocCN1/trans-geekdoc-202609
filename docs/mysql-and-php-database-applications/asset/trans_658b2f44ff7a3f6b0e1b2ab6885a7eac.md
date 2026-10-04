

# 附录 E：PHP 函数引用

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| fileowner(string filename) | int | 获取文件所有者的 userid |
| filegroup(string filename) | int | 获取文件的 groupid |
| fileat(string filename) | int | 获取文件的最后访问时间 |
| filetime(string filename) | int | 获取文件的最后修改时间 |
| filectime(string filename) | int | 获取文件的 inode 修改时间 |
| filetype(string filename) | string | 获取文件类型 |
| is_writable(string filename) | int | 如果文件可写则返回 true |
| is_readable(string filename) | int | 如果文件可读则返回 true |
| is_executable(string filename) | int | 如果文件可执行则返回 true |
| is_file(string filename) | int | 如果文件是普通文件则返回 true |
| is_dir(string filename) | int | 如果文件是目录则返回 true |
| is_link(string filename) | int | 如果文件是符号链接则返回 true |
| file_exists(string filename) | bool | 如果文件名存在则返回 true |
| lstat(string filename) | array | 提供有关文件或符号链接的信息。返回的数组包含以下元素：设备、inode；保护模式；链接数；所有者用户 id；所有者组 id；如果 inode 是设备则设备类型；字节大小；最后访问时间；修改时间；最后更改时间；用于文件大小 I/O 的块大小；分配的块数 |
| stat(string filename) | array | 提供有关文件的信息，与 lstat 相同 |

# 第五部分：附录

# 表 E-7 执行函数

| 函数 | 返回 | 作用 |
|---|---|---|
| exec(string command [, array output [, int return_value]]) | int | 执行外部程序 |
| system(string command [. int return_value]) | int | 执行外部程序并显示输出 |
| passthru(string command [. int return_value]) | void | 执行外部程序并绘制原始输出。通常与类似 PBMPlus 等工具使用 |
| escapeshellcmd(string command) | string | 转义 shell 元元字符 |

# 表 E-8 文件操作函数

| 函数 | 返回 | 作用 |
|---|---|---|
| flock(int fp, int operation [. int wouldblock]) | bool | 锁定文件使其其他其他 PHP 脚本访问。锁定不会阻止其他进程打开文件 |
| get_meta_tags(string filename [, int use_include_path]) | array | 从文件中提取所有的 <meta> 标签内容并返回数组 |
| file(string filename [, int use_include_path]) | array | 将文件读取到数组中，每行作为一个元素 |
| tempnam(string dir, | string | 在字符串前缀)/目录中创建唯一文件名 |
| tmpfile(void) | int | 创建临时文件，该文件将在调用 fclose() 函数后或在脚本结束时自动删除 |
| fopen(string filename, string mode [, int use_include_path]) | int | 打开文件或 URL 并返回文件指针 |

# 附录 E：PHP 函数引用 453

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| fclose(int fp) | int | 关闭已打开的文件指针 |
| open(string command, string mode) | int | 执行命令并对其打开一个读或写管道 |
| pclose(int fp) | int | 关闭由 open() 打开的文件指针 |
| feof(int fp) | int | 测试指针是否到达文件末尾 |
| set_socket_blocking(int socket_descriptor, int mode) | int | 在套接上设置阻塞/非阻塞模式 |
| socket_set_timeout(int socket_descriptor, int seconds, microseconds) | bool | 设置套接读取超时为秒+微秒 |
| socket_get_status(resource socket_descriptor) | array | 返回描述套接状态的数组。数组包含四个元素：timed_out (bool), eof (bool), 和 unbound bytes (int) |
| fgets(int fp, length) | string | 从文件指针获取一行 |
| fgetc(int fp) | string | 从文件指针获取一个字符 |
| fgets(int fp, length, [. string allowable_tags]) | string | 从文件指针获取一行并去除 HTML 标签 |
| sscanf(string str, string format [, string ...])]) | mixed | 使用指定的格式格式化文件 |
| fwrite(int fp, string str, [int length]) | int | 实现二进制安全的的文件写入 |
| fflush(int fp) | int | 刷新输出 |
| set_file_buffer(int fp, int buffer) | int | 设置文件缓冲区；默认大小为 8 kb |
| rewind(int fp) | int | 将文件指针的位置移动到文件开头 |
| ftell(int fp) | int | 获取文件指针的读/写位置 |

继续

# 表 E-8 文件操作函数（继续）

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| fseek(int fp, int offset [, int whence]) | int | 寻求文件指针的位置 |
| mkdir(string pathname, int mode) | int | 创建目录 |
| rmdir(string dirname) | int | 删除目录 |
| readfile(string filename, [. int use_include_path]) | int | 读取文件并输出 |
| umask([int]) | int | 设置 umask。详情请见 umask 帮助页 |
| passthru(int fp) | int | 输出剩余数据 |
| rename(string old_name, string new_name) | int | 重命名文件 |
| unlink(string filename) | int | 删除文件 |
| ftruncate(int fp, int size) | int | 将文件截断到指定的大小 |
| fstat(int fp) | int | 返回与 stat（之前描述）相同的信息 |
| copy(string source, string destination) | int | 复制 |
| fread(int fp, length) | int | 二进制安全的读取读取 |
| getcsv(int fp, length) | array | 从文件指针获取行 |
| realpath(string path) | string | 返回解析后的路径 |

# 附录 E：PHP 函数引用

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| sprintf(string format, mixed arg1 [, mixed ...]) | string | 返回格式化字符串 |
| printf(string format, mixed arg1 [, mixed ...]) | int | 输出格式化字符串 |
| print_r(mixed var) | void | 输出变量的信息 |
| var_dump(mixed var) | void | 输出变量的表示 |

表 E-10 HTTP 函数

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| header(string header) | void | 发送原始头 |
| setcookie(string name [, string value [, int expires [, string secure]]]) | void | 设置 cookie |
| headers_sent(void) | int | 如果头已发送则返回 true；否则返回 false |

表 E-11 HTML 函数

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| htmlspecialchars(string string) | string | 将特殊字符（和、双引号、小于、大于）转换为 HTML 实体 |
| htmlntities(string string) | string | 将所有相应的字符转换为 HTML 实体 |
| get_html_translation_table([int whichone]) | array | 返回 htmlspecialchars 和 htmlntities 使用的翻译表 |

表 E-12 邮件函数

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| mail(string to, string subject, string_ headers[]) | int | 发送电子邮件 |

表 E-13 随机数函数

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| srand(int seed) | void | 设置随机数生成器 |
| rand(int min, int max) | int | 返回随机数 |
| getrandmax(void) | int | 返回随机数可能具有的最大值 |
| mt_srand(int seed) | void | 设置梅森旋转算法 |
| mt_rand([int min, int max]) | int | 返回来自梅森旋转的随机数 |
| mt_getrandmax(void) | int | 返回来自梅森旋转的随机数可能具有的最大值 |

表 E-14 正则表达式函数

| 函数 | 返回 | 作用 |
| --- | --- | --- |
| ereg(string pattern, string string [, array registers]) | int | 执行正则表达式匹配 |
| erei(string pattern, string string [, array registers]) | int | 不区分大小写的正则表达式匹配 |
| ere_replace(string pattern, string replacement, string string) | string | 替换正则表达式 |
| eregi_replace(string pattern, string replacement, string string) | string | 执行不区分大小写的替换正则表达式 |
| split(string pattern, string string [, int limit]) | array | 用正则表达式将字符串分割为数组 |
| spliti(string pattern, string string [, int limit]) | array | 用不区分大小写的正则表达式将字符串分割为数组 |
| sql_regcase(string string) | string | 用于不区分大小写匹配的正则表达式 |

