called a certificate authority since it is the authority that manages the certificates. Sometimes the software itself is referred to as the authority. This is the case with a piece of software called Simple Authority. This software uses the OpenSSL library and utilities to generate the certificates and handles the storage, creation, and management through a graphical interface. Figure 13.5 shows creating a certificate authority, meaning creating the root certificate and the certificate repository, using Simple Authority. The root certificate is the certificate that all other certificates in the CA are signed by.

# FIGURE 13.5 Simple Authority CA creation

![](bbox=[0.31, 0.27, 0.67, 0.47])

Once the root certificate has been generated, you can create other certificates. Figure 13.6 shows not only the creation of a new certificate but also the different types of certificates that can be created. Any entity that wants to encrypt messages using public key cryptography needs to have a certificate. If you want to send messages to someone, you can get a certificate. Servers, though, also need to have certificates. Any web server that uses encrypted messages, and these days it's rare to find a web server that isn't encrypting traffic, needs to have a certificate. You can see that as one of the options. If you were going to set up a web server that was going to use TLS, you would select SSL Server, since TLS is the current implementation of what was once SSL.

# FIGURE 13.6 Certificate creation

![](bbox=[0.33, 0.7, 0.65, 0.94])