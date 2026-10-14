
High-rate DDoS (HDDoS) and low-rate DDoS (LDDoS) (Daffu etal., 2017), which are often referred to as brute force and semantic attacks (Liu etal., 2019), respectively, are two categories into which denial of service (DDoS) attacks typically fall. The high-rate attack is capable of a volume of more than 500 Gbps and attempts to either prevent actual users from connecting, which is referred to as a recourse depletion attack is a type of bandwidth depletion attack that make cloud services unavailable ([Radain etal., 2021](#ch30.xhtml#ref30_13)). Attackers use a brute-force attack, also known as a flooding attack or a high-rate DDoS attack, to send enormous malicious requests that completely absorb the network capacity of the targeted cloud server ([Alanazi etal., 2019](#ch30.xhtml#ref30_15)). On the other hand, vulnerabilities in protocols can be accessed using semantic attacks, also known as vulnerability attacks, rather than by consuming any available network or cloud computing resources. To specifically target a certain protocol or application, the attacker creates a small amount of malicious traffic. These types of attacks are also referred to as low-rate attacks on distributed denial of service. Low-rate attack traffic approaches legal traffic in appearance. As a result, low-rate DDoS attacks consequently are harder to identify than high-rate DDoS attacks ([Alanazi (2019](#ch30.xhtml#ref30_15))).

## Based on botnet-attack

Botnets can be used as part of a DDoS attack. Malware can be installed on servers to build botnets that can then be used to launch DDoS attacks on a server ([Sanjeetha etal.,2021](#ch30.xhtml#ref30_18); [Brar et al., 2022](#ch30.xhtml#ref30_6)). This section provides an overview of the botnet’s architecture and the tools used to perform DDoS flooding attacks. If an attacker uses botnets or zombies, developing an effective and efficient defense mechanism becomes more difficult. This is primarily due to two causes. First, many zombies would be participating in the attacks to increase their size and disruptiveness. Second, it is clear that zombies operating under the attacker’s command use faked IP addresses, making it very difficult to track them back ([Kesavamoorthy etal., 2020](#ch30.xhtml#ref30_3)) ([Figure 30.3](#ch30.xhtml#fig30_3)).

![Figure 30.3 Botnet-based DDoS](images/fig30_3_C.jpg)

[Figure 30.3 Botnet-based DDoS](#ch30.xhtml#R_fig30_3)

IRC Botnet –Most bots are useful and safe and essential to the performance of the internet. The earliest internet bots enabled classroom activity using the internet relay chat (IRC) protocol (Wainwright etal., 2019; [Singh et al., 2020](#ch30.xhtml#ref30_17)). Some operates of the IRC botnet.

Compromising devices –Are often operated via an IRC botnet. The attacker uses malware or vulnerabilities to infect a significant amount of devices, including computers, servers, and IoT devices.

IRC communication –On the infected devices, the bot virus creates a connection to an IRC server.

Command and management –Using an IRC server, the botnet operator gives orders and directives to the bots.

Activity on a botnet –The bots execute the given actions after receiving instructions from the IRC server.

Update andmaintaining –The IRC botnet can communicate with the botnet operator via the IRC server to get updates or new instructions.

Web/HTTP botnet –A drive-by download, spam, and other similar methods are typically used to download an HTTP-based bot at first. Consequently, a particular constant-size transmission between an infected host and a new target is generated.HTTP botnets only communicate with their C…C servers sometimes to obtain requests, rather than maintain a continuous connection (Letteri etal., 2020). Web-based bots can be set up and run and managed via complicated PHP scripts, which also implement encryption over the HTTP (port 80) or HTTPS (port 443) protocols for communication ([Kesavamoorthy etal., 2020](#ch30.xhtml#ref30_3)).

## Conclusion

The basic information about cloud computing and its layer-based design, including the risks of DDoS attacks, was covered in this paper. DDoS attacks, which try to overload a target system by flooding it with overwhelming traffic or resource requests, are well-known as an extreme risk to online services and networks. DDoS attacks can be categorized according to the characteristics of the attack flow, application-level flooding attacks, and Botnet-based DDoS attacks are one particular kind of DDoS attack. In these attacks, an attacker is in control of a botnet, which is a network of compromised devices. By commanding the bots to flood the target system with traffic, the attacker may instruct the botnet to perform DDoS attacks. Organizations need to have strong security measures set up if they want to reduce the risks imposed by the context of cloud computing, and attacks using DDoS.

## References

*   [Abusaimeh, Hesham](#ch30.xhtml#R_ref30_1). (2020). Distributed denial of service attacks in cloud computing. International Journal of Advanced Computer Science and Applications, 11(6). 1–6.

*   [Kati, Sherwin, Abhishek Ove, Bhavana Gotipamul, Mayur Kodche, and Swati Jaiswal](#ch30.xhtml#R_ref30_2). (2020). Comprehensive Overview of DDOS Attack in Cloud Computing Environment using different Machine Learning Techniques. Available at SSRN 4096388. Proceedings of the International Conference on Innovative Computing & Communication (ICICC) 2022, 1–14.

*   [Kesavamoorthy, R., Alaguvathana, P., Suganya, R., and Vigneshwaran, P.](#ch30.xhtml#R_ref30_3) (2020). Classification of DDoS attacks–A survey. Test Engg. Manag., 83, 12926–12932.

*<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1. 重新划分标题层级，使其符合 Markdown 标准，确保 # 用于最高层级标题，## 用于次级标题，### 用于子标题或子部分。 2. 删除多余空行，确保每段文字紧凑排列。 3. 保留所有原始内容，包括引用、引用标记和引用格式。 4. 为所有出现<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1. 重新划分标题层级（保留合理的# ## ###结构）  
2. 优化段落格式，删除多余空行  
3. 保留正文核心内容  
4. 所有单独出现的变<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1. 重新划分标题层级（保留合理的# ## ###结构）
2. 优化段落格式，删除多余空行
3. 保留正<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 2020). 

Web/HTTP botnet –A drive-by download, spam, and other similar methods are typically used to download an HTTP-based bot at first. Consequently, a particular constant-size transmission between an infected host and a new target is generated. HTTP botnets only communicate with their C…C servers sometimes to obtain requests, rather than maintain a continuous connection (Letteri etal., 2020). Web-based bots can be set up and run and managed via complicated PHP scripts, which also implement encryption over the HTTP (port 80) or HTTPS (port 443) protocols for communication ([Kesavamoorthy etal., 2020](#ch30.xhtml#ref30_3)).
