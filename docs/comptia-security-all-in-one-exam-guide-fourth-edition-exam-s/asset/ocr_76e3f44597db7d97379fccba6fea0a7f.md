Figure 24-5
Browsers have a long list of CAs configured to be trusted by default.

![](bbox=[0.34, 0.07, 0.9, 0.46])

signed by the company’s CA. Other products, such as Entrust, use centrally controlled policies to determine which CAs are to be trusted, instead of expecting the user to make these critical decisions.

A number of steps are involved in checking the validity of a message. Suppose, for example, that Maynard receives a digitally signed message from Joyce, who he does not know or trust. Joyce has also included her digital certificate with her message, which has her public key embedded within it. Before Maynard can be sure of the authenticity of this message, he has some work to do. The steps are illustrated in Figure 24-6.

First, Maynard will see which CA signed Joyce’s certificate and compare it to the list of CAs he has configured within his computer. He trusts the CAs in his list and no others. (If the certificate was signed by a CA he does not have in the list, he would not accept the certificate as being valid, and thus he could not be sure that this message was actually sent from Joyce or that the attached key was actually her public key.)

Maynard sees that the CA that signed Joyce’s certificate is indeed in his list of trusted CAs, so he now needs to verify that the certificate has not been altered. Using the CA’s public key and the digest of the certificate, Maynard can verify the integrity of the certificate. Then Maynard can be assured that this CA did actually create the certificate, so he can now trust the origin of Joyce’s certificate. The use of digital signatures allows certificates to be saved in public directories without the concern of them being accidentally or intentionally altered. If a user extracts a certificate from a repository and creates a message digest value that does not match the digital signature embedded