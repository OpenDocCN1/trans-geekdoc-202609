# Don't Invent Your Response Codes

Over the years, some strange decisions have been made by API designers. One is the decision to use UNIX-style codes, where 0 indicates success and 1 through 127 indicate an error, for HTTP response code. Please do not invent your own response codes. HTTP is designed to be layered, which means that middleware servers you might be involved between the client and server. Creating your own codes will only cause problems with these intermediary layers.

While the list of HTTP response codes is quite large, there are several that are commonly used in API design. These are detailed in Table 7.3.
API clients should be prepared for any kind of response code, but it is not necessary to capture every possible response code. Start by identifying at least one success response code for each operation, with any error codes that the API may explicitly return. While the list of errors may not be comprehensive, start by identifying the typical error codes that may be returned. Figure 7.7 shows the possible success and error codes for the Shopping API.

# Step 4: Documenting the REST API Design

Upon the completion of step 3, the high-level API design work is finished. Using the work done so far, it is now time to capture the API design using an API description format. This will allow for sharing the API design within and across teams for feedback.

Table 7.3 Common HTTP Response Codes Used in API Design

| HTTP Response Code | Description |
|---|---|
| 200 OK | The request has succeeded. |
| 201 Created | The request has been fulfilled and resulted in a new resource being created. |
| 202 Accepted | The request has been accepted for processing, but the processing has not been completed. |
| 204 No Content | The server has fulfilled the request but does not need to return a body. This is common for delete operations. |
| 400 Bad Request | The request could not be understood by the server due to malformed syntax or invalid input. |
| 401 Unauthorized | The server requires user authentication. |
| 403 Forbidden | The server understood the request but is refusing to fulfill it. |
| 404 Not Found | The server has not found anything matching the requested URL/URI. |
| 500 Internal Server Error | The server encountered an unexpected condition which prevented it from fulfilling the request. |