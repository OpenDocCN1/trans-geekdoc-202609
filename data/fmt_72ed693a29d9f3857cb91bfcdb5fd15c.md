
### 代码片段

```c
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

5. 接下来是程序的核心，值函数 `db_bytes()`。您将在此处实现之前使用测试程序创建的功能，当然是在 UDF API 的限制范围内。与 `db_bytes_init()` 一样，对函数工作原理进行大量注释是一种良好的实践，并且它提供了此代码如何工作的解释。

> 参数在代码注释中进行了说明。`db_bytes()` 与 `db_bytes_init()` 一样，其前两个参数是指针 `*initid` 和 `*args`，它们是相同的参数，并在两个函数中发挥相同的作用。参数 `*result` 是一个最多 255 字节的字符串。虽然在此示例中未使用它，但您可以使用它来存储结果。为了演示 `init()` 函数如何用于分配值函数使用的内存，此处改用已分配的字符串。您会看到编译器指令 `__attribute__ ((unused))`，它用于避免在函数体中未使用此变量时产生的警告。

6. 下一个参数 `*length` 是一个长指针，您必须使用它来设置 UDF 中返回值的长度，否则您的 UDF 将不知道结果的长度是多少，您可能会导致数据被截断。最后一个参数 `*error` 看起来像是用于错误消息的，但实际上是用于使函数在当前副本的所有调用中返回 NULL。

```c
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

7. 接下来，通过 `initid->ptr` 指向在 `db_bytes_init()` 中为结果字符串分配的内存，而它反过来指向此已分配的内存。然后声明其他变量，这些变量将根据代码中的注释使用。

```c
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
/* character sequence/array for appending directory path to */
char schema_path[DIR_PATH_LENGTH]= "";
/*
    pointer to current directory entry
*/
struct dirent *pdirent;
/*
    stat structure for obtaining the status of the current directory
    entry
*/
struct stat fstats;
```

## 检查 UDF 是否已安装

现在，UDF 通过以下流程进行检查：

- 1. 第一次检查是查看指定的模式是否为 `INFORMATION_SCHEMA` 模式。信息模式是一个包含物化视图的模式，并且没有实际的模式目录或数据库文件，因此对于这种情况永远不会有任何大小，因此返回 NULL。请注意，您将 `is_null` 设置为 1，`length` 设置为 0（如果您这样设置，它们使用指针表示法），然后设置返回的 NULL，当然作为 `char` 指针进行强制转换。

```c
/*
  return a NULL if information_schema, but not an error
*/
if (!strcasecmp("information_schema", args->args[0]))
{
  /*
    setting is_null and returning NULL ensures a NULL is returned
    in MySQL
  */
  *is_null= 1;
  *length= 0;
  return (char *)NULL;
}
```

- 2. `*mysql_data_home` 中的值，即 `datadir` 值，是首先附加到字符序列/数组 `schema_path` 的第一个值，然后附加其他值以构建给定模式的完整模式路径：

```c
/*
  start off concatenating the datadir value set in mysql_data_home
*/
strncat(schema_path, mysql_data_home,
                strlen(mysql_data_home));

/* need to add a delimiter */
strncat(schema_path, "/", 1);

/* now add the schema name */
strncat(schema_path, args->args[0], args->lengths[0]);
strncat(schema_path, "/", 1);
```

- 3. 进行检查以确保提供的模式名称通过简单的 `lstat()` 检查产生有效的目录（或文件）。如果读取 `schema_path` 时出现错误，则返回值设置为 null，并且错误会打印到 `stderr`（MySQL 错误日志）。您有两种方法可以做到这一点——这里显示的方式是返回 null 并将错误记录到日志中。您也可以选择返回错误的字符串值，但这会阻止您使用内置函数 `isnull()` 之类的 true/false 检查。

```c
/* stat the schema_path value */
retval= lstat(schema_path, &fstats);
/*
    if -1 is the return value, print an error to the error log
    and return null
*/
if (retval == -1)
{
    sprintf(errstr, "ERROR with schema '%s': (%s)\n",
        args->args[0], strerror(errno));

    fprintf(stderr, "%s", errstr);
    *length= 0;
    /* *length= strlen(errstr); */
    /* return tmp_errstr; */
    *is_null= 1;
    return (char *)NULL;
}
```

- 4. 目录被打开，并检查 `pdir` 的值以查看该目录是否成功打开。如果没有，则使用 `sprintf()` 设置 `errstr` 的错误，打印到 `stderr`（MySQL 错误日志）并返回 NULL。

```c
/* open the directory */
pdir= opendir(schema_path);
/*
    if the pointer is null, then there was a problem
    so return an error
*/
if (pdir == NULL) {
    sprintf(errstr, "ERROR with schema '%s': (%s)\n",
        args->args[0], strerror(errno));
    *length= strlen(errstr);
    *is_null= 1;
    *error= 1;
    return (char *)NULL;
}
```

- 5. 读取第一个目录条目。这提供了初始条目，可在随后的 while 循环中进行检查，只要目录条目存在，该循环就会迭代。该 while 循环基本上是对每个条目执行 `lstat()` 以获取条目的大小。无需关心条目是文件还是目录，因为两种类型都有大小。此外，需要注意的是，对于 MySQL 模式目录，不应包含任何子目录——只有文件。while 循环中执行的唯一检查是检查目录条目的名称是否为“.”或“..”（分别为父目录或当前目录），其中任何一个都应跳过。每个条目的大小都添加到 `total_size` 中包含的总计中。由于 MySQL 模式目录没有子目录，因此不需要递归。

- 6. 在循环结束时，目录最终被关闭：

```c
/*
    read the first directory entry
*/
pdirent= readdir(pdir);
/*
    in a while loop, continue to read directory entries, summing of the
    directory entry sizes
*/
while (pdirent != NULL) {
    /* buffer for appending directory entries to */
    char path_buf[DIR_PATH_LENGTH] = "";
/* we do not care about reading . or .. */
    if (! strcmp(pdirent->d_name, ".") || ! strcmp(pdirent->d_name, ".."))
    {
        pdirent= readdir(pdir);
        continue;
    }
    /* start out concatenating the schema path */
    strncat(path_buf, schema_path, strlen(schema_path));
    /* add the entry - file or directory name */
    strncat(path_buf, pdirent->d_name, pdirent->d_reclen);
    /* stat the entry - file or directory */
    retval= lstat(path_buf, &fstats);
    /*
        directory entries have a size too, so add to total
    */
    total_size+= fstats.st_size;
    /* rinse, lather, repeat - read the next entry */
    pdirent= readdir(pdir);
}
/* all done now, so close the directory */
closedir(pdir);
```

- 7. 最后，使用 `sprintf()` 将模式目录中文件大小的总和 `total_size` 打印到字符串 `total_bytes` 中，`*length` 使用 `strlen()` 设置，并返回 `total_bytes`，从而将值返回给 UDF 的用户：

```c
/*
    need to return a string, so use sprintf to convert the total_size
    to a string value contained in total_bytes
*/
sprintf(total_bytes, "%d", total_size);
/*
    length MUST be set for the UDF to properly return the value
    */
    *length= strlen(total_bytes);
    /* now return the string */
    return (total_bytes);
    }
```

`db_bytes_deinit()` 的目的是释放任何剩余的分配或执行在 `db_bytes_init()` 或 `db_bytes_get()` 期间分配的其他“清理”操作。在 `db_bytes_init()` 中分配的唯一内存是用于 `db_bytes()` 中使用的字符串 `total_bytes` 的内存，其地址由 `initid->ptr` 指向。在 `db_bytes_init()` 内部，`initid->ptr` 被引用到一个本地 `char` 指针 `*total_bytes` 指针然后被释放。

```c
/* de-init function */
void db_bytes_deinit(UDF_INIT *initid)
{
    char *total_bytes= initid->ptr;
    /* free the allocated memory */
    free(total_bytes);
    return;
}
```

这完成了 `db_bytes()` UDF 的源代码实现。现在是构建它的时候了！

## 构建 UDF
