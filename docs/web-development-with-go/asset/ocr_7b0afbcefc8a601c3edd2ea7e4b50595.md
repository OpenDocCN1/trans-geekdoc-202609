# 2.2. DEMYSTIFYING OUR APP

```
package main
```

If you have written any code in Go, this should be pretty obvious. This simply declares what package this code is a part of. In our case, we are declaring it as part of the main package because we intend to have our application start by running the main () function in this file.

Next up are the imports:

```
import (
  "fmt"
  "net/http"
)
```

used to tell the compiler which packages you intend to use in your code. As we expand on our application we will start to create our own packages so that we can test and reuse code more easily, but for now we are just using two packages from Go’s standard library.

The first is the fmt package. Putting simply, this is the package used to format strings and write them to different places. For example, you could use the fmt.Println(...) function to print "Hello, World!” to the terminal. We will cover how we use this in our code shortly.

The last package we import is net/http. This package is used to create an application capable of responding to web requests, as well as making web requests to other servers. We end using this library quite a bit in our simple server, and it will continue to be the foundation that our web application is built on top of.

> Box 2.2. What are standard libraries?