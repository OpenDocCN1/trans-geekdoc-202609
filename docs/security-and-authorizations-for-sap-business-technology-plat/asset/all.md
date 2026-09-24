![Security and Authorizations for SAP Business Technology Platform – Cover](common/cover.jpg)

Martin Koch, Siegfried Zeilinger

# Security and Authorizations for SAP® Business Technology Platform

![Logo Rheinwerk Publishing](common/logo_sap.png)

# Imprint

This e-book is a publication many contributed to, specifically:

Editor   Megan Fuerst  
Acquisitions Editor   Hareem Shafi  
Copyeditor   Yvette Chin  
Translation   Author translation  
Cover Design   Graham Geary  
Photo Credit    iStockphoto: 1320309139/© dem10  
Production E-Book     
Typesetting E-Book   III-satz, Husby (Germany)  

We hope that you liked this e-book. Please share your feedback with us and read the [Service Pages](#service.html) to find out how to contact us.

  
Library of Congress Cataloging-in-Publication Data Control Number:2022946788

ISBN 978-1-4932-2355-8 (print)  
ISBN 978-1-4932-2356-5 (e-book)  
ISBN 978-1-4932-2357-2 (print and e-book)

  
© 2023 by Rheinwerk Publishing Inc., Boston (MA)  
1st edition 2023

# Dear Reader,

The weather is getting colder, and the leaves are starting to turn. This can only mean one thing: It’s time to start worrying about holiday travel.

A recent Thanksgiving instilled this fear in me. I made the mistake of choosing a 6 a.m. flight, which meant a 3 a.m. drive to the airport to arrive with plenty of time to spare. Naturally, in the groggy rush of the morning, I forgot to transfer my wallet to my travel bag.

I realized my mistake in the departures drop-off area, which was swarming with fellow travelers heading home for the holiday. Thankful that I’m always early to the airport, I made a frantic return trip, secured my wallet, and arrived back roughly an hour ahead of my flight. I beelined my way past the baggage check, and found the end of an extremely long line. It took nearly 30 minutes to reach the checkpoint and show my ID. And then there was the actual security: I was one of hundreds of impatient flyers removing shoes, taking out laptops, dumping out water bottles, and anxiously waiting. The minutes ticked by.

I did make my flight—after a sprint to my gate. However, I didn’t fully relax until I was in the sky.

This book may be on an entirely different type of cloud security, but regardless of the context, security can be stressful. If you’re using SAP Business Technology Platform, it’s critical to protect your organization from unique risks in the cloud. In these pages, you’ll find the step-by-step instructions you need to secure the platform and set up authorizations, whether you’re using the Neo or Cloud Foundry environment. Following guidance from the experts, you’ll journey to the cloud with confidence!

What did you think about  Security and Authorizations for SAP Business Technology Platform? Your comments and suggestions are the most useful tools to help us make our books the best they can be. Please feel free to contact me and share any praise or criticism you may have.

Thank you for purchasing a book from SAP PRESS!

 Megan Fuerst  
 Editor, SAP PRESS

 [meganf@rheinwerk-publishing.com](mailto:meganf@rheinwerk-publishing.com)  
 [www.sap-press.com](http://www.sap-press.com)  
Rheinwerk Publishing • Boston, MA

# Notes on Usage

This e-book is protected by copyright. By purchasing this e-book, you have agreed to accept and adhere to the copyrights. You are entitled to use this e-book for personal purposes. You may print and copy it, too, but also only for personal use. Sharing an electronic or printed copy with others, however, is not permitted, neither as a whole nor in parts. Of course, making them available on the internet or in a company network is illegal as well.

For detailed and legally binding usage conditions, please refer to the section [Legal Notes](#legal_notes.html).

This e-book copy contains a digital watermark, a signature that indicates which person may use this copy:

  

# Notes on the Screen Presentation

You are reading this e-book in a file format (EPUB or Mobi) that makes the book content adaptable to the display options of your reading device and to your personal needs. That’s a great thing; but unfortunately not every device displays the content in the same way and the rendering of features such as pictures and tables or hyphenation can lead to difficulties. This e-book was optimized for the presentation on as many common reading devices as possible.

If you want to zoom in on a figure (especially in iBooks on the iPad), tap the respective figure once. By tapping once again, you return to the previous screen. You can find more recommendations on the customization of the screen layout on the [Service Pages](#service.html).

# Table of Contents

## [Dear Reader](#dear_reader.html#extra-leser)

## [Notes on Usage](#notes.html#extra-hinweise)

## [Table of Contents](#toc.html#extra-toc)

## [Preface](#00a_001.html#h0a)

# [1   Introduction to SAP Business Technology Platform](#01_001.html#h1)

## [1.1   Positioning](#01_001.html#h1.1)

### [1.1.1   SAP Extension Suite: Developing and Extending Cloud Solutions](#01_001.html#h1.1.1)

### [1.1.2   SAP Integration Suite: Cloud Solutions and On-Premise Systems](#01_001.html#h1.1.2)

## [1.2   Environments](#01_002.html#h1.2)

### [1.2.1   SAP BTP, Neo Environment](#01_002.html#h1.2.1)

### [1.2.2   SAP BTP, Cloud Foundry Environment](#01_002.html#h1.2.2)

### [1.2.3   Environment Selection](#01_002.html#h1.2.3)

## [1.3   Architecture](#01_003.html#h1.3)

### [1.3.1   Global Accounts](#01_003.html#h1.3.1)

### [1.3.2   Subaccounts](#01_003.html#h1.3.2)

### [1.3.3   Organizations](#01_003.html#h1.3.3)

### [1.3.4   Spaces](#01_003.html#h1.3.4)

## [1.4   Summary](#01_004.html#h1.4)

# [2   SAP Business Technology Platform Security at a Glance](#02_001.html#h2)

## [2.1   Secure Communication](#02_001.html#h2.1)

### [2.1.1   Basics of Secure Communication](#02_001.html#h2.1.1)

### [2.1.2   SAP Destination Service](#02_001.html#h2.1.2)

### [2.1.3   Certificate Handling in Destinations](#02_001.html#h2.1.3)

## [2.2   Authentication](#02_002.html#h2.2)

### [2.2.1   Identity Providers for SAP BTP](#02_002.html#h2.2.1)

### [2.2.2   Lightweight Directory Access Protocol](#02_002.html#h2.2.2)

## [2.3   Authorizations](#02_003.html#h2.3)

## [2.4   SAP Cloud Identity Services](#02_004.html#h2.4)

### [2.4.1   Identity Authentication](#02_004.html#h2.4.1)

### [2.4.2   Identity Provisioning](#02_004.html#h2.4.2)

## [2.5   SAP Cloud Identity Access Governance](#02_005.html#h2.5)

## [2.6   Checklist for General Security](#02_006.html#h2.6)

## [2.7   Summary](#02_007.html#h2.7)

# [3   Configuring Security and Authorizations in the Neo Environment](#03_001.html#h3)

## [3.1   Setting Up the Command Line for SAP BTP, Neo Environment](#03_001.html#h3.1)

## [3.2   User Management](#03_002.html#h3.2)

## [3.3   Trust Configuration](#03_003.html#h3.3)

### [3.3.1   Setting Up the Local Service Provider](#03_003.html#h3.3.1)

### [3.3.2   Setting Up the Platform Identity Provider](#03_003.html#h3.3.2)

### [3.3.3   Setting Up the Application Identity Provider](#03_003.html#h3.3.3)

## [3.4   Authorization Management](#03_004.html#h3.4)

### [3.4.1   Creating and Managing Roles](#03_004.html#h3.4.1)

### [3.4.2   Creating and Managing User Groups](#03_004.html#h3.4.2)

## [3.5   Checklist for Security and Permissions in SAP BTP, Neo Environment](#03_005.html#h3.5)

## [3.6   Real-World Examples of User and Authorization Management](#03_006.html#h3.6)

### [3.6.1   Two-Factor Authentication of Subaccount Admins Using the Platform Identity Provider](#03_006.html#h3.6.1)

### [3.6.2   Authenticating SAP Web IDE Users via Microsoft Azure AD](#03_006.html#h3.6.2)

## [3.7   Summary](#03_007.html#h3.7)

# [4   Configuring Security and Authorizations in the Cloud Foundry Environment](#04_001.html#h4)

## [4.1   Setting Up the Command Line for SAP BTP, Cloud Foundry Environment](#04_001.html#h4.1)

## [4.2   User Management](#04_002.html#h4.2)

## [4.3   Trust Configuration](#04_003.html#h4.3)

### [4.3.1   Setting Up the SAP ID Service](#04_003.html#h4.3.1)

### [4.3.2   Setting Up a Platform Identity Provider](#04_003.html#h4.3.2)

### [4.3.3   Setting Up Third-Party Identity Providers](#04_003.html#h4.3.3)

## [4.4   Authorization Management](#04_004.html#h4.4)

### [4.4.1   Creating and Managing Roles](#04_004.html#h4.4.1)

### [4.4.2   Maintaining Composite Roles](#04_004.html#h4.4.2)

### [4.4.3   Composite Role Mapping](#04_004.html#h4.4.3)

### [4.4.4   Reporting in the Authorization Environment](#04_004.html#h4.4.4)

## [4.5   Checklist for Security and Permissions in SAP BTP, Cloud Foundry Environment](#04_005.html#h4.5)

## [4.6   Real-World Examples of User and Permission Management](#04_006.html#h4.6)

### [4.6.1   Activation and Secure Configuration of the SAP Launchpad Service](#04_006.html#h4.6.1)

### [4.6.2   Two-Factor Authentication of Users via Microsoft Azure AD](#04_006.html#h4.6.2)

## [4.7   Summary](#04_007.html#h4.7)

# [5   Secure Cloud Connector Configuration](#05_001.html#h5)

## [5.1   Architecture](#05_001.html#h5.1)

## [5.2   Installing and Configuring the Cloud Connector](#05_002.html#h5.2)

### [5.2.1   Download and Installation](#05_002.html#h5.2.1)

### [5.2.2   Initial Configuration](#05_002.html#h5.2.2)

### [5.2.3   Connection to SAP BTP](#05_002.html#h5.2.3)

### [5.2.4   Further Recommendations for Secure Configuration](#05_002.html#h5.2.4)

### [5.2.5   Monitoring](#05_002.html#h5.2.5)

## [5.3   Authentication Methods](#05_003.html#h5.3)

## [5.4   Cloud-to-On-Premise Connections](#05_004.html#h5.4)

### [5.4.1   Security Precautions](#05_004.html#h5.4.1)

### [5.4.2   Setting Up the Connection](#05_004.html#h5.4.2)

### [5.4.3   Configuring Access Control](#05_004.html#h5.4.3)

### [5.4.4   Enabling the SAP Connectivity Service](#05_004.html#h5.4.4)

## [5.5   Setting Up the SAP Destination Service](#05_005.html#h5.5)

### [5.5.1   Creating Destinations in SAP BTP, Neo Environment](#05_005.html#h5.5.1)

### [5.5.2   Creating Destinations in SAP BTP, Cloud Foundry Environment](#05_005.html#h5.5.2)

## [5.6   Checklist for Cloud Connector Configuration](#05_006.html#h5.6)

## [5.7   Real-World Examples of Secure Cloud Connector Configuration](#05_007.html#h5.7)

### [5.7.1   Connecting an On-Premise Git Server to SAP BTP, Neo Environment](#05_007.html#h5.7.1)

### [5.7.2   Connecting SAP BTP, Cloud Foundry Environment to an SAP S/4HANA System](#05_007.html#h5.7.2)

### [5.7.3   LDAP Authentication Configuration](#05_007.html#h5.7.3)

## [5.8   Summary](#05_008.html#h5.8)

# [6   Administration Tools](#06_001.html#h6)

## [6.1   Administering SAP BTP, Neo Environment via the Command Line](#06_001.html#h6.1)

## [6.2   Managing Global Accounts via the Command Line](#06_002.html#h6.2)

## [6.3   Administration via APIs](#06_003.html#h6.3)

### [6.3.1   SAP API Business Hub](#06_003.html#h6.3.1)

### [6.3.2   Audit Log Retrieval via APIs](#06_003.html#h6.3.2)

### [6.3.3   User Management via APIs](#06_003.html#h6.3.3)

### [6.3.4   Permission Management via APIs](#06_003.html#h6.3.4)

### [6.3.5   SAP Cloud Management Service APIs](#06_003.html#h6.3.5)

## [6.4   Checklist for Working with the Command Line and APIs](#06_004.html#h6.4)

## [6.5   Real-World Examples of Using the Command Line Securely](#06_005.html#h6.5)

### [6.5.1   Using the Command Line to Configure a Custom Domain in SAP BTP, Neo Environment](#06_005.html#h6.5.1)

### [6.5.2   Using the Command Line to Manage SAP BTP](#06_005.html#h6.5.2)

## [6.6   Summary](#06_006.html#h6.6)

# [7   Securing Key Cloud Services](#07_001.html#h7)

## [7.1   SAP Web IDE and SAP Business Application Studio](#07_001.html#h7.1)

### [7.1.1   SAP Web IDE](#07_001.html#h7.1.1)

### [7.1.2   SAP Business Application Studio](#07_001.html#h7.1.2)

## [7.2   Cloud Integration](#07_002.html#h7.2)

### [7.2.1   Cloud Integration in SAP BTP, Neo Environment](#07_002.html#h7.2.1)

### [7.2.2   Cloud Integration in SAP BTP, Cloud Foundry Environment](#07_002.html#h7.2.2)

### [7.2.3   Roles and Authorizations](#07_002.html#h7.2.3)

### [7.2.4   Security Recommendations](#07_002.html#h7.2.4)

## [7.3   SAP Integration Suite in SAP BTP, Cloud Foundry Environment](#07_003.html#h7.3)

### [7.3.1   SAP API Management](#07_003.html#h7.3.1)

### [7.3.2   Roles and Authorizations](#07_003.html#h7.3.2)

### [7.3.3   Securing the Provided APIs and Endpoints](#07_003.html#h7.3.3)

## [7.4   SAP Cloud Portal Service and SAP Launchpad Service](#07_004.html#h7.4)

### [7.4.1   SAP Cloud Portal Service in SAP BTP, Neo Environment](#07_004.html#h7.4.1)

### [7.4.2   SAP Launchpad Service in SAP BTP, Cloud Foundry Environment](#07_004.html#h7.4.2)

## [7.5   SAP BTP, ABAP Environment](#07_005.html#h7.5)

### [7.5.1   User Administration](#07_005.html#h7.5.1)

### [7.5.2   Access to External Systems](#07_005.html#h7.5.2)

## [7.6   Corporate User Stores](#07_006.html#h7.6)

## [7.7   Checklist for Securing Cloud Services](#07_007.html#h7.7)

## [7.8   Summary](#07_008.html#h7.8)

# [A   The Authors](#A_001.html#hA)

# [Index](#index.html#index)

## [Service Pages](#service.html#service)

## [Legal Notes](#legal_notes.html#recht)

# Preface

Information technology has changed significantly in recent decades. For example, 20 years ago, we couldn’t imagine media provided on demand—now several people in a household can stream different content at the same time. Today, the cloud is everywhere, always available on all devices. Houses are no longer wired, but wireless networks are ubiquitous. But at what price? New wireless speakers are always listening in on the conversations taking place around them. A recent legal case involving a major retailer in the US revealed the recordings made by its smart home speaker, proving again that Orwell, with his work 1984, was a true visionary.

Now, your company must manage the balancing act between full digitization (with its far-reaching optimizations but also with completely new risks) and a more conservative, risk-averse approach that tries to minimize the risks of digitization. Real-world horror stories include universities paying tens of millions to hackers just to use their own data again or consulting firms replacing their entire stock of laptops because they were all infected by a virus or by encryption scripts. While these events show that digitization can be risky, completely different sales and marketing opportunities are now available.

In the area of business applications, as a market leader, SAP has helped large companies begin the journey into the cloud with applications for human resources (HR) management. SAP SuccessFactors and SAP Concur started as solutions for managing HR master data and travel expense accounting. This shift has lifted sensitive, but relatively uncritical, business data into the cloud for processing.

In the late 1990s and early 2000s, the industry buzz revolved around outsourcing or out-tasking. Major questions at the time were whether to host your own systems and who would take over routine tasks. Later, the virtualization of data centers was a hot topic. People no longer talked about servers, only about virtual instances that could be moved back and forth at will between, for example, São Paulo, Los Angeles, and Frankfurt.

Today, we use the terms cloud versus on-premise as we make similar decisions in different contexts. Do I move databases to the cloud, or do I use a service? Which components remain on-premise? Since exactly where the data is located is often no longer transparent, a bit more documentation than usual might be necessary to create. Key questions include the following: What are you still responsible for in the cloud, and what do you run after the cloud service completes? How safe is your telecommunications provider? What security risks do you run regarding data, processes, trade secrets, and more?

In this context, we can only repeat what has already been said repeatedly: The solutions that are worked out are usually commissioned, or at least approved, by departments. Regarding security and authorizations, IT managers can help, but the responsibility for the processes remains with the business departments, which must weigh the added value of a cloud-based solution against requirements and risks.

This book is intended to serve as both inspiration and guidance. We want to ask the right questions and derive recommendations from those questions. Even though this book is for technicians, by technicians, we’ll always try to think outside the box.

With this book, we are addressing both tech-savvy professionals and newcomers to SAP cloud. If you’re about to embark on your first cloud project, you’ll certainly find useful information. This book, however, is primarily aimed at IT administrators. Developers will also find helpful tips on relevant cloud services. Interested readers from specialist departments who want to think outside the box and, for example, make their own risk assessments, will also find relevant information in this book.

## The Structure of This Book

We’ll start this book with SAP’s positioning and strategy in the context of cloud products, then introduce SAP Business Technology Platform (SAP BTP) in more detail as SAP’s platform as a service (PaaS) offering. We’ll consider SAP BTP’s security aspects and then look at the connections between the cloud and your corporate network, until finally we turn our attention to administering and securing individual cloud services.

Most chapters conclude with a checklist. We hope you use these checklists to confirm whether you’ve asked the right questions about your hybrid system landscapes. If necessary, we recommend thinking through topics again from a different angle. You can also check whether you’ve understood the most important content in each chapter with these checklists. For example, if you’re already familiar with SAP BTP, Neo environment, go through the corresponding checklist first and thus determine whether the associated chapter would be worth your attention.

We also provide the checklists in the Product supplements section on this book's webpage for you to save and print, available at [www.sap-press.com/5627](http://www.sap-press.com/5627).

At the end of most chapters, you’ll also find practical scenarios in which we go through common requirements step by step. You can try out these examples on your own systems, as reinforcement.

In highlighted information boxes, you’ll find content in this book that is worth knowing and may be helpful but is somewhat outside the main explanation. So that you can immediately identify this information, we’ve provided the following types of boxes:

###### \[»\]  Note

In boxes marked with this symbol, you’ll find information on further topics or important content that you should remember.

###### \[ ! \]  Warning!

This symbol draws your attention to special features that you should be aware of. It also warns you of common mistakes or problems that may occur.

###### \[+\]  Tip

Tips marked with this symbol give you special recommendations from our personal experience on projects that can make your work easier.

###### \[eg\]  Example

Examples, indicated by this symbol, point out scenarios from practice and illustrate the functions presented.

Let’s briefly look at the contents of the individual chapters of this book:

*   [Chapter 1](#01_001.html#h1): Introduction to SAP Business Technology Platform  
    In this chapter, we’ll introduce you to SAP BTP and its associated terminology. We’ll explain the structure and positioning of the platform, paying particular attention to its relevance and how it fits into SAP’s product strategy. Finally, we’ll present its usage options.
    
*   [Chapter 2](#02_001.html#h2): SAP Business Technology Platform Security at a Glance  
    This chapter begins with an introduction to the various security mechanisms of SAP’s PaaS offering. You’ll learn about various authentication and authorization options. In this process, you’ll learn about the differences between the various SAP BTP environments available. Finally, we’ll walk you through creating user accounts and authorizations at the global account level.
    
*   [Chapter 3](#03_001.html#h3): Configuring Security and Authorizations in the Neo Environment  
    In this chapter, we’ll highlight the security features available in SAP BTP, Neo environment, in detail. We’ll walk you through setting up different trust configurations. We’ll then explain how to manage users, roles, and user groups.
    
*   [Chapter 4](#04_001.html#h4): Configuring Security and Authorizations in the Cloud Foundry Environment  
    In this chapter, we’ll explain security aspects of SAP BTP, Cloud Foundry environment. Using a best-practice implementation, you’ll learn how to make operations secure and cost effective.
    
*   [Chapter 5](#05_001.html#h5): Secure Cloud Connector Configuration  
    This chapter is devoted to the cloud connector, which is used to connect cloud-based and on-premise systems. The cloud connector is the central component for building hybrid system landscapes. After explaining its architecture, you’ll find instructions for installing and configuring the cloud connector. Securing this connection is described in detail. Finally, you’ll learn how to set up the SAP Destination service, which is the cloud counterpart to the locally installed cloud connector in SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment.
    
*   [Chapter 6](#06_001.html#h6): Administration Tools  
    In this chapter, we’ll provide recommendations for administering SAP BTP so as to minimize the resource burden for its use in your organization. We’ll introduce you to console tools and application programming interfaces (APIs) that enable efficient administration.
    
*   [Chapter 7](#07_001.html#h7): Securing Key Cloud Services  
    In this chapter, we’ll close with an overview of what we consider the most important services in SAP BTP and review these services from a security perspective.
    

In this book, we’ve tried to paint a well-rounded and complete picture of security issues in the context of SAP BTP. We thank you for your interest in our book and hope you enjoy reading it!

  
Martin Koch and Siegfried Zeilinger

# 1    Introduction to SAP Business Technology Platform

SAP Business Technology Platform (SAP BTP) plays a central role in SAP’s strategy. SAP BTP is used for extensions, for integration, and for innovative technologies in the context of hybrid system landscapes. Therefore, in the context of SAP solutions, using SAP BTP may be unavoidable.

SAP BTP is the platform as a service (PaaS) offering from the German software giant SAP. Released in 2012, the first version of this solution was called SAP NetWeaver Cloud. In 2013, renamed SAP HANA Cloud Platform, this solution was expanded over time to include more and more services. In 2017, SAP said goodbye to the name “HANA” in the PaaS offering, and the official product name was SAP Cloud Platform, until January 2021, when it became SAP BTP.

In this chapter, we’ll first discuss the positioning of SAP BTP within the SAP product portfolio in [Section 1.1](#01_001.html#h1.1). In 2021, SAP introduced two suite capabilities: SAP Integration Suite and SAP Extension Suite. A key aspect is the topic of innovation, which is covered by SAP Extension Suite. The platform is intended to support SAP customers and partners in implementing new ideas quickly and efficiently at the cutting edge of technology. But the platform also takes on a strategic role as an extension environment for SAP’s software as a service (SaaS) offerings. And because existing SaaS offerings, innovative new developments, and enhancements often need to communicate with existing systems, SAP BTP also serves as an integration platform, as covered by SAP Integration Suite. With the help of SAP Integration Suite, SaaS applications can be integrated with both cloud-based and on-premise systems in end-to-end processes.

SAP BTP can be operated in various geographical regions both in SAP’s own data centers and in data centers run by hyperscaler providers. These providers include Amazon with Amazon Web Services (AWS), Google with Google Cloud Platform, Microsoft with Microsoft Azure, and Alibaba with Alibaba Cloud. SAP’s strategic focus is on using the infrastructures of these hyperscalers to operate SAP BTP. This alignment enables SAP to expand SAP BTP into new regions more quickly and more efficiently. These hyperscalers have a large number of globally distributed data centers that SAP uses as infrastructure. As a result, SAP doesn’t need to build new data centers of its own to tap into new geographic regions.

In addition, several runtime environments of SAP BTP are available. At the time of writing, the most frequently used are SAP BTP, Neo environment, developed by SAP itself, and SAP BTP, Cloud Foundry environment, based on open-source technologies. In addition, SAP BTP, Kyma environment has been available since the second half of 2020, although this runtime environment is still in its infancy. We’ll present the first two environments and the services offered on them in [Section 1.2](#01_002.html#h1.2).

After you’ve explored SAP BTP’s areas of use and the different environments for SAP BTP, we’ll explain the account model for using the platform in [Section 1.3](#01_003.html#h1.3). You’ll learn about key considerations and pitfalls when choosing an environment, about which commercial usage models are available, and about the advantages and disadvantages of each option.

## 1.1    Positioning

SAP BTP fully covers innovation, extension, and integration use cases as a central building block of SAP’s intelligent enterprise strategy. SAP defines this strategy at [www.sap.com/products/intelligent-enterprise.html](http://www.sap.com/products/intelligent-enterprise.html) in the following way:

> “An intelligent, sustainable enterprise is one that consistently applies advanced technologies and best practices within agile, integrated business processes.”

To summarize, SAP BTP enables organizations to do the following:

*   Use powerful technologies to collect insights about customer, partner, and employee sentiment to sense opportunities, risks, and trends
    
*   Optimize business processes by incorporating artificial intelligence (AI) and machine learning technologies
    
*   Employ tools to understand what is happening across a business and why
    
*   Understand and manage your environmental impact by building flexible value chains and following industry best practices
    
*   Run value chains from end to end in the cloud through the implementation of vertical processes for each industry
    

As shown in [Figure 1.1](#01_001.html#f1.1), SAP has vertically divided the intelligent enterprise into three layers: business processes, applications, and technology.

In simple terms, the focus of the intelligent enterprise strategy is all about business networks, which represent the top layer. SAP Business Network enables you to collaborate with all the trading partners in your supply chain, including suppliers, logistics and service providers, asset operators, maintenance companies, and many more. You’ll gain unprecedented visibility into all processes in your supply chain and make your business more resilient. The whole thing can be summed up with the following three buzzwords:

*   Real-time collaboration  
    You can digitally collaborate with your trading partners in real time to increase operational efficiency. This feature enables the exchange of accurate and consistent data and is the basis for improved planning and optimized processes. With these improvements, your company can increase its resilience.
    
*   Extensive transparency  
    You’ll get an overview of your trading partners’ inventories and capacities. This visibility enables you to optimize your supply chain operations and avoid delays or interruptions.
    
*   Intelligent insights  
    You can use industry-specific benchmarks and other key performance indicators (KPIs) to analyze your company’s performance and identify supply chain issues before they impact you and, in turn, your customers.
    

[![SAP’s Intelligent Enterprise Architecture](bilderklein/klein01_001.png)](img-f1.1.html) 

**Figure 1.1**     SAP’s Intelligent Enterprise Architecture

SAP Business Network offers three solutions for working with your trading partners:

*   SAP Business Network for Procurement  
    This network supports you in planning-driven automation, the optimization of capacities and inventories, and streamlining procurement processes.
    
*   SAP Business Network for Logistics  
    Through this network, you can collaborate with shippers and carriers, share insights, and create transparency along your entire supply chain.
    
*   SAP Business Network for Asset Intelligence  
    This network supports working with asset owners, operators, and service providers and enables sharing information through a single, consistent version of asset master data.
    

On the second layer, applications provide the data for SAP Business Network by being fully integrated. On this level, experience management plays a decisive role. The goal is to ensure that you can deliver a consistent experience across all applications and industries, whether for employees, customers, or suppliers. SAP has placed the intelligent suite and the industry cloud in this level:

*   Intelligent suite  
    An integrated yet modular suite of line-of-business applications enabling SAP customers to share insights across functions, better address stakeholders, and simplify day-to-day operations. Line-of-business applications include products like SAP Business Suite, SAP S/4HANA, SAP SuccessFactors, SAP Concur, SAP Ariba, SAP Fieldglass, etc.
    
*   Industry cloud  
    SAP’s industry cloud simplifies cross-industry access to innovative vertical solutions. Developed by SAP and our partners on an open platform, these solutions are compatible with SAP’s intelligent product suite. The industry cloud enables you to drive business transformation profitably and sustainably, seize new opportunities, and manage disruption and change in your industry.
    

The third layer, technology, is the home of SAP BTP. With SAP BTP, your company can break down departmental silos and introduce dynamic, cross-functional business processes to achieve optimal results. SAP BTP combines intelligent enterprise applications with database and data management, analytics, integration capabilities, and extension capabilities on a stable and proven platform for both cloud and hybrid environments, as shown in [Figure 1.2](#01_001.html#f1.2).

[![SAP BTP Overview](bilderklein/klein01_002.png)](img-f1.2.html) 

**Figure 1.2**     SAP BTP Overview

The following four areas are covered by corresponding services on SAP BTP:

*   Database and data management  
    Services for storing data in the cloud, for data intelligence, and for master data governance.
    
*   Analytics  
    Services that enable deep insights into your data and the ability to visualize your data in appealing ways.
    
*   Application development and integration  
    Services that provide the best possible support in the development of your own applications and in the extension of SAP SaaS applications, as well as the ability to integrate with various systems in a hybrid system landscape.
    
*   Intelligent technologies  
    Services for AI, machine learning, robotic process automation (RPA), the Internet of Things (IoT), and edge computing. These technologies help you redesign your processes and business models.
    

All full list of all available services in SAP BTP are described in SAP Discovery Center at [https://discovery-center.cloud.sap/](https://discovery-center.cloud.sap/), shown in [Figure 1.3](#01_001.html#f1.3).

[![SAP Discovery Center](bilderklein/klein01_003.png)](img-f1.3.html) 

**Figure 1.3**     SAP Discovery Center

SAP offers several licensing models for SAP BTP services, which we’ll introduce in [Section 1.3](#01_003.html#h1.3). In 2021, SAP decided to split SAP BTP into the two suites: SAP Integration Suite and SAP Extension Suite. We’ll describe both SAP Integration Suite and SAP Extension Suite in more detail in this section.

### 1.1.1    SAP Extension Suite: Developing and Extending Cloud Solutions

As its name suggests, you might think that SAP Extension Suite is a solution intended exclusively for extending SAP SaaS applications. But this is not the case. SAP Extension Suite is not a dedicated product and is instead the umbrella term for a collection of a range of services. With SAP Extension Suite services, you can develop and extend your solutions, optimize your business processes, and create engaging digital experiences. SAP Extension Suite helps you achieve the following goals:

*   Increase development productivity and efficiency
    
*   Realize faster value creation
    
*   Ensure data consistency and quality
    
*   Compliance with regulations
    

As you can imagine from this list, a wide variety of services must be available to achieve these goals. Therefore, SAP has divided these services into the following three sections:

*   Development efficiency  
    These services allow you to rapidly build and extend business applications and processes. You can reuse components instead of rebuilding them from scratch, using a library of prebuilt components, templates, and application programming interfaces (APIs). The provided services allow you to follow no-code, low-code, and pro-code development approaches. In addition to the classic developer tools, the runtime environments for Cloud Foundry, ABAP, and Kyma are also an integral part of development efficiency capabilities. In addition, the security services discussed in this book, such as the Identity Authentication service and the Identity Provisioning service, fall under this category.
    
*   Digital experience  
    These services enable you to deliver a consistent and harmonized user experience (UX) across all digital interaction points. This category of services allows you to consolidate disparate systems and tools into a single access point for your entire enterprise to improve the UX and easily create employee or supplier portals. In addition, SAP offers services for delivering customized applications for mobile devices. These features, in turn, form the foundation for delivering enterprise data and increasing employee productivity, engagement, and satisfaction.
    
*   Digital process automation   
    These services enable you to develop workflows by using simple drag-and-drop functions, all based on an intuitive, user-friendly, and powerful no-code development environment. With the help of RPA, you can automate routine manual tasks and decision-making. Furthermore, you can simplify projects with predefined process flows, forms, business rules, and dashboards for process visibility while extending standard processes in SAP applications with packages for predefined process content. A highlight of this category of services is the SAP Intelligent Robotic Process Automation (SAP Intelligent RPA) store, where you can access predefined content for creating your own automations, as shown in [Figure 1.4](#01_001.html#f1.4).
    

[![SAP Intelligent RPA Store](bilderklein/klein01_004.png)](img-f1.4.html) 

**Figure 1.4**     SAP Intelligent RPA Store

Another key use case covered by various SAP Extension Suite capabilities is the extension of SAP SaaS applications, which is often event driven. If an event occurs in an SaaS product, such as the entry of a new application in SAP SuccessFactors or the creation of a new lead in SAP Sales Cloud, these needs can be fulfilled in extensions. Thus, the extension of SaaS applications is event driven, in accordance with the ideals common in development literature and also for SAP. The idea behind event-driven extensions is now trivial and has been in use for many years in a wide variety of integration scenarios. Triggering an event results in a message being sent to the SAP Event Mesh service, which is responsible for asynchronous messaging. Extensions on SAP BTP pick up this message and can react to it. The message itself does not contain the full affected record of the SaaS application, only an ID. The extension uses this ID to retrieve the required data from the SaaS application via an API. Communication with the SaaS application, regardless of whether data is only read or also manipulated, takes place exclusively via APIs.

In this context, we can describe these applications as “loosely coupled.” Extensions to the data model as well as the storage of the data take place in the extension. As a result, the SaaS application itself does not require change, and SAP can perform updates to the SaaS application without affecting related extensions. Extensions are characterized by the fact that they can run in a serverless environment. In these environments, applications that extend the digital core (i.e., the core business application) can be created, managed, and executed in SAP Extension Suite. Serverless architectures are a proven technology, tested for years by various voice-activated virtual assistants like Amazon Alexa or Apple Siri. Serverless architectures consist of servers that are fully managed by the cloud provider, which also applies to provisioning and scaling. In serverless architectures, the pay-per-use principle is applied; that is, you only pay for the resources you use. Thus, while the cloud provider is responsible for automatic scaling, management, and operation of the infrastructure, you and your development team can concentrate on the development and architecture of applications.

To ensure that you’re not left to your own devices when designing and developing extensions, SAP published the SAP Application Extension Methodology. This methodology allows you to create a customer-specific organizational framework that helps solution architects make the right technology choices for building an extension, as shown in [Figure 1.5](#01_001.html#f1.5).

[![SAP Application Extension Methodology](bilderklein/klein01_005.png)](img-f1.5.html) 

**Figure 1.5**     SAP Application Extension Methodology

### 1.1.2    SAP Integration Suite: Cloud Solutions and On-Premise Systems

The second suite capability of SAP BTP is SAP Integration Suite, which is a key enabler of the intelligent enterprise and a growing priority for many organizations. As digital interactions have become the norm, connected, contextual, and end-to-end digital experiences are the new standard. You can prepare your organization for the future using integration to improve customer, product, employee, and brand experiences and to implement—continuously and in real time—far-reaching actions based on experience and data. To meet typical integration requirements, SAP Integration Suite enables processes and data to be connected and contextualized, while new applications can be created more quickly and with less dependency on IT. With SAP Integration Suite, however, SAP has unfortunately also caused a lot of confusion. As a suite capability, SAP Integration Suite is a collection of several services, as shown in [Figure 1.6](#01_001.html#f1.6). Services offered include Event Mesh, Master Data Integration, and SAP Data Intelligence.

[![SAP Integration Suite](bilderklein/klein01_006.png)](img-f1.6.html) 

**Figure 1.6**     SAP Integration Suite

To add to the confusion, note the service called Integration Suite. What exactly is the purpose of this product? In the area of integration, SAP introduced a product called SAP HANA Cloud Integration as one of the first services on the predecessors of SAP BTP. This product is middleware that is, so to speak, SAP BTP's counterpart to SAP Process Orchestration. Also, another service called SAP API Management was added, and later Open Connectors and the Integration Advisor were added. All these products are “integration solutions” in the broadest sense of the term. But each service is offered with its own license model. In addition, these services use different metrics for licensing. As a result, SAP HANA Cloud Integration, now called the Cloud Integration capability, was mostly licensed without the other components. Therefore, from a marketing perspective, SAP has taken an interesting route. A product called SAP Integration Suite was introduced. Functionally, however, this product is not a separate product at all, at least not now. It merely provides a central entry point to enable the activation of the services mentioned earlier. Furthermore, the product is equipped with a uniform license. As a result, as a customer, if you’ve licensed SAP Integration Suite, you can also use SAP API Management, Open Connectors, and the Integration Advisor as well as Trading Partner Management (TPM), which was introduced in 2022, in addition to Cloud Integration. Cloud Integration is a flagship product of SAP BTP and thus also of SAP Integration Suite, seamlessly integrated with all other components of the suite.

The Cloud Integration capability uses the Apache Camel engine as its technological basis. This solution allows synchronous and asynchronous communication and supports a wide range of protocols and technologies. These protocols include, for example, Hypertext Transfer Protocol Secure (HTTPS), Simple Object Access Protocol (SOAP), Java Database Connectivity (JDBC), Representational State Transfer (REST), Java Message Service (JMS), and SSH File Transfer Protocol or Secure File Transfer Protocol (SFTP). There are also several adapters for connecting SaaS solutions such as SAP SuccessFactors and SAP Ariba. Cloud Integration is suitable for implementing application-to-application (A2A), business-to-business (B2B), and business-to-governance (B2G) integration scenarios.

Cloud Integration also enables you to use prepackaged content, which refers to integrations created by SAP or its partners for different scenarios. The advantage of using prepackaged content is that you have ready-made integration solutions in which all aspects of integration between specific systems are already fully mapped. To use this content, typically you’ll only need to configure the connectivity on the sender and receiver sides of your specific systems. An example of prepackaged content for SAP SuccessFactors is shown in [Figure 1.7](#01_001.html#f1.7). Prepackaged content can be found at SAP API Business Hub at [http://s-prs.co/v562704](http://s-prs.co/v562704).

###### \[eg\]  Data Transmission to Tax Authorities

A clear example of such prepackaged content are eDocuments. Many countries have legal requirements for companies to transmit certain data from B2B transactions to tax authorities within a defined period. To implement these interfaces yourself, you must first determine and provide the right data from your involved SAP systems, typically SAP Business Suite or SAP S/4HANA. In the next step, you must analyze the interfaces of the financial authority and bring data from your SAP system into the required format via a mapping. After that step, you must encrypt and sign the data sent. Finally, authentication and technical connectivity to the tax authority must be set up, and of course, adequate error handling should not be forgotten either. Finally, the processing status from the tax authority should also be noted in the SAP system.

The implementation effort for fulfilling these requirements is usually in the double-digit range of man-days. For a multinational corporation that must implement this requirement in ten or more countries, development and integration teams will be kept busy for a long time with this implementation, which of course, is not desirable. Therefore, SAP delivers ready-made content for these scenarios in the form of integration flows (iFlows) that cover all aspects of integration. In an SAP on-premise landscape, you would install a suitable add-on for this purpose to integrate with financial accounting. You would only be responsible for configuring the connectivity and for ongoing monitoring of the interfaces, which massively reduces the overall implementation effort. If something changes in the interfaces provided by the authorities, SAP updates the affected iFlows, and you can switch directly to the latest version in the Cloud Integration capability.

[![SAP API Business Hub: SAP SuccessFactors Integrations](bilderklein/klein01_007.png)](img-f1.7.html) 

**Figure 1.7**     SAP API Business Hub: SAP SuccessFactors Integrations

## 1.2    Environments

Initially, SAP BTP operated exclusively in SAP’s own data centers and in its proprietary Neo environment. Parallel to SAP, other cloud providers have established themselves on the market with their own offerings, such as Amazon with AWS, Microsoft with Microsoft Azure, Google with Google Cloud Platform, and Alibaba with Alibaba Cloud. To standardize the operation and provision of services in the cloud across all providers, well-known cloud providers have come together under the banner of the Cloud Foundry Foundation to define a uniform standard (see [https://www.cloudfoundry.org/](https://www.cloudfoundry.org/)). SAP BTP, Cloud Foundry environment, including SAP BTP, Kyma environment to be activated in it, is based on this standard.

SAP relies on the Cloud Foundry architecture not only in SAP BTP, but also in other products. These products include, for example, SAP HANA extended application services, advanced model (SAP HANA XSA), which is the runtime and development environment integrated in SAP HANA.

The platform offers a wide range of functions that include various technical components such as services, tools, APIs, and applications. Within SAP BTP, SAP makes it optional for you to choose whether you want to use services in SAP BTP, Cloud Foundry environment or continue to use them in SAP BTP, Neo environment. In either environment, the services enable, facilitate, or accelerate the development of business applications and other platform services on SAP BTP. However, new customers will only be able to work with SAP BTP, Cloud Foundry environment or SAP BTP, Kyma environment.

In a nutshell, two types of services are available with SAP BTP:

*   Business services   
    Business services are services that enable, facilitate, or accelerate the development of business process components or that provide industry-specific functionality or content within a business application.
    
*   Technical services   
    Technical services are services that enable, facilitate, or accelerate the development of generic or domain-independent content within a business application, independent of the application’s business process or task.
    

###### \[+\]  Available Services

SAP does not offer all services in all regions and environments. Some services are only offered in SAP BTP, Neo environment, and others are only offered in SAP BTP, Cloud Foundry environment. Further, a large number are offered in both environments. An overview of the available services can be found at SAP Discovery Center, which is located at [https://discovery-center.cloud.sap/](https://discovery-center.cloud.sap/).

In both environments, SAP offers the SAP Custom Domain service. This service enables subaccount holders (see [Section 1.3.2](#01_003.html#h1.3.2)) to make the SAP BTP applications they use accessible via a user-defined domain (custom domain). This domain is different from the default domain (hana.ondemand.com) and can be, for example, cloud.mycompany.com. A custom domain must be licensed and configured per subaccount. The configuration is performed via the command line in SAP BTP, Neo environment or also using the SAP BTP cockpit, which we’ll describe in detail in [Chapter 6](#06_001.html#h6), [Section 6.5.1](#06_005.html#h6.5.1).

### 1.2.1    SAP BTP, Neo Environment

SAP BTP, Neo environment is an enterprise-level PaaS offering from SAP that provides comprehensive application development services and capabilities. With these services, you can build, extend, and integrate business applications in the cloud. SAP BTP, Neo environment is not a standalone product that can be licensed but instead is a collection of different solutions deployed in SAP-owned data centers. [Figure 1.8](#01_002.html#f1.8) provides an overview of all data centers where SAP BTP, Neo environment operates.

[![SAP BTP, Neo Environment: Data Center Locations](bilderklein/klein01_008.png)](img-f1.8.html) 

**Figure 1.8**     SAP BTP, Neo Environment: Data Center Locations

With SAP BTP, Neo environment, you can develop and deploy custom applications in HTML5 and Java that are based on SAP HANA extended application services (SAP HANA XS). Furthermore, you can use the SAP user interface (UI) development toolkit for HTML5 (SAPUI5) to develop state-of-the-art UIs for web-based business applications.

SAP BTP, Neo environment also enables the deployment of solutions on SAP BTP. In the context of SAP BTP, a solution consists of different application types and configurations built with different technologies to implement a specific scenario or task flow. Solutions can be deployed through the enhanced Change and Transport System (CTS+), the console client, or the SAP BTP cockpit. The SAP BTP cockpit is also used for monitoring solutions.

The multitarget application (MTA) model used in SAP BTP, Neo environment encompasses and describes application modules, dependencies, and interfaces in an approach that facilitates the validation, orchestration, maintenance, and automation of applications throughout their lifecycles.

In addition to ability to develop your own applications, SAP BTP, Neo environment offers a variety of services for implementing other scenarios common in SAP environments. These services include a few we would like to introduce to you briefly:

*   SAP Web IDE  
    SAP Web IDE is the integrated development environment (IDE) in SAP BTP, Neo environment. For many developers, SAP Web IDE is their main point of contact with SAP BTP, for instance, for the development and extension of SAP Fiori apps. Additionally, SAP Web IDE can be used to develop IoT applications, workflows, and certain other types of mobile apps. SAP Web IDE can be extended by self-developed plug-ins or using plug-ins from third-party providers.
    
*   Cloud Integration  
    As introduced in [Section 1.1.2](#01_001.html#h1.1.2), Cloud Integration is the central service for integrating different SaaS solutions or for integrating SaaS solutions with on-premise systems. For numerous integration scenarios, predefined content has been provided by SAP and by its partners for immediate use.  
    The Cloud Integration capability is offered in both SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. For information on the restrictions that currently exist in SAP BTP, Cloud Foundry environment, see SAP Note 2752867.
    
*   SAP Mobile Services  
    SAP Mobile Services are used when mobile apps are created in the SAP context and secure access to data in on-premise and SaaS applications is required. Native, hybrid, and metadata-driven apps can be created. Additionally, push notifications and offline functionalities are provided by default. The only differences in the two environments in this context relate to user authentication.
    
*   SAP Cloud Portal service and SAP Launchpad service  
    A typical use case for the SAP Cloud Portal service is to create end customer portals. It is only available in SAP BTP, Neo environment. With the SAP Launchpad service, you can provide employees and end customers with access to certain functionalities in the cloud via catalogs and tiles in the SAP Fiori launchpad. For example, you can provide branches to employee services, evaluations, or time-booking functions through these services. The advantage of using these cloud services is that the backend systems involved don’t need to be directly accessible from the Internet. In this way, SAP BTP provides an additional security layer that takes care of denial of service (DoS) attacks, malware detection, and virus scans, for example.
    
*   SAP Translation Hub  
    SAP Translation Hub helps you translate SAP Fiori apps and mobile apps into different languages in a largely automated way. In addition to SAP’s own multilingual text repository (MLRT), you can use your own repositories and thus provide domain-specific translations or additional languages.
    

If a requirement is not covered by the standard services offered, SAP enables the use of virtual machines in SAP BTP, Neo environment. This option allows you to install and run your own applications. We cover securing SAP BTP, Neo environment in detail in [Chapter 3](#03_001.html#h3).

### 1.2.2    SAP BTP, Cloud Foundry Environment

A nonprofit, open-source project, the Cloud Foundry Foundation aims to become the world’s leading application platform for cloud computing. The Cloud Foundry Foundation drives awareness and encourages the adoption of the Cloud Foundry open-source project by creating a vibrant community of contributing companies. Specifically, the Cloud Foundry Foundation has the following goals:

*   Establishing and sustaining Cloud Foundry as a global industry standard for PaaS open-source technologies in a thriving ecosystem
    
*   Maintaining and ensuring quality, value, and innovation for user companies, operators, and providers of the technology
    
*   Ensuring a vibrant, agile experience for community contributors for delivering the highest-quality cloud-native applications globally at speed
    

SAP BTP, Cloud Foundry environment enables you to develop and operate cloud-based applications in different programming languages. SAP BTP, Cloud Foundry environment applications can be deployed in different regions. Each region constitutes the location of a separate data center.

###### \[»\]  Current Information about the Supported Regions

Since new data centers are being added all the time, we recommend looking at the Regions and Service Portfolio section of the official documentation for SAP BTP. In the documentation, you’ll see references to SAP Discovery Center, which offers an interactive map of the available regions at [https://discovery-center.cloud.sap/](https://discovery-center.cloud.sap/).

SAP BTP, Cloud Foundry environment also integrates with SAP HANA XSA. This successor to SAP HANA XS was introduced with SAP HANA 1.0 support package stack (SPS) 10. The runtime of SAP BTP, Cloud Foundry environment is based on the open-source application platform managed by the Cloud Foundry Foundation. Your company and its development teams can use a variety of buildpacks with SAP BTP, Cloud Foundry environment. With a buildpack, you can compile applications of a certain type and package them as a bundle (typically as an archive).

The following buildpacks are officially supported by SAP in both SAP BTP, Cloud Foundry environment and SAP HANA XSA:

*   sap\_java\_buildpack
    
*   sap\_nodejs\_buildpack
    
*   sap\_python\_buildpack
    

In addition to the buildpacks provided by SAP, community buildpacks (i.e., provided by the developer community) are also available.

An overview of the available buildpacks can be found in the official Cloud Foundry documentation at [https://docs.cloudfoundry.org/buildpacks/](https://docs.cloudfoundry.org/buildpacks/). Note that no community buildpacks are allowed in SAP HANA XSA. However, the following community buildpacks can be used in SAP BTP, Cloud Foundry environment:

*   binary\_buildpack
    
*   dotnet\_core\_buildpack
    
*   go\_buildpack
    
*   java\_buildpack
    
*   nodejs\_buildpack
    
*   php\_buildpack
    
*   python\_buildpack
    
*   ruby\_buildpack
    
*   staticfile\_buildpack
    

In addition, you can create your own customer-specific buildpacks. By using buildpacks, almost all use cases can be mapped in SAP BTP, Cloud Foundry environment. One advantage is that you can rely on buildpacks, for which expertise should already be available in your company.

#### Services and Subscriptions

Buildpacks are used whenever custom applications are created. In addition, SAP also offers a variety of directly usable standard services and application subscriptions in SAP BTP, Cloud Foundry environment that cover specific use cases, such as the following:

*   SAP Business Application Studio  
    SAP Business Application Studio is SAP BTP, Cloud Foundry environment’s counterpart to SAP Web IDE in SAP BTP, Neo environment. This solution is based on the Eclipse Theia IDE and is used, for example, to create and extend SAP Fiori apps. Especially when developing and extending apps based on SAP Fiori elements, SAP Business Application Studio offers several advantages over SAP Web IDE. Using SAP Fiori elements is an accelerated way to develop SAP Fiori apps via building blocks and templates.  
    Like SAP Web IDE, SAP Business Application Studio can be extended by self-developed plug-ins or by plug-ins from third-party vendors. However, no compatibility exists between plug-ins for SAP Web IDE and those for SAP Business Application Studio. If you’ve developed your own plug-ins for SAP Web IDE, a new development project for SAP Business Application Studio is required when you switch.
    
*   Cloud Integration   
    The Cloud Integration service has a similar feature set in SAP BTP, Cloud Foundry environment as in SAP BTP, Neo environment. However, certain limitations exist, which are listed in SAP Note 2752867.
    
*   SAP Mobile Services   
    SAP Mobile Services have the same range of functions in SAP BTP, Cloud Foundry environment as in SAP BTP, Neo environment, but some deviations in the area of security exist. For example, certificate-based authentication and a secure logon server cannot be used in SAP BTP, Cloud Foundry environment. SAP Help Portal at [http://s-prs.co/v562703](http://s-prs.co/v562703) contains a section on migrating existing solutions from SAP BTP, Neo environment to SAP BTP, Cloud Foundry environment.
    
*   SAP Launchpad service   
    The SAP Launchpad service provides access to an SAP Fiori launchpad. This service allows you to provide role-based access to applications and data from SAP systems. The SAP Fiori launchpad uses the SAP Fiori design concepts familiar from the on-premise world. In [Chapter 4](#04_001.html#h4), [Section 4.6.1](#04_006.html#h4.6.1), we’ll look at this service from a security perspective.
    
*   SAP API Management   
    With SAP API Management, APIs can be published, marketed, and monitored during operations in a secure and scalable environment. In the context of a typical system landscape, SAP API Management can be used with any of the many SAP-developed API providers such as SAP Gateway, SAP BTP, or SAP SuccessFactors. SAP API Management protects investments in SAP solutions and can integrate non-SAP solutions as well as SAP solutions. This tool plays a key role in unlocking the value of digital assets by organizing and clearly presenting the available APIs and also enables content creation and delivery. SAP API Management enables applications to run seamlessly by providing secure access to backend data. It also enables management, monitoring, and real-time analysis of APIs across multiple data platforms.
    

###### \[»\]  Deprecation of SAP Internet of Things

SAP Internet of Things and its predecessor services were retired effective July 15th, 2022. During the retirement phase, SAP will continue to provide the service at the current service level until the end of the contract term. SAP does not intend to renew the entitlement or the contract. SAP will continue fixing bugs and applying required security fixes; however, SAP will not add any new capabilities.

In SAP BTP, Cloud Foundry environment services are provided via SAP’s infrastructure as a service (IaaS) partners:

*   Amazon with AWS
    
*   Microsoft with Microsoft Azure
    
*   Google with Google Cloud Platform
    
*   Alibaba with Alibaba Cloud
    

IaaS partners operate on the infrastructure layer of the relevant regions, while SAP operates the platform layer and SAP BTP, Cloud Foundry environment, which is a certified Cloud Foundry distribution. As a customer, you’ll only have access to the platform layer, not to the infrastructure layer.

We’ve dedicated a separate chapter to securing SAP BTP, Cloud Foundry environment ([Chapter 4](#04_001.html#h4)) to explore its significant differences with SAP BTP, Neo environment and its many new features.

### 1.2.3    Environment Selection

From a commercial perspective, whether you use a service in SAP BTP, Neo environment or in SAP BTP, Cloud Foundry environment or both doesn’t matter much. In all these cases, you’ll conclude a contract with SAP, not with the IaaS provider. Therefore, billing always takes place via SAP.

In this section, we’ll compare and contrast the two SAP BTP environments by highlighting their similarities and differences with respect to several topics:

*   Data centers   
    SAP BTP, Neo environment runs in SAP data centers. In contrast, SAP BTP, Cloud Foundry environment runs through external cloud providers.
    
*   Available services   
    In both environments, services are limited by the regions in which they are offered and by the platform itself. For an overview of services and regions, refer to SAP Discovery Center at [https://discovery-center.cloud.sap/](https://discovery-center.cloud.sap/).
    

###### \[eg\]  Services That Are Only Offered in One Environment

For example, SAP Integration Suite exists only in SAP BTP, Cloud Foundry environment, and the SAP Git service is offered only in SAP BTP, Neo environment.

*   Command line   
    For both environments, an environment-specific command line can be used for managing your subaccounts. In addition, an overarching command-line tool is used at the global accounts level (see also [Section 1.3.1](#01_003.html#h1.3.1) and [Chapter 6](#06_001.html#h6)).
    
*   Development tools   
    In SAP BTP, Neo environment, you would use SAP Web IDE, and in SAP BTP, Cloud Foundry environment, you would use SAP Business Application Studio.
    
*   Types of applications   
    In SAP BTP, Neo environment, classic Java applications and SAP Fiori applications can be developed and operated. In SAP BTP, Cloud Foundry environment, applications can also be developed in any other programming language via buildpacks (provided a buildpack is available for that language).
    
*   Users  
    Users can be connected via a local directory, but in SAP BTP, Neo environment, connections can also occur via the SAP ID service, which is based on the S-users and P-users assigned by SAP. In SAP BTP, Cloud Foundry environment, you can register accounts based on any email address.
    
*   Hybrid landscapes   
    Combining different services and subscriptions with on-premise solutions creates a hybrid landscape. If you use the Identity Authentication service for an application in SAP BTP, Cloud Foundry environment, you can use a service in SAP BTP, Neo environment for authentication.
    

## 1.3    Architecture

[Figure 1.9](#01_003.html#f1.9) shows the account model in SAP BTP. A global account can be assigned several subaccounts in the various regions and environments of SAP BTP.

[![SAP BTP: Account Architecture](bilderklein/klein01_009.png)](img-f1.9.html) 

**Figure 1.9**     SAP BTP: Account Architecture

In this section, we’ll focus on the administration of business users and roles within global accounts. The administration of global accounts and subaccounts beyond these security-specific topics will only be covered briefly.

As an SAP customer, you can choose between two commercial models for using SAP BTP:

*   In the subscription-based model, you get access to the selected services for a fixed price over a specific, predefined period of time. This model offers less flexibility and is characterized by the following features:
    
    *   Only the subscribed services may be used.
        
    *   To use additional services or different services, the contract must be modified accordingly.
        
    *   Regardless of the actual usage, the agreed price will be charged.
        
    *   Services will be billed in advance, at the beginning of the billing period.
        
    *   You can renew the subscription at the end of the contract period.
        
*   The usage-based model offers greater flexibility compared to the subscription-based model. This model is characterized by the following features:
    
    *   The services used do not need to be subscribed to in advance.
        
    *   All eligible services, current and future, are available for unrestricted use throughout the contract term.
        
    *   You only must pay for the actual use of the services.
        
    *   There is no minimum usage level (e.g., 1,000 users).
        
    *   New services can be consumed at any time without changing the contract.
        

To use the usage-based model, you must sign either a Cloud Platform Enterprise Agreement (CPEA) or a pay-as-you-go contract for SAP BTP. In the latter approach, you can either purchase cloud credits in advance or commit to paying according to usage.

### 1.3.1    Global Accounts

As soon as you license SAP BTP services, you’re assigned a global account. The basic idea behind this account is that each customer is assigned exactly one global account. However, in practice, a customer can also be assigned to more than one global account. This scenario occurs, for example, when these customers purchase an SAP Integration Suite service as an extension to an SAP SaaS product such as SAP SuccessFactors. If you purchase certain services under the subscription model and purchase others via a CPEA, you’ll also be assigned two global accounts.

User authentication at the global account level is performed exclusively via the SAP ID service. As a customer, you typically log on with an S-user, your user ID for the global account. The SAP ID service is SAP’s public identity provider. When your global account is provisioned, it is assigned exactly one S-user for administration, which you’ll receive in a welcome email. This user plays an important role as the only user that initially has access to the SAP BTP Identity Authentication service. The S-user is initially set as the owner of the administrator role for the global account.

#### Logging on to the Global Account

Your global account is accessed via [https://hana.ondemand.com/](https://hana.ondemand.com/). After your user has been successfully authenticated, you’ll see an overview of all global accounts to which your user is assigned. Our example shown in [Figure 1.10](#01_003.html#f1.10) displays an overview for a user assigned to two global accounts.

[![SAP BTP: Global Account Overview](bilderklein/klein01_010.png)](img-f1.10.html) 

**Figure 1.10**     SAP BTP: Global Account Overview

A tile is displayed for each global account that displays the number of associated subaccounts and the number of regions in which subaccounts are provided. Furthermore, an indicator shows if you’re using feature set B, the most recent feature set for SAP BTP, Cloud Foundry environment (see [Chapter 4](#04_001.html#h4)). For example, our global account CloudDNA GmbH, shown in [Figure 1.10](#01_003.html#f1.10), has been assigned 11 subaccounts in two regions. One global account is using feature set A while the other uses feature set B.

Global accounts are independent of the geographical region, that is, independent of the data centers in which the services are operated. Global accounts are used to administer subaccounts, members, entitlements, and quotas. At the global account level, entitlements are assigned to you for free use. Thus, you’re provided with licensed resources. Quotas are the scope limits within which the licensed resources may be used, for example, the maximum amount of memory that can be allocated to fulfilling your requirements. Global accounts are provided exclusively by SAP and cannot be created by customers themselves.

#### Entitlements

You cannot activate services directly in the global account, only at the level of a subaccount. Think of entitlements as a resource pool that includes all the services that you’re authorized to use based on your license. Individual subaccounts are served from this pool. Entitlements are divided into Subaccount Assignments and Service Assignments, as shown in [Figure 1.11](#01_003.html#f1.11).

[![SAP BTP: Entitlements](bilderklein/klein01_011.png)](img-f1.11.html) 

**Figure 1.11**     SAP BTP: Entitlements

By navigating to Entitlements • Service Assignments in the SAP BTP cockpit, you’ll see an overview of all the resources licensed and assigned to your global account, as shown in [Figure 1.12](#01_003.html#f1.12).

[![SAP BTP: Service Assignment](bilderklein/klein01_012.png)](img-f1.12.html) 

**Figure 1.12**     SAP BTP: Service Assignment

By selecting Subaccount Assignments in the SAP BTP cockpit, you’ll see an overview of assigned resources on the subaccount level. You can assign resources to a subaccount by clicking the Configure Entitlements button, as shown in [Figure 1.13](#01_003.html#f1.13).

[![SAP BTP: Subaccount Assignment](bilderklein/klein01_013.png)](img-f1.13.html) 

**Figure 1.13**     SAP BTP: Subaccount Assignment

#### Global Account Administration

A dedicated global account is assigned to you for each license type. At least one administrator must be assigned at the global account level. This assignment is performed initially by SAP while provisioning the global account. Users with the administrator role are responsible for the following activities at the global account level:

*   Management of subaccounts
    
*   Management of members at the global account level
    
*   Management of entitlements
    

SAP recommends assigning at least two administrators per global account. This redundancy ensures that the required activities can be performed even if an administrator leaves the company or is not available at short notice. At the global account level, users are always authenticated via the SAP ID service and thus typically with their personal S-users.

###### \[»\]  Permissions of the Global Account Administrator

The administrator of the global account is not automatically authorized to manage all subaccounts, only the subaccounts created by that administrator.

Some differences in user management at the global account level exist between feature set A and feature set B. In global accounts that are still provided with feature set A, no role concept is in play; only administrators exist, as shown in [Figure 1.14](#01_003.html#f1.14).

[![Global Account Member Administration, Feature Set A](bilderklein/klein01_014.png)](img-f1.14.html) 

**Figure 1.14**     Global Account Member Administration, Feature Set A

In global accounts that have already been converted to feature set B, a role concept is active. In this approach, several roles are available, and two collections aggregating these roles are delivered by SAP as standard. [Figure 1.15](#01_003.html#f1.15) shows the two standard role collections, Global Account Administrator and Global Account Viewer.

[![Global Account Role Collections](bilderklein/klein01_015.png)](img-f1.15.html) 

**Figure 1.15**     Global Account Role Collections

As shown in [Figure 1.16](#01_003.html#f1.16), the management of the global account users is different than in feature set A. You can immediately see when a user was last logged on, for instance.

[![Global Account Member Administration, Feature Set B (User Management)](bilderklein/klein01_016.png)](img-f1.16.html) 

**Figure 1.16**     Global Account Member Administration, Feature Set B (User Management)

You can navigate to a user’s details by clicking on the user from the overview page. In the user detail screen, you can assign role collections by clicking on the Assign Role Collection button, as shown in [Figure 1.17](#01_003.html#f1.17).

[![User Details with Role Collection Assignment](bilderklein/klein01_017.png)](img-f1.17.html) 

**Figure 1.17**     User Details with Role Collection Assignment

Currently, ten roles are available that you can use to create your own custom roles, as shown in [Figure 1.18](#01_003.html#f1.18). With the introduction of role collections on the global account level, SAP has enabled a lot more flexibility in managing users. Keep in mind, however, that there is usually no need for users on the global account besides administrators and auditors.

[![SAP BTP: Global Account Custom Role Collection](bilderklein/klein01_018.png)](img-f1.18.html) 

**Figure 1.18**     SAP BTP: Global Account Custom Role Collection

###### \[+\]  Permissions of the Global Account Administrator

The administrator of the global account is not automatically authorized to manage all subaccounts, only the subaccounts that he or she creates.

### 1.3.2    Subaccounts

Subaccounts allow you to structure a global account according to your needs and the organization of your projects. This structuring involves the management of members, their permissions, and their entitlements.

Each subaccount must be created within a region and a data center. The region reflects the physical location of the data center where applications, data, and services are hosted. This region does not have to be the same as the region of your enterprise location.

Subaccounts structured under a global account are independent of each other, which is important to remember when planning the overall architecture in terms of security, member management, data management, data migration, and integration. In the SAP BTP cockpit, all subaccounts assigned to your global account using feature set A are displayed under the Subaccounts menu item, as shown in [Figure 1.19](#01_003.html#f1.19). If more than 100 subaccounts have been assigned to a global account, you’ll need to use filters to find the right ones.

[![Global Account Member Administration, Feature Set A (Subaccount Overview)](bilderklein/klein01_019.png)](img-f1.19.html) 

**Figure 1.19**     Global Account Member Administration, Feature Set A (Subaccount Overview)

With feature set B, SAP has introduced directories, which can be quite useful for structuring your subaccounts. Hierarchies can be mapped with directories, as shown in [Figure 1.20](#01_003.html#f1.20).

###### \[+\]  Choose a Useful Subaccount Structure

At the subaccount level, you can configure system connections, among other things. Separate subaccounts for production systems and for development systems are recommended, if only to separate resources and system connections. Furthermore, you can create additional security by separating them according to the backends used (e.g., SAP ERP) or according to responsible teams.

[![Global Account Member Administration, Feature Set B (Subaccount Overview)](bilderklein/klein01_020.png)](img-f1.20.html) 

**Figure 1.20**     Global Account Member Administration, Feature Set B (Subaccount Overview)

Unlike global accounts, you can create subaccounts yourself by following these steps:

1.  Click on the New Subaccount button in the subaccount overview screen.
    
2.  The dialog box for creating the subaccount allows you to select a provider. If you select the Neo Environment checkbox, SAP is set as in the Provider field, since SAP BTP, Neo environment is provided exclusively in SAP data centers, as shown in [Figure 1.21](#01_003.html#f1.21).
    
3.  Next, select the Region from all available data centers for SAP BTP, Neo environment.
    
4.  If you select the Used for production checkbox, you won’t see a direct effect on your subaccount, but this selection will help SAP prioritize support tickets for your production subaccounts.
    
    [![SAP BTP, Neo Environment: New Subaccount Dialog Box](bilderklein/klein01_021.png)](img-f1.21.html) 
    
    **Figure 1.21**     SAP BTP, Neo Environment: New Subaccount Dialog Box
    

Creating a subaccount in SAP BTP, Cloud Foundry environment is performed in the same dialog box, but in this case, do not select the Neo Environment checkbox. When creating a subaccount in SAP BTP, Cloud Foundry environment, you should note two significant differences compared to SAP BTP, Neo environment. First, a mandatory step is selecting a provider. The following providers can be selected:

*   AWS
    
*   Google Cloud Platform
    
*   Microsoft Azure
    

For the Region field, you would choose among the regions operated by the provider.

###### \[+\]  Choosing Alibaba Cloud as Your Provider

Alibaba Cloud cannot be selected as a provider at the time of writing. If you would like to use Alibaba Cloud, you must contact your responsible SAP sales manager.

Second, a subdomain must be defined using a unique resource identifier (URI). The following rules must be observed for this task:

*   The subdomain name must contain letters, numbers, and hyphens only.
    
*   Hyphens may not be used at the beginning or end of a subdomain name.
    
*   The subdomain must be unique across all subaccounts in the selected region across all customers. Therefore, if another customer is already using the subdomain you want, you must choose a different subdomain.
    
*   Uppercase and lowercase letters are allowed, and case does not affect the name match.
    

[Figure 1.22](#01_003.html#f1.22) shows the dialog box for creating a subaccount in SAP BTP, Cloud Foundry environment.

[![SAP BTP, Cloud Foundry Environment: New Subaccount Dialog Box](bilderklein/klein01_022.png)](img-f1.22.html) 

**Figure 1.22**     SAP BTP, Cloud Foundry Environment: New Subaccount Dialog Box

###### \[+\]  Checking the Availability of Services and Resources

Since not all services are available in all environments and regions, we recommend checking in advance, in the documentation for SAP BTP, whether the desired services are available from your preferred provider in your desired region. SAP Discovery Center lists all cloud services and their geographical availability. When activating services in SAP BTP, you’ll see in which data centers a service is offered, as shown in [Figure 1.23](#01_003.html#f1.23).

[![SAP BTP: Regional Service Availability](bilderklein/kleinbtp_service_availability.png)](img-f1.23.html) 

**Figure 1.23**     SAP BTP: Regional Service Availability

### 1.3.3    Organizations

Organizations exist in SAP BTP, Cloud Foundry environment only. In SAP BTP, Neo environment, you’ll work directly in the subaccount without any further sublevels. In SAP BTP, Cloud Foundry environment, to fully use the subaccount, an organization must be created. Open the subaccount and click the Enable Cloud Foundry button to enable SAP BTP, Cloud Foundry environment features. [Figure 1.24](#01_003.html#f1.24) shows the overview of an initial SAP BTP, Cloud Foundry environment subaccount.

[![SAP BTP, Cloud Foundry Environment: Subaccount Details](bilderklein/klein01_023.png)](img-f1.24.html) 

**Figure 1.24**     SAP BTP, Cloud Foundry Environment: Subaccount Details

When activating a subaccount, you must specify the name of the organization. SAP BTP suggests a name at this point, but you can override this suggestion, as shown in [Figure 1.25](#01_003.html#f1.25). The suggested name consists of the name of the global account and the name of the subaccount, separated by an underscore.

[![SAP BTP, Cloud Foundry Environment: Creating an Organization](bilderklein/klein01_024.png)](img-f1.25.html) 

**Figure 1.25**     SAP BTP, Cloud Foundry Environment: Creating an Organization

After the organization is created, you’ll see the organization’s details, as shown in [Figure 1.26](#01_003.html#f1.26). These details include the Org ID field that you’ll need for setting up the cloud connector and the API Endpoint field that will be required in the Cloud Foundry console.

[![SAP BTP, Cloud Foundry Environment: Organization Details](bilderklein/klein01_025.png)](img-f1.26.html) 

**Figure 1.26**     SAP BTP, Cloud Foundry Environment: Organization Details

You can add members to an organization, which we’ll discuss in more detail in [Chapter 3](#03_001.html#h3), [Section 3.2](#03_002.html#h3.2).

You can also delete organizations. For this task, your user must be assigned the global account administrator role, and you must also be assigned as a member to the subaccount whose organization you want to delete. To delete an organization, click the Disable Cloud Foundry button on the SAP BTP, Cloud Foundry environment subaccount overview screen, as shown in [Figure 1.27](#01_003.html#f1.27).

###### \[ ! \]  Deleting Subaccounts

Deleting a subaccount causes all data and configurations stored in it to be irrevocably and permanently deleted.

[![SAP BTP, Cloud Foundry Environment: Disabling an Organization](bilderklein/klein01_026.png)](img-f1.27.html) 

**Figure 1.27**     SAP BTP, Cloud Foundry Environment: Disabling an Organization

### 1.3.4    Spaces

Like organizations, spaces are available in SAP BTP, Cloud Foundry environment only. Spaces can be used to subdivide developments (e.g., into a development space and a quality assurance space). A prerequisite for creating a space is a user who has the organization manager role in the organization subaccount. Creating a space is performed via the SAP BTP cockpit by clicking on the Create Space button in the Spaces section, as shown in [Figure 1.28](#01_003.html#f1.28).

[![SAP BTP, Cloud Foundry Environment: Creating a Space](bilderklein/klein01_027.png)](img-f1.28.html) 

**Figure 1.28**     SAP BTP, Cloud Foundry Environment: Creating a Space

After creation, no quotas are initially assigned to a space, as shown in [Figure 1.29](#01_003.html#f1.29).

[![SAP BTP, Cloud Foundry Environment: Space Quota](bilderklein/klein01_028.png)](img-f1.29.html) 

**Figure 1.29**     SAP BTP, Cloud Foundry Environment: Space Quota

Quotas are not assigned to a space directly. Instead, you’ll assign quotas indirectly by first creating a quota plan and then assigning the quotas to it. A quota plan determines how resources may be distributed to quotas. The plan is then assigned to a space. For this task, make a selection from the dropdown list in the Quota Plan dropdown list, as shown in [Figure 1.30](#01_003.html#f1.30).

[![SAP BTP, Cloud Foundry Environment: Quota Plan Assignment](bilderklein/klein01_029.png)](img-f1.30.html) 

**Figure 1.30**     SAP BTP, Cloud Foundry Environment: Quota Plan Assignment

###### \[+\]  Best Practices for Organizing Spaces

A space is effectively a separate area for development or for different versions of a cloud application. In practice, therefore, a separate space should exist for each application status (development, test, production, and operation). However, as a best practice—also to simplify system connections—a subaccount called PROD with a space for production operations and a subaccount called DEV with a space for development and a space for testing are common. This structure should be set up for each application or for each team.

You can also delete a space if the space is no longer needed. For this task, you must be assigned the organization manager role. In the overview of your spaces, click the Delete icon on the space’s tile, as shown in [Figure 1.31](#01_003.html#f1.31).

[![SAP BTP, Cloud Foundry Environment: Deleting a Space](bilderklein/klein01_030.png)](img-f1.31.html) 

**Figure 1.31**     SAP BTP, Cloud Foundry Environment: Deleting a Space

## 1.4    Summary

In this chapter, we took our first steps with SAP BTP. We covered the fundamental positioning of the solution, including its two key suites: SAP Extension Suite and SAP Integration Suite. We then explored SAP BTP, Neo environment and SAP BTP, Cloud Foundry environments, and described how to choose between them. Finally, we discussed SAP BTP’s architecture, including the creation and management of global accounts, subaccounts, organizations, and spaces.

# 2    SAP Business Technology Platform Security at a Glance

Security starts with the selection of secure data transmission technologies and continues with the identification of users through to the assignment of rights. The maintenance and configuration of user management should not be independent of your company’s own infrastructure. Users should also be able to log on to the cloud with the usual authorizations, and if a user is no longer valid, cloud applications and services should also be aware of this change. Integration at the technical level is therefore a prerequisite for the seamless integration of applications at the business level.

This chapter introduces the security mechanisms found in SAP Business Technology Platform (SAP BTP), starting in [Section 2.1](#02_001.html#h2.1) with secure communication. We’ll then dive into the various authentication and authorization options in [Section 2.2](#02_002.html#h2.2) and [Section 2.3](#02_003.html#h2.3). In this process, we’ll explain the differences between SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. In [Section 2.4](#02_004.html#h2.4), you’ll learn how to manage users as identities through SAP Cloud Identity Services and ensure users have the correct authorizations. We’ll also cover the System for Cross-Domain Identity Management (SCIM) protocol used when managing users and identities in distributed architectures. Finally, in [Section 2.5](#02_005.html#h2.5), we’ll present the governance features to help you discover and migrate critical permissions. In [Section 2.6](#02_006.html#h2.6), you’ll find a checklist for assessing your basic security in SAP BTP.

## 2.1    Secure Communication

Security is vital in communications between cloud systems and between cloud and on-premise systems. On one hand, trust is required in the security on the user side, and on the other hand, you must ensure that data on the communication path cannot be read or manipulated by third parties.

Especially in the consumer sector, in the past, secure communication was rarely the focus of attention. This lack of focus was mainly because secure communication is associated with additional costs on the part of the provider and requires corresponding knowledge. For some time now, however, Google has given preferential treatment in its search results to secure websites. Thus, a rethinking has taken place among service providers in this regard.

In business applications, secure communication is essential and has not been debatable for decades. When securing communications, several concepts like Secure Sockets Layer (SSL), Transport Layer Security (TLS), and Hypertext Transfer Protocol Secure (HTTPS) are often mentioned. In many cases, these protocols are confused or misinterpreted. Protocols are based on symmetric and asymmetric encryption methods, which we explain in this section. We’ll also provide an overview of the International Organization for Standardization (ISO)/Open Systems Interconnection (OSI) layer model as the foundation for the TCP/IP protocol, which is essential for cloud applications. After introducing you to the technical basics, we’ll show you how to handle the various protocols and certificates on SAP BTP.

### 2.1.1    Basics of Secure Communication

To illustrate the importance of secure communication, let’s start with a simple example common in the literature. Imagine the following scenario: You want to send a message by mail to a specific recipient or addressee. In this scenario, insecure communication would be equivalent to sending your message by postcard. This medium can be read by any person involved in the transport route, such as the letter carrier. Sending the message to the recipient in an envelope, on the other hand, corresponds to secure communication. Only the recipient can read the message, provided the envelope is not opened in transit.

In the digital world, unencrypted message exchange corresponds to the HTTP protocol. Any network node can read a message in plain text along this path. Encrypted message exchange corresponds to the HTTPS protocol, in which any network node can also read the message, but the message is encrypted. Thus, according to the current state of the art, without possession of the private key, the message can only be cracked with immense computing power.

The basis for encrypted communication according to the ISO/OSI layer model is formed by symmetric encryption and asymmetric encryption. Let’s briefly describe these concepts next:

*   Symmetric encryption   
    Symmetric encryption uses a single key that must be known to both the sender and receiver systems of a message. The sender encrypts the message with the key, and the receiver decrypts the message with the same key.
    
    The oldest and probably best-known cipher, the Caesar cipher, dates back to antiquity. Named for Julius Caesar, who used this type of encryption for military correspondence, Caesar ciphers use a simple substitution between plain text source and encoded text result.
    
    Of course, the requirements for encryption have changed since Caesar’s time. Today, the Data Encryption Standard (DES) and Triple DES, the Advanced Encryption Standard (AES), Blowfish, and the International Data Encryption Algorithm (IDEA) are among the best-known symmetric encryption algorithms. The key length is of particular importance for the quality of the encryption. However, a longer key length also requires more computing power for encryption and decryption. The biggest challenge of symmetric encryption is the exchange of keys between sender and receiver. Any network node located between the sender and receiver could decrypt the message if the key is known.
    
*   Asymmetric encryption   
    In asymmetric encryption, both the sender and the receiver have a key pair consisting of a secret (private) and a public key. The sender can encrypt the contents of the message using the recipient’s public key. Only the owner of the secret key, in our case the recipient, can decrypt the message with the secret key. Asymmetric encryption provides security but has the disadvantage of being significantly slower than symmetric encryption.
    

A combination of symmetric and asymmetric encryption methods forms the basis of modern and secure network communications.

SSL version 1.0 was released by Netscape in November 1994 and is located between the application and transport layers in an ISO/OSI layer model. Only nine months later, SSL version 2.0 was introduced. Over time, several security vulnerabilities became known. SSL version 3.0 ensured that these gaps were fixed as early as 1996, and new, more secure cipher suites (collections of algorithms and protocols) with longer key lengths and new algorithms were available.

In the meantime, SSL has been further developed into TLS, which is essentially a symmetric procedure for secure data transmissions. The use of SSL/TLS is a prerequisite in any environment running SAP cloud applications and can be used by default without further activation when configuring SAP BTP.

### 2.1.2    SAP Destination Service

SAP BTP offers the SAP Destination service in both SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. This service is used to address services via standard protocols, such as the following:

*   HTTP/HTTPS
    
*   Remote function call (RFC)
    
*   Mail
    
*   Lightweight Directory Access Protocol (LDAP)
    

The services being addressed can either be directly accessible via a public network or be located in a customer’s on-premise landscape and addressed via the cloud connector.

The functionality of the SAP Destination service can basically be compared to that of RFC destinations in ABAP systems, which are maintained via Transaction SM59. Destinations ensure that the configuration of a connection need not be hard coded in an application. Instead, the configuration can be read out in an application via the name of the destination and the connection carried out dynamically.

Depending on your environment, destinations can be created and maintained at different levels in SAP BTP. In this section, we’ll show you how to create and manage destinations in SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment.

#### Destinations in SAP BTP, Neo Environment

In SAP BTP, Neo environment, destinations can be configured simultaneously at three levels:

*   Subaccount level
    
*   Application level
    
*   Level of the subscription to a service (Java or HTML5)
    

As a result, you can define the same destination of a communication method on more than one configuration level. If the destination is to be accessible for a specific subaccount (and only for that destination), the destination is created in the SAP BTP cockpit by navigating to Connectivity • Destinations, as shown in [Figure 2.1](#02_001.html#f2.1). To learn how to configure destinations in detail, see [Chapter 5](#05_001.html#h5), [Section 5.5](#05_005.html#h5.5).

[![SAP BTP, Neo Environment: Creating a Destination on the Level of the Subaccount](bilderklein/klein02_001.png)](img-f2.1.html) 

**Figure 2.1**     SAP BTP, Neo Environment: Creating a Destination on the Level of the Subaccount

If the destination refers to an application and the subaccount of the respective provider (known as the provider subaccount), the destination is created as part of the configuration of the respective service. In this case, the destination is independent of the consumer subaccount in which the application runs. [Figure 2.2](#02_001.html#f2.2) shows an example of the destination overview of a mobile application in SAP Mobile Services. You can create a new destination by clicking the New Destination button.

[![SAP BTP, Neo Environment: Destinations at the Level of an Application](bilderklein/klein02_002.png)](img-f2.2.html) 

**Figure 2.2**     SAP BTP, Neo Environment: Destinations at the Level of an Application

If the target refers to both the application and the provider subaccount and the consumer subaccount, the destination is created at the subscription level. This case is special because the application is deployed in and subscribed from a dedicated subaccount. The application is not installed in the customer’s subaccount. The configuration of such a destination is done on the level of the subscribed application, as shown in [Figure 2.3](#02_001.html#f2.3), for example, with the SAP Cloud Portal service. In this case, too, you’ll find an overview of the destinations under Destinations and can create a new connection via the New Destination button.

[![SAP BTP, Neo Environment: Destinations at the Subscription Level](bilderklein/klein02_003.png)](img-f2.3.html) 

**Figure 2.3**     SAP BTP, Neo Environment: Destinations at the Subscription Level

The runtime environment tries to find destinations in the following order: subscription, consumer subaccount, and application layer.

The following types of destinations can be used in SAP BTP, Neo environment:

*   HTTP   
    An HTTP destination enables data communication over the HTTP protocol for both Internet and on-premise connections.
    
*   RFC   
    An RFC destination enables connections to on-premise ABAP systems via the RFC protocol using the Java Connector (JCo) and the cloud connector.
    
*   LDAP   
    An LDAP destination enables LDAP-based user management if an LDAP server is operated in the on-premise network.
    
*   Mail   
    A destination of this type enables an email provider to be connected for sending and receiving emails using the Simple Mail Transfer Protocol (SMTP), Internet Message Access Protocol (IMAP), or Post Office Protocol 3 (POP3) protocols.
    

#### Destinations in SAP BTP, Cloud Foundry Environment

In SAP BTP, Cloud Foundry environment, destinations can be defined at the subaccount level. The destination is created for the entire subaccount. You can specify the communication protocol used and other properties such as the authentication method, the proxy type, and the URL.

If the destination refers to a specific subaccount, the destination is created in the SAP BTP cockpit under Connectivity • Destinations, as shown in [Figure 2.4](#02_001.html#f2.4). If you compare this environment with SAP BTP, Neo environment (shown earlier in [Figure 2.1](#02_001.html#f2.1)), notice how SAP has tried to create a consistent user experience (UX) in both environments. The setup here is therefore done in the same way as described further in [Chapter 5](#05_001.html#h5), [Section 5.5](#05_005.html#h5.5). Note that the options available in the side menu depend on your assigned role collections in the subaccount.

In SAP BTP, Cloud Foundry environment, HTTP, RFC, and mail destinations can be created in the same way as in SAP BTP, Neo environment. LDAP destinations were not initially supported in this environment but are now also available.

In addition to creating destinations via the SAP BTP cockpit, you can create destinations using the command line in either SAP BTP, Neo environment or SAP BTP, Cloud Foundry environment. Furthermore, destinations can be created via an OData application programming interface (API).

[![SAP BTP, Cloud Foundry Environment: Destinations at the Subaccount Level](bilderklein/klein02_004.png)](img-f2.4.html) 

**Figure 2.4**     SAP BTP, Cloud Foundry Environment: Destinations at the Subaccount Level

### 2.1.3    Certificate Handling in Destinations

SAP BTP includes root certificates from renowned certificate authorities (CAs), which are stored in the default Java development kit (JDK) truststore, as shown in [Figure 2.4](#02_001.html#f2.4). In this area, SAP has followed the same path as the main browser manufacturers, who also deliver a set of trusted certificates with their browsers. Using a destination to an HTTPS endpoint whose certificates are not in the default JDK truststore, as in the example shown in [Figure 2.5](#02_001.html#f2.5), is a potential source of error, which is not directly apparent when the destination is created. Conversely, if your organization is restrictive, you need a process for removing root certificates that are not trusted.

In this case, click the Check Connection button to perform a connection test. Now, you’ll see an SSL handshake type error message, as shown in [Figure 2.6](#02_001.html#f2.6). This message means that the negotiation of key information did not work because the trust relationship is missing.

The problem can be easily solved by using a custom truststore. For this task, deselect the Use default JDK truststore checkbox in the destination’s configuration. Now, you can select your own truststore location and enter the corresponding password, as shown in [Figure 2.7](#02_001.html#f2.7).

[![Destination with Untrusted Endpoint](bilderklein/klein02_005.png)](img-f2.5.html) 

**Figure 2.5**     Destination with Untrusted Endpoint

[![Error Message When SSL Handshake Occurs](bilderklein/klein02_006.png)](img-f2.6.html) 

**Figure 2.6**     Error Message When SSL Handshake Occurs

[![Using a Custom Individual Truststore](bilderklein/klein02_007.png)](img-f2.7.html) 

**Figure 2.7**     Using a Custom Individual Truststore

The truststore can be created using standard Java commands, for example. However, you can also use tools with a graphical user interface (GUI) for this purpose. A freely available tool for truststore administration, for example, is KeyStore Explorer, available at [https://keystore-explorer.org](https://keystore-explorer.org).

After you’ve created a truststore, click the Upload Certificate link to upload the new truststore, as shown in [Figure 2.8](#02_001.html#f2.8).

[![Uploading a Custom Individual Truststore](bilderklein/klein02_008.png)](img-f2.8.html) 

**Figure 2.8**     Uploading a Custom Individual Truststore

[Figure 2.9](#02_001.html#f2.9) shows you how to store your own truststore in a destination.

[![Configuration with Custom Individual Truststore](bilderklein/klein02_009.png)](img-f2.9.html) 

**Figure 2.9**     Configuration with Custom Individual Truststore

[Figure 2.10](#02_001.html#f2.10) shows the result of the connection test when using a custom individual truststore.

[![Connection Test with Custom Individual Truststore](bilderklein/klein02_010.png)](img-f2.10.html) 

**Figure 2.10**     Connection Test with Custom Individual Truststore

## 2.2    Authentication

Authentication is the process of validating and confirming whether a user is who they say they are. Passwords are the most used authentication method. If a user enters the correct password for their user account or user name, the system assumes that the identity is valid and grants access.

However, this simple authentication method is susceptible to what are called brute force attacks. In this case, an attacker tries to log on with different passwords until the correct password is found. The passwords for such attacks are often not chosen randomly but are read from a list of frequently used passwords. Brute force attacks can be made more difficult by locking user accounts after a certain number of incorrect logon attempts.

The following methods for enforcing authentication SAP BTP are available:

*   Password policies  
    You can enforce strong passwords using password policies. Passwords for accessing SAP applications should always consist of uppercase letters, lowercase letters, numbers, and special characters. In addition, passwords should be changed at regular intervals. In addition to password policies, you should also maintain a list of words and terms that should not be used in passwords.  
    Other technologies such as client certificates, biometrics, one-time tokens, or even your own authentication applications can also be used for authentication. SAP BTP offers you a great deal of flexibility at this point. X.509 client certificates are commonly used as the standard technology.
    
*   Client certificates  
    When using client certificates, the identity of users is verified by exchanging a digital certificate. The certificate is issued by a trusted authority and is uniquely assigned to a user account. With SAP Passport, for example, you have the option of creating a digital client certificate for your S-user. This feature allows you to log on to various SAP websites, SAP Support Portal, and also SAP BTP. Detailed information about this topic can be found at SAP Support Portal at [http://s-prs.co/v562701](http://s-prs.co/v562701).
    
*   Multifactor authentication  
    In certain cases, systems require the successful verification of more than one factor or characteristic before access is granted. These cases therefore involve multifactor authentication (MFA), which is often used to increase security compared to traditional password authentication. An additional proof of identity is required when logging on. The following factors are typically used:
    
    *   SMS tokens
        
    *   Hardware tokens
        
    *   Software tokens
        
    *   Authentication apps
        
    *   Phone calls
        
    *   FIDO2 security keys
        
    
    These additional authentications and verifications are usually performed by the identity provider, where the corresponding components must be activated. The various options available from identity providers are explained next.
    

### 2.2.1    Identity Providers for SAP BTP

In the context of SAP BTP, an identity provider provides the user store. This stores the user’s access to certain subaccounts (such as for administration or development) and access to certain business applications. When choosing an identity provider, SAP BTP offers a great deal of flexibility. [Figure 2.11](#02_002.html#f2.11) shows the different options.

[![SAP BTP: Identity Provider Options](bilderklein/klein02_011.png)](img-f2.11.html) 

**Figure 2.11**     SAP BTP: Identity Provider Options

#### Supported Identity Providers

A distinction can be made between a platform identity provider and an application identity provider.

By default, the SAP ID service is used as the platform identity provider for SAP BTP, but the Identity Authentication service can also be used, as shown in [Figure 2.12](#02_002.html#f2.12). In the Identity Authentication service, users are authenticated via the customer’s own user store (corporate user store) without having to be created separately. A customer’s own identity provider is not permitted with this variant.

[![Platform Identity Provider for the Users of a Subaccount](bilderklein/klein02_012.png)](img-f2.12.html) 

**Figure 2.12**     Platform Identity Provider for the Users of a Subaccount

The platform identity provider is characterized by the following features:

*   It provides the user base for accessing the subaccount.
    
*   It is used in the SAP BTP cockpit, in various development tools, and in the command line.
    
*   By default, the SAP ID service is used.
    
*   Optionally, the Identity Authentication tenant and thus the Identity Authentication service can be used.
    
*   Users managed in the platform identity provider are typically administration and development users.
    

The application identity provider is used to authenticate the users or consumers of an application running on SAP BTP. In addition to the SAP ID service and the Identity Authentication service, a customer-specific identity provider (called a custom identity provider) can also be used as an application identity provider, as shown in [Figure 2.13](#02_002.html#f2.13). The custom identity provider must be a Security Assertion Markup Language (SAML)-based identity provider, such as Microsoft Azure Active Directory (Microsoft Azure AD).

[![Application Identity Provider for Use in a Subaccount](bilderklein/klein02_013.png)](img-f2.13.html) 

**Figure 2.13**     Application Identity Provider for Use in a Subaccount

The application identity provider is characterized by the following properties:

*   It provides the user base for accessing applications in a subaccount of SAP BTP.
    
*   It is used to access to user interfaces (UIs), user tools, and application-to-application (A2A) communication.
    
*   By default, the SAP ID service is used.
    
*   Optionally, the Identity Authentication tenant or a third-party corporate identity provider can be used.
    
*   Users managed with the application identity provider are typically end users.
    

Now, let’s take a closer look at the identity provider options:

*   SAP ID service   
    By default, SAP BTP is preconfigured with a trust relationship to the SAP ID service. Thus, the SAP ID service is used both as a platform identity provider and as an application identity provider. No further configuration is required from your side, except for the assignment of users to the subaccount. No additional costs are incurred for using the SAP ID service.
    
    The SAP ID service manages the users of the official SAP sites, including the SAP developer and partner community. Users can be created either via a self-service capability or via SAP Support Portal by an authorized user within your organization.
    
    The SAP ID service consists of the following components:
    
    *   Centralized user store for all identities that require access to protected application resources
        
    *   Standards-based single sign-on (SSO) service that allows users to log on only once and gain seamless access to all applications deployed through SAP BTP
        
*   Custom identity provider  
    Optionally, your own custom identity provider can be used in both SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. Apart from the license, no additional costs are associated with SAP BTP services for the use of such an identity provider.
    
*   Identity Authentication service  
    Another option is to use the Identity Authentication service as a platform identity provider. This service can be used in the platform identity provider role as a proxy for on-premise user stores, such as an LDAP directory. However, you can also use this service as a proxy for third-party identity providers such as Microsoft Azure AD. The Identity Authentication service is discussed in more detail in [Section 2.4.1](#02_004.html#h2.4.1). The use of this service is basically included in the license of SAP BTP. However, an additional license must be purchased for certain use cases. The metric used for billing is the number of logons.
    

#### Supported Authentication Scenarios

The following scenarios are supported by SAP BTP for authenticating users via the identity provider:

*   Standard identity federation through the SAP ID service
    
*   Identity federation through the Identity Authentication tenant
    
*   Identity federation through a corporate identity provider
    

##### Standard Identity Federation

You can also use the SAP ID service as an identity provider for your identity federation scenario. The trust relationship with the SAP ID service is preconfigured by default on SAP BTP, as mentioned earlier, so you can use it without further configuration. Optionally, you can configure additional trust settings on SAP BTP, such as service provider registration, role assignments to users and groups, and so on.

The use of the SAP ID service for a standard identity federation is shown in [Figure 2.14](#02_002.html#f2.14). However, if a user wants to gain access to SAP BTP, authentication is performed via the SAP ID service and is classified as trustworthy by SAP BTP using trust. Access is therefore possible if the SAP ID service has confirmed positive authentication.

[![Process of Authentication with the SAP ID Service as Identity Provider](bilderklein/klein02_014.png)](img-f2.14.html) 

**Figure 2.14**     Process of Authentication with the SAP ID Service as Identity Provider

##### Identity Authentication Tenant

If you want to use subaccount users (members) from your enterprise user base instead of creating S-users for them, you can use the Identity Authentication tenant (i.e., your instance of the Identity Authentication service) as the identity provider for your applications. Identity Authentication is a cloud service for lifecycle management of the identities you manage. This service gives you the ability to integrate your own user base with SAP BTP. You can also leverage corporate branding (e.g., integrating the company logo on the authentication page) and use identity providers from social media sites (such as Facebook, Twitter, Google, or LinkedIn). In this way, you can create the basis for user provisioning in various cloud and on-premise applications.

The Identity Authentication tenant is available to all subaccounts within your global account, as shown in [Figure 2.15](#02_002.html#f2.15).

[![Using the Identity Authentication Tenant for Authentication in the Identity Network](bilderklein/klein02_015.png)](img-f2.15.html) 

**Figure 2.15**     Using the Identity Authentication Tenant for Authentication in the Identity Network

##### Corporate Identity Provider

In addition to using the SAP ID service and the Identity Authentication service, SAP BTP applications can delegate authentication and identity management to an existing identity provider within your company (a corporate identity provider). In this approach, SAP BTP can authenticate your company’s employees against a corporate directory service, for example. This feature allows your employees (and, if applicable, your customers and partners) to log on to the cloud application using their usual user information. All information about a user required by SAP BTP can be securely passed on with the logon process based on a proven and standardized security protocol.

In this scenario, you don’t need to manage additional systems to take care of the synchronization or provisioning of user accounts between the corporate network and SAP BTP. All you need to do is establish a trust relationship (sometimes called simply trust) between the SAP BTP subaccount running the application and your corporate identity provider. This scenario is shown in [Figure 2.16](#02_002.html#f2.16).

[![Corporate Identity Provider in the Identity Federation](bilderklein/klein02_016.png)](img-f2.16.html) 

**Figure 2.16**     Corporate Identity Provider in the Identity Federation

#### Configuring the Identity Provider in SAP BTP, Neo Environment

A platform identity provider is configured in the same way as an application identity provider, in the SAP BTP cockpit at subaccount level. In SAP BTP, Neo environment, navigate to Security • Trust, as shown in [Figure 2.17](#02_002.html#f2.17).

###### \[»\]  Platform Identity Provider Availability

A platform identity provider is supported only for feature set A. If you deactivated the default identity provider (the SAP ID service) for business users in cloud management tools (feature set A), the process of upgrading to cloud management tools feature set B reactivates the default identity provider. SAP reactivates the default identity provider because cloud management tools feature set B currently only supports platform users from the default identity provider.

[![SAP BTP, Neo Environment: Trust Configuration in the Subaccount](bilderklein/klein02_017.png)](img-f2.17.html) 

**Figure 2.17**     SAP BTP, Neo Environment: Trust Configuration in the Subaccount

If the Platform Identity Provider tab is not visible, the SAP Platform Identity Provider service must first be activated for SAP BTP at the subaccount level:

1.  Navigate to the Services section of the subaccount, as shown in [Figure 2.18](#02_002.html#f2.18), and search for “Platform Identity Provider.”
    
    [![Platform Identity Provider Tile](bilderklein/klein02_018.png)](img-f2.18.html) 
    
    **Figure 2.18**     Platform Identity Provider Tile
    
2.  Click the Platform Identity Provider tile to jump to the service details.
    
3.  Click the Enable button, as shown in [Figure 2.19](#02_002.html#f2.19).
    

[![Activating the SAP Platform Identity Provider Service](bilderklein/klein02_019.png)](img-f2.19.html) 

**Figure 2.19**     Activating the SAP Platform Identity Provider Service

Activating the SAP Platform Identity Provider service for SAP BTP results in the SAP ID service being stored as the default platform identity provider. You can recognize this change by the fact that the URL [https://accounts.sap.com](https://accounts.sap.com) is now stored in the Name field under the Platform Identity Provider tab, as shown in [Figure 2.20](#02_002.html#f2.20).

[![Default Settings for the SAP Platform Identity Provider Service](bilderklein/klein02_020.png)](img-f2.20.html) 

**Figure 2.20**     Default Settings for the SAP Platform Identity Provider Service

Click the Use Identity Authentication Tenant link to use the Identity Authentication tenant as a platform identity provider. You can tell that the Identity Authentication tenant is being used as a platform identity provider by the fact that the Cockpit button (for jumping to the SAP BTP cockpit) and the Administration Console button (for jumping to the administration console) are visible, as shown in [Figure 2.21](#02_002.html#f2.21).

[![Configuring an Identity Authentication Tenant as the Platform Identity Provider](bilderklein/klein02_021.png)](img-f2.21.html) 

**Figure 2.21**     Configuring an Identity Authentication Tenant as the Platform Identity Provider

You can delete the connection between your SAP BTP subaccount and the Identity Authentication tenant by clicking the Delete button.

#### Configuring the Identity Provider in SAP BTP, Cloud Foundry Environment

In SAP BTP, Cloud Foundry environment, both the platform identity provider and the application identity provider are configured at the subaccount level under Security • Trust Configuration.

The SAP ID service is also preconfigured as the default identity provider on this screen, as shown in [Figure 2.22](#02_002.html#f2.22). If you want to use the Identity Authentication service as the platform identity provider instead, you must first establish a trust relationship between the SAP BTP, Cloud Foundry environment subaccount and the Identity Authentication service. You’ll learn how to configure this trust relationship in [Chapter 4](#04_001.html#h4), [Section 4.3.2](#04_003.html#h4.3.2).

[![SAP BTP, Cloud Foundry Environment: Default Identity Provider](bilderklein/klein02_022.png)](img-f2.22.html) 

**Figure 2.22**     SAP BTP, Cloud Foundry Environment: Default Identity Provider

###### \[+\]  Third-Party Identity Providers

Third-party or external identity providers are typically used in the role of an application identity provider. Under Security • Trust, switch to the Application Identity Provider tab area for configuration. However, in principle, a third-party identity provider can also be used as a platform identity provider. For this option, you must use the Identity Authentication service as a proxy.

### 2.2.2    Lightweight Directory Access Protocol

LDAP is a network protocol for communication with a directory service. LDAP is therefore not the directory service itself, but merely the access protocol. LDAP makes it possible to easily search a directory distributed over several servers and built up in a tree structure.

The hierarchical tree structure of the directory service is provided in several essential features. The LDAP data model is simple. LDAP is based on objects and follows approaches of object-oriented programming such as inheritance and polymorphism. The top of the directory structure is always the root element (Root). Below, this element can be branched into the following elements:

*   C: Country
    
*   O: Organization
    
*   OU: Organizational Unit (organizational units)
    
*   DC: Domain Component (individuals)
    

Individuals can be documents, people, or objects.

Objects are designated by their distinguished name (DN). For example, a valid DN for an object may look like the following:

CN=Martin Koch,OU=Consulting,DC=clouddna,DC=at

CN here stands for “common name.” This notation means that the individual Martin Koch (cn=Martin Koch) is assigned to the consulting organizational unit (OU=Consulting) within the domain clouddna (DC=clouddna) in Austria (dc=at). [Figure 2.23](#02_002.html#f2.23) shows the position of a DN within an LDAP hierarchy tree.

[![Example LDAP Structure](bilderklein/klein02_023.png)](img-f2.23.html) 

**Figure 2.23**     Example LDAP Structure

You can configure SAP BTP to use an existing LDAP directory from an on-premise system as a user store. This approach requires the use of the cloud connector.

If you’ve configured SAP BTP applications accordingly, they can use the on-premise user store for the following activities:

*   Checking access data
    
*   User search
    
*   Reading user details
    
*   Managing group memberships
    

Another option for LDAP is to use it in identity federation through the Identity Authentication tenant. In this case, the Identity Authentication service acts as a proxy to the on-premise LDAP directory. This scenario requires the use of the Identity Authentication add-on. This add-on allows the interface to be used for authentication on the subaccount (as opposed to the Identity Authentication service, where the interface is used on the Identity Authentication tenant). For this task, switch to your subaccount in the SAP BTP cockpit and search for Identity Authentication Add-on tile under Services, as shown in [Figure 2.24](#02_002.html#f2.24).

In the detailed view for the add-on, you can enable the service by clicking the Not enabled button.

[![Identity Authentication Add-On Tile](bilderklein/klein02_024.png)](img-f2.24.html) 

**Figure 2.24**     Identity Authentication Add-On Tile

If you’ve configured the Identity Authentication tenant to use an LDAP server in your on-premise landscape, the Identity Authentication add-on acts as a proxy into the on-premise landscape. This approach is currently available only in SAP BTP, Neo environment. The Identity Authentication tenant authenticates itself via the open OAuth protocol (see also [Section 2.3](#02_003.html#h2.3)) to the subaccount in which the add-on is deployed. The Identity Authentication add-on then connects to the LDAP server via the cloud connector, as shown in [Figure 2.25](#02_002.html#f2.25).

[![User Authentication against an On-Premise LDAP Server](bilderklein/klein02_025.png)](img-f2.25.html) 

**Figure 2.25**     User Authentication against an On-Premise LDAP Server

## 2.3    Authorizations

Authorization is the process of granting a user permission to access a specific resource or functionality. This term is usually used as a synonym for the term access control. An example of an authorization process is when you give someone permission to download a certain file on your server. Another example is when you grant administrative access to an application to a single user.

In secure environments, authorization always follows authentication. Users must first prove that their identity is genuine before they are granted access to the requested resources. In SAP BTP, two different standards are used for authorization:

*   SAML   
    SAML is an open standard for exchanging authentication and authorization identities between security domains. SAML was published in 2003 and ratified as an OASIS standard in version 2.0 in 2005.  
    The key principle of the OASIS standard is the issuing of what are called SAML tokens by a SAML service provider. These tokens are accepted by other applications via a trust position. Another name for a SAML token is SAML assertion. Authentication in SAP BTP, Neo environment is based on SAML tokens.
    
*   OAuth  
    The OAuth 2.0 authorization framework allows a third-party application to gain restricted access to an HTTP service. Authorization is done either on behalf of a resource owner by orchestrating an approval interaction between the resource owner and the HTTP service, or the third-party application is allowed access on its own behalf.
    

We’ll focus on OAuth in this section. OAuth 2.0 simplifies the implementation of authorization for client developers while providing specific authorization workflows for different application types. The OAuth 2.0 standard and its extensions are defined by the Internet Engineering Task Force (IETF). The framework is specified in RFC 6749. (RFC here stands for request for comments, a collection of internet specifications.)

OAuth defines four roles within the authorization process:

*   Resource owner  
    The resource owner is an entity that can grant access to a protected resource. If the resource owner is a person, that person is called a user.
    
*   Resource server   
    The server hosting the protected resources can accept and respond to requests for protected resources using access tokens.
    
*   Client  
    The client is an application that requests protected resources on behalf of and with the permission of the resource owner. The term “client” does not imply any implementation characteristics (e.g., a form factor or device build type).
    
*   Authorization server   
    The server that issues access tokens to the client after the resource owner has been successfully authenticated and authorized is called an authorization server.
    

To request an access token, the client obtains authorization from the resource owner. The authorization is expressed in the form of an authorization grant. With this authorization, the client then requests the access token, as shown in [Figure 2.26](#02_003.html#f2.26).

[![OAuth Authorization Process Flow](bilderklein/klein02_026.png)](img-f2.26.html) 

**Figure 2.26**     OAuth Authorization Process Flow

OAuth defines four grant types:

*   Authorization code
    
*   Implicit authorization
    
*   Credentials (password) of the resource owner
    
*   Client credentials
    

In addition, OAuth provides an extension mechanism for defining additional types of authorization granting. SAP BTP, Neo environment supports the following types of authorization granting with OAuth 2.0:

*   Authorization code  
    In this variant, a human user authorizes a mobile application to access resources on their behalf.
    
*   Client credentials  
    In this variant, no human user exists, but a device grants the authorization. In this case, the access token is granted based only on the client credentials.
    

OpenID Connect is an identity layer based on the OAuth 2.0 protocol. Clients can use this layer to verify the identity of users based on the authentication performed by an authorization server and obtain basic profile information about users in a Representational State Transfer (REST)\-like manner. The use of the REST format facilitates further use in SAP BTP services, since a great deal of ready-made libraries and examples exist for this format.

In SAP BTP, Cloud Foundry environment, all services are called up by what’s called an app router. This router is the central entry point for all applications running in SAP BTP, Cloud Foundry environment. The app router provides static content, authenticates users, and rewrites URLs. It also forwards requests to other microservices, including passing user information to microservices, or acts as a proxy.

In SAP BTP, Cloud Foundry environment, authentication is based on the OAuth protocol. All access rights to applications (called application scopes) granted to the current user are forwarded in the form of a token. This token is a JSON Web Token (JWT) and is specified in RFC 7519. This token is created by the application router communicating with the user account and authentication instance of SAP BTP.

## 2.4    SAP Cloud Identity Services

SAP offers SAP Cloud Identity Services in SAP BTP with different areas of responsibility. With this collection of services, you can map the entire security lifecycle of users or identities. The spectrum ranges from the onboarding of new users and the provisioning of these users in the various cloud applications to the detection of potential problems in the assignment of critical authorizations. The Identity Authentication service, mentioned earlier in [Section 2.2](#02_002.html#h2.2), is also part of SAP Cloud Identity Services. This allows you to implement SSO scenarios and delegate authentication to third-party identity providers or identity providers in your on-premise systems.

In connection with SAP Cloud Identity Services, the identity directory plays an important role. The identity directory is the central component for the persistence of users and groups within SAP Cloud Identity Services and serves as the central point of contact for users who have access to SAP cloud applications.

### 2.4.1    Identity Authentication

The Identity Authentication service is a PaaS offering from SAP. This SAML 2.0 identity provider is used for authenticating users in SAP BTP applications and in all SAP software as a service (SaaS) products. Optionally, the service can also be used for applications running in your on-premise landscape and for non-SAP applications.

The Identity Authentication service enables you to authenticate SSO users in the cloud. The service is provided for both SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. The Identity Authentication service is a key element for cloud architecture security. SAP’s strategy is to deliver its cloud solutions preconfigured with Identity Authentication.

###### \[»\]  SSO at a Glance

Ideally, all systems in the IT landscape behave as a single system from the user’s perspective. Users should not have to re-authenticate themselves repeatedly when system boundaries are crossed.

Identity Authentication provides you with the following core functions, as shown in [Figure 2.27](#02_004.html#f2.27):

*   Authentication   
    The Identity Authentication service acts as an identity provider that validates credentials provided by users. Upon successful authentication, the service issues a SAML assertion used by target applications. We described this authentication scenario earlier in [Section 2.2.1](#02_002.html#h2.2.1).
    
*   Identity federation  and SSO  
    The service can delegate authentication to a third-party identity provider, enabling SSO across on-premise and cloud-based applications.
    
*   Risk-based authentication   
    The service enables multifactor authentication if stronger means of authentication are required to access specific business applications.
    
*   User management   
    The service enables management of its users.
    

[![Functions of Identity Authentication](bilderklein/klein02_027.png)](img-f2.27.html) 

**Figure 2.27**     Functions of Identity Authentication

This service plan for the Identity Authentication service is included in the overall SAP BTP contract. You’ll receive two instances of the Identity Authentication service: one for testing and one for productive use. These instances are called Identity Authentication tenants. In principle, you have the option of purchasing additional tenants, regardless of whether they are used productively or for testing purposes. The license scope of the Identity Authentication service includes all SAP cloud to SAP cloud logons. If you would also like to connect non-SAP products, then an additional license must be purchased. The metric for this license is based on the number of logons.

After you purchase a license for the Identity Authentication service, you’ll receive an email invitation to register the initial administrator. The email contains a link to the initial page of the Identity Authentication tenant administration console, where you can confirm the registration of your initial administration user.

###### \[+\]  Number of Administrators

Based on our experience in our projects, we recommend that you create another administration user immediately after activating the initial administration user.

#### Scenarios for the Use of Identity Authentication

The Identity Authentication service supports the following scenarios, which we’ll discuss in this section:

*   Business-to-consumer (B2C) scenarios
    
*   Business-to-business (B2B) scenarios
    
*   Business-to-employee (B2E) scenarios
    

##### Business-to-Consumer

From a security perspective, the B2C scenario covers all actions that traditional users perform when using an application, including user registration, authentication, and authorization.

###### \[eg\]  Web Shop Registration

A typical use case is a web store or mobile shopping app. Most likely, you purchased this book online, and we’ll use exactly this case as our example for a B2C scenario. To purchase this book via the SAP PRESS web store, you must register an account in the web store. This action is initiated by you in the role of the customer. In the first step, you’ll be redirected to a registration page where you’ll create a new user account based on your email address. For this task, you must agree to the terms of use. Optionally, you can use a social logon; that is, you can use one of your existing social media accounts (such as Facebook, Twitter, LinkedIn, or Google) for the registration process. If you wish to use your own password, that password must comply with certain guidelines.

After you’ve registered, an email with an activation link will be sent to you. Once you’ve activated the account by clicking on the link, you can purchase both physical and electronic items. If you forget your password in the meantime, you have a self-service option to reset it.

All the functions you learned about in this scenario are covered by the Identity Authentication service for B2C applications on SAP BTP. The service supports you in the following functions:

*   Authentication with user name and password
    
*   SSO for cloud applications
    
*   Social sign-on
    
*   User self-registration
    
*   Creating branding elements on logon, registration, password update, and account activation forms
    
*   Setting password and security policies
    
*   Creating privacy policies and terms of use
    
*   Importing and exporting users
    

##### Business-to-Business

From a security perspective, the B2B scenario covers all actions performed by a corporate customer when using an application. This scenario differs from the B2C scenario in that no self-registration is possible. Users are invited by the service provider or by an authorized person from their own company.

Typical use cases are for service portals or for B2B stores. A B2B store enables corporate customers to purchase certain goods and services that cannot be purchased by end customers. These products might include spare parts, for example. Corporate customers are typically provided with a user account by the store operator. As in B2C scenarios, enterprise customers must activate this user account and accept the provider’s terms of use. After completing the activation steps, these users can shop in the store. Social sign-on is typically not desired in this scenario.

###### \[eg\]  SAP Support Portal

Another example of a B2B scenario is a support portal. We assume that you’ve already worked with SAP Support Portal. Among other things, you can create tickets in SAP Support Portal if a problem occurs in your systems, such as a short dump in a standard SAP program. In SAP Support Portal, you can also access SAP Notes. In both cases, you’ll need an authorized user. SAP initially provides your company with an S-user. This user has administrator rights for your company and can create other users and authorize them according to your requirements.

In the two use cases mentioned earlier, the Identity Authentication service can support you completely or at least partially. The following functions are available:

*   Authentication with user name and password
    
*   SSO for cloud applications
    
*   Inviting partners
    
*   Deputy registration of partners by administrators
    
*   Creating branding elements on the forms for logon, registration, password update, and account activation
    
*   Setting password and security policies
    
*   Creating privacy policies and terms of use
    
*   Importing and exporting users
    

##### Business-to-Employee

The B2E scenario covers, from a security perspective, all the actions that an employee of your company takes when using enterprise applications.

Hybrid system landscapes are now a reality for many SAP customers. In these landscapes, a combination of on-premise and SaaS solutions is used. For example, the SaaS solutions SAP SuccessFactors and SAP Concur are often used in combination with an on-premise SAP Business Suite or an SAP S/4HANA system. In this case, the SAP Fiori launchpad in SAP BTP can take on the role of the central entry point, and the Identity Authentication service handles user authentication and provides the SSO.

###### \[eg\]  SAP Fiori Launchpad

You’ve no doubt heard of the SAP Fiori launchpad. The SAP Fiori launchpad is the central entry point for modern SAP applications. Many applications in SAP S/4HANA are delivered in the form of SAP Fiori apps.

The SAP Fiori launchpad can be deployed both on-premise and via SAP BTP. When deployed via SAP BTP, the Identity Authentication service can be used to help integrate your existing user store and thus provide a consistent UX. Users can log on to the system with their usual credentials and authentication mechanisms.

The following functions are available for B2E scenarios:

*   Authentication with user name and password
    
*   SSO for cloud applications
    
*   Creating branding elements on logon, registration, password update, and account activation forms
    
*   Setting password and security policies
    
*   Creating privacy policies and terms of use
    
*   Importing and exporting users
    

#### Logging on to the Identity Authentication Tenant

You can log on to the Identity Authentication tenant using the following URL: https://<IdentityAuthenticationTenantID>.accounts.ondemand.com. Replace the placeholder <IdentityAuthenticationTenantID> with the ID of your Identity Authentication tenant.

The tenant ID is an ID automatically generated by SAP. The first administration user created for the client receives an activation email with a URL. This URL contains the tenant ID. However, you also have the option of jumping directly from the SAP BTP cockpit to the Identity Authentication tenant.

In the SAP BTP cockpit in SAP BTP, Neo environment, navigate to Security • Trust and switch to the Platform Identity Provider tab. Click the Administration Console button, as shown in [Figure 2.28](#02_004.html#f2.28).

[![SAP BTP, Neo Environment: Jumping to the Identity Authentication Tenant](bilderklein/klein02_028.png)](img-f2.28.html) 

**Figure 2.28**     SAP BTP, Neo Environment: Jumping to the Identity Authentication Tenant

In the SAP BTP, Cloud Foundry environment subaccount, one prerequisite for the jump is that a trust relationship must have been established between the subaccount and the Identity Authentication tenant. For this task, navigate to Security • Trust Configuration and click the Custom IAS tenant link, as shown in [Figure 2.29](#02_004.html#f2.29).

[![SAP BTP, Cloud Foundry Environment: Trust Configuration](bilderklein/klein02_029.png)](img-f2.29.html) 

**Figure 2.29**     SAP BTP, Cloud Foundry Environment: Trust Configuration

In the resulting overview of custom Identity Authentication tenants, click the link that corresponds to the host name of your Identity Authentication tenant (in the Host Name of Identity Authentication Tenant field), as shown in [Figure 2.30](#02_004.html#f2.30).

[![SAP BTP, Cloud Foundry Environment: Jumping to the Identity Authentication Tenant](bilderklein/klein02_030.png)](img-f2.30.html) 

**Figure 2.30**     SAP BTP, Cloud Foundry Environment: Jumping to the Identity Authentication Tenant

[Figure 2.31](#02_004.html#f2.31) shows the logon screen for the administration console of your Identity Authentication tenant. You must initially log on with the user name you received in the invitation email. If you’ve already created another administration user, you can also use that administration user instead.

[![Logging on to the Identity Authentication Tenant](bilderklein/klein02_031.png)](img-f2.31.html) 

**Figure 2.31**     Logging on to the Identity Authentication Tenant

#### User Maintenance

After successful logon, the Identity Authentication service overview screen appears, as shown in [Figure 2.32](#02_004.html#f2.32).

[![Identity Authentication Service: Overview](bilderklein/klein02_032.png)](img-f2.32.html) 

**Figure 2.32**     Identity Authentication Service: Overview

The homepage is built dynamically based on the permissions assigned to you. The menu is divided into the following sections:

*   Users & Authorizations  
    In this area, you can manage and administer users, user groups, and administration users. You can import or export users and configure target systems for user provisioning.
    
*   Applications & Resources  
    In this area, you can register and configure applications and subaccounts. Identity Authentication tenant settings are also made here. You can customize the documents delivered in the standard terms of use and privacy policy and maintain them in different languages. You can also maintain email templates for various notifications in different languages. You also have the option of storing a custom Cascading Style Sheet (CSS) to adapt the log on screen for the Identity Authentication service, for instance, to use your corporate design. You can also adapt the password guidelines to your requirements and specifications in this area.
    
*   Identity Providers   
    In this area, you can integrate your existing corporate identity providers. The configuration of social identity providers is also done here. In this context, the Identity Authentication service allows you to use Google, Facebook, LinkedIn, and Twitter. You can also configure external source systems for user data, such as SAP SuccessFactors, here.
    
*   Monitoring & Reporting  
    In this area, you can view the metrics relevant for measuring or licensing the system. In addition, you can generate access data for the API-based readout of audit logs and for downloading change logs and troubleshooting logs as CSV files.
    

To maintain administration users first, navigate to Users & Authorizations • Administrators.

##### Administrator Types

An overview of the administration users currently maintained in the Identity Authentication service appears, as shown in [Figure 2.33](#02_004.html#f2.33). Notice the two kinds of the icons, which represent two types of administration users: persons ![inline image](bilder/02_icon_person.png)and systems ![inline image](bilder/02_icon_system.png). You can create both types of administration users on this screen. An administration user of the systems type can be given the same roles and can perform the same actions as an administration user of the person type.

[![Identity Authentication Service: Overview of Administration Users](bilderklein/klein02_033.png)](img-f2.33.html) 

**Figure 2.33**     Identity Authentication Service: Overview of Administration Users

##### Creating Administration Users

Click the Add button to create a new administration user. For this purpose, you must maintain the email address and a first name and a last name for the administrator.

You can assign different roles to administration users. Except for the Read Users role, all the following roles are selected by default for administration users:

*   Manage Applications  
    This role gives the tenant administration user the right to configure applications via the administration console.
    
*   Manage Corporate Identity Providers  
    This role gives the tenant administration user the right to configure identity providers via the administration console.
    
*   Manage Users  
    This role gives the tenant administration user the right to manage, import, and export users via the administration console.
    
*   Read Users  
    This role gives the tenant administration user the right to retrieve user data and import users via the administration console and via the Identity Authentication service SCIM REST API. This standard is used to manage identities across domains.
    
*   Manage Groups  
    This role gives the tenant administration user the right to create, edit, and delete user groups via the administration console.
    
*   Manage Tenant Configuration  
    This role gives the tenant administration user the right to manage the tenant configuration and the assignment of permissions to users.
    

###### \[»\]  SCIM Protocol

SCIM is an HTTP-based protocol that simplifies the management of identities in what are called multidomain scenarios by means of a standardized service. Such scenarios exist, for example, across domains between the customer’s own domain and the standard domain of SAP BTP (ondemand.com). The SCIM standard is managed by the IETF. The following specifications cover the SCIM standard:

*   RFC 7642 (SCIM: Definitions, Overview, Concepts, and Requirements)
    
*   RFC 7643 (SCIM: Core Schema)
    
*   RFC 7644 (SCIM: Protocol)
    

SCIM-enabled systems can be used as source or target systems in the Identity Authentication service. In addition, the Identity Authentication service provides the SCIM API, which you can use to create and manage users and user groups.

SCIM 2.0 is built on an object model, shown in [Figure 2.34](#02_004.html#f2.34). In this model, a resource serves as the core element from which all other SCIM objects are derived.

[![SCIM Object Model](bilderklein/klein02_034.png)](img-f2.34.html) 

**Figure 2.34**     SCIM Object Model

Assign the desired roles to your new administration user and then save the user by clicking the Save button, as shown in [Figure 2.35](#02_004.html#f2.35).

[![Identity Authentication Service: Creating Administration Users](bilderklein/klein02_035.png)](img-f2.35.html) 

**Figure 2.35**     Identity Authentication Service: Creating Administration Users

The system now assigns a user ID for the new user. In parallel, the user receives an email. This email contains a link with which the user account can be activated.

##### Maintaining Additional Users

To maintain the additional users who need to access your cloud applications via the Identity Authentication service, navigate to Users & Authorizations • User Management.

You’ll now see a list of all users created in the Identity Authentication service, as shown in [Figure 2.36](#02_004.html#f2.36). Since this list usually contains many entries, you can search for different attributes, such as the User ID. Click on a row in the results table to view the details of a specific user.

[![Identity Authentication Service: User Overview](bilderklein/klein02_036.png)](img-f2.36.html) 

**Figure 2.36**     Identity Authentication Service: User Overview

Click the Add User button to create a new user. In the creation dialog box, you must maintain the last name, email address, user type, and account activation type information as mandatory, as shown in [Figure 2.37](#02_004.html#f2.37). In the User Type field, the Employee option is selected by default. You can choose between several options, including Customer, Employee, Partner, and Public (i.e., people who are not necessarily known to the company).

[![Identity Authentication Service: Creating a User](bilderklein/klein02_037.png)](img-f2.37.html) 

**Figure 2.37**     Identity Authentication Service: Creating a User

The following options are available for activating the user account:

*   Send activation e-mail  
    The user will receive an email with instructions on how to activate the user account.
    
*   Set initial password  
    The tenant administrator sets the password for the user. The user will be prompted to change the password during the first authentication.
    
*   Set status active  
    The tenant administrator directly creates an active user but does not set an initial password for the user. Furthermore, the user does not receive an email with instructions on how to activate the user account. This option must be selected if the Identity Authentication service is used as a proxy to another identity provider or if the user authenticates by means of a certificate.
    

[Figure 2.38](#02_004.html#f2.38) shows the welcome email that a user receives when the Send activation e-mail option is selected. The text used in the email is predefined by SAP. Later in this section, we’ll show how you can customize the email to comply with your branding and also how you can translate SAP’s default texts.

[![Welcome Email](bilderklein/klein02_038.png)](img-f2.38.html) 

**Figure 2.38**     Welcome Email

The emails generated by the Identity Authentication service are always sent via the address notification@sapnetworkmail.com. However, you can also use your own email server for this purpose. The required configuration can be found by navigating to Applications & Resources • Applications and is described at the end of this section.

##### Advanced User Information

When creating a new user, you only need to maintain the attributes that are most important from the perspective of the Identity Authentication service. In many cases, however, you may want to maintain additional information about the user. For this task, jump to the user’s details, as shown in [Figure 2.39](#02_004.html#f2.39). You can maintain personal information, employee information, company information, and customer-specific attributes.

[![User Details](bilderklein/klein02_039.png)](img-f2.39.html) 

**Figure 2.39**     User Details

The Personal Information section will be relevant for many deployment scenarios. In this section, for example, you can configure the validity period of a user account. For example, if an employee leaves your company, you don’t need to delete the associated user account; instead, you can set a date in the Valid To field to capture the effective date of this employee’s departure and thus delimit the validity period for the user, as shown in [Figure 2.40](#02_004.html#f2.40). In this section, you can also at least partially control the behavior of the Identity Authentication service when sending notifications by setting a user’s language. Email notifications are always sent in the appropriate language, if possible.

The Legal section also contains important information that can help support user management, as shown in [Figure 2.41](#02_004.html#f2.41).

[![Personal Information in a User Account](bilderklein/klein02_040.png)](img-f2.40.html) 

**Figure 2.40**     Personal Information in a User Account

[![Legal Information in a User Account](bilderklein/klein02_041.png)](img-f2.41.html) 

**Figure 2.41**     Legal Information in a User Account

Among other things, you can see when a user last successfully logged on, whether the password is locked, when the password was set, and from which system the password was obtained. This information can only be accessed in read-only mode. Data manipulation is therefore not possible.

##### Unlocking Users

A typical support activity is unlocking users or resetting passwords. You can perform these activities starting from the user details. For this task, under the Authentication tab, click Password Details, as shown in [Figure 2.42](#02_004.html#f2.42).

[![Access Password Details in a User Account](bilderklein/klein02_042.png)](img-f2.42.html) 

**Figure 2.42**     Access Password Details in a User Account

On the password details screen, you can perform the following actions, as shown in [Figure 2.43](#02_004.html#f2.43):

*   Unlocking a locked user account
    
*   Sending an email with information about resetting the password
    
*   Resetting the counter for sending emails per user (to limit the number of activation or password reset emails that can be sent to a user)
    
*   Setting an initial password
    

[![Password Activity Details in a User Account](bilderklein/klein02_043.png)](img-f2.43.html) 

**Figure 2.43**     Password Activity Details in a User Account

##### User Groups

A user group is a collection of users. You can use these groups to manage users who share certain commonalities. For example, you might have groups for the users of employees who work in the same department or who have similar tasks within the company. To view existing user groups, navigate to Users & Authorizations • User Groups, as shown in [Figure 2.44](#02_004.html#f2.44).

[![User Group Maintenance](bilderklein/klein02_044.png)](img-f2.44.html) 

**Figure 2.44**     User Group Maintenance

Click the Create button to create a new user group. You must assign a technical name and a display name in the Name and Display name fields, respectively, as shown in [Figure 2.45](#02_004.html#f2.45). The name is subject to the restriction that no special characters or spaces may be used. Optionally, you can add a description. When saving, a group ID in the form of a globally unique identifier (GUID) is also assigned.

[![Creating a User Group](bilderklein/klein02_045.png)](img-f2.45.html) 

**Figure 2.45**     Creating a User Group

Assigning users to a group is done via the user management screen at Users & Authorization • User Management. For this task, navigate to the details of the user account and click the Assign Groups button under the User Groups tab, as shown in [Figure 2.46](#02_004.html#f2.46).

[![Assigning Users to a User Group](bilderklein/klein02_046.png)](img-f2.46.html) 

**Figure 2.46**     Assigning Users to a User Group

In the popup window that opens, select the desired user groups and then click the Save button, as shown in [Figure 2.47](#02_004.html#f2.47).

[![Selecting Groups for Mapping](bilderklein/klein02_047.png)](img-f2.47.html) 

**Figure 2.47**     Selecting Groups for Mapping

#### Tenant Settings

The Identity Authentication tenant is provided by SAP with preconfigured default settings. However, you can customize these settings by navigating to Application & Resources • Tenant Settings.

You can customize various settings for the tenant. The most relevant settings and options from our point of view include the following:

*   Customizing and downloading SAML 2.0 metadata as part of SAML 2.0 configuration
    
*   Configuring the trusted CAs for X.509 client certificates
    
*   Configuring the validity period of email links
    
*   Configuring session timeouts
    
*   Configuring risk-based authentication
    
*   Configuring the corporate user store
    
*   Configuring the email server
    
*   Enabling security alerts
    
*   Configuring a custom domain
    

In the following sections, we’ll go into more detail about the settings relevant in practice.

##### Validity Period of Email Links

Email notifications containing links for specific actions can be sent for a wide variety of events. To configure the validity period of email links, navigate to Applications & Resources • Tenant Settings and select Initial Password and E-Mail Link Validity, as shown in [Figure 2.48](#02_004.html#f2.48).

You can adjust the validity period individually, between 1 hour and 30 days, as shown in [Figure 2.49](#02_004.html#f2.49). For all password-related actions, we recommend limiting the validity to a few hours.

[![Jumping to the Configuration of the Email Link Validity Period](bilderklein/klein02_048.png)](img-f2.48.html) 

**Figure 2.48**     Jumping to the Configuration of the Email Link Validity Period

[![Email Link Validity Period Configuration](bilderklein/klein02_049.png)](img-f2.49.html) 

**Figure 2.49**     Email Link Validity Period Configuration

##### Configuring Session Timeouts

The Identity Authentication service also provides you with the ability to configure session timeouts for users. After the timeout threshold is reached, a new authentication is required. To jump to the configuration, select Session Timeout under Applications & Resources • Tenant Settings, as shown in [Figure 2.50](#02_004.html#f2.50).

[![Navigating to the Configuration of the Session Timeout](bilderklein/klein02_050.png)](img-f2.50.html) 

**Figure 2.50**     Navigating to the Configuration of the Session Timeout

The session timeout is preconfigured, with the maximum value of 12 hours. You can choose a value between 5 minutes and 12 hours as needed, as shown in [Figure 2.51](#02_004.html#f2.51).

[![Configuring Session Timeouts](bilderklein/klein02_051.png)](img-f2.51.html) 

**Figure 2.51**     Configuring Session Timeouts

##### Configuring the Mail Server

As mentioned earlier, the Identity Authentication service enables you to send notification emails via your own email server. To set up this feature, navigate to Applications & Resources • Tenant Settings and select the Mail Server Configuration entry, as shown in [Figure 2.52](#02_004.html#f2.52).

[![Navigating the Configuration of the Mail Server](bilderklein/klein02_052.png)](img-f2.52.html) 

**Figure 2.52**     Navigating the Configuration of the Mail Server

By default, a mail server from SAP is used to send email notifications. To use your own server, you’ll need to provide host and port; sender; and recipient address, user name, and password information, as shown in [Figure 2.53](#02_004.html#f2.53). Your email server must support SSL.

[![Configuring Your Own Custom Mail Server](bilderklein/klein02_053.png)](img-f2.53.html) 

**Figure 2.53**     Configuring Your Own Custom Mail Server

The Identity Authentication service also allows you to send email notifications using Amazon Simple Email Service, as shown in [Figure 2.54](#02_004.html#f2.54). For more information about this solution, visit [https://aws.amazon.com/ses/](https://aws.amazon.com/ses/). By using Amazon Simple Email Service, you can modify the sender and receiver of the email without the need to maintain a custom mail server.

[![Configuring the Amazon Simple Email Service](bilderklein/klein02_054.png)](img-f2.54.html) 

**Figure 2.54**     Configuring the Amazon Simple Email Service

##### Security Alerting

The Identity Authentication service allows you to send alert emails in the following cases:

*   Email change
    
*   Logon name change
    
*   Credential change
    
*   Administrator authorization removal
    
*   Two-factor authentication device activation or deactivation
    
*   Registration with a nonunique email
    

Sending such alerts is disabled by default. Enable these alerts by setting the switch to ON for the desired alert categories, as shown in [Figure 2.55](#02_004.html#f2.55). Users will then be informed about the configured changes.

[![Security Alerting Configuration](bilderklein/klein02_055.png)](img-f2.55.html) 

**Figure 2.55**     Security Alerting Configuration

##### Maintaining Password Policies

Passwords for authenticating users should be subject to certain rules and restrictions, as mentioned earlier. These rules and restrictions are defined in a password policy. The Identity Authentication service provides two predefined password policies for your use. These default policies cannot be changed.

However, you can create custom policies as well by navigating to Application & Resources • Password Policies. Click the Add Custom Policy button to create a custom policy, as shown in [Figure 2.56](#02_004.html#f2.56).

[![Password Policy Configuration](bilderklein/klein02_056.png)](img-f2.56.html) 

**Figure 2.56**     Password Policy Configuration

[Figure 2.57](#02_004.html#f2.57) shows the restrictions you can define for passwords, such as the length of the password, the time after which a password must be changed, the maximum time during which a user may be inactive, the reusability of passwords, and the maximum number of failed logons allowed. Make sure that the duration for locking a password (Password Locked Period) is set to 1 hour by default. Thus, if a user account is locked because of too many incorrect logon attempts, the account will be automatically unlocked after 1 hour has elapsed. The maximum value for a locked period is 24 hours. No option exists for locking a user account permanently or having an indefinitely locked account that can be unlocked only by an administrator.

[![Password Policy Details](bilderklein/klein02_057.png)](img-f2.57.html) 

**Figure 2.57**     Password Policy Details

Password complexity itself cannot be configured at this point. Passwords must contain three of the following four components for all policy types:

*   Lowercase letters (a–z)
    
*   Uppercase letters (A–Z)
    
*   Digits (0–9)
    
*   Special characters
    

#### Application Settings

In the context of SAML authorization, the Identity Authentication service assumes the role of the identity provider. The connected systems, such as the SAP BTP subaccounts, assume the role of a service provider. These service providers are managed as applications in the Identity Authentication service and can be configured independently of each other.

Navigate to Applications & Resources • Applications to see the connected subaccounts, as shown in [Figure 2.58](#02_004.html#f2.58). Then, select the subaccount you want to configure from the list of applications. If your desired subaccount is not visible in the list, the SAP Platform Identity Provider service for SAP BTP has not been activated for it.

[![Configuring Applications for the Identity Authentication Service](bilderklein/klein02_058.png)](img-f2.58.html) 

**Figure 2.58**     Configuring Applications for the Identity Authentication Service

In the settings for the applications, you can adjust the following areas:

*   Setting the trust relationship (Trust)
    
*   Setting authentication and access control (Authentication and Access)
    
*   Setting the branding and layout of the forms (Branding and Layout)
    

##### Trust

In the Trust section, the most important setting is the authentication type used, which can be either SAML 2.0 or OpenID Connect. Subaccounts in SAP BTP, Neo environment use SAML 2.0, while subaccounts of SAP BTP, Cloud Foundry environment use OpenID Connect by default. Additionally, in the Trust section, you can customize the attributes of the authentication assertion and configure API-based access to the subaccount.

##### Conditional Authentication

In the Conditional Authentication area, you have the option of configuring the conditional authentication feature, which allows you to control how users are authenticated by different identity providers depending on the following attributes:

*   Email domain
    
*   User type
    
*   User group
    
*   IP address range
    

To create a corresponding rule, click the \+ Add Rule button and specify which conditions apply to each provider. An example would be to authenticate certain user groups only from a specific identity provider or to allow authentication only if the user logs on from an internal IP address, as shown in [Figure 2.59](#02_004.html#f2.59).

[![Defining Authentication Rules](bilderklein/klein02_059.png)](img-f2.59.html) 

**Figure 2.59**     Defining Authentication Rules

The Authentication and Access section configures how users log on to the system and which policies are used and must be accepted by users, as shown in [Figure 2.60](#02_004.html#f2.60).

[![Configuring Authentication and Access Control](bilderklein/klein02_060.png)](img-f2.60.html) 

**Figure 2.60**     Configuring Authentication and Access Control

##### Social Sign-On

Social sign-on is disabled by default. This logon method is generally used in consumer scenarios where the users are not employees of your company but instead end customers. In most of these cases, creating users in the identity provider for all these customers doesn’t make sense.

Instead, existing user accounts in various social media are used. The prerequisite for this capability is the configuration of social identity providers like Google, Facebook, LinkedIn, or Twitter, as shown in [Figure 2.61](#02_004.html#f2.61). For each of these providers, you can specify separately that social sign-on can be used for authentication.

[![Configuring Social Identity Providers](bilderklein/klein02_061.png)](img-f2.61.html) 

**Figure 2.61**     Configuring Social Identity Providers

##### Risk-Based Authentication

Depending on your company’s internal requirements, you may need to authenticate certain user groups differently. For example, you can set up two-factor authentication for administrators. The Identity Authentication service supports you in such cases with what’s called risk-based authentication.

To configure risk-based authentication, navigate to Risk-Based Authentication (as shown earlier in [Figure 2.48](#02_004.html#f2.48)). In the following window, add a new authentication rule by clicking the \+ Create Rule button, as shown in [Figure 2.62](#02_004.html#f2.62). You can add as many rules as you like.

[![Risk-Based Authentication](bilderklein/klein02_062.png)](img-f2.62.html) 

**Figure 2.62**     Risk-Based Authentication

You must also define an action for the default rule. This action determines what should happen if no other rule applies. The default rule is always active. However, you can set the default rule to inactive by selecting Deny.

The following actions are available for the rule:

*   Allow  
    This action allows you to authenticate users according to the rule conditions.
    
*   Deny  
    This action denies a user authentication according to the rule conditions. This option is typically used for a test application or before an application goes live.
    
*   TOTP Two-Factor Authentication   
    This action uses two factors to authenticate the user. Users must provide a time-based one-time password (TOTP), or passcode, in addition to their primary credentials. For this task, they must install an authenticator application, such as SAP Authenticator, on their mobile devices to generate TOTP passcodes.
    
*   SMS Two-Factor Authentication  
    This variant of two-factor authentication requires users to provide an SMS code sent to their mobile devices in addition to their primary credentials. To use two-factor authentication via SMS, you must have licensed SAP Authentication 365 and configured it in the administration console for Identity Authentication.
    
*   Web Two-Factor Authentication  
    Users must authenticate with a device, such as a built-in biometric scanner, USB drive, Bluetooth device, or near-field communication (NFC) device, in addition to their primary credentials.
    
*   E-Mail OTP Code  
    Users must authenticate by first providing their primary credentials and then providing the 8-digit code sent via email. The code is valid for 10 minutes. If the email is not verified, the system won’t send a code.
    

The configuration of an authentication rule is shown in [Figure 2.63](#02_004.html#f2.63). The central attribute of such a rule is the action to be performed. One or more of the following attributes can trigger an action:

*   IP Range  
    In this field, you can define the range of allowed IP addresses or proxies from which users may log on.
    
*   Authentication Method  
    In this field, you can select the authentication method to be used by the authenticating user.
    
*   User Type  
    In this field, you can specify the user type that the authenticating user must have.
    
*   Group  
    In this field, you can specify a cloud or on-premise user group that the authenticating user must be a member of. If no group is selected, the rule applies to all users.
    
*   Corporate Attribute  
    In this field, you can specify an attribute from the corporate identity provider assertion, based on which the rule action will be applied.
    

[![Defining Risk-Based Authentication](bilderklein/klein02_063.png)](img-f2.63.html) 

**Figure 2.63**     Defining Risk-Based Authentication

##### Branding

Under Branding and Layout, the Identity Authentication service allows you to customize the appearance and behavior of the generated pages and emails (e.g., logon and password reset pages) according to your specifications. These options include, as shown in [Figure 2.64](#02_004.html#f2.64), the logo, a CSS theme for branding, and the email templates to be used.

[![Branding](bilderklein/klein02_064.png)](img-f2.64.html) 

**Figure 2.64**     Branding

### 2.4.2    Identity Provisioning

Another component of SAP Cloud Identity Services is the Identity Provisioning service. This service helps you automate the identity lifecycle process by helping you provision identities and their authorizations for cloud-based and on-premise business applications. At the time of this writing, this service is running only in SAP BTP, Neo environment.

#### Architecture of Identity Provisioning

The operation of identity provisioning is shown in [Figure 2.65](#02_004.html#f2.65). The service reads users from one or more source systems, transforms them, and customizes them. A transformation can mean that attributes that exist in a source system about a user (customer-specific attributes) are mapped to a standard attribute in SAP BTP. Users are then written to one or more target systems.

Let’s break down the key components of this architecture:

*   Source systems   
    The source system is usually your company’s existing corporate user store, which can be a cloud-based or on-premise system, such as Microsoft Active Directory. The Identity Authentication service can also serve as the source system. You can maintain a maximum of 20 source systems.
    
    [![Identity Provisioning Service: Architecture](bilderklein/klein02_065.png)](img-f2.65.html) 
    
    **Figure 2.65**     Identity Provisioning Service: Architecture
    
    Numerous source systems listed are generally supported by the Identity Provisioning service. Your options depend on the license bundle, in which certain combinations are allowed. For an overview of the available bundles, refer to SAP Help Portal at [http://s-prs.co/v562702](http://s-prs.co/v562702). The possible source systems may include the following:
    
    *   Identity Authentication
        
    *   SAP NetWeaver Application Server (AS) for ABAP
        
    *   SAP BTP, ABAP environment
        
    *   SAP BTP account members (Neo)
        
    *   SAP BTP Java/HTML5 apps (Neo)
        
    *   SAP BTP extended services for user account and authentication (XSUAA) (Cloud Foundry)
        
    *   SAP Central Business Configuration
        
    *   SAP Commissions
        
    *   SAP Fieldglass
        
    *   SAP Integrated Business Planning for Supply Chain (SAP IBP)
        
    *   SAP Jam Collaboration
        
    *   SAP Marketing Cloud
        
    *   SAP S/4HANA Cloud
        
    *   SAP S/4HANA on-premise
        
    *   SAP SuccessFactors
        
    *   Google G Suite
        
    *   Microsoft Active Directory
        
    *   Microsoft Azure AD
        
    *   SAP Work Zone
        

*   Target systems   
    The target system is the cloud or on-premise system in which you want to create or customize the identities from your source system. You can maintain a maximum of 50 target systems. The same systems are permitted as the target system as the source system. In addition, you can use the following systems as target systems:
    
    *   Identity Authentication
        
    *   SAP Analytics Cloud
        
    *   SAP NetWeaver AS for ABAP
        
    *   SAP BTP, ABAP environment
        
    *   SAP BTP account members (Neo)
        
    *   SAP BTP Java/HTML5 apps (Neo)
        
    *   SAP BTP XSUAA (Cloud Foundry)
        
    *   SAP Central Business Configuration
        
    *   SAP Commissions
        
    *   SAP Fieldglass
        
    *   SAP IBP
        
    *   SAP Jam Collaboration
        
    *   SAP Marketing Cloud
        
    *   SAP S/4HANA Cloud
        
    *   SAP S/4HANA on-premise
        
    *   SAP Sales Cloud (analytics and artificial intelligence \[AI\])
        
    *   SAP Work Zone
        
*   Proxy system  
    A proxy system is a special connector used in hybrid scenarios where cloud systems are connected to on-premise systems. In this scenario, you can provision entities from a cloud system to an on-premise system, and vice versa, without establishing a direct connection between these systems. For this purpose, the Identity Provisioning service can be used as a proxy system that performs provisioning operations requested by the on-premise system, such as creating, updating, and deleting entities.
    
*   Licensing   
    You can receive the Identity Provisioning service free of charge in a bundle with an SAP cloud solution, for instance, SAP S/4HANA Cloud, SAP Marketing Cloud, SAP Sales Cloud, or SAP SuccessFactors. A complete listing of all available bundles is available either in the product documentation or from your SAP contact.  
    Each customer receives two Identity Provisioning tenants per region. You can use one of these tenants for testing purposes, the other for productive configuration and provisioning jobs. A tenant bundled with an SAP cloud product gets access to all source, target, and proxy systems relevant for this product. If you’ve purchased multiple SAP cloud products, all relevant systems are enabled for both of their tenants (i.e., in both Identity Provisioning administration consoles). As of October 2020, the Identity Provisioning service can no longer be purchased as a standalone product.
    

#### Creating Source and Target Systems

To create a new source system for the Identity Provisioning service, select the Source Systems menu item. Then, click the \+ Add button under the list of source systems, which is still empty in our example shown in [Figure 2.66](#02_004.html#f2.66).

[![Creating a Source System](bilderklein/klein02_066.png)](img-f2.66.html) 

**Figure 2.66**     Creating a Source System

Select the type of the source system and assign a freely selectable name for the system. In addition, you can specify a destination and enter a description. If you select a destination, this choice will be used for the technical communication with the source system, as shown in [Figure 2.67](#02_004.html#f2.67).

[![Specifying Source System Details](bilderklein/klein02_067.png)](img-f2.67.html) 

**Figure 2.67**     Specifying Source System Details

Let’s look at a possible configuration using the Identity Authentication service as a source system as an example. To use this service as a source system, you must create a technical user of type System with a password and a client ID. This user is used to authenticate REST API calls on the Identity Authentication tenant.

Then, create a source system of the Identity Authentication type. Maintain its properties with the values from [Table 2.1](#02_004.html#t2.1).

 
| Field || Value |
| --- | --- |
| Authentication || Basic authentication |
| --- | --- |
| Type || HTTP |
| URL || URL of your Identity Authentication tenant |
| Proxy Type || Internet |
| User || UUID of the technical user for the Identity Authentication tenant |
| Password || Password of the technical user |

**Table 2.1**     Properties for Using an Identity Authentication Tenant as a Source System

You can create a new target system under the Target Systems menu item. For this task, click on the \+ Add button below the list of target systems, which is still empty in our example shown in [Figure 2.68](#02_004.html#f2.68).

[![Creating a Target System](bilderklein/klein02_068.png)](img-f2.68.html) 

**Figure 2.68**     Creating a Target System

You must maintain the same properties for the target system as for the source system, as shown in [Figure 2.69](#02_004.html#f2.69).

In addition, you can select the source systems from which the identities are to be obtained. Maintain the properties for the system connection identically to the source system. The system-specific properties can be found in the documentation.

[![Maintaining Details of the Target System](bilderklein/klein02_069.png)](img-f2.69.html) 

**Figure 2.69**     Maintaining Details of the Target System

#### Configuring Transformations

Source and target systems typically use different data structures. Therefore, you must perform a mapping of these data structures. In the Identity Provisioning service, the mapping is performed in the form of transformations. The Identity Provisioning service processes the data in JavaScript Object Notation (JSON) format. After you configure and save a source system, a default transformation is created. This step converts the data from the source system, which is already in JSON format, into a generic JSON that is used by the Identity Provisioning service.

When identities are provided to the target system of provisioning, a transformation is again run through. This transformation converts the generic JSON into a JSON format that can be processed by the target system. The transformations can be customized on the side of the source system as well as on the side of the target system.

Provisioning is started on the side of the source systems. For provisioning, select the relevant source system again in the menu ribbon (shown earlier in [Figure 2.68](#02_004.html#f2.68)) under the Source Systems item. A job is executed for this purpose. You can execute this job manually or automatically. There are two different job types, as shown in [Figure 2.70](#02_004.html#f2.70):

*   Read Job
    
*   Resync Job
    

[![Scheduling an Identity Provisioning Job](bilderklein/klein02_070.png)](img-f2.70.html) 

**Figure 2.70**     Scheduling an Identity Provisioning Job

You can schedule a read job or start it manually. You can use the read job to perform the following operations:

*   Run Now  
    This operation allows you to start the job immediately. The job reads all identities from the source system and makes them available in the target system after the transformations have been performed. It only checks whether changes have been made to the identities in the source system. If you have made changes in the target system in the meantime, these changes will be overwritten by the job.
    
*   Schedule  
    This operation allows you to schedule the regular execution of the job. The smallest interval is 30 minutes. In this case, the read job is not started immediately, only after the set interval has elapsed.
    
*   Resume  
    This operation allows you to interrupt or resume running read jobs.
    

The resync job allows you to resynchronize the data in the target system when changes have been made in the source system. The only available operation for this job type is Run Now. This operation starts the resynchronization job immediately. An important difference to the read job is that changes you have made manually in the target system in the meantime are overwritten by the resync job.

###### \[ ! \]  Identity Provider and Bundle License for Identity Provisioning

The bundle licenses for the Identity Authentication and Identity Provisioning services are often limited to certain functions. For example, in a bundle with SAP SuccessFactors, only this solution can be used as the source system. Therefore, in SAP Help Portal ([http://s-prs.de/v809806](http://s-prs.de/v809806)), check whether the bundle licenses cover your requirements before deployment. For details on license models, see SAP Note 2717906.

## 2.5    SAP Cloud Identity Access Governance

SAP Cloud Identity Access Governance is a service package that enables you to centrally manage access risk and compliance for on-premise and cloud systems. With the services provided, you can reduce the complexity of role management and automatically detect unauthorized access.

The package contains the following services:

*   Access analysis service
    
*   Access request service
    
*   Role design service
    
*   Access certification
    
*   Privileged access management
    

The service package integrates well with other SAP BTP services, such as SAP Workflow Management with the business rules function. The services connect to target applications running either in the cloud or on-premise.

SAP Cloud Identity Access Governance version 2.0 is currently only available in SAP BTP, Cloud Foundry environment in Amazon Web Services (AWS) data centers.

The architecture of SAP Cloud Identity Access Governance and its interaction with other cloud services is shown in [Figure 2.71](#02_005.html#f2.71). The SAP Workflow Management service can be used in this context to automate access requests that go through the various stages of creation and approval. SAP Workflow Management and the integrated business rules feature allow you to embed flexible customizable business decisions into the workflow. The Identity Authentication service from the SAP Cloud Identity Services package is used to authenticate SAP Cloud Identity Access Governance users. The Identity Provisioning service is used in context to provision the users.

[![SAP Cloud Identity Access Governance: Architecture](bilderklein/klein02_071.png)](img-f2.71.html) 

**Figure 2.71**     SAP Cloud Identity Access Governance: Architecture

## 2.6    Checklist for General Security

[Table 2.2](#02_006.html#t2.2) provides a checklist of security topics in the context of SAP BTP. Check whether you have considered all the criteria listed here.

 
| Completed || Task |
| --- | --- |
|  || You have clarity about the domains to be used. |
| --- | --- |
|  || The certification body has been determined. |
|  || You’ve checked whether the certification authority exists as a root certificate in the standard SAP BTP truststore. Alternatively, a customer-specific truststore has been created. |
|  || Determinations have been made regarding destinations (i.e., at which levels which connections will be established). |
|  || Those responsible for the respective connections have been nominated. |
|  || A place to document destinations was agreed upon. |
|  || The expiration dates of certificates have been noted in a suitable format or calendar (for customer-owned certificates). |
|  || Security policies on passwords and two-factor authentication have been defined. |
|  || You’ve decided which identity provider would be used for which applications and subaccounts. |
|  || The use of an Identity Authentication tenant has been discussed and weighed. |
|  || Permissioning for cloud applications has been integrated into your company’s organization, and responsibilities have been defined. |
|  || You’ve clarified how monitoring and periodic attestations will be performed in the SAP BTP environment. |
|  || Emails and branding have been adapted so that users can identify the cloud applications as belonging to your company. In particular, the sender address of these emails was either adapted to a separate email server, or the SAP sender address was made known as secure in the email server. |
|  || When using web blockers in the browser, you’ve ensured that the applications are accessible in the cloud and that any security notices for external pages are not displayed. |
|  || You’ve determined from where accesses may be made and in which way. Based on this information, authentication rules were adapted or created. |
|  || You’ve clarified how users are provisioned, including whether to use the Identity Provisioning service. |

**Table 2.2**     SAP BTP: Security Checklist

## 2.7    Summary

In this chapter, you first learned about the basics of secure communication. Subsequently, we introduced you to the destination service in SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment, as well as discussed certificate handling. Then, we covered the basics of authentication, and you learned the difference between platform identity providers and application identity providers. Identity provider configuration was presented for both SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. Security is inevitably associated with authorizations. Therefore, we explained the basics relevant for SAP BTP but also differences between OAuth and SAML2. Then, we focused on SAP Cloud Identity Services, which consists of the Identity Authentication service and the Identity Provisioning service. Subsequently, we provided a brief overview of SAP Cloud Identity Access Governance. Finally, we closed this chapter with a general security checklist to provide a solid foundation for your own projects.

# 3    Configuring Security and Authorizations in the Neo Environment

SAP Business Technology Platform (SAP BTP), Neo environment is the older of the two environments for SAP BTP and, as a result, is subject to fewer changes today. Nevertheless, room for improvement always exists in the security and authorization area. Especially when running SAP BTP, Cloud Foundry environment and SAP BTP, Neo environment services and applications in parallel, an important step is to align the concepts of both platforms well.

In this chapter, we look at security-relevant aspects of SAP BTP, Neo environment. Although this SAP BTP environment will eventually be replaced by SAP BTP, Cloud Foundry environment, in the medium term, many SAP customers still have services from SAP BTP, Neo environment in use.

First, in [Section 3.1](#03_001.html#h3.1), we’ll introduce you to the SAP BTP, Neo environment command-line tool, which you can use as an alternative to the web interface to administer the environment. Then, in [Section 3.2](#03_002.html#h3.2), we’ll introduce you to user administration in SAP BTP, Neo environment. In [Section 3.3](#03_003.html#h3.3), we’ll show you how to perform a trust configuration, and during this process, we’ll go into greater depth explaining the functions of the local service provider, the platform identity provider, and the application-specific identity provider.

Then, in [Section 3.4](#03_004.html#h3.4), you’ll learn how to perform authorization management, and we’ll introduce you to relevant concepts. To work with subaccounts, a necessary step is to create a corresponding user and then to provide the user with the required permissions. We’ll show you how to create and manage users and roles. Assigning roles to users can require a lot of effort if you have a large number of users, both initially and during operations. We’ll therefore provide tips on grouping multiple roles and assigning them to users. We’ll also cover the concept of platform roles. You’ll learn about the function of platform roles and what you should pay attention to when creating customer-specific roles.

Once you’re familiar with the basic concepts, you can test your knowledge using the checklist in [Section 3.5](#03_005.html#h3.5). Doing so will ensure that you do not forget any important steps during security-relevant activities and that you can perform the associated activities more efficiently.

Finally, in [Section 3.6](#03_006.html#h3.6), you’ll learn how to implement two-factor authentication for subaccount admins and how to authenticate developers via Microsoft Azure Active Directory (Microsoft Azure AD) for SAP Web IDE through two practical scenarios.

## 3.1    Setting Up the Command Line for SAP BTP, Neo Environment

In the following sections, we’ll work with SAP BTP, Neo environment web interface. Alternatively, you can use the command line, which also provides a great deal of functionality. Therefore, in this section, we’ll briefly show you how to access the command line.

SAP offers the SAP BTP software development kit (SDK )) for the Neo environment for local development. Among other things, a console is delivered with the SAP BTP SDK, which is also called the command-line interface (CLI). To download the SDK, navigate to the CLOUD tab on the SAP Development Tools website ([https://tools.hana.ondemand.com/](https://tools.hana.ondemand.com/)). There, look for the SAP BTP SDK for the Neo environment and click on the download link for Java Web Tomcat 8, as shown in [Figure 3.1](#03_001.html#f3.1). Alternatively, a Tomcat 9 build is available as well.

[![SAP BTP, Neo Environment: Downloading the SAP BTP SDK](bilderklein/klein03_001.png)](img-f3.1.html) 

**Figure 3.1**     SAP BTP, Neo Environment: Downloading the SAP BTP SDK

###### \[»\]  Downloading the Latest Version

The version number shown in [Figure 3.1](#03_001.html#f3.1) reflects the most current version when the screenshot was taken. However, the version number does not play a decisive role for the console.

The SDK is delivered as a ZIP file. No distinction is made between different operating systems, such as Windows or macOS, because the SDK is based on Java. Unzip the ZIP file and navigate to the tools directory, as shown in [Figure 3.2](#03_001.html#f3.2). In that directory, you’ll find the neo.bat file (for computers running Windows) and the neo.sh file (for computers running macOS or Linux) to start the tools. Execute the appropriate file for your operating system.

[![File Structure of the Download Archive](bilderklein/klein03_002.png)](img-f3.2.html) 

**Figure 3.2**     File Structure of the Download Archive

Now, you can use the command line on your computer. A list of all commands for working with SAP BTP, Neo environment can be found in the environment’s documentation at [http://s-prs.de/v809804](http://s-prs.de/v809804). Navigate to Administrations and Operations, Neo Environment • Account Administration in the Neo Console Client • Console Client for the Neo Environment.

###### \[»\]  Setting a Proxy Server as an Environment Variable

In many organizations, a proxy server must be used to connect to the Internet. In this case, you must set the proxy as an environment variable in the operating system.

You can also display the available commands directly from the command line. For this task, use the command shown in [Listing 3.1](#03_001.html#l3.1), which shows the calls for macOS/Linux and Windows as examples. In the following sections, we’ll only use macOS/Linux commands.

```
## MacOS / Linux
./neo.sh help
 
## Windows
neo.bat help 
```

**Listing 3.1**     Getting the List of Available Commands from the CLI

Basically, all commands require authentication. For this purpose, you must always pass a subaccount in the form of the \-account parameter against which authentication is to be performed. In addition, you must supply a user.

###### \[»\]  Observing Identity Provider Settings

Note that the settings of the platform identity provider are used for the transferred subaccount. If you’ve configured the Identity Authentication service as a platform identity provider (see [Chapter 2](#02_001.html#h2), [Section 2.2.1](#02_002.html#h2.2.1)), you must authenticate with a user with access rights to this service. Otherwise, you can use an S-user provided by the SAP ID service.

For all commands, you must also supply the host, which is the data center where your subaccount is deployed. [Table 3.1](#03_001.html#t3.1) provides an overview of the host names of the available regions for SAP BTP, Neo environment.

 
| Region || Host |
| --- | --- |
| Australia (Sydney) || ap1.hana.ondemand.com |
| --- | --- |
| Brazil (São Paulo) || br1.hana.ondemand.com |
| Canada (Toronto) || ca1.hana.ondemand.com |
| Europe (Amsterdam) || eu3.hana.ondemand.com |
| Europe (Frankfurt) || eu2.hana.ondemand.com |
| Europe (Rot/Germany) || hana.ondemand.comeu1.hana.ondemand.com |
| Japan (Tokyo) || jp1.hana.ondemand.com |
| Kingdom of Saudi Arabia (Riyadh) || sa1.hana.ondemand.com |
| Russia (Moscow) || ru1.hana.ondemand.com |
| UAE (Dubai) || ae1.hana.ondemand.com |
| US East (Ashburn) || us1.hana.ondemand.com |
| US West (Chandler) || us2.hana.ondemand.com |
| US East (Sterling) || us3.hana.ondemand.com |
| US West (Colorado Springs) || us4.hana.ondemand.com |

**Table 3.1**     SAP BTP, Neo Environment: Regions and Host Names

For more information about using the SAP BTP, Neo environment command-line tool and an example of its use, see [Chapter 6](#06_001.html#h6), [Section 6.1](#06_001.html#h6.1) and [Section 6.5.1](#06_005.html#h6.5.1).

## 3.2    User Management

Managing users in SAP BTP, Neo environment plays a key role in security. You can manage business users, administrative users, and developers in numerous ways. Basically, a distinction must be made between global account users, subaccount users, and end users, with the following considerations in mind:

*   Global account level users are exclusively administrators who create subaccounts and assign resources to the subaccounts for use within the subaccount. In addition, support staff and auditors must be added as users at the global account level. These users are authenticated against the SAP ID service without exception. Typically, these users are S-users that you create in the service marketplace, which we describe later in this section.
    
*   Users at the subaccount level are created for administrators, developers, and support staff. The end users of the applications deployed in this subaccount are not created as subaccount users (members). The assignment of platform roles and application roles to these users is covered in [Section 3.4.1](#03_004.html#h3.4.1).
    
*   Application end users do not need any permissions in the subaccount. These users are maintained in the application identity provider and do not require platform roles, only application roles. These application roles are usually mapped to groups in the application identity provider.
    

A prerequisite for the direct mapping of users is that the corresponding user accounts must already be registered in the SAP ID service. If this requirement is not fulfilled, SAP Support Portal enables you to create S-users for your company.

To create S-users for global account users, you must log on to the [https://support.sap.com/](https://support.sap.com/) page with an S-user for your company. This user must have the appropriate user administration permissions. Then, proceed with the following steps:

1.  In the SAP Support Portal menu, select the Manage Users entry in the menu to jump to user maintenance, as shown in [Figure 3.3](#03_002.html#f3.3).
    
    [![SAP Support Portal Menu](bilderklein/klein03_003.png)](img-f3.3.html) 
    
    **Figure 3.3**     SAP Support Portal Menu
    
2.  You’re now in the user overview, as shown in [Figure 3.4](#03_002.html#f3.4).
    
    [![Creating a New S-User](bilderklein/klein03_004.png)](img-f3.4.html) 
    
    **Figure 3.4**     Creating a New S-User
    
    Click on the Request User button in the bottom toolbar to create a new user.
    
3.  In the creation dialog box, enter the details of the user, as shown in [Figure 3.5](#03_002.html#f3.5).
    
    [![Maintaining User Details](bilderklein/klein03_005.png)](img-f3.5.html) 
    
    **Figure 3.5**     Maintaining User Details
    
4.  Finish the creation process by clicking Submit.
    

The S-user is not created immediately since SAP must first confirm its creation, which can take up to 24 hours. SAP also assigns the S-user ID during this process. Once approved, the user will receive an invitation email with instructions on activating the user account.

Prerequisites for managing users at the subaccount level include, first, logging on to the subaccount and, second, having sufficient permissions for user management. You can create a subaccount starting from your global account as described in [Chapter 1](#01_001.html#h1), [Section 1.3.2](#01_003.html#h1.3.2). The user who created the subaccount is automatically assigned the administrator and developer roles for the subaccount. Initially, only this user has access to the subaccount.

To create additional users on the subaccount level, (which are called members), switch to the user administration screen. For this task, select the Members menu item in the SAP BTP cockpit, as shown in [Figure 3.6](#03_002.html#f3.6).

[![User Management Menu](bilderklein/klein03_006.png)](img-f3.6.html) 

**Figure 3.6**     User Management Menu

On the user overview screen, you’ll see all users currently assigned to the subaccount, as shown in [Figure 3.7](#03_002.html#f3.7). These users can be edited and deleted at this point. Only your own user cannot be deleted.

[![User Overview on the Subaccount Level](bilderklein/klein03_007.png)](img-f3.7.html) 

**Figure 3.7**     User Overview on the Subaccount Level

To add a new user to the subaccount, click on the Add Members button.

You can create up to 100 users at a time. In the User IDs field, specify the S-user ID(s) generated by the SAP ID service, as shown in [Figure 3.8](#03_002.html#f3.8). The system does not check whether these IDs actually exist, nor whether the corresponding users are assigned to your company’s user master data in SAP Support Portal. Therefore, check the IDs carefully; otherwise, people from outside your company might be granted access.

[![Adding Users](bilderklein/klein03_008.png)](img-f3.8.html) 

**Figure 3.8**     Adding Users

In the same dialog box, you can assign roles to users. You can either use the standard roles delivered by SAP or use self-defined roles. We’ll discuss roles in more detail in [Section 3.4.1](#03_004.html#h3.4.1).

After users have been successfully assigned, they will appear in the user overview with the note \-subaccount not visited yet- in the Name column, as shown in [Figure 3.9](#03_002.html#f3.9). Once a user has logged on to the subaccount for the first time, the name of the user maintained in the SAP ID service is used instead of this note.

[![New User in the User Overview](bilderklein/klein03_009.png)](img-f3.9.html) 

**Figure 3.9**     New User in the User Overview

###### \[»\]  Disadvantages of the SAP ID Service for User Authentication

Using the SAP ID service to authenticate the users of a subaccount has some disadvantages. For example, you cannot store a validity period for a user in the subaccount. You also have no way to lock or unlock a user directly in the subaccount. In [Section 3.3.2](#03_003.html#h3.3.2), we’ll show you how you can use the Identity Authentication service as an alternative way to authenticate users to remove these limitations.

On the user overview screen, you also have the option of viewing all changes made to users by clicking the History button. The change history for the subaccount used in this book is shown in [Figure 3.10](#03_002.html#f3.10).

[![Change History for the Users of a Subaccount](bilderklein/klein03_010.png)](img-f3.10.html) 

**Figure 3.10**     Change History for the Users of a Subaccount

How a user logs on to the subaccount depends on whether the SAP ID service is used for authentication or whether the Identity Authentication service takes on the role of platform identity provider for the subaccount. If the SAP ID service is used, users can log on with their user data via the URL [https://account.hana.ondemand.com/](https://account.hana.ondemand.com/). After successfully logging on, as a user, you’ll see an overview of all the global accounts to which you’re either directly assigned or in which you’re assigned at least via a subaccount, as shown in [Figure 3.11](#03_002.html#f3.11).

[![Overview of Global Accounts](bilderklein/klein03_011.png)](img-f3.11.html) 

**Figure 3.11**     Overview of Global Accounts

If you navigate to the SAP BTP cockpit of the global account, navigate to Subaccounts • System Landscape to call up the overview of all subaccounts to which you’re assigned, as shown in [Figure 3.12](#03_002.html#f3.12).

[![Overview of Subaccounts](bilderklein/klein03_012.png)](img-f3.12.html) 

**Figure 3.12**     Overview of Subaccounts

When a user has logged on to the subaccount for the first time, the user name is read and stored in the user overview of the subaccount, as shown in [Figure 3.13](#03_002.html#f3.13).

[![Subaccount User after First Logon](bilderklein/klein03_013.png)](img-f3.13.html) 

**Figure 3.13**     Subaccount User after First Logon

You can delete a user by clicking on the delete icon ![inline image](bilder/icon_loeschen.png)in the Actions column for a user’s entry, as shown in [Figure 3.14](#03_002.html#f3.14). This action is logged and can be viewed via the change history.

SAP BTP also offers the option of deleting more than one user at a time. For this task, select the desired users and then click the Delete button, as shown in [Figure 3.15](#03_002.html#f3.15). This action is logged just like the deletion of a single user and can be viewed via the change history.

[![Deleting an Individual User](bilderklein/klein03_014.png)](img-f3.14.html) 

**Figure 3.14**     Deleting an Individual User

[![Deleting Multiple Users](bilderklein/klein03_015.png)](img-f3.15.html) 

**Figure 3.15**     Deleting Multiple Users

## 3.3    Trust Configuration

In Security Assertion Markup Language (SAML) 2.0-based communication, a subaccount of SAP BTP always acts in the role of the service provider (see [Chapter 2](#02_001.html#h2), [Section 2.2.1](#02_002.html#h2.2.1)). Each subaccount represents a separate service provider. If you have a requirement to represent each of your applications by a separate service provider, you must therefore create and configure a separate subaccount for each application.

Using SAML 2.0 requires that a trust relationship (sometimes shortened to “trust”) be established between the service provider and the identity provider. The service provider is configured in the subaccount. For this task, navigate to Security • Trust in the SAP BTP cockpit. We’ll show you how to set up a local service provider in the next section.

You must also configure the identity provider. In addition to using the SAP ID service as an identity provider, which is activated in the standard system, the subaccount allows you to configure an application identity provider or a platform identity provider (see also [Chapter 2](#02_001.html#h2), [Section 2.2.1](#02_002.html#h2.2.1)). You’ll learn how to set up platform identity providers and application identity providers in [Section 3.3.2](#03_003.html#h3.3.2) and [Section 3.3.3](#03_003.html#h3.3.3), respectively.

### 3.3.1    Setting Up the Local Service Provider

The trust settings of the local service provider inherit the default configuration from SAP BTP. Among other things, in the trust settings, you’ll define that the SAP ID service is to be used as the identity provider. In the documentation for SAP BTP, Neo environment, you’ll find a note that this default setting should only be used for testing and for exploring the available scenarios. Therefore, for productive scenarios, you should configure a local service provider according to your requirements.

The Local Service Provider tab in the Trust configuration allows you to make the following settings, as shown in [Figure 3.16](#03_003.html#f3.16):

*   Configuration Type
    
*   Principal Propagation
    
*   Force Authentication
    

[![Local Service Provider Configuration](bilderklein/klein03_016.png)](img-f3.16.html) 

**Figure 3.16**     Local Service Provider Configuration

The Configuration Type field allows the following configuration types for the local service provider:

*   Default  
    With this setting, the trust settings of the local service provider inherit the default configuration from SAP BTP.
    
*   None  
    With this type, no trust settings are defined for the local service provider, and thus, the service provider does not participate in any identity federation scenario.
    
*   Custom  
    With this type, you can define a specific configuration for the local service provider that differs from the default configuration.
    

The Principal Propagation field allows you to control whether user identity information is shared between applications. You can select either Enabled or Disabled. Set the value to Enabled if you want to enable cross-application single sign-on (SSO). If you want to use SAP Web IDE for your developments, the Principal Propagation field must be set to Enabled, which is the SAP default.

With the Force Authentication field, you can force users to reauthenticate themselves when starting SAP BTP. If you’ve configured an SSO, this property does not apply at runtime. You can select either Enabled or Disabled for this field. By default, the value Default is set, which is equivalent to Disabled.

### 3.3.2    Setting Up the Platform Identity Provider

The only alternative platform identity provider that can be used is the Identity Authentication service that we introduced in [Chapter 2](#02_001.html#h2), [Section 2.4.1](#02_004.html#h2.4.1). This service allows you to authenticate the users of your subaccount. By default, the SAP ID service is set as the platform identity provider. To use your own instance of the Identity Authentication service, click the Use Identity Authentication Tenant link under the Platform Identity Provider tab on the Trust Management screen, as shown in [Figure 3.17](#03_003.html#f3.17).

[![Activating the Platform Identity Provider](bilderklein/klein03_017.png)](img-f3.17.html) 

**Figure 3.17**     Activating the Platform Identity Provider

Next, select an Identity Authentication tenant associated with your global account, as shown in [Figure 3.18](#03_003.html#f3.18), and click Save to save your selection.

[![Selecting an Identity Authentication Tenant](bilderklein/klein03_018.png)](img-f3.18.html) 

**Figure 3.18**     Selecting an Identity Authentication Tenant

A few seconds will be required to assign the tenant. This step establishes a trust relationship with the Identity Authentication service, and the subaccount is registered as an application in this service, where it can be further configured.

After the mapping has been successfully completed, the Identity Authentication service is visible on the Trust Management screen as a platform identity provider. From this screen, you can jump to the SAP BTP cockpit by clicking the Cockpit button, as shown in [Figure 3.19](#03_003.html#f3.19).

[![Identity Authentication Service Displayed as a Platform Identity Provider](bilderklein/klein03_019.png)](img-f3.19.html) 

**Figure 3.19**     Identity Authentication Service Displayed as a Platform Identity Provider

For users to be authenticated using the Identity Authentication service, they must be created in the Identity Authentication service, as described in [Chapter 2](#02_001.html#h2), [Section 2.4.1](#02_004.html#h2.4.1). This step allows authentication to be successfully performed, but access to the subaccount by these users is still not yet possible. Users must also be added as members to the list of subaccount users, as described in [Section 3.2](#03_002.html#h3.2).

Now, users can authenticate and access the subaccount. The subaccount is accessed in SAP BTP, Neo environment using the following URL:

https://account-<SubaccountName>.<Datacenter>.hana.ondemand.com/cockpit

After successful logon, you’ll see the list of global accounts, as shown in [Figure 3.20](#03_003.html#f3.20). From this list, you can jump to the desired subaccount, as described in [Section 3.2](#03_002.html#h3.2).

[![Identity Authentication Service: Overview of Global Accounts after Successful Logon](bilderklein/klein03_020.png)](img-f3.20.html) 

**Figure 3.20**     Identity Authentication Service: Overview of Global Accounts after Successful Logon

On the user overview screen in the subaccount, notice that the properties of your user have been filled with the data maintained in the Identity Authentication service, as shown in [Figure 3.21](#03_003.html#f3.21).

[![Identity Authentication Service: User Overview with User Data](bilderklein/klein03_021.png)](img-f3.21.html) 

**Figure 3.21**     Identity Authentication Service: User Overview with User Data

No further settings are required in the Identity Authentication tenant. However, you have the option of performing a more advanced configuration. For example, you might set up risk-based authentication, customize email templates to meet your needs, configure your own email server to send emails, or create your own theme for the Identity Authentication service logon screen.

Log on to the administration console for the Identity Authentication tenant and navigate to Applications & Resources • Applications.

Look for the technical name of the subaccount. You’ll find one or two entries. If you find two entries, the Identity Authentication tenant has been configured as both a platform identity provider and an application identity provider. When the tenant is enabled as a platform identity provider, the subaccount is created as a customer-owned application (custom application) named SAP Cloud Platform <technical name of subaccount> in the Identity Authentication tenant, as shown in [Figure 3.22](#03_003.html#f3.22).

[![Registered Subaccount in the Platform Identity Provider](bilderklein/klein03_022.png)](img-f3.22.html) 

**Figure 3.22**     Registered Subaccount in the Platform Identity Provider

The subaccount assumes the role of the service provider in the SAML context. In the Identity Authentication service, all service providers are managed as applications, so you’ll also find the subaccount on this screen, which allows you to configure each service provider that uses the Identity Authentication service differently.

Some advanced configuration options for the service provider are shown in [Figure 3.23](#03_003.html#f3.23). You can also maintain your own terms of use and privacy policies in different languages at this point, in addition to the advanced configurations mentioned earlier.

[![Service Provider: Advanced Configuration Options](bilderklein/klein03_023.png)](img-f3.23.html) 

**Figure 3.23**     Service Provider: Advanced Configuration Options

### 3.3.3    Setting Up the Application Identity Provider

The application identity provider provides the user base for applications in your SAP BTP subaccount. For example, you can use your existing corporate identity provider to authenticate users for your applications and services. This scenario is called identity federation. SAP BTP uses SAML 2.0 for this purpose.

You don’t have to limit yourself to a single application identity provider; you can use multiple identity providers. In such a case, make sure that all user identities are unique across all identity providers and that no user is available in more than one identity provider. Otherwise, security roles could be incorrectly assigned in the SAP BTP subaccount.

SAP BTP also offers the option of using the Identity Authentication tenant as an application identity provider. Its configuration requires a little effort:

1.  In the SAP BTP cockpit, navigate to the Trust Management screen and open the Application Identity Provider tab.
    
2.  Click on the Add Identity Authentication Tenant link, as shown in [Figure 3.24](#03_003.html#f3.24).
    
    [![Application Identity Provider Configuration](bilderklein/klein03_024.png)](img-f3.24.html) 
    
    **Figure 3.24**     Application Identity Provider Configuration
    
3.  Select the desired Identity Authentication tenant, as shown in [Figure 3.25](#03_003.html#f3.25).
    
    [![Selecting an Identity Authentication Tenant](bilderklein/klein03_025.png)](img-f3.25.html) 
    
    **Figure 3.25**     Selecting an Identity Authentication Tenant
    
4.  The configuration process takes a few seconds. Now, the Identity Authentication tenant is configured as the application identity provider for the subaccount, as shown in [Figure 3.26](#03_003.html#f3.26).
    

[![Identity Authentication Tenant as Application Identity Provider](bilderklein/klein03_026.png)](img-f3.26.html) 

**Figure 3.26**     Identity Authentication Tenant as Application Identity Provider

In the Identity Authentication tenant, the subaccount is created as a customer-owned application. This application has the name of the Identity Authentication tenant, as shown in [Figure 3.27](#03_003.html#f3.27). You can only tell that this application is the subaccount by the technical name embedded in the URL.

[![Subaccount in the Identity Authentication Tenant](bilderklein/klein03_027.png)](img-f3.27.html) 

**Figure 3.27**     Subaccount in the Identity Authentication Tenant

As an alternative to using the Identity Authentication tenant, you can use any SAML 2.0-based identity provider as the subaccount’s application identity provider. To establish a trust relationship between the subaccount in the SAML service provider role and the identity provider, it is necessary to exchange metadata between the two actors. First, export the metadata of the service provider. In SAP BTP, Neo environment, you need to perform these steps in Trust Management:

1.  Navigate to the Trust Management area in the SAP BTP cockpit.
    
2.  Open the Local Service Provider tab.
    
3.  Set the Configuration Type field to Custom, which is a prerequisite for downloading the metadata.
    
4.  Save the configuration.
    
5.  The Get Metadata link will appear, as shown in [Figure 3.28](#03_003.html#f3.28). Click on this link to download the metadata in the form of an XML file.
    
    [![Downloading Metadata for Establishing the Trust Relationship](bilderklein/klein03_028.png)](img-f3.28.html) 
    
    **Figure 3.28**     Downloading Metadata for Establishing the Trust Relationship
    
6.  The next step is to import the subaccount metadata into the identity provider. How this import is performed depends on the third-party identity provider you choose, so we won’t go into specifics in this book. We show you how to perform this step in [Section 3.6.2](#03_006.html#h3.6.2) using Microsoft Azure AD as an example.
    
7.  After the metadata has been imported, the specific configuration of the identity provider must be performed, which depends on the provider you choose. After that step, you can download the metadata from the identity provider.
    
8.  Importing the identity provider metadata into the subaccount is performed in Trust Management under the Application Identity Provider tab. Click the Add Trusted Identity Provider link, as shown in [Figure 3.29](#03_003.html#f3.29).
    
    [![Adding a Trusted Identity Provider](bilderklein/klein03_029.png)](img-f3.29.html) 
    
    **Figure 3.29**     Adding a Trusted Identity Provider
    
9.  In the Trusted Identity Provider dialog box, click the Browse button, as shown in [Figure 3.30](#03_003.html#f3.30), and select the metadata file of the identity provider on your local computer.
    
    [![Importing Identity Provider Metadata](bilderklein/klein03_030.png)](img-f3.30.html) 
    
    **Figure 3.30**     Importing Identity Provider Metadata
    
10.  Optionally, you can still configure the desired default values and mappings for attributes and groups of SAP BTP and identity provider users under the Attributes and Groups tabs.
     
11.  After you’ve saved your configuration, the selected identity provider can be used as the application identity provider.
     

###### \[»\]  Cloud Security Concept When Connecting the Identity Authentication Service

For cost reasons, maintaining users in a central directory and connecting them via the Identity Authentication service is the first choice.

However, considerations with regard to security must be addressed. For example, you must clarify how many incorrect logons in the cloud will result in a user being blocked from the company network. You should also consider not making administrative and normal accounts directly identifiable by their names. This discretion will make it much harder for hackers to target administrative accounts. Many organizations tie in their directory services via the Identity Authentication service. However, this setup requires a sound cloud security concept. Among other things, we strongly recommend two-factor authentication.

## 3.4    Authorization Management

In [Chapter 2](#02_001.html#h2), we introduced you to authentication and authorization. Identity providers can be used to authenticate users. Thus, a subaccount of SAP BTP does not perform authentication itself but instead delegates this task to an identity provider. As described earlier, this identity provider can be the SAP ID service managed by SAP, your Identity Authentication tenant, or the identity provider of a third-party provider.

Authorization, on the other hand, takes place directly in the subaccount. This process checks whether users have the necessary authorizations to perform a particular action.

### 3.4.1    Creating and Managing Roles

In SAP BTP, a distinction is made between application roles and platform roles regarding authorizations. Application roles are for activities in applications and subscribed services, while platform roles are for activities related to the administration of the subaccount.

#### Platform Roles

SAP delivers several predefined platform roles to authorize typical interactions with the platform. In addition, as a subaccount admin, you can combine different scopes to create a custom platform role that meets your individual requirements. Scopes are sets of permissions that define what activities users can perform in the subaccount and what platform resources they can access. A platform role is a collection of permissions, or scopes, that are managed by the platform at the subaccount level.

SAP includes the following predefined platform roles:

*   Administrator
    
*   Cloud connector admin
    
*   Developer
    
*   Support user
    
*   Application user admin
    

Predefined roles cannot be deleted or modified. If a role does not meet your requirements, you can copy it and make the desired adjustments. Alternatively, you can create a new role and add the desired permissions.

The administrator platform role authorizes you to perform the following tasks:

*   Manage subaccount users
    
*   Manage subscriptions, trust relationships, permissions, and OAuth settings
    
*   View and download heap dumps (memory images of the runtime environment)
    
*   Start and stop the SAP HANA service
    
*   View the Connectivity tab in the SAP BTP cockpit
    
*   Manage all authorizations of the developer role except for the debugging authorization
    

The cloud connector admin platform role authorizes you to perform the following tasks:

*   Open a secure tunnel in the cloud connector to connect your on-premise network and underlying systems to a subaccount of SAP BTP
    
*   Display the Connectivity tab in the SAP BTP cockpit
    

The developer platform role is assigned to newly created platform users by default and entitles you to perform the following tasks:

*   Deploy applications
    
*   Start and stop applications
    
*   Debug applications
    
*   Change log levels (i.e., the scope of logging for debugging applications)
    
*   Monitoring applications and their resource consumption
    

The support user platform role is designed for technical support and authorizes you to read subaccount-related data, such as metadata, configuration, and logs.

The application user admin platform role authorizes you to manage permissions for accessing HTML5 and Java applications at the application level and to manage permissions at the subscription level. This role does not authorize you to manage roles at the subaccount level nor to start, stop, or delete applications.

The administration of the platform roles is performed in the SAP BTP cockpit. In the cockpit, click on the Platform Roles entry in the menu to call up the administration environment for platform roles, as shown in [Figure 3.31](#03_004.html#f3.31).

[![Calling Up the Administration Environment for Platform Roles](bilderklein/klein03_031.png)](img-f3.31.html) 

**Figure 3.31**     Calling Up the Administration Environment for Platform Roles

Click on the New Platform Role button to create a new platform role, as shown in [Figure 3.32](#03_004.html#f3.32). Note that platform roles created in a subaccount of SAP BTP, Neo environment are available in all subaccounts created in the same global account and region. In other words, you cannot create a platform role that is visible only in one subaccount. A platform role can also be modified and deleted from other subaccounts.

[![Creating a Platform Role](bilderklein/klein03_032.png)](img-f3.32.html) 

**Figure 3.32**     Creating a Platform Role

In the dialog box for creating a new platform role, you must assign an ID. This ID is subject to certain restrictions and may not contain spaces, for example. The entry in the Display Name field is optional, but we recommend maintaining a meaningful display name in addition to the role ID, as shown in [Figure 3.33](#03_004.html#f3.33).

[![Creating a Platform Role: Additional Options](bilderklein/klein03_033.png)](img-f3.33.html) 

**Figure 3.33**     Creating a Platform Role: Additional Options

Finally, you must assign the desired scopes to the role. An overview of the available scopes can be found in the documentation for SAP BTP at [http://s-prs.de/v809805](http://s-prs.de/v809805). SAP provides scopes in the following categories:

*   Account management
    
*   Agent activation for Dynatrace service
    
*   Authorization management
    
*   Connectivity service
    
*   Document service
    
*   Enterprise messaging
    
*   Extension integration management
    
*   Git service
    
*   HTML5 application management
    
*   Java application lifecycle management
    
*   Keystore service
    
*   Logging service
    
*   Member management
    
*   Metering service
    
*   Monitoring service
    
*   Multitarget application (MTA) management
    
*   OAuth client management
    
*   Password storage
    
*   SAP HANA/SAP ASE service
    
*   Service management
    
*   Subscription management
    
*   Trust management
    
*   Virtual machines
    

After selecting the desired scopes, save your platform role settings by clicking the Save button.

###### \[+\]  Developing an Authorization Concept

We recommend that you define the roles you require as part of developing an authorization concept. In this process, you should determine whether the standard roles can fulfill your requirements. Note at this point that the standard administrator and developer roles have quite extensive authorizations. You cannot combine platform roles and application roles.

After creation, the custom platform role is displayed on the platform roles overview screen, as shown in [Figure 3.34](#03_004.html#f3.34). Unlike the predefined roles, no information icon ![inline image](bilder/icon_info.png)is displayed for a custom platform role. You would click this icon to jump to the documentation for predefined roles. While predefined roles cannot be edited or deleted, this restriction does not exist for custom roles, which can be edited, displayed, copied, or deleted using the icons in the Actions column.

[![Overview of Platform Roles](bilderklein/klein03_034.png)](img-f3.34.html) 

**Figure 3.34**     Overview of Platform Roles

The assignment of roles to users is performed via the user overview screen. For this task, navigate to the user overview screen via the Members menu item and click on the Edit icon ![inline image](bilder/icon_stift.png), as shown in [Figure 3.35](#03_004.html#f3.35), in the row of the user to whom you want to assign the role.

[![Editing a User](bilderklein/klein03_035.png)](img-f3.35.html) 

**Figure 3.35**     Editing a User

In the edit view for the user, all the available platform roles are listed. Select the roles you want to assign to the user (e.g., the custom role SAP Security Role we just created), as shown in [Figure 3.36](#03_004.html#f3.36).

[![Performing a Role Assignment](bilderklein/klein03_036.png)](img-f3.36.html) 

**Figure 3.36**     Performing a Role Assignment

No option for bulk editing exists, and thus, you must assign roles to each user individually. Note that determining all the users assigned to a role is not possible.

###### \[»\]  Assignment of Platform Roles

Which users should be assigned which platform roles depends on the use case. Developers and administrators are relatively easy to classify in this context. On a production subaccount, the cloud connector admin role is more likely to be assigned to a member of the Basis team; on a development subaccount, this role can also be assigned to developers.

#### Application Roles

Application roles are provided by various SAP BTP services, which are used to assign authorizations at the application level and have no effect on administrative activities in the SAP BTP subaccount.

###### \[»\]  Services, Subscriptions, and Applications

In the context of SAP BTP, we often talk about applications and subscriptions. The difference is easy to explain: A subscription runs in a different subaccount, called the provider account, and is designed to be used by the different subaccounts of various users, called consumer accounts. A subscription is a multiclient application that ensures that the data of individual consumers is strictly separated and isolated from each other. A subscription can be based on a Java application or on an HTML5 application.

Unlike a subscription, a service (in the form of an application) is provided directly in the customer’s subaccount. In simple terms, imagine that, when you activate a service, SAP installs the underlying application in your subaccount.

You can jump to the subscription management screen by navigating to Applications • Subscriptions, as shown in [Figure 3.37](#03_004.html#f3.37).

[![Subscriptions Menu](bilderklein/klein03_037.png)](img-f3.37.html) 

**Figure 3.37**     Subscriptions Menu

On the subscriptions overview screen, Java applications and HTML applications are displayed separately. A technical name is displayed for each application, as shown in [Figure 3.38](#03_004.html#f3.38). Click the name of an application in the Application column to jump to its details.

[![Overview of Subscriptions](bilderklein/klein03_038.png)](img-f3.38.html) 

**Figure 3.38**     Overview of Subscriptions

In the details of an application, you’ll find an overview of the application metadata. In addition, you can maintain destinations and roles at this point.

Select the Roles menu item to jump to the application role administration screen, as shown in [Figure 3.39](#03_004.html#f3.39).

[![Menu in the Detailed View of an Application](bilderklein/klein03_039.png)](img-f3.39.html) 

**Figure 3.39**     Menu in the Detailed View of an Application

As an example, let’s manage some roles for the SAP Cloud Portal service (the Java application nwc). When activating this application, whether it is a service or a subscription is not obvious. You can find this information in its documentation. The SAP Cloud Portal service is delivered in the form of a subscription and provides four predefined roles.

###### \[»\]  Customer-Specific Application Roles

Theoretically, you could also create customer-specific roles at this level, which may not make sense at first glance because permissions must be checked in the application and this is only done for predefined roles. However, if you take a closer look at the SAP Cloud Portal service, you’ll see that custom roles can also be quite useful for subscriptions.

You can assign either individual users or user groups to a role. Click the Assign button above the Individual Users table on the roles overview screen to start assigning an individual user, as shown in [Figure 3.40](#03_004.html#f3.40).

In the popup window that opens, you must manually maintain the User ID, as shown in [Figure 3.41](#03_004.html#f3.41). No value or search help is offered, and no check is made to ensure if a user with this ID actually exists. Since these are application roles, you also have the option of assigning users that are not listed in the user overview list for the subaccount. After you’ve entered a user ID, confirm the assignment by clicking Assign.

[![Overview of Roles on the Application Level](bilderklein/klein03_040.png)](img-f3.40.html) 

**Figure 3.40**     Overview of Roles on the Application Level

[![Assigning a User to an Application Role](bilderklein/klein03_041.png)](img-f3.41.html) 

**Figure 3.41**     Assigning a User to an Application Role

###### \[+\]  Using User Groups

We generally advise against assigning users directly to application roles in this way. If you have a large number of users, a lot of work may be required both for the initial setup of the application and during operations. Instead, we recommend using user groups, which we’ll discuss in more detail in [Section 3.4.2](#03_004.html#h3.4.2).

For consumers of a service, no major differences exist compared to role management at the subscription level. However, for SAP, as the operator of SAP BTP, a significant difference is in play: Subscriptions only need to be updated in the provider account (i.e., updates are applied at a central location). In the case of a service, on the other hand, updates must be applied to all customer subaccounts.

To jump to the role maintenance of a service, select the Services entry in the Applications menu area, as shown in [Figure 3.42](#03_004.html#f3.42). We’ll show you the role administration at this level in the following using the SAP Workflow Management service as an example. We have already activated this service. Click on the Workflow tile to jump to the service overview. If this tile is not visible in your subaccount, you should check whether you’ve licensed the service and assigned it to your subaccount at the global account level.

[![Service Overview on the Subaccount Level](bilderklein/klein03_042.png)](img-f3.42.html) 

**Figure 3.42**     Service Overview on the Subaccount Level

On the workflow service overview page, you’ll see the Take Action section, as shown in [Figure 3.43](#03_004.html#f3.43). Click the Configure Service link to jump to the configuration. Basically, this area is similar for all services, and you’ll always find a link to jump to the service configuration.

On the service configuration screen, select the Roles menu item to navigate to the role maintenance of the service.

[![Actions for a Service: Jumping to Configuration](bilderklein/klein03_043.png)](img-f3.43.html) 

**Figure 3.43**     Actions for a Service: Jumping to Configuration

As with subscriptions, you can assign either individual users or groups to a role. For this task, first select the desired role and then click the Assign button in the Individual Users area, as shown in [Figure 3.44](#03_004.html#f3.44). Then, you must enter the user ID of the user. No option exists for mass assignment; you must assign each user individually. Therefore, we recommend creating user groups for this purpose as well. On this screen, too, you have the option of creating customer-specific roles.

[![Application Role User Assignment](bilderklein/klein03_044.png)](img-f3.44.html) 

**Figure 3.44**     Application Role User Assignment

For application roles, you can assign a role to a user via authorization management at the subaccount level. This option does not exist for platform roles. Up to now, we’ve only covered the reverse way, in which a user is assigned to a role. Access the Authorization Management via the menu path Security • Authorizations, as shown in [Figure 3.45](#03_004.html#f3.45).

[![Jumping to Authorization Management in the Menu](bilderklein/klein03_045.png)](img-f3.45.html) 

**Figure 3.45**     Jumping to Authorization Management in the Menu

Now, you can search for users. For this task, enter a user ID in the User input field and then click on the Show Assignments button, as shown in [Figure 3.46](#03_004.html#f3.46). You’ll now see a list of all roles assigned to this user. Click the Assign button to assign a new role to the user.

[![Assigned Roles in Authorization Management](bilderklein/klein03_046.png)](img-f3.46.html) 

**Figure 3.46**     Assigned Roles in Authorization Management

Role assignment occurs on three levels. First, you must select the subaccount. Then, you must specify the application on the second level, followed by the role on the third level. Save the assignment by clicking the Save button. As shown in [Figure 3.47](#03_004.html#f3.47), we’ve assigned the WorkflowDeveloper role for the bpmworkflowruntime application to the user in the bpm subaccount.

[![Role Assignment in Authorization Management](bilderklein/klein03_047.png)](img-f3.47.html) 

**Figure 3.47**     Role Assignment in Authorization Management

At this point, note that the workflow service is also provided as a subscription, even though it is not visible in either the Java application overview or among the HTML5 applications. Services basically run in the same subaccount. Since the workflow service is provided in the bpm subaccount, this service must be a subscription.

After you’ve completed the role assignment settings, the new role is visible in the user’s role overview list, as shown in [Figure 3.48](#03_004.html#f3.48). If you want to unassign the role, click the Unassign button next to the desired role.

[![Deleting a Role Assignment](bilderklein/klein03_048.png)](img-f3.48.html) 

**Figure 3.48**     Deleting a Role Assignment

The deletion of the role assignment must be confirmed in a dialog box.

###### \[»\]  Authorization Concept for Cloud and On-Premise Systems

Make sure that the permissions assigned for the cloud and for your local authorization concept match. For example, someone who is allowed to maintain users in the cloud should also be allowed in on-premise systems, and vice versa.

### 3.4.2    Creating and Managing User Groups

You can use user groups to simplify role assignments. You do not assign roles to individual users, but to a group. You can then assign individual users to the group, which thus allows you to make assignments and changes to authorizations from a central point.

Groups also offer an advantage in combination with application-specific identity providers: You have the option of using groups in mapping rules and can thus assign groups dynamically at runtime based on attributes supplied in the SAML assertion. We’ll show you this procedure using an example in [Section 3.6.2](#03_006.html#h3.6.2).

To create a new user group, follow these steps:

1.  Navigate to Authorization Management via the menu path Security • Authorizations.
    
2.  Open the Groups tab and click the New Group button, as shown in [Figure 3.49](#03_004.html#f3.49).
    
    [![Creating a New Group](bilderklein/klein03_049.png)](img-f3.49.html) 
    
    **Figure 3.49**     Creating a New Group
    
3.  Assign a name for the group, as shown in [Figure 3.50](#03_004.html#f3.50). You should use a descriptive name and make sure that the name is unique. Groups are created exclusively in the respective subaccount.
    
    [![Maintaining Group Names](bilderklein/klein03_050.png)](img-f3.50.html) 
    
    **Figure 3.50**     Maintaining Group Names
    
4.  Save the group by clicking the Save button.
    

After the group has been created, you’ll see it on the group overview screen. On this screen, you can also assign roles or individual users to the group. Simply click on the Assign button above the Roles or Individual Users tables, as shown in [Figure 3.51](#03_004.html#f3.51).

[![Assigning Roles and Users](bilderklein/klein03_051.png)](img-f3.51.html) 

**Figure 3.51**     Assigning Roles and Users

The assignment of roles is shown in [Figure 3.52](#03_004.html#f3.52). We discussed this dialog box earlier in [Section 3.4.1](#03_004.html#h3.4.1). In this case, too, you’ll select a subaccount, an application, and a role to assign to the group and then save your selections by clicking the Save button.

[![Assigning a Role to a Group](bilderklein/klein03_052.png)](img-f3.52.html) 

**Figure 3.52**     Assigning a Role to a Group

Assigning a user to a group is shown in [Figure 3.53](#03_004.html#f3.53). The dialog box is identical to the dialog box for assigning a user to an application role. Again, enter the user ID and click Save.

[![Assigning a User to a Group](bilderklein/klein03_053.png)](img-f3.53.html) 

**Figure 3.53**     Assigning a User to a Group

After you’ve assigned the desired users and roles to a group, this information is visible on the group overview screen in the Roles and Individual Users tables, as shown in [Figure 3.54](#03_004.html#f3.54). For this task, select the group in the upper area of the group overview. If necessary, you can delete the assignment of a role or a user by clicking the Unassign button in the corresponding row.

[![Result of Assigning Role and User](bilderklein/klein03_054.png)](img-f3.54.html) 

**Figure 3.54**     Result of Assigning Role and User

The group assignment is also visible at the service level. After you’ve assigned the WorkflowDeveloper role to the SAP\_Security\_Book group for the workflow service, you’ll see the role on the role overview screen of the workflow service, in the Groups table, as shown in [Figure 3.55](#03_004.html#f3.55). The user assignment to the group is not visible at this point.

[![Checking Group Assignments in the Service](bilderklein/klein03_055.png)](img-f3.55.html) 

**Figure 3.55**     Checking Group Assignments in the Service

## 3.5    Checklist for Security and Permissions in SAP BTP, Neo Environment

[Table 3.2](#03_005.html#t3.2) provides a checklist for permissions and entitlement management in SAP BTP, Neo environment.

 
| Completed || Task |
| --- | --- |
|  || You have an overview of the different data centers for SAP BTP, Cloud Foundry environment and SAP BTP, Neo environment, and have noted the servers used in a central location. |
| --- | --- |
|  || You’ve determined which authentication method to use. Specific authentication processes can be set up for applications running in subaccounts in SAP BTP, Neo environment. This option is particularly useful if these applications are shared with a separate group of people, including externally managed identities, for example. |
|  || You’ve delimited your subaccounts from other subaccounts. This step is particularly important when connecting on-premise systems via the cloud connector (see [Chapter 5](#05_001.html#h5)) because, in this case, you can only set up permissions for the connected development systems on the development subaccount. |
|  || You’ve specified where the use of identity providers is documented and how many identity providers you want to use. |
|  || You’ve ensured that only a restricted group of users can make changes to the production configuration of the identity providers. |
|  || The cloud security concept has been coordinated and is coherent with the local security concept. Pay particular attention to which (all?) of your company’s users can log on to the cloud applications. |
|  || You’ve ensured that the platform roles match the user roles in other systems on an application-by-application basis. User roles should be aligned. |

**Table 3.2**     Security and Permissions Checklist for SAP BTP, Neo Environment

## 3.6    Real-World Examples of User and Authorization Management

In this section, we’ll show you how to solve common user management and authorization management tasks in SAP BTP, Neo environment using two concrete real-world use cases. In the first example, you’ll learn how to set up two-factor authentication for administration users in the Identity Authentication service. In this case, this service acts as a platform identity provider. In the second example, you’ll set up Microsoft Azure AD as an application identity provider. From an attribute in the Microsoft Azure AD user master data, you’ll derive a role in SAP BTP that authorizes access to SAP Web IDE.

### 3.6.1    Two-Factor Authentication of Subaccount Admins Using the Platform Identity Provider

We’ve encountered the scenario described in this section in several projects. Therefore, we want to show you the configuration step by step. A typical requirement in many companies is to implement twofactor or multifactor authentication for certain user groups, such as administrators. In many cases, this security is required because these user groups can access the configuration of critical infrastructure components. This concern is not only true in the on-premise world, but also in the cloud and thus in SAP BTP.

This requirement cannot be solved with the SAP ID service in its role as platform identity provider. You must use the Identity Authentication service as the platform identity provider. (We described its configuration in [Chapter 2](#02_001.html#h2), [Section 2.4.1](#02_004.html#h2.4.1).) At this point, we’ll show you the steps required to enable two-factor authentication.

We assume that you’ve already set up the Identity Authentication service as an identity provider. For this task, you must enable the SAP Platform Identity Provider service for SAP BTP, which is disabled by default. You must also enable the Identity Authentication tenant as a platform identity provider in the trust management of the subaccount.

Let’s start by configuring two-factor authentication in the Identity Authentication service by following these steps:

1.  First, navigate to Trust Management in the subaccount.
    
2.  Open the Platform Identity Provider tab and click the Administration Console button.
    
3.  Log on to the Identity Authentication service with an administration user and navigate to Applications & Resources • Applications.
    
4.  Search for the appropriate application based on the technical name of the subaccount. If you get two matches, as in [Figure 3.56](#03_006.html#f3.56), the service is used both as an application identity provider and platform identity provider. The application whose name is composed of SAP Cloud Platform and the technical subaccount name corresponds to the platform identity provider.
    
    [![Applications for Subaccount Identity Providers](bilderklein/klein03_056.png)](img-f3.56.html) 
    
    **Figure 3.56**     Applications for Subaccount Identity Providers
    
5.  The configuration of the application identity provider and the platform identity provider are performed independently. First, click on the application of the platform identity provider.
    
6.  In the application details, switch to the Authentication and Access tab and click on Risk-Based Authentication, as shown in [Figure 3.57](#03_006.html#f3.57).
    
7.  Any number of authentication rules may exist, and one default rule will appear. The default rule is applied if no other rule applies. In our example shown in [Figure 3.58](#03_006.html#f3.58), the Allow action is set for the default rule, which means that no further restrictions apply and additional authentication is not required for all users to whom this rule applies.
    
    [![Invoking Settings for Risk-Based Authentication](bilderklein/klein03_057.png)](img-f3.57.html) 
    
    **Figure 3.57**     Invoking Settings for Risk-Based Authentication
    
    [![Creating Authentication Rules](bilderklein/klein03_058.png)](img-f3.58.html) 
    
    **Figure 3.58**     Creating Authentication Rules
    
8.  Click the Add Rule button to create a new rule.
    
9.  In the creation dialog box, we’ll set up a time-based one-time password (TOTP) for two-factor authentication. Select the TOTP Two Factor Authentication option in the Action dropdown list. In our example, we want this rule to apply to all users assigned to Identity Authentication of a specific user group.
    
10.  Select the Cloud Group option and open the input help in the field below, as shown in [Figure 3.59](#03_006.html#f3.59).
     
     [![Configuring Risk-Based Authentication](bilderklein/klein03_059.png)](img-f3.59.html) 
     
     **Figure 3.59**     Configuring Risk-Based Authentication
     
11.  In the dialog box that opens, select the SubAccount\_Admin group, as shown in [Figure 3.60](#03_006.html#f3.60). This user group was created in preparation for this exercise. (You learned how to create user groups earlier in [Section 3.4.2](#03_004.html#h3.4.2).)
     
     [![Selecting a User Group](bilderklein/klein03_060.png)](img-f3.60.html) 
     
     **Figure 3.60**     Selecting a User Group
     
12.  Finally, confirm your settings by clicking OK.
     

The authentication rule will now be added to the rule hierarchy, as shown in [Figure 3.61](#03_006.html#f3.61). If you’ve defined multiple rules, click the arrow buttons in the Priority column to change the prioritization of these rules. The rule discovery process is aborted as soon as a matching rule is found. The rules are processed from top to bottom; the rule at the top of the list is applied first, and the rule at the bottom of the list is applied last.

[![Authentication Rules](bilderklein/klein03_061.png)](img-f3.61.html) 

**Figure 3.61**     Authentication Rules

###### \[»\]  Additional Authentication Rules

Risk-based authentication enables a great deal of flexibility. The configuration we described can be done in a similar way for the application identity provider.

To enable you to test the configuration, assign the SubAccount\_Admin group to your user. For this task, navigate to the user’s detail view, select User Groups, and then click the Assign Groups button, as shown in [Figure 3.62](#03_006.html#f3.62).

[![Assigning User Groups](bilderklein/klein03_062.png)](img-f3.62.html) 

**Figure 3.62**     Assigning User Groups

Select the user group that is typically used and then click the Save button, as shown in [Figure 3.63](#03_006.html#f3.63).

[![Selecting a User Group](bilderklein/klein03_063.png)](img-f3.63.html) 

**Figure 3.63**     Selecting a User Group

Now, let’s assign the subaccount user. For this task, switch back to the SAP BTP cockpit of the subaccount. Navigate to Member Management and add the user IDs from the Identity Authentication service to the list of users. Make sure you’ve selected the correct User Base, as shown in [Figure 3.64](#03_006.html#f3.64).

[![Assigning Users to a Subaccount](bilderklein/klein03_064.png)](img-f3.64.html) 

**Figure 3.64**     Assigning Users to a Subaccount

###### \[»\]  Duplicate User Maintenance in the Identity Authentication Service and Subaccount

The Identity Authentication service is responsible for authenticating users in the role of SAML identity provider. The service manages all users centrally and across service providers. However, the service provider cannot access this user base. It only receives a SAML ticket in which user identities and group memberships in the Identity Authentication service are passed as information. Therefore, the users must be created in advance in the service provider, as well as in the platform identity provider, to assign them the appropriate platform roles.

In the next step, let’s test our configuration of two-factor authentication. For this task, in Trust Management , under the Platform Identity Provider tab, click the Cockpit button. You’ll be prompted to authenticate with user credentials from the Identity Authentication service user base, as shown in [Figure 3.65](#03_006.html#f3.65).

[![Logging on with an Identity Authentication User](bilderklein/klein03_065.png)](img-f3.65.html) 

**Figure 3.65**     Logging on with an Identity Authentication User

After a user has been successfully authenticated, the Identity Authentication service forwards the user data for two-factor authentication. As we’ve configured, the TOTP method is used for this. In other words, the administrator who wants to log on must read the displayed QR code with an authenticator app and enter the displayed security code in the logon screen, as shown in [Figure 3.66](#03_006.html#f3.66). Different apps can be used for authentication. For our example, we chose Microsoft Authenticator. In principle, SAP Authenticator and other apps would also work.

[![Two-Factor Authentication](bilderklein/klein03_066.png)](img-f3.66.html) 

**Figure 3.66**     Two-Factor Authentication

After the security code has been successfully verified, the administrator is taken to the global account. Now, the administrator can jump to a subaccount.

### 3.6.2    Authenticating SAP Web IDE Users via Microsoft Azure AD

In the next scenario, we’ll look at how a third-party or external identity provider can be used as an application identity provider directly from the subaccount. With Microsoft Azure AD in the role of SAML 2.0 identity provider, you can use a common tool. The aim of our sample configuration is to enable developers to authenticate themselves against Microsoft Azure AD to use SAP Web IDE. Alternatively, you could use the Identity Authentication service as a proxy to the third-party identity provider.

First, you should check whether SAP Web IDE has already been activated in your subaccount. For this task, navigate to the Services area in the subaccount and search for “Web IDE.” If the status Enabled is not displayed on its tile, as shown in [Figure 3.67](#03_006.html#f3.67), you must jump to the details screen by clicking on the tile and then activate the service.

[![Checking the Activation Status of SAP Web IDE](bilderklein/klein03_067.png)](img-f3.67.html) 

**Figure 3.67**     Checking the Activation Status of SAP Web IDE

As explained earlier in [Section 3.3](#03_003.html#h3.3), in SAML 2.0 scenarios, a trust relationship must be established between the service provider and the identity provider. In our case, the service provider is the SAP BTP subaccount. The mutual import of metadata is required to establish the trust relationship, which can be achieved by following these steps:

1.  In the subaccount, navigate to Trust Management in the Security menu area.
    
2.  Under the Local Service Provider tab, check that the Custom configuration type has been selected and that Principal Propagation has been enabled (Enabled).
    
3.  Click the Get Metadata button to start downloading the metadata in the form of an XML file, as shown in [Figure 3.68](#03_006.html#f3.68).
    

[![Downloading the Metadata for the Service Provider](bilderklein/klein03_068.png)](img-f3.68.html) 

**Figure 3.68**     Downloading the Metadata for the Service Provider

Now, we’re ready to configure Microsoft Azure AD:

1.  Log on to [https://portal.azure.com](https://portal.azure.com) on the Microsoft Azure platform, as shown in [Figure 3.69](#03_006.html#f3.69). You can also implement this scenario with a trial account.
    
2.  On the homepage, in the Azure services section, select Azure AD Domain…, as shown in [Figure 3.70](#03_006.html#f3.70).
    
    [![Logging on to Microsoft Azure](bilderklein/klein03_069.png)](img-f3.69.html) 
    
    **Figure 3.69**     Logging on to Microsoft Azure
    
    [![Microsoft Azure AD](bilderklein/klein03_070.png)](img-f3.70.html) 
    
    **Figure 3.70**     Microsoft Azure AD
    
3.  In the side menu, select the Enterprise applications option, as shown in [Figure 3.71](#03_006.html#f3.71). On this overview screen, you’ll configure the necessary service providers.
    
    [![Jumping to Enterprise Applications](bilderklein/klein03_071.png)](img-f3.71.html) 
    
    **Figure 3.71**     Jumping to Enterprise Applications
    
4.  You must now create a new application. Click on the \+ New application button, as shown in [Figure 3.72](#03_006.html#f3.72).
    
    [![Creating a New Application](bilderklein/klein03_072.png)](img-f3.72.html) 
    
    **Figure 3.72**     Creating a New Application
    
5.  As shown in [Figure 3.73](#03_006.html#f3.73), more than 3,700 predefined systems can be registered as service providers. Search for the term “SAP.” From the list of results, click on SAP Cloud Platform.
    
    [![Adding SAP BTP as a Service Provider](bilderklein/klein03_073.png)](img-f3.73.html) 
    
    **Figure 3.73**     Adding SAP BTP as a Service Provider
    
6.  In the dialog box on the right, confirm the creation of the service provider by clicking the Add button, as shown in [Figure 3.74](#03_006.html#f3.74).
    
    At this point, you have the option of customizing the name of the service provider. We recommend that you use descriptive names.
    
    [![Confirming a Service Provider](bilderklein/klein03_074.png)](img-f3.74.html) 
    
    **Figure 3.74**     Confirming a Service Provider
    
7.  A few seconds is required for this process to complete. The progress is displayed in the upper-right pane, as shown in [Figure 3.75](#03_006.html#f3.75).
    
    [![Application Status](bilderklein/klein03_075.png)](img-f3.75.html) 
    
    **Figure 3.75**     Application Status
    
8.  After the service provider has been successfully created, you can jump to the details to start the configuration of SSO by clicking on the Set up single sign on tile, as shown in [Figure 3.76](#03_006.html#f3.76).
    
9.  In the next step, the SSO method must be selected. We’ll use the SAML option for this example, as shown in [Figure 3.77](#03_006.html#f3.77).
    
    [![Setting Up SSO](bilderklein/klein03_076.png)](img-f3.76.html) 
    
    **Figure 3.76**     Setting Up SSO
    
    [![Selecting SAML as the SSO Method](bilderklein/klein03_077.png)](img-f3.77.html) 
    
    **Figure 3.77**     Selecting SAML as the SSO Method
    
10.  Now, upload the metadata of the service provider by clicking Upload metadata file, as shown in [Figure 3.78](#03_006.html#f3.78).
     
     [![Uploading the Metadata of the Service Provider](bilderklein/klein03_078.png)](img-f3.78.html) 
     
     **Figure 3.78**     Uploading the Metadata of the Service Provider
     
11.  In the following dialog box, select the metadata file previously exported from the subaccount.
     
12.  Basic information for the connection is already included in the metadata document. You only need to maintain the Sign on URL parameter, as shown in [Figure 3.79](#03_006.html#f3.79). In our example, we used the SAP Web IDE endpoint.
     
     [![Maintaining the Logon URL for the SAP BTP Service](bilderklein/klein03_079.png)](img-f3.79.html) 
     
     **Figure 3.79**     Maintaining the Logon URL for the SAP BTP Service
     
13.  Finally, click on the Save button. This step will take you back to the service provider details.
     
14.  Now, we’ll adapt the SAML attributes to our requirements. For this task, click Edit in the Attributes & Claims area, as shown in [Figure 3.80](#03_006.html#f3.80).
     
     [![Editing SAML Attributes](bilderklein/klein03_080.png)](img-f3.80.html) 
     
     **Figure 3.80**     Editing SAML Attributes
     
15.  Customize the user identifier used in the SAML assertion. By default, the userprincipalname attribute is used. However, for our purposes, we want to use the user’s email address. For this task, click the Unique User Identifier entry in the Required claim area, as shown in [Figure 3.81](#03_006.html#f3.81).
     
     [![Customizing a User Identifier](bilderklein/klein03_081.png)](img-f3.81.html) 
     
     **Figure 3.81**     Customizing a User Identifier
     
16.  In the Source attribute dropdown list, select user.mail and save the change, as shown in [Figure 3.82](#03_006.html#f3.82).
     
     [![Changing a Source Attribute](bilderklein/klein03_082.png)](img-f3.82.html) 
     
     **Figure 3.82**     Changing a Source Attribute
     
17.  In this scenario, we’ll query the user’s department to determine whether the user is allowed to start SAP Web IDE. For this task, include the Department attribute as a claim in the SAML assertion. Click Add new claim in the Attributes & Claims area, as shown in [Figure 3.83](#03_006.html#f3.83).
     
     [![Adding a New Claim](bilderklein/klein03_083.png)](img-f3.83.html) 
     
     **Figure 3.83**     Adding a New Claim
     
18.  In the Name field, enter “Department” for department and select user.department in the Source attribute dropdown list, as shown in [Figure 3.84](#03_006.html#f3.84). This step will specify that the value of the user.department attribute will be copied to the claim named Department.
     
     [![Creating a Claim](bilderklein/klein03_084.png)](img-f3.84.html) 
     
     **Figure 3.84**     Creating a Claim
     
19.  Save the claim.
     
20.  On the service provider overview screen, navigate to the SAML Signing Certificate section. Now, in the Federation Metadata XML row, click the Download link to download the metadata, as shown in [Figure 3.85](#03_006.html#f3.85).
     

[![Downloading the Service Provider Metadata](bilderklein/klein03_085.png)](img-f3.85.html) 

**Figure 3.85**     Downloading the Service Provider Metadata

You now must add the desired user(s) to Microsoft Azure AD as the service provider. For this task, click on the Users and Groups menu item in Microsoft Azure AD. Then, click Add User/Group and select the desired user.

As a final step, you must configure Microsoft Azure AD as an application identity provider in the SAP BTP subaccount. For this task, navigate to Trust Management as usual, open the Application Identity Provider tab, and click the Add Trusted Identity Provider link, as shown in [Figure 3.86](#03_006.html#f3.86).

Next, import the Microsoft Azure AD metadata. For this task, click the Browse button. Select the XML file that was previously exported from Microsoft Azure AD, as shown in [Figure 3.87](#03_006.html#f3.87).

[![Adding a Trusted Identity Provider](bilderklein/klein03_086.png)](img-f3.86.html) 

**Figure 3.86**     Adding a Trusted Identity Provider

[![Importing Trusted Identity Provider Metadata](bilderklein/klein03_087.png)](img-f3.87.html) 

**Figure 3.87**     Importing Trusted Identity Provider Metadata

You’ll now need to make some adjustments since some values are not prepopulated by Microsoft Azure. Change the value of Assertion Consumer Service dropdown list to Assertion Consumer Service to correctly capture SAP BTP as a service. In the Signature Algorithm dropdown list, select SHA-256, which may be the current default value. Verify that the Enabled checkbox has been selected, as shown in [Figure 3.88](#03_006.html#f3.88).

[![Setting the Trusted Identity Provider](bilderklein/klein03_088.png)](img-f3.88.html) 

**Figure 3.88**     Setting the Trusted Identity Provider

Next, you’ll need to map the attributes of the SAML assertion to what are called principal attributes (i.e., the user attributes in SAP BTP). The term “principal” in this context refers to the user and is the term used in the SAML specification. For this task, switch to the Attributes tab and click the Add Assertion-Based Attribute link, as shown in [Figure 3.89](#03_006.html#f3.89). Maintain the values as listed in [Table 3.3](#03_006.html#t3.3).

[![Adopting Assertion Attributes](bilderklein/klein03_089.png)](img-f3.89.html) 

**Figure 3.89**     Adopting Assertion Attributes

 
| Assertion Attributes || Principal Attributes |
| --- | --- |
| http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname || firstName |
| --- | --- |
| http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress || email |
| http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname || lastName |

**Table 3.3**     Mapping the SAML Assertion Attributes

As mentioned earlier, we’ll derive the authorization to start SAP Web IDE from the employee’s department. Under the Groups tab, click the Add Assertion-Based Group link to define an appropriate user group. In the Group field, select the SAP\_BTP\_Security\_Book group that we created in [Section 3.4.2](#03_004.html#h3.4.2). In the Mapping Rules field, specify the value “Department,” then select the equals operation in the next dropdown list, and enter the value “Development” for the development department, as shown in [Figure 3.90](#03_006.html#f3.90). Save the configuration of the identity provider.

[![Deriving User Groups from Assertion Attributes](bilderklein/klein03_090.png)](img-f3.90.html) 

**Figure 3.90**     Deriving User Groups from Assertion Attributes

Now, set the identity provider we just created as the default identity provider. For this task, under the Application Identity Provider tab, click the radio button in the Default column in the corresponding row, as shown in [Figure 3.91](#03_006.html#f3.91).

[![Selecting Microsoft Azure AD as the Default Identity Provider](bilderklein/klein03_091.png)](img-f3.91.html) 

**Figure 3.91**     Selecting Microsoft Azure AD as the Default Identity Provider

Now, add a role with permissions to start SAP Web IDE to the SAP\_BTP\_Security\_Book group. For this task, navigate to the user group maintenance as usual and select the group in the list. Then, click the Assign button in the Roles area, as shown in [Figure 3.92](#03_006.html#f3.92).

[![Assigning a Role in Group Maintenance](bilderklein/klein03_092.png)](img-f3.92.html) 

**Figure 3.92**     Assigning a Role in Group Maintenance

In the role assignment dialog box, select the sapwebide EU2 subaccount, the di application, and the DiDeveloper role, as shown in [Figure 3.93](#03_006.html#f3.93). This role is predefined to obtain developer rights for the SAP Web IDE application. Save your assignment.

[![Selecting the DiDeveloper Role](bilderklein/klein03_093.png)](img-f3.93.html) 

**Figure 3.93**     Selecting the DiDeveloper Role

You can now test the configuration of the identity provider by calling SAP Web IDE. For this task, jump down to SAP Web IDE in the service overview and click the Go to Service link, as shown in [Figure 3.94](#03_006.html#f3.94).

[![Launching SAP Web IDE](bilderklein/klein03_094.png)](img-f3.94.html) 

**Figure 3.94**     Launching SAP Web IDE

You’ll be redirected to Microsoft Azure AD and will need to authenticate with your Microsoft credentials, as shown in [Figure 3.95](#03_006.html#f3.95). If authentication does not work, check that the development department has been correctly maintained for your user in the Microsoft Azure AD user master.

[![Logging on Using Microsoft Azure AD as the Identity Provider](bilderklein/klein03_095.png)](img-f3.95.html) 

**Figure 3.95**     Logging on Using Microsoft Azure AD as the Identity Provider

In this chapter, we’ve provided a detailed introduction to security and permissions in SAP BTP, Neo environment. This information should enable you to competently and efficiently solve common requirements, from conception to implementation to the final configuration of security and permissions. Based on our examples, we hope you see how easy implementing two-factor authentication can be. Even the use of a third-party identity provider isn’t difficult and can be implemented with a few targeted clicks, as shown in the second example.

## 3.7    Summary

In this chapter, you learned about configuring security and authorizations in SAP BTP, Neo environment. Starting with the command-line setup, we then walked you through key settings for user administration. We then discussed setting up identity providers via trust configuration and explained how to manage authorizations by creating and managing roles and user groups. We provided a handy checklist you can consult when managing security and permissions in SAP BTP, Neo environment, and finally, we walked you through some real-world examples showcasing two-factor authentication and Microsoft Azure AD.

# 4    Configuring Security and Authorizations in the Cloud Foundry Environment

Having covered security concepts and their implementation in SAP Business Technology Platform (SAP BTP), Neo environment in the previous chapter, we’ll now turn to the specifics of SAP BTP, Cloud Foundry environment in this chapter. We’ll cover numerous security options in SAP BTP, Cloud Foundry environment in detail.

In this chapter, we’ll look at SAP BTP, Cloud Foundry environment and its security aspects. You’ll learn everything important about roles and authorizations in this environment as well as about mappings, for example, with users of external identity providers.

In [Section 4.1](#04_001.html#h4.1), we’ll introduce you to the command-line tool as an alternative operating option for SAP BTP, Cloud Foundry environment. In [Section 4.2](#04_002.html#h4.2), you’ll learn all about user management in SAP BTP, Cloud Foundry environment, including how to assign basic permissions. In [Section 4.3](#04_003.html#h4.3), we’ll show you how to configure a trust relationship between identity providers and explore the technical foundation behind trust.

In [Section 4.4](#04_004.html#h4.4), we’ll go into the management of permissions. You’ll learn about the different types of roles and options for dynamic mappings between authorizations and user attributes. Finally, we’ll explore some reporting options available for permissions.

In [Section 4.5](#04_005.html#h4.5), we’ve provided checklist that you can use to verify that you’ve made all the important security settings. We’ll conclude this chapter in [Section 4.6](#04_006.html#h4.6) with two practical examples: one for secure service configuration and another for Microsoft Azure Active Directory (Microsoft Azure AD) integration.

###### \[»\]  Versions of SAP BTP, Cloud Foundry Environment

Currently, two different versions of SAP BTP, Cloud Foundry environment exist, called feature sets. Feature set A and feature set B differ in the design of their interfaces and their features, among other things.

SAP has announced that all customers will be migrated to feature set B in several phases. Therefore, in this book, we’ll only cover the interface activated by feature set B.

In the SAP BTP cockpit, you can determine whether your account is running feature set B by selecting the About option in your personal menu, as shown in [Figure 4.1](#04_001.html#f4.1).

[![Calling Up the System Information in the User Menu](bilderklein/klein04_001.png)](img-f4.1.html) 

**Figure 4.1**     Calling Up the System Information in the User Menu

Under Cloud Management Tools, you’ll find your feature set specification, as shown in [Figure 4.2](#04_001.html#f4.2).

[![Locating Feature Set Information in the About Dialog Box](bilderklein/klein04_002.png)](img-f4.2.html) 

**Figure 4.2**     Locating Feature Set Information in the About Dialog Box

## 4.1    Setting Up the Command Line for SAP BTP, Cloud Foundry Environment

Administration tasks for SAP BTP, Cloud Foundry environment can be performed using a console, called the Cloud Foundry command-line interface (CLI ), just like in SAP BTP, Neo environment. Since the Cloud Foundry CLI was not developed by SAP, the download is not offered by SAP, but via a public Git repository. An operating system-specific installation file and instructions can be found at [https://github.com/cloudfoundry/cli#downloads](https://github.com/cloudfoundry/cli#downloads). If you download the relevant binary version, an installation program is included for which no further prior knowledge is required.

With the following command, you can check whether the console is working. If so, the help command will display a list of all available commands:

```
cf help 
```

With the following command, you can display all commands available in the console:

```
cf help -a 
```

If you want to see all the options for a particular command, include the help command. In the following example, the result would be the options available with the login command:

```
cf help login 
```

To run commands from the console in SAP BTP, Cloud Foundry environment, the first step is to log on using the command shown in [Listing 4.1](#04_001.html#l4.1). At a minimum, you must pass the application programming interface (API) endpoint for your service instance, your organization, and your user ID.

```
cf login 
      -a <yourApiEndpoint>
      -o <yourOrganization>
      -u <yourEmailAddress> 
```

**Listing 4.1**     SAP BTP, Cloud Foundry Environment: Logging on with the login Command

You can determine the values for the required parameters using the SAP BTP cockpit. For this task, navigate to the overview for your subaccount. You can find the name of your organization and the API endpoint in the Cloud Foundry Environment section, in the Org Name and API Endpoint fields, as shown in [Figure 4.3](#04_001.html#f4.3).

[![SAP BTP, Cloud Foundry Environment: Logon Parameters](bilderklein/klein04_003.png)](img-f4.3.html) 

**Figure 4.3**     SAP BTP, Cloud Foundry Environment: Logon Parameters

The Cloud Foundry CLI can be used not only to administer SAP BTP, but also for all other Cloud Foundry implementations. This tool can be extended through plug-ins on a vendor-specific basis. SAP has also made use of this extensibility by delivering the following plug-ins:

*   Plug-in for multitarget applications (MTAs) for distributed applications with a common lifecycle
    
*   Plug-in service factory to support backups and restores of service instances
    
*   Plug-in for PostgreSQL database migrations
    
*   Plug-in for custom domains to support custom domains in applications
    

You can find these plug-ins at [https://tools.hana.ondemand.com/#cloud](https://tools.hana.ondemand.com/#cloud), as shown in [Figure 4.4](#04_001.html#f4.4).

Use the following command to install a plug-in in the Cloud Foundry CLI:

```
cf install-plugin <yourPath>/custom-domain-cli 
```

The name of the plug-in is composed of the path (i.e., darwin-amd64) and the name of the plug-in (i.e., custom-domain-cli). The path is derived from the environment (Linux, Windows, or macOS) for which you have downloaded the plug-in. The path refers to the directory that was created on your computer after unpacking the archive.

[![SAP Plug-Ins for the Cloud Foundry CLI](bilderklein/klein04_004.png)](img-f4.4.html) 

**Figure 4.4**     SAP Plug-Ins for the Cloud Foundry CLI

Use the following command to view the plug-ins installed in your Cloud Foundry CLI:

```
cf plugins 
```

You’ll learn about another command-line tool for managing your SAP BTP global account in [Chapter 6](#06_001.html#h6), [Section 6.2](#06_002.html#h6.2).

## 4.2    User Management

You can add users as members to an organization within your subaccount in SAP BTP, Cloud Foundry environment. In turn, you’ll assign roles to these members to authorize them to perform actions. A prerequisite for creating members and assigning roles is that you have been assigned the organization manager role. The user who created the subaccount is automatically added as a member and assigned this role. For more information on organizations and dependencies in subaccounts, see [Chapter 1](#01_001.html#h1), [Section 1.3.3](#01_003.html#h1.3.3).

You can also add members to a space and assign roles to these members. The prerequisite for this capability is that you must have the space manager or organization manager role. If you only have the space manager role, the users you want to add to the space as members must have already been assigned to the organization as members beforehand. If you have the organization manager role, the new member will not only be added to the space, but also to the parent organization automatically. In SAP BTP, Cloud Foundry environment, members are identified at the subaccount level and the space level solely by their email addresses.

The user administration screen can be accessed via the menu path Security • Users in the SAP BTP cockpit. [Figure 4.5](#04_002.html#f4.5) shows a standard view of the user management screen for an administration user that has been assigned as an identity provider via the SAP ID service. In our example, another user that has been provided via Microsoft Azure AD. For both users, the email address is specified as the User Name in each case.

[![Overview of Users in the Subaccount](bilderklein/klein04_05.png)](img-f4.5.html) 

**Figure 4.5**     Overview of Users in the Subaccount

Click the Create button to create new users. For users originating from the SAP ID service (as indicated by Default identity provider in the overview screen), you should create users explicitly (for more information, see [Section 4.3.1](#04_003.html#h4.3.1)). For other identity providers, you do not need to add users explicitly.

On the user creation screen, enter the user’s email address in the User Name and E-Mail fields as a unique characteristic, as shown in [Figure 4.6](#04_002.html#f4.6). Also specify the Identity Provider that provides this user. Confirm your entries by clicking the Create button.

[![Creating a User](bilderklein/klein04_006.png)](img-f4.6.html) 

**Figure 4.6**     Creating a User

After creating the user, to show the user detail view, you can check the user data again by clicking the arrow on the right side of the line ![inline image](bilder/icon_pfeil_rechts.png), as shown in [Figure 4.7](#04_002.html#f4.7). At this point, you can also directly assign roles to the user, which we describe in [Section 4.4.1](#04_004.html#h4.4.1). You can also delete a user by clicking the Delete button.

[![Showing User Details](bilderklein/klein04_07.png)](img-f4.7.html) 

**Figure 4.7**     Showing User Details

For administrators, this process is the default way to create new users at the subaccount level. On the other hand, if you want end users to have access to a cloud application running in a subaccount of SAP BTP, users are usually created automatically from the company’s own identity provider. For this task, you’ll select a checkmark during identity provider configuration (see [Section 4.3.2](#04_003.html#h4.3.2) and [Section 4.3.3](#04_003.html#h4.3.3)). In practice, this setting saves you several steps when creating users for end users.

###### \[»\]  Administration Users

A point worth mentioning is that you should have at least two administrators assigned the subaccount-specific standard subaccount admin role. This approach allows you to manage the subaccount comprehensively. You should also manage at least two users via the default identity provider in case the external identity provider is ever unavailable.

## 4.3    Trust Configuration

To configure trust relationships, you should be familiar with the basics of authentication, as described in [Chapter 2](#02_001.html#h2), [Section 2.2](#02_002.html#h2.2). Specifically, be sure you understand how identity providers and subaccounts interact, as described in [Chapter 2](#02_001.html#h2), [Section 2.2.1](#02_002.html#h2.2.1).

You can find the administration screen for trusted identity providers in the SAP BTP cockpit under Security • Trust Configuration, as shown in [Figure 4.8](#04_003.html#f4.8).

In this overview screen, you’ll see all providers currently configured. By default, the Default identity provider is activated, which we describe in [Section 4.3.1](#04_003.html#h4.3.1). Alternatively, you can set up a platform identity provider; more on this topic in [Section 4.3.2](#04_003.html#h4.3.2). To use your own provider, you can set up a custom identity provider, which we cover in [Section 4.3.3](#04_003.html#h4.3.3). A trust relationship must be explicitly set up for each additional provider.

[![SAP BTP Cockpit: Trust Configuration](bilderklein/klein04_008.png)](img-f4.8.html) 

**Figure 4.8**     SAP BTP Cockpit: Trust Configuration

###### \[»\]  Comparison of SAP BTP, Neo Environment and SAP BTP, Cloud Foundry Environment

If you have already worked through [Chapter 3](#03_001.html#h3), you’ll notice some differences between the environments when reading the following sections. See [Chapter 2](#02_001.html#h2), [Section 2.2.1](#02_002.html#h2.2.1), for notes on the differences between SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment.

### 4.3.1    Setting Up the SAP ID Service

The SAP ID service serves as the default identity provider. On the screen, this service is referred to as the Default identity provider or with the value sap.default in the Origin Key field. This identity provider cannot be deleted but can be configured. To configure it, click the pencil icon ![inline image](bilder/icon_stift.png)in the Actions column to switch to change mode. If you’re sure that your platform identity provider and/or third-party identity provider correctly authenticates all users, you can disable SAP ID service as an identity provider by deselecting the Available for User Logon checkbox, as shown in [Figure 4.9](#04_003.html#f4.9).

Select the Create Shadow Users During Logon option to control whether users listed in the default identity provider are automatically created in your SAP BTP tenant. This option is quite useful for your own identity providers. In the context of the SAP ID service, however, selecting this checkbox means that all users who have an account in the SAP ID service can log on as users of your cloud applications. They only need to know the link required to call the application. Therefore, this setting is inactive by default for SAP ID service, and we do not recommend enabling it for this identity provider.

[![Disabling the SAP ID Service as the Identity Provider](bilderklein/klein04_009.png)](img-f4.9.html) 

**Figure 4.9**     Disabling the SAP ID Service as the Identity Provider

### 4.3.2    Setting Up a Platform Identity Provider

Using a platform identity provider is another option in SAP BTP, Cloud Foundry environment. The name of the provider comes from the fact that the service runs on SAP BTP for authentication. The Identity Authentication service is used, which is run in a separate tenant. The use of this service is already included in the license for some SAP products (in a bundled license). The main task of Identity Authentication is to serve as a central identity provider for all subaccounts.

To connect an Identity Authentication tenant, click the Establish Trust button, as shown in [Figure 4.10](#04_003.html#f4.10). Setup is easier via this route than with a customer-owned identity provider but follows the same process in SAP BTP, Cloud Foundry environment as in SAP BTP, Neo environment (see [Chapter 3](#03_001.html#h3), [Section 3.3.2](#03_003.html#h3.3.2)).

If the Identity Authentication tenant is not in the same subaccount, you can use the New Trust Configuration button to establish a new trust relationship with the service. In this case, you must download the Security Assertion Markup Language (SAML) metadata yourself and upload it to the Identity Authentication tenant. Downloading the metadata follows the same process as described for the application identity provider in [Chapter 3](#03_001.html#h3), [Section 3.3.3](#03_003.html#h3.3.3). To upload the metadata, use the Identity Authentication tenant’s administration console, which you can access at https://<tenant>.accounts.ondemand.com/admin, where you’ll find SAML 2.0 Configuration in the Configuration section. Under Define from Metadata, you can upload the XML file from SAP BTP.

[![Connecting the Identity Authentication Service to SAP BTP, Cloud Foundry Environment](bilderklein/klein04_010.png)](img-f4.10.html) 

**Figure 4.10**     Connecting the Identity Authentication Service to SAP BTP, Cloud Foundry Environment

### 4.3.3    Setting Up Third-Party Identity Providers

The external identity providers used are primarily central SAML 2.0-capable services. You need these external identity providers to serve as a basis for extended services for user account and authentication (XSUAA)\-based composite role mappings, a concept we’ll explain in detail in [Section 4.4.3](#04_004.html#h4.4.3).

You can start setting up the trust relationship (based on SAML) by downloading the metadata of the service provider (i.e., SAP BTP). For this task, navigate to Security • Trust Configuration and click the SAML Metadata button, as shown in [Figure 4.10](#04_003.html#f4.10). You can then upload the resulting metadata file in XML format to the target application (i.e., the external identity provider).

Once the metadata has been imported into your identity provider, upload the provider’s SAML response in the trust configuration of the SAP BTP cockpit by clicking the New Trust Configuration button. The popup window shown in [Figure 4.11](#04_003.html#f4.11) opens.

[![Create SAML Trust Configuration](bilderklein/klein04_011.png)](img-f4.11.html) 

**Figure 4.11**     Create SAML Trust Configuration

For these settings, follow these steps:

1.  In the Metadata field, click the Upload button and upload the XML file containing the identity provider response. During this step, the Origin Key field is usually prepopulated directly. This key uniquely identifies the identity provider.
    
2.  In the Name field, enter an internal name for the identity provider, which you can choose freely.
    
3.  Select the Available for User Logon checkbox to enable externally managed users to log on.
    
4.  If you select the Create Shadow Users During Logon checkbox, a user is automatically created in the user management environment in SAP BTP, Cloud Foundry environment when an externally managed user logs on for the first time. This option thus eliminates the need to explicitly create users in the subaccount. Both checkboxes are active by default.
    
5.  In the Link Text for User Logon field, enter a display text for the link that will be shown to users on the logon page for the subaccount. Clicking on this link will take users to the linked identity provider.
    
6.  Save your settings by clicking the Save button.
    

In [Section 4.6.2](#04_006.html#h4.6.2), we’ll walk you through the complete process of setting up an external identity provider using Microsoft Azure AD as an example.

## 4.4    Authorization Management

SAP BTP, Cloud Foundry environment has a comprehensive permission management functionality. Roles can be grouped into composite roles and assigned to users or user groups. You can also assign roles to users with similar other attributes. In this section, we’ll show you how to handle both standard roles and composite roles.

### 4.4.1    Creating and Managing Roles

The available standard roles are listed in the SAP BTP cockpit via the menu path Security • Roles, as shown in [Figure 4.12](#04_004.html#f4.12).

[![SAP BTP, Cloud Foundry Environment: Roles](bilderklein/klein04_012.png)](img-f4.12.html) 

**Figure 4.12**     SAP BTP, Cloud Foundry Environment: Roles

The overview screen contains the following columns:

*   Application Name  
    This column contains the technical name of the application that contains the role template.
    
*   Application Description  
    This column contains the description of the application if a description has been maintained by the development teams.
    
*   Role Template  
    Under Role Template, you can see the identification of the role assigned by the development team.
    
*   Role Name  
    In this field, you can find the name of the role template in the form of a link. By clicking on this name, you can jump to the assignments of the role template and edit them.
    
*   Role Description  
    In this column, you’ll find additional explanations deposited by the developer teams to the role concerned.
    

Using the control fields in the last two columns, you can create customer-specific roles based on the standard roles as templates (Add Using Same Role Template), or you can delete roles ![inline image](bilder/icon_loeschen.png).

###### \[»\]  Role Template Development

Role templates are created by SAP BTP application development teams and are usually hard coded into applications. As a result, if you need additional role templates, development teams would need to customize the respective applications. For this task, you can use the Add Using Same Role Template function.

Applications are also available to help you create new roles on the fly. A prominent example is the SAP Launchpad service, which creates a new role each time a new tile is created in the SAP Fiori launchpad to enable easy website access. For a demonstration of this functionality, refer to [Section 4.6.1](#04_006.html#h4.6.1).

Now, for any role template, click the link in the Role Name column, for example, for the Subaccount Viewer role. You’ll get to the Role: <Role Name> - Overview view shown in [Figure 4.13](#04_004.html#f4.13).

All the information on this page except for the assigned Role Collections (the composite roles) comes from the application for which the role was developed.

You can edit the composite roles assigned to the role template by clicking on the Edit button in the upper right. In edit mode, as shown in [Figure 4.14](#04_004.html#f4.14), you can add the role to other composite roles by clicking the plus sign icon ![inline image](bilder/icon_plus.png). You can also remove a role from a composite roles again by clicking on the trash icon ![inline image](bilder/icon_loeschen.png).

[![Overview of a Role Template](bilderklein/klein04_013.png)](img-f4.13.html) 

**Figure 4.13**     Overview of a Role Template

[![Adding and Deleting a Composite Role Assignment](bilderklein/klein04_014.png)](img-f4.14.html) 

**Figure 4.14**     Adding and Deleting a Composite Role Assignment

The ability to jump directly to editing a composite role by clicking the arrow icon ![inline image](bilder/icon_pfeil_rechts.png)at the end of a line is particularly practical. On this screen, you can also check which other roles have already been assigned to the composite role.

Another way to find role templates for applications is to select Instances and Subscriptions from the SAP BTP cockpit menu. On the Instances and Subscriptions overview screen, you can determine which roles belong to an application by clicking on the three dots icon ![inline image](bilder/icon_drei_punkte.png)at the end of a line, as shown in [Figure 4.15](#04_004.html#f4.15). In the action menu, select the Manage Roles function.

[![Overview of Instances and Applications](bilderklein/klein04_015.png)](img-f4.15.html) 

**Figure 4.15**     Overview of Instances and Applications

Selecting this function will take you to the detail page for the application instance, as shown in [Figure 4.16](#04_004.html#f4.16). On the right, you’ll see all the role templates contained in this application instance. Starting from this overview screen, you can add new composite roles by clicking the plus icon ![inline image](bilder/icon_plus.png), or you can edit existing roles by clicking the pencil icon ![inline image](bilder/icon_stift.png).

Using this view is especially useful for finding out everyone has access to a particular application. For example, if the Role Collections and Attributes columns display a value of “0,” at this point, you can assume that no one can use the application in question (assuming the application was programmed correctly).

[![Finding and Editing Roles via the Application Overview](bilderklein/klein04_016.png)](img-f4.16.html) 

**Figure 4.16**     Finding and Editing Roles via the Application Overview

### 4.4.2    Maintaining Composite Roles

As mentioned earlier, composite roles in SAP BTP, Cloud Foundry environment are called role collections. Composite roles are formed from individual roles and assigned to users or groups of users.

You can maintain composite roles via the menu path Security • Role Collections, as shown in [Figure 4.17](#04_004.html#f4.17).

Before assigning composite roles to users, a best practice is to create your own composite roles as copies of existing templates. We do not recommend changing the roles provided in the SAP subaccount area. If necessary, you can rebuild these standard roles.

For SAP BTP, Cloud Foundry environment, SAP delivers the default role collections listed in [Table 4.1](#04_004.html#t4.1).

[![Getting Started with Role Collections Maintenance](bilderklein/klein04_017.png)](img-f4.17.html) 

**Figure 4.17**     Getting Started with Role Collections Maintenance

 
| Role || Description |
| --- | --- |
| SAP Business Application Studio administrator || This role is intended for the administration of SAP Business Application Studio. This role can also export and delete user data. |
| --- | --- |
| SAP Business Application Studio developer || This role is intended for developers working in SAP Business Application Studio. |
| SAP Business Application Studio extension deployer || This role allows the deployment of applications from SAP Business Application Studio. |
| Cloud connector administrator || This role enables the administration of the cloud connector. |
| Connectivity and destination administrator || This role enables the maintenance of cloud connector connections and their corresponding destinations in the SAP BTP cockpit. |
| Destination administrator || This role only allows the maintenance of destinations, not the administration of the cloud connector. |
| Subaccount administrator || This role is the most important role collection delivered by SAP because it allows you to comprehensively manage your subaccount. Ideally, this role is always assigned to at least two people. |
| Subaccount service administrator || This role can be used to manage the services of a subaccount. |
| Subaccount viewer || This role allows read access to a subaccount, for example, to check role assignments. |

**Table 4.1**     Composite Roles Delivered by SAP

To create a new composite role, follow these steps:

1.  In the Role Collections area, click the plus icon ![inline image](bilder/icon_plus.png)to the right, above the list of composite roles.
    
2.  In the popup window, maintain the Name and Description fields for the new role collection, as shown in [Figure 4.18](#04_004.html#f4.18), and save your entries.
    
    [![Creating a Composite Role](bilderklein/klein04_018.png)](img-f4.18.html) 
    
    **Figure 4.18**     Creating a Composite Role
    
    ###### \[»\]  Naming Conventions for Composite Roles
    
    SAP usually composes the names of the composite roles from the name of the application or application area and the possible actions, such as “Viewer” for display authorization. In the technical names, these elements are separated by an underscore. You can use these rules as a guide for your own composite roles, but they are not a binding default.
    
3.  The created composite role is now displayed in the list of composite roles. To edit this role, click the small arrow icon ![inline image](bilder/icon_pfeil_rechts.png)to the right of the line, as shown in [Figure 4.19](#04_004.html#f4.19).
    
4.  In the following view, you can add roles to the composite role and add groups or attributes to the role. Click the Edit button in the upper-right corner to switch into edit mode. [Figure 4.20](#04_004.html#f4.20) shows a composite role in edit mode.
    
    [![Editing a Composite Role](bilderklein/klein04_019.png)](img-f4.19.html) 
    
    **Figure 4.19**     Editing a Composite Role
    
    [![Collection of Roles in Edit Mode](bilderklein/klein04_020.png)](img-f4.20.html) 
    
    **Figure 4.20**     Collection of Roles in Edit Mode
    
5.  In the Roles section, you can add roles to the composite role. For this task, click the value help icon ![inline image](bilder/icon_wertehilfe.png)in the Role Name column.
    
6.  The value help is shown in [Figure 4.21](#04_004.html#f4.21). Using the dropdown lists offered, you can combine roles from various applications of your subaccount as well as from the subaccount itself.
    
    [![Value Help for Role Assignments](bilderklein/klein04_021.png)](img-f4.21.html) 
    
    **Figure 4.21**     Value Help for Role Assignments
    
7.  In the Users section, you can assign a composite role to users with the plus icon ![inline image](bilder/icon_plus.png)or remove an assignment with the trash can icon ![inline image](bilder/icon_loeschen.png).
    
8.  The User Groups and Attribute Mapping sections are important when using composite role mappings. We’ll describe this topic in more detail in [Section 4.4.3](#04_004.html#h4.4.3).
    
9.  In the Description section, you can edit the description for the composite role.
    
10.  Finally, save your changes by clicking the Save button.
     

If you’ve created your own composite role and would like to configure other composite roles based on it, you can easily copy a role using the Copy button at the end of the line, as shown in [Figure 4.22](#04_004.html#f4.22). You can use the creation dialog box (shown earlier in [Figure 4.18](#04_004.html#f4.18)) to define new names for the copied roles.

[![Copying a Composite Role](bilderklein/klein04_022.png)](img-f4.22.html) 

**Figure 4.22**     Copying a Composite Role

###### \[+\]  When Do I Use Composite Roles?

Similar to roles in ABAP systems, a general recommendation is to organize your composite roles according to the positions of the end users within the organizational structure of your company or according to business processes and to fill them with different, granular single roles. Many companies apply their own logic in these contexts. One possibility, for example, would be to name the composite roles on SAP BTP in the same way as the composite roles in the SAP ERP or SAP S/4HANA system if they are assigned to the same user groups.

### 4.4.3    Composite Role Mapping

Composite roles can be automatically associated with properties of users provided by external identity providers. This approach is called composite role mapping. The mapping is based on the concept of XSUAA. Not only are users, authorizations, and authentication obtained from the external identity provider, but decisions on the assignment of authorizations can also be generated from this source. For example, authorizations can be calculated from user attributes. This capability requires transferring these attributes from the identity provider to SAP BTP, Cloud Foundry environment. In [Section 4.6.2](#04_006.html#h4.6.2), we’ll describe this process using Microsoft Azure AD as an example.

If the appropriate information is available from the identity provider, you can perform the mapping by following these steps:

1.  Select the external identity provider in your trust configuration, as shown in [Figure 4.23](#04_004.html#f4.23).
    
2.  From the menu on the left, select Role Collection Mappings, as shown in [Figure 4.24](#04_004.html#f4.24).
    
    [![Selecting the Identity Provider](bilderklein/klein04_023.png)](img-f4.23.html) 
    
    **Figure 4.23**     Selecting the Identity Provider
    
    [![Selecting the Role Collection Mappings](bilderklein/klein04_024.png)](img-f4.24.html) 
    
    **Figure 4.24**     Selecting the Role Collection Mappings
    
3.  On this screen, you can perform the mapping between the role collections and the provided user attributes. For this task, click on the New Role Collection Mapping button, as shown in [Figure 4.25](#04_004.html#f4.25).
    
4.  Specify an attribute name and value for which the role collection should be assigned.
    
5.  Save these values.
    

You can use any of the values from the identity provider. The notation of these values does not have to be exactly the same as the notation in the identity provider. An example result is shown in [Figure 4.25](#04_004.html#f4.25). In our case, the Subaccount Administrator role is automatically assigned to all users who are members of the All Users group (attribute Groups).

[![Overview of Mappings](bilderklein/klein04_025.png)](img-f4.25.html) 

**Figure 4.25**     Overview of Mappings

###### \[»\]  Verify Mapping Values Using Tools

If you use Microsoft Active Directory or Microsoft Azure AD as the source of user attributes, we recommend that you check these values using a tool. For example, you can use the snap-in for the Microsoft Management Console. For more information, see the Microsoft website at [http://s-prs.co/v562700](http://s-prs.co/v562700).

Composite role mappings are convenient if you are responsible for a manageable number of subaccounts and can provide user data for those subaccounts through a single identity provider. In more complex landscapes, we recommend that you use the Identity Provisioning service we introduced in [Chapter 2](#02_001.html#h2), [Section 2.4.2](#02_004.html#h2.4.2). This service runs on only one tenant and allows more complex operations with attributes via transformations. The Identity Provisioning service can also provide several subaccounts with data centrally—comparable to central user administration in ABAP-based SAP solutions.

###### \[»\]  Licensing with SAP Cloud Products

As of Q4 2020, the Identity Authentication service and the Identity Provisioning service are licensed as bundled with many SAP cloud solutions. This bundling makes the use of both services even more attractive from a cost perspective.

### 4.4.4    Reporting in the Authorization Environment

The user overview screen of a subaccount offers the ability to create reports on users and authorizations. This reporting feature provides an overview of authorized users and the roles assigned to them while the system is running.

To create a user report, follow these steps:

1.  Navigate to Security • Users and click the report icon ![inline image](bilder/icon_bericht.png)to the right, above the user list, as shown in [Figure 4.26](#04_004.html#f4.26).
    
    [![Accessing the User Report](bilderklein/klein04_026.png)](img-f4.26.html) 
    
    **Figure 4.26**     Accessing the User Report
    
2.  In the menu that opens, choose between a simple user report (Export all Users) or a report including the role assignments (Export all Users with Role Collections).
    
3.  The report is generated as a CSV file, which can be opened in a spreadsheet program like Microsoft Excel.
    

[Figure 4.27](#04_004.html#f4.27) shows the structure of a report, including assigned roles. You’ll find the user name, the identity provider that provides for the user, the last and first name of the user, an email address, and the time of the last change of the user data. The assigned composite roles are listed in the Assigned Role Collections column separated by a comma.

[![Result of the User Report with Assigned Role Collections](bilderklein/klein04_027.png)](img-f4.27.html) 

**Figure 4.27**     Result of the User Report with Assigned Role Collections

###### \[»\]  Limitations of the User Report

The date of the last user logon is currently not included in the report. Unfortunately, at the time of this writing, such a report does not yet exist for the composite role mappings, only for users with explicit role assignments.

## 4.5    Checklist for Security and Permissions in SAP BTP, Cloud Foundry Environment

[Table 4.2](#04_005.html#t4.2) provides a permissions and user management checklist for SAP BTP, Cloud Foundry environment.

 
| Completed || Task |
| --- | --- |
|  || You have an overview of the different data centers for SAP BTP, Cloud Foundry environment and SAP BTP, Neo environment, and have made a note of the servers in use, preferably in a central location. |
| --- | --- |
|  || You’ve checked that you subscribe to the latest SAP BTP feature set. You should start new projects with the latest version of SAP BTP. |
|  || You’ve chosen a name for your organization so that it does not change quickly since organization names can only be changed by creating a new subaccount. |
|  || You’ve delimited your subaccounts from other subaccounts. This step is especially important when connecting on-premise systems via the cloud connector (see [Chapter 5](#05_001.html#h5)). For overarching scenarios, you’ve considered the use of the Identity Provisioning service. |
|  || You’ve determined where the use of identity providers will be documented and how many identity providers you want to use. |
|  || You’ve ensured that only a restricted group of users can make changes to the productive configuration of identity providers. |
|  || The cloud security concept is coordinated and coherent with the local security concept. Pay particular attention to which users (all users?) in your company can log on to the cloud applications. |
|  || SAP BTP composite roles match the user roles in other systems in your landscape. The mapping should match that of on-premise roles based on the use case. Composite roles from the various systems should be on the same level because the comparisons include single roles and SAP BTP roles. |
|  || When deciding whether to use an Identity Authentication tenant, consider the following criteria:

*   Licensing questions: If you have access to the Identity Authentication service anyway as part of a bundled license for an SAP cloud application, using this service as well makes sense in terms of cost anyway.
    
*   The question of clarity: As you use more and more subaccounts, managing external identity providers through the Identity Authentication service as a platform identity provider becomes easier. The trust relationship can then be established from the respective subaccounts to the Identity Authentication service and from there on to the external identity provider.
    

 |
|  || If you’re using an external identity provider, you’ve set up a composite role mapping. You’ve identified the appropriate attributes for such a mapping. Note that reporting for the mapped assignments is only possible on the external provider side at the time of writing. |

**Table 4.2**     Checklist for Security and Permissions in SAP BTP, Cloud Foundry Environment

## 4.6    Real-World Examples of User and Permission Management

In this section, we’ll explore two real-world examples of user and permission management in SAP BTP, Cloud Foundry environment. We’ve selected scenarios that occur frequently in practice. For example, activating the SAP Launchpad service ([Section 4.6.1](#04_006.html#h4.6.1)) and integrating Microsoft Azure AD ([Section 4.6.2](#04_006.html#h4.6.2)) are quite common requirements.

### 4.6.1    Activation and Secure Configuration of the SAP Launchpad Service

The guidelines for developing SAP user interfaces (UIs) have been available for several years: Use SAP Fiori design guidelines and the underlying technology SAPUI5 for your custom business applications. Also, you should provide an SAP Fiori launchpad to serve as a central entry point for these applications. This new central entry point should gradually replace the aging SAP Enterprise Portal. A simple example of a tile in the SAP Fiori launchpad is shown in [Figure 4.28](#04_006.html#f4.28).

[![SAP Fiori Launchpad: Example Test Tile](bilderklein/klein04_028.png)](img-f4.28.html) 

**Figure 4.28**     SAP Fiori Launchpad: Example Test Tile

Locally or on-premise, the SAP Fiori launchpad is deployed through an SAP Fiori frontend server. However, since you don’t necessarily want to include tiles for calling cloud services in a locally running launchpad, SAP has launched the SAP Launchpad Service. With feature set B (refer to the beginning of this chapter), this service is available in the SAP BTP, Cloud Foundry environment service marketplace.

In the following example, you’ll learn how to set up the SAP Launchpad service and configure it for secure access to your cloud applications.

To perform the following steps, the following prerequisites must be met:

*   You must have an account on SAP BTP, Cloud Foundry environment and have finished setting up a subaccount in the data center of your choice. You can also use a trial account for this example.
    
*   You know who should administer the SAP Fiori launchpad and which users are the target group for the content provided. You have also considered who could be available as a test user.
    

If all these requirements are met, first, we’ll activate the SAP Launchpad service by following these steps:

1.  In the SAP BTP cockpit menu, select Services • Service Marketplace and enter the keyword “Launchpad” in the search field.
    
2.  The Launchpad Service tile is displayed as the search result, as shown in [Figure 4.29](#04_006.html#f4.29).
    
    [![SAP BTP Cockpit: Activating the SAP Launchpad Service](bilderklein/klein04_029.png)](img-f4.29.html) 
    
    **Figure 4.29**     SAP BTP Cockpit: Activating the SAP Launchpad Service
    
3.  Click on the tile to access the detailed view of the service.
    
4.  In this detailed view, click the Create button to create a service instance, as shown in [Figure 4.30](#04_006.html#f4.30).
    
    [![Creating an Instance of the SAP Launchpad Service](bilderklein/klein04_030.png)](img-f4.30.html) 
    
    **Figure 4.30**     Creating an Instance of the SAP Launchpad Service
    
5.  In the next dialog box, leave the default settings and click the Create button, as shown in [Figure 4.31](#04_006.html#f4.31).
    
    [![Default Settings for Creating a Service Instance](bilderklein/klein04_031.png)](img-f4.31.html) 
    
    **Figure 4.31**     Default Settings for Creating a Service Instance
    
6.  Wait for a few minutes and the instance of your service subscription will be ready for use.
    

Before you can use the service, you must assign the necessary permissions to your user.

###### \[»\]  Choosing the Administration Role

Most SAP BTP services provide a predefined administrator role. For information, see the documentation for each service in SAP Help Portal or the documentation provided by the development team that provides the service. You can access the documentation for the SAP Launchpad service (and most other SAP services) by clicking on your subscription in the Instances and Subscriptions area of the SAP BTP cockpit. In the list of subscriptions, click the name of the application—in this case, Launchpad Service (as shown in [Figure 4.32](#04_006.html#f4.32), on the left)—and navigate to the Overview tab.

[![Navigating to the SAP Launchpad Service Documentation](bilderklein/klein04_032.png)](img-f4.32.html) 

**Figure 4.32**     Navigating to the SAP Launchpad Service Documentation

Assign the Launchpad\_Admin composite role to your own user using the following steps:

1.  Navigate to the Security • Role Collections section in the SAP BTP cockpit.
    
2.  Filter the list of composite roles using the term “Launchpad.” Enter this value in the filter box on the right, above the Role Collections list.
    
3.  You should now see two role collections, one of which is the Launchpad\_Admin role, as shown in [Figure 4.33](#04_006.html#f4.33).
    
4.  Double-click on this role collection to switch to the detail view. Click on the Edit button, as shown in [Figure 4.34](#04_006.html#f4.34).
    
5.  Now, select your user ID (i.e., your email address) in the lower area of the edit view. If the email address in the E-Mail column is prepopulated by the system, as shown in [Figure 4.35](#04_006.html#f4.35), but is outlined in red, delete a character in the address and add it back directly. This is a current bug that will probably be fixed in the future.
    
6.  Save the assignment by clicking the Save button.
    

[![Searching for a Composite Role for Managing the SAP Launchpad Service](bilderklein/klein04_033.png)](img-f4.33.html) 

**Figure 4.33**     Searching for a Composite Role for Managing the SAP Launchpad Service

[![Editing the Launchpad Admin Composite Role](bilderklein/klein04_034.png)](img-f4.34.html) 

**Figure 4.34**     Editing the Launchpad Admin Composite Role

[![Assigning Administration Rights to Your Own User](bilderklein/klein04_035.png)](img-f4.35.html) 

**Figure 4.35**     Assigning Administration Rights to Your Own User

###### \[ ! \]  Assign Critical Administration Authorizations with Care

Do not assign the role collection Launchpad\_Admin too generously. The Theme\_Admin role contained in it can be used to change the design of your launchpad, among other things. A better approach is to create a separate role collection from which you exclude the Theme\_Admin role.

Now, check whether you can call the service by navigating to Services • Instances and Subscriptions in the SAP BTP cockpit menu and then clicking the Go to Application ![inline image](bilder/icon_go_to_application.png)icon next to the Launchpad Service in the list of subscriptions, as shown in [Figure 4.36](#04_006.html#f4.36). The Site Directory page, the administration environment of the SAP Launchpad service, opens. The fact that this call works shows that the authorization assignment was successful.

###### \[»\]  User Language of the SAP Launchpad Service

The SAP Launchpad service interface has been translated into several languages. The homepage of the web page directory should greet you in German, for example, if you've set German as the default language in your browser.

[![Jumping to the Administration of the SAP Launchpad Service](bilderklein/klein04_036.png)](img-f4.36.html) 

**Figure 4.36**     Jumping to the Administration of the SAP Launchpad Service

Now, create your first own launchpad website, which you can then set up a role to call. For this task, follow these steps:

1.  Click the Create Site button on the Site Directory screen.
    
2.  A test page with the default settings will be suggested automatically. Accept these settings.
    
3.  The result is shown in [Figure 4.37](#04_006.html#f4.37).
    

[![SAP Launchpad Service: Creating a Test Page](bilderklein/klein04_037.png)](img-f4.37.html) 

**Figure 4.37**     SAP Launchpad Service: Creating a Test Page

Now, you can create a new role that authorizes users to access the test page:

1.  Switch to the Content Manager via the package icon ![inline image](bilder/icon_content.png)in the toolbar on the left.
    
2.  Click the \+ New button there. In the menu that opens, select the Role entry.
    
3.  Simply name the new role “Launchpad role.” In practice, you would now add permissions to the role for the various content (apps, catalog, and groups). Users who are assigned this role are then automatically authorized to access this content.
    
4.  The new role is then displayed in the role overview, as shown in [Figure 4.38](#04_006.html#f4.38).
    

[![SAP Launchpad Service: Creating a Role](bilderklein/klein04_038.png)](img-f4.38.html) 

**Figure 4.38**     SAP Launchpad Service: Creating a Role

The role created in the SAP Launchpad service is also displayed in the SAP BTP cockpit as a composite role. If you navigate to Security • Role Collections and search for the keyword “Launchpad,” you’ll see a role called Launchpad\_Role, as shown in [Figure 4.39](#04_006.html#f4.39).

[![Result of Creating the Role](bilderklein/klein04_039.png)](img-f4.39.html) 

**Figure 4.39**     Result of Creating the Role

In practice, you would now add additional permissions in this composite role that the end users need in order to call the tiles in SAP Fiori launchpad (e.g., the permissions for additional services of SAP BTP).

Finally, familiarize yourself with the intended security settings and restrictions, especially for using the cloud connector in collaboration with the SAP Launchpad service. To assess whether the SAP Launchpad service is suitable for your requirements, but also to see whether the connection of the backend systems has been configured with the correct security settings in the backend and the cloud connector, a best practice is to access the Overview page in the SAP BTP cockpit, under Services • Instances and Subscriptions again. On this page, you’ll find a link to the current documentation for the SAP Launchpad service.

We would like to draw your attention to two topics in this documentation:

*   Under the Initial Setup • Limitations - General menu item, you’ll find information on what you should be aware of regarding the scope and function of the SAP Fiori launchpad.
    
*   Under the Initial Setup • Set Up Cloud Connector menu item, you’ll find a detailed overview of which services must be enabled on the backend systems or in the cloud connector so that proper access is possible, as shown in [Figure 4.40](#04_006.html#f4.40).
    

[![Excerpt from the Documentation for the SAP Launchpad Service](bilderklein/klein04_040.png)](img-f4.40.html) 

**Figure 4.40**     Excerpt from the Documentation for the SAP Launchpad Service

### 4.6.2    Two-Factor Authentication of Users via Microsoft Azure AD

In our second practical example, we assume that the users of your enterprise applications are managed in Microsoft Azure AD. Now, you want to use this user pool to authenticate users in SAP BTP, Cloud Foundry environment. In doing so, you want to ensure that two-factor authentication is performed.

The following prerequisites must be met for you to run through the example in this section:

*   You have administration access to SAP BTP and Microsoft Azure AD.
    
*   You have a user who has already been enabled for two-factor authentication in Microsoft Azure AD.
    
*   You know in which region your SAP BTP, Cloud Foundry environment subaccount is deployed.
    

Let’s start by downloading the trust relationship metadata from your SAP BTP subaccount by following these steps:

1.  Navigate to Security • Trust Configuration in the SAP BTP cockpit.
    
2.  Click on the SAML Metadata button to download the metadata, as shown in [Figure 4.41](#04_006.html#f4.41).
    
    [![SAP BTP Cockpit: Downloading SAML Metadata](bilderklein/klein04_041.png)](img-f4.41.html) 
    
    **Figure 4.41**     SAP BTP Cockpit: Downloading SAML Metadata
    
3.  Save the obtained file locally.
    

Using the metadata, you can then create an enterprise application in Microsoft Azure AD. You also download metadata from Microsoft Azure AD, which you’ll then deploy to SAP BTP. Follow these steps:

1.  Log on to Microsoft Azure AD at [https://portal.azure.com](https://portal.azure.com).
    
2.  Follow the menu path Enterprise Applications • New Application • SAP and call up the SAP Cloud Platform tile.
    
3.  Click the Create button, as shown in [Figure 4.42](#04_006.html#f4.42), to add SAP BTP as an enterprise application.
    
    [![Microsoft Azure AD: Adding SAP Cloud Platform as an Enterprise Application](bilderklein/klein04_042.png)](img-f4.42.html) 
    
    **Figure 4.42**     Microsoft Azure AD: Adding SAP Cloud Platform as an Enterprise Application
    
4.  After creating the application, select it in the application list, under the Enterprise Applications menu item.
    
5.  In the first step, select the users you want to allow to log on to the application. You can select all users or specify a user group in Microsoft Azure AD that seems appropriate.
    
6.  Now, select SAML-based logon in the enterprise application, under Set up single sign on • Getting Started.
    
7.  In the toolbar, click the Upload metadata file button, as shown in [Figure 4.43](#04_006.html#f4.43). This step uploads the metadata file downloaded in the SAP BTP cockpit.
    
8.  In the following popup window, specify the Reply URL, which has the following format:
    
    https://<tenant>.authentication.<region>.hana.ondemand.com/
    
    So, for example, the URL could resemble the following link:
    
    https://abcdeftrial.authentication.eu10.hana.ondemand.com/
    
9.  Click Save.
    

[![Microsoft Azure AD: Uploading Metadata](bilderklein/klein04_043.png)](img-f4.43.html) 

**Figure 4.43**     Microsoft Azure AD: Uploading Metadata

Now, to make the groups of the Microsoft Azure AD visible in SAP BTP, follow these steps:

1.  For this task, select the App registrations subitem in the enterprise applications overview in Microsoft Azure AD, as shown in [Figure 4.44](#04_006.html#f4.44).
    
    [![Microsoft Azure AD: App Registrations](bilderklein/klein04_044.png)](img-f4.44.html) 
    
    **Figure 4.44**     Microsoft Azure AD: App Registrations
    
2.  Then, click the All applications tab, as shown in [Figure 4.45](#04_006.html#f4.45). Select the SAP Cloud Platform enterprise app you created earlier.
    
    [![Microsoft Azure AD: Selecting the SAP Cloud Platform Enterprise App](bilderklein/klein04_045.png)](img-f4.45.html) 
    
    **Figure 4.45**     Microsoft Azure AD: Selecting the SAP Cloud Platform Enterprise App
    
3.  On the following screen, select the Manifest menu item, as shown in [Figure 4.46](#04_006.html#f4.46). The Manifest is the technical specification of the properties that must be passed from Microsoft Azure AD to the SAML token.
    
    [![Microsoft Azure AD: Editing the Visibility of a Group](bilderklein/klein04_046.png)](img-f4.46.html) 
    
    **Figure 4.46**     Microsoft Azure AD: Editing the Visibility of a Group
    
4.  In the manifest JavaScript Object Notation (JSON) editor, locate the groupMembershipClaims property on the right and replace the null value with the SecurityGroup value. This change will consider the group memberships of a Microsoft Azure AD user.
    
5.  When done, save your changes by clicking Save icon in the toolbar.
    

Next, make sure that users are authenticated using their email addresses and not the samaccountname, which is the same as the user name in Windows or Microsoft Azure AD. For this task, go back to your enterprise application and select the Single sign-on menu item. As shown in [Figure 4.47](#04_006.html#f4.47), you should see the Groups attribute (technically the SecurityGroup) defined in the previous step as a new attribute, in the user Attributes & Claims list.

[![Microsoft Azure AD: SSO Configuration](bilderklein/klein04_047.png)](img-f4.47.html) 

**Figure 4.47**     Microsoft Azure AD: SSO Configuration

Now, click Edit on the right, above the list of user attributes and entitlements, and change the value of the Unique User Identifier attribute from user.principalname to user.mail.

Additionally, you must write the group information to the Groups attribute so that this information is also available in SAP BTP for composite role mapping. For this task, click on the user.groups value and change the name of the group claim to “Groups,” as shown in [Figure 4.48](#04_006.html#f4.48). The group claim controls whether a user’s group membership information is included in the SAML token. This information forms the basis for composite role mapping with Microsoft Azure AD groups.

[![Microsoft Azure AD: Group Attribute Customization](bilderklein/klein04_048.png)](img-f4.48.html) 

**Figure 4.48**     Microsoft Azure AD: Group Attribute Customization

Finally, let’s add Microsoft Azure AD as an identity provider in SAP BTP:

1.  From the SAML-based logon overview page in Microsoft Azure AD, download the metadata for the trust relationship by clicking the Download link next to the Federation Metadata XML entry, as shown in [Figure 4.49](#04_006.html#f4.49).
    
    [![Microsoft Azure AD: Downloading the Metadata XML File](bilderklein/klein04_049.png)](img-f4.49.html) 
    
    **Figure 4.49**     Microsoft Azure AD: Downloading the Metadata XML File
    
2.  In the SAP BTP cockpit, navigate to Security • Trust Configuration and click the New Trust Configuration button.
    
3.  In the popup window, upload the metadata XML file by clicking the Upload button, assign a name for the trust configuration, and enter text in the Link Text for User Logon field that will be displayed to users on the logon page, as shown in [Figure 4.50](#04_006.html#f4.50).
    
    [![Microsoft Azure AD: Creating a New Trust Configuration for the External Identity Provider](bilderklein/klein04_050.png)](img-f4.50.html) 
    
    **Figure 4.50**     Microsoft Azure AD: Creating a New Trust Configuration for the External Identity Provider
    
4.  Save your entries by clicking the Save button.
    

Finally, to test whether connecting Microsoft Azure AD as an identity provider works, access the logon URL https://<tenant>.authentication.<region>.hana.ondemand.com/, which you had defined for the SAP Cloud Platform enterprise application in Microsoft Azure AD. The accessed website should display the text you selected for the logon link, as shown in [Figure 4.51](#04_006.html#f4.51).

[![SAP BTP: New Logon Page after Configuring the Identity Provider](bilderklein/klein04_051.png)](img-f4.51.html) 

**Figure 4.51**     SAP BTP: New Logon Page after Configuring the Identity Provider

###### \[ ! \]  User ID and Composite Role Mapping as Prerequisites for Successful Logon

The test only works if you log on as a user with the same email address that you registered with in Microsoft Azure AD. In addition, a mapping of the group from Microsoft Azure AD and the SAP BTP composite role must have been performed in the Role Collection Mappings section in the identity provider configuration. An example of such a mapping is shown in [Figure 4.52](#04_006.html#f4.52). In our case, the All Users group transferred from Microsoft Azure AD has been mapped with the composite role Subaccount Administrator.

[![Role Mapping for Microsoft Azure AD as an Identity Provider](bilderklein/klein04_052.png)](img-f4.52.html) 

**Figure 4.52**     Role Mapping for Microsoft Azure AD as an Identity Provider

When you click the test link on the logon page (shown earlier in [Figure 4.51](#04_006.html#f4.51)), you should be taken to the logon dialog box for Microsoft Azure AD. The success message will display your email address in the top-right corner of the screen, as shown in [Figure 4.53](#04_006.html#f4.53).

[![Successful Logon via the External Identity Provider](bilderklein/klein04_053.png)](img-f4.53.html) 

**Figure 4.53**     Successful Logon via the External Identity Provider

The final requirement in this practical example is the setup of two-factor authentication. Microsoft Azure AD is solely responsible for implementing this feature, so we won’t go into detail about it in this book. You have two options when configuring this type of authentication:

*   You can set the security standards for all access to Microsoft Azure AD to Require Multifactor Authentication within Microsoft Azure AD properties.
    
*   You simply set this authentication method as a policy for conditional access in your enterprise application.
    

A working example of two-factor authentication settings is shown in [Figure 4.54](#04_006.html#f4.54). For this variant, note that the Enable policy switch at the bottom left of the screen still needs to be set to On.

[![Microsoft Azure AD: Requesting Two-Factor Authentication](bilderklein/klein04_054.png)](img-f4.54.html) 

**Figure 4.54**     Microsoft Azure AD: Requesting Two-Factor Authentication

###### \[ ! \]  Concept for the Designation of Composite Roles

Since the value mappings between the external identity provider and SAP BTP composite roles are not so easy to identify, you could name the composite roles after the user or security groups or, if possible, create corresponding groups. Ideally, you should also include an SAP BTP subaccount or at least the category (development, quality assurance, or production) in the group names.

## 4.7    Summary

In this chapter, you learned about configuring security and authorizations in SAP BTP, Cloud Foundry environment. Starting with the command-line setup, we then walked you through key settings for user management. We then discussed setting up identity providers via trust configuration and explained how to manage authorizations by creating and managing roles, specifically composite roles. We provided a handy checklist to consult when managing security and permissions for SAP BTP, Cloud Foundry environment. Finally, we explored some real-world examples showcasing the SAP Launchpad service and two-factor authentication with Microsoft Azure AD.

# 5    Secure Cloud Connector Configuration

SAP’s cloud connector represents the central component for linking your on-premise system landscape to SAP cloud systems. The basic idea behind the cloud connector is to provide centralized access to administering and monitoring connections.

For hybrid system landscapes, the level of complexity of the system architecture will be high. Some years past, a trend to reintegrate systems resulted in methods for system landscape optimization. The integration of the business partner model into the world of SAP ERP is another example following that trend. Today, those integrated systems are extended by another external layer—the cloud layer. Thus, the challenges for system administration are changing. Concerning your company’s on-premise systems, some leading questions might include the following:

*   Where is the server’s exact location?
    
*   Is this particular server a virtual server or a physical one?
    
*   Which networks and zones are these servers a member of?
    

Speaking of cloud architecture, this information is often not transparent to the customer.

But in addition to hardware-based failover and recovery scenarios, the network is challenged by such hybrid scenarios. The network should be self-recovering and should offer plan Bs. For governance and compliance, it will also be important to know which part of your system landscape runs which tasks.

In this chapter, we’ll describe the architecture of hybrid SAP landscapes as well as explore the different options available when using the cloud connector. [Section 5.1](#05_001.html#h5.1) will shed some light on the system architecture of cloud connector and will also cover several network topics (e.g., local network grants and the mapping required to connect to remote systems). In [Section 5.2](#05_002.html#h5.2), we’ll guide you step by step through the configuration and setup of the cloud connector and through its modes of operation. [Section 5.3](#05_003.html#h5.3) covers authentication and user management within the cloud connector.

[Section 5.4](#05_004.html#h5.4) and [Section 5.5](#05_005.html#h5.5) are about system connections between cloud-based and on-premise systems. You’ll learn how to access and use on-premise systems from inside the cloud and how to use defined system connections from within cloud services.

In [Section 5.6](#05_006.html#h5.6), you’ll find another checklist for the secure operation of cloud connector. This chapter will conclude with [Section 5.7](#05_007.html#h5.7), which will explore three example connectivity scenarios widely found in the field. We’ll show you how to link a Git repository or an SAP S/4HANA system as well as the proper configuration of Lightweight Directory Access Protocol (LDAP) authentication for the cloud connector.

## 5.1    Architecture

The cloud connector forms the central interface to access the services of SAP Business Technology Platform (SAP BTP) within your own system landscape. This solution acts as a link between cloud and on-premise systems and communicates with SAP BTP via secure connections, as shown in [Figure 5.1](#05_001.html#f5.1).

[![Cloud Connector as an Intermediary between Cloud-Based and On-Premise Systems](bilderklein/klein05_01_source.png)](img-f5.1.html) 

**Figure 5.1**     Cloud Connector as an Intermediary between Cloud-Based and On-Premise Systems

At the architecture level, the goal is for system connections that send data to or receive data from the SAP cloud solutions to be handled by the cloud connector. Multiple instances of the cloud connector can also be deployed. Distinct from these integration scenarios are connections from end devices that typically access the cloud applications or services directly.

Some reasons for using the cloud connector as a link include the following:

*   Centralized management of system connections
    
*   Support of the necessary protocols, such as remote function call (RFC) for proprietary SAP connections and Hypertext Transfer Protocol Secure (HTTPS) as a global standard
    
*   Elimination of the need to configure various port mappings and firewall rules on both sides of the cloud connector
    
*   Easy and clear administration compared to previous concepts (e.g., SAP Gateway and SAProuter)
    
*   Full support from SAP
    

To illustrate different variants of integration using the cloud connector, consider the following examples:

*   Access to an SAP application in the cloud environment  
    An application in the cloud environment needs data from your local SAP systems, for example, SAP Web IDE or SAP Business Application Studio. Users access the cloud from the Internet, but you don’t want access to the local system to take place directly via the Internet, but instead via a central tool. For this task, you can use the cloud connector. [Figure 5.2](#05_001.html#f5.2) shows the architecture for this scenario.
    

[![Accessing SAP Applications in the Cloud](bilderklein/klein05_02_source.png)](img-f5.2.html) 

**Figure 5.2**     Accessing SAP Applications in the Cloud

*   Use of an SAP cloud service by an on-premise application  
    Let’s say your company provides an on-premise application that receives data through a service running on SAP BTP. Primarily for security reasons, you do not want this data to be accessible directly over the Internet. Thus, you can use the cloud connector to allow an on-premise system to access the cloud service. [Figure 5.3](#05_001.html#f5.3) shows the architecture for this scenario.
    

[![Application Accessing a Cloud Service in the Local On-Premise Network](bilderklein/klein05_03_source.png)](img-f5.3.html) 

**Figure 5.3**     Application Accessing a Cloud Service in the Local On-Premise Network

*   Use of a database on SAP BTP by a local database  
    A local database instance, for example, the database of an SAP Business Warehouse (SAP BW) system, uses data stored in a database on SAP BTP to enrich SAP BW InfoCubes with additional data. The cloud database can be, for example, the SAP HANA service of SAP BTP. In this scenario, no end users exist since the data can also be processed asynchronously. The scenario is shown schematically in [Figure 5.4](#05_001.html#f5.4).
    

[![Communication between a Local SAP BW System Database with an SAP HANA Database in the Cloud](bilderklein/klein05_04_source.png)](img-f5.4.html) 

**Figure 5.4**     Communication between a Local SAP BW System Database with an SAP HANA Database in the Cloud

The cloud connector is used differently for all these three scenarios. Depending on how many subaccounts you have on SAP BTP, your on-premise systems will only ever have access to one subaccount, or only one subaccount will have access to your on-premise systems.

###### \[»\]  Limitations of the Cloud Connector

At the time of this writing, the cloud connector cannot be used yet for direct connections from SAP software as a service (SaaS) solutions (such as SAP S/4HANA Cloud and SAP Customer Experience) to SAP on-premise systems. Other integration scenarios are available for this need, some of which are specific to the product in question.

When installing the cloud connector productively, select a suitable server or fine a suitable place in your local network. Since the cloud connector is a system that communicates externally, this component should not run directly on a server on which other SAP components have also been installed.

The following approaches have proven successful in most cases:

*   Placing the cloud connector in the SAP server network and granting permission for the server to communicate with SAP BTP (if necessary, via an HTTPS proxy).
    
*   Placing the cloud connector in the demilitarized zone (DMZ) and enabling individual connections to the SAP systems. In this case, the DMZ restricts access to the web interface for administering the cloud connector in terms of the network; otherwise, access could occur from the outside.
    

In any case, for productive installations, we recommend using at least one third-party security product between SAP BTP and your on-premise systems. This approach spreads the risk and is generally recommended for any access via external channels.

###### \[»\]  Positioning the Cloud Connector within the Network

In an SAP server network, enabling individual systems for access by the cloud connector is generally not a problem, but routes to the SAP servers must be well secured by appropriate firewalls. In a DMZ, the servers are well secured, but access to the SAP systems must be specially authorized. For the positioning of the cloud connector, the decisive factor in this scenario is which kinds of access should be realized: Access via HTTPS requires something different than access between SAP HANA databases, which is much closer to the “innermost core” of an SAP system.

## 5.2    Installing and Configuring the Cloud Connector

The cloud connector is offered for the Linux and Windows operating systems. A version for macOS exists, but this version is not intended for productive use.

### 5.2.1    Download and Installation

For all variants, the download process is carried out at [https://tools.hana.ondemand.com](https://tools.hana.ondemand.com). At that website, preconfigured test versions (portable), intended for developers, and versions suitable for production (installer) can be downloaded. Developer versions enable you to test system connections to the cloud, for example, without having to contact the Basis department. Note, however, that this version cannot run in the background.

For productive installations, an installer is provided to help you to perform the installation.

To install the cloud connector, a version of the Java development kit (JDK) must be installed on a local machine. At the time of writing, SAP requires either version Java 8 or Java 1.8.x.

In test environments or for the portable version of the cloud connector, any version of Java compatible with JDK 8 can be used. For use in productive environments, we strongly recommend using the JDK included in the Java Virtual Machine (JVM), a version of JDK 8 licensed by SAP. You can download this component from SAP Support Portal at [http://s-prs.de/v809808](http://s-prs.de/v809808). At that website, search for the keyword “SAPJVM8” under Installations & Upgrades.

After you’ve installed the JDK, the system variable JAVA\_HOME points to the corresponding Java version. Once this requirement is met, you can install the cloud connector.

To install the portable version, download and extract archive and run the go file. As a result, you’ll see an image in the command line, which may be different depending on your operating system, as shown in [Figure 5.5](#05_002.html#f5.5). Note the last line, which contains the link to call the cloud connector in your local Internet browser.

[![Result of Calling the Portable Cloud Connector](bilderklein/klein05_05.png)](img-f5.5.html) 

**Figure 5.5**     Result of Calling the Portable Cloud Connector

###### \[»\]  Access to Cloud Services by Development Teams

If development teams need to test new cloud services and access these services directly from a development computer, you must clarify whether the use of the portable version of the cloud connector on these computers is permitted according to your company’s requirements or whether restrictions on the installation of software are required.

To install the full versions, the program for your operating system is run, in which you can select the installation path, the Java version to be used, and the Secure Sockets Layer (SSL) port to be used. The default port is 8443.

### 5.2.2    Initial Configuration

The cloud connector is accessed via an Internet browser. Select the output path or enter the URL [https://localhost:8443](https://localhost:8443). If you have selected a different port, adjust it accordingly in the last part of the unique resource identifier (URI).

Since the cloud connector is delivered with a self-signed certificate, an error message must be confirmed depending on the Internet browser. If you cannot load the page in the Google Chrome browser, we recommend calling the following configuration page:

chrome://flags/#allow-insecure-localhost

On that page, you can update the certificate setting if necessary.

On the logon screen, you can initially log on with the User Name “administrator” and the Password “manage,” as shown in [Figure 5.6](#05_002.html#f5.6).

[![Cloud Connector Logon Screen](bilderklein/klein05_06.png)](img-f5.6.html) 

**Figure 5.6**     Cloud Connector Logon Screen

After changing the initial password to one of your own choosing as prompted, you’ll be taken to the Define Subaccount overview screen of the administration interface (console), as shown in [Figure 5.7](#05_002.html#f5.7). The mandatory fields are the Region, Subaccount, Subaccount User, and Password fields. Enter the access data for the SAP BTP subaccount to be connected. Optionally, you can also enter a display name and a description.

By specifying a Location ID, you can separate multiple cloud connector instances connected to SAP BTP geographically (e.g., separate East Coast data centers from West Coast ones). Leave this field blank for now. If you maintain this field, you should use the same Location ID that you used when creating the destination in SAP BTP.

Now, we’ll configure the connection from the computer on which the cloud connector is installed to the Internet, via an HTTPS proxy. Maintain the Host, Port, User, and Password fields on the right.

[![Cloud Connector Administration: Define Subaccount Overview Page](bilderklein/klein05_07.png)](img-f5.7.html) 

**Figure 5.7**     Cloud Connector Administration: Define Subaccount Overview Page

We recommend that you import an SSL certificate signed by a certificate authority (CA) at this point—definitely do so at least before using the cloud connector productively. Otherwise, when dealing with the cloud connector, you cannot be 100% sure that you’re using a fully protected connection for access.

To import an SSL certificate, proceed as follows:

1.  From the menu on the left, navigate to Connector • Configuration.
    
2.  Under the USER INTERFACE tab, navigate to the UI Certificate section.
    
3.  Click the Generate Certificate Signing Request icon ![inline image](bilder/icon_generate.png)to create your own certificate request or the click the Import a Certificate icon ![inline image](bilder/icon_upload.png)to upload a certificate file with a private key and the intermediate certificates, as shown in [Figure 5.8](#05_002.html#f5.8).
    

[![Cloud Connector Administration: Generating or Uploading an SSL Certificate](bilderklein/klein05_08.png)](img-f5.8.html) 

**Figure 5.8**     Cloud Connector Administration: Generating or Uploading an SSL Certificate

We recommend that you request a certificate through your trusted CA and then package a private key and the intermediate certificate(s) in a Privacy-Enhanced Mail (PEM) file. Such a text file contains all the certificates in a chain, from the root certificate to the actual certificate. You can then upload this file. With this approach, you’ll save the signing process (i.e., downloading, signing, and then reuploading the certificate signing request), and authentication using the certificate is just as secure.

###### \[»\]  Further Information on Secure Network Connection

To get a good handle on the firewall between your corporate network and SAP BTP, we recommend reading SAP Note 2377425.

The portable version of the cloud connector is started from the command line using the go command. If you close the window or cancel the process by pressing the key combination (Ctrl) + (C), you also stop the cloud connector.

Productive installations are started and stopped as a service in Windows, which can be controlled by calling the Services app in the Start menu. In Linux, use the scc\_daemon service. In the Bash shell, enter the following commands:

```
service scc_daemon start 
service scc_daemon stop 
service scc_daemon status 
```

To secure the execution of the service processes, SAP recommends using your own service accounts. To facilitate administration, the cloud connector offers the ability to create these service accounts directly via the administration console. For this task, in the full version, navigate to Connector • Security Status and choose the Set up service user specifically for this connector function.

To ensure that network content can only be logged in a network trace if two users are involved in the process, you should take the following precautions:

*   On Windows, with a non-service user, create a file named writeHexDump in the scc\_config subdirectory of the cloud connector directory. The content of this file is initially allowed=false.
    
*   On Linux, create the writeHexDump file in the /usr/local/vl/base/cfg or /opt/sap/scc/scc\_config directory (cloud connector version 2.x and later) and do not set permissions for this file for the scctunnel user. The content of this file is also initially allowed=false.
    

With these settings, traces can only ever be created with two users, which means a higher level of data protection.

### 5.2.3    Connection to SAP BTP

At this point, you’ve completed the somewhat optional steps for configuring the cloud connector. Next, you can connect the cloud connector to SAP BTP, which is done at the subaccount level. A separate connection must be created for each individual subaccount to be connected. The subaccounts are uniquely identified via their IDs.

To connect the cloud connector to SAP BTP on the individual subaccount level, follow these steps:

1.  In the administration console for the cloud connector, navigate to the Connector area.
    
2.  Click on the \+ Add Subaccount button (see [Figure 5.9](#05_002.html#f5.9)).
    
    [![Cloud Connector Administration: Connecting a New Subaccount](bilderklein/klein05_09.png)](img-f5.9.html) 
    
    **Figure 5.9**     Cloud Connector Administration: Connecting a New Subaccount
    
3.  In the window that opens, enter the connection data for your SAP BTP subaccount, as shown in [Figure 5.9](#05_002.html#f5.9).
    
4.  In the Region field, select the data center that you’ve chosen for your subaccount. The environment (Neo or Cloud Foundry) of the subaccount is also derived from this choice.
    
5.  Optionally, specify a display name for the connection in the Display Name field.
    
6.  In the Subaccount User field, make sure to enter your S-user or P-user ID in SAP BTP, Neo environment. For SAP BTP, Cloud Foundry environment, an email address will be used.
    
7.  Enter the ID of your subaccount in the Subaccount field.
    
8.  Click the Save button to complete the connection setup.
    

###### \[+\]  Finding the ID of the Subaccount

You can find out the ID of your subaccount in the SAP BTP cockpit of SAP BTP, Cloud Foundry environment by clicking the more icon ![inline image](bilder/icon_actionmenu.png)and then navigating to detailed information for the subaccount, as shown in [Figure 5.10](#05_002.html#f5.10). In SAP BTP, Neo environment, you can find the ID in a similar way, as shown in [Figure 5.11](#05_002.html#f5.11).

[![Subaccount ID in SAP BTP, Cloud Foundry Environment](bilderklein/klein05_10.png)](img-f5.10.html) 

**Figure 5.10**     Subaccount ID in SAP BTP, Cloud Foundry Environment

[![Subaccount ID in SAP BTP, Neo Environment](bilderklein/klein05_11.png)](img-f5.11.html) 

**Figure 5.11**     Subaccount ID in SAP BTP, Neo Environment

Now, you’ll see an overview view of the new connection. Click the Connect button to connect the cloud connector to your SAP BTP subaccount, as shown in [Figure 5.12](#05_002.html#f5.12).

[![Establishing the Connection](bilderklein/klein05_12.png)](img-f5.12.html) 

**Figure 5.12**     Establishing the Connection

This connection can now be used to set up further connections between your network and SAP BTP on both sides. Switching between the subaccounts is performed in the cloud connector via the Subaccount dropdown list, as shown in [Figure 5.12](#05_002.html#f5.12), at the top.

### 5.2.4    Further Recommendations for Secure Configuration

SAP recommends providing for failover in your cloud applications for situations where, for example, a data center is unavailable. In cases defined by failover, the application will then run on the infrastructure of another data center (called active/passive failover). Alternatively, you can offer the same service in two data centers and applications simultaneously (called active/active failover).

Such failover can help if SAP BTP is unreachable at some point but does not affect the cloud connector connections. If these connections are interrupted, the cloud application cannot compensate so easily. To pre-empt this case, SAP recommends installing the cloud connector twice with identical settings. You can then switch between the two installations via master shadow logic. The dependent server in this scenario is called a shadow instance.

When setting up a shadow instance, consider the following:

*   If using the LDAP protocol for cloud connector authentication, this protocol must be set up before setting up high availability. We’ll return to the setup of LDAP authentication in [Section 5.3](#05_003.html#h5.3).
    
*   The two instances of the cloud connector must be able to communicate with each other without a proxy.
    
*   Ideally, the two cloud connector instances connect to the Internet via different uplinks or proxies. This setting depends on your company’s specifications.
    
*   Only one master instance and one shadow instance are possible.
    
*   You’ll be asked the first time you call up the cloud connector whether a cloud connector is to be operated as a master instance or shadow instance. However, you can still change this setting later.
    

To configure this scenario, follow these steps:

1.  Within the administration console of the cloud connector, navigate to Connector • High Availability.
    
2.  Use the Enable or Disable button at the top right to toggle the high availability setting for the connection of a subaccount, as shown in [Figure 5.13](#05_002.html#f5.13).
    

Open the action menu by clicking the three dots icon ![inline image](bilder/icon_actionmenu.png). From this menu, you can switch between the role of the master instance and that of the shadow instance for the current cloud connector instance.

[![Cloud Connector Administration: Configuring High Availability](bilderklein/klein05_13.png)](img-f5.13.html) 

**Figure 5.13**     Cloud Connector Administration: Configuring High Availability

If the two instances are connected, the master instance provides the shadow instance with the complete configuration as well as provides information about itself. If the master instance fails, the standby instance takes over after the defined timeout values are reached and attempts to connect to SAP BTP. SAP BTP then opens a tunnel to the standby instance, which then takes over the tasks of the master instance.

###### \[+\]  Number of Cloud Connector Instances

If many systems are connected or availability requirements for your productive system are high, you should consider using a development cloud connector and a productive cloud connector. In addition, if availability requirements are high, you should consider a high-availability installation.

Since the cloud connector does not work with a database in the background, one recommendation regarding the data security and encryption of connections is to include the complete file system of the cloud connector in the planned daily backups in your company. Encrypting the file system is also a good idea to prevent the misuse of logon data (e.g., for logging on to the SAP BTP subaccount).

### 5.2.5    Monitoring

For monitoring, the cloud connector provides several application programming interfaces (APIs). These APIs are also used by SAP Solution Manager, among other SAP solutions.

The following data can be accessed via the available APIs:

*   Connection checks
    
*   Subaccounts
    
*   Open connections
    
*   Performance monitor
    
*   Consumers with the largest time consumption
    

We’ll introduce several APIs for monitoring in this section. Monitoring APIs must be authenticated using either HTTP authentication (basic authentication) or with a user name and password entry form (form-field authentication). A user accessing the monitoring data via the APIs must be assigned the role sccmonitoring and/or sccadmin.

The base URL for API access is /api/v1/configuration/. Simply append the desired API endpoint to this URL. Let’s look at a few examples:

*   Health Check API  
    Using the Health Check API, you can detect whether the cloud connector is reachable. The purpose of this health check is only to verify that the cloud connector is up. Neither internal states nor tunnel connections are checked. The call is made via the URL endpoint /exposed?action=ping.
    
*   Subaccounts API  
    With the Subaccounts API, you can read out a list of all subaccounts of SAP BTP that are connected to the cloud connector. Additionally, you access detailed information about each subaccount. The call is made via the URL endpoint /api/monitoring/subaccounts.
    
*   Backend Connections API  
    The Backend Connections API allows you to get a list of all backend systems currently connected to the cloud connector and access further information about each connection. This API is called using the URL endpoint /api/monitoring/connections/backends.
    
*   Performance Monitor API  
    The Performance Monitor API allows you to read the data determined by the cloud connector’s Performance Monitor. This API is called via the URL endpoint /api/monitoring/performance/backends.
    
*   Top Time Consumers API  
    The Top Time Consumers API allows you to read the data provided by the cloud connector’s performance monitor about the consumers that consume the most time. This API is called using the URL endpoint /api/monitoring/performance/toptimeconsumers.
    

###### \[+\]  Connecting the Cloud Connector to SAP Solution Manager

The cloud connector can be connected to SAP Solution Manager via the saphostcontrol operating system process and the cloud connector APIs. Whether you implement such access in your company depends on your network topology and the monitoring components used.

## 5.3    Authentication Methods

In this section, you’ll learn how to log on to the cloud connector itself. Depending on the roles you have, you can access different functions in the cloud connector.

After installing the cloud connector, the solution uses a file-based user store. Users are stored in the users.xml file in the config subdirectory of the cloud connector. Passwords are encrypted with a keystore certificate located in the same directory.

This file-based authentication is sufficient for smaller cloud connector installations. However, for larger installations, we recommend that you integrate file-based authentication with your company’s LDAP directory. With LDAP authentication, users are authenticated against your company’s LDAP directory service.

The following roles can then be assigned to users authenticated in this way:

*   sccadmin: This role has full administrative rights in the cloud connector.
    
*   sccdisplay: This role enables the display of all data in the cloud connector.
    
*   sccsupport: This role is used to display data and support activities (e.g., to activate traces).
    
*   sccmonitoring: This role is required to access the monitoring APIs of the cloud connector.
    

These roles can be used to differentiate between users who are only allowed to view the configuration and those who are responsible for the administration functions.

To switch from file-based authentication to LDAP-based authentication, follow these steps:

1.  On the cloud connector administration console, navigate to Connector • Configuration.
    
2.  Under the USER INTERFACE tab, switch to the Authentication section.
    
3.  To update the authentication method, click the ![inline image](bilder/icon_wechseln.png)icon, as shown in [Figure 5.14](#05_003.html#f5.14).
    
4.  A configuration dialog box opens where you can set the parameters for LDAP authentication. Maintain the Host field and other credentials for your connection. Select the Secure Host option to use the Lightweight Directory Access Protocol over SSL (LDAPS) protocol.
    
    [![Cloud Connector Administration: Changing the Authentication Method](bilderklein/klein05_14.png)](img-f5.14.html) 
    
    **Figure 5.14**     Cloud Connector Administration: Changing the Authentication Method
    
5.  In the Configuration field, enter the rest of the LDAP configuration, namely, the default user path and search pattern (userBase and userSearch) and the group path including search pattern (roleBase and roleSearch), as shown in [Figure 5.15](#05_003.html#f5.15).
    
    [![Cloud Connector Administration: LDAP Authentication Settings](bilderklein/klein05_15.png)](img-f5.15.html) 
    
    **Figure 5.15**     Cloud Connector Administration: LDAP Authentication Settings
    
6.  Use the Test LDAP Configuration icon ![inline image](bilder/icon_test_config.png)in the upper-right corner to test your settings. We recommend clicking this icon before saving the configuration.
    
7.  Activate the LDAP authentication via the Activate button.
    

###### \[ ! \]  Do Not Use Talking User Accounts

If the user data of your LDAP directory is used via the cloud connector for authentication to SAP BTP, you must consider some security aspects. Do not use prefixes or suffixes to indicate users who have administrative access to systems in the cloud as administration users. For example, if you use a user name with the scheme <user>ADM for the configuration of your local Windows servers, you should not use this scheme in the cloud. Otherwise, attacks from the Internet could target these accounts specifically. If a user named MA00019 could be both an employee with the personnel number 19 and an employee with the name abbreviation MA, identifying these accounts as administration users for a brute force attack is already more difficult. If you use corresponding user names, you might consider providing only the users path of the LDAP directory for LDAP authentication and not providing the administrators branch for the cloud.

To turn LDAP authentication off again, the useFileUserStore file is available in the cloud connector directory. This file ensures that the system sets the authentication back to file-based authentication when the file is found, even though you may have previously switched to LDAP authentication. In production systems, we therefore recommend that you delete this file after enabling LDAP authentication or set it as non-executable.

## 5.4    Cloud-to-On-Premise Connections

All connections from SAP BTP to your on-premise systems are enabled in the cloud connector. In addition to the type of connection (e.g., ABAP system), you’ll specify the connection data of the system and also how authentication is to take place.

### 5.4.1    Security Precautions

Permissions for cloud-to-on-premise connections can be set at a granular level. For example, for connections based on the HTTP protocol, you can restrict access to a specific URI. For RFC connections, you can specify the exact name of the function module(s) that can be called in the on-premise system. An exception in this context are connections to SAP HANA databases via the Transmission Control Protocol (TCP), where access cannot be further restricted.

Experience has shown that the authorization of certain resources and functions quickly raises the question of how granular a level you should work, especially since authorization checks are also carried out in the respective connected system. This question must be answered depending on your use case. If you connect a productive SAP ERP system to SAP BTP and, for example, only want to access three function modules of the SAP ERP system, mentioning these modules explicitly in the resource filter of the connection makes sense. The reason is simple: Another user with more authorizations could log on to the SAP ERP system via the cloud. This user would then sometimes have access to function modules that should not be called remotely.

###### \[+\]  Using Wildcards

If resources that may be accessed cannot be restricted so precisely, a good idea is to use wildcards. For example, the resource filter BAPI\* could be used to catch access to the critical function module RFC\_READ\_TABLE. How you can define these filters is described in detail in [Section 5.4.3](#05_004.html#h5.4.3).

For HTTP connections, you can also apply a filter on explicit paths as well as use wildcards and specify subdirectories. If an ABAP-based SAP system is to be connected to the cloud, but only individual web applications are to be released, we recommend, for example, releasing the /sap/public/\* paths in connection with the corresponding concrete service (which would then be under /sap/bc/... and not /sap/public/... ).

By using virtual host names, the fully qualified domain name (FQDN) or server name of the host in the local network is not transparent to a consumer from SAP BTP. The main security consideration behind this lack of transparency is so that no conclusions can be drawn about the function within the internal corporate network (since the names are not known). But the possibility of load balancing also plays a role in this context.

The virtual host name can no longer be changed. For this task, access would have to be completely re-created. However, you can change the connection data or the URIs behind virtual names at any time, which provides a certain degree of flexibility if, for example, a new server name is assigned in the local network or an existing virtual name needs to be tested against another instance.

###### \[»\]  Unique Virtual Host Names

When using multiple cloud connectors in your organization, make sure that the virtual host names used are unique so you can track which connection is being used.

Mappings for the host names of your on-premise systems must be performed for the virtual host names created. This rule applies to all connections (on ABAP and SAP HANA systems, on URIs, etc.). In practice, a useful approach is to use virtual host names similar to this URI instead of sapDEV01s.company.com as the local server name (e.g., cloudERPdev.company.com). This choice allows the SAP ERP or SAP S/4HANA development system to be addressed in the abstract. If this system is no longer accessible via the sapDEV01s server, but via a new system ID (SID) on another server, your URI would still be meaningful.

You should also consider the SSL certificates used in such virtual connections. If you choose the virtual host name in a different domain, such as server.cloud.local, you don’t make your company name or domain transparent to the cloud connector, but you must worry about an SSL certificate being issued for the server.company.eu domain, even though you requested it in the virtual environment for server.cloud.local. This situation is solvable, but it must be considered. In any case, the solution should not be to not check or only partially check the certificates used “internally” here. One possible approach would be to issue deliberately unique certificates to the source server or to use virtual host configurations on the source side of the communication. For SAP systems, a good presentation of this approach is available in the SAP Community Wiki at [http://s-prs.de/v809809](http://s-prs.de/v809809).

Changes in the configuration of the cloud connector are logged in the cloud connector audit log, which can be accessed by navigating to Subaccount • Audits. Analytical data on these connections is also available by navigating to Subaccount • Monitoring.

If a more detailed analysis of the transferred data is required, you can configure logging settings and download the results by navigating to Subaccount • Log and Trace Files and following these steps:

1.  Switch to edit mode by clicking on the pencil icon ![inline image](bilder/icon_pen.png), as shown in [Figure 5.16](#05_004.html#f5.16).
    
    [![Cloud Connector Administration: Logging Settings](bilderklein/klein05_16.png)](img-f5.16.html) 
    
    **Figure 5.16**     Cloud Connector Administration: Logging Settings
    
2.  Now, you can set the logging level in the Cloud Connector Loggers field, as shown in [Figure 5.17](#05_004.html#f5.17). Note that a lot of data is generated during a level trace and that the generated data may contain sensitive information. For productive systems, the Error level should usually be sufficient; Warning is suitable for troubleshooting. On development systems, you can log even more if necessary.
    
    [![Cloud Connector Administration: Selecting the Logging Level](bilderklein/klein05_17.png)](img-f5.17.html) 
    
    **Figure 5.17**     Cloud Connector Administration: Selecting the Logging Level
    
3.  The other fields indicate other logging tools (Other Loggers), which were usually developed in-house; the CPIC Trace Level field for Java Connector (JCo) connections to SAP systems; and the Payload Trace field enables the precise checking of HTTP data traffic. The SSL Trace field is used to check for secure transmission, in particular, for the correct encryption. All these traces are activated only when needed.
    
4.  In the Automatic Cleanup field, you can specify whether the generated logs should be deleted after a defined time, especially to minimize their space requirements.
    

In this context, refer to SAP Note 2452568, which deals specifically with logs and log files.

### 5.4.2    Setting Up the Connection

Currently, the following on-premise systems are available for connection via the cloud connector:

*   ABAP systems, including SAP S/4HANA, SAP ERP, and SAP BW
    
*   SAP HANA (native SAP HANA databases)
    
*   SAP NetWeaver Application Server (SAP NetWeaver AS) for Java and Java-based SAP systems, such as SAP Enterprise Portal
    
*   SAP Composition Environment, for connecting composite applications running on this platform
    
*   SAP Business Connector, for integrating middleware systems
    
*   SAP Process Integration, for connecting SAP Process Integration or SAP Process Orchestration and Enterprise Application Integration (EAI) messages
    
*   SAP Gateway, for connecting systems to each other
    
*   Other SAP systems that can be addressed via supported protocols
    
*   Non-SAP systems, for web addresses that do not point to an SAP system
    

The following protocols are supported for data exchange:

*   HTTP for “classic” Internet communication (i.e., between web pages, OData services, etc.)
    
*   LDAP for communication with LDAP-enabled directory services
    
*   RFC for communication with ABAP systems
    
*   TCP for network communication via the Internet protocol
    

Encrypted counterparts are also supported for each of the following connection types: HTTPS, LDAPS, RFC SNC, and TCP SSL.

To set up a new connection between a cloud-based system and an on-premise system in the cloud connector, follow these steps:

1.  First, navigate to the Subaccount • Cloud To On-Premise section, as shown in [Figure 5.18](#05_004.html#f5.18).
    
    [![Cloud Connector Administration: Configuring a Cloud-to-On-Premise Connection](bilderklein/klein05_18.png)](img-f5.18.html) 
    
    **Figure 5.18**     Cloud Connector Administration: Configuring a Cloud-to-On-Premise Connection
    
2.  Click on the plus sign icon ![inline image](bilder/icon_plus.png)above the list of connections to create a new connection.
    
3.  On the following Add System Mapping screen, select which type of system should be enabled for access from the cloud, as shown in [Figure 5.19](#05_004.html#f5.19). Continue by clicking Next.
    
    [![Selecting the Type of On-Premise System](bilderklein/klein05_19.png)](img-f5.19.html) 
    
    **Figure 5.19**     Selecting the Type of On-Premise System
    
4.  The next step is to select the protocol to be used for communication, as shown in [Figure 5.20](#05_004.html#f5.20). Depending on the selection of the system type, protocols that do not fit are grayed out from this list. We recommend selecting an encrypted connection type at this point. Then, click Next.
    
    [![Protocol Selection during System Setup](bilderklein/klein05_20.png)](img-f5.20.html) 
    
    **Figure 5.20**     Protocol Selection during System Setup
    
5.  In the next step, depending on the connection type, the relevant internal host is queried first (e.g., via the host name and port or via internal SAP connection data). Specify the addresses so that they can be contacted directly by the host on which the cloud connector is running.
    
    [Figure 5.21](#05_004.html#f5.21) shows as an example connection with an SAP system via a web address—one of the most common use cases. Continue with Next.
    
    [![Connecting an SAP System via HTTP](bilderklein/klein05_21.png)](img-f5.21.html) 
    
    **Figure 5.21**     Connecting an SAP System via HTTP
    
6.  Specify the Virtual Host name of the system, as shown in [Figure 5.22](#05_004.html#f5.22). In this case, we recommend using some kind of alias that indicates, on a semantic level, which system you’re dealing with, for example, dev-erp for an SAP ERP development system or dev-erp-cc1 for “Connection to the SAP ERP development system via Cloud Connector 1.” Click Next.
    
    [![Mapping to a Virtual Host Name](bilderklein/klein05_22.png)](img-f5.22.html) 
    
    **Figure 5.22**     Mapping to a Virtual Host Name
    
7.  The next step is to set the authentication settings. [Figure 5.23](#05_004.html#f5.23) shows the None setting for HTTP connections. This setting only has an effect if you set up principal propagation as the authentication method. The Kerberos option is the logon standard for Windows, while X.509 certificates are industry standards. Continue with Next.
    
    [![Setting Up the Authentication Method for the Connection](bilderklein/klein05_23.png)](img-f5.23.html) 
    
    **Figure 5.23**     Setting Up the Authentication Method for the Connection
    
8.  In the next step, configure the HOST field in the HTTP header, as shown in [Figure 5.24](#05_004.html#f5.24). Depending on whether you want the virtual server or the internal server to be transparent, you can have that defined in the header. Click Next one more time.
    
    [![Configuring the HOST Field in the HTTP Header](bilderklein/klein05_24.png)](img-f5.24.html) 
    
    **Figure 5.24**     Configuring the HOST Field in the HTTP Header
    
    ###### \[»\]  Meaning of the HOST Field in the HTTP Header
    
    When you select the virtual host, the originally requested host is carried in the X-Forwarded-Host HTTP header, as with a reverse proxy. The HOST field in the HTTP header is then used to distinguish where a request comes from. This information is important in ABAP systems, for example, for the correct generation of URIs. For more details, see SAP Note 750292.
    
9.  In the penultimate step, you can enter a description for the connection, for example, the number of the change request or the ticket in which the request was made.
    
10.  To ensure that the internal host is reachable from the cloud connector, specify that the connection should be checked by selecting the Check Internal Host checkbox, as shown in [Figure 5.25](#05_004.html#f5.25).
     
     [![Checking the Internal Server When Creating a Connection](bilderklein/klein05_25.png)](img-f5.25.html) 
     
     **Figure 5.25**     Checking the Internal Server When Creating a Connection
     
11.  Close the wizard by clicking the Finish button.
     

You have now created a system mapping. Note that the internal server name is now final and cannot be changed (except by creating a new mapping). However, by editing the entry, you can change the internal server at any time. So, in our example, you could change the server to be accessed by going to https://dev-erp-customer.external:10000/ from the cloud. This behavior is similar to a connection created in Transaction SM59 from an ABAP system or a destination from an SAP NetWeaver Java stack.

### 5.4.3    Configuring Access Control

However, the system mapping alone does not mean that access is available. For this purpose, you must control individual permitted access via access control lists (ACLs). In the cloud connector, these lists of permitted access are managed in the Resources area.

Resources can be authorized individually or via prefixes. A URI /services/service1 can therefore be authorized in the same way as a URI /services/\*. The same applies if RFC access is enabled via the cloud connector. In this case, you can either allow access to a specific RFC function module or to all RFC function modules by creating the filter with a prefix (e.g., BAPI\_USER\*).

On development systems, you can often get by with the /\* pattern; on production systems, a more precise restriction is desirable. When setting up access filters, also keep in mind that most SAP systems offer a share of public services. In the ABAP stack, these services can be found in Transaction SICF, under the /public/\* subnode. For RFC connections, these are individual services in the SYST group, such as the RFC\_PING function module.

To configure the access control, follow these steps:

1.  Navigate to Subaccount • Cloud To On-Premise.
    
2.  Under the ACCESS CONTROL tab, you’ll see the list of your connections. Click the plus icon ![inline image](bilder/icon_plus.png)below this list to add a new resource, as shown in [Figure 5.26](#05_004.html#f5.26).
    
3.  On the following Add Resource screen, specify the name of the resource and whether the resource is valid with all URIs derived from it (Path And All Sub-Paths), as shown in [Figure 5.27](#05_004.html#f5.27).
    
    [![Entry Point for Creating Resources](bilderklein/klein05_26.png)](img-f5.26.html) 
    
    **Figure 5.26**     Entry Point for Creating Resources
    
    [![Setting Up a Resource for HTTP/HTTPS](bilderklein/klein05_27.png)](img-f5.27.html) 
    
    **Figure 5.27**     Setting Up a Resource for HTTP/HTTPS
    
    ###### \[»\]  No Wildcard Required
    
    You do not need to enter an asterisk (\*) in the URL Path field to use a wildcard. Whether the links are valid with or without sub-paths is defined solely by selecting Path Only or Path And All Sub-Paths.
    
4.  The WebSocket checkbox allows HTTP connections between client and server to remain open. This setting allows a server to send messages to a client without reconnecting. This technique is often used to send live updates to users without them having to reload the corresponding web page. If your application doesn’t really need this setting, you should leave this checkbox deselected because open connections always have an impact on performance.
    
5.  In the Description field, you can add some documentation text.
    
6.  Save your resource by clicking the Save button.
    

An example of configuring a resource for an RFC connection is shown in [Figure 5.28](#05_004.html#f5.28). In this case, too, you can specify the name of an RFC-enabled function module without an asterisk (\*).

[![Creating an RFC Resource](bilderklein/klein05_28.png)](img-f5.28.html) 

**Figure 5.28**     Creating an RFC Resource

For further security, you can restrict RFC connections to certain clients. For this task, click on the authority icon ![inline image](bilder/icon_acl.png)in the Actions column in the list of connections, as shown previously in [Figure 5.26](#05_004.html#f5.26). The Edit Authority for Client and User screen opens, as shown in [Figure 5.29](#05_004.html#f5.29). In the lower part of this popup window, you can block access for certain clients and users.

[![Restricting Access for RFC Connections](bilderklein/klein05_29.png)](img-f5.29.html) 

**Figure 5.29**     Restricting Access for RFC Connections

###### \[ ! \]  Permissions for Access to Services and URIs

The permissions that can be assigned in the cloud connector do not replace the implementation and checking of permissions in the target system.

The following requirements must be fulfilled for access to a URI of an ABAP system:

*   If SAP Web Dispatcher is used, a corresponding ACL must also be defined. This also applies when using the icm/HTTP/auth profile parameters in the ABAP stack.
    
*   For OData services from SAP Gateway, the authorization S\_SERVICE must be checked.
    
*   The node(s) must be activated in Transaction SICF.
    
*   The authorizations in the service must also be implemented for the calling user.
    

The following requirements must be fulfilled for access to an ABAP system via an RFC connection:

*   The user may need the authorizations S\_RFC, S\_RFCACL, or S\_RFC\_TT with the corresponding service rights.
    
*   For the use of the authorization object S\_RFC, we recommend referring to SAP Note 2498923.
    
*   Additional ABAP authorizations are usually checked in the respective RFC module.
    

The other settings you should maintain for cloud-to-on-premise connections concern cookies. Web cookies are used by many applications to identify or authenticate users in web applications, for instance, single sign-on (SSO) cookies. Cookies can only ever be sent from one Internet domain to the same domain. This restriction applies to all Internet browsers to serve as a safeguard. In many cases, however, the virtual and internal host names are in different domains (in our example, customer.internal and customer.external).

Therefore, if applications are used that require cookies, the cookies must be implemented in the cloud connector by following these steps:

1.  Switch to the COOKIE DOMAINS tab, as shown in [Figure 5.30](#05_004.html#f5.30).
    
    [![Mapping Cookie Domains for HTTP(S) Connections](bilderklein/klein05_30.png)](img-f5.30.html) 
    
    **Figure 5.30**     Mapping Cookie Domains for HTTP(S) Connections
    
2.  In the pane on the left, you can see which virtual domains replace the internal domains specified in the right pane. The replacement is then performed by the cloud connector.
    

Starting from SAP BTP, you can also make further safeguards at the application level for messages in the direction of your on-premise systems. These safeguards are cloud applications, such as Java, HTML5, or SAP HANA extended application services (SAP HANA XS) applications developed on SAP BTP. You can categorize these applications as trusted applications. For an overview of the applications in the SAP BTP cockpit, navigate to Applications • HTML5 Applications. [Figure 5.31](#05_004.html#f5.31) shows an example of three cloud-based human resources (HR) applications in SAP BTP, Neo environment.

[![Applications in the SAP BTP Cockpit](bilderklein/klein05_31.png)](img-f5.31.html) 

**Figure 5.31**     Applications in the SAP BTP Cockpit

The names of authorizations for applications in the cloud connector are now composed of the application name and the subaccount. You can see the authorization for the first application hcmfabcommon (shown in [Figure 5.31](#05_004.html#f5.31)) in the cloud connector, as shown in [Figure 5.32](#05_004.html#f5.32). Enter this application into the ACL, under the APPLICATIONS tab, by adding the application via the plus icon ![inline image](bilder/icon_plus.png). If an application exists, it can be accessed this way.

[![Trusted Applications in the Cloud Connector](bilderklein/klein05_32.png)](img-f5.32.html) 

**Figure 5.32**     Trusted Applications in the Cloud Connector

In the Tunnel Connections Limits list, you can optionally define the maximum number of connections allowed for the trusted applications. However, we don’t recommend intervening at this point, as this setting can result in errors. Unexpected terminations could occur when the limit is reached.

Under the PRINCIPAL PROPAGATION tab, you can define which individual identity providers are trusted for authenticating users between the cloud and on-premise systems.

### 5.4.4    Enabling the SAP Connectivity Service

Essential to using the connections is enabling the SAP Connectivity service in the service marketplace. The SAP Connectivity service enables applications to combine services, is virtually the substructure of connections, and is thus a prerequisite for being able to use connections at all.

[Figure 5.33](#05_004.html#f5.33) shows the Service Marketplace in the SAP BTP cockpit. In our example, the list of services is filtered to SAP Integration Suite services. The tile for calling the SAP Connectivity service is shown on the second line. Next to that tile, you’ll see the SAP Destination service, which we’ll need in [Section 5.5](#05_005.html#h5.5). This service must also be enabled first to use it.

[![SAP Destination Service and SAP Connectivity Service in the Service Marketplace](bilderklein/klein05_33.png)](img-f5.33.html) 

**Figure 5.33**     SAP Destination Service and SAP Connectivity Service in the Service Marketplace

To activate each of these services, find the appropriate tile and select New Instance to create a new service instance.

###### \[»\]  Recommendations for Using the Connections

After completing the steps described in this section, connections to on-premise systems can be established. SAP makes the following recommendations for these connections:

*   Using constants for system users and passwords
    
*   Using destinations as modeling level (similar to the RFC destinations from Transaction SM59 in the ABAP environment)
    

Furthermore, for establishing connections from SAP BTP, Cloud Foundry environment with the appropriate authentication via HTTPS, we recommend using the extended services for user account and authentication (XSUAA). We covered this topic in more detail in [Chapter 4](#04_001.html#h4), [Section 4.4.3](#04_004.html#h4.4.3).

[Figure 5.34](#05_004.html#f5.34) shows the connection setup again schematically. We have completed the registration of the cloud connector with the SAP BTP subaccount, but now we need to set up a destination, which we describe in the following section. This destination is optional, but is used for clean encapsulation and, if you’ll, to replace connection data with a textual constant.

[![Schematic of On-Premise System Connectivity with Destinations Considered](bilderklein/klein05_34_source.png)](img-f5.34.html) 

**Figure 5.34**     Schematic of On-Premise System Connectivity with Destinations Considered

To check whether the cloud connector can correctly connect to the SAP BTP environment after connecting the cloud connector, navigate to Connectivity • Cloud Connectors. You’ll see connected cloud connector instances. For a connection to work, a cloud connector must have the status Connected, as shown in [Figure 5.35](#05_004.html#f5.35).

###### \[»\]  Transporting Connections

Conveniently, you can transport or save your connections via import and export functions both on the cloud connector level and on the SAP BTP level. The icons for the Import System Mappings ![inline image](bilder/icon_upload.png)and Export System Mappings ![inline image](bilder/icon_export.png)functions are located directly in SAP BTP (as shown earlier in [Figure 5.26](#05_004.html#f5.26)).

[![Connected Cloud Connector Instances](bilderklein/klein05_35.png)](img-f5.35.html) 

**Figure 5.35**     Connected Cloud Connector Instances

## 5.5    Setting Up the SAP Destination Service

Destinations are created in SAP BTP. Their main purpose is to help you cleanly model outbound connections. These connections can connect to on-premise applications or to other cloud applications. However, all connections work according to the same scheme. A destination provides access to a web address or the host address of an ABAP server, for example, via an abstract name. In the case of access to a remote resource, if the cloud connector is active and the addressing is correct, access is routed via the cloud connector using the On Premise connection type.

In this section, we’ll look at the role of destinations in the context of the cloud connector.

A prerequisite for using destinations is the activation of the SAP Destination service in the SAP BTP cockpit. You can model destinations without activating this service, but at the latest, if you want to access a destination from a cloud application, the service must be active in your space in SAP BTP, Cloud Foundry environment. This service is activated in the same way as the SAP Connectivity service, which we described in [Section 5.4.4](#05_004.html#h5.4.4). In SAP BTP, Neo environment, the service is active by default.

###### \[»\]  Securing Communication When Using Destinations

For information on securing destinations, refer to [Chapter 2](#02_001.html#h2), [Section 2.1.1](#02_001.html#h2.1.1), where you’ll find a detailed description of how trusted certificates are generated, especially for HTTPS connections. We won’t cover this topic further in this section.

In this section, you’ll learn how to set up destinations in SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment.

### 5.5.1    Creating Destinations in SAP BTP, Neo Environment

To create destinations in SAP BTP, Neo environment, navigate to Connectivity • Destinations and click the New Destination button. [Figure 5.36](#05_005.html#f5.36) shows the screen for setting up an HTTPS connection.

[![Creating an HTTP(S) Destination](bilderklein/klein05_36.png)](img-f5.36.html) 

**Figure 5.36**     Creating an HTTP(S) Destination

In the URL field, enter the URI of the virtual server, along with the virtual port, and specify the Type (i.e., HTTP or HTTPS). The Proxy Type field controls where the destination of the connection is located (OnPremise or on the Internet).

In the Name field, give the connection a unique name. Optionally, a longer description can be added in the Description field.

In the Authentication field, you can configure the authentication of users at the connection level, for example, if a Security Assertion Markup Language (SAML) ticket or another type of authentication is to be used to communicate with the connection.

Finally, you can store a location in the Location ID field. If used, this specification must match the IDs used when configuring the cloud connector (as shown earlier in [Figure 5.7](#05_002.html#f5.7)). By default, therefore, this field remains empty.

If the target is an SAP system, specify the property sap-client to the desired client. For this task, click on the New Property button. You’ll be offered a list of properties that can be set optionally. In practice, only the sap-client setting is relevant. If further settings are required, these settings can be found in the documentation of the cloud application that is to be connected.

The situation is similar for RFC connections. In this case, too, the virtual host name is used. If metadata and application data should be transmitted separately (i.e., for example, the metadata is queried via a function module with a dedicated user), a distinction can be made between User and Repository User on the creation screen, as shown in [Figure 5.37](#05_005.html#f5.37). The optional Repository User (with its corresponding Repository Password) is used to query the metadata, and the User (with its Password) is used for all other data, for instance, the specific function module calls.

[![Creating an RFC Destination](bilderklein/klein05_37.png)](img-f5.37.html) 

**Figure 5.37**     Creating an RFC Destination

For the connection data, all properties of the JCo can be maintained in the properties. This connector is the only way to directly access remote-enabled function modules of an ABAP system. This capability works similarly to an HTTP(s) connection. For example, when connecting via the message server, select the property jco.client.mshost, and when connecting via the application server, select jco.client.ashost.

After creating and saving a destination, you can test the connection by clicking the Check Connection button. If problems with the certificates for HTTP(S) connections exist, you can find possible solutions in [Chapter 2](#02_001.html#h2), [Section 2.1.1](#02_001.html#h2.1.1).

If a connection can be established successfully, configuring the permissions on both the subscription level and on the application level make sense. This procedure is described in [Chapter 2](#02_001.html#h2), [Section 2.1.2](#02_001.html#h2.1.2).

Connections to SAP Web IDE are a special case. If the cloud connector is to be used to connect an application developed in SAP Web IDE, the extended settings of the connection, under Additional Properties, must be maintained. As shown in [Figure 5.38](#05_005.html#f5.38), for example, the following properties of the connection have been configured:

*   WebIDEEnabled = true enables the connection for SAP Web IDE.
    
*   WebIDESystem = gateway controls access to SAP Gateway.
    
*   WebIDEUsage = odata\_gen, odata\_abap, bsp\_execute\_abap denotes the executable actions.
    

[![Additional Parameters for Connections to SAP Web IDE](bilderklein/klein05_38.png)](img-f5.38.html) 

**Figure 5.38**     Additional Parameters for Connections to SAP Web IDE

### 5.5.2    Creating Destinations in SAP BTP, Cloud Foundry Environment

To create a destination in SAP BTP, Cloud Foundry environment, navigate to Connectivity • Destinations in your subaccount. Click on the New Destination button. On the creation screen, enter the virtual host name in the URL field to set up a connection via the cloud connector, as shown in [Figure 5.39](#05_005.html#f5.39). Choosing the On-Premise option in the Proxy Type field makes it clear that the connection is to be routed via a cloud connector.

If you develop a cloud application in SAP BTP, Cloud Foundry environment, in our example, the abstract name ERP-DEV can now be used for the destination to resolve the corresponding URI.

[![SAP BTP, Cloud Foundry Environment: Creating a Destination](bilderklein/klein05_39.png)](img-f5.39.html) 

**Figure 5.39**     SAP BTP, Cloud Foundry Environment: Creating a Destination

To secure the connections and for any certificate issues, refer to [Chapter 2](#02_001.html#h2), [Section 2.1.1](#02_001.html#h2.1.1).

## 5.6    Checklist for Cloud Connector Configuration

[Table 5.1](#05_006.html#t5.1) provides a checklist for administering secure connections with the help of SAP’s cloud connector.

 
| Completed || Task |
| --- | --- |
|  || You’ve specified that the cloud connector is mandatory when developing cloud services and applications that use an on-premise backend system. Ideally, this requirement has been added to your development guidelines. |
| --- | --- |
|  || You’ve defined how many cloud connector instances will be installed, distributed geographically to optimize failsafe. Also consider whether developers should have local cloud connector instances running on their devices. |
|  || You’ve developed a concept for the maintenance of your cloud connector instances. You should determine which cloud connector instance will be upgraded first in response to feature upgrades, and you should ensure that the connections are tested correctly. |
|  || You’ve defined who should have access to the cloud connector. Some possibilities are administrators and developers, but also other groups of users might need viewing rights. |
|  || Depending on who is getting access, you should have clarified whether you want to use a connection to an LDAP directory to authenticate users. Such a connection makes sense in many cases, especially if several users need access. |
|  || A monitoring concept for the cloud connector has been developed. As a guide, you can use concepts that are already available for monitoring other system connections in your company. Make sure you also record who is responsible for monitoring. |
|  || You’ve defined a location for documenting cloud connector connections. In this context, use your development guidelines to check whether documentation within cloud connector is sufficient or determine what other documentation will be affected. An important step is to record the subaccounts and the connected cloud connector instances. |
|  || If data protection requirements apply to the data transmitted via the cloud connector, we advise following the four-eyes principle when monitoring network traces. |
|  || You’ve reached agreement on how high the availability of the connection should be. SAP generally recommends a redundant, high-availability connection. Also consider your own internet uplink and work out a fallback scenario. This scenario usually requires extensive clarification with network teams. |
|  || You’ve developed a naming convention for virtual host names and destinations. The naming rule can be technical (e.g., use “FI” for “finance”) or application specific (e.g., use “MTE” for “mobile travel expenses” applications) but should be consistent throughout. |
|  || You’ve defined processes for the activation of services and documented which people must be informed by which means. |

**Table 5.1**     Checklist for Configuring the Cloud Connector

## 5.7    Real-World Examples of Secure Cloud Connector Configuration

Scenarios for using the cloud connector are diverse. In this section, we’ve put together some typical use cases for you: connecting to a local Git server and accessing an SAP S/4HANA system. You’ll also learn how to configure LDAP authentication.

### 5.7.1    Connecting an On-Premise Git Server to SAP BTP, Neo Environment

Git is a free software product that enables version control for the source files of your development projects. The open-source software was invented by Linus Torvalds, creator of Linux. In this section, we’ll show you how to connect a Git server to SAP BTP, Neo environment. We chose this scenario for our first real-life example because we realized that few companies care about how the source files are managed when using SAP Web IDE. However, this consideration should be a central issue since you can save these files in SAP Web IDE, but you must export them manually and import them again whenever another developer wants to work on the same application. When deploying an SAP Fiori application to an ABAP repository, only the compiled application files are transferred, not the source files. We therefore recommend that you actually carry out the following steps for connecting a Git repository in your company.

In this section, we assume that your development team consists of several people who develop cloud applications on SAP Web IDE. Within your on-premise system landscape, you already have a Git server for managing all the source files of these developments.

The following preconditions must be met:

*   You must know the credentials for your Git server.
    
*   The cloud connector must have been installed and configured as described earlier in [Section 5.2](#05_002.html#h5.2).
    
*   Ideally, you should already have access to SAP Web IDE.
    

First, you’ll configure the cloud connector so that it allows a connection to your Git repository. Keep in mind that Git is not an SAP system.

For this configuration task, follow these steps:

1.  Within the administration console of the cloud connector, first select the SAP BTP subaccount on which SAP Web IDE is running, as shown in [Figure 5.40](#05_007.html#f5.40).
    
    [![Cloud Connector Administration: Subaccount Overview](bilderklein/klein05_40.png)](img-f5.40.html) 
    
    **Figure 5.40**     Cloud Connector Administration: Subaccount Overview
    
2.  Select the Cloud To On-Premise menu item. Under the ACCESS CONTROL tab, click the plus icon to create a new system mapping.
    
3.  Select the system type option Non-SAP System from the Back-end Type dropdown list, as shown in [Figure 5.41](#05_007.html#f5.41).
    
    [![Selecting the System Type for Non-SAP Systems](bilderklein/klein05_41.png)](img-f5.41.html) 
    
    **Figure 5.41**     Selecting the System Type for Non-SAP Systems
    
4.  Depending on the server, select the connection type HTTP or HTTPS. We recommend you choose the more secure HTTPS connection option.
    
5.  In the next popup window, select the Git server using its internal host name within your company network, as shown in [Figure 5.42](#05_007.html#f5.42).
    
    [![Git Server Selection](bilderklein/klein05_42.png)](img-f5.42.html) 
    
    **Figure 5.42**     Git Server Selection
    
6.  On the next page, you can create a virtual name for the server. In our example, we chose the name “virtualgitserver:8443.” In productive environments, the use of a virtual name makes sense.
    
7.  In the next step, leave the setting None in the Principal Type field, as shown in [Figure 5.43](#05_007.html#f5.43). In this step, you could configure the use of certificate-based authentication.
    
    [![Selecting the Principal Type](bilderklein/klein05_43.png)](img-f5.43.html) 
    
    **Figure 5.43**     Selecting the Principal Type
    
8.  In the last step, confirm your settings by clicking Finish.
    

The result is an entry in the ACL, under the ACCESS CONTROL tab, that allows access to the Git server. You can test the access by clicking the Check availability of the internal host icon ![inline image](bilder/icon_test_config.png), as shown in [Figure 5.44](#05_007.html#f5.44).

[![Testing of the System Connection](bilderklein/klein05_44.png)](img-f5.44.html) 

**Figure 5.44**     Testing of the System Connection

Now, let’s unlock all paths, which is performed in the Resources Of <xxx> table. First, enable all subpaths via the / entry by clicking on the plus icon ![inline image](bilder/icon_plus.png). The result is shown in [Figure 5.45](#05_007.html#f5.45). This process allows a connection to all directory paths on the Git server.

[![Unlocking Resource Paths](bilderklein/klein05_45.png)](img-f5.45.html) 

**Figure 5.45**     Unlocking Resource Paths

Next, we’ll need a destination to the Git server:

1.  Log on to your subaccount in SAP BTP, Neo environment.
    
2.  Navigate to Connectivity • Destinations.
    
3.  Click on New Destination.
    
4.  In the Name field, select the virtual name that you have assigned to the Git server in the cloud connector, as shown in [Figure 5.46](#05_007.html#f5.46). In the URL field, enter the URI of the Git server. You can leave the default settings in the other fields.
    
    [![Creating a Destination in the SAP BTP Cockpit](bilderklein/klein05_46.png)](img-f5.46.html) 
    
    **Figure 5.46**     Creating a Destination in the SAP BTP Cockpit
    
5.  Click New Property and make the following additional settings:
    
    *   WebIDEEnabled = true
        
    *   HTML5.DynamicDestination = true
        
6.  Finally, save this destination by clicking the Save button.
    

The next step is to use the Git integration in SAP Web IDE to create a project that has been cloned from the Git repository to SAP Web IDE. Follow these steps:

1.  Call SAP Web IDE, click on the File icon ![inline image](bilder/icon_file.png). Then, navigate to GIT • Clone Repository from the menu, as shown in [Figure 5.47](#05_007.html#f5.47).
    
    [![Copying the Git Repository to SAP Web IDE](bilderklein/klein05_47.png)](img-f5.47.html) 
    
    **Figure 5.47**     Copying the Git Repository to SAP Web IDE
    
2.  Enter the virtual server in the URL field and the correct Git repository as the end of the URI (in our example, [http://virtualgitserver:8443/Repo.git](http://virtualgitserver:8443/Repo.git)).
    

In the cloned project, Git operations are now available via the context menu, as shown in [Figure 5.48](#05_007.html#f5.48).

[![Git Operations in the Cloned Project](bilderklein/klein05_48.png)](img-f5.48.html) 

**Figure 5.48**     Git Operations in the Cloned Project

### 5.7.2    Connecting SAP BTP, Cloud Foundry Environment to an SAP S/4HANA System

Many companies require a connection between an on-premise SAP S/4HANA system to SAP BTP, Cloud Foundry environment, so that data from the on-premise system can be accessed from SAP BTP.

To create this connection, the following prerequisites must first be met:

*   You must have the system data for your SAP S/4HANA system (i.e., servers, ports, etc.).
    
*   The SAP S/4HANA system must be accessible for your cloud connector.
    
*   You must have the access data for your subaccount in SAP BTP, Cloud Foundry environment. Your subaccount should have been set up in the cloud connector, as described in [Section 5.2](#05_002.html#h5.2).
    
*   Instances for the SAP Destination service and the SAP Connectivity service have been created in the SAP BTP subaccount. This step must be performed in all spaces in which the destination is to be used. You can also perform the activation later.
    

In the first step, include the SAP S/4HANA server in a cloud-to-on-premise connection via HTTP(S):

1.  In the cloud connector administration console, navigate to Define Subaccount • Cloud To On-Premise, as shown in [Figure 5.49](#05_007.html#f5.49).
    
    [![Cloud To On-Premise View](bilderklein/klein05_49.png)](img-f5.49.html) 
    
    **Figure 5.49**     Cloud To On-Premise View
    
2.  Now, we’ll create a new system mapping. Select the system type ABAP System, as shown in [Figure 5.50](#05_007.html#f5.50).
    
3.  In the following step, select the connection type HTTP or HTTPS, depending on the requirements of your company.
    
    [![Selecting the System Type for an SAP S/4HANA Connection](bilderklein/klein05_50.png)](img-f5.50.html) 
    
    **Figure 5.50**     Selecting the System Type for an SAP S/4HANA Connection
    
4.  Enter the internal name and port of the SAP S/4HANA system, as shown in [Figure 5.51](#05_007.html#f5.51).
    
    [![Entering the Internal Name and Port](bilderklein/klein05_51.png)](img-f5.51.html) 
    
    **Figure 5.51**     Entering the Internal Name and Port
    
5.  Now, you can assign a virtual name in the next step. For our example, we’ll use the name s4demo.test.sap and port 8000. Click Next.
    
6.  For the Principal Type field, leave the existing value (None).
    
7.  Send the internal host name in the HTTP header. For this task, select the Use Internal Host option, as shown in [Figure 5.52](#05_007.html#f5.52).
    
    [![Passing the Internal Host Name in the HTTP Header](bilderklein/klein05_52.png)](img-f5.52.html) 
    
    **Figure 5.52**     Passing the Internal Host Name in the HTTP Header
    
8.  Confirm your settings by clicking Next.
    

Make sure that the connection test is positive by clicking the ![inline image](bilder/icon_test_config.png)icon. In the list of system mappings, the Reachable status should appear in the Check Result column, as shown in [Figure 5.53](#05_007.html#f5.53).

[![Example Connection with the Check Status Reachable](bilderklein/klein05_53.png)](img-f5.53.html) 

**Figure 5.53**     Example Connection with the Check Status Reachable

To enable RFC calls to the SAP S/4HANA system, you’ll need to repeat these steps. This time, however, you would select the RFC option as the connection type instead of HTTP(S). You may also need to provide other connection data, depending on your backend system (for example, message server or application server).

As a final result, you now have two connections: one RFC connection and one HTTP(S) connection. The Reachable status should be displayed for both connections, as shown in [Figure 5.54](#05_007.html#f5.54).

[![Overview of the System Mappings with Both Connections](bilderklein/klein05_54.png)](img-f5.54.html) 

**Figure 5.54**     Overview of the System Mappings with Both Connections

Now, we have created the basis for configuring the resources. In our example, access is allowed to all resources under the URL path /sap as well as to the function module BAPI\_USER\_GETDETAIL. For this task, click the plus icon ![inline image](bilder/icon_plus.png)above the list of resources. Add the HTTP resource with all subpaths, as shown in [Figure 5.55](#05_007.html#f5.55), as well as the RFC resource for the function module BAPI\_USER\_GET\_DETAIL for the connections created, as shown in [Figure 5.56](#05_007.html#f5.56).

[![Adding a Resource for a URL Path](bilderklein/klein05_55.png)](img-f5.55.html) 

**Figure 5.55**     Adding a Resource for a URL Path

[![Adding a Resource for an ABAP Function Module](bilderklein/klein05_56.png)](img-f5.56.html) 

**Figure 5.56**     Adding a Resource for an ABAP Function Module

Save your resources. As a result, the corresponding destinations are unlocked. To use these resources in SAP BTP, Cloud Foundry environment, you still need to create destinations for both cloud-to-on-premise connections, which can be used to address the SAP S/4HANA system. We’ll cover this topic next.

The configuration of the destination for an RFC connection is shown in [Figure 5.57](#05_007.html#f5.57). Note the Additional Properties section at the bottom of the screen. In this section, you can define connections to the application server of the SAP S/4HANA system. In the Name field, reference the system using the virtual host name.

[![Configuring a Destination for an RFC Connection](bilderklein/klein05_57.png)](img-f5.57.html) 

**Figure 5.57**     Configuring a Destination for an RFC Connection

The configuration of the destination for the HTTP connection also refers to the virtual host name, as shown in [Figure 5.58](#05_007.html#f5.58). In this case, we’ve added the parameter sap-client in the Additional Properties field to address the correct client immediately.

[![Configuring a Destination for the HTTP Connection](bilderklein/klein05_58.png)](img-f5.58.html) 

**Figure 5.58**     Configuring a Destination for the HTTP Connection

The result is shown in [Figure 5.59](#05_007.html#f5.59). We now have a destination HTTPS4DEV for HTTP connections, and a destination RFCS4DEV for RFC connections. Now, cloud applications of SAP BTP can connect to the SAP S/4HANA system in the local company network via the cloud connector.

[![Destinations Created](bilderklein/klein05_59.png)](img-f5.59.html) 

**Figure 5.59**     Destinations Created

If the SAP S/4HANA system has not yet been made known to your SAP BTP subaccount, you must import the SSL certificate at this point, as described in [Chapter 2](#02_001.html#h2), [Section 2.1.3](#02_001.html#h2.1.3). For direct HTTP access, the XSUAA proxy must be used.

### 5.7.3    LDAP Authentication Configuration

If many people need access to applications connected via the cloud connector, we commend connecting an LDAP-enabled directory service. Configuring authentication via LDAP is one of the main steps in configuring the cloud connector. Therefore, let’s look at this configuration with an example. In this example, we assume the requirement that not only the administration user has to log on to the cloud connector. For example, a developer may have an interest in checking the connections in case of malfunctions. Your company already uses an LDAP directory service, which you would now like to use for logging on to the cloud connector.

The following prerequisites must be met to perform the steps described in this section:

*   You’ve clarified from which paths of the LDAP directory service the users and groups that are to access the cloud connector are to be read.
    
*   You’ve clarified which attributes are to be mapped.
    
*   You’ve clarified which system user is allowed to log on via LDAP.
    
*   You've enabled the technical connection between the cloud connector and the LDAP connector.
    

First, we’ll configure the cloud connector to authenticate against your LDAP directory service by following these steps:

1.  Log on to the cloud connector and select the Configuration menu area.
    
2.  On the USER INTERFACE tab, switch to the Authentication block, as shown in [Figure 5.60](#05_007.html#f5.60).
    
    [![Starting an LDAP Connection](bilderklein/klein05_60.png)](img-f5.60.html) 
    
    **Figure 5.60**     Starting an LDAP Connection
    
3.  Click on the double arrow icon ![inline image](bilder/icon_wechseln.png)to open the General LDAP Configuration view.
    
4.  Match the values to those of your LDAP directory service and click Activate, as shown in [Figure 5.61](#05_007.html#f5.61).
    
    [![Configuring LDAP Authentication](bilderklein/klein05_61.png)](img-f5.61.html) 
    
    **Figure 5.61**     Configuring LDAP Authentication
    
5.  Note the settings under Custom Roles, shown in [Figure 5.62](#05_007.html#f5.62). In these fields, you can assign your own roles in your LDAP directory to the four default roles of the cloud connector: Administrator Role, Support Role, Display Role, and Monitoring Role. These default roles were described in [Section 5.3](#05_003.html#h5.3).
    

[![Assigning User-Defined Roles to Default Roles](bilderklein/klein05_62.png)](img-f5.62.html) 

**Figure 5.62**     Assigning User-Defined Roles to Default Roles

To assign the Display Role to all users, enter “every\_user” in the Display Role field. In our example, we have a role named every\_user for all users in the LDAP directory service.

The cloud connector will now reboot. You can then log on to the cloud connector using your LDAP credentials. You can click the Test LDAP Configuration icon ![inline image](bilder/icon_test_config.png)in the General LDAP Configuration view to test the configuration. If you’ve made a mistake or if logging on is not possible for some other reason, refer to the instructions provided in [Section 5.3](#05_003.html#h5.3).

## 5.8    Summary

In this chapter, you learned about the cloud connector, which links your on-premise and cloud systems. We began by exploring the architecture, and then we walked you through installing and configuring the cloud connector. You learned about several relevant authentication methods, and then we set up and secured some cloud-to-on-premise connections. We then discussed key settings for the SAP Destination service to create destinations in SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. We also provided a handy checklist for checking your cloud connector configuration. Finally, we explored some real-world examples of secure configuration for the cloud connector, including connecting to an on-premise Git server, connecting to SAP S/4HANA, and connecting using LDAP authentication.

# 6    Administration Tools

Administering SAP Business Technology Platform (SAP BTP) via the command line or via application programming interfaces (APIs) can help you perform common tasks even more efficiently. You can also integrate SAP BTP into your existing administration tools.

For the most part, SAP BTP is administered via the SAP BTP cockpit. However, there are some tasks that can only be performed using the command-line tools, which are called command-line interfaces (CLIs). In addition, you might have a requirement to automate certain activities or to use existing tools.

SAP offers a command-line tool both in SAP BTP, Neo environment and in SAP BTP, Cloud Foundry environment. We’ll show you how to use the tools for SAP BTP, Neo environment in [Section 6.1](#06_001.html#h6.1). We covered the command line for SAP BTP, Cloud Foundry environment in [Chapter 4](#04_001.html#h4), [Section 4.1](#04_001.html#h4.1). The main reason for this placement is that certain functions in this environment can only be administered via the command line. In [Section 6.2](#06_002.html#h6.2), we’ll introduce another command-line tool for the administration of global accounts in both SAP BTP environments.

In addition, SAP also provides APIs for certain functions. These APIs are typically expressed as OData APIs and documented in SAP API Business Hub. In [Section 6.3](#06_003.html#h6.3), you’ll learn how to access SAP BTP functions using APIs. In [Section 6.4](#06_004.html#h6.4), you’ll find a checklist for working with command-line tools and APIs. Finally, in [Section 6.5](#06_005.html#h6.5), we walk you through some examples of how to use the command line for certain administration tasks.

###### \[»\]  APIs for the Cloud Connector

For information on the APIs for the cloud connector, see [Chapter 5](#05_001.html#h5), [Section 5.2](#05_002.html#h5.2).

## 6.1    Administering SAP BTP, Neo Environment via the Command Line

The CLI is provided by SAP for download on the SAP Development Tools website at [https://tools.hana.ondemand.com](https://tools.hana.ondemand.com), in the Cloud section. Working with the command line differs significantly between SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. This difference exists because the command line in SAP BTP, Neo environment is a proprietary SAP tool, while a standardized implementation is used for SAP BTP, Cloud Foundry environment.

We described the installation of the SAP BTP software development kit (SDK) for SAP BTP, Neo environment and the setup of the command line in [Chapter 3](#03_001.html#h3), [Section 3.1](#03_001.html#h3.1). In this section, we’ll present some commands for the command line that, in our experience, are frequently used to administer SAP BTP, Neo environment.

An example call is shown in [Figure 6.1](#06_001.html#f6.1).

[![Calling the SAP BTP SDK for SAP BTP, Neo Environment](bilderklein/klein06_001.png)](img-f6.1.html) 

**Figure 6.1**     Calling the SAP BTP SDK for SAP BTP, Neo Environment

To access a list of all subaccounts, use the command shown in [Listing 6.1](#06_001.html#l6.1). In addition to the technical name of your subaccount, the user name of the subaccount admin and the host are passed.

```
./neo.sh list-accounts 
       --account <technicalnameofyoursubaccount> 
       --user <SubaccountUser> 
       --host <host> 
```

**Listing 6.1**     Reading a List of All Subaccounts

Note that you must log on with one of your subaccounts to get a list of all subaccounts.

Alternatively, you have the option of not supplying the parameters directly attached to the command, as in [Listing 6.1](#06_001.html#l6.1), but to instead store these parameters in a file. For this task, create a file with all the necessary parameters via a text editor or via the command line itself (on Linux, for example, with the touch command and the vi editor; on Windows with the editor provided). Name the file clouddna.properties. The contents of this file for an example subaccount query is shown in [Listing 6.2](#06_001.html#l6.2).

```
##SubAccount
account=yourSubAccountId
##user
user=yourSubAccount userId
##password
password=yourSubAccountPassword
##host
host=SubAccountHost 
```

**Listing 6.2**     Contents of a clouddna.properties Parameter File

This file is then called with the following command:

```
./neo.sh list-accounts clouddna.properties 
```

To get the result in a machine-readable format, you can additionally supply the parameter output with the value json. In this case, you must also supply the password of the subaccount user as well.

Another interesting use case of the Neo console is the creation of a database tunnel between the on-premise landscape and SAP BTP. The SAP HANA service in SAP BTP, Neo environment does not include any tools for direct access to database contents (indirect access via SAP Web IDE is possible). For such access, many developers and administrators prefer to use tools that run on their own computers or in their own system landscapes, such as DataGrip. Such tools use Java Database Connectivity (JDBC) as the protocol for data access. However, the SAP HANA service does not allow a direct database connection using JDBC, for network reasons.

Therefore, as an alternative, the Neo console can be used to connect to a database using the command shown in [Listing 6.3](#06_001.html#l6.3).

```
./neo.sh open-db-tunnel 
       --account <yourSubAccountId> 
       --user <yourSUser> 
       --host eu1.hana.ondemand.com 
       -i <dbInstanceName> 
```

**Listing 6.3**     Setting Up a Database Tunnel

Again, the data for your subaccount (ID, user, and host) is passed. The only difference from the commands shown so far is the \-i parameter. This parameter is the ID of the database or database schema. After the connection has been successfully established, you’ll see the JDBC URL, instance number, and user displayed in the Neo console, as shown in [Figure 6.2](#06_001.html#f6.2). You can then use this information in your preferred tool to access the database.

[![Database Tunnel Information](bilderklein/klein06_002.png)](img-f6.2.html) 

**Figure 6.2**     Database Tunnel Information

###### \[»\]  Setting Up a Service Channel in SAP BTP, Cloud Foundry Environment

You can also set up a corresponding connection in SAP BTP, Cloud Foundry environment. However, in this case, you would create a service channel in the cloud connector. For more information, refer to SAP Help Portal at [http://s-prs.de/v809810](http://s-prs.de/v809810).

###### \[+\]  Further Commands

A detailed description of further commands for SAP BTP, Neo environment can be found at SAP Help Portal at [http://s-prs.de/v809811](http://s-prs.de/v809811).

## 6.2    Managing Global Accounts via the Command Line

The SAP BTP CLI is the command-line tool for all administration tasks related to the global account, subaccounts, and directories. Directories are used to group subaccounts into a directory structure (see also [Section 6.5.2](#06_005.html#h6.5.2)). You can use the SAP BTP CLI for both SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. Note, however, that SAP BTP CLI is used exclusively for managing global accounts, (i.e., the top structural level). In your subaccounts, you’ll need to use the specific command-line tools for either SAP BTP, Neo environment or SAP BTP, Cloud Foundry environment. With the SAP BTP CLI, you can create and update subaccounts and manage authorizations, among other things.

The SAP BTP CLI is installed locally on your computer. Download the tool via the URL [https://tools.hana.ondemand.com/#cloud](https://tools.hana.ondemand.com/#cloud). Navigate to the SAP BTP Command Line Interface (btp CLI) section, where you’ll find different versions for different operating systems, as shown in [Figure 6.3](#06_002.html#f6.3). Click on the link for your operating system to start the download.

[![Downloading the SAP BTP CLI](bilderklein/klein06_003.png)](img-f6.3.html) 

**Figure 6.3**     Downloading the SAP BTP CLI

###### \[»\]  Prerequisite for Use

To use the SAP BTP CLI, your global account must support feature set B as a cloud management tool. For more information, refer to the beginning of [Chapter 4](#04_001.html#h4).

To invoke the SAP BTP CLI help, use the following command in the console:

```
sapcp --help 
```

To work with the console, you must log on to SAP BTP via the command shown in [Listing 6.4](#06_002.html#l6.4).

```
sapcp login 
      --url https://cpcli.cf.eu10.hana.ondemand.com 
      --subdomain <yourSubdomain> 
      --user <yourEmailAddress> 
```

**Listing 6.4**     Logging on to SAP BTP via the Console

###### \[»\]  Logging on to SAP BTP Again

When you log on to SAP BTP from the console, a bearer token is created and stored on your client. This token gives you the ability to close and reopen the console without having to log on again. Each command you execute from the console renews this token. The token is valid for 24 hours.

To read out information about the global account, you can use the following command:

sapcp get accounts/global-account

The result of the call is shown in [Figure 6.4](#06_002.html#f6.4).

[![Global Account Information in the SAP BTP CLI](bilderklein/klein06_004.png)](img-f6.4.html) 

**Figure 6.4**     Global Account Information in the SAP BTP CLI

Other commands are entered in the same way. In [Section 6.5.2](#06_005.html#h6.5.2), we’ll cover some commonly used commands for managing SAP BTP with a practical example.

## 6.3    Administration via APIs

In addition to accessing SAP BTP via the console, SAP also provides APIs for certain activities. Both Representational State Transfer (REST) and OData APIs are offered. Using the APIs, HTTP methods are executed that access a specific URL endpoint. Different APIs are used for SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment.

###### \[»\]  HTTP Methods

For SAP BTP’s REST and OData APIs, the HTTP methods GET, POST, PUT, and DELETE are available:

*   Using the GET method, you can access a record or a list of records in read-only mode.
    
*   You can use the POST method to create a new record.
    
*   If you want to modify an existing record, you can use the PUT method. Optionally, you could also use the PATCH or MERGE methods. Which methods are offered depends on the API.
    
*   To delete an entity, use the DELETE method.
    

For some APIs, not all of these HTTP methods are offered.

In the following sections, we’ll show you how to locate and test APIs. Due to the wide variety of APIs, knowing how to navigate through the SAP API Business Hub API catalog and how to locate the appropriate APIs is vitally important.

### 6.3.1    SAP API Business Hub

SAP API Business Hub plays an important role in the SAP BTP environment. Among other things, all APIs are documented in this central location. SAP API Business Hub can be accessed at [https://api.sap.com](https://api.sap.com).

In SAP API Business Hub, navigate to the Categories tab, where you’ll find the APIs menu item. You can click the View All Categories link to call up the entire API catalog, as shown in [Figure 6.5](#06_003.html#f6.5).

[![SAP API Business Hub: Content Categories](bilderklein/klein06_005.png)](img-f6.5.html) 

**Figure 6.5**     SAP API Business Hub: Content Categories

In the API catalog, as shown in [Figure 6.6](#06_003.html#f6.6), you’ll find the SAP Cloud Integration tile. Click it to go to the APIs for SAP BTP.

SAP distinguishes between REST, Simple Object Access Protocol (SOAP), and OData APIs. For example, the API for reading the audit logs of SAP BTP is an OData API, and the API for accessing the SAP Destination service is implemented as a REST API. OData is based on REST technology, which means that OData APIs offer extended capabilities, but dealing with them is similar to dealing with REST APIs.

SAP API Business Hub provides you with the ability to test specific APIs directly. Click the SAP Cloud Integration tile and navigate to Integration Content • API Reference. This path takes you to the view shown in [Figure 6.7](#06_003.html#f6.7). Now, you can test the Integration Content API for Cloud Integration: Click the Try Out button. Then, maintain the required and optional parameters for the call and make a call directly either against a sandbox account provided by SAP or against your own subaccount of SAP BTP.

[![SAP API Business Hub: Overview of APIs](bilderklein/klein06_006.png)](img-f6.6.html) 

**Figure 6.6**     SAP API Business Hub: Overview of APIs

[![Testing APIs](bilderklein/klein06_007.png)](img-f6.7.html) 

**Figure 6.7**     Testing APIs

SAP API Business Hub also provides the option of creating code snippets for specific APIs. If you click on the Code Snippet link in the detailed view of an API, you can access the source code for calling the API in common programming languages. You can also use code snippets generated in this way for a call in the command line. [Figure 6.8](#06_003.html#f6.8) shows the generated code for a call to the API endpoint /IntegrationDesigntimeArtifacts using the command-line tool cURL.

[![Code Snippet for Calling an API Endpoint in the Console](bilderklein/klein06_008.png)](img-f6.8.html) 

**Figure 6.8**     Code Snippet for Calling an API Endpoint in the Console

###### \[»\]  cURL

cURL is a command-line tool that is offered free of charge for all operating systems that can simulate web requests in various protocols. Specific HTTP headers can be included, and the responses viewed, as in the example shown in [Figure 6.8](#06_003.html#f6.8). Further information can be found on the cURL website at [https://curl.se](https://curl.se).

### 6.3.2    Audit Log Retrieval via APIs

The Audit Log Retrieval API provides you the ability to retrieve audit logs from SAP BTP. This functionality allows you to integrate these audit logs into your own systems and processes, regardless of whether you otherwise use on-premise or cloud-based tools.

#### Retrieving the Audit Log from SAP BTP, Neo Environment

In SAP BTP, Neo environment, the Audit Log Retrieval API is provided as an OData API. For general information about this API, refer to SAP API Business Hub at [https://api.sap.com/api/AuditLogRetrievalAPI/](https://api.sap.com/api/AuditLogRetrievalAPI/overview).

Authentication is required to access the audit log data via the API. Authentication in SAP BTP, Neo environment is performed using OAuth. Therefore, as a prerequisite, an OAuth client must be created in the subaccount. Follow these steps:

1.  Open the SAP BTP cockpit of the subaccount and follow the menu path Security • OAuth.
    
2.  On the OAuth settings screen, open the Platform API tab.
    
3.  Click on the Create API Client button, as shown in [Figure 6.9](#06_003.html#f6.9).
    
    [![Creating a Platform API Client for OAuth Authentication](bilderklein/klein06_009.png)](img-f6.9.html) 
    
    **Figure 6.9**     Creating a Platform API Client for OAuth Authentication
    
4.  In the API client creation dialog box, you’ll need to define the desired scopes, that is, the content that is allowed to be accessed through the API and the APIs that will be used to access it. For our example, select the Audit Log Service in the API Name column and the values Read Audit Logs and Manage Audit Logs in the Scopes column, as shown in [Figure 6.10](#06_003.html#f6.10).
    
5.  Optionally, you can enter a description for the API client in the Description field. Finally, click Save.
    
6.  The next step displays the credentials for OAuth authentication, as shown in [Figure 6.11](#06_003.html#f6.11). The Client ID can still be viewed at a later time, but the Client Secret is only visible at this point. Client ID and Client Secret are used to authenticate the API user. After you’ve noted down the information, confirm with OK.
    

[![Defining APIs and Scopes for Access](bilderklein/klein06_010.png)](img-f6.10.html) 

**Figure 6.10**     Defining APIs and Scopes for Access

[![Credentials for OAuth Authentication](bilderklein/klein06_011.png)](img-f6.11.html) 

**Figure 6.11**     Credentials for OAuth Authentication

OAuth authentication is performed via an HTTP POST call to the "/oauth2/apitoken/v1?grant\_type=client\_credentials endpoint. The SubAccountId must be replaced with the technical name of the subaccount, and the RegionHost must be replaced with the host name of the associated data center. The call must be made with basic authentication; that is, the user name and password are sent in the HTTP header. This information is transmitted using the Base64 encoding method. The OAuth client ID must be used as the user name, and the OAuth client secret must be used as the password.

If authentication is successful, the response is output, as shown in [Listing 6.5](#06_003.html#l6.5). The API calls are authenticated using the token\_type and access\_token attributes included in the response.

```
{
    "access_token": "2d34fa92f748f7c16048f6ad6d60cc",
    "token_type": "bearer",
    "expires_in": 1500,
    "scope": "hcp.manageAuditLogs hcp.readAuditLogs"
} 
```

**Listing 6.5**     Response to API Call for OAuth Authentication

###### \[»\]  Bearer Token

A bearer token is a special key that is issued once. This token receives an access authorization issued by the respective target system in encrypted form via the access token (as shown in [Listing 6.5](#06_003.html#l6.5)). Instead of having to send a new combination of user name and password with each request, the token is sent along. It thus serves as a substitute for other authentication methods.

Reading the contents of the audit log is done via an HTTP GET call to the https://api.eu2.hana.ondemand.com/auditlog/v1/accounts/<SubAccountId>/AuditLogRecords endpoint.

The path component <SubAccountId> must also be replaced by the technical name of the subaccount. The HTTP header authorization must be supplied to authenticate the caller. As a value, the previously received token\_type must be concatenated with the access\_token, separated by a space. In the example response shown in [Listing 6.5](#06_003.html#l6.5), the value of the bearer token would correspond to the string 2d34fa92f748f7c16048f6ad6d60cc.

#### Retrieving the Audit Log of SAP BTP, Cloud Foundry Environment

In SAP BTP, Cloud Foundry environment, calling the audit log is a bit more involved than in SAP BTP, Neo environment. For information about the API, see the Audit Log Retrieval API for SAP BTP, Cloud Foundry environment in SAP API Business Hub at [https://api.sap.com/api/CFAuditLogRetrievalAPI](https://api.sap.com/api/CFAuditLogRetrievalAPI/overview).

The API requires OAuth authentication here as well. The prerequisite for this is the activation of an instance of the SAP Audit Log Management service in SAP BTP:

1.  Navigate to your subaccount in the SAP BTP cockpit and call up the service marketplace via Service • Service Marketplace.
    
2.  Search for the keyword “Auditlog Management.” Click on the Auditlog Management tile to access the detailed view of the service, as shown in [Figure 6.12](#06_003.html#f6.12).
    
    [![SAP BTP, Cloud Foundry Environment: SAP Audit Log Management Service in the Service Marketplace](bilderklein/klein06_012.png)](img-f6.12.html) 
    
    **Figure 6.12**     SAP BTP, Cloud Foundry Environment: SAP Audit Log Management Service in the Service Marketplace
    
3.  Click the Create Instance button to start the process of creating a new service instance, as shown in [Figure 6.13](#06_003.html#f6.13).
    
    [![Creating a Service Instance of the SAP Audit Log Management Service](bilderklein/klein06_013.png)](img-f6.13.html) 
    
    **Figure 6.13**     Creating a Service Instance of the SAP Audit Log Management Service
    
4.  In the dialog box for configuring and creating the service, enter a descriptive name for your instance in the Instance Name field, as shown in [Figure 6.14](#06_003.html#f6.14). You can leave blank fields blank. For other fields, you can leave the default values.
    
    [![Maintaining Service Information](bilderklein/klein06_014.png)](img-f6.14.html) 
    
    **Figure 6.14**     Maintaining Service Information
    
5.  Continue by clicking Next. Then, click your way through the creation wizard. No further entries should be required. Now, complete the creation of the instance by clicking Create Instance, as shown in [Figure 6.15](#06_003.html#f6.15).
    

[![Completing the Creation of the Instance](bilderklein/klein06_015.png)](img-f6.15.html) 

**Figure 6.15**     Completing the Creation of the Instance

You should now receive a success message. In this message, click View Instance to view the details of the service instance, as shown in [Figure 6.16](#06_003.html#f6.16).

[![View Service Instance](bilderklein/klein06_016.png)](img-f6.16.html) 

**Figure 6.16**     View Service Instance

The next step is to create a service key. For this task, navigate to the Service Keys section in the service instance details view and click the Create button, as shown in [Figure 6.17](#06_003.html#f6.17).

[![Creating a Service Key](bilderklein/klein06_017.png)](img-f6.17.html) 

**Figure 6.17**     Creating a Service Key

Enter a suitable technical name for the service key in the Service key name field and complete the creation process by clicking Create, as shown in [Figure 6.18](#06_003.html#f6.18).

[![Dialog Box for Creating a Service Key](bilderklein/klein06_018.png)](img-f6.18.html) 

**Figure 6.18**     Dialog Box for Creating a Service Key

Open the detailed view of the service key by clicking on its name in the service key overview, as shown in [Figure 6.19](#06_003.html#f6.19).

[![Jumping to the Service Key](bilderklein/klein06_019.png)](img-f6.19.html) 

**Figure 6.19**     Jumping to the Service Key

The service key contains all the information required for authentication and for calling the API for the audit log. [Figure 6.20](#06_003.html#f6.20) shows an example of a service key with the relevant properties. The service key is provided in JavaScript Object Notation (JSON) format. The top-level url attribute contains the endpoint for the API call. The uaa object also contains an attribute named url. This attribute is the endpoint used for OAuth authentication. The clientid attribute corresponds to the user name for the API call, and the clientsecret attribute corresponds to the associated password.

[![Structure of a Service Key](bilderklein/klein06_020.png)](img-f6.20.html) 

**Figure 6.20**     Structure of a Service Key

OAuth authentication is performed against the endpoint provided in the service key. Additional components must be added to the path of the endpoint. The final endpoint follows the following scheme:

<uaa.url>/oauth/token?grant\_type=client\_credentials

The call must be sent as an HTTP POST request with basic authentication. The clientid must be passed as the user name, and the clientsecret must be passed as the password. As a result, analogous to the call in SAP BTP, Neo environment, an OAuth response is sent in which the attributes token\_type and access\_token are supplied. These two attributes are used to authenticate the API calls.

For the API call, the path /auditlog/v2/auditlogrecords must be added to the endpoint. The endpoint should look like the following:

https://auditlog-management.cfapps.eu10.hana.ondemand.com/auditlog/v2/auditlogrecords

The call is sent as an HTTP GET request. For the authentication of the client, the HTTP header authorization must be sent. This information contains the result of the concatenation of token\_type and access\_token as value, using a space as a separator. An example result of the API call is shown in [Figure 6.21](#06_003.html#f6.21).

[![Result of the Audit Log Retrieval API Call](bilderklein/klein06_021.png)](img-f6.21.html) 

**Figure 6.21**     Result of the Audit Log Retrieval API Call

### 6.3.3    User Management via APIs

We’ve already recommended using a platform identity provider and thus managing the users of the cloud services in a central location. However, to create the users directly in SAP BTP subaccounts, SAP offers a suitable API for this purpose. You can also read out existing user master data via an API.

#### User Management in SAP BTP, Neo Environment

In SAP BTP, Neo environment, user administration can be performed via the Platform Authorizations Management API. Detailed information about this API can be found in SAP API Business Hub at [https://api.sap.com/api/AccountMembersManagementAPI/](https://api.sap.com/api/AccountMembersManagementAPI/overview).

Authentication is performed via OAuth, as discussed for the Audit Log Retrieval API in the previous section. For this purpose, an OAuth client must be created, as described in [Section 6.3.2](#06_003.html#h6.3.2). Assign the scopes Manage Account Members and Read Account Members for the Account Member Management API, as shown in [Figure 6.22](#06_003.html#f6.22).

###### \[ ! \]  Attention: Changing the Scopes

The assigned scopes for the OAuth client cannot be changed later. If you want to adjust the scopes, you must delete the existing OAuth client and create a new client with the desired scopes.

OAuth authentication is performed against the https://api.eu2.hana.ondemand.com/oauth2/apitoken/v1?grant\_type=client\_credentials endpoint.

[![Setting Scopes for the OAuth Client](bilderklein/klein06_022.png)](img-f6.22.html) 

**Figure 6.22**     Setting Scopes for the OAuth Client

Calling the API to read all users is performed against the https://api.eu2.hana.ondemand.com/authorization/v1/platform/accounts/<SubAccountId>/Users endpoint.

The <SubAccountId> path element must also be replaced with the technical name of the subaccount at this point. For authentication, the Authorization HTTP header must be passed with the bearer token. The result of an example valid request is shown in [Figure 6.23](#06_003.html#f6.23).

[![Result of a User Query via the API](bilderklein/klein06_023.png)](img-f6.23.html) 

**Figure 6.23**     Result of a User Query via the API

You can use the System for Cross-Domain Identity Management (SCIM) protocol to create users. This protocol is described in SAP API Business Hub at [https://api.sap.com/api/AccountMembersManagementAPI/resource](https://api.sap.com/api/AccountMembersManagementAPI/resource). You can test the protocol against your own subaccount at SAP API Business Hub.

#### User Management in SAP BTP, Cloud Foundry Environment

SAP also offers an API for user management in SAP BTP, Cloud Foundry environment, called the Authorization Management API. To use this API, the SAP Authorization and Trust Management service must be activated. For this task, navigate to Services • Service Marketplace in the SAP BTP cockpit. Click the Authorization & Trust Management tile in the service overview, as shown in [Figure 6.24](#06_003.html#f6.24).

[![SAP Authorization and Trust Management Service in the Service Marketplace of SAP BTP, Cloud Foundry Environment](bilderklein/klein06_024.png)](img-f6.24.html) 

**Figure 6.24**     SAP Authorization and Trust Management Service in the Service Marketplace of SAP BTP, Cloud Foundry Environment

Starting from the detail view of the service, create a new service instance by clicking the Create Instance button, as shown in [Figure 6.25](#06_003.html#f6.25).

[![Creating a Service Instance](bilderklein/klein06_025.png)](img-f6.25.html) 

**Figure 6.25**     Creating a Service Instance

The service is delivered in different instances, which are called service plans. For access via the API, an instance must be created with the apiaccess service plan. Select this service plan in the creation dialog box for the service instance, as shown in [Figure 6.26](#06_003.html#f6.26).

In the Service Plan field, select the apiaccess plan and assign a descriptive name for the instance in the Instance Name field. Leave the default values in the other required fields. Continue by clicking Next and go through the other steps of the creation process. Finally, click Create Instance.

[![Maintaining the Properties of the Service Instance](bilderklein/klein06_026.png)](img-f6.26.html) 

**Figure 6.26**     Maintaining the Properties of the Service Instance

Next, create a service key as described in [Section 6.3.2](#06_003.html#h6.3.2). The structure of the service key is slightly different from the service key for the Audit Log Retrieval API. In this case, the endpoint for authentication is contained in the url attribute, as shown in [Figure 6.27](#06_003.html#f6.27). As usual, the clientid corresponds to the user name, and the clientsecret corresponds to the password.

[![Service Key for the User Management API](bilderklein/klein06_027.png)](img-f6.27.html) 

**Figure 6.27**     Service Key for the User Management API

The user is authenticated via OAuth with the client\_credentials authentication type (grant\_type). If the authentication was successful, you can make SAP BTP calls against the API. Let’s consider an example of reading all the users of your subaccount. The call is made against the [https://api.authentication.eu10.hana.ondemand.com/Users](https://api.authentication.eu10.hana.ondemand.com/Users) endpoint. This call can be made without any additional parameters. [Figure 6.28](#06_003.html#f6.28) shows an example response to this request.

[![Result of Calling the User Management API](bilderklein/klein06_028.png)](img-f6.28.html) 

**Figure 6.28**     Result of Calling the User Management API

See [https://docs.cloudfoundry.org/api/uaa/version/75.1.0/index.html#users](https://docs.cloudfoundry.org/api/uaa/version/75.1.0/index.html#users) in SAP BTP, Cloud Foundry environment for documentation for all parameters that can be passed to the /Users endpoint.

### 6.3.4    Permission Management via APIs

For role and permission management, the Authorization Management API is provided, which in our experience is quite commonly used. This API also distinguishes between SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment.

#### Authorization Management in SAP BTP, Neo Environment

The documentation for the Authorization Management API for SAP BTP, Neo environment, unlike the APIs presented so far, is not found in SAP API Business Hub, but instead at [https://api.hana.ondemand.com/authorization/v1/documentation](https://api.hana.ondemand.com/authorization/v1/documentation). This REST API can only be used to manage application roles. You cannot use this API to manage platform roles. The API provides functions for managing roles and assigning roles to users. In addition to roles, it also covers user groups. The application roles are provided by the respective cloud application in the application descriptor. With the application descriptor, developers tell the cloud instance what is to be installed or deployed, including which roles are to be created in the cloud environment for correct operation of the application.

Authentication is performed via OAuth using client credentials. The token issued by the OAuth server has a validity of 25 minutes, and therefore, reauthenticating before each API call is not necessary.

This API is called in the same way as described for the Platform Authorizations Management API in [Section 6.3.3](#06_003.html#h6.3.3). We therefore won’t go into further detail. For more information, see SAP Help Portal at [http://s-prs.de/v809813](http://s-prs.de/v809813).

#### Authorization Management in SAP BTP, Cloud Foundry Environment

The assignment of roles and authorizations is implemented in SAP BTP, Cloud Foundry environment, by the SAP Authorization and Trust Management service. This service comprises a total of four APIs. [Figure 6.29](#06_003.html#f6.29) shows that the APIs are provided as REST APIs. Documentation for these APIs can be found in SAP API Business Hub at the URL [https://api.sap.com/package/authtrustmgmnt](https://api.sap.com/package/authtrustmgmnt).

[![APIs of the SAP Authorization and Trust Management Service](bilderklein/klein06_029.png)](img-f6.29.html) 

**Figure 6.29**     APIs of the SAP Authorization and Trust Management Service

The Authorization API is used to manage roles and authorizations. An API can provide different entities. In the case of the Authorization API, these entities are applications, roles, role templates, and composite roles, as shown in [Figure 6.30](#06_003.html#f6.30).

An example call to the Authorization API might be as follows:

/sap/rest/authorization/v2/apps/<AppId>/roles.

This call would return all the roles that exist for an SAP BTP application <AppId>.

The API calls work in the same way as the APIs presented in [Chapter 4](#04_001.html#h4), [Section 4.4](#04_004.html#h4.4). Therefore, we won’t elaborate further now.

[![Entities of the Authorization API](bilderklein/klein06_030.png)](img-f6.30.html) 

**Figure 6.30**     Entities of the Authorization API

### 6.3.5    SAP Cloud Management Service APIs

Administrative activities on SAP BTP can also be performed using APIs from the SAP Cloud Management service for SAP BTP. Similar to using the SAP BTP CLI, this functionality requires that feature set B is available in your global account.

APIs are provided through the service for the following management functions, as shown in [Figure 6.31](#06_003.html#f6.31):

*   Management of SAP BTP global accounts and subaccounts (Accounts API)
    
*   Allocation of resources (Entitlements API)
    
*   Provisioning of environments, quotas, and job statistics (Provisioning API)
    
*   Management of events (Events API)
    

The APIs for the SAP Cloud Management service are also called Core Service APIs for SAP BTP. The current documentation for these APIs can be found at [http://s-prs.de/v909814](http://s-prs.de/v909814).

SAP Cloud Management service APIs are protected with OAuth 2.0 and via user name and password. For certain APIs, the client authentication method is also used.

[![Core Service APIs](bilderklein/klein06_031.png)](img-f6.31.html) 

**Figure 6.31**     Core Service APIs

To consume these APIs, you must first activate the SAP Cloud Management service. For this task, in a subaccount of SAP BTP, Cloud Foundry environment, navigate to Services • Service Marketplace and call up the Cloud Management Service tile, as shown in [Figure 6.32](#06_003.html#f6.32).

[![SAP BTP, Cloud Foundry Environment: SAP Cloud Management Service in the Service Marketplace](bilderklein/klein06_032.png)](img-f6.32.html) 

**Figure 6.32**     SAP BTP, Cloud Foundry Environment: SAP Cloud Management Service in the Service Marketplace

Next, you’ll create a service instance. The service is deployed exclusively in the spaces of SAP BTP, Cloud Foundry environment. Therefore, you must maintain the Space field in the service instance creation dialog box, as shown in [Figure 6.33](#06_003.html#f6.33). We recommend that you group all services that are used for the administration of SAP BTP in a separate, dedicated space. Also, select an appropriate technical name for the service instance in the Instance Name field. In the Service Plan field, select the value central, and leave the default values in all other mandatory fields. Then, continue by clicking Next. After you have completed all the steps of the creation wizard, confirm your settings by clicking Create Instance.

[![Creating an Instance of the SAP Cloud Management Service](bilderklein/klein06_033.png)](img-f6.33.html) 

**Figure 6.33**     Creating an Instance of the SAP Cloud Management Service

After the service has been successfully deployed and the instance of the service is running in the selected space, a service key must be generated for this instance. For this task, navigate to the service instances overview screen and select the service instance we just created, as shown in [Figure 6.34](#06_003.html#f6.34).

Now, either jump to the details of the service instance using the link in the Service column or open the action menu ![inline image](bilder/icon_drei_punkte.png)in the right column of the overview to generate the service key. In the action menu, select the Create Service Key entry, as shown in [Figure 6.35](#06_003.html#f6.35). Then, create the service key as described in [Section 6.3.2](#06_003.html#h6.3.2), for SAP BTP, Cloud Foundry environment.

[![SAP BTP, Cloud Foundry Environment: Overview of Service Instances in the Dev Space](bilderklein/klein06_034.png)](img-f6.34.html) 

**Figure 6.34**     SAP BTP, Cloud Foundry Environment: Overview of Service Instances in the Dev Space

[![Creating a Service Key via the Action Menu](bilderklein/klein06_035.png)](img-f6.35.html) 

**Figure 6.35**     Creating a Service Key via the Action Menu

The service key contains all the relevant information you need to call the APIs. Click the name of the service key to access it, as shown in [Figure 6.36](#06_003.html#f6.36).

[![Accessing the Service Key](bilderklein/klein06_036.png)](img-f6.36.html) 

**Figure 6.36**     Accessing the Service Key

The service key includes the clientid and clientsecret attributes, as in the example shown in [Figure 6.37](#06_003.html#f6.37). The clientid corresponds to the user name in OAuth authentication, and the clientsecret corresponds to the password.

[![Showing a Service Key](bilderklein/klein06_037.png)](img-f6.37.html) 

**Figure 6.37**     Showing a Service Key

###### \[»\]  OAuth with User Name and Password

In OAuth authentication using user name and password (password credentials), basic authentication is performed via HTTP. For basic authentication, you must use the clientid as the user name and the clientsecret as the password. In addition, you must submit an HTTP body of type x-www-form-urlencoded with the key-value pairs for the grant\_type, username, and password attributes. The grant\_type key must be assigned the password value, the username key must be assigned the SAP BTP user’s email, and the password key must be assigned the password assigned to that user.

You can test the APIs directly at [https://accounts-service.cfapps.eu10.hana.ondemand.com/home](https://accounts-service.cfapps.eu10.hana.ondemand.com/home) using the web-based user interface (UI). This interface is based on the popular Swagger framework for web environments and is great for running and testing web applications and calls to services directly in the browser.

To test an API, select its corresponding tile on the overview screen. In the detailed view of the API, click the Try it out button, as shown in [Figure 6.38](#06_003.html#f6.38).

[![Testing an API of the SAP Cloud Management Service](bilderklein/klein06_038.png)](img-f6.38.html) 

**Figure 6.38**     Testing an API of the SAP Cloud Management Service

Next, let’s look at how you can use APIs to retrieve information from your global account and from subaccounts with two examples.

To retrieve the global account information, use an HTTP GET request to the path /accounts/v1/globalAccount. The result of the request is shown, for example, in [Figure 6.39](#06_003.html#f6.39). In this case, a trial account for SAP BTP was used. In addition to the global key (the guid), you can also query the name (displayName), the creation and modification information (createdDate and modifiedDate), the general status including explanation (entityState and stateMessage), and the Internet subdomain (subdomain). You can also access the contract status; commercial model; consumption-based billing controls and license types (contractStatus, commercialMode, consumptionBased, and licenseType); geographic activation in a region (geoAccess); and contract renewal dates (renewalDate).

[![Response to a Query for Global Account Information](bilderklein/klein06_039.png)](img-f6.39.html) 

**Figure 6.39**     Response to a Query for Global Account Information

To retrieve subaccount information, use an HTTP GET request to the path /accounts/v1/subaccounts. The result of an example request is shown in [Figure 6.40](#06_003.html#f6.40). You’ll find a global key (the GUID) as well as the key of the associated global account (globalAccoungGUID) and the parent node (parentGUID); if the subaccounts are nested in directories, you’ll also see the type of the parent node (parentType).

You can also query the name (displayName), creation and modification information (createdDate and modifiedDate), region (region), and status and general status message (state and stateMessage). In addition, you can retrieve information about the Internet subdomain (subdomain), the activation status of beta functions (betaEnabled), the activation of the production status (usedForProduction), the long description (description), the expiration date (expiryDate), the creator (createdBy), and the zone used (zoneId).

[![Exemplary Response Query of Subaccount Information](bilderklein/klein06_040.png)](img-f6.40.html) 

**Figure 6.40**     Exemplary Response Query of Subaccount Information

## 6.4    Checklist for Working with the Command Line and APIs

[Table 6.1](#06_004.html#t6.1) provides a checklist for working with the administration tools presented in this chapter.

 
| Completed || Task |
| --- | --- |
|  || You’ve determined who gets which administrative permissions for SAP BTP. Derived from this information, only these users should receive similar permissions for the command line. You’ve also defined where API access points and API keys are requested and managed. |
| --- | --- |
|  || You’ve defined where access to SAP BTP applications or via the APIs of SAP BTP applications are documented. |
|  || It has been agreed who is allowed to install the command-line tools on the respective company computers. |
|  || You’ve considered, especially with the APIs of SAP BTP, Cloud Foundry environment, that some APIs may change frequently (mostly functions are added, rarely changed). Therefore, you must ensure that regular checks are made in SAP API Business Hub to always look for newer and better approaches. |

**Table 6.1**     Checklist for Working with the Command Line and APIs

## 6.5    Real-World Examples of Using the Command Line Securely

Most administration and setup tasks can be performed in SAP BTP using the web interface. However, many everyday tasks can be performed using the command line, for instance, creating a custom domain, which must be done via the command line. Another example is managing the platform via the command line, which can be quite helpful to enhance automation, for example.

### 6.5.1    Using the Command Line to Configure a Custom Domain in SAP BTP, Neo Environment

SAP offers you the ability to use a user-defined domain (called a custom domain) on the subaccount level of SAP BTP. CloudDNA GmbH, for example, uses the domain [https://www.clouddna.at/](https://www.clouddna.at/) for its subaccount. To set up such a custom domain, different command-line tools are used in SAP BTP, Neo environment versus SAP BTP, Cloud Foundry environment, but the basic procedure is identical. Therefore, in this section, we’ll show you the configuration steps using SAP BTP, Neo environment in our example.

As prerequisites, you must have a basic understanding of the Secure Sockets Layer (SSL) encryption protocol and its successor Transport Layer Security (TLS) before you can start configuring a custom domain (see also [Chapter 2](#02_001.html#h2), [Section 2.1.1](#02_001.html#h2.1.1)). You or your company must own the domain to be used, and the Domain Name System (DNS) server for that domain must be in your access range. The custom domain for SAP BTP, Neo environment can only be set up using the SAP BTP, Neo environment command line, the configuration of which we described in [Chapter 3](#03_001.html#h3), [Section 3.1](#03_001.html#h3.1).

The process starts with the creation of a certificate signing request (CSR). The CSR is created on the command line for SAP BTP, Neo environment, using the command shown in [Listing 6.6](#06_005.html#l6.6).

```
neo generate-csr 
       --account <SubAccountTechnicalName> 
       --user <SubAccountUser>
       --host <SubAccountHost>
       --name <nameofcertificate> 
       --certificate-distinguished-name <certificateDN> 
```

**Listing 6.6**     Creating a CSR

The name of the domain for which the certificate is to be created must be included as a common name (CN) in the distinguished name (DN) of the certificate.

In the next step, the previously created CSR must be submitted to a certification authority, also called a certificate authority (CA). The CA will sign the certificate. When signing the certificate, specify “F5BigIP” as the server type.

The next step is to import the SSL certificate issued by the CA into the SAP BTP subaccount. The import is performed in the Neo console using the command from [Listing 6.7](#06_005.html#l6.7). The certificate must be in Privacy-Enhanced Mail (PEM) format.

```
neo upload-domain-certificate 
       --account <SubAccountTechnicalName> 
       --user <SubAccountUser>
       --host <SubAccountHost>
       --name <nameofcertificate> 
       --location <pathToCertificate> 
```

**Listing 6.7**     Importing an SSL Certificate

After the certificate has been successfully imported, it must be bound to the host used in CSR. This action is performed in the Neo console using the command shown in [Listing 6.8](#06_005.html#l6.8).

```
neo bind-domain-certificate 
       --account <SubAccountTechnicalName> 
       --user <SubAccountUser>
       --host <SubAccountHost>
       --ssl-host <SSLHostName> 
       --certificate <nameofcertificate> 
```

**Listing 6.8**     Binding a Certificate to an SSL Host

To make an application on SAP BTP accessible through the custom domain, you must associate the custom domain with the application URL. For this task, enter the command shown in [Listing 6.9](#06_005.html#l6.9) in the Neo console.

```
neo add-custom-domain 
       --account <SubAccountTechnicalName> 
       --user <SubAccountUser>
       --host <SubAccountHost>
       --custom-domain <CustomDomainHostName>
       --application-url <urlofApplication>
       --ssl-host mysslhostname 
```

**Listing 6.9**     Associating a Custom Domain with a Cloud Application

The final step is to maintain the DNS records. To route traffic for your custom domain to the desired application on SAP BTP, you must also configure the domain in the DNS you’re using. For this task, you must map the canonical name (CNAME) of your custom domain to the SSL host you have created in the DNS server management tool so that the subdomain can also resolve correctly to the IP address of your server. You must perform this step for each custom domain you want to use.

### 6.5.2    Using the Command Line to Manage SAP BTP

In [Section 6.2](#06_002.html#h6.2), we provided an initial introduction to the SAP BTP CLI, and you learned a few helpful commands. We also pointed out that a logon is mandatory.

After logging on, all commands are executed in the global account by default. To work in a specific subaccount or directory, use the sapcp target command to change the default context, which can be a different global account \-ga <ID>, a different subaccount \-sa <ID>, or a different directory \-dir <ID>. Once you’ve changed contexts, you no longer need to supply the Subaccount or Directory parameters with the calls when executing the commands.

Reading out global account information is quite easy with SAP BTP. We described this command in [Section 6.2](#06_002.html#h6.2).

With the following command, you can query a list of all the subaccounts of your global account:

```
sapcp list accounts/subaccount 
```

In this way, you can determine the ID of a specific subaccount.

If you have a large number of subaccounts, keeping track of them can be difficult. Therefore, SAP has introduced the functionality of directories in feature set B. With a directory, you can structure your subaccounts or set them up hierarchically.

You can create a directory with the command shown in [Listing 6.10](#06_005.html#l6.10). We’ll create a directory with the name “SAP PRESS” as an example.

```
sapcp create accounts/directory 
       --global-account <GlobalAccountSubDomain> 
       --display-name "SAP PRESS" 
```

**Listing 6.10**     Creating a Directory

The directory is then available in the SAP BTP cockpit in the Directories area. It does not yet contain any subaccounts or regions, as shown in [Figure 6.41](#06_005.html#f6.41).

###### \[»\]  Creating a Directory via the Web Interface

Under the Directories menu item on the right, you can create directories (via Create Directory, as shown in [Figure 6.41](#06_005.html#f6.41)) and manage them accordingly. You can set which properties should apply in the stored subaccounts and then place subaccounts in the directories. This capability is intended to enable you to further structure your subaccounts, especially when the system landscape becomes more complex.

[![SAP BTP Cockpit: Directory Overview](bilderklein/klein06_041.png)](img-f6.41.html) 

**Figure 6.41**     SAP BTP Cockpit: Directory Overview

Now that you have an empty directory, you can move a subaccount into the directory. For this task, use the move command, the syntax of which is shown in [Listing 6.11](#06_005.html#l6.11). Both the ID of the subaccount and the ID of the directory must be supplied.

```
sapcp [OPTIONS] move accounts/subaccount ID 
       --global-account SUBDOMAIN 
       --to-directory ID 
```

**Listing 6.11**     Moving a Subaccount to a Directory

###### \[+\]  Calling Help for a Command

You do not need to know the syntax of all commands and all their associated parameters by heart. Use the following command, for example, to call the SAP BTP CLI help for the move command:

```
sapcp --help move accounts/subaccount
```

If you do not have the IDs of the subaccount and the directory, use the following command to first read the global account and pass the show hierarchy parameter:

```
sapcp get accounts/global-account 
       --show-hierarchy 
```

This command will provide you with all the IDs of the subaccounts and directories in addition to the global account information.

After you’ve moved the subaccount to the directory via the command line, the tile of your directory will be displayed in the SAP BTP cockpit, as shown in [Figure 6.42](#06_005.html#f6.42). A subaccount and region are now specified as content. Note that there is a 1:1 mapping between subaccount and region.

[![Directory with Assigned Subaccount](bilderklein/klein06_042.png)](img-f6.42.html) 

**Figure 6.42**     Directory with Assigned Subaccount

You can also view a hierarchical representation of your global account, as shown in [Figure 6.43](#06_005.html#f6.43), using the buttons next to the search dialog box.

[![Hierarchical Representation of a Global Account](bilderklein/klein06_043.png)](img-f6.43.html) 

**Figure 6.43**     Hierarchical Representation of a Global Account

Let’s now introduce you to two more useful commands for managing subaccounts. With the following command, you can query a list of all composite roles within a subaccount:

```
sapcp list security/role-collection 
       --subaccount <SubAccountID> 
```

Use the following command to retrieve all the available service plans within a subaccount:

```
sapcp list services/plan 
       --subaccount <SubAccountID> 
```

At this point, you’ve learned the most important commands for the administration of SAP BTP accounts. As mentioned, many more commands exist, but presenting them in detail would go beyond the scope of this book.

## 6.6    Summary

In this chapter, you learned about the administration tools provided by SAP BTP. To start, we covered using the SAP BTP CLI for the administration of SAP BTP, Neo environment and for managing global accounts. We then walked you through administration tasks using APIs, including audit log retrieval, user management, and permission management. We then provided a handy checklist for working with the CLI and APIs. Finally, we explored two real-world examples of using the CLI, including configuring a custom domain and managing SAP BTP.

# 7    Securing Key Cloud Services

SAP Business Technology Platform (SAP BTP) provides a wide range of services and subscriptions. In many cases, the individual services have rather different requirements regarding their security. In this chapter, we’ll look at the specific requirements for some frequently used services.

This chapter covers cloud security topics. We’ll break down our coverage into the following areas:

*   Development  
    In this chapter, you’ll learn how to securely deploy and operate some commonly used scenarios. The development of user interfaces (UIs), backend functionalities, workflows, and mobile applications is the most prominent use case for SAP BTP. SAP initially introduced SAP Web IDE as a development environment in SAP BTP, Neo environment for this purpose. After the introduction of SAP BTP, Cloud Foundry environment, this development environment was renamed SAP Web IDE, full stack, as no equivalent environment was available in SAP BTP, Cloud Foundry environment.  
    However, soon SAP would also provide a development environment in SAP BTP, Cloud Foundry environment. In this environment, the decision was made not to continue SAP Web IDE and instead to develop SAP Business Application Studio, which is thus the logical successor to SAP Web IDE. SAP Business Application Studio offers an advantage in that all plug-ins provided for SAP Business Application Studio can also be used locally in the popular Visual Studio Code (VS Code) development environment. We’ll show you in [Section 7.1](#07_001.html#h7.1) what you need to consider when securing SAP Web IDE and SAP Business Application Studio.
    
*   Integration  
    In addition to the development of applications, the topic of integration plays an important role in the context of SAP applications. SAP has provided the Cloud Integration tool as a counterpart to the on-premise middleware SAP Process Orchestration in the cloud. Originally, this service was introduced under the name SAP HANA Cloud Integration and continued for a long time under the name SAP Cloud Platform Integration. With the transition from SAP Cloud Platform to SAP BTP, the tool received the current name, Cloud Integration.
    
    Cloud Integration is an Apache Camel\-based solution that has been absorbed as a service into SAP Integration Suite. Apache Camel is a free coding project of the Apache Foundation. The framework can be used for routing and conversion capabilities in Java applications. SAP has extended this project. In [Section 7.2](#07_002.html#h7.2), you’ll learn about security aspects of using Cloud Integration within SAP Integration Suite. Since a large proportion of existing customers still use Cloud Integration in SAP BTP, Neo environment, we’ll also address the special features of this environment.
    
    The provision of programming interfaces, generally called application programming interfaces (APIs), is often included in the context of integrations. This feature enables applications to be integrated into existing solutions and to access them via standardized protocols and technologies. APIs should not be provided arbitrarily, but via a central service instead. For this purpose, SAP offers the SAP API Management service, which is also part of SAP Integration Suite and can now no longer be licensed as a standalone solution. We’ll discuss the security aspects of this service in [Section 7.3](#07_003.html#h7.3).
    
*   User experience (UX)   
    SAP Fiori applications can be deployed via the SAP Fiori launchpad not only in your on-premise landscape, but also on SAP BTP. For this purpose, SAP provides the SAP Launchpad service in SAP BTP, Cloud Foundry environment. For SAP BTP, Neo environment, these functions are integrated into the SAP Cloud Portal service. In [Section 7.4](#07_004.html#h7.4), you’ll learn what to look out for from a security perspective when using these services.
    
*   ABAP  goes cloud  
    Finally, we wanted to look at SAP BTP, ABAP environment. With this ABAP development and runtime environment based in the cloud, SAP has hit its mark with its existing customers. Until introducing SAP BTP, ABAP environment, SAP’s customers and partners had to rely on Java, Node.js, and Python to develop and extend cloud applications. This limitation resulted in the need to rebuild relevant skills and knowledge in many companies. With ABAP development for cloud applications, SAP customers and partners can now build on their existing ABAP skills and at the same time make themselves fit for SAP S/4HANA and the world of the cloud. We therefore address the security aspects of SAP BTP, ABAP environment in [Section 7.5](#07_005.html#h7.5).
    

Finally, in [Section 7.6](#07_006.html#h7.6), you’ll learn how to set up a corporate user store as a source for SAP BTP users. Finally, in [Section 7.7](#07_007.html#h7.7), we provide a checklist for you to use when securing cloud services.

## 7.1    SAP Web IDE and SAP Business Application Studio

SAP Web IDE, full stack, is the development environment and tool in SAP BTP, Neo environment. SAP Business Application Studio is the logical successor of SAP Web IDE and is provided only in SAP BTP, Cloud Foundry environment. Migration of applications developed on SAP Web IDE to SAP Business Application Studio is most easily accomplished using Git repositories. In the following sections, we address security aspects of both development environments.

### 7.1.1    SAP Web IDE

SAP Web IDE is used in many ways in SAP BTP. It is used for the development of SAPUI5 and SAP Fiori applications as well as for the development of workflows or Internet of Things (IoT) applications. SAP Web IDE can be extended by various plug-ins.

For development with SAP Web IDE, you need authorizations for the following software components to cover the full lifecycle in application development and deployment:

*   Git server for version control
    
*   Optionally, a continuous integration (CI)/continuous delivery (CD) service for the central build and deployment of the applications. For example, the SAP Continuous Integration and Delivery service or Microsoft Azure DevOps Services can be used for these functionalities in the cloud, and Apache Jenkins can be used on-premise.
    
*   A system on which the applications are to be provided. For example, SAP BTP can be used here, but you can also use an on-premise system such as SAP S/4HANA or SAP Business Suite.
    

The authorizations for the Git server or the repositories behind it are usually not managed in SAP BTP. However, one exception exists: If you use the SAP Git service of SAP BTP, Neo environment, its permissions are also managed at the level of the corresponding subaccount.

###### \[»\]  Git on SAP BTP

SAP offers the SAP Git service in SAP BTP, Neo environment at the subaccount level, but not in SAP BTP, Cloud Foundry environment. Therefore, at the time of this writing, when using the functionalities of SAP BTP, Cloud Foundry environment, you must resort to an external Git provider such as GitHub, GitLab, or BitBucket or host a Git server in your system landscape yourself.

Regardless of whether you use Git, SAP Web IDE offers the possibility to work based on workspaces. These areas allow development teams to encapsulate related developments. Developers who have experience with the Eclipse development environment are familiar with this concept, as it has been proven in Eclipse over the decades.

To see SAP Web IDE roles, you’ll need to jump to the configuration from the SAP Web IDE service overview screen. For this task, click on the Configure Service link, as shown in [Figure 7.1](#07_001.html#f7.1).

[![SAP Web IDE: Service Overview](bilderklein/klein07_001.png)](img-f7.1.html) 

**Figure 7.1**     SAP Web IDE: Service Overview

As shown in [Figure 7.2](#07_001.html#f7.2), SAP Web IDE comes with three standard roles: DiDeveloper, DiAdministrator, and DiScpGitAdmistrator. These roles can be found in SAP BTP, Neo environment in the SAP BTP cockpit, under the Roles area.

[![SAP Web IDE: Roles](bilderklein/klein07_002.png)](img-f7.2.html) 

**Figure 7.2**     SAP Web IDE: Roles

The permissions provided with these roles are described in [Table 7.1](#07_001.html#t7.1).

 
| Roles || Description |
| --- | --- |
| DiDeveloper || Implementation of developments with SAP Web IDE, full stack |
| --- | --- |
| DiAdministrator || Management of user data, export of user workspaces, and deletion of user data |
| DiScpGitAdministrator || Management of Git repositories and push commits from other developers |

**Table 7.1**     SAP Web IDE: Standard Roles for Development

Basically, you have two options for assigning roles: Either a user or a user group is assigned directly to a role. [Figure 7.3](#07_001.html#f7.3) shows the two variants using the DIDeveloper role as an example. We recommend that you work with groups. Among other things, you can also use groups in mappings for identity providers.

[![Assigning Roles to Individual Users or Groups](bilderklein/klein07_003.png)](img-f7.3.html) 

**Figure 7.3**     Assigning Roles to Individual Users or Groups

If you decide to use user groups, in the SAP BTP cockpit, navigate to the Authorization Management screen, where you can assign both roles and users to these groups. [Figure 7.4](#07_001.html#f7.4) shows the assignment options available using the CloudDNA Developers group as an example.

[![Creating and Managing User Groups](bilderklein/klein07_004.png)](img-f7.4.html) 

**Figure 7.4**     Creating and Managing User Groups

Additionally, you have the option of performing role assignments to groups through mappings based on the Security Assertion Markup Language (SAML) assertion of an identity provider, as shown in [Figure 7.5](#07_001.html#f7.5). In this case, the identity provider must submit the required attributes in the SAML response. For more information about provisioning users and groups in SAP BTP, Neo environment via identity providers, see [Chapter 3](#03_001.html#h3), [Section 3.3](#03_003.html#h3.3).

[![Identity Provider Group Mapping](bilderklein/klein07_005.png)](img-f7.5.html) 

**Figure 7.5**     Identity Provider Group Mapping

SAP Web IDE also uses the SAP Connectivity service from SAP BTP in the background, for example, to access the data of an on-premise system via OData services. However, the connections used must be set up in the subaccount to be usable.

### 7.1.2    SAP Business Application Studio

SAP Business Application Studio is offered by SAP as a cloud service at the hyperscalers Amazon, Microsoft, Google, and Alibaba in SAP BTP, Cloud Foundry environment. As with SAP Web IDE, SAP Business Application Studio is a web-based development tool.

Developers can create what are called dev spaces in SAP Business Application Studio, and these spaces can be personalized and are provided completely isolated from the dev spaces of other users. SAP Business Application Studio is provided in the form of a multitenant application (i.e., the service must be subscribed to via a subscription). Only subscriptions to the Identity Authentication service and the SAP Destination service run in the subaccount; the others, such as SAP Business Application Studio, run as multitenant applications. The SAP Destination service enables the cloud-based applications you develop and use to access other cloud-based and on-premise systems.

The basic architecture of cloud application delivery via SAP Business Application Studio is shown in [Figure 7.6](#07_001.html#f7.6).

[![SAP Business Application Studio: Architecture](bilderklein/klein07_006.png)](img-f7.6.html) 

**Figure 7.6**     SAP Business Application Studio: Architecture

You can find SAP Business Application Studio by navigating to Services • Instances and Subscriptions in SAP BTP, Cloud Foundry environment, as shown in [Figure 7.7](#07_001.html#f7.7). Click the SAP Business Application Studio link to access the details. If you have not yet subscribed to the service, you can do so by clicking the Create button.

[![SAP Business Application Studios: Subscribing](bilderklein/klein07_007.png)](img-f7.7.html) 

**Figure 7.7**     SAP Business Application Studios: Subscribing

Under Security • Role Collections of the subaccount, you’ll see three predelivered role templates, as shown in [Figure 7.8](#07_001.html#f7.8):

*   Business\_Application\_Studio\_Developer
    
*   Business\_Application\_Studio\_Administrator
    
*   Business\_Application\_Studio\_Extension\_Deployer
    

[![SAP Business Application Studio: Role Templates](bilderklein/klein07_008.png)](img-f7.8.html) 

**Figure 7.8**     SAP Business Application Studio: Role Templates

The role collection Business\_Application\_Studio\_Developer is the counterpart to the DiDeveloper role in SAP Web IDE and authorizes development in SAP Business Application Studio. The role Business\_Application\_Studio\_Administrator, the counterpart to the role DiAdministrator in SAP Web IDE, allows you to manage and export dev spaces. Only the role template Business\_Application\_Studio\_Extension\_Deployer, used to develop and install extensions, lacks a counterpart in SAP Web IDE.

The role collections for SAP Business Application Studio do not have to be created manually. They are created automatically when the service is activated. To assign a role collection to a user, go to the user details screen and click the Assign Role Collection button, as shown in [Figure 7.9](#07_001.html#f7.9).

Assigning role collections to users or user groups must be done individually, as shown in [Figure 7.10](#07_001.html#f7.10). Select a role collection from the list and confirm by clicking Assign Role Collection. The roles are not mutually exclusive and do not overlap in terms of the permissions they contain. Therefore, you can assign all available roles to a user. We also recommend at this point to assign the role collections by a mapping based on the SAML assertion via an identity provider.

[![Assigning Role Collections](bilderklein/klein07_009.png)](img-f7.9.html) 

**Figure 7.9**     Assigning Role Collections

[![Assign Role Collections Dialog Box](bilderklein/klein07_010.png)](img-f7.10.html) 

**Figure 7.10**     Assign Role Collections Dialog Box

## 7.2    Cloud Integration

Cloud Integration is one of the most widely used services of SAP BTP. This solution is offered in both SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. In SAP BTP, Cloud Foundry environment, Cloud Integration is part of SAP Integration Suite and is bundled with other products.

###### \[+\]  SAP Integration Suite

SAP Integration Suite combines the integration functions from SAP Process Integration (the Cloud Integration service), SAP API Management, Integration Advisor, Open Connectors, and Trading Partner Management (TPM) in a coherent and simplified toolkit. SAP Integration Suite provides comprehensive enterprise application integration capabilities. Starting in 2021, these services are no longer offered separately and are only available as part of a service plan for SAP Integration Suite.

In terms of architecture, some fundamental differences exist between the Cloud Integration service in SAP BTP, Neo environment and the service in SAP BTP, Cloud Foundry environment. Therefore, in this section, we’ll first compare the architectures and special features of the two environments before going into the management of roles and permissions.

### 7.2.1    Cloud Integration in SAP BTP, Neo Environment

Cloud Integration is provided within SAP BTP, Neo environment, in the form of a subscription. As a multitenant application, Cloud Integration is operated by SAP in what’s called a provider account and consumed by customers in their own subaccounts. Data storage, authentication, and connectivity are completely isolated from other accounts at the consumer level.

[![SAP BTP, Neo Environment: Cloud Integration Architecture](bilderklein/klein07_011.png)](img-f7.11.html) 

**Figure 7.11**     SAP BTP, Neo Environment: Cloud Integration Architecture

The service consists of a tenant management node (TMN) and one or more worker nodes, often called integration flow mappers (IFLMAPs). Dialog users work exclusively with the TMN, while interface calls run against the IFLMAP node(s). SAP prepends the F5 Big IP load balancer for this purpose, which distributes the requests among the different nodes in classic load balancing. [Figure 7.11](#07_002.html#f7.11) shows this architecture graphically.

TMN and IFLMAP are Java applications. You can see the two subscriptions for these applications in the SAP BTP cockpit of SAP BTP, Neo environment under Applications • Subscriptions, as shown in [Figure 7.12](#07_002.html#f7.12). By clicking on the names of the applications (the iflmap or tmn links in the Application column), you can jump to their details to assign roles.

[![SAP BTP, Neo Environment: Java Applications in the Subscription Overview](bilderklein/klein07_012.png)](img-f7.12.html) 

**Figure 7.12**     SAP BTP, Neo Environment: Java Applications in the Subscription Overview

#### Roles for the Tenant Management Node

A comprehensive number of roles are available for the TMN, as shown in [Figure 7.13](#07_002.html#f7.13). The roles whose names begin with the string AuthGroup are collective roles that are mapped to specific personas and their tasks. We’ll go into more detail about these roles in [Section 7.2.3](#07_002.html#h7.2.3).

[![Role Overview for the TMN](bilderklein/klein07_013.png)](img-f7.13.html) 

**Figure 7.13**     Role Overview for the TMN

If these roles do not meet your requirements, you can also assign individual roles to users. However, this assignment may require a lot of effort if you have a large number of users. We therefore recommend that you work with groups. In this case, assign one or more user groups to the roles and then assign the users to the groups. Using groups offers another advantage: If you use an application identity provider, you can derive user groups from SAML assertions.

#### Roles for the Worker Node

For the IFLMAP application, in contrast to TMN, only one predefined role exists, as shown in [Figure 7.14](#07_002.html#f7.14). This role is used in the standard in all HTTP sender communication channels. We therefore recommend that you create a dedicated role for each communication partner (i.e., for each system or alternatively for each interface). Otherwise, unauthorized persons, if they know or can guess the API endpoint, could call each interface with a correspondingly authorized user.

[![Role Overview for a Worker Node](bilderklein/klein07_014.png)](img-f7.14.html) 

**Figure 7.14**     Role Overview for a Worker Node

#### Cloud Integration Logs

You can access the service call logs by navigating to Monitor via the Cloud Integration web interface. For this task, navigate to the Access Logs area on the start page of the monitor, as shown in [Figure 7.15](#07_002.html#f7.15).

In the Audit Log, you’ll see which user performed which critical actions and when, as shown in [Figure 7.16](#07_002.html#f7.16). In the Action column, you’ll see the action performed, in our example, the deletion of an object in the message store. In the Object Type and Object Name columns, you’ll see the type and name of the affected object. You can use the Time Range filter to limit the displayed actions to a specific period to examine.

###### \[»\]  Audit Log at Application and Subaccount Level

You must always distinguish between the general audit logs at the level of your subaccount and the logs in the Cloud Integration monitor. The audit logs of the subaccount can only be accessed via APIs, as described in [Chapter 6](#06_001.html#h6), [Section 6.3.2](#06_003.html#h6.3.2). Authentication in this case is performed via OAuth. For this purpose, you must create a platform API client in the corresponding SAP BTP subaccount and equip it with the required OAuth scopes.

Although the audit log of Cloud Integration is not identical to the audit log of the subaccount, it can also be accessed via an OData API.

[![Cloud Integration Monitor: Calling Up Access Logs](bilderklein/klein07_015.png)](img-f7.15.html) 

**Figure 7.15**     Cloud Integration Monitor: Calling Up Access Logs

[![Cloud Integration Monitor: Audit Logs](bilderklein/klein07_016.png)](img-f7.16.html) 

**Figure 7.16**     Cloud Integration Monitor: Audit Logs

Via the System Log Files application, you can access the HTTP Access Log and the CP Default Trace log. The type of log from which an entry originates is displayed in each case in the Log Type column, as shown in [Figure 7.17](#07_002.html#f7.17). In an HTTP access log, you can view, among other things, failed logon attempts and requests that lack permissions. We recommend that you periodically check the HTTP access log for irregularities.

[![Cloud Integration Monitor: System Logs](bilderklein/klein07_017.png)](img-f7.17.html) 

**Figure 7.17**     Cloud Integration Monitor: System Logs

### 7.2.2    Cloud Integration in SAP BTP, Cloud Foundry Environment

In SAP BTP, Cloud Foundry environment, Cloud Integration is provided as a multitenant application composed of several microservices. In addition, worker nodes are among the components deployed in the subaccount of the respective customer. These microservices run in applications shared by the different tenants of different customers. The worker nodes, which are responsible for message processing and thus may also process confidential data, run in a customer’s own subaccounts. [Figure 7.18](#07_002.html#f7.18) shows this architecture.

[![SAP BTP, Cloud Foundry Environment: Cloud Integration Architecture](bilderklein/klein07_018.png)](img-f7.18.html) 

**Figure 7.18**     SAP BTP, Cloud Foundry Environment: Cloud Integration Architecture

The two storage areas, the runtime store and the operations store, separate the bulk data that is processed by the worker nodes from the operational data that can be accessed by users.

The role collections available in SAP BTP, Cloud Foundry environment are shown in [Figure 7.19](#07_002.html#f7.19). We explain these role collections in more detail in [Section 7.2.3](#07_002.html#h7.2.3).

[![SAP BTP, Cloud Foundry Environment: Role Collections for Cloud Integration](bilderklein/klein07_019.png)](img-f7.19.html) 

**Figure 7.19**     SAP BTP, Cloud Foundry Environment: Role Collections for Cloud Integration

As mentioned earlier, since 2021, the Cloud Integration service can no longer be licensed as a separate service, only as part of SAP Integration Suite. If you’ve selected this option, you must instantiate the Cloud Integration service within SAP Integration Suite itself. To complete this task, your user must be assigned the IntegrationProvisioningAdmin role, as shown in [Figure 7.20](#07_002.html#f7.20). The assignment is not created directly, but via the associated composite role.

[![SAP Integration Suite: Administration Role Template](bilderklein/klein07_020.png)](img-f7.20.html) 

**Figure 7.20**     SAP Integration Suite: Administration Role Template

After you’ve activated the Cloud Integration service (and other services) in SAP Integration Suite, the associated roles, role templates, and role collections appear in your subaccount.

#### User Authentication

The authentication of dialog users, such as administrators and developers, is performed via the identity provider configured in the subaccount of SAP BTP, Cloud Foundry environment. The following options are available:

*   SAP ID service
    
*   Identity Authentication service
    
*   Third-party SAML identity provider
    

The authentication of interface users is different from that of dialog users.

The following options are available for inbound Hypertext Transfer Protocol Secure (HTTPS)-based communication:

*   Basic authentication with a user created in the identity provider. This authentication method corresponds to the authentication of dialog users.
    
*   Basic authentication with a user whose credentials were provided by creating a service key.
    
*   Authentication by using a client certificate.
    
*   Authentication by using OAuth with the client credentials flow, that is, via the system of issuing bearer tokens through an authentication service, as discussed in [Chapter 6](#06_001.html#h6), [Section 6.3.2](#06_003.html#h6.3.2).
    

###### \[+\]  Use of Client Certificates

SAP recommends against using client certificates without certificate-to-user mapping for authentication. Note that, when using client certificates, if the client certificate is renewed or replaced, then the integration flow (iFlow ) modeled in Cloud Integration, which is used to transfer data between different systems, must be redeployed. Only the distinguished name (DN) of the certificate is checked, not the entire certificate.

#### Deployment/Provisioning of the SAP Process Integration Runtime

With a service instance, you can define how to access a certain service in your SAP BTP subaccount. In the context of Cloud Integration, a service instance is the definition of an OAuth client. To use service key\-based authentication, you must instantiate the SAP Process Integration runtime (i.e., you must create a service instance). This service instance, like any other service instance, is deployed in a space in SAP BTP, Cloud Foundry environment. To create a new instance, navigate to the service marketplace of SAP BTP, Cloud Foundry environment, and open the SAP Process Integration runtime service. Then, click the Create button in the service details, as shown in [Figure 7.21](#07_002.html#f7.21).

[![Instantiating the SAP Process Integration Runtime](bilderklein/klein07_021.png)](img-f7.21.html) 

**Figure 7.21**     Instantiating the SAP Process Integration Runtime

In the creation wizard, select the integration-flow service plan and assign a descriptive name for your service instance, as shown in [Figure 7.22](#07_002.html#f7.22). Continue by clicking Next.

[![New Service Provisioning](bilderklein/klein07_022.png)](img-f7.22.html) 

**Figure 7.22**     New Service Provisioning

In the second step of the configuration creation wizard, use a JavaScript Object Notation (JSON) object by specifying the ESBMessaging.send role, as shown in [Figure 7.23](#07_002.html#f7.23). You can optionally pass grant types via the Grant-types field at this point to restrict access to a specific authentication method. We won’t do this in our example. Continue by clicking Next and finish the creation wizard for the instance in the last step by clicking Create Instance.

[![Service Parameters](bilderklein/klein07_023.png)](img-f7.23.html) 

**Figure 7.23**     Service Parameters

#### Creating a Service Key

If you decide to authenticate based on service keys, you must create a service key for the SAP Process Integration runtime instance. (We described how to create a service key several times in previous chapters, for example, in [Chapter 6](#06_001.html#h6), [Section 6.3.2](#06_003.html#h6.3.2).) In the creation dialog box, assign a descriptive name for the service key and click Create, as shown in [Figure 7.24](#07_002.html#f7.24). No further configuration is required.

[![New Service Key Dialog Box](bilderklein/klein07_024.png)](img-f7.24.html) 

**Figure 7.24**     New Service Key Dialog Box

After the service key has been created, it is displayed in the dialog box. You can save the service key locally and send it to communication partners. An example of a service key for the SAP Process Integration runtime is shown in [Figure 7.25](#07_002.html#f7.25). The clientid attribute corresponds to the user name; the clientsecret attribute, to the password.

[![Service Key Details](bilderklein/klein07_025.png)](img-f7.25.html) 

**Figure 7.25**     Service Key Details

### 7.2.3    Roles and Authorizations

Cloud Integration distinguishes between dialog users and interface users in several ways. Dialog users are typically developers, administrators, and support team members. They generally work with the TMN. Dialog users are authenticated as usual against the application identity provider. In the standard system, this identity provider is the SAP ID service.

At this point, a distinction must be made between users of the Cloud Integration application and platform users. Authorizations are assigned outside of Cloud Integration in the respective SAP BTP subaccount. We therefore recommend that you create a dedicated user to be responsible for assigning authorizations.

To bundle authorizations for Cloud Integration in a meaningful way, SAP works with personas. These personas cover the various tasks typically associated with an integration project. Personas can be compared to job titles. In SAP BTP, Neo environment, personas are represented by application-specific roles; in SAP BTP, Cloud Foundry environment, personas are represented by role collections.

The available personas include the following:

*   Business expert   
    The corresponding composite role allows business experts to perform technical tasks, such as checking message content.
    
    *   Authorization group: AuthGroup.BusinessExpert
        
    *   Composite role: PI\_Business\_Expert
        
*   Administrator  
    The tenant’s administration user must connect to the tenant and perform administrative tasks.
    
    *   Authorization group: AuthGroup.Administrator
        
    *   Role collection: PI\_Administrator
        
*   Integration developer   
    An integration developer must be able to connect to a tenant (using the web-based tools and views), download, and deploy artifacts.
    
    *   Authorization group: AuthGroup.IntegrationDeveloper
        
    *   Role collection: PI\_Integration\_Developer
        
*   Read-only persona  
    This persona group must connect to a tenant to monitor processed messages and access the data store viewer.
    
    *   Authorization group: AuthGroup.ReadOnly
        
    *   Role collection: PI\_Read\_Only
        
*   System developer   
    A system developer performs tasks required for system support.
    
    *   Authorization group: AuthGroup.SystemDeveloper
        
    *   Omnibus role: Not available
        
*   Partner directory configurator   
    The partner directory administrator requires permissions to read and write content in the partner directory.
    
    *   Permission group: AuthGroup.TenantPartnerDirectoryConfigurator
        
    *   Collective role: Not available
        

If the authorization groups in SAP BTP, Neo environment or the role collections in SAP BTP, Cloud Foundry environment do not meet your requirements, you have the option of using the underlying roles found in SAP BTP, Neo environment or the existing role templates in SAP BTP, Cloud Foundry environment as a foundation for your own roles.

Interface users are assigned for the systems that exchange messages via Cloud Integration. When a sender system sends HTTPS-based requests to Cloud Integration, that system can authenticate itself in several ways:

*   Client certificate authentication
    
*   Basic authentication
    
*   OAuth
    
*   SAML
    

The authentication method depends on the selected authentication mode. If basic authentication is configured, the calling user is authenticated against the identity provider. On the other hand, if the client authenticates with a client certificate, authentication is performed by the load balancer. The load balancer terminates the Transport Layer Security (TLS) connection and checks the client certificate of the calling component.

### 7.2.4    Security Recommendations

In the development and operation of integration artifacts, several things must be considered with regard to security. As a first step, iFlows are developed in integration projects. These iFlows are assigned to packages.

Basically, integration developers have access to all artifacts within a Cloud Integration instance. Securing this access is a major challenge, especially in large companies and groups with many developers from different divisions and projects. In most cases, both internal and external developers are also involved. SAP quickly recognized this problem and solved it over time with access policies, which allow you to restrict access to integration artifacts and their associated data.

Access policies are consumed both in the design and runtime of integration artifacts. The scope of access policies includes the protection of:

*   Integration packages  
    You can restrict importing a package. You can restrict copying a package from prepackaged content provided via the Discover view to your design workspace.
    
*   iFlows, API-based integration artifacts, message mappings, value mappings, and script collection artifacts in the design perspective  
    You can restrict the creation and upload of artifacts. Furthermore, you may restrict the actions edit, copy, download, delete, and simulate on existing artifacts.
    
*   iFlows, API-based integration artifacts, message mappings, value mappings, and script collection artifacts at a package level  
    You can restrict the creation and upload of artifacts. Furthermore, you may restrict the actions for exporting, publishing, or deleting a package if access to at least one artifact is restricted.
    
*   All integration artifacts  
    You can restrict the execution of the deploy and undeploy, restart, download, and change log level operations and the configuration of archiving.
    
*   All processing of integration artifacts  
    During the execution of all integration artifacts, business data might be collected or created. Therefore, you can restrict access to the message processing log attachments, trace data, data in Java Message Service (JMS) queues, data stores, and variables.
    

During the modeling of iFlows, the integration developer defines how messages are mapped, the recipients for the messages, and which credentials are being used. This set of roles provides powerful permissions and, in some cases, allows the integration developer to access sensitive data.

Therefore, apply the following measures especially when designing iFlows in areas that are security-sensitive:

*   Don’t give the integration developer access to productive systems.
    
*   Use dedicated tenants (subaccounts) for development and/or testing. Integration developers work on the development tenant. The iFlows can then be transported to the test and productive tenant by another person.
    
*   Apply a four-eyes principle before deploying iFlows to production.
    
*   Implement a review process before deploying iFlows to production.
    
*   Don’t share the same secret credentials between tenants with different security levels (i.e., between development, test, and production).
    
*   Consider using client certificate-based authentication whenever possible, rather than basic authentication. When using client certificates, the private key remains in the sender system, and no password is transmitted through the network.
    
*   If read-only access is required to analyze issues in the productive system, use the authorization group AuthGroup.ReadOnly.
    
*   If you suspect a security violation, check the audit log to find out which user deployed the iFlow in question.
    

## 7.3    SAP Integration Suite in SAP BTP, Cloud Foundry Environment

As mentioned in the previous section, integration plays a central role in SAP’s cloud strategy. With Cloud Integration, SAP offers a middleware in SAP BTP. This is offered in SAP BTP, Cloud Foundry environment in the SAP Integration Suite bundle. In addition to Cloud Integration, there is another SAP Integration Suite capability, SAP API Management, which is very popular with customers. In this section, we’ll look at this capability from a security perspective.

### 7.3.1    SAP API Management

APIs enable your company to provide services and information externally. APIs simplify the programming of graphical user interfaces (GUIs) for different types of apps on mobile devices or in the cloud.

SAP API Management helps you securely expose your APIs to employees, partners, and development teams. The tool provides a unified UI for managing and monitoring APIs across different data platforms, along with real-time analytics capabilities. Essentially, SAP API Management can serve as a central hub in your organization for accessing any type of data via APIs. By deploying the service, you can use this central location to develop, deploy, monitor, and monetize all API access. You can also see if your APIs are experiencing problems of any kind at any time.

SAP API Management consists of the following components:

*   API designer
    
*   API portal
    
*   API runtime
    
*   Developer portal
    
*   API analytics
    

Behind these components lie numerous categories of stakeholders, that is, the different user groups that use the service in different ways.

The service can connect to data sources both in the cloud and in your company’s on-premise landscape. Only the Representational State Transfer (REST), Simple Object Access Protocol (SOAP), and OData protocols are used. If your data sources do not support these protocols, you can use Cloud Integration as a proxy (see [Section 7.2](#07_002.html#h7.2)). To access the on-premise landscape, the cloud connector is also used in this service.

Essentially, two security-related issues must be considered conceptually: access by users of any kind to SAP API Management and access by SAP API Management to the provided APIs of the various data sources. [Figure 7.26](#07_003.html#f7.26) graphically shows these two areas of concern. On the left, you’ll see various roles for users to access SAP API Management. We explain these roles in [Section 7.3.2](#07_003.html#h7.3.2). On the right, the systems whose data is being accessed via APIs are indicated. We show you how to secure this access in [Section 7.3.3](#07_003.html#h7.3.3).

[![SAP API Management: Architecture](bilderklein/klein07_026.png)](img-f7.26.html) 

**Figure 7.26**     SAP API Management: Architecture

### 7.3.2    Roles and Authorizations

When assigning roles and authorizations, you must consider various categories of stakeholders. Roles and authorization objects for SAP API Management are delivered in the form of composite roles in SAP BTP, Cloud Foundry environment. [Figure 7.27](#07_003.html#f7.27) shows the available composite roles.

[![SAP API Management: Role Collections](bilderklein/klein07_027.png)](img-f7.27.html) 

**Figure 7.27**     SAP API Management: Role Collections

Some role collections that are common when using SAP API Management include the following:

*   AuthGroup.SelfService.Admin  
    This role is used in the onboarding process.
    
*   AuthGroup.API.Admin  
    This role is authorized to manage access to the developer portal by application developers. Furthermore, the owners of this role can manage the roles for other users. Additionally, they can perform tasks on behalf of developers.
    
*   AuthGroup.ContentAuthor  
    This role authorizes content publishing.
    
*   AuthGroup.API.ApplicationDeveloper  
    This role authorizes the creation, editing, and deletion of applications, as well as access to billing. In addition, holders of this role can access evaluations.
    
*   AuthGroup.Content.Admin  
    This role authorizes the creation and modification of categories.
    
*   AuthGroup.Site.Admin  
    This role allows to change the appearance of the portal.
    

The following predefined role collections are shipped with the API portal component:

*   APIPortal.Administrator  
    This role grants access to the API portal UI and services.
    
*   APIPortal.Service.CatalogIntegration  
    This role authorizes a user to connect to the API catalog in SAP API Business Hub.
    
*   APIManagement.Selfservice.Administrator  
    This role is used in the onboarding process and to access API portal settings.
    
*   APIPortal.Guest  
    This role authorizes read access to the API portal.
    

These role collections are assigned as usual via the SAP BTP cockpit either directly to a user or via an attribute or group mapping from the identity provider.

### 7.3.3    Securing the Provided APIs and Endpoints

SAP API Management allows you to secure the provided APIs through various security policies. These policies are independent of the data sources addressed by the API. The following security policies are provided:

*   Basic authentication
    
*   OAuth v2.0
    
*   OAuth v2.0 GET
    
*   OAuth v2.0 SET
    
*   Verify API key
    
*   SAML assertion policy
    

You can select and apply these security policies depending on your use case. In addition to the classic authentication methods using user name and password (basic authentication), OAuth, or SAML, the verify API key policy also gives you the option of using an API key to authenticate users. This approach is useful because licensing and billing for the use of SAP API Management is typically based on API calls, which are measured based by API key, which API key must be created by an application developer in the developer portal.

## 7.4    SAP Cloud Portal Service and SAP Launchpad Service

The SAP Cloud Portal service in SAP BTP, Neo environment is a web-based tool for providing digital content to your employees, partners, and customers. Typical use cases for the portal include for marketing products and services and for the provision of information. The development of an SAP Fiori launchpad is also possible in SAP BTP, Neo environment via the SAP Cloud Portal service.

The SAP Launchpad service in SAP BTP, Cloud Foundry environment, on the other hand, uses the SAP Fiori launchpad to serve as a central entry point to all applications that employees may need to perform in their daily tasks. The UIs of SAP products based on various technologies (SAPUI5, SAP GUI for HTML, and Web Dynpro ABAP) as well as the interfaces of other content providers can be integrated. The SAP Fiori launchpad enables role-based navigation, user-friendly presentation of content, and single sign-on (SSO).

### 7.4.1    SAP Cloud Portal Service in SAP BTP, Neo Environment

In SAP BTP, Neo environment, the functions for deploying an SAP Fiori launchpad are part of the SAP Cloud Portal service; in other words, no dedicated SAP Launchpad service exists. To gain access to the SAP Cloud Portal service, you must have an administration user. This user can then assign permissions for additional roles. This step is performed during the configuration of the SAP Cloud Portal service, under Roles, as shown in [Figure 7.28](#07_004.html#f7.28).

[![Portal Roles](bilderklein/klein07_028.png)](img-f7.28.html) 

**Figure 7.28**     Portal Roles

The following roles are provided:

*   TENANT\_ADMIN: Authorization to access the administration functions including the creation of new sites
    
*   EXTERNAL\_PORTAL\_USER: User authorization for access to the SAP Cloud Portal service
    
*   WEB\_CONTENT\_EDITOR: Authorization to edit content in the SAP Cloud Portal service
    

#### Websites

Websites are used within the SAP Cloud Portal service. When creating a new website, you can choose from among several different templates, as shown in [Figure 7.29](#07_004.html#f7.29). In our example, we chose the SAP Fiori launchpad template for the following descriptions; this template can be used to build a corresponding launchpad in SAP BTP, Neo environment. A typical deployment scenario is a customer-facing portal, that is, a portal that your business partners and customers can access.

[![Creating a Website Based on a Template](bilderklein/klein07_029.png)](img-f7.29.html) 

**Figure 7.29**     Creating a Website Based on a Template

#### Launchpad Dashboard

The SAP Launchpad service website administration dashboard shown in [Figure 7.30](#07_004.html#f7.30) provides an overview of all relevant artifacts. You can use this dashboard to manage and edit the listed content. The SAP Fiori launchpad created with the SAP Cloud Portal service has many similarities to the SAP Fiori launchpad in an on-premise SAP S/4HANA system. Concepts in common include apps, catalogs, groups, and roles.

[![SAP Cloud Portal Service: Launchpad Dashboard](bilderklein/klein07_030.png)](img-f7.30.html) 

**Figure 7.30**     SAP Cloud Portal Service: Launchpad Dashboard

#### Components of the SAP Fiori Launchpad

The interaction between users, roles, groups, catalogs, and apps is shown in [Figure 7.31](#07_004.html#f7.31). A user can be assigned to roles. The roles can be composed of predefined app catalogs or groups of apps.

[![Interaction between Apps, Catalogs, Groups, and Roles in the SAP Fiori Launchpad](bilderklein/klein07_031.png)](img-f7.31.html) 

**Figure 7.31**     Interaction between Apps, Catalogs, Groups, and Roles in the SAP Fiori Launchpad

#### Integrating Apps

The SAP Fiori launchpad allows you to embed SAP Fiori apps that are either deployed in the same SAP BTP subaccount or in an on-premise system. [Figure 7.32](#07_004.html#f7.32) shows a graphical comparison of these options. Apps from an on-premise system are embedded in an SAP Fiori launchpad using the cloud connector. In addition to SAP Fiori apps, Web Dynpro ABAP apps can also be integrated.

[![Architecture of a Website in the SAP Cloud Portal Service](bilderklein/klein07_032.png)](img-f7.32.html) 

**Figure 7.32**     Architecture of a Website in the SAP Cloud Portal Service

The first step is to reference the apps on the website, in our example, the SAP Fiori launchpad. In this process, you’ll define the origin of the app and configure the appearance and behavior of the tile for calling this app in the launchpad. You’ll then need to assign the app to one or more catalogs. Optionally, you can assign the app to one or more groups.

#### Roles for Apps

For an app to be visible in a user’s SAP Fiori launchpad, the app must be assigned to a role. Catalogs and groups can also be assigned to a role. Standard roles are provided as templates, based on which you can create your own roles. The role with the ID you define must be created in the SAP Cloud Portal service subaccount. As shown in [Figure 7.33](#07_004.html#f7.33), the system checks whether the role already exists in the subaccount when it is saved. If not, you can create the role directly by clicking on the link in the hint message box.

[![Creating a Launchpad Role in an SAP BTP Subaccount](bilderklein/klein07_033.png)](img-f7.33.html) 

**Figure 7.33**     Creating a Launchpad Role in an SAP BTP Subaccount

After the role has been created, it is visible as a customer-specific role in the role overview of the SAP Cloud Portal service, as shown in [Figure 7.34](#07_004.html#f7.34). You can assign the role directly to a user or a group. You can subsequently map user groups to a group in the application identity provider, for example, as you’re familiar with using application roles in SAP BTP.

[![SAP Fiori Launchpad Role in the SAP Cloud Portal Service Configuration](bilderklein/klein07_034.png)](img-f7.34.html) 

**Figure 7.34**     SAP Fiori Launchpad Role in the SAP Cloud Portal Service Configuration

### 7.4.2    SAP Launchpad Service in SAP BTP, Cloud Foundry Environment

The SAP Cloud Portal service discussed in the previous section is only offered in SAP BTP, Cloud Foundry environment in a limited way, namely, as the SAP Launchpad service.

For this service, the Launchpad\_Admin, Launchpad\_Advanced\_Theming, and Launchpad\_External\_User composite roles, shown in [Figure 7.35](#07_004.html#f7.35), are provided.

[![SAP BTP, Cloud Foundry Environment: Role Collections for the SAP Launchpad Service](bilderklein/klein07_035.png)](img-f7.35.html) 

**Figure 7.35**     SAP BTP, Cloud Foundry Environment: Role Collections for the SAP Launchpad Service

The SAP Launchpad service comes with the Launchpad\_Admin composite role. This role allows you to perform all administration tasks for a launchpad site. This composite role must be assigned to a user when setting up the SAP Launchpad service. In addition, this composite role entitles you to use the theme designer for customizing the appearance of the launchpad to match your corporate design. In [Chapter 4](#04_001.html#h4), [Section 4.6.1](#04_006.html#h4.6.1), you learned how to set up the SAP Launchpad service and create an SAP Fiori launchpad through a practical example.

## 7.5    SAP BTP, ABAP Environment

SAP BTP, ABAP environment, is another development and runtime environment offered on SAP BTP in addition to SAP BTP, Neo environment and SAP BTP, Cloud Foundry environment. From a technical point of view, however, SAP BTP, ABAP environment is not an independent environment but instead is a service that is instantiated in SAP BTP, Cloud Foundry environment. The ABAP service serves as a template, so to speak, for the concrete service instance (i.e., an ABAP environment) in the subaccount of an SAP customer. The service instance is deployed within a space in SAP BTP, Cloud Foundry environment. Thus, a basic understanding of SAP BTP, Cloud Foundry environment is required to administer SAP BTP, ABAP environment. Most activities are performed in SAP Fiori apps provided by SAP BTP, ABAP environment.

SAP BTP, ABAP environment can be used both for innovative new applications and for enhancements to existing applications. The innovation use case covers the development of your own applications using all available means. The extensions use case means the functional extension of existing cloud applications.

Programming in the cloud environment is performed using the ABAP RESTful application programming model. This programming model can be used not only in the cloud environment, but also with on-premise SAP S/4HANA systems as of SAP S/4HANA 1909. Compared to classic ABAP programming, the new programming model represents a paradigm shift. The most significant change compared to classic ABAP is the complete abandonment of SAP GUI as an interface technology.

This innovation greatly impacts the work of end users as well as the work of developers and administrators in the following ways:

*   For developers, the ABAP Development Tools (ADT) are delivered based on the Eclipse development environment. Thus, the same tools are used as in modern ABAP development for on-premise applications.
    
*   Administrators work exclusively with SAP Fiori apps.
    
*   End users also work exclusively with SAP Fiori apps.
    

Another innovation has occurred in source code management. The source code is not stored in SAP BTP, ABAP environment, but instead in a Git repository. Such a repository is not provided by SAP but must be obtained by you from an appropriate provider. For this purpose, either a cloud-based Git service or a server operated by yourself in your on-premise system landscape can be used. You’re thus also responsible for the security of the Git repository.

[Figure 7.36](#07_005.html#f7.36) shows the architecture of SAP BTP, ABAP environment, with its various components and a connected Git repository.

[![SAP BTP, ABAP Environment: Architecture](bilderklein/klein07_036.png)](img-f7.36.html) 

**Figure 7.36**     SAP BTP, ABAP Environment: Architecture

In the following sections, we’ll describe the specifics of user management and access to third-party systems by applications developed in SAP BTP, ABAP environment.

### 7.5.1    User Administration

User administration in SAP BTP, ABAP environment is different from user administration in other services and subscriptions in SAP BTP, Cloud Foundry environment. Basically, application users are created in a central SAP Fiori app for administration. Entry is via the SAP Fiori launchpad delivered with the instance of the ABAP service.

###### \[»\]  Full Access to the SAP Fiori Launchpad

Full access to the SAP Fiori launchpad requires the role SAP\_BR\_ADMINISTRATOR. This role is not available to users using the trial version of SAP BTP.

When a user is created, the ABAP service generates a user ID, which cannot be changed. This user ID corresponds to the technical user name within the service. However, SAP BTP, Cloud Foundry environment cannot work with these user IDs. As described in [Chapter 4](#04_001.html#h4), [Section 4.2](#04_002.html#h4.2), users in SAP BTP, Cloud Foundry environment are identified by their email addresses. The link between the user in the instance of the ABAP service and that of SAP BTP, Cloud Foundry environment subaccount is also made using the user’s email address.

Although the service instance runs in an SAP BTP, Cloud Foundry environment space, users are not managed directly in the space, but at the subaccount level. At that level, as mentioned earlier, you have the following options:

*   Managing users in the SAP ID service
    
*   Administering users in the Identity Authentication service
    
*   Administering users in the identity provider of a third-party provider
    

We recommend managing users via the Identity Authentication service because, this way, you can enjoy the highest flexibility of a hybrid SAP landscape and seamless integration of users with all SAP cloud products (as well as many on-premise products).

For SAP BTP, ABAP environment, SAP delivers application catalogs for the SAP Fiori environment. An application catalog is identified by a unique technical ID, such as SAP\_CORE\_BC\_SEC. However, catalogs also have descriptive names, such as “Security.” These catalogs are collections of functionally related apps.

Application roles cannot be assigned to users directly, but via the application catalogs. SAP delivers predefined application roles with the ABAP cloud instance. For example, the SAP\_BR\_ADMINISTRATOR role is assigned to the initial user. You have the option of assigning the application roles delivered by SAP directly to your users. However, you can also create your own application roles. For this task, you can use the roles delivered by SAP as a template or create completely new roles from scratch. SAP delivers the application role templates shown in [Table 7.2](#07_005.html#t7.2) that are relevant for the security application catalog.

 
| Role Name || Description |
| --- | --- |
| SAP\_BR\_ADMINISTRATOR || Administrator of the ABAP cloud instance |
| --- | --- |
| SAP\_BR\_DEVELOPER || Developer of the ABAP cloud instance |

**Table 7.2**     Relevant Templates for Application Roles

Application roles are assigned to users via a separate SAP Fiori app. This step requires neither activities in the SAP BTP cockpit of the subaccount nor in SAP BTP, Cloud Foundry environment space.

###### \[+\]  Development Users

For developers, either a user can be created in the ABAP cloud instance, or a service key can be created in the ABAP cloud instance. The developer can log on to the instance in both ways via ADT in Eclipse. The service key offers an advantage in that all relevant information, such as endpoints or access data, is contained in the service key.

### 7.5.2    Access to External Systems

SAP BTP, ABAP environment also enables communication with third-party systems, regardless of whether they are SAP systems or third-party systems. The SAP Destination service in SAP BTP plays a decisive role in this context. For this purpose, destinations are created in the SAP Destination service that contain the technical configuration of the connection to the target system. This information includes the endpoints, the type of authentication, the protocols used, and more, as described in detail in [Chapter 5](#05_001.html#h5), [Section 5.5](#05_005.html#h5.5).

However, access from SAP BTP, ABAP environment cannot be made directly. Additional artifacts must be created in the ABAP cloud instance for this purpose, such as the following artifacts:

*   Communication agreements
    
*   Communication scenarios
    
*   Communication systems
    
*   Communication users
    

## 7.6    Corporate User Stores

SAP BTP allows you to authenticate users against a corporate identity provider, which holds the users and authenticates them.

The Identity Authentication service acts as a proxy to delegate authentication to the corporate identity provider. Thus, no direct trust relationship exists between the corporate identity provider and the SAP BTP subaccount in the service provider role that the user is trying to access.

An advantage of such an architecture is that, if you have multiple subaccounts, you do not need to create a connection to the corporate identity provider for each individual subaccount. One connection between the Identity Authentication service and the corporate identity provider is sufficient; all further authentications are then performed only against the Identity Authentication service.

The following identity providers are supported as corporate identity providers:

*   SAP Single Sign-on
    
*   Microsoft Active Directory Federation Services
    
*   Microsoft Azure Active Directory (Microsoft Azure AD)
    
*   Other SAML 2.0-compatible identity providers
    

Let’s learn how to configure a corporate identity provider. The Identity Authentication tenant assumes the role of the service provider from the perspective of the corporate identity provider. So far, we’ve only dealt with the direct connection of an identity provider, as we followed an example in [Chapter 4](#04_001.html#h4), [Section 4.6.2](#04_006.html#h4.6.2).

Log on to the Identity Authentication tenant. Open the tenant’s settings by navigating to Applications & Resources • Tenant Settings and then jump to SAML 2.0 Configuration, as shown in [Figure 7.37](#07_006.html#f7.37).

[![Identity Authentication Service: SAML 2.0 Configuration](bilderklein/klein07_037.png)](img-f7.37.html) 

**Figure 7.37**     Identity Authentication Service: SAML 2.0 Configuration

In the SAML 2.0 configuration, you can download the metadata in the form of an XML file by clicking the Download Metadata File button, as shown in [Figure 7.38](#07_006.html#f7.38).

[![Metadata Download](bilderklein/klein07_038.png)](img-f7.38.html) 

**Figure 7.38**     Metadata Download

For the next step, log on to your corporate identity provider. Open the service provider configuration and import the SAML 2.0 metadata from the Identity Authentication tenant. If necessary, perform advanced configuration, such as entitlement assignment. Then, export the SAML 2.0 metadata of your corporate identity provider.

Now, log back into the Identity Authentication tenant. Your user must be assigned the manage corporate identity providers role. Navigate to Identity Providers • Corporate Identity Providers, as shown in [Figure 7.39](#07_006.html#f7.39), and either select an existing provider or create a new one. Then, jump down to the details. For our example, you can select the demo corporate identity provider.

[![Corporate Identity Providers Overview](bilderklein/klein07_039.png)](img-f7.39.html) 

**Figure 7.39**     Corporate Identity Providers Overview

The next step is to perform the SAML 2.0 configuration. For this task, open the SAML 2.0 Configuration in the TRUST area, as shown in [Figure 7.40](#07_006.html#f7.40).

[![Opening the SAML 2.0 Configuration](bilderklein/klein07_040.png)](img-f7.40.html) 

**Figure 7.40**     Opening the SAML 2.0 Configuration

Import the metadata of the corporate identity provider via the Browse... button and make any necessary adjustments, as shown in [Figure 7.41](#07_006.html#f7.41). Finally, the configuration must be saved.

[![Importing SAML Identity Provider Metadata](bilderklein/klein07_041.png)](img-f7.41.html) 

**Figure 7.41**     Importing SAML Identity Provider Metadata

## 7.7    Checklist for Securing Cloud Services

The checklist in [Table 7.3](#07_007.html#t7.3) covers general security topics that must be observed for each SAP BTP service or subscription.

 
| Completed || Task |
| --- | --- |
|  || You’ve checked whether a service is offered as a subscription or as an instance. For a subscription, you’ve checked whether the service runs in a subaccount or, for example, as a multitenant subscription. |
| --- | --- |
|  || You’ve ensured the number of instances of a service you need (for example, one development instance and one production instance). |
|  || You’ve decided whether to instantiate the service in an existing subaccount or in a new one. |
|  || You’ve identified any dependent services in the documentation for the relevant service. These dependencies have been documented to facilitate risk assessment as changes are made to settings or entire applications. |
|  || You’ve checked how the service is licensed. |
|  || You’ve clarified which identity provider you’ll use and how any technical service access and/or activation is to take place. |
|  || The documentation of the service and its settings has been planned, including where and how exactly settings are documented. |
|  || The service has an owner within your organization who coordinates its usage and configuration. |
|  || The role collections provided have been analyzed and adjusted as needed. |
|  || The required connections via the cloud connector and the SAP Destination service have been requested and modeled. |

**Table 7.3**     Checklist for Securing Cloud Services

## 7.8    Summary

In this chapter, we have shown you how to secure important and frequently used cloud services on SAP BTP. We started with developer tools in the form of SAP Web IDE and SAP Business Application Studio. We want to highlight again that SAP Web IDE is being discontinued since it is based on SAP BTP, Neo environment. In the medium term, you’ll therefore need to switch to SAP Business Application Studio and thus to the SAP BTP, Cloud Foundry environment stack.

After that, we continued with Cloud Integration, SAP’s cloud middleware used in connection with almost all SAP SaaS solutions as well as in the business-to-business (B2B) and business-to-governance (B2G) area. Although Cloud Integration is part of SAP Integration Suite, it has been deliberately treated as an independent service.

SAP API Management was then discussed in the context of SAP Integration Suite. Alongside Cloud Integration, SAP API Management is the most frequently used service in SAP Integration Suite. You learned how the service is secured both from an administration perspective and a developer perspective and which roles are offered in this context.

External access to SAP systems and thus the provision of UIs for end users are also important topics in SAP BTP. In this context, the SAP Cloud Portal service is offered in SAP BTP, Neo environment. In contrast, the SAP Launchpad service is offered in SAP BTP, Cloud Foundry environment. We covered the security-relevant aspects for both offerings.

For a long time, ABAP and the cloud sounded like a contradiction in terms. But for some years now, SAP has also had its own ABAP environment in the cloud. SAP BTP, ABAP environment uses its own programming model called the ABAP RESTful application programming model. But in addition to the new programming model, the administration of the users has also changed fundamentally. We presented the relevant security aspects at a high level.

Using your own established authentication infrastructure can also save you a lot of work in SAP BTP. Therefore, this scenario is adopted by many customers. We showed you where and how to set up a corporate identity provider in the Identity Authentication service.

Finally, we’ve put together a checklist to help you activate and use various cloud services in an accelerated and complete implementation.

# A    The Authors

[![](bilderklein/kleinkoch_martin.png)](img-f_none_A_00.html) 

Martin Koch is the managing director of CloudDNA GmbH, an SAP partner in Austria. He and his team conduct training for SAP and have developed four of their own training courses on the topics of SAPUI5, SAP Fiori, cloud integration, and cloud security, which are listed in the SAP training catalog. In addition to his work as a trainer, Martin Koch works as an architect, consultant, and developer for international SAP customers of all company sizes.

Originally trained as an airline pilot and air traffic controller, he participated in a trainee program at SAP Austria in 2007. There, he initially worked on the topics of integration and SAP NetWeaver AS for Java. In 2010, his focus shifted to mobile applications in the SAP environment. After several projects on the architecture, security, and development of mobile solutions, in 2012, Martin Koch focused on SAP HANA, SAPUI5, SAP Fiori, and SAP Business Technology Platform (SAP BTP).

[![](bilderklein/kleinzeilinger_siegfried.png)](img-f_none_A_01.html) 

Siegfried Zeilinger is a freelancer and the managing director of a small management consultancy. His focus is on consulting and security auditing of IT systems as well as authorization and identity management for SAP solutions. His consulting portfolio ranges from SAP architecture to development strategies for ABAP, Java, and the cloud to SAP identity management. In 2016, he received certification as an IT auditor (CISA). Most recently, Siegfried has worked primarily in the pharmaceutical industry and the public sector.

Before becoming self-employed in 2011, he worked for SAP Austria as an SAP NetWeaver and portal consultant and carried out major international projects. Today, he regularly conducts training courses for SAP on the topics of authorizations, SAP in the cloud, and SAP NetWeaver. From 2003 to 2019, he supervised theses at the Vienna University of Technology and the University of Applied Sciences Wiener Neustadt and held various courses in the field of SAP.

# Index

[↓**A**](#index.html#grp1)  [↓**B**](#index.html#grp2)  [↓**C**](#index.html#grp3)  [↓**D**](#index.html#grp4)  [↓**E**](#index.html#grp5)  [↓**F**](#index.html#grp6)  [↓**G**](#index.html#grp7)  [↓**H**](#index.html#grp8)  [↓**I**](#index.html#grp9)  [↓**J**](#index.html#grp10)  [↓**K**](#index.html#grp11)  [↓**L**](#index.html#grp12)  [↓**M**](#index.html#grp13)  [↓**N**](#index.html#grp14)  [↓**O**](#index.html#grp15)  [↓**P**](#index.html#grp16)  [↓**Q**](#index.html#grp17)  [↓**R**](#index.html#grp18)  [↓**S**](#index.html#grp19)  [↓**T**](#index.html#grp20)  [↓**U**](#index.html#grp21)  [↓**V**](#index.html#grp22)  [↓**W**](#index.html#grp23)  

[A ⇑](#index.html#index)

ABAP [\[→ Section 4.4\]](#04_004.html#i04_63) [\[→ Section 7.1\]](#07_001.html#i07_14) [\[→ Section 7.5\]](#07_005.html#i07_135)

ABAP Development Tools (ADT) [\[→ Section 7.5\]](#07_005.html#i07_138)

ABAP RESTful application programming model [\[→ Section 7.5\]](#07_005.html#i07_137)

Access control [\[→ Section 5.4\]](#05_004.html#i05_82) [\[→ Section 5.7\]](#05_007.html#i05_129)

configuration [\[→ Section 5.4\]](#05_004.html#i05_85)

Access control lists (ACLs) [\[→ Section 5.4\]](#05_004.html#i05_83)

Access policies [\[→ Section 7.2\]](#07_002.html#i07_102)

Access tokens [\[→ Section 2.3\]](#02_003.html#i02_122)

Active/active failover [\[→ Section 5.2\]](#05_002.html#i05_39)

Active/passive failover [\[→ Section 5.2\]](#05_002.html#i05_38)

Admin platform role [\[→ Section 3.4\]](#03_004.html#i03_100)

Administration console [\[→ Section 2.2\]](#02_002.html#i02_91) [\[→ Section 2.4\]](#02_004.html#i02_155) [\[→ Section 3.3\]](#03_003.html#i03_65) [\[→ Section 3.6\]](#03_006.html#i03_170) [\[→ Section 4.3\]](#04_003.html#i04_35)

Administrator [\[→ Section 7.2\]](#07_002.html#i07_91)

role [\[→ Section 4.6\]](#04_006.html#i04_93)

Alerts [\[→ Section 2.4\]](#02_004.html#i02_181)

Alibaba Cloud [\[→ Section 1.1\]](#01_001.html#i01_11) [\[→ Section 1.2\]](#01_002.html#i01_60)

Amazon Simple Email Service [\[→ Section 2.4\]](#02_004.html#i02_180)

Amazon Web Services (AWS) [\[→ Section 1.1\]](#01_001.html#i01_08) [\[→ Section 1.2\]](#01_002.html#i01_57) [\[→ Section 2.5\]](#02_005.html#i02_220)

Apache Camel [\[→ Section 7.1\]](#07_001.html#i07_08)

API portal [\[→ Section 7.3\]](#07_003.html#i07_114)

APIs [\[→ Section 1.2\]](#01_002.html#i01_100) [\[→ Section 5.2\]](#05_002.html#i05_46) [\[→ Section 7.1\]](#07_001.html#i07_10) [\[→ Section 7.3\]](#07_003.html#i07_107)

administration [\[→ Section 6.3\]](#06_003.html#i06_15)

audit log retrieval [\[→ Section 6.3\]](#06_003.html#i06_24)

base URLs [\[→ Section 5.2\]](#05_002.html#i05_50)

checklist [\[→ Section 6.4\]](#06_004.html#i06_74)

data [\[→ Section 5.2\]](#05_002.html#i05_47)

global account retrieval [\[→ Section 6.3\]](#06_003.html#i06_70)

HTTP methods [\[→ Section 6.3\]](#06_003.html#i06_18)

management functions [\[→ Section 6.3\]](#06_003.html#i06_62)

permissions management [\[→ Section 6.3\]](#06_003.html#i06_54)

SAP Cloud Management service [\[→ Section 6.3\]](#06_003.html#i06_60)

test [\[→ Section 6.3\]](#06_003.html#i06_68)

user management [\[→ Section 6.3\]](#06_003.html#i06_42)

verify key [\[→ Section 7.3\]](#07_003.html#i07_117)

App router [\[→ Section 2.3\]](#02_003.html#i02_128)

Application identity providers [\[→ Section 2.2\]](#02_002.html#i02_63) [\[→ Section 3.3\]](#03_003.html#i03_70)

configuration [\[→ Section 3.6\]](#03_006.html#i03_171)

Microsoft Azure AD [\[→ Section 3.6\]](#03_006.html#i03_162) [\[→ Section 3.6\]](#03_006.html#i03_206)

set up [\[→ Section 3.3\]](#03_003.html#i03_75)

Applications [\[→ Section 1.2\]](#01_002.html#i01_110) [\[→ Section 2.4\]](#02_004.html#i02_158) [\[→ Section 2.4\]](#02_004.html#i02_185) [\[→ Section 3.4\]](#03_004.html#i03_116)

assign roles [\[→ Section 3.4\]](#03_004.html#i03_128)

catalogs [\[→ Section 7.5\]](#07_005.html#i07_144)

instance [\[→ Section 4.4\]](#04_004.html#i04_53)

overview [\[→ Section 3.4\]](#03_004.html#i03_124)

role administration [\[→ Section 3.4\]](#03_004.html#i03_131)

roles [\[→ Section 3.4\]](#03_004.html#i03_94) [\[→ Section 3.4\]](#03_004.html#i03_115) [\[→ Section 3.4\]](#03_004.html#i03_125) [\[→ Section 3.4\]](#03_004.html#i03_136) [\[→ Section 3.4\]](#03_004.html#i03_137) [\[→ Section 7.5\]](#07_005.html#i07_145)

scopes [\[→ Section 2.3\]](#02_003.html#i02_131)

Architecture [\[→ Section 1.3\]](#01_003.html#i01_112)

Assertion consumer service [\[→ Section 3.6\]](#03_006.html#i03_208)

Assertion-based attribute [\[→ Section 3.6\]](#03_006.html#i03_211)

Assertion-based group [\[→ Section 3.6\]](#03_006.html#i03_213)

Asymmetric encryption [\[→ Section 2.1\]](#02_001.html#i02_14)

Asynchronous messaging [\[→ Section 1.1\]](#01_001.html#i01_37)

Audit log [\[→ Section 5.4\]](#05_004.html#i05_72) [\[→ Section 7.2\]](#07_002.html#i07_58)

Audit log retrieval [\[→ Section 6.3\]](#06_003.html#i06_25)

authentication [\[→ Section 6.3\]](#06_003.html#i06_28)

SAP BTP, Cloud Foundry environment [\[→ Section 6.3\]](#06_003.html#i06_36)

SAP BTP, Neo environment [\[→ Section 6.3\]](#06_003.html#i06_27)

Authentication [\[→ Section 2.2\]](#02_002.html#i02_51) [\[→ Section 2.4\]](#02_004.html#i02_137)

methods [\[→ Section 5.3\]](#05_003.html#i05_57) [\[→ Section 7.2\]](#07_002.html#i07_98)

scenarios [\[→ Section 2.2\]](#02_002.html#i02_73)

Authentication rules [\[→ Section 2.4\]](#02_004.html#i02_193) [\[→ Section 3.6\]](#03_006.html#i03_173) [\[→ Section 3.6\]](#03_006.html#i03_175)

attributes [\[→ Section 2.4\]](#02_004.html#i02_198)

options [\[→ Section 2.4\]](#02_004.html#i02_194)

Authorization [\[→ Section 2.3\]](#02_003.html#i02_111)

concept [\[→ Section 3.4\]](#03_004.html#i03_110) [\[→ Section 3.4\]](#03_004.html#i03_143)

grant [\[→ Section 2.3\]](#02_003.html#i02_123)

server [\[→ Section 2.3\]](#02_003.html#i02_121)

Authorization management [\[→ Section 3.4\]](#03_004.html#i03_91) [\[→ Section 4.4\]](#04_004.html#i04_44)

assign roles [\[→ Section 3.4\]](#03_004.html#i03_138)

Cloud Foundry [\[→ Section 4.4\]](#04_004.html#i04_43) [\[→ Section 6.3\]](#06_003.html#i06_58)

Neo [\[→ Section 3.4\]](#03_004.html#i03_90) [\[→ Section 6.3\]](#06_003.html#i06_56)

real-world examples [\[→ Section 3.6\]](#03_006.html#i03_159)

user groups [\[→ Section 3.4\]](#03_004.html#i03_146) [\[→ Section 7.1\]](#07_001.html#i07_31)

Authorization Management API [\[→ Section 6.3\]](#06_003.html#i06_49) [\[→ Section 6.3\]](#06_003.html#i06_55)

[B ⇑](#index.html#index)

Backend Connections API [\[→ Section 5.2\]](#05_002.html#i05_53)

Basic authentication [\[→ Section 5.2\]](#05_002.html#i05_48) [\[→ Section 6.3\]](#06_003.html#i06_32) [\[→ Section 7.2\]](#07_002.html#i07_73)

Bearer token [\[→ Section 6.3\]](#06_003.html#i06_33)

Branding [\[→ Section 2.4\]](#02_004.html#i02_199)

Brute force attacks [\[→ Section 2.2\]](#02_002.html#i02_53)

Buildpacks [\[→ Section 1.2\]](#01_002.html#i01_91) [\[→ Section 1.2\]](#01_002.html#i01_93)

Bundle licenses [\[→ Section 2.4\]](#02_004.html#i02_216)

Business expert [\[→ Section 7.2\]](#07_002.html#i07_90)

Business rules [\[→ Section 2.5\]](#02_005.html#i02_219)

Business services [\[→ Section 1.2\]](#01_002.html#i01_68)

Business-to-business (B2B) [\[→ Section 2.4\]](#02_004.html#i02_148)

Business-to-consumer (B2C) [\[→ Section 2.4\]](#02_004.html#i02_144)

Business-to-employee (B2E) [\[→ Section 2.4\]](#02_004.html#i02_150)

[C ⇑](#index.html#index)

Caesar cipher [\[→ Section 2.1\]](#02_001.html#i02_12)

Canonical name (CNAME) [\[→ Section 6.5\]](#06_005.html#i06_83)

Certificate authority (CA) [\[→ Section 5.2\]](#05_002.html#i05_28) [\[→ Section 6.5\]](#06_005.html#i06_81)

Certificate handling [\[→ Section 2.1\]](#02_001.html#i02_38)

Certificate signing request (CSR) [\[→ Section 6.5\]](#06_005.html#i06_79)

Certificate-based authentication [\[→ Section 5.7\]](#05_007.html#i05_130)

Change history [\[→ Section 3.2\]](#03_002.html#i03_34) [\[→ Section 3.2\]](#03_002.html#i03_39)

Claims [\[→ Section 3.6\]](#03_006.html#i03_201)

Client [\[→ Section 2.3\]](#02_003.html#i02_120)

certificates [\[→ Section 2.2\]](#02_002.html#i02_55) [\[→ Section 7.2\]](#07_002.html#i07_75)

Cloud connector [\[→ Section 2.2\]](#02_002.html#i02_103) [\[→ Section 2.2\]](#02_002.html#i02_109) [\[→ Section 5.1\]](#05_001.html#i05_00)

architecture [\[→ Section 5.1\]](#05_001.html#i05_03)

audit log [\[→ Section 5.4\]](#05_004.html#i05_71)

authentication methods [\[→ Section 5.3\]](#05_003.html#i05_56)

check connectivity [\[→ Section 5.4\]](#05_004.html#i05_105)

cloud-to-on-premise [\[→ Section 5.4\]](#05_004.html#i05_63)

configuration [\[→ Section 5.2\]](#05_002.html#i05_21)

configuration checklist [\[→ Section 5.6\]](#05_006.html#i05_123)

connect to subaccount [\[→ Section 5.2\]](#05_002.html#i05_36)

connection to SAP BTP [\[→ Section 5.2\]](#05_002.html#i05_34)

download [\[→ Section 5.2\]](#05_002.html#i05_15)

high availability [\[→ Section 5.2\]](#05_002.html#i05_42)

implementing cookies [\[→ Section 5.4\]](#05_004.html#i05_93)

installation [\[→ Section 5.1\]](#05_001.html#i05_12) [\[→ Section 5.2\]](#05_002.html#i05_16)

instances [\[→ Section 5.2\]](#05_002.html#i05_43)

integration examples [\[→ Section 5.1\]](#05_001.html#i05_07)

LDAP configuration [\[→ Section 5.7\]](#05_007.html#i05_143)

limitations [\[→ Section 5.1\]](#05_001.html#i05_11)

location ID [\[→ Section 5.2\]](#05_002.html#i05_25)

monitoring [\[→ Section 5.2\]](#05_002.html#i05_44)

permissions [\[→ Section 5.4\]](#05_004.html#i05_90)

platform roles [\[→ Section 3.4\]](#03_004.html#i03_99)

portable [\[→ Section 5.2\]](#05_002.html#i05_31)

positioning [\[→ Section 5.1\]](#05_001.html#i05_14)

real-world examples [\[→ Section 5.7\]](#05_007.html#i05_124)

SAP Launchpad service [\[→ Section 4.6\]](#04_006.html#i04_105)

service accounts [\[→ Section 5.2\]](#05_002.html#i05_32)

set up connections [\[→ Section 5.4\]](#05_004.html#i05_74)

set up destinations [\[→ Section 5.5\]](#05_005.html#i05_107)

trusted applications [\[→ Section 5.4\]](#05_004.html#i05_97)

Cloud Foundry [\[→ Section 1.1\]](#01_001.html#i01_15) [\[→ Section 1.2\]](#01_002.html#i01_63) [\[→ Section 1.2\]](#01_002.html#i01_86) [\[→ Section 4.1\]](#04_001.html#i04_00) [\[→ Section 5.5\]](#05_005.html#i05_120) [\[→ Section 5.7\]](#05_007.html#i05_134) [\[→ Section 7.2\]](#07_002.html#i07_64) [\[→ Section 7.3\]](#07_003.html#i07_105) [\[→ Section 7.4\]](#07_004.html#i07_132)

authorization management [\[→ Section 4.4\]](#04_004.html#i04_41)

buildpacks [\[→ Section 1.2\]](#01_002.html#i01_92)

CLI [\[→ Section 4.1\]](#04_001.html#i04_06) [\[→ Section 4.1\]](#04_001.html#i04_09)

destinations [\[→ Section 2.1\]](#02_001.html#i02_36)

disable [\[→ Section 1.3\]](#01_003.html#i01_142)

enable [\[→ Section 1.3\]](#01_003.html#i01_140)

identity providers [\[→ Section 2.2\]](#02_002.html#i02_93)

permissions [\[→ Section 4.5\]](#04_005.html#i04_79)

role collections [\[→ Section 4.4\]](#04_004.html#i04_57)

roles [\[→ Section 4.4\]](#04_004.html#i04_45)

trust configuration [\[→ Section 4.3\]](#04_003.html#i04_25)

two-factor authentication [\[→ Section 4.6\]](#04_006.html#i04_108)

user management [\[→ Section 4.2\]](#04_002.html#i04_14)

Cloud Integration capability [\[→ Section 1.1\]](#01_001.html#i01_44) [\[→ Section 1.2\]](#01_002.html#i01_81) [\[→ Section 1.2\]](#01_002.html#i01_95) [\[→ Section 7.1\]](#07_001.html#i07_05) [\[→ Section 7.2\]](#07_002.html#i07_45)

access log [\[→ Section 7.2\]](#07_002.html#i07_56)

architecture [\[→ Section 7.2\]](#07_002.html#i07_50)

audit log [\[→ Section 7.2\]](#07_002.html#i07_59)

integration flow [\[→ Section 7.2\]](#07_002.html#i07_78)

roles and authorizations [\[→ Section 7.2\]](#07_002.html#i07_85)

SAP BTP, Cloud Foundry environment [\[→ Section 7.2\]](#07_002.html#i07_63)

security recommendations [\[→ Section 7.2\]](#07_002.html#i07_100)

user authentication [\[→ Section 7.2\]](#07_002.html#i07_71)

Cloud Platform Enterprise Agreement (CPEA) [\[→ Section 1.3\]](#01_003.html#i01_117)

Cloud security [\[→ Section 2.1\]](#02_001.html#i02_02) [\[→ Section 3.3\]](#03_003.html#i03_85)

Cloud services [\[→ Section 7.1\]](#07_001.html#i07_00)

security checklist [\[→ Section 7.7\]](#07_007.html#i07_155)

Cloud-to-on-premise [\[→ Section 5.4\]](#05_004.html#i05_64) [\[→ Section 5.7\]](#05_007.html#i05_137)

new connection [\[→ Section 5.4\]](#05_004.html#i05_76)

permissions [\[→ Section 5.4\]](#05_004.html#i05_65)

systems [\[→ Section 5.4\]](#05_004.html#i05_75)

Code snippets [\[→ Section 6.3\]](#06_003.html#i06_22)

Command line [\[→ Section 1.2\]](#01_002.html#i01_108) [\[→ Section 6.1\]](#06_001.html#i06_00)

calling help [\[→ Section 6.5\]](#06_005.html#i06_88)

checklist [\[→ Section 6.4\]](#06_004.html#i06_73)

Cloud Foundry [\[→ Section 4.1\]](#04_001.html#i04_07)

display commands [\[→ Section 3.1\]](#03_001.html#i03_11)

global account [\[→ Section 6.2\]](#06_002.html#i06_10)

Neo [\[→ Section 3.1\]](#03_001.html#i03_05) [\[→ Section 3.1\]](#03_001.html#i03_09) [\[→ Section 6.1\]](#06_001.html#i06_02)

real-world example [\[→ Section 6.5\]](#06_005.html#i06_75)

subaccounts list [\[→ Section 6.1\]](#06_001.html#i06_05)

Communication protocols [\[→ Section 2.1\]](#02_001.html#i02_07)

SAP Destination service [\[→ Section 2.1\]](#02_001.html#i02_17)

Composite roles [\[→ Section 4.4\]](#04_004.html#i04_52) [\[→ Section 7.3\]](#07_003.html#i07_112)

copy [\[→ Section 4.4\]](#04_004.html#i04_62)

create [\[→ Section 4.4\]](#04_004.html#i04_60)

designation [\[→ Section 4.6\]](#04_006.html#i04_125)

maintain [\[→ Section 4.4\]](#04_004.html#i04_56)

mapping [\[→ Section 4.4\]](#04_004.html#i04_66) [\[→ Section 4.6\]](#04_006.html#i04_122)

naming conventions [\[→ Section 4.4\]](#04_004.html#i04_61)

Conditional authentication [\[→ Section 2.4\]](#02_004.html#i02_188)

Connection tests [\[→ Section 2.1\]](#02_001.html#i02_43)

Consumer accounts [\[→ Section 3.4\]](#03_004.html#i03_119)

Consumer subaccounts [\[→ Section 2.1\]](#02_001.html#i02_28)

Content manager [\[→ Section 4.6\]](#04_006.html#i04_101)

Continuous integration (CI)/continuous delivery (CD) [\[→ Section 7.1\]](#07_001.html#i07_21)

Core Service APIs [\[→ Section 6.3\]](#06_003.html#i06_63)

Corporate identity provider [\[→ Section 2.2\]](#02_002.html#i02_78) [\[→ Section 2.4\]](#02_004.html#i02_163) [\[→ Section 7.6\]](#07_006.html#i07_150)

configuration [\[→ Section 7.6\]](#07_006.html#i07_152) [\[→ Section 7.6\]](#07_006.html#i07_154)

CP default trace [\[→ Section 7.2\]](#07_002.html#i07_62)

CSS [\[→ Section 2.4\]](#02_004.html#i02_160)

cURL [\[→ Section 6.3\]](#06_003.html#i06_23)

Custom domain [\[→ Section 6.5\]](#06_005.html#i06_76)

Custom identity providers [\[→ Section 2.2\]](#02_002.html#i02_65) [\[→ Section 2.2\]](#02_002.html#i02_71)

Customer-owned applications [\[→ Section 3.3\]](#03_003.html#i03_71) [\[→ Section 3.3\]](#03_003.html#i03_79)

Customer-specific roles [\[→ Section 3.4\]](#03_004.html#i03_127)

[D ⇑](#index.html#index)

Data centers [\[→ Section 1.1\]](#01_001.html#i01_06) [\[→ Section 1.2\]](#01_002.html#i01_106) [\[→ Section 3.1\]](#03_001.html#i03_14)

DataGrip [\[→ Section 6.1\]](#06_001.html#i06_06)

Demilitarized zone (DMZ) [\[→ Section 5.1\]](#05_001.html#i05_13)

Destinations [\[→ Section 2.1\]](#02_001.html#i02_18) [\[→ Section 5.5\]](#05_005.html#i05_109) [\[→ Section 7.5\]](#07_005.html#i07_148)

certificate handling [\[→ Section 2.1\]](#02_001.html#i02_39)

check connection [\[→ Section 5.5\]](#05_005.html#i05_118)

Cloud Foundry [\[→ Section 2.1\]](#02_001.html#i02_35) [\[→ Section 5.5\]](#05_005.html#i05_121)

communication [\[→ Section 5.5\]](#05_005.html#i05_110)

create [\[→ Section 2.1\]](#02_001.html#i02_26)

Git server [\[→ Section 5.7\]](#05_007.html#i05_132)

Neo [\[→ Section 2.1\]](#02_001.html#i02_20) [\[→ Section 5.5\]](#05_005.html#i05_112)

truststores [\[→ Section 2.1\]](#02_001.html#i02_49)

types [\[→ Section 2.1\]](#02_001.html#i02_30)

Dev spaces [\[→ Section 7.1\]](#07_001.html#i07_38)

Developer platform role [\[→ Section 3.4\]](#03_004.html#i03_101)

Development tools [\[→ Section 1.2\]](#01_002.html#i01_109)

DiAdministrator [\[→ Section 7.1\]](#07_001.html#i07_28)

Dialog user [\[→ Section 7.2\]](#07_002.html#i07_72) [\[→ Section 7.2\]](#07_002.html#i07_86)

DiDeveloper [\[→ Section 7.1\]](#07_001.html#i07_27)

Digital process automation [\[→ Section 1.1\]](#01_001.html#i01_32)

Directories [\[→ Section 1.3\]](#01_003.html#i01_132) [\[→ Section 6.2\]](#06_002.html#i06_12) [\[→ Section 6.5\]](#06_005.html#i06_86)

Directory service [\[→ Section 2.2\]](#02_002.html#i02_100)

DiScpGitAdministrator [\[→ Section 7.1\]](#07_001.html#i07_29)

Distinguished name (DN) [\[→ Section 2.2\]](#02_002.html#i02_101)

Domain Name System (DNS) [\[→ Section 6.5\]](#06_005.html#i06_78)

[E ⇑](#index.html#index)

eDocuments [\[→ Section 1.1\]](#01_001.html#i01_53)

Email notifications [\[→ Section 2.4\]](#02_004.html#i02_177)

Encryption [\[→ Section 2.1\]](#02_001.html#i02_10)

End users [\[→ Section 3.2\]](#03_002.html#i03_22)

Enhanced Change and Transport System (CTS+) [\[→ Section 1.2\]](#01_002.html#i01_77)

Entitlements [\[→ Section 1.3\]](#01_003.html#i01_120)

configuration [\[→ Section 1.3\]](#01_003.html#i01_123)

Events [\[→ Section 1.1\]](#01_001.html#i01_35)

Extended services for user account and authentication (XSUAA) [\[→ Section 4.3\]](#04_003.html#i04_38)

Extensions [\[→ Section 1.1\]](#01_001.html#i01_38)

External identity provider [\[→ Section 2.2\]](#02_002.html#i02_97) [\[→ Section 3.6\]](#03_006.html#i03_189) [\[→ Section 4.3\]](#04_003.html#i04_36) [\[→ Section 4.3\]](#04_003.html#i04_39) [\[→ Section 4.4\]](#04_004.html#i04_67) [\[→ Section 4.5\]](#04_005.html#i04_83)

Microsoft Azure AD [\[→ Section 4.6\]](#04_006.html#i04_119)

[F ⇑](#index.html#index)

Failover [\[→ Section 5.2\]](#05_002.html#i05_37)

Feature sets [\[→ Section 1.3\]](#01_003.html#i01_125) [\[→ Section 1.3\]](#01_003.html#i01_131) [\[→ Section 2.2\]](#02_002.html#i02_86) [\[→ Section 4.1\]](#04_001.html#i04_03)

Form-field authentication [\[→ Section 5.2\]](#05_002.html#i05_49)

Fully qualified domain name (FQDN) [\[→ Section 5.4\]](#05_004.html#i05_69)

[G ⇑](#index.html#index)

Git [\[→ Section 5.7\]](#05_007.html#i05_126) [\[→ Section 7.1\]](#07_001.html#i07_19) [\[→ Section 7.5\]](#07_005.html#i07_139)

authorizations [\[→ Section 7.1\]](#07_001.html#i07_22)

server [\[→ Section 7.1\]](#07_001.html#i07_20)

Global accounts [\[→ Section 1.3\]](#01_003.html#i01_118)

administration [\[→ Section 1.3\]](#01_003.html#i01_124)

feature sets [\[→ Section 1.3\]](#01_003.html#i01_126)

log on [\[→ Section 1.3\]](#01_003.html#i01_119)

manage via command line [\[→ Section 6.2\]](#06_002.html#i06_09)

overview [\[→ Section 3.2\]](#03_002.html#i03_37)

retrieve information [\[→ Section 6.3\]](#06_003.html#i06_71)

role collections [\[→ Section 1.3\]](#01_003.html#i01_127)

users [\[→ Section 3.2\]](#03_002.html#i03_20)

view [\[→ Section 6.5\]](#06_005.html#i06_90)

Globally unique identifier (GUID) [\[→ Section 2.4\]](#02_004.html#i02_174)

Google Cloud Platform [\[→ Section 1.1\]](#01_001.html#i01_09) [\[→ Section 1.2\]](#01_002.html#i01_59)

Grant types [\[→ Section 2.3\]](#02_003.html#i02_124) [\[→ Section 7.2\]](#07_002.html#i07_83)

Group assignment [\[→ Section 3.4\]](#03_004.html#i03_151)

Group claim [\[→ Section 4.6\]](#04_006.html#i04_116)

Group mapping [\[→ Section 7.1\]](#07_001.html#i07_32)

[H ⇑](#index.html#index)

Health Check API [\[→ Section 5.2\]](#05_002.html#i05_51)

HOST field [\[→ Section 5.4\]](#05_004.html#i05_79)

Hosts [\[→ Section 3.1\]](#03_001.html#i03_13)

HTML [\[→ Section 3.4\]](#03_004.html#i03_123)

HTML5 [\[→ Section 3.4\]](#03_004.html#i03_103)

applications [\[→ Section 5.4\]](#05_004.html#i05_96)

HTTP

access log [\[→ Section 7.2\]](#07_002.html#i07_61)

destination [\[→ Section 2.1\]](#02_001.html#i02_31)

header authorization [\[→ Section 6.3\]](#06_003.html#i06_34)

protocol [\[→ Section 2.1\]](#02_001.html#i02_08)

HTTPS [\[→ Section 2.1\]](#02_001.html#i02_06) [\[→ Section 5.1\]](#05_001.html#i05_06) [\[→ Section 5.7\]](#05_007.html#i05_138)

endpoint [\[→ Section 2.1\]](#02_001.html#i02_42)

protocol [\[→ Section 1.1\]](#01_001.html#i01_45) [\[→ Section 2.1\]](#02_001.html#i02_09)

proxy [\[→ Section 5.2\]](#05_002.html#i05_26)

Hybrid landscapes [\[→ Section 1.2\]](#01_002.html#i01_111)

Hyperscaler [\[→ Section 1.1\]](#01_001.html#i01_07)

[I ⇑](#index.html#index)

Identity Authentication add-on [\[→ Section 2.2\]](#02_002.html#i02_106)

Identity Authentication service [\[→ Section 2.2\]](#02_002.html#i02_62) [\[→ Section 2.2\]](#02_002.html#i02_72) [\[→ Section 2.2\]](#02_002.html#i02_98) [\[→ Section 2.2\]](#02_002.html#i02_105) [\[→ Section 2.4\]](#02_004.html#i02_135) [\[→ Section 3.2\]](#03_002.html#i03_32) [\[→ Section 3.2\]](#03_002.html#i03_36) [\[→ Section 3.3\]](#03_003.html#i03_57) [\[→ Section 3.3\]](#03_003.html#i03_60) [\[→ Section 3.3\]](#03_003.html#i03_64) [\[→ Section 3.3\]](#03_003.html#i03_86) [\[→ Section 3.6\]](#03_006.html#i03_167) [\[→ Section 3.6\]](#03_006.html#i03_178) [\[→ Section 3.6\]](#03_006.html#i03_182) [\[→ Section 4.3\]](#04_003.html#i04_32) [\[→ Section 7.1\]](#07_001.html#i07_39) [\[→ Section 7.5\]](#07_005.html#i07_143) [\[→ Section 7.6\]](#07_006.html#i07_151)

administrator types [\[→ Section 2.4\]](#02_004.html#i02_164)

advanced information [\[→ Section 2.4\]](#02_004.html#i02_169)

authenticate users [\[→ Section 3.3\]](#03_003.html#i03_62)

scenarios [\[→ Section 2.4\]](#02_004.html#i02_143)

source system [\[→ Section 2.4\]](#02_004.html#i02_207)

user maintenance [\[→ Section 2.4\]](#02_004.html#i02_157)

user management [\[→ Section 2.4\]](#02_004.html#i02_167)

Identity Authentication tenant [\[→ Section 2.2\]](#02_002.html#i02_76) [\[→ Section 2.2\]](#02_002.html#i02_107) [\[→ Section 2.4\]](#02_004.html#i02_141) [\[→ Section 3.3\]](#03_003.html#i03_72) [\[→ Section 3.3\]](#03_003.html#i03_78) [\[→ Section 4.3\]](#04_003.html#i04_33) [\[→ Section 4.5\]](#04_005.html#i04_80) [\[→ Section 7.6\]](#07_006.html#i07_153)

log on [\[→ Section 2.4\]](#02_004.html#i02_153)

overview [\[→ Section 2.4\]](#02_004.html#i02_156)

settings [\[→ Section 2.4\]](#02_004.html#i02_176)

use [\[→ Section 2.2\]](#02_002.html#i02_90) [\[→ Section 3.3\]](#03_003.html#i03_59)

Identity directory [\[→ Section 2.4\]](#02_004.html#i02_134)

Identity federation [\[→ Section 2.2\]](#02_002.html#i02_74) [\[→ Section 2.2\]](#02_002.html#i02_104) [\[→ Section 2.4\]](#02_004.html#i02_138) [\[→ Section 3.3\]](#03_003.html#i03_76)

Identity providers [\[→ Section 2.2\]](#02_002.html#i02_58) [\[→ Section 2.2\]](#02_002.html#i02_67) [\[→ Section 2.4\]](#02_004.html#i02_161) [\[→ Section 3.1\]](#03_001.html#i03_12) [\[→ Section 3.3\]](#03_003.html#i03_48) [\[→ Section 4.2\]](#04_002.html#i04_19)

add [\[→ Section 3.3\]](#03_003.html#i03_84) [\[→ Section 3.6\]](#03_006.html#i03_207)

application [\[→ Section 2.2\]](#02_002.html#i02_60) [\[→ Section 3.3\]](#03_003.html#i03_69) [\[→ Section 3.3\]](#03_003.html#i03_74)

Cloud Foundry [\[→ Section 2.2\]](#02_002.html#i02_92)

corporate [\[→ Section 2.2\]](#02_002.html#i02_77) [\[→ Section 2.4\]](#02_004.html#i02_162) [\[→ Section 7.6\]](#07_006.html#i07_149)

custom [\[→ Section 2.2\]](#02_002.html#i02_64) [\[→ Section 2.2\]](#02_002.html#i02_70)

default [\[→ Section 3.6\]](#03_006.html#i03_214)

external [\[→ Section 2.2\]](#02_002.html#i02_96) [\[→ Section 3.6\]](#03_006.html#i03_188) [\[→ Section 4.3\]](#04_003.html#i04_37) [\[→ Section 4.4\]](#04_004.html#i04_68) [\[→ Section 4.5\]](#04_005.html#i04_82) [\[→ Section 4.6\]](#04_006.html#i04_120)

group mapping [\[→ Section 7.1\]](#07_001.html#i07_35)

Microsoft Azure AD [\[→ Section 3.6\]](#03_006.html#i03_161) [\[→ Section 3.6\]](#03_006.html#i03_187) [\[→ Section 3.6\]](#03_006.html#i03_205) [\[→ Section 4.6\]](#04_006.html#i04_121)

Neo [\[→ Section 2.2\]](#02_002.html#i02_80)

platform [\[→ Section 2.2\]](#02_002.html#i02_59) [\[→ Section 2.2\]](#02_002.html#i02_84) [\[→ Section 3.3\]](#03_003.html#i03_55) [\[→ Section 3.3\]](#03_003.html#i03_67) [\[→ Section 3.6\]](#03_006.html#i03_165) [\[→ Section 4.3\]](#04_003.html#i04_30)

SAML [\[→ Section 3.6\]](#03_006.html#i03_179)

SAML 2.0 [\[→ Section 3.3\]](#03_003.html#i03_81)

social [\[→ Section 2.4\]](#02_004.html#i02_190)

test [\[→ Section 3.6\]](#03_006.html#i03_216)

Identity Provisioning service [\[→ Section 2.4\]](#02_004.html#i02_200) [\[→ Section 4.4\]](#04_004.html#i04_73)

transformations [\[→ Section 2.4\]](#02_004.html#i02_209)

Identity Provisioning tenant [\[→ Section 2.4\]](#02_004.html#i02_205)

Industry cloud [\[→ Section 1.1\]](#01_001.html#i01_25)

Infrastructure as a service (IaaS) [\[→ Section 1.2\]](#01_002.html#i01_102)

Integration Content API

test [\[→ Section 6.3\]](#06_003.html#i06_21)

Integration developer [\[→ Section 7.2\]](#07_002.html#i07_92)

Integration flows (iFlows) [\[→ Section 1.1\]](#01_001.html#i01_54) [\[→ Section 7.2\]](#07_002.html#i07_77) [\[→ Section 7.2\]](#07_002.html#i07_101)

Integration flows mappers (IFLMAPs) [\[→ Section 7.2\]](#07_002.html#i07_53)

Integration package [\[→ Section 7.2\]](#07_002.html#i07_103)

Integrations [\[→ Section 1.1\]](#01_001.html#i01_42)

Intelligent enterprise [\[→ Section 1.1\]](#01_001.html#i01_19)

Intelligent suite [\[→ Section 1.1\]](#01_001.html#i01_24)

Intelligent technologies [\[→ Section 1.1\]](#01_001.html#i01_27)

Interface user [\[→ Section 7.2\]](#07_002.html#i07_87) [\[→ Section 7.2\]](#07_002.html#i07_97)

Internal host [\[→ Section 5.4\]](#05_004.html#i05_80) [\[→ Section 5.7\]](#05_007.html#i05_131)

[J ⇑](#index.html#index)

Java [\[→ Section 3.4\]](#03_004.html#i03_104) [\[→ Section 3.4\]](#03_004.html#i03_122)

Java Connector (JCo) [\[→ Section 5.5\]](#05_005.html#i05_117)

Java Database Connectivity (JDBC) [\[→ Section 1.1\]](#01_001.html#i01_47) [\[→ Section 6.1\]](#06_001.html#i06_07)

Java development kit (JDK) [\[→ Section 2.1\]](#02_001.html#i02_40) [\[→ Section 5.2\]](#05_002.html#i05_17)

Java Message Service (JMS) [\[→ Section 1.1\]](#01_001.html#i01_49)

Java Virtual Machine (JVM) [\[→ Section 5.2\]](#05_002.html#i05_18)

JavaScript Object Notation (JSON) [\[→ Section 2.4\]](#02_004.html#i02_211) [\[→ Section 4.6\]](#04_006.html#i04_114) [\[→ Section 6.3\]](#06_003.html#i06_40) [\[→ Section 7.2\]](#07_002.html#i07_82)

JSON Web Token (JWT) [\[→ Section 2.3\]](#02_003.html#i02_132)

[K ⇑](#index.html#index)

Key length [\[→ Section 2.1\]](#02_001.html#i02_13)

KeyStore Explorer [\[→ Section 2.1\]](#02_001.html#i02_47)

Kyma [\[→ Section 1.1\]](#01_001.html#i01_17) [\[→ Section 1.2\]](#01_002.html#i01_62)

[L ⇑](#index.html#index)

Launchpad website [\[→ Section 4.6\]](#04_006.html#i04_100)

Licensing [\[→ Section 1.1\]](#01_001.html#i01_29) [\[→ Section 2.4\]](#02_004.html#i02_142) [\[→ Section 2.4\]](#02_004.html#i02_204) [\[→ Section 2.4\]](#02_004.html#i02_215) [\[→ Section 4.4\]](#04_004.html#i04_74) [\[→ Section 4.5\]](#04_005.html#i04_81)

Lightweight Directory Access Protocol (LDAP) [\[→ Section 2.2\]](#02_002.html#i02_99) [\[→ Section 5.1\]](#05_001.html#i05_02)

authentication [\[→ Section 5.3\]](#05_003.html#i05_58) [\[→ Section 5.3\]](#05_003.html#i05_61) [\[→ Section 5.7\]](#05_007.html#i05_142)

destination [\[→ Section 2.1\]](#02_001.html#i02_33)

Lightweight Directory Access Protocol over SSL (LDAPS) [\[→ Section 5.3\]](#05_003.html#i05_59)

Load Balancer [\[→ Section 7.2\]](#07_002.html#i07_99)

Local service providers [\[→ Section 3.3\]](#03_003.html#i03_49)

configuration types [\[→ Section 3.3\]](#03_003.html#i03_52)

Logging [\[→ Section 5.4\]](#05_004.html#i05_73) [\[→ Section 7.2\]](#07_002.html#i07_57)

[M ⇑](#index.html#index)

Mail [\[→ Section 2.1\]](#02_001.html#i02_34)

servers [\[→ Section 2.4\]](#02_004.html#i02_179)

Manifest [\[→ Section 4.6\]](#04_006.html#i04_113)

Master shadow logic [\[→ Section 5.2\]](#05_002.html#i05_40)

Member management [\[→ Section 3.6\]](#03_006.html#i03_176)

Members [\[→ Section 3.2\]](#03_002.html#i03_26)

add [\[→ Section 3.2\]](#03_002.html#i03_29)

assign roles [\[→ Section 3.4\]](#03_004.html#i03_113)

Microservice [\[→ Section 7.2\]](#07_002.html#i07_66)

Microsoft Active Directory [\[→ Section 4.4\]](#04_004.html#i04_70)

Microsoft Authenticator [\[→ Section 3.6\]](#03_006.html#i03_183)

Microsoft Azure [\[→ Section 1.1\]](#01_001.html#i01_10) [\[→ Section 1.2\]](#01_002.html#i01_58)

Microsoft Azure Active Directory [\[→ Section 2.2\]](#02_002.html#i02_66) [\[→ Section 3.1\]](#03_001.html#i03_02) [\[→ Section 3.6\]](#03_006.html#i03_160) [\[→ Section 3.6\]](#03_006.html#i03_186) [\[→ Section 4.1\]](#04_001.html#i04_02) [\[→ Section 4.4\]](#04_004.html#i04_71)

add as identity provider [\[→ Section 4.6\]](#04_006.html#i04_118)

add users [\[→ Section 3.6\]](#03_006.html#i03_204)

app registrations [\[→ Section 4.6\]](#04_006.html#i04_112)

configuration [\[→ Section 3.6\]](#03_006.html#i03_191)

create application [\[→ Section 4.6\]](#04_006.html#i04_111)

create applications [\[→ Section 3.6\]](#03_006.html#i03_192)

groups [\[→ Section 4.6\]](#04_006.html#i04_117)

SSO [\[→ Section 3.6\]](#03_006.html#i03_195) [\[→ Section 4.6\]](#04_006.html#i04_115)

test [\[→ Section 3.6\]](#03_006.html#i03_218)

two-factor authentication [\[→ Section 4.6\]](#04_006.html#i04_107) [\[→ Section 4.6\]](#04_006.html#i04_124)

Microsoft Management Console [\[→ Section 4.4\]](#04_004.html#i04_72)

Monitoring [\[→ Section 5.2\]](#05_002.html#i05_45)

Multifactor authentication (MFA) [\[→ Section 2.2\]](#02_002.html#i02_57)

Multitarget applications (MTAs) [\[→ Section 1.2\]](#01_002.html#i01_79) [\[→ Section 4.1\]](#04_001.html#i04_10)

[N ⇑](#index.html#index)

Neo [\[→ Section 1.1\]](#01_001.html#i01_13) [\[→ Section 1.2\]](#01_002.html#i01_56) [\[→ Section 1.2\]](#01_002.html#i01_73) [\[→ Section 3.1\]](#03_001.html#i03_00) [\[→ Section 5.5\]](#05_005.html#i05_111) [\[→ Section 5.7\]](#05_007.html#i05_125) [\[→ Section 7.4\]](#07_004.html#i07_121)

authorization management [\[→ Section 3.4\]](#03_004.html#i03_89)

command line [\[→ Section 3.1\]](#03_001.html#i03_04)

destinations [\[→ Section 2.1\]](#02_001.html#i02_21)

identity providers [\[→ Section 2.2\]](#02_002.html#i02_82)

roles [\[→ Section 3.4\]](#03_004.html#i03_92)

trust configuration [\[→ Section 3.3\]](#03_003.html#i03_41)

user groups [\[→ Section 3.4\]](#03_004.html#i03_144)

user management [\[→ Section 3.2\]](#03_002.html#i03_18)

[O ⇑](#index.html#index)

OAuth [\[→ Section 2.2\]](#02_002.html#i02_108) [\[→ Section 2.3\]](#02_003.html#i02_115) [\[→ Section 7.2\]](#07_002.html#i07_76)

2.0 [\[→ Section 2.3\]](#02_003.html#i02_116) [\[→ Section 6.3\]](#06_003.html#i06_64)

authentication [\[→ Section 6.3\]](#06_003.html#i06_29) [\[→ Section 6.3\]](#06_003.html#i06_37) [\[→ Section 6.3\]](#06_003.html#i06_41)

password [\[→ Section 6.3\]](#06_003.html#i06_67)

roles [\[→ Section 2.3\]](#02_003.html#i02_118)

user name [\[→ Section 6.3\]](#06_003.html#i06_66)

OData [\[→ Section 7.3\]](#07_003.html#i07_110)

APIs [\[→ Section 6.3\]](#06_003.html#i06_17)

OpenID Connect [\[→ Section 2.3\]](#02_003.html#i02_126) [\[→ Section 2.4\]](#02_004.html#i02_187)

Organization manager role [\[→ Section 4.2\]](#04_002.html#i04_17)

Organizations [\[→ Section 1.3\]](#01_003.html#i01_139)

[P ⇑](#index.html#index)

Partner directory configurator [\[→ Section 7.2\]](#07_002.html#i07_94)

Passwords [\[→ Section 2.2\]](#02_002.html#i02_52)

details [\[→ Section 2.4\]](#02_004.html#i02_171)

policy [\[→ Section 2.2\]](#02_002.html#i02_54) [\[→ Section 2.4\]](#02_004.html#i02_182)

Permissions management [\[→ Section 6.3\]](#06_003.html#i06_53)

Cloud Foundry [\[→ Section 4.6\]](#04_006.html#i04_86)

Neo [\[→ Section 3.5\]](#03_005.html#i03_154)

SAP Web IDE [\[→ Section 7.1\]](#07_001.html#i07_26)

services and URIs [\[→ Section 5.4\]](#05_004.html#i05_89)

Persona [\[→ Section 7.2\]](#07_002.html#i07_89)

Platform as a service (PaaS) [\[→ Section 1.1\]](#01_001.html#i01_01)

Platform authorizations management [\[→ Section 6.3\]](#06_003.html#i06_45)

Platform identity providers [\[→ Section 2.2\]](#02_002.html#i02_61) [\[→ Section 2.2\]](#02_002.html#i02_85) [\[→ Section 3.3\]](#03_003.html#i03_56) [\[→ Section 3.3\]](#03_003.html#i03_68) [\[→ Section 4.3\]](#04_003.html#i04_31)

two-factor authentication [\[→ Section 3.6\]](#03_006.html#i03_166)

Platform roles [\[→ Section 3.4\]](#03_004.html#i03_95) [\[→ Section 3.4\]](#03_004.html#i03_97)

administration [\[→ Section 3.4\]](#03_004.html#i03_105)

assign [\[→ Section 3.4\]](#03_004.html#i03_112) [\[→ Section 3.4\]](#03_004.html#i03_114)

create [\[→ Section 3.4\]](#03_004.html#i03_107)

custom [\[→ Section 3.4\]](#03_004.html#i03_111)

predefined [\[→ Section 3.4\]](#03_004.html#i03_98)

Plug-in [\[→ Section 4.1\]](#04_001.html#i04_12)

PostgreSQL [\[→ Section 4.1\]](#04_001.html#i04_11)

Prepackaged content [\[→ Section 1.1\]](#01_001.html#i01_51)

Principal attributes [\[→ Section 3.6\]](#03_006.html#i03_210)

Principal propagation [\[→ Section 3.3\]](#03_003.html#i03_53) [\[→ Section 5.4\]](#05_004.html#i05_78) [\[→ Section 5.4\]](#05_004.html#i05_99)

Privacy-Enhanced Mail (PEM) [\[→ Section 5.2\]](#05_002.html#i05_30) [\[→ Section 6.5\]](#06_005.html#i06_82)

Provider accounts [\[→ Section 3.4\]](#03_004.html#i03_118) [\[→ Section 7.2\]](#07_002.html#i07_49)

Provider subaccounts [\[→ Section 2.1\]](#02_001.html#i02_24)

Proxy server [\[→ Section 3.1\]](#03_001.html#i03_10)

Proxy systems [\[→ Section 2.4\]](#02_004.html#i02_203)

Proxy type [\[→ Section 5.5\]](#05_005.html#i05_114)

[Q ⇑](#index.html#index)

Quotas [\[→ Section 1.3\]](#01_003.html#i01_121)

assign to spaces [\[→ Section 1.3\]](#01_003.html#i01_147)

plan [\[→ Section 1.3\]](#01_003.html#i01_148)

[R ⇑](#index.html#index)

Read jobs [\[→ Section 2.4\]](#02_004.html#i02_213)

RegionHost [\[→ Section 6.3\]](#06_003.html#i06_31)

Remote function call (RFC) [\[→ Section 2.1\]](#02_001.html#i02_32) [\[→ Section 5.1\]](#05_001.html#i05_05)

connections [\[→ Section 5.4\]](#05_004.html#i05_88) [\[→ Section 5.5\]](#05_005.html#i05_116)

destination [\[→ Section 5.7\]](#05_007.html#i05_141)

enable [\[→ Section 5.7\]](#05_007.html#i05_139)

Reporting [\[→ Section 4.4\]](#04_004.html#i04_75)

Representational State Transfer (REST) [\[→ Section 1.1\]](#01_001.html#i01_48) [\[→ Section 2.3\]](#02_003.html#i02_127) [\[→ Section 6.3\]](#06_003.html#i06_16) [\[→ Section 7.3\]](#07_003.html#i07_108)

Request for comments [\[→ Section 2.3\]](#02_003.html#i02_117)

Resource [\[→ Section 5.7\]](#05_007.html#i05_140)

server [\[→ Section 2.3\]](#02_003.html#i02_119)

Resync jobs [\[→ Section 2.4\]](#02_004.html#i02_214)

Risk-based authentication [\[→ Section 2.4\]](#02_004.html#i02_139) [\[→ Section 2.4\]](#02_004.html#i02_192) [\[→ Section 3.6\]](#03_006.html#i03_172)

Robotic process automation (RPA) [\[→ Section 1.1\]](#01_001.html#i01_33)

Role collections [\[→ Section 1.3\]](#01_003.html#i01_128) [\[→ Section 4.4\]](#04_004.html#i04_51) [\[→ Section 4.4\]](#04_004.html#i04_55) [\[→ Section 4.6\]](#04_006.html#i04_95) [\[→ Section 7.2\]](#07_002.html#i07_96)

administration [\[→ Section 4.6\]](#04_006.html#i04_96)

assign [\[→ Section 7.1\]](#07_001.html#i07_44)

launchpad [\[→ Section 4.6\]](#04_006.html#i04_103)

mapping [\[→ Section 4.4\]](#04_004.html#i04_69)

SAP API Management [\[→ Section 7.3\]](#07_003.html#i07_113)

SAP BTP, Cloud Foundry environment [\[→ Section 7.2\]](#07_002.html#i07_68)

SAP Business Application Studio [\[→ Section 7.1\]](#07_001.html#i07_43)

Role templates [\[→ Section 4.4\]](#04_004.html#i04_48)

instances [\[→ Section 4.4\]](#04_004.html#i04_54)

[S ⇑](#index.html#index)

SAP API Business Hub [\[→ Section 1.1\]](#01_001.html#i01_52) [\[→ Section 6.3\]](#06_003.html#i06_19)

SAP API Management [\[→ Section 1.1\]](#01_001.html#i01_43) [\[→ Section 1.2\]](#01_002.html#i01_99) [\[→ Section 7.1\]](#07_001.html#i07_11) [\[→ Section 7.3\]](#07_003.html#i07_106)

security policies [\[→ Section 7.3\]](#07_003.html#i07_115)

SAP Application Extension Methodology [\[→ Section 1.1\]](#01_001.html#i01_40)

SAP Audit Log Management service [\[→ Section 6.3\]](#06_003.html#i06_38)

SAP Authentication 365 [\[→ Section 2.4\]](#02_004.html#i02_197)

SAP Authenticator [\[→ Section 3.6\]](#03_006.html#i03_184)

SAP Authorization and Trust Management service [\[→ Section 6.3\]](#06_003.html#i06_50)

SAP BTP CLI [\[→ Section 6.2\]](#06_002.html#i06_11) [\[→ Section 6.5\]](#06_005.html#i06_84)

download [\[→ Section 6.2\]](#06_002.html#i06_13)

prerequisite [\[→ Section 6.2\]](#06_002.html#i06_14)

SAP BTP cockpit [\[→ Section 1.2\]](#01_002.html#i01_78) [\[→ Section 2.2\]](#02_002.html#i02_81) [\[→ Section 2.4\]](#02_004.html#i02_154) [\[→ Section 3.2\]](#03_002.html#i03_27) [\[→ Section 3.3\]](#03_003.html#i03_46) [\[→ Section 3.4\]](#03_004.html#i03_106) [\[→ Section 4.1\]](#04_001.html#i04_04) [\[→ Section 4.1\]](#04_001.html#i04_08) [\[→ Section 5.4\]](#05_004.html#i05_95) [\[→ Section 6.5\]](#06_005.html#i06_89)

roles [\[→ Section 4.4\]](#04_004.html#i04_47)

SAP BTP software development kit (SDK) [\[→ Section 3.1\]](#03_001.html#i03_08) [\[→ Section 6.1\]](#06_001.html#i06_04)

SAP BTP, ABAP environment [\[→ Section 7.1\]](#07_001.html#i07_15) [\[→ Section 7.5\]](#07_005.html#i07_136)

access to external systems [\[→ Section 7.5\]](#07_005.html#i07_146)

user administration [\[→ Section 7.5\]](#07_005.html#i07_140)

SAP BTP, Cloud Foundry environment [\[→ Section 1.1\]](#01_001.html#i01_14) [\[→ Section 1.2\]](#01_002.html#i01_66) [\[→ Section 1.2\]](#01_002.html#i01_87) [\[→ Section 4.1\]](#04_001.html#i04_01) [\[→ Section 5.4\]](#05_004.html#i05_104)

audit log retrieval [\[→ Section 6.3\]](#06_003.html#i06_35)

authorization management [\[→ Section 4.4\]](#04_004.html#i04_42) [\[→ Section 6.3\]](#06_003.html#i06_59)

CLI [\[→ Section 4.1\]](#04_001.html#i04_05)

Cloud Integration capability [\[→ Section 7.2\]](#07_002.html#i07_65)

connect to SAP S/4HANA [\[→ Section 5.7\]](#05_007.html#i05_136)

create destinations [\[→ Section 5.5\]](#05_005.html#i05_122)

create subaccounts [\[→ Section 1.3\]](#01_003.html#i01_137)

destinations [\[→ Section 2.1\]](#02_001.html#i02_37)

development environment [\[→ Section 7.1\]](#07_001.html#i07_41)

disable [\[→ Section 1.3\]](#01_003.html#i01_143)

enable [\[→ Section 1.3\]](#01_003.html#i01_141)

identity providers [\[→ Section 2.2\]](#02_002.html#i02_94)

OAuth [\[→ Section 2.3\]](#02_003.html#i02_129)

role collections [\[→ Section 4.4\]](#04_004.html#i04_58)

roles [\[→ Section 4.4\]](#04_004.html#i04_46)

security and permissions [\[→ Section 4.5\]](#04_005.html#i04_78)

selection considerations [\[→ Section 1.2\]](#01_002.html#i01_105)

trust configuration [\[→ Section 4.3\]](#04_003.html#i04_24)

two-factor authentication [\[→ Section 4.6\]](#04_006.html#i04_109)

user administration [\[→ Section 7.5\]](#07_005.html#i07_142)

user and permission administration [\[→ Section 4.6\]](#04_006.html#i04_85)

user management [\[→ Section 4.2\]](#04_002.html#i04_16) [\[→ Section 6.3\]](#06_003.html#i06_48)

SAP BTP, Kyma environment [\[→ Section 1.1\]](#01_001.html#i01_16) [\[→ Section 1.2\]](#01_002.html#i01_61)

SAP BTP, Neo environment [\[→ Section 1.1\]](#01_001.html#i01_12) [\[→ Section 1.2\]](#01_002.html#i01_67) [\[→ Section 1.2\]](#01_002.html#i01_74) [\[→ Section 3.1\]](#03_001.html#i03_01)

audit log retrieval [\[→ Section 6.3\]](#06_003.html#i06_26)

authorization granting [\[→ Section 2.3\]](#02_003.html#i02_125)

authorization management [\[→ Section 3.4\]](#03_004.html#i03_88) [\[→ Section 6.3\]](#06_003.html#i06_57)

Cloud Integration capability [\[→ Section 7.2\]](#07_002.html#i07_48)

command line [\[→ Section 3.1\]](#03_001.html#i03_06) [\[→ Section 6.1\]](#06_001.html#i06_01) [\[→ Section 6.5\]](#06_005.html#i06_80)

connect Git server [\[→ Section 5.7\]](#05_007.html#i05_127)

create destinations [\[→ Section 5.5\]](#05_005.html#i05_113)

destinations [\[→ Section 2.1\]](#02_001.html#i02_22)

development environments [\[→ Section 7.1\]](#07_001.html#i07_17)

identity providers [\[→ Section 2.2\]](#02_002.html#i02_83)

real-world examples [\[→ Section 3.6\]](#03_006.html#i03_157)

regions and hosts [\[→ Section 3.1\]](#03_001.html#i03_15)

roles [\[→ Section 3.4\]](#03_004.html#i03_93)

SAP Cloud Portal service [\[→ Section 7.4\]](#07_004.html#i07_122)

security and permissions checklist [\[→ Section 3.5\]](#03_005.html#i03_155)

selection considerations [\[→ Section 1.2\]](#01_002.html#i01_104)

trust configuration [\[→ Section 3.3\]](#03_003.html#i03_40)

user groups [\[→ Section 3.4\]](#03_004.html#i03_145)

user management [\[→ Section 3.2\]](#03_002.html#i03_19) [\[→ Section 6.3\]](#06_003.html#i06_44)

SAP Business Application Studio [\[→ Section 1.2\]](#01_002.html#i01_94) [\[→ Section 5.1\]](#05_001.html#i05_09) [\[→ Section 7.1\]](#07_001.html#i07_03) [\[→ Section 7.1\]](#07_001.html#i07_18) [\[→ Section 7.1\]](#07_001.html#i07_37)

roles [\[→ Section 4.4\]](#04_004.html#i04_59) [\[→ Section 7.1\]](#07_001.html#i07_42)

SAP Business Network [\[→ Section 1.1\]](#01_001.html#i01_20)

SAP Business Network for Asset Intelligence [\[→ Section 1.1\]](#01_001.html#i01_23)

SAP Business Network for Logistics [\[→ Section 1.1\]](#01_001.html#i01_22)

SAP Business Network for Procurement [\[→ Section 1.1\]](#01_001.html#i01_21)

SAP Business Technology Platform (SAP BTP) [\[→ Section 1.1\]](#01_001.html#i01_00) [\[→ Section 2.1\]](#02_001.html#i02_00) [\[→ Section 5.1\]](#05_001.html#i05_04)

architecture [\[→ Section 1.3\]](#01_003.html#i01_113)

environments [\[→ Section 1.2\]](#01_002.html#i01_55) [\[→ Section 1.2\]](#01_002.html#i01_103)

positioning [\[→ Section 1.1\]](#01_001.html#i01_18)

service areas [\[→ Section 1.1\]](#01_001.html#i01_26)

SAP Business Warehouse (SAP BW) [\[→ Section 5.1\]](#05_001.html#i05_10)

SAP Cloud Identity Access Governance [\[→ Section 2.5\]](#02_005.html#i02_217)

SAP Cloud Identity Services [\[→ Section 2.4\]](#02_004.html#i02_133) [\[→ Section 2.5\]](#02_005.html#i02_221)

SAP Cloud Management service for SAP BTP [\[→ Section 6.3\]](#06_003.html#i06_61)

SAP Cloud Platform [\[→ Section 1.1\]](#01_001.html#i01_02) [\[→ Section 7.1\]](#07_001.html#i07_07)

SAP Cloud Portal service [\[→ Section 1.2\]](#01_002.html#i01_83) [\[→ Section 2.1\]](#02_001.html#i02_29) [\[→ Section 3.4\]](#03_004.html#i03_126) [\[→ Section 7.4\]](#07_004.html#i07_118)

roles [\[→ Section 7.4\]](#07_004.html#i07_123)

websites [\[→ Section 7.4\]](#07_004.html#i07_124)

SAP Connectivity service [\[→ Section 5.4\]](#05_004.html#i05_100) [\[→ Section 7.1\]](#07_001.html#i07_36)

new instance [\[→ Section 5.4\]](#05_004.html#i05_103)

SAP Custom Domain service [\[→ Section 1.2\]](#01_002.html#i01_72)

SAP Destination service [\[→ Section 2.1\]](#02_001.html#i02_16) [\[→ Section 5.4\]](#05_004.html#i05_102) [\[→ Section 5.5\]](#05_005.html#i05_108) [\[→ Section 7.1\]](#07_001.html#i07_40) [\[→ Section 7.5\]](#07_005.html#i07_147)

SAP Development Tools [\[→ Section 6.1\]](#06_001.html#i06_03)

SAP Discovery Center [\[→ Section 1.1\]](#01_001.html#i01_28) [\[→ Section 1.2\]](#01_002.html#i01_71) [\[→ Section 1.2\]](#01_002.html#i01_88) [\[→ Section 1.3\]](#01_003.html#i01_138)

SAP Enterprise Portal [\[→ Section 4.6\]](#04_006.html#i04_91)

SAP ERP [\[→ Section 4.4\]](#04_004.html#i04_64)

SAP Event Mesh [\[→ Section 1.1\]](#01_001.html#i01_36)

SAP Extension Suite [\[→ Section 1.1\]](#01_001.html#i01_04) [\[→ Section 1.1\]](#01_001.html#i01_30)

SAP Fiori apps [\[→ Section 2.4\]](#02_004.html#i02_152) [\[→ Section 7.4\]](#07_004.html#i07_129)

roles [\[→ Section 7.4\]](#07_004.html#i07_130)

SAP Fiori launchpad [\[→ Section 1.2\]](#01_002.html#i01_98) [\[→ Section 2.4\]](#02_004.html#i02_151) [\[→ Section 4.4\]](#04_004.html#i04_50) [\[→ Section 4.6\]](#04_006.html#i04_90) [\[→ Section 4.6\]](#04_006.html#i04_104) [\[→ Section 7.4\]](#07_004.html#i07_120)

components [\[→ Section 7.4\]](#07_004.html#i07_127) [\[→ Section 7.4\]](#07_004.html#i07_128)

full access [\[→ Section 7.5\]](#07_005.html#i07_141)

roles [\[→ Section 7.4\]](#07_004.html#i07_131)

SAP Cloud Portal service [\[→ Section 7.4\]](#07_004.html#i07_126)

SAP Git service [\[→ Section 7.1\]](#07_001.html#i07_23)

SAP HANA [\[→ Section 1.2\]](#01_002.html#i01_65) [\[→ Section 1.2\]](#01_002.html#i01_90)

SAP HANA extended application services (SAP HANA XS) [\[→ Section 1.2\]](#01_002.html#i01_75) [\[→ Section 5.4\]](#05_004.html#i05_94)

SAP HANA extended application services, advanced model (SAP HANA XSA) [\[→ Section 1.2\]](#01_002.html#i01_64) [\[→ Section 1.2\]](#01_002.html#i01_89)

SAP ID service [\[→ Section 2.2\]](#02_002.html#i02_68) [\[→ Section 2.2\]](#02_002.html#i02_75) [\[→ Section 2.2\]](#02_002.html#i02_89) [\[→ Section 2.2\]](#02_002.html#i02_95) [\[→ Section 3.2\]](#03_002.html#i03_23) [\[→ Section 3.2\]](#03_002.html#i03_30) [\[→ Section 3.2\]](#03_002.html#i03_35) [\[→ Section 3.3\]](#03_003.html#i03_58) [\[→ Section 4.2\]](#04_002.html#i04_20) [\[→ Section 4.3\]](#04_003.html#i04_28) [\[→ Section 7.2\]](#07_002.html#i07_88)

disadvantages [\[→ Section 3.2\]](#03_002.html#i03_31)

set up [\[→ Section 4.3\]](#04_003.html#i04_27)

SAP Integration Suite [\[→ Section 1.1\]](#01_001.html#i01_03) [\[→ Section 1.1\]](#01_001.html#i01_41) [\[→ Section 5.4\]](#05_004.html#i05_101) [\[→ Section 7.1\]](#07_001.html#i07_09) [\[→ Section 7.2\]](#07_002.html#i07_46) [\[→ Section 7.2\]](#07_002.html#i07_47) [\[→ Section 7.2\]](#07_002.html#i07_69) [\[→ Section 7.3\]](#07_003.html#i07_104)

roles and authorizations [\[→ Section 7.3\]](#07_003.html#i07_111)

SAP Intelligent Robotic Process Automation (SAP Intelligent RPA) [\[→ Section 1.1\]](#01_001.html#i01_34)

SAP Internet of Things [\[→ Section 1.2\]](#01_002.html#i01_101)

SAP Launchpad service [\[→ Section 1.2\]](#01_002.html#i01_84) [\[→ Section 1.2\]](#01_002.html#i01_97) [\[→ Section 4.4\]](#04_004.html#i04_49) [\[→ Section 4.6\]](#04_006.html#i04_87) [\[→ Section 4.6\]](#04_006.html#i04_94) [\[→ Section 7.1\]](#07_001.html#i07_13) [\[→ Section 7.4\]](#07_004.html#i07_119) [\[→ Section 7.4\]](#07_004.html#i07_133)

documentation [\[→ Section 4.6\]](#04_006.html#i04_106)

roles [\[→ Section 4.6\]](#04_006.html#i04_102)

set up [\[→ Section 4.6\]](#04_006.html#i04_92)

site directory [\[→ Section 4.6\]](#04_006.html#i04_97)

website [\[→ Section 4.6\]](#04_006.html#i04_99)

website dashboard [\[→ Section 7.4\]](#07_004.html#i07_125)

SAP Mobile Services [\[→ Section 1.2\]](#01_002.html#i01_82) [\[→ Section 1.2\]](#01_002.html#i01_96) [\[→ Section 2.1\]](#02_001.html#i02_25)

SAP Passport [\[→ Section 2.2\]](#02_002.html#i02_56)

SAP Platform Identity Provider service [\[→ Section 2.2\]](#02_002.html#i02_87) [\[→ Section 2.4\]](#02_004.html#i02_186) [\[→ Section 3.6\]](#03_006.html#i03_168)

SAP Process Integration runtime [\[→ Section 7.2\]](#07_002.html#i07_81) [\[→ Section 7.2\]](#07_002.html#i07_84)

SAP Process Orchestration [\[→ Section 7.1\]](#07_001.html#i07_06)

SAP S/4HANA [\[→ Section 4.4\]](#04_004.html#i04_65) [\[→ Section 5.7\]](#05_007.html#i05_135)

SAP Solution Manager [\[→ Section 5.2\]](#05_002.html#i05_55)

SAP Support Portal [\[→ Section 2.4\]](#02_004.html#i02_149) [\[→ Section 3.2\]](#03_002.html#i03_24) [\[→ Section 5.2\]](#05_002.html#i05_19)

SAP Translation Hub [\[→ Section 1.2\]](#01_002.html#i01_85)

SAP Web IDE [\[→ Section 1.2\]](#01_002.html#i01_80) [\[→ Section 3.1\]](#03_001.html#i03_03) [\[→ Section 3.6\]](#03_006.html#i03_163) [\[→ Section 3.6\]](#03_006.html#i03_185) [\[→ Section 3.6\]](#03_006.html#i03_200) [\[→ Section 3.6\]](#03_006.html#i03_212) [\[→ Section 3.6\]](#03_006.html#i03_217) [\[→ Section 5.1\]](#05_001.html#i05_08) [\[→ Section 5.7\]](#05_007.html#i05_128) [\[→ Section 7.1\]](#07_001.html#i07_01)

connection [\[→ Section 5.5\]](#05_005.html#i05_119)

create project [\[→ Section 5.7\]](#05_007.html#i05_133)

full stack [\[→ Section 7.1\]](#07_001.html#i07_02) [\[→ Section 7.1\]](#07_001.html#i07_16)

roles [\[→ Section 3.6\]](#03_006.html#i03_215) [\[→ Section 7.1\]](#07_001.html#i07_25)

SAP Workflow Management [\[→ Section 2.5\]](#02_005.html#i02_218) [\[→ Section 3.4\]](#03_004.html#i03_132) [\[→ Section 3.4\]](#03_004.html#i03_139) [\[→ Section 3.4\]](#03_004.html#i03_152)

SAPUI5 [\[→ Section 1.2\]](#01_002.html#i01_76) [\[→ Section 4.6\]](#04_006.html#i04_89)

Scopes [\[→ Section 2.3\]](#02_003.html#i02_130) [\[→ Section 3.4\]](#03_004.html#i03_96)

categories [\[→ Section 3.4\]](#03_004.html#i03_109)

Secure communication [\[→ Section 2.1\]](#02_001.html#i02_01)

Secure File Transfer Protocol (SFTP) [\[→ Section 1.1\]](#01_001.html#i01_50)

Secure Sockets Layer (SSL) [\[→ Section 2.1\]](#02_001.html#i02_04) [\[→ Section 2.1\]](#02_001.html#i02_15) [\[→ Section 5.2\]](#05_002.html#i05_20) [\[→ Section 6.5\]](#06_005.html#i06_77)

handshake error [\[→ Section 2.1\]](#02_001.html#i02_44)

Security [\[→ Section 2.1\]](#02_001.html#i02_03)

general checklist [\[→ Section 2.6\]](#02_006.html#i02_222)

Security Assertion Markup Language (SAML) [\[→ Section 2.3\]](#02_003.html#i02_112) [\[→ Section 3.3\]](#03_003.html#i03_44) [\[→ Section 3.3\]](#03_003.html#i03_77) [\[→ Section 4.3\]](#04_003.html#i04_34) [\[→ Section 5.5\]](#05_005.html#i05_115)

assertion [\[→ Section 2.3\]](#02_003.html#i02_114) [\[→ Section 3.6\]](#03_006.html#i03_199) [\[→ Section 7.1\]](#07_001.html#i07_34)

attributes [\[→ Section 3.6\]](#03_006.html#i03_197)

identity providers [\[→ Section 3.3\]](#03_003.html#i03_80)

signing certificate [\[→ Section 3.6\]](#03_006.html#i03_203)

tokens [\[→ Section 2.3\]](#02_003.html#i02_113)

Security policies [\[→ Section 7.3\]](#07_003.html#i07_116)

Self-registration [\[→ Section 2.4\]](#02_004.html#i02_147)

Self-signed certificate [\[→ Section 5.2\]](#05_002.html#i05_23)

Serverless architectures [\[→ Section 1.1\]](#01_001.html#i01_39)

Service assignments [\[→ Section 1.3\]](#01_003.html#i01_122)

Service channel [\[→ Section 6.1\]](#06_001.html#i06_08)

Service instance [\[→ Section 7.2\]](#07_002.html#i07_79)

Service Key [\[→ Section 7.2\]](#07_002.html#i07_74)

Service key [\[→ Section 6.3\]](#06_003.html#i06_39) [\[→ Section 6.3\]](#06_003.html#i06_52) [\[→ Section 6.3\]](#06_003.html#i06_65) [\[→ Section 7.2\]](#07_002.html#i07_80)

Service plans [\[→ Section 6.3\]](#06_003.html#i06_51)

Service providers [\[→ Section 2.4\]](#02_004.html#i02_184) [\[→ Section 3.3\]](#03_003.html#i03_47)

advanced configuration [\[→ Section 3.3\]](#03_003.html#i03_73)

configuration types [\[→ Section 3.3\]](#03_003.html#i03_51)

create [\[→ Section 3.6\]](#03_006.html#i03_193)

download metadata [\[→ Section 3.6\]](#03_006.html#i03_202)

metadata [\[→ Section 3.3\]](#03_003.html#i03_82)

set up [\[→ Section 3.3\]](#03_003.html#i03_50)

upload metadata [\[→ Section 3.6\]](#03_006.html#i03_196)

Services [\[→ Section 1.2\]](#01_002.html#i01_70) [\[→ Section 1.2\]](#01_002.html#i01_107) [\[→ Section 2.2\]](#02_002.html#i02_88) [\[→ Section 3.4\]](#03_004.html#i03_120) [\[→ Section 3.4\]](#03_004.html#i03_141)

configuration [\[→ Section 3.4\]](#03_004.html#i03_134)

roles [\[→ Section 3.4\]](#03_004.html#i03_135)

Session timeouts [\[→ Section 2.4\]](#02_004.html#i02_178)

Shadow instance [\[→ Section 5.2\]](#05_002.html#i05_41)

Shadow users [\[→ Section 4.3\]](#04_003.html#i04_29) [\[→ Section 4.3\]](#04_003.html#i04_40)

Signature algorithm [\[→ Section 3.6\]](#03_006.html#i03_209)

Simple Object Access Protocol (SOAP) [\[→ Section 1.1\]](#01_001.html#i01_46) [\[→ Section 6.3\]](#06_003.html#i06_20) [\[→ Section 7.3\]](#07_003.html#i07_109)

Single sign-on (SSO) [\[→ Section 2.2\]](#02_002.html#i02_69) [\[→ Section 2.4\]](#02_004.html#i02_136) [\[→ Section 3.3\]](#03_003.html#i03_54) [\[→ Section 3.6\]](#03_006.html#i03_194)

cookies [\[→ Section 5.4\]](#05_004.html#i05_92)

Site directory [\[→ Section 4.6\]](#04_006.html#i04_98)

Social identity providers [\[→ Section 2.4\]](#02_004.html#i02_191)

Social sign-on [\[→ Section 2.4\]](#02_004.html#i02_146) [\[→ Section 2.4\]](#02_004.html#i02_189)

Software as a service (SaaS) [\[→ Section 1.1\]](#01_001.html#i01_05)

Software development kit (SDK) [\[→ Section 3.1\]](#03_001.html#i03_07)

Source systems [\[→ Section 2.4\]](#02_004.html#i02_201)

create [\[→ Section 2.4\]](#02_004.html#i02_206)

provisioning [\[→ Section 2.4\]](#02_004.html#i02_212)

Space manager [\[→ Section 4.2\]](#04_002.html#i04_18)

Spaces [\[→ Section 1.3\]](#01_003.html#i01_145)

best practices [\[→ Section 1.3\]](#01_003.html#i01_149)

create [\[→ Section 1.3\]](#01_003.html#i01_146)

SSL certificate [\[→ Section 5.2\]](#05_002.html#i05_27)

import [\[→ Section 5.2\]](#05_002.html#i05_29)

SubAccountId [\[→ Section 6.3\]](#06_003.html#i06_30)

Subaccounts [\[→ Section 1.3\]](#01_003.html#i01_114) [\[→ Section 1.3\]](#01_003.html#i01_129) [\[→ Section 2.4\]](#02_004.html#i02_159) [\[→ Section 3.5\]](#03_005.html#i03_156) [\[→ Section 5.2\]](#05_002.html#i05_24)

access [\[→ Section 3.3\]](#03_003.html#i03_63)

add members [\[→ Section 3.2\]](#03_002.html#i03_28)

admin role [\[→ Section 4.2\]](#04_002.html#i04_22)

API [\[→ Section 5.2\]](#05_002.html#i05_52)

Cloud Foundry [\[→ Section 1.3\]](#01_003.html#i01_136)

commands [\[→ Section 6.5\]](#06_005.html#i06_91)

consumer [\[→ Section 2.1\]](#02_001.html#i02_27)

create [\[→ Section 1.3\]](#01_003.html#i01_133)

create a list [\[→ Section 6.5\]](#06_005.html#i06_85)

delete [\[→ Section 1.3\]](#01_003.html#i01_144)

feature sets [\[→ Section 1.3\]](#01_003.html#i01_130)

history [\[→ Section 3.2\]](#03_002.html#i03_33)

ID [\[→ Section 5.2\]](#05_002.html#i05_35)

overview [\[→ Section 3.2\]](#03_002.html#i03_38)

platform roles [\[→ Section 3.4\]](#03_004.html#i03_108)

provider [\[→ Section 2.1\]](#02_001.html#i02_23)

retrieve information [\[→ Section 6.3\]](#06_003.html#i06_72)

technical names [\[→ Section 3.3\]](#03_003.html#i03_66)

users [\[→ Section 3.2\]](#03_002.html#i03_21)

Subdomains [\[→ Section 1.3\]](#01_003.html#i01_134)

Subscription management [\[→ Section 3.4\]](#03_004.html#i03_121)

Subscription-based model [\[→ Section 1.3\]](#01_003.html#i01_115)

Subscriptions [\[→ Section 3.4\]](#03_004.html#i03_117) [\[→ Section 3.4\]](#03_004.html#i03_130) [\[→ Section 3.4\]](#03_004.html#i03_142)

Support user platform role [\[→ Section 3.4\]](#03_004.html#i03_102)

S-users [\[→ Section 3.2\]](#03_002.html#i03_25)

Swagger [\[→ Section 6.3\]](#06_003.html#i06_69)

Symmetric encryption [\[→ Section 2.1\]](#02_001.html#i02_11)

System developer [\[→ Section 7.2\]](#07_002.html#i07_93)

System for Cross-Domain Identity Management (SCIM) [\[→ Section 2.4\]](#02_004.html#i02_165) [\[→ Section 6.3\]](#06_003.html#i06_46)

System ID (SID) [\[→ Section 5.4\]](#05_004.html#i05_70)

System landscape optimization [\[→ Section 5.1\]](#05_001.html#i05_01)

System Logs app [\[→ Section 7.2\]](#07_002.html#i07_60)

[T ⇑](#index.html#index)

Talking user accounts [\[→ Section 5.3\]](#05_003.html#i05_60)

Target systems [\[→ Section 2.4\]](#02_004.html#i02_202)

create [\[→ Section 2.4\]](#02_004.html#i02_208)

Technical services [\[→ Section 1.2\]](#01_002.html#i01_69)

Tenant management node (TMN) [\[→ Section 7.2\]](#07_002.html#i07_51)

roles [\[→ Section 7.2\]](#07_002.html#i07_54)

Theme designer [\[→ Section 7.4\]](#07_004.html#i07_134)

Time-based one-time password (TOTP) [\[→ Section 2.4\]](#02_004.html#i02_196) [\[→ Section 3.6\]](#03_006.html#i03_174)

Top Time Consumers API [\[→ Section 5.2\]](#05_002.html#i05_54)

Transaction

SICF [\[→ Section 5.4\]](#05_004.html#i05_84)

SM59 [\[→ Section 2.1\]](#02_001.html#i02_19) [\[→ Section 5.4\]](#05_004.html#i05_81)

Transformations [\[→ Section 2.4\]](#02_004.html#i02_210)

Transmission Control Protocol (TCP) [\[→ Section 5.4\]](#05_004.html#i05_66)

Transport Layer Security (TLS) [\[→ Section 2.1\]](#02_001.html#i02_05)

Transporting connections [\[→ Section 5.4\]](#05_004.html#i05_106)

Trust configuration [\[→ Section 3.3\]](#03_003.html#i03_43) [\[→ Section 4.3\]](#04_003.html#i04_26)

Cloud Foundry [\[→ Section 4.3\]](#04_003.html#i04_23)

Neo [\[→ Section 3.3\]](#03_003.html#i03_42)

Trust management [\[→ Section 3.3\]](#03_003.html#i03_61) [\[→ Section 3.3\]](#03_003.html#i03_83) [\[→ Section 3.6\]](#03_006.html#i03_181)

Trust relationship [\[→ Section 2.2\]](#02_002.html#i02_79) [\[→ Section 3.3\]](#03_003.html#i03_45) [\[→ Section 3.6\]](#03_006.html#i03_190)

Truststore [\[→ Section 2.1\]](#02_001.html#i02_41) [\[→ Section 2.1\]](#02_001.html#i02_45)

configuration [\[→ Section 2.1\]](#02_001.html#i02_48)

create [\[→ Section 2.1\]](#02_001.html#i02_46)

Tunnel connection limits [\[→ Section 5.4\]](#05_004.html#i05_98)

Two-factor authentication [\[→ Section 2.4\]](#02_004.html#i02_195) [\[→ Section 3.3\]](#03_003.html#i03_87) [\[→ Section 3.6\]](#03_006.html#i03_164) [\[→ Section 4.6\]](#04_006.html#i04_110) [\[→ Section 4.6\]](#04_006.html#i04_123)

set up [\[→ Section 3.6\]](#03_006.html#i03_169)

test [\[→ Section 3.6\]](#03_006.html#i03_180)

[U ⇑](#index.html#index)

Unique resource identifier (URI) [\[→ Section 1.3\]](#01_003.html#i01_135) [\[→ Section 5.2\]](#05_002.html#i05_22)

Usage-based model [\[→ Section 1.3\]](#01_003.html#i01_116)

useFileUserStore file [\[→ Section 5.3\]](#05_003.html#i05_62)

User accounts [\[→ Section 2.4\]](#02_004.html#i02_168)

User authentication [\[→ Section 2.2\]](#02_002.html#i02_50)

Cloud Integration capability [\[→ Section 7.2\]](#07_002.html#i07_70)

User authorization [\[→ Section 2.3\]](#02_003.html#i02_110)

User experience (UX) [\[→ Section 1.1\]](#01_001.html#i01_31) [\[→ Section 7.1\]](#07_001.html#i07_12)

User groups [\[→ Section 2.4\]](#02_004.html#i02_172) [\[→ Section 3.4\]](#03_004.html#i03_129) [\[→ Section 3.4\]](#03_004.html#i03_147) [\[→ Section 7.1\]](#07_001.html#i07_30) [\[→ Section 7.2\]](#07_002.html#i07_95)

assign [\[→ Section 2.4\]](#02_004.html#i02_175)

assign roles [\[→ Section 3.4\]](#03_004.html#i03_149)

assign users [\[→ Section 3.4\]](#03_004.html#i03_150)

create [\[→ Section 2.4\]](#02_004.html#i02_173) [\[→ Section 3.4\]](#03_004.html#i03_148)

mapping [\[→ Section 7.1\]](#07_001.html#i07_33)

User identifiers [\[→ Section 3.6\]](#03_006.html#i03_198)

User interfaces (UIs) [\[→ Section 4.6\]](#04_006.html#i04_88)

User management [\[→ Section 2.4\]](#02_004.html#i02_140) [\[→ Section 2.4\]](#02_004.html#i02_166) [\[→ Section 3.2\]](#03_002.html#i03_17) [\[→ Section 4.2\]](#04_002.html#i04_13)

Cloud Foundry [\[→ Section 4.2\]](#04_002.html#i04_15) [\[→ Section 4.6\]](#04_006.html#i04_84) [\[→ Section 6.3\]](#06_003.html#i06_47)

create users [\[→ Section 4.2\]](#04_002.html#i04_21)

duplicate users [\[→ Section 3.6\]](#03_006.html#i03_177)

locking users [\[→ Section 2.4\]](#02_004.html#i02_183)

Neo [\[→ Section 3.2\]](#03_002.html#i03_16) [\[→ Section 6.3\]](#06_003.html#i06_43)

real-world examples [\[→ Section 3.6\]](#03_006.html#i03_158)

unlocking users [\[→ Section 2.4\]](#02_004.html#i02_170)

User reports [\[→ Section 4.4\]](#04_004.html#i04_76) [\[→ Section 4.4\]](#04_004.html#i04_77)

User store [\[→ Section 2.2\]](#02_002.html#i02_102)

[V ⇑](#index.html#index)

Virtual host name [\[→ Section 5.4\]](#05_004.html#i05_68) [\[→ Section 5.4\]](#05_004.html#i05_77)

Visual Studio Code (VS Code) [\[→ Section 7.1\]](#07_001.html#i07_04)

[W ⇑](#index.html#index)

Web cookies [\[→ Section 5.4\]](#05_004.html#i05_91)

Web interface directory [\[→ Section 6.5\]](#06_005.html#i06_87)

Web shop registration [\[→ Section 2.4\]](#02_004.html#i02_145)

WebSocket [\[→ Section 5.4\]](#05_004.html#i05_87)

Wildcards [\[→ Section 5.4\]](#05_004.html#i05_67) [\[→ Section 5.4\]](#05_004.html#i05_86)

Worker node [\[→ Section 7.2\]](#07_002.html#i07_52) [\[→ Section 7.2\]](#07_002.html#i07_67)

roles [\[→ Section 7.2\]](#07_002.html#i07_55)

Workflows [\[→ Section 3.4\]](#03_004.html#i03_133) [\[→ Section 3.4\]](#03_004.html#i03_140) [\[→ Section 3.4\]](#03_004.html#i03_153)

Workspace [\[→ Section 7.1\]](#07_001.html#i07_24)

writeHexDump file [\[→ Section 5.2\]](#05_002.html#i05_33)

# Service Pages

The following sections contain notes on how you can contact us. In addition, you are provided with further recommendations on the customization of the screen layout for your e-book.

## Praise and Criticism

We hope that you enjoyed reading this book. If it met your expectations, please do recommend it. If you think there is room for improvement, please get in touch with the editor of the book: [Megan Fuerst](mailto:meganf@rheinwerk-publishing.com). We welcome every suggestion for improvement but, of course, also any praise! You can also share your reading experience via Twitter, Facebook, or email.

## Supplements

If there are supplements available (sample code, exercise materials, lists, and so on), they will be provided in your online library and on the web catalog page for this book. You can directly navigate to this page using the following link: [https://www.sap-press.com/5627](https://www.sap-press.com/5627). Should we learn about typos that alter the meaning or content errors, we will provide a list with corrections there, too.

## Technical Issues

If you experience technical issues with your e-book or e-book account at SAP PRESS, please feel free to contact our reader service: [support@rheinwerk-publishing.com](mailto:support@rheinwerk-publishing.com).

Please note, however, that issues regarding the screen presentation of the book content are usually not caused by errors in the e-book document. Because nearly every reading device (computer, tablet, smartphone, e-book reader) interprets the EPUB or Mobi file format differently, it is unfortunately impossible to set up the e-book document in such a way that meets the requirements of all use cases.

In addition, not all reading devices provide the same text presentation functions and not all functions work properly. Finally, you as the user also define with your settings how the book content is displayed on the screen.

The EPUB format, as currently provided and handled by the device manufacturers, is actually primarily suitable for the display of mere text documents, such as novels. Difficulties arise as soon as technical text contains figures, tables, footnotes, marginal notes, or programming code. For more information, please refer to the section [Notes on the Screen Presentation](#notes.html#screenpresentation) and the following section.

Should none of the recommended settings satisfy your layout requirements, we recommend that you use the PDF version of the book, which is available for download in your online library.

## Recommendations for Screen Presentation and Navigation

We recommend using a sans-serif font, such as Arial or Seravek, and a low font size of approx. 30–40% in portrait format and 20–30% in landscape format. The background shouldn’t be too bright.

Make use of the hyphenation option. If it doesn't work properly, align the text to the left margin. Otherwise, justify the text.

To perform searches in the e-book, the index of the book will reliably guide you to the really relevant pages of the book. If the index doesn't help, you can use the search function of your reading device.

Since it is available as a double-page spread in landscape format, the table of contents we’ve included probably gives a better overview of the content and the structure of the book than the corresponding function of your reading device. To enable you to easily open the table of contents anytime, it has been included as a separate entry in the device-generated table of contents.

If you want to zoom in on a figure, tap the respective figure once. By tapping once again, you return to the previous screen. If you tap twice (on the iPad), the figure is displayed in the original size and then has to be zoomed in to the desired size. If you tap once, the figure is directly zoomed in and displayed with a higher resolution.

For books that contain programming code, please note that the code lines may be wrapped incorrectly or displayed incompletely as of a certain font size. In case of doubt, please reduce the font size.

## About Us and Our Program

The website [https://www.sap-press.com](https://www.sap-press.com) provides detailed and first-hand information on our current publishing program. Here, you can also easily order all of our books and e-books. Information on Rheinwerk Publishing Inc. and additional contact options can also be found at [https://www.sap-press.com](https://www.sap-press.com).

# Legal Notes

This section contains the detailed and legally binding usage conditions for this e-book.

## Copyright Note

This publication is protected by copyright in its entirety. All usage and exploitation rights are reserved by the author and Rheinwerk Publishing; in particular the right of reproduction and the right of distribution, be it in printed or electronic form.  
© 2023 by Rheinwerk Publishing Inc., Boston (MA)

## Your Rights as a User

You are entitled to use this e-book for personal purposes only. In particular, you may print the e-book for personal use or copy it as long as you store this copy on a device that is solely and personally used by yourself. You are not entitled to any other usage or exploitation.

In particular, it is not permitted to forward electronic or printed copies to third parties. Furthermore, it is not permitted to distribute the e-book on the internet, in intranets, or in any other way or make it available to third parties. Any public exhibition, other publication, or any reproduction of the e-book beyond personal use are expressly prohibited. The aforementioned does not only apply to the e-book in its entirety but also to parts thereof (e.g., charts, pictures, tables, sections of text).

Copyright notes, brands, and other legal reservations as well as the digital watermark may not be removed from the e-book.

## Digital Watermark

This e-book copy contains a digital watermark, a signature that indicates which person may use this copy.

If you, dear reader, are not this person, you are violating the copyright. So please refrain from using this e-book and inform us about this violation. A brief email to [info@rheinwerk-publishing.com](mailto:info@rheinwerk-publishing.com) is sufficient. Thank you!

## Trademarks

The common names, trade names, descriptions of goods, and so on used in this publication may be trademarks without special identification and subject to legal regulations as such.

All of the screenshots and graphics reproduced in this book are subject to copyright © SAP SE, Dietmar-Hopp-Allee 16, 69190 Walldorf, Germany. SAP, ABAP, ASAP, Concur Hipmunk, Duet, Duet Enterprise, ExpenseIt, SAP ActiveAttention, SAP Adaptive Server Enterprise, SAP Advantage Database Server, SAP ArchiveLink, SAP Ariba, SAP Business ByDesign, SAP Business Explorer (SAP BEx), SAP BusinessObjects, SAP BusinessObjects Explorer, SAP BusinessObjects Web Intelligence, SAP Business One, SAP Business Workflow, SAP BW/4HANA, SAP C/4HANA, SAP Concur, SAP Crystal Reports, SAP EarlyWatch, SAP Fieldglass, SAP Fiori, SAP Global Trade Services (SAP GTS), SAP GoingLive, SAP HANA, SAP Jam, SAP Leonardo, SAP Lumira, SAP MaxDB, SAP NetWeaver, SAP PartnerEdge, SAPPHIRE NOW, SAP PowerBuilder, SAP PowerDesigner, SAP R/2, SAP R/3, SAP Replication Server, SAP Roambi, SAP S/4HANA, SAP S/4HANA Cloud, SAP SQL Anywhere, SAP Strategic Enterprise Management (SAP SEM), SAP SuccessFactors, SAP Vora, TripIt, and Qualtrics are registered or unregistered trademarks of SAP SE, Walldorf, Germany.

## Limitation of Liability

Regardless of the care that has been taken in creating texts, figures, and programs, neither the publisher nor the author, editor, or translator assume any legal responsibility or any liability for possible errors and their consequences.