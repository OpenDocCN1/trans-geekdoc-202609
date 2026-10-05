

```php
// 检查 $file 变量是否等于
// 当前目录或上级目录
if($file != "." && $file != "..")
{
    $ftime = filetime($dirname."/"$file);
    if(date("Y") == date("Y", $ftime) &&
        date("m") == date("m", $ftime) &&
        date("d") == date("d", $ftime))
    {
        echo date("Y-m-d", $ftime) . " " . $dirname."/"$file."<br>";
    }
    // 如果当前项目是一个目录
    // 则递归调用 scandir() 函数
    if(is_dir($dirname."/"$file))
    {
        scandir($dirname."/"$file);
    }
    // 关闭目录
    closedir($dir);
}?>
```

在遍历目录树时，必须从递归下降列表中排除 `.`（当前目录）和 `..`（父目录），以防止脚本进入无限循环。`scandir()` 函数通过以下条件找到在当天创建或修改的文件：

```php
if(date("Y") == date("Y", $ftime) &&
    date("m") == date("m", $ftime) &&
    date("d") == date("d", $ftime)
```

将条件更改为如下：

```php
if(date("Y") == date("Y", $ftime) &&
    date("m") == date("m", $ftime)
```

因此，在本月内创建或修改的文件将被列出来。

如果列表 II.14.8 生成的报告包含过多的“额外”文件（例如用户上传的图像或文本文件），可以通过添加过滤器来修改条件，例如只捕获 PHP 文件。

## II.14.4. 监控大文件

这个问题也可以通过递归遍历目录树来解决。列表 II.14.9 显示了一个列出所有超过 50 KB 文件大小限制的 PHP 文件脚本。

## II.14.9. 用于定位大文件的脚本

```php
<?php
// 目录名称
$dirname = ".";
// 调用递归进入
// 根目录子目录的函数
scan_dir($dirname);

/////////////////////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

# 第 II.14 章: 脚本 377

```php
if($fsize > 50*1024)
{
    // 提取文件后缀名
    $ext = strchr($dirname."/"$file
```

# 第 II.15 章: 杂项

![](img/a893312ec68b8170fe567f785e95c06e_391_0.png)

## II.15.1. 交换变量的位置

解决此问题的脚本可能类似于列表 II.15.1 所示。

列表 II.15.1. 交换变量的位置

```php
<?php
$x = 4;
$y = 5;

echo "Before:<br>";
echo "x = $y<br>";
```

# 第 II.15 章: 杂项 379

脚本执行结果如图 II.15.1 所示。

![](img/a893312ec68b8170fe567f785e95c06e_392_0.png)

## II.15.2. 页面预加载脚本

如果访问者被直接发送到 1.php 页面（列表 I.15.1）并必须等待加载，他们可能会认为网站挂了。因此，他们应该先重定向到 2.php 页面（列表 II.15.2）。

列表 II.15.2. 页面预加载脚本 (2.php)

```php
<?php
// 这是 2.php 文件。
echo
"<p>计算结果可能需要一些时间。请等待 5 秒。</p>
// 重定向到 1.php 页面
echo "<HTML><meta http-equiv='refresh' content='5;URL=1.php'>"
```

通过这种方式，当 1.php 页面加载时，会显示“计算结果可能需要一些时间。请等待 5 秒。” 脚本执行结果显示在图 II.15.1 中。显示执行进度

![](img/a893312ec68b8170fe567f785e95c06e_392_0.png)

第 380 页: 解决方案

img/a893312ec68b8170fe567f785e95c06e_391_0.png) 显示动画 (GIF) 用户等待等待。

II.15.3. 打打包文件。

```php
<?php
/////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

# 第 II.15 章: 杂项

```php
if($fsize > 50*1024)
{
    // 提取文件后缀名
    $ext = strchr($dirname."/"$file
```

381 页

```php

// 目录名称
$dirname = ".";
// 调用递归进入
// 根目录子目录的函数
scan_dir($dirname);

/////////////////////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

```php
// 检查 $file 变量是否等于
// 当前目录或上级目录
if($file != "." && $file != "..")
{
    $ftime = filetime($dirname."/"$file);
    if(date("Y") == date("Y", $ftime) &&
        date("m") == date("m", $ftime) &&
        date("d") == date("d", $ftime))
    {
        echo date("Y-m-d", $ftime) . " " . $dirname."/"$file."<br>";
    }
    // 如果当前项目是一个目录
    // 则递归调用 scandir() 函数
    if(is_dir($dirname."/"$file))
    {
        scandir($dirname."/"$file);
    }
    // 关闭目录
    closedir($dir);
}?>
```

在遍历目录树时，必须从递归下降列表中排除 `.`（当前目录）和 `..`（父目录），以防止脚本进入无限循环。`scandir()` 函数通过以下条件找到在当天创建或修改的文件：

```php
if(date("Y") == date("Y", $ftime) &&
    date("m") == date("m", $ftime) &&
    date("d") == date("d", $ftime)
```

将条件更改为如下：

```php
if(date("Y") == date("Y", $ftime) &&
    date("m") == date("m", $ftime)
```

因此，在本月内创建或修改的文件将被列出来。

如果列表 II.14.8 生成的报告包含过多的“额外”文件（例如用户上传的图像或文本文件），可以通过添加过滤器来修改条件，例如只捕获 PHP 文件。

## II.14.4. 监控大文件

这个问题也可以通过递归遍历目录树来解决。列表 II.14.9 显示了一个列出所有超过 50 KB 文件大小限制的 PHP 文件脚本。

## II.14.9. 用于定位大文件的脚本

```php
<?php
// 目录名称
$dirname = ".";
// 调用递归进入
// 根目录子目录的函数
scan_dir($dirname);

/////////////////////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

# 第 II.14 章: 脚本 377

```php
if($fsize > 50*1024)
{
    // 提取文件后缀名
    $ext = strchr($dirname."/"$file
```

# 第 II.15 章: 杂项

![](img/a893312ec68b8170fe567f785e95c06e_391_0.png)

## II.15.1. 交换变量的位置

解决此问题的脚本可能类似于列表 II.15.1 所示。

列表 II.15.1. 交换交换的位置

```php
<?php
$x = 4;
$y = 5;

echo "Before:<br>";
echo "x = $y<br>";
```

# 第 II.15 章: 杂项 379

脚本执行结果如图 II.15.1 所示。

![](img/a893312ec68b8170fe567f785e95c06e_392_0.png)

## II.15.2. 页面预加载脚本

如果访问者被直接发送到 1.php 页面（列表 I.15.1）并必须等待加载，他们可能会认为网站挂了。因此，他们应该先重定向到 2.php 页面（列表 II.15.2）。

列表 II.15.2. 页面预加载脚本 (2.php)

```php
<?php
// 这是 2.php 文件。
echo
"<p>计算结果可能需要一些时间。请等待 5 秒。</p>
// 重定向到 1.php 页面
echo "<HTML><meta http-equiv='refresh' content='5;URL=1.php'>"
</HTML>
```

通过这种方式，当 1.php 页面加载时，会显示“计算结果可能需要一些时间。请等待 5 秒。” 脚本执行结果显示在图 II.15.1 中。显示执行进度

img/a893312ec68b8170fe567f785e95c06e_392_0.png) 第 380 页: 解决方案

img/a893312ec68b8170fe567f785e95c06e_391_0.png) 显示动画 (GIF) 用户等待等待。

II.15.3. 打打包文件。

```php
<?php
/////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

# 第 II.15 章: 杂项

```php
if($fsize > 50*1024)
{
    // 提取文件后缀名
    $ext = strchr($dirname."/"$file
```

381 页

```php

// 目录名称
$dirname = ".";
// 调用递归进入
// 根目录子目录的函数
scan_dir($dirname);

/////////////////////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

```php
// 检查 $file 变量是否等于
// 当前目录或上级目录
if($file != "." && $file != "..")
{
    $ftime = filetime($dirname."/"$file);
    if(date("Y") == date("Y", $ftime) &&
        date("m") == date("m", $ftime) &&
        date("d") == date("d", $ftime))
    {
        echo date("Y-m-d", $ftime) . " " . $dirname."/"$file."<br>";
    }
    // 如果当前项目是一个目录
    // 则递归调用 scandir() 函数
    if(is_dir($dirname."/"$file))
    {
        scandir($dirname."/"$file);
    }
    // 关闭目录
    closedir($dir);
}?>
```

在遍历目录树时，必须从递归下降列表中排除 `.`（当前目录）和 `..`（父目录），以防止脚本进入无限循环。`scandir()` 函数通过以下条件找到在当天创建或修改的文件：

```php
if(date("Y") == date("Y", $ftime) &&
    date("m") == date("m", $ftime) &&
    date("d") == date("d", $ftime)
```

将条件更改为如下：

```php
if(date("Y") == date("Y", $ftime) &&
    date("m") == date("m", $ftime)
```

因此，在本月内创建或修改的文件将被列出来。

如果列表 II.14.8 生成的报告包含过多的“额外”文件（例如用户上传的图像或文本文件），可以通过添加过滤器来修改条件，例如只捕获 PHP 文件。

## II.14.4. 监控大文件

这个问题也可以通过递归遍历目录树来解决。列表 II.14.9 显示了一个列出所有超过 50 KB 文件大小限制的 PHP 文件脚本。

## II.14.9. 用于定位大文件的脚本

```php
<?php
// 目录名称
$dirname = ".";
// 调用递归进入
// 根目录子目录的函数
scan_dir($dirname);

/////////////////////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

# 第 II.14 章: 脚本 377

```php
if($fsize > 50*1024)
{
    // 提取文件后缀名
    $ext = strchr($dirname."/"$file
```

# 第 II.15 章: 杂项

![](img/a893312ec68b8170fe567f785e95c06e_391_0.png)

## II.15.1. 交换变量的位置

解决此问题的脚本可能类似于列表 II.15.1 所示。

列表 II.15.1. 交换变量的位置

```php
<?php
$x = 4;
$y = 5;

echo "Before:<br>";
echo "x = $y<br>";
```

# 第 II.15 章: 杂项 379

脚本执行结果如图 II.15.1 所示。

![](img/a893312ec68b8170fe567f785e95c06e_392_0.png)

## II.15.2. 页面预加载脚本

如果访问者被直接发送到 1.php 页面（列表 I.15.1）并必须等待加载，他们可能会认为网站挂了。因此，他们应该先重定向到 2.php 页面（列表 II.15.2）。

列表 II.15.2. 页面预加载脚本 (2.php)

```php
<?php
// 这是 2.php 文件。
echo
"<p>计算结果可能需要一些时间。请等待 5 秒。</p>
// 重定向到 1.php 页面
echo "<HTML><meta http-equiv='refresh' content='5;URL=1.php'>"
</HTML>
```

通过这种方式，当 1.php 页面加载时，会显示“计算结果可能需要一些时间。请等待 5 秒。” 脚本执行结果显示在图 II.15.1 中。显示执行进度

img/a893312ec68b8170fe567f785e95c06e_392_0.png) 第 380 页: 解决方案

img/a893312ec68b8170fe567f785e95c06e_391_0.png) 显示动画 (GIF) 用户等待等待。

II.15.3. 打打包文件。

```php
<?php
/////////////////////////////////////////
// 用于递归遍历目录树的函数
/////////////////////////////////////////
function scan_dir($dirname)
{
    // 打开当前目录
    $dir = opendir($dirname);
    // 循环读取当前目录
    while (($file = readdir($dir)) != false) {
        // 检查 $file 变量是否
        // 等于当前或上级目录
        if($file != "." && $file != "..") {
            // 提取文件大小...
            $filesize = filesize($dirname."/".$file);
            // 如果文件大小大于 50 KB
            if($fsize > 50*1024)
            {
                // 提取文件后缀名
                $ext = strchr($dirname."/"$file,
```

