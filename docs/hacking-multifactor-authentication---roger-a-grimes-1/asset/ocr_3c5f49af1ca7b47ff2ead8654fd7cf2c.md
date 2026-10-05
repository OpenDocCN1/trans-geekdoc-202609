# Chapter 19 API Abuses 409

# OATH

The Initiative for Open Authentication (OATH; openauthentication.org) is an industry consortium focusing on strong authentication (i.e., token devices) and creating and using open standards. They focus on three major types of MFA solutions:

+   - Subscriber identity module (SIM)
- Public key infrastructure (PKI)
- One-time password (OTP)-based solutions

OATH has a large list of members and has created widely adopted open token standards (most covered in previous chapters), including the following:

+   - HOTP: HMAC-Based OTP Algorithm (RFC 4226)
- TOTP: Time-Based One Password Algorithm (RFC 6238)
- OCRA: OATH Challenge/Response Algorithms Specification (RFC 6287)
- PSCK: Portable Symmetric Key Container (RFC 6030)
- DSKP: Dynamic Symmetric Key Provisioning Protocol (RFC 6063)

Even though OATH seems to have a lot of promise and there are fairly recent partner announcements, such as Microsoft in 2018 (techcommunity.microsoft.com/t5/azure-directory-identity/hardware-oath-tokens-in-azure-mfa-in-the-cloud-are-now-available/ba-p/276466), it appears to have dissolved recently. The FIDO standard seems to be capturing the lion's share of news and progress, even from the same members. OATH has come into existence, released a bunch of important RFCs, and then disappeared. Sadly, some of the methods that became more popular—such as generating keys in cleartext, like Google Authenticator, instead of using Dynamic Key Provisioning Protocol (DSKP)—seem to have won out even though OATH is clearly technically superior. Unfortunately, that of popularity over security is not unusual in the field.

> NOTE One other very interesting OATH initiative is Sharing Transaction Data Fraud, RFC 5941 (www.ietf.org/rfc/rfc5941.txt). It is an RFC that recognizes the world would be better served if we could share information about security incidents in a faster, previously agreed-on format and structure. Information about fraud and cybersecurity incidents could be uploaded and shared by participants to help respond to incident and prevent future threats. Unfortunately, it doesn't appear much traction has occurred since its submission in 2010. Something like this needs to happen and is likely to be part of what ends up making the Internet a safe place to be.

You can learn more about OATH here: openauthentication.org and openauthentication.org/wp-content/uploads/2015/09/AnIndustryRoadmapforOpenStandardAuthentication.pdf.