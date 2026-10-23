# Authentication

In this section of the book we’re going to look at how to *authenticate* requests to our API, so that we know exactly which user a particular request is coming from.

> **Remember:** *Authentication* is about confirming *who a user is*, whereas *authorization* is about checking whether that user is permitted to do something.

We will:

+   - Lay out the possible approaches to API authentication that we could use, and talk through their relative pro and cons.
+   - Implement a stateful token-based authentication pattern, which allows clients to exchange their user credentials for a time-limited authentication token identifying who they are.