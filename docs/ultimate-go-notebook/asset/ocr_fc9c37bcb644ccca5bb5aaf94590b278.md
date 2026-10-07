# Pacing

The collector has a pacing algorithm which is used to determine when a collection is to start. The algorithm depends on a feedback loop that the collector uses to gather information about the running application and the stress the application is putting on the heap. Stress can be defined as how fast the application is allocating heap memory within a given amount of time. It's that stress that determines the pace at which the collector needs to run.

Before the collector starts a collection, it calculates the amount of time it will take to finish the collection. Then, once a collection is running, latencies will be inflicted on the running application that will slow down application work. Every collection adds to the overall latency of the pacing.

One misconception is thinking that slowing down the pace of the collector is a way to improve performance. The idea being, if you can delay the start of the collection, then you are delaying the latency it will inflict. Being sympathetic with the collector isn't about slowing down the pace.

You could decide to change the GC Percentage value to something larger than 100. This will increase the amount of heap memory that can be allocated before the next collection has to start. This could result in the pace of collection to slow down. Don't consider doing this.

Figure 14

| | 100% | 200% | 300% | 400% | 500% |
|---|---|---|---|---|---||
| 6MB | 12MB | 18MB | 24MB | 30MB | 36MB |

Figure 14 shows how changing the GC Percentage would change the amount of heap memory allowed to be allocated before the next collection has to start. You can visualize how the collector could be slowed down as it waits for more heap memory to become in-use.

Attempting to directly affect the pace of collection has nothing to do with being sympathetic with the collector. It's really about getting more work done between each collection or during the collection. You affect that by reducing the amount or the number of allocations any piece of work is adding to heap memory.

Note: The idea is also to achieve the throughput you need with the smallest heap memory possible. Remember, minimizing the use of resources like heap memory is