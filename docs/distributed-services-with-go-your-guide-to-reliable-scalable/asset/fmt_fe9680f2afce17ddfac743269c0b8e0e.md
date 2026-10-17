
Let’s test our index. Create an index_test.go file in internal/log starting with the following code:

`/WriteALogPackage/internal/log/index_test.go` 

| || **package** log |

| --- | --- |

| || |

| || **import** ( |

| || *"io"* |

| || *"io/ioutil"* |

| || *"os"* |

| || *"testing"* |

| ||  |

| || *"github.com/stretchr/testify/require"* |

| || ) |

| ||  |

| || **func** TestIndex(t *testing.T) { |

| || f, err := ioutil.TempFile(os.TempDir(), "index_test") |

| || require.NoError(t, err) |

| || **defer** os.Remove(f.Name()) |

| || c := Config{} |

| || c.Segment.MaxIndexBytes = 1024 |

| || idx, err := newIndex(f, c) |

| || require.NoError(t, err) |

| || _, _, err = idx.Read(-1) |

| || require.Error(t, err) |

| || require.Equal(t, f.Name(), idx.Name()) |

| ||  |

| || entries := [ ]struct { |

| || Off uint32 |

| || Pos uint64 |

| || }{ |

| || {Off: 0, Pos: 0}, |

| || {Off: 1, Pos: 10}, |

| || } |

This code sets up the test. We create an index file and make it big enough to contain our test entries via the Truncate call. We have to grow the file before we use it because we memory‑map the file to a slice of bytes and if we didn’t increase the size of the file before we wrote to it, we’d get an out‑of‑bounds error.

Finally, add the following code beneath the previous snippet to finish the test:

`/WriteALogPackage/internal/log/index_test.go` 

| || **for**​ _ , want := ​**range**​ entries { |

| --- | --- |

| || err = idx.Write(want.Off, want.Pos) |

| || require.NoError(t, err) |

| ||  |

| || _ , pos, err := idx.Read(​**int64**​(want.Off)) |

| || require.NoError(t, err) |

| || require.Equal(t, want.Pos, pos) |

| || } |

| ||  |

| || *// index and scanner should error when reading past existing entries*​ |

| || _ , _ , err = idx.Read(​**int64**​(len(entries))) |

| || require.Equal(t, io.EOF, err) |

| || _ = idx.Close() |

| ||  |

| || *// index should build its state from the existing file*​ |

| || f, _ = os.OpenFile(f.Name(), os.O\_RDWR, 0600) |

| || idx, err = newIndex(f, c) |

| || require.NoError(t, err) |

| || off, pos, err := idx.Read(-1) |

| || require.NoError(t, err) |

| || require.Equal(t, ​**uint32**​(1), off) |

| || require.Equal(t, entries[1].Pos, pos) |

| || } |

We iterate over each entry and write it to the index. We check that we can read the same entry back via the Read method. Then we verify that the index and scanner error when we try to read beyond the number of entries stored in the index. And we check that the index builds its state from the existing file, for when our service restarts with existing data.

We need to configure the max size of a segment’s store and index. Let’s add a config struct to centralize the log’s configuration, making it easy to configure the log and use the configs throughout the code. Create an internal/log/config.go file with the following code:

`/WriteALogPackage/internal/log/config.go` 

| || **package** log |

| --- | --- |

| ||  |

| || **type**​ Config ​**struct**​ { |

| || Segment ​**struct**​ { |

| || MaxStoreBytes ​**uint64**​ |

| || MaxIndexBytes ​**uint64**​ |

| || InitialOffset ​**uint64**​ |

| || } |

| || } |

That wraps up the code for store and index types, which make up the lowest level of our log. Now let’s code the segment.

### Create the Segment

The segment wraps the index and store types to coordinate operations across the two. For example, when the log appends a record to the active segment, the segment needs to write the data to its store and add a new entry in the index. Similarly for reads, the segment needs to look up the entry from the index and then fetch the data from the store.

To get started, create a file called segment.go in internal/log that starts with the following code:

`/WriteALogPackage/internal/log/segment.go` 

| || **package** log |

| --- | --- |

| ||  |

| || **import**​ ( |

| || *"fmt"*​ |

| || *"os"*​ |

| || *"path"*​ |

| ||  |

| || api *"github.com/travisjeffery/proglog/api/v1"*​ |

| || *"google.golang.org/protobuf/proto"*​ |

| || ) |

| ||  |

| || **type**​ segment ​**struct**​ { |

| || store *store |

| || index *index |

| || baseOffset, nextOffset ​**uint64**​ |

| || config Config |

| || } |

Our segment needs to call its store and index files, so we keep pointers to those in the first two fields. We need the next and base offsets to know what offset to append new records under and to calculate the relative offsets for the index entries. And we put the config on the segment so we can compare the store file and index sizes to the configured limits, which lets us know when the segment is maxed out.

Below the previous snippet, add the following newSegment function:

`/WriteALogPackage/internal/log/segment.go` 

| || **func**​ newSegment(dir ​**string**​, baseOffset ​**uint64**​, c Config) (\*segment, ​**error**​) { |

| --- | --- |

| || s := &segment{ |

| || baseOffset: baseOffset, |

| || config: c, |

| || } |

| || **var**​ err ​**error**​ |

| || storeFile, err := os.OpenFile( |

| || path.Join(dir, fmt.Sprintf(​*"%d%s"*​, baseOffset, ​"*.store"*​)), |

| || os.O\_RDWR|os.O\_CREATE|os.O\_APPEND, |

| || 0644, |

| || ) |

| || ​**if**​ err != nil { |

| || ​**return**​ nil, err |

| || } |

| || ​**if**​ s.store, err = newStore(storeFile); err != nil { |

| || ​**return**​ nil, err |

| || } |

| || indexFile, err := os.OpenFile( |

| || path.Join(dir, fmt.Sprintf(​*"%d%s"*​, baseOffset, ​"*.index"*​)), |

| || os.O\_RDWR|os.O\_CREATE, |

| || 0644, |

| || ) |

| || ​**if**​ err != nil { |

| || ​**return**​ nil, err |

| || } |

| || ​**if**​ s.index, err = newIndex(indexFile, c); err != nil { |

| || ​**return**​ nil, err |

| || } |

| || ​**if**​ off, \_, err := s.index.Read(-1); err != nil { |

| || s.nextOffset = baseOffset |

| || } ​**else**​ { |

| || s.nextOffset = baseOffset + ​**uint64**​(off) + 1 |

| || } |

| || ​**return**​ s, nil |

| || } |

The log calls newSegment when it needs to add a new segment, such as when the current active segment hits its max size. We open the store and index files and pass the os.O\_CREATE file mode flag as an argument to os.OpenFile to create the files if they don’t exist yet. When we create the store file, we pass the os.O\_APPEND flag to make the operating system append to the file when writing. Then we create our index and store with these files. Finally, we set the segment’s next offset to prepare for the next appended record. If the index is empty, then the next record appended to the segment would be the first record and its offset would be the segment’s base offset. If the index has at least one entry, then that means the offset of the next record written should take the offset at the end of the segment, which we get by adding 1 to the base offset and relative offset. Our segment is ready to write to and read from the log—once we’ve written those methods!

Next, below newSegment put the following Append method:

`/WriteALogPackage/internal/log/segment.go` 
