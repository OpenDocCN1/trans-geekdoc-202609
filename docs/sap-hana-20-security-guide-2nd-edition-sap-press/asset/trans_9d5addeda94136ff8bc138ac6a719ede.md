


![SAP HANA® 2.0 Security Guide – Cover](common/cover.jpg)

Jonathan Haun

# SAP HANA® 2.0 Security Guide

2nd edition 2020

![Logo Rheinwerk Publishing](common/logo_sap.png)

# Imprint

This e-book is a publication many contributed to, specifically:

Editor Meagan White  
Acquisitions Editor Hareem Shafi  
Copyeditor Yvette Chin  
Cover Design Graham Geary  
Photo Credit iStockphoto.com/173255520/© aluxum  
Production E-Book Hannah Lane  
Typesetting E-Book III-satz, Husby (Germany)  

We hope that you liked this e-book. Please share your feedback with us and read the [Service Pages](#service.html) to find out how to contact us.

The Library of Congress has cataloged the printed edition as follows:  

Names: Haun, Jonathan, author.  
Title: SAP HANA 2.0 security guide / Jonathan Haun.  
Other titles: SAP HANA security guide  
Description: 2nd edition. | Bonn ; Boston : Rheinwerk Publishing, 2020. |  
Revised editon of: SAP HANA security guide.  
Identifiers: LCCN 2020000009 (print) | LCCN 2020000010 (ebook) | ISBN  
9781493218967 (hardcover) | ISBN 9781493218974 (ebook)  
Subjects: LCSH: Database security. | Computer security. | Business  
enterprises--Computer networks--Security measures. | SAP HANA  
(Electronic resource)  
Classification: LCC QA76.9.D314 H348 2020 (print) | LCC QA76.9.D314  
(ebook) | DDC 005.8--dc23  
LC record available at https://lccn.loc.gov/2020000009  
LC ebook record available at https://lccn.loc.gov/2020000010  

ISBN 978-1-4932-1896-7 (print)  
ISBN 978-1-4932-1897-4 (e-book)  
ISBN 978-1-4932-1898-1 (print and e-book)  

© 2020 by Rheinwerk Publishing Inc., Boston (MA)  
2nd, updated and revised edition 2020  

# Dear Reader,

Recently, a new branch of a bank was built on my route to work. Because I was driving past it twice a day, I got to see how it was built, brick-by-brick. First the ground was leveled, and then the foundation poured. From there, the whole building was framed and then gradually filled in with brick and plaster. At some point, pre-roof, the vault was lifted in, disappearing into the building before I could even see it.

While building a secure bank branch and setting up security in your SAP HANA system are wildly different processes, there are some lessons to be drawn. A new SAP HANA system is good chance to start your security practices fresh, leveling on the ground beneath you. Layers of security in the form of privileges, authorizations, certificates, and other measures are the best way to put up walls and vaults between those who should have access, and those who shouldn’t.

What did you think about SAP HANA 2.0 Security Guide? Your comments and suggestions are the most useful tools to help us make our books the best they can be. Please feel free to contact me and share any praise or criticism you may have.

Thank you for purchasing a book from SAP PRESS!

Meagan White  
Editor, SAP PRESS  

[meaganw@rheinwerk-publishing.com](mailto:meaganw@rheinwerk-publishing.com)  
[www.sap-press.com](http://www.sap-press.com)  
Rheinwerk Publishing • Boston, MA  

# Notes on Usage

This e-book is protected by copyright. By purchasing this e-book, you have agreed to accept and adhere to the copyrights. You are entitled to use this e-book for personal purposes. You may print and copy it, too, but also only for personal use. Sharing an electronic or printed copy with others, however, is not permitted, neither as a whole nor in parts. Of course, making them available on the Internet or in a company network is illegal as well.

For detailed and legally binding usage conditions, please refer to the section [Legal Notes](#legal_notes.html).

This e-book copy contains a digital watermark, a signature that indicates which person may use this copy:

# Notes on the Screen Presentation

You are reading this e-book in a file format (EPUB or Mobi) that makes the book content adaptable to the display options of your reading device and to your personal needs. That’s a great thing; but unfortunately not every device displays the content in the same way and the rendering of features such as pictures and tables or hyphenation can lead to difficulties. This e-book was optimized for the presentation on as many common reading devices as possible.

If you want to zoom in on a figure (especially in iBooks on the iPad), tap the respective figure once. By tapping once again, you return to the previous screen. You can find more recommendations on the customization of the screen layout on the [Service Pages](#service.html).

# Table of Contents

## [Dear Reader](#dear_reader.html#extra-leser)

## [Notes on Usage](#notes.html#extra-hinweise)

## [Table of Contents](#toc.html#extra-toc)

## [Preface](#00_001.html#h0.1)

## [Introduction](#00_002.html#h0.2)

# [1 Managing Security with the SAP HANA Cockpit](#01_001.html#h1)

## [1.1 What Is the SAP HANA Cockpit?](#01_001.html#h1.1)

### [1.1.1 SAP HANA Cockpit Architecture](#01_001.html#h1.1.1)

### [1.1.2 Getting Started with the SAP HANA Cockpit](#01_001.html#h1.1.2)

### [1.1.3 Navigating SAP HANA Cockpit](#01_001.html#h1.1.3)

## [1.2 Security Areas in SAP HANA Cockpit](#01_002.html#h1.2)

### [1.2.1 User & Role Management Area](#01_002.html#h1.2.1)

### [1.2.2 Data Encryption](#01_002.html#h1.2.2)

### [1.2.3 Authentication](#01_002.html#h1.2.3)

### [1.2.4 Security Related Links](#01_002.html#h1.2.4)

### [1.2.5 Anonymization Report](#01_002.html#h1.2.5)

### [1.2.6 Auditing](#01_002.html#h1.2.6)

## [1.3 SAP HANA Database Explorer and SQL Console](#01_003.html#h1.3)

## [1.4 Summary](#01_004.html#h1.4)

# [2 Introduction to SAP HANA Privileges](#02_001.html#h2)

## [2.1 Privileges within SAP HANA](#02_001.html#h2.1)

### [2.1.1 System Privileges](#02_001.html#h2.1.1)

### [2.1.2 Object Privileges](#02_001.html#h2.1.2)

### [2.1.3 Analytic Privileges](#02_001.html#h2.1.3)

### [2.1.4 Package Privileges](#02_001.html#h2.1.4)

### [2.1.5 Application Privileges](#02_001.html#h2.1.5)

## [2.2 Privilege Validation and Assignment](#02_002.html#h2.2)

### [2.2.1 Assigning Privileges](#02_002.html#h2.2.1)

### [2.2.2 Validating Privileges](#02_002.html#h2.2.2)

## [2.3 Summary](#02_003.html#h2.3)

# [3 Catalog Objects](#03_001.html#h3)

## [3.1 What Are SAP HANA Catalog Objects?](#03_001.html#h3.1)

## [3.2 Creating and Managing Native Catalog Objects](#03_002.html#h3.2)

### [3.2.1 Creating Schemas](#03_002.html#h3.2.1)

### [3.2.2 Creating Catalog Tables](#03_002.html#h3.2.2)

### [3.2.3 Creating Other Catalog Objects](#03_002.html#h3.2.3)

## [3.3 Creating and Managing Repository Catalog Objects](#03_003.html#h3.3)

### [3.3.1 Creating Repository Schemas](#03_003.html#h3.3.1)

### [3.3.2 Creating Repository Tables](#03_003.html#h3.3.2)

## [3.4 Deploying Repository Objects](#03_004.html#h3.4)

## [3.5 Case Study](#03_005.html#h3.5)

## [3.6 Summary](#03_006.html#h3.6)

# [4 User Accounts](#04_001.html#h4)

## [4.1 What Are User Accounts?](#04_001.html#h4.1)

### [4.1.1 Standard User Accounts](#04_001.html#h4.1.1)

### [4.1.2 Technical User Accounts](#04_001.html#h4.1.2)

### [4.1.3 Restricted User Accounts](#04_001.html#h4.1.3)

### [4.1.4 LDAP User Accounts](#04_001.html#h4.1.4)

## [4.2 Creating and Managing User Accounts](#04_002.html#h4.2)

### [4.2.1 Creating and Managing Users with SQL Statements](#04_002.html#h4.2.1)

### [4.2.2 Creating and Managing Users in the SAP HANA Cockpit](#04_002.html#h4.2.2)

### [4.2.3 Creating and Managing Users with the SAP HANA Web-Based Development Workbench](#04_002.html#h4.2.3)

### [4.2.4 User Account System Views](#04_002.html#h4.2.4)

### [4.2.5 Deleting User Accounts](#04_002.html#h4.2.5)

## [4.3 Granting and Revoking Privileges](#04_003.html#h4.3)

### [4.3.1 Granting and Revoking Privileges with SQL](#04_003.html#h4.3.1)


