1.0 \cdot 10^{16} + 1 = 1.0000000000000001 \cdot 10^{16},

but the closest representable answer is 10^{16}.

At first glance, this approximation doesn’t look too bad. Being wrong by one part in 10^{16} (ten million billion) is close enough to the truth. Unfortunately, this kind of problem can add up to huge problems. Consider the list of numbers in figure 144 and determine the values of these expressions:

+   - (sum JANUS)
+   - (sum (reverse JANUS))
+   - (sum (sort JANUS <))

```
(define JANUS
 (list 31.0
   #i2e+34
   #i1-1.2345678901235e+80
   2749.0
   -2939234.0
   #i-2e+33
   #i3.2e+270
   17.0
   #i-2.4e+270
   #i14.2344294738446e+170
   1.0
   #i-8e+269
   0.0
   99.0))
```

# Figure 144: A Janus-faced series of inexact numbers

Assuming sum adds the numbers in a list from left to right, explain what these expressions compute. What do you think of the results?

Generic advice on inexact calculations tells programmers to start additions with the smallest numbers. While adding a big number to two small numbers might yield the big one, adding small numbers first creates a large one, which might change the outcome:

```
> (expt 2 #i53.0)
#i9007199254740992.0
```