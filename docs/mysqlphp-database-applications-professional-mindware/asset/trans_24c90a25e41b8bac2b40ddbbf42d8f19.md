
| GRANT ALL PRIVILEGES ON my_test.* TO 'jayg'@'localhost' |
+----------------------------------------------------------+
集合中 1 行 (0.00 秒)

## 重新加载授权

授权表在 MySQL 守护进程启动时被加载到内存中。未使用 grant 命令对授权表所做的更改，在重启程序或使用 flush 命令通知 MySQL 重新加载表之前不会生效。

只需运行：

```
flush privileges
```

## 附录 E

### PHP 函数参考

到目前为止，PHP 包含的函数数量多到不可能全部列在这本书中，而且函数列表每天都在增长。表 E-1 至 E-43 仅列出了其中部分可用函数。请访问在线手册 www.php.net/manual 以查看最新列表。

### 表 E-1 PHP 信息函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| phpinfo(void) | void | 输出有关 PHP 和当前请求的实用信息页面 |
| phpversion(void) | string | 返回当前 PHP 版本 |
| phpcredits(void) | void | 打印参与 PHP 项目的人员名单 |

### 表 E-2 变量类型函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| intval(mixed var [, int base]) | int | 使用可选的 base 将变量转换为整数值 |
| doubleval(mixed var) | double | 获取变量的双精度值 |
| strval(mixed var) | string | 获取变量的字符串值 |
| gettype(mixed var) | string | 返回变量的类型 |

*继续*

### 表 E-2 变量类型函数（续）

| 函数 | 返回值 | 作用 |
|---|---|---|
| `settype(string var, string type)` | int | 设置变量的类型。转换成功时返回 1 |
| `is_bool(mixed var)` | bool | 如果变量是布尔值则返回 true |
| `is_long(mixed var)` | bool | 如果变量是长整型（整数）则返回 true |
| `is_double(mixed var)` | bool | 如果变量是双精度浮点数则返回 true |
| `is_string(mixed var)` | bool | 如果变量是字符串则返回 true |
| `is_array(mixed var)` | bool | 如果变量是数组则返回 true |
| `is_object(mixed var)` | bool | 如果变量是对象则返回 true |
| `is_numeric(mixed value)` | bool | 如果值是数字或数字字符串则返回 true |

### 表 E-3 引号设置函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| `set_magic_quotes_runtime(int new_setting)` | int | 设置 magic_quotes_runtime 的当前活动配置设置并返回之前的设置 |
| `get_magic_quotes_runtime(void)` | int | 获取 magic_quotes_runtime 的当前活动配置设置 |
| `get_magic_quotes_gpc(void)` | int | 获取 magic_quotes_gpc 的当前活动配置设置 |

### 表 E-4 日期时间函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| time(void) | int | 返回当前 UNIX 时间戳 |
| mktime(int hour, int min, int sec, int mon, int day, int year) | int | 为指定日期组合 UNIX 时间戳 |
| gmktime(int hour, int min, int sec, int mon, int day, int year) | int | 获取 GMT 日期对应的 UNIX 时间戳 |
| date(string format [, int timestamp]) | string | 格式化时间/日期 |
| gmdate(string format [, int timestamp]) | string | 格式化 GMT/CUT 日期/时间 |
| localtime([int timestamp [, bool associative_array]]) | array | 如果 associative_array 参数设为 1，则以关联数组形式返回 C 系统调用 localtime 的结果；否则返回普通数组 |
| getdate([int timestamp]) | array | 获取日期/时间信息 |
| checkdate(int month, int day, int year) | bool | 如果是有效日期则返回 1 |
| strftime(string format [, int timestamp]) | string | 根据本地设置格式化本地时间/日期 |
| gmstrftime(string format [, int timestamp]) | string | 根据本地设置格式化 GMT/CUT 时间/日期 |
| strtotime(string time, int now) | int | 将日期和时间的字符串表示转换为时间戳。可接受大多数常见日期格式的字符串。例如 YYYY-MM-DD 和 MM/DD/YYYY |
| microtime(void) | string | 返回包含当前秒数和微秒数的字符串 |
| gettimeofday(void) | array | 以数组形式返回当前时间 |
| getrusage([int who]) | array | 返回来自 Unix 命令 getrusage 的使用统计数组。请参阅 Unix 手册页了解更多详细信息 |

### 表 E-5 目录函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| `opendir(string path)` | int | 打开目录并返回 dir_handle |
| `dir(string directory)` | class | 返回一个具有三个方法（read、rewind 和 close）和两个属性（handle 和 path）的对象 |
| `closedir([int dir_handle])` | void | 关闭由 dir_handle 标识的目录连接 |
| `chdir(string directory)` | int | 更改当前目录 |
| `getcwd(void)` | string | 获取当前目录 |
| `rewinddir([int dir_handle])` | void | 将 dir_handle 重新定位到开头 |
| `readdir([int dir_handle])` | string | 从 dir_handle 读取目录条目 |

### 表 E-6 文件系统函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| `diskfreespace(string path)` | double | 获取路径所在文件系统的可用磁盘空间，单位为字节 |
| `chown(string filename, mixed user)` | bool | 更改文件所有者。成功返回 TRUE，否则返回 FALSE |
| `chgrp(string filename, mixed group)` | bool | 更改文件组。成功返回 TRUE，否则返回 FALSE |
| `chmod(string filename, int mode)` | bool | 更改文件模式。成功返回 TRUE，否则返回 FALSE |
| `touch(string filename [, int time])` | bool | 设置文件的修改时间 |
| `clearstatcache(void)` | void | 清除文件状态缓存 |
| `fileperms(string filename)` | int | 以八进制形式获取文件权限 |
| `fileinode(string filename)` | int | 获取文件 inode |
| `filesize(string filename)` | int | 获取文件大小 |

| 函数 | 返回值 | 作用 |
|---|---|---|
| fileowner(string filename) | int | 获取文件所有者的用户 ID |
| filegroup(string filename) | int | 获取文件的组 ID |
| fileatime(string filename) | int | 获取文件的最后访问时间 |
| filemtime(string filename) | int | 获取文件的最后修改时间 |
| filectime(string filename) | int | 获取文件的 inode 修改时间 |
| filetype(string filename) | string | 获取文件类型 |
| is_writable(string filename) | int | 如果文件可写则返回 true |
| is_readable(string filename) | int | 如果文件可读则返回 true |
| is_executable(string filename) | int | 如果文件可执行则返回 true |
| is_file(string filename) | int | 如果文件是普通文件则返回 true |
| is_dir(string filename) | int | 如果文件是目录则返回 true |
| is_link(string filename) | int | 如果文件是符号链接则返回 true |
| file_exists(string filename) | bool | 如果文件名存在则返回 true |
| lstat(string filename) | array | 给出文件或符号链接的信息。返回的数组包含以下元素：设备、inode；inode 保护模式；链接数；所有者用户 ID；所有者组 ID；如果 inode 为设备则为设备类型；字节大小；最后访问时间；最后修改时间；最后更改时间；文件系统 I/O 的块大小；分配的块数 |
| stat(string filename) | array | 给出文件的信息，与 lstat 描述相同 |

### 表 E-7 执行函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| exec(string command [, array output [, int return_value]]) | int | 执行外部程序 |
| system(string command [, int return_value]) | int | 执行外部程序并显示输出 |
| passthru(string command [, int return_value]) | void | 执行外部程序并显示原始输出。通常会与类似 PB MPlus 的东西一起使用 |
| escapeshellcmd(string command) | string | 转义 shell 元字符 |

### 表 E-8 文件操作函数

| 函数 | 返回值 | 作用 |
|---|---|---|
| flock(int fp, int operation [, int wouldblock]) | bool | 锁定文件使其对其他 PHP 脚本不可访问。锁定不会阻止其他进程打开文件 |
| get_meta_tags(string filename [, int use_include_path]) | array | 从文件中提取所有 <meta> 标签内容属性并返回数组 |
| file(string filename [, int use_include_path]) | array | 将整个文件读入数组，每行作为数组元素 |
| tempnam(string dir, string prefix) | string | 在指定前缀目录中创建唯一文件名 |
| tmpfile(void) | int | 创建一个临时文件，该文件将在调用 fclose() 函数后或脚本结束时自动删除 |
| fopen(string filename, string mode [, int use_include_path]) | int | 打开文件或 URL 并返回文件指针 |
