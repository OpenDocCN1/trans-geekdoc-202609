

## 查找所有权的变更

在在上一个示例中，我们看到大多数 WHOIS 记录通过私有注册被锁定（图 9.23）。

![](img/ceaab52f5a948b18995b8efe89758781_212_0.png)

图 9.23

通过查看历史列表，我们可以看到域名最后一次非私有注册数据是在 2014 年 3 月 1 日（图 9.24）。

![](img/ceaab52f5a948b18995b8efe89758781_212_1.png)

图 9.24

# 第 9 章 ■ WHOIS 195

> **注意** 友情提醒，示例中的所有名称、地址、电话号码和电子邮件（大部分情况下）都将被更改。如果你在家里尝试，你的结果可能会有所不同。

我们可以看到，在 2014 年 3 月 1 日域名注册开放到 2015 年 10 月 18 日变为私有之间，存在着巨大的时间间隔（超过一年）。这可能表明所有权发生了变化，由于是所有权失效（即域名过期）。这是我们可以（并且应该）确认的内容。

在检查了 2014 年域名注册库后，图 9-25 显示该域名由英国伦敦 Westbury Court 178 号的 Johnny Framerson 拥有。

```
Domain Name: FREEPACKET.COM
Registry ID: 
Registrar Server: whois.freeaking.co.uk
Registrar URL:
Updated Date: 05-Feb-2014
Creation Date: 25-Dec-2013
Registrar Registration Date: 25-Dec-2013
Registrar: Freeaking Registrants Inc
Registrar IANA ID: 83
Admin Abuse Contact Email:
Admin Abuse Contact Phone:
Domain Status: REDEMPTIONPERIOD
Registrant Registration ID: DI_20084243
Registrant Name: Domain Contact (42986)
Registrant Organization: Johnny Framerson
Registrant Street: 178 Westbury Court
Registrant City: London
Registrant State/Province: England
Registrant Postal Code: EH6 6RU
Registrant Country: GB
Registrant Phone: +44.3456789123
Registrant Phone Ext:
Registrant Fax:
Registrant Fax Ext:
Registrant Email: johnnyboy@fakemail.com
Registrant Admin ID: DI_20084244
```

图 9-25

查看 Domain Status（域名状态），我们可以看到域名处于“REDEMPTIONPERIOD（赎回期）”，这表明 Johnny 在这段时间让域名过期了。WhitePacket 的当前所有者可能与 2014 年拥有该域名的人不是同一个人。

虽然在技术上，2014 年的所有者可能让域名过期，然后在 2015 年以私有注册状态买回，但这种这种情况看起来不太可能。

然而，这是需要记在心上的这一点。有很多原因导致某人会让域名过期，然后使用私有注册再次买回。例如，也许这个威胁者非常聪明，他知道自己想将该域名用于恶意目的，并预料到了这类调查。虽然极不可能是，但你永远无法确定。

## 反向 WHOIS (Reverse WHOIS)

我们现在拥有了关于 WhitePacket.com 可能所有者的追溯到 2014 年的一些信息。这就是反向 WHOIS 搜索派上用场。反向 WHOIS 搜索引擎允许我们通过搜索姓名、公司电话、物理地址或电子邮件地址来（反向）查询域名所有权。你的搜索结果将是一个域名列表，这些域名的 WHOIS 记录中包含了你的搜索内容。9.26 显示了 DomainTools 反向 WHOIS 搜索框。

![](img/ceaab52f5a948b18995b8efe89758781_214_0.png)

图 9.26

让我们看看是否能找到由我们的新线索 Johnny Framerson 拥有的额外域名。图 9.27 显示了包含“Johnny”和“Framerson”“所有单词”的 WHOIS 记录的搜索结果。

![](img/ceaab52f5a948b18995b8efe89758781_214_1.png)

图 9.27

结果返回了三个活跃域名（我们无法显示，抱歉）。一个很不错的发现！现在我们拥有了同样由 Framerson 先生拥有的新且活跃的域名。默认结果只会向我们显示活跃且由搜索人员拥有的域名。这太棒了，但你注意到图 9.27 右侧写着“Add history and get（添加历史并获取）”的链接了吗？这将添加他以前拥有的域名！9.28 显示了我们点击该链接后的新结果。

| 域名名称 | 创建日期 | 注册商 |
| :--- | :--- | :--- |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2003-07-22 | LIMITED |
| ... | 2010-03-03 | fastdomain inc. |
| ... | 2010-04-14 | enom, inc. |
| ... | 2014-07-10 | DOMAIN.COM, LLC |
| ... | 2017-12-30 | DOMAIN.COM, LLC |
| ... | 2015-05-09 | NET, INC. |
| ... | 2015-12-28 | DOMAIN.COM, LLC |
| ... | 2005-10-27 | TUCO, INC |
| ... | 2017-09-28 | DOMAIN.COM, LLC |

图 9.28

砰！我们有了此人以前拥有的 37 个域名。那非常多。我希望你做好了详细的笔记并建立了良好的跟踪系统，因为这意味着需要大量的额外调查来寻找线索！我们将在下一章中调查其中的几个域名。

## 交叉检查所有信息

我无法告诉你我忘记做过多少次了。这需要自律和大量的组织工作。在我们检查了 2014 年域名注册库后，图 9-25 显示该域名由英国伦敦 Westbury Court 178 号的 Johnny Framerson 拥有。

```
Domain Name: FREEPACKET.COM
Registry ID: 
Registrar Server: whois.freeaking.co.uk
Registrar URL:
Updated Date: 05-Feb-2014
Creation Date: 25-Dec-2013
Registrar Registration Date: 25-Dec-2013
Registrar: Freeaking Registrants Inc
Registrar IANA ID: 83
Admin Abuse Contact Email:
Admin Abuse Contact Phone:
Domain Status: REDEMPTIONPERIOD
Registrant Registration ID: DI_20084243
Registrant Name: Domain Contact (42986)
Registrant Organization: Johnny Framerson
Registrant Street: 178 Westbury Court
Registrant City: London
Registrant State/Province: England
Registrant Postal Code: EH6 6RU
Registrant Country: GB
Registrant Phone: +44.3456789123
Registrant Phone Ext:
Registrant Fax:
Registrant Fax Ext:
Registrant Email: johnnyboy@fakemail.com
Registrant Admin ID: DI_20084244
```

图 9-25

查看 Domain Status，我们可以看到域名处于“REDEMPTIONPERIOD”，这表明 Johnny 在这段时间让域名过期了。WhitePacket 的当前所有者可能与 2014 年拥有该域名的人不是同一个人。

虽然在技术上，2014 年的所有者可能让域名过期，然后在 2015 年以私有注册状态买回，但这种情况看起来不太可能。

然而，这是需要记在心上的这一点。有很多原因导致某人会让域名过期，然后使用私有注册再次买回。例如，也许这个威胁者非常聪明，他知道自己想将该域名用于恶意目的，并预料到了这类调查。虽然极不可能是，但你永远无法确定。

## 反向 WHOIS (Reverse WHOIS)

我们现在拥有了关于 WhitePacket.com 可能所有者的追溯到 2014 年的一些信息。这就是反向 WHOIS 搜索派上用场。反向 WHOIS 搜索引擎允许我们通过搜索姓名、公司电话、物理地址或电子邮件地址来（反向）查询域名所有权。你的搜索结果将是一个域名列表，这些域名的 WHOIS 记录中包含了你的搜索内容。9.26 显示了 DomainTools 反向 WHOIS 搜索框。

![](img/ceaab52f5a948b18995b8efe89758781_214_0.png)

图 9.26

让我们看看是否能找到由我们的新线索 Johnny Framerson 拥有的额外域名。图 9.27 显示了包含“Johnny”和“Framerson”“所有单词”的 WHOIS 记录的搜索结果。

![](img/ceaab52f5a948b18995b8efe89758781_214_1.png)

图 9.27

结果返回了三个活跃域名（我们无法显示，抱歉）。一个很不错的发现！现在我们拥有了同样由 Framerson 先生拥有的新且活跃的域名。默认结果只会向我们显示活跃且由搜索人员拥有的域名。这太棒了，但你注意到图 9.27 右侧写着“Add history and get（添加历史并获取）”的链接了吗？这将添加他以前拥有的域名！9.28 显示了我们点击该链接后的新结果。

| 域名名称 | 创建日期 | 注册商 |
| :--- | :--- | :--- |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2003-07-22 | LIMITED |
| ... | 2010-03-03 | fastdomain inc. |
| ... | 2010-04-14 | enom, inc. |
| ... | 2014-07-10 | DOMAIN.COM, LLC |
| ... | 2017-12-30 | DOMAIN.COM, LLC |
| ... | 2015-05-09 | NET, INC. |
| ... | 2015-12-28 | DOMAIN.COM, LLC |
| ... | 2005-10-27 | TUCO, INC |
| ... | 2017-09-28 | DOMAIN.COM, LLC |

图 9.28

砰！我们有了此人以前拥有的 37 个域名。那非常多。我希望你做好了详细的笔记并建立了良好的跟踪系统，因为这意味着需要大量的额外调查来寻找线索！我们将在下一章中调查其中的几个域名。

## 交叉检查所有信息

我无法告诉你我忘记做过多少次了。这需要自律和大量的组织工作。在我们检查了 2014 年域名注册库后，图 9-25 显示该域名由英国伦敦 Westbury Court 178 号的 Johnny Framerson 拥有。

```
Domain Name: FREEPACKET.COM
Registry ID: 
Registrar Server: whois.freeaking.co.uk
Registrar URL:
Updated Date: 05-Feb-2014
Creation Date: 25-Dec-2013
Registrar Registration Date: 25-Dec-2013
Registrar: Freeaking Registrants Inc
Registrar IANA ID: 83
Admin Abuse Contact Email:
Admin Abuse Contact Phone:
Domain Status: REDEMPTIONPERIOD
Registrant Registration ID: DI_20084243
Registrant Name: Domain Contact (42986)
Registrant Organization: Johnny Framerson
Registrant Street: 178 Westbury Court
Registrant City: London
Registrant State/Province: England
Registrant Postal Code: EH6 6RU
Registrant Country: GB
Registrant Phone: +44.3456789123
Registrant Phone Ext:
Registrant Fax:
Registrant Fax Ext:
Registrant Email: johnnyboy@fakemail.com
Registrant Admin ID: DI_20084244
```

图 9-25

查看 Domain Status，我们可以看到域名处于“REDEMPTIONPERIOD”，这表明 Johnny 在这段时间让域名过期了。WhitePacket 的当前所有者可能与 2014 年拥有该域名的人不是同一个人。

虽然在技术上，2014 年的所有者可能让域名过期，然后在 2015 年以私有注册状态买回，但这种情况看起来不太可能。

然而，这是需要记在心上的这一点。有很多原因导致某人会让域名过期，然后使用私有注册再次买回。例如，也许这个威胁者非常聪明，他知道自己想将该域名用于恶意目的，并预料到了这类调查。虽然极不可能是，但你永远无法确定。

## 反向 WHOIS (Reverse WHOIS)

我们现在拥有了关于 WhitePacket.com 可能所有者的追溯到 2014 年的一些信息。这就是反向 WHOIS 搜索派上用场。反向 WHOIS 搜索引擎允许我们通过搜索姓名、公司电话、物理地址或电子邮件地址来（反向）查询域名所有权。你的搜索结果将是一个域名列表，这些域名的 WHOIS 记录中包含了你的搜索内容。9.26 显示了 DomainTools 反向 WHOIS 搜索框。

![](img/ceaab52f5a948b18995b8efe89758781_214_0.png)

图 9.26

让我们看看是否能找到由我们的新线索 Johnny Framerson 拥有的额外域名。图 9.27 显示了包含“Johnny”和“Framerson”“所有单词”的 WHOIS 记录的搜索结果。

![](img/ceaab52f5a948b18995b8efe89758781_214_1.png)

图 9.27

结果返回了三个活跃域名（我们无法显示，抱歉）。一个很不错的发现！现在我们拥有了同样由 Framerson 先生拥有的新且活跃的域名。默认结果只会向我们显示活跃且由搜索人员拥有的域名。这太棒了，但你注意到图 9.27 右侧写着“Add history and get（添加历史并获取）”的链接了吗？这将添加他以前拥有的域名！9.28 显示了我们点击该链接后的新结果。

| 域名名称 | 创建日期 | 注册商 |
| :--- | :--- | :--- |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2003-07-22 | LIMITED |
| ... | 2010-03-03 | fastdomain inc. |
| ... | 2010-04-14 | enom, inc. |
| ... | 2014-07-10 | DOMAIN.COM, LLC |
| ... | 2017-12-30 | DOMAIN.COM, LLC |
| ... | 2015-05-09 | NET, INC. |
| ... | 2015-12-28 | DOMAIN.COM, LLC |
| ... | 2005-10-27 | TUCO, INC |
| ... | 2017-09-28 | DOMAIN.COM, LLC |

图 9.28

砰！我们有了此人以前拥有的 37 个域名。那非常多。我希望你做好了详细的笔记并建立了良好的跟踪系统，因为这意味着需要大量的额外调查来寻找线索！我们将在下一章中调查其中的几个域名。

## 交叉检查所有信息

我无法告诉你我忘记做过多少次了。这需要自律和大量的组织工作。在我们检查了 2014 年域名注册库后，图 9-25 显示该域名由英国伦敦 Westbury Court 178 号的 Johnny Framerson 拥有。

```
Domain Name: FREEPACKET.COM
Registry ID: 
Registrar Server: whois.freeaking.co.uk
Registrar URL:
Updated Date: 05-Feb-2014
Creation Date: 25-Dec-2013
Registrar Registration Date: 25-Dec-2013
Registrar: Freeaking Registrants Inc
Registrar IANA ID: 83
Admin Abuse Contact Email:
Admin Abuse Contact Phone:
Domain Status: REDEMPTIONPERIOD
Registrant Registration ID: DI_20084243
Registrant Name: Domain Contact (42986)
Registrant Organization: Johnny Framerson
Registrant Street: 178 Westbury Court
Registrant City: London
Registrant State/Province: England
Registrant Postal Code: EH6 6RU
Registrant Country: GB
Registrant Phone: +44.3456789123
Registrant Phone Ext:
Registrant Fax:
Registrant Fax Ext:
Registrant Email: johnnyboy@fakemail.com
Registrant Admin ID: DI_20084244
```

图 9-25

查看 Domain Status，我们可以看到域名处于“REDEMPTIONPERIOD”，这表明 Johnny 在这段时间让域名过期了。WhitePacket 的当前所有者可能与 2014 年拥有该域名的人不是同一个人。

虽然在技术上，2014 年的所有者可能让域名过期，然后在 2015 年以私有注册状态买回，但这种情况看起来不太可能。

然而，这是需要记在心上的这一点。有很多原因导致某人会让域名过期，然后使用私有注册再次买回。例如，也许这个威胁者非常聪明，他知道自己想将该域名用于恶意目的，并预料到了这类调查。虽然极不可能是，但你永远无法确定。

## 反向 WHOIS (Reverse WHOIS)

我们现在拥有了关于 WhitePacket.com 可能所有者的追溯到 2014 年的一些信息。这就是反向 WHOIS 搜索派上用场。反向 WHOIS 搜索引擎允许我们通过搜索姓名、公司电话、物理地址或电子邮件地址来（反向）查询域名所有权。你的搜索结果将是一个域名列表，这些域名的 WHOIS 记录中包含了你的搜索内容。9.26 显示了 DomainTools 反向 WHOIS 搜索框。

![](img/ceaab52f5a948b18995b8efe89758781_214_0.png)

图 9.26

让我们看看是否能找到由我们的新线索 Johnny Framerson 拥有的额外域名。图 9.27 显示了包含“Johnny”和“Framerson”“所有单词”的 WHOIS 记录的搜索结果。

![](img/ceaab52f5a948b18995b8efe89758781_214_1.png)

图 9.27

结果返回了三个活跃域名（我们无法显示，抱歉）。一个很不错的发现！现在我们拥有了同样由 Framerson 先生拥有的新且活跃的域名。默认结果只会向我们显示活跃且由搜索人员拥有的域名。这太棒了，但你注意到图 9.27 右侧写着“Add history and get（添加历史并获取）”的链接了吗？这将添加他以前拥有的域名！9.28 显示了我们点击该链接后的新结果。

| 域名名称 | 创建日期 | 注册商 |
| :--- | :--- | :--- |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2005-12-01 | webfusion ltd. |
| ... | 2003-07-22 | LIMITED |
| ... | 2010-03-03 | fastdomain inc. |
| ... | 2010-04-14 | enom, inc. |
| ... | 2014-07-10 | DOMAIN.COM, LLC |
| ... | 2017-12-30 | DOMAIN.COM, LLC |
| ... | 2015-05-09 | NET, INC. |
| ... | 2015-12-28 | DOMAIN.COM, LLC |
| ... | 2005-10-27 | TUCO, INC |
| ... | 2017-09-28 | DOMAIN.COM, LLC |

图 9.28

砰！我们有了此人以前拥有的 37 个域名。那非常多。我希望你做好了详细的笔记并建立了良好的跟踪系统，因为这意味着需要大量的额外调查来寻找线索！我们将在下一章中调查其中的几个域名。

## 总结

本章涵盖了 WHOIS 搜索的基础知识，包括用于识别域名所有权的几种免费和付费服务。并非所有服务都是同质的，这是一个你极可能需要花费资金获取最佳结果的领域。遗憾的是，目前没有查询免费 WHOIS 数据的优秀工具或解决方案，而且你搜索的时间越远，服务的费用就越高。

在下一章中，我们将学习如何使用证书透明度日志来识别域名所有者，以及使用互联网档案如 Wayback Machine。

