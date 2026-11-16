The `bindValue()` method works similarly, but it won’t accept a PHP variable as a parameter — it wants a hard-coded value instead. Similarly, `bindParam()` will fail if you try to pass it a hard-coded value — it wants a variable passed by reference.

There are four key benefits to this approach.

First (and foremost) is the benefit of abstraction. If MS SQL Server likes its parameterization to be represented using square brackets (`[` and `]`), and PostgreSQL likes single quotes (`'` and `'`), then a natural barrier to portability is introduced. By having PDO and the database itself handle such database-specific nuances, this particular barrier is removed.

The second issue is the particularly hot topic of security — specifically, vulnerability to SQL injection attacks. Web-based applications that pass HTTP `POST` or `GET` parameters toward a database as statement input parameters are particularly vulnerable to such an attack. Input parameters can be manipulated adversely in an attempt to execute malicious queries other than those originally intended. For more information, see the informative Wikipedia article at `http://en.wikipedia.org/wiki/SQL_injection`.

One solution to avoiding SQL injection is _escaping_ — that is, pre-parsing HTTP `POST` and `GET` parameters to escape any characters with special meaning in SQL (such as square brackets and apostrophes). This is not foolproof, however, especially when using unusual non-ASCII character sets such as Unicode.

It also introduces a portability problem — compare databases that escape apostrophes using a backslash (`\'`) versus those that escape by using double-entry (`''`).

Using parameterized prepared statements closes this issue down once and for all. The escaping of values (including the encapsulation in delimiters as needed) is handled entirely by PDO and the database itself. The onus is therefore no longer on the developer to mitigate against SQL injection throughout — which, on a large project, can be a serious boon, even to an experienced developer.

Finally, there is the issue of performance. By using a single prepared statement, the underlying database can be made aware that a popular query (such as the example shown earlier) in an application is, in fact, structurally the same throughout, with only a parameter or set of parameters changing each time. This enables the database’s own caching and memory-management techniques to self-optimize to allow those queries to execute as quickly as possible each time. When parameters are passed in outside of the database engine’s consciousness, such optimizations cannot occur.

# ## Write-Only Statements

In the previous examples, you’ve learned how to use PDO to extract data from the database using `SELECT` statements; but, naturally, not all statements result in data being returned — `UPDATE`, `DELETE` and `INSERT` statements spring to mind.