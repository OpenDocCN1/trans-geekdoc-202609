where,

```
$$p(x = x_H|D = \{x = x_H\})$$
$$= \frac{p(D = \{x = x_H\}|x = x_H)p(x = x_H)}{p(D = \{x = x_H\})}$$
$$= \frac{p(D = \{x = x_H\}|x = x_H)p(x = x_H)}{\sum_{i=L}^{H} p(D = \{x = x_H\}|x = x_i)p(x = x_i)}.$$\quad(2A.2)
```

Using the conjectured manager's strategy, we have

```
$$p(D = \{x = x_H\}|x = x_i) = p(s \ge s^*|x = x_i)$$
$$= \int_{s^*}^{1} f(s|x_i)ds \equiv 1 - F(s^*|x_i),$$\quad(2A.3)
```

where $F(.)$ is the cumulative distribution function of $\tilde s$ conditional on $x_i$.

Inserting equation (2A.3) into equation (2A.2), we have

```
$$p(x = x_i|D = \{x = x_H\}) = \frac{[1 - F(s^*|x_i)]p_i}{\sum_{i=L}^{H}[1 - F(s^*|x_i)]p_i}.$$\quad(2A.4)
```

Thus, we have

```
$$p(D = \{x = x_H\})$$
$$= x_H \times \frac{(1 - F(s^*|x_H))p_H}{(1 - F(s^*|x_H))p_H + (1 - F(s^*|x_L))p_L}$$
$$+ x_L \times \frac{(1 - F(s^*|x_L))p_L}{(1 - F(s^*|x_H))p_H + (1 - F(s^*|x_L))p_L}$$
$$= \frac{1 + r s^*}{2}x_H + \frac{1 - r s^*}{2}x_L.$$\quad(2A.5)
```

Similarly, we have

```
$$p(D = \{\emptyset\}) = \frac{1 - r + r s^*}{2}x_H + \frac{1 + r - r s^*}{2}x_L.$$\quad(2A.6)
```

Given this pricing schedule, the manager will adopt a threshold strategy if and only if the manager's expected benefit as a function of his disclosure choice exceeds the costs associated with a disclosure:

```
$$\alpha[P(D = \{x = x_H\}) - P(D = \{\emptyset\})]$$
$$\ge p(\text{the manager incurs a penalty }|s^*) * c.$$\quad(2A.7)
```