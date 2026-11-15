| Nr | Pattern | Description |
|---|---|---|
| 20 | Cancel case | Activity 1
Activity 2
Activity 3
Activity 4
Activity 5
cancel A3
catch
throw
N

The progression of the process instance makes it clear that a particular case in progress should be canceled. This is like the previous pattern but here we are canceling a complete case (and all the activities relating to it) instead of just an activity. If the case represents the whole process, we can just use a Terminate event, which kills every activity in progress. |

The original workflow patterns focused on flow-of-control aspects. A similar analysis has been applied to workflow data patterns by Russell and colleagues (Russell et al., 2016), who define five main categories of pattern: Data Visibility (7 patterns), Internal Data Interaction (6 patterns), External Data Interaction (12 patterns), Data Transfer (7 patterns), and Data Routing (7 patterns). The patterns illustrate the way in which many data-related features are handled by current workflow tools. Although no claim is made that the list of features is exhaustive, the patterns probably represent a reasonable catalog of concepts that need to be considered in the context of process data.

Because the data patterns were gleaned by examining current practice, they effectively make statements about the way that process data is typically handled in a software implementation. However, here we are mainly concerned with modeling processes at a conceptual level. This corresponds to the distinction between an ORM information model and its implementation in (say) a relational database management system. Examination of the documented data patterns shows that several of them are primarily abstractions of implementation patterns, rather than information usage patterns.

As an example, we could consider two activities, A and B, with a dependency between them. Activity B needs some information created by Activity A, and so it would be natural for an instance of Activity A to precede temporally the corresponding instance of Activity B. This is true whether we are considering the process at a purely conceptual level or looking at the implementation.

If the activities are implemented in some object-oriented software language, a standard approach would be to create some object within the Activity A instance and then pass it to the corresponding Activity B instance; in other words, we could say that Activity A