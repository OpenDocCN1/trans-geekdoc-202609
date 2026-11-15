| Politician | Country | Year |
|---|---|---|
| George W. Bush | US | 1946 |
| William J. Clinton | US | 1946 |
| John Howard | AU | 1939 |
| Kevin Rudd | AU | 1957 |

| Politician | Country | Year |
|---|---|---|
| George W. Bush | GB | 2003 |
| George W. Bush | IE | 1999 |
| William J. Clinton | IE | 1999 |
| William J. Clinton | IE | 2003 |
| John Howard | IE | 2003 |
| John Howard | US | 2003 |

FIG. 3.2 Two reports about politicians.

Although there are in principle infinitely many possible interpretations of the data, you can probably guess the intended meaning. We may read off the information represented in Fig. 3.2(a) and (b), respectively, as shown in the following two facts.

+   30. The Politician “George W. Bush” *was born in* the Country “US” in the Year 1946.
+   31. The Politician “George W. Bush” *visited* the Country “GB” *in* the Year 2003.

While these facts do provide a correct interpretation of the meaning of the data on the top rows, only one of these facts is elementary. Which is it?

Fact 30 is not elementary because it may be split into the following facts without loss of information.

+   32. The Politician “George W. Bush” *was born in* the Country “US”.
+   33. The Politician “George W. Bush” *was born in* the Year 1946.

Connecting two sentences by “and” forms a logical *conjunction* of the two sentences. Intuitively, fact 30 is equivalent to the conjunction of facts 32 and 33, so fact 30 is splittable (nonelementary). Formally, this is because of a uniqueness constraint on the politician column—each politician was born in only one country and in only one year. We discuss such constraints in a later chapter and provide rules and heuristics to help determine whether a given fact is elementary. For now, however, let’s just use our intuitions.

Fact 31 is elementary because you cannot treat it as a conjunction of simpler facts without losing information. For example, if we told you that George W. Bush visited the United Kingdom (the country with country code “GB”) and that he travelled overseas in 2003, it does not follow that he visited the United Kingdom in that year.

In some cases, a ternary fact that is not splittable into two facts may be split into three facts. Here we might try split fact 31 into the above two facts as well as the third fact that the United Kingdom was visited in 2003. However even these three facts don’t guarantee that George W. Bush visited the United Kingdom in 2003.

Formally, the structural difference between reports (a) and (b) is their uniqueness constraint pattern. In report (a), the first column values must be unique (not duplicated). In report (b), only the whole rows must be unique (entries for single columns or any column pair may be duplicated). The next chapter discusses such patterns in detail.