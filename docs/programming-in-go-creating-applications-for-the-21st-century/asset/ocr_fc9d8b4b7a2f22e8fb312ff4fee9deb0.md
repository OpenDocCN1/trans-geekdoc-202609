# 216

# Chapter 5. Procedural Programming

package and errors. Another use is to recover() to ensure that the panics don't leak out and are
reported as errors. Another use case is to put calls like panic("unreachable")
in places where our logic cannot be reached (e.g., at the end of a function
which always returns by using return statements before reaching the ending), or
calling panic() if a pre- or post-condition is broken. This ensures that if
we break the logic of such functions we will soon know about it.

None of the above reasons apply then we ought to dego panicking and return
a non-error when problems occur. So, in this example, we want to return an int
and nil if a conversion succeeds and an error if a conversion fails.
Here is a wrapper function that achieves what we want:

```
func IntToInt64(x int64) (i int, err error) {
	defer func() {
		if e := recover(); e != nil {
		terr = fmt.Errorf("%v", e)
		}
	ni = Convert64ToInt(x)
	return i, nil
}
```

When this function is called, as usual, Go automatically sets the return values
to the zero values for their types, in this case nil and nil. If we call the custom
Convert64ToInt() function returns normally, we assign its result to the i
return value, and return along with nil to signify that no error occurred.
tif the Convert64ToInt() panics, we catch the panic in the deferred
anonymous function and set err to be an error with its text set to set to the textual
representation of the panic it caught.

As the IntToInt64() function shows, it is straightforward to convert panics
to errors.

For our second example we will consider how to make a web server robust
to the face of panic. Back in Chapter 2 we reviewed the statistics example
($2.4, 72). If we make a programming error in that server—example, if we
accidentally passed nil as an image.Image value and call a method on it—we
get a panic without a call to recover() would terminate the program.
This is, of course, a very unsatisfactory situation if the web site is important to
, especially if we want to run it unattended for some of the time. We want
is for the server to continue running and to log any panic
so that we can track them down and fix them at our leisure.

We have created a modified version of the statistics example (in fact, of the
st_ans solution), in file statistics_nonstop/statistics.go. One modifica-
tion we have made is to add an extra button to the web page, Panic!, that can