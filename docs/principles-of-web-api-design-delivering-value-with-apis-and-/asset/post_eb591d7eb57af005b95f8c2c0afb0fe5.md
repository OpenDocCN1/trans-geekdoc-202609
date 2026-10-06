
Dependent resources are nested under the parent, requiring the parent identifier in the path to interact with the dependent resources.

# A Warning about Dependent Resources

It is common to see a considerable number of dependent resources when APIs are designed from the bottom up from a relational database or by using a relational style to resource design.
Nesting dependent resources is for constraining the navigability of children to the scope of the parent. While it may be tempting to create dependent resources, keep in mind that each nested level requires the API consumer to include the parent identifier in the path. For example:

```
GET /users/{userId}/projects/{projectId}/tasks/{taskId}
```

For an API consumer to retrieve a task by a given identifier, it also needs to have the parent project and user identifiers. This places additional work on the client to track these parent identifiers.
Nesting dependent resources is a useful design option but should be used only when it improves the usability of the API.

The results are shown in Figure 7.4. Notice that the resource collections are plural names. While required, this convention is commonly found with REST APIs.
Migrate the list of operations, including their descriptions and request/response details, into a new tabular format designed to capture the high-level design. This is shown in Figure 7.5.

| Resource Path |
| :--- |
| /books |
| /carts |
| /carts/(cartId)/items |
| /authors |

**Figure 7.4** Convert each resource name into a URL-friendly name with dependent resources nested under the parent.

# CHAPTER 7 REST-BASED API DESIGN

| Resource Path | Operation Name | HTTP Method | Description | Request | Response |
|---|---||---|---|---|---|
| /books | listBooks() | GET | List books by category or release date | categoryId/releaseDate | Book[] |
| /books/search | searchBooks() | GET | Search for books by author, or title. | searchQuery | Book[] |
| /books/{bookId} | viewBook() | GET | View book details | bookId | Book |
| /carts/{cartId} | viewCart() | GET | View the current cart and total | cartId | Cart |
| /carts/{cartId} | clearCart() | DELETE | Remove all books from the customer's cart | cartId | Cart |
| /carts/{cartId}/items | addItemToCart(itemId) | POST | Add a book to the customer's cart | cartId, itemId | Cart |
| /carts/{cartId}/items | removeItemFromCart(itemId) | DELETE | Remove a book from the customer's cart | cartId, itemId | Cart |
| /authors/{authorId} | getAuthorDetails() | GET | Retrieve the details of an author | authorId | Author tabular format |

Figure 7.5 Migrate the API profile's list of operations, descriptions, and request into a new design-centric format.

# Step 2: Map API Operations to HTTP Methods

The next step is to determine which HTTP method is appropriate for each operation. Table 6.1 outlined three safety classifications that each HTTP method may be assigned: safe, idempotent. Table 7.1 outlines the safety classifications for common HTTP methods based on their intended use.

During modeling, common verbs were likely identified in the operation name and/or description of the API profile. These verbs often provide clauses to the HTTP method that best matches the operation. By combining the safety classification of HTTP methods, as outlined in Table 7.1, with the operation mappings listed in Table 7.2, the appropriate HTTP method can be selected.

Using Table 7.2 as a reference, along with the list of resource paths created previously in step 1, assign the appropriate path and HTTP method to each operation based on the intended use. If the operation is interacting with a specific resource instance, include the resource identifier in the path. The results are shown in Figure 7.6.

| HTTP Method | Method Description | Safety Classification | Safety Description |
|---|---||---|---|
| GET | Returns requested data | Safe | No state changes are made |
| POST | Used in a variety of scenarios, from calculations to creating new resources | Unsafe | Cannot guarantee the same results for multiple calls with the same input |
| PUT | Representation from client to replace resource | Idempotent | Guarantees the same results for multiple calls with the same input as is providing to the entire resource representation |
| PATCH | Performs a partial update of a resource | Unsafe | Cannot guarantee the same results for multiple calls with the same input, as only the client provides representation of the resource |
| DELETE | Deleted a resource from the server | Idempotent | Multiple calls to delete the same resource will still result in the resource being deleted (even if it doesn't exist) |

# CHAPTER 7 REST-BASED API DESIGN

| Table 7.2 Mapping Common Verbs Found in Operation Names/Descriptions to HTTP |
| Operation Verb | Typical HTTP Method + Resource with Examples |
|---|---|
| List, Search, Match, View All | GET resource collection <br> GET /books |
| Show, Retrieve, View | GET resource instance <br> GET /books/12345 |
| Create, Add | POST resource collection <br> POST /books |
| Replace | PUT resource instance or collection <br> PUT /carts/123 <br> PUT /carts/123/items |
| Update | PATCH resource instance <br> PATCH /carts/123 |
| Delete, Remove All, Clear, Reset | DELETE resource instance <br> DELETE /carts/123/items |
| Delete | DELETE resource instance <br> DELETE /carts/123/items/456 |
| Search, Secure Search | POST custom search action on the resource collection <br> POST /carts/search |
| <other verbs> | POST as a custom action on a resource collection or instance |

# Step 3: Map API Operations to HTTP Methods

The next step is to determine which HTTP method is appropriate for each operation. Table 6.1 outlined three safety classifications that each HTTP method may be assigned: safe, idempotent. Table 7.1 outlines the safety classifications for common HTTP methods based on their intended use.

During modeling, common verbs were likely identified in the operation name and/or description of the API profile. These verbs often provide clauses to the HTTP method that best matches the operation. By combining the safety classification of HTTP methods, as outlined in Table 7.1, with the operation mappings listed in Table 7.2, the appropriate HTTP method can be selected.

Using Table 7.2 as a reference, along with the list of resource paths created previously in step 1, assign the appropriate path and HTTP method to each operation based on the intended use. If the operation is interacting with a specific resource instance, include the resource identifier in the path. The results are shown in Figure 7.6.

# Step 3: Assign Response Codes

The API design is starting. The next step is to assign response codes for each operation. These belong to three primary families:
- 2xx: Success
- 4xx: Client error
- 5xx: Server error

API clients should be prepared for any kind of response, but it is not necessary to capture every possible code. Start by identifying at least one success response code for each operation, with any error codes that the API may explicitly return. While the list of errors may not be comprehensive, start by identifying the typical error codes that may be returned. Figure 7.7 shows the possible success and error codes for the Shopping API.

| Resource Path | Operation Name | HTTP Method | Description | Request | Response |
|---|---|---|---|---|---|
| /books | listBooks() | GET | List books by category or release date | categoryId/releaseDate | Book[] |
| /books/search | searchBooks() | GET | Search for books by author, or title. | searchQuery | Book[] |
| /books/{bookId} | viewBook() | GET | View book details | bookId | Book |
| /carts/{cartId} | viewCart() | GET | View the current cart and total | cartId | Cart |
| /carts/{cartId} | clearCart() | DELETE | Remove all books from the customer's cart | cartId | Cart |
| /carts/{cartId}/items | addItemToCart(itemId) | POST | Add a book to the customer's cart | cartId, itemId | Cart |
| /carts/{cartId}/items | removeItemFromCart(itemId) | DELETE | Remove a book from the customer's cart | cartId, itemId | Cart |
| /authors/{authorId} | getAuthorDetails() | GET | Retrieve the details of an author | authorId | Author tabular format |

Figure 7.6 Using the list of paths identified, assign the appropriate path and HTTP method to each operation based on the intended usage.

# Don't Invent Your Codes

Over the years, some strange decisions have been made by API designers. One is the decision to use UNIX-style codes, where 0 indicates success and 1 through 127 indicate an error. Please do not invent your own. HTTP is designed to be layered, which means that middleware servers might be involved between the client and server. Creating your own codes will only cause problems with these intermediary layers.

While the list of response codes is quite large, there are several that are commonly used in API design. These are detailed in Table 7.3.

# Step 4: Documenting the REST Design

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
