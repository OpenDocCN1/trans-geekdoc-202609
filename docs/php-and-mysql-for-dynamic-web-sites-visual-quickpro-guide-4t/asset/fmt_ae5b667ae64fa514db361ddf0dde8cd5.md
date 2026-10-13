
The query should reveal the contents of the table as they originally were.

**8.** Repeat Steps 2 through 4.

To see what happens when the transaction is committed, the two `UPDATE` queries will be run again. Be certain to start the transaction first, though, or the queries will automatically take effect!

**9.** Commit the transaction and confirm the results:

```
COMMIT;
SELECT * FROM accounts;
```

Once you enter `COMMIT`, the entire transaction is permanent, meaning that any changes are now in place. `COMMIT` also ends the transaction, returning MySQL to autocommit mode.

***

Tip

One of the great features of transactions is that they offer protection should a random event occur, such as a server crash. Either a transaction is executed in its entirety or all of the changes are ignored.

***

Tip

To alter MySQL’s autocommit nature, type

```
SET AUTOCOMMIT=0;
```

Then you do not need to type `START TRANSACTION` and no queries will be permanent until you type `COMMIT` (or use an `ALTER`, `CREATE`, etc., query).

***

Tip

You can create *savepoints* in transactions:

```
SAVEPOINT savepoint_name;
```

Then you can roll back to that point:

```
ROLLBACK TO SAVEPOINT savepoint_name;
```

***

### Database Encryption

Up to this point, pseudo-encryption has been accomplished in the database using the `SHA1()` function. In the *sitename* and *forum* databases, the user’s password has been stored after running it through `SHA1()`. Although using this function in this way is perfectly fine (and quite common), the function doesn’t provide *real* encryption: the `SHA1()` function returns a *representation* of a value (called a *hash*), not an encrypted version of the value. By storing the hashed version of some data, comparisons can still be made later (such as upon login), but the original data cannot be retrieved from the database. If you need to store data in a protected way while still being able to view the data in its original form at some later point, other MySQL functions are necessary.

MySQL has several encryption and decryption functions built into the software. If you require data to be stored in an encrypted form that can be decrypted, you’ll want to use `AES_ENCRYPT()` and `AES_DECRYPT()`. The `AES_ENCRYPT()` function is considered to be the most secure encryption option.

These functions take two arguments: the data being encrypted or decrypted and a *salt* argument. The salt argument is a string that helps to randomize the encryption. Let’s look at the encryption and decryption functions first, and then I’ll return to the salt.

To add a record to a table while encrypting the data, the query might look like

```
INSERT INTO users (username, pass)
VALUES ('troutster', AES_ENCRYPT('mypass', 'nacl19874salt!'))
```

The encrypted data returned by the `AES_ENCRYPT()` function will be in binary format. To store that data in a table, the column must be defined as one of the binary types (e.g., `VARBINARY` or `BLOB`).

To run a login query for the record just inserted (matching a submitted username and password against those in the database), you would write

```
SELECT * FROM users WHERE
username='troutster' AND
AES_DECRYPT(pass, 'nacl19874salt!') = 'mypass'
```

This is equivalent to:

```
SELECT * FROM users WHERE
username = 'troutster' AND
AES_ENCRYPT('mypass', 'nacl19874salt!') = pass
```

Returning to the issue of the *salt*, the exact same salt must be used for both encryption and decryption, which means that the salt must be stored somewhere as well. Contrary to what you might think, it’s actually safe to store the salt in the database, even in the same row as the salted data. This is because the purpose of the salt is to make the encryption process harder to crack (specifically, by a “rainbow” attack). Such attacks are done remotely, using brute force. Conversely, if someone can see everything stored in your database, you have bigger problems to worry about (i.e., all of your data has been breached).

Finally, to get the maximum benefit from “salting” the stored data, each piece of stored data should use a unique salt, and the longer the salt the better.

To put all this together, let’s add PIN and salt columns to the *banking.customers* table, and then store an encrypted version of each customer’s PIN.

#### To encrypt and decrypt data

**1.** Access MySQL and select the *banking* database:

**2.** Add the two new columns to the *customers* table ![Image](graphics/circle-a.jpg):

```
ALTER TABLE customers ADD COLUMN pin VARBINARY(16) NOT NULL;
ALTER TABLE customers ADD COLUMN nacl CHAR(20) NOT NULL;
```

![Image](graphics/07_figure_44_a.jpg)

![Image](graphics/circle-a.jpg)Two columns are added to the *customers* table.

The first column, *pin*, will store an encrypted version of the user’s PIN. As `AES_ENCRYPT()` returns a binary value 16 characters long, the *pin* column is defined as `VARBINARY(16)`. The second column stores the salt, which will be a string 20 characters long.

**3.** Update the first customer’s PIN ![Image](graphics/circle-b.jpg):

```
UPDATE customers
SET nacl = SUBSTRING(MD5(RAND()), -20)
WHERE customer_id=1;
UPDATE customers
SET pin=AES_ENCRYPT(1234, nacl)
WHERE customer_id=1;
```

![Image](graphics/07_figure_45_b.jpg)

![Image](graphics/circle-b.jpg)A record is updated, using an encryption function to protect the PIN.

The first query updates the customer’s record, adding a salt value to the *nacl* column. That random value is obtained by applying the `MD5()` function to the output from the `RAND()` function. This will create a string 32 characters long, such as *4b8bb06aea7f3d162ad5b4d83687e3ac*. Then the last 20 characters are taken from this string, using `SUBSTRING()`.

The second query stores the customer’s PIN—1234, using the already-stored *nacl* value as the salt.

**4.** Retrieve the PIN in an unencrypted form ![Image](graphics/circle-c.jpg):

```
SELECT customer_id, AES_DECRYPT(pin,
nacl) AS pin FROM customers
WHERE customer_id=1;
```

![Image](graphics/07_figure_46_c.jpg)

![Image](graphics/circle-c.jpg)The record has been retrieved, decrypting the PIN in the process.

This query returns the decrypted PIN for the customer with a *customer_id* of 1. Any value stored using `AES_ENCRYPT()` can be retrieved (and matched) using `AES_DECRYPT()`, as long as the same salt is used.

**5.** Check out the customer’s record without using decryption ![Image](graphics/circle-d.jpg):

```
SELECT * FROM customers
WHERE customer_id=1;
```

![Image](graphics/07_figure_47_d.jpg)

![Image](graphics/circle-d.jpg)Encrypted data is stored in an unreadable format (here, as a binary string of data).

As you can see in the figure, the encrypted version of the PIN is unreadable.

***

Tip

As a rule of thumb, use `SHA1()` for information that will never need to be viewable, such as passwords and perhaps usernames. Use `AES_ENCRYPT()` for information that needs to be protected but may need to be viewable at a later date, such as credit card information, Social Security numbers, addresses (perhaps), and so forth.

***

Tip

As a reminder, never storing credit card numbers and other high-risk data is always the safest option.

***

Tip

The `SHA2()` function is an improvement over `SHA1()` and should be preferred for hashing data. I only chose not to use it in this book because `SHA2()` requires MySQL 5.5.5 or later.

***

Tip

The same salting technique can be applied to `SHA1()`, `SHA2()`, and other functions.

***

Tip

Be aware that data sent to the MySQL server, or received from it, could be intercepted and viewed. Better security can be had by using an SSL connection to the MySQL database.

***

### Review and Pursue
