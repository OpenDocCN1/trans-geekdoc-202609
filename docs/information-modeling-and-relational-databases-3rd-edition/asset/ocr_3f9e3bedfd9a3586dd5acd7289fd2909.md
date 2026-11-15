would produce a result such as:

| orderld | Xorder |
|---|---|
| 9876 | `<order>`
`<customer> Widgets Inc </customer>`
`<date> 2007-12-12 </date>`
`</order>` |
| 9877 | `<order>`
`<customer> Thingummy Co </customer>`
`<date> 2007-08-15 </date>`
`</order>` |

If preservation of the case in SQL names is important, they should be aliased as delimited identifiers. Regular identifiers are likely to be mapped to all uppercase in some implementations. For example, the _date_ element in the example just given could appear as `<DATE> ... </DATE>` instead of `<date> ... </date>`.

An equivalent result table could be produced in SQL Server as follows:

```
select o.orderld,
(select o.custName 'customer', o.date 'date'
from orders as o
for xml path ('order'), type) as Xorder
from orders as o
where orderid > 9800
```

SQL Server uses various **for xml** ... constructs to convert relational data to XML. The **for xml path** variant gives full control over how the XML structure is to be generated on a column-by-column basis. The **type** parameter specifies that the result should be of type **xml**, as opposed to its string equivalent.

Returning to SQL/XML, the **xmlagg** function is an aggregate function, similar to SQL’s `sum`, `avg`, etc. It returns a single value from a given bag of values, which must be the result of an `xml` type expression. The resulting `xml` values are concatenated to produce a single `xml` value. Optionally, an `order by` clause can be used to order the results before concatenating, using a similar syntax to SQL. Any null produced is dropped before concatenating. If all the results of the expression are **null**, or the bag is empty, the result of the **xmlagg** function is the `null` value. The basic syntax is as follows:

```
xmlagg ( XML-value-expression [ order by sort-specification ]
[ returning { content | sequence } ] )
```

As an example of the `xmlagg` function, suppose we have an “Orders” table and want to group by customer, showing, for each customer, an element for each order placed by that customer. For simplicity, we’ll just assume that both orders and customers are represented by a simple ID value. We could construct the result as follows: