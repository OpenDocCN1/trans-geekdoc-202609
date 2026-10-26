Employees table successfully dropped.

Employees table successfully created.

All data inserted successfully.

Executing query: SELECT * from Employees
order by last_name, first_name

Number of rows in query result = 7

|  | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 2 | Cox | Jeffrey | 225 | 0 | 1 |
| 1 | 3 | McNulty | Kate | 214 | 3 | 2 |
| 2 | 51 | Murphy | Jim |  | 1 | 1 |
| 3 | 1 | Schwendiman | Joe | 2204 | 3 | 1 |
| 4 | 4 | Schwendiman | Ryan | 128 | 1 | 1 |
| 5 | 58 | Schwendiman | Scott | 234 | 1 | 1 |
| 6 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

Executing query: SELECT * from Employees
where ( mgr_id = 3 )

Number of rows in query result = 2

|  | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 1 | Schwendiman | Joe | 2204 | 3 | 1 |
| 1 | 3 | McNulty | Kate | 214 | 3 | 2 |

Executing query: SELECT * from Employees
where ( dept_id = 2 )

Number of rows in query result = 1

|  | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 3 | McNult | Kate | 214 | 3 | 2 |