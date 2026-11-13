**Sample Problem** Design an algorithm that proposes a way to introduce one person to another in a directed email graph for a large company. The program consumes a directed graph representing established email connections and two email addresses. It returns a sequence of email addresses that connect the first email with the second.

Mathematical scientists call the desired sequence a *path*.

Figure 168 makes the sample problem concrete. For example, you may wish to test whether the program can find a path from C to D. This particular path consists of the origination node C and the destination node D. In contrast, if you wish to connect E with D, there are two paths:

+   * send email from E to F and then to D.

+   * send it from E to C and then to D.

Sometimes it is impossible to connect two nodes with a path. In the graph of figure 168, you cannot move from C to G by following the arrows.

Looking at figure 168 you can easily figure out how to get from one node to another without thinking much about how you did it. So imagine for a moment that the graph in figure 168 is a large park. Also imagine someone says you are located at E and you need to get to G. You can clearly see two paths, one leading to C and another one leading to F. Follow the first one and make sure to remember that it is also possible to get from E to F. Now you have a new problem, namely, how to get from C to G. The key insight is that this new problem is just like the original problem; it asks you to find a path from one node to another. Furthermore, if you can solve the problem, you know how to get from E to G—just add the step from E to C. But there is no path from C to G. Fortunately, you remember that it is also possible to go from E to F, meaning you can *backtrack* to some point where you have a choice to make and restart the search from there.

Now let’s design this algorithm in a systematic manner. Following the general design recipe, we start with a data analysis. Here are two compact list-based representations of the graph in figure 168: