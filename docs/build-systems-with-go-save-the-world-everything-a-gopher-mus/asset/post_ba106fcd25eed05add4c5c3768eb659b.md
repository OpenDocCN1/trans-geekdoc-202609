
```
7 fmt.Println(aux)
9 aux = 10
11 fmt.Println(aux)
13 aux = "hello"
14 fmt.Println(aux)
```

The empty interface is a very ambiguous context for a typed language Go. In many situations, it is necessary to know the underlying data type of the interface. Otherwise, it is not possible to know how to proceed with that data. A practical way to define the variable is using a switch statement. Example 4.12 fills a slice of empty interfaces with an integer, a string, and a boolean. The switch statement can extract the type of value in runtime. This can be used to define how to operate with the value. In the example, we modify a print statement accordingly to the type. Notice that `%T` in the print statement gets the name of the value type.

## Example 4.12: Explore the type of an empty interface.

```
1 package main
3 import "fmt"
5 func main() {
7 aux := []interface{}(42, "hello", true)
9 for i, v := range aux {
11 switch t := v.(type) {
13 default:
14 fmt.Printf("%T -> %s\n", t, i)
16 case int:
17 fmt.Printf("%T -> %d\n", t, i)
19 case string:
20 fmt.Printf("%T -> %s\n", t, i)
22 }
24 }
```

> Go cannot be fully considered an object-oriented language. Actually, concepts such as classes or hierarchy of classes do not exist. Similar functionality can indeed be obtained using the current language definition. However, we cannot say Go is an object-oriented language.

## 4.4 SUMMARY

This Chapter introduces the concepts of struct, methods, and interfaces used in Go. These concepts are fundamental pieces of the Go language and will appear across different sections of this book. Additionally, we explained certain situations that may seem weird to early adopters such as the difference between value and pointer receivers in methods.

## CHAPTER 5
 REFLECTION

In programming, reflection is the ability of a program to examine, modify its structure and behavior [11]. In other words, this is a form of metaprogramming. Reflection is an extremely powerful tool for developers and extends the horizon of any programming language. Unfortunately, this comes with additional complexity.

In this Chapter, we introduce the reflect package and explain examples how to explore, introspect and modify our code in run-time. We split this explanation into two sections, according to how Go organizes the reflection package. Finally, we introduce how Go uses tags to enhance fields information.

## 5.1 REFLECT.TYPE

A starting point to understand reflection in Go, is to remember the concept of empty interface interface{} seen in 4.3.1. The empty interface can contain whatever type. For example:

```
unknown := interface{}(
a := 16
unknown = a
```

This code works because interface{} accepts everything, there we can say everything is an empty interface. This is very important because the function reflect.TypeOf is the main entrypoint for code introspection and receives empty interface as argument. Observe Example 5.1 and how it obtains the type of variables a and b.

**Example 5.1:** reflect.TypeOf with basic types.

```
package main

import (
	"fmt"
	"reflect"
)

func main() {
	var a int32 = 42
	var b string = "Forty two"

	typeA := reflect.TypeOf(a)
	fmt.Println(typeA)

	typeB := reflect.TypeOf(b)
	fmt.Println(typeB)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_57_0.png)

The function TypeOf returns type Type with a set of methods to for code introspection.

Example 5.2 explores a struct with two fields. Notice that we can navigate through fields of any type, accessing its name and type.

## Example 5.2: reflect.TypeOf with structs.

```
package main

import (
	"fmt"
	"reflect"
)

type T struct {
	A int32
	B string
}

func main() {
	t := T(42, "forty two")

	type := reflect.TypeOf(t)
	fmt.Println(type)

	for i := 0; i < type.NumField(); i++ {
		field := type.Field(i)
		fmt.Println(field.Name, field.Type)
	}
}
```

Beyond type exploration, we can check if a type implements an interface. This can be done using Implements method as shown in Example 5.3. This is a good example of interfaces work in Go. The method Add has a pointer receiver (*Calculator) for that reason, the main Calculator type does not implement the interface.

## Example 5.3: reflect.TypeOf with structs.

```
package main

import (
	"fmt"
	"reflect"
)

type Adder interface {
	Add(int, int) int
}

type Calculator struct {
}

func (c *Calculator) Add(a int, b int) int {
	return a + b
}

func main() {
	var ptrAdder Adder
	adderType := reflect.TypeOf(ptrAdder).Elem()

	c := Calculator{}
	calcType := reflect.TypeOf(c)
	calcTypePtr := reflect.TypeOf(&c)

	fmt.Println(calcType, calcType.Implements(adderType))
	fmt.Println(calcTypePtr, calcTypePtr.Implements(adderType))
}
```

Using reflect we can explore any kind of struct, with any number of fields and types. Example 5.4 uses a recursive inspector that prints the structure of any given type. The inspector through the struct fields if they are other structs. This is done by obtaining the Kind of field and comparing it with struct (f.Type.Kind() == reflect.Struct). You can check how this code skips exported fields.

## Example 5.4: Recursive struct inspector.

```
package main

import (
	"fmt"
	"reflect"
	"strings"
)

type T struct {
	B int
	C string
}

type S struct {
	C string
	D T
	E map[string]int
}

func printerReflect(offset int, t reflect.Type) {
	indent := strings.Repeat("", offset)
	if t.Kind() == reflect.Struct {
		for i := 0; i < t.NumField(); i++ {
			innerIndent := strings.Repeat("", offset+4)
			field := t.Field(i)
			fmt.Printf("%s%s: %s\n", indent, field.Name, field.Type)
			if field.Type.Kind() == reflect.Struct {
				printerReflect(offset+4, field.Type)
			} else {
				fmt.Printf("%s%s: %s\n", innerIndent, field.Name, field.Type)
			}
		}
	}
	fmt.Printf("%s\n", indent)
}

func main() {
	x := S("root", T{42, "forty two"}, make(map[string]int))
	printerReflect(&x, reflect.TypeOf(x))
}
```

## 5.2 REFLECT.VALUE

We have seen how reflect.Type permits code introspection. However, the reflect.Type type cannot access fields. This functionality is reserved to to the reflect.Value type. Actually, from a reflect.Value type we can access its reflect.Type type. Example 5.5 uses the same variables in Example 5.1. Notice that in this case we can print the current value.

Example 5.5: reflect.ValueOf().

```
1 package main
import (
	"fmt"
	"reflect"
)

func main() {
	var a int32 = 42
	var b string = "forty two"

	valueOFA := reflect.ValueOf(a)
	fmt.Println(valueOFA.Interface())

	valueOBB := reflect.ValueOf(b)
	fmt.Println(valueOBB.Interface())
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_60_0.png)

In order to know what type implements a value, we can compare it with the Kind type returned by method Kind(). The type Kind is a number representing one of the types available in Go (int32, string, map, etc.). This can be combined with a switch statement as shown in Example 5.6.

## Example 5.6: switch using reflect.Kind.

```
package main

import (
	"fmt"
	"reflect"
)

func ValuePrint(i interface{}) {
	v := reflect.ValueOf(i)
	switch v.Kind() {
	case reflect.Int32:
		fmt.Printf("Int32 with value %v\n", v.Int32())
	case reflect.String:
		fmt.Printf("String with value, %v\n", v.String())
	default:
		fmt.Printf("unknown type\n")
	}
}

func main() {
	var int32 = 42
	var string = "forty two"
	ValuePrint(int32)
	ValuePrint(string)
}
```

5.7 uses reflect.Value with a struct to print the field values. The reflected value of variable is correctly printed. We can print the value of every field in the struct. Notice the difference between printing field.String() and field. For numeric values field.String() returns a string like <int32>. The string informs that there is an integer value in that field. However, fmt.Printf(field) works as expected. This occurs because the function prints the corresponding value when it receives Value types.

## Example 5.7: reflect.ValueOf with structs.

```
package main

import (
	"fmt"
	"reflect"
)

type T struct {
	A int32
	B string
}

func main() {
	t := T(42, "forty two")

	type := reflect.TypeOf(t)
	fmt.Println(type)

	for i := 0; i < type.NumField(); i++ {
		field := type.Field(i)
		fmt.Println(field.Name, field.Type)
	}
}
```

| struct (42 two 3.14) |
| int32 <int32 Value> 42 |
| string forty forty two |
| float32 <float32 Value> 3.14 |
