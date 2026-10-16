
1 包 main
2 
3 导入 "fmt"
4 
5 类型 Point 结构体 {
6  x float32
7  y float32
8 }
9 
10 类型 Vehicle 结构体 {
11  velocity float32
12  Point
13 }
14 
15 类型 Spaceship 接口 {
16  fly()
17  land()
18  position() Point
19 }
20 
21 方法 (v *Vehicle) fly() {
22  v.velocity = 10
23 }
24 
25 方法 (v *Vehicle) land() {
26  v.velocity = 0
27 }
28 
29 方法 (v Vehicle) position() Point {
30  返回 v.Point
31 }
32 
33 func main() {
We are now able to invoke the `Help()` function from *main.go* like so:
34 
35 ```
36 if (condVar > someVal) {console.log("xxx")}
37 ```
