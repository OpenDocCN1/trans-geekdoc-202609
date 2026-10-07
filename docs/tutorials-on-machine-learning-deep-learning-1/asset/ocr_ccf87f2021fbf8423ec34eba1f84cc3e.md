Those colored-vertical lines are central distribution i.e. the real expected values of the machine. The algorithm of course doesn't know about those.

At first all the machines are considered as similar. You have to have at least one or even a couple of trial rounds just to guess some data to analyze.

Say we run some trail in the blue machine, then the algorithm tries to make a distribution

![](bbox=[0.233, 0.189, 0.766, 0.403])

So we do the same things for other two, we pull the machines arm several times and draw a distribution for each machine.

![](bbox=[0.131, 0.473, 0.871, 0.638])

The actual meaning of these distributions is not what you might think at at first, these distributions are not trying to guess the distributions behind the machines.

+   The first thing that might come to mind is that (for instance): the blue distribution is attempting to guess the actual distribution behind the blue machine right. Or, same for the green or Orange !!!

But in reality they are not doing that; we are actually constructing distributions of where we think the actual expected value might lie.

![](bbox=[0.131, 0.755, 0.896, 0.969])