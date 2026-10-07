The cookie can hold a lot of information, but the most important fields are:

+   * Name: A key for the cookie for referring to it in your code.
* Value: The cookie's data.
* Expires: A Time value that denotes when the browser can delete it.

Other fields that might be useful for controlling access to the cookie:

+   * Path
* Domain
* HttpOnly

For now, let's keep it simple.

Here is an example of how you can set a cookie:

```
expiration := time.Now().Add(365 * 24 * time.Hour)
cookie := http.Cookie(Name: "username", Value: "jsmith", Expires: expiration)
http.SetCookie(w, &cookie)
```

> Tip: Go's time functions are sophisticated but complex. For more information, see the documentation at https://golang.org/pkg/time/

# Fetching cookies

In order to retrieve a cookie from a request, you can do the following:

```
cookie, _ := r.Cookie("username")
fmt.Fprintf(w, cookie.body.)
```

Or, if several cookies are associated with a request, you can iterate through them, as follows:

```
for _, cookie := range r.Cookies() {
fmt.Fprintf(w, cookie.Name)
}
```

# Using cookies

Let's create a simple application that uses a cookie.

The following code checks to see if this is a visitor's first visit to our site. If it is, it displays a welcome message. If not, it displays the time of the last visit.