
| | varName | ( |
| | | offWidth uint64 = 4 |
| | | posWidth uint64 = 8 |
| | | entWidth = offWidth + posWidth |
| | | ) |
| | | ) |
| | | ) |
| | | type index struct { |
| | | file *os.File |
| | | mmap gommap.MMap |
| | | size uint64 |
| | | } |

We use the `*Width` constants throughout the index, so like with the store’s variables and constants, we put the constants at the top of the file to make them easy to find. The `*Width` constants define the number of bytes that make up each index entry.

Our index entries contain two fields: the record’s offset and its position in the store file. We store offsets as uint32s and positions as uint64s, so they take up 4 and 8 bytes of space, respectively. We use the `entWidth` to jump straight to the position of an entry given its offset since the position in the file is offset * entWidth.

`index` defines our index file, which comprises a persisted file and a memory‑mapped file. The `size` tells us the size of the index and where to write the next entry appended to the index.

Now add the following `newIndex` function below the `index`:

``` 
func newIndex(f *os.File, c Config) (*index, error) {
    idx := &index{
        file: f,
    }
    fi, err := os.Stat(f.Name())
    if err != nil {
        return nil, err
    }
    idx.size = uint64(fi.Size())
    if err = os.Truncate(f.Name(), int64(c.Segment.MaxIndexBytes)); err != nil {
        return nil, err
    }
    if idx.mmap, err = gommap.Map(f.Fd(), gommap.PROT_READ|gommap.PROT_WRITE, gommap.MAP_SHARED); err != nil {
        return nil, err
    }
    return idx, nil
}
```

`newIndex` creates an index for the given file. We create the index and save the current size of the file so we can track the amount of data in the index file as we add index entries. We grow the file to the max index size before memory‑mapping the file and then return the created index to the caller.

Next, add the following `Close` method below `newIndex`:

``` 
func (i *index) Close() error {
    if err := i.mmap.Sync(gommap.MS_SYNC); err != nil {
        return err
    }
    if err := i.file.Sync(); err != nil {
        return err
    }
    if err := i.file.Truncate(int64(i.size)); err != nil {
        return err
    }
    return i.file.Close()
}
```

`Close` makes sure the memory‑mapped file has synced its data to the persisted file and that the persisted file has flushed its contents to stable storage. Then it truncates the persisted file to the amount of data that’s actually in it and closes the file.

Now that we’ve seen the code for both opening and closing an index, we can discuss what this growing and truncating the file business is all about.

When we start our service, the service needs to know the offset to set on the next record appended to the log. The service learns the next record’s offset by looking at the last entry of the index, a simple process of reading the last 12 bytes of the file. However, we mess up this process when we grow the files so we can memory‑map them. (The reason we resize them now is that, once they’re memory‑mapped, we can’t resize them, so it’s now or never.) We grow the files by appending empty space at the end of them, so the last entry is no longer at the end of the file—instead, there’s some unknown amount of space between this entry and the file’s end. This space prevents the service from restarting properly. That’s why we shut down the service by truncating the index files to remove the empty space and put the last entry at the end of the file once again. This graceful shutdown returns the service to a state where it can restart properly and efficiently.

| Handling Ungraceful Shutdowns |
| --- |
| ![images/aside-icons/warning.png](Images/warning.png) || A graceful shutdown occurs when a service finishes its ongoing tasks, performs its processes to ensure there’s no data loss, and prepares for a restart. If your service crashes or its hardware fails, you’ll experience an ungraceful shutdown. An example of an ungraceful shutdown for the service we’re building would be if it lost power before it finished truncating its index files. You handle ungraceful shutdowns by performing a sanity check when your service restarts to find corrupted data. If you have corrupted data, you can rebuild the data or replicate the data from an uncorrupted source. The log we’re building doesn’t handle ungraceful shutdowns because I wanted to keep the code simple. |

And now back to our regularly scheduled programming.

Add the following `Read` method below `newIndex`:

``` 
func (i *index) Read(in int64) (out uint32, pos uint64, err error) {
    if i.size == 0 {
        return 0, 0, io.EOF
    }
    if in == -1 {
        out = uint32((i.size / entWidth) - 1)
    } else {
        out = uint32(in)
    }
    pos = uint64(out) * entWidth
    if i.size < pos+entWidth {
        return 0, 0, io.EOF
    }
    out = enc.Uint32(i.mmap[pos : pos+offWidth])
    pos = enc.Uint64(i.mmap[pos+offWidth : pos+entWidth])
    return out, pos, nil
}
```

`Read(int64)` takes in an offset and returns the associated record’s position in the store. The given offset is relative to the segment’s base offset; 0 is always the offset of the index’s first entry, 1 is the second entry, and so on. We use relative offsets to reduce the size of the indexes by storing offsets as uint32s. If we used absolute offsets, we’d have to store the offsets as uint64s and require four more bytes for each entry. Four bytes doesn’t sound like much, until you multiply it by the number of records people often use distributed logs for, which with a company like LinkedIn is trillions of records every day. Even relatively small companies can make billions of records per day.

Now add the following `Write` method below `Read`:

``` 
func (i *index) Write(off uint32, pos uint64) error {
    if uint64(len(i.mmap)) < i.size+entWidth {
        return io.EOF
    }
    enc.PutUint32(i.mmap[i.size:i.size+offWidth], off)
    enc.PutUint64(i.mmap[i.size+offWidth:i.size+entWidth], pos)
    i.size += uint64(entWidth)
    return nil
}
```

`Write(off uint32, pos uint64)` appends the given offset and position to the index. First, we validate that we have space to write the entry. If there’s space, we then encode the offset and position and write them to the memory‑mapped file. Then we increment the position where the next write will go.

Add this `Name` method to return the index’s file path:

``` 
func (i *index) Name() string {
    return i.file.Name()
}
```
