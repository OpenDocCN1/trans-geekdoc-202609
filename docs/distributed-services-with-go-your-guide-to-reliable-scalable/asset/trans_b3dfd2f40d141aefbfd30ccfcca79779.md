
-   [WriteALogPackage/internal/log/log.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/log.go) 
    ``` 
    [WriteALogPackage/internal/log/log.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/log.go) 

    | ​  || ​**func**​ (l \*Log) Truncate(lowest ​**uint64**​) ​**error**​ { |

    | --- | --- |

    | ​  || l.mu.Lock() |

    | ​  || ​**defer**​ l.mu.Unlock() |

    | ​  || ​**var**​ segments \[\]\*segment |

    | ​  || ​**for**​ \_, s := ​**range**​ l.segments { |

    | ​  || ​**if**​ s.nextOffset <= lowest+1 { |

    | ​  || ​**if**​ err := s.Remove(); err != nil { |

    | ​  || ​**return**​ err |

    | ​  || } |

    | ​  || } |

    | ​  || segments = append(segments, s) |

    | ​  || } |

    | ​  || l.segments = segments |

    | ​  || ​**return**​ nil |

    | ​  || } |
    ```
    Truncate(lowest uint64) removes all segments whose highest offset is lower than lowest. 因为我们没有无限空间的磁盘，我们会定期调用 Truncate 来删除已经处理并（希望）不再需要的旧段。

    在 Truncate 之后，添加以下代码片段：

    ``` 
    [WriteALogPackage/internal/log/log.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/log.go) 

    | ​  || ​**func**​ (l \*Log) Reader() io.Reader { |

    | --- | --- |

    | ​  || l.mu.RLock() |

    | ​  || ​**defer**​ l.mu.RUnlock() |

    | ​  || readers := make([]io.Reader, len(l.segments)) |

    | ​  || ​**for**​ i, segment := ​**range**​ l.segments { |

    | ​  || readers[i] = &originReader{segment.store, 0} |

    | ​  || } |

    | ​  || ​**return**​ io.MultiReader(readers...) |

    | ​  || } |

    | ​  ||  |

    | ​  || ​**type**​ originReader ​**struct**​ { |

    | ​  || \*store |

    | ​  || off ​**int64**​ |

    | ​  || } |

    | ​  ||  |

    | ​  || ​**func**​ (o \*originReader) Read(p \[\]​**byte**​) (​**int**​, ​**error**​) { |

    | ​  || n, err := o.ReadAt(p, o.off) |

    | ​  || o.off += ​**int64**​(n) |

    | ​  || ​**return**​ n, err |

    | ​  || } |
    ```
    Reader 返回一个 io.Reader 以读取整个日志。我们将在实现协调一致时需要这种能力，以支持快照和恢复日志。Reader 使用 io.MultiReader 调用来连接各段的 store。段的 store 通过 originReader 类型包装，有两个原因。第一个原因是为了满足 io.Reader 接口，以便可以传递给 io.MultiReader 调用。第二个原因是为了确保从 store 的起始位置开始读取并读取其整个文件。
    ```
    ``` 
    [WriteALogPackage/internal/log/log.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/log.go) 

    | ​  || ​**func**​ (l \*Log) newSegment(off ​**uint64**​) ​**error**​ { |

    | --- | --- |

    | ​  || s, err := newSegment(l.Dir, off, l.Config) |

    | ​  || ​**if**​ err != nil { |

    | ​  || ​**return**​ err |

    | ​  || } |

    | ​  || l.segments = append(l.segments, s) |

    | ​  || l.activeSegment = s |

    | ​  || ​**return**​ nil |

    | ​  || } |
    ```
    newSegment(off int64) 创建一个新段，将该段追加到日志的段切片中，并将新段设为活动段，以便后续的追加操作写入它。
    ```
    ``` 
    [WriteALogPackage/internal/log/log_test.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/log_test.go) 

    | ​  || ​**package**​ log |

    | --- | --- |

    | ​  ||  |

    | ​  || ​**import**​ ( |

    | ​  || ​*"io/ioutil"*​ |

    | ​  || ​*"os"*​ |

    | ​  || ​*"testing"*​ |

    | ​  || ​*"github.com/stretchr/testify/require"*​ |

    | ​  || api ​*"github.com/travisjeffery/proglog/api/v1"*​ |

    | ​  || ​*"google.golang.org/protobuf/proto"*​ |

    | ​  || ) |

    | ​  ||  |

    | ​  || ​**func**​ TestLog(t \*testing.T) { |

    | ​  || ​**for**​ scenario, fn := ​**range**​ ​**map**​\[​**string**​\]​**func**​( |

    | ​  || t \*testing.T, log \*Log, |

    | ​  || ){ |

    | ​  || ​*"append and read a record succeeds"*​: testAppendRead, |

    | ​  || ​*"offset out of range error"*​: testOutOfRangeErr, |

    | ​  || ​*"init with existing segments"*​: testInitExisting, |

    | ​  || ​*"reader"*​: testReader, |

    | ​  || ​*"truncate"*​: testTruncate, |

    | ​  || } { |

    | ​  || t.Run(scenario, ​**func**​(t \*testing.T) { |

    | ​  || dir, err := ioutil.TempDir(​*""*​, ​*"store-test"*​) |

    | ​  || require.NoError(t, err) |

    | ​  || ​**defer**​ os.RemoveAll(dir) |

    | ​  ||  |

    | ​  || c := Config{} |

    | ​  || c.Segment.MaxStoreBytes = 32 |

    | ​  || log, err := NewLog(dir, c) |

    | ​  || require.NoError(t, err) |

    | ​  ||  |

    | ​  || fn(t, log) |

    | ​  || }) |

    | ​  || } |

    TestLog(\*testing.T) 定义了一个测试用例表，用于测试日志。我使用了表格来编写测试用例，以避免在每个测试用例中重复创建新日志的代码。

    现在，在 TestLog 函数下面定义测试用例：

    ``` 
    [WriteALogPackage/internal/log/log_test.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/log_test.go) 

    | ​  || ​**func**​ testAppendRead(t \*testing.T, log \*Log) { |

    | --- | --- |

    | ​  || append := &api.Record{ |

    | ​  || Value: \[\]​**byte**​(​*"hello world"*​), |

    | ​  || } |

    | ​  || off, err := log.Append(append) |

    | ​  || require.NoError(t, err) |

    | ​  || require.Equal(t, ​**uint64**​(0), off) |

    | ​  ||  |

    | ​  || read, err := log.Read(off) |

    | ​  || require.NoError(t, err) |

    | ​  || require.Equal(t, append.Value, read.Value) |

    | ​  || } |

    testAppendRead(\*testing.T, \*log.Log) 测试我们能够成功地向日志追加并从中读取记录。当我们向日志追加一个记录时，日志会返回它为该记录分配的偏移量。因此，当我们请求日志在该偏移量处的记录时，我们期望得到与我们追加的相同记录。

    [WriteALogPackage/internal/log/log_test.go] 

    | ​  || ​**func**​ testOutOfRangeErr(t \*testing.T, log \*Log) { |

    | --- | --- |

    | ​  || read, err := log.Read(1) |

    | ​  || require.Nil(t, read) |

    | ​  || require.Error(t, err) |

    | ​  || } |

    testOutOfRangeErr(\*testing.T, \*log.Log) 测试当我们尝试读取超出日志已存储偏移范围时，日志会返回错误。

    [WriteALogPackage/internal/log/log_test.go] 

    | ​  || ​**func**​ testInitExisting(t \*testing.T, o \*Log) { |

    | --- | --- |

    | ​  || append := &api.Record{ |

    | ​  || Value: \[\]​**byte**​(​*"hello world"*​), |

    | ​  || } |

    | ​  || ​**for**​ i := 0; i < 3; i++ { |

    | ​  || \_, err := o.Append(append) |

    | ​  || require.NoError(t, err) |

    | ​  || } |

    | ​  || require.NoError(t, o.Close()) |

    | ​  ||  |

    | ​  || off, err := o.LowestOffset() |

    | ​  || require.NoError(t, err) |

    | ​  || require.Equal(t, ​**uint64**​(0), off) |

    | ​  || off, err = o.HighestOffset() |

    | ​  || require.NoError(t, err) |

    | ​  || require.Equal(t, ​**uint64**​(2), off) |

    | ​  ||  |

    | ​  || n, err := NewLog(o.Dir, o.Config) |

    | ​  || require.NoError(t, err) |

    | ​  ||  |

    | ​  || off, err = n.LowestOffset() |

    | ​  || require.NoError(t, err) |

    | ​  || require.Equal(t, ​**uint64**​(0), off) |

    | ​  || off, err = n.HighestOffset() |

    | ​  || require.NoError(t, err) |

    | ​  || require.Equal(t, ​**uint64**​(2), off) |

    | ​  || } |

    testInitExisting(\*testing.T, \*log.Log) 测试当我们创建一个日志时，日志会从之前的日志实例存储的数据中初始化。我们在关闭前向原始日志追加三条记录。然后我们创建一个新日志，配置与旧日志相同的目录。最后，我们确认新日志已从旧日志存储的数据中初始化。

