```
"included": [
{
  "type": "authors",
  "id": "765",
  "fullName": "Vaughn Vernon",
  "links": {
    "self": "/authors/765",
    "authoredBooks": { "href": "/books?authorId=765" }
  }
}
]
```

Static mocks may be provided using a Web server, such as Apache nginx, to allow frontend developers to integrate the mock API responses to the user interface. They will be able to provide feedback early and often as they start to parse and integrate the static mocks into their code.

It is important to note that static mocks lack any implementation, so mock integration will be limited to GET-based operations only. However, creating a static mock of an API operation that retrieves a resource representation is quite useful, easy to build, and provides opportunities for plenty of feedback.

# API Prototype Mocking

Throwaway prototype provides greater validation of an API design than a static mock. Unlike a static mock, which is often limited to GET-based operations, an API prototype is able to support all types of operations, including those that create or modify resource state.

API prototypes take more effort to produce manually. Typically, teams select a preferred programming language and framework that is optimized for rapid delivery. Ruby, Python, PHP, and Node.js are popular choices because of their fastest development and abundant libraries for producing APIs and synthesized data sets.

# Note

Teams may wish to select a language and framework that isn't supported for production by the organization. Doing so will ensure that prototypes intended to be throwaway don't suddenly become production code.