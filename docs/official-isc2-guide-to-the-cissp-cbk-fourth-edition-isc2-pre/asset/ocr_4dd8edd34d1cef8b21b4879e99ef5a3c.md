modes for the data channel:

+   - **Active mode (PORT mode)** – Where the server initiates the data connection to the client. This mode has obvious drawbacks in firewalled environments, as incoming connections to the client can (and should) be blocked. A number of firewall products still support active mode.
+   - **Passive mode (PASV mode)** – Where the client initiates the data connection to the server. Even though RFC 959 does not mandate implementation of passive FTP, the majority of FTP servers offer this type of connection.

# Anonymous FTP

Before the advent and proliferation of HTTP, publication of information to an unspecific user group was fulfilled by FTP services offering guest authentication to anyone who so desired. These services were called anonymous FTP due to the fact that the guest user would be mapped to the FTP log-in ID "anonymous," whereas the user would pseudo-authenticate (and thereby identify) himself with his email address. In practice, the user could have been using any password or email address, whereas using one’s true email address would still have been considered common courtesy.

Although Web browsers still support the (social) protocol as such, the use of anonymous FTP has widely fallen by the wayside. There are three main reasons.

+   1. With HTTP, anonymous publication of information can be handled in a much more efficient and seamless manner.
+   2. Disclosure of email addresses on the part of the user (or a requirement to do so) is widely regarded as an unsafe and privacy-violating practice that will expose the user to address harvesting by spammers.
+   3. Guest access can expose the FTP server to security risks.

# Trivial File Transfer Protocol (TFTP)

TFTP is a simplified version of FTP, which is used when authentication is not needed and quality of service is not an issue. TFTP runs on port 69 over UDP. It should therefore only be used in trusted networks with low latency.

| Ports | 69/UDP |
|-------|--------|
| Definition | RFC 1350 |

Table 4.8 - TFTP Quick Reference