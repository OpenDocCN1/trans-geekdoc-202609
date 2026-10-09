increase sales at all prices, they can change price sensitivity, and they can do both of these things in a brand-specific manner:

\( \mathbb{E}[\log(y) \mid \boldsymbol{x}] = \alpha_{b,\text{feat}} + \beta_{b,\text{feat}} \log(\text{price}). \tag{2.15} \)

This encodes a three-way interaction between price, brand, and feat.

```
> ojreg <- glm(log(sales) ~ log(price)*brand*feat, data=oj)
> coef(ojreg)
```

(Intercept) \quad 10.40657579 \quad \text{log(price)} \quad -2.77415436
column_2_row_3 = brandminute.maid \quad 0.04720317 \quad \text{brandtropicana} \quad 0.70794089
column_2_row_4 = feat \quad 1.09440665 \quad \text{log(price):brandminute.maid} \quad 0.78292310
column_2_row_5 = \text{log(price):brandtropicana} \quad 0.73579299 \quad \text{log(price):feat} \quad -0.47055331
column_2_row_6 = \text{brandminute.maid:feat} \quad 1.17294361 \quad \text{brandtropicana:feat} \quad 0.78525237
column_2_row_7 = \text{log(price):brandminute.maid:feat} \quad -1.10922376 \quad \text{log(price):brandtropicana:feat} \quad -0.98614093

The brand and ad specific elasticities are compiled in **Table 2.2**.

**TABLE 2.2:** Brand- and ad-dependent elasticities. Test your understanding of the regression equations by recovering these numbers from the **R** output.

|  | *Dominick's* | *Minute Maid* | *Tropicana* |
|---|---|---|---|
| Not Featured | $-2.8$ | $-2.0$ | $-2.0$ |
| Featured | $-3.2$ | $-3.6$ | $-3.5$ |

We see that being featured always leads to more price sensitivity. Minute Maid and Tropicana elasticities drop from -2 to below -3.5 with ads, while Dominick's drops from -2.8 to -3.2. Why does this happen? One possible explanation is that advertisement increases the population of consumers who