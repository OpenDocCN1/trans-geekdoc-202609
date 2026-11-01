
Bitcoin relies on a public–private key cryptography, explained in greater technical detail in a subsequent chapter. Here we provide a simple illustration of how it works in the context of the above example, as an introduction to the underlying process. Briefly, there are two types of keys: private key and public key. Private key is known only to the user, whereas the public key is widely shared. In [Fig. 2.4](#CH002.html#fig4), Adam sends three Bitcoins to Bob by publishing the message in the Bitcoin network along with the reference to the transaction where he had obtained those three Bitcoins in the first place. The message is encrypted using Adam’s private key to indicate that the message came from him. When Bob transfers three Bitcoins to Chris, he likewise publishes a message using his private key, indicating that he is transferring to Chris the Bitcoins he had received from Adam. A Bitcoin transaction does not clear until it has been added to the consensus blockchain. In [Table 2.1](#CH002.html#tab1), it is shown that as of December 2019, a new block was being added every nine minutes. Once the transactions are recorded in a block, they are validated and are included in every subsequent block, hence form immutable permanent records.

## 2.7. BLOCKCHAIN BEYOND BITCOIN

As we have discussed throughout this chapter blockchain was the essential technology, the infrastructure, which enabled the growth of Bitcoin. Blockchain enabled Bitcoin transactions without the need for a third-party verification. Bitcoin perhaps could have functioned as a cryptocurrency, through a third-party verification scheme, much like PayPal. However, the blockchain technology enabled transactions via Bitcoin to occur without the third party, thereby increasing the popularity and functionality of Bitcoin.

**Fig. 2.5:    Bitcoin : Blockchain : Car : Road.**

![image](images/C02-FIG5.jpg)

To fully appreciate the relationship between Bitcoin and blockchain, consider the relationship between the invention of the car and the paved road. At the turn of twentieth century, when cars were first introduced, these cars had to mostly drive on cobblestone paths meant for horse-drawn carriages. While the cars could be driven on unpaved roads. (Panel 1, [Fig. 2.5](#CH002.html#fig5)), the functionality was limited. The car could not reach its full potential or speed when driving on the unpaved road, and the ride was not as comfortable. Development of asphalt roads and highways in the United States, circa 1920–1950 (Panel 2, [Fig. 2.5](#CH002.html#fig5)) tremendously aided the performance and functionality of the car. The car could drive much faster on the asphalt road than on a grassy meadow or a cobblestone pavement, and the ride was much more comfortable. However, when paved roads became common, existing or archaic modes of transportations were adapted for improved performance on the asphalt paved road. Even centuries old bullock carts could perform better on these roads when fitted with rubber tires (Panel 3, [Fig. 2.5](#CH002.html#fig5)).

Similarly, the introduction of blockchain and its incorporation into Bitcoin enabled transactions to occur between two parties without the need of a trusted third party. This reduced transaction costs, similar to reducing friction, which led to the flourishing popularity of Bitcoin akin to the performance of the car on a paved road. However, once the blockchain technology has been developed, features of it could be harnessed to improve existing business processes or develop new applications that were previously intractable. In the subsequent chapters of this book we discuss those additional applications of blockchain, beyond that of Bitcoin.

### NOTES

[1.](#CH002.html#ifn1) The seminal paper on blockchain was self-published on the internet as a White Paper and can be found at [https://bitcoin.org/bitcoin.pdf](https://bitcoin.org/bitcoin.pdf) (accessed on January 2020).

[2.](#CH002.html#ifn2) Data obtained from [https://www.marketplacepulse.com/stats/us-ecommerce/us-e-commerce-growth-rate-55](https://www.marketplacepulse.com/stats/us-ecommerce/us-e-commerce-growth-rate-55).

[3.](#CH002.html#ifn3) See [http://www.bbc.co.uk/ahistoryoftheworld/objects/F3oFoFDuTx-rzhCkCL9_BA](http://www.bbc.co.uk/ahistoryoftheworld/objects/F3oFoFDuTx-rzhCkCL9_BA) (accessed on January 2020). At the website there is a picture of an ancient Chinese banknote with the inscription that reads, “to counterfeit is death.”

[4.](#CH002.html#ifn4) National Public Radio did a feature on Yap money, available at: [https://www.npr.org/sections/money/2011/02/15/131934618/the-island-of-stone-money](https://www.npr.org/sections/money/2011/02/15/131934618/the-island-of-stone-money) (accessed on January 2020).

[5.](#CH002.html#ifn5) Milton Friedman (1994) discussed the Yap money in his book *Money Mischief* – *Episodes in Monetary History*.

[6.](#CH002.html#ifn6) The features and importance of “proof of work” will be discussed in greater detail in a subsequent chapter.

[7.](#CH002.html#ifn7) This bullet point list is adapted from the original publication of Satoshi Nakamoto.

[8.](#CH002.html#ifn8) Hashing is a common practice in computer science, whereby the original data is masked by another value, say transformation of letters to numbers. It is quite common in cryptography.

[9.](#CH002.html#ifn9) [https://ccsearch.creativecommons.org/photos/b43e6343-64e5-433a-b4fb-8d68ae5dc6fc](https://ccsearch.creativecommons.org/photos/b43e6343-64e5-433a-b4fb-8d68ae5dc6fc); Sand and Tsunamis; [https://ccsearch.creativecommons.org/photos/a03c3b4d-4c69-4568-b097-29920736b325](https://ccsearch.creativecommons.org/photos/a03c3b4d-4c69-4568-b097-29920736b325); JeepersMedia; [https://ccsearch.creativecommons.org/photos/ee1d50cb-286f-4893-b499-3e3522067db9](https://ccsearch.creativecommons.org/photos/ee1d50cb-286f-4893-b499-3e3522067db9).

[10.](#CH002.html#ifn10) [https://ccsearch.creativecommons.org/search?license=&license_type=&categories=&extension=&aspect_ratio=&size=&source=&q=yap%20money&searchBy=&mature=/](https://ccsearch.creativecommons.org/search?license=&license_type=&categories=&extension=&aspect_ratio=&size=&source=&q=yap%20money&searchBy=&mature=/)

# 3. BASIC PRIMER ON BLOCKCHAIN TERMINOLOGY

## 3.1. INTRODUCTION

As discussed in the previous chapter, blockchain is an enabling technology, in that it facilitates immutable record-keeping. The record itself could be of any object, from sport records, educational certification, ownership or monetary transaction. The most well-known application of this new record-keeping mechanism is that in cryptocurrency, hence many people associate blockchain with Bitcoin. However, as discussed in the previous chapter, it is important to remember that Bitcoin is merely an implementation of blockchain technology.

Accessibility, anonymity, immutability and real-time sharing of information are some of the key features that make blockchain technology suitable for record-keeping in complex business arrangements. Due to these properties, blockchain enables transfer of money, property, data or any other asset type between two parties securely, anonymously and immutably. Moreover, this is achieved without having to go through expensive intermediaries, who normally would charge agent or broker fees to mediate such transactions. One of the many accepted scientific definition of blockchain is[¹](#CH003.html#fn1)

*a peer-to-peer network which timestamps records by hashing them into an ongoing chain of hash-based proof-of-work, forming a record that cannot be changed without redoing the proof-of-work.*
