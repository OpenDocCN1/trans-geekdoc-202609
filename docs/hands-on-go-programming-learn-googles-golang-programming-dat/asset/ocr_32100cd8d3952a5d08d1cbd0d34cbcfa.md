```
func main() {

ch := make(chan int)

go func() {
for i := 0; i < 10; i++ {
ch <- i
}
close(ch)
}()

for val, ok := <-ch; ok; val, ok = <-ch {
fmt.Println(val)
}
}
```

The following will be the output for the above program:

0
1

2
3
4
5
6
7
8
9