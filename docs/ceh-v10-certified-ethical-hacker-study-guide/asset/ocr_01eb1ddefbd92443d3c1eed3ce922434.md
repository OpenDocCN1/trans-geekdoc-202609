like one thing when in fact it’s something else entirely. It may also be a result of a misconfiguration. You can see an example of this in Figure 13.8.

# FIGURE 13.8 Certificate error

![](bbox=[0.27, 0.19, 0.72, 0.5])

Google Chrome has generated this error because the name on the certificate doesn’t match the name of the server. The hostname of the web server is www.sofamart.com. When you register for a certificate, you have to provide the name. This includes the hostname of the server you are installing the certificate to. These values must match. In the case here, the certificate was issued to *.furniturerow.com. This demonstrates that even if a certificate comes from a trusted authority, that doesn’t mean the server you are connecting to can be trusted because the certificate may have been taken and installed somewhere else. Here, Furniture Row is the company that owns Sofa Mart, so it attempted to save some money by using the same certificate across all servers it uses.

# Self-Signed Certificates

Sometimes you want to just encrypt messages between two systems in a lab, for instance. You can create your own certificates. You don’t even need to go through the steps of creating your own certificate authority. You can just generate your own certificate and use it. This will result in certificate errors because the certificate won’t be signed. It will be a bare certificate. Just as OpenSSL was used by Simple Authority, it can be used on the command line to generate certificates by hand. You would be using the commands Simple Authority is running. Here you can see the OpenSSL commands used to create a certificate.