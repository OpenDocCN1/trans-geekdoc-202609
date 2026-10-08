Combining this and the fact that for all \(\varepsilon \in (0, 1]\) it holds that

```
log _ { 2 } ( A _ { \varepsilon } ) = d \log _ { 2 } \left( \frac { 3 L ( b - a ) } { \varepsilon } \right) = d \left( \log _ { 2 } ( \varepsilon ^ { - 1 } ) + \log _ { 2 } ( d ) + \log _ { 2 } ( 3 L ( b - a ) ) \right)
```

establishes that for all \(\varepsilon \in (0, 1]\) it holds that

```
\mathcal { H } ( \mathbf { F } _ { \varepsilon } ) \le \max \left\{ 0 , d \left( \log _ { 2 } ( \varepsilon ^ { - 1 } ) + \log _ { 2 } ( d ) + \log _ { 2 } ( 3 L ( b - a ) ) \right) + 1 \right\} .
```

Moreover, observe that (4.222) and (4.223) show that for all \(\varepsilon \in (0, 1]\) it holds that

```
\begin{array}{l} \mathcal { P } ( \mathbf { F } _ { \varepsilon } ) = \sum _ { i = 1 } ^ { \mathbf { L } _ { \varepsilon } } \mathbf { l } _ { i } ^ { ( \varepsilon ) } \left( \mathbf { l } _ { i - 1 } ^ { ( \varepsilon ) } + 1 \right) \\\[ 1em ] \begin{array}{l} \le \left( [ A _ { \varepsilon } ] + 1 \right) ( d + 1 ) + 3 \left\lfloor \frac { A _ { \varepsilon } } { 4 d } \right\rfloor \left( [ A _ { \varepsilon } ] + 2 \right) \\ + \max \left\{ [ A _ { \varepsilon } ] + 1 , 3 \left\lceil \frac { A _ { \varepsilon } } { 2 L \varepsilon ^ { - 1 } d } \right\rceil \right\} + 1 + \sum _ { i = 3 } ^ { \mathbf { L } _ { \varepsilon } - 1 } 3 \left\lceil \frac { A _ { \varepsilon } } { 2 ^ { i } d } \right\rceil \left( 3 \left\lceil \frac { A _ { \varepsilon } } { 2 ^ { i + 1 } d } \right\rceil + 1 \right) \\\[ 1em ] \le ( A _ { \varepsilon } + 1 ) ( d + 1 ) + 3 \left( \frac { A _ { \varepsilon } } { 4 } + 1 \right) ( A _ { \varepsilon } + 2 ) + 3 A _ { \varepsilon } + 4 + \sum _ { i = 3 } ^ { \mathbf { L } _ { \varepsilon } - 1 } 3 \left( \frac { A _ { \varepsilon } } { 2 ^ { i } } + 1 \right) \left( \frac { 3 A _ { \varepsilon } } { 2 ^ { i + 1 } } + 4 \right) . \end{array}
```

In addition, note that the fact that \( \forall x \in (0, \infty ) : \log _{2}(x)= \log _ { 2 } ( x / 2 ) + 1 \le x / 2 + 1 \) ensures that for all \(\varepsilon \in (0, 1]\) it holds that

```
\mathbf { L } _ { \varepsilon } \le 2 + \log _ { 2 } \left( \frac { A _ { \varepsilon } } { d } \right) \le 3 + \frac { A _ { \varepsilon } } { 2 d } \le 3 + \frac { A _ { \varepsilon } } { 2 } .
```

This implies that for all \(\varepsilon \in (0, 1]\) it holds that

```
\begin{array}{l} \sum _ { i = 3 } ^ { \mathbf { L } _ { \varepsilon } - 1 } 3 \left( \frac { A _ { \varepsilon } } { 2 ^ { i } } + 1 \right) \left( \frac { 3 A _ { \varepsilon } } { 2 ^ { i - 1 } } + 4 \right) \\ \begin{array}{l} \le 9 [ A _ { \varepsilon } ] ^ { 2 } \left[ \sum _ { i = 3 } ^ { \mathbf { L } _ { \varepsilon } - 1 } 2 ^ { 1 - 2 i } \right] + 1 2 A _ { \varepsilon } \left[ \sum _ { i = 3 } ^ { \mathbf { L } _ { \varepsilon } - 1 } 2 ^ { - i } \right] + 9 A _ { \varepsilon } \left[ \sum _ { i = 3 } ^ { \mathbf { L } _ { \varepsilon } - 1 } 2 ^ { 1 - i } \right] + 1 2 ( \mathbf { L } _ { \varepsilon } - 3 ) \\ \le \frac { 9 [ A _ { \varepsilon } ] ^ { 2 } } { 8 } \left[ \sum _ { i = 1 } ^ { \infty } 4 ^ { - i } \right] + 3 A _ { \varepsilon } \left[ \sum _ { i = 1 } ^ { \infty } 2 ^ { - i } \right] + \frac { 9 A _ { \varepsilon } } { 2 } \left[ \sum _ { i = 1 } ^ { \infty } 2 ^ { - i } \right] + 6 A _ { \varepsilon } \\ = \frac { 3 } { 8 } [ A _ { \varepsilon } ] ^ { 2 } + 3 A _ { \varepsilon } + \frac { 9 } { 2 } A _ { \varepsilon } + 6 A _ { \varepsilon } = \frac { 3 } { 8 } [ A _ { \varepsilon } ] ^ { 2 } + \frac { 2 7 } { 2 } A _ { \varepsilon } . \end{array}
```

This and (4.228) demonstrate that for all \(\varepsilon \in (0, 1]\) it holds that

```
\begin{array}{l} \mathcal { P } ( \mathbf { F } _ { \varepsilon } ) \le \left( \frac { 3 } { 4 } + \frac { 3 } { 4 } \right) ( A _ { \varepsilon } ) ^ { 2 } + \left( d + 1 + \frac { 9 } { 2 } + 3 + \frac { 2 7 } { 2 } \right) A _ { \varepsilon } + d + 1 + 6 + 4 \\ = \frac { 9 } { 8 } ( A _ { \varepsilon } ) ^ { 2 } + ( d + 2 2 ) A _ { \varepsilon } + d + 1 1 . \end{array}
```