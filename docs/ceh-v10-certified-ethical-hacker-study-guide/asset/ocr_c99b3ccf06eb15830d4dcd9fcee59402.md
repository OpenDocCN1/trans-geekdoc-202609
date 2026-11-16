Admin Phone: REDACTED FOR PRIVACY
Admin Phone Ext:
Admin Fax: REDACTED FOR PRIVACY
Admin Fax Ext:
Admin Email: a25006f8175341e32979e6f59e7b87ea-178660@contact.gandi.net

Using a strategy like this will keep information private and out of the hands of the very people spamhaus.org seeks to protect against. The data provided can be used to create a mailing list for spammers. It can also be used to create a physical mailing list for traditional junk mail providers (sometimes called mail marketing companies).

# Regional Internet Registries

Not all the useful information is stored with the domain registrars, however. There is other data that is important to be kept. Earlier, we discussed IANA. While the IANA server provided information about domain registrars, its purpose has long been to be a central clearinghouse for addresses. This includes not only port numbers for well-known services, but also IP addresses. IANA, at a high level, owns all IP addresses. It hands out those IP addresses, based on need, to the RIRs. The RIRs then hand them out to organizations that fall into their geographic region.

There are five RIRs around the world. They are based in different geographic regions, and an organization would refer to the RIR where they are located for things like IP addresses. The RIRs and the geographic areas they are responsible for are listed here.

+   * African Network Information Center (AfriNIC) Africa
+   * American Registry for Internet Numbers (ARIN) North America (US and Canada) as well as Antarctica and parts of the Caribbean.
+   * Asia Pacific Network Information Centre (APNIC) Asia, Australia, New Zealand, and neighboring countries
+   * Latin America and Caribbean Network Information Centre (LACNIC) Latin America and parts of the Caribbean
+   * Réseaux IP Européens Network Coordination Centre (RIPE NCC) Europe, Russia, West Asia, and Central Asia

All of these RIRs have their own databases that can be queried using whois, just as we used whois to query information from the domain registrars. Typically, you would use whois against the RIRs to find out who owns a particular IP address. For example, in the output for wiley.com earlier, part of the output indicated which name servers the domain uses to resolve hostnames to IP addresses. One of those name servers is ns.wiley.co.uk. With a minimal amount of effort (we will cover the DNS later in the chapter), we can discover that the hostname ns.wiley.co.uk resolves to the IP address 193.130.68.19. Using whois, we can find out who owns that IP address. You can see the results of that query in the following code.