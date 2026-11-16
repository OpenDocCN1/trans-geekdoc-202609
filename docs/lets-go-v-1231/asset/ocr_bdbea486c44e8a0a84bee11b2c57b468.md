path only. But there is one special case.

If a route pattern ends with a wildcard, and this final wildcard identifier ends in ..., then the wildcard will match any and all remaining segments of a request path.

For example, if you declare a route pattern like "/post/{path...}" it will match requests like /post/a, /post/a/b, /post/a/b/c and so on — very much like a subtree path pattern does. But the difference is that you can access the entire wildcard part via the r.PathValue() method in your handlers. In this example, you could get the wildcard value for {path...} by calling r.PathValue("path").