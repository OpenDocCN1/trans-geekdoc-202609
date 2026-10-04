# 9.3.1 CookieJar

The previous example is a basic description of how to manipulate cookies. One drawback of the example is that we have to manually set the new cookie for future requests. This could be easily done considering that we only have one cookie. However, when interacting with web applications it is common to use many and it would be more efficient to have a non-supervised approach to update these cookies.

The 21 package net/http/cookiejar implements an in-memory storage solution for cookies that follow the cookiejar interface from net/http. Example 9.8 extends Example 9.7 with a client using a CookieJar. The SetCookies method associate an array of cookies with a URL. Now every time the client uses CookieJar, the CookieJar will update the corresponding cookies. This enhancement is only required at the client side. Finally, we iteratively send requests to the server which without the CookieJar we would have to manually update the cookie for the next request.

This can be done adding the cookies to the CookieJar (jar.SetCookies) and setting the jar field in the http.client. After every request cookies are automatically updated and we can check their values.

# Example 9.8: Use of CookieJar to set cookie values.

```
package main

import (
	"fmt"
	"net/http"
	"net/http/cookiejar"
	"url"
	"strconv"
)

func setCookie(w http.ResponseWriter, r *http.Request) {
	counter, err := r.Cookie("counter")
	if err != nil {
		w.WriteHeader(http.StatusInternalServerError)
		return
	}

	value, err := strconv.Atoi(counter.Value)
	if err != nil {
		w.WriteHeader(http.StatusInternalServerError)
		return
	}

	value = value + 1
	newCookie := http.Cookie{
		Name: "counter",
		Value: strconv.Itoa(value),
	}
	http.SetCookie(w, &newCookie)
```