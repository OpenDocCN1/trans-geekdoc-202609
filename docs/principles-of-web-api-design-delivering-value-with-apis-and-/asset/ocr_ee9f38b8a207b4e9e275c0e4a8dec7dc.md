Following is an example of a JSON-RPC call over HTTP. Notice the explicit mention of the method (the procedure) and the ordered parameter list that results in a tight coupling between client and server:

```
POST https://rpc.example.com/calculator-service HTTP/1.1
Content-Type: application/json
Content-Length: ...application/json
```

```
{"jsonrpc": "2.0", "method": "Subtract", "params": [42, 23], "id": 1}
```

Most RPC-based systems take advantage of a helper library and code generation tooling to generate the client and server stubs that are responsible for network communications. Those familiar with the fallacies of distributed computing recognize that failures can occur whenever code is executed remotely. One of RPC's goals is to remove invocation behavior as if it is calling a local procedure, network outages and failure-handling support is often incorporated into the client and server stubs and raised as an error.

The remote procedures are defined using an interface definition language (IDL). Code generators use the IDL to generate the client stub and a server skeleton that is ready for implementation. RPC-based APIs are generally faster to design and implement for this reason but are less resilient to method renaming and reordering of parameters.

# The gRPC Protocol

gRPC was created by Google in 2015 to speed the development of services through the use of RPC and code generation. Initially started as an initiative, it has since released and adopted by many organizations and open-source initiatives, including Kubernetes.

gRPC is built upon HTTP/2 for transport and Protocol Buffers for serialization. It also leverages the bidirectional streaming offered by HTTP/2, allowing the client to stream data to the server and the server to stream data back to the client. Figure 8.2 shows how multiple programming languages communicate using generated client stubs with a gRPC server within a GoLang-based service.

+   1. Wikipedia, s.v. "Fallacies of Distributed Computing," last modified July 24, 2021, 20:52, https://wikipedia.org/wiki/Fallacies_of_distributed_computing.
2. https://developers.google.com/protocol-buffers.