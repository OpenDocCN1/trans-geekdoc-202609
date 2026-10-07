So we're going to pick any of them. Next we actually pull the lever of that selected machine. (Or, in case of Ads picking problem: we display that Ad and want to see if the person click on it did the person not click on it)

Lets in, in this case person loss hit to the machine (or user didn't click on Ad), so red-dotted value goes down because it is like the observed average for a large numbers of observation this red-dotted value is always going to converge to the expected return or expected average or expected value for this distribution

![](bbox=[0.258, 0.148, 0.742, 0.269])

D1 D2 D3 D4 D5
Red-dotted value goes down

![](bbox=[0.258, 0.345, 0.742, 0.467])

D1 D2 D3 D4 D5
Confidence bond Shrinks

And now because we have an extra observation, the second thing happens is the confidence bond Shrinks. That confidence interval become smaller because we have an additional observation we are more confident in our predictions.

So the next step is now we find the next one with the highest confidence bond. Obviously it's one of these machines, and we are picking a random one. Say we choose the Green one.

![](bbox=[0.103, 0.642, 0.896, 0.753])

D1 D2 D3 D4 D5 D1 D2 D3 D4 D5

Say we got positive i.e. user wins with this machine (or, visitor clicked in our Ad), in this case the red-dotted value goes up. And the confidence bond shrinks.

+   - Because we got an additional observation in our sample. Confidence bands only purpose is to include the actual expected value wherever it is. When the sample grow, we become more confident about the expected value, hence this confidence bond shrinks.

+   - Now in this iteration we stop looking for the best distribution and we can conclude that this current machine (or current Ad) is with the bestdistribution(which is not). In case algorithm fails.

Similarly we pick a machine/Ad from the remaining ones. We do trial and get positive/negative result the red-dotted line goes up/down according to the results and Confidence bond Shrinks.

* We want