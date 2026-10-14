
假设你是一个高级文档工程师和翻译员，请参考下面的注意事项了解 Markdown 文档的格式，然后参考示例，将给定英文文本翻译成中文。

## 注意事项

-   粗体（**bold**）和斜体（*itatic*）需要翻译翻译内容并保留符号。
-   内联代码（`code`）和代码块不需要翻译。
-   链接（[link](https://example.org)）需要翻译其内容，但保留网址。
-   列表，表格，引用块保留格式，翻译内容
-   原文可能有多行，不要漏掉任何一行，并且注意一定不要重复输出原文！！！
-   输出应包含在“[content]...[/content]”中

## 示例

原文：

[content]
-   [Feynman's learning method](https://wiki.example.org/feynmans_learning_method) is inspired by **Richard Feynman**, the Nobel Prize winner in physics. 

1.  With Feynman's skills, you can understand the knowledge points in depth in just `20 min`, and it is memorable and *hard to forget*. 

```
if (condVar > someVal) {console.log("xxx")}
```
[/content]

译文：

[content]
-   [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**理查德·费曼**。

1.  运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
if (condVar > someVal) {console.log("xxx")}
```
[/content]

## 以下是需要翻译的文本

[content]

Nothing says the techniques used have to resemble what a human would do. Quite the contrary, the power of computers is their ability to process large amounts of data very fast. Whereas a human will rely on reasoning and experience, a machine will test a billion solutions, from the most absurd to the most relevant, or search through giant databases in the same amount of time. It doesn’t think, it computes!

So, this is somewhat disappointing. However, it would be absurd to expect machines to do things “like humans.” They are not physically capable of it.

\_______ 

[1](#ch05.xhtml#Cfn5_1)  The name `Deep Thought` comes from the supercomputer in Douglas Adams’s humorous novel *The Hitchhiker’s Guide to the Galaxy*. In the book, the computer computes the “Answer to the Ultimate Question of Life, the Universe and Everything,” no less! According to the author, the answer is… `42`!

[2](#ch05.xhtml#Cfn5_2)  In 1975, the engineer and computer scientist `Gordon Moore` made a hypothesis that the number of transistors on a microprocessor doubles every two years. This assertion gave life to `Moore’s law`, which in plain language is “computer processing power doubles every two years.” This very imprecise assumption has become a target to aim for in the computer science industry, and it has pretty much been the norm since the 1970s.

| [The Journey Continues](#contents.xhtml#toc1_55)[*Understanding That One Graph Can Conceal Another*](#contents.xhtml#toc1_55) || [6](#contents.xhtml#toc1_55) |

| --- | --- |

Unlike humans, machines do not “think.” That’s why it’s difficult to make true artificial intelligence.

## [ON THE INTELLIGENCE OF MACHINES](#contents.xhtml#toc2_56)

As humans, we resolve problems by using our experience and our ability to reason. To develop AI algorithms, on the other hand, we have to “think AI.” All we have is a `Turing machine`, a strip of tape with small cells containing data and instructions to go from one cell to the next. Therefore, we have to find a technique that works with this tool and its strengths. This means computing power, not reasoning.

To help themselves with this task, artificial intelligence researchers can take inspiration from nature, which often does things very well. You may already have heard of *genetic algorithms*, artificial *neural networks*, or *ant colony algorithms*. Behind these peculiar names are AI methods inspired, in one form or another, by nature.

## [A VERY PARTICULAR TRAVELER](#contents.xhtml#toc2_57)

To understand these different methods, let’s consider an amusing problem known as the *traveling salesman* problem. Imagine you are a sales representative for some company – a company that makes air conditioners, let’s say. Your job is to present your new models in several large cities throughout France. Naturally, you want to make the trip as efficient as possible by spending the least possible amount of time on the road.

When you put it that way, the problem looks similar to our GPS story. However, it is very different.

![image](images/inline6_1.jpg)

## [A HEALTHY WALK](#contents.xhtml#toc2_58)

Naturally, it is also a graph problem. If we represent each city as a point on a graph and connect each point to all the others with “lines” showing the time required to go from one city to the next, we indeed get a graph that we’ll have to travel across.

But this isn’t about finding a path from one point to another. To start, all the points are connected to each other. So the path is a piece of cake! What we need is to find the shortest path that passes through *all* of the points on the graph.

This problem is very well known in computer science… and it is impossible to resolve it efficiently! It is nothing like the GPS problem or Dijkstra’s algorithm: that’s child’s play compared to this! To give you an idea, if you try to find an exact solution to the traveling salesman problem for a graph with 20 points, the best algorithms possible will take a hundred years to give you an answer with a modern computer. With Dijkstra’s algorithm, you get an answer in under a second for a graph with 1,000 points.

## [A REALLY DIFFICULT PROBLEM…](#contents.xhtml#toc2_59)

The traveling salesman problem has many applications in computer science, but that’s not all. In the “door-to-door” category, in addition to urban furniture and sonic vacuum sales, it can also be used by an power company to determine the route the meter reader should take, by a pizza company for customer deliveries, by the post office to deliver mail as quickly as possible, by the city to pick up garbage, and so on.

The solution to this problem is also needed to optimize the computational costs for computer graphics cards, to test electronic circuits, or to control the movements of industrial machinery. The economic implications are huge!

Very early on, computer scientists sought to provide a “good” solution to the traveling salesman problem in a reasonable amount of time, in the absence of an exact solution.

## [THE GREEDY ALGORITHM](#contents.xhtml#toc2_60)

Over the course of time, several AI algorithms have been proposed. The first of them has a very original name: the *greedy* algorithm. This AI method uses a simple heuristic: at each stage, the traveler chooses the city that is closest to where he is (and which he hasn’t visited yet, of course).

In computing terms, we just choose the one that’s the closest distance away from among the remaining unvisited points. We can write the algorithm as follows:

Let `C` be the set of all the non-visited points in the graph.

Let `p` be the closest point in `C` to the current position.

Go to the point and remove it from `C`.

If `C` is empty, you are finished. If not, resume.

This algorithm is called “greedy” because it never reconsiders a previously selected city. It just goes straight ahead, traveling miles and miles without ever thinking about it.

![image](images/inline6_2.jpg)

## [AT LEAST, IT’S FAST!](#contents.xhtml#toc2_61)

Greedy algorithms are used in numerous problems in computer science. The version we use in the traveling salesman problem is known as the *nearest neighbor algorithm* because it chooses the nearest neighbor (from among those who haven’t been visited yet).

What can we say about this algorithm?

First, it effectively calculates a solution: that’s a good start. Plus, it does it very fast. The program’s complexity is the number of points squared, the same as with Dijkstra’s algorithm, which we used for the GPS. This means the computer can work on graphs with a thousand points before hitting any real difficulty. Not so bad, right? Especially for an AI algorithm that requires less than ten lines of computer code!

Now, with that being said, the solution probably won’t be the best. In certain cases, it can even be very bad.

Imagine we leave from Limoges and have to visit Toulouse, Bordeaux, Marseille, and Nantes before we return to Limoges. With the greedy algorithm, we’re going to go to Bordeaux first (137 miles), then to Toulouse (152 miles), then to Marseille (252 miles), before we go 615 miles in the opposite direction to Nantes, passing through Bordeaux and Toulouse, or through Clermont-Ferrand. If we had done a little thinking, we probably would have gone to Nantes first, which is, admittedly, a little further from Limoges than Bordeaux (186 miles), but then we would have passed through all the other cities in a loop (Nantes, Bordeaux, Toulouse, Marseille), instead of making the same trip twice. Our loop would have been 805 miles instead of almost 1,160 miles!

## [COME ON, WE CAN DO BETTER!](#contents.xhtml#toc2_62)

The problem with the greedy algorithm is that it doesn’t attempt to do any better than the first path it determines. It’s a real shame because this first solution isn’t necessarily very good, and it might be easy to fix a few mistakes, like going to Nantes and back, which isn’t well positioned on the route.

