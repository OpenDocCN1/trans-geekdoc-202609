# 474 • NETWORK SECURITY AND CRYPTOGRAPHY

+   * If verified, the Payment Gateway creates a Clearing Request, which is sent to the Issuer Bank on the secure payment network.
* The Clearing Request causes funds to be transferred to the Merchant's Account.

ii. Capture Response: This message is sent from the Payment Gateway to notify the Merchant About the Payment. This message includes a Capture Response signed by the Public Gateway and encrypted. The message also includes a digital envelope and the Payment Gateway's Signature Key Certificate. The Merchant will decrypt the message, verify it, and store it. The Capture Response is used by the merchant for reconciliation with the payment received from the acquirer bank. This concludes the transaction.

# 12.10 EXERCISES

+   1. What are the services provided by IPSec?
2. What are the Headers through which IPSec provides security services?
3. What are the formats of Authentication Header (AH) and Encapsulating Security Payload (ESP)?
4. What are the services supported by AH and by ESP?
5. What are the Symmetric Encryption Algorithms supported by ESP?
6. What Hashing Algorithms are supported by Integrity Check value (ICV)?
7. What is the size (in bits) of HMAC-SHA-1-96?
8. Are mutable fields in the IP Header considered while computing ICV?
9. What is the purpose of using the Sequence Number in AH and ESP?
10. What is the purpose of padding in ESP?
11. What is Security Association (SA) in IPSec?
12. What are the parameters associated with each Security Association?
13. What do you understand by the combining of Security Associations?
14. What are IPSec Protocol Modes?