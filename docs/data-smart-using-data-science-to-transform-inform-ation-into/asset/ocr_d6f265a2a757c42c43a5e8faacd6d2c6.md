It's still better than not having a model at all, right? Undoubtedly. But the question is how much better is the stump than not having a model. One way to evaluate that is through a measurement called node impurity.

Node impurity measures how often a chosen customer record would be incorrectly labeled as pregnant or not-pregnant if it were assigned a label randomly, according to the distribution of customers in its decision stump subset.

For instance, you could start by shoving all 1,000 training records into the same subset. That is to say, start without a model. The probability that you'll pull a pregnant person from the heap is 50 percent. And if you label them randomly according to the 50/50 distribution, you have a 50 percent chance of guessing the label correctly.

Thus, you have a 50% * 50% = 25 percent chance of pulling a pregnant customer and appropriately guessing they're pregnant. Similarly, you have a 25 percent chance of pulling a not-pregnant customer and guessing they're not pregnant. Everything that's not those two cases is just some version of an incorrect guess.

That means I have a 100% – 25% – 25% = 50 percent chance of incorrectly labeling a customer. So, you would say that the impurity of my single starting node is 50 percent.

The folic acid stump splits this set of 1,000 cases into two groups—894 folks who didn't buy folic acid and 106 folks who did. Each of those subsets will have its own impurity, so if you average the impurities of those two subsets (adjusting for their size difference), you can tell how much the decision stump has improved your situation.

For those 894 customers placed into the not-pregnant bucket, 44 percent of them are pregnant and 56 percent are not. This gives an impurity calculation of 100% – 44%² – 56%² = 49 percent. Not a whole lot of improvement.

But for the 106 customers placed in the pregnant category, 98 percent of them are pregnant and 2 percent are not. This gives an impurity calculation of 100% – 98%² – 2%² = 4 percent. Very nice. Averaging those together, you find that the impurity for the entire stump is 44 percent. That's better than a coin flip!

Figure 7.3 shows the impurity calculation.

# SPLITTING A FEATURE WITH MORE THAN TWO VALUES

In the RetailMart example, all the independent variables are binary. You never have to decide how to split the training data when you create a decision tree—the 1s go one way, and the 0s go the other. But what if you have a feature that has all kinds of values?

For example, let's say you work for a large email service, and you want to know if an email address is alive and can receive mail. One of the metrics used to do this is how many days have elapsed since someone sent an email to that address.