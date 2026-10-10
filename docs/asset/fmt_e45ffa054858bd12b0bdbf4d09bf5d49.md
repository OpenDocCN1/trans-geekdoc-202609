
```php
// 在表格中打印当前目录

print("<TABLE ORDER=\"1\">\n");

// 创建标题行

print("<TR>\n");

print("<TH>Filename</TH>\n");

print("<TH>File Size</TH>\n");

print("</TR>\n");

// 打开目录

$myDirectory = opendir(".");

// 获取每个条目

while($entryName = readdir($myDirectory)) {

    print("<TR>\n");

    print("<td>$entryName</td>\n");

    print("<TD ALIGN=\"right\">");

    print(filesize($entryName))."</TD>\n");

    print("</TR>\n");

}

// 关闭目录

closedir($myDirectory);?>
```

# PHP 核心编程

```php
print("</TABLE>\n");
?>
```

## 整数型 `pclose(integer file_handle)`

`pclose` 关闭由 `popen` 打开的文件流。返回值是 `popen` 的输出。

## 整数型 `popen(string command, string mode)`

`popen` 以文件的方式打开读取或写入管道。出错时返回 false。

## 字符串 `readdir(integer handle)`

`readdir` 返回目录中的下一个文件名，当没有剩余条目时返回 FALSE。请参见 `closedir`。

## 字符串 `readlink(string filename)`

`readlink` 返回符号链接指向的路径。出错时返回 false。另一个提供链接信息的函数是 `linkinfo`。

## 布尔型 `rename(string old_name, string new_name)`

`rename` 将 `old_name` 参数的文件重命名为 `new_name` 参数指定的名称。新旧名称可以包含完整路径，允许你使用 `rename` 移动文件。

```php
<?

// 将 data.txt 从本地目录
// 移动到临时目录
rename("./data.txt", "tmp/data");
?>
```

## 布尔型 `rewind(integer file_handle)`

`rewind` 将 PHP 的内部指针移回文件开头。这与使用 `fseek` 移动到零位置相同。

```php
<?

/*
 * 打印文件，再次打印第一行
 */

// 打开本地文件
$myFile = fopen("data.txt", "r");
while(!feof($myFile)) {
    // 从文件中读取一行
    $myLine = fgets($myFile, 255);
    print("$myLine <BR>\n");
}
rewind($myFile);
$myLine = fgets($myFile, 255);
print("$myLine <BR>\n");

// 关闭文件
close($myFile);
?>
```

## 布尔型 `rewinddir(integer handle)`

`rewinddir` 将内部指针重置为目录列表的开头。除非发生错误，否则它返回 TRUE。该句柄是 `opendir` 返回的整数。

```php
<?

/*
 * 在表格中打印当前目录
 */
print("<TABLE ORDER=\"1\">\n");

// 打开目录
$myDirectory = opendir(".");
print("<TR>\n");
print("<TH>Filename</TH>\n");

// 获取每个条目
while($entryName = readdir($myDirectory)) {
    print("<td>$entryName</td>\n");
}
?>
```

# PHP 核心编程

```php
print("</TR>\n");

// 回到开头
rewdir($myDirectory);
print("<TR>");
print("<TH>Size</TH>");

// 获取每个条目
while($entryName = readdir($myDirectory)) {
    print("<TD ALIGN=\"right\">");
    print(filesize($entryName));
    print("</TD>");
}
print("</TR>");

// 关闭目录
closedir($myDirectory);
print("</TABLE>");
?>
```

## 布尔型 `rmdir(string directory)`

使用 `rmdir` 函数删除目录。该目录必须为空。若要删除文件，请使用 `unlink`。

## integer `set_file_buffer(integer file_handle, integer size)`

使用 `set_file_buffer` 设置文件流上写缓冲区的大小。它需要一个由 `fopen`、`fsockopen` 或 `popen` 创建的有效文件句柄。`size` 参数是字节数，如果你将缓冲区设置为 0，则将不会使用任何缓冲。你必须在对文件流进行任何读取或写入操作之前调用 `set_file_buffer`。默认情况下，文件流从 8K 缓冲区开始。

# PHP 核心编程

```php
<?php
// 打开文件进行写入
$myFile = fopen("data.txt","w");

// 确保打开成功
if(!($myFile)) {
    print("file could not be opened");
    exit;
}

// 使用 1K 缓冲区
print(set_file_buffer($myFile, 1024));
for($index=0; $index<10; $index++) {
    // 向文件写入一行
    fwrite($myFile, "line $index\n");
}

// 关闭文件
close($myFile);
?>
```

## 数组 `stat(string filename)`

`stat` 函数执行 C 语言的 `stat` 函数并返回一个数组。该数组包含 13 个元素，从 0 开始编号。如果 `filename` 参数指向符号链接，则数组将反映链接所指向的文件。要获取有关链接本身的信息，请使用 `istat` 函数。表 8.7 列出了数组的内容。

```php
<?php
/*
 根据操作系统打印 stat 信息
 */
// 获取 stat 信息
$statInfo = stat("data.txt");
if(ereg("windows", $os)) {
    // 打印直到 Windows 信息
    printf("Drive: %c <BR>\n", $statInfo[0]+65);
    printf("Mode: %o <BR>\n", $statInfo[2]);
    printf("Size: %s bytes <BR>\n", $statInfo[7]);
    printf("Last Accessed: %s <BR>\n",
    date("H:i S D, Y", $statInfo[8]));
    printf("Last Modified: %s <BR>\n",
    date("H:i S D, Y", $statInfo[9]));
    printf("Created: %s <BR>\n", $statInfo[10]);
}
date("H:i F d, Y", $statInfo[10]);
}
else {
    // 打印 UNIX 版本
    print("Device: $statInfo[0] <BR>\n");
    print("INode: $statInfo[1] <BR>\n");
    printf("Mode: %s <BR>\n", $statInfo[2]);
    print("links: $statInfo[3] <BR>\n");
    print("UID: $statInfo[4] <BR>\n");
    print("GID: $statInfo[5] <BR>\n");
    print("Device: $statInfo[6] <BR>\n");
    print("Size: $statInfo[7] bytes <BR>\n");
    date("H:i F d, Y", $statInfo[8]);
    print("Last Modified: %s <BR>\n");
    date("H:i F d, Y", $statInfo[9]);
    print("Last Changed: %s <BR>\n");
    date("H:i F d, Y", $statInfo[10]);
    print("Block Size: $statInfo[11] <BR>\n");
    print("blocks: $statInfo[12] <BR>\n");
}
```

### 表 7.8. `stat` 函数返回的数组

| 元素 | 名称 | 描述 |
|---|---|---|
| 0 | 设备驱动器字母 | 这是一个标识文件系统设备的数字。在 Windows 上，此数字表示它所在的驱动器字母，其中 A 为 0。 |
| 1 | Inode | 文件的唯一标识符，在 Windows 上始终为 0。这与从 `inode` 函数得到的值相同。 |
| 2 | 模式 | 这与从 `fileperms` 得到的值相同，即读/写/执行权限。 |
| 3 | 链接数 | 指文件的链接数。在 Windows 上，如果文件存在，此值始终为 1。 |
| 4 | 用户 | 文件所有者的 ID，在 Windows 上始终为 0。 |
| 5 | 组 | 组 ID，在 Windows 上始终为 0。 |
| 6 | 设备 | 设备类型。 |
| 7 | 大小 | 以字节为单位的文件大小。 |
| 8 | 最后访问 | 文件最后访问的时间。 |
| 9 | 最后修改 | 文件最后修改的时间。 |
| 10 | 最后更改 | 文件最后更改的时间。 |
| 11 | 块大小 | 块的大小。 |
| 12 | 块 | 块的数量。 |

## 布尔型 `rmdir(string directory)`

使用 `rmdir` 函数删除目录。该目录必须为空。若要删除文件，请使用 `unlink`。

## integer `set_file_buffer(integer file_handle, integer size)`

使用 `set_file_buffer` 设置文件流上写缓冲区的大小。它需要一个由 `fopen`、`fsockopen` 或 `popen` 创建的有效文件句柄。`size` 参数是字节数，如果你将缓冲区设置为 0，则将不会使用任何缓冲。你必须在对文件流进行任何读取或写入操作之前调用 `set_file_buffer`。默认情况下，文件流从 8K 缓冲区开始。

# PHP 核心编程

```php
<?php
// 打开文件进行写入
$myFile = fopen("data.txt","w");

// 确保打开成功
if(!($myFile)) {
    print("file could not be opened");
    exit;
}

// 使用 1K 缓冲区
print(set_file_buffer($myFile, 1024));
for($index=0; $index<10; $index++) {
    // 向文件写入一行
    fwrite($myFile, "line $index\n");
}

// 关闭文件
close($myFile);
?>
```

## 数组 `stat(string filename)`

`stat` 函数执行 C 语言的 `stat` 函数并返回一个数组。该数组包含 13 个元素，从 0 开始编号。如果 `filename` 参数指向符号链接，则数组将反映链接所指向的文件。要获取有关链接本身的信息，请使用 `istat` 函数。表 8.7 列出了数组的内容。

```php
<?php
/*
 根据操作系统打印 stat 信息
 */
// 获取 stat 信息
$statInfo = stat("data.txt");
if(ereg("windows", $os)) {
    // 打印直到 Windows 信息
    printf("Drive: %c <BR>\n", $statInfo[0]+65);
    printf("Mode: %o <BR>\n", $statInfo[2]);
    printf("Size: %s bytes <BR>\n", $statInfo[7]);
    printf("Last Accessed: %s <BR>\n",
    date("H:i S D, Y", $statInfo[8]));
    printf("Last Modified: %s <BR>\n",
    date("H:i S D, Y", $statInfo[9]));
    printf("Created: %s <BR>\n", $statInfo[10]);
}
date("H:i F d, Y", $statInfo[10]);
}
else {
    // 打印 UNIX 版本
    print("Device: $statInfo[0] <BR>\n");
    print("INode: $statInfo[1] <BR>\n");
    printf("Mode: %s <BR>\n", $statInfo[2]);
    print("links: $statInfo[3] <BR>\n");
    print("UID: $statInfo[4] <BR>\n");
    print("GID: $statInfo[5] <BR>\n");
    print("Device: $statInfo[6] <BR>\n");
    print("Size: $statInfo[7] bytes <BR>\n");
    date("H:i F d, Y", $statInfo[8]);
    print("Last Modified: %s <BR>\n");
    date("H:i F d, Y", $statInfo[9]);
    print("Last Changed: %s <BR>\n");
    date("H:i F d, Y", $statInfo[10]);
    print("Block Size: $statInfo[11] <BR>\n");
    print("blocks: $statInfo[12] <BR>\n");
}
```

### 表 7.8. `stat` 函数返回的数组

| 元素 | 名称 | 描述 |
|---|---|---|
| 0 | 设备驱动器字母 | 这是一个标识文件系统设备的数字。在 Windows 上，此数字表示它所在的驱动器字母，其中 A 为 0。 |
| 1 | Inode | 文件的唯一标识符，在 Windows 上始终为 0。这与从 `inode` 函数得到的值相同。 |
| 2 | 模式 | 这与从 `fileperms` 得到的值相同，即读/写/执行权限。 |
| 3 | 链接数 | 指文件的链接数。在 Windows 上，如果文件存在，此值始终为 1。 |
| 4 | 用户 | 文件所有者的 ID，在 Windows 上始终为 0。 |
| 5 | 组 | 组 ID，在 Windows 上始终为 0。 |
| 6 | 设备 | 设备类型。 |
| 7 | 大小 | 以字节为单位的文件大小。 |
| 8 | 最后访问 | 文件最后访问的时间。 |
| 9 | 最后修改 | 文件最后修改的时间。 |
| 10 | 最后更改 | 文件最后更改的时间。 |
| 11 | 块大小 | 块的大小。 |
| 12 | 块 | 块的数量。 |

## 布尔型 `symlink(string source destination)`

`symlink` 函数通过 `destination` 参数创建指向 `source` 的符号链接。要创建硬链接，请使用 `link` 函数。

```php
<?php
// 创建符号链接到文件
if(symlink("data.txt", data.txt)) {
    print("Symbolic link created");
} else {
    print("Symbolic link not created");
}
?>
```

## integer `tmpfile()`

`tmpfile` 函数打开一个临时文件并返回其句柄。该句柄可以像 `fopen` 一样使用。如果无法创建临时文件，返回 FALSE。

```php
<?php
// 打开临时文件
$fp = tmpfile();

// 写入一些数据
for($i = 0; $i < 1024; $i++) {
    // 写入字符
    fputs($fp, chr($i));
}

// 回到开头
rewind($fp);

// 打印内容
passthru($fp);

// 关闭文件，
fclose($fp);
```
