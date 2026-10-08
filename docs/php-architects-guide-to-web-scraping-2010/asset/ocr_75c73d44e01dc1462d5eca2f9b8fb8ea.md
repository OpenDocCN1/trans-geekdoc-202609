since the client essentially has to wait for two requests to complete for every one request that would normally be made to the target application.

The batch approach is based on synchronization. For read operations, data is updated on a regular interval. For write operations, changes are stored locally and then pushed out in batches (hence the name) to the target application, also on a regular interval. The pros and cons to this approach are the complement of those from the real-time approach: updates will not be real-time, but the web scraping application's response time will not be increased. It is of course possible to use a batch approach with a relatively low interval in order to approximate real-time while gaining the benefits of the batch approach.

The selection of an approach depends on the requirements of the web scraping application. In general, if real-time updates on either the web scraping application or target application are not required, the batch approach is preferred to maintain a high level of performance.

# # Availability

Regardless of whether a web scraping application takes a real-time or batch approach, it should treat the remote service as as potential point of failure and account for cases where it does not return a response. Once a tested web scraping application goes into production, common causes for this are either service downtime or modification. Symptoms of these include connection timeouts and responses with a status code above the 2xx range.

An advantage of the batch approach in this situation is that the web scraping application's front-facing interface can remain unaffected. Cached data can be used or updates can be stored locally and synchronization can be initiated once the service becomes available again or the web scraping application has been fixed to account for changes in the remote service.

# ## Parallel Processing

Two of the HTTP client libraries previously covered, cURL and pecl_http, support running requests in parallel using a single connection. While the same feature can-