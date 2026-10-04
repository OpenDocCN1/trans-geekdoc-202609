```
24 err := t.Execute(os.Stdout, u1)
25 if err != nil {
26   panic(err)
27 }
28 err := t.Execute(os.Stdout, u2)
29 if err != nil {
30   panic(err)
31 }
32 }
```

For binary variable comparisons templates use a different syntax than the one used in Go.
Check Table 10.1 for a list of equivalences.

| | |
|---||
| < | lt |
| > | gt |
| <= | le |
| >= | ge |
| == | eq |
| != | ne |

# **Table 10.1:** Comparison operators in Go and templates.

Example 10.3 defines personalized messages depending on the score of every user.

# **Example 10.3:** if/else binary variable comparisons.

```
1 package main
2
3 import (
4   "text/template"
5   "os"
6   )
7
8 type User struct {
9   Name string
10  Score uint32
11 }
12
13 const Msg = '
14 {{.Name}} your score is {{.Score}}
15 your level is:
16 {{if le .Score 50}}Amateur
17 {{else if le .Score 80}}Professional
18 {{else}}Expert
19 {{end}}
20 ''
21
22 func main() {
```

![](bbox=[0.757, 0.576, 0.882, 0.693])