# Third-Party Software Management

The use of third-party software adds additional risk. A third party may have limited access to your systems but will often have direct access to some portion of your data. If this is sensitive data, a careful review is necessary and should involve the vendor management office (VMO) if your organization has one. Specific language regarding security should be part of every vendor contract.

The typical issues that are addressed include the following:

+   - Where in the cloud is the software running? Is this on a well-known CSP, or does the provider use their own cloud service?
+   - Is the data encrypted at rest and in transit, and what encryption technology is used?
+   - How is access management handled?
+   - What event logging can you receive?
+   - What auditing options exist?

In addition to basic security questions, a review of the third-party SOC-2 report, recent vulnerability scans and penetration tests, and security and privacy policies will provide an assessment of the security maturity of the organization and whether you should entrust them with your sensitive data. While you may delegate some processes, you cannot delegate responsibility for your data.

Another risk that will occur with some third-party vendors is fourth-party risk. Fourth party refers to a third party’s third party, such as if your vendor uses a separate, independent vendor to provide you a service. For example, when a SaaS solution uses an independent CSP for some of their storage needs, your risks include the risks associated with the SaaS solution as well as any additional risks created by the CSP they use. In essence, your infrastructure (computing, storage, and so on) is hosted on the Internet, and any services used by these parties increase the perimeter of the risk that must be considered.

There are advantages to using third-party services. A third party may supply software to address in-house needs when there is no in-house expertise. Third-party solutions can also provide cost and tax advantages. However, these resources must be understood and managed just as much as in-house application solutions.

# Validated Open-Source Software

All software, including open-source software (OSS), must be validated in a business environment. Some argue that open-source software is more secure because the source code is available to review, and many eyes are upon it. However, large and complex solutions are not simple to review. So, validation through sandbox testing, vulnerability scans, and third-party verification is required.