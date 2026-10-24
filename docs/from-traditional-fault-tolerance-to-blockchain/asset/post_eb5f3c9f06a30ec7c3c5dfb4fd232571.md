
## From Traditional Fault Tolerance to Blockchain

- Trust
- Privacy
- Immutability
- Availability
- Integrity
- Interoperability
- Data Provenance
- Atomic Code Execution

## From Traditional Fault Tolerance to Blockchain

## Scrivener Publishing

100 Cummings Center, Suite 541J
Beverly, MA 01915-6106

### Publishers at Scrivener

Martin Scrivener (martin@scrivenerpublishing.com)
Phillip Carmical (pcarmical@scrivenerpublishing.com)

## From Traditional Fault Tolerance to Blockchain

### Wenbing Zhao

Cleveland State University

![](img/7320b1480d74f1d65f74659cab456782_4_0.png)

WILEY

This edition first published 2021 by John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, USA and Scrivener Publishing LLC, 100 Cummings Center, Suite 541J, Beverly, MA 01915, USA © 2021 Scrivener Publishing LLC For more information about Scrivener publications please visit www.scrivenerpublishing.com.

All rights reserved. No part of this publication may be reproduced, stored in a retrieval system, or transmitted, in any form or by any means, electronic, mechanical, photocopying, recording, or otherwise, except as permitted by law. Advice on how to obtain permission to reuse material from this title is available at http://www.wiley.com/go/permissions.

## Wiley Global Headquarters

111 River Street, Hoboken, NJ 07030, USA

For details of our global editorial offices, customer services, and more information about Wiley products visit us at www.wiley.com.

## Limit of Liability/Disclaimer of Warranty

While the publisher and authors have used their best efforts in preparing this work, they make no representations or warranties with respect to the accuracy or completeness of the contents of this work and specifically disclaim all warranties, including without limitation any implied warranties of merchantability or fitness for a particular purpose. No warranty may be created or extended by sales representatives, written sales materials, or promotional statements for this work. The fact that an organization, website, or product is referred to in this work as a citation and/or potential source of further information does not mean that the publisher and authors endorse the information or services the organization, website, or product may provide or recommend it make. This work is sold with the understanding that the publisher is not engaged in rendering professional services. The advice and strategies contained herein may not be suitable for your situation. You should consult with a specialist where appropriate. Neither the publisher nor authors shall be liable for any loss of profit or any other commercial damages, including but not limited to special, incidental, consequential, or other damages. Further, readers should be aware that websites listed in this work may have changed or disappeared between when this work was written and when it is read.

## Library of Congress Cataloging-in-Publication Data

ISBN 978-1-119-68195-3

Cover image: Pixabay.Com Cover design by Russell Richardson

Set in size of 11pt and Minion Pro by Manila Typesetting Company, Makati, Philippines

Printed in the USA

## To My Parents

## Contents

- List of Figures xiii
- List of Tables xix
- Acknowledgments xxi
- Preface xxiii
- References xxix
- 1 Introduction 1
- 1.1 Basic Concepts and Terminologies for Dependable Computing 2
- 1.1.1 System Models 2
- 1.1.2 Threat Models 3
- 1.1.3 Dependability Attributes and Evaluation Metrics 6
- 1.2 Means to Achieve Dependability 9
- 1.2.1 Fault Avoidance 9
- 1.2.2 Fault Detection and Diagnosis 9
- 1.2.3 Fault Removal 10
- 1.2.4 Fault Tolerance 11
- 1.3 System Security 13
- References 18
- 2 Logging and Checkpointing 21
- 2.1 System Model 22
- 2.1.1 Fault Model 23
- 2.1.2 Process State and Global State 23
- 2.1.3 Piecewise Deterministic Assumption 26
- 2.1.4 Output Commit 26
- 2.1.5 Stable Storage 27
- 2.2 Checkpoint-Based Protocols 27
- 2.2.1 Uncoordinated Checkpointing 27
- 2.2.2 Tamir and Sequin Global Checkpointing Protocol 29
- 2.2.3 Chandy and Lamport Distributed Snapshot Protocol 35
- 2.2.4 Discussion 38
- 2.3 Log Based Protocols 40
- 2.3.1 Pessimistic Logging 42
- 2.3.2 Sender-Based Message Logging 51
- References 60
- 3 Recovery-Oriented Computing 63
- 3.1 System Model 65
- 3.2 Fault Detection and Localization 68
- 3.2.1 Component Interactions Modeling and Anomaly Detection 72
- 3.2.2 Path Shapes Modeling and Root Cause Analysis 76
- 3.2.3 Inference-Based Fault Diagnosis 80
- 3.3 Microreboot 89
- 3.3.1 Microrebootable System Design Guideline 90
- 3.3.2 Automatic Recovery with Microreboot 91
- 3.3.3 Implications of the Microrebooting Technique 92
- 3.4 Overcoming Operator Errors 93
- 3.4.1 The Operator Undo Model 94
- 3.4.2 The Operator Undo Framework 95
- References 99
- 4 Data and Service Replication 103
- 4.1 Service Replication 105
- 4.1.1 Replication Styles 107
- 4.1.2 Implementation of Service Replication 109
- 4.2 Data Replication 111
- 4.3 Optimistic Replication 116
- 4.3.1 System Models 117
- 4.3.2 Establishing Ordering among Operations 119
- 4.3.3 State Transfer Systems 122
- 4.3.4 Operation Transfer System 126
- 4.3.5 Update Commitment 131
- 4.4 CAP Theorem 136
- 4.4.1 2 out of 3 139
- 4.4.2 Implications of Enabling Partition Tolerance 140
- References 143
- 5 Group Communication Systems 147
- 5.1 System Model 149
- 5.2 Sequencer Based Group Communication System 152
- 5.2.1 Normal Operation 153
- 5.2.2 Membership Change 157
- 5.2.3 Proof of Correctness 165
- 5.3 Sender Based Group Communication System 166
- 5.3.1 Total Ordering Protocol 167
- 5.3.2 Membership Change Protocol 174
- 5.3.3 Recovery Protocol 183
- 5.3.4 The Flow Control Mechanism 190
- 5.4 Vector Clock Based Group Communication System 192
- References 197
- 6 Consensus and the Paxos Algorithms 199
- 6.1 The Consensus Problem 200
- 6.2 The Paxos Algorithm 202
- 6.2.1 Algorithm for Choosing a Value 202
- 6.2.2 Algorithm for Learning a Value 204
- 6.2.3 Proof of Correctness 204
- 6.2.4 Reasoning of the Paxos Algorithm 206
- 6.3 Multi-Paxos 212
- 6.3.1 Checkpointing and Garbage Collection 213
- 6.3.2 Leader Election and View Change 214
- 6.4 Dynamic Paxos 216
- 6.4.1 Dynamic Paxos 217
- 6.4.2 Cheap Paxos 220
- 6.5 Fast Paxos 227
- 6.5.1 The Basic Steps 228
- 6.5.2 Collision Recovery, Quorum Requirement, and Value Selection Rule 229
- 6.6 Implementations of the Paxos Family Algorithms 235
- 6.6.1 Hard Drive Failures 236
- 6.6.2 Multiple Coordinators 236
- 6.6.3 Membership Changes 237
- 6.6.4 Limited Disk Space for Logging 241
- References 242
- 7 Byzantine Fault Tolerance 245
- 7.1 The Byzantine Generals Problem 246
- 7.1.1 System Model 247
- 7.1.2 The Oral Message Algorithms 250
- 7.1.3 Proof of Correctness for the Oral Message Algorithms 260
- 7.2 Practical Byzantine Fault Tolerance 261
- 7.2.1 System Model 262
- 7.2.2 Overview of the PBFT Algorithm 263
- 7.2.3 Normal Operation of PBFT 265
- 7.2.4 Garbage Collection 267
- 7.2.5 View Change 268
- 7.2.6 Proof of Correctness 271
- 7.2.7 Optimizations 273
- 7.3 Fast Byzantine Agreement 277
- 7.4 Speculative Byzantine Fault Tolerance 278
- 7.4.1 The Agreement Protocol 279
- 7.4.2 The View Change Protocol 283
- 7.4.3 The Checkpointing Protocol 288
- 7.4.4 Proof of Correctness 288
- References 290
- 8 Cryptocurrency and Blockchain 295
- 8.1 History of Cryptocurrency 295
- 8.2 Bitcoin 298
- 8.2.1 Decentralized Network and Architecture 301
- 8.2.2 Self-Contained Cryptography 302
- 8.2.3 Decentralized Data Structure 304
- 8.2.4 Decentralized Algorithms 313
- 8.3 Ethereum 317
- 8.3.1 Ethereum Computing Model 318
- 8.3.2 Block and Consensus 326
- 8.3.3 Tokenization 340
- 8.4 Attacks on Blockchain 342
- References 347
- 9 Consensus Algorithms for Blockchain 349
- 9.1 Model on Blockchain Consensus 353
- 9.1.1 Requirements on Puzzle Design 354
- 9.1.2 Zero-Knowledge Proof 355
- 9.2 Proof of Work 356
- 9.3 Proof of Resources 357
- 9.3.1 Using Storage as Resource 357
- 9.3.2 Using Computing as Resource 359
- 9.4 Virtual Mining 360
- 9.4.1 PeerCoin PoS 360
- 9.4.2 Fixed-Epoch Time Based PoS Schemes 368
