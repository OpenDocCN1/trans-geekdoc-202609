to deployment once a testable amount of code is available and can be run throughout the remaining steps in the SSDLC.

+   - **Dynamic Application Security Testing (DAST):** This tool is used primarily as a web application vulnerability scanner. It is a form of black-box testing. DAST is known for having poor risk coverage, unclear reporting, and slow performance. So, it should not be the only testing tool used. When used, it should be used as early in the development process as practical. Once an application is deployed, a DAST is not your best choice.
+   - **Interactive Application Security Testing (IAST):** IAST is newer than SAST and DAST and provides a gray-box testing approach. IAST provides an agent within an application and performs real-time analysis of real-time traffic application performance, detecting potential security issues. It can also be used to analyze code as well as runtime behavior, HTTP/HTTPS traffic, frameworks, components, and back-end connections. IAST can be used at every phase of the SSDLC.

Another tool often discussed with SAST, DAST, and IAST is Runtime Application Self-Protection (RASP). RASP is less a test and more of a security tool. RASP runs on a server and works whenever the application is running. RASP intercepts all calls to and from the application and validates all data requests. The application can be wrapped in RASP and provides additional system security. In a layered defense, this is an additional layer and should not replace secure development and testing.

Security testing provides assurance that the software has been developed securely. While SAST and DAST may have their place, if you could use only one security testing tool, IAST would be the best choice. However, new methodologies are always being developed, and care should be taken to consider and use new tools as they become stable and available to improve your security assurance testing.

# ## USE VERIFIED SECURE SOFTWARE

The only type of software that a security conscious organization should use is software that has been verified as secure. Verification generally comes from a third party that will perform testing on software and validate that it has no discernable vulnerabilities. When there are no verified secure options, a customer must do their own due diligence to ensure security. In this section, we will discuss some major components of secure software.

# ### Approved Application Programming Interfaces

API development and deployment in custom applications requires the same SSDLC as other software development projects. The requirements can specify the methods used in the API to monitor access. API access monitoring is often done through authentication or keys.