
FIGURE 8.10: MNIR projection $z_{overall}$ against true overall review rating.

These MNIR projections (also called sufficient reduction [SR] projections) are especially useful for sorting documents according to the various attributes. Taking an example from Taddy [2015b], we consider reviews on Yelp.com for a variety of places (restaurants, hotels, landmarks). In addition to the reviewer’s star rating, these reviews also come accompanied with votes from other Yelp users on the quality of the review itself. On Yelp.com you can give a review a vote as funny, useful, or cool. You can run MNIR onto these vote counts as well as a list of other variables that you would like to control for, such as the category of the review subject (e.g., restaurant, bowling alley, or both) and how long this subject has been up on Yelp.

The results illustrate the usefulness of MNIR projections based on partial correlations. Sorting reviews by vote alone is not especially informative because the reviews that get a lot of votes tend to be those that are old or associated with popular subjects. For example, the funniest review by votes in the sample is a nonhumorous review of the Casa Grande national monument in Coolidge, Arizona; this is also the most useful and coolest review by votes.

In contrast, the review with highest MNIR projection $z_{funny}$ is an open letter to the restaurant that is designed to be humorous:

> Dear La Piazza al Forno: you need to talk. I don’t quite know how to say this so I’m just going to come out with it. I’ve been seeing someone else. How long? About a year now. Am I in love?
>
> *Yes. Was it you? It was. The day you decided to remove hoagies from the lunch menu, about a year ago, I’m sorry, but it really was you...and not me. Hey...wait...put down that pizza peel...try to stay calm...please? [Olive oil container whizzing past head] Please! Stop throwing shit at me...everyone breaks up on social media these days...or haven’t you heard? Wow, what a Bitch!*

You can also normalize the SR projections by the length of review, for example, reporting $z_ik / m_i$. On this scale, the funniest review is *Holy Mother of God*, and the most useful review is *Ask for Nick!*.

Overall, MNIR is useful for sorting through a large number of related influences on text and for categorizing texts according to these factors. It is a complement to text regression and topic modeling. In full-scale text analysis applications, you will find yourself combining all of these tools as appropriate. For example, in Taddy [2013a], I tracked political sentiment on Twitter about candidates in the 2012 Republican presidential primaries (plus sentiment about Obama, the incumbent president). This work uses topic modeling to factorize a massive bank of unlabeled text; I then used this factor representation to guide the selection of tweets for labeling by human readers. Once I accumulated the labeled data, I used MNIR to model tweet content as a function of both generic sentiment (happy versus sad) and sentiment about specific politicians (e.g., support for Romney is not the same as being positive in general). The resulting factors are used as input to a text regression, along with some raw token counts, to train a model that can track subject-specific sentiment on Twitter. The results are shown in **Figure 8.11**.

FIGURE 8.11: Sentiment about politicians in Twitter traffic during the 2012 Republican presidential primaries.

Before leaving text behind for a bit, here is an important reminder that is relevant to any novice text-miner: when you introduce text data, don’t forget all that you already know. If you get access to a Twitter feed, don’t just naively try to use this data to predict, for example, stock prices. Instead, use the text as a complement to the existing trading system—use it to predict residuals. Text information is best as part of a larger system. Use it to fill in the pieces you don’t know and to automate analysis that is expensive and time-consuming.

## COLLABORATIVE FILTERING

At the beginning of this chapter, we were clear that the bag-of-words representation is a brutal oversimplification of language. However, we’ve seen that this simple framework can facilitate a number of powerful text analysis frameworks. The simplicity of the bag-of-words representation leads us to treat text as a series of generic counts. This implies that the tools of text analysis we’ve covered in this chapter should apply beyond text to any other setting that is centered on count data.

One important case is that of collaborative filtering: the task of predicting a person’s future choices from their and others’ past choices. A well-known example is the Netflix problem: Given past movie choices, what should be recommended for you to watch tonight? The data here is essentially the same as what you get for text: each user has a vector $x_i$ containing 0/1 information for what they have watched. We’d like to, for example, find underlying genres that collect movies watched by the same people.

I don’t know what Netflix uses as a collaborative filtering scheme, and I imagine that it depends upon movie context (e.g., reviews, actors, content) as well as past transaction data. But the creative “genres” that they suggest on their platform (e.g., “darkly comedic historical drama”) suggest that they are fitting some sort of a topic model and building an ex-post interpretation around the topics.

Collaborative filtering is far more general than movie recommendation. As Amazon says, “People who buy this book also bought . . .” One way to approach the problem is to run a ton of logistic lasso regressions—one for each product (movie) on to every other product. This is actually not a bad idea, if you have the massive computing resources that it requires. A lower fidelity but more computationally feasible alternative is the classic data mining strategy of market basket analysis (MBA), which searches efficiently through the data for association rules.

An association rule is a case where the conditional probability of product A given you also purchase product B is high—much higher than the unconditional probability for product A. For example, perhaps when you buy beer, you need chips for the munchies. If you only ever buy chips after beer, then there will be an association rule: beer → chips. However, if you always buy chips regardless of beer, then the probability of chips will be high, but this is not an association rule because beer doesn't make a difference.

That's it. MBA has its own lingo that can confuse outsiders, but this can be easily translated into basic probabilities. Suppose that chips are purchased 10% of the time in general, but 50% of the time when the consumer grabs beer. You then have a beer → chips association rule.

- The **support** for chips is 10%. This is p(chips).
- The **confidence** of this rule is 50%. This is p(chips|beer).
- The rule **lift** is 5: 50% is 5 times higher than 10%. This is $\frac{\text{p(chips|beer)}}{\text{p(chips)}} = \frac{\text{p(chips,beer)}}{\text{p(beer)p(chips)}}$

The increase in the joint probability relative to what you'd expect if chips and beer were independent.

Association rules with high lift are most useful because they tell you something you don't already know.

There's no deep theory around association rules. You just scan the product pairings to find interesting high-lift and high-confidence rules. To illustrate, we'll switch from movies and beer to music. We have data from last.fm, an online radio service. For each of 15,000 users, we have the playlist of their recent listening session.

```
> head(lastfm)
```

| user | artist | sex | country |
|---|---|---|---|
| 1 | red hot chili peppers | f | Germany |
| 1 | the black dahlia murder | f | Germany |
| 1 | goldfrapp | f | Germany |
| 1 | dropkick murphys | f | Germany |
| 1 | le tigre | f | Germany |
