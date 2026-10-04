```
select avg(contribution) as avg_contrib, state
from contributions
group by state
having avg(contribution)>500
```

# Joining Tables

If you read Chapter 1, you know that relational databases work so well because they segment information. Different tables hold information on different topics, and fields are inserted into the tables to maintain relationships. After you finish the normalization process, it's likely that none of your tables will be usable without the others. That is why you'll need to join tables in your SQL select statements.

# Two-table join (the equi-join)

For the sake of continuity, we're going to reprise a couple of tables first in Chapter 1. Take a look at the familiar tables in Figure 3–11.

| company_id | company_name | address |
|---|---||
| 1 | Big Co Company | 1121 43rd St |
| 2 | Little Co Company | 4444 44th St |

| contract_id | company_id | Name | Title | Phone | Email |
|---|---|---|---|---|---||
| 1 | 1 | Jay Greenspan | Vice President | 415551212 | 1121 43rd St |
| 2 | 1 | Brad Bulder | President | 4155552222 | 4444 44th St |
| 3 | 2 | John Doe | Lucky | 2125556666 | 4444 44th St |

Figure 3–11: Tables in a need of join

If you're looking to do a mailing to all of the people in the contacts, you are going to join the contacts table to the companies table, because the street address is in the companies table (and it's exactly where it should be). company_id column in the contacts table creates the relationship between these tables. And if you join these tables on occasions where the company_id field in the contacts table is equal to the company_id field in the contacts table, all of the information will be at your fingertips.