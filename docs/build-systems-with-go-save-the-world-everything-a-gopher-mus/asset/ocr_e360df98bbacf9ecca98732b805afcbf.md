The Marshal function converts booleans, integers, floats, strings, arrays, and slices into its corresponding JSON representation. Example 8.3 shows the output generated after marshalling types. Note that the Marshal function returns a []byte with the JSON representation of the input and error in case of failure.

# Example 8.3: JSON marshalling.

```
1 package main
2
3 import (
4 "encoding/json"
5 "fmt"
6 )
7
8 func main() {
9 number, err := json.Marshal(42)
10 if err != nil {
11 panic(err)
12 }
13 fmt.Println(string(number))
14
15 float, _ := json.Marshal(3.14)
16 fmt.Println(string(float))
17
18 msg, _ := json.Marshal("This is a msg!!")
19 fmt.Println(string(msg))
20
21 numbers, _ := json.Marshal([]int{1,1,2,3,5,8})
22 fmt.Println(string(numbers))
23
24 aMap, _ := json.Marshal(map[string]int{"one":1,"two":2})\n25 fmt.Println(string(aMap))
26 }
```

If a JSON is correctly formed, the unmarshal function can convert it to a previously known type. Example 8.4 recovers JSON representations of int and map[string]int. The unmarshalling process requires to convert to a type compatible with the data to be marshalled and returns an error if the process fails. That the output from this example is the string representation of Go types, not JSON representations.

# Example 8.4: JSON unmarshalling.

```
1 package main
2
3 import (
4 "encoding/json"
5 "fmt"
6 )
7
8 func main() {
```

```
42
map[one:1
two:2]
```