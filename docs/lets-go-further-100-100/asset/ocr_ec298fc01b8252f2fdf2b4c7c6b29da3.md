On one hand this is a positive thing — if there is no client left to return a response to, we may as well cancel the SQL query and free-up resources.

On the other hand, we will receive the same error message in two very different scenarios:

+   - When a database query takes too long to complete, in which case we would want to log it as an error.
+   - When a client closes the connection — which can happen for many innocuous reasons, such as a user closing a browser tab or terminating a process. It’s not *really* an error from our application’s point of view, and we would probably want to either ignore it or perhaps log it as a warning.

Fortunately, it *is* possible to tell these two scenarios apart by calling the `ctx.Err()` method on the context. If the context was canceled (due to a client closing the connection), then `ctx.Err()` will return the error `context.Canceled`. If the timeout was reached, then it will return `context.DeadlineExceeded` instead. If both the deadline is reached and the context is canceled, then `ctx.Err()` will surface whichever happened first.

It’s also important to be aware that you may receive a `context.Canceled` error if the client closes the connection while the query is queued by `sql.DB`, and likewise `Scan()` may return a `context.Canceled` error too.

Putting all that together, a sensible way to manage this is to check for the error `pq: canceling statement due to user request` in our