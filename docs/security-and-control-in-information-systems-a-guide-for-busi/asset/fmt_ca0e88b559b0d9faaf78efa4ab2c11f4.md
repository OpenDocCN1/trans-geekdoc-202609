
## 2.
You have reason to suspect that a group of employees is defrauding the company by setting up false customer details in the accounting system. The accounting is done using a standard package on the office PC server. The system is normally only run in normal office hours, but it is customary for staff to work at other hours, especially towards the end of each accounting period.

You would like to find out whether your suspicions are correct and, if so, to establish who is involved in the fraud. Identify the types of data records you would seek access to in order to further your investigations, and give some examples of the kind of analysis to which you would subject them.

## 3.
Give `three` reasons why it can be preferable *not* to carry out forensic analysis on a ‘live’ system, but to copy the data and take it away for analysis elsewhere.

## 4.
Explain how an ‘electronic watermark’ works. What are the main differences between this and a more conventional watermark, as applied, for example, to a bank note?

# Part 6 Regulation and Standards

## Introduction to Part 6

If I am trying to sell you a door lock, I can take a demonstration model to pieces while you watch, and try to convince you that its innermost workings are so sophisticated and well engineered that it will defeat even the most determined burglar. Alternatively, I could have asked an expert to make a thorough inspection of the product beforehand. If the expert concluded that the lock met certain standards, and you were willing to accept these conclusions, we would both save much time.

Testing for compliance with standards is well established in connection with consumer products. Many bear seals of approval or ‘kite marks’, which indicate that they have passed through some kind of certification process. Numerous efforts have been made to bring the same approach to bear on IS security and control. Standards have been defined for security features in IS products, for security products themselves, and even for the overall security management in an installation.

The criteria for security in firewalls or operating systems are, of course, much more complicated than those for a door lock. Furthermore, the principles of secure door locks are well understood and generally known. If you wished, it would not be too difficult to dismantle the lock and take a look for yourself. In the realm of IS security, the opposite situation applies. Experts do not always agree on how security features should be built, and there is little chance that the average person will be able to evaluate products which consist of circuit boards and lines of code.

In [Part 6](#pt6.xhtml), some of the schemes which have been developed for setting and measuring standards are described. In most cases, these schemes are backed by a regulatory body, and the status of some of these bodies is described. Attention is also given to questions of Data Protection, where regulation is now in force in many parts of the world. The Part concludes with a few pointers to the way things may change in the future.

# chapter fourteen Standards, Codes of Practice and Regulatory Bodies

DOI: [10.4324/9780203992319-21](https://dx.doi.org/10.4324/9780203992319-21)

## 14.1 Frameworks for Regulation

With so much at stake over the integrity and security of information systems, one might expect to find public authorities eager to encourage supervision and regulation. Initiatives have indeed been launched by many governments and international agencies. However, the situation has become confused by a proliferation of would-be regulators, each with their own standards, rules, benchmarks and codes of conduct. Some are sponsored by governments, others by industry alliances, and others by professional and consumer groups. Overall, the results have not proved to be very coherent. On the one hand, there are well-resourced bodies which can enforce their standards using rigorous procedures, and on the other are bodies which, even though they have titles which sound imposing, lack any real substance or authority.

This makes life difficult for anyone looking for ‘official’ guidance or reassurance. There is also much potential for confusion about who is entitled to jurisdiction in any particular instance, and on what basis. There are several reasons for this less than ideal situation, the main ones being as follows.

* Technology continues to advance rapidly, setting a moving target for those who are trying to establish rules and regulations.
* Networked trading is increasingly carried out on a global basis, so regulatory regimes must be world-wide to be effective. This invariably generates intense pressures, as countries press for what they see as being in their national interests.
* Because information systems permeate so many aspects of business, their regulation does not fit neatly into the remit of any one profession, industry sector or government agency.
* At the technical level, there is a huge range of business software and hardware products to choose from. Each organisation sets up its own permutation of products in its own particular way. It is very difficult to predict what kind of vulnerabilities will emerge when all these products are put together in a system, and start to interact.
* Even where there is a desire to set up regulatory regimes, there are severe shortages of people with the appropriate skills and know-how who can put them into practice.

In the face of these obstacles to progress, it is perhaps remarkable that there are many useful and worthwhile measures which have in fact been implemented. Efforts to introduce some degree of orderliness and reassurance can be seen as coming from three different directions, as illustrated in [Figure 14.1](#ch14.xhtml#fig14_1).

![Figure 14.1 ](images/fig14_1_B.jpg)

[Figure 14.1 ](#ch14.xhtml#R_fig14_1)

In the case of *products*, there are two quite different ways in which ‘standards’ can be relevant. First, standards may be applied in the sense of detailed specifications, which indicate exactly how a product should work. These are vital if, for example, a connection is to be set up between two computers across a network. The messages travelling to and fro must be handled in exactly the same way at both ends. This depends on *standardisation*, which will be necessary both for the basic communications protocols, and for any security functions applied to the messages (such as encryption, or message authentication codes).

There is also the more everyday meaning for ‘setting standards’, where the aim is to ensure that products achieve certain levels of *quality*. It is possible, for example, to write a program which faithfully follows a security protocol such as SET or SSL, but which contains coding flaws making the program vulnerable to attack by an unscrupulous person. For security-related products, it is vital that implementations meet standards in *both* senses. Of the two, it is generally much more difficult to prove that the product is of good quality and free from flaws. For this to be tested, the design and coding of the product must be subjected to rigorous scrutiny, and it should be subjected to various kinds of problem situations or malicious attacks, under controlled conditions. The importance of such checks has been demonstrated in a number of studies by Anderson, who has found weaknesses in the implementations of several commercial security systems, including smart cards and teller machines (Anderson [1994](#reference.xhtml#ref_r5)).

Compliance with *standardisation*, on the other hand, is often easier to check, because an incorrect implementation will give rise to obvious errors, or may not even work at all. For example, my not-quite-correct implementation of a standard encryption algorithm is likely to produce output which will defeat the attempts of everyone else to decrypt it, even with the correct algorithm and key.
