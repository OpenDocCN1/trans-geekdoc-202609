```
32 )
33
34 <- ctx.Done()
35 fmt.Println("counter is:", counter)
36 )
```

# 6.6.4 WithValue

A context can be defined by the information it contains. The context.WithValue function receives key and value arguments not returning a cancel function. In Example 6.18, we use a context with key "action" to define the action to be performed by a calculator function.

Example 6.18: Context WithValue.

```
1 package main
2
3 import (
4 "context"
5 "errors"
6 "fmt"
7 )
8
9 func main(ctx) {
10
11 f := func(ctx context.Context, a int, b int) (int, error) {
12
13 switch ctx.Value("action") {
14 case "+":
15 return a + b, nil
16 case "-":
17 return a - b, nil
18 default:
19 return 0, errors.New("unknown action")
20
21 }
22
23 ctx := context.WithValue(context.Background(), "action", "+")
24 r, err := f(ctx, 22, 20)
25 fmt.Println(r,err)
26 ctx2 := context.WithValue(context.Background(), "action", "-")
27 r, err = f(ctx, 22, 20)
28 fmt.Println(r,err)
29 )
```

![](bbox=[0.827, 0.345, 0.879, 0.417])

As can be extracted from the example, these contexts are not attached to temporal restrictions and their termination can be determined by other factors such as an invalid authentication token.

# 6.6.5 Parent contexts