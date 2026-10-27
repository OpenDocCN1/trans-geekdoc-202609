# 15.2 A Factoring Challenge

The first part of this chapter was concerned with nonfactoring attacks on RSA. We now take the direct approach. Various algorithms for factoring are considered, although none are quick enough to break RSA with the size primes presently used. Factoring is especially hard when the number is a product of two large primes. To help convince yourself that this is a difficult problem, try to factor

```
25195908475657893494027183240048398571429282126204
03202777713783604366202070759555626401852588078440
69182906412495150821892985591491761845028084891200
72844992687392807287776735971418347270261896375014
97182469116507761337985909570009733045974880842840
17974291006424586918171951187461215151726546322822
16869987549182422433637259085141865462043576798423
38718477444792073993423658482382428119816381501067
48104516603773060562016196762561338441436038339044
1495263443219011467574445417842402092461615723350
7787077498171257724679629263865367328991215483143
8167899885040453640235273819513786365643912120103
97122822120720357
```

This number has 617 digits in base 10, but it’s called RSA-2048, because it has that many bits in base 2. There was once a $200,000 prize offered by RSA Security for anyone who could find the two prime factors and explain how they did it. The RSA factoring challenge has expired, but they did give away prizes for the factorization of other, smaller products. See Table 15.1 for sizes and prizes.

# Table 15.1  RSA Factoring Challenge Prizes

| Challenge Number | Prize ($US) | Status | Submission Date | Submitters |
|---|---:|---|---|---|
| RSA-576 | $10,000 | Factored | December 3, 2003 | J. Franke et al. |
| RSA-640 | $20,000 | Factored | November 2, 2005 | F. Bahr et al. |
| RSA-704 | $30,000 | Not factored |  |  |
| RSA-768 | $50,000 | Not factored |  |  |
| RSA-896 | $75,000 | Not factored |  |  |
| RSA-1024 | $100,000 | Not factored |  |  |
| RSA-1536 | $150,000 | Not factored |  |  |
| RSA-2048 | $200,000 | Not factored |  |  |

*Note:* The website that was the source for this table has been archived at http://web.archive.org/web/20071126084720/http://www.rsa.com:80/rsalabs/node.asp?id=2093.