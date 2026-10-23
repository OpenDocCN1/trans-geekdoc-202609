

## 清单3.4.

实际数据从制表符分隔的文件中加载。这些文件保存在作者的ResearchGate网站上（https://www.researchgate.net/publication/360568958_SIV_overall 和 https://www.researchgate.net/publication/360568853_SIV_results）。文件下载到本地目录后，可以使用`read.table`将其加载到R环境中。该函数以本地目录完整路径（绝对路径）的形式接收文件指针。否则，除非文件下载到的本地目录就是R的默认目录，否则可以使用`setwd`设置工作目录，然后从那里访问文件，无需写出全部（相对）路径。在清单中，由于不知道本地目录，因此使用`getwd`函数确定当前目录，并将其作为参数传递给`setwd`。这一过程实质上是将R的默认目录简化为工作目录。在实际使用中，用户可以设置首选目录，从而无需写下下载文件的完整路径。或者，`read.table`可以接受完整的URL。此外，`read.table`是一个通用函数，其各个参数也尽可能通用。其他相关函数如`read.csv`和`read.delim`专门用于读取逗号分隔值（csv）和制表符分隔值（tsv），方法是将`sep`参数分别设置为逗号（“,”）和制表符（“\t”）。文件`SIV_overall.tsv`包含从热循环仪获取的扩增数据，而`SIV_results.tsv`包含所有反应的定量循环。每个反应由一个唯一索引标识。`SIV_overall.tsv`文件被加载到对象*扩增*中，`SIV_results.tsv`文件被加载到对象*验证*中。

```
Determining the current (more properly: working) folder where R reads and writes file
is given by the function `getwd`, which does not require an argument. It is possible to
set the current folder with `setwd`.

`getwd()`
    x
        the path to a folder

`read.table(file, header, sep, quote, dec, row.names, col.names, na.strings, skip,
fill, strip.white, blank.lines.skip, comment.char, encoding, skipNul,
stringsAsFactors)`
    file
        name of the data file. If it does not contain an absolute path, the file name is
        relative to the current working directory. The file can also be a complete URL.

    header
        logical indicating whether the file contains the names of the variables as its
        first line.
    sep
        field separator character (default = "").
    quote
        quoting character (default = "\"").
    dec
        character used for decimal points (default = ".").
    row.names, col.names
        vector of row or column names.
    na.strings
        vector of strings to be interpreted as NA values.
    skip
        number of lines of the data file to skip before beginning to read data.
    fill
        if TRUE, blank fields are implicitly added.
    strip.white
        logical to determine whether leading and trailing white space from unquoted
        character fields should be removed.
    blank.lines.skip
        if TRUE, blank lines are ignored.
    comment.char
        comment character (default = "#"). details see scan.
    encoding
        type of text encoding (default = UTF-8).
    skipNul
        logical to determine whether NULL values should be skipped.
    stringsAsFactors
        logical to determine whether strings should be converted to factors.
```

## 清单3.5.

每个样本的MR和FCN值是通过对存储在验证数据框中的数据重复调用mrCalc函数而生成的。结果存储在两个向量（MRs和FCNs）中，然后分别作为MR和FCN列添加到数据框。使用颜色代码绘制数据，分为阳性（反应性）或阴性（非反应性）。

```
An alternative way to select data from data frame is to use the function
subset. Indexing is obtained with the square bracket operators as shown in listing 1.1.
The function subset simplifies the procedure using parameters for condition and field
selection.
The library lattice provides a sophisticated way to display multivariate data. There
are several functions to draw virtually all types of plots, such as scatter plots
(xyplot), barplots (barchart), and box-and-whiskers plots (bwplot), which all have the
same syntax. Unlike the core R graphical functions, the high-level and low-level elements
are merged into the functions' call. The explanation of lattice's graphic is extensive
and goes beyond the scope of the present work, thus this will be a very cursory summary.
The basic call to the lattice plots is in the form y~x, but it is possible to group the
data and add an effect to the data as in y~x+2. Lattice's plots cannot be drawn inside
a graphical device such as the function jpg; they need to be saved into an object that
is then called in a graphical device.
Tables are exported from the R's environment to a stored file using the function
write.table. The selection of different separators allows to store CSV, TSV and other
types of files.
subset(x, condition, select, ...)
    x
    data frame to subset.
    condition
    the logical test that specified column's values need to pass to be selected.
    select
    list of columns to select from the data frame.
xyplot(y~x, group, ...)
    y, x
    the coordinates of the points.
    group
    labeling of the data.
write.table(x, file, append, quote, sep, eol , na, dec, row.names, col.names, ...)
    x
    the matrix or data frame to be written.
    file
    name of the file (" " indicates output to the console).
    append
    logical determining whether the data written has to be added to an existing file
    of the same name.
    quote
    logical determining whether strings should be quoted.
    sep
    field separator string (default = " "). Use "\t" for TSV and "," for CSV.
    eol
    string to print at the end of each line (default = "\n").
    na
    string to use for missing values in the data (default = "NA").
    dec
    string to use for decimal points (default = ".").
    row.names, col.names
    logical value indicating whether the row or column names are to be written, or a
    vector of names to be written.
```

## 清单3.6.

从缺失数据条目中清理出的扩增数据（在清单3.5中存储于文件amplificationCleaned.tsv）被重新加载到R环境中。callingShots函数允许操作员直观检查给定反应的扩增图，为其输入编码标签：阳性（1）、阴性（0）或不确定（-1），然后移动到下一个样本。该函数的实现如下。可以选择开始的反应编号；从而允许操作员在多个会话中筛选数据。开始反应编号通过readline函数从终端直接输入获取，并存储在变量set_start中。如果set_start为空，则假定操作员想要重新开始，变量Start被设置为1；否则Start取set_start中存储的值。将包含操作员提供标签（shot_calling）的向量被实例化，变量stopper允许操作员随时停止该函数。变量k和M是计数器，后者被设置为数据集中已知存在的反应数量（120）。验证数据框有一组新列，这些列源自评分者（此处为rater_1、rater_2）提供的结果。通过比较不同评分者的值，创建一个新列agreed。如果不同评分列中的所有评分相同，则给出等于一致评分（1或0）的标签，否则为-1。具有一致标签1的数据被绘制，标签为0的数据被绘制在它们之上。条目按因子分层。

```
The function readline reads an input directly from the terminal. The function as.factor is used to encode a vector as a factor. The levels of each factor and an associated label can be provided. The associated function is.factor tests if a vector is stratified in factors. The low-level graphical function grid adds a rectangular grid to a plot.
readline(prompt)
prompt
optional string to be displayed on screen.
as.factor(x, levels, labels, exclude, ordered, nmax)
x
a data vector.
levels
optional character vector of unique values.
labels
optional character vector of labels for the levels.
exclude
a vector of values to be excluded.
ordered
logical flag to determine if the levels should be regarded as ordered.
nmax
maximum number of levels.
grid(x, y, ...)
x, y
number of lines on the x or y axis. The default value (NULL) links these to the major ticks of the axis. The y value is optional, forcing y = x.
```

## 清单3.7.

创建一个新目录data，以有序方式存储k-means分类所需的文件。分析仅限于评分者一致的反应，这是通过对数据框进行索引获得的，从而排除不确定的反应（df$label != "Uncertain"）。通过生成10组数据框（存储在新文件夹data中）来获得k-means验证。每组包含一个包含80%反应的训练数据框和一个包含20%数据的测试数据框。这些组包含每个反应的标识号（索引）。数据集以RDS对象形式保存，作为文本文件的替代方案，并减少硬盘空间占用。由于label列最初包含三个水平（阳性、阴性和不确定），但现在只有两个水平（阳性和阴性），因此因子被覆盖为只有两个水平。为了给出该过程的示例，我仅使用变量i将第一组数据加载到内存中。索引包含在测试数据集中的反应被选中并存储在一个新数据框（train_set）中；对测试集进行相同操作。通过将'negative'分配给没有荧光信号的反应来创建新列，否则为'positive'；该分类按标签分层。

```
The function dir.create creates a new directory in a specified path. An alternative to store tables is to use R objects; these are compressed files that are read faster into memory and maintain additional characteristics such as levels. The R objects are written and read with saveRDS and readRDS, respectively, and have the extension '.rds'.
The function round rounds a fractional number to a specified decimal value. The associated functions are trunc, floor and ceiling. The function length returns the number of elements or levels of a vector. The function sample randomly extracts elements from a vector.
saveRDS(x, path)
readRDS(path)
x
an object to be saved.
path
a string containing the path and name of the object.
round(x, digits)
x
a floating point number.
digits
the number of decimals required.
```

