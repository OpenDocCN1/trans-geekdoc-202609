
## PRACTICAL CORE SOFTWARE SECURITY
### A REFERENCE FRAMEWORK

JAMES F. RANSOME
ANMOL MISRA
MARK S. MERKOW

CRC Press
Taylor & Francis Group
AN AUERBACH BOOK

## PRACTICAL CORE SOFTWARE SECURITY

As long as humans write software, the key to successful software security is making the software development program process more efficient and effective. Although the approach of this textbook includes people, process, and technology approaches to software security, Practical Core Software Security: A Reference Framework stresses the people element of software security, which is still the most important part to manage as software is developed, controlled, and exploited by humans.

The text outlines a step-by-step process for software security that is relevant to today’s technical, operational, business, and development environments. It focuses on what humans can do to control and manage a secure software development process using best practices and metrics. Although security issues will always exist, students learn how to maximize an organization’s ability to minimize vulnerabilities in software products before they are released or deployed by building security into the development process.

The authors have worked with Fortune 500 companies and have often seen examples of the breakdown of security development lifecycle (SDL) practices. The text takes an experience-based approach to apply components of the best available SDL models in dealing with the problems described above. Software security best practices, an SDL model, and framework are presented in this book. Starting with an overview of the SDL, the text outlines a model for mapping SDL best practices to the software development life cycle (SDLC). It explains how to use this model to build and manage a mature SDL program. Exercises and an in-depth case study aid students in mastering the SDL model.

Professionals skilled in secure software development and related tasks are in tremendous demand today. The industry continues to experience exponential demand that should continue to grow for the foreseeable future. This book can benefit professionals as much as students. As they integrate the book’s ideas into their software security practices, their value increases to their organizations, management teams, community, and industry.

## About the Authors

Dr. James Ransome, PhD, CISSP, CISM is a veteran chief information security officer (CISO), chief security officer (CSO), and chief production security officer (CPSO), as well as an author and co-author of numerous cybersecurity books.

Anmol Misra is an accomplished leader, researcher, author, and security expert with over 16 years of experience in technology and cybersecurity.

Mark S. Merkow, CISSP, CISM, CSSLP has over 25 years of experience in corporate information security and 17 years in the AppSec space helping to establish and lead application security initiatives to success and sustainment.

Some material in this book is taken from the following books written by one or both of the authors, with permission from Taylor & Francis Group:

| Book | ISBN | Year |
|---|---|---|
| Core Software Security: Security at the Source | 9781466560956 | 2013 |
| Secure, Resilient, and Agile Software Development | 978-0367332594 | 2019 |

## PRACTICAL CORE SOFTWARE SECURITY
### A Reference Framework

James F. Ransome
Anmol Misra
Mark S. Merkow

CRC Press
Taylor & Francis Group
Boca Raton London New York

CRC Press is an imprint of the Taylor & Francis Group, an informa business
AN AUERBACH BOOK

First Edition published 2023
by CRC Press
6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

CRC Press is an imprint of Taylor & Francis Group, LLC

© 2023 James F. Ransome, Anmol Misra and Mark S. Merkow

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access www.copyright.com or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact mpkbookspermissions@tandf.co.uk

Trademark notice: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-1-032-33314-4 (hbk)
ISBN: 978-1-032-27603-8 (pbk)
ISBN: 978-1-003-31907-8 (ebk)

DOI: 10.1201/97810033319078

Typeset in Adobe Garamond Pro
by DerryField Publishing Services

## Dedications

To the next generation of defensive cyber warriors who will provide core software security to the world's software.

— James Ransome

To software security professionals committed to building secure software.

— Anmol Misra

This book is dedicated to the next generation of application security professionals to help alleviate the struggle to reverse the curses of defective software, no matter where they show up.

— Mark Merkow

![](img/a54ed04827050a271316d34985425127_6_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Contents

- Dedications v
- Contents vii
- List of Figures xiii
- List of Tables xv
- Preface xvii
- About the Book xviii
- Audience xix
- Support xix
- Structure xix
- Assumptions xix
- Acknowledgments xxi
- About the Authors xxiii
- Chapter 1: Introduction 1
- CHAPTER OVERVIEW 1
- CHAPTER TAKE-AWAYS 1
- 1.1 The Importance and Relevance of Software Security 2
- 1.2 Software Security and the Software Development Life Cycle 5
- 1.3 Quality Versus Secure Code 7
- 1.4 The Three Most Important SDL Security Goals 8
- 1.5 Threat Modeling and Attack Surface Validation 9
- 1.6 Summary 11
- Chapter Quick-Check 11
- Exercises 12
- References 12
- Chapter 2: The Security Development Lifecycle 15
- CHAPTER OVERVIEW 15
- CHAPTER TAKE-AWAYS 15
- 2.1 Overcoming Challenges in Making Software Secure 16
- 2.2 Software Security Maturity Models 17
- 2.3 ISO/IEC 27034—Information Technology—Security Techniques—Application Security 18
- 2.4 Other Resources for SDL Best Practices 19
- 2.4.1 SAFECode 19
- 2.4.2 U.S. Department of Homeland Security Software Assurance Program 19
- 2.4.3 National Institute of Standards and Technology 20
- 2.4.4 Common Computer Vulnerabilities and Exposures 21
- 2.4.5 SANS Institute Top Cyber Security Risks 22
- 2.4.6 U.S. Department of Defense Cyber Security and Information Systems Information Analysis Center (CSIAC) 23
- 2.4.7 CERT, Bugtraq®, and SecurityFocus 23
- 2.5 Critical Tools and Talent 23
- 2.5.1 The Tools 24
- 2.5.2 The Talent 25
- 2.6 Principles of Least Privilege 29
- 2.7 Privacy 30
- 2.8 The Importance of Metrics 31
- 2.9 Mapping the Security Development Lifecycle to the Software Development Life Cycle 33
- 2.10 Software Development Methodologies 35
- 2.10.1 Waterfall Development 39
- 2.10.2 Agile Development 40
- 2.11 Summary 43
- Chapter Quick-Check 43
- Exercises 44
- References 44
- Chapter 3: Security Assessment (A1): SDL Activities and Best Practices 47
- CHAPTER OVERVIEW 47
- CHAPTER TAKE-AWAYS 47
- 3.1 Software Security Team Is Looped in Early 47
- 3.2 Software Security Hosts a Discovery Meeting 49
- 3.3 Software Security Team Creates an SDL Project Plan 51
- 3.4 Privacy Impact Assessment (PIA) Plan Initiated 51
