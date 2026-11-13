| 8 | 29.96 | 7.49274e+06 | 35 | 643.528 | 987.419 | 9.06s |
| 9 | 35.43 | 2.61246e+07 | 37 | 635.438 | 979.855 | 9.16s |
| 10 | 39.70 | 184599 | 47 | 632.776 | 968.959 | 8.46s |
| 11 | 43.96 | 103712 | 63 | 622.238 | 1080.15 | 7.73s |
| 12 | 49.71 | 226647 | 85 | 626.494 | 1037.15 | 7.30s |
| 13 | 53.44 | 381808 | 21 | 625.923 | 1092.07 | 6.49s |
| 14 | 62.79 | 1.63537e+10 | 73 | 631.003 | 743.992 | 5.95s |
| 15 | 69.80 | 8.3692e+07 | 85 | 615.331 | 1026.55 | 5.10s |
| 16 | 79.79 | 125911 | 69 | 608.597 | 1061.46 | 4.88s |
| 17 | 89.14 | 2.29499e+08 | 109 | 587.532 | 1112.72 | 3.07s |
| 18 | 93.87 | 127462 | 75 | 590.906 | 1004.49 | 1.59s |
| 19 | 101.48 | 267719 | 99 | 594.219 | 872.978 | 0.00s |

```
score=est_gp.score(x_test,y_test)
print ('R2:',z)
```

# #Model score

R2: 0.89190545618484

```
#The equation that the symbolic regressor was able to generate,
#but needs alot of simplificaation which will be provided in
#the next couple codes
print (est_gp._program)
add(add(div(add(mul(X2, X4), div(X2, 0.920)), X2), X0), add(div(sub(add(X0,
sub(add(X0, X0), sub(div(div(sub(add(X0, sub(add (X0, X1), sub(div(sub(X3, X4),
sub(add(div(sub(X2, X0), sub(X2, X0)), X0), add(X0, add(X0, add(sub(mul(0.095, X2),
X0), X0))))), -0.911))), sub(mul(0.095, X2), -0.911)), div(0.920, X1)), mul(0.095,
add(X0, sub(add(X0, div(X0, X2)), sub(div(add(mul(0.095, X2), X2), mul(0.095, X2)),
-0.911)))), -0.911)), sub(mul(0.095, X2), -0.911)), div(0.920, X1)), div(X0, X2)))
```

```
#Simplify the above equation
converter = {
'add': lambda x, y : x + y,
'sub': lambda x, y : x - y,
'mul': lambda x, y : x*y,
'div': lambda x, y : x/y,
'sqrt': lambda x : x**0.5,
'log': lambda x : log(x),
'abs': lambda x : abs(x),
'neg': lambda x : -x,
'inv': lambda x : 1/x,
'max': lambda x, y : max(x, y),
'min': lambda x, y : min(x, y),
'sin': lambda x : sin(x),
'cos': lambda x : cos(x),
'pow': lambda x, y : x**y,
}
```

```
from sympy import *
N = sympify(str(est_gp._program), locals=converter)
```

N = X_{0} + \frac{X_{0}}{X_{2}} + 1.0869X_{1} \left( 3X_{0} - \frac{1.0869X_{1} \left( 2X_{0} + X_{1} - 0.095X_{2} - \frac{X_{3} - X_{4}}{-X_{0} - 0.095X_{2} + 1} - 1.822 \right)}{0.19X_{0} + \frac{0.095X_{0}}{X_{2}} - 1.1815} - 0.095X_{2} - 1.822 \right) + \frac{X_{2}X_{4} + 1.0869X_{2}}{X_{2}}

```
save.N
```