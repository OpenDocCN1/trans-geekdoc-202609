
-   [open ports] 和甚至是 [applications] 在这些端口上正在监听，这只是一个好的开始。你可以在对这些应用程序中可能存在的漏洞进行大量研究后，开始在 `open ports` 处盲目尝试和摸索。你也可以直接找到大量 `exploits` 并将其抛向在 `open ports` 上的应用程序。这可能是一种简单的方法，用来检查是否存在漏洞。你只需将你能找到的所有 `exploits` 与目标进行比对。这种做法有几个问题。第一个问题是，你可能会导致目标系统出现故障，而你并不想要这样。盲目测试可能会产生意外结果，而从伦理角度来说，你的目标之一是不造成伤害。

-   当然，任何类型的安全测试都可能导致意外结果和失败。然而，你的工作是尽可能地控制它，并确保你的客户或雇主了解你的测试可能带来的后果。你不应该向客户说明你只是随意向他们的系统抛出大量 `exploits`，而对其影响缺乏了解，导致他们可能出现宕机。你的工作是控制测试——要了解自己在做什么以及可能的结果。

-   另一个问题是，如果你正在进行红队测试，目标系统对你的攻击毫不知情，你需要确保他们不会检测到你，或者至少要尽一切努力避免被发现。盲目对大量系统（包括那些可能根本没有受影响的应用程序）进行大量 `exploits` 的做法会产生噪音，一旦有检测能力就会被发现，这意味着你失败了。

-   更好的做法是使用 `vulnerability scanner`，它采用智能的方式识别潜在漏洞。`vulnerability scanner` 会识别 `open ports` 和监听的 `applications`，然后根据这些 `applications` 判断可能的漏洞。随后，它会运行为这些漏洞预定义的测试。扫描器的目标不是 compromising 系统，而是仅仅识别潜在漏洞。

-   这并不保证扫描器识别出的就是可利用的漏洞。它意味着扫描器根据与目标系统的交互以及扫描器拥有的数据，认为某个点可能是漏洞。这被称为 `*false positive*`。任何扫描器发现的问题都需要手动验证。这可能包括检查扫描器呈现的实际交互——有时仅凭返回码而未查看实际数据，例如。也可能需要重新执行扫描器执行的测试。漏洞扫描器是工具，不应被视为测试的终点，而是起点。尽管扫描器功能强大，但它们并非最终。

-   从历史角度看，网络漏洞扫描器自 1990 年代初期就存在。第一个由 Dan Farmer 和 Wietse Venema 开发的工具是 Security Analysis Tool for Auditing Networks (SATAN)。SATAN 后来衍生出 Security Auditors Research Assistant (SARA) 和 Security Administrator's Integrated Network Tool (SAINT)。SATAN 主要使用 Perl 编写，并提供 Web 界面。虽然现代漏洞扫描器主要使用其他语言，但它们通常也使用 Web 界面。其中一个非常流行的扫描器是 Nessus。我们稍后会看 Nessus，但先从与 Nessus 相关的 OpenVAS 开始。

### OpenVAS

-   SATAN 是开源的，意味着你可以查看 SATAN 的所有实现，并且如果你愿意，可以自行添加模块来扩展其功能。即使你找到 SATAN 的副本，也能查看其源代码。

-   2000 年代初期，另一个开源漏洞扫描器是 Nessus。它最初于 1998 年以免费漏洞扫描器的形式发布，并在 2005 年（公司在三年前成立）关闭源代码，使后续开发全部专有。当时，已有的 Nessus 源码是第 2 版，Tenable 的第一个版本是第 3 版。第 2 版的源码是开放的，于是两个独立项目相继创建，其中一个是将 Nessus 第 2 版源码（由 Nessus 开发者放弃）fork 为新项目的基础。

-   其中一个 fork 产生了 Open Vulnerability Assessment System (OpenVAS)。最初，OpenVAS 与 Nessus 完全相同，正如你所期待的。随着时间的推移，OpenVAS 发展出自己的应用架构，采用了 Nessus 未明确使用的多层结构。Nessus 最初拥有本地客户端用于管理扫描，而 OpenVAS 继续使用相同的本地客户端。OpenVAS 通过 Greenbone Security Assistant (GSA) 作为用户界面。今天，GSA 通过 Web 界面访问。你可以在 [Figure 5.7](#c05.xhtml#c05-fig-0007) 中看到 GSA 的登录界面。

![FIGURE 5.7 Greenbone Security Assistant](images/c05f007.png)

[**FIGURE 5.7**](#c05.xhtml#R_c05-fig-0007) Greenbone Security Assistant

-   OpenVAS 允许你拥有多个用户，每个用户可能拥有不同的权限。有些用户可以创建扫描，而有些用户只能查看扫描结果。还有用户可以创建用户并管理 OpenVAS 安装。除了用户，OpenVAS 支持角色。角色内的权限可以修改，甚至可以新建角色。安装 OpenVAS 时，管理员用户会在设置过程中自动创建，并生成一个随机密码。

#### 在 OpenVAS 中设置目标

-   在 OpenVAS 中，一次扫描包含许多组件。创建扫描时，需要指定目标或目标集合。创建目标也需要一些信息。你需要提供想要测试的 IP 地址集合。你也可以排除某些地址。为了说明，你可能会在目标列表中提供一个网络段，但该段内可能包含脆弱系统，因此你可能希望告诉 OpenVAS 不对该地址进行测试。[Figure 5.8](#c05.xhtml#c05-fig-0008) 展示了在 OpenVAS 中创建目标的对话框，里面显示了 IP 地址以及排除项。

![FIGURE 5.8 Creating a target in OpenVAS](images/c05f008.png)

[**FIGURE 5.8**](#c05.xhtml#R_c05-fig-0008) Creating a target in OpenVAS

-   你还可以定义要扫描的端口范围。漏洞扫描器如 OpenVAS 会扫描端口以确定应集中测试的端口。你可以指定要测试的端口范围，这有助于限制测试范围，特别是当你只关注特定服务时。这是控制 OpenVAS 作业范围的一种方式。

-   你不总是进行黑盒测试，即不总是没有任何目标信息。有时你会拥有目标的详细信息，这些信息能帮助你更深入地了解目标组织面临的漏洞。例如，你可能会被提供凭据，这些凭据可以让 OpenVAS 通过本地凭据登录系统，从而查找本地漏洞而非仅限网络或远程漏洞。凭据在 OpenVAS 中使用后，会用于登录系统。一旦认证成功，扫描器即可开始查找本地漏洞。

