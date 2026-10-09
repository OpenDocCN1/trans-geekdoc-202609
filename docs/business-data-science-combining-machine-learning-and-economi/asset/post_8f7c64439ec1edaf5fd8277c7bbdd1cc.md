

increase sales at all prices, they can change price sensitivity, and they can do both of these things in a brand-specific manner:

\[ \mathbb{E}[\log(y) \mid \boldsymbol{x}] = \alpha_{b,\text{feat}} + \beta_{b,\text{feat}} \log(\text{price}). \tag{2.15} \]

This encodes a three-way interaction between price, brand, and feat.

```
> ojreg <- glm(log(sales) ~ log(price)*brand*feat, data=oj)
> coef(ojreg)
```

| Term | Coefficient |
| :--- | :--- |
| (Intercept) | 10.40657579 |
| log(price) | -2.77415436 |
| brandminute.maid | 0.04720317 |
| brandtropicana | 0.70794089 |
| feat | 1.09440665 |
| log(price):brandminute.maid | 0.78292310 |
| log(price):brandtropicana | 0.73579299 |
| log(price):feat | -0.47055331 |
| brandminute.maid:feat | 1.17294361 |
| brandtropicana:feat | 0.78525237 |
| log(price):brandminute.maid:feat | -1.10922376 |
| log(price):brandtropicana:feat | -0.98614093 |

The brand and ad specific elasticities are compiled in **Table 2.2**.

**TABLE 2.2:** Brand- and ad-dependent elasticities. Test your understanding of the regression equations by recovering these numbers from the **R** output.

| | *Dominick's* | *Minute Maid* | *Tropicana* |
|---|---|---|---|
| Not Featured | $-2.8$ | $-2.0$ | $-2.0$ |
| Featured | $-3.2$ | $-3.6$ | $-3.5$ |

We see that being featured always leads to more price sensitivity. Minute Maid and Tropicana elasticities drop from -2 to below -3.5 with ads, while Dominick's drops from -2.8 to -3.2. Why does this happen? One possible explanation is that advertisement increases the population of consumers who are considering your brand. In particular, it can increase your market beyond brand loyalists, to include people who will be more price sensitive than those who reflexively buy your orange juice every week. Indeed, if you observe increased price sensitivity, it can be an indicator that your marketing efforts are expanding your consumer base. This is why Marketing 101 dictates that ad campaigns should usually be accompanied by price cuts. There is also an alternative explanation. Since the featured products are often also discounted, it could be that the demand curve is nonlinear—at lower price points the average consumer is more price sensitive. The truth is probably a combination of these effects.

Finally, notice that in Table 2.1 Minute Maid had a price elasticity similar to that of Dominick’s—it behaved like a budget product. However, in Table 2.2, we see that Minute Maid and Tropicana have nearly identical elasticities and that both are different from Dominick’s. What happened?

The answer is that the overly simple model in Equation 2.14 led to a confounding between advertisement and brand effects. Figure 2.7 shows that Minute Maid was featured more often than Tropicana. Since being featured leads to more price sensitivity, this leads Minute Maid to artificially appear more price sensitive when we don’t account for the ad’s effect. The model in Equation 2.15 corrects this by including feat in the regression. This phenomenon, where variable effects can get confounded if you don’t control for them correctly, will play an important role in the later discussions of causal and structural inference.

![](img/315929ad4bddd26368466d02e06e2385_81_0.png)

**FIGURE 2.7:** A mosaic plot of the amount of advertisement by brand.

## LOGISTIC REGRESSION

Linear regression is just one instance of the linear modeling framework. Another technique (perhaps even more common in practice) is *logistic regression*. This strategy is used for modeling *binary response*: a *y* that is either 0 or 1 (true or false).

Binary responses arise from a number of prediction targets:

- Will this person pay their bills or default?
- Is this a thumbs-up or thumbs-down review?
- Will the Edmonton Oilers win or lose this game?
- Is the writer a Republican or Democrat?

Even when the response of interest is not binary (e.g., revenue), it will sometimes be that your decision-relevant information is binary (e.g., profit versus loss) and it is simplest to think in these terms.

Recall the general linear model specification: $\mathbb{E}[y|x]=f(x'\beta)$. When the response *y* is 0 or 1, the conditional mean becomes

$\mathbb{E}[y|x]=\mathrm{p}(y=1|x)\times 1+\mathrm{p}(y=0|x)\times 0=\mathrm{p}(y=1|x)$.

Therefore, the expectation you're modeling is a *probability*. This implies that you need to choose the *link function* $f(x'\beta)$ to give values between zero and one:

$\mathrm{p}(y=1|x)=f(\beta_0+\beta_1x_1\dots+\beta_px_p)$.

Logistic regression uses a *logit* link function:

$\mathrm{p}(y=1|\mathbf{x})=\frac{e^{x'\beta}}{1+e^{x'\beta}}=\frac{\mathrm{exp}[\beta_0+\beta_1x_1\dots+\beta_px_d]}{1+\mathrm{exp}[\beta_0+\beta_1x_1\dots+\beta_px_d]}$.

See **Figure 2.8** for a picture of the logit function. To see how this link works, consider extreme values for $x'\beta$. At large negative values, $f(-\infty)=0/(1+0)=0$ and $y=1$ has zero probability. At large positive values, $f(\infty)=\infty/(\infty+1)=1$ and $y=1$ is guaranteed. Thus, the logit link maps from the "real line" of numbers to the [0, 1] space of probabilities.

![](img/315929ad4bddd26368466d02e06e2385_83_0.png)

**FIGURE 2.8:** A logistic link function.

To interpret the $\beta$ coefficients, writing $\mathrm{p} = \mathrm{p}(y = 1 \mid x)$ and a little algebra shows that

$$ \log \bigg[ \frac { p } { 1 - p } \bigg] = \beta _ { 0 } + \beta _ { 1 } x _ { 1 } + . . . + \beta _ { p } x _ { p } . $$

Thus, logistic regression is a linear model for log odds. The odds of an event are the probability that it happens over the probability that it doesn’t. For example, if an event has a 1/4 probability, then its odds are “one in three,” or 1/3. You should get used to is now binary and you add the argument `family='binomial'`. The response variable can take a number of forms: numeric ($0/1$), logical (**TRUE**/**FALSE**), factor (e.g., *win/lose*), or even a two-column binary matrix. In the email data, we have $y = 1$ for spam and $y = 0$ for important emails.

```r
> spammy <- glm(spam ~ ., data=email, family='binomial')
```

Note that the formula “$y \sim .$” is shorthand for “regress $y$ on to all variables in the data.” Take a look at one of the large positive coefficients in our fit:

```r
> coef(spammy)["word_free"]
 word_free
 1.542706
> exp(1.542)
[1] 4.673929
```

Thus, the *odds* that an email is spam increase almost 5 times if that email contains the word *free*. On the other hand, we see next that if the email contains the word *george*, the odds of it being spam drop by a factor larger than 300.

```r
> coef(spammy)["word_george"]
 word_george
 -5.779841
> 1/exp(-5.78)
[1] 323.7592
```

This is an old dataset collected from the inbox of a guy named George. Spammers were not very sophisticated in the 1990s, so emails containing your name were most likely not spam.

When you run the spam regression, R warns that `fitted probabilities numerically 0 or 1 occurred`. You need not worry: this just says that the regression is able to fit some data points *exactly*—for example, a spam email
