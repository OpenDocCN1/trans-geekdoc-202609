# What Is a REST-Based API?

111

RMM was meant to be used as a general classification of an API's improvement as designers seek to reach a design that uses hypermedia controls. Unfortunately, it has been used to denigrate the efforts of designers by proving that an API labeled as REST-compliant has not met sufficient criteria to be truly labeled REST.

Richardson described the confusion and intent of RMM in a 2015 REST fest titled "What Have I Done?" Richardson described the whole idea of RMM as "very embarrassing" and said it was meant simply as possible measurement of improvement and maturity when attempting to target a hypermedia API. It was not meant to be a canonical method of classifying all APIs as REST-compliant. Instead, design to meet the needs of clients rather than trying to measure a specific level of design maturity.

# When to Choose REST

Fielding's dissertation explicitly defines REST as an architectural style for coarse-grained data transfer:

The REST interface is designed to be efficient for large-grain hypermedia data transfer, optimizing for the common case of the Web, but resulting in an interface that is not optimal for other forms of architectural interaction.

While Fielding defines fine grain explicit, the Web is a good example. An HTML page is sent as a single, complete resource. It is not split into separate assets and retrieved separately. Once the HTML resource has been received and parsed, all images, JavaScript, and style sheets are retrieved individually.

REST is a good architectural style when the interaction level requires course-grained resources over HTTP. This is common for APIs that may encounter additional latency or unpredictable connectivity.

For finer-grained interaction styles, RPC or other styles may be a better fit. RPC styles offer improved performance and long-running connections that do not meet the REST constraints outlined by Fielding. This includes the choice of gRPC and asynchronous API styles, discussed in Chapter 8 and Chapter 9, "Messaging, Streaming, and Event-Based Async APIs," for service-to-service and client-to-service interactions.

+   2. Leonard Richardson, "What Have I Done?" (lecture, REST Fest, Greenville, SC, September 18, 2015).