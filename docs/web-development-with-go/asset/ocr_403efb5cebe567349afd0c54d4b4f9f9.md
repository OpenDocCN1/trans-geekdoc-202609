# 13.8. RECOVERING FROM VIEW RENDERING ERRORS

2. Execute the entire template into a temporary buffer, then copy it to the ResponseWriter we know it has executed correctly.

The first option uses less memory and can be faster when shaving every little millisecond matters, but for most web applications this isn’t important. People can’t really perceive a few milliseconds of delay, and the memory footprint is relatively minor.

We will be going with the second option because it won’t slow down our application noticeably, and it provides a much better user experience. Rather than ending up with a half-rendered page users will get a clear error page, and we will also have a chance to set the proper status code.

We will be working inside the views package to implement these changes.

```
$ atom views/view.go
```

The first thing we are going to change is the Render method’s return type. We currently have it returning an error whenever we run into one executing our templates, leaving the error handling up to whoever called the Render method. Moving forward we are going to handle those errors inside the Render method, so we do not have to return an error.

> Note: If you want to continue returning errors so you can track when errors occur you can, but we won’t be doing that in this course.

```
func (v *View) Render(w http.ResponseWriter, data interface{}) {
  // .. . we will edit the internals of this method shortly
}
```

After we need to skip down to the return statement where we execute our template. We are going to start off by creating a Buffer², a type that comes from the bytes package.

¹²https://golang.org/pkg/bytes/#Buffer