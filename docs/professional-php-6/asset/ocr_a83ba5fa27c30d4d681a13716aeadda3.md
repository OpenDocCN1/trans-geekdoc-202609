# ## Limitations

By now, it is hoped that you have worked your way through the class and, using the examples supplied here, have proven to yourself that it does actually work. Furthermore, the benefits should be clear. A relatively complex class means that your application code can be kept lightweight, simple, and portable.

There are a few limitations to this approach, though.

# ## Impact on the Database

When instantiating the class with an existing ID for reading, updating, or deleting, a `SELECT` query is automatically executed to transfer the contents of the underlying database table entry directly into the class object. This is usually, but not always, desirable.

Consider a hypothetical method in a factory class that produces a collection or array of `User` objects. For example, your `Product` class may well have a method called `GetOrderingUsers()` that will return all those users who have ordered that product. The result may be an array of a hundred or so `User` objects. That's all well and good, but how likely are you to need all 100 of those objects at once? Hardly at all — it's far more likely that you will paginate over them five or so at a time.

By simply creating the object with an existing ID, however, you are forcing a `SELECT` query to be generated. As a result, in the previous example, 100 `SELECT` queries will hammer the database in one go, rendering 95 of them totally redundant.

Database queries are expensive, so anything that can be done to minimize them should (and must) be done.

# ## Unnecessary Queries

When creating a brand-new instance of a `User`, the `INSERT` statement that is built is reasonably smart in that it includes only those columns that have been set; don't set (for example) the `date created` property, and it won't be included in the `INSERT` statement.

Unfortunately, this technique is dependent on the use of the `isset()` method to determine whether or not a property has been assigned a value. That's fine when dealing with a brand-new object; but when working with an existing `User`, every property is assigned a value as it is read from the database. As a result, `isset()` simply replies “yes!” when called; therefore, a call to `Save()` will yield an `UPDATE` statement that updates every column in the table — whether it has actually been changed or not. Not only is this wasteful, it can also have undesirable effects if other applications connected to the database commit changes to other columns between the initial `SELECT` and the final `UPDATE` being executed.

# ## Code Duplication

Finally, read the class source code again. How much of that class is actually specific to the `User` object and/or its underlying table? Not a great deal.

As a result, this complex code is going to end up being duplicated repeatedly for every business object in your application, which disregards the well-respected philosophy of DRY (Don't Repeat Yourself).