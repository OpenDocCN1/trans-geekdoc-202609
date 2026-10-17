
Append函数（`Append(`[]byte`)`）会将给定的字节持久化到存储中。我们会先写入记录的长度，这样在读取记录时就能知道需要读取多少字节。我们会将数据写入缓冲写入器，而不是直接写入文件，以减少系统调用次数并提高性能。如果用户写入了大量的小记录，这将会带来很大的帮助。随后，我们会返回写入的字节数，这与 Go 标准 API 的惯例一致，同时也返回存储中保存该记录的位置。该段将在创建关联索引条目时使用该位置。

在 Append 方法下面，添加以下 Read 方法：

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  | **func** (s \*store) Read(pos **uint64**) (**[]byte**, **error**) { |
| --- | --- |
| ​  | s.mu.Lock() |
| ​  | **defer** s.mu.Unlock() |
| ​  | **if** err := s.buf.Flush(); err != nil { |
| ​  | **return** nil, err |
| ​  | } |
| ​  | size := make(**[]byte**, lenWidth) |
| ​  | **if** \_, err := s.File.ReadAt(size, **int64**(pos)); err != nil { |
| ​  | **return** nil, err |
| ​  | } |
| ​  | b := make(**[]byte**, enc.Uint64(size)) |
| ​  | **if** \_, err := s.File.ReadAt(b, **int64**(pos+lenWidth)); err != nil { |
| ​  | **return** nil, err |
| ​  | } |
| ​  | **return** b, nil |
| ​  | } |

Read(pos uint64) 方法会返回在给定位置存储的记录。首先它会刷新写入缓冲区，以防我们即将尝试读取的记录还未写入磁盘。随后我们会计算需要读取多少字节才能获取完整记录，并读取返回该记录。编译器会在函数作用域内为字节切片分配栈内存。当值在函数调用生命周期之外使用时（例如返回该值），该值会逃逸。

在 Read 方法下面，添加以下 ReadAt 方法：

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  | **func** (s \*store) ReadAt(p **[]byte**, off **int64**) (**int**, **error**) { |
| --- | --- |
| ​  | s.mu.Lock() |
| ​  | **defer** s.mu.Unlock() |
| ​  | **if** err := s.buf.Flush(); err != nil { |
| ​  | **return** 0, err |
| ​  | } |
| ​  | **return** s.File.ReadAt(p, off) |
| ​  | } |

ReadAt(p []byte, off int64) 方法会将 len(p) 字节读取到 p，起始偏移为 off，并在 store 类型上实现 io.ReaderAt 接口。

最后，在 ReadAt 方法下面添加以下 Close 方法：

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  | **func** (s \*store) Close() **error** { |
| --- | --- |
| ​  | s.mu.Lock() |
| ​  | **defer** s.mu.Unlock() |
| ​  | err := s.buf.Flush() |
| ​  | **if** err != nil { |
| ​  | **return** err |
| ​  | } |
| ​  | **return** s.File.Close() |
| ​  | } |

Close 方法会在关闭文件前持久化任何缓冲数据。

现在，我们来测试我们的存储是否正常工作。在日志目录下创建一个 store_test.go 文件，包含以下代码：

[WriteALogPackage/internal/log/store_test.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store_test.go) 

| ​  | **package** log |
| --- | --- |
| --- | --- |
| ​  | |
| ​  | **import** ( |
| ​  | *"io/ioutil"* |
| ​  | *"os"* |
| ​  | *"testing"* |
| ​  | ) |
| ​  | |
| ​  | **var** ( |
| ​  | write = **[]byte**("hello world") |
| ​  | width = **uint64**(len(write)) + lenWidth |
| ​  | ) |
| ​  | |
| ​  | **func** TestStoreAppendRead(t **\*testing.T**) { |
| ​  | f, err := ioutil.TempFile("", "store_append_read_test") |
| ​  | require.NoError(t, err) |
| ​  | **defer** os.Remove(f.Name()) |
| ​  | |
| ​  | s, err := newStore(f) |
| ​  | require.NoError(t, err) |
| ​  | |
| ​  | testAppend(t, s) |
| ​  | testRead(t, s) |
| ​  | testReadAt(t, s) |
| ​  | |
| ​  | s, err = newStore(f) |
| ​  | require.NoError(t, err) |
| ​  | testRead(t, s) |
| ​  | } |
| ​  | |
| ​  | **func** testAppend(t **\*testing.T**, s **\*store**) { |
| --- | --- |
| ​  | t.Helper() |
| ​  | **for** i := **uint64**(1); i < 4; i++ { |
| ​  | n, pos, err := s.Append(write) |
| ​  | require.NoError(t, err) |
| ​  | require.Equal(t, pos+n, width*i) |
| ​  | } |
| ​  | } |
| ​  | |
| ​  | **func** testRead(t **\*testing.T**, s **\*store**) { |
| --- | --- |
| ​  | t.Helper() |
| ​  | **var** pos **uint64** |
| ​  | **for** i := **uint64**(1); i < 4; i++ { |
| ​  | read, err := s.Read(pos) |
| ​  | require.NoError(t, err) |
| ​  | require.Equal(t, write, read) |
| ​  | pos += width |
| ​  | } |
| ​  | } |
| ​  | |
| ​  | **func** testReadAt(t **\*testing.T**, s **\*store**) { |
| --- | --- |
| ​  | t.Helper() |
| ​  | **for** i, off := **uint64**(1), **int64**(0); i < 4; i++ { |
| ​  | b := make(**[]byte**, lenWidth) |
| ​  | n, err := s.ReadAt(b, off) |
| ​  | require.NoError(t, err) |
| ​  | require.Equal(t, lenWidth, n) |
| ​  | off += **int64**(n) |
| ​  | |
| ​  | size := enc.Uint64(b) |
| ​  | b = make(**[]byte**, size) |
| ​  | n, err = s.ReadAt(b, off) |
| ​  | require.NoError(t, err) |
| ​  | require.Equal(t, write, b) |
| ​  | require.Equal(t, **int**(size), n) |
| ​  | off += **int64**(n) |
| ​  | } |
| ​  | } |
| ​  | |
| ​  | **func** TestStoreClose(t **\*testing.T**) { |
| --- | --- |
| ​  | f, err := ioutil.TempFile("", "store_close_test") |
| ​  | require.NoError(t, err) |
| ​  | **defer** os.Remove(f.Name()) |
| ​  | s, err := newStore(f) |
| ​  | require.NoError(t, err) |
| ​  | \_, \_, err = s.Append(write) |
| ​  | require.NoError(t, err) |
| ​  | |
| ​  | f, beforeSize, err := openFile(f.Name()) |
| ​  | require.NoError(t, err) |
| ​  | |
| ​  | err = s.Close() |
| ​  | require.NoError(t, err) |
| ​  | |
| ​  | \_, afterSize, err := openFile(f.Name()) |
| ​  | require.NoError(t, err) |
| ​  | require.True(t, afterSize > beforeSize) |
| ​  | } |
| ​  | |
| ​  | **func** openFile(name **string**) (**\*os.File**, **int64**, **error**) { |
| --- | --- |
| ​  | f, err := os.OpenFile( |
| ​  | name, |
| ​  | os.O_RDWR|os.O_CREATE|os.O_APPEND, |
| ​  | 0644, |
| ​  | ) |
| ​  | **if** err != nil { |
| ​  | **return** nil, 0, err |
| ​  | } |
| ​  | fi, err := f.Stat() |
| ​  | **if** err != nil { |
| ​  | **return** nil, 0, err |
| ​  | } |
| ​  | **return** f, fi.Size(), nil |
| ​  | } |

