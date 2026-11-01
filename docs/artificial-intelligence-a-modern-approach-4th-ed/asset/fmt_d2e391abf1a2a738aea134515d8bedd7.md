
[Equation (15.2)](#Chapter15-02.xhtml#eq15-2) says that there is no absolute scale for utilities, but it is helpful, nonetheless, to establish some scale on which utilities can be recorded and compared for any particular problem. A scale can be established by fixing the utilities of any two particular outcomes, just as we fix a temperature scale by fixing the freezing point and boiling point of water. Typically, we fix the utility of a “best possible prize” at `U(S) = u⊤` and a “worst possible catastrophe” at `U(S) = u[⊥]`. (Both of these should be finite.) Normalized utilities use a scale with `u[⊥] = 0` and `u⊤ = 1`. With such a scale, an England fan might assign a utility of 1 to England winning the World Cup and a utility of 0 to England failing to qualify.

*Normalized utilities*

Given a utility scale between `u⊤` and `u[⊥]`, we can assess the utility of any particular prize `S` by asking the agent to choose between `S` and a standard lottery `[p, u⊤; (1 – p), u[⊥]]`. The probability `p` is adjusted until the agent is indifferent between `S` and the standard lottery. Assuming normalized utilities, the utility of `S` is given by `p`. Once this is done for each prize, the utilities for all lotteries involving those prizes are determined. Suppose, for example, we want to know how much our England fan values the outcome of England reaching the semi-final and then losing. We compare that outcome to a standard lottery with probability `p` of winning the trophy and probability `1 – p` of an ignominious failure to qualify. If there is indifference at `p = 0.3`, then 0.3 is the value of reaching the semi-final and then losing.

*Standard lottery*

In medical, transportation, environmental and other decision problems, people’s lives are at stake. (Yes, there are things more important than England’s fortunes in the World Cup.) In such cases, `u[⊥]` is the value assigned to immediate death (or in the really worst cases, many deaths). Although nobody feels comfortable with putting a value on human life, it is a fact that tradeoffs on matters of life and death are made all the time. Aircraft are given a complete overhaul at intervals, rather than after every trip. Cars are manufactured in a way that trades off costs against accident survival rates. We tolerate a level of air pollution that kills four million people a year.

Paradoxically, a refusal to put a monetary value on life can mean that life is undervalued. Ross Shachter describes a government agency that commissioned a study on removing asbestos from schools. The decision analysts performing the study assumed a particular dollar value for the life of a school-age child, and argued that the rational choice under that assumption was to remove the asbestos. The agency, morally outraged at the idea of setting the value of a life, rejected the report out of hand. It then decided against asbestos removal—implicitly asserting a lower value for the life of a child than that assigned by the analysts.

Currently several agencies of the U.S. government, including the Environmental Protection Agency, the Food and Drug Administration, and the Department of Transportation, use the value of a statistical life to determine the costs and benefits of regulations and interventions. Typical values in 2019 are roughly $10 million.

*Value of a statistical life*

Some attempts have been made to find out the value that people place on their own lives. One common “currency” used in medical and safety analysis is the micromort, a one in a million chance of death. If you ask people how much they would pay to avoid a risk—for example, to avoid playing Russian roulette with a million-barreled revolver—they will respond with very large numbers, perhaps tens of thousands of dollars, but their actual behavior reflects a much lower monetary value for a micromort.

*Micromort*

For example, in the UK, driving in a car for 230 miles incurs a risk of one micromort. Over the life of your car—say, 92,000 miles—that’s 400 micromorts. People appear to be willing to pay about $12,000 more for a safer car that halves the risk of death. Thus, their car-buying action says they have a value of $60 per micromort. A number of studies have confirmed a figure in this range across many individuals and risk types. However, government agencies such as the U.S. Department of Transportation typically set a lower figure; they will spend only about $6 in road repairs per expected life saved. Of course, these calculations hold only for small risks. Most people won’t agree to kill themselves, even for $60 million.

Another measure is the `QALY`, or quality-adjusted life year. Patients are willing to accept a shorter life expectancy to avoid a disability. For example, kidney patients on average are indifferent between living two years on dialysis and one year at full health.

*QALY*

## 15.3.2 The utility of money

Utility theory has its roots in economics, and economics provides one obvious candidate for a utility measure: money (or more specifically, an agent’s total net assets). The almost universal exchangeability of money for all kinds of goods and services suggests that money plays a significant role in human utility functions.

It will usually be the case that an agent prefers more money to less, all other things being equal. We say that the agent exhibits a monotonic preference for more money. This does not mean that money behaves as a utility function, because it says nothing about preferences between lotteries involving money.

*Monotonic preference*

Suppose you have triumphed over the other competitors in a television game show. The host now offers you a choice: either you can take the $1,000,000 prize or you can gamble it on the flip of a coin. If the coin comes up heads, you end up with nothing, but if it comes up tails, you get $2,500,000. If you’re like most people, you would decline the gamble and pocket the million. Are you being irrational?

Assuming the coin is fair, the expected monetary value (`EMV`) of the gamble is $\\frac{1}{2}(\\$ 0) + \\frac{1}{2}(\\$ 2,500,000) = \\$ 1,250,000$, which is more than the original $1,000,000. But that does not necessarily mean that accepting the gamble is a better decision. Suppose we use `Sn` to denote the state of possessing total wealth `n`, and that your current wealth is `k`. Then the expected utilities of the two actions of accepting and declining the gamble are

```
$\\begin{array}{l} {EU\\text{(}Accept\\text{)~=}\\frac{1}{2}U\\text{(}S\_{k}\\text{)} + \\frac{1}{2}U(S\_{k + 2,500,000})\\text{,}} \\\\ {EU\\text{(}Decline\\text{)~=~}U\\text{(}S\_{k + \\text{1,000,000}}\\text{)~}\\text{.}} \\\\ \\end{array}$
```

*Expected monetary value*

To determine what to do, we need to assign utilities to the outcome states. Utility is not directly proportional to monetary value, because the utility for your first million is very high (or so they say), whereas the utility for an additional million is smaller. Suppose you assign a utility of 5 to your current financial status (`Sk`), a 9 to the state `Sk + 2,500,000`, and an 8 to the state `Sk + 1,000,000`. Then the rational action would be to decline, because the expected utility of accepting is only 7 (less than the 8 for declining). On the other hand, a billionaire would most likely have a utility function that is locally linear over the range of a few million more, and thus would accept the gamble.

In a pioneering study of actual utility functions, Grayson (1960) found that the utility of money was almost exactly proportional to the logarithm of the amount. (This idea was first suggested by Bernoulli (1738); see Exercise 15.STPT.) One particular utility curve, for a certain Mr. Beard, is shown in [Figure 15.2(a)](#Chapter15-03.xhtml#fig15-2). The data obtained for Mr. Beard’s preferences are consistent with a utility function

Description
