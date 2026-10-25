
any one individual. They're the fodder the model will chew on before generating a predictive score.

As all data scientists know, the training data's input columns are technically known as *independent variables* (a.k.a. *features*) and the output column is called the *dependent variable*. But in this book, I'll just call them input and output variables or the inputs and the output.

By placing the input variables next to the output variable on each row, we juxtapose what was known at one point in time alongside the outcome that was found out later, which we'd like to be able to predict. This juxtaposition is what enables the system to discover how things known at one point relate to—and therefore are predictive of—something that will happen later.

To be clear, in this data, both the inputs and the output are already known—no prediction required. Rather, each row is an example from which to learn. Once we ultimately have a model, we'll apply it to cases that look similar to those in the training data, except the output will be as yet unknown. After all, that's the whole point of the modeling process: When the resulting model is used in deployment, all it will have is the input variables. The outcome will be part of the *ultimate unknown* that we call the future. Putting odds on that eventuality is precisely what we're making the model for.

## Big Training Data for Ad Targeting

Of course, real training data grows much wider and longer than the small sample of three rows and nine columns shown earlier. It's wider because more model inputs means more to predict with. For EduPay, I pulled together thirty-three inputs—making the training data thirty-four columns wide if you also count the output variable. This included other elements from the extensive profile EduPay collects from its users, such as career objectives, school clubs, and military experience.

It also included inputs I designed in the hope they would provide novel predictive value, such as:

- The ratio of SAT verbal and math scores. This reflects whether someone is relatively “more verbal”- or “more math”-oriented. For example, if a user got 700 on verbal and 580 on math, the value for this variable would be 1.2.
- College category, as determined by keywords in the institution’s name, for example, Ivy League, state school, university, technical school, or community college.

When you think up new inputs like these, they’re called derived variables and your effort to add them is called feature engineering. This is typically an ad hoc, manual process that taps your own creativity. It’s a key opportunity during the project for business insights to contribute, complementing the degree to which the machine will automatically form combinations that are useful for the predictive goal at hand. Some of the variables that people come up with would be difficult if not impossible for ML to derive automatically, so manually designing new inputs is an important part of the data prep process. Collaborating with business stakeholders to generate ideas for new derived variables often contributes a valuable impact.

Some of the most fruitful derived variables come from if displayed for the user at hand. This meant about 170,000 cases per training dataset on average.

170,000 rows may sound like a lot—but one can’t blithely assume it’s enough.

## How Big Is Big Enough?

How much data do you need? Actually, that’s not the right question. What really matters is how many positive cases you have, because those are more rare. You need a healthy mix of both positive and negative examples. If you have enough positive cases, you're sure to also have enough negative cases.

For example, if an ad's response rate is 1 percent, then 1 percent of the training data will be positive cases and the rest negative. In that situation, negative cases occur ninety-nine times as often as positive. With 1,000 positive cases, we'd have 99,000 negative cases.

Okay, then how many of those less common positive cases do you need? Often, you'll have thousands or even up into six or seven digits' worth. But when positive cases are very rare or your overall dataset is small, that's when this question arises. Responses to ads are rare. Cases of fraud are even more so, amounting to somewhere around 0.1 percent of card transactions.

This question can only be answered vaguely. For many projects, a few thousand positive cases is enough. Even a few hundred may be enough to make a project viable—it's still potentially worth trying. A few dozen usually puts you more into “research project” territory. But there are no absolutes here. You never know how well modeling will work until you try it. There is no concrete theory that provides an absolute answer since the factors at play are just too complex. These include how well your inputs (columns) serve the prediction goal, how well the model must perform to deliver value—depending on the business context—and just how “difficult” the prediction goal is. Some things are easier to predict than others. For example, asking the model to predict further into the future is usually harder than predicting the more immediate future, in that your model's performance would likely be lower for longer-term prediction.

Whatever amount of data may suffice to train the model, you actually need a bit more than that for the purpose of evaluating the model—you need test data. This is a sample of, say, 20 percent of the training data that's held aside during model training. Since it's not available during the model's formation, the test data serves as a basis to assess how well the model performs in general—in new situations that extend beyond the training cases used to develop it.
