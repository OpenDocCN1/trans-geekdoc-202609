
使用真实地址，除非他们是在信用卡支付时检查账单地址。事实上，有些时候我注册的域名使用的是虚假电话号码和错误地址。由于数据是公开的，因此要注意分享的内容。任何人都可以挖掘注册表获取这些信息，并用于各种目的。

不过，在深入探讨之前，你很可能需要了解互联网在域名和地址方面的治理方式。首先，有互联网名称与数字地址分配机构（ICANN）。ICANN之下是互联网数字名称与地址分配机构（IANA），负责管理与互联网运行相关的IP地址、端口、协议及其他基本数字。在ICANN于1998年成立之前，IANA的职能由一人管理，即Jon Postel，他还维护了请求评论（RFC）文档。

除了负责编号的ICANN之外，还有域名注册商。这些组织存储其负责的地址及联系人信息。曾经有一段时间，注册域名和其他数据都通过单一实体完成。不过，现在有几家公司可以执行注册商职能。如果你想注册域名，可以去DomainMonger或GoDaddy等注册商公司。然后可以查询这些公司以获取域名详细信息。

为了从区域互联网注册表（RIR）获取信息，你会使用whois程序。这是一个可以在大多数类Unix系统（包括Linux和MacOS）的命令行上使用的程序。如果你手头没有类Unix系统，也有提供whois实现的网站。下面，你可以看到whois查询输出的一部分。

```
$ whois wiley.com
% IANA WHOIS server
% for more information on IANA, visit http://www.iana.org
% This query returned 1 object

refer:        whois.verisign-grs.com

domain:       COM

organisation: VeriSign Global Registry Services
address:      12061 Blumont Way
address:      Reston Virginia 20190
address:      United States
phone: +1 703 925-6999
fax-no: +1 703 948 3978
e-mail: info@verisign-grs.com
<- SNIP ->
Domain Name: wiley.com
Registry Domain ID: 936038_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.corporatedomains.com
Registrar URL: www.cscprotectsbrands.com
Updated Date: 2017-10-07T05:19:30Z
Creation Date: 1994-10-12T04:00:00Z
Registrar Registration Expiration Date: 2019-10-11T04:00:00Z
Registrar: CSC CORPORATE DOMAINS, INC.
Registrar IANA ID: 299
Registrar Abuse Contact Email: domainabuse@cscglobal.com
Registrar Abuse Contact Phone: +1.8887802723
Domain Status: clientTransferProhibited
http://www.icann.org/epp#clientTransferProhibited
Registry Registrant ID:
Registrant Name: Domain Administrator
Registrant Organization: John Wiley & Sons, Inc
Registrant Street: 111 River Street
Registrant City: Hoboken
Registrant State/Province: NJ
Registrant Postal Code: 07030
Registrant Country: US
Registrant Phone: +1.3175723355
Registrant Phone Ext:
Registrant Fax: +1.3175724355
Registrant Fax Ext:
Registrant Email: domains@wiley.com
Registry Admin ID:
Admin Name: Domain Administrator
Admin Organization: John Wiley & Sons, Inc
Admin Street: 111 River Street
Admin City: Hoboken
Admin State/Province: NJ
Admin Postal Code: 07030
Admin Country: US
Admin Phone: +1.3175723355
Admin Phone Ext:
Admin Fax: +1.3175724355
Admin Fax Ext:
Admin Email: domains@wiley.com
```

↓ 对wiley.com的whois查询

输出内容很多需要查看，我删减了大部分，只保留真正相关的信息。首先，whois会查询IANA的whois服务器，以确定需要联系谁来处理这个特定域名。你可以在输出的最顶部看到这种情况。IANA指示Verisign是该域名的注册商。我们获取了注册商Verisign的详细信息。之后，在删减了大量信息后，我们终于得到了域名wiley.com的详细信息。在输出中可以看到公司的地址和电话号码。此外，你还能看到公司的一些联系人信息。注册商期望有行政联系人和技术联系人。

如前所述，并非所有域名都会提供这么详细的信息。一个不包含任何联系信息的域名示例是spamhaus.org。下面，你可以看到联系信息显示数据已因隐私原因被编辑。

## 关于spamhaus.org的详细信息

```
Registry Registrant ID: REDACTED FOR PRIVACY
Registrant Name: REDACTED FOR PRIVACY
Registrant Organization: The Spamhaus Project
Registrant Street: REDACTED FOR PRIVACY
Registrant City: REDACTED FOR PRIVACY
Registrant State/Province:
Registrant Postal Code:
Registrant Country: CH
Registrant Phone: REDACTED FOR PRIVACY
Registrant Phone Ext:
Registrant Fax: REDACTED FOR PRIVACY
Registrant Fax Ext:
Registrant Email: 26a60f47fb7b1b2a0e5ea9927ed7f15c-666344@contact.gandi.net
Registry Admin ID: REDACTED FOR PRIVACY
Admin Name: REDACTED FOR PRIVACY
Admin Organization: REDACTED FOR PRIVACY
Admin Street: REDACTED FOR PRIVACY
Admin City: REDACTED FOR PRIVACY
Admin State/Province: REDACTED FOR PRIVACY
Admin Postal Code: REDACTED FOR PRIVACY
Admin Country: REDACTED FOR PRIVACY
Admin Phone: REDACTED FOR PRIVACY
Admin Phone Ext:
Admin Fax: REDACTED FOR PRIVACY
Admin Fax Ext:
Admin Email: a25006f8175341e32979e6f59e7b87ea-178660@contact.gandi.net
```

使用这种策略可以保护信息隐私，防止落入spamhaus.org所要防范的人手中。提供的数据可用于为发送垃圾邮件者创建邮件列表。也可用于为传统垃圾邮件提供商（有时称为直邮营销公司）创建实体邮件列表。

## 区域互联网注册表

然而，并非所有有用信息都存储在域名注册商处。还有其他重要数据需要保存。前面我们讨论过IANA。虽然IANA服务器提供关于域名注册商的信息，但其长期目的是作为地址的中央清算所。这不仅包括众所周知服务的端口号，还包括IP地址。从高层来看，IANA拥有所有IP地址。它根据需求将这些IP地址分配给RIR。RIR随后将其分配给其地理区域内的组织。

全球有五个RIR。它们位于不同的地理区域，组织会参考其所在位置的RIR来获取IP地址等信息。RIR及其负责的地理区域列在下面。

- 非洲网络信息中心 (AfriNIC) 非洲
- 互联网数字资源管理机构 (ARIN) 北美洲（美国和加拿大）以及南极洲和加勒比海部分地区。
- 亚太网络信息中心 (APNIC) 亚洲、澳大利亚、新西兰及邻近国家
- 拉丁美洲和加勒比海网络信息中心 (LACNIC) 拉丁美洲和加勒比海部分地区
- 欧洲IP网络协调中心 (RIPE NCC) 欧洲、俄罗斯、西亚和中亚

所有这些RIR都有自己的数据库，可以使用whois进行查询，就像我们使用whois查询域名注册商的信息一样。通常，你会针对RIR使用whois来查找特定IP地址的所有者。例如，在前面wiley.com的输出中，部分输出指示该域名使用哪个域名服务器来将主机名解析为IP地址。其中一个域名服务器是ns.wiley.co.uk。只需付出少量努力（我们将在本章后面介绍DNS），我们就可以发现主机名ns.wiley.co.uk解析为IP地址193.130.68.19。使用whois，我们可以查明谁拥有该IP地址。你可以在下面的代码中看到该查询的结果。
