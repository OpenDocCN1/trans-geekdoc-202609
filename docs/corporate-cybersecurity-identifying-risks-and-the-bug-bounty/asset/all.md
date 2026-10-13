![](images/cover.jpg)

![](images/cover.jpg)

This edition first published 2022

© 2022 John Wiley & Sons, Ltd.

All rights reserved. No part of this publication may be reproduced, stored in a retrieval system, or transmitted, in any form or by any means, electronic, mechanical, photocopying, recording or otherwise, except as permitted by law. Advice on how to obtain permission to reuse material from this title is available at [http://www.wiley.com/go/permissions](http://www.wiley.com/go/permissions).

The right of John Jackson to be identified as the author of this work has been asserted in accordance with law.

*Registered Office(s)*

John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, USA

John Wiley & Sons Ltd, The Atrium, Southern Gate, Chichester, West Sussex, PO19 8SQ, UK

*Editorial Office*

The Atrium, Southern Gate, Chichester, West Sussex, PO19 8SQ, UK

For details of our global editorial offices, customer services, and more information about Wiley products visit us at [www.wiley.com](http://www.wiley.com).

Wiley also publishes its books in a variety of electronic formats and by print-on-demand. Some content that appears in standard print versions of this book may not be available in other formats.

*Limit of Liability/Disclaimer of Warranty*

While the publisher and authors have used their best efforts in preparing this work, they make no representations or warranties with respect to the accuracy or completeness of the contents of this work and specifically disclaim all warranties, including without limitation any implied warranties of merchantability or fitness for a particular purpose. No warranty may be created or extended by sales representatives, written sales materials or promotional statements for this work. The fact that an organization, website, or product is referred to in this work as a citation and/or potential source of further information does not mean that the publisher and authors endorse the information or services the organization, website, or product may provide or recommendations it may make. This work is sold with the understanding that the publisher is not engaged in rendering professional services. The advice and strategies contained herein may not be suitable for your situation. You should consult with a specialist where appropriate. Further, readers should be aware that websites listed in this work may have changed or disappeared between when this work was written and when it is read. Neither the publisher nor authors shall be liable for any loss of profit or any other commercial damages, including but not limited to special, incidental, consequential, or other damages.

*Library of Congress Cataloging-in-Publication Data*

Names: Jackson, John (Cybersecurity professional), author.  
Title: Corporate cybersecurity : identifying risks and the bug bounty program / John Jackson.  
Description: Hoboken, NJ : John Wiley & Sons, 2021. | Includes bibliographical references and index.  
Identifiers: LCCN 2021020794 (print) | LCCN 2021020795 (ebook) | ISBN 9781119782520 (hardback) | ISBN 9781119782568 (ebook) | ISBN 9781119782537 (pdf) | ISBN 9781119782544 (epub)  
Subjects: LCSH: Business enterprises--Computer networks--Security measures. | Penetration testing (Computer security) | Cyberspace--Security measures.  
Classification: LCC HD30.38 .J34 2021 (print) | LCC HD30.38 (ebook) | DDC 658.4/78--dc23  
LC record available at [https://lccn.loc.gov/2021020794](https://lccn.loc.gov/2021020794)  
LC ebook record available at [https://lccn.loc.gov/2021020795](https://lccn.loc.gov/2021020795)

Cover image: © WhataWin/Shutterstock

Cover design by Wiley

Set in 9.5/12pt STIX Two Text by Integra Software Services Pvt. Ltd, Pondicherry, India

# Contents

1.  [Cover](#cover.xhtml)
2.  [Title page](#f01.xhtml)
3.  [Copyright](#f02.xhtml)
4.  [Foreword](#f03.xhtml)
5.  [Acknowledgements](#f04.xhtml)
6.  [**Part 1 Bug Bounty Overview**](#p01.xhtml) 
    1.  [**1 The Evolution of Bug Bounty Programs**](#c01.xhtml) 
        1.  [1.1 Making History](#c01.xhtml#c1-sec-01001)
        2.  [1.2 Conservative Blockers](#c01.xhtml#c1-sec-01002)
        3.  [1.3 Increased Threat Actor Activity](#c01.xhtml#c1-sec-01003)
        4.  [1.4 Security Researcher Scams](#c01.xhtml#c1-sec-01004)
        5.  [1.5 Applications Are a Small Consideration](#c01.xhtml#c1-sec-01005)
        6.  [1.6 Enormous Budgetary Requirements](#c01.xhtml#c1-sec-01006)
        7.  [1.7 Other Security Tooling as a Priority](#c01.xhtml#c1-sec-0100)
        8.  [1.8 Vulnerability Disclosure Programs vs Bug Bounty Programs](#c01.xhtml#c1-sec-01008)
        9.  [1.8.1 Vulnerability Disclosure Programs](#c01.xhtml#c1-sec-02001)
        10.  [1.8.2 Bug Bounty Programs](#c01.xhtml#c1-sec-02002)
        11.  [1.9 Program Managers](#c01.xhtml#c1-sec-01009)
        12.  [1.10 The Law](#c01.xhtml#c1-sec-01010)
        13.  [1.11 Redefining Security Research](#c01.xhtml#c1-sec-01011)
        14.  [1.12 Taking Action](#c01.xhtml#c1-sec-01012)
        15.  [1.12.1 Get to Know Security Researchers](#c01.xhtml#c1-sec-02003)
        16.  [1.12.2 Fair and Just Resolution](#c01.xhtml#c1-sec-02004)
        17.  [1.12.3 Managing Disclosure](#c01.xhtml#c1-sec-02005)
        18.  [1.12.4 Corrections](#c01.xhtml#c1-sec-02006)
        19.  [1.12.5 Specific Community Involvement](#c01.xhtml#c1-sec-02007)
7.  [**Part 2 Evaluating Programs**](#p02.xhtml) 
    1.  [**2 Assessing Current Vulnerability Management Processes**](#c02.xhtml) 
        1.  [2.1 Who Runs a Bug Bounty Program?](#c02.xhtml#c2-sec-01001)
        2.  [2.2 Determining Security Posture](#c02.xhtml#c2-sec-01002)
        3.  [2.3 Management](#c02.xhtml#c2-sec-01003)
        4.  [2.3.1 Software Engineering Teams](#c02.xhtml#c2-sec-02001)
        5.  [2.3.2 Security Departments (Security Operations, Fraud Prevention, Governance/ Risk/Compliance, Edge Controls, Vulnerability Management, Endpoint Detection, and Response)](#c02.xhtml#c2-sec-02002)
        6.  [2.3.3 Infrastructure Teams](#c02.xhtml#c2-sec-02003)
        7.  [2.3.4 Legal Department](#c02.xhtml#c2-sec-02004)
        8.  [2.3.5 Communications Team](#c02.xhtml#c2-sec-02005)
        9.  [2.4 Important Questions](#c02.xhtml#c2-sec-01004)
        10.  [2.5 Software Engineering](#c02.xhtml#c2-sec-01005)
        11.  [2.5.1 Which Processes Are in Place for Secure Coding? Do the Software Engineers Understand the Importance of Mitigating the Risks Associated with Vulnerable Code?](#c02.xhtml#c2-sec-02006)
        12.  [2.5.2 How Effective Are Current Communication Processes? Will Vulnerabilities Be Quickly Resolved If Brought to Their Attention?](#c02.xhtml#c2-sec-02007)
        13.  [2.5.3 Is the Breadth of Our Enterprise’s Web and Mobile Applications Immense? Which Processes Are Engineers Using for Development in the Software Development Lifecycle?](#c02.xhtml#c2-sec-02008)
        14.  [2.6 Security Departments](#c02.xhtml#c2-sec-01006)
        15.  [2.6.1 How Does Security Operations Manage Incidents? Will Employee Assistance Be Provided from the Security Operations Team If a Threat Actor Manages to Exploit an Application Vulnerability? Which Tools Do They Have in Place?](#c02.xhtml#c2-sec-02009)
        16.  [2.6.2 What Does the Fraud Prevention Team Do to Prevent Malicious Activities? How Many Occurrences Do They See of Issues such as Account Takeover, and Could They Potentially Create Application Vulnerabilities?](#c02.xhtml#c2-sec-02010)
        17.  [2.6.3 Are There Any Compliance Practices in Place and, If So, How Do They Affect the Vulnerability Management Process? What Does the Application Security Team Have to Do to Assist in Enterprise Compliance?](#c02.xhtml#c2-sec-02011)
        18.  [2.6.4 What Edge Tooling Is in Place to Prevent Attacks? Are Any of the Enterprise Applications at Risk of Being Exploited due to an IoT (Internet of Things) Device?](#c02.xhtml#c2-sec-02012)
        19.  [2.6.5 How Often Does Our Vulnerability Management Team Push for Updates? How Does the Vulnerability Management Team Ensure Servers in which Enterprise Applications Reside Are Secure?](#c02.xhtml#c2-sec-02013)
        20.  [2.7 Infrastructure Teams](#c02.xhtml#c2-sec-01007)
        21.  [2.7.1 What Are Infrastructure Teams Doing to Ensure Best Security Practices Are Enabled? How Long Will It Take the Infrastructure Team to Resolve a Serious Issue When a Server-side Web Application Is Exploited, or During a Subdomain Takeover Vulnerability?](#c02.xhtml#c2-sec-02014)
        22.  [2.7.2 Is There Effective Communication between Infrastructure, Vulnerability Management, Security Operations, and Endpoint Detection and Response?](#c02.xhtml#c2-sec-02015)
        23.  [2.8 Legal Department](#c02.xhtml#c2-sec-01008)
        24.  [2.8.1 How Well Refined is the Relationship between the Application Security Team and the Legal Department?](#c02.xhtml#c2-sec-02016)
        25.  [2.8.2 What Criteria Are/Will Be Set Out for the Escalation of Issues?](#c02.xhtml#c2-sec-02017)
        26.  [2.8.3 Does the Legal Department Understand the Necessity of Bug Bounty Program Management?](#c02.xhtml#c2-sec-02018)
        27.  [2.9 Communications Team](#c02.xhtml#c2-sec-01009)
        28.  [2.9.1 Has the Communications Team Dealt with Security Researchers Before? Is the Importance Understood?](#c02.xhtml#c2-sec-02019)
        29.  [2.9.2 Was the Communications Team Informed of Bug Bounty Program Expectations?](#c02.xhtml#c2-sec-02020)
        30.  [2.10 Engineers](#c02.xhtml#c2-sec-01010)
        31.  [2.11 Program Readiness](#c02.xhtml#c2-sec-01011)
    2.  [**3 Evaluating Program Operations**](#c03.xhtml) 
        1.  [3.1 One Size Does Not Fit All](#c03.xhtml#c3-sec-01001)
        2.  [3.2 Realistic Program Scenarios](#c03.xhtml#c3-sec-01002)
        3.  [3.3 Ad Hoc Program](#c03.xhtml#c3-sec-01003)
        4.  [3.4 Note](#c03.xhtml#c3-sec-01004)
        5.  [3.5 Applied Knowledge](#c03.xhtml#c3-sec-01005)
        6.  [3.5.1 Applied Knowledge #1](#c03.xhtml#c3-sec-02001)
        7.  [3.5.1.1 Private Programs](#c03.xhtml#c3-sec-03001)
        8.  [3.5.2 Applied Knowledge #2](#c03.xhtml#c3-sec-02002)
        9.  [3.5.2.1 Public Programs](#c03.xhtml#c3-sec-03002)
        10.  [3.5.3 Applied Knowledge #3](#c03.xhtml#c3-sec-02003)
        11.  [3.5.3.1 Hybrid Models](#c03.xhtml#c3-sec-03003)
        12.  [3.6 Crowdsourced Platforms](#c03.xhtml#c3-sec-01006)
        13.  [3.7 Platform Pricing and Services](#c03.xhtml#c3-sec-01007)
        14.  [3.8 Managed Services](#c03.xhtml#c3-sec-01008)
        15.  [3.9 Opting Out of Managed Services](#c03.xhtml#c3-sec-01009)
        16.  [3.10 On-demand Penetration Tests](#c03.xhtml#c3-sec-01010)
8.  [**Part 3 Program Setup**](#p03.xhtml) 
    1.  [**4 Defining Program Scope and Bounties**](#c04.xhtml) 
        1.  [4.1 What Is a Bounty?](#c04.xhtml#c4-sec-01001)
        2.  [4.2 Understanding Scope](#c04.xhtml#c4-sec-01002)
        3.  [4.3 How to Create Scope](#c04.xhtml#c4-sec-01003)
        4.  [4.3.1 Models](#c04.xhtml#c4-sec-02001)
        5.  [4.4 Understanding Wildcards](#c04.xhtml#c4-sec-01004)
        6.  [4.4.1 Subdomain](#c04.xhtml#c4-sec-02002)
        7.  [4.4.2 Domain](#c04.xhtml#c4-sec-02003)
        8.  [4.4.3 Specific Domain Path or Specific Subdomain Path](#c04.xhtml#c4-sec-02004)
        9.  [4.5 Determining Asset Allocation](#c04.xhtml#c4-sec-01005)
        10.  [4.6 Asset Risk](#c04.xhtml#c4-sec-01006)
        11.  [4.7 Understanding Out of Scope](#c04.xhtml#c4-sec-01007)
        12.  [4.8 Vulnerability Types](#c04.xhtml#c4-sec-01008)
        13.  [4.8.1 Denial of Service (DOS) or Distributed Denial of Service (DDoS) Attacks](#c04.xhtml#c4-sec-02005)
        14.  [4.8.2 Social Engineering Attacks](#c04.xhtml#c4-sec-02006)
        15.  [4.8.3 Brute Force or Rate Limiting](#c04.xhtml#c4-sec-02007)
        16.  [4.8.4 Account and Email Enumeration](#c04.xhtml#c4-sec-02008)
        17.  [4.8.5 Self-XSS](#c04.xhtml#c4-sec-02009)
        18.  [4.8.6 Clickjacking](#c04.xhtml#c4-sec-02010)
        19.  [4.8.7 Miscellaneous](#c04.xhtml#c4-sec-02011)
        20.  [4.9 When Is an Asset Really Out of Scope?](#c04.xhtml#c4-sec-01009)
        21.  [4.10 The House Wins – Or Does It?](#c04.xhtml#c4-sec-01010)
        22.  [4.11 Fair Judgment on Bounties](#c04.xhtml#c4-sec-01011)
        23.  [4.12 Post-mortem](#c04.xhtml#c4-sec-01012)
        24.  [4.13 Awareness and Reputational Damage](#c04.xhtml#c4-sec-01013)
        25.  [4.14 Putting It All Together](#c04.xhtml#c4-sec-01014)
        26.  [4.15 Bug Bounty Payments](#c04.xhtml#c4-sec-01015)
        27.  [4.15.1 Determining Payments](#c04.xhtml#c4-sec-02012)
        28.  [4.15.2 Bonus Payments](#c04.xhtml#c4-sec-02013)
        29.  [4.15.3 Nonmonetary Rewards](#c04.xhtml#c4-sec-02014)
    2.  [**5 Understanding Safe Harbor and Service Level Agreements**](#c05.xhtml) 
        1.  [5.1 What Is “Safe Harbor”?](#c05.xhtml#c5-sec-01001)
        2.  [5.1.1 The Reality of Safe Harbor](#c05.xhtml#c5-sec-02001)
        3.  [5.1.2 Fear and Reluctance](#c05.xhtml#c5-sec-02002)
        4.  [5.1.3 Writing Safe Harbor Agreements](#c05.xhtml#c5-sec-02003)
        5.  [5.1.4 Example Safe Harbor Agreement](#c05.xhtml#c5-sec-02004)
        6.  [5.2 Retaliation against a Rogue Researcher (Cybercriminal or Threat/Bad Actor)](#c05.xhtml#c5-sec-01002)
        7.  [5.3 Service Level Agreements (SLAs)](#c05.xhtml#c5-sec-01003)
        8.  [5.3.1 Resolution Times](#c05.xhtml#c5-sec-02005)
        9.  [5.3.2 Triage Times](#c05.xhtml#c5-sec-02006)
    3.  [**6 Program Configuration**](#c06.xhtml) 
        1.  [6.1 Understanding Options](#c06.xhtml#c6-sec-01001)
        2.  [6.2 Bugcrowd](#c06.xhtml#c6-sec-01002)
        3.  [6.2.1 Creating the Program](#c06.xhtml#c6-sec-02001)
        4.  [6.2.2 Program Overview](#c06.xhtml#c6-sec-02002)
        5.  [6.2.2.1 The Program Dashboard](#c06.xhtml#c6-sec-03001)
        6.  [6.2.2.2 The Crowd Control Navbar](#c06.xhtml#c6-sec-03002)
        7.  [Summary](#c06.xhtml#c6-sec-04001)
        8.  [Submissions](#c06.xhtml#c6-sec-04002)
        9.  [Researchers](#c06.xhtml#c6-sec-04003)
        10.  [Rewards](#c06.xhtml#c6-sec-04004)
        11.  [Insights Dashboard](#c06.xhtml#c6-sec-04005)
        12.  [Reports](#c06.xhtml#c6-sec-04006)
        13.  [6.2.3 Advanced Program Configuration and Modification](#c06.xhtml#c6-sec-02003)
        14.  [6.2.3.1 Program Brief](#c06.xhtml#c6-sec-03003)
        15.  [6.2.3.2 Scope and Rewards](#c06.xhtml#c6-sec-03004)
        16.  [6.2.3.3 Integrations](#c06.xhtml#c6-sec-03005)
        17.  [6.2.3.4 Announcements](#c06.xhtml#c6-sec-03006)
        18.  [6.2.3.5 Manage Team](#c06.xhtml#c6-sec-03007)
        19.  [6.2.3.6 Submissions](#c06.xhtml#c6-sec-03008)
        20.  [6.2.4 Profile Settings](#c06.xhtml#c6-sec-02004)
        21.  [6.2.4.1 The Profile and Account](#c06.xhtml#c6-sec-03009)
        22.  [6.2.4.2 Security](#c06.xhtml#c6-sec-03010)
        23.  [6.2.4.3 Notification Settings](#c06.xhtml#c6-sec-03011)
        24.  [6.2.4.4 API Credentials](#c06.xhtml#c6-sec-03012)
        25.  [6.2.5 Enterprise “Profile” Settings](#c06.xhtml#c6-sec-02005)
        26.  [6.2.5.1 Management and Configuration](#c06.xhtml#c6-sec-03013)
        27.  [6.2.5.2 Organization Details](#c06.xhtml#c6-sec-03014)
        28.  [6.2.5.3 Team Members](#c06.xhtml#c6-sec-03015)
        29.  [6.2.5.4 Targets](#c06.xhtml#c6-sec-03016)
        30.  [6.2.5.5 Authentication](#c06.xhtml#c6-sec-03017)
        31.  [6.2.5.6 Domains](#c06.xhtml#c6-sec-03018)
        32.  [6.2.5.7 Accounting](#c06.xhtml#c6-sec-03019)
        33.  [6.3 HackerOne](#c06.xhtml#c6-sec-01003)
        34.  [6.3.1 Program Settings](#c06.xhtml#c6-sec-02006)
        35.  [6.3.1.1 General](#c06.xhtml#c6-sec-03020)
        36.  [6.3.1.2 Information](#c06.xhtml#c6-sec-03021)
        37.  [6.3.1.3 Product Edition](#c06.xhtml#c6-sec-03022)
        38.  [6.3.1.4 Authentication](#c06.xhtml#c6-sec-03023)
        39.  [6.3.1.5 Verified Domains](#c06.xhtml#c6-sec-03024)
        40.  [6.3.1.6 Credential Management](#c06.xhtml#c6-sec-03025)
        41.  [6.3.1.7 Group Management](#c06.xhtml#c6-sec-03026)
        42.  [6.3.1.8 User Management](#c06.xhtml#c6-sec-03027)
        43.  [6.3.1.9 Audit Log](#c06.xhtml#c6-sec-03028)
        44.  [6.3.2 Billing](#c06.xhtml#c6-sec-02007)
        45.  [6.3.2.1 Overview](#c06.xhtml#c6-sec-03029)
        46.  [6.3.2.2 Credit Card](#c06.xhtml#c6-sec-03030)
        47.  [6.3.2.3 Prepayment](#c06.xhtml#c6-sec-03031)
        48.  [6.3.3 Program](#c06.xhtml#c6-sec-02008)
        49.  [6.3.3.1 Policy](#c06.xhtml#c6-sec-03032)
        50.  [6.3.3.2 Scope](#c06.xhtml#c6-sec-03033)
        51.  [6.3.3.3 Submit Report Form](#c06.xhtml#c6-sec-03034)
        52.  [6.3.3.4 Response Targets](#c06.xhtml#c6-sec-03035)
        53.  [6.3.3.5 Metrics Display](#c06.xhtml#c6-sec-03036)
        54.  [6.3.3.6 Email Notifications](#c06.xhtml#c6-sec-03037)
        55.  [6.3.3.7 Inbox Views](#c06.xhtml#c6-sec-03038)
        56.  [6.3.3.8 Disclosure](#c06.xhtml#c6-sec-03039)
        57.  [6.3.3.9 Custom Fields](#c06.xhtml#c6-sec-03040)
        58.  [6.3.3.10 Invitations](#c06.xhtml#c6-sec-03041)
        59.  [6.3.3.11 Submission](#c06.xhtml#c6-sec-03042)
        60.  [6.3.3.12 Message Hackers](#c06.xhtml#c6-sec-03043)
        61.  [6.3.3.13 Email Forwarding](#c06.xhtml#c6-sec-03044)
        62.  [6.3.3.14 Embedded Submission Form](#c06.xhtml#c6-sec-03045)
        63.  [6.3.3.15 Bounties](#c06.xhtml#c6-sec-03046)
        64.  [6.3.3.16 Swag](#c06.xhtml#c6-sec-03047)
        65.  [6.3.3.17 Common Responses](#c06.xhtml#c6-sec-03048)
        66.  [6.3.3.18 Triggers](#c06.xhtml#c6-sec-03049)
        67.  [6.3.3.19 Integrations](#c06.xhtml#c6-sec-03050)
        68.  [6.3.3.20 API](#c06.xhtml#c6-sec-03051)
        69.  [6.3.3.21 Hackbot](#c06.xhtml#c6-sec-03052)
        70.  [6.3.3.22 Export Reports](#c06.xhtml#c6-sec-03053)
        71.  [6.3.3.23 Profile Settings](#c06.xhtml#c6-sec-03054)
        72.  [6.3.4 Inbox](#c06.xhtml#c6-sec-02009)
        73.  [6.3.4.1 Report Details](#c06.xhtml#c6-sec-03055)
        74.  [6.3.4.2 Timeline](#c06.xhtml#c6-sec-03056)
        75.  [6.4 Summary](#c06.xhtml#c6-sec-01004)
9.  [**Part 4 Vulnerability Reports and Disclosure**](#p04.xhtml) 
    1.  [**7 Triage and Bug Management**](#c07.xhtml) 
        1.  [7.1 Understanding Triage](#c07.xhtml#c7-sec-01001)
        2.  [7.1.1 Validation](#c07.xhtml#c7-sec-02001)
        3.  [7.1.2 Lessons Learned](#c07.xhtml#c7-sec-02002)
        4.  [7.1.3 Vulnerability Mishaps](#c07.xhtml#c7-sec-02003)
        5.  [7.1.4 Managed Services](#c07.xhtml#c7-sec-02004)
        6.  [7.1.5 Self-service](#c07.xhtml#c7-sec-02005)
        7.  [7.2 Bug Management](#c07.xhtml#c7-sec-01002)
        8.  [7.2.1 Vulnerability Priority](#c07.xhtml#c7-sec-02006)
        9.  [7.2.2 Vulnerability Examples](#c07.xhtml#c7-sec-02007)
        10.  [7.2.2.1 Reflected XSS on a login portal](#c07.xhtml#c7-sec-02007a)
        11.  [Report and Triage](#c07.xhtml#c7-sec-04001)
        12.  [Validation](#c07.xhtml#c7-sec-04002)
        13.  [7.2.2.2 Open redirect vulnerability](#c07.xhtml#c7-sec-04002a)
        14.  [Report and Triage](#c07.xhtml#c7-sec-04003)
        15.  [Validation](#c07.xhtml#c7-sec-04004)
        16.  [7.2.2.3 Leaked internal Structured Query Language (SQL) server credentials](#c07.xhtml#c7-sec-04002aa)
        17.  [Report and Triage](#c07.xhtml#c7-sec-04005)
        18.  [Validation](#c07.xhtml#c7-sec-04006)
        19.  [7.3 Answers](#c07.xhtml#c7-sec-01003)
        20.  [7.3.1 Vulnerability Rating-test Summary](#c07.xhtml#c7-sec-02008)
        21.  [7.3.1.1 Reflected XSS in a login portal](#c07.xhtml#c7-sec-01003a)
        22.  [7.3.1.2 Open redirect vulnerability](#c07.xhtml#c7-sec-01003b)
        23.  [7.3.1.3 Leaked internal SQL server credentials](#c07.xhtml#c7-sec-01003c)
        24.  [7.3.2 Complexity vs Rating](#c07.xhtml#c7-sec-02009)
        25.  [7.3.3 Projected Ratings](#c07.xhtml#c7-sec-02010)
        26.  [7.3.4 Ticketing and Internal SLA](#c07.xhtml#c7-sec-02011)
        27.  [7.3.4.1 Creating Tickets](#c07.xhtml#c7-sec-03001)
    2.  [**8 Vulnerability Disclosure Information**](#c08.xhtml) 
        1.  [8.1 Understanding Public Disclosure](#c08.xhtml#c8-sec-01001)
        2.  [8.1.1 Making the Decision](#c08.xhtml#c8-sec-02001)
        3.  [8.1.1.1 Private Programs](#c08.xhtml#c8-sec-03001)
        4.  [The Bottom Line](#c08.xhtml#c8-sec-04001)
        5.  [8.1.1.2 Public Programs](#c08.xhtml#c8-sec-03002)
        6.  [The Bottom Line](#c08.xhtml#c8-sec-04002)
        7.  [8.2 CVE Responsibility](#c08.xhtml#c8-sec-01002)
        8.  [8.2.1 What are CVEs?](#c08.xhtml#c8-sec-02002)
        9.  [8.2.2 Program Manager Responsibilities](#c08.xhtml#c8-sec-02003)
        10.  [8.2.3 Hardware CVEs](#c08.xhtml#c8-sec-02004)
        11.  [8.2.4 Software and Product CVEs](#c08.xhtml#c8-sec-02005)
        12.  [8.2.5 Third-party CVEs](#c08.xhtml#c8-sec-02006)
        13.  [8.3 Submission Options](#c08.xhtml#c8-sec-01003)
        14.  [8.3.1 In-house Submissions](#c08.xhtml#c8-sec-02007)
        15.  [8.3.2 Program Managed Submissions and Hands-off Submissions](#c08.xhtml#c8-sec-02008)
        16.  [8.3.2.1 Program Managed Submissions](#c08.xhtml#c8-sec-03003)
        17.  [8.3.2.2 Hands-off Submissions](#c08.xhtml#c8-sec-03004)
10.  [**Part 5 Internal and External Communication**](#p05.xhtml) 
     1.  [**9 Development and Application Security Collaboration**](#c09.xhtml) 
         1.  [9.1 Key Role Differences](#c09.xhtml#c9-sec-01001)
         2.  [9.1.1 Application Security Engineer](#c09.xhtml#c9-sec-02001)
         3.  [9.1.2 Development](#c09.xhtml#c9-sec-02002)
         4.  [9.2 Facing a Ticking Clock](#c09.xhtml#c9-sec-01002)
         5.  [9.3 Meaningful Vulnerability Reporting](#c09.xhtml#c9-sec-01003)
         6.  [9.4 Communicating Expectations](#c09.xhtml#c9-sec-01004)
         7.  [9.5 Pushback, Escalations, and Exceptions](#c09.xhtml#c9-sec-01005)
         8.  [9.5.1 Internal steps](#c09.xhtml#c9-sec-02003)
         9.  [9.5.2 External steps](#c09.xhtml#c9-sec-02004)
         10.  [9.5.2 Escalations](#c09.xhtml#c9-sec-02005)
         11.  [9.5.3 Summary](#c09.xhtml#c9-sec-02006)
         12.  [9.6 Continuous Accountability](#c09.xhtml#c9-sec-01006)
         13.  [9.6.1 Tracking](#c09.xhtml#c9-sec-02007)
         14.  [9.6.2 Missed Deadlines](#c09.xhtml#c9-sec-02008)
     2.  [**10 Hacker and Program Interaction Essentials**](#c10.xhtml) 
         1.  [10.1 Understanding the Hacker](#c10.xhtml#c10-sec-01001)
         2.  [10.1.1 Money, Ethics, or Both?](#c10.xhtml#c10-sec-02001)
         3.  [10.1.2 Case Study Analysis](#c10.xhtml#c10-sec-02002)
         4.  [10.2 Invalidating False Positives](#c10.xhtml#c10-sec-01002)
         5.  [10.2.1 Intake Process and Breaking the News](#c10.xhtml#c10-sec-02003)
         6.  [10.2.2 Dealing with a Toxic Hacker](#c10.xhtml#c10-sec-02004)
         7.  [10.3 Managed Program Considerations](#c10.xhtml#c10-sec-01003)
         8.  [10.4 In-house Programs](#c10.xhtml#c10-sec-01004)
         9.  [10.5 Blackmail or Possible Threat Actor](#c10.xhtml#c10-sec-01005)
         10.  [10.6 Public Threats or Disclosure](#c10.xhtml#c10-sec-01006)
         11.  [10.7 Program Warning Messages](#c10.xhtml#c10-sec-01007)
         12.  [10.8 Threat Actor or Security Researcher?](#c10.xhtml#c10-sec-01008)
         13.  [10.9 Messaging Researchers](#c10.xhtml#c10-sec-01009)
         14.  [10.9.1 Security Researcher Interviews](#c10.xhtml#c10-sec-02005)
         15.  [10.9.2 Bug Bounty Program Manager Interviews](#c10.xhtml#c10-sec-02006)
         16.  [10.10 Summary](#c10.xhtml#c10-sec-01010)
11.  [**Part 6 Assessments and Expansions**](#p06.xhtml) 
     1.  [**11 Internal Assessments**](#c11.xhtml) 
         1.  [11.1 Introduction to Internal Assessments](#c11.xhtml#c11-sec-01001)
         2.  [11.2 Proactive Vs Reactive Testing](#c11.xhtml#c11-sec-01002)
         3.  [11.3 Passive Assessments](#c11.xhtml#c11-sec-01003)
         4.  [11.3.1 Shodan](#c11.xhtml#c11-sec-02001)
         5.  [11.3.1.1 Using Shodan](#c11.xhtml#c11-sec-03001)
         6.  [11.3.2 Amass/crt.sh](#c11.xhtml#c11-sec-02002)
         7.  [11.3.2.1 Amass](#c11.xhtml#c11-sec-03002)
         8.  [11.3.2.2 crt.sh](#c11.xhtml#c11-sec-03003)
         9.  [11.4 Active Assessments](#c11.xhtml#c11-sec-01004)
         10.  [11.4.1 nmapAutomator.sh](#c11.xhtml#c11-sec-02003)
         11.  [11.4.2 Sn1per](#c11.xhtml#c11-sec-02004)
         12.  [11.4.3 Owasp Zap](#c11.xhtml#c11-sec-02005)
         13.  [11.4.4 Dalfox](#c11.xhtml#c11-sec-02006)
         14.  [11.4.5 Dirsearch](#c11.xhtml#c11-sec-02007)
         15.  [11.5 Passive/Active Summary](#c11.xhtml#c11-sec-01005)
         16.  [11.6 Additional Considerations: Professional Testing and Third-Party Risk](#c11.xhtml#c11-sec-01006)
     2.  [**12 Expanding Scope**](#c12.xhtml) 
         1.  [12.1 Communicating with the Team](#c12.xhtml#c12-sec-01002)
         2.  [12.2 Costs of Expansion](#c12.xhtml#c12-sec-01003)
         3.  [12.3 When to Expand Scope](#c12.xhtml#c12-sec-01004)
         4.  [12.4 Alternatives to Scope Expansion](#c12.xhtml#c12-sec-01005)
         5.  [12.5 Managing Expansion](#c12.xhtml#c12-sec-01006)
     3.  [**13 Public Release**](#c13.xhtml) 
         1.  [13.1 Understanding the Public Program](#c13.xhtml#c13-sec-01001)
         2.  [13.2 The “Right” Time](#c13.xhtml#c13-sec-01002)
         3.  [13.3 Recommended Release](#c13.xhtml#c13-sec-01003)
         4.  [13.3.1 Requirements](#c13.xhtml#c13-sec-02001)
         5.  [13.4 Rolling Backwards](#c13.xhtml#c13-sec-01004)
         6.  [13.5 Summary](#c13.xhtml#c13-sec-01005)
12.  [**Index**](#b01.xhtml)
13.  [End User License Agreement](#eula.xhtml)

## List of Illustrations

1.  Chapter 6 
    1.  [Figure 6.1 Bugcrowd “Start now” button.](#c06.xhtml#c6-fig-0001)
    2.  [Figure 6.2 Bugcrowd: selection “Bug Bounty Program”.](#c06.xhtml#c6-fig-0002)
    3.  [Figure 6.3 Selecting the program name on Bugcrowd.](#c06.xhtml#c6-fig-0003)
    4.  [Figure 6.4 Adding targets to test on Bugcrowd.](#c06.xhtml#c6-fig-0004)
    5.  [Figure 6.5 Adding a target to Bugcrowd.](#c06.xhtml#c6-fig-0005)
    6.  [Figure 6.6 Adding reward ranges by severity on Bugcrowd.](#c06.xhtml#c6-fig-0006)
    7.  [Figure 6.7 Identify goals and concerns on Bugcrowd.](#c06.xhtml#c6-fig-0007)
    8.  [Figure 6.8 Select researcher activities, environments,...](#c06.xhtml#c6-fig-0008)
    9.  [Figure 6.9 Upload your company’s logo and create a...](#c06.xhtml#c6-fig-0009)
    10.  [Figure 6.10 Vulnerability tasking tabs.](#c06.xhtml#c6-fig-0010)
    11.  [Figure 6.11 Bugcrowd documentation.](#c06.xhtml#c6-fig-0011)
    12.  [Figure 6.12 Program dropdown menu.](#c06.xhtml#c6-fig-0012)
    13.  [Figure 6.13 Crowd control navbar.](#c06.xhtml#c6-fig-0013)
    14.  [Figure 6.14 Vulnerability submissions panel.](#c06.xhtml#c6-fig-0014)
    15.  [Figure 6.15 Program participants tab.](#c06.xhtml#c6-fig-0015)
    16.  [Figure 6.16 Program invitations tab.](#c06.xhtml#c6-fig-0016)
    17.  [Figure 6.17 Program rewards dashboard.](#c06.xhtml#c6-fig-0017)
    18.  [Figure 6.18 Insights dashboard: technical severity chart.](#c06.xhtml#c6-fig-0018)
    19.  [Figure 6.19 Insights dashboard: target breakdown.](#c06.xhtml#c6-fig-0019)
    20.  [Figure 6.20 Insights dashboard: performance.](#c06.xhtml#c6-fig-0020)
    21.  [Figure 6.21 Program brief settings.](#c06.xhtml#c6-fig-0021)
    22.  [Figure 6.22 Scope details.0](#c06.xhtml#c6-fig-0022)
    23.  [Figure 6.23 Profile dropdown menu.](#c06.xhtml#c6-fig-0023)
    24.  [Figure 6.24 Targets tab.](#c06.xhtml#c6-fig-0024)
    25.  [Figure 6.25 Program dropdown menu.](#c06.xhtml#c6-fig-0025)
    26.  [Figure 6.26 Add group” button.](#c06.xhtml#c6-fig-0026)
    27.  [Figure 6.27 Description of an asset group.](#c06.xhtml#c6-fig-0027)
    28.  [Figure 6.28 Target groups.](#c06.xhtml#c6-fig-0028)
    29.  [Figure 6.29 Target group rewards.](#c06.xhtml#c6-fig-0029)
    30.  [Figure 6.30 Target group listings.](#c06.xhtml#c6-fig-0030)
    31.  [Figure 6.31 Integrating various tools to help with report management.](#c06.xhtml#c6-fig-0031)
    32.  [Figure 6.32 Announcements option.](#c06.xhtml#c6-fig-0032)
    33.  [Figure 6.33 New announcement option.](#c06.xhtml#c6-fig-0033)
    34.  [Figure 6.34 Manage team option.](#c06.xhtml#c6-fig-0034)
    35.  [Figure 6.35 Invite a team member option.](#c06.xhtml#c6-fig-0035)
    36.  [Figure 6.36 Data fields option.](#c06.xhtml#c6-fig-0036)
    37.  [Figure 6.37 CVSS v3 option.](#c06.xhtml#c6-fig-0037)
    38.  [Figure 6.38 Remediation advice option.](#c06.xhtml#c6-fig-0038)
    39.  [Figure 6.39 Retesting option.](#c06.xhtml#c6-fig-0039)
    40.  [Figure 6.40 Markdown embedded attachments option.](#c06.xhtml#c6-fig-0040)
    41.  [Figure 6.41 Profile and enterprise sidebar.](#c06.xhtml#c6-fig-0041)
    42.  [Figure 6.42 Profile option.](#c06.xhtml#c6-fig-0042)
    43.  [Figure 6.43 Security option.](#c06.xhtml#c6-fig-0043)
    44.  [Figure 6.44 Events option.](#c06.xhtml#c6-fig-0044)
    45.  [Figure 6.45 Two-factor authentication option.](#c06.xhtml#c6-fig-0045)
    46.  [Figure 6.46 Notifications settings option.](#c06.xhtml#c6-fig-0046)
    47.  [Figure 6.47 API credentials option.](#c06.xhtml#c6-fig-0047)
    48.  [Figure 6.48 Single sign-on option.](#c06.xhtml#c6-fig-0048)
    49.  [Figure 6.49 Unverified domains option.](#c06.xhtml#c6-fig-0049)
    50.  [Figure 6.50 Activity summary.](#c06.xhtml#c6-fig-0050)
    51.  [Figure 6.51 Submit deposit request option.](#c06.xhtml#c6-fig-0051)
    52.  [Figure 6.52 Transfer funds option.](#c06.xhtml#c6-fig-0052)
    53.  [Figure 6.53 Program balances option.](#c06.xhtml#c6-fig-0053)
    54.  [Figure 6.54 Program settings option.](#c06.xhtml#c6-fig-0054)
    55.  [Figure 6.55 Miscellaneous program options.](#c06.xhtml#c6-fig-0055)
    56.  [Figure 6.56 Security page function.](#c06.xhtml#c6-fig-0056)
    57.  [Figure 6.57 HackerOne product editions.](#c06.xhtml#c6-fig-0057)
    58.  [Figure 6.58 Single sign-on with SAML.](#c06.xhtml#c6-fig-0058)
    59.  [Figure 6.59 Domain verification example.](#c06.xhtml#c6-fig-0059)
    60.  [Figure 6.60 Credential management tab.](#c06.xhtml#c6-fig-0060)
    61.  [Figure 6.61 Group management options.](#c06.xhtml#c6-fig-0061)
    62.  [Figure 6.62 Group management options.](#c06.xhtml#c6-fig-0062)
    63.  [Figure 6.63 Adding users option.](#c06.xhtml#c6-fig-0063)
    64.  [Figure 6.64 Audit log option.](#c06.xhtml#c6-fig-0064)
    65.  [Figure 6.65 Overview of bounties and fees.](#c06.xhtml#c6-fig-0065)
    66.  [Figure 6.66 Adding assets.](#c06.xhtml#c6-fig-0066)
    67.  [Figure 6.67 The CIA triad.](#c06.xhtml#c6-fig-0067)
    68.  [Figure 6.68 Submit report form option.](#c06.xhtml#c6-fig-0068)
    69.  [Figure 6.69 Customizing the report form.](#c06.xhtml#c6-fig-0069)
    70.  [Figure 6.70 Response targets option.](#c06.xhtml#c6-fig-0070)
    71.  [Figure 6.71 Metrics display option.](#c06.xhtml#c6-fig-0071)
    72.  [Figure 6.72 Setting email notifications.](#c06.xhtml#c6-fig-0072)
    73.  [Figure 6.73 Inbox views option.](#c06.xhtml#c6-fig-0073)
    74.  [Figure 6.74 Disclosure option.](#c06.xhtml#c6-fig-0074)
    75.  [Figure 6.75 Invitations option.](#c06.xhtml#c6-fig-0075)
    76.  [Figure 6.76 Public launch option.](#c06.xhtml#c6-fig-0076)
    77.  [Figure 6.77 Submission requirements option.](#c06.xhtml#c6-fig-0077)
    78.  [Figure 6.78 Messaging hackers option.](#c06.xhtml#c6-fig-0078)
    79.  [Figure 6.79 Email forwarding function.](#c06.xhtml#c6-fig-0079)
    80.  [Figure 6.80 Embedded submission configuration.](#c06.xhtml#c6-fig-0080)
    81.  [Figure 6.81 Bounties option.](#c06.xhtml#c6-fig-0081)
    82.  [Figure 6.82 Common reponses option.](#c06.xhtml#c6-fig-0082)
    83.  [Figure 6.83 Add common response option.](#c06.xhtml#c6-fig-0083)
    84.  [Figure 6.84 Edit common response option.](#c06.xhtml#c6-fig-0084)
    85.  [Figure 6.85 Default common responses option.](#c06.xhtml#c6-fig-0085)
    86.  [Figure 6.86 Create triggers option.](#c06.xhtml#c6-fig-0086)
    87.  [Figure 6.87 Hackbot settings option.](#c06.xhtml#c6-fig-0087)
    88.  [Figure 6.88 Export reports option.](#c06.xhtml#c6-fig-0088)
    89.  [Figure 6.89 Reporting inbox vulnerabilities.](#c06.xhtml#c6-fig-0089)
    90.  [Figure 6.90 Example report.](#c06.xhtml#c6-fig-0090)
    91.  [Figure 6.91 Timeline option.](#c06.xhtml#c6-fig-0091)
2.  Chapter 11 
    1.  [Figure 11.1 Shodan Browser Search.](#c11.xhtml#c11-fig-0001)
    2.  [Figure 11.2 Shodan Search Bar.](#c11.xhtml#c11-fig-0002)
    3.  [Figure 11.3 Generating Results.](#c11.xhtml#c11-fig-0003)
    4.  [Figure 11.4 Shodan Asset Analysis.](#c11.xhtml#c11-fig-0004)
    5.  [Figure 11.5 Shodan Services Analysis.](#c11.xhtml#c11-fig-0005)
    6.  [Figure 11.6 Google Search Results.](#c11.xhtml#c11-fig-0006)
    7.  [Figure 11.7 Amass Scanning for Subdomains.](#c11.xhtml#c11-fig-0007)
    8.  [Figure 11.8 Subdomains in Nano.](#c11.xhtml#c11-fig-0008)
    9.  [Figure 11.9 Subdomain Enumeration with crt.sh.](#c11.xhtml#c11-fig-0009)
    10.  [Figure 11.10 nmapAutomator Scanning Information.](#c11.xhtml#c11-fig-0010)
    11.  [Figure 11.11 nmapAutomator Performing Full Scan of Asset.](#c11.xhtml#c11-fig-0011)
    12.  [Figure 11.12 nmapAutomator Results.](#c11.xhtml#c11-fig-0012)
    13.  [Figure 11.13 Sn1per Running Metasploit Modules.](#c11.xhtml#c11-fig-0013)
    14.  [Figure 11.14 Sn1per Running Nmap Scripts.](#c11.xhtml#c11-fig-0014)
    15.  [Figure 11.15 Setting up an Automated Scan in OWASP ZAP.](#c11.xhtml#c11-fig-0015)
    16.  [Figure 11.16 OWASP ZAP Scan Results.](#c11.xhtml#c11-fig-0016)
    17.  [Figure 11.17 OWASP ZAP Potential Vulnerability Result.](#c11.xhtml#c11-fig-0017)
    18.  [Figure 11.18 XSS Attack Performed.](#c11.xhtml#c11-fig-0018)
    19.  [Figure 11.19 Dalfox Available Command.](#c11.xhtml#c11-fig-0019)
    20.  [Figure 11.20 Dalfox Identifying an XSS Instance.](#c11.xhtml#c11-fig-0020)
    21.  [Figure 11.21 XSS Attack.](#c11.xhtml#c11-fig-0021)
    22.  [Figure 11.22 Dirsearch Finding Folders.](#c11.xhtml#c11-fig-0022)

## Guide

1.  [Cover](#cover.xhtml)
2.  [Title page](#f01.xhtml)
3.  [Copyright](#f02.xhtml)
4.  
5.  [Foreword](#f03.xhtml)
6.  [Acknowledgments](#f04.xhtml)
7.  [Begin Reading](#c01.xhtml)
8.  [Index](#b01.xhtml)
9.  [End User License Agreement](#eula.xhtml)

## Pages

1.  [i](#f01.xhtml#page_i)
2.  [ii](#f01.xhtml#page_ii)
3.  [iii](#f01.xhtml#page_iii)
4.  [iv](#f02.xhtml#page_iv)
5.  [v](#navigation.xhtml#page_v)
6.  [vi](#navigation.xhtml#page_vi)
7.  [vii](#navigation.xhtml#page_vii)
8.  [viii](#navigation.xhtml#page_viii)
9.  [ix](#navigation.xhtml#page_ix)
10.  [x](#navigation.xhtml#page_x)
11.  [xi](#navigation.xhtml#page_xi)
12.  [xii](#navigation.xhtml#page_xii)
13.  [xiii](#f03.xhtml#page_xiii)
14.  [xiv](#f03.xhtml#page_xiv)
15.  [xv](#f04.xhtml#page_xv)
16.  [1](#p01.xhtml#page_1)
17.  [2](#p01.xhtml#page_2)
18.  [3](#c01.xhtml#page_3)
19.  [4](#c01.xhtml#page_4)
20.  [5](#c01.xhtml#page_5)
21.  [6](#c01.xhtml#page_6)
22.  [7](#c01.xhtml#page_7)
23.  [8](#c01.xhtml#page_8)
24.  [9](#c01.xhtml#page_9)
25.  [10](#c01.xhtml#page_10)
26.  [11](#p02.xhtml#page_11)
27.  [12](#p02.xhtml#page_12)
28.  [13](#c02.xhtml#page_13)
29.  [14](#c02.xhtml#page_14)
30.  [15](#c02.xhtml#page_15)
31.  [16](#c02.xhtml#page_16)
32.  [17](#c02.xhtml#page_17)
33.  [18](#c02.xhtml#page_18)
34.  [19](#c02.xhtml#page_19)
35.  [20](#c02.xhtml#page_20)
36.  [21](#c03.xhtml#page_21)
37.  [22](#c03.xhtml#page_22)
38.  [23](#c03.xhtml#page_23)
39.  [24](#c03.xhtml#page_24)
40.  [25](#c03.xhtml#page_25)
41.  [26](#c03.xhtml#page_26)
42.  [27](#c03.xhtml#page_27)
43.  [28](#c03.xhtml#page_28)
44.  [29](#c03.xhtml#page_29)
45.  [30](#c03.xhtml#page_30)
46.  [31](#p03.xhtml#page_31)
47.  [32](#p03.xhtml#page_32)
48.  [33](#c04.xhtml#page_33)
49.  [34](#c04.xhtml#page_34)
50.  [35](#c04.xhtml#page_35)
51.  [36](#c04.xhtml#page_36)
52.  [37](#c04.xhtml#page_37)
53.  [38](#c04.xhtml#page_38)
54.  [39](#c04.xhtml#page_39)
55.  [40](#c04.xhtml#page_40)
56.  [41](#c04.xhtml#page_41)
57.  [42](#c04.xhtml#page_42)
58.  [43](#c04.xhtml#page_43)
59.  [44](#c04.xhtml#page_44)
60.  [45](#c04.xhtml#page_45)
61.  [46](#c04.xhtml#page_46)
62.  [47](#c04.xhtml#page_47)
63.  [48](#c04.xhtml#page_48)
64.  [49](#c05.xhtml#page_49)
65.  [50](#c05.xhtml#page_50)
66.  [51](#c05.xhtml#page_51)
67.  [52](#c05.xhtml#page_52)
68.  [53](#c05.xhtml#page_53)
69.  [54](#c05.xhtml#page_54)
70.  [55](#c06.xhtml#page_55)
71.  [56](#c06.xhtml#page_56)
72.  [57](#c06.xhtml#page_57)
73.  [58](#c06.xhtml#page_58)
74.  [59](#c06.xhtml#page_59)
75.  [60](#c06.xhtml#page_60)
76.  [61](#c06.xhtml#page_61)
77.  [62](#c06.xhtml#page_62)
78.  [63](#c06.xhtml#page_63)
79.  [64](#c06.xhtml#page_64)
80.  [65](#c06.xhtml#page_65)
81.  [66](#c06.xhtml#page_66)
82.  [67](#c06.xhtml#page_67)
83.  [68](#c06.xhtml#page_68)
84.  [69](#c06.xhtml#page_69)
85.  [70](#c06.xhtml#page_70)
86.  [71](#c06.xhtml#page_71)
87.  [72](#c06.xhtml#page_72)
88.  [73](#c06.xhtml#page_73)
89.  [74](#c06.xhtml#page_74)
90.  [75](#c06.xhtml#page_75)
91.  [76](#c06.xhtml#page_76)
92.  [77](#c06.xhtml#page_77)
93.  [78](#c06.xhtml#page_78)
94.  [79](#c06.xhtml#page_79)
95.  [80](#c06.xhtml#page_80)
96.  [81](#c06.xhtml#page_81)
97.  [82](#c06.xhtml#page_82)
98.  [83](#c06.xhtml#page_83)
99.  [84](#c06.xhtml#page_84)
100.  [85](#c06.xhtml#page_85)
101.  [86](#c06.xhtml#page_86)
102.  [87](#c06.xhtml#page_87)
103.  [88](#c06.xhtml#page_88)
104.  [89](#c06.xhtml#page_89)
105.  [90](#c06.xhtml#page_90)
106.  [91](#c06.xhtml#page_91)
107.  [92](#c06.xhtml#page_92)
108.  [93](#c06.xhtml#page_93)
109.  [94](#c06.xhtml#page_94)
110.  [95](#c06.xhtml#page_95)
111.  [96](#c06.xhtml#page_96)
112.  [97](#c06.xhtml#page_97)
113.  [98](#c06.xhtml#page_98)
114.  [99](#c06.xhtml#page_99)
115.  [100](#c06.xhtml#page_100)
116.  [101](#c06.xhtml#page_101)
117.  [102](#c06.xhtml#page_102)
118.  [103](#c06.xhtml#page_103)
119.  [104](#c06.xhtml#page_104)
120.  [105](#c06.xhtml#page_105)
121.  [106](#c06.xhtml#page_106)
122.  [107](#c06.xhtml#page_107)
123.  [108](#c06.xhtml#page_108)
124.  [109](#c06.xhtml#page_109)
125.  [110](#c06.xhtml#page_110)
126.  [111](#p04.xhtml#page_111)
127.  [112](#p04.xhtml#page_112)
128.  [113](#c07.xhtml#page_113)
129.  [114](#c07.xhtml#page_114)
130.  [115](#c07.xhtml#page_115)
131.  [116](#c07.xhtml#page_116)
132.  [117](#c07.xhtml#page_117)
133.  [118](#c07.xhtml#page_118)
134.  [119](#c07.xhtml#page_119)
135.  [120](#c07.xhtml#page_120)
136.  [121](#c07.xhtml#page_121)
137.  [122](#c07.xhtml#page_122)
138.  [123](#c08.xhtml#page_123)
139.  [124](#c08.xhtml#page_124)
140.  [125](#c08.xhtml#page_125)
141.  [126](#c08.xhtml#page_126)
142.  [127](#c08.xhtml#page_127)
143.  [128](#c08.xhtml#page_128)
144.  [129](#c08.xhtml#page_129)
145.  [130](#c08.xhtml#page_130)
146.  [131](#c08.xhtml#page_131)
147.  [132](#c08.xhtml#page_132)
148.  [133](#p05.xhtml#page_133)
149.  [134](#p05.xhtml#page_134)
150.  [135](#c09.xhtml#page_135)
151.  [136](#c09.xhtml#page_136)
152.  [137](#c09.xhtml#page_137)
153.  [138](#c09.xhtml#page_138)
154.  [139](#c09.xhtml#page_139)
155.  [140](#c09.xhtml#page_140)
156.  [141](#c09.xhtml#page_141)
157.  [142](#c09.xhtml#page_142)
158.  [143](#c10.xhtml#page_143)
159.  [144](#c10.xhtml#page_144)
160.  [145](#c10.xhtml#page_145)
161.  [146](#c10.xhtml#page_146)
162.  [147](#c10.xhtml#page_147)
163.  [148](#c10.xhtml#page_148)
164.  [149](#c10.xhtml#page_149)
165.  [150](#c10.xhtml#page_150)
166.  [151](#c10.xhtml#page_151)
167.  [152](#c10.xhtml#page_152)
168.  [153](#c10.xhtml#page_153)
169.  [154](#c10.xhtml#page_154)
170.  [155](#c10.xhtml#page_155)
171.  [156](#c10.xhtml#page_156)
172.  [157](#c10.xhtml#page_157)
173.  [158](#c10.xhtml#page_158)
174.  [159](#c10.xhtml#page_159)
175.  [160](#c10.xhtml#page_160)
176.  [161](#c10.xhtml#page_161)
177.  [162](#c10.xhtml#page_162)
178.  [163](#c10.xhtml#page_163)
179.  [164](#c10.xhtml#page_164)
180.  [165](#p06.xhtml#page_165)
181.  [166](#p06.xhtml#page_166)
182.  [167](#c11.xhtml#page_167)
183.  [168](#c11.xhtml#page_168)
184.  [169](#c11.xhtml#page_169)
185.  [170](#c11.xhtml#page_170)
186.  [171](#c11.xhtml#page_171)
187.  [172](#c11.xhtml#page_172)
188.  [173](#c11.xhtml#page_173)
189.  [174](#c11.xhtml#page_174)
190.  [175](#c11.xhtml#page_175)
191.  [176](#c11.xhtml#page_176)
192.  [177](#c11.xhtml#page_177)
193.  [178](#c11.xhtml#page_178)
194.  [179](#c11.xhtml#page_179)
195.  [180](#c11.xhtml#page_180)
196.  [181](#c12.xhtml#page_181)
197.  [182](#c12.xhtml#page_182)
198.  [183](#c12.xhtml#page_183)
199.  [184](#c12.xhtml#page_184)
200.  [185](#c13.xhtml#page_185)
201.  [186](#c13.xhtml#page_186)
202.  [187](#c13.xhtml#page_187)
203.  [188](#c13.xhtml#page_188)
204.  [189](#b01.xhtml#page_189)
205.  [190](#b01.xhtml#page_190)
206.  [191](#b01.xhtml#page_191)
207.  [192](#b01.xhtml#page_192)
208.  [193](#b01.xhtml#page_193)
209.  [194](#b01.xhtml#page_194)
210.  [195](#b01.xhtml#page_195)
211.  [196](#b01.xhtml#page_196)
212.  [197](#b01.xhtml#page_197)
213.  [198](#b01.xhtml#page_198)
214.  [199](#b01.xhtml#page_199)
215.  [200](#b01.xhtml#page_200)

# Foreword

It’s safe to say that information security and the industry surrounding it has exploded into a massive, constantly growing sector around the world. Like many other professions within technology, the main attribute which has secured many organizations success (or failure) in maintaining their relevance has been their ability to adapt. In the case of security, we are constantly adapting to methods used by malicious actors with the hopes of becoming as secure as possible – with the goal of identifying (and remediating) vulnerabilities prior to an attack.

As security professionals we understand that it isn’t a matter of *if* an event happens, but *when*. Although nothing can be completely secure, it’s our job to work towards obtaining a level of maturity within our security programs that are proactive against potential threats. Although zero days will always exist, it’s our job to stay up to date and as protected as possible, which can be very costly, especially for many organizations that don’t fully understand security and (in many situations) are hesitant to move forward with a proper budget for what is needed to enable adequate professionally accepted levels of protection.

Information security, or cybersecurity, is still in its infancy. This may be a shocking statement to someone who doesn’t work within the industry; it is, however, accurate. Only recently have many universities begun offering degrees in the field of cybersecurity. Many pieces of software that would be considered a “must have” for a company’s defense in depth weren’t in existence just a couple of short years ago.

Many professionals in the industry have moved to their positions as security specialists after previously working in general information technology. I have worked with many organizations, in both the private and the public sectors, and at this point in time, from what I’ve witnessed, a very small fraction of security professionals have been formally educated in security, and rely heavily on certifications to prove their understanding of the field. This is a blessing for those who need to obtain credentials quickly without the slow drag of the many years of college, but also is a curse for those with certifications but little real world experience. An overwhelming number of professionals are learning on the job, which can be daunting given the fact that many organizations are looking to increase their maturity as quickly as possible.

There are many gears turning in a proper security program. There’s an overall lack of understanding of security by those outside of the security team, so one of the most prominent procedures by security professionals is to understand how to assign tasks to thelimited resources they have while properly managing a security program that grows in maturity on a constant basis. All in a world where new vulnerabilities can be found daily.

It’s no secret that software security and web application security are fast-growing segments within the field of cybersecurity. Every organization has a web presence. Every organization uses software. Individuals also use software and web applications in their daily lives, assets which hold personally identifiable information, and whose contents can greatly range in sensitivity.

Although identifying vulnerabilities through continuous testing is a powerful activity, many organizations don’t have the resources or budget to consider it as an option. In search for a remedy to this situation, I have seen many explore the option of creating or joining a bug bounty program, albeit reasons for considering such a program are not limited to such issues. This can clearly be seen in large organizations’ involvement with their own bug bounty programs. It’s quickly becoming a standard for many large companies to have a bug bounty program, either in house or through a third party.

Bug bounty programs may be new, but they have caught on quickly with proactive organizations seeking to be more secure. It was only in 2013 (less than a decade as of this writing) that Katie Moussouris created Microsoft’s first bug bounty program. In March 2016, Moussouris would also be involved with the creation of the Department of Defense’s “Hack the Pentagon” pilot program, which would serve as the United States Federal Government’s first bug bounty program. Bug bounty programs have gained in popularity due to their benefits greatly outweighing their negatives, many of which are explained clearly within this book, which at the time of writing is geared to be the first wide-release publication on how to create and manage a bug bounty program.

This book is a critical asset for security professionals who seek to understand how to build and operate a bug bounty program. Security professionals can use this book as a guide for the creation of their own bug bounty program. Professionals across all domains of security can use this book to quickly absorb the years of information acquired by real world experience to understand the subject and provide more value to their team.

Robert (@rej\_ex) Willis

# Acknowledgments

There are far too many influential people in my career to mention in this section. I’m thankful for all of the information security individuals who have let me learn alongside them, given me opportunities, and have put my skills to the test. I’ve learned many lessons along the way.

A special thank-you to my friend Christian Bobadilla is in order. Christian is one of the most talented application security experts I know, and his humility keeps him out of the information security limelight. Through me, your excellent advice and mentoring lives. If it weren’t for you, I wouldn’t know even a quarter of what I do about bug bounty programs. Thank you for being a positive role model in my life. It’s exceedingly difficult to find people who are not only intellectually sharp and humble but also incredible leaders. This book is dedicated to the faith that you have put in my abilities.

One final dedication: to my father, who encouraged me to try my best at all times. Rest in peace.

# Part 1   
Bug Bounty Overview

#  1   
The Evolution of Bug Bounty Programs

## 1.1 Making History

Understanding the evolution of bug bounty programs first requires familiarity with the hacking landscape, or as many in the information security field know it, penetration testing. Security researchers haven’t always been respected or given the opportunity to shine. Throughout history, hacking has been a word that scares the public and creates waves of fear inside a company when rumors of a “hack” spread. The first bounty paid for breaking into something (in recorded history) was in 1851. Charles Alfred Hobbs was paid roughly the equivalent of $20,000 to pick a physical lock. ([https://www.itspmagazine.com/itsp-chronicles/history-and-interesting-facts-about-bug-bounties-an-appsec-usa-2017-panel-recap](https://www.itspmagazine.com/itsp-chronicles/history-and-interesting-facts-about-bug-bounties-an-appsec-usa-2017-panel-recap)).

The first actual bounty program was run by Netscape and it began in 1995. The primary scope was application testing for Netscape Navigator 2.0., their primary product. Slowly, other enterprises started to adapt their own bug bounty programs and offer awards. Bug bounty crowdsourcing platforms introduced the new wave, compiling enterprise programs into a neat catalogue in which security researchers could hop into various programs and begin to participate. Bugcrowd was known as the first crowdsourcing platform in bug bounty history and has been a key player in enterprise bug bounty program management. The pioneers – Casey Ellis, Chris Raethke, and Sergei Belokamen – believed in connecting latent potential to unmet demand with the overall goal of making security easier for everyone. In addition, Ellis firmly believed in assisting security researchers in keeping their records clean. Casey Ellis has also expressed a desire to help educate the youth toward the idea of ethical hacking, rather than a life of crime, and part of the inspiration for creating such a company has to do with the ideal of destigmatizing security research.

In all actuality, reviewing the state and history of bug bounty programs gives the reader a valuable positive perspective, but enterprises are slow to adapt. Even since 1995, there are still fewer than 400 bug bounty programs and 1600 vulnerability disclosure programs that exist in the world. The surprisingly small number of programs that exist in the world represent the resistance and conservatism of the field of legal hacking, otherwise known as security research.

## 1.2 Conservative Blockers

When information security specialists learn about bug bounty programs, many of them are excited to get involved. Application security is a growing field, and modern day web, mobile, and hardware assets need to be protected. With such an essential requirement to protect applications, enterprises still resist the absolute necessity of making vulnerability reporting management a prioritized incentive. As with everything, there’s not a “one-size-fits-all” answer for why an enterprise would ignore application security; however, many factors play a role in the resistance that is widespread, even today. For example, here are some of the reasons a company may decide to ignore the idea of a bug bounty program:

*   Increased threat actor activity.
*   Security researchers scamming.
*   Applications being a small consideration.
*   Enormous budgetary requirements.
*   Other security tooling as a priority.

There are obviously several other reasons an enterprise may believe a bug bounty program will cause unnecessary risk or negative effects. Debunking the above five defined points will give people a better understanding of why being afraid is natural, but it can be detrimental to the overall health of a good application security program.

## 1.3 Increased Threat Actor Activity

An enterprise may be fearful that establishing a bug bounty program will cause an increase of malicious threat actors attempting to hack into or successfully exploiting applications. The logic can be portrayed as such, “If an enterprise bug bounty program is established, then security researchers will be allowed to hack, and it will be impossible to tell who is malicious.” The problem with this statement’s assumption that threat actors are hiding among security researchers is one of a common philosophical logical fallacy: the Slippery Slope.

The Slippery Slope logical fallacy is best defined as, “A course of action that seems to lead inevitably from one action or result in another with unintended consequences.” In layman’s terms, the translation of the Slippery Slope in the security research scenario is, “If the enterprise allows security researchers to conduct research, we will be maliciously exploited.” It’s best to imagine the scenario of increased threat actor activity with the other perspective in mind. Without a bug bounty program, flaws may never be identified – vulnerabilities that could compromise an organization’s sensitive information or intellectual property.

Enterprises considering operating bug bounty programs should learn effective logging and prevention through logging mechanisms and web application firewalls, which are discussed later in this book.

## 1.4 Security Researcher Scams

Any type of business that relies on services rendered by another party should always be weary of scamming. Understanding the vulnerability types, criticality, and assessing payment amounts will always be the best course of action for a company running a bug bounty program. Still, the idea of scamming isn’t a new one. Potential program managers have to learn best practices and understand the basics of vulnerability management. Nonetheless, protections for programs are in place. Managed services offered through bug bounty crowdsourcing platforms such as Bugcrowd and HackerOne will become useful tools. The triage team will assist in validating the legitimacy of a vulnerability which can assist in preventing scamming. Program managers shouldn’t solely rely on the validation, but scamming happens far more infrequently than enterprises that are on the fence imagine.

## 1.5 Applications Are a Small Consideration

Enterprises that avoid bug bounty programs because of the idea of applications being a small attack surface are asking for trouble. When employees tasked with the security of a company evaluate vulnerability potential, the obvious go-to is to secure the network and related assets. However, web and mobile applications in particular have become exceedingly complex. With multiple development languages and servers, the attack surface is far greater than one might imagine. Consider the following example:

> Server → Hosts one part of the web application → One assigned IP address
> 
> Web application → Connected to multiple servers → Multiple IP addresses

The deployment of an enterprise’s assets will always be the determinant factor in the attack service; however, modern applications are becoming more interconnected than they ever were in the past. It’s easy to think about a “server” as an asset with a wide attack surface, and in many cases, that is true, and the attack vectors will always vary. Regardless, enterprises should not consider the value of a bug bounty program as something minute and ineffective. In addition, flawed application logic may result in the exploitation of the network and enterprises may not consider that. For example, SQL (Structured Query Language) injection can result in a full server-database dump or remote code execution on the network. Server side request forgery can result in the exposure of sensitive information leading to unauthorized server access or pivoting to other parts of the network. Application security is a large undertaking and neglecting it can result in the full compromise of an enterprise.

## 1.6 Enormous Budgetary Requirements

Bug bounty programs scale. The size and operation of the bug bounty program is up to the enterprise to decide. In addition, if the company isn’t giant, it’s unrealistic to assume that the enterprise would have to pay a large sum of money to get a program up and running. With bug bounty crowdsourcing becoming the norm, companies like Bugcrowd and HackerOne are willing to have scoping calls with leadership to identify a fair pricing model for program management. The price of program management is well worth the cost of identifying vulnerabilities that can result in the loss of hundreds of thousands, if not millions, of dollars in assets or compliance violations such as GDPR (General Data Protection Regulation) or the California Privacy Act. Application security, like any other subbranch of security, is an investment – and security doesn’t typically see hefty returns on investment. Information security doesn’t make a company money: it protects the company from losing money, allowing the acquisition of money.

## 1.7 Other Security Tooling as a Priority

Out of all of the other potential worries for setting up a program, security tooling is a legitimate concern. Balancing a budget requires coordination with all levels of leadership and an overall evaluation of security posture. For example, establishing a bug bounty program isn’t likely a good idea if the enterprise does not have a web application firewall, or a decent endpoint protection and response solution. Coordination with the security team will have to occur, but if all other bases are covered, there’s no reason a basic bug bounty program cannot be established.

## 1.8 Vulnerability Disclosure Programs vs. Bug Bounty Programs

Even for the most technical of individuals, understanding the difference between a vulnerability disclosure program (VDP) and a bug bounty program (BBP) can be mind boggling. Even still, engineers who run bug bounty programs may make the mistake over calling a bug bounty program a vulnerability disclosure program, or vice versa. Understanding the difference between the two is essential to communicating expectations clearly and educating the general public on the day-to-day processes involved.

### 1.8.1 Vulnerability Disclosure Programs

Vulnerability disclosure programs are the method used when an enterprise wants to facilitate the disclosure of vulnerabilities but not offer any sort of paid incentive. Vulnerability disclosure programs can be considered a goodwill type of vulnerability management process. The two types of vulnerability disclosure programs are managed and unmanaged. An unmanaged program would be a vulnerability disclosure program that is offered in-house, with an associated good faith based effort. In contrast, a managed vulnerability disclosure program could be one where program managers are assisted by a triage team from a bug bounty crowdsourcing platform such as Bugcrowd or HackerOne. As an incentive to researchers, they are offered points in return for reports, which is an essential part of leveling-up and getting invited to private programs, which typically have less competition for security researchers and a better chance of vulnerability finding.

Private vulnerability disclosure programs are also allowed through crowdsourcing platforms, reducing the costs associated with paying bounties as points will be rewarded.

### 1.8.2 Bug Bounty Programs

Bug bounty programs are typically more mature vulnerability disclosure programs, offering rewards in place of points. When program managers want to convert their vulnerability disclosure programs to bug bounty programs, the process is typically as simple as initiating a financial incentive for security research. Bug bounty programs carry more weight and attract more professional hackers. For example, some of the best security researchers may never participate in vulnerability disclosure programs because the time they spend evaluating bug bounty programs could easily be time converted to a cash flow. An enterprise’s end state should always be aspiring to reach paid-program participation. Security research consumes a lot of time and an enterprise should want to pay its researchers for the time spent. If confused, think of it like this: how many people are willing to do a full-time job for free versus paid? Hobbyists will always exist, but the participation of some of the greatest security researchers can only be obtained with monetary incentives.

## 1.9 Program Managers

Throughout the book, the phrase “program manager” will come up frequently. A program manager isn’t to be thought of as a traditional manager who coordinates employee activity. Rather, program managers are any employee who deals with the configuration or management of an enterprise bug bounty program. For example, the title of the employee doesn’t matter: an application security engineer or a chief information security officer could be a program manager. The only consideration is that the employee must have oversight of the program and the ability to make changes. After all, even an employee who is remediating bugs is managing the day-to-day workflow of the program.

## 1.10 The Law

Historically, the law hasn’t always been kind to security researchers. Even today, hacking is still considered dangerous or controversial to nontechnical people. A substantial part of society does not view hacking as an art, but as a criminal behavior in all circumstances. When most people view hacking as an overwhelmingly criminal activity, it is unsurprising that legitimate researchers often find themselves working in a hostile environment, and one that threatens to punish them. Many documented instances of security researchers being threatened with legal action exist. A quick search on the Internet of the phrase “security researcher threatened” will bring up quite a bit of news.

Redefining the expectations of security research starts with educating the community – and bug bounty programs play a gigantic role in helping society understand that hacking can be ethical. Vulnerability disclosure programs are a great start, but the end state is a transition to a bug bounty program that allows hackers to receive fair compensation for their efforts. Nonetheless, security research without utilizing a bug bounty program can be highly dangerous and can risk the livelihood of the individual conducting the research. A bug bounty program and the safe harbor clauses it contains can help to guarantee researcher safety. Vulnerability research has changed the landscape of what category hackers fall into, and has allowed quite a bit of flexibility and protection from punishment from the law.

## 1.11 Redefining Security Research

During the course of this book, the reader will see what skills are necessary to create, manage, and refine bug bounty programs. The one important aspect to remember when reading this book is that establishing or managing a bug bounty program is only one small part of a much bigger picture. History is being made, in real time, and the expansion of ethical hacking into the enterprise space is a necessary component of ensuring the safety of company assets and user data. Understanding how important programs can be is a way of information security that should be shared in a positive light. The best way to bring attention to the ethical nature of thousands of security researchers while they hack and make a difference is to operate with an open mind and attempt to give honest disclosure, while awarding processes a fair evaluation on every occasion.

Security research, or in other words the art of hacking, needs the assistance of enterprises that operate bug bounty programs – to adequately reshape the landscape of hacking. As a community, we cannot let the fear of hacking prevail as the action of shaming individuals that care about the security of an organization ends up causing more harm than good. Reshaping the world will take the cooperation and understanding of all individuals involved in the process. In addition, enterprises should maintain a neutral state of mind. Security researchers hack for various reasons: money, credibility, press, portfolio building, or fun. The reason vulnerability research is conducted should hardly matter: the only responsibility of the enterprise is to provide a safe environment and to patch the vulnerabilities. Fear of the press, while a legitimate concern, can be redirected into positive energy that rewards and values the researchers. If the organization engages openly with the researcher, it could well result in a positive outcome, in terms of media spin or as a learning outcome.

## 1.12 Taking Action

It shouldn’t come as a surprise that word of mouth is a powerful tool. The enterprise space is ever-expansive and companies will constantly compete to be better than their competition. As a society, the establishment of honest programs and disclosure processes can influence the entire enterprise space. Here are some ways program managers or potential program managers can help assist researchers and the security research space.

### 1.12.1 Get to Know Security Researchers

Be involved in the community aspect of research. Whether reading publications on CVEs (common vulnerabilities and exposures) or bug writeups, participating in Twitter conversations, or connecting with hackers on LinkedIn, it’s important to understand all aspects of the landscape.

### 1.12.2 Fair and Just Resolution

Running a program isn’t the final solution. Managing an enterprise program requires collaboration and fair resolution processes. Ensuring that the program stays ethical and cares about the security researchers is a key part of spreading the positive aspects of bug bounty programs.

### 1.12.3 Managing Disclosure

While not recommended until a program is more established, eventually enterprises should strive to help researchers disclose their findings to the public when patched, if they wish to do so. Research disclosure helps inspire new generations of hackers and also receives enterprise, and potentially media, attention. Nonetheless, within a program security researchers should maintain the ability to disclose in any circumstance if the information is redacted enough or if a CVE exists on an enterprise product/there’s user or customer PII exposure that needs to go public.

### 1.12.4 Corrections

Program managers should strive to speak highly of researchers and the great work that is provided as a service. “Hackers” aren’t malicious by default, and program managers receive first-hand experience of ethical behavior. When hackers are called malicious, program managers should strive to set the record straight and describe the differences between an ethical hacker (security researcher) and a malicious hacker (threat actor).

### 1.12.5 Specific Community Involvement

Joining the movement for better disclosure is the first step to a greater collaboration between researchers and programs. Casey Ellis built a one-of-a-kind community named Disclose as a way for companies to participate in the conversation. ([https://disclose.io](https://disclose.io)).

# Part 2   
Evaluating Programs

# 2   
Assessing Current Vulnerability Management Processes

## 2.1 Who Runs a Bug Bounty Program?

Ultimately, who would be responsible for starting a bug bounty program? Ideally, a bug bounty program manager should be whoever does the day-to-day work in coordinated application or web application security measures.

Not every engineer has the dilemma of figuring out their role in the vulnerability management process. If an engineer is hired as an application security engineer, it’s a given that they will have to be responsible for monitoring and triaging any application vulnerabilities as they pertain to mobile or web applications. It’s important to understand that engineers who have the sole responsibility of vulnerability management typically focus on network vulnerabilities. It would be unusual to see a security engineer on the vulnerability management team identify, remediate, or manage application vulnerabilities.

The ideal situation is one in which an application security manager and at least one application security or general security engineer set up and manage a bug bounty program. However, this isn’t always the case. Therefore, it’s important to have the tools to know what to do if it’s your responsibility to establish a program.

## 2.2 Determining Security Posture

The most difficult part of the entire process of executing a bug bounty program for an enterprise is evaluating the risk and risk mitigation programs. While a reader may not be a compliance expert, or an endpoint detection and response engineer, determining which role that will have to be played in the vulnerability management process is nonnegotiable. The position that an engineer was hired to fill at the company will directly assist one in understanding what specific expectations lie ahead.

“Security posture” is a flexible term. Truthfully, it would be impossible to recommend an in-depth and thorough analysis without understanding what type of business use case is in play. Risk analysis requires visualizing how all of the parts of a security team come together, and rationally determining how it plays into application security. As a rule of thumb, it can be evaluated from the perspective of management or engineering. While there are many other aspects and subcategories of information security, a fair baseline will be starting with understanding some of the core differences in responsibility as they pertain to management and engineering:

## 2.3 Management

It wouldn’t be absurd to suggest that an application security manager is typically responsible for evaluating the connections between the product and the application security team, and other departments in the organization. It’s the manager’s job to choose the right personnel to ensure the successful day-to-day operation of the enterprise. After operational pace is established, a manager has to determine which appropriate remediation steps need to occur before creating a bug bounty program. In the application security realm, vulnerability remediation communication occurs between a wide range of groups. As a baseline here are some of the teams that a manager will have to collaborate with.

### 2.3.1 Software Engineering Teams

Responsible for the development of the applications that will be subject to testing when a bug bounty program is established.

### 2.3.2 Security Departments (Security Operations, Fraud Prevention, Governance/Risk/Compliance, Edge Controls, Vulnerability Management, Endpoint Detection, and Response)

The various subteams that make up the root of security, subject to be vastly different based on the structure of the organization.

### 2.3.3 Infrastructure Teams

Responsible for the backbone of the organization that is meant for hosting applications and various assets that both stakeholders and users/customers operate.

### 2.3.4 Legal Department

Application security managers may have to communicate with the legal department if malicious activity is noted. Therefore, managers should have close relationships with legal representatives.

### 2.3.5 Communications Team

Depending on the structure of the organization, social media marketing may be up to the communications or marketing teams. Researchers may reach out via social media to disclose vulnerabilities and application security managers should be aware of this, and adequately prepare the responsible team.

## 2.4 Important Questions

It’s crucial to keep in mind that the answers to some of the questions covered in this section may be trivial. If known, that’s absolutely fantastic! When the answers are not known, future program managers may be able to find out without disrupting the team or space. Managers should make an effort to be cordial and responsive to concerns or pushback. It’s always better to know than to assume: operating in a presumptuous way can open the door to security issues or ineffective vulnerability management processes. In reality, the questions that proceed are to be used as a baseline and not as a full representation of an enterprise risk management guide.

During the processes of identifying risk, application security managers will find that many other questions arise – that’s great! Ask them! Operating in a way that creates a dialogue between the various teams and application security is a great first step toward building rapport and trust. Maintaining trust is an essential part of securing the organization, as it is impossible to remediate vulnerabilities if other teams do not trust the remediation techniques that will be placed by the application security team. While it may not initially be possible to understand how every single team works together, application security is most effective when an application security manager can envision the macrovision of enterprise security. In addition, application security managers should avoid siloing off and exercising an “unreachable” state. The resolution of vulnerabilities can occur twice as fast if managers know the other major players and innovators within the organization. Here are some questions that can be asked with explanations of why these questions should be answered.

## 2.5 Software Engineering

### 2.5.1 Which Processes Are in Place for Secure Coding? Do the Software Engineers Understand the Importance of Mitigating the Risks Associated with Vulnerable Code?

Once again, application security managers should never assume that engineers have a working knowledge of secure coding. The best way to achieve enterprise security is to understand the way software engineers build, and assist in establishing best practice. No organization is perfect. Therefore, it will take time to work with all of the teams that exist in the enterprise. Secure coding platforms such as Checkmarx Codebashing and security awareness incentives such as hacking demos, security riddles, and other fun educational events can help break down any barriers that may exist between application security and software engineering. ([https://www.checkmarx.com/products/codebashing-enterprise-application-security-training](https://www.checkmarx.com/products/codebashing-enterprise-application-security-training)).

### 2.5.2 How Effective Are Current Communication Processes? Will Vulnerabilities Be Quickly Resolved If Brought to Their Attention?

Evaluating the communication processes and vulnerability remediation expectations will develop over time. The question of effective communication and resolution isn’t one to ask software engineering teams, but it is a matter that should be carefully documented, and reevaluated when more data is available.

### 2.5.3 Is the Breadth of Our Enterprise’s Web and Mobile Applications Immense? Which Processes Are Engineers Using for Development in the Software Development Lifecycle?

In summary, managers should identify how many applications exist and what the software development lifecycle (SDLC) looks like. Preventing vulnerabilities starts with implementing adequate application security processes beforehand.

## 2.6 Security Departments

### 2.6.1 How Does Security Operations Manage Incidents? Will Employee Assistance Be Provided from the Security Operations Team If a Threat Actor Manages to Exploit an Application Vulnerability? Which Tools Do They Have in Place?

Incidents are inevitable for any growing organization, and an incident that only affects a security operations team, or an application security team, is unrealistic. Application security managers will have to bridge the communication gap between engineers and management on both teams to collaborate on investigations. Establishing thorough processes in the event of an application incident that ends up affecting both teams (such as a client side web application exploit that turns into a server side exploit) isn’t negotiable. Transparency with incident resolution should be maintained between both teams. Application security managers should know what forensic tools, logging solutions, and endpoint detection response tools exist within the enterprise. Many of the tools owned by other security teams can greatly benefit the application security team during investigative or prevention processes. Team collaboration can allow for a togetherness mindset of security instead of a reluctance to provide assistance.

### 2.6.2 What Does the Fraud Prevention Team Do to Prevent Malicious Activities? How Many Occurrences Do They See of Issues such as Account Takeover, and Could They Potentially Create Application Vulnerabilities?

If a fraud team exists within the enterprise, application security will have a ton of collaboration work to do. For example, the aspects of security that the fraud team focus on are important areas of review for application security as well. If the fraud team sees instances of account takeover, application security engineers will have to brainstorm the prevention methodologies for the login page logic. Alternatively, if the fraud team starts to see a giant spike in gift card purchases, application security may have to review the application security of the gift card purchase and redemption pages to ensure that vulnerabilities do not exist. The possibilities are endless.

### 2.6.3 Are There Any Compliance Practices in Place and, If So, How Do They Affect the Vulnerability Management Process? What Does the Application Security Team Have to Do to Assist in Enterprise Compliance?

Compliance teams within the organization will have to review third-party security relationships as well as internal security compliance. Application security managers should understand the processes to best help in evaluating and remediating risks that may affect adequate compliance.

### 2.6.4 What Edge Tooling Is in Place to Prevent Attacks? Are Any of the Enterprise Applications at Risk of Being Exploited due to an IoT (Internet of Things) Device?

IoT is a large attack vector. The security of Internet-connected devices may be up to a dedicated team, such as an edge team, or may fall into the purview of a security operations team. Nonetheless, the exploitation of IoT devices is an important consideration for application security as these devices might directly connect to or host enterprise applications.

### 2.6.5 How Often Does Our Vulnerability Management Team Push for Updates? How Does the Vulnerability Management Team Ensure Servers in which Enterprise Applications Reside Are Secure?

Vulnerability management processes are complex, and when teams are dedicated to such efforts, the attack surface does end up reduced. However, knowing how the processes are coordinated for resolution is necessary for application security managers. For example, if a security researcher abuses a server identified from the web application because it’s out of date, the vulnerability management team will have to assist, and knowing what type of collaboration will need to occur is quite important.

## 2.7 Infrastructure Teams

### 2.7.1 What Are Infrastructure Teams Doing to Ensure Best Security Practices Are Enabled? How Long Will It Take the Infrastructure Team to Resolve a Serious Issue When a Server-side Web Application Is Exploited, or During a Subdomain Takeover Vulnerability?

Even though application security isn’t responsible for the security of servers, pivots can take place and a researcher may report an exploit to the application security team that involves a server. Application security managers will have to know what the coordination efforts look like to resolve the problem. In addition, collaborating with nonsecurity-oriented teams may prove challenging so it’s best to develop effective security practices before issues are identified.

### 2.7.2 Is There Effective Communication between Infrastructure, Vulnerability Management, Security Operations, and Endpoint Detection and Response?

On some occasions, a vulnerability will end up requiring the attention of many teams. Stressing the importance of security being a team fight, even for nonsecurity-based teams, will be the smoking gun of application security. The sooner teams understand that remediating vulnerabilities must be a priority, the easier collaboration will be.

## 2.8 Legal Department

### 2.8.1 How Well Refined is the Relationship between the Application Security Team and the Legal Department?

Transparent communication between application security and the legal department is necessary in the event that application security needs coverage should communications go awry with a security researcher or a threat actor is identified. Application security managers should attempt to build rapport with the legal department immediately.

### 2.8.2 What Criteria Are/Will Be Set Out for the Escalation of Issues?

Identifying enterprise regulations for the escalation of any identified vulnerabilities is a requirement. For example, the legal department will advise in the event that PII is accessed by a security researcher or an unauthorized threat actor.

### 2.8.3 Does the Legal Department Understand the Necessity of Bug Bounty Program Management?

If no communications have occurred between the legal department and the application security team, confusion may occur if an application security manager asks for guidance on a possible threat or breach scenario. A weak rapport between application security and the legal department could result in advice that includes threatening a security researcher. Application security managers should make an honest effort to explain to the legal department what bug bounty programs do and how they assist – given that they are not familiar with such processes.

## 2.9 Communications Team

### 2.9.1 Has the Communications Team Dealt with Security Researchers Before? Is the Importance Understood?

Asking employees on the communications team if they have dealt with security research is important. If the team has dealt with a security researcher reporting through social media, identify how the communication was carried out. Explaining the importance of adequate and cordial collaboration with a researcher is essential.

### 2.9.2 Was the Communications Team Informed of Bug Bounty Program Expectations?

Knowing how teams that manage social media intend to deal with a researcher who discloses a vulnerability publicly or through direct message is a key piece of information to have. Application security managers should redefine expectations with the teams to enable a direct line between the application security and communications team.

The importance of asking questions as a manager is to ensure that the enterprise is prepared for all of the vectors of risk before establishing a bug bounty program within the organization. Forging alliances and receiving answers to questions may not be the sole responsibility of management. Application security managers should discuss the risk assessment measures with engineers on the team and other employees in various security departments that may be able to achieve answers, or may even have answers already.

## 2.10 Engineers

An engineer’s primary responsibility is to assist management in determining all of the vulnerabilities and risks that could be directly related to or impact the application security team. It never hurts to ask questions, and arguably some of the best engineers will want to know everything about the process – just as management will. Many engineers that may come across this book will be in a position other than application security and may not be ready to take on the responsibility of a bug bounty program without a manager. If that’s the case, it’s crucial to review the management section and get a thorough grasp of vulnerability management and how it pertains to application security.

Engineers should care about the passion for the craft and the great contributions that researchers will put forward. Even if a security engineer has management who has put a substantial amount of effort into knowing the entire enterprise layout and application security responsibilities, they should aspire to ingest all of that information. There’s not a day that goes by in day-to-day responsibilities in which a security engineer does not need to be familiar with the various enterprise teams and vulnerability remediation best practices.

## 2.11 Program Readiness

Bug bounty programs are an amazing security tool. A good program can provide valuable insight and help enterprises continuously test their assets. It’s important to note that the effectiveness of a program can only be as good as the program manager who configures it. Future program managers should identify telltale signs that their organization may not be ready to start a bug bounty program. As already stated, close communication between the various teams and a precise definition of expectations are essential when setting up a bug bounty program.

Going through the various risk assessment and information gathering processes to define the enterprise security stance is not an option: it’s a requirement. Enterprises cannot build a house without a foundation, and avoiding any advance risk-assessment exercises will undoubtedly result in the shoddiest of bug bounty programs. While a bug bounty program can be a useful way to identify vulnerabilities, it isn’t the be all and end all, and engineers or managers who go through the process of attempting to set up a program without first evaluating the other aspects of security might burn their enterprise. Recovering is possible, but it would be better to carefully prepare and evaluate security gaps before launching a program. Even a limited bug bounty program can result in frustrated security researchers if communication gaps are not filled in before inviting researchers to participate in a program.

#  3   
Evaluating Program Operations

## 3.1 One Size Does Not Fit All

Future program managers need to understand how to work with what they have. When it comes to looking at the different options for programs, it’s important to remember that one size doesn’t fit all. One enterprise may run a successful public program, while another enterprise struggles to do so. The reason there seems to be such a wide variance in appropriate program types is because of the enterprise security model, configurations, and level of flexibility that a program may or may not have. In the application security space, there’s a lack of understanding when addressing program configuration, and a careful review during setup will give an enterprise the ability to gather relevant vulnerabilities and manage/resolve these issues effectively. Program managers must understand the key differences in the setup process for maximum success.

An enterprise’s bug bounty program is only as good as its reputation. Hackers will consistently engage with the program if they feel that it’s representing their needs efficiently. As a starting point, program managers will want to review all aspects of an established program in place and expand or retract as needed. If the enterprise does not have a bug bounty program, the goal to achieve will undoubtedly be to create an effective program from the ground-up.

## 3.2 Realistic Program Scenarios

In lieu of explaining program options with bullet points and graphs, read the following scenario of an ethical hacker who accidentally discovers a vulnerability, and what the approach would look like from their perspective. Then consider how to explain each option. By doing so, bug bounty program functionality can be better understood.

A hacker is using their favorite website to buy electronics and other home goods. The checkout process appears to be standard. They type in their name, their address, email address, and so on. Now it’s time to pay. The hacker enters their card information and submits the request to the server. The standard “thank you for your purchase” message and confirmation number didn’t appear. Instead, they received an Internal Server Error (500).

At this point, red flags are flying at full mast. What happened, why is the hacker receiving this message? A hacker’s curiosity burns with the power of a thousand suns. The ethical hacker backpedals, carefully reviewing the checkout process. One by one, they decide to test each input field, adding a single quote to the end of the information submitted. They’ve now managed to replicate a possible SQL (Structured Query Language)injection by adding this single quote to the last name field of the checkout form. They save the POST request in a file, feed it into SQLMap and test the last name parameter. Within seconds they can now dump the entire SQL database and get a reverse shell, accessing every single piece of PII (personally identifiable information) on the company’s server. The hacker knows that they can take this even further. The hacker’s thoughts are now racing at a million miles per second, and their heart is beating uncontrollably fast. They quietly contemplate and think to themselves, “I’m not a criminal. I need to report this. What if a threat actor decides to exploit this vulnerability with malicious intentions?”

## 3.3 Ad Hoc Program

An ad hoc program is a program that may not necessarily be considered organized. Many enterprises have a security page where bugs can be reported, or instructions for reporting with a security.txt file hosted on the root domain, and others gamble on the probability of a hacker performing good faith reporting and contacting the company. If the perspective of a security researcher is considered, reporting the vulnerability might be difficult and various circumstances may deter a researcher from doing so. Primarily, even the most seasoned security researchers fear retaliation, and an ad hoc program leaves the floor open for guesswork. Researchers want to do the right thing, but hacking without permission is currently taboo and it leaves a lot to be desired.

With a wide variety of unknown enterprise-to-hacker response possibilities, researchers might avoid reporting vulnerabilities altogether. Assuming that the researcher wants to do the right thing, they will likely first check the website to look for a point of contact for the enterprise’s security team. If they don’t find anything, they may reach out to the company or security professionals on social media websites, or use a contact form on the website. If an enterprise maintains a new or underdeveloped security posture, or doesn’t adequately highlight various ways to get in contact about security issues, vulnerabilities may never be reported.

An enterprise may believe that utilizing a spontaneous reporting methodology seems useful, even foolproof. Unfortunately, it can be dangerous to assume that security researchers will reach the enterprise without any mention of a program. Security researchers come in all shapes and sizes, and from all walks of life. Language barriers and cultural differences may result in reported research that seems malicious or threatening. A company with security professionals that don’t understand proper vulnerability management or security research might end up threatening the researcher or reporting them out of fear. As a program manager, being aware of the potential threats that researchers face during disclosure could be a way to ease the pain of reporting.

In addition to a limited ad hoc reporting configuration preventing adequate communication, there are a wide range of vulnerabilities that exist, further complicating the situation. For example, a client side misconfiguration versus a server side misconfiguration might be managed by two completely separate teams. Additionally, a dedicated team to address all client side or server side exploits might be unrealistic. A certain block of servers may end up being managed by one team, and another block of servers managed by another team, and so on and so forth. Standard enterprise models have a lot of applications, servers, components, etc. An enterprise without a dedicated bug bounty program may open up the possibility for a lot of communication issues and misinterpretation, or a lack of understanding can lead to the researcher disclosing to the media, damaging the company’s reputation.

Company reputation aside, many bugs can be exploited in critical ways that could negatively impact revenue, customers, clients, and so on. One communication blunder in the research process can result in valuable and legitimate vulnerability findings being lost. Visibility through an established program, reluctance, or withdrawal of a researcher’s findings may have negative consequences – and ad hoc programs do not have adequate mediation because of existing biases, whereas a bug bounty platform allows researchers and enterprises to communicate with one another effectively.

It’s important to note that, while an ad hoc program may not be for every company, it doesn’t mean it’s completely ineffective. A smaller company with fewer employees or assets may not warrant the need for an organized third-party program. However, security engineers should keep that in mind and even still quote the cost of creating a third-party bug bounty program. Nonetheless, even if a company decides not to establish a program, they should be prepared to respond to, validate, and reward ad hoc findings in a way that is concise and fair to researchers. After all, while a researcher may not have had permission to test, the vulnerability exists and could lead to full-scale exploitation, irrevocably damaging the enterprise’s reputation or resulting in great monetary losses. Having an open mind will utilizing an ad hoc program is an essential part of doing so.

On a positive note, ad hoc programs are the cheapest possible solution. An enterprise should use this program until a baseline security posture is established, especially if they have nothing else. An ad hoc program will always be the cheapest option, but it’s apparent that it could take a toll on the communication between a researcher and an enterprise.

An ad hoc program is best defined for an enterprise that has the ability to manage large volumes of vulnerability reports. For example, if an enterprise is too large, they may find better results by offloading most, if not all, of their reporting architecture to a third-party crowdsourced research platform. Large enterprises that care about the state of their security will not offload; otherwise, it could put their data and assets at risk. Imagine if the enterprise in question were an ecommerce site that ran through a web development company. The company that became entrusted with the managing aspects of the enterprises’ services would be responsible for the security posture of the web application and the server that hosted the application. An important distinction to make is what the stance on custom application plugins is, as requiring the client to keep plugins updated might be something that would have to be considered. Even if plugins have to be kept up to date, doing so usually won’t warrant a full-scale bug bounty program, in comparison to a more standard projected enterprise model. Plugins that are derived from a library of on-demand applications will be maintained by third parties. If researchers find vulnerabilities that affect the applications, it will be considered a zero-day exploit. If reported through MITRE or other appropriate means, a notice will be sent out by the third-party provider (given the appropriate scenario), but an offload to a third-party provider for most of the infrastructure may result in the partner company not informing the company in the event of exploitation, and the enterprise must be vigilant to risks no matter what program model is used.

## 3.4 Note

This book won’t focus on the aspect of setting up custom-built vulnerability disclosure programs or bug bounty programs. The margin for error with the legality of paying researchers through a custom program could open up unnecessary risk, and the objective of this book strays away from any fully custom program setup that utilizes a proprietary platform solution. Without leveraging the extensive features and capacity of a program run through a bug bounty crowdsourcing platform, the overall considerations for vulnerability management become a lot larger. Please exercise caution if setting up a completely in-house solution. Ensure that a risk assessment is performed and that legal agreements are up to date and comply with the local, state, and government laws. If the enterprise has in-house lawyers, consult about potential legal mitigation before setting up the program. Enterprise vulnerability program managers must remember that a completely in-house program may need to extend into the field of compliance as well, owing to researchers who may submit PII or sensitive information such as payment information, home address, and so on, coupled with the required delivery of tax documentation. This book is not a replacement for any form of legal advice, so all and any program should be setup at one’s own risk, regardless of the platform used or created.

## 3.5 Applied Knowledge

### 3.5.1 Applied Knowledge #1

Imagine if the hacker from our earlier story takes the SQL vulnerability that was identified and searches for a way to report the vulnerability. If they search and find a lack of security email address, they may decide to use the customer support email address instead. Knowing that there’s a certain level of fragility with reporting a vulnerability with this much impact, they say something along the lines of:

> Hello,
> 
> My name is *X* and I’m a hacker. I’ve found a serious vulnerability that allows someone to obtain credit card information, passwords, addresses, and so on through a simple exploit. Please reply as soon as possible.<query id="Q1"> <p>Dear TS, Please set this as a block quote/displayed in some way.</p> </query>

Given a realistic scenario, a simple email that expresses the urgency is fairly effective. If a security professional were asked what should be done in the instance of an email as defined above, they would usually recommend that the customer service specialist gather more information or ask a set of questions and then forward the hacker to a specified email address for security purposes.

Unfortunately, that’s just not the most realistic approach. Using an ad hoc program, vulnerability management professionals aren’t typically coordinating with their customer support team on the bug resolution process. Communication breakdown can open up the possibility of a wide variety of security issues which may hinder the professional resolution of vulnerabilities. As an organization, it feels easy enough to avoid a researcher – but no one has the power to wish away a vulnerability, not even governments or top officials.

#### 3.5.1.1 Private Programs

When an enterprise sets up the baseline security posture, the next step is to harden the environment further. To do so, they typically establish a private bug bounty program. Private programs are the evolution of ad hoc programs. They demonstrate a willingness to commit to rewarding and encouraging active participation. Private programs can be seen as a steppingstone to a wider vulnerability disclosure program.

A private program, compared to an ad hoc program, is a day and night difference. Instead of waiting for researchers to approach the enterprise with vulnerabilities, the responsibility and expectation of the program managers and engineers is to actively seek researchers to participate in their bug bounty program. Similarities will always exist in some researcher intake processes. However, establishing a legitimate program will make it easier to manage ad hoc researchers. Private bug bounty programs facilitate enterprises to manage the flow of hackers and control which assets are tested, and when.

Still, operating a private program comes with its own challenges. For example, a poorly configured, mismanaged, or neglected program can result in the same issues that an ad hoc program results in. If researchers do not feel heard, some will quit, while others won’t hesitate to attack the reputation of a company. Neglected programs have similar results. Therefore, it’s exceedingly important to remember that just because the program is private doesn’t mean that it can tolerate mismanagement.

### 3.5.2 Applied Knowledge #2

The hacker takes their SQL vulnerability and searches for a way to report the vulnerability. Upon finding no security email address, they decide to use the customer support email address. This scenario differs in one key way. Customer support knows that the enterprise has a team that’s responsible for vulnerability management. Customer support quickly forwards the email over to the security team, which notifies the bug bounty program manager. An email can now be sent to the hacker, and they can be onboarded into the private program.

A key takeaway from this applied knowledge scenario is to ensure that the customer support team knows the appropriate point of contact for forwarding vulnerability-related email. As an engineer or a program manager responsible for managing engineers, be proactive. The sooner a meeting is held between the responsible point of contact at customer support and a bug bounty program manager, the easier it will be to deal with all future issues.

#### 3.5.2.1 Public Programs

The most dangerous type of vulnerability disclosure program is a public program, and dangerous here means, “If risk is poorly assessed prior to launching the program.” That’s not to say going public is bad, it’s to understand that being public facing can be risky for an enterprise that isn’t ready to take on the inevitable financial and psychological burdens this would involve. It shouldn’t come as a surprise that a public program will cost the enterprise much more money than any other program. Visibility equates to greater hacker participation, which converts to vulnerabilities, and in turn the organization is now responsible for paying the security researchers for their work.

An enterprise can easily destroy its reputation in the hacking community if the organization’s engineers are not ready to be responsible, or cannot be responsible, for managing too many vulnerabilities. Bug bounty program managers tend to look at programs through rose-tinted glasses. Unfortunately, a jaded perception of application and network strength can result in the destruction of a program that has just barely begun. It’s strongly recommended that an enterprise runs a private program for a decent amount of time before taking the leap into the public bug bounty space.

There’s not a set requirement for public release, but it’s important to know that an organization should never start with a public program. Running a private program for a while gives engineers a chance to understand the bug bounty process, sharpen their skills, and understand the spectrum of vulnerabilities before plunging into a visible world. That’s where more participation increases the risk of scrutiny and reputational damage.

### 3.5.3 Applied Knowledge #3

The hacker takes their SQL vulnerability and searches for a way to report it. Doing a quick search for a security point of contact, the hacker finds a public bug bounty program. Any communicative issues are mitigated and the researcher is able to easily report the vulnerability and be rewarded for their efforts.

When a hacker finds a public program, it’s the best possible situation for the researcher to be in. A researcher who can adequately receive a response for their efforts is a researcher who is more likely to be cordial and ready to engage with the enterprise in a constructive manner.

#### 3.5.3.1 Hybrid Models

Mixing multiple models together can easily be the best solution to a complex situation in which a private program is considered too limited and a public program is considered too visible. The standard model is a program that is private in participation, but public-facing. Although private but public-facing sounds confusing, it simply means a program that lets security researchers know they have a program, but it’s not actively organized on the bug bounty program platform as a public program that can be participated in. An enterprise can benefit from utilizing a hybrid model as it can help combine the best aspects of bug bounty programs. Even if the program is private, program managers *should implement a security.txt file under the/.well-known/directory of root domains*.

*What is a security.txt?* (Thanks to Duncan McAlynn @infosecwar for the reminder.)

Simply, it is a means of informing security researchers that a bug bounty program exists. Imagine if a hacker were to poke around at the web application and accidentally stumble upon a vulnerability. They may try to find a security contact at the organization and struggle to do so, which can further complicate the situation. Hackers typically start with fuzzing web applications, and even if the hacker misses the/.well-known/directory while fuzzing, a seasoned researcher is certain to check for a security.txt file manually if they need to report a vulnerability. To understand the best implementation of a security.txt file, please visit: [https://securitytxt.org](https://securitytxt.org) .

## 3.6 Crowdsourced Platforms

There are multiple bug bounty platform providers to choose from, but it would be a mistake to make a specific recommendation. The key companies that provided bug bounty platform setup and management are Bugcrowd, HackerOne, Integriti, and Synack. Program managers should decide for themselves based on pricing, configuration models, and the other range of functionality options. At the end of the day, application security engineers and their managers need to ensure that a consistent evaluation of their program provider is occurring. Engineers are hired to do a job: build, fix, configure, and innovate – and, as with any other engineering tool, crowdsourcing platforms should be evaluated regularly to enable effective management processes.

The process of identifying an adequate crowdsourcing platform to use is simple: set aside a quarter (roughly three months) to evaluate options. Set aside another quarter in the year to proceed with all of the logistics, a quick proof of concept, and set a date for implementation. Researching and implementing the platform does not include the pre-risk assessments and vulnerability analysis that should occur prior to expanding the enterprise security model. Asking the right questions of platform providers requires a neutral mindset. An application security engineer or general cybersecurity engineer has typically dealt with vendor comparisons. With that being said, there are several suggestions for process improvement, especially when dealing with platform evaluation:

*   **Ensure the platform is accredited by hackers as well as engineers:** avoid negative speculation from hackers who haven’t been rewarded for bugs to their satisfaction. Research can be conducted on most platforms and by gathering various opinions from engineers and hackers. Additionally, be open minded, as everyone is entitled to their own unique perspective.
*   **Without prejudgment, schedule meetings with sales representatives from multiple companies:** if you’re working within a strict budget, inform them.
*   **Pricing is nearly always an issue, keep in mind that every part of a platform and extended feature is going to accrue an additional cost:** while evaluating platforms, remember that managed triage services, on-demand penetration tests, and bug bounty payouts aren’t typically included in standard program deployment.
*   **Ask difficult questions, be sure to interject:** remember, if sales representatives have the chance, they will attempt to get through their entire presentation uninterrupted, glossing over the finer details. It’s the enterprise’s responsibility to evaluate the features being promised and consider what’s realistic.
*   **Don’t offload technical work on a sales representative:** it’s not their job to ensure that “x” feature will work with your enterprise model. Instead, formulate an exact question and ask to get in touch with a technical account manager to get a more granular understanding.

On top of the major tips previously mentioned, remember that engineers and management should be in control of the evaluation. Transparency with pricing and features from day one will allow for a more thorough negotiation process. Don’t be afraid to tell the vendors you are working with other vendors and looking for the most efficient spending plan. When vendors are uncontested, you are likely to pay far higher than being transparent in your comparison process.

Overall, any platform will have its advantages and disadvantages, but a good start will be to look for a crowdsourcing vendor that rewards security researchers and fairly mediates issues between programs and researchers. While it may seem advantageous to choose a platform that favors an enterprise’s decision on a vulnerability, it’s not. Be sure to be on the lookout for solutions that have a bad reputation with the bug bounty hunting community. If researchers avoid the platform, it will not be beneficial for you to use the platform. The last thing an enterprise should want is to receive a poor reputation among the information security community. Program mismanagement can start with a poor platform choice, and the best way to approach a vulnerability disclosure program is starting off with a leg up.

## 3.7 Platform Pricing and Services

As discussed in Section 3.5, program establishment starts with paying fees for the platform itself. While it is impossible to discuss the granularity of platform pricing, the typical scenario is one in which an enterprise is charged based on its size. A crowdsourcing platform will bridge the gap between security research management and responsible disclosure. A typical deployment involves no infrastructure. Therefore, associated costs will typically be calculated on a standard basis. Comparably, managed services will initiate recurring fees, and on-demand penetration testing services will require fixed-cost fees, depending on services rendered, and so on.

In addition to the recurring annual contracting fees, a program manager must consider the buffer room that must be allocated for a bounty pool. A bounty pool is an allocated amount of money that is committed to paying hackers. Think of it like a prepaid card. An engineer will validate a vulnerability and, if appropriate, triage and assess impact. If the program deems the submission valid, the engineer responsible for managing the vulnerabilities will award the security researcher money, which will be rewarded from the bounty pool.

It’s important to note that even though the bounty pool seems simple it usually has associated fees. For example, a platform provider might require that the enterprise pay an “x” percent surcharge to the crowdsourcing platform on top of any bounty. When establishing a bug bounty program, it’s important to account for any fees that might occur on top of bounties and any additional services.

## 3.8 Managed Services

Understanding the necessity for an initial period of managed services requires first knowing what managed services do. Every security research crowdsourcing platform is going to have a different model for the specifics of the services, but at a high level.

Managed services typically include the initial triage of any vulnerabilities that are reported, inviting hackers to the enterprise’s program, communicating recommendations and evaluating program analytics, and helping assist in collaboration between the enterprise and the security researcher. Enterprises that are on a budget may opt to avoid purchasing any form of advanced managed services (depending on the platform provider) even from the start, but it’s in the best interests of the engineers, or management establishing the program, to use all managed services functionality, at least for a little while. Over time, program managers can downgrade to a model that uses hand-holding techniques less.

Bug bounty programs are not overly complicated, yet many companies fail to effectively manage the workflow and processes that are involved in programs. Managed services can help warm a team up to the various program requirements and best practices before dumping engineers or management into the unknown. As another consideration, most managed service programs will validate vulnerabilities prior to passing them on to the enterprise, helping introduce engineers to new concepts and validation methodologies.

During the establishment of a program, there may be a point in time in which the option to add-on managed services is discussed. There may be a preliminary warm-up period where the platform provider includes these services for free, or it might be an accrued cost from the start, but keep in mind that advanced managed services don’t have to be purchased at all or maintained past a given contract period unless otherwise stated.

## 3.9 Opting Out of Managed Services

Based on experience, the best recommendation would be to never fully opt out of the advanced managed services, unless there’s a reason such as poor service or small value from additional managed services add-ons (and depending on the provider, it may not be possible). A reduction from fully managed services to something more partial such as baseline triaging services would be the wisest move with time.

Advanced managed services is a best practice to ensure that the program receives analytics and feedback to progress, which isn’t usually provided in a standard baseline model. Noting that it’s a best practice and not a requirement is an important difference because the enterprise setting up a program may be able to completely validate, triage, and remediate vulnerabilities without any third-party involvement. If the organization setting up the program has the capacity to reduce the provided options and move to a baseline level of managed services without negatively impacting reputation or tarnishing a security researcher’s work, by all means, use best judgment.

In addition, it’s not usually possible to fully opt out of managed services. If a program manager had the ability to do so, they could neglect a program.

## 3.10 On-demand Penetration Tests

Many security research crowdsourcing platforms offer on-demand penetration tests. The penetration tests offered by these platforms are similar to traditional testing methodology in the sense that there are typically findings that are presented and remediation methodology. The best way to think of crowdsourced penetration testers are as expert bug bounty hunters. The researchers assigned to the penetration test will likely find a decent amount of client and server side exploits.

There’s no question that one might wonder about the efficiency of purchasing an application penetration test. In terms of compliance, there isn’t adequate evidence to believe that purchasing a dedicated test is any more efficient than running a program. A bug bounty program is an ongoing incentive: the enterprise running this program is consistently being tested on. However, the program itself cannot fulfill the compliance requirements for penetration testing criteria as it’s impossible to have full oversight being tested by the researchers participating in your program. Instead, hire a third-party penetration testing company and put applications in scope for testing. An enterprise can bundle together the network and application assets to maximize the money spent on testing, especially if the budget is particularly tight.

Overall, an application penetration test offered through a crowdsourcing program isn’t necessarily required. As a note, if the enterprise has enough money to perform a wide array of testing, it wouldn’t hurt to purchase the services. Before the services are purchased, ensure that the bug bounty program is ready to be tested on. In order to determine readiness, the program should be actively receiving bugs for at least a year and have had some major vulnerabilities reported. It wouldn’t be recommended to start this testing until the program is major enough to timely resolve any reported bugs. If a junior program uses a penetration testing service as described, it could end up being a waste of money – especially if the software development lifecycle isn’t using the best possible application security processes. As described previously, if the objective is to establish a thorough and respectable program, it wouldn’t make much sense to throw an enterprise into an arena that the program isn’t currently prepared for.

# Part 3   
Program Setup

# 4   
Defining Program Scope and Bounties

## 4.1 What Is a Bounty?

Simply put, a bounty is a reward paid to a security researcher. Bounty programs establish a way for a researcher to disclose bugs of impact to organizations. The enterprise has the ability to define various reward tiers to encourage participation.

Bounties should never be viewed as paying for exploitation, but for adequate and detailed vulnerability research.

## 4.2 Understanding Scope

Scope can be a confusing topic for some engineers. Historically, scope has been a means of defining what researchers are allowed to target. Scope can be tricky in the sense that anything not defined as “out of scope” can be fair game to a researcher. When engineers imagine “fair game,” they may envision assets, yet, realistically it can also pertain to methodology used by security researchers. Imagine this: a researcher finds a program, and there’s nothing in the out-of-scope definitions that state brute force attacks (i.e. attempts to submit many passwords or passphrases in the hope of eventually guessing the correct combination) as being out of scope. A researcher now has unlimited time to run through enumerated usernames and test for account takeover. As a secondary consideration, they may negatively impact the application. The researcher spends a couple of days attempting “credential stuffing” against an application login portal and now gains unauthenticated access to an account. The enterprise must now pay this attacker for a high or critical payout depending on the program definitions. It’s qualified as a full account takeover.

A scenario such as the one provided above could have been completely avoided if the engineer setting up the program understood the applications, attack methodologies, and so on.

## 4.3 How to Create Scope

Many engineers approach scope with the idea of limiting the attack surface for a researcher. Limiting the attack surface for a researcher is absurd, and the complete reverse methodology that should be used for increasing the security of enterprise application development. Instead, a better approach is to start with a smaller amount of assets and work up to a larger attack surface when reports start to dwindle.

For example, compare two models of scope and notice subtle changes to the web testing portion of the scope.

### 4.3.1 Models

Model A (1st Month of Program Setup):

*In-Scope*

Web:

1.  [https://example.com/login](https://example.com/login)
2.  [https://example.com/policies](https://example.com/policies)
3.  [https://example.com/legal](https://example.com/legal)
4.  [https://dev.example.com/about-us](https://dev.example.com/about-us)
5.  [https://dev.example.com/login](https://dev.example.com/login)
6.  [https://dev.example.com/profile](https://dev.example.com/profile)
7.  [https://dev.example.com/customer/support-services](https://dev.example.com/customer/support-services)

Model B (6th Month of Program Setup):

*In-Scope*

Web:

1.  [https://example.com](https://example.com)\*
2.  [https://dev.example.com](https://dev.example.com)\*
3.  [https://staging.example.com/join](https://staging.example.com/join)
4.  [https://staging.example.com/about-us](https://staging.example.com/about-us)
5.  [https://testing.example.com](https://testing.example.com)

While comparing both models A and B, it’s easy to see that staging and testing were added to the web scope (subdomains), but why are fewer assets listed overall? Both the [example.com](http://example.com) and the [dev.example.com](http://dev.example.com) subdomains now have wildcards. It’s standard to eventually use wildcards where possible.

## 4.4 Understanding Wildcards

Wildcards are fairly simple to understand. They are a means of allowing for a wider attacker surface. A wildcard can help a program identify more vulnerabilities, and give a security researcher more flexibility to stick to an enterprise’s program and get to know it and want to test on the program. One of the biggest complaints that researchers will touch on is the lack of wildcards in a program. Some researchers will not participate in any programs that don’t use wildcards because they don’t have the breadth that a researcher is looking for.

When thinking about wildcards, there are several methodologies:

*   Subdomain: \*.example.com
*   Domain: [example.com/](http://example.com)\*
*   Specific Domain Path: [example.com/login/](http://example.com/login/)\*
*   Subdomain Path: [dev.example.com/](http://dev.example.com/)\*

### 4.4.1 Subdomain

Simply, a program that sets a wildcard domain is using the most permissive scenario possible. Imagine, for instance, that [example.com](http://example.com) has subdomains such as [mail.example.com](http://mail.example.com), [app.example.com](http://app.example.com), [dev.example.com](http://dev.example.com), etc.; a security researcher can test any of these subdomains, on any URL path. An important consideration to be made before allowing a wildcard in the subdomain slot of a domain is whether the engineers who are managing the program have done their due diligence and evaluated all of the subdomains or not. It would be a poor decision to allow a subdomain wildcard if the full attack surface weren’t evaluated.

Does this example seem unrealistic? It can and has happened. An engineer has to ensure that the subdomains in scope are being evaluated just as the main domain of the web application is. There are a plethora of attacks that can impact subdomain and turn critical if unchecked.

### 4.4.2 Domain

Wildcard use on domains is typically the in-between scope option for bug bounty programs. A researcher who tests against a basic domain wildcard can perform research on the entire domain, but any identified subdomains would not be in scope unless otherwise stated. As explained earlier, it would not be advisable to use a domain or subdomain wildcard without knowing all paths or assets that could be tested.

### 4.4.3 Specific Domain Path or Specific Subdomain Path

Unless there’s a wide range of URLs involved, a specific path asset set as in scope typically maintains the least permissive testing posture. Programs that are just being established can get the feel for bug bounty programs by using this model and setting certain domain paths as in scope. The more critical paths, such as /login or/checkout, are a necessity to test against because malicious hackers will attempt to exploit any low-hanging fruit that may be exposed on these paths.

## 4.5 Determining Asset Allocation

Enterprise bug bounty programs will typically have a vastly different setup, depending on the specific field that the company actively participates in. For example, a medical company may be concerned with protecting patient records, and may use a model that allows doctors or nurses to log in to a web portal that allows them to access patient records. What company in its right mind would allow such a critical asset to be exposed to the public? Well, the reality is, if it’s absolutely necessary to expose critical assets to the public, they need to be checked. Paying a couple thousand dollars to a security researcher is nowhere near the level of pain that will occur if vital information were to leak to the public.

To a medical organization, protecting patient records is vital. Just ask Alberto Hill, who on a dark day performed security research, logging into a public facing web portal with the username “admin” and the password “admin.” All legal issues aside, Alberto had access to financial records, medical records, medication information, and so on. Alberto’s story can teach engineers that putting the most critical assets in scope for a bug bounty program isn’t optional: it’s a requirement. If the engineers managing the program are not ready to allow researchers to test these assets, the first part of the journey is understood: the engineers know that it’s important to assess these assets and should adequately do so, in some form.

One size can never fit all for an organization identifying assets. As another example, consider an ecommerce website that focuses on selling digital assets. Some of the biggest risks that a digital sales website could face are account takeover opportunities, stealing assets through business logic, or insecure web application code, and so on. Depending on the model of the enterprise, there may be less of a risk for exposed customer data, and more of a risk of theft or manipulation. The best possible thing an engineer can do while setting up a program is to consider the logic of their critical company assets, test them, and put parts or entire domains, subdomains, etc. in scope.

Web applications are just the tip of the iceberg for bug bounty programs. Crowdsourcing platforms have been known to allow enterprises to include mobile applications and public-facing network assets in their program testing scope. Some of the bigger companies have even made the news for coordinating with their top hackers and sending the latest hardware or tech for testing purposes, allowing researchers to keep the hardware when testing is complete.

Overall, whoever is tasked with establishing the bug bounty program will have to consider what assets to put into scope. Only the engineers establishing the program can make this determination. The recommended release order would depend on whether the company manufactured physical goods. For example, if the company in question were an Internet service provider, it would make sense to allow security researchers to test their own home routers if the company produced those routers. Obviously, the stipulation would be that a researcher refrained from damaging the hardware, or less they will have to pay for it.

An application security engineer running a program, for instance, can collaborate with network security, infrastructure, mobile teams, and so on, to determine important assets to test. The best way to view asset allocation is with the mindset that one can always expand, but it’s harder to retract. If an enterprise puts all wildcards for subdomains and every main domain in scope and has 100 vulnerabilities reported within the first 24 hours, these assets can be pulled out of scope. But the researcher’s findings will stand and have to be addressed according to the service level agreement (SLA) guidelines that are defined in the program. An SLA is a commitment between a service provider and a client. In this instance, the bug bounty program sets an SLA and the researchers agree to their promise to address or patch vulnerabilities in the appropriate timeframe.

## 4.6 Asset Risk

Outside of determining what assets are appropriate for the scope of the program, it’s essential to understand production impact. While it’s typically a good idea to put critical assets in scope, bug bounty program managers must ask: “Why is this critical?” If it’s critical because of sensitive information, that’s one scenario. However, if it’s critical because testing can cause major impact or financial loss, it should not be put into the scope unless the program is certain that it will not cause major issues.

While it’s difficult to evaluate every possible scenario in which there can be impact for production components, engineers must try to identify any conflicts where possible. In the event that impact does occur, communicate the notion quickly to software engineers and be transparent about the situation. Hiding facts will not help remediate any issues that may occur, and taking ownership is the best possible solution.

## 4.7 Understanding Out of Scope

While it may seem ridiculous to describe the meaning of “out of scope,” there’s more to the equation than just defining assets that are not “in scope.” It can take a careful hand to appropriately decide what assets shouldn’t be tested on, and out of scope represents more than just what *shouldn’t* be tested on. Initiating the most thorough program requires knowing the type of attacks that are out there and creating a scope that prevents disruption.

First and foremost, as a baseline, it’s important to assign testing environments and assets that you don’t want a research to test to the out-of-scope section. In most instances forgetting to include certain assets in your out-of-scope section isn’t detrimental. Security researchers should know to avoid testing on anything that isn’t defined as “in scope,” and they undoubtedly want to get paid. Don’t inadvertently assume that all security researchers will respect the rules of the bug bounty program. In many instances, security researchers will test on whatever they feel like in hopes they can abuse it to prove that it’s in scope. Additionally, researchers may ignore specific prohibited testing criteria by proxy-chaining (the act of changing IP address with each new request), and engineers managing the bug bounty program must keep this in mind.

When considering what to prohibit, it’s recommended to put the majority of the most common disruptive techniques in the out-of-scope section; this is a formality. Prohibiting disruptive behavior is a formality because, as stated, it will not stop anyone from performing those actions. As the program manager, don’t punish security researchers for their testing methodologies. At the end of the day if there isn’t disruption it’s not problematic. It’s the old adage: don’t make mountains out of molehills.

As a general rule of thumb, here’s a pocket guide to some of the major vulnerabilities and testing methodology that should be included in the out-of-scope section, along with the “why.”

## 4.8 Vulnerability Types

### 4.8.1 Denial of Service (DOS) or Distributed Denial of Service (DDoS) Attacks

In short, DOS or DDoS attacks can cause production impact and take servers down that host major services. Even if the security researcher doesn’t test it, but presents possible DOS or DDoS attacks on “x” server or service, there are minimal cases in which this finding is worth anything.

### 4.8.2 Social Engineering Attacks

Many subtechniques within the category of social engineering are exceedingly effective. However, save the testing of these techniques for hired penetration testers. It’s generally not a good idea to include social engineering attacks as in scope, because this could cause potential legal issues if an employee or customer ends up having any sensitive data leaked.

In addition to legal liability, social engineering attacks can be disruptive to enterprise workflow. A constant barrage of phishing emails via contact forms, emails, phone calls (or whatever the means may be) can result in employee complaints or cause monetary loss depending on the specific instance. It’s important to be adamant about excluding social engineering attacks due to the possibility of disruption.

### 4.8.3 Brute Force or Rate Limiting

Attacks that include attempting to break into user accounts (brute force) can possibly cause issues as well. Brute force attacks can disrupt the application security workflow and also cause legal issues if user accounts are taken over and abused in the security research “proof of concept” process. In addition to legal issues, brute force attacks can negatively affect production environments, and in the instance it goes down, the application security team may be responsible for not annotating this as out of scope.

Rate limiting should also be included as out of scope for the same reasons. Security researchers may disrupt production environments and cause impact or other related security issues. In addition, it’s considerably low impact.

### 4.8.4 Account and Email Enumeration

Building a list of usernames or emails that exist on the application typically has no impact on the enterprise. In this day and age of technology, it’s become exceedingly easy to gather wordlists of usernames and emails to use for brute force attacks.

### 4.8.5 Self-XSS

Being able to produce an XSS (cross-site scripting) alert that can only be seen by the user themselves and not anyone else, including staff, is not generally considered a vulnerability. Self-XSS has no considerable impact. However, program managers must understand the difference between all of the various XSS types to ensure that they understand the security researcher.

### 4.8.6 Clickjacking

Clickjacking is the practice of manipulating a user’s activity by concealing hyperlinks beneath legitimate clickable content, thereby causing the user to perform actions of which they are unaware. Clickjacking is also known as a “UI redress attack”. The vulnerability of clickjacking is usually out of scope because it relies on social engineering heavily. It can be used to exploit users, but generally not in the scope of vulnerabilities that a program should/would accept.

### 4.8.7 Miscellaneous

Realistically, there are far too many attacks that can be considered nonpayable. Program managers should take the time to review all of the various attack methods and look at other attacks that are out of scope in similar bug bounty programs to determine why allowing that type of attack may end up being problematic. Keep in mind that expansions are continuous. Program managers will find that certain types of attacks may be too disruptive to their workflow or considerably low impact and not worth evaluating. Assess the out-of-scope attack vector portion of programs as needed, and be sure to inform hackers of any major modifications.

## 4.9 When Is an Asset Really Out of Scope?

Overall, the objective of out-of-scope reporting is never to discourage a security researcher from reporting, but to ensure that baseline restrictions are placed to prevent legal or financial impact. With that being considered, ideally program managers should be fair in the evaluation of vulnerabilities that are in and out of scope.

A security researcher pulls up a list subdomains for the enterprise and finds a lot of assets, some of which are explicitly stated as out of scope. Researchers are curious, be it by nature or acquired in their lives. They want to know how components work. In this specific scenario, assume that it’s well known that this asset is out of scope (defined in the out-of-scope section of the enterprise bug bounty program): should it be tested on?

If the answer that came to mind was *no*, it can be simultaneously the right and wrong answer. To demonstrate scenarios that bug bounty program managers may run into, consider an example of a (P1) – critical vulnerability – and a (P4) – low vulnerability.

Now, review the next scenario, keeping the P1 example in mind.

## 4.10 The House Wins – Or Does It?

The ultimate decision of many bug bounty programs that currently operate typically resides with not paying the security researcher if it’s out of scope. Some that have been overheard reside within the school of thought of “We don’t want to encourage our researchers to hack out-of-scope assets just to get a bounty” or “If we pay a researcher for one out-of-scope bounty, we will have to pay them for every out-of-scope bounty.”

A major issue with adverse thinking toward out-of-scope research is that it can lead to key research being overlooked. When determining whether paying for a reported vulnerability appears to be the right move, ask the following questions:

1.  What is the level of impact of this vulnerability? Could it lead to extremely sensitive information leakage?
2.  If no sensitive information is leaked, could the vulnerability severely damage company reputation?
3.  Do we value the researcher and want to reward them?

One size does not fit all in terms of paying a security researcher. Remember, when managing a program, the rules are made by the program manager. While transparency with leadership must always be exercised, caring is the key to developing a strong and loyal research platform and building brand reputation among the cybersecurity community. Let’s take our earlier examples of the critical and low vulnerabilities and perform a dry run of answering the above questions.

In this admin takeover example, it’s easily determined that a lot of damage could occur. Company information could be sold, or there could be direct impact to business continuity, creating a loss in revenue. With that being said, the right thing to do would be to pay the security researcher. In a circumstance such as the one described, there would be far more loss in a breach scenario than there would ever be if the researcher were adequately paid. Programs should consider setting a moral example and paying for the vulnerability findings.

When a lower-end vulnerability is reported out of scope, it’s not technically immoral to refuse to reward hackers for their findings. Expectations that were set out early in the process are fair game. However, consider paying researchers a mild bonus or sending a t-shirt. A little bit of gratitude, especially for someone who went out of their way to help, goes a long way.

## 4.11 Fair Judgment on Bounties

It’s easy to stray from the moral path as a program manager. At times, it can seem enticing to claim plausible deniability for an issue. If using a managed program, the triagers only know your environment as well as they possibly can from an external perspective. Bug bounty programs are only as efficient as the engineers and managers that run the program. Similarly, programs can only be as honest as the parties responsible for validating vulnerabilities.

There are many blind exploitation paths that can easily be denied, or are questionable from the perspective of an attacker, and it takes adequate communication between the researcher and engineer to confirm the existence of some vulnerabilities.

If a researcher were to stumble across a GitHub repository for an organization and find SQL credentials, it would be an extremely valuable finding, especially if they could log in. In the instance that the login is restricted to the internal network, they may not have a way to immediately control the server. At times, it may take internal verification. Verification may fall out of the line of sight of the triage team and the researcher.

Observe the following interaction between a triage team, program, and hacker.

## 4.12 Post-mortem

When reviewing the reporting process, it’s seemingly harmless, right? The researcher submits what they believe to be a vulnerability, and the enterprise confirms that the credentials are no longer in use. What if they *were* in use? Would the triagers or security researcher know the difference? The unfortunate answer is a simple, *no*. Unless the researcher has adequate proof that they were able to interact with the server, not much can be done at this point. Nothing is stopping the application security team from inquiring with the team maintaining the credentials, who then decide to rotate the credentials and pretend that the vulnerability never existed.

The situation in which a program steals vulnerability findings from a security researcher isn’t unrealistic. In fact, many security researchers can attest to the theft of such research. The issue with a bug bounty program versus a security researcher is that of monetary and legal binding. A large enterprise typically has lawyers on hand who can contribute toward the cause in the event of legal fallout. In addition, programs use blanket nondisclosure agreements (NDAs) to bind researchers into silence. While the intention of most programs isn’t to use an NDA as a means of trapping researchers into legal battles and stealing research, *it has happened*. Determining fault is yet another tricky situation. The program manager responding to the incident may not have checked to see if the credentials were working, or may not have been able to because of enterprise restrictions. Communication is essential to the mitigation of further issues during these circumstances.

## 4.13 Awareness and Reputational Damage

The intent of highlighting the issues that some security researchers will face isn’t to shame programs. As an engineer or manager working on or running a program the takeaway is to realize that technical ineptitude or immoral behavior isn’t excusable. Professionals need to do their part to contribute to the greater good, and in the scenarios in which vulnerability research is stolen, or payment is blatantly refused, it can directly impact the enterprise.

Social media is the new norm. Most businesses maintain social media pages, and it’s not uncommon to witness upper management frequently using popular social media websites. An unintended consequence of running a bug bounty program poorly is escalation from security researchers on social media websites. When a researcher does not feel heard, or they determine that their research is being stolen, don’t be surprised to see them take to social media with their concerns. An NDA via participating in a bug bounty platform seems like an effective countermeasure. However, it’s rarely the be all and end all from a researcher. Many people have no issue or second thought about getting their bug hunting profile banned if it means that they have the ability to possibly hold program managers to account.

Bug bounty hunting is a niche trade. There are not millions of bug bounty hunters getting paid for their research. With that being said, the community is small enough to develop an internal burn list of programs that have been notably sketchy in their communications or resolution. Ask any seasoned bug bounty hunter which programs should be avoided and they will more than likely have a list of programs to avoid like the plague. Researchers aren’t always being wronged. The unfortunate truth resides in the fact that sometimes the captain goes down with the ship – or in other words, even if a security researcher is in the wrong, they may possibly fight the program, and cause great reputational harm.

## 4.14 Putting It All Together

The moral of the story: running a program requires patience, and honesty. At times, the level of truthfulness that is required is deafening, and can feel self-defeating. No one program manager or engineer working on a program has all of the answers. It’s not unreasonable to assume that a situation may occur in which a vulnerability is difficult to understand, or seems downright impossible to grasp. In situations where comprehension of a vulnerability is lacking, reach out to other individuals in the application security space and ask for guidance.

It does not hurt to get a second opinion on a report, and individuals working in the cybersecurity space need to know when it’s appropriate to do so. Everyone wants to be a superstar, but being an application security expert requires knowing when to ask for help and when to work through the issue alone. Researchers are not obligated to work with enterprises. A lot of the vulnerabilities identified through bug bounty programs can be abused for financial exploitation far past any monetary amount that the company would have paid for the vulnerability.

## 4.15 Bug Bounty Payments

While there are many ways to determine responsible payout amounts, the realism lies with the program type, enterprise budget, and visibility of the program. Payments can never be a one-size-fits-all scenario, so it’s important to keep that in mind when determining the right payment table. There are several questions and steps that can be taken to assist in the determination process and make it enjoyable for both the program and security researcher.

### 4.15.1 Determining Payments

First and foremost, before anything pertaining to payments is created, know this: can a monetary amount be assigned to the value of vulnerability mitigation? Running a bug bounty program means that a monetary value *has* to be assigned, or at least some form of compensation. However, remember that a breach can be far more painful and costly than any form of payment that would be given to a security researcher. In the instance where a program pays $10,000 for a critical vulnerability, that could be a drop in the bucket compared to millions of dollars that could be paid in the instance of threat actor exploitation.

With payment amounts in mind, there are two options: set values or set ranges. While setting specific reward values may seem like a great option, it limits the scope and ability to determine granularity, especially in the instance that a vulnerability is riding a fine line between a high and a critical rating, or a medium and a low rating. Program reward ranges per vulnerability criticality is an incredibly useful option for tricky situations.

A security researcher discovers a stored XSS vulnerability. Unfortunately, it’s a payload that can only be stored in a part of the application that is exceedingly limited in scope. Maybe it requires an expensive subscription in which the realism of replicating the attack against another user becomes fairly unlikely. Nonetheless, there’s a potential in which this attack may be considered “low paying,” or not qualified for payment at all. Now, imagine that the researcher reports it, and during the reporting process the engineer triaging the vulnerability triggers the stored-XSS vulnerability, and it results in an authentication token for a separate internal user management platform being acquired. A scenario described as such isn’t unlikely, and has happened to other companies in the past.

Bug bounty program managers have now successfully evaluated the bug, and it appears to be a self-XSS vulnerability. The engineer managing the program marks this vulnerability as out of scope. After the report is marked as disqualifying, the researcher takes note of the logging mechanism attached to the domain that was used in their XSS payload, and notices the token. The researcher has now successfully obtained access to the enterprise user management portal. Inside of the company portal, there are thousands of pieces of personally identifiable information and unlimited access to perform account actions on other users.

In a scenario described as the one above, the security researcher has taken an action that may have been considered out of scope or a low-payable action, and has completely escalated it to a critical vulnerability. As a program manager, it has to be decided how to pay the researcher – if at all. However, the situation has escalated into a bit of a predicament. Should the program pay the researcher?

Earlier in the chapter, it is stated that critical research is valuable. However, the actions were resultant of a specific scenario that may be considered out of scope from several different angles (social engineering, nearly self-XSS). When a situation occurs in which you want to pay a researcher, but maybe not as much, a rewards range can make the difference.

The difference between the values and the range make quite the impact (see [Table 4.1](#c04.xhtml#c4-tbl-0001)). In the described situation in which a researcher performs the stored XSS abuse (which may be considered somewhat out of scope), a program that wants to compensate the researcher fairly might struggle. They most certainly don’t want to pay them $5000 but, on the other hand, paying $3000 isn’t quite on the cards, based on the out-of-scope effort and the level of complexity required in exploitation.

[**Table 4.1**](#c04.xhtml#rc4-tbl-0001) Setting Bug Bounty Reward Values and Ranges.

 
| **Set Reward Values**  |
| --- |
| Critical || High || Medium || Low |
| $5000 || $3000 || $1000 || $200 |
| **Set Reward Values** |
| Critical || High || Medium || Low |
| $3500–$5000 || $1500–$3000 || $400–$1000 || $50–$200 |

A reward range makes more sense. The program knows that they don’t want to pay the researcher between $3500 and $5000, and $3000 was undoubtedly a little too steep for the specific scenario. Luckily, the range varies between $1500 and $3000. The program then decides to pay the researcher $1500 dollars. Reward ranges give an enterprise breathing room when more complicated vulnerability submission events occur. Instead of paying a hefty $3000 for an event that was out of scope, a program can now choose to pay $1500 – rewarding the researcher for their efforts (without discounting the research) and maintaining a positive affirmation for researchers that stay in scope by giving them the potential to earn $3000.

### 4.15.2 Bonus Payments

The burning question: “When should a bonus payment be used?”

A bonus payment should be used in instances where there’s a unique circumstance. For example, if a researcher were to find a duplicate vulnerability but write a highly extensive report detailing the vulnerability in length and provide new evidence, consider a bonus payment. Bonus payments don’t have to be excessive or used frequently, but they can be a way to say thanks to an awesome researcher.

An alternate use case for bonus payments is when exploitation bypasses the normal means of criticality, and the bug bounty program wants to be fair. Imagine a program in which the top reward (critical) was set at $4500. In an instance where a researcher was able to pivot from the web application to the backend, and from the backend server to the domain controller and obtain sensitive information, would $4500 be a fair reward? Bonus payments can help extend enterprise reward capacity without requiring an extremely large reward range to be set by the program manager. There’s not a set answer when it comes to awarding researchers bonus payments. Use the best possible discretion and be willing to reward researchers for creative instances of vulnerability exploitation.

### 4.15.3 Nonmonetary Rewards

An aspect that’s frequently overlooked in the payment process is “swag.” A lot of programs can benefit by using swag as a motivating incentive. It shouldn’t come as a surprise that many security researchers like to hack because it’s fun. In fact, most CVEs (common vulnerabilities and exposures) are a result of security researchers putting in their hard-earned time to submit research for free. Swag as it applies to bug bounty programs should be something unique that cannot be bought from the enterprise apparel shop with money – think “feat of strength” or “unique.”

There are many instances in which swag can be used as a way to bolster program strength, or to encourage security researchers to participate. Some of the more commonly used methods are:

1.  Researcher finds an exceedingly critical bug.
2.  Researchers who frequently participate in or have contributed a lot of research to a program.
3.  As an alternate payment for vulnerabilities that are rated as “low.”
4.  As an alternate payment for vulnerabilities that are rated as “informational” but provide important perspectives that may not have been known otherwise.
5.  Used as an incentive to hack during a certain timeframe or for a specific vulnerability type (“Find a way to buy items from our store for free and we will reward researchers with payment + special swag”).

At times, swag is avoided because enterprises worry about budgetary restrictions. After all, many program managers may not want to have to buy 50 or more t-shirts or hoodies as a minimum print requirement. Therefore, a program manager should consider a print-on-demand service. A quick search will bring up many options for print on demand. It’s a service that boasts flexibility to be able to fully customize products with a design provided by the user, and there’s typically no minimum order fulfillment requirements. Creativity integrated in a modest way with bug bounty programs can help the program stand out. Security researchers will likely post about the uniqueness and creativity of the program online (plus it’s free marketing).

The one disclaimer with swag is to minimize using it in instances where the program being managed is in the private stage, or has no intentions of being in the public space. Security researchers are relentless in their desires. They may hack the company solely for obtaining a piece of apparel or an item, and this could be problematic if the program is private, causing resentment. As ridiculous as that sounds, considering all of the possibilities of a researcher’s mindset contributes directly to the success of a program. Ideally, if a program manager runs a private program and wants to give out swag, kindly instruct the researcher not to post pictures of the swag on social media. (But please consider if the researcher decides to ignore the request to perform automated scans anyway, as this may occur.)

# 5   
Understanding Safe Harbor and Service Level Agreements

## 5.1 What Is “Safe Harbor”?

Safe harbor is the means of a bug bounty program providing affirmation to a researcher whom they will not seek legal action against the researcher if the researcher is acting in good faith within the constraints of the program scope and rules.

### 5.1.1 The Reality of Safe Harbor

Program managers may feel a bit out of place while writing a safe harbor agreement. Safe harbors contain legal jargon and can seem intimidating, especially when it’s the program’s responsibility to at least work up a simple safe harbor clause. It’s important to note that this isn’t always the case. Most modern-day bug bounty platforms allow a program manager to use a templated safe harbor agreement, and in all actuality that’s all a safe harbor is: a templated nonaction clause.

### 5.1.2 Fear and Reluctance

Most security researchers are willing to poke around an enterprise’s assets, regardless of whether the asset is in scope or not (or if they even have a program). Nonetheless, that cannot be said of every researcher. Security researchers have different flavors of hacking, and for some that means acting only in the most legitimate sense of ethics. Program managers need to heed the safe harbor recommendation. Not every bug bounty program has a full safe harbor plan, and in many cases there isn’t one at all.

It’s not recommended to operate a bug bounty program without a safe harbor plan.A safe harbor can actually work in the benefit of a program and researcher. When security researchers want to be protected, they will look for the safe harbor clause, and synonymously programs can use it to protect themselves in a court of law if research goes awry.

### 5.1.3 Writing Safe Harbor Agreements

First and foremost, it may be unnecessary to write a handcrafted safe harbor clause. As stated previously, many bug bounty platforms give the program manager an option to fully integrate a templated safe harbor agreement that would hold up in a court of law. In the instance a safe harbor needs to be written, it’s likely because the enterprise is running its own program without using a bug bounty platform.

Here are some tips for writing an effective safe harbor agreement:

*   Let the researcher know they are expected to respect any hacking laws that may be relevant in their country or region.
*   Ensure that they understand the research must be conducted in good faith and that, as long as it’s done in such manner, they are exempt from legal action and free to conduct research.
*   Repeat that the enterprise will not take any negative legal action against them if assets that are considered in scope are exploited.
*   Communicate that accidental violations of the policy which were not intended to be malicious are forgiven.
*   Provide means of contact in the event that the researcher has any questions about the safe harbor agreement.

Generally speaking, the above safe harbor agreement represents a good start – although, again, it’s recommended that the program managers use anything templated by bug bounty platforms or consult with lawyers when drawing up custom safe harbor agreements.

## 5.2 Retaliation against a Rogue Researcher (Cybercriminal or Threat/Bad Actor)

It’s not always easy to make a determination of criminal activity versus criminal activity. In a sense, exploitation that may have sounded all of the alarms in the past can turn into a daily, weekly, or monthly occurrence. Before starting a program, knowing what your usual attack patterns look like is essential to be able to separate legitimate individuals from malicious ones. Typically, attack patterns can be analyzed via SIEM (security information and event management) logs or the web application security firewall, and hopefully at this point a program has not been established without these key tools. Identifying legitimate attacks versus pseudo-attacks becomes second nature after working on a program for a little bit of time – but deciding when to prosecute is a different story.

The unfortunate part of working in the cybersecurity field is that we may not necessarily maintain the ability to prosecute anyone who’s deemed a threat actor. Getting legal assistance depends on the structure of the organization and the type of attack that has occurred. Every situation may vary, and it will be up to the program managers to attempt to figure out the behavior patterns of a threat actor.

For example, a program manager may have had a negative communication with a researcher pertaining to a vulnerability that was considered social engineering, and therefore out of scope. If the researcher decides they are going to turn into a threat actor, all cards are up in the air. The beauty of a bug bounty program is that a situation like this provides a good paper trail of evidence in the event that this actor decides they want to go rogue. However, in a situation where the vulnerability was leaked on the dark web or it was sourced through someone else, it may be harder to determine the course of action.

Generally speaking, one of the best things that can be done when the program is feeling threatened by the research is to gather logistical evidence that the researcher has gone rogue with their vulnerability. This may include logs, screenshots, the report from the bug bounty platform, and proof of exploitation. A transparent chain of custody may help expedite the legal process to legal and hopefully bring any threats to an actionable state. However, realize that, as a program manager, you should be vigilant but not looking to punish researchers. Exercise caution, but don’t look for ways to punish legitimate researchers. One wrong move in which a security researcher is confused as a threat actor could ruin company reputation.

Another risk may be the possibility of the researcher leaking the vulnerability through social media or other public channels. In an instance like this, a program manager should proceed with caution to avoid a witch hunt. A researcher may not always be in the right, and even in an instance of a legitimate vulnerability, community retaliation can be deadly and attempts to mask the vulnerability can result in the Streisand effect. (The Streisand effect is a social phenomenon that occurs when an attempt to hide, remove, or censor information has the unintended consequence of further publicizing that information.) Nonetheless, use the tools that are adequately provided from the enterprise. Consultation with the legal team can help prevent a minor mishap from escalating into something that is much more serious. Initiating conversations with the legal team should always be used as an absolute last resort. Even if the vulnerability did leak on social media, a program manager must be willing to accept that these types of events happen. Program managers should not default to a thought process of assuming that the hacker is malicious, but always try to diffuse and understand the hacker. Is the hacker leaking the vulnerability on social media purely because they believe they are not getting a fair or swift response? Is the program’s communication good, but the hacker wants an absurd amount of money? Be fair. When a program manager puts themselves in a hacker’s shoes, it’s easier to have better interactions – even if they seem like a threat actor at first.

It may not always be possible to prevent exploitation, and in a carefully planned scenario in which the researcher was not satisfied with the outcome, it can prove quite deadly. Therefore, it’s advisable to maintain good communication and keep adequate documentation of reported vulnerabilities and pertinent information.

## 5.3 Service Level Agreements (SLAs)

A service level agreement, or SLA, is the enterprise’s promise to a researcher to respond to or to fix the reported vulnerability in an adequate amount of time. Private bug bounty programs can benefit from providing both report triage times and vulnerability patching times. When a program grows, times may need to be shifted, or in specific scenarios pulled out altogether. One solid affirmation that can be made about the triage or resolution process: no matter whether times are defined or not, it’s 100% safe to assume that at some given point a researcher is going to ask either when their vulnerability is going to be looked at or when a triaged vulnerability will be fixed.

How does one accurately build a model for resolution or triage times? Most of the crowdsourcing platforms will have recommended best practices outlined for adequate triage process, especially if the platform is going to be providing managed services. However, in the event that the enterprise does not choose to go with a managed service model or avoids using a crowdsourced solution altogether, all of the possible scenarios should be known.

It’s difficult to determine what model will be best for a given enterprise. Consider the following:

*   Is the program private or public? If it’s public, set realistic expectations. Can every medium vulnerability be resolved by the enterprise in seven days or less?
*   How well do the software engineers know how to patch bugs? It’s no surprise that bugs are going to have to be fixed by these engineers. If they don’t understand secure coding models, it’s impossible to provide adequate resolution timeframes.
*   Have statistics for the program been analyzed? As stated earlier in the book, launching a public program from the jump typically isn’t an effective way to evaluate the necessary adjustments and build a decent program. Although it’s not impossible, it’s not recommended. If a program manager starts with a private program, it’s easier to get accustomed to the workflow and determine SLA estimates. Security has never been a race – it’s a marathon.

Although there are several ways to line up SLA agreements, here are some examples to assist in the brainstorming process.

### 5.3.1 Resolution Times

Misconceptions exist about bug bounty program resolution times. A lot of security researchers believe that missing a resolution time represents a disastrous program, and it’s up to program managers to fix these misconceptions. Defining adequate time ranges that the program knows engineering teams can hold themselves accountable to in regards to vulnerability resolution is an important part of program management. By creating such resolution ranges, program managers have more flexibility to be transparent with researchers.

As an additional note, most bug bounty platforms auto-populate average resolution times, issues resolved, and so on. Most researchers can deduce the level of effort and responsibility exercised by the program from these statistics. However, providing a table helps a researcher compare averages against SLA and, if done properly, it can inspire more participation in a program (see [Table 5.1](#c05.xhtml#c5-tbl-0001)).

[**Table 5.1**](#c05.xhtml#rc5-tbl-0001) Resolution Times for Identified Vulnerabilities.

| **Vulnerability Rating** || **Resolution Time** |
| --- | --- |
| Critical || 2–7 days |
| --- | --- |
| High || 7–14 days |
| Medium || 14–30 days |
| Low || Best effort |
| Informational || N/A |

Defining an SLA directly in a program is best done when the enterprise can properly establish it without guesswork. The possibility of a bug falling out of the team’s purview could happen, and missing an SLA can hurt a program’s reputation, but it shouldn’t be a discouraging factor for program managers.

### 5.3.2 Triage Times

Triage times are different in the sense that most bug bounty platforms can manage them on behalf of the researcher if the program decides to go with a managed service model. Nonetheless, if a standalone program is established or an enterprise has to establish its own resolution criteria, an example of possible triage times is displayed in [Table 5.2](#c05.xhtml#c5-tbl-0002). Triage doesn’t typically require a wide range, unless the bug bounty program is exceedingly large. Validating vulnerabilities doesn’t typically take that long. The most difficult portion of the process is the resolution as it requires multitenant collaboration.

[**Table 5.2**](#c05.xhtml#rc5-tbl-0002) Triage Times for Identified Vulnerabilities.

| **Vulnerability Rating** || **Resolution Time** |
| --- | --- |
| Critical || 2 days |
| --- | --- |
| High || 5 days |
| Medium || 7 days |
| Low || 14 days |
| Informational || N/A |

The time ranges of all these processes should be adjusted according to program need.

# 6   
Program Configuration

## 6.1 Understanding Options

The time has finally come to configure a program. This chapter focuses on all of the various options available. Realistically, a step-by-step setup process is less likely to be as useful as a chapter that describes all of the available options. To best configure a program for the enterprise environment, knowing all of the various techniques available will make the bug bounty program far more successful. A lot of engineers setting up programs stray from the options that are within easy reach. Specifically, the objective of this chapter is not to focus on one crowdsourcing platform, but instead to evaluate the options to adequately prepare program managers for a more successful setup. Nonetheless, the various options between Bugcrowd and HackerOne will be presented.

## 6.2 Bugcrowd

### 6.2.1 Creating the Program

When first signing up on Bugcrowd’s platform, the program manager has the option to choose the program or service they want to use. For our example, we will be choosing between vulnerability disclosure and bug bounty programs. First, the program manager will click on the blue “Start now” button which pulls up the list of the given options.

1.  Click on “Start now” ([Figure 6.1](#c06.xhtml#c6-fig-0001))
    
    ![Figure 6.1 Bugcrowd “Start now” button.](images/c06f001.png)
    
    [**Figure 6.1**](#c06.xhtml#rc6-fig-0001) Bugcrowd “Start now” button.
    
2.  Choose “Bug Bounty Program” by clicking the “Start now” button ([Figure 6.2](#c06.xhtml#c6-fig-0002)).
    
    ![Figure 6.2 Bugcrowd: selection “Bug Bounty Program”.](images/c06f002.png)
    
    [**Figure 6.2**](#c06.xhtml#rc6-fig-0002) Bugcrowd: selection “Bug Bounty Program”.
    
3.  Once the start button is clicked, a basic program configuration wizard will populate. The details that are defined can always be changed later, so do not worry too much about getting everything right.
4.  When the program wizard comes up, it will show all of the various steps. In total, there are 9. Step 1 focuses on naming the program. The program name should be the name of the company that the program manager will be in charge of ([Figure 6.3](#c06.xhtml#c6-fig-0003)).
    
    ![Figure 6.3 Selecting the program name on Bugcrowd.](images/c06f003.png)
    
    [**Figure 6.3**](#c06.xhtml#rc6-fig-0003) Selecting the program name on Bugcrowd.
    
5.  Next, targets, or “assets,” will be set for testing. Again, it is OK if only limited assets are added. At this point, it’s not necessary to add every asset ([Figure 6.4](#c06.xhtml#c6-fig-0004)).
    
    ![Figure 6.4 Adding targets to test on Bugcrowd.](images/c06f004.png)
    
    [**Figure 6.4**](#c06.xhtml#rc6-fig-0004) Adding targets to test on Bugcrowd.
    
    Clicking the “Add target” button will bring up the dialog that allows a wide array of asset selections.
    
6.  Now, targets can be added and options can be selected from the dropdown ([Figure 6.5](#c06.xhtml#c6-fig-0005)). The name represents what you would like to call the asset, keeping in mind that the researcher will see this. Tags can now be selected. Utilizing tagging is essential because it gives the security researcher the best chance of having the correct expertise for conducting research. Next, the URL/location defines where you should expect the researcher to begin testing. Finally, the category helps you define what type of asset it is. Many researchers will look at the category right away and determine if it’s the right type of research for them. Be sure to make an adequate effort to label all assets correctly; there’s no use in rushing the assets. Click “Add,” which will then populate the target on the list. Adding as many as necessary. Click the “Next step” button and proceed.
    
    ![Figure 6.5 Adding a target to Bugcrowd.](images/c06f005.png)
    
    [**Figure 6.5**](#c06.xhtml#rc6-fig-0005) Adding a target to Bugcrowd.
    
7.  Step 3 focuses on the bug bounty program participation guidelines. The first slider allows a program manager to enable or disable Bugcrowd’s rating taxonomy. The specific guide outlining all of Bugcrowd’s ratings can be seen under the block of text. It’s highly recommended that a program manager use this taxonomy rating. Bugcrowd has been managing security research since 2011 and the VRT (vulnerability rating taxonomy) that they use is well maintained, frequently updated as new vulnerabilities are discovered, and reassessed. Alternatively, this can be turned off and self-maintained, but this is not recommended. The next slider allows the program to accept reported issues that are adjacent to nontarget issues, or in other words imagine a researcher finds an API (application programming interface; a component that defines interactions between multiple software applications or mixed hardware/software intermediaries) key on [www.example.com](http://www.example.com) that allows them to interact with [login.example.com](http://login.example.com). If the login subdomain is not in scope, and this slider is disabled, a researcher will not have the opportunity to report the vulnerability. It is recommended to allow researchers to report out of scope, even though it is noted that they will not be rewarded for the vulnerability. The third slider enables or disables safe harbor. Program managers also have the option to select a partial or full safe harbor if the slider is enabled. The entire point of setting up a bug bounty program is giving security researchers a safe haven to hack while improving the effectiveness of the enterprise security posture. Program managers should enable the safe harbor option. Last, the fourth and final slider of this section is the coordinated disclosure option. Enabling this slider gives the researcher the ability to request that their findings be published to the public. This option should be turned on. Security researchers that hack on a program put in their hard work to disclose to get paid and disclose to the public. If a program manager feels as if they are not ready to have patched vulnerabilities disclosed to the world, running a bug bounty program will prove futile. Silence is the exact opposite of what is needed to encourage the growth of an already fragile relationship between hackers and enterprises.
8.  In step 4, reward ranges are defined ([Figure 6.6](#c06.xhtml#c6-fig-0006)). Choose the “Basic” radio button, especially if this is the first time managing a bug bounty program. Additionally, using the maximum advertised reward feature is unnecessary for a program starting out. Tweaking the reward amounts will come with time as vulnerabilities harden the enterprise security posture. Once the radio button is selected, click on the “Next step” button.
    
    ![Figure 6.6 Adding reward ranges by severity on Bugcrowd.](images/c06f006.png)
    
    [**Figure 6.6**](#c06.xhtml#rc6-fig-0006) Adding reward ranges by severity on Bugcrowd.
    
9.  In step 5, program managers should describe what ideal research concerns look like. Describing areas of focus will help security researchers get a better understanding of what the enterprise is trying to accomplish, for example imagine if a retail company runs a bounty program. They may write something like this ([Figure 6.7](#c06.xhtml#c6-fig-0007)):
    
    ![Figure 6.7 Identify goals and concerns on Bugcrowd.](images/c06f007.png)
    
    [**Figure 6.7**](#c06.xhtml#rc6-fig-0007) Identify goals and concerns on Bugcrowd.
    
10.  As a small example, some considerations focus on cash registers, exposure of sensitive customer data, and any vulnerabilities that can result in the theft of sensitive information. It’s highly important to tell researchers what the program is looking for. However, note that researchers will still attempt to research whatever they want if not explicitly stated as out of scope (and sometimes even still, if it is). Additionally, feel free to focus on specific classes of attacks instead of vectors of attack such as telling researchers that the program is highly interested in “local file inclusion” or “remote code execution,” and so on. This is a great space for the program manager to describe all of the important versus unimportant aspects.
11.  Step 6 is the technical tagging follow-through after defining the vulnerabilities that the bug bounty program is concerned with. There are four sections of the tagging process: researcher activities, asset environments, languages and frameworks, and hosted and third-party applications ([Figure 6.8](#c06.xhtml#c6-fig-0008)). Defining these tags can be important as it can help the correct researchers participate. For example, if a researcher sees that a program is mostly concerned with mobile and API testing, they may decide that it is not for them, saving them a great deal of wasted time and encouraging the right research demographics to participate. Ensuring that asset tagging, research desires, and various frameworks and desired activities are defined is an essential process to help ensure that the program is adequately defined. Programs are free to limit the amount of information that is provided, but it does tend to hurt the general security stance and waste a researcher’s time.
     
     ![Figure 6.8 Select researcher activities, environments, languages, frameworks, and applications/services.](images/c06f008.png)
     
     [**Figure 6.8**](#c06.xhtml#rc6-fig-0008) Select researcher activities, environments, languages, frameworks, and applications/services.
     
12.  Next is “Adding the look and feel” – in short, uploading a logo, generating a tagline that will go under the program, and welcoming researchers to the program with a short description ([Figure 6.9](#c06.xhtml#c6-fig-0009)).
     
     ![Figure 6.9 Upload your company’s logo and create a tagline and introduction.](images/c06f009.png)
     
     [**Figure 6.9**](#c06.xhtml#rc6-fig-0009) Upload your company’s logo and create a tagline and introduction.
     
13.  Additionally, a background color can be chosen for the logo, so give it the best attempt at a decent contrast to make it pop to a security researcher. The introduction space is nothing more than explaining who the program is and why they are hiring security researchers. The space can also be used to explain what the company does and their mission. Inspiring researchers to participate is the ultimate goal.
14.  Step 8 focuses on defining a timeline for both a private and a public launch. If the program manager has already reached the phase of setting up the program, it typically indicates a certain level of readiness and a commitment to setting up a program. For the “Preferred private launch timeline” it is recommended to prepare to launch “Within a month.” As program managers tend to learn, a public program launch is a far bigger commitment. Program managers should select the “More than a month after private launch” option as there will be plenty of work to accomplish to enable a public launch.
15.  Finally, when the next button is clicked in step 8, a page will populate that highlights all of the incentives. Review all of the submitted information and click “Submit” when ready to move on to the next phase.

### 6.2.2 Program Overview

Now that the program is fully set up, getting a feel for the various options and functionality is the next step in understanding how to manage a bug bounty program. Program managers should get familiar with all of the various pages and each of the ways to modify existing program settings to prevent any issues when the program goes live.

#### 6.2.2.1 The Program Dashboard

Once the bug bounty program is created, it brings the program manager back to the dashboard in which they started. The dashboard allows the creation of additional programs but also allows program managers to click on a “Tasks” or the “Welcome center” tab ([Figure 6.10](#c06.xhtml#c6-fig-0010)). The tasks tab allows program managers to see a quick overview of all the to-do vulnerabilities within all of the programs, or even filter by specific programs.

![Figure 6.10 Vulnerability tasking tabs.](images/c06f010.png)

[**Figure 6.10**](#c06.xhtml#rc6-fig-0010) Vulnerability tasking tabs.

As seen, the program manager can see if there are any blockers or vulnerabilities that need to be dealt with or rewarded.

The welcome center promotes all the various Bugcrowd documentation ([Figure 6.11](#c06.xhtml#c6-fig-0011)), including various videos to help program managers effectively run a bug bounty program. The welcome center can assist in leading a program in the right direction. If ever a program manager needs ideas to upgrade the program, fix common configuration issues, or understand the breadth of the vulnerability research space, the welcome center is the hub for knowledge. The welcome center contains hours of videos, manuals, questions, and studies highlighting best practices for managing effective programs. Program managers can benefit from taking the time to read through some of the documentation and to watch the included videos. While not necessary at first, it wouldn’t hurt to get a better understanding of the way Bugcrowd operates.

![Figure 6.11 Bugcrowd documentation.](images/c06f011.png)

[**Figure 6.11**](#c06.xhtml#rc6-fig-0011) Bugcrowd documentation.

Returning back to the main screen, there is a program dashboard the program manager can click on the dropdown menu to select the bug bounty program that they would like to manage ([Figure 6.12](#c06.xhtml#c6-fig-0012)).

![Figure 6.12 Program dropdown menu.](images/c06f012.png)

[**Figure 6.12**](#c06.xhtml#rc6-fig-0012) Program dropdown menu.

#### 6.2.2.2 The Crowd Control Navbar

When a program manager clicks on their program in the dropdown menu, they will be directed to an interface that allows them to manage vulnerabilities and the more advanced configuration settings for the program.

The top panel allows program managers to see a summary of the program, submissions, view and manage researchers, gain insights into the program, and view reports/modify settings ([Figure 6.13](#c06.xhtml#c6-fig-0013)).

![Figure 6.13 Crowd control navbar.](images/c06f013.png)

[**Figure 6.13**](#c06.xhtml#rc6-fig-0013) Crowd control navbar.

##### Summary

The summary page shows program managers all of the program’s recent activities as well as a quick snapshot of their assigned submissions and status of each submission that is currently within the program. Program managers can use this dashboard as a quick way to navigate to issues that need their attention and to get a general feel for the remediation processes and steps needed to push their program into an adequate state.

##### Submissions

The submissions panel is a more extensive version of the summary page ([Figure 6.14](#c06.xhtml#c6-fig-0014)). This page can be used for more advanced filtering of issues and allows program managers to have a much wider view of all of the submitted vulnerabilities and resolve them effectively. Program managers also have the option to download all of the submissions as a CSV file for tracking and sorting.

![Figure 6.14 Vulnerability submissions panel.](images/c06f014.png)

[**Figure 6.14**](#c06.xhtml#rc6-fig-0014) Vulnerability submissions panel.

##### Researchers

The researchers web page shows a total of all the researchers that have been invited, have submitted to the program, the total submissions, and the valid submissions. Underneath the totals, a program manager can see the participating researchers ([Figure 6.15](#c06.xhtml#c6-fig-0015)).

![Figure 6.15 Program participants tab.](images/c06f015.png)

[**Figure 6.15**](#c06.xhtml#rc6-fig-0015) Program participants tab.

Additionally, the “Invitations” tab allows program managers to invite researchers by email. Details of the researcher will not be revealed, to maintain a good privacy posture and allow the researcher to stay safe ([Figure 6.16](#c06.xhtml#c6-fig-0016)).

![Figure 6.16 Program invitations tab.](images/c06f016.png)

[**Figure 6.16**](#c06.xhtml#rc6-fig-0016) Program invitations tab.

##### Rewards

The rewards tab allows program managers to see the various metrics as they pertain to researcher rewards. A quick summary shows how many rewards were given out, the highest reward achieved, the average monetary amount given out, and the remaining reward pool. Program managers have the option to change the length of time that is evaluated in the upper-right-hand corner, and the “Reward History” will provide all of the researchers that were awarded in a given period ([Figure 6.17](#c06.xhtml#c6-fig-0017)). Program managers also have the option to download this as a CSV file. The rewards tab is useful as it allows higher-level management to analyze trends and project expansion and reward predictions.

![Figure 6.17 Program rewards dashboard.](images/c06f017.png)

[**Figure 6.17**](#c06.xhtml#rc6-fig-0017) Program rewards dashboard.

##### Insights Dashboard

The insights dashboard provides an overview of various trends and allows program managers to view valuable data and charts that help them understand the bug bounty program better ([Figure 6.18](#c06.xhtml#c6-fig-0018)). For example, the severity trend of reports and the volume of reports received can be viewed. Additionally, there are performance metrics, amounts paid to researchers by target, and an overall target breakdown ([Figures 6.19](#c06.xhtml#c6-fig-0019) and [6.20](#c06.xhtml#c6-fig-0020)).

![Figure 6.18 Insights dashboard: technical severity chart.](images/c06f018.png)

[**Figure 6.18**](#c06.xhtml#rc6-fig-0018) Insights dashboard: technical severity chart.

![Figure 6.19 Insights dashboard: target breakdown.](images/c06f019.png)

[**Figure 6.19**](#c06.xhtml#rc6-fig-0019) Insights dashboard: target breakdown.

![Figure 6.20 Insights dashboard: performance.](images/c06f020.png)

[**Figure 6.20**](#c06.xhtml#rc6-fig-0020) Insights dashboard: performance.

##### Reports

In the reports tab, program managers can generate reports on their program summary, program health and spend, and security posture reports. Program managers should occasionally generate and review these reports as it will assist in establishing a great deal of information on every aspect of their program.

Review the Bugcrowd link for a more granular overview on reporting and instructions for doing so: [https://docs.bugcrowd.com/customers/program-management/generating-reports/#program-summary-report](https://docs.bugcrowd.com/customers/program-management/generating-reports/#program-summary-report).

### 6.2.3 Advanced Program Configuration and Modification

All of the program settings from the initial setup can be modified. While the “Settings” tab is part of the crowd control navbar, there are many aspects to cover that warrant this tab having its own section in this chapter.

#### 6.2.3.1 Program Brief

The program brief web page is the first visual that a program manager will see when clicking on the “Settings” tab. Essentially, the program brief contains the basic settings of the bug bounty program ([Figure 6.21](#c06.xhtml#c6-fig-0021)). These settings were established when the program was first made, such as the program’s name, tagline, disclosure policy, safe harbor, etc. If any updates to the general program need to be made, this is the section that will be utilized.

![Figure 6.21 Program brief settings.](images/c06f021.png)

[**Figure 6.21**](#c06.xhtml#rc6-fig-0021) Program brief settings.

#### 6.2.3.2 Scope and Rewards

The scope and rewards section is a more visual representation of the program scope details. In this section, the program manager has the specific ability to drill down into more of the details of the focus areas, what assets are out of scope, and modify the safe harbor as they see fit. Additionally, the ability to discuss the specifics of rewards for in- and out-of-scope assets can be discussed here. The scope and rewards sections may seem redundant, but the purpose is to express the enterprise’s stance to ensure that the researcher is aware of all of the possibilities. For example, earlier during the initial configuration the scope and rewards were set. However, this would be a good section to use as a venue to explain to the researcher specifics of the scope as the enterprise may have specific ideas in mind. Take a look at the following screenshot ([Figure 6.22](#c06.xhtml#c6-fig-0022)):

![Figure 6.22 Scope details.](images/c06f022.png)

[**Figure 6.22**](#c06.xhtml#rc6-fig-0022) Scope details.

As seen in [Figure 6.22](#c06.xhtml#c6-fig-0022) under the target information section, a defined credential pair has been provided for testing purposes. In addition, the same figure highlights areas that the enterprise is also concerned with, as an example. Finally, this section is closed out with a custom “Out-of-Scope” notes section. The scope details section is not to be taken lightly, because a failure to handle this section carefully can result in mishaps such as a researcher attempting an attack that can be detrimental to employee safety or the enterprise environment. A program manager should strive to carefully review the ideal out-of-scope attacks in [Chapter 4](#c04.xhtml) and also review the various out-of-scope sections of some of the other public bug bounty programs that are out there to get a good idea of what the enterprise should strive to avoid. For the most part, triage will assist in explaining to a researcher the issues that surround low-level vulnerabilities or those that lack impact. However, the problem lies with valid vulnerabilities that the enterprise bug bounty program may not want to accept. Imagine the following.

The program manager knows that the enterprise is riddled with cross-site scripting (XSS) vulnerabilities. All of the software engineers are aware that nearly every parameter on the domain has issues with XSS. The enterprise still wants to utilize a private bug bounty program but areas of focus are on vulnerabilities that are not well known as issues, such as local file inclusion, remote code execution, html injection, etc. If the program manager did not consider the cleverness of the hackers that will be invited to the program, they may end up with a massive amount of XSS reports – and because it wasn’t marked as an out-of-scope vulnerability type, it could result in the bug bounty program having to pay a lot of money to researchers. One of the most important aspects of program management is realizing that saying, “Ah, we should have had this in our out-of-scope section,” is not an acceptable response by any means and the enterprise will be on the hook for it.

For the most part, the premade safe harbor section is decent and should be kept. Nonetheless, program managers should talk to management to ensure that everyone is on the same page and that the safe harbor adequately reflects the needs of the enterprise. Still, program managers should not let upper-level management or legal teams fully control the safe harbor clause or additions to such clauses, as the result may be overbearing and dissuasive to security researchers who may want to participate.

A “Target Groups” section also exists in this section. It can be a useful way to organize similar assets to prevent researchers from smashing their keyboard attempting to look at all of the tags for what they are hoping to test. Logically, a program manager will want to add all relevant assets before making the group. Unfortunately, to do so, a different section of the application must be utilized. Follow these instructions:

1.  Click on the profile image in the top-right-hand corner and then click on the “Targets” tab under the bug bounty program name ([Figure 6.23](#c06.xhtml#c6-fig-0023)):
    
    ![Figure 6.23 Profile dropdown menu.](images/c06f023.png)
    
    [**Figure 6.23**](#c06.xhtml#rc6-fig-0023) Profile dropdown menu.
    
2.  Clicking on the “Targets” option brings up a web page that acts similar to the initial targets page as discussed when the program was initially set up ([Figure 6.24](#c06.xhtml#c6-fig-0024)). This would be a good time to add and tag any additional assets that researchers should test.
    
    ![Figure 6.24 Targets tab.](images/c06f024.png)
    
    [**Figure 6.24**](#c06.xhtml#rc6-fig-0024) Targets tab.
    
    **Note: remember that not every asset needs to be added at once. If the program manager only has a couple of targets at first, or does not have a lot of assets that can be similarly grouped – that’s fine! As the program expands, groups can be utilized. In fact, there’s no harm in establishing the groups as is with minimal assets just to keep everything organized for the future.** <query id="Q1"> <p>Dear TS, Set as either all bold or highlighted/indented in some way. Please do not first line indent. Set as Note paragraph.</p> </query>
    
3.  After adding all of the relevant assets, as seen above, return to the scope and rewards section by clicking on the “Select a program” dropdown menu and selecting the program ([Figure 6.25](#c06.xhtml#c6-fig-0025)).
    
    ![Figure 6.25 Program dropdown menu.](images/c06f025.png)
    
    [**Figure 6.25**](#c06.xhtml#rc6-fig-0025) Program dropdown menu.
    
4.  Again, click on the “Settings’’ tab on the crowd control navbar, as done previously. Then click on the “Scope and Rewards” tab and, lastly, the “Target Groups” tab.

Adding the groups can be simple but daunting and turn into a mess if the program manager isn’t ready to do so. In reality, the option of group utilization is useful for adjusting reward levels, and can be used to turn out-of-scope reporting into in-scope reporting with benefits. To add a group, perform the following.

1.  First, click on the “Add group” button ([Figure 6.26](#c06.xhtml#c6-fig-0026)).
    
    ![Figure 6.26 “Add group” button.](images/c06f026.png)
    
    [**Figure 6.26**](#c06.xhtml#rc6-fig-0026) “Add group” button.
    
2.  A target group web page will populate. For the title, it is recommended to use something broad to prevent an overwhelming amount of groups from being created. As an example, having general categories such as “Web Application Testing,” “Network Testing,” “Mobile Application Testing,” “API Testing,” etc., will give security researchers a better sense of what to test. However, it isn’t a necessity, and program managers can use more granular names depending on the specific case. After the title is added, a description of the asset group can be useful for security researchers ([Figure 6.27](#c06.xhtml#c6-fig-0027)).
    
    ![Figure 6.27 Description of an asset group.](images/c06f027.png)
    
    [**Figure 6.27**](#c06.xhtml#rc6-fig-0027) Description of an asset group.
    
3.  The next portion underneath the description box is a checkbox that asks if the target group is in scope ([Figure 6.28](#c06.xhtml#c6-fig-0028)). Clicking on the checkbox reveals another checkbox that asks the program manager if the asset group “pays monetary rewards.” The checkbox for rewards is a useful component of target groups, because program managers can take assets that would normally be considered out of scope and offer a limited in-scope option. For example, if the enterprise maintains a domain that is highly vulnerable, leaving the “pays monetary rewards” option unchecked but adding the assets can allow researchers to test and report the vulnerabilities, and the enterprise will not have to pay for the asset. The official recommendation would be to eventually put the assets in scope when they are considered less vulnerable.
    
    ![Figure 6.28 Target groups.](images/c06f028.png)
    
    [**Figure 6.28**](#c06.xhtml#rc6-fig-0028) Target groups.
    
    For this current example, the “Network Assets” group is being created. Therefore, the example that is going to be shown is the result of enabling monetary rewards to walk through the process of creating and modifying rewards.
    
4.  With the checkbox clicked for the rewards option, an overlay will pop up, showing various reward options for the group, such as tiers ranked at high, medium, low, and custom ([Figure 6.29](#c06.xhtml#c6-fig-0029)). These brackets have price ranges on each, and the custom tier can be used for defining rewards per vulnerability criticality classification. Groups are unique in the sense that multiple groups can be assigned different tiers, therefore making it worth a researcher’s time to hack mobile applications over web applications, etc.
    
    ![Figure 6.29 Target group rewards.](images/c06f029.png)
    
    [**Figure 6.29**](#c06.xhtml#rc6-fig-0029) Target group rewards.
    
5.  After the reward is selected, a program manager must click on the “Add new target” button. The only option that is different with this interface is the ability to pick pre-existing targets and add them to the group. Adding each target to a specific group will have to be completely individually. Once all of the targets are added, a program manager can click on the “Save group” button, which will bring program managers to the next web page.
6.  Finally, the groups will be populated on the “Target groups” page, with the name, rewards, and all of the details that were assigned previously ([Figure 6.30](#c06.xhtml#c6-fig-0030)). Program managers will have to utilize the “Add group” option in order to make any additional groups.
    
    ![Figure 6.30 Target group listings.](images/c06f030.png)
    
    [**Figure 6.30**](#c06.xhtml#rc6-fig-0030) Target group listings.
    

#### 6.2.3.3 Integrations

The integrations tab of the settings option allows program managers to connect any relevant tools that their enterprise might have for managing reports ([Figure 6.31](#c06.xhtml#c6-fig-0031)). For example, various configurations such as Jira, Slack, ServiceNow, etc., exist – allowing for an effective reporting and triage workflow. Program managers can opt to use none of these tools, or many of these tools. A standard integration flow may be a ticketing system tool such as Jira, Slack notifications to bring a program manager’s attention to the submission, or an embedded submission form on the website that gives the enterprise the ability to receive submissions from anyone if they don’t exclusively know about Bugcrowd’s services.

![Figure 6.31 Integrating various tools to help with report management.](images/c06f031.png)

[**Figure 6.31**](#c06.xhtml#rc6-fig-0031) Integrating various tools to help with report management.

Rather than explain each integration, program managers are encouraged to review the Bugcrowd documentation. The integration process will vary based on the type of tool Bugcrowd is integrating with.

#### 6.2.3.4 Announcements

The “Announcements” tab is used for notifying researchers of major changes within the program ([Figure 6.32](#c06.xhtml#c6-fig-0032)). Examples of an adequate usage of announcements would be: Increasing Rewards, Expanding Scope, Asking researchers to test a specific asset, etc.

![Figure 6.32 Announcements option.](images/c06f032.png)

[**Figure 6.32**](#c06.xhtml#rc6-fig-0032) Announcements option.

In addition, Bugcrowd maintains specific premade templates that can be used as a starting point for notifying researchers such as Email usage reminders, Scope updates, Reward delays, and more. As you can see in [Figure 6.33](#c06.xhtml#c6-fig-0033), the premade templates can be written and the publish announcement button can be pressed to announce the program’s message to all researchers.

![Figure 6.33 New announcement option.](images/c06f033.png)

[**Figure 6.33**](#c06.xhtml#rc6-fig-0033) New announcement option.

#### 6.2.3.5 Manage Team

In the manage team section, program managers can invite team members to assist in managing the program ([Figure 6.34](#c06.xhtml#c6-fig-0034)). Additionally, the settings allow for an auto assignment of triaged or critical tickets which can assist employees in responding to issues faster, especially if it’s necessary to do so quickly.

![Figure 6.34 Manage team option.](images/c06f034.png)

[**Figure 6.34**](#c06.xhtml#rc6-fig-0034) Manage team option.

Beyond seeing the existing team members, program managers can invite team members by clicking on the “Invite a team member” button, and additionally assign the roles as discussed. ([Figure 6.35](#c06.xhtml#c6-fig-0035)).

![Figure 6.35 Invite a team member option.](images/c06f035.png)

[**Figure 6.35**](#c06.xhtml#rc6-fig-0035) Invite a team member option.

Three separate roles exist when the invite button is pressed: Admin, Analyst, and Viewer. The Admin role can do anything within the program. The Analyst can only manage submissions and basic settings, and the Viewer can only review submissions and options within the program.

#### 6.2.3.6 Submissions

The final program settings tab is the “Submissions” tab. One of the options that can be utilized is a data fields option. This allows program managers to create custom submission fields that can only be seen internally. The fields can be useful in the instance where vulnerabilities need to be easily identified and tagged with a message that the entire team has the ability to see. For example, data fields such as “No Impact” or “Special Exception” could be useful to internally relay that a ticket may be a false-positive or a vulnerability that was brought from out of scope to in scope ([Figure 6.36](#c06.xhtml#c6-fig-0036)). The options are limitless and program managers should experiment and brainstorm with team members to come up with useful data field options.

![Data fields option.](images/c06f036.png)

Data fields option.

Next, the CVSS v3 score option is the same as the initial configuration of the program ([Figure 6.37](#c06.xhtml#c6-fig-0037)). Enabling this option allows for Bugcrowd’s scoring and metric system for the various vulnerabilities.

![Figure 6.37 CVSS v3 option.](images/c06f037.png)

[**Figure 6.37**](#c06.xhtml#rc6-fig-0037) CVSS v3 option.

The remediation advice option should be enabled. There’s no logical reason not to have it enabled as the researcher cannot see the advice and it is a useful feature ([Figure 6.38](#c06.xhtml#c6-fig-0038)). If the option becomes redundant, it can be turned off in the same way that it was turned on.

![Figure 6.38 Remediation advice option.](images/c06f038.png)

[**Figure 6.38**](#c06.xhtml#rc6-fig-0038) Remediation advice option.

After the remediation advice option is the ability to enable retesting. To be honest, the option is up to the discretion of the program manager. When engineers gain more experience, it’s unlikely that they will need assistance with retesting. Nonetheless, it could be a useful option for new program managers. However, it should not be relied upon. One of the best ways to learn the ins and outs of a program is to be on top of testing the vulnerabilities submitted by the researcher. If the program manager constantly tests the vulnerabilities, it’s unlikely that they will need to pay researchers for retesting ([Figure 6.39](#c06.xhtml#c6-fig-0039)).

![Figure 6.39 Retesting option.](images/c06f039.png)

[**Figure 6.39**](#c06.xhtml#rc6-fig-0039) Retesting option.

Last is the “Markdown Embedded Attachments” option ([Figure 6.40](#c06.xhtml#c6-fig-0040)). If this option is enabled, it will require the application to utilize authentication to view embedded images. Leaving this on is important if a program manager values the security of their enterprise.

![Figure 6.40 Markdown embedded attachments option.](images/c06f040.png)

[**Figure 6.40**](#c06.xhtml#rc6-fig-0040) Markdown embedded attachments option.

### 6.2.4 Profile Settings

The final part of the Bugcrowd platform (loosely stated, as there’s much to learn) is the “Profile and Enterprise” sidebar which also includes some payment and good housekeeping functionality ([Figure 6.41](#c06.xhtml#c6-fig-0041)). Among the settings is the ability to refine account security, utilize API credentials, and manage the program’s accounting capabilities. Program managers should immediately tune their profile settings to adequately secure their program login. Maintaining best security practice for the bug bounty program login itself is arguably just as important as resolving the vulnerabilities. If a threat actor were to get access to the bug bounty program login, they would be able to see all of the pre-existing bugs. Therefore, securing any associated accounts registered to the program is not to be taken lightly.

![Figure 6.41 Profile and enterprise sidebar.](images/c06f041.png)

[**Figure 6.41**](#c06.xhtml#rc6-fig-0041) Profile and enterprise sidebar.

The first aspect, “Profile”, includes the settings that are under the email address of the user that is logged into the program. Here, the program manager has the ability to modify profile and account settings, security settings, notification settings, and generate API credentials that can interact with Bugcrowd’s API ([Figure 6.42](#c06.xhtml#c6-fig-0042)).

![Figure 6.42 Profile option.](images/c06f042.png)

[**Figure 6.42**](#c06.xhtml#rc6-fig-0042) Profile option.

#### 6.2.4.1 The Profile and Account

This tab is the default view, and to be frank there’s not much that needs to be explained about this tab. Program managers can expect all of the basic functionality such as modifying profile settings, such as name and display name, and changing their passwords or uploading profile pictures.

#### 6.2.4.2 Security

Modifying the profile security settings is the first aspect of profile management that a program manager should do. The “Security” tab allows for a review of individual sessions, or in other words the ability to see where the account is logged in ([Figure 6.43](#c06.xhtml#c6-fig-0043)).

![Figure 6.43 Security option.](images/c06f043.png)

[**Figure 6.43**](#c06.xhtml#rc6-fig-0043) Security option.

The next tab is “Events,” which can be used as a method of additional telemetry into sessions which could allude to suspicious activity ([Figure 6.44](#c06.xhtml#c6-fig-0044)).

![Figure 6.44 Events option.](images/c06f044.png)

[**Figure 6.44**](#c06.xhtml#rc6-fig-0044) Events option.

Last, but not least, two-factor authentication is the actual security configuration setting that can be utilized ([Figure 6.45](#c06.xhtml#c6-fig-0045)). Setting up two-factor authentication is fairly simple. A program manager will install a two-factor authentication app, such as Google Authenticator, on their mobile device and scan the corresponding QR code or manually enter the code into the app. The final part to enable is to type in a generated six-digit OTP code and click on the “Enable 2FA button.” While using two-factor authentication can seem pesky, it’s important to do so to protect enterprise bug reports, which, if exposed, could lead to compromised assets.

![Figure 6.45 Two-factor authentication option.](images/c06f045.png)

[**Figure 6.45**](#c06.xhtml#rc6-fig-0045) Two-factor authentication option.

#### 6.2.4.3 Notification Settings

A program manager has full transparency and control over the notifications that they will receive from the bug bounty program. Tuning the notifications panel should be an important priority to program managers. Otherwise, “alert fatigue” may occur, or in other words an overwhelming feeling of having too much to look at ([Figure 6.46](#c06.xhtml#c6-fig-0046)). Preventing alert fatigue through managing notifications is an aspect of engineering that is frequently overlooked. Imagine a home alarm system that also has cameras and alerts based on a ruleset. If the homeowner gets an alert twenty times a day, it may feel burdensome and could result in their ignoring an actual event that needs to be reviewed. The same considerations go for alert management.

![Figure 6.46 Notifications settings option.](images/c06f046.png)

[**Figure 6.46**](#c06.xhtml#rc6-fig-0046) Notifications settings option.

As can be seen in [Figure 6.46](#c06.xhtml#c6-fig-0046), there’s quite a bit to unpack, but it’s actually less than one would imagine. For example, the email notification options are straightforward, allowing a program manager to receive emails during activity on subscribed submissions, when team members @mention them, or when a submission is assigned to their program management account username. Leaving the “Activity on subscribed submissions” turned off is up to the preference of the program manager. If the company isn’t exceedingly large, or an engineer’s near-full-time role is to manage a bug bounty program, having all of the notifications turned on is likely the best possible decision. As an in-between consideration, “Activity on subscribed submissions” can be set to “on” in conjunction with the “Subscribe me when a submission reaches a given state” to “Triaged.” Enabling the in-between consideration as described will allow program managers to be alerted in the instance of receiving important updates on a ticket that is triaged. However, please note that at times there may be overbearing security researchers, so experimenting with the notifications and tuning until it’s right will be a program manager’s best bet. Not every program manager has the same preferences. Advice for notifications should be taken in one’s stride.

#### 6.2.4.4 API Credentials

Program managers may want to develop workflows that utilize API calls through scripting, or various external tooling. Bugcrowd allows this type of flexibility to occur as engineers, both security and software alike, may want to utilize this feature. Generating an API key is simple. To generate a key, the program manager just has to type the name of the application in the “Application name” field and click on the “Create credentials” button. The credentials will then be generated and will not be accessible after navigating away from the page ([Figure 6.47](#c06.xhtml#c6-fig-0047)).

![Figure 6.47 API credentials option.](images/c06f047.png)

[**Figure 6.47**](#c06.xhtml#rc6-fig-0047) API credentials option.

### 6.2.5 Enterprise “Profile” Settings

#### 6.2.5.1 Management and Configuration

The final aspect of Bugcrowd is the ability to reconfigure, set up program authentication, or fund the program with accounting settings. Program managers will have to review and action several of these items, as a bug bounty program offers rewards and a pool of money to pull rewards from, which will need to be allocated.

#### 6.2.5.2 Organization Details

The organization details web page hardly differs from the initial setup. This page allows a program manager to upload a new logo for the organization, changing the background color or adding a contact number for the program.

#### 6.2.5.3 Team Members

The team members page exists on other parts of the program configuration. Therefore, the only thing program managers need to know is that this is another route.

#### 6.2.5.4 Targets

Program managers setting up their first program have already utilized this page, as adding targets was a prerequisite to creating groups for the bug bounty program.

#### 6.2.5.5 Authentication

Aspects of authentication are harder to advise on initially, as it will depend on the way the enterprise structures their IdP (identity provider) management. However, program managers should strive to utilize SSO (single sign-on) where available as it is far safer for the enterprise as a whole. Nearly all of the modern-day SSO solutions require users to have (two-factor authentication)TFA enabled to log in, therefore making a program manager’s experience far safer. As an example, Okta is an application that enables the usage of SSO for various applications. Program managers should reach out to their IT support team to find out which team within the organization manages identity management provisioning. There are two aspects of the SSO integration: specific site configuration and SAML (Security Assertion Markup Language) settings. The SSO configuration needs to be provided to the appropriate team to fill in the required fields for the enablement of the solution. In addition, the same team will have to provide the program manager with all of the SAML settings for the identity management provider to fill in the corresponding fields. Once complete, the authentication settings can be saved.

As seen in [Figure 6.48](#c06.xhtml#c6-fig-0048), the various fields need to be completed. If the enterprise does not maintain an SSO solution, the Bugcrowd default will be the utilization of a standard enterprise email address in conjunction with a password.

![Figure 6.48 Single sign-on option.](images/c06f048.png)

[**Figure 6.48**](#c06.xhtml#rc6-fig-0048) Single sign-on option.

**Note: domain verification is needed in order to establish SSO within the program, so the following “Domains” tab setup should be carefully followed.** <query id="Q2"> <p>Dear TS, Set as either all bold or highlighted/indented in some way. Please do not first line indent. Set as Note paragraph.</p> </query>

#### 6.2.5.6 Domains

Verifying any of the domains added to the program is required to enable SSO. To complete the verification process, all of the domains can be entered in the textbox and the “Add domain” button can be pressed. Once the domain is added, it will populate under the “Unverified domains” section and a program manager will have to communicate with the enterprise team responsible for managing the DNS (domain name server) for the company. Program managers should let the responsible team (which may be the network engineering team or similar) know that they need to verify all of the domains in order to set up SSO. The unverified domains will have a verification code next to them, and the code needs to be added to a TXT (text record, which is a resource record in the domain name system \[DNS\] used to provide the ability to associate arbitrary text with a host or other name) record and hosted on the root domain ([Figure 6.49](#c06.xhtml#c6-fig-0049)). It may take 24 hours for it to populate.

![Figure 6.49 Unverified domains option.](images/c06f049.png)

[**Figure 6.49**](#c06.xhtml#rc6-fig-0049) Unverified domains option.

#### 6.2.5.7 Accounting

Program managers will utilize the accounting page as a means of allocating a bug bounty pool. Bug bounty program managers can transfer funds, deposit funds, or see an overall activity or program balance. Without a bounty pool assigned, researchers cannot get awarded. Program managers should ensure that this feature is set up before continuing.

As shown in [Figure 6.50](#c06.xhtml#c6-fig-0050), an activity summary is provided, including an organizational pool, pending deposits, program allocation, and total amount of money spent. Program managers can click on the “Deposit funds” button to assign money to their bounty pool.

![Figure 6.50 Activity summary.](images/c06f050.png)

[**Figure 6.50**](#c06.xhtml#rc6-fig-0050) Activity summary.

When the “Deposit funds” button is clicked, there will be a textbox that asks for the destination, and that is where the program manager will select the program they would want to assign money to. The program manager can then type the amount of money into the textbox, click on the “I agree to terms and conditions for the transaction” checkbox, and click on the submit deposit request ([Figure 6.51](#c06.xhtml#c6-fig-0051)). The account manager will then send an invoice to the program manager to run through to the finance team. Program managers will have to ensure that management is tracking expenditures and get it approved through the correct processes. Once Bugcrowd approves the pending deposits, the bug bounty pool will be assigned money that can be used to reward researchers.

![Figure 6.51 Submit deposit request option.](images/c06f051.png)

[**Figure 6.51**](#c06.xhtml#rc6-fig-0051) Submit deposit request option.

**Note: program managers should never assume that they have enough money in the pool. It is an essential responsibility to ensure that the program manager is keeping track of the reward pool at all times.** <query id="Q3"> <p>Dear TS, Set as either all bold or highlighted/indented in some way. Please do not first line indent. Set as Note paragraph.</p> </query>

As shown in [Figure 6.52](#c06.xhtml#c6-fig-0052), a program manager can also utilize the “Transfer funds” button. Transferring funds allows program managers to deposit money from one pool to another when they run multiple programs. The transfer funds option is nearly identical to the deposit funds option. The final option within the accounting tab is the “Program balances” tab. The program balances tab allows program managers to see the bug bounty pool for a multitude of programs. For example, some enterprises own multiple companies and may want to segment bug bounty programs by company to avoid confusion. When a program manager runs multiple bug bounty programs, they should periodically check the program balances tab to ensure that all of the programs are funded ([Figure 6.53](#c06.xhtml#c6-fig-0053)).

![Figure 6.52 Transfer funds option.](images/c06f052.png)

[**Figure 6.52**](#c06.xhtml#rc6-fig-0052) Transfer funds option.

![Figure 6.53 Program balances option.](images/c06f053.png)

[**Figure 6.53**](#c06.xhtml#rc6-fig-0053) Program balances option.

## 6.3 HackerOne

Another crowdsourcing option is HackerOne. Using HackerOne will feel different from Bugcrowd in the sense that there’s more going on, immediately from the login. Specifically, the login to Bugcrowd provides the program manager with a simple overview, whereas HackerOne merges a security researcher’s and program manager’s views. The merging of research and program views can feel daunting. A new program manager may have issues sorting through the options. Attempting to manage the program can even feel clunky for a more seasoned program manager. However, the intention is to describe most of the functionality available within HackerOne. Additionally, HackerOne has many more options for configuration. However, the expertise of the program manager will determine which crowdsourcing platform is best for them.

Unfortunately, HackerOne does not have an easy-to-utilize demo program that is readily available to anyone. In order to mitigate this issue, an already established program will be utilized and the settings and configurations evaluated. The primary tabs that will be focused on are the program dashboard, program settings, and inbox tabs; anything else within HackerOne typically tends to relate to researchers specifically. Additionally, some of the configuration settings of the profile will be evaluated as well. The ability to understand the setup of a program from start to finish will ultimately result in an easier transition if a program manager ever works for a firm that utilizes a different crowdsourcing platform.

### 6.3.1 Program Settings

The first aspect that will be focused on is the “Program settings” tab ([Figure 6.54](#c06.xhtml#c6-fig-0054)). The program settings tab has two subtabs: General and Program. As a baseline, the general tab contains information, product addition, authentication, verified domains, credential management, user management, group management, and an audit log. Additionally, there is a small section dedicated to billing. The program tab has four subheaders with a wide range of options: customization, hacker management, rewards, and automation.

![Figure 6.54 Program settings option.](images/c06f054.png)

[**Figure 6.54**](#c06.xhtml#rc6-fig-0054) Program settings option.

#### 6.3.1.1 General

The general tab can be considered the tab to use when program managers want to configure all of the miscellaneous options of the program ([Figure 6.55](#c06.xhtml#c6-fig-0055)). The utilization of the general tap will be essential, as billing information is contained within the general tab under the “billing” subheader.

![Figure 6.55 Miscellaneous program options.](images/c06f055.png)

[**Figure 6.55**](#c06.xhtml#rc6-fig-0055) Miscellaneous program options.

#### 6.3.1.2 Information

The information tab contains the security page information for the bug bounty program ([Figure 6.56](#c06.xhtml#c6-fig-0056)). Within this tab, program managers can name the program, assign a program handle, define the main website for the program, and write a tagline under the “About me” tab. Additionally, program managers can provide a relevant Twitter account username or update the program’s logo.

![Figure 6.56 Security page function.](images/c06f056.png)

[**Figure 6.56**](#c06.xhtml#rc6-fig-0056) Security page function.

#### 6.3.1.3 Product Edition

HackerOne has two different product editions, the first edition is “bounty professional” and the other option is “bounty enterprise” ([Figure 6.57](#c06.xhtml#c6-fig-0057)). Program managers have the option between the two, but should consult with management and with account managers to determine the major differences and price considerations. The given price point could be a general determinant, however professional the basic edition. This tab allows program managers to see product addition statistics, and contact support for a different product.

![Figure 6.57 HackerOne product editions.](images/c06f057.png)

[**Figure 6.57**](#c06.xhtml#rc6-fig-0057) HackerOne product editions.

#### 6.3.1.4 Authentication

Similar to Bugcrowd, HackerOne has the option to enable SSO. Program managers can click on the “Enable SAML” button. However, this is not currently shown in the screenshot example ([Figure 6.58](#c06.xhtml#c6-fig-0058)). Program managers will have to go through the IdP management team to acquire the correct settings to configure SSO. In addition, HackerOne varies from Bugcrowd as HackerOne program managers can contact their account managers to enable the IP Allowlist feature. The IP Allowlist feature will ensure that only certain IP addresses can access program management.

![Figure 6.58 Single sign-on with SAML.](images/c06f058.png)

[**Figure 6.58**](#c06.xhtml#rc6-fig-0058) Single sign-on with SAML.

#### 6.3.1.5 Verified Domains

The “Verify domains” tab allows a program manager to add domains, which is a requirement to enable SSO. The one difference between Bugcrowd’s verification and HackerOne’s verification, is that HackerOne also allows HTML meta tag verification and web file verification in addition to DNS txt records ([Figure 6.59](#c06.xhtml#c6-fig-0059)).

![Figure 6.59 Domain verification example.](images/c06f059.png)

[**Figure 6.59**](#c06.xhtml#rc6-fig-0059) Domain verification example.

#### 6.3.1.6 Credential Management

The “Credential management” tab allows program managers to provide CSV files to hackers in order to authenticate the application ([Figure 6.60](#c06.xhtml#c6-fig-0060)). In some cases, having an authenticated account is useful for testing for certain vulnerabilities.

![Figure 6.60 Credential management tab.](images/c06f060.png)

[**Figure 6.60**](#c06.xhtml#rc6-fig-0060) Credential management tab.

#### 6.3.1.7 Group Management

Even though user management comes before group management, setting up a group is a step that will be essential before setting up users to ensure that program managers are maintaining the best possible security practice for role-based access control, or in other words keeping their program in check. Program managers should make the best attempt to create appropriate role groups for need-to-know and essential roles. As a general rule of thumb, there should be one role that has full permissions, one role that has most permissions, and one role that has extremely limited permissions ([Figure 6.61](#c06.xhtml#c6-fig-0061)). Maintaining the full suite of roles will allow program managers to assign permissions quickly without impacting the program.

![Figure 6.61 Group management options.](images/c06f061.png)

[**Figure 6.61**](#c06.xhtml#rc6-fig-0061) Group management options.

To add a role group, program managers should click the “Add group” button in the top-right-hand corner of the group management pane. Once the button is clicked, the add group page will appear and program managers can name the group and assign appropriate permissions. The default level of permissions allows users to view reports and post internal comments. Outside of default permissions, program managers can assign the reporting role, the program role, the reward role, or the admin role. As a good example of a limited role, a program manager should name a group and maintain default permissions if not already set within the group management tab. Another group can be created that allows response to vulnerabilities without program management. In order to do so, program managers can assign the report role in conjunction with the reward role. Finally, program managers can click all of the checkboxes to enable others to have full admin permissions over the program ([Figure 6.62](#c06.xhtml#c6-fig-0062)).

![Figure 6.62 Group management options.](images/c06f062.png)

[**Figure 6.62**](#c06.xhtml#rc6-fig-0062) Group management options.

#### 6.3.1.8 User Management

Once the role groups are made, users can be added to the groups based on appropriate roles to keep the program efficient and well managed. Adding users is a fairly simple task, the only thing program managers have to do is click on the user management tab, click on the “Invite User” button, and then enter an email address and pick the groups to assign to the user ([Figure 6.63](#c06.xhtml#c6-fig-0063)).

![Figure 6.63 Adding users option.](images/c06f063.png)

[**Figure 6.63**](#c06.xhtml#rc6-fig-0063) Adding users option.

#### 6.3.1.9 Audit Log

The final section of the general subheader is the audit log. The audit log is for viewing all of the events that have occurred within the program ([Figure 6.64](#c06.xhtml#c6-fig-0064)). The events include actions that team members have taken as well as user agents and the date and region of occurrence. Maintaining accountability for actions within the program is important, especially if a lot of employees are participating in managing the program. In addition, HackerOne allows program managers to search by event, user, or date of the event occurrence. Audit log data can also be downloaded in CSV format.

![Figure 6.64 Audit log option.](images/c06f064.png)

[**Figure 6.64**](#c06.xhtml#rc6-fig-0064) Audit log option.

### 6.3.2 Billing

The billing subheader includes an overview, credit card setup, and prepayment for the bug bounty program pool. As stated in Section 6.3, it is essential to set up the billing section and fund the bounty pool as soon as possible. Delays in funding could result in a delay in the launch of the program.

#### 6.3.2.1 Overview

The overview section includes the current balance of bounties and fees that a program manager has paid to security researchers. In this section, an activity report is available which allows program managers to see all of the dates that they have awarded researchers as well as the fees and running balance ([Figure 6.65](#c06.xhtml#c6-fig-0065)). Program managers can change the billing period, and view all of the month’s activity history. Additionally, program managers can export reports as PDF or CSV files.

![Figure 6.65 Overview of bounties and fees.](images/c06f065.png)

[**Figure 6.65**](#c06.xhtml#rc6-fig-0065) Overview of bounties and fees.

#### 6.3.2.2 Credit Card

The credit card portion of the billing section is straightforward. A credit card can be saved within this section to be used for adding money to the bounty pool.

#### 6.3.2.3 Prepayment

Program managers should consult with the finance team responsible for organizational funding, or contact their account managers to seek guidance on requesting invoices and prepayments. Specific enterprises will have internal regulations for invoices. Therefore, it is pertinent to ensure that the correct procedure is followed.

### 6.3.3 Program

The program subheader of the program’s setting tab, is used for the majority of the technical details that will be used for configuring the program and managing hacker interactions. Program managers can depend on this tab to set up nearly every aspect of the bug bounty program. Nonetheless, bug bounty crowdsourcing platforms typically have similar options. Even with option overlap, program managers should be aware of subtle differences in configurations between platforms.

#### 6.3.3.1 Policy

HackerOne’s policy tab is nearly identical to Bugcrowd’s policy configuration options. Owing to the nature of the policy being in use for a live, private bug bounty program, a screenshot will not be included. However, rest assured that the overlap makes the policy configuration within HackerOne easy to understand.

#### 6.3.3.2 Scope

The scope configurations within HackerOne are completely different from Bugcrowd’s scope and assets configuration. Program managers can click on the “Add asset” button, which will allow them to determine the rating and criticality of the assets as well as set labels, add instructions, and the live addition of the asset to the program. The “Add asset” page allows program managers to get fairly granular with considerations for researchers testing on the specific asset. In addition, program managers can scroll over most of the labels to determine what the labels mean ([Figure 6.66](#c06.xhtml#c6-fig-0066)).

![Figure 6.66 Adding assets.](images/c06f066.png)

[**Figure 6.66**](#c06.xhtml#rc6-fig-0066) Adding assets.

To determine the environmental score of an asset, program managers must understand the CIA Triad. The CIA Triad stands for confidentiality, integrity, and availability ([Figure 6.67](#c06.xhtml#c6-fig-0067)). Confidentiality impact can be determined by the exposure of sensitive data to a threat actor. Integrity typically pertains to the modification of data. For instance, a high integrity impact rating would mean that all of the files can be modified by a threat actor. Lastly, availability is the determination of the uptime of an asset. A program manager may think of availability as an environmental factor that is only impacted by a certain suite of vulnerabilities. However, program managers must consider how a specific type of attack affects all of the environmental factors. As an example, remote code execution could result in a total loss of confidentiality, integrity, and availability. If a threat actor were to gain complete root access to a server, for instance, they could shut the server down, steal data, or modify any of the data on the server giving the vulnerability the highest rating for environmental score. Other than the difference in criticality scoring, the scope is similar to most of the other program options utilized by other platforms.

![Figure 6.67 The CIA triad.](images/c06f067.png)

[**Figure 6.67**](#c06.xhtml#rc6-fig-0067) The CIA triad.

#### 6.3.3.3 Submit Report Form

The “Submit Report Form” tab is where program managers can customize the introduction for submission templates ([Figure 6.68](#c06.xhtml#c6-fig-0068)). Program managers can customize the submit report form even allowing or hiding specific weakness configurations ([Figure 6.69](#c06.xhtml#c6-fig-0069)). However, it is highly recommended that program managers only hide weakness configurations that are blatantly regarded as out-of-scope attack vectors. Program managers should not attempt to hide legitimate weakness configurations just because they do not want to deal with the report. If the vulnerability is a legitimate issue, it would be better for the security posture of the enterprise if the program allows the submission and resolves appropriately.

![Figure 6.68 Submit report form option.](images/c06f068.png)

[**Figure 6.68**](#c06.xhtml#rc6-fig-0068) Submit report form option.

![Figure 6.69 Customizing the report form.](images/c06f069.png)

[**Figure 6.69**](#c06.xhtml#rc6-fig-0069) Customizing the report form.

#### 6.3.3.4 Response Targets

The “Response Targets” tab is where the program manager can set the time to “first response but time to triage” and the time to bounty as a baseline for the program ([Figure 6.70](#c06.xhtml#c6-fig-0070)). Additionally, the time to resolution projection can also be set for each vulnerability pending on the corresponding criticality. All of the days that the program manager sets as a target are just that: an anticipated date of action and not necessarily representative of the actual time it will take. Also, the target dates per action or in business days means that weekends do not count or identified the days the enterprise does not operate. An important aspect of evaluating the response targets is being honest as a program manager. While setting up the bug bounty program, the configuration should not be set to unrealistic response targets as it will dissuade researchers from future participation, especially if the targets are consistently missed.

![Figure 6.70 Response targets option.](images/c06f070.png)

[**Figure 6.70**](#c06.xhtml#rc6-fig-0070) Response targets option.

It is not of the highest priority to get the exact target days to resolve correctly. However, program managers should aspire to uphold the timelines they set out between response, triage, bounty, and resolution. If a program manager runs a bug bounty program for a long time. They are likely to eventually miss a target. Nonetheless, program managers should not take this too hard, but rather should learn from their mistakes.

#### 6.3.3.5 Metrics Display

The metrics display tab shows various statistics that could potentially attract security researchers to the bug bounty program ([Figure 6.71](#c06.xhtml#c6-fig-0071)). However, the metrics that are displayed are completely up to the program manager. There isn’t necessarily a “wrong” way to display metrics.

![Figure 6.71 Metrics display option.](images/c06f071.png)

[**Figure 6.71**](#c06.xhtml#rc6-fig-0071) Metrics display option.

#### 6.3.3.6 Email Notifications

The email notifications tab is self-explanatory. Program managers have the ability to choose from three options. The options given are “No content,” “Minimal content,” and “Full content” ([Figure 6.72](#c06.xhtml#c6-fig-0072)).

![Figure 6.72 Setting email notifications.](images/c06f072.png)

[**Figure 6.72**](#c06.xhtml#rc6-fig-0072) Setting email notifications.

#### 6.3.3.7 Inbox Views

In short, these are quick views that can execute filters applied to reports in the inbox tab. Program managers can come to this tab to enable or disable saved views ([Figure 6.73](#c06.xhtml#c6-fig-0073)).

![Figure 6.73 Inbox views option.](images/c06f073.png)

[**Figure 6.73**](#c06.xhtml#rc6-fig-0073) Inbox views option.

#### 6.3.3.8 Disclosure

Enabling this function allows hackers to disclose reports in the program ([Figure 6.74](#c06.xhtml#c6-fig-0074)).

![Figure 6.74 Disclosure option.](images/c06f074.png)

[**Figure 6.74**](#c06.xhtml#rc6-fig-0074) Disclosure option.

#### 6.3.3.9 Custom Fields

The “Custom Fields” tab allows a program manager to tag reports with key value data. Unfortunately, this feature is only available to enterprise edition users. Bugcrowd, on the other hand, includes this functionality by default.

#### 6.3.3.10 Invitations

Hacker invitations are just that: a functionality that is utilized to invite hackers to the program. This tab allows the invitation by email, username, or reputation. In addition, a report volume can be set; the report volume allows program managers to set a minimum report desire ([Figure 6.75](#c06.xhtml#c6-fig-0075)). If the minimum is not met, the program will automatically invite hackers until the number of monthly reports is met.

![Figure 6.75 Invitations option.](images/c06f075.png)

[**Figure 6.75**](#c06.xhtml#rc6-fig-0075) Invitations option.

When program managers are ready for a public launch, this is where they can go to launch the incentive ([Figure 6.76](#c06.xhtml#c6-fig-0076)). HackerOne recommends that the program contains at least 100 hackers before launching to the public. Additionally, HackerOne warns that a bug bounty program can receive up to 200 reports in the first week of going public and that reverting back to private can affect the program and hackers negatively.

![Figure 6.76 Public launch option.](images/c06f076.png)

[**Figure 6.76**](#c06.xhtml#rc6-fig-0076) Public launch option.

#### 6.3.3.11 Submission

The submission tab utilizes the ability to limit who has access to the program by creating signal restrictions that affect how many reports can be submitted ([Figure 6.77](#c06.xhtml#c6-fig-0077)). Four different settings allow security researchers to submit more or fewer reports. For example, a strict signal setting would be the best option for a new bug bounty program, especially if the program manager doesn’t have much experience with bug bounty programs. However, conversely, turning off signal requirements are for the most seasoned of bug bounty programs. Usually, choosing the standard signal option is best practice.

![Figure 6.77 Submission requirements option.](images/c06f077.png)

[**Figure 6.77**](#c06.xhtml#rc6-fig-0077) Submission requirements option.

Additionally, enabling “Human-augmented Signal” will allow HackerOne permission to allow analysts from HackerOne to classify all incoming reports. This human review could be a good feature to enable as it can assist in preventing spam or bad reports. However, the feature should be used with caution. If the report is rejected, it will be marked as “Not Applicable” but will not generate a notification for the bug bounty program. A lack of a generated notification could potentially be bad for a program manager new to bug bounty programs, especially if mistakes are made in the flagging process.

The last part of the submission section allows a forced requirement of two-factor authentication and bounty splitting. While there may be legitimate concern for some programs, it’s not an absolute necessity to force hackers to have two-factor authentication and may actually discourage program participation. Bounty splitting is an essential feature if the enterprise can afford to set up prepayment for programs. Encouraging hacker collaboration and participation can lead to more unique, critical exploits that are presented to the organization.

#### 6.3.3.12 Message Hackers

The ability to message hackers is yet another standard feature offered by most bug bounty program platforms. HackerOne’s functionality specifically allows program managers to select specific groups of security researchers to message ([Figure 6.78](#c06.xhtml#c6-fig-0078)).

![Figure 6.78 Messaging hackers option.](images/c06f078.png)

[**Figure 6.78**](#c06.xhtml#rc6-fig-0078) Messaging hackers option.

#### 6.3.3.13 Email Forwarding

The ability to set up an email address and enable email forwarding allows program managers to receive relevant vulnerability reports ([Figure 6.79](#c06.xhtml#c6-fig-0079)). Enabling this functionality is helpful in the event that an enterprise wants to keep its bug bounty program somewhat private. Providing a good forwarding email on a security page or security.txt could prove useful. Programs will receive these emails in the HackerOne inbox. However, one should note that this could create spam too. Therefore, a dedicated email for the HackerOne program is recommended.

![Figure 6.79 Email forwarding function.](images/c06f079.png)

[**Figure 6.79**](#c06.xhtml#rc6-fig-0079) Email forwarding function.

#### 6.3.3.14 Embedded Submission Form

First and foremost, the embedded submission form option is only available to enterprises that have the Enterprise edition of HackerOne. Unfortunately, this could not be tested, because of my product model. However, the form appears to have the same functionality that comes with Bugcrowd’s program natively ([Figure 6.80](#c06.xhtml#c6-fig-0080)). A program manager can set up and embed the form on a web page for hackers who may stumble upon vulnerabilities.

![Figure 6.80 Embedded submission configuration.](images/c06f080.png)

[**Figure 6.80**](#c06.xhtml#rc6-fig-0080) Embedded submission configuration.

#### 6.3.3.15 Bounties

Rewarding researchers is the bread and butter of a bug bounty program. Within HackerOne’s “Bounties” tab, there are several things that can be done ([Figure 6.81](#c06.xhtml#c6-fig-0081)). For one, specific monetary reward values can be assigned per asset. In addition, custom bounty headings can be made or other rows can be inserted. It’s *not* recommended to make up custom criticality ratings, as this can be confusing to hackers who have previously utilized the standard low/medium/high/critical ratings. The optional description field allows program managers to discuss the specifics of rewards and, underneath, a history of bounties that were paid out can be seen.

![Figure 6.81 Bounties option.](images/c06f081.png)

[**Figure 6.81**](#c06.xhtml#rc6-fig-0081) Bounties option.

#### 6.3.3.16 Swag

Within this tab, there isn’t much to cover. An option to turn swag awards on or off is available. If you don’t know what swag is, it’s basically company-branded apparel or items that programs can opt to give out to hackers for participating in the program.

#### 6.3.3.17 Common Responses

When managing a bug bounty program, enterprises will find an annoyance in out-of-scope or nonvulnerable/unqualifying vulnerability reports. The “Common responses” tab provides an easy way for program managers to add custom responses to mitigate considerable nonissues that are reported to the program ([Figure 6.82](#c06.xhtml#c6-fig-0082)).

![Figure 6.82 Common reponses option.](images/c06f082.png)

[**Figure 6.82**](#c06.xhtml#rc6-fig-0082) Common reponses option.

The common responses automation can assist with more than just dealing with out-of-scope vulnerabilities. Program managers can create automations for any scenario, including a ticket changing from open to triage, or closing tickets. For example, a program manager may want to automate a common response that congratulates a researcher for participating when they are rewarded, and so on.

To create a flow, follow the following steps.

Click on the “Add Common Response” button ([Figure 6.83](#c06.xhtml#c6-fig-0083)):

![Figure 6.83 Add common response option.](images/c06f083.png)

[**Figure 6.83**](#c06.xhtml#rc6-fig-0083) Add common response option.

Create the flow, set the title to something that can be remembered. As an example it could be a decent idea to title a common response as “Reward Response,” and in the message field a program manager can type a message to send to a hacker after rewarding them, such as “Thank you for participating in our program! We encourage you to keep hacking!” or whatever seems like a good fit ([Figure 6.84](#c06.xhtml#c6-fig-0084)).

![Figure 6.84 Edit common response option.](images/c06f084.png)

[**Figure 6.84**](#c06.xhtml#rc6-fig-0084) Edit common response option.

Once the response is saved, a program manager can click on the “Default Common Responses” button to set a common response to an action ([Figure 6.85](#c06.xhtml#c6-fig-0085)):

![Figure 6.85 Default common responses option.](images/c06f085.png)

[**Figure 6.85**](#c06.xhtml#rc6-fig-0085) Default common responses option.

As seen, nearly any ticketing action can be utilized in conjunction with common responses. Program managers can creative baseline responses to help assist in day-to-day workflows, but it isn’t a requirement of a successful program.

#### 6.3.3.18 Triggers

The “Triggers” tab offers similar functionality to the common responses tab. However, it offers more specific wording and tuning. Enterprises can configure default rules that elicit specific responses when keywords or fields are matched. The triggers are written as basic if/then statements. Program managers can combine a wide variety of options, even multiple options to make up the various triggers. Observe the following example ([Figure 6.86](#c06.xhtml#c6-fig-0086)):

![Figure 6.86 Create triggers option.](images/c06f086.png)

[**Figure 6.86**](#c06.xhtml#rc6-fig-0086) Create triggers option.

The above is broken into simple statements, and two rules were added to show how it can be utilized. First, a program manager must select what their triggering event is. So, in this instance, if the report weakness contains a use of hard-coded credentials, and the report severity contains critical, then a comment will be added to all participants in the program (bug bounty program managers and hackers) stating, “If you do not get a response in thirty minutes, please contact our emergency response team at 123-123-1234.” There are many ways in which triggers can be used to increase the effectiveness of programs.

#### 6.3.3.19 Integrations

In all, the HackerOne program options allow for more integrations than Bugcrowd. Additionally, similar to Bugcrowd, documentation for the integrations exist and can be utilized as a means of understanding the ins and outs of configuration. Again, as there are a lot of options and some are fairly specific, they are not discussed individually in this chapter.

#### 6.3.3.20 Api

The API settings are straightforward and are also identical in many senses to Bugcrowd’s API features.

#### 6.3.3.21 Hackbot

Settings within the “Hackbot” tab enable the automation of specific actions and triggers within the bug bounty program. For the most part, all of the various settings are concise and program managers can decide what level of option functionality makes sense for their situation ([Figure 6.87](#c06.xhtml#c6-fig-0087)).

![Figure 6.87 Hackbot settings option.](images/c06f087.png)

[**Figure 6.87**](#c06.xhtml#rc6-fig-0087) Hackbot settings option.

#### 6.3.3.22 Export Reports

The ability to export reports is simple. A program manager only has to enter in their email and all of the reports will be emailed to them ([Figure 6.88](#c06.xhtml#c6-fig-0088)). All of the vulnerability reports will take some time to process, and then when it’s done the reports will be available for download as a CSV file.

![Figure 6.88 Export reports option.](images/c06f088.png)

[**Figure 6.88**](#c06.xhtml#rc6-fig-0088) Export reports option.

#### 6.3.3.23 Profile Settings

The profile settings page is fairly standard and all in all isn’t much different from other configurations. HackerOne is a little bit more unique in the sense that it blends researcher and program manager preferences together.

### 6.3.4 Inbox

Program managers will spend the majority of their time within the inbox, working on resolving reported vulnerabilities. The left-hand side of [Figure 6.89](#c06.xhtml#c6-fig-0089) represents a preview of all reports within the program, starting with the new and unassigned reports. Several tabs exist for filtering reports, primarily by new reports that haven’t been addressed, reports that need resolution, reports that need retesting, and reports that are considered “missed targets.” The last tab of the top inbox panel is the “All” tab. It contains the historical contents of every report that has been submitted through the program.

![Figure 6.89 Reporting inbox vulnerabilities.](images/c06f089.png)

[**Figure 6.89**](#c06.xhtml#rc6-fig-0089) Reporting inbox vulnerabilities.

An example report is shown in [Figure 6.90](#c06.xhtml#c6-fig-0090).

#### 6.3.4.1 Report Details

![Figure 6.90 Example report.](images/c06f090.png)

[**Figure 6.90**](#c06.xhtml#rc6-fig-0090) Example report.

The fields that the report contains will change based on the platform that a program manager uses. However, many pieces repeat. For example, the “State” simply defines what phase the submission is in, the “Severity” is the criticality, the “Asset” is what the hacker is reporting on, etc.

#### 6.3.4.2 Timeline

The portion of the report in which a hacker proves to the program that there’s a legitimate proof of concept for the vulnerability is the “timeline.” In short, the timeline is the overall justification including the description of the vulnerability, presumed impact caused, and the steps to replicate ([Figure 6.91](#c06.xhtml#c6-fig-0091)). The timeline is also used as a means to address any vulnerabilities that are reported. Bug bounty program managers can click on the various functions and reward hackers, add comments, close reports, etc.

![Figure 6.91 Timeline option.](images/c06f091.png)

[**Figure 6.91**](#c06.xhtml#rc6-fig-0091) Timeline option.

## 6.4 Summary

Creating bug bounty programs can feel complex, and while there are many options for program management platforms many of them offer similar functionality. Overall, Bugcrowd and HackerOne were used as examples, each with unique management styles and methodologies. In my opinion, Bugcrowd maintains a higher overall ease of access, setup, and program management segmentation, whereas HackerOne has more automation, filtering, and features for an exceedingly large program. Nonetheless, program managers should still research all of the options as, periodically, functionality changes.

# Part 4   
Vulnerability Reports and Disclosure

# 7   
Triage and Bug Management

## 7.1 Understanding Triage

Triage is the act of reviewing vulnerabilities, and determining whether the report warrants further action within the intake process.

1.  Determine if the asset is in scope.
    
    If it’s not in scope, assess the criticality of the vulnerability. If it isn’t a serious vulnerability, determine if the bug will be triaged. In most cases, program managers will want to triage serious bugs, even if the vulnerability is considered out of scope.
    
2.  Analyze the report.
    
    This includes attempting to see if the proof of concept that was submitted is valid, determining criticality, and so on.
    
3.  Request additional information.
    
    Generally speaking, a program manager should not triage a vulnerability unless it meets all of the criteria set out in the in-scope section of the program description.
    
    Ensure that any questionable information that’s provided is clarified upon, generally, as it pertains to vulnerability validation. The criticality of the bug can be changed later in the resolution process, as well as other detail determinations.
    
4.  Triage the bug.
    

### 7.1.1 Validation

The vulnerability validation process should be handled diligently with respect to the production environment, research authenticity, and program definitions. While this sounds complex, it translates to making sure that bug handling occurs in a way that isn’t detrimental to any sort of current production processes and that adequate time and effort is dedicated to validating the bug.

In addition to ensuring that a researcher’s report is handled swiftly in the validation process, programs must be diligent about validation – for their own protection in the communication processes and against financial manipulation.

### 7.1.2 Lessons Learned

Failure to validate and understand vulnerabilities can prove deadly for an organization. The impact can be monetary loss, software engineering distrust, and general reputational damage. It’s better to take a little time to be valuable and assess the true impact of the vulnerability, and then to quickly triage it. As a note, it never hurts to coordinate with peers if the impact of the vulnerability is misunderstood or if there’s any sign of strange validation anomalies. Additionally, the triage evaluation stage is a perfect time to ask a researcher for more information. Bug bounty program managers must make use of additional information gathering where necessary.

### 7.1.3 Vulnerability Mishaps

When vulnerability mishaps occur, it’s the responsibility of the program managers to accept the mistakes. Confrontation with the security researcher over mishaps or any requests or threats made in an attempt to retrieve the money are out of bounds. At the end of the day, it’s not the researcher’s fault when a program does not validate the vulnerability. In fact, we are all human and it’s not improbable that triage, the program manager, and the researcher could have all made a mistake. Part of growth is accepting the issue and being transparent with leadership if asked about the situation.

There’s a lot of room for improvement in a program. Even the experts in the application security field know that there’s no possible way they will know everything. Security is dynamic and a team effort. One of the best ways to prevent mistakes from happening again is to ensure that records of accidents have been maintained. Mishaps aren’t the end of the world, but it’s difficult to know what to avoid in the future if accountability for the mistakes isn’t accepted.

On top of self-accountability, there’s a possibility a researcher might hold themselves accountable and message the program about the mistake. Even though the probability of a researcher doing so is significantly lower, don’t accept any sort of return and thank them for their honesty. No one should be punished for a mistake that was made in good faith.

### 7.1.4 Managed Services

Managed services are discussed in [Chapter 3](#c03.xhtml). It’s undeniable that using managed services is an essential component for a wide range of programs. However, what does the vulnerability triage process look like in the instance that an enterprise’s program managers allow a bug bounty platform to do so? Having a team of professionals makes a world of a difference when a program is bogged down with other cybersecurity incentives, and the ability to have someone validate a bug and give the researcher peace of mind is priceless.

In many cases, the program manager may wake up in the morning, log in, and find that a vulnerability is nicely triaged, and the triage team has exercised the liberty of cleaning up the researcher’s report so that the program manager can adequately and quickly reproduce. Arguably, managed services can even help reduce friction in the reporting process. Both small and large enterprises can benefit in multiple ways. For example, a large program may need a dedicated triage team through managed services because the alternative might be having to hire employees to manage the program at a rate that is significantly higher than using a bug bounty platform’s services. Alternatively, fewer employees can be hired for the triage process, and the current program managers can expand the program to focus on the validation portion of the reporting process. Smaller programs can typically get away with avoiding managed services, but arguably, the inexpensive nature and value of complex vulnerability validation can help smaller enterprises expand their security teams without spending too much time stuck in the triage loop.

Nonetheless, the same objective of validation must occur, whether the program includes managed services or not. We are all prone to error. If triage validates a bug, and assigns it to the program for resolution, revalidate and ensure it meets scope criteria

### 7.1.5 Self-service

The process of managing one’s own process from report to end isn’t impossible or improbable. When an enterprise chooses to do so, it’s safe to say that the triage and validation portions of the report can nearly be combined. However, program managers should be aware of the importance of separating triage or validation and impact assessments. Vulnerabilities should not be automatically triaged unless program managers are absolutely certain that it is a vulnerability and that there’s no question about it. If the vulnerability can wait, triage should always have a first look because a second opinion is a far safer option.

## 7.2 Bug Management

The entire report management process can take quite a bit of preparation and understanding to turn a clunky process into a smooth workflow. Even though every aspect of the process is important, the overall vulnerability management portion is the portion that the enterprise cares about above all else – it is the reason why the program exists in the first place. Try not to have a negative mentality or stress about the bug management process. Application security engineers are typically equipped to deal with bug bounty programs more effectively because of their experience in the software development lifecycle (SDLC), but realistically any cybersecurity engineer can manage this process with the right organizational setup.

### 7.2.1 Vulnerability Priority

Even though triage is responsible for the initial intake and validation of specific reports, it’s not their job to prioritize the vulnerabilities internally. A common misconception within program management is the taxonomy of triaged items. For the most part, vulnerabilities are accurately rated within the reporting processes. Nonetheless, a program manager should be careful not to use vulnerability taxonomy as something set in stone.

For example, please go to a search engine and look up the following CVE to evaluate: CVE-2020-14179. As it stands, this is rated as medium on the common vulnerability scoring system (CVSS) version 3.x scale. Obviously, as is known up to this point the criticality will determine the payout. The question is, what is the comparison of the CVE in the program versus the CVE in reality? Realistically, the vulnerability may be rated medium, but by reading the current description, it can be seen that it’s an information disclosure vulnerability and may be on the lower end of the scale. An attacker can essentially view field names and custom service level agreement (SLA) names on Jira tickets. The vulnerability may not be too serious in retrospect. However, the CVSS score is the typical scoring mechanism for bug bounty programs. Therefore, a medium would likely have to be paid (or at least recommended). The importance of establishing bounty pay ranges instead of set values shines in this regard because the Jira vulnerability can now be paid at the lower end of the medium scale in severity. Paying on the lower end of the scale shouldn’t be commonplace within a program. Program managers must always remember to stick to payout guidelines, and be fair to the researcher, especially if the vulnerability is a legitimate issue. Programs should not look for ways to pay a researcher less, but instead evaluate impact to see if a researcher should be getting paid more.

Now, compare the Jira vulnerability to a standard cross-site scripting (XSS) vulnerability. Regardless of what asset the vulnerability affects, an XSS vulnerability will always have more exploitation use cases than CVE-2020-14179, as long as it’s not considered self-XSS. An information disclosure bug isn’t as serious as being able to phish users and steal credentials, in nearly every circumstance (unless the information disclosure is sensitive, such as passwords, PII, etc.).

Take a look at three vulnerabilities and determine the order in which these should be resolved. Rate them on a scale between 1 and 3, where 1 is the highest priority and three is the lowest:

### 7.2.2 Vulnerability Examples

#### 7.2.2.1 Reflected XSS on a login portal

##### *Report and Triage*

A researcher found a XSS vulnerability on the login portal by abusing a native parameter. They are able to pop-up alerts, and the proof used the classic <script>alert(1)</script> technique. The alert is triaged by managed services as a medium rated vulnerability.

##### *Validation*

The program is able to validate the vulnerability as a legitimate XSS vulnerability.

#### 7.2.2.2 Open redirect vulnerability

##### *Report and Triage*

The same researcher finds a vulnerability that allows them to redirect users to any website, with no restrictions. Additionally, the researcher notes that they are able to check if specific ports are open and are closed on the backend with the URL “http://127.0.0.1:port” appended to the path. They reported it as an open redirection vulnerability because they are having a difficult time telling if the ports are actually opened or closed – it’s just the researcher’s guess. The alert is triaged by managed services as a medium rated vulnerability, as they could not validate any sort of service-side request forgery vulnerability.

##### *Validation*

The program is able to validate the open redirection vulnerability. Additionally, they’ve noted that the ability to enumerate internal ports and even see contents of specific files is possible through testing.

#### 7.2.2.3 Leaked internal Structured Query Language (SQL) server credentials

##### *Report and Triage*

Lastly, a vulnerability was found in which the enterprise’s public GitHub repository appears to be leaking credentials for a My Structured Query Language (MYSQL) server over port 3306. Triage is unable to validate the authenticity, as the credentials appear to be accessible from the internal subnet only.

##### *Validation*

The program validates the existence of the credentials, and has determined that the exposed internal credentials are legitimate. However, the program, in keeping with best practice, determines that this vulnerability is rated at a medium rated vulnerability.

## 7.3 Answers

In the three given scenarios, the results are ranked from least to most pertinent, along with an explanation of why.

### 7.3.1 Vulnerability Rating-test Summary

The truth is, the perception of how vulnerabilities are handled has some room for flexibility, and it’s impossible to set strict guidelines. What triage considers critical may only be a medium for the enterprise. If the leaked internal SQL server credentials example were for a critical asset such as a database that held credit cards, or PII, would the priority change? Understanding that the taxonomy and priority of vulnerability remediation may change/have to change is an essential part of program management.

**7.3.1.1 Reflected XSS in a login portal**

The reflected XSS vulnerability ranks below the open redirect that escalates into an SSRF. Realistically, the ease of exploitation and possibility of phishing credentials can be highly disruptive to the business and causes a lot of strife and impact in the enterprise’s security process. An XSS, in most cases, ends up as a true medium unless the researcher manages to escalate the vulnerability to an instance of account takeover.

**7.3.1.2 Open redirect vulnerability**

While this vulnerability starts out as a low-impact, redirect based-scenario, the researcher was able to turn it into a server-side request forgery vulnerability by attempting to enumerate ports. Additionally, the program manager was able to read other files, turning a low-impact vulnerability into a high-impact vulnerability. In this instance, it would be recommended to escalate the researcher’s vulnerability from a low to a high since they identified the possibility of the SSRF attack. However, this would not be considered critical, because no further escalation had occurred from the researcher’s part. Resolving this issue first would be the best recommendation to prevent critical exploitation or data leakage.

**7.3.1.3 Leaked internal SQL server credentials**

While at first glance the internal SQL server exposure may appear to be the most critical vulnerability, if anything, it’s either equally as vulnerable or less than the instance of the reflected XSS. An enterprise shouldn’t sleep on a vulnerability that’s considered internally reproducible only, though. In the instance legitimate internal credentials are exposed, even if the researcher cannot access them, tell the affected team to rotate the credentials immediately. A common misconception about internal credentials is that it’s not problematic because a security researcher cannot get onto the network; this couldn’t be further from the truth.

### 7.3.2 Complexity vs Rating

No one can thoroughly define how the enterprise should manage different vulnerabilities. Generally, there’s a baseline. But as we’ve seen, a baseline is just that: an outline of a recommended approach. Alternatively, a good way to address various issues is to compare all of the factors, starting with the complexity of the vulnerability and the rating.

*   **Complexity**: how difficult replicating a vulnerability is, with respect to how difficult the vulnerability would be to replicate by an unskilled threat actor. Imagine that the rating scale ranges from very easy, to easy, medium, hard, extremely hard.
*   **Rating**: the severity or impact of a vulnerability that is exploited by a threat actor. The rating scale can be realistic, in one of these categories: non-applicable, informational, low, medium, high, critical.

The baseline for evaluating vulnerabilities against complexity and rating doesn’t have to use strict wording, nor does it have to be included in the bug bounty program’s description, or even written down. It’s meant to be a mental note to keep in mind while evaluating vulnerabilities for triage priority as well as helping during the logical process of working through reported bugs when monetary ranges need to be evaluated.

To understand how the complexity and rating scales are used in conjunction with each other, note the following two separate examples and compare them.

1. Stack based buffer overflow on example.exe resulting in remote code execution.

A vulnerability was identified in which it were possible to perform a buffer overflow exploit against the example.exe file offered by [company.com](http://company.com).

2. Local file inclusion (LFI) vulnerability led to remote file inclusion (RFI) resulting in remote code execution.

A vulnerability was identified in which the foo.php?page = parameter suffered from a local file inclusion vulnerability. When a payload of ../../../../../../../etc/passwd was appended to the end of the parameter, the vulnerability was exploited. Additionally, swapping out the LFI payload with a PHP input wrapper (php://input) and modifying POST request data to include <? system(‘uname -a’);?> resulted in full remote code execution on the system.

### 7.3.3 Projected Ratings

### 7.3.4 Ticketing and Internal SLA

The process of creating tickets and managing internal service level agreements that are defined within the enterprise is a unique, yet important, aspect of information security. During the ticket creation process, engineers managing the bug bounty program should use any integrations to ticket systems that the bug bounty platform may offer. Or in the unique instance that the enterprise is self-managing a program, engineers should define SLA management processes, which is discussed further in [Chapter 9](#c09.xhtml).

#### 7.3.4.1 **Creating Tickets**

The vulnerability triage and validation process doesn’t necessarily require program managers to make tickets internally. Managed services and triage employees cannot partake in such incentives. Normally, after the process of validating vulnerabilities and deeming them as reproducible and legitimate, first things first: *pay the researcher* if the vulnerability is valid, and due diligence has been performed to validate the issue. Obviously, ensure that the possibility of accidentally paying for a vulnerability that isn’t valid doesn’t exist before paying the researcher, as discussed previously.

Once the researcher is paid, connectors that integrate into most ticketing platforms will do the work of generating the report for the program internally. However, in some instances, the ticketing integration may not support the inclusion of the entire report. For example, as a bare minimum, a program will want to make sure of the following.

1.The ticket contains fully detailed steps.

If triage or the security researcher writes steps that an application security engineer can understand, it doesn’t necessarily mean that a software engineer will understand the same steps. Translate any complex processes into easy-to-understand replication examples, something that someone who has limited technical experience may understand.

(Software engineers are highly technical, but understanding the exploitation process may require a different level of understanding.)

2.The ticket contains relevant files.

In instances of exploitation where the security researcher uses an externally hosted file for a proof of concept, such as an HTML file, include this in the ticket. An engineer’s time is valuable. Internal teams should not have to create any exploitation processes from scratch. If the researcher did not include the file, either ask for it or include the file that was used for validating the vulnerability.

3.The ticket contains proofs.

Security researchers tend to include screenshots/videos of exploitation. If there’s reason to believe that the exploit may be too complex to detail in several reproducible steps, be sure to include the material used to detail the exploitation process.

4.Additional information.

Program managers should include any relevant information that wasn’t parsed via the ticket integration functionality.

# 8   
Vulnerability Disclosure Information

## 8.1 Understanding Public Disclosure

Program managers will typically have the ability to allow security researchers to disclose their findings after the issues are fixed. Allowing public disclosure of vulnerabilities isn’t necessarily a program requirement, and program managers should be aware of any implications that may occur because of disclosure. Public disclosure, as it pertains to bug bounty platforms, is simply the act of allowing the report to populate via public feeds. It would be safe to assume that a report disclosed on the feed could possibly leave the platform in the form of writeups on the researcher’s website, social media posts – or even journalists writing on the vulnerability.

### 8.1.1 Making the Decision

Ultimately, the decision to allow public disclosure depends on the objective of the program. The control of vulnerability remediation transparency (allow/deny) is up to the discretion of program managers. Still, it’s important to understand that public programs have their own unique challenges in this process.

#### 8.1.1.1 Private Programs

There are two ways that private programs can deal with vulnerability disclosure: one represents a standard built-in configuration use case, while the other is more of a decided-upon courtesy in support of the security researcher’s efforts. Ultimately, it will also depend on the configuration allowances that a crowdsourcing platform determines. In most cases, private programs will have the ability to allow disclosure, although it’s slightly different than what a program manager would expect from a public program.

1\. Allowing Disclosure

The option to allow disclosure has to come from a place of understanding a security researcher’s mentality, but also one of the potential enterprise impact. For example, consider the following.

A researcher works with the enterprise bug bounty program on a critical issue, one in which they could have been able to acquire hundreds of thousands of pieces of PII. Acting in good faith, the security researcher stopped when they had access to the server, to avoid any accidental disclosure of PII.

If disclosure is allowed, most crowdsourcing platforms have policies in place where the only people that can view the disclosed (and patched) vulnerabilities are the other security researchers who have been invited to and are participating in the program. While most security researchers will have respect for the processes put in place for preventing disclosure of the vulnerability outside of the organization, that may not always be the case. A program manager shouldn’t be presumptuous, but associated risk should be known.

The security researcher who found the vulnerability may not have any intention on the disclosure leaving the “feed” or “stream” in which it was shared with other researchers. If the enterprise is running a private program and participating in limited private disclosure, another researcher may take the report or the findings and leak the report to a journalist or online elsewhere. While the risk of such leakage occurring is exceedingly low, no one should ever assume that it could never happen. Ultimately, the damage that would be caused is one of reputation and not of exploitation as the vulnerability would be fixed. However, in reality, disclosure shouldn’t be looked at as a means of reputation damage. When a program encourages disclosure, the community respects the enterprise far more.

2\. Disclosure Restrictions

Program managers may decide to avoid disclosure altogether. In any case, the primary occasion in which an enterprise may not want limited disclosure may be due to fears of further exploitation or information leakage, outside of the control of the security researcher or program management.

Disclosure restrictions, at least from the perspective of program managers, are typically a result of immaturity in the bug bounty space. The exploitation of any disclosed report is improbable unless the report reveals more infrastructure or internal information on the program’s private researcher feed. In any case, the information can typically be redacted prior to disclosing.

3\. Ad Hoc Redactions

A lot of researchers participating in a private program will want disclosure, no matter what policy is currently in place. Security researchers may ask to redact information to be able to include it in their writeup. Instances where disclosure of this form is requested can occur if the enterprise’s program only allows private-stream disclosure, or if the program allows no disclosure.

##### *The Bottom Line*

Security researchers value their research. If redaction can be done to support a researcher’s disclosure, it would be a good incentive to do so in support of their participation. A program manager can write a clause in their program, or respond to researchers if asked, with the following:

“We will allow public disclosure in writeups. However, please give us the chance to review the writeup to ensure that no potential vectors for exploitation exist. We want you to share the research, but we would like to keep the company safe. We do not want to be overbearing, therefore it will be a light review. If you would prefer not to allow us to review the writeup, we understand and respect the value that you bring to our company. Disclose at will.”

In most cases, a statement of support as defined above will be an adequate method of support for the security researcher’s findings. Without falling subject to the fallacy of a slippery slope, completely preventing any form of public disclosure isn’t useful methodology. Researchers who are avid writers that participate in the public-facing bug bounty community will end up disclosing, and this could result in accidentally disclosing internal information or infrastructure outside of the visibility or control of a program. Nonetheless, while it is an option to ask for redaction of specific aspects of the writeup, this should not be weaponized against a hacker. Redaction should only be done in a way that prevents further exploitation of the service. If a program manager does not feel comfortable with a researcher disclosing their research, they should aim to either improve security or refrain from operating a bug bounty program.

#### 8.1.1.2 Public Programs

The subject of public programs represents a different challenge, the “anyone can do it” effect. In other words, an enterprise bug bounty program manager may find increased participation if participating researchers are allowed to disclose. Nearly all aspects of disclosure from private programs carry over to the configuration in public programs, with the exception of one additional feature that is reserved to public programs: full public disclosure.

1\. Full Public Disclosure

Public programs have the ability to fully commit to the most permissive state of programs: full disclosure. Essentially, when an enterprise program is configured to have the disclosure feature in a public state, security researchers can request disclosure of their patched vulnerabilities, and that means the vulnerability will hit a highly visible state, one in which any person who accesses the crowdsourcing platform can completely see the report (with the desired redacted information).

One of the primary issues with fully public disclosure is the representation of a program’s value and the possibility of increased participation (the anyone can do it effect). Basically, there are several scenarios in which full public disclosure can result in an excessive uptick of participation, primarily when a program discloses a vulnerability that resulted in a big reward or the program releases a chain of reports.

Payday mayday, or in summary, is the disclosure of a report in which a researcher has earned a significant amount of money, which could result in possible press. It’s not unheard of to have a journalist write on the subject of a patched vulnerability, especially if it could have resulted in a significant exploitation or compromise of a user’s data or a company’s product. If a journalist picks up a vulnerability report and writes about it, a surge of researchers may rush to the program hoping for their shot at a big payday. Even though the instance of a vulnerability as critical as the disclosed one being found after the previous one was disclosed is unlikely, it’s not impossible. Secondly, a burst of smaller vulnerabilities may be reported, or even if no greater-than-average amount of vulnerabilities get reported, there could be enterprise disruption as a result of a lot of security research activity being conducted. It’s not a matter of fact that the vulnerability will be picked up by a journalist, but all scenarios should be considered.

Chain report disclosure may not result in press exposure, but comparatively, some similar effects seen in a high-payout scenario could possibly occur, particularly increased security researcher participation or disruptive levels of activity that the enterprise isn’t ready to manage.

##### *The Bottom Line*

Program managers should allow public disclosure and realize that they need to be prepared to deal with a spike in reports, and have thoroughly hardened assets. The public disclosure process shouldn’t be discouraged. However, if the enterprise is not comfortable with disclosure, realize that it’s an uncomfortable event that program managers must get comfortable with. After all, even if the enterprise did not have a program, they face hackers disclosing vulnerabilities to the public. A program at least gives the chance to encourage positive rhetoric and rewards around reporting, giving program managers an edge. Allow researchers to disclose, or do not run a bug bounty program.

## 8.2 CVE Responsibility

### 8.2.1 What are CVEs?

CVEs stand for common vulnerabilities and exposures. The CVE program was developed in 1999 and is sponsored by the US Department of Homeland Security and the Cybersecurity and Infrastructure Security Agency. CVEs were meant to be used as a way of standardizing vulnerabilities and disclosures, linking many databases together in an attempt to make it easier for enterprises to manage and patch newly identified vulnerabilities.

### 8.2.2 Program Manager Responsibilities

A difficult aspect of bug bounty program management is to be on the lookout for CVEs, always. When the enterprise’s product is involved, it could be more obvious that a CVE exists within the product if it requires patching a specific component that is used outside of the company. However, there are multiple instances that exist in which a CVE may be overlooked, and it’s usually due to a lack of knowledge of the security research space. Both a security researcher and a program manager could end up overlooking the widespread impact of an identified vulnerability.

### 8.2.3 Hardware CVEs

An enterprise may offer a wide range of hardware, for instance in the case of the ISP their product could be a cable box or a router, and so on. If testing on routers were in scope, a researcher who finds a vulnerability within the router has likely successfully identified a CVE, but as stated, they may not know that the bug is a CVE which has a wider range of impact. Maintaining vigilance is important to ensure that the enterprise reduces impact and exploitability.

In most instances, CNAs aren’t a resource that the majority of program managers will be able to utilize. Instead, follow the guidelines outlined in Section 8.3.2.

### 8.2.4 Software and Product CVEs

The same ISP may have a premium video streaming service that’s served via an application that users may purchase as an addition to their monthly bill. The application is served via a connection that is made externally over the Internet, and isn’t a web-based asset. In fact, it’s downloaded as an executable (.exe) file, with a separate version for MAC (.dmg). Additionally, the application allows users to create accounts and share their video lists with other users, and view recent activity on their profile page.

### 8.2.5 Third-party CVEs

In the previous two scenarios, the requirement for public vulnerability disclosure and patching was presented directly to the organizations, but what happens in the circumstance that it’s not clear? In the example scenario with the ISP, one could now imagine that their web application is using a wide array of third-party software integrations and code. For this specific scenario, let’s create two fictional company names – Ryudar the ISP and AppAncors, a vendor they use for link anchors and redirects.

## 8.3 Submission Options

Whether it’s the responsibility of a program manager to submit the vulnerability or not completely depends on the vulnerability submitted and the coordination that takes place. There are several options for reporting the vulnerability, and it’s subject to change. Program managers should understand the various scenarios that can occur during the reporting process and realize that CVE management is dynamic. As always, the best interests of both the enterprise bug bounty program and the researcher should be kept in mind at all times.

### 8.3.1 In-house Submissions

The standard in-house submissions are usually the easiest because they defer to internal processes that have already been established (i.e. CNA). If a program manager is confused about whether their enterprise is a CNA, they should refer to the comprehensive list of CNAs ([https://cve.mitre.org/cve/request\_id.html#cna\_participants](https://cve.mitre.org/cve/request-id.html#cna-participants)), and keep in mind that the probability of an enterprise having a CNA without the security team knowing about it is fairly unlikely. If the enterprise does indeed have a CNA, best practice would be to patch the vulnerability, and submit the CVE via the reporting system that the CNA has access to ([https://cve.mitre.org/cve/cna/Requesting\_Blocks\_of\_CVE\_IDs-for\_CNAs\_only.pdf](https://cve.mitre.org/cve/cna/Requesting-Blocks-of-CVE-IDs-for-CNAs-only.pdf)) if the enterprise running a program has a large enough use case to become a CNA, please use the following form:

([https://cve.mitre.org/cve/cna.html#become\_a\_cna](https://cve.mitre.org/cve/cna.html#become-a-cna))

### 8.3.2 Program Managed Submissions and Hands-off Submissions

An enterprise should allow the researcher the opportunity to submit the CVE themselves if they so wish. However, ask the researcher if they would allow the program to disclose on their behalf. Realistically speaking, the program reserves the right to do so because of the bug bounty program nondisclosure agreements, but they should not be depended on exclusively.

#### 8.3.2.1 Program Managed Submissions

If a vulnerable component is identified that may affect more than just one user and requires a CVE disclosure, follow a set of submission steps.

Steps to Submit<query id="Q5"> <p>Dear TS, This is a list heading for the following numbered list. I do not know the tag for that.</p> </query>

1.  First, tell the researcher that the vulnerability has been identified as a CVE (if this wasn’t in the program).
2.  Tell the researcher that you would prefer that the enterprise goes through the submission process, but ask if the researcher is okay with that.
3.  If the researcher does not establish a deadline, offer 90 days for the patching process before submitting. If the vulnerability will likely be much sooner, be sure to express that. It’s probable that the researcher will disclose far sooner than the full 90-day period, especially if the issue is critical.
4.  The program manager should first coordinate with the appropriate internal team to ask them to fix the issue. Next, the program should go to MITRE’s website and submit the official CVE ID request form.
5.  When MITRE processes the request, a CVE ID will be assigned and they will wait for references, or in other words, a proof of concept or advisory from the affected party, confirming a fix.
6.  Program managers can submit the references via replying to the CVE assignment email, and then MITRE will publicly publish the CVE. If timing permits and the researcher has taken responsible measures, the actual bug bounty report can be disclosed and used as the primary reference.

**Note: social media handles or temporary posts on social media are insufficient references. In order to protect the enterprise, at a minimum, submit one reference from the enterprise such as a bug bounty report, patch notice, or GitHub pull request, and so on.** <query id="Q6"> <p>Dear Typesetter, Please set as Note text.</p> </query>

#### 8.3.2.2 Hands-off Submissions

If after collaboration, the program and researcher agree to a self-submission approach, the security researcher is agreeing to manage interactions. There are several instances in which this would occur. For example, a vulnerability identified on a third party would constitute a hands-off approach, and this would likely be non-negotiable on behalf of the researcher as it’s not the responsibility of the enterprise to disclose vulnerabilities for products they don’t own. Program managers should let the researcher know that they will have to contact the affected party. Additionally, there’s the possibility of a researcher wanting to disclose the CVE to MITRE themselves. In this instance, discuss how it can be done safely, and kindly ask the researcher to provide the proposed submission to MITRE. Validating the submission will adequately enable the enterprise bug bounty program to ensure that the security researcher is effectively describing and capturing the vulnerability, affected version, or severity levels.

**Note: do *not* attempt to provoke the security researcher or threaten legal action. Attempt to understand the case for disclosure, and so on. Mitigating negative interactions is an essential part of provoking positive research, as markets where researchers can sell CVEs exist. The researcher chose to adequately report an issue that may have been worth a lot of money otherwise.** <query id="Q7"> <p>Dear TS, Please set as Note text.</p> </query>

Once the form is submitted, typically the organization will patch and then provide a patch notice or writeup (aka references) to MITRE and then MITRE will officially release the CVE to the public.

# Part 5   
Internal and External Communication

# 9   
Development and Application Security Collaboration

## 9.1 Key Role Differences

The application security and development roles are vastly different in both workflow and responsibility. Obviously, depending on the enterprise, the roles can vary dramatically and the enterprise program may be composed of information security practitioners, and not necessarily application security engineers acting as bug bounty program managers.

### 9.1.1 Application Security Engineer

During the program process, application security engineers are responsible for the consistent evaluation of security programs as it pertains to the enterprises applications such as websites, mobile apps, and third-party reviews, especially if partners use any of the applications in a privileged manner. Typically, an application security engineer will be responsible for the security during the development of the applications and all of the processes involved.

### 9.1.2 Development

Primarily, software engineers will acquire the brunt of the workload involved with remediating vulnerabilities that have been established. However, that’s not always the case. Depending on the identified issue, application security engineers will find that they may have to collaborate with other teams, such as cloud security or infrastructure teams, to resolve identified vulnerabilities. The resolution of vulnerabilities does not solely fall into the bracket of software engineering.

**Note: even though application security engineers are responsible for evaluating and remediating security issues, the various application creators and maintainers must exercise good secure coding practices.** <query id="Q1"> <p>Dear TS, Please set as Note text, and the same as earlier chapter&#39;s style, including to bold or to roman.</p> </query>

## 9.2 Facing a Ticking Clock

It shouldn’t come at a surprise that the responsible program managers will have quite a few hurdles to face when dealing with vulnerability remediation. Obviously, the expectation to resolve the identified vulnerabilities comes from both the security researcher and enterprise program perspective. For example, if multiple identified vulnerabilities are validated, ensuring that criticality is prioritized is an absolute necessity, and will help in the ticking clock also known as a service level agreement (SLA). Researchers are eager to resolve issues, and program managers will likely be facing anxious researchers constantly asking for updates. While a swift resolution isn’t guaranteed in all scenarios, the important part is ensuring that both researchers and management understand the level of effort required.

Imagine a scenario in which a vulnerability was identified that has a recommended remediation timeline of two full weeks. Program managers should be proactive about the resolution and communicate any blockers to anyone involved. If a researcher expects updates throughout the period and receives zero updates, they will get discouraged. They will become even more discouraged if the expected service level agreement time isn’t met. Instead of apologies post-failed criteria, it doesn’t hurt to update the researcher before the missed deadline, explaining various blockers in the resolution process. The program manager responsible for facilitating communication doesn’t necessarily have to divulge too much information about the blockers, but an update is usually appreciated.

In conjunction with keeping researchers updated, program managers must prioritize blockers to leadership. If leadership has to consistently ask for updates on vulnerabilities, it can impact the workflow and create an unnecessary sense of urgency for the teams responsible for patching the identified vulnerability. If leadership has to intervene during the remediation process too often, software engineers or other responsible development parties may feel as if vulnerabilities are being blown out of proportion when collaborating in the future.

## 9.3 Meaningful Vulnerability Reporting

Often, engineers make the mistake of relaying reported vulnerabilities to software engineers in an overly technical way. Even though software engineers are highly technical individuals, exploitation is a different art and in some instances the vulnerability may be overlooked or misunderstood if reported incorrectly. As anything, program managers should learn how the different teams within the organization operate and adjust according. How does one define “overly technical”? First and foremost, it’s unlikely that a software engineer would ever admit to a report being outside of their range of understanding. There’s no specific threshold for a report being too technical. Therefore, program managers should strive to relay vulnerabilities in a way that everyone can understand. There’s no such thing as a report being “too easy to understand.”

Compare two excerpts from the same report, translated with two separate summaries, and notice differences in the effectiveness of the following relayed report.

Even though both of the summaries are true, Report 2’s summary is friendlier for presentation to a software engineer or other development team. Paired with easy-to-understand steps, Report 2 will surpass the presentation of Report 1. Communicating the information in a concise way that gets to the root of the vulnerability is essential to prevent mishaps or delays in any of the resolution processes. The replication steps should be written about in a similar sense. When attempting to summarize the replication steps, refrain from using highly technical terms if there’s an easier way of explaining things. Although there isn’t a set way to accomplish this, two ways a program manager can alleviate the stress of a software engineer or other responsible party from feeling bogged down are minimizing the number of steps it will take to replicate the vulnerability or, if all the steps are necessary, avoiding acronyms and providing the “why” a bug is a particular issue.

For example, a software engineer may be familiar with the term “XSS” but when a program manager first starts, they should expand upon the abbreviation, (cross-site scripting). In addition, an engineer may not know what cross-site scripting is. Typically, a quick blurb, such as: “Cross-site scripting (aka XSS) is a method in which an attack can steal information from a user via social engineering,” is a good way to explain quick risk. Refer to the OWASP Top Ten guide to understand a little more about application vulnerabilities ([https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)).

## 9.4 Communicating Expectations

One of the ways program managers risk hurting the potential for success in an enterprise bug bounty program is with unrealistic expectations or being too lax in management processes. Program managers should maintain a balanced approach to achieve the best possible outcome, adjusting based on the severity of the vulnerability. It’s typically unwise to set high expectations on a low severity vulnerability, as it can potentially damage the relationship between the program manager and responsible remediating party. Similarly, setting low expectations can cause just as much harm to the program’s reputation, especially if engineers don’t believe they are being held accountable to fix the issues. Whatever timelines are agreed upon, both software development managers and security managers should have full oversight of the remediation process to prevent any unnecessary disagreements.

In addition, encourage software engineers to add comments to any vulnerability tickets to update the application security team of progress. While not every software engineer has a workflow that includes consistent communication via comments, the idea in mind is to maintain an open dialogue in the resolution process. No single software engineer is alike and program managers should strive to make determinations of all of the effective communication processes and adjust accordingly.

## 9.5 Pushback, Escalations, and Exceptions

The responsibility of professional accountability falls on the program manager. Whether discussing timelines provided for software engineers or executive management, the one key point of understanding is to know that, no matter what, the program managers will be held responsible for the remediation of any vulnerabilities. Since program managers are held accountable, understanding when to escalate on responsible parties is a necessary truth, but it doesn’t have to be a toxic interaction. For example, imagine that a software engineer was given two full weeks to remediate a SSRF vulnerability. During the process, the program manager communicates expectations and the software engineer immediately says, “I’m not going to have enough time to fix this. This incentive needs to wait until the end of the month.” Realistically, since the vulnerability is rated as a high severity with the potential of easily turning into a critical, the remediation process cannot afford to wait too long. While it may seem embarrassing to talk about how to talk, a bug bounty program will fail if program managers don’t have the power to push back. The most effective way to ensure the bug bounty program is taken seriously is to define steps and methodologies internally and externally, that everyone can refer to.

### 9.5.1 Internal steps

*   Develop a team board or way to track resolution processes. It can be as simple as a list of tickets and due dates, or as extensive as full story tracking, such as with the capabilities that agile methodologies bring to the table.
*   Create a playbook as a means of explaining processes. Executive leadership may not be heavily involved in the application security workflows. A playbook can be an excellent way to present key pieces of information, such as company policy on vulnerability resolution expectations, managing issues or exceptions, and so on. In addition, more information can always be worked into the runbook to elaborate on any defined workflows to junior engineers who may not have had to deal with security issues.
*   Reiterate the processes to responsible impacted teams, even if it’s believed that the team may know what they are doing. For example, a simple: “Hello, we identified a vulnerability with X component on X application. The expectation is to get this resolved within (X weeks or months) as the criticality of the vulnerability is (low/medium/high/critical) and might result in negative possibilities if exploited by a threat actor.” Program managers will find far greater success if thorough yet useful expectations and risk analyses are conducted and relayed in a meaningful way.

### 9.5.2 External steps

*   Establish SLA times within the bug bounty program description to hold internal teams accountable for resolution, ideally something that meets or is close to internally defined times.
*   Exclude security researchers from internal communication processes. It’s important to prevent any advanced oversight of the relationship between the program manager and different development aspects of security. The program manager’s main priority is to validate, resolve, and pay researchers for vulnerabilities. Therefore, it’s pertinent to prevent speculation or demotivation.

### 9.5.2 Escalations

To be completely transparent, it may be difficult or even feel discouraging to have to deal with engineers who are not apt to maintain a good vulnerability resolution track record. As an information security professional, managing relationships with nonsecurity personnel will always be difficult. Whether the issue at large is miscommunication, demotivation, or disrespect, speculation can be harmful and permanently damage relationships with colleagues who will inevitably have to assist if any vulnerabilities are identified in their space. Evaluate the following scenarios of communications between a senior application security engineer and a software engineer and read the various analyses, noting which situations may need escalation depending on the program manager’s leadership style, defined resolution times, and preferences.

1.  *Scenario: miscommunication* Shanice talks to Ricardo about an XSS vulnerability that has been identified. She notices that the ticket hasn’t been updated with any progress and the deadline indicates that the ticket is two days overdue. In addition, a week prior to the deadline Shanice informed her manager that she believed Ricardo might miss the deadline, and her manager is informed that she will be looped in on Shanice’s follow-up emails. She has talked to Ricardo and his manager on multiple occasions about the deadline via email, in which Ricardo’s manager responded with a claim that it would be finished in time.  
     **Analysis:** Shanice maintained the right principles throughout the process but overall there’s still a level of disconnect between the application security team and the engineering team. Shanice has followed up with the team on multiple occasions to check on the progress of the work, and the responsible team has reassured her that it would be taken care of. Even though assurance was provided, the responsible team did not contact Shanice about the possibility of missing the deadline, even with her manager involved in the interaction. In this particular scenario, Shanice should make a recommendation to her manager that escalation to the next level of leadership should occur. Typically, this would have been best addressed several days prior to the missed deadline. However, responsibility isn’t always claimed and program managers must maintain some level of responsibility for failures of miscommunication as well.
2.  *Scenario: Demotivation* Shanice receives a message from James stating that he’s having a lot of issues resolving the sensitive information disclosure vulnerability that was assigned to him. James also seems to be stressed out about the 30-day timeline resolution requirement, stating that it’s difficult to prioritize and resolve this. Shanice doesn’t specifically know how to resolve the vulnerability, but she knows that another software engineer, Rachel, has dealt with this issue. Shanice offers to have a call and bring Rachel on to advise. Reluctantly, James accepts the meeting and allows Rachel to talk him through the resolution process. Shanice interjections about timelines and expectations where needed.  
     **Analysis:** Shanice made the right call. Rather than scorn the engineer for not knowing how to fix the vulnerability, she decided to kindly reach out to another engineer and coordinate a meeting with James. In this specific scenario, Shanice did not need to escalate, because there was plenty of time remaining for the resolution process and a lack of any major issues.
3.  *Scenario: Disrespect* On a Friday, a security researcher identifies a critical remote code execution vulnerability. Shanice gathers all of the information, and immediately reports it to her manager, who also informs the chief information security officer. The affected team, the API development team, only has two employees (a manager and Jaycee, the principal software engineer). Shanice reaches out to Jaycee about the vulnerability and is ignored for several hours. After finally touching base with the engineer, Jaycee responds and states she doesn’t believe the vulnerability really matters, and that she has higher priorities. Shanice explains why it matters, in a professional manner, and Jaycee escalates – stating that she has better things to do than deal with this and she can wait until Monday morning. Quickly, Shanice tries to refute this, but Jaycee stops responding. Jaycee’s manager catches wind of the situation and tries to work it out with Shanice, but ultimately agrees that the team doesn’t believe it matters and that the team’s workflow is already heavy.  
     **Analysis:** in this situation, Shanice approached the scenario correctly from a professional perspective, but could use a bit of guidance on proper escalation procedures. Explaining the criticality and why a vulnerability matters to software engineers is an essential skill that all program managers must acquire. However, this scenario seems particularly heated, at least from Shanice’s perspective. When a scenario becomes negative enough that a software engineer believes they can say no and ignore the security team, a program manager should immediately escalate to leadership. When a vulnerability is critical enough, program managers should put reservations of escalation aside and think about the security of the enterprise. Failure to remediate quickly could be enough for an organization to fail to protect user data, infrastructure or other key components of the organization.

### 9.5.3 Summary

The scenarios described in the examples are not the only issues that can happen in the bug bounty resolution lifecycle. The key takeaway is understanding that program managers must appropriately use critical thinking to adequately think on their feet and resolve issues in a logical manner. It’s not appropriate to unnecessarily escalate issues that can be resolved or ignore issues that should clearly be escalated. Maintaining a kind but fair approach is the best way a program manager can operate the bug bounty program successfully, throughout the entire lifecycle.

## 9.6 Continuous Accountability

Program managers have an obligation to follow up in the vulnerability remediation process. Assigning vulnerability tickets to affected teams with no due date, or not actually following up with the teams for remediation, is a simple way to burn money and tank a bug bounty program. Security researchers will want their issues to be resolved, but this cannot happen when teams are not being held accountable. Although a close relative of the category of escalation, continuous accountability is the full responsibility of the program manager.

### 9.6.1 Tracking

Proper accountability is more or less a matter of ensuring that all of the vulnerabilities that have been communicated are tracked from start to finish. It’s highly recommended to use the ticketing processes described in [Chapter 7](#c07.xhtml). Technically, a program manager can maintain vulnerabilities however they want, but ticketing systems such as Jira are the preferred methodologies to maintain full oversight of any blockers in the vulnerability resolution process.

### 9.6.2 Missed Deadlines

In reality, it would be extremely unfair to assume that a bug bounty program will maintain the SLA in every scenario. Even the best program managers can possibly miss a deadline, and the same can be said about the top software engineers. Life happens, and the vital takeaway piece of information is to remember to stay calm in the instance of a missed deadline. A few key steps will prevent a missed deadline from turning into a disaster:

1.  First and foremost, notify leadership. Bug bounty programs cannot be effective if transparency isn’t maintained. However, don’t notify leadership without a plan, and there’s no need to escalate if there’s a fairly good reason for why the deadline was missed. For example, if a software engineer did not meet the deadline by a day because of something else that went wrong in the production environment, generally speaking a program manager would notify leadership of the deadline. However, if, for instance, the program manager forgot about a vulnerability and then it was two months overdue, transparency with leadership is essential. Being honest is of paramount importance.
2.  Communicate about the issue. Maintain communication with the appropriate team to resolve the issue. Inform them that it’s overdue and explain the importance of fixing the vulnerability.
3.  Notify the researcher. Obviously, letting the researcher know that the resolution is in progress is important. However, this is not nearly as important as actually fixing the issue or notifying leadership of any blockers in the resolution process.

# 10   
Hacker and Program Interaction Essentials

## 10.1 Understanding the Hacker

A program manager should never automatically assume that the hacker holds “x” intention. Security research is delicate, but the common misconception is that hackers are motivated by money. Many program managers don’t understand the value of security research until they’ve been managing a bug bounty program for a while. Understanding why a hacker participates isn’t always as simple as it seems.

### 10.1.1 Money, Ethics, or Both?

Hackers’ motivations vary. Some hackers are from countries where the value of the US dollar scales exceedingly well with their local currency. Therefore, even smaller payouts can work wonders. Researchers that are motivated to work for money aren’t necessarily unethical, and shouldn’t be viewed as such – after all, bug bounty hunting is a day job for many across the world. Bug bounty program managers should consider the possibility that the security researcher reporting the vulnerability could rely on it as their primary source of income, and treat all researchers as full-time professionals. The suggestion to consider full-time bounty hunters’ need for money isn’t affirmation to pay for invalid bugs, simply something to remember when realizing the amount of power that program managers amass. There’s nothing wrong with a security researcher being financially motivated. A program manager should not be fearful of a researcher who approaches and immediately asks about financial reward. The researcher could mean well, and that most often appears to be the case. Always be wary of exploitation attempts, but presumptions of a researcher’s bad intentions can be detrimental. Always gather information first.

Believe it or not, there are security researchers out there that could care less about money. Several components exist that are worrisome in this regard. For one, it’s undeniable that researchers that could care less about money are fairly easygoing people. It takes a lot of spirit and commitment to hacking in order to be transparent and honest enough to disclose a vulnerability to a program, knowing right well that a payment for research may not be provided (for an out-of-scope or disqualifying vulnerability.) Easygoing researchers may lull some project managers into a belief that they don’t need to be too forthcoming with payments, and this can jeopardize the future of vulnerability research. Imagine that program managers become used to a handful of researchers who are easygoing and decide to report vulnerabilities, even if they are out of scope, and don’t express any interest in payment. Researchers can inadvertently lead to programs not expanding the scope or program managers opting out of bug bounty programs to offer proprietary programs where no rewards are offered. One could argue that it’s a fallacious line of thinking, possibly even a slippery slope. However, the point here is to ensure that security researchers receive their due. If a researcher reports a vulnerability that’s in scope but says, “You don’t have to pay me,” it is still always best to respond with “Are you sure? We would really like to pay you for your efforts.” Giving the researcher the opportunity to at least be rewarded for their work can help avoid corruption or unrealistic expectations creeping into a program based on past experiences with easygoing researchers.

The in-between are researchers who represent both a desire for money and a willingness to ignore the monetary aspect if push comes to shove. The majority of researchers tend to fall into this category of hacking. Researchers that don’t hack for the money, or for the pure ethics of the craft, are known as in-between researchers. Money doesn’t usually come into the argument; however, the in-between researchers don’t necessarily say no to adequate payment.

However, it’s not unusual to see this category of researchers first ask for money and disclose anyway if there isn’t a financial benefit.

**Note: the following case studies are real, but the company names have been redacted to provide anonymity to the organizations.** <query id="Q1"> <p>Dear TS, Please set as Note text.</p> </query>

### 10.1.2 Case Study Analysis

When reviewing all of the case studies, identifying major defining differences between all of the researchers is a simple task. The ethical and monetary approaches can have negative consequences for the future of researchers, and operating a fair program will ensure that researchers receive their due diligence. For example, in Case Study 1, the researcher was clearly interested in money from the get-go. An inexperienced program manager might be very wary of a researcher immediately discussing payment and refusing to disclose otherwise. However, it’s necessary to understand that taking all reports seriously is the responsibility of a program manager, and even if the researcher sounds threatening, enterprises have an obligation to respond to the researcher to a certain extent. Every situation should be managed diligently, and understanding the perspective of a researcher is important to understanding their intention for hacking and participating in programs.

## 10.2 Invalidating False Positives

One of the most difficult aspects of managing bug bounty programs is the process of invalidating false positives. Most individuals don’t want the responsibility of having to tell a security researcher that the identified issue isn’t actually a problem at all. Unfortunately, this is the burden program managers have a responsibility to bear. Managing a false positive can feel embarrassing at first, but there are ways to manage the occurrence professionally.

### 10.2.1 Intake Process and Breaking the News

As a program manager, the false positive rate should be relatively low if the enterprise has a bug bounty platform. The triage team for the platform will maintain the responsibility of validating to ensure that it’s a true positive, but in some instances false positives will accidentally get triaged. First and foremost, a program manager should never create a ticket and assign it to an engineering team without first validating that the vulnerability is legitimate. Avoiding the situation of going through the entire triage process will ensure that program managers and affected teams don’t bear the burden of having more steps than necessary if a vulnerability is invalid. Once the vulnerability is deemed invalid, program managers should calmly inform the security researcher that a mistake was made, without pointing their finger at the triage team. The following is a good example of a fictional scenario, and the appropriate way to manage the situation and address the security researcher:

Nick is the program manager for Company X. The bug bounty program that he manages receives a report on a Friday evening about a cross-site request forgery (CSRF) vulnerability, resulting in the theft of sensitive data from a user. During the weekend, the triage team evaluates the vulnerability and notes that it’s a true positive. The triage team cleans up the report, produces a subreport with easy-to-follow vulnerability replication steps, and assigns the ticket to Nick’s team for further review. Nick doesn’t have a lot of experience with hacking, but is excellent in the code review process. After reviewing the researcher’s proof of concept, Nick is having issues understanding how this is a vulnerability. Typically, a standard CSRF vulnerability proof of concept would result in the security researcher being able to prove that sensitive data can be stolen. When a domain’s access control allow origin is too permissive and the access-control-allow-credentials is set to “true” it can result in someone being able to steal credentials.

The issue that Nick is facing appears to be one in which sensitive information that is being returned is nonexistent. When Nick executes the researcher’s proof of concept script, he notices that the only information being returned to the page is source code for the page and a few other minor details, but nothing deemed a security risk. To ensure that he isn’t overlooking something important, Nick decides to host his own separate proof of concept and, again, notes that no sensitive data is being returned. Nick’s overall verdict is that the research is indeed able to exploit the overly permissive cross-origin resource sharing (CORS) policy. However, the exploitation occurs on a page that has no sensitive data at all and does not impact the confidentiality, integrity, or availability of any user or enterprise data. Additionally, the occurrence of this false positive has been identified a long time prior to the bug bounty program inviting hackers. In fact, Nick ensured that in the out-of-scope section there was a specific clause that stated exploitation on pages that had no provable impact was to be considered out of scope. Nick did not open a ticket, and began to prepare communications with the security researcher.

Now that it has been established that a false positive exists, Nick has to break the news to the security researcher.

NICK:

After further validation, we’ve noted that the CSRF vulnerability you are reporting is actually a false positive. We are sorry for the mix-up, and hope you continue to participate in our program.

RESEARCHER:

I don’t understand. The program said this was a verified vulnerability and I was even able to pull sensitive information from the page.

NICK:

I understand and I apologize. However, we had noted that there isn’t any sensitive information actually being displayed in this vulnerability. Even when logged into a user account and clicking on the CSRF that is externally hosted, no sensitive information, tokens, or anything that can be used for nefarious purposes was able to be retrieved.

RESEARCHER:

I think the information is sensitive and that I should be compensated for the vulnerability. This is clearly a CSRF vulnerability.

NICK:

Yes, this is a CSRF vulnerability but in our program out-of-scope section we highlight the following:

RESEARCHER:

OK, I took a look and this appears to be true. I’m sorry for reporting this.

NICK:

Don’t be sorry! We appreciate your participation, thank you.

While this was a difficult conversation for Nick to have, it’s important to ensure that false positives are deemed as such. Paying for one could be the difference between negative interactions in the future, although program managers shouldn’t take it to heart in the event of an honest mistake. It may seem unlikely that both a triager and program manager fail and pay for a nonissue, but nothing is impossible. Keeping false positives in mind and being willing to tell a security researcher “no” is a nonnegotiable aspect of bug bounty program management.

### 10.2.2 Dealing with a Toxic Hacker

The time will eventually come when a program manager has to deal with a security researcher who has now become toxic or exceedingly difficult to deal with. In some cases, the program manager may not have to deal with a negative security researcher immediately. The point they decide to cause issues can vary, such as before the ticket is addressed, during the vulnerability remediation process, or after. Each situation must be handled delicately as there’s a possibility it can end up completely working against the enterprise, or the researcher, and neither is ideal. How is a toxic interaction defined? Unfortunately, it’s difficult to define what “toxic” is, but generally it’s an exceedingly negative interaction in which the program manager has no choice but to implement drastic measures to resolve the behavior.

## 10.3 Managed Program Considerations

As discussed in [Chapter 3](#c03.xhtml) (Section 3.7), managed programs are an excellent way to offset some of the inevitable grief that will be experienced from program management. If a security researcher reports a vulnerability and it’s not actually an issue, a triager can quickly resolve the issue. In the instance a security researcher decides to become toxic, it’s even easier for a bug bounty program manager to deal with because they now have the ability to moderate and participate at will and are not quite emotionally attached to the situation. Bug bounty platform solutions will typically have the means to resolve toxic interactions fairly quickly. Here are some general considerations when observing interactions between the bug bounty platform triage team and the security researcher:

1.  Without having to ask, a program manager should be able to determine what the dispute is about via reading through the various communications.
2.  If the dispute is about the legitimacy of a vulnerability, validate the triager’s response. For example, a triager may believe that it’s not a vulnerability. However, it’s possible that it’s a legitimate issue.
3.  Determine the toxicity level and gauge the appropriateness of the responses. If the triager is too hostile or afraid to speak up, both scenarios have the potential to damage future interactions.
4.  Provide commentary. Don’t be afraid to give the triager more information to help them or to correct the course of action the triager is planning on taking. Perception is subjective. Therefore, program managers should be willing to express an opinion on the matter.
5.  Intervene where necessary. If the situation appears to be negative to the point of no return, if it hasn’t already occurred, inform the triager that it would probably be a good idea to remove the researcher from the program. Additionally, if misinformation about the state of the enterprise bug bounty program is being relayed from the triager, correct it. Starting with a private conversation is the best route to avoid any potential of accidentally embarrassing the triager. A simple, “I noticed that you said ‘x’ to the researcher and that’s not exactly what we do” can be a saving grace for the communications between triage, the enterprise, and researchers.
6.  It’s possible that a triager can verify a vulnerability and then the interaction may turn sour with the program manager. In this instance, refer to: “Toxic Interaction #2” in Section 10.4 for guidance on resolution, keeping in mind that managed services should be brought into the loop before attempting to manage the disrespectful behavior with the researcher.

## 10.4 In-house Programs

Toxic interactions can intensify when enterprise bug bounty programs are operated without any form of managed service on a dedicated platform. It’s no surprise that differences in opinion can occur between a program and a researcher, and program managers need to be aware of the various resolution options. With that being said, even though programs will ultimately have the final say, understanding where the researcher is coming from is part of the equation. However, a program should not allow themselves to be run over by a toxic security research who is displaying explicit or threatening behavior. As is the situation with false positives, dealing with a security researcher and addressing this situation can be difficult. In any case, two examples with explanations are provided to help spell out the importance of understanding and correctly addressing the situation.

Overall, the scenarios presented should provide an adequate example of what a severely toxic interaction and a more mild one look like. Toxicity is about perception. Therefore, a program manager should always prioritize the safety of the enterprise and put all feelings aside when dealing with program communication affairs. If a program manager reacts adversely because of a negative interaction, it can further escalate the problem. Emotional intelligence is a difficult subject to approach in program management. Security researchers may not understand why their tone sounds threatening and bug bounty program managers must be prepared to deal with the possibility of such occurrences. In addition, many security researchers don’t operate in English as a native language and some translations may be perceived as more hostile than they actually are. Make an effort to understand the researcher’s point of view.

## 10.5 Blackmail or Possible Threat Actor

Toxic interactions may be hard to decipher from actual threats and, in the instance of a threat actor trying to exploit the enterprise, may lead to a lot of confusion. As a general guideline, unsolicited emails that seem exceedingly threatening should be forwarded to the legal team immediately for the next course of action. Conversely, if the person is asking for money for a bug, cautiously respond and ask if they would like to be invited to the bug bounty program. If they respond with a lot of hostility in what seems like a possible exploitation attempt, forward to legal immediately for further review. All threats should be treated equally, just as all emails reporting vulnerabilities that seem legitimate should be reviewed.

## 10.6 Public Threats or Disclosure

The most sensitive situation is when someone threatens the organization publicly. There are multiple scenarios that could potentially take place, and program managers should be prepared to deal with each one of them – or understand program management well enough to adjust to dynamic situations. Here are some of the possible ways a program can be at risk:

1.  *Security researcher discloses unpatched vulnerability*: it’s possible that a researcher may get overzealous and post about a vulnerability immediately upon reporting it or before it’s patched. While the act alone does not constitute toxicity, asking the researcher to remove the vulnerability may result in toxic backlash. Program managers may attempt to reach out to the researcher directly if they feel comfortable. Legal should not need to be involved. Step up as the program manager and tell the legal department that you will deal with it. Communicate with the researcher and ask them if they would be willing to take the writeup down until the vulnerability is patched. If they refuse, don’t seek to punish them but, instead, escalate the criticality of patching that vulnerability internally. The most important part isn’t that the hacker disclosed but that the vulnerability exists. Get it fixed.
2.  *Threat actor blackmails or discloses vulnerability*: if the attention of a program manager is brought to a vulnerability that is released to the public without regard for the enterprise, inform social media managers not to respond, and consult with legal on the next move. Document any evidence of the exploitation and review logs of the affected asset(s). Validating the vulnerability is also a nonnegotiable portion of this exercise. However, if the enterprise has an incident response team, they should be notified first and foremost, before exploring the data. However, *before* engaging with legal, or even the incident response team, please ensure that it’s a legitimate blackmail attempt and not just a researcher angry about a lack of contact. Nearly all situations in which a vulnerability is being disclosed can be worked out, and most threats are a result of a frustrated hacker who has gone unheard.
3.  *Security researcher threatens to disclose on* *Open Bug Bounty*: program managers may find that a security researcher attempted to contact them multiple times and there may have been an oversight. They may report the vulnerability through a website such as Open Bug Bounty which forcibly discloses the vulnerability after 90 days (industry standard). Program managers should attempt to contact the researcher using any information on file under their Open Bug Bounty account. If a response isn’t received, the program manager should investigate the asset and vulnerability type in question and set an alert for the disclosure date reveal to see the exploitation methodology and resolve as soon as possible if it’s serious enough. If possible, getting the researcher into the bug bounty program and getting them paid is a priority. Encouraging research is the mission of bug bounty program managers. Typically, when an event such as a report through Open Bug Bounty occurs, it’s the result of a bug bounty program that’s too inaccessible to hackers. Program managers may observe this occurrence if they run private programs.
4.  *Security researcher threatens to disclose on social media*: typically, the disclosure that is threatened by security researchers on social media is far more mild than one of a threat actor. A situation as described would usually start as the researcher asking if someone has a contract for the enterprise and tagging them on Twitter, Facebook, or LinkedIn. If they don’t receive a response, the urgency increases, and depending on the tolerance of the researcher, they may threaten to drop it publicly or switch to a more threat-actor-like release mode. Program managers are usually free to respond with a little less caution, and just as the email intake process is done, invite the researcher to the bug bounty program. If they don’t want to disclose the vulnerability to the enterprise, realize that there’s probably a good reason for it. Is the program paying researchers well? Does the program force a nondisclosure agreement upon a researcher after reporting? On average, researchers want money and public disclosure. Offer both and you’ll typically note a better response. If the researcher refuses, do not pursue them with a legal team – rather, aim to fix the vulnerabilities that are revealed. Some researchers can’t be reasoned with, but one must communicate with them appropriately and not in a threatening manner.

## 10.7 Program Warning Messages

Security researchers are hackers, and curiosity can be their saving grace and their downfall at the same time. Security researchers typically practice anonymity, and this may include using a virtual private network (VPN). For example, the enterprise program scope may say, “Don’t use automated scans.” A good enterprise security program will use a web application firewall or other rate limiting and blocking options, and a security researcher who decides to use their real IP can get blocked quickly during testing, especially if scanning. In a perfect program management world, a security researcher will respect the scope and not use automated solutions. In all reality, it’s not usually an issue. However, circumstances may occur during heavy production times or development cycles and software engineers may report a lot of errors. Program managers will have to come up with creative ways to block the traffic if they are not utilizing tooling that can prevent this type of behavior automatically. Even if the enterprise does have tooling, messaging may be necessary to get the point across.

## 10.8 Threat Actor or Security Researcher?

To be frank, the “Is it a threat actor or security researcher?” game is awful to play and mentally exhausting for the program managers and any other involved teams. Over time, bug bounty programs have attempted to innovate unique ways to deal with this situation, such as requiring a specific VPN connection pack to begin research or instructing the researcher to use a specific user agent or header. Unfortunately, that may work in some instances, but the more that is required of a researcher to begin, the more friction it creates and participation may dwindle, or these requirements may be ignored altogether. Creating a playbook in these circumstances can help address the issues quickly, whether it’s a mental note or physical documentation.

First, ask the following questions:

1.  Where are the issues occurring and are they contained?
2.  Is there production impact and, if yes, how severe is it?
3.  Does incident response need to get involved?
4.  Do the requests follow any basic pattern (IP addresses, headers, requests, URL paths, etc.)?

As a general basis, some of the above questions can be used to start sifting through data and analyzing the differences. Here are two different examples and their suggested resolutions.

Situation #1 seems like a security researcher. In this instance, patterns appear to match behavior observed in the past. Situation #2 is more of a nefarious situation in which reaching out to security researchers will be unnecessary. The questions above are not to be treated as an incident response plan but as a means of understanding some of the various information that program managers should attempt to acquire to assist in making the process easier.

## 10.9 Messaging Researchers

At this point, when there’s a pattern of disruption, it doesn’t hurt to send out a program message to remind participating researchers not to perform disruptive testing. The reason it’s a good idea to send a message to all of the researchers is to avoid singling out the particular researcher. Program managers should avoid the possibility of causing further issues or demotivating the security researchers. In addition, there’s always a chance that the analysis is incorrect and baseless or incorrect accusations could damage enterprise reputation. If using an in-house bug bounty program solution, you may have to send a mass email with BCC depending on the setup. Most managed bug bounty platform solutions have messaging functionality built in.

### 10.9.1 Security Researcher Interviews

Bug bounty programs benefit greatly from the expertise that security researchers bring to the table with the vulnerability research that they conduct.

### 10.9.2 Bug Bounty Program Manager Interviews

## 10.10 Summary

When it comes down to it, the bottom line is this: security researchers and program managers are similar. They all know that communication is an important aspect of program participation and management. Particularly, security researchers just want to be understood – they want their impact to be heard and assessed in a fair way. Program managers want the researchers to let them in and to let their guard down a bit more so that the situation can be assessed properly. In addition, they don’t want to have to tell researchers to respect them: they just want to deal with patient researchers who are polite.

As both a security researcher and a bug bounty program manager, I have seen both sides of a wide array of issues. Ultimately, I know that I’ve been impatient as a researcher and that I’ve also been lax and not willing to hear a researcher out when operating as a program manager. When I catch myself doing these things, I readjust. There’s no harm in admitting fault and adjusting stance – or even just realigning silently. Program managers and security researchers will appreciate adjustments, and that’s what matters. Communication is a key component and driver.

# Part 6   
Assessments and Expansions

# 11   
Internal Assessments

## 11.1 Introduction to Internal Assessments

Program managers, at a minimum, must understand why it’s necessary to have a working understanding of penetration testing and the associated vulnerability assessment phases. Unfortunately, in some cases, enterprise leadership may not understand that program managers should have a background in application security with penetration testing, if not at least a working knowledge of application vulnerability types and mitigation processes. When an employee is hired with no knowledge of common vulnerability types, it may make managing the program exceedingly difficult. This chapter introduces some useful crash-course assessment concepts and tooling but the intention of this chapter isn’t to replace formal penetration testing assessment resources. When reading through this chapter, please understand that penetration testing from both an application and network standpoint requires an extensive amount of training and practice. Some of the best penetration testers in the world still don’t know every aspect of hacking. Aspiring hackers that want to up their game should seek other resources.

## 11.2 Proactive Vs Reactive Testing

The best bug bounty program managers don’t begin testing after the vulnerability reports start rolling in. As can be said about a ship, one does not embark on a journey across the seven seas without checking the ship for holes and ensuring that it’s sound and ready for smooth sailing. Program managers should perform full internal assessments before opening the program, even to a small group of security researchers. An amateur mistake would be assuming that one or even two security researchers would be an OK number of individuals to start with prior to testing. Enterprise assets need to be thoroughly hardened to prevent overpaying security researchers or forcing a pull-back of program launch. Regardless of all of the internal assessments performed, researchers will always find security issues, and program managers shouldn’t be immediately alarmed when reports are received – even on assets that they have tested.

## 11.3 Passive Assessments

Arguably, one of the most important aspects of internal testing is to place oneself in the shoes of a threat actor. A malicious hacker does not automatically acquire a list of assets to attack. As does anyone else, a threat actor needs to perform reconnaissance to identify assets through various means. Program managers can benefit from understanding the different ways passive research is conducted, as it can open up a better understanding of security gaps, prior to performing any active testing at all.

**Note: passive assessments require little/no interaction with the target. All IP address ranges and domains in this section are accessible to the public. Please acquire written permission to perform on any targets past the passive assessment stage. In fact, the intent of this book is to give program managers some tips and tricks to test on their own assets. It is not intended for use on nonprogram-related assets.** <query id="Q1"> <p>Dear TS, Please set as Note text.</p> </query>

### 11.3.1 Shodan

The best way to describe Shodan is as a tool that turns active recon into passive recon. Shodan crawls the Internet continuously and attempts to identify open ports and services on those ports. It’s a search engine that includes any Internet-connected device that it can make contact with. Program managers need to use Shodan as a resource because the enterprise may have exposed assets that they were not even aware of.

#### 11.3.1.1 Using Shodan

1\. First go to a browser and navigate to shodan.io ([Figure 11.1](#c11.xhtml#c11-fig-0001)).

![Figure 11.1 Shodan Browser Search.](images/c11f001.png)

[**Figure 11.1**](#c11.xhtml#rc11-fig-0001) Shodan Browser Search.

Program managers will be greeted with a search bar and various functionality. Creating a free account is highly recommended, especially if this source will be used often.

2\. In the search bar, type the IP address of the specific asset that needs to be looked up to see if Shodan has any data on it. In any case, a good course of action for a program manager performing recon for the first time is to enter the name of a web application domain that is controlled by the enterprise, and click the magnifying glass to search ([Figure 11.2](#c11.xhtml#c11-fig-0002)):

![Figure 11.2 Shodan Search Bar.](images/c11f002.png)

[**Figure 11.2**](#c11.xhtml#rc11-fig-0002) Shodan Search Bar.

3\. The search will then bring up a list of many different results ([Figure 11.3](#c11.xhtml#c11-fig-0003)). The domain may show up as linked to various assets, filtering by country, services, organizations, and products. At this point, any of this information is considered open and exposed to the Internet. Viewing the information isn’t illegal in any sense. Program managers should be advised that it would be in their best interests to carefully check assets and ensure that they belong to the organization before proceeding with testing. Additionally, Shodan has a wide array of filters and logic that could be used. For example, a security researcher, threat actor, or program manager may want to obtain visibility on where a service is being used, or even a specific version of the service. In this scenario, we are using “vsftpd 2.3.4” as a means of searching and generating results.

![Figure 11.3 Generating Results.](images/c11f003.png)

[**Figure 11.3**](#c11.xhtml#rc11-fig-0003) Generating Results.

4\. Next, if an asset meets the criteria defined, a program manager can click on it to understand the impact and analyze enterprise exposure. Imagine that the asset labeled “216.199.146.90” appears to belong to the enterprise. When a program manager clicks on it, a new page loads that highlights many additional pieces of information including all open ports that Shodan has identified – as well as services, and the best attempt of identifying vulnerabilities against the asset based on versioning ([Figure 11.4](#c11.xhtml#c11-fig-0004)). It’s important to note that some CVEs against services and versions may not be identified. Nonetheless, the level of insight that Shodan provides can prevent deadly situations.

![Figure 11.4 Shodan Asset Analysis.](images/c11f004.png)

[**Figure 11.4**](#c11.xhtml#rc11-fig-0004) Shodan Asset Analysis.

Taking a closer look at the vsFTPd 2.3.4 example ([Figure 11.5](#c11.xhtml#c11-fig-0005)), it can be seen that Shodan has appeared to confirm that this asset is running the service. If a program manager were to find out that one of their assets were running this version of FTP, it could mean that threat actors may be able to easily see this information too and, knowing that many exploits exist, take advantage of the out-of-date service.

![Figure 11.5 Shodan Services Analysis.](images/c11f005.png)

[**Figure 11.5**](#c11.xhtml#rc11-fig-0005) Shodan Services Analysis.

5\. The risk identification process is essentially broken into several parts while using Shodan.

*   Looking up assets by domain or IP address.
*   Checking to see what information or additional mapping Shodan has on the assets.
*   Identifying out-of-date versioning on services or infrastructure.
*   Searching for exploitability.
*   Confirming asset ownership.
*   Attempting exploitation or relaying the vulnerability to the affected team.

For example, in this instance a program manager may not know what, if any, exploits exist against the various services or exposed ports. A quick Google search for “vsFTPd 2.3.4” brings up multiple well-known and developed exploits ([Figure 11.6](#c11.xhtml#c11-fig-0006)):

![Figure 11.6 Google Search Results.](images/c11f006.png)

[**Figure 11.6**](#c11.xhtml#rc11-fig-0006) Google Search Results.

If the asset is indeed confirmed as belonging to the enterprise and it’s verified to be running that service, a program manager now must contact the affected team immediately for resolution as the exploit could lead to a threat actor achieving remote code execution on the server. Shodan can help assist program managers in quickly identifying easily exploitable services and out-of-date components or assets that may have not been known about prior.

### 11.3.2 Amass/crt.sh

Common misconceptions presented by program managers are that “they know the extent of the subdomains controlled by the organization.” Bug bounty program managers would be surprised to find that infrastructure teams have abandoned subdomains that are actively hosting applications and exposing them to the Internet or creating unnecessary risk. Amass provides far more functionality than just subdomain enumeration. However, a quick technique exists to help program managers quickly identify subdomains passively in order to look for additional attack surfaces.

Additionally, crt.sh is a tool that can be used to gather more subdomains and to possibly enumerate technology that the organization is using. crt.sh looks for all certificates containing variations of the root domain provided, which can be helpful (and even surprise a program manager). Domains not found before enumeration can be dumped into Amass (although it’s important to note that Amass also performs queries from crt.sh) or a preferred subdomain enumeration tool to discover even more assets to test on.

**Special thanks to Donk for showing me crt.sh (Twitter: @donk\_enby).** <query id="Q2"> <p>Dear TS, Please set as Note text.</p> </query>

#### 11.3.2.1 Amass

As a standard, Amass comes standard with Kali Linux or most other penetration testing distributions. First and foremost, gather a list of domains that need to be tested. As a program manager, maintaining a list of all of the subdomains is a necessary evil, or in other words, no subdomain oversight equals no vulnerability oversight. If the enterprise is large enough, acquiring a list of all root domains may be difficult. If the organization is using Amazon Web Services (AWS), talk to infrastructure or networking teams to make a determination of all assets.

1.  First, put all of the root domains in a file, such as [example.com](http://example.com), [example2.com](http://example2.com), etc. Once this is done, dumping subdomains into the file can be an additional method of testing as results may prove to be promising.
2.  After the domains/subdomains are in a file, run the subdomain enumeration with Amass:

amass enum -df test.txt > subdomains.txt ([Figure 11.7](#c11.xhtml#c11-fig-0007))

![Figure 11.7 Amass Scanning for Subdomains.](images/c11f007.png)

[**Figure 11.7**](#c11.xhtml#rc11-fig-0007) Amass Scanning for Subdomains.

The above command tells Amass to perform subdomain enumeration on the domain/subdomain file with the -df switch; it then writes the output into the subdomain file ([Figure 11.8](#c11.xhtml#c11-fig-0008)).

![Figure 11.8 Subdomains in Nano.](images/c11f008.png)

[**Figure 11.8**](#c11.xhtml#rc11-fig-0008) Subdomains in Nano.

**Note: if having issues writing the output into the file, make sure that permissions are correct on the directory that is being written to. Additionally, if Amass appears to stall at a specific DNS queries per second rate after a few minutes, stop the tool.** <query id="Q3"> <p>Dear TS, Please set as Note text.</p> </query>

**Once the tool is finished, subdomains will be output into the file specified.**

#### 11.3.2.2 crt.sh

Subdomain enumeration is an essential portion of testing. Even though Amass queries crt.sh, program managers may want to see a more comprehensive overview on the certificates and software utilized. Utilizing crt.sh is a fast alternative to using scans to discover domains that may have been overlooked ([Figure 11.9](#c11.xhtml#c11-fig-0009)).

![Figure 11.9 Subdomain Enumeration with crt.sh.](images/c11f009.png)

[**Figure 11.9**](#c11.xhtml#rc11-fig-0009) Subdomain Enumeration with crt.sh.

## 11.4 Active Assessments

An active assessment is one in which a hacker tests for vulnerabilities. The active stage can be considered disruptive to the enterprise if a program manager is not careful. Extreme caution should be exercised and no exploitation attempts should be made in the instance that a program manager is inexperienced. It is highly recommended to be comfortable with exploitation before moving into this phase as it can be detrimental to the production environment. Even when comfortable with exploits, a good practice is to inform the organization via a “Pentest” active board or post somewhere to let everyone know to contact you if any weird traffic comes their way. Doing so can prevent an “all hands on deck” emergency-type situation. Plenty of tooling exists for active testing. However, only several small aspects will be covered (more automated tooling for the busy professional).

### 11.4.1 nmapAutomator.sh

Nearly any beginner hacker understands nmap, but how about nmapAutomator? The tool was designed by 21y4d and can be found on GitHub. It was created as an easier means of combining multiple toolsets for network and web application hacking, including full nmap port and service scans on tcp/udp, CVE scans, and following that, various suggested recon commands depending on the ports/services found. Additionally, nmapAutomator will utilize nikto, gobuster, sslscan, joomscan, wpscan, droopescan, smbmap, smbclient, enum4linux, snmp-check, snmpwalk, dnsrecon, ldapsearch, odat, etc. The tool can be used for a wide variety of scenarios, but is best used on backend servers.

As can be seen in [Figure 11.10](#c11.xhtml#c11-fig-0010), there are many options to use in conjunction with nmapAutomator. Program managers can utilize the command **./nmapAutomator.sh 10.0.0.212 All** to perform a full scan on the asset. Once the command is executed, the tool will go through various stages including a quick scan, basic scan, and full scan ([Figure 11.11](#c11.xhtml#c11-fig-0011)), and then evaluate the given services to perform more refined tool usage and vulnerability scans thereafter. All of the results will be output into a folder to enable a neat and organized way to maintain findings ([Figure 11.12](#c11.xhtml#c11-fig-0012)).

![Figure 11.10 nmapAutomator Scanning Information.](images/c11f010.png)

[**Figure 11.10**](#c11.xhtml#rc11-fig-0010) nmapAutomator Scanning Information.

![Figure 11.11 nmapAutomator Performing Full Scan of Asset.](images/c11f011.png)

[**Figure 11.11**](#c11.xhtml#rc11-fig-0011) nmapAutomator Performing Full Scan of Asset.

![Figure 11.12 nmapAutomator Results.](images/c11f012.png)

[**Figure 11.12**](#c11.xhtml#rc11-fig-0012) nmapAutomator Results.

### 11.4.2 Sn1per

Created by 1N3, Sn1per is yet another automated vulnerability scanning tool. A free version of Sn1per can be downloaded from GitHub. However, a professional version that allows a graphical user interface (GUI) view and workspace management is available. The free version can be utilized efficiently. Once the tool is downloaded and configured per the instructions, a program manager can take a URL for a domain and begin testing against it. Sn1per has a lot of modes. However, a good start would be the utilization of the “normal” mode.

Once downloaded, it’s as easy as utilizing the command: **sniper -t** [https://example.com](https://example.com).

The tool will then attempt to utilize a wide variety of enumeration tools on the domain for both web application and network penetration testing. Be warned: if not specified, the tool may attempt various exploits which could be detrimental to the production environment; it’s essential to be prepared for this instance. (See ures [11.13](#c11.xhtml#c11-fig-0013) and [11.14](#c11.xhtml#c11-fig-0014).)

![Figure 11.13 Sn1per Running Metasploit Modules.](images/c11f013.png)

[**Figure 11.13**](#c11.xhtml#rc11-fig-0013) Sn1per Running Metasploit Modules.

![Figure 11.14 Sn1per Running Nmap Scripts.](images/c11f014.png)

[**Figure 11.14**](#c11.xhtml#rc11-fig-0014) Sn1per Running Nmap Scripts.

### 11.4.3 Owasp Zap

In the suite of free DAST (dynamic application security tools) is OWASP ZAP. This tool focuses on the aspects of web application testing, and will evaluate URLs or parameters for a wide range of vulnerabilities. ZAP comes with most penetration testing toolkits, including Kali Linux and Parrot. Alternatively, the professional version of Burp Suite has a decent DAST scanner. However, not every program manager will have access to the funds to purchase a license.

Scanning is fairly easy: once the tool is loaded a program manager can input a URL in the “URL to Attack” field. At this point, it’s as easy as pressing “Attack.” However, in more realistic scenarios or depending on an enterprise’s needs, the configurations may need to be modified. There are plenty of open-source guides that explain the many things that ZAP can perform when configured for advanced usage.

For the example shown in [Figure 11.15](#c11.xhtml#c11-fig-0015), we are using a purposely vulnerable domain for testing purposes.

![Figure 11.15 Setting up an Automated Scan in OWASP ZAP.](images/c11f015.png)

[**Figure 11.15**](#c11.xhtml#rc11-fig-0015) Setting up an Automated Scan in OWASP ZAP.

When the “attack” button is clicked, it will begin to crawl and test a wide variety of payloads to look for vulnerabilities ([Figure 11.16](#c11.xhtml#c11-fig-0016)).

![Figure 11.16 OWASP ZAP Scan Results.](images/c11f016.png)

[**Figure 11.16**](#c11.xhtml#rc11-fig-0016) OWASP ZAP Scan Results.

The alerts fields shows all of the possible vectors of attack, and in this case the crawl and payload testing discovered a DOM Based XSS vulnerability ([Figure 11.17](#c11.xhtml#c11-fig-0017)). To the right of the vulnerability identified, a payload and description of the attack is typically available. If we copy the payload, it looks like this:

![Figure 11.17 OWASP ZAP Potential Vulnerability Result.](images/c11f017.png)

[**Figure 11.17**](#c11.xhtml#rc11-fig-0017) OWASP ZAP Potential Vulnerability Result.

[https://xss-game.appspot.com/level1/frame#jaVasCript](https://xss-game.appspot.com/level1/frame#jaVasCript):/\*-/\*\`/\*\\\`/\*’/\*”/\*\*/(/\* \*/oN cliCk = alert())//%0D%0A%0d%0a// </stYle/ </titLe/ </teXtarEa/ </scRipt/–! >\\x3csVg/ < sVg/oNloAd = alert()// >\\x3e

When the payload is entered into the browser, a successful XSS attack is executed ([Figure 11.18](#c11.xhtml#c11-fig-0018)):

![Figure 11.18 XSS Attack Performed.](images/c11f018.png)

[**Figure 11.18**](#c11.xhtml#rc11-fig-0018) XSS Attack Performed.

Don’t be fooled: OWASP ZAP isn’t a dedicated XSS tool. It maintains the capacity to fuzz, edit and resend requests, and search for an entire slew of vulnerabilities. A program manager can spend hours customizing ZAP and can even export vulnerability reports.

### 11.4.4 Dalfox

One of the best tools in a program manager’s arsenal for testing URL parameters and finding hidden parameters is DalFox. Maintained by hahwul, DalFox can be downloaded from GitHub. By gathering a list of URLs, or even having a list of root domains, DalFox has proven to be a worthy tool. The file option allows for testing multiple parameters, whereas a single URL can also be provided for testing ([Figure 11.19](#c11.xhtml#c11-fig-0019)). There are plenty of options to utilize, so please read the manual prior to usage.

![Figure 11.19 Dalfox Available Command.](images/c11f019.png)

[**Figure 11.19**](#c11.xhtml#rc11-fig-0019) Dalfox Available Command.

For this specific example, a known vulnerable URL will be utilized from our previous testing with ZAP.

/dalfox url [https://xss-game.appspot.com/level1/frame](https://xss-game.appspot.com/level1/frame)

Quickly after running the script, an XSS instance is identified via the query = parameter ([Figure 11.20](#c11.xhtml#c11-fig-0020)). A final payload is output with a \[POC\]\[V\] meaning that the exploit was verified as working – or at least detected as such ([Figure 11.21](#c11.xhtml#c11-fig-0021) ).

![Figure 11.20 Dalfox Identifying an XSS Instance.](images/c11f020.png)

[**Figure 11.20**](#c11.xhtml#rc11-fig-0020) Dalfox Identifying an XSS Instance.

![Figure 11.21 XSS Attack.](images/c11f021.png)

[**Figure 11.21**](#c11.xhtml#rc11-fig-0021) XSS Attack.

Payload: [https://xss-game.appspot.com/level1/frame?query=%3CScRipt+class%3Ddalf​ox%3Ealert%2845%29%3C%2Fscript%3E](https://xss-game.appspot.com/level1/frame?query=%3CScRipt+class%3Ddalfox%3Ealert%2845%29%3C%2Fscript%3E)

### 11.4.5 Dirsearch

Fuzzing is an important aspect of internal assessments as well. Hackers love to jump to the meat and potatoes of exploitation, which leaves many to forget that, sometimes, more is less. The best attack is one in which the hacker knows everything there is to know about the target. Therefore, program managers should strive to know twice as much as the participating security researchers. The idea of fuzzing is to search for secret files or directories on a web application. Dirsearch simplifies the process. As most of the tools, starting requires downloading it from GitHub, unless it’s prepackaged with the penetration testing operating system of choice. Dirsearch was created by maurosoria. Once again, reading the manual is important as there are plenty of different switches to create and fine tune the involved processes.

Several combined switches seem to be effective for quick testing: -x to include status codes to ignore false positives (or an overload of irrelevant true positives), -e to annotate which extensions need to be tested, and -f to force append extensions onto each word tested from the default wordlist. For example, if a URL were tested and the tool was looking for an admin directory, admin.php would also be tested if utilizing “-e php –f” as a switch option. If a more hasty test is utilized, removing the -e and -f switches will test directories and include file paths only.

As an example, imagine the following command: python3 dirsearch.py -u [http://127.0.0.1:8000](http://127.0.0.1:8000) -e php,txt,bak,conf -f -x 300,301,302,303,304,400,401,402,403,404,500,501,502,503,504

Given that 127.0.0.1 is the domain, such as [https://example.com](https://example.com) – and the semicolon is either the preferred port or service (unnecessary to append the port for ports 443 and 80) – the command will look for files and directories and output them along with the status response code when finished ([Figure 11.22](#c11.xhtml#c11-fig-0022) ).

![Figure 11.22 Dirsearch Finding Folders.](images/c11f022.png)

[**Figure 11.22**](#c11.xhtml#rc11-fig-0022) Dirsearch Finding Folders.

## 11.5 Passive/Active Summary

There’s a wide range of tools available to program managers, and this portion of the book doesn’t even scratch the service of the amount of free tooling and resources available, including the manual reviews that can be done to support the health of the bug bounty program. Program managers don’t need to be expert hackers with impeccable wit and skill, but they do need to know how to identify low-hanging fruit, and a lot of the tooling discussed is good when utilized for the purposes of surface level penetration testing. Nonetheless, program managers should aspire to learn as much as possible to identify a wider range of bugs.

## 11.6 Additional Considerations: Professional Testing and Third-Party Risk

For program managers that don’t have the experience to perform internal assessments themselves, they should outsource to a trusted penetration testing firm and ask for a black-box test (meaning no information is given). Even enterprises that have the expertise to carry out full penetration tests could benefit from further testing, especially if the engineers do not perform penetration testing as a full-time job. Third-party risk is yet another factor that needs to be considered throughout the assessment period. It’s easy to think about the impact of testing company-owned assets, but how about assets not owned by the enterprise running the bug bounty program?

It would be unwise to open up a program to security researchers if the enterprise isn’t prepared to deal with remediating a lot of vulnerabilities. Third-party risk can be yet another factor, opening up the opportunity of exploitation or more bugs that a program will have to pay if not recognized in the first stage of partnership from company to company. Program managers should work with governance, risk, and compliance to evaluate acquisitions or partners consistently. Failure to do so can result in the exploitation of the organization.

# 12   
Expanding Scope

Earlier in the book, the scope of a bug bounty program was discussed and a key principle was to ensure that the scope that is defined was not too wide to prevent overburdening of the program managers who are attempting to triage and remediate vulnerabilities. The idea behind scope expansions is to give researchers more surface to test on. After all, a threat actor may want something that the enterprise has: scope does not exist in the world of crime and illegal personal gain.

Opening up additional assets for testing can prove painful if too many assets are added or if an enterprise decides to offer rewards on an untested asset. While there’s not necessarily a right or wrong time to expand scope, several steps can be taken to mitigate the potential of failure, nearly all within the realm of prior testing and level of effort.

## 12.1 Communicating with the Team

The nonnegotiable aspect of scope expansion is adequately portraying intentions to the team. Standalone program managers should communicate with leadership to ensure that everyone is on the same page with the expansion. A program manager should never add an asset without talking to other engineers on the team. Bridging any gaps in communication is a fairly easy process, and with an adequate plan resistance won’t necessarily be met unless the budget isn’t flexible for the needs of the bug bounty program.

Program managers should focus on a few aspects to enable a thorough conversation:

*   Intention: during the process, the reason for scope expansion should be discussed with the program team or with leadership. The idea of the expansion is to allow more attack surface. Therefore, the reasoning should be communicated to the appropriate party.
*   Testing: let the team know what the vulnerability analysis plan is prior to the expansion. An in-house penetration test may suffice, but weighing the pros and cons of an out-sourced penetration test may be necessary depending on the attack surface. For example, expanding to one single subdomain may be a small project, whereas adding an additional root domain for a subsidiary company could prove to open up quite a large attack surface.
*   Value: highlight the value of an expansion. At the point of considering such expansions, leadership should already have seen an adequate vulnerability finding and resolution workflow. Therefore, value should speak for itself. If the workflow has been less than ideal, considering an interim solution, such as adding more hackers to the program or achieving a better security posture, may be a better option.
*   Target launch: talk about ideal scope expansion data. Notification is essential: there’s nothing worse than surprised engineering teams. In addition, proper notification can assist in preparing the teams for the expansion, and in some cases development teams may be dedicated to monitoring and ensuring a smooth launch.
*   Follow through: explain what the intention looks like for rolling back or putting a hard stop on the expansion if any issues occur.

## 12.2 Costs of Expansion

Program managers should never expect that an expansion, even to a single asset, will yield minimal results or payouts. Before expanding, it’s absolutely essential to evaluate the current bounty pool and analyze the trends of payouts over the course of the period to attempt to get a rough estimate of what the expansion may do to the budget. Additionally, no expansions should occur if the budget is severely limited or if a program is close to hitting the maximum allotment for the fiscal year. If the enterprise is running a program that offers points instead of bounties, it’s still essential to ensure that a thorough analysis of vulnerability reports submitted occurs to prevent burdening teams.

## 12.3 When to Expand Scope

Unfortunately, there’s never a correct way to actually define this. There are most certainly best practices, but an actual enterprise program may have a wide array of considerations to take into account before being able to make a decision on an expansion. Ideally, scope expansions are best approached when there is adequate reason to believe that the current scope is either too limited or exhausted in one way or another. Take, for instance, an enterprise program that is receiving an average of five or more reports a month. Depending on the payout table for the program, over five reports may end up being a little more than the enterprise had bargained for and an expansion of additional assets may not be appropriate.

Expanding scope is about comparing the current reports received within a given period, and analyzing the enterprise’s ability to prepare and safely increase the effectiveness of the program without inadvertently damaging the program. Program managers can find great solace in expanding when ready and not rushing into it.

## 12.4 Alternatives to Scope Expansion

Scope expansions aren’t the only way to encourage more program participation. Program managers can alternatively invite more security researchers, with automated approaches and by hand. For example, most bug bounty management platforms have an option to send automated invites out to researchers until a certain threshold of reports is met on a monthly basis. Automated invites may increase the amount of reports that a program receives. If the amount of hackers being invited is abnormally high, it’s best to remove the option and consider a scope expansion.

To elaborate, imagine that the enterprise has 120 security researchers. If after a few weeks, it’s getting close to 200 and no reports have come in, it may be time to expand scope. Exhausted scopes can discourage security researchers. Overly restrictive scopes tend to have the same effect. Therefore, dynamic adaptations within program management need to be used when the program becomes stagnant.

## 12.5 Managing Expansion

The same processes that have been applied to the pre-considerations of setting up a program should be applied to scope expansions. Testing, communicating with teams and developing expectations with leadership are essential parts of this process. A program manager should not attempt to form any expansion processes until a baseline level of security is considered.

# 13   
Public Release

## 13.1 Understanding the Public Program

Ultimately, the public program is the end state. Most legitimate bug bounty programs aspire to finally opening up their doors to everyone. As is any other expansion incentive, the biggest consideration is a matter of being prepared for this undertaking. A lack of preparedness or a premature launch can result in the complete obliteration of enterprise reputation. The public program is meant to be a way of giving anyone and everyone a chance to research. Many enterprises may never reach this state depending on the size of their program, but it’s undoubtedly the final incentive that most will want to reach.

## 13.2 The “Right” Time

Regardless of the desired launch, there isn’t exactly a right time to launch. The key principle is to not launch too early, to avoid issues with the team being overwhelmed. Thinking about whether an enterprise should open a program is more than just a standard yes or no. A public program means full transparency at all times, and even with a limited scope researchers typically manage to find a ton of vulnerabilities. Considering the various aspects of a public program launch is an absolute necessity:

1.  Employees: does the enterprise have enough employees to manage the incentives if it gets busy? For example, if an application security team has three employees overseeing dozens of high-priority projects, it may become necessary to set up a separate dedicated bug bounty program team alongside them.
2.  Analysis: has the entire program been through rigorous testing? In a scope expansion, only the added assets have to be tested, but prior to public launch, testing is needed to prevent paying out for a lot of easily identifiable vulnerabilities.
3.  Team: is the entire team on board for the expansion? Does everyone realize their roles in their process and the level of effort and coordination needed?
4.  Finances: does the enterprise have a flexible enough bounty pool in the event that a lot of high-impact vulnerabilities are reported quickly?
5.  Statistics: how many hackers are currently within the program and how often are vulnerability reports received? Has scope been expanded multiple times prior to the public program being initiated?

While there are many more aspects that can be evaluated, the above highlights some pertinent questions that should be asked prior to such a big expansion. Program managers should take the time to be honest about their assessment to ensure that they do not sink the program by launching before the enterprise and the employees are ready to deal with the work.

## 13.3 Recommended Release

Managed services and account managers exist for a reason – utilize them. One thing is known for certain: an enterprise should not take a bug bounty program public until it can handle managing over 100 hackers and is prepared for a giant spike in reports. Managing the public release of a program requires diligent planning and careful execution, especially if the program belongs to a big-name company. The official recommendation is to release **when ready** and not based on a specific guideline. While having over 100 hackers seems to be a decent milestone, it may not equate to a prepared enterprise bug bounty program.

### 13.3.1 Requirements

To play it safe, program managers should aspire to check off all of these tasks:

*   Have 100 active hackers participating in the bug bounty program.
*   Receive multiple vulnerability reports weekly.
*   Analyze the budget to ensure that the enterprise can ingest new costs and associated risks.
*   Present an adequate plan of expansion to management.
*   Explain any new workflow predictions to fellow colleagues or managed employees.
*   Prep the software engineers for the release and inform the organization with a mass notice.

Ensure that, as a baseline, all of the above bullet points are met. In actuality, a program manager may have to adapt and should analyze **each and every** possibility.

## 13.4 Rolling Backwards

The reason it’s important to express all of the necessary precautions is because a rollback of the launch of a public program isn’t a great start. It can be detrimental to the security team because it’s embarrassing, as well as the software engineers (depending on the issues that occur). For example, if a public program is launched and the reports are overwhelming, a program manager may end up rolling back the program as it may be the only way to catch up with all the reports, especially if underprepared or understaffed. Doing so can hurt security researchers and cause a lot of mistrust and paranoia about the status of their report. It’s best to gather in all of the reports that were submitted prior to the closure of the public program to prevent unnecessary refute. Still, rolling a program back into private mode may be the only way to handle a situation in which a program manager wasn’t prepared. Always have a backup plan.

## 13.5 Summary

To be frank, not every program manager will receive the opportunity to take their program public – especially if consistently underfunded and overworked. While the goal should always be to launch a public program, it may simply not be on the cards for a smaller asset with no capacity to manage such incentives. It’s not necessarily a cut-and-dry requirement to have to push a program into a public state. Feel out the idea of taking the program public and maintain an effective private program for a while before deciding to do so.

# Index

*   accountability, [91](#c06.xhtml#page_91) 
    *   continuous, [141](#c09.xhtml#page_141)
    *   professional, [38](#c04.xhtml#page_38)

*   account enumeration, [38](#c04.xhtml#page_38)
*   active assessments, [173](#c11.xhtml#page_173). *See also* [passive assessments](#b01.xhtml#c1-idx-0342) 
    *   DalFox tool, [177](#c11.xhtml#page_177)–179
    *   Dirsearch, [179](#c11.xhtml#page_179)–180
    *   nmapAutomator.sh tool, [173](#c11.xhtml#page_173)–174
    *   Owasp Zap tool, [175](#c11.xhtml#page_175)–177
    *   Sn1per tool, [175](#c11.xhtml#page_175)

*   ad hoc program, [22](#c03.xhtml#page_22)–25
*   ad hoc redactions, [124](#c08.xhtml#page_124)
*   alert fatigue, [79](#c06.xhtml#page_79)
*   Amass, [171](#c11.xhtml#page_171)–172
*   Amazon Web Services (AWS), [172](#c11.xhtml#page_172)
*   American Registry for Internet Numbers (ARIN), [137](#c09.xhtml#page_137)
*   Apache server status page leaking server information, [40](#c04.xhtml#page_40), [41](#c04.xhtml#page_41), [114](#c07.xhtml#page_114)
*   application programming interface (API), [58](#c06.xhtml#page_58) 
    *   credentials in Bugcrowd, [76](#c06.xhtml#page_76), [77](#c06.xhtml#page_77), [80](#c06.xhtml#page_80), [80](#c06.xhtml#page_80)f
    *   hacking, [158](#c10.xhtml#page_158)
    *   settings in HackerOne, [107](#c06.xhtml#page_107)
    *   testing, [60](#c06.xhtml#page_60)

*   applications: 
    *   of BBP, [5](#c01.xhtml#page_5)
    *   enterprise, [17](#c02.xhtml#page_17), [135](#c09.xhtml#page_135)
    *   mobile, [5](#c01.xhtml#page_5), [16](#c02.xhtml#page_16), [36](#c04.xhtml#page_36), [71](#c06.xhtml#page_71)
    *   web, [5](#c01.xhtml#page_5), [16](#c02.xhtml#page_16), [26](#c03.xhtml#page_26), [36](#c04.xhtml#page_36), [71](#c06.xhtml#page_71)

*   application security, [4](#c01.xhtml#page_4)–6, [15](#c02.xhtml#page_15) 
    
    *   communicating expectations, [137](#c09.xhtml#page_137)–138
    *   continuous accountability, [141](#c09.xhtml#page_141)
    *   development, [135](#c09.xhtml#page_135)
    *   engineers, [7](#c01.xhtml#page_7), [13](#c02.xhtml#page_13), [16](#c02.xhtml#page_16), [27](#c03.xhtml#page_27), [36](#c04.xhtml#page_36), [116](#c07.xhtml#page_116), [120](#c07.xhtml#page_120), [135](#c09.xhtml#page_135), [139](#c09.xhtml#page_139) 
        *   responsibility in vulnerability management, [19](#c02.xhtml#page_19)
    
    *   escalations, [138](#c09.xhtml#page_138), [139](#c09.xhtml#page_139)–140
    *   exceptions, [138](#c09.xhtml#page_138)
    *   firewall, [54](#c05.xhtml#page_54)
    *   managers, [13](#c02.xhtml#page_13)–19
    *   pushback, [138](#c09.xhtml#page_138)
    *   SLA, [136](#c09.xhtml#page_136)
    *   space, [21](#c03.xhtml#page_21), [44](#c04.xhtml#page_44)
    *   vulnerability reporting, [136](#c09.xhtml#page_136)–137

*   applied knowledge scenarios, [24](#c03.xhtml#page_24)–26
*   asset(s), [57](#c06.xhtml#page_57), [67](#c06.xhtml#page_67), [68](#c06.xhtml#page_68), [109](#c06.xhtml#page_109) 
    *   allocation, [36](#c04.xhtml#page_36)–37
    *   enterprise, [49](#c05.xhtml#page_49), [167](#c11.xhtml#page_167)
    *   group, [70](#c06.xhtml#page_70)–71, [70](#c06.xhtml#page_70)–71*f*
    *   as “out of scope”, [39](#c04.xhtml#page_39)–40
    *   risk, [37](#c04.xhtml#page_37)
    *   for testing, [57](#c06.xhtml#page_57), [57](#c06.xhtml#page_57)–58*f*

*   audit log of HackerOne, [85](#c06.xhtml#page_85), [91](#c06.xhtml#page_91), [91](#c06.xhtml#page_91)f
*   Australian Women in Security Network (AWSN), [160](#c10.xhtml#page_160)
*   availability, [94](#c06.xhtml#page_94), [146](#c10.xhtml#page_146)

*    
*   blackmail of threat actor, [151](#c10.xhtml#page_151), [152](#c10.xhtml#page_152)
*   bonus payments, [46](#c04.xhtml#page_46)
*   bounty/bounties, [33](#c04.xhtml#page_33) 
    *   enterprise, [86](#c06.xhtml#page_86)
    *   fair judgment on, [42](#c04.xhtml#page_42)–43
    *   hunter, [143](#c10.xhtml#page_143), [159](#c10.xhtml#page_159)
    *   option in HackerOne, [103](#c06.xhtml#page_103), [103](#c06.xhtml#page_103)f
    *   pool, [28](#c03.xhtml#page_28), [83](#c06.xhtml#page_83), [84](#c06.xhtml#page_84), [92](#c06.xhtml#page_92), [182](#c12.xhtml#page_182)
    *   professional, [86](#c06.xhtml#page_86)

*   brute force attacks, [33](#c04.xhtml#page_33), [38](#c04.xhtml#page_38)
*   bug bounty: 
    *   crowdsourcing platforms, [3](#c01.xhtml#page_3), [5](#c01.xhtml#page_5)–6, [24](#c03.xhtml#page_24), [93](#c06.xhtml#page_93)
    *   hunting, [28](#c03.xhtml#page_28), [44](#c04.xhtml#page_44), [143](#c10.xhtml#page_143), [159](#c10.xhtml#page_159)
    *   payments, [44](#c04.xhtml#page_44) 
        *   bonus payments, [46](#c04.xhtml#page_46)
        *   determining payments, [45](#c04.xhtml#page_45)–46
        *   nonmonetary rewards, [46](#c04.xhtml#page_46)–47
        *   setting bug bounty reward values and ranges, [48](#c04.xhtml#page_48)*t*

*   bug bounty programs (BBP), xiv, [3](#c01.xhtml#page_3), [6](#c01.xhtml#page_6), [7](#c01.xhtml#page_7), [19](#c02.xhtml#page_19) [29](#c03.xhtml#page_29), [155](#c10.xhtml#page_155), [185](#c13.xhtml#page_185) 
    
    *   applications, [5](#c01.xhtml#page_5)
    *   budgetary requirements, [5](#c01.xhtml#page_5)–6
    *   conservative blockers, [4](#c01.xhtml#page_4)
    *   increased threat actor activity, [4](#c01.xhtml#page_4)
    *   law, [7](#c01.xhtml#page_7)–8
    *   program managers, [7](#c01.xhtml#page_7), [167](#c11.xhtml#page_167), [171](#c11.xhtml#page_171) 
        *   interviews, [159](#c10.xhtml#page_159)–164
    
    *   redefining security research, [8](#c01.xhtml#page_8)
    *   running, [13](#c02.xhtml#page_13)
    *   scope of, [181](#c12.xhtml#page_181)
    *   security researcher scams, [5](#c01.xhtml#page_5)
    *   security tooling, [6](#c01.xhtml#page_6)
    *   taking action, [8](#c01.xhtml#page_8)–9
    *   VDP *vs*., [6](#c01.xhtml#page_6)–7
    *   for vulnerability management, [19](#c02.xhtml#page_19)–20

*   Bugcrowd, [3](#c01.xhtml#page_3), [5](#c01.xhtml#page_5), [6](#c01.xhtml#page_6), [27](#c03.xhtml#page_27). *See also* [HackerOne](#b01.xhtml#c1-idx-0265) 
    
    *   advanced program configuration and modification, [66](#c06.xhtml#page_66) 
        *   “add group” button, [70](#c06.xhtml#page_70)*f*
        *   “announcements” tab, [73](#c06.xhtml#page_73), [73](#c06.xhtml#page_73)f
        *   CVSS v3 score option, [75](#c06.xhtml#page_75), [75](#c06.xhtml#page_75)f
        *   data fields option, [75](#c06.xhtml#page_75), [75](#c06.xhtml#page_75)f
        *   description of asset group, [70](#c06.xhtml#page_70)*f*
        *   integrations tab, [72](#c06.xhtml#page_72)–73, [72](#c06.xhtml#page_72)f
        *   manage team section, [74](#c06.xhtml#page_74)–75, [74](#c06.xhtml#page_74)f
        *   “markdown embedded attachments” option, [76](#c06.xhtml#page_76), [76](#c06.xhtml#page_76)f
        *   profile dropdown menu, [68](#c06.xhtml#page_68)*f*
        *   program brief web page, [66](#c06.xhtml#page_66)–67, [66](#c06.xhtml#page_66)f
        *   program dropdown menu, [69](#c06.xhtml#page_69)*f*
        *   remediation advice option, [75](#c06.xhtml#page_75)–76, [76](#c06.xhtml#page_76)f
        *   retesting option, [76](#c06.xhtml#page_76), [76](#c06.xhtml#page_76)f
        *   scope and rewards section, [67](#c06.xhtml#page_67)–72
        *   scope details, [67](#c06.xhtml#page_67)*f*
        *   “submissions” tab, [75](#c06.xhtml#page_75)
        *   target group listings, [72](#c06.xhtml#page_72)*f*
        *   target group rewards, [71](#c06.xhtml#page_71)*f*
        *   target groups, [71](#c06.xhtml#page_71)*f*
        *   targets tab, [69](#c06.xhtml#page_69)*f*
        *   team member option, [74](#c06.xhtml#page_74)*f*
    
    *   documentation, [62](#c06.xhtml#page_62)*f*
    *   enterprise “profile” settings: 
        *   accounting page, [83](#c06.xhtml#page_83)–84
        *   activity summary, [83](#c06.xhtml#page_83)*f*
        *   authentication, [81](#c06.xhtml#page_81)
        *   domains, [82](#c06.xhtml#page_82)
        *   management and configuration, [81](#c06.xhtml#page_81)
        *   organization details, [81](#c06.xhtml#page_81)
        *   program balances option, [84](#c06.xhtml#page_84), [84](#c06.xhtml#page_84)f
        *   single sign-on option, [82](#c06.xhtml#page_82)f
        *   submit deposit request option, [83](#c06.xhtml#page_83)*f*
        *   targets, [81](#c06.xhtml#page_81)
        *   team members, [81](#c06.xhtml#page_81)
        *   transfer funds option, [83](#c06.xhtml#page_83), [84](#c06.xhtml#page_84)f
        *   unverified domains option, [82](#c06.xhtml#page_82)*f*
    
    *   profile settings, [76](#c06.xhtml#page_76) 
        *   API credentials, [80](#c06.xhtml#page_80), [80](#c06.xhtml#page_80)f
        *   events tab, [78](#c06.xhtml#page_78), [78](#c06.xhtml#page_78)f
        *   notification settings, [79](#c06.xhtml#page_79)–80, [80](#c06.xhtml#page_80)f
        *   “profile and account” tab, [78](#c06.xhtml#page_78)
        *   “profile and enterprise” sidebar, [76](#c06.xhtml#page_76), [77](#c06.xhtml#page_77)f
        *   profile option, [77](#c06.xhtml#page_77), [78](#c06.xhtml#page_78)f
        *   security settings, [78](#c06.xhtml#page_78), [78](#c06.xhtml#page_78)f
        *   two-factor authentication option, [78](#c06.xhtml#page_78), [79](#c06.xhtml#page_79)f
    
    *   program creation, [55](#c06.xhtml#page_55)–61 
        *   adding reward ranges by severity, [59](#c06.xhtml#page_59)*f*
        *   adding target, [57](#c06.xhtml#page_57)–58*f*
        *   “bug bounty program” selection, [56](#c06.xhtml#page_56)*f*
        *   identify goals and concerns, [59](#c06.xhtml#page_59)*f*
        *   program dropdown menu, [63](#c06.xhtml#page_63)*f*
        *   program name selection, [57](#c06.xhtml#page_57)*f*
        *   “start now” button, [55](#c06.xhtml#page_55)*f*
        *   uploading company’s logo and tagline and introduction creation, [61](#c06.xhtml#page_61)*f*
        *   vulnerability tasking tabs, [62](#c06.xhtml#page_62)*f*
    
    *   program overview, [61](#c06.xhtml#page_61) 
        *   crowd control navbar, [63](#c06.xhtml#page_63)–66
        *   program dashboard, [61](#c06.xhtml#page_61)–63

*   bug management, [116](#c07.xhtml#page_116) 
    *   projected ratings, [120](#c07.xhtml#page_120)
    *   ticketing and internal SLA, [120](#c07.xhtml#page_120)–121
    *   vulnerability: 
        *   complexity *vs*. rating, [119](#c07.xhtml#page_119)
        *   examples, [117](#c07.xhtml#page_117)–119
        *   priority, [116](#c07.xhtml#page_116)–117
        *   rating-test summary, [119](#c07.xhtml#page_119)

*   bug writeups, [9](#c01.xhtml#page_9)

*    
*   California Privacy Act, [6](#c01.xhtml#page_6)
*   chain report disclosure, [124](#c08.xhtml#page_124)–125
*   Checkmarx Codebashing, [15](#c02.xhtml#page_15)
*   CIA Triad (confidentiality, integrity, and availability), [94](#c06.xhtml#page_94), [94](#c06.xhtml#page_94)f
*   clickjacking, [39](#c04.xhtml#page_39)
*   common vulnerabilities and exposures (CVEs), [9](#c01.xhtml#page_9), [46](#c04.xhtml#page_46)–47, [126](#c08.xhtml#page_126), [131](#c08.xhtml#page_131), [169](#c11.xhtml#page_169) 
    *   CVE-2020–14179, [116](#c07.xhtml#page_116)–117
    *   disclosure, [130](#c08.xhtml#page_130)
    *   hardware, [126](#c08.xhtml#page_126), [127](#c08.xhtml#page_127)
    *   program manager responsibilities, [126](#c08.xhtml#page_126)
    *   remote code execution on partner software, [129](#c08.xhtml#page_129)
    *   software and product, [128](#c08.xhtml#page_128)
    *   SQL injection on router, [127](#c08.xhtml#page_127)
    *   stored XSS vulnerability, [128](#c08.xhtml#page_128)
    *   third-party, [128](#c08.xhtml#page_128)

*   common vulnerability scoring system (CVSS), [116](#c07.xhtml#page_116)–117 
    *   v3 score option, [75](#c06.xhtml#page_75), [75](#c06.xhtml#page_75)f

*   communication: 
    
    *   breakdown, [24](#c03.xhtml#page_24)
    *   expectations, [137](#c09.xhtml#page_137)–138
    *   information, [137](#c09.xhtml#page_137)
    *   processes, [15](#c02.xhtml#page_15)–16
    *   team, [14](#c02.xhtml#page_14) 
        *   BBP expectations, [19](#c02.xhtml#page_19)
        *   dealing with security researchers, [18](#c02.xhtml#page_18)
    
    *   vulnerability remediation, [14](#c02.xhtml#page_14)

*   complexity of vulnerability, [119](#c07.xhtml#page_119)
*   compliance: 
    *   and penetration testing criteria, [30](#c03.xhtml#page_30)
    *   practices, [17](#c02.xhtml#page_17)
    *   violations, [6](#c01.xhtml#page_6)

*   confidentiality, [94](#c06.xhtml#page_94), [146](#c10.xhtml#page_146)
*   conservative blockers, [4](#c01.xhtml#page_4)
*   credential stuffing, [33](#c04.xhtml#page_33)
*   critical vulnerability, [39](#c04.xhtml#page_39)–40, [45](#c04.xhtml#page_45), [118](#c07.xhtml#page_118), [150](#c10.xhtml#page_150)
*   cross-origin resource sharing policy (CORS policy), [146](#c10.xhtml#page_146)
*   cross-site request forgery vulnerability (CSRF vulnerability), [146](#c10.xhtml#page_146)–147
*   cross-site scripting (XSS), [39](#c04.xhtml#page_39), [137](#c09.xhtml#page_137) 
    *   reflected XSS on login portal, [117](#c07.xhtml#page_117), [118](#c07.xhtml#page_118)
    *   stored XSS abuse, [45](#c04.xhtml#page_45)
    *   stored XSS vulnerability, [128](#c08.xhtml#page_128)
    *   vulnerabilities, [68](#c06.xhtml#page_68)
    *   vulnerability, [117](#c07.xhtml#page_117)

*   crowd control navbar of Bugcrowd, [63](#c06.xhtml#page_63), [63](#c06.xhtml#page_63)f 
    *   insights dashboard, [65](#c06.xhtml#page_65)–66*f*
    *   program invitations tab, [64](#c06.xhtml#page_64), [64](#c06.xhtml#page_64)f
    *   program participants tab, [64](#c06.xhtml#page_64)*f*
    *   reports tab, [66](#c06.xhtml#page_66)
    *   researchers web page, [64](#c06.xhtml#page_64)
    *   rewards tab, [65](#c06.xhtml#page_65), [65](#c06.xhtml#page_65)f
    *   submissions panel, [63](#c06.xhtml#page_63), [64](#c06.xhtml#page_64)f
    *   summary page, [63](#c06.xhtml#page_63)

*   crowdsourced platforms, [27](#c03.xhtml#page_27)–28
*   crt.sh tool, [171](#c11.xhtml#page_171), [173](#c11.xhtml#page_173) 
    *   subdomain enumeration with, [173](#c11.xhtml#page_173)*f*

*   custom application plugins, [23](#c03.xhtml#page_23)
*   CVE numbering authorities (CNAs), [127](#c08.xhtml#page_127), [130](#c08.xhtml#page_130)
*   cybersecurity. *See* [information security (InfoSec)](#b01.xhtml#c1-idx-0330)

*    
*   DalFox tool, [177](#c11.xhtml#page_177) 
    *   available command, [178](#c11.xhtml#page_178)*f*
    *   identifying XSS instance, [178](#c11.xhtml#page_178), [178](#c11.xhtml#page_178)f
    *   XSS attack, [179](#c11.xhtml#page_179)*f*

*   deadlines, [130](#c08.xhtml#page_130), [139](#c09.xhtml#page_139) 
    *   missed, [136](#c09.xhtml#page_136), [139](#c09.xhtml#page_139)–141

*   demotivation scenario, [139](#c09.xhtml#page_139), [140](#c09.xhtml#page_140)
*   denial of service attacks (DOS attacks), [38](#c04.xhtml#page_38)
*   directory traversal vulnerability, [150](#c10.xhtml#page_150)
*   Dirsearch, [179](#c11.xhtml#page_179) 
    *   finding folders, [180](#c11.xhtml#page_180)*f*

*   Disclose (community), [9](#c01.xhtml#page_9)
*   disclosure. *See* [vulnerability disclosure](#b01.xhtml#c1-idx-0687)
*   disrespect scenario, [140](#c09.xhtml#page_140)
*   distributed denial of service attacks (DDoS attacks), [38](#c04.xhtml#page_38)
*   domain name system (DNS), [82](#c06.xhtml#page_82)
*   dynamic application security tools (DAST), [175](#c11.xhtml#page_175)

*    
*   edge tooling, [17](#c02.xhtml#page_17)
*   email enumeration, [38](#c04.xhtml#page_38)
*   enterprises, [4](#c01.xhtml#page_4)–5 
    *   assets, [167](#c11.xhtml#page_167)
    *   security program, [153](#c10.xhtml#page_153)
    *   space, [8](#c01.xhtml#page_8)
    *   vulnerability program managers, [24](#c03.xhtml#page_24)

*   ethical hacker. *See* [security researcher](#b01.xhtml#c1-idx-0082)
*   exploitation, [51](#c05.xhtml#page_51), [121](#c07.xhtml#page_121), [136](#c09.xhtml#page_136), [146](#c10.xhtml#page_146), [179](#c11.xhtml#page_179) 
    *   of disclosed report, [124](#c08.xhtml#page_124)
    *   full-scale, [23](#c03.xhtml#page_23)
    *   of IoT devices, [17](#c02.xhtml#page_17)
    *   of network and enterprises, [5](#c01.xhtml#page_5)
    *   paths, [42](#c04.xhtml#page_42)
    *   third-party risk and, [180](#c11.xhtml#page_180)
    *   use cases, [117](#c07.xhtml#page_117)

*    
*   false positives invalidation, [145](#c10.xhtml#page_145) 
    *   dealing with toxic hacker, [147](#c10.xhtml#page_147)
    *   intake process and breaking news, [145](#c10.xhtml#page_145)–147

*   fraud prevention, [14](#c02.xhtml#page_14), [16](#c02.xhtml#page_16)
*   fuzzing, [26](#c03.xhtml#page_26), [179](#c11.xhtml#page_179)

*    
*   Galitz, Geoff, [161](#c10.xhtml#page_161)–163
*   General Data Protection Regulation (GDPR), [6](#c01.xhtml#page_6)
*   graphical user interface (GUI), [175](#c11.xhtml#page_175)

*    
*   hacker(s), [8](#c01.xhtml#page_8), [9](#c01.xhtml#page_9), [21](#c03.xhtml#page_21), [22](#c03.xhtml#page_22), [143](#c10.xhtml#page_143), [180](#c11.xhtml#page_180) 
    *   active assessment, [173](#c11.xhtml#page_173)
    *   ethical. *See* [security researchers](#b01.xhtml#c1-idx-0498)
    *   ethical motivations of, [143](#c10.xhtml#page_143)–144. *See also* [security researchers](#b01.xhtml#c1-idx-0498)
    *   invitations, [99](#c06.xhtml#page_99), [99](#c06.xhtml#page_99)f
    *   issues in SQL vulnerability, [24](#c03.xhtml#page_24)–26
    *   malicious. *See* [threat actor](#b01.xhtml#c1-idx-0488)
    *   messaging, [101](#c06.xhtml#page_101), [101](#c06.xhtml#page_101)f
    *   money motivations of, [143](#c10.xhtml#page_143)–144. *See also* [threat actor](#b01.xhtml#c1-idx-0488)
    *   toxic. *See* [threat actor](#b01.xhtml#c1-idx-0261)

*   HackerOne, [5](#c01.xhtml#page_5), [6](#c01.xhtml#page_6), [27](#c03.xhtml#page_27), [84](#c06.xhtml#page_84). *See also* [Bugcrowd](#b01.xhtml#c1-idx-0087) 
    
    *   adding users option, [91](#c06.xhtml#page_91)*f*
    *   “audit log” option, [91](#c06.xhtml#page_91), [91](#c06.xhtml#page_91)f
    *   authentication, [87](#c06.xhtml#page_87)–88
    *   billing, [92](#c06.xhtml#page_92) 
        *   credit card portion, [92](#c06.xhtml#page_92)
        *   overview section, [92](#c06.xhtml#page_92), [92](#c06.xhtml#page_92)f
        *   prepayment tab, [92](#c06.xhtml#page_92)
    
    *   “credential management” tab, [89](#c06.xhtml#page_89), [89](#c06.xhtml#page_89)f
    *   general tab, [85](#c06.xhtml#page_85)
    *   “group management” tab, [89](#c06.xhtml#page_89)–90, [89](#c06.xhtml#page_89)f, [90](#c06.xhtml#page_90)f
    *   information tab, [86](#c06.xhtml#page_86)
    *   miscellaneous program options, [85](#c06.xhtml#page_85)*f*
    *   product editions, [86](#c06.xhtml#page_86), [87](#c06.xhtml#page_87)f
    *   “program settings” tab, [85](#c06.xhtml#page_85), [85](#c06.xhtml#page_85)f
    *   program subheader, [93](#c06.xhtml#page_93) 
        *   adding assets, [93](#c06.xhtml#page_93)*f*
        *   API settings, [107](#c06.xhtml#page_107)
        *   “bounties” tab, [103](#c06.xhtml#page_103), [103](#c06.xhtml#page_103)f
        *   CIA Triad, [94](#c06.xhtml#page_94), [94](#c06.xhtml#page_94)f
        *   “common responses” tab, [104](#c06.xhtml#page_104)–106, [104](#c06.xhtml#page_104)–105*f*
        *   “custom fields” tab, [98](#c06.xhtml#page_98)
        *   disclosure tab, [98](#c06.xhtml#page_98), [98](#c06.xhtml#page_98)f
        *   email forwarding function, [102](#c06.xhtml#page_102), [102](#c06.xhtml#page_102)f
        *   email notifications tab, [97](#c06.xhtml#page_97), [98](#c06.xhtml#page_98)f
        *   embedded submission form, [102](#c06.xhtml#page_102), [102](#c06.xhtml#page_102)f
        *   export reports option, [108](#c06.xhtml#page_108), [108](#c06.xhtml#page_108)f
        *   “Hackbot” tab, [107](#c06.xhtml#page_107), [107](#c06.xhtml#page_107)f
        *   inbox views tab, [98](#c06.xhtml#page_98), [98](#c06.xhtml#page_98)f
        *   inbox, [108](#c06.xhtml#page_108), [108](#c06.xhtml#page_108)f
        *   integrations, [107](#c06.xhtml#page_107)
        *   invitations option, [99](#c06.xhtml#page_99), [99](#c06.xhtml#page_99)f
        *   messaging hackers option, [101](#c06.xhtml#page_101), [101](#c06.xhtml#page_101)f
        *   metrics display tab, [97](#c06.xhtml#page_97), [97](#c06.xhtml#page_97)f
        *   policy tab, [93](#c06.xhtml#page_93)
        *   profile settings, 08
        *   public launch option, [99](#c06.xhtml#page_99), [99](#c06.xhtml#page_99)f
        *   report details, [109](#c06.xhtml#page_109), [109](#c06.xhtml#page_109)f
        *   “response targets” tab, [96](#c06.xhtml#page_96)–97, [96](#c06.xhtml#page_96)f
        *   scope configurations, [93](#c06.xhtml#page_93)–94
        *   submission tab, [100](#c06.xhtml#page_100)–101, [100](#c06.xhtml#page_100)f
        *   “submit report form” tab, [95](#c06.xhtml#page_95)–96, [95](#c06.xhtml#page_95)f
        *   swag tab, [103](#c06.xhtml#page_103)
        *   timeline option, [109](#c06.xhtml#page_109), [109](#c06.xhtml#page_109)f
        *   “triggers” tab, [106](#c06.xhtml#page_106)–107, [106](#c06.xhtml#page_106)f
    
    *   security page function, [86](#c06.xhtml#page_86)*f*
    *   single sign-on with SAML, [88](#c06.xhtml#page_88)*f*
    *   user management, [90](#c06.xhtml#page_90)
    *   “verify domains” tab, [88](#c06.xhtml#page_88), [88](#c06.xhtml#page_88)f

*   hacking, [3](#c01.xhtml#page_3), [7](#c01.xhtml#page_7) 
    *   API, [158](#c10.xhtml#page_158)
    *   art of. *See* [security research](#b01.xhtml#c1-idx-0082)
    *   ethical, [3](#c01.xhtml#page_3), [8](#c01.xhtml#page_8)
    *   flavors of, [49](#c05.xhtml#page_49)
    *   legal, [3](#c01.xhtml#page_3)
    *   network and web application, [173](#c11.xhtml#page_173)
    *   without permission, [22](#c03.xhtml#page_22)

*   “Hack the Pentagon” pilot program, xiv
*   hands-off submissions, [131](#c08.xhtml#page_131)–132
*   hardware CVEs, [126](#c08.xhtml#page_126), [127](#c08.xhtml#page_127)
*   Henry, Jackson, [155](#c10.xhtml#page_155)–156
*   “Human-augmented Signal”, [100](#c06.xhtml#page_100)
*   hybrid models of BBP, [26](#c03.xhtml#page_26)

*    
*   Iman, Ifrah, [156](#c10.xhtml#page_156)–157
*   in-between researchers, [144](#c10.xhtml#page_144)
*   information security (InfoSec), xviii, [3](#c01.xhtml#page_3), [6](#c01.xhtml#page_6), [8](#c01.xhtml#page_8)
*   infrastructure Teams, [14](#c02.xhtml#page_14) 
    *   effectiveness of communication, [18](#c02.xhtml#page_18)
    *   security practices, [17](#c02.xhtml#page_17)

*   in-house programs, [24](#c03.xhtml#page_24), [148](#c10.xhtml#page_148), [151](#c10.xhtml#page_151)
*   in-house submissions, [130](#c08.xhtml#page_130)
*   “in-scope”, [37](#c04.xhtml#page_37), [50](#c05.xhtml#page_50), [9](#c01.xhtml#page_9), [75](#c06.xhtml#page_75) 
    *   assets, [67](#c06.xhtml#page_67)

*   Integriti, [27](#c03.xhtml#page_27)
*   integrity, [94](#c06.xhtml#page_94), [146](#c10.xhtml#page_146)
*   internal assessments, [167](#c11.xhtml#page_167) 
    *   active assessments, [173](#c11.xhtml#page_173)–180
    *   passive assessments, [168](#c11.xhtml#page_168)–173
    *   proactive *vs*. reactive testing, [167](#c11.xhtml#page_167)
    *   professional testing and third-party risk, [180](#c11.xhtml#page_180)

*   Internet of Things (IoT), [17](#c02.xhtml#page_17)
*   internet service provider (ISP), [36](#c04.xhtml#page_36), [126](#c08.xhtml#page_126), [128](#c08.xhtml#page_128)

*    
*   Jira (ticketing system tool), [72](#c06.xhtml#page_72), [141](#c09.xhtml#page_141) 
    *   vulnerability, [117](#c07.xhtml#page_117)

*   judgment on bounties, [42](#c04.xhtml#page_42)–43

*    
*   Kali Linux, [172](#c11.xhtml#page_172)
*   Kinser, Jesse, [163](#c10.xhtml#page_163)–164

*    
*   law against hacking, [7](#c01.xhtml#page_7)–8
*   legal department, [14](#c02.xhtml#page_14) 
    *   criteria for escalation of issues, [18](#c02.xhtml#page_18)
    *   necessity of BBP management, [18](#c02.xhtml#page_18)
    *   relationship with application security team, [18](#c02.xhtml#page_18)

*   local file inclusion (LFI), [60](#c06.xhtml#page_60), [68](#c06.xhtml#page_68), [129](#c08.xhtml#page_129) 
    *   vulnerability, [119](#c07.xhtml#page_119)

*   Lohani, Sajeeb, [159](#c10.xhtml#page_159)–161
*   low vulnerability, [40](#c04.xhtml#page_40)

*    
*   malicious hacker. *See* [threat actor](#b01.xhtml#c1-idx-0261)
*   managed program, [147](#c10.xhtml#page_147)–148 
    *   toxic interactions, [149](#c10.xhtml#page_149)–151

*   managed services, [5](#c01.xhtml#page_5), [28](#c03.xhtml#page_28)–29, [52](#c05.xhtml#page_52), [115](#c07.xhtml#page_115)–117, [120](#c07.xhtml#page_120), [148](#c10.xhtml#page_148), [186](#c13.xhtml#page_186)
*   managed services, advanced, [29](#c03.xhtml#page_29)
*   messaging researchers, [155](#c10.xhtml#page_155) 
    *   BBP manager interviews, [159](#c10.xhtml#page_159)–164
    *   security researcher interviews, [155](#c10.xhtml#page_155)–159

*   miscommunication, [139](#c09.xhtml#page_139)–140
*   MITRE, [23](#c03.xhtml#page_23), [131](#c08.xhtml#page_131)–132
*   My Structured Query Language (MYSQL), [118](#c07.xhtml#page_118)

*    
*   Netscape Navigator 2. 0, [3](#c01.xhtml#page_3)
*   network address translation (NAT), [162](#c10.xhtml#page_162)
*   nmapAutomator.sh tool, [173](#c11.xhtml#page_173) 
    *   performing full scan of asset, [174](#c11.xhtml#page_174)*f*
    *   results, [174](#c11.xhtml#page_174)*f*
    *   scanning information, [174](#c11.xhtml#page_174)*f* 

*   nondisclosure agreements (NDAs), [43](#c04.xhtml#page_43), [44](#c04.xhtml#page_44), [130](#c08.xhtml#page_130), [153](#c10.xhtml#page_153)
*   nonmonetary rewards, [46](#c04.xhtml#page_46)–47

*    
*   Okta application, [81](#c06.xhtml#page_81)
*   on-demand penetration tests, [29](#c03.xhtml#page_29)–30
*   Open Bug Bounty, [152](#c10.xhtml#page_152)
*   open redirect vulnerability, [114](#c07.xhtml#page_114), [117](#c07.xhtml#page_117)–118
*   “out of scope”, [33](#c04.xhtml#page_33), [37](#c04.xhtml#page_37)–38, [144](#c10.xhtml#page_144), [146](#c10.xhtml#page_146), [149](#c10.xhtml#page_149) 
    *   assets, [39](#c04.xhtml#page_39)–40, [67](#c06.xhtml#page_67)
    *   research, [40](#c04.xhtml#page_40)–42

*   Owasp Zap tool, [175](#c11.xhtml#page_175)–176 
    *   potential vulnerability result, [176](#c11.xhtml#page_176)–177, [176](#c11.xhtml#page_176)f
    *   scan results, [176](#c11.xhtml#page_176)*f*
    *   setting up automated scan in, [176](#c11.xhtml#page_176)*f*
    *   XSS attack, [177](#c11.xhtml#page_177)*f*

*    
*   passive assessments, [168](#c11.xhtml#page_168). *See also* [active assessments](#b01.xhtml#c1-idx-0005) 
    *   Amass tool, [171](#c11.xhtml#page_171)–172
    *   crt.sh tool, [171](#c11.xhtml#page_171), [173](#c11.xhtml#page_173)
    *   Shodan tool, [168](#c11.xhtml#page_168)–171

*   Paxton-Fear, Katie, [157](#c10.xhtml#page_157)–159
*   payments, [45](#c04.xhtml#page_45)–46 
    *   bonus, [46](#c04.xhtml#page_46)
    *   bug bounty, [44](#c04.xhtml#page_44)–47

*   “Pentest” active board, [173](#c11.xhtml#page_173)
*   personally identifiable information (PII), [18](#c02.xhtml#page_18), [22](#c03.xhtml#page_22), [24](#c03.xhtml#page_24), [45](#c04.xhtml#page_45), [119](#c07.xhtml#page_119)
*   platform pricing and services, [28](#c03.xhtml#page_28)
*   private programs, [6](#c01.xhtml#page_6), [25](#c03.xhtml#page_25), [26](#c03.xhtml#page_26). *See also* public programs 
    *   for vulnerability disclosure, [123](#c08.xhtml#page_123) 
        *   ad hoc redactions, [124](#c08.xhtml#page_124)
        *   allowing disclosure, [123](#c08.xhtml#page_123)–124
        *   bottom line, [124](#c08.xhtml#page_124)–125
        *   disclosure restrictions, [124](#c08.xhtml#page_124)

*   private VDPs, [7](#c01.xhtml#page_7)
*   proactive testing, [167](#c11.xhtml#page_167)
*   product CVEs, [128](#c08.xhtml#page_128)
*   professional testing, [180](#c11.xhtml#page_180)
*   program configuration, [21](#c03.xhtml#page_21). *See also* [bug bounty programs (BBP)](#b01.xhtml#c1-idx-0071) 
    *   advanced, [66](#c06.xhtml#page_66)
    *   Bugcrowd. *See* [Bugcrowd](#b01.xhtml#c1-idx-0087)
    *   HackerOne. *See* [HackerOne](#b01.xhtml#c1-idx-0265)
    *   understanding options, [55](#c06.xhtml#page_55)

*   program interaction essentials. *See also* [bug bounty programs (BBP)](#b01.xhtml#c1-idx-0071) 
    *   false positives invalidation, [145](#c10.xhtml#page_145)–147
    *   finding blackmail or threat actor, [151](#c10.xhtml#page_151)
    *   finding public threats or disclosure, [151](#c10.xhtml#page_151)–153
    *   finding threat actor or security researcher, [153](#c10.xhtml#page_153)–155
    *   in-house programs, [148](#c10.xhtml#page_148)
    *   managed program considerations, [147](#c10.xhtml#page_147)–151
    *   messaging researchers, [155](#c10.xhtml#page_155)–164
    *   program warning messages, [153](#c10.xhtml#page_153)

*   program managed submissions, [130](#c08.xhtml#page_130)–131
*   program managers, [5](#c01.xhtml#page_5), [7](#c01.xhtml#page_7), [9](#c01.xhtml#page_9) 
    *   allowing public disclosure, [126](#c08.xhtml#page_126)
    *   blocking trafficking, [153](#c10.xhtml#page_153)
    *   bug bounty, [26](#c03.xhtml#page_26), [45](#c04.xhtml#page_45), [171](#c11.xhtml#page_171)
    *   communication with team, [181](#c12.xhtml#page_181)
    *   enterprise vulnerability, [24](#c03.xhtml#page_24)
    *   future, [15](#c02.xhtml#page_15), [19](#c02.xhtml#page_19), [21](#c03.xhtml#page_21)
    *   Geoff Galitz, [161](#c10.xhtml#page_161)–163
    *   inviting security researchers, [183](#c12.xhtml#page_183)
    *   Jesse Kinser, [163](#c10.xhtml#page_163)–164
    *   obligation to follow up in vulnerability remediation process, [141](#c09.xhtml#page_141)
    *   in passive assessments, [168](#c11.xhtml#page_168)
    *   proactive, [136](#c09.xhtml#page_136)
    *   public program launch, [61](#c06.xhtml#page_61)
    *   responsibilities in CVEs, [126](#c08.xhtml#page_126)
    *   role in API credentials, [80](#c06.xhtml#page_80)
    *   role in releasing BBP, [186](#c13.xhtml#page_186)
    *   Sajeeb Lohani, [159](#c10.xhtml#page_159)–161
    *   in scope expansion, [182](#c12.xhtml#page_182)
    *   tuning profile settings, [76](#c06.xhtml#page_76), [78](#c06.xhtml#page_78)
    *   understanding of penetration testing, [167](#c11.xhtml#page_167)
    *   writing safe harbor agreement, [49](#c05.xhtml#page_49), [58](#c06.xhtml#page_58)

*   program operations evaluation: 
    *   ad hoc program, [22](#c03.xhtml#page_22)–23
    *   applied knowledge scenarios, [24](#c03.xhtml#page_24)–26
    *   crowdsourced platforms, [27](#c03.xhtml#page_27)–28
    *   managed services, [28](#c03.xhtml#page_28)–29
    *   note, [24](#c03.xhtml#page_24)
    *   on-demand penetration tests, [29](#c03.xhtml#page_29)–30
    *   one size does not fit all, [21](#c03.xhtml#page_21)
    *   platform pricing and services, [28](#c03.xhtml#page_28)
    *   realistic program scenarios, [21](#c03.xhtml#page_21)–22

*   program readiness in vulnerability management, [19](#c02.xhtml#page_19)–20
*   program warning messages, [153](#c10.xhtml#page_153)
*   “proof of concept” process, [27](#c03.xhtml#page_27), [131](#c08.xhtml#page_131), [146](#c10.xhtml#page_146) 
    *   CSRF vulnerability, [146](#c10.xhtml#page_146), [147](#c10.xhtml#page_147)
    *   security research, [38](#c04.xhtml#page_38)
    *   timeline, [109](#c06.xhtml#page_109)

*   public disclosure, [123](#c08.xhtml#page_123), [153](#c10.xhtml#page_153). *See also* [vulnerability disclosure](#b01.xhtml#c1-idx-0687) 
    *   decision making, [123](#c08.xhtml#page_123)–126

*   public program, [25](#c03.xhtml#page_25)–26, [185](#c13.xhtml#page_185). *See also* [private programs](#b01.xhtml#c1-idx-0403) 
    *   launch time, [185](#c13.xhtml#page_185)–186
    *   recommended release, [186](#c13.xhtml#page_186)
    *   rolling backwards, [186](#c13.xhtml#page_186)–187
    *   for vulnerability disclosure, [125](#c08.xhtml#page_125) 
        *   bottom line, [126](#c08.xhtml#page_126)
        *   full public disclosure, [125](#c08.xhtml#page_125)–126

*   public program launch, [61](#c06.xhtml#page_61)
*   public threats, [151](#c10.xhtml#page_151)–153

*    
*   rate limiting, [38](#c04.xhtml#page_38), [153](#c10.xhtml#page_153) 
    *   rules, [155](#c10.xhtml#page_155)

*   rating: 
    *   high integrity impact, [94](#c06.xhtml#page_94)
    *   VRT, [58](#c06.xhtml#page_58)
    *   of vulnerability, [53](#c05.xhtml#page_53)*t*, [54](#c05.xhtml#page_54)*t*, [119](#c07.xhtml#page_119)

*   reactive testing, [167](#c11.xhtml#page_167)
*   realistic program scenarios, [21](#c03.xhtml#page_21)–22
*   remote code execution, [5](#c01.xhtml#page_5), [60](#c06.xhtml#page_60), [68](#c06.xhtml#page_68), [94](#c06.xhtml#page_94), [149](#c10.xhtml#page_149) 
    *   on partner software, [129](#c08.xhtml#page_129)
    *   stack based buffer overflow, [119](#c07.xhtml#page_119)
    *   threat actor achieving, [171](#c11.xhtml#page_171)
    *   vulnerability, [140](#c09.xhtml#page_140)

*   remote file inclusion (RFI), [119](#c07.xhtml#page_119), [129](#c08.xhtml#page_129)
*   reputational damage, [43](#c04.xhtml#page_43)–44, [115](#c07.xhtml#page_115)
*   resolution processes, [9](#c01.xhtml#page_9), [52](#c05.xhtml#page_52), [136](#c09.xhtml#page_136)–138, [140](#c09.xhtml#page_140), [141](#c09.xhtml#page_141)
*   resolution times, [53](#c05.xhtml#page_53), [53](#c05.xhtml#page_53)t
*   retaliation against rogue researcher, [51](#c05.xhtml#page_51)–52
*   rewards, [85](#c06.xhtml#page_85) 
    *   of BBPs, [7](#c01.xhtml#page_7)
    *   nonmonetary, [46](#c04.xhtml#page_46)–47
    *   security researchers, [28](#c03.xhtml#page_28)

*   risk identification process in Shodan, [170](#c11.xhtml#page_170)

*    
*   safe harbor, [49](#c05.xhtml#page_49), [67](#c06.xhtml#page_67)–68 
    *   agreements, [50](#c05.xhtml#page_50), [50](#c05.xhtml#page_50)t
    *   clauses, [8](#c01.xhtml#page_8)
    *   fear and reluctance, [49](#c05.xhtml#page_49)
    *   reality of, [49](#c05.xhtml#page_49)

*   scope, [33](#c04.xhtml#page_33) 
    
    *   asset allocation, [36](#c04.xhtml#page_36)–37
    *   asset risk, [37](#c04.xhtml#page_37)
    *   configurations within HackerOne, [93](#c06.xhtml#page_93)
    *   creation, [34](#c04.xhtml#page_34)
    *   expansion, [181](#c12.xhtml#page_181) 
        *   alternatives, [183](#c12.xhtml#page_183)
        *   communication with team, [181](#c12.xhtml#page_181)–182
        *   costs, [182](#c12.xhtml#page_182)
        *   management, [183](#c12.xhtml#page_183)
        *   timing, [182](#c12.xhtml#page_182)
    
    *   “in scope”, [37](#c04.xhtml#page_37)
    *   models, [34](#c04.xhtml#page_34)
    *   “out of scope”, [37](#c04.xhtml#page_37)–38, [40](#c04.xhtml#page_40)–42

*   secure shell version (SSH version), [114](#c07.xhtml#page_114)
*   security: 
    *   awareness incentives, [15](#c02.xhtml#page_15)
    *   operations, [14](#c02.xhtml#page_14), [16](#c02.xhtml#page_16), [18](#c02.xhtml#page_18)
    *   tooling for BBP, [6](#c01.xhtml#page_6)

*   Security Assertion Markup Language (SAML), [81](#c06.xhtml#page_81) 
    *   single sign-on with, [88](#c06.xhtml#page_88)*f*

*   security departments, [14](#c02.xhtml#page_14) 
    *   compliance practices, [17](#c02.xhtml#page_17)
    *   edge tooling, [17](#c02.xhtml#page_17)
    *   fraud prevention, [16](#c02.xhtml#page_16)
    *   security operations, [16](#c02.xhtml#page_16)
    *   team coordination for resolution, [17](#c02.xhtml#page_17)

*   security information and event management (SIEM), [51](#c05.xhtml#page_51)
*   security posture, [6](#c01.xhtml#page_6), [13](#c02.xhtml#page_13)–14, [22](#c03.xhtml#page_22) 
    *   baseline, [25](#c03.xhtml#page_25)
    *   enterprise, [58](#c06.xhtml#page_58), [59](#c06.xhtml#page_59), [96](#c06.xhtml#page_96)

*   security research, [3](#c01.xhtml#page_3), [143](#c10.xhtml#page_143) 
    *   activity, [125](#c08.xhtml#page_125)
    *   crowdsourcing platform, [28](#c03.xhtml#page_28), [29](#c03.xhtml#page_29)
    *   expectations of, [7](#c01.xhtml#page_7)–8
    *   financial incentive for, [7](#c01.xhtml#page_7)
    *   redefining, [8](#c01.xhtml#page_8)
    *   toxic, [148](#c10.xhtml#page_148)

*   security researchers, [9](#c01.xhtml#page_9), [124](#c08.xhtml#page_124), [143](#c10.xhtml#page_143), [153](#c10.xhtml#page_153)–155 
    
    *   case study analysis, [145](#c10.xhtml#page_145)
    *   disclosing unpatched vulnerability, [152](#c10.xhtml#page_152)
    *   Ifrah Iman, [156](#c10.xhtml#page_156)–157
    *   in-between researchers, [144](#c10.xhtml#page_144), [145](#c10.xhtml#page_145)
    *   Jackson Henry, [155](#c10.xhtml#page_155)–156
    *   Katie Paxton-Fear, [157](#c10.xhtml#page_157)–159
    *   scams, [5](#c01.xhtml#page_5)
    *   threatening to disclose: 
        *   on Open Bug Bounty, [152](#c10.xhtml#page_152)
        *   on social media, [152](#c10.xhtml#page_152)–153
    
    *   to triage, [42](#c04.xhtml#page_42)

*   security.txt, [26](#c03.xhtml#page_26)
*   self-service, [116](#c07.xhtml#page_116)
*   self-XSS vulnerability, [39](#c04.xhtml#page_39), [45](#c04.xhtml#page_45)
*   server-side request forgery (SSRF), [114](#c07.xhtml#page_114), [118](#c07.xhtml#page_118), [137](#c09.xhtml#page_137) 
    *   vulnerability, [138](#c09.xhtml#page_138)

*   service level agreements (SLAs), [52](#c05.xhtml#page_52)–53, [117](#c07.xhtml#page_117), [136](#c09.xhtml#page_136), [139](#c09.xhtml#page_139), [141](#c09.xhtml#page_141), [160](#c10.xhtml#page_160) 
    *   guidelines, [37](#c04.xhtml#page_37)
    *   resolution times, [53](#c05.xhtml#page_53)
    *   ticketing and internal, [120](#c07.xhtml#page_120)–121
    *   triage times, [53](#c05.xhtml#page_53)–54

*   ServiceNow (ticketing system tool), [72](#c06.xhtml#page_72)
*   Shodan tool, [168](#c11.xhtml#page_168) 
    *   asset analysis, [169](#c11.xhtml#page_169), [170](#c11.xhtml#page_170)f
    *   browser search, [168](#c11.xhtml#page_168)*f*
    *   generating results, [169](#c11.xhtml#page_169)*f*
    *   Google search results, [171](#c11.xhtml#page_171)*f*
    *   risk identification process, [170](#c11.xhtml#page_170)–171
    *   search bar, [168](#c11.xhtml#page_168)–169, [169](#c11.xhtml#page_169)f
    *   services analysis, [170](#c11.xhtml#page_170), [170](#c11.xhtml#page_170)f

*   single sign-on (SSO), [81](#c06.xhtml#page_81)–82, [82](#c06.xhtml#page_82)f, [87](#c06.xhtml#page_87), [88](#c06.xhtml#page_88)
*   Slack (ticketing system tool), [72](#c06.xhtml#page_72)
*   slippery slope logical fallacy, [4](#c01.xhtml#page_4), [125](#c08.xhtml#page_125), [144](#c10.xhtml#page_144)
*   Sn1per tool, [175](#c11.xhtml#page_175) 
    *   running Metasploit modules, [175](#c11.xhtml#page_175)*f*
    *   running Nmap scripts, [175](#c11.xhtml#page_175)*f*

*   social engineering, [45](#c04.xhtml#page_45), [51](#c05.xhtml#page_51), [138](#c09.xhtml#page_138) 
    *   attacks, [38](#c04.xhtml#page_38), [128](#c08.xhtml#page_128)

*   social media, [44](#c04.xhtml#page_44) 
    *   communications team dealing through, [18](#c02.xhtml#page_18), [19](#c02.xhtml#page_19)
    *   marketing, [14](#c02.xhtml#page_14)
    *   risk of researcher leaking vulnerability through, [51](#c05.xhtml#page_51), [52](#c05.xhtml#page_52)
    *   security researcher threatening to disclose, [152](#c10.xhtml#page_152)
    *   temporary posts, [131](#c08.xhtml#page_131)

*   software CVEs, [128](#c08.xhtml#page_128)
*   software development lifecycle (SDLC), [16](#c02.xhtml#page_16), [30](#c03.xhtml#page_30), [116](#c07.xhtml#page_116)
*   software engineering, [15](#c02.xhtml#page_15) 
    *   distrust, [115](#c07.xhtml#page_115)
    *   effectiveness of communication processes, [15](#c02.xhtml#page_15)–16
    *   process for coding security, [15](#c02.xhtml#page_15)
    *   process for SDLC, [16](#c02.xhtml#page_16)
    *   teams, [14](#c02.xhtml#page_14)

*   software security, xiv
*   SQLMap, [22](#c03.xhtml#page_22), [154](#c10.xhtml#page_154)
*   standard model of BBP, [26](#c03.xhtml#page_26)
*   Streisand effect, [51](#c05.xhtml#page_51)
*   Structured Query Language (SQL), [5](#c01.xhtml#page_5) 
    
    *   credentials, [42](#c04.xhtml#page_42)
    *   injection, [5](#c01.xhtml#page_5), [22](#c03.xhtml#page_22), [154](#c10.xhtml#page_154) 
        *   on router, [127](#c08.xhtml#page_127)
    
    *   leaked internal SQL server credentials, [118](#c07.xhtml#page_118)–119
    *   vulnerability, [24](#c03.xhtml#page_24)–26

*   subdomain(s), [34](#c04.xhtml#page_34)–36, [129](#c08.xhtml#page_129), [171](#c11.xhtml#page_171) 
    *   enumeration, [171](#c11.xhtml#page_171)–173, [173](#c11.xhtml#page_173)f
    *   in Nano, [172](#c11.xhtml#page_172)*f*
    *   takeover vulnerability, [17](#c02.xhtml#page_17)

*   submission options in vulnerability disclosure, [130](#c08.xhtml#page_130) 
    *   hands-off submissions, [131](#c08.xhtml#page_131)–132
    *   in-house submissions, [130](#c08.xhtml#page_130)
    *   program managed submissions, [130](#c08.xhtml#page_130)–131

*   swag, [46](#c04.xhtml#page_46)–47, [103](#c06.xhtml#page_103)
*   Synack, [27](#c03.xhtml#page_27)

*    
*   targets. *See* [asset(s)](#b01.xhtml#c1-idx-0043)
*   text record (TXT), [82](#c06.xhtml#page_82)
*   third-party: 
    *   bug bounty program, [23](#c03.xhtml#page_23)
    *   crowdsourced research platform, [23](#c03.xhtml#page_23)
    *   CVEs, [128](#c08.xhtml#page_128)
    *   penetration testing company, [30](#c03.xhtml#page_30)
    *   risk, [180](#c11.xhtml#page_180)
    *   security relationships, [17](#c02.xhtml#page_17)
    *   third-party, [149](#c10.xhtml#page_149)

*   threat actor, [9](#c01.xhtml#page_9), [51](#c05.xhtml#page_51), [52](#c05.xhtml#page_52), [151](#c10.xhtml#page_151), [153](#c10.xhtml#page_153)–155 
    *   achieving remote code execution on server, [171](#c11.xhtml#page_171)
    *   activity, [4](#c01.xhtml#page_4), [16](#c02.xhtml#page_16)
    *   blackmails or disclosing vulnerability, [152](#c10.xhtml#page_152)
    *   dealing with, [147](#c10.xhtml#page_147)
    *   needs to performing reconnaissance, [168](#c11.xhtml#page_168)
    *   risk of getting BBP login access, [76](#c06.xhtml#page_76)

*   ticketing systems, [120](#c07.xhtml#page_120)–121, [141](#c09.xhtml#page_141) 
    *   tool, [72](#c06.xhtml#page_72)

*   ticking clock. *See* [service level agreement (SLA)](#b01.xhtml#c1-idx-0560)
*   timeline option in HackerOne, [109](#c06.xhtml#page_109), [109](#c06.xhtml#page_109)f
*   toxic hacker. *See* [threat actor](#b01.xhtml#c1-idx-0261)
*   tracking, [83](#c06.xhtml#page_83), [138](#c09.xhtml#page_138), [141](#c09.xhtml#page_141)
*   triage, [113](#c07.xhtml#page_113) 
    *   evaluation stage, [115](#c07.xhtml#page_115)
    *   managed services, [115](#c07.xhtml#page_115)–116
    *   to program, [42](#c04.xhtml#page_42)–43
    *   to researcher, [43](#c04.xhtml#page_43)
    *   security researcher to, [42](#c04.xhtml#page_42)
    *   self-service, [116](#c07.xhtml#page_116)
    *   times, [53](#c05.xhtml#page_53), [54](#c05.xhtml#page_54)t, [96](#c06.xhtml#page_96)
    *   vulnerability, [28](#c03.xhtml#page_28), [120](#c07.xhtml#page_120) 
        *   mishaps, [115](#c07.xhtml#page_115)
        *   validation, [113](#c07.xhtml#page_113)–114

*   triage team: 
    *   assisting in validating legitimacy, [5](#c01.xhtml#page_5)
    *   evaluating vulnerability, [146](#c10.xhtml#page_146)
    *   maintaining responsibility of validation, [145](#c10.xhtml#page_145)
    *   managed vulnerability disclosure program, [6](#c01.xhtml#page_6)

*   two-factor authentication (TFA), [78](#c06.xhtml#page_78), [79](#c06.xhtml#page_79)f, [81](#c06.xhtml#page_81), [101](#c06.xhtml#page_101)

*    
*   UI redress attack. *See* [clickjacking](#b01.xhtml#c1-idx-0160)
*   unmanaged VDPs, [6](#c01.xhtml#page_6)

*    
*   virtual private network (VPN), [153](#c10.xhtml#page_153)
*   vulnerability. *See also* [common vulnerabilities and exposures (CVEs)](#b01.xhtml#c1-idx-0161) 
    
    *   account and email enumeration, [38](#c04.xhtml#page_38)
    *   awareness and reputational damage, [43](#c04.xhtml#page_43)–44
    *   brute force or rate limiting, [38](#c04.xhtml#page_38)
    *   bug bounty payments, [44](#c04.xhtml#page_44)–47
    *   clickjacking, [39](#c04.xhtml#page_39)
    *   disclosure information: 
        *   CVEs, [126](#c08.xhtml#page_126)–129
        *   public disclosure, [123](#c08.xhtml#page_123)–126
        *   submission options, [130](#c08.xhtml#page_130)–132
    
    *   DOS or DDoS attacks, [38](#c04.xhtml#page_38)
    *   examples: 
        *   leaked internal SQL server credentials, [118](#c07.xhtml#page_118)–119
        *   open redirect vulnerability, [117](#c07.xhtml#page_117)–118
        *   reflected XSS on login portal, [117](#c07.xhtml#page_117), [118](#c07.xhtml#page_118)
    
    *   identification, xiv
    *   miscellaneous attacks, [39](#c04.xhtml#page_39)
    *   mishaps, [115](#c07.xhtml#page_115)
    *   priority, [116](#c07.xhtml#page_116)–117
    *   rating-test summary, [119](#c07.xhtml#page_119)
    *   remediation, [15](#c02.xhtml#page_15)–16, [141](#c09.xhtml#page_141), [147](#c10.xhtml#page_147) 
        *   communication, [14](#c02.xhtml#page_14)
        *   transparency control, [123](#c08.xhtml#page_123)
    
    *   reporting, [136](#c09.xhtml#page_136)–137 
        *   management, [4](#c01.xhtml#page_4)
    
    *   reviewing reporting process, [43](#c04.xhtml#page_43)
    *   self-XSS, [39](#c04.xhtml#page_39)
    *   social engineering attacks, [38](#c04.xhtml#page_38)

*   vulnerability disclosure programs (VDPs), [3](#c01.xhtml#page_3), [6](#c01.xhtml#page_6)–8, [151](#c10.xhtml#page_151)–153 
    *   custom-built, [24](#c03.xhtml#page_24)
    *   management, [9](#c01.xhtml#page_9)
    *   public program, [25](#c03.xhtml#page_25)–26, [128](#c08.xhtml#page_128)

*   vulnerability management processes: 
    *   communications team, [14](#c02.xhtml#page_14), [18](#c02.xhtml#page_18)–19
    *   engineers responsibility, [19](#c02.xhtml#page_19)
    *   infrastructure teams, [14](#c02.xhtml#page_14), [17](#c02.xhtml#page_17)–18
    *   legal department, [14](#c02.xhtml#page_14), [18](#c02.xhtml#page_18)
    *   management, [14](#c02.xhtml#page_14)
    *   program readiness, [19](#c02.xhtml#page_19)–20
    *   questions in, [15](#c02.xhtml#page_15)
    *   running BBP, [13](#c02.xhtml#page_13)
    *   security departments, [14](#c02.xhtml#page_14), [16](#c02.xhtml#page_16)–17
    *   security posture, [13](#c02.xhtml#page_13)–14
    *   software engineering, [14](#c02.xhtml#page_14), [15](#c02.xhtml#page_15)–16

*   vulnerability rating taxonomy (VRT), [58](#c06.xhtml#page_58)

*    
*   web applications, [23](#c03.xhtml#page_23), [26](#c03.xhtml#page_26), [36](#c04.xhtml#page_36) 
    *   Dirsearch tool for, [176](#c11.xhtml#page_176)
    *   firewall, [4](#c01.xhtml#page_4), [6](#c01.xhtml#page_6), [51](#c05.xhtml#page_51), [153](#c10.xhtml#page_153)
    *   nmapAutomator tool for, [173](#c11.xhtml#page_173)
    *   OWASP ZAP tool for, [175](#c11.xhtml#page_175)–176
    *   security, xiv
    *   server-side, [17](#c02.xhtml#page_17)
    *   Sn1per tool for, [175](#c11.xhtml#page_175)

*   wildcards, [34](#c04.xhtml#page_34)–35 
    *   specific domain path, [35](#c04.xhtml#page_35)
    *   specific subdomain path, [35](#c04.xhtml#page_35)
    *   use on domain, [35](#c04.xhtml#page_35)
    *   use on subdomain, [35](#c04.xhtml#page_35)

# WILEY END USER LICENSE AGREEMENT

Go to [www.wiley.com/go/eula](http://www.wiley.com/go/eula) to access Wiley’s ebook EULA.