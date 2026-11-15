# 12.14 Summary

The data manipulation aspect of the relational model includes relational algebra and relational assignment (:=). Apart from the use of logical and comparison operators in expressing conditions, the algebra includes nine basic table operations. Comparison operators have precedence over logical operators, which have precedence over table operators.

Table 12.3 listed the six priority levels of the operators: =, <>, <, >, <=, >=; not; and; or; selection (where ...) and projection ([ ]); and finally union \(\cup\), intersection \(\cap\), difference \(-\) (termed except in SQL), Cartesian product \(\times\), natural join \(\bowtie\), and division \(\div\). Parentheses may be used to override this order. A notation common in academic journals is shown on the left, with our notation on the right.

```
\sigma_c(T) \equiv T \text{ where } c
\pi_{a,b,...}(T) \equiv T [a,b,...]
A \bowtie_c B \equiv (A \times B) \text{ where } c
```

Operators on the same precedence level are left associative (evaluated in left to right order as they appear in an expression). Our priority convention is designed to minimize the use of parentheses and is stronger than some other conventions in use. If in doubt, or purely for the sake of clarity, feel free to add extra parentheses.

A relational DBMS has the relational table as its only essential data structure and supports relational selection, projection, and join without needing to specify access paths.

The table operators are summarized visually in Fig. 12.64. Many different notations exist for selection, projection, and joins.

The laws for the comparison and logical operators are well known. Table 12.17 sets out most of the main laws for the table operators. Some of these have not been discussed; their proof is left as an easy exercise. Here \(A, B\), and \(C\) are tables, \(c\) is a condition, and \(p\) is a projection list of attributes.

Various other distributive laws could be stated; recall, however, that \([\) does not distribute over \(\cap\) or \(-\).

SQL is the dominant language used in relational DBMSs, and various versions have been standardized over the years, with the most recent being SQL:2023. Most commercial SQL dialects support all of SQL-89, some of the extra features in SQL-92 and SQL:1999, and some of their own special features.

Database objects such as tables and columns may be named using standard identifiers or delimited identifiers (allowing any characters inside double quotes). Database fields may be defined in terms of predefined data types (e.g., varchar(20)).