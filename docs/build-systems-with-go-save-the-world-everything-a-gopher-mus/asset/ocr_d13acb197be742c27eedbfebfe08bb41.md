```
17 )
18 fmt.Println(">>> You're right!!!")
19 fmt.Println(strings.ToUpper(text))
20 }
```

The **scanner** can be particularly useful if we have a stream that has to be split into certain pieces. Example 7.9 uses a scanner to read lines from the standard input until the total accumulated length of the input strings exceeds 15 characters. The delimiter can be customized defining a split function¹⁴.

# **Example 7.9: Standard input reading using bufio scanners.**

```
1 package main
2 
3 import (
4  "bufio"
5  "fmt"
6  "os"
7 )
8 
9 func main() {
10  scanner := bufio.NewScanner(os.Stdin)
11  fmt.Println(">>> what do you have to say?\\n")
12  counter := 0
13  for scanner.Scan() {
14    text := scanner.Text()
15    counter := counter + len(text)
16    if counter > 15 {
17      break
18    }
19  }
20  fmt.Println("that's enough")
21 }
```

![](bbox=[0.725, 0.305, 0.875, 0.415])

Example 7.10 demonstrate how to use a `bufio.Writer` with the standard output. The program emulates a typing by printing the characters of a string with a temporal sleep between each character. Notice that the `Flush()` method has be invoked to force the buffer to be printed.

# **Example 7.10: Standard output writing.**

```
1 package main
2 
3 import (
4  "bufio"
5  "os"
6  "time"
7 )
8 
9 func main() {
10  writer := bufio.NewWriter(os.Stdout)
```

![](bbox=[0.735, 0.775, 0.875, 0.835])