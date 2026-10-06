
# 现场调查记录：Nortelem 公司 NT 系统安全评估

## 1. 初步问答评估

### 1.1 物理安全与服务记录
**该 NT 系统在过去四周内是否曾进行过服务？**
> [否。然而，设备外壳未保持上锁，钥匙在外壳上。housing 该设备的房间已上锁，但多位人员持有钥匙。此情况极不安全。首先，NT 网页服务器外壳应上锁，钥匙应由物理安全部门保管，同时房间钥匙也应由物理安全部门保管。若系统近期接受过服务，您需要查阅相关文档，并核实实际完成的工作与文档描述是否一致。有时维修人员会“植入”恶意硬件或软件。]

### 1.2 人员安全风险
**过去四周内是否有不满的员工被解雇？**
> [据我们所知没有。请注意回答的措辞。在大型组织中，员工可能在少数人知晓的情况下被解雇，他们可能认为该人员在休假或病假。请务必与 HR 确认此点。若有不满员工被解雇，则需获取其系统用户 ID 并仔细检查其用户 ID 下的日志活动。他们可能会以多种方式隐藏活动（取决于其专业水平），但这是一个良好的起点。]

**您是否知道当前有任何不满的员工？**
> [据我们所知没有。请在面谈时 discreet 地确认。仔细倾听受访者。您可能会发现线索。]

### 1.3 历史安全事件
**过去三个月内是否发生过其他安全事件？**
> [据我们所知没有。请保持审慎态度。您的客户可能一年前已被入侵但未觉察。若查阅某些存放此类信息的网站，您可能会为客户带来惊喜。两个主要站点供参考：`rootshell.com` 与 `ATTRITION.org`。还有众多其他站点，但这两个是最佳选择。]

### 1.4 物理访问控制
**实际拥有对该 NT4 盒子的物理访问权限的人员有哪些？**
> [一位秘书持有钥匙并将其发放给需要的人员。未维护钥匙日志。显然这里存在明显的安全漏洞，虽然这种情况很常见。任何未获正式授权的人员都不应获取锁定服务器机房的钥匙。]

### 1.5 网络架构与防火墙配置
**该系统位于防火墙内部还是外部？**
> [位于防火墙内部，防火墙规则仅允许特定 IP/PORT 访问。防火墙已打开 80 与 21 端口，以便通过 Internet 的人员能够访问 Web 服务器。端口 80 是 HTTP 流量的常规端口，端口 21 是 FTP 端口，用于文件传输。这也是部署 IDS 的另一理由。尽管防火墙可能允许恶意流量经由 21 与 80 端口，但 IDS 可能能够检测并终止此类流量，或根据配置执行其他操作。]

**该系统是仅供 Internet 使用，还是配备额外的网卡（NIC）连接到组织内部网（intranet）？**
> [两者皆有。系统配备一张用于 Internet 的 NIC 以及一个用于 intranet 的虚拟主机（两个 IP 地址）。*]
> **注意**：此配置相当不安全，使用它的人员将面临内部网络被威胁的风险。

### 1.6 系统用途与端口详情
**该系统的所有用途是什么？**
> [该 Web 服务器用于存放包含我们对各类产品和公司进行研究结果的 Oracle 数据库。法律要求我们使这些信息公开。]

**该系统使用哪些传输控制协议（TCP）/用户数据报协议（UDP）端口？其用途是什么？**
> [我们认为 TCP 80 与 21 为唯一开放端口。该系统还配置为 NT 远程管理。]

### 1.7 资产管理与配置核对
**我希望查看该系统的原始采购订单副本，显示其最初购买时的配置。我也希望获得任何硬件层面的服务或修改记录副本。**
> [我们已有原始采购订单、配置及修改记录，可供您查阅。但该系统维护较为松散，我们不确定其实际配置是否与文档描述一致。]

> **Note:** You can run a software program called `InsightManager` on NT to identify the current configuration. If the same program was run at an earlier date, you can compare the old report with the new one you just made.

### 1.8 应用变更记录
**Were any new applications recently (in the past four weeks) added to or removed from the system?**
> [Three system administrators stated that they did make some application file changes, but they did not document which files were changed.]

---

## 2. 调查方法论总结

> The above question and answer session occurred during my trip to the airport in the cab and while I waited to board the airplane at the airport.

> **Note:** If this had been an established client, I would have had the answers to most of the above questions at the time when the client initially contacted me. An established client has a checklist to use when a network security incident occurs. The client quickly works through the checklist, providing answers as well as possible, and e-mails me the results via a secure encrypted link. This is a big timesaver. Saving time at the beginning of an investigation makes it more likely that the resolution of the investigation will be successful. The first 24 hours of a new case are critical.

---

## 3. 行前准备：网络取证设备包 (CFEC)

I am now on the airplane, heading to Boston. My carry-on luggage is above my seat, stored safely away. This is an important point. **Never put your Cyber Forensics Equipment Container (CFEC) in the hands of the airline personnel.** Too much can go wrong. You have expensive (and sensitive) hardware and software and are responsible for it. If you arrive at the client site without your CFEC, you have a serious problem. Always keep your Cyber Forensics Equipment (CFE) in carry-on luggage that has wheels and a handle and is a size that fits in the compartment above your airplane seat.

The contents of a CFEC may vary to some degree, depending on your work, but the following is a good standard to follow:

### 3.1 核心硬件与存储介质
- Velcro fasteners to keep cables contained
- Hard drives that will work in the system(s) you will investigate
- Read/write CD-ROMs
- DAT tape drive (I recommend Ecrix VXA-1 External SCSI.)
- Jaz Drive with 2-MB disks
- Imation Super Disks for Macintosh computers
- 5.25-inch diskettes with labels
- Boot diskettes for various operating systems/version levels
- All power cords, device connectors, and adapters required
- Surge protector

### 3.2 取证分析笔记本电脑 (无线)
A wireless laptop loaded with vulnerability analysis, IDS, CF software, etc.:
- Mijenix Fit It Utilities CD-ROM
- Norton Utilities CD-ROM
- NTI (New Technologies, Inc.) CF tools
- EnCase
- Access Data System Management Toolkit
- L3 Network Security Expert
- ISS Real Secure, Internet Scanner, System Scanner
- NeoTrace
- Visual Route
- Microsoft Office
- Internet and e-mail access
- Antivirus software
- PERL
- Microsoft Visual C++ 6.0 or later
- Intel/Motorola Assembler
- Fortran
- Digital camera
- Bootable to Windows 95/98/2000, Linux, Solaris, Macintosh
- Network ICE (personal laptop firewall)
- Partition Magic and Boot Magic
- VMware
- MatLab
- Mathcad
- QuickTime
- Adobe Acrobat
- NetScan Tools Pro
- War dialer
- Analyst’s notebook
- Big Business Directory
- Dragon voice recognition
- NFR
- SafeBack
- Video camera (no active microphone)

### 3.3 文档、连接与外设
- Electronic copies of any documentation needed (paper is too bulky)
- Cables: all SCSI types, parallel, serial, telephone (RJ11), network (RJ45)
- Tape recorder: hand held, digital with IBM Via Voice and regular tape types
- Technical Surveillance Counter Measures (TSCM) equipment (The concern is that someone may have planted a transmitter.):
  - Radio frequency (RF)/microwave transmitter locator
  - White noise generator
- Duplicator (to make second copy of the bitstream backup)
- Four-port mini 10/100 network hub
- Mini projector for laptop
- Fluke Network Meter
- Null modem cable/Lap Link cable
- NetWare CD-ROM or diskettes
- Portable color printer that connects to your laptop (with extra ink cartridge)
- Color-coded stickers (circular)
- Cable labels
- Evidence labels and chain of custody forms
- Erasable and nonerasable markers
- Cameras (digital and film type)
- Kensington Sonic Lock Alarm
- Kensington laptop security cable

### 3.4 个人物品与应急装备
- Extra pens/pencils and a wire-bound notepad
- A pair of Motorola radios (walkie talkies)
- Computer repair tool kit (includes antistatic wrist line)
- Extra battery and hard drive (duplicate of your current drive) for your laptop
- Paper and electronic copies of all e-mail/telephone numbers you might need
- Cellular telephone
- TechCard (to obtain 24/7 support on nearly any product)
- Credit cards, driver’s license, badges, etc. required
- Passport
- Sequoia pocket books: Pocket Partner, Pocket PCRef, WinRef, TechRef

> This may seem like a large amount of equipment, but it all packs well into one carry-on piece of airplane luggage. Lest I forget, there are two more important details:
>
> 1. Be sure you have notified at least one person (preferably two or three) to let them know where you are going; provide them with emergency contact information.
> 2. Be sure to inform your computer crime attorney of your location, contact information, and general information pertaining to the case. Your attorney should expect to be contacted and therefore should readily respond to a ringing cell telephone or pager.

---

## 4. 现场到达与初步简报

I arrived at the client site, Nortelem, in Boston, Massachusetts, and was met at the gate by a security guard, who requested proper identification and then notified Bob Jacobs of my arrival. The security guard inspected my CFEC and required me to sign a statement stipulating my understanding of company policy pertaining to the equipment I am bringing in. Bob picked me up at the gate and we went to a conference room.

The first thing I always do when I arrive at a site is to hold a 15-minute briefing. (After reviewing the information Bob sent me, I contacted him and told him who I would like to have available as soon as I arrived on site.) The briefing covered the following topics:

- Was physical security able to secure the area where the security incident occurred?
- Have you learned anything new since we last communicated?
- Do you have available the personnel I requested?
  - Web server system administrators (at least two of them)
  - Firewall, switch, router experts
  - NT4 operating system expert
  - Applications expert for the compromised system
  - Legal, HR, and union (if necessary)

In summary, this is the procedure I followed.
