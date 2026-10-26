
## Third-Party Software Management

The use of third-party software adds additional risk. A third party may have limited access to your systems but will often have direct access to some portion of your data. If this is sensitive data, a careful review is necessary and should involve the vendor management office (VMO) if your organization has one. Specific language regarding security should be part of every vendor contract.

The typical issues that are addressed include the following:

- Where in the cloud is the software running? Is this on a well-known CSP, or does the provider use their own cloud service?
- Is the data encrypted at rest and in transit, and what encryption technology is used?
- How is access management handled?
- What event logging can you receive?
- What auditing options exist?

In addition to basic security questions, a review of the third-party SOC-2 report, recent vulnerability scans and penetration tests, and security and privacy policies will provide an assessment of the security maturity of the organization and whether you should entrust them with your sensitive data. While you may delegate some processes, you cannot delegate responsibility for your data.

Another risk that will occur with some third-party vendors is fourth-party risk. Fourth party refers to a third party’s third party, such as if your vendor uses a separate, independent vendor to provide you a service. For example, when a SaaS solution uses an independent CSP for some of their storage needs, your risks include the risks associated with the SaaS solution as well as any additional risks created by the CSP they use. In essence, your infrastructure (computing, storage, and so on) is hosted on the Internet, and any services used by these parties increase the perimeter of the risk that must be considered.

There are advantages to using third-party services. A third party may supply software to address in-house needs when there is no in-house expertise. Third-party solutions can also provide cost and tax advantages. However, these resources must be understood and managed just as much as in-house application solutions.

## Validated Open-Source Software

All software, including open-source software (OSS), must be validated in a business environment. Some argue that open-source software is more secure because the source code is available to review, and many eyes are upon it. However, large and complex solutions are not simple to review. So, validation through sandbox testing, vulnerability scans, and third-party verification is required.

A cloud native architecture can deploy in a DevOps, and a CI/CD process and can use microservices and containers.

Serverless environments use an event-driven architecture. Events trigger and communicate between decoupled services. Because they are serverless, these architectures scale well using a Representational State Transfer (REST) API or event triggers.

Cloud-based architectures are well suited to building and deploying web applications. Using an API Gateway, a secure API is a front door to web applications providing access to data and business logic.

Considering these cloud architectures, there are a number of tools and services that can support the security needs of both new software solutions as well as legacy devices. These services provide enhanced security and deal directly with common security issues. These services may be supplemental services that protect certain parts of the application architecture, encryption services that protect data at rest or in motion to ensure confidentiality of the data, methods to test securely, and services that tie all these services, web services, and application services together.

## Supplemental Security Components

Supplemental security components provide service to your cloud environment to solve specific security concerns. For example, database monitoring works to ensure the integrity of our databases, while XML firewalls support application services through XML messages. Each supplemental security service will describe the problem solved by this service.

### Web Application Firewall

A web application firewall (WAF) protects HTTP/HTTPS applications from common attacks. Usually, a WAF protects an Internet-facing application, but it can also be used internally on an intranet. The WAF can be a hardware device, a software device, or both. The WAF monitors GET and POST requests. The requests are then compared to configured rules. A WAF may look for specific signatures or apply heuristics.

By filtering HTTP/HTTPS traffic, a WAF helps protect against SQL injection, cross-site scripting (XSS) and cross-site forgery, and other attacks. The WAF specifically addresses attacks on application services and external sources.

The WAF differs from an Intrusion Detection System (IDS), which monitors specific traffic patterns on a network. A WAF works at the application level and focuses on specific web application traffic and is often employed as a proxy, with one or more websites or web applications protected behind the WAF. The CSPs and third-party vendors provide many WAF options.

### Database Activity Monitoring

Database activity monitoring (DAM) refers to a set of tools that supports the identification and reporting of fraudulent or suspicious behavior in the databases used by your application services. This real-time monitoring may use but is independent of native DBMS

## Application Programming Interface Gateway

An API gateway allows traffic to your application backend services. The services provided by an API gateway include rate limiting, access logging, and authorization enforcement. For secure computing, there should be limited doors into your application service. For example, some SaaS providers provide an API to access your account from your PC, Apple device, or Android device. These gateways control the way a user accesses and interacts with the SaaS solution and allow securing and monitoring this traffic. API gateways provide authentication and key validation services that control who may access the service, ensuring confidentiality of data.

Amazon Web Services (AWS) provides this service through Amazon API Gateway. AWS provides both RESTful for serverless computing and WebSocket APIs for real-time communication. Google Cloud provides an API gateway for REST APIs to provide serverless computing and a consistent and scalable interface. Azure API management provides a REST-based API for legacy systems. Essentially, all CSPs provide an API to allow the customer to monitor and control access to data and services to their workforce, partners, and customers in a way that provides a layer of protection and access control.

## Cryptography

Cryptography is a key technology for encrypting and protecting sensitive data in the cloud. Encryption is the first line of defense for data confidentiality. Encryption requires the use of keys. Management of the keys is a critical security vulnerability. There are three primary parts of encryption: data at rest, data in motion, and key management.

Encryption for data at rest is a standard practice for all sensitive information. Many CSP services have encryption as a standard option. Some CSPs provide standard APIs to allow encryption to be added to any CSP service or customer application. CSPs generally also provide encryption options for their storage and database services. Naturally, encryption tools are standard in all large CSPs.

Data-in-motion encryption is accomplished in standard ways to include TLS, HTTPS, and VPNs. The ability to work with standard secure data transmission methods is provided by all mature CSP. In addition, larger CSPs can accommodate data sharing between software solutions, even in multiple regions, without ever transiting the public Internet. However, this promise of not transiting the Internet does not necessarily mean that data is transiting a trusted network. Even when staying off the Internet, encrypted data transmission should be expected.

With all of this encryption, there are encryption keys to manage. The major CSPs all provide key management services (KMS) as do some third-party vendors. The first decision is who will manage the keys. Solutions exist to allow the vendor to manage the keys. However, for sensitive data, it is preferable that the customer use a commercial KMS rather than the vendor in order to improve key security. This provides a separation of duties between the service managing the encrypted data and the service managing encryption keys.
