# DcDIAG

DcDiag was originally part of earlier versions of administrator support tools (which needed to be installed separately) from Windows Server but is now included by default as part of the Windows Server 2012 R2 installation. It's our first-choice tool to perform a quick health check on the DNS structure. Since it runs through score of domain controller diagnostics, it validates that DNS is working as needed. After running the standard battery of tests, you may see errors in attempting to connect to domain controllers. Then you could run additional DcDiag tests specifically for DNS. The following examples test whether a domain controller can perform DNS to register its SRV records:

```
dcdiag:/test:RegisterInDNS /DnsDomain:bigfirm.com /f:documents\dcdiagRegisterInDNS.txt
```

This produced the following test output:

Starting test: RegisterInDNS

DNS configuration is sufficient to allow this domain controller to dynamically register the domain controller Locator records in DNS.

The DNS configuration is sufficient to allow this computer to dynamically register the A record corresponding to its DNS name.

BF1 passed test RegisterInDNS

DcDiag performs a domain of domain controller-related tests, including DNS tests. We mentioned one, the RegisterInDNS test. These tests primarily focus on the integration between the DNS servers within an Active Directory environment. Tests can be performed on delegation, forwards, dynamic update, and external DNS name resolution.
The following is a portion of the help information for the DcDiag utility. It lists the tests available for DNS. We normally rely on Lookup to test external name resolution, so we never use the /DnsForwarders and /DnsResolveName tests but listed them here for transparency:

DNS
This test checks the health of DNS settings for the whole enterprise. Sub tests can run individually using the switches below. By default, all tests except external name resolution are run

+   /DnsBasic (basic tests, can't be skipped)
/DnsForwarders (forwards and root hints tests)
/DnsDelegation (delegation tests)
/DnsDynamicUpdate (dynamic update tests)
/DnsRecordRegistration (records registration tests)
/DnsResolveName (external name resolution test)
/DnsAll (Includes all tests above)
/DnsInternetName: <internet name> (for test /DnsResolveExtName)
(default is www.microsoft.com)