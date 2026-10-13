
*   [Rissanen J.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1095) Independent components of relations. *ACM Trans. Database Syst.* 1977;2(2):317–325.
*   [Seidman C.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1145) Creating horizontally partitioned views. In: *SQL Server Magazine, No. 14.* Duke Communications; 2000:51–53.
*   [Thalheim B.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1250) Deductive basis of relations. In: *Proc. MFSSS-84.* Berlin Heidelberg: Springer LNCS 215; 1984:226–230.
*   [Thalheim B.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1255) *Fundamentals of Entity-Relationship Modelling.* Heidelberg: Springer; 1994.
*   [van Bommel P., van der Weide T.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1270) Reducing the search space for conceptual schema transformations. *Data Knowl. Eng.* 1992;8:269–292.
*   [Vincent M.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1295) *Semantic Justification of Normal Forms in Relational Database Design.* PhD Thesis Monash University; 1994.
*   [Vincent M., Srinivasan B.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1300) Redundancy and the justification for fourth normal form in relational databases. *Int. J. Found. Comput. Sci.* 1993;4(4):355–365.
*   [Vincent M., Srinivasan B.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1305) A note on relation schemes which are in 3NF but not in BCNF. *Inform. Process. Lett.* 1994;48:281–283.
*   [Zaniolo C.](#Ch014_681-771_B9780443237904000189.xhtml#B-bb1330) A new normal form for the design of relational database schemas. *ACM Trans. Database Syst.* 1982;7(3):489–499.

# 15 Process and State Modeling

## Abstract

This chapter examines how business activity and business information can be modeled as complementary to each other. The two main approaches of process modeling and state modeling are analyzed using their representations in `UML`. Detailed coverage of process modeling using the `BPMN` standard is provided, together with a methodology for linking process models and information models.

### Keywords

Process modeling; State modeling; Workflow; `BPMN`; `DMN`; Process-Information bridge

## Chapter Outline

*   15.1 **Modeling Dynamic Behavior**
*   15.2 **Processes and Workflow**
*   15.3 **Foundations for Process Theory**
*   15.4 **State Models**
*   15.5 **Modeling Information Dynamics in UML**
*   15.6 **Business Process Standards Initiatives**
*   15.7 **Business Process Model and Notation**
*   15.8 **Standard Process Patterns**
*   15.9 **Process Models, Databases, and ORM**
*   15.10 **Decision Model and Notation**
*   15.11 **Summary**

## 15.1 Modeling Dynamic Behavior

In this book, we have been mostly concerned with understanding information structures. This has very practical applications: if we want to build a business information system, it is crucial that we have an accurate definition of the information that we intend to use. We have seen how information can be modeled and how we can use the knowledge gained through modeling as the basis for storing and manipulating the information. Of course, modeling does not in itself determine what kind of information fulfills a business need. For example, should a customer information system include each customer’s shoe size? For a shoe retailer, this is likely to be important information, but it would probably be irrelevant for an auto insurance company. Whatever the chosen scope, we’ve seen how it is possible to produce very precise definitions of the required business information.

Information models make minimal assumptions about how the information will be used. This is quite deliberate: a business may find that information originally intended for one purpose turns out to be useful for other purposes. Some implementation choices may be made below the conceptual level, such as denormalizing a database schema to improve query performance. However, it’s generally desirable to have an information model that reflects the intrinsic structure of the information itself and is neutral with respect to information usage.

A side effect of this is that an information model does not provide a complete specification of the information dynamics, the temporal relationships among information creation, modification, and deletion. To represent these aspects fully, we need some additional specification.

We can illustrate this point with an example. [Fig. 15.1](#Ch015_773-830_B9780443237904000190.xhtml#f0010) shows a fragment of an information model. In practice, each of `Data1`, `Data2`, and `Data3` could represent a complex set of data, but that’s not important for our purposes here. Let us assume that our business has three activities, `CollectData1`, `CollectData2`, and `CollectData3`, which result in the creation of `Data1`, `Data2`, and `Data3`, respectively. Each of these activities takes the same amount of time and has the same cost in terms of resources required. We will further assume that our business is only interested in `Data3` if both `Data1` and `Data2` meet certain criteria; otherwise, `Data3` is not needed. On average, 90% of cases meet the `Data1` criterion, and 10% of cases meet the `Data2` criterion.

![Fig. 15.1 A simple information structure.](images/B9780443237904000190/f15-01-9780443237904.jpg)

[Fig. 15.1](#Ch015_773-830_B9780443237904000190.xhtml#B-f0010) A simple information structure.

Now, let us consider the question of how the information represented by `Data1`, `Data2`, and `Data3` could evolve. Given the business scenario, it would not seem very sensible to collect `Data3` before trying to collect `Data1` and `Data2`, so we can immediately eliminate some of the possible orderings of `CollectData1`, `CollectData2`, and `CollectData3`. The remaining options are as follows:

1.  (a) `CollectData1` followed by `CollectData2`, then `CollectData3` if needed.
2.  (b) `CollectData2` followed by `CollectData1`, then `CollectData3` if needed.
3.  (c) `CollectData1` and `CollectData2` simultaneously, then `CollectData3` if needed.
4.  (d) `CollectData1`, `CollectData2`, and `CollectData3` in parallel, accepting that we will be carrying out some additional unnecessary work.

We can compare these alternatives by considering an average set of 100 cases. For option (a), we carry out 100 `CollectData1` operations. On average, 90% of the cases meet the `Data1` criterion, so we then carry out 90 `CollectData2` operations. On average, 10% of the cases meet the `Data2` criterion, so we finally carry out nine `CollectData3` operations. The total cost will be 100 + 90 + 9 = 199 units.

For option (b), we carry out 100 `CollectData2` operations. On average, 10% of the cases meet the `Data2` criterion, so we then carry out 10 `CollectData1` operations. On average, 10% of the cases meet the `Data1` criterion, so we finally carry out nine `CollectData3` operations. The total cost will be 100 + 10 + 9 = 119 units.

For option (c), we carry out 100 `CollectData1` operations and 100 `CollectData2` operations. On average, 9% of the cases meet both the `Data1` and the `Data2` criterion, so we finally carry out nine `CollectData3` operations. The total cost will be 100 + 100 + 9 = 209 units.

Finally, for option (d) we carry out 100 `CollectData1` operations, 100 `CollectData2` operations, and 100 `CollectData3` operations. We end up with the same nine cases, but this time at a cost of 300 units. [Fig. 15.2](#Ch015_773-830_B9780443237904000190.xhtml#f0015) summarizes these results.

![Fig. 15.2 Alternative processing strategies.](images/B9780443237904000190/f15-02-9780443237904.jpg)

[Fig. 15.2](#Ch015_773-830_B9780443237904000190.xhtml#B-f0015) Alternative processing strategies.

From this analysis, we can see that option (b) is likely to have the lowest cost. However, our business may have decided that speed of service is more important than lowest cost, and may prefer option (d), despite the higher cost. In fact, the company might choose to offer multiple options, passing the choice between cost and speed on to the customer.
