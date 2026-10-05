
# 12.8 SECURE ELECTRONIC TRANSACTION

Secure Electronic Transaction (SET) is a protocol for securing Credit Card transactions over the Internet. It was jointly developed by VISA and Mastercard, with the involvement of some other companies like IBM, Microsoft, Netscape, VeriSign. The protocol provides privacy to online transactions over the Internet. Also, it provides mutual authentication to the consumers and the merchants involved in electronic commerce. It makes use of both Symmetric and Public-Key Cryptography for the communications over the Internet. Figure 12.14 displays participants involved in Secure Electronic Transaction (SET).

![](img/d3b56042c756fbcc011ff06f1b9f53f0_484_0.png)

FIGURE 12.14 Participants in Secure Electronic Transaction (SET).

1. Customer (Cardholder): A customer (known as Cardholder) is an authorized holder of a Credit Card of some brand, say MasterCard or Visa, and so on, issued by a bank (known as Issuer). Each Cardholder will have an account linked to the credit card, opened in the Issuer Bank. The cardholder is also issued an X.509 V3 Public Key certificate, signed by the issuer bank. The certificate is to be used by the other participants for verification of the cardholder's RSA signatures.

2. Merchant: A merchant is a person or an organization that sells goods or provides online services over the Internet. The merchant accepts payments through specified brands of credit cards. A merchant has a relationship with a bank called the Acquirer. Each merchant is issued two public key certificates—one for the verification of its signatures and the other for the exchange of session keys.

3. Issuer: The Issuer is a financial institution (such as a bank) that issues credit cards (like MasterCard or Visa, etc.) to customers, after due verification. Each card will have an account opened in the issuer bank, which is linked to the credit card. The issuer bank is fully responsible for the clearing of all debts of its cardholders.

4. Acquirer: The Acquirer is also a financial institution (bank) that establishes relationships with merchants. Each merchant will have an account opened at its acquirer bank, and the acquirer is responsible for the following:

- a. Processing of the Merchant’s “payment authorization,” which amounts to the confirmation that the cardholder making the related purchases is a valid cardholder and that the related purchases are within the credit limits of the cardholder.

- b. Processing of “Payment Capture,” which results in the transfer of funds from the cardholder’s account to the Issuer Bank to the Merchant’s account at the Acquirer Bank. The “Payment Capture” is affected only after the Merchant has delivered the ordered items/provided the ordered services.

5. Payment Gateway: This is a function performed by the acquirer bank or by a designated trusted third-party that processes merchant payment messages. The merchant exchanges the SET messages with the payment gateway over the Internet, while the payment gateway communicates with the acquirer over a direct secure link or secure payment network.

## 12.8.1 Business Requirements of SET

- 1. Ensure integrity of all transmitted data.
- 2. Provide authentication that a cardholder is a legitimate user of a credit card account.
- 3. Provide authentication that a merchant can accept credit card actions through its relationship with a financial institution (called an acquirer bank).
- 4. The order Information should be shared only between the cardholder and the merchant (not to be shared with the payment gateway).
- 5. The payment information (that includes credit card details) should be shared only between the cardholder and the payment gateway (not to be shared with the merchant).
- 6. Develop a mechanism to link the payment information with the order information, and this linkage should be made available to all the participants. This is to avoid tampering with order-payment-information by any participant without being detected by other participants. If any of the participants tampers with this information, then the other parties should be able to prove that information has been tampered with.
- 7. Ensure the use of best security practices and system design techniques to protect all legitimate parties in online transactions.
- 8. Create protocols that neither depend on the transport security mechanisms nor prevent their use.
- 9. Facilitate and encourage interoperability among software and network providers.

## 12.9 KEY FEATURES OF SET

1. Confidentiality of Information: The Cardholder account and payment information is secured as it travels across the network, and this information is not provided to the merchant. Credit card information is provided only to the issuing bank. Symmetric encryption by DES is used to provide confidentiality. DES uses one-time session-key encryption. The session key, encrypted by the recipient's public key using RSA, is also sent to the intended recipient along with the message. The encrypted session is called "Digital Envelope." At the recipient end, the session is first extracted from the digital envelope by decrypting it using the recipient's private key. The session key is used to decrypt the encrypted message. The schematic is shown in Figure 12.15.

FIGURE 12.15 A schematic diagram displaying confidentiality of information in SET.

2. Integrity of Data: SET guarantees that message contents are not altered in transit. RSA digital signatures using SHA-1 hash codes provide message integrity. The signer's public key certificate is sent to the recipient along with the signed message. The recipient will extract the signer's public key from the received certificate and use it for verification of the signature on the received message as in Figure 10.16.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_488_0.png)

FIGURE 10.16 A schematic diagram showing integrity of data.

- 3. Cardholder Authentication: SET enables a merchant to verify that a cardholder is a legitimate user of a credit card account. SET uses X.509 V3 certificates and RSA signatures.
- 4. Merchant Authentication: SET enables cardholders to verify that a merchant has a relationship with a financial institution allowing it to accept credit card payments. SET uses X.509 V3 certificates and RSA signatures.

### 12.9.1 Use of Public Key Certificates in SET

SET makes use of X.509 V3 certificates of two categories:

- 1. X.509 V3 certificates for Signature Verification
- 2. X.509 V3 certificates for exchange of session keys

### 12.9.2 Sequence of Events in SET

- 1. The Customer opens a Credit Card Account with an Issuer Bank and obtains a Credit Card of some brand.
- 2. The Customer receives an X.509 V3 digital certificate, signed by the issuer bank. The certificate contains the cardholder's public key (PU), to be used by others for verification of the cardholder's signatures, created using RSA with the cardholder's private key (PR).
- 3. Merchants have their own certificates, one for signatures using RSA and the other for the exchange of session keys. The merchant also needs a copy of the Payment Gateway's Public Key Certificate.
- 4. Purchase Request by the Customer
- 5. Payment Authorization by the Acquirer
- 6. Payment Capture

The Cardholder and the Merchant first finalize the list of items to be purchased and then perform SET protocols, which comprises the following sequence of messages:

## Purchase Request: It comprises four messages:

1. Initiate Request (Cardholder Merchant)
2. Initiate Response (Merchant Cardholder)
3. Purchase Request (Cardholder Merchant)
4. Purchase Response (Merchant Cardholder)

- a. Initiate Request: The Initiate Request Message from the Cardholder to the Merchant comprises:
* Brand of the Credit Card used by the Cardholder
* ID assigned to this Request
* Nounce N1 (This is to be echoed back by the Merchant)

- b. Initiate Response: In response, the Merchant generates an Initiate Response Message, signs it with its private key, and sends it to the requesting cardholder. The Initiate Response Message comprises:
* Nounce N1 (Echoed back by the Merchant)
* Nounce N2 (For the Cardholder to echo back) Message (M)
* Transaction ID (ID assigned to this Transaction)
* Signed Message Digest of Message M
