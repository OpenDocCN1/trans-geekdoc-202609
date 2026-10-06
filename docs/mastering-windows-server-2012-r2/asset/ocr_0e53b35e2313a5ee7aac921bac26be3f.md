# CAVEATS TO USING SPLIT-BRAIN DNS

Depending on whom you speak to or what technical document on DNS you read, you might see recommendations telling you not to use the same domain name for your company's internal and external DNS namespace. They will recommend that you use something else that may not be found on the Internet or a registered name you never use.

When companies don't follow this recommendation, they soon realize that they have a conflict with resolving external resources that you such as www.Bigfir.com. The internal DNS server can't find the name, so it kicks back a big goose egg for the response. The admins try to fix this by adding the name with the external IP address, but adding the external IP address causes routing issues. In addition, the developers are whining that they can't upload new content with the external IP address. They need the internal IP address. This kind of administrative hassle becomes the norm for dealing with split-brain issues.

Managing this with just one server would be ideal. A split-brain DNS implementation is a code that is proposed to remedy this issue. You could have a DNS server support at an internal and external zone of the same namespace. The IP addresses for the external zone would be provided to external requests and internal IP addresses for the internal requests.

It's a nice idea that Windows Server 2012 R doesn't support. Primarily, Microsoft doesn't support your organization expanding the domain controller that holds the internal namespace to the edge of the Internet. This is not a secure measure. The Active Directory database is too valuable to have in a DMZ like a ripe peach. So, you have to come up with an alternative.

Your objective is to provide resolution of external requests with external IP addresses and internal requests with internal IP addresses. Using Microsoft DNS, you will have to administer (a minimum of) two DNS servers to support this scenario. Here are the basic steps:

+   1. Implement an internal DNS server to support Bigfir.com. Typically, this is already in place with the resolution of a domain name with the help of the ISP.
2. Implement the internal DNS structure. Using the Active Directory Services Installation Wizard, this is handled quite readily.
3. Add any external records to the internal zone for Bigfir.com.
Remember, the DNS servers within the network will be authoritative for the Bigfir.com domain. If it can't find www.Bigfir.com, it doesn't exist. External records must be duplicated in the internal zone so a positive result can be returned. You will have to test to ensure that the IP address is accessible. If routing problems occur, you may have to use an internal address.
4. Configure resolving external namespaces using root hints or forwards. This topic is covered in the following section.

# Resolving External Namespaces

We discussed how to integrate a DNS server with others. The primary methods of resolving DNS names in the Internet are the root hints or the forwards. The root hints were a list of DNS servers that were at the top of the Internet's DNS structure. The DNS server could communicate