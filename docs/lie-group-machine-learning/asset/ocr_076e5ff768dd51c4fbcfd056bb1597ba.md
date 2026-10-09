# **Tab. 15.4**: Sample data set.

| Day | Outlook | Temperature | Humidity | Wind | PlayTennis |
| --- | --- | --- | --- | --- | --- |
| D1 | Sunny | Hot | High | Weak | No |
| D2 | Sunny | Hot | High | Strong | No |
| D3 | Overcast | Hot | High | Weak | Yes |
| D4 | Rain | Mild | High | Weak | Yes |
| D5 | Rain | Cool | Normal | Weak | Yes |
| D6 | Rain | Cool | Normal | Strong | No |
| D7 | Overcast | Cool | Normal | Strong | Yes |
| D8 | Sunny | Mild | High | Weak | No |
| D9 | Sunny | Cool | Normal | Weak | Yes |
| D10 | Rain | Mild | Normal | Weak | Yes |
| D11 | Sunny | Mild | Normal | Strong | Yes |
| D12 | Overcast | Mild | High | Strong | Yes |
| D13 | Overcast | Hot | Normal | Weak | Yes |
| D14 | Rain | Mild | High | Strong | No |

All attribute set objects $Q$ can be defined as the set of data in Table 15.4 above, and the elements in object $E$ can be obtained from the entropy morphism: $g_{1} =$ Entropy $(S)=\sum_{i=1}^{c}-p_{i} \log _{2} p_{i}: Q \rightarrow E$

```
$E>\left\{\begin{aligned} E(& PT)=0.940,\ E(S_{weak} | wind)=0.811,\ E(S_{strong} | wind)=1.00,\ E(wind)=0.892, \\ E(& Sunny | out)=0.971,\ E(Overcast | out)=0,\ E(Rain | out)=0.971,\ E(out)=0.693, \\ E(& S_{cool} | temp)=0.811,\ E(S_{mild} | temp)=0.918,\ E(S_{hot} | temp)=1.00,\ E(temp)=0.911, \\ E(& S_{high} | humidity)=0.985,\ E(S_{normal} | humidity)=0.591,\ E(humidity)=0.789 \end{aligned}\right.$
```

The following are obtained by information gain state projection: $g_{2} = \text{Gain}(S, A) =$ Entropy $(S)-\sum_{v \in \text{Value}(A)}|S_{v}|/|S \cdot$ Entropy$(S_{v}): E \rightarrow G, G>\{G(S, out) = 0.246,$ $(S, temp) = 0.029, G(S, humidity) = 0.151, G(S, wind) = 0.048\}; h = \text{max}\sum_{i,j}$ Gain$(X_{i}, Q_{ij}): G \rightarrow M$. Then, we get the root node $M>\{$ out (sunny, overcast, rain).$

Reselect the three attribute entries in the object $Q$, respectively, choose out(sunny) and out(rain) as a branch, repeat the process to get the other branches and leaf nodes, and get the final decision tree, as shown in Figure 15.8.

The sample data in Table 15.4 is randomly changed so that the value of the property item assumes a random missing state, and the newly generated data set is used as the test set. Now take the eighth data, e.g., the outlook attribute is missing; we can use it to examine the classification of data.

Test sample data property object $Q>\emptyset$, Mild, High, Weak, ?]. The prior probabilities and other probability objects of the missing items obtained from Tables 15.4 and Figure 15.8 are as follows:

```
$P>\left\{\begin{array}{l} p(Sunny) = \frac{1}{3},\ p(Overcast) = \frac{1}{3},\ p(Rain) = \frac{1}{3}, \\ p(N | Sunny) = 0.60,\ p(N | Overcast) = 0,\ p(N | Rain) = 0.40, \\ p(Y | Sunny) = 0.40,\ p(Y | Overcast) = 1.0,\ p(Y | Rain) = 0.60 \end{array}\right.$
```