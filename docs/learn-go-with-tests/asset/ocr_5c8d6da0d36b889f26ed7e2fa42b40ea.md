# WebSockets

+   - Convenient way of sending messages between clients and servers that does not require the client to keep polling the server. Both the client and server code we have is very simple.
+   - Trivial to test, but you have to be wary of the asynchronous nature of the tests

# Handling code in tests that can be delayed or never finish

+   - Create helper functions to retry assertions and add timeouts.
+   - We can use go routines to ensure the assertions don't block anything and then use channels to let them signal that they have finished, or not.
+   - The `time` package has some helpful functions which also send signals via channels about events in time so we can set timeouts