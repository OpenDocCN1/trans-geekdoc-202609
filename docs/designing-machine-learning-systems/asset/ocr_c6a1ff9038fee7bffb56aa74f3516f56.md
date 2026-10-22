data, the way they’re processed is similar across applications. The transactions are inserted as they are generated, and occasionally updated when something changes, or deleted when they are no longer needed.¹⁹ This type of processing is known as *online transaction processing (OLTP)*.

Because these transactions often involve users, they need to be processed fast (low latency) so that they don’t keep users waiting. The processing method needs to have high availability—that is, the processing system needs to be available any time a user wants to make a transaction. If your system can’t process a transaction, that transaction won’t go through.

Transactional databases are designed to process online transactions and satisfy the low latency, high availability requirements. When people hear transactional databases, they usually think of ACID (atomicity, consistency, isolation, durability). Here are their definitions for those needing a quick reminder:

# Atomicity

To guarantee that all the steps in a transaction are completed successfully as a group. If any step in the transaction fails, all other steps must fail also. For example, if a user’s payment fails, you don’t want to still assign a driver to that user.

# Consistency

To guarantee that all the transactions coming through must follow predefined rules. For example, a transaction must be made by a valid user.

# Isolation

To guarantee that two transactions happen at the same time as if they were isolated. Two users accessing the same data won’t change it at the same time. For example, you don’t want two users to book the same driver at the same time.

# Durability

To guarantee that once a transaction has been committed, it will remain committed even in the case of a system failure. For example, after you’ve ordered a ride and your phone dies, you still want your ride to come.

However, transactional databases don’t necessarily need to be ACID, and some developers find ACID to be too restrictive. According to Martin Kleppmann, “systems that do not meet the ACID criteria are sometimes called BASE, which stands for Basically Available, Soft state, and Eventual consistency. This is even more vague than the definition of ACID.”²⁰

¹⁹ This paragraph, as well as many parts of this chapter, is inspired by Martin Kleppmann’s *Designing Data-Intensive Applications.*

²⁰ Kleppmann, *Designing Data-Intensive Applications.*