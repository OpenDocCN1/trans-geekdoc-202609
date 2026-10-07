```
01 package main
02
03 import "fmt"
04
05 func bubbleSort(numbers []int) {
06   n := len(numbers)
07   for i := 0; i < n; i++ {
08     if sweep(numbers, i) {
09       return
10     }
11   }
12 }
13
14 func sweep(numbers []int, currentPass int) bool {
15   var idx int
16   idxNext := idx + 1
17   n := len(numbers)
18   var swap bool
19
20   for idxNext < (n - currentPass) {
21     a := numbers[idx]
22     b := numbers[idxNext]
23     if a > b {
24       numbers[idx] = b
25       numbers[idxNext] = a
26       swap = true
27     }
28     idx++
29     idxNext = idx + 1
30   }
31   return swap
32 }
33
34 func main() {
35   org := []int(1, 3, 2, 4, 8, 6, 7, 2, 3, 0)
36   fmt.Println(org)
```