# 37.6.7.4 Certificate and Certificate Revocation List Dissemination.

The communicating parties must obtain the certificates and CRLs issued by the various CAs in each other's domain. These certificates and CRLs may be obtained from a repository such as an X.500 and Lightweight Directory Access Protocol (LDAP) server. Alternatively, the certificates and CRLs can be carried as part of the communication protocol between the parties, for example, as defined in S/MIME (Secure/Multipurpose Internet Mail Extension) version 3.

The X.500 and LDAP repositories are based on hierarchical databases. Each node in the hierarchical tree structure belongs to an object class. The node's object class determines the attributes that are stored for that node. Examples of attributes are job title, phone number, fax number, and the like. Certificates and CRLs are also attributes.

X.500 and LDAP have defined a standard schema for PKI certificates and CRLs. For certificates, these attributes are userCertificate, cACertificate, and crossCertificatePair. The end-entity certificates should be stored in userCertificate attribute. All CA certificates should be stored in the forward element of the crossCertificatePair attribute of the subject CA. In addition, all certificates issued to the CAs in the same domain should be stored in the cACertificate attribute of the subject CA.

Various revocation lists should be stored in the cRL, aRL, and deltaCRL attributes of the issuing CA as applicable.

If the certificates and CRLs are not stored in these standardized attributes, the relying-party software may not be able to obtain these objects. Furthermore, X.500 directory products still may not always interoperate due to additional complexity of the X.500 standard and to product differences. When implementing X.500 directories and connecting X.500 directory products from different vendors, implementers should allow time to make the products and directories interoperate.

# 37.6.7.5 Certificate Policies.

In order to trust and cross-certify each other, the CAs in two domains need to operate under similar policies. Users in the two domains should be able to accept or reject certificates of each other's domains based on the security requirements of the application, and on the policy under which the certificates were issued.

In order to determine the similarity, or equivalence, of the policies of the two domains, the CP should be written using the IETF standard RFC-2527 framework. The CP is represented using an OID in the certificate. To ensure that the user software accepts and rejects certificates based on the application requirements and on the CP, PKI products should be selected and configured so that the CA asserts the certificate policies, policy mapping, and policy constraints extensions appropriately. The user's PKI-enabling software must process these extensions appropriately and fully in compliance with the requirements of X.509 certificate-path validation rules.

# 37.6.7.6 Names.

The communicating domains must not assign the same name to two different entities. X.500 distinguished names (DNs) are steps in that direction but not sufficient to achieve this.

To illustrate the point, consider, for example, CygnaCom, a company incorporated in the Commonwealth of Virginia. While it is highly unlikely that there is another CygnaCom in Virginia, there is no assurance that there is no CygnaCom incorporated in other U.S. states. Thus, it would be possible that c=US, O=CygnaCom could be asserted by the CAs for several different domains.