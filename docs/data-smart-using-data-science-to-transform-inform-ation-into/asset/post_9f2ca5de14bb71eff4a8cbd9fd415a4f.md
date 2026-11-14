
Hold the phone. The model might be "accurate," but is it useful? Pregnant individuals, the minority class, is who we actually care about. How accurate would our model be if trained on mostly nonpregnant cases?

This is why we've assembled a sample with a 50/50 split. This is called oversampling. By rebalancing the training data, our model will have much more pregnancy-related individuals to train on. Though this choice does introduce bias and implies pregnancy is more common than it really is, in truth, we don't care. The model doesn't need to be a perfect reflection of reality. What model is?

Instead, as we'll see later in this chapter, we care much more about the results. We'll want to tune the model to hit that "sweet spot," wherein we find the perfect balance of true positives and false positives. It's there where we'll find the most predictive value.

| Implied Gender | Home/Apt/PO Box | Pregnancy Test | Birth Control | Feminine Hygiene | Folic Acid | Prenatal Vitamins | Yoga | Pillow | Ginger Ale | Sea Bands | Stopped buying... | Cigarettes | Smoking... | Stopped buying... | Wine | Maternity Clothing | Pregnant? |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M | A | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | H | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | H | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| F | A | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | A | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| F | H | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | H | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| M | A | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| F | H | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| F | H | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| F | A | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 |
| F | H | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 1 |
| U | A | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
| M | A | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | 1 |
| M | H | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | P | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| F | H | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | H | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | A | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
| M | A | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| F | H | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
| F | P | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 |
| F | H | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| M | A | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| F | A | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| M | H | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| M | A | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| F | A | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| M | A | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
| F | A | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
| M | H | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
| U | A | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| F | A | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| M | H | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 |
| M | H | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |

Figure 6.1: Raw training data

In the first two columns of the training dataset, you have categorical data for gender and address type. The rest of the features are binary where a 1 means TRUE. For example, if you look at the first row in the spreadsheet, you can see that this customer was confirmed pregnant (column R). That's the column you're going to train the model to predict. And if you look at this customer's past purchasing history, you can see that they purchased a pregnancy test and some prenatal vitamins. Also, they have not purchased cigarettes or wine recently.

If you scroll through the data, you'll see all types of customers, some with lots of indicators and some with little. Just as expected, pregnant households will occasionally buy cigarettes and wine, while nonpregnant households will buy products associated with pregnancy.

## Creating Dummy Variables

You can think of an AI model as nothing more than a formula that takes numbers in, chews on them a bit, and spits out a prediction that should look something like the 1s (pregnant) and 0s (not) in column R of the spreadsheet.

But the problem with this data is that the first two columns aren't numbers, are they? They're letters standing for categories, like male and female and unknown.

This issue, handling *categorical data*, that is, data that's grouped by a finite number of labels without inherent numeric equivalents, is one that constantly nips at data miners' heels. Perhaps you can feel the lil' ankle biters right now as you go through this. If you send out a survey to your customers and they have to report what line of work they're in, their marital status, the country they live in, the breed of dog they own, or their favorite episode of *Gilmore Girls* ("the one when Jess and Rory kiss," says my friend, Nicole), then you're going to be stuck dealing with categorical data.

This is in contrast to *quantitative data*, which is already numeric and ready to be devoured by data mining techniques.

So, what do you do to handle categorical data? Well, in short, you need to make it quantitative.

Sometimes, your categorical data may have a natural ordering that you can use to assign each category a value. Think T-shirts: small, medium, large is easily translated to numbers like 1, 2, and 3.

But more frequently, there is no inherent ordering, such as with gender. In this case, it's common to use a technique called *dummy coding* to convert your categorical data to quantitative data.

Dummy coding works by taking a single categorical column (consider the Gender column) and turning it into multiple columns with a quantitative encoding. If a value in the original column were "M," that instead could be coded as a 1 in the Male column and 0 for the other columns.

When dummy coding a categorical variable, you always need one less column than you have category values—the last category is always implied by the other values being zero. In stats-speak, you could say any categorical variable has *n-1 degrees of freedom*, where *n* is the total count of possible encodings. The last possibility is implied so the degrees of freedom are always one less.

NOTE The included sample dataset assumes an exhaustive categorical split between male and female categories, which I've not changed in keeping with the first edition. But consider that a gender column in the real world might have more categories. For example, "nonbinary," "genderqueer," and "prefer not to say" are some possibilities. Remember, demographic features are particularly subject to cultural force and interpretation. Be sure not to exclude groups whose data might help your analysis. And, always be attentive to the context in which your data is collected and presented.

In this particular example, let's start by creating a copy of the Training Data sheet called Training Data w Dummy Vars. You're going to split the first two predictors into two columns each, so go ahead and clear out columns A and B and insert another two blank columns to the left of column A.

Label these four empty columns Male, Female, Home, and Apartment (unknown gender and PO box become implied). As shown in Figure 6.2, you should now have four empty columns to house the dummy coding of your two categorical variables.

![](img/9c4b3d77873bec9e7da149a75c568d36_189_0.png)

Figure 6.2: Training Data w Dummy Vars tab with new columns for the dummy variables

Consider the first row of training data. To turn the "M" in the gender column into dummy-encoded data, you place a 1 in the Male column and a 0 in the Female column.

In cell A2 on the Training Data w Dummy Vars tab, check the old category on the Training Data tab and set a 1 if the category was set to "M."

```
= (CustomerData[@[Implied Gender]]="M") * 1
```
