Likewise, a response from a server is also broken into two parts - headers and a body. The response doesn't need a URL because it is simply responding to your request. Similar to requests, the headers are used to store mostly metadata that is useful to the browser, and the body contains the data that was requested.

First up is `w http.ResponseWriter`. This is a structure that allows us to modify the response that we want to send to whoever visited our website. By default `w` implements the `Write()` method that allows us to write to the response, hence the name `ResponseWriter`, but it also has methods that help us set headers when we need to.

Next is `r *http.Request`. This is a structure used to access data from the web request. For example, we might use this to get the users email address and password after they sign up for our web application.

# Box 2.4. What are pointers?

Pointers are exactly what they sound like - a data type that doesn't actually contain the data itself, but instead points to a memory address in a computer where the data is stored.

Pointers are used for many different reasons, but the primary thing to remember is when you pass a pointer to a function it can alter the data you provided. This means that when we alter the request object we received, the changes will still be present after our code is done running.

If you are unfamiliar with pointers, you should probably take a moment to familiarize yourself with them before proceeding beyond this chapter, as they are a pretty important component of programming in Go.