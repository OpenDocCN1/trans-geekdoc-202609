
The SAP HANA cockpit can also be utilized to enable or disable backup encryption. From the System Overview page, click the Data Encryption tile to manage your SSFS keys and enable or disable encryption. The same tile also includes a section where you can quickly enable or disable backup encryption by using the On/Off slider. You can also access this same option by clicking the Data Encryption link. Locate the Backup Encryption section to view its current status, as shown in [Figure 13.18](#13_003.html#f13.18). Again, use the On/Off slider to disable or enable backup encryption.

[![Interface for Enabling or Disabling Backup Encryption in the SAP HANA Cockpit](bilderklein/klein13_018.png)](img-f13.18.html)

**Figure 13.18** Interface for Enabling or Disabling Backup Encryption in the SAP HANA Cockpit

## 13.4 Summary

To properly protect an SAP HANA system, encryption for communication data and for data at rest encryption must both be enabled. Without encryption, someone could gain unauthorized access to your SAP HANA system or the data it hosts. SAP HANA offers options to protect communications using X.509 certificates and provides a root key system to protect backups, data, and log volumes.

# 14 Security Lifecycle Management

Implementing a security model is just the beginning. In this chapter, we’ll discuss how you can create processes and procedures to govern future changes and to promote those changes to other environments.

As mentioned throughout this book, SAP HANA is a development platform, which makes SAP HANA more than just a database. As a development platform, security administrators will discover that security-related development artifacts can be easily transported between different SAP HANA instances. In this chapter, we’ll outline the best practices and options available when using this transportation mechanism, so that you can maintain a consistent security model between SAP HANA instances. We’ll start by discussing how to maintain a consistent security model. Then, we’ll review the steps necessary to define a delivery unit containing security-related artifacts. You’ll use the delivery unit to transport security models between systems. We’ll then review the steps necessary to access the SAP HANA application lifecycle management tool. Finally, we’ll discuss additional features in SAP HANA application lifecycle management that can benefit the lifecycle management of security artifacts.

## 14.1 Maintaining a Consistent Security Model

Most organizations will maintain more than one instance of SAP HANA within their landscapes. Some organizations will need multiple instances to support multiple SAP application solutions, and others will need multiple instances to support lifecycle management within the same solution. Given the likelihood that an organization will have multiple unique or related instances, expecting security administrators to manually create security models for each unique environment isn’t practical. Fortunately, SAP HANA offers capabilities to easily transport repository-based content, including repository roles, between environments.

You’ll need to follow three sets of guidelines to ensure that your security models are both consistent and secure. The first practice involves lifecycle management best practices. The second governs how you make changes to the security model and conduct testing. The final practice centers on the policies and procedures required to maintain a consistent security model in each environment.

### 14.1.1 Best Practices

Security model lifecycle management encompasses the process, procedures, and tasks you’ll follow to ensure that your security model is secure and consistent in all environments. Because SAP HANA is also a development platform, built-in tools are available to help you manage and promote software code stored within its repository. Fortunately, many of your security artifacts, such as repository roles, are stored in this repository. To facilitate the management and promotion of the software code and security artifacts within SAP HANA, a tool called SAP HANA application lifecycle management is available as a web-based application hosted in the SAP HANA extended application services engine (XS engine). Note that, as of SAP HANA 2.0 SPS 04, the SAP HANA cockpit does not offer tools to help you manage the application lifecycle of artifacts hosted in the SAP HANA XS-based repository.

SAP HANA application lifecycle management allows you organization to both manage changes within the SAP HANA repository and promote those changes to other SAP HANA environments. In [Section 14.2](#14_002.html#h14.2) and [Section 14.3](#14_003.html#h14.3), we’ll discuss SAP HANA application lifecycle management in more detail, but in this section, we’ll discuss a few basic security model lifecycle management best practices. Securing an SAP HANA environment is only the first step. Once the environment is secured, you’ll need to follow strict policies and procedures to help maintain the security of the environment. Specifically, organizations should maintain multiple environments, create content in development, organize content effectively, cleanup unused content, have a rollback plan, and manage content dependencies. These best practices will help you formulate policies and procedures to facilitate security model and content lifecycle management. To further your understanding, let’s look at each of these items in more detail.

#### Maintaining Multiple Environments

A key dependency in the development, validation, testing, and implementation of a security model requires that organizations maintain multiple unique SAP HANA instances. Most organizations will deploy a development (DEV) environment in which they create content, security models, and other dependent content; a quality assurance (QA) environment in which they validate the promotion process and test content changes to application code; and a production (PROD) environment, which serves as the active environment in which your users work and execute business-related transactions.

The purpose of maintaining multiple environments is to identify issues with developed content or to identify issues related to configuration changes before they are implemented in production. As shown in [Figure 14.1](#14_001.html#f14.1), the lifecycle management process for SAP HANA security follows a strict path from DEV to QA to PROD.

[![Lifecycle Management Process for SAP HANA Security](bilderklein/klein14_001.png)](img-f14.1.html)

**Figure 14.1** Lifecycle Management Process for SAP HANA Security

#### Creating Content in Development

Generating repository roles and their dependencies in a DEV environment is best. After the content is validated, this content should then be transported to a QA environment for further testing. We never recommend making security changes directly in production. Changes in production are untested and can lead to the accidental elevation of privileges or the exposure of sensitive data.

#### Organizing Content in Packages
