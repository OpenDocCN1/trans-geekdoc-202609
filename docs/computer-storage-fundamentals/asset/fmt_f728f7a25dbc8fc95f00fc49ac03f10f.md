
![](images/cover.jpg)

![Cover](images/cover.jpg)

# Second Revised and Updated Edition 2025

First Edition 2018

**Copyright © BPB Publications, India**

**eISBN: 978-93-65893-137**

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

## LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY

The information contained in this book is true and correct to the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but the publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

![Copy-Logo](images/BPB_Catalogue_QR.png)

[www.bpbonline.com](https://www.bpbonline.com)

## About the Author

Susanta Dutta is a senior storage R&D architect with more than two decades of industry working experience in Hewlett-Packard Enterprise (HPE) Company. He has been working with all types of storage product development and solution implementations with the latest storage technologies. He is an engineering graduate in electronics and communication from the National Institute of Technology (NIT), Durgapur, India.

## Acknowledgement

The work presented in this book would not have been possible without a close association with my colleagues. Mentors, seniors and juniors, everyone contributed to this work directly or indirectly.

I express my deepest and sincere gratitude to my senior Mr. Srikanth BK, who introduced me to storage many years back and guided me to understand basic storage concepts.

I am also grateful to BPB Publications for their guidance and expertise in bringing this book to fruition. It was a long journey of revising this book, with valuable participation and collaboration of reviewers, technical experts, and editors.

I am also thankful to my organization, Hewlett-Packard Enterprise (HPE), for the opportunities and exposure to work with different types of storage products and solutions.

Finally, I would like to thank my family for their love, support, and blessings.

## Preface

In today’s competitive markets, students and IT professionals are more aggressive to create a differentiating factor over and above regular courses, and they are more curious to learn about industry-specific technologies that can help in technical interviews and as well as performing job more efficiently.

On the other hand, the enormous growth of digital information has significantly increased the demand for the storage job market in recent years. Today, several universities, engineering colleges, and educational institutes are offering undergraduate/postgraduate courses on storage technologies.

There are plenty of storage vendors who make storage products and implement solutions. Most vendors explain and advertise feature sets for their products using their terminologies through internet blogs, videos, etc. At times, it is hard to understand the context and underlying concept and larger objective of a feature and difficult to locate a document or write-up for conceptual understanding.

I wrote this book with the learnings captured from decades of working experience with storage technologies to fill the abovementioned gap and connect it with the need. This book explains the concept of storage features and functionalities without referring to or highlighting any vendor’s product. It focuses on the fundamental and underlying concepts of storage technologies. Every Storage vendor builds their products using these technologies.

Therefore, the following readers would undoubtedly benefit from the content of this book:

*   **Engineering students**
    *   Course/Syllabus that covers storage technologies
    *   Step-up skills for effective campus placement
*   **IT professionals**
    *   The ramp-up of the newly hired workforce
    *   Upgrade the talent of existing employees to perform the job efficiently and effectively.
*   **Storage administrators:**
    *   Administrators who manage and monitor their deployed storage systems and solutions.

## Table of Contents

*   [Chapter 1: Storage Systems and Solutions](#ch01.xhtml) - This chapter discusses the types of storage systems, the technologies to store data, and solutions that are deployed in small, medium, and large organizations. You will also learn about the pros and cons of all the storage systems with respect to their usage in the solutions.
*   [Chapter 2: Storage Infrastructure](#ch02.xhtml) - This chapter explains all the physical components of a storage system and their connectivity within it as well as storage networking and host server’s storage components. In addition to it, the chapter also explains software defined storage concept.
*   [Chapter 3: Storage Disk Array](#ch03.xhtml) - In this chapter, you will learn about the design and implementation of various features and functionalities of a storage system, such as storage controller operation modes, different data caching techniques, and how user data is stored on to the physical disk using different RAID levels. This chapter also discussed the pros and cons of each RAID level.
*   [Chapter 4: Storage Communication Protocols](#ch04.xhtml) - A protocol is a set of rules and guidelines for communicating data between host servers and storage systems. In this chapter, you will learn about various standard storage protocols, such as SCSI, FC, iSCSI and FCoE, NFS, and CIFS/SMB. This includes how data gets transferred between the host server and storage system during read and write operations using each protocol.
*   [Chapter 5: Storage Networking to Share Storage](#ch05.xhtml) - In this chapter, you will learn different network topologies through which host servers and storage systems are connected. You will also learn about network configurations to control various access of the storage system by the host servers, such as zoning and LUN masking. Due to some specific network physical connectivity and access configuration, multiple paths get created between the host server and storage system. In this chapter, you will also learn about how virtual volumes are accessed over multiple paths along with load balance and failover.
*   [Chapter 6: Storage Performance](#ch06.xhtml) - In this chapter, you will learn about storage performance basics that include the definition of key factors to measure storage performance. This chapter explains how to determine whether storage is performing slowly or faster. You will also learn about the important features that are implemented within a storage system to enhance performance.
*   [Chapter 7: Fault Tolerance and Data Protection](#ch07.xhtml) - In this chapter, you will learn about various features that enable host applications to continue accessing the data in the event of failure within the storage solution or storage system. This chapter also explains storage technologies related to data protection, such as snapshot, clone, and replication, that allow data recovery in case of any corruption or accidental loss. Further, this chapter highlights the types of backup solutions that organizations implement to recover data in case of any loss.
