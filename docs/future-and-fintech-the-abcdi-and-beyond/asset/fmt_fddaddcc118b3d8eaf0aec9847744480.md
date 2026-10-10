
*   **Cost-saving** — DevSecOps reduces overall reliance on cybersecurity teams to manually conduct post release code and infrastructure checks, resulting in the overall reduction of remediation cost.

## 13.3 DevSecOps Current Status

Since 2017, DevSecOps has become more and more popular and been started to be adopted by some early adopters. There are a number of reports to present and analyze the status of DevSecOps every year. One of popular DevSecOps reports is titled “DevSecOps Community Survey 2020” [[4](#chap13.xhtml#rref4)] is produced by the DevSecOps community organized by Sonatype, CloudBee. Twistlock, etc. In this report, it mainly compares the teams with DevOps Elite Practices and the teams without DevOps Practice on many different application security aspects.

Another DevSecOps report titled “DevSecOps Practices and Open Source Management in 2020” [[5](#chap13.xhtml#rref5)] is produced by Synopsys, who interviewed about 1,500 IT employees, and it includes 79% of developers and 21% of security engineers mainly from seven countries around the world — 65% of interviewees is from Asia (i.e., China, Japan, and Singapore); 18% is form Europe (the UK, Germany, and Finland); 17% is from the US.

In the report, based on the survey results, it shows that 33% of teams has already adopted DevSecOps practice well for their business delivery and another 30% of teams is on their way to partially or fully run DevSecOps. This is a good sign to demonstrate that many development teams are starting to be interested in DevSecOps and that the adoption of DevSecOps is rapidly growing.

Synopsys’s report also indicates that a successful DevSecOps solution entails a full security toolset, which includes static application security testing (`SAST`), dynamic application security testing (`DAST`), interactive application security testing (`IAST`), software composition analysis (`SCA`), runtime application self-protection (`RASP`), and penetration testing tools to fully address security issues at the early stages of the software development life cycle (`SDLC`).

`SAST`, `DAST`, and `IAST` are the top DevSecOps tools and have been well adopted by development teams. The `SCA` tool, also known as the free open-source security (`FOSS`) tool, analyzes the application by detecting the open-source software (such as third-party libraries, dependencies, licenses, etc.) It produces an inventory or Bill of Materials (`BOM`) to keep all open-source information in the codebase (such as versions and potential vulnerabilities). Comprehensive `SCA` solutions monitor the `BOM` to provide clients with early notifications of new vulnerabilities, and even deliver upgrades or patch guides. In addition, with the increasing of Cloud and Container technology adoption, the container security will become more and more important when teams start to move to the Cloud.

Regarding the response to the discovered critical open-source vulnerability, the survey found that more than half of the teams need to spend two to three weeks to apply for an open-source patch to fix the vulnerability, which means that the risk (that can be attacked by a hacker) will stay in the application for two to three weeks. Worse than that, a quarter of the teams ignore the risks in their applications up to a month, and only 16% of the teams fix the vulnerability within a week. In this regard, most of the development teams do not respond to the critical vulnerability fast enough, and therefore keep their applications at risk. The developer may not have the right mindset to be aware about vulnerabilities, may not have enough knowledge to fix the vulnerability, may not have the automation solution to speed up, or may have to go through complex and long processes to deal with the security issues. Any of these can result in slow response to the discovered critical vulnerabilities and leave their applications at potential risk to be attacked.

## 13.4 The Challenge to Implement DevSecOps

Although DevSecOps provides a novel methodology to solve the problems between DevOps and cybersecurity, and also make security everyone’s job during the development process, the journey to migrate from DevOps to DevSecOps is not easy and requires cultural or mindset change, new governance, workflows, and process to be established and new technology to be adopted. Here, the challenge to implement DevSecOps falls into two main areas, as follows.

### 13.4.1 Technical Challenges

Software development is a complex process, which may use different programming languages, large source code repositories, and a mess of open-source libraries and packages. DevSecOps needs to be able to support all of them. Unfortunately, so far, there are not many DevSecOps tools available on the market. In addition, many DevSecOps tools are not mature enough and still have weaknesses, which can slow down the promotion and wide adoption of DevSecOps tools. More details will be discussed in following section.

### 13.4.2 People/Culture Challenges

Compared to the technical challenges, the most challenge comes from people. Security is often an afterthought and has poor relation in the software development life cycle, so people normally do not have enough awareness about cybersecurity. In addition, many developers believe cybersecurity is the job of a dedicated cybersecurity department or team and that DevSecOps is additional work.

In 2018, Threat Stack [[6](#chap13.xhtml#rref6)] produced a survey to demonstrate that 52% of companies have cut security budget to meet a business deadline or objective. This report also examines that the main reason why DevSecOps has not become a reality in most organizations is due to the lack of support from senior management, who are keen on business delivery rather than cybersecurity. Without the buy-in from senior management to promote the DevSecOps from top to bottom, it will be difficult and slow for teams to widely adopt DevSecOps.

## 13.5 DevSecOps Best Practice

In order to overcome the aforementioned challenges to implement DevSecOps and finally establish the DevSecOps culture in the company, it is essential for DevSecOps’ best practices to be adopted by considering novel technology, new processes, and a mindset change.

### 13.5.1 Technology Innovation

Technology enables DevSecOps processes to be properly executed and makes sure that security flaws are detected at the early stages rather than the end of the software development lifecycle or even on the customer side.

#### Automate security — Automate security testing in the continuous delivery

In order to remove the bottleneck in the DevOps process caused by the cybersecurity assessment, automation is the essential solution. Automate security source-code scanning and binary scanning through the `CI/CD` pipeline by running static and dynamic security analysis, and therefore speed up secure code delivery. Integrating security tools at Integrated Drive Electronics (`IDE`) will further help developers detect and fix vulnerabilities at the coding stage, which is earlier than the Continuous Integration stage. In addition, pre/post-deployment auditing and scanning allows businesses to fully understand their risk postures.

#### Security Dashboard — Visualize technical security debt
