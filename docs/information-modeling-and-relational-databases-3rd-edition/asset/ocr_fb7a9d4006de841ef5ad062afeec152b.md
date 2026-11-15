function of Subject, but this has no bearing on the spltability. We should use two binaries even if the same subject can have many lecturers. It is the functional dependency of Credit on Subject that disqualifies the nested approach.

In a case like this where it is difficult to come up with a natural name for the objectified association, such nesting errors are unlikely to occur in practice. When a natural name for the nested object type is available, however, it is easier to make the error. For example, we might objectify the fact type Person was born in Country as “Birth”, and then add the fact type Birth occurred on Date. Although it sounds reasonable, this nesting violates the spanning rule, and should normally be replaced by the unnested binary: Person was born on Date. We discuss further cases of objectification in Chapter 10 and provide heuristics for choosing when to objectify.

One lesson to be learned from this section is to look out for UCs even when performing step 1. Consider the output report of Table 4.13. If I told the population is significant, how would you model this?

If you used either a ternary or a nested fact type, you made a mistake! Although similar to an earlier example, the UoD described by this table is more restricted. Given that the population is significant, the lack of duplicates in the Person column indicates that, at any given time, each person can be enrolled in only one subject.

Table 4.13 Student results.

| Person | Subject | Rating |
|---|---|---|
| Adams | CS112 | 7 |
| Brown | CS112 | 5 |
| Collins | PD102 | 5 |

For example, these people might be your employees, and you are funding their studies and want to ensure that they don’t take on so much study that it interferes with their work performance.

Because we store information only about the current enrollments, and each person is enrolled in only one subject, it follows that each person can get only one rating. So, if we know the subject in which a person is enrolled and we know the rating obtained by the person, we do know the subject in which this rating is obtained by that person. To begin with, we might express the information on the first row of the table in terms of the ternary “Person (surname) “Adams” scores Rating (.nr) 7 for Subject (.code) “CS112”. However, because of the UC on Person we should rephrase this information as the conjunction:

```
Person (Surname) 'Adams' studies Subject (.Code) 'CS112'
and
Person (Surname) 'Adams' scores Rating (.Nr) 7.
```

This leads to a conceptual schema with two binary fact types. Because of this unusual UC, the ternary has the same truth value as the conjunction of binaries for all possible states of this UoD.