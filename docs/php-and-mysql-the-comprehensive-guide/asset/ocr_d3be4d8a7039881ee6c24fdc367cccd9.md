| name | email | date | entry |
|---|---|---|---|
| Tobias | tobias@xy.zzz | 2025-01-02 | This isn't exactly the place to be ... |
| Christian | christian@xy.zzz | 2025-01-01 | A warm welcome! The guestbook is open. |

Table 17.6 Result of the "SELECT" Query (Cont.)

It is also possible to sort by several columns. The following query sorts first by the name of the contributor (ascending), then by date (descending):

```
SELECT name, email, date, entry FROM entry ORDER BY name ASC, date DESC
```

| name | email | date | entry |
|---|---|---|---|
| Christian | christian@xy.zzz | 2025-01-03 | There is some truth in that. |
| Christian | christian@xy.zzz | 2025-01-01 | A warm welcome! The guestbook is open. |
| Tobias | tobias@xy.zzz | 2025-01-02 | This isn't exactly the place to be ... |

Table 17.7 Result of the "SELECT" Query

The previous queries always returned all rows from the table. But often, you are only looking for a selection of all the data. The `WHERE` clause can be used for this. Behind it, you specify one or more conditions that must be fulfilled by the data to be returned. All Boolean expressions are possible, including OR and AND. Here you can see a query that returns all of Tobias's entries (well, the only one):

```
SELECT * FROM entry WHERE name = 'Tobias'
```

| name | email | date | entry |
|---|---|---|---|
| Tobias | tobias@xy.zzz | 2025-01-02 | This isn't exactly the place to be ... |

Table 17.8 Result of the "SELECT" Query

The comparison of character strings is usually _case-sensitive_; that is, a distinction is made between upper- and lowercase. If you do not want this, you must use the `LIKE` operator instead of the equality operator:

```
SELECT * FROM entry WHERE name LIKE 'tobiAS'
```

| name | email | date | entry |
|---|---|---|---|
| Tobias | tobias@xy.zzz | 2025-01-02 | This isn't exactly the place to be ... |

Table 17.9 Result of the "SELECT" Query