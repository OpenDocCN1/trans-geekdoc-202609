# 12.1 The error

Go has a built-in error type. The error can be assigned to a variable and returned from a function. Section 12.1.1 explains the error interface in more detail. Any method/function in Go which may cause unexpected behavior returns the error as the last returned value.

We have already seen in Section 2.3.1 that a function can return multiple values. When we say the last returned value as an error, it means a function returns multiple values and the last value is an error. It is not mandatory to return an error as the last return value but it is a convention.

There are many functions in the standard library which return the error. One example is os.Open as shown below which opens a file and returns *File and If something goes wrong like file not found or you do not have permission to open a file, this function would return an error value; otherwise, it will return file handler as a first return value and nil value for error as a second return value:

```
```go
func Open(name string) (*File, error) {
    return OpenFile(name, O_RDONLY, 0)
}
```
```

The caller of this function can check whether the error returned by the function is nil or not before processing the opened file. If