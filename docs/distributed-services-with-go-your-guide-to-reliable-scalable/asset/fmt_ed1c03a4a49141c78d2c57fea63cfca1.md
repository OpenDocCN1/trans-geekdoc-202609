
|​  || require.Equal(t, got, want) |

Now we check that Raft has replicated the record we produced to the leader by consuming the record from a follower and that the replication stops there—the leader doesn’t replicate from the followers.

Run your tests with $ make test. Your distributed service now uses Raft for consensus and replication!

## What You Learned

In this chapter, you learned how to coordinate distributed services with Raft by adding leader election and replication to our service. We also looked at how to multiplex connections and run multiple services on one port. Next, we’ll talk about client-side discovery, so clients can discover and call our servers.

#### Footnotes

[\[48\]](#f_0061.xhtml#FNPTR-48)

: 

[https://cwiki.apache.org/confluence/display/KAFKA/KIP-500:+Replace+ZooKeeper+with+a+Self-Managed+Metadata+Quorum](https://cwiki.apache.org/confluence/display/KAFKA/KIP-500:+Replace+ZooKeeper+with+a+Self-Managed+Metadata+Quorum)

[\[49\]](#f_0062.xhtml#FNPTR-49)

: 

[https://www.cockroachlabs.com/blog/scaling-raft](https://www.cockroachlabs.com/blog/scaling-raft)

[\[50\]](#f_0062.xhtml#FNPTR-50)

: 

[https://github.com/boltdb/bolt](https://github.com/boltdb/bolt)

[\[51\]](#f_0063.xhtml#FNPTR-51)

: 

[https://tools.ietf.org/html/rfc7983](https://tools.ietf.org/html/rfc7983)

Copyright © 2021, The Pragmatic Bookshelf. 

## Three Load-Balancing Strategies

Three strategies can be used for solving the discovery and load balancing problem:

*   Server proxying—your client sends its requests to a load balancer that knows the servers (either by querying a service registry or by being the service registry) and proxies the requests to your back-end services.

*   External load balancing—your client queries an external load-balancing service that knows the servers and tells the client which server to send the RPC.

*   Client-side balancing—your client queries a service registry to learn about the servers, picks the server to send its RPC, and sends its RPC directly to the server.

Using a server proxy is the most commonly used discovery and load-balancing pattern. Most servers don’t trust their clients enough to give them control over how load balancing works because these decisions might affect the service’s availability (for example, allowing a client to target a single server and call it until it’s unavailable). You can put a proxy between clients and servers to act as a trust boundary. The proxy lets you control how your system ingests requests, as all the networking behind the proxy is in your network, trusted, and under your control. The server proxy knows about the servers it proxies to by maintaining or calling a service registry. People often use AWS’s Elastic Load Balancer (ELB) to load balance external traffic from the internet. The ELB is an example of a service-side discovery router—incoming requests hit the ELB, and the ELB proxies that request to one instance registered with the ELB.

For complex and very accurate load balancing, you can run an external load balancer. The external load balancer knows all the servers and potentially all the clients, so it has all the data to decide the best server for the client to call. You pay for external load balancers with operational burden. I’ve never needed an external load balancer.

Alternatively, you can use client-side load balancing when you trust the clients. Client-side load balancing reduces latency and increases efficiency because requests go directly to their destination—there are no intermediates. This load balancing pattern is resilient because there isn’t a single point of failure. However, you need to work on your network and security to give clients direct access to your servers.

We’ll build client-side discovery and load balancing into our service because we control both the client and server and we designed our service for low-latency, high-throughput applications.

## Load Balance on the Client in gRPC

Though the ideas we’ll talk about in this chapter can apply to any client and server, because our service is a gRPC service, we’ll use those terms. gRPC separates server discovery, load balancing, and client requests and response handling—often the only code you’ll write is the latter. In gRPC, resolvers discover servers and pickers load balance by picking what server will handle the current request. gRPC also has balancers that manage subconnections but defer the load balancing to the pickers. gRPC provides an API (base.NewBalancerBuilderV2) to create a base balancer, but you probably won’t have to write your own balancer.

When you call grpc.Dial, gRPC takes the address and passes it on to the resolver, and the resolver discovers the servers. gRPC’s default resolver is the DNS resolver. If the address you give to gRPC has multiple DNS records associated with it, gRPC will balance the requests across each of those records’ servers. You can write your own resolvers and use resolvers written by the community. For example, Kuberesolver^([\[52\]](#f_0072.xhtml#FOOTNOTE-52)) resolves the servers by fetching the endpoints from Kubernetes’ API.

gRPC uses round-robin load balancing by default. The round-robin algorithm works by sending the first call to the first server, the second call to the second server, and so on. After the last server, it goes back to the first server again. So, we send each server the same number of calls. Round-robin works well when each request requires the same work by the server—stateless services that defer the work to a separate service like a database, for example. You can always begin with round-robin load balancing and optimize later.

The issue with round-robin load balancing, however, is that it doesn’t consider what you know about each request, client, and server. For example:

*   If your server is a replicated distributed service with a single writer and multiple readers, you’ll want to read from replicas so the writer can focus on the writes. This requires knowing whether the request is a read or a write and whether the server is a primary or a replica.

*   If your service is a globally distributed service, you’ll want your clients to prioritize networking with local servers, which means you must know the location of the clients and the servers.

*   If your system is latency sensitive, you can track metrics on how many in-flight or queued requests a server has or some other combination of latency metrics and have the client request the server with the smallest number.

Now you’ve seen how client-side discovery and load balancing work in gRPC, and when you might want to go beyond round-robin to load balance more efficiently, what can you do with this knowledge when building your own services?

The service we’re building is a single-writer, multiple-reader distributed service—the leader server is the only server that can append to the log. Currently our clients connect to a single server, so if we want to call a leader and a follower, we have to create multiple clients. And if we want to balance consume calls across the followers, we have to manage it in our client code.

We can solve some problems by writing our own resolver and picker: the resolver discovers the servers and what server is the leader, and the picker manages directing produce calls to the leader and balancing consume calls across the followers. The resolver and picker will make your service easier to use, and we’ll be able to delete some of our test code too. Hopefully that sounds sweet to you—it does to me—so let’s get started.

## Test Discovery and Balancing End-to-End

We’re ready to update our agent’s tests to test everything end-to-end: the client configuring the resolver and picker, the resolver discovering the servers, and the picker picking subconnections per RPC.

Open your agent tests in internal/agent/agent_test.go and add this import:
