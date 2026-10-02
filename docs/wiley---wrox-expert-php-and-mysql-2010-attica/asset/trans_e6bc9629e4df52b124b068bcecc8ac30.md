
- **db_bytes_init()**: 用于检查提供的参数数量和类型，如果不正确，则返回错误以通知用户。
- **db_bytes_deinit()**: 这通常用于释放在 db_bytes_init() 或 db_bytes() 中分配的任何数据。

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

4. 接下来是 db_bytes_init() 的定义。实现包括检查参数计数以及参数是否为字符串。如果任一检查失败，则返回错误。此外，还为将包含结果的字符串分配内存。参数在函数开始处的函数注释中进行了描述。值得关注的是 UDF_INIT 指针 *initid。这是一个有用的指针，会传递给所有函数。它允许您分配内存或设置所有函数都可以访问的值，就像在此处为存储文件大小总和的字符串结果所做的那样。

由于 *initid 会传递给所有函数，您可以在值函数中使用在 init 函数中分配的内存，而您也需要在 deinit() 函数中释放它。

> 这里需要知道的一件重要事情是，您可能会有冲动在 init() 函数中执行其他类型的检查。在这种情况下，您可能会认为检查目录名是否存在或是否为空字符串是好的。请注意！对于您提供给 UDF 的字面值来说，这工作得很好；例如，在以下语句中：

SELECT some_function('some value');

值“some value”是可访问的并且可以正常工作。

但是，如果您在 SQL 语句中调用 UDF 以提供函数的参数，例如在表 t1 上使用 SELECT 语句的 name 列：

SELECT some_function(name) from t1;

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
        check the number of arguments and if a string and if
        not only one, return an error
    */
    if (args->arg_count != 1 || args->arg_type[0] != STRING_RESULT)
    {
        /*
            copy a useful message to the char pointer *message
            this will be returned to the user
        */
        strncpy(message, " USAGE: db_bytes('<schema>').",
                    MYSQL_ERRMSG_SIZE);
        return 1;
    }

    /*
        allocate a character sequence (string) pointer
        this will be used for the results in the value
        function, db_bytes()
    */
    total_bytes = malloc(RESULT_LENGTH);

    /*
        coerce the single argument to a string
    */
    args->arg_type[0]= STRING_RESULT;

    /*
        initid can be used in _init to point to allocated memory
        for use in the value function. This must be freed in
        db_bytes_deinit()
    */
    initid->ptr = (char *)total_bytes;

    /*
      return of 0 is success
    */
    return 0;
}
```

5. 接下来是程序的核心，值函数 db_bytes()。您将在此处实现之前使用测试程序创建的功能，当然是在 UDF API 的限制范围内。与 db_bytes_init() 一样，对函数工作原理进行大量注释是一种良好的实践，并且它提供了此代码如何工作的解释。

> 参数在代码注释中进行了说明。db_bytes() 与 db_bytes_init() 一样，其前两个参数是指针 *initid 和 *args，它们是相同的参数，并在两个函数中发挥相同的作用。参数 *result 是一个最多 255 字节的字符串。虽然在此示例中未使用它，但您可以使用它来存储结果。为了演示 init() 函数如何用于分配值函数使用的内存，此处改用已分配的字符串。您会看到编译器指令 __attribute__ ((unused))，它用于避免在函数体中未使用此变量时产生的警告。

6. 下一个参数 *length 是一个长指针，您必须使用它来设置 UDF 中返回值的长度，否则您的 UDF 将不知道结果的长度是多少，您可能会导致数据被截断。最后一个参数 *error 看起来像是用于错误消息的，但实际上是用于使函数在当前副本的所有调用中返回 NULL。

```
/*
db_bytes()

This is the value function that given a schema name
argument (string) it then obtains the number of bytes of
all files in a MySQL schema subdirectory, then that
value is stored in the return string and returned to the user

ARGUMENTS:
    UDF_INIT *initid
        UDF_INIT pointer which can be used to make
        allocated memory available to the other functions

    UDF_ARGS *args
        UDF_ARGS pointer to the UDF arguments, which includes
        the argument lengths and types

    *result
Unused, but could alternatively be used to store the result,
255 bytes long

*length
    Pointer, specifies the length of the return value

*is_null
    Set to true, denotes that the value being returned
    is NULL

*error
    if set to 1 the function will not be
    called anymore and mysqld will return NULL
    for all calls to this copy of the function.

    RETURNS
        string pointer containing the value returned by the UDF
*/
char *db_bytes(UDF_INIT *initid,
               UDF_ARGS *args,
               __attribute__ ((unused)) char *result,
               unsigned long *length,
               char *is_null,
               char *error)
{
```

7. 接下来，通过 initid->ptr 指向在 db_bytes_init() 中为结果字符串分配的内存，而它反过来指向此已分配的内存。然后声明其他变量，这些变量将根据代码中的注释使用。

```
/*
    set a char pointer to point to the memory allocated
    in db_bytes_init() for storing the result
*/
char *total_bytes= (char *)initid->ptr;

/* for return values from functions */
int retval;
/*
    the variable containing the sum of file sizes
*/
uint64_t total_size= 0;

/*
    for printing errors to which you then pass to stderr
*/
char errstr[255];

/*
    pointer to the directory, when opened
*/
DIR *pdir;
/*

