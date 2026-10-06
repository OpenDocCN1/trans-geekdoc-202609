# THE API MODELING PROCESS

# 91

Event names should be presented in past tense and should apply the preferred standards and practices used within the organization. 6.9 expands the previous model with events that each operation will emit. Notice the past-tense naming in the Emitted Events column.

The API profile now reflects what the identified operations will emit. Some operations may only emit one event, some more than one event, and some may not need to emit any event at all.

# Step 5: Expand Operation Details

The final step is to expand the details of each operation to include important input and output details. Don't be too concerned with capturing everything at this point, as it is unnecessary. Focus on the essential input and output resources and parameters necessary to convey understanding across the team. There is no need to capture the type of each property or define a schema in the API model at this stage. Avoid being overly concerned with finding every parameter, as there will be plenty of time during the design phase to capture the complete design. If necessary, use a “parking lot” to capture important items that will need to be addressed as the design emerges.

An additional level of detail that is used to inform the upcoming API design is the matter of operations being synchronous or asynchronous. Synchronous APIs operate in a traditional request/response manner common to HTTP. Asynchronous APIs operate in the background rather than providing an immediate result. Asynchronous APIs are discussed in Chapter 9, “Messaging, Streaming, and Event-Based Async APIs.\ For now the synchronous nature of each operation.

An often-overlooked detail for operations is safety. Safety and idempotence are important concerns when selecting the appropriate HTTP method. Each HTTP method specification describes the safety and idempotency that a server must implement. Safety classifications are also important for clients to consider as part of their error-handling code.

There are three classifications of safety for HTTP operations:

+   1. Safe: The operation does not make any changes to the target resource(s). This safety classification is assigned to all read-based (GET) operations.

+   2. Idempotent: The operation makes state changes to the target resource(s), but if the operation is executed with the same input, it will produce the same result. This is important, as it informs API clients if they can reissue a request that previously failed, without additional side effects. This safety classification is assigned to replace and delete operations (PUT and DELETE).