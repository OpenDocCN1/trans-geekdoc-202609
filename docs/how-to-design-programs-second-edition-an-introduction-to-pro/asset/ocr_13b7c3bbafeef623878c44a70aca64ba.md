R = 10

to stand for the number of rectangles to be considered. Hence the width of each rectangle is

W = (b - a)/R .

The height of one of these rectangles is the value of f at its midpoint. The first midpoint is clearly at a plus half of the width of the rectangle,

S = width/2 ,

which means its area is

W · f(a + S) .

To compute the area of the second rectangle, we must add the width of one rectangle to the first midpoint:

W · f(a + W + S) ,

For the third one, we get

W · f(a + 2 · W + S) .

In general, we can use the following formula for the ith rectangle:

W · f(a + i · W + S) .

The first rectangle has index 0, the last one R - 1.
Using these rectangles, we can now determine the area under the graph: