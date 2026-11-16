+   - Scheduled scripts to clean up tables (using, for example, the VACUUM statement in PostgreSQL) whose contents are updated frequently may well prove to be sound investments.

+   - Never use SELECT *. If you know the names of the columns you want, specify them. This will improve performance.

+   - Subselects are easier to put together than INNER or OUTER joins, but nowhere near as efficient. Avoid them if possible (this will also, as a side effect, increase RDBMS portability). If you suspect that subselects may be slowing down your application, try replacing them with either INNER or OUTER joins as appropriate. Consult the documentation of your preferred flavor of database for more information.

Most tips such as the preceding increase speed by only fractions of a second but this really is a case of every little bit helping, especially when you are dealing with pages with a large number of queries.

Don't forget that you will almost certainly need to look outside the PHP script itself to track down the offending SQL query, particularly if you are following the best practice principles described in this book. If you have devised an object model that is heavily dependent on a database back end, you may find that performance tweaks in queries used in that model have unexpected performance gains elsewhere. By the same token, however, when changes are being made to such high-level classes, care should be taken to thoroughly test all components that depend on them to ensure that functionality and behavior remain consistent with expectations.

# ## Fixing Code Holdups

Ultimately, the same principles that apply to optimizing database queries apply here. It's not good enough to know simply which block of code is causing a holdup; you need to work out which PHP statement is being slow and under what circumstances.

# ## Logic Errors

However, sometimes simple errors in application logic are to blame. In such cases, the application does function as expected, so ordinary QA techniques have not registered a bug, but some human error in the code has caused performance to be adversely affected. These are the easiest to fix.

Consider the following example:

```
```
switch ($i) {
case 0:
    array_pop($arMediumArray);
    break;
case 1:
    array_reverse($arAnotherHugeArray);
case 2:
    $arHugeArray = array_unique($arHugeArray);
    break;
};
```
```

As you can probably spot, this code is missing a break statement under the case where $i is equal to 1. This means that the case where $i is equal to 2 will also be executed when $i is equal to 1. In that case, it is only necessary to reverse $arAnotherHugeArray. However, $arHugeArray is also being made unique, as a side effect. It is quite possible that $arHugeArray will never be used again after this switch