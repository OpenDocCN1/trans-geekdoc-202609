
1. 显示的序列号并非真实的序列号。

2. 显示的序列号尚未递增。

3. 显示的序列号不足。

4. 显示的序列号是确认号。

18. 关于 Wireshark 提供的 `[TCP Segment Len: 35]`，你能说些什么？

1. 窗口大小已变化。

2. Wireshark 推断了该信息。

3. Wireshark 从头部信息中提取了它。

4. Wireshark 在下方有更多细节。

19. 端口桥接（port spanning）能克服什么问题？

1. 交换机不支持第 3 层。

2. 交换机聚合端口。

3. 交换机过滤流量。

4. 交换机不可靠。

20. `/etc/ettercap/etter.dns` 文件的用途是什么？

1. 为 Ettercap 启用防火墙规则

2. 配置主机名到 IP 地址

3. 为 Ettercap 设置邮件

4. 在 Ettercap 中禁用 ARP 欺骗

21. 如果在 `ifconfig` 输出中看到以下内容，你能说是什么情况正在发生？

```
eth0: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
options=50b<RXCSUM,TXCSUM,VLAN_HWTAGGING,AV,CHANNEL_IO>
ether 14:98:77:31:b2:33
 inet6 fe80::10c6:713a:e86f:556d%en0 prefixlen 64 secured scopeid 0x7
 inet 192.168.1.144 netmask 0xffffff00 broadcast 192.168.1.255
 inet6 2601:18d:8b7f:e33a::52 prefixlen 64 dynamic
 inet6 fd23:5d5f:cd75:40d2:87:38bc:9448:3407 prefixlen 64 autoconf secured
 nd6 options=201<PERFORMNUD,DAD>
 media: autoselect (1000baseT <full-duplex,flow-control,energy-efficient-ethernet)
 status: active
```

1. ARP 欺骗攻击

2. ARP 洪水攻击

3. 网络嗅探

4. 中间人攻击

22. 以下哪项不是 DHCP 餓餓（starvation）攻击对受害者的结果？

1. 攻击者获取新 IP 地址

2. 攻击者设置默认网关

3. 攻击者设置 DNS 服务器

4. 服务拒绝

23. 如果你在网络中突然看到大量的 DHCPDISCOVER 包，你可能会开始调查什么？

1. ARP 欺骗

2. 网络嗅探

3. DHCP 餓餓攻击

4. DNS 中毒

24. 哪种网络技术让攻击者更难进行嗅探？

1. 集线器

2. DHCP

3. 交换机

4. 邮件服务器

25. 如果你的 `sslstrip` 会话进行得不顺利，你可能会怀疑什么？

1. 所有会话都是 SSL v3。

2. 所有会话都是 TLS v1.0。

3. 所有会话都是 TLS v1.1。

4. 所有会话都是 TLS v1.3。

# Chapter 10  

Social Engineering

At the time this is being written, about 80 percent of attacks are thought to involve social engineering of some sort. This makes learning about social engineering significant. If the attackers are using it, you should be using it too. Ultimately, social engineering attacks are going to be very effective avenues into a network so you can continue to perform testing. This would be especially true when it comes to red teaming, where you are likely to have the cuffs taken off, as it were, and you have more latitude in your tactics.

You may be familiar with some basic social engineering strategies like phishing, simply because it's so common. Social engineering isn't just about sending emails, though. There are other social engineering strategies. Ultimately, any means of manipulating someone to do something they shouldn't or wouldn't otherwise do is social engineering. Social engineering brings in a lot of psychology and elements of human nature, so essentially you are using the way people are against them.

Beyond the basics of social engineering, including how and why it works, there is also social engineering outside the virtual world. A skilled social engineer can get a lot of people to do what the engineer wants them to do. In the digital space, there is phishing, of course, but even phishing can make use of other elements, including rogue websites. Rogue websites may be used even without the phishing component, and they are called *rogue* because either they are controlled by an attacker or there may be malware installed by an attacker within a legitimate website.

Speaking of rogue, an attacker may create a rogue wireless access point. This would be done to lure people to connect to what they believe is a trusted wireless network. Creating rogue networks, as well as other aspects of social engineering, can be automated to take the time out of setting them up. We'll cover all of this over the course of this chapter.

## Social Engineering

Social engineering, regardless of what it was called or how it was thought of, has been around probably as long as humans have been around. You may call it manipulation if you like, but in the information security community, it's called *social engineering*. The objective is to convince or manipulate someone into doing something they wouldn't normally do for someone they don't know. There are a number of techniques for doing that. They are generally considered to be related to the science of influence. Robert Cialdini proposed six principles as part of his theory of influence. They are as follows, and understanding these principles may help you start to understand how to influence or manipulate people:

*   **Reciprocity**   People will generally feel like they want to or may be obligated to respond to a kindness or favor. You may feel this way if a company gives away free samples. If you get one of these free samples, you may be inclined to feel like you should buy the product in response.

*   **Commitment**   If someone commits to something, either in writing or orally, they are more inclined to follow through on that commitment.

*   **Social Proof**   Think about social proof as peer influence. If you see someone else doing something, such as using a product, you will see that it is acceptable to do that. You may therefore be more willing to try the product, or whatever it is you've seen.

*   **Authority**   If you've ever been pulled over by the police, you can recognize this one. Even if you haven't, you may think back to being at school. In general, people are inclined to follow authority figures and do what they say or ask.

*   **Liking**   If you like someone, you may be more easily swayed by what they think or do.

*   **Scarcity**   This is easy to recognize. Think about Cabbage Patch Kids, if you go back that far, and also many of the product rollouts by Apple. The lack of availability of these products increases their perceived value. The perception of increased value makes them more desirable.

Many of these go back to the early origins of humanity. Think about social proof as an example. If you were to see your neighbor eating something and then not dying, you would be more inclined to eat that thing yourself. You have proof that it's safe. Similarly, humans have long relied on one another to survive. If your neighbor does something for you, you would do something for them because that is how communities work. Essentially, these are deep‑seated modes of behaving because of the way our brains and neurochemistry work. We are wired to be susceptible to social engineering and scams because from an evolutionary standpoint we needed one another to survive, so trust is important.
