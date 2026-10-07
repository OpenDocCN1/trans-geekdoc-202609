```
http.Handle("/", middleware1(middleware2(finalHandler)))
http.ListenAndServe(":8999", nil)
}
```

Look at the main() function. Here, we are intercepting requests to our root web directory with the middleware1 handler. This handler accepts a parameter another handler called middleware2. In that turn the final handler serves as a parameter.

When someone visits our application, it will call middleware1, which displays a message, and when it hits next.serveHTTP, executes the code in middleware2. The middleware2 handler in turn calls final(), which executes and then returns control to middleware2, which completes its tasks and returns control to middleware1.

The output will look like Figure 8.

![](bbox=[0.161, 0.3675, 0.818, 0.47875])

Figure 8: The Output of the Middleware Example

Figure 8 offers a completely artificial example, but it serves to illustrate how much control middleware can give you.

Go often uses middleware internally. For example, many functions in the net/http package, as is StripPrefix, are textbook examples of what middleware is—they wrap your handler and perform additional operations on requests or responses.

The concept of middleware can be somewhat difficult to understand, so Code Listing 5 shows another example.

Code Listing 5: Middleware Example 2

```
package main

import (
    "net/http"
)

type AfterMiddleware struct {
    handler http.Handler
}
```