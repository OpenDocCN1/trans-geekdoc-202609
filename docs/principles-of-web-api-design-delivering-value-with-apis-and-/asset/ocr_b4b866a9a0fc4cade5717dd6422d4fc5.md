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
| <other verbs> | POST as a custom action on a resource collection or instance <br> POST /books/123/deactivate |

# Step 3: Assign Response Codes

The API design is starting to emerge. The next step is to assign the expected response codes for each operation. HTTP response status codes belong to three primary response code families:

+   * 200 codes indicate success, some with more clarity (e.g., 201 CREATED vs. 200 OK).
* 400 codes indicate a failure in the request that the client may wish to fix and resubmit.
* 500 codes indicate a failure on the server that is not the fault of the client. The client may attempt a retry at a future time, if appropriate.

Be sure to use the right code for the right reason. When in doubt, refer to the most current RFC that details the intended usage for the code. If a specific code isn't available within the response code family, then use the default 200, 400, or 500 code as appropriate.