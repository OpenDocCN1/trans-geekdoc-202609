
# Communications Media Vulnerabilities

Communications media are known to be vulnerable to data corruption. Simple factors such as weather and trees can interfere with clean transmission. For this reason, communications protocols include features to check for and correct, at least some, errors in transmission. The `TCP/IP` protocol suite (which we describe later in this chapter), is used for most Internet data communication. `TCP/IP` has extensive features to ensure that the receiver gets a complete, correct, and well-ordered data stream, despite any errors during transmission.

***

**Network data corruption occurs naturally because of minor failures of transmission media. Corruption can also be induced for malicious purposes. Both must be controlled.**

***

In this section we describe some of the modification failures to which communications are vulnerable.

## Sequencing

A **sequencing** attack or problem involves permuting the order of data. Most commonly found in network communications, a sequencing error occurs when a later fragment of a data stream arrives before a previous one: Packet 2 arrives before packet 1.

Sequencing errors are actually quite common in network traffic. Because data units are routed according to available routing information, when packet 1 is sent, the best route, which is the route chosen, goes via node C. Subsequently the router learns node C is no longer optimal, so when packet 2 is to be sent, the routing goes via node D. The second route is indeed superior, so much so that packet 2 arrives before packet 1. Congestion, network interference, faulty or failed equipment, and performance problems can easily cause these kinds of speed difficulties.

Network protocols such as the `TCP` suite ensure the proper ordering of traffic. However, application programs do not always detect or correct sequencing problems within the data stream. For example, if an application handles input from many concurrent clients at a shopping site, the application must ensure that individual orders are constructed correctly, regardless of the order in which the pieces of orders arrived.

## Substitution

A **substitution** attack is the replacement of one piece of a data stream with another. Nonmalicious substitution can occur if a hardware or software malfunction causes two data streams to become tangled, such that a piece of one stream is exchanged with the other stream.

Substitution errors can occur with adjacent cables or multiplexed parallel communications in a network; occasionally, interference, called crosstalk. allows data to flow into an adjacent path. Metallic cable is more subject to crosstalk from adjacent cables than is optical fiber. Crossover in a multiplexed communication occurs if the separation between subchannels is inadequate. Such hardware-induced substitution is uncommon.

A malicious attacker can perform a substitution attack by splicing a piece from one communication into another. Thus, Amy might obtain copies of two communications, one to transfer $100 to Amy, and a second to transfer $100,000 to Bill, and Amy could swap either the two amounts or the two destinations. Substitution attacks of this sort are easiest to carry out with formatted communications. If Amy knows, for example, that bytes 24–31 represent the account number, she knows how to formulate a new message redirecting money to her account.

The obvious countermeasure against substitution attacks is encryption, covering the entire message (making it difficult for the attacker to see which section to substitute) or creating an integrity check (making modification more evident). In [Chapter 12](#ch12.html#ch12) we describe chaining, a process in which each segment of a message is encrypted so that the result depends on all preceding segments. Chaining prevents extracting one encrypted piece (such as the account number) and replacing it with another.

Not all substitution attacks are malicious, as the example of [Sidebar 6-6](#ch06.html#ch06sb06) describes.

***

### Sidebar 6-6 Substitute Donors

The British National Health Service (`NHS`) maintains a database of potential organ donors in the United Kingdom. According to an article in *The Register* 12 April 2010, the organ donor status field was incorrectly entered for people who registered their organ donation preferences while applying for a driver’s license. Some 400,000 data fields were corrected by the `NHS` and another 300,000 people had to be contacted to determine the correct value.

According to a subsequent review [[DUF10]](#bib01.html#bib_168), the error arose in 1999 and went unnoticed from then until 2010. The `NHS` receives data from three sources: hospitals, doctors, and the drivers’ license office. When applying for a driver’s license or registering with a doctor or hospital, an applicant can mark boxes specifying which organs, if any, the applicant wishes to donate after death. The record transmitted to `NHS` from any source contains identification data and a seven-digit number coded as 1 for no and 2 for yes. However, the order of the organs listed on the license application is different from the order the other two sources use, which was properly handled by software before 1999. In a software upgrade in 1999, all inputs were erroneously processed by the same order.

The review after discovery of the error recommended enhanced testing procedures, notification of all affected parties whenever a programming change was to be implemented, and periodic auditing of the system, including sample record validation.

***

## Insertion

An **insertion** attack, which is almost a form of substitution, is one in which data values are inserted into a stream. An attacker does not even need to break an encryption scheme in order to insert authentic-seeming data; as long as the attacker knows precisely where to slip in the data, the new piece is encrypted under the same key as the rest of the communication.

## Replay

In a **replay** attack, legitimate data are intercepted and reused, generally without modification. A replay attack differs from both a wiretapping attack (in which the content of the data is obtained but not reused) and a man-in-the-middle attack (in which the content is modified to deceive two ends into believing they are communicating directly).

In real life, a bank prevents someone from depositing the same check twice by marking the physical check, but with electronic deposits, for which the depositor takes a check’s picture with a smartphone, preventing reuse is more difficult. The classic example of a replay attack involves financial transactions in the following way. An unscrupulous merchant processes a credit card or funds transfer on behalf of a user and then, seeing that the transfer succeeded, resubmits another transaction on behalf of the user.

With a replay attack, the interceptor need not know the content or format of a transmission; in fact, replay attacks can succeed on encrypted data without altering or breaking the encryption. Suppose a merchant has a credit card terminal with built-in encryption, such that the user’s card number, perhaps a `PIN`, the transaction amount, and merchant’s identifier are bound into a single message, encrypted, and transmitted to the credit processing center. Even without breaking the encryption, a merchant who taps the communications line can repeat that same transaction message for a second transfer of the same amount. Of course, two identical transactions to one merchant would be noticeable and natural for the client to dispute, and the net gain from repeating a single credit purchase would be relatively small. Nevertheless, possible repetition of a transaction would be a vulnerability.
