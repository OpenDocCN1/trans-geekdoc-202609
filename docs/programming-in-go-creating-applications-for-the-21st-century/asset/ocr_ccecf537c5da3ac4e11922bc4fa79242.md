# Chapter 7. Concurrent Programming

```
}
  return
}
infoChan <- fileInfo(hash.Sum(nil), info.Size(), filename)
}
```

This function is called from the current goroutine or in a newly created goroutine to compute the file's SHA-1 and to send the file's details to the infoChan channel.

If the done variable is not nil, this function has been called in a goroutine, so we defer a call to the done() function (which simply calls a call to the sync.WaitGroup.Done() method;352). This is to ensure that for every sync.WaitGroup.Add(1), there is a corresponding sync.WaitGroup.Done() call, since this is essential to the correct operation of the sync.WaitGroup() function(). If the variable is nil we ignore it.

Next, we open the file for reading, and defer closing it, in the usual way. The standard library's crypto/sha package provides the sha.New() function which returns a value that satisfies the hash.Interface. This interface provides a Sum() method that returns the hash value (i.e., the 20-byte SHA-1 hash in this case), and also fulfills the io.Writer interface. (We pass in nil to existing [byte] to make the Sum() method give us a new [byte]; alternatively, we could pass it an [byte] to which it will append the hash sum.)

We could have read in the entire contents of the file and then called the sha.Write() method to write the file into the hash, but we have opted to take a much more efficient approach and used the io.Copy() function instead. This function takes a writer to write to (in this case the hash), and a reader to read from (here, the open file), and copies from the latter to the former. When the copy has finished, it returns nil or an error. Since the SHA-1 hash can work on chunks of data at a time, the maximum amount of memory used by the io.Copy() call will be the size of the buffer used by the SHA-1 plus some overhead. If we had read the entire file into memory first, we would have used the same amount of buffer and overhead memory—plus enough memory to store the whole file. So, for larger files, using io.Copy() achieves real savings.

Once the computation is done we send a fileInfo to the infoChan channel with the SHA-1 value, the file's size (available from the os.FileInfo passed to the processFile() function from the walker function), and the filename (including the full path).

```
type pathsInfo struct {
  size int64
  paths []string
}
```