# CHAPTER 12. NORMALIZING AND VALIDATING DATA

The context; when we look at normalizing our data we are talking about making sure our data is in the format we expect, and if not attempting to transform it into that format. For example we might verify that a phone number matches the format we expect before persisting it in our database, or we might convert all email addresses to their lowercase equivalent.

The reasons for using validation is much more obvious than normalization. We clearly need to verify that data is valid, but why do we care about the format of phone numbers? Does it really matter?

Imagine we are storing each user's phone number in our database. If we didn't normalize the data, we might end up with a table with data similar to below.

| user_id | phone_number |
|---|---|
| 1 | (123) 456-7890 |
| 2 | 123-456-8989 |
| 3 | 12345699999 |

Now imagine that we wanted to search for a user by their phone number. Perhaps we needed a support call, and we go to know which account is linked to that phone number. When we go to search we run into a problem - how do we search for a phone number when they are all stored in a different format? Despite that phone number “1234567890” existing in our database, searching for it in that format wouldnt return any result because it is in a different format.

If we were to instead normalize our data, we could write code that takes in any format like above and trims everything except the digits. That would leave us with a database that is much easier to search.

| user_id | phone_number |
|---|---|
| 1 | 1234567890 |
| 2 | 1234568989 |
| 3 | 12345699999 |