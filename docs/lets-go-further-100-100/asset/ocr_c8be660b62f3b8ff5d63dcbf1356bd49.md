# Authenticating Requests

Now that our clients have a way to exchange their credentials for an authentication token, let’s look at how we can use that token to *authenticate them*, so we know exactly which user a request is coming from.

Essentially, once a client has an authentication token we will expect them to include it with all subsequent requests in an `Authorization` header, like so:

```
Authorization: Bearer IEYZQUBEMPPAKPOAWTPV6YJ6RM
```

When we receive these requests, we’ll use a new `authenticate()` middleware method to execute the following logic:

+   - If the authentication token is not valid, then we will send the client a `401 Unauthorized` response and an error message to let them know that their token is malformed or invalid.
+   - If the authentication token is valid, we will look up the user details and add their details to the *request context*.
+   - If no `Authorization` header was provided at all, then we will add the details for an *anonymous user* to the request context instead.