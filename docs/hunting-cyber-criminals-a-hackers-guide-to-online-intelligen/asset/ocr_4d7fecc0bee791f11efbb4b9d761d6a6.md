# Chapter 5 Automated Tools for Network Discovery 101

```
139/tcp filtered netbios-ssn
443/tcp filtered https
445/tcp filtered microsoft-ds
3389/tcp filtered ms-wbt-server
53/udp filtered domain
67/udp filtered dhcp
123/udp filtered ntp
135/udp filtered msrpc
137/udp filtered netbios-ns
138/udp filtered netbios-dgm
161/udp filtered smp
445/udp filtered microsoft-ds
631/udp filtered ipp
1434/udp filtered ms-sql-m
```

Too many fingerprints match this host to give specific OS details
Find Intrigue to be really not only because of the capacity of tasks/modules you use but because of how wide you can go with these modules. For example, with the results shown in Figure 5.24, we can see websocket .uberpepe.net and ftp.uberpepe.net.

| | | |
|---|---||
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | D | complete |
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | D | complete |
| dns_bute on DnsRecord: cpanel.uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: cpanel.uberpepe.net | D | complete |
| dns_bute on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: microsoft.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: microsoft.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: uberpepe.net | 2 | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | 2 | complete |
| dns_bute on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: mokotoldband.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: bedmaybreakfast.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: bedmaybreakfast.uberpepe.net | 3 | complete |
| dns_bute on DnsRecord: ns2.uberpepe.net | 3 | complete |
| enrich_dns_record on DnsRecord: ns2.uberpepe.net | 3 | complete |
| enrich_nameerver on DnsRecord: ns1.uberpepe.net | D | complete |
| enrich_nameerver on DnsRecord: ns1.uberpepe.net | D | complete |
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | D | complete |
| public_groups, check on DnsRecord: uberpepe.net | 13 | complete |
| dns_bute on DnsRecord: uberpepe.net | 4 | complete |
| search_ct on DnsRecord: uberpepe.net | 4 | complete |
| enumerate, namervers on DnsRecord: uberpepe.net | 2 | complete |
| dns_bute on DnsRecord: uberpepe.net | D | complete |
| enrich_net, block on NetBlock: 184.154.0.16 | D | complete |
| hmap_scan on ipAddress: 184.154.76.235 | 39 | complete |
| whoislookup on ipAddress: 184.154.76.235 | 1 | complete |
| enrich_dns_record on DnsRecord: uberpepe.net | 1 | complete |
| enrich/domain on DnsRecord: uberpepe.net | 1 | complete |
| enrich/p_address on ipAddress: 184.154.76.235 | 2 | complete |
| create_entity on DnsRecord: uberpepe.net | 1 | complete |

Figure 5.22