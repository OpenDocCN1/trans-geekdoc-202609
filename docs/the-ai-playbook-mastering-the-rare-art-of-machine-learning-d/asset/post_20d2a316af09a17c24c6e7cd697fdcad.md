
## To Launch Is to Take a Leap

model's potential value. At 27 percent, my model showed a lift of 1.5, which I translated into a potential profit of $286,000. That's where the beautiful profit curve that I showed them came to a peak, forecasting the effect of a targeted marketing campaign offering a discount to customers most at risk for cancellation.

But the value of churn modeling is harder to forecast than the value of response modeling. A response model is trained on data recording a previous marketing campaign, but a churn model is only trained on the history of who did and who didn't cancel. Gay.com hadn't conducted a campaign to retain customers, so even if the model promised to target likely defectors well, we could only guesstimate how many of those defectors would change their minds after receiving a discount meant to keep them around. For gay.com, I assumed the company would gain an average of $100 in value for every would-be defector offered a $25 discount. The profit calculation also had to take into account that the company would lose $25 in revenue for FPs—customers who were provided that discount but weren't actually going to cancel.

Although gay.com didn't deploy, my second client, EduPay, courageously launched my ad targeting models—despite an equally high dose of uncertainty. Remember that, for EduPay, I generated 291 different models, each predicting whether the user would respond to its corresponding ad. I could see how well each model predicted, but that only indirectly spoke to how much deployment would pan out financially. How much would using these predictions improve over the existing process of displaying ads that are popular across users in general? Until we conducted the ultimate experiment that is model deployment, we couldn't be certain how much value it would generate.

At UPS, this uncertainty only added to the pressure Jack Levi felt. It magnified the challenge presented by the Innovator's Paradox—that the more novel or radical an idea, the greater the struggle to gain support for it. On top of that, Jack now faced the Deployment Paradox:

The Deployment Paradox: For some projects, the business value of improved decisioning is hard to estimate before deployment; it can only be reliably established _after_ you deploy.

Jack's model was technically sound, predicting up to 93 percent of tomorrow's deliveries correctly. And he knew how to estimate the misclassification costs. Each FP cost a good deal, on average, since the resulting plan would include an unnecessary delivery destination. FNs weren't as bad, since it was often relatively easy to later correct a truck's plan by incorporating a new destination.

But Jack wanted to translate this to business metrics. As he put it, “I wanted to know what more accuracy's worth, moneywise.” However, for UPS's complex delivery-planning system, this translation wasn't straightforward. Delivery prediction injected insight into UPS's complex planning system. How much this more sophisticated method would improve operations in business terms was something you could only roughly approximate beforehand. The pertinent KPIs included annual dollars and driving miles saved. They also included the more wonky metric _stops-per-mile_, which increases as truck planning becomes more efficient—the more densely a route is packed with deliveries, the more value is generated from each mile of driving.

Jack made rough estimates, but he would only find out the ultimate value of his optimization system by tracking its performance during deployment. When we get to the topic of deployment in chapter 6, we'll see the ups and downs his system experienced. And we'll also see EduPay's deployment results in that chapter as well.

But we have a couple more steps to go before deployment. In the next chapter, we prepare the data on which the model will be trained.

## 4 Fuel

## Prepare the Data

Data trumps the algorithm. Machine learning algorithms may be the fun, sexy part—everyone wants to crash that party—but improving the data is where you usually get the greatest payoff. Data is the source of predictive power. It encodes the prior happenings of the world, the experience from which ML will learn. ML software is only as good as the data you give it.

To make use of the data you have, you’ve got to expertly reconfigure it into training data, which takes a simple form: Whatever you want to predict, you need a bunch of both positive and negative learning examples. But despite this simplicity, training data is no easier to prepare than Michelin-starred cuisine. Whatever form your existing data has come to take, it probably wasn’t accrued with ML in mind. As a result, preparing the training data usually represents the ML project’s greatest technical bottleneck.

So why is data prep so commonly underestimated, underplayed, and undervalued? How do business-side priorities drive data requirements? How much data do you need? And how do you know which learning examples are positive and which are negative—where do you get those labels? Finally, what kind of noise in the data kills ML and what kind is copacetic?

### The BizML Practice:

- 1. Value: Establish the deployment goal.
- 2. Target: Establish the prediction goal.
- 3. Performance: Establish the evaluation metrics.
- 4. Fuel: Prepare the data.
- 5. Algorithm: Train the model.
- 6. Launch: Deploy the model.

Scott Zoldi fights crime across the globe. His superpower is data—and an unprecedented, innovative process to amass that data.

He's got his work cut out for him. Every day, hordes of criminals work to exploit systemic vulnerabilities in how you and I shop. Their relentless work chips away at the very integrity of consumer commerce at large.

I'm talking about fraud. Crooks obtain your card details so that they can perform a transaction and make off with the spoils. In 2021, payment card fraud losses reached $28.58 billion worldwide. The United States suffers more than any other country, accounting for more than a third of that loss. To make matters worse, fraud increased during the pandemic, in part due to the increase in “card-not-present” virtual transactions. Some called it the “scamdemic.”

Scott is FICO’s chief analytics officer. He oversees the world’s largest-scope anti-fraud operation. Day in and day out, his product Falcon screens all of the transactions made with most of the world’s credit and ATM cards—2.6 billion cards globally. With Falcon, banks and other financial institutions can instantly block suspicious purchases and withdrawals.

This capability hinges on machine learning—and it demands an impressive dataset. As we saw in the last chapter, a fraud-detection model must predict well, striking a tricky balance so that it recognizes a lot of fraud and yet does so without incurring too many false positives. To this end, the data must fulfill exacting requirements. If you visualize the data as a simple table, just a big spreadsheet, it must be long, wide, and labeled—here’s what I mean:

- 1. Long. You need data about real transactions—a lot of them. This list of many, many example cases from which to learn must be a long one. And by including a broad assortment of cases from around the world, the data can be representative. Each case composes a row of the data.

- 2. Wide. You need revealing information about each case, including behavioral characteristics of both the cardholder and the merchant. These are the factors on which a model will base its predictions. Since each row enumerates all these factors, the data is also wide. Each factor composes a column of the data.

- 3. Labeled. ML software needs many known examples of fraud from which to learn, prior transactions that have been designated as such. How do these cases get labeled? The fraudsters who perpetrated these crimes know which are which, but they have not, so far, been cooperative. This means we need humans on our side to manually label many examples. These labels typically make up the rightmost column of the data.

### Wide data has more information about each case

| E-commerce | $125 | Not-present | $250/day | .... | Yes |
|---|---|---|---|---|---|
| Grocery | $17 | Chip | $700/day | .... | No |
| Clothing | $275 | Swipe | $25/day | .... | No |
| Pharmacy | $27 | Tap | $150/day | .... | Yes |
| Utility | $59 | Not-present | $75/day | .... | No |
| Airline | $782 | Not-present | $35/day | .... | Yes |
| Hotel | $1,221 | Chip | $100/day | .... | No |
| Restaurant | $76 | Tap | $40/day | .... | No |
| Pharmacy | $32 | Swipe | $275/day | .... | No |
| Grocery | $112 | Tap | $400/day | .... | No |
| E-commerce | $43 | Not-present | $80/day | .... | No |
| Restaurant | $82 | Chip | $30/day | .... | No |
| Utility | $26 | Not-present | $100/day | .... | No |

Such a dataset sounds almost impossible to acquire. It could only be sourced from multiple banks across the globe. And even if you somehow
