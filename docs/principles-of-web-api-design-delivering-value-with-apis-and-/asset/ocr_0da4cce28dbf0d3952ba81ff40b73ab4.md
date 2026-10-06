# REST Was Never about CRUD

As already mentioned, REST is not a specification or a protocol. Contrary to popular opinion, a REST-based API does not require JSON or the use of the create-read-update-delete (CRUD) pattern of data interaction. REST is simply a set of constraints and agreements on how the individual components work together. This offers flexibility to address architectural issues. Many of today's Web-based APIs use JSON and the CRUD pattern as design elements.

Unfortunately

Frankly, these disagreements are not beneficial. Instead, it is best to approach an API labeled RESTful or REST-based with a mindset of grace and understanding that not everyone has read and fully applied the original REST paper. Use the opportunity to gently coach teams on how their architecture and API design can be improved over time. Whatever you do, please don't use the opportunity to show how much more you know about REST than they do.

# REST Is Client/Server

The client/server architecture is an essential REST constraint. The server hosts available resources, supporting operations through synchronous, message-based interactions that the client and server allows the user interface of the client interacts with it.

Separating the client and server allows the user interface of the client to change over time. New devices and interface styles may be used without requiring changes to the server.

Most important is that the client is able to evolve independently of the server. The server may offer new resources or additional representation formats without negatively impacting the client. This is fundamental to why APIs may be offered as products, with or without a preexisting user interface provided by the vendor.

# REST Is Resource-Centric

The key abstraction of information in REST is a resource. As mentioned in Chapter 1, “The Principles of API Design,” a resource consists of a unique name or identifier that can reference documents, images, collections of other resources, or a digital representation of anything in the real world, such as a person or thing.