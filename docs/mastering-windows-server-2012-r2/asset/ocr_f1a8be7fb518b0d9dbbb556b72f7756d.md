# FIGURE 6.28

DDNS options
on DHCP

![](bbox=[0.318, 0.068, 0.843, 0.403])

# # UNDERSTANDING Active Directory’s DNS

Microsoft has integrated DNS and Active Directory so tightly together that it's difficult to discuss the two separately. When an Active Directory environment is created with Windows Server 2012 R2, the Active Directory installation process automatically configures DNS while adding the role. This provides a hands-off capability for the IT generalist setting up DNS.

In the following sections, we'll cover how the Active Directory configures DNS and uses it to support clients. For a more detailed discussion of the Active Directory terms and concepts, refer to Chapter 7.

# ## Configuring DNS Automatically

Windows Server 2012 R2 offers two ways of installing the DNS server: on its own (as you've seen in the stand-alone non-domain configuration) or adding the Active Directory Domain Services role. When you opt for the latter, you must run the Active Directory Installation Wizard, which performs a number of configurations for the Active Directory Domain Services role, including automatically configuring and integrating the DNS. In Chapter 7, we will walk you through the Active Directory installation process in detail, but here we take a look at what happens regarding the DNS.

First, you must understand the prerequisite for the Active Directory installation process. The prospective domain controller needs to have connectivity to the existing Active Directory DNS structure. Otherwise, it won't be able to connect to the domain controllers and obtain the necessary information. The IP configurations must list a DNS server within the Active Directory environment, preferably the root's DNS server or a DNS server in the same domain you are about to join. The only exception to this is when you create the first