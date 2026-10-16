```
import "io"

type tape struct {
    file io.ReadWriteSeeker
}

func (t *tape) Write(p []byte) (n int, err error) {
    t.file.Seek(0, 0)
    return t.file.Write(p)
}
```

Notice that we're only implementing `Write` now, as it encapsulates the `Seek` part. This means our `FileSystemStore` can just have a reference to a `Writer` instead.

```
//file_system_store.go
type FileSystemPlayerStore struct {
    database io.Writer
    league   League
}
```

# Update the constructor to use Tape

```
//file_system_store.go
func NewFileSystemPlayerStore(database io.ReadWriteSeeker) *File
    database.Seek(0, 0)
    league, _ := NewLeague(database)

    return &FileSystemPlayerStore{
        database: &tape{database},
        league:   league,
    }
}
```

Finally, we can get the amazing payoff we wanted by removing the `Seek` call from `RecordWin`. Yes, it doesn't feel much, but at least it means if we do any other kind of writes we can rely on our `Write` to behave how we need it to. Plus it will now let us test the potentially problematic code separately and fix it.