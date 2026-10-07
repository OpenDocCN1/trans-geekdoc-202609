# Figure 12.4

![](bbox=[0.121, 0.073, 0.905, 0.246])

There are two colors (or shades) that are represented in the heap graph. Orange (the darker shade) represents the amount of memory in-use on the heap at microsecond. Green (the lighter shade) represents when the next GC will be triggered based on when that amount of memory is once again in-use on the heap.

# Figure 12.5

![](bbox=[0.121, 0.467, 0.905, 0.683])

This is why when the orange area reaches the top of the green area, there is a line in the GC section. Each line represents a GC that took place. BTW, the dot is the selection point for the heap information listed here.

Since the green area is in a consistent straight line for the entire run of the program, I can select any orange point to see the max size of the heap.