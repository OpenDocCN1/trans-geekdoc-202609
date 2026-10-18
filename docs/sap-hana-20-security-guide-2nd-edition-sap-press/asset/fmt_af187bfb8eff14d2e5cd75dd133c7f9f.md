
# [15   Querying Audit Data](#15_004.html#h15.4)

## [15.5   Case Study: Defining Audit Policies](#15_005.html#h15.5)

### [15.5.1   Proactive Event Monitoring](#15_005.html#h15.5.1)

### [15.5.2   Audit Reporting](#15_005.html#h15.5.2)

### [15.5.3   Authentication Auditing](#15_005.html#h15.5.3)

### [15.5.4   Unauthorized Action Auditing](#15_005.html#h15.5.4)

### [15.5.5   System Change Auditing](#15_005.html#h15.5.5)

### [15.5.6   Security Management Task Auditing](#15_005.html#h15.5.6)

### [15.5.7   Super User Event Auditing](#15_005.html#h15.5.7)

## [15.6   Summary](#15_006.html#h15.6)

# [16   Security Tracing and Troubleshooting](#16_001.html#h16)

## [16.1   Authorization Tracing](#16_001.html#h16.1)

### [16.1.1   Enabling Tracing with the SAP HANA Cockpit](#16_001.html#h16.1.1)

### [16.1.2   Enabling Tracing with SQL](#16_001.html#h16.1.2)

### [16.1.3   Viewing the Trace File in the SAP HANA Cockpit](#16_001.html#h16.1.3)

## [16.2   Querying the System to Review Effective Privileges](#16_002.html#h16.2)

### [16.2.1   Granted Privileges](#16_002.html#h16.2.1)

### [16.2.2   Granted Roles](#16_002.html#h16.2.2)

### [16.2.3   Accessible Views](#16_002.html#h16.2.3)

### [16.2.4   Effective Privilege Grantees](#16_002.html#h16.2.4)

### [16.2.5   Effective Structured Privileges](#16_002.html#h16.2.5)

### [16.2.6   Effective Privileges](#16_002.html#h16.2.6)

### [16.2.7   Effective Role Grantees](#16_002.html#h16.2.7)

### [16.2.8   Effective Roles](#16_002.html#h16.2.8)

## [16.3   Case Study: Identifying Deficiencies in Information View Access](#16_003.html#h16.3)

### [16.3.1   Troubleshooting the Problem](#16_003.html#h16.3.1)

### [16.3.2   Reviewing the Results](#16_003.html#h16.3.2)

### [16.3.3   Reviewing the Solution](#16_003.html#h16.3.3)

## [16.4   Summary](#16_004.html#h16.4)

# [17   Security Recommendations](#17_001.html#h17)

## [17.1   Password Authentication Settings](#17_001.html#h17.1)

### [17.1.1   Standard User Password Policies](#17_001.html#h17.1.1)

### [17.1.2   Service Accounts](#17_001.html#h17.1.2)

## [17.2   Encryption Settings](#17_002.html#h17.2)

## [17.3   Identifying Users with Elevated Privileges](#17_003.html#h17.3)

### [17.3.1   System Privileges](#17_003.html#h17.3.1)

### [17.3.2   Root Package Privileges](#17_003.html#h17.3.2)

### [17.3.3   Bypass Analytic Privileges](#17_003.html#h17.3.3)

### [17.3.4   Default Standard Roles](#17_003.html#h17.3.4)

### [17.3.5   WITH GRANT or WITH ADMIN](#17_003.html#h17.3.5)

### [17.3.6   Trace, Dump File, and Debug Access](#17_003.html#h17.3.6)

## [17.4   Disabling the SYSTEM Account](#17_004.html#h17.4)

## [17.5   Identifying Privilege Escalation Vulnerabilities](#17_005.html#h17.5)

## [17.6   Handover from Hardware Vendors](#17_006.html#h17.6)

## [17.7   Creating Audit Policies](#17_007.html#h17.7)

## [17.8   Summary](#17_008.html#h17.8)

# [18   SAP HANA XSA Security](#18_001.html#h18)

## [18.1   Overview of SAP HANA XSA](#18_001.html#h18.1)

## [18.2   Managing Space Access, Users, and Roles Collections in SAP HANA XSA](#18_002.html#h18.2)

### [18.2.1   Accessing Applications](#18_002.html#h18.2.1)

### [18.2.2   Managing SAP HANA XSA Users](#18_002.html#h18.2.2)

### [18.2.3   Managing SAP HANA XSA Role Collections](#18_002.html#h18.2.3)

### [18.2.4   Managing Organization and Space Access](#18_002.html#h18.2.4)

## [18.3   Working with SAP Web IDE for SAP HANA](#18_003.html#h18.3)

### [18.3.1   SAP Web IDE for SAP HANA Overview](#18_003.html#h18.3.1)

### [18.3.2   SAP HANA Database Explorer in SAP Web IDE for SAP HANA](#18_003.html#h18.3.2)

## [18.4   HDI Containers and Security](#18_004.html#h18.4)

### [18.4.1   Security Architecture of the HDI Container](#18_004.html#h18.4.1)

### [18.4.2   HDI Container Roles](#18_004.html#h18.4.2)

### [18.4.3   Granting the HDI Container Access to External Objects](#18_004.html#h18.4.3)

## [18.5   Summary](#18_005.html#h18.5)

# [The Author](#A_001.html#hA)

# [Index](#index.html#index)

## [Service Pages](#service.html#service)

## [Legal Notes](#legal_notes.html#recht)

# Preface

SAP HANA powers SAP applications and hosts data from a variety of sources, functionalities that are often critical to an organization’s operations. Failure to properly secure an SAP HANA environment often can lead to system instability and hurt data integrity; therefore, SAP HANA security must be given the proper attention and scrutiny.

## Purpose

This book was written with the goal of educating readers about securing SAP HANA. We’ll focus on key aspects of the SAP HANA security model, including user provisioning, role creation, privilege assignment, encryption, auditing, and authentication. We’ll also discuss the tools you can use to create and maintain an SAP HANA security model. Such information is critical for SAP HANA security architects to implement security models for their organizations. This information is also necessary for organizations to protect the data hosted within SAP HANA and to maintain the reliability of systems that rely on SAP HANA.

## Who Should Read This Book?

This book will help security teams, SAP Basis teams, security consultants, and anyone looking for a comprehensive guide to implementing an SAP HANA security model.

We recommend the following prerequisites for readers of this book:

*   General knowledge of the SAP HANA cockpit
*   General knowledge of SQL
*   Experience working in areas of database administration
*   Experience working with database objects such as tables, views, and stored procedures

Each chapter is structured to offer background and theory for specific security-related concepts. Many chapters conclude with a case study—centering on the fictitious E-Corporation—for a “real-world” application of the topics covered in the book. Our goal is to provide you with technical knowledge and a unique perspective on how security has been implemented in the field based on real customer engagements.

## Structure of This Book

The book is structured into 18 chapters. The Introduction and [Chapter 1](#01_001.html#h1) through [Chapter 4](#04_001.html#h4) introduce SAP HANA, SAP HANA security, the SAP HANA cockpit, privileges, and database objects. [Chapter 4](#04_001.html#h4), [Chapter 5](#05_001.html#h5), and [Chapter 6](#06_001.html#h6) introduce users and roles. [Chapter 7](#07_001.html#h7) through [Chapter 11](#11_001.html#h11) discuss the various privilege types within SAP HANA. The remaining chapters discuss SAP HANA authentication, encryption, lifecycle management, audit policies, security troubleshooting, and general recommendations for securing your SAP HANA environment.

### Introduction

Representing the next evolution of data management for many organizations, SAP HANA also powers critical applications for managing your organization. Thus, SAP HANA can be a valuable asset in many organizations. Because of its importance, SAP HANA must be secured. In the Introduction, we’ll provide an overview of SAP HANA’s hardware and software layers. We’ll introduce the basic concepts of SAP HANA security and list several reasons why securing your SAP HANA environment is important.

### [Chapter 1](#01_001.html#h1): Managing Security with the SAP HANA Cockpit

This chapter introduces the SAP HANA cockpit, a key tool for managing SAP HANA security. We’ll start with an overview of the architecture of the SAP HANA cockpit. We’ll explain how you can navigate the SAP HANA cockpit. We’ll also provide a detailed workflow to help identify key security management areas within the SAP HANA cockpit, including all security-related functionalities, the SAP HANA database explorer, and the SQL console.

### [Chapter 2](#02_001.html#h2): Introduction to SAP HANA Privileges
