# Chapter 1: Database Design with MySQL

Industries

| Industry_ID | Industry_name |
| 1 | Utilities |
| 2 | Construction |
| 3 | Banking |

Companies

| Company_id | Company_Name | Industry_id |
| 1 | Big Co Corporation | 1 |
| 2 | Little Co Corporation | 1 |
| 3 | Joe's Utility | 1 |
| 4 | Leadfoot Builders | 2 |
| 5 | Angel's Cement Boots | 2 |
| 6 | Al's Bank | 3 |

| Location_id | Company_id | city |
| 1 | 2 | San Francisco |
| 2 | 2 | New York |
| 3 | 2 | Chicago |
| 4 | 5 | Dallas |

Figure 1-2: Tables with one-to-many relationships

Executives

| ExecID | Exec_first_name | Exec_last_name |
| 1 | Jon | Dust |
| 2 | Melinda | Burns |
| 3 | Larry | Gains |

Assistants

| Asst_id | Exec_id | Asst_first_name | Asst_last_name |
| 1 | 1 | Walter | James |
| 2 | 2 | James | Walter |
| 3 | 3 | Nancy | Els |

Figure 1-3: Tables with a one-to-one relationship

![](bbox=[0.185, 0.078, 0.745, 0.855])