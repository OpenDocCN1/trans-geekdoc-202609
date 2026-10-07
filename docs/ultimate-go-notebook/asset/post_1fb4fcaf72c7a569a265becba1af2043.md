
![](img/8be06d78925d0d5a2d2ade851e9bad63_349_0.png)

Figure 18 is showing STW latency where all the Goroutines are stopped. This happens twice every collection. If your application is healthy, the collector should be able to keep the total STW time at or below 100 microsecond for the majority of collections.

You now know the different phases of the collector, how memory is sized, how pacing works, and the different latencies the collector inflicts on your running application. With all that knowledge, the question of how you can be sympathetic with the collector can finally be answered.

## Being Sympathetic

Being sympathetic with the collector is about reducing stress on heap memory. Remember, stress can be defined as how fast the application is allocating heap memory within a given amount of time. When stress is reduced, the latencies inflicted by the collector will be reduced. It's the GC latencies that are slowing down your application.

The way to reduce GC latencies is by identifying and removing unnecessary allocations from your application. Doing this will help the collector to:

- Maintain the smallest heap possible.
- Find an optimal consistent pace.
- Stay within the goal for every collection.
- Minimize the duration of every collection, STW and Mark Assist.

All these help reduce the amount of latency the collector will inflict on your running application. That will increase the performance and throughput of your application. The pace of the collection has nothing to do with it.

## Conclusion

If you take the time to focus on reducing allocations, you are doing what you can as a Go developer to be sympathetic with the garbage collector. You are not going to write zero allocation applications so it's important to recognize the difference between allocations that are productive (those helping the application) and those that are not productive (those hurting the application). Then put your faith and trust in the garbage collector to keep the heap healthy and your application running consistently.

Having a garbage collector is a nice tradeoff. I will take the cost of garbage collection so I don't have the burden of memory management. Go is about allowing you as a developer to be productive while still writing applications that are fast enough. The garbage collector is a big part of making that a reality.

## ULTIMATE GO NOTEBOOK

The Ultimate Go Notebook is the official companion book for the Ardan Labs Ultimate Go class. With this book, you will learn how to write more idiomatic and performant code with a focus on micro-level engineering decisions. This notebook has been designed to provide a reference to everything mentioned in class, as if they were your own personal notes.

If you have taken the class before, this notebook will be an invaluable resource for reminders on the content. If you have never taken the class, there is still tremendous value in this book as it covers more advanced topics not found in other books today.

> "If you want to be a better Go developer, code reviewer, designer and architect, this is the book you want."

When coming from another language, developers often struggle to builds layers of foundational knowledge that will give you a deeper understanding into data semantics, decoupling, concurrency and tooling that is provided with the language.

![](img/8be06d78925d0d5a2d2ade851e9bad63_351_0.png)

William has been developing software for more than 30 years. In 2013 he became a pioneer using Go and now has trained over 10,000 engineers who work for Fortune 100 companies. He can be found online at www.ardanlabs.com

## HOANH AN

Hoanh An is a software engineer with a background in distributed systems and the author of several popular open-source projects. In his free time, he enjoys reading and sharing his thoughts on different topics of software engineering, product development, and entrepreneurship on his blog.

![](img/8be06d78925d0d5a2d2ade851e9bad63_351_1.png)
