# # End-to-end testing

In the last chapter we talked through the general pattern for how to unit test your HTTP handlers in isolation.

But — most of the time — your HTTP handlers aren’t *actually used* in isolation. So in this chapter we’re going to explain how to run end-to-end tests on your web application that encompass your routing, middleware and handlers. In most cases, end-to-end testing should give you more confidence that your application is working correctly than unit testing in isolation.

To illustrate this, we’ll adapt our `TestPing` function so that it runs an end-to-end test on our code. Specifically, we want the test to ensure that a `GET /ping` request to our application calls the `ping` handler function and results in a 200 OK status code and "OK" response body.

Essentially, we want to test that our application has a route like this:

| Route pattern | Handler | Action |
| --- | --- | --- |
| ... | ... | ... |
| GET /ping | ping | Return a 200 OK response |

# ## Using httptest.Server

The key to end-to-end testing our application is the `httptest.NewTLSServer()` function, which spins up a `httptest.Server` instance that we can make HTTPS requests to.

The whole pattern is a bit too complicated to explain upfront, so it’s probably best to demonstrate first by writing the code and then we’ll talk through the details afterwards.

With that in mind, head back to your `handlers_test.go` file and update the `TestPing` test so that it looks like this: