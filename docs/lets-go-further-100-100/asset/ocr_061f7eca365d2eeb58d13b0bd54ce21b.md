+   - To help facilitate swapping databases gracefully behind a load balancer.

If you do decide to set a `ConnMaxLifetime` on your pool, it’s important to bear in mind the frequency at which connections will expire (and subsequently be recreated). For example, if you have 100 open connections in the pool and a `ConnMaxLifetime` of 1 minute, then your application can potentially kill and recreate up to 1.67 connections (on average) every second. You don’t want the frequency to be so great that it ultimately hinders performance.

# The SetConnMaxIdleTime method

The `SetConnMaxIdleTime()` method (which was introduced in Go 1.15) sets the `ConnMaxIdleTime` limit. This works in a very similar way to `ConnMaxLifetime`, except it sets the maximum length of time that a connection can be *idle* for before it is marked as expired. By default there’s no limit.

If we set `ConnMaxIdleTime` to 1 hour, for example, any connections that have sat idle in the pool for 1 hour since last being used will be marked as expired and removed by the background cleanup operation.

This setting is really useful because it means that we can set a relatively high limit on the number of idle connections in the pool, but periodically free-up resources by removing any idle connections that we know aren’t really being used anymore.