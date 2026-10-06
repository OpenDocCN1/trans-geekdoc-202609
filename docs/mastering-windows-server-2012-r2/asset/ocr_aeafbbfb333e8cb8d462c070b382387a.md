will appear somewhere on the client side, management may not like seeing that name on their desktop when they log in. We highly recommend discussing and getting a commitment from the responsible manager when choosing the domain name.

What should a domain name look like? As you know, a valid Active Directory root name looks like a fully qualified domain name (FQDN) and a suffix, such as bigfirm.com, myomain, or forest. These are all valid domain names. In Windows Server 2003 you could choose a single-label domain name like bigfirm, myomain, forest and it would be supported by Microsoft. But as applications, such as Exchange evolved and depended on Active Directory and DNS, you are no longer allowed to create single-label domains. If you try to create a single-label domain in Windows Server 2012, you will get an error.

For the second part of a top-level domain you could use a suffix such as .com, .gov, .ch, or .net, or you might prefer other suffixes, such as .local or .domain.
The advantages of having the same name for Active Directory and the public DNS name, such as bigfirm.com, are these:

+   * The company web applications URL is the same whether it is internal or external.
* You can use certificates internally
* The Sync IP address is the same as the email and login address.
* The logon could be used as the email address.

One big disadvantage is that it's not easy to distinguish from a firewall perspective between internal and external zones. Many administrators specifically try to use Internet top-level domain names to avoid confusion with their internal networks.
As you can see, there are advantages and disadvantages to each of these options. We cannot recommend naming one convention in general. In the end the name has to fit your technical requirements and also meet your company's security policy.

# ACTIVE DIRECTORY AND DNS

It is essential to know that Active Directory heavily depends on DNS. No DNS, no Active Directory. Why? Why Active Directory registers all kinds of SRV records in DNS to locate specific services that are needed for Active Directory to function correctly. I gather that 80 percent of problems of a nonfunctioning Active Directory are related to DNS.

When you installed your domain controller, a warning appeared that a delegation for the DNS could not be created. This is because the Active Directory wizard configures DNS for the server, but there is no DNS installed. Confirm the dialog and continue.

# DOMAIN FUNCTIONAL LEVELS

During the Active Directory setup wizard you are prompted to select the domain functional level. The domain functional level depends on the operating system you are using for your domain controller. You cannot select a higher domain functional level than the one your oldest version of the operating system has.

The following domain functional levels are available in Windows Server 2012.