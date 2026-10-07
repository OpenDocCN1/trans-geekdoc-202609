engineering point of view about trying to optimize the total system. You try to optimize the bits and bytes.\ - Tom Kurtz (inventor of BASIC)

# 1.8.5 Micro-Optimizations

Micro-Optimizations are about squeezing every ounce of performance out of the machine as possible. When code is written with this as the priority, it's very difficult to write code that is readable, simple or idiomatic.

# 1.8.6 Data-Orientation

Data oriented is a core philosophy and concept with the language. I must embrace data oriented design with a prototype first approach.

> "Data dominates. If you've chosen the right structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming." - Rob Pike

# Design Philosophy

+   * If I don't understand the data, I don't understand the problem.
* All programs are unique and specific to the data I'm working with.
* Data transformations are at the heart of solving problems. Each function, method and work-flow must focus on implementing the specific data transformations required to solve the problems.
* If my data is changing, my problems are changing. When my problems are changing, data transformations need to change with it.
* Uncertainty about the data is not a license to guess but a directive to STOP and learn more.
* Solving problems I don't, create more problems I now do.
* If performance matters, I must have mechanical sympathy for how the hardware and operating system work.
* Minimize, simplify and reduce the amount of code required to solve each problem. Do less work by wasting effort.
* Code that can be reasoned about and does not hide execution costs can be better understood, debugged and performance tuned.
* Coupling data together and writing code that produces predictable access patterns to the data will be the most performant.
* Changing data layouts can yield more significant performance improvements than just using the algorithms.
* Efficiency is obtained through algorithms but performance is obtained through data structures and layouts.

# Reading

+   * Data-Oriented Design and C++ - Mike Acton
* Efficiency with Algorithms, Performance with Data Structures - Chandler Carruth