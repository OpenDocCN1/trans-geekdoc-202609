# 228 CHAPTER 12 API TESTING STRATEGIES

Contract testing answers the following questions:

+   - Is each operation working to the specification for all success cases?
- Are input parameters being followed? How are bad inputs handled?
- Are the expected outputs received?
- Is response formatting correct? Are the proper data types used?
- Are errors being handled correctly? Are they reported back to the consumer?

In the Align-Define-Design-Refine (ADDR) process, API descriptions are defined during the process, prior to implementation. These description files may be used to verify the API contract as part of the contract testing process. Some common specification formats for REST APIs OpenAPI (Swagger), API Blueprint, and RESTful API Modeling Language (RAML). GraphQL APIs have a schema defined, which helps drive contract testing. gRPC defines service contracts using an interface definition (IDL) file. This topic is discussed further in Chapter 13, "Documenting the API."

API contract testing must first ensure the correctness of each API operation. Handling thousands of clients per minute does not get the information that the API is providing or acting on not meet the API's specification. Identifying and eliminating bugs, hunting out inconsistencies, and verifying that an API meets the specification against which it has been designed all fall under the umbrella of testing for correctness.

Next, API contract testing must focus on reliability. The API should provide the correct information every time an operation is called. Executing the same action repeatedly for an API operation designed to be idempotent should produce the same results. API operations that support pagination page produce results in a predictable way.

Finally, API contract testing should submit invalid and missing data and verify that the expected error response is received. String values may be submitted in place of numeric values, along with values outside the range of acceptable values. Date formats should be incorrect or result in dates outside an expected range of acceptable dates.

# User Interface Testing versus API Testing

Some members may suggest that building dedicated tests for an API is wasteful. They may attempt to make the case that user interface (UI) tests cover the API sufficiently, given that the UI calls the API. However, this is not