   

![image](OEBPS/Images/9781284031652_FC.jpg)

![pub](OEBPS/Images/9781284031652_title.jpg)

![pub](OEBPS/Images/9781284031652_pgii.jpg)

*World Headquarters*

Jones & Bartlett Learning

5 Wall Street

Burlington, MA 01803

978-443-5000

[info@jblearning.com](mailto:info@jblearning.com)

[www.jblearning.com](http://www.jblearning.com)

Jones & Bartlett Learning books and products are available through most bookstores and online booksellers. To contact Jones & Bartlett Learning directly, call 800-832-0034, fax 978-443-8000, or visit our website, [www.jblearning.com](http://www.jblearning.com).

Substantial discounts on bulk quantities of Jones & Bartlett Learning publications are available to corporations, professional associations, and other qualified organizations. For details and specific discount information, contact the special sales department at Jones & Bartlett Learning via the above contact information or send an email to [specialsales@jblearning.com](mailto:specialsales@jblearning.com).

**Copyright © 2014 by Jones & Bartlett Learning, LLC, an Ascend Learning Company**

All rights reserved. No part of the material protected by this copyright may be reproduced or utilized in any form, electronic or mechanical, including photocopying, recording, or by any information storage and retrieval system, without written permission from the copyright owner.

The content, statements, views, and opinions herein are the sole expression of the respective authors and not that of Jones & Bartlett Learning, LLC. Reference herein to any specific commercial product, process, or service by trade name, trademark, manufacturer, or otherwise does not constitute or imply its endorsement or recommendation by Jones & Bartlett Learning, LLC and such reference shall not be used for advertising or product endorsement purposes. All trademarks displayed are the trademarks of the parties noted herein. *Security Strategies in Windows Platforms and Applications, Second Edition* is an independent publication and has not been authorized, sponsored, or otherwise approved by the owners of the trademarks or service marks referenced in this product.

There may be images in this book that feature models; these models do not necessarily endorse, represent, or participate in the activities represented in the images. Any screenshots in this product are for educational and instructive purposes only. Any individuals and scenarios featured in the case studies throughout this product may be real or fictitious, but are used for instructional purposes only.

This publication is designed to provide accurate and authoritative information in regard to the subject matter covered. It is sold with the understanding that the publisher is not engaged in rendering legal or other professional service. If legal advice or other expert assistance is required, the service of a competent professional person should be sought.

**Production Credits**

Chief Executive Officer: Ty Field

President: James Homer

Chief Product Officer: Eduardo Moura

SVP, Curriculum Solutions: Christopher Will

Director of Sales, Curriculum Solutions: Randi Roger

Senior Marketing Manager: Andrea DeFronzo

Associate Marketing Manager: Kelly Thompson

VP, Design and Production: Anne Spencer

VP, Manufacturing and Inventory Control: Therese Connell

Manufacturing and Inventory Control Supervisor: Amy Bacus

Editorial Management: High Stakes Writing, LLC, President: Lawrence J. Goodrich

Senior Editor, HSW: Ruth Walker

Associate Program Manager: Rainna Erikson

Production Manager: Susan Schultz

Composition: Gamut+Hue, LLC

Cover Design: Kristin E. Parker

Director of Photo Research and Permissions: Amy Wrynn

Photo Research Coordinator: Joseph Veiga

Cover Image: © HunThomas/ShutterStock, Inc.

Chapter Opener Image: © Rodolfo Clix/[Dreamstime.com](http://Dreamstime.com)

Printing and Binding: Edwards Brothers Malloy

Cover Printing: Edwards Brothers Malloy

**ISBN: 978-1-284-03165-2**

**Library of Congress Cataloging-in-Publication Data**

Not available at time of printing.

6048

Printed in the United States of America

17 16 15 14 13 10 9 8 7 6 5 4 3 2 1

**Contents**

 
|  || [Preface](#04_Preface.xhtml) |
| --- | --- |
|  || [Acknowledgments](#05_Acknowledgments.xhtml) |
| [**PART ONE**](#09_Part1.xhtml) || [**The Microsoft Windows Security Situation**](#09_Part1.xhtml) |
| [**CHAPTER 1**](#10_Chaper1_split_000.xhtml) || [**Microsoft Windows and the Threat Landscape**](#10_Chaper1_split_000.xhtml) |
|  || [Information Systems Security](#10_Chaper1_split_001.xhtml#sec_1) |
|  || [Tenets of Information Security: The C-I-A Triad](#10_Chaper1_split_001.xhtml#sec_2) |
|  || [Confidentiality](#10_Chaper1_split_001.xhtml#sec_3) |
|  || [Integrity](#10_Chaper1_split_001.xhtml#sec_4) |
|  || [Availability](#10_Chaper1_split_001.xhtml#sec_5) |
|  || [Mapping Microsoft Windows and Applications into a Typical IT Infrastructure](#10_Chaper1_split_001.xhtml#sec_6) |
|  || [Windows Clients](#10_Chaper1_split_001.xhtml#sec_7) |
|  || [Windows Servers](#10_Chaper1_split_001.xhtml#sec_8) |
|  || [Microsoft’s End-User License Agreement (EULA)](#10_Chaper1_split_001.xhtml#sec_9) |
|  || [Windows Threats and Vulnerabilities](#10_Chaper1_split_001.xhtml#sec_10) |
|  || [Anatomy of Microsoft Windows Vulnerabilities](#10_Chaper1_split_001.xhtml#sec_11) |
|  || [Code Red](#10_Chaper1_split_001.xhtml#sec_12) |
|  || [SQL Slammer](#10_Chaper1_split_001.xhtml#sec_13) |
|  || [Conficker](#10_Chaper1_split_001.xhtml#sec_14) |
|  || [Discovery-Analysis-Remediation Cycle](#10_Chaper1_split_001.xhtml#sec_15) |
|  || [Discovery](#10_Chaper1_split_001.xhtml#sec_16) |
|  || [Analysis](#10_Chaper1_split_001.xhtml#sec_17) |
|  || [Remediation](#10_Chaper1_split_001.xhtml#sec_18) |
|  || [Common Forms of Attack](#10_Chaper1_split_001.xhtml#sec_19) |
|  || [**CHAPTER SUMMARY**](#10_Chaper1_split_001.xhtml#sec_20) |
|  || [**KEY CONCEPTS AND TERMS**](#10_Chaper1_split_001.xhtml#sec_21) |
|  || [**CHAPTER 1 ASSESSMENT**](#10_Chaper1_split_001.xhtml#sec_22) |
| [**CHAPTER 2**](#11_Chaper2_split_000.xhtml) || [**Security in the Microsoft Windows Operating System**](#11_Chaper2_split_000.xhtml) |
|  || [Operating System Components and Architecture](#11_Chaper2_split_001.xhtml#sec_23) |
|  || [The Kernel](#11_Chaper2_split_001.xhtml#sec_24) |
|  || [Operating System Components](#11_Chaper2_split_001.xhtml#sec_25) |
|  || [Basic Windows Operating System Architecture](#11_Chaper2_split_001.xhtml#sec_26) |
|  || [Windows Run Modes](#11_Chaper2_split_001.xhtml#sec_27) |
|  || [Kernel Mode](#11_Chaper2_split_001.xhtml#sec_28) |
|  || [User Mode](#11_Chaper2_split_001.xhtml#sec_29) |
|  || [Access Controls and Authentication](#11_Chaper2_split_001.xhtml#sec_30) |
|  || [Authentication Methods](#11_Chaper2_split_001.xhtml#sec_31) |
|  || [Access Control Methods](#11_Chaper2_split_001.xhtml#sec_32) |
|  || [Security Access Tokens, Rights, and Permissions](#11_Chaper2_split_001.xhtml#sec_33) |
|  || [Security Identifier](#11_Chaper2_split_001.xhtml#sec_34) |
|  || [Access Rules, Rights, and Permissions](#11_Chaper2_split_001.xhtml#sec_35) |
|  || [Users, Groups, and Active Directory](#11_Chaper2_split_001.xhtml#sec_36) |
|  || [Workgroups](#11_Chaper2_split_001.xhtml#sec_37) |
|  || [Active Directory](#11_Chaper2_split_001.xhtml#sec_38) |
|  || [Windows Attack Surfaces and Mitigation](#11_Chaper2_split_001.xhtml#sec_39) |
|  || [Multilayered Defense](#11_Chaper2_split_001.xhtml#sec_40) |
|  || [Mitigation](#11_Chaper2_split_001.xhtml#sec_41) |
|  || [Fundamentals of Microsoft Windows Security Monitoring and Maintenance](#11_Chaper2_split_001.xhtml#sec_42) |
|  || [Security Monitoring](#11_Chaper2_split_001.xhtml#sec_43) |
|  || [Identify Vulnerabilities](#11_Chaper2_split_001.xhtml#sec_44) |
|  || [**CHAPTER SUMMARY**](#11_Chaper2_split_001.xhtml#sec_45) |
|  || [**KEY CONCEPTS AND TERMS**](#11_Chaper2_split_001.xhtml#sec_46) |
|  || [**CHAPTER 2 ASSESSMENT**](#11_Chaper2_split_001.xhtml#sec_47) |
| [**PART TWO**](#12_Part2.xhtml) || [**Managing and Maintaining Microsoft Windows Security**](#12_Part2.xhtml) |
| [**CHAPTER 3**](#13_Chaper3_split_000.xhtml) || [**Access Controls in Microsoft Windows**](#13_Chaper3_split_000.xhtml) |
|  || [The Principle of Least Privilege](#13_Chaper3_split_001.xhtml#sec_48) |
|  || [The Orange Book](#13_Chaper3_split_001.xhtml#sec_49) |
|  || [Least Privilege and LUAs](#13_Chaper3_split_001.xhtml#sec_50) |
|  || [Rights and Permissions](#13_Chaper3_split_001.xhtml#sec_51) |
|  || [Access Models: Identification, Authentication, Authorization, ACLs, and More](#13_Chaper3_split_001.xhtml#sec_52) |
|  || [Windows Server 2012 Dynamic Access Control (DAC)](#13_Chaper3_split_001.xhtml#sec_53) |
|  || [User Account Control (UAC)](#13_Chaper3_split_001.xhtml#sec_54) |
|  || [Sharing SIDs and SATs](#13_Chaper3_split_001.xhtml#sec_55) |
|  || [Managed Service Accounts](#13_Chaper3_split_001.xhtml#sec_56) |
|  || [Kerberos](#13_Chaper3_split_001.xhtml#sec_57) |
|  || [NT LAN Manager](#13_Chaper3_split_001.xhtml#sec_58) |
|  || [Windows Objects and Access Controls](#13_Chaper3_split_001.xhtml#sec_59) |
|  || [Windows DACLs](#13_Chaper3_split_001.xhtml#sec_60) |
|  || [DACL Advanced Permissions](#13_Chaper3_split_001.xhtml#sec_61) |
|  || [SIDs, GUIDs, and CLSIDs](#13_Chaper3_split_001.xhtml#sec_62) |
|  || [Calculating Microsoft Windows Access Permissions](#13_Chaper3_split_001.xhtml#sec_63) |
|  || [Auditing and Tracking Windows Access](#13_Chaper3_split_001.xhtml#sec_64) |
|  || [Microsoft Windows Access Management Tools](#13_Chaper3_split_001.xhtml#sec_65) |
|  || [Cacls.exe](#13_Chaper3_split_001.xhtml#sec_66) |
|  || [Icacls.exe](#13_Chaper3_split_001.xhtml#sec_67) |
|  || [Robocopy](#13_Chaper3_split_001.xhtml#sec_68) |
|  || [Best Practices for Microsoft Windows Access Control](#13_Chaper3_split_001.xhtml#sec_69) |
|  || [**CHAPTER SUMMARY**](#13_Chaper3_split_001.xhtml#sec_70) |
|  || [**KEY CONCEPTS AND TERMS**](#13_Chaper3_split_001.xhtml#sec_71) |
|  || [**CHAPTER 3 ASSESSMENT**](#13_Chaper3_split_001.xhtml#sec_72) |
| [**CHAPTER 4**](#14_Chaper4_split_000.xhtml) || [**Microsoft Windows Encryption Tools and Technologies**](#14_Chaper4_split_000.xhtml) |
|  || [Encryption Methods Microsoft Windows Supports](#14_Chaper4_split_001.xhtml#sec_73) |
|  || [Encrypting File System, BitLocker, and BitLocker To Go](#14_Chaper4_split_001.xhtml#sec_74) |
|  || [Encrypting File System](#14_Chaper4_split_001.xhtml#sec_75) |
|  || [BitLocker](#14_Chaper4_split_001.xhtml#sec_76) |
|  || [BitLocker To Go](#14_Chaper4_split_001.xhtml#sec_77) |
|  || [Enabling File-, Folder-, and Volume-Level Encryption](#14_Chaper4_split_001.xhtml#sec_78) |
|  || [Enabling EFS](#14_Chaper4_split_001.xhtml#sec_79) |
|  || [Enabling BitLocker](#14_Chaper4_split_001.xhtml#sec_80) |
|  || [Enabling BitLocker To Go](#14_Chaper4_split_001.xhtml#sec_81) |
|  || [Encryption in Communications](#14_Chaper4_split_001.xhtml#sec_82) |
|  || [Encryption Protocols in Microsoft Windows](#14_Chaper4_split_001.xhtml#sec_83) |
|  || [SSL/TLS](#14_Chaper4_split_001.xhtml#sec_84) |
|  || [Virtual Private Network](#14_Chaper4_split_001.xhtml#sec_85) |
|  || [Wireless Security](#14_Chaper4_split_001.xhtml#sec_86) |
|  || [Microsoft Windows and Security Certificates](#14_Chaper4_split_001.xhtml#sec_87) |
|  || [Public Key Infrastructure](#14_Chaper4_split_001.xhtml#sec_88) |
|  || [Best Practices for Windows Encryption Techniques](#14_Chaper4_split_001.xhtml#sec_89) |
|  || [**CHAPTER SUMMARY**](#14_Chaper4_split_001.xhtml#sec_90) |
|  || [**KEY CONCEPTS AND TERMS**](#14_Chaper4_split_001.xhtml#sec_91) |
|  || [**CHAPTER 4 ASSESSMENT**](#14_Chaper4_split_001.xhtml#sec_92) |
| [**CHAPTER 5**](#15_Chaper5_split_000.xhtml) || [**Protecting Microsoft Windows Against Malware**](#15_Chaper5_split_000.xhtml) |
|  || [The Purpose of Malware](#15_Chaper5_split_001.xhtml#sec_93) |
|  || [Types of Malware](#15_Chaper5_split_001.xhtml#sec_94) |
|  || [Virus](#15_Chaper5_split_001.xhtml#sec_95) |
|  || [Worm](#15_Chaper5_split_001.xhtml#sec_96) |
|  || [Trojan Horse](#15_Chaper5_split_001.xhtml#sec_97) |
|  || [Rootkit](#15_Chaper5_split_001.xhtml#sec_98) |
|  || [Spyware](#15_Chaper5_split_001.xhtml#sec_99) |
|  || [Ransomware](#15_Chaper5_split_001.xhtml#sec_100) |
|  || [Malware Type Summary](#15_Chaper5_split_001.xhtml#sec_101) |
|  || [Antivirus and Anti-Spyware Software](#15_Chaper5_split_001.xhtml#sec_102) |
|  || [Antivirus Software](#15_Chaper5_split_001.xhtml#sec_103) |
|  || [Anti-Spyware Software](#15_Chaper5_split_001.xhtml#sec_104) |
|  || [Importance of Updating Your Software](#15_Chaper5_split_001.xhtml#sec_105) |
|  || [Maintaining a Malware-Free Environment](#15_Chaper5_split_001.xhtml#sec_106) |
|  || [Scanning and Auditing Malware](#15_Chaper5_split_001.xhtml#sec_107) |
|  || [Tools and Techniques for Removing Malware](#15_Chaper5_split_001.xhtml#sec_108) |
|  || [Malware Prevention Best Practices](#15_Chaper5_split_001.xhtml#sec_109) |
|  || [**CHAPTER SUMMARY**](#15_Chaper5_split_001.xhtml#sec_110) |
|  || [**KEY CONCEPTS AND TERMS**](#15_Chaper5_split_001.xhtml#sec_111) |
|  || [**CHAPTER 5 ASSESSMENT**](#15_Chaper5_split_001.xhtml#sec_112) |
| [**CHAPTER 6**](#16_Chaper6_split_000.xhtml) || [**Group Policy Control in Microsoft Windows**](#16_Chaper6_split_000.xhtml) |
|  || [Group Policy and Group Policy Objects](#16_Chaper6_split_001.xhtml#sec_113) |
|  || [Group Policy Settings](#16_Chaper6_split_001.xhtml#sec_114) |
|  || [GPO Linking](#16_Chaper6_split_001.xhtml#sec_115) |
|  || [Making Group Policy Conform to Security Policy](#16_Chaper6_split_001.xhtml#sec_116) |
|  || [Security Responsibility](#16_Chaper6_split_001.xhtml#sec_117) |
|  || [Security Policy and Group Policy](#16_Chaper6_split_001.xhtml#sec_118) |
|  || [Group Policy Targets](#16_Chaper6_split_001.xhtml#sec_119) |
|  || [Types of GPOs in the Registry](#16_Chaper6_split_001.xhtml#sec_120) |
|  || [Local Group Policy Editor](#16_Chaper6_split_001.xhtml#sec_121) |
|  || [GPOs in the Registry Editor](#16_Chaper6_split_001.xhtml#sec_122) |
|  || [Types of GPOs in Active Directory](#16_Chaper6_split_001.xhtml#sec_123) |
|  || [Group Policy Management Console](#16_Chaper6_split_001.xhtml#sec_124) |
|  || [GPOs on the Domain Controller](#16_Chaper6_split_001.xhtml#sec_125) |
|  || [Designing, Deploying, and Tracking Group Policy Controls](#16_Chaper6_split_001.xhtml#sec_126) |
|  || [GPO Application Order](#16_Chaper6_split_001.xhtml#sec_127) |
|  || [Security Filters](#16_Chaper6_split_001.xhtml#sec_128) |
|  || [GPO Windows Management Instrumentation (WMI) Filters](#16_Chaper6_split_001.xhtml#sec_129) |
|  || [Deploying Group Policy](#16_Chaper6_split_001.xhtml#sec_130) |
|  || [Auditing and Managing Group Policy](#16_Chaper6_split_001.xhtml#sec_131) |
|  || [Group Policy Inventory](#16_Chaper6_split_001.xhtml#sec_132) |
|  || [Analyzing the Effect of GPOs](#16_Chaper6_split_001.xhtml#sec_133) |
|  || [Best Practices for Microsoft Windows Group Policy and Processes](#16_Chaper6_split_001.xhtml#sec_134) |
|  || [Group Policy Design Guidelines](#16_Chaper6_split_001.xhtml#sec_135) |
|  || [**CHAPTER SUMMARY**](#16_Chaper6_split_001.xhtml#sec_136) |
|  || [**KEY CONCEPTS AND TERMS**](#16_Chaper6_split_001.xhtml#sec_137) |
|  || [**CHAPTER 6 ASSESSMENT**](#16_Chaper6_split_001.xhtml#sec_138) |
| [**CHAPTER 7**](#17_Chaper7_split_000.xhtml) || [**Microsoft Windows Security Profile and Audit Tools**](#17_Chaper7_split_000.xhtml) |
|  || [Profiling Microsoft Windows Security](#17_Chaper7_split_001.xhtml#sec_139) |
|  || [Profiling](#17_Chaper7_split_001.xhtml#sec_140) |
|  || [Profiling Windows Computers](#17_Chaper7_split_001.xhtml#sec_141) |
|  || [Microsoft Baseline Security Analyzer (MBSA)](#17_Chaper7_split_001.xhtml#sec_142) |
|  || [MBSA GUI](#17_Chaper7_split_001.xhtml#sec_143) |
|  || [MBSA Command Line Interface](#17_Chaper7_split_001.xhtml#sec_144) |
|  || [Shavlik Security Analyzers](#17_Chaper7_split_001.xhtml#sec_145) |
|  || [NetChk Protect Limited](#17_Chaper7_split_001.xhtml#sec_146) |
|  || [NetChk Protect](#17_Chaper7_split_001.xhtml#sec_147) |
|  || [Secunia Personal and Corporate Security Analyzers](#17_Chaper7_split_001.xhtml#sec_148) |
|  || [Secunia Personal Scanners](#17_Chaper7_split_001.xhtml#sec_149) |
|  || [Secunia Corporate Products](#17_Chaper7_split_001.xhtml#sec_150) |
|  || [Microsoft Windows Security Audit](#17_Chaper7_split_001.xhtml#sec_151) |
|  || [Microsoft Windows Security Audit Tools](#17_Chaper7_split_001.xhtml#sec_152) |
|  || [Best Practices for Microsoft Windows Security Audits](#17_Chaper7_split_001.xhtml#sec_153) |
|  || [**CHAPTER SUMMARY**](#17_Chaper7_split_001.xhtml#sec_154) |
|  || [**KEY CONCEPTS AND TERMS**](#17_Chaper7_split_001.xhtml#sec_155) |
|  || [**CHAPTER 7 ASSESSMENT**](#17_Chaper7_split_001.xhtml#sec_156) |
| [**CHAPTER 8**](#18_Chaper8_split_000.xhtml) || [**Microsoft Windows Backup and Recovery Tools**](#18_Chaper8_split_000.xhtml) |
|  || [Microsoft Windows Operating System (OS) and Application Backup and Recovery](#18_Chaper8_split_001.xhtml#sec_157) |
|  || [The Need for Backups](#18_Chaper8_split_001.xhtml#sec_158) |
|  || [The Backup Process](#18_Chaper8_split_001.xhtml#sec_159) |
|  || [The Restore Process](#18_Chaper8_split_001.xhtml#sec_160) |
|  || [Workstation, Server, Network, and Internet Backup Techniques](#18_Chaper8_split_001.xhtml#sec_161) |
|  || [Workstation Backups](#18_Chaper8_split_001.xhtml#sec_162) |
|  || [Server Backups](#18_Chaper8_split_001.xhtml#sec_163) |
|  || [Network Backups](#18_Chaper8_split_001.xhtml#sec_164) |
|  || [Internet Backups](#18_Chaper8_split_001.xhtml#sec_165) |
|  || [Microsoft Windows and Application Backup and Recovery in a Business Continuity Setting](#18_Chaper8_split_001.xhtml#sec_166) |
|  || [Disaster Recovery Plan](#18_Chaper8_split_001.xhtml#sec_167) |
|  || [Business Continuity Plan](#18_Chaper8_split_001.xhtml#sec_168) |
|  || [Where a Restore Fits In](#18_Chaper8_split_001.xhtml#sec_169) |
|  || [Microsoft Windows Backup and Restore Utility](#18_Chaper8_split_001.xhtml#sec_170) |
|  || [Restoring with the Windows Backup and Restore Utility](#18_Chaper8_split_001.xhtml#sec_171) |
|  || [Restoring with the Windows Server 2008 Server Recovery Utility](#18_Chaper8_split_001.xhtml#sec_172) |
|  || [Rebuilding Systems from Bare Metal](#18_Chaper8_split_001.xhtml#sec_173) |
|  || [Managing Backups with Virtual Machines](#18_Chaper8_split_001.xhtml#sec_174) |
|  || [Best Practices for Microsoft Windows Backup and Recovery](#18_Chaper8_split_001.xhtml#sec_175) |
|  || [**CHAPTER SUMMARY**](#18_Chaper8_split_001.xhtml#sec_176) |
|  || [**KEY CONCEPTS AND TERMS**](#18_Chaper8_split_001.xhtml#sec_177) |
|  || [**CHAPTER 8 ASSESSMENT**](#18_Chaper8_split_001.xhtml#sec_178) |
| [**CHAPTER 9**](#19_Chaper9_split_000.xhtml) || [**Microsoft Windows Network Security**](#19_Chaper9_split_000.xhtml) |
|  || [Network Security](#19_Chaper9_split_001.xhtml#sec_179) |
|  || [Network Security Controls](#19_Chaper9_split_001.xhtml#sec_180) |
|  || [Principles of Microsoft Windows Network Security](#19_Chaper9_split_001.xhtml#sec_181) |
|  || [Common Network Components](#19_Chaper9_split_001.xhtml#sec_182) |
|  || [Connection Media](#19_Chaper9_split_001.xhtml#sec_183) |
|  || [Networking Devices](#19_Chaper9_split_001.xhtml#sec_184) |
|  || [Server Computers and Services Devices](#19_Chaper9_split_001.xhtml#sec_185) |
|  || [Microsoft Windows Security Protocols and Services](#19_Chaper9_split_001.xhtml#sec_186) |
|  || [Securing Microsoft Windows Environment Network Services](#19_Chaper9_split_001.xhtml#sec_187) |
|  || [Service Updates](#19_Chaper9_split_001.xhtml#sec_188) |
|  || [Service Accounts](#19_Chaper9_split_001.xhtml#sec_189) |
|  || [Necessary Services](#19_Chaper9_split_001.xhtml#sec_190) |
|  || [Securing Microsoft Windows Wireless Networking](#19_Chaper9_split_001.xhtml#sec_191) |
|  || [Microsoft Windows Desktop Network Security](#19_Chaper9_split_001.xhtml#sec_192) |
|  || [User Authorization and Authentication](#19_Chaper9_split_001.xhtml#sec_193) |
|  || [Malicious Software Protection](#19_Chaper9_split_001.xhtml#sec_194) |
|  || [Outbound Traffic Filtering](#19_Chaper9_split_001.xhtml#sec_195) |
|  || [Microsoft Windows Server Network Security](#19_Chaper9_split_001.xhtml#sec_196) |
|  || [Authentication and Authorization](#19_Chaper9_split_001.xhtml#sec_197) |
|  || [Malicious Software Protection](#19_Chaper9_split_001.xhtml#sec_198) |
|  || [Network Traffic Filtering](#19_Chaper9_split_001.xhtml#sec_199) |
|  || [Best Practices for Microsoft Windows Network Security](#19_Chaper9_split_001.xhtml#sec_200) |
|  || [**CHAPTER SUMMARY**](#19_Chaper9_split_001.xhtml#sec_201) |
|  || [**KEY CONCEPTS AND TERMS**](#19_Chaper9_split_001.xhtml#sec_202) |
|  || [**CHAPTER 9 ASSESSMENT**](#19_Chaper9_split_001.xhtml#sec_203) |
| [**CHAPTER 10**](#20_Chaper10_split_000.xhtml) || [**Microsoft Windows Security Administration**](#20_Chaper10_split_000.xhtml) |
|  || [Security Administration Overview](#20_Chaper10_split_001.xhtml#sec_204) |
|  || [The Security Administration Cycle](#20_Chaper10_split_001.xhtml#sec_205) |
|  || [Security Administration Tasks](#20_Chaper10_split_001.xhtml#sec_206) |
|  || [Maintaining the C-I-A Triad in the Microsoft Windows OS World](#20_Chaper10_split_001.xhtml#sec_207) |
|  || [Maintaining Confidentiality](#20_Chaper10_split_001.xhtml#sec_208) |
|  || [Maintaining Integrity](#20_Chaper10_split_001.xhtml#sec_209) |
|  || [Maintaining Availability](#20_Chaper10_split_001.xhtml#sec_210) |
|  || [Microsoft Windows OS Security Administration](#20_Chaper10_split_001.xhtml#sec_211) |
|  || [Firewall Administration](#20_Chaper10_split_001.xhtml#sec_212) |
|  || [Performance Monitor](#20_Chaper10_split_001.xhtml#sec_213) |
|  || [Backup Administration](#20_Chaper10_split_001.xhtml#sec_214) |
|  || [Operating System Service Pack Administration](#20_Chaper10_split_001.xhtml#sec_215) |
|  || [Group Policy Administration](#20_Chaper10_split_001.xhtml#sec_216) |
|  || [DACL Administration](#20_Chaper10_split_001.xhtml#sec_217) |
|  || [Encryption Administration](#20_Chaper10_split_001.xhtml#sec_218) |
|  || [Anti-Malware Software Administration](#20_Chaper10_split_001.xhtml#sec_219) |
|  || [Ensuring Due Diligence and Regulatory Compliance](#20_Chaper10_split_001.xhtml#sec_220) |
|  || [Due Diligence](#20_Chaper10_split_001.xhtml#sec_221) |
|  || [The Need for Security Policies, Standards, Procedures, and Guidelines](#20_Chaper10_split_001.xhtml#sec_222) |
|  || [Best Practices for Microsoft Windows OS Security Administration](#20_Chaper10_split_001.xhtml#sec_223) |
|  || [**CHAPTER SUMMARY**](#20_Chaper10_split_001.xhtml#sec_224) |
|  || [**KEY CONCEPTS AND TERMS**](#20_Chaper10_split_001.xhtml#sec_225) |
|  || [**CHAPTER 10 ASSESSMENT**](#20_Chaper10_split_001.xhtml#sec_226) |
| [**PART THREE**](#21_Part3.xhtml) || [**Microsoft Windows OS and Application Security Trends and Directions**](#21_Part3.xhtml) |
| [**CHAPTER 11**](#22_Chaper11_split_000.xhtml) || [**Hardening the Microsoft Windows Operating System**](#22_Chaper11_split_000.xhtml) |
|  || [Understanding the Hardening Process and Mindset](#22_Chaper11_split_001.xhtml#sec_227) |
|  || [Strategies to Secure Windows Computers](#22_Chaper11_split_001.xhtml#sec_228) |
|  || [Install Only What You Need](#22_Chaper11_split_001.xhtml#sec_229) |
|  || [Security Configuration Wizard](#22_Chaper11_split_001.xhtml#sec_230) |
|  || [Manually Disabling and Removing Programs and Services](#22_Chaper11_split_001.xhtml#sec_231) |
|  || [Hardening Microsoft Windows Operating System Authentication](#22_Chaper11_split_001.xhtml#sec_232) |
|  || [Hardening the Network Infrastructure](#22_Chaper11_split_001.xhtml#sec_233) |
|  || [Securing Directory Information and Operations](#22_Chaper11_split_001.xhtml#sec_234) |
|  || [Hardening Microsoft Windows OS Administration](#22_Chaper11_split_001.xhtml#sec_235) |
|  || [Hardening Microsoft Servers and Client Computers](#22_Chaper11_split_001.xhtml#sec_236) |
|  || [Hardening Server Computers](#22_Chaper11_split_001.xhtml#sec_237) |
|  || [Hardening Workstation Computers](#22_Chaper11_split_001.xhtml#sec_238) |
|  || [Hardening Data Access and Controls](#22_Chaper11_split_001.xhtml#sec_239) |
|  || [Hardening Communications and Remote Access](#22_Chaper11_split_001.xhtml#sec_240) |
|  || [Authentication Servers](#22_Chaper11_split_001.xhtml#sec_241) |
|  || [VPNs and Encryption](#22_Chaper11_split_001.xhtml#sec_242) |
|  || [Hardening PKI](#22_Chaper11_split_001.xhtml#sec_243) |
|  || [User Security Training and Awareness](#22_Chaper11_split_001.xhtml#sec_244) |
|  || [Best Practices for Hardening Microsoft Windows OS and Applications](#22_Chaper11_split_001.xhtml#sec_245) |
|  || [**CHAPTER SUMMARY**](#22_Chaper11_split_001.xhtml#sec_246) |
|  || [**KEY CONCEPTS AND TERMS**](#22_Chaper11_split_001.xhtml#sec_247) |
|  || [**CHAPTER 11 ASSESSMENT**](#22_Chaper11_split_001.xhtml#sec_248) |
| [**CHAPTER 12**](#23_Chaper12_split_000.xhtml) || [**Microsoft Application Security**](#23_Chaper12_split_000.xhtml) |
|  || [Principles of Microsoft Application Security](#23_Chaper12_split_001.xhtml#sec_249) |
|  || [Common Application Software Attacks](#23_Chaper12_split_001.xhtml#sec_250) |
|  || [Hardening Applications](#23_Chaper12_split_001.xhtml#sec_251) |
|  || [Securing Key Microsoft Client Applications](#23_Chaper12_split_001.xhtml#sec_252) |
|  || [Web Browser](#23_Chaper12_split_001.xhtml#sec_253) |
|  || [E-mail Client](#23_Chaper12_split_001.xhtml#sec_254) |
|  || [Productivity Software](#23_Chaper12_split_001.xhtml#sec_255) |
|  || [File Transfer Software](#23_Chaper12_split_001.xhtml#sec_256) |
|  || [AppLocker](#23_Chaper12_split_001.xhtml#sec_257) |
|  || [Securing Key Microsoft Server Applications](#23_Chaper12_split_001.xhtml#sec_258) |
|  || [Web Server](#23_Chaper12_split_001.xhtml#sec_259) |
|  || [E-mail Server](#23_Chaper12_split_001.xhtml#sec_260) |
|  || [Database Server](#23_Chaper12_split_001.xhtml#sec_261) |
|  || [ERP Software](#23_Chaper12_split_001.xhtml#sec_262) |
|  || [Line of Business Software](#23_Chaper12_split_001.xhtml#sec_263) |
|  || [Case Studies in Microsoft Application Security](#23_Chaper12_split_001.xhtml#sec_264) |
|  || [Sporton International](#23_Chaper12_split_001.xhtml#sec_265) |
|  || [Monroe College](#23_Chaper12_split_001.xhtml#sec_266) |
|  || [Dow Corning](#23_Chaper12_split_001.xhtml#sec_267) |
|  || [Best Practices for Securing Microsoft Windows Applications](#23_Chaper12_split_001.xhtml#sec_268) |
|  || [**CHAPTER SUMMARY**](#23_Chaper12_split_001.xhtml#sec_269) |
|  || [**KEY CONCEPTS AND TERMS**](#23_Chaper12_split_001.xhtml#sec_270) |
|  || [**CHAPTER 12 ASSESSMENT**](#23_Chaper12_split_001.xhtml#sec_271) |
| [**CHAPTER 13**](#24_Chaper13_split_000.xhtml) || [**Microsoft Windows Incident Handling and Management**](#24_Chaper13_split_000.xhtml) |
|  || [Understanding and Handling Security Incidents Involving Microsoft Windows OS and Applications](#24_Chaper13_split_001.xhtml#sec_272) |
|  || [Formulating an Incident Response Plan](#24_Chaper13_split_001.xhtml#sec_273) |
|  || [Plan Like a Pilot](#24_Chaper13_split_001.xhtml#sec_274) |
|  || [Plan for Anything That Could Cause Loss or Damage](#24_Chaper13_split_001.xhtml#sec_275) |
|  || [Build the SIRT](#24_Chaper13_split_001.xhtml#sec_276) |
|  || [Plan for Communication](#24_Chaper13_split_001.xhtml#sec_277) |
|  || [Plan Security](#24_Chaper13_split_001.xhtml#sec_278) |
|  || [Revision Procedures](#24_Chaper13_split_001.xhtml#sec_279) |
|  || [Plan Testing](#24_Chaper13_split_001.xhtml#sec_280) |
|  || [Handling Incident Response](#24_Chaper13_split_001.xhtml#sec_281) |
|  || [Preparation](#24_Chaper13_split_001.xhtml#sec_282) |
|  || [Identification](#24_Chaper13_split_001.xhtml#sec_283) |
|  || [Containment](#24_Chaper13_split_001.xhtml#sec_284) |
|  || [Eradication](#24_Chaper13_split_001.xhtml#sec_285) |
|  || [Recovery](#24_Chaper13_split_001.xhtml#sec_286) |
|  || [Lessons Learned](#24_Chaper13_split_001.xhtml#sec_287) |
|  || [Incident Handling and Management Tools for Microsoft Windows and Applications](#24_Chaper13_split_001.xhtml#sec_288) |
|  || [Investigating Microsoft Windows and Applications Incidents](#24_Chaper13_split_001.xhtml#sec_289) |
|  || [Acquiring and Managing Incident Evidence](#24_Chaper13_split_001.xhtml#sec_290) |
|  || [Types of Evidence](#24_Chaper13_split_001.xhtml#sec_291) |
|  || [Chain of Custody](#24_Chaper13_split_001.xhtml#sec_292) |
|  || [Evidence Collection Rules](#24_Chaper13_split_001.xhtml#sec_293) |
|  || [Best Practices for Handling Microsoft Windows OS and Applications Incidents and Investigations](#24_Chaper13_split_001.xhtml#sec_294) |
|  || [**CHAPTER SUMMARY**](#24_Chaper13_split_001.xhtml#sec_295) |
|  || [**KEY CONCEPTS AND TERMS**](#24_Chaper13_split_001.xhtml#sec_296) |
|  || [**CHAPTER 13 ASSESSMENT**](#24_Chaper13_split_001.xhtml#sec_297) |
| [**CHAPTER 14**](#25_Chaper14_split_000.xhtml) || [**Microsoft Windows and the Security Life Cycle**](#25_Chaper14_split_000.xhtml) |
|  || [Understanding System Life Cycle Phases](#25_Chaper14_split_001.xhtml#sec_298) |
|  || [Agile Software Development](#25_Chaper14_split_001.xhtml#sec_299) |
|  || [Managing Microsoft Windows OS and Application Software Security](#25_Chaper14_split_001.xhtml#sec_300) |
|  || [Developing Secure Microsoft Windows OS and Application Software](#25_Chaper14_split_001.xhtml#sec_301) |
|  || [Implementing, Evaluating, and Testing Microsoft Windows OS and Application Software Security](#25_Chaper14_split_001.xhtml#sec_302) |
|  || [Maintaining the Security of Microsoft Windows OS and Application Software](#25_Chaper14_split_001.xhtml#sec_303) |
|  || [Microsoft Windows OS and Application Software Revision, Change Management, and End-of-Life Phaseout](#25_Chaper14_split_001.xhtml#sec_304) |
|  || [Software Development Areas of Difficulty](#25_Chaper14_split_001.xhtml#sec_305) |
|  || [Software Control](#25_Chaper14_split_001.xhtml#sec_306) |
|  || [Software Configuration Management (SCM)](#25_Chaper14_split_001.xhtml#sec_307) |
|  || [Best Practices for Microsoft Windows and Application Software Development Security Investigations](#25_Chaper14_split_001.xhtml#sec_308) |
|  || [**CHAPTER SUMMARY**](#25_Chaper14_split_001.xhtml#sec_309) |
|  || [**KEY CONCEPTS AND TERMS**](#25_Chaper14_split_001.xhtml#sec_310) |
|  || [**CHAPTER 14 ASSESSMENT**](#25_Chaper14_split_001.xhtml#sec_311) |
| [**CHAPTER 15**](#26_Chaper15_split_000.xhtml) || [**Best Practices for Microsoft Windows and Application Security**](#26_Chaper15_split_000.xhtml) |
|  || [Basic Rules of Microsoft Windows OS and Application Security](#26_Chaper15_split_001.xhtml#sec_312) |
|  || [Audit and Remediation Cycles](#26_Chaper15_split_001.xhtml#sec_313) |
|  || [Security Policy Conformance Checks](#26_Chaper15_split_001.xhtml#sec_314) |
|  || [Security Baseline Analysis](#26_Chaper15_split_001.xhtml#sec_315) |
|  || [OS and Application Checks and Upkeep](#26_Chaper15_split_001.xhtml#sec_316) |
|  || [Network Management Tools and Policies](#26_Chaper15_split_001.xhtml#sec_317) |
|  || [Software Testing, Staging, and Deployment](#26_Chaper15_split_001.xhtml#sec_318) |
|  || [Compliance/Currency Tests on Network Entry](#26_Chaper15_split_001.xhtml#sec_319) |
|  || [Trends in Microsoft Windows OS and Application Security Management](#26_Chaper15_split_001.xhtml#sec_320) |
|  || [**CHAPTER SUMMARY**](#26_Chaper15_split_001.xhtml#sec_321) |
|  || [**KEY CONCEPTS AND TERMS**](#26_Chaper15_split_001.xhtml#sec_322) |
|  || [**CHAPTER 15 ASSESSMENT**](#26_Chaper15_split_001.xhtml#sec_323) |
| [**APPENDIX A**](#27_Answer_split_000.xhtml) || [**Answer Key**](#27_Answer_split_000.xhtml) |
| [**APPENDIX B**](#28_Standard_split_000.xhtml) || [**Standard Acronyms**](#28_Standard_split_000.xhtml) |
|  || [**Glossary of Key Terms**](#29_Glossary.xhtml) |
|  || [**References**](#30_Reference.xhtml) |
|  || [**Index**](#31_Index.xhtml) |

**Preface**

**Purpose of This Book**

This book is part of the Information Systems Security & Assurance Series from Jones & Bartlett Learning (*[www.jblearning.com](http://www.jblearning.com)*). Designed for courses and curriculums in IT Security, Cybersecurity, Information Assurance, and Information Systems Security, this series features a comprehensive, consistent treatment of the most current thinking and trends in this critical subject area. These titles deliver fundamental information-security principles packed with real-world applications and examples. Authored by Certified Information Systems Security Professionals (CISSPs), they deliver comprehensive information on all aspects of information security. Reviewed word for word by leading technical experts in the field, these books are not just current, but forward-thinking—putting you in the position to solve the cybersecurity challenges not just of today, but of tomorrow, as well.

[Part 1](#09_Part1.xhtml) of this book focuses on new risks, threats, and vulnerabilities associated with the Microsoft Windows operating system. Particular emphasis is placed on Windows XP, Vista, 7, and 8 on the desktop, and Windows Server 2003, 2008, and 2012 versions. More than 90 percent of individuals, students, educators, businesses, organizations, and governments use Microsoft Windows, which has experienced frequent attacks against its well-publicized vulnerabilities. [Part 2](#12_Part2.xhtml) emphasizes how to use tools and techniques to decrease risks arising from vulnerabilities in Microsoft Windows operating systems and applications. [Part 3](#21_Part3.xhtml) provides a resource for readers and students desiring more information on Microsoft Windows OS hardening, application security, and incident management, among other issues.

**Learning Features**

The writing style of this book is practical and conversational. Step-by-step examples of information security concepts and procedures are presented throughout the text. Each chapter begins with a statement of learning objectives. Illustrations are used both to clarify the material and to vary the presentation. The text is sprinkled with Notes, Tips, FYIs, Warnings, and sidebars to alert the reader to additional and helpful information related to the subject under discussion. Chapter Assessments appear at the end of each chapter, with solutions provided in the back of the book.

Chapter summaries are included in the text to provide a rapid review or preview of the material and to help students understand the relative importance of the concepts presented.

**Audience**

The material is suitable for undergraduate or graduate computer science majors or information science majors, students at a two-year technical college or community college who have a basic technical background, or readers who have a basic understanding of IT security and want to expand their knowledge.

**Acknowledgments**

I would like to thank Jones & Bartlett Learning for the opportunity to write this book and be a part of the Information Systems Security & Assurance Series. I would also like to thank K Rudolph, the book’s technical reviewer and liaison between me and Jones & Bartlett Learning. Your input really made this a better book. And thanks so much to Ed Tittel for getting me involved in the first place and Carole Jelen with Waterside Productions for working so hard to make this happen.

*To God, who has richly blessed me in so many ways*

**About the Author**

**MICHAEL G. SOLOMON** (CISSP, PMP, CISM) is a full-time security speaker, consultant, and author, and a former university instructor who specializes in development and assessment security topics. As an IT professional and consultant since 1987, he has worked on projects for more than 100 major companies and organizations. From 1998 until 2001, he was an instructor in the Kennesaw State University Computer Science and Information Sciences (CSIS) department, where he taught courses on software project management, C++ programming, computer organization and architecture, and data communications. Solomon holds an MS in mathematics and computer science from Emory University (1998), and a BS in computer science from Kennesaw State University (1987). He is currently pursuing a PhD in computer science and informatics at Emory University with a research focus on confidentiality assurance in untrusted cloud environments. He has also authored and contributed to various security books, including *Security Strategies in Windows Platforms and Applications* (Jones & Bartlett Learning, 2011), *Auditing IT Infrastructures for Compliance* (Jones & Bartlett Learning, 2011), and *Computer Forensics JumpStart*, 2nd Edition (Sybex, 2011). Solomon coauthored *Information Security Illuminated* (Jones and Bartlett, 2005), *Security1 Lab Guide* (Sybex, 2005), *PMP ExamCram2* (Que, 2005), and authored and provided the on-camera delivery of LearnKey’s CISSP Prep and PMP Prep e-Learning courses.

**PART ONE**

**The Microsoft Windows Security Situation**

 
| [**CHAPTER 1**](#10_Chaper1_split_000.xhtml) || [**Microsoft Windows and the Threat Landscape**](#10_Chaper1_split_000.xhtml) |
| --- | --- |
| [**CHAPTER 2**](#11_Chaper2_split_000.xhtml) || [**Security in the Microsoft Windows Operating System**](#11_Chaper2_split_000.xhtml) |

**CHAPTER 1**

**Microsoft Windows and the Threat Landscape**

MICROSOFT WINDOWS is the most common operating system used today. More than 90 percent of computers use a Windows operating system. Microsoft provides operating system software for a wide variety of solutions, including both client and server computers. The latest Windows releases for server environments provide the most advanced features of the Windows product line.

Those releases contain new and updated security features. Each year brings new and unique threats to violate a system’s security. Whether the goal is to crash a system, access information without authorization, or disrupt normal system operation, attackers are finding much vulnerability to exploit.

It is important to understand the threats to Windows system security and the steps to protect it from attackers. The first step to creating and maintaining a secure environment is learning how to find and mitigate vulnerabilities and how to protect your systems.

**Chapter 1 Topics**

This chapter covers the following topics and concepts:

• What information systems security is

• What the tenets of information security are: the Confidentiality-Integrity-Availability (C-I-A) triad

• What mapping Microsoft Windows and applications into a typical IT infrastructure is

• What Microsoft’s End-User License Agreement (EULA) and limitations of liability are

• What common Windows threats and vulnerabilities are

• What Microsoft Windows vulnerabilities are, including Code Red, Conficker, and SQL Slammer

• What the discovery-analysis-remediation cycle is

• What common forms of attack on Windows environments are

**Chapter 1 Goals**

When you complete this chapter, you will be able to:

• Review key concepts and terms associated with information systems security

• Discuss the tenets of information security: C-I-A triad

• Explain how Microsoft Windows and applications map to a typical IT infrastructure

• List the main objectives of the Microsoft EULA

• Describe the limitations of liability in the Microsoft EULA

• Categorize Windows threats and vulnerabilities

• Recognize the anatomy of common Microsoft Windows vulnerabilities

• Summarize the discovery-analysis-remediation cycle

• Analyze common methods of attack

• Discuss emerging methods of attack

**Information Systems Security**

As computers become more complex, attackers become more sophisticated. **Attackers** are continually crafting new methods to defeat the most secure environments. The job of the security professional is becoming more difficult because of the complexity of systems and attacks. No single action, rule, or device can protect an information system from all attacks. It takes a collection of strategies to make a **computer environment** safe. This approach to using a collection of strategies is often called **defense in depth**. To maintain secure systems, it is important to understand how environments are attacked and how computer systems and networks can be protected. The focus here is specifically on securing the family of Microsoft Windows operating systems and applications.

The main goal in information security is to prevent loss. Today’s information is most commonly stored in electronic form on computers, also referred to as information systems. Although printed information, or hard copy, needs to be protected, this text addresses only issues related to protecting electronic information stored on information systems.

The two goals of protecting information from unauthorized use and making the information available for authorized use are completely separate and often require different strategies. Ensuring information is readily available and accessible for authorized use makes restricting the data from unauthorized use more difficult. Most information security decisions require careful thought to ensure balance between security and usability. Information that is secure is simply serving the purpose for which it is intended. It is not being used for unintended purposes.

Mechanisms used to protect information are called **security controls**. Security controls can be part of the operating system or application software setup, part of a written policy, or a physical device that limits access to a resource. There are two methods of categorizing controls. These aren’t the only methods used to classify controls and a single control may fit into more than one category. The first method looks at what the control is. Security controls belong to at least one of the following types:

• **Administrative controls** are written policies, procedures, guidelines, regulations, laws, and rules of any kind.

• **Technical controls** are devices or processes that limit access to resources. Examples include user authentication, antivirus software, and firewalls. Technical controls are also called **logical controls**.

• **Physical controls** are devices that limit access or otherwise protect a resource, such as fences, doors, locks, and fire extinguishers.

Security controls can also be categorized by the type of function they perform—also referred to as what they do. Here are the most common types of security control function types:

• **Preventive controls** prevent an action. Preventive controls include locked doors, firewall rules, and user passwords.

• **Detective controls** detect that an action has occurred. Detective controls include smoke detectors, log monitors, and system audits.

• **Corrective controls** repair the effects of damage from an attack. Corrective controls include virus removal procedures, firewall table updates, and user authorization database updates.

**Tenets of Information Security: The C-I-A Triad**

The practice of securing information involves ensuring three main attributes of information. These three attributes are often called the tenets of information security, or the **C-I-A triad**. Some security professionals may refer to it as the A-I-C triad, but the concept is the same. The three tenets of information security are:

**FIGURE 1-1** The C-I-A triad.

![image](OEBPS/Images/9781284031652_pg5.jpg)

• **Confidentiality**—The assurance that the information cannot be accessed or viewed by unauthorized users is **confidentiality**.

• **Integrity**—The assurance that the information cannot be changed by **unauthorized users** is **integrity**.

• **Availability**—The assurance that the information is available to **authorized users** in an acceptable time frame when the information is requested is **availability**.

Each of the tenets interacts with the other two, and in some cases, may cause conflict with other tenets ([Figure 1-1](#10_Chaper1_split_001.xhtml#ba-9781284031652-ch1fig1)). In this section, you will look at each tenet in more detail and how each one may cause conflicts with the others.

Confidentiality

In some cases, it is not enough to ensure information is protected from changes. Some information is private, privileged, business confidential, or classified and must be protected from unauthorized access of any type. Part of the value of confidential information is that it is available only to a limited number of authorized users. Some examples of confidential information include financial information, either personal or corporate; personal medical information; and secret military plans.

Confidentiality also introduces a need for an additional layer of protection. Sometimes, it is necessary to limit users with access to many resources by only allowing them to access specific resources on a need-to-know (NTK) basis. For example, a manager may have access to project documents that contain sensitive information. To limit the damage that could occur from accidents or errors, it is common to limit access to documents that directly relate to the manager’s projects only. Documents that do not directly relate to the manager’s projects are not accessible. That means that although a user possesses sufficient access for a resource, if the user does not have a specific need to know what a resource stores, the user still cannot access it.

A successful attack against confidential information enables the attacker to use the information to gain an inappropriate advantage or to extort compensation through threats to divulge the information.

Confidentiality has long been the subject of many types of legislation. Legislative bodies in many countries have enacted laws and regulations to protect the confidentiality of personal medical and financial information. Attorneys and physicians have long enjoyed the privilege of confidentiality when conversing with clients and patients. This assurance of confidentiality is crucial to the free flow of necessary information.

Integrity

Information is valid only when it is correct and can be trusted. The second tenet of information security ensures that information can be modified only by authorized users. Ensuring integrity means applying controls that prohibit unauthorized changes to information. Controls that ensure information integrity can be based on the user’s role. Other examples of integrity controls are security classification and user clearance.

Since information may change as a result of application software instructions, it is important that controls ensuring integrity extend to the application software development process. Regardless of the specific controls in use, the goal of integrity is to protect information from unauthorized changes.

Availability

Secure information is serving the purpose for which it was created. This means that secure information must be available when the information is requested.

Many attacks focus on denying the availability of information. One common type of attack that denies the availability of information is the denial of service (DoS) attack. This type of attack does not need to actually access or modify information. It prevents authorized users from accessing it. For example, an attack that denies access to [Amazon.com](http://Amazon.com)’s Web-based information would have a negative impact on sales. Amazon can’t afford to allow its information to be inaccessible for any length of time. Since so many businesses rely on available information to function properly, unavailable information poses a **risk** to the primary business functions.

Over a period of several months, from September 2012 to February 2013, a group of activists with hacking abilities, called **hactivists**, launched a series of attacks against several major U.S. bank computer systems. Hacktivists are behind more and more large-scale attacks, the intent of which is generally to bring attention to some political or social issue. The targets of these attacks included U.S. Bancorp, JPMorgan Chase, Bank of America, PNC Financial Services, and SunTrust Banks. Some customers were frustrated due to slow bank Web sites, while others were unable to reach their banks online at all. The banks learned from the attacks of this period and added new controls, but the hacktivists continued to find new vulnerabilities.

**Mapping Microsoft Windows and Applications into a Typical IT Infrastructure**

Satisfying the C-I-A triad requires more than just implementing controls on a single system. Today’s IT environments consist of a collection of computers and network devices connected to one or more networks. The collection of all computers, devices, and network components that make up an IT environment is called an IT infrastructure. An IT infrastructure diagram depicts the various components that work together to satisfy the organization’s information processing requirements ([Figure 1-2](#10_Chaper1_split_001.xhtml#ba-9781284031652-ch1fig2)). Some common infrastructure components include:

• Client platforms

• Network segments

• Network devices

• Server instances (often listed by function)

In most environments, the Microsoft Windows family of operating systems fills both the roles of client and server. Windows systems can operate as network devices, such as gateways or routers. It is more common to see either purpose-built devices or Windows servers providing device services. This text will focus on the client and server roles of Windows.

**FIGURE 1-2** A sample IT infrastructure.

![image](OEBPS/Images/9781284031652_pg7.jpg)

Windows Clients

Client systems exist to provide functionality to end users. These systems are often called customer-facing systems. Each specific application can be deployed as either a thin or a thick client.

Thin clients collect information from end users, send it to a server for processing, and display the returned results back to the end user. Most of the actual processing of the information occurs on a server. One of the most common examples of a thin client application is a Web browser.

Thick clients collect information from the end user and process some, or all, of the information locally. Commonly, the information is stored in a database running on a server. The client handles a large amount of the information processing work. Examples of thick client applications are legacy enterprise applications that provide accounting and manufacturing control.

The most common Windows operating systems in use on client computers are:

• Windows XP

• Windows Vista

• Windows 7

• Windows 8 (the newest Windows client)

Windows client computers are often general-purpose computers that provide end user applications for various purposes. It is common for a single Windows client computer to have a Web browser, an e-mail client, and an office productivity suite, as well as proprietary application software installed. Client computers are rarely single-purpose devices. This multirole functionality often makes securing these computers more difficult.

The newest version of Windows, Windows 8, recognizes that all clients are not just typical computers. Windows 8 introduces a new user interface that works well on desktops, laptops, and mobile devices. Tablet devices and smartphones are very popular, and Microsoft has responded with Windows 8. Windows 8 may look different, but the strategies to keep it secure are very similar to those of other Windows clients.

Windows Servers

Server computers exist in the IT infrastructure to provide specific types of services to client applications, either directly or indirectly. Common server applications may include Web servers, application servers, and database servers. Microsoft provides several different server products to satisfy various needs. In each version, it is common to tailor the specific applications installed on the server to customize the services provided. Microsoft markets several server packages; all based on the following Windows server products:

• **Windows Server 2003**—Many existing installations are still in operation.

• **Windows Server 2008 R2**—Currently the most common Windows operating system for servers, this server product is available in several editions for different applications. The main differences among editions are the number of processors, the amount of memory, and the high-availability features supported.

• **Foundation**—Cost-effective, entry-level server for small businesses

• **Standard**—More features than the Foundation edition and supports more common server functions for medium-sized businesses

• **Enterprise**—Advanced server for more performance and reliability than Standard edition

• **Datacenter**—Optimized for large-scale deployment using virtualization on small and large servers

• **Web**—Optimized Web application and services platform

• **HPC**—Windows High Performance Computing server for extensive scalability and interoperability between servers

• **Itanium**—Windows server specifically designed for the Intel Itanium high-performance processor

• **Windows Server 2012**—This server product is the latest server product available, in four different editions.

• **Foundation**—Cost-effective, entry-level server for small businesses

• **Essentials**—More features than the Foundation edition for most small to medium-sized businesses

• **Standard**—Suitable for most server functions, along with limited virtualization ability

• **Datacenter**—Designed for large-scale deployment on servers that support extensive virtualization

**Microsoft’s End-User License Agreement (EULA)**

A software license agreement must be accepted prior to the installation of any Microsoft Windows product. The software license agreement contains the Microsoft Software License Terms and is also referred to as the **End-User License Agreement (EULA)**. It is important to read the EULA before accepting it—don’t just blindly choose the “I accept” option. Each edition of Windows ships with a specific version of the EULA, so it is important to know the contents of the EULA for each edition of Windows present in your environment.

The Windows install folder or the Microsoft Web site contains the EULA. To find the EULA on a computer with Windows currently installed:

**1.** Click the Start button, and then, in the Start menu, click My Computer.

**2.** Under Hard Disk Drives, double-click the drive where Windows is installed. This is often the drive labeled (C:).

**3.** Double-click the Windows folder, double-click the System32 folder, double-click the en-US folder, double-click the Licenses folder, and then double-click the \_Default folder.

**4.** Double-click the folder that corresponds to the edition of Windows that’s installed on your computer, and then double-click License.

To find the EULA for any edition of Windows:

**1.** Open a Web browser, such as Internet Explorer.

**2.** Enter the following address: *[http://www.microsoft.com/about/legal/useterms/](http://www.microsoft.com/about/legal/useterms/).*

**3.** Enter the requested information for:

a. How the software was acquired

b. Product Name

c. Version

d. Language

**4.** Select the link for the desired EULA document.

There are a few sections of the Windows EULA that are of interest to security personnel. Make sure you read the following sections fully and are prepared to agree with Microsoft’s statements before accepting the agreement. [Table 1-1](#10_Chaper1_split_001.xhtml#ba-9781284031652-ch1tab1) highlights the sections of the EULA that are of most interest to security personnel.

In summary, the EULA states that it is your responsibility to secure all Windows platforms.

**Windows Threats and Vulnerabilities**

Securing any platform requires an understanding of its capability and the most likely ways the platform can be compromised. Simply understanding everything about Windows will not make your systems secure. The main goal in securing an operating system and application environment is recognizing risks and implementing controls to mitigate the risks. In this section, you will look at risks and how to handle them.

A risk is defined as any exposure to a threat. A **threat** is any action that could lead to damage, disruption, or loss. A threat by itself is not necessarily dangerous. For example, lighting a fire could be considered a threat. In the right environment, such as on a camping trip or in a fireplace, lighting a fire is desirable. However, lighting a fire in an operational datacenter is not desirable at all. Such an action will likely result in business process disruption and possibly even damage.

For damage to occur, there has to be a threat, such as lighting a fire, in a vulnerable environment, such as in a datacenter. Attackers look for **vulnerabilities**, or weaknesses, in the operating system and application software. Once vulnerabilities are discovered, the next step is to devise an attack that will exploit the weakness. A successful attack is defined as one that realizes, or carries out, a threat against vulnerabilities.

It is important to understand the most common methods of attack in a Windows environment. This understanding allows you to devise controls that limit an attacker’s ability to realize threats. The controls you implement can directly address vulnerabilities or restrict an attacker’s ability to get into a position to realize a threat. Either way, by breaking the ability of an attacker to carry out a threat against a vulnerability, you make your environment more secure.

| **TABLE 1-1** Security-related sections of the Microsoft EULA. |
| **EULA SECTION** || **DESCRIPTION** |
| Potentially unwanted software || Windows Defender is a program that will search for and, optionally, remove spyware and other unwanted software. If turned on, Windows Defender may identify software as harmful and automatically remove it. This behavior may result in the removal of software that is necessary to proper system operation. |
| Internet-based services || Microsoft provides Internet-based services with Windows and may transmit information. This section of the EULA provides details of services and potential information that may be transmitted, i.e., system detail information resulting from a crashed program. Windows will optionally send information to Microsoft in an effort to find a resolution for the problem that caused the program to crash. |
| Limitation and exclusion of damages || Only the purchase price of Windows can be recovered, regardless of any damages incurred as a result of a Windows fault or incident. This clause alone provides an excellent reason for security personnel to protect organizations by securing all Windows environments. |
| Exclusions from warranty || The cost of a Windows license cannot be recovered if an organization suffers damages caused by its personnel. |
| Limitation and exclusion of damages for breach of warranty || If any part of the EULA is breached, damages cannot be recovered. |
|   ||   |

**Anatomy of Microsoft Windows Vulnerabilities**

Consider a few well-known Windows vulnerabilities. It is instructive to examine how real vulnerabilities have been exploited by attackers. Such analysis helps to understand the nature of vulnerabilities and methods of protecting systems from attackers. All of the following attacks used **worms**. Worms are standalone **malicious software** programs that actively transmit themselves, generally over networks, to infect other computers.

Code Red

The Code Red worm provides a sobering warning on how to secure Windows environments. The worm was first observed on July 13, 2001, as malicious software that attacked Microsoft Internet Information Services (IIS) Web server software. Once a vulnerable IIS system was attacked, Code Red would do the following:

• Deface Web sites with the phrase “HELLO! Welcome to *[http://www.worm.com](http://www.worm.com)*! Hacked By Chinese!”

• Attempt to spread the worm to additional Web servers

• Wait 20–27 days and launch DoS attacks against specific IP addresses

The worm attacked a vulnerability of IIS by creating a buffer overflow. A buffer overflow is a vulnerability where data is supplied that is larger than the program expects—but the program accepts it anyway. In some cases, specially designed data can cause the program to execute instructions that were never intended. Buffer overflow vulnerabilities are well known, but still exist in software due to a lack of solid design and testing. This buffer overflow allowed Code Red to cause instructions to execute that would produce the desired worm behavior.

The most interesting aspect of Code Red is that a successful attack depended on a vulnerability for which a patch had been released over a month before Code Red appeared. Systems with the patch applied were not vulnerable to the attack. It’s ironic that it appears that the Code Red designers may have learned about the vulnerability from the patch documentation.

SQL Slammer

The SQL Slammer worm was another famous worm to exploit well-known buffer overflow vulnerability. SQL Slammer first appeared on January 25, 2003, and spread rapidly. The worm exploited a bug in Microsoft’s SQL Server and Desktop Engine database products.

SQL Slammer is a very small, simple worm. It is only 376 bytes and fits into a single network packet. Since the worm uses User Datagram Protocol (UDP), it can propagate to a large number of other computers quickly without maintaining a connection. To make matters worse, the Desktop Engine product is installed on many client computers as a supporting service and many users do not even know it is there. The transparent nature of the Desktop Engine meant that most of the instances were unprotected.

When the SQL Slammer worm runs on a vulnerable computer, it creates a list of IP addresses and quickly sends itself to the target computers. This process is very fast and can result in a large number of network packets in a network. This large concentration of UDP packets generated as more and more computers are infected causes routers to slow down or even crash under the load. This saturation of routers is a denial of service (DoS) attack on network resources.

Similar to its response to the Code Red worm, Microsoft had released a patch for the vulnerability SQL Slammer exploited six months prior to the first detection of the worm.

![image](OEBPS/Images/war.jpg)**WARNING**

Computers with the patch applied were not vulnerable to SQL Slammer, but could still be affected if other computers on the same network were vulnerable and attacked.

Conficker

Conficker, also known as Downadup, is another worm that targets Microsoft Windows computers. Conficker is the newest worm of the three, first observed in November 2008. There are at least five variants of Conficker. Each successive variant is more sophisticated than the previous one.

The initial Conficker attack depended on a network service vulnerability. This vulnerability allowed the worm to infect systems and spread throughout the local network to other trusted computers. Microsoft released an emergency patch to address the initial vulnerability, but Conficker had already been updated to propagate using removable media as well as networks. Conficker does not employ new or unknown attack methods. The methods Conficker uses are largely well known. Conficker is unique because it combines many aggressive techniques in a manner that makes it very difficult to eradicate.

Conficker has proven to be a pervasive worm and difficult to contain. Microsoft has released a removal guide for the worm using its own Malicious Software Removal Tool. Microsoft also strongly recommends that the infected systems be patched with the latest security patches after worm removal.

**Discovery-Analysis-Remediation Cycle**

The process for addressing attacks follows a recurring three-step process. This process is referred to as the discovery-analysis-remediation cycle ([Figure 1-3](#10_Chaper1_split_001.xhtml#ba-9781284031652-ch1fig3)). This process may occur exclusively within your organization, outside your organization, or both.

**FIGURE 1-3** Discovery-analysis-remediation.

![image](OEBPS/Images/9781284031652_pg13.jpg)

| **TABLE 1-2** Popular repositories for security vulnerabilities and exposures. |
| **RESOURCE** || **ADDRESS** || **COMMENTS** |
| Common Vulnerabilities and Exposures (CVE) || *[http://cve.mitre.org/](http://cve.mitre.org/)* || Dictionary of publicly known vulnerabilities and exposures |
| National Vulnerability Database || *[http://nvd.nist.gov/](http://nvd.nist.gov/)* || CVE data plus additional resources |
| United States Computer Emergency Readiness Team (US-CERT) || *[http://www.us-cert.gov/](http://www.us-cert.gov/)* || Numerous security alerts and bulletins |
|   ||   ||   |

Discovery

The first step in responding to an attack is to know an attack has occurred or is occurring. Discovering an attack is often more difficult than it would seem. Experienced attackers know that the success of an exploit often depends on the amount of time vulnerable systems are exposed. Once an attack starts, a common goal of attackers is to become as inconspicuous as possible. Keeping a low profile often allows an attack to become more successful as time passes.

It is important to recognize what “normal” looks like. Often the only way to know something is not right is to compare suspect activity with normal activity. The most common method of accomplishing this is to use activity and monitoring logs. Log files often contain evidence to detect that something abnormal has happened.

Analysis

Once abnormal activity is identified, the next step is to analyze it. Not all suspect activity is bad. Some activity has a rational explanation. Perhaps the database server was under an unusual load due to too many users running large reports. Load balancing could have been disabled so that all network activity was sent through a single device. Both of these cases are abnormal but do not indicate attacks. The analysis phase includes validating suspect activity as abnormal and then figuring out what is causing it.

The next step is to consult current vulnerability and security bulletin databases to see if others are experiencing the same activity. There are many security-related databases that serve this purpose, but several repositories are the most popular and commonly used to research vulnerabilities. [Table 1-2](#10_Chaper1_split_001.xhtml#ba-9781284031652-ch1tab2) lists the most common repositories for security vulnerabilities and exposures.

Remediation

The third step in the cycle is to remediate the activity. Simply put, that means to contain any damage that has occurred, recover from any loss, and implement controls to prevent a recurrence.

The particular steps to take in any of these phases depend on the nature of the attack. Most vulnerabilities and exposures that are documented in a public database are accompanied by suggested remediation steps.

It is possible to trace back from the discovery event that indicated abnormal activity occurred. Controls that prevent any new activity that results in the abnormal activity may be a good place to start. Ensure that any new controls comply with operational requirements and don’t interfere with critical business processes.

**Common Forms of Attack**

Attacks on Windows platforms can take on many forms. It is common to see several types of attacks combined to accomplish the attacker’s goal. [Table 1-3](#10_Chaper1_split_001.xhtml#ba-9781284031652-ch1tab3) contains a brief list of the most common types of attacks on any information systems.

| **TABLE 1-3** Common information system attack types. |
| **ATTACK TYPE** || **DESCRIPTION** |
| Trojan horse || A malicious program that tricks users into running it—often through social engineering |
| Backdoor || Programs that allow unauthorized access |
| Denial of service || Any action that dramatically slows down or blocks access to one or more resources |
| Robot/intermediary process || A process that runs on one target computer that launches attacks on other computers |
| Unprotected Windows Share || A situation that allows attackers to install tools, including malicious software |
| Mobile code || Java/ActiveX malicious code that is sent to clients before being executed |
| Cross-site scripting || Specially crafted malicious code used to attack Web applications |
| Packet sniffing || The process of collecting network messages as they travel across a network in hopes of divulging sensitive information, such as passwords |

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Securing Windows operating systems and applications is not easy, but it is possible. It is necessary for an organization to successfully meet its operational goals.

The first step in securing a Windows environment, and then maintaining a secure environment, is to understand how your computers are vulnerable. From there, a study of the most common attacks against vulnerabilities leads to steps that respond to threats and make your systems more secure. Learning about past attacks against information systems is more than a technical history lesson. It is a study of techniques attackers use to compromise systems.

In spite of the increasing sophistication of attackers, most current attacks are either a resurgence of, or a variation on, earlier attack methods. Close attention to previous exploits makes you far more agile to respond to the next attack.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Administrative control**

**Attacker**

**Authorized user**

**Availability**

**C-I-A triad**

**Computer environment**

**Confidentiality**

**Corrective control**

**Defense in depth**

**Detective control**

**End-User License Agreement (EULA)**

**Hacktivist**

**Integrity**

**Logical control**

**Malicious software**

**Physical control**

**Preventive control**

**Risk**

**Security control**

**Technical control**

**Threat**

**Unauthorized user**

**Vulnerability**

**Worm**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 1 ASSESSMENT**

  **1.** Which of the following is the best description of the defense-in-depth strategy?

A. Hiding protected resources behind multiple firewalls

B. Using multiple layers of security controls to protect resources

C. Fully securing the most important resources first

D. Staying current on as many known attacks as possible

  **2.** What is the main goal of information security?

A. Protect information from unauthorized use

B. Catch as many unauthorized users as possible

C. Protect information from unauthorized modification

D. Stop anonymous users from accessing information

  **3.** Does turning off a computer make the information it contains secure?

A. Yes, because no unauthorized user can access information on a computer that is turned off.

B. No, because the information might be copied somewhere else.

C. Yes, because aggressive actions always result in more secure systems.

D. No, because secure data must still be available to authorized users.

  **4.** Which of the following is the best description of a security control?

A. A mechanism to stop attacks before they occur

B. A rule that defines acceptable use of a computer

C. A mechanism that protects a resource

D. A device that detects unusual activity

  **5.** Which of the following could be classified as a logical control?

A. Firewall

B. Fence

C. Acceptable use policy

D. Smoke detector

  **6.** Which of the following could be classified as a detective control?

A. Password

B. Door

C. Acceptable use policy

D. Log monitor

  **7.** Which of the tenets of information security most directly serves the needs of authorized users?

A. Availability

B. Integrity

C. Confidentiality

D. None of the above

  **8.** Which of the tenets of information security is most related to the need-to-know property?

A. Availability

B. Integrity

C. Confidentiality

D. None of the above

  **9.** Where is the most likely place a database management system would run?

A. Network device

B. Server

C. Thin client

D. Thick client

**10.** Which Microsoft Windows Server 2008 R2 edition would be most appropriate for large-scale deployment using extensive virtualization?

A. Datacenter

B. HPC

C. Enterprise

D. Web

**11.** According to the Microsoft EULA, what is the extent of the damages that can be recovered due to a Windows fault?

A. Nothing

B. The price paid for the software license

C. Actual damages incurred

D. Actual damages incurred plus the cost of the software license

**12.** Which of the following is the best definition of a threat?

A. Any exposure to damage

B. A weakness that allows damage to occur

C. An action that exploits a weakness

D. Any action that could lead to damage

**13.** What worm was released in 2001 and primarily defaced Web sites?

A. SQL Slammer

B. Conficker

C. Code Red

D. Melissa

**14.** What term describes a malicious software program that users are tricked into running?

A. Trojan horse

B. Worm

C. Virus

D. Phishing message

**15.** Which of the following defines the cycle used to address Windows threats and vulnerabilities?

A. Plan-do-review

B. Discovery-analysis-remediation

C. Design-implementation-verification

D. Detection-containment-eradication

**CHAPTER 2**

**Security in the Microsoft Windows Operating System**

ONE OF THE MORE DIFFICULT TASKS when securing any computer system or network is identifying where to start. There are many components in any computing environment. Each component is a potential point of attack. Since the operating system provides the ability for software and hardware to interact, it is a good starting point for securing an entire environment. On any computer, the operating system enables software to access physical resources. For example, it is the operating system that governs how any application actually reads from, or writes to, a physical disk. Consequently, the operating system is a prime candidate for attack and a valuable resource to protect.

From an attacker’s point of view, a compromised operating system provides easy access to protected information. Compromising operating system controls gives the attacker the ability to remove evidence of attacks and “clean up” any leftover log entries or other traces of the attack. A secure operating system is the basis of a secure environment.

In this chapter, you will learn about the Windows operating system architecture and controls to ensure system security. You will also learn how attackers search for, find, and exploit operating system vulnerabilities. With the knowledge of how attackers operate, you’ll be able to identify and implement the right controls to secure your environment.

**Chapter 2 Topics**

This chapter covers the following topics and concepts:

• What the organization of the operating system components and architecture is

• What the basic Windows operating system architecture is

• What access controls and authentication are

• What security tokens, rights, and permissions are

• What users, groups, and Active Directory are

• What Windows attack surfaces and mitigation are

• What fundamentals of Microsoft Windows security monitoring and maintenance are

**Chapter 2 Goals**

When you complete this chapter, you will be able to:

• Distinguish operating system components from architecture

• Describe the basic Windows OS architecture

• Discuss access controls and authentication

• Explain security tokens, rights, and permissions

• Research the features of several common security tokens

• Identify the purposes of users and groups

• Discuss the features of directory services

• Analyze the business advantages and challenges of Active Directory

• Describe Windows attack surfaces and mitigation

• Summarize the fundamentals of Microsoft Windows security monitoring and maintenance

**Operating System Components and Architecture**

In spite of the reference to an “operating system” as a single entity, an operating system is not a single huge program. An operating system is actually a collection of many programs working together, along with data, to provide access to physical resources. The goal of secure information can simply be expressed as simultaneously ensuring both of the following situations:

**1.** All required information is available to authorized users.

**2.** No information is available to unauthorized users.

Although these two basic situations appear to be clear and straightforward, simultaneously ensuring both can be challenging. A **control** is any mechanism or action that prevents, detects, or addresses an attack. Once security controls are in place, attackers must identify methods to compromise the controls and gain the privileges of an authorized user. The methods attackers use will rely on one or more vulnerabilities. Your goal is to identify and mitigate as much vulnerability as possible to deny the opportunity for an attacker to realize a threat.

The first step in planning how to secure the operating system is to understand the purpose of various operating system components. Each operating system component, and the communication between components, can be a potential point of attack. There are many different operating systems in use today, and often multiple versions of each one; however, there are components and services that are common among them.

The Kernel

The central component of most operating systems is the kernel. The **kernel** is the part of the operating system that may reside partially in memory and provides the backbone of the operating system’s services ([Figure 2-1](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2fig1)). The classic definition of the kernel states that the entire kernel resides in memory. Today’s more complex operating system kernels are made up of both the main memory-resident components and external loadable modules. The use of loadable modules reduces the kernel’s memory footprint. The kernel provides access to physical resources and often runs other operating system programs to complete a task. The memory-resident kernel code will directly handle access to the CPU, where efficiency is crucial. In other cases, where flexibility is more important, the kernel will run device driver programs to handle physical resource access. The second approach is slower but makes it easy for the operating system to support a wide variety of hardware from different vendors. All that is needed is a device driver program for the operating system to support a new device.

![image](OEBPS/Images/war.jpg)**WARNING**

Of course, each new device driver means a new potential vulnerability and possible point of attack. Ensure your systems do not have device drivers installed for retired devices.

**FIGURE 2-1** Operating system kernel.

![image](OEBPS/Images/9781284031652_pg22.jpg)

Many current operating systems actually implement **microkernel** architecture. A microkernel only implements the minimal required functionality in the memory-resident portion of the operating system, such as memory management, interprocess communication, and process scheduling. Other necessary functionality is supported by external programs. The main difference between internal and external programs is the privilege level at which each runs. A pure microkernel allows only memory-resident components to run at kernel, or maximum privilege, mode.

The kernel also includes areas of memory reserved for the operating system data structures. One example of an operating system data structure is the process, or task table. The process table contains one entry for each running process. Each operating system stores different process properties, but the basic information in the process table is consistent. [Figure 2-2](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2fig2) shows a few of the types of information the operating system maintains for processes.

** ![image](OEBPS/Images/note.jpg)NOTE**

Some operating system implementations also refer to the maximum privilege mode as supervisor mode.

**FIGURE 2-2** Windows process table contents.

![image](OEBPS/Images/9781284031652_pg22-1.jpg)

One common process property is the mode in which a process is run. Processes generally run in either **user mode** or **supervisor mode**. Processes run in supervisor mode can perform more tasks and access more restricted parts of the computer system. One way for an attacker to access a protected resource is to modify the process table entry and change a user mode process to supervisor mode. The process table is only one example of a kernel data structure that must be secured from changes. However, processes running in user mode should be able to view the information in the process table to see what is running at any point in time. The kernel keeps track of what processes can do and what they can’t.

Operating System Components

Operating systems contain far more than just the kernel. The kernel provides core services of the operating system and calls external programs to provide many more operating system services. [Table 2-1](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2tab1) contains a list of general services most current operating systems provide.

| **TABLE 2-1** Operating system general services. |
| **OPERATING SYSTEM SERVICE** || **DESCRIPTION** |
| Program/process management || The operating system manages locating, loading, and actually executing all programs. It handles memory allocation, CPU scheduling, and providing the necessary environment for each program. |
| Input and output || Nearly every program requires input and produces output. The operating system hides the details of the physical hardware and provides programs with the ability to process input and output. |
| File system || The operating system also provides access to long-term storage, such as disk drives, and helps to organize the information to make it easily and efficiently accessible. |
| Communication || Programs often need to communicate with other programs, both locally and on other computers. The operating system provides the support for exchanging information between programs. |
| Error detection and alerts || The operating system is responsible for monitoring activities that occur within the computer and for responding when errors occur. |
|   ||   |

From a security view, the most important concept of this section is that the operating system is the collection of programs that control access to the physical hardware. Since information is stored and transmitted on physical hardware, ensuring the security of protected information starts with ensuring the security of the operating system.

**Basic Windows Operating System Architecture**

The Microsoft Windows operating system has changed a lot from the simple personal computer operating system, DOS. It has grown from a single product offering to a full family of products to meet different needs. The current versions of Windows address a wide variety of computing needs, from portable devices and workstations to enterprise-class, high-performance platforms. The Windows operating system is designed to be a modular system to provide the widest variety of services for most platform requirements.

The current versions of client and server operating systems, Windows 7, Windows 8, Windows Server 2008 R2, and Windows Server 2012, are all based on the Windows NT code base. Windows NT was Microsoft’s first operating system designed with security in mind. The first commercial version of Windows NT was version 3.1, released in 1993. At the time, Windows NT was a ground-breaking product from Microsoft. Several versions of Windows share a common ancestry back to Windows NT.

Based on the same kernel, the current Windows operating systems are designed with modified microkernel architectures. The operating system design allows many system functions to be implemented as external programs that run in kernel mode. In a pure microkernel architecture, external programs are not allowed to run in kernel mode. Because of the modular nature of Windows, major components can be removed, replaced, or enhanced without having to rewrite the entire operating system. This design allows Microsoft to create different versions of the same base operating system to provide specific services for different client and server environments.

** ![image](OEBPS/Images/note.jpg)NOTE**

Windows 7 and Windows Server 2008 R2 are both based on the NT 6.1 kernel. Windows 8 and Windows Server 2012 are both based on the NT 6.2 kernel.

Windows Run Modes

The architecture of the Windows operating system consists of two main layered components—user mode programs and kernel mode programs. Kernel mode programs run in a privileged mode, also called kernel or supervisor mode, and interact closely with the physical hardware. User mode programs interact with both users and kernel mode programs. [Figure 2-3](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2fig3) shows the basic architecture of a Windows operating system.

**FIGURE 2-3** Windows operating system components.

![image](OEBPS/Images/9781284031652_pg25.jpg)

Kernel Mode

Programs running in kernel mode have complete access to the computer’s hardware and system services. This level of access is needed by the operating system and provides an attractive target for attackers.

[Table 2-2](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2tab2) shows the main kernel mode program components.

**technical TIP**

One common goal of attackers is to run a program of their choice in kernel mode. At that level of privilege, an attacker can pretty much own a computer. Pay special attention to any vulnerability you encounter that could allow an attacker to escalate privilege to kernel mode.

| **TABLE 2-2** Windows kernel mode components. |
| **COMPONENT** || **DESCRIPTION** |
| **Hardware Abstraction Layer (HAL)** || The HAL provides the actual access to physical hardware. All other kernel mode programs interact with hardware through the HAL. This allows Microsoft to support multiple hardware platforms by just writing different HAL modules, instead of rewriting all operating system programs. |
| Kernel mode drivers || Kernel mode drivers provide user programs and other kernel mode programs access to individual hardware devices, through the HAL. These drivers provide the translation to allow other programs to access devices as file objects. |
| Microkernel || The microkernel is the memory-resident portion of the operating system that provides the core functionality of operating system functionality, including CPU synchronization, process thread/interrupt scheduling, and exception handling. |
| Executive || The executive is at the “highest level” of the kernel mode programs. It provides services, such as managing objects, I/O, security, and process management. User mode programs interact with the operating system via the executive. |

| **TABLE 2-3** Windows user mode components. |
| **COMPONENT** || **DESCRIPTION** |
| Environment subsystem || The Environment subsystem provides the ability to run programs written for different operating systems, including previous Windows versions and UNIX. |
| Integral subsystem || The Integral subsystem handles the user mode functions on behalf of the environment subsystem, including logon and access control, network access, and providing network services. |

User Mode

All non-kernel mode programs run under user mode. This includes application programs and the user mode layer of Windows. The Windows user mode layer programs handle all user interaction and processing requests, and pass I/O requests to the necessary kernel mode drivers, using the executive. [Table 2-3](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2tab3) lists the two main user mode program components.

**Access Controls and Authentication**

All computer users, including attackers, need to establish access to a computer system before accessing its resources. The operating system is responsible for providing access to authorized users while denying access to unauthorized users. This process of providing and denying access is called **access control**. As developers of operating systems have become more concerned with security issues, access control has matured with each new operating system release. Access control is a multi-step process, starting with **identification** and **authentication**. Regardless of the methods used, the operating system needs to identify the user asking for access to a resource. Most often, the user provides a username (or user ID). A username alone is not sufficient to use as a basis for granting access to resources, however. Anyone can claim to be any user. There must be a process that validates that a user is authentic.

The authentication process ensures that users are who they claim to be. There are many methods to authenticate users. The most common method in use is the password. Although anyone can claim to be a particular user, no one else but the real user should know the user’s password. The ability to provide both the username and password provides the authentication that the user is valid and authentic.

![image](OEBPS/Images/war.jpg)**WARNING**

Attackers know that passwords are common and many people have trouble memorizing the complex ones. So an attacker will likely explore words and numbers that are easily remembered, such as birthdays, anniversaries, and names of pets or children. Another favorite attack is to walk around an office and look for sticky notes on monitors and under keyboards. Many users write down passwords there.

Authentication Methods

Authentication methods aren’t limited to just passwords—they can be one of three types. Each type of authentication is useful in different applications and has strengths and weaknesses. [Table 2-4](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2tab4) lists the three authentication types: **Type I**, **Type II**, and **Type III authentication**.

Regardless of the type, or types, of authentication used, the authentication system performs the following tasks:

• Collects identification credentials, such as a username.

• Collects authentication credentials, such as a password.

• Finds the stored information that corresponds to the supplied credentials in the user list, often in an authentication database.

• Compares the stored credentials with the supplied credentials. If they match, the user is authenticated.

 
| **TABLE 2-4** Authentication types. |
| --- |

![image](OEBPS/Images/9781284031652_pg28.jpg)

The strongest authentication comes from using more than one type at the same time. Using two types of authentication is called **two-factor authentication** and using more than two types is called **multifactor authentication**. Any operating system or application that requests more than one response during authentication is using two-factor or multifactor authentication. Using more than a single authentication type strengthens the process by increasing the difficulty of impersonating a valid user.

Access Control Methods

Once a user is identified and properly authenticated, the operating system can grant or deny access based on different rule sets. Access control doesn’t only apply to users. Any user or program that requests access to a resource is called the access **subject**. The resource to which the subject requests access is called the access **object**. Using these terms, access control is the process of granting or denying subjects access to specific objects.

The most common types of access control rules are **discretionary access control (DAC)**, **mandatory access control (MAC)**, and **role based access control (RBAC)**. DAC strategies are defined primarily at the user, or subject, level. Each object has a defined owner and the owner has complete control over which users can access the object. In an operating system environment, this means access is granted to resources based on the user’s settings. Windows extends this concept to allow object properties that can further restrict access. While this approach is simple to define, it can be challenging to maintain in large environments with many users.

The next main type of access control is MAC. A familiar MAC implementation is used in military and government environments. In such an environment, all data objects are labeled with a specific **classification**. Government classifications are Unclassified, Restricted, Confidential, Secret, and Top Secret. Likewise, all subjects are granted a specific **clearance**. A subject must hold a clearance at, or above, the classification level of the desired object to access it. In most environments, subjects must also demonstrate a specific “need to know.”

The final type of access control is RBAC. In one point of view, RBAC extends, or generalizes, DAC. Object access is defined by role, as opposed to individual users. Each user is assigned one or more roles. The roles to which a user is assigned define which objects that user (subject) can access. Most operating systems, including Windows, do not directly use RBAC, but use a combination of DAC and RBAC. This combination of access control methods is implemented using both user- and user group–based permissions.

**Security Access Tokens, Rights, and Permissions**

In a Windows environment, each local system defines local users and groups during the installation process. You can add more local users and groups at any time using the Computer Management tool.

The Local Users and Groups section of the Computer Management tool allows you to add, remove, and manage local users and groups. This tool is most commonly used to create new users and groups, and to associate users with groups. [Figure 2-4](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2fig4) shows the Local Users and Groups section of the Computer Management tool.

**technical TIP**

Here’s how to open the Computer Management tool:

**1.** Select Start.

**2.** Right-click Computer to open the Computer context menu.

**3.** Select Manage.

**FIGURE 2-4** Computer Management tool with open Local Users and Groups.

![image](OEBPS/Images/9781284031652_pg30.jpg)

Security Identifier

Each local user and group in Windows has a unique **security identifier (SID)**. Windows uses the SID to identify users and groups, not the names. Once you create a local user or group, the SID remains the same, even if you change the user or group name. There are several well-known users and groups that are defined for all Windows machines, but aside from the Microsoft-defined SIDs, all other SIDs are unique to a local machine. [Table 2-5](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2tab5) lists a few of the Windows well-known SIDs.

| **TABLE 2-5** Well-known SIDs. |
| **WELL-KNOWN SID** || **STRING VALUE** || **IDENTIFIES** |
| Null SID || S-1-0-0 || Group with no members, often used when a SID is not known |
| World || S-1-1-0 || Group that includes all members |
| Local || S-1-2-0 || Users who log on local terminals |
| Creator Owner ID || S-1-3-0 || SID replaced by the SID of the user who created a new object |
| Creator Group ID || S-1-3-1 || SID replaced by the primary group SID of the user who created a new object |
|   ||   ||   |

If you create a user named “Fred” on two different Windows computers, each account will have a different SID. To Windows, the users are completely different, even though they share the same username. This uniqueness between machines makes it difficult to synchronize security settings among multiple standalone computers.

Every time a Windows user logs on, the operating system fetches the user’s SID and the SIDs for all groups to which the user is assigned. The operating system also looks up any local rights for this computer. All of the SIDs and local rights are written to an ID object called your Security Access Token (SAT). Your session’s SAT is attached to all your processes. When you run any process, Windows looks at the SAT and any defined access control information for resources to decide whether to grant or deny access to any requested resources.

Access Rules, Rights, and Permissions

Defining local users and groups is only the first part of the access control implementation process. Windows allows you to associate specific rights and permissions to each user that tell Windows what a user can do. User **rights** define tasks that a user is permitted to carry out, such as take ownership of objects or shut down the computer. **Permissions** define what a user can do to a specific object, such as read or delete the object. Windows stores access rules, or permissions, for resources (objects) in **access control lists (ACLs)**. Each object has an associated ACL and can be used to allow or deny access to the object by user or group. The most common use of ACLs to the general user is to protect files or folders. The Properties dialog box of Files and Folders contains a Security page, which allows you to change the object’s access permissions for specific users or groups. The collection of access permissions for each object is called the object’s ACL. Windows uses the SAT attached to the currently running process and the ACLs defined for a requested resource to decide whether to grant or deny the requested access.

**Users, Groups, and Active Directory**

Today’s computing environments are quickly becoming more diverse and integrated. Fewer environments are composed of isolated and unconnected personal computers. Windows environments, both home and office, are becoming more dependent on shared resources. Even the smallest home networks commonly share printers, storage devices, and network access devices. While defining access permissions for small home networks is fairly easy, the same cannot be said for larger business networks.

Workgroups

In a business network, there may be dozens, hundreds, or even thousands of computers. It is desirable to allow users to access network resources from multiple computers attached to the network. By default, Windows allows computers to share resources by creating a workgroup. A workgroup simply allows standalone computers to “see” each other’s shared resources. Common shared resources include files, folders, and printers. Each resource can be shared or hidden, and the access to each resource can be controlled by user and group permissions.

So far, workgroups sound good. The main problem with Windows workgroups is that each computer is still defined as a standalone computer. That means users and groups must be defined on multiple computers. In fact, if you want all users to have access on all computers in the workgroup, you have to add the local users on every computer. On small networks, this may seem OK at first, but maintenance can quickly get out of hand. Since all user and group accounts in a workgroup are local accounts, every change to security permissions must be applied to every computer. Administration of workgroups with more than 10 computers can quickly become too difficult to remain viable.

Active Directory

Microsoft offered a solution to local users and groups in the original Windows NT operating system. All Windows operating systems since Windows NT have the ability to share user and group definitions. Many operating systems support a generic capability to share such information, called directory services. This functionality has matured into a core Windows feature, called **Active Directory**. Instead of having to define users and groups locally on each computer, Active Directory allows users and groups to be defined once and shared among multiple computers. You get to define the limits of how many computers share users and groups by defining domains. The actual database of shared users and groups is stored on one or more computers designated as domain controllers. There are many more features of Microsoft Active Directory, but its main feature is the ability to define identity and **authorization** permission that can be shared among multiple computers within one or more domains. This capability greatly simplifies security administration in larger networks.

Implementing Active Directory requires more hardware for domain controller computers and network devices. It also requires additional administration time and resources to ensure shared information is protected and available in a timely fashion. In fact, securing Active Directory information ensures its confidentiality, integrity, and availability. An organization that uses Active Directory depends on the security of its information.

The main reason organizations invest in Active Directory resource requirements is not just to make users happy. While implementing a single sign-on capability is a huge benefit for users in a large organization, the real reason to implement Active Directory is to reduce redundant administrative effort. Securing resources across a network, or multiple networks, requires substantial administrative effort. The amount of redundant controls administrators must keep current opens opportunities for attacks on stale controls. Active Directory automates and centralizes many controls, making the entire environment more secure.

Unlike workgroup environments, a domain user or group definition is defined on the domain controller and its SID will be the same for all computers in the domain. In the workgroup environment, a user named “Fred” may be defined on each computer, but the SID will be different on each one. Auditing Fred’s actions across multiple computers can be more difficult when trying to coordinate multiple SIDs. Active Directory removes the problem of different SIDs on each computer.

**Windows Attack Surfaces and Mitigation**

Windows, like any operating system, is a collection of services provided to allow users to interact with the physical hardware. Each service provides a specific set of access methods to the hardware and functions that satisfy user requirements. In short, operating system services provide some functionality to users. Each service exposes some part of the computer to external access. Regardless of the care taken to ensure the security of the provided access, there is a risk when exposing any part of a computer to external access. All computing systems include vulnerabilities—weaknesses that can allow unauthorized access if successfully exploited. The total collection of all possible vulnerabilities that could provide unauthorized access to computer resources is referred to as the **attack surface**. Another way to define the attack surface is the set of all exposed vulnerabilities.

Multilayered Defense

The discipline of information security is concerned with minimizing the attack surface of any protected resource. This can be achieved by successfully removing, or substantially reducing, the ability of an attacker to conduct an attack against vulnerability. There are several effective methods to minimize the attack surface. The most secure environments employ a combination of strategies. Most important, a solid overall security strategy avoids monolithic solutions. Relying on a single control to protect a resource increases the probability of a successful attack. Always design a defense strategy that is multilayered, which requires multiple controls be compromised to **exploit** any vulnerability. Such a strategy is often called a defense-in-depth approach to security. [Figure 2-5](#11_Chaper2_split_001.xhtml#ba-9781284031652-ch2fig5) shows how a multilayered defense strategy protects resources.

At a high level, the easiest way to reduce the attack surface is to remove functionality. Suppose an attacker wants to exploit Internet Information Services (IIS) Web server vulnerability. The quickest way to deny such an attack is to disable or remove the IIS Web server. Although disabling IIS may be easy, it may be unacceptable. What if the server computer in question is a Web server? Disabling IIS in that case is not an option! But in many cases, disabling a Web server is perfectly OK. It all depends on the purpose of the server computer and the services it must provide to be functional. Defining the computer role and configuring the operating system for that role is one of the best ways to reduce the attack surface of any computer.

Proper workstation and server role definition makes it easier during the installation process to only install and enable services that are necessary for a particular computer. By installing and enabling only the necessary services, you reduce the operating system’s complexity and overall attack surface. Windows Server 2008 and Windows Server 2008 R2 include the Server Manager tool, which makes it easy to define specific roles for a server. There is even a new installation option available called Server Core that installs only the basic services to support file and print services, Active Directory, and a few other basic server functions. The resulting installation takes up less disk space, consumes less memory, and has a much smaller attack surface due to fewer installed services.

**FIGURE 2-5** Multilayered defense.

![image](OEBPS/Images/9781284031652_pg34.jpg)

Mitigation

If you must install and enable a service, such as the IIS Web server, you must employ measures to protect your system from IIS vulnerabilities. The strategies you will learn to secure any resource, also called mitigating a risk, fall into two main categories:

**1.** Remove vulnerabilities.

**2.** Stop attacks from exploiting vulnerabilities.

Between the two strategies, the former is the better option. Removing vulnerabilities by disabling the service or by updating vulnerable software to a more secure version removes the possibility of a successful attack against a specific vulnerability. However, just applying a security patch doesn’t guarantee there is no more vulnerability in the service. That’s why a multilayered defense is so important. Never rely on a single control or strategy to protect a resource. Always employ multiple levels of controls. Your goal is to make attackers work very hard to exploit resources on protected computers.

**Fundamentals of Microsoft Windows Security Monitoring and Maintenance**

The process of securing a Windows computer system and maintaining a secure system is an iterative process. There are three main points in a system’s life cycle that serve as milestones for security management. It is important to maintain a secure system when you:

**1.** Install the operating system or application software

**2.** Monitor the operation of the computer system

**3.** Make any configuration changes to the computer system

The first and third milestones are easy events to identify and result from some administrative action. It is important to include security concerns in the installation and modification procedures to avoid introducing unintended vulnerabilities. For example, the procedure to upgrade to a new version of SQL Server should include steps to ensure insecure user accounts or demo procedures are not added to the system environment. It is also desirable to carry out validation tasks after any new installations or configuration changes to ensure system security meets stated goals. The second milestone occurs at intervals specified by security administrators for each system. Monitoring can be as frequent or infrequent as necessary. Typically the monitoring frequency depends on the volatility of the resource and the risk of attacks against the resource.

Security Monitoring

In general, the process of security monitoring involves comparing performance or configuration information with a stated baseline. Microsoft offers several tools and resources to help create and maintain secure systems. The basic process of security monitoring is to follow these steps:

**1.** Define security goals.

**2.** Describe secure behavior as a baseline.

**3.** Sample performance information and compare with the baseline.

**4.** Report anomalies.

The tools and resources available for Windows operating systems include both suggested baselines and the tools to compare baselines with system configuration and performance information. System configuration information could include user and group definitions, critical resource permissions, and lists of folders. Baseline information could include a list of known vulnerable users, groups, and folders. Any items in the lists of users, groups, or folders that exist in the baseline could indicate vulnerability. Performance information could include Web server log files. Monitoring such log files could show attacks that have been carried out against your system. Or even better, you could see the evidence of a pre-attack reconnaissance effort. In the case of the latter example, you could use such information to take action to protect your system from an expected future attack.

Identify Vulnerabilities

The idea behind monitoring is to simply consider the current state of a system and identify any existing security vulnerabilities. You are proactively taking a similar approach of what an attacker will do to plan an attack. After identifying vulnerabilities, you must decide how to address each one. It sounds simple, and it really is at its core. However, putting that goal into practice can be difficult. There are many options to address each vulnerability, and you have to choose the best option for each situation. The process isn’t a single occurrence of each step. Security monitoring and responding to the results is a process you’ll repeat over and over to keep your systems secure.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Microsoft Windows is a mature family of operating systems that address the needs of many different types of enterprises and users. The wide variety of information managed by Windows systems and the large number of existing systems that run Windows make the platform an attractive target for attacks. Attackers know that each new Windows release gives security administrators new and improved tools to help secure protected resources and information. They know the only way to stay ahead of the game, and outsmart Windows administrators, is to know the operating system and its attack surface as well as possible. And they know it well.

The best way to defend your systems from attack is to know as much, if not more, about your operating system and its vulnerabilities as attackers know. Think like an attacker. Know where and how they’ll likely attempt to compromise your systems. Anticipate their moves and you’ll be better prepared to place deterrents in their path. You have learned the basics of the Windows operating system architecture.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Access control**

**Access control list (ACL)**

**Active Directory**

**Attack surface**

**Authentication**

**Authorization**

**Classification**

**Clearance**

**Control**

**Discretionary access control (DAC)**

**Exploit**

**Hardware Abstraction Layer (HAL)**

**Identification**

**Kernel**

**Mandatory access control (MAC)**

**Microkernel**

**Multifactor authentication**

**Object**

**Permission**

**Right**

**Role based access control (RBAC)**

**Security identifier (SID)**

**Subject**

**Supervisor mode**

**Two-factor authentication**

**Type I authentication**

**Type II authentication**

**Type III authentication**

**User mode**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 2 ASSESSMENT**

  **1.** Which of the following is *not* a goal of a secure environment?

A. All required information is available to authorized users.

B. No information is available to unauthorized users.

C. All required information is available to unauthorized users.

D. No classified information is available to unauthorized users.

  **2.** Which term describes the central component of an operating system?

A. Kernel

B. Shell

C. Hardware Abstraction Layer

D. Executive

  **3.** What are the two run modes for Windows programs?

A. Supervisor mode and executive mode

B. Kernel mode and supervisor mode

C. User mode and executive mode

D. Kernel mode and user mode

  **4.** Which of the following Windows components resides in memory to provide the core operating system services?

A. Kernel

B. Microkernel

C. Executive

D. Hardware Abstraction Layer

  **5.** What is the name of the process that proves you are who you say you are?

A. Identification

B. Authorization

C. Permission

D. Authentication

  **6.** Which type of authentication is a smart card?

A. Type I

B. Type II

C. Type III

D. Type IV

  **7.** Which access control method relates data classification to user clearance?

A. MAC

B. DAC

C. RBAC

D. LDAC

  **8.** What value uniquely identifies a user or group in Windows?

A. UID

B. SAT

C. SID

D. ACE

  **9.** If the same user is created on three separate Windows computers, which value is the same on all three computers?

A. SID

B. User code

C. Username

D. SAT

**10.** Which Windows feature allows users and groups to be “shared” among machines?

A. Domain controller

B. Workgroup

C. SID

D. Active Directory

**11.** What defines the limit of how many computers share users and groups?

A. SID

B. GUID

C. Domain

D. Workgroup

**12.** Which of the following best describes the term *attack surface*?

A. All possible vulnerabilities in application software that could be exploited

B. All possible vulnerabilities that could be exploited

C. The most likely avenues of attack

D. Known vulnerabilities that have not been patched

**13.** When possible, what is the best way to mitigate vulnerability in a specific service?

A. Remove the service.

B. Disable the service.

C. Block access to the service.

D. Patch the service.

**14.** When monitoring a Windows system, with what do you compare current system performance to test for security compliance?

A. The previous monitoring results

B. A normal performance scan

C. A stated baseline

D. A defined security goal

**15.** Why should you immediately test your system for security compliance after making a configuration change?

A. Configuration changes generally increase security.

B. Configuration changes generally decrease security.

C. Configuration changes may introduce new vulnerabilities.

D. Configuration changes may remove existing vulnerabilities.

**PART TWO**

**Managing and Maintaining Microsoft Windows Security**

 
| [**CHAPTER 3**](#13_Chaper3_split_000.xhtml) || [**Access Controls in Microsoft Windows**](#13_Chaper3_split_000.xhtml) |
| --- | --- |
| [**CHAPTER 4**](#14_Chaper4_split_000.xhtml) || [**Microsoft Windows Encryption Tools and Technologies**](#14_Chaper4_split_000.xhtml) |
| [**CHAPTER 5**](#15_Chaper5_split_000.xhtml) || [**Protecting Microsoft Windows Against Malware**](#15_Chaper5_split_000.xhtml) |
| [**CHAPTER 6**](#16_Chaper6_split_000.xhtml) || [**Group Policy Control in Microsoft Windows**](#16_Chaper6_split_000.xhtml) |
| [**CHAPTER 7**](#17_Chaper7_split_000.xhtml) || [**Microsoft Windows Security Profile and Audit Tools**](#17_Chaper7_split_000.xhtml) |
| [**CHAPTER 8**](#18_Chaper8_split_000.xhtml) || [**Microsoft Windows Backup and Recovery Tools**](#18_Chaper8_split_000.xhtml) |
| [**CHAPTER 9**](#19_Chaper9_split_000.xhtml) || [**Microsoft Windows Network Security**](#19_Chaper9_split_000.xhtml) |
| [**CHAPTER 10**](#20_Chaper10_split_000.xhtml) || [**Microsoft Windows Security Administration**](#20_Chaper10_split_000.xhtml) |

**CHAPTER 3**

**Access Controls in Microsoft Windows**

IN THIS CHAPTER, you’ll start learning the details of Windows security features and specific steps to make Windows computers more secure.

As in any complex endeavor, it is important to understand the concepts of information systems security before you start making changes and placing controls. Poorly placed security controls can often do more harm than good. A control that is too permissive to be effective does not increase security. Likewise, a control that is too stringent can often reduce availability and increase user frustration. It is important to always keep security goals in mind as you design and implement controls. Always follow the time-tested strategy of:

• Think

• Plan

• Design

• Implement

• Evaluate

Follow these steps in order, and many of the frustrations encountered from poorly planned actions will be avoided. The first step in designing and implementing an effective access control strategy is considering the most important access control goals. This chapter will cover access control design strategies and the steps necessary to implement and evaluate them.

**Chapter 3 Topics**

This chapter covers the following topics and concepts:

• What the principle of least privilege is

• What access models are, including identification, authentication, authorization, ACLs, and more

• What Windows objects and access controls are

• What forms of identification are, including SIDs, GUIDs, and CLSIDs

• What Microsoft Windows access permissions are

• What auditing and tracking Windows access is

• What Microsoft Windows access management tools are, including cacls, xcacls, and Robocopy

• What best practices for managing Microsoft Windows and application vulnerabilities are

**Chapter 3 Goals**

When you complete this chapter, you will be able to:

• Summarize the principle of least privilege

• Differentiate among identification, authentication, and authorization

• Illustrate the use of Windows ACLs

• Discuss Microsoft Windows objects and access controls

• Identify forms of identification in Microsoft Windows

• Describe Microsoft Windows access permissions

• Examine auditing and tracking Microsoft Windows access

• Research Microsoft Windows access management tools

• Outline best practices for managing Microsoft Windows and application vulnerabilities

• Discuss business challenges of managing vulnerabilities

**The Principle of Least Privilege**

Here is the goal of access control (and security in general):

To ensure all authorized users have access to required information on demand, while denying access to unauthorized users.

In the context of access control, security controls must provide object access for all authorized subjects. The easiest way to do that is to grant full access to all objects, for all subjects. In other words, give everybody access to everything. Global access would satisfy the first part of the security goal, but not the second part of the goal. If object access is granted to everyone, it is impossible to prevent access by unauthorized users.

The Orange Book

The solution is to find the best balance between providing necessary access for authorized subjects (users and applications), and deny any unnecessary access. This principle of providing just the necessary access required to carry out a task is called the **principle of least privilege**.

The United States Department of Defense Trusted Computer System Evaluation Criteria, DOD-5200.28-STD, also known as the **Orange Book**, was one of the first generally accepted standards for computer security. The Orange Book has since been replaced by the **Common Criteria for Information Technology Security Evaluation**—an international standard. The Common Criteria extend the concepts stated in the Orange Book. The Orange Book defines least privilege to be a principle that “requires that each subject in a system be granted the most restrictive set of privileges (or lowest clearance) needed for the performance of authorized tasks. The application of this principle limits the damage that can result from accident, error, or unauthorized use.”

Least Privilege and LUAs

In a Windows environment, the principle of least privilege is implemented at the user account level. In fact, Microsoft refers to user accounts defined using this principle as **least privilege user accounts (LUAs)**. All Windows users are associated with one or more **groups**. The majority of permissions in a Windows environment are controlled at the user group level. A common and manageable way to implement least privilege is to create user groups that represent roles in your organization. Every organization is different and there are many options for creating roles. [Table 3-1](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab1) shows a few examples of common groups found in Windows Server 2008 R2 and Windows Server 2012. The Windows installation process creates these groups, and others, as Windows is installed. These groups represent common roles within an organization and provide a starting point for implementing least privilege.

| **TABLE 3-1** Sample default groups in Windows Server 2008 R2 and Windows Server 2012. |
| **GROUP** || **DESCRIPTION** |
| Administrators || Unrestricted access to the computer’s resources |
| Power users || Limited administrative rights, including the ability to install software and manage users, and extensive file and folders access permissions |
| Users || Limited user rights, prevented from making most system changes (also called limited user accounts) |
| Guests || Very limited rights—fewer rights than regular users |
| Backup operators || Ability to back up and restore files, regardless of the files’ permissions |
| Remote desktop users || Regular user rights plus the right to log on remotely |

Rights and Permissions

Each group in Windows has the ability to apply rights and permissions to sets of users.

Associating users with one or more groups allows the implementation of least privilege in a group setting, as opposed to configuring each individual user account. Securing groups instead of individual users makes the goal of least privilege far more feasible, especially in environments with many users.

User rights are defined and maintained through group security policy objects. Permissions apply to specific objects and are maintained through each object’s security settings. By defining a list of access control rules for each object, access permissions are defined for specific users or groups. The list of access permissions is called the access control list (ACL) for the object. Since the ACLs that Windows uses are implemented as discretionary access control, the more accurate, but less common, term used for the list of access control rules is a **discretionary access control list (DACL)**. Each entry in the DACL is called an **access control entry (ACE)**. The process of securing resources in Windows starts with creating object DACLs that satisfy your security goals. [Figure 3-1](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig1) shows a Windows object DACL.

 ![image](OEBPS/Images/note.jpg)**TIP**

Ensure that you understand the difference between rights and permissions. Rights define what tasks a user can perform on a computer, and permissions define what a user can do to an object. Rights are associated with users, or subjects, and permissions are associated with objects; for example, files.

**FIGURE 3-1** Windows object DACL.

![image](OEBPS/Images/9781284031652_pg44.jpg)

**Access Models: Identification, Authentication, Authorization, ACLs, and More**

When you log on to your computer, Windows follows a specific process to validate you as an authorized user and to decide what you are allowed to do. At the end of the process, Windows has all the information it needs to allow or deny actions based on your security settings. Here are the steps Windows takes to validate a user and build the necessary security information:

**1.** Windows prompts the user to enter identification and authentication credentials. This can be a prompt for username and password, token entry such as a smart card or a token generated password, or a biometric device such as a fingerprint reader.

**2.** Windows looks up the defined user and the associated authentication information. If the supplied information matches the stored information, the user is authenticated.

**3.** Once a user has been authenticated, the operating system records the user account’s security identifier (SID) and the SID of each group to which the user is assigned in one or more tokens. The token that Windows uses to store all the SIDs is called the **Security Access Token (SAT)**. [Figure 3-2](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig2) shows a Windows SAT.

**4.** The SAT, with all the user and group SIDs, is attached to each process the user runs.

 ![image](OEBPS/Images/note.jpg)**TIP**

Windows gets this information from the local machine for local accounts and from Active Directory for domain accounts. Domain account information stored in Active Directory is delivered to the logon machine, no matter where it is. The ability to share logon and security information among computers in a domain, and perhaps more, is one of the most powerful features of Active Directory.

Windows Server 2012 Dynamic Access Control (DAC)

Windows Server 2012 includes new and extended capabilities to help keep data secure. **Dynamic Access Control (DAC)** describes a collection of features to describe user and data attributes. These attributes help Windows protect files using policies that provide more control over who can access data. DAC includes several features:

**FIGURE 3-2** Windows Security Access Token (SAT).

![image](OEBPS/Images/9781284031652_pg45.jpg)

• **Identify and classify data**—You can tag data either automatically or manually to tell Windows how to secure different types of data. Automatic tagging can look for special types of data, such as Social Security numbers.

• **Control file access**—Central access policies allow organizations to set global rules on who can access different types of data.

• **Audit file access**—DAC includes central audit policies that provide the ability for auditors and forensic investigators to find out who accessed sensitive information.

• **Apply encryption to sensitive documents**—Automatic **Rights Management Services (RMS)** can encrypt files that contain tagged sensitive data without requiring user interaction.

DAC builds on features introduced in Windows Server 2008 R2. Features available in Windows Server 2008 R2 include:

• **File Classification Infrastructure (FCI)** provides the ability to define classification properties for files.

• Automatic classification of files is automatically based on location and content. Windows Server 2012 makes it easier to identify sensitive files and automatically encrypt file contents.

• Windows Server 2008 R2 allows enforcement of file expiration policies and custom actions based on classification.

Windows Server 2012 adds to the capabilities of Windows Server 2008 R2 by automating many of the classified file management utilities. Many of the actions an administrator may take, such as classification and encryption, can be automated in Windows Server 2012. Windows Server 2012 also helps support personnel and investigators by enhancing access denied support. The newest version of Windows Server also provides more capability to identify and respond to actions that result in file access denial.

User Account Control (UAC)

Members of the Administrators group have additional powers and responsibilities. They each get two-piece, or split, SAT. One part of the SAT is built with the full privileges of the Administrators group. Members of this group enjoy full access to the computer and can perform many tasks that can be harmful to the computer. The other part of the SAT is built to reflect the more limited capabilities of a normal user. All processes initially run using the limited SAT. If a process requires a privilege that is allowed for administrators and the process also contains an administrator SAT, Windows will prompt the user for an escalation confirmation ([Figure 3-3](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig3)). Windows asks the user to confirm escalating the process to administrator privileges. This confirmation is designed to stop malicious software from making unauthorized changes by running at a higher-than-expected privilege level.

**FIGURE 3-3** Privilege escalation request.

![image](OEBPS/Images/9781284031652_pg47.jpg)

This Windows feature of prompting users before escalating to administrator privileges is called **User Account Control (UAC)**.

Each time a process needs access to an object, Windows refers to the process’s SAT and the object’s DACL to see if the access request is allowed. If the access request is allowed, the process accesses the object. If the access request is not allowed, Windows returns an error and the process cannot complete the requested object access.

Once Windows builds the SAT and attaches it to each process, the SAT becomes the subject part of the authorization process. Before granting access to an object, Windows must first authorize the request. Windows uses the DACL defined for an object to decide whether the access request will be granted or denied. DACLs will be covered in the next section.

**technical TIP**

**UAC Settings**

In previous Windows versions, UAC was often seen as annoying and intrusive. The only options were to turn UAC on or off. Starting with Windows 7 and Windows Server 2008 R2, users can choose one of four “comfort levels” of UAC, from “Never Notify” to “Always Notify.” In Windows 7, you can change this setting in Start > Control Panel > User Accounts and Family Safety > User Accounts > Change User Account Control Settings ([Figure 3-4](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig4)). In Windows Server 2008 R2, you can change this setting in Start > Control Panel > User Accounts > User Accounts > Change User Account Control Settings.

**FIGURE 3-4** UAC settings.

![image](OEBPS/Images/9781284031652_pg48.jpg)

**FIGURE 3-5** Distributed SAT.

![image](OEBPS/Images/9781284031652_pg49.jpg)

Sharing SIDs and SATs

The SAT for each process is built from the user’s SID and group SIDs. The SAT is specific to a computer in a standalone or workgroup environment. Recall that workgroups do not share users or groups. As user and group settings and assignments are customized, synchronizing changes across computers in a workgroup becomes increasingly difficult. This makes Active Directory even more appealing. Active Directory stores the shared necessary information to construct SATs, which are identical for a given user, regardless of the computer where the user logs on.

If the **domain controller** sends security information to the computer where a user logs on, how does Windows stop an attacker from intercepting the SAT information and impersonating an authorized user? Windows extends the concept of authentication to the computer level when constructing SATs. The complete SATs are never shared across a network—only the parts necessary to construct the SAT ([Figure 3-5](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig5)). The domain controller stores the domain user’s SID and the SIDs for all of the domain groups to which the user is assigned. The target server, the server where the resource access resides, already has the local group list of groups to which the user is defined and the local user rights definitions. The domain controller sends the domain user and group SIDs to the target server using one of two Windows authentication protocols.

Managed Service Accounts

Windows Server 2012 adds support for a new type of account to help administrators manage servers. In previous versions of Windows, administrators had to maintain passwords for multiple system accounts. These accounts provide the credentials that critical Windows services and tasks use. Administrators commonly use multiple accounts to handle the needs of various critical services. For example, backup needs are different from the account for an IIS server. Administrators define each system account with just the permissions required to carry out its tasks. Manually maintaining the passwords for system accounts across many servers was tedious.

**FIGURE 3-6** Kerberos.

![image](OEBPS/Images/9781284031652_pg50.jpg)

Windows Server 2012 includes **managed service accounts**, which can be shared across systems. Administrators create these accounts as managed domain accounts that provide automatic password management. Earlier versions of Windows provided computer accounts and managed server accounts, but neither of these account types could be shared across systems. The new group managed service accounts allow the Windows Server 2012 domain controllers to manage the passwords automatically at the domain level.

Kerberos

The default authentication protocol since Windows 2000 is **Kerberos**. Kerberos is a fast and scalable protocol that allows for secure exchange of information ([Figure 3-6](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig6)). Each domain controller functions as a Kerberos **key distribution center (KDC)**. The KDC stores all user and computer Kerberos master keys. When a subject requests access to an object, the subject asks the domain controller for an access ticket. The domain controller authenticates the subject. If successful, the domain controller issues the access ticket. The access ticket contains all of the subject’s SIDs and is encrypted with the target server’s **public key**. The subject then presents the access ticket to the server where the desired object resides. Since the access ticket was encrypted with the server’s public key, the server can decrypt it with its private key. Successful decryption means the ticket is valid and the server evaluates the SIDs for access permission.

NT LAN Manager

The other, older Windows authentication method is **Network Translation LAN Manager (NTLM)**. NTLM differs from Kerberos in function and strength. In NTLM, a client requests access to an object on a server. The client sends the server its password for access. The server then forwards the password to the domain controller. The domain controller validates the password and returns the appropriate result to the server. NTLM requires more effort on the part of the server and has been shown to protect passwords poorly. NTLM is slower in larger environments and is less secure than Kerberos. For the most secure Windows authentication, you should use Kerberos instead of NTLM.

**Windows Objects and Access Controls**

One of the primary security features of Windows is the ability to control access to resources. In a Windows environment, every resource where access can be controlled is defined as a securable object. There are many types of securable objects in Windows, including both named and unnamed objects. The most common securable objects include:

• NTFS files and folders

• Pipes, named or unnamed

• Processes and threads

• Registry keys

• Windows services

• Printers, both local and remote

• Network shares

• Job objects

Windows DACLs

A securable object requires a DACL for Windows to control access to the object.

Any object with no DACL defined is accessible by any subject—any process, any user. An object’s DACL is a collection of individual ACEs and can be modified in the object’s Properties dialog box.

The Security page of the object Properties dialog box ([Figure 3-7](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig7)) allows you to view and modify the security permissions for the selected object. On the Security page, the Group or User Names area lists the users and groups for which ACEs are defined. The Permissions for Users area shows the current permissions for the selected user or group.

**technical TIP**

Here’s how to display and edit any object’s DACL:

**1.** Open the object’s Properties dialog box. Use any one of these procedures:

**a.** Right-click the object, then select Properties.

**b.** Select the object, press SHIFT+F10, then select Properties.

**c.** Hold the ALT key and double-click the object.

**2.** In the Properties dialog box, select the Security tab.

**FIGURE 3-7** Object Properties dialog box, Security page.

![image](OEBPS/Images/9781284031652_pg52.jpg)

The Edit button under the Group or User Names area modifies basic permissions for the highlighted user or group. New users, group permissions, or the removal of existing user or group permissions can be modified here. Basic permissions are predefined common groups of individual permissions that make maintaining DACLs easier. Every permission has two check boxes next to it. Actions can be allowed or modified by using one of the two check boxes. [Table 3-2](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab2) lists the basic permissions that can be modified for each user or group.

DACL Advanced Permissions

The Advanced page provides access to individual object permissions, as opposed to predefined groups of permissions in the general Security page ([Figure 3-8](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig8)). The Advanced page lists every individual permission for the selected user or group.

 ![image](OEBPS/Images/note.jpg)**TIP**

Choose the Advanced button on the Security page to open the Advanced Security Settings dialog box. To change any permissions settings, choose the Change Permissions button.

| **TABLE 3-2** Basic Windows object permissions. |
| **PERMISSION** || **DESCRIPTION** |
| Full Control || Provides no restrictions on access to object |
| Modify || Allows all modifications to files and folders; cannot delete files or folders, change permissions, or take ownership |
| Read & Execute || Traverses folders; executes files; lists folders; reads data, basic and extended attributes, and permissions |
| Read || Lists folders; reads data, basic and extended attributes, and permissions |
| Write || Creates files and folders, writes data and basic and extended attributes, reads permissions |
| Special Permissions || Indicates the ACE for this user or group is defined on the Advanced page |

**FIGURE 3-8** DACL advanced security settings.

![image](OEBPS/Images/9781284031652_pg53.jpg)

**FYI**

To see an example of ACE inheritance, navigate to the following file in Windows Explorer and open the Advanced Security Settings dialog box: C:\\Windows\\System32\\drivers\\etc\\services. Replace C:\\Windows with the Windows OS installation folder if Windows was installed to another folder.

Notice that the rightmost column, titled Inherited From, shows the original source of each ACE. In this example, the ACEs are all inherited from the parent folder.

There are several changes you can make in the Advanced Security Settings dialog box. ACEs for specific users or groups can be added or deleted. The ACE inheritance setting can also be modified. Most objects inherit some ACEs from other objects. For example, it is common for file objects to inherit at least some ACEs from the parent folder.

To disable ACE inheritance, uncheck the “Include inheritable permissions from this object’s parent” check box. If this box is disabled, first select the Change Permissions button. When disabling the inheritance feature, Windows asks what to do with existing inherited ACEs. There are two choices:

**1. Add**—Select this option to add all previously inherited ACEs as new explicit ACEs. This option retains the same functionality but any subsequent changes to the parent’s ACEs will not change the current object’s permissions.

**2. Remove**—Select this option to simply remove all previously inherited ACEs from this object’s DACL.

[Table 3-3](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab3) lists the special permissions available in the Advanced page.

 ![image](OEBPS/Images/note.jpg)**TIP**

If any changes have been made in the Advanced page, one of the Special Permissions boxes will be checked on the Security page to indicate that advanced permissions are defined.

 ![image](OEBPS/Images/note.jpg)**TIP**

Although the Advanced page can be used to set the same permissions as those on the Security page, it should be used only when the basic permissions are not detailed enough to meet current demands. Use the simpler basic permissions when they meet the security objectives. Like basic permissions, special permissions can be allowed or denied by checking one of the two check boxes.

**SIDs, GUIDs, and CLSIDs**

In the Windows operating system environment, all users, groups, and computers all have unique SIDs. A SID identifies a security subject or group of subjects. Local users and groups are assigned SIDs that are unique to a single computer, while domain objects are assigned SIDs that are unique within the domain. A subject’s SID is assigned when the subject is created and never changes throughout its lifetime. A user’s name can be changed, but the user’s SID remains the same. The use of SIDs gives Windows the ability to record references to users, groups, and computers that remain constant and don’t change over time.

| **TABLE 3-3** Special Windows object permissions. |
| **PERMISSION** || **DESCRIPTION** |
| Traverse Folder/Execute File || Navigates to a folder for folder objects and can execute files for file objects |
| List Folder/Read Data || Lists the contents of folders for folder objects or reads data for nonfolder objects |
| Read Attributes || Reads basic object attributes |
| Read Extended Attributes || Reads extended object attributes |
| Create Files/Write Data || Creates files in a folder for folder objects or writes data for nonfolder objects |
| Create Folders/Append Data || Creates new folders for folder objects or appends data to existing nonfolder objects |
| Write Attributes || Writes basic object attributes |
| Write Extended Attributes || Writes extended object attributes |
| Delete Subfolders and Files || Deletes subfolders and files within a folder |
| Delete || Deletes nonfolder objects |
| Read Permissions || Reads object permissions |
| Change Permissions || Changes object permissions |
| Take Ownership || Becomes the new owner of this object |
|   ||   |

As information systems have grown, they have become more diverse and distributed. Many applications now operate as a collection of distributed components running on several different computers. Microsoft uses identification values that are unique across all environments to keep track of objects across many computers. Microsoft assigns many objects a **globally unique identifier (GUID)** to distinguish objects that may originate from different computers. Originally intended to identify ActiveX controls, GUIDs are now used to identify many different types of objects, including:

• Computers

• Web browsers

• Database records

• Files

• Application components

There are several ways to generate GUIDs. Performing an Internet search for “Generate GUID” will result in references to programs, Web sites, scripts, and other strategies to create GUIDs on demand. Microsoft offers a tool to create GUIDs called GUIDGEN.EXE. Any strategy that generates a true globally unique ID will provide a GUID that can be used in your own system.

Windows uses GUIDs extensively to keep track of many objects. The Windows Registry uses GUIDs to identify objects and records many of their attributes. When used in this context, the GUIDs are stored as **Class Identifiers (CLSIDs)**. Windows uses CLSIDs to represent a software application or software component. In fact, CLSIDs can represent even more. Using CLSIDs, even basic information, such as an executable filename, can be changed but still refers to the same application. Windows recognizes either the filename or the CLSID for executable objects. For example, follow these steps to launch the Recycle Bin by running its CLSID:

**1.** Select Start > Run.

**2.** Type the following value in the Open box:  
::{645ff040-5081-101b-9f08-00aa002f954e}

**3.** Choose OK.

 ![image](OEBPS/Images/note.jpg)**TIP**

Get the program GUIDGEN.EXE from Microsoft’s Web site. To find it, visit Microsoft’s Web site at *[http://www.microsoft.com](http://www.microsoft.com)* and search for GUIDGEN.EXE. Download and use the program to generate GUIDs.

| **TABLE 3-4** Common CLSIDs. |
| **CLSID** || **DESCRIPTION** |
| **::{20d04fe0-3aea-1069-a2d8-08002b30309d}** || My Computer |
| **::{450d8fba-ad25-11d0-98a8-0800361b1103}** || My Documents |
| **::{208d2c60-3aea-1069-a2d7-08002b30309d}** || My Network Places |
| **::{1f4de370-d627-11d1-ba4f-00a0c91eedba}** || Network Computers |
| **::{7007acc7-3202-11d1-aad2-00805fc1270e}** || Network Connections |
| **::{2227a280-3aea-1069-a2de-08002b30309d}** || Printers and Faxes |
| **::{645ff040-5081-101b-9f08-00aa002f954e}** || Recycle Bin |
| **::{d6277990-4c6a-11cf-8d87-00aa0060f5bf}** || Scheduled Tasks |
| **::{450d8fba-ad25-11d0-98a8-0800361b1103}\\My Folder** || Opens My Folder under My Documents; assumes the folder “My Folder” exists |
|   ||   |

Windows uses CLSIDs to reference software components without having to know the component’s name. [Table 3-4](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab4) lists some common Windows CLSIDs to run programs without referencing the program name. Run any of the listed CLSIDs to open the corresponding program.

Regardless of whether Microsoft refers to objects using a CLSID or the object name, all access control rules must be satisfied before access is allowed. There is no shortcut that uses direct CLSID references to bypass access controls.

**Calculating Microsoft Windows Access Permissions**

The purpose of access control is to grant and deny access to objects, based on defined rules. Windows supports this goal through definitions of users, groups, and object DACLs. Every object may have a DACL that includes several ACEs. Since an ACE is defined for a specific user or group, it is possible to introduce conflicts. How does the Windows operating system resolve conflicting ACEs?

Windows resolves object access requests by following this procedure:

**1.** Retrieves user and group SIDs from the process’s SAT.

**2.** Examines all ACEs in the object’s DACL for requested permission.

a. If no DACL or ACE is defined for the requested access, Windows allows the access.

b. If only one ACE exists for the requested access, access is based on whether the ACE is defined as “allow” or “deny.”

c. If multiple ACEs exist for the same requested access, all ACEs must be defined as “allow” for Windows to allow the access. Any ACE defined as “deny” will result in Windows denying the access.

**3.** Returns an access approval or denial based on permissions.

Since overlapping ACEs can be confusing, Windows makes it easy to see the permissions in effect for any object. The Advanced Security Settings dialog box contains the **Effective Permissions** page to display calculated permissions for any user or group ([Figure 3-9](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig9)).

Choose the Select button to open the Select User or Group dialog box, type the desired user or group name, and then select OK. Windows will display the effective permissions calculated for the entered user or group. Any permission checked in the Effective Permissions display means that permission is allowed for this user or group. An unchecked check box means the permission is denied.

![image](OEBPS/Images/war.jpg)**WARNING**

Whenever Windows encounters ACE conflicts, “deny” always supersedes “allow.” This feature makes it difficult to accidentally grant more access to users than intended.

![image](OEBPS/Images/war.jpg)**WARNING**

Viewing effective permissions can provide valuable information. It can also be misleading. Viewing the effective permissions for a single group may not tell the whole story. A user that is associated with multiple groups may have less permission than expected at run time if the user is a member of a more restrictive group as well as the one you are viewing.

**FIGURE 3-9** Windows object effective permissions.

![image](OEBPS/Images/9781284031652_pg58.jpg)

**Auditing and Tracking Windows Access**

Access control is primarily a set of preventive security controls. Preventive controls are mechanisms that prevent undesired actions from occurring. While it is good to prevent undesired actions, it is also helpful to get information on what the access controls are doing. Viewing access information can help validate access controls and identify any potential issues. Defined access controls may be either too restrictive or too permissive. Collecting performance information for later analysis can help fine-tune controls to make them more effective and precise.

**Auditing** is the process of collecting performance information on which actions were taken and storing that information for later analysis. In the context of access control, auditing makes a record of desired, allowed, and denied-access requests. This information can be stored for a long or short length of time, allowing time to analyze how well access controls are doing their job.

The first step to collecting access control auditing information is to enable auditing. The process of enabling auditing tells Windows to record the events that will be defined for later analysis. Windows stores audit event notes in event logs and makes it easy to see what has happened on Windows computers.

 ![image](OEBPS/Images/note.jpg)**TIP**

Before enabling access control auditing, know what information is desired and how long it will be retained. Any auditing activity can create a substantial amount of output and add a performance load to your computer. Audit only events that need to be reviewed.

**technical TIP**

To enable auditing for a local machine, choose Start > Administrative Tools > Local Security Policy to launch the Local Security Policy maintenance tool ([Figure 3-10](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3fig10)). Expand Local Policies in the tree view on the left side of the window then select Audit Policy. There are several auditing options that can be enabled. To enable auditing for logon events and object access, double-click Audit Logon Events and Audit Object Access. Each selection gives the option of logging both successful and unsuccessful actions. Unless you want to see a log message for every successful logon and object access, just choose Failure for both.

**FIGURE 3-10** Local Audit Policy.

![image](OEBPS/Images/9781284031652_pg59.jpg)

**FYI**

To launch the Windows Event Viewer, choose Start > Administrative Tools > Event Viewer. In the Event Viewer, expand Windows Logs from the tree view on the left side of the window then select Security.

When enabling auditing for any event category, Windows asks if you want to record successful or failed events, or both. Carefully consider which event types would be beneficial. Each audit event that is recorded requires extra processing to save the event in a log file. Although the effort required for each event is small, it can add up for events that occur frequently. Limit audits to only those events that are needed.

![image](OEBPS/Images/war.jpg)**WARNING**

Windows servers commonly provide resource access to many subjects. Consider the auditing needs before auditing any successful events. If you are unsure, try enabling the event category in question, waiting for a short period, and then looking at the audit log files to see how many events have occurred. The number of events will give you an idea of how many audit events to expect.

The next step in auditing Windows computers is to view and analyze the log files that contain audit entries. Use the Windows Event Viewer to access audit event records.

Each row in the main Event Viewer windows displays a single audit event. Details of the selected row display in the details section at the bottom of the window. The Event Viewer gives you the ability to filter the current log for ad hoc analysis. You can save filter settings as custom views. The ability to filter events allows you to show only the events that are of most interest without having to scroll through the entire log file.

Expression-Based Security Audit Policy (Windows Server 2012)

Windows Server 2012 provides administrators with the ability to use expression-based security audit policies. DAC in Windows Server 2012 enables administrators to create targeted audit policies by using expressions that are based on user, computer, and resource claims.

Here are two examples of expression-based audit policies that administrators can apply in Windows Server 2012:

• Audit everyone who does not have a high security clearance and attempts to access highly sensitive documents.

• Audit all contractors when they try to access documents that are related to projects that they are not working on.

Policies with specific constraints can help limit the number of audit events and record only the most relevant data or users. Administrators can create expression-based audit policies directly on a file or folder or applied centrally through Group Policy.

| **TABLE 3-5** Windows ACL management tools. |
| **TOOL** || **DESCRIPTION** |
| **Cacls.exe** || Legacy command-line tools to display or modify ACLs for files or folders. Cacls.exe is still provided with current Windows versions. |
| **Icacls.exe** || Command-line tool intended to replace and extend **cacls.exe and another legacy tool, xcacls.exe. icacls.exe allows you to list, update, and back up** file and folder ACLs. |
| **Robocopy.exe** || Command-line tool that copies files and folders with or without their associated ACLs. |
|   ||   |

**Microsoft Windows Access Management Tools**

You have seen how to modify object DACLs using the Security page in the Properties dialog box. Although the Properties dialog box is easy to use, it is not effective for managing DACLs for a large number of objects. Making bulk DACL changes in the Properties dialog box is a time-consuming process. Suppose you add a new group and want to add group permissions to the DACLs for a large number of objects. How would you do that without opening each object’s Properties dialog box?

Fortunately, Microsoft provides several tools that make changing DACLs for a group of objects easy. [Table 3-5](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab5) lists the main ACL management tools and their uses.

 ![image](OEBPS/Images/note.jpg)**TIP**

All the tools listed in [Table 3-5](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab5) are command-line interface (CLI) tools. You launch these tools from a command prompt. To launch a command prompt window, choose Start > Run then enter **cmd.exe**

Cacls.exe

The cacls.exe CLI tool was first introduced in Windows 2000. Although Windows now includes the icacls.exe tool as a newer, updated tool, Windows still includes the cacls.exe tool for those who are used to it and may have batch files that depend on it. The cacls.exe command allows users to list or modify the DACLs for one or more files or folders. A single file or folder can be specified, or wildcards can also be used for multiple files or folders. [Table 3-6](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab6) shows a few cacls.exe examples and what each command accomplishes.

| **TABLE 3-6** Sample cacls.exe commands. |
| **COMMAND** || **RESULT** |
| **cacls testfile.txt** || Lists ACLs for the testfile.txt. The output shows one line for each user or group, along with the permissions assigned to each user/group. Permissions will be one of:• N—None• R—Read• W—Write• C—Change (write)• F—Full |
| **cacls testfile.txt /e /g fpurvis:f** || Grants the user “fpurvis” full access to the file testfile.txt. |
| **cacls testfile\*.txt /e /g erpusers:r** || Grants the members of the “erpusers” group full access to all files that match the pattern “testfile\*.txt”. |
| **cacls testfile.txt /e /r erpusers** || Revokes access permission for members of the erpusers group to the file testfile.txt. |
| **cacls C:\\appdocs\\test /e /t /c /g erpusers:c** || Grants the change access permission to members of the erpusers group to all files and folders in the C:\\appdocs\\test folder and all subfolders. |
|   ||   |

Icacls.exe

The icacls.exe CLI tool replaces both the cacls.exe and the xcacls.exe tools. The icacls.exe tool enables the listing, updating, and backup of ACLs for both files and folders. You can also find files that belong to a particular user, change the ownership of files and folders, and replace the permissions for one user with permissions of a different user. [Table 3-7](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab7) shows a few icacls.exe examples and what each command accomplishes.

| **TABLE 3-7** Sample icacls.exe commands. |
| **COMMAND** || **RESULT** |
| **icacls C:\\windows\\\* /save AclFile /T** || Saves the ACLs for all items in C:\\windows folder and its subfolders into a file named AclFile |
| **icacls C:\\windows\\ /restore AclFile** || Restores the ACLs for every file within a file named AclFile to any relevant item that exists in C:\\windows folder and its subfolders |
| **icacls file /grant Administrator:(D,WDAC)** || Grants the user named “Administrator” the Delete and Write permissions to a file named file |
| **icacls file /grant \*S-1-1-0:(D,WDAC)** || Grants the user or security group whose security identifier is S-1-1-0 the Delete and Write permissions to a file named file |
| **icacls C:\\windows\\explorer.exe** || Displays the access control list for a file named C:\\windows\\explorer.exe |
| **icacls file /setintegritylevel H** || Modifies the mandatory integrity level of an object named file to High |

Robocopy

Robocopy, or “Robust Copy,” is a CLI utility that has been available in the Windows Resource Kit for years. Far more than a simple file and folder copy utility, Robocopy provides the functionality to replicate objects and their ACLs in a volatile networked environment. Maintaining a solid access control policy requires keeping defined ACLs intact. Robocopy provides the ability to do just that. Robocopy incorporates many features, including:

• Provides the ability to resume copying where it left off in the case of interruption, as in the case of network disruptions

• Preserves attributes, owner information, auditing information, and timestamp information by default

• Copies all ACLs with objects

• Copies a large number of files without having to invoke the tool multiple times

• Copies long file and folder names

• Allows multithreaded copying

| **TABLE 3-8** Sample robocopy.exe commands. |
| **COMMAND** || **RESULT** |
| **robocopy C:\\source C:\\target /E** || Copies folder contents recursively (/E) all files in C:\\source to C:\\target |
| **robocopy C:\\source C:\\target /COPYALL /E** || Copies folder contents recursively (/E) all files in C:\\source to C:\\target, including all ACL, owner, timestamp, and attribute information |
| **robocopy C:\\source \\\\backupserver\\target /MIR /Z** || Mirrors source to target, destroying any files in target that are not present in source (/MIR), copy files in restartable mode (/Z) in case network connection is lost |
| **robocopy C:\\source C:\\target testfile.txt** || Copies the file testfile.txt from directory C:\\source to C:\\target |

[Table 3-8](#13_Chaper3_split_001.xhtml#ba-9781284031652-ch3tab8) shows a few robocopy.exe examples and what each command accomplishes.

**Best Practices for Microsoft Windows Access Control**

Microsoft provides tools to manage object ACLs and implement solid access control. A secure information system depends on a secure strategy. Best practices for access control center on solid planning and implementing a manageable approach to both subjects and objects. There are many schools of thought related to access control. One particular strategy provides clarity and security. The **AGULP** approach provides a method for managing any number of users predictably. AGULP may appear overly complex for smaller environments, but it really shines when there are many users in a network. AGULP is an acronym that stands for:

• **A**ccounts

• **G**lobal groups

• **U**niversal groups

• **L**ocal groups

• **P**ermissions

The idea behind AGULP is to systematically nest individual user accounts in groups to make securing objects more general. The first step is to create separate user accounts for each user. Creating separate accounts for each user’s role adds an extra step of security. In this case, you may have more than one account. User accounts are then added to global groups, according to their shared attributes. These attributes can be geographical or functional, such as manufacturing or human resources. Global groups would then be added to universal groups, or groups that are defined for users in any domain in Active Directory. Global groups and universal groups are then added to local groups on computers that contain resources you want to secure. This strategy avoids the need to add individual users to local groups. Finally, the permissions for secured resources, or objects, are defined for local groups. The AGULP strategy allows you to reduce the number of ACLs for each resource. Regardless of the strategy you decide to use, avoid defining ACLs for individuals. Group-based ACLs are easier and more efficient to maintain.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Securing information system resources means evaluating each resource request and deciding whether the request should be allowed or denied. While each request can be evaluated on a per-user basis, ease of maintenance often dictates a group-based strategy. Since many users have shared needs for specific resources, it makes sense to group users and assign permissions to resources based on these groups. Windows implements access controls by allowing you to define users, groups, and object DACLs that support your environment. You define the rules and Windows enables you to enforce those rules.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Access control entry (ACE)**

**AGULP**

**Auditing**

**Class Identifiers (CLSIDs)**

**Common Criteria for Information Technology Security Evaluation**

**Discretionary access control list (DACL)**

**Domain controller**

**Dynamic Access Control (DAC)**

**Effective Permissions**

**File Classification Infrastructure (FCI)**

**globally unique identifier (GUID)**

**Group**

**Kerberos**

**Key distribution center (KDC)**

**Least privilege user accounts (LUAs)**

**Managed service accounts**

**Network Translation LAN Manager (NTLM)**

**Orange Book**

**Principle of least privilege**

**Public key**

**Rights Management Services (RMS)**

**Security Access Token (SAT)**

**User Account Control (UAC)**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 3 ASSESSMENT**

  **1.** Which of the following best describes the principle of least privilege?

A. Providing the necessary access to carry out any task

B. Providing access to the least number of objects possible

C. Providing just the necessary access required to carry out a task

D. Providing access equivalent to the least populated security group

  **2.** Which type of user account is designed using the principle of least privilege?

A. LUA

B. SID

C. GUID

D. KDC

  **3.** What structure does the Windows operating system use to store collections of permissions for objects?

A. ACE

B. DACL

C. GUID

D. CLSID

  **4.** If a regular user is a member of four groups, how many SIDs will be stored in the user’s SAT?

A. 1

B. 4

C. 5

D. 6

  **5.** Which of the following best describes UAC?

A. Prompts users before escalating to administrator privileges

B. Prevents processes from escalating to administrator privileges

C. Terminates programs that attempt to escalate to administrator privileges

D. Alerts users that attempts to escalate to administrator privileges have been automatically denied

  **6.** Which protocol does the Windows operating system use by default to authenticate computers to exchange security information?

A. Kerberos

B. NTLM

C. SAML

D. TCP/IP

  **7.** When viewing an object’s DACL, which permission indicates that advanced permissions have been set?

A. Extended permissions

B. Advanced permissions

C. Special permissions

D. Level II permissions

  **8.** Which type of identifier was originally developed to identify ActiveX controls?

A. SID

B. PID

C. CLSID

D. GUID

  **9.** Which type of identifier is used to identify user groups?

A. SID

B. PID

C. CLSID

D. GUID

**10.** If a user, userA, is a member of groupA and groupB, and groupB allows read access to helloWorld.c but groupA denies read access to helloWorld.c, can userA read helloWorld.c?

A. Yes, because groupA allows read access to helloWorld.c.

B. No, because groupB denies read access to helloWorld.c.

C. Yes, because userA is a member of groupB.

D. No, because users cannot belong to multiple groups.

**11.** Why should you carefully design an auditing strategy before turning auditing on?

A. Auditing incomplete information wastes analysis time.

B. Auditing too much information causes excessive overhead.

C. Ad-hoc auditing rarely provides useful information.

D. Audit log files only retain limited information without extensive configuration.

**12.** Which of the following guidelines tends to provide the most useful auditing information?

A. Always audit event success and failures.

B. Never audit both event successes and failures.

C. Generally audit event failures.

D. Do not audit event failures unless you first audit event successes.

**13.** What tool is most commonly used to view and search audit logs?

A. Windows Event Viewer

B. Windows Log Viewer

C. Windows Audit Viewer

D. Windows ACL Viewer

**14.** Which of the following Windows tools replaces previous legacy tools and allows ACL modifications?

A. cacls

B. xcacls

C. icalcs

D. robocopy

**15.** When using AGULP, for which entity type are local object permissions defined?

A. User accounts

B. Global groups

C. Universal groups

D. Domain local groups

**CHAPTER 4**

**Microsoft Windows Encryption Tools and Technologies**

SECURING DATA BY RESTRICTING access to objects using operating system access controls works well for **data at rest**, or data that is stored at a single location. Access controls limit which subjects can read or write data. This provides a level of security while the data remains on the object’s storage device, accessible only through Windows. The problem with this configuration is that functional data tends to be used. Sensitive data is stored in objects that need to be secured. It is also accessed at some point for the purpose of being presented, manipulated, or transmitted to another subject. Once data leaves its protected storage device, you need to provide additional protection to ensure its security is maintained.

In this chapter, you’ll learn about different strategies Microsoft Windows supports to secure data at rest and **data in transit**. Data that is in transit is being sent from one location to another. Encryption is the most common technique used to secure data in transit. Properly used encryption can make accessing, viewing, or changing protected data very difficult. You’ll also learn how encryption can be used to secure data at rest to provide an additional layer of protection over and above solid access controls. Encryption is another valuable strategy for securing your information.

**Chapter 4 Topics**

This chapter covers the following topics and concepts:

• Which encryption methods Microsoft Windows supports

• What Encrypting File System, BitLocker, and BitLocker To Go are

• How to enable file-, folder-, and volume-level encryption

• What encryption in communications is

• What encryption protocols in Microsoft Windows are

• What security certificates are

• What the public key infrastructure (PKI) is

• What best practices for Microsoft Windows encryption techniques are

**Chapter 4 Goals**

When you complete this chapter, you will be able to:

• Identify encryption methods supported by Microsoft Windows

• Describe EFS, BitLocker, and BitLocker To Go

• Explain setup and enabling of file-, folder-, and volume-level encryption

• Research encryption in communications

• Outline encrypted Microsoft Windows protocols

• Debate the advantages and disadvantages of encrypted communications

• Describe security certificates

• Examine the public key infrastructure (PKI)

• Outline best practices for Microsoft Windows encryption techniques

• Discuss business challenges of implementing encryption

**Encryption Methods Microsoft Windows Supports**

Microsoft Windows access controls depend on subjects using Windows to access the secured objects. But what if an attacker is able to bypass Windows and its access controls? Nearly all of today’s computers support multiple **boot devices**. It is not difficult to create a bootable CD, DVD, or USB device that loads another operating system and completely bypasses Windows. Such a boot device could provide direct access to disks and other connected devices without the access controls defined in Windows. In short, an attacker can boot another operating system, effectively bypass all access controls, and gain full access to stored data.

Attacking a computer by booting into a different operating system is easy. Windows access controls alone are not sufficient to protect data. This is a prime example that highlights the need for a defense-in-depth strategy. You need additional controls to protect sensitive data. One type of additional control should be physical controls to limit direct access to computers that store sensitive data. By limiting physical access, you make it more difficult for an attacker to insert a disk or USB device and boot a computer from alternate media.

Another type of control is the use of **encryption**. Files, folders, and volumes can be encrypted using Windows encryption. Windows-encrypted files cannot be booted into another operating system. Windows stores the **decryption keys**. An attacker could still potentially boot from alternate media, but the data on the storage devices would be encrypted and useless outside Windows. Whether the encrypted data is stored on a disk or backed up onto other media, it is useless without the decryption keys. Encryption makes stealing backup media far less attractive to attackers. Encryption provides a valuable additional layer in your defense strategy.

![image](OEBPS/Images/war.jpg)**WARNING**

Just booting a computer using another operating system, such as Linux, is not enough to bypass access controls. The booted operating system has to be configured with drivers and software specifically designed to access NTFS. It may take a little work, but it’s not hard to do.

![image](OEBPS/Images/war.jpg)**WARNING**

Since decrypting data depends on having access to the decryption keys, you’ll need to carefully protect both the primary and recovery keys. If both sets of keys are damaged or lost, you can’t decrypt the data.

Encryption is handy when transferring data between programs. Programs can reside on the same or different computers. It is important to protect sensitive information as it is being transferred from one storage location to another. Commonly, networks are used to transport data. This type of data transport can be vulnerable to attack. Encryption is used to ensure that no unauthorized user can view sensitive data. Encryption also validates both the integrity and source of the data.

Microsoft provides various programs and methods to secure data with encryption. For securing data at rest, Microsoft includes:

• BitLocker for encrypting entire volumes

• Encrypting File System (EFS) for encrypting files and folders

For securing data in transit, Microsoft provides support for many methods and strategies, including:

• Secure networking protocols

• Digital certificates

• Public key infrastructure

• Virtual private networks

 ![image](OEBPS/Images/note.jpg)**TIP**

If you need to support multiple operating systems, you’ll need to look beyond the Windows-only options presented in this section. One of the most popular cross-platform encryption products is Truecrypt. You can find out more about this free open source product at: *[http://www.truecrypt.org/](http://www.truecrypt.org/)*.

**Encrypting File System, BitLocker, and BitLocker To Go**

The Windows operating system supports three main methods to encrypt stored data. Individual applications use additional methods to encrypt data before it is written to the disk. These methods are embedded into the operating system. They occur as the data is written to the disk, not before. Each approach has its place and should be considered based on specific capabilities. The best choice of data at rest encryption depends on the scope of encrypted data and the location of the data. These three methods are specific to Microsoft Windows operating systems.

Encrypting File System

Microsoft introduced the **Encrypting File System (EFS)** in Windows 2000. This feature works only for NTFS file systems. It allows users to encrypt files or entire folders. You can enable the encryption for files or folders simply by selecting a check box on the object’s properties page. It doesn’t require any additional input from the user. [Figure 4-1](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig1) shows the object property page’s encryption setting.

**FIGURE 4-1** Object properties page.

![image](OEBPS/Images/9781284031652_pg72.jpg)

Current versions of EFS use a **symmetric key** partially derived from the user’s password. The choice of a symmetric key provides faster encryption and decryption. Previous versions of Windows used Data Encryption Standard-X (DESX) or **Advanced Encryption Standard (AES)** as the default encryption algorithm. The latest versions of both Windows server and client operating systems use a mixed mode of AES, **Secure Hash Algorithm (SHA)**, and **Elliptic Curve Cryptography (ECC)** algorithms. This allows maximum strength and flexibility. The advantage of EFS is its simplicity, transparency, and ability to limit the scope of encrypted data.

The main drawback to EFS is that it is user-based. Each user must choose to enable encryption for specific files or folders. Alternatively, administrators must define policies that require encryption. The key used to encrypt and decrypt data is based on the user’s password. Using any tool that resets passwords outside of Windows will result in your losing all encrypted data for that user.

You must also take care to avoid using single file encryption for sensitive files. When using single file encryption, the file is written in **plaintext**—unencrypted—to the disk and then encrypted. The plaintext file is then deleted. However, many utilities exist that make it easy to recover deleted files. If the data has not been overwritten, you can easily read the unencrypted data.

BitLocker

A more current encryption method included in Windows is **BitLocker** Drive Encryption. Windows Vista first introduced BitLocker in the Ultimate and Enterprise versions.

Unlike EFS, BitLocker only has two settings for each volume: on or off. You can’t selectively choose which files or folders you want to encrypt. Everything on the selected volume is encrypted. Since entire volumes are encrypted, only administrators can enable or disable encryption. Individual users cannot alter any BitLocker settings. BitLocker also differs from EFS in how it encrypts data. All but one of the BitLocker operation modes depend on the computer’s **Trusted Platform Module (TPM)** microchip to manage and protect the key used for volume encryption and decryption. Most computers manufactured within the last several years contain the required TPM hardware to support BitLocker.

![image](OEBPS/Images/war.jpg)**WARNING**

If you are using EFS, *do not* change passwords except through Windows. It’s not hard to search the Internet and find bootable images that will reset passwords for you. These utilities operate by booting an alternate operating system and modifying system files on your computer. Since this change occurs outside Windows, all EFS encrypted data owned by the user whose password is reset will be lost! Change user passwords only from within Windows.

![image](OEBPS/Images/war.jpg)**WARNING**

Since EFS encrypted files are written to disk unencrypted first, Windows leaves traces of files that can be vulnerable to attack. To avoid leaving unencrypted data lying around, only use folder encryption. That way, the data in the folder is never stored unencrypted.

 ![image](OEBPS/Images/note.jpg)**TIP**

“BitLocker” is a misnomer. Disks refer to physical disk drives. Any computer may have several physical disk drives. Each disk is formatted and one or more disk volumes are created on each one. A disk volume is what you normally see in the operating system as drive letters, such as “C:” or “D:”. BitLocker is actually a disk volume encryption tool, since it encrypts entire volumes.

 ![image](OEBPS/Images/note.jpg)**TIP**

One attractive advantage of relying on the TPM hardware is that encryption can occur with no input from the user—the encryption operations are totally transparent.

BitLocker offers several authentication modes, based on input requirements for credentials. [Table 4-1](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4tab1) lists the BitLocker authentications modes.

BitLocker and EFS solve similar problems, but use different approaches. Each approaches the goal of securing data at different levels, and with different requirements. [Table 4-2](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4tab2) compares the major features of BitLocker and EFS.

EFS is present in the latest newly installed Windows clients and servers. BitLocker is available on Windows 7 and Windows 8 computers, but is not enabled by default for Windows Server 2008 or Windows Server 2012. If you plan to use BitLocker on Windows Server 2008 or Windows Server 2012, you must enable it using the Server Manager utility. To launch Server Manager, choose Start > Server Manager or just choose the Server Manager icon in the taskbar. In Server Manager, select Features in the tree view to open the Features detail window. Select Add Features. [Figures 4-2](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig2) and [4-3](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig3) show the Server Manager and the Add Features Wizard window.

| **TABLE 4-1** BitLocker authentication modes. |
| **MECHANISM** || **AUTHENTICATION MODE** || **DESCRIPTION** |
| TPM only || Transparent operation || No additional input is required from the user. |
| TPM + PIN || User authentication || The user is required to enter a PIN before Windows boots. |
| TPM + PIN + USB key || User authentication || The user is required to enter a PIN and insert a USB key with authentication credentials before Windows boots. |
| TPM + USB key || User authentication || The user is required to insert a USB key with authentication credentials before Windows boots. |
| USB key only || USB Key mode || The only authentication mode that does depend on TPM hardware—the user only inserts a USB with authentication credentials before Windows boots. |
|   ||   ||   |

| **TABLE 4-2** BitLocker and EFS feature comparison. |
| **BITLOCKER** || **ENCRYPTING FILE SYSTEM (EFS)** |
| Encrypts all files on the selected volume || Encrypts only selected files and folders |
| Either on or off for all users || Encrypts files based on user actions—each user can encrypt files or folders individually |
| Uses TPM or USB key as part of the authentication process || Does not require any special hardware |
| Must be administrator to turn BitLocker on or off || Any user can choose to encrypt files or folders |

**FIGURE 4-2** Server Manager—features.

![image](OEBPS/Images/9781284031652_pg75.jpg)

**FIGURE 4-3** Install new BitLocker feature.

![image](OEBPS/Images/9781284031652_pg76.jpg)

**FIGURE 4-4** Confirm BitLocker installation.

![image](OEBPS/Images/9781284031652_pg76-1.jpg)

**FIGURE 4-5** Completed BitLocker installation.

![image](OEBPS/Images/9781284031652_pg77.jpg)

Before adding BitLocker, Windows will ask you to confirm that you want to continue. Select Install to confirm your choice to add BitLocker. Once BitLocker has been installed, Windows will warn you that you must restart the system. When you select Close, Windows will ask if you want to restart your system now or later. Once you restart Windows, the BitLocker feature will be available for all volumes. [Figures 4-4](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig4) and [4-5](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig5) show the confirmation and completion windows.

Windows 8 and Windows Server 2012 added new features to BitLocker. The new features make it even easier to encrypt files on a Windows computer. Here is a list of the new BitLocker features available in Windows 8 and Windows Server 2012:

• **BitLocker provisioning**—In Windows 7, BitLocker could be enabled only after installing the operating system. Now administrators can enable BitLocker as part of the Windows 8 installation process. This allows administrators to deploy Windows 8 in an encrypted state.

• **Encrypt only used disk space**—BitLocker for Windows 8 and Windows Server 2012 allows administrators to encrypt only blocks in a volume that are used to store data. When using this option, BitLocker will not encrypt unused blocks. This option can dramatically reduce the time required to initially encrypt an existing volume.

• **Allow regular users to change BitLocker PIN or password**—Regular users can change the Windows 8 BitLocker PIN or password for operating system volumes. Regular users can also change the Windows 8 BitLocker for fixed data volumes. These features make it easier for administrators to deploy BitLocker to a large number of computers without having to use only generated PINs and passwords.

• **Network unlock**—The Windows Server 2012 feature allows desktop and server computers to automatically unlock operating system volumes when they boot. To use this feature, computers must be connected to a trusted wired network.

• **Support for encrypted hard drives**—BitLocker is a software solution that provides **Full Volume Encryption (FVE)**. Another encryption method gaining popularity is **Full Disk Encryption (FDE)**. In FDE, the disk controller encrypts each block. FDE is faster than FVE, since it occurs at a lower level than the operating system. BitLocker for Windows 8 and Windows Server 2012 now supports encrypted hard drives that use FDE.

BitLocker To Go

**BitLocker To Go** is an extension to BitLocker that protects removable storage devices, such as USB keys. Since removable storage devices may be used to transport sensitive data from one computer to another, it is important to ensure the data is secure as it is being transported. BitLocker To Go makes it easy to encrypt an entire device. When you turn on BitLocker To Go for a device, Windows asks whether to use a password or a **smart card** to encrypt the data.

Once initialized, all data on the removable device is encrypted. You’ll need to enter the same password or use your smart card to access the media’s contents on the other computer (based on which option you selected when you enabled BitLock To Go). As long as the other computer is running Windows 7 or Windows 8, you’ll just be prompted for the password or smart card. If the other computer is running Windows XP or Vista, you’ll be asked if you want to launch the BitLocker To Go Reader. This reader loads the drivers necessary to access BitLocker To Go protected devices.

 ![image](OEBPS/Images/note.jpg)**TIP**

Since removable devices routinely transport files among computers, it wouldn’t make much sense to store encryption keys on one computer’s TPM hardware. That would make the device usable only on that computer. For that reason, TPM encryption isn’t an option for BitLocker To Go.

**Enabling File-, Folder-, and Volume-Level Encryption**

Enabling EFS, BitLocker, and BitLocker To Go is easy. All you have to do is open the Properties dialog box for the desired object and select the appropriate option. Here’s how to enable each type of encryption.

**FIGURE 4-6** Object properties—Advanced attributes.

![image](OEBPS/Images/9781284031652_pg79.jpg)

Enabling EFS

The first step to enabling EFS is deciding what to encrypt. Remember that individual files are stored on disk in plaintext form—unencrypted—before being encrypted. After being encrypted, the plaintext files are deleted, but not totally removed. To avoid any traces of plaintext files being left, it is recommended that you use folder encryption. Once you decide what to encrypt, open Windows Explorer and navigate to the file or folder. To encrypt the object, open the context menu by right-clicking on the object, and select Properties. From the Properties dialog box, choose the Advanced button. In the Advanced Attributes dialog box, select the “Encrypt contents to secure data” check box, choose OK, then choose OK again to close the Properties dialog box. The object is now stored as an encrypted object. No further action from the user is necessary. [Figure 4-6](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig6) shows the Properties and Advanced Attributes dialog boxes.

Enabling BitLocker

Enabling BitLocker is just as easy as EFS. First, however, ensure that you are logged on as an administrator user. To enable BitLocker, open Windows Explorer and navigate to Computer. Open the context menu of the selected volume by right-clicking on the desired volume, and select Turn On BitLocker. [Figure 4-7](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig7) shows the BitLocker option on the object’s context menu.

Alternatively, you can launch the BitLocker management tool to view and manage BitLocker for all volumes. Open the Control Panel by selecting Start > Control Panel. Select System and Security, then BitLocker Drive Encryption. The BitLocker management tool displays all volumes, along with an option to turn BitLocker on or off for each volume. [Figure 4-8](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig8) shows the BitLocker management tool.

 ![image](OEBPS/Images/note.jpg)**TIP**

Note that you can select more than one BitLocker Authentication option. Selecting more than one option requires a user to provide more than one type of authentication before Windows boots and allows access to the encrypted volumes.

**FIGURE 4-7** Enabling BitLocker.

![image](OEBPS/Images/9781284031652_pg80.jpg)

**FIGURE 4-8** BitLocker management tool.

![image](OEBPS/Images/9781284031652_pg81.jpg)

After selecting to enable BitLocker, Windows asks you to pick an authentication method. The authentication method tells Windows what information is required to access an encrypted volume. [Figure 4-9](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig9) shows the BitLocker Authentication options.

Once you select the desired authentication options, Windows will ask where to save a **recovery key**. If you lose the ability to access the primary encryption key, you’ll need the recovery key to decrypt the volume. Windows provides the following options for storing the recovery key:

• Save the recovery key to a USB flash drive.

• Save the recovery key to a file.

• Print the recovery key.

![image](OEBPS/Images/war.jpg)**WARNING**

Ensure your recovery key is secure and available in case of a failure. For example, a motherboard hardware failure makes the primary key unavailable. If you save the recovery key to a file, don’t save it to the volume that is being encrypted.

**FIGURE 4-9** BitLocker Authentication options.

![image](OEBPS/Images/9781284031652_pg82.jpg)

Enabling BitLocker To Go

Enabling BitLocker To Go is very similar to enabling BitLocker. Before starting the procedure, ensure your removable device is attached. First, open Windows Explorer and navigate to Computer. Open the context menu of the selected removable volume by right-clicking on the desired volume, and select Turn On BitLocker. [Figure 4-10](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig10) shows the BitLocker To Go option on the object’s context menu.

The rest of the process for enabling BitLocker To Go is identical to enabling BitLocker.

 ![image](OEBPS/Images/note.jpg)**TIP**

Notice that there is no “Administrator required” icon next to the “Turn on BitLocker” as there was for fixed drives. That is because any user can enable BitLocker To Go. You don’t have to be an administrator to enable BitLocker To Go on removable devices.

**FIGURE 4-10** Enabling BitLocker To Go.

![image](OEBPS/Images/9781284031652_pg83.jpg)

**Encryption in Communications**

Encryption is commonly used for more than just data at rest. It can be used to keep data secure as it is transferred from one place to another. You have already seen how BitLocker To Go can encrypt data on removable media. This is a combination of data at rest and data in transit. BitLocker To Go encryption is technically just encryption of data at rest. A common use of removable media is to transport data from one computer to another. Encryption protects the data by making the data unreadable by anyone who does not possess a valid decryption key. If the removable device is lost or stolen, the contents are unreadable without a decryption key.

 ![image](OEBPS/Images/note.jpg)**TIP**

Encryption should never be the only control in place to protect data. Good physical controls are important to protect physical media. Other technical controls, such as a firewall, should be in place to provide additional barriers to attackers. Encryption should be necessary only if other controls have failed to keep unauthorized subjects away from sensitive information.

Communication data encryption is similar to the concept of BitLocker To Go. Data is encrypted as it is placed on the transmission media. Data is transmitted from the sending process to the receiving process. Here, it is decrypted and used as normal data. [Figure 4-11](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig11) shows the encryption process when used for data transmission.

There are many methods available to secure data transfer. You can encrypt individual messages or create an encrypted connection, or tunnel, to encrypt all data between a sender and a receiver. Regardless of the method or protocols you choose, the goal of communication encryption is to make it very difficult for unauthorized users to access the contents of a message.

The most common perception of encryption is to ensure confidentiality. Encryption provides the ability to “hide” data from unauthorized users. It also provides integrity and **nonrepudiation**. Integrity is provided by ensuring data has not been modified since it was encrypted. This is often accomplished by calculating hash or checksum values. These values are then sent along with the data. Nonrepudiation means that a receiver can verify the source of a message. Additionally, the sender cannot deny sending the message. Windows supports the use of digital signatures to provide nonrepudiation. You’ll learn about several ways Windows uses encryption in the following sections.

**FIGURE 4-11** Encrypted data transmission.

![image](OEBPS/Images/9781284031652_pg84.jpg)

**FIGURE 4-12** Secure Web application connection.

![image](OEBPS/Images/9781284031652_pg85.jpg)

**Encryption Protocols in Microsoft Windows**

Windows includes support for several protocols to provide the infrastructure for encrypted communication. Since encryption can be invoked at several different levels, Windows includes a rich set of protocols to support various encryption needs.

SSL/TLS

One of the most common types of encrypted communication is the Transport Layer security protocol **Transport Layer Security (TLS)**. TLS was formerly called **Secure Sockets Layer (SSL)**. It was originally introduced to secure Web application communication. TLS provides the secure channel for the Hypertext Transfer Protocol Secure (HTTPS) protocol for secure Web pages. TLS creates an encrypted tunnel between a Web client, most commonly a Web browser, and a Web server. All data sent back and forth between the server and the client is encrypted. The client and server negotiate a **cipher** and then exchange a key using **public key cryptography**. Once the key has been securely exchanged, both sides use the symmetric key for subsequent communications. [Figure 4-12](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig12) shows a secure connection between a Web client and a Web server.

Although SSL/TLS was created for Web application communication, it is commonly used in many applications, including Remote Desktop, database connections, and any network connections that require exchanging encrypted data.

Virtual Private Network

Another type of encrypted communication is a **virtual private network (VPN)**. This type of communication exists between a client and a server or between two servers. Once the VPN is established, all messages exchanged between the computers are encrypted. The difference between a VPN and a standard TLS connection is the number of applications each can handle. The TLS connection is generally limited to a single application, while the VPN may transport data from many different applications.

A client must initiate a VPN. During negotiation, the client and server agree on a protocol and set up an encrypted tunnel. The tunnel looks like a regular network connection to local applications, but doesn’t require any special processing. Applications send unencrypted messages to one another while the VPN endpoints take care of the encryption and decryption. [Figure 4-13](#14_Chaper4_split_001.xhtml#ba-9781284031652-ch4fig13) shows a VPN.

Several protocols are commonly used in VPNs. The most common VPN protocol pair is the **Internet Protocol Security (IPSec)** with **Layer 2 Tunneling Protocol (L2TP)**. This protocol pair, often referred to as IPSec/L2TP, provides end-to-end tunneling with optional encryption. The other common VPN protocol used in legacy systems is the **Point-to-Point Tunneling Protocol (PPTP)**. Windows supports both IPSec/L2TP and PPTP when setting up VPNs. One drawback to both protocols is that they can have problems with **firewalls** and **Web proxies**, among other things. Each of these protocols uses specific ports that must be open through network devices for the protocol to work.

![image](OEBPS/Images/war.jpg)**WARNING**

Depending upon the VPN configuration, PPTP VPNs need ports TCP/1723 and UPD/500 open to operate. L2TP needs ports TCP/1701 and UDP/500 open to operate. If any network device between the client and server blocks traffic on any of these ports, the VPN will not work.

**FIGURE 4-13** Virtual private network (VPN).

![image](OEBPS/Images/9781284031652_pg86.jpg)

Microsoft introduced a new VPN protocol for Windows Vista Service Pack 1 and Windows Server 2008—**Secure Socket Tunneling Protocol (SSTP)**. It establishes an encrypted tunnel over an SSL/TLS connection. The advantage of using SSL/TLS is that only port TCP/443 is required for the protocol to operate. Since this is the same default port for secure Web pages using SSL/TLS protocol, it is commonly open through most network devices that connect to the outside world. Although SSTP provides more flexibility than the other two common protocols, it does not support site-to-site tunnels.

Wireless Security

More and more devices are connected to a network using wireless connections. These connections are often temporary. They allow authorized users to connect to enterprise resources from insecure locations, such as coffee shops. Although VPNs can secure all traffic flowing between the client computer and enterprise network, all other traffic will be transmitted in the clear unless another form of encryption is employed.

It is cumbersome to enable encryption for transient public wireless networks because it makes connecting more difficult. This generally conflicts with the provider’s purpose of installing a wireless access point in the first place. Despite this, you should use encryption for all wireless entry points into your network. The original wireless security protocol, **Wired Equivalent Privacy (WEP)**, has been shown to be easily compromised. A determined attacker can hack a WEP key in just a few minutes. The successor to WEP is **Wi-Fi Protected Access (WPA)**. The original WPA implemented only a portion of the IEEE 802.11i standard. The successor to WPA, WPA2, is a full 802.11i implementation. While the full WPA2 protocol requires an 802.11X server, the **pre-shared key (PSK)** mode bypasses the complexity of the authentication server. Simpler WPA implementations, including most homes and small businesses, use WPA-PSK or WPA2-PSK.

**Microsoft Windows and Security Certificates**

There are two main types of encryption algorithms: symmetric and asymmetric. Symmetric algorithms use the same key to encrypt and decrypt data. **Asymmetric algorithms** use two related keys—one key to encrypt data and another key to decrypt data. In general, symmetric algorithms are faster than asymmetric algorithms of the same strength. For large amounts of data or frequent encryption/decryption cycles, symmetric algorithms are preferable to asymmetric algorithms because of the faster execution time.

The main problem with using symmetric algorithms in distributed applications, such as Web applications or VPNs, is getting the same key to both server and client. If you can’t get the encryption key to a client in a secure manner, then you can’t create a secure connection. One approach to the problem is to only use asymmetric encryption. Asymmetric encryption is slower and requires substantial overhead to maintain connections.

A novel solution is to use asymmetric encryption to exchange a symmetric key. The receiver receives a message containing the symmetric encryption key that has been encrypted using the sender’s private key. The receiver can decrypt the message with the sender’s public key. Once the key is properly exchanged, all subsequent communication can use the faster symmetric encryption. One problem with this approach is ensuring there is trust when negotiating and exchanging encryption keys during connection setup. You have to trust that the sender is who he or she claims to be and not an imposter.

A **security certificate**, also called a **digital certificate**, is used to deliver a trusted public key that can be used with assurance it belongs to the stated owner. A security certificate is a document that contains identity information and a public key, along with other descriptive information. The document is then encrypted with the private key of a trusted entity. A digital certificate can be decrypted using the public key of the trusted entity—if it came from the trusted entity. Once successfully decrypted, the document will contain the public key from a source that can be trusted—at least you can trust that the key came from the stated source.

**Public Key Infrastructure**

The general approach to handling keys using trusted entities and digital certificates has been formalized into a strategy called the **public key infrastructure (PKI)**. PKI is the collection of hardware, software, policies, and procedures needed to manage digital certificates. The PKI process starts with a list of trusted entities and their public keys. A trusted entity is generally a **certificate authority (CA)** or a defined **trusted source**. Each computer system contains a list of public keys of trusted entities. A document that is encrypted with a trusted entity’s private key can be decrypted with the same entity’s public key.

When setting up a connection, you would first obtain a security certificate from a trusted entity. The formal PKI process would require you to request a certificate for the connection’s target, or other end, from the PKI **registration authority (RA)**. The RA authenticates you and directs the CA to issue the certificate. You would decrypt the certificate using the CA’s public key. The certificate contains the public key for the target. Once the target’s public key is obtained, you can use it to encrypt messages that only the target can decrypt with its private key.

**Best Practices for Windows Encryption Techniques**

There are many options and strategies to consider when implementing encryption in Windows. Encryption can provide a valuable layer of protection for data, but it does come with a cost. Encrypting and decrypting data is slower than storing the data in unencrypted format. While the performance impact may not be noticeable, you must investigate its impact in your environment before encrypting large amounts of data. Encryption also increases the amount of administrative effort required to maintain system health. Policies must be kept up to date, and you should maintain recovery keys to use with encrypted objects if the primary keys become unusable. Maintaining recovery keys can require a significant amount of time for large organizations with many users. Before implementing encryption of any type, you must assess the cost to both performance and maintenance effort.

While no single set of rules or guidelines is the “best” for any specific environment, there are general best practices that should result in a secure environment. Here is a list of best practices for implementing encryption in a Windows environment:

• Change your passwords periodically. The longer passwords remain unchanged, the higher the probability they will be compromised. Change passwords at least every six months.

• Do not write down passwords. Use passwords that can be remembered. Passwords that are written down are easier for an attacker to find and use.

• Export recovery keys to removable media and store the media in a safe place. EFS or BitLocker recovery information should be physically stored in a separate, safe location.

• Encrypt the My Documents folder for all users. Since most people use My Documents for most document files, encrypting this folder will protect the most commonly used file folder.

• Never encrypt individual files—always encrypt folders. This keeps any sensitive data from ever being written to the disk in plaintext.

• Designate two or more recovery agent accounts per organizational unit. Designate two or more computers for recovery, one for each designated recovery agent account.

• Avoid using print spool files in your print server architecture, or make sure that print spool files are generated in an encrypted folder. This keeps sensitive information from being stored in plaintext on a print server.

• Use multifactor authentication when using BitLocker on operating system volumes to increase volume security.

• Store recovery information for BitLocker in Active Directory Domain Services to provide a secure storage location.

• Disable standby mode for portable computers that use BitLocker. BitLocker protection is effective only when computers are turned off or in hibernation.

• When BitLocker keys have been compromised, either format the volume or decrypt and encrypt the entire volume to remove the BitLocker metadata.

• Require strong passwords for all VPN connections.

• Use the strongest level of encryption that your situation allows for VPNs.

• Use SSTP for VPNs when possible.

• Disable SSID broadcasting for wireless networks.

• Never use WEP for wireless networks—only use WPA/WPA2.

• Trust only certificates from CAs or trusted sites. Train users to reject certificates from unknown or untrusted sites.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

A solid security strategy depends on multiple layers of controls to protect each object. In this chapter, you learned how additional layers of controls using encryption can increase the security of sensitive data. Windows includes the ability to encrypt data at rest using EFS, BitLocker, and BitLocker To Go. Windows also supports encryption of data in transit through the use of several protocols and methods.

Selecting the best mix of encryption methods and applying best practices when using those methods will make your data more secure. Effective use of Windows encryption provides a greater level of security for data at rest and in transit by adding a solid layer of protection to a multilayered security strategy.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Advanced Encryption Standard (AES)**

**Asymmetric algorithm**

**BitLocker**

**BitLocker To Go**

**Boot device**

**Certificate authority (CA)**

**Cipher**

**Data at rest**

**Data in transit**

**Decryption key**

**Digital certificate**

**Elliptic Curve Cryptography (ECC)**

**Encrypting File System (EFS)**

**Encryption**

**Firewall**

**Full Disk Encryption (FDE)**

**Full Volume Encryption (FVE)**

**Internet Protocol Security (IPSec)**

**Layer 2 Tunneling Protocol (L2TP)**

**Nonrepudiation**

**Plaintext**

**Point-to-Point Tunneling Protocol (PPTP)**

**Pre-shared key (PSK)**

**Public key cryptography**

**Public key infrastructure (PKI)**

**Recovery key**

**Registration authority (RA)**

**Secure Hash Algorithm (SHA)**

**Secure Socket Tunneling Protocol (SSTP)**

**Secure Sockets Layer (SSL)**

**Security certificate**

**Smart card**

**Symmetric key**

**Transport Layer Security (TLS)**

**Trusted Platform Module (TPM)**

**Trusted source**

**Virtual private network (VPN)**

**Web proxy**

**Wi-Fi Protected Access (WPA)**

**Wired Equivalent Privacy (WEP)**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 4 ASSESSMENT**

  **1.** Which of the following is the strongest reason why operating system access controls are insufficient to secure objects?

A. It’s possible to boot into another operating system and format the disk.

B. Strong passwords longer that 24 characters are not common.

C. It’s possible to boot into another operating system and bypass access controls.

D. It is often possible to find a user’s password written down.

  **2.** What piece of information is necessary to encrypt and decrypt data?

A. Key

B. Salt

C. TPM

D. Recovery agent

  **3.** Which Windows feature allows you to encrypt entire volumes?

A. EFS

B. Truecrypt

C. BitLocker

D. AppLocker

  **4.** Which Windows feature uses keys based on a user’s password?

A. EFS

B. Truecrypt

C. BitLocker

D. AppLocker

  **5.** Where does BitLocker store encryption keys for transparent mode?

A. USB key

B. Recovery file

C. EFS

D. TPM

  **6.** Which operating system does not have BitLocker enabled by default?

A. Windows Server 2008

B. Windows Vista

C. Windows 7 Premium

D. Windows 7 Ultimate

  **7.** Which of the following services does communication encryption *not* provide?

A. Confidentiality

B. Nonrepudiation

C. Integrity

D. Availability

  **8.** Which protocol commonly provides a secure channel for HTTPS?

A. SSL/TLS

B. PPTP

C. S-PPTP

D. L2TP

  **9.** Which VPN protocol has the fewest issues with NATs and firewalls?

A. L2TP

B. SSTP

C. IPSec

D. PPTP

**10.** Which of the following is the weakest wireless protocol (and should never be used)?

A. WPA

B. PSK

C. WEP

D. SSID

**11.** Which type of encryption algorithm uses two related keys?

A. Symmetric

B. Balanced

C. Private

D. Asymmetric

**12.** Which of the following is used to deliver a trusted public key that can be used with assurance it belongs to the stated owner?

A. Digital signature

B. Digital certificate

C. Certificate authority

D. Private key

**13.** What is a general approach to handling keys using trusted entities and digital certificates?

A. PKI

B. IPSec

C. WPA-PSK

D. SSTP

**14.** Which common folder should be encrypted for all users?

A. Windows

B. Program Files

C. My Documents

D. My Secure Files

**15.** Why is it recommended to encrypt folders instead of files?

A. Individual files are written to disk unencrypted before being encrypted.

B. Folder encryption is faster.

C. Folder encryption results in less disk usage.

D. Individual files are encrypted first then written to disk.

**CHAPTER 5**

**Protecting Microsoft Windows Against Malware**

INFORMATION SECURITY EFFORTS are often focused on protecting data from unauthorized people. While the concepts are generally stated in terms of users and not people, it is common to relate the two. What if an attacker is not a person? Programs can carry out attacks. It is important to consider controls to prevent programs from violating the confidentiality, integrity, and availability of data as well as just preventing human attacks.

In this chapter, you’ll learn about the different types of software that can violate the security of your information systems. Software designed to infiltrate a target computer and carry out the attacker’s instructions is referred to as malicious software. Malicious software of all types is generally referred to as malware. You’ll also learn techniques to prevent malware attacks, search for the presence of suspect software, and remove any software you have identified as malicious. Diligence is required to fully protect an information system environment from malware attacks, and you’ll learn what to do to keep your systems secure.

**Chapter 5 Topics**

This chapter covers the following topics and concepts:

• What the purpose of malware is

• What different types of malware are

• What antivirus and anti-spyware software are

• Why updating software is important

• What maintaining a malware-free environment is

• What scanning and auditing malware are

• What tools and techniques for removing malware are

• What best practices for malware prevention are

**Chapter 5 Goals**

When you complete this chapter, you will be able to:

• Explain the purpose of malware

• Explain the effects of malicious code

• Classify malicious code

• Describe how malicious code spreads and operates, and where it resides

• Explain how antivirus and anti-spyware software work

• Discuss the importance of timely updates, testing, and deployment

• Identify strategies for maintaining a malware-free environment

• Recognize the importance of scanning regimes

• Analyze tools and techniques for malware cleanup

• Outline best practices for malware prevention

**The Purpose of Malware**

The term **malware** refers to a collection of different types of software that share the goal of infiltrating a computer and making it do something. It is often called malicious software. In many cases, malware does something undesired and operates without the explicit consent of the owner. This is not always the case, however. Some types of malware are downloaded and installed with the owner’s full knowledge.

Malware was first introduced to computers and networks as “harmless” experiments or pranks. In fact, the earliest examples of programs that later came to be known as malware really were not malicious at all. The earliest malware developers were mostly interested in learning what novel computer programs could accomplish. Today, most malware satisfies more dubious purposes. Current malware generally exists to fulfill one or more of the following purposes:

• **Disrupt computer operations**—Malware programs can overwhelm a computer’s ability to run other programs or communicate with other computers or devices. They can also damage or even remove critical operating system components that other programs need to operate. Malware can also alter or delete memory or disk content that programs need to run. Most of the actions malware takes to disrupt computer operation results in unexpected conditions that programs cannot handle. The result is unexpected program behavior or even crashed programs.

• **Gather sensitive information**—Many types of malware programs operate without announcing themselves. They search for sensitive data, such as financial data and personal identification data. They store any data they find or send it to the malware creator using the computer’s network connection. There are many places users store sensitive information, including browser cache, files on disk, and even in memory. Malware programs know where to look for the most common sensitive data.

• **Gain unauthorized access to restricted computer resources**—The third main purpose of malware is to provide a way for attackers to access computers and other network resources. Malware written for this purpose exploits vulnerabilities to get inside a protected network. It then takes some action that results in a new access method for an attacker. In effect, this type of malware opens a new door to a restricted computer.

Malware may exist to carry out specific attacks or to accomplish only one step in more complicated attacks. For example, malware can often help attackers identify likely victims for a subsequent attack. Attackers routinely use many types of tools to carry out attacks. Malware is just one tool in their arsenals.

**Types of Malware**

Attackers can choose different types of malware to meet the goals of their attacks. The best type of malware for any situation depends on the type of attack. Malware can be loosely divided into two main categories: programs that spread or infect and programs that hide.

Programs that spread or infect actively attempt to copy themselves to other computers. Their main purpose is to carry out instructions on new targets. Malware of this type includes:

• Viruses

• Worms

Other malware hides in the computer to carry out its instructions while avoiding detection. Malware that tends to hide includes:

• Trojan horses

• Rootkits

• Spyware

Understanding these five basic types of malware and how to protect your systems from them is an important component of a solid security plan. The following sections describe each malware type.

**FYI**

Developers at Bell Labs actually created a game called Darwin that contained virus-like behavior as far back as 1962. The game allowed “creatures” to grow, thrive, and overtake each other. One of the developers, Robert Morris, Sr., created a lethal beast that used virus-like tactics to infect areas of the playing arena. It was constrained to a single computer but set the stage for future malware.

Virus

A computer **virus** is a software program that attaches itself to, or copies itself into, another program. It causes the computer to follow instructions not intended by the original program developer. A virus “infects” a host program and may cause that host program to replicate itself to other computers. The term virus is used to describe malware that acts in a similar fashion to biological viruses. The virus cannot exist without a host, similar to many parasites. It can spread from host to host in an infectious manner.

The Creeper was the first reported inter-computer virus recorded. It was written by Bob Thomas in 1971. The Creeper would copy itself to other networked computers and display the message “I’m the creeper, catch me if you can!” It was designed as an experimental self-replicating program to see how such programs would affect computers on a network. Shortly after the Creeper was released, the Reaper program was unleashed to find and eradicate the Creeper.

Today, there are thousands of known viruses that infect programs of all types. The main concern with viruses is that they often attach themselves to commonly run programs. When users run these infected programs, they are actually running virus code with their user credentials and authorization. The virus doesn’t have to escalate privileges. Users who run the infected program provide the virus with their authenticated credentials and permissions.

Worm

A worm is a type of malware that is self-contained. It is a program that replicates and sends copies of itself to other computers, generally across a network. The worm may take other actions, or its purpose may just be to reduce availability by using up network bandwidth. The main difference between a virus and a worm is that a worm does not need a host program to infect; the worm is a standalone program. Since worms don’t rely on hosts, they generally can spread faster and farther. On the other hand, worms tend to be somewhat platform specific, since they are standalone programs.

The first worm reported to spread “in the wild” was the Morris worm. The Morris worm was written by Robert Tappan Morris, Jr. in 1988. It was designed to spread across the Internet and infect computers running versions of the UNIX operating system. The original intent of this worm was to estimate the size of the Internet, but the worm spread faster than its author expected. The worm ended up infecting computers multiple times and eventually slowed each infected computer down until it became unusable.

The Morris worm exploited **buffer overflow** vulnerability. A buffer overflow is a condition in which a running program stores data in an area outside the memory location set aside for the data. By storing more data than a program expects, it is possible to put instructions into a program that alter its behavior at run time. Buffer overflows are numerous and always result from a programmer neglecting to validate input data.

Since the Morris worm, attackers have released many other notable worms, such as Melissa, The Love Bug, Code Red, Nimda, SQL Slammer, Sasser, and Conficker. Worms tend to thrive in environments where users run them without thinking about the potential consequences. In the past, many worms were transported in e-mail messages. In the near future, expect to see a substantial increase in worms spreading through social networking. The fast pace of communicating through social media mechanisms opens new opportunities for both attackers and security administrators.

** ![image](OEBPS/Images/note.jpg)NOTE**

The Morris worm was the first malware incident to gain widespread media attention and resulted in the first conviction under the U.S. 1986 Computer Use and Fraud Act.

Trojan Horse

The **Trojan horse**, also called a Trojan, is malware that either hides or masquerades as a useful or benign program. The name derives from the story of the Trojan horse in *The* *Aeneid*. In the story, the Greeks constructed a large wooden horse and offered it as a gift to Troy. After 10 years of war with Troy, the Greeks left the horse and sailed away. The gift was seen as a victory offering and was brought into the city. That night, Greek soldiers hidden inside the hollow horse opened the city gates, and let the rest of the Greek army, which had returned after dark, into the city. The Greeks soundly defeated Troy that night.

Trojan horse programs use their outward appearance to trick users into running them. They are disguised as programs that perform useful tasks, but actually hide malicious code. Once the program is running, the attack instructions execute with the user’s permissions and authority. In essence, the Trojan horse developer has tricked a user into running an attack program.

The first known Trojan was Animal, released in 1974. The program was disguised as a simple quiz game in which the user would think of an animal and the program would ask questions to attempt to guess the animal. In addition to just asking questions, the program would actually copy itself into every directory where the user had write access. Today’s Trojans do far more than just save copies of themselves. Trojans can hide programs that collect sensitive information, open backdoors into a computer, or actively upload and download files. The list of possibilities is endless.

Rootkit

A **rootkit** is a type of malware that modifies or replaces one or more existing programs to hide the fact that a computer has been compromised. It is common for rootkits to modify parts of the operating system to conceal traces of their presence. Rootkits can exist at any level, from the boot instructions of a computer up to the applications that run in the operating system. Once installed, rootkits provide attackers with access to compromised computers and easy access to launching additional attacks.

Rootkits are newer than other types of malware and did not appear until around 1990. They can be difficult to detect and remove since their main purpose is to hide their own existence. But identifying and removing rootkits is crucial to maintaining a secure system.

 ![image](OEBPS/Images/note.jpg)**TIP**

Rootkits often work with other malware. Suppose a program, malware.exe, is running on a Windows system. A simple rootkit example would be to replace the Windows Task Manager with a modified version that does not list any program named malware. exe. Administrators would not know the malware program is running.

Spyware

The last main type of malware is **spyware**. Spyware is software that covertly collects information without the user’s knowledge or permission. The information collected can be sensitive personal information, such as a password or credit card number, or information used to build profiles for future action. Spyware is commonly used by aggressive marketers to collect specific information about customers and their preferences.

Most spyware programs piggyback onto other legitimate programs. They are installed along with the intended programs. Although the primary purpose of most spyware is to collect and report on information, the process of doing just that can cause other problems. Spyware causes additional processes to run to collect the pieces of information. This adds more processes, uses more memory, and can generally slow down a computer. Computers that have many spyware programs installed can run noticeably more slowly than a clean computer.

Spyware has been around since the late 1990s, but became more common after 2000. The rapid growth of the Internet enabled attackers to collect useful information from unsuspecting users. Use of the information collected by spyware can range from customized suggestive selling to identity theft. The main goal of spyware is to collect and deliver information—especially private information. When successful, spyware violates the privacy of information and provides easy access to unauthorized users. Private information should stay private. Spyware is a type of malware that specifically threatens the confidentiality of information.

Ransomware

Another type of malware attempts to generate funds directly from a computer user. **Ransomware** attacks a computer and limits the user’s ability to access the computer. It can limit access by slowing the computer down, denying access for authorized users, or by blocking access to specific programs or resources. Some ransomware operates by encrypting important files, or even the entire disk, and making them inaccessible. The attacker generally alerts the users to the restrictions and demands a payment to restore full access. The payment, or ransom, gives this type of malware its name. The attacker promises to decrypt the user’s data or remove any mechanisms that block access once the ransom is paid. Most computer users rely on their computers and the data they store. Few computer users can lose access to their data and other resources without encountering ongoing frustration.

Business users may find ransomware to be far more than a simple annoyance. The inability to access key parts of a business computing system can have the same effect as a DoS attack. Ransomware can cause organizations to lose large profits in a very short period of time. Attackers who launch ransomware attacks expose themselves to huge risks but also can realize large profits. Ransomware is a growing trend in malware. User reliance on mobile devices makes such devices attractive targets. As Windows computers and devices become more mobile, they become even more vulnerable to potential ransomware attacks.

Malware Type Summary

Most current malware tends to be complex and possess characteristics of several of the basic types discussed in this section. Modern malware is commonly a hybrid of two or more types, allowing it to be more effective and harder to combat. Even though hybrid malware is becoming more common, it is still important to understand the basic types and how to protect your systems. Protection from more complex malware often includes protecting systems from a combination of basic malware types. [Table 5-1](#15_Chaper5_split_001.xhtml#ba-9781284031652-ch5tab1) compares the five basic types of malware and their most prominent characteristics.

| **TABLE 5-1** Common types of malware. |
| **MALWARE TYPE** || **PROMINENT CHARACTERISTIC** |
| Virus || Attaches to or “infects” a host program |
| Worm || Standalone program—does not need a host |
| Trojan || Hides or masquerades as a harmless program, tricking users into running the malware |
| Rootkit || Modifies programs, possibly even operating system programs, to hide traces of its own existence |
| Spyware || Covertly collects information and sends it to a collector |
| Ransomware || Program that limits access to the infected computer and demands a ransom to be paid to the attacker to restore full access |

**Antivirus and Anti-Spyware Software**

The success of any malware program lies in its ability to avoid and resist detection and removal. The basic design of malware makes the process of keeping your computers clean more difficult. It is nearly impossible to manually identify and remove all traces of malware—there is just too much active malware threatening any computer connected to a network.

The only reasonable approach to addressing the problems of malware is to use a collection of programs specially designed to combat malware. Such programs include antivirus and anti-spyware software. Collectively, these software packages are also called anti-malware software. While there are some overlapping features, each type of software generally performs different functions. Both types of software are necessary to create and maintain a secure computer system.

![image](OEBPS/Images/war.jpg)**WARNING**

A computer does not have to be connected to a network to be infected with malware. Malware can travel from computer to computer via removable media as well as via networks. Any CD, DVD, USB device, or removable device has the potential to transport infected programs to a target machine. Don’t neglect removable media when you develop an anti-malware policy.

Antivirus Software

**Antivirus software** can help detect and mitigate some types of malware. There are many antivirus programs available that can identify many known types of malware and help respond to the threats malware programs present. Most antivirus software focuses on viruses, worms, and Trojan horses, but may also address rootkits and spyware. Current antivirus software provides the ability to prevent, detect, and remove malware instances.

Many quality antivirus software products are available. [Table 5-2](#15_Chaper5_split_001.xhtml#ba-9781284031652-ch5tab2) lists several of the more commonly used antivirus products for Windows. Note that [Table 5-2](#15_Chaper5_split_001.xhtml#ba-9781284031652-ch5tab2) is just a sample list of some common antivirus products.

The most common method used to identify malware is to compare known malware code with processes running in memory or files stored on disk. Each instance of malware has a unique set of instructions, called the malware’s **signature**, which identifies any copies of the malware on your system. The organized collection of known malware signatures is stored in a **signature database**. The antivirus software uses the signature database for signature matches when scanning processes or files. Any process or file that contains instructions that match a known malware signature is flagged as malware.

![image](OEBPS/Images/war.jpg)**WARNING**

Regardless of how good your anti-malware software is, it won’t catch everything. Never rely on any single control to do all the work. Always use the defense-in-depth strategy to ensure multiple controls protect each resource.

| **TABLE 5-2** Common antivirus software for Windows. |
| **PRODUCT** || **WEB SITE** |
| Bitdefender Antivirus || *[http://www.bitdefender.com/](http://www.bitdefender.com/)* |
| Kapersky Anti-Virus || *[http://www.kapersky.com/anti-virus](http://www.kapersky.com/anti-virus)* |
| Norton Antivirus || *[http://us.norton.com/antivirus/](http://us.norton.com/antivirus/)* |
| F-Secure Anti-Virus || *[http://www.f-secure.com](http://www.f-secure.com)* |
| G Data AntiVirus || *[https://www.gdatasoftware.com/](https://www.gdatasoftware.com/)* |
| BullGuard Antivirus || *[http://www.bullguard.com/products/bullguard-antivirus-2013.aspx](http://www.bullguard.com/products/bullguard-antivirus-2013.aspx)* |
| Panda Antivirus || *[http://www.pandasecurity.com/usa/homeusers/solutions/antivirus/](http://www.pandasecurity.com/usa/homeusers/solutions/antivirus/)* |
| Avast Antiviruss || *[http://avast.en.softonic.com/](http://avast.en.softonic.com/)* |
| AVG AntiVirus || *[http://www.avg.com/us-en/buy-antivirus](http://www.avg.com/us-en/buy-antivirus)* |
| Avira AntiVir || *[http://us.avira.com/](http://us.avira.com/)* |

Another method some antivirus software uses to identify malware is called **heuristics**. Heuristics is the practice of identifying malware based on previous experience. The actions malware programs tend to carry out are stored in a database. When searching for malware, a heuristic scanner compares observed behavior with stored malware behavior. A match indicates the process in question is malware. The heuristic approach is more complex and slower than signature matching, but can detect previously unknown malware if its behavior is similar to a known malware instance.

Anti-Spyware Software

**Anti-spyware software** is another type of anti-malware software. It helps detect and mitigate malware. As the name implies, the primary target is spyware. While many antivirus software suites may include an anti-spyware component, there is value to using one or more additional standalone anti-spyware products. There are so many spyware instances that it makes sense to use multiple anti-spyware software products to ensure you identify as many instances on your computers as possible.

There are many good anti-spyware software products available. [Table 5-3](#15_Chaper5_split_001.xhtml#ba-9781284031652-ch5tab3) lists several of the more commonly used anti-spyware products for Windows.

| **TABLE 5-3** Common anti-spyware software for Windows. |
| **PRODUCT** || **WEBSITE** |
| Microsoft Windows Defender, included in Windows 7 and Windows 8 || *[http://www.microsoft.com/en-us/download/details.aspx?id=17](http://www.microsoft.com/en-us/download/details.aspx?id=17)* |
| SpyBot Search and Destroy || *[http://www.safer-networking.org/](http://www.safer-networking.org/)* |
| Lavasoft Ad-Aware || *[http://www.lavasoft.com/](http://www.lavasoft.com/)* |
| Webroot Spy Sweeper || *[http://www.webroot.com/En\_US/consumer-products-spysweeper.html](http://www.webroot.com/En_US/consumer-products-spysweeper.html)* |

**Importance of Updating Your Software**

Attackers introduce new malware on a daily basis. Eugene Kapersky, of Kapersky Lab, reports that there are currently around 70,000 new viruses, Trojans, and other malware threats every day. That represents a dramatic increase from just a few years ago. Today’s malware creators commonly use automated tools to craft new malware threats by automatically making small changes to existing malware. Essentially, the signature database downloaded last week can’t protect you from new threats that have emerged this week. If you update your antivirus or anti-spyware software only once a week, you could be vulnerable to as many as 1,400 new threats before downloading an updated signature database.

When an attacker releases a new malware instance, the race against the clock begins. From the beginning, heuristic-based software may detect the activity and identify the software as malware. If the attacker designed a clever malware program, it could fool heuristic-based tools. Signature-based anti-malware tools will not identify this new threat until a signature for the threat is added to a signature database.

The largest number of potential victims occurs during a **zero-day attack**. A zero-day attack is malware that is actively exploiting an unknown vulnerability and one or more of the following is true:

• The malware’s actions have not been noticed and the vulnerability has not been discovered.

• The malware’s actions have been noticed but not identified as an attack.

• The malware and the vulnerability have been identified but no fix is available yet.

Organizations that produce anti-malware software strive to stay up to date on emerging threats, create rules and signatures to identify new threats, and develop mitigation actions for each threat. Each of these steps takes time. By the time a new signature database is released, several days or weeks could have elapsed since the malware was on the rampage. Because brand-new signature databases are several days behind zero-day attacks, it is vitally important that your anti-malware software and data be kept as current as possible.

Most antivirus and anti-spyware software have an option to automatically update the software and data. Ensure that you have enabled the automatic update option and have selected the minimum reasonable update frequency. Frequent updates will help keep your protection from malware at its highest level.

 ![image](OEBPS/Images/note.jpg)**TIP**

In most environments, daily updates should be sufficient. Ask your antivirus and anti-spyware software vendors when they release updated signature databases. Then, schedule your updates to occur shortly after the new information is released.

**Maintaining a Malware-Free Environment**

The key to keeping malware out of your computer system is to start with a clean structure and diligently protect it from becoming infected. Your anti-malware software contains several components that work together to keep your computer free of malware. [Table 5-4](#15_Chaper5_split_001.xhtml#ba-9781284031652-ch5tab4) lists the common components of anti-malware software needed to keep a system malware-free.

The first step in staying malware-free is to install one or more anti-malware software products and scan your system. You’ll learn more about the scanning process in the next section, but for now, scanning searches your computer for malware. The scanning process uses the scanner and signature database components to find any malware programs. If the software does find any malware, it will need to be removed. You’ll learn more about malware removal in a later section. The removal process may use the vault component in the cleanup process.

| **TABLE 5-4** Common anti-malware software components. |
| **COMPONENT** || **DESCRIPTION** |
| Signature database || Collection of identifying instructions for known malware used to detect malware in existing programs and files |
| Scanner || Software that compares existing file contents with a signature database to identify malware |
| Vault || Secure location on disk used to store identified malware |
| Shield || Software that intercepts all incoming—and optionally outgoing—information, scanning each message or file for malware content |

Once the computer is free from malware, you need to ensure it stays clean. The remaining common component of anti-malware software is the **anti-malware shield**. The shield is software that intercepts and scans incoming information for malware. Some shield software can also scan outgoing information for malware. The shield helps protect a computer from new malware, or from sending malware to another computer if you have enabled outgoing scanning.

Malware can move from computer to computer in many ways, so anti-malware shield software often intercepts information such as:

• Internet e-mail messages

• Local e-mail client messages

• Instant messaging

• Web traffic

• Network traffic

• P2P traffic

The shield function of your anti-malware software will go a long way toward keeping your computers malware free, but should not be the only control in place. Always remember the defense-in-depth strategy when protecting resources. A good anti-malware shield is only one part of an overall security plan to keep computers malware free.

** ![image](OEBPS/Images/note.jpg)NOTE**

Many anti-malware software products give options for enabling or disabling the shield function, also called real-time scanning, for different types of information. Unless you have a specific reason to disable the shield for a specific type of information, leave it enabled for all types.

**Scanning and Auditing Malware**

Anti-malware software can fail to detect very new malware. Don’t rely only on an anti-malware shield to keep your computers clean. Recall that even the latest version of a signature database will not have zero-day attack signatures. It is important to periodically scan the contents of your computers to detect any malware that the shields have missed.

The scan process is simple: The anti-malware scanner opens files that have been selected and searches them for malware. The scanner looks for copies of known malware signatures from the signature database in files selected for scanning. This can be a time-consuming process. It is important to carefully plan your scanning schedule and select the most efficient options for each scan. [Table 5-5](#15_Chaper5_split_001.xhtml#ba-9781284031652-ch5tab5) lists the most important questions to consider when scheduling a malware scan for your computers. Each anti-malware software package has specific options that may differ among vendors, but the general questions you must answer are common among most anti-malware software.

| **TABLE 5-5** Malware scanning options. |
| **QUESTION** || **POTENTIAL IMPACT** |
| Scan which drives? || Scanning physical disk drives takes longer and can degrade overall computer performance. For frequent scans, scan only the disks that are frequently used by users and applications. |
| Scan removable media? || For the best security, scan all removable media when it is inserted. This may cause excessive scan activity. Another option is to only require removable media scanning for any media introduced from outside your controlled organization. |
| Full or quick scan? || Quick scans generally only scan files that are likely to contain malware, such as executable files. Quick scans can reduce the negative performance impact on computers. Ensure full scans occur periodically, such as weekly. |
| Scan when? || Computers should be scanned for malware under any of the following circumstances:• You suspect that malware is present.• You have installed new software or upgraded existing software.• Sufficient time has passed since the last scan. Each organization should develop a schedule for malware scans. |
|   ||   |

**Tools and Techniques for Removing Malware**

Despite the best efforts to keep malware away from your computers, you may find active malware during a scan process. Once you have identified malware, what do you do? The answer to that question is simple: Follow your malware eradication plan. That means you should have already planned your actions. The time to think through the best way to handle malware infection is before the infection occurs.

There are two primary resources you should consult as you develop a malware eradication plan. Become familiar with these resources. They can help you avoid reinventing the wheel when developing your plan to handle malware infections.

**1.** Your anti-malware software’s support resources

**2.** Microsoft’s online resources—specifically, the Microsoft Malicious Software Removal Tool—*[http://www.microsoft.com/security/malwareremove/default.aspx](http://www.microsoft.com/security/malwareremove/default.aspx)*

In many cases, anti-malware software will suggest an action for each malware instance it finds. You can accept the suggestion or override the suggestion with your own action. Most anti-malware software provides links to follow for more information if you don’t have enough information to make a decision.

If you detect malware soon after installing or updating software, the easiest fix may be to uninstall or downgrade the offending software. Make sure you initiate another scan after taking any action to ensure your action actually fixed the problem.

If the options provided by your anti-malware software are not sufficient to remove the detected malware, the next step is to employ the Microsoft Malicious Software Removal Tool. Visit the link provided earlier in this section to download the Microsoft Malicious Software Removal Tool. Install the tool and run it to help in removing some common malware found on Windows computers.

![image](OEBPS/Images/war.jpg)**WARNING**

Don’t just choose the default action when presented with malware. Carefully read the explanation your software provides and do some research. In many cases, the action your software suggests is the best action, but you always need to make an informed decision. Always read the anti-malware’s explanation before responding.

If the detected malware still persists after taking the actions suggested above, the best course of action is to isolate the infected computer and explore more aggressive actions. Follow as many of these steps as are practical:

**1.** Disconnect the infected computer from your network.

**2.** Download at least one alternate anti-malware using another computer connected to the Internet. This chapter includes a list of suggested anti-malware software packages.

**3.** Install the additional product(s) on the infected computer.

**4.** Use the new tool(s) to scan the infected computer.

**5.** Follow instructions presented to remove any detected malware.

If using additional anti-malware tools still does not remove the infection, you should seek additional assistance to clean the computer. It is possible at this point that you’ll need to reinstall the operating system to fully remove all malware.

![image](OEBPS/Images/war.jpg)**WARNING**

In some circumstances, especially in the case of certain rootkits, the only way to completely clean a computer is to reformat the disks and perform a full operating system install. This option is extreme and should only be used as a last resort.

**Malware Prevention Best Practices**

Removing malware and cleaning up after an infection can be time consuming. Although the process of protecting computers from malware may seem to be tedious, it is far better to prevent malware than to clean up after a malware infection. Develop a malware prevention strategy as well as malware mitigation procedures.

Aggressive malware prevention strategies will likely include some of the following:

• Frequent media scans

• Multiple anti-malware software shields

• Frequent signature database updates

• Restrictive software installation policy

• Restrictive download policy

• Restrictive removable policy

• Limited Web browser functionality

• Not running in Administrator mode unless necessary

While each item on this list does reduce the probability of malware infections, it reduces the computer’s usability. Overly aggressive malware prevention measures can become so intrusive that they can interfere with business functions. On the other hand, weak malware prevention can allow infections that can also interfere with, or even prevent, business functions.

The best solution is a balance between the two extremes. The following best practices employ a good measure of malware prevention without being overly intrusive. Follow these suggestions to develop a solid malware prevention strategy:

• Install antivirus and anti-spyware software on all computers.

• Enable all real-time scanning (shield) options.

• Update signature databases and software daily.

• Perform a complete scan of all hard drives at least weekly.

• Perform a quick scan after installing or updating any software.

• Enable boot time virus checking, including boot sector and memory scan at startup options.

• Remove administrator rights from all normal users.

• Apply software and operating system security patches.

• Educate users.

• Block outbound network connections that are not required for your applications.

• Establish incident response capabilities.

• Back up your files.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Malware is already a big problem for organizations. The problem is growing at an increasing pace. McAfee Threats Report has stated that there were more than 100 million unique malware strands as of the end of 2012. The report has also indicated that the number of malware strands grew by over 25 percent just since the beginning of 2012. Malware is becoming more sophisticated and more difficult to contain. The potential payoff for a successful attack can be quite lucrative and the lure of a big score attracts more and more attackers.

Malware gets in the way of normal computer operation and threatens the security of information stored on the computers. Results of malware infestation can range from annoying to destructive and cause substantial loss for any organization. Each incident requires effort and personnel to react to the incident and repair any damage. Such activity requires time and money. Preventing incidents is nearly always less expensive than repairing the damage. Maintaining a secure computer system requires an understanding of the malware threat and the knowledge of how to combat it.

The two most important concepts when combating malware are defense in depth and prevention. A layered approach to securing systems against malware is crucial. No single control will prevent all malware instances, so you need multiple layers. When planning to manage malware threats, prevention efforts are more productive than eradication. Malware is manageable if you plan ahead wisely.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Anti-malware shield**

**Anti-spyware software**

**Antivirus software**

**Buffer overflow**

**Heuristics**

**Malware**

**Ransomware**

**Rootkit**

**Signature**

**Signature database**

**Spyware**

**Trojan horse**

**Virus**

**Zero-day attack**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 5 ASSESSMENT**

  **1.** Which type of malware is a standalone program that replicates and sends itself to other computers?

A. Worm

B. Virus

C. Rootkit

D. Trojan

  **2.** Which type of malware modifies or replaces parts of the operating system to hide the fact that the computer has been compromised?

A. Worm

B. Virus

C. Rootkit

D. Trojan

  **3.** Which type of malware disguises itself as a useful program?

A. Worm

B. Virus

C. Rootkit

D. Trojan

  **4.** Which term describes a unique set of instructions that identify malware code?

A. Fingerprint

B. Signature

C. Rule set

D. Heuristic

  **5.** Which of the following terms means identifying malware based on past experience?

A. Heuristic analysis

B. Log file analysis

C. Signature analysis

D. Historical analysis

  **6.** A signature database that is one month old may potentially expose that computer to how many new threats?

A. 70,000

B. 490,000

C. 210,000

D. 2,100,000

  **7.** Which of the following terms describes a secure location to store identified malware?

A. Safe

B. Vault

C. Signature database

D. Secure storage

  **8.** Which of the following anti-malware components is also referred to as a real-time scanner?

A. Shield

B. Scanner

C. Heuristic engine

D. Antivirus software

  **9.** Which anti-malware tool is included with Windows 7?

A. Windows AntiVirus

B. Windows Doctor

C. Windows Defender

D. Windows Sweeper

**10.** Which of the following best describes a zero-day attack?

A. Malware that no longer is a threat

B. Malware that can exploit a vulnerability but has not yet been released

C. Malware that is actively exploiting vulnerabilities on computers that have not applied the latest patches

D. Malware that is actively exploiting an unknown vulnerability

**11.** What is the best first step to take when malware is discovered soon after installing new software?

A. Uninstall the new software.

B. Scan for malware.

C. Update the new software.

D. Install additional anti-malware software.

**12.** What is the best first step to take if initial actions to remove malware are not successful?

A. Install additional anti-malware software.

B. Rescan for malware.

C. Update the signature database.

D. Disconnect the computer from the network.

**13.** The Morris worm exploited this vulnerability: \_\_\_\_\_\_\_\_.

**14.** Which type of malware covertly primarily collects pieces of information?

A. Spyware

B. Trojan

C. Virus

D. Rootkit

**15.** Why is a rootkit so difficult to detect?

A. Most anti-malware tools don’t scan for rootkits.

B. A rootkit gives administrator privileges to an attacker.

C. A rootkit does not run in memory.

D. A rootkit may have modified the tools used to detect it.

**CHAPTER 6**

**Group Policy Control in Microsoft Windows**

MICROSOFT PROVIDES MORE EFFECTIVE security controls and countermeasures with each new Windows release. This protects computers from new and improved methods of attacks. It can be difficult and confusing to keep track of all the individual security rules as the number of new features continues to grow. Windows provides administrators with the ability to configure many security rules in a central location. The **Group Policy** feature of Windows organizes collections of security rules that control different aspects of how Windows operates. To make administration easier, collections of Group Policy settings can be stored in named objects called **Group Policy Objects (GPOs)**. GPOs can be associated with one or more users and across multiple computers to enforce settings without having to edit each user’s individual settings.

In this chapter, you’ll learn about Group Policy and GPOs and how to maintain them in Windows. You’ll learn how to use GPOs to control what your users can and cannot do. You’ll also learn how to do more than just change settings—you’ll learn how to design GPOs that satisfy your organization’s security policy.

**Chapter 6 Topics**

This chapter covers the following topics and concepts:

• What Group Policy and Group Policy Objects are

• How to make Group Policy conform to security policy

• Which types of GPOs are in the Registry

• Which types of GPOs are stored in Active Directory

• What designing, deploying, and tracking Group Policy controls are

• How to audit and manage Group Policy

• What best practices for Microsoft Windows Group Policy and processes are

**Chapter 6 Goals**

When you complete this chapter, you will be able to:

• Explain Group Policy and Group Policy Objects (GPO)

• Recognize the relationship between Group Policy and security policy

• Illustrate how to make Group Policy conform to security policy

• Describe GPOs in the Windows Registry

• Describe GPOs in Active Directory

• Design Group Policy controls

• Analyze techniques to deploy and track Group Policy controls

• Examine auditing and managing Group Policy

• Outline best practices for Group Policy and processes

• Discuss business challenges of Group Policy

**Group Policy and Group Policy Objects**

The Windows Group Policy feature provides a centralized set of rules that govern the way Windows operates. It provides the ability to define and apply both general and security configuration changes to one or more computers. You can define both Local Group Policy settings and Group Policies in Active Directory. Local Group Policies control the behavior of a single computer. Active Directory Group Policies can apply to any users on any computers defined in Active Directory. Using Group Policy can make administration tasks easier than having to write scripts or individually secure basic security settings.

When booting a computer or logging on, Windows looks up and applies the GPOs for that computer and user. Group Policy uses a “pull” technology, which means that Windows periodically searches for any updated GPOs. If it finds a new GPO, it downloads and applies the changes to the existing environment. It pulls new or changed GPOs to the local computer and ensures that the settings are current. By default, Windows checks for new or updated GPOs at a random interval from 90 to 120 minutes. This automatic update feature ensures that Windows applies any new or updated GPOs, often without requiring that users log off or reboot computers.

** ![image](OEBPS/Images/note.jpg)NOTE**

Windows Server 2012 includes a new feature to make applying GPOs easier. Instead of waiting for individual computers to pull GPO changes, Windows Server 2012 computers can force GPOs to refresh. All of the selected computers will receive the new or changed GPOs within 10 minutes. This new feature, called the Remote Group Policy Update, makes deploying GPOs easier and more dependable.

**FIGURE 6-1** Group Policy.

![image](OEBPS/Images/9781284031652_pg112.jpg)

Group Policy Settings

GPOs make it easy to enforce standard behavior across multiple users or computers. For example, GPOs can easily set firewall settings on multiple computers, define consistent desktop layouts, run scripts when users log on and log off, and redirect folders to network folders. These are only a few of the uses for GPOs. [Table 6-1](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6tab1) lists additional category settings using GPOs.

Group Policy is a central method to customize computer and user settings ([Figure 6-1](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig1)). Most operating systems, including Windows, provide the ability to create boot and logon scripts that run when a computer boots or a user logs on. Group Policy extends this capability by maintaining the commands from a central location. You don’t have to make changes to scripts and copy them to each computer or user’s directory. Group Policy changes are automatically distributed to the right locations. Another benefit that bears a closer look is the periodic update feature of Group Policy. Boot and logon scripts take effect only when you reboot the computer or log off and log on again. Group Policy applies many settings to the current session. This feature causes changes to take effect faster than with using other configuration options.

**technical TIP**

Microsoft publishes a handy spreadsheet listing all of the Group Policy settings included when installing an operating system. Microsoft includes several template files with each Windows version that define many settings. The spreadsheet can be found by visiting the Web site *[http://www.microsoft.com/downloads](http://www.microsoft.com/downloads)*, and searching for “Group Policy Settings Reference.” Microsoft provides several versions of the spreadsheet to cover different Windows releases. This reference contains descriptive information you can use to create and modify GPOs to meet your organization’s security needs.

| **TABLE 6-1** Categories of settings in GPOs. |
| **CATEGORY** || **DESCRIPTION** |
| Password Policy || Sets requirements for password strength, age, history, and storage |
| Account Lockout Policy || Determines how Windows handles accounts locked after failed logon attempts |
| Kerberos Policy || Sets lifetime limits for Kerberos tickets and clock synchronization |
| Audit Policy || Defines events Windows should record in audit files |
| User Rights Assignment || Assigns individual user rights that define what general actions users can perform, such as “Access this computer from the network” or “Change the system time” |
| Security Options || Offers options granting rights that define what security-related actions users can perform, such as “Allowed to format and eject removable media” or “Require smart card” |
| Event Log || Defines maximum size, retention settings, and guest access settings for event logs |
| Restricted Groups || Lists users in security-sensitive groups and to what other groups the restricted group can belong |
| System Services || Defines startup mode and access permissions for system services |
| Registry || Defines access permissions and audit settings for Registry keys |
| File System || Defines access permissions on discretionary access control lists (DACLs) and audit settings for system access control lists (SACLs) |
|   ||   |

GPO Linking

You can link GPOs to specific users to customize settings for groups of users or even individual users. Users who log on anywhere in the Active Directory domain will get GPOs linked to their user account. You can also link GPOs to **organizational units (OUs)**. In fact, you must link GPOs to at least one computer, domain, or OU for the GPO to be active. GPOs that aren’t linked to a computer, domain, or OU are defined but inactive. You can define OUs to logically group computers into functional groups, such as “Accounting,” “Manufacturing,” and “Distribution.” Once you define one or more OUs, you can add computers to each OU to logically group them together. When you link GPOs to OUs, Windows will download and apply only the appropriate GPOs for the computer and the user logging on.

** ![image](OEBPS/Images/note.jpg)NOTE**

You may define a desktop with icons related to manufacturing applications for the Manufacturing OU. A user who logs on to a computer in the Manufacturing OU will see the desktop specific to manufacturing. Users who log on to a computer that is not in the Manufacturing OU will see a different desktop.

**Making Group Policy Conform to Security Policy**

Group Policy is a functional feature of Windows that has little meaning by itself. It is a mechanism used to apply controls enforcing your security policy. For example, should you set a maximum password age for all the computers in your environment? The answer is: “It depends.” Setting a maximum password age is generally a good idea, but not something you should arbitrarily enforce. Your security policy should direct any settings you add to GPOs. In fact, the GPOs you define and use should conform to your security policy. There are two main reasons for making Group Policy conform to your security policy: to allow management to meet security responsibilities, and to ensure that there are no gaps in your security policy and your policy doesn’t contain additional controls.

Security Responsibility

First, it is management’s responsibility to ensure the security of an organization’s assets, including information. All actions IT security personnel take to secure information occur within the authority granted by management to do the job. IT security controls that exceed management’s security goals also exceed granted authority. Technically, management authorizes IT security to do only what the security policy states. It is important that management include all necessary security goals in your organization’s security policy. The policy provides the direction for creating controls to secure information. A strict security policy interpretation means that any control that the security policy does not address is not important to the organization.

![image](OEBPS/Images/war.jpg)**WARNING**

Your organization’s culture should provide guidance on interpreting the security policy. A strict security policy interpretation means that no security controls exist unless they are directed by the policy. A less strict interpretation is more common. It allows IT security to exercise some discretion to implement best practices that may not be explicitly defined in the security policy.

Security Policy and Group Policy

Second, your Group Policy definition should satisfy your security policy goals and not add any arbitrary controls. Your primary goal for designing Group Policy should be to ensure your Group Policy does not leave any gaps in your security policy. The GPOs you create and implement should meet all the goals in your security policy. It shouldn’t add any controls that are not covered in the policy. When your environment’s Group Policy conforms to your security policy, you create a validation method of your security policy. You can record the existence and performance of GPOs as evidence that you are complying with your security policy. You’ll learn how to audit how your Group Policy is functioning later in this chapter.

Making Group Policy conform to your security policy is a three-step process. First, examine a list of GPO settings that already exist in the default Windows templates. The Group Policy Settings Reference from Microsoft is an excellent resource for this task. Identify any GPO settings that satisfy parts of your security policy. Activate all settings that are appropriate for your policy.

The second step is to identify any elements in your security policy that do not already exist in default Windows templates. Then list the elements that new GPO settings can address. For example, suppose you want to hide the Recycle Bin on every user’s desktop. You can easily create a new GPO with this setting.

The third step in making Group Policy conform to your security policy is to create new GPOs for each of the remaining goals in your security policy that you identified in the second step.

Group Policy Targets

Group Policy allows you to define the specific targets for each rule. Some rules on your security policy apply to all users on all machines while others do not. For example, the rule “All users must create passwords for user accounts that conform to the strong password policy” applies to all users. On the other hand, the rule “Members of the Database Administrator group must change passwords at least every 90 days” applies only to users who are members of the Database Administrator user group. Windows provides you with the ability to specify GPO scope, which defines how Windows enforces security rules.

Active Directory provides the ability to define Group Policy at different levels. Windows looks up all applicable GPOs when a computer boots or a user logs on. Windows applies multiple GPOs in the following order (lower to higher) ([Figure 6-2](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig2)):

• **Local GPOs**—GPOs defined and stored on the local computer

• **Site GPOs defined in AD**—GPOs defined in AD for a specific site

• **Domain GPOs**—Domainwide GPOs defined in AD

• **Organizational unit GPOs**—OU GPOs defined in AD

**FIGURE 6-2** Group Policy Object order.

![image](OEBPS/Images/9781284031652_pg116.jpg)

Any setting in a higher-level GPO will override a lower-level GPO setting. For example, a setting in a domain GPO will override a conflicting setting in a local GPO. This behavior applies only if a GPO setting contains a specific value. If the higher-level GPO setting value is “Not Configured,” then Windows applies the value of the lower-level GPO setting.

Creating GPOs that conform to your security policy enables you to validate and evaluate each part of the policy. You’ll learn later in this chapter how to list and audit GPOs. Reporting on GPOs makes it easy to evaluate how well your organization is complying with your security policy.

**Types of GPOs in the Registry**

Windows stores many Group Policy settings in the **Registry**. The Registry is a database on each Windows computer that stores configuration settings for the computer and users. The Group Policy Settings Reference spreadsheet lists the key locations for settings stored in the Registry. The Registry stores Group Policy settings either in HKEY\_CURRENT\_USER (HKCU) or HKEY\_LOCAL\_MACHINE (HKLM). HKCU keys define settings that are specific to each user. HKLM keys define settings that apply to the computer, regardless of who is logged on.

**technical TIP**

Recall that Microsoft publishes a handy spreadsheet that lists all of the Group Policy settings included when you install your operating system. Microsoft includes several template files with each Windows version that define many settings. You can go to *[http://www.microsoft.com/downloads](http://www.microsoft.com/downloads)* and search for “Group Policy Settings Reference” to find the spreadsheet. Microsoft provides several versions of the spreadsheet to cover different Windows releases. This reference contains descriptive information you can use to create and modify GPOs to meet your organization’s security needs.

Open the spreadsheet and examine the “Policy Path” column to find the key for settings stored in the Windows Registry.

**technical TIP**

You can open the Local Group Policy Editor using these steps:

**1.** Choose the Windows Start button.

**2.** Type gpedit.msc in the Run box.

**3.** Press the Enter key.

Local Group Policy Editor

It is easy to view and edit Group Policy settings with the Group Policy Editor. There are two main types of Group Policy settings: Local Group Policy settings and Active Directory Group Policy settings, which you’ll learn about in the next section. You define local Group Policy settings on each computer and Windows stores the settings on that computer. All of the local Group Policy settings apply to a single computer. When you first open the **Local Group Policy Editor**, you see the two main groups of settings, “Computer Configuration” and “User Configuration” settings. [Figure 6-3](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig3) shows the Local Group Policy Editor.

Notice the two main categories of settings in the Local Group Policy Editor. The settings under the Computer Configuration category are stored in the Registry under the HKLM entry. The settings under the User Configuration category are stored under the HKCU entry. Although the Windows Registry Editor can be used to modify Group Policy settings, the Local Group Policy Editor is easier and safer. The Local Group Policy Editor allows you to change only Group Policy settings and ensures the settings are stored properly and in the correct location in the Registry. Changing Group Policy settings in the Local Group Policy Editor is easy. Find the setting you want to change, choose Edit, and change the setting to the value you choose. [Figure 6-4](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig4) shows the modified value for the Turn Off user-installed desktop gadgets setting. When you enable this setting, users will not be able to launch any of their own user-installed gadgets in the sidebar of their desktop.

**FIGURE 6-3** Local Group Policy Editor.

![image](OEBPS/Images/9781284031652_pg117.jpg)

**FIGURE 6-4** Changing a setting in the Local Group Policy Editor.

![image](OEBPS/Images/9781284031652_pg118.jpg)

**technical TIP**

You can follow these steps to change the same setting you see in [Figure 6-4](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig4).

**1.** In the Local Group Policy Editor, expand the Computer Configuration, Administrative Templates, and Windows Components items.

**2.** Select Desktop Gadgets.

**3.** On the right side of the window, select Turn Off user-installed desktop gadgets.

**4.** Right-click to open the context menu and select Edit.

**5.** Choose the Enabled option button to enable the setting.

**6.** Choose OK to save the setting and close the setting editor dialog box.

GPOs in the Registry Editor

Since Group Policy settings are stored in the Registry, they can be edited directly using the **Registry Editor**. Windows stores all currently active GPOs in the Registry under the HKCU entry. When a user logs on, and every 90 to 120 minutes thereafter, Windows will update the HKCU hive with the most current GPOs that apply to the current user. This updater will also occur within 10 minutes if a Windows Server 2012 computer refreshes GPOs with the Remote Group Policy Update. Each GPO has a globally unique identifier (GUID) that uniquely identifies it as a Windows object. The GPO GUID is the key Windows uses to store the GPO in the Registry. Windows stores current GPOs under the key: HKEY\_CURRENT\_USER\\Software\\Microsoft\\Windows\\CurrentVersion\\Group Policy Objects\\. [Figure 6-5](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig5) shows the GPO setting for “Turn Off user-installed desktop gadgets” from the previous example in the Registry Editor.

![image](OEBPS/Images/war.jpg)**WARNING**

Be very careful when using the Registry Editor. Changing the wrong Registry data in the Registry Editor can make your computer unstable. When another editor is available to edit data, such as the Local Group Policy Editor, use it instead of the Registry Editor.

**FIGURE 6-5** Group Policy setting in the Registry Editor.

![image](OEBPS/Images/9781284031652_pg119.jpg)

**technical TIP**

You can follow these steps to view the same setting you see in [Figure 6-5](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig5).

**1.** Select the Windows Start button.

**2.** Type regedit.exe in the Run box, then press the Enter key to run the Registry Editor.

**3.** Select Edit > Find from the menu bar.

**4.** Type Turn Off User Installed Gadgets, then choose Find Next.

**5.** Examine the full path to the GPO setting in the status area at the bottom of the Registry Editor window.

a. If you don’t see a path in the status bar, choose View > Status Bar from the menu bar.

**Types of GPOs in Active Directory**

Although defining local GPOs provides positive control over single computers, the real power of Group Policy is in Active Directory (AD). Defining GPOs in AD gives you the ability to centralize security rules and control how Windows applies each rule. You create AD GPOs on a domain controller. Windows stores GPOs in AD in such a way that the domain controller automatically replicates the GPOs to other domain controllers. This feature reduces the workload of administrators. Using Group Policy in AD relieves the need to define security rules on multiple computers one at a time.

Group Policy Management Console

AD GPOs are created on the domain controller using the **Group Policy Management Console (GPMC)** ([Figure 6-6](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig6)). The GPMC looks a lot like the Local Group Policy Editor, but it allows you to do far more than just create GPOs and maintain their settings. Here is a list of some of the actions you can perform in the GPMC:

• Create and edit GPOs

• Import and export GPOs

• Copy and paste GPOs

• Back up and restore GPOs

• Search for GPOs

• Create reports on GPOs

Although there are multiple ways to create GPOs, the most common method is to create GPOs under the desired domain in the GPMC. New AD GPOs don’t actually do anything until you link them with some entity. You’ll learn about GPO linking later in this chapter.

**FIGURE 6-6** Group Policy Management Console.

![image](OEBPS/Images/9781284031652_pg121.jpg)

**technical TIP**

When you promote a server to a domain controller, Windows automatically installs the GPMC on that server. You can follow these steps to open the GPMC:

**1.** Choose the Windows Start button.

**2.** Select All Programs > Administrative Tools > Group Policy Management.

You can also follow these steps to open the GPMC:

**1.** Choose the Windows Start button.

**2.** Type gpmc.msc in the Run box.

**3.** Press the Enter key.

GPOs on the Domain Controller

Windows stores AD GPOs in a folder on the domain controller. Computers that are in a domain retrieve all the GPOs that apply to that computer when a user logs on using a domain account or when a computer connects to the domain. The domain controller searches for the appropriate GPOs and sends them to the computer. Of course, the computer and user must first successfully authenticate to the domain controller. Then, every 90 to 120 minutes the remote computer asks the domain controller if any GPOs have changed. If they have, the domain controller sends the new or updated GPOs and the remote computer applies them.

The domain controller stores AD GPOs in a folder named Policies ([Figure 6-7](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig7)). Windows creates a Policies folder for each domain. For example, the full pathname for the Policies folder for a domain named [corp.domain.com](http://corp.domain.com) is: C:\\Windows\\soldev\\soldev\\corp.domain.com\\Policies.

Windows stores each GPO in a subfolder under Policies. The name of each subfolder under Policies is the GUID for the GPO. You can navigate to the GPO in Windows Explorer to see where Windows stores the GPO settings. Each GPO folder, or GPO shell, contains two subfolders named Machine and User. These subfolders contain the GPO settings for both the machinewide and user-specific settings. Each subfolder contains policy files for defined GPOs that apply to a domain.

![image](OEBPS/Images/war.jpg)**WARNING**

If you installed Windows in a directory other than C:\\Windows, then the path to Policies for your computer will be different. Just replace C:\\Windows with your Windows install folder to get the correct path to the Policies folder.

**FIGURE 6-7** GPOs in the Policies folder.

![image](OEBPS/Images/9781284031652_pg122.jpg)

**FIGURE 6-8** Linking AD GPOs in the GPMC.

![image](OEBPS/Images/9781284031652_pg123.jpg)

Unlike Local GPOs, AD GPOs do nothing until you link them to one or more **containers**. An AD container can be a site, a domain, or an OU. The Group Policy Objects section of the GPMC lists all defined GPOs. You can edit existing GPOs or add new GPOs. You must link GPOs to one or more sites, domains, or OUs to make the GPOs do anything ([Figure 6-8](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig8)). A single GPO may be linked to multiple containers, and each container can have multiple GPOs linked to it. The easiest way to link GPOs to containers is from the context menu of the container.

**technical TIP**

Follow these steps to link a GPO to a container:

**1.** In the GPMC, select a container. For example, select the newly created OU named testOU.

**2.** Open the context menu for testOU by right-clicking on testOU.

**3.** Choose Link an Existing GPO.

**4.** Select the desired GPO from the list of defined GPOs.

**5.** Choose OK.

**Designing, Deploying, and Tracking Group Policy Controls**

One of the most important considerations when designing GPOs is efficiency. You want to define and link the minimum number of GPOs to satisfy your security policy. Creating too many GPOs will increase the time and effort you’ll need to administer and maintain your security policy. Having too many GPOs also increases the possibility of errors and opportunities for attackers to compromise your systems. The simplest environment would be one in which you define one set of GPOs that applies to all computers and all users in all domains. Unfortunately, few environments end up being that simple. Functional demands often require different controls for various computers and users.

GPO Application Order

You can define several layers of GPOs that work together to ensure you enforce your security policy for all computers and all users. Windows gives you the ability to create high-level GPOs that enforce large-scale security settings and more specific GPOs that allow you to fine-tune settings for specific situations. Recall from earlier in this chapter that Windows applies GPOs in a specific order. Knowing this order lets you put more generic settings in GPOs that Windows applies first, and more specific settings in GPOs Windows applies later in the process.

Recall that Windows applies GPOs in this order:

• **Local GPOs**—GPOs defined and stored on the local computer

• **Site GPOs defined in AD**—GPOs defined in AD for a specific site

• **Domain GPOs**—Domainwide GPOs defined in AD

• **Organizational unit GPOs**—OU GPOs defined in AD

Design your GPOs with this order in mind. Since Windows applies OU GPOs last, any global GPO settings should go here. Identify any settings you want to enforce for all computers and users and define GPOs that you link to one or more OUs. Then you can define GPOs and link them to lower-level containers for settings that do not apply to all computers or users. Since OU GPOs have the largest scope, they are the easiest to implement and maintain. Start by reviewing your OU structure. You should ensure your OU structure realistically represents your functional organizational structure as closely as possible. OU designs that closely represent functional structures make it easier to create appropriate OU-level GPOs that satisfy your security policy. For example, suppose your security policy requires specific application and object access for members of the Human Resources (HR) Department. If you define all users in the HR Department in the HR OU, it is easy to create GPOs for the OU that affect all HR Department users.

![image](OEBPS/Images/war.jpg)**WARNING**

OU GPO settings will override any settings that exist in lower-level GPOs. For example, if a setting exists in both a site GPO and an OU GPO, the OU GPO setting will override the site GPO setting. Don’t include settings in OU GPOs that may require local overrides.

All security control design starts with your security policy. Once you validate your OU design and identify the controls you’ll need to satisfy your security policy, you can define the control scope. In the context of GPO settings, the scope of any control is the group of computers or users to which each GPO applies. Settings scoped to the OU level should exist in OU GPOs. You can define any settings that apply only to some computers or users in local, site, or domain GPOs. You can also define limited scope GPOs at the OU level and use filters to limit the scope. You’ll learn about GPO filters later in this chapter. As a general rule, define GPO settings either at the lowest level that includes all of the desired computers and users or at the OU level using filters when the OU approach meets your needs. For example, you can define any settings that apply to all users for a specific computer in either a local GPO, site GPO, or a filtered OU GPO. The main difference is that Windows stores local GPOs on the affected computer and stores site and OU GPOs in AD. OU GPOs also make administration simpler since you define and link GPOs at a single level.

Security Filters

Windows applies GPOs to all computers and users in a container by default. That means all computers and users in an OU will inherit any OU GPOs defined for that OU by default. You can change that behavior with **security filters** ([Figure 6-9](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig9)) if you want an OU GPO to apply only to some computers or users in the OU. The GPMC allows you to add as many security filters for GPOs as necessary to satisfy your security policy. You can limit a GPO to users, groups, or computers. Once you define a security filter, Windows will apply that GPO only to subjects defined in the filter. This option gives you much more control over how Windows applies GPOs you define at the OU level.

![image](OEBPS/Images/war.jpg)**WARNING**

The GPMC creates new GPOs that apply to all authenticated users. If you create filters to limit the scope of a GPO, make sure you delete the default filter of “Authenticated Users.”

**technical TIP**

Follow these steps to define a security filter for an OU GPO:

**1.** In the GPMC, select and expand a domain.

**2.** Expand Group Policy Objects and select a GPO.

**3.** Select the Scope tab in the right pane and then select Add in the Security Filtering section.

**4.** You have the option to change the type of objects and the location Windows uses to build the filter options. The defaults will allow you to select users, groups, or built-in security principles from the domain you selected in Step 1. You can select the Object Types button and select the Computers check box to define a filter for specific computers.

**5.** Enter the user, group, or computer name for this filter. Choose Check Names to validate the object name you entered.

**6.** Choose OK to create the new filter and return to the GPMC.

**FIGURE 6-9** GPO security filters.

![image](OEBPS/Images/9781284031652_pg126.jpg)

GPO Windows Management Instrumentation (WMI) Filters

**Windows Management Instrumentation (WMI)** is the infrastructure Windows uses to maintain and exchange management and operations data. **WMI filters** give you even more control over when and where GPOs apply. You can create multiple WMI filters for each domain and then link each filter to one or more GPOs. You can link only one WMI filter to each GPO. Windows evaluates the GPO’s WMI filter before applying a GPO and proceeds only if the WMI filter expression evaluates to TRUE. WMI filters allow you to query the target environment and apply security settings only in certain situations.

For example, suppose you want to apply a GPO only for computers that are running Microsoft Windows Vista Ultimate. You could define a WMI filter that would restrict the GPO to the desired machines. Windows uses the **WMI Query Language (WQL)** to define the queries for the filters. WQL is a subset of the SQL language many database engines use to query data. The following WQL query will return TRUE when the target computer is running Microsoft Windows 7 Ultimate:

Select \* from Win32\_OperatingSystem where Caption = Microsoft Windows 7 Ultimate

**technical TIP**

You can find more information on WQL on Microsoft TechNet at: *[http://technet.microsoft.com/en-us/library/ee176998.aspx](http://technet.microsoft.com/en-us/library/ee176998.aspx)*.

If the target computer is running Microsoft Windows 7 Ultimate, Windows will apply the GPO. This additional feature gives administrators the ability to define GPO scope at a very specific level of detail. Once you define the WMI filter in the GPMC, you can link the filter to any GPO by just selecting the desired WMI filter from the drop-down list in the GPO’s WMI Filtering section ([Figure 6-10](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6fig10)).

**FIGURE 6-10** WMI filters.

![image](OEBPS/Images/9781284031652_pg127.jpg)

**technical TIP**

Follow these steps to define a WMI filter and link it to an existing GPO:

**1.** In the GPMC, select and expand a domain.

**2.** Expand WMI Filters, open the context menu and choose New.

**3.** Type the desired name and description, then choose Add.

**4.** Type the following text into the query editor: \* from Win32\_OperatingSystem where Caption = “Microsoft Windows 7 Ultimate”.

**5.** Choose OK, then Save to create the new WMI filter and return to the GPMC.

**6.** Expand Group Policy Objects and select a GPO.

**7.** Open the drop-down list in the WMI Filters section and select the newly created WMI filter.

Deploying Group Policy

Windows ensures that new and changed GPOs get distributed and applied every 90 to 120 minutes. In some cases, you may want to force GPO distribution. In Windows Server 2012, you can force a GPO refresh from within the GPMC. For all versions of Windows, you can use the **Group Policy Update tool** to accomplish this task. The tool also provides the ability to force user logoff or system boot when setting changes require these actions. You can use the Group Policy Update tool whenever you want to ensure that settings are in place on target computers.

Follow these steps to run the Group Policy Update tool:

**1.** Choose the Windows Start button > Command Prompt.

**2.** Enter the following command: gpupdate.exe.

The Group Policy Update tool supports several options that change the scope of targets or additional actions. [Table 6-2](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6tab2) lists the most common options for gpupdate.exe.

| **TABLE 6-2** Gpupdate.exe options. |
| **OPTION** || **DESCRIPTION** |
| /Target:{Computer | User} || Limits the target of the update to only user or computer policy settings. |
| /Force || Reapplies all settings. The default is to apply only new or changed settings. |
| /Wait:value || Sets wait time for the specified number of seconds for the processing to finish. A value of –1 means wait forever. |
| /Logoff || Forces a user logoff after the update processing completes. |
| /Boot || Forces a system reboot after update processing completes. |
| /Sync || Synchronously applies the next logoff or boot policy setting. |

**Auditing and Managing Group Policy**

Once you design and deploy GPOs to support your security policy, it is important to validate your Group Policy to ensure that you have defined the right GPOs. Auditing Group Policy ensures the GPOs you have in place satisfy your security policy. As you change users and computers in your organization, you may find that your GPOs no longer satisfy your security policy. It is important to audit Group Policy periodically to ensure that any changes in your organization have not reduced your GPO’s effectiveness.

Microsoft provides two main tools you will use to audit Group Policy: Group Policy Inventory and Resultant Set of Policy tool. The first tool, Group Policy Inventory, provides an inventory list of GPOs and many other computer and user settings. You must download this program from Microsoft’s Web site and install it on your computer—it isn’t included when you install Windows. The second tool is included with Windows. The Resultant Set of Policy tool shows what settings Windows applies to a specific user on a specific computer.

** ![image](OEBPS/Images/note.jpg)NOTE**

Windows Server 2012 adds a new tab to the GPMC. The new Status tab shows the current replication status of the selected GPO. This new option makes it easier to see the deployment status of your GPOs.

Group Policy Inventory

The first step in using the **Group Policy Inventory tool** (gpinventory.exe) is to download and install it on your computer. You can get the tool from Microsoft’s Web site. Gpinventory queries the computers you select for system and GPO information and then displays the results in a single window. This tool makes it easy to collect information from many computers across a domain to ensure that your Group Policy is deploying the way that you expect. Follow these steps to run Gpinventory:

**1. Open a command prompt window**—Choose the Windows Start button > Command Prompt.

**2. Change directories to the install directory for the Gpinventory tool**—Enter: cd C:\\program files (x86)\\Windows Resource Kits\\Tools.

**3. Run Gpinventory**—The command is gpinventory.exe.

**4. Choose the computers to query**—Query > Select Computers to target using Active Directory.

**5. Choose the information you want to gather**—Query > Select information to gather.

**6. Execute the query**—Query > Run Query.

After Group Policy Inventory gathers the information you requested, it displays the results in the main window. You can view the details and save the information to analyze later. The Group Policy Inventory tool will save the results in an XML file or a text file. Use the Results menu item to save the results in either format. Group Policy Inventory is an important tool to provide validation of Group Policy in your domain. Use it after any GPO change and periodically to ensure computers and users are operating with the settings you define to comply with your security policy.

**technical TIP**

You must download and install the Group Policy Inventory tool before you can use it. You can get the tool from the Microsoft Web site. Go to: *[http://www.microsoft.com/en-us/download/details.aspx?id=14126](http://www.microsoft.com/en-us/download/details.aspx?id=14126)* to download the tool.

Analyzing the Effect of GPOs

The other common tool you will use to audit GPOs is the **Resultant Set of Policy (RSOP) tool**. The RSOP tool is included in Windows and shows the specific settings that will result from applying GPOs to a specific user logged on to a specific computer. The Group Policy Inventory tool can include some RSOP results, but the standalone RSOP tool provides access to more details. RSOP is a great way to analyze the effect of any GPO changes. RSOP provides two modes of operations—logging mode to show existing GPOs and planning mode that shows the effect of planned GPO changes.

You can run RSOP using two methods. The first method runs RSOP in logging mode that defaults to the currently logged-on user on the current computer. After the initial information displays, you can easily change the user or computer and generate updated GPO information. Follow these steps to run RSOP in logging mode:

**1.** Choose the Windows Start button.

**2.** Type rsop.msc in the Run box, and then press Enter.

**3.** The Resultant Set of Policy window displays the current settings for the user who is currently logged on. The display looks like the GPMC, but you can’t change any settings here.

**4.** If you want to run RSOP for another user or computer, open the context menu (by right-clicking) for the main item in the left pane. This item will be your username and computer name.

**5.** On the context menu, select Change Query.

**6.** Select the desired computer and user on the next two dialog boxes.

**7.** RSOP will calculate the effective settings using the new user and computer you provided.

RSOP also runs in a powerful planning mode. The planning mode is useful when you want to analyze the effects of a GPO change before deploying the change. Follow these steps to run RSOP in planning mode:

**1.** Choose the Windows Start button > Administrative Tools > Active Directory Users and Computers.

**2.** Open the context menu of the desired object by right-clicking the desired computer, user, domain, or OU.

**3.** Select All Tasks > Resultant Set of Policy (Planning).

**4.** The next several screens ask you to provide information that describes the planned target environment. RSOP will evaluate the GPOs based on the information you provide here. You can provide the following information:

a. **User and Container**—Run RSOP for any user for any container.

b. **Advanced options**—Set advanced simulation conditions.

c. **Groups**—Analyze the effects of adding or removing group assignments.

d. **WMI Filters**—See what effects different WMI filters produce.

Group Policy Inventory and RSOP help you validate the Group Policy you have in place and evaluate how changes will affect your environment. Both tools are important components of a complete administrator’s toolbox.

**Best Practices for Microsoft Windows Group Policy and Processes**

Group Policy is an important component of secure Windows environments. Many resources are available to help you follow established best practices for secure systems. You’ll learn about a few of the recommended guidelines and available resources in this section.

Group Policy Design Guidelines

While there are many ways to design Group Policy for your organization, a few guidelines can help focus your efforts. Follow these guidelines to design a Group Policy that will minimize administrative effort while satisfying your security policy. Most important, don’t make your Group Policy overly complex. Simplicity is always an asset in any policy. Keep your security policy and Group Policy as simple as possible while still fulfilling your goals. Here are a few additional guidelines that should result in simple and effective Group Policy:

• Define OUs that reflect your organization’s functional structure.

• Create OU GPOs for controls required in your security policy.

• Use meaningful names for GPOs to make maintenance and administration easier.

• Deploy GPOs in a test environment before deploying to your live environment.

• Use security filtering and WMI filters to restrict settings when necessary.

• Back up your GPOs regularly.

• Do not modify the default policies—instead, create new GPOs.

Ensure your Group Policy is both effective and easily maintainable. Only define and deploy the GPOs you actually need to meet the goals of your security policy. Extra GPOs will only complicate administrative tasks and may get in the way of completing primary business functions. The process of migrating from an environment with few controls to a secure environment can be frustrating both for end users and administrators. Make sure you test all GPOs before deploying them to a live environment. Conduct tests that will allow you to evaluate how each GPO will affect your users’ abilities to do their jobs. New security settings that stop people from doing their jobs are harmful to your business. Be aware of any new policies that may result in a negative business impact. When security requirements conflict with business requirements, it is up to the organization’s management to resolve the conflict. The best security solutions always support both security and business concerns.

| **TABLE 6-3** Group Policy best practices resources. |
| **RESOURCE** || **DESCRIPTION** || **WHERE TO FIND IT** |
| Group Policy Best Practices Analyzer || Helps you identify Group Policy configuration errors or dependency issues that may prevent settings from functioning as you expected. || In Server Manager, open a server role and select Scan This Role under Best Practices Analyzer. |
| Group Policy Settings Reference || Spreadsheets that list the policy settings included in the Administrative template files that are delivered with the Windows operating systems. || *[http://www.microsoft.com/downloads](http://www.microsoft.com/downloads)* (Search for Group Policy Settings Reference) |
| Microsoft Server 2008 R2 Security Baseline || Resources for planning, deploying, and monitoring the security baselines of servers running Windows Server 2008 R2. || *[http://technet.microsott.com/en-us/library/gg236605.aspx](http://technet.microsott.com/en-us/library/gg236605.aspx)* |
| Microsoft Server 2012 Security Baseline || Resources for planning, deploying, and monitoring the security baselines of servers running Windows Server 2012. || *[http://technet.microsoft.com/en-us/library/jj898542.aspx](http://technet.microsoft.com/en-us/library/jj898542.aspx)* |
| Windows 7 Security Baseline || Resources for planning, deploying, and monitoring the security baselines of computers running Windows 7 and BitLocker drive encryption. || *[http://technet.microsoft.com/en-us/library/ee712767.aspx](http://technet.microsoft.com/en-us/library/ee712767.aspx)* |
| GPOAccelerator || Helps you automatically deploy the recommendations in the Security Compliance Management Toolkit. The security guides in the toolkit recommend Group Policy configurations and Security Template configurations that are enforced via Active Directory Domain Services. || *[http://technet.microsoft.com/en-us/library/cc748655.aspx](http://technet.microsoft.com/en-us/library/cc748655.aspx)* |
| Group Policy Management Pack for Operations Manager 2007 || Includes monitors, rules, views, and knowledge for the monitoring of the application of Group Policy settings on Windows Server 2008. It provides a knowledge base of useful information to help administrators resolve an issue when Group Policy fails to process. || *[http://myitforum.com/cs2/files/folders/mps/entry120565.aspx](http://myitforum.com/cs2/files/folders/mps/entry120565.aspx)* |
|   ||   ||   |

There are several other resources listed in [Table 6-3](#16_Chaper6_split_001.xhtml#ba-9781284031652-ch6tab3) that make designing and implementing Group Policy across a domain easier. Use these resources as well as the tools and resources you have already seen. They keep you from reinventing the wheel. They also provide input on solving issues that you may not have encountered yet.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Group Policy is one of the most important security and administrative features in Windows. It enables administrators to effectively implement a security policy across a network of computers. Group Policy and Active Directory provide a centrally controlled environment to define and deploy changes to security and other configuration settings. Although Group Policy is most often discussed in security contexts, it is an efficient way to enforce standard settings across a diverse environment. You can use Group Policy to enforce password aging settings and a default screen saver. Group Policy uses are nearly endless. A good Group Policy design can reduce the workload of administrators and greatly enhance their abilities to enforce organizational standards in a consistent manner.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Container**

**Group Policy**

**Group Policy Inventory tool**

**Group Policy Management Console (GPMC)**

**Group Policy Object (GPO)**

**Group Policy Update tool**

**Local Group Policy Editor**

**Organizational unit (OU)**

**Registry**

**Registry Editor**

**Resultant Set of Policy (RSOP) tool**

**Security filter**

**Windows Management Instrumentation (WMI)**

**WMI filter**

**WMI Query Language (WQL)**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 6 ASSESSMENT**

  **1.** The Windows Group Policy feature provides a centralized set of rules that govern the way Windows operates.

A. True

B. False

  **2.** Windows checks for new or updates GPOs every \_\_\_\_\_\_\_\_ minutes.

  **3.** Which of the following statements best describes the relationship between security policy and Group Policy?

A. Security policy should implement Group Policy.

B. Security policy is derived from Group Policy.

C. Group Policy should implement security policy.

D. Group Policy supersedes security policy.

  **4.** Who holds the primary responsibility to ensure the security of an organization’s information?

A. IT security

B. Management

C. Information system users

D. Human resources

  **5.** Which tool would you most likely use to edit Group Policy settings in a standalone computer?

A. Local Group Policy Editor

B. Registry Editor

C. Group Policy Management Console

D. Resultant Set of Policy Editor

  **6.** You can only edit user-specific Group Policy settings in the Windows Registry Editor.

A. True

B. False

  **7.** Defining GPOs in \_\_\_\_\_\_\_\_ gives you the ability to centralize security rules and control how Windows applies each rule.

  **8.** Which folder does Windows use to store AD GPOs on the domain controller?

A. Windows

B. Policies

C. GPO

D. ADdata

  **9.** Windows stores each GPO in a subfolder with the same name as the \_\_\_\_\_\_\_\_ of the GPO.

**10.** Which of the following features allows you to restrict the groups to which a GPO applies?

A. Security filter

B. WMI filter

C. GPO link

D. OU list

**11.** Which of the following features allows you to restrict the types of operating systems to which a GPO applies?

A. Security filter

B. WMI filter

C. GPO link

D. OU list

**12.** Windows will automatically cause a user logoff or system reboot after applying new or changed GPOs.

A. True

B. False

**13.** Which of the following tools lists information about deployed GPOs and other computer specific attributes?

A. Gpupdate.exe

B. RSOP

C. Gpedit.msc

D. Gpinventory.exe

**14.** You can use the \_\_\_\_\_\_\_\_ tool to view the effective settings after all current GPOs are applied to a specific user.

**15.** Which of the following resources is installed with Windows?

A. Group Policy Settings Reference

B. Security Compliance Management Toolkit

C. Group Policy Best Practices Analyzer

D. GPOAccelerator

**CHAPTER 7**

**Microsoft Windows Security Profile and Audit Tools**

THE GOAL OF INFORMATION SECURITY is to prevent loss by protecting the confidentiality, integrity, and availability of information. Security controls protect resources and manage controls in a larger environment using group policy. How do you know if your system is meeting your security goals? You can verify that controls are working, but how do you know if they are getting the job done? How do your controls compare with other environments? Are your systems configured with similar controls using recognized best practices? Is your environment radically different?

In this chapter, you’ll learn how to analyze your current computer settings. You’ll learn how to compare them with established settings and goals. You’ll learn how to identify differences from your desired settings or overall security goals. You’ll also learn how to fix any issues that you identify and how to monitor your environment’s behavior over time to ensure that you’re staying secure.

**Chapter 7 Topics**

This chapter covers the following topics and concepts:

• What profiling Microsoft Windows security is

• What the Microsoft Baseline Security Analyzer (MBSA) is

• What Shavlik security analyzers are

• What Secunia personal and corporate security analyzers are

• What a Microsoft Windows security audit is

• What Microsoft Windows security audit tools are

• What best practices for Microsoft Windows security audits are

**Chapter 7 Goals**

When you complete this chapter, you will be able to:

• Describe the need for profiling the security of a Windows system

• Explain how to use common Windows security profiling tools

• Explain the process of auditing Windows security

• Describe how to use Windows security audit tools

**Profiling Microsoft Windows Security**

It is difficult to know if your controls are correct without the ability to compare other configurations. You want to be able to compare configuration settings of your systems with the configurations of systems you know to be secure. System administrators often collect reported configuration settings for comparison with similar settings. A collection of configuration settings is called a **baseline** and can take on many forms. Each baseline generally contains a collection of configuration settings intended for a specific purpose. For example, a collection of security-related settings is commonly referred to as a security baseline.

Profiling

Once you have a baseline, or snapshot, of one or more of your computers, what do you do with it? One of the most effective uses of baselines is to compare them with known “good” baselines. There are many definitions for a “good” baseline. It generally means a baseline of a secure system. The process of comparing configuration settings of a computer with a collection of secure configuration settings makes it easy to see the differences. An alternate approach would be to define an insecure baseline and look for similarities or differences with your systems.

The process of comparing real computer configurations to known baselines is called **profiling**. Profiling in general means extracting information about someone or something based on known attributes. Many movies contain plot devices that depend on profiling. Westerns provide a great example of character profiling. In many old Westerns, the good guys wore white hats. The bad guys wore black hats. It was easy to tell who was good and who was bad. The process of comparing the known wardrobe characteristics with what a specific character wears is called profiling the character.

While profiling is not accurate in all cases, it quickly identifies attributes or characteristics associated with a subject of a predefined group. In old Western movies, wearing a black hat doesn’t make a character bad, but it makes the audience suspicious of that character. Profiling in the operating system security context is really no different. The idea of profiling is to define a baseline of a known configuration. In most cases, the baseline is that of a secure configuration. Once you have a defined baseline, it can be compared with existing system configurations, reporting any differences. You can investigate the differences and take appropriate action to make your computers more secure.

Profiling also allows you to compare snapshots, or baselines, of your systems over time. Comparing two snapshots of the same computer taken at two different times helps you see configuration changes over time. While some changes may be normal, other configuration changes may indicate unauthorized changes to your environment.

Profiling Windows Computers

Microsoft provides a few tools that make profiling Windows easy. The **Security Configuration and Analysis (SCA)** tool helps administrators do several things. It allows you to analyze a computer and compare its configuration settings with a baseline. The SCA can also apply a baseline to force current computer settings to match the settings defined in the baseline. This feature is handy anytime you want to overwrite existing settings and revert to a known configuration. The SCA uses **security templates** to store the settings that make up baselines ([Figure 7-1](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig1)). A security template is a text file that contains a list of configuration settings.

**FIGURE 7-1** Security templates.

![image](OEBPS/Images/9781284031652_pg137.jpg)

**technical TIP**

To open the Security Templates snap-in in the MMC to manage Windows security templates:

**1.** Open the MMC. Choose the Windows Start button and enter mmc in the Run box.

**2.** From the MMC menu, select File, Add/Remove Snap-in.

**3.** Select Security Templates from the list of snap-ins on the left.

**4.** Choose Add, OK, to add the Security Templates snap-in.

**5.** Select the first path under Security Templates and open the context menu by right-clicking on the path.

**6.** Select New Template.

**7.** Enter a name and description for the new template and choose OK.

**8.** Expand sections of the new template and edit any desired settings.

Older versions of Windows included a collection of security templates. Windows Server 2008 R2, Windows Server 2012, Windows 7, and Windows 8 do not include an assortment of specific templates. Creating generic default security templates becomes more difficult as the number of configuration roles and options grow. A good way to create a baseline for profiling use is to create your own security template that corresponds to your organization’s security policy. The process of editing template settings is very similar to editing Group Policy Object (GPO) settings. Microsoft provides the Security Templates **snap-in** ([Figure 7-2](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig2)) to the **Microsoft Management Console (MMC)**, which helps you to create and manage security templates.

The SCA tool can be used to profile a Windows computer. The SCA tool allows you to analyze a computer using either a default template or a custom template you created using the Security Templates MMC snap-in. You can also use security templates you have acquired from some other source. You can conduct a security analysis, also called profiling a system, using either the SCA MMC snap-in or the SCA command-line tool. The security analysis compares the current system settings with the template loaded representing the baseline. Once a baseline template is created, use the SCA command-line tool to report any differences between the current computer settings and the baseline. Although the same information is available in the SCA MMC snap-in, the SCA command-line tool produces text output. This makes it easier to spot differences without having to navigate through multiple windows. You can even use SCA to change current settings to match the baseline template.

** ![image](OEBPS/Images/note.jpg)NOTE**

Windows Server operating systems, starting with Windows Server 2003 Service Pack 1, include another tool that is helpful in profiling a Windows server. The Security Configuration Wizard (SCW) analyzes a server and makes recommendations to improve its security. In Windows Server 2012, you can launch the SCW from the Server Manager dashboard.

**FIGURE 7-2** Security Configuration and Analysis MMC snap-in.

![image](OEBPS/Images/9781284031652_pg139.jpg)

**technical TIP**

The Security Configuration and Analysis snap-in in the MMC profiles a Windows computer. To add the Security Configuration and Analysis snap-in:

**1.** Open the MMC. Choose the Windows Start button and enter mmc in the Run box.

**2.** From the MMC menu, select File, Add/Remove Snap-in.

**3.** Select Security Configuration and Analysis from the list of snap-ins on the left.

**4.** Choose Add, OK, to add the Security Configuration and Analysis snap-in.

The SCA snap-in compares your current computer’s settings with the baseline in an SCA database. The next step is either to load the baseline template into a database or to open an existing database. Follow these steps to open a database:

**1.** Select Security Configuration and Analysis and right-click to open the context menu.

**2.** Select Open Database.

**3.** Enter the name of a new database or navigate to an existing database and choose Open.

**4.** Select the template you want to use for the profiling session and choose Open.

**5.** Right-click to open the context menu for Security Configuration and Analysis.

**6.** Select Analyze Computer Now.

**7.** Enter the fully qualified pathname for the analysis error log file and choose OK.

**8.** To view the results of the analysis, select the desired policy element. Expand a parent node to see the desired policy elements. The SCA snap-in displays each policy setting along with the baseline setting and the current computer setting ([Figure 7-3](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig3)).

**FIGURE 7-3** SCA snap-in analysis results.

![image](OEBPS/Images/9781284031652_pg140.jpg)

**technical TIP**

The Security Configuration and Analysis command-line tool can be used to profile a Windows computer. Follow these steps:

**1.** Open the command prompt window. Choose the Windows Start button and select Command Prompt.

**2.** Enter the following command to profile a Windows computer using the SCADB.sdb database, loading the OUSettings.inf and the SCALog.log file for the output log file:

Secedit /analyze /db SCADB.sdb /cfg OUSettings.inf /Log SCALog. log /verbose

**3.** If you have already loaded a template into a database, you can use this command instead to use an existing database:

Secedit /analyze /db SCADB.sdb /Log SCALog.log /verbose

**4.** Open the SCALog.log file to review the analysis results ([Figures 7-4](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig4) and [7-5](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig5)).

**FIGURE 7-4** Security Configuration and Analysis command-line tool.

![image](OEBPS/Images/9781284031652_pg141.jpg)

**FIGURE 7-5** SCA command-line tool analysis results.

![image](OEBPS/Images/9781284031652_pg141-1.jpg)

**technical TIP**

You can download MBSA 2.2 from this link: *[http://www.microsoft.com/en-us/download/details.aspx?id=7558](http://www.microsoft.com/en-us/download/details.aspx?id=7558)*. You can also go to Microsoft’s download site at *[http://www.microsoft.com/downloads](http://www.microsoft.com/downloads)* and search for “MBSA 2.2.” If you search for MBSA on the Microsoft downloads site, be sure the version supports your current versions of Windows.

Once you download MBSA, open the downloaded file and follow the directions to install MBSA on your computer.

**Microsoft Baseline Security Analyzer (MBSA)**

Microsoft provides a free tool that analyzes computers to identify insecure configurations. The **Microsoft Baseline Security Analyzer (MBSA)** is an easy-to-use tool. It evaluates the current security state of computers in accordance with Microsoft security recommendations. It not only identifies problems, but also ranks them by severity and provides recommendations to fix each one. According to Microsoft, many organizations use MBSA to scan over three million computers each week. It provides a convenient way to identify and address the most common security vulnerabilities.

The latest version of MBSA, version 2.2, supports Windows Server 2008 R2 and Windows 7, as well as several previous Windows versions. If your environment includes computers running previous versions of Windows, you can consult the MBSA release notes or download page to ensure that your version of MBSA supports all your Windows computers. Since MBSA does not install with Windows, you must download and install it yourself. It is well worth the small amount of time and effort to acquire and install this tool. You can get it from Microsoft’s Web site.

** ![image](OEBPS/Images/note.jpg)NOTE**

As of the publication of this book, Microsoft has not released a new version of MBSA that supports Windows Server 2012 or Windows 8. If you use one of these operating systems, use the SCW to obtain recommendations on ways to make your computers more secure.

MBSA GUI

You can run the MBSA using the graphical user interface (GUI) or command-line interface. The GUI provides an intuitive way to select the types of resources MBSA will analyze. The GUI is the most common interface to use when learning about MBSA. To run MBSA, launch the program, select the scan scope and options, and then start the scan. The scan report contains lots of information on what was found and what you should do about it. You choose to address or ignore each identified issue. It’s really that simple. The MBSA will scan your selected computers for just the types of vulnerabilities, that interest you. In addition to looking for specific security vulnerabilities, MBSA will alert you if operating system or application updates exist that you haven’t installed.

**technical TIP**

Follow these steps to use the MBSA GUI ([Figure 7-6](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig6)) to scan your computer for vulnerabilities:

**1.** Open MBSA. Choose the Windows Start button and then select Microsoft Baseline Security Analyzer 2.2.

**2.** Select the desired operation mode:

a. Select Scan a Computer to scan a single computer.

b. Select Scan Multiple Computers to scan more than one computer in a single session.

c. Select View Existing Security Scan Reports to view the results of previous scans.

**3.** If you chose to scan one or more computers, enter the computer or domain name or IP address(es).

a. For single computer scans, enter either a computer name or IP address.

b. For multiple computer scans, enter a domain name or a range of IP addresses.

**4.** Select the check boxes next to the desired scanning options ([Figure 7-7](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig7)). In many cases, leaving all options checked provides the most extensive analysis.

**5.** Choose Start Scan to begin the scanning process.

**6.** Whether you selected the scan option or selected an existing security scan report, MBSA presents the results ([Figure 7-8](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig8)) in a user-friendly report. Each report issue includes a description of what was scanned, details of the result, and in many cases, descriptive information on how to resolve the issue.

**7.** Choose OK to close the report viewer and return to the MBSA main window.

**FIGURE 7-6** MBSA GUI.

![image](OEBPS/Images/9781284031652_pg143.jpg)

**FIGURE 7-7** MBSA scan options.

![image](OEBPS/Images/9781284031652_pg144.jpg)

**FIGURE 7-8** MBSA scan results.

![image](OEBPS/Images/9781284031652_pg144-1.jpg)

MBSA Command-Line Interface

Microsoft also provides a command-line interface for MBSA ([Figure 7-9](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig9)). The mbsacli. exe command performs the same scan as the MBSA GUI ([Figure 7-10](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig10)) but with the added flexibility of starting the scan from the command line. Calling an MBSA scan from the command line gives you the ability to use batch files to scan computers for vulnerabilities. You can schedule batch files to run scans unattended at any time.

**technical TIP**

Follow these steps to use the MBSA GUI to scan your computer for vulnerabilities:

**1.** Open the command prompt window. Choose the Windows Start button and select Command Prompt.

**2.** Enter the following command to scan a single computer named “generic” for all vulnerabilities and store the results in a file named mbsaout.txt:

mbsacli /target generic >mbsaout.txt

**3.** Enter the following command to scan a single computer named “generic” only for missing updates and store the results in a file named mbsaout.txt:

mbsacli /target generic /n os+iis+sql+password >mbsaout.txt

This command uses the /n option to “Not scan” for “OS,” “IIS”, “SQL”, and “Password” vulnerabilities.

**4.** Enter the following command to scan a range of computers using IP addresses only for missing updates and store the results in a file named mbsaout.txt:

mbsacli /r 192.168.141.130-192.168.141.254 /n os+iis+sql+password >mbsaout.txt

This command uses the /n option to “Not scan” for “OS,” “IIS”, “SQL”, and “Password” vulnerabilities.

The results for each scan are reported in two locations. The mbsacli command produces text output and also creates a descriptive results report in the C:\\users\\username\\SecurityScans folder. This is the same folder that the MBSA GUI uses and the report is in the same format. You can use the MBSA GUI to view and analyze the output of the command-line MBSA just as if the output were generated from the GUI.

**FIGURE 7-9** MBSA command-line interface.

![image](OEBPS/Images/9781284031652_pg146.jpg)

**FIGURE 7-10** MBSA command-line interface scan results.

![image](OEBPS/Images/9781284031652_pg146-1.jpg)

| **TABLE 7-1** Common MBSA command-line interface (mbsacli.exe) options. |
| **OPTION** || **DESCRIPTION** |
| /target || Computer to scan. Target can be a domain or computer name or an IP address. |
| /d || Domain to scan. Use NetBIOS-compatible domain names instead of fully qualified domain names. For example, use “CorpDomain” instead of “[CorpDomain.com](http://CorpDomain.com).” |
| /r || Range of IP addresses of computers to scan. Beginning and ending IP addresses should be separated by a hyphen. For example, use “192.168.141.130-192.168.141.254.” |
| /listfile || Filename of a text file that contains computer names or IP addresses of computers to scan. Each computer name or IP address should be on a separate line. |
| /n || Scan options that MBSA should not perform. Excluded options may consist of:• OS—Windows administrative vulnerabilities• IIS—Internet Information Services administrative vulnerabilities• SQL—SQL Server administrative vulnerabilities• Updates—Missing security updates• Password—Check for weak passwordsYou can combine options with the “+” operator. For example, “/n os+iis+sql+password” would scan only for missing updates. MBSA excludes all options you supply. |
|   ||   |

The MBSA command-line interface supports the same functions as the GUI. In fact, there are advanced options that give you more flexibility than the GUI. [Table 7-1](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7tab1) shows the most common MBSA command-line interface options.

Microsoft SCA and MBSA aren’t the only profilers. Other vendors provide products that help you identify security vulnerabilities and keep your computers as secure as possible. You’ll learn about two vendors that provide products that extend and complement SCA and MBSA in the next sections.

**technical TIP**

Both NetChk Protect Limited and NetChk Protect scanners support legacy Microsoft products that MBSA no longer supports, such as Office 2000 and SQL Server 7. Go to *[http://technet.microsoft.com/en-us/security/cc184924.aspx](http://technet.microsoft.com/en-us/security/cc184924.aspx)* for a list of Microsoft products MBSA supports.

**Shavlik Security Analyzers**

Shavlik Technologies, LLC, provides a variety of products that extend and enhance MBSA’s functionality. Shavlik’s products work well with MBSA. They can produce output files MBSA can read and analyze. Their scanning products make it easy to run multiple scans using different products while still using MBSA to view and review scan results. This tight integration with MBSA isn’t really a surprise since Shavlik’s CEO, Mark Shavlik, wrote the original MBSA’s patch engine for Microsoft. Shavlik Technologies produces a range of security products from personal scanners to enterprise security assessment and management suites.

The Shavlik products **NetChk Protect** and NetChk Protect Limited analyze the patch status of products MBSA does not support. NetChk Protect also analyzes the patch status of products MBSA does support. In effect, the NetChk products pick up where MBSA stops. While MBSA focuses on current Microsoft products, including the Windows operating system, IIS, and SQL Server, the NetChk products include legacy Microsoft products, and in the case of NetChk Protect, include non-Microsoft products as well.

NetChk Protect Limited

NetChk Protect Limited is a limited version of the NetChk product line. NetChk Protect Limited is free for personal use but provides only a subset of the full NetChk product’s functionality. It does scan for more products than MBSA, but fewer than the full NetChk Protect product. Here is a list of limitations in the NetChk Protect Limited product:

• It scans fewer products than the full NetChk Protect scanner—NetChk Protect Limited scans for legacy Microsoft software MBSA does not support. For example, NetChk Protect Limited will scan for vulnerabilities in legacy products such as Office 2000 and SQL Server 7. You can visit *[http://www.shavlik.com/netchk-limited-supported-products.aspx](http://www.shavlik.com/netchk-limited-supported-products.aspx)* for a complete list of products NetChk Protect Limited supports.

• It does not enable you to deploy missing patches.

• It does not provide access to agent-based patch capabilities or the threat management capabilities of NetChk Protect.

In spite of NetChk Protect Limited’s limitations, it is a functional scanner—and it’s free. If you want more functionality in a scanner, you may want to look at the full-featured version of NetChk Protect.

NetChk Protect

The full version of NetChk Protect removes the limitations of the NetChk Protect Limited product. You have to pay a license fee to get the full functionality. The NetChk Protect scanner license includes a substantially longer list of supported products. The products in NetChk Protect’s supported applications list are among the most popular and commonly used software in today’s environments. They tend to be frequent targets for attackers and undergo updates and patches as vulnerabilities are identified and addressed. It is important to keep all software that users are running patched to the latest version to maintain a secure environment.

A partial list of products the NetChk Protect analyzes includes:

• Current Microsoft products included in MBSA scans

• Legacy Microsoft products included in NetChk Protect Limited scans

• Mozilla Firefox

• Adobe Acrobat

• Adobe Flash Player

• Sun JAVA

• Apple QuickTime

• RealNetworks

• RealPlayer

** ![image](OEBPS/Images/note.jpg)NOTE**

NetChk Protect helps fill in the gaps for products MBSA does not support. NetChk Protect supports both Windows 8 and Windows Server 2012 in addition to many legacy products.

In addition to including many more products in its analysis, the full NetChk Protect product adds many more capabilities, including:

• Automated patch management, which includes deploying missing patches

• Support of both agentless and agent-based operation to cover your entire environment with minimum administrative overhead

• Consolidated Patch Management with integrated antivirus and anti-spyware in a single Agent

• Support for migrating from physical systems to virtual machines

[Figure 7-11](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig11) shows the summary information from a single machine scan.

**technical TIP**

You can see a complete list of products the full NetChk product includes in its scans at *[http://xml.shavlik.com/data/supportedproducts.htm](http://xml.shavlik.com/data/supportedproducts.htm)*.

**FIGURE 7-11** NetChk Protect Limited scan summary.

![image](OEBPS/Images/9781284031652_pg150.jpg)

[Figure 7-12](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig12) shows the results from the last NetChk Protect Limited opened in MBSA.

**technical TIP**

You can visit *[http://www.shavlik.com](http://www.shavlik.com)* for complete Shavlik product descriptions, requirements, and costs.

**FIGURE 7-12** NetChk Protect Limited scan results viewed in MBSA.

![image](OEBPS/Images/9781284031652_pg151.jpg)

**Secunia Personal and Corporate Security Analyzers**

Secunia is a company that provides security scanner software products to extend MBSA’s functionality. Like the Shavlik products, Secunia products vary in functionality and overlap with MBSA. Secunia offers two scanner products targeted toward consumers and three products for corporate customers.

Secunia Personal Scanners

The two consumer products are **Online Software Inspector (OSI)** and **Personal Software Inspector (PSI)**. Both of these products are free for personal use. They scan computers for vulnerable and out-of-date software. The Secunia OSI ([Figure 7-13](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig13)) is a scanner that runs in a Web browser. It does not require that you install any software on the computer you are scanning. It doesn’t scan the number of programs or plug-ins that PSI does and it doesn’t support scheduled scans. It does provide a good vulnerability scanner for computers where you cannot or choose not to install scanning software.

** ![image](OEBPS/Images/note.jpg)NOTE**

Secunia scanners also help to fill in the gaps for products MBSA does not support. Secunia scanners support both Windows 8 and Windows Server 2012 in addition to many other products.

**technical TIP**

Go to *[http://secunia.com/vulnerability\_scanning/online/](http://secunia.com/vulnerability_scanning/online/)* to access Secunia’s Online Software Inspector. You can go to *[http://secunia.com/vulnerability\_scanning/online/programs\_covered/](http://secunia.com/vulnerability_scanning/online/programs_covered/)* to see which programs OSI covers during its scanning process.

**FIGURE 7-13** Secunia’s Online Software Inspector (OSI).

![image](OEBPS/Images/9781284031652_pg152.jpg)

The Secunia Personal Software Inspector is the main product for consumers. You must download and install this product on the computer you want to scan. PSI scans many more Microsoft programs and third-party programs and plug-ins to identify and report vulnerabilities. In fact, PSI covers all Microsoft software products and software from thousands of third-party providers. PSI provides a simple or advanced user interface that makes it easy to get up and running but gives you plenty of flexibility.

**technical TIP**

Go to *[http://secunia.com/vulnerability\_scanning/personal/](http://secunia.com/vulnerability_scanning/personal/)* to download Secunia’s Personal Software Inspector.

In addition to covering many more programs and plug-ins, PSI allows you to set up weekly scheduled scans. PSI also verifies vulnerabilities in all third-party programs and plug-ins and monitors your computers continuously to protect you from installing insecure programs. Both of the consumer products from Secunia are free and provide valuable protection from security vulnerabilities.

Figures 7-14 and 7-15 show the Secunia PSI Simple Interface and Advanced Interface.

**FIGURE 7-14** Secunia’s Personal Software Inspector (PSI) simple interface.

![image](OEBPS/Images/9781284031652_pg153.jpg)

**FIGURE 7-15** Secunia’s Personal Software Inspector (PSI) advanced interface.

![image](OEBPS/Images/9781284031652_pg154.jpg)

Secunia Corporate Products

Secunia offers three products for corporate customers. Each of the products requires a license fee and offers substantial functionality over the free consumer products. Secunia designed each product for specific corporate needs and organization types. Secunia corporate products support both centralized and decentralized management philosophies. Here’s a brief overview of Secunia’s corporate products:

• **Corporate Software Inspector (CSI)**—Authenticated vulnerability and patch scanner that identifies thousands of installed programs and missing security patches. CSI includes centralized management and reporting to support managing patches across networks of any size.

• **Enterprise Vulnerability Manager (EVM)**—Vulnerability alerting and management tool that enables effective decentralized management and handling of vulnerability intelligence.

• **Vulnerable Intelligence Feed (VIF)**—Enables centralized security teams to modify and distribute vulnerability intelligence provided by the Secunia Research team, using existing communication channels within an organization.

**technical TIP**

Visit *[http://www.secunia.com](http://www.secunia.com)* for complete Secunia product descriptions, requirements, and costs. See a side-by-side comparison of Secunia’s corporate products at *[http://secunia.com/products/corporate/compare/](http://secunia.com/products/corporate/compare/)*.

**Microsoft Windows Security Audit**

An *audit* is an evaluation of a collection of one or more objects. The objects can be people, things, processes, or organizations. An audit can be an evaluation of pretty much anything. The purpose of an audit is to determine if the objects of the audit meet some criteria. An audit is more than just collecting information about things. You must compare the collected information with some standards or guidelines and then determine if your collected information is similar to, or different from, the standard information. In most cases, an audit doesn’t focus only on a point in time. Most audits consider information gathered over a specific period. In this way, audits can reveal patterns of performance when compared with standards.

A security audit in a Windows computer environment is a collection of configuration and performance information compared with information contained in your security policy. The purpose of a Windows security audit is to measure how well the audited computer operation complies with your security policy. This process may seem similar to profiling a Windows computer. Although there are similarities, and profiling is often a part of a security audit, the two processes differ. Profiling is the process of comparing computer security settings with a baseline. Windows security auditing is a larger process of comparing computer security settings and performance with your security policy, typically over a period of time. As a general rule, the scope of an audit is larger than just profiling a collection of computers.

A Windows security audit involves several activities. These activities are related and may occur multiple times throughout an audit. Each audit may take different paths but the basic process ([Figure 7-16](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7fig16)) includes:

• Verifying that security controls comply with the security policy

• Collecting configuration and performance information

• Creating initial and subsequent baselines

• Recognizing and analyzing configuration or performance information changes

Collecting initial and subsequent baseline information involves more than just saving analysis reports. You will likely include various audit log files to track access to sensitive resources. Most log file entries of interest will likely be data access for sensitive data and execute events for administrative programs that can cause damage if used improperly. Log files can provide a wealth of performance information. They can help isolate problems and identify behaviors that both support and violate security policy.

**FIGURE 7-16** Windows security audit activities.

![image](OEBPS/Images/9781284031652_pg156.jpg)

Carefully consider what items you want to audit. Auditing too many events for too many objects can cause your computers to run more slowly and consume more disk space to store the audit log file entries. Consider logging only access failures for most objects you choose to audit. You can audit both access successes and failures for resources that are critical to your organization, but don’t track audit information for all resources.

The key to conducting an effective audit is to establish a consistent process. Define the information you’ll need for the analysis phase and then ensure that you are collecting and storing the necessary information. Planning audit activities improves the likelihood that you’ll capture all the information you need. Auditing should not be viewed as activities that attempt to uncover problems. It should be a continuous process of improving the security standing of your computing environment.

**Microsoft Windows Security Audit Tools**

A Windows security audit involves identifying, collecting, and analyzing information. You’ll need a plan and some tools to make the task manageable. You should plan ahead for any audit information needs and start the collection process as soon as possible. Your goal is to use the tools at your disposal to collect every bit of information that an auditor can use to verify compliance or research unusual activity.

Collecting every bit of information that may be needed is impossible without collecting lots of unneeded information. The goal should be to collect as much information as possible that is likely to be useful for auditing. [Table 7-2](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7tab2) lists some Windows auditing-related tools you can use and the information they help you retain.

| **TABLE 7-2** Windows auditing tools. |
| **TOOL** || **DESCRIPTION** |
| Security and Configuration Analysis (SCA) snap-in || GUI snap-in to the MMC that compares a computer’s settings with a predefined template. The SCA is useful to quickly identify any differences from standard settings. |
| Secedit.exe || Command-line version of SCA. Secedit performs the same basic functions of SCA but produces a text file as output. The command-line format allows you to use secedit in batch files for automatically scheduled audits. |
| Microsoft Baseline Security Analyzer (MBSA) || GUI auditing tool that checks one or more computers for missing patches, weak passwords, and other common security vulnerabilities. |
| Mbsacli.exe || Command-line interface for MBSA. Mbsacli makes it easy to run MBSA on a schedule and store output text files for later analysis. |
| Microsoft Security Assessment Tool (MSAT) || Tool to measure current system security and provide recommendations to mitigate vulnerabilities. MSAT supports Windows versions through Windows 7 and Windows Server 2008. |
| Microsoft Security Compliances Manager (SCM) || Tool to help configure and manage multiple Windows computers using Group Policy and System Center Configuration Manager. SCM includes baselines for most Windows versions, including Windows 8 and Windows Server 2012. |
| DumpSec || The SomarSoft utility that dumps permissions and audit settings for the file system, Registry, and printers, and shares the information to a text file; a command-line utility to use in batch files to schedule audit tasks. |
| DumpEvt || The SomarSoft utility that dumps the Windows event logs to text files. DumpReg is a command-line utility you can use in batch files to schedule audit tasks. |
| DumpReg || The SomarSoft utility that dumps part or all of the Windows Registry to text files. DumpReg is a command-line utility you can use in batch files to schedule audit tasks. |
|   ||   |

**technical TIP**

You can download the SomarSoft utilities from *[http://www.systemtools.com/somarsoft/?somarsoft.com](http://www.systemtools.com/somarsoft/?somarsoft.com)*.

You can download MSAT from *[http://www.microsoft.com/en-us/download/details.aspx?id=12273](http://www.microsoft.com/en-us/download/details.aspx?id=12273).*

You can download the Microsoft SCM from *[http://www.microsoft.com/en-us/download/details.aspx?id=16776](http://www.microsoft.com/en-us/download/details.aspx?id=16776)*.

The tools listed in [Table 7-2](#17_Chaper7_split_001.xhtml#ba-9781284031652-ch7tab2) are a great starting point for collecting audit information. Develop a naming convention and storage location for the tools’ output. A good naming convention includes information such as the computer name, date, time, and type of information in the file. Here is a suggested audit file-naming convention:

Computer\_name.file\_contents.yyyymmddhhmmss.txt

Example: SCILaptop.sec\_evt\_log.20100401113533.txt

• **Computer\_name**—Name of the computer

• **File\_contents**—Abbreviated identifier that represents the contents of the file, such as sec\_evt\_log or ‘registry’

• **Date and time**—Creation date and time of the file

• **yyyy**—Four-digit year

• **mm**—Two-digit month

• **dd**—Two-digit day of the month

• **hh**—Two-digit hour in 24-hour format

• **mm**—Two-digit minute

• **ss**—Two-digit second

Use the Windows auditing tools at your disposal to create periodic baselines and store event log files. You should decide what frequency works best for your organization. Monthly or quarterly baselines generally provide a good starting point for auditors. Consider creating baselines more frequently in environments that regularly change. The baselines show a snapshot of your computers at a point in time and the event logs show how settings changed from one baseline to another. Taken together, baselines and event log files can provide the information to better understand your Windows environment and make it compliant with your security policy.

**Best Practices for Microsoft Windows Security Audits**

A solid Windows security audit strategy is one that collects just enough information to satisfy audit needs and no more. Collecting too much information slows down your computers and wastes disk space. It also makes the auditing task harder with excessive information to review. You want to continually refine the audit information collection process to add collectors for information you need and remove collectors for information that is irrelevant.

Here is a list of Windows security audit best practices that will help you design, develop, and maintain an audit process that is efficient and effective. Modify these guidelines to suit your organization but pay attention to the suggestions—they can help you avoid wasting time and resources.

• Create initial baselines that represent a “secure” starting point for each computer. Develop security templates in SCA that contain the security settings for each type of workstation and server. Change the templates as needed and use them when building new computers. You can apply up-to-date templates to new Windows installations to quickly configure a new computer to your security standards.

• Run SCA/MBSA using command-line interface options to compare computer settings and configurations with your standards. Schedule scans to run periodically, such as weekly or monthly, and review the resulting output files for any identified problems.

• Develop batch files to run scans and collect ongoing operational information. Collect information using a set daily, weekly, or monthly schedule and archive collected data files.

• Maintain current backups of all audit information so you can recover historical audit information in the case of a disaster.

• Enable Windows auditing only for sensitive or critical resources.

• Do not enable Read or List auditing on any object unless you really need the information. Read/List access auditing can create a tremendous amount of auditing information.

• Do not enable Execute auditing on binary files except for administrative utilities that could be used in an attack.

• Limit enabling all auditing actions to files, folders, programs, and other resources that are important to your business functions. Don’t be afraid to enable auditing for any object—just ensure you need the information you’ll be saving.

• Enable auditing for all change actions for your Windows install folder and any folders you use in normal business operation. It is also a good idea to audit changes to the Program Files folder.

• Audit all printer actions. You may need to be able to know who printed a document that found its way into the wrong hands.

• Ignore Read and Write actions for temporary folders but do audit Change Permissions, Write Attributes, and Write Extended Attributes actions. These actions can help identify attacker activities.

• Develop Windows policies and Group Policy Objects that are as simple as possible and still satisfy your security policy. Complex policies are difficult to verify.

• Develop clear guidelines to evaluate each element of your security policy. An audit should be a structured process to verify your security policy, not an unorganized hunt for problems. Know what you will be looking for before you search through lots of audit data.

These best practices guidelines are only a starting point, but they give you guidance on how to develop an auditing strategy that will work for your organization.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Auditing is the process of validating that an environment complies with its design. Basically, auditing helps ensure that your computers are doing what they are supposed to be doing and nothing more. Although the process sounds simple, it takes substantial thought and planning to get to the point of successfully performing an audit. You must clearly define the standards and guidelines for your environment. Then, you must collect and retain the information that provides evidence your environment is operating as designed. Finally, you must develop and execute the procedures that analyze the collected information to decide whether your environment complies with your security policy.

Auditing includes planning to collect information and using tools to collect and organize information for audit analysis. In this chapter, you learned about the planning, the process, and the tools. All that is left is to put it all into practice.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Baseline**

**Microsoft Baseline Security Analyzer (MBSA)**

**Microsoft Management Console (MMC)**

**NetChk Protect**

**Online Software Inspector (OSI)**

**Personal Software Inspector (PSI)**

**Profiling**

**Security Configuration and Analysis (SCA)**

**Security template**

**Snap-in**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 7 ASSESSMENT**

  **1.** A baseline is the initial settings in a newly installed system.

A. True

B. False

  **2.** A baseline, also called a \_\_\_\_\_\_\_\_, is a collection of settings at a specific point in time.

  **3.** Which Microsoft tool analyzes a computer’s settings and compares its configuration with a baseline?

A. SCA

B. MBSA

C. NetChk

D. OSI

  **4.** Stored settings that make up a baseline are stored in which type of files?

A. Baseline configuration

B. Baseline database

C. Security template

D. Security object

  **5.** The Security Configuration and Analysis tool operates as a snap-in to the \_\_\_\_\_\_\_\_.

  **6.** Which command-line tool provides the same scanning capability as SCA?

A. Secedit

B. Mbsacli

C. Scacli

D. Mbsaedit

  **7.** Which of the following products does MBSA *not* analyze?

A. IIS

B. SQL Server

C. Adobe Acrobat

D. Windows 7

  **8.** MBSA automatically ranks vulnerabilities by severity.

A. True

B. False

  **9.** Which command-line tool provides the same scanning capability as MBSA?

A. Secedit

B. Mbsacli

C. Scacli

D. Mbsaedit

**10.** Which security scanner looks for weak passwords?

A. SCA

B. OSI

C. NetChk Protect

D. MBSA

**11.** What does NetChk Protect Limited do that MBSA does not do?

A. Scans the latest Microsoft products

B. Scans legacy Microsoft products

C. Scans all Microsoft products

D. Scans selected Microsoft products

**12.** Which security scanner runs in a Web browser and doesn’t require that you install a product before scanning?

A. NetChk Protect Limited

B. MBSA

C. OSI

D. PSI

**13.** Which of the following statements best describe the relationship between profiling and auditing?

A. Auditing is often a part of profiling.

B. Profiling is often a part of auditing.

C. Profiling and auditing are interchangeable terms.

D. If auditing is in place, profiling is not necessary.

**14.** When designing an audit strategy, you should log access attempts on the \_\_\_\_\_\_\_\_ number of objects.

**15.** What is the main purpose of an audit?

A. To uncover problems

B. To catch errors

C. To validate compliance

D. To standardize configurations

**CHAPTER 8**

**Microsoft Windows Backup and Recovery Tools**

AVAILABILITY IS ONE OF THE PROPERTIES, or pillars, of the C-I-A triad of information systems security, along with confidentiality and integrity. Secure information must be available to authorized users when they request it. Ensuring information availability requires planning and preparation to confront issues that threaten to make your information unavailable. Issues include attacks to deny service, degraded performance, and failures or disasters that limit or terminate access to your information. A solid security plan includes both components to avoid situations that threaten information availability and procedures to deal with problems if they do occur.

In this chapter, you’ll learn about the basics of creating backup images and using them to restore your information. You’ll learn about different scenarios that can result in loss of information and how to recover from different types of loss. Although most people consider the backup the most important component of a recovery plan, you’ll learn how important other components really are. When you finish this chapter, you will be better prepared to protect your Windows computers from information loss.

**Chapter 8 Topics**

This chapter covers the following topics and concepts:

• What Microsoft Windows operating system (OS) and application backup and recovery are

• What workstation, server, network, and Internet backup techniques are

• What Microsoft Windows and application backup and recovery is in the context of business continuity and disaster recovery planning

• What the Microsoft Windows Backup and Restore utility is

• What rebuilding systems from bare metal is

• How organizations manage backups with virtual machines

• What best practices for Microsoft Windows backup and recovery are

**Chapter 8 Goals**

When you complete this chapter, you will be able to:

• Describe Microsoft Windows operating system and application backup and recovery techniques

• Compare different options for creating backups

• Incorporate backups and restore operations into a business continuity plan

• Use virtual images to create backups

**Microsoft Windows Operating System (OS) and Application Backup and Recovery**

Most of your efforts to secure information will focus on the **primary copy** of your information. The primary copy of any piece of information is the copy you use most frequently. You’ll spend time and effort ensuring your organization’s information is accessible only by authorized users. You’ll carefully control what users can do with and to your information. But what happens if the primary copy of any data gets damaged or destroyed? What if a fire, flood, or other disaster destroys the computer where information resides? Or what if a worm deletes many of your important documents? How do you recover if existing controls do not protect your data?

The Need for Backups

The answer to all of these issues is to have access to a current **secondary copy** of the information you lost. While that solution may sound simple, it takes some thought and planning to provide a usable alternative. A valid **backup** is a crucial part of an organization’s ability to recover from losing data. A backup is a defined collection of copies of files you create in case the primary copies of the files are damaged or destroyed. There are many ways you can lose data. Not all situations that result in losing data are major disasters. You have already seen a few situations that may cause you to lose data. [Figure 8-1](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig1) shows some of the reasons you may lose data:

• **Hardware errors**—Hard disks or disk controllers can fail. Hardware failures may occur slowly, introducing errors into your data files over time. Equipment can also be lost or stolen. Hundreds of thousands of laptops are left in airports and taxicabs each year.

• **Software errors**—Software bugs and poorly written software can cause you to lose data you thought was safe.

• **Malicious software**—Many types of malware damage or delete files to alter or destroy data.

• **User actions**—Users can take actions that damage or destroy data. Users can misuse application software or operating system utilities to cause data loss. Data loss because of user actions can be either intentional or accidental. Each type of motivation requires a different type of control.

• **Attacks**—Successful attacks on your information systems can cause substantial data loss. Many of the controls you implement keep attackers from successfully harming your information’s security.

• **Environmental issues**—Many issues with the computing environment can cause computers to fail and possibly damage data. Air-conditioning system failures can cause computers to overheat and possibly result in hardware damage. Fire suppressants and sprinkler systems can damage computers as well. Power spikes and fluctuations can also cause hardware damage that could result in losing data.

• **Natural disasters**—This is the category most people consider first when discussing reasons for backups. Disasters such as fires, floods, tornadoes, and earthquakes can cause substantial damage and result in data loss. Any large-scale disaster has the potential to damage your data.

**FIGURE 8-1** Reasons for data loss.

![image](OEBPS/Images/9781284031652_pg164.jpg)

Anytime you lose the primary copy of your data, you have two choices:

**1.** Reconstruct the data.

**2.** Recover the data from a secondary source.

In most cases, reconstructing data is the last resort. Duplicating the work effort required to reconstruct data is often counterproductive, wasteful, and expensive. It is generally faster and easier to recover lost data from a secondary copy, or a backup. You must have created a secondary copy of your data prior to the loss for this option to be viable. A scheduled backup is the most common method to create secondary copies of important data to use in the case of primary data loss. A backup doesn’t guarantee that you’ll be able to recover all the data you’ve lost, but it does make recovery a real possibility.

![image](OEBPS/Images/war.jpg)**WARNING**

You should consider only verified backups to be useful. The safest practice is to assume unverified backups are always bad.

The Backup Process

The process to create a backup is fairly simple. You copy the files you want to duplicate to a target location. Creating an effective backup plan that enables the most recovery options, however, is not so simple and takes time to design. The backup planning process starts with a series of questions to decide how to conduct the actual backup. Common questions include:

• Which files or folders will you back up?

• Will you use a static list of files or dynamically identify the items for backup?

• Where will the backed-up files be copied?

• Will you use removable media?

• Does the backup require human intervention?

• How will you label and identify backup media?

• What controls will you use to protect the C-I-A properties of the backup media?

• How frequently will you create a backup?

**Backup Media Security**

Secure the removable media that you use for backups. Attackers know that one of the easiest ways to bypass access controls in the operating system is to acquire a backup tape or disk. If the information on your backup media is not protected, it can provide easy access for attackers. Backups will be targets and should be protected from falling into the wrong hands. Use aggressive physical security controls and even encryption to protect your backup media.

• Will you back up all your data each time, or just what changed since the last backup?

• How many generations of backups will you keep?

• How will you use the backup to recover lost data?

These are just a few of the questions you’ll have to answer when deciding how to create a backup. There’s a lot more to creating effective backups than just copying files. Once you identify the files and folders you want to back up, you can open a backup utility to create the actual copies.

The Restore Process

The real reason for creating any backup is to have the option of restoring if you lose any primary data. A **restore operation** is the process of copying secondary copies of files back to their primary locations. The most common reason to restore files is to replace damaged or missing data.

The restore process involves deciding whether to copy all files and folders from the backup media back to their original locations or only some files and folders. First, identify the files and folders you want to restore. Then, open a restore utility that is compatible with the backup image you created and start the process. There are several important considerations when you choose to restore data from a backup. Answer these three questions to ensure you understand the impact of restoring data to a previous state:

**1.** How long will it take to restore the selected data?

**2.** What data will I lose in the restore process?

**3.** Will I be able to use the data I restore?

All three questions may seem minor, but they have a large impact on how effective your backup policy will be. The first question is one that many IT personnel and users fail to appreciate. Many organizations choose to create complete backup images anytime they create backups. You can be sure you don’t miss any files or folders when you back up everything.

**Restore Uses**

There are other uses for the restore process other than repairing damage. Sometimes it is beneficial to restore a system, or parts of a system, to a previously known state. For example, many organizations that use computers for training use the restore process to reset computers after classes. The ability to restore a computer to a state before students made any changes allows the organization to undo changes students made during a class. You can also use the restore process to undo changes, such as a new software installation, that cause your computer to stop functioning properly.

**technical TIP**

Include estimates of the effort you’ll expend to reconstruct data in your restoration plan. After looking at the cost of reconstructing a half day’s worth of data, you may find that taking more frequent backups saves time and money.

The problem with complete backups is that they tend to take longer than backing up only selected files and folders, and they will certainly take longer to restore. Taking longer to create a backup can have other effects as well. If your backups take a long time to complete and it slows down your system to create the backup, you may choose to back up less frequently. That means more time passes, and you make more changes, between backups. The other part of this concern is how long it takes to restore lost data. You must define a target goal for how long it should take to recover from an interruption. Otherwise, it may be difficult to decide on the best recovery option.

Most organizations set a **recovery time objective (RTO)** for critical resources. The RTO is the amount of time it should take to recover a resource and bring it back to normal operation. Assume the RTO for a specific server is three hours. If a full restore takes four hours but you can reenter and verify the lost data in two hours, a restore is not the most efficient choice.

The answer to the second question can often lead to many more questions. A backup is a snapshot of a collection of files at the time you created the backup. As long as you make no changes after you create the backup, you can recover all of your data. However, if you make any changes to data files after you create the backup, you risk losing those changes.

The most common reason to restore files is to recover from damaged or lost data. If you restore one or more files from backup media, you will lose any changes made to those files since creating the backup. Waiting longer between backups means you can potentially lose more data if you have to restore files. Carefully consider how you will reconstruct data created or changed since your last backup if you lose primary copies of your data. The common perception that simply restoring the most recent backup will fix everything is not accurate.

The last question addresses data that tends to change very frequently. Most organizations use database management systems to manage large amounts of data. Database files are likely updated frequently and may change during the backup process. Other large files may change while copying during a backup. When a file changes as it is being copied, it may lose its integrity. Most database vendors provide specialized backup utilities for database files to ensure the data maintains its integrity. Get to know your applications and any special requirements for including large files in backup operations. You don’t want to find out your backed-up files aren’t usable.

The choice of restore utilities depends on which utility you used to create the backup image. Utilities must be compatible with backups. Beyond basic compatibility, the process depends on the specific options your backup and restore utility provides. In many cases, the restore utility copies everything from the backup media to a location on your hard disk. When you complete a well-planned restore operation, you’ll have to take few additional steps to get running again.

**Volume Shadow Copy Service**

Microsoft backup utilities make it easy to maintain integrity during backups for applications that support the **Volume Shadow Copy Service (VSS)**. VSS supports utilities and applications in creating snapshots of a running Windows system. Microsoft Backup utility uses VSS to alert applications like Structured Query Language (SQL) Server and Exchange. This allows the backup to take a snapshot of the system. VSS-aware applications stop writing to data files until the snapshot completes. The applications can continue writing, but will work with the backup process to ensure blocks that are about to be written are backed up first. In this way, Windows ensures data integrity.

**Workstation, Server, Network, and Internet Backup Techniques**

Workstation Backups

Workstations store and process some information locally. It is important to ensure all your workstations back up important files. Some organizations overlook workstation backups. This results in data loss when problems arise. Often, locally stored data is an integral piece of organizational data. For example, software developers often copy programs to their local workstations to make changes. It is not unusual for developers to have several dozen programs on their local workstations. When they finish making program changes and testing the changes, they copy their work back to a central repository. What happens if a software developer encounters a problem that results in losing one or more local programs? He or she will lose all the work invested in program changes unless frequent backups for Workstation Domain computers keep current secondary copies of work in progress.

Even if members of your organization do not copy files from a central source to edit locally, backups will protect your workstations from loss. Nearly every workstation user stores local documents, spreadsheets, presentations, custom settings, and other data that would take time to reconstruct. At the very least, backing up workstations will save time if a user loses data.

Microsoft includes an updated Backup and Restore utility with Windows 7. It has been upgraded from its Vista predecessor to make backing up and restoring workstations simpler. The Windows Backup and Restore Wizard asks you to provide answers to three main questions to configure your backup scope and schedule. [Figure 8-2](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig2) shows the Windows Backup and Restore utility in action.

**FIGURE 8-2** Windows Backup and Restore utility.

![image](OEBPS/Images/9781284031652_pg169.jpg)

**technical TIP**

Open the Windows Backup and Restore utility on a computer running Windows 7 using these steps:

**1.** Choose the Windows Start button > Control Panel.

**2.** Select System and Security > Backup and Restore.

Provide three types of information to describe your backup process. Follow the Backup and Restore Wizard prompts to enter:

• **What to back up**—Let Windows select the most important files and folders to back up or select which files and folders to include.

• If Windows selects the files to back up, it will choose data files that are saved in libraries, on the desktop, and in default Windows folders for all user accounts on the computer.

• If the drive you are saving the backup on is formatted using the NT file system (NTFS) and has enough disk space, Backup and Restore will also include a system image of programs, windows, and all drivers and Registry settings in the backup.

• **Where Windows will store the backup**—Select a local hard disk or a CD/DVD writer if the computer has the hardware to write CD/DVD disks.

• If the computer runs Windows 7 Professional or Windows 7 Ultimate edition, you can also back up files to a network resource.

• **When to back up**—Select the frequency and time Windows will start the backup. [Figure 8-3](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig3) shows the options Windows provides to schedule a backup.

That’s it—Windows does the rest. Once the Windows Backup and Restore utility is set up, it creates a backup according to the defined schedule. Of course, you have to ensure that your computer is turned on when your scheduled backup should run. If your computer is turned off, the backup will run at the next scheduled time. You can also back up your selected files at any time by choosing the Back Up Now button and change any settings by selecting the Change Settings link.

**FIGURE 8-3** Windows Backup and Restore.

![image](OEBPS/Images/9781284031652_pg170.jpg)

**Workstation Backups from the Command Line**

You can also create Windows backups from the command line. The wbadmin command provides a way to create Windows backups without using the graphical user interface (GUI). You can find the complete syntax of the wbadmin at *[http://technet.microsoft.com/en-us/library/cc754015(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc754015\(WS.10\).aspx)*.

Here is a sample command you can use to create a backup of drive C: and store on drive I:

WBADMIN START BACKUP -backupTarget:I: -include:C: -allCritical -vssFull -quiet

| **TABLE 8-1** Commercial products for Windows Backup and Restore. |
| **PRODUCT** || **WEB SITE** |
| Acronis Backup & Recovery || *[http://www.acronis.com](http://www.acronis.com)* |
| EaseUS To-Do Backup || *[http://www.todo-backup.com/](http://www.todo-backup.com/)* |
| Macrium Reflect || *[http://www.macrium.com/](http://www.macrium.com/)* |
| NovaBACKUP || *[http://www.novastor.com/en/software/windows-backup](http://www.novastor.com/en/software/windows-backup)* |
| Fbackup || *[http://www.fbackup.com/](http://www.fbackup.com/)* |
| AlmerBackup || *[http://www.almersoft.com/products/backup/](http://www.almersoft.com/products/backup/)* |
| Syncovery || *[http://www.syncovery.com/](http://www.syncovery.com/)* |
|   ||   |

Other Workstation Backup Utilities

Microsoft doesn’t provide the only software for backing up and restoring Windows workstations. There are many alternatives. If you want to explore other products that provide more control over how you create and manage backups, look at what other vendors offer. [Table 8-1](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8tab1) lists a few of the more popular Windows backup programs. Compare the features of the various products and select the one that fits your requirements best.

Server Backups

Although it’s likely that your organization’s data is stored and processed on workstations, the majority of data probably resides on servers. Server computers provide many services within an organization, including storing large volumes of data. Most organizations store at least some data on server computers. Servers exist to provide services to an organization’s users. These services are almost exclusively data-related or data-dependent services. To put things into perspective, [Table 8-2](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8tab2) lists just a few common types of servers and the type of data they store and process.

There are many more types of servers that store many different types of data. You can begin to see how many organizations depend on servers and server data. The loss of one server can cause a significant interruption to normal operation. For example, consider the impact of losing an e-mail server. How much of a problem would it be if an organization lost all of its e-mail messages? A good backup and restore strategy becomes increasingly important when considering the impact of losing even a little data. It is crucial to back up each server frequently and manage the backup images efficiently. Make sure your plan includes methods to easily and quickly retrieve the backup images on demand.

| **TABLE 8-2** Types of Windows servers. |
| **SERVER** || **TYPE OF DATA** |
| Active Directory Domain Services server || Active Directory configuration data for users, groups, and resources in one or more domains |
| Web server || Configuration and files to support Web sites and applications |
| Database server || Database management system configuration data and all managed data in your databases |
| Application server || Programs and configuration data to support distributed applications |
| Audio/Video server || Audio and video configuration and data to support streaming applications and bulk media storage |
| Mail server || Server and mailbox data for mail-related functions |
| File server || Any files and folders stored on central servers |
|   ||   |

**Compensating Controls for Backups**

In many cases you will identify multiple controls that meet a specific goal. A frequent backup schedule is the primary control to protect any organization from data loss. There are other methods to avoid losing data due to errors of failure. These “other” controls are often called **compensating controls**. Compensating controls fulfill the original goal without implementing the primary control. The alternate control compensates for the absence of the primary control.

Many hardware manufacturers provide hardware-based solutions to protect computers from certain types of data loss. For example, a **redundant array of independent disks (RAID)** system protects computers from disk failure–related data loss. RAID systems store extra data and can reconstruct damaged data if a disk fails. While RAID systems can protect systems from more common types of hardware failure, they can’t protect organizations from other types of failures, such as fires or floods. In fact, RAID systems themselves are not immune to failure. You still need a good backup strategy.

**technical TIP**

Install the Windows Server Backup utility on a computer running Windows Server 2008 by following these steps:

**1.** Choose the Windows Start button > Administrative Tools > Server Manager.

**2.** Select Features in the left pane, then select Add Features in the right pane.

**3.** Scroll down and expand Windows Server Backup Features.

**4.** Check the boxes next to Windows Server Backup and Command Line Tools.

a. Note: Check only Command Line Tools if you want to install the backup command-line tools as well as the Microsoft Management Console (MMC) snap-in.

**5.** Choose Next, then Install.

**6.** After the Windows Server Backup installs, close the Server Manager.

Microsoft provides a utility for backing up Windows servers. All Windows Server 2008 versions, except for the Core Server installation, include the Windows Server Backup utility. Before the backup utility can be used, it has to be installed on each server that you want to back up. Once the utility is installed, it can be configured to create flexible backups according your organization’s needs.

Once you have installed the Windows Server Backup utility, you can schedule and create backups for your servers. Since Windows servers perform different functions, they often have different backup needs. The Microsoft Windows Server Backup utility addresses many different server backup needs and takes more effort to configure than a simple workstation backup ([Figure 8-4](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig4)). The basic steps are similar to setting up a workstation backup—but more options are available.

**technical TIP**

Open the Windows Server Backup utility on a computer running Windows Server 2008 using these steps:

**1.** Choose the Windows Start button > Administrative Tools > Windows Server Backup.

**2.** Select the Backup Schedule link to launch the Backup Schedule Wizard to configure a scheduled backup.

a. Select the Backup Once link to launch the Backup Once Wizard to configure a one-time backup.

**FIGURE 8-4** Windows Server Backup.

![image](OEBPS/Images/9781284031652_pg174.jpg)

You provide three types of information to describe your backup process. Follow the Backup Wizard prompts to enter:

**• What to back up**—Back up an entire server or select which files and folders to include. Microsoft recommends backing up entire servers in most cases.

**• When to back up**—Select the frequency and time Windows will begin the backup process.

**• Where Windows will store the backup**—Select a disk dedicated for backup images, a volume with other files on it, or a shared network folder.

**Server Backups from the Command Line**

You can also create Windows server backups from the command line. The wbadmin command is the same you saw from the previous section on workstation backups. You can find the complete syntax of the “wbadmin” at *[http://technet.microsoft.com/en-us/library/cc754015(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc754015\(WS.10\).aspx)*.

**technical TIP**

You can find detailed instructions for creating and managing Windows Server backups at *[http://technet.microsoft.com/en-us/library/cc753528.aspx](http://technet.microsoft.com/en-us/library/cc753528.aspx)*.

Once you set up your server backups, Windows handles copying the files and folders you identified to another disk. If you want to copy your backups to removable tape drives, you will have to do that manually. The Windows Server Backup does not support backing up directly to tape drives. You will have to create a scheduled job to copy the backup files from the Server Backup destination to your tape drive.

Other Server Backup Utilities

Microsoft doesn’t provide the only software for backing up and restoring Windows servers. As with workstation backups, there are many alternatives for server backup utilities. If you want to explore other products that provide more control over how you create and manage backups, look at what other vendors offer. [Table 8-3](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8tab3) lists a few of the more popular Windows server backup programs. Compare the features of the various products and select the one that fits your requirements best.

Network Backups

Most backup utilities provide the ability to back up files and folders to a network shared folder. This approach has both advantages and disadvantages. Be sure to evaluate the impact to your system before selecting network destinations for any new backup operations. Adding new backups to network destinations without assessing the impact can degrade your network performance. It can even make your network unusable. Remember that you are establishing backups as controls to support the availability principle, not violate it.

| **TABLE 8-3** Commercial Windows server backup software. |
| **PRODUCT** || **WEB SITE** |
| NovaBACKUP || *[http://www.novastor.com/en/software/windows-backup](http://www.novastor.com/en/software/windows-backup)* |
| Acronis Backup & Recovery || *[http://www.acronis.com](http://www.acronis.com)* |
| Genie Timeline Server 2013 || *[http://www.genie9.com/](http://www.genie9.com/)* |
| EaseUS To-Do Backup || *[http://www.todo-backup.com/](http://www.todo-backup.com/)* |
| BackupAssist || *[http://www.backupassist.com](http://www.backupassist.com)* |
| Total Backup Recovery || *[http://www.farstone.com/](http://www.farstone.com/)* |
| Continuous Data Protection || *[http://r1soft.idera.com/](http://r1soft.idera.com/)* |
|   ||   |

Backing up files and folders to network destinations provides two main benefits:

**1.** Files and folders are copied to another computer or device. Copying data to another computer or device protects the backed-up data from damage to the primary computer or storage device. In the past, network backups implied that the backup location was physically separate from the source. In today’s environments where virtual machines and cloud computing resources are more common, don’t assume backing up to a network destination ensures physical separation. The networked destination may be another virtual device on the same physical server.

**2.** Local disk space is not used to create backups. The backup process consumes disk space on the destination device and makes it easier to separate disk usage impact from live servers.

![image](OEBPS/Images/war.jpg)**WARNING**

Virtual images make backing up data easy. Both your primary copy and secondary copies may reside on the same physical server. But this can actually reduce your data’s security. A catastrophic failure could cause you to lose both copies. If your backup image is not physically located on a separate server, you should plan to archive the backup image on removable media or another server.

On the other hand, backing up files and folders to network destinations has drawbacks:

**1.** Backups consume network resources. Backups across a network, just like all network applications, send messages to the remote destination. Backups send a lot of messages across your network. If the network segment between the backup source and backup destination is used, you will experience slower service during the backup. If you do not have sufficient bandwidth to handle the extra traffic, your network services may experience extreme slowdowns, timeouts, and may even crash.

**2.** Backups across networks will be slower than backups using local disks. The degree to which network backups run more slowly depends on available network bandwidth. Available network bandwidth depends on the speed of your network and what other applications are using your network. It is a good idea to use only backups to network folders connected using fast network segments.

**3.** Backups to networked shared folders may timeout and fail more frequently than local resources. Closely monitor your backup status to detect failed backups. Remember that a failed backup means your data is not protected from loss.

Networked shared folders can provide convenient destinations for both workstation and server backups. Before setting up networked backups, ensure your network can handle them. Monitor network activity to detect any bandwidth problems before they become critical. As you modify scheduled backups, try to stagger backups to avoid saturating your network with multiple backups running simultaneously.

Internet Backups

Backing up data across the Internet is another backup option that is gaining popularity in some environments. Data backed up to an Internet destination is physically separate from your local computer. It provides a high level of protection from any damage to local data. By far, the biggest restriction for Internet backups is the lack of bandwidth. Even the fastest Internet connection has limited available bandwidth. The Internet’s architecture virtually guarantees there will be several segments between your computer and any destination, and many other users are sharing the bandwidth with you.

| **TABLE 8-4** Internet backup software. |
| **PRODUCT** || **WEB SITE** |
| CrashPlan || *[http://www.crashplan.com/](http://www.crashplan.com/)* |
| Carbonite || *[http://www.carbonite.com/](http://www.carbonite.com/)* |
| Backblaze || *[http://www.backblaze.com/](http://www.backblaze.com/)* |
| IDrive || *[https://www.idrive.com/](https://www.idrive.com/)* |
| Jungle Disk || *[https://www.jungledisk.com/](https://www.jungledisk.com/)* |
| Mozy || *[http://mozy.com/](http://mozy.com/)* |
| Livedrive || *[http://www.livedrive.com/](http://www.livedrive.com/)* |
|   ||   |

Your data’s confidentiality is a valid concern. Sending data across the Internet exposes it to the outside world. Anyone with a network sniffer between you and the backup destination can intercept your data. Never use an Internet backup product unless using strong connection encryption. This will ensure your data is safe during the transfer process. In addition to confidentiality concerns during transit, carefully consider how the data will be handled by the backup service provider. If you are paying another company to handle your backup data on its servers, how secure are its servers? Make sure any organization that stores your data has an aggressive security policy.

[Table 8-4](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8tab4) lists a few of the products that specialize in backups across the Internet.

The most common use for Internet backups is for workstation computers. Internet backups are popular for laptop computers that change locations frequently. Computers can be set up to perform backups at specific times or to continually back up changed files whenever you are connected to the Internet. Having current backups available for laptop computers is a useful additional layer of protection from damage or theft.

**technical TIP**

The online backup market changes rapidly and there are many more providers than those listed in [Table 8-4](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8tab4). Visit *[http://en.wikipedia.org/wiki/Comparison\_of\_online\_backup\_services](http://en.wikipedia.org/wiki/Comparison_of_online_backup_services)* for a more comprehensive and up-to-date list of companies that provide online backup software and services.

**Microsoft Windows and Application Backup and Recovery in a Business Continuity Setting**

Recall that the real value of a backup is not the backup itself, but its ability to play a part in recovering lost data. You must have a recovery plan in place before the backup is of much use. There are two main types of plans you must have in place to ensure your organization doesn’t suffer when the unexpected happens. The first plan is a **disaster recovery plan (DRP)**. Your disaster recovery plan covers the actions you must take when a disaster strikes to address the damage and return your infrastructure to a point where you can continue operations. The next plan is a **business continuity plan (BCP)** that ensures critical business functions continue in the face of interrupted processes. While these two plans are related and do work together, they each have their own purpose.

Disaster Recovery Plan

A disaster recovery plan contains the steps to restore an IT infrastructure to a point where an organization can continue operations. If a disaster occurs that causes damage and interrupts your business functions, it is important to return to productive activities as soon as possible. If your organization can’t carry out its main business functions, it cannot fulfill its purpose. A solid disaster recovery plan carefully identifies each component of your IT infrastructure that is critical to your primary business functions. Then the plan states the steps you can take to replace damaged or destroyed components.

There are several options available for serious disasters that damage or destroy major IT infrastructure components ([Figure 8-5](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig5)). These are a few of the most common options, starting with the most expensive option with the shortest cutover time:

• **Hot site**—A complete copy of an environment at a remote site. Hot sites are kept as current as possible with replicated data so switching from the original environment to the alternate environment can occur with a minimum of downtime.

• **Warm site**—A complete copy of an environment at a remote site. Warm sites are updated only periodically—normally daily or even weekly. When a disaster occurs, there is a short delay while a switchover team prepares the warm site with the latest data updates.

• **Cold site**—A site that may have hardware in place, but it will not likely be set up or configured. Cold sites take more time to bring into operation because of the extensive amount of configuration work required for hardware and software.

• **Service level agreement (SLA)**—A contract with a vendor that guarantees replacement hardware or software within a specific amount of time.

• **Cooperative agreement**—An agreement between two or more organizations to help one another in case a disaster hits one of the parties. The organization that is not affected by the disaster agrees to allow the other organization to use part of its own IT infrastructure capacity to conduct minimal business operations. There is usually a specified time limit that allows the organization that suffered damage time to rebuild its IT infrastructure.

**FIGURE 8-5** Disaster recovery options.

![image](OEBPS/Images/9781284031652_pg179.jpg)

Regardless of which option best suits your organization, the purpose of a disaster recovery plan is to repair or replace damaged IT infrastructure components as quickly as possible to allow the business to continue in operation.

Business Continuity Plan

There is a lot of confusion between a disaster recovery plan (DRP) and a business continuity plan (BCP). The two plans work closely with one another and depend on one another for success. You can summarize the difference between the two plans into two main points:

**1.** A DRP for IT ensures the IT infrastructure is operational and ready to support primary business functions. A DRP for IT focuses mainly on the IT department.

**2.** A BCP is an organizational plan. It doesn’t focus only on IT. The BCP ensures the organization can survive any disruption and continue operating. If the disruption is major, the BCP will rely on the DRP to provide an IT infrastructure the organization can use.

To summarize, a comprehensive BCP will take effect any time there is a disruption to business functions. An example would be a power outage or a water main break that interrupts water flow to your main office. A DRP takes effect when an event causes a major disruption. A major disruption is one where you must intervene and take some action to restore a functional IT infrastructure. A fire or tornado that damages your datacenter would be an example of a disaster.

Where a Restore Fits In

Any time there is data loss, at least part of a previous backup will need to be restored. In most cases, this means using a restore utility to extract some, or all, of the files and folders you backed up during the most recent backup operation. The restore procedure is a technical operation. Your DRP and BCP contain the steps you follow to get your organization back up and running. While the restore procedure is an important part of a successful recovery, it is only one part of a solid plan.

**Microsoft Windows Backup and Restore Utility**

Recovering from data loss can be a fairly straightforward process when you follow a solid plan. If you carefully developed a DRP and BCP, along with detailed procedures for backing up and restoring data, this part should be easy. If you do not have a plan, you’ll likely spend extra time figuring out what to do.

The process of restoring is basically the opposite of creating a backup. Of course, you can schedule a backup, but you will probably execute the restore process manually. In nearly every case, you follow these steps:

**1.** Verify that you have a stable infrastructure. Since you just suffered data loss, be sure that you know why you lost data and that you have addressed the problem. If you have not addressed the problem, you could end up losing more data.

**2.** Open your restore utility. The utility you choose will depend on the backup utility you used to create your backup images. In short, you have to use a restore utility designed to work with your backup utility.

**3.** Select the backup image to use and the type of restore (complete or selective) you’ll perform.

Once you start the restore process, the restore utility will copy the selected files back to their original locations. The result should be an environment with the damaged or missing data restored. You should be up and running again.

Restoring with the Windows Backup and Restore Utility

Use the Windows Restore utility to restore some, or all, of the files you backed up with the same utility ([Figure 8-6](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig6)).

You provide three types of information to the restore process. Follow the Backup and Restore Wizard prompts to enter:

• **The scope of the restore operation**—Choose one of the following options:

• Select the Restore My Files button to restore only files that you own.

• Select the Restore All Users’ Files link to restore files for all users.

• Select the Select Another Backup To Restore Files From link to restore files from a different backup location.

**technical TIP**

You can open the Windows Backup and Restore utility on a computer running Windows 7 using these steps:

**1.** Choose the Windows Start button > Control Panel.

**2.** Select System and Security > Backup and Restore.

**FIGURE 8-6** Windows workstation restore.

![image](OEBPS/Images/9781284031652_pg181.jpg)

• **What files and folders to restore**—Add individual files and folders you want to restore.

• **Where Windows will place the restored files**—Restore files back to their original location or to another folder.

Restoring with the Windows Server 2008 Server Recovery Utility

Several pieces of information you provide describe the recovery process. Follow the Server Recovery Wizard ([Figure 8-7](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig7)) prompts to enter:

• **Where Windows can locate the backup image**—Choose the local server or a remote server.

• **When the backup was created**—Choose the desired date for the backup you want to use.

**technical TIP**

You can open the Windows Server Backup utility on a computer running Windows Server 2008 using these steps:

**1.** Choose the Windows Start button > Administrative Tools > Windows Server Backup.

**2.** Select the Recover link to launch the Server Recovery Wizard.

**FIGURE 8-7** Windows server recovery.

![image](OEBPS/Images/9781284031652_pg182.jpg)

• **What to recover**—You can recover four different ways. Select one of:

• **Files and folders**—Select individual files and folders to recover.

• **Volumes**—Select entire volumes to recover.

• **Applications**—If you chose to back up specific applications, you can select the applications to recover.

• **System state**—Choose to recover only the system state to recover essential system settings.

• **Where Windows will store the recovered files and folders**—Files and folders can be recovered to their original location or another location. You can also select what Windows does if it encounters duplicate files and whether the recovery operation should recover access control lists (ACLs) along with recovered files and folders.

**Rebuilding Systems from Bare Metal**

A solid recovery plan will allow you to recover from any interruption. Some interruptions are minor and others are catastrophic. If a fire destroys your entire datacenter, along with all your computer hardware, you have to replace the hardware first. Once you have the proper hardware in place, you can start the software restore process. The specific steps you take depend on the type of backup you previously created.

**technical TIP**

Since the operating system, software, or data can’t be restored until you have working hardware, consider keeping extra hardware around to swap out in critical situations. Explore the option of acquiring an identical copy of critical hardware devices. If you suffer hardware failure and you have a spare server or laptop available, you may be able to restore your hardware functionality by just swapping the spare hardware for the damaged hardware.

If you backed up only critical files or folders, you’ll need to build each computer back to the point where you can restore those critical files. In most cases, those steps will include:

• Install the operating system.

• Be sure to install all patches and service packs to match the predisaster environment.

• Configure the operating system to match the predisaster settings.

• Install utility and application software.

• Be sure to install all patches and service packs to match the predisaster environment.

• Configure your software to match predisaster settings.

• Restore the critical files you backed up from the most recent backup.

Although backups probably run quickly and are simple, restoring your environment from a catastrophic disaster can be very time consuming. Another option is to perform a complete backup of the computer. This includes the operating system and all items you’ll need to restore the operating system, all configuration settings, and all applications and data. A complete system backup generally takes a lot longer since you are backing up literally everything. It can also make the process of restoring computers much easier. You need to create a complete system backup that includes all of the operating system and physical settings only once. After that, you can either perform full server backups or back up selected volumes or files and folders.

All Microsoft backup utilities provide the option to create a complete system backup that supports restoring to a computer with no operating system installed. Most third-party utilities provide this option as well. A restore that includes the operating system and all configuration settings is called a **bare metal recovery**. The name comes from the fact that you can restore everything from your backup media. All you need is the actual hardware, or the bare metal. If using Microsoft backup utilities, you can create a bare metal recovery backup with the GUI ([Figure 8-8](#18_Chaper8_split_001.xhtml#ba-9781284031652-ch8fig8)) or the command-line tool.

**technical TIP**

You can open the Windows Server Backup utility on a computer running Windows Server 2008 using these steps:

**1.** Choose the Windows Start button > Administrative Tools > Windows Server Backup.

**2.** Select the Backup Once link to launch the Backup Once Wizard.

Follow these steps to create a one-time complete backup for a bare metal restore:

**1.** Select Different Options then choose Next.

**2.** Select Custom then choose Next.

**3.** Choose Add Items.

**4.** In the Select Items window, select the Bare Metal Recovery check box, choose OK, and then choose Next.

**5.** Select Local drives to store the backup on a local drive or Remote Shared Folder to store the backup on a shared network folder, and then choose Next.

**6.** Select your desired location to store this special backup from the drop-down list, and then choose Next.

**7.** On the Confirmation page, choose Backup.

**FIGURE 8-8** Creating a backup for a bare metal recovery.

![image](OEBPS/Images/9781284031652_pg184.jpg)

Since the backup serves as protection from catastrophic failures, you should store it either on a remote shared folder or on an external drive. The external drive should be stored at a different location to ensure a disaster that destroys the primary computer does not destroy the backup as well. The recovery process starts with a stable computer and a Windows boot DVD. Follow these steps to perform a bare metal restore:

**1.** Boot from the Windows DVD (ensure any external drives you’ll need are connected).

**2.** In the main window, select Next.

**3.** In the Install Now window, select the Repair Your Computer link.

**4.** Load any necessary drivers on the next window, then select Next.

**5.** Select the Windows Complete PC Restore link.

**6.** Select the backup to restore and select Next.

**7.** Enter any additional settings and select Next.

Windows will install all computer settings and operating system using the backup selected. When the backup finishes, you should be able to reboot from your hard disk and log on to your newly restored computer. Unless you routinely create bare metal recovery backups, you will need to execute a normal restore to recover the most recent backup information.

**Managing Backups with Virtual Machines**

Many organizations have incorporated **virtualization** into their IT infrastructure. Virtualization is the ability to run two or more **virtual machines (VMs)** simultaneously on a single physical computer. A virtual machine is a software implementation of a physical computer. Virtualization allows organizations to do more with less physical hardware. There are many benefits to using virtualization in an IT infrastructure, including advantages in managing backups.

Windows Server 2008 R2 and Windows Server 2012 each include Microsoft’s **Hyper-V** technology. Hyper-V is a product that supports creating and running virtual machines in newer Windows Server operating systems. Hyper-V requires CPU support for virtualization and is optimized for server-based operations. While Hyper-V has many features and benefits, it supports the ability to create snapshots of a running VM. This ability makes creating a virtual backup image nearly trivial. All you have to do is create VM snapshots anytime you want to create a rollback point. Hyper-V lets you restore a VM back to any snapshot.

Virtualization offers many advantages to single-purpose physical hardware use. Many organizations enjoy increased performance as well as decreased cost of physical hardware. The backup and recovery features alone may make it worthwhile to explore virtualization in your environment.

**Hyper-V Alternatives**

Hyper-V is not the only virtualization product for Windows. Hyper-V is provided by Microsoft and is tightly integrated with Windows Server 2008 R2 and Windows Server 2012, but there are other products that work very well with Windows Server 2008, Windows Server 2012, Windows 7, and Windows 8. If you are new to virtualization, look at these products as well:

• **VMWare**—Commercial virtualization products for workstation and server environments: *[http://www.vmware.com/](http://www.vmware.com/)*

• **VirtualBox**—Open source virtualization software that runs on multiple operating systems, including Windows 7, Windows 8, Windows Server 2008, and Windows Server 2012: *[http://www.virtualbox.org/](http://www.virtualbox.org/)*

• **Virtual PC**—Microsoft Workstation virtualization product that runs on Windows 7: *[http://www.microsoft.com/en-us/download/details.aspx?id=3702](http://www.microsoft.com/en-us/download/details.aspx?id=3702)*

**technical TIP**

You can get complete details on Microsoft Hyper-V at *[http://www.microsoft.com/en-us/server-cloud/windows-server/server-virtualization.aspx](http://www.microsoft.com/en-us/server-cloud/windows-server/server-virtualization.aspx)*.

In fact, virtualization has many more benefits than just convenient ways to roll back. The entire movement toward cloud computing is based on virtualization. Cloud computing is based on running several virtual machines on physical servers. Cloud service providers make it easy to create, resize, and dispose of virtual machines. This flexibility makes it possible to provision just the right number of virtual servers to meet current application demands. Cloud service providers can maintain the physical servers and allow customers to manage virtual machines for a fee.

Cloud computing is growing in popularity and will change the way organizations conduct business. Now it is possible to create virtual machines, then add and remove capability based on current needs. Clouds can also make backing up and restoring easier than with traditional methods. The concepts are the same, however. Every organization, whether based in the cloud or in a traditional datacenter, must evaluate its needs for backup and recovery. Regardless of the techniques used, resilience in the face of disruptions or disasters is crucial to any organization’s survival.

**Best Practices for Microsoft Windows Backup and Recovery**

All too often, backup scheduling occurs as an afterthought—part of the list of items after setting up a new system. The backup should be an integral part of a complete recovery plan. A recovery plan should be in place before you physically install new computers or devices. Planning ahead for recovery protects your organization from unexpected interruptions that may impact critical business functions. Here are some industry best practices that will help keep your Windows environment and all the data it contains available to users:

• Ensure that you know which business functions are critical to your organization. These are the functions you must ensure do not permanently cease due to interruptions or disasters.

• Develop a plan to continue all critical business functions. This business continuity plan should cover all aspects of your organization to ensure your organization can resume operation after an interruption.

• Define recovery time objectives for each critical resource. Identify resources required for the recovery process. You’ll need to identify which parts of your recovery plan are sequential and which ones you can work on simultaneously. For example, assume you have eight servers you need to recover. Each server has an RTO of four hours. If only one person is working on the recovery plan, it is unlikely all eight servers will be operational within the RTO. You’ll likely need more people working to recover the servers.

• Develop a backup plan for each resource that minimizes the impact on performance while keeping secondary copies of data as up to date as possible. Explore various options, including alternate sites and virtualization.

• Automate as many backup operations as possible. Create logs and reports that make problems with backup operations easy to recognize.

• Verify all backup operations. A secondary copy of data with errors may be no better than damaged primary copy data.

• Document all backup and recovery procedures. Train all primary and backup personnel on all procedures.

• Test all recovery procedures rigorously. Conduct at least one full interruption recovery test each year. A full interruption test is one that actually interrupts normal operation to test the full recovery process. This type of test is the only way to fully test your recovery plan.

• Review your complete recovery plan quarterly (or more frequently), and adjust for any infrastructure changes.

These best practices provide a solid foundation for creating a secure recovery plan for your organization’s IT assets.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Availability is one of the three main pillars of security. A secure system ensures information is available to authorized users on demand. That means a secure system is one that is protected from data loss. A solid recovery plan ensures even the most catastrophic disaster interrupts your business process only temporarily. The plan specifies what the maximum downtime will be. Backups of workstations and servers are an important part of any recovery strategy.

In this chapter, you learned how to create backups, how to restore those backup images, and how to design a recovery plan. You learned what questions to ask to develop a recovery plan that fits your organization. Your complete recovery plan will help protect your organization’s information and ensure its overall security.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Backup**

**Bare metal recovery**

**Business continuity plan (BCP)**

**Compensating control**

**Disaster recovery plan (DRP)**

**Hyper-V**

**Primary copy**

**Recovery time objective (RTO)**

**Redundant array of independent disks (RAID)**

**Restore operation**

**Secondary copy**

**Virtual machine (VM)**

**Virtualization**

**Volume Shadow Copy Service (VSS)**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 8 ASSESSMENT**

  **1.** A valid backup is all an organization needs to recover from a disaster.

A. True

B. False

  **2.** Which of the following options are valid approaches to recovering from lost data? (Select two.)

A. Manually reconstruct lost data.

B. Reinstall the operating system and application software.

C. Restore from a backup.

D. Use anti-malware software to heal infections.

  **3.** Which of the following is the focus of data availability?

A. Backup plan

B. Backup schedule

C. Recovery plan

D. Disaster response plan

  **4.** Using removable media for backups generally \_\_\_\_\_\_\_\_\_\_\_ data availability, as opposed to using internal disks.

  **5.** Using removable media for backups generally \_\_\_\_\_\_\_\_ data confidentiality, as opposed to using internal disks.

  **6.** The only valid uses for restoring a backup image are to recover lost data and quickly load programs and files on completely new computers.

A. True

B. False

  **7.** Which of the following best describes RTO?

A. The goal for how much time a recovery effort should take

B. The maximum time a recovery effort can take

C. The minimum time a recovery effort should take

D. The maximum downtime an organization can sustain

  **8.** Which of the following do you *not* need to tell the Microsoft Windows Backup and Restore utility?

A. What to back up (files, folders, volumes, etc.)

B. What type of backup (full, incremental, blocks versus files)

C. Where to store the backup (local disk or shared network folder)

D. When to back up (date and time, frequency)

  **9.** The wbadmin command-line utility performs the same functions as the Microsoft Windows Backup and Restore utility on Windows workstations.

A. True

B. False

**10.** Only the Microsoft Backup utilities can create valid backup images for Windows computers.

A. True

B. False

**11.** Which type of plan addresses minor interruption such as a power outage lasting several hours?

A. RTO

B. DRP

C. VSS

D. BCP

**12.** Which of the following terms refers to an alternate recovery site that has the basic infrastructure in place, but no configured hardware and no software installed?

A. Warm site

B. Cold site

C. Hot site

D. Initial site

**13.** A recovery strategy that installs the operating system and all software and data on a completely new physical computer is called a \_\_\_\_\_\_\_\_.

**14.** Virtual image snapshots can back up only virtual machines that are not running.

A. True

B. False

**CHAPTER 9**

**Microsoft Windows Network Security**

MICROSOFT WINDOWS COMPUTERS can be very useful by themselves, but they are far more effective when they are able to communicate with one another. Windows computers that can communicate and exchange information have the ability to assume specific roles that make your organization’s computing environment more efficient and effective. Unfortunately, connecting computers also makes accessing your organization’s information easier for unauthorized users as well as authorized users. That means you have to be diligent to ensure the confidentiality, integrity, and availability of your data.

In this chapter, you’ll learn about techniques that many organizations use to ensure that their Windows networks are secure. You’ll learn how to connect computers together without risking your organization’s information to loss, alteration, or disclosure.

**Chapter 9 Topics**

This chapter covers the following topics and concepts:

• What network security is

• What the principles of Microsoft Windows network security are

• What Microsoft Windows security protocols and services are

• How to secure Microsoft Windows environment network services

• How to secure Microsoft Windows wireless networking

• What Microsoft Windows desktop network security is

• What Microsoft Windows server network security is

• What best practices for Microsoft Windows network security are

**Chapter 9 Goals**

When you complete this chapter, you will be able to:

• Describe goals for securing Microsoft Windows networks

• Secure Microsoft Windows networking services

• Secure Microsoft Windows wireless networks

• Secure Microsoft Windows workstations and servers

**Network Security**

Today’s IT environments include components connected to form a **network**, or multiple networks. A network is a collection of computers and devices joined by connection media. Network components work together to support an organization’s business functions. This makes information available for various uses and many users. As networks grow and become more functional, they can become complex to manage. One way to help organize network components and keep your network simple is to categorize components by function. One way to organize components is to use an IT Infrastructure approach to group components into functional areas, or domains. [Figure 9-1](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9fig1) shows an IT infrastructure with seven domains. These are the domains you’ll commonly encounter as you study IT environments.

In a general network perspective, users generally use their workstations to access other resources that are connected to an organization’s **local area network (LAN)**, a **metropolitan area network (MAN)**, or even a **wide area network (WAN**). [Table 9-1](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9tab1) lists each of the basic three network types and their characteristics.

Organizations rely on networked resources more than ever in today’s environments. Networks make it possible to share expensive resources. Examples of shared resources are color printers, high-performance disk subsystems, and applications. Networks increase efficiency in critical business functions by supporting faster information transfer and resource sharing. These benefits often result in direct cost reductions and productivity increases. Organizations rely on network resources to maintain cost-efficient operations. Protecting the network-based resources and services directly affects cost and efficiency. Implementing the controls necessary to support your security policy and protect your networks makes your organization more secure and effective.

**FIGURE 9-1** The seven domains of a typical IT infrastructure.

![image](OEBPS/Images/9781284031652_pg192.jpg)

| **TABLE 9-1** Network types. |
| **NETWORK TYPE** || **SIZE** || **DESCRIPTION** |
| Local area network (LAN) || A LAN covers a small physical area, such as an office or building. || LANs are common in homes and businesses and make it easy to share resources such as printers and shared disks. |
| Metropolitan area network (MAN) || A MAN connects two or more LANs but does not span an area larger than a city or town. || MANs are useful to connect multiple buildings or groups of buildings spread around an area larger than a few city blocks. |
| Wide area network (WAN) || WANs connect multiple LANs and WANs and span very large areas, including multiple country coverage. || WANs provide network connections among computers, devices, and other networks that need to communicate across great distances. For example, the Internet is a WAN. |
|   ||   ||   |

**technical TIP**

There are other types of networks, and you may see a few more terms used to describe networks. These terms aren’t in widespread use but they do describe specific types of networks. Other types of networks include:

• **Personal area network (PAN)**—A PAN consists of one or more workstations and its network devices, such as printers, network disk systems, and scanners. A PAN refers to the networked devices one person would likely use and normally does not span an area larger than an office or cubicle.

• **Campus area network (CAN)**—A CAN is larger than a LAN but generally smaller than a MAN. CANs are useful to connect the LANs across multiple buildings that are all in fairly close proximity to one another.

• **Global area network (GAN)**—A GAN is a newer term for a super-WAN. A GAN is a collection of interconnected LANs, CANs, MANs, and even WANs that span an extremely large area.

Network Security Controls

Network security controls often focus on limiting access to **remote resources**. A **local resource** is any resource attached to a local computer—the same computer to which the user has logged on. A remote resource is any resource attached to another computer on a network that is different from the computer to which the user is logged on. The user’s computer and the remote computer must be connected to a network to provide access to the remote resource. Many of the security controls you’ll find to protect network resources are similar to controls found protecting local resources. You’ll learn more about how each type of control works in a Microsoft Windows network environment in this chapter. The main types of network security controls include:

• Access controls for protected resources, such as printers and shared folders

• Communication controls to limit the spread of malicious software and traffic

• Anti-malware software on all computers in the network to detect and eradicate malware

• Recovery plans, including backups, for all computers and devices in the network

• Procedures to control network device configuration changes

• Monitoring tools and other detective controls to help detect and stop suspicious network activity

• Software patch management for all computers and devices in the network

**Principles of Microsoft Windows Network Security**

A secure Microsoft Windows network allows access on demand to resources for authorized users while denying access for unauthorized users. While the goal is similar to securing a single computer, putting that goal into practice involves more types of controls. Setting up a network exposes all resources in the network to security threats. Securing a Microsoft Windows network requires attention to three main types of vulnerabilities:

• **Physical and logical access**—Locate important computers and devices in physically secure areas and limit access to them. Separate networks logically into smaller segments to control resource access. Logically separating networks is beneficial when you need to keep groups of devices separate. This is common in larger networks.

• **Traffic flow**—Use firewalls and other types of filters to discard unauthorized traffic on a network. Filters should exist at all network boundaries and between segments to control network ingress and egress.

• **Computer and device security**—Ensure each computer and device on the network is prepared to handle any known attack. Any computer or device that does not have proper security controls deployed poses a threat to the entire network.

Securing a Microsoft network involves deploying controls that protect all network components from all known threats. Although that may sound like a large goal, it’s manageable when you approach it in a structured manner. The first step in understanding how to secure a network is to explore the most common components of networks.

Common Network Components

The main purpose of any network is to provide users with the ability to access and share remote resources. Networks use three main types of components to meet this goal. These components work together to allow users to share resources and reduce the need for multiple dedicated resources such as printers, file storage systems, and backup devices. The three main types of components in networks include:

• **Connection media**—The adapters and wires that connect components together. Not all connection methods use wires. With wireless devices, radio waves transmit data. So, connection media also includes wireless adapters.

• **Networking devices**—Hardware devices that connect other devices and computers using connection media.

• **Server computers and services devices**—Hardware that provides one or more services to users, such as server computers, printers, and network storage devices.

Many physical devices found in networks are actually combinations of several types of components. These components should work together to provide easy access to desired resources and still maintain the security of an organization’s information. [Figure 9-2](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9fig2) shows common network components.

**FIGURE 9-2** Common components found in networks.

![image](OEBPS/Images/9781284031652_pg195.jpg)

Connection Media

The purpose of any network is to allow multiple computers or devices to communicate with each other. By definition, networked computers and devices are connected to one another and have the necessary software to communicate. In the past, networked computers and devices were connected using cable. Today’s networks contain a mix of cables and wireless connections. While the technical details of network connections are beyond the scope of this discussion, it is important to have a general understanding of a network’s components.

There are two options to establish network connections between computers and devices. You either build your own network or pay another organization to allow you to use their network for your purposes. The following sections that cover connection media assume you own the connection media and are installing the hardware necessary to establish network communications. The following network connection media options appear most commonly in LANs, CANs, and MANs, but may be used in other networks as well.

Wired Network Connections

There are four basic cabling options for most physical network connections, including **coaxial cable**. Each option has its own advantages and disadvantages. If you choose to use physical cables for part or all of your network, you will have to run cables to each device. Running cables between devices takes careful planning. Make sure when you explore cabling options you evaluate the cost of installing all of the cables and connection hardware to support both your current and future needs. [Table 9-2](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9tab2) lists the four basic cable options, along with the advantages and disadvantages of each one.

Wireless Network Connections

Wireless connections are very popular in today’s network environments, where flexibility is an important design factor. Wireless connections allow devices to connect to your network without your having to physically connect to a cable. This flexibility makes it easy to connect computers, or devices, in situations where running cables is either difficult or not practical for temporary connections. The **Institute of Electrical and Electronics Engineers (IEEE)** defines standards for many aspects of computing and communications. The **IEEE 802.11** defines standards for **wireless local area network (WLAN)** communication **protocols**. A protocol is a set of rules that govern communication.

| **TABLE 9-2** Basic network cabling options. |
| **CABLE TYPE** || **DESCRIPTION** || **ADVANTAGES AND DISADVANTAGES** |
| **Unshielded twisted pair (UTP)** || The most common type of network cable, UTP generally consists of two or four pairs of wires. Pairs of wires are twisted around each other to reduce interference with other pairs. The most common type of UTP is Category 5 UTP, which supports 100 megabits per second (Mbps) for two pairs of wires and 1,000 Mbps for four pairs. || • Lowest cost• Ease of installation• Susceptibility to interference• Limited transmission speeds and distances |
| **Shielded twisted pair (STP)** || Same as UTP, but with foil shielding around each pair and optionally around the entire wire group to protect the cable from external radio and electrical interference. || • Low cost• Ease of installation• Greater resistance to interference than UTP• Same speed limitations as UTP but support for longer run lengths |
| Coaxial cable || A single copper conductor surrounded with a plastic sheath, then a braided copper shield, and then the external insulation. || • Higher cost• Difficult installation• Strong resistance to interference• Higher speeds and longer• run lengths |
| **Fiber optic cable** || A glass core surrounded by several layers of protective materials. || • Highest cost• Ease of running cable• Special tools needed to install end connectors• Immunity to radio and electrical interference• Extremely high speeds and long run lengths |

There are four main protocols currently in the 802.11 standard. There are also two emerging protocols that will likely play a role in future wireless networks. As with the discussion of wired network connections, the technical details are beyond the scope of this discussion, but it is important to know the basic differences between different wireless protocols. [Table 9-3](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9tab3) lists the most common current and emerging wireless protocols.

**Communication Protocol**

A communication protocol isn’t as complex as the name implies. The technical details of each protocol can be quite complex but the concept is pretty simple. A protocol is just a set of rules parties use to communicate. You use protocol rules every day. For example, suppose you want to invite a person to attend a meeting. If that person is a close friend, you would use an informal greeting and style of conversation. If, on the other hand, the person is an elected official, you would likely use a far more formal greeting and choice of words. You decide how to communicate based on your own protocol rules. You’ll learn more about computer communication protocols later in this chapter.

Generally, hardware that supports protocols with faster speeds with longer range costs more than hardware with slower protocols. Your choice of wireless protocols will likely be based on cost, transmission speed requirements, and other devices that may cause interference in a specific frequency.

Bluetooth is a popular wireless protocol for connecting devices over short distances. The most popular use of Bluetooth is to create PANs of devices that communicate with a computer or device. Headsets, mice, and printers are some examples of devices that commonly support the Bluetooth protocol. From a security perspective, it is important to consider Bluetooth support for your computers and devices when you are developing wireless policies and controls. Bluetooth-enabled computers are vulnerable to several types of wireless attacks unless you protect all wireless connections.

![image](OEBPS/Images/war.jpg)**WARNING**

In all cases, allowing wireless connections to your network increases the potential for unauthorized users to access network resources. If you choose to implement wireless connections, you must ensure you are using strong access controls and strong wireless encryption. In other words, use Wi-Fi Protected Access (WPA) as opposed to Wired Equivalent Privacy (WEP).

| **TABLE 9-3** Common current and emerging 802.11 wireless standards. |
| --- |

![image](OEBPS/Images/9781284031652_pg197.jpg)

**FIGURE 9-3** Simple network with a single hub.

![image](OEBPS/Images/9781284031652_pg198.jpg)

Networking Devices

Once you decide on the types of connections you’ll use for your network, you have to decide how your components connect to one another. Only the simplest networks with very few devices have every component connected. With more than just a few devices, this arrangement would make managing your network connections extremely difficult. Networks in today’s environments use several types of devices to keep connections manageable. You’ll see many different types of devices, but the following two sections discuss the ones you’ll most commonly use.

Hub

The simplest network device is a **hub**. A hub is simply a box with several connectors, or ports, that allows multiple network cables to attach to it. Common hubs have 4, 8, 16, or 32 ports. A hub is a hardware repeater. A hub takes input from any port and repeats the transmission, sending it as output on every port, including the original input port. Hubs make it easy to connect many devices to a network by connecting each device to the hub. [Figure 9-3](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9fig3) shows a simple network created using a single hub.

Switch

Hubs are inexpensive devices used to connect many computers and devices to a network. One problem with hubs is that they repeat all network traffic to all ports. This can cause message collisions and a frequent need to resend messages. Hubs also tend to contribute to network congestion since every computer and device receives all network traffic. Networks are designed to handle collisions and congestion but at the cost of high performance. A **switch** can help avoid many collision and congestion issues and actually speed up networks. A switch is a hardware device that forwards input it receives only to the appropriate output port.

For example, if Computer A wants to send a message to Computer B, a switch will send the message from Computer A’s port only to Computer B’s port. No other computers ever see the message. As an additional benefit, if Computer C wants to send a message to Computer F at the same time Computers A and B are talking, the switch can handle both connections at the same time without causing a collision. Switches are also more secure since the only computers that actually see information exchanged over the network are the computers involved in the transfer. This is more secure than a hub that repeats messages to all connected computers.

Router

A **router** is another network device that connects two or more separate networks. A router can connect any types of networks as long as they use the same protocols. Routers are more intelligent than switches and actually inspect the address portion of the packets on your network. The router examines the destination address and then forwards the packet to the correct outbound port. Routers can be standalone hardware devices or computers with multiple network interfaces running routing software.

Routers also provide an important security capability. You can define rules for each router that tell the router how to filter network traffic. You can restrict which packets are allowed to flow through the network. Routers give the ability to aggressively control how users and applications use the network.

Gateway

A **gateway** is a network device that connects two or more separate networks using different protocols. Networks using different protocols may include wired LANs, wireless LANs, and WANs. A gateway can perform many of the tasks a router performs but also has the ability to translate network packets from one protocol to another. Since it translates messages between protocols, a gateway is much more complex than either a router or a switch.

One of the most common types of gateways is one that connects a LAN to the Internet. This type of gateway is often called an **Internet gateway**. Gateways are necessary anytime you want to connect two networks that use different protocols. Gateways provide the same filtering capabilities of routers, and much more. Gateways analyze more than just the destination address and port of each message. Since the gateway has to translate an entire message from one protocol to another, detailed rules can be set up to filter out inappropriate traffic.

Server Computers and Services Devices

Networks provide easy access to shared resources and shared services. Centralized services make it possible for multiple users to share information and physical resources at a lower cost than duplicating information or purchasing devices for every workstation. Examples of shared resources include:

• File storage

• Printer and print services

• Central database and document management systems

• Central authentication services

Network File Server

One common service present in even the earliest networks is the file sharing service. A **file server** is a computer or hardware device that has at least three distinct components:

• One or more connected hard disk drives

• A network interface

• Software to provide network access to files and folders on the attached disks

In the past, most file servers were computers that managed shared folders or file systems. The file server managed connections and supported authorized read/write access to its disks by remote users. Computer-based file servers are still in widespread use, but standalone hardware devices with internal hard disk drives are becoming more popular. A file server’s main purpose is to provide secure access to its disk drives for remote users.

Network Print Server

A **print server** provides the interface between the network and one or more printers. Like file servers, the actual server can be a computer or a standalone hardware device. In either case, the print server accepts print jobs from authorized users and processes them. That means the print server may contain the intelligence to store multiple print jobs and provide advanced abilities to manage the printing process. Print servers vary widely in capabilities but all generally exist to allow multiple remote users to share printers.

Data Storage

Network data storage may sound like the service the file server provides but the two services are distinct. A file server only stores files. A data storage server organizes data and attempts to make it more accessible than just a list of files. Data storage software includes database management systems and document management systems. Both types of management software provide efficient, effective centralized access to data and documents for remote users.

Another substantial difference between file servers and data storage products is that data storage products generally provide far greater control over access authorization. File servers can control access to individual folders and files, but data storage software can control access to the contents of files. Database management systems and document management systems often provide their own features to maintain and authorize users and requests. These systems manage large amounts of data and can grant or deny access to individual pieces of information stored inside very large files. The advantage of databases and document management systems is they can provide fast and efficient access to large amounts of data while maintaining security of the data down to a very specific level.

Application Servers

**Application servers** are computers that run application programs on behalf of remote users. Instead of having remote users install and run programs, a user can request that an application server run the program and return the results. There are several advantages to using application servers:

**1.** Software does not need to be installed on every user’s computer; one license supports all users on one server (or several servers).

**2.** Updating software is easier; only application servers need to be updated.

**3.** Programs running on application servers tend to be closer to the database servers that store the data they need to run. Running programs on servers that are close to database servers can make accessing data much faster.

**4.** Since the database sends less data to the users’ computers, more data stays inside an organization’s secure network.

**5.** Server computers generally have the ability to serve many users efficiently, speeding up application programs.

Many of today’s application programs rely on distributed design, which means at least part of the application runs on an application server. This application model gets a lot of attention from developers and attackers alike. Be sure to secure application servers along with the other components of your network.

Firewalls

A firewall is a common network component. It filters network traffic to block suspicious packets or messages. A firewall examines all network traffic and compares it with predefined rules. Firewall rules tell the firewall software whether to forward or deny traffic. After matching traffic to its rules, a firewall should drop or reject any network messages that are unauthorized or suspicious. So, much of a firewall’s effectiveness is based on its rules.

Firewalls run as software on computers, or as standalone devices. Either way, the firewall needs at least two network adapters to separate incoming traffic from outgoing traffic. Routers and gateways often include firewall functionality and the ability to filter traffic before forwarding it.

One very useful application of firewalls is to separate your organization’s secure networks from its insecure networks. This is most useful when you want to separate your Internet access point from the secure network. Many organizations want to expose some services to the Internet while maintaining separation from the internal network. Firewalls make this scenario possible. Many organizations use two firewalls to create an untrusted network that Internet users can access and a trusted network for secure resources. The two networks are connected, but separated by a firewall.

The un-trusted network is called a **demilitarized zone (DMZ)**. The DMZ is a convenient place for Web servers, File Transfer Protocol (FTP) servers, or any servers you want unauthorized users to access without being able to get into your trusted network. [Figure 9-4](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9fig4) shows a DMZ with two firewalls.

Many firewalls provide the ability to translate an external IP address into an internally mapped IP address. The firewall stores a table that allows the software to translate the IP address for incoming and outgoing traffic. This feature, called **network address translation (NAT)**, hides the true IP address of internal computers from outside nodes. External nodes see only a generic IP address. The firewall receives traffic from the external IP address and changes the destination IP address to route the message to the correct internal IP address.

**FIGURE 9-4** DMZ with two firewalls.

![image](OEBPS/Images/9781284031652_pg202.jpg)

The main principle of Microsoft Windows network security is to ensure you enforce the C-I-A triad properties, confidentiality, integrity, and availability, for your information. Design the controls for the network media, traffic flow, and network computers and devices to ensure a secure environment and information.

**Microsoft Windows Security Protocols and Services**

Every computer or device connected to a network is called a **node**. Nodes communicate with one another by agreeing on a set of communication rules called a protocol. A communication protocol sets the rules for how nodes construct, send, receive, and interpret messages. Each protocol serves a specific purpose and has its own structure for constructing and addressing messages. In fact, several protocols are necessary to transport a message from one application to an application running on a remote computer. The physical media has one way of handling data, the network addressing software uses a different protocol, and applications use yet another set of rules to communicate.

Most discussions of network protocols include a discussion of the **Open Systems Interconnection (OSI) Reference Model**. The OSI Reference Model is a generic description for how computers use multiple layers of protocol rules to communicate across a network. The OSI Reference Model defines seven different layers of communication rules. You’ll also likely encounter another popular reference model, the Transmission Control Protocol/Internet Protocol (TCP/IP) Reference Model, when discussing network protocols. The **TCP/IP Reference Model** defines four different layers of communication rules. Both models are useful to describe how protocols work and how to implement them in network communications. [Figure 9-5](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9fig5) shows the TCP/IP Reference Model and the OSI Reference Model.

Protocols provide the ability for applications to exchange information with other applications on other computers. For example, most Web browser applications communicate with a Web server application using the **Hypertext Transfer Protocol (HTTP)**. Web browsers can use other protocols, but HTTP is the most common protocol for regular Web pages. The Web browser passes the message to the networking software layer. That layer handles the details of breaking the message into smaller packets suitable for networks, addressing the target machine, and routing the request across the network to ensure it arrives.

A common networking protocol is **Transmission Control Protocol/Internet Protocol (TCP/IP)**. TCP/IP is actually a combination of two separate protocols, but they work together in so many environments that they are often referenced as a single protocol.

Finally, the networking software passes the messages off to the software that physically controls the hardware that sends the data using physical media. This is the software and hardware that creates the radio transmission for wireless networks or electrical signals for Ethernet.

It is important to know the protocols your systems and applications use. You can change many protocol settings to make your systems more secure. You’ll want to learn more eventually about the specific protocol settings to use in hardening systems. For now, you should be aware of the most common protocols and the ones that relate most directly to security. [Table 9-4](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9tab4) shows a list of common protocols and how each one relates to your environment’s security.

**FIGURE 9-5** TCP/IP and OSI Reference Models.

![image](OEBPS/Images/9781284031652_pg203.jpg)

**Layered Protocols in Real Life**

The idea of layered protocols sounds complex. It really reflects what happens in human-to-human communication. Layers and translations are used in subtle ways every time you talk with a different person. Here’s an example that demonstrates the obvious need for multiple layers.

Consider how delegates communicate in the United Nations ([Figure 9-6](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9fig6)). Assume the U.S. delegate wants to send a written note to the delegates of China, Russia, and Italy. In this example, the protocol rule in place requires all written messages to be presented in French. Here is how the message travels through the U.N.:

**1.** The U.S. delegate writes a message in English, then hands the message to a translator—the delegate layer passes the message to the translator layer.

**2.** The translator translates the message into French, then hands it to an aide to take to the mailroom—the translator layer passes the message to the aide layer.

**3.** The aide makes three copies of the message, addresses each copy and places the messages in the U.S. outbox in the mailroom—the aide layer duplicates and passes the messages to the mailroom clerk layer.

**4.** The mailroom clerk picks up the messages from the U.S. outbox and places them in the appropriate inboxes for China, Russia, and Italy—the mailroom clerk handles the physical transfer.

**5.** An aide for each country, China, Russia, and Italy, picks up the message and delivers it to the translator—the aide layer collects a message from the mailroom and passes it to the translator layer.

**6.** The translator translates the message from French into the country’s national language and gives it to—the delegate the translator layer translates the message and passes it to the delegate layer.

**7.** The delegate for each country reads the message and takes appropriate action.

**FIGURE 9-6** Message flow in the U.N. example.

![image](OEBPS/Images/9781284031652_pg204.jpg)

| **TABLE 9-4** Common network communication protocols. |
| **PROTOCOL** || **DESCRIPTION** || **SECURITY NOTES** |
| Telnet || Legacy protocol used for connecting terminals to servers. Sends text to and from the server. Historically used for remote administration accessing command-line utilities. || Telnet sends all information, including usernames and passwords, in readable text. Telnet should always be considered insecure and should not be used. |
| Secure Shell (SSH) || Similar to Telnet, except messages are encrypted. Useful for secure remote system administration using command-line utilities. || Older versions, such as 1.X, contain documented vulnerabilities. Newer versions are secure for most uses. |
| HTTP (Hypertext Transfer Protocol) || Used for most Web browser/Web server communication. || All data is sent in the clear. HTTP is not appropriate for confidential data. |
| HTTPS (Hypertext Transfer Protocol Secure) || Secure HTTP. Useful for exchanging confidential information between Web browsers and Web servers. || HTTPS uses SSL/TLS to provide encryption services. Ensure your Web server is using SSL version 3.X or TLS. |
| SSL/TLS (Secure Sockets Layer/Transport Layer Security) || SSL is the predecessor of TLS. Both protocols provide encryption for Application Layer protocols, such as HTTPS. || TLS is the most secure. Do not use versions 1.X or 2.X of SSL. Use only SSL 3.X or TLS unless your application does not support newer versions. |
| TCP/IP (Transmission Control Protocol/Internet Protocol) || The most common protocol pair for Internet communication. || TCP/IP is a frequent target for attackers since it is used in so many applications. Use helper protocols, such as TLS, to secure TCP/IP communications and filters to detect malicious traffic. |
| UDP (User Datagram Protocol) || Another common protocol used in place of IP when persistent connections are not necessary or desirable. || Use the same precautions as TCP/IP. Use UDP with other protocols and filters. |
| IPSec (Internet Protocol Security) || A protocol suite used to secure IP communication by encrypting each IP packet. || IPSec secures any messages that use IP to communicate. IPSec is transparent to applications that use it. |
| PPP (Point-to-Point Protocol) || Protocol to establish a direct connection between nodes. || PPP includes the ability to encrypt and authenticate messages. |
| PPTP (Point-to-Point Tunneling Protocol) || One of three common protocols used for virtual private networks (VPNs). || PPTP relies on PPP’s encryption and authentication features to provide a VPN for applications that use TCP. |
| Layer 2 Tunneling Protocol (L2TP) || Another common protocol used for VPNs. || L2TP operates at a lower level than PPTP and must rely on a higher-level protocol, such as IPSec, to provide encryption. L2TP relies on UDP to transport messages. |
| SSTP (Secure Socket Tunneling Protocol) || New VPN protocol that uses SSL/TLS to encrypt HTTP traffic in a tunnel. || SSTP overcomes limitations that PPTP and L2TP messages have with firewalls and NAT devices. SSTP has no conflicts with NAT. |
| WEP (Wired Equivalent Privacy) || Older protocol for securing wireless network traffic. || WEP is a legacy protocol to encrypt wireless network traffic. It is better than nothing, but not sufficient to secure confidential information. |
| WPA (Wi-Fi Protected Access) || WPA and WPA2 are more secure protocols than WEP with stronger encryption for wireless network traffic. || The latest version of WPA, WPA2, is based on Advanced Encryption Standard (AES) encryption and supports several modes for varying needs of encryption security. |
| Kerberos || Protocol network nodes can use it to authenticate themselves to one another using an insecure network. || Windows uses Kerberos as a default authentication protocol. |
|   ||   ||   |

Windows uses protocols to communicate with other nodes across a network. This allows a program running on one computer to communicate with a program on another computer. It is common that the program on at least one end of a communication channel is a **Windows service**. A Windows service is a long-running program that performs a specific set of functions, such as a firewall, database server, or a Web server. Services generally run without requiring user intervention and commonly run on server computers. Most services that provide network-related functions monitor one or more **ports**. A port is a numeric identifier that programs use to classify network messages.

**technical TIP**

Most Web traffic is directed to port 80 on a server computer. When a server receives a Web-related message, it redirects the message to the service that monitors port 80. Most likely, any service that monitors port 80 is a Web server.

**Securing Microsoft Windows Environment Network Services**

Securing services is an important step in securing Windows computers. Services are often powerful programs that can be dangerous if an attacker takes control. Since services are just programs, they can contain programming errors and vulnerabilities. While there are many specific configuration strategies to secure each type of service, there are three high-level strategies that will keep all your services more secure. These strategies include keeping all service software up to date, limiting the permissions granted to service user accounts, and removing unneeded services.

Service Updates

Before enabling any service, develop a plan for keeping the service up to date. Service programs generally run for long periods of time waiting for requests. The services commonly monitor communication ports for requests and respond anytime they receive messages. Attackers know which services are in widespread use and they also know how to find out if you are running any services of interest. Whenever attackers uncover new vulnerabilities, they generally share the information with other potential attackers and start looking for vulnerable systems.

Once a new vulnerability surfaces, it is important to mitigate it as soon as possible. You can mitigate many vulnerabilities using compensating controls. The best way to address a vulnerability is to remove it. Many updates to service software do just that. Keep current on the latest releases available for any services you run. Keeping Windows updated with the latest service packs will keep many services up to date, but will not address any non-Microsoft services you run. If you run any non-Microsoft services, such as the Apache Web server or an Oracle database, you’ll need to consult their Web sites for update information. Keeping your services up to date will help maintain your environment’s security.

Service Accounts

Windows defines rights and permissions based on user accounts. Windows runs every program as a specific user. That means even services run as a user. By default, many services run as a local admin account. If an attacker can exploit a vulnerability and compromise a service, it is possible the attacker could assume the identity of the user running the service. For this reason, it is important to run each service as a user that possesses the minimum privileges necessary to perform the service’s functions.

**FYI**

Windows Server 2008 R2 included the new managed service accounts (MSA) feature. While this made managing service accounts easier, it didn’t solve all of the issues. MSAs did provide automatic password management and instance name registration. However, the accounts could not be shared across multiple servers. Windows Server 2012 introduced group managed service accounts (gMSA). These accounts extend the earlier capabilities. Windows Server 2012 computers can share gMSAs and even use them for scheduled tasks. Administrators can also use the new gMSAs for more common software services, such as Microsoft Exchange or Microsoft SQL Server.

Carefully review the user account used for each service. You can see which user Windows uses for each service in the Services Microsoft Management Console (MMC) snap-in. You can use these steps to access the Service Properties:

**1.** Choose the Windows Start button then select Administrative Tools > Services.

**2.** Select a service, right-click to open the context menu, and then select Properties.

**3.** Choose the Log On tab to view or change the user account Windows uses to run the service.

![image](OEBPS/Images/war.jpg)**WARNING**

Avoid using a domain admin account for any service. If a domain admin account is used, an attacker can jeopardize an entire network by compromising a service running on your least secure computer.

Instead of using default accounts for services, create one or more user accounts that limit what services can do. Here are guidelines for creating secure accounts for services:

• Create a new account, with leading underscores in the name, whichs makes it easier to identify service accounts.

• Use strong passwords.

• Revoke all logon rights for local and remote logons.

• Set the Password Never Expires property.

• Set the User Cannot Change Password property.

• Remove the user from all default groups.

• Assign the minimum privileges necessary to run services.

These guidelines will help create user accounts that are safer for services. Any service compromise will have less impact than a service using a local or domain admin account. Be sure to test the new accounts extensively. Be sure to grant sufficient permission to the user for the service to perform all the necessary tasks.

Necessary Services

The best way to secure a specific service is to disable, or even remove it. If the service isn’t running, it isn’t providing any functionality. If a service is not needed on a computer, stop it from running. It is important to disable unused services. Since a service monitors one or more communications ports, each service is a potential point of attack. Start only the necessary services.

**FIGURE 9-7** Windows Services startup options.

![image](OEBPS/Images/9781284031652_pg209.jpg)

For Windows Server computers, enable only the role(s) you need the computer to perform. Windows will not install services that do not fit a specific role. For example, if you don’t need a Web server running on a computer, don’t enable the Web server role. A server that doesn’t have Internet Information Services (IIS) installed is immune to IIS vulnerabilities. For both Windows client and server computers, review all of the services in the Services MMC snap-in. Ensure that you need each running service.

If a service is not needed, there are several steps you can take:

• **Stop it**—Stop a service in the Services snap-in. Change its Startup Type to Manual to disable the service from starting automatically when the system boots.

• **Disable it**—Change the Startup Type to Disabled to tell Windows not to start a service.

• **Remove it**—If an unneeded service is installed on a computer, remove the software for the service. The procedure to remove a service depends on the type of service.

[Figure 9-7](#19_Chaper9_split_001.xhtml#ba-9781284031652-ch9fig7) shows the startup options in the Services MMC snap-in.

Regardless of your mitigation actions, take the time to review all of the services your computers run. Ensure each running service is necessary for that computer to accomplish its goals. Stop any unnecessary services. Each service you stop removes another potential attack point from your environment.

**Securing Microsoft Windows Wireless Networking**

Securing your wireless network is a crucial step in securing your overall Windows environment. Allowing unsecured wireless access to your Windows network can provide easy access for attackers and undermine your efforts to secure your environment. Wireless access makes it easier for anyone to connect to your network even from outside your physical environment. An attacker armed with a notebook computer and a wireless card can access an unsecured wireless network from as much as several hundred feet away from the access point. You can’t rely on any physical security measures to protect your wireless networks, as you can with wired connections.

![image](OEBPS/Images/war.jpg)**WARNING**

If you do not turn on the security features of your wireless Internet devices, you may be the victim of Wi-Fi jacking. This occurs when attackers walk or drive through business areas and neighborhoods and identify unprotected wireless LANs from the street using a laptop or a handheld computer. When they find an unprotected network, they can hijack that wireless connection to download illegal materials, send spam, etc. They can also use their connection to the wireless network to hack into other computers on the LAN to steal information and identities.

There are several steps you can take to secure wireless networks. The actual steps you take to enable each of the following suggestions depend on your wireless hardware manufacturer. However, all current wireless devices provide the ability to make your wireless network more secure. For specific instructions for your hardware, consult the hardware manufacturer’s Web site or user guide. Follow these guidelines to make any wireless network more secure:

• **Use WPA or WPA2 encryption**—Do not use WEP unless your wireless access point does not support WPA/WPA2. Security professionals have demonstrated they can compromise WEP in a matter of minutes. WPA/WPA2 is the only secure protocol you should consider for confidential information available on a wireless network.

• **Use Media Access Control (MAC) address filtering**—Most wireless access points allow you to define valid MAC addresses. If you enable MAC address filtering, only valid MAC addresses can connect to the wireless network. MAC address filtering does make administration more difficult and attackers can spoof MAC addresses, but adding layers of controls makes the environment safer.

• **Disable Service Set Identifier (SSID) broadcast**—Many attackers scan for potential victim networks by collecting information for all networks broadcasting **Service Set Identifiers (SSIDs)**. Turning off the SSID broadcast doesn’t make your network more secure, but it does make it less visible to casual scanners.

• **Limit outside eavesdropping**—Each wireless access point has an effective transmission range. You can move the devices away from external walls to make it harder to use a signal outside your physical environment. Locate your wireless devices as far away from external walls as possible while still providing ample coverage for your organization’s users.

• **Physically separate wireless networks by purpose**—Many organizations deploy at least two wireless networks. One wireless network is secure and requires each new device and user to register with an administrator before getting access. This wireless network would likely provide access to the organization’s internal network. Another wireless network uses fewer controls and makes it easy for guests to connect. This second wireless network would likely connect only to an Internet bridge. This approach makes it easy to give guests Internet access without exposing your organization’s network.

Limiting access to wireless networks makes your environment far more difficult for attackers to compromise. Wireless security is only one layer in your overall security plan, but it is an important one.

**Microsoft Windows Desktop Network Security**

Windows desktop computers operate in the Workstation Domain in the IT infrastructure and generally operate as clients in network communications. That means desktop computers generally initiate communication by sending requests to servers in another domain. The main areas of focus with respect to desktop network security should be user authentication and authorization, malicious software protection, and outbound traffic validation.

User Authorization and Authentication

Users can do only what you allow them to do. One of the best ways to keep attackers away from your network is to keep them away from your workstations. In addition to physical controls to limit unauthorized access to workstations, it is important to aggressively protect workstations from unauthorized logons. This means deploying a user account policy that makes it difficult for an attacker to log on as an authorized user. Here are some guidelines to protect your workstations from unauthorized access:

• Train all users on how to create strong passwords and protect user account credentials.

• Require unique user accounts with strong passwords for each user.

• Use the principle of least privilege to grant minimal rights and permissions to users.

• Audit failed access attempts.

• Audit all logons for privileged accounts.

• Enable account lockout after five failed logon attempts.

• Explore alternate authentication methods. For more privileged users or workstations, consider multifactor authentication.

• Remove or disable unused user accounts.

• Disable remote access.

Malicious Software Protection

A popular attack vector for central servers is to compromise a trusted workstation using malicious software. A workstation is often easier to compromise than a server due to the relative lack of attention to security controls. Workstations are frequent targets for attacks. Don’t forget to consider all workstations that will access your organization’s environment. This includes remote workstations. Remote workstations can be very difficult to manage, but you cannot overlook the security risks associated with any workstation.

You should require all workstations have anti-malware software installed before you allow them to connect to your environment. This includes antivirus and anti-spyware software. Ensure the software and the software’s signature databases are up to date. You can use Group Policy to enforce this requirement. You should also create a schedule to scan workstations for malicious software. Just because the software is present doesn’t mean the computer is clean. It is important to proactively scan workstations at least weekly along with active anti-malware shield software to maintain as clean an environment as possible for your workstations.

Outbound Traffic Filtering

Despite your best efforts, it is possible that one or more of your workstations may be compromised. One popular attack when targeting workstations is to place on a workstation malicious software that creates a flood of messages. Since the workstations inside your network are trusted nodes, your network will accept the traffic. There are several attacks that send a large volume of network messages that end up flooding the network and making it unusable for legitimate traffic. Attacks of this type are called **denial of service (DoS) attacks**. The result of a successful DoS attack makes information unavailable to authorized users since the network is too saturated to respond. If the attack coordinates with other compromised workstations, it is called a **distributed denial of service (DDoS) attack**.

You can protect your network from many DoS and DDoS attacks by configuring each workstation’s firewall to filter outbound traffic. Most DoS and DDoS attacks create traffic that a firewall can easily recognize and refuse to pass onto the network. Although your workstation has still been compromised, the attack is not effective if the traffic doesn’t make it to the network. Make sure all workstations have active and up-to-date firewall rules that filter incoming and outgoing traffic for known suspicious packets.

**Microsoft Windows Server Network Security**

Windows servers provide various types of services for enterprises. In many cases, servers either directly or indirectly enable enterprise applications to access shared data to support business functions. While compromising a workstation may open a door into an organization’s secure network, compromising a server will likely allow an attacker to get even closer to sensitive or confidential data.

Although each layer of security is important to the overall security of your organization’s data, you should view server security controls as even more crucial. The controls you place on server computers will only act as obstacles for attackers that have already found ways to defeat outer layers of controls. It is likely any attacker who has made it this far is sophisticated and skilled. You must carefully design, deploy, and monitor controls for servers in your network to increase the likelihood that you’ll stop an attack before it compromises the data you’re trying to protect.

Authentication and Authorization

All three of the C-I-A triad properties of data security depend on the positive identification of an authorized user. Your servers inside your organization’s secure network should require specific user accounts to use any service. You may allow anonymous users or shared user accounts to access some resources, such as generic Web pages or public file downloads, but these servers should reside in the DMZ and not in your secure network.

Inside the secure network, you should authenticate all computers and users before processing resource access requests. Windows uses Kerberos by default to provide a secure method to establish two-way authentication. This level of authentication assurance provides protection from eavesdropping or certain types of replay attacks.

A replay attack is one where an attacker intercepts authentication messages. Unless the attacker is working with a protected network, it is possible to replay the authentication messages and log on again. It is similar to your Web browser storing your password to a Web site. But in this case, the attacker is storing someone else’s password. Kerberos gives both sides of a network conversation the assurance that the other party is who he or she claims to be.

Carefully examine each server’s role to ensure that no unnecessary services are running. For the services you are running, make sure you have defined access control lists (ACLs) for all authorized users and all protected resources. Apply the principle of least privilege for all users. Use Group Policy Objects (GPOs) as much as possible to standardize security settings.

Malicious Software Protection

Servers are vulnerable to malware just like workstations. You must install antivirus and anti-spyware software on each Windows server on your network. As with workstations, be sure to update both the software and signature databases frequently. Check for updated software and signature databases daily for server computers.

Use Group Policy to enforce this requirement on servers as well as for workstations. You should also create a schedule to scan each server for malicious software. Your scan schedule depends on the services and data on any server, but weekly scans should be the minimum frequency. Scheduled scans, along with active anti-malware software will help you to maintain as clean an environment as possible for your servers.

Network Traffic Filtering

Firewalls protect services running on servers by filtering out suspicious traffic that attackers could use to compromise servers. The success of your firewall depends on its rules and location. Standalone firewalls can be used to filter traffic before it reaches a server or you can implement firewalls on your servers.

Either option has advantages and disadvantages. Standalone firewalls relieve some of the workload from your servers. The firewall device processes firewall rules and forwards only approved traffic. The server never sees traffic that does not match your firewall rules. The disadvantages of standalone firewalls include additional administrative workload, since standalone firewalls are separate devices, and additional hardware cost.

Firewalls that are integrated with servers have advantages and disadvantages. First, Microsoft’s firewall uses the familiar MMC interface for administration. You can also use GPOs to enforce standard rules across multiple servers. Microsoft’s firewall also comes with Windows Server operating systems and does not require an additional license or hardware purchase. The main disadvantage is that an embedded firewall adds to the server’s workload. The server must examine all network traffic to apply its filtering rules. Another disadvantage is that since a firewall is a program, it can have vulnerabilities that attackers may be able to exploit. An attacker who compromises a server firewall may be able to gain access to protected resources on that server.

Regardless of the type of firewall, set up rules to allow only valid traffic for the specific server functions you define. Deny, and potentially log, all other traffic.

![image](OEBPS/Images/war.jpg)**WARNING**

Be careful about logging firewall traffic. Your log file can become quite large if you don’t monitor and clear it out periodically. Log only the events you really need and carefully monitor the size of your log files.

**Best Practices for Microsoft Windows Network Security**

Securing a Windows network is an ongoing endeavor. Although the process never really ends, you can reach a level of assurance that your network is secure from most threats. It is important to continually monitor controls to ensure they are as effective as expected. Here are some best practices that will help you get started securing your network and provide a good set of guidelines for ensuring your network stays secure:

• Identify sensitive data.

• Protect sensitive data at rest using encryption.

• Establish unique domain user accounts for each user.

• Enforce strong passwords for all user accounts.

• Create new user accounts with limited rights and permission for services.

• Do not allow any services to run as a domain admin user.

• Use Kerberos for secure authentication.

• Install firewalls to create a DMZ.

• Place all Internet-facing servers—Web servers and other publicly accessible servers—in the DMZ.

• Use encrypted communication for all traffic flowing through the DMZ and the trusted network.

• Use encryption for all communication involving sensitive data.

• Establish firewall rules.

• Deny all suspicious traffic.

• Allow only approved traffic for servers.

• Filter inbound and outbound traffic for servers and workstations for malicious messages.

• If your firewall supports it, automatically terminate connections with sources generating DoS traffic to mitigate DoS attacks in process.

• Install anti-malware software on all computers and establish frequent update schedules and scans.

• Update software and signature databases daily.

• Perform quick scans daily.

• Perform complete scans at least weekly.

• Use WPA or WPA2 for all secure wireless networks.

• Disable SSID broadcast for secure wireless networks.

• Do not enable wireless or mobile broadband cards while connected to your organization’s internal network. Always disable your wireless adapter before connecting a laptop to the wired network.

• Do not allow visitors to roam around your facilities using wireless LANs. Many access points can be physically reset to insecure factory default settings by pressing a reset switch on the box.

• Avoid connecting to public networks. When you connect to an open wireless network, you should have no expectation of privacy or security.

• If you have to use an open wireless connection, do not visit Web sites that require usernames, passwords, or account numbers, such as online banking. Use an encrypted connection or a virtual private network (VPN).

• Install a separate wireless access point connected only to the Internet for guests.

• Disable or uninstall any services that you do not need.

These best practices provide a solid foundation for establishing and maintaining a secure Windows network.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Securing a Windows network means securing all of the components. You learned about the different components that make up a Windows network. You learned about workstations, servers, devices, and software. You also learned about the process to secure each type of component. While securing a Windows network takes planning and effort to be successful, it is possible.

Once you know your network and what each component does, you’re ready to start planning for the most effective security controls. No control set is best for every organization. The controls that work best for your network will maximize the C-I-A triad properties for your data and still support your business functions.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Application server**

**Coaxial cable**

**Demilitarized zone (DMZ)**

**Denial of service (DoS) attack**

**Distributed denial of service (DDoS) attack**

**Fiber optic cable**

**File server**

**Gateway**

**Hub**

**Hypertext Transfer Protocol (HTTP)**

**IEEE 802.11**

**Institute of Electrical and Electronics Engineers (IEEE)**

**Internet gateway**

**Local area network (LAN)**

**Local resource**

**Metropolitan area network (MAN)**

**Network**

**Network address translation (NAT)**

**Node**

**Open Systems Interconnection (OSI) Reference Model**

**Port**

**Print server**

**Protocol**

**Remote resource**

**Router**

**Service Set Identifier (SSID)**

**Shielded twisted pair (STP)**

**Switch**

**TCP/IP Reference Model**

**Transmission Control Protocol/Internet Protocol (TCP/IP)**

**Unshielded twisted pair (UTP)**

**Wide area network (WAN)**

**Windows service**

**Wireless local area network (WLAN)**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 9 ASSESSMENT**

  **1.** A \_\_\_\_\_\_\_\_ is a network that generally spans several city blocks.

  **2.** A local resource is any resource connected to the local LAN.

A. True

B. False

  **3.** Which of the following devices repeats input received to all ports?

A. Switch

B. Hub

C. Gateway

D. Router

  **4.** \_\_\_\_\_\_\_\_ cabling provides very good protection from interference but is difficult to install.

  **5.** Even the newest wireless protocols are slower than using high-quality physical cable.

A. True

B. False

  **6.** Which LAN device commonly has the ability to filter packets and deny traffic based on the destination address?

A. Router

B. Gateway

C. Hub

D. Switch

  **7.** A \_\_\_\_\_\_\_\_ is an untrusted network that contains Internet-facing servers and is separated from your trusted network by at least one firewall.

  **8.** Which network device feature provides the ability to hide internal network node addresses?

A. DMZ

B. NAT

C. STP

D. OSI

  **9.** Which network layer reference model includes four layers to describe how computers use multiple layers of protocol rules to communicate across a network?

A. IEEE

B. IPSec

C. UDP

D. TCP/IP

**10.** Which of the following actions is *not* an effective way to secure Windows services that you do not use?

A. Stop it

B. Disable it

C. Block it

D. Remove it

**11.** You should disable the \_\_\_\_\_\_\_\_ broadcast to make wireless networks harder to discover.

A. SSID

B. NAT

C. MAC

D. WPA

**12.** A successful DoS attack violates which property of the C-I-A triad?

A. Availability

B. Integrity

C. Consistency

D. Confidentiality

**13.** Where must sensitive data appear encrypted to ensure its confidentiality? (Select two.)

A. While in use in the workstation

B. During transmission over the network

C. As it is stored on disk

D. In memory

**14.** Which authentication protocol does Windows Server 2008 use as a default?

A. NTLM

B. Kerberos

C. WPA

D. NAT

**15.** What can some firewalls do to attempt to stop a DoS attack in progress?

A. Alert an attack responder

B. Log all traffic coming from the source of the attack

C. Terminate any connections with the source of the attack

D. Reset all connections

**CHAPTER 10**

**Microsoft Windows Security Administration**

THE SECURITY OF AN ORGANIZATION’S INFORMATION is a direct result of the quality of its security policy. The security policy states the importance of security and defines a secure environment. Once a solid security policy is defined, it must be put into practice. Administering the components of a security policy means creating and deploying controls that ensure compliance with the policy.

In this chapter, you’ll learn how to ensure that your organization meets your security policy’s goals. You’ll learn about the responsibilities of a security administrator and the tasks needed to go from a policy to usable controls. You’ll also learn how important it is to constantly review and measure performance to ensure that you maintain the most secure environment possible.

**Chapter 10 Topics**

This chapter covers the following topics and concepts:

• What security administration is

• How to maintain the C-I-A triad in the Microsoft Windows operating system (OS) world

• What Microsoft Windows OS security administration is

• How to ensure due diligence and regulatory compliance

• What the need for security policies, standards, procedures, and guidelines is

• What best practices for Microsoft Windows OS security administration are

**Chapter 10 Goals**

When you complete this chapter, you will be able to:

• Describe Microsoft Windows OS security administration

• Maintain the C-I-A triad in the Microsoft Windows OS

• Ensure due diligence and regulatory compliance

• Understand the need for security policies, standards, procedures, and guidelines

**Security Administration Overview**

**Security administration** is the process of putting security controls into effect within the IT infrastructure. Security administrators configure and maintain all of the computers and devices to uphold your security policy. While many of a security administrator’s tasks center on Windows server and workstation computers, other devices also require attention. As a security administrator, you’ll be responsible for ensuring that the following hardware components are secure:

• Windows servers

• Windows workstations and mobile devices

• Network connection media

• Network connection devices (hubs, switches, routers, gateways, and firewalls)

• Wireless access points

• Printers

• Shared storage devices

• Scanners

• Any other network devices

The responsibilities of security administration extend far beyond managing hardware. The following are examples of additional items security administrators must ensure are up to date and configured to be as secure as possible:

• User accounts

• Authentication methods and credentials

• Windows operating systems

• Application software

• Anti-malware software and signature databases

• Other supporting drivers and software

• Software tools and utilities

• Group Policy

• Active Directory (AD)

• Backup schedules

• Recovery plans

• Maintenance plans

Security administration is the process that puts security controls in place.

The Security Administration Cycle

The security administration process is not a straight-line process that is completed and finished. Security administration is a cycle. The Deming cycle is one common method that describes the phases that you will encounter in security administration. The **Deming cycle** was made popular by Dr. W. Edwards Deming. It explains standardized quality control. The Deming cycle is also known as the **Plan-Do-Check-Act (PDCA)** process:

• **Plan**—Establish objectives and the processes to meet a goal. In security administration, the stated goal is one aspect of a security policy. A specification document will be created during the planning activity. It details how to measure your results to determine if you’ve met your goal.

• **Do**—Implement the process you planned in the previous step.

• **Check**—Measure the effectiveness of the new process and compare the results against the expected results from the plan.

• **Act**—Analyze the differences between expected results and measured results. Determine the cause of any differences and proceed to the Plan process to develop a plan to improve the performance.

[Figure 10-1](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig1) shows the Plan-Do-Check-Act cycle.

Security administration is a quality process. Several basic concepts help keep activities in perspective. First, quality is a continuous process, not a single goal. There is always room for improvement in any IT infrastructure. It is your responsibility as a security administrator to constantly follow the Plan-Do-Check-Act cycle. Following the cycle ensures that your environment maintains the highest level of security possible.

**FIGURE 10-1** Plan-Do-Check-Act cycle.

![image](OEBPS/Images/9781284031652_pg220.jpg)

Second, a proactive plan for security is less expensive than a minimal plan relying on detective controls. Manufacturers know that reducing defects in their processes saves more money than using inspections to catch the defective items. Prevention is always better than a cure. The same concept in security means it is better to implement preventive controls, than to rely on detective controls to throw an alert when something bad happens. In reality, both types of controls are needed. Search for a control that denies an undesired action. If controls stop an attack before damage occurs, you’ll spend less time hunting through audit logs trying to figure out what happened.

Security Administration Tasks

The security administration process includes any tasks that directly support an organization’s security policy. The security administrator’s role includes tasks to keep a Windows environment secure. [Table 10-1](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10tab1) lists some of the more prominent tasks of a security administrator.

The tasks in [Table 10-1](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10tab1) do not represent all of the responsibilities of a security administrator. The tasks listed tend to be common examples across organizations. Each organization will have a slightly different list of tasks its security administrators carry out to maintain a secure environment.

**Maintaining the C-I-A Triad in the Microsoft Windows OS World**

Every security control deployed should directly address a security policy goal. Each goal in the security policy should support one or more of the C-I-A triad properties—confidentiality, integrity, and availability. As controls are developed and deployed, be sure to protect all three properties for data at multiple layers. Any unaddressed security property leaves your data vulnerable to attack.

**Partial Security Is No Security**

Failure to ensure any of the three C-I-A triad properties is failure to protect your data. For example, assume you are the security administrator for a group of physicians. You manage a small Windows network. The network runs software to process and store medical and billing records for the medical practice. You store all of the medical records in an encrypted database. You restrict access to medical data to a limited number of user accounts. You allow only authorized clients to access the network using encrypted connections. Your database stores record-based access control lists (ACLs) that allow only specific access for viewing and changing data. You create a backup of the entire database daily to protect from data loss.

Your use of encryption, user accounts, and ACLs enforces data integrity and confidentiality. However, you find that there is no plan to replace the computer hardware for the database server if it fails. You find that ordering a replacement server would take at least 24 hours to arrive and another six hours to prepare for use. Your medical data would be unavailable during that time. Since you have not protected the availability property of your data, it isn’t really secure.

| **TABLE 10-1** Common security administrator tasks. |
| **TASK** || **DESCRIPTION** |
| Provide input for Acceptable use policies (AUPs) || AUPs provide users with a documented statement of actions that are acceptable and unacceptable. AUPs provide guidance for aspects of computer use, such as e-mail, Internet, personal use of business computers, and standard of care when handling business information. Developing AUPs gives planners the ability to state security goals, define controls, and decide on consequences for noncompliance. |
| Enforce password controls || Password controls are some of the most common and visible controls because they affect every user. A user’s password is one of the first targets for many attackers. |
| Enforce physical security standards || Physical security is an important layer to secure all components in the IT infrastructure. Components that store or transmit sensitive data should have stronger physical controls. For example, the database servers that store an organization’s most critical and confidential data should be located in a room with a controlled environment and very limited physical access. |
| Deploy controls to meet encryption requirements || Enforce encryption for data at rest and when sensitive data is transmitted across the network. Appropriate controls depend on data sensitivity and its destination. For example, most, if not all, data should be encrypted when it is transferred to clients over the Internet. Data transferred between two trusted servers both in a secure datacenter, however, may not need encryption. |
| Implement backup policies || Develop schedules and procedures to ensure all IT infrastructure components are backed up with current data. Waiting too long between backups may mean available backups aren’t very useful for recovery. |
| Keep software up to date || Ensure all operating system and application software has as many necessary patches applied as possible without affecting the environment’s ability to perform business functions. |
| Ensure anti-malware controls are current and in force || Enforce requirements to ensure anti-malware software is in place on all computers and is kept up to date. |
| Monitor log files || Identify log files and regularly review each file for unauthorized activity. Know what you’re looking for and have a plan of action if unauthorized activity is located. |
| Monitor system and network performance || Monitor system performance measurements for critical computers and network devices for unusual activity. Have plans in place to react to any identified unusual activity. |
|   ||   |

Maintaining Confidentiality

Protecting data confidentiality means keeping it safe from unauthorized access. All object access decisions made in Windows depend on the effective user. The effective user is the user account that is running the process requesting object access. Any decision to grant or deny access to an object depends on the discretionary access control list (DACL) that exists for the object and effective user. Ensuring that you know the identity of the user running any process is crucial to protecting integrity and confidentiality. With respect to user identity and authorization, you can use the same types of controls to enforce confidentiality that you used to enforce integrity.

| **TABLE 10-2** Security controls that protect data confidentiality. |
| **CONTROL** || **DESCRIPTION** |
| Encryption || Encrypting any data scrambles it in such a way that it is unreadable. Anyone who possesses a valid decryption key can unscramble that data back to its original form. By distributing decryption keys to authorized users only, you can use encryption to enforce data confidentiality. You can employ encryption at different levels, including disk, volume, folder, file, or application-level data object. |
| Password policies || Documented password policies serve as a basis for user training. Password settings in Group Policy make it easy to enforce password policies across your entire Windows environment. |
| Object DACLs || Extend DACLs used to protect integrity to include restrictions on users authorized to read or access objects, not just modify them. |
| Active Directory || Active Directory provides a central repository for security policy settings along with the ability to easily deploy settings to many target locations. AD is an important part of an effective security administration plan. |
| Physical access controls || If you employ Windows Encrypting File System, an attacker can boot from alternate media and cause you to lose data. If the attacker can boot and reset passwords, users will be unable to decrypt data that was encrypted before the password reset. Physical access controls will protect you from this type of attack. |
| Anti-malware protection || Malware can substantially modify or delete data. Successful attacks can render all or part of your data unavailable for use. |
| Operating system and application software updates || Many attacks target known operating system and software vulnerabilities. Apply all available software patches to remove as many vulnerabilities as possible. |
|   ||   |

Confidentiality extends the scope of protecting data to ensure that no unauthorized user can view data. Many operating systems and applications use encryption as a primary confidentiality control. Encrypting data and then providing decryption keys only to authorized users enforces confidentiality for data either at rest or in transit. [Table 10-2](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10tab2) lists some controls that help maintain data confidentiality.

| **TABLE 10-3** Security controls that protect data integrity. |
| **CONTROL** || **DESCRIPTION** |
| Password policies || Documented password policies serve as a basis for user training. Password settings in Group Policy make it easy to enforce password policies across your entire Windows environment. |
| Object DACLs || Each object DACL defines specific access permissions for users. Since Windows stores DACLs in AD, the settings can be globally administered and deployed (within an AD domain or forest). DACLs protect integrity by restricting permissions to write or modify object data to authorized users. |
| Active Directory (AD) || Active Directory provides a central repository for security policy settings along with the ability to easily deploy settings to many target locations. AD is an important part of an effective security administration plan. |
| Physical access controls || Persistent attackers can defeat the best access controls. One tactic is to boot a computer from alternate boot media and load a different operating system. The attacker can then use tools to directly access files and folders without going through Windows and its controls. Since an attacker needs to physically access a computer to insert alternate boot media, physical access controls can limit an attacker’s ability to carry out such attacks. |
| Message/file authentication || You can use a message digest to detect unauthorized modifications to messages or files. A message digest is a shortened unique string of digits that represent a file or message. You can use one of several popular hashing algorithms to create a message digest. The recipient uses the same hashing algorithm to create a message digest of the received message. If the two digests are identical, the message has not been modified. |
| Anti-malware protection || Malware can substantially modify or delete data. Successful attacks can render all or part of your data unavailable for use. |
| Operating system and application software updates || Many attacks target known operating system and software vulnerabilities. Apply all available software patches to remove as many vulnerabilities as possible. |
|   ||   |

Maintaining Integrity

Protecting integrity is crucial to maintaining trust in your data’s accuracy. Your main goal is to ensure no unauthorized user can change data. Changing data includes modifying or deleting data. The majority of the controls you’ll deploy to protect integrity focus on user identification, authentication, and authorization. Windows provides you with the tools to positively identify a unique user and determine what that user can do. The three main types of integrity concerns include:

• **User identification**—The first step in granting or denying actions is to identify the user attempting an action. Users are identified in Windows through a user account. Organizations using Active Directory can define users. Active Directory uses the same account when accessing different resources, avoiding a logon each time.

• **User authentication**—Authentication is proving to Windows that you are who you say you are. The most common type of authentication is providing a password when you log on. You can choose to use other methods with, or instead of, passwords. You can make it harder for attackers to log on using someone else’s user account by requiring a security token, smart card, or even a biometric input. You can use any method that provides assurance that a user is authentic.

• **User authorization**—Once you know who a user is, you can determine what that user can do. Windows grants rights to users that dictate what they can do. You can also define DACLs for individual objects to allow or deny users, or groups of users, different types of access to the object. Active Directory and Group Policy Objects (GPOs) make this process manageable across a network of any size.

When considering the integrity property of data security, make sure to deploy controls addressing each of the areas of concern listed below. [Table 10-3](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10tab3) lists some controls that help maintain data integrity.

Maintaining Availability

Availability can often be the trickiest of the three security properties to protect. The unforeseen issues must be uncovered to establish the best controls. Ensuring data availability requires controls that address both daily operation and unusual situations. Four main types of concerns affect data availability. All four types of issues must be addressed to ensure that data is available when it is needed. The four main types of availability concerns are as follows:

• **Attacks**—Denial of service (DoS) and distributed denial of service (DDoS) attacks specifically target your network’s ability to access data. If the network or server is too busy to service authorized users’ requests, your data is not available. Other types of attacks move, modify, or destroy data and can affect availability.

• **Performance**—All computing environments tend to suffer performance loss over time. Increased resource load, fragmented disks, out-of-date configuration settings, and malware are examples of why computers get slower. Monitor system and network performance and fix any performance problems. This ensures that your environment does not become slow. Slow environments limit access to data that users need to do their jobs.

• **Interruptions or disasters**—Short-duration interruptions, such as a power outage or a network service interruption, can prevent your users from accessing data. Disasters, such as fires or floods, can cause data loss and interruptions lasting longer than minutes or hours. You need to plan for both types of availability problems.

• **Other security controls**—Controls protecting data integrity or confidentiality can violate availability. For example, you can choose to disable access to your database for all users outside your organization’s local area network (LAN). This control can help protect the data’s integrity and confidentiality. However, it makes your data unavailable to users in remote locations. Always search for controls that balance all three security properties. The best way to uncover the side effects of controls is to check each one thoroughly in a test environment. Ensure that new or changed controls allow users to do their jobs.

| **TABLE 10-4** Security controls that protect data availability. |
| **CONTROL** || **DESCRIPTION** |
| Firewall, **intrusion detection system (IDS), intrusion prevention system (IPS)** || A firewall can block traffic that matches specific rules. In many cases, firewall rules are based on IP address and port numbers. An IDS can analyze traffic and detect a potential intrusion based on traffic patterns. An IPS can not only detect an intrusion, but also change firewall rules in real time to prevent further damage from an attack. |
| System and network performance monitors || Windows 7, Windows 8, Windows Server 2008 R2, and Windows Server 2012 include the Windows Performance Monitor (PerfMon) toolset. PerfMon provides a rich collection of monitors, alerts, logging options, and reports to create baselines and real-time samples of your Windows systems’ performance. Several third-party vendors also provide tools to make it easy to monitor network traffic and recognize problems. |
| Backup and recovery plan || Use the Windows backup utilities to create frequent backups and know how they fit into your complete business continuity plan (BCP) and disaster recovery plan (DRP). |
| Security control testing || Test all new controls and changes to existing controls before deploying them to a live environment. More restrictive controls may limit availability as they increase integrity and confidentiality protection. Virtual machines are useful when testing any configuration and software changes. |
| Anti-malware protection || Malware can substantially modify or delete data. Successful attacks can render all or part of your data unavailable for use. Controlling this type of threat overlaps with protecting data integrity. |
|   ||   |

When you consider the availability property of data security, be sure to deploy controls that address each of the four areas of concern in the preceding list. The goal is to ensure your data is always available to authorized users when needed, and never available to unauthorized users. [Table 10-4](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10tab4) lists some controls that help maintain data availability.

Consider the controls you’ll need to ensure authorized users can access data, regardless of any other influences. Other controls, interruptions, disasters, and attacks can reduce users’ ability to access data. Your job is to ensure the data is available.

**Microsoft Windows OS Security Administration**

Once controls are planned to maximize the C-I-A triad properties, you can implement them. The steps to implement each control depend upon the type and goal. Security administrators most commonly implement technical controls. Personnel from other departments typically implement administrative and physical controls. You implement most technical controls by installing software, updating software, or modifying settings. In this section, you’ll learn about the most common tools security administrators use to create objects and change security settings.

Firewall Administration

You can maintain Windows Firewall settings for Windows 7 and Windows Server 2008 in the Windows Firewall with Advanced Security MMC snap-in. This new utility combines Windows Firewall settings with Internet Protocol Security (IPSec) settings. You can manage both groups of settings using a single utility.

**FYI**

Microsoft provides a wealth of information on how to secure its operating systems. For more information on how to secure Windows Server 2008 R2, visit *[http://technet.microsoft.com/en-us/library/dd548350(v=ws.10).aspx](http://technet.microsoft.com/en-us/library/dd548350\(v=ws.10\).aspx)*. For more information on how to secure Windows Server 2012, visit *[http://technet.microsoft.com/en-us/library/jj730960.aspx](http://technet.microsoft.com/en-us/library/jj730960.aspx)*.

**technical TIP**

You can open the Windows Firewall with Advanced Security MMC snap-in using these steps for Windows 7 and Windows Server 2008 R2:

**1.** Choose the Windows Start button > Administrative Tools.

**2.** Select Windows Firewall with Advanced Security.

[Figure 10-2](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig2) shows the Windows Firewall with Advanced Security MMC snap-in.

The Windows Firewall with Advanced Security snap-in allows you to maintain four main types of information:

• **Inbound rules**—Rules to filter inbound network traffic using program, port, predefined, or custom criteria.

• **Outbound rules**—Rules to filter outbound network traffic. The available criteria are the same as for inbound rules.

• **Connection security rules**—IPSec rules for establishing connections between computers.

• **Monitoring**—Access to firewall performance information for firewall rule analysis.

**FIGURE 10-2** Windows Firewall with Advanced Security MMC snap-in.

![image](OEBPS/Images/9781284031652_pg228.jpg)

**FIGURE 10-3** Windows Performance Monitor.

![image](OEBPS/Images/9781284031652_pg229.jpg)

Performance Monitor

The Windows Performance Monitor enables you to view real-time performance data or data from a log file. The Performance Monitor can identify potential problems threatening data availability. Data Collector Sets can configure and collect performance data based on specifications for analysis and reporting. You can view detailed information about hardware resources and system resources that the operating system and running programs use. You can also start and stop services, stop processes, and analyze process locking activity.

[Figure 10-3](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig3) shows the Windows Performance Monitor.

**technical TIP**

You can open the Windows Performance Monitor using these steps for Windows 7 and Windows Server 2008 R2:

**1.** Choose the Windows Start button > Administrative Tools.

**2.** Select Performance Monitor.

Backup Administration

A valid backup is a crucial part of an organization’s ability to recover from losing data. One of the most visible recurring tasks you will have as a security administrator is to create frequent backups of your organization’s data. You can use either Microsoft backup utilities or third-party programs. Either way, you should frequently create fresh backup copies of the data your organization cannot afford to lose.

Windows Workstation Backups

Microsoft has included an updated Backup and Restore utility starting with Windows 7. The utility has been upgraded from its Vista predecessor to make backing up and restoring Windows workstations simple. The Windows Backup and Restore Wizard asks you to provide answers to three main questions to initially configure your backup scope and schedule. [Figure 10-4](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig4) shows the Windows Backup and Restore utility in action.

**FIGURE 10-4** Windows Backup and Restore for Windows 7.

![image](OEBPS/Images/9781284031652_pg230.jpg)

**technical TIP**

Open the Windows Backup and Restore utility on a computer running Windows 7 using these steps:

**1.** Choose the Windows Start button > Control Panel.

**2.** Select System and Security > Backup and Restore.

**FIGURE 10-5** Windows Server 2008 Backup.

![image](OEBPS/Images/9781284031652_pg231.jpg)

**technical TIP**

Open the Windows Server Backup utility on a computer running Windows Server 2008 using these steps:

**1.** Choose the Windows Start button > Administrative Tools > Windows Server Backup.

**2.** Select the Backup Schedule link to launch the Backup Schedule Wizard. This allows you to configure a scheduled backup.

a. You can also select the Backup Once link to launch the Backup Once Wizard to configure a one-time backup.

Windows Server Backups

The Microsoft Windows Server Backup utility must be installed on Windows Server 2008 R2 and Windows Server 2012. Once installed, you can use it to schedule and create backups for your servers. Since Windows servers perform different functions, they often have different backup needs. The Microsoft Windows Server Backup utility addresses the many different server backup needs ([Figure 10-5](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig5)). It may take a little more effort to configure than a simple workstation backup. The basic steps are similar to setting up a workstation backup—you just have more options available to you.

Operating System Service Pack Administration

Microsoft provides the Microsoft Baseline Security Analyzer (MBSA) utility. This utility evaluates computers in accord with Microsoft security recommendations. MBSA checks to ensure the operating system and current Microsoft software are up to date. The latest version of MBSA, version 2.2, supports Windows Server 2008 R2, Windows Server 2012, Windows 7, and Windows 8, as well as several previous Windows versions. Download and install MBSA to automate the process of identifying out-of-date workstation and server software.

**technical TIP**

Follow these steps for Windows 7 and Windows Server 2008 R2 to use the MBSA graphical user interface (GUI) ([Figure 10-6](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig6)) to scan your computer for vulnerabilities:

**1.** Open MBSA. Choose the Windows Start button > Microsoft Baseline Security Analyzer.

**2.** Select the desired operation mode:

a. Select Scan A Computer to scan a single computer.

b. Select Scan Multiple Computers to scan more than one computer in a single session.

c. Select View Existing Security Scan Reports to view the results of previous scans.

**3.** If you choose to scan one or more computers, enter the computer/domain name or IP address(es):

a. For single computer scans, enter either a computer name or an IP address.

b. For multiple computer scans, enter a domain name or a range of IP addresses.

**4.** Select the check boxes next to the desired scanning options. In many cases, leaving all options checked provides the most extensive analysis.

**5.** Choose Start Scan to begin the scanning process.

**6.** Whether you selected the scan option or selected an existing security scan report, MBSA presents the scan results in a user-friendly report. Each report issue includes a description of what was scanned, details of the result, and in many cases, descriptive information on how to resolve the issue.

**7.** Choose OK to close the report viewer and return to the MBSA main window.

**FIGURE 10-6** MBSA GUI.

![image](OEBPS/Images/9781284031652_pg233.jpg)

Group Policy Administration

You can define GPOs at the local level or in AD. Defining GPOs in AD gives you the ability to centralize security rules and control how Windows applies each rule. You create AD GPOs on a domain controller, and Windows automatically replicates the GPOs to other domain controllers. This feature reduces the workload of administrators. Using Group Policy in AD relieves the need to define security rules on multiple computers one at a time.

AD GPOs are created on the domain controller using the Group Policy Management Console (GPMC) ([Figure 10-7](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig7)). Although there are multiple ways to create GPOs, the most common method is to create GPOs under the desired domain in the GPMC. Once a new AD GPO is created, link it with an entity to activate it.

**FIGURE 10-7** Group Policy Management Console.

![image](OEBPS/Images/9781284031652_pg234.jpg)

**technical TIP**

Follow these steps to open the GPMC on a Windows Server 2008 R2 domain controller:

**1.** Choose the Windows Start button.

**2.** Select All Programs > Administrative Tools > Group Policy Management.

Follow these steps to open the GPMC:

**1.** Choose the Windows Start button.

**2.** Type gpmc.msc in the Run box.

**3.** Press the Enter key.

**technical TIP**

Here’s how to display and edit any object’s DACL:

First, open the object’s Properties dialog box. Use any one of these procedures:

**1.** Right-click the object, and then select Properties.

**2.** Select the object, press SHIFT+F10, and then select Properties.

**3.** Hold the ALT key and double-click the object.

In the Properties dialog box, select the Security tab.

DACL Administration

Windows uses an object’s discretionary access control list (DACL) to determine if it should grant access a subject has requested. Any object you want to protect must have a DACL for Windows to control access to the object. Objects without a DACL defined are accessible by any subject—any process, any user. An object’s DACL is a collection of individual ACLs and can be modified in the object’s Properties dialog box ([Figure 10-8](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig8)).

**FIGURE 10-8** Object Properties Security dialog box.

![image](OEBPS/Images/9781284031652_pg235.jpg)

**FIGURE 10-9** DACL advanced security settings.

![image](OEBPS/Images/9781284031652_pg236.jpg)

The Security page of the object Properties dialog box allows you to view and modify the security permissions for the selected object. On the Security page, the Group or User Names area lists the users and groups for which each access control entry (ACE) is defined. Recall that each entry in an ACL is an ACE. The Permissions for Users area shows the current permissions for the selected user or group.

The Advanced page provides access to individual object permissions, as opposed to predefined groups of permissions in the general Security page ([Figure 10-9](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig9)). The Advanced page lists each individual permission for the selected user or group.

Encryption Administration

Windows supports three main methods to encrypt stored data: Encrypting File System (EFS), BitLocker, and BitLocker To Go. Other methods are available within applications. Additional solutions are available from other vendors. Consider your encryption needs and evaluate each method based on its specific capabilities. The best choice of encryption methods is the one that best meets your needs. If you choose one of the default Windows encryption methods, all you have to do is enable your selected encryption option.

Enabling EFS

You enable EFS for objects using the object’s Properties dialog box. Open Windows Explorer and navigate to the file or folder. To encrypt the object, open the context menu by right-clicking the object, and then select Properties. From the Properties dialog box, choose the Advanced button. In the Advanced Attributes dialog box, select the Encrypt Contents To Secure Data check box, choose OK, then choose OK again to close the Properties dialog box. The object is now stored as an encrypted object. No further action from the user is necessary. [Figure 10-10](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig10) shows the Properties and Advanced Attributes dialog boxes.

Enabling BitLocker or BitLocker To Go

Enabling BitLocker or BitLocker To Go is just as easy as EFS. The main difference between the two is that BitLocker To Go encrypts removable media. To enable either BitLocker version, open Windows Explorer and navigate to Computer. Open the context menu of the selected volume by right-clicking on the desired volume, and select Turn On BitLocker or Turn On BitLocker To Go. [Figure 10-11](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig11) shows the BitLocker option on the object’s context menu.

**FIGURE 10-10** Object properties—advanced attributes.

![image](OEBPS/Images/9781284031652_pg237.jpg)

Alternatively, you can launch the BitLocker management tool to view and manage BitLocker for all volumes. Open the Windows Control Panel, select System and Security, and select BitLocker Drive Encryption. The BitLocker management tool displays all volumes, along with an option to turn BitLocker on or off for each volume. [Figure 10-12](#20_Chaper10_split_001.xhtml#ba-9781284031652-ch10fig12) shows the Bitlocker management tool.

After enabling BitLocker, Windows asks you to pick an authentication method and to determine where to save a recovery key. Once you provide the required information, Windows handles the rest and encrypts your data when you store it on the disk.

**FIGURE 10-11** Enabling BitLocker.

![image](OEBPS/Images/9781284031652_pg238.jpg)

**FIGURE 10-12** BitLocker management tool.

![image](OEBPS/Images/9781284031652_pg239.jpg)

Anti-Malware Software Administration

The key to keeping computers malware free is to identify all known malware on each computer, remove it, and diligently keep the computers from getting infected with new malware. The most important step in the process is making the commitment to pursue a malware-free environment. There are many anti-malware software options and your specific scan, update, and removal procedures will depend on your software.

The key steps in staying malware free are:

• Require antivirus and anti-spyware software for every computer before you allow it to connect to your network.

• Ensure that all anti-malware software is current and all data is up to date.

• Scan each computer at least weekly to search for malware.

• Ensure anti-malware shield software runs on every computer that connects to your network.

**Ensuring Due Diligence and Regulatory Compliance**

**Compliance** is more than just checking items off a list. It is a dynamic process. It ensures the items in each domain of your IT infrastructure meet or exceed your security goals. This should include all legal, regulatory, and standard requirements. Conditions change in any organization. The status of how well you are meeting your goals can change as well. Make all decisions related to security controls to satisfy your security policy. Be sure to meet any other relevant compliance requirements. For example, the Health Insurance Portability and Accountability Act (HIPAA) and Health Information Technology for Economic and Clinical Health Act (HITECH) place requirements on handling health and medical information. The Gramm-Leach-Bliley Act (GLBA) and Sarbanes-Oxley Act (SOX) place requirements on financial information. Many states place additional requirements on personally identifiable information. Ensuring compliance to your security policy keeps security-related actions headed in the right direction.

It is important to implement compliance requirements to minimize the impact on **business drivers**. Business drivers are the components (including people), information, and conditions that support business objectives. Any negative impact on business drivers may have a negative impact on your organization’s ability to satisfy business objectives. Carefully research the impact to business drivers before you implement any compliance controls.

Remember that compliance requirements dictate how your organization conducts its activities. Whether the compliance requirement comes from legislation, regulation, industry requirements, or even your organization’s standards, the result is the focus. In most cases, there are multiple ways your organization can control activities to ensure compliance. Always consider alternative controls to achieve the end result compliance requires. You’ll likely find that some controls are less costly and less intrusive than others. Don’t just accept the first control that does the job. Many times, alternate controls are just as good but intrude less on your organization’s activities.

Due Diligence

Paying attention to compliance can reduce liability in direct and indirect ways. You can think of it in terms of additional insurance. In the context of information security, the term **due diligence** means the ongoing attention and care an organization places on security and compliance. You can reduce your exposure to third-party liability by investing resources into establishing and maintaining compliance. Demonstrating aggressive compliance activities can reduce the liability potential if security incidents result in damages. In short, being compliant looks good in court.

You can follow the Plan-Do-Check-Act cycle to demonstrate due diligence. PDCA directs your activities to continuously evaluate your security position and make any changes necessary to better meet your security policy. As long as your policy contains all necessary compliance requirements, documenting your PDCA activities will provide substantial evidence of due diligence.

**The Need for Security Policies, Standards, Procedures, and Guidelines**

Security doesn’t just happen. It’s not a single event. Security, or more precisely, the pursuit of security, is an ongoing process. As Bruce Schneier, internationally renowned security technologist said, “Security is a process, not a product.” It is a process of continually working to reach your organization’s security goals. Every organization is different and security goals likewise differ among organizations. The process of reaching security goals is a continual process that requires specific direction.

Any organization’s success at satisfying security goals depends on three main elements. A weakness in any of the three elements makes it more difficult to comply with your organization’s security requirements. These three elements include:

• **Clearly stated security goals**—You must have a clear security goals document that the organization’s upper management fully endorses. A lack of clear goals means you don’t really know what you’re trying to do, how you’re doing it, and when you’re done. A lack of upper management support means you’ll likely encounter resistance when you try to implement any new controls. In fact, trying to fulfill the responsibilities of a security practitioner in an organization without upper management’s support is difficult at best.

• **Documented plans**—A plan is a series of steps designed to achieve a goal. You should have a plan for each security goal. Each plan may have additional guidance documents that provide more details to meet security goals.

• **Communication with stakeholders**—A stakeholder is anyone who has an interest in, or is affected by, some activity. Documented plans are worthless if no one who is doing security work knows about them. A common point of failure in security administration is a lack of direction. In many cases, a lack of direction comes from just not knowing what plans have already been made.

An organization that desires to implement solid security in the IT infrastructure should commit to fulfill each of the three elements of security. Follow the list in order. Start with stating security goals that are appropriate for the organization’s culture and compliance requirements. Next, develop any additional guidance documents. A solid security plan will include several types of guidance documents. Good security training should stress the importance of compliance and cover the important parts of these guidance documents:

• **Security policy**—A high-level statement that defines an organization’s commitment to security and the definition of a secure system, such as the importance of changing passwords periodically

• **Security standard**—A collection of requirements the users must meet, typically within a specific system or environment, such as changing a Windows password every six months

• **Security procedure**—Individual tasks users accomplish to comply with one or more security standards, such as the steps to change a password

• **Security guidelines**—A collection of best practices or suggestions that helps users comply with procedures and standards, such as suggestions on how to create strong passwords

Clearly stated goals, complete plans and guidance documents, and a strong commitment to training and communication can dramatically increase the success rate of meeting your security goals. Following these steps will put you well on your way to a secure environment.

**Best Practices for Microsoft Windows OS Security Administration**

Effective Windows security administration ensures your organization has all the technical controls in place to support its security goals. It takes more than just technical controls to meet all security goals, but security administrators mainly focus on deploying and maintaining technical security controls.

Here is a list of Windows security administration best practices that will help you deploy and maintain the controls to support your security policy. Change the list to suit your organization, but pay attention to the suggestions—they can help you avoid wasting time and resources:

• Clearly state security goals in your security policy.

• Include all compliance requirements for applicable legislation, regulation, and vendor standards in your security policy.

• Use the PDCA method for all security administration activities.

• Communicate with all stakeholders—share as much information as possible.

• Strive for simplicity in all controls and systems—complexity invites failures.

• Search for controls that have little impact on users. Users tend to bypass controls that they find intrusive or difficult.

• Coordinate AUPs with technical controls.

• Automate as much as possible—use scheduled jobs whenever possible.

• Use AD GPOs for as many security settings as possible.

• Coordinate physical controls with technical controls.

• Never allow a computer that doesn’t have current anti-malware controls in place to connect to your network. This rule applies to all computers—even laptops owned by distinguished guests. Enforce the rule or be prepared to put your malware removal plan into action.

• Develop a plan to monitor system and network performance and follow it.

• Ensure the operating system and all software is up to date for all computers.

• Periodically examine log files for suspicious behavior.

• Stay current on emerging attacks and trends and update your controls appropriately.

• Fully test your recovery plans at least annually, or more often if possible. You’ll never really know how your recovery plan works until you actually execute each of the steps.

• Define DACLs when necessary and modify or remove them when user account roles change.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Windows security administration is as much a business process as a security endeavor. While getting the right technical controls in place is the ultimate goal for the security administrator, it is only one part of the process. Substantial analysis and planning precedes deploying any control. After deployment, you should conduct an ongoing effort to ensure that the right controls are in place and working well. Implementing the quality concept of continuous improvement can make you more effective as a security administrator. Take the time to learn and implement the PDCA method in your security activities. It will be well worth the investment and will make your organization’s environment more secure.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Business driver**

**Compliance**

**Deming cycle**

**Due diligence**

**Intrusion detection system (IDS)**

**Intrusion prevention system (IPS)**

**Message digest**

**Plan-Do-Check-Act (PDCA)**

**Security administration**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 10 ASSESSMENT**

  **1.** Security administration is the process of developing an organization’s security policy.

A. True

B. False

  **2.** What is the most important feature of PDCA?

A. PDCA was developed for security administration.

B. PDCA is a Microsoft standard.

C. PDCA repeats and does not end.

D. PDCA was developed by Dr. Deming.

  **3.** Which of the following activities would a security administrator be *least* likely to do?

A. Monitor log files.

B. Deliver AUP training.

C. Keep software up to date.

D. Enforce physical security controls.

  **4.** If time to recover exceeds the recovery goal, which property of security have you violated?

A. Availability

B. Integrity

C. Confidentiality

D. Consistency

  **5.** Which of the following devices or software programs can detect intrusions? (Select two.)

A. Firewall

B. IDS

C. IPS

D. NAT

  **6.** A valid backup is an integral part of your \_\_\_\_\_\_\_\_ and \_\_\_\_\_\_\_\_.

  **7.** Protecting both integrity and confidentiality depends largely on knowing a user’s identity.

A. True

B. False

  **8.** A DACL is used primarily to enforce which security properties? (Select two.)

A. Integrity

B. Consistency

C. Confidentiality

D. Availability

  **9.** You can use the \_\_\_\_\_\_\_\_ tool to ensure your Microsoft operating system is up to date and has all patches and service packs installed.

**10.** Active Directory requires that you create multiple GPOs, one for each computer.

A. True

B. False

**11.** Which of the following terms is best described as a collection of requirements users must meet, typically within a specific system or environment?

A. Security policy

B. Security standard

C. Security procedure

D. Security guideline

**12.** Which type of Windows component would you use to define which users can create files in a folder?

A. DACL

B. NAT

C. User right

D. IPSec rule

**13.** Which tool would you use to edit the setting that disables user-installed desktop gadgets for all users?

A. Local Group Policy Editor

B. MBSA

C. GPMC

D. Performance Monitor

**14.** Microsoft provides a command-line utility for creating backups on Windows server and workstation operating systems.

A. True

B. False

**PART THREE**

**Microsoft Windows OS and Application Security Trends and Directions**

 
| [**CHAPTER 11**](#22_Chaper11_split_000.xhtml) || [**Hardening the Microsoft Windows Operating System**](#22_Chaper11_split_000.xhtml) |
| --- | --- |
| [**CHAPTER 12**](#23_Chaper12_split_000.xhtml) || [**Microsoft Application Security**](#23_Chaper12_split_000.xhtml) |
| [**CHAPTER 13**](#24_Chaper13_split_000.xhtml) || [**Microsoft Windows Incident Handling and Management**](#24_Chaper13_split_000.xhtml) |
| [**CHAPTER 14**](#25_Chaper14_split_000.xhtml) || [**Microsoft Windows and the Security Life Cycle**](#25_Chaper14_split_000.xhtml) |
| [**CHAPTER 15**](#26_Chaper15_split_000.xhtml) || [**Best Practices for Microsoft Windows and Application Security**](#26_Chaper15_split_000.xhtml) |

**CHAPTER 11**

**Hardening the Microsoft Windows Operating System**

IN THIS CHAPTER, you’ll learn how to apply what you’ve studied to make a computer running a Microsoft Windows operating system more secure. You’ll find out where you should focus your efforts for the most effective use of resources. You’ll also learn how to ensure each computer is as secure as possible. You’ll read as well how important a documented and repeatable process is when making computers more secure.

**Chapter 11 Topics**

This chapter covers the following topics and concepts:

• What the hardening process and mindset are

• How to harden Microsoft Windows operating system authentication

• How to harden the network infrastructure

• How to secure directory information and operations

• How to harden Microsoft Windows operating system administration

• How to harden Microsoft servers and client computers

• How to harden data access and controls

• How to harden communications and remote access

• How to harden public key infrastructure (PKI)

• What user security training and awareness is

• What the best practices are for hardening Microsoft Windows operating system and applications

**Chapter 11 Goals**

When you complete this chapter, you will be able to:

• Describe the Windows operating system hardening process

• Harden all aspects of Windows computers and network environments

• Provide security training and awareness

**Understanding the Hardening Process and Mindset**

Software vendors of all types, including operating system vendors, encounter a basic dilemma when deciding on default installation options. One school of thought is to install the most features possible to showcase what the product can do. This approach is the one that vendors generally select because it promotes the richness of their product’s features. The other approach is to only install the bare minimum of features to avoid increasing the product’s vulnerability to attack. Many vendors, however, end up showcasing more features. This raises the risk of making their product more vulnerable. The software a computer runs that is vulnerable to attack is called the attack surface. The primary goal in securing Windows computers is to reduce the attack surface. While you can’t ever reduce the risk of attack to zero, you can employ controls to make your computers more secure.

Strategies to Secure Windows Computers

You have two main strategies to choose from to reduce a computer’s attack surface. First, disable or remove programs that contain vulnerabilities. This strategy is the most secure method. For example, suppose you are concerned about vulnerabilities in the Microsoft Internet Information Services (IIS) Web server. This Web server is running on your computer and is named WebServ01. You could disable IIS on WebServ01, or remove it entirely. An attacker can’t compromise a program that isn’t present or running on a computer. Unfortunately, WebServ01 is an important service for your organization. It is a Web server for your e-commerce application. Since you can’t disable or remove IIS, you’ll have to use another strategy.

The second main strategy to reduce the attack surface is to establish controls on running programs to mitigate any known vulnerabilities. This method is always more difficult and less complete. It is also more time consuming than just disabling unneeded programs or services. Despite this, it is necessary when running a program that contains vulnerabilities.

In this chapter, you’ll learn the steps to reduce the operating system attack surface of your computers. The process of making configuration changes and deploying controls to reduce the attack surface is called **hardening**.

Hardening Windows computers is not a single activity—it is an ongoing process. When installing Windows, choose the installation options for programs and services you absolutely need. Then, harden each computer as soon as you complete the installation process.

**technical TIP**

Always consider disabling or removing programs or services that you don’t really need. You shouldn’t install programs if you don’t need them. You’ll find that if you disable or remove unneeded components, the hardening process is easier. You end up with a more secure computer. Always explore which programs or services you actually need before researching controls.

 
| **TABLE 11-1** Windows Server 2008 R2 standard installation roles and editions. |
| --- |
| ![image](OEBPS/Images/9781284031652_pg250.jpg) |

Install Only What You Need

The Windows 7 and Windows 8 installation procedures follow a standard process. You can’t easily change which programs the process installs. If you are installing Windows 7 or Windows 8, you’ll have to complete the install process and then remove any unwanted components. When you install a Windows Server 2008 R2 or Windows Server 2012 operating system, you have the ability to select which programs to install. The easiest way to customize a server is to define one or more **roles** for the computer. A role is a predefined set of services, programs, and configuration settings that enables a computer to fulfill specific requirements. The available roles depend on the edition of Windows you are installing. Microsoft offers multiple editions of each of its server operating systems. Each edition can support different types of roles.

Windows Server 2008 R2 Editions and Roles

Recall that Microsoft offers the following editions of Windows Server 2008 R2:

• **Foundation**—Cost-effective, entry-level server for small businesses

• **Standard**—Supports more features than Foundation edition for medium-sized businesses

• **Enterprise**—Advanced server for more performance and reliability than Standard edition

• **Datacenter**—Optimized for large-scale deployment using virtualization on small and large servers

• **Web**—Optimized Web application and services platform

• **HPC**—Windows High Performance Computing server for extensive scalability and interoperability between servers

• **Itanium**—Windows server specifically designed for the Intel Itanium high-performance processor

[Table 11-1](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11tab1) lists the 17 Windows Server 2008 R2 roles and which editions support each role.

![image](OEBPS/Images/war.jpg)**WARNING**

Before installing Windows Server 2008 R2 or Windows Server 2012, ensure you have the correct edition to support the roles you’ll need. For more information on the limitations on role support for each edition, go to *[http://technet.microsoft.com/en-us/windowsserver/bb310558.aspx](http://technet.microsoft.com/en-us/windowsserver/bb310558.aspx)*, or *[http://www.microsoft.com/en-us/download/details.aspx?id=38809](http://www.microsoft.com/en-us/download/details.aspx?id=38809)* for Windows Server 2012.

Microsoft provides a new installation option making it easier to exclude programs you don’t need. The **server core installation** option provides a minimal Windows Server 2008 R2 environment that includes only programs necessary for the roles you select. A server core installation doesn’t even include a Windows graphical user interface (GUI). You use a command-line interface to interact with the operating system. Since Microsoft limits the programs a server core installation installs, your choice of roles is limited. [Table 11-2](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11tab2) lists the roles from which you can choose for a server core installation of Windows Server 2008 R2.

Taking the time to select the right role for each Windows Server 2008 R2 installation is the first step in hardening your Windows servers.

 
| **TABLE 11-2** Windows Server 2008 R2 core installation roles and editions. |
| --- |
| ![image](OEBPS/Images/9781284031652_pg252.jpg) |

Windows Server 2012 Editions and Roles

Recall that Microsoft offers the following editions of Windows Server 2012:

• **Foundation**—Cost-effective, entry-level server for small businesses

• **Essentials**—With more features than Foundation for most small to medium-sized businesses

• **Standard**—Suitable for most server functions, along with limited virtualization ability

• **Datacenter**—Designed for large-scale deployment on servers that support extensive virtualization

[Table 11-3](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11tab3) lists the 19 Windows Server 2012 roles and which editions support each role.

 
| **TABLE 11-3** Windows Server 2012 standard installation roles and editions. |
| --- |
| ![image](OEBPS/Images/9781284031652_pg253.jpg) |

Windows Server 2012 supports server core installations as well. In fact, starting with Windows Server 2012, you can switch between a full server and server core installation without having to reinstall the entire operating system. Windows Server 2012 offers a single server core installation. Here are the roles a Windows Server 2012 server core supports:

• Active Directory (AD)

• Active Directory Lightweight Directory Services (AD LDS)

• DHCP Server

• DNS Server

• File Services

• Hyper-V

• Print Services

• Streaming Media Services

• Web Server (IIS)

• Active Directory Certificate Services

Security Configuration Wizard

Microsoft provides a tool with Windows Server 2008 R2 and Windows Server 2012 that helps further reduce the attack surface of servers. The **Security Configuration Wizard (SCW)** provides guidance to administrators. It also creates policies based on the least privilege principle for the server roles you’ve selected. The policies the SCW creates help control services that run, authentication methods between computers, Registry settings, audit policy settings, and firewall settings for your server computers.

[Figure 11-1](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig1) shows the Security Configuration Wizard’s Configuration Action window.

The SCW allows you to create, edit, apply, or roll back policies. It provides you with one place to manage many security settings. This utility helps you harden several servers without manually modifying many security settings. If you have several servers that you want to configure to operate the same as one or more other servers, use the SCW to create a baseline policy and then apply that policy to the other servers. Once you select the server on which this policy is based, you can either view the current configuration or continue to the next wizard windows to enter policy information.

**technical TIP**

You can open the SCW on a computer running Windows Server 2008 R2 using these steps:

**1.** Choose the Windows Start button > Administrative Tools.

**2.** Select Security Configuration Wizard.

**FIGURE 11-1** Windows Security Configuration Wizard—Configuration Action.

![image](OEBPS/Images/9781284031652_pg255.jpg)

In each configuration, the wizard window displays the current computer configuration for new policies or the current policy setting for existing policies. Here’s a list of the SCW configuration settings windows and the information you can enter in each one:

• **Select Server Roles**—Select or deselect the roles you want to define for this policy.

• **Select Client Features**—Select the specific client services for the policy, since servers may also serve as clients for some services.

• **Select Administration and Other Options**—Select the additional options that apply to this policy.

• **Select Additional Services**—Select the additional services defined in the policy or on the computer that you want to keep.

• **Handling Unspecified Services**—Keep or disable any services not specified in the previous four windows.

• **Confirm Service Changes**—Review changes that SCW will make to the policy.

• **Network Security Rules**—Define, edit, or remove firewall rules for this policy.

• **Require SMB Security Signatures**—Set minimum requirements for access to computers using shared resources.

• **Require LDAP Signing**—Set minimum requirements for computers sending LDAP queries.

• **Outbound Authentication Methods**—Set the mode for outbound computer authentication.

**FIGURE 11-2** Windows Security Configuration Wizard—Select Server Roles.

![image](OEBPS/Images/9781284031652_pg256.jpg)

• **Outbound Authentication Using Domain Accounts**—Set minimum requirements for outbound authentication using domain accounts.

• **Registry Settings Summary**—Review Registry settings changes that SCW will make to the policy.

• **System Audit Policy**—Set the global audit level for activities.

• **Audit Policy Summary**—Review audit policy changes that SCW will make.

• **Save Security Policy**—Save the policy under a specified name and optionally apply the security policy.

[Figure 11-2](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig2) shows the Security Configuration Wizard’s Select Server Roles window.

Use the SCW after installing each Windows server to harden it for use in your secure environment.

Manually Disabling and Removing Programs and Services

Before proceeding, back up the Windows Registry. It is a good idea to back up the Windows Registry before making any changes. Some of the changes you make to Windows can cause unexpected results. A Windows Registry backup may help you research problems and restore settings. In addition, make changes on a test computer whenever possible. Making changes on test computers gives you the ability to test the results of those changes before they impact your production environment.

**technical TIP**

You can create a Windows Registry backup by following these steps:

**1.** Choose the Windows Start button > Run.

**2.** Type regedit.exe in the text box.

**3.** Select File > Export from the menu.

**4.** Enter the desired filename for the Registry backup and choose Save.

The next step is to evaluate each computer. Identify remaining programs and services that you don’t need. If you carefully select the roles for each server computer and then run the SCW, you shouldn’t have to remove or disable many programs. Since Windows 7 and Windows 8 do not provide the option to install the operating system based on roles or a tool like the SCW, you’ll likely find several programs and services you don’t need. For example, it is a good idea to disable the Remote Registry service. This service allows remote users to modify their Windows Registry. Once you identify any unneeded programs or services, either disable or remove them.

The most permanent and secure option is to remove unneeded programs. Make sure you know what a program is before you remove it. Don’t just remove a program because you don’t know what it is. If you don’t recognize a program, try searching for the program name using an Internet search. You’ll likely find information that will help you decide whether or not to remove the program. You can remove unneeded programs in the Control Panel. Removing a program makes it impossible for an attacker to use that program to compromise a computer. [Figure 11-3](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig3) shows the uninstall utility for Windows 7.

Many programs in the Windows operating system run as services. You’ll find many services running on servers as well as workstations. The Windows Services maintenance utility allows you to start, stop, and change the settings for services defined for a computer. An alternative to removing or uninstalling a program that runs as a service is to disable it. When a Windows computer boots, the operating system reads the list of services and starts the services with a Startup type value of Automatic. Windows will also start services with a Startup type value of Automatic (delayed start) as well once all of the Automatic services have started. You can change the Startup type to Disabled for any services you want to prevent Windows from starting. Although it is possible to manually start a service by running the program, disabling a service reduces the probability an attacker can use it to compromise a computer.

**FIGURE 11-3** Uninstalling a program in Windows.

![image](OEBPS/Images/9781284031652_pg258.jpg)

**technical TIP**

Open the Add/Remove Programs utility on a computer running Windows 7 or Windows Server 2008 R2 using these steps:

**1.** Choose the Windows Start button > Control Panel.

**2.** Select Uninstall a Program under the Programs link.

[Figure 11-4](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig4) shows the Windows Services Maintenance utility.

[Figure 11-5](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig5) shows the Windows Services Properties dialog box.

After you’ve identified unneeded programs and services and have either removed or disabled them, you can address remaining vulnerabilities. To continue the hardening process, learn about common vulnerabilities in running programs and deploy controls to secure your computers from those vulnerabilities.

**FIGURE 11-4** Windows Services.

![image](OEBPS/Images/9781284031652_pg259.jpg)

**technical TIP**

Launch and use the Windows Service Maintenance utility on a computer running Windows 7 or Windows Server 2008 R2 using these steps:

**1.** Choose the Windows Start button > Administrative Tools.

a. If the Administrative Tools option does not appear on the menu, select Control Panel > Administrative Tools.

**2.** Select Services.

**3.** To edit the properties of any service, select the service, open the context menu by right-clicking on the service, then select Properties.

**FIGURE 11-5** Windows Services Properties.

![image](OEBPS/Images/9781284031652_pg260.jpg)

**Hardening Microsoft Windows Operating System Authentication**

The next step in hardening your Windows operating systems is to address authentication weaknesses. If you ran the SCW on each server, you have already hardened the computer to computer authentication. The SCW allows you to require higher minimum operating system levels for inbound and outbound authentication. Later operating system versions are more secure and provide more features. If all of the computers in your environment are running the latest version of Windows, then disallow older authentication methods. For example, computers that run Windows 2000 or later support NTLMv2 authentication. Earlier versions of Windows only support the older NTLM protocol. If all your computers are running Windows 2000 or later, you can disable support for NTLM. The SCW allows you to change these security settings.

Remove or disable any unused or inactive user accounts defined for each computer, both locally and in Active Directory (AD). Unused user accounts provide additional targets for attackers. The most dangerous user for any Windows computer is Administrator. This user has elevated permissions and exists on every Windows computer. Attackers know that accessing the Administrator account allows them many ways to compromise a computer. Unfortunately, you can’t delete the Administrator account. But you can disable it. The best way to protect your administrative rights from attackers is to follow these steps:

**1.** Create new accounts that will become the new Administrator users.

**2.** Assign the necessary Administrator rights to the new users, or to a group object.

a. Test each of the new Administrator accounts to ensure they possess the necessary rights and permissions.

**3.** Disable the default Administrator account.

Following these steps will make it more difficult for attackers to escalate their privileges to include administrative rights. They have to guess which users now have administrative rights. Many automated attacks target the default Administrator user, so if you have disabled that user such attacks will fail. Once you have disabled the Administrator user, remove other users, such as Guest, that you do not need. As with the Administrator user, attackers know that many Windows operating systems have default users no one took the time to remove. They’ll try to use these accounts to compromise your computers.

The next step in hardening Windows authentication is to establish and enforce strong account policies. Create or edit Group Policy to modify settings for the following policies:

• **Password policy**—Settings for password age, length, complexity, storage, and history. The goal for passwords is to require users to change passwords frequently, but not too frequently. If you force users to change passwords too often and make them too complex, users will likely just write down passwords and keep them close to their workstations. A good rule of thumb is to set maximum password age to 60 days, enable password complexity, and require that passwords be at least eight characters in length. Users will have to change their passwords every 60 days and create passwords that contain upper- and lowercase characters as well as digits or special symbols.

• **Account policy**—Settings for account lockout duration, threshold, and reset count. Use these settings to make it more difficult for automated tools to use brute-force attacks to guess passwords. A good rule of thumb is to use an account lockout threshold of five to lock a user account after five failed logon attempts. You could set the duration and reset count to 15 to force a user to wait 15 minutes after five failed logons. After 15 minutes, the user could try to log on and have five more attempts before either successfully logging on or being locked out again.

• **Kerberos policy**—Settings for logon restrictions and ticket lifetimes. These settings tell Windows how long Kerberos tickets should be allowed to live and whether the Kerberos servers should authenticate users on every request. The default ticket lifetime is 10 hours. This default works well unless your environment routinely supports users who work for more than 10 hours at a time. The Kerberos lifetime should be a little longer than a user’s workday.

Ensuring you only have the accounts you need, both at the local computer level and in Active Directory, can reduce your exposure to attack. Reviewing, and if needed, strengthening the password policies will harden your Windows authentication and make it harder for attackers to compromise your Windows computers.

**Hardening the Network Infrastructure**

Once you’ve reduced the ability for unauthorized users to log on to your Windows computers, the next step is to harden other access methods. Computers communicate with other devices and computers on a network by sending messages to a destination port address. The combination of a protocol, a host name or address, and a port number identifies the intended target location for a message. For example, assume a Transport Control Protocol (TCP) message travels to *[www.myserver.com](http://www.myserver.com)* at port 80. Port 80 is the commonly used port for Web traffic. It is likely that there is a Web server on the server at the address *[www.myserver.com](http://www.myserver.com)*. If this server is a Web server, then you would want to accept TCP traffic on port 80. If you didn’t accept the traffic, your Web server would never receive any Web requests and essentially wouldn’t be able to do its job.

Identify all of the network server and client services that require access to ports. In the previous example, you know that the Web server needs port 80 to be open. If other services are running on the same computer, investigate which ports each service needs. Once you know what your computer needs to operate, modify your firewall settings to open those ports. Depending on which ports you need, you may find that they’re already open. Close all other ports. If a specific server computer does not run a Web server, it generally doesn’t need port 80 open. The SCW utility helps you define firewall rules that correspond to server roles and services required to support those roles. You can customize your firewall rules to fine-tune your network infrastructure security for Windows server computers. You’ll have to manually change firewall settings for Windows 7 or Windows 8 workstations.

**FIGURE 11-6** Windows Firewall with Advanced Security.

![image](OEBPS/Images/9781284031652_pg262.jpg)

**FIGURE 11-7** Group Policy Management Editor—Windows Firewall with Advanced Security.

![image](OEBPS/Images/9781284031652_pg263.jpg)

In previous versions of Windows, you would make firewall changes directly in the Windows Firewall maintenance utility. In Windows 7, Windows 8, Windows Server 2008 R2, and Windows Server 2012, you can maintain firewall rules in two different ways. One way is to use the Windows Firewall with the Advanced Security maintenance utility. Alternatively, you can use the Group Policy Management Editor to manage firewall settings. Using Group Policy to manage your firewall makes maintenance easier. Create one or more Group Policy Objects (GPO) for firewall settings in Active Directory and apply them to groups of computers without having to edit each one. [Figures 11-6](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig6) and [11-7](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig7) show the Windows Firewall with Advanced Security and editing firewall settings in the Group Policy Management Editor.

Regardless of the method you use to edit firewall settings, close all ports and disallow all connections except for those ports and applications you need. Fewer entry points to your computers make them more secure.

**Securing Directory Information and Operations**

Active Directory (AD) is a valuable feature of Microsoft Windows for IT operations. AD centralizes many maintenance tasks and makes it easy to standardize security settings. It also is a valuable target for attackers, because it stores so much useful information. Since AD is a target for attackers, it should also be a target for your hardening efforts.

Begin by recognizing the value of compromising AD. Limit the number of administrators with access to AD. Ensure that administrators managing AD do so using separate Administrator user accounts. Administrators should have one account for AD administration and at least one other account for other administration tasks. Isolating privileged user accounts makes the accounts harder to compromise. You can create an AD security group with necessary privileges for this purpose. To add additional AD administration restrictions, require that AD administrators do their AD work only from dedicated terminal servers instead of their workstations. This requirement reduces the potential of malware infections on workstation computers to infect AD or allow AD compromise.

Periodically change the **Directory Service Restore Mode (DSRM)** password. And immediately change it from the default password after installation. This password is what you use to log on to a domain controller (DC) that has been booted into DSRM mode to create an offline copy of AD. This capability would allow an attacker to copy all your AD information. Protect the DSRM password for each DC and change it at least every six months.

Other steps you can take to harden AD include ensuring all DCs are physically secure. Locate your DCs in a datacenter or other location with limited access. Configure your DCs to audit important activities and use Internet Protocol Security (IPSec) between all servers. IPSec may be a little difficult to use for client connections, but setting it up for use between servers doesn’t take a lot of effort. IPSec will help ensure that your AD remains secure.

**Hardening Microsoft Windows OS Administration**

Hardening the Windows operating system administration involves protecting the Administrator user accounts and ensuring computers are up to date. You’ve already learned that disabling the built-in Windows Administrator account is a recommended step. After you create other user accounts with Administrator privileges, disable the default Administrator account and use the new accounts for all administrative tasks. Enable strong passwords and set Administrator passwords to expire on a regular basis. These settings will help keep your Administrator user accounts secure.

Since a common administrative activity is to evaluate and change security settings, it is very helpful to create and maintain baselines. Baselines are copies of files and settings you can use for comparison or to restore if necessary. Create a full backup of each system both before and after hardening. The post-hardening backup will be your initial secure baseline. You can use that backup to compare with future backups to identify changes. Although full backups contain all files and folders, it may be beneficial to create individual backups of policies each time you change them. The Group Policy Management Console (GPMC) gives you the ability to back up and restore GPOs. The GPMC also allows you to manage backups of all GPOs. [Figure 11-8](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig8) shows the Backup GPO option in the GPMC.

**FIGURE 11-8** Group Policy Management Console—Backup GPO.

![image](OEBPS/Images/9781284031652_pg265.jpg)

Another critical component of hardening operating system administration is ensuring all Windows systems are updated to the latest patch. Ensure that Windows Update is configured to automatically download and install the latest updates from Microsoft.

[Figure 11-9](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig9) shows the Windows Update window.

[Figure 11-10](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11fig10) shows the Windows Update settings.

**technical TIP**

Change the Windows Updates settings in Windows 7 and Windows Server 2008 R2 using these steps:

**1.** Choose the Windows Start button > Control Panel.

**2.** Select System and Security.

**3.** Select Windows Update. From this window, you can change Windows Update settings, manually check for available updates, or view update history.

**FIGURE 11-9** Windows Update.

![image](OEBPS/Images/9781284031652_pg266.jpg)

**FIGURE 11-10** Windows Update settings.

![image](OEBPS/Images/9781284031652_pg266-1.jpg)

**Hardening Microsoft Servers and Client Computers**

Don’t neglect any computer that is attached to your network. You should harden both servers and workstation computers. Any compromised computer that is connected to your network is a threat to the entire network. Microsoft makes the process of hardening server computers easier with the SCW utility. You can implement many of the hardening recommendations just by answering questions in the SCW. Workstation computers are another matter. You will have to manually harden your workstations. However, the news isn’t all bad. Windows 7 and Windows 8 are fairly secure when they are installed and you won’t have to start from scratch. You’ll need to take extra steps, but Windows 7 and Windows 8 do not require substantial effort to harden.

Hardening Server Computers

Server computers exist on your network to provide one or more specific services. You have two main areas to address when hardening servers. First, ensure that your server computers don’t do anything they’re not supposed to do, such as run extra services that aren’t needed. If a server should provide database services only, then it probably shouldn’t have IIS installed as well. Second, harden the services they are supposed to provide. Start off by installing only the roles you need for any particular server to fulfill its purpose. One of the first steps to take after installing any new server is to run the SCW utility. The SCW utility helps identify many of the unneeded services and open ports. Run SCW to disable any roles or services you don’t need and then review the remaining services in the Windows Services window. Disable any services that are still running but you don’t need.

After running SCW and disabling additional services, it is a good idea to scan each server using a port scanner to identify any open ports you may have missed. Use the **nmap** utility or any other port scanning software to identify open ports. Your open port scan shouldn’t find any unexpected open ports. If it does locate any ports that are open, find out what service is using them and decide whether to close the ports or add them to your approved open ports list. You should know how every open port is being used.

To make it harder for unauthorized users to connect to your server computers, enable IPSec for all server-to-server connections. IPSec will require that any computer that attempts to connect to your server be authorized to connect. Using IPSec and removing or disabling unnecessary user accounts will make it more difficult for attackers to compromise your server computers.

Once you’ve taken these steps to harden your servers, focus on the services that are still running. Every server will have some services running and some ports open. The second main phase of hardening servers is to focus on these components.

**technical TIP**

Get more information on the free nmap utility at *[http://nmap.org/](http://nmap.org/)*. The utility can be downloaded from this site and installed on any computer. Before you use nmap to scan any computer, ensure you have permission in writing from the computer and network owner to perform the scan. Port scanning can cause substantial network activity and even trigger intrusion alarms. You don’t want to cause someone to treat your scan as a hostile attack. Make sure all stakeholders know what you’re planning to do, when you’re planning to do it, and that you have permission to do it.

Nmap offers many command options, but here are a few simple ones that will provide a list of open ports:

nmap -vA 192.168.1.128

The previous command scans for any open ports on 192.168.1.128 and also attempts to detect the operating system running on the computer at that Internet Protocol (IP) address.

nmap -vsT 192.168.1.128

The previous command scans and attempts to connect to any open ports on the computer at 192.168.1.128. Using the “-vsT” option is slower than the “-vA” scan but also provides more complete information on services that are running and monitoring open ports.

For even more command options, go to the nmap Web site for additional details and complete documentation. Nmap can help you identify any vulnerability on your computers.

Hardening Workstation Computers

While many of the strategies for hardening computers apply to all computers, some are especially important for workstations. In general, workstation computers act as clients, and not servers. When hardening workstation computers, one of the main goals is to ensure the computer maintains a clean identity and doesn’t attempt to violate your security policy.

One of the more common issues with workstation computers is malware. Since workstations tend to connect to many Internet resources and run many software programs, they run into malware frequently. Removing malware is often far more difficult than preventing it. Ensure that every workstation computer has up-to-date anti-malware software installed and that its database of known malware is up to date as well. Microsoft provides two products for this purpose. Each includes anti-malware protection:

• **Microsoft Security Essentials** (*[http://www.microsoft.com/Security\_Essentials/](http://www.microsoft.com/Security_Essentials/)*)—A free collection of security products intended to protect home computer users from various types of malware

• **Microsoft Forefront** (*[http://technet.microsoft.com/en-us/forefront/default.aspx](http://technet.microsoft.com/en-us/forefront/default.aspx)*)—A commercial product that is a complete security management solution for enterprise users

Other anti-malware products are available for workstations.

In addition to ensuring workstations are protected from malware, it is important to mitigate as many other vulnerabilities as possible. Most workstation installations add many unneeded programs and services. And no single program effectively analyzes a workstation’s role and recommends changes to make it more secure. Review all running services and programs and disable the ones you don’t need. Likewise, review the Windows Firewall settings to only allow network traffic for the services and applications your workstations really need.

![image](OEBPS/Images/war.jpg)**WARNING**

Securing workstations requires control. You can exert control over workstations your organization owns or directly manages. Group Policy makes it possible to effectively manage and enforce nearly all security settings for your organization’s workstations. Remote users pose a more difficult challenge. It is very difficult to exert any control over workstations your organization doesn’t own or manage. You should provide a separate access path for internal versus external workstations. Isolate external workstations and restrict what resources they can access.

**Hardening Data Access and Controls**

The key to deploying the best Windows access controls is to first develop a clear idea of what you are attempting to control. In general, minimize the number of user accounts on all computers and carefully control access to accounts with Administrator rights. Access to data and resources is based on identity. You have to implement secure identity management before you can trust your access controls. As you’ve already learned, having fewer user accounts and using strong passwords make your systems more secure. But just limiting user account access is only part of the solution.

Once you identify the data and resources you need to control, use Windows Group Policy to establish access control lists (ACLs) that limit access to specifically defined users and groups. The easiest way to implement access control in a large environment is to use AD and global groups for as many ACLs as possible. Avoid allowing anonymous or guest user accounts to access any sensitive data.

To protect data at rest, either use Windows Encrypting File System (EFS) for folders that contain sensitive data or Windows BitLocker to encrypt entire volumes. Regardless of the option you choose, ensure any backups encrypt your data as well.

**Hardening Communications and Remote Access**

Remote connections can present additional security challenges. You need the ability to evaluate several attributes of a connection request’s source before granting access to your network. Define different access profiles based on your policies to meet the needs of different types of network users. **Network access control (NAC)** is a solution that defines and implements a policy that describes the requirements to access your network. NAC defines the rules a connecting node must meet to establish a secure connection with your network. It also allows you to proactively interrogate nodes that request a connection to your network to ensure they don’t pose a risk. Use NAC to classify connecting nodes based on the level of compliance with your access rules. NAC allows you to evaluate node attributes such as these:

| **TABLE 11-4** NAC software products. |
| **PRODUCT** || **WEB SITE** |
| PacketFence (Open source) || *[http://www.packetfence.org/en/home.htmll](http://www.packetfence.org/en/home.htmll)* |
| Sophos Network Access Control || *[http://www.sophos.com/en-us/your-needs/features/nac.aspx](http://www.sophos.com/en-us/your-needs/features/nac.aspx)* |
| Symantec Endpoint Protection || *[http://www.symantec.com/endpoint-protection](http://www.symantec.com/endpoint-protection)* |
| StillSecure Safe Access || *[http://www.stillsecure.com/service/safe-access-world%E2%80%99s-best-and-most-secure-nac-solution](http://www.stillsecure.com/service/safe-access-world%E2%80%99s-best-and-most-secure-nac-solution)* |
| McAfee Endpoint Protection || *[http://www.mcafee.com/us/products/endpoint-protection/index.aspx](http://www.mcafee.com/us/products/endpoint-protection/index.aspx)* |
| Checkpoint Endpoint Security || *[http://www.checkpoint.com/products/endpoint\_security/nac.html](http://www.checkpoint.com/products/endpoint_security/nac.html)* |
| Cisco Network Admission Control || *[http://www.cisco.com/en/US/products/ps6128/index.html](http://www.cisco.com/en/US/products/ps6128/index.html)* |
| TrustWave Network Access Control || *[https://www.trustwave.com/network-access-control/](https://www.trustwave.com/network-access-control/)* |
| Enterasys Network Access Control || *[http://www.enterasys.com/products/advanced-security-apps/enterasys-network-access.aspx](http://www.enterasys.com/products/advanced-security-apps/enterasys-network-access.aspx)* |
| Aerohive Network Access Control || *[http://www.aerohive.com/partners/solution-partners/network-access-control-nac](http://www.aerohive.com/partners/solution-partners/network-access-control-nac)* |

• Anti-malware protection

• Firewall status and configuration

• Operating system version and patch level

• Node role and identity

• Custom attributes for enterprise configuration

NAC solutions enable you to exert control over which nodes can connect to your networks and what rights you’ll grant to them once they connect. NAC provides a formal method to establish relationships with several types of security controls and helps you minimize threats from malware, increase LAN-to-WAN availability, and provide proof of compliance through NAC-related auditing data. NAC is a method of controlling network access that several vendor products support. [Table 11-4](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11tab4) lists some vendors that provide NAC software.

You can choose from many products to implement NAC. NAC software alone won’t secure your networks, but it gives you the ability to define and enforce policies that can get you closer to your security goals.

Authentication Servers

Once remote computers are authorized to connect, you’ll need to authenticate the remote user as well. You have many ways to authenticate remote users, but three main approaches are common. The first two, RADIUS and TACACS+, rely on centralized authentication databases and servers to handle all remote users. Either of these approaches works well when there are a large number of remote users or you need to manage remote users from a central location. The third option is to use a virtual private network (VPN).

RADIUS

Remote Authentication Dial In User Service (RADIUS) is a network protocol that supports remote connections by centralizing the management tasks for authentication, authorization, and accounting for computers to connect and access a network. RADIUS is a popular protocol that many network software and devices support and is often used by Internet service providers (ISPs) and large enterprises to manage access to their networks.

RADIUS is a client/server protocol that runs in the Application Layer—Layer 7 in the Open Systems Interconnection (OSI) Reference Model or Layer 4 in the TCP/IP Reference Model—and uses, and uses the User Datagram Protocol (UDP) to transport authentication and control information. Servers with RADIUS support that control access for remote users and devices communicate with the RADIUS server to authenticate devices and users before granting access. In addition to just granting access and authorizing actions, RADIUS records network services used for accounting.

TACACS+

Terminal Access Controller Access-Control System Plus (TACACS+) is another network protocol. TACACS+ was developed by Cisco. TACACS+ has roots back to an earlier protocol, TACACS, but is an entirely different protocol. TACACS+ provides access control for remote networked computing devices using one or more centralized servers. TACACS+ is similar to RADIUS in that it provides authentication, authorization, and accounting services, but TACACS+ separates the authentication and authorization information. TACACS+ also uses the TCP protocol for more reliability.

One difference between RADIUS and TACACS+ is important to security. RADIUS only encrypts the password when sending an access request packet to the server. TACACS+ encrypts the entire packet. That makes it a little harder to sniff data from a TACACS+ packet.

VPNs and Encryption

Virtual private networks (VPNs) are one of the most popular methods to establish remote connections. A VPN appears to your software as a regular network connection. It is actually a virtual connection, also called a tunnel, which uses a regular WAN connection of many hops but looks like a direct connection to your software. Most VPNs offer the option to encrypt traffic using different modes to meet different needs.

**technical TIP**

Most people associate VPNs with encrypted traffic. Although most VPN uses include encrypting all of the traffic transported through the VPN tunnel, encryption is an option and not a part of the VPN itself. The private part of VPN really refers to private addressing, not data privacy.

The concept of **tunneling** is central to most VPNs. Tunneling allows applications to use any protocol to communicate with servers and services without having to worry about addressing privacy concerns. Applications can even use protocols that aren’t compatible with your WAN. Here’s how tunneling works:

**1.** Your application sends a message to a remote address using its Application Layer protocol.

**2.** The target address your application used directs the message to the tunnel interface. The tunnel interface places each of the packets from the Application Layer inside another packet using an **encapsulating protocol**. This encapsulating protocol handles tunnel addressing and encryption issues.

**3.** The tunnel packet interface then passes the packets to the layers that handle the WAN interface for physical transfer.

**4.** On the receiving end, the packets go from the WAN to the remote tunnel interface where the packets are decrypted and assembled back into Application Layer packets and then passed up to the remote Application Layer.

This arrangement provides excellent flexibility and security. Depending on your VPN solution, you can choose from several encapsulating protocols, including:

• **Generic Routing Encapsulation (GRE)**—A tunneling protocol developed by Cisco Systems as an encapsulating protocol that can transport a variety of other protocols inside IP tunnels.

• **IPSec**—A protocol suite designed to secure IP traffic using authentication and encryption for each packet.

• **Layer 2 Forwarding Protocol (L2FP)**—A tunneling protocol developed by Cisco Systems to establish VPNs over the Internet. L2F does not provide encryption—it relies on other protocols for encryption.

• **Point-to-Point Tunneling Protocol (PPTP)**—A protocol used to implement VPNs using a control channel over TCP and a GRE tunnel for data. PPTP does not provide encryption.

• **Layer 2 Tunneling Protocol (L2TP)**—A tunneling protocol used to implement a VPN. L2TP is a newer protocol that traces its ancestry to L2FP and PPTP. Like its predecessors, L2TP does not provide encryption itself.

The VPN you select depends on several factors. Some VPN solutions are vendor specific and rely on one type of hardware. Other types of VPNs are operating system specific. For example, the new Secure Socket Tunneling Protocol (SSTP) is only available for the Windows operating system. SSTP is Microsoft’s attempt to provide a solution that works on any networking hardware. SSTP uses a Secure Sockets Layer (SSL) to transport Point-to-Point Protocol (PPP) or Layer 2 Tunneling Protocol (L2TP) traffic. Using SSL removes many of the firewall and network address translation (NAT) issues some other protocols encounter.

Regardless of the remote authentication method you choose to use, ensure that you configure each server and client to establish connections only using your preferred method.

**Hardening PKI**

One method of hardening authentication is by using digital certificates. Certificates can increase the security of IPSec, SSL connections, and Web server authentication. Implementing such an approach requires a method of creating, distributing, and maintaining certificates. A common approach is to implement a public key infrastructure (PKI). PKI is a term that refers to the hardware, software, policies, and procedures to manage all aspects of digital certificates. PKI has the reputation of making environments more secure, but this is only true if your PKI components are secure.

The most important component of securing PKI is to ensure all computers that participate are hardened. This is especially true for the Certificate Authority (CA) servers. In addition to hardening CAs like other servers, ensure your CAs are physically secure and only accessible by authorized administrators. Ensure that you back up the CA keys and store them in a safe location. You’ll need these to recover certificate access after restoring from some types of disasters.

Use GPOs to distribute root CA certificates. Using GPOs gives you the ability to control and automate the certificate distribution. To ensure you can track down unauthorized certificate actions, enable auditing for all CA and certificate events. You will probably need to increase the maximum audit log file to store log entries for more than a few days for heavily utilized servers.

**User Security Training and Awareness**

One of the most important aspects of hardening any computer is how the computers are used. Although malicious attackers are a threat to computer security, so are authorized users. Many security incidents result from poorly trained, forgetful, or stubborn authorized users. In some environments, users view security as a barrier and stubbornly refuse to abide by the security policy. Security awareness training is crucial from a person’s first exposure to your environment.

Each new employee, contractor, or visitor should go through security awareness training that corresponds to his or her level of system access. Employees generally have the greatest privileges in any organization’s information systems and should be required to undergo the most comprehensive security training. Contractors or other temporary personnel have less access than employees. Visitors often have less access. You should design security training for each group of users, based on their access and responsibilities. Part of internal personnel training should include procedures for granting access to visitors. Security awareness programs are always good ideas and they also may be mandatory. If your organization must comply with Sarbanes-Oxley, Gramm-Leach-Bliley, HIPAA, or the Federal Information Security Management Act (FISMA), you must implement a security awareness program. [Table 11-5](#22_Chaper11_split_001.xhtml#ba-9781284031652-ch11tab5) lists different groups of users and suggested security training requirements.

| **TABLE 11-5** User types and suggested security training. |
| **USER TYPE** || **DESCRIPTION** || **SECURITY TRAINING** |
| Employee || Person employed by an organization with permanent responsibilities and access to certain information system resources || Employees receive mandatory security policy training with signed acceptance of acceptable use policies (AUPs), completion of information system access security training prior to receipt of access credentials, and mandatory recurrent security awareness and policy update training. Properly trained employees should be able to recognize security breaches and know what to do about them. |
| Contractor || Temporary worker with limited temporary access to information resources related to assigned responsibilities || Contractors receive mandatory pre-engagement security policy training with signed acceptance of AUPs, completion of information system access security training that relates to assigned responsibilities prior to receipt of access credentials, and mandatory recurrent security awareness and policy update training. Properly trained contractors should be able to recognize security breaches and know whom to notify if a breach occurs. |
| Visitor/guest || Transient user with very limited access to information system resources || Visitors/guests agree to comply with AUPs. |
|   ||   ||   |

Regardless of the type of user, anyone who connects to your computer systems should encounter frequent reminders of the importance of security. Use any of these formats to remind users of the importance of security:

• Physical posters and banners in conspicuous locations, such as in break rooms and cafeterias, and around printers, fax machines, or shredders

• E-mail newsletters and security policy updates

• Periodic Web site reminders

• Social media messages

• Daily or weekly tip programs

• Contests with security themes

• Security events on specific dates, such as November 30, International Computer Security Awareness Day

• Lunch-and-learn meetings about topics of interest to employees personally—such as identity theft or cyberbullying—as well as topics of interest to your organization

• Visible modeling of good security behaviors by your organization’s leaders

**Best Practices for Hardening Microsoft Windows OS and Applications**

Many resources are available to you for hardening Windows computers. Some resources focus on a few high-level suggestions while others go into very detailed lists of suggestions. To make your job of securing Windows computers easier, here is a list of best practices for securing different types of computers. These best practices may not all apply to every one of your computers. They do provide a solid starting point that will result in a far higher level of security than taking no action at all. The key to hardening your Windows computers is to reduce each computer’s attack surface to the absolute minimum while still allowing the computer to fulfill its purpose.

Here are the best practices for hardening Windows operating systems:

• Install only the Server Core option when you don’t need extra functionality.

• Select the minimum number of roles when installing Windows Server 2008 R2 and Windows Server 2012.

• Run SCW immediately after installing the operating system for Windows Server 2008 R2 and Windows Server 2012.

• Update each computer with the latest operating system patches.

• Configure each computer for automatic Windows updates.

• Install and run Microsoft Baseline Security Analyzer (MBSA) and at least one other Windows security vulnerability scanner.

• Create one or more user accounts with Administrator rights.

• Disable the Administrator and Guest user accounts.

• Disable all unneeded services.

• Close all ports not required by services or applications.

• Create GPOs for all security settings, including firewall rules.

• Use AD to distribute all configuration changes using GPOs.

• Create a backup of each GPO.

• Scan all computers for open ports.

• Limit physical access to all critical servers.

• Create an initial baseline backup.

• Change the AD DSRM password periodically, at least every six months.

• Install anti-malware software on each computer.

• Ensure all anti-malware software and data is current.

• Use NAC software or devices to control remote computer connections.

• Use remote authentication methods to authorize remote computers and users.

• Require secure VPNs to access internal network resources.

• Use IPSec with digital certificates to authenticate computer-to-computer connections in the datacenter.

• Require security awareness training prior to issuing access credentials.

• Require periodic recurrent security awareness training to retain access credentials.

• Provide continuing security awareness through different means.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

*Hardening* is the process of making computers more secure. The process involves identifying vulnerabilities and implementing compensating controls. In this chapter, you read about some of the most important steps to make your Windows computers more secure. You learned how to install servers to be more secure and how to make both servers and workstations more secure after installation. Following the best practices at the end of this chapter will help you keep your Windows environment secure and difficult for attackers to compromise.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Directory Service Restore Mode (DSRM)**

**Encapsulating protocol**

**Hardening**

**Network access control (NAC)**

**Nmap**

**Role**

**Security Configuration Wizard (SCW)**

**Server core installation**

**Tunneling**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 11 ASSESSMENT**

  **1.** The term *attack surface* refers to all of the software a computer runs that is vulnerable to attack.

A. True

B. False

  **2.** The best way to secure a service is to disable it.

A. True

B. False

  **3.** The process of making configuration changes and deploying controls to reduce the attack surface is called \_\_\_\_\_\_\_\_.

  **4.** Which Windows Server 2008 R2 and Windows Server 2012 feature allows you to specify which services you want to include during the operating system installation?

A. Edition

B. Role

C. GPO

D. Configuration

  **5.** Which Windows Server 2008 R2 and Windows Server 2012 installation option includes only a minimal environment to just run selected services?

A. Server core

B. Foundation

C. Standard

D. Runtime

  **6.** Which Microsoft tool guides administrators and creates policies based on least privilege to reduce the attack surface of a Windows server after installation?

A. GPO

B. MBSA

C. SCW

D. NMAP

  **7.** You can use GPOs to deploy Windows Firewall rules.

A. True

B. False

  **8.** Which of the following actions is the best action to take to secure an unneeded service?

A. Close the port.

B. Disable the service.

C. Delete the service from Services.

D. Create a GPO restriction for the service.

  **9.** You should disable the \_\_\_\_\_\_\_\_ user account to make it harder for attackers to access the default escalated-privilege account.

**10.** AD makes securing many computers in a network more complex.

A. True

B. False

**11.** The \_\_\_\_\_\_\_\_ tool is a handy open source tool to scan computers for open ports.

**12.** Which term describes software that defines and implements a policy that describes the requirements to access your network?

A. SCW

B. VPN

C. GPO

D. NAC

**13.** VPNs increase security of remote connection by guaranteeing all traffic is encrypted.

A. True

B. False

**14.** Which new Microsoft VPN protocol makes it easy to use VPNs even through firewalls?

A. L2TP

B. SSTP

C. TLS

D. TCP

**15.** \_\_\_\_\_\_\_\_ refers to the hardware, software, policies, and procedures to manage all aspects of digital certificates.

**CHAPTER 12**

**Microsoft Application Security**

ONCE YOUR OPERATING SYSTEM IS SECURE, you can focus on securing the software that runs in the operating system. Operating system software is different from application software. Regardless of how secure your operating system is, one vulnerable application can put your organization’s data at risk. This chapter will teach you about the most popular Microsoft applications. You will also find out how to make each one more secure to protect your organization’s data.

**Chapter 12 Topics**

This chapter covers the following topics and concepts:

• What the principles of Microsoft application security are

• How to secure key Microsoft client applications

• How to secure key Microsoft server applications

• What you can learn from case studies in Microsoft application security

• What best practices for securing Microsoft Windows applications are

**Chapter 12 Goals**

When you complete this chapter, you will be able to:

• Describe the principles of Microsoft application security

• Secure Microsoft client applications

• Secure Microsoft server applications

• Apply lessons learned from application security case studies

**Principles of Microsoft Application Security**

Application security covers all activities related to securing **application software** throughout its lifetime. Application software is any computer software that allows users to perform specific tasks. Examples of these tasks are sending and receiving e-mail, browsing the Web, creating a document or spreadsheet, or entering orders for materials. Ensuring application software security includes ensuring security during design, development, testing, deployment, maintenance, and retirement. All too often, organizations view application security as a deployment issue. Security must begin earlier in the design and development process. In this chapter, you’ll study how to harden software after it has been completed or acquired by your organization.

A secure application is one that protects each of the three C-I-A properties of data security at all times. The three C-I-A properties are confidentiality, integrity, and availability. Check that your software, whether developed in-house or licensed, makes the data it manages available to authorized users on demand while denying access to unauthorized users. This chapter applies to any application software running on a server or client computer. Your applications provide access to data. They must also make certain that only authorized users can view or modify data based on your organization’s specific security restrictions. In short, application security is all about ensuring that your applications add at least one more layer of controls between users and your data.

Common Application Software Attacks

Understanding the basic principles of securing applications starts with understanding how attackers damage applications. Hackers have many ways to harm applications. Several approaches are more common and deserve the most attention. The more common types of attacks include:

• **Malformed input**—This is one of the most common types of attack. Computer criminals provide input to an application that is designed to cause results the developers did not intend. They use malformed input to crash programs, disclose or modify data, or hijack connections.

• **Privilege escalation**—**Privilege escalation** adds more authority to the current session than the process should possess. There are several methods to escalate privileges, and all compromise the access control lists (ACLs) you have in place to limit data and resource access.

• **DoS**—Denial of service attacks focus on either making the application or network slow enough that it can’t respond to user requests in a timely manner or crashing the application. Either way, users can’t get to the data they need.

• **Identity spoofing**—This means assuming the identity of another user. **Spoofing** means masquerading as another person or process. In most cases, the other user is one who possesses more privileges, and this greater access allows an attacker to get into more data and resources. In some cases, hackers use identity spoofing just to hide their own identities—not to escalate privileges.

**technical TIP**

Many options are available to harden applications. One resource is the Open Web Application Security Project (OWASP). OWASP is a not-for-profit organization that focuses on improving application security. OWASP offers many valuable resources related to application security. You can find many informational videos and the latest Top 10 Web Application Security Risks list. Although primarily focused on Web applications, information on this site applies to all application security topics. The OWASP Web page is located at *[http://www.owasp.org](http://www.owasp.org)*.

• **Direct file or resource access**—This refers to exploiting holes in access controls that allow a user to directly access files or other resources. If your application allows direct object access, users may be able to bypass normal access controls.

• **Extra-application data access**—This means accessing your application’s data outside the application. This could be from the operating system or from another program, or by just taking or copying backup media.

Each of these attacks is preventable. Some of the controls to stop attacks, such as processing malformed input, for example, depend on the application’s design. You can implement controls to stop other attacks. Put extra-application data access into operation outside your application. Just as operating systems need to be hardened to be as secure as possible, follow steps to harden each application you run on any computer.

Hardening Applications

Hardening applications generally follows several steps. The specific actions differ from application to application, but the overall strategy remains the same. Here are the general steps to hardening applications:

• Install the application using only the options and features you plan to use.

• After installing the application, remove any default user accounts and sample data, along with any unneeded files and features.

• Configure the application according to the principle of least privilege.

• Ensure your application has all of the latest available security patches applied.

• Monitor application performance to verify that your application adheres to security policy.

Keep general guidelines in mind and follow the recommendations for each type of application software. You’ll end up with a far more secure environment than when you started.

**Securing Key Microsoft Client Applications**

Many applications tend to run as either client or server components. Clients generally initiate connections and request services from servers. Servers generally listen for incoming connection and service requests. Your approach to securing each type of application software will be different. Client applications are often targets because many workstations, laptops, and mobile devices are not aggressively hardened. With so many personal computers that are insecure and contain client applications, common applications are attractive to attackers who want to compromise an organization’s data. If an attacker can compromise a client application that an organization uses to access a server application, that hacker is one step closer to your data. In this section, you’ll learn about how to secure, or harden, several of the most popular Microsoft client applications.

Web Browser

Arguably, the most popular and frequently used client application is the Web browser. A Web browser allows a user to access content from Web servers across a network. In most cases, users access resources and applications using the Internet. Web browsers are attractive targets because they are the primary client of Web applications. A compromised Web browser can make it easy for an attacker to access stored server connections by means of stored credentials. Hackers can even compromise your organization’s data without attacking the Web browser directory but by intercepting the information your Web browser sends to the Web server.

Web browsers are attractive targets for several types of attacks, including:

• **Infect with malware**—Several default Web browser settings allow Web browsers to run helper programs, such as ActiveX controls or Java applets, to enhance the user experience. Although many helper programs are useful, attackers can provide substitute programs that are actually malware.

• **Intercept communication**—Authorized users can access sensitive organizational data, often using a Web browser. Any device or computer that sits between the client and the server sees all traffic passing back and forth between the two. An attacker who places a proxy server between a Web browser and a Web server can see and collect all of the traffic, including sensitive data that is intended only for the authorized user. This type of attack is often called a **man-in-the-middle attack**.

• **Harvest stored data**—Some versions of Web browsers have vulnerabilities that allow Web pages to collect information stored on the client computer. This information includes usernames, passwords, account numbers, and local copies of sensitive data. This stored information can appear in cookies, application files, and settings. Criminals can look for this type of information and tell your Web browser to send it to any location.

| **TABLE 12-1** Securing a Web browser. |
| **ACTION** || **DESCRIPTION** |
| Set the security level of the Internet zone to High from the Security tab. || Setting the security zone to High in Internet Explorer (IE) automatically enables many features that block most known vulnerabilities. Setting the security zone to High will also likely reduce the Web browser’s functionality. |
| Add specific sites you trust as Trusted Sites from the Security tab. || When you are visiting sites defined as trusted, Internet Explorer relaxes the restrictions placed on general Internet sites. This setting allows ActiveX and Java application components to run. |
| Change the cookie settings from the Privacy tab. On the Advanced dialog box, select to prompt for first-party and third-party cookies. || This setting will alert you any time a Web site attempts to access any cookies. This requires user interaction each time a Web site wants to access a cookie. It gives you the chance to deny cookie access. You can also add any sites from which you want to accept all cookies to the list of allowed sites. You won’t be prompted for cookie access from the listed sites. You can also select the Delete Browsing History on Exit check box on the General tab to have IE delete all cookies and other browsing history each time you exit IE. |
| Uncheck Enable Third-Party Browser Extensions from the Advanced tab. || This setting limits the potential of browser helpers from disclosing private data. |
| Check Always Show Encoded Addresses from the Advanced tab. || This setting makes it harder to spoof Internet addresses. |
| Uncheck Play Sounds in Web Pages from the Advanced tab. || This setting prevents an attacker from infecting your computer using a sound file. |

These are just a few of the many types of Web browser attacks. You can, however, harden each Web browser to resist attacks. Some of the hardening suggestions may reduce the Web browser’s flexibility and functionality, but it will be more secure. Change settings in any Web browser by opening the settings or options page. Most of the following suggestions apply to all Web browsers, but the actions in the following table are specifically oriented toward Internet Explorer. [Table 12-1](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12tab1) lists steps to secure a Web browser.

[Figure 12-1](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12fig1) shows the Internet Options dialog box for Internet Explorer.

**technical TIP**

Access the Internet Options dialog box by using either of these procedures:

**1.** Inside Internet Explorer, select Tools > Internet Options.

**2.** From Windows, launch Control Panel, and then select Network and Internet > Internet Options.

**FIGURE 12-1** Internet Options dialog box in Internet Explorer 8.

![image](OEBPS/Images/9781284031652_pg284.jpg)

Many more settings are available, but the settings in [Table 12-1](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12tab1) will harden your Web browser and will limit the damage an attacker can do using your Web browser.

E-mail Client

E-mail clients are another popular type of client software. Most of today’s e-mail clients connect to a mail server and either display or download e-mail messages. One of the most popular e-mail clients is Microsoft Office Outlook. As with Web browsers, there are other popular e-mail clients.

Generally, the key to hardening e-mail clients is to limit any malicious code that may be attached to e-mail messages. Next, take steps to ensure e-mail message privacy. The first step requires additional software. You should already have anti-malware software installed on each computer. Select anti-malware software that integrates with your e-mail client. Many current anti-malware software packages work with e-mail clients to scan all incoming and outgoing messages for malware. It is important to scan incoming messages to detect any malware before it infects your computer. It is also important to scan outgoing messages to ensure your computer is not sending malware to other destinations. The enterprise solution from Microsoft is Microsoft Forefront. This product fully integrates with existing Microsoft application software.

The second step to securing an e-mail client is to safeguard message privacy. Require the use of Secure Sockets Layer/Transport Layer Security (SSL/TLS) when connecting to your mail server to make certain that all message exchanges are encrypted. This option will work only if your mail server supports it and is properly configured to handle encrypted connections. The main drawback is that once your message reaches your mail server, the message is decrypted and sent on its way. Alternatively, you can encrypt each message to guarantee your message stays encrypted all the way from your e-mail client to the recipient’s e-mail client.

Unfortunately, there is no automatic method to encrypt e-mail messages for generic recipients. Microsoft Office Outlook includes Secure/Multipurpose Internet Mail Extensions (S/MIME) encryption as long as the recipient has your public key. Several add-on products work with most e-mail clients to encrypt messages as well. For example, OpenPGP, GPG, and S/MIME are all examples of e-mail message encryption methods. Before using any of the methods or software, confirm that the recipient of your e-mail message uses the same method. Additionally, his or her e-mail client must be capable of receiving and decrypting the message. Since you have to take special steps for each recipient to whom you send e-mail, encrypting e-mail messages is not used extensively for sending messages to large groups of people. It does work very well in situations where you know you’ll be sending several private messages to the same person or persons.

Most general hardening recommendations are appropriate for other e-mail clients. The following specific recommendations apply directly to Microsoft Office Outlook 2007 and newer versions. [Table 12-2](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12tab2) lists steps to make your e-mail client more secure.

**technical TIP**

Some attacks on your computer are intended to turn your computer into a **zombie**. A zombie may also be called a bot. It is a computer that follows the instructions sent from another computer. Attackers often use zombies to send spam or malware to all the e-mail addresses in a zombie’s address book. Outbound malware scanning will catch many of these attacks.

| **TABLE 12-2** Securing an e-mail client. |
| **ACTION** || **DESCRIPTION** |
| Install anti-malware software that integrates with your e-mail client. || Integrated anti-malware software should scan each incoming and outgoing message. Have a plan to keep all anti-malware software and data up to date. |
| Enable the junk filter function. || Configure your e-mail client to filter suspicious messages and put them in a junk messages folder. Keep them separate from your regular messages. |
| If your mail server supports secure connections, force your e-mail client to use only secure connections when retrieving or sending e-mail. || Although this setting will encrypt all e-mail messages between your e-mail client and the mail server, messages that travel beyond your mail server will be transmitted in the clear. |
| Do not preview messages. || Many attackers embed malicious code in images or other e-mail content. Train users to never open an e-mail message from an unknown source. Since many types of malware send e-mail messages using the sender’s address book, users shouldn’t open any attachment they aren’t expecting. |
| Change the default mail format to plaintext. || Plaintext does not contain embedded commands that could result in malware infections. HTML messages are much more visually appealing but more dangerous as well. |
| Use an Encrypting File System (EFS) or BitLocker to encrypt the folder or drive that contains your e-mail data files and attachments. || Keeping your e-mail messages and attachment folders encrypted makes it harder for attackers to access the contents of your e-mail messages without encountering operating system access controls. |
| If you need to exchange private e-mail messages with a number of recipients, either use Microsoft’s e-mail encryption or acquire additional software to use another solution. || Ensure both sides of the e-mail exchange use the same encryption method. Also, each recipient must have the sender’s public key. In most cases, this is accomplished by first sending a digitally signed message to the recipient. The recipient receives the message and adds the public key to the address book. The recipient can now receive and decrypt encrypted messages from the sender. |
|   ||   |

Productivity Software

Most workstation computers and even mobile devices have some type of productivity software installed. Productivity software is any software enabling users to accomplish general work more efficiently. Productivity software may be installed as several separate programs or as a collection, or suite, of software. Common productivity software programs include the following, along with Microsoft’s product for each solution:

• **Word processing**—Microsoft Word

• **Spreadsheet**—Microsoft Excel

• **Lightweight database**—Microsoft Access

• **Presentation**—Microsoft PowerPoint

• **Project scheduling/management**—Microsoft Project

• **Publishing**—Microsoft Publisher

Productivity software packages are also targets for attackers, especially the more popular programs. The main goals for compromising productivity software are malware infection and private data disclosure. Many types of malware infect computers when users open infected files. Infected documents, spreadsheets, presentations, and databases can exploit vulnerabilities in your productivity software and launch malware that infects your computer. Many successful attacks still introduce malware to computers using productivity software document types that appear to be harmless.

| **TABLE 12-3** Securing productivity software. |
| **ACTION** || **DESCRIPTION** |
| Install anti-malware software that integrates with your productivity software. || Integrated anti-malware software should scan each file before opening it. Make sure you have a plan to keep all anti-malware software and data up to date. |
| Use EFS or BitLocker to encrypt the folder or drive that contains your productivity software documents and databases. || Keeping your document folders encrypted makes it harder for attackers to access the contents of your documents without encountering operating system access controls. |
| Never open a file unless you trust the source. || Many malware infections depend on a user opening an infected file. |
| Ensure your productivity software has the latest security patches installed. || New vulnerabilities are discovered daily. Unpatched software is at risk. |

The standard file extensions also identify potential content types to attackers. If a criminal is looking for private data that is likely stored in an Access database, any files with the extension .accdb are good candidates. [Table 12-3](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12tab3) lists the general steps to help secure your productivity software.

File Transfer Software

One of the earliest uses of networks was to transfer files from one computer to another. Users still transfer files routinely between computers, sometimes over large distances. Every file download or upload is a file transfer. Unfortunately, the protocols most commonly used to transfer files send the contents of each file in the clear, which means unencrypted. The reason for sending data in the clear is that it is much faster than encrypting the data first. However, security is a greater concern than efficiency for private data. Do not use standard file transfer methods for any files that contain private data. Use a secure transfer method.

The most common method of transferring files across a network is the **File Transfer Protocol (FTP)**. FTP uses the Transmission Control Protocol/Internet Protocol (TCP/IP) suite to decompose a file into small messages and send the file to a recipient where the file is reassembled. The process is solid but insecure. As security has become more and more important, additional methods have been introduced, including FTP over a Secure Shell (SSH) and Secure FTP (SFTP). Virtual private networks (VPNs) are also a good choice for transferring files. Use unencrypted FTP within a secure VPN to achieve very good privacy.

Regardless of the specific choice you use, both ends of the network connection must agree on the methods. The main point of securing file transfer software is to ensure all files that contain private data are transferred using some type of encryption.

AppLocker

Microsoft introduced a new feature in Windows that allows you to restrict program execution using Group Policy. This new feature, called AppLocker, is included with Windows Server 2008 R2, Windows Server 2012, Windows 7 (Ultimate and Enterprise editions), and Windows 8 (Professional and Enterprise editions). Prior to AppLocker, Microsoft provided basic software restriction capabilities through the Software Restriction Policies (SRP) in previous Windows versions. SRP is still in newer Windows versions but is harder to use in a larger enterprise than AppLocker. Define rules using Group Policy to restrict which applications workstation computers can run using these types of rules:

• **Path rules**—SRP and AppLocker allow you to define specific paths from which users can execute applications. Any application located in paths not approved by these Windows features cannot run. Unless you carefully restrict users from common installation folders, they can just copy new applications into a common folder and essentially bypass the path rule restriction.

• **Hash rules**—SRP and AppLocker allow you to create a cryptographic hash for each executable to distribute to workstation computers. Windows validates that the executable program matches the approved hash value each time you run a program. This type of rule is more secure than a path rule, but it requires that you update the hash value each time you distribute a program update.

• **Publisher rules**—AppLocker makes application security easier than SRP by introducing a new type of rule. Publisher rules use digital signatures provided by application publishers. Use these signatures with additional criteria, such as minimum version to define allowable applications. For example, you could allow Microsoft Word to run on a workstation only if it has a valid publisher certificate and is at least version 12.0. Although AppLocker publisher rules are slightly similar to SRP certificate rules, AppLocker has added a lot of features and made defining rules much easier.

**technical TIP**

Access AppLocker settings in the Group Policy Management Console (GPMC) on Windows Server 2008 R2 by following these steps:

**1.** Choose Start > Administrative Tools > Group Policy Management.

**2.** Select a Group Policy Object (GPO) or create a new GPO.

**3.** Open the context menu for the selected GPO and select Edit.

**4.** Expand Computer Configuration\\Policies\\Windows Settings\\Security Settings\\ Application Control Policies\\AppLocker.

In addition to the additional features AppLocker provides with Publisher Rules, AppLocker makes it easy to define rules for any number of users employing Group Policy.

**Securing Key Microsoft Server Applications**

Server applications are designed to listen for requests and provide some service. They commonly run in the background on server computers, listen to one or more defined ports, and process requests on behalf of clients. Server applications often interact with centralized data and will likely have access to private data. All three properties in the C-I-A triad are of concern in server applications. A secure application is available to respond to client requests, and enforces the integrity and confidentiality of the data it manages. Several types of server applications are common in organizations and each has its own specific security concerns.

One of the most useful features of both Windows Server 2008 R2 and Windows Server 2012 is the definition of server roles. When you select a server role, Windows installs only the services you’ll likely need to fill that role. The first step in securing any server software is to secure the server computer. One of the best ways to secure a server computer is to limit the roles you install. Install only roles that are necessary for each server to fulfill its purpose.

| **TABLE 12-4** Individual parts of a URL. |
| **DESCRIPTION** || **VALUE** |
| Protocol || *http*—The protocol the Web server will use for this exchange |
| Separator || *://*—Standards separator between the protocol and the host name or address |
| Host name or address || *[www.MicrosoftApplicationSecurityChapter12.com](http://www.MicrosoftApplicationSecurityChapter12.com)*—The name or IP address where the Web server is running |
| Web server command || *Scripts/wsisa.dll/WService=catlookup?isbn=076372677X—*The rest of the URL contains information the Web server uses to interpret the client’s request. In this case, the Web server would attempt to execute wsisa.dll in the scripts folder. |

Web Server

A Web server is a software program that monitors a specific port, normally port 80 or 443, for Web requests and provides content for a Web client. Web servers support many types of requests and apply various protocols to respond to requests. The two most common protocols that Web servers use for normal Web traffic are the Hypertext Transfer Protocol (HTTP) and **Hypertext Transfer Protocol Secure (HTTPS)**. The Web server receives a message from the inbound port in the form of a request that includes a **uniform resource locator (URL)**. The URL contains information for the Web server to know how to handle the request.

For example, suppose you are running a Web server at the address *[www.MicrosoftApplicationSecurityChapter12.com](http://www.MicrosoftApplicationSecurityChapter12.com)*. Your Web server may receive a URL that looks like this:

*[http://www.MicrosoftApplicationSecurityChapter12.com/scripts/wsisa.dll/WService=catlookup?isbn=076372677X](http://www.MicrosoftApplicationSecurityChapter12.com/scripts/wsisa.dll/WService=catlookup?isbn=076372677X)*

[Table 12-4](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12tab4) describes the individual parts of a URL.

The Web server receives the message and evaluates the Web server command. The Web server command tells the Web server what to do. If your Web server executes a command without taking any precautions, any anonymous user can tell it to do many malicious things, such as return private data, delete files, or shut down the server. Any of these actions would violate the server’s security.

Since you don’t want any Web server blindly executing commands, you need to restrict what the Web server accepts and what it can do. Make a Web server more secure by following a few simple strategies. [Table 12-5](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12tab5) lists some of the main strategies for securing any Web server.

The strategies in [Table 12-5](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12tab5) represent a few of the tasks necessary to fully secure a Web server. Since Web servers are often exposed to the Internet and provide an interface into your network, they are attractive targets. Make sure you spend the time securing each Web server you deploy.

| **TABLE 12-5** Strategies to secure a Web server. |
| **STRATEGY** || **DESCRIPTION** |
| Disable unused protocols/services. || Web servers can support many more protocols than HTTP and HTTPS. Each protocol gives attackers additional methods to compromise a server. If you don’t need a particular protocol, such as File Transfer Protocol (FTP), disable it in the Web server configuration and ensure the corresponding service is disabled as well. |
| Remove samples, help, and administration scripts. || Some Web servers install additional components you don’t need on a production server and may be vulnerable to attacks. |
| Disable scripts for types you don’t need. || Web servers recognize many different types of file extensions and will attempt to interpret scripts and programs it receives. Hackers use this knowledge to send attack scripts to exploit vulnerabilities. |
| Deny directory traversal and listing. || Stop Web clients from sending paths or commands that access resources outside the Web server path. Also, don’t let anyone see a directory listing of directories on your server. Criminals use information to plan more attacks. |
| Enable auditing of failed logon attempts and failed resource requests. || Auditing can provide information to identify attacks or reconnaissance on your Web server. |
| Put all Web content on a disk drive that is separate from the operating system or any private data. || Separating Web server files from system files and private data reduces the damage an attacker can do if your Web server is compromised. |
| Require secure connections for any private data exchange. || SSL/TLS connections encrypt traffic between the Web server and the Web browser, keeping messages private. |
| Use operating system access controls to limit access for Web users. || Operating system access controls can limit the objects any user can access, including Web users. |
| Disable any Web server authentication methods your application does not need. || Some Web server authentication methods, such as digest authentication, are vulnerable and should not be used. |
| Remove any unused encryption ciphers. || Many Web servers install several encryption ciphers to support as many types of encryption as possible. Remove any ciphers that are weaker than your minimum requirements. This stops clients from negotiating a weaker encryption algorithm with the Web server. |

**technical TIP**

You can add a role to a Windows Server 2008 R2 server from the Server Manager window. Follow these steps to add a new role to a server:

**1.** From the Windows desktop, choose Start > Administrative Tools > Server Manager.

**2.** Select Roles > Add Roles.

**3.** Select Next to see the roles you can add to the current server.

**4.** Check the Web Server (IIS) box and choose Next.

Microsoft’s Web server, Internet Information Services (IIS), has long been a familiar component in Windows environments. The latest version of IIS that ships with Windows Server 2008 R2 or Windows Server 2012 represents Microsoft’s most secure Web server to date. Microsoft learned many lessons from previous versions of IIS and made the latest version secure from the beginning. If you take the time to install IIS with only the options you need, it doesn’t require much additional work to create a secure Web server.

**FIGURE 12-2** Add Roles Wizard for adding Web Server (IIS) role to Windows Server 2008 R2.

![image](OEBPS/Images/9781284031652_pg292.jpg)

**FIGURE 12-3** Select Role Services for adding Web Server (IIS) role to Windows Server 2008 R2.

![image](OEBPS/Images/9781284031652_pg293.jpg)

The starting point for installing IIS is a Windows Server 2008 R2 or Windows Server 2012 server. Install IIS to a standard Windows server or a Windows Core Server installation. You’ll learn about adding IIS to a standard server in this chapter. You install IIS by adding an additional role to the server.

[Figure 12-2](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12fig2) shows the Add Roles Wizard windows for adding the Web Server (IIS) role to Windows Server 2008 R2.

Notice in [Figure 12-2](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12fig2) that Windows provides several resources to help you add IIS to your server. Read through an overview of the new role services Microsoft introduced in IIS starting with version 7.5. These services allow you to pick and choose just the services your Web server needs to run your Web sites and applications. This saves you the time and effort of having to disable unneeded services after installation. Microsoft also provides detailed checklists to help you install IIS with the features and security you want. After reviewing the help and documentation, proceed to the role services selection window.

[Figure 12-3](#23_Chaper12_split_001.xhtml#ba-9781284031652-ch12fig3) shows the Select Role Services window for adding the Web Server (IIS) role to Windows Server 2008 R2.

Windows lets you select the services your Web server will need before it installs anything. This is the step that can make your Web server lean and secure. Carefully review each selection before checking any box. Once you have all of the desired services selected, continue installing IIS. Although IIS installs in a fairly secure state, you should still review the server and the Web server software to ensure the highest level of security possible.

E-mail Server

Another common server you’ll find in many organizations is an e-mail server. Microsoft’s e-mail server is Microsoft Exchange Server. An e-mail server provides e-mail services to clients. Clients connect to the e-mail server and either receive e-mail messages from the server or send e-mail messages to the server. One connection could include both operations. Clients can either download messages to read locally or read messages directly from the e-mail server. If you allow it, each client can choose between remote or local message storage.

When considering e-mail server security, cover all three properties of the C-I-A triad. Your e-mail server must be available. One of the most frustrating situations for users to encounter is an e-mail server that is unavailable. E-mail is such an integral part of daily tasks that access to it is expected. Your e-mail server must also ensure private messages are private and no message changes in transit. While the confidentiality and integrity properties are important for some messages, the overhead generally doesn’t warrant securing all messages.

It is important to secure all e-mail that is stored on your e-mail server. Your e-mail server may store messages for very short periods of time or for months, or even years. Double-check that both your e-mail server software and the operating system protect e-mail message data using file, folder, or drive encryption. Since many people rely on the practice of storing e-mail messages on the e-mail server, have a solid disaster recovery plan (DRP) and business continuity plan (BCP). These plans protect your e-mail in case of data loss.

Unlike IIS, Exchange Server is a separate commercial product. Once you purchase a license, you can acquire and install Exchange Server on your Windows Server computer. During installation, you specify many of the characteristics to secure your e-mail server. Exchange Server 2010 allows you to select from several roles that define whether the server will store messages, provide client access to messages, transport messages to other e-mail servers, or even perform a combination of roles. The specific role your e-mail server plays tells the installation process how to configure the software for the most functionality and highest security.

An e-mail server must deal with several vulnerabilities to support secure e-mail exchange. When securing an e-mail server, address these issues:

• **Limit operating system logons and administrator rights**—Only a limited number of user accounts should have administrator access to the e-mail server computers.

• **Enforce strong e-mail user authentication**—Require strong authentication for all e-mail clients.

• **Use encrypted connections for all communication between Exchange servers**—This is the default behavior.

• **Enable only the protocols your e-mail clients require**—Post Office Protocol version 3 (POP3) and Internet Message Access Protocol 4 (IMAP4) are older protocols and are disabled by default. Enable them if necessary, but Exchange allows these connections only if they are encrypted.

• **Patch all Exchange Server instances**—Frequently check for security updates and install them to all your Exchange servers.

• **Use anti-malware software on each server**—Microsoft Forefront is one enterprise solution.

• **Encrypt folders or drives that store e-mail messages**—Use Encrypting File System (EFS) or BitLocker.

• **Plan for high availability**—Develop a solid BCP and DRP that ensure maximum uptime.

E-mail servers are frequent participants in spreading malware. Good anti-malware software, along with strong access controls, can reduce the potential for your e-mail server spreading malware. Requiring encryption of all connections will greatly increase the overall security of messages exchanged within your organization. Remember that messages that travel outside your organization are not encrypted by default. It is the responsibility of the e-mail clients to agree and encrypt messages. Microsoft Exchange Server goes a long way toward ensuring your e-mail messages are as secure as possible.

Database Server

Nearly every application needs some type of stored data on which to operate. Some applications use their own internal data storage techniques. The majority of applications use separate database management products to store data. Application developers write application software that interfaces with one or more databases to maintain the data each application needs. Today’s databases are getting larger. It is not uncommon to see database sizes in excess of many terabytes. As applications rely on database management systems more and more to provide access to data, organizations are isolating databases on separate servers. These specially configured database servers are efficient platforms for applications and attractive targets for attackers.

Database management systems routinely store application data for rapid and secure retrieval on demand. Databases can store private and public data. They handle each type of data differently. Separating all of an organization’s data to a database server gives the organization greater control over how to secure that data. Securing a database, like securing any other server software, depends on a secure operating system first. After the basic security needs of the underlying platform have been addressed, databases can help ensure the confidentiality, integrity, and availability of stored data.

Current database management systems have several options and strategies to provide maximum availability. Take frequent backups, archive transactions logs, or implement data replication. Most current database products also provide configuration options that are specific to high availability. One configuration option is using failover clustering to protect from hardware failure. Regardless of the options you choose, research your database management system’s capabilities and deploy the configuration that fits your budget and provides the greatest availability.

The ability of a database management system to provide confidentiality and integrity depends on the quality of the authentication, access controls, and query preprocessing. First, use strong authentication for all database queries. In the database world, a **query** is any statement that accesses data. A query can read, write, create, or delete data. Each query requests access to data on behalf of a specific user or process. Enforce unique user accounts and strong authentication. Legacy database applications often allowed generic user accounts that multiple users shared. While this practice is acceptable for public data, it is not acceptable for databases that contain sensitive data. Do not allow this practice for databases that contain sensitive data. Each user should have a unique account. Unique user accounts make it possible to grant access privileges to specific users and audit activity more precisely. Just as with hardening the operating system, require the strongest authentication method your clients support.

The next security property is confidentiality. Database management systems use encryption to support confidentiality. To make database access as secure as possible, enforce encrypted connections any time you transfer private data. You can enforce this using VPNs or individual connection encryption. Make sure no private data is transmitting in the clear.

![image](OEBPS/Images/war.jpg)**WARNING**

If your organization deploys a distributed application, make sure all connections from the client to the database are encrypted. Many applications force secure connections just from the client to the Web server. While this strategy protects data transmitted across the Internet, data is decrypted and transmitted in the clear from the Web server to the application servers and database servers. Encrypt all connections.

Databases also use encryption to store data. Data at rest has several different encryption options. This list of options includes:

• **EFS or BitLocker**—While encrypting a file, folder, or volume does store data encrypted, most database administrators prefer more control over what gets encrypted. Encrypting data at the operating system level may lead to far more data being encrypted than what an organization needs.

• **Transparent Data Encryption (TDE)**—Current database management systems generally offer an option to encrypt either selected database objects or even an entire database. **Transparent Data Encryption (TDE)** encrypts all data without requiring any user or application action.

• **Application encryption**—The most fine-grained control is for the application to decide what data to store encrypted and carry out the encryption process directly. This last option provides the most control over encrypted data but at the cost of substantial software development effort.

The last major security property that database management systems protect is data integrity. Although database vendors go to great lengths to ensure internal data integrity, integrity in a security context has a slightly different meaning. To support both confidentiality and integrity, database management systems make certain that no unauthorized user can view or modify data. To enforce these two properties, the database management system must know the identity of the user who submitted the query. Positive identification and authentication provide a trusted user account. The next step is to authorize a user to carry out a data operation. Most of the commercial database management systems support the **Structured Query Language (SQL)** to access data in a database. SQL defines a security model that grants or revokes access privileges to specific pieces of data. The database management system evaluates each field, or column of data, based on the permissions defined for the current user.

SQL security is quite good. The problem is that it can be cumbersome to manage. SQL security is based on users, and granting data access to anonymous users can allow anyone to access your data. As long as you have unique user accounts, you can secure data in your database at a very detailed level. Doing so requires substantial effort in verifying that all permissions are current and accurate.

One common problem arises with storing secure data in a database. Most database products interpret SQL queries at run time. In other words, the query statement isn’t evaluated until it is time to execute the statement. Many attackers have learned how to trick the database query processor into doing more than intended. It is possible to add SQL statements to input data, and if an attacker is crafty and careful, he or she can make a database server respond to nearly any command. Adding SQL statements to data for the purpose of sending commands to a database management system is called **SQL injection**.

The best defense against an SQL injection attack is to validate all input before sending it to the SQL query processor. Have your client application validate each input field to ensure it meets your input standards, but make your server validate input as well. Recall that man-in-the-middle attacks sometimes use proxy servers. They also use these servers in injection attacks. If an attacker can intercept network traffic, he or she can also modify the traffic. That means a computer criminal can modify any data that already passed validation on the client. For that reason, never trust data from a client—always validate all input on the server. By validating all input, your database server can detect and remove illegal input such as injected SQL statements.

Keeping all these points in mind, here are the general steps to securing a database server:

• **Secure the operating system**—Always start with a secure operating platform.

• **Install the latest patches**—Check that you have the latest security patches and develop a plan to acquire and install all released patches.

• **Require strong authentication**—Require authentication of all users before processing a query and force the strongest authentication method your clients can support.

**Let Microsoft Handle Your Database**

Microsoft offers another option for organizations that use Microsoft SQL Server. Microsoft SQL Azure provides SQL Server database services as a subscription. Your database no longer resides in your environment but resides and is managed in Microsoft’s cloud environment. The advantages to this approach are that Microsoft handles all of the patching, high availability, and basic security tasks for you. You can find more information on Microsoft SQL Azure at *[http://www.windowsazure.com/en-us/home/features/data-management/](http://www.windowsazure.com/en-us/home/features/data-management/)*.

• **Use separate user accounts for database administration**—These are separate system administrators, database administrators, and database user accounts.

• **Install only necessary components**—Do not install database services or components you don’t need. Review the installation process and remove unneeded components.

• **Remove or disable default users**—Most database management systems install default user accounts. Attackers know which default users exist in most databases. Remove or disable all of these default accounts.

• **Use auditing**—Enable auditing for failed logon attempts and possibly access to critical data. Be aware that auditing any data access can create a large number of log entries.

• **Change default ports**—Never use the default ports to access database services. Attackers know these default ports. Select alternate ports for all database accesses.

• **Revoke any developer access to production environments**—Developers should have access only to development and testing environments.

• **Encrypt private data**—Select an encryption method that secures private data.

• **Develop and maintain plans for business continuity and disaster recovery**—Plan for disruptions and know how to minimize your downtime.

• **Validate all input**—Never evaluate a database query without validating the query first to ensure that no extra data is in the query.

• **Monitor performance**—Monitor how well the database is executing queries and be prepared to respond if performance degrades.

These steps will help you create a database environment that supports your data’s security.

ERP Software

**Enterprise Resource Planning (ERP)** software is an integrated collection of software programs. It manages many aspects of a business, including finances, human resources, assets, and business processes. ERP software generally serves to unite different users and organizational units by sharing and combining data. ERP software provides centralized data storage and functional software capabilities that streamline business processes.

The security concern of ERP software is that a large portion of an organization’s data is centralized. Most, if not all, of the users in the organization access the ERP software as part of their normal business function. That means many users have access to the application and the database. Each software vendor provides specific recommendations for its product, but many strategies to secure ERP software are common among vendors. Follow these guidelines to secure any ERP software application:

• **Create unique user accounts**—Securing shared data depends on uniquely identifying users. Don’t allow users to share accounts.

• **Enforce strong authentication**—Since data security depends on user- or group-based authorization, choose the strongest authentication type your application allows.

• **Restrict access to application components**—Use application security options to restrict function access by user or group.

• **Develop ERP acceptable use policy (AUP)**—Develop acceptable use policies for the ERP software. Train all users on current AUPs.

• **Secure workstations**—Follow recommendations for securing any workstation that accesses your ERP application.

• **Require encrypted connections**—Require secure VPN or other encrypted connection to access the ERP application.

Line of Business Software

ERP applications address mostly generic business needs. Some organizations have specific business processes that are unique to their market or organization. Many organizations either develop or acquire specialized application software to help them conduct business. Software applications that are specific to a particular process in an organization are called line of business (LOB) software. For example, line of business software can include any of these applications:

• Enterprise project management

• Workflow control

• Service technician tracking and scheduling

LOB software isn’t necessarily unique to an organization, but it isn’t needed by all organizations. The security concerns are the same ones as with ERP applications. The workforce depends on the application’s operation and the data’s security. The application must be available, responsive, and dependable. Follow the same recommendations as in the ERP application section, and you’ll have a secure LOB application.

**Case Studies in Microsoft Application Security**

When learning new concepts, it often helps to see examples. The best examples are real-life examples. In this section, you’ll learn about three real-life organizations that encountered IT security issues and solved them in a Microsoft Windows environment. These examples show that few problems have quick fixes and are often related to other issues. All security problems take time and effort to resolve. Here is how three organizations resolved their challenges.

Sporton International

Sporton International is based in Taiwan. It certifies hardware devices that use electromagnetic current, including computers and mobile phones. Sporton provides certification and testing services for IT leaders such as Apple, HP, and Nokia. The company has access to its customers’ sensitive trade secrets and product prototypes and must ensure that these remain secure. To safeguard customers’ data, Sporton worked toward more complete documentation and control of its security infrastructure. It deployed Microsoft Forefront security products, which work with the Microsoft products Sporton was already using, to manage risk and empower people across the enterprise. Using a product that integrated with Microsoft applications already in use lowered software licensing costs by at least US$15,000 a year. The company now automatically enforces security compliance, proactively blocks noncompliant e-mail messages before an attacker can compromise data, and uses reporting and documentation features to more easily meet security regulations.

Sporton demonstrated that changing software isn’t always the best answer. In its case, Sporton was able to add an additional layer of software, Microsoft Forefront, which maintained the company’s existing integration and provided the documentation it required. One of the features of Microsoft Forefront is advanced anti-malware protection for an enterprise. This feature protects all application software from potential infection.

Monroe College

Monroe College is a private college with its main campus in New York City. It has two additional campuses in New Rochelle, New York, and St. Lucia. The college offers degrees in a variety of professional career-oriented areas of study. It has an IT staff of 30 full-time professionals who are responsible for maintaining and protecting more than 1,800 computers, 70 physical servers, and 100 virtual servers. They are also in charge of providing secure college network access for students, who bring their own laptops and mobile devices to the campuses.

The IT staff tried two previous solutions to manage the security of their computers. The first attempt didn’t properly secure the desktop and laptop computers and left them vulnerable to Internet viruses and spyware. These infections resulted in multiple outages and much downtime. The second product reduced the number of outages but was difficult to maintain. The Monroe IT group had to struggle to keep security updates current. On the third attempt, Monroe College turned to Microsoft Forefront Client Security. Since installing Microsoft Forefront Client Security, Monroe College has experienced no disruptions resulting from a virus or malicious software. The IT staff also has Microsoft Forefront at its disposal to simplify system administration to make software updates easy to deploy.

Dow Corning

Dow Corning is a global chemical manufacturer that is jointly owned by the Dow Chemical Company and Corning. Dow Corning provides more than 7,000 silicone-based products and serves more than 25,000 customers worldwide. More than half of the company’s annual sales are outside the United States.

Dow Corning’s goals were to consolidate and extend identity management workflows. The company also needed to move toward a more secure, well-managed, and dynamic core IT infrastructure capable of protecting their sensitive data as it moved through e-mail and collaboration systems. Dow Corning planned to migrate its e-mail infrastructure to Microsoft Exchange Server 2007 but was unable due to restrictions in its existing provisioning scripts. Dow Corning decided to deploy Microsoft Forefront Identity Manager 2010 to replace custom user provisioning scripts that could not support the upcoming migration to Microsoft Exchange Server 2007 or additional Active Directory domains. With Forefront Identity Manager 2010, the company should increase efficiency through password synchronization and reduce work for the help desk staff. As of this writing, Dow Corning also plans to extend messaging and collaboration beyond the enterprise to business partners, who will also be supported by the Microsoft identity-based access solution.

**Best Practices for Securing Microsoft Windows Applications**

A little research on securing applications will yield many resources. You can find tutorials, how-to guides, and complete reference works with detailed instructions to follow. While there are many details necessary to make your applications as secure as possible, several general guidelines will address the most important security needs.

Although each application and each organization is different, they all share common strategies to establish good security controls and foil attackers. The following recommendations come from practical experience with many organizations and applications. They are the strategies that produce the best results. These best practices will help you establish a solid foundation for securing your applications:

• Harden the operating system first.

• Install only the services necessary.

• Use server roles when possible.

• Use SCW to apply least privilege principle to applications.

• Remove or disable unneeded services.

• Remove or disable unused user accounts.

• Remove extra application components.

• Open only the minimum required ports at the firewall.

• Define unique user accounts.

• Use strong authentication.

• Use encrypted connections for all communication.

• Encrypt files, folders, or volumes that contain private data.

• Develop and maintain a BCP and DRP.

• Disable any unneeded server features.

• Ensure every computer has up-to-date anti-malware software and data.

• Never open any content or files from untrusted sources.

• Validate all input received at the server.

• Audit failed logon and access attempts.

• Conduct penetration tests to discover vulnerabilities.

These best practices apply to most server applications and ensure you are protecting your data at the server level.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Securing applications is an integral part of an overall security plan. The most secure environment is not very secure if the servers aren’t hardened as well. Attackers know that servers store an organization’s valuable data and the programs that manipulate that data. Your servers will be targets. Your clients will be targets, too. In many cases, attackers will attempt to compromise clients to get to your servers. Have a plan for foiling assaults at both the client and server levels. That plan should start with hardening your applications to make them as secure as possible.

In this chapter, you learned how to secure several types of application software. You found out how to secure both client and server applications and why each one is important. You also reviewed best practices that will provide a solid foundation for a secure application environment.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Application software**

**Enterprise Resource Planning (ERP)**

**File Transfer Protocol (FTP)**

**Hypertext Transfer Protocol Secure (HTTPS)**

**Man-in-the-middle attack**

**Privilege escalation**

**Query**

**Spoofing**

**SQL injection**

**Structured Query Language (SQL)**

**Transparent Data Encryption (TDE)**

**Uniform resource locator (URL)**

**Zombie**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 12 ASSESSMENT**

  **1.** The main focus when securing application software is confidentiality.

A. True

B. False

  **2.** Which type of application attack attempts to add more authority to the current process?

A. Privilege spoofing

B. Identity escalation

C. Privilege escalation

D. Identity spoofing

  **3.** Which of the following is the best first step in securing application software?

A. Install all of the latest patches.

B. Harden the operating system.

C. Configure application software using least privilege.

D. Perform penetration tests to evaluate vulnerabilities.

  **4.** A \_\_\_\_\_\_\_\_ is an attractive target because it is the primary client of Web applications.

  **5.** Why are ActiveX controls potential security risks?

A. ActiveX controls can contain malware and run on the client.

B. ActiveX controls can contain malware and run on the server.

C. ActiveX controls require that you divulge sensitive authentication details.

D. ActiveX controls are outdated and generally used by older Web applications.

  **6.** Enabling secure connections ensures e-mail messages are encrypted between sender and recipient.

A. True

B. False

  **7.** Which of the following is a simple step to make e-mail clients more secure?

A. Use EFS/BitLocker to store e-mail messages on the server.

B. Install third-party message encryption.

C. Turn off message preview.

D. Remove e-mail clients and use server-based e-mail access.

  **8.** Which of the following steps can increase the security of all application software?

A. Install anti-malware software.

B. Use whole disk encryption on client workstations.

C. Run SCW on workstations.

D. Require SSL/TLS for connections to a Web server.

  **9.** You use Windows server roles to configure each Windows server computer to perform only one task.

A. True

B. False

**10.** A URL can contain commands the Web server will execute.

A. True

B. False

**11.** How do you install IIS on a Windows Server 2008 R2 computer?

A. Purchase IIS and install it.

B. Download IIS for free and install it.

C. Add the Web Server (IIS) role to a server.

D. Install IIS from the Windows install DVD.

**12.** A \_\_\_\_\_\_\_\_ is any statement that accesses data in a database.

**13.** \_\_\_\_\_\_\_\_ encrypts all data in a database without requiring user or application action.

**14.** SQL injection attacks are possible only against popular Microsoft SQL Server databases.

A. True

B. False

**15.** Is requiring secure connections between your Web server and your application server worth the overhead and administrative effort?

A. No, because both the Web server and application server are inside your secure network.

B. Yes, because your Web server is in the DMZ and is Internet-facing.

C. No, because secure connections between high-volume servers can dramatically slow down both servers.

D. Yes, because your application server is in the DMZ and is Internet-facing.

**CHAPTER 13**

**Microsoft Windows Incident Handling and Management**

DESPITE THE BEST EFFORTS to secure a computing environment, no organization is completely safe. Sooner or later you will encounter a security policy violation. It may be a minor violation such as a user attempting to log on too many times after forgetting a password. Or it could be a major incident such as an attacker destroying your organization’s primary database. Either way, learn how to react. When you discover a security violation, you have only one proper response—to follow your plan.

Map out your response to security violations before any occur. In this chapter, you’ll find out how to plan for the inevitable actions that result in security violations. You’ll learn how to recognize violations and how to develop a plan for handling each one. You’ll study up on the Microsoft tools available to collect information and manage a response process. Some violations are more severe and may result in law enforcement involvement or litigation. In this chapter, you will also learn the right ways to collect and protect evidence that is admissible in court.

**Chapter 13 Topics**

This chapter covers the following topics and concepts:

• How to handle security incidents involving Microsoft Windows operating system (OS) and applications

• How to formulate an incident response plan

• How to handle incident response

• What incident handling and management tools are available for Microsoft Windows and applications

• How to investigate Microsoft Windows and applications incidents

• How to acquire and manage incident evidence

• What the best practices are for handling Microsoft Windows OS and applications incidents and investigations

**Chapter 13 Goals**

When you complete this chapter, you will be able to:

• Describe Microsoft Windows OS security incidents

• Use available tools to handle and manage security incidents

• Investigate incidents, including acquiring and managing evidence

**Understanding and Handling Security Incidents Involving Microsoft Windows OS and Applications**

A security policy is a description of how an organization defines a secure computing environment. It is a collection of rules that define appropriate and inappropriate behavior. Once an organization deploys controls to govern behavior, it’s helpful to devise a method to measure how effective the controls are. All activity in a computing environment is made up of individual events. An **event** is any observable occurrence within a computer or network. An event could be a user logging on, an application server connecting to a database server, an authentication server rejecting a password, or an antivirus scanner reporting a suspected virus. Any event that results in a violation of your security policy, or poses an imminent threat to your security policy, is an **incident**.

The first step in responding to an incident is to recognize that an incident has occurred. Many incidents go unnoticed because no one is looking for them. It’s common to review operating system and application software log files after a major incident, such as data loss or a system failure. In some cases, there is evidence of smaller incidents leading up to the big event. Many organizations lack the procedures to identify incidents early. Like any persistent problem, identifying incidents in a timely fashion can help contain any damage and prevent further damage.

The adage, “An ounce of prevention is worth a pound of cure,” applies to incidents. The best way to avoid handling incidents is to prevent them. Securing computers and network devices is better than dealing with security incidents. The only exception is when the cost of the controls is more than the loss you would incur if an incident did happen. Microsoft has a lot to say about handling incidents for Windows environments and recommends pursuing prevention first. According to Microsoft’s recommendations, these strategies can help any organization minimize the number and impact of security incidents:

• Develop, maintain, and enforce a clear security policy that management supports and promotes. A security policy defines incidents and behavior that lead to incidents.

• Conduct routine vulnerability assessments to discover vulnerabilities that could lead to incidents.

**Real-Life Incidents**

Security incidents can be disruptive to any organization. They end up costing a lot of money and time. The following are three examples of recent incidents that caused substantial damage to different organizations. Learn from these incidents. Take every opportunity to avoid being the next example:

• T.J. Maxx exposes 94 million credit card numbers and transaction details in 2007—*[http://datalossdb.org/incidents/548-hack-exposes-94-million-credit-card-numbers-and-transaction-details](http://datalossdb.org/incidents/548-hack-exposes-94-million-credit-card-numbers-and-transaction-details)*.

• T-Mobile loses a disk containing customer information for 17 million customers in 2008—*[http://datalossdb.org/incidents/1172-t-mobile-lost-disk-containing-data-on-17-million-customers](http://datalossdb.org/incidents/1172-t-mobile-lost-disk-containing-data-on-17-million-customers)*.

• Heartland Payment Systems loses millions of credit card payment records in 2009—*[http://datalossdb.org/incidents/1518-malicious-software-hack-compromises-unknown-number-of-credit-cards-at-fifth-largest-credit-card-processor](http://datalossdb.org/incidents/1518-malicious-software-hack-compromises-unknown-number-of-credit-cards-at-fifth-largest-credit-card-processor)*.

If you doubt the impact one security incident can have on an organization, visit the Web sites above and look at the stock prices for each organization after each incident.

• Ensure all computers and network devices have the latest available patches installed.

• Train all computer system users on acceptable and unacceptable behavior. Establish frequent and visible security awareness reminders. Use both physical and virtual methods to notify and remind users.

• Enforce strong passwords throughout your environment.

• Frequently monitor network traffic, system performance, and all available log files to identify any incidents or unusual events. The first logs you’d likely analyze would be logs from your intrusion detection system or intrusion prevention system.

• Ensure you have a solid business continuity plan (BCP) and disaster recovery plan (DRP) that you test at least annually. A serious incident will likely require that you enact one or both of these plans.

• Create a **security incident response team (SIRT)**. The SIRT is a team organized to respond to incidents.

**technical TIP**

Find more information on Microsoft’s recommendations for handling incidents on the Microsoft TechNet Web site. The incident-handling article is at *[http://technet.microsoft.com/en-us/library/cc700825.aspx](http://technet.microsoft.com/en-us/library/cc700825.aspx)*.

All of the suggestions in the previous list are really just elements of good security. These are things you should be doing already to maintain a secure environment. The last suggestion, create a SIRT, is specific to handling incidents. This is the team of people who will respond to any incidents. There are six separate steps to handling incidents. Understanding and following all six steps will help you avoid many incidents and prepare your SIRT to handle the ones that do occur. [Table 13-1](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13tab1) lists the six steps for handling incidents.

The most important aspect of properly handling incidents is preparing to do it right. Once you understand what it takes to respond well to security incidents and have your SIRT in place, you are ready to begin developing your response plan.

| **TABLE 13-1** Six steps to handling incidents. |
| **STEP** || **DESCRIPTION** |
| Preparation || In this step, you create and train the SIRT; develop plans for handling incidents; assign roles and responsibilities; and assemble any supplies, hardware, and software you’ll need. In short, most of your time is spent in this step so you’ll be ready to respond when an incident occurs. |
| Identification || When you suspect that an incident has occurred, validate it, then identify the type and if possible, the source. You’ll respond differently to a Web site defacement than to a compromised database encryption key. |
| Containment || Once you have identified the type of incident, the next step is to contain the damage the incident has caused or is causing. Incidents are often not single events, but processes that can continue to cause damage. It is important to take action to limit the amount of damage to as small a scope as possible. This may require removing an affected computer from your network or other actions to keep the damage from spreading. |
| Eradication || Once the damage is contained, remove the vulnerability that allowed the incident to occur. This may involve configuration changes, software updates, or physical modifications. Eradicating an incident includes deploying any new or modified controls to ensure the incident does not happen again. |
| Recovery || The recovery step includes the actions necessary to return any affected systems to an operational state. Recovery actions will likely be driven by your BCP and DRP. |
| Lessons learned || One of the characteristics of a good team in any endeavor is that they continually learn and improve. The step that will improve long-term security is to document the lessons learned. The team should review their performance in handling the incident and make any changes necessary to the response plan to make the next response even better. |

**Formulating an Incident Response Plan**

The only way to respond to incidents in a predictable manner is to follow a well-documented plan. Your strategy for responding to incidents should be one that applies to many different types of incidents. Continually improve this plan. A solid incident response plan standardizes the SIRT’s actions and makes each incident response predictable and repeatable.

Plan Like a Pilot

Trying to respond to incidents without a plan is like piloting an airplane without any checklists. Even pilots of small aircraft use several checklists for each flight. Just a few used by pilots of small aircraft include pre-flight, engine start, post-engine start, taxi, run-up, pre-takeoff, and post-takeoff.

Those are the checklists just to get into the air! Since most aircraft incidents and accidents are caused by poor planning, it makes sense to plan well. Checklists are very important to pilots because it is easier to follow a well-documented checklist when things are hectic than it is to remember every important detail. Pilots also carry checklists for emergencies, such as an engine out or fire in the cockpit. At those times, they won’t want to try to figure out what to do. Those are the times to react efficiently and calmly.

Plan for Anything That Could Cause Loss or Damage

The first step in properly responding to a security incident is to prepare. By the time an incident occurs, it is too late to get organized. The preparation step includes building the SIRT and developing a response plan. Preparing also includes assembling any supplies, software, and hardware your team will need to respond to an incident.

Your organization should invest the resources to develop checklists and complete plans to address the results of each likely incident. It will require substantial effort to plan for every likely incident, but focusing on those that could cause loss or damage will be worthwhile. Many SIRTs discover existing vulnerabilities while developing response plans. You may find problems you can address just by planning for incidents. The greatest reason for preparing for incident response is that your team can decide on the best course of action for each incident when there is time to really think through the alternatives. You probably won’t have much time to consider alternatives during an incident. A plan increases the possibility your team can contain the damage and prevent further problems.

When developing your plan, consider every type of incident that can cause unacceptable damage. One way to develop a complete incident response plan is to think of as many incidents as possible and rank them by importance. Base your rankings on probability and severity. The most important incidents are those that are most likely to occur and would have the greatest impact on your organization. Those are the incidents to prioritize if your budget doesn’t allow developing a plan for all identified incidents.

| **TABLE 13-2** SIRT roles. |
| **ROLE** || **DESCRIPTION** |
| Team lead || Leader of the SIRT and the primary point of contact for all SIRT issues. |
| Incident lead || Member of the SIRT assigned to lead activities for a specific incident. Medium and large organizations may routinely need to respond to multiple incidents simultaneously. |
| IT liaison || Point of contact for communicating with the IT department. Even though there will likely be IT department members on the SIRT, having a single point of contact makes communicating easier. Primary responsibilities include communicating SIRT activities to IT and keeping everyone aware of how incident response actions might impact IT operations. The IT liaison also helps identify the IT expertise and resources needed to respond to incidents. |
| Legal representative || Generally an attorney who specializes in law related to security incidents. The legal representative advises the SIRT on incident-handling methods that minimize the organization’s legal liabilities. The legal representative will also communicate with law enforcement as needed and address evidence-handling procedures to maintain admissibility. |
| Public relations representative || Person responsible for communicating with the media and customers regarding incident-related events. The main goal for this role is to protect the organization’s reputation. |
| Management || Person with ability to authorize team activities. Without solid support from management, the SIRT will not have the authority or resources to be successful. |
| Subject matter experts (SMEs) || As the name implies, SMEs are experts in at least one area. For example, your team may need a network security SME, a malware SME, and an application security SME. One person may fill multiple roles. SMEs may be full team members or you may just consult with them as needed, especially during the planning phases. |
|   ||   |

Build the SIRT

The first step is to identify and assemble the SIRT members. A good plan includes input from all team members. Have your initial team in place before you begin developing the plan. The SIRT is the group that mobilizes to respond when incidents occur. The team should contain all of the members who will authorize, conduct, and communicate every incident response activity. A good way to ensure you have the right team members is to define the roles your SIRT must fulfill. [Table 13-2](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13tab2) lists the SIRT roles.

The first team members to assign to your SIRT are the management representative and the SIRT leader. These assignments originate with the team’s sponsor. The sponsor is a member of your organization’s management who has the authority to create and fund a SIRT. The management representative can be the team’s sponsor or another member of management. Once the team has management support and a lead, you can start to fill the other roles on the team.

After the initial team is in place, begin planning. Depending on the team’s existing knowledge of security incident response, you may need to provide some training on the subject. The idea is to give team members enough of a foundation in incident response that they are prepared to develop your initial plan.

Plan for Communication

Before you start to develop checklists for each specific type of incident, take the time to plan the framework. Your SIRT should handle all incidents in the same way. The severity of incidents will change some of the team’s responses. However, the overall manner in which the team responds should be consistent across incidents. You achieve consistent behavior by developing a response framework. One crucial part of your response framework is your plan for communication. A simple plan for communicating SIRT actions can reduce overall tension during an incident and may contribute to a successful incident resolution.

Your plan for SIRT communication should include sections for each of the following topics:

• **Contacts and hierarchy**—Include a list of every internal and external stakeholder in your information system environment. Identify areas of interest for each one. This list should also include media contacts. Store this information in a database or spreadsheet to make it easy to query and sort. Storing areas of interest can cut down on the number of people in the communication chain when efficient communication is important. For example, assume the SIRT is responding to a Microsoft update that causes remote client computers to crash. Remote users are very interested in this incident but database administrators are not as interested. On the other hand, an incident resulting from corrupted data in the central application database would be of interest to database administrators and remote users. Also include in this section any hierarchy of indirect communication if you use multiple points of contact to distribute information.

**technical TIP**

TechRepublic uses Identify/React charts to document many types of malware. The charts contain step-by-step instructions on both identifying a specific type of malware and how to react to it. This format lends itself well to many SIRT tasks. You can find a sample Identify/React chart for the Sober.I/Sober.J worm at *[http://www.techrepublic.com/i/tr/downloads/netadmin/resource\_doc/sober-chart.pdf?tag=content;siu-container](http://www.techrepublic.com/i/tr/downloads/netadmin/resource_doc/sober-chart.pdf?tag=content;siu-container)*.

**technical TIP**

Be creative and responsive when communicating SIRT activities. Most important, know your audience. If your organization is largely made up of tech-savvy employees, you may find that sending tweets is a very effective strategy to release status updates that don’t contain any confidential or sensitive content.

• **Responsibilities**—Descriptions of SIRT communication responsibilities include press releases, incident notifications, updates, and resolution notification. This section assigns the responsibility for each type of communication to avoid finger pointing.

• **Frequency expectations**—This section states the expected frequency of communication based on incident severity and type. Critical incidents require updates at least every 15 to 30 minutes while minor incidents may only warrant daily updates. The incident’s severity in the initial notification lets stakeholders know when to expect an update. Consider your audience as well when determining update frequency. You’ll likely keep management more up to date than the press.

• **Methods**—This section informs stakeholders of how the SIRT will communicate with them. Avoid frustration by ensuring everyone knows where to find messages that relate to incidents. Options include e-mail, Web site status pages, social media methods, and physical signs or banners. This section also includes plans for secondary communications in the case of severe incidents. A fully prepared SIRT would likely have radios to communicate when all other methods fail.

Plan Security

When an incident occurs, the SIRT responds to it in the manner prescribed in the incident response plan. In other words, the team follows the plan. Make sure your team has access to the plan. Ensure the team can retrieve the most current version of the plan regardless of the circumstances. Have multiple copies available in different formats stored in different locations. An incident that corrupts the document management system could make life difficult for your SIRT if the response plan is stored in the corrupt system. Part of your plan should ensure that the plan is available when needed.

A comprehensive plan will likely contain proprietary information. This information should only be available to authorized users. Likewise, only authorized users should be able to make changes to the plan. Unauthorized changes to the response plan could result in incorrect steps, making an incident worse. The best way to guarantee your response plan is available, confidential, and trustworthy is to consider the plan private and essential data. Then pursue controls to ensure the confidentiality, integrity, and availability (C-I-A) properties of data security that you’ve learned about.

Revision Procedures

Regardless of the effort invested to create your initial plan, you’ll encounter situations that require changes to it. You may have left some incidents or procedures out of the initial plan. You may also have discovered better methods for handling incidents. In any case, include a formal procedure to change the plan. In general, the whole team or an appointed group of team members should review any changes. They should then either approve or deny them. As long as you review all change requests and fully document any changes approved for the plan, you can continually make your plan better.

Also include formal periodic reviews in the plan. The entire team should review the response strategy at least annually. This periodic checkup ensures changes to the plan or changes to your environment haven’t weakened the team’s ability to respond to an incident.

Plan Testing

The final step in the recurring cycle of incident response planning is to test the plan. Regardless of how good your plan looks on paper, you won’t know how well it works until you try it out.

Simulated incidents test the plan and train your team. These simulations can be informal walk-throughs where team members talk through plan steps or more realistic simulations where the team responds with realistic actions. The more realistic simulations better train team members and reveal any plan weaknesses. Test your response as often as you can to ensure you’re ready when a real incident occurs.

**Handling Incident Response**

You learned earlier in this chapter that there are six steps to responding to a security incident. These steps are not purely linear. You may repeat some steps several times while responding to incidents. Each step is important because it isolates a specific area of concentration that you must address to respond well to any incident.

For simple incidents, several steps may be combined or are trivial. Regardless of an incident’s simplicity, however, each step is important. A solid incident response plan ensures a SIRT will address each step for all types of incidents.

Preparation

The first step in a proper incident response is to prepare for the incident. In other words, get ready for incidents before they occur. Taking the time to prepare to respond to an incident after it occurs likely will worsen the incident’s effects. Being prepared greatly increases the probability that you can respond to an incident in a positive, professional manner. If you have a comprehensive response plan, a complete and trained SIRT, and all of the supplies the team will need, you should be ready to handle incidents.

Identification

The main purpose of the identification step is to decide the next course of action. The first question is whether an incident has occurred at all. Many incidents go unnoticed while other events that are harmless are reported as incidents. Identifying incidents starts with a complete definition of what an incident is. In your plan, include procedures to identify incidents your security policy defines. Some events such as defacing a Web site are obvious incidents for any organization. Other events such as an attempt to use an incorrect password five times may or may not be an incident. Each organization’s security policy should contain enough details to decide whether any event is an incident.

Once you decide to implement a formal incident response, create a method to report suspected incidents and publicize the proper reporting steps. You could publish an incident reporting form on an intranet page, use an e-mailed form, or hard-copy forms. In some organizations, the help desk is the primary point of contact for incidents. Help desk personnel would likely be the ones to determine whether to refer an event to the SIRT. When this is the case, the SIRT should have a help desk representative as a member. The procedure you decide to use should be standard for your organization and should contain enough information to determine the next step. [Figure 13-1](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13fig1) shows a sample incident reporting form.

** ![image](OEBPS/Images/note.jpg)NOTE**

Your end user security training should encourage users to report any activity that could be an incident. For example, you want to know about social engineering attacks that do not succeed, as well as those that do. Keeping data on all attack attempts helps identify trends.

**FIGURE 13-1** Sample incident reporting form.

![image](OEBPS/Images/9781284031652_pg314.jpg)

Once you have an incident reporting form available for your users, train the person who might report a violation on the proper reporting procedures. The initial part of incident reporting training is to help users identify potential incidents. First, teach users how to find out if any scheduled maintenance or known issues are causing the events. If no known issues are present, users should report a potential incident if any of the following events occur:

• A password has been changed without their making the alteration.

• They are asked for their password or other private information by someone who does not have a need to know. This includes requests that users change their password to one an outside party supplies.

• They notice e-mail responses to messages they did not send, messages in their Sent Messages mailbox they didn’t send, or an increase in spam.

• Their Web browser home page changes, or they can’t close pop-up ads.

• They spot changes in the way their desktop appears when they log on.

• They can’t connect to servers they need to complete tasks.

• Noticeable increases in disk activity, network activity, or wait time to complete any task occur.

• New files or folders appear that they haven’t seen before.

Once users suspect that an incident has occurred, they should save their work, leave all applications open, and notify the SIRT using the published notification procedure. Users should leave the computer in its current state rather than shut it down or reboot. The SIRT will likely want to see what the computer is doing before making any changes to its configuration.

Once the SIRT receives the suspected incident report, it is assigned to a team member. That team member becomes the incident lead. The incident lead reviews the information and begins an investigation. The first step is to determine whether the report contains information about an incident or some other event. This is where you will rely on the technical expertise of your team members. If the incident lead validates the incident, the next activity is to determine the incident’s attributes. The three main attributes of an incident that direct subsequent action are:

• **Classification**—What type of incident is this? An incident’s classification tells the SIRT what actions to take. [Table 13-3](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13tab3) lists common suggested incident classifications.

• **Scope**—How many computers or users does this incident affect, and how long has the issue existed? Knowing the incident scope helps the SIRT determine if it needs more resources and how to handle communication.

• **Severity**—How bad is this incident? Setting the severity level helps the SIRT and management allocate resources efficiently. More severe incidents get higher priority and more resources as needed. [Table 13-4](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13tab4) lists suggested incident severity levels.

This step may also include notifying other parties, including law enforcement, of certain types of incidents. If your investigation produces evidence of illegal material, such as copyrighted material or child pornography, the law requires you to report it to the proper authorities. In such situations, the SIRT legal representative will provide the direction for the proper course of action.

| **TABLE 13-3** Incident classifications. |
| **CLASSIFICATION** || **DESCRIPTION** |
| Unauthorized access of a privileged account || An unauthorized user has gained access to a privileged account, either by an unauthorized logon or a privilege escalation. |
| Unauthorized access of a limited account || An unauthorized user has gained access to a limited account, either by an unauthorized logon or a privilege escalation. |
| Failed attempt to access any account || An attempt to log on or change user accounts has failed. |
| Unauthorized scan of one or more systems, or even users, as in social engineering queries || A port scan has targeted one or more computers or devices to collect information about the computers or devices. In the case of social engineering attacks, calling multiple users with the same request could be a process to identify potential victims. |
| Acceptable use policy (AUP) violation || A user action violates AUPs, including both accidental and malicious actions. |
| Denial of service (DoS) attack || An attack has resulted in a reduction or total denial of service. |
| Malware infection || Malware infection has occurred. |
| Hardware or software failure || A computer, device, or software error or failure not related to malicious activity has occurred. |
| Infrastructure failure || Any failure of supporting services and utilities, including power, HVAC, and communications, has occurred. |
|   ||   |

| **TABLE 13-4** Incident severity levels. |
| **SEVERITY** || **DESCRIPTION** |
| Severe || Potential long-term negative effects on an organization’s reputation or the ability to conduct critical operations. One or more critical systems have been compromised. An example would be discovering that an intruder extracted a large number of credit card numbers from your customer database. |
| High || Compromise of one or more noncritical systems or a verified threat of an imminent attack, such as the theft of a laptop that contained only sales presentation information. |
| Moderate || Verified threat of a future security incident, such as identifying infection of malware that triggers on a certain date and time. |
| Low || Indication of a potential future security incident, such as a port scan or multiple telephone calls from a person asking users to disclose information. |

Containment

The classification, scope, and severity attributes of an incident direct the containment activities. The main purpose of containment is to keep the incident’s scope from expanding. The specific steps you follow to contain an incident vary from one incident to another. The subject matter experts (SMEs) who participated in developing your incident response plan would have provided the technical details to contain each type of incident.

Steps you take to contain the damage an incident causes depend on several factors. Once you understand the current incident’s nature, the steps necessary to contain the incident should become clear. However, the steps will only be clear if your response plan includes steps to deal with the current incident. There is no substitute for having a comprehensive incident response plan that includes input from SMEs in several areas. The SMEs you use to help develop your incident response plan or carry out investigations don’t have to be SIRT members. The SIRT has the flexibility to use the best available resources for each investigation. The steps you take to contain incident damage may include some of the following actions:

• Disable networking services.

• Physically detach the computer or device from the network.

• Logically separate the affected computers or devices into a separate subnet.

• Turn off the computer or device.

• Terminate one or more programs or services.

• Remove software from the computer or device.

• Restore the computer or device to a previous state.

• Initiate appropriate communications to let interested parties know an incident’s status.

Regardless of the option your SMEs select, the most import consideration in the containment step is to keep the incident damage scope from expanding. Consider any incident to be like an infectious disease. Setting up a quarantine area can help keep the disease from spreading and making healthy people sick.

** ![image](OEBPS/Images/note.jpg)NOTE**

In October 2011, the Securities and Exchange Commission (SEC) issued official guidance on how publicly traded companies should report cybersecurity incidents. The SEC now mandates that publicly traded companies must report any cybersecurity incidents that could have a negative impact on their operations or financial status. Prior to this SEC guidance, reporting cybersecurity incidents was recommended but optional. See the SEC Web site for more information: *[http://www.sec.gov/divisions/corpfin/guidance/cfguidance-topic2.htm](http://www.sec.gov/divisions/corpfin/guidance/cfguidance-topic2.htm)*.

Eradication

Containment stops the incident damage from expanding. This allows you to remove the vulnerability that allowed the incident to occur in the first place. The steps you take will depend entirely on the incident’s nature and the course of action your SMEs recommend. In general, pursue the least intrusive course of action that will completely remove any vulnerability to prevent further incidents. Note that the eradication step doesn’t remove the incident’s effects—it just removes the vulnerabilities that allowed the incident.

Depending on the nature of the incident, the eradication step can include any of the following actions:

• Modifying firewall rules to close one or more ports or block IP addresses

• Installing operating system or application software patches or updated software

• Removing malware

• Providing targeted user training

• Removing or detaching hardware devices or device drivers

• Restricting remote access to deny offending computers

• Replacing or repairing failed hardware

• Firing a disgruntled employee and terminating his/her account access

IT SMEs will provide the best course of action to eradicate each type of incident.

Recovery

The final technical step is to return the affected computers or devices to a fully operational state. That means to restore the hardware, operating system, software, and data to a state that is usable in your environment. The incident’s severity and nature will direct team actions in this step. Minor incidents may require no recovery. For example, suppose your Web server encountered a series of unauthorized scans from a specific range of IP addresses. During the eradication step, you could add rules to your firewall to block any traffic from the range of IP addresses that initiated the scan. Unless complicating circumstances arise, you wouldn’t need to take any further recovery steps. The recovery step is unnecessary in this situation.

While some incidents require no restore activity, others require austere measures. Suppose your incident investigation revealed that a critical server contains a rootkit. Further investigation reveals that the rootkit exists on several recent backups. In most cases, you’ll have to rebuild the server from bare metal. From there, you’d identify the usable parts of your backups to extract the latest data possible. Sometimes restoring a computer isn’t as easy as just restoring a backup.

**technical TIP**

What are complicating circumstances? Suppose the range of IP addresses showed that the unauthorized scans originated from within your largest business partner’s network. Blocking those IP addresses would also restrict your ability to conduct business. You’d have to work with your customer’s IT department, or hopefully their SIRT, to find out whether they have a malware infestation or someone who is doing bad things.

**technical TIP**

To get more information on current incidents, visit the following Web sites:

• The Computer Emergency Response Team: *[http://www.cert.org/](http://www.cert.org/)*

• The DataLossDB: *[http://datalossdb.org/](http://datalossdb.org/)*

• The Repository of Industrial Security Incidents, requires membership fee: *[http://www.securityincidents.org/](http://www.securityincidents.org/)*

Lessons Learned

Regardless of the effort required to respond to an incident, formally review the incident and all team actions. Larger incidents should be reviewed by the whole team. Analyze what went well and what didn’t work so well. Use the information you uncover after each incident to improve the plan. Review incidents as soon after the actual events as possible. Memory fades and takes valuable insight with it. The lessons learned can keep you from repeating mistakes and help you avoid making new mistakes.

It is also a good idea to learn from other organizations’ mistakes and successes as well. Be on the lookout for any stories about security incidents and how organizations handled them. You can learn a lot from how others handle the same issues you encounter.

**Incident Handling and Management Tools for Microsoft Windows and Applications**

Managing incidents using the techniques you have learned in this chapter requires that you collect and deal with a substantial amount of information. Improve your team’s performance and make the entire process smoother by identifying and acquiring the right tools to help run the process. Two basic types of tools can aid in your work. The first type helps manage the SIRT’s activities and gather information about the incident response process. The second type collects information about the incident itself. You’ll learn about several tools of both types in this section.

**technical TIP**

The European Network and Information Security Agency (ENISA) Web site has a page dedicated to incident-handling tools. This site is a great reference for researching many of the tools available to support your SIRT. You can find the ENISA site at *[http://www.enisa.europa.eu/act/cert/support/chiht](http://www.enisa.europa.eu/act/cert/support/chiht)*.

| **TABLE 13-5** Incident process management tools. |
| **PRODUCT** || **WEB SITE** |
| D3 Incident Reporting and Case Management || *[http://www.d3security.com/](http://www.d3security.com/)* |
| SAI Global Incident Management Software || *[http://www.compliance360.com/solution\_incident\_management\_software.asp](http://www.compliance360.com/solution_incident_management_software.asp)* |
| MetricStream IT Incident Management || *[http://www.metricstream.com/solutions/it\_incident\_management.htm](http://www.metricstream.com/solutions/it_incident_management.htm)* |
| Rsam Incident Management || *[http://www.rsam.com/](http://www.rsam.com/)* |
| Application for Incident Response Teams (AIRT) || *[http://airt.leune.com/](http://airt.leune.com/)* |
| Request Tracker for Incident Response (RTIR) || *[http://www.bestpractical.com/index.html](http://www.bestpractical.com/index.html)* |

SIRT process management tools help team members collect and organize information about managing incidents. These tools assist the SIRT with the normal, day-to-day responsibilities of managing the information flow and status of current and historical incidents. These SIRT responsibilities include:

• Tracking incidents

• Reporting on incidents

• Archiving incident reports

• Communicating incident information

Available is a growing number of software packages specifically designed to help SIRTs manage the process of incident response. [Table 13-5](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13tab5) lists some incident process management tools.

** ![image](OEBPS/Images/note.jpg)NOTE**

In addition to the tools listed in [Table 13-5](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13tab5), many project management software products contain the basic tools to help manage incident response activities. View each incident as a project, and manage it using industry standard project management standards. To learn more about managing projects, go to the Project Management Institute: *[http://www.pmi.org](http://www.pmi.org)*.

**Investigating Microsoft Windows and Applications Incidents**

The second type of tool helps SIRT members collect technical information to support incident investigation and resolution. These tools enable forensic investigators to collect evidence of incident activity to discover what happened, why it happened, how to stop it from happening again, and whether any legal action can be taken against the incident source. These toolsets often provide the ability to discover traces of past activity in memory, stored on disks, or in log files. SIRT members who are trained to use investigation software can be very valuable resources for your team. In many cases, the difference between a successful incident resolution and an unknown loss is the quality of the incident investigation.

Explore the various tools and any training that is available for them. Select the set that fits your SIRT activities. [Table 13-6](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13tab6) lists some incident data collection and management tools.

The tools you choose will help find evidence of incident activity. The information will only be useful if it supports your investigation’s goals. Arbitrarily searching for evidence will likely result in collecting too much data and possibly missing evidence you will need. Before beginning any investigation activities, review your SIRT’s goals for an investigation. Although each organization should develop its own specific goals to direct activities, most incident investigations strive to answer the following questions:

• **What happened?**—Gather as much information about the incident as possible.

• **Who did it?**—Discover as much information as possible about the source of the attack.

• **When did it happen?**—Collect information on when the incident started and when it stopped.

• **Where did the incident originate and where was its target?**—Discover the source’s location and the target of the attack.

• **Why did the attacker attack this system?**—Discover the attack’s purpose and goal.

• **How did it happen?**—Attempt to understand how the attacker compromised your security controls and accessed your system.

Incident response tools make investigation activities easier, but they cannot take the place of clear goals. Your incident response plan directs all of the activities involved in an investigation, and your investigative tools provide the capability to satisfy your investigation’s goals.

| **TABLE 13-6** Incident data collection and management tools. |
| **PRODUCT** || **WEB SITE** |
| SANS Investigative Forensic Toolkit (SIFT) || *[https://computer-forensics2.sans.org/community/siftkit/](https://computer-forensics2.sans.org/community/siftkit/)* |
| PlainSight Open Source Computer Forensics || *[http://www.plainsight.info/](http://www.plainsight.info/)* |
| The Sleuth Kit || *[http://www.sleuthkit.org/](http://www.sleuthkit.org/)* |
| ProDiscover Incident Response || *[http://www.techpathways.com/ProDiscoverIR.htm](http://www.techpathways.com/ProDiscoverIR.htm)* |
| F-Response || *[http://www.f-response.com/](http://www.f-response.com/)* |
| EnCase Enterprise Platform || *[http://www.guidancesoftware.com/](http://www.guidancesoftware.com/)* |
| Forensic Toolkit (FTK) || *[http://www.accessdata.com/forensictoolkit.html](http://www.accessdata.com/forensictoolkit.html)* |
|   ||   |

**Acquiring and Managing Incident Evidence**

One of an investigation’s goals is to discover evidence that answers the who, what, when, where, why, and how questions you learned about in the previous section. The evidence you collect will further the discovery of facts. The same evidence could provide the proof necessary to result in a legal finding in your favor.

Treat every investigation as if it will end up in court. When you begin a new investigation, you don’t know how it will be resolved. Any investigation can end up as an internal matter. Alternatively, it could end up in civil or criminal court. Ensure that any evidence you collect will be useful in court if that’s where you end up.

Your investigation should produce evidence of an incident and possibly support action against an attacker. The evidence you will collect consists of files and their contents left behind after an incident. The existence of some files, such as pictures or executable files, can provide evidence of an incident. In other cases, the contents of files, such as log files, provide the necessary proof. Recognizing and identifying hardware, software, and data you can use is the first step in the evidence collection process.

Types of Evidence

The two types of evidence you’ll collect during an incident investigation are **real evidence** and **documentary evidence**. Real evidence is any physical object that you can bring into court. You can touch, hold, and directly observe real evidence. The real evidence you collect during an incident investigation could include computers and other hardware. If your incident involves criminal activity, real evidence may contain fingerprints that you can introduce in court.

The more common type of evidence you’ll collect is documentary evidence. Documentary evidence is any written evidence, such as printed reports or data in log files. Unlike real evidence, documentary evidence cannot stand on its own. Documentary evidence must be authenticated. Much of the evidence you are likely to use in proving a case will be in files, such as log files, database files, and incident-specific files and reports, that provide information indicating what occurred. Because anyone can create a data file or report with desired contents, you must prove that the evidence was collected appropriately and the data it contains proves a fact.

The majority of activities during your investigation will involve using utilities and tools to explore the contents of the computer and storage media. All files and file contents that support your case will be considered documentary evidence. This is where you’ll find most of the evidence for your investigation.

![image](OEBPS/Images/war.jpg)**WARNING**

Anytime you introduce documentary evidence, introduce the original document, not a copy. This rule is called the best evidence rule. The purpose of this rule is to protect evidence from being modified inappropriately. If the original document is required, there is less opportunity for a modification to occur during a copy operation. When you testify, you’ll have to convince the judge and jury that what you bring into court is the original document.

**FIGURE 13-2** Sample chain of custody log.

![image](OEBPS/Images/9781284031652_pg323.jpg)

Chain of Custody

All evidence you present in court must exist in the same condition as it did when you collected it. Each device, computer, and operating system has specific procedures for preserving data. Evidence cannot change at all once you collect it; it must be in pristine condition. The court will require you to prove that the evidence did not change during the investigation. You’ll have to provide your own proof that all collected evidence exists without changes as it did when your team collected it. The documentation that supplies details of every move and access of evidence is called the **chain of custody**. The chain starts when you collect any piece of evidence. [Figure 13-2](#24_Chaper13_split_001.xhtml#ba-9781284031652-ch13fig2) shows a sample chain of custody log.

The chain of custody must be complete and without gaps. You demonstrate this by providing the evidence log that shows every access to evidence, from collection to appearance in court. A complete chain of custody log also includes procedures that describe each step. For example, an entry might read “checked out hard disk drive serial number XN629H to create a primary analysis image.” Also include a description of what “creating a primary analysis image” means. The defense will examine the chain of custody documents, looking for any gaps or inconsistencies. Any issue with the chain of custody has the real potential of causing the court to throw out the evidence in question. Once that happens, the evidence you have collected becomes useless and your credibility will probably be questioned.

Since you don’t know if you’ll have to present evidence in court, collect all evidence during an incident investigation as if you will take it to court. If you carefully preserve the chain of custody and do not go to court after all, you just have well-documented evidence. This type of information is great for analyzing incidents for the lessons learned step of incident response. On the other hand, if you are sloppy in the way you collect evidence and then end up going to court, your sloppiness will likely result in having your evidence rejected by the court. Without the evidence you need to prove your case, you may not be able to prevail. Always treat each investigation as if it will end up in court.

Evidence Collection Rules

It is important that you know the rules surrounding evidence collection and handling before starting any investigation. Each state and local jurisdiction may impose slightly different rules, so familiarize yourself with local laws and policies. In addition, different rules govern different types of evidence. For example, analyzing a database that contains confidential personal medical information will have more stringent requirements than a database containing a parts inventory. Medical data falls under federal Health Insurance Portability and Accountability Act (HIPAA) regulations. Ask questions before engaging in evidence collection. Making incorrect assumptions when collecting evidence will likely get it thrown out of court.

A good place to start learning about local laws concerning collecting evidence is by developing a relationship with your local law enforcement agents. Call your local agency and ask for the computer forensics unit. Meet with them and take the time to learn how they approach investigations. Often, law enforcement officers will provide guidance and help you comply with their investigative requirements. Learning from them will save both of you substantial time and effort when an event occurs that requires law enforcement involvement.

Spend time with your organization’s legal representatives. Start with your SIRT’s legal representative. He or she can provide valuable input that will guide your investigative efforts as well. The goal is to ensure your processes comply with any statues, regulations, and policies before an investigation starts.

**Best Practices for Handling Microsoft Windows OS and Applications Incidents and Investigations**

Handling incidents and investigations is an important discipline within security management. If incidents are handled efficiently, the information system environment can benefit from the experience. To handle incidents professionally, it is crucial that the process of responding to incidents and conducting investigations be carefully thought out and planned. The quality of your organization’s response to incidents directly relates to the quality of its planning.

Although all organizations have different structures and needs, many goals and general procedures in the incident response process are standard. Organizations have collectively kept the practices that work and discarded the ones that have not. Here is a general list of best practices for handling incidents and investigations:

• Harden operating systems and software to avoid incidents.

• Assess computers periodically to expose vulnerabilities, potentially including penetration testing.

• Validate BCPs and DRPs.

• Get full management support for a SIRT.

• Create a SIRT.

• Conduct a risk assessment to identify potential incidents that require attention first.

• Develop an incident response plan around the six steps to handling incidents.

• Create an incident reporting form and procedures.

• Distribute and publicize the incident reporting form and procedures.

• Test the incident response plan before attackers do.

• Identify and acquire incident management software.

• Identify and acquire incident investigation software.

• Train key SIRT members on proper evidence collection and handling.

These best practices are the starting point for your incident response plan. Begin with these guidelines and develop a complete plan that works for your organization to conduct effective and efficient incident response activities.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Handling incidents well helps keep your organization from losing to the attackers. A solid incident response plan is one that continually improves while directing effective efforts. Taking the time to assemble the right SIRT members and develop a comprehensive incident response plan results in a more secure system. A solid incident response plan allows the SIRT to follow a prescribed path instead of making up the next step on the fly. Incidents generally result in less damage and are resolved more quickly. The thoughtful process of developing the incident response plan may even highlight existing vulnerabilities that should be addressed before an incident occurs.

Creating a SIRT and developing a comprehensive incident response plan makes the statement that your organization values security and can even increase your brand value. A functional SIRT not only makes a statement by its existence but also makes a difference by ensuring a high quality of security guarantees in spite of security violations. The SIRT assures your users and customers that your environment’s security is a priority and will be maintained regardless of the prevailing circumstances.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Chain of custody**

**Documentary evidence**

**Event**

**Incident**

**Real evidence**

**Security incident response team (SIRT)**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 13 ASSESSMENT**

  **1.** To ensure a secure computing environment, investigate each reported event.

A. True

B. False

  **2.** Many incidents go unreported because they are never recognized.

A. True

B. False

  **3.** Which of the following is the best description of the SIRT’s initial responsibility for incidents?

A. Recognize incidents.

B. Validate that an incident has occurred.

C. Initiate the incident investigation.

D. Contain the incident damage.

  **4.** The \_\_\_\_\_\_\_\_ step of handling incidents should always occur before an incident happens.

  **5.** Which incident-handling step might include disconnecting a computer from the network?

A. Identification

B. Eradication

C. Containment

D. Recovery

  **6.** The \_\_\_\_\_\_\_\_ step to handling incidents is the most important step to continuously improving your incident response plan.

  **7.** IT investigators (SMEs) are all SIRT team members.

A. True

B. False

  **8.** Which incident classification would apply to a situation where you find that your user account is locked due to too many logon tries using an incorrect password?

A. Unauthorized access of a limited account

B. AUP violation

C. Failed attempt to access any account

D. Unauthorized scan of one or more systems

  **9.** Which incident security level would be appropriate after discovering that several of your workstations are infected with worms that will launch a coordinated DoS attack against your Web servers in 12 hours?

A. Severe

B. High

C. Moderate

D. Low

**10.** Which incident-handling step might include scanning a computer for malware?

A. Identification

B. Containment

C. Eradication

D. Recovery

**11.** Which incident-handling step might include removing a virus from a computer?

A. Identification

B. Containment

C. Eradication

D. Recovery

**12.** The contents of log files are which type of evidence?

A. Real evidence

B. Documentary evidence

C. Testimonial evidence

D. Demonstrative evidence

**13.** The documentation that provides details of every move and access of evidence is called the \_\_\_\_\_\_\_\_.

**14.** You should treat every incident as if it might end up in court.

A. True

B. False

**15.** Any small change to evidence data may render that evidence unusable to your case.

A. True

B. False

**CHAPTER 14**

**Microsoft Windows and the Security Life Cycle**

IN THIS CHAPTER, you’ll learn about securing applications by creating or changing the application code. You’ll also study the software development process. You’ll learn as well to develop secure applications. And you’ll examine the importance of formal testing, validation, and the configuration management process. Finally, you’ll be able to apply what you’ve learned to your own development environments and start making the application software you write more secure from the very start.

**Chapter 14 Topics**

This chapter covers the following topics and concepts:

• What system life cycle phases are

• What agile software development is

• How to manage Microsoft Windows operating system (OS) and application software security

• How to develop secure Microsoft Windows OS and application software

• How to implement, evaluate, and test Microsoft Windows OS and application software security

• How to maintain the security of Microsoft Windows OS and application software

• What Microsoft Windows OS and application software revision, change management, and end-of-life phaseout are

• What the best practices for Microsoft Windows and application software development security investigations are

**Chapter 14 Goals**

When you complete this chapter, you will be able to:

• Describe system life cycle phases

• Explain how agile software development differs from traditional software development

• Manage the existing Microsoft operating system and application software security

• Implement, evaluate, and test Microsoft operating system and application software

• Describe how to manage the process of secure software development

**Understanding System Life Cycle Phases**

In the early 1960s, application software developers realized the software development process needed some structure. Computers were becoming more numerous and the need for programmers was growing. The capabilities of hardware and software expanded. In turn, software development projects began to grow in scope. Organizations that owned computers demanded more functionality from their large investments. The increased demand for functionality required more sophisticated applications. Software developers began to collaborate to create systems of software that were made up of numerous programs that worked together.

Software development began to look like an engineering process. It needed a model to help coordinate all of the individual pieces and people involved. One emerged that is still in use in various forms today. That model is the **System Development Life Cycle (SDLC)**. It is also known as the Software Development Life Cycle. The SDLC is a formal model for creating and modifying software. It breaks down the software development process into between 6 and 10 phases, depending on whose version of the model you adopt. [Figure 14-1](#25_Chaper14_split_001.xhtml#ba-9781284031652-ch14fig1) shows a 10-phase SDLC model.

**FIGURE 14-1** An SDLC with 10 phases.

![image](OEBPS/Images/9781284031652_pg329.jpg)

The SDLC uses industry best practices to guide software system development activities. Software development activities have the characteristics of projects. Software projects have specific start and end dates. They also have specific **deliverables**. A deliverable is an object created as a result of project activities. Using the wealth of best practices from project management for software development projects is a good fit. Project management techniques help standardize the software development process. These techniques make it easier to identify problems and fix them.

The SDLC provides both control and visibility of the tasks throughout the development project. It can also increase the probability of success. The SDLC encourages the development processes to be repeated in a predictable fashion. The SDLC has been around for quite a while in different forms. It has matured and changed with system architectures, but the overriding themes have remained the same. Throughout the years, the SDLC has also been called:

• The classic life cycle model

• The linear sequential model

• The waterfall method

The most important concept in SDLC is **decomposition**, or breaking down a software development project into distinct phases. From a security perspective, this practice provides specific points in time. These points in time allow you to validate or test the product to ensure it meets requirements. You can never start testing too early. The earlier you validate that your deliverables satisfy the requirements for the phase you are in, the more secure the final product will be. The SDLC phases mark different activities along the development process. The 10-phase SDLC defines the following phases:

  **1. Initiation**—This phase is where you scope and submit the initial project to management for approval and funding. If management agrees, the process is formally authorized and the process moves to the next phase.

  **2. System/Information Engineering and Modeling**—Here you collect information about your environment and the environment’s requirements. The idea is that you document everything your computing environment has and any specific requirements or restrictions. For example, if your proposed software system requires Microsoft IIS Web server and none of your servers has IIS installed, document this information. You’ll need either to change the Web server requirement or to install IIS. You don’t have to make decisions yet, but you’ll need these facts for later phases when making decisions. This information will provide a baseline of what your environment currently does and what must be changed to support the new or modified application.

  **3. Planning**—You develop your project management plan in this phase. The processes include resource requirements and scheduling. The deliverables of the planning phase direct the remainder of the software project.

  **4. Software Requirement Analysis**—You’ll document what the software must do in this phase. This includes both functionality and security requirements. Study the business needs that the software will meet. List them in terms of business functions.

  **5. System Analysis and Design**—Once you know details about your environment and what the software must do, begin the process of designing software that will fulfill business requirements. The deliverable of this phase is a complete design document that describes the software. You haven’t written any software yet—you have just described it. Your descriptions can be formal, such as using Unified Modeling Language (UML), or informal using your own standards. The important point is that the development team clearly understands what it needs to write. This is also the last chance to ensure your project is still on track before coding begins. If there are any design documents that do not satisfy the requirements from the previous phase or do not fit with your environmental requirements, address those before continuing.

  **6. Code Generation**—This phase is not the starting point. By this stage of the SDLC, most big decisions have already been made. Ensure that all code generated during this phase meets the design criteria from the previous phase. The code you generate in this phase should operate correctly.

  **7. Formal Testing**—This phase is the first formal mention of testing. However, you should have been validating that each phase’s deliverables meet the requirements of the previous phase’s deliverables. Thorough validation can save a lot of wasted programming effort.

  **8. Implementation**—The implementation phase represents the point in the project where the customer accepts the software product and the software moves into a production environment.

  **9. Maintenance**—This is typically the last phase. It is the step after implementation. Once in the maintenance phase there are really only two main reasons to modify the application. One reason to modify the application is enhancement request. The only other reason to modify the application is to fix a bug. In either of these situations, the correct approach is to return to Step 1 and go through the whole process again. However, you don’t start from scratch. This time you have all of the deliverables from the previous phases. You simply start with a description of what you want to change, and then go through each phase until you end up with modified code. By ensuring that even code fixes meet the application’s design goals, you avoid many of the situations where a fix breaks something else. It takes a little longer, but you save time and money by not chasing as many bugs later.

**10. Disposition**—This phase represents the activities related to retiring a software product and cleansing any hardware of sensitive data. In nearly all cases, plan to either archive application data or transfer it to another system. The disposition phase addresses all of the activities that reverse the actions in the implementation phase. By the end of this phase, you have completely removed all of your sensitive data from any hardware or devices that may be sold or recycled.

The SDLC formalizes the development process. This process also keeps you from jumping ahead and writing code that doesn’t satisfy requirements. Don’t make the mistake of allowing your team to start the project by writing code. You will almost always end up either ditching or rewriting at least parts of software you develop without planning. Some development approaches rely on prototyping at the beginning of projects. Even in these cases, though, you should have already put plans in place for ensuring any code is secure. Any time your software has to interact with other system components, carefully decide how it should operate. That requires time to make decisions before writing code.

Keep two important points in mind when following the SDLC. One, precede the code generation phase with several iterations of modeling and design. Two, validate each phase’s deliverables. By the time you reach the code generation phase, make certain you have substantial documentation on the software’s purpose, requirements, and design. It should be fairly easy to validate whether or not software written in this phase satisfies the system design.

Each phase has defined deliverables. A phase in the SDLC ends when the project team has accepted the deliverables for that stage. Deliverables are up to standard when they satisfy all of the goals, including security goals. Each phase generally culminates with a meeting of the project team to review the phase’s deliverables. When the team agrees that the deliverables are valid, the phase ends and the project moves to the next step. Phase validation and testing should identify any areas in your project where you have deviated from the prior phase’s deliverables. Make sure that the deliverables for each phase satisfy all preceding deliverables. Testing at every phase ensures that your team will quickly spot any variances from the stated design. Early detection of problems allows you to fix the problems with the minimum cost and disruption to the project.

**Agile Software Development**

Traditional software development management is still based largely on some variation of the waterfall method. During the 1990s, some organizations began to realize that the software industry was changing in different ways. Increasing demands to develop more complex software more efficiently led to new methods of managing software development. Instead of managing large projects with long delivery schedules, many organizations looked for ways to be more responsive. They wanted to be able to develop their software in smaller pieces. This move toward smaller development cycles eventually became known as the **agile development** method.

Agile loosely describes a method of developing software that is based on small project iterations, or **sprints**, instead of long project schedules. Organizations that use the agile method produce smaller deliverables more frequently and can evaluate a large project in terms of its individual pieces as they are completed. Sprints are generally one to four weeks in duration. That means there is some deliverable once or more each month. This focus on frequent delivery makes it possible to see and use pieces of a large software product as it matures over time.

The first organized meeting of agile enthusiasts was in 2001. Several organizations that were exploring this new type of software development sent representatives to a meeting in Snowbird, Utah, to collaborate and exchange ideas. The attendees created the foundational document of the Agile movement—the “Manifesto for Agile Software Development.” It is a concise document that reflects its writers’ affection for simple methods. Here is the Manifesto for Agile Software Development in its entirety:

We are uncovering better ways of developing software by doing it and helping others do it. Through this work we have come to value:

• Individuals and interactions over processes and tools

• Working software over comprehensive documentation

• Customer collaboration over contract negotiation

• Responding to change over following a plan

That is, while there is value in the items on the right, we value the items on the left more.

[Figure 14-2](#25_Chaper14_split_001.xhtml#ba-9781284031652-ch14fig2) shows the basic idea behind the agile method. Unlike the waterfall method, agile is designed to be iterative throughout the development process. Each time around the cycle is a single sprint. It takes many sprints to create a complete software project. Each sprint ends at a specific point in time and should have some deliverable. A deliverable should be something, such as working software, that the team can demonstrate. The focus on working software helps to focus the team on results.

** ![image](OEBPS/Images/note.jpg)NOTE**

You can find more information on the Manifesto for Agile Software Development and the agile method in general at *[http://agilemanifesto.org/](http://agilemanifesto.org/)*. Another good starting point to learn about agile is *[http://www.agile-process.org/](http://www.agile-process.org/)*.

**FIGURE 14-2** The agile software development method.

![image](OEBPS/Images/9781284031652_pg333.jpg)

Agile is a growing technique of managing software development projects. It tends to perform well in organizations that encourage ongoing communication and value short development cycles. It is important to begin developing software with security in mind from the very beginning. Agile methods encourage developers to plan for security and then test for security at the end of each sprint. Developing secure software can become an integral part of the overall development effort, that is, if the organization values and encourages security. Regardless of the development method an organization uses, attention to security is more important than any method.

**Managing Microsoft Windows OS and Application Software Security**

A security representative participating in the development process is your key to managing software security. One benefit of a model like the SDLC or agile method is the group nature of the model process. If you formally implement a development model, you should have required phase pass-off meetings every time your project is ready to move from one stage to another. The frequency of this phase pass-off depends on how you scope your projects. You have many different ways to scope software development projects. [Table 14-1](#25_Chaper14_split_001.xhtml#ba-9781284031652-ch14tab1) lists several common approaches to software project scope.

In most SDLC environments, the best choice is to create a project for a group of related software programs. This balances the advantages and disadvantages of other approaches. This approach also makes it easy to include maintenance modifications after you have implemented your software product. Of course, the first three choices are for SDLC environments. Choosing agile is another choice many organizations make.

Once you decide how you will scope projects, include a security component in every phase. Incorporating security in the earliest phases of software development increases the application’s security and decreases the cost of adding safeguards. In fact, many development organizations have one or more security specialists on the development team to ensure such concerns are met. All too often, organizations add security features late in the development cycle. Waiting too late in the design or development process may cause problems that could force a partial redesign. Include security requirements from the very beginning.

Another way to ensure your applications include security concerns early in the development process is to pursue security training for developers. Security classes are available that specifically target software developers. It makes sense to find good training for your analysts and developers to help them learn how to write more secure programs.

| **TABLE 14-1** Common approaches to setting software project scope. |
| **APPROACH** || **ADVANTAGES** || **DISADVANTAGES** |
| Create one project to develop a complete software application. || • Single project• Ultimate visibility || • Difficult to sift through tasks to find related work• Difficult to move to another phase until all components are ready• Very difficult to manage a large number of related components |
| Create a new project for each individual program. || • Ultimate flexibility• Easy to move from one phase to the next || • Difficult to define interproject dependencies• Difficult to maintain status reporting among multiple projects |
| Create a project for a group of related software programs. || • A balance of flexibility and visibility• Easy to manage groups of related programs together || • Must maintain interproject dependencies• Some projects may have to wait for dependent projects before moving to a new phase. |
| Use the agile method for each project. || • Flexibility to focus on rapid results• Dynamic team environment that changes as the product matures• Easier to detect and address emerging issues || • Challenging to schedule limited resources• Aggressive production schedules may not suit all organizations• Requires more sophisticated team leadership |

Along with ensuring your software developers are fully trained to write secure code, make sure your development environment and tools don’t get in the way. Many of the latest development environments integrate tools with secure libraries to empower developers to write more sound applications. One of the most popular development environments for Windows applications is Microsoft Visual Studio. Visual Studio supports developers working in Visual Basic, Visual C/C++, Visual C#, and F#. Visual Studio includes many features and tools for developing secure applications, including:

• **Code analyzer**—Identifies many coding errors

• **Application verifier**—Identifies stability, compatibility, and security issues

• **Compiler option**—Helps prevent buffer overflows

• **Secure libraries**—Are used in applications

• **Security exceptions**—Are used in debugging

Each time programs move from one phase to the next, conduct a security review. It is also a good time to perform a risk analysis. The review should cover the programs that have changed to ensure no new vulnerabilities have been introduced into your software. Start your security reviews with the very first phase. Microsoft has formalized the inclusion of security activities into the classic SDLC. To punctuate the need for integrating security into all phases of the development life cycle, Microsoft developed the **Security Development Lifecycle (SDL)**. According to Microsoft, the SDL “is a security assurance process that is focused on software development.” The company based the SDL on three core concepts that support secure development: education, continuous improvement, and accountability. The SDL groups security-related activities into seven phases. The SDL’s phases correspond to phases in the SDLC. [Figure 14-3](#25_Chaper14_split_001.xhtml#ba-9781284031652-ch14fig3) shows the phases and activities of the SDL.

The Microsoft SDL defines the following phases of development activities:

• **Training**—Ensure all developers are fully trained on security development topics before engaging in any software application development activities. Training all developers on secure development techniques is crucial to creating secure applications.

• **Requirements**—This phase corresponds to the SDLC Software Requirements Analysis phase. During this phase, the development team establishes security requirements as well as creates quality gates and conducts security and privacy risk assessments.

• **Design**—This SDL phase corresponds to the SDLC System Analysis and Design phase. SDL activities include establishing design requirements, analyzing the application’s attack surface, and modeling threats to the application.

• **Implementation**—This SDL phase corresponds to the Code Generation SDLC phase. During code generation, SDL activities include using approved tools, deprecating unsafe functions, and performing static code analysis to ensure new or modified code is secure.

**FIGURE 14-3** The Microsoft Security Development Lifecycle (SDL)—simplified.

![image](OEBPS/Images/9781284031652_pg336.jpg)

**technical TIP**

Find more information on the Microsoft SDL by visiting the SDL Web page at: *[http://www.microsoft.com/sdl](http://www.microsoft.com/sdl)*.

• **Verification**—This SDL phase corresponds to the Formal Testing SDLC phase. Formal testing focuses on evaluating functionality, while verification activities include dynamic code analysis, fuzz testing, and attack surface reviews.

• **Release**—This SDL phase corresponds to the Implementation SDLC phase. Once you implement application changes, you can create or update the incident response plan and conduct a final security review.

• **Response**—This phase comes into play when an incident occurs. The response phase corresponds to executing your incident response plan.

The Microsoft SDL extends the classic SDLC and complements standard development activities with a security-related focus. It provides managers with a prescribed method to ensure that the software development process pays appropriate attention to security matters. The three core concepts ensure that developers are well educated, always improving the development process, and accountable for the code they write.

**Developing Secure Microsoft Windows OS and Application Software**

As an IT professional, you should be soundly convinced of the importance of securing your organization’s data. You’ve seen many techniques to limit access to critical resources and make your data more secure. Some of the controls you’ve read about directly correspond to software vulnerabilities. If your development organization could create more secure software, you wouldn’t have to invest quite so much time and money to compensate for software vulnerabilities. From one perspective, secure software is its own control. So, how do you get started putting the SDLC and SDL models into action? How do you make it all result in more secure code?

A recently developed framework can help you design a development process that works in real organizations. The **Building Security in Maturity Model (BSIMM)** is the result of a study of large organizations that develop software with a specific focus on security. The organizations studied include Microsoft, Adobe, Google, Bank of America, Intel, Sallie Mae, Nokia, and Capital One. The BSIMM reveals how 51 large organizations use developer training, tool selection, and conducting the right activities to develop secure applications. This study wasn’t based on theory, but rather it reported on real situations in today’s environments.

**FIGURE 14-4** The Software Security Framework (SSF).

![image](OEBPS/Images/9781284031652_pg338.jpg)

The BSIMM defines 111 unique activities, along with the frequency each activity was observed during the study. While that sounds like a lot of work for a development group that is just starting to look at security, the BSIMM makes it clear. The BSIMM also organizes the 111 activities into a framework, called the **Software Security Framework (SSF)**, that groups 12 practices into four domains. [Figure 14-4](#25_Chaper14_split_001.xhtml#ba-9781284031652-ch14fig4) shows the SSF’s components.

The SSF’s four domains organize activities into related practices. These domains address the high-level concerns throughout the development life cycle. Here are the SSF domains, along with the BSIMM’s definition of each one:

• **Governance**—“Those practices that help organize, manage, and measure a software security initiative. Staff development is also a central governance practice.”

• **Intelligence**—“Practices that result in collections of corporate knowledge used in carrying out software security activities throughout the organization. Collections include both proactive security guidance and organizational threat modeling.”

• **Secure Software Development Lifecycle (SSDL) touch points**—“Practices associated with analysis and assurance of particular software development artifacts and processes. All software security methodologies include these practices.” The touch points provide direct correlations with activities in the SDLC. The activity groups in this domain include Architectural Analysis, Code Review, and Security Testing.

• **Deployment**—“Practices that interface with traditional network security and software maintenance organizations. Software configuration, maintenance, and other environment issues have direct impact on software security.”

**FYI**

You may be thinking that the BSIMM looks like just another model. At a high level, it is. But the BSIMM is a direct result of observing development behavior that works and produces secure results. That is not to say that the participating organizations produce perfect software. These organizations have simply identified activities that decrease the number of software defects they produce. And the BSIMM translates directly into defined activities that you can put into practice in your organization. You don’t have to figure out how to implement a model’s theoretical steps.

**technical TIP**

For more information on BSIMM and SSF, visit their Web site at *[http://bsimm2.com/](http://bsimm2.com/)*.

The SSF makes it easy to identify and organize activities in which you should engage throughout the software development process. If you want to simplify the process of developing secure software even further, it all boils down to four areas of focus:

• **Provide training in secure development**—Untrained developers lack the understanding, skills, and motivation to expend extra effort to incorporate security into their code. That may sound harsh, but it is true. While software developers are generally savvy enough to get the training they need on their own, your organization will fall short of its secure software development goals if you ignore the need to provide comprehensive security training for your developers.

• **Include security from the beginning**—Don’t wait for coding to begin to include security concerns. Security goals should be part of the initial requirements and subsequent design of any software.

• **Use secure programming techniques**—Here’s where the training pays off. Since you know what attackers are looking for and what they can use to compromise an application, don’t give it to them. Write applications in a way that is not vulnerable to known tactics.

• **Test for vulnerabilities**—Part of the formal testing activities should include testing for security vulnerabilities.

Each language has its own set of known vulnerabilities and techniques to avoid them. Learn how to write solid, secure code in your languages of choice. While languages often suffer from different vulnerabilities, a few common programming errors lead to insecure code. If you can’t implement a complete secure application development initiative immediately, you can at least alert developers to avoid a few common pitfalls for code they write. Here are a few of the most common application vulnerabilities:

• **Lack of input validation**—Attackers know that developers often don’t validate data that comes from user input. They use this known issue to launch buffer overflows, injection attacks, and other attacks that rely on a lack of input checking. To avoid this in your applications, confirm that every piece of data you receive is valid before you use it in any way. That means you should check the length of the data as well as the content for any characters that the software might interpret as commands.

• **Information leakage through poor error handling**—One of the early phases of any attack is reconnaissance. Attackers poke around to get information about your application and internal infrastructure. Error messages can be a problem. You want your error messages to provide enough information to understand what has happened but not enough to divulge internal details of your application or environment. Consider using coded error messages instead of explicit details.

• **Sloppy authentication or encryption**—Some applications store authentication credentials or encryption keys either in the application code or in easily accessed files. If attackers find these pieces of information, neither the authentication nor the encryption offers much data security. Carefully design how you’ll protect authentication credentials and encryption keys.

• **Remote system access or code execution**—Some applications allow users to access the server’s file system or run commands on the server. While the intention is to restrict what users can do, many software applications lack the controls to ensure users aren’t abusing this feature. Carefully validate any commands from users that will result in server access of any type.

• **Dynamic code execution**—Developers write many applications, and especially database applications, so that some code is dynamically generated before it is executed. This feature is an efficient way to handle complex database queries where you don’t know all of the query components until the user provides some input. Dynamic code is also helpful when code execution depends on data at run time. Using dynamic code also can make it easy for attackers to alter the intended commands and run malicious code dynamically. A secure application limits the use of dynamic code and aggressively validates any input to ensure it doesn’t contain malicious data or instructions.

These vulnerabilities are just a few of the opportunities application developers have to make code more secure. There is no substitute for good developer security training. Make sure to train all of your developers on application vulnerabilities and how to write secure code.

**Implementing, Evaluating, and Testing Microsoft Windows OS and Application Software Security**

Once you complete the code generation phase of any software project, have a reasonable level of confidence that the software meets your security and functional requirements. However, any program changes may have unexpected side effects when interacting with other programs. The purpose of formal testing is to evaluate how well your application meets overall performance, functionality, and security goals. Once your development group approves a set of application changes for testing, then the testing group applies any changed programs to its separate environment and carries out test scenarios.

Every goal from the original specification should have at least one corresponding testing scenario. The testing scenario evaluates whether the application satisfies the goal. Every time you identify a vulnerability in your application, include a scenario in your testing package that assesses whether or not a vulnerability exists. Your testing activities can be both manual and automated. Manual code reviews and functionality testing can be very valuable for finding obvious flaws, but automated software analyzers or testing tools allow you to test for far more vulnerabilities in a short amount of time. Numerous companies produce quality application testing and evaluation tools. Here is a list of a few companies that produce products to help you test your applications:

• **Microsoft Visual Studio Test Professional**—*[http://www.microsoft.com/visualstudio/eng/products/visual-studio-test-professional-2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-test-professional-2012)*

• **Coverty Test Advisor**—*[http://www.coverity.com/products/test-advisor.html](http://www.coverity.com/products/test-advisor.html)*

• **HP Fortify**—*[http://www8.hp.com/us/en/software-solutions/software.html?compURI=1337215#.Ua-F1-fVB8E](http://www8.hp.com/us/en/software-solutions/software.html?compURI=1337215#.Ua-F1-fVB8E)*

• **IBM Security AppScan Source**—*[http://www-03.ibm.com/software/products/us/en/appscan-source](http://www-03.ibm.com/software/products/us/en/appscan-source)*

• **TestPlant eggplant**—*[http://www.testplant.com/products/eggplant/](http://www.testplant.com/products/eggplant/)*

• **uTest**—*[http://www.utest.com/](http://www.utest.com/)*

• **Inflectra SpiraTest**—*[http://inflectra.com/SpiraTest/Default.aspx#0](http://inflectra.com/SpiraTest/Default.aspx#0)*

![image](OEBPS/Images/war.jpg)**WARNING**

Don’t think that once you fix a security vulnerability it stays fixed forever. It is not uncommon to see vulnerabilities you previously fixed get reintroduced into your code. Once you identify a particular vulnerability, always test future code for the presence of that vulnerability. This is also known as regression testing.

An ideal world features at least three environments: development, testing, and production. First, your code must pass all of the required tests in the testing environment. Then, it is ready to release to your production environment. This is the purpose of the implementation phase of the SDLC. Copying programs from your testing environment to the production environment may not seem difficult, but it can cause issues if not handled properly. The best way to handle implementation is to create a copy of a production environment. Then, have your testing group test the implementation process in that environment. Passing an implementation test means you should have no problems when you implement the real code to the real production environment.

One additional common security control for the software development environment is to employ separation of duties. Since software developers can write software that accesses sensitive data, they have the ability to compromise your data’s security. One way to protect your production data from a malicious developer is to not allow any developers to have access to production. Developers write code and can place their software in the testing environment. When testing is complete, another role must have access to move software from testing into production.

So, what can happen from just copying code to production? A lot. Today’s applications tend to be large, integrated systems that depend on many small modules of code. If even one doesn’t work properly, the whole system could encounter problems. This brief list includes some of the problems you might encounter if you implement faulty code to a production environment:

• **Inconsistent code and schema changes**—Many of today’s applications depend on database management systems to access their data. Database management systems use formal declarations, called **schemas**, to describe databases. When you change the way a table or column in a database is defined, you change the database’s schema. Programs rely on the database schema to access data and know how to use it. If you implement programs that expect a new schema to a production environment that still has an old schema, your programs may encounter problems. Depending on the language and the database product you use, your programs could either return errors or crash.

• **Inconsistent interfaces with other programs**—Programs generally work with other programs. To do that, each program has to know how to invoke other programs and what kind of data to exchange with them. If you change a program’s data requirements but neglect to change other programs that expect to exchange data with that first program, they will likely not be able to operate together any longer. Those problems will probably cause errors or program crashes.

• **Faulty installation procedure**—Due to local environmental differences, your production environment may be slightly different from your testing environment. Any subtle differences, such as folder locations, file permissions, or even defined printers could cause your programs to behave in an unexpected manner.

You may encounter many more potential issues when implementing programs and application changes. It is important to isolate as many issues as possible during your formal testing. However, you won’t identify every problem during testing. Some problems are dependent on the production environment. You won’t see these issues until your application is up and running in production. For this reason, it is necessary to test and evaluate any application changes after implementation.

After installing changes to your application, have your production team execute controlled evaluation scripts that validate the new software functions as prescribed. These tests also ensure that the software doesn’t do what it isn’t supposed to do. Once you are comfortable with the code’s functionality, test its security level. One of the best ways to test for security vulnerabilities in code that is in production is a penetration test. You should be conducting penetration tests periodically anyway, so this point in the implementation phase is an effective place to do it. Schedule a penetration test soon after you install any application changes. The test will validate that your changes are secure and that no new vulnerabilities exist in your software.

![image](OEBPS/Images/war.jpg)**WARNING**

Use caution when testing code in production. You don’t want to run a test that may slow the system down or cause it to crash. Be very restrictive about whom you allow to run tests in a production environment and which tests you run. As a general rule, avoid running any unnecessary tests or evaluations in your production environment.

**Maintaining the Security of Microsoft Windows OS and Application Software**

In this chapter, you’ve found out how to develop secure software. To make sure you have the most secure environment to develop secure software, combine all of these topics. Your development environment and tools need to be up to date just like the rest of your application software. Likewise, ensure the operating systems on all of your software development computers have the latest security patches. Take the time to treat your development environment computers like production computers, and make sure they are hardened and current.

Once you have confidence that your development environment is secure, provide the same level of assurance to your customers. Just as you expect to receive timely operating system and application software updates to address any newly discovered vulnerabilities, so do your clients. It doesn’t matter whether the recipients of the software you develop are internal customers or external customers. Your goal is to provide them with secure software, including periodic updates. Prioritize your software development to address any vulnerability discovered in your application software. Don’t take any shortcuts, but make every attempt to release security patches that address known vulnerabilities as quickly as possible.

Maintaining a software application often requires making difficult decisions. It would be nice to deliver every request in the order it was received. Realistically, you’ll run into times when you have to fast track software modifications. Your customers may need a critical new feature. Alternatively, you may have to address a newly discovered vulnerability or management may simply require you to implement a specific service or function as a priority. Or your organization may require you to suspend or postpone scheduled maintenance software development to address other critical projects. Although it is tempting to treat fast track projects differently than regular development, try not to bypass your development controls to speed up the process. Extreme cases calling for speedy fixes are inevitable. So when they crop up, make sure you document what you did and have a plan to reconcile the production change with testing as soon as possible. The secure development process you adopt isn’t there to slow you down—it’s there to protect you from making common mistakes. Don’t proceed without these protections simply to try to increase the speed with which you deploy maintenance patches.

Releasing patches every few days can make your customers’ system administrators scramble to validate and test each patch before they apply it. While not all organizations test new patches in isolated environments, some do. Those that do test patches before applying them to their production environments can get overwhelmed with frequent patches. Further, applying patches generally requires some type of a privileged user account. Frequent updates or patches mean more opportunities for problems during the installation process and more potential for attackers to compromise your environment during installation.

Also, check that all maintenance procedures protect your data’s security. For example, if a security patch or feature upgrade requires data conversion, one approach is to export the data to an external file and import the file into a new or modified database table. This strategy will expose the data while the program stores the data on disk. You could store the data in an encrypted folder to protect it from other users, but the disk still resides, at least temporarily, outside of the database and its internal access controls. Take care that you don’t expose any data during maintenance procedures. Keep it secure at all times.

**Microsoft Windows OS and Application Software Revision, Change Management, and End-of-Life Phaseout**

Developing software is basically the process of creating a collection of useful programs. Unlike other engineering disciplines, software development isn’t quite like building physical objects. Software development is far more flexible than building physical objects and generally far less constrained. Software development is as much an art as it is a science. The truth is, software is easy to change. Sometimes it’s too easy. And not only is it easy to change, but controlling those changes in a group environment can be difficult.

When you develop software in a group that is uncontrolled and undirected, imagination can easily turn into a nightmare. That’s where models and control methodologies come into play. Although the SDLC and the SDL provide solid frameworks for organizing software development efforts, they still have some issues. Many software development organizations that adhere to the SDLC or the SDL find three main areas of difficulty in producing software products.

Software Development Areas of Difficulty

The first issue is Phase Identification. As simple as it may sound, knowing where you are in the SDLC or SDL flow is not always obvious. The reason behind the difficulty is that different parts of a software application may be at different phases at any point in time. For example, the modifications to an accounting report may be ready for testing while a program changed to fix tax calculation bugs is ready to be released to production. To make matters worse, the new bug found in the general ledger posting programs hasn’t been fixed and requires more work.

With so many programs in different development phases, how do you define and communicate which versions of programs are in a specific phase? In other words, how do you know what programs you have at any time in any phase? As the number of developers and the number of programs increase, the problem can get progressively worse.

The second issue, Phase Transition, can also be confusing. Making the transition from one phase to the next often is more complex than it first appears. You need to get answers to several questions each time you move from one phase to another. These questions include:

• Which programs are ready to move to the next phase?

• Has the development team documented and approved the phase transition?

• Is the receiving phase prepared to receive the migrated objects?

• What is the residual impact to the receiving phase of migrating objects?

The last of the common issues with software development is activity coordination. It is important that all changes to objects and phase configurations are communicated to all interested parties and agreed to by all necessary parties. Make sure objects aren’t copied to a new place without prior notice or approval. Document every change and provide a method to undo changes if needed.

Software Control

Regardless of the specific software development method you use, refer to these common needs for control throughout the development process:

• **Baseline identification**—It is important for any software project to be able to identify which version, or collection of object versions, of an application exist in any defined collection, or configuration. For example, you need to know which versions of program are currently in production, which versions are being tested, and what your developers are currently modifying.

• **Control of changes**—Since it is almost guaranteed that you will change some of your software, either to address problems or enhance the functionality, you need to control how you change those items. Change control includes the ability to enforce rules that govern how you change items, who can change them, and when you can change them.

• **Communication**—Another common need in any business endeavor is communication. Since software applications are composed of programs and other components that must work together, it is crucial that all interested parties are in the loop throughout the change process. Good communication when using any model is essential to ensure your software satisfies its intended requirements.

• **Repeatable process**—Doing anything well once is good, but doing it well over and over again increases product quality and reduces costs. Software control provides the ability to learn from what you didn’t do well last time, implements controls to keep the bad stuff from happening again, and helps you do a better job next time. In short, good software control impacts your bottom line by minimizing loss.

Software Configuration Management (SCM)

The traditional **software configuration management (SCM)** process is a collection of best practices for handling changes in software projects. It is up to each organization to implement tools and techniques that identify both the functional and physical attributes of software at various points in time, and then perform systematic control of changes. This application of SCM allows you to maintain software integrity and traceability throughout the software development life cycle and proactively manage all your software assets. The SCM process defines the need to trace changes and the ability to verify that the final delivered software has all of the planned enhancements that are supposed to be included in the release. SCM identifies four procedures, also called activities, that must be defined for each software project to ensure a sound SCM process. The four SCM activities are:

• **Configuration identification**—The process of identifying the attributes that define every aspect of a configuration item. A configuration item is a product that has an end user purpose. In the context of software development, configuration items commonly include files and schema definitions. The files in a software product can include program code, documentation, configuration files, and data files. A structured collection, or collection of specific item versions, is called a baseline, or configuration. A baseline allows the definition of a snapshot of a configuration and enables change control.

• **Configuration control**—Configuration control is a set of processes and approval stages required to change a configuration item’s attributes and to re-baseline them. Any changes to item versions can only occur by following defined procedures. Item version changes include adding and removing items, modifying item versions, and modifying item attributes. The **Configuration Control Board (CCB)** plays a central role in the configuration control process. It can have many or few members and is responsible for making decisions about changes to the system definition during the course of the development life cycle.

• **Configuration auditing**—Configuration auditing is the process of confirming that all system components that should be in a given baseline are present. It is how management ensures that a software project is on track and building what is actually required. As long as a software product complies with all requirements in the current baseline, and all requirements in previous baselines, the product is valid. The process of conducting an audit can be straightforward or very complex, depending on the specific requirements. At the highest level, configuration auditing checks the current software product to ensure it satisfies the baseline requirements. More in-depth validation may be required to ensure any changes since the previous baseline have not invalidated other functionality. In short, the software must still satisfy all requirements. Configuration auditing also ensures that a project satisfies all requirements. Ensuring that changes meet requirements is backward-looking validation. Ensuring all requirements have been satisfied is forward-looking validation. Configuration auditing checks that the baseline scope of work has been fully satisfied without violating existing requirements.

• **Configuration status accounting**—Configuration status accounting is the ability to record and report on the configuration baselines associated with each configuration item at any moment in time. Basically, it is a snapshot of a configuration. It ensures that a complete and accessible record of the changes to a software system and reasons for such changes are available. The objective in configuration status accounting is to record item attributes, as well as why changes are made, when changes are made, and who made the changes. Configuration status accounting is often a reporting function that pulls the required information out of data stores created and managed by the configuration control tools in the SCM system.

| **TABLE 14-2** Common SCM tools. |
| **PRODUCT** || **WEB SITE** || **CLASSIFICATION** |
| Microsoft Team Foundation Server || *[http://msdn.microsoft.com/en-us/library/fda2bad5(v=VS.100).aspx](http://msdn.microsoft.com/en-us/library/fda2bad5\(v=VS.100\).aspx)* || SCM |
| IBM Rational ClearCase || *[http://www-01.ibm.com/software/awdtools/clearcase/](http://www-01.ibm.com/software/awdtools/clearcase/)* || SCM |
| Apache Subversion || *[http://subversion.apache.org/](http://subversion.apache.org/)* || VCS |
| Borland StarTeam || *[http://www.borland.com/us/products/starteam/index.html](http://www.borland.com/us/products/starteam/index.html)* || SCM |
| Mercurial SCM || *[http://mercurial.selenic.com/](http://mercurial.selenic.com/)* || SCM |
| Roundtable TSMS || *[http://www.tugboatsoftware.com/roundtable/](http://www.tugboatsoftware.com/roundtable/)* || SCM |

SCM is far more than just version control. Version control systems keep track of all changes made to a file over time. Each change creates a new version of the file. Keeping track of changes you have made to files is important both to research a history of changes and also to have the ability to revert back to a previous specific version of a file. SCM includes version control, but also adds build management, promotion management when promoting software from one configuration to another, and unit of work management. Each SCM toolset provides different capabilities, but they all help control the software development process. [Table 14-2](#25_Chaper14_split_001.xhtml#ba-9781284031652-ch14tab2) lists some common SCM tools. Each tool’s classification is either Software Configuration Management (SCM) or Version Control System (VCS).

**Best Practices for Microsoft Windows and Application Software Development Security Investigations**

Creating and maintaining secure applications is the topic of many books and articles. It has emerged as an important concern for software developers. Numerous models and frameworks tell you how to write cleaner, more secure code. One of the main reasons the BSIMM model is so valuable is that it reports on what works in the area of secure application development. When considering any new procedure or technology, it is wise to learn from those who have already used it. Learn from other people’s mistakes, and adopt strategies that worked. Plan well and you can enjoy a more productive software development environment. The following best practices for developing secure Windows applications represent what many organizations have learned:

• Think of security early and often.

• Adopt a software development model to help define your organization’s development activities and flow.

• Define activities for each phase in your model.

• Ensure all developers are trained to develop secure applications. Look for developer training from:

• **SANS**—*[http://www.sans.org](http://www.sans.org)*

• **SEI**—*[http://www.sei.cmu.edu/](http://www.sei.cmu.edu/)*

• **Cigital**—*[http://www.cigital.com/](http://www.cigital.com/)*

• Validate your software product at the end of every phase.

• Create separate software projects for each related group of programs or program changes.

• Do not begin a software development project by writing code—plan and design first.

• Keep the three SDL core concepts in focus—education, continuous improvement, and accountability.

• Develop tests to ensure each component of your application meets security requirements.

• Study the most common application vulnerabilities and develop programming standards to ensure you don’t include the vulnerabilities in your application.

• Identify and store programs, files, and schema definitions in a centralized, secure repository.

• Control and audit changes to programs, files, and schema definitions.

• Organize versioned programs, files, and schema definitions into versioned components.

• Organize versioned components and subsystems into versioned subsystems.

• Create baselines at project milestones.

• Record and track requests for change.

• Organize and integrate consistent sets of versions using activities.

• Maintain stable and consistent workspaces.

• Ensure reproducibility of software builds.

Using these best practices as guidelines will help your organization develop more secure applications and be more responsive to your customers.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

Securing applications that someone else wrote is one thing. Writing your own applications and ensuring they are secure requires a different focus. Before starting any development activities, prepare to develop secure applications. Preparation includes establishing or adopting a framework and using it to develop standards and procedures. Writing secure applications requires that your developers start off by receiving proper training on secure development topics. Then they’ll work closely with your security personnel to incorporate security into any development project from the beginning.

In this chapter, you learned how useful models and frameworks can be. You learned about how to formalize the software development process and how some large organizations structure their secure development activities. You read about the importance of controlling the development process and how SCM can provide the structure to develop complex applications. Take what you’ve learned, and start directing your organization’s development activities toward writing secure application software.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Agile development**

**Building Security in Maturity Model (BSIMM)**

**Configuration Control Board (CCB)**

**Decomposition**

**Deliverable**

**Schema**

**Security Development Lifecycle (SDL)**

**Software configuration management (SCM)**

**Software Security Framework (SSF)**

**Sprint**

**System Development Life Cycle (SDLC)**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 14 ASSESSMENT**

  **1.** A deliverable is an object created as a result of project activities.

A. True

B. False

  **2.** Which of the following is the most important concept in SDLC?

A. Initialization

B. Writing code

C. Decomposition

D. Disposition

  **3.** In which SDLC phase do you collect information about your current computing environment?

A. Initialization

B. System/Information Engineering and Modeling

C. System Analysis and Design

D. Implementation

  **4.** Testing occurs only immediately after code generation.

A. True

B. False

  **5.** Microsoft identifies the most important component of security by placing the \_\_\_\_\_\_\_\_ phase as the first phase of the SDL.

  **6.** Which SDL phase corresponds to executing your incident response plan?

A. Requirements

B. Verification

C. Response

D. Release

  **7.** The \_\_\_\_\_\_\_\_ framework is based on secure development practices of 51 larger organizations.

  **8.** Which SSF domain most closely maps to SCM?

A. Governance

B. Intelligence

C. SSDL Touchpoints

D. Deployment

  **9.** A common application vulnerability that can lead to several other vulnerabilities is a lack of input \_\_\_\_\_\_\_\_.

**10.** A \_\_\_\_\_\_\_\_ is a description of the data stored in a database.

**11.** Which SCM activity verifies that all of the components that are supposed to be in a configuration are in the configuration?

A. Configuration control

B. Configuration auditing

C. Configuration identification

D. Configuration status accounting

**12.** The \_\_\_\_\_\_\_\_ authorizes all change to an application.

**13.** A structured collection, or collection of specific item versions, is called what?

A. Release

B. Work package

C. Configuration item

D. Baseline

**CHAPTER 15**

**Best Practices for Microsoft Windows and Application Security**

THIS CHAPTER LISTS EACH OF THE BEST PRACTICES for securing Microsoft Windows computers and software. Use this chapter as a single resource to organize what you know about Windows security and apply it to your environment. These best practices will help you sort through a lot of information and focus on the steps you can take to make the biggest impact for your organization.

**Chapter 15 Topics**

This chapter covers the following topics and concepts:

• What the basic rules are for Microsoft Windows operating system (OS) and application security

• What the best practices for audit and remediation cycles are

• What the best practices for security policy conformance checks are

• What the best practices for security baseline analysis are

• What the best practices for operating system (OS) and application checks and upkeep are

• What the best practices for network management tools and policies are

• What the best practices for software testing, staging, and deployment are

• What the best practices for compliance/currency tests on network entry are

• What the trends are in the management of Microsoft Windows operating system (OS) and application security

**Chapter 15 Goals**

When you complete this chapter, you will be able to:

• Describe basic rules of Microsoft Windows Operating system and application security

• Use best practices for securing Microsoft Windows Operating system and application software

• Explain trends in Microsoft Windows Operating system and application software security management

**Basic Rules of Microsoft Windows OS and Application Security**

The basic rules of the Microsoft Windows operating system and application security cover a lot of ground. These best practices are here to remind you to address basic security first. After that, you can fine-tune your operating system, applications, and network. If you don’t cover the basics first, many advanced hardening efforts will not be as effective as possible. Here are the best practices to ensure your basic environmental components are secure:

• Install antivirus and anti-spyware software on all computers.

• Enable all real-time scanning (shield) options.

• Update signature databases and software daily.

• Perform a complete scan of all hard drives at least weekly.

• Perform a quick scan after installing or updating any software.

• Enable boot-time virus checking, including boot sector and memory scan at startup options.

• Remove administrator rights from all normal users.

• Apply software and operating system security patches.

• Educate users.

• Block outbound network connections that are not required for your applications.

• Establish incident response capabilities.

• Ensure that you know which business functions are critical to your organization. Then take whatever steps necessary to protect these functions in case of interruptions or disasters.

• Develop a plan to continue all critical business functions in case of an interruption. This business continuity plan (BCP) should cover all aspects of your organization.

• Define recovery time objectives (RTO) for each critical resource. Identify resources required for the recovery process. You’ll need to identify which parts of your recovery plan are sequential and which ones you can work on simultaneously.

• Develop a backup plan for each resource that minimizes the impact on performance while keeping secondary copies of data as up to date as possible. Explore various options, including alternate sites and virtualization.

• Automate as many backup operations as possible. Create logs and reports that make problems with backup operations easy to recognize.

• Verify all backup operations. A secondary copy of data with errors may be no better than damaged primary copy data.

• Document all backup and recovery procedures. Train all primary and backup personnel on all procedures.

• Test all recovery procedures rigorously. Conduct at least one full interruption recovery test each year.

• Review your complete recovery plan quarterly (or more frequently), and adjust for any infrastructure changes.

• Change your passwords periodically; the longer passwords remain unchanged, the higher the probability an attacker will compromise them. Change passwords at least every six months.

• Do not write down passwords. Use passwords you can remember. When you write down passwords, they are easier for an attacker to find and use.

• Export all encryption recovery keys to removable media and store the media in a safe place. Physically store your Encrypting File System (EFS) or BitLocker recovery information in a separate, safe location.

• Encrypt the My Documents folder for all users. Since most people use My Documents for most document files, encrypting this folder will protect the most commonly used file folder.

• Never encrypt individual files—always encrypt folders. This keeps any sensitive data from ever being written to the disk in plaintext.

• Designate two or more recovery agent accounts per organizational unit. Designate two or more computers for recovery, one for each designated recovery agent account.

• Avoid using print spool files in your print server architecture, or make sure that print spool files are generated in an encrypted folder. This keeps sensitive information from being stored in plaintext on a print server.

• Use multifactor authentication when using BitLocker on operating system volumes to increase volume security.

• Store recovery information for BitLocker in Active Directory Domain Services (AD DS) to provide a secure storage location.

• Disable standby mode for portable computers that use BitLocker. BitLocker protection is in effect only when computers are turned off or in hibernation.

• When BitLocker keys have been compromised, either format the volume or decrypt and encrypt the entire volume to remove the BitLocker metadata.

• Require strong passwords for all virtual private network (VPN) connections.

• Use the strongest level of encryption that your situation allows for VPNs.

• Use Secure Socket Tunneling Protocol (SSTP) for VPNs when possible. SSTP is the newest VPN protocol from Microsoft.

• Disable Service Set Identifier (SSID) broadcasting for wireless networks.

• Never use Wired Equivalent Privacy (WEP) for wireless networks—use only Wi-Fi Protected Access (WPA/WPA2).

• Trust only certificates from certificate authorities (CAs) or trusted sites. Train users to reject certificates from unknown or untrusted sites.

**Audit and Remediation Cycles**

Once you’ve covered the basics, you can move on to start addressing more advanced concerns. Don’t assume that covering the basics once is enough. Auditing the status of your security controls and planning to fix any problems you find is an ongoing, necessary process. The Deming cycle provides a simple model on which to base your security administration. Auditing is a critical part of the cycle. The Deming cycle is also known as the Plan-Do-Check-Act (PDCA) process. The name comes from each of the four steps in the process:

• **Plan**—Establish your objectives and processes to meet a stated goal. In the context of routine auditing, the goal should be to assess specific security controls.

• **Do**—Implement the process you planned in the previous step.

• **Check**—Measure the effectiveness of the new process and compare the results against the expected results from your plan. You’ll compare the expected results of your auditing information with a baseline.

• **Act**—Analyze the differences between expected results and measured results. Determine the cause of any differences. Then, proceed to the Plan process to develop a plan to improve the performance.

Being able to routinely validate security settings depends on proper use of auditing. These auditing best practices will cover most general environments:

• Maintain current backups of all audit information so you can recover historical audit information in the case of a disaster.

• Do not enable Read or List auditing on any object unless you really need the information. Read/List access auditing can create a tremendous amount of information.

• Do not enable Execute auditing on binary files except for administrative utilities that attackers commonly use. Do turn auditing on for these utilities to help monitor their use.

• Limit enabling all auditing actions to files, folders, programs, and other resources that are important to your business functions. Don’t be afraid to enable auditing for any object—just ensure you need the information you’ll be saving.

• Enable auditing for all change actions for your Windows install folder and any folders you use in normal business operation. It is also a good idea to audit changes to the Program Files folder.

• Audit all printer actions. You may need to know who printed a document that found its way into the wrong hands.

• Ignore Read and Write actions for temporary folders but audit Change Permissions, Write Attributes, and Write Extended Attributes actions. These actions can help identify attacker activities.

• Develop Windows policies and Group Policy Objects (GPOs) that are as simple as possible and still satisfy your security policy. Complex policies are difficult to verify.

• Develop clear guidelines to evaluate each element of your security policy. An audit should be a structured process to verify your security policy, not an unorganized hunt for problems. Know what you will be looking for before you search through lots of audit data.

**Security Policy Conformance Checks**

Group Policy is an important component of secure Windows environments. Windows Group Policy helps centralize settings that ensure conformance with your security policy. Once you take the time to develop a comprehensive Group Policy, use it to both apply settings and ensure settings are correct. Here are a few guidelines that should result in an effective Group Policy:

• Define organizational units (OUs) that reflect your organization’s functional structure.

• Create OU GPOs for controls required in your security policy.

• Use meaningful names for GPOs to make maintenance and administration easier.

• Deploy GPOs in a test environment before deploying to your live environment.

• Use security filtering and Windows Management Instrumentation (WMI) filters to restrict settings when necessary.

• Back up your GPOs regularly.

• Do not modify the default policies—instead, create new GPOs.

• Use the Group Policy Best Practices Analyzer (BPA) to identify Group Policy configuration errors or dependency issues that may prevent settings from functioning as you expected.

• Use the Group Policy Settings Reference spreadsheets for more information on available GPO settings. You can find these spreadsheets by visiting the Web site *[http://www.microsoft.com/downloads](http://www.microsoft.com/downloads)*, and searching for Group Policy Settings Reference. Microsoft provides several versions to cover different Windows releases.

• Acquire the Windows Server Security Compliance Management resource from Microsoft to help design, deploy, and monitor your server baselines.

• Acquire the Windows 7 or Windows 8 Security Compliance Management resource from Microsoft to help design, deploy, and monitor your workstation baselines.

• Use the GPOAccelerator tool to automatically deploy recommendations from the Security Compliance Management toolkits.

• Use the Group Policy Management Pack for Microsoft Operations Manager (MOM) for monitors, rules, views, and knowledge for monitoring the application of Group Policy settings.

**Security Baseline Analysis**

Baselines help you collect and analyze the data required for auditing needs without collecting a lot of extra data. A baseline defines the settings and data you want to collect for later comparison and trend analysis. The following guidelines will help you identify and create baselines you can use to ensure compliance with your security policy:

• Create initial baselines that represent a secure starting point for each computer. Develop security templates in Security Configuration and Analysis (SCA) that contain the security settings for each type of workstation and server. Change the templates as needed and use them when building new computers. You can apply up-to-date templates to new Windows installations to quickly configure a new computer to your security standards.

• Run SCA/Microsoft Baseline Security Analyzer (MBSA) using command-line interface options to compare computer settings and configurations with your standards. Schedule scans to run periodically (weekly or monthly), and review the resulting output files for any identified problems.

• Develop batch files to run scans and collect ongoing operational information. Collect information using a set daily, weekly, or monthly schedule and archive collected data files.

**OS and Application Checks and Upkeep**

An effective security policy ensures that your organization has all the technical controls in place to support its security goals. It takes more than just technical controls to meet all security goals, but security administrators mainly focus on deploying and maintaining technical security controls.

This list of Windows security administration best practices will help you deploy and maintain controls to support your security policy. Change the list to suit your organization, but pay attention to the suggestions. They can help you avoid wasting time and resources:

• Clearly state security goals in your security policy.

• Include all compliance requirements for applicable legislation, regulation, and vendor standards in your security policy.

• Use the PDCA method for all security administration activities.

• Communicate with all stakeholders—share as much information as possible.

• Strive for simplicity in all controls and systems—complexity invites failures.

• Search for controls that have little impact on users. Users tend to bypass controls that they find intrusive or difficult.

• Coordinate acceptable use policies (AUPs) with technical controls.

• Automate as much as possible—use scheduled jobs whenever you can.

• Use AD GPOs for as many security settings as possible.

• Coordinate physical controls with technical controls.

• Never allow a computer or mobile device that doesn’t have current anti-malware controls in place to connect to your network. This rule applies to all computers and mobile devices—even laptops or smartphones owned by distinguished guests. Enforce the rule or be prepared to put your malware removal plan into action.

• Develop a plan to monitor system and network performance and follow it.

• Ensure the operating system and all software is up to date for all computers.

• Periodically examine log files for suspicious behavior.

• Stay current on emerging attacks and trends and update your controls appropriately.

• Fully test your recovery plans at least annually (more often if possible). You’ll never really know how your recovery plan works until you actually execute each of the steps.

• Define discretionary access control lists (DACLs) when necessary and modify or remove them when user account roles change.

Hardening your Windows operating system removes as many vulnerabilities as possible. The best practices to harden your Windows operating systems are as follows:

• Install only the Server Core option when you don’t need extra functionality.

• Select the minimum number of roles when installing Windows Server 2008.

• For Windows Server, run the Security Configuration Wizard (SCW) immediately after installing the operating system.

• Update each computer with the latest operating system patches.

• Configure each computer for automatic Windows updates.

• Install and run MBSA and at least one other Windows security vulnerability scanner.

• Create one or more user accounts with administrator rights.

• Disable the Administrator and Guest user accounts.

• Disable all unneeded services.

• Close all ports not required by services or applications.

• Create GPOs for all security settings, including firewall rules.

• Use AD to distribute all configuration changes using GPOs.

• Create a backup of each GPO.

• Scan all computers for open ports.

• Limit physical access to all critical servers.

• Create an initial baseline backup.

• Change the AD Directory Service Restore Mode (DSRM) password periodically, at least every six months.

• Install anti-malware software on each computer.

• Ensure all anti-malware software and data is current.

• Use network access control (NAC) software or devices to control remote computer connections.

• Use remote authentication methods to authorize remote computers and users.

• Require secure VPNs to access internal network resources.

• Use Internet Protocol Security (IPSec) with digital certificates to authenticate computer-to-computer connections in the datacenter.

• Require security awareness training prior to issuing access credentials.

• Require periodic recurrent security awareness training to retain access credentials.

• Provide continuing security awareness through different means.

The process of hardening applications is just as important as hardening your operating system. These best practices will help you establish a solid foundation for securing your applications:

• Harden the operating system first.

• Install only necessary services.

• Use server roles when possible.

• Use SCW to apply the least privilege principle to applications.

• Remove or disable unneeded services.

• Remove or disable unused user accounts.

• Remove extra application components.

• Open only the minimum required ports at the firewall.

• Define unique user accounts.

• Use strong authentication.

• Use encrypted connections for all communication.

• Encrypt files, folders, or volumes that contain private data.

• Develop and maintain a business continuity plan (BCP) and disaster recovery plan (DRP).

• Disable any server features you don’t need.

• Ensure every computer has up-to-date anti-malware software and data.

• Never open any content or files from untrusted sources.

• Validate all input received at the server.

• Audit failed logon and access attempts.

• Conduct penetration tests to discover vulnerabilities.

**Network Management Tools and Policies**

Computers communicate using networks. A secure networking environment is crucial to overall security. To start securing your network calls for some best practices. These practices will provide a good set of guidelines for ensuring your network stays secure:

• Identify sensitive data.

• Protect sensitive data at rest using encryption.

• Establish unique domain user accounts for each user.

• Enforce strong passwords for all user accounts.

• Create new user accounts with limited rights and permission for services:

• Do not allow any services to run as a domain admin user.

• Use Kerberos for secure authentication.

• Install firewalls to create a demilitarized zone (DMZ):

• Place all Internet-facing servers in the DMZ, such as Web servers and other publicly accessible servers.

• Use encrypted communication for all traffic flowing between the DMZ and the trusted network.

• Use encryption for all communication involving sensitive data.

• Establish firewall rules:

• Deny all suspicious traffic.

• Allow only approved traffic for servers.

• Filter inbound and outbound traffic for servers and workstations for malicious messages.

• If your firewall supports it, automatically terminate connections with sources generating denial of service (DoS) traffic to mitigate DoS attacks in process.

• Install anti-malware software on all computers and establish frequent update schedules and scans:

• Update software and signature databases daily.

• Perform quick scans daily.

• Perform complete scans at least weekly.

• Use WPA or WPA2 for all secure wireless networks.

• Disable SSID broadcast for secure wireless networks.

• Do not enable wireless or mobile broadband cards while connected to your organization’s internal network. Always disable your wireless adapter before connecting a laptop to the wired network.

• Do not allow visitors to roam around your facilities that use wireless LANs. Many access points can be physically reset to insecure factory default settings by pressing a reset switch on the box.

• Avoid connecting to public networks. When you connect to an open wireless network, don’t expect privacy or security.

• If you have to use an open wireless connection, don’t visit Web sites that require usernames, passwords, or account numbers, such as online banking. Use an encrypted connection or a VPN.

• Install a separate wireless access point connected only to the Internet for guests.

• Disable or uninstall any services that you don’t need.

**Software Testing, Staging, and Deployment**

Developing secure software can be a challenge. Regardless of whether you develop or purchase software, you must deploy and maintain it as well. Some general best practices for developing, deploying, and maintaining secure Windows application software are the following:

• Adopt a software development model to help define your organization’s development activities and flow.

• Define activities for each phase in your model.

• Ensure all developers are trained on developing secure applications.

• Validate your software product at the end of every phase.

• Create separate software projects for each related group of programs or program changes.

• Do not begin a software development project by writing code—plan and design first.

• Keep the three Security Development Lifecycle (SDL) core concepts in focus—education, continuous improvement, and accountability.

• Develop tests to ensure each component of your application meets security requirements.

• Study the most common application vulnerabilities and develop programming standards to ensure you don’t include the vulnerabilities in your application.

• Identify and store programs, files, and schema definitions in a centralized, secure repository.

• Control and audit changes to programs, files, and schema definitions.

• Organize versioned programs, files, and schema definitions into versioned components.

• Organize versioned components and subsystems into versioned collections.

• Create baselines at project milestones.

• Record and track requests for change.

• Organize and integrate consistent sets of versions using activities.

• Maintain stable and consistent workspaces.

• Ensure reproducibility of software builds.

Despite your best efforts to secure your applications and operating system, you still may encounter attacks. You have already learned how important it is to have a well-thought-out plan to handle incidents when they do occur. A general list of best practices for handling incidents and investigations includes these steps:

• Harden operating systems and software to avoid incidents.

• Assess computers periodically to expose vulnerabilities.

• Validate BCPs and DRPs.

• Get full management support for a security incident response team (SIRT).

• Create a SIRT.

• Define and assign SIRT roles.

• Conduct a risk assessment to identify potential incidents that require attention first.

• Develop an incident response plan around the six steps to handling incidents.

• Create an incident reporting form.

• Distribute and publicize the incident reporting form and procedure.

• Test the incident response plan.

• Identify and acquire incident management software.

• Identify and acquire incident investigation software.

• Train key SIRT members on proper evidence collection and handling.

**Compliance/Currency Tests on Network Entry**

Some of the most sensitive points in your IT infrastructure are the entry points from remote users and systems. It is important that you carefully consider how remote users connect to your network and how you ensure these connections do not compromise your security. One straightforward way to control access to your network and any resource on it is to employ an aggressive user-based set of access controls. Computer security experts use many models to manage user accounts over large networks, but one particular strategy provides clarity and security. The AGULP approach provides a method for managing any number of users predictably. AGULP is an acronym that stands for:

• **A**ccounts

• **G**lobal groups

• **U**niversal groups

• **L**ocal groups

• **P**ermissions

The idea behind AGULP is to systematically nest individual user accounts in groups to make securing objects more general. The first step is to create separate user accounts for each user. Creating separate user accounts for each user’s role adds an extra step of security. In this case, a user may have more than one account. You then add user accounts to global groups, according to the users’ shared attributes. These attributes can be geographical or functional, such as manufacturing or human resources. Next, add global groups to universal groups, or groups that are defined for users in any domain in Active Directory. After that, add global groups and universal groups to local groups on computers that contain resources you want to secure. This strategy avoids the need to add individual users to local groups. Finally, you define the permissions for secured resources, or objects, for local groups. The AGULP strategy allows you to reduce the number of access control lists (ACLs) for each resource. Use AGULP to decide how many users and groups you need of each type to reduce the administrative load.

Additionally, to maintain secure access for remote clients, check this list of best practices:

• Map your proposed remote access architecture, including redundant and backup connections. Use one of the several available network mapping software products to make the process easier.

• Update the network map any time you make physical changes to your network.

• Install at least one firewall between your VPN endpoint and your internal network.

• Select a VPN provider that your clients can easily access. If you select a vendor-specific VPN solution, develop a method to distribute and maintain the VPN client software to your users.

• Use global user accounts whenever possible:

• Use strong authentication for all user accounts.

• Create a limited number of administrative accounts with permissions for remote administration.

• Develop a backup and recovery plan for each component in the Remote Access Domain.

• Do not ignore backing up and recovering configuration settings for network devices.

• Implement frequent update procedures for all operating systems, applications, and network device software and firmware in the Remote Access Domain.

• Monitor VPN traffic for performance and suspicious content.

• Carefully control any configuration setting changes or physical changes to domain nodes.

• Update your network map after any changes.

• Require encryption for all communication in the Remote Access Domain.

• Enforce anti-malware minimum standards for all remote computers as well as server computers in the Remote Access Domain. Ensure all anti-malware software and signature databases remain up to date.

**Trends in Microsoft Windows OS and Application Security Management**

The landscape of security is constantly changing. Attackers are becoming increasingly more sophisticated and in some cases more aggressive. You’ve had opportunities to learn about known issues and vulnerabilities. These topics are crucial to your environment’s security, but you have more to learn. As new threats emerge, you’ll be responsible for adapting your environment to face them. As long as you have established a solid security policy and are diligently protecting your environment from threats, you should be able to react to new threats.

Good security practices help you react to new threats as well as existing ones. Don’t ever think that emerging threats are the only ones you should consider. Many attackers focus on older, well-known methods. Even so, numerous organizations still aren’t proactive about security and are vulnerable to these older threats. Stay diligent against all known threats as you build defenses against new ones.

These emerging threats are likely to shape the security landscape for the near future:

• One of the fastest growing attack methods is **social engineering**. Social engineering is the process of an attacker tricking or convincing an authorized user to carry out an action or provide valuable information for which the attacker does not have authorization. In other words, the attacker gets the authorized user to do the dirty work. Many types of attacks depend on this attack method and the trend indicates even more growth. The best defense against social engineering attacks is educating your users to recognize and report any social engineering attempts.

• Mobile devices are rapidly becoming the most attractive targets for attackers. While device theft is a valid concern, many attackers attempt to compromise mobile devices to use as bots. The mobile nature of these devices attracts attackers to create mobile bots to launch attacks. Mobile devices also commonly store large amounts of personal information. The information that makes mobile devices so convenient for users also makes them valuable attack targets. Most mobile devices used to run iOS, Blackberry OS, or Android operating systems. Microsoft released Windows 8 and Windows Phone operating systems to compete in the mobile device marketplace. While these mobile Windows operating systems running on mobile devices are different from legacy desktops and laptops, many of the security concerns are the same.

• Expect to see more scams by questionable security consulting or software firms. These companies use fear tactics to get users to purchase their product to remove security problems. These programs may not work, may be rebranded versions of freely available software, or may be malware themselves. Train users to install software only from trusted sources.

• As attacks become more data-focused, focus your controls more on data than on the containers of that data. Explore access controls in your applications and database management systems.

• **Cloud computing** will continue to grow as the environment of choice for organizations of any size. Cloud computing is the practice of renting computer resources from a provider instead of owning the resources. Operating in the cloud environment opens your data to many more vulnerabilities, because your data resides on servers accessible from the Internet. Use secure access controls to keep you data safe.

• Malware will expand and use legitimate network traffic to send itself to other computers. Malware programs are getting more sophisticated to avoid detection. Be diligent. Recognize suspicious traffic and filter it out.

These are just a few of the expected trends that will continue or emerge in the coming years. Stay secure by ensuring good basic security, training and engaging your users in secure practices, and keeping all software current. These steps will allow you to withstand today’s attacks and those that will come in the near future.

 ![image](OEBPS/Images/lock.jpg)**CHAPTER SUMMARY**

You should be comfortable with the Microsoft Windows operating system environment on both server and workstation computers. You should also know what you need to do to make each component of your IT infrastructure more secure. Windows offers many features and capabilities to deploy a secure and functional environment. You learned in this chapter how to distill all of the concepts on securing your Windows environment into targeted best practices that work for many different types of organizations. You know how to secure today’s Windows environment, and you learned about developing trends to keep you current for challenges yet to come. You are now ready to establish and maintain a secure Windows environment.

 ![image](OEBPS/Images/lock.jpg)**KEY CONCEPTS AND TERMS**

**Cloud computing**

**Social engineering**

 ![image](OEBPS/Images/lock.jpg)**CHAPTER 15 ASSESSMENT**

  **1.** Anti-malware software applies mainly to workstation computers.

A. True

B. False

  **2.** What is RTO?

A. Real-time objective

B. Recovery time objective

C. Recovery turn over

D. Real turn over

  **3.** Test your backup only when you suspect media corruption.

A. True

B. False

  **4.** Even if you use the same password for a long time, it will remain secure.

A. True

B. False

  **5.** Which of the following is an encryption recovery key that you should physically store in a separate safe location?

A. DES

B. AES

C. SSTP

D. EFS

  **6.** Which protocol is the newest VPN protocol from Microsoft?

A. SSTP

B. L2TP

C. PPP

D. TLS

  **7.** The Plan, Do, Check, Act (PDCA) process is also called a \_\_\_\_\_\_\_\_ cycle.

  **8.** Which printer actions should you audit?

A. Remote access

B. Print nontext files

C. Change printer destination

D. All actions

  **9.** Which of the following tools will compare computer settings with your standards? (Select two.)

A. GPMC

B. SCA

C. MBSA

D. PDCA

**10.** Change your \_\_\_\_\_\_\_\_ Directory Service Restore Mode (DSRM) password periodically, at least every six months.

**11.** What program should you run on Windows Server immediately after installing the operating system?

A. Group Policy Object (GPO)

B. Anti-malware shield

C. Security Configuration Wizard (SCW)

D. Network access control (NAC)

**12.** What is the first step to take when hardening applications?

A. Remove or disable unneeded services.

B. Define unique user accounts.

C. Harden the operating system.

D. Ensure every computer has up-to-date anti-malware software and data.

**13.** To isolate Web server computers from your internal network, place them in a segregated network called a \_\_\_\_\_\_\_\_.

**14.** Which of the following is the best choice for secure wireless communications?

A. WPA

B. WEP

C. SSID

D. TLS

**15.** Which of the following is *not* a core concept of Security Development Lifecycle (SDL)?

A. Education

B. Availability

C. Continuous improvement

D. Accountability

**APPENDIX A**

**Answer Key**

**CHAPTER 1  ** Microsoft Windows and the Threat Landscape

1\. B 2. A 3. D 4. C 5. A 6. D 7. A 8. C 9. B 10. A 11. B 12. D 13. C 14. A 15. B

**CHAPTER 2  ** Security in the Microsoft Windows Operating System

1\. C 2. A 3. D 4. B 5. D 6. B 7. A 8. C 9. C 10. D 11. C 12. B 13. A 14. C 15. C

**CHAPTER 3  ** Access Controls in Microsoft Windows

1\. C 2. A 3. B 4. C 5. A 6. A 7. C 8. D 9. A 10. B 11. B 12. C 13. A 14. C 15. D

**CHAPTER 4  ** Microsoft Windows Encryption Tools and Technologies

1\. C 2. A 3. C 4. A 5. D 6. A 7. D 8. A 9. B 10. C 11. D 12. B 13. A 14. C 15. A

**CHAPTER 5  ** Protecting Microsoft Windows Against Malware

1\. A 2. C 3. D 4. B 5. A 6. D 7. B 8. A 9. C 10. D 11. A 12. D 13. Buffer overflow 14. A 15. D

**CHAPTER 6  ** Group Policy Control in Microsoft Windows

1\. A 2. 90–120 3. C 4. B 5. A 6. B 7. Active Directory 8. B 9. GUID 10. A 11. B 12. B 13. D 14. RSOP 15. C

**CHAPTER 7  ** Microsoft Windows Security Profile and Audit Tools

1\. B 2. Snapshot 3. A 4. C 5. MMC 6. A 7. C 8. A 9. B 10. D 11. B 12. C 13. B 14. Minimum 15. C

**CHAPTER 8  ** Microsoft Windows Backup and Recovery Tools

1\. B 2. A and C 3. C 4. Increases 5. Decreases 6. B 7. A 8. B 9. A 10. B 11. D 12. B 13. Bare metal recovery 14. B

**CHAPTER 9  ** Microsoft Windows Network Security

1\. Metropolitan area network (MAN) 2. B 3. B 4. Coaxial 5. A 6. A 7. Demilitarized zone (DMZ) 8. B 9. D 10. C 11. A 12. A 13. B and C 14. B 15. C

**CHAPTER 10** Microsoft Windows Security Administration

1\. B 2. C 3. B 4. A 5. B and C 6. Business continuity plan (BCP) *and* disaster recovery plan (DRP) 7. A 8. A and C 9. MBDA 10. B 11. B 12. A 13. C 14. A

**CHAPTER 11** Hardening the Microsoft Windows Operating System

1\. A 2. B 3. Hardening 4. B 5. A 6. C 7. A 8. B 9. Administrator 10. B 11. Nmap 12. D 13. B 14. B 15. PKI

**CHAPTER 12** Microsoft Application Security

1\. B 2. C 3. B 4. Web browser 5. A 6. B 7. C 8. A 9. B 10. A 11. C 12. Query 13. Transparent Data Encryption (TDE) 14. B 15. B

**CHAPTER 13** Microsoft Windows Incident Handling and Management

1\. B 2. A 3. B 4. Preparation 5. C 6. Lessons learned 7. B 8. C 9. B 10. A 11. C 12. B 13. Chain of custody log 14. A 15. A

**CHAPTER 14** Microsoft Windows and the Security Life Cycle

1\. A 2. C 3. B 4. B 5. Training 6. C 7. Building Security in Maturity Model (BSIMM) 8. D 9. Validation 10. Schema 11. B 12. Configuration Control Board (CCB) 13. D

**CHAPTER 15** Best Practices for Microsoft Windows and Application Security

1\. B 2. B 3. B 4. B 5. D 6. A 7. Deming 8. D 9. B and C 10. Active Directory 11. C 12. C 13. Demilitarized zone (DMZ) 14. A 15. B

**APPENDIX B**

**Standard Acronyms**

 
| **3DES** || triple data encryption standard |
| --- | --- |
| **ACD** || automatic call distributor |
| **AES** || Advanced Encryption Standard |
| **ANSI** || American National Standards Institute |
| **AP** || access point |
| **API** || application programming interface |
| **B2B** || business to business |
| **B2C** || business to consumer |
| **BBB** || Better Business Bureau |
| **BCP** || business continuity planning |
| **C2C** || consumer to consumer |
| **CA** || certificate authority |
| **CAP** || Certification and Accreditation Professional |
| **CAUCE** || Coalition Against Unsolicited Commercial Email |
| **CCC** || CERT Coordination Center |
| **CCNA** || Cisco Certified Network Associate |
| **CERT** || Computer Emergency Response Team |
| **CFE** || Certified Fraud Examiner |
| **CISA** || Certified Information Systems Auditor |
| **CISM** || Certified Information Security Manager |
| **CISSP** || Certified Information System Security Professional |
| **CMIP** || Common Management Information Protocol |
| **COPPA** || Children’s Online Privacy Protection |
| **CRC** || cyclic redundancy check |
| **CSI** || Computer Security Institute |
| **CTI** || Computer Telephony Integration |
| **DBMS** || database management system |
| **DDoS** || distributed denial of service |
| **DES** || Data Encryption Standard |
| **DMZ** || demilitarized zone |
| **DoS** || denial of service |
| **DPI** || deep packet inspection |
| **DRP** || disaster recovery plan |
| **DSL** || digital subscriber line |
| **DSS** || Digital Signature Standard |
| **DSU** || data service unit |
| **EDI** || Electronic Data Interchange |
| **EIDE** || Enhanced IDE |
| **FACTA** || Fair and Accurate Credit Transactions Act |
| **FAR** || false acceptance rate |
| **FBI** || Federal Bureau of Investigation |
| **FDIC** || Federal Deposit Insurance Corporation |
| **FEP** || front-end processor |
| **FRCP** || Federal Rules of Civil Procedure |
| **FRR** || false rejection rate |
| **FTC** || Federal Trade Commission |
| **FTP** || file transfer protocol |
| **GIAC** || Global Information Assurance Certification |
| **GLBA** || Gramm-Leach-Bliley Act |
| **HIDS** || host-based intrusion detection system |
| **HIPAA** || Health Insurance Portability and Accountability Act |
| **HIPS** || host-based intrusion prevention system |
| **HTTP** || hypertext transfer protocol |
| **HTTPS** || HTTP over Secure Socket Layer |
| **HTML** || hypertext markup language |
| **IAB** || Internet Activities Board |
| **IDEA** || International Data Encryption Algorithm |
| **IDPS** || intrusion detection and prevention |
| **IDS** || intrusion detection system |
| **IEEE** || Institute of Electrical and Electronics Engineers |
| **IETF** || Internet Engineering Task Force |
| **InfoSec** || information security |
| **IPS** || intrusion prevention system |
| **IPSec** || IP Security |
| **IPv4** || Internet protocol version 4 |
| **IPv6** || Internet protocol version 6 |
| **IRS** || Internal Revenue Service |
| **(ISC)²** || International Information System Security Certification Consortium |
| **ISO** || International Organization for Standardization |
| **ISP** || Internet service provider |
| **ISS** || Internet security systems |
| **ITRC** || Identity Theft Resource Center |
| **IVR** || interactive voice response |
| **LAN** || local area network |
| **MAN** || metropolitan area network |
| **MD5** || Message Digest 5 |
| **modem** || modulator demodulator |
| **NFIC** || National Fraud Information Center |
| **NIDS** || network intrusion detection system |
| **NIPS** || network intrusion prevention system |
| **NIST** || National Institute of Standards and Technology |
| **NMS** || network management system |
| **OS** || operating system |
| **OSI** || open system interconnection |
| **PBX** || private branch exchange |
| **PCI** || Payment Card Industry |
| **PGP** || Pretty Good Privacy |
| **PKI** || public key infrastructure |
| **RAID** || redundant array of independent disks |
| **RFC** || Request for Comments |
| **RSA** || Rivest, Shamir, and Adleman (algorithm) |
| **SAN** || storage area network |
| **SANCP** || Security Analyst Network Connection Profiler |
| **SANS** || SysAdmin, Audit, Network, Security |
| **SAP** || service access point |
| **SCSI** || small computer system interface |
| **SET** || Secure electronic transaction |
| **SGC** || server-gated cryptography |
| **SHA** || Secure Hash Algorithm |
| **S-HTTP** || secure HTTP |
| **SLA** || service level agreement |
| **SMFA** || specific management functional area |
| **SNMP** || Simple Network Management Protocol |
| **SOX** || Sarbanes-Oxley Act of 2002 (also Sarbox) |
| **SSA** || Social Security Administration |
| **SSCP** || Systems Security Certified Practitioner |
| **SSL** || Secure Sockets Layer |
| **SSO** || single system sign-on |
| **STP** || shielded twisted cable |
| **TCP/IP** || Transmission Control Protocol/Internet Protocol |
| **TCSEC** || Trusted Computer System Evaluation Criteria |
| **TFTP** || Trivial File Transfer Protocol |
| **TNI** || Trusted Network Interpretation |
| **UDP** || User Datagram Protocol |
| **UPS** || uninterruptible power supply |
| **UTP** || unshielded twisted cable |
| **VLAN** || virtual local area network |
| **VOIP** || Voice over Internet Protocol |
| **VPN** || virtual private network |
| **WAN** || wide area network |
| **WLAN** || wireless local area network |
| **WNIC** || wireless network interface card |
| **W3C** || World Wide Web Consortium |
| **WWW** || World Wide Web |

**Glossary of Key Terms**

**  A**

**Access control |** The process of providing and denying access to objects.

**Access control entry (ACE) |** An individual entry in a DACL.

**Access control list (ACL) |** The list of access permissions for an object.

**Active Directory |** A shared database of domain users, groups, computers, resources, and other information, along with network functionality to centralize and standardize network management and interoperation.

**Administrative control |** A management action, written policy, procedure, guideline, regulation, law, or rule of any kind.

**Advanced Encryption Standard (AES) |** An encryption algorithm adopted by the U.S. government in 2002 as the standard for encryption operations.

**Agile development |** A method of developing software that is based on small project iterations, or sprints, instead of long project schedules.

**AGULP |** An acronym for Accounts, Global groups, Universal groups, domain Local groups, and permissions. AGULP is an access control approach that systematically nests individual user accounts in groups that make securing objects more general.

**A-I-C triad |** *See* C-I-A triad.

**Anti-malware shield |** Software that intercepts all incoming (and optionally outgoing) information, scanning each message or file for malware content.

**Anti-spyware software |** Software designed to detect and mitigate spyware.

**Antivirus software |** Software designed to detect and mitigate some types of malware, including mainly viruses, worms, and Trojan horses.

**Application server |** A computer that runs application programs on behalf of remote users.

**Application software |** Computer software designed to allow users to perform specific tasks.

**Asymmetric algorithm |** A cryptographic algorithm that uses two related keys—one key to encrypt data and another key to decrypt data.

**Attack surface |** The collection of all possible vulnerabilities that could provide unauthorized access to computer resources; all of the software a computer runs that is vulnerable to attack.

**Attacker |** Any person or program that attempts to interact with a computer information system in an unauthorized manner.

**Auditing |** The process of collecting performance information on what actions were taken and storing that information for later analysis.

**Authentication |** Proving that provided identity credentials are valid and correct.

**Authorization |** Granting and/or denying access to resources based on the authenticated user.

**Authorized user |** Any user (person or program) that possesses permission to access a resource.

**Availability |** The assurance that requested information is available to authorized uses upon request.

**  B**

**Backup |** A defined collection of copies of files created in case the primary copies of the files are damaged or destroyed.

**Bare metal recovery |** A restore that includes the operating system and all configuration settings.

**Baseline |** A collection of configuration settings often collected and saved for the purposes of comparing to other similar collections of configuration settings; a structured collection, or collection of specific item versions.

**BitLocker |** A Windows feature that encrypts entire volumes and normally uses a computer’s Trusted Platform Module (TPM) hardware to store encryption keys.

**BitLocker To Go |** A Windows feature that encrypts removable media devices.

**Boot device |** Any device, typically a CD, DVD, or USB key, from which a computer will boot and load an operating system.

**Buffer overflow |** A condition in which a running program stores data that is larger than the memory location set aside for the data. The extra data spills over into adjacent memory, causing other data and possibly instructions to be overwritten. An attacker can place specific data in the overflowed buffer to change the instructions a program executes.

**Building Security in Maturity Model (BSIMM) |** A newly published framework for software development that is the result of a study of large organizations that develop software with a specific focus on security.

**Business continuity plan (BCP) |** A plan that ensures an organization can survive any disruption and continue operating.

**Business driver |** Any one of the components, including people, information, and conditions, that support business objectives.

**  C**

**Certificate authority (CA) |** A computer that stores digital certificates and issues them to authenticated subjects.

**Chain of custody |** Documentation that provides details of every move and access of evidence.

**C-I-A triad |** Confidentiality, availability, and integrity, the goals of information security.

**Cipher |** Algorithm for performing encryption and decryption.

**Class Identifiers (CLSIDs) |** GUIDs used in the Windows Registry to identify objects and record many of their attributes.

**Classification |** A level of sensitivity assigned to an object by its owner. An example object could be assigned as top secret, secret, confidential, restricted, or unclassified.

**Clearance |** A security level assigned to subjects, authorizing them to access objects with an equal or lower classification. Clearance levels include top secret, secret, and confidential.

**Cloud computing |** The practice of renting computer resources from a provider instead of owning the resources.

**Coaxial cable |** Network cabling that consists of a single copper conductor surrounded with a plastic sheath, then a braided copper shield, and then the external insulation.

**Common Criteria for Information Technology Security Evaluation |** An international set of standards for functionality and assurance of computer security. The Common Criteria superseded the Orange Book as well as other standards.

**Compensating control |** An alternate security control that fulfills an original goal without implementing the primary control.

**Compliance |** The process of ensuring that the items in each domain of the IT infrastructure meet or exceed security goals.

**Computer environment |** A collection of computer and network devices connected to one or more networks, generally for the purpose of fulfilling business functions. Also called IT Infrastructure.

**Confidentiality |** The assurance that information can be accessed and viewed only by authorized users.

**Configuration Control Board (CCB) |** A person or group of people responsible for making decisions about changes to the system definition during the course of the development life cycle.

**Container |** A site, a domain, or an organizational unit in Active Directory.

**Control |** Any mechanism or action that prevents, detects, or addresses an attack.

**Corrective control |** A control that repairs the effects of damage from an attack. Corrective controls include virus removal procedures, firewall table updates, and user authorization database updates.

**  D**

**Data at rest |** Data that is stored on a persistent storage device, such as a disk drive.

**Data in transit |** Data that is currently being transported from one location to another, as in a transfer across a network connection.

**Decomposition |** Breaking down a software development project into distinct phases.

**Decryption key |** A piece of information that an algorithm needs as input to decrypt or “unlock” a document to make it readable.

**Defense in depth |** A security strategy that relies on multiple layers of security that require attackers to defeat multiple controls to access any protected resource.

**Deliverable |** Any object created as a result of project activities.

**Demilitarized zone (DMZ) |** An untrusted network created by using one or more firewalls to separate an untrusted network from a trusted network.

**Deming cycle |** *See* Plan, Do, Check, Act.

**Denial of service (DoS) attack |** An attack that sends a large volume of network messages that end up flooding the network and making it unusable for legitimate traffic.

**Detective control |** A control that detects when an action has occurred. Detective controls include smoke detectors, log monitors, and system audits.

**Digital certificate |** Another term for security certificate.

**Directory Service Restore Mode (DSRM) |** A special mode that allows administrators to create an offline copy of Active Directory (AD).

**Disaster recovery plan (DRP) |** A plan that ensures the infrastructure is operational and ready to support primary business functions.

**Discretionary access control (DAC) |** An access control method based on an object’s owner and permissions granted by the owner.

**Discretionary access control list (DACL) |** The list of access permissions for an object, based on access granted by the object’s owner.

**Distributed denial of service (DDoS) attack |** A DoS attack in which the controller instructs one or more compromised computers to flood a network with packets.

**Documentary evidence |** Any written evidence, such as printed reports or data in log files.

**Domain controller |** A server computer designated to handle Active Directory requests.

**Due diligence |** The ongoing attention and care an organization places on security and compliance.

**Dynamic Access Control (DAC) |** A collection of features that describe user and data attributes; these attributes help Windows protect files using policies that provide more control over who can access data.

**  E**

**Effective Permissions |** The page within the Advanced Security Settings dialog box of Windows that displays calculated permissions for any user or group.

**Elliptic Curve Cryptography (ECC) |** A public key cryptographic algorithm based on the structure of elliptic curves.

**Encapsulating protocol |** A rule that handles addressing and encryption issues.

**Encrypting File System (EFS) |** A Windows feature that provides transparent file and folder encryption. Encryption keys in EFS are based on a user’s password.

**Encryption |** The process of transforming readable information into unreadable information in such a way that anyone with a proper key can reverse the process, making the information readable again.

**End-User License Agreement (EULA) |** An agreement between the software producer and the end user. The EULA addresses issues regarding approved use and liability. Also called a Software License Agreement.

**Enterprise Resource Planning (ERP) |** An integrated collection of software programs that are used to manage many aspects of a business, including financials, human resources, assets, and business processes.

**Event |** Any observable occurrence within a computer or network.

**Exploit |** To take advantage of a specific vulnerability.

**  F**

**Fiber optic cable |** Network cabling that consists of a glass core surrounded by several layers of protective materials.

**File Classification Infrastructure (FCI) |** A feature of Windows that provides the ability to define classification properties for files.

**File server |** A computer or hardware device that has one or more connected hard disk drives, a network interface, and software to provide network access to files and folders on the attached disks.

**File Transfer Protocol (FTP) |** A popular protocol used to transfer files from one computer to another.

**Firewall |** A device or software program to filter data passing through the device or program, limiting network traffic to authorized traffic only.

**Full Disk Encryption (FDE) |** A form of encryption in which the disk controller encrypts each block. FDE is faster than FVE, since it occurs at a lower level than the operating system.

**Full Volume Encryption (FVE) |** A method for encrypting a single partition, either physical or virtual, on a hard drive.

**  G**

**Gateway |** A network device that connects two or more separate networks that use different protocols.

**Globally unique identifier (GUID) |** Identification value that is unique across all environments to keep track of an object across many computers.

**Group |** A set of named entities that define a group of users for the purpose of defining permissions that apply to multiple users.

**Group Policy |** Centralized set of rules that govern the way Windows operates.

**Group Policy Inventory tool |** Utility to collect deployed GPO and computer information that is used to verify Group Policy implementations.

**Group Policy Management Console (GPMC) |** Utility used to create, edit, and manage AD GPOs.

**Group Policy Object (GPO) |** A named object that contains a collection of Group Policy settings.

**Group Policy Update tool |** Utility to immediately deploy and apply GPOs.

**  H**

**Hacktivist |** A hacker who is, or claims to be, motivated by political or social justice concerns and uses hacking skills to reinforce his or her chosen position.

**Hardening |** The process of making configuration changes and deploying controls to reduce the attack surface.

**Hardware Abstraction Layer (HAL) |** Software layer in the operating system kernel that provides the actual access to physical hardware.

**Heuristics |** The practice of identifying malware based on previous experience.

**Hub |** A network device with several connectors, or ports, that allows multiple network cables to attach to it.

**Hyper-V |** A product that supports creating and running virtual machines in Windows Server 2008.

**Hypertext Transfer Protocol (HTTP) |** An application layer protocol used to transfer content between Web browsers and Web servers.

**Hypertext Transfer Protocol Secure (HTTPS) |** A secure application layer protocol used to transfer encrypted content between Web browsers and Web servers. HTTPS encrypts traffic by sending HTTP messages over SLS/TLS.

**  I**

**Identification |** Providing credentials that claim a specific identity, such as a user name.

**IEEE 802.11 |** Defines standards for wireless local area network (WLAN) communication protocols.

**Incident |** An event that results in violating your security policy, or poses an imminent threat to your security policy.

**Institute of Electrical and Electronics Engineers (IEEE) |** Defines standards for many aspects of computing and communications.

**Integrity |** The assurance that information can be modified only by authorized users.

**Internet gateway |** A gateway that connects a LAN to the Internet.

**Internet Protocol Security (IPSec) |** A framework of open standards for protecting communications over Internet Protocol (IP) networks.

**Intrusion detection system (IDS) |** A network device or software that can analyze traffic and detect a potential intrusion based on traffic patterns.

**Intrusion prevention system (IPS) |** A network device or software that can analyze traffic and detect a potential intrusion based on traffic patterns and can also change firewall rules in real time to prevent further damage from an attack.

**  K**

**Kerberos |** A computer network authentication protocol which allows computers to communicate in a secure manner across an insecure network, and the default authentication protocol for Windows.

**Kernel |** The core part of an operating system that provides the essential services of the operating system.

**Key distribution center (KDC) |** A computer designated to authenticate users and, upon authentication, issue Kerberos keys that will allow subjects to access objects.

**  L**

**Layer 2 Tunneling Protocol (L2TP) |** A tunneling protocol used to support VPNs.

**Least privilege user accounts (LUAs) |** User accounts that are defined using the principle of least privilege.

**Local area network (LAN) |** A network that covers a small physical area, such as an office or building.

**Local Group Policy Editor |** Editor for local Group Policy settings.

**Local resource |** Any resource attached to a local computer—the same computer to which the user has logged on.

**Logical control |** An alternate term for technical control.

**  M**

**Malicious software |** Software that is designed to infiltrate a target computer and make it do something the attacker has instructed it to do.

**Malware |** A common term used to describe malicious software, including viruses, worms, and Trojan horses, especially in combinations.

**Managed service accounts |** Accounts that administrators can create as managed domain accounts to provide automatic password management.

**Man-in-the-middle attack |** An attack in which the attacker is located between a client and a server and intercepts traffic flowing back and forth between the two computers. The attacker can view or modify data that is transmitted in the clear.

**Mandatory access control (MAC) |** An access control method based on the subject’s clearance and the object’s classification. MAC implementations often also require demonstration of a subject’s “need to know” to receive access.

**Message digest |** A shortened unique string of digits that represents a file or message.

**Metropolitan area network (MAN) |** A network that connects two or more LANs but does not span an area larger than a city or town.

**Microkernel |** The portion of an operating system’s kernel that resides exclusively in memory.

**Microsoft Baseline Security Analyzer (MBSA) |** An easy-to-use tool that evaluates the current security state of computers in accordance with Microsoft security recommendations.

**Microsoft Management Console (MMC) |** A graphical user interface framework that provides a centralized method to manage software components on Windows computers.

**Multifactor authentication |** Authentication process that requires multiple types of authentication credentials.

**  N**

**NetChk Protect |** A security scanner from Shavlik that scans and analyzes the patch status of products MBSA does not support. Shavlik also produces the scaled-down version of its scanner called NetChk Protect Limited.

**Network |** A collection of computers and devices connected by some connection media.

**Network access control (NAC) |** A solution that defines and implements a policy that describes the requirements to access your network.

**Network address translation (NAT) |** A technique used in many firewalls that translates internal IP addresses into an external IP address. This feature hides the true IP address of internal computers from outside nodes.

**Network Translation LAN Manager (NTLM) |** Authentication protocol used in legacy Windows systems to support secure communications across an insecure network.

**Nmap |** An open source utility used to scan one or more computers or network devices for open ports and other information.

**Node |** Any computer or device connected to a network.

**Nonrepudiation |** This allows a sender to verify the source of a message.

**  O**

**Object |** A resource to which access is controlled.

**Online Software Inspector (OSI) |** A consumer-based vulnerability scanner from Secunia that searches for vulnerable or out-of-date programs and plug-ins. OSI runs in a Web browser and does not need to be installed on the computer it is scanning.

**Open Systems Interconnection (OSI) Reference Model |** A generic description for how computers use multiple layers of protocol rules to communicate across a network. The OSI Reference Model defines seven different layers of communication.

**Orange Book |** United States Department of Defense Trusted Computer System Evaluation Criteria, (DOD-5200.28-STD), was one of the early formal standards for computer security.

**Organizational unit (OU) |** AD containers that group computers either logically or functionally.

**  P**

**Permission |** Permissions define what a user can do to a specific object, such as read or delete the object.

**Personal Software Inspector (PSI) |** A consumer-based vulnerability scanner from Secunia that searches for vulnerable or out-of-date programs and plug-ins. PSI must be installed on the computer before you can use it to scan for vulnerabilities.

**Physical control |** A device that limits access or otherwise protects a resource, such as a fence, door, lock, or fire extinguisher.

**Plaintext |** Unencrypted data, also known as cleartext.

**Plan-Do-Check-Act (PDCA) |** A quality method indicating a continuous process consisting of four repeating steps: Plan, Do, Check, Act. PDCA is also known as a Deming cycle.

**Point to Point Tunneling Protocol (PPTP) |** A tunneling protocol used to support VPNs.

**Port |** In the context of network protocols, a numeric identifier that programs use to classify network messages.

**Pre-shared key (PSK) |** A shared secret used by cryptographic algorithms to perform symmetric encryption and decryption.

**Preventive control |** A control that stops an action before it occurs. Preventive controls include locked doors, firewall rules, and user passwords.

**Primary copy |** The copy of any piece of information that you use most frequently.

**Principle of least privilege |** The practice of providing a user or process with only the necessary access required to carry out a task.

**Print server |** A computer or network device that provides the interface between the network and one or more printers.

**Privilege escalation |** Adding more authority to the current session than the process should possess.

**Profiling |** The process of comparing real computer configurations with known baselines for the purpose of documenting the pertinent differences with secure settings and similarities to insecure settings.

**Protocol |** A set of rules that govern communication.

**Public key |** An encryption key that can be shared and does not need to be kept private.

**Public key cryptography (PKC) |** Cryptographic algorithm that uses two related keys—one key to encrypt data and another key to decrypt data.

**Public key infrastructure (PKI) |** A general approach to handling encryption keys using trusted entities and digital certificates; the hardware, software, policies, and procedures to manage all aspects of digital certificates.

**  Q**

**Query |** A statement that accesses data in a database.

**  R**

**Ransomware |** A type of malware that attempts to generate funds directly from a computer user by attacking the computer and limiting the user’s ability to access it until some money is paid.

**Real evidence |** Any physical object that you can bring into court that you can touch, hold, and directly observe.

**Recovery key |** Key that can be used to decrypt BitLocker-protected data if the primary key is lost or damaged.

**Recovery time objective (RTO) |** The amount of time it should take to recover a resource and bring it back to normal operation.

**Redundant array of independent disks (RAID) |** A collection of disks organized in a way that protects data by duplicating it or writing extra information to reconstruct any damaged data.

**Registration authority (RA) |** A computer that authenticates subjects and directs the CA to issue digital certificates to authenticated subjects.

**Registry |** Database for Windows configuration settings.

**Registry Editor |** Editor for Windows Registry contents.

**Remote resource |** Any resource attached to another computer on a network that is different from the computer to which the user is logged on.

**Restore operation |** The process of copying secondary copies of files back to their primary locations.

**Resultant Set of Policy (RSOP) tool |** Utility that shows the settings that result from existing or planned GPOs for a specific computer and user.

**Right |** User rights define tasks that a user is permitted to carry out, such as take ownership of objects or shut down the computer.

**Rights Management Services (RMS) |** A security feature of Windows, which can encrypt files that contain tagged sensitive data without requiring user interaction.

**Risk |** Any exposure to a threat.

**Role |** A predefined set of services, programs, and configuration settings that enable a computer to fulfill a specific set of requirements.

**Role based access control (RBAC) |** An access control method based on permissions defined by a role, e.g., manager, authorized user, guest, as opposed to an individual user, e.g., Michael Solomon.

**Rootkit |** Software that modifies or replaces one or more existing programs, often part of the operating system, to hide the fact a computer has been compromised.

**Router |** A network device that examines the destination address and then forwards the packet to the correct outbound port.

**  S**

**Schema |** A description of components stored in a database.

**Secondary copy |** A copy of information created to assist in the recovery of the information in the event the primary copy is damaged or destroyed.

**Secure Hash Algorithm (SHA) |** A set of hash functions adopted by the National Security Agency as a U.S. government information processing standard.

**Secure Socket Tunneling Protocol (SSTP) |** VPN protocol that creates an encrypted tunnel over SSL/TLS.

**Secure Sockets Layer (SSL) |** The predecessor to TLS, SSL is a cryptographic protocol that operates at the transport network layer and provides security for communications across the Internet.

**Security Access Token (SAT) |** A document used by Windows to store all SIDs associated with a process.

**Security administration |** The process of implementing the security controls within the IT infrastructure.

**Security certificate |** A document that contains identity information and a public key, along with other descriptive information. Also called a digital certificate.

**Security Configuration and Analysis (SCA) |** A tool that helps administrators to analyze a computer and compare its configuration settings against a baseline.

**Security Configuration Wizard (SCW) |** A Microsoft utility that provides guidance to administrators and creates policies based on the least privilege principle for the server roles you have selected either during installation or afterward using the Server Manager Utility.

**Security control |** A mechanism used to protect information and related assets.

**Security Development Lifecycle (SDL) |** A security assurance process that is focused on software development.

**Security filter |** GPO filter that limits a GPO’s scope to specific computers or users.

**Security identifier (SID) |** A unique identifier for each user and group in a Windows environment.

**Security incident response team (SIRT) |** A team of representatives from IT, management, legal, and public relations that is organized to respond to incidents.

**Security template |** A text file that contains a list of configuration settings.

**Server core installation |** A Windows Server 2008 R2 installation option that provides a minimal environment that includes only programs necessary for the roles you select.

**Service Set Identifier (SSID) |** A unique identifier for a wireless network.

**Shielded twisted pair (STP) |** Network cabling that generally consists of two or four pairs of wires with a foil shielding around each pair to reduce external electrical and radio interference. Pairs of wires are twisted around each other to reduce interference with other pairs.

**Signature |** The unique set of instructions that make up an instance of malware and distinguish it from other malware.

**Signature database |** An organized collection of malware signatures used by antivirus or anti-spyware (or other antimalware) software to identify malware.

**Smart card |** A card or device that stores information used for authentication or encryption.

**Snap-in |** An administrative program designed to run in the MMC.

**Social engineering |** The process of an attacker tricking or convincing an authorized user to carry out an action or provide valuable information for which the attacker is unauthorized.

**Software configuration management (SCM) |** A collection of best practices for handling changes in software projects.

**Software Security Framework (SSF) |** A component of the BSIMM that organizes the 109 BSIMM activities into a framework consisting of 12 practices in four domains.

**Spoofing |** The act of masquerading as another identity.

**Sprint |** One of the small project iterations used in the “agile” method of developing software, in contrast with the usual long project schedules of other ways of developing software.

**Spyware |** Software that covertly monitors and records pieces of information such as Web surfing activities and all data processed by the browser.

**SQL injection |** An attack that adds SQL statements to input data for the purpose of sending commands to a database management system.

**Structured Query Language (SQL) |** A computer language for accessing data in a database.

**Subject |** An entity requesting access to an object.

**Supervisor mode |** The highest privilege at which programs can run, allowing access to the physical hardware and kernel resources. Also called kernel mode.

**Switch |** A network hardware device that forwards input it receives only to the appropriate output port.

**Symmetric key algorithm |** Encryption algorithm that uses a single key for both encryption and decryption.

**System Development Life Cycle (SDLC) |** A formal model for the process of creating and modifying software.

**  T**

**TCP/IP Reference Model |** A generic description for how computers use multiple layers of protocol rules to communicate across a network. The TCP/IP Reference Model defines four different layers of communication rules.

**Technical control |** A device or process that limits access to a resource. Examples include user authentication, antivirus software, and firewalls.

**Threat |** Any action that could lead to damage or loss.

**Transmission Control Protocol/Internet Protocol (TCP/IP) |** A combination of two separate protocols commonly used in Internet network communication.

**Transparent Data Encryption (TDE) |** An option in several database management systems that encrypts all data in the database without any user or application action required.

**Transport Layer Security (TLS) |** Cryptographic protocol that operates at the transport network layer and provides security for communications across the Internet.

**Trojan horse |** Software that masquerades as an apparently harmless program or data file but contains malware instructions.

**Trusted Platform Module (TPM) |** Microchip designed to securely store cryptographic keys.

**Trusted source |** A computer from which digital certificates are accepted.

**Tunneling |** A technique that creates a virtual encrypted connection and allows applications to use any protocol to communicate with servers and services without having to worry about addressing or privacy concerns.

**Two-factor authentication |** Authentication process that requires two separate types of authentication credentials.

**Type I authentication |** Authentication based on information only a valid user knows, such as a password or PIN.

**Type II authentication |** Authentication based on a physical object that contains identity information, such as a token, card, or other device.

**Type III authentication |** Authentication based on a physical characteristic (biometric), such as a fingerprint, hand print, or retina characteristic.

**  U**

**Unauthorized user |** Any user (person or program) that does not possess permission to access a resource.

**Uniform resource locator (URL) |** A character string used to identify the location and name of a resource on the Internet.

**Unshielded twisted pair (UTP) |** Network cabling that generally consists of two or four pairs of wires. Pairs of wires are twisted around each other to reduce interference with other pairs.

**User Account Control (UAC) |** Windows feature that prompts users for a confirmation before escalating to administrator privileges.

**User mode |** Limited privilege for running programs that does not allow direct access to the computer’s physical hardware or certain kernel resources.

**  V**

**Virtual machine |** A software implementation of a physical computer.

**Virtual private network (VPN) |** A computer network that is implemented over an existing network, often to provide an encrypted tunnel to exchange data securely.

**Virtualization |** The ability to run two or more virtual machines simultaneously on a single physical computer.

**Virus |** A software program that attaches itself to, or copies itself into, another program for the purpose of causing the computer to follow instructions that were not intended by the original program developer.

**Volume Shadow Copy Service (VSS) |** A Windows service that assists utilities and applications in creating snapshots of a running Windows system.

**Vulnerability |** Any weakness that could allow a threat to be realized.

**  W**

**Web proxy |** A server that receives a Web request, processes the request based on defined filters, and acts on the request based on defined rules. Rules can include actions such as forward, drop, deny, and translate.

**Wi-Fi Protected Access (WPA) |** Algorithm designed to replace WEP by providing secure wireless communications.

**Wide area network (WAN) |** A network that connects multiple LANs and WANs and spans very large areas, including multiple country coverage.

**Windows Management Instrumentation (WMI) |** The infrastructure Windows uses to maintain and exchange management and operations data.

**Windows service |** A long-running program that performs a specific set of functions, such as a firewall, database server, or a Web server.

**Wired Equivalent Privacy (WEP) |** Legacy algorithm designed to secure wireless communications.

**Wireless local area network (WLAN) |** A LAN in which computers and devices communicate using radio frequency transmissions.

**WMI filter |** GPO filter that limits a GPO’s scope based on a WMI query’s result.

**WMI Query Language (WQL) |** Subset of SQL used to query Windows machines for management and operations data.

**Worm |** A standalone malicious software program that actively transmits itself, generally over networks, to infect other computers.

**  Z**

**Zero-day attack |** Active malware that either exploits an unknown vulnerability or one for which no fix has yet been released.

**Zombie |** A computer that follows the instructions sent from another computer.

**References**

Altholz, Nancy, and Larry Stevenson. *Rootkits for Dummies (For Dummies \[Computer/Tech\])*. Hoboken, NJ: Wiley, 2007.

Barrett, Larry. “Symantec’s ‘Unlucky 13’ Security Trends for 2010.” [InternetNews.com](http://InternetNews.com), November 20, 2009. [http://www.internetnews.com/security/article.php/3849371/Symantecs-Unlucky-13-Security-Trends-for-2010.htm](http://www.internetnews.com/security/article.php/3849371/Symantecs-Unlucky-13-Security-Trends-for-2010.htm) (accessed May 24, 2010).

Black, Mike, and Daniel Castillo. *Backup Exec 9: For Windows Servers*. Plano, TX: Wordware Publishing, Inc., 2004.

Bott, Ed, Carl Siechert, and Craig Stinson. *Windows*^® *7 Inside Out*. Redmond, WA: Microsoft Press, 2009.

Bragg, Roberta. *Hardening Windows Systems*. New York: McGraw-Hill Osborne Media, 2008.

Crawford, Sharon, and Charlie Russel. *Windows Server 2008 Administrator’s Companion*. Redmond, WA: Microsoft Press, 2008.

d2d. “Incident: Heartland Payment Systems Data Breach—Malicious Software/Hack compromises unknown number of credit cards at fifth largest credit card processor | DataLossDB.” OSF DataLossDB | Data Loss News, Statistics, and Research, 2010. [http://datalossdb.org/incidents/1518-malicious-software-hack-compromises-unknown-number-of-credit-cards-at-fifth-largest-credit-card-processor](http://datalossdb.org/incidents/1518-malicious-software-hack-compromises-unknown-number-of-credit-cards-at-fifth-largest-credit-card-processor) (accessed May 20, 2010).

———. “Incident: TJX Companies Inc. Data Breach—Hack exposes 94 million credit card numbers and transaction details | DataLossDB.” OSF DataLossDB | Data Loss News, Statistics, and Research, 2010. [http://datalossdb.org/incidents/548-hack-exposes-94-million-credit-card-numbers-and-transaction-details](http://datalossdb.org/incidents/548-hack-exposes-94-million-credit-card-numbers-and-transaction-details) (accessed May 20, 2010).

———. “Incident: T-Mobile, Deutsche Telekom Data Breach—T-Mobile lost disk containing data on 17 million customers | DataLossDB.” OSF DataLossDB | Data Loss News, Statistics, and Research, 2010. [http://datalossdb.org/incidents/1172-t-mobile-lost-disk-containing-data-on-17-million-customers](http://datalossdb.org/incidents/1172-t-mobile-lost-disk-containing-data-on-17-million-customers) (accessed May 20, 2010).

Davis, Chris, Mike Schiller, and Kevin Wheeler. *IT Auditing: Using Controls to Protect Information Assets*. 1st ed. New York: McGraw-Hill Osborne Media, 2006.

Eagle, Chris, Allen Harper, Shon Harris, and Jonathan Ness. *Gray Hat Hacking*. 2nd ed. New York: McGraw-Hill Osborne Media, 2007.

Faircloth, Jeremy, and Paul Piccard. *Combating Spyware in the Enterprise*. Rockland, MA: Syngress Publishing, Inc., 2006.

Grimes, Roger A. *Professional Windows Desktop and Server Hardening*. Indianapolis, IN: Wiley, 2006.

Hanrion, Patrick, and Bill Stackpole. *Software Deployment, Updating, and Patching (Information Security)*. 1st ed. Boca Raton, FL: CRC Press, 2007.

Hassell, Jonathan. *Hardening Windows*. 2nd ed. Berkeley, CA: Apress, 2006.

Holme, Dan. *Windows Administration Resource Kit: Productivity Solutions for IT Professionals*. Redmond, WA: Microsoft Press, 2008.

Honeycutt, Jerry, Tony Northrup, and Mitch Tulloch. *Windows*^® *7 Resource Kit (PRO—Resource Kit)*. Redmond, WA: Microsoft Press, 2009.

Johansson, Jesper M. *Windows Server 2008 Security Resource Kit (PRO—Resource Kit)*. Redmond, WA: Microsoft Press, 2008.

Keyes, Jessica. *Software Configuration Management*. Boca Raton, FL: CRC Press LLC, 2004.

Kezema, Conan, Mike Mulcare, Stan Riemer, and Byron Wright. *Windows Server 2008 Active Directory Resource Kit*. Redmond, WA: Microsoft Press, 2008.

Kizza, Joseph Migga. *Securing the Information Infrastructure*. Hershey, PA: IGI Global, 2007.

Korelc, Justin, and Ed Tittel. *Windows Server 2008 For Dummies (For Dummies \[Computer/Tech\])*. Hoboken, NJ: Wiley, 2008.

Mackin, J. C., and Charlie Russel. *Windows*^® *Essential Business Server 2008 Administrator’s Companion*. Redmond, WA: Microsoft Press, 2009.

Mackin, J. C., and Tony Northrup. *MCITP Self-Paced Training Kit (Exam 70-685): Windows*^® *7 Enterprise Desktop Support Technician: Windows 7 Enterprise Desktop Support Technician (Pro—Certification)*. 1st ed. Redmond, WA: Microsoft Press, 2010.

Matthews, Marty. *Microsoft Windows Server 2008: A Beginner’s Guide (Network Professional’s Library)*. 1st ed. New York: McGraw-Hill Osborne Media, 2008.

Mclean, Ian, and Orin Thomas. MCITP Self-Paced Training Kit (Exam 70-646): *Windows Server*^® *Administration (PRO—Certification)*. Redmond, WA: Microsoft Press, 2008.

Melber, Derek. *Windows*^® *Group Policy Resource Kit: Windows Server*^® *2008 and Windows Vista*^®. Redmond, WA: Microsoft Press, 2008.

Moskowitz, Jeremy. *Creating the Secure Managed Desktop: Using Group Policy, SoftGrid, Microsoft Deployment Toolkit, and Other Management Tools*. Indianapolis, IN: Sybex, 2008.

———. *Group Policy: Fundamentals, Security, and Troubleshooting*. Indianapolis, IN: Sybex, 2008.

Northcutt, Stephen. *Computer Security Incident Handling: Step-by-Step (Version 2.3.1)*. Bethesda, MD: Sans Institute, 2003.

Northrup, Tony, and Joseph Davies. *Windows Server 2008 Networking and Network Access Protection (NAP)*. Redmond, WA: Microsoft Press, 2008.

Piltzecker, Anthony. *The Best Damn Windows Server 2008 Book Period*. 2nd ed. Burlington, MA: Syngress Publishing, Inc., 2008.

Ruest, Danielle, and Nelson Ruest. *Microsoft Windows Server 2008: The Complete Reference (Complete Reference Series)*. 1st ed. New York: McGraw-Hill Osborne Media, 2008.

Scambray, Joel. *Hacking Exposed Windows: Windows Security Secrets and Solutions*. 3rd ed. New York: McGraw-Hill Osborne Media, 2007.

Seagren, Eric. *Secure Your Network for Free*. Rockland, MA: Syngress Publishing, Inc., 2007.

Seguis, Steve. *Microsoft Windows Server 2008 Administration (Network Professionals Library)*. 1st ed. New York: McGraw-Hill Osborne Media, 2008.

Shapiro, Jeffrey R. *Windows Server 2008 Bible*. New York: Wiley, 2008.

Solomon, Michael, Neil Broom, and Diane Barrett. *Computer Forensics JumpStart (Jumpstart \[Sybex\])*. Alameda, CA: Sybex Inc., 2004.

Stanek, William R. *Windows*^® *7 Administrator’s Pocket Consultant*. Redmond, WA: Microsoft Press, 2009.

Tayntor, Christine B. *Six Sigma Software Development*. 2nd ed. Chicago: Auerbach Publications, 2007.

Thuraisingham, Bhavani. *Database and Applications Security: Integrating Information Security and Data Management*. 1st ed. Chicago: Auerbach, 2005.

Tulloch, Mitch. *Introducing Windows Server 2008*. Redmond, WA: Microsoft Press, 2007.

Vacca, John R. *Computer and Information Security Handbook*. San Francisco: Morgan Kaufmann, 2009.

**Index**

*The index that appeared in the print version of this title was intentionally removed from the eBook. Please use the search function on your eReading device to search for terms of interest. For your reference, the terms that appear in the print index are listed below.*

**  A**

acceptable use policy (AUP)

access control

access control entry (ACE)

access control lists (ACLs)

access control methods

access management tools

access permissions

access rules

account lockout policy

account policy

ACE. *See* access control entry

ACLs. *See* access control lists

Active Directory (AD)

Active Directory Domain Services server

Active Directory Group Policies

ActiveX controls

activities

activity coordination

AD. *See* Active Directory

Add Roles Wizard

Add/Remove Programs utility

administrative controls

administrator account

Advanced Encryption Standard (AES)

advanced security settings dialog

AES. *See* Advanced Encryption Standard

agile method

agile software development

AGULP approach

A-I-C triad

Allow ACE

analysis step

anti-malware protection

anti-malware shield

anti-malware software

anti-spyware software

antivirus software

application encryption

application security

application servers

application software

application software security

applications

AppLocker

apply encryption

architecture

asymmetric algorithms

attack surface

attackers

attacks

audio/video server

audit

audit file access

audit policy

auditing

Auditing Group Policy

AUP. *See* acceptable use policy

authentication

authentication servers

authorization

authorized users

availability

**  B**

backdoor attack

backup administration

Backup and Restore utility

backup media security

backup policies

backups

bare metal recovery

baselines

BCP. *See* business continuity plan

best evidence rule

best practices

BitLocker

BitLocker authentication modes

BitLocker authentication options

BitLocker Drive Encryption

BitLocker installation

BitLocker management tool

BitLocker recovery information

BitLocker To Go

Bluetooth

boot devices

BPA. *See* Group Policy Best Practices Analyzer

BSIMM. *See* Building Security in Maturity Model

buffer overflow

Building Security in Maturity Model (BSIMM)

business continuity plan (BCP)

business drivers

**  C**

CA. *See* certificate authority

cacls.exe CLI tool

campus area network (CAN)

CAN. *See* campus area network

CCB. *See* Configuration Control Board

certificate authority (CA)

chain of custody

change control

checklists

C-I-A triad. *See* confidentiality-integrity-availability triad

cipher

Class Identifiers (CLSIDs)

classification

classify data

clearance

CLI tools. *See* command-line interface tools

client applications

client systems

cloud computing

coaxial cable

code execution

code generation phase

Code Red worm

cold site

command-line interface for MBSA

command-line interface (CLI) tools

command-line server backups

command-line workstation backups

Common Vulnerabilities and Exposures (CVE)

communication data encryption

communication protocols

communication service

communication, SIRT

compensating controls

complete system backup

compliance

computer and device security

computer environment

Computer Management tool

computer virus

Conficker worm

confidentiality

confidentiality-integrity-availability (C-I-A) triad

Configuration Action window

configuration auditing

Configuration Control Board (CCB)

configuration status accounting

connection media

connection security rules

contacts and hierarchy, SIRT communication

containers

containment step in handling incidents

contractors

control

control file access

controlling access

cookie settings

cooperative agreement

Corporate Software Inspector (CSI)

corrective controls

Creator Group ID

Creator Owner ID

Creeper

critical incidents

cross-site scripting attack

CSI. *See* Corporate Software Inspector

customer-facing systems

**  D**

DAC. *See* discretionary access control

DACL. *See* discretionary access control List

Darwin (game)

data at rest

Data Collector Sets

data in transit

data integrity

data loss

data reconstruction

data storage server

database server

Datacenter Edition of Windows Server 2008

Datacenter Edition of Windows Server 2012

DC. *See* Domain Controller

DDoS attack. *See* distributed denial of service attack

decomposition

decryption keys

default ports

default users

defense in depth

deliverables

demilitarized zone (DMZ)

Deming cycle

denial of service (DoS) attack

deploying application software

deployment domain

design guidelines for Group Policy

Desktop Engine product

desktop network security

detective controls

developer security training

developing application software

device driver programs

device security

digital certificates

direct file or resource access

Directory Service Restore Mode (DSRM)

Directory Service Restore Mode (DSRM) password

directory services

directory traversal and listing

disabling programs and services

disaster recovery plan (DRP)

disasters

discovery step

discovery–analysis–remediation cycle

discretionary access control (DAC)

discretionary access control list (DACL)

disk volume encryption

disposition phase

distributed denial of service (DDoS) attack

DMZ. *See* demilitarized zone

documentary evidence

documented plans

domain admin account

Domain Controller (DC)

domain GPOs

domains of IT infrastructure

DoS attack. *See* denial of service attack

Dow Corning

Downadup. *See* Conficker

DRP. *See* disaster recovery plan

DSRM password. *See* Directory Service Restore Mode password

due diligence

DumpSec utility

dynamic access control (DAC)

dynamic code execution

**  E**

eavesdropping

Effective Permissions

EFS. *See* Encrypting File System

e-mail clients

e-mail server

employees

Enabling BitLocker

encapsulating protocol

encrypted data transmission

Encrypting File System (EFS)

encryption

encryption algorithms

End-User License Agreement (EULA)

ENISA Web site. *See* European Network and Information Security Agency Web site

Enterprise Edition of Windows Server 2008

Enterprise Resource Planning (ERP) software

Enterprise Vulnerability Manager (EVM)

entry points

environment subsystem

environmental issues

eradication step in handling incidents

ERP software. *See* Enterprise Resource Planning software

error detection and alerts service

error handling

escalation confirmation

Essentials Edition of Windows Server 2012

European Network and Information Security Agency (ENISA) Web site

event log

Event Viewer

events

evidence

evidence collection rules

EVM. *See* Enterprise Vulnerability Manager

Exchange Server 2010

executive (kernel mode program)

exploits

Expression-Based Security Audit Policy

extra-application data access

**  F**

faulty installation procedure

FDE. *See* Full Disk Encryption

fiber optic cable

file authentication

File Classification Infrastructure (FCI)

file server

file system

file system service

File Transfer Protocol (FTP)

file transfer software

files backup

firewalls

folder encryption

folders backup

formal testing phase

Foundation Edition of Windows Server 2008

Foundation Edition of Windows Server 2012

frequency expectations

FTP. *See* File Transfer Protocol

Full Disk Encryption (FDE)

full interruption test

Full Volume Encryption (FVE)

FVE. *See* Full Volume Encryption

**  G**

GAN. *See* global area network

gateway

Generic Routing Encapsulation (GRE)

global area network (GAN)

global groups

globally unique identifier (GUIDs)

gMSA. *See* group managed server accounts

governance domain

GPMC. *See* Group Policy Management Console

GPOAccelerator tool

GPOs. *See* Group Policy Objects

graphical user interface (GUI)

graphical user interface (GUI) of MBSA

GRE. *See* Generic Routing Encapsulation

group managed server accounts (gMSA)

Group Policy

Group Policy administration

Group Policy Best Practices Analyzer (BPA)

Group Policy Inventory tool (gpinventory.exe)

Group Policy Management Console (GPMC)

Group Policy Management Editor

Group Policy Management Pack

Group Policy Objects (GPOs)

Group Policy Settings Reference

Group Policy Update tool

group security policy objects

group-based ACLs

groups

GUI. *See* graphical user interface

GUI of MBSA. *See* graphical user interface of MBSA

guidelines

GUIDGEN.EXE program

**  H**

hactivists

HAL. *See* Hardware Abstraction Layer

hardening

hardening applications

hardening authentication

hardening communications and remote access

hardening data access and controls

hardening network infrastructure

hardening PKI

hardening server computers

hardening Windows OS

hardening workstation computers

Hardware Abstraction Layer (HAL)

hardware errors

harvesting stored data

hash rules

Health Information Technology for Economic and Clinical Health (HITECH) Act

Health Insurance Portability and Accountability Act (HIPAA)

Health Insurance Portability and Accountability Act (HIPAA) regulations

Heartland Payment Systems incident

heuristic-based tools

heuristics

HIPAA. *See* Health Insurance Portability and Accountability Act

HIPAA regulations. *See* Health Insurance Portability and Accountability Act regulations

HITECH Act. *See* Health Information Technology for Economic and Clinical Health Act

hot site

HPC Edition of Windows Server 2008

HTTP. *See* Hypertext Transport Protocol

HTTPS. *See* Hypertext Transfer Protocol Secure

hubs

hybrid malware

Hypertext Transfer Protocol Secure (HTTPS)

Hypertext Transport Protocol (HTTP)

Hyper-V technology

**  I**

icacls.exe CLI tool

identification

identification step in handling incidents

identify data

identify/react charts

identity spoofing

IDS. *See* intrusion detection system

IEEE. *See* Institute of Electrical and Electronics Engineers

IEEE 802.11

IIS. *See* Internet Information Services

IIS Web server. *See* Internet Information Services Web server

implementation phase

implementation testing

inbound rules

incident classifications

incident data collection and management tools

incident evidence

incident handling and management tools

incident investigation

incident lead on SIRT

incident reporting form

incident response

incident response plan

incident response tools

incident scope

incident severity levels

incidents

information leakage

information systems security

initiation phase

input and output service

input validation

installation procedure

Institute of Electrical and Electronics Engineers (IEEE)

integral subsystem

integrity

intelligence domain

intercept communication

interfaces with other programs

Internet backups

Internet gateway

Internet Information Services (IIS)

Internet Information Services (IIS) Web server

Internet Options dialog in Internet Explorer 8

Internet Protocol Security (IPSec)

Internet Service Providers (ISPs)

Internet-based services

interruptions

intrusion detection system (IDS)

intrusion prevention system (IPS)

investigations

IPSec. *See* Internet Protocol Security

ISPs. *See* Internet Service Providers

IT infrastructure

IT infrastructure domains

IT liaison on SIRT

Itanium edition of Windows Server 2008

**  J**

junk filter function

**  K**

Kerberos

Kerberos policy

kernel

kernel mode programs

Key Distribution Center (KDC)

**  L**

LAN. *See* local area network

laptop computer backups

Layer 2 Forwarding (L2F)

Layer 2 Tunneling Protocol (L2TP)

layered protocols

least privilege user accounts (LUAs)

legal representative on SIRT

lessons learned step in handling incidents

L2F. *See* Layer 2 Forwarding

line of business (LOB) software

LOB software. *See* line of business software

local area network (LAN)

Local Group Policies

Local Group Policy Editor

local resource

Local Security Policy maintenance tool

local users and groups section

log files

logging mode of RSOP

logical access

logical controls

L2TP. *See* Layer 2 Tunneling Protocol

**  M**

MAC. *See* mandatory access control

MAC address filtering. *See* Media Access Control address filtering

mail server

maintaining application software

maintenance phase

malformed input

malicious software

malicious software protection

malware

malware prevention strategies

MAN. *See* metropolitan area network

managed service accounts (MSA)

management on SIRT

mandatory access control (MAC)

man-in-the-middle attack

maximum password age

maximum privilege mode

MBSA. *See* Microsoft Baseline Security Analyzer

MBSA utility. *See* Microsoft Baseline Security Analyzer utility

mbsacli.exe command

Media Access Control (MAC) address filtering

memory-resident kernel

memory-resident kernel code

message digest

metropolitan area network (MAN)

microkernel architecture

Microsoft Active Directory

Microsoft Baseline Security Analyzer (MBSA)

Microsoft Baseline Security Analyzer (MBSA) utility

Microsoft Exchange Server

Microsoft Forefront

Microsoft Internet Information Services (IIS) Web server

Microsoft Malicious Software Removal Tool

Microsoft Management Console (MMC)

Microsoft Office Outlook

Microsoft Operations Manager (MOM)

Microsoft Security Essentials

Microsoft SQL Azure

Microsoft SQL Server

Microsoft Windows

Microsoft Windows Backup and Recovery

Microsoft Windows operating system (OS)

Microsoft Windows restore utility

mitigation

MMC. *See* Microsoft Management Console

MMC snap-in

mobile code attack

mobile devices

monitor system performance measurements

monitoring

Monroe College

Morris worm

MSA. *See* managed service accounts

multifactor authentication

multilayered defense

**  N**

NAC. *See* network access control

NAT. *See* network address translation

National Vulnerability Database

natural disasters

necessary services

need to know (NTK) basis

NetChk Protect

NetChk Protect Limited

network

network access control (NAC)

network access control (NAC) software

network address translation (NAT)

network backups

network bandwidth

network communication protocols

network components

network data storage

network entry

network file server

network infrastructure

network management tools and policies

network print server

network security

network security controls

network services

network traffic filtering

networking devices

nmap utility

nodes

non-Microsoft services

nonrepudiation

NT LAN Manager (NTLM)

**  O**

Object access requests

object DACLs

object properties page

object properties security page

objects

Online Software Inspector (OSI)

Open Systems Interconnection (OSI) Reference Model

Open Web Application Security Project (OWASP)

operating system components

operating system service pack administration

Orange Book

organizational unit GPOs (OU GPOs)

organizational units (OUs)

OSI. *See* Online Software Inspector

OSI Reference Model. *See* Open Systems Interconnection Reference Model

OUs. *See* organizational units

outbound rules

outbound traffic filtering

OWASP. *See* Open Web Application Security Project

**  P**

packet sniffing attack

PAN. *See* personal area network

partial security

password controls

password policy

passwords

patch management

path rules

PDCA process. *See* Plan-Do-Check-Act process

penetration testing

performance

performance information

Performance Monitor

permissions

personal area network (PAN)

personal scanners

Personal Software Inspector (PSI)

Phase Transition

physical access controls

physical and logical access

physical controls

physical security

PKI. *See* public key infrastructure

plaintext (unencrypted)

Plan-Do-Check-Act (PDCA) process

planning

Point-to-Point Protocol (PPP)

Point-to-Point Tunneling Protocol (PPTP)

policies

port scanning

ports

PPP. *See* Point-to-Point Protocol

PPTP. *See* Point-to-Point Tunneling Protocol

preparation step in handling incidents

pre-shared key (PSK) mode

preventive controls

primary copy

principle of least privilege

print server

printer actions auditing

private data disclosure

privilege escalation

privilege escalation request

privileged mode

proactive plan

procedures

process table

productivity software

profiling

Program Files folder

program removal

program/process management service

project management techniques

protocols

PSK. *See* pre-shared key mode

public key

public key cryptography

public key infrastructure (PKI)

public relations representative on SIRT

publisher rules

pull technology

**  Q**

quality process

query

**  R**

RA. *See* registration authority

RADIUS. *See* Remote Authentication Dial In User Service

RAID. *See* redundant array of independent disks

ransomware

RBAC. *See* role based access control

react/identify chart

Read/List access auditing

real evidence

reaper

recovery keys

recovery plan

recovery step in handling incidents

recovery time objective (RTO)

redundant array of independent disks (RAID)

registration authority (RA)

Registry

Registry Editor

regression testing

remediation cycles

remediation step

Remote Authentication Dial In User Service (RADIUS)

remote clients

Remote Registry service

remote resources

remote system access

remote users and systems

remote workstations

removable storage device

removing programs and services

repeatable process

response framework

responsibilities

Restore All Users’ Files link

Restore My Files button

restore operation

restore process

restore uses

restore utilities

restricted groups

Resultant Set of Policy (RSOP) tool

rights

risk

robocopy CLI utility

robocopy.exe

robocopy.exe commands

robot/intermediary process attack

role based access control (RBAC)

roles

rootkits

router

RSOP. *See* Resultant Set of Policy (RSOP) tool

RTO. *See* recovery time objective

**  S**

SAT. *See* Security Access Token

SCA command-line tool

SCA snap-in

SCA tool. *See* Security Configuration and Analysis tool

scanner

scanning process

schemas

SCM. *See* software configuration management

scope of restore operation

scripts

SCW. *See* Security Configuration Wizard

SDLC model. *See* System Development Life Cycle model

secedit.exe

secondary copy

Secunia personal and corporate security analyzers

securable objects

secure accounts for services

secure connections

Secure FTP (SFTP)

Secure Shell (SSH)

Secure Socket Tunneling Protocol (SSTP)

Secure Sockets Layer (SSL)

Secure Sockets Layer/Transport Layer Security (SSL/TLS)

Secure Software Development Lifecycle (SSDL) touch points

Secure Web application connection

securing services

Security Access Token (SAT)

security administration

Security and Configuration Analysis (SCA) snap-in

security audit

security awareness programs

security baseline

security baseline analysis

security certificates

Security Compliance Management Toolkit

Security Configuration and Analysis (SCA)

Security Configuration and Analysis (SCA) tool

Security Configuration Wizard (SCW)

security controls

Security Development Lifecycle (SDL)

security filters of GPO

security goals

security guidelines

security identifiers (SIDs)

security incident response team (SIRT)

security incidents

security monitoring

security options

security patches

security policy

security procedure

security protocols and services

security responsibility

security standard

security templates

security vulnerabilities

Select Role Services for Web Server (IIS) role

Select Server Roles window

sensitive data

separation of duties

separator

server applications

server backups

server computers

server computers and services devices

Server Core

server core installation option

Server Manager tool

Server Manager Utility

server network security

Server Recovery Wizard

servers

service accounts

service level agreement (SLA)

Service Set Identifier (SSID)

service updates

services

services devices

Services MMC snap-in

SFTP. *See* Secure FTP

Shavlik security analyzers

shield

shielded twisted pair (STP) cable

SIDs. *See* security identifiers

signature

signature based anti-malware tools

signature database

SIRT. *See* security incident response team

site GPOs

SLA. *See* service level agreement

smart card

SMEs. *See* subject matter experts

snap-in

social engineering

software configuration management (SCM)

software control

software development

software errors

software license agreement

software project scope

software requirement analysis

Software Restriction Policies (SRP)

Software Security Framework (SSF)

software security management

software testing

software updates

solid disaster recovery plan

SomarSoft utilities

special Windows object permissions

spoofing

Sporton International

sprints

spyware

SQL. *See* Structured Query Language

SQL injection

SQL Slammer worm

SRP. *See* Software Restriction Policies

SSF. *See* Software Security Framework

SSH. *See* Secure Shell

SSID. *See* Service Set Identifier

SSL. *See* Secure Sockets Layer

SSL/TLS. *See* Secure Sockets Layer/Transport Layer Security

SSTP. *See* Secure Socket Tunneling Protocol

stakeholders

standalone firewalls

Standard Edition of Windows Server 2008

Standard Edition of Windows Server 2012

startup type values

STP cable. *See* shielded twisted pair cable

strong authentication

Structured Query Language (SQL)

subject

subject matter experts (SMEs)

supervisor mode

switch

symmetric algorithms

symmetric key

system analysis and design

system configuration information

System Development Life Cycle (SDLC) model

system rebuilding

system services

system/information engineering and modeling

**  T**

TACACS+. *See* Terminal Access Controller Access-Control System Plus

targets

TCP. *See* Transport Control Protocol

TCP/IP. *See* Transmission Control Protocol/Internet Protocol

TCP/IP Reference Model. *See* Transmission Control Protocol/Internet Protocol Reference Model

TDE. *See* Transparent Data Encryption

team lead on SIRT

technical controls

TechRepublic

Telnet protocol

Terminal Access Controller Access-Control System Plus (TACACS+)

test scenarios

thick clients

thin clients

threats

time-tested strategy

T.J. Maxx incident

TLS. *See* Transport Layer Security

T-Mobile incident

Top 10 Web Application Security Risks

TPM. *See* Trusted Platform Module

traditional software development management

traffic flow

Transmission Control Protocol/Internet Protocol (TCP/IP)

Transmission Control Protocol/Internet Protocol (TCP/IP) Reference Model

Transparent Data Encryption (TDE)

Transport Control Protocol (TCP)

Transport Layer Security (TLS)

Trojan horse

Truecrypt

Trusted Platform Module (TPM)

trusted sites

trusted source

tunneling

two-factor authentication

two-way authentication

Type I authentication

Type II authentication

Type III authentication

**  U**

UDP. *See* User Datagram Protocol

UML. *See* unified modeling language

unauthorized users

unified modeling language (UML)

uniform resource locator (URL)

uninstall utility for Windows

United States Computer Emergency Readiness Team (US-CERT)

universal groups

Unprotected Windows Share

unshielded twisted pair (UTP) cable

unused services

URL. *See* uniform resource locator

URL individual parts

user account control (UAC)

user accounts

user actions

user authentication

user authorization

User Configuration category

User Datagram Protocol (UDP)

user identification

user mode

user mode programs

user rights

user rights assignment

user security training and awareness

username (or user ID)

UTP cable. *See* unshielded twisted pair cable

**  V**

vault

VCSs. *See* version control systems

version control systems (VCSs)

VIF. *See* Vulnerable Intelligence Feed

virtual images

virtual machines (VMs)

virtual PC

virtual private network (VPN)

virtualBox

virtualization

virus

visitor/guest

Visual Studio

VMs. *See* virtual machines

VMWare

Volume Shadow Copy Service (VSS)

VPN. *See* virtual private network

VSS. *See* Volume Shadow Copy Service

vulnerabilities

Vulnerable Intelligence Feed (VIF)

**  W**

WAN. *See* wide area network

warm site

wbadmin command

Web browser

Web proxies

Web servers

WebServ01

WEP. *See* Wired Equivalent Privacy

wide area network (WAN)

Wi-Fi jacking

Wi-Fi Protected Access (WPA)

Windows 7

Windows 8

Windows 7 Security Compliance Management toolkit

Windows 8 Security Compliance Management toolkit

Windows Backup and Restore

Windows clients

Windows Defender

Windows Encrypting File System (EFS)

Windows Firewall with Advanced Security

Windows Group Policy

Windows Management Instrumentation (WMI) filters

Windows NT code base

Windows operating system

Windows Performance Monitor

Windows Registry backup

Windows run modes

Windows security auditing

Windows Server 2003

Windows Server 2008

Windows Server 2012

Windows Server 2012 editions and roles

Windows Server 2008 Group Policy Management Pack

Windows Server 2008 R2 core installation

Windows Server 2008 Server Recovery utility

Windows Server Backup utility

Windows servers

Windows service

Windows Services maintenance utility

Windows Services Properties

Windows Services Properties dialog

Windows Update Settings

Windows Update window

Windows workstation restore

Wired Equivalent Privacy (WEP)

wired network connections

wireless local area network (WLAN)

wireless network connections

wireless networking

wireless protocols

wireless security

WLAN. *See* wireless local area network

WMI. *See* Windows Management Instrumentation filters

WMI Query Language (WQL)

workgroup environments

workgroups

workstation backups

workstation computers

Workstation Domain

worms

WPA. *See* Wi-Fi Protected Access

WPA/WPA2 encryption

WQL. *See* WMI query language

**  Z**

zero-day attack

zombie