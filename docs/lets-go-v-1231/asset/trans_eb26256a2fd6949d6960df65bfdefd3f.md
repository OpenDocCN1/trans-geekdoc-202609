

使得很难确保你的应用程序的所有路由声明都能在一个中心位置轻松发现。

这也意味着你的应用程序导入的任何第三方包都可以与 http.DefaultServeMux 一起注册路由。如果其中任何一个第三方包被攻破，它们可能会利用 http.DefaultServeMux 将恶意处理程序暴露到 Web 上。只需不使用 http.DefaultServeMux，就可以简单地避免这个风险。

因此，为了清晰性、可维护性和安全性，通常最好避免使用 http.DefaultServeMux 及其对应的辅助函数。相反，请使用你自己的局部作用域 servemux，就像我们迄今在这个项目中所做的那样。

## 通配符路由模式

还可以定义包含通配符段的路由模式。你可以使用这些来创建更灵活的路由规则，并通过请求 URL 向你的 Go 应用程序传递变量。如果你之前使用其他语言的框架构建过 Web 应用程序，本章中的概念可能会让你感到很熟悉。

让我们暂时放下应用程序的构建，来解释一下它的工作原理。

路由模式中的通配符段用 {} 括号内的通配符标识符表示。例如：

```
mux.HandleFunc("/products/{category}/item/{itemID}", exampleHandler)
```

在这个示例中，路由模式包含两个通配符段。第一个段的标识符是 category，第二个段的标识符是 itemID。

包含通配符段的路由模式的匹配规则与我们在上一章中看到的相同，附加规则是请求路径可以为通配符段包含任何非空值。例如，以下请求都将与我们上面定义的路由匹配：

```
/products/hammocks/item/sku123456789
/products/seasonal-plants/item/pdt-1234-wxyz
/products/experimental_foods/item/quantum%20bananas
```

重要：定义路由模式时，每个路径段（正斜杠字符之间的部分）只能包含一个通配符，并且通配符需要填满整个路径段。诸如 `"/products/c_{category}"`、`/date/{y}-{m}-{d}` 或 `/{slug}.html` 之类的模式都是无效的。

在你的处理程序中，你可以使用其标识符和 r.PathValue() 方法来检索通配符段的相应值。例如：

```
func exampleHandler(w http.ResponseWriter, r *http.Request) {
	category := r.PathValue("category")
	itemID := r.PathValue("itemID")

	...
}
```

r.PathValue() 方法始终返回一个字符串值，重要的是要记住，这可以是用户在 URL 中包含的*任何值*——因此在对该值执行任何重要操作之前，你应该对其进行验证或合理性检查。

## 在实践中使用通配符段

好的，让我们回到我们的应用程序，并将其更新为在 /snippet/view 路由中包含一个新的 {id} 通配符段，这样我们的路由看起来就像这样：

| 路由模式 | 处理程序 | 操作 |
| :--- | :--- | :--- |
| `/{$}` | home | 显示主页 |
| `/snippet/view/{id}` | snippetView | 显示特定代码片段 |
| `/snippet/create` | snippetCreate | 显示创建新代码片段的表单 |

打开你的 main.go 文件，并进行如下更改：

```
File: main.go

package main

...

func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("/{$}", home)
	mux.HandleFunc("/snippet/view/{id}", snippetView) // Add the {id} wildcard segment
	mux.HandleFunc("/snippet/create", snippetCreate)

	log.Print("starting server on :4000")

	err := http.ListenAndServe(":4000", mux)
	log.Fatal(err)
}
```

现在让我们前往 snippetView 处理程序，并将其更新为从请求 URL 路径中检索 id 值。本书稍后，我们将使用此 id 值从数据库中选择特定代码片段，但目前我们将只是将 id 作为 HTTP 响应的一部分回显给用户。

因为 `id` 值是不可信的用户输入，我们应该在使用它之前对其进行验证，以确保它是合理且明智的。就我们的应用程序而言，我们想要检查 `id` 值是否包含正整数，我们可以通过尝试使用 `strconv.Atoi()` 函数将字符串值转换为整数，然后检查该值是否大于零来完成。

具体做法如下：

```
File: main.go

package main

import (
	"fmt" // New import
	"log"
	"net/http"
	"strconv" // New import
)

...

func snippetView(w http.ResponseWriter, r *http.Request) {
	// Extract the value of the id wildcard from the request using r.PathValue()
	// and try to convert it to an integer using the strconv.Atoi() function. If
	// it can't be converted to an integer, or the value is less than 1, we
	// return a 404 page not found response.
	id, err := strconv.Atoi(r.PathValue("id"))
	if err != nil || id < 1 {
		http.NotFound(w, r)
		return
	}

	// Use the fmt.Sprintf() function to interpolate the id value with a
	// message, then write it as the HTTP response.
	msg := fmt.Sprintf("Display a specific snippet with ID %d...", id)
	w.Write([]byte(msg))
}

...
```

保存你的更改，重新启动应用程序，然后打开浏览器并尝试访问 http://localhost:4000/snippet/view/123 这样的 URL。你应该会看到包含来自请求 URL 的回显 `id` 通配符值的响应，类似于这样：

显示带有 ID 123 的特定代码片段...

你可能还想尝试访问一些 id 通配符值无效或根本没有通配符值的 URL。例如：

- http://localhost:4000/snippet/view/
- http://localhost:4000/snippet/view/-1
- http://localhost:4000/snippet/view/foo

对于所有这些请求，你都应该收到 404 页面未找到响应。

## 附加信息

## 优先级和冲突

定义包含通配符段的路由模式时，你的某些模式可能会“重叠”。例如，如果你使用 `"/post/edit"` 和 `/post/{id}` 模式定义路由，它们会重叠，因为路径为 /post/edit 的传入 HTTP 请求是两个模式的有效匹配。

当路由模式重叠时，Go 的 servemux 需要决定哪个模式优先，以便将请求分发给相应的处理程序。

这条规则非常简洁明了：*最具体的路由模式获胜*。从形式上讲，Go 定义如果一个模式仅匹配另一个模式所匹配请求的子集，则该模式比另一个模式更具体。

继续以上面的示例为例，路由模式 `"/post/edit"` *仅*匹配路径为 /post/edit 的请求，而模式 `/post/{id}` 匹配路径为 /post/edit、/post/123、/post/abc 等更多请求的请求。因此 `"/post/edit"` 是更具体的路由模式，将优先匹配。

顺便说一句，还有几件事值得一提：

- *最具体模式优先*规则的一个好副作用是，你可以以任何顺序注册模式，*这不会改变 servemux 的行为*。
- 有一种潜在的边缘情况，即你有两个重叠的路由模式，但其中任何一个都不明显比另一个更具体。例如，模式 `"/post/new/{id}"` 和 `"/post/{author}/latest"` 重叠，因为它们都匹配请求路径 /post/new/latest，但不清楚哪个应该优先。在这种情况下，Go 的 servemux 认为这些模式*冲突*，并在初始化路由时在运行时发生 panic。
- 仅仅因为 Go 的 servemux 支持重叠路由，并不意味着你应该使用它们！拥有重叠的路由模式会增加应用程序中出现错误和意外行为的风险，如果你有自由设计应用程序的 URL 结构，通常最好将重叠减少到最少或完全避免重叠。

## 带通配符的子树路径模式

重要的是要理解，即使在使用通配符段时，我们在上一章中描述的路由规则仍然适用。特别是，如果你的路由模式以尾随斜杠结尾且结尾没有 `{$}`，则它被视为*子树路径模式*，并且只需要请求 URL 路径的*开头*匹配。

所以，如果你的路由中有一个类似 `"/user/{id}/"` 的子树路径模式（注意尾随斜杠），则该模式将匹配 /user/1/、/user/2/a、/user/2/a/b/c 等请求。

同样，如果你不想要这种行为，就在末尾加上 `{$}` —— 例如 `"/user/{id}/{$}"`。

## 剩余通配符

路由模式中的通配符通常匹配请求的一个单一、非空段。

