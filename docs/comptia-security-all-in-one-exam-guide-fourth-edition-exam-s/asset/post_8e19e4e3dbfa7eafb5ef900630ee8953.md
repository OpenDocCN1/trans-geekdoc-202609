
The certificate server is the actual service that issues certificates based on the data provided during the initial registration process. The server constructs and populates the digital certificate with the necessary information and combines the user's public key with the resulting certificate. The certificate is then digitally signed with the CA's private key.

## Registration Authorities

The registration authority (RA) is the component that accepts a request for a digital certificate and performs the necessary steps of registering and authenticating the person requesting the certificate. The authentication requirements differ depending on the type of certificate being requested.

The types of certificates available can vary between different CAs, but usually at least three different types are available, and they are referred to as classes:

- **Class 1** A Class 1 certificate is usually used to verify an individual's identity through e-mail. A person who receives a Class 1 certificate can use his public/private key pair to digitally sign e-mail and encrypt message contents.
- **Class 2** A Class 2 certificate can be used for software signing. A software vendor would register for this type of certificate so it could digitally sign its software. This provides integrity for the software after it is developed and released, and it allows the receiver of the software to verify from whom the software actually came.
- **Class 3** A Class 3 certificate can be used by a company to set up its own CA, which will allow it to carry out its own identification verification and generate certificates internally.

Each higher class of certificate can carry out more powerful and critical tasks than the one below it. This is why the different classes have different requirements for proof of identity. If you want to receive a Class 1 certificate, you may only be asked to provide your name, e-mail address, and physical address. For a Class 2 certification, you may need to provide the RA with more data, such as your driver's license, passport, and company information that can be verified. To obtain a Class 3 certificate, you will be asked to provide even more information and most likely will need to go to the RA's office for a face-to-face meeting. Each CA will outline the certification classes it provides and the identification requirements that must be met to acquire each type of certificate.

In most situations, when a user requests a Class 1 certificate, the registration process will require the user to enter specific information into a web-based form. The web page will have a section that accepts the user's public key, or it will step the user through creating a public/private key pair, which will allow the user to choose the size of the keys to be created. Once these steps have been completed, the public key is attached to the certificate registration form and both are forwarded to the RA for processing. The RA is responsible only for the registration process and cannot actually generate a certificate. Once the RA is finished processing the request and verifying the individual's identity, the RA will send the request to the CA. The CA will use the RA-provided information to generate a digital certificate, integrate the necessary data into the certificate fields (user identification information, public key, validity dates, proper use for the key and certificate, and so on), and send a copy of the certificate to the user. These steps are shown in Figure 24-3. The certificate may also be posted to a publicly accessible directory so that others can access it.

Note that a 1:1 correspondence does not necessarily exist between identities and certificates. An entity can have multiple key pairs, using separate public keys for separate purposes. Thus, an entity can have multiple certificates, each attesting to separate public key ownership. It is also possible to have different classes of certificates, again with different keys. This flexibility allows entities total discretion in how they manage their keys, and the PKI manages the complexity by using a unified process that allows key verification through a common interface.

**EXAM TIP** The RA verifies the identity of the certificate requestor on behalf of the CA. The CA generates the certificate using information forwarded by the RA.

![](img/922567202a944c5e8d3ba0168d2ad3a5_505_0.png)

- 1. The user registers for a digital certificate.
- 2. Some method is used to determine random values.
- 3. An algorithm generates a public/private key pair.
- 4. The key pair is stored in a key store on the workstation.
- 5. A copy of the public key and other identifying information is sent to the CA.
- 6. The CA generates a digital certificate containing the public key and the other identifying information.
- 7. The new certificate is sent to the user.

Figure 24-3 Steps for obtaining a digital certificate

If an application creates a key store that can be accessed by other applications, it will provide a standardized interface, called the application programming interface (API). In Mozilla and Linux systems, this interface is usually PKCS #11, and in Microsoft applications, the interface is Cryptography API: Next Generation (CNG) for Microsoft Vista and later. As an example, Figure 24-4 shows that Application A went through the process of registering a certificate and generating a key pair. It created a key store that provides an interface to allow other applications to communicate with it and use the items held within the store.

The local key store is just one location where these items can be held. Often, the digital certificate and public key are also stored in a certificate repository so that they are available to a subset of individuals.

## Trust and Certificate Verification

We need to use a PKI if we do not automatically trust individuals we do not know. Security is about being suspicious and being safe, so we need a third party that we do trust to vouch for the other individual before confidence can be instilled and sensitive communication can take place. But what does it mean that we trust a CA, and how can we use this to our advantage?

When a user chooses to trust a CA, she will download that CA’s digital certificate and public key, which will be stored on her local computer. Most browsers have a list of CAs configured to be trusted by default, so when a user installs a new web browser, several of the most well-known and most trusted CAs will be trusted without any change of settings. An example of this listing is shown in Figure 24-5.

In the Microsoft CNG environment, the user can add and remove CAs from this list as needed. In production environments that require a higher degree of protection, this list will be pruned, and possibly the only CAs listed will be the company’s internal CAs. This ensures that digitally signed software will be automatically installed only if it was

Figure 24-4
Some key stores can be shared by different applications.

![](img/922567202a944c5e8d3ba0168d2ad3a5_506_0.png)

Figure 24-5
Browsers have a long list of CAs configured to be trusted by default.

![](img/922567202a944c5e8d3ba0168d2ad3a5_507_0.png)

signed by the company’s CA. Other products, such as Entrust, use centrally controlled policies to determine which CAs are to be trusted, instead of expecting the user to make these critical decisions.

A number of steps are involved in checking the validity of a message. Suppose, for example, that Maynard receives a digitally signed message from Joyce, who he does not know or trust. Joyce has also included her digital certificate with her message, which has her public key embedded within it. Before Maynard can be sure of the authenticity of this message, he has some work to do. The steps are illustrated in Figure 24-6.

First, Maynard will see which CA signed Joyce’s certificate and compare it to the list of CAs he has configured within his computer. He trusts the CAs in his list and no others. (If the certificate was signed by a CA he does not have in the list, he would not accept the certificate as being valid, and thus he could not be sure that this message was actually sent from Joyce or that the attached key was actually her public key.)

Maynard sees that the CA that signed Joyce’s certificate is indeed in his list of trusted CAs, so he now needs to verify that the certificate has not been altered. Using the CA’s public key and the digest of the certificate, Maynard can verify the integrity of the certificate. Then Maynard can be assured that this CA did actually create the certificate, so he can now trust the origin of Joyce’s certificate. The use of digital signatures allows certificates to be saved in public directories without the concern of them being accidentally or intentionally altered. If a user extracts a certificate from a repository and creates a message digest value that does not match the digital signature embedded
