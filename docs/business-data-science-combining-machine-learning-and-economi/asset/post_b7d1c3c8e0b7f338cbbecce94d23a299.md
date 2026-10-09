
![](img/315929ad4bddd26368466d02e06e2385_337_0.png)

**FIGURE 8.6:** We8there overall rating against topic scores $\omega_{1i}$ and $\omega_{2i}.$

These relationships suggest a topic regression strategy for predicting review rating from text content. The scheme for topic regression works the same as the PCR in Algorithm 19: fit the topics and then use them as inputs to a lasso with AICc or CV selection.

```r
> stars <- we8thereRatings[,"Overall"]
> tpcreg <- gamlr(tpcs$omega, stars, lmr=1e-3)
```

The AICc selects a model that loads on nine of ten topics.[1] We can multiply the coefficients by 0.1 to see what happens to the expected overall star rating from a 0.1 increase in $\omega_{ki}$.

```r
> round(coef(tpcreg)[-1,]*.1, 1)
  1    2    3    4    5    6    7    8    9    10
0.1  -0.4  0.0  0.0  0.0  0.1  0.1  0.0  -0.1  -0.1
```

So, for example, you drop an expected $-0.4$ star when a review has an extra 10% of its content coming from topic 2 (the waiting topic). As anyone who has worked in restaurants can tell you, the fastest way to unhappy (American) customers is to make them wait.

We can also compare the topic regression to a lasso where the overall rating is regressed onto raw token counts. **Figure 8.7** shows results of OOS validation for each approach, and we see that the topic regression outperforms the token regression. There is a useful low-dimensional factor structure in the review text, and this factor structure is directly relevant to the response of interest: overall quality. In this case, we gain estimation efficiency by doing unsupervised dimension reduction before running the lasso.

![](img/315929ad4bddd26368466d02e06e2385_338_0.png)

**FIGURE 8.7:** Comparison of topic regression and a lasso onto the raw token counts $x_{ij}.$

# MULTINOMIAL INVERSE REGRESSION (MNIR)

Between text regression and topic modeling, you are now equipped to use text to predict some $y$ or to build models for latent unobserved factors in text. Another task that comes up often in social science is understanding how text connects to a *set* of related covariates. For example, you might want to connect the we8there reviews simultaneously to all five aspect ratings, allowing you to determine which content is predictive of ratings on, say, atmosphere *separate* from food or service.

For such tasks, we can turn to multinomial inverse regression (MNIR)$^{12}$ to link the text with observable covariates through a multinomial distribution. The “inverse” in MNIR comes from the fact that, while text regression usually fits a single document attribute as a function of word counts, we are inverting the process by regressing the counts on any number of document attributes. Given document attributes $v_{i}$ (author characteristics, date, beliefs, sentiment, etc.), MNIR follows the familiar generalized linear model framework. Each document $x_{i}$ is modeled as arising from a multinomial with a logit link onto a linear function of $v_{i}$:

$$\boldsymbol{x}_{i}\sim \operatorname{MN}(\boldsymbol{q}_{i}, m_{i})\quad \text{with}\quad q_{ij}=\frac{\exp[\alpha_{j}+\boldsymbol{v}_{i}^{\prime}\boldsymbol{\varphi}_{j}]}{\sum_{l=1}^{p}\exp[\alpha_{l}+\boldsymbol{v}_{i}^{\prime}\boldsymbol{\varphi}_{l}]}\quad\quad\quad(8.4)$$

This is the same as the multinomial logistic regression introduced in Chapter 4. Now, the number of outcome categories is the number of tokens in our text vocabulary. This can be viewed as a natural extension of topic modeling: we are keeping the multinomial model for token counts but replacing unknown topics with known attributes.

Looking again at the we8there data, we can set $v_{i}$ as the vector of five aspect ratings: overall, atmosphere, value, food, and service. The multinomial response will be the vector of word counts for each document, $x_{i}$, which implies 2640 outcome categories. This is far too many dimensions for most multinomial logistic regression algorithms (e.g., `glmnet` will hang and then choke). Fortunately, as discussed in Chapter 4, the `distrm` package is specifically designed to be efficient for these types of massive-response multinomials. It uses a Poisson distribution representation of the multinomial to distribute computation for each vocabulary element across multiple processors.

```text
> cl <- makeCluster(detectCores())
> ## small lambda for a fast example
> fits <- dmr(cl, we8thereRatings,
+          we8thereCounts, bins=5)
```

Figure 8.8 shows the lasso regularization paths for a selection of terms. Some terms (chicken wing and ate here) are found to be unrelated to review rating, while the others can load positively on some ratings and negatively on other ratings. For example, `terribl servic` (stemmed from *terrible service*) is negatively related to all aspects except food, with which it has a strong positive relationship.

![](img/315929ad4bddd26368466d02e06e2385_340_0.png)

**FIGURE 8.8:** Lasso paths for a selection of the terms from the we8there reviews.

```
> B[-1, "terribl servic"]

       Food  Service  Value  Atmosphere  Overall
       0.312  -1.489  -0.639  -0.333     0.000
```

As in any multivariate regression, these are a *partial effects*: they represent the influence of one attribute after controlling for the other attributes. In the case of `terribl servic`, this term is expected to occur more often if the food rating is *high relative to what you'd expect given the other ratings*. That is, even though `terribl servic` has a negative *marginal* association with the food rating (count-to-rating correlation is $-0.1$), it has a positive MNIR loading for the food rating because diners will highlight it in a generally negative review if the food was not that bad (just, for example, overpriced and slow).

This is the power of MNIR—you can control for confounds in the same way that you do in a standard regression analysis. It allocates language among multiple observable influences, similar to how topic models attempt to allocate language across multiple unobserved topics. **Figure 8.9** shows top loadings by the size of their $|\rho_{kj}|$ for each aspect *k*. There is a clear sorting of terms to the appropriate aspect rating, and the overall ratings are related to summaries of the experience: you “plan to return” if the experience was positive and ended up “speaking to the manager” if it was overall negative.

| **Overall** | **Food** | **Service** | **Value** | **Atmosphere** |
| :----------------- | :--------------------- | :------------------- | :---------------- | :------------------ |
| plan.return | again.again | cozzi.atmospher | big.portion | walk.down |
| feel.welcom | mouth.water | servic.terribl | around.world | great.bar |
| best.meal | francisco.bay | servic.impecp | chicken.pork | atmospher.wonder |
| select.includ | high.recommend | attent.staff | perfect.place | dark.wood |
| finest.restaur | cannot.wait | time.favorit | place.visit | food.superb |
| steak.chicken | best.servic | servic.outstand | mahi.mahi | atmospher.great |
| love.restaur | kept.secret | servic.horribl | very.reason | always.go |
| ask.waitress | food.poison | dessert.great | barb.back | bleu.chees |
| good.work | outstand.servic | terribl.servic | low.price | realli.cool |
| can.enough | far.best | never.came | peanut.sauce | recommend.everyon |
| after.left | food.awesom | expert.wonder | wonder.time | great.atmospher |
| come.close | best.kept | time.took | garlic.sauce | wonder.restaur |
| open.lunch | everyth.menu | waitress.come | great.can | love.atmospher |
| warm.friend | excel.price | servic.except | absol.best | bar.just |
| spoke.manag | keep.come | final.came | place.best | expos.brick |
| definit.recommend | hot.fresh | new.favorit | year.alway | back.drink |
| expect.wait | best.mexican | servic.awesom | over.dish | fri.noth |
| great.time | best.sushi | server.mimut | dish.well | great.view |
| chicken.beef | pizza.best | best.dine | few.place | chicken.good |
| room.dessert | food.fabul | veri.rude | authent.mexican | bar.great |
| price.great | melt.mouth | ppl.veri | wether.com | person.favori |
| seafood.restaur | each.dish | poor.servic | espec.good | great.decor |
| friend.atmospher | absol.wonder | ask.check | like.sit | french.dip |
| sent.back | foie.gras | real.treat | open.untill | pub.food |
| ll.defini | menu.chang | never.got | great.too | coconut.shrimp |
| anyon.look | food.blanc | non.exist | open.daili | go.up |
| most.popular | noth.fanci | flag.down | best.valu | servic.fantast |
| order.wrong | back.time | tabl.ask | just.great | gas.station |
| delici.food | food.excel | least.mimut | fri.littl | pork.loin |
| fresh.seafood | worth.trip | won.disappoint | portion.huge | place.friend |
| | | | - negative | -- positive |

**FIGURE 8.9:** Big absolute loadings by aspect rating in the we8there MNIR.

There is a connection between MNIR and factorization. Recall that, after the PC factor model, you obtain the PC scores by projecting the raw $x_{i}$ through the loadings $\rho_{k}$. The same operation is used in PLS to map from marginal regressions to each PLS direction. A similar logic applies to MNIR: if you want to get a *score* for the degree to which text $x_{i}$ is associated with document attribute $k$, you can obtain the MNIR projection $z_{ik} = x^{T}\rho_{k} = \sum_{j} x_{ij}\rho_{jk}$. These scores will contain *all of the information in* $x_{i}$ *that is relevant to* $v_{ik}$. If you know $z_{ik}$, then there is nothing more that $x_{i}$ can tell you about aspect $k$. **Figure 8.10** shows scores against true values for overall rating; it is clear that $z_{overall}$ is rich with information about $Overall$.
