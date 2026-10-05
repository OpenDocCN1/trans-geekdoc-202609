It also makes other features, like email formatters, easier to write, because they can always assume the data is in a consistent format. Converting “1234567890” to “(123) 456-7890” is fairly easy to do, but if we had to deal with many different-formats and convert each to the (“(###) ### ####” format it would become much harder.

Note: When we talk about normalization we ARE NOT talking about normalization that you might hear about when learning SQL. That form of normalization revolves around avoiding duplicate/unsynced data in your database. We won't be covering that here.

While validation and normalization are not the same, the two are very tightly linked. For starters, it is very hard to separate the two entirely. Whenever we want to verify an email address isn't taken we need to first normalize it, then search our database for a user with that email address. If we didn't normalize first we might end trying to create two users with the same email address. In this case we are doing normalization first, then validation, but there are also cases where we must validate data first, then normalize it. One instance of this is when validating a password has a minimum length; we can't tell how long an original password is once it is hashed (normalized), so we need to validate it first, then normalize it.

This tends to lead to a common pattern where we don't perform one then the other, but instead create a sort of sandwich:

+   1. Some normalization

+   2. All validations

+   3. Remaining normalizations

As a result of the tight dependency between the two, we will be keeping all of this code together in our application.