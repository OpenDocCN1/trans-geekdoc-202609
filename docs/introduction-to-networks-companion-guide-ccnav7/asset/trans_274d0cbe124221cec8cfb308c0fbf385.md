
## Network Security (1.8)
网络安全 (1.8)

Security is a critical component in designing, implementing, and maintaining networks. Network engineers and administrators must always consider security risks and employ the proper mitigation methods before deploying any type of network service.
安全是设计、实施和维护网络中的关键组成部分。网络工程师和管理员在部署任何类型的网络服务之前必须始终考虑安全风险并采用适当的缓解方法。

### Security Threats (1.8.1)
安全威胁 (1.8.1)

You have, no doubt, heard or read news stories about a company network being breached, giving threat actors access to the personal information of thousands of customers. Network security is always going to be a top priority of administrators.
你无疑听说或读到过关于公司网络被入侵的新闻报道，导致威胁行为者能够访问数千名客户的个人信息。网络安全始终是管理员的首要优先事项。

Network security is an integral part of computer networking, regardless of whether the network is a home network with a single connection to the internet or a corporate network with thousands of users. Network security must consider the environment, as well as the tools and requirements of the network. It must be able to secure data while still allowing for the quality of service that users expect of the network.
无论是只有一个互联网连接的家庭网络还是拥有数千用户的企业网络，网络安全都是计算机网络不可或缺的一部分。网络安全必须考虑环境以及网络的工具和要求。它必须能够在保护数据的同时，仍允许用户对网络所期望的服务质量。

Securing a network involves using protocols, technologies, devices, tools, and techniques to protect data and mitigate threats. Threat vectors may be external or internal. Many external network security threats today originate from the internet.
保护网络涉及使用协议、技术、设备、工具和技术来保护数据并减轻威胁。威胁向量可能是外部的或内部的。许多当今的外部网络安全威胁源自互联网。

There are several common external threats to networks:
网络存在几种常见的外部威胁：

- **Viruses, worms, and Trojan horses:** These contain malicious software or code running on a user device.
- **病毒、蠕虫和特洛伊木马：** 这些包含在用户设备上运行的恶意软件或代码。
- **Spyware and adware:** These types of software are installed on a user's device to secretly collect information about the user.
- **间谍软件和广告软件：** 这类软件安装在用户的设备上，以秘密收集有关用户的信息。
- **Zero-day attacks:** Also called zero-hour attacks, these attacks occur on the first day that a vulnerability becomes known.
- **零日攻击：** 又称为零小时攻击，这些攻击发生在漏洞被发现的第一天。
- **Threat actor attacks:** In these attacks, malicious persons attack user devices or network resources.
- **威胁行为者攻击：** 在这些攻击中，恶意人员攻击用户设备或网络资源。
- **Denial-of-service attacks:** These attacks slow or crash applications and processes on a network device.
- **拒绝服务攻击：** 这些攻击会减慢或导致网络设备上的应用程序和进程崩溃。
- **Data interception and theft:** This type of attack involves capturing private information from an organization's network.
- **数据拦截和窃取：** 此类攻击涉及从组织的网络中捕获私人信息。
- **Identity theft:** This type of attack involves stealing the login credentials of a user in order to access private data.
- **身份盗窃：** 此类攻击涉及窃取用户的登录凭据以访问私人数据。

It is important to consider internal threats. Many studies have shown that the most common data breaches are related to internal network users. Such breaches may be attributed to lost or stolen devices, accidental misuse by employees, or even malicious employees. BYOD strategies make corporate data especially vulnerable. Therefore, when developing a security policy, it is important to address both external and internal security threats, as shown in Figure 1-24.
考虑内部威胁很重要。许多研究表明，最常见的数据泄露与内部网络用户有关。此类泄露可能归因于设备丢失或被盗、员工意外误用，甚至是恶意员工。BYOD 策略使企业数据尤其容易受到攻击。因此，在制定安全策略时，重要的是同时解决外部和内部安全威胁，如图 1-24 所示。

![](img/e71dc48d3ae3db3394e5857ab2acae75_70_0.png)

Figure 1-24 External and Internal Threats
图 1-24 外部和内部威胁

### Security Solutions (1.8.2)
安全解决方案 (1.8.2)

No single solution can protect a network from the variety of threats that exist. For this reason, security should be implemented in multiple layers, using more than one security solution. If one security component fails to identify and protect a network, others may succeed.
没有单一的解决方案可以保护网络免受存在的各种威胁。因此，安全应分层实施，使用不止一种安全解决方案。如果一个安全组件未能识别和保护网络，其他组件可能会成功。

A home network security implementation is usually rather basic. Typically, you implement it on the end devices, as well as at the point of connection to the internet. You may even be able to rely on contracted services from the ISP.
家庭网络安全实施通常相当基础。通常，你会在终端设备以及连接到互联网的接入点上实施它。你甚至可能能够依赖 ISP 提供的合同服务。

These are the basic security components for a home or small office network:
家庭或小型办公室网络的基本安全组件如下：

- **Antivirus and antispyware:** These applications help to protect end devices from becoming infected with malicious software.
- **防病毒和反间谍软件：** 这些应用程序有助于保护终端设备免受恶意软件感染。
- **Firewall filtering:** Firewall filtering blocks unauthorized access into and out of the network. This may include a host-based firewall system that prevents unauthorized access to the end device or a basic filtering service on the home router to prevent unauthorized access from the outside world into the network.
- **防火墙过滤：** 防火墙过滤阻止未经授权的网络进出访问。这可能包括基于主机的防火墙系统，防止未经授权访问终端设备，或家庭路由器上的基本过滤服务，防止外部世界未经授权访问网络。

In contrast, the network security implementation for a corporate network usually consists of many components built into the network to monitor and filter traffic. Ideally, all components work together to minimize maintenance and improve security. Larger networks and corporate networks use antivirus, antispyware, and firewall filtering, and they also have additional security requirements:
相比之下，企业网络的网络安全实施通常由内置于网络中的许多组件组成，用于监控和过滤流量。理想情况下，所有组件协同工作以最大限度地减少维护并提高安全性。大型网络和企业网络使用防病毒、反间谍软件和防火墙过滤，并且还具有额外的安全要求：

- **Dedicated firewall systems:** These provide more advanced firewall capabilities that can filter large amounts of traffic with more granularity.
- **专用防火墙系统：** 这些提供更先进的防火墙功能，可以更精细地过滤大量流量。
- **Access control lists (ACL):** ACLs further filter access and traffic forwarding based on IP addresses and applications.
- **访问控制列表 (ACL)：** ACL 根据 IP 地址和应用程序进一步过滤访问和流量转发。
- **Intrusion prevention systems (IPS):** These systems identify fast-spreading threats, such as zero-day or zero-hour attacks.
- **入侵防御系统 (IPS)：** 这些系统识别快速传播的威胁，例如零日或零小时攻击。
- **Virtual private networks (VPN):** These networks provide secure access into an organization for remote workers.
- **虚拟专用网络 (VPN)：** 这些网络为远程工作人员提供进入组织的 安全访问。

Network security requirements must consider the environment as well as the various applications and computing requirements. Both home and business environments must be able to secure their data while still allowing for the quality of service that users expect of each technology. In addition, any security solution that is implemented must be adaptable to the growing needs of the network and changing trends.
网络安全要求必须考虑环境以及各种应用程序和计算要求。家庭和企业环境都必须能够在保护数据的同时，仍允许用户对每项技术所期望的服务质量。此外，实施的任何安全解决方案都必须能够适应网络不断增长的需求和不断变化的趋势。

The study of network security threats and mitigation techniques starts with a clear understanding of the underlying switching and routing infrastructure used to organize network services.
网络安全威胁和缓解技术的研究始于对用于组织网络服务的底层交换和路由基础设施的清晰理解。

### Check Your Understanding—Network Security (1.8.3)
检查你的理解——网络安全 (1.8.3)

Refer to the online course to complete this activity.
请参考在线课程完成此活动。

![](img/e71dc48d3ae3db3394e5857ab2acae75_71_0.png)

## The IT Professional (1.9)
IT 专业人员 (1.9)

The role of an IT professional is constantly evolving. An IT professional is always learning in an ever-changing environment.
IT 专业人员的角色不断发展。IT 专业人员在不断变化的环境中始终在学习。

### CCNA (1.9.1)
CCNA (1.9.1)

As a NetAcad student, you may already have a career in IT, or you may be educating yourself to prepare for your career. In either case, it is good to know about the skills needed for the various jobs that are available in IT.
作为 NetAcad 学生，你可能已经从事 IT 职业，或者你可能正在为你的职业做教育准备。在任何情况下，了解 IT 中可用的各种工作所需的技能都是有益的。

Network engineers are more vital today than ever before, and their roles and required skills are constantly evolving. The Cisco Certified Network Associate (CCNA) certification demonstrates that you have knowledge of foundational technologies and ensures that you stay relevant with the skills needed for the adoption of next-generation technologies.
网络工程师今天比以往任何时候都更重要，他们的角色和所需技能不断发展。思科认证网络助理 (CCNA) 认证证明你具备基础技术的知识，并确保你保持与采用下一代技术所需的技能的相关性。

The requirements of the CCNA for networking engineers have been consolidated and updated to three courses and one exam covering the fundamental topics for all network technologies. This new CCNA focuses on IP foundation and security topics, along with wireless, virtualization, automation, and network programmability.
网络工程师的 CCNA 要求已整合并更新为三门课程和一门考试，涵盖所有网络技术的核心主题。新的 CCNA 专注于 IP 基础和安全主题，以及无线、虚拟化、自动化和网络可编程性。

Cisco offers new DevNet certifications at the associate, specialist, and professional levels to validate your software development skills.
思科提供新的 DevNet 认证，分为助理、专家和专业级别，以验证你的软件开发技能。

In addition, you can obtain specialist certifications (such as Cisco Enterprise Advanced Infrastructure Specialist certification) to validate your skills in line with your job role and interests.
此外，你可以获得专家认证（如思科企业高级基础设施专家认证）以验证你的技能与你的工作角色和兴趣保持一致。

You can start where you want. There are no prerequisites to start earning your associate-, specialist-, professional-, or expert-level certifications. Continuing education credits for recertification and ongoing development are now available for CCNA certification.
你可以从任何地方开始。开始获得助理级、专家级、专业级或专家级认证没有先决条件。CCNA 认证现在提供继续教育学分用于重新认证和持续发展。

### Networking Jobs (1.9.2)
网络工作 (1.9.2)

Your CCNA certification will prepare you for a variety of jobs in today's market. At www.netacad.com you can click the Careers menu and then select Employment opportunities. You can find employment opportunities where you live by using the Talent Bridge Matching Engine. Use this new program to search for jobs with Cisco and Cisco partners and distributors seeking Cisco Networking Academy students and alumni.
你的 CCNA 认证将为你在当今市场中的各种工作做好准备。在 www.netacad.com，你可以点击职业菜单，然后选择就业机会。你可以使用人才桥匹配引擎找到你所在地的就业机会。使用这个新程序搜索思科及其合作伙伴和分销商为思科网络学院学生和校友提供的职位。

You can also search for IT jobs using online search engines such as Indeed, Glassdoor, and Monster. Use search terms such as IT, *network administrator*, *network architect*, and *computer systems administrator*. You can also search using the term *Cisco CCNA*.
你也可以使用 Indeed、Glassdoor 和 Monster 等在线搜索引擎搜索 IT 工作。使用诸如 IT、*网络管理员*、*网络架构师* 和 *计算机系统管理员* 等搜索词。你也可以使用 *Cisco CCNA* 术语进行搜索。

![](img/e71dc48d3ae3db3394e5857ab2acae75_72_0.png)

### Lab—Research IT and Networking Job Opportunities (1.9.3)
实验——研究 IT 和网络工作机会 (1.9.3)

In this lab, you will complete the following objectives: Part 1: Research Job Opportunities; Part 2: Reflect on Research.
在本实验中，你将完成以下目标：第一部分：研究工作机会；第二部分：反思研究。
