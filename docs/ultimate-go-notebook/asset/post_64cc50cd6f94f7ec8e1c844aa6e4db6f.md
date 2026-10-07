
# Reading

+   * Software Development for Infrastructure - Bjarne Stroustrup
* Normalization of Deviance in Software - danlu.com
* Lessons learned from reading postmortems - danlu.com
* Technical Debt Quadrant - Martin Fowler
* Design Philosophy On Integrity - William Kennedy
* Ratio of bugs per line of code - Dan Mayer
* Developing Software The Right Way, with Intent and Carefulness - David Gee
* What bugs lie in the Cloud - usenix.org
* Masterm of Programming - Federico Biancuzzi and Shane Warden

# 1.8.2 Readability

I must structure my systems to be more comprehensible.

This is about writing simple code that is easier to read and understand without the need of mental exhaustion. Just as important, it's not about the cost/impact of the code per line, function, package and the overall ecosystem it runs in.

# Code Must Never Lie

It doesn't matter how fast the code might be if no one can understand or maintain it moving forward.

# Average Developer

I must be aware of who I am on my team. When hiring new people, I must be aware of where the new person falls. Code must be written for the average developer to comprehend. If I'm below average for my team, I have the responsibility to work to average. If I'm above average, I have the responsibility to reduce writing clear code and coach/mentor.

# Real Machine

In Go, the underlying machine is a real machine, unlike what I would find in Java or C# with their virtual machine layer. The model of computation is that of the computer. Here is the key, Go gives me direct access to the machine while still providing abstraction mechanisms to allow higher-level ideas to be expressed.

# Quotes

+   * "This is a cardinal sin amongst programmers. If code looks like it's doing one when it's actually doing something else, someone down the road will read code and misunderstand it, and use it or alter it in a way that causes bugs. That someone might be you, even if it is your code in the first place." - Nate Finch
* "Can you explain it to the median user (developer)? as opposed to will the smartest user (developer) figure it out" - Peter Weinberger (inventor of AWK)
+   - "Making things easy to do is a false economy. Focus on making things easy to understand and the rest will follow." - Peter Bourgeon

# Reading

+   - Code Must Never Lie - Nate Finch

# 1.8.3 Simplicity

I must understand that simplicity is hard to design and complicated to build.

This is about hiding complexity. A lot of care and design must go into simplicity because it can cause more problems than it solves. It can create issues with readability and it cause issues with performance.

# Complexity Sells Better

Focus on encapsulation and validate that I'm not generalizing or even being too concise. I need to validate my code is still easy to use, understand, debug and maintain.

# Encapsulation

Encapsulation is what the industry has been trying to figure out for 40+ years. Go is a slightly new approach with packaging. Bringing encapsulation up a level and providing richer support at the language level.

# Quotes

+   - "Simplicity is a great virtue but it requires hard work to achieve it and education to appreciate it. And to make matters worse: complexity best." - Edsger W. Dijkstra
+   - "Everything should be made as simple as possible, but not simpler." - Albert Einstein
+   - "You wake up and say, I will be productive, not just today." - Dave Cheney
+   - Paraphrasing: "Encapsulation and the separation of concerns are for designing software. This is largely based on how other industries handle complexity. There seems to be a human pattern using encapsulation to wrestle complexity to the ground." - Brad Cox (inventor of Object C)
+   - "The purpose of abstraction is not to be vague, but to create a new semantic level in which one can be absolutely precise." - Edsger W. Dijkstra
+   - "A proper abstraction decouples the code so that every change doesn't echo throughout the entire code base." - Ronna Steinberg
+   - "A good API is not just easy to use but hard to misuse." - JBD
"Computing is all about abstractions. Those below yours are just details. Those above yours are limiting complicated crazy town." - Joe Beda

# Reading

+   - Simplicity is Complicated - Rob Pike
- What did Alan Kay mean, "Lisp is the greatest single programming language ever designed?" - Alan Kay

# 1.8.4 Performance

I must compute less to get the results we need.

This is not about wasting effort and achieving execution efficiency. Writing code that is mechanically sympathetic with the runtime, operating system and hardware. Achieving performance by writing less and more efficient code, but staying within the idioms and framework of the language.

# Rules of Performance

+   - Never guess about performance.
- Measurements must be relevant.
- Profile before I decide something is performance critical.
- Test to know I'm correct.

Rules Of Optimization Club

# Broad Engineering

Performance is important but it can't be my priority unless the code is not running fast enough. I only know this once I have a working program and I have validated it. The industry places those we think know how to write performant code on a pedestal. I need to put those whose code that is optimized for correctness and performs fast enough on those pedestals.

# Quotes

+   - Programmers waste enormous amounts of time thinking about, or worrying about, the speed of noncritical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget small efficiencies, say about 97% of the time: premature optimization is the root of all evil. We should not pass up our opportunities in that critical 3%." — Donald E. Knuth
- "I don't try anything until it runs twice." In fact, I don't try anything until it runs twice - Andrew Gelman (one of the greatest living statisticians at Columbia University).
+   - When we're computer programmers we're concentrating on the intricate little fascinating details of programming and we don't take a broad engineering point of view about trying to optimize the total system. You try to optimize the bits and bytes.\ - Tom Kurtz (inventor of BASIC)

# 1.8.5 Micro-Optimizations

Micro-Optimizations are about squeezing every ounce of performance out of the machine as possible. When code is written with this as the priority, it's very difficult to write code that is readable, simple or idiomatic.

# 1.8.6 Data-Orientation

Data oriented is a core philosophy and concept with the language. I must embrace data oriented design with a prototype first approach.

> "Data dominates. If you've chosen the right structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming." - Rob Pike

# Design Philosophy

+   * If I don't understand the data, I don't understand the problem.
* All programs are unique and specific to the data I'm working with.
* Data transformations are at the heart of solving problems. Each function, method and work-flow must focus on implementing the specific data transformations required to solve the.
* If my data is changing, my problems are changing. When my problems are changing, data transformations need to change with it.
* Uncertainty about the data is not a license to guess but a directive to STOP and learn more.
* Solving problems I don't, create more problems I now do.
* If performance matters, I must have mechanical sympathy for how the hardware and operating system work.
* Minimize, simplify and reduce the amount of code required to solve each problem. Do less work by wasting effort.
* Code that can be reasoned about and does not hide execution costs can be better understood, debugged and performance tuned.
* Coupling data together and writing code that produces predictable access patterns to the data will be the most performant.
* Changing data layouts can yield more significant performance improvements than just using the algorithms.

# Reading

+   * Data-Oriented Design and C++ - Mike Acton
* Efficiency with Algorithms, Performance with Data Structures - Chandler Carruth
