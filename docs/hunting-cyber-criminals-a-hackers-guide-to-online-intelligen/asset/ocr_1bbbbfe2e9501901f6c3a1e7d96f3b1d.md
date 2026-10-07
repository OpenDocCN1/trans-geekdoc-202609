# Chapter 11 ■ Iris by DomainTools 227

Pivot Engine Visualization Stats IP Tools Whois History Hosting Screenshot History

| Domain | Proximity | Email |
| --- | --- | --- |
| | alused@godaddy.com | Whois |
| curverecords.com 13 | Address | Typeis |
| | dns@dmadadeasy.com | DNS/SOA |
| info@jplsk.com | SSL |
| alused@godaddy.com | Whois |
| nightlion.net 13 | Address | Typeis |
| | dns@dmadadeasy.com | DNS/ISO |
| | alused@godaddy.com | Whois |
| nightlionsecurity.com 10 | Address | Typeis |
| | dns@dmadadeasy.com | DNS/SOA |
| | alused@godaddy.com | Whois |

Figure 11.9

# # Pivoting on SSL Certificate Hashes

SSL certificates are a great way to categorize domains and will often provide the connections between related infrastructure. The previous chapter showed the power of being able to find related domains using SSL certificate hashes or subject names. Iris brings that functionality into its own platform, allowing investigators to follow leads based on the same SSL certificate transparency information.

Looking at the certificate information for my personal domain, VinnyTroia.com, and my company domain, NightLionSecurity.com (shown in Figure 11.10), you see obvious differences in the SSL certificate.

Two of the domains share a similar SSL hash and subject name. The NightLionSecurity.com hash and subject is unique to that domain, which is why the data is not highlighted. There are no other matches.

To explore one of the highlighted SSL hash pivot points, right-click the hash and select Expand Search to expand your search to include domains using this new SSL hash (Figure 11.11).

You can also choose to start a new search, or narrow your search results, meaning only sites that share the selected SSL hash will be displayed. Until now, previous examples have used the Expand Search option, which continues to add to the overall number of matches.