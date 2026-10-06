NIL
NIL
NIL
NIL
1

BUTTON
4
123
106
156
layout
dc-layout\ndisplay

T
1
T
OBSERVER
NIL
NIL
NIL
1

PLOT
583
13
949
182
Degree Distribution
degree
# of nodes
0.0
10.0
0.0
10.0
true
false
"""

```
PENS
"default" 1.0 1 -16777216 true "" "let max-degree max [count link-neighbors]
of turtles\nplot-pen-reset\nset-plot-x-range 0 (max-degree + 1)
nhistogram
[count link-neighbors] of turtles
```

MONITOR
4
246
140
291
NIL
clustering-coefficient

17
11

MONITOR
4
295