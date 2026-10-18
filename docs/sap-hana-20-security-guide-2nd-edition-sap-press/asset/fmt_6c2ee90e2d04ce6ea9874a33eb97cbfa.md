
You’ll use this link to create, edit, and delete database users. You can only configure user account settings in this link. For example, you can configure the user’s authentication mode, password, third-party authentication settings, and custom user properties in this area. You cannot use this area to grant roles or privileges to users. Instead, you’ll use the Assign role to users and Assign privilege to users links for those activities. We’ll discuss these options in more detail in [Chapter 4](#04_001.html#h4).

*   Assign role to users  

    You’ll use this link to grant or revoke a role from a user account. We’ll discuss this link in more detail within [Chapter 5](#05_001.html#h5).

*   Assign privilege to users  

    You’ll use this link to grant or revoke individual privileges to a user. We’ll discuss this link in more detail in [Chapter 4](#04_001.html#h4) and from [Chapter 6](#06_001.html#h6) through [Chapter 11](#11_001.html#h11).

*   Manage roles  

    You’ll use this link to view and manage standard database runtime roles, for example, granting additional roles, system privileges, and object privileges to a role. You’ll also use this link to create and delete roles. We’ll discuss this link in more detail in [Chapter 5](#05_001.html#h5).

*   Manage user group  

    You’ll use this link to create and edit user groups. User groups help organize users into groups. You can configure user groups so that only specific users can manage the other user accounts within the group. You can also establish a unique password policy for each user group.

*   View database object dependencies  

    You’ll use this link to review the authorization dependencies of a given catalog objects, an important step that security administrators must perform before deleting database objects and for determining which users have access to a database object.

In the next section, we’ll explore the Data Encryption tile and its links.

### 1.2.2 Data Encryption

You’ll use the Data Encryption tile and its links to manage data encryption options for data at rest. The tile itself contains slider buttons where you can quickly enable or disable (ON or OFF) Data Volume Encryption, Redo Log Encryption, and Backup Encryption, as shown in [Figure 1.12](#01_002.html#f1.12).

[![Data Encryption Tile and Links in SAP HANA Cockpit](bilderklein/klein01_012.png)](img-f1.12.html)

**Figure 1.12** Data Encryption Tile and Links in SAP HANA Cockpit

In addition to using the sliders, each item can be clicked, including the tile’s title, to navigate to additional options for each item in the Data Encryption configuration interface. We’ll discuss this interface and these options in more detail in [Chapter 13](#13_001.html#h13). You should now have a basic understanding of how to access the Data Encryption tile and of the options it offers for managing an SAP HANA security model. In the next section, we’ll explore the Authentication tile and links.

### 1.2.3 Authentication

You’ll use the Authentication tile and its links to manage password policies, single sign-on (SSO), and the SYSTEM user’s password. The links in this tile (Password Policy, Single Sign-On, and SYSTEM User Password) can be clicked to manage each specific area, as shown in [Figure 1.13](#01_002.html#f1.13).

[![Authentication Tile and Links in SAP HANA Cockpit](bilderklein/klein01_013.png)](img-f1.13.html)

**Figure 1.13** Authentication Tile and Links in SAP HANA Cockpit

In [Chapter 12](#12_001.html#h12), we’ll discuss these link options in more detail. You should now have a basic understanding of how to access the Authentication tile and the options available when managing an SAP HANA security model. In the next section, we’ll explore the Security Related Links tile and its links.

### 1.2.4 Security Related Links

You’ll use the Security Related Links tile and its links to manage several security-related items SAP HANA database, as shown in [Figure 1.14](#01_002.html#f1.14).

[![Security Related Links Tile and Links in SAP HANA Cockpit](bilderklein/klein01_014.png)](img-f1.14.html)

**Figure 1.14** Security Related Links Tile and Links in SAP HANA Cockpit

Let’s explore the purpose and intended use of each link in more detail:

*   Manage certificates  

    You’ll use this link to access in-database certificates. As we’ll discuss further in [Chapter 13](#13_001.html#h13), you’ll use this interface to import and delete certificates.

*   Manage certificate collections  

    You’ll use this link to manage certificate collections. A certificate collection is a physical or logical store that holds a certificate and defines its purpose. As we’ll discuss further in [Chapter 13](#13_001.html#h13), you’ll use this interface to manage certificate collections stored within the database.

*   View network security information  

    You’ll use this link to access a page that provides general information concerning the status of communication encryption, the Transport Layer Security (TLS)/Secure Sockets Layer (SSL) settings and types, and internal communication encryption. This information is read-only, and no settings can be changed within this interface.

*   Manage SAML identity providers  

    You’ll use this link to manage third-party Security Assertion Markup Language (SAML) authentication providers and to import and delete SAML certificates critical to this mechanism. As we’ll discuss further in [Chapter 12](#12_001.html#h12), SAML can provide SSO capabilities to the SAP HANA database and web application interfaces.

*   Manage JWT identity providers  

    You’ll use this link to manage JSON Web Token (JWT) providers supported for SSO within the SAP HANA system. JWT is an open standard (RFC 7519) that outlines a means for communicating security information between two parties using JavaScript Object Notation (JSON) objects. SAP HANA has limited support for this functionality, as we’ll discuss further in [Chapter 12](#12_001.html#h12).

*   Security checklist  

    You’ll use this link to access SAP’s checklist for comparing current SAP HANA security settings to recommendations from SAP. This checklist provides real-time reports, warnings, and information related to securing your SAP HANA system. The interface only provides warnings and does not recommend specific actions. See [Chapter 17](#17_001.html#h17) for ways to mitigate the risk associated with some of the warnings found in the checklist.

*   Security administration help  

    You’ll use this link to open the SAP HANA Administration with SAP HANA Cockpit Guide hosted on the SAP HANA cockpit web application server. This guide provides detailed information on administering the SAP HANA cockpit. This link will take you directly to the “Security Administration” section of the guide.

*   SAP HANA security website   

    You’ll use this link to open the SAP HANA security product page at [www.sap.com](http://www.sap.com). On this page, you’ll find links to pertinent security help documents, white papers, and case studies.

You should now have a basic understanding of how to access the Security Related Links tile and the options it offers when managing an SAP HANA Security model. In the next section, we’ll explore the Anonymization Report tile and its links.

### 1.2.5 Anonymization Report

Starting with SAP HANA 2.0 SPS 04, you can define SQL views for anonymizing data when the data is queried based on a variety of parameters and methods. Views protected with the functionality are called anonymization views. You can use Anonymization Report tile and link to access the View Available Anonymization Views link navigating you to the Anonymization Report interface. On the Anonymization Report interface, you’ll see a list of catalog views where this feature is enabled. You can click on each listed view to view read-only information about the Anonymization Parameters and method that have been applied to the view.
