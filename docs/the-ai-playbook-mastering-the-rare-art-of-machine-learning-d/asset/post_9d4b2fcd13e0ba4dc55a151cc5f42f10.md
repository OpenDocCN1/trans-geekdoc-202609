
so many incorrect values that it's effectively random junk, then a good learning algorithm will completely avoid using that variable—or at least lower its involvement within the model down to nearly zero.

To put it another way, incorrect input values just make for more noise. Inputs are already noisy in the sense of uncertainty. For the ML algorithm, noise is noise and it doesn't matter which kind of noise it is.

Picture it this way: If you're doing image classification, you can see that even if there's a fair amount of noise in the image, it is still easy for you to tell that it's a photograph of a person wearing a hat. A model can handle noise much the same.

![](img/99a58a0ea5f8204f7fbf446f6593fd4f_162_0.png)

A photograph of a person wearing a hat is still easy to discern with noise added.

It's a relief the world won't end if you have bad values among the input variables. But there's one major caveat: The level of noise must remain roughly consistent between the training data and the data input to the model during deployment. If incorrect values are provided when actually using a model, but a similar prevalence of errors wasn't present in the training data when developing the model, the model's performance won't hold up. So its input better not be wrong much more often than it was within the training data that the machine learned from in the first place.

This is just one part of a more general requirement: The training data must be *representative* of the data encountered during deployment. That is, the experience over which the machine learns must come from the same “world” or “universe” within which the model will subsequently be used. The learning cases must *represent* the same “reality.” For example, if the model will target marketing for all customers in the United States but the training data only includes customers in California, that data won’t be representative; you can’t expect model performance to carry over to the rest of the country.

For the EduPay project, my data failed to meet this requirement. It wasn’t entirely representative. For each ad, the training cases were a result of the legacy system’s peculiarities. For example, an ad hoc method estimated how popular each new ad would be when first launched, which determined how often and on whom it was tested. I was working with the available data in hand, not conducting experiments to collect an evenly distributed battery of tests for each ad. Although there are technical approaches that might have helped, I didn’t take any measures to address this imperfection in the data. In the chapter on deployment, you’ll see how things panned out nonetheless.

Now that we’ve covered the various requirements for training data, let’s return to FICO to see how the company pulls the data together for its global fraud-detection system.

## FICO Cultivates Data without Borders

Scott Zoldi has a PhD in theoretical physics from Duke University. And he’s formed a team of seventy more people with PhDs. Together, they generate the world’s de facto system for detecting fraudulent card transactions. You, me, and most people with payment cards are relying on them.

Scott’s antifraud operation isn’t what FICO is most widely known for. Along with another one of his teams, Scott also oversees this country’s *most famous* deployed model: the FICO Credit Score. Your FICO Score determines your power to borrow. It's the most widely used credit score in the United States, employed by the vast majority of banks and credit grantors. It's a household name, and many understandably feel that their FICO Score is a central part of their identity as a consumer.

But FICO’s fraud detection, which is normally invisible to us as consumers, affects us much more often. Named Falcon, this product is the biggest part of FICO’s software business and affects most of us almost every day—every time you use your card. FICO evaluates financial power by day—and fights financial crime by night.

To meet this responsibility, it’s important that the Falcon team gets the data it needs—some long, wide, and labeled data. To do so, it collects data from across a global network of banks.

This reliance on inter-enterprise data—collected from multiple companies—is atypical. Ordinarily, an ML project serves only the enterprise running the project. For such a project, internal data suffices, since the company has been tracking the very operations that the project aims to improve. In contrast, FICO isn’t a bank. It doesn’t process card transactions. Rather, it holds a rare, globally central, entrusted role across banks.

In 1992, Falcon was born of a radical move by a small group of banks: They decided to cooperate rather than only compete. At the time, a tremendous portion of all credit card transactions—almost 1 percent—were fraudulent. The fraud rate was only growing and threatened the entire industry. This looming crisis convinced financial institutions to overcome their raw capitalistic instincts and follow a call to arms for the universal good: to collaborate to fight crime, improve transaction integrity, and cut losses. Led by a company called HNC Software, they joined their data together, thereby multiplying their power to train fraud-detection models. Ten years later, FICO acquired HNC Software—and both Falcon and Scott Zoldi along with it.

Since then, Falcon’s consortium has grown to more than 9,000 banks globally, all continually sending in anonymized card transaction details. FICO receives about 20 billion records—amounting to terabytes of raw data—each month, a petabyte every five years.

![](img/99a58a0ea5f8204f7fbf446f6593fd4f_165_0.png)

Banks provide data to develop Falcon's fraud detection model and Falcon deploys that model for each bank.

Banks can’t benefit from Falcon without contributing to it. To be a FICO customer that uses Falcon, you must also join the consortium and share your data. Falcon has become so standard that, despite its cooperative nature, it’s a competitive necessity. To hold their position in the payment card market, banks need Falcon’s best-in-class fraud detection—which they can access only by cooperating. In the end, this levels the playing field: Even the smallest bank can deploy the very best fraud-detection model.

## Engineering Better Inputs for Falcon

For each card transaction, Falcon’s model needs an informative but reasonably succinct summary of all the “evidence” that could reveal whether it’s legitimate or fraudulent. That list of factors, each a potential model input, makes for a row of training data. It includes a rundown of the cardholder’s previous transactions, such as the total number of transactions, number of cash withdrawals, and average transaction amount. These counts are broken down by different time ranges, such as for transactions conducted over the last day, week, month, and three-month period. The counts are also broken down by different types of merchants, such as restaurants and clothing stores.

But that's only the basic groundwork. Scott's team has made a fine art of feature engineering, manually designing more complex inputs that further help identify fraud. These inputs encode whether recent transactions mark changes in cardholder behavior, such as an extreme acceleration in spending or purchases from a completely new kind of merchant—for example, purchasing from a golf store when you've never done so before. At the same time, long-term tracking for each cardholder must recognize annual trends so they don't trigger false flags, such as when a family vacations every year in Florida.

Actually, it's a bit more "meta" than that. Even the most dramatic change in behavior doesn't necessarily reveal fraud since some cardholders are prone to change. They're inclined to do something unprecedented. For this kind of customer, purchasing from a golf store for the first time should not be interpreted as potential fraud. For them, change is nothing new. Some anomalies are benign. With the right inputs, a well-trained model will be able to discern which sort of change in behavior corresponds with fraud.

On top of all this, other inputs track updates to the cardholder's profile. For example, after you change your email address, it may turn out that you're a little more likely to conduct a transaction in a new-to-you country. With inputs designed to reflect this kind of change, the model can potentially learn when to be forgiving of such first-time behaviors. Remember, the aim isn't only to identify fraud but also to tame false positives by allowing legitimate transactions even when they're an outlier for that cardholder.

Finally, other inputs help the model scrutinize aspects of the merchant. After all, it's not only the cardholder's history that reveals that an attempted transaction may be fraudulent. The goings-on at the merchant—across all cards—also provide clues. This includes whether
