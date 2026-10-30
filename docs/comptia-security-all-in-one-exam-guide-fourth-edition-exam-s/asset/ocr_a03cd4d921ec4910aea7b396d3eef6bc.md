If an application creates a key store that can be accessed by other applications, it will provide a standardized interface, called the application programming interface (API). In Mozilla and Linux systems, this interface is usually PKCS #11, and in Microsoft applications, the interface is Cryptography API: Next Generation (CNG) for Microsoft Vista and later. As an example, Figure 24-4 shows that Application A went through the process of registering a certificate and generating a key pair. It created a key store that provides an interface to allow other applications to communicate with it and use the items held within the store.

The local key store is just one location where these items can be held. Often, the digital certificate and public key are also stored in a certificate repository so that they are available to a subset of individuals.

# Trust and Certificate Verification

We need to use a PKI if we do not automatically trust individuals we do not know. Security is about being suspicious and being safe, so we need a third party that we do trust to vouch for the other individual before confidence can be instilled and sensitive communication can take place. But what does it mean that we trust a CA, and how can we use this to our advantage?

When a user chooses to trust a CA, she will download that CA’s digital certificate and public key, which will be stored on her local computer. Most browsers have a list of CAs configured to be trusted by default, so when a user installs a new web browser, several of the most well-known and most trusted CAs will be trusted without any change of settings. An example of this listing is shown in Figure 24-5.

In the Microsoft CNG environment, the user can add and remove CAs from this list as needed. In production environments that require a higher degree of protection, this list will be pruned, and possibly the only CAs listed will be the company’s internal CAs. This ensures that digitally signed software will be automatically installed only if it was

Figure 24-4
Some key stores can be shared by different applications.

![](bbox=[0.22, 0.64, 0.9, 0.95])