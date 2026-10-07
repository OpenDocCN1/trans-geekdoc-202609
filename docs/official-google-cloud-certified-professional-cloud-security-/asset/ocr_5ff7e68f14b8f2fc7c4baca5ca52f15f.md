In Figure 7.25, you first assign a name to your private zone in the Zone field. Then, specify DNS name, which is the domain name, and then set the DNSSEC option to On. Once completed, click the CREATE button.

In the most basic form, DNSSEC works by including a digital signature in responses to DNS queries. So, for every DNS zone, public and private keys are created. Cloud DNS serves the public key (DSKEY), resource record signatures (RRSIG), and non-existence (NSEC) records to authenticate your zone's contents. These are automatically managed by Cloud DNS when you have enabled DNSSEC.

An important thing to note is that for DNSSEC to work, your registrar and registry should support DNSSEC for your top-level domain. This means that for DNSSEC to be effective, the company that is responsible for registering the domain name (registrar) and the company that is responsible for maintaining the database of domain names and their associated IP addresses (registry) must support DNSSEC for the top-level domain (for example, .com, .org, and so on).

If you are unable to add a Delegation Sign (DS) record through your registrar to enable DNSSEC, enabling on Cloud DNS will have no effect. Another thing to be aware of is that DNSSEC is not encrypted; keys are used to authenticate the resolver, not to encrypt client-server queries and resolutions.

If you are migrating from your DNSSEC-signed zone to Cloud DNS, you can use the Transfer state when enabling DNSSEC for your public zone. The Transfer state copies you relevant keys, such as the key signing key (KSK) and zone signing key (ZSK), from your old zone to Cloud DNS. You should keep the state as Transfer until all DNS changes have propagated to the authoritative DNS server and then change the state to On.

# Load balancers

In this section, we will look at load balancing. There are many different load balancers that are available on Google Cloud. We will look at each of the different types of load balancers, what they are, and when to use which type of load balancer based on the traffic type. We will go over a decision tree that helps you decide what type of load balancer would meet your requirements, with some limitations as well.

The other aspects that we will cover include the difference between external and internal load balancers and when to use which and why; regional versus global load balancers; and some considerations from a network tier perspective, as some load balancers are only supported by Premium Tier while others are also supported by Standard Tier. This is an important thing to be aware of both from a cost and security perspective.