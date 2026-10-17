
```c
/* read the directory */
pdirent= readdir(pdir);

/* iterate over each directory entry */
while (pdirent != NULL) {
    /* buffer for appending directory entries to */
    char dir_buff[500]="";

    /* we do not care about reading . or . .*/
    if (! strcmp(pdirent->d_name, ".") || ! strcmp(pdirent->d_name, ".."))
    {
        pdirent= readdir(pdir);
        continue;
    }

    /* copy the initial directory */
    strncpy(dir_buff, dir_str, strlen(dir_str));

    /* add delimiter */
strncat(dir_buff, "/", 1);

/* add the file or directory name */
strncat(dir_buff, pdirent->d_name, pdirent->d_reclen);

/* stat the entry--file or directory */
retval= lstat(dir_buff, &fstats);

/* directories have sizes too */
total += fstats.st_size;

/* if a file . */
if (pdirent->d_type == DT_REG) {
    fprintf(stderr, "file: %s size: %d ", dir_buff, fstats.st_size, total);
    fprintf(stderr, "total %lu\n", total);
}
/* if a directory, then recurse */
else if (pdirent->d_type == DT_DIR) {
    uint64_t tmp_total;
    fprintf(stderr, "dir: %s total so far: %lu\n", dir_buff, total);
    tmp_total= dir_byte_count(dir_buff);
    /* add total from subdirs */
    total += tmp_total;
    fprintf(stderr, "tmp_total %lu ", tmp_total);
    fprintf(stderr, "total %lu\n", total);
}
/* get next directory entry */
pdirent= readdir(pdir);
}
/* close the directory */
closedir(pdir);

return (total);
}
```

现在你有一个程序可以用来测试你的想法是否可行！

### 10. 编译此程序：

```
gcc -o total_bytes_dir total_bytes_dir.c
```

### 11. 编译完成后，你可以测试程序。为了便于测试，你可以创建一个测试目录，甚至包含子目录。将文件复制到每个子目录中，如以下代码列表所示，你会看到同一文件被复制到每个子目录中。测试的目标是验证程序是否递归地累加文件大小。结构如下所示：

```
ls -latRF testdir/
```

```
total 72

drwxr-xr-x  93 pgalbraith 22256  3162 Jul 14 17:56 ./

drwxr-xr-x   4 pgalbraith 22256   136 Jul 14 09:40 subdir/

drwxr-xr-x   4 pgalbraith 22256   136 Jul 14 09:40 ./

```
```
-rw-r--r-- 1 pgalbraith 22256 34813 Jul 14 09:21 wroxcode-0216.tar.gz

testdir/subdir:
total 72
drwxr-xr-x 3 pgalbraith 22256 102 Jul 14 09:40 subsubdir/
drwxr-xr-x 4 pgalbraith 22256 136 Jul 14 09:40 ./
-rw-r--r-- 1 pgalbraith 22256 34813 Jul 14 09:40 wroxcode-0216.tar.gz
drwxr-xr-x 4 pgalbraith 22256 136 Jul 14 09:40 ./

testdir//subdir/subsubdir:
total 72
drwxr-xr-x 3 pgalbraith 22256 102 Jul 14 09:40 ./
-rw-r--r-- 1 pgalbraith 22256 34813 Jul 14 09:40 wroxcode-0216.tar.gz
drwxr-xr-x 4 pgalbraith 22256 136 Jul 14 09:40 ./
```

### 12. 运行程序：

```
./total_bytes_dir testdir/
dir: testdir//subdir total so far: 136
dir: testdir//subdir/subsubdir total so far: 102
file: testdir//subdir/subsubdir/wroxcode-0216.tar.gz size: 34813 total 34813
tmp_total 34813 total 34915
file: testdir//subdir/wroxcode-0216.tar.gz size: 34813 total 69728
tmp_total 69728 total 69864
file: testdir//wroxcode-0216.tar.gz size: 34813 total 104677
total size of testdir/ in bytes: 104677
```

太棒了！正如你所看到的，数字加起来是正确的！现在你已经拥有了 UDF 所需的大部分功能。更妙的是，因为 MySQL 模式目录不包含子目录，你甚至不需要担心递归。

现在你已经有了已知可行的功能代码，下一步就是使用这段代码创建你的 UDF。

## 编写 UDF

你接下来要问自己的问题是：应该如何命名这个 UDF？如果在 SQL 语句中调用该函数，函数名应该是什么？对于本示例，所选的名称是 `db_bytes()`。

## 项目目录组织——创建开源项目

编写 UDF 时，你可能首先想做的是创建一个目录来存放源代码。对于本示例，目录被组织为开源项目，因为毕竟，你不想成为一名开源黑客并与社区分享你的成果吗？此 UDF 示例的源代码也可以从 Wrox 网站下载，你可以将其作为模板来创建自己的 UDF。在本示例中，创建了一个名为 `db_bytes` 的目录。

你可以将其安排为包含子目录。表 7-1 显示了这些子目录的列表。

### 表 7-1：开源项目的子目录

| 子目录 | 描述 |
|---|---|
| `src/` | 包含任何源文件，包括 `.c` 和 `.h`。 |
| `docs/` | 包含文档文件。对于多个项目，使用 Perl 的 POD 文档很方便，该文档可通过 Makefile 转换为主页面，便于编写文档且具有简单的标记语言。 |
| `sql/` | 包含 UDF 运行所需的任何 SQL 文件，例如用于安装函数的 CREATE FUNCTION 语句。 |
| `tests/` | 包含测试。通常这是一个包含一系列 SQL 语句的文件，你将其在服务器上运行并将输出连接到结果文件，然后在后续测试中用于输出比较。 |
| `utils/` | 可以包含你使用的任何额外实用工具。这可能包括安装函数或展示如何利用函数的 PHP 命令行脚本。 |
| `config/` | 包含 autoconf 宏和自动化脚本。通常，如果你从另一个项目获得这些文件并且它们能正常工作，你不会更改此目录的内容。如果你有一个空闲的周末，这是一个很好的地方来研究以了解更多关于自动构建工具的信息。 |

当然还有顶级目录，如表 7-2 所示，它本身包含这些子目录以及文件：

### 表 7-2：开源项目的顶级目录

| 目录 | 描述 |
|---|---|
| `AUTHORS:` | 这里列出项目的开发者。 |
| `COPYING` | 这是许可证文件。可从 BSD、GPL 各版本、Artistic 等多种许可证中选择。 |
| `ChangeLog` | 每次正式发布项目时，在此文件中包含你的姓名、日期和版本的标题，其下会有关于本次发布更改内容的说明。 |
| `INSTALL` | 此文件说明如何安装 UDF。 |
| `README` | 此文件对 UDF 进行说明。可以是任何你想提供的信息。此外，这也可以是顶级文档，指导用户在存储库中（docs、INSTALL 等）以及在线资源中查找更详细的信息。 |
| `configure/` `configure.ac` | 正式发布版包含 `configure`，它由 autoconf 根据 `configure.ac` 生成。你通常不会将 `configure` 纳入存储库，而是让用户运行 autoconf 生成脚本来创建它。 |
| `Makefile.am` | 这是 autoconf 在运行 configure 时用于构建 Makefile 的模板。 |

设置一个包含源文件和头文件、文档以及自动构建文件的基本包以使构建过程变得容易是很好的：

```
radha:db_bytes patg$ ls

AUTHORS      Makefile.am   aclocal.m4   docs      utils

COPYING      Makefile.in   config       sql

ChangeLog    NEWS          configure    src

INSTALL      README        configure.ac tests
```

即使一开始并非所有内容都完全完成或完善，建立这种结构以促进良好项目的启动也是一种良好的实践。

## 源代码实现

如前所述，`src` 目录包含源文件和头文件。对于本项目，创建了一个头文件 `common.h`。它包含一个或多个 UDF 源文件所需的数据类型、常量等。此文件可以包含进来，方便所有数据类型都被定义。下面是 `common.h` 中的内容，它定义了多个 UDF 常量，特别是与字符串长度相关的常量，尤其是将在 `init()` 函数中分配的结果字符串的长度：

```
#define VERSION_STRING "0.1\n"

#define VERSION_STRING_LENGTH 4

#define DIR_PATH_LENGTH 255

#define RESULT_LENGTH sizeof(char) * 16;
```

`db_bytes.c` 是接下来创建的源文件。这里实现你的 UDF。它包含本示例的所有函数。在创建其他 UDF 时，它们也可以包含在此文件中，或放在单独的文件中，具体取决于你的偏好。如果你为每个 UDF 创建单独的文件，你将需要修改 autoconf 配置文件（`Makefile.am`）以包含这些文件。

如前所述，每个 UDF 都定义了三个主要函数。对于本示例，函数命名如下：

- `db_bytes()`：这是执行 UDF 主要操作的实际值函数——你将在此实现你编写的测试程序的大部分功能。这也是实现“实现程序”部分中检查的好地方，以确保提供的目录名（这将是提供给 UDF 的模式名）存在并且可以访问。
- `db_bytes_init()`：用于检查提供的参数数量和类型，如果不正确，则返回错误以通知用户。
- `db_bytes_deinit()`：这通常用于释放在 `db_bytes_init()` 或 `db_bytes()` 中分配的任何数据。

实现 UDF，请按以下步骤操作：

1. 此源文件中的头文件，包含以下内容：

```
/*

    Copyright (C) 2009 Patrick Galbraith

    See COPYING file found with distribution for license.

*/

#include <mysql.h>

#include <string.h>

#include <stdio.h>

#include <stdlib.h>

#include <time.h>

#include <sys/types.h>

#include <sys/stat.h>

#include <errno.h>

#include <unistd.h>

#include <dirent.h>

#include "db_bytes.h"
```

2. 接下来声明包含 MySQL datadir 值的字符串。它被声明为 extern 以将该变量暴露给 MySQL 服务器，后者将用正确的值设置此变量。

```
/*

    this variable contains the directory path of datadir

    as read by MySQL, usually a relative path to the server

*/

extern char *mysql_data_home;
```

3. 在实现任何函数之前，先在文件顶部声明它们，在 UDF 函数定义之前：

```
/* function declaration */
/* init function */
my_bool db_bytes_init(UDF_INIT *initid,
                    UDF_ARGS *args,
                    char *message);

/* value function */
char *db_bytes(UDF_INIT *initid,
               UDF_ARGS *args,
               char *result, unsigned long *length,
char *is_null,
char *error);

/* de-init function */
void db_bytes_deinit(UDF_INIT *initid);
```

4. 接下来是 `db_bytes_init()` 的定义。实现包括检查参数计数以及参数是否为字符串。如果任一检查失败，则返回错误。此外，还为将包含结果的字符串分配内存。参数在函数开始处的函数注释中进行了描述。值得关注的是 UDF_INIT 指针 `*initid`。这是一个有用的指针，会传递给所有函数。它允许您分配内存或设置所有函数都可以访问的值，就像在此处为存储文件大小总和的字符串结果所做的那样。

由于 `*initid` 会传递给所有函数，您可以在值函数中使用在 init 函数中分配的内存，而您也需要在 deinit() 函数中释放它。

> 这里需要知道的一件重要事情是，您可能会有冲动在 init() 函数中执行其他类型的检查。在这种情况下，您可能会认为检查目录名是否存在或是否为空字符串是好的。请注意！对于您提供给 UDF 的字面值来说，这工作得很好；例如，在以下语句中：

`SELECT some_function('some value');`

值“some value”是可访问的并且可以正常工作。

但是，如果您在 SQL 语句中调用 UDF 以提供函数的参数，例如在表 `t1` 上使用 SELECT 语句的 name 列：

`SELECT some_function(name) from t1;`

参数值将为 NULL（调试器显示 0x0），如果您尝试使用或依赖此值，可能会导致您的 UDF 崩溃。这是设计使然，并且由于对 UDF 调用的解析方式而导致。字面值是可用的，因为它们是语句的一部分。然而，需要转译的值，例如尚未从表中读取的值（如上例中 name 列的值）尚未在 init() 函数中可访问。因此，任何此类检查都应在值函数中实现。

```
/*

db_bytes_init

Checks the number of arguments passed to the UDF and

returns an error if not exactly one argument

Also, memory is allocated for string result returned

in value function db_bytes() which must be freed in

db_bytes_init()

ARGUMENTS:

    UDF_INIT *initid

        UDF_INIT pointer which can be used to make

        allocated memory available to the other functions

    UDF_ARGS *args

        UDF_ARGS pointer to the UDF arguments, which includes

        the argument lengths and types

    char *message

        String for setting errors

    RETURNS boolean value, 0 success, 1 failure

*/

my_bool db_bytes_init(UDF_INIT *initid,
                    UDF_ARGS *args,
                    char *message)
{

    char *total_bytes;
    /*
