# 9.4. A Brief Survey of the Go Standard Library

# 9.4.8. Networking Packages

The Go standard library has many packages that support networking and programming. The net package provides functions and types for communicating over Unix domain and network sockets, TCP/IP, and UDP. The package provides functions for domain name resolution.

The net/http package uses many of the net package and provides for parsing HTTP requests and replies, and provides a basic HTTP client. The net/http package also includes an easy-to-extend HTTP server, as we saw in Chapter 2($24.4, 72 ➤) and Chapter 3's exercises. The net/url package provides URL parsing and query escaping.

Some other high-level networking packages are included in the standard library. One is the net/rpc (Remote Procedure Call) which allows a server to provide objects whose exported methods can be called by clients. Another is the net/smtp (Simple Mail Transport Protocol) package which can be used to send email.

# 9.4.9. The Reflect Package

The reflect package provides runtime reflection (also introspection), that is the ability to access and interact with values of arbitrary types at runtime.

The package also provides some utility functions such as reflect.DeepEqual() which can compare any two values—for example, slices, which aren't comparable using the == and != operators.

Every value in Go has two attributes: its actual value and its type. The reflect.Typeof() function can tell us the type of any value.

```
x := 8.6
y := float32(2.5)
fmt.Printf("var x %v = %v\n", reflect.TypeOf(x), x)
fmt.Printf("var y %v = %v\n", reflect.TypeOf(y), y)
```

```
var x float64 = 8.6
var y float32 = 2.5
```

Here we have output two floating-point variables and their types as Go declarations using reflection.

When the reflect.Valueof() function is called on a value it returns a reflect.Value which holds the value but uses not the value itself. If we want to access the value held we must use one of the reflect.Value methods.

```
word := "Chameleon"
value := reflect.Valueof(word)
```