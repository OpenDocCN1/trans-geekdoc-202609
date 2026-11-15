# Table 6.5 What determines whether we record a person's favorite group?

| Person | Age | Favorite group |
|---|---|---|
| Bill | 17 | Abba |
| Fred | 12 | - |
| Mary | 20 | - |
| Sue | 13 | Dire Straits |
| Tom | 19 | The Beatles |

One pattern that fits the sample data is to record a person's choice of favorite group if and only if the person is aged between 13 and 19 inclusive (i.e., the person is a teenager). This is not the only pattern that fits, however. Maybe favorite group is recorded just for people with odd ages (13, 17, and 19 are odd numbers).

While these might be the two most “obvious” patterns, there are infinitely many patterns that are consistent with the data. Just based on age, we could specify any set of natural numbers within the possible age range that included 13, 17, and 19 but excluded 12 and 20 (e.g., {13, 17, 19, 1}, {13, 17, 19, 5, 63} and so on).

A database population is *significant with respect to a constraint* if and only if it satisfies no alternative choice for this constraint (excluding weaker constraints implied by this choice). Obtaining a sample population that is significant with respect to uniqueness constraints can be tedious, but it can be done in a modest amount of time. Unfortunately, no decision procedure exists to automatically churn out the correct subtype definitions.

If we remove the restriction that a computer system has finite memory, then we encounter the problem that for any finite set of data, there will always remain an infinite number of possible patterns that fit the data. This is the basis of the philosophical “problem of induction”.

As a scientific example, consider the graph shown in Fig. 6.49. This shows three data points determined from an experiment in which the pressure (p) and absolute temperature (T) of a gas are measured at a fixed volume. What pattern, rule, or law does this suggest to connect pressure and temperature?

One pattern that fits the data is the linear relationship between pressure and temperature shown by the straight line in Fig. 6.50(a). This shows that when the volume of gas is fixed, its pressure is directly proportional to its absolute temperature. You may recall learning this law of physics in high school. However, the curved line in Fig. 6.50(b) also fits the data. How do we know which (if any) is correct?

![](bbox=[0.37, 0.76, 0.6, 0.87])

FIG. 6.49 What pattern matches the data?