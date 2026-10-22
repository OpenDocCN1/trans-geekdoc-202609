This poses authorization problems for any access control lists attached to X.500 data objects, due to the difficulty of identifying all of the access control lists that grant privileges to a particular user’s name. The unique identifier field added in X.509v2 provides somewhere to put a new value whenever a name is reused. In fact, a better solution is to use a better distinguisher in the X.500 name, such as:

[Common Name = Fred Jones, Employee Number = 1000002]

In 1993, when the Internet Privacy Enhanced Mail (PEM) RFCs were published, they included specifications for a public key infrastructure based on X.509v1 certificates. Attempts to deploy PEM, however, revealed deficiencies in the Version 1 and 2 certificate formats. Consequently, ISO/IEC/ITU and ANSI X9 developed the X.509v3 format, which greatly extends the capabilities of the format by providing extension fields and broader naming options in X.509v3.

# 7.5.3.2 **Extending the Standard.**

Extensions were added in Version 3 to address problems discovered while implementing Version 1 and 2 certificates. These can be seen in the diagram in Exhibit 7.20. Particular extension field types may now be specified in standards or defined and registered by any organization or community. Each extension field is assigned a type by means of an object identifier, registered in the same way that an algorithm is registered. Although theoretically anyone can define an extension type, to achieve practical interoperability, common extension types need to be understood by different implementations. Thus, the most important extension types are standardized. But when X509v3 is used within a closed group—for example,

![](bbox=[0.132, 0.509, 0.938, 0.921])

**EXHIBIT 7.20**  X.509v3 Certificate