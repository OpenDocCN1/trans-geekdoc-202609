but few were taking part in the day-to-day discussions about
the future of the DAO.

But a second, more serious problem emerged. A number of
programmers thought they had found a vulnerability in the
DAO code, which allowed a Token holder to withdraw their
own money and pull out of the DAO. It meant a user could trick
the DAO by asking for withdrawals multiple times, during which
the DAO would only check the user’s account balance once. This
attack was not unlike the transaction malleability problem (see
‘What is the transaction malleability problem?’, Chapter 4) in
that by exploiting the bug, an attacker could withdraw double the
amount of money they actually had in their account. (Although
from a code standpoint, the two problems were not at all alike.)
By performing this recursive split attack many successive times,
a criminal could easily drain the DAO of its cryptocurrency.

A week after the vulnerability was announced, an attacker
struck. Nearly $80 million worth of Ether, around a third of
the DAO’s total holdings, was withdrawn. Those holding DAO
Tokens, as well as the larger Ethereum community, panicked,
and the value of Tokens and Ether crashed on cryptocurrency
exchanges.

# Saving the DAO

An immediate and obvious solution was a hard fork of the
Ethereum blockchain. Because the code for the DAO was
within the blockchain, it could not just be rolled back to
reverse the theft. The same blockchain that preserved the DAO
also made the DAO difficult to alter or update. However, if the
entirety of the blockchain was rolled back, all the money could
be refunded to the original investors, and it would be as if the
theft had never occurred.