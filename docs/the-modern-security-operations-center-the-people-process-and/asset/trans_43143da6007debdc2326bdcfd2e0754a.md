

在本书的这个阶段，你应该已牢固掌握规划、建设、资助和维护成熟 SOC 环境的关键概念。剩下的唯一主题是你应该对你的 SOC 以及其他 SOC 的未来抱有何种期待。[第 11 章](#ch11.xhtml#ch11)将展望 SOC 的未来，为本书画上句号。

### 参考文献

Ansible Project. (2019). Installing Ansible. In *Ansible Installation Guide*. Red Hat, Inc. [https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html](https://docs://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

Amazon Web Services (AWS). (n.d.). What Is DevOps? AWS. [https://aws.amazon.com/devops/what-is-devops/](https://aws.amazon.com/devops/what-is-devops/)

Creately. (2020, December 1). Ultimate Flowchart Tutorial (Complete Flowchart Guide with Examples). Creatley Blog. [https://creately.com/blog/diagrams/flowchart-guide-flowchart-tutorial/](https://creately.com/blog/diagrams/flowchart-guide-flowchart-tutorial/)

Incident Response Consortium (IRC). Playbook – Virus Outbreak. IRC. [https://www.incidentresponse.com/playbooks/virus-outbreak](https://www.incidentresponse.com/playbooks/virus-outbreak)

ISACA. (n.d.). COBIT 2019 Framework (various publications). ISACA. [https://www.isaca.org/resources/cobit](https://www.isaca.org/resources/cobit)

Oren Ben-Kiki, O., Evans, C., & döt Net, I. (2009, October1). YAML Ain’t Markup Language (YAML) Version 1.2. YAML.org. [https://yaml.org/spec/1.2/spec.html](https://yaml.org/spec/1.2/spec.html)

Vertis. (n.d.). DevOps Automation Tools: Configuration Tools for Continuous Deployment. Vertis. [https://www.veritis.com/solutions/devops/made-easier-with-devops-tools/#:~:text=DevOps%20tools%20facilitate%20ways%20for,for%20an%20effective%20product%20output](https://www.veritis.com/solutions/devops/made-easier-with-devops-tools/#:~:text=DevOps%20tools%20facilitate%20ways%20for,for%20an%20effective%20product%20output)

W3Schools. (n.d.). Introduction to XML. Refsnes Data. [https://www.w3schools.com/xml/xml_whatis.asp](https://www.w3schools.com/xml/xml_whatis.asp)

W3Schools. (n.d.). JSON – Introduction. Refsnes Data. [https://www.w3schools.com/js/js_json_intro.asp](https://www.w3schools.com/js/js_json_intro.asp)

Yuan, S. (2019, May 22). The Anatomy of NetDevOps. Cisco Blogs. [https://blogs.cisco.com/developer/anatomy-of-netdevops](https://blogs.cisco.com/developer/anatomy-of-netdevops)

Eric Ahlm, Augusto Barros, Michael Clark. SOAR: Assessing Readiness Through Use-Case Analysis. [https://www.gartner.com/en/documents/3981938/soar-assessing-readiness-through-use-case-analysis](https://www.gartner.com/en/documents/3981938/soar-assessing-readiness-through-use-case-analysis)

## 第 11 章：SOC 的未来

> *预测未来的最好方式是创造未来。*
>
> ——亚伯拉罕·林肯

欢迎来到这趟深入 SOC 之旅的最后一章。本书涵盖的主题范围广泛，从如何建设 SOC 到成熟 SOC 通行的实践类型。你已探索了当今成熟 SOC 中行之有效的做法，但这留下了一个最后的开放性话题，即你应该期待在未来的 SOC 中看到什么。技术正在飞速变化，网络犯罪分子使用的战术也是如此。应对这些变化需要调整你的 SOC 实践，否则最终你将遭遇妥协（安全失陷）。安全是一场旅程，而非终点。你不会一劳永逸地变得安全然后转战另一个项目。相反，你会像 OODA 循环（详见[第 10 章](#ch10.xhtml#ch10)“[数据编排](#ch10.xhtml#ch10)”）所述那样，持续观察和调整。

本最后一章概述了安全行业趋势，以及我认为未来 SOC 成功的关键要素。这些主题基于行业分析师对安全行业的预测、对技术如何改进的预期，以及我从行业会议、客户会面和分析师对未来算力预期中所获取的行业动态。请思考这些概念，在规划下一个 SOC 项目时，推动你自己和 SOC 保持前瞻性思维。随着你成熟 SOC 服务，保持前瞻性思维至关重要。

### 所有目光聚焦 SD-WAN 和 SASE

第一个概念是自 2020 年初以来每个组织的 C 级高管都在谈论的，即如何应对对新型网络架构方法的需求，该方法被 Gartner 称为*安全访问服务边缘*，即 SASE（读作“sassy”）。SASE 代表将 WAN 和安全技术融合为单一的云交付服务。疯狂的是，在 Gartner 于 2019 年首次定义 SASE 时，没有任何单一供应商提供 SASE，但自 2019 年底以来，几乎每个安全供应商都声称能够提供 SASE。现实是，许多供应商仅提供 SASE 承诺功能的一部分，导致不准确的营销宣传泛滥，且没有具体参考 Gartner 关于供应商和服务提供商应如何提供 SASE 的解释。这自 Gartner 推出 SASE 以来造成了大量困惑，这也是为什么它是本章需要首先清晰阐述的面向未来的主题，因为它将影响你当下和未来的 SOC。

如果你想保持前瞻性，你需要制定 SASE 战略。接下来，我将解释为什么这样做对你的 SOC 未来至关重要。

#### VoIP 采用作为 SD-WAN 采用的序章

要理解 SASE，让我们先退一步，回顾一个技术趋势，它对 IT 行业产生了类似的变革性影响，但侧重于组织如何运行其电话系统。在 IP 语音 (VoIP) 出现之前，组织由电话公司提供电话服务，由 ISP 提供互联网服务。电话系统技术非常基础，仅提供拨号音和有限的通话功能。20 世纪 90 年代某个时候，VoIP 开始作为一种将电话服务和互联网服务合并为单一套餐的方式被引入，为组织节省了大量资金。除了节省成本，组织还能使用前沿的 VoIP 电话，其中包括具有简化用户界面的集中管理系统和其他很酷的功能，极大地提高了最终用户满意度。

VoIP 的所有优势导致组织对语音通信需求的看法发生重大转变。到 2000 年，VoIP 已被视为组织中的常见技术。从零售店到大型企业，都拥有基于计算机的电话系统。VoIP 是一种颠覆行业的技术，导致许多擅长部署和管理模拟电话系统的工程师不得不转向数字电话系统，否则将面临失业。如今，很少见到企业还在使用模拟电话系统。

##### VoIP 优势总结

VoIP 改变 IT 市场格局的一些原因可总结如下：

*   合并互联网账单和电话账单，从而节省成本
*   提供前沿技术：
    *   新型 IP 电话
    *   集中管理
    *   个性化铃声和保持音乐等前沿功能
    *   更好的性能监控以了解投资回报率
    *   更多安全选项
*   成为人人争相投资的趋势
*   被视为提供竞争优势

#### SD-WAN 简介

