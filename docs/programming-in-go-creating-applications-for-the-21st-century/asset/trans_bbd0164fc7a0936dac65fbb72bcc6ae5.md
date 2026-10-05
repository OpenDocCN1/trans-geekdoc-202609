

## 8.2. 归档文件

我们首先以常见的方式打开要压缩的文件以准备读取，并使用 `defer` 延迟关闭。

接下来，我们调用 `os.File.Stat()` 方法获取文件的时间戳和权限值，并封装为 `os.FileInfo`。然后，我们将此值传递给 `zip.FileInfoHeader` 函数，该函数返回一个 `zip.FileHeader` 值，其中填充了时间戳、权限和文件名。我们并不强制使用与原始文件名相同的名称，在这里，我们选择用经过处理后的版本（在 `zip.FileHeader.Name` 字段中）覆盖文件名。

使用头信息（header），我们调用 `zip.CreateHeader()` 函数并将头信息作为参数传递。这会在 .zip 归档中创建一个带有头信息时间戳、权限和文件名的条目，并返回一个 `io.Writer`，我们可以用它写入要归档的文件内容。为了这个目的，我们使用了 `io.Copy()` 函数——它返回复制的字节数（我们将其丢弃了）以及 `nil` 或错误。

如果在任何点发生错误，我们立即将其返回给调用者进行处理。如果没有发生错误，在最后，.zip 归档就包含了给定的文件。

如果归档中包含绝对路径或包含 `.path` 组件路径的文件，当我们在解压归档时，可能会意外覆盖文件。为了降低这种风险，我们对存储在归档中的每个文件的名称进行处理。

`sanitizedName()` 函数去除了前面的盘器号和冒号（如果有），然后剥离任何领先目录分隔符、点以及 `..` 路径组件。它还会强制将文件分隔符转换为斜杠。

### 8.2.2. 创建可选压缩的 Tar 包

创建 tar 包（tarballs）与 .zip 归档非常相似，主要区别在于我们将所有数据写入同一个写入器，并且我们必须在每个文件的数据之前写入完整的头信息，而不仅仅是文件名。我们 `pack` 程序的实现使用了 `createTar()` 和 `writeFileToTar()` 函数。

```go
func createTar(filename string, files []string) error {
    file, err := os.Create(filename)
    if err != nil {
        return err
    }

    defer file.Close()
    var fileWriter io.Closer = file
    if strings.HasSuffix(filename, ".gz") {
        fileWriter = gzip.NewWriter(file)
        defer fileWriter.Close()
    }

    writer := tar.NewWriter(fileWriter)
    defer writer.Close()
    for _, name := range files {
        if err := writeFileToTar(writer, name); err != nil {
            return err
        }
    }
    return nil
}
```

此函数创建给定的 tar 包文件，如果文件名后缀指示 tar 包应该被压缩，则添加 gzip 过滤。`gzip.NewWriter()` 返回一个 *gzip.Writer*，它实现了 `io.WriteCloser` 接口（就像打开的 *os.File* 一样）。

一旦文件准备好写入，我们我们就创建一个 *tar.Writer* 向其写入。然后，我们遍历所有文件并尝试逐个写入每一个文件。

```go
func writeFileToTar(writer *tar.Writer, filename string) error {
    file, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer file.Close()
    stat, err := file.Stat(filename)
    if err != nil {
        return err
    }
    header := &tar.Header{
        Name: sanitizedName(filename),
        Mode: int64(stat.Mode()),
        Uid: os.Getuid(),
        Gid: os.Getgid(),
        Size: stat.Size(),
        ModTime: stat.ModTime(),
    }
    if err := writer.WriteHeader(header); err != nil {
        return err
    }
    _, err = io.Copy(writer, file)
    return err
}
```

此函数首先打开给定的文件进行读取，并延迟关闭文件。然后，它对文件进行 `stat` 操作，以获取文件的模式、大小和修改日期/时间——这些数据被用于填充为写入 tar 包的每个文件必须创建的 *tar.Header*。（此外，我们还设置了头信息的用户 ID 和组 ID；这些在 Unix 类系统上会被使用。）我们至少应该设置文件的文件名（`Name` 字段），并且我们必须将其 `Size` 字段设置为文件的大小，否则 tar 包将是无效的。

一旦创建并填充了 *tar.Header*，我们将头信息写入 tar 包。最后，我们将文件内容拷贝到 tar 包中。

### 8.2.3. 解压 Zip 归档

解压 .zip 文件与压缩一个文件一样简单，只是如果归档中包含包含路径的文件名，我们必须重新创建目录结构。

```go
func unpackZip(filename string) error {
	reader, err := zip.OpenReader(filename)
	if err != nil {
		return err
	}
	defer reader.Close()
	for _, zipFile := range reader.Reader.File {
		name := sanitizedName(zipFile.Name)
		mode := zipFile.Mode()
		if mode.IsDir() {
			if err := os.MkdirAll(name, 0755); err != nil {
				return err
			}
		} else {
			if err := unpackZippedFile(name, zipFile); err != nil {
				return err
			}
		}
	}
	return nil
}
```

此函数通过打开给定的文件进行读取并延迟关闭文件。然后，它对文件进行 `stat` 操作以获取文件的模式、大小和修改日期/时间——这些数据被用于填充为写入 tar 包的每个文件必须创建的 *tar.Header*。（此外，我们设置了头信息的用户 ID 和组 ID；这些在 Unix 类系统上会被使用。）我们至少应该设置文件的文件名（`Name` 字段），并且我们必须将其 `Size` 字段设置为文件的大小，否则 tar 包将是无效的。

一旦创建并填充了 *tar.Header*，我们将头信息写入 tar 包。最后，我们将文件内容拷贝到 tar 包中。

> 如前所述，文件权限标志传统上使用八进制数字，666 是文件一个合理的选择。对于目录，755 是合理的选择。

此函数从 .zip 归档中提取单个文件并将其写入文件系统。它以通常的方式创建要写入的文件。然后它打开 .zip 文件并将归档数据写入新创建的文件。

在最后，如果没有发生错误，函数将打印它创建的文件名，如果处理后的文件名不同，则带括号显示原始文件名。

此外，*zip.File 类型还有其他实用的方法，例如 `zip.File.Mode()`（在 `unpackZip()` 函数中使用过）、`zip.File.ModTime()`（返回文件的修改时间为 `time.Time`）以及 `zip.File.FileInfo()` 返回文件的 `os.FileInfo` 值。

### 8.2.4. 解压可选压缩的 Tar 包

解压 tar 文件比打包它们稍微简单。然而，正如我们解压 .zip 文件一样，如果归档中包含包含路径的文件，我们必须重新创建目录结构。

```go
func unpackTar(filename string) error {
	file, err := os.Open(filename)
	if err != nil {
		return err
	}
	defer file.Close()
	var fileReader io.ReadCloser = file
	if strings.HasSuffix(filename, ".gz") {
		if fileReader, err = gzip.NewReader(file); err != nil {
			return err
		}
		defer fileReader.Close()
	}
	reader := tar.NewReader(fileReader)
	return unpackTarFiles(reader)
}
```

