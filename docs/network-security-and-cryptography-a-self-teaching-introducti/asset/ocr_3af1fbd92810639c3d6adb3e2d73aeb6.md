E: Public Key Encryption Algorithm (RSA)

PRC: Cardholder's Private Key (for signing of messages)

DS: Dual Signature

```
DS = EPrc[H(PI)||H(Oi)]
```

The purpose of the dual signature is to link two messages that are intended for different recipients. For obvious reasons, the Cardholder (customer) intends to send the Payment Information (PI) only to the issuer bank, through the Payment Gateway; and the Order Information only to the Merchant. This is because the credit card information, being sensitive, should not be disclosed to anyone other than the issuer bank, and the bank need not know the Order Information. However, both PI and OI must be linked in a way that can be used to resolve disputes, if any, in future. So, the customer creates a link between the OI and PI through the Dual Signature, which the customer can prove later on to both the Merchant and the Issuer Bank.

Finally, the customer will be in possession of the PI, OI, and Dual Signature.

The Merchant received the OI, PIMD, and Dual Signature.

And the issuer bank received the PI, OIMD, and Dual Signature.

None of the three parties (Customer, Merchant, and Bank) can alter the information it possesses since the other parties will be to verify and prove any such alteration with the information they possess.

Processing Purchase Request (by the Merchant’s Software)

+   - Verifies the Customer’s Public Key Certificate by verifying its CA Signature

+   - Verifies the Dual Signature as indicated in Figure 12.19 diagrammatically. This ensures that the message has not been tampered with in transit and that the message has been signed by the alleged Customer.