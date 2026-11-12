rogerg@knowbe4 .com and claim that is my 5321.MailFrom email address, SPF can be used to verify if that email really came from an email server authorized for the knowbe4 .com domain.

SPF must be first enabled on the email sender’s side using a DNS record called a “TXT record.” The TXT record for SPF is formatted similarly to:

```
```
domainname IN TXT "v=spf1" ip4:publicIPAddressofemail
server -all"
```
```

For example, if the sending email domain you were trying to protect was called knowbe4 .com, your SPF record might look like the following:

```
```
knowbe4.com. IN TXT "v=spf1 ip4:18.160.60.106 -all"
```
```

In this instance, 18.160.60.106 would be the public IP address of the email server/service authorized to send email on behalf of the knowbe4 .com domain.

There must be a separate TXT record in DNS for each protected domain name. You can also specify ip6: if you want to use IP version 6 addresses instead of IP version 4 addresses. The IP address can also be multiple IP addresses, a range of IP addresses, and a CIDR IP address range like 192.168.1.0/24 if you want to cover a large consecutive range of IP addresses. You can also include other domain names as desired that are officially allowed to send emails on behalf of your domain, which is often the case with legitimate businesses using very large email vendors (like Microsoft and Google) or marketing firms. If so, you can configure SPF to allow sending from “third-party” domains using the following syntax, which has an “include” statement:

```
```
v=spf1[ip4/6:] [publicIPAddressesofemailservers]
[include:[3rdpartydomainnames]] -all
```
```