# 13.7. HANDLING LOGIN ERRORS

> One worth noting with our PublicError interface is that our modelError type inside the models package never directly sees or interacts with the type. It is possible to implement an interface in Go without ever importing or using the interface directly. This is a very big difference from other languages like Java where you have to explicitly state “this class implements interface X”, but it is also a very powerful feature of Go.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/13.6

Changes - book.usegolang.com/13.6-diff

# 13.7 Handling login errors

Next on our agenda is to address how we are handling errors that occur when logging users via via the Login action inside our users controller. Open your users controller source file and find the Login method.

```
$ atom controllers/users.go
```

The first error we need to address is one we saw in the Create method; whenever we fail to parse a form we need to render the login form again along with an alert explaining that something went wrong.