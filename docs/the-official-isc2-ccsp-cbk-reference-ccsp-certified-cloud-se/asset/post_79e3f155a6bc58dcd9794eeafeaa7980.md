
and operates within the architecture security strategy of the organization. The goal of this testing is to determine if the software is secure. Again, this is a confidence level as to the security of the software system developed prior to deployment.

## Functional Testing

Functional testing is used to test that the functional specifications of the system, linked to system requirements, are met. The execution of a robust set of test cases, linked to functional requirements, will create a level of confidence that the software operates as intended.

There are many ways to test software. However, there are some common tests that are consistently used leading up to functional testing. The primary categories of testing that lead up to functional testing are unit testing, integration testing, and usability testing.

- **Unit testing:** This is testing by a developer on modules being developed as part of a larger system. All paths through the module need to be tested.
- **Integration testing:** As modules are combined, integration testing ensures that the modules work together. As additional modules are added, we get ever closer to functional testing.
- **Usability testing:** This testing uses customers in a production-like environment to get feedback on the interaction between the user and the system.

As the modules are tested and then are integrated (and tested) and the user’s feedback is obtained and incorporated into the system, we get to the point where we are ready to perform functional testing on the entire system. When conducting functional testing, there are important considerations that include the following:

- **Testing must be realistic:** Many development shops have Dev, Test, Stage, and Prod environments. These environments are called *lanes* in some organizations. The Dev or development environment can be set up to suit the developers’ needs. However, for the greatest assurance, the Test and Stage environments should be set up as closely as possible to the Prod environment. In many cases, the Test and Stage environments will have live data or older copies of live data to ensure functional requirements are met. Once development is complete, the application moves to the Test environment for testing. Upon successful testing, the application will move to the Stage environment for configuration management and potentially additional testing. Once the next release cycle occurs, the software in the Stage environment moves into production. Any environment with live data (current or older) must be protected as well as the Prod environment to prevent data loss.
- **Acceptance:** Testing must be sufficient to guarantee that the application service meets the requirements of the customer and the organization (sometimes they are the same). This means that testing must be designed to exercise all requirements.

to deployment once a testable amount of code is available and can be run throughout the remaining steps in the SSDLC.

- **Dynamic Application Security Testing (DAST):** This tool is used primarily as a web application vulnerability scanner. It is a form of black-box testing. DAST is known for having poor risk coverage, unclear reporting, and slow performance. So, it should not be the only testing tool used. When used, it should be used as early in the development process as practical. Once an application is deployed, a DAST is not your best choice.
- **Interactive Application Security Testing (IAST):** IAST is newer than SAST and DAST and provides a gray-box testing approach. IAST provides an agent within an application and performs real-time analysis of real-time traffic application performance, detecting potential security issues. It can also be used to analyze code as well as runtime behavior, HTTP/HTTPS traffic, frameworks, components, and back-end connections. IAST can be used at every phase of the SSDLC.

Another tool often discussed with SAST, DAST, and IAST is Runtime Application Self-Protection (RASP). RASP is less a test and more of a security tool. RASP runs on a server and works whenever the application is running. RASP intercepts all calls to and from the application and validates all data requests. The application can be wrapped in RASP and provides additional system security. In a layered defense, this is an additional layer and should not replace secure development and testing.

Security testing provides assurance that the software has been developed securely. While SAST and DAST may have their place, if you could use only one security testing tool, IAST would be the best choice. However, new methodologies are always being developed, and care should be taken to consider and use new tools as they become stable and available to improve your security assurance testing.

## USE VERIFIED SECURE SOFTWARE

The only type of software that a security conscious organization should use is software that has been verified as secure. Verification generally comes from a third party that will perform testing on software and validate that it has no discernable vulnerabilities. When there are no verified secure options, a customer must do their own due diligence to ensure security. In this section, we will discuss some major components of secure software.

### Approved Application Programming Interfaces

API development and deployment in custom applications requires the same SSDLC as other software development projects. The requirements can specify the methods used in the API to monitor access. API access monitoring is often done through authentication or keys.

If not securely developed, a custom API can be vulnerable, leading to the compromise of the system it fronts. Deployment should focus on API configuration and automate the monitoring of that configuration.

APIs can control access to software or application services in a SaaS solution, to back-end services in a PaaS solution, or even to computing, storage, and other infrastructure components in an IaaS solution. For each of these, an approved API is important to ensure security to the system components with which we are interacting. In addition, when possible, enforcing the use of APIs to create a minimum number of methods for accessing an application service simplifies monitoring and protection of these application services.

A CSP or other vendor will provide an API or services that allow the use of an API. It is important to use the APIs as defined and to configure them carefully. An organization can develop approved configurations for APIs used commonly within that customer's organization, and policy can enforce the use of those standard configurations.

In addition, vulnerability scanning of APIs can test the adherence to standards and can provide assurance that known vulnerabilities do not exist. It is impossible of course to ensure that unknown vulnerabilities such as zero-day vulnerabilities do not exist.

## Supply-Chain Management

There are two parts to supply chain management. First, it can refer to the needs of a CSP and potentially the customer to use third parties to provide services. For example, the CSP may rely on other vendors to provide services used by their customers. Management of this supply chain is a form of vendor risk management. When creating relationships with these vendors, both operational and security concerns should be addressed.

Additionally, traditional supply chain management is moving increasingly to the cloud. As the life of many organizations is tightly coupled with their supply chain management, the risks of cloud computing are important to consider. However, as the supply chain becomes increasingly global and sourcing of goods requiring primary and secondary sources, cloud computing increases the reach and benefit of supply chain management. Cloud computing can optimize infrastructure to provide operational and financial benefits.

In recent years, supply chain risk has become an increasingly common theme. An earthquake in one country will affect the availability of a resource in another. Large-scale cyberattacks like the SolarWinds hack can impact critical infrastructure. A global pandemic leads to shortages worldwide. Even a simple problem, like a ship blocking the Suez Canal, can interrupt the global supply in unexpected ways.

So, supply-chain management has a complex set of risks that include cloud computing. Cloud computing cannot overcome the risks of a pandemic or a ship running aground in the Suez Canal. But, securing the supply-chain management software in the cloud and securely connecting vendors globally through cloud services reduces the IT-related risk.
