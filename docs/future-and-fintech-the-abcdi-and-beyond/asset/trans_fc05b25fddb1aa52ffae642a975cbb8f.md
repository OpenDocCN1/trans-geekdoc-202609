
In the previous sections, we discussed the importance of DevSecOps for fintech companies and detailed DevSecOps, including its current state, challenges, best practices, tools, etc. After understanding DevSecOps, you may be more interested in how to implement DevSecOps in a fintech company and what it takes to achieve this goal. In this section, we will take a large global bank (referred to as Bank B) as an example, using its DevSecOps transformation program as a case study to demonstrate how to implement DevSecOps and ultimately win the benefits of DevSecOps for development teams, while establishing a DevSecOps culture and mindset.

### 13.7.1 Background

Bank B has been running an enterprise-level DevOps program for two years since 2016. It invested heavily in toolchains to automate processes and in agile training to change people's mindsets. "Double the release frequency, halve the business incidents" was used to measure the outcomes of application teams adopting DevOps. After 2 years of the DevOps program, the overall DevOps maturity of development teams improved to the expected level. Although some legacy applications remain difficult to adopt DevOps, most application teams improved during the DevOps transformation, accelerating delivery speed, developing higher-quality products, and saving costs, which greatly benefits their competitiveness in the financial market.

With business delivery speed and product quality improved due to DevOps adoption, cybersecurity became the next hot topic for Bank B to maintain its technology leadership and further support its business, as a top-level requirement of the bank. With this in mind, the DevSecOps program was proposed and launched at the end of 2018.

### 13.7.2 DevSecOps Implementation Model and Operating Model

Before running the DevSecOps program, the first step is to clarify what needs to be done and how to do it. To achieve this, the DevSecOps Implementation Model and the DevSecOps Operating Model were formulated.

The DevSecOps Implementation Model (see [Figure 13.8](#chap13.xhtml#fig13-8)) identifies what needs to be done to achieve the ultimate goal of the DevSecOps program: establishing a DevSecOps culture and mindset.

*   The first step is to gain the capability to discover vulnerabilities from applications by adopting DevSecOps tools. These tools need to be integrated into the `CI/CD` pipeline to automate the process and visualize vulnerability scan results on dashboards or notify users for reporting.
*   The second step is to provide training for developers so they possess sufficient skills to remediate vulnerabilities.
*   After introducing DevSecOps tools and providing training to development teams, the ultimate goal of the DevSecOps program is for everyone to have a DevSecOps mindset and to establish a DevSecOps culture within teams. Additionally, each development team is expected to have at least one "Security Champion" who possesses advanced application security skills to help the team remediate tricky vulnerabilities and train other team members.

![](images/p443.jpg)

**Figure 13.8.** DevSecOps implementation model

After understanding what needs to be done and the goals of the DevSecOps program, the DevSecOps Operating Model (see [Figure 13.9](#chap13.xhtml#fig13-9)) provides the solution for executing the DevSecOps implementation. It defines the responsibilities of different roles as follows:

**DevSecOps Champion:**

*   Leads the DevSecOps program, responsible for promoting DevSecOps culture and helping development teams establish a DevSecOps mindset.
*   Connects development teams and cybersecurity teams.
*   Collects feedback from development teams and reports to the cybersecurity team or experts so they can provide technical/training solutions.

![](images/p444.jpg)

**Figure 13.9.** DevSecOps operating model

**Development Teams:**

*   Integrate DevSecOps tools into the `CI/CD` pipeline to automate the process and visualize security scan results on dashboards.
*   Receive DevSecOps training to gain sufficient application security knowledge and possess sufficient skills to remediate vulnerabilities.
*   Use DevSecOps tools and knowledge in actual projects and daily work, gradually changing mindsets and establishing a DevSecOps culture within the team.

**Cybersecurity Team:**

*   Provide DevSecOps tool support.
*   Provide application security training support.
*   Provide consulting services on demand.

### 13.7.3 Integrating DevSecOps Tools into the CI/CD Pipeline

After evaluation, the security department decided to procure several commercial products as the DevSecOps tool solution, such as `Checkmarx` (SAST tool), `Sonatype IQ Server` (SCA tool), and `Contrast Security` (IAST). After successfully setting up the tools for pilot teams, the next step was to integrate the tools into the `CI/CD` pipeline to automate their security scan execution. Scan results and discovered vulnerabilities need to be displayed on dashboards. If necessary, security rules within the `DevSecOps` tools can be customized according to the team's situation and needs.

To integrate `DevSecOps` tools into the `CI/CD` pipeline, the first step is to install relevant plugins on the `CI` server to connect the `DevSecOps` tool server and the `CI` server. Taking `Checkmarx` and `Jenkins` as an example. From the `Jenkins` dashboard (see [Figure 13.10](#chap13.xhtml#fig13-10)), click "Manage Jenkins" and go to the "Manage Plugins" section. After the "Plugin Manager" screen appears, select the "Available" tab and check the "Checkmarx Plugin" box. Click "Install without restart" or "Download now and install after restart", and `Jenkins` will automatically install the plugin. After successfully installing the `Checkmarx` plugin on the `Jenkins` server, you need to complete the `Checkmarx` configuration in the `Jenkins` "Configure System".

![](images/p446.jpg)

**Figure 13.10.** Manage Jenkins Dashboard

![](images/p446-1.jpg)

**Figure 13.11.** Checkmarx scan configuration

After completing all installation and configuration work, the next step is to create and configure a `Jenkins` job. There are two ways to configure a job in `Jenkins` to automatically execute `Checkmarx` vulnerability scans (see [Figure 13.11](#chap13.xhtml#fig13-11)). One solution is the traditional configuration method of creating a job by filling out a form. From the "Jenkins Dashboard", select a "job" and click Configure. After the job configuration appears, scroll down to the "Build" section, click "Add build step" and select "Execute Checkmarx Scan". After Execute Check Scan appears, fill in the form below by entering required information such as the `Checkmarx` server URL, credentials, source code project/location, and other parameters.

After successfully running the `Checkmarx` scan, results will be displayed simultaneously on the `Checkmarx` dashboard and the `Jenkins` dashboard, with vulnerabilities categorized into different levels such as High, Medium, and Low.

### 13.7.4 DevSecOps Training

The primary purpose of adopting `DevSecOps` tools is to help teams discover vulnerabilities from applications. However, tools cannot help teams fix security issues; development teams should possess sufficient capability to remediate vulnerabilities on their own. To achieve this, relevant training is crucial as part of the `DevSecOps` program.

Some tools have incorporated learning tutorials as part of their features to guide users on how to fix vulnerabilities when discovered. Such learning materials provide a practical and simple way to educate developers. However, they may not cover a sufficient number of vulnerabilities for users to understand.
