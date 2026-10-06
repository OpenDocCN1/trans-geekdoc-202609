# HOST AND POINTER RECORDS

Host (A) and pointer (PTR) records are the most common records you will find in the forward lookup zones and the reverse lookup zones, respectively. The A records list the hostname of the computer and return the IP address. The PTR records list the IP address and return FQDN.
You may have to create these for computers that do not have the DDNS update protocol.

# ALIAS RECORDS

CNAME records are created to list a secondary name for a computer. This record will list the name and return the assigned computer's FQDN. These are useful in the event of replacing the service of a published name that the clients use to access applications or services. Without reconfiguration, clients will still be able to access the alias after replacement.

# MAIL EXCHANGER RECORDS

# SERVICE RECORDS

Service records (SRV) are the "big kahunas" for Windows DNS implementations. Without the SRV records, workstations and servers would not be able to find domain controllers. The SRV records by themselves involve five values:

+   - Service Name This is a standard value predicted by an underscore, or as _gc_ldap. This is equivalent to a hostname and it be tackled under the FQDN of a service.
- Server FQDN This is the server that provides the service.
- Port is the TCP or UDP port on which the service is available. The protocol is signed in the registered name, such as _tcp.
- Priority works just like MX records--has "number-priority."
- Weight is the tiebreaker for priority. Leave it at 0 if you're not concerned with ties.

You will see a plethora of SRV records in a Windows DNS zone that supports Active Directory. They are found in subdomain folders where the service name is assigned different FQDNs. The required service is described by the FDN like _gc_tcp.bigfirm.com. Figure 6.22 illustrates the SRV records.