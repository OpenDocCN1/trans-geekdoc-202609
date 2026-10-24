series of functions for setting communications parameters and exchanging data.

In some cases, a driver is configured to request periodic transfers, and applications can read the retrieved data or provide data to send in these transfers. During enumeration, the operating system initiates transfers. Other transfers require an application to request to send or receive data.

# ## Transactions: the Building Blocks of a Transfer

Figure 2-3 shows the elements of a typical transfer. A lot of the terminology here begins to sound the same. There are transfers and transactions, stages and phases, data transactions and data packets, Status stages and handshake

![](bbox=[0.309, 0.387, 0.869, 0.818])

Figure 2-3: A USB transfer consists of transactions. The transactions in turn contain packets, and the packets contain a packet identifier (PID), PID-check bits, and sometimes additional information.