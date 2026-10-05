

## 5.5. Defer、Panic 和 Recover

...被点击以出于测试目的触发 panic。最重要的修改是，我们已经让服务器能够在发生 panic 后存活。为了帮助我们观察发生了什么，我们还在客户端被成功服务、我们收到错误请求以及服务器被重启时记录了日志。这里是一个典型日志的微型示例。

```
[127.0.0.1:41373] served OK
[127.0.0.1:41373] served OK
[127.0.0.1:41373] bad request: 'gy' is invalid
[127.0.0.1:41373] served OK
[127.0.0.1:41373] caught panic: user clicked panic button!
[127.0.0.1:41373] served OK
```

我们告诉 log 包不要使用时间戳仅仅是为了让输出在书中看起来更美观。

在查看我们所做的更改之前，我们将简要回顾一下原始代码。

```gofunc main() {
	http.HandleFunc("/", homePage)
	if err := http.ListenAndServeAndServe(":9001", nil); err != nil {
		log.Fatal("failed to start server", err)
	}
}

func homePage(writer http.ResponseWriter, request *http.Request) {
	// ...
}
```

这个网站只有一个页面，尽管我们将要介绍的技术可以很容易应用到多个页面。如果发生了没有被 recover() 捕获的 panic，也就是说如果 panic 到达了 main() 函数，服务器将会终止；这正是我们必须防止的。

```go
func homePage(writer http.ResponseWriter, request *http.Request) {
	defer func() {
		if x := recover(); x != nil {
			log.Printf("%s caught panic: %v", request.RemoteAddr, x)
		}
	}()
	// ...
}
```

为了让 Web 服务器在面对 panic 时具有健壮性，我们必须确保每个页面处理器都有一有一个调用 recover() 的延迟函数。这将阻止任何 panic 的传播（因为 defer 语句在函数返回之前执行）。当然，对于一个拥有许多处理器的大型网站，添加一个用于捕获和记录 panic 的延迟函数涉及大量的重复，并且很容易忘记。这可以通过一个包含每个页面处理器所需的代码的包装函数来解决。只要我们更改了 http.HandleFunc() 的调用，我们就可以从页面处理器中省略 recover 代码：

```go
http.HandleFunc("/", logPanics(homePage))

func logPanics(function func(http.ResponseWriter, request *http.Request)) func(http.ResponseWriter, request *http.Request) {
	return func(writer http.ResponseWriter, request *http.Request) {
		defer func() {
			if x := recover(); x != nil {
				log.Printf("%s caught panic: %v", request.RemoteAddr, x)
			}
		}()
		function(writer, request)
	}
}
```

## 5.6. 自函数

函数是过程化编程的基石，Go 为它们提供了一类支持。Go 方法（第 6 章介绍）与 Go 函数非常相似，因此本节对于过程化和面向对象的编程都相关。以下是函数定义的基础语法：

```go
func name(optionalParameters) optionalReturnType {}
func name(optionalParameters) (optionalReturnValues) {}
```

函数可以接受零个或多个参数。如果没有参数，括号留空。如果有一个或多个参数，则写成 `params1 type, ..., paramsN type`，其中 params1 是单个参数名，或者是给定类型的两个或多个参数名的逗号分隔列表。参数必须按顺序传递：没有等同于 Python 命名参数的内容，尽管正如我们稍后看到的，可以实现类似的效果。

最后一个参数的类型之前可以跟一个省略号 (...)。此类函数被称为变长函数（variadic functions）；这意味着函数将接受零个或多个该类型的值作为该参数的值，在函数内部该参数的类型将是 `[]type`。

函数可以返回零个或多个值。如果没有值，可以写成 `type`。如果有两个或多个返回值，则必须使用括号，并写成 `(type1, ..., typeN)`。如果有一个或多个命名返回值，则必须使用括号，并写成 `(values1 type1, ..., valuesN typeN)`，其中 values1 是单个返回名，或者是给定类型的两个或多个返回名的逗号分隔列表。函数的返回值可以是全部无命名的，也可以是全部命名的，但不能混用。

具有一个或多个返回值的函数必须至少有一个 return 语句——或者一个 panic() 调用作为它们的最后语句。如果返回值是没有命名的，return 语句指定的数值必须与返回值数量相同，每个值的类型必须与对应的返回值匹配。如果返回值是有命名的，return 语句既可以像无命名情况那样指定值，也可以直接裸写（即不提供显式的返回值）。请注意，虽然裸返回（bare returns）是合法的，但它们被认为是糟糕的——书中没有任何示例会使用它们。

如果一个函数有一个或多个返回值，它的最后一个可执行语句必须是 return 或 panic()。Go 编译器足够智能，能够意识到以 panic 结尾的函数不会正常返回，因此在该处不需要 return 语句。遗憾的是，目前的 Go 编译器并不理解一个带有无条件 else 语句的 if 语句以 return 语句结尾，或者一个 switch 语句具有一个以 return 语句结尾的 default case，因此在之后不再需要额外的 return。在这些情况下，常见的做法是不以 else 或 default case 结尾，而是将 return 语句放在 if 或 switch 之后，或者干脆...

