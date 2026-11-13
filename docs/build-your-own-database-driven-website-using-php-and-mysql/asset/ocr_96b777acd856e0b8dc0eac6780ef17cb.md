# # LOCKING TABLES

Notice how, in the UPDATE query given above (and repeated here for convenience), we use the existing value of TimesViewed and add one to it to set the new value.

```
```php
$sql = "UPDATE Jokes SET TimesViewed=TimesViewed+1 WHERE ID=$id";
```
```

If you hadn't known that you were allowed to do this, you might have done a separate SELECT to get the current value, add one to it, and then do an UPDATE using that newly calculated value. Besides the fact that this requires two queries instead of one, and thus will take about twice as long, there is a danger to using this method. What if, while that new value was being calculated, someone else viewed the same joke? The PHP script would be run a second time for that new request. When it performed the SELECT to get the "current" value of TimesViewed, it would retrieve the same value as the first script did, because the value had not yet been updated. Both scripts would then add one to the same value, and write the new value into the table. See what happens? Two users view the joke, but the Timesviewed counter only increments by one!

In some situations, this kind of fetch-calculate-update procedure cannot be avoided, and the possibility of interference between simultaneous requests (of the nature described above) must be dealt with. Other situations where this may be necessary include cases where you need to update several tables in response to a single action (e.g. updating inventory and shipping tables in response to a sale on an eCommerce Web site).

By locking the table or tables with which you're working in a multiple-query operation, you can obtain exclusive access for the duration of that operation to prevent potentially damaging interference from concurrent operations. The syntax for locking a table is fairly simple:

```
LOCK TABLES tblName READ/WRITE
```

As shown, when you lock a table, you must specify whether you want a read lock or a write lock. The former prevents other processes from making changes to the table, but allows others to read the table. The latter stops all other access to the table.

When you're done with a table you have locked, you must release the lock to give other processes access to the table again:

```
UNLOCK TABLES
```

A LOCK TABLES query implicitly releases whatever locks you may already have; so to safely perform a multi-table operation, you must lock all the tables you'll use with a single query. Here's what the PHP code might look like for the eCommerce application we mentioned above: