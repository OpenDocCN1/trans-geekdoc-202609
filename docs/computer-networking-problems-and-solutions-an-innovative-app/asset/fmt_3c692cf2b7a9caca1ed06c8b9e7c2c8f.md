
The problem link aggregation faces is determining which packets should be sent down which member of the bundle. Intuitively, this might not seem like a problem. After all, it would seem to make sense to use the link bundle in a round-robin fashion. The initial frame would be sent down the first member of the bundle, the second frame down the second member, and so on, eventually wrapping back around to the first link bundle member. In this way, the link should be used perfectly evenly, and bandwidth should scale linearly.

There are a very few real-life implementations where aggregated links are used on a round-robin basis like this because they run the risk of delivering out-of-order packets. Assume Ethernet frame one is sent down link member one, and frame two is sent down link member two immediately after. For whatever reason, frame two gets to the other end before frame one. The packets that these frames contain will be delivered to the receiving hosts out of order—packet two before packet one. This is a problem because a computational burden is now placed on the host to reorder the packets so the entire datagram can be properly reassembled.

Therefore, most vendors implement flow hashing to ensure the entirety of a traffic flow uses the same bundle member. In this way, there is no risk of a host receiving packets out of order, as they will be sent sequentially across the same link member.

## Hash Algorithms

A hash is a simple concept that is actually quite difficult to implement in a useful way: a hash takes a string of numbers of any size and returns a fixed length number, or hash, that (more or less) uniquely represents the original string. The simple-to-implement part is this: one rather naïve hash is to simply add the numbers in a set of numbers until you reach a single digit, calling the result the hash. For instance:

[Click here to view code image](#ch07_images.xhtml#p07pro01a)

```
23523  
2 + 3 + 5 + 2 + 3 == 15  
1 + 5 == 6
```

Hence, the number 23523 can be *represented* as 6. One curious property of the hash is there is no way to determine, from the hash, what the original number was—this is one of the essential observations of many uses for the hash. If I share a number with some third party, and that party then shares it with you, you can ask me for the hash of the number (without telling me what the actual number is!), and you can verify the number is the same by verifying the hash I give you matches the one you calculate.

The hash here is naïve because it is too easy to obtain a *collision*. In other words, there are many different sets of numbers that will result in a hash of 6 given the same process, such as 222, 33, 111111, and (probably) an almost infinite number of others. In some situations, collisions are extremely undesirable. For instance, if you are trying to store pairs of numbers, where you look up the first number to find the second (an indexing problem), then you want to minimize collisions. Once you have computed the hash of the number you are using as the index, you do not want to have the result point to a hash bucket with a lot of entries, as each entry in the bucket needs to be searched to find the index. In the extreme case, every number will index into a single hash bucket, resulting in the hash being completely ineffective as a sorting tool.

In other cases, such as the load-sharing example given here, it is more important to make certain the hash spreads entries out among the available buckets as evenly as possible. You want to make certain each bucket contains about the same number of entries, as each bucket represents a single link, and you want the links to each receive the traffic of about the same number of destinations.

Flow hashing works by performing a mathematical operation on two or more static components of a flow, such as source and destination `MAC` addresses, source and destination Internet Protocol (`IP`) addresses, or Transmission Control Protocol (`TCP`) or User Datagram Protocol (`UDP`) port numbers to compute a link member the flow will use. Because the characteristics of the flow are static, the hashing algorithm results in an identical computation for each frame or packet in a traffic flow, guaranteeing the same link will be used for the life of the flow.

While flow hashing solves the out-of-order packet problem, it introduces a new problem. Not all flows are the same size. Some flows use a high amount of band-width, such as those used for file transfers, backups, or storage; these are sometimes called *elephant flows*. Other flows are quite small, such as those used to load a web page or communicate using voice over IP; these are sometimes called *mouse flows*. Because flows are different sizes, some link members might be running at capacity, while others are underutilized.

This mismatch in utilization brings us back around to the point about linear scaling. If frames were load-balanced across an aggregated link bundle perfectly evenly, then adding new links to the bundle would evenly multiply capacity. However, hashing algorithms combined with the unpredictable volume of traffic flows mean bundled links will not be evenly loaded.

The job of the network engineer is to understand the type of traffic flowing through the aggregated bundle and choose an available hashing algorithm that will result in the most even load distribution. For instance, some considerations might be

• Are many hosts in the same broadcast domain communicating with one another across the aggregated link? Hashing against the `MAC` addresses found in the `Ethernet` frame header is a possible solution, because the `MAC` addresses will be varied.

• Are a small number of hosts communicating to a single server across the aggregated link? There might not be enough variety of either `MAC` addresses or `IP` addresses in this scenario. Instead, hashing against `TCP` or `UDP` port numbers might result in the greatest variety and subsequent traffic distribution across the aggregated links.

### Link Aggregation Control Protocol

When bundling links together, you must consider the network devices on either end of the link and take special care to allow the link bundle to be formed while maintaining a loop-free topology. The most common way of addressing this issue is by using industry standard Link Aggregation Control Protocol (`LACP`), codified as Institute of Electrical and Electronic Engineers (`IEEE`) standard `802.3ad`.

On links designated by a network engineer, `LACP` advertises its intent to form an aggregated link to the other side. The other side, also running `LACP`, accepts this advertisement if the announced parameters are valid, and forms the link. Once the link bundle has been formed, the aggregated link is placed into a forwarding state. Network operators can then query `LACP` for status on the aggregated link and the state of link members.

`LACP` is also aware when a member of the link bundle goes down, as control packets no longer flow across the failed link. This capability is useful, as it allows the `LACP` process to notify the network operating system to recalculate its flow hashes. Without `LACP`, it might take the network operating system a longer time to become aware of the failed link, causing traffic to be hashed to a link member that is no longer a valid path.

Other link aggregation control protocols exist. It is also possible in some scenarios to create link bundles manually without the protection of a control protocol; however, `LACP` dominates as the standard in use by networking vendors as well as host operating systems and hypervisor vendors for link aggregation.

### Multichassis Link Aggregation
