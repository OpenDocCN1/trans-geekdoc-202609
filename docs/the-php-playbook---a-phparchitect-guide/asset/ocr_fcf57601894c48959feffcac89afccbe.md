# Application Optimization

```
```sql
EXPLAIN SELECT * FROM guests LEFT JOIN record ON record.id = guests.id WHERE
g uests.firstname = "Pete";
```
```

In our command line instance of MySQL, we get a result set back that does not contain matching records, but instead contains the way MySQL intends to process this query. See Figure 3.2.

```
```text
mysql> EXPLAIN SELECT * FROM guests LEFT JOIN record ON record.id = guests.id WHERE guests.first_name = "Pete";
ERROR 1045 (4S22): Unknown column 'guests.first_name' in 'where clause'
mysql> EXPLAIN SELECT * FROM guests LEFT JOIN record ON record.id = guests.id WHERE guests.firstname = "Pete";
+----+-------------+---------+--------+---------------+---------+---------+-------------------+------+-------------+
| id | select_type | table   | type   | possible_keys | key     | key_len | ref               | rows | Extra       |
+----+-------------+---------+--------+---------------+---------+---------+-------------------+------+-------------+
|  1 | SIMPLE      | guests  | ALL    | NULL          | NULL    | NULL    | NULL              |    4 | Using where |
|  1 | SIMPLE      | record  | eq_ref | PRIMARY       | PRIMARY | 4       | wedding.guests.id |    1 |             |
+----+-------------+---------+--------+---------------+---------+---------+-------------------+------+-------------+
2 rows in set (0.00 sec)
```
```

Straight away we have valuable information about how MySQL is executing this query. Our LEFT JOIN looks pretty good: we have the possible_keys of PRIMARY and it is actually using key PRIMARY; it is only selecting a single row, because it has the ability to make use of an index.

On the other hand, in our first query (the SELECT * FROM guests part), we see that there are no possible keys, and thus it is not using any. We see that it is selecting four records as well. This is a problem, because without any keys, MySQL is not making use of its indices.

The EXPLAIN has shown us the problem: if we are making frequent requests where we select based on the first name, we need to add an index on that column. Adding an index on that column yields the following EXPLAIN results in Figure 3.3:

```
```text
mysql> EXPLAIN SELECT * FROM guests LEFT JOIN record ON record.id = guests.id WHERE guests.firstname = "Pete";
+----+-------------+---------+--------+---------------+-----------+---------+-------------------+------+-------------+
| id | select_type | table   | type   | possible_keys | key       | key_len | ref               | rows | Extra       |
+----+-------------+---------+--------+---------------+-----------+---------+-------------------+------+-------------+
|  1 | SIMPLE      | guests  | ref    | firstName     | firstName | 258     | const             |    1 | Using where |
|  1 | SIMPLE      | record  | eq_ref | PRIMARY       | PRIMARY   | 4       | wedding.guests.id |    1 |             |
+----+-------------+---------+--------+---------------+-----------+---------+-------------------+------+-------------+
2 rows in set (0.00 sec)
```
```

In this example, we see that EXPLAIN shows us MySQL only needs to request one record, because it knows exactly where the record is that we are hunting for. This is