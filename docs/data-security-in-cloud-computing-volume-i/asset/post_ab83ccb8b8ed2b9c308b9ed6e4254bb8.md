
# COMPUTER ENGINEERING FOUNDATIONS, CURRENTS, AND TRAJECTORIES COLLECTION

Lisa MacLean, Editor

## Data Security in Cloud Computing, Volume I

Giulio D'Agostino

MOMENTUM PRESS ENGINEERING

# DATA SECURITY IN CLOUD COMPUTING, VOLUME I

GIULIO D’AGOSTINO

![](img/625475237d5c9b4148fda1077938a911_3_0.png)

### Copyright

Data Security in Cloud Computing, Volume I

Copyright © Momentum Press®, LLC, 2019.

All rights reserved. No part of this publication may be reproduced, stored in a retrieval system, or transmitted in any form or by any means—electronic, mechanical, photocopy, recording, or any other—except for brief quotations, not to exceed 250 words, without the prior permission of the publisher.

First published in 2019 by
Momentum Press®, LLC
222 East 46th Street, New York, NY 10017
www.momentumpress.net

ISBN-13: 978-1-94708-399-8 (print)
ISBN-13: 978-1-94944-900-6 (e-book)

Momentum Press Computer Engineering Foundations, Currents, and Trajectories Collection

Cover and interior design by S4Carlisle Publishing Services Private Ltd., Chennai, India

First edition: 2019

10 9 8 7 6 5 4 3 2 1

Printed in the United States of America

# Dedication

*To my wife Eimear for standing beside me throughout my career and writing this book.*

# ABSTRACT

Cloud computing has already been adopted by many organizations and people because of its advantages of economy, reliability, scalability and guaranteed quality of service amongst others. Readers will learn specifics about software as a service (SaaS), platform as a service (PaaS), infrastructure as a service (IaaS), server and desktop virtualization, and much more.

This book covers not only information protection in cloud computing, architecture and fundamentals, but also the plan design and in-depth implementation details needed to migrate existing applications to the cloud. Readers will have a greater comprehension of cloud engineering and the actions required to rapidly reap its benefits while at the same time lowering IT implementation risk. The book’s content is ideal for users wanting to migrate to the cloud, IT professionals seeking an overview on cloud fundamentals, and computer science students who will build cloud solutions for testing purposes.

# KEYWORDS

Amazon Web Services; API; Azure; BaaS; cloud computing; computer engineering and science; Google Cloud; Java; MySQL; Node.js; SaaS; SQL

# CONTENTS

LIST OF FIGURES xiii

LIST OF TABLES xv

LIST OF ABBREVIATIONS xvii

ACKNOWLEDGMENTS xix

INTRODUCTION xxi

### CHAPTER 1 CLOUD COMPUTING ESSENTIALS 1

- 1.1. Infrastructure-as-a-Service 4
- 1.2. Platform-as-a-Service 4
- 1.3. Software-as-a-Service 5
- 1.4. Deployment Designs 5

### CHAPTER 2 OVERVIEW OF CLOUD COMPUTING 11

- 2.1. Essential Characteristics 12
- 2.2. Cloud Services 13
- 2.3. Platform-as-a-Service and IaaS 15
- 2.4. Additional Cloud Services 16
- 2.5. XaaS (Anything-as-a-Service) 17
- 2.6. Public Cloud 19
- 2.7. Personal Cloud 20
- 2.8. Community Cloud 20
- 2.9. Hybrid 20
- 2.10. Cloud Provider Architectural Components 24
- 2.11. ITU-T Cloud Computing Reference Architecture 25
  - 2.11.1. Cloud Computing “Actors” 25
  - 2.11.2. Layered Architecture 27
- 2.12. Network Requirements for Cloud Computing 29

### CHAPTER 3 CLOUD SECURITY BASELINES 33

- 3.1. Fundamentals 33
- 3.2. Program Layer 34
- 3.3. Other Potential Reasons for Data Leakage from the Cloud 43
- 3.4. Privacy and Security in Multiclouds 45
- 3.5. Cloud Accountability 47

### CHAPTER 4 CLOUD COMPUTING ARCHITECTURE 53

- 4.1. Hardware Customers 55
  - 4.1.1. Thick Clients 55
  - 4.1.2. Thin Clients 55
  - 4.1.3. Smartphones 56
  - 4.1.4. Software Customers 56
  - 4.1.5. Thick or Thin . . . or Smart? 56
  - 4.1.6. Thin or Web-applications Customers 58
  - 4.1.7. Smart Customers 58
  - 4.1.8. Personal Cloud 66
  - 4.1.9. Virtual Private Cloud 67
- 4.2. Cloud-storage Prerequisites 70
- 4.3. Cloud OS Prerequisites 70
- 4.4. Memory Prerequisites 70
- 4.5. CPU Prerequisites 71
- 4.6. Software Prerequisites 71

### CHAPTER 5 CLOUD COMPUTING SECURITY ESSENTIALS 75

- 5.1. Cloud Computing Definition 76
- 5.2. Cloud Computing Security Essentials 81
- 5.3. Dividing Operational Responsibilities 86
- 5.4. User-data Boundary 89
- 5.5. Ecosystem Orchestration Boundary 94
- 5.6. Deployment Boundary 96
- 5.7. Defining Your Root of Trust 98
- 5.8. Managing User Authentication and Authorization 99

### CHAPTER 6 CLOUD SECURITY 103

- 6.1. The State of Cloud Security 103
- 6.2. Understanding the Threats 104
- 6.3. Classification and Countermeasures 106
  - 6.3.1. Recruitment and Host Threats 107
  - 6.3.2. Network Breaks 108
  - 6.3.3. Lock-in 109
- 6.4. Compliance Issues 110
- 6.5. Infrastructure Modifications 110
- 6.6. Data Processing 111
- 6.7. Administrative and Assets 111
- 6.8. DoS 111
- 6.9. Service Provider 112
- 6.10. Information Interception 112
- 6.11. Clients' Negligence and Cloud Security 113
- 6.12. Reduction of Governance 113
- 6.13. Common Risks 114
- 6.14. Encryption Keys 114
- 6.15. Service Engine Presence 114

ABOUT THE AUTHOR 121

Index 123

## LIST OF FIGURES

| Figure | Description | Page |
| :--- | :--- | :--- |
| Figure 1.1 | Database server, web server, internet | 3 |
| Figure 1.2 | IaaS, PaaS, SaaS | 4 |
| Figure 1.3 | A public cloud is available to the public | 6 |
| Figure 1.4 | A personal cloud usually belongs to an organization | 6 |
| Figure 1.5 | Hybrid cloud | 6 |
| Figure 1.6 | Cloud isolation | 7 |
| Figure 1.7 | Hybrid computing environments are device agnostic when linked with cloud safely | 8 |
| Figure 2.1 | Cloud computing networks | 12 |
| Figure 2.2 | Cloud support | 13 |
| Figure 2.3 | Compares the functions executed by the cloud support supplier for the three main cloud support versions | 14 |
| Figure 2.4 | Four primary architectural components of the CP (user, supplier, auditor, agent) | 22 |
| Figure 2.5 | Cloud “actors” connections | 24 |
| Figure 2.6 | Cloud ecosystem | 26 |
| Figure 2.7 | Shows the four-layer cloud computing reference architecture as described in *Cloud Computing— Overview and Vocabulary*. ITU-T Y.3500 | 28 |
| Figure 2.8 | Cloud system version developed by ITU-T | 29 |
| Figure 2.9 | Cloud host network | 30 |
| Figure 3.1 | Reveals cloud safety vulnerabilities | 34 |
| Figure 3.2 | User, client machine, cloud server flow | 36 |
| Figure 3.3 | Code | 37 |
| Figure 3.4 | Amazon user login portal | 40 |
| Figure 4.1 | Cloud computing structure | 54 |
| Figure 4.2 | Cloud computing solution's features | 54 |
| Figure 4.3 | Hardware customers. Thick clients, lean customers, smartphones, hardware customers | 55 |
| Figure 4.4 | Thick or Thin customers, web software customers (or occasionally thin customers), Bright customers | 57 |
| Figure 4.5 | Thick and thin customers | 59 |
| Figure 4.6 | Cloud computing suppliers provide their services based on three basic models | 61 |
| Figure 4.7 | Cloud setup version | 65 |
| Figure 4.8 | Illustrates the installation of the cloud model | 66 |
| Figure 4.9 | Personal cloud is committed to one company | 67 |
| Figure 4.10 | Virtual private cloud | 67 |
| Figure 4.11 | Third-party managed service supplier | 68 |
| Figure 4.12 | Hybrid model is made up of a blend of private and public cloud tools | 69 |
| Figure 4.13 | Cloud browser-based functioning system | 71 |
| Figure 5.1 | Information systems are currently at a triple or 3-factor inflexion point in the IT's development | 76 |
| Figure 5.2 | Cloud architecture, NIST cloud computing security RA strategy | 79 |
| Figure 5.3 | Uses a building block approach to depict a graphical representation of the cloud consumer's visibility and availability of the numerous layers of a cloud atmosphere | 82 |
| Figure 5.4 | Consumer's level of control | 83 |
| Figure 5.5 | User-data boundary | 89 |
| Figure 5.6 | Platform-as-a-service border—supplier's layers | 92 |
| Figure 5.7 | Deployment border with PaaS external layers. Platform-as-a-service boundary—consumer's layers | 92 |
| Figure 5.8 | Ecosystem orchestration boundary, IaaS, PaaS, SaaS, and user-data borders | 95 |
| Figure 5.9 | Depicts the trust boundary as the surface of the bounds. Trust boundary—notation explained | 96 |
| Figure 6.1 | Cloud insiders are primarily privileged users, who might be prompted to undermine the safety of their cloud infrastructure | 106 |
