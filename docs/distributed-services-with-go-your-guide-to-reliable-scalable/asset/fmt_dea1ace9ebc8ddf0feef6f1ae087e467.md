
Append(`\[\]byte`) persists the given bytes to the store. We write the length of the record so that, when we read the record, we know how many bytes to read. We write to the buffered writer instead of directly to the file to reduce the number of system calls and improve performance. If a user wrote a lot of small records, this would help a lot. Then we return the number of bytes written, which similar Go APIs conventionally do, and the position where the store holds the record in its file. The segment will use this position when it creates an associated index entry for this record.

Below Append, add the following Read method:

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  || ​**func**​ (s \*store) Read(pos ​**uint64**​) (\[\]​**byte**​, ​**error**​) { |
| --- | --- |
| ​  || s.mu.Lock() |
| ​  || ​**defer**​ s.mu.Unlock() |
| ​  || ​**if**​ err := s.buf.Flush(); err != nil { |
| ​  || ​**return**​ nil, err |
| ​  || } |
| ​  || size := make(\[\]​**byte**​, lenWidth) |
| ​  || ​**if**​ \_, err := s.File.ReadAt(size, ​**int64**​(pos)); err != nil { |
| ​  || ​**return**​ nil, err |
| ​  || } |
| ​  || b := make(\[\]​**byte**​, enc.Uint64(size)) |
| ​  || ​**if**​ \_, err := s.File.ReadAt(b, ​**int64**​(pos+lenWidth)); err != nil { |
| ​  || ​**return**​ nil, err |
| ​  || } |
| ​  || ​**return**​ b, nil |
| ​  || } |

Read(pos uint64) returns the record stored at the given position. First it flushes the writer buffer, in case we’re about to try to read a record that the buffer hasn’t flushed to disk yet. We find out how many bytes we have to read to get the whole record, and then we fetch and return the record. The compiler allocates byte slices that don’t escape the functions they’re declared in on the stack. A value escapes when it lives beyond the lifetime of the function call—if you return the value, for example.

Put this ReadAt method under Read:

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  || ​**func**​ (s \*store) ReadAt(p \[\]​**byte**​, off ​**int64**​) (​**int**​, ​**error**​) { |
| --- | --- |
| ​  || s.mu.Lock() |
| ​  || ​**defer**​ s.mu.Unlock() |
| ​  || ​**if**​ err := s.buf.Flush(); err != nil { |
| ​  || ​**return**​ 0, err |
| ​  || } |
| ​  || ​**return**​ s.File.ReadAt(p, off) |
| ​  || } |

ReadAt(p \[\]byte, off int64) reads len(p) bytes into p beginning at the off offset in the store’s file. It implements io.ReaderAt on the store type.

Last, add this Close method after ReadAt:

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  || ​**func**​ (s \*store) Close() ​**error**​ { |
| --- | --- |
| ​  || s.mu.Lock() |
| ​  || ​**defer**​ s.mu.Unlock() |
| ​  || err := s.buf.Flush() |
| ​  || ​**if**​ err != nil { |
| ​  || ​**return**​ err |
| ​  || } |
| ​  || ​**return**​ s.File.Close() |
| ​  || } |

Close persists any buffered data before closing the file.

Let’s test that our store works. Create a store_test.go file in the log directory with the following code:

[WriteALogPackage/internal/log/store_test.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store_test.go) 

| ​  || ​**package**​ log |
| --- | --- |
| --- | --- |
| ​  ||  |
| ​  || ​**import**​ ( |
| ​  || ​*"io/ioutil"*​ |
| ​  || ​*"os"*​ |
| ​  || ​*"testing"*​ |
| ​  || ) |
| ​  ||  |
| ​  || ​**var**​ ( |
| ​  || write = \[\]​**byte**​(​*"hello world"*​) |
| ​  || width = ​**uint64**​(len(write)) + lenWidth |
| ​  || ) |
| ​  ||  |
| ​  || ​**func**​ TestStoreAppendRead(t \*testing.T) { |
| ​  || f, err := ioutil.TempFile(​*""*​, ​*"store_append_read_test"*​) |
| ​  || require.NoError(t, err) |
| ​  || ​**defer**​ os.Remove(f.Name()) |
| ​  ||  |
| ​  || s, err := newStore(f) |
| ​  || require.NoError(t, err) |
| ​  ||  |
| ​  || testAppend(t, s) |
| ​  || testRead(t, s) |
| ​  || testReadAt(t, s) |
| ​  ||  |
| ​  || s, err = newStore(f) |
| ​  || require.NoError(t, err) |
| ​  || testRead(t, s) |
| ​  || } |
| ​  ||  |
| ​  || ​**func**​ testAppend(t \*testing.T, s \*store) { |
| --- | --- |
| ​  || t.Helper() |
| ​  || ​**for**​ i := ​**uint64**​(1); i < 4; i++ { |
| ​  || n, pos, err := s.Append(write) |
| ​  || require.NoError(t, err) |
| ​  || require.Equal(t, pos+n, width\*i) |
| ​  || } |
| ​  || } |
| ​  ||  |
| ​  || ​**func**​ testRead(t \*testing.T, s \*store) { |
| ​  || t.Helper() |
| ​  || ​**var**​ pos ​**uint64**​ |
| ​  || ​**for**​ i := ​**uint64**​(1); i < 4; i++ { |
| ​  || read, err := s.Read(pos) |
| ​  || require.NoError(t, err) |
| ​  || require.Equal(t, write, read) |
| ​  || pos += width |
| ​  || } |
| ​  || } |
| ​  ||  |
| ​  || ​**func**​ testReadAt(t \*testing.T, s \*store) { |
| ​  || t.Helper() |
| ​  || ​**for**​ i, off := ​**uint64**​(1), ​**int64**​(0); i < 4; i++ { |
| ​  || b := make(\[\]​**byte**​, lenWidth) |
| ​  || n, err := s.ReadAt(b, off) |
| ​  || require.NoError(t, err) |
| ​  || require.Equal(t, lenWidth, n) |
| ​  || off += ​**int64**​(n) |
| ​  ||  |
| ​  || size := enc.Uint64(b) |
| ​  || b = make(\[\]​**byte**​, size) |
| ​  || n, err = s.ReadAt(b, off) |
| ​  || require.NoError(t, err) |
| ​  || require.Equal(t, write, b) |
| ​  || require.Equal(t, ​**int**​(size), n) |
| ​  || off += ​**int64**​(n) |
| ​  || } |
| ​  || } |
| ​  ||  |
| ​  || ​**func**​ TestStoreClose(t \*testing.T) { |
| --- | --- |
| ​  || f, err := ioutil.TempFile(​*""*​, ​*"store_close_test"*​) |
| ​  || require.NoError(t, err) |
| ​  || ​**defer**​ os.Remove(f.Name()) |
| ​  || s, err := newStore(f) |
| ​  || require.NoError(t, err) |
| ​  || \_, \_, err = s.Append(write) |
| ​  || require.NoError(t, err) |
| ​  ||  |
| ​  || f, beforeSize, err := openFile(f.Name()) |
| ​  || require.NoError(t, err) |
| ​  ||  |
| ​  || err = s.Close() |
| ​  || require.NoError(t, err) |
| ​  ||  |
| ​  || \_, afterSize, err := openFile(f.Name()) |
| ​  || require.NoError(t, err) |
| ​  || require.True(t, afterSize > beforeSize) |
| ​  || } |
| ​  ||  |
| ​  || ​**func**​ openFile(name ​**string**​) (file \*os.File, size ​**int64**​, err ​**error**​) { |
| ​  || f, err := os.OpenFile( |
| ​  || name, |
| ​  || os.O_RDWR|os.O_CREATE|os.O_APPEND, |
| ​  || 0644, |
| ​  || ) |
| ​  || ​**if**​ err != nil { |
| ​  || ​**return**​ nil, 0, err |
| ​  || } |
| ​  || fi, err := f.Stat() |
| ​  || ​**if**​ err != nil { |
| ​  || ​**return**​ nil, 0, err |
| ​  || } |
| ​  || ​**return**​ f, fi.Size(), nil |
| ​  || } |
