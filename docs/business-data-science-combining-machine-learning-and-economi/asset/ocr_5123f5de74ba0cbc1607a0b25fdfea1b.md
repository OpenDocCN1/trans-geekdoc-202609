$$\begin{gathered}\log q_{it} = \log p_{it}\gamma + {\boldsymbol{x}_{it}}^{\prime}\boldsymbol{\beta} + \varepsilon_{it}, \\ \log p_{it} = {\boldsymbol{x}_{it}}^{\prime}\boldsymbol{\tau} + v_{it},\end{gathered}\tag{6.16}$$

with $\varepsilon_{it}\mid p_{it}, x_{it}=0$ and $v_{it}\mid x_{it}=0$ as in Equation 6.2. Here, $x_{it}$ is the set of demand signals that were known to the price-setter. This model is nice because, recalling from Chapter 2, in a log-log model $\gamma$ is directly interpretable as the percentage change in $q$ per $1\%$ change in $p$—that is, $\gamma$ is directly interpretable as the price elasticity of demand (hence the choice of notation in Equation 6.14). Moreover, as mentioned earlier, it is plausible for firm-side analysts to know all of the demand signals, $x_{it}$. The consequence of this is that $\varepsilon \perp v$, as required for conditional ignorability. The model defined in Equation 6.16 is then an instance of the LTE system from Equation 6.2, and it can be analyzed using the methods of this chapter.

As an example, we will consider data on sales of beer between 1989 and 1994 at Dominick’s stores in the Chicagoland area.16 For each beer unique product code (UPC), we have weekly total unit sales $^{(MOVE)}$ and average prices across 63 different stores.

```
```\n> load("dominicks-beer.rda")\n> head(wber)\n```
```

|  |  | STORE | UPC | WEEK | PRICE | MOVE |
|  |---|---|---|---|---|---|
| 1 | 8 | 1820000008 | 91 | 1.59 | 5 |
| 2 | 8 | 1820000008 | 92 | 1.59 | 7 |
| 3 | 8 | 1820000008 | 93 | 1.59 | 9 |
| 4 | 8 | 1820000008 | 94 | 1.59 | 4 |
| 5 | 8 | 1820000008 | 95 | 1.59 | 2 |
| 6 | 8 | 1820000008 | 96 | 1.59 | 10 |

For the UPCs, we have available their size in beer volume $^{(OZ,}$ for fluid ounces$)$ and a short text description.