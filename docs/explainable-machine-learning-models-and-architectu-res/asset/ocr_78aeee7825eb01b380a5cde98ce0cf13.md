Where, \( f_o \) is the observed data from the histogram and \( fest \) is the estimated value from BM-MFO

```
\( fest = w1\left(\frac{k1}{c1}\right)\left(\frac{v}{c1}\right)^{k1-1} \exp\left(-\left(\frac{v}{c1}\right)^{k1}\right) \)
\( +w2\left(\frac{k2}{c2}\right)\left(\frac{v}{c2}\right)^{k2-1} \exp\left(-\left(\frac{v}{c2}\right)^{k2}\right) \) (11.12)
```

The MFO Pseudocode algorithm with program logic is derived below and the flow chart for the MFO algorithm is described in Figure 11.1.

```
Update flame no using Equation
OM = Fitness Function(M);
if iteration == 1
    F = sort(M);
    OF = sort ( OM);
else
    F = sort ( M_{t-1}, M_t);
    OF = sort ( M_{t-1}, M_t);
end
for i = 1: n
    for j = 1: d
        Update r and t
        Calculate D using Eq with respect to the corresponding moth
        Update M (i, j) using Eqns. with respect to the corresponding moth
    end
end
```