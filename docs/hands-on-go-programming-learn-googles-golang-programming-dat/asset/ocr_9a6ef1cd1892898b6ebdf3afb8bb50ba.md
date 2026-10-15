# 8.3.3 Method on the function type

We can define methods on function type also. This feature is used a lot in One good example of stdlib is net/http package. This package has a function type as shown below:

```
type HandlerFunc *Request)
```

The HandleFunc method type has a method ServeHTTP as below:

```
func (f HandlerFunc) ServeHTTP(w ResponseWriter, r *Request)
```

The method on the function is very useful when we need to provide similar functionality with multiple scenarios. The following code does the same thing. This code has a Filter method on the By function type. The Filter method filters the user’s slice by age, most liked, most visited, and most followed.

# Program 8.11

```
package main

import "fmt"

type User struct {
id int
```