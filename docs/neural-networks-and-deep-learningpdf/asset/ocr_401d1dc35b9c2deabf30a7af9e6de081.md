to develop a technique called _gradient descent_ which can be used to solve such minimization problems. Then we'll come back to the specific function we want to minimize for neural networks.

Okay, let's suppose we're trying to minimize some function, \(C(v)\).
This could be any real-valued function of many variables,
\(v = v_1, v_2, ...\) . Note that I've replaced the \(w\) and \(b\) notation by \(v\) to emphasize that this could be any function - we're not specifically thinking in the neural networks context any more. To minimize \(C(v)\) it helps to imagine \(C\) as a function of just two variables, which we'll call \(v_1\) and \(v_2\) :

![](bbox=[0.247, 0.343, 0.563, 0.547])

What we'd like is to find where \(C\) achieves its global minimum.
Now, of course, for the function plotted above, we can eyeball the graph and find the minimum. In that sense, I've perhaps shown slightly _too_ simple a function! A general function, \(C\), may be a complicated function of many variables, and it won't usually be possible to just eyeball the graph to find the minimum.

One way of attacking the problem is to use calculus to try to find the minimum analytically. We could compute derivatives and then try using them to find places where \(C\) is an extremum. With some luck that might work when \(C\) is a function of just one or a few variables.
But it'll turn into a nightmare when we have many more variables. And for neural networks we'll often want _far_ more variables - the biggest neural networks have cost functions which depend on billions of weights and biases in an extremely complicated way.
Using calculus to minimize that just won't work!