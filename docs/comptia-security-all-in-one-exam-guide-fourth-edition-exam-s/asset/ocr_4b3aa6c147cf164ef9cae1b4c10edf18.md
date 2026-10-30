# Validating a digital certificate

![](bbox=[0.058, 0.073, 0.819, 0.591])

+   1. Joyce sends the message and digital certificate to Maynard.
+   2. Maynard extracts the certificate.
+   3. He puts the certificate through a hashing algorithm.
+   4. The algorithm calculates a value of A.
+   5. Maynard extracts the encrypted message digest from the certificate.
+   6. Maynard decrypts the value with the CA's public key.
+   7. Maynard checks to see if the certificate was revoked. Maynard compares values A and B.
+   8. The values are the same, so Maynard reads the message.

**Figure 24-6**  Steps for verifying the authenticity and integrity of a certificate

within the certificate itself, that user will know that the certificate has been modified by someone other than the CA, and he will know not to accept the validity of the corresponding public key. Similarly, an attacker could not create a new message digest, encrypt it, and embed it within the certificate because he would not have access to the CA's private key.

But Maynard is not done yet. He needs to be sure that the issuing CA has not revoked this certificate. The certificate also has start and stop dates, indicating a time during which the certificate is valid. If the start date hasn't happened yet, or the stop date has been passed, the certificate is not valid. Maynard reviews these dates to make sure the certificate is still deemed valid.

Another step Maynard may go through is to check whether this certificate has been revoked for any reason, so he will refer to a list of revoked certificates to see if Joyce's