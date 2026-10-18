# FIGURE 14.11 Problem with obtaining a specific person’s record

Customers
| Title | Surname | Firstname |
| Mrs | Smith | Lynne |
| Miss | Jones | Ann |
| Mr | Brown | Simon |
| Mr | Smith | David |
| Mr | Bell | Peter |
| Ms | Hall | Liz |
| Mr | Smith | Kevin |
| Mr | Jones | Jack |
| Mr | Green | William |
| Mrs | Smith | Lynne |
| Mr | Bell | Simon |
| Mr | Brown | Ian |

![](bbox=[0.24, 0.18, 0.45, 0.32])

| Title | Surname | Firstname |
| Mrs | Smith | Lynne |
| Mrs | Smith | Lynne |

# FIGURE 14.12 Unique identifier field

Customers
| Id | Title | Surname | Firstname |
| 1 | Mrs | Smith | Lynne |
| 2 | Miss | Jones | Ann |
| 3 | Mr | Brown | Simon |
| 4 | Mr | Smith | David |
| 5 | Mr | Bell | Peter |
| 6 | Ms | Hall | Liz |
| 7 | Mr | Smith | Kevin |
| 8 | Mr | Jones | Jack |
| 9 | Mr | Green | William |
| 10 | Mrs | Smith | Lynne |
| 11 | Mr | Bell | Simon |
| 12 | Mr | Brown | Ian |

![](bbox=[0.24, 0.55, 0.45, 0.67])

| Id | Title | Surname | Firstname |
| 6 | Ms | Hall | Liz |

NOTE Note that our unique key fields can have the same name and values in different database tables.

The types for each of the fields in our Customers table now look like this:

+   - Id int
+   - Title varchar (10)
+   - Surname varchar (100)
+   - Firstname varchar (100)