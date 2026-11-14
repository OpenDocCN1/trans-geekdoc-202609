Similarly, we use $q_j^{(k)}$ and $q_j^{(0)}$ to denote the smoothed spam score after the attack depending on whether or not the $j^\text{th}$ token was used in the attack message. We will analyze the quantity

```
\(\Delta^{(k)}q_j \triangleq q_j^{(k)} - q_j^{(0)}.\)
```

One might reasonably expect this difference to always be non-negative, but here we show that there are some scenarios in which \(\Delta^{(k)}q_j < 0\). This unusual behavior is a direct result of the assumption made by SpamBayes that \(N^{(h)} = N^{(s)}\) rather than using a proper prior distribution. In fact, it can be shown that the usual spam model depicted in Figure 5.1(b) does not exhibit these irregularities. Below, we will show how SpamBayes’ assumption can lead to situations where \(\Delta^{(k)}q_j < 0\) but also that these irregularities only occur when there is *many* more spam messages than ham messages in the training dataset. By expanding \(\Delta^{(k)}q_j\) and rearranging terms, the difference can be expressed as:

```
\(\Delta^{(k)}q_j = \frac{s \cdot k}{(s + n_j + k)(s + n_j)} \left( P_j^{(s,k)} - x \right)
+ \frac{k \cdot N^{(h)} \cdot n_j}{(s + n_j) \left( N^{(h)} \cdot n_j^{(s)} + (N^{(s)} + k) n_j^{(h)} \right)} P_j^{(h,k)},\)
```

where \(P_j^{(h,k)} = 1 - P_j^{(s,k)}\) is the altered ham score of the \(j^\text{th}\) token. The difference can be rewritten as

```
\(\Delta^{(k)}q_j = \frac{k}{(s + n_j + k)(s + n_j)} \cdot \alpha_j\)

\(\alpha_j \triangleq s(1-x)
+P_j^{(h,k)} \cdot \frac{N^{(h)} \cdot n_j (n_j + k) + s \cdot N^{(h)} \cdot n_j^{(h)} - s (N^{(s)} + k) n_j^{(h)}}{N^{(h)} \cdot n_j^{(s)} + (N^{(s)} + k) n_j^{(h)}}.\)
```

The first factor \(\frac{k}{(s+n_j+k)(s+n_j)}\) in the above expression is non-negative so only \(\alpha_j\) can make \(\Delta^{(k)}q_j\) negative. From this, it is easy to show that \(N^{(s)} + k\) must be greater that \(N^{(h)}\) for \(\Delta^{(k)}q_j\) to be negative, but we demonstrate stronger conditions. Generally, we demonstrate that for \(\Delta^{(k)}q_j\) to be negative there must be a large disparity between the number of spams after the attack, \(N^{(s)} + k\), and the number of ham messages, \(N^{(h)}\). This reflects the effect of violating the implicit assumption made by SpamBayes that \(N^{(h)} = N^{(s)}\).

Expanding the expression for \(\alpha_j\), the following condition is necessary for \(\Delta^{(k)}q_j\) to be negative:

```
\(\frac{s \left( N^{(s)} + k \right) n_j^{(h)} x}{N^{(h)}} > \frac{s(1-x) \left( n_j^{(s)} + k \right)}{n_j^{(h)} \left( N^{(s)} + k \right)} \left[ \left( N^{(s)} + k \right) n_j^{(h)} + N^{(h)} \cdot n_j^{(s)} \right]
+ n_j (n_j + k) + s n_j^{(s)} (1-x) + s \cdot n_j^{(h)} .\)
```