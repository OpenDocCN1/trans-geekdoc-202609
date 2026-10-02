1.3 Isolation: Isolation ensures that concurrent transactions do not interfere with each other. Each transaction is executed in isolation, as if it were the only transaction running on the database. This prevents data inconsistencies and conflicts caused by concurrent access.

1.4 Durability: Durability guarantees that once a transaction is committed, its changes are permanent and will survive any subsequent system failures. The committed data is stored in a way that allows it to be recovered and restored even in the event of a system crash or power loss.

# Section 2: Transaction Control Statements

SQL provides transaction control statements to manage transactions explicitly. These statements allow you to define the boundaries of a transaction and control its behavior. The three main transaction control statements are:

2.1 BEGIN TRANSACTION/START TRANSACTION: Marks the beginning of a transaction. It defines the starting point from which all subsequent operations are part of the same transaction.

2.2 COMMIT: Commits the transaction and makes all its changes permanent. It indicates that the transaction has been completed successfully and all its modifications should be saved.