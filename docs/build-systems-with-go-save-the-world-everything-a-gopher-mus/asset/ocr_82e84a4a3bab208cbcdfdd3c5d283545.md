```
<userId>Gopher</userId>
<score>1000</score>
</users>
<users>
<userId>Big</userId>
<score>10</score>
</users>
<users>
<userId>GGBoom</userId>
</users>
</UsersArray>
```

# 8.4 YAML

YAML [18] (Yet Another Markup Language) is a data serialization language that is human-readable and easy to parse. It is a superset of JSON [17] although it uses indentation to indicate nested entities. This format has gained popularity as a default format for configuration files. Go does not offer any YAML support in the standard library. However, we can find third-party modules with all the tools necessary to use this.

This section covers the utilization of go-yaml 17 marshal and unmarshal YAML content. Before running this code in your environment download the go-yaml code to your machine. Execute get gopkg.in/yaml.v2 to get the code. Refer to Section 2.1.1 for more details about importing third-party code or Chapter 12 to how to use it.

Go-yaml follows the same marshal/unmarshal approach we have already seen for JSON and XML formats. 8.9 prints some YAML encodings after using the Marshal function.

Example 8.9: YAML marshall.

```
1 package main
3 import (
4 	"gopkg.in/yaml.v2"
5 	"fmt"
6 )
7
8 func main() {
9 	number, err := yaml.Marshal(42)
10 if err != nil {
11 		panic(err)
12 }
13 	fmt.Println(string(number))
14
15 	float, _ := yaml.Marshal(3.14)
16 	fmt.Println(string(float))
17
18 	msg, _ := yaml.Marshal("This is a msg!!!")
19 	fmt.Println(string(msg))
20
21 	numbers, _ := yaml.Marshal([]int{1,2,3,5,6,8})
```

| 42 |
| 3.14 |
| This is a msg!!! |
| 1 |
| 2 |
| 3 |
| 5 |
| 8 |
| one: 1 |
| two: 2 |