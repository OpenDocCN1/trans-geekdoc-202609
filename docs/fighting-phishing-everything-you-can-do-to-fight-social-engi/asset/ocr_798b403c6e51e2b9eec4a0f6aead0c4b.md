Here’s how SPF verification works. Anyone (actually their receiving email client, server/service, or agent on their behalf with SPF validation enabled) getting an email claiming to be from a particular 5321 domain can validate that email’s claimed 5321 domain. The receiving agent retrieves the sending email server’s SPF record from the sender’s DNS server and compares the information in the provided SPF record to the email’s claimed 5321 domain information. Again, the SPF record states what email servers (by IP address or domain name) are allowed to send email on behalf of that particular domain. If the comparison information matches, then the SPF check is a “PASS.” If they don’t match, then the SPF check is a “FAIL.”

Most people’s email servers or clients are already doing SPF checks today whether they know it or not. To verify, all the user has to do is open up any email that they have received, look at the email header, and look for text that says “SPF=.” It will likely say “PASS,” “FAIL,” “NONE,” or something similar. Having any SPF validation message means the client agent (or some other agent in the receiving pathway) has SPF validation checking enabled.

Figure 7-8 shows an example of an email which was an SPF pass.

![](bbox=[0.12, 0.64, 0.83, 0.91])

FIGURE 7-8 An example of an SPF pass.