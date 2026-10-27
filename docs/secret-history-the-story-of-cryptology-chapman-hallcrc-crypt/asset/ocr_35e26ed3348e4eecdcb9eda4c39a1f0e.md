A quick definition: If we start with a permutation A and use another permutation P to form the product P^{-1}AP, we say that A has been transformed by the action of P.

Now take the six equations above and transform both sides by the action of P, P², P³, P⁴, P⁵, and P⁶, respectively. We label the results with new letters for convenience:

```
U = P^{-1}H^{-1}S^{-1}ASHP          U = NP^{-1}QPN^{-1}
V = P^{-2}H^{-1}S^{-1}BSHP²         V = NP^{-2}QP²N^{-1}
W = P^{-3}H^{-1}S^{-1}CSHP³         W = NP^{-3}QP³N^{-1}
X = P^{-4}H^{-1}S^{-1}DSHP⁴         X = NP^{-4}QP⁴N^{-1}
Y = P^{-5}H^{-1}S^{-1}ESHP⁵         Y = NP^{-5}QP⁵N^{-1}
Z = P^{-6}H^{-1}S^{-1}FSHP⁶         Z = NP^{-6}QP⁶N^{-1}
```

*Note: The left-hand sides are known.*

We now use the second column of equations to take some products.

```
UV = (NP^{-1}QPN^{-1})(NP^{-2}QP²N^{-1})
VW = (NP^{-2}QP²N^{-1})(NP^{-3}QP³N^{-1})
WX = (NP^{-3}QP³N^{-1})(NP^{-4}QP⁴N^{-1})
XY = (NP^{-4}QP⁴N^{-1})(NP^{-5}QP⁵N^{-1})
YZ = (NP^{-5}QP⁵N^{-1})(NP^{-6}QP⁶N^{-1})
```

Removing the parenthesis, the N^{-1}N in the middle drops out of each equation. We then combine the powers of P that appear next to one another and insert a new pair of parenthesis (to stress a portion the equations all share) and get the following.

```
UV = NP^{-1}(QP^{-1}QP)PN^{-1}
VW = NP^{-2}(QP^{-1}QP)P²N^{-1}
WX = NP^{-3}(QP^{-1}QP)P³N^{-1}
XY = NP^{-4}(QP^{-1}QP)P⁴N^{-1}
YZ = NP^{-5}(QP^{-1}QP)P⁵N^{-1}
```

Now take the first four equations above and transform both sides of each by the action of NPN^{-1}:

```
NP^{-1}N^{-1}(UV)NPN^{-1} = NP^{-1}N^{-1}NP^{-1}(QP^{-1}QP)PN^{-1}NPN^{-1}
NP^{-1}N^{-1}(VW)NPN^{-1} = NP^{-1}N^{-1}NP^{-2}(QP^{-1}QP)P²N^{-1}NPN^{-1}
NP^{-1}N^{-1}(WX)NPN^{-1} = NP^{-1}N^{-1}NP^{-3}(QP^{-1}QP)P³N^{-1}NPN^{-1}
NP^{-1}N^{-1}(XY)NPN^{-1} = NP^{-1}N^{-1}NP^{-4}(QP^{-1}QP)P⁴N^{-1}NPN^{-1}
```