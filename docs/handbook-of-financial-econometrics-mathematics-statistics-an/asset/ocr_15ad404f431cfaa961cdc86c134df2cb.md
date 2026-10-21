```
For j = Nstep - 1 To 0 Step -1
    For i = 0 To 2 * j
        vvec(i) = (pu * vvec(i + 2) + pm * vvec(i + 1) + pd * vvec(i)) / erdt
    Next i
Next j
TriCall = vvec(0)
End Function
```

Similar data can be used in this function and the same call option at today’s price can be obtained.

![](bbox=[0.09, 0.32, 0.93, 0.62])

The function in cell B12 is equal to

= TriCall(B3, B4, B5, B6, B8, B7, B10, B9).

# 84.7.3 Comparison of the option price efficiency

In this section, we would like to compare the efficiency of these two methods. In the following table, we represent different numbers of steps 1,2,… to 50, and we represent Black and Scholes, CRR binomial tree and trinomial tree method results. The following figure is the result.