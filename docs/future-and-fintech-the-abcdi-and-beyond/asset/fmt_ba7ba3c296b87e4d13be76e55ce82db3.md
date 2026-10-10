
# Case Studies: DevOps Implementation in Financial Institutions

*   **LMAX**, a global FinTech company, started with pair programming, TDD, and Continuous Integration, and later focused and invested heavily in automation testing and best practices. LMAX also introduced quality gates in the pipeline by considering unit test coverage, cybersecurity testing, and code quality analysis to guarantee the delivery of good-quality software.

*   **SIX** is one of the best examples of successfully running DevOps transformation on both technology and organizational change by adopting microservices, CI/CD, containers, and cybersecurity. For example, SIX's ATM network relies on the container management of microservices and automated tests.

*   **ING** is another example of how banks move to an automated CI/CD pipeline, including code analysis, unit test, static security testing, compliance, and functional and performance testing.

*   **BBVA** addressed its challenges first — inconsistent manual processes, poor automation testing, and siloed delivery teams. Based on current status analysis, BBVA adopted DevOps to improve time-to-market and application reliability by building an automated delivery pipeline with automated approval criteria and behavior enforcement, virtualizing metrics, and establishing a DevOps culture.

*   **JP Morgan** provides senior management with regular updates on key metrics related to delivery speed (release frequency) and production stability (business incident number) to gain leadership buy-in and support. They also maintain regular communication with development teams on business change requirements and help business stakeholders as part of the DevOps process. Based on better communications between business and IT teams, this business engagement model provides a more efficient way and saves costs on remediation due to misunderstandings of business requirements.

*   **Fidelity Investment** is also an early adopter of the Cloud and aims to modernize applications and minimize technical debt. In addition, Fidelity had an experience moving their CI back from the development environment to the developer's local machine, allowing developers to own their workload and engage in a culture of knowledge-sharing. The outcome showed that deployment time was reduced from minutes to seconds, which is beneficial for a team to deploy daily.

## 12.10 Case Study: DevOps Implementation in a Large Bank

### 12.10.1 Background

Recently, IT applications have become increasingly important to business in the financial industry. If applications in a bank can be delivered faster than its competitors, it will have an advantage and may affect business deals and market share. In the example of Bank A, there are thousands of IT employees available to support its global business. To support business in a very efficient development way, both Agile and DevOps were adopted, and a DevOps program ran from 2016 to 2018 on different aspects, as follows:

*   DevOps tooling chain
*   DevOps dashboard
*   Agile training and business engagement
*   DevOps community
*   Microservice and Cloud migration
*   Team organization change

### 12.10.2 DevOps Tooling Chain

Regarding the tooling aspect, Bank A adopted DevOps tools at different stages of the SDLC and integrated them to become a DevOps tooling chain to automate the process. Most applications in Bank A are coded in `Java`, and the DevOps tooling stack is provided in [Figure 12.8](#chap12.xhtml#fig12-8). To provide a global and advanced service, Enterprise tools were considered. However, with an increasing number of teams becoming users of the DevOps tooling chain, providing a robust and fast-response service was a big challenge. The tools used at the different stages of the SDLC in Bank A are given as follows:

![](images/p417.jpg)

**Figure 12.8.** The DevOps tooling chain for Java applications

*   Task management: `Jira`
*   Source code management: `Github (Enterprise)`
*   Continuous Integration: `Jenkins (Enterprise)`
*   Build: `Maven`
*   Code analysis: `Sonarqube (Enterprise)`
*   Unit test: `JUnit`
*   Artifact management: `Nexus (Enterprise)`
*   Automation testing: `Selenium` and `Jmeter`
*   Automation deployment: `Ansible Tower (Enterprise)`
*   Monitoring: `Prometheus`

### 12.10.3 DevOps Dashboard

When development teams started to use DevOps tools, it was easy to collect data from the different tools, then centralize, analyze, and finally display the DevOps metrics on the dashboard.

To influence the development teams' mindset and establish DevOps culture, TV monitors were purchased and allocated next to the development teams to display the DevOps dashboard in real time from many different aspects, such as code quality, build status, testing results and status, deployment status, production monitoring, etc. The purpose was to help development teams be more aware of the DevOps process by displaying relevant data. In addition, the DevOps dashboard also provided a vision or report for managers/leaders to easily understand what happened during the development process, evaluate team performance, and measure the teams' output.

### 12.10.4 Microservice and Cloud Migration

Although Bank A had adopted Agile training to improve team collaboration and a DevOps tooling chain to automate the process, there are many legacy applications with huge and complex architecture designs that blocked faster delivery. To solve this problem, Bank A defined two standards for both new and legacy applications. Regarding new applications/projects, the architecture was designed in a microservice way associated with a CI/CD automation pipeline to quickly deliver applications from the beginning. Unlike new applications, the architecture of legacy applications had already been designed in a complex way, so it took time to gradually rebuild them in the microservice way, piece by piece. Although microservices provide many benefits, the rebuild cost still needs to be considered to decide whether to rebuild the legacy application architecture in the microservice way or retire the legacy application.

As mentioned in the previous section, Cloud and container technology increase infrastructure utilization and improve development process efficiency. Bank A also decided to migrate to the Cloud, especially the internal/private Cloud due to cybersecurity concerns. Tools available in the Cloud are considered to collaborate with the DevOps tooling chain to provide better DevOps services. After a few months, several pilot teams successfully moved their applications and development processes to the Cloud environment. However, Cloud migration was still very slow in the banking environment due to restrictions on regulation and cybersecurity.

### 12.10.5 Agile Training and Business Engagement

In Bank A, proper Agile training was provided to the development teams. The Agile coach/lead accompanied the development teams to train them in `Scrum` and `Kanban`, enabling them to benefit from better communications, more efficient task management, and smaller, more frequent deliveries.

As the development teams in Bank A are responsible for delivering business requirements, most of the workload comes from the business. When DevOps was promoted across teams in Bank A, many managers found that although they were very keen on DevOps, their teams were too busy with business delivery and did not have time for IT improvement (DevOps). Furthermore, DevOps-related work was always considered a "low priority" task, and the teams might never have a chance to implement it. On this basis, you can find that DevOps is not only about IT but is also related to the business, which is the key for further DevOps implementation.
