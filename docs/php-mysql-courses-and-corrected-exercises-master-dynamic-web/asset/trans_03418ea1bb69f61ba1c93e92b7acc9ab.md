

"a": 以仅写模式打开文件。文件指针位于文件末尾。如果文件不存在，则尝试创建它。

"r+": 以读写模式打开文件。文件指针位于文件开头。
fopen() 函数返回一个文件指针，该指针由其他文件操作函数（如 fread()、fwrite() 等）使用。如果 fopen() 函数失败，则返回 FALSE。

以下是一个示例：

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
?>
```

使用 fopen() 函数打开文件后，下一步是读取其内容。PHP 为这项任务提供了多个函数，包括 fread() 函数、fgets() 函数和 fgetc() 函数。这些函数各自提供了从打开的文件中读取数据的不同方法。

**fread() 函数：** 从使用 fopen() 打开的文件中读取特定数量的字节。它接受两个参数：由 fopen() 返回的文件指针和要读取的字节数。但是，如果你希望读取整个文件，可以使用 filesize() 函数，该函数返回文件的总大小。只需提供要读取的文件名即可。

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
$content = fread($handle, filesize("filetext/poem1.txt"));
echo $content;
?>
```

执行此代码将打开 poem1.txt 文件并允许只读访问其全部内容。

![](img/caba2aa22f5409ba73dea47176330677_302_0.png)

如果你希望从文件内容中读取特定数量的字节，只需将此字节数作为 fread() 函数的第二个参数指定即可。例如，以下代码允许你只读取此内容的 50 个字节。

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
$content = fread($handle, 50);
echo $content;
?>
```

### 结果：

### fgets() 函数：
从 fopen() 打开的文件中读取一整行。它以 fopen() 返回的文件指针作为参数。该函数读取直到行尾字符（通常是换行符或回车符）的那一行。它将读取的行作为字符串返回，包括行尾字符。如果到达文件末尾，则返回 false。

### 示例：

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
$content = fgets($handle);
echo $content;
?>
```

### 结果：

我可将你比作夏日？

### fgetc() 函数：
从 fopen() 打开的文件中一次读取一个字符。它以 fopen() 返回的文件指针作为参数。每次调用 fgetc() 时，它在文件中向前移动一个字符，并将读取的字符作为字符串返回。如果到达文件末尾，则返回 false。

在以下示例中，fgetc() 函数将被执行六次，显示相关文件的前六个字符：

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
echo fgetc($handle);
?>
```

### 结果：

![](img/caba2aa22f5409ba73dea47176330677_305_0.png)

要使用 fgetc() 函数读取文件的全部内容，可以在 while 循环中调用它，直到它返回 false，表示到达文件末尾。

以下是代码示例：

```php
<?php
$file = fopen("filetext/poem1.txt", "r");
if ($file) {
// Loop for reading character by character
while ((!$char = fgetc($file)) != false) {
echo $char;
}
}
?>
```

这段 PHP 代码使用 fopen() 函数以读取模式打开 "poem1.txt" 文件。如果文件打开成功（即 $file 不等于 false），则启动一个 while 循环。在循环的每次迭代中，使用 fgetc() 函数从文件中读取一个字符。循环条件检查 fgetc() 返回的值是否不为 false，意味着文件中仍有字符可读。如果是，则使用 echo 显示该字符。该循环重复执行，直到到达文件末尾，此时 fgetc() 返回的值变为 false，从而终止循环。

### fclose() 函数：
用于关闭之前使用 fopen() 函数打开的文件。它以 fopen() 返回的文件指针作为参数。

使用 fclose() 的示例：

```php
<?php
$handle = fopen("filetext/poem1.txt", "r");

if ($handle) {
$content = fread($handle, filesize("filetext/poem1.txt"));
echo $content;
fclose($handle); // Close file
} else {
echo "Unable to open file";
}
?>
```

这段 PHP 代码使用 fopen() 函数以读取模式打开文件 "poem1.txt"。如果文件打开成功，则使用 filesize() 函数获取文件大小，并使用 fread() 函数将文件内容读入变量。然后使用 echo 显示内容。

读取文件内容后，使用 fclose() 函数关闭文件并释放关联资源。如果无法打开文件，则显示一条错误消息，指示文件打开失败。

## 文件创建

在 PHP 中创建文件是一项常见操作，可以使用一些内置函数轻松完成。以下是创建新文件的方法：

### 使用 fopen() 函数

创建文件的第一步是使用 fopen() 函数。此函数打开一个文件，如果文件不存在则创建一个。以下是一个示例：

```php
<?php
// Open a file in write mode (create a new file if it doesn't exist)
$handle = fopen("filetext/new_file.txt", "w");

// Check if the file has been opened successfully
if ($handle != false) {
    echo "The file has been created successfully!";
    fclose($handle); // Close file after use
} else {
    echo "Impossible to create the file";
}
?>
```

在此示例中，我们使用 fopen() 以写入模式（“w”）打开名为 "new_file.txt" 的文件。如果文件不存在，fopen() 将创建它。如果文件打开成功，则显示成功消息；否则显示错误消息。

fopen() 函数还可用于以其他模式打开文件，例如只读（“r”）、读写（“r+”）、追加（“a”）等等。

在向其中写入数据之前创建文件，此步骤至关重要。

如果此代码无错误执行，将显示消息 "The file has been created successfully"，并在 "filetext" 目录中创建一个名为 "new_file.txt" 的新空文件。

![](img/caba2aa22f5409ba73dea47176330677_309_0.png)

## 写入文件

在 PHP 中向文件写入是一项常见操作，常用于生成数据文件、活动日志或报告。PHP 提供了多种向文件写入的方法，提供了极大的灵活性以满足不同的开发需求。在本节中，我们将探讨在 PHP 中向文件写入的不同方式。

### 使用 fwrite() 函数

文件成功打开后，可以使用 fwrite() 函数向其中写入数据。

PHP 中的 fwrite() 函数用于将数据写入文件。它通常接受三个参数：文件指针（通常由 fopen() 函数返回）、要写入文件的字符串，以及可选的要写入的字符串长度。如果未指定长度，fwrite() 将写入提供的整个字符串。

fwrite() 函数返回写入文件的字节数，如果出错则返回 FALSE。它通常与 fopen() 函数配合使用，以写入模式打开文件。数据写入后，我们建议使用 fclose() 函数关闭文件，以释放系统资源。

以下是使用 fwrite() 向文件写入的示例：

```php
<?php
// Open a file in write mode
$file = fopen("filetext/new_file.txt", "w");

// Write a string to the file
$data = "This is an example of content to be written to the file.";
fwrite($file, $data);

// Close the file
fclose($file);
?>
```

在此示例中，fopen() 函数以写入模式（“w”）打开名为 "new_file.txt" 的文件。接下来，fwrite() 函数将 $data 变量中存储的字符串写入此文件。最后，fclose() 函数关闭新创建的文件。

### 使用 file_put_contents() 函数

PHP 中的 file_put_contents() 函数用于将数据写入文件。它将要写入的文件路径、要写入的数据以及可能的其他选项作为参数。

使用 file_put_contents() 向文件写入的示例：

```php
<?php

// Data to be written to the file
$data = "Content to be written to the file.";

// Target file path
$filename = "filetext/new_file.txt";

// Write data to file
file_put_contents($filename, $data);
