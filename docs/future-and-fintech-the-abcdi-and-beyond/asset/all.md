![figure](images/cover.jpg)

*“This is an excellent book, covering the most important technology areas of Fintech: AI, Blockchain, Cloud, IoT, etc. The authors have succeeded in producing self-contained chapters with rich contents, which are accessible to anyone with a good background in engineering.”*

*Yong Xia*  
*Managing Director, Global Head of HSBC Lab*

*“To stay relevant in this digital era, it is critical for financial service providers to transform digitally using emerging technologies. The Future is Fintech is a must-read guidebook that explains the key concepts, practical applications, and comprehensive case studies to enable any leader to play an effective role in leveraging ABCDI technologies and beyond.”*

*Zhu Kuang Lee*  
*Managing Director, Chief Digital, Data & Innovation Officer,*  
*Securities Services, HSBC*

THE FUTURE AND

FINTECH

ABCDI and Beyond

THE FUTURE AND

FINTECH

ABCDI and Beyond

Editor

**Jun Xu**

![](images/logo.jpg)

*Published by*

World Scientific Publishing Co. Pte. Ltd.

5 Toh Tuck Link, Singapore 596224

*USA office:* 27 Warren Street, Suite 401-402, Hackensack, NJ 07601

*UK office:* 57 Shelton Street, Covent Garden, London WC2H 9HE

 

 

**Library of Congress Cataloging-in-Publication Data**

Names: Xu, Jun (Research and Development Engineer), editor.

Title: The future and FinTech : ABCDI and beyond / editor Jun Xu.

Description: Singapore ; Hackensack, NJ : World Scientific Publishing Co. Pte. Ltd., \[2022\] | Includes bibliographical references.

Identifiers: LCCN 2022008148 | ISBN 9789811250897 (hardcover) | ISBN 9789811250903 (ebook for institutions) | ISBN 9789811250910 (ebook for individuals)

Subjects: LCSH: Financial services industry--Technological innovations. | Finance--Data processing. | Banks and banking--Technological innovations.

Classification: LCC HG173 .F88 2022 | DDC 332.028541--dc23/eng/20220318

LC record available at [https://lccn.loc.gov/2022008148](https://lccn.loc.gov/2022008148)

 

 

**British Library Cataloguing-in-Publication Data**

A catalogue record for this book is available from the British Library.

 

 

 

Copyright © 2022 by World Scientific Publishing Co. Pte. Ltd.

*All rights reserved. This book, or parts thereof, may not be reproduced in any form or by any means, electronic or mechanical, including photocopying, recording or any information storage and retrieval system now known or to be invented, without written permission from the publisher.*

 

 

For photocopying of material in this volume, please pay a copying fee through the Copyright Clearance Center, Inc., 222 Rosewood Drive, Danvers, MA 01923, USA. In this case permission to photocopy is not required from the publisher.

 

 

For any available supplementary material, please visit  
[https://www.worldscientific.com/worldscibooks/10.1142/12686#t=suppl](https://www.worldscientific.com/worldscibooks/10.1142/12686#t=suppl)

 

Desk Editors: Balamurugan Rajendran/Amanda Yun

 

Typeset by Stallion Press

Email: [enquiries@stallionpress.com](mailto:enquiries@stallionpress.com)

 

Printed in Singapore

## **Preface**

*The Future and FinTech* examines the fundamental financial technologies and its growing impact on the Banking, Financial Services, and Insurance (BFSI) sectors. With global investments amounting to more than $100 billion in 2020, the proliferation of FinTech has underpinned the direction that payments, loans, wealth management, insurance, and digital assets are heading.

This book presents FinTech from an industrial perspective in the context of architecture and its basic building blocks, e.g., Artificial Intelligence (AI), Blockchain, Cloud, Big Data, Internet of Things (IoT) — thereafter, we abbreviate the five technologies as ABCDI — and its connections to real-life applications at work. It provides a detailed guidance on how FinTech digitalizes business operations, improves productivity and efficiency, and optimizes resource management with the help of some new concepts, such as AIOps, MLOps, and DevSecOps. Readers will also discover how FinTech innovations connect BFSI to the rest of the world with the growing interests in Open Banking, Banking-as-a-Service (BaaS) and FinTech-as-a-Service (FaaS).

To help readers understand how FinTech has unlocked numerous opportunities for tapping into the massive substantial group of customers, this book illustrates the massive changes already underway and provides insights into changes yet to come, through practical examples and applications with illustrative figures and summary tables, making this book a handy quick reference for all things FinTech.

This book is organized as follows. [Chapter 1](#chap1.xhtml), “FinTech Innovation and Strategy”, presents an overview of the FinTech industry with its innovation applications and development strategies. Challenges, risks, and opportunities are intensively discussed along with some potential solutions. [Chapter 2](#chap2.xhtml), “The Technical Foundations of FinTech: ABCDI and More”, further explains the fundamental technologies behind FinTech with their functionalities and interactions between each other, with the aim of enabling non-technical readers to understand FinTech conceptually.

[Chapter 3](#chap3.xhtml), “AI Theory and Applications in the Financial Industry”, discusses AI theory and its applications in the financial industry. It starts with the general AI taxonomy and methodology, and then summarizes the typical applications in the different business domains. Hot topics such as responsible AI and sustainable AI are addressed together with their development trends. [Chapter 4](#chap4.xhtml), “AI Fairness in the Financial Industry: A Machine Learning Pipeline Approach”, focuses on a specific AI topic on ethics — how fairness and biasness are entangled in the whole Machine Learning (ML) life-cycle. Key points in the pipelines are highlighted with substantive workflow charts and checklists. [Chapter 5](#chap5.xhtml), “Knowledge Graphs and its Applications in Finance”, illustrates the importance of knowledge graphs for financial services. A practical approach to build and maintain a business knowledge graph is presented and illustrated with a simplified sample use case.

[Chapter 6](#chap6.xhtml), “Migration from the Traditional Financial Markets to a World of Digital Assets”, and [Chapter 7](#chap7.xhtml), “Central Bank Digital Currencies: Opportunities and Challenges in the Post-pandemic Era” go on to discuss digital assets with Blockchain and DLT technologies. In particular, [Chapter 6](#chap6.xhtml) considers the changes and challenges during the migration from traditional financial markets to a world of digital assets, while [Chapter 7](#chap7.xhtml) presents a deep study on the central bank digital currency (CBDC) with its opportunities, framework, challenges, and technologies. The state-of-the-art development including the availability of technology, balance sheet implications, and legal framework. Some use cases are also studied, e.g., Project Ubin in Singapore.

[Chapters 8](#chap8.xhtml) and [9](#chap9.xhtml) focus on data management. Data is the most valuable asset in BFSI. [Chapter 8](#chap8.xhtml), “Artificial Intelligence and Machine Learning in Data Management”, presents the methodologies, solutions, and platforms of AI and ML for data management in the Big Data era. A case study of extensive AI/ML integration in enterprise data management is also presented, together with the associated challenges and future directions. [Chapter 9](#chap9.xhtml), “Technologies and Strategies to Leverage Cloud Infrastructure for Data Integration”, provides an overview of Cloud data technologies for data integration and their strategic implications. In addition to common Cloud services for data ingestion, storage, processing and lifecycle management, major Cloud platforms, leading data tech companies, and open-source communities also provide various tools for delivering data security and sensitive data management. A case study on how a leading financial services company leverages Cloud data infrastructure to digitalize banking is also presented.

[Chapter 10](#chap10.xhtml), “Smart Home for Financial Services: Security, Privacy, and Solutions” and [Chapter 11](#chap11.xhtml), “Biometrics in FinTech: A Technological Review”, discuss two important topics in IoT — the smart home and biometrics. The smart home is one of the most prevalent applications of Internet of Things (IoT). Biometrics information sensed by IoT devices, e.g., voice, face, fingerprint and behaviors, can be used to verify personal identity. Besides home appliance control, smart home could become the future personal financial center of comprehensive financial services with enhanced security and safety using AI, Blockchain, Cloud and biometrics technologies. [Chapter 11](#chap11.xhtml) further explains the techniques, applications, challenges, and future directions of biometrics.

[Chapters 12](#chap12.xhtml) to [14](#chap14.xhtml) emphasize on one of the most important techniques for digital transformation — DevOps, the integration of development and operation in the productionization lifecycle. [Chapter 12](#chap12.xhtml), “DevOps: Speeding up Financial Applications Delivery to the Market”, gives an overview of DevOps. Agile and CI/CD concepts and their tools, (e.g., microservice and Docker) are also explained. A few of DevOps success stories in financial industry are also highlighted. [Chapter 13](#chap13.xhtml), “DevSecOps: Integrating Security in DevOps for Financial Applications”, further adds security concerns into DevOps, and analyzes the status of DevSecOps together with its challenges, practices, and tools. [Chapter 14](#chap14.xhtml), “MLOps in the Financial Industry: Philosophy, Practices, and Tools”, applies DevOps into the AI/ML lifecycle for MLOps, which can dramatically reduce the ML adoption cost and improve AI responsibility in the BFSI. Case studies are provided on how to implement DevOps, DevSecvOps, and MLops in large banks.

[Chapter 15](#chap15.xhtml), “The Open Banking Ecosystem and its Evolution”, demonstrates the power of open banking with BaaS and FaaS for the platformization ecosystem. Their implementation strategies and concerns in different countries are discussed. In particular, we highlight their developments in China, and believe that future banking will be more open and smarter with the integration of FinTech.

During the preparation of this book, the editor received support from numerous colleagues and alumni of HSBC. Here I only mention a few — Dr. Yong Xia, Alex Tsui, Dr. Xinming Jin, Dr. Amy Shi-Nash, Eros Ye, Dr. Kwok Ching Tsui, Cherrie Xu, Wenne Chen, Sam Fan, Jiang Zhao, Adam Chen, Edward Liu, Andrew Liu, Jay Gu, Robin Wu, Shair Zheng, Chloe Qian, Sandeep Sharma, Dave Vijay, Astor Law, Joe Li, Daniel Lewis, Chioma Anyanwu-Akpom, Jennifer Doherty, Wei He, Marco Yao, Alex Han, *et al.* Some friends have also helped to review some chapters — Dr. Martin Qiao, Mark Liu, Victor Lu, Kenneth Liu, Running He. My current colleagues also offer considerable helps, and there are too many to list here. In particular, my wife, Grace Wu, read through the whole book and provided many useful suggestions. As a senior executive in a global leading high-tech firm, her understanding on FinTech has grown exponentially after being the first reader of this book, which marks this book as an ideal guide for both technical leaders and management on the non-tech track. Deep appreciation also goes out to the publishers, Dr. Yan Hong Ng, Amanda Yun, and Karimah Samsudin for their professional support.

Jun Xu  
March 2022

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_fmatter](https://doi.org/10.1142/9789811250903_fmatter)

**About the Editor and Contributors**

![](images/pxi.jpg)

**Dr. Jun Xu** is a director of Machine Learning (ML) engineering in a top financial institution and a guest professor at South China University of Technology (SCUT). He was previously a data scientist senior vice president in HSBC, a principal engineer in Western Digital, and a research scientist in Temasek Labs. He has also held some editorial positions with international journals and conferences, such as *Unmanned Systems,* ICCA, and ICARV. He is a senior member of the Institute of Electrical and Electronics Engineers (IEEE).

His working experiences across multiple disciplines include Artificial Intelligence (AI), Machine Learning (ML), FinTech, Data Storage, Robotics, Internet of Things (IoT), Big Data, Cloud, Digitalization Transformation, System Architecture, Optimization and Modelling. He has published 3 books, 16 patents (and applications), and around 60 peer-reviewed papers. He received his Bachelor of Science (BS) from Southeast University, China, and his PhD from Nanyang Technological University (NTU), Singapore.

He is the editor of this book and the author of [Chapters 1](#chap1.xhtml)–[4](#chap4.xhtml), [10](#chap10.xhtml), [11](#chap11.xhtml), [14](#chap14.xhtml), and [15](#chap15.xhtml).

![](images/pxii.jpg)

**Dr. Zhiyu Ge** is a veteran quantitative risk and valuation analyst and senior vice president at HSBC. He is an enthusiast in financial technology innovation in the area of Big Data and Machine Learning, helping the bank to become more digitalized and data driven. Prior to HSBC, he was a vice president in the Quantitative Risk and Analysis team of Blackrock, and a fixed income quantitative analyst at Merrill Lynch Investment Managers. He received his PhD degree in statistics with honors from the University of California at Berkeley.

He is the author of [Chapters 5](#chap5.xhtml), [8](#chap8.xhtml), and [9](#chap9.xhtml). He also contributes some contents in [Section 3.2](#chap3.xhtml#h3-2).

![](images/pxii-1.jpg)

**Dr. Steven Hu** is an executive director of Digital Assets in a leading banking group. In this role, he focuses on setting up the digital assets’ capabilities in the bank, driving initiatives across digital currencies, asset tokenization, as well as incubating new business models.

Previously, Steven led the Distributed Ledger Technology (DLT) Program within the Global Liquidity and Cash Management business in HSBC. He focused on the development of DLT strategy and road-map, leveraging the distributed ledger to drive innovations in the payments landscape. Steven led a team of experts and created the HSBC’s On-Chain Payment solution which streamlines payments processes for multiple participants, by linking blockchain-based ecosystems to be able to transact in multiple currencies near instantaneously, 24/7. Industry awards for solutions by his team, such as The Assets Triple A Best Digital Collaboration Award, are testament to his work. Prior to joining HSBC, he was working with international banks, such as BNP Paribas, as well as technology companies driving the digital transformation agenda.

Steven is an Advisory Council Member in Global Digital Finance, the Co-Chairman of Digital Currency Sub-Committee in Blockchain Association Singapore. He serves as a grant reviewer in several national FinTech funding schemes. He has been in the advisory/working committees of several central banks, working on the designs of wholesale and retail central bank digital currencies (CBDCs). Steven received his Ph.D. degree from the National University of Singapore. He holds several FinTech and technology patents and has published a number of journal/conference papers. His recent patent titled “Integration of Blockchain with Off-chain Processing” has proposed a novel “always on” and programmable banking payment technology, in parallel to CBDCs and stablecoins. He speaks regularly on the Future of Money in international conferences, such as the Singapore FinTech Festival.

He is the author of [Chapter 7](#chap7.xhtml).

![](images/pxiii.jpg)

**Dr. Jihai Zhou** graduated from Imperial College London with a PhD degree. He worked in different banks (Barclays Bank, HSBC, UBS, etc.) and Tencent, with more than 10 years’ working experience on leading DevOps/DevSecOps transformation. From 2018 to 2021, he has attended more than 30 technical conferences as the speaker (such as Open Source Summit, DevOpsDays, etc.) held in different countries to share his experience on DevOps/DevSecOps. In 2021, his first book, *DevSecOps Guide and Practice,* was published in China.

He is the author of [Chapters 12](#chap12.xhtml) and [13](#chap13.xhtml).

![](images/pxiii-1.jpg)

**Dr. Frank Tong** is a managing partner at QBN Capital. Frank graduated from Columbia University with a PhD degree and worked at IBM Research, before he took up a tenured faculty position at the Chinese University of Hong Kong (CUHK). He joined TDK Corporation later on and headed the optical business unit. Since then, Frank has served as a senior executive in many institutions, including HSBC, ASTRI, and Hisense. He is currently an adjunct professor at CUHK, and a member of the Research Council of Our Hong Kong Foundation.

He is the author of [Chapter 6](#chap6.xhtml).

![](images/pxiv.jpg)

**Ms. Yuling Zhang** is with Deloitte Cloud Consulting. She received her Master of Science degree in Financial Technology with the Excellent Scholarship from the Hong Kong University of Science and Technology (HKUST). In 2018, She joined IT Innovation at HSBC, through the FinTech Career Accelerator Scheme launched by the Hong Kong Monetary Authority. She has working experience in the FinTech sector in Hong Kong, Singapore, and mainland China.

She is the author of [Chapter 15](#chap15.xhtml).

![](images/pxiv-1.jpg)

**Ms. Philea Chim** is a former tech policy advisor in the United Kingdom (UK) Government. She is very familiar with the tech ecosystem and investment landscape in the UK and Europe, as well as policies relating to Open Banking, Data Protection, and Digital Economy. She currently leads the FinTech and Deep Tech venture investments at QBN Capital, with an emphasis on Blockchain, AI, and cyber and data security, both in the UK and in Hong Kong. Philea is well connected in the tech sector with universities, venture capitals, and public sector bodies, and is uniquely positioned to bridge the East and West.

She is the author of [Chapter 6](#chap6.xhtml).

## **Contents**

[*Preface*](#preface.xhtml)

[*About the Editor and Contributors*](#editor.xhtml)

[Chapter 1FinTech Innovation and Strategy](#chap1.xhtml)

*Jun Xu*

[Chapter 2The Technical Foundations of FinTech: ABCDI and More](#chap2.xhtml)

*Jun Xu*

[Chapter 3AI Theory and Applications in the Financial Industry](#chap3.xhtml)

*Jun Xu*

[Chapter 4AI Fairness in the Financial Industry: A Machine Learning Pipeline Approach](#chap4.xhtml)

*Jun Xu*

[Chapter 5Knowledge Graphs and its Applications in Finance](#chap5.xhtml)

*Zhiyu Ge*

[Chapter 6Migration from the Traditional Financial Markets to a World of Digital Assets](#chap6.xhtml)

*Philea Chim and Frank Tong*

[Chapter 7Central Bank Digital Currencies: Opportunities and Challenges in the Post-pandemic Era](#chap7.xhtml)

*Steven Hu*

[Chapter 8Artificial Intelligence and Machine Learning in Data Management](#chap8.xhtml)

*Zhiyu Ge*

[Chapter 9Technologies and Strategies to Leverage Cloud Infrastructure for Data Integration](#chap9.xhtml)

*Zhiyu Ge*

[Chapter 10Smart Home for Financial Services: Security, Privacy, and Solutions](#chap10.xhtml)

*Jun Xu*

[Chapter 11Biometrics in FinTech: A Technological Review](#chap11.xhtml)

*Jun Xu*

[Chapter 12DevOps: Speeding up Financial Applications Delivery to the Market](#chap12.xhtml)

*Jihai Zhou*

[Chapter 13DevSecOps: Integrating Security in DevOps for Financial Applications](#chap13.xhtml)

*Jihai Zhou*

[Chapter 14MLOps in the Financial Industry: Philosophy, Practices, and Tools](#chap14.xhtml)

*Jun Xu*

[Chapter 15The Open Banking Ecosystem and its Evolution](#chap15.xhtml)

*Yuling Zhang and Jun Xu*

[*Conclusion*](#conclusion.xhtml)

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0001](https://doi.org/10.1142/9789811250903_0001)

## Chapter 1

## FinTech Innovation and Strategy

***Jun Xu***

**1.1Background**

The COVID-19 pandemic has brought a lot of changes and challenges to financial institutions (FIs) around the world. As many countries have begun easing the lockdown restrictions since the early 2021, FIs have successfully navigated the immediate pressures of the COVID-19 crisis, and recognized the importance of digital transformation in this new normal situation. This scenario is likely to continue in the post-pandemic world so as digital transformation will be a critical condition for the survival of many organizations before we can completely eliminate the threats of serious epidemic diseases.

Digitalization is not a new concept to most FIs — mobile banking and online banking were offered to customers several years ago, and the availability of digital operation platforms enable bank staff to monitor, operate, and manage some internal resources remotely. The COVID-19 pandemic has accelerated the digitalization of FIs as customer expectations have changed during the pandemic, and those changes present new challenges for most FIs, but it will also help them cope with the tougher operating environment the pandemic has brought. New risks are emerging, and banking models and regulations are being tested.

Financial technology (abbreviated as FinTech) is one of the major forces to help FIs to overcome one challenge after another. Although the modern FinTech is usually recognized since 2008, the history of FinTech can even be traced back to over 150 years ago. FinTech was originally defined as technology and innovation that aim to compete with traditional financial methods and models to deliver new financial products and services. In a more general sense, it can be “any innovative ideas that improve financial service processes by proposing technology solutions according to different business situations, while the ideas could also lead to new business models or even new business opportunities”. Therefore, FinTech can be any new applications, processes, products, or business models with an end-to-end process in the financial services industry.

The advancement of FinTech is driven by both new technology developments and new business requirements. For example, financial demands from people without credit cards in China and the unbanked people in Kenya, together with the wide usage of smart phones and internet growth, expedited the delivery of Alipay and WeChatPay in China, and M-PESA in Kenya, respectively. These new demands can be also evolving.

**1.2FinTech Taxonomy and Scope**

FinTechs have seized the initiative and come up with technologies to transform financial services, particularly in the areas of customer experience, process automation, and decision making. Today, we have seen many disruptive forces such as cost commoditization of FIs’ generic services, profile redistribution in the value chain with new forms of partnerships between FinTech firms and FIs, experience ownership of customer interfaces and dominant platforms, data monetization in real time, intelligent robot to augment humans, etc. \[[1](#chap1.xhtml#rref1)\]. The so-called upcoming Bank 4.0 era means that your bank will either integrate into the world through technology or will no longer exist \[[2](#chap1.xhtml#rref2)\].

Four main types of FinTech firms are driving the evolution \[[1](#chap1.xhtml#rref1)\]:

*   The first type is FinTech start-ups, which are generally small- to medium-size but own new technologies and/or new business models in a specific domain. Some of the leading firms in this category include Stripe, Revolut, Chime, Klarna, and coinbase.
*   The second type includes some traditional information technology (IT) infrastructure and service providers such as IBM and CISCO. These firms have developed strong capabilities in digitalization and modernization, and they can help FIs to navigate the technological transformation journey.
*   Internet and Cloud giants, such as Google, Microsoft, AWS, Alibaba, and Tencent belong to the third type. They have built their ecosystem with a large-scale of clients, and some of them may have their own financial infrastructure and services, e.g., Apple Pay, Alipay, and WeChat Pay. Many profound disruptions are originated from these technology giants. By leveraging the social platforms in their ecosystem, these tech giants have successfully transformed their business model from a single line to multiple lines to our daily life.
*   The fourth type is the traditional FIs, which are actively involved in the adoptions, development, and incubation of FinTech. In fact, many FIs start their strategical planning in this area throughout the whole value chain including business logic, business model, operation model, risk control, etc. In China, most large banks, such as China Merchants Bank and PingAn Bank, have their own FinTech subsidiaries.

While some FinTech startups have made big impact to the market, e.g., Stripe, Klarna, Plaid, and Robinhood, many others are still struggling in competing with the incumbents, and exploring alternative financial infrastructure. Some may choose to partner with FIs as an alternative.

In contrast, successful incumbent FIs have the liberty to collaborate with FinTech firms to build an ecosystem of innovation and new capabilities, in the form of partnerships and/or acquisitions. In most cases, FinTech firms are complementary to FIs, while the latter are the largest customers to the former. The accelerated changes are driving a shift from cost and product leadership to business agility — the speed with which companies can build new capabilities and partnerships determines their success.

Although the newcomers may face more challenges even when the FinTech market has grown to about US$100 billion business recently, the development of the FinTech ecosystem and the opening up of financial infrastructure has also lowered the barrier to entry. We believe that more FinTech startups will emerge in the market, even though direct investment from venture capitals (VCs) has dropped slightly during the pandemic. Top 100 VC-backed FinTech unicorns together are valued at over US$500 billion, and a growing number of FinTech unicorns are seeking IPO opportunities in the global capital market. Note that FinTech firms are subject to the challenges posed by technology, economics, and regulatory environment. For example, during the exploration phase, over lenient regulatory environment often leads to a fast but barbaric development. In China, it led to the success of many FinTech companies, such as Ant Technology (Alipay) and JD Digital. However, the recent regulatory changes in China put FinTech under similar regulations as banks. Even the companies in the category of “too-big-to-fail”, e.g., Ant technology, WeBank, and JD Digital, may face some new challenges.

![](images/p4.jpg)

**Figure 1.1.**Major technologies supporting FinTech — ABCDI and others

**1.2.1*Foundation Technologies to Drive FinTech***

Over the past 20+ years, some major technologies, such as Artificial intelligence (AI), Blockchain (and distributed ledger technology, or DLT), Cloud, Big Data, Internet of Things (IoT), and others as shown in [Figure 1.1](#chap1.xhtml#fig1-1), have expedited the overall development of FinTech, driven the business model reconstruction, and impacted the competitive landscape of the financial industry.^([1](#chap1.xhtml#rfn1)) Today’s technological advances are expected to reshape tomorrow’s financial landscape and longer-term future.

[Chapter 2](#chap2.xhtml) will provide more details on those technologies and their general applicable domains in FIs to build self-contained content for this book.

**1.2.2*General Domains***

FIs provide a wide range of services (see [Section 1.7, Appendix 1.1](#chap1.xhtml#h1-7) for an illustration of banking infrastructure). As digitalization becomes the mainstream practice in the financial services industry, today’s FinTech innovations mainly focus on digital services as well.

1.2.2.1*Digital payments*

The payment landscape has changed dramatically in the past 20 years, from online payment (e.g., PayPal, Stripe), mobile payment (e.g., Apple Pay, AliPay, WeChat Pay), to cryptocurrency-based payment (e.g., coinbase). Cardless payment now becomes the dominant mode in many countries.

In most Tier 3 or above cities of China, mobile payment becomes the main stream due to the dramatic growth of e-commerce, which generates huge demands for user-friendly online and secured payment services. Around 83% of all payments in China were made via mobile payment in 2018, and the total number of users increased to 852.52 million in 2020. They enjoy the conveniences from Tenpay (Wechat Pay or QQ Wallet), Alipay, China Union Pay, and other payment apps. \[They all belong to cardless payment mode.\]

The global payment networks not only open up new opportunities for merchants with a global scale, but also help consumers to enjoy financial services smoothly via digital mobile devices. The market size of the global digital payments is expected to grow from US$5.4 trillion in 2020 to US$6.6 trillion in 2021, according to a report from Finaria.^([2](#chap1.xhtml#rfn2))

As described in other chapters in this book, digital payment will be expected to be more intelligent via AI technology (see [Chapter 3](#chap3.xhtml)), more secured via enhanced biometrics techniques (see [Chapter 11](#chap11.xhtml)), more convenient and customer-friendly with IoT techniques loaded on smart edge devices in various scenarios (see [Chapter 10](#chap10.xhtml)).

1.2.2.2*Digital lending*

Digital lending is defined as the use of technology to originate and renew loans, in order to deliver faster services and decisions, better customer experience, and more cost-effective products. The digitalization process starts with information collection (e.g., online application form, credit file, etc.), information processing (e.g., ID document Optical Character Recognition (OCR), entity identification for Know Your Customer (KYC), etc.), and covers decision making (data insight based on both rules and AI models) and loan collection (e.g., loan status monitoring, auto nonfiction, auto calling, etc.).

The digital lending platforms can be built by banks, non-banking finance company (NBFC) and FinTech companies. There are multiple models, such as point-of-sale (POS) transaction-based lending, marketplaces, and peer-to-peer (P2P) lending. An increased level of personalization is offered in the services to meet the needs of next generation clients. In other words, specialized digital lenders are trying to understand the clients’ particular needs to customize their loan requirements at scale.

Due to the lack of significant regulations imposed in the early 2010s, China’s online lending industry had growth rapidly in the past decade, which led to a large number of players in the market. On the other hand, it poses potential systematic financial risk to the overall China market. A growing number of regulatory requirements have been released in the past few years by the financial regulatory authorities in China. For example, P2P platforms of China peaked to around 5,000 at 2017, and then went to almost zero at the end of 2020 with the increasingly tightened regulations. In fact, without sufficient risk control on lending, those platforms under savage growth will find it hard to survive once the cake of the whole industry shrinks sharply. Only a few of them have been transformed to FinTech service platforms, which provide risk reserves through cooperation with banks and other FIs. Obviously, regulators do not want to “kill” innovations, but to cultivate a healthier environment for the entire ecosystem. For example, Microloan platforms, such as Huabei and JieBei, used to be major financial platforms for young adults. Now they are required to increase capital reserve, discontinue the improper linkage between microloans and other financial products, and decrease the credit limit, etc.

Despite the regulatory changes mentioned above, the size of the global digital lending market is still growing rapidly. According to Mordor intelligence, it is expected to hit US$587.27 billion by 2026, up from US$311.06 billion in 2020, with a compound annual growth rate (CAGR) of approximately 11.9% during the forecast period (2021–2026).^([3](#chap1.xhtml#rfn3))

1.2.2.3*Digital capital raising*

Digital capital raising is closely related to digital lending (e.g., P2P lending). In fact, they are often integrated in the same platform. Crowdfunding is one of the basic forms of digital capital raising, in which a project or venture is funded by raising small amounts of money from a large group of people. It can be broadly classified into investment-based and non-investment-based crowdfunding. The former usually relate to equity, revenue, profit sharing, real estate, and commodity, while the latter is often associated with donation and/or rewards.

A popular approach for crowdfunding is via digital tokens backed by Blockchain or DLT. For example, the well-known initial coin offer (ICO) in the first half of 2010s is a way that investors exchange their government currencies and/or cryptocurrencies with digital tokens for participation. Tokens represent the interests or performance rights of the holder relative to the issuer. The approach of offering digital tokens has evolved at a rapid pace from ICO to initial exchange offering (IEO), where an exchange collects the tokens, issues, and then sells them. In the mid-2010s, it continued to evolve to security token offering (STO), where the digital assets offered are structured to comply with applicable securities regulations. As regulators around the world begin to stipulate digital token regulation frameworks, both issuers and investors are switching to other digital capital raising solutions which can comply with the applicable regulations. Some platforms, such as Globacap and Realbocks, belong to this category and they provide unified solutions for digital capital raising together with Blockchain and Machine Learning (ML).

1.2.2.4*Digital savings*

Digital savings solutions, such as SaveBetter and Qapital, are typically more flexible and faster than traditional savings accounts. In many cases, a digital savings account is the first account to a customer, and offer a higher yield than that offered by a brick-and-mortar bank. Some digital platforms integrate saving, investing, budgeting, and lending functions into a unified wealth management tool.

1.2.2.5*Wealth management and investment*

The emergence of robo-advisors has changed the way financial advisors interact with their clients. Traditionally, a financial advisor provides advice relating to investment management, wealth management, and other financial services, and charge a fee. Robo-advisors rely on AI and ML to deliver financial planning and investment advice, and compared to traditional investment advisors, services offered by robo-advisors are typically the same or more advanced, and at a cheaper cost. While robo-advisors are considered the best option for basic investment decisions, they may not be suitable for complex decisions such as those related to real estate planning. Many banks, such as the Big-4 state-owned Chinese banks and three major local banks in Singapore, provide robo-advisors in their mobile apps.

Global assets under management (AUM) by robo-advisors are projected to reach US$1.427 trillion in 2021, up from nearly US$1.1 trillion in 2020, and they are expected to grow at an annual rate of 18.83% (CAGR 2021–2025), according to Statista.^([4](#chap1.xhtml#rfn4))

Other innovative forms include quant advisor (an extension of robo-advisor focusing on active management of investment strategies), robo-retirement (another extension of robo-advisor specialized in retirement portfolio), trading platforms with algorithmic trading and social trading (a combination of machine intelligence and expert knowledge; also known as digital brokerage), and micro investing (promote savings and investment through micro-credits or small investments), etc.

All these FinTech innovations in this area share a new term, WealthTech, i.e., new ways of investing money by leveraging technology and solid financial knowledge.

1.2.2.6*Insurance*

InsureTech (also known as InsurTech) is a term used when FinTech is employed in insurance industry, i.e., the use of technology innovations to improve the efficiency of the current insurance industry players, such as direct insurers (tied agents), smart insurance planer and management, insurance marketplaces (aggregators), and P2P insurance, etc.

We illustrate using P2P as an example. The P2P insurance networks grow with the rise of the sharing economy. The first P2P insurance company, Friendsurance, was founded in Germany in 2011. Since then, Guevara, Lemonade, Uvamo, insPeer, and many other insurers have launched P2P insurance networks. They generally serve three types of customers: (i) those who insure their own risks, (ii) those who insure risks for others, and (iii) those who insure risks for others in exchange for a premium.

Some digitalized insurers, such as Clover Health, ZhongAn Insurance, Root Insurance, PolicyBazaar, Lemonade, Acko, PolicyStree, SingLife, and DirectAsia, are targeted at affordable and personalized insurance products. They generally use AI, Big Data analytics, Blockchain, and IoT to develop customer profiles, strengthen risk management, optimize product features quickly, and enhance customer experience.

According to Allied Market Research, the InsurTech market is expected to reach US$158.99 billion globally by 2030, with a compound annual growth rate of 32.7% from 2021 to 2030.^([5](#chap1.xhtml#rfn5))

1.2.2.7*Digital currency: cryptocurrencies and CBDC*

Digital currency, also known as digital money, electronic money, electronic currency, or cybercast, is the currency available only in digital or electronic form. All cryptocurrencies are digital currencies, but not all digital currencies are crypto. The main feature of cryptocurrencies is decentralization. It means that the currency is not controlled by any central authority, such as central banks. The main principle of cryptocurrencies is encryption (hence the name). Each unit has its own code or hash. The code serves as a unique identifier for each unit. Since the first cryptocurrency, Bitcoin, thousands of cryptocurrencies have appeared in the market, e.g., Ethereum, LiteCoin, PeerCoin, EOS, cardano, etc.

Although the trust in cryptocurrencies is rising (e.g., electric automobile maker Tesla allows Bitcoin for its car purchase payments) and the value of cryptocurrencies are hitting new high (e.g., Bitcoin surpassed US$85,000 per coin in April 2021, Ethereum rose to over $4,000 in May 2021), many central banks and monetary authorities have imposed tighter regulations to prevent potential risks, such as money laundering and tax evasion.

On the other side, the central bank digital currency (CBDC), which is issued by central banks in a regulated form, attracts more attention. In this book, we will not argue which form of digital currency is superior to the other, as their existence serve their purpose. More details on the CBDC will be discussed in [Chapter 7](#chap7.xhtml).

Note that tokens are the most important form of digital currency. A token needs to meet certain conditions in order to be considered a digital currency. It has to be a unit of value that is issued by a central party, such as a central bank. It has to be accepted by an ecosystem of participants that are willing to exchange goods and services for the token. Meanwhile, it must be easy to store and trade.

1.2.2.8*Digital asset and consensus services*

Digital asset is a general concept covering digital currency, funds, private equity, and commercial real estate. Broadly, it refers to any type of digital data that is stored on a Blockchain or DLT using cryptographic methods. In most cases, it is linked to a physical asset, such as bond, stock, car, etc. It not only includes cryptocurrency and CBDC, but also encompasses software, contracts, and any other kind of data that represents an ownership right. Note that the custody of digital asset shall be also carefully considered. [Chapter 6](#chap6.xhtml) will discuss digital asset in multiple dimensions.

**1.2.3*FinTech versus RegTech***

FinTech is a broad concept because financial services cover a wide range of fields (see [Section 1.7, Appendix 1.1](#chap1.xhtml#h1-7) for an example). When a specific field is considered, FinTech may have a synonym. Besides WealthTech and InsureTech mentioned earlier, BankingTech (also known as BankTech) is another term where FinTech is applied in the general banking area, i.e., the new generation of technologies created for the banking systems, typically using the methods like AI and ML.

![](images/p12.jpg)

**Figure 1.2.**Cooperative development between FinTech and RegTech

FinTech innovations are incomplete without the complementary Regulatory Technology (RegTech) solutions. RegTech refers to technology-based innovative solutions for attenuating regulatory and supervisory challenges, including the challenges posed by the expansion of FinTech, while at the same time being savvy and secure (see [Figure 1.2](#chap1.xhtml#fig1-2)).

RegTech enables organizations to automate information monitoring, and improve the procedure of regulatory prerequisites. Each new regulation creates opportunities for the RegTech business to deploy new technology for FIs, and FinTech firms \[[3](#chap1.xhtml#rref3)\].

Another commonly referred term is SupTech (Supervisory technology), which is sometimes purposely differentiated from RegTech by different applicable entities, i.e., RegTech addresses the need of FIs and FinTech companies, whilst SupTech provides aid to Supervisors and Regulators. However, in this book, we view SupTech as part of RegTech, i.e., SupTech is a RegTech for supervisors.

**1.2.4*From BaaS, FaaS, to Platformization Ecosystem***

Banking-as-a-Service (BaaS) is an operating model in which licensed banks integrate their digital banking services directly with the products of other non-FI businesses (e.g., a retailer, an airline, and a chained restaurant or hotel). Therefore, these non-FI businesses can offer financial services such as digital bank accounts, debit cards, loans, insurance, wealth management and payment services, without owning a banking license of their own. For non-FI businesses, this is the most viable, efficient, and valuable alternative to offer financial services. Due to its scalable and agile nature, it can enter new markets easily and expand rapidly. BaaS can be further categorized to Lending-as-a-Service, Card-as-a-Service, Brokerage-as-a-Service, etc., based on different types of Application Programming Interfaces (APIs). Some typical BaaS platforms include PingAn OneConnect, ClearBank, StarlingBank, SolarisBank, etc.

BaaS is a natural expansion of open banking (see [Chapter 15](#chap15.xhtml)), where banks also provide APIs for non-bank businesses without necessarily integrating banks’ whole customer base. It also brings the “shortcut” for digital banking to corporate core banking service easily.

FinTech-as-a-Service (FaaS), on the other hand, describes another model such that FinTech companies provide technical services to FIs via their API platforms. By leveraging FaaS, FIs can optimize their end-to-end processes, customize their products and services for better user experiences, and enhance legal compliance and internal security mechanism. For example, DataGrand, a FinTech company based in China, provides integrated Robot Process Automation (RPA), Optical Character Recognition (OCR), Natural Language Processing (NLP), and APIs to help banks to process their internal documents, such as contract, invoice, financial statement, in an end-to-end pipeline. Banks can easily automate their lending process and claim process. The streamlined document analysis can also help to identify the potential risk in legal documents, thus, enable the digitalization of know your customer (KYC) and anti-money laundering (AML) together with Big Data analytics.

The popularity of BaaS and FaaS demonstrates that these new models are booming and shaping new opportunities for the financial industry. They also promote the concept of “embedded FinTech”, which essentially brings financial features into the existing consumer and business applications. With that, separated financial functions are merging with other domains, e.g., media, education, healthcare, transportation, social network, etc. As the services from multiple domains generally require a unified portal of authentication for customers to enjoy the convenience, biometrics-based digital identity might be a choice (see [Chapter 11](#chap11.xhtml)).

![](images/p14.jpg)

**Figure 1.3.**Unified BaaS and FaaS

While BaaS brings new growth opportunities for FIs, it also leads to new risks. FIs must conduct comprehensive due diligence and risk assessment for each BaaS offering and partnership. In this sense, FaaS can provide AI and Big Data-backed risk assessment and compliance service. As both BaaS and FaaS are based on API platforms, their combination leads to a new paradigm named Banking as a Platform (BaaP), as illustrated in [Figure 1.3](#chap1.xhtml#fig1-3). Essentially, banks construct an integrated business ecosystem by integrating digital services from FinTech companies with their own portfolio, so that they can offer a wider range of services and products (even other than financial domain) through a broader customer channel (omni-channel). Note that similar BaaPs may be also provided by aggregating service providers. Some aggregation platforms integrate various APIs from both FIs and FinTech to provide complex services.

Customers may use one platform while enjoying services from multiple domains. BaaP, therefore, gradually develops its value chain and inhabits its ecosystem influencing all aspects of customers’ daily life. While FIs historically provide the entire suite of financial products and services to all of their customers, FinTech companies started gaining traction and largely targeted narrow verticals and customer segments. Big tech companies such as Amazon, Google, Alibaba, Tencent, and JD, formed their empires in the similar way, eventually impacting other segments, such as telecom, logistics, and manufacturing.

With all the API and platform infrastructures, “developer as a customer” becomes one of the important forces to drive FinTech in an agile way. Instead of the traditional path of “FIs → customers”, the new path “FIs → developers → customers” might be one of the main streams in the near future. Furthermore, when banking services is replaced by the general digital assets, the path is further evolved as “digital assets → API platforms → developers → customers”.

**1.3FinTech Innovation**

The FinTech innovation department in a large organization performs multiple functions, as shown in [Figure 1.4](#chap1.xhtml#fig1-4). It shall have unique resources, such as market leading experts in new and emerging technologies. It has experiences in successfully delivering innovation from idea to solution. It builds partnerships with leading research institutions, tech vendors, and FinTech around the globe. It creates access to sandbox environments to assist development and testing in a safe environment. Usually, it funds both internal and external projects and start-ups, specially ring-fenced to accelerate initial assessment and proof of concept (PoC), delivering innovation fast.

![](images/p15.jpg)

**Figure 1.4.**A common innovation organization chart

**1.3.1*Innovation Organization***

The core objectives of the FinTech innovation department include, but are not limited to:

*   Build an internal open and sharing innovation culture to incubate the innovative business ideas
*   Stimulate innovation by engaging the business units in developing new technologies and pursuing opportunities they present
*   Educate the business in the potential of new technologies to address business issues and challenges
*   Facilitate innovation development through connecting internal and external innovation partners to maximize value
*   Accelerate and scale delivery of business sponsored experiments through leveraging sandbox environments
*   Support investments in external FinTech through our strategic innovation investment funding
*   Encourage collaboration with top research institutions for future technologies

More importantly, it is necessary to setup chief roles in charge of adoption and development for each major technology, e.g., AI and Cloud. The roles must be held by individuals with strong domain knowledge, hands-on experience, and proven record. They not only predict the technical trends but also understand technical details. They shall be the key person to make some decisions in the organizational technological committee and also drive the technical roadmap for the organization.

FinTech innovation adoption in FIs can be broadly divided into two categories: (i) applied innovation and (ii) innovation development and incubation. The former identifies, provides access, and supports delivery of technology innovation across all business units and functions.

The applied innovation team shall:

1.  Provide technical expertise to the business
2.  Support strategic innovation investments with technical due diligence to access target companies
3.  Partner with internal clients to deliver experiments
4.  Provide access to vendors’ matured technologies, products, and services
5.  Partner with universities, institutions and labs on research and development (R&D) of FinTech project

On the contrary, innovation incubation puts more emphasis on new technology and business models, which may not be mature enough to adopt in production directly. It usually spends more than one year to study the feasibility of the new idea, and another year or longer to demonstrate via an Minimal Viable Product (MVP).

It is encouraged to get funding from governmental agencies to support long-term research and development projects. For example, the Monetary Authority of Singapore (MAS) has a couple of innovation grants for various aspects, e.g., investment, digital solution adoption, AI/Data analytics technology adoption, cybersecurity enhancement, etc.

**1.3.2*Innovation Challenges***

FinTech innovation is a “sexy” concept to many bankers, but may not be the case for those who actually implement it, as there are many inherited and external challenges generally. We will also discuss some of the internal challenges in this section.

Firstly, the potential bureaucratic processes and legacy systems internally are often one of the main obstacles for innovation. It is not uncommon that an approval process for onboarding a FinTech solution can take more than 1 year due to complex internal policies, even though such a solution has been adopted by industry peers. Many chief executives including CEOs, CIOs, and CTOs at FIs treat their legacy core system as the biggest barrier to innovation. The transformation process might be slow, expensive, and even painful. Some historical failures due to the radical “revolution” have discouraged many top executives. As stability is one of their top priorities, the innovation journey to the core systems and their extended services becomes very slow.

Secondly, some hierarchical or mesh type of organizational structure might harm the innovation agility and effectiveness. Many multinational corporations may have a global innovation team in the headquarter, and at the same, some country-level teams also co-exist (but may not report to the global team). In addition, there may be multiple innovation teams formed at the department and/or business unit level. In some cases, this has worked very well, for example, there may be some country-specific regulation requirements with some dedicated solutions. In other cases, the different innovation teams may fight for limited budget/resources and attention from senior executives. The following are some examples of common mistakes in this structure:

*   Lack of clearly defined roles and responsibilities for the global team and local teams. Usually, the global team shall be in responsible for developing and executing the general innovation strategy for the whole organization, while the local team shall design their country-, business-, and function-specific innovation applications in alignment with the global strategy. For example, the global team may decide the Cloud-first and AI-first strategy for the IT infrastructure and application innovation, respectively, and may have a few demonstrative innovation projects or business models for group-wide reference. When the global team noticed that several business units adopt the same solution from the same vendor for multiple applications, they should coordinate for better resource utilization, and build a central resource pool for internal collaboration.
*   Lack of clear budget plan for innovation teams in different levels. Some innovation teams have a hierarchical reporting line, such as retail banking, wholesale banking, or IT, so that they have to compete for the budget for these projects, even if they were for the same objective. It might lead to a waste of resources and adoption delay.
*   Controversy between business-dominated and technology-dominated teams. When the business teams observe some opportunities to develop competitive products or services internally, they intend to hire specialists in the corresponding technological domain (however, the hirers often lack enough experience to judge the interviewees), or sometimes, simply re-positioning internal staff who are viewed as having “potential” capability. This often leads to some mismatch of technical roles. When it comes to a leader or decision-making position, we may observe a high chance of ineffective teams delivering some vague strategy with low-value tools. Forming a team with the right skills and experiences, and cultivating a collaborative culture in the team are the key to success delivery.

Thirdly, many banks have built their own innovation labs (e.g., DBS Asia X, Citi Innovation Labs, and Deutsche Bank innovation labs), accelerators (e.g., Barclays Accelerator, Wells Fargo Startup accelerator) or incubators (e.g., CommerzBank group main incubator), or set up investment funds (e.g., HSBC). They focus on innovation ideas and initiatives from their own staff or FinTech startups. The internal labs or accelerators typically do not have a long-term budget. Usually after a 3-year trial period, they are struggling for survival due to the lack of resource and funding. When accelerators or incubators start to partner with FinTech hubs, the solution are more likely always in proof of concept (PoC) stage only. A realistic expectation on output, e.g., direct business impact and Return on Investment (ROI), must be properly established at the beginning.

**1.4Technical Platforms for Innovation**

A healthy innovation culture shall be open and sharing. Therefore, for large organizations, we suggest building a 3-pillar platform as shown in [Figure 1.5](#chap1.xhtml#fig1-5).

The first platform is for FinTech experimental. This is a unified platform to export internal capability on FinTech to all group business and group function units (GB/GF), e.g., analytics with AI/ML, security on Blockchain, data processing on Big Data and scalability on Cloud. Each main technology may have its dedicated portal with three components as illustrated in [Figure 1.6](#chap1.xhtml#fig1-6), which are:

![](images/p20.jpg)

**Figure 1.5.**The three pillars of FinTech platforms

![](images/p20-1.jpg)

**Figure 1.6.**The three portals in the AI platform

*   *Development environment and workbench.* The workbench is generally an integrated development environment (IDE) for a particular technology or a web user interface (UI) for configurations. Developers use this workbench to deliver their projects, sometimes, a sandbox is provided for PoC in safe experimental environments.
*   *Marketplace.* It showcases some internal existing technology applications, possibly together with a demo link to user cases. The users can easily find the potential reusage and reproduction opportunity in their own domains. At the same time, the redundant resource may be sold or shared at this place.
*   *Open API.* This component exports the corresponding technologies’ capability directly to the developers or end-users so that they can obtain this capability by a simple API call.

The second one is the FinTech knowledge platform. This is an educational CoE (Center of Excellence) for business and an interactive environment for end-users, in order to promote an innovation culture. [Figure 1.7](#chap1.xhtml#fig1-7) lists key components that play a critical role in this platform, such as:

*   *Knowledge graph (KG) with visualization.* The FinTech domain knowledge is reorganized in the form of KG for the ease of reasoning. A networked visualization enables the users to find the connected information conveniently. [Chapter 5](#chap5.xhtml) will provide more information on KG.
*   *Multi-purpose interactive chatbot and web.* The web UI provides a central portal to search for the knowledge and filter users’ findings by categories and provide question-and-answer functions.

![](images/p21.jpg)

**Figure 1.7.**The components of the knowledge platform

The third one is the FinTech solution platform. This is an integrated platform for demonstrating FinTech solutions (mostly from vendors) with business analysis (e.g., SWOT). For a large FI, it is highly likely that hundreds of FinTech vendors are contacted or consulted for some potential solutions, which are then evaluated by different business units (BUs). Although some of them have been documented in internal knowledge base, e.g., Confluence, most are only shared within a small group and are unknown to the general audience in the organization. Thus, a solution-sharing platform can help to promote the potential solutions under the different stages including heard-about, contacted, evaluated, PoC/demonstrated, and productized. It can help to achieve the following:

*   Collect knowledge and information on technology providers, particularly, FinTech companies;
*   Educate the business owners on the necessity and feasibility of business applications;
*   Provide a business requirement mapping/match between user cases and solution providers via AI (e.g., KG);
*   Export innovation teams’ consulting capability to GB/GF.

This platform contains the following components as shown in [Figure 1.8](#chap1.xhtml#fig1-8):

![](images/p22.jpg)

**Figure 1.8.**Solution platform

*   *Information dashboard with categorized solution providers.* This is integrated with a vendor management system. Several dimensions of labels shall be tagged to the vendors’ solutions, e.g., the business area, the techniques applied, etc.
*   *Intelligent search engine with filtering and reasoning.* The engine can also take the advantages of KGs. For example, users may simply input their project background and scope to find the potential solutions.

The three pillars are closely connected to each other. For example, the knowledge platform can be used as a “helper” icon for the other two platforms. The use cases in the experimental platform and the solution platform can be referred to each other for similarity and relevancy. The use cases can also be used to illustrate the concepts in the knowledge platform.

As many organizations may have some similar dashboards or components, the suggested platform may simply integrate them into a unified portal as a starting point. For example, all the platforms can be accessed via a unified portal through access control (e.g., authentication and authorization), so that only permitted person can access the suitable contents.

Let us use examples of experimental platforms for AI and Blockchain, respectively. The AI and data analytics platform can provide the following functions:

*   Show internal analytics capabilities, in particular, AI and ML, via marketplace;
*   Provide a rapid development platform for AI/ML PoC projects for both technical and non-technical staff;
*   Export to and share the capabilities with various R&D teams via APIs and workbenches.

[Figure 1.9](#chap1.xhtml#fig1-9) shows a sample structure of this AI platform. The key is the shared data via data middle platform (see the next section) and the shared ML platforms under the MLOps concept (see [Chapter 14](#chap14.xhtml)) with some core components, e.g., Jupyter lab, DataRobot, Seldon, HopsWorks, etc. Through the scalable cloud service and container techniques, the unified portal can reach more users inside the organization.

![](images/p24.jpg)

**Figure 1.9.**A sample structure of the AI platform

The Blockchain experimental platform for innovation attempts to:

*   Support multiple Blockchain/DLT technologies, e.g., Corda, Hyperledge, Ethereum, etc., using container techniques;
*   Showcase the knowledge and technology on Blockchain/DLT;
*   Educate business owners for the necessity and feasibility of business applications;
*   Provide a rapid development platform for Blockchain/DLT PoC projects;
*   Export the consulting and development capability to GB/GF.

**1.5Infrastructure Innovations**

The innovation platforms heavily depend on IT and data infrastructures. However, large FIs with a long history, such as HSBC, Standard Chartered Bank, Citibank, and the Bank of New York Mellon, always have large legacy systems, which is the root cause of the slow pace of innovation as aforementioned. The development of a single platform and/or the integration of different platforms are among the top priorities of some FIs in the near future.

Most of those banks adopt a progressive modernization approach, which is a safe option if the current system can function steadily in the next five to 10 years. It essentially retains the legacy core platform but gradually minimizes its functionalities and builds a modern architecture around it. In other words, it is a bi-model architecture with the traditional core, which is usually closed and centralized in silo, and the digital core, which is often open and distributed in cloud. However, for the “new” banks and the recent digital banks, they may either fully replace the core architecture with the new tech stack or build the new tech stack from scratch.

One of the key components for the digital core is the data platform when the data becomes the most important asset of the FIs. From data warehouse, data lake to data lakehouse and data fabric/mesh, data platform has gone through continuous evolution. Since Alibaba set up the so-called data middle platform (or data middle office) strategy in 2014, similar concepts have been adopted gradually by many Chinese FIs. There are three core components in the data middle platform \[[4](#chap1.xhtml#rref4), [5](#chap1.xhtml#rref5)\]:

*   *OneData* is essentially a data management system. It includes global data warehouse/lake planning, data specification definition, data modeling research and development, data connection extraction, data operation and maintenance monitoring, data asset management tools, etc.
*   *OneEntry* is data asset catalog for data exploration, data analysis, and other services. It enables users from both business and development departments to collaborate on the platform to create data value.
*   *OneService* provides various service APIs for business systems to call directly for both real-time and batch tasks, such as thematic data services with unified SQL-like interface and diversified functionalities based on cross-databases platforms (e.g., Hadoop, Spark, Oracle, etc.) This component can be either light (e.g., only provide basic data services) or heavy (e.g., advanced data analytics and ML services).

OneData is the foundation of OneEntry and OneService. The data middle platform hits some of the pain points of FIs, e.g., data isolation of different BUs, repeated data construction with many duplications, no unified data models and catalogues, inefficient communication between business and development departments, weak data government systems, slow response to business change, etc.

The data middle platform may have significant impact on internal processes, services and products. In [Section 1.8, Appendix 1.2](#chap1.xhtml#h1-8), a unified three lines of defense (3LoDs) is discussed, where Auditing-as-a-service (AaaS) becomes a possible solution to be embedded into the business lifecycle. Similarly, we can have the so-called compliance-asa-service, risk-as-a-service, legal-as-a-service, finance-as-a-service, etc. They may share some common technology and data cores but abstract their specific domain applications as a service.

Further development of unified data platform may lead to a future cloud-based banking architecture as simplified in [Figure 1.10](#chap1.xhtml#fig1-10), where the hybrid clouds may be fused to provide an intelligent IaaS. The dedicated financial PaaS can support higher security level than the general cloud services; BaaS, FaaS, and BaaP can work together to provide wider banking services embedded into various applications in our daily life.

![](images/p26.jpg)

**Figure 1.10.**Future banking architecture in Cloud

However, it is not easy to build such a platform inside many FIs. [Chapters 8](#chap8.xhtml) and [9](#chap9.xhtml) provide some general guidance from the perspective of cloud and AI; [Chapters 12](#chap12.xhtml) to [14](#chap14.xhtml) discuss it from technical development and operations, i.e., DevOps, DevSecOps, and MLOps, respectively. Despite the existence of general guidelines, when designing data middle platform, FIs may differ in organizational structure, data demands, data foundation, and data application capabilities, which inevitably leads to huge differences in construction and implementation strategies. With changing environments externally and internally, the data middle platform is also evolving, and there is no “one-size-fits-all” solution. FIs shall choose the solutions based on their own requirements instead of a “big-and-complete” solution, with the latter often leading to a bloated collection of tools, and subsequentially, a costly but inefficient platform. FIs may also apply the concept of “Platform of Platforms” during the design phase.

**1.6Challenges, Risks and Opportunities**

In previous sections we have discussed the challenges and risks faced by FinTech firms in terms of regulatory environment and infrastructure needs. Here, we list other challenges, risks, and potential opportunities.

First, when more AI and Big Data analytics are used in FinTech, data security and privacy preserving become a big concern. Customers should have full control of their personal data like many other personal assets. FinTech firms shall not abuse the data and breach data regulations to gain advantages. On the other hand, how to use customers’ data wisely for business analysis became a hot topic.

Second, when more FinTech solutions are applied in the financial industry, cybersecurity issues would get more intensive, e.g., the third-party access of FinTech solutions inside FIs, cloud migration with multiple gateways, system complexity and compatibility between legacy systems and FinTech systems, digital platform integrations with multiple services, money laundering, fraud transactions, and malware attacks, etc. FIs are always under the pressure of cybersecurity threats, as no mistakes are tolerated for potential data privacy violation, data leakage, money loss, and reputation damage. Therefore, FIs make significant investments in this area to achieve multiple levels of protections. At the same time, customers are educated on the importance of cybersecurity, and FinTech companies can utilize one or a few aspects of the hundreds of risky points to develop their unique products and services.

Third, from the sustainable and green finance point of view \[[6](#chap1.xhtml#rref6)\], FIs shall build the additional capabilities to “incorporate Environmental, Social, and Governance (ESG) considerations into financing decisions and drive long-term sustainable economic growth” according to MAS.^([6](#chap1.xhtml#rfn6)) FinTech companies often aim for targets at reducing cost and information asymmetry and increasing efficiency, and therefore, it is natural for financial sustainability. Some FinTech firms and projects work directly for carbon-neutrality. For instance, there are some ongoing green projects led by FinTech firms, e.g., the Ant Forest by Ant Group has planted more than 100 million trees in China and expanded to GCash Forest in the Philippines. Some firms target at carbon offsetting “RegTech” via high-resolution satellite imagery to monitor projects and/or Big Data analytics to rate projects. InsurTech firms can then use parametric solutions for the dynamic pricing of climate-related projects.

Fourth, unequal access to FinTech services may generate a new request for service fairness. Adoption of new technologies heavily depends on the economic status, age, education, and other social factors. Even when WeChat acts as the largest social communicator in China, there are still many people outside of its coverage, which presents innovation opportunities for niche markets, e.g., longevity banking optimizing wealth for those aged 60 and above, young adult financial management with a total plan covering education and career, and so on.

Fifth, even in some “matured” fields, there are still innovation opportunities due to entry barriers. For example, digital payment is considered as one of the most successful innovations in FinTech in the past 20 years. It covers many financial aspects, such as digital onboarding, real-time transaction flow, personalized customer engagement, preferred payment, real-time fraud analysis, robotic process automation (RPA) for compliance automation, etc. However, cross-border transactions are still under development in many countries, as it requires collaborations among multiple countries. During the pandemic, payment failures are rising which meant the infrastructure still needs improvements, and many different payment methods are not compatible to each other. New innovation opportunities are still possible, e.g., the “Buy Now, Pay Later” and the omnichannel payment. Another example relates to payroll in which FinTech may make salary more flexibly accessible via a unique pay experience.

Sixth, customers have strong demands for personalization. For example, personalized engagement across customer journey can provide unique experiences to customers, when they are attracted from different media sources such as social media, digital marketing, and mobile app messaging, etc. This factor drives at least three innovation aspects: (i) the refined customer profiling via AI and big data, (ii) customized advertising in the omnichannel, and (iii) personalized UI design for engagement.

Seventh, from the IT infrastructure perspective, a unified data platform can serve as the foundation for innovation, and is a long-term goal to conquer at many FIs. When “Cloud-first” becomes a strategy at many large organizations, the so-called financial PaaS becomes even more important. Particularly, when many FIs select multiple cloud providers as their major suppliers, the hybrid financial PaaS platforms shall be considered seriously.

Eighth, emerging technologies, such as quantum computing, metaverse and digital twins, brain machine interface, deoxyribonucleic acid (DNA) computing, and storage and hyper-automation, can generate tons of new business opportunities. For example, a digital bank based on metaverse can provide customers a unique experience in the virtual reality with their digital identities, which may lead to a boost of digital-only neobanks. Quantum computing may ask the FIs to redesign their security and AI systems.

Last but not the least, the potentially system-wide risk associated with FinTech’s expansion could have a huge impact on financial stability. Regulations are changing rapidly to address the economic and financial needs, both locally and globally. Different countries are unavoidable to be diverse based their own economic and financial market conditions. With strong regulatory support, FinTech is booming in countries such as the US, China, the UK, Singapore, and many other countries in Asia, Africa and South America. For example, the Chinese centralized government has given a strong push in investing and defining long-term strategies via multiple 5-year plans, and China has always been at the forefront of FinTech with its huge population, talent pool, and modern infrastructures. Particularly, a stable Sino-US bilateral relation is also one key factor for the sustainable development of FinTech. RegTech creates innovative regulatory-driven transformations for both regulators and FIs.

**1.7Appendix 1.1: General Banking Structure**

Some big banks may divide their internal departments into two parts: (i) the group business (GB) and (ii) group functions (GF). GB normally contains the retail banking (may also include private banking and wealth management sometimes), wholesale banking (may also include corporate, commercial, and institutional banking), and investment banking. GF usually refers to all support functions, such as legal, audit, compliance/risk, HR, finance, IT, and logistics. [Figure 1.11](#chap1.xhtml#fig1-11) illustrates a common bank structure with four major business and various support functions.

![](images/p30.jpg)

**Figure 1.11.**General banking architecture

Retail banking focuses on individuals who are mainly on retail clients, while wholesale banking mainly deals with the large group of individuals or organizations or companies (e.g., other banks and FIs, government agencies, large corporations, and real estate companies). Sometimes, banks may use wholesale or corporate banking for relatively big organizations while commercial banking is used for relatively small organizations. As some small companies have similar service requests to individuals, banks may put a portion of commercial banking (e.g., self-employed businesses) into retail banking. Banks may also have institutional banking offering a comprehensive suite of products and services for large institutions. To further reduce the cost, some banks may merge part functionalities of retail and wholesale banking.

**1.8Appendix 1.2: Unified 3LoDs**

Based on the data middle platform, both GB and GF can gain the benefits directly. Some traditional enterprise architecture may be fundamentally changed. In the following example, we use the three lines of defense (3LoDs), instead of the core banking businesses (see [Figure 1.12](#chap1.xhtml#fig1-12)). Although the 3LoDs have their own duties, the essence is risk control and management. Looking at [Figures 1.13](#chap1.xhtml#fig1-13) and [1.14](#chap1.xhtml#fig1-14), the 3LoDs actually have some overlaps in terms of the functionalities of data and technologies. However, in a traditional sense, the first line is more in the “real-time” manner, the second line is close to “near real-time” manner, while internal audit usually applies “offline” and “batch” process.

![](images/p31.jpg)

**Figure 1.12.**A simplified 4-layer structure for 3LoDs

![](images/p32.jpg)

**Figure 1.13.**Unified line of defense

![](images/p32-1.jpg)

**Figure 1.14.**The 3 LoDs evolution

Use internal audit (IA) as an example, which focuses more on the assurance to regulator and external auditors that the risk control is effective in both design and operation. Now the question is how to measure the effectiveness. A direct way is to “duplicate” the business logics and then apply audit control. The other is only to check the high-level control/implementation. We shall note that under current situations, the audit target’s domain knowledge is still from business (and therefore, auditors have no means to go beyond this knowledge), and the data is generally a subset of the corresponding business data. When considering automation (e.g., continuous monitoring and continuous auditing), both business, compliance, and audit may use the similar techniques to implement alike functions. In other words, IA may “copy” the logics and re-implement them to verify the business result in an automatic way. It might be celebrated by a few people, as this *ad hoc* automation may cover the “full population” of some specific auditing topics. However, it might be more meaningful to consider the “full” coverage of auditing controls/topics (e.g., discontinuous points versus systematic view).

With the data middle platform, the shared data and technology will be a trend. The 3LoDs will be eventually based on the same data and technology middle platforms (for both accountability and transparency), although the access permission may be different. In fact, in my view, the fundamental techniques for the 3LoDs are almost the same.^([7](#chap1.xhtml#rfn7)) While most of the current automation projects are good for short-term targets, the innovation plan of auditing shall focus on the long-term objectives, as the organization generally does not need a “duplicated” work from IA if the overall platform has been “audited” to be effective and efficient. So, with the advance of digitalization and the coming sharing platforms, will the importance of IA in the organization become lower? The answer is no! It depends on how to redefine the roles, for example:

1.  Internal supervisor in the “middle” level (compared to the existing internal supervisors of executive management), e.g., the enhanced assurance role to properly evaluate the happened and emerging risks. IA may not focus on the “direct” business result validation (which might be the focus of the control unit of first and second lines); instead, emphasizes on the implementation and operation effectiveness after a complete auditing of the platforms with continuous-auditing/monitoring.
2.  Agile coordinator and collaborator, e.g., being involved in the platform/project from the initial design phase to the final project evaluation phases (assure the end-to-end lifecycle); auditors are not to find trouble, while preventing/reducing troubles in the future. The collaboration can help the first and second lines to avoid unnecessary issues by sharing auditing knowledges. Agility to any system changes with first-hand knowledge is one of the keys for the agile auditing.
3.  Risk capture/identification pioneer, i.e., identify the new type of risks owning to the emerging technologies (e.g., Blockchain, digital twin, complex AI model and ethics), new situations and events (e.g., the COVID-19 pandemic), and new high-impact changes (e.g., structural, organizational, and political changes).
4.  General advisor and educator, e.g., continuous advisory and education service to targeted GB/GF.

Therefore, the IA shall be independent, but equally important, it shall be open-minded, collaborative, and sharing. Independence is not an excuse to stop collaboration for IA across and beyond the organization. IA has not enough funding for long-term innovation as a support function. To keep IA strong and agile in the digitalization world, IA shall be open to wider opportunities from internal and external partners.

Auditing-as-a-Service (AaaS), as shown in [Figure 1.15](#chap1.xhtml#fig1-15), is feasible with the data platform, where data is close to the decision-making module for efficiency, the auditing can be real-time or near real-time with flexible configurations for different scenarios using APIs to embed into business directly. An auditing decision workflow could be something similar to [Figure 1.16](#chap1.xhtml#fig1-16).

In sum, the traditionally conceptual independency of IA may be out-of-date; instead, more collaborations in term of shared data and technology services may be the future. IA shall be proactive in this direction to re-orient its position. Many auditing automation projects are just duplicates of business logics and risk controls from the first and second lines, which may not be major work of the third line; instead, higher-level supervisory automation might be more attractive. Agility is also the main approach, which makes it possible for IA to let auditors be involved in the initial design and final implementation of the business projects, products, and services. The continuous auditing of lifecycles with AI, RPA, automation, etc., could be more effective and efficient.

![](images/p35.jpg)

**Figure 1.15.**AaaS in Cloud

![](images/p35-1.jpg)

**Figure 1.16.**The workflow of auditing decision using AI

**References**

[1](#chap1.xhtml#ref1).World Economic Forum and Deloitte, “Beyond Fintech: A Pragmatic Assessment Of Disruptive Potential In Financial Services,” 2017.

[2](#chap1.xhtml#ref2).B. King, *Bank 4.0: Banking Everywhere, Never at a Bank,* Wiley, 2019.

[3](#chap1.xhtml#ref3).Toronto Centre, FinTech, RegTech and SupTech: What They Mean for Financial Supervision, Toronto Leadership Centre, 2017.

[4](#chap1.xhtml#ref4).Z. Deng, Big Data Innovation: *Alibaba’s Cloud-Based Data Middle Platform* (Chinese), Publishing House of Electronics Industry, 2018.

[5](#chap1.xhtml#ref5).D. Fu, M. Jiang, Y. Ren and S. Sun, *Data Middle Office: Move Data Valuable* (Chinese), China Machine Press, 2020.

[6](#chap1.xhtml#ref6).C. C. Vergara and L. F. Agudo, “Fintech and Sustainability: Do They Affect Each Other?,” *Sustainability,* Vol. 12, p. 7,012, June 2021.

[7](#chap1.xhtml#ref7).S. Brown, *The Innovation Ultimatum: How six strategic technologies will reshape every business in the 2020s,* 1, Ed., Wiley, 2020.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap1.xhtml#fn1)Slightly different from \[[7](#chap1.xhtml#rref7)\], where it considers key digital technologies, AI, DLT/Blockchain, IoT, autonomous machine, virtual and augmented reality, and 5G communication, we think the later three types are derivations of five main technologies: AI, Blockchain, Cloud, Big Data, and IoT, which are abbreviated as ABCDI.

[²](#chap1.xhtml#fn2)J. Kranjec. “Digital Payments to Hit $6.6T Value in 2021, a 40% Jump in Two Years”. Finaria, [https://www.finaria.it/pr/digital-payments-to-hit-6-6t-value-in-2021-a-40-jump-in-two-years/](https://www.finaria.it/pr/digital-payments-to-hit-6-6t-value-in-2021-a-40-jump-in-two-years/). Accessed Nov 20, 2021.

[³](#chap1.xhtml#fn3)“Global Digital Lending Market (2021 to 2026) — Growth, Trends, COVID-19 Impact. And forecasts — [ResearchandMarkets.com](http://www.ResearchandMarkets.com)”, BusinessWire \[Accessed: Nov 20, 2021\]. \[Online\]. Available: [https://www.businesswire.com/news/home/20210406005479/en/Global-Digital-Lending-Market-2021-to-2026---Growth-Trends-COVID-19-Impact-and-Forecasts---ResearchAndMarkets.com](https://www.businesswire.com/news/home/20210406005479/en/Global-Digital-Lending-Market-2021-to-2026---Growth-Trends-COVID-19-Impact-and-Forecasts---ResearchAndMarkets.com).

[⁴](#chap1.xhtml#fn4)“Robo-Advisors”. Statista \[Accessed: Nov 20, 2021\]. \[Online\]. Available: [https://www.statista.com/outlook/dmo/fintech/personal-finance/robo-advisors/worldwide](https://www.statista.com/outlook/dmo/fintech/personal-finance/robo-advisors/worldwide)

[⁵](#chap1.xhtml#fn5)A. Goswami, P. Borasi, and V. Kumar. “Global Insurtech Market: Opportunities and Forecast, 2021–2030”. Allied Market Research, [https://www.alliedmarketresearch.com/insurtech-market-A12373](https://www.alliedmarketresearch.com/insurtech-market-A12373). Accessed: Nov 20, 2021.

[⁶](#chap1.xhtml#fn6)“Sustainable Finance”. Monetary Authority of Singapore, [https://www.mas.gov.sg/development/sustainable-finance](https://www.mas.gov.sg/development/sustainable-finance). Accessed: Nov 20, 2021.

[⁷](#chap1.xhtml#fn7)As the first and second lines generally have more funding to buy commercial software and/or hire more (internal and/or external) developers, the tools may be more “advanced” than the *ad hoc* auditing’s automation tool. However, since the tools are still operated by humans, auditing work may spend more time on the implementation and operation effectiveness. IA may also be involved from system design and implementation phase.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0002](https://doi.org/10.1142/9789811250903_0002e)

## **Chapter 2**

## **The Technical Foundations of FinTech: ABCDI and More**

***Jun Xu***

**2.1Background**

Driven by Artificial Intelligence (AI), Blockchain, Cloud, Big Data, and Internet of Things (IoT), technologies truly impact all aspects of financial services, and build the foundation of FinTech. These different technologies generally share some common features and depend on each other. For example, all of them have dedicated algorithms (software), chips, and devices (hardware) to fulfill certain functions. In another example, as illustrated in [Figure 2.1](#chap2.xhtml#fig2-1), AI may gain intelligence support from other technologies, IoT collects data as the “food” for AI, Cloud may provide computing and storage resource to train and serve the model, Blockchain protects data privacy in the process, and finally Big Data platform acts as data ETL (Extract, Transform, and Load) and injection tools for AI.

For simplicity, we denote these five major technologies, AI, Blockchain, Cloud, Big Data, and IoT, as A, B, C, D, I, respectively, in this chapter. Besides ABCDI, there are many others that nurture the growth of FinTech, which is summarized in [Figure 2.2](#chap2.xhtml#fig2-2). This chapter aims to provide a comprehensive introduction on the technical background of FinTech, and towards the end of this chapter, our readers will be able to have general conceptual and architectural understanding on how these technologies work for FIs. We will start with the basic concept and features of each technology, and then discuss their functionalities via a comparative study. In addition to the five major technologies, we will also briefly touch on other technologies, such as quantum computing and metaverse.

![](images/p38.jpg)

**Figure 2.1.**Relation between AI and BCDI

![](images/p38-1.jpg)

**Figure 2.2.**Technologies for FinTech

**2.1.1*Artificial Intelligence (AI)***

Artificial Intelligence (AI) is the intelligence demonstrated by machines, i.e., a machine performs or make decisions in a human-like manner. It is a broader concept of machines’ capability in accomplishing tasks in a way that we would consider “intelligent”. It brings tons of benefits to financial institutions (FIs), for example:

*   Improve operational efficiency through greater automation and better insights to reduce the operational cost and risk, such as robotic process automation (RPA) and optical character recognition (OCR);
*   Make faster business decisions, such as those relating to loan and credit;
*   Generate new models for both business and operation processes, such as price prediction and analysis, claim processing, wealth management advisory services, and investment process automation;
*   Create highly customized and personalized financial products and services using recommendation engines and chatbots to enhance customer experiences; and
*   Enhance the overall risk management system by fraud detection, regulatory compliance, cybersecurity monitoring, etc.

As shown in [Figure 2.1](#chap2.xhtml#fig2-1), AI is closely related to BCDI technologies. Almost all the major FIs have their AI strategies and have adopted many applications (see examples in [Figure 2.3](#chap2.xhtml#fig2-3)). In [Chapter 3](#chap3.xhtml), we will discuss AI theories and applications in the context of financial services. Given the increasing importance of ethics for responsible and sustainable AI adoption, [Chapter 4](#chap4.xhtml) will discuss AI bias and fairness in a Machine Learning (ML) experimental way.

**2.1.2*Blockchain/DLT***

Blockchain creates shared ledger databases, and is also known as Distributed Ledger Technology (DLT). In this book, we interchangeably use Blockchain and DLT, although some definitions claim they are different.^([1](#chap2.xhtml#rfn1)) It has the following key characteristics:

![](images/p40.jpg)

**Figure 2.3.**AI in financial applications

*   *Immutable.* All validated records are irreversible and cannot be changed. For some Blockchains such as Bitcoin, it is changeable unless someone can take control over 51% of nodes simultaneously.
*   *Distributed and decentralized.* All the participated nodes have a copy of the ledger. Centralized node is unnecessary, and the data can be recorded, stored, and updated on a distributed basis.
*   *Transparent.* As all nodes have a copy of the ledger with its involvement for any data access, it is transparent to all nodes for trust.
*   *Programmable.* Some Blockchains support built-in programming protocols, such as smart contract.

![](images/p41.jpg)

**Figure 2.4.**The relation between Blockchain and ACDI

*   *Open Source.* Most Blockchain codes are open to everyone for trust purpose. Some Blockchains even make their records public so that people can use it to create any relevant application.
*   *Autonomy.* As the consensus protocol makes the data transfer or update safely and all records are individually encrypted, the Blockchain system can be generally autonomous.
*   *Anonymity.* The consensus mechanism with time stamps solves the trust problem between node to node, so data transfer or even transaction can be anonymous or pseudonymous, i.e., use Blockchain address instead of individual identity.

[Figure 2.4](#chap2.xhtml#fig2-4) briefly explains the relation between Blockchain and ACDI. [Chapters 6](#chap6.xhtml) and [7](#chap7.xhtml) will present more details on its applications, such as digital assets and cryptocurrencies.

**2.1.3*Cloud and Fog/Edge***

The Cloud provides on-demand services of IT resources over the Internet. These resources include but not limited to computing, storage, networking, databases, software, analytics, virtual machine and intelligence over the Internet, where computing, storage, and networking are the three major services. Usually, customers use the cloud services in the mode of pay-as-you-go, which is flexible and scalable depending on the usage and requirements. [Table 2.1](#chap2.xhtml#tab2-1) lists some major features of Cloud.

The Cloud has three major service models, i.e., Infrastructure-asa-Service (IaaS), Platform-as-a-Service (PaaS), and Software-as-a-Service (SaaS). Many FIs are adopting the so-called “Cloud First” strategy by moving the original on-premise infrastructure to the Cloud. The majority concern is the data security in cloud (e.g., intransit and on-rest data policy using tokenization and encryption for sensitive data). [Chapter 9](#chap9.xhtml) will discuss some technologies and strategies when applying Cloud infrastructure for data integration.

“Cloud Native” technologies are accepted by an increasing number of organizations, as they empower organizations to develop and deploy, and maintain scalable, flexible, and resilient applications in modern dynamic cloud environments, via various approaches such as containers, service meshes, microservices, immutable infrastructure, serverless computing, and declarative APIs.

The term “fog computing” (or fogging) is an extension of cloud computing, and it represents the structure consisting of multiple edge nodes with computing capability connected directly to physical devices \[[1](#chap2.xhtml#rref1)\]. It was coined by Cisco in 2014. The main objective is to support resource-intensive IoT apps that require low latency, i.e., move some IT resources from the Cloud to edge. So, fogging is a mediator between local hardware and remote servers. Similar to fog computing, edge computing tries to put more processes in the local nodes. We will not purposely differentiate them. Fog/Edge technology often work with IoT to generate new opportunities for FIs. For example, by using the client’s contextual information, it can provide personalized recommendation on banking products through their own edge devices.

**Table 2.1.**The main features of Cloud computing

 
| **Item** || **Descriptions** |
| --- | --- |
| Characteristics || 

*   On-demand self-service with pay-as-you-go model
*   Broad network access
*   Elastic scalability and high availability
*   Multi-tenancy and resource pooling
*   High security and resilience

 |
| --- | --- |
| Advantages || 

*   Easy deployment and maintenance with automation
*   Almost unlimited resources
*   Efficient recovery, e.g., backup and restore data and applications
*   Improved collaboration and mobility with APIs
*   Excellent accessibility and flexibility for growth
*   Requirement on initial investment is limited

 |
| Disadvantages || 

*   Limited control or no longer in control, e.g., downtime, connectivity, etc.
*   Limited customization of services
*   Vendor lock-in, although it may be alleviated by using hybrid cloud
*   Security and data privacy concern
*   Internet bandwidth.

 |

[Table 2.2](#chap2.xhtml#tab2-2) compares the differences between Cloud and Fog computing, although they complement each other in many cases. [Figure 2.5](#chap2.xhtml#fig2-5) highlights the connection between Cloud/Fog and ABDI.

**Table 2.2.**A Comparison of Cloud and Fog Computing

 
|  || **Cloud** || **Fog** |
| --- | --- | --- |
| Location and Model of Computing || Centralized in some big data centers (DCs), although the logic structure can be distributed.Large providers have DCs located around the globe for disaster recovery. || Generally, widely and physically distributed as the edge devices may be potentially located over large geographical areas, closer to users along the Cloud-to-Thing continuum, although the logic control can be centralized or distributed. |
| --- | --- | --- |
| Size || Cloud DCs are generally huge, each typically has tens of thousands or even millions of servers. || A Fog in each location is generally a much smaller system closer to end-users.Multiple Fog nodes can be interconnected to form a large Fog system. |
| Operation || Operated and maintained fully by a team of technical experts in large companies’ relatively static environment. || Operate in various environments primarily determined by customers’ requirements.A Fog system is often operated in an autonomous way depending on its control mechanism. |
| Deployment || Generally sophisticated deployment planning despite some Cloud DC standards. || Usually, *ad hoc* deployment with minimal planning. |
| Applications || Typically support almost all applications except for those real-time services requiring millisecond or less response time.Other exceptions may be some core banking systems with highly-restricted data. || Usually support significantly more time-critical and higher security applications than Cloud. |
| Internet Connectivity and Bandwidth Requirements || Network connectivity between clients and Cloud are required for the entire duration of services.Bandwidth is an important factor that impacts users’ experience. || Internet connectivity is not an essential condition, as Fog can operate autonomously to provide uninterrupted services with intermittent connection or even without Internet. |
| Vendors || Amazon Web Service (AWS), Microsoft Azure, Google Cloud Platform, IBM Cloud Services. || AWS, Azure, Google, IBM, Cisco, etc. |

![](images/p44.jpg)

**Figure 2.5.**The relation between Cloud and ABDI

**2.1.4*Big Data***

Definitions on Big Data varies in its attributes such as dataset, processing, and value, etc. \[[2](#chap2.xhtml#rref2)\]. A definition from Wikipedia emphasizes on dataset explains it as follows: “Big data is a term used to refer to data sets that are too large or complex for traditional data-processing application software to adequately deal with. Data with many cases (rows) offer greater statistical power, while data with higher complexity (more attributes or columns) may lead to a higher false discovery rate.”^([2](#chap2.xhtml#rfn2)) Another one from DBpedia focuses on data processing:^([3](#chap2.xhtml#rfn3)) “Big data is a field that treats ways to analyze, systematically extract information from, or otherwise deal with data sets that are too large or complex to be dealt with by traditional data-processing application software.”

In fact, the definition itself is evolving, e.g., the original three main characteristics (volume, variety, and velocity) have been extended to five, six and even eight characteristics as shown in [Figure 2.6](#chap2.xhtml#fig2-6).^([4](#chap2.xhtml#rfn4)) For example, variety means that data may exist in various formats, e.g., structured, unstructured, or semi-structured, and are from multiple sources. Variety is critical for ML because it enables data-driven models to be robust enough to handle various scenarios. Value is the worthy information extracted from large datasets, i.e., intrinsic value shall be measured by assessing qualities such as accuracy and completeness. An intuitive example is the profitability that the data can bring to FIs ([Figure 2.7](#chap2.xhtml#fig2-7)).

![](images/p45.jpg)

**Figure 2.6.**The 8 ‘V’s for Big Data

![](images/p46.jpg)

**Figure 2.7.**The relation between Big Data and ABCI

FIs use Big Data to solve many practical issues, such as aggregating customers’ profiling, assessing social media impact, and evergrowing volumes with increased query. Furthermore, Big Data is also widely used in fraud detection, cybersecurity, customer acquisition and retention, risk modeling, and compliance reporting, etc.

**2.1.5*IoT***

IoT is essentially a network of networks which identify and connect digital entities with physical objects and sensing functionalities \[[3](#chap2.xhtml#rref3)\]. In our definition, IoT covers a broad-spectrum of topics ranging from 5G/6G, wireless sensing network, Li-Fi, satellite communication, to biometrics, augmented reality/virtual reality/mixed reality (AR/VR/MR) and robots. Conceptually, IoT indicates a type of new identities for objects. Technically, IoT is also called Internet+ as it is an extension of the Internet to the cyber-physical system. There are a few other synonyms, such as Internet of Everything (proposed by Cisco), Industry 4.0, Cloud of Things, Web of Things, Future of Things, and such.

A full stack of IoT contains several layers. [Figure 2.8](#chap2.xhtml#fig2-8) lists the definitions for different layered structures of IoT platforms. We cannot say one is definitely better than the other. It depends on the actual requirements of business applications. [Chapter 10](#chap10.xhtml) provides more IoT concepts with a full technical stack.

Many financial applications are rooted in IoT infrastructure and the data collected, for example:

*   Mobile apps are the most basic and necessary IoT application. When mobile banking and e-commerce are prevailing in the industry, smartphones became the most reliable data source for FIs to gain insights in areas such as customers’ browsing behavior, transaction record, user interactions, and product reviews.
*   Digital sensors are widely deployed in physical units such as bank branches and facilities to automate some internal processes and analyze consumer behavior. These digital sensors with AI techniques can identify abnormal behaviors, service exceptions, and system issues.
*   VR/AR devices and wearable devices provide special user experiences to increase the degree of personalization.

![](images/p47.jpg)

**Figure 2.8.**Layer definitions in various IoT platforms

![](images/p48.jpg)

**Figure 2.9.**The relation of IoT and ABCD

Hence, IoT can be generally viewed as the “infrastructure” for many other technologies. [Figure 2.9](#chap2.xhtml#fig2-9) represents the interaction between IoT and ABCD, using the interaction between Big Data and Cloud as an example. One of the most important components for financial Big Data is the financial Cloud. If Big Data is a rich mineral, then Cloud is the entrance and facility to the mine. Mining efficiency depends on the safety and reliability of infrastructure. At the same time, Big Data is also syngenetic to AI. AI helps IoT to sense, cognize, analyze, and predict the financial world based on the quality, volume, and precision of data collected. Conversely, AI promotes the evolution of data technology by improving efficiency on data collection and enhancing data quality to expediate the advances of big data collected from IoT.

[Table 2.3](#chap2.xhtml#tab2-3) provides some typical IoT financial examples with the aid of ABCD. Those applications are sometimes considered as part of the “Bank of Things”.

IoT evolution is accompanied with challenges from the technical, business, and social perspectives. On the technical perspective, we must consider its complexity, heterogeneity, communication paradigms, data management, software/hardware (e.g., data center infrastructure), standards, security, etc. Some techniques are still not matured, e.g., quantum sensing. On the business side, we have to solve some issues such as silos versus horizontal application domains, revenue (per device, connectivity, or data), value chain, new business models, etc. From the societal point of view, we must consider privacy, security, ease of use, social cooperation, regulations, etc. Use carbon-neutrality as an example. The IoT monitoring network globally is still under development, and the business using the IoT data is yet to explore.

**Table 2.3.**Financial applications using IoT

 
| **Applications** || **Description** |
| --- | --- |
| Digital Unified Account Management || 

*   Customers can access their multiple bank accounts with a digital interface (e.g., open banking as discussed in [Chapter 15](#chap15.xhtml)) in a unified portal, e.g., entertainment systems in autonomous cars or planes, smart home system (see [Chapter 10](#chap10.xhtml)).
*   Biometrics can simplify account access in these new types of “anywhere” digital channels (see [Chapter 11](#chap11.xhtml)). Therefore, digital signature or identity is created for authentication and authorization with multi-level security.

 |
| --- | --- |
| Automatic Payment and Smart Wallet || 

*   Smartphone and smart card: SIM-embedded bank card (possibly powered or rechargeable); multi-layer SIM card (possible additional thin layer added as token)
*   Others include wearables, smart home, connected car, etc.
*   A “wallet of things” with unique digital identity together with unified account management may provide an integrated view of incomes, costs, and expenses in multiple IoT devices.

 |
| IoT enabled Smart Contracts || 

*   IoT devices along with smart contracts and digital identity can make payments partially or fully autonomously (i.e., self-executing and self-enforcing).
*   Examples: Payment after a trial period for home appliances, after a health self-diagnosis and satisfactory feedback, auto fee collection of power generated by home-based solar panels, controlled access to a rented house with timely payment contracts, etc.

 |
| Person-to-person (P2P) Finance || 

*   P2P services, such as instant payment locally and internationally (at low cost) for both real and virtual currency, insurance based on an IoT community built on a trusted IoT platforms, etc.

 |
| Leasing Finance Automation || 

*   IoT-based system enables real-time monitoring of tangible assets for their status and usage, which provide essential pricing information for leased assets. Smart contracts may be applied.
*   Localization techniques and electric fence can restrict the movement regions of assets.

 |
| Smart Collaterals || 

*   IoT can provide real-time control and/or monitoring over assets mortgaged by customers, such as cars, manufacturing machinery, houses, and home appliances, together with their status.
*   The assets condition can be closed monitored and alerts may be triggered if any violations are detected
*   The transfer of ownership could be automatic through a smart contract.

 |
| Risk Mitigation in Trade Finance || 

*   Fine-grained tracking of the asset via RFID, Bluetooth, ZigBee, NFC, etc., is possible, similar to smart collaterals, e.g., temperature measurement of temperature sensitive goods, quantality measurement of precious metals, regional crop analysis for agriculture and farming sector, etc.

 |
| Contextualized Personal Financial Management || 

*   A personal financial planner together with a smart wallet app can offer more contextualized alerts and advice using the data from IoT devices, e.g., revise a leisure travel plan based on weather, cost, and other factors, adjust nearby parking place based on location and parking fees, switch different electricity suppliers based on real-time pricing, suggest the purchase list of grocery items based on current home inventory, etc.

 |
| Frictionless Customer Onboarding and KYC || 

*   IoT device can record users’ daily behaviors and also dig into social networks and emails, and interested websites for users’ social behaviors (see [Chapter 11](#chap11.xhtml)).
*   Unique digital identity via encryption technologies can link all data together.
*   With customers’ consent, FIs can gain holistic insights into customers’ financial behaviors, which provide more accurate information than some paper documents.

 |
| Fine-grained Auto Insurance || 

*   IoT system provides on-board tracking and diagnostic function for cars, and monitoring function for drivers, which indicate driving behavior.
*   The insurance price can be adjusted based on driving habits, driving environment, and vehicle health conditions.
*   5G and vehicle-to-vehicle networks make it more reliable.

 |
| Real-time Life/Health Insurance || 

*   Multiple wearables with smartphones can be used to track health condition in an almost real-time manner. Life or health insurance can be priced in near “real-time” manner.
*   Those data will eventually be aggregated and sent to the Cloud to build “digital twins” or an avatar in a metaverse.

 |

**2.2Comparative Study: Relations and Differences among ABCDI**

In this section, we discuss the relations between the five major technologies. Through a comparative study, we aim to identify their unique features and gain a better understanding on how they work together to grow for FIs.

**2.2.1*AI versus IoT***

IoT is essentially about sensors implanted into connected devices, which often offer streams of data through network connectivity. While IoT is more hardware-focused, AI is more on software, especially the ML models derived from data, which is possibly collected by IoT devices. [Table 2.4](#chap2.xhtml#tab2-4) specifies the differences between AI and IoT.^([5](#chap2.xhtml#rfn5))

All IoT related services inevitably follow five basic steps known as create, communicate, aggregate, analyze, and act. AI can help the last three steps by providing a smart layer working with the hardware, an edge processing unit in real time manner, some specific analytics models suitable to IoT domain, sensing filtering and fusion, etc.

With those functionalities, AI can boost operational efficiency, provide better risk management, enhance product and service qualities, increase IoT scalability, and reduce downtime. A seamless integration of AI and IoT leads to the so-called IoT analytics, which is one of the major applications of Data Analytics. Sometimes, it also needs the aid of Big Data and Cloud if the IoT infrastructure crosses over large scales and ranges (read more in [Section 2.2.10](#chap2.xhtml#h2-2-10)).

**Table 2.4.**The differences between AI and IoT

 
| **Aspects** || **AI** || **IoT** |
| --- | --- | --- |
| Common features || 

*   Both increase the efficiency of financial services
*   Both provide a harness for interoperability
*   Both highly depend on the system architecture and hardware infrastructure
*   Both may use complimentary Cloud for efficiency
*   Both can operate in online or offline manner

 |
| --- | --- |
| Data acquisition and usage || Data is the food for AI, or AI is driven by data. However, current AI technology cannot create raw data, even though it can generate synthetic data, which is still based on some raw data. || IoT collects data and feeds into data warehouse, data lake, etc., for AI-based analytics; it is all about sensed data. |
| Cost || Price is decreasing for some general applications, such as facial recognition and machine translation, while increasing for some advanced NLP applications, such as text generation. || Price is substantially reduced for the general sensors. |
| Scalability || Less scalable for computation-intensive projects. || A native feature with it being Cloud-based. |
| System and Object || AI identifies system behavior patterns based on data; no specific object is attached to the AI system. || IoT is mostly concerned about the sensory objects in a system. |
| Algorithm and Behavior || AI heavily depends on Machine Learning and Deep Learning algorithms to learn the system behavior. || IoT is all about sensory data that is used to creating an algorithm to formulate the system behavior. Most IoT devices operate under a set of predefined rules, although some of them started to embed local intelligence via AI. |

![](images/p53.jpg)

**Figure 2.10.**Mutual view of AI and Blockchain

**2.2.2*AI versus Blockchain***

Traditional Blockchain is essentially an immutable record of digital events shared in a peer-to-peer manner between different parties, with its main concerns of security, scalability, and efficiency.

As shown in [Figure 2.10](#chap2.xhtml#fig2-10), both AI and Blockchain have their own pain points and challenges. For example, Blockchain may face issues of cybersecurity, scalability, and efficiency. With the aid of AI, Blockchain can improve its security and transparency. At the same time, Blockchain can provide decentralized marketplaces and a coordinated platform for AI components and applications, e.g., secured data and model sharing, AI-enabled computing resources, etc.

**2.2.3*AI versus Cloud***

AI relies on Cloud computing for large-scale applications, and cloud storage for data source (in particular, from IoT). The major Cloud service providers, such as Google, AWS, and Azure, deliver AI services via their cloud infrastructure. They allow the abstraction of complex AI operations, e.g., call simple APIs to enable cognitive computing capabilities. At the same time, AI also enhances Cloud technology, e.g., AIOps can dramatically improve the cloud operation efficiency (see [Chapter 3](#chap3.xhtml)).

It is important to note that AI shall be on the Cloud or on-device (edge). While edge AI allows real-time ML through localized data processing for enhanced security and heightened customer experience, Cloud AI can reduce implementation barriers, improve knowledge sharing, and support complex models. When speed and latency are critical for some applications, e.g., computer vision and the virtual radio access networks used for 5G, or when privacy is a big concern e.g., limiting what data is uploaded to the Cloud, edge side implementation would be a good choice. However, a computation-intensive Deep Learning model training via large volume of data, might be better to be carried out in the Cloud.

To strike a balance between AI and Cloud, we need to carefully consider factors including computational resource, latency, energy consumption, security, and connectivity.^([6](#chap2.xhtml#rfn6)) In fact, Edge and Cloud AI complement one another, and Cloud resources are almost always involved in Edge AI use cases. In recent years, with the rise of better networking infrastructure and new edge computing architectures (e.g., the so-called AI-powered chips), the barriers between centralized Cloud AI and distributed edge AI workloads are being broken down. For example, a financial authentication and authorization device can embed biometrics such as facial and fingerprint recognition at the Edge side as the first level of security, while the Cloud side can further match the biometrics with the online database for potential risk detection. In another words, Edge AI focuses on immediate local decision, while Cloud AI can provide global optimization. Like a connected self-driving car, the edge AI senses the surrounding environments via local data processing, and then apply the brakes and/or adjust the steering wheel. At the same time, Cloud AI grasps the information about all the connected cars nearby and has access to the global map about the routes, therefore, it can provide the optimized driving path.

**2.2.4*AI versus Big Data***

Although there are differences between Big Data and AI as shown in [Table 2.5](#chap2.xhtml#tab2-5), their interdependence is more native. The training of AI relies on a large amount of data. On the other hand, AI itself has improved the speed of data collection and the quality of data, especially the structural processing of unstructured data (see [Figure 2.11](#chap2.xhtml#fig2-11)). At the same time, the Human is the adjustment factor, e.g., to coach and teach AI as a supervisory role.

**Table 2.5.**A comparison of Big Data and AI

 
|  || **Big Data** || **AI** |
| --- | --- | --- |
| Data || It generally accepts raw data with ELT techniques. || AI models generally require processed data so that features can be extracted. |
| --- | --- | --- |
| Computing || It usually applies traditional computing methods whose reactions and responses are passive without prediction. || It allows machines to perform cognitive functions with prediction on future actions. |
| Objective || Provide insight on historical data. || Make better decisions for the future. |

![](images/p55.jpg)

**Figure 2.11.**Interaction of AI and Big Data

Besides continuously growing data to make the AI system more meaningful and contextually, Big Data infrastructure can also help to expand AI and ML workforce. The combination of Big Data and AI accelerates the adoption of the new concept of Big Data Analytics in many organizations. Big Data analytics is based on advanced analytics techniques (usually, ML, massively parallel processing, in memory database and computing, distributed file system and database, cloud, MapReduce, etc.) on very large datasets. Some typical Big Data analytics platforms include Microsoft HDInsight, Apache Hadoop + Mahout, Oracle Analytics Cloud, Cloudera Analytics, Databricks, etc.

**2.2.5*Blockchain versus Cloud***

Some experts argue that the Blockchain is truly a “Cloud 2.0” in evolving, i.e., a really transparent and interconnected network without the need for a centralized transactional authority, which solves most troublesome security risks of Cloud. [Table 2.6](#chap2.xhtml#tab2-6) compares the differences between Blockchain and Cloud.

Blockchain-as-a-Service (BaaS), derived from the Software-as-a-Service (SaaS) model, is a third-party Cloud-based infrastructure and management model for companies to build and operate Blockchain apps. Due to its convenience, BaaS can become one of the driving forces of the widespread adoption of Blockchain technology. Microsoft Azure provides Ethereum BaaS in 2015,^([7](#chap2.xhtml#rfn7)) and AWS introduced the Amazon-managed Blockchain for Ethereum and Hyperledger Fabric in 2019.^([8](#chap2.xhtml#rfn8))

Another Cloud concept inspirited by decentralized nature of Blockchain named decentralized Cloud computing is also emerging. Both provide access to high-quality infrastructure with additional data breach security and flexibility in data storage costs. Note that decentralized Cloud computing is not necessarily built on Blockchain protocols, although there are some types of Blockchain-based decentralized Cloud computing platforms.

**Table 2.6.**A comparison of Blockchain and Cloud

 
|  || **Blockchain** || **Cloud** |
| --- | --- | --- |
| Common features || 

*   Computing architecture: distributed system
*   Driving force to change enterprises’ work environments and the way traditional computing works.

 |
| --- | --- |
| Interactions || Blockchain-as-a-service needs the support of Cloud, i.e., Cloud computing can push the execution of Blockchain technology-based projects |
| Data storage || Decentralized or distributed || Generally centralized data centers, although multiple copies may exist in few different locations. |
| Data validation || Distributed consensus or validation protocol || Data recovery depends on the RAID/EC algorithms |
| Security and encryption || 

*   Immutable
*   Natively encrypted

 || 

*   Mutable
*   Encrypted when necessary

 |
| Transparency || One of the core characteristics of the public Blockchain. || The visibility depends on whether it is public or private. |
| Access || Permissioned (enterprise/private) or permission less (public) depends on Blockchain type || Permissioned |

**2.2.6*Blockchain versus Big Data***

Blockchain ensures data storage, security, and privacy to increase the data integrity, whereas Big Data ensures the 8 ‘V’s of data properties to deliver better insight and value. Despite their differences as listed in [Table 2.7](#chap2.xhtml#tab2-7), the requirements and challenges related to Big Data are perfectly met by Blockchain technology, which offers transparency and security \[[4](#chap2.xhtml#rref4)\].

**Table 2.7.**A comparison of Blockchain and Big Data

 
|  || **Blockchain** || **Big Data** |
| --- | --- | --- |
| Benefits || Decentralization, flexibility, transparency, and security. || Enhanced productivity, time-and cost-saving, efficient decision-making with customer insight. |
| --- | --- | --- |
| Data integrity || Usually structured, abundant and complete, making it a perfect source for further analysis || Usually raw data; not necessarily high quality; further processing is required |
| Data sharing || Provides security || Not a native functionality |

Big Data analytics is critical for tracking transactions and presents a fundamental shift in business decision-making. On one hand, Blockchain can improve business processes in various ways as follows:

*   Expand cost-efficient accessibility of Blockchain to data analytics tools by decentralizing the necessary technology.
*   Generate new forms of data monetization, i.e., democratize the sharing and monetization of data analysis by completely eliminating the middlemen.
*   Enable fluent data exchange, i.e., allow users to process large amounts of data, while also greatly inhibiting the way these data are exchanged.

On the other hand, FIs using Blockchain enjoy benefits from Big Data analysis (and possibly with AI too, as discussed in the section of “AI versus Blockchain” and “AI versus Big Data”). In fact, the trends, models, and threats through data production and exchange can be identified by utilizing data analysis strategies on Blockchains. These issues are typically addressed through the use of pattern mining, text mining, and outlier detection algorithms. For example, Big Data applications can perform pattern recognition tasks from millions or even billions of Blockchain interactions to identify fraud users and misuse activities. At the same time, Blockchain data can be clustered and classified via ML algorithms to assess the trustworthiness of developers and users. A similar idea is also applicable for digital payment systems and insurance claim systems.

The integration creates some Blockchain-based Big Data platforms, e.g., StorJ and Endor Protocol listed in [Table 2.8](#chap2.xhtml#tab2-8). However, it is not easy to find a one-size-fit-all solution, as there are many challenges to overcome, such as security, privacy, complexity, standard, etc. For example, when Blockchain brings encrypted data, it also comes with computational overhead. If there is a real-time response requirement, the additional computational resource is not a small number. As the permissionless Blockchains allow any user to join the chain without permission, higher potential network threats may happen during the analytics processes.

**Table 2.8.**Blockchain-based Big Data platforms and Tools

 
| **Name** || **Application** || **Description** |
| --- | --- | --- |
| Streamr || IoT data marketplace || Collects large datasets from both individual users and IoT devices via leveraging “shading” techniques, so that every node in the network does not bear the weight of the entire database, to create a fast network that encompasses all data. |
| --- | --- | --- |
| ReBloc || Real estate transaction || Uses a validation protocol to ensure the accuracy and trustworthiness of real estate transactions on its platform. |
| FileCoin || Open storage market || Intends to create a decentralized storage network that would allow users to buy and sell storage resources in an open market. |
| Endor Protocol || Social knowledge || Uses data pulled from online human-based sources with AI analytics to generate crowd-based wisdom. It employs a method named “social physics” to answer future questions. |
| StorJ || Storage solution provider || Allows data to be stored in the Cloud in a completely end-to-end decentralized manner. |
| BigChainDB^([9](#chap2.xhtml#rfn9)) || Secured database || Starts with a Big Data distributed database and then adds Blockchain characteristics — decentralized control, immutability, and the transfer of digital assets. |
| Wibson || Data marketplace || Intends to create a data exchange so that consumers pay for the data usage, while the contributors are paid for data sharing, i.e., users can monetize their anonymous private information while contributors are being paid via a token-based system. |

**2.2.7*Blockchain versus IoT***

Blockchain-based IoT solutions can be built to maintain an evergrowing list of cryptographically secured and immutable data \[[5](#chap2.xhtml#rref5), [6](#chap2.xhtml#rref6)\]. Three key benefits can be brought when using Blockchain for IoT:

*   Build trust, i.e., building trust between parties and devices, and mitigate the risk of collusion and tampering;
*   Reduce costs by eliminating overheads associated with intermediaries;
*   Accelerate transactions, e.g., reduce settlement time from days to near instantaneous.

Therefore, the integrated platform of Blockchain and IoT is valuable for smart collaterals, leasing automation, real-time auto insurance, and life insurance, etc. Digital twins, acting as virtual replicas of physical objects or systems in IoT, often work with this integrated platform for a better management and optimization.

However, such integration may face many challenges, e.g., scalability, security, privacy, storage, etc., as listed in [Figure 2.12](#chap2.xhtml#fig2-12). For example, IoT device at the edge of the networks usually have limited computing power and storage space, which may not meet the requirements of the Blockchain, as the Blockchain usually needs intensive data encryption and consensus protocol operations with a large size of ledger copy. Sometimes, immature Blockchain-as-a-Service (BaaS) may lead to unsecured devices and accounts, and thus cause serious security risks.

![](images/p61.jpg)

**Figure 2.12.**Challenges for Integration of IoT and Blockchain

**2.2.8*Cloud versus Big Data***

Essentially, “Big Data” refers to the large volume of data collected with the 8 ‘V’ characteristics, while “Cloud” refers to the storage and computing mechanism that remotely stores the data in and performs any operations specified on that data.^([10](#chap2.xhtml#rfn10)) [Table 2.9](#chap2.xhtml#tab2-9) shows the common and unique features of Cloud and Big Data.^([11](#chap2.xhtml#rfn11)) For example, due to the dynamic nature of Big Data platforms, scalability is one of its essential requirements, which results in more and more Cloud deployment of those platforms.

**2.2.9*Cloud versus IoT***

Cloud and IoT share many common features in data processing with different levels, although they have their unique features, as shown in [Table 2.10](#chap2.xhtml#tab2-10).

**Table 2.9.**A comparison of Cloud and Big Data

 
| **Item** || **Cloud** || **Big Data** |
| --- | --- | --- |
| Common features || Related to data processing  
Highly scalable and robust |
| --- | --- |
| Interactions || Cloud platforms can be the carrier for Big Data technology, e.g., major Cloud providers have embedded big data functionalities.Big Data concepts accelerate Cloud deployment and adoption. |
| Definition || Provide remote resources (e.g., computing, storage, network) on demand. || A way to organize the large volume of data and generate insights. |
| Target || Provide universal access to cloud services. || Solve technical problem dealing with humongous dataset. |
| Reference || SaaS, PaaS, IaaSPublic, private, hybrid || Structured, unstructured, semi-structured. |
| Challenges || High availability, security concern, charging model, etc. || Data variety, data integration, data efficient processing, and resource management, etc. |
| Formats || New paradigm to IT resources || All kinds of data in different structures and formats. |
| Usage || When a rapid deployment and application scaling whilst maintaining centralized access is required. || When traditional centralized methods and frameworks are ineffective, and distributed framework to process large datasets is required. |
| Benefits || Low maintenance costs, centralized platform without upfront cost, disaster recovery, and much more. || Highly scalable, cost-effective, and robust ecosystem, increased productivity and efficiency, parallelism and much more. |
| Vendors || Google, Amazon Web Service (AWS), Microsoft, Dell, Apple, IBM, Alibaba, Tencent || Cloudera, Hortonworks, Apache, MapR |

They are generally complementary to each other, as the Cloud offers:

*   On-demand dynamic resources pool in a centralized data center, which is almost “unlimited”;
*   Scalable resources and services management with high elasticity;

**Table 2.10.**A comparison of Cloud and IoT

|  || **Cloud** || **IoT** |
| --- | --- | --- |
| Common features || Both of them involve data collection, storage, and computing in different level. |
| --- | --- |
| Interactions (Complimentary relationship) || Massive data generated by IoT may use Cloud infrastructure to travel from the source to its destination. Such a pathway is scalable and flexible for various workloads. |
| Characteristics || Ubiquitous IT resource over the internet || Pervasive and real-world objects |
| Processing capability || Virtual and almost unlimited || Limited |
| Connectivity || Usually over the internet for service delivery || Usually over the internet as a point of convergence |
| Big Data || A means of management of Big Data || A source of Big Data |

*   More homogeneous in term of services (e.g., data IO) for interoperability;
*   Location independent, accessible from anywhere;
*   Highly reliable and easily accessible services with certain robustness; and
*   Essentially compensate IoT’s technical constraints (e.g., storage, processing and communication);

whilst IoT offers:

*   Real world things and applications in a more distributed and dynamic way; and
*   Delivery of new service in large number of real-life scenarios

Therefore, it leads to the convergence of IoT and the Cloud, i.e., the Cloud to provide computing, storage, and communication functionalities for IoT to support the realization of the IoT vision, while IoT is to provide huge opportunities for expansion of Cloud services. In other words, the IoT Platform is integrated with the Cloud platform in two major types: (i) *Cloud-centric IoT* (bring IoT functionalities to Cloud) and (ii) *IoT-Centric Cloud* (bring Cloud functionalities to IoT), as listed in [Table 2.11](#chap2.xhtml#tab2-11). To select a suitable platform, we must consider at least four aspects, i.e., (i) the user management and human-machine interaction, (ii) the device communication and management, (iii) the application integrated services based on aggregated data, and (iv) access portal and control.

Many new models have appeared recently, e.g., Sensing-as-a-Service \[[7](#chap2.xhtml#rref7)\], which allows access to sensor data; Data-as-a-Service (DaaS), which provides ubiquitous access to any kind of data; and Identity and Policy Management-as-a-Service (IPMaaS), which provides access to identity and policy management. In particular, depending on the processing power of IoT nodes, the IoT infrastructure could be designed so that a balance between Cloud and Fog structure is achieved. Note that some IoT infrastructure may use local networks if necessary.

**Table 2.11.**Cloud-centric IoT versus IoT-centric Cloud

 
|  || **Cloud-centric IoT** || **IoT-Centric Cloud** |
| --- | --- | --- |
| Core || Bring IoT data to the Cloud by taking advantage of Cloud infrastructure. || Provide the opportunities via IoT infrastructure to take services, workloads, applications, and large amounts of data and deliver almost all to the edge of the network. |
| --- | --- | --- |
| Processing || Almost all the other components are connected through the Cloud, e.g., data processing and computing, and management tools deployment are in the Cloud. || Process and store data close to users/near to sources, e.g., distribute data to edges closer to the end-users to eliminate latency, numerous hops, and support edge/mobile computing and data streaming; create dense geographical distribution; process data and execute service locally; support end-users security. |
| Scenario || Service is provisioned with IoT objects in multiple locations; users allow for the tolerance of network processing delays. || Service is provisioned from the data in same location with strict real-time requirements. |
| Platform examples || ThingWorx, Carriots, Axeda, etc. || Microsoft Azure IoT, IBM, AWS IoT, Google Cloud IoT. |

**2.2.10*Big Data versus IoT***

Big Data is simply all about data, even as many adjectives are used to describe the “big” concept. IoT is also about data, but more focusing on the data of connected devices, no matter how big or small. [Table 2.12](#chap2.xhtml#tab2-12) lists some of their differences. Note that IoT is becoming the largest data source of Big Data.

In terms of analytics, loading data into data lakes and performing data analytics are still in the Big Data domain. To build an IOT analytics platform using Big Data technology, it must have the following capabilities:

*   Data streaming capability to ingest, aggregate (e.g., some statistical and filtering operation), and compress real-time and high-volume data collected from a wide variety of edge sensor devices in the network, and
*   Edge analytics using Edge computing and AI techniques, to enable real-time use cases that rely on low-latency and high data throughput at the edge of the network for operational performance optimization, behavioral anomaly detection, etc.

**Table 2.12.**A comparison of Big Data and IoT

 
|  || **Big Data** || **IoT** |
| --- | --- | --- |
| Core || Find insights from data for better decision-making || Provide interconnection between devices to create smart environments for automation |
| --- | --- | --- |
| Data source || Usually both human-generated and machine-generated data in an accumulating manner || Usually massive amounts of low latency, low duration, or high volume machine-generated data coming from a wide variety of sensors |
| Analytics || More on longer-duration use cases for a large scope; generally, more powerful || More on real-time use cases for local scenarios; usually limited capability in edge |
| Application || Predictive maintenance, capacity and resource planning, customer profiling and revenue prediction || Operational optimization, realtime ad bidding, fraud detection, AML and security breach detection |

To summarize, the senses of IoT, the fuel of Big Data, and the brain of AI will make the future of an intelligent and connected world a reality.

**2.3Other Technologies and Concepts**

Other concepts and technologies such as digitalization, mobility, and open banking, generally reply on the five major techniques. Therefore, we can embed them into the platforms mainly supported by ABCDI. Such integrations often lead to unbelievable innovations. The following are a few emerging examples.

**2.3.1*Quantum Computing***

Quantum computing is a new computing mode that follows the laws of quantum mechanics to regulate quantum information units to perform calculations. It applies physical properties such as quantum superposition and entanglement, uses qubits (quantum bits) composed of microscopic particles as basic units, and realizes calculations through the controlled evolution of quantum states. To understand it further, we can start with Quantum’s three basic principles:

*   *Uncertainty* principle means that it is impossible for the observer to know the position of a particle and its momentum at the same time. In other words, the particles after measurement will inevitably change compared to its status before measurement.
*   *Unclonability* principle means an unknown quantum state cannot be completely cloned, i.e., it is impossible to realize the exact copy of an unknown quantum state, so that each copied state is exactly the same as the initial quantum state.
*   *Indistinguishability* principle of non-orthogonal quantum states means that it is impossible to accurately measure two non-orthogonal quantum states at the same time. In fact, regardless of which measurement method is applied, there will be errors in the measurement results.

The three basic principles above lead to three fundamental features of quantum states, as follows:

*   *Superposition,* i.e., quantum states can be superimposed, so quantum information can also be superimposed. This is an important basis for realizing parallelism in quantum computing, that is, the superposition state of a qubit can be input and operated at the same time.
*   *Entanglement,* i.e., two or more quanta can exist in a relatively stable state of quantum entanglement in a specific environment (e.g., temperature, magnetic field). Based on this entanglement, the action of one particle will instantaneously affect another particle.
*   *Interference/Coherence,* i.e., the superposition of microscopic particles in quantum mechanics can produce interference phenomena like light in classical mechanics.

Compared with classical computing, quantum computing has exponential acceleration advantages in dealing with certain specific problems. For example, it provides solutions to large-scale computing problems required by cryptanalysis, weather forecasting, petroleum exploration, drug design, etc. It has the potential to reveal the security of high-temperature superconductivity and complex physics, and build a scientific foundation for advanced material manufacturing and new energy development.

However, it is hard to realize the high-bit quantum computers under the same operating conditions as classical computers. For example, quantum computing is probabilistic in nature and is subject to intrinsic noise, which is different from the deterministic input and output of classical computing. The implementation of quantum error correction (QEC) codes typically consumes intensive hardware and software resource overhead. In addition, there is no mature quantum random access memory (QRAM) available yet to reliably store quantum information for an extended period of time similar to RAM in classical computers, although theoretically, we shall not worry about storage space. Furthermore, due to engineering limitations, many quantum theories are yet to be implemented with approximation or heuristics. Many tech giants, such as Google, IBM, Intel, Microsoft, Huawei, Tencent, Alibaba, and Baidu, have built the first wave of quantum computers in the early stages.

Several technical paths for quantum computers’ implementation are proposed, such as hybrid approach and analog approach. The former switches between optimization steps via quantum algorithms and iterative control via classical algorithms, e.g., Oak Ridge National Laboratory’s XACC and D-Wave Hybrid. The latter uses direct quantum simulation and quantum annealing to employ controlled evolution techniques to transit the initial quantum state to a desired state corresponding to the final outcome or optimization solution., e.g., InfinityQ. In terms of hardware and materials, the current major approaches include superconducting qubits (e.g., Google, IBM, Intel, D-Wave, MIT, University of Science and Technology of China, Rigetti, SeeQC, Quantum Circuits, IQM Finland), ion traps (e.g., IonQ, Honeywell, Sandia National Laboratories), Silicon qubits (e.g., Intel, Leti, IMEC), Photons (e.g., Xanadu, PsiQuantum), etc.

Quantum computing can be generally applied to the areas of random simulation, combinatorial optimization, ML, and security. For example, transfer learning may apply the hybrid approach in quantum ML to have a part of the neural network layer retrained by a quantum computer. Simulation, such as quantum Monte-Carlo methods (QMC), likely represents the best chance for near-term production use with a more tangible advantage over classical computing, especially in simulation from a parametric distribution or from an approximate data distribution (e.g., via the quantum Generative Adversarial Network approach). In terms of security, Quantum Key Distribution (QKD) securely generates and shares cryptographic keys for better protection of sensitive information and better compliance with privacy policies and regulations. Other potential application scenarios include quantum sensing and quantum communication.

With the general benefits brought by the boost of computing capacity, speed increase of transactions, and reduction of energy cost, some typical examples of financial applications are listed as follows:

*   Trading strategies due to powerful randomness and combination, such as asset pricing, trading risk analytics (e.g., VaR and CVaR via QMC), portfolio construction and optimization, and trading, hedging, or arbitrage strategical optimization.
*   Marketing, sales, and logistics due to strength in network analysis
*   Market and economic analysis, e.g., instability detection.
*   Feature selection optimization, classification, and regression involving difficulty in computing kernel functions, highly sophisticated neural network structures, and Natural Language Processing, for quantum ML applications such as credit scoring, fraud detection, and marketing, etc.
*   Model explainability due to reversible logic gates, e.g., load application and credit score.
*   Stronger cryptographic algorithms and keys of quantum encryption for financial encryption-related activities, e.g., authentication, authorization, and data transmission.

It is the time for FIs to investigate the existing infrastructures and algorithms for future usage, although they are not equipped with direct technical capability to develop new quantum devices and algorithms. A small team in the central CTO/CIO/CDO office or global innovation department shall be built to explore potential applications. They shall work closely with research institutions and solution providers to develop necessary capabilities. Investment in quantum start-ups and university projects is also a good idea to gain IPs.

**2.3.2*Metaverse***

The term Metaverse is derived from the science fiction novel *Snow Crash* written by writer Neal Stephenson, which describes a world where people interact with various software in a 3-dimensional (3D) space as virtual images. The meta universe (Metaverse) is a collection of virtual time and space, which is a direct expansion of augmented reality (AR) and virtual reality (VR) on the Internet. Generally speaking, the metaverse is a virtual world parallel to the real world and is highly interoperable. With the continuous development of IoT, AR/VR/MR, human-machine-interface, Cloud computing, AI, Digital Twins, Blockchain, 5G, and other technologies, and the listing of the first Roblox stock of Metaverse, Metaverse is changing from a concept to a reality.

There are several fundamental characteristics of the Metaverse. Roblox summarized eight of them as identify, friends, immersive, anywhere, low friction, variety of content, economy, and civility, which can be further elaborated as follows:

*   The immersive experience with low friction from anywhere brings us a shock beyond reality. The virtual world is separated and independent from the physical world, while they are connected via “wormholes”, which enable instantaneous space transfer or time travel between two parallel universes.
*   In the Metaverse, simple and easy-to-use creative tools via AI and Blockchain give people endless creativity. At the same time, the diversity of the Metaverse provides a variety of rich content, including gameplay, props, art materials, etc.
*   Social networking with virtual identity is the standard configuration of Metaverse, similar to the tools used in reality, such as Facebook (now Meta) and TikTok (ByteDance) in many countries, WeChat in China, and Line in Japan.
*   As a virtual society, the metaverse is also inseparable from the “virtual” economy. The metaverse economy strictly defines the lifecycle of digital assets from the creation, exchange, to consumption stages in the digital market. As a special form of the digital economy, the Metaverse economy follows one basic principle of the digital economy, e.g., the larger the market size, the more prosperous the economy is, but it also has its own unique features, e.g., marginal cost reduction, marginal benefit increase, and transaction costs approaching zero with an increased market size.
*   The so-called civilization is about integrating human social behavior and natural behavior. Everyone is “multi-faceted”. In the metaverse, people appear in front of friends as Avatars, which may own different desires in their hearts. Participants can experience a more colorful life than a game. Therefore, the civilization formed in the meta-universe has both similarities and differences when compared to that of the physical world. However, the Metaverse mainly solves a human’s non-material spiritual needs, and cannot fulfill their actual material needs. In other words, a human cannot completely break away from the real world and enter the virtual world without material support from the real world. A proper coordination between the virtual world and the real world is essential.

Many tech giants, such as Nvidia, Facebook/Meta, Google, Tencent, and ByteDance, are marching towards the Metaverse. Facebook announced its ambitious new initiative on the metaverse in June 2021 and released Horizon Workrooms in August 2021, after it acquired Oculus for VR in 2014. NVIDIA announced the world’s first simulation and collaboration platform that provides the foundation for the establishment of the metaverse, NVIDIA Omniverse, in 2020. Microsoft Cloud provides metaverse technology stack by bringing together multiple components, e.g., Microsoft Mesh and HoloLens, Microsoft power platform, Azure Synapse analytics, Azure Maps, Azure Digital Twins, and Azure IoT infrastructure. Tencent continues to invest in companies and products related to the concept of the Metaverse, such as Roblox and Epic.

The Metaverse is also a key initiative for FIs, as exponential growth of this market is expected under the new normal pandemic, in particular, there is a need to attract customers of Millennials and Generation Z. Meanwhile, the rising virtual economy presents new opportunities for the financial industry. For example, the metaverse platform helps to create a virtual space extended from the real branches, public relations, and recruitment booths. The virtual space can also provide a wide range of services, such as entertainment, e-commerce, and tourism, besides common financial services, which logically lead to the promotion of digital currency.

Korea is active in adopting the Metaverse to the industry. A so-called “K-Metaverse Alliance” was hosted by governmental agencies with over 450 members. Shinhan Bank is applying metaverse-themed initiatives to develop its own platform, offering virtual banking branches and financial education. Hana Bank launched a special task-force on virtual metaverse to stimulate business scenarios and attract the younger generation in August 2021, aiming at building both online and offline metaverse platforms and designing VR-based financial services.

Metaverse is still in its infant stage, as social networking and gaming are still dominated in a less matured digital economy. In fact, since 2020, the fast-expanding Metaverse craze including the extreme hype of Non-Fungible Tokens (NFT), virtual currency, and other related elements has indicated a hidden risk of breaking away from the real world, and the need for regulatory supervision, which is currently absent. Therefore, FIs must carefully review their Metaverse initiatives (e.g., Finverse, short for financial Metaverse), such as risk, ROI, data security, and intellectual property issues, before they embark on the journey to build their Metaverse businesses.

There are so many emerging fundamental technologies, e.g., DNA digital data storage, brain-computer interface, brain reading, and 6G, which may impact the future financial industry. Some other derivatives, e.g., quantum ML, semantic web, industry clouds, digital humans, generative AI, and influence engineering, are essentially the more advanced stage of the ABCDI discussed earlier. Since we could not discuss all of them in a single volume, readers may look forward to our next edition.

**References**

[1](#chap2.xhtml#ref1).E. Hernández-Nieves, G. Hernández, A.-B. Gil-González, S. Rodríguez-González and J.-M. Corchado, “Fog computing architecture for personalized recommendation of banking products,” *Expert Systems With Applications,* Vol. 140, pp. 112, 900, Feb 2020.

[2](#chap2.xhtml#ref2).J. B. Awotunde, “Application of Big Data with Fintech in Financial Services,” in *Fintech with Artificial Intelligence, Big Data, and Blockchain,* Springer, 2021.

[3](#chap2.xhtml#ref3).N. Bansal, *Designing Internet of Things Solutions with Microsoft Azure: A Survey of Secure and Smart Industrial Applications,* Apress, 2020.

[4](#chap2.xhtml#ref4).N. Deepa, Q.-V. Pham, D.-C. Nguyen and *et al.,* “A Survey on Blockchain for Big Data: Approaches, Opportunities, and Future Directions,” arXiv:2009.00858, 2021.

[5](#chap2.xhtml#ref5).A. Panarello, N. Tapas, G. Merlino, F. Longo and A. Puliafito, “Blockchain and IoT Integration: A Systematic Survey,” *Sensors,* Vol. 19, No. 8, p. 2,575, Aug 2018.

[6](#chap2.xhtml#ref6).A. Reyna, C. Martín, J. Chen, E. Soler and M. Díaz, “On blockchain and its integration with IoT. Challenges and opportunities,” *Future Generation Computer Systems,* Vol. 88, pp. 173–190, Nov 2018.

[7](#chap2.xhtml#ref7).M. Alarbi and H. Lutfiyya, “Sensing as a Service Middleware Architecture,” in *IEEE 6th International Conference on Future Internet of Things and Cloud (FiCloud),* 2018.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap2.xhtml#fn1)In other definition, the DLT is a wider concept than Blockchain. DLT is a decentralized database managed by multiple participants, across multiple nodes. Blockchain, as a type of DLT, has its transactions recorded with a hash value, which is an immutable cryptographic signature.

[²](#chap2.xhtml#fn2)“Big data”. Wikipedia, [https://en.wikipedia.org/wiki/Big\_data](https://en.wikipedia.org/wiki/Big_data). Accessed Nov 21, 2021.

[³](#chap2.xhtml#fn3)“Big data”. DBpedia, [https://dbpedia.org/page/Big\_data](https://dbpedia.org/page/Big_data). Accessed Nov 21, 2021.

[⁴](#chap2.xhtml#fn4)K.C. Cheung. “Big Data: All the Stats, Facts, and Data You’ll Ever Need to Know”, Algorithm-XLab, [https://algorithmxlab.com/blog/big-data/](https://algorithmxlab.com/blog/big-data/). Accessed Nov 21, 2021.

[⁵](#chap2.xhtml#fn5)“Artificial Intelligence versus IoT”. Gangboard, [https://www.gangboard.com/blog/artificial-intelligence-vs-iot#difference](https://www.gangboard.com/blog/artificial-intelligence-vs-iot#difference). Accessed Nov 21, 2021; “4 Unique Differences between IoT vs AI for 2021”. Data Flair, [https://data-flair.training/blogs/iot-vs-ai/](https://data-flair.training/blogs/iot-vs-ai/). Accessed Nov 21, 2021; P. Vadapalli. “IoT vs AI: Difference Between Internet of Things and Artificial Intelligence”. upGrad, [https://www.upgrad.com/blog/iot-vs-ai/](https://www.upgrad.com/blog/iot-vs-ai/). Accessed Nov 21, 2021.

[⁶](#chap2.xhtml#fn6)G. Lawton. “Finding the balance between edge AI vs. cloud AI.” TechTarget. [https://searchenterpriseai.techtarget.com/feature/Finding-the-balance-between-edge-AI-vs-cloud-AI](https://searchenterpriseai.techtarget.com/feature/Finding-the-balance-between-edge-AI-vs-cloud-AI). Accessed Nov 21, 2021.

[⁷](#chap2.xhtml#fn7)M. Gray, “Ethereum Blockchain As a Service Now On Azure”. Microsoft Azure. [https://azure.microsoft.com/en-us/blog/ethereum-blockchain-as-a-service-now-on-azure/](https://azure.microsoft.com/en-us/blog/ethereum-blockchain-as-a-service-now-on-azure/). Accessed Nov 21, 2021.

[⁸](#chap2.xhtml#fn8)“Announcing General Availability of Amazon Managed Blockchain”, AWS, [https://aws.amazon.com/about-aws/whats-new/2019/04/introducing-amazon-managed-blockchain/](https://aws.amazon.com/about-aws/whats-new/2019/04/introducing-amazon-managed-blockchain/). Accessed Nov 21, 2021.

[⁹](#chap2.xhtml#fn9)“Meet BigchainDB: The blockchain database”. BIGCHAINDB. [https://www.bigchaindb.com/](https://www.bigchaindb.com/). Accessed Nov 21, 2021.

[^(10)](#chap2.xhtml#fn10)“Difference between Big Data and Cloud Computing”. GeeksforGeeks. [https://www.geeksforgeeks.org/difference-between-big-data-and-cloud-computing/](https://www.geeksforgeeks.org/difference-between-big-data-and-cloud-computing/). Accessed Nov 21, 2021.

[^(11)](#chap2.xhtml#fn11)P. Pedamkar. “Cloud computing vs Big Data analytics”. EDUCBA. [https://www.educba.com/cloud-computing-vs-big-data-analytics/](https://www.educba.com/cloud-computing-vs-big-data-analytics/). Accessed Nov 21, 2021; R. Stark. “Which is best in cloud computing and big data analysis?” CISIN. [https://www.cisin.com/coffee-break/Enterprise/which-is-best-in-cloud-computing-and-big-data-analysis.html](https://www.cisin.com/coffee-break/Enterprise/which-is-best-in-cloud-computing-and-big-data-analysis.html). Accessed Nov 21, 2021.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0003](https://doi.org/10.1142/9789811250903_0003)

## **Chapter 3**

## **AI Theory and Applications in the Financial Industry**

***Jun Xu***

**3.1Introduction**

Banks have continuously applied latest technologies to achieve breakthrough innovation on their services, products, as well as the customer experiences in the past decades. Starting from automated teller machines (ATMs) in the 1960s, online banking and peer to peer (P2P) payment in the 1990s, mobile banking in 2000s, chatbots, Augmented Reality (AR) and Virtual Reality (VR), biometrics in the 2010s, and digital asset and trading backed by Distributed Ledger Technology (DLT) in recent years, almost all these innovations are empowered by technologies.

In particular, Artificial Intelligence (AI), as one of the largest value creators, can potentially unlock one trillion dollars of incremental value for various industries on an annual basis. Since the late 1990s, AI has achieved many milestones, which create tons of surprises for the world. For example, IBM’s Deep Blue beat a world champion in 1997, Apple’s Siri acted as the first intelligent personal assistant in 2010, IBM’s Watson beat Jeopardy! Champions in 2011, Microsoft and Google machines defeated humans at image recognition in the 6^(th) ImageNet Challenge in 2015, DeepMind’s AlphaGo Zero had the extraordinary success at the Go game in 2016, Google’s BERT (Bidirectional Encoder Representations from Transformers) sit on the top of almost all Natural Language Processing (NLP) champions and opened a new window for academy and industry in 2018, Deepfake fooled many people with spurious photos and videos in 2019, OpenAI’s Generative Pre-trained Transformer (GPT3) continued its precursors and built many interesting applications in 2020, DeepMind’s AlphaFold 2 shocked the world in the field of medical science and biology in 2020, which is open sourced in 2021, and we can create an even longer list here.

After a few decades of rapid development, some of the AI technologies are becoming mature in Gartner’s Hyper Cycle chart of 2020.^([1](#chap3.xhtml#rfn1)) For example, Machine Learning (ML) and chatbots are already in the phase of “Trough of disillusionment”, while Deep Learning (DL) and Natural Language Processing (NLP) are at its boundary. On the other hand, there are still techniques under quick evolution, such as responsible and smart data.

At this stage, both Cloud service providers and AI companies accelerate their pragmatic commercialization. AI becomes a tool rather than a myth. People enjoy the convenience brought by AI to our daily lives, e.g., the facial recognition and chatbot services provided by banks.

Many banks started to implement the so-called AI-first strategy together with their Cloud campaign. A survey conducted by IDC and Microsoft in 2019 shows that 52% of FIs are already on their AI journey.^([2](#chap3.xhtml#rfn2))

In this chapter, we start with the general AI knowledge, e.g., its taxonomy, and then go through AI applications in financial institutions (FIs). Some recent hot topics, e.g., responsible AI and sustainable AI, will also be discussed. Last, we present the AI challenges and trends in the financial industry.

**3.2AI Taxonomy**

AI is a term for emulated machine’s intelligence of human to think and act via programming. It generally has three phases: (i) narrow or weak AI, (ii) general or strong AI, and (iii) artificial superintelligence. Despite the rapid development and evolution in the past few years, we are still in the weak AI phase, in which ML and Deep Learning (DL) are the two most representative concepts. As shown in [Figure 3.1](#chap3.xhtml#fig3-1), DL is a subset of ML, which is essentially a condensation of many subjects, such as computer science, information theory, neuroscience, etc.

A large variety of ML algorithms have either found their way into or can be applied in assisting sophisticated financial tasks at scale. A high-level overview of common ML taxonomy is shown in [Figure 3.2](#chap3.xhtml#fig3-2), where ML can be described in different types. Usually, we consider the following four types of ML: (i) supervised, (ii) unsupervised, (iii) semi-supervised, and (iv) reinforcement learning.

**3.2.1*Supervised Learning***

Supervised learning uses labeled data to train algorithms for establishing a functional relationship between features (input) and response (output) to predict outcomes or classify data. Therefore, it generally has two categories, (i) classification and (ii) regression. Supervised learning can be applied in data analysis as follows (with examples of typical algorithms):

![](images/p76.jpg)

**Figure 3.1.**AI and ML relations

![](images/p77.jpg)

**Figure 3.2.**ML taxonomy

*   *Classification:* Logistic regression, KNN (K Nearest Neighbor), SVM (Support Vector Machine), decision tree, random forest, naive Bayes classifier, hidden Markov model, and conditional random fields.
*   *Regression:* Linear regression, generalized linear regression, nonlinear regression, support vector regression (SVR), regression tree, and naive Bayes for regression.

Many advanced ML algorithms, such as gradient boosting algorithms (e.g., GBM, XGBoost), Convolutional Neural Network (CNN), Recurrent Neural Network (RNN), Gated Recurrent Unit (GRU), Long-Short Term Memory (LSTM), and Bayesian network, can handle both types of tasks.

**3.2.2*Unsupervised Learning and Self-Supervised Learning***

Unlike supervised learning, unsupervised learning mainly handles unlabeled data to discover patterns and association/correlation of the information embedded inside the data (as opposed to predictions). Unsupervised learning has two common categories:

*   *Clustering:* Hierarchical clustering, K-means, mixture models, spectral clustering, density-based clustering methods (e.g., DBSCAN/OPTICS), self-organizing maps, etc.
*   *Dimensionality reduction:* Principal Component Analysis (PCA), kernel PCA, linear/generalized discriminant analysis, nonlinear dimensionality reduction approaches (such as multidimensional scaling, *t*\-distributed stochastic neighbor embedding, isomap, locally-linear embedding, autoencoders, self-organizing maps), etc.

Self-supervised learning is a special type of unsupervised learning with self-generated supervision signals or labels. The “self-supervision” is not induced by the task of preset prior knowledge; in other words, this learning method only needs unlabeled data to formulate the pretext learning task whose objective can be calculated without supervision. A general example in DL is AutoEncoder, which predicts its input (i.e., treat the input as the target output), and its variants, e.g., variational AutoEncoder (VAE). Another example is generative adversarial networks (GANs), which is constructed by at least a generator that directly produces samples, and at least a discriminator as the generator’s adversary, which can distinguish between samples extracted from the training data and samples created the generator. Tasks can be broadly classified into four types based on different self-supervision signal or label: (i) based on data generation (recovery), (ii) based on data transformation, (iii) based on multi-modality, and (iv) based on auxiliary information. For example, the recovery of the colors (i.e., predict a color representation/colorization) and missing parts in a photo is a data generation task.

While self-supervised learning is a type of generative modeling, contrastive learning is another type of unsupervised learning focusing on learning the common features and distinguishing their differences. Different from generative learning, comparative learning does not need to pay attention to the cumbersome details of the instance. Instead, it needs to distinguish the data in the feature space of the abstract semantic level, so the model optimization becomes simpler, and its generalization ability becomes stronger.

**3.2.3*Semi-Supervised Learning and Weakly-Supervised Learning***

While supervised algorithms typically require a big amount of manually labelled training data, semi-supervised approaches have been adopted to reduce the annotation effort. In a typical semi-supervised learning setting, we have a relatively small amount of labeled training data together with a relatively large amount of unlabeled training data. We can either use the unlabeled data to help improve the performance of the supervised learning on the labeled data or use the labeled data to enhance the unsupervised learning on the unlabeled data.

If our goal is to predict based on unlabeled training data, this type of semi-supervised learning is called transductive learning. If the goal is to generalize the learner to predict for future test cases, it is called inductive semi-supervised learning. The reason why unlabeled data may help in predictive model construction lies in the intuition that the data structures in the unlabeled training set may shed light on the data structures in the labeled training set, assuming both labeled and unlabeled data come from the same distribution. In other words, if we believe similar data points should have similar outputs, then unlabeled data has value in revealing which data points are similar. In training, the unlabeled data information is typically incorporated as a regularization term in the objective function to balance the model fit between the labeled piece and the unlabeled piece. Some typical semi-supervised methods include generative models, Semi-Supervised Support Vector Machines (S3VM), graph-based models, co-training/ multi-view training, positive and unlabeled (PU) learning, etc. For example, PU learning is a particular case of semi-supervised learning, in which only positive labels are observable or accessible and the unlabeled training set includes both positive and negative cases. Of course, with such more “handicapped” data, stronger assumptions on the labeling mechanism are needed for modeling, and such assumptions need to be conceptually justified and/or empirically verified so that we can have enough confidence in the model.

While semi-supervised approaches deal with situations where only a subset of training data has labels, weakly-supervised approaches \[[3](#chap3.xhtml#rref3)\] address training data with noisy labels. Such labels may be obtained from a noisy channel, from crowdsourcing, or with weak annotators from unsupervised learning. Weakly-supervised approaches typically involve certain simplifying assumptions on the mechanism of label noise, such as the assumption that labeling noise depends only on the underlying true label but not the features. The general and realistic noise mechanisms that depend on both the true label and features are very complex to model. Weakly-supervised learning methods attempt to improve the robustness of the underlying supervised learning approaches to reduce the impact of label noise. This objective can be achieved, for example, by using more robust or noise adjusted loss functions, leveraging proper regularization to avoid overfitting to noisy labels, applying sample selection/ reweighting schemes to remove or under-weight noisy labels, adopting meta learning strategies, and transforming weakly-supervised learning problems to semi-supervised learning tasks (i.e., treating possible falsely labeled instances as unlabeled). These methods have their own pros and cons with respective to adaptiveness to new advances in Deep Learning architecture, the need for a pre-trained network, the ability to include all training samples, the requirement of additional supervision in training, the ability to handle high noise levels, and the ability to handle complex label noise structures. This remains an active research area.

**3.2.4*Reinforcement Learning (RL)***

A Reinforcement Learning (RL) algorithm learns to produce policy-driven actions while interacting in an environment, and it receives a reward or penalty depending on the outcome. The goal is usually to find the policy that maximizes the weighted sum of long-term rewards. If we have enough prior knowledge about environment dynamics, we can formulate the RL problem as a Markov decision process. Otherwise, model-free algorithms such as Q-learning, State-Action-Reward-State-Action (SARSA), Deep Q-Networks (DQN), and Deep Deterministic Policy Gradient (DDPG), can be applied.

**3.2.5*Other Learning Approaches***

In addition to the prevailing approaches above, there are also some special training techniques that generate unique algorithms to fit specific application scenarios. For example, opposite to offline learning algorithms, online learning updates the model once there is new data coming, i.e., the model is expected to at least partially update based on new data adaptively using elegant algorithms. Sometimes, it is also associated with incremental learning. Many ML models have their online versions, e.g., SVM, Extreme Learning Machine (ELM), AutoEncoder, etc. This type of algorithms is suitable for the cases with frequently updated data and changed patterns.

The individual simple models can be further integrated via ensemble learning. This approach combines the scores from at least two models (supervised or unsupervised) to produce the final result. It is expected that the ensembled models can perform better than any individual model. It usually consists of three techniques:

*   *Bagging* — It usually combines homogeneous weak learners, which build the independent models in parallel, and then use deterministic averaging process or other weighted approach to generate final result.
*   *Boosting* — It usually lets homogeneous weak learners train the models sequentially in an adaptive manner, e.g., let the newer model pay more attention to those wrongly classified samples.
*   *Stacking* — Similar to bagging, it considers heterogeneous weak learners, and usually combines the individual weak learner’s outputs as new input to train another meta model.

In addition, we want to highlight some special learning approaches that could be applied in the industry, although they might be not matured yet. Some of them are closely related and may have overlaps in terms of methodology.

*   *Active learning:* Like semi-supervised learning, active learning starts with a relatively small-labeled data and abundant unlabeled data. However, different from standard semi-supervised learning, active learning allows us to select some of the unlabeled data to query from an oracle (e.g., human experts) for their true labels. The original learner can then be enhanced with the help from the additional labeled data. As such, this can be regarded as a human-in-the-loop version of the semi-supervised approach. To minimize the cost of querying the oracle, we need to carefully select the most valuable unlabeled training instances for labeling. Some active learning algorithms are proposed to take sample informativeness and/or representativeness into consideration in the selection criteria.
*   *Transfer learning:* Transfer learning is another commonly used approach for Deep Learning without large-labeled training data. The idea is to leverage a base ML model pre-trained on rich data sets, which is similar or related to the training data required for learning the new model from scratch. If the base model can provide the lower-level network structure and/or features, all we need to do is just to use a relatively smaller amount of additional data to train the higher-level network structure and/or features. In addition to the cost savings from smaller training data, training only the higher-level network structure can also save significant amount of compute resources during model development. Transfer learning has proven its value in computer vision and Natural Language Processing (NLP), which in turn can be applied in data management tasks for information extraction and semantic parsing. In addition, it can also be used in other areas such as code optimization and log data processing, as good quality pre-trained base ML models are already available. It should be emphasized that even for powerful pre-trained models such as GPT-3, the base model itself may not work well for a domain specific application. The base model usually needs to be refined, customized and tested with domain specific data.
*   *Multi-task learning:* This is essentially supervised learning devising a model that can be trained on multiple related tasks. Compared with training on any single task, the performance and generalization of the model can be improved through multi-task training. Usually, these tasks share some common features or some foundational layers in the deep neural network; and the outputs may be predicted by different part of the model. For example, a word embedding in NLP can be used across multi-tasks, such as Name Entity Recognition (NER), text classification, and text generation. In some definitions, people treat it as a subset of transfer learning.
*   *Meta learning and few-shot learning.* Meta learning models learn from other learning algorithms, supervised or unsupervised. When it applies stacking techniques to combine the outputs from other learning algorithms, it might be a type of ensemble learning. When it learns across multiple related prediction tasks, it may be a multi-task learning. Few-shot learning is one type of supervised meta learning that uses a very small number of samples. Many approaches characterize few-shot learning as a meta-learning problem. Few-shot learning is also considered as a special case of transfer learning sometimes. In this sense, meta learning is closely connected to transfer learning, and their combination meta-transfer learning can be also applied for few-shot learning.
*   *Federated learning and swarm learning.* Different from traditional centralized learning, which requires the data aggregated in one server or cluster, federated learning trains the models across multiple decentralized edge nodes (e.g., devices or servers), each holding its own local dataset, i.e., these nodes do not exchange data between each other, while a dedicated parameter server responsible for aggregating and distributing local learning (parameter centric). Federated learning ensures data privacy or data secrecy of different parties, while fully utilizing the information from all data. Swarm learning \[[1](#chap3.xhtml#rref1)\], an extension of federated learning, trains its parameters via the Swarm network (e.g., blockchain-based peer-to-peer networking) and builds the models independently on private data at the edge nodes without the central coordinator for parameters. This eliminates the potential risk of the third party that holds the centric parameter server.
    
    Both learning methods provide a way for FIs to fully utilize their data. For example, within a multinational bank, data from different countries can be fed into this learning framework without moving the data out of their country. Different banks can also build a unified model without sharing their data, which is very useful when comes to financial crime detection and risk management, e.g., Know Your Customer (KYC) and Anti-Money Laundering (AML).
    
*   *Privacy-preserving ML* (PPML). This category includes but is not limited to Homomorphic Encryption, Differential Privacy, Secure Multi-Party Computation, and Anonymization, which can be applied to both centralized learning and federated learning. A related concept is privacy-enhancing techniques, which intend to provide both trusted environment (e.g., confidential computing) for sensitive data and encrypted data processing in decentralized manner.

**3.2.6*Knowledge Graph and Graph Neural Networks***

Knowledge graph (KG) represents a unified framework to organize, manage, and consume a collection of interlinked entities (concepts, hierarchies, relationships, interactions, etc.) associated with target business application and data. It can process and represent data and knowledge in a very similar way to what a human brain processes and stores information. Therefore, it is able to incorporate human expertise into a ML model to make meaningful decisions.

The KG has wide applications in FIs when the “connections” play a key role. It is an excellent tool for data management and solve the so-called isolated data silos issues, as it can link the data, metadata, data system architectures, data access control or logs, security incident identification or mitigation, data policies, data access policies, compliance policies, analytics, data processes or workflows, business intelligence (BI) dashboards or reports, applications or APIs that produce or consume data, etc.

By connecting all the internal data and extracting inside relations, it can provide a full spectrum of data value, enterprise risk, and regulatory compliance, and then can be applied to KYC, due diligence, investment decision, insurance underwriting, claiming processing, regulatory report, trade surveillance, etc.

It is also an important component in financial anti-fraud and anticrime, such as AML, anomaly detection, insider treats, suspicious activity report, counterfeiting, etc. KG can real-time identify fraudulent patterns by traversing huge number of nodes and edges of the social and transaction network built on CRM, trading, loan, transaction, logs, and third-party data. Similarly, the recommendation system can also use the connections between users and products with embedded common sense to find the suitable recommendation suggestions. Chatbots can use the built-in reasoning network to provide better conversional experiences.

The KG also faces many challenges, such as completeness, correctness, etc. Graph Neural Network (GNN) is one of the solutions to overcome those challenges. GNNs are a class of DL methods (e.g., Convolutional Neural Network (CNN)) with graph embeddings. They can provide a simple means to handle node-level, edge-level, and graph-level prediction tasks. In fact, with the Graph-structured data, GNN can solve various problems such as node classification (classify samples represented by nodes), graph classification (classify the whole graph into different categories), graph clustering (cluster the data in the form of graphs), link prediction (predict the connection between nodes), and graph visualization (present the data in network). Another relevant concept is Graph Embedding, which represents the nodes of the graph in a low-dimensional vector space, while retaining the network topology and node information, so that existing ML algorithms can be applied directly in subsequent graph analysis tasks. Some graph embeddings based on DL algorithms also belong to graph neural networks. Both GNN and graph embedding are also important tools for NLP. More details are discussed in [Chapter 5](#chap5.xhtml).

**3.3AI Applications in the Financial Industry**

With various AI and ML technologies, some general applications can be formed. For example,

*   *Image recognition* can help to identify the objects in an image (object detection) and recognize its categories (image classification). The most recent techniques can “understand” the content of an image and generate descriptive text and story. The most famous example is facial recognition. Nowadays, under ideal static conditions, the recognition accuracy can be as high as 99.99% with a false rate lower than 0.001%.
*   *Text recognition* can recognize text in an image, e.g., labels, numbers, etc. The most famous example is Optical Character Recognition (OCR), which is the first step towards further text processing of scanned documents. Advanced OCR can convert text into their original format, e.g., a table with its original location information. Some automation tools that using OCR techniques are developed for invoice, contract, offer, and deals processing.
*   *Text processing* helps to extract key information from documents and analyze properties of these documents. For example, it may return the contract value, parties, time, etc., for a contract document, and then we can check if the parties and price in a contract are correct.
*   *Text classification* can tell which category that one document belongs to. For example, some historical documents can be separated based on their functions (e.g., invoice, offer letter, contract), types (e.g., news, entertainment, sport), countries, and business units.
*   *Sentimental analysis* is a special form of text classification to analyze the sentimental emotion (e.g., anger, joy, tepid, disgust, worried, sadness, etc.) and attitude (e.g., agree or disagree) via textual description and emoji. For example, we can identify the risk of a company via analyzing the online comments. If many online comments are against a company, this company may have a high risk. We can also use it internally to analyze the staff’s attitude towards some topics.
*   *Speech recognition* can convert audios into text, e.g., phone calls, meeting conversations, and technical presentations, etc. It is often used in audio conferencing, customer service, and auditing. For example, it can help call centers to convert audio documents into text, so that we can analyze the text later for service quality improvement and internal audit.
*   *Pattern recognition and anomaly detection* can find patterns from the data and detect the anomaly or outlier. For example, ML can be used to identify attack patterns in cybersecurity.

Some of the techniques mentioned above are applied simultaneously. For example, we can apply image processing and anomaly detection algorithm to find out the anomaly behaviors of humans in surveillance videos. [Table 3.1](#chap3.xhtml#tab3-1) further lists some typical AI applications used in multiple domains.

**Table 3.1.**Explanation of some applications

 
| **Applications** || **Explanation and benefits** |
| --- | --- |
| Chatbot || 

*   Automatic solution suggestion and recommendation, e.g., Q&A, knowledge base, etc.
*   Omni-channel integrated with others, e.g., CRM.

 |
| --- | --- |
| Credit Scoring || 

*   Profile customer risk more accurately, taking into account the person, not a stereotype.

 |
| Anti-fraud and Security || 

*   Analyze documents for account registration (RegTech), detect anomalies in patterns within accounts, and more.

 |
| Robotic Process Automation (RPA) || 

*   Replacement of routine repeatable works, e.g., invoice processing, payroll, sales order, customer/HR information processing (onboarding/offboarding), etc.
*   Semi-automation in documentation, workflow, etc.

 |
| Asset Management || 

*   Fast and accurate prediction to reduce the number of intermediaries, helping reduce operational costs.

 |
| Supply chain and inventory optimization || 

*   Prediction for the best solution of inventory/route/ supplier/etc. with lower cost.

 |
| IT system analytics || 

*   Automated deployment, modularity, use of microservices, avoid excessive fine-grained optimization early on.
*   Big Data analytics and predictive maintenance to prevent failure.

 |
| Collaborative Robot || 

*   Completion of IT hardware/software installation/ maintenance/monitoring/etc.

 |

**3.3.1*General Applications***

Compared to other traditional industries, such manufacturing and food, FIs take the lead in AI adoptions, although sometimes they are a bit conservative in applying the latest ML development. AI techniques have been applied across all front, middle, and back offices at FIs, and covers various financial service areas, such as retail banking, wholesale banking, private banking, IT, audit, etc. [Table 3.2](#chap3.xhtml#tab3-2) summarizes some popular AI applications in the industry, such as price prediction, resource allocation, risk analysis, and loan or credit approval applications.

With these AI applications, FIs expect to achieve:

*   Better quality of services and customer experience;
*   Meliorated production lifecycle and improved production continuity and rhythm;
*   Increased automation, enhanced workforce efficiency, collaboration, and productivity;
*   Increased availability, accuracy, and consistency for operational and maintenance work.

In the following section, we will use general banking as an example to describe some typical applications. Large banks usually divide their organization into two parts, the group business (GB) and group functions (GF) as discussed in [Chapter 1](#chap1.xhtml). The GB normally contains the retail banking (it may also include private banking and wealth management), wholesale banking (it may also include corporate, commercial and institutional banking) and investment banking. The GF generally refers to support functions, e.g., legal, audit, compliance/risk, HR, finance, IT, and logistics departments. GB and GF may be integrated to an extent.

**3.3.2*Retail and Private Banking***

As more and more banks provide similar services and products, user experience becomes the key point to attract and retain customers.

Some customer-facing applications, e.g., chatbots and document RPA it is defined in [Table 3.1](#chap3.xhtml#tab3-1), adopt AI quickly to improve service efficiency and quality. For example, HBSC’s virtual assistant, Wells Fargo’s Facebook Messenger chatbot, United Overseas Bank (UOB)’s processing bot, and Bank of America’s mobile voice assistant “Erica” are replacing the work previously done by client service officers. Due to the strict requirement on accuracy, most of these robots have predefined question and answer pairs, which limits the usage of the latest generative NLP models. This is relieved for the internal staff facing chatbot, which may require a higher recall than a precision value. Thus, some latest reading comprehension (i.e., text understanding by AI engine) models can be directly applied to internal documents so that the chatbot can answer users’ questions.

**Table 3.2.**AI applications in FI

![](images/p89.jpg)

The basic objective of the RPA is to automate some routine repeatable works with a certain level of aid from software and hardware. Such routine work can relate to invoice processing, payroll, sales order, customer complaints, etc. The early stage of RPA is mostly rule-based, but now it becomes more powerful with the aid of ML techniques.

AI is also widely used in service centers, ranging from the service quality monitoring to automatic calling. For example, based on certain regulations in China, sales staff must clearly inform the clients about the risks of the financial products before they can sell it. These conversations shall be taped. Instead of conducting manual checks on the sample data, AI engines can be used to understand the whole population of conversations so that it can detect whether key information has been stated by the staff and consented by the client. Using sentimental analysis, we can further identify the mood of the client and staff, and assess his/her level of satisfaction with the service delivered.

AI-aid credit scoring systems are also widely used in banks to promote personalized and prompt decision-making. In some Chinese digital banks, e.g., WeBank (Tencent) and MyBank (Alibaba), the almost instant loans have been carried out for years.

Through various AI techniques with IoT (see [Chapter 10](#chap10.xhtml)) and automation, personality can be embedded into the products and services, such as personal financial assistant (robo-advisors) to manage your income, consumption, investment, loan, etc. Portfolio managers can also gain benefits for the portfolio optimization, selection, and allocation.

Thus, AI actually can accompany the customers for their full banking journey. For example, when a potential customer starts to apply for an account, she or he can use the chatbot for the questions encountered during the application. During the online application through web or mobile, the bank may use an AI robot to detect if the applicant is a human or a bot agent. After the required forms are filled and documents are submitted, the onboarding system will process some image documents using OCR, e.g., the scanned ID card, salary, and address proof. All the client information extracted will be further verified by due diligence steps, such as KYC. Together with the traditional credit bureau query, KG-based engine may provide a much wider knowledge about the applicant. An AI algorithm will suggest an approval or rejection decision to a bank staff. Once the application is accepted, the bank may use a profiling system to understand the customer better, which is further refined with the customer’s financial activities associated with the bank. The bank may use the third-party data, e.g., social network and e-commerce, to have a further enhanced “label” for the customer. A recommendation engine may help relation managers to provide some potential financial services or products to the customers by wisely using all the data. A transaction monitoring system is always running in the background to identify if a transaction is illegal.

**3.3.3*Wholesale Banking***

Wholesale banks are stepping up efforts to streamline receivable and payable processes of client accounts using AI technology. For example, AI-backed robots are used in front-end activities, e.g., secure customer identities, provide frictionless onboarding and streamline processes, and enhance user experiences.

In the middle-end, AI is used for fraud detection and anti-money-laundering (AML) activities. With anomaly detection and predictive analytics, banks can protect their corporate clients’ privacy and funds. Predictive analytics in automated pipelines could enable a bank’s system to check accounts receivables and analyze their behaviors. At the same time, the bank can also identify new opportunities across clients and markets and increase conversion rates, thus building a revenue-driving synergy by combining both external and internal data.

In the back-end, AI is applied widely in supply chain management and inventory optimization. We can always predict when the stock will run out and what is the next year’s demand. This type of information can definitely help to optimize cost. RPA with OCR is used for document digitization. Legal, finance, and compliance departments digitalize all these documents for full compliance and regulation requirements.

**3.3.4*Global Market and Trading***

Algorithmic trading has a long historic application of ML, where the buy or sell decision is made by algorithmic models. It enriches first principle-based models into data-driven models with features such as historical price, bid-ask spread, limit order book, position-sizing, etc. Recently, it also integrates AI-driven microeconomics of engineering operations into their financial outcomes, in response to the highly competitive landscape, constant pricing pressures, and fluctuating demand cycles. AI-backed news/blog analysis (e.g., find out the potential risk) and user behavior analysis (e.g., identify the customers’ attitude) are also embedded by using DL models, such as CNN, LSTM, and deep Q-learning.

Similar techniques are also applied in asset pricing and derivative market e.g., options, futures, forward contracts, hedging strategy, etc. With the rising of cryptocurrency and Blockchain, trading price prediction is also under active study.

**3.3.5*IT***

With aforementioned fundamental functionalities, we can also apply AI into many areas in IT. For example, ML can be used in IT system analytics, including the data extract-transform-load (ETL), data analytics, system analysis, etc. It can be used for automated deployment, modularity, and use of microservices. It is particularly useful for predictive maintenance. Some industries such as banks suffer downtime costs of tens of thousands of dollars per minute. Predictive maintenance can help to predict potential failures. Before the actual system fails, you can prepare to avoid the same level of loss.

Another example is the collaborative robot (Cobot) which utilizes ML to implement automated and flexible processes with human. The Cobot can learn from past experiences to mimic. Thus, it can help IT operators to complete many hardware deployment and maintenance works. However, the most promising usage might be AIOps, which will be discussed in [Section 3.6.1](#chap3.xhtml#h3-6-1).

**3.3.6*Auditing***

There are usually seven steps in a general auditing process, as shown in [Figure 3.3](#chap3.xhtml#fig3-3) \[[2](#chap3.xhtml#rref2)\]. Traditionally, most of those steps are manually processed. However, with AI techniques, some automations with high coverage of auditing samples become feasible.

![](images/p93.jpg)

**Figure 3.3.**Auditing procedure

For example, in the first step of pre-planning, we shall try to understand the auditing business field. Almost all activities in this step are performed manually currently. However, an AI-based solution can collect and analyze both internal and external data to develop common objectives and scope. More advanced systems can even understand the auditing coverage based on regulatory requirements. In the second and third steps, machine reading techniques can understand the chart flow in predefined formats, and convert them into the knowledge graph. After that, the AI reasoning algorithm can estimate the risk level and corresponding cost.

AI can also automate the contract and audit report preparing with NLP techniques. Most important, AI allows continuous monitoring and continuous auditing with almost 100% of population coverage.

**3.4More Considerations**

**3.4.1*AI Risks***

Although the algorithm and model performances are the major consideration in the early days, FIs have already realized the importance of AI risks, such as data and model, as FIs face the general public and take the social responsibility. [Figure 3.4](#chap3.xhtml#fig3-4) lists some major AI risks. In fact, many data-driving decisions root from social contexts that affect and are affected by the social and personal data in equal measure. In addition, AI systems may be under various attacks for dataset, features, model, and IO interfaces, as shown in [Figure 3.5](#chap3.xhtml#fig3-5) \[[3](#chap3.xhtml#rref3)\]. In the following, the data privacy, model explainability, and ethical risk will be further discussed.

**3.4.2*Data Privacy and Proper Usage***

Financial data represents a relationship between customers, businesses, and brands. There is often a perception gap between FIs and consumers on how a consumer view their FIs and how the FIs believe they are viewed. Customers expect to receive benefits for sharing their data in the form of offers, reduced interest rates, recognition, and other rewards. However, not all FIs have the ability to provide advance and dynamic insight from the data in real time through digital channels.

![](images/p95.jpg)

**Figure 3.4.**AI risk

![](images/p96.jpg)

**Figure 3.5.**ML attack types

[Table 3.3](#chap3.xhtml#tab3-3) shows some typical data usage of AI applications. The proper usage shall be governed by both external regulatory requirements (e.g., GDPR of the EU, PDPA in Singapore) and internal compliance and risk requirements. FIs shall pay attention to the security during the data collection and transmission, the collaboration during the data processing and application, and the circulation during data analytics sharing. More information can be found in [Chapter 4](#chap4.xhtml).

Data-driven ML cannot learn automatically to infer knowledge by analogy; therefore, it has poor robustness (i.e., easily be affected by noise). There are huge differences between the mechanisms and methodologies of ML and human learning. To enhance the capability of ML, it is necessary to integrate psychology, cognitive science, and neuroscience learnt from human learning mechanisms, and incorporate common sense and reasoning into the learning procedure.

**3.4.3*Explainable AI***

Explainable AI (XAI; sometimes, it is exchangeable with Interpretability) has attracted more and more attention recently. Essentially, XAI aims to make AI systems (both modeling and outcome) more understandable to human. It improves transparency via human understandable language to outcome, enhances trust by increasing the confidence in decision-making, and reduce bias by regulating data pattern and model behavior.

**Table 3.3.**Data usage for financial applications

| **Applications** || **Basic information** || **Advanced information** |
| --- | --- | --- |
| Application (credit card) || Individual basics, Family basic, employment, banking account || Web |
| --- | --- | --- |
| Target marketing (credit card) || Individual basics, Family basic, employment, banking account, credit || E-commerce, personal IoT data, Web, social network |
| Target marketing (loan) || Individual basics, Family basic, Asset, employment, banking account, credit || E-commerce, personal IoT data, Web, social network |
| Payment Default || Individual basics, Family basic, || Web, asset, e-commerce |
| Anti-fraud (Credit card) || Individual basics, Family basic, Web || E-commerce, personal IoT data, social network, |
| Issuance (health) || Individual basics, Family basic, Health basics || Personal IoT data, web |
| 

*   Individual basics — ID, gender, age, education, contact, living place, etc.
*   Family basics — Marital status, children, etc.
*   Health basics — Historical critical illness, current critical illness, etc.
*   E-commerce — Purchase behavior and history
*   Web — Browsing behavior, app usage pattern, micro-blog, etc.
*   Social networking — Telecom, Facebook, twitter, WeChat, QQ, dating, etc.

 |

For financial applications with high requirements on security and compliance, there is a difference to the extent to which it needs to be explained. Although explainability is not the primary goal of AI research, more and more FIs implement their internal frameworks for XAI due to business decisions, and customer and internal governance requirements.

Similar to the situation that human intelligence itself is still a “black box” (i.e., unexplainable human brain.), some deep artificial neural networks are not fully explainable yet, although they work better on explaining the decision-making processes. Hierarchical XAI may have the most stringent interpretability directly from mathematics (e.g., strict mathematical proof) and statistics (e.g., causal inference), and the most intuitive approach from visualization. A survey in 2018 \[[4](#chap3.xhtml#rref4)\] provides an entry point to learn the key aspects of XAI, where it divides the XAI into two categories, (i) the intrinsic methodologies (all model specific, e.g., decision tree, linear regression) and (ii) the post-hoc methodologies (usually model-agnostic, e.g., LIME^([3](#chap3.xhtml#rfn3)) and SHAP).^([4](#chap3.xhtml#rfn4)) A recent work by Prof Yi Ma from UC Berkeley attempts to provide a reasonably theoretical framework to explain modern deep (convolutional) networks from the principles of data compression and discriminative representation (and “group invariance”), showing that forward propagation can derive all parameters such as deep architecture and linear operators without back-propagation \[[5](#chap3.xhtml#rref5)\].

Explainability and prediction accuracy are often two contradictory metrics. Just like high computational performance versus low power consumption, and wide versatility versus high efficiency, it is hard to hold both. However, when the “idiotic” errors of artificial neural networks are accompanied by their high predictability, improving interpretability is a suggested way to prevent errors. Diverse applications have very different requirements for interpretability.

**3.4.4*Artificial General Intelligence (AGI)***

In recent years, DL, in particular, the NLP and computer vision (CV), has achieved significant progresses. In Stanford Question Answering Dataset (SQuAD) hosted by Stanford University and GLUE/super GLUE Benchmark by New York University and other organizations, DL achieved better results than the human’s average score. Even in more difficult tests, e.g., Winograd Schema Challenge (WSC), GPT-3 and BERT get high marks (the latest benchmark is 90.1%).

In many fields, we find that AI capability is significantly enhanced with increased computational power. Researchers and developers used to rely on a variety of feature engineering to train the AI model, but now they rely on a large amount of computational resource to let the DL model exert its power, and then defeat the feature engineering. Programs such as AlphaGo Zero are able to find the rules by themselves. However, as pointed out by AI practitioners, we may overestimate the inference capability of those models. For example, the current deep neural network (DNN) model still cannot develop its own structure without human knowledge such as convolution and LSTM components. Even for AlphaGo Zero, the “rule” of rules on reinforcement learning is still defined by humans. The machine may still lack a powerful ability that human beings possess, e.g., the “coun-terfactual” ability.

Professor Noriko Arai from the University of Tokyo, Japan, spent nearly 10 years organizing a research team of around 100 people to carry out the project named “Todai Robot” to “pass the entrance exam to University of Tokyo” by 2021. The project is considered one of the most influential AI research projects in Japan after the fifth generation of computers. Although the robot outscored 80% of students who took the test, Todai Robot flunked eventually as it did not achieve the design objectives. In 2020, she clearly declared that there were many obstacles that cannot be surpassed via the current AI technologies, and the biggest difficulty was “common sense”.

On June 5, 2021, Tsinghua University announced the first virtual college student named Huazhibing, to be admitted to its Department of Computer. The university intends to use the virtual student to test the “Enlightenment” (Wu Dao) V2, a super-large-scale AI model released on June 2, 2021, and continuously improve the general intelligence level of the virtual human system through ML. However, the ambition to grow Huazhibing’s intelligence to a university graduate within three years caused some intensive debates.

Those projects are just a few attempts where human beings are working toward the so-called artificial general intelligence (AGI; sometimes, it is also called General AI or Strong AI). AGI is the ultimate goal of the modern AI study. So, when will this goal be achieved? In a survey conducted in 2018 on 23 top AI scholars in the world \[[6](#chap3.xhtml#rref6)\], the most optimistic experts gave a time of 2029, and the most pessimistic experts believed that it would be 2200. On average, the time point is 2099, which is not so “near” yet. By acquiring enough background knowledge and making machines have more common sense, the versatility of AI systems can be gradually improved, but it is not necessary to pursue versatility like that of the human brain as the main research goal in the near future. We may have more urgent research goals than the maximum versatility to pursue, such as robustness and adaptability to the complex environments and specific applications, and the security and ethics of intelligent systems.

**3.4.5*Responsible AI***

Responsible AI (RAI) is a governance framework covering both ethical and legal aspects. It contains many topics, e.g., explainability (i.e., XAI is part of RAI); fairness (see [Chapter 4](#chap4.xhtml)); reliability, safety or robustness; privacy or security; transparency; accountability, reproducibility, or monitorability; justifiability; efficiency; etc. RAI is human-centric so that the impact of the model’s outcome (e.g., prediction, recommendations, and decisions) can be reflected via user experiences (human-AI interaction) efficiently.

Practically, we shall always ensure that:

*   the design and implementation are documented and recorded in a diverse culture of coloration and support,
*   the data and model are measurable and accountable with high confidence and interpretable in human’s language, and
*   comprehensive testing for bias or fairness is implemented with AI security engineering, and more.

Although many tech giants such as Microsoft, Google, and IBM, have created or implemented their responsible AI framework, most FIs just started their journey. In 2019, Deutsche Bank, Standard Chartered Bank, and Visa with Linklaters and Microsoft formed a cross industry group to explore the application of RAI principles in financial services.^([5](#chap3.xhtml#rfn5)) HSBC and UOB joined the Monetary Authority of Singapore (MAS)’s Veritas project towards this purpose in 2020.^([6](#chap3.xhtml#rfn6)) Recently, MAS launched the inaugural Global Veritas Challenge to accelerate innovation on responsible AI solutions.^([7](#chap3.xhtml#rfn7))

**3.4.6*Sustainable AI***

The Sustainable Development Goals (SDGs) to be adapted by the United Nations (UN) by 2030 have 17 objectives, e.g., no poverty, zero hunger, good health and wellbeing, innovation and infrastructure, reduced inequalities, sustainable cities and communities, responsible consumption and production, peace, justice, and strong institutions, etc.^([8](#chap3.xhtml#rfn8))

AI can be an important tool for sustainable development, which transforms global productivity, efficiency, equality, and inclusion, and many other critical areas critical to the SDGs. AI projects can improve not only FIs’ prospects but all our futures, alleviating tensions between AI innovation, fair resource allocation, inter- and intra-generational justice, and, among environment, society and economy \[[7](#chap3.xhtml#rref7)\]. Sustainable AI solutions can strengthen FIs’ climate change strategies and contribute to more sustainable territories, such as green finance and carbon neutrality.

However, it is not easy to achieve the sustainable goal, as AI, in particular, some NLP pre-trained models (PTM) models are power-hungry by themselves. For example, training a single language translation model would emit a large amount of carbon which is roughly equivalent to 125 round-trip flights from New York to Beijing.^([9](#chap3.xhtml#rfn9)) To balance between energy efficiency and cost efficiency would be an aporia for both FIs and Cloud/AI service providers. “Sustainable AI”, in its infancy, ought to address the sustainability of the entire AI lifecycle, i.e., design, development (training, validation, re-tuning, etc.), and operation (e.g., monitoring and diagnosis of usage).

In sum, when FIs plan their Sustainable AI strategy, they must consider both “AI for sustainability” and “the sustainability of AI”. The former uses AI technology to achieve sustainability, e.g., SDGs, AI4Good, AI4climate, etc. The latter attempts to improve the energy efficiency of AI lifecycle and enhance the governance of AI applications to safeguard (e.g., privacy, security, transparency, accountability, fairness, and justice).

**3.5Challenges**

For any technology, if it cannot be commercialized on a large scale, its own value will be greatly reduced. The ultimate goal of applied AI technology is to reduce costs, increase efficiency, and improve user experience; otherwise, the development and adoption of AI technology will lose its purpose. This has gradually become the industry consensus.

AI techniques provide many promising applications in FIs. However, the adoption is not so smooth in many banks. In fact, in terms of commercialization, the difficulties in AI’s large-scale productionization can be summarized in [Table 3.4](#chap3.xhtml#tab3-4) along multiple dimensions of technology and scenic application.

Firstly, many AI techniques are not matured enough, or the performance may not be high enough to meet business requirements in reality. For example, many OCR engines have achieved high marks in some international competitions using their specific datasets. However, when they are applied to mixed printed and handwriting characters in reality, the accuracy may be lower than 95%, in particular, when it is applied to Chinese characters, which have much more patterns than Latin characters. So, when the business requires 99.9% accuracy for the check recognition, there is an obvious mismatch between the technology and the business demand. Even for the well-known facial and voice recognition, we may still encounter difficulty in some special cases. For example, during the new normal of living with the endemic COVID-19, facial recognition must be adopted with facial masks. As the normal facial recognition model can only achieve around 95% accuracy, the facial pattern must be re-designed and redeveloped with new data.

**Table 3.4.**Challenges for AI development and adoption

 
| **Category** || **Items** |
| --- | --- |
| Cognition and skills || 

*   Mysterious to the general public, which causes over-expectation or under-estimation
*   Skilled and experienced ML teams and roles, e.g., data scientist and ML engineer, despite active development of AutoML; close collaboration in complex projects
*   Mismatch between technology maturity/performance and business requirements

 |
| --- | --- |
| Data || 

*   Considerable data required to guarantee the model quality
*   Data privacy and ethical concerns, as well as AI-related data risks
*   Complexity added to the organization’s data integration strategy

 |
| Algorithm and Model || 

*   Model reusability due to data bias and algorithmic vulnerability
*   Large computing power for complex models, in particular, Deep Learning model, i.e., balance between model accuracy and computational cost
*   Influence of data variability and algorithmic bias to model reusability and explainability
*   General processing versus specific pattern

 |
| Infrastructure || 

*   ML frameworks: Who is dominated; why not AI-specific program language; the necessity of ML-specific complier
*   Interaction between algorithm and hardware: Unified software-hardware interface?
*   Large diversity in AI chip architectures: Convergence possibility and instruction set and complier
*   Ecosystem for AI

 |
| Regulation || 

*   Adulting and regulation difficulty in AI models
*   Balance between AI performance and risk

 |

All the examples above mean that the models developed using the current AI technology must have enough personalized or customized data for the specific scenarios before we can create realistic applications for that scenario. The lack of such data makes AI unable to perform “Deep Learning”. Therefore, cognitive non-routine tasks are still difficult to be fully automated via AI technologies. In other words, the technical problems brought about by data and algorithms have become the primary obstacle to the large-scale implementation of AI.

Secondly, from the infrastructure point of view, the modern DL, e.g., some NLP models, require huge computational resources and thus energy consumption. Although the growth of computing power is accelerating, the computing demands of DL are growing even faster. This motivated engineers to develop specific hardware accelerators for DL, e.g., Google’s tensor processing unit (TPU)^([10](#chap3.xhtml#rfn10)) and Intel’s Agilex FPGA.^([11](#chap3.xhtml#rfn11)) One promising technique may be Photonic \[[8](#chap3.xhtml#rref8)\], in which the author explained how a photonic chip can perform neural-network calculations and how light-based computing could reduce the energy needs for DL. Another one is the data infrastructure. Data islands still exist in FIs. When banks have a large volume of scattered data sources and the data is not well connected and organized, it is difficult for the banks to develop high-quality AI products. As suggested in [Chapter 1](#chap1.xhtml), a unified data analytical platform with reasonable scalability and capability is necessary.

Thirdly, AI risk exists not only in the procedure to generate the model but also with the model itself. The development and delivery procedure may contain some human errors, no matter whether it is done on purpose or not. For example, a retired engineer in the US was accused in 2019 for inserting a backdoor into his code, which generates errors periodically. So, the company had to pay the engineer a big amount of money every year to repair the system. Few “evil” developers with privileges may change the account via some AI programs such that they cannot be detected by internal simple rules. In other cases, the AI model may inherit some risks, if it is not fully properly evaluated. Many AI models are often considered as “black boxes”, in particular, the DL models usually have millions of parameters so that it is impossible to explain the output that can be understood easily.

To overcome the challenges and alleviate the AI risks as shown in [Figure 3.4](#chap3.xhtml#fig3-4), FIs may use systematic innovation of the whole organization to realize the benefits brought by the AI industry with overall considerations. Single-point technological innovation only solves the local issues, not the major propositions in the organization. A possible systematic approach may be as follows:

*   Form a clear AI strategy (e.g., AI first) and a data asset strategy with a solid technology core for the whole organization;
*   Build a unified data foundation (e.g., the data middle platform or data mesh) integrated with a technology pool;
*   Develop an AI-specific risk management and control framework with clear definition on AI or ML risks; assign dedicated staff for AI model validation, auditing, and management;
*   Establish a flexible and efficient AI development and operation framework, e.g., AI middle platform operated in MLOps (ML + DevOps; see [Chapter 14](#chap14.xhtml)) way, clear duties assigned for each role in terms of AI development and operation;
*   Make AI adoption more robust and democratic. For example, the automatic (assisted) programming technology or the automatic evolution technology using AI, might be adopted into the MLOps. The recent pilot project, Copilot, by OpenAI and Github, opens the door for automatic programming era.^([12](#chap3.xhtml#rfn12))

**3.6Trending Discussion**

It is no doubt that strong AI or general AI is still in the infant stage, and we must emancipate our minds and strive for “a wide variety of rare harvests.” For weak AI, we shall not hesitate to vigorously develop and promote it with more scenarios and integrate AI technology into the digital economy and smart society.

**3.6.1*MLOps versus AIOps***

MLOps and AIOps are two different concepts. The former applies DevOps (see [Chapter 12](#chap12.xhtml)) in ML lifecycle so that the whole lifecycle is easy to manage and deliver. However, the latter uses AI technology to enhance IT DevOps capability. See [Table 3.5](#chap3.xhtml#tab3-5) for a comparison. We will discuss MLOps in details in [Chapter 14](#chap14.xhtml).

AIOps platforms, according to Gartner, directly and indirectly improve IT operations (e.g., monitoring, maintenance, diagnosis, and service desk) via automation and intelligence with proactive, customized, and dynamic insight, derived from big data, modern ML, and other advanced analytics technologies,^([13](#chap3.xhtml#rfn13)) as shown in [Figure 3.6](#chap3.xhtml#fig3-6).

**Table 3.5.**MLOps versus AIOps

 
|  || **MLOps** || **AIOps** |
| --- | --- | --- |
| **Main duty** || Standardize ML lifecycle with a certain level of automation using DevOps || Automate IT operations and system using AI technology |
| --- | --- | --- |
| **Main benefits** || Increase team collaboration, efficiency and productivity; automate and reproduce ML experiments; mitigate ML risks and bias; etc. || Automate repetitive processes; perform anomaly detection, predictive operations and root cause analysis/resolution easily; conduct data-driven decision making; etc. |
| **Tools** || Azure ML, Amazon Sage Maker, Kubeflow, MLflow, DataRobot, Databricks || Splunk, IBM Watson AIOps, Servicenow, BMC Helix, AppDynamics, Dynatrace, Moogsoft |

![](images/p107.jpg)

**Figure 3.6.**AIOps technical stacks

Traditional IT is reactive, like a battle of zombie hordes. Only when a problem happens, we try to solve it. The best outcome expected is a final score of 0–0. AIOps is a proactive approach, which predicts several steps ahead, quickly comes up with the relevant insights, and then moves quickly to prevent similar problems and their spread, thereby achieving a powerful IT offensive.

Besides IT operations (possibly also under DevOps framework), AIOps can support the work of the service desk and information security teams along with both business leaders and operators.

The first level of AIOps is to simply detect anomaly and exceptions, group correlated events, and reduce the false alarms in the same time period by using the physical and software topology of the IT system and aggregating the alarms with AI techniques.

The next level is to apply causal analysis to find out the root cause of some system errors. Part of this functionality is provided in AIOps tools, e.g., BMC, Mogsoft and Splunk and ELK (ElasticSearch, Loghash, and Kabana). It is often implemented using statistical ML or graph computing. Multiple approaches can be implemented to view topological information and find out which nodes in the topology are most likely to have important events occurred. However, there is still a huge leap from causal analysis (find the root cause of an issue) to proactive diagnosis (fix the issue proactively), i.e., a gap between conceptual ideas and the actual effective implementation still exists in the near future. We shall set up a gradual plan with a reasonable entry target, while improving the capability of AIOps platforms. Other challenges when applying AIOps into the FIs include data regulation, cost consideration regarding ROI, too many legacy IT systems for AI to learn, etc.

According to Gartner, by 2023, AI will be used in around 30% of large enterprises for AIOps platforms and digital experience monitoring technology in their non-legacy IT estates. In particular, the COVID-19 pandemic has caused a much broader appreciation for the need for AIOps; more manual and routine work in IT operations will be replaced by automatic AIOps. With the advances of recent AI (e.g., NLP, causal inference, etc.), we can expect faster incident response, enhanced security, and preventative prognosis for remote and automatic IT operations.

Both AIOps and MLOps actually imply an important trend for AI engineering, which makes AI easier to be adopted in various domains and more convenient for end users.

**3.6.2*Low-Code or No-Code, and AutoML***

Low-code is usually a Graphical User Interface (GUI)-based programming/development approach with minimal human coding for the faster delivery of applications. No-code takes a step further, i.e., the development procedure has almost no coding by human at all.

Low-code or no-code platforms are usually built on the cloud architecture (e.g., AWS, Microsoft Azure, and GCP) with autoscaling resilience containerization like Kubernetes and Docker. Those platforms democratize to an extent for application development via enabling rapid solution building with close collaboration between the business and IT. Those platforms usually develop end-to-end enterprise-grade applications via a drag-and-drop interface based on a model-driven concept, which makes the customization and integration easily with the existing systems. By hiding the underlying complexities, e.g., AI model, database, UX, security, integrations, etc., from the citizen developers, the platforms can build and deliver “revolutionary” solutions much faster. Note that the underlying AutoML (automated ML) enables building high-quality AI models without in-depth data science knowledge. Thus, those platforms can stimulate AI innovation, enhance user experience, promote digital transformation progress, and bring more personalization into the applications.

When FIs consider adopting those platforms, some factors must be taken into account, e.g., cost and ROI (return on investment), infrastructure, developer resources, security, etc. The platform(s) must be integrated with the data platform with proper data pipelines so that high-quality data can be fed into it without pain. DevOps (MLOps) might be part of the platform so that it can deliver fast. Some typical platforms include Salesforce, Mendix, OutSystems, Microsoft Power App, Appian, ServiceNow, Google App Maker, etc. These platforms have been used in some applications of FIs. [Table 3.6](#chap3.xhtml#tab3-6) lists some examples.

As pointed out by Gartner, more than 65% of application development activity will be handled by low-code development by 2024 and its development technologies market size will be total $13.8 billion in 2021.^([14](#chap3.xhtml#rfn14))

**Table 3.6.**Applications using low- or no-code platforms

 
| **Banks** || **Solution provider** || **Application** |
| --- | --- | --- |
| Aviva (a UK-based MNC insurer) || Appian || Built a single customer view using data from 22 systems, resulting in more efficient call center operations.Customer service response time has increased by 9 times, and costs has been reduced by 40%. |
| --- | --- | --- |
| Bendigo Bank (one of the largest retail banks in Australia) || Appian || Transformed customer experience by develop and deploy 23 Tier-1 enterprise applications at a pace greater than one per month. |
| HSBC, Standard chartered banks, Development banks of Singapore, etc. || ServiceNow || Built their internal chatbot and service portal quickly. |
| Rabobank (a Dutch multinational bank) || Mendix || Developed its fully integrated online banking portal that manages 18 billion Euro for over 500,000 customers and achieved half IT cost saving. |

Note that those platforms may not be a fit for all cases. For example, some applications that have high security and compliance requirements may not find a proper out-of-the-box framework inside the platform. Some high-performance applications may also face challenges as the autogenerated code may not be efficient enough when compared with the customized code by the experienced developers. Considering the overall cost, the traditional development may cost more upfront, but the application is usually running independent from the platforms. Thus, the long-term cost of traditional development for scaling is lower. In addition, the wise usage of those platforms still needs the “expertise” of the platforms themselves, which means a learning curve is applied. In fact, even for common and “simple” software like Microsoft Office (Word, PowerPoint, Excel, Access), not many people actually master it for its advanced functionalities, e.g., micro, template, plug-ins, etc. As discussed in [Section 3.5](#chap3.xhtml#h3-5), a specific AI application often requires specific implementation, which is especially true for some NLP tasks, because the current AutoML technology is still not intelligent enough as AGI. The problem formulation and modeling, the relevant data processing, feature engineering, and model training/ fine-tuning to meet business multi-objectives are still hard for nonexperts to handle. Therefore, although AutoML and low- or zero-code platforms are one of the most important driving forces for AI democratization, it’s still a long way to achieve a realistic democratization.

**3.6.3*Pre-Trained Language Models***

The emergence of PTM has ushered in a new era of NLP \[[9](#chap3.xhtml#rref9)\]. From the first generation of word embedding (e.g., word2vec, fasttext) to the latest transformers (e.g., GPT and BERT), the PTMs are used in more and more areas, e.g., question and answer, sentiment analysis, text classification, NER, text summarization, etc. PTMs based on a huge text corpus can generally learn universal language representations for various downstream tasks. Starting from a PTM, the new model initialization is usually better than randomness and thus converge much faster after fine-tuning. Even trained on small dataset, a PTM can avoid overfitting to an extent. Recently, this “pre-train, fine-tune” mode is further developed as “pre-train, prompt, and predict” mode to use text prompt to reformulate downstream tasks.

The architecture of PTMs has been advanced from shallow to deep. Since the GPT and BERT, the PTM becomes bigger. OpenAI released unsupervised PTM model, GPT-3, in May 2020. This model contains 175 billion of parameters based on a data set of 45 terabyte, and broke many records in contextual query, text generation, machine comprehension, machine translation, etc. Google released their Switch transformer, the first trillion-parameter model, in January 2021, and LaMDA (Language Model for Dialogue Applications), the next generation of chatbot, and MUM (Multitask Unified Model), a new search engine, in May 2021. In June 2021, the Beijing Academy of AI (BAAI) published its model with 1,750 billion of parameters, the top in the world at that time.

Due to its difficulty and complexity in training and applying super-large PTMs, some researchers also seek ways to reduce the size using model compression techniques, e.g., parameter quantization/ binarization, network pruning, knowledge distillation, etc.

PTMs can be enhanced via knowledge-enriched model (embedded with domain knowledge), multilingual model and multi-modal model (text together with video, image, audio etc.) They are also extended to areas other than text, such as code (e.g., Copilot and Codex) and table (e.g., Tapex). Therefore, we can expect an even wider usage of PTMs.

With the financial specific corpus, the finance dedicated PTMs can be trained and then applied to multiple NLP tasks as mentioned earlier; FinBert^([15](#chap3.xhtml#rfn15)) is one of the examples.

**3.6.4*Integrated Data Platform for Analytics and AI***

From the database, data warehouse, to data lake and houselake, unifying internal data sources into a proper data storage and management system to explore the data value is always a hot topic inside FIs. With the wide use of edge sensing devices, how to unify the on-premise, Cloud, and edge data is even more challenging. FIs have adopted various digital solutions and platforms from different vendors. However, it is quite often that one solution or platform only solves one issue.

Therefore, the concept of platform of platforms appears to offer a “best-of-breed” solution. That strategy allows FIs assemble their existing solutions by integrating products from several different vendors, such as software, platform, hardware, and infrastructure. It leverages FIs’ existing IT decisions and investments, and allows FIs to focus on delivering the most valuable services and products. Data middle platform/office, which was originally used by Alibaba, is one of the applications in this area.

**3.6.5*Generative Synthetic Contents***

It is well-known that synthetic data can be used to enhance AI model quality. By the data augmentation techniques (e.g., geometric, color, space transformations, and kernel filter and random erasing or pruning for images, word, phrase, or sentence shuffling, and replacement for text, noise injection, and shifting in voice), the AI mode can adapt to more scenarios.

The synthetic content is more than that. With the advanced PTMs mentioned above, AI can help to write news, poems, novels, music pieces, code, etc. However, NLP is not the only AI area to generate synthetic content. Deepfake, a DL-based fake content generation technique, synthesizes images, videos, and voices that humans cannot discriminate, such as face-swapping, puppeteer (emulate facial or full-body actions and behaviors), voice cloning, lip-sync, human portrait synthesis, etc.

Generative Adversarial Networks (GANs) demonstrates remarkable feats in creating the fake arts, similar to transformers, which are the foundation of many NLP PTMs. Usually, GANs require large training sets. However, some recent developments dramatically reduced the data requirements with the data augmentation approach.

Synthesis techniques can also be widely used in the FIs. For example, the marketing email and call can be personalized, the notification and collection of service centers can be replaced by the AI bot. The virtual banking inside the Metaverse (see [Chapters 2](#chap2.xhtml) and [10](#chap10.xhtml)) may bring more vivid Avatars for better user experiences.

When they bring FIs benefits, they may also cause some ethical risks due to malicious uses, e.g., scams, fraud, political disinformation, forged identities, and more, which threaten psychological security, political stability, and business sustainability. FIs must defend the AI trust and secure it with proper countermeasures via enhanced AI techniques.

**3.6.6*Cybersecurity***

As cyberattacks become more technically sophisticated and targetdiverse, cybersecurity gains prominence recently. In fact, the number and types of cyberattacks have grown from year to year. According to a 2021 report from Experian, 55% of companies ranked security as their top priority.^([16](#chap3.xhtml#rfn16)) FIs will emphasize the fight against various risks such as data leakage, fraud, point of compromises, and money laundering during the digital transactions.

The anti-cybersecurity tools should be able to predict breaches ahead and eliminate them eventually. AI in the financial section allows you to discover vulnerabilities in the security system and explore potential solutions. It will be able to analyze account registration information, detect abnormal activities, and more. It is expected that AI can help solve many problems that people cannot solve manually. For example, AI can identify unknown threats via digging into tons of data to find threat patterns, increase the authentication level via background analysis of the users’ behavioral biometrics, respond to the abnormal transactions immediately to prevent some frauds, etc. The so-called cybersecurity mesh with centralized policy orchestration and distributed policy enforcement needs AI enablers to make it responsive and proactive. At the same time, AI models shall be robust enough to prevent adversarial attacks, and therefore, privacy-preserving computation and federated learning would be fused for this purpose. Analytics and modeling on highly sensitive data using confidential computations will be conducted inside the trusted execution environments.

**3.7Conclusion**

AI is revolutionizing the way FIs are using their data to obtain valuable insights, make prompt decisions, and automate some repetitive tasks. Popular AI applications range from algorithmic trading, fraud detection, AML, risk assessments, to virtual financial assistants in various business units, which make the BAU (business as usual) of FIs possible, especially when the COVID-19 pandemic devastates “normal” life. In fact, AI is being widely integrated into the client user interface/user experience (UI/UX), automated chat services, omni-channel marketing and customer support, anomaly detection, and security alarm. This not only enables bank staff to focus on solving more complex problems, but also helps customers get higher satisfaction. More generally, AI-disrupting technologies can significantly enhance the capability of FIs in profitability, efficiency, personalization, and innovation lifecycle.

However, due to the constraints on data and model (e.g., a variety of regulatory requirements, internal availability, and usability), ROI and cost, the actual ethical and explanation implementation, etc., the journey of an AI application is usually not so smooth. Nevertheless, the recent advances in AIOps, MLOps, low- or no-code platforms, PTM, explainable AI, sustainable AI, etc., may pave the way for wider and further adoption of AI in FIs technically. FIs are also encouraged to fully utilize the advances of FinTech-as-a-Service (FaaS) to get the AI capability quickly.

In sum, an AI-powered FI must have a full capability stack for its value creation. [Figure 3.7](#chap3.xhtml#fig3-7) presents an example for a modern bank, which has its stacks on methodology, data, core technology, AI capability and applications and innovative service experiences. The key is to build an agile, analytical and innovative culture inside the organization, integrate the platform of platforms for core data and core technologies, provide AI capability layer via FaaS and in-house development, and finally create the customer-centric layer to deliver high quality products and improve customer satisfaction.

![](images/p115.jpg)

**Figure 3.7.**Capability stack of an AI-powered bank

**References**

[1](#chap3.xhtml#ref1).S. Warnat-Herresthal, H. Schultze and *et al.,* “Swarm Learning for decentralized and confidential clinical machine learning,” *Nature,* Vol. 594, pp. 265–270, May 2021.

[2](#chap3.xhtml#ref2).Editorial, “Research Ideas for Artificial Intelligence in Auditing: The Formalization of Audit and Workforce Supplementation,” *Journal of Emerging Technologies in Accounting,* Vol. 13, No. 2, December 2016.

[3](#chap3.xhtml#ref3).G. A. Kaissis, M. R. Makowski, D. Rückert and R. F. Braren, “Secure, privacy-preserving and federated machine learning in medical imaging,” *Nature, Machine Intelligence,* pp. 305–311, June 2020.

[4](#chap3.xhtml#ref4).A. Adadi and M. Berrada, “Peeking Inside the Black-Box: A Survey on Explainable Artificial Intelligence (XAI),” *IEEE Access,* Vol. 6, pp. 52, 138–52,160, September 2018.

[5](#chap3.xhtml#ref5).K. H. R. Chan, Y. Yu, C. You, H. Qi, J. Wright and Y. Ma, “ReduNet: A White-box Deep Network from the Principle of Maximizing Rate Reduction,” [https://arxiv.org/abs/2105.10446](https://arxiv.org/abs/2105.10446), May 2021.

[6](#chap3.xhtml#ref6).M. Ford, *Architects of Intelligence: The truth about AI from the people building it,* Packt Publishing, 2018.

[7](#chap3.xhtml#ref7).A. van Wynsberghe, “Sustainable AI: AI for sustainability and the sustainability of AI,” *AI and Ethics,* February 2021.

[8](#chap3.xhtml#ref8).R. Hamerly, “The Future of Deep Learning is Photonic,” *IEEE Spectrum,* June 2021.

[9](#chap3.xhtml#ref9).X. Qiu, T. Sun, Y. Xu, Y. Shao, N. Dai and X. Huang, “Pre-trained models for natural language processing: A survey,” *Science China Technological Sciences,* No. 63, pp. 1,872–1,897, September 2020.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap3.xhtml#fn1)L. Goasduff. “2 Megatrends Dominate the Gartner Hype Cycle for Artificial Intelligence, 2020”. Gartner. [https://www.gartner.com/smarterwithgartner/2-megatrends-dominate-the-gartner-hype-cycle-for-artificial-intelligence-2020/](https://www.gartner.com/smarterwithgartner/2-megatrends-dominate-the-gartner-hype-cycle-for-artificial-intelligence-2020/), retrieved Nov 21, 2021.

[²](#chap3.xhtml#fn2)D. Morissey. “4 Principles of Responsible AI in financial services”. Microsoft Industry Blogs. [https://cloudblogs.microsoft.com/industry-blog/financial-services/2021/03/29/4-principles-of-responsible-ai-in-financial-services/](https://cloudblogs.microsoft.com/industry-blog/financial-services/2021/03/29/4-principles-of-responsible-ai-in-financial-services/), retrieved Nov 22, 2021.

[³](#chap3.xhtml#fn3)“Lime: Explaining the predictions of any machine learning disaster”. Github. [https://github.com/marcotcr/lime](https://github.com/marcotcr/lime). Accessed Nov 21, 2021.

[⁴](#chap3.xhtml#fn4)“A game theoretic approach to explain the output of any machine learning model”. Github. [https://github.com/slundberg/shap](https://github.com/slundberg/shap). Accessed Nov 21 2021.

[⁵](#chap3.xhtml#fn5)“From principles to practice: Use cases for implementing responsible artificial intelligence in financial services”. Linklaters. [https://www.linklaters.com/en/insights/publications/2019/november/from-principles-to-practice-use-cases-for-implementing-responsible-ai-in-financial-services](https://www.linklaters.com/en/insights/publications/2019/november/from-principles-to-practice-use-cases-for-implementing-responsible-ai-in-financial-services). Accessed Nov 21, 2021.

[⁶](#chap3.xhtml#fn6)‘“Fairness metrics’ to aid responsible AI adoption in financial services”. Monetary AuthorityofSingapore. [https://www.mas.gov.sg/news/media-releases/2020/fairness-metrics-to-aid-responsible-ai-adoption-in-financial-services](https://www.mas.gov.sg/news/media-releases/2020/fairness-metrics-to-aid-responsible-ai-adoption-in-financial-services). Accessed Nov 21, 2021.

[⁷](#chap3.xhtml#fn7)“MAS launches global challenge to accelerate innovation in responsible AI solutions”. Monetary Authority of Singapore. [https://www.mas.gov.sg/news/media-releases/2021/mas-launches-global-challenge-to-accelerate-innovation-in-responsible-ai-solutions](https://www.mas.gov.sg/news/media-releases/2021/mas-launches-global-challenge-to-accelerate-innovation-in-responsible-ai-solutions). Accessed Nov 21, 2021.

[⁸](#chap3.xhtml#fn8)The 17 goals, Department of Economic and Social Affairs, UN, [https://sdgs.un.org/goals](https://sdgs.un.org/goals). Accessed Nov 21, 2021.

[⁹](#chap3.xhtml#fn9)K. Crawford *et al.* AI Now: 2019 Report. The AI Now Institute. [https://ainowin-stitute.org/AI\_Now\_2019\_Report.pdf](https://ainowin-stitute.org/AI_Now_2019_Report.pdf). Accessed Nov 21, 2021.

[^(10)](#chap3.xhtml#fn10)“Cloud TPU: Train and run machine learning models faster than ever before”. Google Cloud. [https://cloud.google.com/tpu](https://cloud.google.com/tpu). Accessed Nov 21, 2021.

[^(11)](#chap3.xhtml#fn11)“FPGA vs. GPU for Deep learning”. Intel. [https://www.intel.com/content/www/us/en/artificial-intelligence/programmable/fpga-gpu.html](https://www.intel.com/content/www/us/en/artificial-intelligence/programmable/fpga-gpu.html). Accessed Nov 21, 2021.

[^(12)](#chap3.xhtml#fn12)“Your AI pair programmer”. Github. [https://copilot.github.com/](https://copilot.github.com/). Accessed Nov 21, 2021.

[^(13)](#chap3.xhtml#fn13)P. Prasad, P. Byrne, and J. Chessman. “Market Guide for AIOps Platforms”. Gartner Research. [https://www.gartner.com/en/documents/4000217/market-guide-for-aiops-platforms](https://www.gartner.com/en/documents/4000217/market-guide-for-aiops-platforms). Accessed Nov 21, 2021.

[^(14)](#chap3.xhtml#fn14)P. Vincent, K. Iijima, M. Driver, J. Wong, and Y. Natis. “Gartner Magic Quadrant for Enterprise Low-Code Application Platforms”. Gartner. [https://www.gartner.com/en/documents/3956079/magic-quadrant-for-enterprise-low-code-application-platf](https://www.gartner.com/en/documents/3956079/magic-quadrant-for-enterprise-low-code-application-platf). Accessed Nov 21, 2021; K. Costello and M. Rimol. “Gartner forecasts worldwide low-code development technologies market to grow 23% in 2021”. Gartner, [https://www.gartner.com/en/newsroom/press-releases/2021-02-15-gartner-forecasts-worldwide-low-code-development-technologies-market-to-grow-23-percent-in-2021](https://www.gartner.com/en/newsroom/press-releases/2021-02-15-gartner-forecasts-worldwide-low-code-development-technologies-market-to-grow-23-percent-in-2021). Accessed Nov 21, 2021.

[^(15)](#chap3.xhtml#fn15)“FinBert: Financial Bert (in Chinese)”. [https://github.com/valuesimplex/FinBERT](https://github.com/valuesimplex/FinBERT). Accessed Nov 21, 2021.

[^(16)](#chap3.xhtml#fn16)“2021 Global Identity and Fraud Report: Protecting and enabling customer engagements in the new digital era”. Experian. [https://www.experian.com.sg/wpcontent/uploads/2021/04/Experian-Global-Identity-Fraud-Report-2021.pdf](https://www.experian.com.sg/wpcontent/uploads/2021/04/Experian-Global-Identity-Fraud-Report-2021.pdf). Accessed Nov 21, 2021.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0004](https://doi.org/10.1142/9789811250903_0004)

Chapter 4

**AI Fairness in the Financial Industry: A Machine Learning Pipeline Approach**

***Jun Xu***

**4.1Introduction**

Artificial Intelligence (AI) technologies and Machine Learning (ML) algorithms have inspired a lot of excitements in our daily life, from smart television (TV), mobile phones, driver-less cars to the robot landing on Mars. In particular, with the creation, collection, and storage of “Big Data”, and dramatically concentrated computing power and storage capacity in large business and financial organizations, ML algorithms have demonstrated the power to identify non-intuitive and implicit correlations in massive datasets that human may not recognize. Thus, ML models have been widely adopted by financial institutions (FIs) as a means for decision-making processes, from high-frequency trading, cybersecurity, to various financial products and services.

In recent years, how to use AI properly has gained renewed popular interest. In fact, when AI brings tons of benefits, some applications making use of AI may generate harms to the human society if AI ethics, particularly AI fairness, is not carefully considered. For example, the Correctional Offender Management Profiling for Alternative Sanctions (COMPAS) software in the US has been proven to be biased against African Americans for the judicial systems.^([1](#chap4.xhtml#rfn1)) One of the hospitalization score models for healthcare systems favor certain racial groups \[[1](#chap4.xhtml#rref1)\].

In the financial industry, AI fairness also plays an important role. Decisions made by machines could impact a large group of user population for financial products and services, such as credit score and loan, and some level of biases inheritably exist. Some data collected from FI clients may be prone to bias and imbalance, for example, more male holders than female holders own world elite business credit cards. Such biases may also exist in chatbots, online advertisement and marketing champion, facial recognition, etc.

However, due to the black-box nature for most ML and Deep Learning (DL) algorithms, fairness of algorithm output becomes a serious concern, although it is expected to remove human prejudices from decision-making processes with the “fairness” of the machine! Therefore, many studies and experiments have been conducted to embed fairness into AI modeling.

This chapter proposes a practical framework for addressing the problems above. It starts with high-level conceptual prospects on AI ethics and fairness. Then, we develop a guidance on building a ML pipeline approach. Both connections and contradiction between ML and fairness concepts are intensively discussed. Examples are demonstrated on how to consider fairness in term of ML pipeline. The contribution of this chapter has three folds: (i) it summarizes the key points of AI fairness in FIs; (ii) introduces a ML pipeline approach to explain fairness treatment with structured representations in details; (iii) elaborates substantive workflow charts and checklists.

**4.2AI Ethics and Fairness**

AI ethics has been intensively discussed by many government organizations, e.g., the Monetary Authority of Singapore (MAS) proposed FEAT principles (i.e., fairness, ethics, accountability and transparency) and practices,^([2](#chap4.xhtml#rfn2)) the US Defense Department adopts five principles (i.e., responsible, equitable, traceable, reliable, and governable),^([3](#chap4.xhtml#rfn3)) the EU released ethics guidelines for trustworthy AI in 2018,^([4](#chap4.xhtml#rfn4)) and the Australian Government also released a version with eight rules.^([5](#chap4.xhtml#rfn5)) Other countries such as the China, the UK, and Australia also have released AI ethical guidelines. In [Figure 4.1](#chap4.xhtml#fig4-1), we suggest seven main characteristics.

![](images/p119.jpg)

**Figure 4.1.**Ethical AI

![](images/p120.jpg)

**Figure 4.2.**Bias types

To define fairness, various versions have been proposed \[[2](#chap4.xhtml#rref2)\]. Roughly speaking, fairness means “No Bias and No Discrimination”, i.e., people with similar properties should be treated similarly, otherwise they should be treated differently.

Some biases are inherited and unavoidable, but most are not; instead, they are just being simply misapplied or manipulated. [Figure 4.2](#chap4.xhtml#fig4-2) shows three common types of biases in a general sense, and we can avoid most of the cognitive and contextual biases if we are cautious.

Fairness in fact is closely related to other factors such as accuracy, privacy, explainability, and security ([Figure 4.3](#chap4.xhtml#fig4-3)). Fairness is usually in the same direction as explainability, but may not be with others in some scenarios, hence, we may need a trade-off in the design stage. For example, it is generally difficult for an AI system to achieve both high degrees of privacy and accuracy. Similarly, more privacy information can make fairness treatment more adjustable. Note that we need to take the application scenarios into consideration, as sometimes accuracy is more important and there are legitimate grounds for privacy and fairness. Sometimes, however, the fairness metrics must be satisfied at the expense of accuracy. Therefore, risk mitigation techniques are necessary for achieving the right balance between different metrics.

In AI and data-driven modeling, we usually use “protected” variables to indicates factors that may cause fairness issues, e.g., gender, age, race, citizenship, disability status, sexual orientation, religion, culture, theology, tradition, social class, resource availability, and ethnicity. The opposite is “unprotected” variables, which refers to public information available in the market.

![](images/p121.jpg)

**Figure 4.3.**Relations between fairness and other factors

Protected variables often implicate personal privacy, and its usage varies by the type of financial products. For example, personal income may be required in the case of credit card applications but not for general bank account openings. These protected variables can be further differentiated into privileged and unprivileged categories. For example, disabled persons and minority races are often considered as unprivileged categories.

AI ethics shall not be considered as a constraint on the Fl’s capabilities to increase profits for shareholders. In fact, AI ethical principles can be used as one of the key design criteria for innovative development, with the objective to improve wellbeing, reduce inequities and bias, and help people achieve their goals. For example, not lending to someone who is falsely predicted with a higher risk due to racial reasons is a reputational risk and also a missed opportunity. By removing such biases, FIs may attract more high-net-worth clients.

Therefore, FIs shall build their AI ethical framework. As pointed out by the Personal Data Protection Commission (PDPC) of Singapore,^([6](#chap4.xhtml#rfn6)) the model framework is intended to be broadly applicable — it shall be agnostic to algorithm, technology, sector, scale, and business model. The design for the fairness treatment in AI shall follow similar rules. Since ML pipeline can be applied in the most design and development process, we choose it as the main stem to discuss AI Fairness. In the next two sections, we will discuss the general ML pipeline first, and then present more details on the Fairness pipeline.

**4.3ML Pipeline**

The pipeline is a widely accepted concept and methodology in many industries. A product pipeline is a series of components to reduce the delay between completed tasks. It has a certain level of automation and increases the throughput in various stages of the product lifecycle. Pipelines usually contain batch processing, i.e., collecting data, sending it through a network, and processing it to provide pre-calculated results and guidance for next stages.

A ML pipeline is used to create a formal and automated ML workflows. It builds the necessary components and steps in the lifecycle of the data and model. For example, a data pipeline enables a sequence of data to be extracted, transformed, filtered, and cleaned before sending to a model for training, testing, and evaluation. A model pipeline also contains model deployment and maintenance. A ML lifecycle usually contains five stages, i.e., project design, data processing, model development, model/system deployment, and model maintenance as show in [Figure 4.4](#chap4.xhtml#fig4-4).

A common ML lifecycle pipeline is illustrated in [Figure 4.5](#chap4.xhtml#fig4-5). An abstracted concept of ML pipelines within the ML lifecycle is named as MLOps, which will be further discussed in [Chapter 14](#chap14.xhtml).

For a completed new project, its problem statement, scope, and objective must be clearly defined first by business stakeholders and SMEs. The development team studies its feasibility and provides potential solutions. Resource and cost shall be estimated before project starts. Once the project is formally set up, the access to various ML relevant resources, e.g., data, workbench, ML platform, and Cloud, shall be applied for approval. Then the raw data will be ingested from databases or other data sources, pre-processed and analyzed at Stage 1 before feeding into the ML development environment in Stage 2.

![](images/p123.jpg)

**Figure 4.4.**ML lifecycle in five stages

![](images/p124.jpg)

**Figure 4.5.**ML pipeline

ML development is generally an iterative procedure to enhance the features and improve models with proper evaluation metrics at Stage 2. The processed data and features can be stored in the Feature Store, an ML-specific feature management system. The relevant codes, configurations, and documentations will be stored in Git (a file version control and management system, e.g., Bitbucket or Github), and the model will be registered in the Model Inventory (or Model Registry) and accessed in Central Repository. ML developers may get the required tools and repositories from Central Repository (e.g., Artifactory, a universal artifact repository manager), and gain access to container images (e.g., packaged ML model and environments). Once all the necessary artifacts are ready, the model, which might be integrated into a system, will be deployed in different environments, e.g., the user acceptance testing (UAT) and staging for testing and validation. Non-satisfactory result of ML metrics may lead to a ML model re-train, i.e., go back from Stage 3 to Stage 2.

If all the tests are passed and the model/system is signed off by the right person, the model and system can be promoted into a formal production environment. Feature store can feed the live data into the ML model for real-time or batch inference. A proper monitoring and diagnosis configuration must be implemented for potential ML issues, e.g., model performance downgrade, data drift, etc., which might trigger a re-train event, with a proper process governance.

Note that it is not necessary that every project must have all the five stages or all the components indicated here. Sometimes, even the execution sequences in a pipeline can be different. A proper pipeline design shall depend on actual project requirements, not a fixed structure. More details will be discussed in [Chapter 14](#chap14.xhtml).

**4.4Fairness Pipeline**

Following the ML pipeline, we can create similar pipelines for fairness. [Figure 4.6](#chap4.xhtml#fig4-6) highlights a few questions to be asked at each stage, and [Table 4.1](#chap4.xhtml#tab4-1) highlights the key considerations for each stage.

A precondition to relieve bias is the proper definition and measurement of fairness during the product and service design phrases. For simplicity, we may divide them into three phases, i.e., before-, in-, and after-modeling, as shown in [Table 4.2](#chap4.xhtml#tab4-2), where each phase has its emphasis, i.e., data, model, and maintenance, respectively.

To evaluate the degree of fairness quantitatively, many metrics for data and model have been created. Data bias is often considered in its statistical properties, e.g., mean, maximum, minimum, distribution function, etc., while model bias needs more elegant algorithms to identify. [Figure 4.7](#chap4.xhtml#fig4-7) lists some commonly used metrics for (discrete) classification problem, including bi-class classification problems such as fraud/non-fraud, approval/non-approval, etc. For multiple-class problems, we may apply similar ML training techniques, such as One-versus-Many or One-versus-One approaches, to the metrics.

For continuous cases such as regression, bias metrics can be formulated around aggregate functions of the errors a model makes on different types of individuals (such as the mean squared/absolute (percentage) error, also known as MSE, MSPE, MAE, MAPE) or tests for the distribution similarity of these errors across subgroups. Continuous outcomes from a prediction increase the complexity in terms of fairness definition, taking into account the extent of the errors being made. For example, we shall choose the model between large errors on the minority group and relatively small errors on majority group.

![](images/p126.jpg)

**Figure 4.6.**General points for fairness pipeline in ML lifecycle

**Table 4.1.**Fairness pipeline considerations

 
| **Stage** || **Fairness consideration points** |
| --- | --- |
| Design || 

*   Task, scope, business sector, end-users
*   Stakeholders, product owner
*   Potential for errors and harm

 |
| --- | --- |
| Data || 

*   Data provenance, ETL compliance
*   Data representation, privacy, security
*   Data verification procedure via qualitative and experimental survey and other research
*   Data EDA for historical/presentation bias

 |
| Model || 

*   Feature engineering and selection readiness regarding protected data and unprivileged categories
*   Explainable mechanisms on model
*   Logic behind model making decision
*   Consistence between supporting evidence, human decision and machine decision
*   Twyman’s Law: The more unusual the result, the greater the likelihood of an error

 |
| Deployment || 

*   Proper auditing process
*   Ensure optimization and guardrail metrics in accordance with responsible practices and harm prevention

 |
| Maintenance || 

*   Identification and respond to failures and harms as they occur
*   Continuous monitoring, including feedback channel from end-users
*   Feedback loop for model adjustment

 |

**Table 4.2.**Key points around modeling

 
| **Before modeling/processing (main for data)** || **In modeling/processing (main for modeling)** || **After modeling/processing (main for deployment and maintenance)** |
| --- | --- | --- |
| Data quality (completeness, accuracy, etc.) || Model and feature selection || Performance and fairness testing and verification |
| --- | --- | --- |
| Data bias || Model fairness metrics || Auditing condition |
| Data fairness metrics || Model interpretability || Performance and fairness trigger |
| Protected features (privileged/unprivileged) || Model regularization for bias || Sensitivity analysis |
| Data preprocessing (fairness, supplement, etc.) || Model mitigation (tradeoff) || Maintenance policy |

![](images/p128.jpg)

**Figure 4.7.**Common fairness methods and metrics

Once the bias is detected, e.g., the fairness metrics do not satisfy some criteria, de-bias and risk mitigation procedures shall be applied. For example, during the model training, a trade-off between the business requirement, model performance, and fairness shall be carefully evaluated.

A human’s judgement within a proper framework is also a key factor to maintain a fair model, e.g., human expert’s decision system, auditing procedure, human-machine interaction, etc.

**4.4.1*Design***

The product/project designer, manager and owner shall consider the impact of fairness to the clients. Several general considerations are as follows \[[3](#chap4.xhtml#rref3)\]:

*   *Damage:* Will it harm the clients’ lives or destroy the company’s reputation? Is the price change for products or services affordable to our clients? Are the products or services favored by a specific group only?
*   *Scale:* Will the financial product or services change the lives of a large scale of population, e.g., the credit score model?
*   *Opaqueness:* Is the underlying assumption for the model clearly explained and validated? Will the model be created in a black-box? If the model’s decision-making process is questionable and hard to be understood, fairness is a likely concern.

**4.4.2*Data***

Data bias has many phenomena. Some examples include:

*   Data at scale of people’s past decisions are naturally socially biased, and models will learn that unfairness.
*   Data is dirty and often simply wrong.
*   Data at scale often encodes protected characteristics like race, ability, and health markers.
*   Restricted options, or menu-driven identity mistakes, create worthless or dirty data.
*   No ground truth to test our assumptions against Big Data is usually not Big Data for protected classes. Less data for the protected class means bigger error bars and worse predictions \[[4](#chap4.xhtml#rref4)\].

Sometimes, the bias is hidden in the available samples (observations). A famous example is the statistics of survived bombers in World War II. When engineers intended to find vulnerable parts of the bombers from those survived from the battle, they did not include the engine, which was counterintuitive. This is because those bombers with damaged engines rarely returned safely. Thus, it is improper to observe the “survival” data only. Similarly, when a model is built based on a majority population in FIs, it may have issues for minority groups, e.g., when a local bank mainly serves the locals, it may not properly process foreigners’ loan applications. In this sense, besides the consideration of known protected features as stated in [Section 4.3](#chap4.xhtml#h4-3), we shall also examine the unknown protected features.

In fact, some variables may be implied as protected variables. For example, demographic variables used for the modeling can often be applied in statistical approaches for bias. However, modelers turn to proxies that implicitly provide the same signals. Zip/postal code is one of those cases, which may have correlation with income and community; and further indicates wealth and class, and even race in some places.

To systematically measure data bias, we may consider both statistical properties and some distortions. Besides the general privacy and security of data properties (see [Table 4.3](#chap4.xhtml#tab4-3)), we shall also consider the factors listed in [Table 4.4](#chap4.xhtml#tab4-4), such as biases in population, behavioral activities, content, association, and temporal events. More specifically, we can further divide data bias into seven types as shown in [Table 4.5](#chap4.xhtml#tab4-5).

**Table 4.3.**Data privacy objectives \[[4](#chap4.xhtml#rref4)\]

 
| **Objective** || **Explanation** |
| --- | --- |
| Transparency || Consistence in understanding who can access it, what is the meaning of the data, how their data will be used, who the data is shared with, and how long it is held by a user, etc. |
| --- | --- |
| User-driven || Users’ full and granular access control of their own data wherever they share. |
| Anonymity || Non-disclosure of the identity of users via IoT applications. |
| Pseudonymity || A trade-off between anonymity and accountability. Actually, an individual’s actions are not associated with an identity; instead, they are related to a pseudonym, a random identifier. Pseudonymity could be used for multiple purposes including resolving privacy and accountability concerns in FIs. |
| Unlinkability || Degree of pseudonymity in the sense of unlinking specific actions from the same person, which might be used as a shield against profiling in FIs. |
| Unobservability || The ability that the third parties without permission cannot identify that a resource or service is being used by a person. It means that users and/or subjects cannot determine whether an operation is being carried out. |
| Decentralization || P2P sharing, i.e., each node directly shares its data with other nodes in the network, without interference of any third party or trusted entity. |

**Table 4.4.**Data considerations

 
| **Items** || **Questions** |
| --- | --- |
| Representation || Does the data set offer a balanced representation for all relevant groups? |
| --- | --- |
| Adequate Quantity || Is the data set large enough? |
| Reliability || How much confidence do you have in the accuracy of data? Does the set include noisy or badly labelled data? |
| Relevant features || Does the data set have relevant features for the purpose of processing? |
| Necessity || Are all the attributes in the data set necessary for the purpose of processing? |
| Impact || What is the impact of the algorithm on the rights and interests of data subjects? |

**Table 4.5.**Data bias types

 
| **Data bias type** || **Explanation** |
| --- | --- |
| Population bias || Target under-represented groups regarding the user population |
| --- | --- |
| Representation bias || Oversample from minority groupsPrevention of misclassification of “outliers” treated by models requires sufficient data from each group |
| Aggregation bias || False assumptions about a population |
| Augmentation bias || Data synthetization for minority groups |
| Sampling bias || Skewed sample, e.g., initial bias that compounds over timeTainted examples, e.g., bias in the data caused by humansSample size disparity, e.g., minority groups not as well represented |
| Linking and labelling bias || Link attributes to the raw data; often seen in classificationLimited features, e.g., less informative data collected on minority groupsProxies, e.g., data implicitly encoding sensitive attributes |
| Temporal bias || Difference in populations and behaviors over time |

**4.4.3*Model***

Once data bias is removed or mitigated, the AI/ML models will be built or trained to predict the designed targets. [Figure 4.8](#chap4.xhtml#fig4-8) illustrates the general concepts during the modeling, where the left side shows the common steps for users’ involvement in fairness application, and the right side selects some common rules in the loop with their questions and duties. As the models can be a grey box or black box, we usually apply XAI techniques to the models.

![](images/p132.jpg)

**Figure 4.8.**Model fairness concept

**Explainable AI (XAI)**

Model explainability is essential for achieving model transparency, accountability, and fairness. Usually, there are two categories \[[5](#chap4.xhtml#rref5)\]:

*   Category 1: Design and generate an interpretable AI model, which is usually intrinsic. 
    *   Some models are self-explainable, e.g., logistic regression, decision trees, decision lists and sets, generalized additive models (GAMs).
*   Category 2: Post-hoc interpretation of an AI model, which is model-agnostic. 
    *   Local explanations attempt to interpret how the model predicts for a given instant, in terms of input features, influential examples, local feature importance, local decision rules, etc.
    *   Global explanations of the entire model usually try to interpret the overall questions, such as how the model predicts and how the dataset impacts decision-making. It can apply the terms, such as partial dependence plots, global feature importance, global decision rules, in a sense of “average” generally.

By improving transparency and trust of models, XAI can be used to improve the understanding of model bias and fairness \[[5](#chap4.xhtml#rref5)\]. For example, the feature importance of protected features gives a direct illustration for model fairness, e.g., if the importance index for the protected features, such as age and gender, is very small, it means the model is insensitive to the protected features, and thus usually fair.

**Training**

Although the model performance is usually the first priority during the training procedure for data scientists, some businesses may require additional constraints, e.g., profit, into the objectives, which sometimes contradict the fairness metrics. Three main approaches are used to leverage it. One is to embed the fairness metrics (see [Table 4.6](#chap4.xhtml#tab4-6)) into the objective function directly, i.e., either use an optimization target or a constraint variable. The second is the risk mitigation approach (see [Section 4.4.6](#chap4.xhtml#h4-4-6) for more details). The third is a 2-step model selection approach, e.g., iteratively optimize the two objectives of performance and fairness.

To properly select a fair model, we may consider the following options:

**Table 4.6.**Fairness metrics

 
| **Type** || **Fairness metrics** |
| --- | --- |
| Before-modeling (data) || Fair data distributionStatistical parity difference |
| --- | --- |
| In-modeling (training, testing) || Disparate impact Statistical parity difference Average odds difference Equal opportunity difference Benefit–harm rate |
| After-modeling (deployment, maintenance) || Long-term disparate impact Benefit-harm rate |

*   Calculate the equitability from multiple models that have similar performance along overall evaluation metrics of interest (with a reasonable threshold), and then select the one with the best fairness index; also applicable for several equity metrics consideration at the same time
*   Plot a trade-off curve between the performance and fairness index. Understand how much “cost” in terms of performance to be taken to reach various levels of fairness
*   If fairness across multiple subgroups (e.g., several race/ethnicity/region categories, multiple age groups, etc.) is more concerned, explore the best performed models for each subgroup in addition to those perform similarly across groups. Note that different thresholds may be applied across groups to achieve more equitable results.

**Testing and validation**

The key of testing step is to make sure the “Differential Validity of Test Scores for Sub-Groups”. Some general test methods are as follows:

*   Targeted tests are generally domain specific (e.g., image, language, etc.)
*   A/B tests can be performed quickly throughout the development cycle.
*   Comprehensive tests are used to valid the result ecologically using real-world data.
*   Differential tests target at finding the model bugs via various “cheating” techniques.
*   Adversarial tests attempt to find poisonous needles.

**4.4.4*Deployment***

One potential bias in this stage is how the model or its prediction might be applied in practice. For example, the model may be deployed by a different population from the training dataset. Before the official deployment into production, we shall audit the model’s prediction results. For example, in a classification application (e.g., loan/credit card approval), given the labeled results for existing or new processes, bias detection and identification tools can be applied to determine whether that process is generating fair outcomes. The procedures may not require the ML model to be involved directly, as some fairness metrics can be obtained for any set of decisions and outcomes, no matter whether the decisions are derived from a ML model, a heuristic rule, or other processes.

**4.4.5*Maintenance***

Some detector and trigger mechanism to update (e.g., retrain the model), adjust (e.g., revise the output policy), or stop (e.g., decommission) the models shall be implemented for the data and model drift events, e.g.,

*   Feature drift (independent drift), i.e., the change of properties of independent data, such as population statistical property change
*   Label drift (prior probability drift), i.e., the change of properties of target data
*   Concept drift, i.e., the shift in the relationship between independent and target data
*   Prediction drift i.e., change the prediction performance downgrade
*   Fairness metric index downgrade

One ethical decision here is if these triggers can be executed automatically without a human’s review as it does during the development iteration. Different from technology companies such as Alibaba, Jingdong, and Pinduoduo, which use a continuous deliver (CD) pipeline to frequently update their recommendation models, FIs under strict governance may require more human involvements.

**4.4.6*Bias/Risk Mitigation***

As mentioned earlier, the metrics described in [Table 4.6](#chap4.xhtml#tab4-6) and [Figure 4.7](#chap4.xhtml#fig4-7) can be considered in a variety of aspects — auditing existing models and processes for fair results, choosing a proper model to deploy, making a decision about how a chosen model is put into production, or mitigating the risk using some techniques.

Bias mitigation algorithms are aimed at improving fairness by modifying the dataset, the training algorithms, and/or the prediction process. [Table 4.7](#chap4.xhtml#tab4-7) lists some existing techniques and algorithms for risk mitigation in different stages of ML \[[6](#chap4.xhtml#rref6), [7](#chap4.xhtml#rref7)\]. For example, the pre-processing methods generally re-weight, reselect, or modify classes. In-processing methods often add more regularization/loss function constraints and make the model adaptive to the protected variable changes. Post-processing methods adjust confidence or probability score corrections, promote or demote boundary decisions, and build a wrapper on top of the traditional classifiers.

**Table 4.7.**Risk mitigation \[[6](#chap4.xhtml#rref6)\]

![](images/p136.jpg)

**4.4.7*Humans in the AI Lifecycle***

Although one objective of the AI techniques is automation and partially replacing a human’s repetitive work processes, a human is often required to be involved in the whole ML lifecycle, i.e., the human in the loop (HIL). In fact, in many situations \[[8](#chap4.xhtml#rref8)\]:

*   Humans can distinguish the interaction between an AI system and a human.
*   Humans may discern the decision made by an AI system or a human based on their reasoning.
*   AI can make improvements regularly to meet humans’ requirements and technical standards.

As illustrated in [Figure 4.8](#chap4.xhtml#fig4-8), the human in various roles, e.g., product designer, product manager, project manager, data scientist, ML engineer, IT architect, system administrator, auditor, etc., (see [Chapter 14](#chap14.xhtml) for more details) is involved in the whole lifecycle of the AI models. When the human correct one bias, they may bring other biases into the models at the same time. Some proper standards and guidance shall be set up by a formal organization inside the organization. [Figure 4.9](#chap4.xhtml#fig4-9) proposes a framework for AI ethics and fairness governance.

![](images/p138.jpg)

**Figure 4.9.**Suggested AI fairness governance

**4.5Case Study on Marketing Champions**

This section provides an example to illustrate how the framework is applied to real financial applications. A marketing campaign is any action planned for achieving a marketing goal for a company, focusing on customer needs and their overall satisfaction. The goal could be increasing awareness or sales for a product, service, and business, or other purposes. It generally considers four aspects: (i) product with its population segmentation, i.e., the targeted customers; (ii) distribution channel (omni-channel) to reach the customers, e.g., telephones, radio, TV, social media, mail, customer referrals, etc.; (iii) price, e.g., the best offer with a balance between customers’ acceptance and profitability; (iv) promotion strategy, i.e., a proper way to make the marketing campaign more effective. AI or ML techniques can help to connect customers to the right products and/or services, predict the policy customers may choose, forecast sales, and thus adjust targets, etc.

**Problem Statement**

Telecommunication is still one of the main approaches for FIs to engage new customers. Here, we use an open data set of UC Irvine Machine Learning Repository^([7](#chap4.xhtml#rfn7)) and Kaggle,^([8](#chap4.xhtml#rfn8)) which is from a Portuguese banking institution for its direct marketing campaigns using phone calls. The bank staff often called more than once to the same client, in order to assess if the bank term deposit would be subscribed \[[9](#chap4.xhtml#rref9)\]. A term deposit is a deposit that a FI offers with a fixed rate in which your money will be returned at a specific maturity time.

Some protected attributes are used, i.e., age, job, marital status, and education. Other variables include credit default, housing, loan and account balance, contact type, contact time (month, day, duration), campaign times, etc. The outcome is denoted as “yes” (subscribed) or “no”.

**Basic analysis**

The dataset contains 11,162 records, and distributions on the protected variables are obviously uneven ([Figure 4.10](#chap4.xhtml#fig4-10)).

By using the pair plot, we can find the relation between the selected protected variables and the other variables. [Figure 4.11](#chap4.xhtml#fig4-11) shows an example for marital status with relation to others. If we consider the pair of “age” and “balance”, we may find the “divorced” persons may have a smaller balance amount than other statuses. [Figure 4.12](#chap4.xhtml#fig4-12) illustrates the correlation matrix of variables. It is obvious that “age” has high correlation with “marital”.

“pdays” is relatively highly corrected to “previous”, as if it is not contacted before, it is highly likely to be contacted. A further exploratory data analysis (EDA) shows that the youngest category had a 71% chance for subscribing to a term deposit while the eldest category had a 77% chance (see [Figure 4.13](#chap4.xhtml#fig4-13)). It implies that the model may lean towards the youngest and eldest categories. Another observation is the “job” attribute; considering age, the potential clients who were students or retired had the most likelihood to a term deposit subscription. Retirees tend to have more term deposits so that they gain some interest payments of cash.

![](images/p140.jpg)

**Figure 4.10.**Distribution of protected variables

Now we use classifiers to consider the impact of features to “deposit”. Instead of simple categorical values, we define the so-called one-hot coding for them, and use the string of categorical value as the column name’s extension. For example, “marital” has three statuses, so we get three one-hot coding for it — “marital\_divorced”, “marital\_married”, and “marital\_single”.

![](images/p141.jpg)

**Figure 4.11.**Pair plot of marketing data

For different ML classifiers with a cross-validation approach, we may use area under curve (AUC) of receive operating characteristics (ROC) as their main performance metric, for example:

*   Gradient Boost Classifier: 0.92
*   Neural Classifier: 0.92
*   Random Forest: 0.92
*   Naives Bayes Classifier: 0.81

With the aid of SHAP, we get the Shapley value for Random Forest as show in [Figure 4.14](#chap4.xhtml#fig4-14). We can see that the variable “age” has a relatively large impact to the outcome, although its average value (0.025) is small. However, other three protected variables have almost no impact to the outcome. Therefore, we may say the ML model is relatively insensitive to the protected variables of “marital”, “job”, and “education”.

![](images/p142.jpg)

**Figure 4.12.**Correlation matrix of marketing data

![](images/p142-1.jpg)

**Figure 4.13.**Impact of age

![](images/p143.jpg)

**Figure 4.14.**Shapley value for feature importance

**Debias processing**

As illustrated in [Figure 4.12](#chap4.xhtml#fig4-12), the protected variable “age” is sensitive to the model prediction, which is also shown in [Figure 4.15(a)](#chap4.xhtml#fig4-15). We may use the methods introduced in [Section 5.5](#chap5.xhtml#h5-5) to alleviate the pain of bias. For simplicity, we divide the age into two groups: G1 is between 25 and 60 years old, while G2 is out of this range. Based on the observation of [Figure 4.12](#chap4.xhtml#fig4-12), we set G2 is the privilege group. Here, we applied the re-weighting approach of pre-processing category, the adversarial debiasing approach of in-processing category, and reject option classification of post-processing category to migrate the bias.

![](images/p144.jpg)

![](images/p145.jpg)

**Figure 4.15.**Fairness metrics value changes after processing

![](images/p146.jpg)

**Figure 4.16.**ROC comparison

We can see from [Figures 4.15(a)](#chap4.xhtml#fig4-15) to [4.15(d)](#chap4.xhtml#fig4-15) that the bias is generally reduced for almost all metrics, in particular, the parity difference and disparate impact.

Note that the general performance (e.g., AUC) is not largely impacted by the debias algorithms in this case, as shown in [Figure 4.16](#chap4.xhtml#fig4-16).

**4.6Related works**

AI has been widely adopted in FIs, as discussed in [Chapter 3](#chap3.xhtml). For example, \[[10](#chap4.xhtml#rref10)\] conducts a survey on DL for financial applications, where the works according to the intended finance subfields are categorized and analyzed based on their DL models. \[[11](#chap4.xhtml#rref11)\] summarizes the ML methods and applications on credit risk.

AI ethics, as an important consideration for AI adoption, has been intensively discussed, e.g., \[[12](#chap4.xhtml#rref12)–[14](#chap4.xhtml#rref14)\]. \[[12](#chap4.xhtml#rref12)\] seems to be the first dedicated book to discuss AI fairness with many technical details. \[[14](#chap4.xhtml#rref14)\] gives a comprehensive survey on AI ethics with a taxonomy to analyze the literatures. \[[13](#chap4.xhtml#rref13)\] focuses on bias and fairness for various aspects with consideration of some ML techniques, e.g., variational auto encoder, adversarial learning, etc. \[[15](#chap4.xhtml#rref15)\] provides a broad multidisciplinary overview for AI system bias, concentrating on technical challenges, solutions, and new research direction suggestions towards approaches well-grounded in a legal frame. \[[6](#chap4.xhtml#rref6)\] uses an empirical study to illustrate how explainability can help fairness judgement. \[[16](#chap4.xhtml#rref16)\] attempts to explore various families of AI fairness solutions for their pro and con comparison. \[[17](#chap4.xhtml#rref17)\] gave a survey on fair and responsible ML/AI to the consumer financial services. It explained the bias in term of social contexts and structural inequalities. \[[18](#chap4.xhtml#rref18)\] uses explainable ML to discuss the fairness in a sense. \[[19](#chap4.xhtml#rref19)\] briefly discussed the challenges and solutions on modelling financial data, and provided an example of default credit card as illustration.

All these papers have not explicitly shown the workflow of ML pipeline and its application to fairness pipeline. However, we do notice that some keynotes and tutorials at various AI conferences also provide in-depth solutions and address ML pipeline, e.g., \[[20](#chap4.xhtml#rref20)–[22](#chap4.xhtml#rref22)\]. However, there is no detailed workflow presented like in this chapter.

Besides the government- and organization-level frameworks and guidance as discussed in [Section 4.2](#chap4.xhtml#h4-2), some consulting firms also contribute their insights in this area, e.g., McKinsey suggested 6 potential ways forward for AI practitioners and business or policy leaders to consider.^([9](#chap4.xhtml#rfn9)) Most of the major AI-related companies, such as Facebook, Amazon, Google, IBM, Microsoft, etc., announced their AI principles, and open-sourced AI fairness evaluation and mitigation tools (see [Table 4.9](#chap4.xhtml#tab4-9) in [Appendix 4.1](#chap4.xhtml#h4-8)). Many renowned universities, e.g., New York University, MIT, Harvard University, Stanford University, Fudan University, etc., published white papers on AI ethics and fairness. Some AI professional organizations have also formed to provide guidance and supervision. For instance, “Partnership on AI” initialized by Facebook, Amazon, Google, IBM, Microsoft, etc., brings together diverse, global voices to realize the promise of AI.^([10](#chap4.xhtml#rfn10))

**4.7Conclusion**

Many research and development works have been conducted on AI ethics and fairness. This chapter uses a ML pipeline approach and attempts to link it with a unified framework. A detailed workflow is illustrated in [Figure 4.17](#chap4.xhtml#fig4-17). We also present a checklist which is similar to \[[23](#chap4.xhtml#rref23)\], but in the structure of the ML pipeline.

We shall note that bias or discrimination is not an abstract concept. Instead, it is usually domain- and application-specific, as it very likely impacts people’s daily life dramatically. It is also feature- and framework-specific, since it is highly relevant with socially salient qualities that have underpinned unjustness and systematically adverse treatment during the past.

Although we discuss numerous exciting works in this chapter, we are still facing many challenges on AI fairness, for example:

*   *Framework-specific issues.* We generally lack standards, tools, or interfaces (e.g., API) for general ML models, which leads to the difficulty in pluggable fairness explanation. In addition, integrating the fairness pipelines data, model, and application into a single framework is always not easy.
*   *Application-specific issues.* Different fairness criteria actually depend on users’ requirement and problem specification, which is difficult to normalize. In addition, AI explainability of the algorithms depends on various aspects, such as the use case, model type, data property, etc.
*   *Trade-off issues.* Users’ requirements shall be balanced along various dimensions. First, consider the balanced objectives among explainability, accountability, performance, auditability, fairness, and privacy. For example, how to balance harm and benefit, how to identify long-term harms, how to migrate harms and misbehaviors quickly, and how to improve robustness and explainability to failure modes (interaction between ML components). Second, decide the relationships between different people and machines. For example, we need to consider the dependency from the perspectives of model developers, business stakeholders, and end users. We shall have a proper human interference (HIL) within the pipeline and automation.

![](images/p149.jpg)

**Figure 4.17.**AI fairness workflow

We present a checklist of AI fairness in [Table 4.8](#chap4.xhtml#tab4-8) \[[2](#chap4.xhtml#rref2), [8](#chap4.xhtml#rref8), [12](#chap4.xhtml#rref12), [20](#chap4.xhtml#rref20), [23](#chap4.xhtml#rref23), [24](#chap4.xhtml#rref24)\].

**Table 4.8.**Checklist for AI fairness

 
| **Stage** || **Items** |
| --- | --- |
| Design || 

*   How much needs to be considered from outside an organization when claiming that a system is fair?
*   What is the targeted usage of output for the service and product? Who is the audience in general and who is the most impacted group?
*   If the designated humans have the ultimate responsibility for all decisions and outcomes, e.g., explicitly defined between the AI system and human(s), and how they are shared; final decisions that affect a person’s life, quality of life, health, or reputation.
*   Are humans always able to monitor, control, and deactivate systems? Who is the person in charge for model quality and risk control?
*   Will the significant decisions made by the AI system be explained, overridable, appealable and reversible?
*   Are the purpose, limitations, and biases of the AI system explained in plain language?

 |
| --- | --- |
| Data || 

*   Are there missing values for a large number of observations?
*   Are there missing features that might impact the output and/or affect other features?
*   Are there any unexpected feature values, which might be considered as outliers?
*   Is the training dataset sufficient for diversity and reliability? Is there only necessary data collected, e.g., respecting privacy and data rights
*   Are there any understandable security methods for data?
*   Which datasets was the service trained and tested on? (Provide links to datasets that were used for testing, along with corresponding datasheets)
*   Was the dataset checked for bias used by the service? What types of statistical data skew observed?
*   What is the data lifecycle from data ingestion to the model serving?
*   What efforts were made to ensure that it is fairly representative?

 |
| **Model** || 

*   Do we need new laws (not disparate impact/treatment) to address these systems?
*   Is automated decision making ethically different than human decision making?
*   Can there be unfair models for reasons other than group differences?
*   Should we study fairness *with* privacy, security, transparency…or not?
*   Is data or model the cause of bias in ML decisions? What are the potential worst scenarios of the model output?
*   What algorithms or techniques is this mode applied with?
*   Are testing methodology and test results clearly explained?
*   Are the service outcomes or model outputs explainable and/or interpretable?
*   Does the service have any mechanism for bias detection and remediation?
*   Does the service have any expectation or implement any mechanism to handle unseen data or data with different distributions?

 |
| Deployment and Maintenance || 

*   Is the service robust enough against adversarial attacks?
*   How frequent is the model updated and when were the its last updated?
*   Is the updated automatically or manually (who is the approver)?
*   Is there any feedback on bias, ethical or other risks issues when using the service?
*   Are the straightforward and interpretable monitoring systems are provided?
*   Is there a regular policy defined for model improvements to meet human needs and technical standards? Any model retain and model decommission policies?
*   Is the AI system robust, valid, and reliable?

 |
| Governance || 

*   Do we identify the full range of risks (harmful, malicious use and consequences) and benefits (good, beneficial use and consequences)?
*   Is there any plan for the misuse/abuse of the AI system, including the communication plans to share pertinent information with all affected people, and the mitigation plans for managing the identified speculative risks?
*   Is there a proper pipeline to make sure that the data, algorithms and models are appropriate and verifiable? Are the overall procedures properly reviewed and approved?
*   Are confidence and context presented for humans to make proper decisions?
*   Is transparent justification for recommendations and outcomes provided?

 |

**4.8Appendix 4.1: Fairness Tools**

There are many tools available in the markets, and many of them are open sourced. [Table 4.9](#chap4.xhtml#tab4-9) lists some relatively matured tools, mainly from Github.

**Table 4.9.**Some open-source tools

 
| **Name** || **Functionality** || **Github** |
| --- | --- | --- |
| Fairness Measures || Framework to test given algorithm on variety of datasets and fairness metrics. || [https://github.com/megantosh/fairness\_measures\_code](https://github.com/megantosh/fairness_measures_code) |
| --- | --- | --- |
| Fairness Comparison || Extensible test-bed to facilitate direct comparisons of algorithms with respect to fairness measures. Includes raw and pre-processed datasets. || [https://github.com/algofairness/fairness-comparison](https://github.com/algofairness/fairness-comparison) |
| Themis-ML || Python library built on scikit-learn that implements fairness-aware ML algorithms. || [https://github.com/cosmicBboy/themisml](https://github.com/cosmicBboy/themisml) |
| FairML || Looks at significance of model inputs to quantify prediction dependence on inputs || [https://github.com/adebayoj/fairml](https://github.com/adebayoj/fairml) |
| Aequitas || Web audit tool as well as Python library. Generates bias report for given model and dataset. || [https://github.com/dssg/aequitas](https://github.com/dssg/aequitas) |
| Fairtest || Tests for associations between algorithm outputs and protected populations. || [https://github.com/columbia/fairtest](https://github.com/columbia/fairtest) |
| Themis || Takes a black-box decision-making procedure and designs test cases automatically to explore where the procedure might be exhibiting group-based or causal discrimination. || [https://github.com/LASER-UMASS/Themis](https://github.com/LASER-UMASS/Themis) |
| Audit-AI || Python library built on top of scikit-learn with various statistical tests for classification and regression tasks. || [https://github.com/pymetrics/audit-ai](https://github.com/pymetrics/audit-ai) |
| AIF360 || Comprehensive bias metrics and mitigation toolbox (including unique algorithms from IBM Research). || [https://github.com/ibm/aif360](https://github.com/ibm/aif360) |
| Interpret ML || Fit interpretable models. Explain black-box machine learning. || [https://github.com/interpretml](https://github.com/interpretml) |
| fairlearn || Assess and improve fairness of machine learning model. || [https://fairlearn.github.io/](https://fairlearn.github.io/) |
| fairness indicators || Evaluating, improving, and comparing models for fairness concerns in partnership with the broader Tensor flow toolkit. || [https://github.com/tensorflow/fairness-indicators](https://github.com/tensorflow/fairness-indicators) |

**References**

[1](#chap4.xhtml#ref1).T. Grote and B. Philipp, “On the ethics of algorithmic decision-making in healthcare,” *Journal of Medical Ethics,* Vol. 46, No. 3, November 2020.

[2](#chap4.xhtml#ref2).N. Arvind, “Tutorial: 21 fairness definition and their politics,” ACM FAT (Fairness, Accountability and Transparency) Conference, 2018.

[3](#chap4.xhtml#ref3).C. O’Neil, “Weapon of mass destruction,” Broadway Books, 2016.

[4](#chap4.xhtml#ref4).A. Ouaddah, A. A. Elkalam and A. A. Ouahman, “FairAccess: A new blockchain-based access control framework for the internet of things,” *Security and Communication Networks,* Vol. 18, No. 9, pp. 5,943–5,964, February 2017.

[5](#chap4.xhtml#ref5).A. Das and P. Rad, “Opportunities and Challenges in Explainable Artificial Intelligence (XAI): A Survey,” arXiv:2006.11371, 2020.

[6](#chap4.xhtml#ref6).J. Dodge, V. Q. Liao, Y. Zhang, R. K. Bellamy and C. Dugan, “Explaining models: An empirical study of how explanations impact fairness judgment,” in *ACM International Conference on Intelligent User Interfaces,* 2019.

[7](#chap4.xhtml#ref7).R. K. E. Bellamy *et al.,* “AI fairness 360: An extensible toolkit for detecting, understanding, and mitigating unwanted algorithmic bias,” [https://arxiv.org/abs/1810.01943](https://arxiv.org/abs/1810.01943), 2018.

[8](#chap4.xhtml#ref8).E. Wall, L. M. Blaha, L. Franklin and A. Endert, “Warning, bias may occur: A proposed approach to detecting cognitive,” in *IEEE Conference on Visual Analytics Science and Technology (VAST),* 2017.

[9](#chap4.xhtml#ref9).S. Moro, P. Cortez and P. Rita, “A data-driven approach to predict the success of bank telemarketing,” *Decision Support Systems,* Vol. 62, pp. 22–31, June, 2014.

[10](#chap4.xhtml#ref10).A. M. Ozbayoglu, M. U. Gudelek and O. B. Sezer, “Deep learning for financial applications: A survey,” *arXiv:2002.05786,* 2020.

[11](#chap4.xhtml#ref11).J. L. Breeden, “A survey of machine learning in credit risk,” SSRN, May 2020.

[12](#chap4.xhtml#ref12).S. Barocas, M. Hardt and N. Arvind, *Fairness in Machine Learning: Limitations and Opportunities,* [fairmlbook.org](http://www.fairmlbook.org), 2019.

[13](#chap4.xhtml#ref13).N. Mehrabi, F. Morstatter, N. Saxena, K. Lerman and A. Galstyan, “A survey on bias and fairness in machine learning,” arXiv:1908.09635, 2019.

[14](#chap4.xhtml#ref14).S. Tolmeijer, M. Kneer, C. Sarasua, M. Christen and A. Bernstein, “Implementations in machine ethics: A survey,” arXiv:2001.07573, 2020.

[15](#chap4.xhtml#ref15).E. Ntoutsi *et al.,* “Bias in data-driven artificial intelligence systems — An introductory survey,” *WIREs Data Mining Knowledge Discovery,* February, 2020.

[16](#chap4.xhtml#ref16).I. Akbari, “On fair representation in machine learning,” DOI: 10.13140/RG.2.2.28800.66565, 2020.

[17](#chap4.xhtml#ref17).S. C. Rea, “A survey of fair and responsible machine learning and artificial intelligence: Implications for consumer financial services,” *SSIN,* 2020.

[18](#chap4.xhtml#ref18).U. Bhatt *et al.,* “Explainable machine learning in deployment,” in Conference on Fairness, Accountability, and Transparency (FAT), 2020.

[19](#chap4.xhtml#ref19).Y. Zhang and L. Zhou, “Fairness assessment for artificial intelligence in financial industry,” arXiv:1912.07211v1, 2019.

[20](#chap4.xhtml#ref20).H. Cramer *et al.,* “Challenges of incorporating algorithmic fairness into practice,” *Conference on Fairness, Accountability, and Transparency (FAT),* 2019.

21.K. Crawford, “The trouble with bias,” Conference on Neural Information Processing Systems (NeurIPS), Keynote, 2017.

[22](#chap4.xhtml#ref22).S. Corbett-Davies and S. Goel, “Defining and designing fair algorithms,” in International Conference on Machine Learning *(ICML),* Tutorial, July 2018.

[23](#chap4.xhtml#ref23).C. J. Smith, “Designing trustworthy AI: A user experience (UX) framework,” in *RSA Conference,* 2020.

[24](#chap4.xhtml#ref24).F. Ian, G. Rayid, J. S. Ron, K. Frauke and L. Julia, *Big Data and Social Science — Data Science Methods and Tools for Research and Practice* (2nd), Chapman and Hall/CRC, 2020.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap4.xhtml#fn1)J. Angwin, J. Larson, S. Mattu, and L. Kirchner. “Machine Bias: There’s software used across the country to predict future criminals. And it’s biased against blacks.” ProPublica. [https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing](https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing). Accessed: Nov 21, 2021.

[²](#chap4.xhtml#fn2)“Veritas Initiative addresses implementation challenges in the responsible use of artificial intelligence and data analytics”. Monetary Authority of Singapore. [https://www.mas.gov.sg/news/media-releases/2021/veritas-initiative-addresses-implemen-tation-challenges](https://www.mas.gov.sg/news/media-releases/2021/veritas-initiative-addresses-implemen-tation-challenges). Accessed: Nov 21, 2021.

[³](#chap4.xhtml#fn3)C. T. Lopez. “DOD adopts 5 principles of artificial intelligence ethics”. US Department of Defense. [https://www.defense.gov/Explore/News/Article/Article/2094085/dod-adopts-5-principles-of-artificial-intelligence-ethics/](https://www.defense.gov/Explore/News/Article/Article/2094085/dod-adopts-5-principles-of-artificial-intelligence-ethics/). Accessed: Nov 21, 2021.

[⁴](#chap4.xhtml#fn4)“Draft ethics guidelines for trustworthy AI”. European Commission. [https://ec.europa.eu/digital-single-market/en/news/draft-ethics-guidelines-trustworthy-ai](https://ec.europa.eu/digital-single-market/en/news/draft-ethics-guidelines-trustworthy-ai). Accessed: Nov 21, 2021.

[⁵](#chap4.xhtml#fn5)“Australia’s artificial intelligence ethics framework”. Australian Government: Department of Industry, Science, Energy and Resources. [https://www.industry.gov.au/data-and-publications/building-australias-artificial-intelligence-capability/ai-ethics-framework/ai-ethics-principles](https://www.industry.gov.au/data-and-publications/building-australias-artificial-intelligence-capability/ai-ethics-framework/ai-ethics-principles). Accessed: Nov 21, 2021.

[⁶](#chap4.xhtml#fn6)IMDA, Singapore. *Model Artificial Intelligence Governance Framework.* 2nd ed. \[Online\]. Available: [https://www.pdpc.gov.sg/-/media/files/pdpc/pdf-files/resource-for-organisation/ai/sgmodelaigovframework2.pdf](https://www.pdpc.gov.sg/-/media/files/pdpc/pdf-files/resource-for-organisation/ai/sgmodelaigovframework2.pdf). Accessed: Nov 21, 2021.

[⁷](#chap4.xhtml#fn7)UC Irvine Machine Learning Repository. UC Irvine. [https://archive.ics.uci.edu/](https://archive.ics.uci.edu/). Accessed: Nov 21, 2021.

[⁸](#chap4.xhtml#fn8)*Marketing dataset: Predict if a client will subscribe a bank term deposit,* Kaggle, \[Online\]. Available: [https://www.kaggle.com/c/marketing-dataset/data](https://www.kaggle.com/c/marketing-dataset/data). Accessed: Nov 21, 2021.

[⁹](#chap4.xhtml#fn9)J. Silberg and J. Manyika. “Tackling bias in artificial intelligence (and in humans).” McKinsey Global Institute. [https://www.mckinsey.com/featured-insights/artificial-intelligence/tackling-bias-in-artificial-intelligence-and-in-humans#](https://www.mckinsey.com/featured-insights/artificial-intelligence/tackling-bias-in-artificial-intelligence-and-in-humans#). Accessed: Nov 21, 2021.

[^(10)](#chap4.xhtml#fn10)“Partnership on AI is bringing together diverse voices from across the AI community”. Partnership on AI. [https://www.partnershiponai.org/](https://www.partnershiponai.org/). Accessed: Nov 21, 2021.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0005](https://doi.org/10.1142/9789811250903_0005)

Chapter 5

**Knowledge Graphs and its Applications in Finance**

***Zhiyu Ge***

**5.1Introduction**

The Knowledge Graph (KG) is a graph-based abstraction of knowledge in which entities (such as objects, events, situations, and concepts) are represented as nodes and relationships are represented as edges, with a semantic layer on top of such graph representations of data and information. The semantic layer links all data and metadata covered by the KG and provides a structure to represent knowledge as explicit semantics. The KG provides a powerful framework to organize, connect, manage, explore, share, and expand data, information, and knowledge. As such, it has many important applications in various subject domains including sociology, science, technology, business, etc.

Although the phrase “Knowledge Graph” was coined decades ago, KG re-emerged as a practical and impactful enterprise knowledge management tool only within the past decade or so. Google Knowledge Graph introduced in May 2012 was the first large-scale operational KG. Since then, technological advances in other areas including data, compute, and algorithms have brought new life to this field and allowed building, maintaining, and utilizing KGs at scale. Enterprise Knowledge Graphs (EKG) help integrate data, information, and knowledge across disparate silos and provide a holistic view of business knowledge and associated connections, equipping organizations with more timely, relevant, enriched, and complete knowledge to effectively and efficiently carry out strategic planning, business operations, IT operations, risk management, and audit or compliance activities.

**5.2Characteristics and Features of Knowledge Graphs**

KG has a combination of characteristics and features that make it unique, interesting, attractive, and useful. These characteristics and features can be utilized to bring benefits while some may also lead to challenges. We will discuss the main challenges toward the end of this chapter.

**5.2.1*Basic Structure and Components of a Knowledge Graph***

By its name, the KG is a graph. It inherits all the data representation and analytical advantages associated with graphs. The graph is a natural choice for connected data. It can easily represent any entities as nodes. Classes of nodes can also be distinguished, and individual node instances can be labeled. Any relationships among these nodes can be defined and represented as edges connecting node pairs, and edges can be directed or undirected and be labeled (either directly or indirectly) as well. Graphs are also good at connecting data, since all data objects, such as data sets, datastores, databases, documents, text, images, audio or video files, etc., can either be represented as nodes in a graph or be transformed into graph format themselves (however, efficiency and operability of such graph representation is a different story depending on its applications). Graphs and their subcomponents are flexible to explore, extend, merge, or delete by simply traversing, adding, combining, or removing nodes and edges.

On the other hand, the KG is more than a graph or a graph database. It typically requires some level of standardization in representation through a controlled vocabulary or taxonomy. Entities and types of relationships need to be uniquely identifiable for interchangeability across different KGs or applications. To structure or represent graph data as knowledge, we also need ontology. Ontologies can describe entities, connections between entities, and business processes. They can also incorporate certain facts and data constraints (axioms). Semantics can be captured via entity or relation identifier (for example, a URI linked to a description webpage), vocabulary, and ontology as well as derived through KG’s logical inference capabilities. KGs incorporate both concept level connections (through taxonomy or ontology) and data level connections for individual data instances. Both types of connections can either be explicitly specified or be inferred by KG.

**5.2.2*Semantic Links or Connections***

It is important to note that KG connects data at the semantic level rather than at the physical level. This means that KG does not join the contents of data objects to form new data objects, but rather it establishes the semantic links between data objects. Such links can either be explicitly specified, automatically generated by the rules embedded in ontology, or created by AI or ML algorithms. So effectively the KG combines knowledge and data in one place, so that they can be queried together.

If we view individual data sources as data objects, KG can span data sources across on-Cloud and on-premises systems or platforms via the use of URIs. KG does not require its underlying data sources to be standardized or enforce a particular schema to source its data, although consistent and therefore merge-able vocabularies and ontologies are typically required. In certain applications, it may require some sort of schema on metadata.

Statistical or ML modeling tasks typically require combined data (in terms of features or labels and training instances) in tabular form. However, for querying, analytics, and business intelligence (BI), in many situations, we may not have to directly access the underlying detailed tabular data, datastore, or databases, we may only need to work with metadata as well as abstracted information and knowledge rather than underlying data itself. KG works well and can even excel in such applications, as we do not have to transform and integrate all underlying data into a data warehouse. Knowledge integration does not require putting everything into a single data lake or data warehouse, the data can be distributed but still connected via KG. In this sense, regardless of where the data is, whether in a single data lake or datastore, or distributed across multiple data lakes or datastores, they can still be connected by a KG. In particular, it makes the KG a well-suited tool to link data across microservices even though data on the inside may not be visible.

**5.2.3*Flexibility and Versatility***

The KG offers a lot of flexibility. It does not have strict requirements on schema. When creating a KG, you do not have to specify the detailed schema up front. Instead, KG allows the schema to evolve, so that users can enhance or modify the data model after seeing the data. This flexibility makes KG more future-proof, as you can modify or update your schema to fit new data without having to recreate the KG from scratch.

The KG is versatile. In addition to data instances, any data objects, data systems, or data application APIs can be represented as nodes in KG, and their connections represented as edges. It can embed domain knowledge, business glossary, and taxonomy; it can represent any structures on entities and relationships; and it is capable of incorporating structured and unstructured data (documents, emails, reports, presentations, and other text or non-text files, etc.) in different languages. The KG can also incorporate multiple domains and associated ontologies, along with connections among these ontologies. Such versatility is derived from the fact that graph is a universal representation of data and data models.

The KG is dynamic and extensible. At any time, existing data or information can be updated, new data or information can be added, and obsolete ones can be removed. As such, KG can facilitate continuous learning through user feedback, and it can easily be extended to accommodate new concepts, objects, or relationships, offering resilience and sustainability. If developed appropriately, KGs can easily be merged, or you can limit your focus on sub-graphs. This is because by design, any graph (or elements of the graph) can be linked to other graphs (or their elements), and relational information can be embedded in the graph not only through edges but also through attributes associated with nodes and/or edges. When merging KGs, you effectively merge the corresponding ontologies (themselves as graphs) and the underlying graph data by merging the nodes or edges and adding any additional edges. When you limit your focus to a sub-graph, you only need to look at nodes within this subgraph and edges connecting those nodes.

The KG can be distributed and scalable. Data in various sources do not have to be pooled. KG query languages such as SPARQL (a recursive acronym for SPARQL Protocol and RDF Query Language) can perform federated query with distributed graph data. There is typically no need to force any changes to existing data systems for the task of building or maintaining KG. It can work alongside existing data systems. Ontology or knowledge representation management can be separated from the day-to-day management of the underlying source data systems. As such, building or maintaining KG does not interfere with maintaining or improving existing data systems. You can link knowledge elements (entities or relationships) to any appropriate data backends such as data systems, databases, data objects, and data APIs.

**5.3Application Areas**

The flexibility and versatility of its underlying graph structure combined with its semantic capability make KG uniquely positioned to meet many material data and information management challenges associated with enterprise applications. In some cases, it may be the most suitable primary tool, while in some other cases, it can significantly enhance the performance of other tools. We focus on applications for financial services, but some of them are also generally applicable for many other business, scientific, and technology domains.

**5.3.1*Enterprise Data and Information Management***

Effective and efficient data and information management at the enterprise scale has always been a challenging but highly rewarding business imperative. Data and information are the life blood of survival and success for any organization in this digital era. There are already a multitude of tools and applications developed to assist critical data and information workloads such as data harmonization, data cataloging, data lineage tracking, data application/API management, data analytics, BI dash boarding, AI/ML model life cycle management, etc. The KG, given its tremendous flexibility in representing and connecting data, is particularly suited for integration of huge amounts of structured and unstructured data from diverse data sources in various formats, and it can enhance the functionalities of existing tools and applications in individual data and information workloads. The KG has become an important tool for enterprise digital transformation.

Enterprise data will continue being distributed but should not be siloed. Simply aggregating them into a data lake will not solve the problem, and we still face data integration or usability challenges. Centralized views alone will not meet the challenges of modern data management. The KG can be an effective tool to integrate data at the semantic level, and help to guide data integration at the physical level. For data integration, semantic data integration into knowledge graphs does not need to merge or even pool data physically from difference sources, but rather pooling the metadata and then building a semantic layer on top to catalog, search, and discover data, make inferences and to derive new knowledge. The KG, by design, can be a distributed system, and it is well equipped to handle the integration of distributed data. Although it can help to build individual data-driven applications, its most impactful use is perhaps to serve as the backbone of a distributed enterprise data strategy that connects not only data, but also information and knowledge across all parts of the organization.

The KG can provide an overarching framework to capture, manage, and make use of all information associated with data, metadata, data systems, and data applications. In particular, an EKG sitting on top of all data assets, information systems, and data workloads can provide an umbrella structure to holistically manage enterprise data and information system, and serve as an effective tool for the development and maintenance of enterprise data strategy and data model. The semantic layer of the EKG contains information and knowledge that are abstracted from the complexity of the actual data underneath, so that the actual data can stay where they are and do not have to be moved, transformed, or copied. With a well-developed EKG, not only we can get a clear and aggregated view of the data and information inventory at the enterprise level, it can also help us to see the connections and the process flows among key elements, enabling us to search for and discover data assets, track data lineage, identify data processing critical paths, understand strong or weak links, develop plans to remediate critical flaws and enhance data systems, derive new strategic business insights, etc. Guided by the EKG, we can quickly identify the likely sources of data and information management issues, and through the links to individual data systems and applications, we can drill down to any specific components of the data and information management system to extract more detailed information and/or to conduct a more targeted investigation. While a data catalog manages metadata and serves as the backbone of the enterprise data governance infrastructure, a KG-powered enterprise data catalog can also intelligently connect metadata and attach meanings to such connections.

At the database level, KG can help enhance the design and performance of traditional relational database management system (RDBMS). By placing a KG on top of the database schema, we can add a layer of semantic connections and constraints among the fields of data tables. This allows automated schema mapping, schema constraint enforcement, and ETL (extract, transform, load) governance. This alternative to traditional RDBMS is called categorical database \[[1](#chap5.xhtml#rref1)\] and is becoming more and more popular for organizations with large amounts of relational data and complicated dependencies.

**5.3.2*Business Operations***

The ability for KG to quickly and efficiently integrate data from diverse sources in various formats makes the KG well-suited for enterprise data integration, cataloging, and governance, and these are indeed the mostly widely adopted use cases for KG. However, data management is not the only type of use cases. In fact, many business applications of KG also stem from the same ability. Additionally, because all semantics in KG are machine processable, business processes represented in KG can be leveraged to automate business operations. Some business application examples in finance are discussed below.

Customer 360 is a celebrated KG use case in finance and many other industries. A KG-enhanced Customer 360 view can bring customer data from all heterogeneous sources and in all formats, and sew them together to assist marketing, identity verification (for secure access and monitoring), customer experience, customer service, risk analytics, fraud detection, etc. Take retail banking on a digital platform for example; the KG-based Customer 360 analysis can help identify individual customers, verify security access, retrieve customer information (such as previous experience, customer preferences, order or service history), and make targeted recommendations, all done in real-time. For customer service, customer data can also be linked to service records and customer service representatives to track quality of service, identify improvement areas, and facilitate intelligent complaint handling. Diversified Customer 360 information can also be leveraged for more effective business analytics and Machine Learning modeling to identify promising customer acquisition leads.

For business strategy development, a KG can incorporate catalogs and information for customers, suppliers, employees, competitors, investors, regulators, and any kinds of relationships and dependencies among these parties, along with market information, supply/demand, and risk/reward data. It can help us to assess the potential impact of a market event, a business campaign or a business plan through analyzing the complicated interactions and through KG reasoning.

For securities trading, financing, and market making, a well-built KG can help to keep close track of all securities on the permissible instrument list (exchange-traded, OTC-traded, or private placement) along with relevant security profile, order book, trade execution, clearing, settlement, and market information such as structure, covenants, rating, issuer profile, ownership, encumbrance, indexes, market participates, bid/ask/book prices, volumes, demand, supply, counterparty, collateral, etc., as well as relationships, dependencies, or constraints among these entities. Such a web of real-time information can help traders to assess timely market opportunities, security availability, security liquidity, supply/demand trends, order book matching, hedging strategies, hedging instrument, financing terms, post trade surveillance, etc. KG traversal and reasoning allows deep-link patterns and connections to be identified timely as the market conditions evolve.

The KG can be used for investment strategy research in equity, bonds, commodities, currencies, real-estate, etc. A big part of investment research is about identifying connections and analyzing consequences, and KG is well suited for both. For example, for even-driven investing, a KG can take names (a company, a commercial real estate (CRE) trust, a corporate issuer, a sovereign, etc.) and events (credit default, earnings surprise, bankruptcy, etc.) as nodes and link names to events by edges representing event happening, together with additional types of nodes and edges representing other market entities and relationships. An analyst can then dynamically estimate the likelihood of a future event link between a pair of name and event based on information and knowledge embedded in the KG together with other AI/ML techniques. Additionally, analyzing the connections and making inferences in the KG may help reveal abnormal patterns in relationships and generate signals for arbitrage opportunities. With KG, analysts can easily trace existing connections, discover hidden connections, and derive new facts with built-in inference capabilities. Information and knowledge derived from the KG can also be used for feature engineering to develop relevant factors for downstream AI/ ML modeling.

For insurance underwriting, the KG can connect data from various traditional and non-traditional sources about the prospects, and assemble unstructured data quickly into structured information according to pre-developed business vocabulary and ontology. Such structured information can then be fed into downstream AI/ML powered underwriting process to determine the optimal policy. Take life insurance for example; the KG is able to incorporate various alternative data such as electronic health records, biometrics, and genomics (where legally permissible), in addition to prospect interview data and paramedical exam data. For property insurance, various customer profile data, property data, and hazard data can be connected and structured in a KG.

For financial and business analytics, the KG can be used to handle the semantics for Natural Language Queries (NLQ). Different types of information can be represented by different node types, and NLQ can be parsed (with help from NLP) to map search terms to relevant nodes in the KG. Semantically legitimate and relevant machine queries can then be derived based on the relationships among nodes and the reasoning functionality embedded in the KG. For example, if the user is asking for facility drawdown amount by credit rating, then the KG can identify the facility node types and the credit rating node types and link the underlying data sources to execute the query. For NLQs that are vague, KG can find all legitimate queries that involve the keywords in the NLQs and conform to the business logic baked into the KG ontology. Then the NLQ engine can either rank these candidate queries and return the most probable ones or ask the user for clarification to narrow them down.

**5.3.3*Risk and Compliance***

The KG also finds its applications in risk management and regulatory or legal compliance. Enterprise KG can serve as the foundation for rapid integration and analysis of all data types. Rapid integration, wide coverage of data, and contextualized information can help provide a holistic and updated picture of aggregated risks, detect hidden risks, and identify new risks timely as they emerge. Regulatory reporting based on such connected data can also become more accurate, timely, and automated. Some examples of KG use cases for risk and compliance are discussed below.

For Know Your Customer or Know Your Business (KYC/KYB) and financial crime compliance, financial institutions are required to conduct effective due diligence to establish customer identity, understand customer activities, and evaluate financial crime risks when developing and maintaining business relationships. A variety of structured and unstructured customer data from multiple sources integrated in the KG can help build up a better Customer 360 profile. In the meantime, the flexible and extensible KG data structure can easily accommodate new and updated customer information and transaction activity information to facilitate ongoing monitoring.

Fraud detection and financial crime analytics is a celebrated use case for KG. For fraud detection and prevention, customer identity data, behavioral data, network data, and transaction data from different sources, such as public records, KYC, cybersecurity, and sales and marketing, can be joined up in a KG, allowing covert fraud patterns and anomalies to be discovered as they emerge. In addition, by tracing the connections in the KG, the findings can have better explanability (compared to signals generated by a black box), so that suspicious activities identified can be more specific and false positive rates can be reduced. This makes anomaly detection and fraud prediction more effective and timelier. Likewise, KG has demonstrated its utility in optimizing transaction surveillance for anti-money laundering detection. The Panama Papers investigation \[[2](#chap5.xhtml#rref2)\] is a famous success story of leveraging the power of KG to systematically and automatically sift through huge amounts of intertwined information to reveal large-scale tax evasion, financial fraud, and money laundering activities involving a complex web of offshore entities, wealthy individuals, and public officials.

For retail credit risk analysis, a large variety of Customer 360 data and traditional personal credit data can be rapidly integrated in KG, allowing for the quick establishment of customer credit profile for credit officers to make faster and more informative decisions. For corporate credit analysis, the KG can help disentangle complicated relationships among suppliers, distributors, partners, and competitors, as well as cross-ownerships to have a better assessment of corporate fundamentals. Target entity (individual customer or company) profiles, transaction history, financial records, etc., and associated relationships in the KG can also be used to develop predictive risk analytics for more accurate credit scoring models.

Trade surveillance at financial institutions, especially large multinational banks and asset managers, has become more and more demanding because of the growing regulatory focus for compliance, high transaction volumes, large varieties of transaction types, and new challenges brought on by the COVID-19 pandemic. To detect trading anomalies and market abuses, compliance teams have to monitor information across trading activities, restricted lists, watch lists, deal teams, HR data, email communications, phone conversations, news stories, research reports, etc., related to a variety of markets across multiple geographic regions and a large number of asset classes (equities, bonds, derivatives, commodities, precious metals, foreign exchange, cryptocurrencies, etc.) A KG-powered intelligent surveillance solution can significantly improve the efficiency and precision of automatic alert generation, management, and reporting by providing better connected information for event/actor identification, alignment of regulatory and business requirements, interpretation of trading conventions and rules, and verification of transaction type specific conditions and constraints, etc.

**5.3.4*Search Engine Optimization and Recommendation Systems***

KGs can also serve as the knowledge base for enterprise search tools and questions-and-answers (Q&A) self-service tools. Relationship information in KG can help enhance discoverability of information, allowing KG-assisted search engines to provide more relevant, accurate, consistent, personalized, and optimized information for better digital customer experience. The KG also brings in information from unstructured or semi-structured data that was previously difficult to search for, making the search results more comprehensive. Additionally, search engines can be enhanced by the semantic capabilities of the KG to return not just the relevant documents or statements but also relevant facts that may not be explicitly stated in any documents. Optimized search performance can make it easier for customers or clients to search for suitable banking and wealth management products, for example, leading to higher customer acquisition rate, lower acquisition cost, and more sales.

Recommendation systems typically employ algorithms to find patterns to reveal association and similarity among items and users. They can benefit from heterogeneous data sources linked together by the KG to include more connected contents and to allow more ways to identify similarities. Recommender systems can have many applications in finance, such as cross-sale of financial products in online banking, finding suitable loans for borrowers in credit underwriting, recommending personalized insurance policy and insurance rider, identifying optimal asset allocation strategies for portfolio management, constructing candidate stock/bond investment portfolios based on investor profile and investment objectives, etc. For these complex problems that depend on many factors and their interplays, KG can add extra benefits on top of traditional approaches by providing alternative information and additional context.

**5.4Key Technology Components for Knowledge Graphs**

Knowledge graphs (KG) build upon two key technology components: (i) a graph representation of data and (ii) an explicit representation of knowledge. Other supporting technologies include storage, compute, and data technologies (especially the Cloud stack), technologies for distributed graph databases and KG functionality delivery, and relevant AI/ML algorithms such as NLP and Named Entity Recognition (NER).

On graph data technologies, there are many ways to represent data as a graph. A graph data model can be implemented from the ground up with a key-value store, for example. There are also graph databases with higher levels of abstraction for users to define more complex graph structures, populate data, and perform query/analytics. Graph databases provide graph representation, graph data storage, and graph query languages. Graph representation tools allow users to define graph ontology that specifies graph data structure, and graph query languages allow users to apply graph algorithms to search for patterns and generate graph analytics. Graph ontology is a way to perform top–down lookup or retrieval of information, while graph query languages allow bottom–up lookup or retrieval of information. As such, KGs typically leverage graph databases as a solid foundation to build further functionalities, in particular the semantic layer. There are primarily two types of graph databases, namely Resource Description Framework (RDF) graph database and Labeled Property Graph (LPG) databases, each having their own pros and cons (discussed in a separate section) depending on use cases.

On top of a graph database, the KG needs a semantic middleware layer which consists of components such as taxonomy and ontology editors, entity/relation extractors, graph mappers for visualization, graph validation and search tools, etc. The semantic middleware components allow humans or other systems to interact with KG; that is, to work with the data in the graph database, and develop and maintain a functional KG which can be used for knowledge retrieval by humans or other systems. Data are the strings and binaries, and information is structured data, while knowledge is human understandable, relatable, and actionable information. As an imperfect analogy from construction, data is like the raw material ground clay, information is like the brick, knowledge is like the building, and the middleware that transforms information to knowledge is like the mortar.

Ontology is a primary mechanism for the KG to embed semantics. It specifies classes or categories of entities together with associated attributes and relationships among entity classes. Ontology can capture business concepts or processes, business models, data models, and connections among them. It can be thought of as the blueprint to automatically map relationships across data. Or put in another way, it can serve as a high-level graph data schema or data model for automatically cataloging and linking data instances. They can incorporate business glossary and business logic, and provide a practical, flexible, and scalable way to link domain knowledge with data. It can also be used to check graph data consistency with built-in constraints. Financial Industry Business Ontology (FIBO) and Financial Industry Business Data Model (FIB-DM: FIBO in SAP PowerDesigner, erwin, Sparx EA, ER/Studio, Visual Paradigm and other data modeling tools) are examples of standardized ontologies for finance.

While ontology embeds rule-based semantics into KG, Natural Language Processing (NLP) algorithms can produce AI/ML based semantics to supplement rule-based semantics and help with KG construction (e.g., entity resolution, association of data records to ontology, generate new knowledge, etc.) and the development of middleware components such as visualization, search engine, and recommendation system. A more detailed discussion on the relationship between KG and AI/ML is provided in a later section.

The EKG is built for scale, and therefore it has high demand for advanced big data technologies. In fact, it is precisely the advances in big data storage and compute that make EKGs more practically feasible for large-scale enterprise data, information, and knowledge management. As Big Data becomes distributed, and alongside graph databases becoming distributed, EKGs also heavily rely on high performance networking for the delivery of KG functionality. Cloud platforms, in particular, encompass all of these Big Data technology components required for the successful implementation and application of the EKG. Commercially available graph databases offered by Cloud providers include AWS Neptune, Azure Cosmos DB, IBM Graph, and Alibaba Graph Database. TigerGraph is designed for distributed graph storage and computing, and is readily available on Cloud, and other leading LPG vendors such as Neo4j have also established distributed computing frameworks leveraging Cloud infrastructure.

**5.5Resource Description Framework Graph versus Labeled Property Graph**

Resource Description Framework (RDF) graphs and Labeled Property Graph (LPG) are the two most popular approaches to modeling graph data. Both allow users to represent and store graph data as nodes and edges (although these terms may have different connotations between RDF and LPG). The RDF is a data model that represents information as “subject–predicate–object” triples. This triple form can naturally represent graph data at the atomic level, where both “subject” and “objects” are nodes (entities) and “predicate” is the directed edge connection (relationship). While the RDF graph represents data at the most granular semantic triple level, the LPG makes use of data structures (key-value structs) to represent entities (objects and concepts) as nodes and relationships as edges. Nodes and edges can have labels, and the associated data structures can consist of key-value pairs as attributes. LPG data models and graphs are generally more transactional and more compact than those of RDF.

In addition to differences in graph data representation, other key differentiations between RDF and LPG are discussed below:

*   *Semantics capturing:* The RDF captures the meaning inside the graph (expressive at the semantic layer and through resolvable identifiers), and semantics in RDF graphs are both human-readable and machine-processable, and can be interpreted uniformly and consistently by any user. Inferences can be generated directly from the graph via standard tools. For property graph, while we can attempt to annotate and store as much information through node/edge attributes, a large part of knowledge and interpretation may reside inside the brains of analysts, which may not be transparent to other users who are not involved in the development of the graph. Inferences with the LPG generally rely on query logics with associated query languages.
*   *Schema and constraints management:* Schema and constraints can be managed primarily at the data level, as in the case of RDF graphs, or primarily at the code level, as in the case of property graphs. There are pros and cons to either approach. If managed at the code level, we have more freedom in data structure, allowing us to specify the schema and constraints after seeing the data, but it puts more responsibility to individual users to ensure compatibility and consistency among data and between data and queries. If managed at the data level, it is vice versa. LPGs have some basic schema and constraint management built in to ensure graph structure and ACID (atomicity, consistency, isolation, durability) support for database transaction processing, while other schemas and constraints need to be explicitly programmed through LPG query languages. Also changes to property graph data model may require refactoring of the graph and associated queries. For RDF, schemas and constraints can be set up and automatically enforced at data level, semantic level, and logical level, providing higher level of assurance for data quality at data ingestion, and requiring minimal changes to the existing graph data and queries as the data model evolves.
*   *Query and graph analytics capabilities:* Different graph data models require different graph query languages. SPARQL is the standard query language for RDF graphs that handles pattern match/ search and ruleset-based inference. SPARQL\* is the property graph extensions of SPARQL to query on RDF\* triples that can reference RDF triples as subject and object resources. LPG query languages are not standardized (yet) and have different syntaxes across different vendor platforms. In addition, LPG queries need to be written in accordance with how the data structures are defined. Both LPG query languages and the standard SPARQL query language for RDF graphs also allow users to update data in the graph databases. With respect to graph analytics and algorithms, such as graph traversal, pattern matching, node centrality, clustering, Page Rank, shortest path, etc., LPGs had an earlier head start, and many LPG platforms have already built up a rich set of analytical capabilities. RDF platforms are catching up in this respect, but because RDF works with atomic decomposition of the data while LPG works with higher level of abstraction customizable for specific applications, LPG generally has better query efficiency and faster analytics performance and is easier to integrate with AI/ML.
*   *Extensibility:* Thanks to global RDF standards such as the World Wide Web Consortium (W3C), RDF graphs can share common global entity identifiers, common data representation, and common ontology, giving users the ability to readily extend their graphs upon new data and perform federated query across different RDF graphs. On the other hand, LPG users tend to use local entity identifiers (internal to the graph), *ad hoc* data structure (for representation and annotation of nodes and edges), and customized ontologies. These may offer flexibility and convenience for the tasks at hand, but may not make it easy to generalize to wider application scope or to merge information between graphs in a uniform way.
*   *Complexity and flexibility:* RDF tends to be more rigid in terms of structure and operability given its atomic data representation and the fact that it has to conform to a set of standards. Its data representation and even some RDF standards may not be user friendly or intuitive for specific domain applications. As such, it is more difficult to learn and has higher overhead costs to set up. On the other hand, LPG data structure is more flexible, since it not bounded by the triple structure. The higher level of abstraction for the node/edge structures allows LPG to build rich internal graph data structures more easily than RDF. Property graphs are more intuitive, agile, nimble, and more adaptive to domain specific requirements. It is easier to learn, easier to set up, and simpler to use, and therefore more user-friendly. In LPG, both nodes and edges can carry attributes, and this is particularly useful for capturing and processing temporal relationships, as the graph can easily incorporate effective date and expiration date as node/edge attributes.
*   *Standardization:* RDF is part of the W3C global standards and technologies to support the Semantic Web. As such, RDF graphs can leverage a stack of standards and tools the W3C community has developed. In addition to the standardized sets of global identifiers that help to identify unique entities, Web Ontology Language (OWL) is a language for defining and instantiating RDF ontologies. RDF Schema (RDFS) and OWL set the W3C standards for schema, and SHApes Constraint Language (SHACL) can be used to specify constraints. The Rule Interchange Format (RIF) and OWL can handle logic-based and ontology-based inferences to discover new relationships. SPARQL is the query language for RDF graphs and the Semantic Web. The PROV standard defines a data model to support the interchange of provenance information in heterogeneous environments, which is very helpful for data lineage tracking. LPGs, on the other hand, either lack such standardized functionalities or need to establish some workarounds to leverage these RDF tools. Application-specific schemas, constraints, and inferences may need to be explicitly programmed through LPG query languages. LPGs do not require standardized entity identifiers, vocabularies, and ontologies, and different LPG platforms have their own separate query languages. However, there is an ongoing effort to standardize those query languages across LPG platforms.

It is not a question of which approach wins over the other, as both have their own pros and cons that lead to different strengths and weaknesses for different types of use cases. As RDF is an atomic, universal, and standardized representation of graph data, it is very interoperable across different RDF graph instances and RDF graph data systems. Also, RDF has richer capabilities in terms of semantic expressivity and inference, allowing higher level of machine operable semantic information to be directly incorporated in and derived from RDF graphs. Therefore, for use cases where interchangeability is important and for applications requiring more explicit semantic information capturing, processing, and inferencing, RDF may be a better choice. On the other hand, the object-oriented and higher-level abstractions of graph data model with LPGs can be more intuitive, more efficient, and easier to work with. An analogy in computer programming is that while binary arithmetic operations are atomic, universal, and interoperable, we do not need to represent every computing task as a series of such operations and program binary arithmetic operations directly. The LPG data structures help to make the graph data representation more compact, and graph query and analytics more efficient, saving storage and time. It is also simpler and takes less time to prepare in terms of setting up a graph database and getting acquainted with the analytics software. So, LPG approach may be preferred for use cases where large-scale graph analytics are involved, where semantics and/ or inferences are not in high demand, and where agility and time to production are important considerations.

An important note to mention is that there has been some progress to integrate these two approaches to reap the benefits associated with strengths of both graph data models. As RDF is more atomic and semantically more expressive than LPG, LPGs can in theory be converted to RDF without loss of information for graph data interchange, integration, and inference, for example. However, since LPGs generally do not embed high level of semantics internally, the exported RDF graphs will not capture the knowledge external to LPGs, although inference may help to some extent. In the other direction, frameworks and software applications have been developed to convert RDF graphs to LPG graphs without loss of information. For example, the LPG platform Neo4j has developed neosemantics (n10s), a plug-in that enables the use of RDF in Neo4j, and integrated GraphScale to make queries more performant through more expressive reasoning. A Neo4j study \[[3](#chap5.xhtml#rref3)\] showed that this combination had faster query performance comparing to RDF-based reasoning through SPARQL. Of course, there would be some additional cost to convert between RDF and LPG. TigerGraph can also import RDF graphs and ontologies for KG construction on their LPG platform.

With the existing technologies available, conversions between RDFs and LPGs can be done, in both directions, without loss of information, as long as the vocabularies and ontologies are well mapped between the two. There is enough flexibility in vocabulary or ontology design for LPGs to map all RDF vocabularies and ontologies in theory, and vice versa. However, whether users want or need to do so and whether vendors opt to provide full conversion functionalities are separate questions. Ultimately RDF/RDF\* can serve as the common denominator for graph data exchange and graph data integration across different types of graphs — RDF graphs or LPGs (after converting to RDF/RDF\* representation of course).

Recently, a Semantic Property Graph (SPG) \[[4](#chap5.xhtml#rref4)\] approach was proposed to take advantage of the best of both worlds by restructuring and converting certain RDF nodes and edges into attributes of a property graph, in a way that RDF functionalities can still be preserved and the resulting SPG becomes more compact in size (with respect to memory and storage) and more efficient in terms of scalable graph analytics.

With respect to applications to knowledge graphs specifically, the KG can be built using either graph data models, although the term “knowledge graph” traditionally and still commonly refers to RDF-based KGs. However, RDF may be more suitable to serve as a strategic tool for large-scale EKG, while LPG may be better suited as a tactical tool for more agile and localized KG use cases. As Jesús Barrasa of Neo4j put it, we need to “balance between expressivity and performance without falling into unneeded complexity”. Ultimately, there are tools available to convert, connect, and integrate LPG-based KGs into a broader EKG.

Currently, the graph database field, in Google search interest terms (which may not represent actual usage), is dominated by LPG thanks to its intuitive design, faster graph traversal/pattern matching, and ease of use \[[5](#chap5.xhtml#rref5)\]. However, for large-scale KG and EKG applications, standardization and exchangeability can be important, and semantic or reasoning capabilities can be helpful as well. That is why industry-scale and web-scale KGs and EKGs for semantic data or information integration are typically built based on RDF standards. It is absolutely fine to begin the KG-building journey with LPG to smoothen out the learning curve and for a faster delivery, but inconsistencies due to non-standard data models, vocabularies, and query languages will accumulate as technical debt that may come back to bite you later at the time of knowledge integration across KGs. Therefore, LPG-based KGs need to be designed carefully across different parts of the organization in terms of identifiers, vocabulary, and ontology. Otherwise, we are just creating isolated KGs that may be difficult to integrate in the future. The LPG community needs to learn or borrow from the RDF community with respect to standardization, not just on a common query language but also on data structure abstraction and entity references.

**5.6The Role of Machine Learning**

Deductive reasoning reaches specific conclusions from generalities. Inductive reasoning makes broad generalizations from specific observations. Human intelligence combines both deductive and inductive reasoning. There is no reason why machine intelligence, also known as AI, should be effectuated differently. For machine deductive reasoning, the KG is an effective tool to capture domain terminologies, taxonomies, hypotheses, and logics via vocabularies, ontologies, and inference. For machine inductive reasoning, data driven analytics and modeling, in particular Machine Learning (ML), fit the objective well. The academic community also defines a third type of reasoning for making the likeliest possible explanation from an incomplete set of observations, termed abductive reasoning. For the sake of this discussion, we group it with inductive reasoning, as machine learning answers to both.

The KG is a structured and natural approach to represent domain knowledge that can be subsequently ported to AI applications. In KG, rulesets are governed by vocabulary, ontology, and logic. They define formal concepts and clear relationships with no ambiguity in entities and semantics. Inferences made are also deterministic. There are already domain specific vocabularies and ontologies that are available for use while continuously being enhanced. Examples include FIBO (Financial Industry Business Ontology), BMO (an e-Business Model Ontology), and KPIOnto (an ontology to describe Key Performance Indicators). Relevant subsets of these standardized public vocabularies and ontologies can be carefully selected and then augmented to incorporate organization-specific business glossaries, business taxonomies, and business processes etc. Legitimate and logically consistent rules that are not explicitly specified can also be automatically derived by the KG through its inference capability. Deductive semantics via KG can be used on a standalone basis when clarity and accuracy are required, e.g., for policy and procedure management, contract management, and legal applications. Although deductive semantics enjoy high level of accuracy and precision, it may not be complete, as the number of rules that can be either explicitly specified or logically derived are still finite. In contrast, ML (in particular NLP) based inductive semantics are data driven and therefore largely probabilistic in nature. New patterns can be identified, additional rules can be discovered, and hidden associations can be revealed. However, NLP-based inductive semantics and inferences are made with possible errors and ambiguity. They may not be suitable when high levels of clarity and accuracy are required. KG and ML can enhance each other. ML can help to enrich the set of rules explicitly or implicitly embedded in KG, and rules in KG can be used to constrain or guide ML model training to enhance ML accuracy and precision.

**5.6.1*Machine Learning for Knowledge Graphs***

Building KGs, especially the large-scale ones, typically needs to rely on rule-based and/or model-based algorithms to automate tasks related to knowledge representation and knowledge acquisition. Knowledge representation is about representing entities and relationships in lower dimensional vector spaces, as well as criteria and methods for assessing the plausibility of entities and relationships. Proper knowledge representations preserve the meanings or semantic structures in the data while being machine processable. They can be used for downstream semantic processing such as knowledge acquisition and KG enrichment, and for knowledge-aware applications such as ML feature engineering, natural language understanding (NLU), and recommender systems. While for simpler use cases, we may be able to develop a well-defined vocabulary and ontology for domain knowledge representation, there could be considerable manual efforts required to specify all possible entity types and their relationships. In large-scale use cases, we may be limited by the amount of human resources available and our ability to specify everything comprehensively through manual efforts. Most of the time, we do need to develop at least part of the knowledge representations from data, and statistical/ML methods such as knowledge graph embedding, energy-based semantic matching, linear/bilinear encoding, factorization, deep neural network (DNN), convolutional neural network (CNN), recurrent neural network (RNN), and graph neural network (GNN) can be employed for this task. Some of these approaches are also capable of handling uncertainties (as confidence scores) associated with relational facts.

Knowledge acquisition involves entity extraction, relation extraction, and KG completion (filling in the missing relationships between entities or missing subjects/objects in relationships). ML approaches, in particular NLP ones, can help to crawl through structured and unstructured source data, extract/resolve entities, identify relationships among these entities, and map these entities to nodes and relationships to edges in the KG. More advanced ML algorithms can also help discover deeper and more subtle patterns and distill information into connected knowledge, so that such knowledge can be directly embedded into the KG (e.g., \[[6](#chap5.xhtml#rref6)\]).

Text mining for the extraction of entities and relationships can be done at the data model level to establish the concepts (entity/ node classes) and high-level relationships (edges connecting node classes), which are ingredients of KG vocabulary and ontology. It can also be done at the data instance level to identify the specific entity instances, relationships, and associated attributes. For named entity recognition (NER), in addition to language and subject domain specific rule-based methods and traditional ML approaches, such as multi-class classification and conditional random fields (CRF), advanced deep learning algorithms such as LSTM-CNN, LSTM-CRF, and Stack-LSTM can be implemented with ML libraries such as Keras and Tensorflow. To reduce the label annotation labor, semi-supervised learning approaches can be taken. ML algorithms are also available for named entity typing (NET) which classifies named entities into types (possibly hierarchical), named entity linking/disambiguation (NEL/NED) which links entities between source data and KG, and entity alignment which maps entities between KGs. Relation extraction (RE) from text generally can be more complicated than entity extraction. Rule-based approaches generally suffer from low recall, and supervised learning typically is impractical due to the lack of sufficient accurately labeled data. Therefore, RE is typically done with weakly supervised learning, self-supervised learning, or distantly supervised learning, in which labels are machine generated from strong heuristics, from a set of hand-crafted rules, from parallelism to an existing knowledge base, or otherwise derived from the output of pre-existing NLP systems. Common neural networks involved in those learning types for RE include variants of CNN, RNN, GNN, generative adversarial network (GAN), reinforcement learning, etc. Beyond entity/relation extraction and classification from text corpora, there are ML algorithms to tag documents to concepts, including those semantically related concepts not directly mentioned in those documents, and to classify graphs/sub-graphs. All of these ML algorithms allow extraction of entities/relations and semantic tagging to be done automatically and at scale in KG construction.

Once entity/relationship extractions are done, knowledge graph completion can be performed with the semantic reasoning functionality offered by the RDF technology, which is ontology and logic driven. Alternatively, data driven ML approaches can be used to supplement rule-based completion to enhance KG semantics. ML algorithms can take KG embeddings and other auxiliary information to project missing entities and relationships. This can be done for example on a step-by-step basis to capture deep link (multi-hop) relationships. There are also potentially more efficient multi-hop reasoning and path-finding algorithms such as random walks and reinforcement learning based path-finding algorithms \[[7](#chap5.xhtml#rref7), [8](#chap5.xhtml#rref8)\] for multi-hop machine reasoning. Relationship representation in knowledge graphs tends to be skewed, with some relations having large associated observations (triples) while many others having very few. Meta relational learning approaches \[[9](#chap5.xhtml#rref9)\] attempt to deal with this challenging few-shot link prediction problem by leveraging ML algorithms such as Graph Convolutional Networks (GCN), long short-term memory (LSTM), GAN, etc.

**5.6.2*Knowledge Graph-Assisted Machine Learning***

New ML frameworks have been proposed to leverage domain knowledge in model training and prediction \[[10](#chap5.xhtml#rref10)\]. There are multiple ways to leverage information, knowledge, and inference in KG for ML workflows, such as integrating data from diverse data sources, augmenting training data, guiding automatic feature selection, incorporating graph data/analytics for feature engineering, embedding graph structure in neural network design, embedding domain knowledge as declarative rules or constraints directly in neural network training, verifying validity of ML models, and making enhanced inferences from ML projections.

As the KG is a very effective tool to integrate all sorts of data, structured and unstructured in various formats, from diverse sources, it can quickly assemble the broad range of data needed for data intensive ML training tasks, while the traditional way of generating training data from data warehouses may be relatively slow and limited in scope, given its dependency on ETL to handle structured data only.

For feature engineering, machine processable domain knowledge embedded in KG can be used to automatically determine the most relevant and predictive features to use for specific learning tasks by assessing the original input features against the relationships (specified or derived) depicted in the KG. This is a highly desirable functionality for AutoML and reinforcement learnings, in particular. As KG integrates alternative data and creates structures for unstructured data, it also represents a good source to create novel features to enhance the predictability of ML models. Novel features can be extracted directly from the explicit data/information from the KG or indirectly via graph analytics and graph embeddings, which are low-dimensional vector representations of nodes, edges, and subgraphs that retain semantic meanings.

Domain knowledge can also be used to generate or augment labeled training data for ML. For example, for object classification in computer vision, image transformations such as rotation, minor distortion or background noise, and flipping usually would not change classification of objects in an image. Therefore, these transformations can be applied to the original set of training images to create variations and thereby propagating the image samples available for training. For entity resolution, known variations of the same entities can also be added to the training data, so that accuracy of the solution can be enhanced. Generally, all the observations explicitly stored in KG and derived from the KG rulesets can be added to the ML training data where appropriate. ML model training data can also be augmented with data instances algorithmically generated from the rules embedded in the KG. Those machine-generated instances reflect prior knowledge and may be very helpful in situations such as few-shot learning. Similar to instance weighting, with enough representation in ML model training data, the prior knowledge will sink in.

Graph Neural Networks (GNN) \[[11](#chap5.xhtml#rref11)\] such as recurrent GNN, convolutional GNN, Graph Autoencoder (GAE), and Spatial-temporal GNN are neural network architectures designed to capture domain structures in the graph form. New DNN frameworks (e.g., \[[12](#chap5.xhtml#rref12)–[14](#chap5.xhtml#rref14)\]) have been proposed to incorporate declarative rules and constraints (either by adding additional neurons to represent such rules or constraints or by translating them into regularization terms) as an integral part of the end-to-end deep neural network model training, so that the model trained can automatically conform to or bias toward the domain knowledge captured in the KG. In this sense, the KG can serve as the default data model for an ML exercise and guide machine learning. Additionally, ML can take the existing learnings in KG as the starting point or the prior, avoiding the problem of a cold start and potentially reducing the need for large amount of labeled training data.

KG can contextualize ML not just in terms of guiding model training but also in terms of making inferences from ML model. When interpreting ML predictions or creations, the KG can provide the context to translate ML output to semantics and knowledge, thereby enhancing ML explanability. Knowledge acquired from machine learning can be incorporated into the KG and run through KG inference to derive additional knowledge or to validate the ML model by checking for consistency between KG native knowledge and ML acquired knowledge, all done automatically by machine. Once acquired knowledge from ML is embedded into a KG, it can be made visible, discoverable, and understandable to other users and computer systems.

**5.6.3*Combining Knowledge Graphs and Machine Learning for more Effective AI***

Although KG and ML provide solutions to different types of machine reasoning, they can closely intertwine and interact with each other to build more advanced solutions for AI. Semantic AI \[[15](#chap5.xhtml#rref15)\] is one prominent example of fusing Machine Learning and Knowledge Graphs together to deliver automated applications such as semantic classification, semantic search, smart cataloging, content management, recommender systems, dialog systems, NLU, and many more related to Natural Language Processing. A semantic AI approach can also materially enhance data management, providing a structured, connected, informative, and holistic view of enterprise data assets and making these data assets more discoverable, searchable, interpretable, and reusable. Better data management in turn helps to develop better AI/ML.

There is no need to rediscover through ML for knowledge already captured in the KG. A well-developed KG can serve as a strong base model for transfer learning, i.e., to train ML models on top of this KG and use the existing knowledge in the KG as constraints. KG as a tool for active learning can incorporate feedback from human interactions semantically, thereby allowing continuous improvement of ML model quality. Reciprocally, learnings from AI/ML can also be solidified and incorporated into to the existing knowledge body in KG, providing a more comprehensive knowledge base as well as a stronger learning base for further transfer learning.

Brute-force deep learning approaches to NLP attempt to capture word associations and semantics from corpora of text while not explicitly taking into account language rules of phonology, morphology, syntax, semantics, and pragmatics. Such approaches typically require massive corpora of text and a considerable amount of training time to re-learn such rules. Whereas leveraging a linguistic KG incorporating even some most common language rules can help reduce the volume of data and time required to train a language model and offer performance improvements. This is a highly viable approach as languages are themselves symbolic and rule-governed systems. Meanwhile, any additional knowledge automatically acquired for a specific domain via fine-tuning deep language models pre-trained from large-scale corpora (such as BERT and GPT-2/3) can be added to a domain-specific KG for better performance of knowledge aware applications.

KG has a natural close tie to NLP, because both are targetted to capture semantics and can interact with each other for better AI performance. For example, Google uses Google Knowledge Graph to answer Google Assistant and Google Home voice queries with the help from NLP. In return, these Machine Learning algorithms deployed on Google Cloud Platform (GCP) can be improved with the help from Google Knowledge Graph. For Named Entity Recognition (NER), extraction and classification of entities can apply a combination of statistical/deep learning-based and KG-based approaches. NER based on rules and patterns embedded in KG enjoys precision and unambiguity, with no training data required; however, its scope could be narrow and limited to the semantic information captured in KG. NER through statistical/ML modeling is probabilistic in nature and does not require any prior knowledge structure, but it can be very data and compute intensive to develop. The combined approach can be thought of as a semi-supervised learning in cases where some labels used for ML training can be automatically derived based on KG, or it can be thought of as a type of transfer learning where the base model is derived from the KG. If you apply this process iteratively, that is, use ML to augment KG (by enriching vocabulary and ontology and by embedding new patterns) and then use KG to enhance ML (linking to background/contextual information and constraints), you get a virtuous circle that continuously improves the functionality and performance of your NER algorithm.

As an example of combining KG and ML for financial applications, there have been many success stories in leveraging such a combination for fighting financial crime. In the fraud and money laundry detection domain, a large body of hand-crafted rules and patterns already exist and are proven to be valid and effective, especially when they are incorporated in a connected KG with assistance from KG reasoning. These rules or patterns do not need to be re-learnt with ML. Instead, posing them as constraints or transforming them as additional features in the ML training can allow modelers to train more effective models more efficiently and to focus on discovering new patterns or rules, and in some cases, reducing the need for large amounts of data. In turn, these new patterns and rules can be linked to the existing patterns and rules in the KG to reveal more signals and insights, and provide better contextual explanations for findings.

![](images/p184.jpg)

**Figure 5.1.**The KG development process

**5.7Building and Maintaining a Business Knowledge Graph**

KGs are usually not developed in one go, but rather, it is typically an iterative process. For demonstration purposes, we take a common use case and illustrate the high-level steps to follow, assuming we start from scratch. A sketch of KG development process is illustrated in [Figure 5.1](#chap5.xhtml#fig5-1).

**5.7.1*Clarify Business Objectives for Knowledge Graphs***

Like in many other innovation projects with advanced technologies, we can start out by identifying a relevant and manageable use case that can immediately add value to the organization. Possible quick win candidates may come from domains like semantic search, data cataloging, talent management, recommendation system, operational risk identification, financial fraud detection, etc. Stakeholders for KG building may include knowledge scientists, data architects, data engineers, data scientists, MLOps, domain experts, business users, etc., and it will be better to have these stakeholders represented in the KG development team.

For this high-level discussion, we take a sample use case in talent management, which is a universal concern for all organizations. Given that talent management is still a very broad area, we can narrow down the scope of the project further to focus on skillset matching for project assignment. This is a meaningful problem since many organizations are optimizing their existing workforce by making resources more fungible across team boundaries. For our example project, the domain experts could be from the HR department, and the business users could be business unit managers or department heads.

**5.7.2*Analyze Relevant Types of Data Objects and Data Models***

To decide what should be included in the KG, we need to have a good overall understanding of what data and information are required for the project at hand and what are available. Relevant data and information may include structured data, semi-structured data, unstructured data (such as emails, reports, dashboards, articles, text files, video/ audio files, etc.), metadata, and business glossaries or taxonomies. This is may be achieved, for example, with the help from another KG on enterprise data assets or a data catalog for data discovery and sharing. Having a clear picture of the source data inventory helps to ensure the relevancy and completeness of information to be included in the KG. Additionally, if any critical information is missing, incomplete, or inaccurate, such as inadequate metadata, then additional data collection, cleansing, and curation actions need to be taken. Some applications may require only metadata (such as a KG for data cataloging if the data assets are well-tagged), while others may need to look into the contents of the data assets in order to extract semantic information. In the latter case, if semi-structured/unstructured data are involved, we need to decide on appropriate information extraction approaches. Business glossaries and taxonomies, if available, also carry data model information that is very helpful for KG building.

For our example project, we may need employee profiles (such as skillsets, education, qualifications, experiences, and interests) and project information (such as type of project, project description, list of tasks/methods involved, skillsets required, and project keywords). Relevant documents may include webpages for employee biography and project description, employee CVs, detailed project specification documentation, reports or documentation on related past projects, reports written by employees, company organization charts, functional instruction manuals, related subject domain information (in various internal documents, webpages, articles, books, etc.), project timelines, employee holiday or leave schedules, relevant business domain taxonomies (e.g. commercial banking, investment banking, asset management, IT, risk management, finance), relevant HR taxonomies, etc. Apparently, there are unstructured text documents involved and text mining techniques are needed for information extraction in this project.

**5.7.3*Develop Functional Vocabulary and Ontology***

A vocabulary is a controlled and standardized set of terms that the KG can reference. It usually focuses on a specific domain, and represents all objects and concepts in that domain that are relevant for the KG. Each term should have a specific and unambiguous meaning and is uniquely identifiable. Ontology, on the other hand, describes all relations among the terms in vocabulary. It captures the relations at the conceptual level or category, class, or type level, rather than at the data instance level.

Existing business glossaries and taxonomies represent a good starting point for defining the vocabulary and ontology needed by the KG. User and/or domain expert focused design sessions can be held to brainstorm and determine additional terms and relations with respect to business concepts and processes. If multiple business glossaries and taxonomies are involved, we need to standardize across them and then add in any additional terms or relations required to represent all the concepts needed in the knowledge graph. Connections between the final set of terms and between taxonomies are then identified and reconciled to form the initial versions of the vocabulary and ontology. Designing vocabulary and ontology usually requires a combined effort from all stakeholders. The process itself can be distributed, for example, via a card sorting exercise, where individual team members come up with their own proposals first, but it also needs to be centrally coordinated, aggregated, and standardized. In this effort, formal ontology languages, such as Web Ontology Language (OWL) and its enhanced version OWL2, can be used to help construct ontologies. For certain common subject/business domains, there are already standardized public vocabularies and ontologies available. We may not need to start from scratch but instead, we can evaluate such standard sets for appropriateness of use, choose a subset as the base vocabulary and ontology, and then enrich or modify them according to our own specific business environments and practices. Given flexibility and extensibility of the KG, its vocabulary and ontology can be built in an incremental fashion by starting with simpler versions which cover the key concepts and relationships for immediate application, then enhancing them gradually, each time adding new elements based on domain expert/user feedback and business needs.

For our example project, let us start with a simple ontology that includes three concepts only — (i) Employee, (ii) Skill, and (iii) Project — together with a few basic relations, as depicted in [Figure 5.2](#chap5.xhtml#fig5-2).

Let us also assume that our skill vocabulary includes only five sample skills needed for our application: (i) data processing (DP), (ii) data visualization (Vis), (iii) machine learning (ML), (iv) Python,and (v) SQL. Our objective is to match employees to projects based on skillsets (both possessed and required), employee experience, and employee interest. Of course, in the real-world setting, each of these concepts may have their own hierarchies (taxonomies), and there can be more relations, richer vocabularies, and more matching considerations such as geographic location, project timelines, and employee availability, but we can leave those for future enhancement.

![](images/p187.jpg)

**Figure 5.2.**A simple ontology for project assignment use case illustration

**5.7.4*Embed Knowledge Data into Knowledge Graphs***

Ontology is the skeleton of a KG. Once we have it, we need to add knowledge data instances to the KG as the flesh. Mapping individual data instances to the ontology manually is not practical in general. We need to automate this process. For small-scale applications and applications with structured input, rule-based mapping from raw data to graph representation may be feasible and sufficient. However, when the data volume becomes large and data source or type becomes diverse, we will have to find intelligent ways to process raw data and relate them to the ontology. This typically requires NLP-based knowledge acquisition, which involves techniques such as entity extraction, relation extraction, attribute extraction, and KG completion. Note that knowledge representation is the foundation for these techniques. It refers to the machine internal representation of semantics for text mining, not the graph representation of data (RDF triples or property graph structs).

Instead of or in addition to parsing the contents of unstructured data and extract structured information to be incorporated into a KG, we may also opt to leverage deterministic or AI/ML algorithms to generate metadata on each unstructured source object and embed such metadata into the KG. For example, we can use NLP techniques to classify documents, and represent each individual document as a node in the KG and associate its document class as an attribute of the node. Likewise, we can also tag datasets and even databases, and bring them in as nodes. There are no restrictions to mixing different types of nodes in the same KG, as long as it is semantically meaningful to do so. In this approach, there is no need to replicate or transform any of the underlying data assets, and they can physically stay where they are, yet are semantically linked by the KG.

The same NLP techniques can also be used to extract concepts and relations needed for ontology. Hypothetically, this allows ontologies to be generated completely from data without any human input. However, this is not generally recommended, given the high degree of relevancy and accuracy required of ontologies. If the ontology is messed up, the quality of the KG can be materially affected. We can, however, take this approach to supplement ontologies developed by human experts, and let the human experts decide whether or not the new ontology elements found by ML should be added to the KG.

For our example use case, suppose we have the following data available after going through the entity/relation extraction exercise over structured and unstructured raw data for employees and projects.

We have three projects together with required skillsets:

1.  Analytics: DP, SQL
2.  BI Dashboarding: DP, Vis
3.  AI/ML: DP, Python, ML

We have three employees with possessed skillsets, project experiences, and interests:

1.  Alice 
    *   Skills: ML, Vis, Python, SQL
    *   Has experience in: AI/ML
    *   Interested in: BI Dashboarding
2.  Bob 
    *   Skills: DP, Vis, SQL
    *   Has experience in: Analytics, BI Dashboarding
    *   Interested in: AI/ML
3.  Cathy 
    *   Skills: DP, Vis
    *   Has experience in: BI Dashboarding
    *   Interested in: Analytics

Using these data to populate our KG based on the ontology we have developed earlier, we get three employee nodes, three project nodes, and five skill nodes, along with the corresponding arrows specified by the data.

Note that as a by-product of the entity/relation extraction exercise, we may also be able to expand, based on the actual employee data and project data, the skill vocabulary to include additional skills, or to expand the existing concept set to include “availability”, for instance.

**5.7.5*Store, Evaluate, and Deploy Knowledge Graphs***

Extracted entities and relations can be serialized into various graph data formats (such as RDF/XML, RDF/JSON, Turtle, N-Triples, N-Quads, JSON-LD for RDF, and various LPG formats such as Neo4j and TigerGraph) for storage and analytics. The RDF serialization formats and mappings are fairly standardized, but the property graph formats and mappings are not. For LPG serializations, some entities and relations may be mapped to attributes instead of nodes or edges, depending on data model design of course.

Before putting a KG into production, we also need to evaluate its quality. Testing may involve KG query and KG inference checks with ground truth samples that are manually or algorithmically generated, or samples of KG facts can be selected and manually inspected for validity. However, such an approach may become too complex or difficult to scale for large and sophisticated KGs. In addition, different use case requirements may demand different performance metrics (such as semantic accuracy, syntactic validity, consistency, relevancy, similarity, conciseness, completeness) or different combinations of performance metrics. For example, with recommender systems such as our example use case, relevancy of recommendations and the degree of match (similarity) between project requirements and employee qualifications may be more important than syntactic validity or conciseness. To limit the complexity in testing, separate tests may focus on smaller subsets or specific application requirements of the KG.

The initial KG may be developed and tested with a narrower scope (in terms of the use of simplified vocabulary and ontology and/ or samples of raw data). Once its functionality and utility are proven, it can be gradually scaled up and optimized by augmenting its vocabulary and ontology, by loading more raw data, and by the virtuous circular enhancement interaction between KG and ML. In the sense, KGs can be deployed on a CI/CD basis.

**5.7.6*Query a Knowledge Graph***

Querying the structured information extracted and stored in the KG, either in the ontology or in graph nodes/edges, is quite straightforward. SPARQL is the query language for RDF-based KGs, and LPG vendors also provide their own graph query languages (e.g., Cypher for Neo4j and GSQL for TigerGaph) that can work on LPG-based KGs. When querying an RDF-based KG, SPARQL can automatically infer additional knowledge not explicitly included in the underlying data or metadata. For an LPG-based KG, users may need to write specific query snippets to derive additional information.

KGs can also have their own search APIs that allow other applications to find information. For RDF-based KGs, such APIs can be built based on W3C standard [schema.org](http://www.schema.org) types. APIs for LPG-based KG need to be built upon the underlying LPG database APIs. GraphQL (not restricted to graph applications despite its name) is a very effective tool to query a KG through its API, and the ontology of the KG provides the schema that GraphQL needs to describe the data.

For our example use case, we can query for a one-to-one match between employee and project. If we base our criteria on experience, then the query should return Alice to AI/ML, Bob to Analytics, and Cathy to BI Dashboarding. If we base our criteria on interest (for career development purpose, for example), then the query should return Alice to BI Dashboarding, Bob to AI/ML, and Cathy to Analytics.

**5.7.7*Lifecycle Management***

As KG is flexible and dynamic in nature, its vocabulary and ontology can evolve, and its underlying data may be subject to change. Vocabulary or ontology management and data update management have become important. Policies and procedures need to be established to control Create, Read, Update, and Delete (CRUD) operations with proper governance. Performance of the KG-based application needs to be monitored to identify and remediate potential issues. Vocabulary or ontology design needs to be subject to continuous validation and enhancement, along with underlying ML algorithms involved in KG building. The ability to collect ongoing feedback from users is also very important. For example, for our project assignment recommender, we can request user feedback on relevancy of resource recommendations, either as a Yes/No option or on a sliding scale.

The initial KG can be expanded to cover a wider domain, and sub-domain KGs can be merged to form an EKG. For our example use case for instance, once we have established utility to assign resources to projects, we may consider adding a similar functionality of matching employees or external candidates to job openings, and iterate the KG building procedures to include additional concepts, vocabularies, relations, and relevant data. The new KG may be further expanded to cover other areas of staffing and then be combined with KGs for career development, compensation, safety and health, and employee and labor relations to serve as the EKG for human resource management.

An enterprise level KG development and governance strategy can be very helpful to coordinate development effort among different domain areas, ensure consistency in standards and quality, optimize coverage, and minimize future integration problems.

**5.8Knowledge Graph Solutions**

This section provides a brief survey of tools, platforms, and software solutions for KG development and maintenance. The survey is not intended to be comprehensive. We leave it as a good exercise for the reader to develop a KG for this topic. Examples of KGs publicly available and KG-based services, including some specifically for the financial services industry, are also provided. The following discussion is for information only and should not be interpreted as an advertisement or endorsement for any of the service providers mentioned.

**5.8.1*Knowledge Graph Development and Maintenance Solutions***

5.8.1.1*Graph Database Solutions*

Although the first prototypes of graph databases emerged many decades ago, it was not until mid- to late-2000s when operational graph databases with ACID guarantees started to become popular. By now, more than a dozen fully functional graph databases are available for hosting KGs.

LPG databases such as Neo4j and TigerGraphs use very intuitive data structures to represent graph data. Although they are less semantically expressive than RDF graphs, they are easy for users to learn, and it is nimble and user friendly to set up KGs, and agile enough to score quick wins. These LPG platforms may have their own query languages and/or graph computing engines, offering better query and analytics performance than their RDF counterparts. As such, developers often start out with LPG databases for their first KGs. Additionally, Neo4j has built in many functionalities including conversion tools for RDF graphs to make KG building and maintenance more feasible and pragmatic. TigerGraphs, on the other hand, has an edge in terms of native support for massively parallel processing (MPP), making its databases more scalable with better graph query and analytics performance (especially for deep-link graph traversal and analytics). Other common LPG databases include ArangoDB, OrientDB, JanusGraph, Dgraph, etc.

RDF-based KGs are more semantically expressive, and they are supported by semantic capabilities such as inference and reasoning. However, to what extent such level of expressivity and inference capability are required depends on the use cases. For use cases where graph query and analytics are more important than semantics, the semantic overhead can slow down analytics. Therefore, RDF-based KGs graphs are more suited for use cases where semantics and reasoning are the more important considerations. Regardless, standardization associated with RDF does allow for much better data exchange ability and therefore makes it much easier to integrate across KGs. Because of semantic and standardization advantages, RDF databases are more often used to support large-scale KGs and EKGs. Popular RDF graph databases (triple stores) include, for example, Apache Jena, GraphDB, AllegroGraph, Stardog, and AnzoGraph DB. The last two also support LPG.

Some Cloud providers also offer their own graph database services. For example, Azure Cosmos DB supports LPG, AWS Neptune supports RDF and LPG, IBM Graph supports LPG, and Graph Database on Alibaba Cloud supports LPG. In addition, many third-party SaaS graph databases offerings are also available on Cloud marketplace. Self-managed Neo4j databases can be deployed on the major Cloud platforms including Amazon Web Services, Google Cloud Platform, and Microsoft Azure. Full-managed Neo4j (Aura) is available on GCP. TigerGraph Cloud is available through Cloud marketplaces on AWS, Azure, and GCP. Some other graph databases available on cloud marketplace include JanusGraph on GCP (backed by Google Cloud Bigtable) and AWS, Dgraph on AWS, GCP and Azure, Virtuoso on AWS and Azure, and OrientDB on AWS and Azure, etc.

5.8.1.2*Graph Computing Frameworks*

Graph compute engines read in graph data from graph stores and process the data for query results and analytics. They implement global graph computational algorithms. While graph databases are usually optimized for transactions (online transaction processing, or OLTP), graph compute engines are usually optimized for scanning and processing data in batches (online analytical processing, or OLAP). There are in-memory/single machine graph compute engines such as Cassovary, and distributed graph compute engines such as Apache Giraph, Apache Spark – GraphX, GraphLab, Tencent Plato, Katana Graph Engine, and Microsoft Graph Engine. Apache TinkerPop is a property graph computing framework for both graph databases (OLTP) and graph analytic systems (OLAP), and it supports both in-memory and distributed graph compute.

5.8.1.3*Machine Learning Solutions for Information Processing*

There are many Machine Learning solutions and toolkits for information processing that plays an important role in KG construction and maintenance. Some relevant popular open-source ML libraries and toolkits are discussed next.

*   Transformers: This repository contains state-of-the-art pre-trained general purpose NLP models (such as BERT, GPT-2, RoBERTa, XLM, DistilBert, and XLNet) for Pytorch and TensorFlow 2.0. In particular, it includes implementations of self-supervised learning of language representation approaches, such as ELECTRA and ALBERT for enhanced NER when labeled data are limited.
*   spaCy: It offers industrial-strength NLP in Python designed for production use. It includes pre-trained models and pipelines for common NLP tasks on 60+ languages. It is a popular open-source library for building information extraction or natural language understanding applications, as well as pre-processing text for deep learning.
*   Spark NLP: It is an NLP library built on top of Apache Spark ML. It has a rich set of more than 1,100 pre-trained pipelines and models in more than 190 languages, and supports many state-of-the-art transformers.
*   HanLP: Han Language Processing is a multilingual NLP library built on PyTorch and TensorFlow 2.x. It offers solutions for common NLP tasks including NER, syntactic and semantic dependency parsing, document classification, etc., that are relevant for KG. Version 2.1 covers 104 languages such as English and Chinese.
*   Gensim: It is a Python library for NLP tasks such as topic modelling, document indexing, and similarity retrieval. It is highly optimized in terms of memory management and distributed computing, and therefore can handle large text corpora. However, other libraries need to be leveraged for other NLP tasks not in its core strength.
*   PyTorch geometric: It is a library of methods for geometric deep learning, which deals with deep learning on graphs and other irregular structures. It includes many variants of graph neural networks including GCN, graph attention networks (GAT), graph recurrent networks (GRN), and graph autoencoders/variational autoencoders.
*   DGL (Deep Graph Library) and DGL-KE: DGL is an open-source library that implements graph neural network models, contributed by researchers at Amazon Web Services (AWS). On top of DGL, AWS developed DGL-KE, which is a set of tools for deep-graph-learning knowledge embeddings Amazon uses to power their own KGs, including the one behind Alexa’s question-answering service. DGL-KE provides different compute optimizations under different parallel computing environments, thereby improving significantly the performance of the knowledge embedding algorithms.

There are also Cloud SaaS NLP APIs for information processing. Examples include:

*   NLP on AWS: Amazon Textract automatically extracts text and data from forms and tables in handwriting and scanned documents. Amazon Comprehend is a AWS built-in tool for information extraction from unstructured data. Users can train custom ML models by providing a small sample of their own data to build customized applications for entity identification and document classification. Twinword on AWS Marketplace can identify distance, relationship, and similarity between pieces of text. AWS integrated GluonNLP, a deep learning NLP framework built on top of MXNet, with SageMaker. AWS also recently partnered with Hugging Face to bring thousands of NLP models in the Transformers library to Amazon SageMaker.
*   Google Natural Language API and AutoML Natural Language: Natural Language API includes pre-trained models for NLU applications such as sentiment analysis, entity analysis, entity sentiment analysis, content classification, and syntax analysis. AutoML Natural Language is a no-code tool for users to train and test custom ML models by simply uploading their own training data.
*   Microsoft Azure knowledge mining solutions: Azure Cognitive Search is not just a search tool but it also provides AI enrichment capability to meaningfully index unstructured data. Azure Cognitive Services includes, among other cognitive APIs, Language Understanding Intelligence Service (LUIS) for natural language text meaning prediction and information extraction, as well as Text Analytics service for sentiment analysis, key phrase extraction, and language detection. The API solutions provide access to pre-built models. Alternatively, users can also access Spark NLP to build custom models through Azure Databricks or Azure HDInsight, which offers a fully managed Spark service.

5.8.1.4*Semantic Middleware Solutions*

Semantic middleware exchanges information between applications based on semantic standards rather than simply exchanging data. It is more powerful than traditional middleware. Instead of connectors based on data schemas only, as done in traditional middleware, semantic connectors use reasoning to achieve native interoperability. Semantic middleware solutions typically leverage machine learning algorithms to extract and process information from unstructured data sources. Examples of semantic middleware and enterprise data and information integration solution providers include:

*   Anzo Platform by Cambridge Semantics: Anzo is built on top of AnzoGraph DB, Cambridge Semantics’ own graph database that uses an in-memory MPP processing paradigm and is optimized for OLAP. AnzoGraph DB supports RDF\*, LPG, and Cypher. In addition to the standard KG capabilities such as W3C standardization, knowledge query, knowledge reasoning, ontology management, and metadata management, it integrates KG with a rich set of AI/ML tools and graph algorithms for data wrangling, information extraction, KG completion, KG management, graph traversal, pattern matching, graph analytics, recommendation making, etc. Combined with built-in KG workflows, the platform enables the implementation of a data fabric for modern data integration and data management. Anzo platform forms the backbone of Anzo Smart Data Lake solutions. The platform also offers connectivity for third-party business intelligence tools such as TIBCO Spotfire, Tableau, and Microsoft Power BI.
*   PoolParty Semantic Suite by the Semantic Web Company: It offers a comprehensive semantic middleware platform for metadata management, enterprise knowledge graph management, text mining and NLP, graph automation, and semantic AI applications. It can help automate the processes to generate, use, analyze, and share metadata, including semantic metadata and active metadata, on information assets. The PoolParty Vocabulary Hub includes information and links to industry-specific taxonomies and ontologies, including knowledge models for financial services FIBO, World Bank Topical Taxonomy, XBRL, and Currencies Name Authority List. The PoolParty Semantic Suite can make direct use of these publicly available SKOS taxonomies and OWL ontologies.
*   Ontotext Platform: It provides enterprise solutions to organize information and documents into enterprise knowledge graphs. It uses text analysis and ML models to extract knowledge, annotate unstructured documents, and generate semantic metadata. It can automatically generate GraphQL access from ontologies, provide semantic search, recommendations, explainable predictions and inference, and support content enrichment and provenance tracking. Ontotext is also the inventor of GraphDB, which is a scalable graph database with strength in semantic inferencing and support for RDF\*.
*   Perfect Memory Digital Asset Management Platform: It semantically integrates digital assets for centralized management with AI/ML powered connectors to extract information from unstructured data, such as named entity recognition, video analysis, face recognition, speech to text, natural language processing, and semantic segmentation annotation, automated content annotation and enrichment, and taxonomy-based content indexation.
*   Smartlogic’s Semaphore: It is a semantic AI platform for organizing enterprise data assets to contextualize information, generate new insights, and automate business decisions. It leverages information extraction to create and manage semantic metadata and active metadata, and provides a foundation for information governance, process automation, informed analytics, and cognitive applications such as intelligent contextual search and recommendation engines to support customer experience, regulatory compliance, contract lifecycle management, and information security.

Some other solution providers in this space include Stardog, Franz, Ant Graph Intelligence Platform on Alibaba Cloud, Semantic Arts, KgBase (no-code knowledge graphs), timbr.ai, etc.

Many of the companies offering semantic middleware and enterprise data and information integration platform solutions also developed their own industry-leading graph databases such as AnzoGraph DB by Cambridge Semantics, GraphDB by Ontotext, AllegroGraph by Franz, and Stardog Enterprise Knowledge Graph platform (which is more than a graph database by its name).

5.8.1.5*Graph Visualization*

For graph visualization, some graph databases come with their own visualization tools such as Neo4j Bloom and Visual analytics environment in TigerGraph GraphStudio. Other stand-alone graph visualization tools are capable of linking with multiple graph databases. These tools include, for example:

*   Arcade, which is an enterprise-ready platform for graph visualization and analytics with enterprise level security and user level permissions. It integrates with many popular relational and graph databases (Oracle, MySQL, PostgresSQL, Neo4j, OrientDB, TigerGraph, JanusGraph, Cosmos DB, and Neptune). Its enterprise version is available on premises and on cloud (AWS and Azure). Open-source community version is free.
*   AntV G6, which is a simple, configurable, interactive, performant, and user friendly open-source JavaScript solution developed by Ant Financial.
*   Gephi, which is an open-source, Photoshop™-like tool running on Windows, Mac, and Linux. It displays graphically the graph data as well as analytics.
*   KeyLines and ReGraph, which are graph visualization toolkits from Cambridge Intelligence for JavaScript and React developers.
*   Linkurious, which offers an enterprise-ready on-premises graph visualization and analysis platform with built-in support for the leading graph databases.
*   Graphistry, which is a browser-based, GPU-accelerated, and interactive Big Data visualization and analysis tool capable of handling graph data.

5.8.1.6*Knowledge Graph-Based Search*

As the KG organizes and links all kinds of information semantically, KG can naturally facilitate intelligent contextual search. The ability to search over a KG is important to productionalize the KG. As a matter of fact, popular search engines such as Google and Bing are powered by their respective web-scale KGs, and voice assistants such as Alexa, Siri, or Google Assistant are also supported by KGs. Information in KG can be added as metadata to a smart search engine. The search can be semantic and more contextual than keyword driven only, and the search results can be ranked, organized, and annotated according to the entities and relations captured in the KG. It can also help enhance the auto-complete function of the search box.

The Cloud search APIs from Google, Amazon, and Microsoft are all integratable with knowledge graphs, so do other advanced search APIs such as Elasticsearch. For example, on AWS, a knowledge graph stored in Amazon Neptune can be added as metadata to Amazon Kendra to help find more relevant results. Neo4j has a framework for Elasticsearch to search over Neo4j KGs. Traditional on-premises search solutions are catching up with this trend. Some additional tools that can facilitate natural language search with knowledge graphs are:

*   SIREn, short for Semantic Information Retrieval Engine, integrates Elasticsearch with knowledge graphs (among other data sources) to search and visualize information. It started out as an open-source solution, but later became commercialized. SIREn is currently deployed in application areas such as law enforcement and intelligence, financial crime, cyber threat hunting, and life sciences.
*   Open Semantic Search is a free software to build custom search engine based on Apache Solr or Elasticsearch open-source enterprise-search and Open Standards for Linked Data, Semantic Web, and Linked Open Data integration. This framework allows the resulting search engine to search over KGs that adopt the Open Standards.

**5.8.2*Publicly Available Knowledge Graphs and Ontologies***

There are a slew of KGs and ontologies publicly available or accessible. They fall into two categories:

1)General purpose KGs for language, encyclopedic, and web information, which may be relevant for financial services applications.

2)Domain-specific KGs, including those specific for financial services applications.

Although some of them can be borrowed to help build EKGs, none of them provide coverage of the internal knowledge of companies.

*   Google Knowledge Graph powers Google applications such as Google Search, Google Assistant, and the Google Knowledge panel. In addition to being able to access it through individual applications, Google offers a Knowledge Graph Search API, which allows users to query entities in the Google Knowledge Graph. Google Maps is a knowledge graph, and it is also accessible through the Google Maps Platform API. Likewise, Microsoft Satori is the KG that powers Bing and Cortana, and is accessible through Bing Entity Search API.
*   BabelNet is a multilingual encyclopedic dictionary and a large semantic network with connected concepts and named entities in semantic relations, made up of about 20 million entries. Synonyms of a given meaning across a range of different languages are grouped into synonym sets or synsets. BabelNet is automatically generated and updated by integrating over a number of dictionaries, lexicons, encyclopedias, databases, and knowledge bases.
*   Wikidata by its own definition is a “free, collaborative, multilingual, secondary database, collecting structured data to provide support for Wikipedia, Wikimedia Commons, the other wikis of the Wikimedia movement, and to anyone in the world.” It is both human readable and machine readable.
*   DBpedia Knowledge Base represents an open knowledge graph built and maintained through a crowd-sourcing effort to extract structured content from the information created in various Wikimedia projects. It is multilingual and covers many domains.
*   Zhishi.me is a Chinese Linking Open Data knowledge graph extracted from the largest Chinese encyclopedias — Baidu Baike, Hudong Baike, and Chinese Wikipedia.
*   Open industry/domain-specific knowledge graphs and ontologies such as FIBO for financial business applications, ChEBI for chemical entities of biological interest, the Automotive Ontology (AUTO) for the automotive industry, and the ESCO ontology for European Skills, Competences, qualifications and Occupations, can be re-used and adapted to build customized enterprise KGs.

For financial services applications in particular, information from general purpose KGs can be used either directly for applications such as company, economic, or market research, or indirectly as sources of alternative data for ML model training in financial modeling. For example, a company profile information from Wikidata may help an analyst to identify legal entities when performing KYC due diligence. Google Map data may be used when planning for branch openings.

FIBO is a fairly comprehensive set of ontologies organized by a taxonomy starting with a domain layer, then subsequent sub-domain layers (modules), and individual ontologies at the bottom layer. FIBO domains include Business Entities, Business Process Domain, Corporate Actions and Events Domain, Derivatives Domain, Financial Business and Commerce, Foundations, Indices and Indicators, Loans, Market Data Domain, and Securities. FIBO can be accessed for either online use (via dedicated ontology tools) or offline use (download), and it is updated on a quarterly basis. In addition to FIBO, there are also other standardized knowledge models for the financial industry such as (i) World Bank Topical Taxonomy, which covers the organizational structure, subject fields, and activities of the World Bank that may be leveraged by other banks in the public and private sectors; (ii) XBRL, which is the open international standard for digital business reporting such as financial statements, and risk and performance reports; and (iii) Currencies Name Authority List, which is a controlled vocabulary of currencies, their authority codes, and labels in EU official languages. Adoption of these standards across different financial institutions can greatly enhance the interoperability of KGs within and across individual organizations.

**5.8.3*Services Powered by Knowledge Graphs***

Many successful commercial service products are offered based on KGs behind the scenes. The likes of Airbnb, Amazon, Google, LinkedIn, Uber, and Zalando all leverage knowledge graphs in their core businesses. In addition to the smart search engines and voice assistants discussed previously, two more examples of common commercial KG-based services relevant for the financial industry are discussed next.

As an inventory of all data assets with associated tags or metadata, data catalog is a key component of enterprise data and information management. Data catalog stores and organizes the metadata rather than the actual data. It can be used to link the data assets in a meaningful and intelligent way to help identify or discover data, track data lineage, manage sensitive data, and provide relevant information to assess data quality, provenance, and fitness of data for intended use. The KG can be quite an effective tool for data linking, not just in terms of tracking the explicit categorizations and connections, but also in terms of establishing the semantic links among data assets through entity recognition, relation extraction, KG completion, and KG reasoning. For this reason, a KG-assisted data catalog can do much more than a traditional rule-based catalog, and serves as a key mechanism for weaving an enterprise data fabric. Examples of commercial KG based data catalog services include:

*   Collibra Data Catalog, which is powered by Collibra’s Context Graph
*   Informatica Enterprise Data Catalog, which leverages KG and ML for data search, discovery, relations, governance, and use
*   Cambridge Semantics Anzo Smart Data Lake, which includes Anzo Catalog as one of its key components
*   data.world Cloud-native enterprise data catalog
*   Zeenea Data Catalog powered by KG and ML

In addition to these data catalog products, many semantic middleware and enterprise data and information integration solution platforms can enable the creation of and host custom semantic data catalogs.

Financial data and intelligence service providers are increasingly turning to KG not only to manage data and information internally but also to provide their clients with better structured contents and more enlightening insights. Dow Jones DNA is a ML- and KG-enabled premium news data delivery service. Such data are not just plain facts extracted from news articles but rather enriched by the interconnections in people, organizations, places, events, etc. The DNA platform offers flexible APIs to access machine-readable news, and event data tagged and structured with intelligent taxonomy and metadata. Professionally structured and curated data allow users to focus more on building their own real-time applications, such as event risk modeling, market intelligence, and investment/trading strategy, rather than spending extra time and resources on data pre-processing. In addition, with the platform’s ability to automatically screen out “fake news”, users can have more confidence in the accuracy of data received. Thomson Reuters Knowledge Graph Feed is a service powered by KG to provide multi-faceted and connected financial data. Two commercial data feed packages are available, Core Entities and Value Chain Relationships. The Core Entities package includes entities involved in capital markets, equity instruments, officers and directors, and financial markets metadata. The Value Chain Relationships package includes supplier and customer relationships, comparable companies, joint ventures and strategic alliances, and industry classification. These data and associated metadata provided by the data feed service can help analysts to obtain a holistic view of the entire landscape in respective domains, to get a more informed and connected view of individual entities, and to discover hidden connections.

**5.9Challenges and Future Directions**

Building a working KG for an agile application at a relatively small scale is not difficult nowadays, given existing technologies. However, there are quite some methodological and practical challenges in scaling up KG to wider and more complex domains and larger data sizes, as well as in applying and integrating KG within the broader information management framework.

**5.9.1*Methodological Challenges***

On the methodological front, although KG-based applications can derive better interpretability from semantic relationships captured in KG, interpretability of knowledge representation itself is still an active research area, since not all forms of knowledge representations are transparent enough for human understanding, in particular, those based on deep neural networks. The semantics generated based on such representations may need to be vetted by domain experts, especially at the ontology level.

Quality of NLP algorithms for entity/relation extractions and KG completion can have material impacts on the quality of the KG itself. Despite the fact that some state-of-the-art NER systems for the English language produce near-human performance in specific subject domains, their performance in general is not guaranteed and may be brittle. Performance of relation extraction algorithms have generally fared worse. Graph-based approaches have been proposed to take into account available information in graph form to assist entity/ relation extractions. This fits into the theme of mutual improvement between KG and ML through an iterative process.

Even though the KG is flexible and dynamic to accommodate knowledge evolution, knowledge representation of temporal entities, relations, and attributes adds another layer of difficulty. Such knowledge representation should also take into account certain time-invariant properties of the KG. Methods (e.g., \[[16](#chap5.xhtml#rref16)\]) are proposed to address temporal information embedding (by adding the time dimension to traditional embedding for example), entity dynamics, relation dynamics, and temporal logical reasoning. However, more research needs to be done in these areas.

For KG evaluation, the main difficulty associated with semantic accuracy tests is the availability of adequate labeled test samples. Some research focuses on efficient sampling design such as cluster-sampling \[[17](#chap5.xhtml#rref17)\] to lower the annotation cost, while others focus on automated generation of test cases based on common data quality test case patterns \[[18](#chap5.xhtml#rref18)\]. Beyond semantic accuracy, there are a multitude of other aspects of KG quality, such as availability, licensing, interlinking, security, performance, syntactic validity, consistency, conciseness, completeness, relevancy, trustworthiness, understandability, timeliness, interoperability, interpretability, and versatility. Depending on the use cases, some aspects may be more important than others, and they may interact with one another with respect to impact on KG quality. Each of these quality aspects requires its own set of metrics. Knowledge graph evaluation is a complex problem and in general remains an under-researched area for scalable and targeted solutions for different application requirements.

**5.9.2*Application and Integration with Other Information Systems***

When applying KG and/or integrating it with other information systems, there may be challenges in embedding KG domain knowledge and integrating KG semantics within the computational framework. Using KG to build rule-based decision/recommendation systems is relatively straightforward, but using it to inform AI/ML applications may not. It will depend on the capability of the downstream applications to handle such semantic information. For example, with existing approaches, leveraging facts and rules in KG for ML is done primarily through carefully selected Machine Learning network designs, through imposing constraints to knowledge representations and/or loss function formulation, through Machine Learning regularizations, and/or through data augmentation. These approaches tend to be soft enforcements of facts and rules in nature, and attempt to minimize the degree or probability of deviations rather than prohibiting them. Enforcing the exact KG facts and semantic rules in ML training and prediction, however, may require additional research and *ad hoc* treatment in domain specific applications.

Given the uncertainties and possible sources of error in both the KG development data and development methods, there can be potential inaccuracies in the facts extracted. The robustness of the downstream applications to the possible errors in input from KG also needs to be assessed, and the degree of error tolerance depends on individual use cases. For example, legal applications can have very different KG quality and fact accuracy requirements from those of search/ recommender systems.

**5.9.3*Practical Considerations***

EKG can be massive, and it takes time and resources to encode knowledge about complex domains and make such encoded knowledge functionally usable. Building an EKG from scratch can involve many people in many business units and support teams, and it is usually a long-term undertaking. Resource-intensive tasks include developing standardized, consistent, complete, and functional enterprise vocabularies and ontologies, identifying and aggregating structured and unstructured data from numerous data sources, training and deploying ML models to extract and embed information into KG, standardizing and merging sub-domain KGs, and evaluating and maintaining all components of EKG on an ongoing basis, etc. As such, the organization may not be able to see immediate benefits from investment, and benefits may take years to fully materialize.

It is highly recommended to build the EKG through an incremental and distributed approach. Individual business units or functional areas can build their own subdomain specific KGs first, starting small, and then build upon previous KGs incrementally according to business needs, reaping tangible benefits along the way. Finally, KGs in different sub-domains can be integrated to form the EKG. The incremental and distributed approach also enjoys positive network effect, that is, as more data sources are connected by the EKG, more new business insights and values can be generated. Building individual business unit level KGs incrementally as well as building the EKG from the ground up by integrating business unit KGs does not necessarily require refactoring or replacing the existing data applications that access the underlying data. Rather, KGs and EKG allow such applications and associated data to be reusable and integratable for other applications to derive new knowledge and insights, by linking the underlying data assets semantically. As long as the underlying KGs are built following the same standards in terms of vocabularies and ontologies, they can be easily integrated. Otherwise, standardization and conversion efforts may be required. When designing a subdomain KG, we need to take into account the balance between future extensibility versus current agility, as well as whether and how it will contribute to the EKG, and then choose the most appropriate tools such as the underlying graph databases (RDF versus LPG) and semantic platforms. Building an EKG is a long-term effort, and the EKG itself is subject to continuous improvement.

Although all data can be represented in a graph form, it may not be the most efficient to do so. Comparing with relational databases (RDB), graph databases are more efficient and effective to handle data in sparse matrices. However, RDB is usually a better choice to manage densely populated matrix data in large relational tables. Such relative pros and cons have important implications to the question of at what level of granularity we need to embed data into KG. Transforming all RDB data into KG may consume huge amounts of compute and storage resources, bloat the size of the KG, and significantly affect query performance. For unstructured data such as documents, extracting all facts stated in those documents into the KG can have similar effects. Alternatively, if we only pull these large datasets, databases, and documents into the KG as nodes together with associated metadata, the resulting KG can be much leaner and manageable. As a matter of fact, for certain applications, in particular enterprise data management, the alternative approach can be quite sufficient, effective, and efficient.

The EKG is resource-hungry in terms of both development and maintenance. It requires extensive compute, storage, and networking infrastructure along with advanced technology stacks. Cloud platforms come in handy, as users do not need to assemble required technology components from the ground up, and they can be easily scaled. Given the trade-off between computational efficiency and model expressiveness, a more semantically expressive KG requires more powerful computing resources and more efficient distributed computing platforms for graph data processing and analytics. In addition, not all steps of KG construction are easily automatable. Some may be labor-intensive. Building a KG can be an iterative process, with earlier versions of KG providing supervision for subsequent KG enhancement/augmentation, and hopefully with reduced labor each time.

Security and privacy are important considerations for KGs and EKGs. As they encompass a wide range of information about part of or the entire organization, proper policies and procedures need to be in place to govern their development, maintenance, and use. With respect to development and maintenance, the incremental and distributed approach can help restrict the developers to the parts of KG and underlying data they are authorized to work on. In terms of KG use, access rights can be granted on a need-to-know basis. Security and privacy policies can be implemented to restrict user access to subsets of the graph, metadata, or data only. Access to individual data sources can be managed separately and stay as part of the source system access control.

From the data integration point of view, a KG works differently from a a data hub. At the holistic level, the KG may serve as a virtual single source of truth, which can consist of multiple physical data hubs as well as other data sources, with each data hub serving as a materialized single source of truth. This can help the organization to strike a balance between data centralization and distribution. Centralization allows for better visibility, accuracy, standardization, and economy of scale, while distribution allows for better agility. The KG can help bridge the gap between the two. With the KG helping to connect, discover, and share data within and across data hubs, we can then physically integrate only what we need, rather than all data. For enterprise data integration purposes, KGs are built primarily on top of metadata. Although some metadata required for an effective KG may be automatically extracted, either through handcrafted rules or statistical/Machine Learning algorithms, most may still need to be curated. Therefore, the metadata collection scheme needs to be carefully designed, and rigorous effort is required of the DataOps teams to ensure availability of complete and high-quality metadata on the underlying data assets, data systems, and data applications.

KG can work with and enhance existing data or information systems and applications, rather than replacing them. It organizes, manages, and retrieves knowledge from various data and information sources. It is a structured, distributed, human understandable, and machine operable way to describe, store, find, update, delete, and derive knowledge for insights, and a key building block of many knowledge-aware applications. In the Big Data era, the KG will play a more and more prominent role in leveraging machine power to systematically and intelligently process data and information into actionable knowledge and insights. Enterprise business strategies and practices evolve continuously, and the EKG can adapt to changes in business strategy and practice easily, given its flexibility and extensibility. New business objects/concepts can be added without affecting existing data. Obsolete information can be excluded by ignoring or deleting the related nodes/edges. Updates can be made either at the conceptual level (vocabulary, taxonomy, and ontology) or at the data instance level (named entities and associated relations). The organization can reap the benefits of a well-designed, well-developed, and well-maintained EKG for as long as the business lasts.

**5.9.4*Knowledge Graph as a Universal Database for Data, Information, and Knowledge***

With the explosion of unstructured and semi-structured data alongside structured data, organizations are shifting from the traditional relational data model to the NoSQL data model for many applications, and the KG is a natural extension of this movement to allow more flexibility in data management and utilization, integrate data at a semantic level, and guide physical data integration. In a way, it is a much broader type of umbrella database which can include both relational and non-relational databases as its data/information sources. In this sense, it can be regarded as a universal database. With a well-developed KG, you can readily identify the sources of data, information, and knowledge, and drill down to such sources for further investigation when necessary. Of course, specialized databases such as RDBs, key-value stores, and document stores have specialized tools to more efficiently process and query specific types of data, which the KG may not be optimized for. So, there are still roles for them to play.

Nodes in a KG can have associated datastores (e.g., key/value) to capture additional attributes. Each of these nodes can also have its own compacted knowledge graph (termed semantic footprint) capturing connected metadata associated with this node. Semantic footprints can be considered as digital twins of underlying data/document sources.

Queries can be satisfied at the ontology level, at the metadata level, through inference, or at the underlying data instance level. Therefore, a 2-step query design may be implemented with the KG, if the KG also includes databases, datasets, or documents as nodes with associated metadata. First in Step 1, we can perform a graph query over KG ontology, metadata, and inference. If the desired information is found, then the query is satisfied. Otherwise, we can search the metadata to identify the likely sources of requested information and move on to the next step. In Step 2, we query the individual identified data sources for results, using the query tools associated with these data sources (SQL for RDB, NoSQL for nonrelational, graph query languages for graph databases, etc.). The second level querying may be implemented and automated, for example with GraphQL, which is an open-source API query language and runtime. Despite its name, GraphQL is really a general purpose tool that is largely agnostic of the underlying data structure of the target APIs, not just those associated with graph databases. This decoupling of KG querying and underlying source data querying allows KG users not to worry about changing their semantic queries every time the schema of the source data changes. The changes to source data schema and the translation of the user query to source data query can be handled by GraphQL. Of course, for this 2-step scheme to work successfully, it will require carefully designed and curated metadata that fit the query type.

**5.10Conclusion**

In summary, the KG is a powerful tool in its own right to systematically and semantically link all data and information within a business domain to generate better and faster business intelligence. It has many practically applications, including a large variety of financial industry applications, that can add significant business values. Its most prevalent application at the present time is perhaps semantic integration of business data, where it is not only convenient but also effective for data, information, and knowledge management, and new insight generation at the enterprise scale. In addition, the combination of KG and ML provides a practical approach to neurosymbolic AI, which integrates knowledge representation, Machine Learning, and logical reasoning for more effective, interpretable and trustworthy next generation of AI.

**References**

[1](#chap5.xhtml#ref1).D. A. Nelson and B. N. Rossiter. “Prototyping a Categorical Database in P/FDM,” in *Advances in Databases and Information Systems. Workshops in Computing,* J. Eder, L.A. Kalinichenko, Eds. London, UK: Springer, 1996, pp. 432–456.

[2](#chap5.xhtml#ref2).The International Consortium of Investigative Journalists. “The Panama Papers: Exposing the Rogue Offshore Finance Industry,” \[Online\]. Available: [https://www.icij.org/investigations/panama-papers/](https://www.icij.org/investigations/panama-papers/)

[3](#chap5.xhtml#ref3).T. Liebig. “Neo4j: A Reasonable RDF Graph Database & Reasoning Engine \[Community Post\].” [https://neo4j.com/blog/neo4j-rdf-graph-database-reasoning-engine/](https://neo4j.com/blog/neo4j-rdf-graph-database-reasoning-engine/), February 27, 2018.

[4](#chap5.xhtml#ref4).S. Purohit, N. Van, and G. Chin. *Semantic Property Graph for Scalable Knowledge Graph Analytics* \[Online\]. Available: [https://arxiv.org/abs/2009.07410](https://arxiv.org/abs/2009.07410), 2020.

[5](#chap5.xhtml#ref5).D. McCreary. Enterprise Knowledge Graph 2020 \[Online\]. Available: [https://dmccreary.medium.com/enterprise-knowledge-graph-2020-58fc0c494f7c](https://dmccreary.medium.com/enterprise-knowledge-graph-2020-58fc0c494f7c), 2020.

[6](#chap5.xhtml#ref6).H. Wang, K. Qin, R. Y. Zakari, G. Lu, and J. Yin. Deep Neural Network Based Relation Extraction: An Overview \[Online\]. Available: [https://arxiv.org/abs/2101.01907](https://arxiv.org/abs/2101.01907), 2021.

[7](#chap5.xhtml#ref7).W. Xiong, T. Hoang, and W. Y. Wang. DeepPath: A Reinforcement Learning Method for Knowledge Graph Reasoning \[Online\]. Available: [https://arxiv.org/abs/1707.06690](https://arxiv.org/abs/1707.06690), 2018.

[8](#chap5.xhtml#ref8).Y. Liu, M. Hildebrandt, M. Joblin, M. Ringsquandl, R. Raissouni, and V. Tresp. Neural Multi-Hop Reasoning with Logical Rules on Biomedical Knowledge Graphs \[Online\]. Available: [https://arxiv.org/abs/2103.10367](https://arxiv.org/abs/2103.10367), 2021.

[9](#chap5.xhtml#ref9).M. Chen, W. Zhang, W. Zhang, Q. Chen, and H. Chen. Meta Relational Learning for Few-Shot Link Prediction in Knowledge Graphs \[Online\]. Available: [https://arxiv.org/abs/1909.01515](https://arxiv.org/abs/1909.01515), 2019.

[10](#chap5.xhtml#ref10).A. Borghesi, F. Baldo, and M. Milano. Improving Deep Learning Models via Constraint-Based Domain Knowledge: A Brief Survey \[Online\]. Available: [https://arxiv.org/abs/2005.10691](https://arxiv.org/abs/2005.10691), 2020.

[11](#chap5.xhtml#ref11).Z. Wu, S. Pan, F. Chen, G. Long, C. Zhang, and P. S. Yu. A Comprehensive Survey on Graph Neural Networks \[Online\]. Available: [https://arxiv.org/abs/1901.00596](https://arxiv.org/abs/1901.00596), 2019.

[12](#chap5.xhtml#ref12).N. Muralidhar, M. R. Islam, M. Marwah, A. Karpatne, and N. Ramakrishnan. “Incorporating Prior Domain Knowledge into Deep Neural Networks,” presented at the 2018 *IEEE Int. Conf. Big Data (Big Data).* 2018, pp. 36–45.

13.T. Li and V. Srikumar. Augmenting neural networks with first-order logic. \[Online\]. Available: [https://arxiv.org/abs/1906.06298](https://arxiv.org/abs/1906.06298), 2019.

[14](#chap5.xhtml#ref14).M. Fischer, M. Balunovic, D. Drachsler-Cohen, T. Gehr, C. Zhang, and M. Vechev, “DL2: Training and querying neural networks with logic,” presented at the *Proc. 36th Int. Conf. on Machine Learning,* 2019, Vol. 97, pp. 1,931–1,941.

[15](#chap5.xhtml#ref15).Semantic Web Company. “What is Semantic AI? The Fusion of Machine Learning and Knowledge Graphs” \[Online\] Available: [https://www.poolparty.biz/semantic-ai](https://www.poolparty.biz/semantic-ai)

[16](#chap5.xhtml#ref16).B. Yu, H. Yin, and Z. Zhu, “Spatio-temporal graph convolutional networks: A deep learning framework for traffic forecasting,” presented at the *Proc. 27th Int. Joint Conf. Artificial Intelligence,* 2018, pp. 3,634–3,640.

[17](#chap5.xhtml#ref17).J. Gao, X. Li, Y. E. Xu, B. Sisman, X. L. Dong, and J. Yang, “Efficient knowledge graph accuracy evaluation,” presented at the *Proc. VLDB Endowment,* 2019, Vol. 12, Issue 11, pp. 1,679–1,691.

[18](#chap5.xhtml#ref18).D. Kontokostas, P. Westphal, S. Auer, S. Hellmann, J. Lehmann, and R. Cornelissen, “Test-driven Evaluation of Linked Data Quality,” presented at the *Proc. 23rd Int. Conf. World Wide Web,* 2014, pp. 747–758.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0006](https://doi.org/10.1142/9789811250903_0006)

Chapter 6

**Migration from the Traditional Financial Markets to a World of Digital Assets**

***Philea Chim and Frank Tong***

**6.1Rise of Digital Assets**

Since the introduction of the Bitcoin in 2008, the world has become fascinated with Blockchain and the wider topic of distributed ledger technologies (DLT). The immutable feature of DLT provides a level of security not achievable in the past, which gives rise to a myriad of use cases, in particular, in the financial industry. The spiking prices of Bitcoin and the emergence of numerous cryptocurrencies have quickly caught the attention of both retail and institutional investors. The daily trading volume from just the top 10 crypto exchanges reached $250 billion this year. With such popular demand, even the traditional financial institutions are aggressively considering crypto assets as alternative investment products to offer to their clients.

Digital assets, however, are not limited to cryptocurrencies. The concept of tokenization, coupled with DLT, offers a new paradigm to the financial market. Digital tokens can be created on a distributed ledger or Blockchain to represent assets. The underlying asset can be digital or physical, and can be anything from equities to real estate, to account receivables. Tokenization allows for the denomination of assets into fractional ownership, thus providing more liquidity to the market as a much larger audience of investors can have access. Assets once considered illiquid and not available to the mass market investor can now be traded in the secondary market. Basket of securities can also be tokenized to create new financial products. Tokenized securities are cheaper, more secure, and less burdensome to issue.

Non-fungible tokens (NFT) is another form of digital assets, created to represent ownership and certify the uniqueness of an asset. The data is stored on a distributed ledger or Blockchain to ensure immutability, and is becoming popular for art, gaming, music, and intellectual properties. NFT has the potential to introduce unconventional but valuable assets, like art, to be traded just like other regular financial products in the market.

DLT not only enables new innovations, it also creates more digital channels for the distribution of new and traditional assets.

**6.2DLT and Financial Markets**

The global financial markets represent over one quadrillion US dollars of assets (see [Figure 6.1](#chap6.xhtml#fig6-1)), consisting of $71 trillion in stocks, $255 trillion in bonds, and $640 trillion in derivatives. In addition, there are $20 trillion in commodities, $17 trillion in trade finance, $289 trillion in real estate, and $3.6 trillion in private debt and private equity. All of these traditional market products could potentially be digitized, tokenized, and traded using DLT.^([1](#chap6.xhtml#rfn1)) As a comparison, the entire cryptocurrency market today is only about $2 trillion; there is enormous scope and potential for the digital assets market to grow.

![](images/p216.jpg)

**Figure 6.1.**Global financial market size in comparison. Courtesy of QBN Capital

The debt capital market (DCM) which comprises mostly bonds, presents a huge opportunity for DLT and tokenization. The current bond issuance process is archaic and fragmented. There is not a single solution that covers the entire value chain and there is no economies of scale. Bond issuance today is costly, opaque, non-user-friendly, and inefficient. The bond issuing parties are not connected to each other as each party adopts their own proprietary systems. There exist opportunities for automation with a DLT-based platform that integrates pre-trade, front/middle/back offices, pricing, and post-trade, to significantly reduce time and cost. The system will bring borrowers, banks, investors, and regulators onto the same platform; each step of the transaction will be recorded on the Blockchain which all parties can access for price discovery, regulatory monitoring, trading, and settlement.

Currently, most of the bond subscribers are institutions and trading over-the-counter (OTC). DLT-based platforms can greatly enhance the secondary market for bond trading by eliminating counterparty risks and offering faster settlement. Digital issuance also has the potential to democratize the bond market, allowing small- to medium-sized bonds, which would otherwise be too costly to launch, to be issued and traded in the market.

The US debt capital market is long established and sizeable. It is much less so in the rest of the world. As banks and corporates in Europe and Asia move towards more bond issuance, they are also taking the lead to adopt new technologies and transform the bond market into one that matches up to the new digital age. The world’s first issuance of a US$300 million digital bond took place in Singapore in 2020 by HSBC and Temasek on SGX’s digital asset issuance, depository, and servicing platform. Huge opportunity awaits Hong Kong, with China being the second largest bond issuing country in the world. Currently, the offshore uptake of Chinese bonds through the Bonds Connect in Hong Kong is still very low — the market is ripe to be disrupted.

Another example of a traditional financial activity that can become a viable digital asset is fund trading. Current fund trading practice involves stages: (i) equity trade execution, (ii) clearing, (iii) settlement, and (iv) asset servicing by fund managers, fund service providers, and fund distributors. The investors purchase the funds through exchanges or OTC. This is followed by registration and settlement with the central securities depository and the central counterparty clearing houses. For investors, fund purchasing can be expensive and the process is often opaque. For fund managers, there is severe competition and a long chain of processes adding costs and risks. For the fund service providers and distributors, their margin is further squeezed due to the slow and costly antiquated processes. DLT-based fund trading platforms will drastically change the scene. Several traditional fund houses have already joined this movement towards DLT fund trading. Eventually, tokenized funds can also be traded with high transparency in secondary markets.

Trade finance has a long history of existence, and much of the process today is still the same as it was in the Victorian times. Traditionally, the lack of trust between buyers and sellers means that intermediaries, the banks, and often more than two, were involved. The back and forth of documentation both for the trade and for the financing is costly and inefficient, with multiple versions of the information being passed around. Today, DLT has enabled trade documents to be digitized and recorded on the Blockchain. Parties can come onto the same platform and receive the same single version of truth. This dramatically reduced the amount of administrative work, increasing efficiency and reducing cost. Having one unified document with all changes tracked and traceable also enhances security and compliance. Many consortiums have been formed to use DLT in trade finance — Contour, Komgo, Marco Polo, to name but a few. As documents and the financing process are being digitized and moved onto DLT platforms, it is not inconceivable that trade finance — invoices — can also be tokenized and traded in the secondary market.

**6.3Market Infrastructure and Regulations**

With all kinds of digital assets coming into the market, a new form of trading platform — security token exchanges (STX) — has become necessary. With the same operating principle as traditional exchanges, STX requires extensive system architecture, but the infrastructure build will be simpler, thanks to the availability of new technologies. The prerequisite for the ecosystem is to have services across the entire token life cycle from minting, trading, custody, to destruction. Like traditional exchanges, STX requires brokers, liquidity providers, asset management (funds and structured products), and other financial services support, in particular, legal, insurance, and auditing. The ecosystem must include the operations of central securities depositories and the central counterparty clearing houses. DLT will make the clearing and settlement process much simpler, faster, and cheaper.

For better illustration, [Figure 6.2](#chap6.xhtml#fig6-2) outlines the relationship and the process flows of different parties in a traditional exchange and one based on DLT, which is self-explanatory.

The financial services industry has long been tightly regulated. If digital assets are to become regular financial products in the market, they will be no exception and are subject to the same level of regulatory scrutiny. Tokenized securities, in the eyes of regulators, are simply the digital version of traditional, regulated securities.

Jurisdictions are taking on DLT and STX at a different pace, but most of them take references from the European Union and the US regulators for their advanced and comprehensive financial laws. The UK’s Financial Conduct Authority, Switzerland’s FINMA, and Germany’s BaFin are granting Multilateral Trading Facility licenses for the operating of STXs. Hong Kong’s Securities and Futures Commission has started to issue Automatic Trading System licenses to STX operators. The Monetary Authority of Singapore (MAS) is giving out corresponding licenses to operate STX. Other jurisdictions such as Gibraltar, Abu Dhabi Global Market, Labuan of Malaysia, etc., are also active participants.

**6.4Significance of the Central Bank Digital Currency (CBDC)**

Research shows that 80% of the world’s central banks^([2](#chap6.xhtml#rfn2)) are seriously looking into DLT-based Central Bank Digital Currency (CBDC) (see [Figure 6.3](#chap6.xhtml#fig6-3)).^([3](#chap6.xhtml#rfn3)) There are many benefits in having a CBDC. Firstly, a stable coin like the CBDC has far-reaching implications on any currency monopoly and the diversification of payment methods. Secondly, a DLT-based solution can significantly reduce the time it takes to conduct cross-border settlement, thus reducing the capital requirement from the correspondent bank and the load on their balance sheet.

![](images/p220.jpg)

**Figure 6.2.**Comparison in process flow in traditional and securities token exchange ecosystem. Courtesy of Archax Limited

![](images/p221.jpg)

**Figure 6.3.**Global central banks on CBDC progress. Courtesy of Our Hong Kong Foundation

The year 2020 was an important year, with the pilot launch of the Chinese CBDC, known as eCNY. This is the world’s first CBDC to focus on retail users, in addition to the highly sought-after wholesale capabilities. Starting with 5 Chinese cities initially, the pilot scheme has already been extended to 10 Chinese cities. In addition, a pilot on cross-border settlement is being carried out by the Hong Kong Monetary Authority, the Bank of Thailand, the UAE, and the People’s Bank of China, in a mCBDC project with the Bank of International Settlements (BIS).^([4](#chap6.xhtml#rfn4))

Beyond retail, the CBDC could potentially be used for financial market transactions. Once tokenized, bonds, funds, derivatives, commodities could be issued and traded in CBDC. With the immutable and traceable features of the DLT-based architecture, the CBDC could provide the additional functions of market monitoring to minimize fraud and prevent malicious attacks. All these require the setting up of the corresponding token handling infrastructure and ecosystem.

**6.5Looking Forward**

Since “Blockchain” became a household term a decade ago, there has been a significant increase in the adoption of crypto assets by the general public. From “only the geeks know crypto”, to the retail layman and the established institutions all getting involved, the trend has spread fast. This has also motivated governments to accelerate their regulatory efforts on crypto-related activities. While DLT has the potential to liberate the financial industry, central banks and regulators must take on the leadership role to establish rules and boundaries to protect the financial system as well as investors. The old legacy systems are not going to be replaced overnight; market participants need to ensure there is a seamless bridge between the traditional capital markets and the digital financial markets that are becoming more prominent.

Like the Internet in the early 2000s, DLT has irreversibly changed the financial industry, and this revolution will carry on in the coming years.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap6.xhtml#fn1)World Economic Forum. *Digital Asset, DLT and the future of Capital Markets.* (2021). Accessed: September 2021. \[Online\]. Available: [http://www3.weforum.org/docs/WEF\_Digital\_Assets\_Distributed\_Ledger\_Technology\_2021.pdf](http://www3.weforum.org/docs/WEF_Digital_Assets_Distributed_Ledger_Technology_2021.pdf)

[²](#chap6.xhtml#fn2)Bank for International Settlement. *Central bank digital currencies for cross-border payments.* (2021). Accessed: September 2021. \[Online\]. Available: [https://www.bis.org/publ/othp38.pdf](https://www.bis.org/publ/othp38.pdf)

[³](#chap6.xhtml#fn3)Our Hong Kong Foundation. *Central Bank Digital Currency — The Cornerstone of Digital Financial Infrastructure.* (2021). Accessed: October 2021. \[Online\]. Available: [https://ourhkfoundation.org.hk/sites/default/files/media/pdf/20210910\_CBDC\_report\_E.pdf](https://ourhkfoundation.org.hk/sites/default/files/media/pdf/20210910_CBDC_report_E.pdf)

[⁴](#chap6.xhtml#fn4)Bank for International Settlement. *Multi-CBDC arrangements and the future of cross-border payments.* (2021). Accessed: September 2021. \[Online\]. Available: [https://www.bis.org/publ/bppdf/bispap115.pdf](https://www.bis.org/publ/bppdf/bispap115.pdf)

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0007](https://doi.org/10.1142/9789811250903_0007)

Chapter 7

**Central Bank Digital Currencies: Opportunities and Challenges in the Post-pandemic Era**

***Steven Hu***

**7.1Introduction**

Before the COVID-19 pandemic emerged, we had already seen the warning signs of a slowdown in the world economy. The inversion in the yield curve of sovereign debt securities in the US happened in 2019, indicating a liquidity pressure in the markets. Brexit and the trade war between China and the US have added to the uncertainties in the economic environment. Many countries were also facing challenges in their structural reforms.

The outbreak of the COVID-19 pandemic has only exacerbated the situation, causing a severe impact to supply chains and its output. Waves of shocks have arrived, disrupting the supply and demand of the economies. On the one hand, there has been a sharp drop in domestic and global demands for goods and services due to lock-downs and mobility restrictions. On the other hand, many materials and products could not reach where they are most wanted, on account of the curtailment of businesses. In addition, big shifts in stock markets were happening. The FTSE, Dow Jones Industrial Average, and the Nikkei all experienced significant plummets as the number of COVID-19 infection cases increased. The aggravated economic challenge has resulted in job losses or pay cuts for millions of people. According to the US Bureau of Labor Statistics, the unemployment rate declined from 2010 to 2019, recuperating from the last crisis. However, the number quickly climbed to 13% in May 2020 as the virus became widespread \[[1](#chap7.xhtml#rref1)\]. Things are not going well on the other side of the continent either. According to the Ministry of Trade and Industry (MTI), COVID-19 has significantly affected sectors including air transport, accommodation, and other tourism-related sectors in Singapore \[[2](#chap7.xhtml#rref2)\]. There is no doubt that the COVID-19 pandemic has caused substantial damages to the world. In response to the pandemic, governments around the world have announced a raft of support packages to help businesses and citizens tide through this difficult time. The stimulus packages have been effective to offer temporary relief to the businesses and individuals who were badly hit (see the summary of policy responses from 197 countries by IMF at \[[3](#chap7.xhtml#rref3)\]). The mass vaccine program started in December 2020 has offered hope to millions of people wanting to return to a normal life. However, as of June 8, 2021, only about 12% of global population had received at least the first dose of the vaccine \[[4](#chap7.xhtml#rref4)\]. The vaccine rollout is also facing challenges of global shortage and unequal distribution. Scientists have warned that the COVID-19 herd immunity is probably impossible even with vaccination efforts in full force \[[5](#chap7.xhtml#rref5)\]. Unfortunately, the fight against COVID-19 can become an ongoing one. World leaders, academics, and industry players are exploring many options, leveraging new technologies, in order to resume economic activities gradually.

Central Bank Digital Currencies (CBDCs) are one among the innovations being actively discussed and debated. [Figure 7.1](#chap7.xhtml#fig7-1) is the Google Search Trend of CBDCs from April 2014 to May 2021, which shows a clear jump of interest-over-time since January 2020 onwards.

CBDCs present opportunities in the post-pandemic era in a number of ways. Firstly, the government can use digital currencies to pay out stimulus packages in reduced time and cost. This is particularly effective when reaching out to the unbanked community. In addition, CBDCs can help ensure a competitive payments landscape. As our lifestyle changes to digital and online, concentration risk and data privacy concerns due to the monopoly of data behemoths are worrying to governments and citizens. CBDCs can benefit the payment efficiency by creating contestability in the market. In an extreme situation, the CBDCs can also perform the role of redundancy system. Other opportunities include seigniorage retention, as well as the potential to be a new monetary policy tool — should the CBDCs are designed to be interest-bearing. What makes CBDCs different than prior trials is really the new imaginations provoked by the combination of smart contracts and blockchain technology. The programmability of money with the immutability of records present a revolutionary view of how we conceive money, interest rates, and debts, offering a glimpse into the futuristic financial infrastructure. That said, there are hurdles to overcome, ranging from technological issues and business implications to the legal challenges. Importantly, CBDCs need to find a “killer application” and a viable financing option that can sustain the development, in the face of advances in technology and innovation. Trust, a given property in CBDCs, alone does not warrant an automatic success in the user adoption in the longer term. The transition risk also needs to be carefully managed in order to mitigate the potential disruptions to strategic priorities and resource planning in commercial banks.

![](images/p225.jpg)

**Figure 7.1.**Google search trend of CBDCs

This chapter aims to give an overview of the state-of-the-art development in CBDCs in the context of the ongoing COVID-19 pandemic. [Section 7.1](#chap7.xhtml#h7-1) introduces the definition and taxonomy of framework and explains the differences between wholesale and retail CBDCs. The latest global development in this field is also provided. [Section 7.2](#chap7.xhtml#h7-2) presents prevailing motivations that central banks have when embarking on the journey. In [Section 7.3](#chap7.xhtml#h7-3), after a review of the smart contracts and Blockchain, the key requirements of Blockchain-based CBDCs will be discussed. We will also give an overview of the framework of integrating CBDCs to banks. [Section 7.4](#chap7.xhtml#h7-4) lays out the key challenges of CBDCs development, including the availability of technology, balance sheet implications, legal challenges, the search of a “killer application”, and viable financing options. We will use two anecdotes to tap into the prior knowledge and experiences in developing CBDCs. [Section 7.5](#chap7.xhtml#h7-5) presents a case study of Project Ubin in Singapore. This chapter ends by drawing a conclusion in [Section 7.6](#chap7.xhtml#h7-6).

**7.1.1*Definitions of CBDCs***

For decades, central banks issue two types of money: (i) cash in the form of physical bank notes and coins, as well as (ii) bank reserves in the electronic format. Both represent claims liabilities on central banks book. Cash is publicly accessible and accepted as legal tender according to local laws. No interests are paid for cash. As a bearer instrument, the parties involved in cash transactions are anonymous. Once cash changes hands, the settlement is final and irreversible. No central party is in place to perform ledger keeping — each party is responsible for its own records. In fact, cash resembles many characteristics of distributed payment system.

Bank reserves are accessible to authorized banks and financial institutions, and book-kept in the accounts maintained at the central bank. In many countries, bank reserves are interest-bearing, for example in the US. The balances of bank reserves are typically used for inter-bank payment settlement. The participants in inter-bank systems are pre-registered, validated, and authorized by the central bank in order to access and conduct transactions in the financial market infrastructure. Typically, the transactions are settled in a Real-Time Gross Settlement (RTGS) system run by the central bank or its authorized entity. In Singapore, the MAS Electronic Payment System (MEPS+) is the RTGS system implemented and operated by MAS, supporting large-value local currency inter-bank funds transfer and the settlement of script-less Singapore Government Securities. In many countries, RTGS systems are in place to facilitate the countless payment settlement transactions on a daily basis.

Both cash and bank reserves are central bank liabilities and are considered to be “risk-free”.

Central Bank Digital Currencies (CBDCs) are a recent innovation in money, on top of cash and bank reserves. In discussing CBDCs, it is important to be clear on what it entails, especially when central banks are already issuing monies in electronic format. CBDCs are largely hypothetical and in research stage, thus no universally accepted definition of CBDCs is available to-date. Back in 2014, Zhou Xiaochuan, former Governor of the People’s Bank of China, led the detailed engineering, design, and policy work required to digitize the sovereign Chinese Yuan. However, to the author’s best knowledge, the term “CBDCs” was coined by researchers in the Bank of England and first appeared in a speech made by Ben Broadbent, the bank’s deputy governor of monetary policy, as early as 2016 \[[6](#chap7.xhtml#rref6)\]. The present concept is largely inspired by blockchain-based cryptocurrencies, such as Bitcoin, but CBDCs are dissimilar to cryptocurrencies, as in they are issued by the central bank. There are also significant differences between cash, bank reserves, and CBDCs. This innovation in money has the potential to supplement the existing brick and mortar monetary system, enabled by the new digital technologies and processes. In what follows, we attempt to draw upon the current literature and explain the key concepts related to CBDCs. In the rest of this chapter, the abbreviation of “CBDCs” is used to denote Central Bank Digital Currencies.

Fundamentally, CBDCs must fulfill three functions of money: (i) secure store of value, (ii) stable unit of account, and (iii) costless medium of exchange.^([1](#chap7.xhtml#rfn1)) There exists proliferated literature with varying wordings in CBDCs definitions, considering the structure and access, token- or account-based, interest-bearing, and level of anonymity. The definition has since evolved in the past few years. [Table 7.1](#chap7.xhtml#tab7-1) presents the wordings in some highly cited research papers. A clear trend of convergence and maturity is obvious, thanks to growing interests and active development in the field.

**Table 7.1.**Definitions of Central Bank Digital Currencies (CBDCs)

![](images/p228.jpg)

What stands out from [Table 7.1](#chap7.xhtml#tab7-1) is that more recent attention has focused on the provision of CBDCs to “the larger public”, i.e., in retail applications, possibly due to its significant implications. More technical definition is also given by central banks, such as People’s Bank of China, highlighting the Chinese central digital currency “e-CNY” (a.k.a., “DC/EP”) is a substitute of M0^([2](#chap7.xhtml#rfn2)) money supply. Among all, the definition in \[[11](#chap7.xhtml#rref11)\] is rather descriptive than definitive, emphasizing the dissimilarity to existing form of central bank money. The significance is that it can cover a broader context, including both retail and wholesale, giving rise to a more complete taxonomy of money.

**7.1.2*CBDCs Taxonomy***

Early investigations in CBDCs have focused on the typology of the money flower given by Bank of International Settlement (BIS), as shown in [Figure 7.2](#chap7.xhtml#fig7-2).

![](images/p229.jpg)

**Figure 7.2.**The Bank of International Settlement money flower: A taxonomy of money \[[11](#chap7.xhtml#rref11)\].

[Figure 7.2](#chap7.xhtml#fig7-2) provides some useful perspectives putting CBDCs in the wider context of money. The taxonomy in [Figure 7.2](#chap7.xhtml#fig7-2) classifies money based on four dimensions: (i) accessibility (public or restricted), (ii) issuer authority (central bank or private), (iii) form (digital or analog), and (iv) technology (token- or account-based) \[[11](#chap7.xhtml#rref11)\]. The first three dimensions are intuitive to understand, but the last may require elaborations for the sake of clarity. Both token- and account-based money exist in our current monetary system. Token is a transferable asset that carries instant redeemable value. The physical bank note is an example of a token, as in the value can be transferred from one party to the other instantaneously. As such, no “clearing” process occurs before the obligations are settled. In other words, the steps of “clearing” and “settlement” are combined into one. As a result, there is no intermediary required to perform calculations and reconciliation as part of the transaction processing. In contrast, account-based money concerns electronic money centrally managed by an account servicing institution, such as a bank. Money goes through an intermediary for balance check and update. In the case of bank reserves, the transactions are recorded in the accounts in the ledge kept by the central bank. Another dissimilarity is that the responsibility of verifying the validity of the payment object lies with the receiver. In the example of cash, the receiver should ensure no counterfeiting of bank notes before the acceptance. Cash is spent instantaneously when the payment object changes hand. From the performance perspective, token-based money is less efficient than account-based money but is able to support peer-to-peer transactions with greater anonymity. In today’s world, the majority of financial transactions are performed using accounts maintained by banks. To a great extent, payment innovation is about innovative solutioning in the creation and enhancement of account structures, account types, and the management of account-related processes. It is worth noting that CBDCs can be both token-based, leveraging the blockchain and cryptographic technologies, but also account-based under the centralized management by financial institutions or by central banks directly. What is also interesting about [Figure 7.2](#chap7.xhtml#fig7-2) is that it highlights two types of non-central bank money — (i) bank deposit and (ii) privately issued digital money. Privately issued money includes crypto-based Bitcoin, Ether, and stablecoins.

Next, let us consider the funds flows between various types of money as a system. In [Figure 7.2](#chap7.xhtml#fig7-2), cash circulates back to the central bank systems via bank deposits held on commercial banks. As a matter of fact, no effective conduits exist to channel back the liquidity from privately issued digital money to the existing banking systems at the comment. Frictions are intended due to the concerns on Anti-Money Laundering (AML), Counter Terrorism Financing (CTF), and payment transparency requirements, in short of regulatory clarity in a global context. Some banks ban customers from accessing private issued digital money \[[15](#chap7.xhtml#rref15)\]. However, the liquidity can still find its way owing out of the existing bank deposits, imposing a risk of liquidity crunch. If more privately issued digital money gain the critical mass of adoption, it may also lead to an undesired state of hyperinflation. In the short-term future, we may start to witness the bifurcation in approaches in the industry — bank it or regulate it.

Following the afore-going taxonomy, we propose a topology as shown in [Figure 7.3](#chap7.xhtml#fig7-3), focusing on the categorization of CBDCs. With this, we will conveniently investigate the various initiatives using the tree diagram representation.

![](images/p231.jpg)

**Figure 7.3.**A tree representation of CBDCs taxonomy.

In [Figure 7.3](#chap7.xhtml#fig7-3), the branches (a) to (n) are used to represent the different money categories. For instance, branch (a) is central bank issued account-based digital money for wholesale application, i.e., bank reserves. CBDCs are represented in branches (b), (g), and (i). Cash, denoted in branches (m) and (n), would continue to exist, issued by either central banks or commercial banks (e.g., HK dollar bank notes). Interestingly, branch (b) reflects a recent step taken by JP Morgan, DBS, and Temasek Holdings to create a blockchain-based shared platform for payments, trade, and foreign exchange settlement, all using commercial bank digital currencies \[[16](#chap7.xhtml#rref16)\]. It is also worthwhile pointing out that technology is not an explanatory variable for the output category in [Figure 7.3](#chap7.xhtml#fig7-3). In the next section, we will discuss the wholesale and retail CBDCs in greater details.

**7.1.3*Wholesale and Retail CBDCs***

Wholesale CBDCs, as shown in branches (a) and (d) in [Figure 7.3](#chap7.xhtml#fig7-3), are digital currencies similar to the arrangement of settlement accounts at central banks. It allows restricted access to pre-registered financial institutions, issued, stored, and updated by the central banks or designated operators by the central banks. Such digital currencies have no anonymity requirements and can guarantee counterparty data privacy, reducing design complexities. Wholesale CBDCs can help improve the efficiency and reduce the costs for payments settlement. For example, it may open up more opportunities if CBDCs are integrated to blockchain-based ecosystems, facilitating the cash leg of settlement, for example in MarketNode (bond issuance and asset servicing platform) and Contour (trade finance platform). Due to growing interest, central banks are exploring ways to join forces in developing an interoperable wholesale CBDCs framework, for example the m-CBDC Bridge initiative \[[17](#chap7.xhtml#rref17)\].

To a certain extent, wholesale CBDCs can be considered as substitutes of the bank reserves, giving rise to re-imaginations of the RTGS systems. The Project Ubin in Singapore has demonstrated the technical feasibility of CDBCs with RTGS functionalities. The project pointed out that the decentralized infrastructure may require further investigations in the roles of central banks, from the perspectives system governance, liquidity management, service level agreement governor, and system auditor and mediator. Similar to other experiments, the investigation in Project Ubin has assumed zero interest-bearing condition. More studies are required to understand the policy implications if there exists an interest rate gap between reserves and the new CBDCs arrangement.

Next, as shown in branches (g) and (j) in [Figure 7.3](#chap7.xhtml#fig7-3), the retail CBDCs are accessible to the individuals, households, and businesses in consumer use cases. Retail CBDCs can help reduce the production cost of cash, serve as a redundancy of private e-money systems, and improve financial inclusion, just to name a few. The designs of retail CBDCs are relatively more complex, on account of deeper implications to the participants and financial system. That said, from the user experience perspective, the end users can access their CBDCs using wallets (software or hardware), cards, or other applications provided either by central banks or its designated entities. The design parameters of retail CBDCs include interest-bearing or not, token- or account-based data model, circulation mechanism, legal basis, and technology. In this regard, China is taking the lead in the development of digital Yuan, also known as the e-CNY (initially named as “DC/EP”) \[[18](#chap7.xhtml#rref18)\]. Users need to use wallets to access the digital currency. Financial institutions facilitate the issuance and return of CBDCs, leveraging the experiences, risk management practices, and technology from the private sector. The e-CNY is non-interest-bearing and not a replacement of cash; thus e-CNY will unlikely become a new monetary policy tool. Also, the pseudo-anonymity also equips governments with stronger capabilities in the surveillance and control of money flows to fight corruption, catch tax evasion, and other illicit activities.

Unlike wholesale CBDCs experiments, the development of retail CBDCs has centered around the study on economic consequences of a state-granted, widely accessible, electronic, 24/7, and interest-bearing access to central banks’ balance sheet. We present the key similarities and differences between wholesale and retails CBDCs in [Table 7.2](#chap7.xhtml#tab7-2).

The global development status of wholesale and retail CBDCs is presented in [Figure 7.4](#chap7.xhtml#fig7-4). Interested readers are kindly referred to the references herein for more details \[[19](#chap7.xhtml#rref19)\]. The definitions and taxonomy of CBDCs will continue to evolve and expand, as the research community garners more understandings in this new form of money. Constructive debates are beneficial to provide inputs and formulate recommendations to the central banks, governments, and other stakeholders.

**Table 7.2.**Retail versus wholesale CBDCs

| **Attributes** || **Retail CBDCs** || **Wholesale CBDCs** |
| --- | --- | --- |
| Accessibility || public || restricted |
| --- | --- | --- |
| Interests bearing || feasible || feasible |
| Anonymity || pseudo || not required |
| Blockchain-based || unsuitable || feasible |
| Tokenization || infeasible || feasible |
| Policy implications || complex || medium |
| Tech. complexity || high || medium |
| Availability || 24/7 || 24/7 |
| Programmability || feasible || feasible |

![](images/p234.jpg)

**Figure 7.4.**Global development landscape of CBDCs

**7.2Motivations and Opportunities**

**7.2.1*Financial Inclusion***

Financial inclusion refers to a set of measures and processes that allow individuals and business to have access to useful, affordable, and timely financial products and services. These include payments, loans, and insurance delivered responsibly and sustainably. Financial access is a pre-requisite of long-term planning and financial wellbeing. It also helps individuals, families, and businesses in achieving long-term financial goals, and providing the emergency support in unexpected circumstances such as a job loss.

According to World Bank \[[20](#chap7.xhtml#rref20)\], there are approximately 1.7 billion people are still unbanked, albeit bank account ownership is nearly universal in developed countries. Most of unbanked adults are women — 56% in the total population. Twice as many unbanked adults live in the poorest households in their economy as in the richest countries. Approximately half of all unbanked adults reside in just seven countries. China and India claim the largest shares due to their large population base, albeit having a high percentage of bank account ownership. The 1.7 billion people unbanked has no access to the financial infrastructure and are unable to tap into financial institutions to safeguard their possessions, send and receive payments, or invest their wealth. Some choose to not having a bank relationship, but many do not have other options. Either it is due to the inadequacy of the financial infrastructure or the unaffordability. Many turn to collateralized loan or shadow banking, which collect stifling fees and exploit the financially under-privileged for profits. In turn, the illegitimate source of capital and financial services worsens the rift between the banked and unbanked. Onboarding the 1.7 billion unbanked is going to be the largest market expansion in human history.

The global COVID-19 pandemic has only aggravated the challenge, with over 3 billion people seeing their workplace fully or partially close down. According to the Congressional Research Service \[[1](#chap7.xhtml#rref1)\], the unemployment rate in the US has reached a historical high of 14% — the highest rate recorded since data collection began in 1948. The COVID-19 pandemic has also impacted economic sectors dispa-rately. The leisure and hospitality sector lost the largest number of jobs since January 2020. Against this backdrop, governments around the globe have announced stimulus packages and job support schemes, targeting families and businesses, so that workers stay employed and businesses remain viable. Currently, the payouts are facilitated using mostly traditional payments instruments, such as cheques, bank transfers, or prepaid cards. In the US, millions have to wait for months to receive the support package; it takes only longer for the unbanked \[[21](#chap7.xhtml#rref21)\].

There are growing interests in modernizing the payment infrastructure based on CBDCs. Survey results indicate that financial inclusion is one of the key motivations for issuing CBDCs, especially in many emerging and developing countries, as shown in [Figure 7.5](#chap7.xhtml#fig7-5).

This is not surprising because governments can harness the power of CBDCs to directly access citizens, thus reaching out to the beneficiaries in reduced time and costs. The economic stimulus programs can be carried out more efficiently, ensuring that support is quickly distributed through a uniform digital payment rail. The CBDCs-based payouts scheme is able to provide more data points in representing the economic activities. As a result, the outcomes and effectiveness of the stimulus schemes can be more accurately measured and adjusted when required. In addition, financial inclusion cannot be achieved without viable use cases. The afore-going government-led use cases, together with countless others, are instrumental to improve the financial inclusion. This is not possible in cryptocurrencies, given the well-known usability pain, despite enthusiasm from crypto-commentators. Moreover, CBDCs have the potential to cut to the bone of the cost of storing money and making payments. The take-up of account ownership — the entry point to financial services should explode and the ability to preserve wealth should see enhancement, improving the quality of life, and alleviating the growing rift of income inequality.

![](images/p236.jpg)

**Figure 7.5.**Financial inclusion is one of the key motivations for issuing CBDCs

In addition, CBDCs can bring positive impacts to the unbanked or underbanked by pumping up the legitimate economy. Research shows that blockchain applications including digital currencies will save banks $15 to $20 billion yearly \[[22](#chap7.xhtml#rref22)\]. The extra liquidity will be re-invested to support other parts of the economy. CBDCs can become the new payment rails underpinning the new digital businesses. In the capital market, there are trials or pilot transaction to use CBDCs to perform the cash leg settlement for government bonds. In real estate, CBDCs can facilitate the efficient fund flows between buyers and suppliers in almost all phases of construction, such as in digital project account management or direct developer sales.

When capital recycles faster and the cost of capital decreases, an economic boom follows. Recent research suggests that the adoption of CBDCs raises the real GDP by approximately 3%, based on the analysis of a dynamic stochastic general equilibrium model of the US economy \[[23](#chap7.xhtml#rref23)\]. As the economy accelerates, people get richer and, as this happens, more people will have access to affordable financial products and services. That said, this growth-driven financial inclusion enabled by CBDCs may be more appealing in developing countries. The growth in the developed economies may quickly hit the glass ceiling.

As such, financial inclusion has the potential to be the common denominator of the wider adoption of CBDCs, particularly in countries with large underbanked or unbanked communities.

**7.2.2*Fostering Payments Innovation***

With the advent of technology, the payments landscape has been rapidly changed by new market entrants, payment service providers, and BigTech firms. Globalization and the proliferation of e-commerce have witnessed an unprecedented growth in the payments industry. As a result, payment systems have elevated from the salt mines to the board room.

There are reasons that the payments business has become the first frontline and the battlefield for banks, FinTechs, and BigTechs. First, it is much easier to venture into as compared to other banking lines, such as investment banking or corporate banking. The stakeholders involved are much less than capital markets. For example, one corporate bond issuance requires a number of participants such as book-runners, paying agents, legal councils, central securities depository, custodians, etc. In contrast, payments business largely deals with clearing banks and regulators. The messaging network SWIFT is robust and proven. The BigTech or data behemoths can easily leverage their brand, replicating the customer intimacy in the new endeavor. The scale, the brand potency, and the data can be readily translated to commercial viability. As such, the Diem, Facebook’s rebranded Libra crypto project has come under ongoing pressure from the global regulators.

Central banks have the responsibility to ensure a competitive payments market, while being prepared for potential crisis and concentration risks. Firstly, payments exhibit a strong network effect, thus the critical mass of adoption could be won rapidly. Alipay by Ant Financial Group commands a user base of more than 400 million users. The Chinese messaging app WeChat is a pioneer in introducing P2P payments transactions. Secondly, the technology firms are experienced in innovating business models, such as “freemium”. Revenue will follow the rapidly increasing the user base from cross-sell and the sales from a premium version. It is worth noting that the success of payments innovations goes hand in hand with the concentration risk, which leads to a higher bar of entry and innovation. Regulators are increasingly concerned about the risks that the centralized payment service providers could abuse their market power. The un-competitiveness of the payments industry is particularly worrying, not to mention the privacy concerns. Also, central banks should be able to provide resilience in the digital era, since the negative consequences for the society is unaffordable.

CBDCs can benefit the payment efficiency by creating contestability in the payments market. As CBDCs bear zero transaction cost and are secure by design, which could prompt substitution from both physical bank notes and e-money. The e-money providers, FinTechs, BigTechs, and banks will compete to revamp their product stack, so as to retain the customer intimacy, flows, and the distribution channel. Banks’ omni-channel collection solutions will likely undergo an overhaul to support new customer requirements. The revenue value chain across card network, acquiring bank, payment processors, and issuing banks will be redistributed. The decade-long core banking infrastructure, ranging from API interface to end-of-day batch jobs, needs to undertake modernization to support the CBDCs transactions. In the mid- to longer-term, payments in the Internet of Things (IoT) and machine-to-machine payments would require programmable features in money. CBDCs can provide countless opportunities to let algorithm specify rules and conditions. Conventional networks are not upgraded to support this innovation. Companies are competing to gain the first mover advantage.

In addition, we may also see a new form of public–private partnership to facilitate the adoption of CBDCs from both retail and wholesale perspectives. An example of the partnership model is the 2-tier structure of the e-CNY (also known as “DC/EP”) project in China. Another is the joint-venture creation of “Partior” by Temasek Holdings, JP Morgan, and DBS, as a commercialization effort of Project Ubin in Singapore. We will discuss in detail the Project Ubin case study in a later part of this chapter.

Last but not least, interest-bearing CBDCs can foster greater innovation in the payments landscape, as compared to cash-like CBDCs. As CBDCs stores value, there will be inevitably fund flows from operational account and deposits to CBDCs wallets. Banks may respond by increasing the deposit interest rates so as to regain the deposit based lost to CBDCs. New wealth management products may be packaged and offered to preserve the market share. The vacuum period during the transaction may produce new FinTech or payment service providers. In extreme situations, CBDCs can serve as the redundancy of the private payments services in the event of breakdowns.

**7.2.3*Seigniorage Retention***

Seigniorage refers to the profit made by the central bank by issuing currency, especially the difference between the face value of physical notes and coins and the production cost. As an example, the printing cost of $1 notes in the US is 6.2 cents \[[24](#chap7.xhtml#rref24)\]. Moreover, there are also costs related to the distributions of currencies and research and development (R&D) in counterfeit efforts.

Seigniorage can be positive or negative. When the seigniorage is positive, the central bank will have an economical gain; whereas a negative seigniorage will lead to an economic loss. When bank notes, at the dollar amount, are distributed to the banks, banks wire the respective monies to the central bank. The funds can be invested in state-issued securities such as treasury bills to generate interest income.

We may describe seigniorage in mathematical simple terms as follows,

![](images/p240.png)

where *S* is the seigniorage revenue, *V* is the value of the bank notes outstanding, *I* is the prevailing interest rate, and *P* is the bank note production and distribution cost. As can be seen in Equation 7.1, the more bank notes outstanding, the higher seigniorage revenue.

As the payments landscape are getting more digitized, the use of cash has declined sharply in the past decade and the trend is expected to continue. One concern for central bankers is that the declining use of physical notes may pose a threat to the seigniorage revenue. Equation 7.1 reveals that the seigniorage plummets, with an increasing *V* and decreasing *P*. The decreased seigniorage may undermine the central bank’s ability to cover the cost of production operations and its autonomy. On the other hand, issuing CBDCs could provide a new source of revenue, given the cost of “mining” digital currencies is expected to be lower than “printing” physical bank notes. This may be welcomed by both developed and developing economies, given the weightage of currency in circulation on central banks’ balance sheet. The additional support will mean improved abilities in carrying out day-to-day business. Hence, central banks may be motivated to introduce CBDCs considering the effects of increased revenue.

**7.2.4*New Monetary Policy Tool***

The COVID-19 pandemic has caused significant declines in output, and precipitated an extraordinary economic crisis. Combined with the aftermath of the 2008–2009 financial crisis, major economies have been in a liquidity trap. Low interest rates have been the catalysts to increase the aggregate demand and propel the economy. In certain economies, the policy interest rates have entered the negative territory. For instance, Japan’s policy rate has dropped to below zero in 2016, and it is set at −0.1% per annum as of April 2021. In Europe, the Governing Council of the European Central Bank (ECB) sets the key interest rate. The deposit facility rate, which banks may use to make overnight deposits with the Eurosystem, became zero in 2013, and it has been set as −0.5% since 2019, whereas the refinancing rate has been zero since 2016.

The unconventional easing and forward guidance approach did not have a significant effect on GDP growth and core inflation in key developed countries such as in the US, Europe, and Japan. The core inflation remains well below each central bank’s inflation target. Physical bank notes or cash bears zero interests, thus putting a limit to the central banks’ efforts to reduce the nominal interest rates. Ideally, the real interest rates should fall to an equilibrium point of negative interest rates to effectively increase the aggregate demand and boost the economic outputs.

Cash-like CBDCs with limit controls will unlikely to have significant impacts to the implementation of monetary policy, regardless whether such CBDCs are operationalized by the central bank directly or through public–private partnership. Being non-interest-bearing instrument, it is unlikely that physical bank notes can be totally replaced by CBDCs. Therefore, the limit of lower bound rate attributed to the cash will remain. In economies with negative policy rate, it is possible that effective lower bound could be pushed towards zero. In countries with positive policy rate, the CBDCs will almost certainly be operational in nature, in other words, petty cash alike. As a result, varying the supply of bank notes and their digital counterpart would be unlikely to be an effective monetary policy tool for central bankers. Once introduced, the total supply will still be controlled by the central bank with a prescribed set of terms and conditions. Such CBDCs are more likely to minimize the disruption with a coordinated and smooth transition.

There has been active research whether interest-bearing CBDCs could serve as a main tool for conducting monetary policy. According to \[[7](#chap7.xhtml#rref7)\], if certain design principles are followed, CBDCs would foster true price stability in the monetary policy framework. The real value of CBDCs would remain stable over time in terms of a broad consumer price index. Previously, research also showed that it is expected to have consistent interest rate on central bank reserve and the interest rate on CBDCs, due to the arbitrage opportunities for clearing banks. In a negative interest rate environment, CBDCs users would tend to convert CBDCs to physical bank notes. The central bank may need to eliminate the physical bank notes or introduce frictions in the conversion step, in order to sustain the negative interest rates. In addition, the risk of digital bank runs due to interest-bearing CBDCs should also be carefully studied and managed.

The effects of CBDCs on monetary policy, the financial system, and the wider economy remain to be a research topic to be carefully assessed. The desired benefits and outcomes depend on the design choice both economically and technologically. There are trade-offs in the decisions, and we expect the central bank to be prudent in the decision-making process.

**7.3Technology Considerations**

The CBDCs do not necessarily have to be based on blockchain technology. A centralized technological design based on a traditional database solution is feasible to implement central bank issued money. However, there are characteristics that make blockchain-based CBDCs desirable, for example, the transparency, cryptographic security, and resilience, as compared to a traditional database solution. Additionally, the programmability feature of smart contracts and software programs stored on a blockchain that run when pre-set conditions are met, have provoked unlimited imaginations in the future financial world.

**7.3.1*Blockchain and Smart Contract***

Blockchain is a tamper-evident and tamper-resistant digital ledger implemented in a distributed fashion (i.e., without a central repository) and usually without a central authority \[[25](#chap7.xhtml#rref25)\]. Recent trends in digitization have led to a proliferation of studies for blockchain theories and applications \[[26](#chap7.xhtml#rref26)\]. The research results in the past few years point to the conclusion that blockchain can bring solutions to solve complex distributed business network use cases, ranging from cryptocurrencies, digital ecosystems, to CBDCs. That said, Blockchain is not a new concept. It is widely recognized that David Chaum is the first person that proposed a blockchain-like protocol in his dissertation in 1982 \[[27](#chap7.xhtml#rref27)\]. Follow-on researches by Stuart Haber and W. Scott Stornetta developed a secured chain of blocks based on cryptographic techniques \[[28](#chap7.xhtml#rref28)\]. The technology has become widespread since the groundbreaking cryptocurrency of Bitcoin \[[29](#chap7.xhtml#rref29)\]. In Bitcoin, the transfer of value digitally is achieved by using blockchain combined with several other computing and communication technologies in a decentralized system.

The original blockchain used in Bitcoin is somewhat similar to the classical data structure of linked list — a basic data structure concept taught in computing classes. In blockchain, however, data objects are “linked” to one another, forming a sequence by cryptographical pointers with more complex and integrated functions. No operations are allowed to insert, delete, and update data in blockchain at arbitrary positions, different to linked lists. When transactions are grouped into blocks and blocks are linked together cryptographically, a chain of record is formed. The collection of records is referred to as blocks and the records are called transactions. The ledger is open to all authorized participants in the network. Transactions are sorted and added to the ledger upon successful verification, following a pre-configured protocol. [Figure 7.6](#chap7.xhtml#fig7-6) illustrates the Blockchain concept.

Blockchain relies on the premise that the sequence of records is converged by autonomous execution of algorithms, leading to consensus and lowering the cost of trusts. This is different than most of the current infrastructure we live in, where trusts are ensured by the intermediaries. Despite rapid development, blockchain technologies in general are limited by the system performance. The transaction throughput of Bitcoin is around 7 transactions per second, whereas Visa processes 1,700 transactions per second on average. Efforts to improve the performance include the introduction of permissioned blockchain (versus permissionless ones such as Bitcoin) and less compute intensive consensus algorithms. However, research results have shown that the system throughput of popular blockchain platforms are far from being superior to the existing centralized database. The network latency degrades with an increased number of nodes (blocks of data are stored on nodes) \[[26](#chap7.xhtml#rref26)\].

![](images/p244.jpg)

**Figure 7.6.**Blockchain — A linked list that is built with hash pointers

Bitcoin or other alternative coins are shadow cryptocurrencies that leverage blockchain to transfer values between involved parties. Similarly, blockchain-based CBDCs use blockchain as the underlining data structure, as a result, inheriting its advantages and limitations. The key advantages of the technology are immutability, operational resilience, transparency, and data integrity. That said, the advantages also come at a cost or risks. For example, while Blockchain-based CBDCs can avoid any single point of failure, but if a software bug exists, it would require a coordinated upgrade in all the participating nodes.

Smart contracts are basically executable files. The concept was first proposed by computer scientist Nick Szabo in 1994. He defined smart contracts as “computerised transaction protocols that execute terms of a contract”. The original purpose is to “satisfy common contractual conditions (such as payment terms, liens, confidentiality, and even enforcement), minimize exceptions both malicious and accidental, and minimize the need for trusted intermediaries” \[[30](#chap7.xhtml#rref30)\]. In blockchain systems, smart contracts are programs stored on a blockchain that run when predetermined conditions are met. Traditional smart contacts can perform conditional automated execution but suffer from issues of lack of trusts, given the single point of execution and the inability to tamper-proof. To this end, Blockchain can address the problems of single-point smart contracts due to its non-tamperability, transparency, consensus-based trust, and other characteristics. Blockchain-based smart contracts improve the level of automation with programmability, immutability, transparency, and traceability. It is worth noting that not all Blockchain platforms support contracts. Common blockchain platforms and smart contracts are summarized in [Table 7.3](#chap7.xhtml#tab7-3). We will not do a deep dive on the platform features that not the objectives here. Interested readers are referred to the reference herein for more details \[[25](#chap7.xhtml#rref25)\].

**Table 7.3.**Common Blockchain platforms and smart contracts features

 
| **Platform** || **Smart contract** || **Consensus** |
| --- | --- | --- |
| Hyperledger Fabric || Go, Javascript || Pluggable |
| --- | --- | --- |
| Corda || Kotlin, Java || Raft |
| Hyperledger Besu || Solidity, DAML || PoW, PoA |
| Quorum || Golang || Raft |
| Bitcoin || **—** || PoW |
| Ethereum || Solidity || PoW |
| VMWare || DAML || BFT |
| Ripple || **—** || Ripple consensus |
| Multichain || C++ || Trusted validators |

**7.3.2*Requirements of Blockchain-based CBDCs***

The desired CBDCs features, objectives, and use cases will be essential to determine the technical requirements. Much of the requirements are still uncertain, but there are several key requirements reasonably acknowledged in the CBDCs community, which are elaborated as follows.

7.3.2.1*Secure and scalable programmability money*

Smart contracts offer CBDCs the prospect of programmable money, which are digital cash stored on a Blockchain with cash placed under the control of smart contracts. Apart from the benefits, smart contracts may also introduce known and unknown risks. For example, there are large amounts of losses in the Ethereum cryptocurrencies due to software bugs. The losses include accidental losses or logic loopholes that make the blockchain vulnerable to deliberate cyber-attacks. If CBDCs incorporate smart contract functionalities, then it will be important to consider safety and security when designing these. It is important to strike a balance between safety and extensibility. The solution should be scalable and robust for future economies, such as the machine-to-machine transactions. The existing token-based CBDCs also face the challenge of race condition of token selection, i.e., the performance is limited by concurrent access to the same token. Hence, token size management CBDCs splits and merges tokens on the fly may be required to ensure the optimal number of tokens for concurrent spending.

7.3.2.2*On-chain and off-chain interoperability*

Real-world CBDCs need to coexist with the existing financial infrastructure due to a variety of reasons. Firstly, not all transactions details are required to be stored on the Blockchain. For example, sensitive and private information may be exposed to leakage risks if stored on the Blockchain. Secondly, Blockchain systems do not have unlimited storage capacity. Thirdly, the integration is a requirement of data integrity and consistency from legacy systems and infrastructure. These require a multi-faceted integration to the current systems, technologies, and processes. All of these need to be designed carefully before the CBDCs graduate from the sandbox. [Figure 7.7](#chap7.xhtml#fig7-7) illustrates a CBDCs-based payments system.

![](images/p247.jpg)

**Figure 7.7.**An illustration of CBDCs-based payment systems

Referring to [Figure 7.7](#chap7.xhtml#fig7-7), we can see that the Blockchain is linked to the central banks, banks, and large corporates. Smart contracts play an important orchestration role to synchronize the CBDCs transactions to the existing off-chain systems. The orchestration tasks include various activities to perform accounting entries, on-chain and off-chain balance reconciliation, start of day or end of day account balances update, as well as errors detection and prevention steps. Thanks to API technologies, the synchronization can be performed in real time. In addition, integration to the off-chain ledger may require significant efforts to upgrade the existing core banking systems, for instance. Hence, the involvement of banks and private partners is crucial for the success of the CBDCs design and roll-out. Readers are referred to \[[31](#chap7.xhtml#rref31)\] for a detailed study of on-chain and off-chain interoperability in payment systems.

7.3.2.3*Privacy and compliance*

It is important that the CBDCs system can preserve user privacy while ensuring the adherence to regulatory and financial crime compliance requirements, to mitigate the risks of money laundering, tax evasion, and other illicit uses of digital currencies. New technologies such as Intel © Software Guard Extensions (Intel © SGX) may be options used to address the privacy requirements in CBDCs. The hardware design uses a private area of execution called an enclave to encrypt the entire ledger when it is stored. This can prevent unintended disclosures of transaction history. Another possibility is to leverage complex cryptographic algorithms such as zero-knowledge proof to ensure compliance without revealing the identities. However, zero-knowledge proof algorithm is computational extensive and still finds itself at an early adoption stage.

**7.3.3*CBDCs Integration Framework for Banks***

Depending on the CBDCs designs, the technology integration efforts for commercial banks may differ. Nevertheless, banks need to be prepared to support the retail and corporate customers as soon as the CBDCs are rolled out. For instance, the merchant acquiring business would have to deal with CBDCs in a retail context and merchants bank are required to support the automatic deposits from CBDCs to bank deposits. This requires an upgrade to existing banking infrastructure and interface. It is important for banks to stay close to the CBDCs development and get ready from the technology perspective. Banks also need to mitigate the risk that a large number of central banks start to roll out CBDCs at the same time, which may cause serious disruptions to the strategic priorities and resource planning in global banks. Due to the free-of-charge nature of CBDC transactions, commercial banks and industry players need to have a viable financing option to fund the transition and continued operations.

[Figure 7.8](#chap7.xhtml#fig7-8) shows the potential CBDCs integration points for commercial banks.

In [Figure 7.8](#chap7.xhtml#fig7-8), the e-channels upgrade include the required frontend and back-end technologies and processes changes to support the CBDCs/fiat and fiat/CBDCs conversions. In certain jurisdictions, this may also include the upgrade in the Automatic Teller Machines (ATM). The balance sheet management practices cannot be overlooked, as the CBDCs would likely impact banks’ liquidity conditions. If the CBDCs are interest-bearing, the demand of cash may be reduced, and the effects on bank deposits need to be analyzed and simulated, just to name a few.

![](images/p249.jpg)

**Figure 7.8.**Bank integration points for CBDCs

In addition, banks are encouraged to assess the current processes early to determine how they fit into the CBDCs system and to create a Target Operating Model (TOM) accordingly. The assessment is also critical to make the revenue generation sustainable by offering new CBDCs-related products and services. The business, operational, and technology impact analysis should also include the gap analysis in data protection (e.g., GDPR, MIFD) requirements as well as the non-functional performance evaluation. [Figure 7.9](#chap7.xhtml#fig7-9) shows a phased approach in CBDCs integration to banks. Interactions and reviews between phases would be helpful to optimize the integration efforts.

What is more, with a variety of development stages and approaches, the industry players have kicked off initiatives to help centrals banks and commercial banks explore how CBDCs can fit into the needs of a country. Prior to official integration, virtual platforms can be used to emulate the operating environments for issuance, distribution, circulation, and the return of CBDCs. For example, Mastercard has developed CBDCs Sandbox, which is capable of showcasing the customer payment journey, examining the technology designs, and evaluating the development efforts \[[32](#chap7.xhtml#rref32)\]. Similarly, ConsenSys’ CodeFi Payments has deployed CBDCs Ecosystem-as-a-Service, a permissioned network or test environment offering the functionalities of CBDCs platform \[[33](#chap7.xhtml#rref33)\].

![](images/p250.jpg)

**Figure 7.9.**Phased approach in CBDCs integration to banks

**7.4Challenges and Risks**

The adoption of CBDCs is associated with an array of challenges and risks from the business, technology, economy, and legal perspectives, as it is explained next.

**7.4.1*Technological Limitations***

There are challenges and risks for both permissionless and permissioned Blockchains to be the backbone of the financial market infrastructure. While possessing some desirable characteristics, a number of limitations need to be overcome for Blockchain-based CBDCs to be implemented in the current financial systems.

7.4.1.1*Adherence to financial market infrastructure principles*

The current financial market infrastructure is well-established with clear principles and responsibilities. For example, the coordination of standard policy design and implementation is enhanced by the Committee on Payments and Markets Infrastructure (CPMI) and the International Organization of Securities (IOSCO), on matters ranging from clearing, settlement, to reporting. Payment systems, among others, are considered Financial Market Infrastructure (FMI) in the global financial world. To date, there are 24 principles and responsibilities of central banks, market regulators, and other relevant authorities as guided by the Technical Committee of the International Organization of Securities Commissions \[[34](#chap7.xhtml#rref34)\]. It is not difficult to note that the designs of blockchain, especially permissionless ones, are not fully adherent to these principles.

The settlement finality principle states that the “FMI should provide clear and certain final settlement, at a minimum by the end of the value date”. The rules and procedures are also required to define the point at which settlement is final. In contrast, many Blockchain systems, including the widely-used Ethereum, are currently using Proof-of-Work (PoW) consensus mechanism, resulting in non-deterministic settlement of transactions. Although a close states of settlement finality can be achieved, there are risks that unexpected events could occur, which introduces risks to users. Additionally, the principle of money settlement guides that “FMI should conduct its money settlements in central bank money where practical and available”. Referring to [Section 7.1](#chap7.xhtml#h7-1) in this chapter, the central bank money denotes the payments settlement using bank reserves. As a result, if a form of tokens on Blockchain is used in the settlement, the principles would require clarifications, if not revisions, on the exact designs of Blockchain-based CBDCs. Another challenge is that “FMI should have objective, risk-based, and publicly disclosed criteria for participation, which permit fair and open access”, whereas as its name suggests, permissionless Blockchain are without permissions required.

The afore-going analysis is non-comprehensive but to show the existing gap between the new and the current world. The use of permissioned Blockchain may alleviate some of these challenges by more advanced designs. However, CBDCs must be financially inclusive. A permissioned Blockchain directly accessible to a population of 1.4 billion citizens in China, for the sake of this argument, is no different to being permissionless. In other words, it is irrelevant to distinguish the Blockchain framework based on its permission level in the context of CBDCs. The closure of gaps requires advancements in the technology as a whole.

7.4.1.2*Technical standards and performance*

Blockchain technologies, as a matter of fact, are still in the early stages of development. Technical problems remain to be fully resolved, for example, the lack of technical standard, scalability, coupled with known and unknown cybersecurity risks. The IEEE Standards Association are actively pursuing Blockchain standardization efforts through various activities in multiple industry sectors, recognizing the vital role of standards in the development and the adoption of Blockchain technologies \[[35](#chap7.xhtml#rref35)\]. At the time of writing, there are six published standards and 52 standards under development, covering a wide range of applications and data models. The maturity level of blockchain technical standards remains to be improved.

In addition, the research work in Ethereum, Parity, and Hyperledger Fabric has shown that the throughput tends to decrease, and latency tends to increase as the number of nodes increases \[[26](#chap7.xhtml#rref26)\]. This puts a limit to the scalability of Blockchain-based systems in general, including CBDCs. As a result, the usability of the Blockchain is compromised, leading to its unreadiness for mass usage. The designs and codebases are still being refined constantly. Some systems such as Ethereum has a higher Technology Readiness Level (TRL), but the efforts to port over smart contracts from one to another is tedious and error-prone, due to the inconsistent models of programming languages. With more block-chain platforms being produced, we would expect the situation to exacerbate till a convergent stage is reached. Only at that point of time, a well-informed clear choice can be made whether or not to use and which Blockchain system to use in the CBDCs context.

7.4.1.3*Race condition of token selection*

There are limitations in both account-based and token-based representation in CBDCs with the same account being unable to proceed concurrently, since every transaction requires the previous balance or token output as the transaction input. This is called the race condition of token selection. On account of this, blockchain transactions need to be queued, sorted, and be executed one by one. Because of the consensus algorithm required and the communication overhead in general blockchain, the throughput is limited by this dependency. There are efforts such as Hyperledger Fabric that attempts to improve this by reversing the sequence of ordering and execution, but this in turn leads to complexities in conflict management of transactions. Token size management which splits and merges tokens on-the-fly may be helpful to ensure the optimal number of tokens for concurrent spending. Another plausible approach is to leverage the ultra-high parallel processing capacity by off-chain supercomputers or mainframe computers in core banking systems when on-chain and off-chain are integrated \[[31](#chap7.xhtml#rref31)\]. That said, the effectiveness of the solutions has yet to be proven in complex real-world applications, due to the low level of adoption of blockchain technologies.

7.4.1.4*Source of truth*

Blockchain systems segregated from legacy infrastructure is not sustainable. On-chain and off-chain ledgers need to be integrated at a certain point of time. This introduces complications when both ledgers are storing copies of transactions and related information. Which one should be considered as the single source of truth? In the current Blockchain world, the single source of truth is often being referred to as a significant advantage of Blockchain-based systems. This may be true for a community living on-chain, but it becomes a confusion when Blockchain transactions meet the off-chain ledger are connected. For example, the off-chain ledger can be the core banking systems in banks. The rulebook or partnership agreement of pioneer projects often has to specify that the single source of truth is in no doubt the off-chain ledger in order to fulfill the current data framework, whereas the Blockchain transactions are merely secondary references. This compromises the usefulness of Blockchain, particularly when the technology is used in important infrastructure systems such as CBDCs.

With the advent of research, the core requirements of CBDCs designs and the various technical issues of Blockchain are gradually revealed. Hopefully, the research would lead to a solution that can balance the innovations in Blockchain as well as the practicality of current market infrastructures, given the tremendous potential of this revolutionary technology.

**7.4.2*Balance Sheet Implications***

Central banks maintain a balance sheet listing the assets and liabilities as in other business organizations. The assets include items such as treasury bills, derivatives, or cash foreign deposits, whereas the liabilities include currency in circulation and bank reserve, etc. During financial crisis, the central bank can expand the balance sheet by undertaking open market operations (OMO). The bank reserve has limited access by financial institutions or payment service providers that operate in the large-value payments systems. In Singapore, the MEPS+ is the RTGS system to instantaneously and irrevocably settle inter-bank payment obligations and script-less government securities. Typically, only participants which are eligible to have settlement accounts at the central banks and satisfy certain technical and operational requirements can participate in the MEPS+ operations.

On the other hand, the currency in circulation, such as the physical bank notes, is approximately 10%–20 % of the total liabilities in a central bank’s balance sheet. Physical bank notes, also known as cash, is an anonymous bearer instrument. Moreover, it has not required intermediaries to facilitate the transactions, i.e., peer-to-peer without reliance on bank account-based infrastructure. This is the existing publicly accessible risk-free and non-interest-bearing central bank money widely used by the consumers and investors. A sample of the liability part of balance sheet reported by Monetary Authority of Singapore is shown in [Figure 7.10](#chap7.xhtml#fig7-10).

Other things being equal, the proportion of liabilities due to currency in circulation in total liabilities would increase as a result of the circulating CBDCs in the economy. This increase may lead to a challenging situation as the value of legal tender decreases. Simply put, there will be abundant money chasing too few goods and services, resulting in a so-called “demand-pull inflation” or the increase in aggregate demand. In the current times of uncertainties amid the COVID-19 pandemic, the additional source of aggregate demand may lead to complications in the distribution and delivery of key materials, goods, and services, which is undesirable from the economy perspective. A detailed study of the impacts to central bank’s balance sheet expansion can be found in the references herein \[[36](#chap7.xhtml#rref36)\].

![](images/p255.jpg)

**Figure 7.10.**Liabilities in the balance sheet published by the Monetary Authority of Singapore (MAS) as of March 31, 2021

In addition, if the convertibility is guaranteed and no amount caps is imposed, the demand for bank deposits will be substantially reduced. The switch from retail balances to CBDCs will leave a larger portion of bank financing dependent on the wholesale market at higher interest rates. Banks may also have to increase the retail deposit rates to regain the retail deposits, further narrowing the profit margins of banks. In the event of market panic, the shortage of liquidity may trigger severe consequences in digital bank runs, creating an imminent threat to financial stability. Thus, it is important to be prudent in designing and transitioning to CBDCs, while recognizing the potential risks to the financial markets.

**7.4.3*Legal Challenges***

Traditional currency is well-defined and regulated by the authorities, but there are legal gaps in the introduction of CBDCs. The issuance of CBDCs should be on the basis of “a robust, ideally explicit, legal basis” in the central bank law, according to the International Monetary Fund (IMF) \[[37](#chap7.xhtml#rref37)\]. A comprehensive examination of the existing legal framework will ensure the right understandings of policy choice from the legal perspective. The scope of review may be beyond the scope of central bank law and monetary laws as well, such as criminal law and tax law. The IMF’s preliminary study of the legal aspects in CBDCs has pointed out important conclusions. This chapter is not intended to dive deep into legal matters. Thus, we merely reproduce some of the key conclusions in \[[37](#chap7.xhtml#rref37)\] for the readers’ reference:

*   Many central bank laws will support the issuance of account-based CBDCs to financial institutions, but its issuance to the general public will often lack a sufficient legal basis.
*   Questions remain whether central banks are legally authorized to issue token-based CBDCs. Most central bank laws currently only authorize the issuance of currency in the form of bank notes and metallic coins.
*   CBDCs status under monetary law raises many complex issues, as neither form of a means of payment expressed in the official monetary unit. In most countries, token-based CBDCs do not qualify as currency.
*   The remedy of monetary law would be subject to a number of challenges and complexities.

**7.4.4*In Search of the Killer Application***

With more than 80% of central banks at different stages of CBDCs development, the commentators claim that CBDCs can be the killer application of Blockchain technology. This could be true but the question that follows is what would be the killer application of CBDCs?

From the wholesale perspective, the bank reserve is already digital in many parts of the world. While there are constraints in the RTGS systems, central banks have ongoing programs to upgrade the Real-Time Payment (RTP) framework. For example, the Federal Reserve bank will build and operate the FedNow Service, a new inter-bank 24/7/365 RTGS service with integrated clearing functionality to support faster payments \[[38](#chap7.xhtml#rref38)\]. The Fedwire®Funds Service and National Settlement Service hours are also expected to expand to 24/7/365. In countries with the RTGS systems in place, the benefits to replace the RTGS system with another version of “digital” bank reserve may not be obvious, and the cost of switching is high in view of the technology uncertainties as we explained. Experiments in Asia point to the direction of cross-border payments, such as the Project Lionrock-Inthanon jointly by the Hong Kong Monetary Authority (HKMA) and the Bank of Thailand (BoT). Recently, the initiative has evolved into a multi-central bank setup called the “m-Bridge”, welcoming new participants of the Central Bank of the UAE (CBUAE) and People’s Bank of China (PBoC). The “m-bridge” is also highlighted in the HKMA “FinTech 2025” blueprint to future-proof for CBDCs \[[39](#chap7.xhtml#rref39)\]. The exploration by the Monetary Authority of Singapore (MAS) in Project Ubin has also pointed out similar potentials of wholesale CBDCs in streamlining the cross-border payments.

From the retail perspective, the killer app will determine the level of success in CBDCs. Trust, a given property in CBDCs, does not automatically translate into adoption or transaction flows. History tends to repeat itself. We present two anecdotes to the readers as follows.

7.4.4.1*Anecdote I: Mondex versus Octopus in Hong Kong*

Mondex and Octopus are two reusable payments cards in Hong Kong in mid-1990. Both were built around the same timing, but ended with dramatically different fates.

The Octopus card was initially introduced by the Mass Transit Railway Corporation for collecting fares for the mass transit system, but the use case has rapidly expanded to include an array of retail businesses. Nowadays, the Octopus card is commonly used in MTR, at mini-marts, car parks, and many places where low-value payments are required, and is considered one of the most successful electronic payments cards in the world \[[40](#chap7.xhtml#rref40)\]. In contrast, the Mondex card was launched by the joint venture between the legitimate and trustworthy HSBC and Mastercard International. At that point of time, HSBC (including Hang Seng Bank) managed over 30% of bank deposits in Hong Kong and was a bank note-issuing bank licensed by HKMA. Endowed with the full legal status of the money, the Mondex was the most “cash-like” electronic cash smartcard, being an “effective substitute to physical bank notes”. However, Mondex smartcard ended up in a complete failure within five years. Today, even most of HSBC staff are unaware of this innovation episode in HSBC history.

In retrospect, minimally the following factors have contributed to the outcome.

*   *Killer application:* Octopus has a clear use case that is the travel fares payments, which has a high-frequency usage and a large pool of target user base, i.e., public transport travelers. As compared to a traditional ticket, Octopus also has clear differentiators in terms of functionality and user experience. The network effect and the economics of scale allow Octopus to rapidly expand to non-transport sectors, grabbing huge returns. Both the returns and the growths are sustainable. In contrast, Mondex was marketed as a one-size-fits-all solution, without a clear use case to demonstrate the benefits of substituting cash with Mondex. Over 5,000 merchants agreed to accept Mondex at the beginning, but consumer adoption was not successful. As a result, the merchants started pulling out, creating a downward spiral of usage.
*   *Initial user base:* During the initial phase, the MTR and the then Kowloon–Canton Railway made all passengers replace the traditional tickets into Octopus within two to three months. Despite initial dissatisfaction, the Octopus card had quickly accumulated more than three million card users in three months. In contrast, the adoption of the Mondex was “democratic”, i.e., users were given a choice whether or not to use Mondex. This is disastrous when merchants and consumers did not see clear benefits to switching.
*   *Technology:* Mondex was built with contact-based magnetic technology to perform read/write operations. Octopus uses state-of-art radio frequency identification (RFID) technology. It is contactless and the read/write speed is as fast as 0.3 seconds. In the use case of transport fares payments, the experience brought by RFID was revolutionary.
*   *Trust levels:* Clearly, the financial institutions behind Mondex are a lot more trustworthy as compared to a private transport company. However, the trust did not magically translate to the desired outcomes. Moreover, trust levels are dynamic. After Octopus won critical mass adoption, the HKMA issued a deposit-taking license to Octopus in 2000. The competitions are multi-faceted in the business world. On top of trust, user experience and commercialization strategy, for instance, also play a part to determine results.

7.4.4.2*Anecdote II: Avant in Finland*

Another anecdote is that the Bank of Finland (BoF) once launched the first state-issued e-money named Avant for retail use in December 1992. The e-money was intended to substitute cash and took on the form of stored-value payment cards. The design features of Avant include general merchant acceptance, anonymity, efficiency, and safety. The card was based on microchip with added security measures. The ATMs were modified to allow the exchange between cash and Avant money. The funds were absolutely secure as they were backed by the central bank. [Figure 7.11](#chap7.xhtml#fig7-11) shows the issuance framework.

As can be seen in [Figure 7.11](#chap7.xhtml#fig7-11), the issuance framework was a 2-tiered structure, consisting of BoF as the issuer, distributors, merchants, and consumers. The distributors were initially identified to be commercial banks, and later changed to a large network of convenience stores. Within a year, the total number of outstanding cards reached 500,000. Prior to the Avant rollout, the BoF thoroughly examined various aspects in the monetary system, such as monetary policy implications, seigniorage income, legal tender status, and financial stability, as we are doing today for CBDCs. The conclusion was that Avant would unlikely lead to significant impacts to monetary systems, given that it is “cash-like”. Due to the hefty cost of maintaining the system, a small fee for top-up and withdrawal was charged, which resulted in consumer dissatisfaction. Avant went into oblivion in 2003 as a result of costs, and the facts that debit/credit card networks had become more efficient.

![](images/p260.jpg)

**Figure 7.11.**Distribution structure of Avant in Finland in 1990s \[[41](#chap7.xhtml#rref41)\]

Referring to [Section 7.1](#chap7.xhtml#h7-1), Avant in Finland resembles the key features of the concept of retail CBDCs today. The distribution framework and the discussion points on impacts to monetary systems were similar to the case of retail CBDCs as well. Its launch was attributed to the hypothesis that BoF had at that point of time. What is interesting is that the anecdote provides us with important lessons.

*   *Killer application:* Avant did not have a high-frequency use case that could sustain its existence, in the face of the advancement of the card network. Without a killer application, the challenge would be maintaining the stickiness of its users.
*   *Initial user base:* Avant had a good initial user base of 500,000 outstanding cards. However, the cost of maintaining a central bank issued e-money turned out to the hefty. The transfer of costs to users discouraged its wider adoption. When the ATM withdrawal and deposit fees were free of charge, the additional cost did not outweigh Avant’s benefits.
*   *Technology:* Avant was built on state-of-art technology, but the interoperability with legacy ATM network had caused problems to the BoF. User experiences tend to be adversely affected by the incompatibility. The upgrade of the legacy technology could not be achieved over the night.
*   *Trust levels:* Central bank issuance guaranteed the safety of the funds, thus increased trust levels. That said, in low-value payments use cases, the advantage of higher levels of trust did not automatically translate to desired outcomes in the longer term.

For retail CBDCs to be successful, the differentiator has to be more than the “trust” factor provided by central banks. The implementation framework may vary from a 2-tier structure to direct distribution, but in order to stay relevant in the longer run, a well-thought “commercialization strategy” is required. Adoption is subject to user behavior changes and the user experiences of retail CBDCs. The technology has to keep up with innovation from the private sectors. Central banks have all the capabilities and mobilization power to roll out a state-issued e-money. However, the “cash-like” retail CBDCs would unlikely have revolutionary effects to the payments landscape.

What may be different this time around is, in fact, the new capabilities introduced by smart contracts and Blockchain technologies. The programmability that could embed in the e-money could lead to a giant leap in payments development. But what if private e-money providers also started issuing programmable e-money? How will the retail CBDCs stand up to the competition? The good news is that central banks are devoting more resources to research. Academics and industry players are also striving to advance the smart contracts and Blockchain technologies.

**7.5Case Study — Singapore’s Project Ubin**

Project Ubin is Singapore’s CBDCs initiative, leveraging public–private partnership to collaboratively explore the use of Blockchain and distributed ledger technology (DLT) for the clearing and settlement of payments and securities. The aim is to help the Monetary Authority of Singapore (MAS) and the financial industry better understand the Blockchain technology, exploit the potential benefits, and explore the applicability to Singapore’s financial market infrastructure through practical experiments. This initiative is in line with the eventual goal of developing simpler and more efficient alternatives to existing systems and technologies \[[42](#chap7.xhtml#rref42)\].

Project Ubin spans over five consecutive phases from 2016 to 2020, and has been officially concluded. Each phase focuses on a specific set of prevailing challenges and concerns faced by the industry. Phases 1 and 2 explore the technology capabilities building out the infrastructure required in the context of a domestic payments network. Phases 3 and 4 focuses on the interoperability issue of blockchain-based ecosystems and networks in the applications of Delivery versus Payment (DvP) and Payment versus Payment (PvP). Phase 5 as the last phase of the project shifts from providing technical concepts towards proving value, including understanding how such new models could improve settlement efficiencies, and the potential benefits for the broader ecosystem. [Figure 7.12](#chap7.xhtml#fig7-12) shows the development journey of Project Ubin in Singapore.

![](images/p263.jpg)

**Figure 7.12.**Project Ubin journey: Phase 1 to 5

*Phase 1: Tokenised Singapore Dollar*

On November 16, 2016, the Monetary Authority of Singapore (MAS) announced that it would partner with nine financial institutions supported by the technology startup R3 on a proof-of-concept of inter-bank settlement. The consortium of financial institutions were the Bank of America Merrill Lynch, Credit Suisse, DBS Bank, Hong Kong and Shanghai Banking Corporation (HSBC) Limited, JP Morgan, Mitsubishi UFJ Financial Group, OCBC, Singapore Exchange (SGX), and United Overseas Bank (UOB). BCS Information Systems has also been included as a technology vendor.

The objective of Project Ubin was to evaluate the implications of a tokenized Singapore dollar (SGD) on a distributed ledger in Singapore’s financial infrastructure. An Ethereum-based Proof-of-Concept (POC) prototype was developed, leveraging the existing MAS MEPS+ system to enable domestic inter-bank payment on a distributed ledger. The prototype was tested for the ability to transaction 24/7, in real time, resilience against single point of failure, and the timeliness of settlements.

Project Ubin was investigated by two workstreams: (i) a technical workstream responsible for the delivery of the Ubin POC prototype; and (ii) a research workstream to focus on studying, analyzing, and documenting the various adjacent potential implications of implementing the solution in a production environment.

The technical workstream developed a prototype that established the distributed ledger network, a set of smart contracts to interact with the MEPS+ and dashboard, and the connectivity of the network to the MEPS+ system. MAS was able to issue the SGD denominated depository receipt and create wallets for participating banks. Other participants were able to pledge, transfer, and withdraw the depository receipt. The private Ethereum-based prototype was successfully integrated to the MEPS+ system to synchronize the on-chain and off-chain accounting entries. The consensus mechanism used was the well-known Proof-of-Work (PoW) mechanisms (unfortunately, its settlement is probabilistic, hence not deterministic). The high-level system architecture of Project Ubin Phase 1 is shown in [Figure 7.13](#chap7.xhtml#fig7-13).

As shown in [Figure 7.13](#chap7.xhtml#fig7-13), the RTGS system (MEPS+) was integrated to the Ubin network via the “DLT connector”. In MEPS+, a new account called “DR Cash Custody Account” was created for each bank to back the DRs on the distributed ledger. The account functioned similar to the existing FAST Cash Custody account in the MEPS+ system. The balance is periodically adjusted to match the outstanding values of the DRs owed to the account holder.

![](images/p264.jpg)

**Figure 7.13.**High-level system architecture of Project Ubin Phase 1

When the operations of pledging and redemptions were performed, the respective account entries were reflected in the existing RTGS account and the new “DR Cash Custody Account”. For more details on the account entries please refer to reference \[[43](#chap7.xhtml#rref43)\]. It is worth noting that the DR issued to the individual bank could be held on-chain overnight, requiring no intraday redemption. By doing so, Project Ubin participants may perform inter-bank settlement around-the-clock and were not limited to the operating hours of the MEPS+ system.

The research workstream consisted of subject matter experts to investigate the business, regulatory, monetary, and policy implications, and to develop thought leadership in this field.

From the risk perspective, it was suggested that that the approach in Project Ubin Phase 1 did not create credit risk for the participants, on the basis that the transfers of a binding claim on the central bank’s currency and the central bank were not subject to default. That said, an appropriate legal structure was required to ensure that the transfer of digital SGD equal to a full and irreversible transfer of the underlying claim. It was further suggested to consider a new form of “money market” to allow banks to borrow liquidity from others without posting cash with the MAS. By doing so, the liquidity requirement in the Singapore market may be optimized but a detailed study and evaluation on the credit risk implications would be required.

It was assumed that all participants funded their expected payments on a gross basis, thus no liquidity risks existed in the distributed ledger. In the event that one participant suffered from outage or failure, the remaining participants would be able to continue to fulfill their payment obligations. If the distributed ledger became a permanent facility alongside the MEPS+, the risk of inadequate funding may be introduced, because the banks had to decide the allocation of liquidity to each system. Banks would require advanced liquidity management techniques in order to optimize the available liquidity in the Singapore market. In the case of “money market”, it would require careful considerations on the implications of the liquidity risk, for example, MAS’ potential role of liquidity provider.

Project Ubin Phase 1 was concluded with the following deliverables:

*   Developed an Ethereum-based domestic interbank payments settlement network interconnected to the existing MEPS+ system;
*   Studied the various account entries and money transfer mechanisms, and selected the continuous depository receipt model that allowed banks to exchange cash collateral for depository receipts on the distributed ledger;
*   Researched the implications on credit and liquidity risks and challenges; and
*   Identified the future work required to operate the Ubin network, pointing out the directions of securities settlement by Delivery versus Payment (DvP) and cross-border payment (PvP).

*Phase 2: Re-imagining RTGS*

On October 5, 2017, the Monetary Authority of Singapore (MAS) and the Association of Banks in Singapore (ABS) announced that the consortium which they were leading had developed three system prototypes for the decentralized Real-Time Gross Settlement (RTGS) systems. Citi and Standard Chartered Bank (SCB) had officially joined the original consortium of nice financial institutions in the second phase of Project Ubin. The technology partners consisted of Accenture, R3, IBM, ConsenSys, and Microsoft in building out the prototypes of models \[[44](#chap7.xhtml#rref44)\].

The objective was to assess the potential implications of deploying distributed ledger technology (DLT) for specific RTGS functionalities by focusing on the fund transfer, queueing, and Liquidity Saving Mechanism (LSM). In addition, the phase also investigated how privacy in the RTGS system can be ensured using distributed ledger technologies.

Three software prototypes were developed by separate work-streams. Each prototype was built on a different platform — R3 Corda, Hyperledger Fabric, and Quorum running on a Microsoft Azure-based cloud infrastructure. The solutions were based a common set of business and functional requirements, in order to conduct a fair assessment and comparison on the three platforms. No quantitative or non-functional assessment was performed in all workstreams. In addition to a project report, detailed design specifications for each prototype, along with the source code were made open on MAS’s GitHub account. The codebase by MAS was under Apache License Version 2.0. Interested readers may refer to the link in reference \[[45](#chap7.xhtml#rref45)\] for more information.

[Figure 7.14](#chap7.xhtml#fig7-14) presents the functional scope of the Project Ubin Phase 2.

As shown in [Figure 7.14](#chap7.xhtml#fig7-14), there are six key criteria to be addressed, i.e., (i) digitalization of payments, (ii) decentralized processing, (iii) payment queue handling, (iv) transaction privacy, (v) settlement finality, and (vi) liquidity optimization.

Core RTGS functions such as gridlock resolution was implemented using distributed ledger technologies. The distributed and resilient infrastructure ensured no single point of failure. Queueing mechanism was developed to hold, prioritize, and cancel facilities. Relevant transaction details were only visible to the pre-defined parties. Unlike in Phase 1 where probabilistic settlement was used, all three prototypes used deterministic finality. The netting and liquidity saving algorithms were tested to maximize the liquidity efficiency.

Apart from the key findings and observations in Corda, Hyperledger Fabric, and Quorum, there were issues brought up by the consortium bank representatives. The issues included the cross-organizational resiliency, disaster recovery and high availability strategy, operating considerations associated with 24/7 operations, fair treatment of liquidity saving mechanism to all banks, cost effectiveness of decentralization for smaller banks, operational level agreement and service level agreement of node hosting arrangement, as well as impacts to the central bank’s role. It was worth pointing out that the roles of central banks in the decentralized RTGS systems may require it to transform from a centralized operator to system governor, auditor, and mediator, or overall liquidity manager.

![](images/p267.jpg)

**Figure 7.14.**The functional scope of Project Ubin Phase 2

In summary, the findings from Phase 2 demonstrated that all of Corda, Hyperledger Fabric, and Quorum can execute the key functions of fund transfer, queuing, and gridlock resolution in a modern RTGS system, without compromising transaction privacy. This phase discussed topic ranging from scalability, performance, and resilience, and identified areas where the prototypes can be enhanced prior to production.

*Phase 3: Delivery versus Payment (DvP)*

On August 24, 2018, MAS and Singapore Exchange (SGX) announced the plan to experiment on the Delivery versus Settlement (DvP) of tokenized assets across different distributed ledger platforms \[[46](#chap7.xhtml#rref46)\]. The tokenized assets were MAS-issued Singapore Government Securities (SGS) and an MAS-issued central bank digital currency in the form of Digital Singapore dollar \[[47](#chap7.xhtml#rref47)\].

Phase 3 extended the work in previous phases to develop capability, allowing corporate investors and financial institutions to perform simultaneous exchange and the final settlement of tokenized digital currencies and securities assets in order to improve the operational efficiency and reduce the settlement risks \[[48](#chap7.xhtml#rref48)\]. The prototype was developed by three companies — Anquan, Deloitte, and Nasdaq — as technology partners, seeking to achieve inter-ledger connectivity and settlement finality for SGS with cash-depository receipts (CDRs) on separate distributed ledgers. It leveraged open-source software developed and made publicly available in Phase 2, allowing for the transfer of tokenized assets such as SGS and CDRs on a trade-by-trade basis.

The followings are the defined project objectives:

*   To verify inter-ledger interoperability between cash and securities ledgers built on separate DLT platforms;
*   To mitigate counterparty risks in DvP by enabling recovery on cash and securities ledgers;
*   To achieve of DvP settlement finality 24/7 with clearing members by counterparties; and
*   To strengthen the investor confidence and an enhanced user experience in DvP with safe and sound recovery.

The high-level architecture is shown in [Figure 7.15](#chap7.xhtml#fig7-15).

As can be seen in [Figure 7.15](#chap7.xhtml#fig7-15), three prototypes have been built by Anquan, Deloitte, and Nasdaq. The cash and securities ledgers in each prototype are implemented using disparate technologies in order to investigate the interoperability as well as to achieve the DvP settlement. The Recognized Market Operator (RMO) role was the owner and operator of the network.

The RMO role had full visibility of transactions and acted as an Arbiter for dispute resolution. Cash and securities ledgers, managed by MAS and SGX respectively, were used to facilitate the issuance, storage, and transfer of cash and securities tokens. Buyers and sellers were exchange-registered trader who held cash and securities accounts.

![](images/p269.jpg)

**Figure 7.15.**Functional Scope of Project Ubin Phase 2

The prototypes have developed the following features in order to achieve a DvP fit for purpose.

*   *Time boundaries:* The seller to specify a time period before the settlement process is initiated, where cash and securities legs will take place;
*   *Contract locks:* The underlying assets have been locked and participants are unable to use them in other transactions until the contracts are discharged based on certain conditions;
*   *Account controls:* Counterparties to fulfill multi-signature conditions at certain steps of the settlement process;
*   *Self-enforcing smart contracts:* Self-enforcing codes to automate the processes as well as provide a greater degree of protection; and
*   *Secure secrets:* RMO-generated keys are sent to off-chain to transacting parties as a PDF file, providing an extra layer of security for post-trade tasks to achieve DvP finality.

The features and technologies were tested and evaluated in the DvP securities settlement scenarios, as follows:

*   Scenario I: Successful settlement;
*   Scenario II: Failed settlement with automatic recovery;
*   Scenario III: Failed transaction requiring arbitration; and
*   Scenario IV: Failed transaction with arbitration.

Through the experiments, some key design elements and the characteristics of the solutions developed by Anquan, Deloitte, and Nasdaq can be summarized in [Table 7.4](#chap7.xhtml#tab7-4).

**Table 7.4.**Comparison among Anquan, Deloitte, and Nasdaq solutions

![](images/p270.jpg)

The Project Ubin Phase 3 prototypes were able to successfully confirm a variety of positive and negative scenarios. In summary, the project demonstrated that DvP settlement finality, inter-ledger interoperability, and investor protection can be achieved through specific solutions designed and built on Blockchain technology.

*Phase 4: Cross-border Payment versus Payment (PvP)*  
On November 15, 2018, the Bank of Canada (BoC), the Bank of England (BoE), and the MAS jointly published a report which explores the proposals for new and more efficient hypothetical models that could enhance cross-border payments and settlements \[[49](#chap7.xhtml#rref49)\]. Subject matter experts from a group of commercial banks (HSBC, OCBS Bank, TD Bank, and UOB) have provided domain knowledge. By developing insights into the challenges and issues in cross-border payments, the project concluded that current initiatives underway are incremental changes, and in the longer term, there may need to be a paradigm shift to address the challenges, empowered by new technologies, such as blockchain. Some of the challenges for central banks, commercial banks, and end users are summarized as follows.

*   Central banks: 
    *   Restrictions by legacy systems to move to 24/7 operations.
    *   Proprietary standards and protocols, resulting in a lack of interoperability across networks and systems, and a diminished ability of in-country networks to adapt and facilitate innovation.
*   Commercial banks: 
    *   The complexity of a correspondent banking model accompanied by the divergence in regulatory standards across jurisdictions adds to the overall costs.
    *   Continuous Linked Settlement (CLS) offers payment-versus-payment settlement to 60 banks in only 18 currencies, with the constraints by the markets in which it operates.
    *   The opening window in the CLS system is not always available for spot trades, and may be short as it needs to coordinate with the opening hours of the RTGS systems.
    *   The limited range of currencies is dictated by the ability for a given RTGS operator to participate in the system, requiring significant legal and operational efforts.
*   End-users: 
    *   Lack of transparency in payments status and costs.
    *   Lack of transparency and visibility in the fees charged in the chain of correspondent banks, which increases the financial exposure of the end-user.
    *   Delay in payment processing due to separate bank guidelines and processes for cross-border payments.
    *   Service availability across multiple jurisdictions bounded by cut-off times.

To this end, the project has discussed three possible models that could potentially address the afore-going challenges.

*   Model 1: The collection of ongoing and planned industry initiatives
*   Model 2: The expanded role for in-country RTGS operators that act as “super-correspondents”, instead of relying on intermediaries.
*   Model 3a, 3b, and 3c: The variations based on wholesale CBDC, using tokenized limited access form of central bank liability.

The first two models enhance the existing domestic inter-bank payments systems without changing the existing correspondent banking model. The third model considers three variations based on issuing a wholesale CBDCs. Later on, MAS and BoC have integrated their respective experimental wholesale CBDCs network and conducted an experiment on cross-border payments. In the report \[[50](#chap7.xhtml#rref50)\], three potential approaches to enhance the cross-border payments using wholesale CBDCs were discussed, i.e., (i) the intermediary approach, (ii) the widened access approach, and (iii) the multi-currency approach. The intermediary approach has been implemented, as shown in [Figure 7.16](#chap7.xhtml#fig7-16).

As shown in [Figure 7.16](#chap7.xhtml#fig7-16), the prototype has built the cross-chain atomic swaps to achieve the inter-ledger value exchange. Readers interested in the hashed time-locked contracts (HTLC) is referred to \[[51](#chap7.xhtml#rref51)\]. There is one intermediary at either side of Singapore and Canada, each operating a Blockchain node. In theory, the HTLC can be used for more than two networks, but due to the scope of this project, atomic transactions involving three or more networks have not been tested. However, the HTLC also has limitations, for example, when the intermediary in the receiving end could not transfer the secret to the intermediary in the sending end within a prescribed period of time. In addition, the project assumes the networks run different platforms; however, this may not be true practically. The interledger value exchange can be more straightforward if both networks are based on the same protocol.

![](images/p273.jpg)

**Figure 7.16.**Overview of the linkage between BoC and MAS wholesale CBDCs platforms

*Phase 5: Enabling Broad Ecosystem Collaboration*  
Phase 5 is the final phase of Project Ubin, marking a successful conclusion of the experimental journey. This phase focuses on proof-of-value, laying out the foundation for future productionization efforts. As compared to Phase 4, the final phase develops a Blockchain-based multi-currency payments network that can facilitate multi-currency payments. Phase 5 network’s development is based on a high level of production fidelity by using the production-ready system by JP Morgan. The report begins with an architectural view of the Ubin 5 network and describes the key features \[[52](#chap7.xhtml#rref52)\]. In total, 16 use cases across capital markets, trade, and supply chain finance, issuance have been presented.

[Figure 7.17](#chap7.xhtml#fig7-17) presents the high-level architecture of Ubin 5 network.

In [Figure 7.17](#chap7.xhtml#fig7-17), the currency issuers refer to the entities that facilitate the issuance of digital currencies. The currency issuers can be central banks or commercial banks. The platform is built with a set of functionalities to perform the payments, DvP, conditional payments, and payment commitment. The platform is linked to end users’ wallets, such that the digital currencies can be circulated in third party ecosystems and platforms. [Table 7.5](#chap7.xhtml#tab7-5) presents the 16 use cases identified by the Ubin 5 project team.

With the completion of the five phases of Project Ubin, MAS has continued to lead the charge in the development of CBDCs, especially in experiments and productionization of blockchain technologies. The open-source policy and collaborative approach are widely recognized by the international community.

![](images/p274.jpg)

**Figure 7.17.**Project Ubin Phase 5 system architecture

**Table 7.5.**The 16 use cases identified by the Project Ubin Phase 5 project team \[[52](#chap7.xhtml#rref52)\]

 
| **Focus area** || **Description** || **User case** |
| --- | --- | --- |
| Private Equities || Private exchange to facilitate trading of equities in privately-held companies || 1exchange |
| --- | --- | --- |
| Private Equities || Platform for issuance, custody, and trading of digital securities || iSTOX |
| Bonds || Trading and settlement platform for issuance and lifecycle management of digital securities || STACS |
| Syndicated Loans || Primary syndication and secondary trading of syndicated loans || iLex + IHS Markit |
| Investment || Infrastructure assets funding, in a low-cost and secure manner || Allinfra |
| Payments || Cross-border securities settlement and dividend payments using digital currencies || Sygnum |
| Supply Chain || Procure-to-Pay platform for exchanges of trade documents || Digital Ventures |
| Supply Chain || Unified platform to connect buyers and sellers for orders, logistics, and payments || Invictus |
| Supply Chain || Exchange, verification, and automatic matching of trade data || Marco Polo |
| Supply Chain || Electronic matching of trade data for bank payment obligation transactions || essDOCS |
| Financing || Supply chain financing for SMEs with non-bank institutional capital || Crediti |
| Healthcare || Lifecycle management of insurance claims || Digital Asset |
| Insurance || Sharing and recording of information for automobile insurance claims || Inmediate |
| Media and Advertising || Streamlining digital supply chain of programmatic advertising || Aqilliz |
| Payments || HR payments solution for real-time, accurate salary payments || Octomate + Adecco |

**7.6Conclusions**

The outbreak of the COVID-19 pandemic has imposed significant challenges in the global economy. Various efforts are spent to lessen the impact, supporting businesses and individuals to tide through the unprecedented difficulty. Among various approaches, Central Bank Digital Currencies (CBDCs) is being actively discussed and debated as an option to help improve the effectiveness of government measures. However, we face both opportunities and challenges in this financial innovation, attributing to its novelty, complexity, and maturity levels. This chapter presents the fundamentals, motivations, opportunities, and challenges of CBDCs against the backdrop of the global pandemic. Based on the analysis, the development of CBDCs will have to be executed following a phased approach in order to achieve the grand ambitions. Central banks should stay focused on the destination, lead the charge of development, and be prudent in every step of execution.

History has proved that trust alone, as a given property in CBDCs, does not automatically warrant a successful future. Commercial banks may face challenges during the transition and need to mitigate the risks in the transition, but CBDCs are tremendous opportunities to innovate and upgrade their capabilities. Ultimately, businesses and individuals are the ones benefiting from the innovation. For a promising future, the industry must continue working collaboratively to improve the Technology Readiness Level (TRL) of smart contracts and blockchain technologies.

**References**

[1](#chap7.xhtml#ref1).G. Falk, P.D. Romero, I. Nicchitta, and E. Nyhof, “Unemployment Rates During the COVID-19 Pandemic”, Congressional Research Service, R46554.

[2](#chap7.xhtml#ref2).C. Saw, J. Lin, and Y. Wong, “Impact of the COVID-19 Pandemic on the Singapore Economy”, Economic Survey of Singapore First Quarter 2020, pp. 36–44, 2020.

[3](#chap7.xhtml#ref3).International Monetary Fund, “Policy Responses to COVID-19”, Available: [https://www.imf.org/en/Topics/imf-and-covid19/Policy-Responses-to-COVID-19](https://www.imf.org/en/Topics/imf-and-covid19/Policy-Responses-to-COVID-19)

[4](#chap7.xhtml#ref4).Our World Data, “Coronavirus Vaccinations”, Available: [https://ourworldindata.org/covid-vaccinations](https://ourworldindata.org/covid-vaccinations)

[5](#chap7.xhtml#ref5).C. Aschwanden, “Five Reasons Why COVID Herd Immunity is Probably Impossible”, *Nature,* Vol. 591, pp. 520–522, 2021, March 18, 2021.

[6](#chap7.xhtml#ref6).B. Broadbent, “Central Banks and Digital Currencies”, BIS Central Bankers’ Speeches, March 2, 2016.

[7](#chap7.xhtml#ref7).M. D. Bordo and A. T. Levin, “U.S. Digital Cash: Principles & Practical Steps”, Hoover Institution Economics Working Papers, No. 19101, January 2019.

8.J. Barrdear and M. Kumhof, “The Macroeconomics of Central Bank Issued Digital Currencies”, Bank of England Staff Working Paper, No. 605, July 2016.

9.W. Engert and B. Fung, “Central Bank Digital Currency: Motivations and Implications”, Bank of Canada Staff Discuss Paper, No. 2017-16, November 2017.

10.K. E. Gurtler, K. Rasmussen, S. T. Nielsen and M. Spange, “Central Bank Digital Currency in Denmark”, Danmarks Nationalbank Analysis, No. 28, December 2017.

[11](#chap7.xhtml#ref11).Bank of International Settlement, “Central Bank Digital Currencies”, Committee on Payments and Market Infrastructure, March 2018.

12.M. Kumhof and C. Noone, “Central Bank Digital Currencies — Design Principles and Balance Sheet Implications”, Bank of England Staff Working Paper, No.725, May 2018.

13.J. Kiff, J. Alwazir, S. Davidovic, G. Huertas and A. Khan, T. Khiaonarong, M. Malaika, H. Monroe, N. Sugimoto, H. Tourpe, P. Zhou, “A Survey of Research on Retail Central Bank Digital Currency”, International Monetary Fund Working Paper, WP/20/104, June 2020.

14.U. Bindseil, “Tiered CBDC and the Financial System”, European Central Bank Working Paper Series, No. 2351, January 2020.

[15](#chap7.xhtml#ref15).T. Wilson, *HSBC Bans Customers from Buying Bitcoin-backer MicroStrategy Shares,* Available: [https://www.reuters.com/business/\_nance/hsbc-bans-customers-buying-bitcoin-backer-microstrategy-shares-2021-04-12/](https://www.reuters.com/business/_nance/hsbc-bans-customers-buying-bitcoin-backer-microstrategy-shares-2021-04-12/), June 2021.

[16](#chap7.xhtml#ref16).Temasek News. *Temasek, DBS, J.P. Morgan and Temasek to Establish Platform to Transform Interbank Value Movements in A New Digital Era* \[Online\], Available: [https://www.temasek.com.sg/en/news-and-views/newsroom/news/2021/dbs-jp-morgan-temasek-establish-platform-to-transform-interbank-value-movement-new-digital-era](https://www.temasek.com.sg/en/news-and-views/newsroom/news/2021/dbs-jp-morgan-temasek-establish-platform-to-transform-interbank-value-movement-new-digital-era), Apr 28, 2021.

[17](#chap7.xhtml#ref17).Bank of International Settlement, *Multiple CBDC (mCBDC)Bridge* \[Online\], Available: [https://www.bis.org/about/bisih/topics/cbdc/mcbdcbridge.htm](https://www.bis.org/about/bisih/topics/cbdc/mcbdcbridge.htm), June 2021.

[18](#chap7.xhtml#ref18).People’s Bank of China, *Progress of Research* & *Development of E-CNY in China* \[Online\], Available: [http://www.pbc.gov.cn/en/3688110/3688172/4157443/4293696/2021071614584691871.pdf](http://www.pbc.gov.cn/en/3688110/3688172/4157443/4293696/2021071614584691871.pdf), 2021.

[19](#chap7.xhtml#ref19).CBDC Tracker, *Central Bank Digital Currency Tracker* \[Online\], Available: [https://cbdctracker.org](https://cbdctracker.org), 2021.

[20](#chap7.xhtml#ref20).World Bank, “The Unbanked”, The Global Index Database, 2017.

[21](#chap7.xhtml#ref21).A. Fowers and H. Long, *Months Later, More Than 1 Million Americans are Still Waiting for Unemployment Aid* \[Online\], Available: [https://www.washingtonpost.com/business/2021/01/04/unemployment-never-recevied](https://www.washingtonpost.com/business/2021/01/04/unemployment-never-recevied), 2021.

[22](#chap7.xhtml#ref22).M. Belinky, E. Rennick and A. Veitch, *The Fintech 2.0 Paper: Rebooting Financial Services* \[Online\], Available: [https://www.oliverwyman.com/content/dam/oliver-wyman/global/en/2015/jun/The\_Fintech\_2\_0\_Paper\_Final\_PV.pdf](https://www.oliverwyman.com/content/dam/oliver-wyman/global/en/2015/jun/The_Fintech_2_0_Paper_Final_PV.pdf), 2021.

[23](#chap7.xhtml#ref23).J. Barrdear and M. Kumhof, “The Macroeconomics of Central Bank Issued Digital Currencies”, Bank of England Staff Working Paper, No. 605, July 2016.

[24](#chap7.xhtml#ref24).Federal Reserve System, *How much does it cost to produce currency and coin?* \[Online\], Available: [https://www.federalreserve.gov/faqs/currency12771.htm](https://www.federalreserve.gov/faqs/currency12771.htm), 2021.

[25](#chap7.xhtml#ref25).S. W. Lo, Y. Wang and D. K. C. Lee, “Blockchain and Smart Contracts: Design Thinking and Programming for Fintech, World Scientific, Singapore, 2021.

[26](#chap7.xhtml#ref26).T. A. D. Tien, R. Liu, M. Zhang, G. Chen, B. C. Ooi and J. Wang, “Un-tangling Blockchain: A Data Processing View of Blockchain Systems”, *IEEE Transactions on Knowledge and Data Engineering,* 2017.

[27](#chap7.xhtml#ref27).D. Chaum, “Computer Systems Established, Maintained, and Trusted by Mutually Suspicious Groups”, Ph.D. Thesis, University of California, Berkeley, 1982.

[28](#chap7.xhtml#ref28).S. Haber and W. S. Stornetta, “How to Time-stamp a Digital Document”, *Journal of Cryptology,* No. 3, pp. 99–111, January, 1991.

[29](#chap7.xhtml#ref29).S. Nakamoto, *Bitcoin: A Peer-to-peer Electronic Cash System* \[Online\], Available: [https://bitcoin.org/bitcoin.pdf](https://bitcoin.org/bitcoin.pdf), 2008.

[30](#chap7.xhtml#ref30).N. Szabo, *Smart Contract* \[Online\], Available: [https://www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart.contracts.html](https://www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart.contracts.html), 1994.

[31](#chap7.xhtml#ref31).B. Hu, F. Kwan, M. Ng, L. Lee, R. Craig and L. Sun, “Integration of Blockchain Transactions with Off-chain Processing”, Singapore, Patent Application No. PCT/SG2021/050143, March, 18, 2021.

[32](#chap7.xhtml#ref32).Mastercard, *Mastercard Launches Central Bank Digital Currencies (CBDCs) Testing Platform, Enabling Central Banks to Assess and Explore National Digital Currencies* \[Online\], Available: [https://investor.mastercard.com/investor-news/investor-news-details/2020/Mastercard-Launches-Central-Bank-Digital-Currencies-CBDCs-Testing-Platform-Enabling-Central-Banks-to-Assess-and-Explore-National-Digital-Currencies/default.aspx](https://investor.mastercard.com/investor-news/investor-news-details/2020/Mastercard-Launches-Central-Bank-Digital-Currencies-CBDCs-Testing-Platform-Enabling-Central-Banks-to-Assess-and-Explore-National-Digital-Currencies/default.aspx), 2021.

[33](#chap7.xhtml#ref33).Consensys, *Introducing the Codefi Payments Sandbox for Digital Currencies* \[Online\], Available: [https://consensys.net/blog/codefi/the-digital-currency-technology-sandbox-powered-by-codefi-payments/](https://consensys.net/blog/codefi/the-digital-currency-technology-sandbox-powered-by-codefi-payments/)

[34](#chap7.xhtml#ref34).Bank of International Settlements, “Principles for Financial Market Infrastructure”, Technical Committee of the International Organisation of Securities Commissions, April 2012.

[35](#chap7.xhtml#ref35).IEEE, *Blockchain and Distributed Ledger Standards Committee* \[Online\], Available: [https://sagroups.ieee.org/bdlsc/](https://sagroups.ieee.org/bdlsc/), 2021.

[36](#chap7.xhtml#ref36).M. Kumhof and C. Noone, “Central Bank Digital Currencies — Design Principles and Balance Sheet Implications”, Bank of England Staff Working Paper, No. 725, May 2018.

[37](#chap7.xhtml#ref37).W. Bossu, M. Itatani, C. Margulis, A. Rossi, H. Weenink and A. Yoshinaga, “Legal Aspects of Central Bank Digital Currency: Central Bank and Monetary Law Considerations”, IMF Working Paper, No. 2020/254, November 20, 2020.

[38](#chap7.xhtml#ref38).J.C. Boggs, M. Hanson, J. King and G. William, *FedNow Service Pilot Program Gaining Traction and Support* \[Online\], Available: [https://www.jdsupra.com/legalnews/fednow-service-pilot-program-gaining-2523613/](https://www.jdsupra.com/legalnews/fednow-service-pilot-program-gaining-2523613/), 2021.

[39](#chap7.xhtml#ref39).Hong Kong Monetary Authority, *Joint Statement on the Multiple Central Bank Digital Currency (m-CBDC) Bridge Project* \[Online\], Available: [https://www.jdsupra.com/legalnews/fednow-service-pilot-program-gaining-2523613/](https://www.jdsupra.com/legalnews/fednow-service-pilot-program-gaining-2523613/), Feb 2021.

[40](#chap7.xhtml#ref40).L. L. Siu, “Coercing Consensus: Unintended Success of the Octopus Electronic Payment System”, *PISTA,* 2008.

[41](#chap7.xhtml#ref41).A. Grym, “Lessons Learnt from the World’s First CBDC”, Bank of Finland Economic Review, No. 8, 2020.

[42](#chap7.xhtml#ref42).Monetary Authority of Singapore, *Project Ubin: Central Bank Digital Money Using Distributed Ledger Technology* \[Online\], Available: [https://www.mas.gov.sg/schemes-and-initiatives/project-ubin](https://www.mas.gov.sg/schemes-and-initiatives/project-ubin)

[43](#chap7.xhtml#ref43).Monetary Authority of Singapore, *The future is here: Project Ubin: SGD on Distributed Ledger* \[Online\], Available: [https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin--SGD-on-Distributed-Ledger.pdf](https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin--SGD-on-Distributed-Ledger.pdf)

[44](#chap7.xhtml#ref44).Monetary Authority of Singapore, *Project Ubin Phase 2: Re-imagining Interbank Real-Time Gross Settlement System Using Distributed Ledger Technologies* \[Online\], Available: [https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin-Phase-2-Reimagining-RTGS.pdf?la=en&hash=02722F923D88DE83C35AF4D1346FDC2D42298AE0](https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin-Phase-2-Reimagining-RTGS.pdf?la=en&hash=02722F923D88DE83C35AF4D1346FDC2D42298AE0)

[45](#chap7.xhtml#ref45).Project Ubin GitHub, [https://github.com/project-ubin](https://github.com/project-ubin)

[46](#chap7.xhtml#ref46).Monetary Authority of Singapore, *MAS and SGX Partner Anquan, Deloitte and Nasdaq to Harness Blockchain Technology for Settlement of Tokenised Assets* \[Online\], Available: [https://www.mas.gov.sg/news/media-releases/2018/mas-and-sgx-partner-anquan-deloitte-and-nasdaq-to-harness-blockchain-technology](https://www.mas.gov.sg/news/media-releases/2018/mas-and-sgx-partner-anquan-deloitte-and-nasdaq-to-harness-blockchain-technology)

[47](#chap7.xhtml#ref47).Monetary Authority of Singapore, *MAS and SGX Successfully Leverage Blockchain Technology for Settlement of Tokenised Assets* \[Online\], Available: [https://www.mas.gov.sg/news/media-releases/2018/mas-and-sgx-successfully-leverage-blockchain-technology-for-settlement-of-tokenised-assets](https://www.mas.gov.sg/news/media-releases/2018/mas-and-sgx-successfully-leverage-blockchain-technology-for-settlement-of-tokenised-assets)

[48](#chap7.xhtml#ref48).Monetary Authority of Singapore, *Delivery versus Payment on Distributed Ledger Technologies* \[Online\], Available: [https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin-DvP-on-Distributed-Ledger-Technologies.pdf?la=en&hash=2ADD9093B64A819FCC78D94E68FA008A6CD724FF](https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin-DvP-on-Distributed-Ledger-Technologies.pdf?la=en&hash=2ADD9093B64A819FCC78D94E68FA008A6CD724FF)

[49](#chap7.xhtml#ref49).Monetary Authority of Singapore, *Cross-border Interbank Payments and Settlements — Emerging Opportunities for Digital Transformation* \[Online\], Available: [https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Cross-Border-Interbank-Payments-and-Settlements.pdf?la=en&hash=5472F1876CFA9439591F06CE3C7E522F01F47EB6](https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Cross-Border-Interbank-Payments-and-Settlements.pdf?la=en&hash=5472F1876CFA9439591F06CE3C7E522F01F47EB6)

[50](#chap7.xhtml#ref50).Monetary Authority of Singapore, *Design Paper: Enabling Cross-Border High Value Transfer using DLT* \[Online\], Available: [https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Jasper-Ubin-Design-Paper.pdf?la=en&hash=437222C94FD39314FB4C685EA31FC3AAA5CA5DA1](https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Jasper-Ubin-Design-Paper.pdf?la=en&hash=437222C94FD39314FB4C685EA31FC3AAA5CA5DA1)

[51](#chap7.xhtml#ref51).J. Frankenfield, *Hashed Timelock Contract* \[Online\], Available: [https://www.investopedia.com/terms/h/hashed-timelock-contract.asp](https://www.investopedia.com/terms/h/hashed-timelock-contract.asp)

[52](#chap7.xhtml#ref52).Monetary Authority of Singapore, Project Ubin Phase 5: Enabling Broad Ecosystem Opportunities \[Online\], Available: [https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin-Phase-5-Enabling-Broad-Ecosystem-Opportunities.pdf](https://www.mas.gov.sg/-/media/MAS/ProjectUbin/Project-Ubin-Phase-5-Enabling-Broad-Ecosystem-Opportunities.pdf)

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap7.xhtml#fn1)See Bordo and Levin’s paper titled “U.S. Digital Cash: Principles & Practical Steps” (see Reference section \[[7](#chap7.xhtml#rref7)\]) for a comprehensive review of the design principles of digital cash.

[²](#chap7.xhtml#fn2)M0 is the most liquid measure of the money supply including coins and notes in circulation and other assets that are easily convertible into cash.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0008](https://doi.org/10.1142/9789811250903_0008)

Chapter 8

**Artificial Intelligence and Machine Learning in Data Management**

***Zhiyu Ge***

**8.1Introduction**

In the Big Data era, data management plays a vital role in information processing, knowledge accumulation, decision making, and ultimately the survival and growth of a data-focused organization. Highly effective and efficient data management paves the way for the organization to harness the full potential of its data assets for analytics, business intelligence (BI), and machine learning (ML) to unleash the full power or might of its data assets to generate timely and valuable business insights.

Data preparation often is the most time/resource consuming task in an artificial intelligence (AI)/ML project. The importance of an effective and efficient data management framework to the success of AI/ML programs cannot be overestimated. First, data needs to be integrated. Assembling features for ML model training typically require data extraction from multiple sources and often involves both structured and unstructured data and require extensive data mastering work. Second, for large-scale ML projects, data can be voluminous and therefore requiring a highly scalable data management system. Third, accurate and reliable AI/ML applications depend on the breadth and quality of data, which only a well-controlled and well-functioning data management system can deliver. Sound data management provides a solid foundation for building data driven applications including AI/ML. AI/ML can be incomprehensible and unreliable without the support from sound data management.

Reciprocally in the other direction, AI/ML can also improve effectiveness and/or efficiency of data management and help meet a multitude of data management challenges arising from:

*   Multiple data sources,
*   Diversity in data format, quality, and complexity, in particular for unstructured data in NoSQL databases and BLOB stores,
*   Sheer data volume, and
*   The need for high throughput processing (e.g., Hadoop/Spark based distributed processing) and real-time streaming.

Rule-based systems alone cannot meet the high demands of today’s enterprise Big Data management, and AI/ML can be leveraged to supplement the traditional approach to achieve greater agility, faster speed, and more optimized cost-efficiency in modern data management. In some cases, AI/ML algorithms may even be the only feasible solutions to accomplish convoluted data management tasks at scale. Just like AI/ML techniques can be very useful tools for making data driven decisions for business success, they can also be very helpful for making data driven decisions on data for more scalable, more automated, and more effective data management.

Modern data management systems have already built in a variety of AI/ML functionalities as integral components to achieve better data governance, easier data discovery, and sensitive data identification, more transparent data lineage, higher data quality, enhanced scalability, more versatility, and wider automation. Even for legacy data management systems, integrating AI/ML to at least some part of the data workflows can improve efficiency and effectiveness on top of existing infrastructure. The impact of AI/ML on data management is the focus of discussion in this chapter.

**8.2Areas of Application**

There have already been successful AI/ML applications in a variety of data management and governance workflows, along with many other promising potential use cases. The following application areas are discussed separately in more details:

*   Data acquisition, cleansing, and maintenance
*   Data mastering to build single source of truth and Business 360
*   Data cataloging and lineage
*   Synthetic data generation
*   DataOps workload and workflow optimization
*   Data privacy, security, auditing, and compliance

**8.2.1*Data Acquisition, Cleansing, and Maintenance***

AI/ML-based techniques have been used to identify data entry, data extraction, and data creation patterns to allow automatic data capture, automatic information extraction (IE) from unstructured data, and automatic attribute assignment/value imputation. A simple example of AI-driven data capture is the auto-fill feature that many of us have first-hand experience with when we fill out online forms. Extensive literature is available on ML methodologies to extract structured information from text, speech, image, and video data with numerous real-world applications. Various automated data entry applications, such as invoice scanning, form processing, and web scraping, have been developed based on those advanced IE techniques.

Big Data cleaning can be viewed as a large-scale ML problem, where data errors are treated as signals and ML algorithms can be used for signal detection as well as identifying correlations and dependencies among these signals. In this sense, data repair can be formulated as a problem of predicting the correct values for erroneous or missing data entries. Repair can be done either within the same ML algorithms for detection or in combination with separate traditional/ML algorithms. We can use AI/ML to detect the patterns of data problems as well as the patterns in the patterns of data problems (metapatterns). While understanding patterns helps to surface data problems automatically, understanding metapatterns can help to produce rules for surfacing new/unseen types of data problems.

In addition to automated data capturing, outlier/error detection, and data repair, AI/ML algorithms can also help optimize data backup strategies for data loss prevention and establish an automated disaster recovery protocol. ML can also be used to recover data from failed data storage devices.

**8.2.2*Data Mastering to Build a Single Source of Truth***

Data mastering is the core process of reconciling and unifying data from various sources. In the course of normal business operations, organizations may have generated siloed data within their individual business units, or their in-house data may only provide a partial view of their clients and/or markets. To obtain a more holistic view on entities of interest (suppliers, customers, products, services, etc.), data from different sources need to be integrated. Augmenting or enhancing existing data mastering processes with AI/ML can help improve efficiency and effectiveness in master data discovery, master data extraction, data structure and association identification, semantic mapping/schema matching, and entity resolution (deduplication, record linkage, and canonicalization). In the era of Big Data, AI/ML provides the important tools for revealing intricate data linkages, scaling out master data workflow, automating conflict resolution, and if done right, reducing the number of exceptions requiring manual overrides.

Legacy data system migration is often a daunting task. Legacy data may be structured or unstructured, may reside in multiple places and in multiple formats, and may be inconsistent or incompatible with one another or with current data platforms. The same data mastering techniques discussed above can be applied to automate the conversion and integration process at scale to help address those challenges.

**8.2.3*Data Cataloging and Lineage***

A data catalog is an organized inventory of data assets. It contains a collection of metadata, together with tools for working with such metadata that enable data discovery, data search, data tracking, data evaluation (for suitability of intended use), and inventory management and reporting, etc. Creating and maintaining a data catalog involves data and metadata identification/tagging, classification, semantic mapping, identification of data relationships for data linkage, and dependency tracking. Given the large variety of data sources and formats combined with huge data volume and intricate relationships among data assets, AI/ML can help to intelligently automate these steps, enabling functionalities such as ML recommendations for data search and discovery, natural language querying, intelligent data lineage tracing, and dynamic data masking for privacy enhancement, etc. AI/ML-powered data catalogs lead to easier data access, better data utilization, enhanced data interpretability, and improved data governance.

**8.2.4*Synthetic Data Generation***

Synthetic data are data not directly observed or measured but rather generated programmatically. They are often used as a surrogate for the real data to reduce cost, protect privacy, and facilitate application testing. Generally, in order for synthetic data to be useful, it needs to capture the important characteristics and relationships in the data it intends to mimic. For tasks involving complicated data structures, simple rule-based algorithms and expert systems may fail to synthetically simulate new data that resemble the original data. This is where deep learning algorithms may be helpful to capture convoluted/hidden structures and patterns in the real data to preserve utility of simulated data. AI/ML-based synthetic data generation algorithms have found successful applications in computer vision, neural programming, bioinformatics, natural language processing (NLP), software/ML algorithm development and testing, data privacy protection, and environment simulation, etc. For example, for financial fraud detection, we may not be able to observe confirmed real fraud cases for modeling purpose. However, we may develop/test models using synthetic data for which we know the “real” events. As another example, for data privacy protection, we can filter sensitive data and replace them with synthetic information so that analytical insights can still be extracted while maintaining compliance with data privacy laws and regulations. For companies operating in multiple regions/countries, synthetic data may also be used to facilitate cross-border data sharing and pooling.

**8.2.5*DataOps Workload and Workflow Optimization***

Sheer volume, high velocity, and presence of unstructured data are among the main reasons for difficulties in Big Data management for DataOps. On top of advanced IT technologies in storage, distributed computing, and networking, many DataOps workloads (e.g., database/system administration, ETL, backup jobs, model serving, BI, and analytics) can be further optimized with AI/ML techniques. Here are a few examples.

AI/ML algorithms can help us optimize data storage by intelligently classifying data into storage classes (from hot to cold) and making storage recommendations. In particular, organizations typically retain a significant portion of their data for compliance purposes only. Identification and management of such dark data may have a big cost implication. AI/ML techniques can help to sort through the dark data and make classification/retention recommendations to assist human decision.

For database indexing, instead of the traditional BTrees, Hash maps and Bloom filters, more flexible, faster, and smaller machine learned neural networks can be used to capture critical data structures at scale \[[1](#chap8.xhtml#rref1)\]. Not only does this approach provide a systematic way to accommodate and produce customized indexes for different data structures, the learned indexes can also be retrained as the underlying databases evolve. Another way to improve query performance materially is to optimize database caching strategies with ML.

IT systems including data systems generate huge amounts of machine data daily. Such log data may not be human readable, unless to IT specialists. Even for the experts, it is not efficient reading the logs line by line. Instead, they rely on query tools and analytics to make sense of such data. AI/ML techniques come in handy to help analyze telemetry data supplied by data systems, monitor system performance/utilization, monitor data access, and provide performance optimization recommendations in real time. More broadly for system resource management, AI/ML tools can help with resource planning and onboarding, job prioritizing/scheduling, workload-aware autoscaling, compute cluster management, and service disruption identification/avoidance. AI/ML can also be leveraged to analyze data from algorithm/model performance monitoring and software performance monitoring, and facilitate automated application development/testing and continuous integration and continuous deployment (CI/CD). Last but not least, AI/ML can play a productive role in improving human–machine interaction interface through NLP techniques.

**8.2.6*Data Privacy, Security, Auditing and Compliance***

Multiple data sources, distributed storage/computing in Big Data processing, and the proliferation of unstructured data have brought significant challenges in managing data privacy and security. Huge data volumes and the complexity in managing multiple data platforms exacerbate the problem. AI/ML can help address these challenges.

Traditional rule-based algorithms to identify sensitive data such as personally identifiable information (PII) may have difficulties handling the large variety of data sources and data formats, especially with sensitive data embedded in unstructured data. There are ML algorithms that scan through large amounts of texts, documents, and images to automatically detect and/or mask PIIs on the fly. Other AI/ML-based tools are also available to track lineage of PII when datasets are copied or transformed for downstream processes.

For information security, AI/ML tools can help monitor data access patterns to detect and mitigate unauthorized or fraudulent access in real time. Granular data access policies at various levels (e.g., data file, table, column/row, and cell) can be automatically and dynamically generated, and enforced based on user profile and project requirements. Data incident patterns can also be learned to allow automated incidence prevention. Data access logs can be analyzed and classified for compliance breaches and provide a structured audit trail for further investigation. Data policy requirements can be checked automatically prior to data retirement to verify eligibility with respect to retention period, as well as whether such data is involved in any ongoing litigation. AI/ML can also help with other legal or regulatory compliance tasks such as the identification of natural persons for General Data Protection Regulation (GDPR).

**8.3AI/ML Methods for Data Management**

A large variety of ML algorithms have either found their way into or can be applied in assisting sophisticated data management tasks at scale. The high-level review of common ML modeling approaches below is applicable to use cases for data management and beyond. More details can be found in [Chapter 3](#chap3.xhtml).

![](images/p288.jpg)

**Figure 8.1.**Common AI/ML approaches applicable to data management workflows

**8.3.1*Supervised Learning***

Supervised learning involves labeled data, and the goal is to establish a functional relationship between response and features to predict the response for additional/new observations. Common supervised learning tasks include classification and regression.

Supervised learning can be used to assist in data management tasks such as PII identification, data classification, named entity recognition, data error correction, missing value imputation, semantic mapping, data recommendation systems, etc.

Supervised learning often requires sufficiently large and good quality labeled data, which is typically a luxury in data management applications. More commonly, we have either unlabeled data or partially labeled data at hand. In those situations, unsupervised, semi-supervised, or weakly-supervised learning techniques may be employed.

**8.3.2*Unsupervised Learning***

In contrast to supervised learning, unsupervised learning mainly deals with unlabeled data. Its goal is to discover previously unknown patterns and association/correlation information embedded in the data (as opposed to predictions). Unsupervised learning can be used to perform the following data analyses (with typical algorithms), besides clustering and dimensionality reduction:

*   Data association/correlation identification: association rule learning
*   Detection of unspecified signals or patterns including anomaly detection: one-class SVM, local outlier factor, isolation forest, replicator neural networks, autoencoders, variational autoencoders, Bayesian network, hidden Markov model, deviations from association rules and frequent itemsets \[[2](#chap8.xhtml#rref2)\], cluster analysis-based outlier detection, etc.
*   Probability distribution fitting, density estimation, and simulation: mixture models, kernel density estimation, spectral density estimation, method of moments, maximum likelihood method, Boltzmann machines, variational autoencoders, generative adversarial networks (GAN), etc.

Unsupervised learning can be used to assist in data management tasks such as data cleaning, incremental semantic mapping, data cataloging, schema matching, synthetic data generation, data loss prevention (data intrusion detection and corrupted data identification), and data recommendation systems, etc.

A learning approach between supervised learning and unsupervised learning is the so-called semi-supervised learning, which trains the model using a relatively small amount of labeled training data together with a relatively large amount of unlabeled training data. Similarly, weakly-supervised learning further considers training data with noisy labels \[[3](#chap8.xhtml#rref3)\]. Both semi-supervised learning and weakly-supervised learning can work with and improve upon existing supervised learning approaches to handle more realistic data labeling mechanisms in data management applications.

**8.3.3*Other Learning Approaches***

There are many additional machine learning approaches applicable for data management, such as Reinforcement learning (RL), Active learning, Transfer learning, Multi-task learning, Meta-learning, Federated learning, etc.

For example, reinforcement learning is a policy-driven approach on rewarding desired behaviors and/or punishing undesired ones. It can be used to assist in data management related tasks such as job scheduling, resource management, network traffic scheduling, database query processing, synchronization for sensor data streaming and IoT data streaming, and data recommendation systems/dialog agents, etc.

Meta-learning (also commonly referred to as learning-to-learn) focuses on learning from multiple learning episodes to improve learning algorithms, which is in contrast to conventional ML using data instances for prediction, classification, and pattern recognition. Although some better-known ML techniques such as hyperparameter tuning by cross-validation and active learning can be viewed as special instances of meta-learning, more broadly, its main objective is to learn the meta-knowledge, or knowledge that are common across learning tasks, and generalize it to new learning tasks. By leveraging the meta-knowledge, meta-learning intends to reduce the learning effort and/or improve the learning quality of learning procedures for new learning tasks. While each individual learning episodes have their own learning objectives, in a meta-learning setting, there is also an explicitly defined meta-level objective. Examples of meta-objective include, for example, optimizing certain predictive performance metrics over learning episodes, the fast adaptation of learning algorithm to new learning task (with or without the presence of a domain-shift), and optimizing the learning algorithm for adversarial defense. A good survey of meta-learning objectives, meta-knowledge representation, meta-optimization approaches, and meta-learning applications is conducted by Hospedales *et al.* \[[6](#chap8.xhtml#rref6)\]. One important area of application for meta-learning is few-shot learning, in which a base model can be improved upon with only very limited amount of task-specific labeled data available. This has a significant implication to many AI/ML applications in data management, as often times labeled data are expensive to curate. Of course, since meta-learning typically involves compute-intensive bilevel optimization (an optimization problem nested within another), computation cost, in terms of both time and memory, may be large. Distributed computing frameworks such as Apache Ray can help here. Apache Ray already has demonstrated success in large-scale hyperparameter tuning, and it can conceivably be a great tool for general bilevel optimization problems as well.

**8.3.4*Knowledge Graphs for Information Management and Data Governance***

The knowledge graph (KG) provides a unified framework to capture, manage, and make use of all information (concepts, hierarchies, relationships, interactions, etc.) associated with data, metadata, data system architectures, data access control/logs, security incident identification/mitigation, data policies, data access policies, compliance policies, analytics, data processes or workflows, BI dashboards or reports, and applications or APIs that produce/consume data, etc. It can encompass information about almost all components of data management. For example, it can provide an effective tool to support the overall management of data availability, relevancy, usability, integrity, lineage, provenance, and security in an enterprise. The basic architecture of KG itself makes it an ideal tool for capturing and exploring relationships among data objects. Data catalog and lineage can themselves be a subset of this KG, and data security, data mastering, and data governance can all benefit directly from it. It enables self-service. Users can query the knowledge base to obtain information about data, analytics, reports, policies, standards, procedures, and more. The search for relevant data objects and data information can be facilitated by chatbots, for example, the Risk ML Bot by CapitalOne \[[4](#chap8.xhtml#rref4)\] for real-time credit exposure monitoring/trend predicting.

The KG built for data management can incorporate business glossary, and be linked to the broader business domain knowledge graph that covers all elements of the business ontology. Incorporating data management KG into the broader enterprise business KG provides an important avenue to integrate data into day-to-day business operations and risk management.

Knowledge graphs are flexible and dynamic, allowing the organization to simplify knowledge discovery, facilitate better data connection (among data, data producers and data users), correct/update information more easily, produce better data insights, and continuously expand the existing knowledge base by capturing new concepts, entities, and relationships. As an AI tool itself, the KG can feed into other AI/ML applications to help produce more powerful information-driven business insights. Other AI/ML techniques (such as NLP and neural symbolic computing) can also be leveraged in the development of the data management knowledge graph and the broader enterprise business knowledge graph.

Knowledge graphs can provide another route for data integration involving legacy data systems. Instead of directly converting all the legacy data, for certain applications, it may be sufficient to use specific pieces of structured data and/or metadata extracted from legacy sources to link legacy data with other data assets. This integration approach does not require transforming and merging of the underlying legacy data itself, but rather, it provides a summary of legacy data and establishes the data connections at a semantic level for data cataloging, information fusion, and new insight generation. Such a KG in turn can help standardize data integration across legacy and modern data systems, and serve as a unified platform for data discovery, data utilization, and data governance. More information on this can be found in [Chapter 5](#chap5.xhtml).

**8.4Available AI/ML Platforms and Software Solutions for Data Management Applications**

The previous sections provide an overview of AI/ML application areas and general ML approaches for data management. This section focuses on data/analytics platforms and software solutions that leverage AI/ML tools for data management tasks. These platforms and solutions can be integrated into ETL pipelines, as well as analytics and ML workflows.

Let us start with some special purpose platforms and AI/ ML-assisted software solutions designed to tackle specific data management challenges.

*   Data crowdsourcing platforms generate data labels by a group of experts/non-experts, and some of them also provide other crowd-sourcing data management services. Examples include Amazon’s Mechanical Turk, Lionbridge AI, Scale API, Appen, and Cloud Factory.
*   HoloClean system is an open-source weakly supervised ML system for data repair and predictions on structured data leveraging certain high-level domain-specific information. It can utilize reference datasets, incorporate available rules and constraints, and learn from examples of similar entries to identify and fix data errors such as typos, outliers, data inconsistencies, and missing entries. Data wrangling tools such as Trifacta (GCP Dataprep) and Paxata also leverage ML models to facilitate data exploration, hidden pattern detection, and probabilistic data quality rule generation.
*   Data mastering systems such as Tamr, Zaloni’s DataOps Arena, TIBCO MDM, Infosys MDM, and Informatica offer data curation and integration powered by a combination of rule-based and supervised ML techniques. Dedupe.io is an ML-based tool that scans for similar rows to identify matches in Excel spreadsheets or databases. Amperity AI-Powered Identity Resolution helps to build Customer 360 profiles.
*   For resource utilization and workload/performance optimization, Informatica CLAIRE has a smart optimizer to decide on the best engine for Big Data workload and can intelligently change the join order for ETL based on cost and heuristics. NetApp Active IQ provides actionable intelligence for optimal storage health. Datadog applies ML to automatically analyze infrastructure and application performance, and detects abnormal error rates, elevated latency, and network issues for applications and services. Splunk Machine Learning Toolkit and Splunk Machine Learning Environment give users the ability to operationalize ML models with machine log/messaging data and allow partial-fit of pre-trained models for the user to leverage transfer learning to customize their own applications.
*   Machine learning catalogs automatically and continuously crawl and index corporate data assets across multiple data sources for cataloging. They may also include features such as lineage tracking, natural language querying, ML recommendations, and dynamic sensitive data masking. Vendors in the ML data catalog market include Alation, Collibra, Informatica, Oracle, IBM, Talend Data Catalog, erwin Data Catalog, and Google Cloud Data Catalog, etc. Some catalogs are powered by knowledge graphs or can search over knowledge graphs, such as Collibra, Informatica, data.world, and Cambridge Semantics Anzo Catalog. Alation and Collibra are among the pioneers of active data governance which encompasses data quality, data discovery, data security, and governance.
*   Data privacy protection and access control policies are two essential elements of Data Governance 2.0. AI/ML algorithms can help detect data vulnerabilities and recommend or apply the appropriate security policies. Automated data governance platforms such as Immuta, Privacera, and BigID provides GDPR compliance tools for sensitive data identification, data proliferation control (especially for PIIs), data access control/monitoring, and policy enforcement. Data Capsule is an intelligent paradigm for automatic and sensitive data tracing and policy enforcement. In this paradigm, the combination of data and associated policy form a capsule, and after the capsule is processed by an analysis program (e.g., ETL and machine learning), the policy is automatically updated accordingly based on the set of data operations in the analysis program. The resulting updated policy (residual policy) is then combined with the output of the analysis program to form a new capsule. In this way, data privacy policies are encapsulated with the data from the very beginning and automatically cascaded to the downstream data processing and model runs.

Many of these specialty solutions are also accessible on public Cloud such as Informatica for AWS/Azure/GCP, Alation Data Catalog and Data Governance on AWS, Collibra Data Governance and Catalog on AWS/GCP, Immuta on AWS/Azure/GCP, Zaloni’s Arena on AWS/Azure, and Tamr on AWS/Azure/GCP.

Public Cloud providers such as AWS, Azure, and GCP make available to their clients a wealth of Cloud-based data, analytics, and AI/ ML services that provide the building blocks for AI/ML assisted data management solutions. In addition to third-party managed solutions for data management through cloud marketplace, a number of native/integrated ML features and supporting technologies available on public Cloud platforms can facilitate building a smart pipeline for secure and automated data processing and analytics, even from raw data to useful insights in real time.

[Table 8.1](#chap8.xhtml#tab8-1) provides a summary of main native/integrated ML capabilities on the top three public cloud platforms. It by no means represents a complete listing of all AI/ML capabilities for data management on these Cloud platforms. Some of these AI/ML functionalities are discussed in more detail next. Some others are discussed in [Chapter 5](#chap5.xhtml).

**Table 8.1.**Main ML capabilities for data management on top public cloud platforms

![](images/p296.jpg)

**8.4.1*AI/ML Tools for Data Processing and Governance on Amazon Web Services (AWS)***

AWS boasts an impressive technology stack for data processing and data governance. Many of these are AI/ML-enabled or AI/ML enabling.

Amazon Sagemaker is AWS’ fully managed machine learning service that helps users with their end-to-end ML workflow including data labeling, data wrangling, feature management, model training, model validation, model deployment, model monitoring, continuous integration, and continuous delivery (CI/CD). It also provides AutoML feature (Autopilot) which automatically explores different solutions to find the best model. Additionally, Sagemaker offers pre-canned ML solutions for common use cases with one-click deployment.

Amazon Kendra is an ML-powered enterprise search tool for data and information in documents across a diverse set of internal/external and on-premises/on-cloud data sources. Queries can be performed with natural language search input. Kendra can take the documents inside configured data sources together with an optional set of frequently asked questions (FAQs) provided by the user, and then uses smart ML algorithms to build a search index for these documents and FAQs. NLP and NLU are used not only for semantic query, but also to help extract and index the keywords, concepts, and relationships among those documents. Users have the flexibility to create their own customized indexes as well. All of these allow Kendra to take into account the content, user context, and query input for intelligent search. Not only is it highly scalable and tightly integrated with other AWS services, search results can take into account the security model of the organization, with only the contents of appropriate security levels delivered to users.

For PII identification and de-identification, Amazon Macie is the fully managed data security and data privacy service provided by AWS. It allows users to define sets of criteria to detect sensitive data deterministically and/or through smart AI/ML algorithms. Finding output can be sent to downstream processes, such as AWS Lambda and AWS Step Functions, for automated remediation including de-identification. Macie can scan data items in AWS Simple Cloud Storage (S3) buckets. For data items in other AWS storage, users can move them temporarily to S3 for the scan. Macie is accessible through AWS Management Console, AWS command line tools (AWS CLI and the AWS Tools for PowerShell), AWS SDKs, and Amazon Macie REST API.

For contact center activities that often require real-time information and analytics, several AI/ML features are available for Amazon Connect such as Connect Wisdom (in preview), which takes real-time customer input (e.g., voice, chat), searches for content in knowledge repositories, and provides relevant recommendations/answers for quicker and more effective customer service. Connect Customer Profiles can quickly bring up unified customer profile information from multiple sources, so that the agent has all the information about the customer to provide better personalized service in real-time. Connect Contact Lens provides real-time contact center analytics powered by ML, analyses contact transcripts to standardize and ensure quality of service, prevent conflicts, facilitate customer service training, and automatically generates alerts to escalate customer issues. Connect Tasks is a tool to help assign, prioritize, and track customer service tasks and manage follow-up actions based on availability and expertise. Connect Voice ID (in preview) uses voice print for real-time customer authentication, adding another layer of security protection.

Other applicable AWS AI/ML and AI/ML empowered services include for example:

*   Amazon Textract for data extraction from scanned documents,
*   Amazon Comprehend for finding insights and relationships in text,
*   AWS Lake Formation FindMatches for record matching,
*   Amazon CodeGuru for recommendations to improve client code quality and optimize code performance,
*   Amazon DevOps Guru to improve application operational performance and availability,
*   AWS Glue deploys ML algorithms to automatically impute missing data,
*   Amazon Quicksight Q for serverless automatic data indexing, relationship finding, and NLP to answer business questions instantly (for example, CapitalOne uses it for BI dashboards),
*   Amazon Monitron for detecting abnormal behavior in industrial machinery, sensors, and IoT devices.

Many of AWS’ AI/ML-based services take in user feedback to allow for the continuous improvement of the underlying ML models, and the underlying AWS tech stack can be helpful managing resources for other types of data management workflows.

**8.4.2*AI/ML Tools for Data Processing and Governance on Azure***

Microsoft recently launched Azure Purview (in preview), its unified data governance service for managing enterprise data across on-premises and on-Cloud systems. It is an extended and enhanced version of Azure Data Catalog. It can provide a holistic, up-to-date view of client data assets with intelligent features including automated data discovery, sensitive data classification, and end-to-end data lineage. It leverages the AI/ML technologies behind Microsoft Information Protection that help users to identify sensitive information, classify them, and implement appropriate protection policies. It can also incorporate business glossary/taxonomy to enhance data indexing and searching. Microsoft applies Purview for its own compliance with data privacy regulations such as GDPR and California Consumer Privacy Act (CCPA), and it can be leveraged to minimize compliance risk on the client side as well.

Azure also offers several options for users to develop their ML models: Azure Machine Learning, Azure Cognitive Services, Azure SQL Managed Instance Machine Learning Services, Machine Learning in Azure Synapse Analytics, Machine Learning and AI with ONNX in Azure SQL Edge, and Azure Databricks, with their own features and purposes. In particular, Azure Cognitive Services include pre-trained ML models for OCR (Form Recognizer), speech data (Speech Service), text data (Translator, Text Analytics, Language Understanding, QnA Maker), and anomaly detection (Anomaly Detector), etc.

**8.4.3*AI/ML Tools for Data Processing and Governance on Google Cloud Platform (GCP)***

Cloud DLP is GCP’s fully managed service for sensitive data discovery, classification, and protection. In addition to deterministic rules, Cloud DLP also employs AI/ML algorithms to identify sensitive information from data assets in Cloud Storage/Datastore/BigQuery, anonymize and transform text and images, and provide risk analysis to measure sensitive data protection. Same for some other Cloud platforms, automatic detection can be made in almost real time, and users can build workflows to scan data for sensitivity before moving it to storage buckets to prevent PII leak.

AI/ML-enabled Google Cloud Data Catalog is a useful tool for data governance. It is powered by intelligent Cloud Search and interacts with Cloud DLP to automatically identify sensitive data by leveraging DLP’s powerful auto-tagging mechanism. It can automatically catalog data assets in BigQuery, Cloud Storage, Cloud Bigtable, and Google Sheets as well as topics in Pub/Sub. Custom tags can also be created and used for data search.

Cloud Dataprep (Trifacta) is a serverless, scalable, and intelligent data wrangling service. It enables users to visually explore, clean, and prepare structured and unstructured data for downstream analytics, business intelligence, and ML. In addition to deterministic data quality rules, it also uses ML to derive probabilistic data quality rules to assess if the data is fit for purpose. Cloud Dataprep can also infer user’s data transformation intent based on the data selected, and automatically generates a ranked set of suggestions and patterns to match the selection.

The fully-managed Google Cloud AI Platform provides a powerful toolbox for users to develop their own ML models for purposes including data management. Like Amazon Sagemaker, it also provides coverage for the end-to-end ML workflow. It leverages other Google Cloud services such as Data Labeling Service for labeling training data, BigQuery for data preparation, Dataprep for data wrangling, managed Jupyter Notebook and AI Platform Training for ML model training, AI Explanations and What-If Tool for model validation, AI Platform Prediction for model serving, AutoML for no-code automatic model selection, Continuous evaluation for model performance monitoring, MLOps tools for CI/CD, and TensorFlow Enterprise for enterprise-grade support and managed services for TensorFlow instances. Google Contact Center AI and Document AI suites also provide tools for potential use in data management. Additionally, BigQuery ML allows users to create and evaluate a variety of statistical and ML models and makes model predictions with Structured Query Language (SQL).

At the Google Data Cloud Summit in May 2021, Google announced Dataplex (in preview), which is an intelligent data fabric for unified data management over metadata, intelligence, lifecycle, governance, and security. Google’s AI/ML capabilities are leveraged to automate data discovery, metadata generation/enrichment, data lifecycle management, and data quality assurance workflows. Additionally, BigQuery now incorporates data anomaly detection with its “built-in” machine learning capabilities.

**8.4.4*Integrated Data, Analytics, and ML Platforms***

In addition to major public cloud services, integrated data, analytics, and ML platforms such as Databricks, Snowflake+Datarobot, Dataiku, Alteryx, SAS, and MathWorks allow users to build their own customized intelligent data management solutions and pipelines with rich functionalities in data preparation, ML model training, and AI-assisted automation.

Many general purpose ML algorithms can serve as the building blocks for customized AI/ML data management solutions. For example, popular ML programming libraries/modules such as Scikit-Learn, Keras, Caffe, PyTorch, MXNet, and Tensorflow implement a large variety of ML algorithms, including dozens of semi-supervised, weakly-supervised, and transfer learning ones. There are also active learning libraries such as ModAL, Libact, and Alipy. You can find other ML packages in the PyPI repository for Python. A few examples of specialty ML packages and plugins are listed, as follows:

*   Snorkel leverages labeling functions — code snippets capable of incorporating domain specific rules, logics, and heuristics — to assign labels to unlabeled instances programmatically.
*   OpenAI API is the developer of GPT-2 and GPT-3 language APIs; OpenAI Gym is a toolkit for developing and comparing reinforcement learning algorithms.
*   Synthetic Data Vault includes open-source libraries for deep learning algorithms such as Variational Autoencoder (VAE) and Generative Adversarial Network (GAN) to generate and evaluate synthetic data, along with Gaussian mixture models (GMM), a powerful clustering algorithm, for synthetic data generation.
*   Dataiku offers Active Learning Plugin to improve data quality with an efficient data labeling process, and transfer learning with Dataiku’s deep learning for images plugin also helps to accelerate learning in computer vision.

**8.5Case Study: How Informatica uses AI/ML to Improve Data Management**

Informatica is an enterprise Cloud data management and data integration solution provider. It is an industry leader in applying AI/ML to enhance automation and intelligence in enterprise data management.

In April 2021, Informatica introduced its new Intelligent Data Management Cloud powered by more than 200 intelligent data services covering the key enterprise data management and data integration workflows such as ingestion, discovery, transformation, cleansing, metadata management, master data management, security/privacy, and governance. At the core of the Informatica Intelligent Data Platform (IDP) is the Cloud-scale AI-powered Real-time Engine (CLAIRE) that powers a variety of data management solutions and products for use by data engineers, data scientists, data analysts, data stewards, DataOps, DevOps, SecOps and business users. [Figure 8.2](#chap8.xhtml#fig8-2) shows the extensiveness of AI/ML solutions supported by CLAIRE, which makes it a good example of high-level AI/ML integration into the end-to-end data management process.

![](images/p303.jpg)

**Figure 8.2.**Key CLAIRE intelligent data management capabilities

These capabilities are discussed in more detail, as follows:

*   *Data cataloging*: Leveraging the rich set of metadata collected and managed by IDP, CLAIRE’s ML-based data discovery engine can scan and catalog data assets across the enterprise. For dataset relationship discovery, primary keys, unique keys, and joins across structured datasets can be automatically identified with help from ML algorithms. The ML algorithms can learn from user feedback to improve their performance. For intelligent data mapping, smart algorithms are available to assess similarity between data columns and make suggestions for data discovery, categorization, deduplication, merging, etc. The engine can also intelligently apply semantic labels to data fields for automatic data classification. Such automatically tagged data domains can be used to aggregate relevant data fields to assemble datasets for appropriate business entities, again leveraging ML for smart data aggregation and business entity identification by learning from user examples.
*   *Analytics workflows*: CLAIRE can leverage an organization’s own metadata from its data pipelines to apply AI/ML for data transformation recommendations. Based on user acceptance or rejection of recommendations, the underlying AI/ML algorithms can be progressively improved. It applies adaptive optimization methods for data pipeline execution such as designing data join operation plans and selecting the best processing engine to achieve desired performance level. For combining data sets, it can make recommendations on join keys based on field tags, and make suggestions to data scientists and data analysts on data sets they can use for their projects by learning from users’ past experiences. For data visualization, it generates recommendations and leverages Apache Zeppelin to produce graphs and charts based on user selections. CLAIRE also powers Informatica Intelligent Structure Discovery (ISD) to automatically extract structured information during file ingestion and data onboarding.
*   *Data quality and master data management*: Leveraging metadata-driven AI, CLAIRE can infer data cleaning rules based on how similar data are handled. Similarity based approaches are also used to detect and remove duplicate data. It employs a combination of deterministic, heuristic, and probabilistic algorithms, as well as contextual synthesis matching and active learning entity matching to stitch data from various sources for Business 360 views on business entities. Synthesis matching is used to leverage “contextual attributes” extracted from unstructured data sources to help match between different types of business entities (e.g., matching prospects to customers) and identify hidden relationships. The ISD also helps named entity extraction leveraging natural language understanding for data mastering. A variety of classical and modern techniques are applied for identity matching using people’s names, organization names, addresses, identity numbers, dates, and other identification data. For entity resolution, CLAIRE applies a combination of declarative rules and machine-learned random forest classifier trained through supervised active learning.
*   *Data governance and compliance*: The Informatica data governance tools, including Axon Data Governance, Informatica Data Quality, and Informatica Enterprise Data Catalog, leverage CLAIRE to intelligently automate many aspects of data governance workflows such as data quality assessment, data quality enrichment, and associating business terms with physical datasets by enriching and linking metadata with business semantics and by recommending machined learned rules for data quality issue identification and data association.
*   *Data Privacy and Protection*: In addition to ML algorithms for sensitive data tagging, CLAIRE provides users the ability to track movement and the proliferation of sensitive data, and detect policy violations with respect to sensitive data access and handling. Subject registry identity mapping allows users to assess the correlation between combinations of data and subject identity. This tool can be used to find indirect identifiers of personal identity. Potential effects of different privacy protection schemes can be assessed via simulation. Abnormal data user behaviors, such as impersonation, credential hijacking, and privilege escalation attacks, can be monitored with user behavior analytics (UBA), which are generated through unsupervised learning algorithms. Real-time API data protection feature monitors sensitive data transmission between APIs and offers user options to block sensitive data on API calls.
*   *DataOps workflows*: CLAIRE can be used for resource and capacity management such as monitoring resource utilization, predicting resource utilization trends, and applying auto-scaling to meet runtime demand. It monitors the health of data systems such as job run times, data usage, resource consumption, throughput, etc., and detects anomalies in job runs by taking into account seasonality effects.

Our discussion has focused only on the spectrum of AI/ML technologies that have already been incorporated into the Informatica IDP to help automate the data management workflows and make intelligent recommendations. Informatica is focusing on extending the AI/ML capabilities of CLAIRE to provide more intelligent and automated solutions to help organizations adapt to the fast-evolving data landscape. For more information about how ML-based innovations in CLAIRE can help drive new advances in data management, readers can refer to the Informatica white paper titled “Artificial Intelligence for the Data-Driven Intelligent Enterprise” \[[5](#chap8.xhtml#rref5)\]. We leave readers to evaluate the performance and cost/benefit profile of IDP for your specific data management needs.

**8.6Challenges and Way Forward**

Traditional data management practices are inadequate to handle the challenges brought on by the proliferation and explosion of data. AI/ML is not just something fashionable to have for data management in the Big Data era but is increasingly becoming a necessity. Organizations aspiring to become digitally successful need to seriously think about building up the capability and capacity to incorporate AI/ML as an integral part of modern data management. This journey mostly likely would not be smooth sailing, as a number of challenges lie in the way.

Perhaps the biggest potential challenge is culture related. Cultivating a data driven culture within an organization already takes a lot of effort, and on top of that, we need to have another layer of mental preparedness for applying cutting-edge technologies. There are certain human behavioral factors and short-term corporate imperatives that contribute to organizational inertia in innovation. Sometimes, we may be just too accustomed to traditional ways of doing things, or in the mindset that “if something is not broken, why fix it.” Another school of thought prefers building up the data driven culture first then worrying about more advanced technologies. The problem here is that the rest of the world is moving ahead fast and will not wait for us to catch up. If we are not proactively starting to build up the capability and seeking out the most effective and efficient solutions to the clear and present Big Data management problems we are facing today, we will never get ready for the future, let alone leading the way to shape the future.

Even for data management tasks involving Big Data, we may still face limited data availability and usability for AI/ML purposes, which restrict our ability to train highly performant ML models. For both supervised and unsupervised learning tasks, we may need to first use data integration tools to unify training data across silos. For supervised learnings, which typically require large amounts of labeled data, there are some strategies to deal with inadequate labeled data, for example, through crowdsourcing, synthetic data, semi-supervised learning, weakly supervised learning, and active learning with a feedback loop. Transfer learning is also proven very helpful to materially reduce the number of labeled training samples for text, image, audio, and video data applications. We also need to be data frugal and establish long-term data collection strategies to proactively and holistically assess what new data items the organization needs to collect, including data that can help in the future but with no immediate use for the moment, and start accumulate such data on a day-to-day basis. We need to be careful about throwing away raw data. For example, with the traditional ETL approach for data warehousing, if we only store the final transformed data, we may lose some information embedded in the raw data, which may be costly to recover or is not recoverable at all. Historically, we keep only transformed data to reduce storage costs, but as such costs become cheaper, we need to carefully weigh storage costs against the opportunity costs of losing potentially valuable information. In addition to data records, other data assets such as metadata, analytics, charts, dashboards, BI reports, models, data APIs, and metadata on models/APIs can also be included in the collection basket. All of these may be helpful for data cataloging, lineage tracing, and ML model training in addition to any regulatory retention requirements.

The lack of understanding of AI/ML technologies by data operation and business operation teams is a legitimate concern. DataOps and business experts usually do not have the technical know-how to fully grasp the inner workings of the underlying ML algorithms. This is where data scientists on the team can help to educate other colleagues on the basics, select the right algorithms, train performant models, understand limitations, assess proper use, and monitor model performance. Additionally, as discussed previously, there are already many applications that have AI/ML built-in and are made easy/ready to use for anyone, not just the data scientists. The drive to democratize AI/ML continues by technology companies, academia research institutes, and open-source communities, and we should expect more user-friendly AI/ML tools targeted for a variety of business domains. It is a misconception that AI/ML is just for the technically privileged few. It is up to us to keep abreast of latest developments and to try them out. As many of these AI/ML applications require user feedback to improve (for example, chatbots), the more we use them and the more feedback we provide, the better their performance can be. Continuous user feedback also helps to alleviate data availability problem.

The quality, accuracy, and capability of existing ML algorithms may not satisfy the requirements of all relevant data management tasks. Generally speaking, labeled data (and supervised learning) are more informative than unlabeled data (and unsupervised learning). However, for many (if not most) data management tasks, labeled data are hard to come by. Even with labeled data available, for different data labeling mechanisms and different levels of label accuracy, different machine learning approaches are required. Some general frameworks are available to handle inadequate labeled data, such as semi-supervised learning and weakly supervised learning, but they may need to adapt to specific use cases. The quality of ML algorithms for data management is subject to ongoing research and improvement. In particular, challenges remain in leveraging AI/ML to embed domain knowledge in the data wrangling process, and it may not be easy to teach machine what data to keep, change, or reformat as competently as human experts can. Knowledge graphs, to some extent, can help to provide better context, reveal more connections, and broaden the machine’s ability to find additional patterns and rules to process data more autonomously. However, the data munging process to establish data transformation rules remains primarily a human intensive effort.

The lack of adequate resources may impede operations teams’ ability to embark on AI/ML-assisted data management initiatives. If this is due to budget constraints, then budget allocation decisions can be informed by a cost/benefit analysis, taking into account future enterprise needs, not just the lowest cost solutions for current needs. Within a limited budget, we can start with efficiency quick-wins through some easy-to-implement AI/ML-assisted process optimization and/or automation to achieve initial resource savings. This will allow operational teams to have more time to focus on further innovation and so forth. In this way, the efficiency gained can feed on itself through a virtuous circle.

Data management cannot be done in isolation. It needs to be tightly integrated with business operations and risk management. AI/ ML-assisted data management systems also need support from other advanced technologies to better materialize their potentials. Enterprise systems, including data management systems, need to talk to each other through technologies such as APIs, microservices, and messaging systems (e.g., Google Cloud Pub/Sub and Apache Kafka). Connections between data assets within data systems and connections among enterprise systems can be captured by enterprise knowledge graphs, which can themselves be developed and supported in combination with other AI/ML tools.

**8.7Conclusion**

Big Data is the life blood for AI/ML, and an effective and efficient data management system is crucial for AI/ML application development. AI/ML in turn can offer tremendous help for data management at scale. They go hand-in-hand. Large data volume and high data velocity require scale, while variety and veracity of data require something more than rule-based systems. AI/ML fits the bill well. There are already many successful AI/ML applications for data management in the real world, bringing tangible and material efficiency/effectiveness gains. Looking into the future, there is no reason to doubt even wider adoptions. The future is bright for applying AI/ ML for data management.

**References**

[1](#chap8.xhtml#ref1).T. Kraska, A. Beutel, E. H. Chi, J. Dean and N. Polyzotis, *The Case for Learned Index Structures,* 2018. \[Online\]. Available: [https://arxiv.org/abs/1712.01208](https://arxiv.org/abs/1712.01208)

[2](#chap8.xhtml#ref2).J. Leskovec, A. Rajaraman and J. D. Ullman, *Mining of Massive Datasets,* 3rd Ed. UK: Cambridge University Press, 2020.

[3](#chap8.xhtml#ref3).H. Song, M. Kim, D. Park, Y. Shin and J. Lee, *Learning from Noisy Labels with Deep Neural Networks: A Survey,* 2021. \[Online\]. Available: [https://arxiv.org/abs/2007.08199](https://arxiv.org/abs/2007.08199)

[4](#chap8.xhtml#ref4).B. Davay and Y. Bogdanov, “Disrupting risk management through emerging technologies”, Spark+AI Summit 2020, [https://databricks.com/session\_na20/disrupting-risk-management-through-emerging-technologies](https://databricks.com/session_na20/disrupting-risk-management-through-emerging-technologies). Accessed: June 24, 2020.

[5](#chap8.xhtml#ref5).Informatica. *Artificial Intelligence for the Data-Driven Intelligent Enterprise,* 2020. Accessed: December 31, 2020. \[Online\]. Available: [https://www.informatica.com/content/dam/informatica-com/en/collateral/white-paper/artificial-intelligence-for-data-driven-disruption\_white-paper\_3328en.pdf](https://www.informatica.com/content/dam/informatica-com/en/collateral/white-paper/artificial-intelligence-for-data-driven-disruption_white-paper_3328en.pdf)

[6](#chap8.xhtml#ref6).T. Hospedales, A. Antoniou, P. Micaelli and A. Storkey, *Meta-Learning in Neural Networks: A Survey,* 2020. Accessed: November 7, 2020. \[Online\]. Available: [https://arxiv.org/abs/2004.05439](https://arxiv.org/abs/2004.05439)

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0009](https://doi.org/10.1142/9789811250903_0009)

Chapter 9

**Technologies and Strategies to Leverage Cloud Infrastructure for Data Integration**

***Zhiyu Ge***

**9.1Introduction**

Companies around the world are increasingly relying on data to provide business insights and advanced analytics for data driven decisions. This objective requires a well-designed enterprise data storage and processing framework that integrates data in a variety of formats from multiple data sources across all parts of the organization. The Cloud infrastructure can provide not only the storage space and the computing power but also a solid foundation for managing, integrating, and sharing data across different business units and support functions. The scale of economy also makes the Cloud implementation a cost-effective solution. Firms are increasingly aware that Cloud-based data solutions should be an essential part of their enterprise data strategy. This chapter discusses latest technologies and strategies firms can use to leverage cloud infrastructure for data integration.

**9.2Cloud Data Integration Services**

We begin with a high-level overview of the main Cloud data integration services. Data integration services from three of the major Cloud providers Amazon Web Services (AWS) \[[1](#chap9.xhtml#rref1)\], Azure \[[2](#chap9.xhtml#rref2)\], and Google Cloud Platform (GCP) \[[3](#chap9.xhtml#rref3)\], taken as examples, are discussed in parallel. Other major Cloud providers also have similar services available on their respective platforms. [Table 9.1](#chap9.xhtml#tab9-1) below provides a high-level overview of some common cloud integration services that are available on these public cloud platforms.

Cloud platforms provide a lot of flexibility in data movement. Major Cloud providers develop and maintain a large number of connectors for ingesting data from a large variety of external sources including client on-premises systems, IoT devices, and other Cloud platforms. In particular, both AWS and GCP have several solution components to ingest data with different combinations of size, source, and latency. For example, on-premises databases can be bulk loaded with AWS Database Migration Service, Azure Database Migration Service and Google Cloud Storage Transfer Service. Streaming data from IoT devices can be transferred with AWS Kinesis, Azure Event Hubs, and GCP Pub/Sub. Such flexibility in data movement allows firms to aggregate data from different sources into the cloud environment for further integration.

**Table 9.1.**Summary of common cloud data integration services

![](images/p312.jpg)

For data repository, the Cloud boasts enormous storage space with practically unlimited capacity for individual clients. Firms can use Cloud data lake to hold structured, semi-structured, and unstructured data from various data sources with high durability, flexibility, availability, scalability, and security. It is a low-cost alternative relative to on-premises data centers. Data lakes can be hosted on Amazon Simple Storage Service (S3), Azure Data Lake Storage, and Google Cloud Storage. Data warehouses can be managed by Redshift on AWS, Synapse Analytics (previously SQL Data Warehouse) on Azure, and BigQuery on GCP. Delta Lake, which adds a structured ACID (atomicity, consistency, isolation, and durability) transactional layer on top of existing data lakes, is the latest state-of-the-art data repository that can significantly increase speed, capacity, quality, and functionality of data management and data utilization over data lakes. Managed Delta Lake services on the cloud are provided by Databricks.

Data processing on the Cloud leverages the enormous compute power that comes with the Cloud infrastructure. Advanced distributed processing can be carried out using Spark and Hadoop clusters with auto scaling. Parquet columnar format and intelligent data partition can also be applied to further maximize data processing efficiency, reducing latency, and increasing throughput. On the AWS, the EMR (Elastic Map-Reduce) is a fully managed data lake service with distributed data processing. Google Cloud Dataproc offers similar services, functionalities, and performance. Azure Data Lake is a Microsoft fully managed data lake service with 4 key building blocks: (i) core data lake Infrastructure, (ii) Azure Data Lake Storage (ADLS), (iii) Azure Data Lake Analytics (ADLA), and (iv) Azure HDInsight. AWS Glue is a fully managed ETL (extract, transform, load) service. Its Azure counterpart is Azure Data Factory, and its GCP counterpart is Cloud Data Fusion. There are also third-party managed enterprise distributed data processing solutions available on the Cloud such as Databricks, Snowflake, Confluent, and Cloudera.

Cloud platforms also have data lifecycle management tools available for creating, executing, and managing data pipelines, creating and maintaining data catalogs, and keeping track of data lineage. AWS Data Pipeline, Azure Data Factory, and GCP Dataflow can be used to schedule regular data movement and data processing activities in the Cloud. All of them can integrate with on-premises and Cloud-based storage systems. AWS Glue can generate data catalog for ETL, Azure Purview Data Catalog, and GCP Data Catalog can do the same. AWS Glue DataBrew can track and visualize data lineage, and Apache Atlas installed on top of Amazon EMR provides capability for lineage, discovery, and classification. On Azure, Data Factory, Data Share, Power BI, and data storage systems can capture the lineage of data as it moves, and Azure Purview can stitch lineage information together and show end-to-end dataset dependencies. GCP Cloud Data Fusion provides lineage at the dataset level and field level, and can track lineage over time. Informatica Enterprise Data Catalog, a third-party managed service available on AWS, Azure, and GCP, can track data lineage with AI-powered data catalog. Zaloni Arena, an end-to-end DataOps platform which includes a data catalog service, is also available on AWS Marketplace.

In addition to native cloud solutions, there are also third-party managed unified data analytics solutions available on major Cloud platforms that not only handle the end-to-end data pipelines and data lifecycle management, but also integrate with downstream analytics, data science, Machine Learning modeling, visualization, and BI reporting systems. One such example is Databricks, which leverages Cloud infrastructure to provide enterprise solutions for efficient, timely, reliable, and secure Big Data management, together with tools and services for downstream analytics, BI, and Machine Learning workflows. Databricks is available on AWS, Azure, and GCP.

Our discussion only scratches the surface of rich data services available on each of these public Cloud platforms, and these platform providers keep churning out new data services and enhancing existing ones. With so many powerful Cloud data functionalities, it makes a strong case for firms to use Cloud as the platform for enterprise data integration to the extent possible in their digital transformation journey.

**9.3Data Security, Privacy, and Access Control in the Cloud**

This topic deserves a dedicated discussion, although data security, privacy, and access control are also among the foundational services built into Cloud platforms. In this section, we discuss the features and tools available on the Cloud to address data security, privacy, and access control concerns. The implications to strategies for data migration and sensitive information protection in the Cloud will be discussed in the last section of this chapter.

On top of the strong physical security of Cloud data centers, main Cloud data security features include identity management, firewalls, intrusion detection/prevention, encryption, access control policies, and data recovery. There are dedicated and well-qualified security experts at major Cloud providers who constantly monitoring security threats and improving data protection to ensure Cloud security is up-to-date. It is important to understand that Cloud data security is a shared responsibility between Cloud providers and clients. Cloud providers are responsible for their global infrastructure including hardware, software, networking, and facilities, as well as built-in security features of their managed services. Clients are responsible for user configurations of the Cloud IaaS, PaaS, and managed service products they use. For different products, the set of user configurations may be different, but in general, access controls for client applications and client data are the responsibilities of clients. The tools to help clients control such accesses, such as identity management, firewall configuration, and access policy management, are available through security services offered by cloud providers and cloud marketplaces. When used properly, they provide protection at least as safe and effective as on-premises security systems.

Despite the robust Cloud security features and tools, data breach may still occur if these tools are miss-used (e.g., misconfigured firewalls on the client side), and if client internal data protection policies and procedures are not robustly designed or well enforced, as exemplified by the 2019 Capital One data breach incidence. In order to reap the full benefits of the Cloud security infrastructure and to bridge any skill and knowledge gaps, firms must train in-house Cloud administrators and internal users on proper use of Cloud security mechanisms, ensure everyone understands the functionalities and potential vulnerabilities, and develop and strictly enforce sound Cloud security policies. (Remember that users are the most critical and weakest link in the information security chain.) Firms should not shy away from Cloud just because of security breach incidences like Capital One’s. The same type of breach could happen at on-premises data centers as well if firewalls are not configured properly or policies are not followed. Comparing to on-premises security systems, for enterprise data protection at a large scale, Cloud security infrastructure allows more convenient deployment of and access to advanced tools and functionalities for real-time or near real-time security breach detection and prevention (such as intrusion detection/prevention systems with event logging). Cloud security logs also give clients the ability to keep track of application and data access events for further analysis/investigation if needed. So, the bottom line is — trust the cloud security infrastructure, understand it, and use it properly.

In addition to data security, protecting client data privacy is also a high priority for Cloud providers. Cloud providers do not access or use client content without client consent, and they offer APIs for clients to configure access control permissions for data residing on Cloud and client services developed and/or deployed in the Cloud environment. Clients have the option to choose what data to share and how to share it, either internally or externally. For compliance with regulatory data residency and privacy requirements, the global Cloud infrastructure allows clients to retain complete control over the regions in which their data is physically located. Many Cloud data services also have the ability to mask, encrypt, delete, and/or track usage of personal data. Clients can implement additional privacy enhancement techniques (such as anonymization and differential privacy) to their own data, or leverage third-party vendor data privacy solutions available through the Cloud marketplace. For Personally Identifiable Information (PII) management, Amazon Macie and Google Cloud Data Loss Prevention (DLP) are examples of fully managed services offered directly by Cloud providers for sensitive data discovery, classification, and protection. On Azure, PII can be detected with Azure Cognitive Search and Microsoft Presidio. More discussion on sensitive data identification and tracking can be found in the next section.

Data access control plays a very important role in both data security and data privacy protection. There are two data access control paradigms, (i) Role-Based Access Control (RBAC) and (ii) Attribute-Based Access Control (ABAC). The RBAC is the incumbent and by far the most common approach adopted in almost all IT systems (including on-premises/on-cloud data systems). A typical traditional RBAC-based data access control assigns manually created static policies (data set, column, row, or cell level, etc.) to specified roles. The ABAC is relatively a newcomer, but one with huge potential. With the ABAC, access to data is determined by attributes such as characteristics about the user, the data, and the environment. These characteristics can include, for example, group, department, role, position, location, project, database/dataset metadata, device type, IP address, etc. In a way, the ABAC is more encompassing than the RBAC and can include the RBAC as a subset. The ABAC is more versatile since it can take all these attributes as variables in eXtensible Access Control Markup Language (XACML), a popular programming language to implement ABAC logics. It not only allows fine-grained access control for any combinations of these variables, but can also generate and enforce finegrained access control policies programmatically and dynamically on the fly, offering a huge potential for automation. In particular, when implementing ABAC rules based on dataset attributes such as column attributes and row attributes, users can achieve dynamic column-based, row-based, and cell-based data access control. Since the ABAC executes more complex and dynamic searches than the RBAC, it does require more compute resources. However, when implementing the ABAC in a Cloud environment, this disadvantage can well be addressed by scalable and elastic distributed computing power cloud offers.

The ABAC and RBAC can be combined in different ways to maximize the effectiveness and performance of access control framework for different applications. For example, one way is to have role-based control as the first layer and then fine grain data element access controls with ABAC policies within individual roles. Alternatively, we can apply ABAC policies first over user attributes, environment attributes, and data attributes to assign access requests to specified set of roles.

There are open-source tools, such as Casbin and Accesscontrol, available to automate the ABAC or RBAC data access policy enforcement for compliance with legal, regulatory, and internal data privacy control requirements. Managed Cloud data privacy and security solutions are offered by Cloud providers and vendors such as Immuta, NextLabs, Qualys, and PHEMI Systems, with some of them also providing automated data access policy enforcement. Databricks Unity Catalog allows users to leverage ANSI SQL DCL to implement fine-grained ABAC on data, models, and other data assets. In situations where raw data includes sensitive information with restricted access, these automatic policy enforcement tools not only can block non-permissible accesses but also help to anonymize, transform, or redact data to allow maximum use of information within the relevant legal, regulatory, and ethical boundaries. Also, the implementation of such tools in the Cloud environment gives users the ability to leverage Big Data processing capabilities and technologies integrated in the Cloud infrastructure, such as cloud storage, cloud computing, secure computing, and Apache Spark-based data platforms, to process sensitive data anonymously at scale.

**9.4Sensitive Data Identification, Tracing, and Processing**

With the Cloud data lake, more data in a variety of formats and from a variety of sources can be pooled into a central data repository. With Cloud facilitating data processing and sharing, it is easier for data to proliferate. However, it is not practical to examine individual raw data items to assess sensitivity, or to manually label data derived from sensitive sources. What can we do to identify and trace sensitive data intelligently and automatically at scale? Fortunately, for some common data types such as text and images, there are already promising solutions based on methods such as Artificial Intelligence (AI) or Machine Learning (ML) algorithms and knowledge graphs (KG).

For PII identification and de-identification, Amazon Macie is the fully managed data security and data privacy service provided by AWS. It allows users to define sets of criteria to detect sensitive data deter-ministically and/or through smart AI/ML algorithms. Finding output can be sent to downstream processes, such as AWS Lambda and AWS Step Functions, for automated remediation including de-identification. Macie can scan data items in S3 buckets. For data items in other AWS storage, users can move them temporarily to S3 for the scan. Macie is accessible through AWS Management Console, AWS command line tools (AWS CLI and the AWS Tools for PowerShell), AWS SDKs, and Amazon Macie REST API. On Azure, both Azure Cognitive Search and Microsoft Presidio leverage ML algorithms to automatically detect PII, and then other Azure data processing services can be used to mask, redact, or remove PII data. Azure Information Protection (AIP) builds on top of Microsoft Information Protection (MIP) solution and scans on-Cloud and on-premises file repositories to label, classify, and protect sensitive content. Cloud DLP (Data Loss Prevention) is GCP’s fully managed service for sensitive data discovery, classification, and protection. It applies deterministic and AI/ML algorithms to identify sensitive information, anonymize, and transform text and images, and provide risk analysis to measure sensitive data protection. Sensitive data in data objects stored in Cloud Storage, Datastore, and BigQuery are detectable and classifiable. Users can invoke Cloud DLP via the GCP Console, the RESTful Cloud DLP API, or Cloud DLP client library in popular programming languages. With these Cloud platforms, automatic detection can be made almost real time, and they also allow users to build workflows to scan data for sensitivity before moving it to data buckets to prevent PII leak.

In addition to the sensitive data identification/de-identification tools, semantic data catalogs, which are powered by knowledge graph, can be used to store and query sensitive data dependencies. Knowledge graphs are well suited for this type of problems and makes sensitive data tracing through enterprise systems much more efficient, since it avoids complex queries with a complex set of table JOINs associated with relational databases. The semantic data catalog approach also opens the door for the potential to use semantic query and schema mapping with catalog program synthesis to help identify sensitive fields and their dependencies. Examples of Cloud solutions in this area include Data.world Cloud native enterprise data catalog, Cambridge Semantics Anzo Catalog, and Informatica Enterprise Data Catalog.

There are also sensitive data tracing and policy enforcement frameworks that allow users to label the sensitive fields in the initial Cloud data load, either programmatically or using AI/ML algorithms to help discover them, and then programmatically track the downstream processing of these sensitive fields so that all downstream dependencies will also be properly labeled and checked against data access policies before the data is released to end users, all done automatically. Such tracing tools make use of data set attributes (or metadata) which can include information about which columns are sensitive fields, encrypted fields, and/or plaintext fields, as well as column dependencies for derived fields. Column dependencies can be captured automatically while various data operations are performed. Behind the scene, this approach also builds process graphs that include datasets/columns and analysis programs as nodes. The tracing can be done through graph traversal algorithms. In this way, there is no need to scan through the derived data to re-identify sensitive fields. Instead, such information can be recorded in the metadata associated with derived datasets. All of these metadata can then be incorporated into an ABAC data access policy, so that compliance and access control can be enforced on the fly for both raw and downstream derived data sets.

One such framework for automatic sensitive data tracing and policy enforcement is the Data Capsule paradigm \[[4](#chap9.xhtml#rref4)\]. In this paradigm, the combination of data and associated policy form a capsule, and after the capsule is processed by an analysis program (e.g., data aggregation, cleaning, extraction, transformation, and Machine Learning model), the policy is automatically updated accordingly based on the set of data operations in the analysis program. The resulting updated policy (residual policy) is then combined with the output of the analysis program to form a new capsule. In this way, data privacy policies are encapsulated with the data from the very beginning and are automatically cascaded to the downstream data processing and model runs. PrivGuard, the data capsule manager, maintains the data capsule graph (data and analysis workflow), propagates privacy policies and metadata, and calculates residual policies on analysis programs. Even if the data are copied or transformed multiple times, PrivGuard can track all dependencies and automatically perform the policy actions (e.g., consent-based access, automatic notification, retrieval, modification, or deletion of subject data, automatic anonymization, declassification or release of data, etc.) on all copies. Although PrivGuard can be deployed alongside the existing data infrastructure (on Cloud or on-premises), on-Cloud deployment can enjoy the benefit of Cloud-distributed computing and metadata management services to process large data and metadata volumes at the enterprise scale.

For sensitive data processing, in addition to the common privacy enhancement techniques such as anonymization, encryption, and differential privacy, two alternative privacy-preserving computing approaches are worth mentioning for the most critical sensitive data, especially when such data are both secretive and at the same time requiring high computational accuracy. In such situations, anonymization and differential privacy may not be fully protective, and they will also lead to loss of computational accuracy, while standard encryption may leave the encrypted data useless for computing.

One such alternative is cryptographic computing, in which plaintext data is mapped (encrypted) into an encrypted space via homomorphic encryption. Computations (not the same numerical operations in the plaintext world) can be performed on the ciphertext data in the encrypted space, and then the result is mapped back (decrypted) to the plaintext space. In this way, even staff members performing the cryptographic computing do not need to see the plaintext input or the final plaintext output, ensuring both complete secret protection and high computational accuracy. Google Private Join and Compute \[[5](#chap9.xhtml#rref5)\] (open-source release June 2019) is a secure 2-party computation tool employing homomorphic encryption to help teams within and across organizations work together with confidential data sets. HEAWS \[[6](#chap9.xhtml#rref6)\] is an accelerator for homomorphic encryption on AWS FPGA (reprogrammable hardware devices that can implement any logic function) that can help configure the user’s own hardware for optimal execution of cryptographic computing. CrypTFlow \[[7](#chap9.xhtml#rref7)\] is Microsoft’s open-source system that converts Tensorflow and ONNX models into Secure Multi-party Computation (MPC) protocols for Machine Learning inference. Of course, cryptographic computing does not come for free. It can be highly compute intensive and even prohibitive (for large-scale deep neural network training, for example) with on-premises compute infrastructure, and this is where Cloud computing can come to the rescue, and indeed, distributed Cloud computing is better suited for cryptographic computing. Nonetheless, Cloud computing at its current state is not a panacea for cryptographic computing, as the Cloud cryptographic computing cost (with respect to compute time) may still be too overwhelming for Big Data problems.

A more cost effective and efficient privacy-preserving computing approach is trusted execution environments (TEE) or secure enclaves. In an enclave approach, encrypted data are sent into the TEE from different sources (Cloud or on-premises partitions). Only the enclave can decrypt the data within a secure processor and perform plaintext calculations for data processing, analytics, and model training. As soon as any data leaves the secure processor, it will be encrypted before being released to memory. In addition to the use of single large TEE, there can be distributed TEEs to cope with distributed data storage and processing (a good solution for data residence compliance). While there are still vulnerabilities being discovered and remediated with TEEs, there have already been some industry applications with Cloud-based TEE solutions, such as Google Confidential VM \[[8](#chap9.xhtml#rref8)\], Amazon Nitro Enclaves \[[9](#chap9.xhtml#rref9)\], and Azure Confidential Computing \[[10](#chap9.xhtml#rref10)\].

Other open-source secure computing solutions implementable on Cloud include Oblivious Coopetitive Queries (OCQ) \[[11](#chap9.xhtml#rref11)\], Coopetitive XGBoost, HELEN \[[12](#chap9.xhtml#rref12)\] and Cerebro \[[13](#chap9.xhtml#rref13)\], all from the UC Berkeley RISE Lab. OCQ is a general framework for coopetitive (collaborative + competitive) analytics based on hardware enclaves. It can allow organizations to leverage each other’s confidential data for privacy-protected large-scale secure analytics without sharing the actual databases of any parties or intermediate results in the query execution. Coopetitive XGBoost is a secure enclave implementation of XGBoost (a popular Machine Learning algorithm) that allows parties to jointly develop Machine Learning models without sharing plaintext data. HELEN facilitates maliciously secure coopetitive learning with linear models, and Cerebro allows customizable compute policies and security policies to handle a variety of machine learning algorithms. Both HELEN and Cerebro are based on cryptographic computing.

Although many sensitive data identification, tracing, and processing tasks can also be performed within on-premises systems, Cloud implementation can make the underlying tools more accessible and execution of these solutions much more efficient and effective at large scale. Utilizing Cloud computing for sensitive data handling can help us to strike a better balance between privacy, efficiency, and data usability.

**9.5Strategy Considerations for Cloud Data Migration, Data Integration, and Managing Sensitive Data in the Cloud**

Now that we have a high-level view of the features of Cloud data integration services and related technologies, we can discuss some implications to building and executing a sound and efficient strategy for Cloud data migration, data integration, and sensitive data management. Although the discussion here focuses only on the handling of data in the Cloud, firms should take into account other considerations and requirements related to infrastructure migration, application migration, business process migration, and compliance when developing an overall Cloud migration strategy.

While Cloud platforms provide convenient services to ingest data from various sources both on-premises and from other Cloud platforms, data onboarding to the Cloud is more than just data ingestion and needs to be carefully planned and carried out. Before any data migration, firms need to establish proper Cloud data governance frameworks, which should cover policies and procedures, roles and responsibilities, data cataloging, data usage, data security, data privacy, and data integrity.

**9.5.1*Data Migration to the Cloud***

[Figure 9.1](#chap9.xhtml#fig9-1) depicts a typical Cloud data migration process, which includes migration planning, data preparation, approval process, and migration execution.

In the data migration planning stage, business, project, and technology requirements are assessed. Business requirements may include the identification of stakeholders and the consideration for business needs, expectations, and risks. Project requirements may include architecture design, identification of data assets and their dependencies, timelines, and resource needs. Technology requirements concern the technology stack, such as applications or services for data wrangling and integration, and their availability. At this stage, it is also highly recommended to ensure all data governance pre-requisites are satisfied.

![](images/p324.jpg)

**Figure 9.1.**A sketch of the Cloud data migration process

In the data preparation phase, the owners of the individual data assets are identified. Data assets are profiled, cleansed, and transformed if necessary to ensure quality and usability. Metadata are generated or enriched for data cataloging.

The approval process may involve approval request, data owner certification (with respect to data integrity and consent for data uploading), cyber security review, data privacy review, regulatory compliance review, and endorsements from relevant oversight committees, business heads, and regional/country regulators, if applicable.

The migration execution stage may start with the migration pipeline design and implementation. Then a pilot run at a smaller scale may be initiated to test the functionality and robustness of the pipeline and to fix any issues. After the successful test run, the actual migration workflow can be kicked off according to a carefully planned execution schedule. The progress should be monitored and any additional issues need to be addressed timely. After the migration workflow is completed, the final outcome needs to be verified and accepted by business users.

For financial institutions, a number of data privacy laws and regulations apply, including the California Consumer Privacy Act (CCPA), the Fair Credit Reporting Act (FCRA), the Gramm Leach Bliley Act (GLBA), etc., in the US, and international ones such as the European Union General Data Protection Regulation (GDPR) and the Chinese Personal Information Protection Law (PIPL). In particular, firms are required to comply with rules governing data transfer across international borders when loading data to global Cloud platforms.

Some specific Cloud data onboarding considerations are further elaborated next.

*What data to load to the Cloud?*

This depends on a number of factors including business needs, data and analytical needs, security/privacy policies, budgetary constraints, and other resource constraints, etc. It is desirable that firms load, to the extent possible, all permissible raw data and relevant processed data as needed. Keeping raw data in the Cloud, rather than only processed data after the transformation step in an ETL workflow, ensures no loss of information and facilitates data retention, recovery, and time travel. Even with no immediate use of all raw data loaded, data will come in handy when needed to support new business initiatives or to apply new modeling methodologies to extract better insights. In essence, by also keeping raw data as opposed to only processed data, we are trading storage for better data availability and utility. It is more future-proof and provides better productivity in the long run. For legacy data, firms may opt to load them in processed form as well, since there is no need to reprocess them in the Cloud. For new data, it can be more efficient to establish Cloud data workflows to process them at the enterprise scale going forward. The good news is that Cloud storage is cheap in terms of cost per unit of data comparing to on-premises storage. Furthermore, depending on the frequency of access and storage duration, users can choose different Cloud storage classes to optimize storage costs. For example, Google Cloud Storage offers Standard Storage, Nearline Storage, Coldline Storage, and Archive Storage; AWS S3 offers Standard, Standard-IA (for infrequent data access), Glacier, Glacier Deep Archive, etc.; and Azure offers three Blob Storage tiers — Hot Access, Cool Access, and Archive Access.

*Do we have to anonymize sensitive data before loading to the Cloud?*  
Masking sensitive data prior to Cloud loading may offer a sense of security and control, but it is not really necessary. Major Cloud platforms provide adequate security and privacy-preserving features and tools to help clients manage and make use of sensitive data in the Cloud. For example, data can be encrypted in transit, at rest and in use. Cloud platforms can perform sensitive data anonymization easily at scale and control data access through access policies and automatic enforcement. There are also secure computing protocols available in the Cloud protecting both data security and data privacy. Masking prior to loading may slow down Cloud data migration, and in some cases, the masking task itself may be inefficient and difficult to perform with on-premises systems, especially for projects involving Big Data. In addition to the common privacy-preserving functionalities, the Cloud also enables more advanced and automated AI/ML tools that can help clients to discover and anonymize both direct and indirect identifiers. So, the Cloud can provide an environment at least as secure and effective as on-premises data centers for storing and managing enterprise sensitive data.

Having said all these, if a firm wants to be absolutely safe and decides not to keep any personal identifiable information (PII) data in cloud, a Cloud staging storage/landing zone can be created first to temporarily host the raw data, and then the user can utilize Cloud PII identification/de-identification tools such as Dataguise’s DgSecure to mask or filter out PIIs before writing the de-identified data to the production Cloud data lake. Of course, by doing so, users need to retain the PII information and management separately on their own on-premises systems.

*How to load data to the Cloud?*

Generally, there are two different approaches — the piecemeal approach (“Trickle”) and the bulk loading (“Big Bang”) approach. In a piecemeal approach, data migration is limited to specific use cases and granted on a case-by-case basis. Users are generally not allowed to upload their data to the Cloud if they do not have a legitimate use case requiring utilization of a Cloud environment. The data loaded is typically restricted to the data owners and developers involved in the use case. If sensitive data is present, there is also typically a requirement to mask PIIs prior to Cloud uploading. As such, it may take a few days to a few weeks or even longer for users to go through the required approval process before any data can be loaded. In a bulk loading approach, data loading is not dependent on specific use cases, but rather based on an assessment of the data utility for the entire organization as a whole, regardless of immediate data use or not. Data files and databases can be prioritized and loaded into Cloud in large batches according to a well-planned migration schedule. With this approach, we load data first, and then apply security and privacy controls to data in the Cloud. A large part of these controls is automatable at scale with the Cloud security and privacy features and tools discussed previously. Centralized data in the Cloud can also facilitate better data sharing. Once the data is loaded and cataloged in the cloud, it will make it easier for users to discover the right data that can be useful for their BI, analytical, and modeling needs. Bulk loading approach can be a great enabler for faster data democratization across the organization.

The piecemeal approach is more agile and can be taken to coordinate between data migration and application/business process migration for specific business applications. In particular, if there are close dependencies between data and application, or if highly confidential data is involved, the piecemeal approach can tailor to the specific needs to ensure safety, consistency, and continuity. Also, the data is well controlled and the highest level of data access protection can be achieved, though at the cost of potential over-protection and inefficiency. With the piecemeal approach, you do not load data more than what you immediately need, but the explicit dollar savings in Cloud storage may not be material overall even without considering the opportunity costs. While the piecemeal approach is good in the beginning for firms to gain experience and expertise with Cloud data services and help identify potential operational or security issues associated with Cloud data migration, it is not efficient as a long-term solution and can be difficult to scale due to separate approvals for individual use cases, separate setup overheads for individual loading efforts, reduced ability to leverage the Big Data processing tools that operates more efficiently on a large scale, and limited opportunities for data sharing. If speed and efficiency are among the high priority considerations for enterprise Cloud migration projects, then bulk loading will be a better choice. Of course, in practice, firms may employ a hybrid approach in which most of Cloud data onboarding is done with bulk loading and some selected data, including the most sensitive data, is loaded with the piecemeal approach. The exact balance depends on the stage of the cloud migration journey and business needs.

**9.5.2*Data Integration in the Cloud***

[Figure 9.2](#chap9.xhtml#fig9-2) illustrates at a high level a common Cloud data integration pipeline from ingestion to utilization. Data can be ingested from various on-premises data systems, other Cloud platforms and IoT devices via connectors offered by Cloud data ingestion services and then stored in Cloud storage. Cloud data integration services can then be utilized to cleanse, transform, and join up data in different formats and storage units. The output from this process is then loaded into Cloud data warehouses and ready for consumption by downstream data applications including analytics, BI reporting, and data science.

A couple of specific considerations related to this process are discussed next.

*ETL or ELT?*

A data transformation/integration process typically involves three steps: (i) Extract, (ii) Transform and (iii) Load. ETL and ELT perform these steps in different orders. ETL loads data into a data warehouse, and the transformation step is necessary before loading. ELT, on the other hand, loads data into a data lake, and transformation takes place after loading but before data is further processed into a data warehouse/database. ELT may require more storage since it loads the raw data directly, which is usually bigger than the transformed data, while ETL is more economical in terms of storage cost but with potential information loss due to data transformation. However, storage on Cloud nowadays is cheap, and powerful Cloud compute and data services can be leveraged to carry out the transformation step for structured, unstructured, and semi-structured data in data lakes. ELT can keep all source information for future consumption, minimize data loss, and help with data recovery and time travel. A typical data warehouse may have limited capability and may be less efficient to perform additional transformations on data already loaded into the warehouse, but advanced Cloud data warehouses such as AWS Redshift and Google BigQuery can handle additional transformations at scale and at relative ease. Additionally, there are powerful data processing and granular data access control tools in Lakehouse paradigms such as Databricks^([1](#chap9.xhtml#rfn1)) Delta Lake that address many practical challenges associated with ETL/ELT workflows at any scale. So, from the modern enterprise data management perspective, ELT may represent the future direction and is more future-proof. However, ETL may still be needed for legacy data pipelines and workflows, and many existing well-developed ETL tools can be adapted to assist ELT pipelines and workflows.

![](images/p329.jpg)

**Figure 9.2.**A sample Cloud data integration pipeline

*What to look for when designing or choosing data integration solutions in the Cloud?*

Firms in need of enterprise data integration solutions should look for the following desired characteristics:

1.  *Big Data capability*: For a data application, simply being on Cloud does not guarantee its capability for Big Data handling. Enterprise data integration solutions need to leverage distributed processing frameworks such as Hadoop and Spark.
2.  *Interoperability*: Integration solutions need to be portable among different Cloud platforms. This is especially important for firms adopting a multi-Cloud strategy.
3.  *Support for both ELT and ETL based data workflows*: Modern enterprise data integration starts at the data lake layer as opposed to the data warehouse layer. Both ELT and ETL are needed for integration at different layers.
4.  *AI/ML-enabled*: AI/ML tools can bring speed, quality, and accurate predictability to data-driven decision-making. For example, AI/ML can be used to assist at scale: 
    1.  Data catalog and data lineage/dependency tracking;
    2.  Data mastering such as entity resolution, matching, merging, and deduplication; and
    3.  Sensitive data identification/de-identification
5.  *Open integration framework*: Open frameworks can connect Cloud data centers to on-premises data centers and easily integrate with automated data governance and privacy management, metadata management, API management, and master data management tools. They support continuous improvement with ease of embedding new tools/functionalities developed either in-house or by third parties. They also enable integration beyond data to provide unified solutions to integrate data with applications such as analytics, data science, BI, ML modeling, and visualization. Strong open integration frameworks typically have robust partner ecosystems for applications, database, and Big Data integrations.

There are unified data integration and analytics platforms on the Cloud that fit the bill, such as Databricks, Talend, and SnapLogic. Some of these vendors also maintain open-source versions of their respective data applications.

**9.5.3*Sensitive Data Management in the Cloud***

*How can Cloud data access control be leveraged for sensitive data?*

For the sensitive data that have already been loaded into the Cloud, release of data to target users can be controlled with RBAC and ABAC approaches. To maximize the utility of data and minimize the loss of information, any necessary data anonymization can be applied right before data release to the target users. If we anonymize data too early, users may have difficulty processing anonymized field. For example, if age is masked by hashing, then if a user decides later on to define age groups for modeling, he/she may not be able to recover that information from the masked field. These kinds of problems can arise if internal policy requires that all sensitive data need to be anonymized prior to being loaded to the cloud. In addition to potential loss of information by anonymizing too early, big data sets may be difficult to anonymize outside of the Cloud. One solution is to load all plaintext data into a secure Cloud area, perform necessary plaintext data operations there, and anonymize sensitive fields (original and derived) right before the data is released to authorized users. Static and automated Cloud data access control policies can be utilized to control the release of and access to anonymized and/or plaintext data.

Fine-grained data access control policies and data masking policies can be dynamically and automatically generated and enforced at scale, according to programmable security and privacy control logics using the technologies discussed before (through policy variables). This approach can turn manual Cloud data loading/access approval processes into automated access controls. Of course, not all business approval processes can be automated. Even for automatable processes, sometimes we may opt to have a human in the loop to ensure critical business controls. So, there is still a place for manual/semiannual approval processes. Nonetheless, at least in the enterprise data management area, automated access controls offer the benefit of great efficiency, timeliness, and avoidance of manual error.

Additionally automatic sensitive data tracing and policy enforcement frameworks such as Data Capsule, can be implemented in the Cloud to intelligently track the flow of sensitive data and automatically perform policy actions including but not limited to controlling access to and release of original and processed sensitive data.

*How to perform privacy-preserving data processing and computing in the Cloud?*

There are a number of ways privacy-preserving data processing and computing can be performed in the Cloud. For data tables with primary/foreign keys involving PIIs, users can hash these keys and then match on hash key values. This method can be implemented as easily in the Cloud as on-premises. The Cloud provides a variety of hash functions for database indexing.

Differential privacy is a very popular privacy-preserving technique, and there are open-source libraries available implementing various differential privacy algorithms. A popular one is the Python Differential Privacy Library in PyPI. Google also made its differential privacy library for aggregate statistics available on github. It is the library that helps power some of Google’s core products including Google Maps, Fi MVNO, and Gboard. The functionality is currently available in C++, Go, and Java. Also launched by Google in 2019 is an open-source Python library Tensorflow Privacy \[[14](#chap9.xhtml#rref14)\] for model developers to conduct Machine Learning model training with differential privacy. Microsoft and Harvard University jointly developed the OpenDP (Open Differential Privacy) platform \[[15](#chap9.xhtml#rref15)\], and it includes an open-source library of differential privacy algorithms. These differential privacy libraries can be used in conjunction with Cloud client libraries/cloud APIs on AWS, Azure, GCP, and other Cloud platforms.

Another privacy-preserving computing approach is through the Cloud server side and/or client-side encryption. Cloud environment configuration settings are available to encrypt data on ingestion and at rest. Cloud client-side encryption libraries allow users to encrypt and decrypt data using industry standards and best practices. In addition, Cloud cryptographic computing capabilities (via homomorphic encryption) can be leveraged to handle data encryption in use, so that numerical calculations can be performed on encrypted data with no plaintext information revealed. The trusted execution environments (TEE) approach for cloud confidential computing also employs encryption for any data (input, intermediate, or output) outside of the secure processor. So, it can be regarded as an encryption in use approach for protection against internal and external security/privacy threats. For firms’ most sensitive data, users may also encrypt or anonymize it prior to ingestion to the Cloud and then encrypt it again by the Cloud on ingestion, so that even in case the Cloud security is compromised, their most sensitive data are still protected. However, the downside is that users cannot perform computing with such doubly encrypted data.

In a multi-party setting, for example, if we need to leverage private data from a large number of edge devices in fog computing, or if multiple firms or multiple units/regions within the same firm are jointly calculating analytics or training ML models while keeping their own private data, multi-party computing (MPC) protocols can be implemented for privacy-preserving computing. In MPC protocols, private data from individual parties are not transferred or aggregated into a central location. Instead, analytics/model parameters are first computed on individual parties’ own devices (local computing step) and then aggregated to arrive at the overall analytics/model parameters (central coordination step). An iterative process may be required between local computing and central coordination steps to obtain the final desired output. Broadly, these MPC protocols can be classified into two categories according to different levels of security and privacy requirements: (i) federated learning and (ii) coopetitive learning. In federated learning, a trusted central server is required for central coordination. This central server will receive intermediate output from each party and may be able to infer certain private information from such output. As such, federated learning is often used in conjunction with differential privacy to help reduce the degree of potential information leak. In coopetitive learning, on the other hand, the coordination step is performed jointly by all parties, and no trusted central party is employed. In every iteration, each party broadcasts encrypted intermediate data (e.g., summary statistics, loss function, gradients, parameter updates, etc.) to all other parties and performs encrypted calculation in the local computing step. Then their local results are synchronized into a single set of global results. Zero knowledge proof can be used to verify the local computation among parties. While coopetitive learning protocols can provide the highest level of security and privacy protection, the communication cost can be high if too many parties are involved. Therefore, they are better suited for collaboration among institutions or organizations rather than millions of individual retail customers. Coopetitive learning can also be implemented via the TEE approach to relieve users from the high homomorphic encrypted computing cost for Big Data projects.

For privacy-preserving computing with sensitive data, in addition to hash/encryption tools and differential privacy libraries, users can leverage confidential computing services offered by major Cloud platforms. For MPC, Tensorflow Federated is available as an open-source library, Private Join and Compute can be installed and run on the command line, and Cloud partner solutions, such as Enveil ZeroReveal and Inpher XOR, are available on the Cloud marketplace. A number of open-source coopetitive learning protocols in the UC Berkeley RISE Lab MC2 suite discussed previously can also be deployed in the Cloud. Additionally, another RISE protocol Delphi can be used to facilitate Deep Learning inference with the Cloud holding the model and the user holding the input vector, without any sharing of model or input data between parties.

**9.6Case Study: CapitalOne’s Data Migration Journey to the Cloud**

Capital One is a Fortune 500 financial service company that offer services in credit cards, consumer banking (e.g., consumer and auto loans), and commercial banking. In 2020, Capital One completed a full migration from on-premises data centers to the public Cloud \[[16](#chap9.xhtml#rref16)\]. Their Cloud migration journey can be helpful for other organizations to learn from.

In 2015, Capital One settled on their Cloud-first strategy. They made the decision to re-architect their existing applications for the Cloud and, in the meantime, develop all new applications in the Cloud. Since then, the firm never looked back. They started out by matching on-premises data service components to Cloud data service components, and took a “lift and shift” approach to migrate applications to the Cloud. Then they turned to Cloud native data services that were either non-existent or costly to build or set up on-premises and utilized those to help materialize the benefits of a Cloud platform to its fullest potential. They came to realize that great power and flexibility with the Cloud also brought higher risks if not utilized properly. They followed the guidelines of the AWS Well-Architected framework to build applications and infrastructure in the Cloud. The framework covers five pillars: (i) Operational Excellence, (ii) Security, (iii) Reliability, (iv) Performance Efficiency, and (v) Cost Optimization. By focusing more on the first two pillars from the get-go, Capital One was able to build a solid foundation for the other three pillars as well along the way.

As the Cloud platform is continuously evolving with enhancements to existing services and additions of new services, Capital One has been closely monitoring the latest advances in Cloud technology and improving their own Cloud-based services. They have also heavily leveraged Cloud DevOps tools to facilitate its use of Infrastructure as Code (IaC), Microservices, Continuous Integration and Continuous Delivery (CI/CD), and Monitoring and Logging, which greatly enhance their data and software lifecycle management in continuous feedback loop. Their agile Cloud-based DevOps processes allow them to develop new features and products quickly, process large amounts of data efficiently in near real-time, and provide a highly effective platform to generate business analytics, train machine learning models and drive data-driven decisions.

Despite remarkable achievements, their Cloud journey is far from smooth-sailing. Some setbacks, including the massive data leak incident that had occurred in July 2019, led to doubts and the erosion of public confidence in their ability to execute their Cloud strategy. However, they learned their lessons, strengthened their Cloud governance framework, stayed the course of their cloud journey, and ultimately achieved success. By leveraging the might of Cloud, Capital One is leading the way in the financial industry in terms of offering customers brand new banking experiences as well as the establishment of an effective and efficient digital banking infrastructure that helps to shape the future of digital banking.

**9.7Ending Remarks**

Cloud and related technologies serve as a great enabler for highly effective and efficient enterprise data integration. The Cloud offers greater scalability, reliability, availability, flexibility, mobility, collaborativity, accessibility, and a lot more freedom and choices of solutions. It is up to us to utilize all these tools to the best of their potentials.

**References**

[1](#chap9.xhtml#ref1).“AWS Documentation”. Amazon Web Services. [https://docs.aws.amazon.com/index.html](https://docs.aws.amazon.com/index.html). Accessed: November 20, 2021.

[2](#chap9.xhtml#ref2).“Azure documentation”. Microsoft. [https://docs.microsoft.com/en-us/azure/](https://docs.microsoft.com/en-us/azure/). Accessed: November 20, 2021.

[3](#chap9.xhtml#ref3).“Google Cloud Documentation”. Google. [https://cloud.google.com/docs](https://cloud.google.com/docs). Accessed: November 20, 2021.

[4](#chap9.xhtml#ref4).L. Wang, J. Near, N. Somani, P. Gao, A. Low, D. Dao and D. Song, Data Capsule: A New Paradigm for Automatic Compliance with Data Privacy Regulations. Accessed: August 30, 2019. \[Online\]. Available: [https://arxiv.org/abs/1909.00077](https://arxiv.org/abs/1909.00077)

[5](#chap9.xhtml#ref5).“Helping organizations do more without collecting more data”. Google Security Blog. [https://security.googleblog.com/2019/06/helping-organizations-do-more-without-collecting-more-data.html](https://security.googleblog.com/2019/06/helping-organizations-do-more-without-collecting-more-data.html). Accessed: June 19, 2019.

[6](#chap9.xhtml#ref6).F. Turan, S. Roy and I. Verbauwhede, “HEAWS: An Accelerator for Homomorphic Encryption on the Amazon AWS FPGA,” *IEEE Transactions on Computers,* Volume 69, Issue 8, pp. 1,185–1,196, 2020.

[7](#chap9.xhtml#ref7).N. Kumar, M. Rathee, N. Chandran, D. Gupta, A. Rastogi and R. Sharma, CrypTFlow: Secure TensorFlow Inference. Accessed: March 19, 2020. \[Online\]. Available: [https://arxiv.org/abs/1909.07814](https://arxiv.org/abs/1909.07814)

[8](#chap9.xhtml#ref8).“Introducing Google Cloud Confidential Computing with Confidential VMs”. Google Security and Identity Blog. [https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-confidential-computing-with-confidential-vms](https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-confidential-computing-with-confidential-vms). Accessed: July 14, 2020.

[9](#chap9.xhtml#ref9).“Announcing General Availability of AWS Nitro Enclaves”. Amazon Web Services. [https://aws.amazon.com/about-aws/whats-new/2020/10/announcing-general-availability-of-aws-nitro-enclaves/](https://aws.amazon.com/about-aws/whats-new/2020/10/announcing-general-availability-of-aws-nitro-enclaves/). Accessed: October 28, 2020.

[10](#chap9.xhtml#ref10).“Confidential computing on Azure”. Microsoft. [https://docs.microsoft.com/en-us/azure/confidential-computing/overview](https://docs.microsoft.com/en-us/azure/confidential-computing/overview). Accessed: November 11, 2021.

[11](#chap9.xhtml#ref11).A. Dave, C. Leung, R. Popa, J. Gonzalez and I. Stoica, “Oblivious coopetitive analytics using hardware enclaves,” *Proc. 15th European Conf. Computer Systems,* Article No.: 39, pp. 1–17, April, 2020.

[12](#chap9.xhtml#ref12).W. Zheng, R. Popa, J. Gonzalez and I. Stoica, Helen: Maliciously Secure Coopetitive Learning for Linear Models. Accessed: September 3, 2019. \[Online\]. Available: [https://arxiv.org/abs/1907.07212](https://arxiv.org/abs/1907.07212)

[13](#chap9.xhtml#ref13).W. Zheng, R. Deng, W. Chen, R. Popa, A. Panda and I. Stoica, Cerebro: A Platform for Multi-Party Cryptographic Collaborative Learning. *30th USENIX Security Symposium (USENIX Security 21),* pp. 2723–2740, August, 2021.

[14](#chap9.xhtml#ref14).“TensorFlow Privacy”. Google *et al*. [https://github.com/tensorflow/privacy](https://github.com/tensorflow/privacy). Accessed: December 21, 2020.

[15](#chap9.xhtml#ref15).“OpenDP: Open Differential Privacy” Microsoft and Harvard University. [https://github.com/opendp](https://github.com/opendp). Accessed: November 19, 2021.

[16](#chap9.xhtml#ref16).D. du Preez, “Capital One closes its data centres and goes all in with AWS”. Diginomica. [https://diginomica.com/capital-one-closes-its-data-centres-and-goes-all-aws](https://diginomica.com/capital-one-closes-its-data-centres-and-goes-all-aws). Accessed: January 12, 2021.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap9.xhtml#fn1)Databricks is a first party service on Microsoft Azure cloud, and Databricks is also available on AWS and GCP.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0010](https://doi.org/10.1142/9789811250903_0010)

Chapter 10

**Smart Home for Financial Services: Security, Privacy, and Solutions**

***Jun Xu***

**10.1Introduction**

The home is the center of our human society. Many people view the home as the most restful and comfortable place, and spend more than half of their time at home. With technological advances, in particular, the Internet of Things (IoT) \[[1](#chap10.xhtml#rref1)–[8](#chap10.xhtml#rref8)\], this view is strengthened. Smart homes, mainly based on IoT technologies, incorporates intelligence into dwellings management and home operations, as IoT edge and Cloud services together with artificial intelligence (AI) and Blockchain techniques provide ubiquitous sensing, data security, and intelligent computing functionalities.

From the technical point of view, the traditional smart home aims at connecting sensors, home appliances, and smart devices via the Internet and local (wireless) area network to achieve (remote) monitor, access, and control of a residential environment. In other words, it uses the IoT paradigm for automation capability to react to the requirements of its inhabitants, providing convenience, comfort, and security. From the social perspective, the smart home shall have ambiently intelligent, sensitive, and adaptive environments to meet modern human and social demands. The goal of the smart home is to increase home automation, simplify resource management (e.g., energy and water), reduce resource waste (e.g., environment release and pollution), improve living conditions, and bring more benefits to the home.

At the same time, many financial services, e.g., payments, transfers, loans, insurance, etc., can be delivered via Online Banking or Mobile Banking nowadays, with the aid of financial technology (FinTech). In fact, over half of banking services can be accessed at home instead of at the bank. During the COVID-19 pandemic since late-2019, home-based services definitely bring conveniences and benefits to the clients.

Now the question is how to seamlessly integrate financial services into smart home systems with high security and client satisfaction, when the pandemic becomes the new normal. In this chapter, we will discuss integrated solutions with the fusion of IoT, AI, and Blockchain technologies, which shows a promising smart home platform for future financial services.

**10.2Smart Home**

**10.2.1*Application and Classification***

The smart home system has been widely used in our daily lives, from your door to your entertainment system. We summarize the application of the smart home into eight categories, as listed in [Table 10.1](#chap10.xhtml#tab10-1).

Home control is the largest portion of smart home applications currently. There are many matured products available in the market, e.g., Google Home and Amazon Echo. Voice assistant systems have become more closely integrated with home control facilities. Video surveillance is one of the most important applications in the category of home security and safety. China supplies nearly two-thirds of consumer surveillance cameras in the global market, and Hikvision and Dahua are among the top three in the world.

For home utilities, many cities in China have implemented the NB-IoT or Bluetooth measurers, which automatically send readings to service providers. In Singapore, some recently-launched Housing Development Board (HDB) apartment buildings have similar measurement devices embedded within the public facilities.

**Table 10.1.**IoT categories

 
| **Category** || **Examples** |
| --- | --- |
| Home control || 

*   Thermostat/HVAC control
*   Lighting control
*   Household appliances (fridge, washing machine, cooking, water heater, vacuum, etc.)
*   Robotics
*   Indoor/outdoor plant watering
*   Many others in smart bedroom, kitchen, bathroom, living room, etc.

 |
| --- | --- |
| Home Security and Safety || 

*   Remote surveillance (remote video camera, window, door, or appliance motion sensors)
*   Intrusion detection (motion detection, glass breakage, IR beam interruption etc.)
*   Door or windows locker and smart doorbell
*   Drug, smoke, water leakage, freezer, heat, fire, gas, carbon dioxide, carbon monoxide, etc., detection and alarm

 |
| Home Utilities or Public services || 

*   Water, electricity, gas, etc., manager
*   Energy management, e.g., solar power

 |
| Home Entertainment || 

*   Digital contents: video, music, software, etc.
*   Gaming system (VR/AR)

 |
| Smart workspace or home office || 

*   Remote learning and working from home
*   Telepresence (remote event/meeting/etc.)

 |
| Smart Interface and smart home hub || 

*   Interface to smart education, smart wearable, smart healthcare, smart living, smart city, smart grid, smart transportation, etc.

 |
| Data services || 

*   Smart data hub
*   All aspects of data management

 |
| E-commerce and financial services || 

*   Smart devices for e-commercial, e.g., speaker, tablet and television
*   Alternative site for financial services

 |

The home entertainment system can recommend suitable video, music, and software to residents. You may also play virtual reality (VR) games with an AI assistant. If you prefer to work from home, which has become a preferred choice during the new-normal pandemic, a smart workspace facility will make your work easy. Ideally, the smart home shall have enough interfaces to other smart objects and services, e.g., smart education, smart healthcare, smart grid, smart transportation, etc. For example, to make full use of a private parking slot for public parking, you can rent it out when you are not using it during some time. The used solar power energy gathered in your home can be also sold to the public electric network. Most of these services can be integrated into the smart home hub, e.g., AWS Echo, Google home, Xiaomi Home, and AliGenie.

Not enough attention is being paid to home-based data services, e.g., how the data generated by home devices and personal mobile devices are being properly used and shared for financial services. When the smart home concept is widely adopted, data collected in the home level will be more valuable than that collected from an individual’s single device. Thus, the data aggregation has an increasing value. When smart home users can benefit from their own sensing data, a dedicated data bank for exchange is therefore necessary.

[Figure 10.1](#chap10.xhtml#fig10-1) shows the data sources from multiple types of IoT devices, e.g., some environmental sensors and home appliances. We shall note that the home server can be a potential device for edge computing, which can provide a certain level of intelligence, while Cloud can provide deep analysis. [Table 10.2](#chap10.xhtml#tab10-2) summarizes major requirements for smart home systems \[[4](#chap10.xhtml#rref4), [6](#chap10.xhtml#rref6), [8](#chap10.xhtml#rref8), [9](#chap10.xhtml#rref9)\]. Intelligence is definitely a key factor for customers’ adoption and satisfaction. We have seen that many smart hubs, such as the AWS Echo and Google Home, are replacing the previous router-based hub. With more devices and data integrated into one single hub, security and privacy concerns are attracting more attention.

![](images/p342.jpg)

**Figure 10.1.**IoT devices at smart home

**Table 10.2.**Major requirements for smart home

 
| **Objective** || **Explanation** |
| --- | --- |
| Heterogeneity || The ability to connect heterogeneous things and exchange information among them in a given network. |
| --- | --- |
| Self-configuration and diagnosis || The ability to register, modify, and delete things automatically, and diagnose potential problems. |
| Extensibility and scalability || The ability to change the functionality of things, the scale of networks, the adoption of new techniques, and the connection to other smart home networks. |
| Context awareness || The capability to recognize the changes of the things and their environments, e.g., when, where, and what. |
| Usability || The user friendliness — easy to use and learn. |
| Security and privacy protection || The ability to protect the smart home against malicious attacks and unauthorized usage of private information. |
| Intelligence || The ability to interact with human beings with strong computing and storage capability in either edge or the Cloud. |

**10.2.2*Security and Privacy***

Security and privacy are two major issues in the current IoT ecosystems \[[9](#chap10.xhtml#rref9), [10](#chap10.xhtml#rref10)\]. It was reported that more than half a million IoT devices were cracked in 2017. The IoT security objectives are listed in [Table 10.3](#chap10.xhtml#tab10-3) \[[19](#chap10.xhtml#rref19)\]. For example, authentication is usually related to the object or service registration, i.e., the first step to build a connection, and authorization means that the user would require permission to use the services.

Privacy is conceptually different from security. For example, if an IoT device with useless data stored inside is stolen or cracked, it is a security issue but not a privacy issue, as it does not contain anything confidential. Some general objectives for privacy design are listed in [Table 10.4](#chap10.xhtml#tab10-4). Privacy of the smart home is essentially related to personal activities, location, and timestamp \[[18](#chap10.xhtml#rref18)\]. From the data-oriented aspect, it contains aggregation and transmission of the sensed data (e.g., an individuals’ private data), and from the context-oriented aspect, it refers to the mechanisms related to location and timing, i.e., protecting the location and timing of users’ data generated from unnecessary exposure. We shall note that the end-users and the service providers usually hold different views.

**Table 10.3.**IoT security objectives

 
| **Objective** || **Explanation** |
| --- | --- |
| Authentication or Authenticity || An act of verifying the truth or origin of the credentials or attributes provided. |
| --- | --- |
| Authorization || A process to specify the access rights/permissions to the resources of interest. For example, resources could be a data table with personal information. |
| Accountability || An ability to trace the historical activities to resources of interest. |
| Confidentiality || An act or rules to limit the access to resources of interest. For example, ensure the data readable by the proposed destination only. |
| Integrity || An assurance that resources of interest are accurate, complete and trustworthy. |
| Availability or accessibility || Provides reliable and robust access to resources of interest to authorized people. |
| Nonrepudiation || An implication of complete obligation to a particular contract or transaction. |
| Freshness || An ability to keep freshness of data and key. |

Due to the constrained computational and storage resources, most of the IoT devices cannot use full stack implementations, which increase the difficulty in strong level of security and privacy preserving. [Table 10.5](#chap10.xhtml#tab10-5) lists some challenges to maintain a high standard of security. For example, many organizations are promoting their own standards, making it difficult to create a universal standard.

**Table 10.4.**Privacy objectives

 
| **Objective** || **Explanation** |
| --- | --- |
| Transparency || Consistency in understanding the persons and activities during the data access and processing, e.g., access duration, operators, permission, etc. |
| --- | --- |
| User-driven || Complete control of users’ own data, i.e., the full and granular access control over their shared data in the network. |
| Anonymity || Non-disclosure of the identity of users in IoT applications. |
| Pseudonymity || A trade-off between anonymity (privacy) and accountability. The personal actions are related to a pseudonym or a random identifier, rather than an identity. |
| Unlinkability || A degree of pseudonymity in that the specific actions of the same person should not be inter-related so that the personal profiling in IoT can be prevented to an extent. |
| Unobservability || An ability that the access history of a resource or service is not allowed to be observed by unauthorized persons, i.e., the unauthorized users and/or subjects cannot determine whether an operation is being performed. |
| Decentralization || P2P sharing, i.e., each node in the network shares its data with others node directly, without intervention of any third or trusted entity. |

**10.2.3*Trust Evaluation***

Once the system is designed, we shall evaluate whether it is trusted or not \[[11](#chap10.xhtml#rref11), [12](#chap10.xhtml#rref12)\]. Trust is defined as a key property to establish reliability, trustworthiness, and connectivity between devices to ensure the security and safety of the services and applications. [Table 10.6](#chap10.xhtml#tab10-6) enumerates some evaluation metrics. For example, the system shall be generally robust and adaptive.

**10.3Financial Services**

Financial services cover multiple aspects, e.g., make and receive payments (domestic and across borders); save, consume, or invest later; borrow to consume or invest now; manage risks relating to income, savings, and transactions; and provide advisory on all the above, etc. For a consumer bank, its daily operations include savings accounts, current accounts, mortgages, loans, credit cards, and debit cards. Some services can be done via online banking or mobile banking.

**Table 10.5.**IoT security challenges

 
| **Items** || **Explanation** |
| --- | --- |
| Constrained resource || In particular, the limited computational and memory resources enforce a constraint in the system design. |
| --- | --- |
| Heterogeneity devices || Different security measures between different devices due to IoT’s heterogeneous nature. |
| QoS || Allow differentiated delivery and ensure quality of service. |
| Trust management || Keep the privacy confidential. |
| Lightweight authentication/ authorization || Implementation in the resource constrained devices. |
| Key and identity management || There is no absolute safe box. Multiple encryptions rules shall be applied. |
| Standardization on protocols, middleware, etc || So far, there is no general platform to unify all the protocols, although we can see some protocols are becoming dominated in the markets, and some middleware, platforms, or operating systems (OSs) are merging or have more functionalities embedded. |

Nowadays, financial institutions (FIs) are under the pressure of technology innovation. In particularly, FinTech startups are taking over many businesses from traditional FIs, and expanding the domain of the financial industry, e.g., payment and loan. As the saying goes, “Banking is essential, but banks are not”. Without a successful digitalization evolution or revolution, traditional retail banks may become extinct.

The key forces for FinTech are high-scalability, low-latency, and high-availability requirements of digitalization, web-scale computing, hybrid transactional, and analytical processing, etc., (see [Figure 10.2](#chap10.xhtml#fig10-2)). They are further driven by major fundamental technologies, such as AI, Big Data, IoT, Blockchain, and Cloud, which essentially require an upgrade of current computational and storage resources for better performance and scalability. These technologies do not exist on its own. Technical fusion is active in the evolution of technologies. In [Chapter 2](#chap2.xhtml), we explain the relations among these technologies \[8, 13–16\].

**Table 10.6.**IoT system trust evaluation

 
| **Metrics** || **Explanation** |
| --- | --- |
| Trustworthiness || Robust to overcome various potential attacks.The research should prevent the IoT systems from various attacks, for example, DoS, node control, counterfeit original attack, and so on. |
| --- | --- |
| Adaptability || Adaptive to context changes with dynamic support.In the IoT application scene, the relationship is dynamic changing between nodes, such as nodes joining and leaving a system in very short time. |
| Usability || Usable for users with regard to user-device interaction in order to provide more intelligent services interacting with humans. |
| Privacy || Preserve user privacy when user data is collected for trust evaluation.It should allow legitimate users to preserve their privacy to the maximum extent. |
| Accuracy || Accurate to evaluate trust or reputation. |
| Efficiency || Efficient to dynamically manage trust relationships in the IoT systems in order to ensure network layer security. |
| Uniformity || Uniform for users voting with trustworthy credibility to evaluate objects trust values. |
| Comprehension || Support various trust influencing factors to achieve accurate evaluation. |
| Generality || Suitable for various IoT systems and services that can be commonly used in different application scenarios. |

![](images/p347.jpg)

**Figure 10.2.**Computing requirement for FinTech

The smart home, embedded with many physical assets and digital devices, provides a more secured identity than a single personal wearable. Some banking services, such as “opening a new Class I account” in China, may require an in-person verification on-site at the bank’s branch, which is generally not able to be processed online in a single mobile device (e.g., smartphone) because the device cannot guarantee that the unique and genuine identity is presented in a secured and safe environment, even with the live facial detection technology. However, the smart home with more facilities for sensing makes it possible. We will explain this further in the following sections.

**10.4General Infrastructure**

A conceptual infrastructure is proposed in [Figure 10.3](#chap10.xhtml#fig10-3). It consists of some building blocks — the smart home, FIs, governmental organizations, public service providers, and ICT infrastructure providers. The central secured analytical cloud connects all these parts. Do note that in order to achieve more flexibility, the whole system will need to be software-defined enabled \[[17](#chap10.xhtml#rref17)\], e.g., the separation of data platform and control platform.

![](images/p348.jpg)

**Figure 10.3.**A simplified workflow for smart home architecture

![](images/p349.jpg)

**Figure 10.4.**Conceptual infrastructure of small-home-based financial services

[Figure 10.4](#chap10.xhtml#fig10-4) of a simplified architecture illustrates a basic workflow among sensors, edge devices, the Cloud, and mobile devices. The data must be encrypted before it is sent to the others or to the Cloud. A possible encryption solution is the so-called Privacy Enforcement Points (PEPs).

**10.4.1*Smart Home Sensing Networks***

Technically, a local smart home system contains four building components: (i) controllable devices, (ii) sensor, actuators, and controller, (iii) the (wireless) network of sensing and control, and (iv) the (remote) control devices. [Figure 10.5](#chap10.xhtml#fig10-5) shows a general infrastructure with the component stacks for the smart home system.

**10.4.2*Digital Twin and Digital Identity***

While the concept of a digital twin has been around since 2002, it was IoT technology that made it affordable and accessible to many businesses. A digital twin is a virtual or digital model of a process, product, or service. This pairing of the virtual and physical worlds allows for the analysis of data and the monitoring of systems to preempt problems before they even occur, prevent downtime, develop new opportunities, and even plan for the future by using simulations and emulations. In short, it generally uses a digital copy of the physical system to perform real-time optimization. Normally, smart IoT sensors that gather data on real-time status, working conditions, or position are integrated with a physical device or system. The device or system are usually connected to a Cloud-based system that receives and processes all the sensing data, which is further analyzed against business and other contextual data. With the development of AI and distributing computing techniques, more analysis is conducted in the edge side, e.g., live facial and voice recognition. In addition, the emerging spatial computing digitizes the Cloud objects, and enable sensors and motors to react to interactive events, and then build the digital representations of reality.

![](images/p350.jpg)

**Figure 10.5.**The general IoT infrastructure of building blocks

The digital twin technology helps the financial industry to improve customer experience by better understanding customer needs, developing enhancements to existing products, operations, and services, and driving the innovation of new businesses. With the digital twin, the financial industry also gets a secured and safe identity for the targeted objects with IoT and biometrics (see [Chapter 11](#chap11.xhtml)).

Digital twins often take pre-existing (private) data and turn it into a simulation and prediction. During this process, the Blockchain can make digital twins permanent, immutable, and decentralized. So, they cannot be deleted or changed; instead, they can be accessed from multiple places. If a digital twin for humans were to be built with traditional technologies, it will still need us to trust a central intermediary that will hold all the data and perform analytics for the predictions. While machines do not care who owns their data, the human generally will care. Blockchain then allows the technology to create these identities on an immutable ledger, with no central party owning that data. This means that it enables a self-sovereign identity where the owner of the data decides who gets access to their data and they can track everyone who has accessed it. In some cases, the trusted third-party agents may also use a consortium DLT (distributed ledge technology) instead of a fully decentralized Blockchain.

The expansion of the digital twins together with AR, VR, and MR (mixed reality) technology leads to another concept, the Metaverse, which is a virtual world parallel to the real world and is highly interoperable (see [Chapter 2](#chap2.xhtml)). The so-called total experience (combining multi-experience, customer experience, employee experience, and user experience to transform business outcomes) proposed by Gartner can be relatively easy to implement and illustrate inside the Metaverse compared with the physical world.

**10.4.3*Blockchain-based Solution***

To keep data in the smart home secured and private, we can use the Blockchain technology. [Figure 10.6](#chap10.xhtml#fig10-6) provides a Blockchain-based solution for financial services in the smart home. Essentially, a hybrid Blockchain shall be implemented. For example, the association of smart homes may organize or apply for a public Blockchain, while the FIs implement a consortium DLT. Different chains may use different digital currency or token systems, with some exchange agents in the overlay network.

![](images/p352.jpg)

**Figure 10.6.**Blockchain-based smart home structure

![](images/p352-1.jpg)

**Figure 10.7.**A simplified workflow for sensing data

We use overlay network because it can cluster some nodes and virtualize the network. It also provides an additional security mechanism. As we know, the Blockchain is not an absolutely secure solution. Therefore, we shall carefully design the security protocols in each layer.

Let us consider an example that a smart home can sell and publish its sensing data. [Figure 10.7](#chap10.xhtml#fig10-7) illustrates how the sense data is verified and valued by the IoT data broker and device manufacturer. The links show how the data is transmitted among four parties. First of all, we shall guarantee that the sense device is trusted. Therefore, a verification between the data broker and the device manufacturer shall be conducted via a public key mechanism. Once the data is verified, the data broker will publish it to the Blockchain. Here, we may have the flexibility to choose between a consortium or a public Blockchain network.

10.4.3.1*Consensus protocol*

It is generally difficult for IoT devices to apply PoW (proof of work) as the underlaying consensus policy due to the limited computational power of IoT devices. Thus, we can adopt the so-called PoW + PoS (proof of stack) + PoT (Proof of time) policy. The PoW is a pseudo one, as it does not actually do some computational work. It works with the PoT through an auxiliary awarding system, which includes two parts. One is the quality and volume of sensing data that the IoT device contributes to the data platform. The sensing data can be sold to the purchasers based on its qualitative, quantitative, and privacy levels. The other is the involvement of online activities, e.g., how active is the IoT involved in the platforms’ general missions or tasks controlled by smart contracts. For example, the completion of online tasks, such as remote sensing for a particular scenario, sharing services, gaming, etc.

The PoS can be achieved by a directly linked credit via an exchange platform. It means the user can increase their credit for higher chances to mine the block. Note that a dynamic exchange ratio between real money and virtual digital currency with relatively stable value shall be maintained to an extent.

10.4.3.2*Smart contract*

[Figure 10.8](#chap10.xhtml#fig10-8) illustrates how data or other goods can be sold via a smart contract without a central agent. The payment can be done through cryptocurrency, e.g., Bitcoin, Ethereum, and a smart home coin, or digital currency issued by central banks (CBDC). In this sense, the trading may or may not be closely monitored by the FIs or governments, depending on the type of digital currency used. Of course, the smart contract can be also signed in a supervised way in a different DLT setting.

![](images/p354.jpg)

**Figure 10.8.**Smart transactions via contract

10.4.3.3*Reconfigurable Blockchain*

Due to the limited resources in some smart home devices, it is generally impossible to hold all blocks of a frequent transaction chain. Therefore, it is necessary to define several levels of integration and security to allow users to choose their preferences. For example, users can choose to store data in the last seven days into their IoT devices only, while querying other data from the smart home hub or their association’s Cloud server.

**10.5Smart Home-based Financial Applications**

Once the Blockchain-based and AI-aid platform is set up, we may develop various financial applications of the smart home with designed business objectives. In this section, we enumerate some potential examples.

**10.5.1*Mixed Currency***

Digital assets and virtual/digital currency are important applications. For example, once a refrigerator is manufactured, a transaction will be sent to the Blockchain. Therefore, it has a unique and immutable record in the network. Any owner change can be simply done online. The following are some general cases:

*   Asset virtualization/digitalization (Blockchain/DLT) 
    *   Physical assets, e.g., real-estate, car, home appliance, etc.
    *   Monetary assets, e.g., cash, stock, CPF, etc.
    *   Data assets, e.g., IoT data, creative digital works, etc.
*   Virtual currency with actual value 
    *   Not limited to virtual money in the gaming
    *   IoTCoin — secured consumers information, e.g., different level for different shops and native rewarding system

**10.5.2*Smart Payment***

The smart pay service now is widely used, e.g., mobile applications and e-wallets. New use cases and commercial IoT applications that can initiate remote payment are certainly emerging, including smart assistants (voice-enabled devices, e.g., Amazon Echo, AliGenie, and Google Home), refrigerators, and in-car dashboard systems. An alternative currency, e.g., IoTCoin or smart home coin, may be available for your digital items or home facilities in the near future. It can be used for auto or mobile payments, such as online shopping (possibly via AR/VR/ MR, and automatic product comparison and recommendation); license for software, game, video, music, books, etc.; TV subscriptions, VoD, news, courses, and other digital content; subscription for remote surveillance and healthcare services; public utilities (gas, electricity, water, etc.); automatically adjust usage and frequency for efficiency and saving; real-time alerting system for abnormal events, etc.

**10.5.3*Customized Loans***

Loans (home, personal, car, etc.) is one of the fundamental financial services, which still relies on a passive mode currently. In this mode, customers generally initialize the request. The so-called conversion of credit card balance to cash is one of the simplest cases.

For the active mode, banks take the initiative to propose a proper loan to the customers. In this case, banks need to understand the customers’ actual requirements, which are likely to be obtained by analyzing the data collected from the smart home hub with users’ consent. Unfortunately, it may deeply infringe upon the customer’s privacy. Therefore, banks need to have a proper solution to keep a balance between recommendations and privacy with customers’ consent.

**10.5.4*Personalized Insurance***

Again, personal or family insurance has both passive and active modes. The passive mode is similar to a traditional counter service (initialized by costumers), although some online services (i.e., a shopping cart with multiple options, questions-based wizard, etc.) are available. The active mode tries to understand the insured object’s status in a realtime matter, e.g., a trip. The following are a few examples:

*   On-demand insurance, e.g., micro-duration and atomization of insurance by item;
*   Smart home and property insurance with smart home sensing capability;
*   Personal health issuance — health conditions via smart healthcare and wearable techniques;
*   Car insurance — car conditions via smart sensing techniques, e.g., driving behavior sensing and analysis, telematics and driverless cars;
*   Weather insurance — a weather-concerned activity, e.g., insurance for an outdoor trip.

**10.5.5*Smart Investment***

Gearless customized plans from conservative to aggressive objectives can be provided based on combined expert mode and an AI mode, e.g., capital guaranteed deposit with various interest rate, and capital non-guaranteed investment with various return rate. For the AI-aided selection, the system will need to fully understand the customers’ investment preference, and then suggest adjustable and customized financial plans. This may also lead to investment platform changes, e.g., from a traditional bank’s direct investment to a P2P (bank-backed) investment. In a sense, the contract will be more complex but more “standard”.

**10.5.6*Data Banking and Marketplace***

The massive collection of information in smart homes shall be categorized, indexed, and valued. A data exchange agent is also engaged and connected for value realization. The service is also extendable for exchanging other resources via digitalization and tokenization, e.g., the energy generated by solar panel. The collection of such services may form a (virtual) data bank or marketplace under regulation.

**10.5.7*IoT Contractor or Broker***

Ideally, there might be an IoT information marketplace such that categorical information is exposed to the public and it will likely enhance transparency, create a liquid trading market, and reduce friction in the trading processes. However, the asymmetric information may still exist, depending on how you use the public information wisely. Therefore, authorized “agents” can provide many types of microservices, e.g., the transaction of smart objects and security trade. Brokers can use IoT sensors to generate and analyze information to unlock new possibilities. In particular, the IoT data broker can setup a micro-billing framework, and a mart commission system, etc.

**10.5.8*Total Management***

An integrated IoT and AI system for personal or family financial management can:

*   Continuously monitor your social activities and online or offline behavior to understand your personality;
*   Intelligently analyze your financial situation, such as your insurance, loans, bank accounts, etc., to understand your risk level and preference; and then offer dedicated digital financial assistant for total financial management, e.g., investment, pension, etc.;
*   Closely track your health conditions and provide suggestions;
*   Provide a smart home data broker with multi-level privacy protection.

Digital twin and metaverse technologies help to understand the efficiency of financial management and improve your financial quality. Note that users shall have full control of their own data, and decide if their data can be shared to a third party.

**10.6Conclusion**

This chapter describes a conceptual infrastructure and a potential implementation solution of smart home for financial services. Essentially, it is a fusion of the IoT, AI, Cloud, Blockchain, and Big Data technologies. Due to the impact of the COVID-19 pandemic, the work-from-home arrangement has become a growing trend in today’s working environment, and more activities will be performed at home, including many financial-relevant events, e.g., online shopping, online trading, etc. The smart home facility provides not only the convenience but also the security. A proper governance framework shall be implemented for IoT data privacy and security. The smart home is also an important component for a smart city and smart nation. Singapore’s “Smart HDB Town Framework”, for instance, encapsulates a 4-pronged approach that HDB is taking to introduce smart into housing estates — Smart Planning, Smart Environment, Smart Estate, and Smart Living. The similar concept and technology can be easily extended to the smart car, which is the mobile “home” in some countries.

The IoT technology in the financial market size is expected to grow to US$2 billion by 2023, up from US$249.4 million in 2018 with a CAGR of 52.1% during the forecast period of 2019–2024, according to Markets and Markets.^([1](#chap10.xhtml#rfn1)) The smart home, as one of the largest portions of IoT industry, will definitely grow even faster during the pandemic. FIs shall define their strategy to adopt the trend.

**References**

[1](#chap10.xhtml#ref1).C. Perera, C. Liu and S. Jayawardena, “The emerging internet of things marketplace from an industrial perspective: A survey,” *Emerging Topics in Computing, IEEE Transactions on,* Vol. 3, No. 4, pp. 585–598, Jan 2015.

2.C. Perera, C. H. Liu, S. Jayawardena and M. Chen, “A survey on internet of things from industrial market perspective,” *IEEE Access,* Vol. 2, pp. 1,660–1,679, Dec 2014.

3.M.-C. C. Chun-Wei Tsai, Chin-Feng Lai and L. T. Yang, “Data mining for internet of things: A survey,” *IEEE Communications Surveys and Tutorials,* Vol. 16, No. 1, pp. 77–97, Nov 2013.

[4](#chap10.xhtml#ref4).L. D. Xu, W. He and S. Li, “Internet of things in industries: A survey,” *Industrial Informatics, IEEE Transactions on,* Vol. 10, No. 4, pp. 2,233–2,243, Jan 2014.

5.H. Zhou, *The Internet of Things in the Cloud: A Middleware Perspective.* Boca Raton, London, New York: CRC Press, 2013.

[6](#chap10.xhtml#ref6).A. Al-Fuqaha, M. Guizani, M. Mohammadi and M. Aledhari, “Internet of things: A survey on enabling technologies, protocols, and applications,” *IEEE Communications Surveys and Tutorials,* Vol. 17, No. 4, pp. 2347–2376, Jun 2015.

7.P. N. Flavio Bonomi, Rodolfo Milito and J. Zhu, *Big Data and Internet of Things: A Roadmap for Smart Environments,* ser. Studies in Computational Intelligence. Springer, 2014, Vol. 546, Ch. Fog Computing: A Platform for Internet of Things and Analytics, pp. 169–186.

[8](#chap10.xhtml#ref8).E. Borgia, “The internet of things vision: key features, applications and open issues,” *Computer Communications,* Vol. 54, pp. 1–31, Dec 2014.

[9](#chap10.xhtml#ref9).E. M. Jorge Granjal and J. S. Silva, “Security for the internet of things: A survey of existing protocols and open research issues,” *IEEE Communication Surveys* & *Tutorials,* Vol. 17, No. 3, pp. 1,294–1,302, Jan 2015.

[10](#chap10.xhtml#ref10).J. Gubbi, R. Buyya, S. Marusic and M. Palaniswami, “Internet of things (IoT): A vision, architectural elements, and future directions,” *Future Generation Computer Systems,* Vol. 29, p. 16451660, Sept 2013.

[11](#chap10.xhtml#ref11).I. Mashal, O. Alsaryrah, T.-Y. Chung, C.-Z. Yang, W.-H. Kuob and D. P. Agrawal, “Choices for interaction with things on internet and underlying issues,” *Ad Hoc Networks,* Vol. 28, p. 6,890, May 2015.

[12](#chap10.xhtml#ref12).J. Mineraud, O. Mazhelis, X. Su and S. Tarkoma, “A gap analysis of internet-of-things platforms,” arXiv: 1502.01181, Tech. Rep., 2015.

13.A. R. Biswas and R. Giaffreda, “IoT and cloud convergence: Opportunities and challenges,” in *Internet of Things (WF-IoT), 2014 IEEE World Forum on,* Seoul, Mar 2014, pp. 375–376.

14.G. Fersi, “Middleware for Internet of Things: A study,” in *International Conference on Distributed Computing in Sensor Systems (DCOSS),* Fortaleza, Jun 2015, pp. 230–235.

15.E. I. Gaura, J. Brusey, M. Allen, R. Wilkins, D. Goldsmith and R. Rednic, “Edge mining the internet of things,” *IEEE Sensors Journal,* Vol. 13, No. 10, pp. 3,816–3,825, Jun 2013.

16.V. Gazis, M. Gortz, M. Huber, A. Leonardi and K. Mathioudakis, “A survey of technologies in internet of things,” in *Wireless Communications and Mobile Computing Conference (IWCMC), International,* Dubrovnik, Aug 2015, pp. 1,090–1,095.

[17](#chap10.xhtml#ref17).Y. Jararweh, M. Al-Ayyoub, A. Darabseh, E. Benkhelifa, M. Vouk and Rindos, “SDIoT: a software defined based internet of things framework,” *Journal of Ambient Intelligence and Humanized Computing,* Vol. 6, No. 4, pp. 453–461, Aug 2015.

[18](#chap10.xhtml#ref18).A. Ouaddah, A. A. Elkalam and A. A. Ouahman, FairAccess: a new Blockchain-based access control framework for the Internet of Things, *Security and Communication Networks,* Vol. 9, pp. 5943–5964, 2016.

[19](#chap10.xhtml#ref19).O. Sangpetch and A. Sangpetch, Security Context Framework for Distributed Healthcare IoT Platform, International Conference on IoT Technologies for HealthCare, pp. 71–76, 2016.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap10.xhtml#fn1)“IoT in Banking and Financial Services Market”. Markets and Markets. [https://www.marketsandmarkets.com/Market-Reports/iot-banking-financial-services-market-172304505.html](https://www.marketsandmarkets.com/Market-Reports/iot-banking-financial-services-market-172304505.html)

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0011](https://doi.org/10.1142/9789811250903_0011)

Chapter 11

**Biometrics in FinTech: A Technological Review**

***Jun Xu***

**11.1Introduction**

Biometrics is a technical term used to describe measurements and calculations for human bodies. It refers to the metrics or indexes of some human characteristics that can provide a reasonable degree of confidence in the authentication of a person with a certain level of convenience. Therefore, biometrics authentication (or at least, realistic authentication) is applied as a form of identification and access control.

Till now, biometrics has been widely applied in law enforcement, public security (e.g., criminal or suspect investigation), civilian registration, border, travel, or migration control, civil identification and healthcare (e.g., national identity document verification, resident or voter identification), e-commerce, and physical and logical access control (e.g., owner, user, employee, contractor, or partner identification). In financial institutions (FIs), biometrics has been broadly adopted in various services and products, such as e-banking, online payments, and e-onboarding. During the COVID-19 pandemic, contactless, password-free, and frictionless biometrics-based approaches are getting accepted by a growing number of clients.

The biometric market is expanding rapidly since early 2010, and it is expected to be valued at US$32.7 billion by 2022, according to a forecast by MarketsandMarkets.^([1](#chap11.xhtml#rfn1)) Another forecast by the Global Industry Analysts indicates its market size will reach US$82.8 billion by 2027, 19.3% CAGR from around US$24.1 billion in 2020.^([2](#chap11.xhtml#rfn2)) Mobile biometrics applications are most prevalent and their market is projected at US$79.8 billion by 2027, with a CAGR of 23.7% from US$18 billion in 2020.^([3](#chap11.xhtml#rfn3))

**11.1.1*Taxonomy***

Biometric identifiers are often categorized into two groups: (i) physiological and (ii) behavioral characteristics. Physiological characteristics are usually associated with the shape of the body, such as fingerprint, face recognition, palm veins, DNA, palm print, hand geometry, iris, retina, odor, and scent. Behavioral characteristics are usually linked to the pattern of human behavior, including but not limited to signature, typing rhythm, gait and lip motion. A few biometrics may have both physical and behavior characteristics, e.g., voice, heartbeat, and brain wave. [Figure 11.1](#chap11.xhtml#fig11-1) shows typical biometrics with physiological, behavioral characteristics, or a combination. [Table 11.1](#chap11.xhtml#tab11-1) describes the key features of those biometrics in more detail \[[1](#chap11.xhtml#rref1), [3](#chap11.xhtml#rref3), [5](#chap11.xhtml#rref5)\].

The fingerprint, face, and voice are typical physical biometrics, and have been widely used in financial applications. Some other biometrics, e.g., Iris Recognition and Retinal Scanning, Palm, Finger, Ear Geometry, and Vein are becoming popular, due to the rapid improvements in both sensing devices and recognition algorithms.

![](images/p363.jpg)

**Figure 11.1.**Biometrics classification

**Table 11.1.**Summary of biometrics

 
| **Metrics** || **Description** |
| --- | --- |
| Brain Wave/EEG || 

*   It measures signals from the brain to build a unique individual feature set on the database. Some researchers believe EEG to be 100% accuracy for biometric identification. It is usually measured by electroencephalogram (EEG) devices.

 |
| --- | --- |
| Fingerprint || 

*   It uses the image features, such as Line types, Core Point, Delta, Ridge Count, Ridge Patterns (Loop, Arch, Whorl), to create fingerprint pattern.

 |
| Footprint and Foot Dynamics || 

*   It captures the biometric identification characteristics of the footprint of a human, and is relatively new when compared to the fingerprint.

 |
| Gait || 

*   It analyzes the manner of walking or running of a human by his/her saunter, swagger, sashay, etc.
*   It is now widely used for surveillance purpose.

 |
| Gesture || 

*   It can be made from any part(s) of the body, especially hands, arms, legs, fingers, the head, and even from facial expressions.
*   A combination of several actions is even more expressive, and thus more accurate.

 |
| Hand/Finger Geometry || 

*   It indicates the shape of a human’s hand characteristics in multiple dimensions.

 |
| Heartbeat Measurement/ ECG || 

*   A variety of phenomena, e.g., electric, optical, pressure, and acoustic, can be used to sense heartbeat. However, it is usually measured by electrocardiogram (ECG) devices.

 |
| Iris || 

*   This metric measures the unique patterns in the colored circle of human eyes by controlling the diameter and actual size of the pupil, and the amount of light reaching the retina.

 |
| Lip Motion || 

*   It analyzes a human’s lip motions and creates a pattern according to its activity.

 |
| DNA || 

*   Deoxyribo Nucleic Acid (DNA) is an essence of every living cell, which does not change through the life of human beings. Tangible physical sample is required in non-real-time manner.

 |
| Odor || 

*   Use the body odor of a human for verification and identification.

 |
| Pulse response || 

*   It is based on a human body’s unique response to an electrical pulse and measured when that individual holds two diodes (one in each hand) and a weak electrical current (e.g., 1V) passes through.

 |
| Retinal Scanning || 

*   It usually uses infrared technology to capture the unique patterns of a human’s retina blood vessels through the cornea and the lens.

 |
| Skin Reflection || 

*   Various wavelengths of light generated by several LEDs is reflect into the human skin, and photodiodes read the scattered light that is then analyzed to perform the authentication.

 |
| Signature and Handwriting || 

*   It captures the main characteristic of handwriting (dynamic or static), e.g., speed, velocity, and pressure. It captures images (static) and has high user acceptance and etc.

 |
| Sweat || 

*   It captures the sweat profile, sometimes can even measure sweat pores.
*   It is usually used as a complementary metric.

 |
| Thermography || 

*   Infrared cameras are used to capture the flow of blood beneath the skin of a human.
*   It is often applied in human “liveness” test together with other tests such as face recognition.

 |
| Typing and keystroke || 

*   It captures the users’ typing patterns, e.g., speed, press and release rate, dwell time (duration of a key being pressed), flight time (the interval between releasing key and pressing another key), unique patterns of keys, comparisons, and etc.
*   The keystroke dynamics measure the manner and the rhythm of a human’s typing on a keyboard.

 |
| Voice and Speech || 

*   It is a combination of physiological and behavioral biometrics to capture speech/voice characteristics, e.g., frequency, nasal tone, inflection, duration, cadence, etc.
*   It is also called as automatic speech recognition (ASR), computer speech recognition, or speech to text (STT).

 |

Although many biometrics have some common features, they generally have their unique features. For example, although iris and retina are similar biometrics with high accuracy, they have some essential differences as described in [Table 11.2](#chap11.xhtml#tab11-2). The iris controls the diameter, actual size of the pupil, as well as the amount of light reaching the retina. The iris has two layers, i.e., stroma (the front part) and pigmented epithelial cells (the opposite part). Iris recognition is performed by measuring the iris’s unique characteristics, e.g., wavelength and melanin. Two typical recognition process methods are the Daugman system and Wilders system. On the other hand, the human retina is a light and highly sensitive layer of tissue made of neural cells located in the back part of the eye, the third and inner coat of the eye. Infrared technology can be used to capture the unique patterns of a human’s retina blood vessels through cornea and the lens.

**Table 11.2.**Comparison of iris and retina

|  || **Iris** || **Retina** |
| --- | --- | --- |
| Common || 

*   Ocular-based unique physiological characteristics of eyes
*   Contactless image capturing facilities
*   Generally stable during lifetime (except for few diseases for retina)
*   High accuracy (although the accuracy of retina scan is even higher than that of Iris scan)

 |
| --- | --- |
| Performance || 

*   False Positive: very low
*   False Negative: almost 0%
*   Reliability: very high due to uniqueness
*   Recognition speed: fast

 |
| Characteristics || Pattern of the colored circle of eyes || Pattern of retina blood vessels of eyes |
| Difference: Disease || Stable features; almost not affected by diseases || May change due to diseases including diabetes, glaucoma and retinal degenerative disorders |
| Measurement Distance || Normal distance like a photograph to get an accurate scanning || Close measurement distance between a person and the retina scanner |
| Complexity || Relatively easy and less complex to use compared to retina scanning || Relatively complex and not acceptable in many circumstances |
| Acceptance || Highly acceptable for most commercial occasions; suitable for both physical and digital scenarios || Not widely accepted for generally commercial purposes; suitable for physical identification |
| Invasive || Normal photograph without invasive issue || Although a visible light beamed into the eye is not considered invasive, it may cause discomfort |

Unlike most physical biometrics, behavioral biometrics can often be collected from existing hardware, e.g., surveillance camera for gait, the keyboard and mouse of computer or smart phone for typing, moving, and keystroke. This usually makes behavioral biometrics simpler and less costly to implement with a software. For example, the speed of typing, the time duration from one letter to another, the degree of impact on the keyboard, the mouse movements, and finger motion on trackpads or touchscreens are unique to individuals and not difficult to detect with a simple app. However, as their detection accuracy is relatively lower than the fingerprint, face, or iris, they can be used as a complementary metrics, e.g., detection if the input is from a human or a robot, if the user of a device is changed, etc. Therefore, they are useful for online fraud detection.

Voice, heartbeat, and brain wave have strong physical characteristics, and also significantly influenced by human behavior, to be more specific, physiological behavior. For example, the heartbeat patterns during a peaceful mood and an anxious one could be very different.

By applying biometrics into business products and services, tons of benefits can be gained for FIs.

**11.1.2*Benefits Brought by Biometrics***

Essentially, biometrics provide a high-level of security for the authentication and authorization of financial services without scarification of convenience. It is universal but unique for all individuals, and permanent in most cases, recordable, and measurable. At the same security level, biometrics offer many advantages compared to the pin- or token-based traditional methods, including:

*   Superior user experiences due to the convenience and availability, e.g., no demand for complex passwords and PINs;
*   Lower operational costs, e.g., manual authentication is not required for large call centers;
*   Omnichannel usability for customers consistently, conveniently, and securely across all channels including web, mobile app, automated teller machines (ATM), phone banking, online banking, web chat, in-store or online shopping, digital assistants (e.g., Alexa, Tmall Genie, etc.), and more, without a duplicated authentication process. For example, an Alipay app inside a smart phone can link your bank account, check your balance, and pay for your favorites in millions of online and offline shops; and
*   Avoidance of disclosing stolen information obtained from a malicious data breach.

**Table 11.3.**The pros and cons of biometrics

 
|  || **General cases** || **Specific cases** |
| --- | --- | --- |
| Pro || Security, accuracy, accountability, convenience, flexibility, trustable, time-saving || ROI, scalability, cost-saving |
| --- | --- | --- |
| Con || Non-changeability of physical traits, error rate, delay environment and usage matters, system integration || Unhygienic, access/operation difficulty for physical disability, cost for some advanced biometrics, e.g., brain wave. |

[Table 11.3](#chap11.xhtml#tab11-3) provides further illustration on the pros and cons of general and specific cases.

While biometrics provide a unique “passport” for human beings, a general question is if biometrics can lead to a fraud-proof financial service in the future. A simple answer is that although it is not 100% guaranteed, it is highly likely to be close to this value with integration of multiple biometrics.

**11.2Biometric Characteristics**

When deciding which biometrics to use for a financial app, we must consider their characteristics carefully. [Table 11.4](#chap11.xhtml#tab11-4) lists some main properties to consider, although their weights changes under different scenarios. For example, their performance (e.g., accurately identifying the right person) for a critical financial application (e.g., personal authentication for releasing of loan) is always the top criteria. However, it is also important to choose a technology that can be easily accepted and used by customers, particularly, on mobile devices. Therefore, we shall think about universality, convenience, collectability, and usability at least.

**Table 11.4.**Desirable properties \[[2](#chap11.xhtml#rref2)\]

 
| **Metrics** || **Properties** |
| --- | --- |
| Universality || Every individual should have the characteristic and possesses the trait. |
| --- | --- |
| Uniqueness || Every individual should have a unique characteristic that is distinguishable from others. |
| Robustness || The characteristic should not display variance with time, e.g., example variance over time. It shall be able to detect the liveness, not a faked one such as video, picture, or synthetic voice. |
| Collectability and scalability || The characteristic should be easily extracted or collected from the subjects, e.g., the capture process shall be painless and harmless. It shall also have an efficient capability of processing a chosen biometric in both enrolment and claim of the capture steps. |
| Unobtrusiveness || The biometric should be maximally transparent. Ideally, it should be used in a passive manner, without any extra requirements added to users’ normal behaviors, or interacting with users. |
| Repeatability and stability || The characteristic should be sufficiently distinct and repeatable to achieve high recognition rate of the subject. The characteristic shall be relatively permanent in term of its invariance or stability over time and in different contents. |
| Circumvention Difficulty, or Spoof resistance || The characteristic must be difficult to circumvent in any security context, i.e., difficult to be duplicated. |
| Performance || The application’s performance indexes mainly refer to FAR, FRR, success/false detection rate, etc., for recognizing individuals. |
| Acceptability || This characteristic represents the level of willingness of a user to apply the biometric. |
| Usability || This characteristic indicates the level of convenience of its usage, e.g., enrolment (the biometrics’ initial (training) phase should be made as simple as possible). |
| Cost Effectiveness || This characteristic is related to the cost of development, deployment, and maintenance. |

Some performance metrics, such as the false acceptance rate (FAR) and the false rejection rate (FRR), shall be carefully reviewed with a proper threshold. The FAR is the possibility of somebody other than you being allowed to access your account. Low FAR is the most important factor for security concerns. The FRR is the probability that you are not authorized to access your own account. A low FRR is essential when convenience has high priority. Other indexes include true acceptance rate (TAR = 1-FAR), weighted error rate (the weighted sum of FRR and FAR), and success/false detection rate, etc. Customers will not trust a system that fails to recognize a biometric that they have no power to change. Once your authentication system relies on a biometric identifier, it must recognize it every time or the bank risks alienating its customers.

We shall also make sure that the biometrics patterns for an individual is reliable. In fact, some biometrics are intrinsically probabilistic, and therefore potentially fallible. The probability of an error can be drastically reduced but not completely eliminated, which should be handled by system designers, developers, and operators carefully.

In reality, we may also need to consider data quality and integration with privacy. Unlike passwords which can be easily changed, biometrics are unique features that you cannot revise generally. Thus, secured storage and proper usage become a big topic, which will be discussed later.

**11.2.1*Comparison***

To select one or a few proper biometrics for an application, we need to compare them along several metrics. [Table 11.5](#chap11.xhtml#tab11-5) summarizes the comparisons between some commonly used biometrics.^([4](#chap11.xhtml#rfn4)) For example, the DNA is more accurate than the fingerprint; however, it has no advantage on convenience and cost over fingerprint. Fingerprint identification device now can be made small and slim enough to be embedded into a credit card; however, the same is impossible for DNA devices which are usually used in labs. [Tables 11.6](#chap11.xhtml#tab11-6) to [11.8](#chap11.xhtml#tab11-8) further list the major features of the biometrics with their advantages and disadvantages \[[1](#chap11.xhtml#rref1), [3](#chap11.xhtml#rref3)–[5](#chap11.xhtml#rref5)\].

**Table 11.5.**Comparison of biometrics characteristics

![](images/p371.jpg)

**Table 11.6.**Physiological metric comparison

![](images/p371-1.jpg)

![](images/p372.jpg)

![](images/p373.jpg)

**Table 11.7.**Behavior metric comparison

![](images/p374.jpg)

**Table 11.8.**Combined metric comparison

![](images/p375.jpg)

**11.3Data Matters**

**11.3.1*Data Privacy and Security***

Biometric data is defined as a special category of personal data that can be processed for uniquely identifying a natural person. More precisely, biometric data are “personal data resulting from specific technical processing relating to the physical, physiological, or behavioral characteristics of a natural person, which allows or confirms the unique identification of that natural person, such as facial images or fingerprint data.”^([5](#chap11.xhtml#rfn5)) The security of biometrics is more important than that of passwords, as the latter can be easily revised if they are disclosed, while the former cannot.

Biographic data is protected under personal data protection regulations, e.g., the GDPR in EU and the PDPA in Singapore. The use of biometric data must be given with the corresponding persons’ consent. The abuse of biometrics in the hands of a third party must be prevented. Similar to AI technology, FIs must have their ethical, legal, and social considerations when applying biometric technology.

One risk to be highlighted here is data leakage and steal, e.g., the data can be captured in one transaction during the transmission from a sensing device to a remote database, and then fraudulently reproduced in another transaction. To avoid that, FIs must implement stringent data protection and privacy measures across their core systems for secured data transmission, processing, and storage. They need to ensure data integrity and prevent data leakages that could lead to identity fraud.

**11.3.2*Data Storage***

The storage methodology for biometric data varies by the user scenarios. Data can be stored in remote systems (e.g., cloud) or local devices. Below are two typical types:

1.  The first type is the portable devices, for example, smartphones and smart cards (token), where personal biometric data can be stored. As users have the freedom to control their biometric data, user acceptance of those devices is increased. Some devices with processing units (e.g., smartphones) offer a viable advantage of quick response during user authentication as the reference template is locally stored and can be fetched quickly without the Internet. This is the most common way nowadays due to the popularity of smartphones. FIs even do not need to collect and store the information themselves. Some smart tokens with crypto-currency may also use this approach.
2.  The second type is the networked (remote) devices or servers, e.g., a centralized biometric database or distributed servers. Typically, a central biometric database server, possibly in the Cloud, is used to keep biometric templates. It is a relatively inexpensive implementation of biometric authentication on the average, and is beneficial for multi-location authentication, although centralization may be a performance bottleneck without proper design.

In some countries, centralized databases of face and fingerprint are created nationwide. For example, India created its Aadhaar database containing biometrics, e.g., the fingerprint and eye scans, for many of its 1.2 billion citizens, and has offered them to commercial entities, e.g., technology firms, healthcare providers, and app developers, in the last few years. Some FIs, e.g., Ujjivan and IDFC, use Aadhaar in their apps. China also collects face information, and most FIs utilize the data for client identification. Some Chinese nationwide digital payment apps, such as WeChat and Alipay, use biometrics with users’ consent too.

Note that it is unlikely to store raw information of biometric data such as a full image of the fingerprint and the iris. However, the encrypted features extracted from biometric templates might be stored. Commonly used protection techniques for biometric templates are usually divided into two categories: (i) cancellable transformation and (ii) biometric cryptosystem. The cancellable transformation is a type of feature transformation which is computationally difficult to revert the original data, such as non-invertible transforms (e.g., robust hashing algorithms). Dimension reduction is one approach in this category to calculate an optimal subset of predictive features measured in the original data for model building. Biometric cryptosystem usually uses either a key-binding approach, which is independent from the features with the template, or a key-generating approach with the cryptographic key directly generated from the helper data and the query features. This approach may be integrated with block-chain techniques.

**11.4Biometric Accesses**

There are generally two steps to apply biometrics in authentication services at financial services.

*   *Enrolment* (Capture, Transformation/cryptosystem, and Storage). This process is performed once to create reference or template data for comparison and securely store it in the device or database, which is usually performed once per device. It can be done by the user independently or assisted by a bank employee at the branch.
*   *Authentication* (Capture, Recognition, Identification, and Verification). It is performed every time when users intend to enter the service. A general procedure is as follows: 
    *   The biometric data is captured from an individual (e.g., acquisition);
    *   The biometric data template is prepared by extracting and transforming feature sets. Perform encryption or decryption if necessary;
    *   The transformed biometric template and the reference template in the database or device are compared for identification and verification. Usually, there are two types of results returned: (i) “pass” or “fail”; (ii) identified ID.

**11.4.1*Attack Vectors***

During the access procedure of biometrics authentication, many potential attacks may happen, for example:

*   Fake biometrics, including physical and digital types, are used for masquerade attacks and replay attacks, and from the input side usually. The masquerade attack uses fake biometric data such as digitized facial images and latent fingerprints, which can be extracted from surfaces the targeted users have touched or the device memory where the templates are stored. A replay attack, or a false data inject, happens inside the biometric system to replay the reference dataset or templates. It may have middle-man-attacks involving capturing the biometrics data and replaying it later. An alternative way is to inject a fake data stream between the sensor and the processing system, or override feature extraction. The false data can be a synthesized data generated by AI models.
*   Feature, template, or parameter override or modification often happens in the process side. For example, the acceptance threshold or other key system parameters may be modified to accept a false or low-quality data, the biometric template may be revised to tamper without proper authorization.
*   Some other general attack techniques in the hardware, operating system (OS), and network include access right modification, decision override, and denial of services (DoS). Weak hardware and algorithm design often lead to unauthorized access to the device storage to pilfer the biometric template or bypass the compromised templates.

Thus, the security department of FIs must include biometric risks into their monitoring portfolios.

**11.4.2*Multimodal Biometric System and Multi-Factor Access***

Smartphones have become the most important media of biometrics access as there were 3.5 billion sets of smartphones in circulation in November 2020.^([6](#chap11.xhtml#rfn6)) The phone and its auxiliaries can provide multiple sensing information. Its direct sensors include but not limited to graph, movement, touch, or movement pattern, voice recognition, facial recognition, fingerprint, iris recognition, etc. Some of its auxiliary sensors from wearing devices (e.g., watch, glasses) can measure heartbeat or rhythm, sphygmus, etc. In other words, the smartphone itself is a multimodal biometric system (MBS), as it combines more than one biometric for authentication.

A typical way required for critical transactions is to use hybrid authentication or authorization technology from multiple sensors (possibly integrated with existing technologies such as passwords, 2-factor authentication (2FA), use of e-tokens, and hardware SIM overlay) for enhanced security. However, the multi-factor access (MFA) is not straightforward; in fact, it faces many challenges as illustrated in [Figure 11.2](#chap11.xhtml#fig11-2). For example, it could increase the difficulty in system integration and robustness. To start, we shall create a proper procedure with a certain degree of fault-tolerance. Some big banks may even establish direct collaboration with phone manufacturers such as Huawei, Samsung, Lenovo, and Xiaomi for dedicated security certification solutions and applications.

The MFA for a digital account access may have the following ways with increased security levels:

![](images/p380.jpg)

**Figure 11.2.**Challenges of using the multi-factor access (MFA)

*   Level 1: A digital password, pattern, or signature, or smartphone-based identity via one or multiple sensors, e.g., face, iris, fingerprint, signature, and typing.
*   Level 2: Authentication via SMS, dedicated hardware token, or software token.

In a more critical scenarios, it may have more levels:

*   Level 3: Authentication in a dedicated app for voice- and video-based verification.
*   Level 4: Authentication in a nearby ATM-like self-service machine with higher quality sensors via face, iris, fingerprint, palm, and gesture to confirm liveness and uniqueness.
*   Level 5: Authentication in dedicated devices inside branch, e.g., retina, vein, and ECG.

The MFA may also gain benefits from Cloud services, e.g., some biometrics may be stored in cloud as a part of the complex MFA system. For a general IoT-based authentication with a biometric system and edge computing device, it works as follows — the sensor pre-processes and extracts the biometrics raw data, then the edge device is used to generate, and possible store some biometric template data, for pattern match to the reference data in the local database. If the reference data is in Cloud, the encrypted template data will be sent to the Cloud for further verification.

**11.5Security Enhancement: Embedded AI**

Artificial intelligence (AI) can analyze biometric characteristics to create a digital identity that allows for a much more secured authentication, which is essential for financial services. It can be also used in indexing, template protection, spoofing attack detection, ROI detection, gender classification, etc. \[[6](#chap11.xhtml#rref6)\]. For example, the raw data of a face can be represented geometrically using a few hundred reference points covering the whole face. When people wear surgical masks during the COVID-19 period, the traditional approach may not be effective as fewer feature points are captured. With Deep Learning technology, more information is processed from a few photos or a video of a face and then fed into an irreversible hash cryptographic function to create an irreversible pattern data to the Cloud for better verification. Deep Learning techniques are also helping liveness detection algorithms to be more accurate. Consequently, the manipulation of fingerprint readers and scanners now requires a much higher level of expertise that goes beyond the rudimentary spoof.

Many dedicated AI chips e.g., Huami, Intellifusion, AnyVision, Syntiant, and Xailient, are developed or are currently under development for this purpose. The Huami Huangshan-2(MHS002) is based on RISC-V architecture as an AI-backed cardiac biometrics engine. Syntiant’s solutions of edge AI processors target at a voice-controlled “multimodal” AI processor, while Intellifusion, AnyVision, and Xailient target at super-fast biometric face detection and identification chips.

When AI improves the security of biometrics technology, it is also used for attacks. In fact, AI can beat standard biometrics by deceiving it using synthetic fingerprints, manipulated printed 3-dimensional (3D) face image or mask, etc. Brute force attacks can be orchestrated with such synthetic data, trying every option till none are left. For example, Apple’s Face ID can be tricked by an altered pair of glasses in just 120 seconds. Deepfakes^([7](#chap11.xhtml#rfn7)) is an amusing but also threatening tool for the liveness detection of face biometrics.

**11.6Biometrics Applications in Financial Services**

In this section, the financial service applications of biometrics are discussed in details.

**11.6.1*General Category***

Biometrics are essentially used to identify personal characteristics, although they can also be applied for healthcare and personal health insurance. Here, we mainly consider its applications in individual authentication and group differentiation for digital identity and cybersecurity.

11.6.1.1*Mobile and online banking*

This is the most common application nowadays with various biometrics, e.g., fingerprint, face, iris, etc. Almost all banks, insurance companies, and trading platforms provide their mobile apps and online portal for business operations, i.e., it becomes a standard component for a modern financial institution.

Several recent advancements could be used to improve MFA methods for better convenience and security, e.g., biometric-based single sign-on (SSO) services, AI-backed hardware security module (HSM), and continuous user authentication.

11.6.1.2*Digital payment*

It is generally divided into online and offline categories. Offline devices can be a biometric embedded card (e.g., a credit card), a token device, or a mobile device. For example, the central bank digital currency (CBDC) issued in China supports offline payment. Online device is usually smartphone-based. Many banks support mobile apps with selfie payment and virtual credit card activation via face recognition and fingerprint (e.g., Apple Touch ID).

Based on Juniper’s study,^([8](#chap11.xhtml#rfn8)) by 2023, in-store and remote payments authenticated by mobile biometrics will have a market value of US$2 trillion, and the mobile biometrical-verified commerce transactions will represent a massive 57% of total biometric transactions from 28% in 2018.

11.6.1.3*Seamless digital onboarding, KYC, AML*

According to Forbes,^([9](#chap11.xhtml#rfn9)) digital account opening (DAO) is one of the most popular technologies in banking for the third consecutive year since 2018. Nearly 80% of all banks and credit unions were either adding new DAO systems or improving their existing ones in 2020.

Know your customer (KYC) is a mandatory due diligence process to identify and verify customers’ identity upon onboarding, e.g., DAO. It becomes a significant aspect of fighting against financial crime and money laundering. Biometrics-based authentication allows FIs to dramatically expedite their due diligence and eKYC activities to deliver fast and seamless onboarding experiences, from hours to few minutes.

Singaporean banks can enjoy the benefits of Singpass and its mobile apps to authenticate the customers and authorize their access to the customers’ government-certificated personal profile for opening new accounts. NatWest in the UK is one of the first major high street banks to open accounts using a selfie and AI-backed real-time verification. Branch video teller machines (VTMs) and mobile VTMs (e.g., portable-dedicated device or staff tablet) with face recognition and other biometrics sensors, support to open new account, issue debit cards, and provide personal identification numbers (PIN) on the spot or at the customers’ locations.

From the perspective of anti-money laundering and counter-terrorism financing (AML/CTF), the customer onboarding (enrolment) and transaction verification are the two most important steps. With multimodal biometrics system (MBS), potential bad actors, bots, and synthetic or fraudulent identities can be identified during the onboarding phase, while illegal activities, such as account takeover fraud, identity theft, and phishing can be prevented during the authentication phase. Therefore, the AML/CTF process can be enhanced dramatically by reducing the time and cost of onboarding, mitigating financial fraud and crime, improving compliance efficiency, and preventing many criminal events, such as unauthorized account access, fraudulent payments, and money mules.

11.6.1.4*Online fraud detection and cybersecurity*

When FIs are going through digitalization and increasing the varieties of digital services, particularly during the COVID-19 pandemic, cyber-attackers have become increasingly sophisticated. Without compromising users’ experiences, intelligent security measurements to detect cybercrime in omnichannel becomes more important. At the same time, online fraud continues to grow dramatically, and fraudsters are incessantly refining their attack bots and agents with new strategies to identify vulnerabilities and penetrate defenses.

[Table 11.1](#chap11.xhtml#tab11-1) and [Figure 11.1](#chap11.xhtml#fig11-1) seen earlier list behavioral biometrics that capture multiple forms of interactive gestures, keystroke, mouse movement, or tapping and typing pattern, to analyze a user’s online physical and cognitive behavior. By differentiating the patterns of digital behavioral traits common to fraudsters and trusted users, behavioral biometrics can be used to identify legitimate human users versus non-human cybercriminal actors like bots, and detect anomaly sessions, etc. This analysis generally works together with AI and Big Data technologies for better accuracy. Many companies provide relative matured solutions, such as ThreatMark, LexisNexis, and BioCatch.

11.6.1.5*Cardless ATM transactions*

Cash is still widely used in most countries. The traditional ATM allows customers to withdraw money with only physical cards and a digital PIN, which caused a loss of about 250 million Euros’ in 2018 in Europe due to ATM fraud, e.g., duplicated cards and PIN loss.^([10](#chap11.xhtml#rfn10)) However, as it is generally not easy to trace the wrongful users, anti-fraud detection for ATM is technically difficult. Therefore, some new types of ATMs using biometrics are built to enhance the security:

1.  *Biometric-equipped ATM.* Customers can use their fingerprint, face, palm, iris, etc., to get authenticated. However, this approach has the advantage of easy adoption, but leave the data storage security issue to banks.
2.  *App-enabled ATM.* Users can authenticate themselves via on-device biometrics and initiate transactions using the corresponding bank’s app. An example is the collaboration between Mastercard and Diebold Nixdorf for banking experiences with cardless ATMs.^([11](#chap11.xhtml#rfn11))

A similar idea can be applied to safe-box services in the bank.

11.6.1.6*On-site marketing*

In some on-site roadshow and promotion events, the prompters need to identify potential customers immediately when they pass by the venue. Experienced prompters may capture key information from the persons’ appearance, emotions, and movement trajectory, and quickly judge if they have the intention to buy the products or services. AI-based biometrics detection system can achieve the same with properly trained models.

11.6.1.7*Surveillance*

Besides the general video recording functionalities, such as cameras at the ATMs and in the branches, modern video surveillance system is able to detect the anomaly in a real-time manner. Signals such as anxious and nervous emotions, unusual movement trajectory and stiff body gestures, can be combined with other information, such as suspicious packages, bags, and clothes, to identify potential risks.

Recently, FIs also leverage video to help with compliance during the COVID-19 pandemic. As we adjust to the “new normal” situations, FIs need to create a safer environment for all employees and clients without compromising the service quality.

**11.6.2*Real-world Applications***

Due to the widespread of smartphones with the fingerprint scanner and camera, apps with fingerprint and facial recognition for authentication has become a standard configuration nowadays in many FIs, including Lloyds Banking Group plc, Standard Chartered, Barclays, Commonwealth Bank of Australia, HSBC, JP Morgan Chase, Mastercard, Deutsche Bank, USAA, Bunq, Visa, IDFC, Gulf Bank, BNP Paribas, Nequi, SMBC, etc.

Voice biometrics is also widely adopted by banks including ANZ Bank, Barclays, Citi Group, Wells Fargo, Santander UK, HSBC USA, Virginia Credit Union, TIAA, Sberbank of Russia, Standard Chartered, etc. Iris and retina are used on a relatively smaller scale, as they are not as convenient as face, fingerprint, and voice recognition devices. Some FIs also use online and mobile behaviors to detect anomalies. As the device to sense palm or hand geometrics or vein is still too big to be portable for personal use, they are usually deployed in the branches, at ATMs, and self-service machines. [Figure 11.3](#chap11.xhtml#fig11-3) lists a few more examples of biometric applications in FIs.

**11.7Future Directions**

Biometric technology has become a part of our daily life around the world, with the widespread use of smartphones and IoT wearables. When biometric authentication acts as a dominating approach, FIs interact with their clients through mobile applications and digital/ online banking services in a more convenient and secured way. With the advancements so far, we expect to see the following trends in the near future:

*   Traditional biometrics continue to improve their accuracy under complex scenarios with noise input. Some examples include facial recognition with masks, and voice recognition with noise cancellation.
*   More advanced biometrics, such as ECG and pulse response, will be widely adopted in the near future. Today, ECG modules are already contained in the Apple Watch G4, Samsung Galaxy Watch 3, the new Fitbit Sense, and Huawei GT2. These modules use flashing LEDs to penetrate the skin and sense blood flow and beats per minute (BPM). As more ECG modules obtain medical certification with high accuracy, the ECG can become a regular biometric in a few years. Brain wave could be next wave of biometric technology. Brain Machine Interfaces (BMIs) or Brain Computer Interfaces (BCIs) is one of the most promising fields for developing life-changing applications in the future. The EEG can be captured via non-invasive devices with much higher accuracy than in the past. Together with VR/AR devices, FIs can deliver fantastic virtual banking experiences to their clients.
*   “Invisible” MFA may be applied widely with users’ consent. For example, when taking a facial recognition scan, the iris and gesture recognitions can be carried out simultaneously, which means one action can have a multimodal process.

![](images/p388.jpg)

**Figure 11.3.**Sample applications in FIs

*   Both dynamic biometrics and scene-based biometrics help to augment security level. Instead of a static image, some recent face recognition techniques actually capture a dynamic video with multiple gestures to test its liveness. Some designed actions, such as blinking, emotions, mouth opening and closing, have been used in the given scenarios. For voice recognition, some random sentences may be required to be read out immediately to avoid pre-recorded or AI-generated voices. Dynamic, continuous or scene-based biometrics generally prevents imitation.
*   Reuse or reinvent the “old” component so that new biometric features can be captured in an innovative way. HeadFi, a new design paradigm example, brings intelligence to headphones. HeadFi turns the pair of headphones into a versatile sensor, which can lead to many new applications covering mobile health, userinterface, and context-awareness for heart rate monitoring and gesture recognition \[[7](#chap11.xhtml#rref7)\].
*   Biometric sensing modules are becoming more compact and intelligent with embedded AI processors. Smart sensor cards may be popular as an enhanced version of the credit or debit card. With the offering of digital currency such as digital yuan of China (CBDC), these physical or digital cards are not necessarily to be connected to Internet.
*   Biometric data can integrate with other data for extended applications. For example, typing patterns and navigation standards (e.g., mouse movements and finger movements) together with Internet data (e.g., the browser’s historical data, social media, etc.) can be used for anti-fraud of online credit card applications. Putting all the relevant information together may form a new concept named Internet of Behavior (IoB).

Essentially, the biometrics-based personal identity can be applied in both the physical and virtual worlds. When Banking-as-a-Service (BaaS) and FinTech-as-a-Service (FaaS) become popular, various APIs interact intensively on multiple platforms, biometrics can play a critical role in safeguarding platform-to-platform and customer-to-platform security. Meanwhile, when the virtual worlds, such as the Metaverse (see [Chapter 2](#chap2.xhtml)), attract more attentions from investors, developers, and users, digital identity generated by biometrics becomes a critical asset for the virtual or digital economy. To reap all these benefits, FIs shall develop their own strategies for capturing digital identities under sound regulatory frameworks.

**References**

[1](#chap11.xhtml#ref1).S. Dargan and M. Kumar, “A comprehensive survey on the biometric recognition systems based on physiological and behavioral modalities,” *Expert Systems with Applications,* Vol. 143, No. 113114, April 2020.

[2](#chap11.xhtml#ref2).MEI, “Security guidelines for use of biometric technology in e-governance projects,” Technology, Ministry of Electronics and Information, Government of India, New Delhi, 2017.

[3](#chap11.xhtml#ref3).M. S. Obaidat, I. Traore and I. Woungang, *Biometric-Based Physical and Cybersecurity Systems,* Springer, 2019.

4.R. Jiang, S. Al-maadeed, A. Bouridane, D. Crookes and A. Beghdadi, *Biometric Security and Privacy,* Springer, 2017.

[5](#chap11.xhtml#ref5).S. Bilan, M. Elhoseny and J. D. Hemanth, *Biometric Identification Technologies Based on Modern Data Mining Methods,* Springer, 2021.

[6](#chap11.xhtml#ref6).G. Jaswal, V. Kanhangad and R. Ramachandra, AI and Deep Learning in Biometric Security: Trends, Potential, and Challenges, CRC Press, 2021.

[7](#chap11.xhtml#ref7).X. Fan and *et al.,* “HeadFi: Bringing intelligence to all headphones,” in *MobiCom* ’21, 2021.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap11.xhtml#fn1)“Biometric system market with COVID-19 impact by authentication type”. Markets and Markets. [http://www.marketsandmarkets.com/PressReleases/biometric-technologies.asp](http://www.marketsandmarkets.com/PressReleases/biometric-technologies.asp). Accessed: Nov 21, 2021.

[²](#chap11.xhtml#fn2)Global Industry Analysts. “Biometrics — Global Market Trajectory & Analytics”. Research and Markets. [https://www.researchandmarkets.com/reports/5141259/biometrics-global-market-trajectory-and](https://www.researchandmarkets.com/reports/5141259/biometrics-global-market-trajectory-and). Accessed: Nov 21, 2021.

[³](#chap11.xhtml#fn3)Global Industry Analysts. “Mobile Biometrics — Global Market Trajectory & Analytics”. Research and Markets. [https://www.researchandmarkets.com/reports/5027979/mobile-biometrics-global-market-trajectory-and](https://www.researchandmarkets.com/reports/5027979/mobile-biometrics-global-market-trajectory-and). Accessed: Nov 21, 2021.

[⁴](#chap11.xhtml#fn4)“Biometric blog”, [https://www.bayometric.com/biometric-blog/](https://www.bayometric.com/biometric-blog/). Accessed: Nov 21, 2021.

[⁵](#chap11.xhtml#fn5)“Data protection in the EU.” European Commission. [https://ec.europa.eu/info/law/law-topic/data-protection/data-protection-eu\_en](https://ec.europa.eu/info/law/law-topic/data-protection/data-protection-eu_en). Accessed: Nov 21, 2021.

[⁶](#chap11.xhtml#fn6)“How many smartphones are in the world?”. Bankmycell. [https://www.bankmycell.com/blog/how-many-phones-are-in-the-world](https://www.bankmycell.com/blog/how-many-phones-are-in-the-world). Accessed: Nov 21, 2021.

[⁷](#chap11.xhtml#fn7)“DeepFaceLab is the leading software for creating deepfakes.” Github. [https://github.com/iperov/DeepFaceLab](https://github.com/iperov/DeepFaceLab). Accessed: Nov 21, 2021.

[⁸](#chap11.xhtml#fn8)“Mobile biometrics to authenticate $2 trillion of sales by 2023, driven by over 2,500% growth”. Juniper Research. [https://www.juniperresearch.com/press/press-releases/mobile-biometrics-to-authenticate-$2-trillion-of-s](https://www.juniperresearch.com/press/press-releases/mobile-biometrics-to-authenticate-$2-trillion-of-s). Accessed: Dec 18, 2021.

[⁹](#chap11.xhtml#fn9)R. Shevlin. “The 5 Hottest Technologies in Banking for 2020”. Forbes. [https://www.forbes.com/sites/ronshevlin/2020/02/03/the-5-hottest-technologies-in-banking-for-2020](https://www.forbes.com/sites/ronshevlin/2020/02/03/the-5-hottest-technologies-in-banking-for-2020). Accessed: Dec 18, 2021.

[^(10)](#chap11.xhtml#fn10)D. Clark. “Losses incurred during ATM related fraud attacks (incidents) in European countries from 2010 to 2019”. Statista. [https://www.statista.com/statistics/419739/fraud-attacks-atm-losses-in-europe/](https://www.statista.com/statistics/419739/fraud-attacks-atm-losses-in-europe/). Accessed: Dec 18, 2021.

[^(11)](#chap11.xhtml#fn11)“More than 50 years of payments experience combined with innovative technology”. Mastercard. [https://www.mastercard.us/en-us/issuers/products-and-solutions/customer-needs/consumer-solutions/cardless-atm.html](https://www.mastercard.us/en-us/issuers/products-and-solutions/customer-needs/consumer-solutions/cardless-atm.html). Accessed: Dec 18, 2021.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0012](https://doi.org/10.1142/9789811250903_0012)

Chapter 12

**DevOps: Speeding up Financial Applications Delivery to the Market**

***Jihai Zhou***

**12.1Why FinTech Needs DevOps**

Today, we are moving to a new age where all companies and every industry are becoming software companies. If software is everywhere in the world, like Marc Andreessen’s famous words in 2011^([1](#chap12.xhtml#rfn1)), the first area to be affected will be the financial industry. With the emergence of new online/mobile pay services, such as Apply Pay, Alipay, and etc., FinTech companies, whatever firm size and population, start to realize that the acceleration of new features and new applications to their customers is one of the keys to maintain a competitive advantage and earn the market share. To meet this business demand, the application development and operations teams are under huge pressure, as their application development process (coding, build, test, and release) for new features and incremental updates need to be done in shorter cycles. This is where DevOps can play an important role in the software development and deployment process for FinTech companies.

However, not all FinTech companies may have an interest in accelerated delivery. For example, rather than 10 releases daily, some companies may only need weekly or monthly release based on their business demands. In addition, from the cost aspect, failed application deployment and the relevant rollback eat up the most IT budget. Regarding this situation, DevOps can provide help on stability, security, and compliance. With continuous feedback, the quality of products is improved and maintained due to catch and fix defect early. Continuous delivery or deployment automates the development process and therefore further minimize the risk of human operating errors. By following the “shift-left” guide, there is a change on replicating production earlier in the software development lifecycle (SDLC), so small changes do not crash the whole application and this results in higher quality releases. When incidents come up, the mean time to recover the application is obviously short. In one word — fail or correct fast and continuous feedback are another key benefit of adopting DevOps. In addition, Cloud technology also help FinTech companies to save on the infrastructure costs as well as establishing robust applications due to recover disaster and scalable capacity techniques provided by the Cloud.

On this basis, DevOps can be of great help to FinTech in general. Based on the priority and depending on which kind of FinTech solutions are built, Aaron Contorer \[[1](#chap12.xhtml#rref1)\] talks about how DevOps helps FinTech into its different areas:

*   *Cryptocurrency* — Better test suite in the auto testing, separate Virtual Machines (VMs), credential management, and storage redundancy will provide a robust and secure service to minimize the risks for a cryptocurrency system to be attacked.
*   *Human-assisted and automated trading* — Auto testing and auto deployment can make sure any change will be quickly and frequently delivered to production under careful control.
*   *Asset valuation, market analysis, and research* — DevOps (such as Infrastructure as Code, monitoring, rollback process, and version control) can help to manage and maintain their large-scale database and complex data feed flow.
*   *Consumer banking and account management* — DevOps can integrate their legacy applications well to meet clients’ demands and protect from attacks.
*   *Compliance, regulation, and auditability* — Credential management, traceability, and verification will minimize the risk at production.
*   *Security and endurance against direct attack* — DevOps can do much more to defend you than many people realize and can make the most of your security budget.

There are a few leading annual technical conferences focused on DevOps in the FinTech industry, such as FINTECH: CODE and FinConDX Virtual Summit, for practitioners and experts from banks, asset management firms, and insurance companies to join and share their experiences on adopting and scaling DevOps at an enterprise level.

**12.2Introduction to DevOps**

Traditionally, during the software development lifecycle (SDLC), different groups/roles of people work individually. For example, when developers finish coding, they forward codes to testers (QA); after testing, testers forward artifacts to Operations for the release and production support. The weakness of this process is that different groups/roles of people have to wait for each other to fully complete their work, which results in a long delivery time due to inefficient collaboration and processes. This traditional way of work does not fit the rapid-change market and it requires a novel development way to quickly respond to the competitive market. On this basis, how to efficiently run the development process has become a challenge for the software development industry. Now, DevOps (Development Operations) is here to solve this problem.

The term “DevOps” was coined by Patrick Debois in 2009, and he started to run a community-based DevOpsDays conference in Ghent, Belgium since 2009 to promote the DevOps methodology. By 2020, DevOpsDays has organized more than 300 conferences in more than 80 cities around the world for people to share their DevOps experience and practices. In addition, *The Phoenix Project,* published in 2013 by Gene Kim, and *The DevOps Handbook* published in 2016, written by Gene Kim, Jez Humble, Patrick Debois and John Wills, have been considered as the must-read guide in the DevOps world.

Since 2012, the DevOps Research and Assessment (DORA) and Google Cloud have published the annual “Accelerate: State of DevOps” report to present the status and growth of DevOps across the world. The latest report \[[2](#chap12.xhtml#rref2)\] publishes the performance profile based on the assessment results — 48% of teams is ranked as high performers (in which 7% is ranked as elite performers); 37% of teams is ranked as medium performers; and only 15% of teams is ranked as low performers. The proportion of high performers has grown year by year, which identifies that the industry is continuing to improve on DevOps.

DevOps is a set of software development practice and methodology to integrate developers, testers, and operations to think alike, break down silos and share responsibility, and finally to improve collaboration and productivity by automating infrastructure and workflows, as well as measuring the development process performance. DevOps practice emphasizes on methods for more effective communication and collaboration between development, operations, testing, and quality assurance teams. The way to implement DevOps in development teams requires both a mindset change and new tools. Mindset change enables development teams to adjust their way of working through continuous feedback and continuous improvement, as well as accepting new methodologies, such as Agile. New tools are fundamental and help the team to establish new skills to manage development process in an efficient way by automating everything.

In order to delivery faster and better-quality code, a number of methodologies and new technologies are introduced in DevOps:

*   Agile changes people’s mindset and culture through small change and iterative process.
*   Continuous Integration and Continuous Delivery/Deployment (CICD) accelerates the delivery by adopting DevOps tools to automate the development process.
*   Microservice designs the application architecture into many small services for it to be able to release quickly.
*   Cloud and Container Technology further improve infrastructure efficiency, flexibility, and reduce cost.

With the growth of DevOps, some new jobs and roles on DevOps are created in the organization to drive and implement the technology transformation.

1.  *DevOps Champion or Lead* — Responsible for driving DevOps across teams in the organization and make DevOps implementation happen; work with application teams to identify necessary initiatives to bring efficiency and quality improvement; drive teams to be faster, show better performance, and set current and future targets against these initiatives.
2.  *DevOps Engineer* — Responsible for DevOps implementation and focus on DevOps tooling; help application teams to build up and maintain a continuous integration and continuous delivery or deployment (CI/CD) process; and provide a fundamental automation infrastructure for fast delivery and quality improvement.
3.  *DevOps/Agile Coach* — Train teams in the new way of working and educate teams on how DevOps practices can help development teams to deliver faster and better; keep ongoing feedback within teams and drive to get teams to continuously reflect on performance and drive out better way of working.

**12.3Agile Development**

Agile is a software development methodology based on iterative development, where requirements and solutions can evolve through the collaboration between self-organized cross-functional teams. Unlike the Waterfall methodology, which has a separated and dedicated process for teams to follow at each stage of the SDLC to delivery and release for one big project, Agile divides one big project into multiple iterative periods and includes all process of the SDLC into each iteration, which requires small delivery and release. There are several frameworks to implement the Agile methodology. The most two famous frameworks are Scrum and Kanban. They have many in common, but also have different approaches and focus.

Scrum is an Agile framework to break down the project into actions that can be completed within certain period, called sprint, which is normally two weeks or even shorter, at least no more than one month. During each sprint, several approaches are established to help teams track progress, plan and review. In addition, different roles below are defined in a team to allocate responsibilities and ensure the sprint to be executed well.

*   *Product Owner* — Represent product stakeholders, who is responsible for prioritizing product backlog and maximizing value on what the team can deliver.
*   *Scrum Master* — Responsible for facilitating scrum meetings and ensuring the team follows the scrum framework and agreed processes to delivery. Different from Project Manager or the Team Lead, the Scrum Master focuses more on process management rather than people management.
*   *Development team* — Responsible for delivering product features and updates every sprint.

A standard Scrum workflow covers the following four scrum meetings (see [Figure 12.1](#chap12.xhtml#fig12-1)).

![](images/p396.jpg)

**Figure 12.1.**Scrum framework

![](images/arr.jpg)*Sprint planning* — At the beginning of each sprint, prepare and select backlog, discuss the potential scope of work and effort, prioritize, and finally agree on a decision.

![](images/arr.jpg)*Daily Scrum (or daily standup or daily catch up)* — Every day during a sprint, the team will spend a small amount of time (i.e., 15 minutes) to update by each member on “What did you do yesterday?”, “What you plan to do today?”, and “Any blockers or problems?”

![](images/arr.jpg)*Sprint Review* — Define and present the deliverables (i.e., what has been done and what has not been done) of the current sprint to the Product Owner.

![](images/arr.jpg)*Retrospective* — At the end of a sprint; review what went well, what did not go well, and anything that could be improved during the current sprint; and identify and agree on continuous improvement actions.

The Kanban is a lean method to manage work by balancing demands with available capacity. It requires the real-time communication of capacity and full transparency of work. The Kanban is based on three basic principles: (i) visualize what you do today (workflow), (ii) limit the amount of works-in-progress (WIP), and (iii) enhance flow. The Kanban promotes continuous collaboration and encourage active, ongoing learning and improving by defining the best possible team workflow. Work items are visualized on a Kanban board to allow team members to track the state of every piece of work at any given time. While the physical board is simple and easy to be accepted by some teams, virtual boards provided by software tools (such as Jira) have more features to help the development team manage and keep track of the state of progress more efficiently. In addition, it is easy for virtual boards to keep historical data for analysis purposes.

Both Scrum and Kanban focus on releasing into production early and often, and requires high-collaborative and self-managed teams, but they are still different approaches. [Table 12.1](#chap12.xhtml#tab12-1) shows a summary of the differences between these two approaches.

**Table 12.1.**Scrum versus Kanban

 
|  || **Scrum** || **Kanban** |
| --- | --- | --- |
| Cadence || Regular fixed-length sprints (i.e., 2 weeks) || Continuous flow |
| --- | --- | --- |
| Release || At end of each sprint once approved by PO || Continuous delivery |
| Roles || Product owner (PO), scrum master, development teams || No existing roles |
| Key metrics || Velocity || Cycle time |
| Change || better not make change during sprint || can happen at any time |

![](images/p398.jpg)

**Figure 12.2.**Continuous integration and continuous delivery/continuous deployment

**12.4Continuous Integration and Continuous Delivery/Deployment (CI/CD)**

As mentioned in the previous section, Agile is a methodology focused on the process and the people to manage workflows in software development. Agile and Continuous Integration and Continuous Delivery/ Deployment (CI/CD) are related, but they describe completely different aspects of the software development. CI/CD is the natural progression of agility but it relies on automation to remove the human elements that ultimately create bottlenecks in releasing and improving software (see [Figure 12.2](#chap12.xhtml#fig12-2)).

*Continuous Integration (CI)* is a development practice that requires developers to integrate the change to the source code in the shared repository several times per day. Each commit is verified by an automated build and testing for teams. By integrating regularly, the errors and problems can be detected, and feedback is given to developers for them to fixed at the early stage.

*Continuous Delivery (CD)* is an extension of Continuous Integration to ensure the new change can be released to production as quickly as possible. Apart from the automation build and automation testing, the deployment process should also be automated to make sure that small batches are easy to troubleshoot in case of a problem. However, Continuous Delivery may still require human intervention and operations (i.e., click the button to release) when the change is approved to be released into the production.

*Continuous Deployment (CD)* is a step further of Continuous Delivery. Once the new code is committed, the change will be automatically built, tested, and deployed into the production without any human intervention. Continuous Deployment is an excellent way to accelerate the feedback loop with clients through delivering the change into the production more frequently.

CI/CD are referred to as continuous software development, which allow business to leverage automation to develop, build, test, and deploy better-quality code more rapidly, and therefore respond faster to market changes. In order to implement and execute continuous integration and continuous delivery/deployment (CI/CD), a DevOps tooling stack or tooling chains is proposed to be used at different stages of the development lifecycle to automate process.

*   Coding — source code management (SCM), code development, and code quality analysis
*   Building — automation build
*   Testing — unit test and automation testing
*   Packaging and Deployment — artifact management and automation release
*   Configuration — infrastructure as code
*   Monitoring — application performance continuous monitoring and issue analysis

**12.5DevOps Tools**

The way to implement CI/CD is to adopt DevOps tools across the whole SDLC. There are a lot of DevOps tools (open source or commercial products) available on the market. The DevOps process follows the pipeline or workflow to execute tools at each stage to automate the process or measure the development quality. In this section, we will introduce some popular and well-known DevOps tools at different stages of the DevOps process (see [Figure 12.3](#chap12.xhtml#fig12-3)), such as task management, source code management (SCM), Continuous Integration (CI), static code analysis, build, artifact management, automation testing, automation deployment, monitoring, log analysis, etc.

**12.5.1*Task/Issue Management Tools***

The most popular task management tool on the market is Jira, developed by Atlassian. It supports both Scrum and Kanban features used for Agile project management. The workflow feature at Jira provides a visible approach for people to easily manage processes. The service desk feature at Jira also provides a scheme for business and production support purpose. Jira can easily integrate with other tools (such as Github and Jenkins), especially the Atlassian products (i.e., Bitbucket and Bamboo) to display commit information and build status at the relevant task dashboard, which gives people an easy way to have all the development information located at one central location. In addition, there are a lot of plugins for Jira to be able to extend its functions, such as testing reporting.

![](images/p400.jpg)

**Figure 12.3.**The DevOps process

**12.5.2*Source Code Management Tools***

Git is an open-source distributed version control system designed for tracking source code change during the development process. Unlike other SCM tools (Subversion, Perforce and ClearCase), Git provides special features like branching (master, release, develop, and feature), convenient staging areas, and multiple workflows. There are a few popular SCM tools based on Git — Github, GitLab, and Bitbucket (previously called Stash).

Github is a web-based source code management (SCM) and version control tool. It has an open-source version to support public and limited private projects. The enterprise version has unlimited private repositories for large-scope development teams where the firm wishes to keep their repositories behind a corporate firewall. So far, Github may be the largest repository host, with more than 38 million projects (where there are more than 19.4 million open-source projects). In 2018, it was purchased by Microsoft.

Gitlab can do almost everything that Github does. The Gitlab Community is the self-hosted free version for people who like to have full control over the code base and have the resources to maintain their own servers. Gitlab’s Cloud-hosted plan allows for an unlimited number of users to collaborate on an unlimited number of public and private projects, but with limited space per repository.

Regarding the branching strategy, there are four different popular schemes:

*   *Trunk-based development* only has master and release branches. The development work is at master branch. When the code is ready for testing, the release branch is created from the master branch. The bug fix is at the release branch.
*   *Git flow* has multiple branches — master, develop, release, feature, and hotfix ([Figure 12.4](#chap12.xhtml#fig12-4)). The master branch should always be stable and the latest version of code. The develop branch is originally from the master branch and is mainly used for development purposes. The feature branch is originally from the develop branch and used for application feature or function development. When the code at the develop branch is ready for testing, then the release branch is created. After successful deployment, the release branch is merged back to the master branch. Hotfix is used for bug fix. If the bug is found before the production release, then the hotfix branch is created from the release branch; if the bug is found after the production release, then the hotfix branch is created from the master branch. As Git flow introduces many different branches for different development scenarios, it is normally used for complex development environments and large teams.
*   *Github flow* only has the master and feature branches, and therefore provide a simple development scheme. The Github flow is normally used for small changes and fast deployment scenario, in which the change and bug fix are not very different.
*   *Gitlab flow* introduces production and pre-production branches to deal with complex deployment scenarios.

![](images/p402.jpg)

**Figure 12.4.**Git flow

**12.5.3*Continuous Integration Tools***

Jenkins is the most popular open-source Continuous Integration (CI) tool or automation build server written in Java. Jenkins has a large community to provide hundreds of plugins for it to earn additional features and to be easily integrated with other tools. A Jenkins-based build farm can be easily established by connecting Jenkins’s master with multiple slaves via Secure Shell (SSH). CloudBee (Enterprise Jenkins) is a commercial extension of the open-source Jenkins and provides support at the enterprise level. CloudBee introduces an Operations Center to manage multiple Jenkins masters in a cluster way.

In 2016, Jenkins released its new version called Jenkins 2, which brought huge changes for Jenkins. The highlight of the new features provided by Jenkins 2 is “Pipeline as Code”. The pipeline is a feature to provide a visible workflow to keep tracking the progress and status of the development process. Jenkins 2 not only supported the traditional way to configure the pipeline from jobs, but also provides a coding way written in Apache Groovy to build up the development process pipeline, which is easily to be accepted by developers.

TeamCity is a commercial CI product, but it also provides a free version (TeamCity professional), which could support three build agents and up to 100 build configurations. Compared with Jenkins, TeamCity does not have a powerful “Pipeline as Code” feature, and a large number of plugins for additional functions. However, TeamCity has a nice user interface and better support for .NET development (such as MSTest, Nunit, Nuget package and deploy), and therefore is well accepted by Windows and .NET developers.

**12.5.4*Build Tools***

Ant is a Java library used for the automation build of Java applications. From many aspects, Ant is similar to “Make”, but its build files are written in XML format. The main benefit of Ant is its flexibility. However, Ant does not impose any coding conventions or project structure, which means Ant requires developers to write all the commands themselves, and this may lead to a huge XML build files which is hard to maintain.

Apache Maven is the most popular Java dependency management and automation build tool based on the concept of a Project Object Model (POM), which is based on an XML format. Compared to Ant, Maven also uses XML files but in a much more manageable way. In other words, Ant may allow for flexibility but it requires everything to be written from scratch. Maven relies on conversions and provides predefined commands. In addition, Maven has a scheme to manage the dependency, and this makes it easy for developers.

Another popular automation build tool for Java is Gradle, which is built upon the concept of Ant and Maven. However, the major difference between Maven and Gradle is that Gradle does not use XML files but instead uses a Domain Specific Language (DSL) based on Groovy for the configuration, and therefore it is preferred by developers and is well adopted in more complex codebases.

Different from Java, the most popular build tool for .NET is MSBuild, which is a platform for building .NET applications. MSbuild is also in the XML schema for a project file that controls the build configuration and process. Visual Studio uses MSBuild to load and build projects. The MSBuild can be used as a Command Prompt in Visual Studio or integrated with Continuous Integration (CI) tools, such as Jenkins.

**12.5.5*Static Code Analysis Tools***

Sonarqube is an open-source static code quality analysis tool used to provide capability to not only display the health of an application but also to highlight issues introduced. Sonarqube supports multiple languages, such as Java, C#, Javascript, XML, PHP, etc. More coding standard rules for additional languages can be added through installing extra plugins. The Quality Gate feature at Sonarqube provides a mechanism to break the build if the code quality does not meet the conditions (i.e., number of critical issues > 0). This approach guarantees that developers deliver good-quality code. Another highlight of Sonarqube is to display the code information at one dashboard, such as line of code, complexity, duplication, code quality (issues), code coverage, etc. The time machine feature displays the historical data to help the development team understand and analyze their code quality or technical debt trend. Sonarqube also provides the flexibility for developers to customize its coding standard rules or add new rules to fit the team’s situation.

FindBugs is a free static code analysis tool used to detect possible bugs in Java. Based on the impact level, errors are classified into four different levels: (i) scariest, (ii) scary, (iii) troubling, and (iv) concern. The coding standard rule set can be enriched by installing additional plugins. As FindBugs is well known for its Java code quality analysis, many plugins have been developed for it to be easily integrated with other tools, such as Jenkins, Eclipse, IntelliJ IDEA, Maven, Gradle, etc.

FXCop, also known as FxCop analyzer, is an open-source static code analysis tool produced by Microsoft and is based on the .NET Complier Platform. It runs source-code analysis during complier execution and project built, and report along with complier results. FXCop also has relevant Nuget package/plugins to be integrated with Visual Studio (IDE) and Jenkins (CI).

The most popular open-source static code quality analysis tool for C/C++ is Cppcheck, which provides unique code analysis to detect bugs, and focuses on detecting undefined behavior and dangerous coding constructs. Cppcheck supports a wide variety of static checks and aims to detect only real errors in C/C++ code. In addition, the Cppcheck community also provides a few plugins for Cppcheck to be easily integrated into other tools to trigger its execution and display its results at the dashboard, such as plugins for Jenkins, Visual Studio, etc.

**12.5.6*Artifactory Management Tools***

There are two popular artifact management products available on the market and both of them have a free version and an enterprise version: (i) Sonatype Nexus and (ii) Jfrog Artifactory. One highlight of the Sonatype Nexus is that the Nexus OSS (free version) supports Nuget (.NET artifact format) for free. However, Jfrog Artifactory supports more languages and repository types (such as C++), but only in the paid version. In addition, Jfrog Artifactory has better integration with CI tools (such as Jenkins) and artifacts can be traced back to build jobs. The Sonatype Nexus can only do the same with a plugin in the paid version. The paid version of both products supports enterprise functions, such as multiple repository management, external repo management, clustering, and high availability.

**12.5.7*Automation Testing Tools***

The unit test is a software testing approach by individual units of source code, a set of one or more modules together associated with control data, usage, and operating procedures are tested to determine whether they are fit for use. Regarding the unit testing framework, the JUnit is the most popular framework for Java development, and the NUnit is the most popular framework for all .NET languages. Both JUnit and NUnit are from the XUnit family, and they play an important role for test-drive development (TDD).

According to the “Survey on Test Automation Challenges” \[[3](#chap12.xhtml#rref3)\], Selenium is ranked first as the open-source automation testing tool for web applications, and 84% of testers have used it in their projects. Selenium is very flexible for developers or testers who have experience in coding and scripting. Users can write test scripts in many different languages, such as Java, Groovy, Python, C#, Ruby, etc., that run on multiple operating systems and web browsers.

JMeter is a free testing tool for testing loading and performance measurement. It mainly focuses on web applications, and supports many types of applications, servers, and protocols, like Web, SOAP, FTP, TCP, LDAP, SOAP, etc. The highlight of JMeter includes it being lightweight with a simple and easy-to-use interface, a replay feature on test results, powerful Test Integrated Drive Electronics (IDE), and dynamic reporting.

Cucumber is an open-source tool written in Ruby, and is designed based on behavior-driven development (BDD). It is used to perform the automated acceptance testing by running the test case that best describes the behavior of the application. It provides a single up-to-date living document that has both specification and test documentation.

**12.5.8*Automation Deployment and Configuration Tools***

Infrastructure as Code is the process to manage and provisioning infrastructure and hardware devices (such as server, database, etc.) through machine-readable files (which are coded), rather than physical configuration interactive configuration tools. The benefit of this approach is to manage and configure infrastructure in a coding way, which is easier for developers to use to configure large scopes of infrastructure devices. There are three popular open-source tools used for automation configuration and can be used for automation deployment as well.

The Puppet is a pioneering automation configuration and deployment orchestration solution for distributed application and infrastructure. The open-source Puppet is built with Ruby, and offers custom Domain Specific Languages (DSL) and Embedded Ruby (ERB) template. The Puppet uses an agent architecture, where the agent is installed at nodes and controls the configuration based on the information and commands sent from the master. Like Puppet, Chef also uses an agent architecture and a pull-based approach as well as offering configuration in a Ruby DSL.

Compared to Puppet and Chef, Ansible is designed to simplify complex orchestration and configuration management tasks. Ansible is written in Python and allows users to script in YAML. Unlike Puppet and Chef, Ansible does not requires agents on every server and offers multiple push models to send command modules to nodes via SSH that are executed sequentially. A central Ansible server is used to manage all playbooks (configuration information) and inventories (target server list), and push the configuration to be executed at the target server.

**12.5.9*Monitoring Tools***

Prometheus is a popular open-source distributed application and service monitoring tool, and is founded as the Cloud Native Computing Foundation (CNCF) project. It collects metrics from configured applications at certain intervals and displays the results at the dashboard, as well as triggering alters when the given threshold is broken. Prometheus supports multi-dimensional data model, an HTTP pull model for time series collection, as well as Pushing time series for batch jobs.

Grafana is an open-source, web-based, general-purpose dashboard, and graph composer tools. It can be used on top of a variety of different data stores, such as influxDB, graphite, and MySQL. For each data source, Grafana has a specific query editor that is customized for the features and capabilities that are included in that data source. Due to its powerful features on the graph dashboard, Grafana helps users to easily create and edit dashboards, as well as create comprehensive charts with smart axis formats.

**12.5.10*Logging Analysis Tools***

There are two popular log analysis tools: (i) ELK, an open-source combination of three tools — Elasticsearch, Logstash, and Kibana; and (ii) Splunk, which is a commercial product. Like its name, Elasticsearch is a search and analytics engine. Logstash is a server-side data processing pipeline that gathers data from multiple sources simultaneously, then transforms and sends data to Elasticsearch. Kibana is a visualization tool that displays charts and graphs. The highlight of ELK is that it provides a function to run log search, analysis, and display the results at the dashboard, and finally helps the development and operations teams do troubleshooting and issue or incident analysis.

**12.6Microservices**

Microservice (see [Figure 12.5](#chap12.xhtml#fig12-5)) is also known as the microservice architecture, which is an architecture style that structures an application as a collection of services that are highly maintainable and testable, loosely coupled, independently deployable, and self-organized around business capabilities. Due to its advantage, microservice has been extremely hot for architecture design, but it does not mean there are no drawbacks. Because of multiple small services, developing distributed system, multiple-service management, configuration, monitoring, packaging, patching, testing, and deployment has become complex. This is the reason why microservice frameworks like SpringCloud comes out.

![](images/p409.jpg)

**Figure 12.5.**The microservice architecture

The main ideas and key concept on how to successful adopt microservices can be documented as follows:

*   Microservices should be based on domain, not functionality.
*   Each microservice should be owned by a dedicated team.
*   Microservice should be independently deployable.
*   Security is something that each service should be concerned with.
*   Monitoring and logging become more distributed.

The microservice architecture enables the continuous delivery/ deployment of large and complex applications through decomposing them into different smaller services that improves modularity. Each small service is self-managed and has its own repo and CI/CD pipeline (see [Figure 12.6](#chap12.xhtml#fig12-6)). As these small services are independent of each other, the change on each small service can be released quickly into the production with the CI/CD pipeline. In addition, the small services can perfectly fit the breakdown tasks during each sprint, which help teams easily run and manage their iterative process.

![](images/p410.jpg)

**Figure 12.6.**Microservice and CI/CD

**12.7Cloud and Container Technology**

Cloud computing technology grows extremely fast and has become very mature so far. It provides the shared services which improve the resource utilization efficiency. Cloud technology covers infrastructure to platform and software applications. Users do not need to purchase, build up, and maintain themselves, but can instead rent these services based on a pay-as-you-go scheme to save costs. There are three different Cloud deployment types or models:

*Public Cloud* is the Cloud service provided and operated by third-party providers, such as AWS, Google Cloud, and Microsoft Azure. Users access the service (hardware or software owned and managed by the Cloud provider) based on a web browser.

*Private Cloud* is the Cloud infrastructure normally physically located in the organization’s on-site data centers, which are owned by and maintained on a private network by the company itself.

*Hybrid Cloud* combines both public and private Clouds, bound together by technology that allows data and applications to be shared between them. By allowing data and applications to move between the private and public Cloud, a hybrid Cloud gives businesses greater flexibility, more deployment options, and helps optimize existing infrastructure, security, and compliance.

Most of the Cloud services fall into three different categories: (i) Infrastructure-as-a-Service (IaaS), (ii) Platform-as-a-Service (PaaS), and (iii) Software-as-a-Service (SaaS). These are sometimes called the Cloud computing stack, as they build on top of one another.

*Infrastructure-as-a-Service (IaaS)* — The most basic and common Cloud computing service. Users can rent IT infrastructures (servers, VMs, storage, networks, etc.) from a Cloud provider and do not need to build up and maintain the infrastructure themselves.

*Platform-as-a-Service (PaaS)* — The service that supplies an on-demand environment for developing, testing, delivering, and managing software applications.

*Software-as-a-Service (SaaS)* — The service that provides on-demand software applications for users to connect over the Internet, usually with a web browser. With SaaS, Cloud providers host and manage the software applications and underlying infrastructure, and handle any maintenance.

Both DevOps and Cloud technology offer greater effectiveness and business impact, but DevOps focuses more on process improvement, automation, and culture change, and Cloud technology makes life easy or saves cost based on technology and services. Although they have different focuses, it is important to understand and get DevOps and Cloud technology to work together to help businesses achieve their digital transformation goals.

DevOps can also benefit from Cloud Technology. By adopting Cloud technology, infrastructure capacity will not be a blocker to limit DevOps implementation, especially for application resilience and day-time release, etc. For example, if the infrastructure resource is not enough to have hot-hot secondary architecture, development teams may have to release to the production only on the weekends, which results in slow delivery. In addition, the lack of infrastructure resource will also affect the application’s stability and finally affect the quality of production. IaaS can provide a solution to solve this problem by providing enough infrastructure at a low cost, and is dynamic and fast. In addition, SaaS and PaaS can also provide a fast and dynamic CI/CD solution for developers to focus on coding and they do not need to worry on building up and maintaining a CI/CD solution themselves. In this regard, Cloud technology not only helps DevOps teams remove its blockers but also further enhance its efficiency.

A Container is a standard unit of software that packages up codes and all its dependencies, so the application runs quickly and reliably from one development environment to another. Containers and virtual machines (VMs) have similar resource isolation and allocation benefits, but containers virtualize the operating system instead of hardware. Containers are an abstraction at the app layer that packages code and dependencies together (see [Figure 12.7](#chap12.xhtml#fig12-7)). VMs are an abstraction of the physical hardware turning one server into many servers. Both multiple Containers and VMs can run on the same machine. However, Containers share the OS kernel with other containers and each running as isolated processes in user space, while each VM includes a full copy of an operations system, the applications, necessary binaries, and libraries (where the size could be up to Gigabytes (GBs)). On this basis, Containers take up less space than VMs and can also be fast to boot, and therefore Containers are more portable and efficient. Some popular Containers and management tools are Docker, Kubernetes, etc.

![](images/p412.jpg)

**Figure 12.7.**Containerized applications

Containers solve application conflicts between different environments. Indirectly, containers bring developers and IT operations closer together, making it easier for them to collaborate effectively. Adopting the container workflow provides many customers with the DevOps continuity they have sought but previously had to implement via more complex configurations for release and build pipelines. In other words, Containers simplify the CI/CD pipelines in DevOps. The use of containerization and microservices causes new challenges in the development process and the challenges create new demands for DevOps tools.

**12.8The Challenge to Implement DevOps in FinTech**

The Internet companies (such as Google and Facebook), which has been on the rise in the recent 10 to 20 years, is easy to accept new methodologies and new technologies, as there is no legacy asset. In addition, the way to produce internet products naturally fits the Agile development way. Unlike Internet firms, financial companies are more traditional — legacy applications, waterfall process, restrict regulation, huge and complex architecture design, etc. All of this could be the blocker to slow down DevOps implementation in the financial industry.

In some traditional banks and insurance companies, there is still existing legacy applications, which needs to run on dedicated and specialized hardware and operating systems, such as mainframe, AS400, etc. Most of the DevOps tools do not support such legacy applications which are more than 20 or 30 years old. In addition, most legacy applications are designed into one big and complex architecture, and will remain unchanged for decades, so one small change may result in a big impact. In this regard, the legacy application is a challenge for both DevOps tools and microservice implementation in the financial industry.

Financial systems are normally huge and complex. Although the Agile development can be adopted to develop in a small and iterative way, the error-tolerant and experimental development cost is much high than the internet product. This is the reason why waterfall methodology is more popular for complex application development, as it may require proper, stable, and detailed architecture design and development to avoid high experiment cost.

Within the financial industry, the strict regulation, and procedures, as well as security requirement, all aim to minimize the delivery risk but block the DevOps implementation. One example is the approval process prior the production release due to strict regulation. It normally takes days or weeks to be approved by different roles or different groups of people. How to simplify the approval process to reduce the pending period time, while still follow the regulation and security requirements.

**12.9The DevOps Success Stories in Financial Industry**

In reports “DevOps Success Stories in the Financial Services Industry”, “How the Financial Industry Is Doing DevOps” and “Why Financial Services is Turning to DevOps”, several DevOps success stories in the financial industry are listed and presented \[[4](#chap12.xhtml#rref4), [5](#chap12.xhtml#rref5)\]. Some examples include:

*   *Barclays banks* started its digital transformation journey by adopting DevOps from 2015. Due to its DevOps implementation, the quality of code improved, and the complexity of code reduced, which helped development teams reduce delivery risks and improve service quality.
*   Another UK bank, *HSBC,* also made changes by being the user of Google’s Cloud Service Platform to adopt Cloud-native technology and DevOps to improve its core banking services to the clients.
*   *Capital One* is one of the early adopters for Agile and DevOps since 2011. By following the Scaled Agile Framework (SAFe), Capital One started with Agile training and slowly moved to DevOps by adopting the Continuous Delivery pipeline to automate process. By 2016, Capital One had more than 700 teams working in the Agile and DevOps way.
*   The third largest bank in the Netherlands, *ABN AMRO Bank,* started the container technology from the beginning, but then faced many challenges on compliance, governance, and security. In order to solve this problem, ABN created a team called “Stratus”, which is responsible for building up easy-to-use platforms for the development teams to quickly deliver secure and good-quality products to the business.
*   *LMAX,* a global FinTech company started with the pair programming, TDD and Continuous Integration, and later focused and invested a lot on automation testing and the best practice. LMAX also introduced quality gate at the pipeline by considering unit test coverage, cybersecurity testing, and code quality analysis at the quality gate to guarantee the delivery of good-quality software.
*   *SIX* is one of the best examples to successfully run DevOps transformation on both technology and organization change by adopting microservice, CI/CD, container, and cybersecurity. For example, SIX’s ATM network relies on the container management of microservices and automated tests.
*   *ING* is another example of how banks move to automation CI/ CD pipeline, including code analysis, unit test, static security testing, compliance, and functional and performance testing.
*   *BBVA* addressed its challenge first — inconsistent manual processes, poor automation testing, and silo delivery teams. According to the current status analysis, BBVA adopted DevOps to improve time-to-market, and application reliability by building automated delivery pipeline with automated approval criteria and behavior enforcement, virtualizing metrics, and establishing the DevOps culture.
*   *JP Morgan* provides senior management with regular updates on key metrics related to the delivery speed (release frequency) and production stability (business incident number) to gain the leadership’s buy-in and support. They also have regular communication with development teams on business change requirements and help business stakeholders as part of the DevOps process. Based on better communications between business and IT teams, this business engagement model provides a more efficient way and saves costs on remediation due to misunderstandings of the business requirements.
*   *Fidelity Investment* is also an early adopter for the Cloud and would like to modernize applications and minimize technical debt. In addition, Fidelity also had an experience to move their CI back from the development environment back to the developer’s local machine, for the developers to own their workload and engage in a culture of knowledge-sharing. The outcome of this experience showed that the deployment time is reduced from minutes to seconds, which is good for a team to deploy daily.

**12.10Case Study: DevOps Implementation in a Large Bank**

**12.10.1*Background***

Recently, IT application has become more and more important to the business in the financial industry. If applications in a bank can be delivered faster than its competitors, it will have the advantage and may affect business deals and market share. In the example of Bank A, there are thousands of IT employees available to support its global business. In order to support business in very efficient development way, both Agile and DevOps were adopted, and a DevOps program was run from 2016 to 2018 on different aspects, as follows:

*   DevOps tooling chain
*   DevOps dashboard
*   Agile training and business engagement
*   DevOps community
*   Micro service and Cloud migration
*   Team organization change

**12.10.2*DevOps Tooling Chain***

Regarding the tooling aspect, Bank A adopted DevOps tools at different stages of the SDLC and integrated them to become a DevOps tooling chain to automate the process. Most of the applications in Bank A are coded in Java, and the DevOps tooling stack is provided in [Figure 12.8](#chap12.xhtml#fig12-8). To provide a global and advanced service, Enterprise tools were considered. However, with an increasing number of teams becoming users of the DevOps tooling chain, providing a robust and fast-response service was a big challenge. The Tools used at the different stages of the SDLC in Bank A is given as follows:

![](images/p417.jpg)

**Figure 12.8.**The DevOps tooling chain for Java applications

*   Task management: Jira
*   Source code management: Github (Enterprise)
*   Continuous Integration: Jenkins (Enterprise)
*   Build: Maven
*   Code analysis: Sonarqube (Enterprise)
*   Unit test: JUnit
*   Artifact management: Nexus (Enterprise)
*   Automation testing: Selenium and Jmeter
*   Automation deployment: Ansible Tower (Enterprise)
*   Monitoring: Prometheus

**12.10.3*DevOps Dashboard***

When the development teams started to use DevOps tools, it was easy to collect data from the different tools, and then centralize, analyze, and finally display the DevOps metrics at the dashboard.

To influence the development teams’ mindset and establish DevOps culture, TV monitors were purchased and allocated next to the development teams to display the DevOps dashboard in real time from many different aspects, such as code quality, build status, testing result and status, deployment status, production monitoring, etc. The purpose of this was to help the development teams be more aware about the DevOps process through displaying the relevant data. In addition, the DevOps dashboard also provided a vision or report for the managers/leaders to easily understand what happened during the development process, evaluate the team performance, and measure the teams’ output.

**12.10.4*Microservice and Cloud Migration***

Although Bank A had adopted Agile training to improve team collaboration and DevOps tooling chain to automate the process, there are many legacy applications in which architecture design was huge and complex, and it was the blocker in achieving faster delivery. In order to solve this problem, Bank A defined two standards for both new and legacy applications. Regarding the new applications/projects, the architecture was designed in microservice way associated with CI/CD automation pipeline to quickly deliver the applications from the beginning. Unlike new applications, as the architecture of legacy applications had already been designed in complex way, it took time to gradually rebuild the legacy applications in the microservice way, piece by piece. Although microservice does provide a lot of benefit, the rebuild cost still needs to be considered to make the judgment to rebuild legacy application architecture in the microservice way or retire the legacy application.

As mentioned in the previous section, the Cloud and contain technology increase the infrastructure utilization and improve development process efficiency, Bank A also decided to migrate to the Cloud, especially the internal/private Cloud due to cybersecurity concerns. Tools available at the Cloud are considered to collaborate with the DevOps tooling chain to provide better DevOps services. After a few months, several pilot teams successfully moved their applications and development process to the Cloud environment. However, the Cloud migration was still very slow in the banking environment due to the restrictions on the regulation and cybersecurity.

**12.10.5*Agile Training and Business Engagement***

In Bank A, the proper Agile training was provided to the development teams. The Agile coach/lead accompanied the development teams to train them in Scrum and Kanban, for them to benefit from better communications, more efficient task management, and small and more frequent delivery.

As the development teams in Bank A are responsible for delivering the business requirement, most of the workload comes from the business. When DevOps is promoted across teams in Bank A, many managers found, although they are very keen on DevOps, their teams were too busy on business delivery and did not have time for IT improvement (DevOps). Furthermore, the DevOps-related work were always considered as a “low priority” task and the teams may never have a chance to implement it. On this basis, you can find that DevOps is not only about IT, but is also related to the business which is the key for further DevOps implementation.

To solve this problem, engagement between the business and development teams needs to be established. The business team needs to understand the benefits of DevOps and be happy for the development teams to invest time to run DevOps to improve development efficiency. In return, the business team will benefit from faster and better-quality delivery, as well as saving costs.

However, educating the business team to accept DevOps is even more challenging compared to educating the IT teams. One recommendation is that you may need to think like a businessman and try to convince them based on what they care most about. For example, if they are not interested in fast delivery, what about cost-savings?

**12.10.6*DevOps Community***

A DevOps community is found within Bank A and regular events are organized to influence people and gradually change people’s mindset and establish the DevOps culture in the organization. For example, internal or external experts are invited to share their DevOps experience. A DevOps committee is organized by a group of DevOps experts to produce the “DevOps Best Practice” as the knowledge database to benefit the development teams. In addition, to share more between the teams from different departments, a number of lighting talk events are organized for people to show and demonstrate their DevOps improvements for other teams to learn from. Furthermore, not only is the connection enhanced between the teams within Bank A, but the development teams are also recommended to connect with and learn from external organizations through attending external technical conferences, communities, etc.

**12.10.7*Team Organization Change***

The development team organizational structure in Bank A was very traditional. It had dedicated large development teams, testing teams, and operations teams, and therefore, there was an invisible barrier between the different teams. To have better team collaboration, the team structure was changed from the following aspects:

*   Application-based large development team was changed to multiple small service-based team called “Pod” teams, which had no more than 10 members.
*   The dedicated testing team was dismissed, and testers were allocated to the relevant Pod teams to work on automation testing.
*   The dedicated operations team was dismissed, and operations people were allocated to the relevant Pod teams to work on both application support and scripting (such as Infrastructure as code).
*   After team restructuring, although there was a small number of members (less than 10) in each Pod team, it had all the roles required (developer, tester, and operations). The final goal of the team structural change was to break the barriers between the teams for developer, tester, and operations to work together, and therefore improve on team collaboration and communication. In addition, the knowledge should be exchanged between developer, tester, and operations, for them to learn more skills and be able to partially back up each other.
*   However, in practice, as people got used to the traditional way of work, it was difficult to move to the new team structure and the challenge came from many aspects: 
    *   Developer, tester, and operations had no idea how to work together, and therefore it required training and enough time for them to get used to the new way of working.
    *   To have better communication and collaboration, each Pod team is normally designed as the local team. However, the local team cannot easily provide 24/7 support for global business applications.
    *   It took time for developer, tester, and operations to do knowledge exchange.
    *   After team restructuring, there were multiple small teams and each team had one Pod lead, which meant more people needed leadership and management skills.

Overall, compared to the technical changes (i.e., automation and micro service) and team culture changes, the team organization change is the most challenging work for DevOps. Any benefit you earn from the structural change, there is always big challenge, and it normally takes years for teams to gradually complete the change.

**12.11Summary**

DevOps is a new methodology which promotes a culture and practices for applications to be developed in a fast and good-quality way. It brings strong opportunities in the FinTech sector to develop leading edge applications which truly transforms a financial organization’s methods and successes. By adopting DevOps, FinTech companies will be able to enable culture, practice, and process for customer and company success, as well as taking the advantage during the competition in the market.

However, there are still a lot of challenges to implement DevOps in FinTech firms, such as legacy, strict regulation, waterfall process,etc. In addition, the traditional DevOps does not consider cybersecurity much, but security is the top priority in the financial industry. We will talk about DevSecOps (DevOps + Security) in next chapter to see how DevSecOps can further help FinTech companies.

**References**

[1](#chap12.xhtml#ref1).A. Contorer, “Fintech best practices: DevOps Priorities for Financial Technology Applications.” FPComplete. [https://www.fpcomplete.com/blog/fintech-best-practices-devops-priorities-for-financial-technology-applications/](https://www.fpcomplete.com/blog/fintech-best-practices-devops-priorities-for-financial-technology-applications/). Accessed: March 01, 2021.

[2](#chap12.xhtml#ref2).N. Forsgren and J. Humble, *Accelerate: State of DevOps,* IT Revolution Press, 2020.

[3](#chap12.xhtml#ref3).P. Belagatti, “DevOps Success Stories in the Financial Services Industry.” DZone. [https://dzone.com/articles/devops-success-stories-in-the-financial-services-i](https://dzone.com/articles/devops-success-stories-in-the-financial-services-i). Accessed: April 1, 2021.

[4](#chap12.xhtml#ref4).J. Miranda, “How the Financial Industry Is Doing DevOps”. InfoQ. [https://www.infoq.com/news/2017/06/does-financial-industry/](https://www.infoq.com/news/2017/06/does-financial-industry/). Accessed: January 01, 2021.

[5](#chap12.xhtml#ref5).S. Carey, “Why Financial Services is Turning to DevOps.” InfoWorld. [https://www.infoworld.com/article/3584761/why-fs-is-turning-to-devops.html](https://www.infoworld.com/article/3584761/why-fs-is-turning-to-devops.html),” Accessed: February 1, 2021.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap12.xhtml#fn1)M. Andreessen, “Why Software is Eating the World”, *The Wall Street Journal,* August 20, 2011.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0013](https://doi.org/10.1142/9789811250903_0013)

Chapter 13

**DevSecOps: Integrating Security in DevOps for Financial Applications**

***Jihai Zhou***

**13.1Why FinTech Needs DevSecOps**

In the financial industry, one of the big changes in the distribution of banking products is the transformation from primary branch-based banks to digital banks. The digital bank means the simplification of end user experience. However, it complicates security problems as it increases the number of attack vectors within the digital channels. For example, the digital transaction is transferred through the Internet which is exposed to cyberattacks. Deposit and user accounts can be also opened and closed through the Internet channel by hackers. Hackers can exploit applications’ weakness to access the personal identifiable information and use them for financial fraud and data theft. In addition, many companies may not know they are under attack until it is too late. According to the Bitdefenders’ survey, around 64% of companies are not aware of data breaches in their applications.

According to a Verizon 2020 Data Breach Investigation report, “The cyber-attack risk continues to grow every year. Application-layer attacks start to become the leading cause of data breaches from 2016 and web applications were a top cyber-attack pattern used against financial service institutions with 1509 incidents in 2019.” In addition, data security is the top concern for 70% of banks consulted during the Sixth Annual Bank Survey. In the DevSecOps Whitepaper \[[1](#chap13.xhtml#rref1)\], it predicts that the cost to the world will be more than US$6 trillion by 2021 due to cybercrime in many different forms. It also presents some real cases of breaches that have happened in recent years, such as Target, where up to 40 million credit and debit cards data were stolen in 2013, and Tesco Bank, which suffered a data breach in 2015, costing the company a total of $80 million in fines.

When financial service institutions suffer a data breach, not only losing data and money, they also damage their reputation, and destroy the confidence of their customers and investors. In order to fight against horrible cybercrime and protect companies from cyberattacks, many financial companies have heavily invested in their security departments/teams and infrastructure. According to Deloitte and the Financial Services Information Sharing and Analysis Center (FS-ISAC), banks commit 6% to 14% of their information technology (IT) budget to cybersecurity. According to research by Kaspersky, financial service organizations spend around three times more than non-banking companies. However, although there is huge amount of available budget to build up cybersecurity teams in financial companies, it is still lacking in skilled security professionals.

In this regard, cybersecurity becomes even more critical to get transactions safe and secure from potential fraudsters, and therefore it requires proper security measures in place to be fully automated across the development process. As mentioned in previous Chapter, FinTech startups, along with traditional banking and insurance institutions, have adopted Agile and DevOps to move to rapid deployment of new capabilities and services that respond to competitive markets. Their businesses benefited from continuous integration/ continuous delivery (CI/CD) to streamline and speed up the application development process, with continuous testing to ensure the quality of products. However, rapid innovation may conflict with security. Some companies focus more on the advantages of DevOps to deliver products to the market faster, and therefore drop the awareness of security as they believe security will slow down their software development process, which is identified by Gartner’s survey in 2016. In addition, many companies also face another common problem — cybersecurity is normally only considered and addressed at the end of the software development lifecycle, which may not only slow down the process, but also add additional costs due to remediation. Kevin Bocek, Chief Security Strategist for Venafi, has mentioned that “Financial services organizations use DevOps technology to deliver new features and improve customer experience in today’s hyper competitive market. However, the competitive advantage DevOps offers cannot come at the expense of security, data privacy and compliance” \[[2](#chap13.xhtml#rref2)\].

In order to provide both fast and secure software development for the business delivery, adopting DevSecOps (DevOps + Cyber Security) is becoming important in the journey for a traditional bank to move to a digital bank, as well as playing a key role in the future of all FinTech companies. DevSecOps can remove the isolation and boundaries that previously existed between security teams and development teams, and it integrates security into the full life of development process, rather than as part of a deployment checklist only. The combination of DevOps and application security addresses the need to scale security from professional AppSec teams to development teams, and without burdening developers with security decision making. However, in order to implement the real DevSecOps, application teams not only need to adopt DevSecOps technology and tools, but also need to apply the cultural transition. In the following sections, we will discuss DevSecOps in details.

**13.2From DevOps to DevSecOps**

In 2012, Gartner introduced the term “DevSecOps” (originally coined as DevOpsSec), and it started to become a hot topic at the RSA Conference in 2017. DevSecOps aims to shift left cybersecurity mindset to the development teams and makes everyone responsible for security. “Information security architects must integrate security at multiple points into DevOps workflows in a collaborative way that is largely transparent to developers, and preserves the teamwork, agility and speed of DevOps and agile development environment, delivering “DevSecOps” — Gartner \[[3](#chap13.xhtml#rref3)\].

After understanding what DevSecOps is, people may start to ask — why do we need cybersecurity in DevOps? Agile and DevOps help development teams reduce software delivery time from months to days. However, the original DevOps does not consider cybersecurity and mainly focuses on the speed and the quality. When the development teams speeds up delivery, the cybersecurity becomes the bottleneck.

[Figure 13.1](#chap13.xhtml#fig13-1) provides an example to compare three different development processes — (i) the traditional process, (ii) the DevOps process, and (iii) the DevSecOps process. When the development team is running under the traditional development process, the first stage takes three weeks for requirement gathering, architecture design, coding, build, testing, and finally it is ready to be deployed into production. Prior to the release, it takes one week for the security team to evaluate the potential risks and discover vulnerabilities in applications by running the cybersecurity assessment. When the DevOps process is adopted (such as automation, microservice, better team coordination, etc.), the development efficiency improves, and it reduces the development process time from three weeks to one week. However, there is no change for the second stage and therefore it still takes one week to complete the security assessment. Now, it is easy to understand why cybersecurity becomes the bottleneck of DevOps, especially if the teams’ DevOps level is mature. In order to break this bottleneck, the DevSecOps process was created and it aims to remove the barriers between DevOps and Security. It shifts security from reactive to proactive through identifying security issues in the early stages of the development process.

![](images/p426.jpg)

**Figure 13.1.**Traditional, DevOps, and DevSecOps processes

DevSecOps provides the strategies and technology required to build security at each stage or checkpoint of the DevOps process, for development teams to deliver better quality and secure products quicker. In order to achieve this, development teams must change the traditional way of working and start to establish new mindsets and culture that everyone is responsible for security and develop software in both DevOps and secure way. The top three benefit offered by the DevSecOps to the development team can be summarized into the following three aspects:

*   *Faster* — DevSecOps reduces time-to-market by left shifting security assessment work to the design, coding, or testing stage through automating DevSecOps tools for teams to be able to find and fix the security issues early, and finally reduce the security assessment time.
*   *Control the Risk* — DevSecOps provides baseline security criteria for vulnerability identification and remediation, to enable project teams to self-certify applications for deployment within acceptable risk criteria, and therefore reduces the overall risk of business and internally applications.
*   *Cost-saving* — DevSecOps reduces overall reliance on cybersecurity teams to manually conduct post release code and infrastructure checks, resulting in the overall reduction of remediation cost.

**13.3DevSecOps Current Status**

Since 2017, DevSecOps has become more and more popular and been started to be adopted by some early adopters. There are a number of reports to present and analyze the status of DevSecOps every year. One of popular DevSecOps reports is titled “DevSecOps Community Survey 2020” \[[4](#chap13.xhtml#rref4)\] is produced by the DevSecOps community organized by Sonatype, CloudBee. Twistlock, etc. In this report, it mainly compares the teams with DevOps Elite Practices and the teams without DevOps Practice on many different application security aspects.

Another DevSecOps report titled “DevSecOps Practices and Open Source Management in 2020” \[[5](#chap13.xhtml#rref5)\] is produced by Synopsys, who interviewed about 1,500 IT employees, and it includes 79% of developers and 21% of security engineers mainly from seven countries around the world — 65% of interviewees is from Asia (i.e., China, Japan, and Singapore); 18% is form Europe (the UK, Germany, and Finland); 17% is from the US.

In the report, based on the survey results, it shows that 33% of teams has already adopted DevSecOps practice well for their business delivery and another 30% of teams is on their way to partially or fully run DevSecOps. This is a good sign to demonstrate that many development teams are starting to be interested in DevSecOps and that the adoption of DevSecOps is rapidly growing.

Synopsys’s report also indicates that a successful DevSecOps solution entails a full security toolset, which includes static application security testing (SAST), dynamic application security testing (DAST), interactive application security testing (IAST), software composition analysis (SCA), runtime application self-protection (RASP), and penetration testing tools to fully address security issues at the early stages of the software development life cycle (SDLC).

SAST, DAST, and IAST are the top DevSecOps tools and have been well adopted by development teams. The SCA tool, also known as the free open-source security (FOSS) tool, analyzes the application by detecting the open-source software (such as third-party libraries, dependencies, licenses, etc.) It produces an inventory or Bill of Materials (BOM) to keep all open-source information in the codebase (such as versions and potential vulnerabilities). Comprehensive SCA solutions monitor the BOM to provide clients with early notifications of new vulnerabilities, and even deliver upgrades or patch guides. In addition, with the increasing of Cloud and Container technology adoption, the container security will become more and more important when teams start to move to the Cloud.

Regarding the response to the discovered critical open-source vulnerability, the survey found that more than half of the teams need to spend two to three weeks to apply for an open-source patch to fix the vulnerability, which means that the risk (that can be attacked by a hacker) will stay in the application for two to three weeks. Worse than that, a quarter of the teams ignore the risks in their applications up to a month, and only 16% of the teams fix the vulnerability within a week. In this regard, most of the development teams do not respond to the critical vulnerability fast enough, and therefore keep their applications at risk. The developer may not have the right mindset to be aware about vulnerabilities, may not have enough knowledge to fix the vulnerability, may not have the automation solution to speed up, or may have to go through complex and long processes to deal with the security issues. Any of these can result in slow response to the discovered critical vulnerabilities and leave their applications at potential risk to be attacked.

**13.4The Challenge to Implement DevSecOps**

Although DevSecOps provides a novel methodology to solve the problems between DevOps and cybersecurity, and also make security everyone’s job during the development process, the journey to migrate from DevOps to DevSecOps is not easy and requires cultural or mindset change, new governance, workflows, and process to be established and new technology to be adopted. Here, the challenge to implement DevSecOps falls into two main areas, as follows.

**13.4.1*Technical Challenges***

Software development is a complex process, which may use different programming languages, large source code repositories, and a mess of open-source libraries and packages. DevSecOps needs to be able to support all of them. Unfortunately, so far, there are not many DevSecOps tools available on the market. In addition, many DevSecOps tools are not mature enough and still have weaknesses, which can slow down the promotion and wide adoption of DevSecOps tools. More details will be discussed in following section.

**13.4.2*People/Culture Challenges***

Compared to the technical challenges, the most challenge comes from people. Security is often an afterthought and has poor relation in the software development life cycle, so people normally do not have enough awareness about cybersecurity. In addition, many developers believe cybersecurity is the job of a dedicated cybersecurity department or team and that DevSecOps is additional work.

In 2018, Threat Stack \[[6](#chap13.xhtml#rref6)\] produced a survey to demonstrate that 52% of companies have cut security budget to meet a business deadline or objective. This report also examines that the main reason why DevSecOps has not become a reality in most organizations is due to the lack of support from senior management, who are keen on business delivery rather than cybersecurity. Without the buy-in from senior management to promote the DevSecOps from top to bottom, it will be difficult and slow for teams to widely adopt DevSecOps.

**13.5DevSecOps Best Practice**

In order to overcome the aforementioned challenges to implement DevSecOps and finally establish the DevSecOps culture in the company, it is essential for DevSecOps’ best practices to be adopted by considering novel technology, new processes, and a mindset change.

**13.5.1*Technology Innovation***

Technology enables DevSecOps processes to be properly executed and makes sure that security flaws are detected at the early stages rather than the end of the software development lifecycle or even on the customer side.

*Automate security — Automate security testing in the continuous delivery*

In order to remove the bottleneck in the DevOps process caused by the cybersecurity assessment, automation is the essential solution. Automate security source-code scanning and binary scanning through the CI/CD pipeline by running static and dynamic security analysis, and therefore speed up secure code delivery. Integrating security tools at Integrated Drive Electronics (IDE) will further help developers detect and fix vulnerabilities at the coding stage, which is earlier than the Continuous Integration stage. In addition, pre/post-deployment auditing and scanning allows businesses to fully understand their risk postures.

*Security Dashboard — Visualize technical security debt*  
The security issues or vulnerabilities discovered by security testing tools need to be reported, displayed at dashboard, and be visible to everyone. The security dashboard can be considered as feedback to developers to keep tracking continuous improvement on technical security debt during each iterative development process. The relevant security issue analysis and study tutorials could also help developers fix vulnerabilities and reduce technical security debt in a more efficient way. Furthermore, the visible security dashboard will help the DevSecOps culture to be established at both the managers (security vision and awareness) and the developers (easily track and fix security issue in their daily job) sides in the development teams.

*Security gate — Integrate risk controls in development pipelines*  
A security gate is required to be added into the development process at different stages as the checkpoint to control the risks. A number of conditions could be set up at the security gate for a certain security quality threshold (for example, zero critical vulnerability). If the scanning result does not pass the conditions at the security gate, the process will be blocked until the developers fix the relevant vulnerabilities to pass the condition. Security gate provides a scheme to guarantee developers deliver good-quality and secure code with minimum vulnerability risk to the production.

*Security as Code*

Code-driven automation configuration management tools (such as Chef, Ansible, and Puppet) can easily set up standardized configurations across hundreds of servers using common templates, and therefore minimize the risk that hackers can exploit one unpatched server. On this basis, cybersecurity should be considered when producing Chef cookbooks, Ansible playbooks, and Puppet manifests to ensure the infrastructure configuration management automation solution is secure enough.

*New Security Process*

One of DevSecOps final goals is to create repeatable ways of working to ensure the transparency of security. For example, a short, feedback-driven and holistic model-based security loop will need to be created to quickly identify problems, react swiftly, and lead to process improvement and culture change. In addition, the mechanisms and procedures for dealing with security problems will also need to be established. For example, how to deal with security issues discovered from the source code, open-source package, and etc.; or how to manage the security issues like the software issues or business tasks.

**13.5.2*Culture and Mindset Change***

It is very challenging to change the way of working that people are used to, and therefore the culture and mindset changes are not easy, and it normally takes years to achieve. There are many different approaches to influence people and finally get them to accept a new way of working.

*Ongoing training and education*

Good training ensures that standards are implemented correctly, and developers earn required knowledge faster. Security training could be run through many different channels, such as online training courses, tools, tutorials, and consultancy, and the learning media needs to be flexible and tailored to help developers easily understand more about the hacker’s behaviors, different vulnerabilities, and the solutions to fix them.

*DevSecOps Champion*

The DevSecOps champion is a new role and requires qualified professional experience on both DevOps and cybersecurity. The DevSecOps champion is responsible for DevSecOps implementation through coordinating and connecting development teams and cybersecurity teams, automating the DevSecOps tools at the CI/CD pipeline, tracking security issues, and finally helping teams move from DevOps to DevSecOps.

*Business Engagement*

Similar to DevOps, business is the stakeholder to drive DevSecOps. On this basis, the business needs to understand the value of DevSecOps, and finally provide fully support to run DevSecOps transformation.

*Security exercises and events*

Organizing security events, such as security coding competition, security talks, security games, etc., will gradually change people’s mindsets and build up a DevSecOps culture in the development teams.

**13.6DevSecOps Tools**

The main purpose of DevSecOps tools is to help the development teams discover and visualize the security vulnerabilities at the different stages of the SDLC. The application security tools fall into the following categories:

*   Static Application Security Testing (SAST) Tools
*   Dynamic Application Security Testing (DAST) Tools
*   Interactive Application Security Testing (IAST) Tools
*   Software Composition Analysis (SCA) Tools

**13.6.1*Static Application Security Testing (SAST) Tools***

Based on recent statistics, more than 50% of security vulnerabilities are from coding. Developers are normally more focused on business function, so they always forget to develop in a secure way and are also lacking in cybersecurity knowledge, which will result in the potential risk or vulnerabilities in the source code. In order to minimize the risk from the beginning, a security testing scheme is required at the source code level.

Static application security testing (SAST) tool, also known as the “white box security testing” tool, is a set of technology designed to analyze the application source code, byte code and binaries for coding, and design conditions that are indicative of security vulnerabilities. SAST solutions also ensures conformance to coding guidelines and standards without executing the underlying code, and therefore analyze an application from the “inside-out” in a non-running state. The following are some advantages and disadvantages of SAST ([Figure 13.2](#chap13.xhtml#fig13-2)):

![](images/p434.jpg)

**Figure 13.2.**SAST 10-dimensional radar

*Advantages:*

*   Accurately lock down the location of codes which result in the vulnerability.
*   The principle is easy to understand and accepted by developers.

*Disadvantages:*

*   Poor accuracy and high false positive, so you will have to spend extra resources to verify the result.
*   Scanning speed becomes slow with the increase of codes.

Overall, SAST is easily understand and can mark the source issue to help developers easily fix the problem. However, high false positives, which causes additional cost, is the main issue that can slow down the wide adoption of SAST.

On the market, there are several popular SAST commercial products — Checkmarx, Fortify, IBM Appscan, etc. Checkmarx is a source code analysis solution that provides the tools for identifying, tracking, and repairing technical and logical flaws in the source code, such as security vulnerabilities, compliance issues, and business logic problems. It supports a vast number of programming languages and frameworks (i.e., Java, JavaScript, .NET, ASP, C/C++, PHP, Spring, Node.js) and could be easily integrated into the CI pipeline and connect to Source Control Management (SCM) to scan source code on check-in/schedule to automate the vulnerability scanning process. IBM AppScan is another example of a SAST tool which can run at a source code level to detect possible security vulnerabilities, such as those published by the OWASP Top 10, i.e., SQL injection, XSS, etc.

**13.6.2*Dynamic Application Security Testing (SCA) Tools***

Dynamic Application Security Testing (DAST), also known as black box testing (i.e., testing is from the outside in), is designed to detect conditions indicative of a security vulnerability in an application in its running state. On this basis, the DAST may be called “behavioral testing”, in that the problems are not specifically linked to a code module but instead it happened during use. The DAST has been considered as one of the main application security technology and tools for a while, and is mainly used before releasing to the production environment.

![](images/p436.jpg)

**Figure 13.3.**DAST 10-dimensional radar

The DAST ([Figure 13.3](#chap13.xhtml#fig13-3)) is good at discovering external visible issues and vulnerabilities, and it is easy to run by only providing the URL. DAST is not reply on any languages or platforms. Compared with the SAST, the scanning result is more accurate and there is no need to spend much effort to verify. However, the downside of DAST is its heavy reliance on experts to write the security case, making it difficult to scale. In addition, it cannot lock down the location where the vulnerability comes from. Due to its “attack behavioral”, it may introduce “dirty data” to the testing environment.

Regarding popular DAST tools available on the market — IBM AppScan, AWVS, and Web Inspect are all commercial DAST products, and OWASP ZAP is an open-source web security tool provided by the OWASP community and is maintained by volunteers. OWASP ZAP is sufficient and simple to use, and it helps development teams automatically discover vulnerabilities in the web applications while teams are developing and testing applications. You only need to input the URL address and click on the “Attack” button, which will start and retrieve the results in a few minutes. In the “Alerts” section, each individual vulnerability that the OWASP ZAP detected is displayed, along with its name, URL address, risk level, reliability, and parameter. In addition, it also displays a possible solution to the problem to help developers remove any risks for the web application. Overall, the OWASP ZAP is an advanced open-source tool for running penetration tests to discover risks and vulnerabilities in your web applications.

In order to automate the DAST process, the OWASP ZAP can be integrated with Jenkins (see [Figure 13.4](#chap13.xhtml#fig13-4)). Firstly, a Jenkins OWASP ZAP plugin needs to be installed at Jenkins instance. Next, configure the plugin at Jenkins “configure system” section, such as the host address and port. Once the configuration is completed, a build job needs to be created and the relevant configuration information should be provided. Once the job is set up, the Jenkins will be able to atomically trigger the OWASP ZAP to run a penetration test for the web application. Finally, the testing results are produced and feedback is provided to the users at Jenkins dashboard.

**13.6.3*Interactive Application Security Testing (IAST) Tools***

IAST (interactive application security testing) is an emerging technology to analyze applications for security vulnerabilities while the app is running by an automation test, a human tester, or any activity “interacting” with the application functionality. It reports vulnerabilities in real time, which means it does not add any extra time to your CI/CD pipeline. IAST works inside the application, which makes it different from both the SAST and DAST. This type of testing also does not test the entire application or codebase, but only whatever is exercised by the functional test.

![](images/p437.jpg)

**Figure 13.4.**OWASP ZAP is auto by Jenkins to run penetration test for web applications

![](images/p438.jpg)

**Figure 13.5.**IAST 10-dimensional radar

The design of the IAST is to combine the advantages of both the SAST and DAST ([Figure 13.5](#chap13.xhtml#fig13-5)). The IAST installs an agent in an application and performs all its analysis in real time to analyze the entire application, such as all your code, HTTP requests and responses, control and data flow information, configuration information, libraries, frameworks, etc. Access to such a large amount of information allows the IAST engine to produce more accurate results than the SAST or DAST.

There are a few IAST products available on the market. Contrast Security is an example of a IAST tool which is a passive way of assessing the security posture of running application. It is for teams with fully automated testing capabilities within the CI pipelines. The development of this solution requires the integration of an agent with the application being assessed. Once this has been setup, the results will be fed back to the management server as the application is being used.

![](images/p439.jpg)

**Figure 13.6.**The comparison between SAST, DAST, and IAST

[Figure 13.6](#chap13.xhtml#fig13-6) provides a comparison between SAST, DAST, and IAST. [Table 13.1](#chap13.xhtml#tab13-1) below gives more details for SAST, DAST, and IAST.

**13.6.4*Software Composition Analysis Tools***

Free and open-source software allows users and developers to edit, modify, or reuse the software’s source code. This gives developers the opportunity to develop software more efficiently. As free and open-source software are normally developed and shared by third parties, there are potential security risks, and therefore developers often download and use unknown vulnerable open-source components and frameworks.

Software Composition Analysis (SCA) is a technique to verify the potential vulnerabilities from third-party libraries, frameworks, plugins, and components used in your application. In other words, all of the code, which are not produced by you and your team, is to be considered by SCA tools. Different from DAST and IAST, SCA tools do not run the security scanning within the application while the application is running. Instead, SCA tools analyze the list of dependencies, cross reference them against their list of known-vulnerable dependencies, and then report the matching dependencies as the finding.

**Table 13.1.**Comparison of SAST, DAST, and IAST

![](images/p440.jpg)

In 2020, the DevSecOps Community survey \[[4](#chap13.xhtml#rref4)\] identified that the open-source security risk expands quickly as the breach that can be attributed to a vulnerability in an open-source component or dependency increased more than 50% from 2017 to 2018. Although the open-source component related breaches continue to drop since 2018, it still occurs very often.

There are several SCA products available on the market. Both the Sonatype IQ server and Jforg X-ray are commercial products, and the OWASP Dependency-Check is the free SCA tool provided by the OWASP community. Dependency-Check (see [Figure 13.7](#chap13.xhtml#fig13-7)) attempts to detect publicly disclosed vulnerabilities contained within a project’s dependencies. The core engine contains a series of analyzers that inspects the project dependencies and collect pieces of information about the dependencies. It does this by determining if there is a Common Platform Enumeration (CPE) identifier for a given dependency. If the vulnerability is discovered, it will generate a report link to the associated Common Vulnerabilities and Exposures (CVE) entries.

In order to automate the security issues scanning, Dependency-Check can be integrated with Jenkins to be triggered automatically to produce the result. Firstly, a Jenkins OWASP Dependency-check plugin needs to be installed at Jenkins instance as well as its relevant dependencies. Next, configure the Dependency-check plugin at the Jenkins “configure system” section. Once the configuration is completed, a build job needs to be created for Jenkins to be able to atomically trigger the OWASP Dependency-check to run an open-source vulnerability scanning. Finally, the testing results are produced as a HTML file and also displayed.

![](images/p441.jpg)

**Figure 13.7.**OWASP dependency-check

**13.7Case Study: DevSecOps Implementation in a Bank**

In previous sections, we have discussed how important DevSecOps is to FinTech companies and also presented DevSecOps in detail, such as its current status, challenges, best practices, tools, etc. After understanding DevSecOps, you may be more interest in how to implement DevSecOps in FinTech companies and what needs to be done to achieve this. In this section, we will consider one of large global banks — let us call it Bank B — and use its DevSecOps transformation program as the case study to demonstrate how to implement DevSecOps, and finally earn the benefits from DevSecOps for development teams as well as establishing a DevSecOps culture and mindset.

**13.7.1*Background***

Bank B has run a firm-level DevOps program for two years since 2016. It invested a lot on tooling to automate the process and Agile training to change people’s mindset. “Double release frequency and Half business incidents” is used to measure the outcome of application teams who have adopted DevOps. After the 2-year DevOps program, the overall DevOps maturity of development teams was improved to an expected level. Although there are still some legacy applications which are not easy to adopt DevOps, most application teams have improved during the DevOps transformation to speed up their delivery and develop better quality products as well as saving on cost, which benefits the business a lot for them to be more competitive in the financial market.

After the improvements on business delivery speed and business product quality due to the DevOps adoption, as the top-level requirement in the bank, cybersecurity become next hot topic for Bank B to keep leading on technology to further support its business. By considering this, a DevSecOps program was proposed and it kicked off at the end of 2018.

**13.7.2*DevSecOps Implementation and Operating Models***

Prior to running the DevSecOps program, the first step is to be clear on what needs to be done and how to do it. In order to achieve this, a DevSecOps implementation model and a DevSecOps Operating model are developed.

The DevSecOps implementation model (see [Figure 13.8](#chap13.xhtml#fig13-8)) identifies what needs to be done to achieve the DevSecOps program final goal, which is to establish the DevSecOps culture and mindset.

*   The first step is to have the capability to discover vulnerabilities from applications by adopting DevSecOps tools, which need to be integrated into the CI/CD pipeline to automate the process and also be able to visualize the vulnerability scanning results at dashboard or notify users as the reporting purpose.
*   The second step is to provide training for the developers to have enough skills to fix the vulnerabilities.
*   After introducing DevSecOps tools and providing training to the development teams, the final goal of the DevSecOps program is to get everyone to have the DevSecOps mindset and establish DevSecOps culture in the team. In addition, each development team is expected to have at least one “security expert” who has advanced application security skills to be able to help the teams to fix tough vulnerabilities and train other team members.

![](images/p443.jpg)

**Figure 13.8.**DevSecOps implementation model

After understanding what needs to be done and the goals of DevSecOps program, the DevSecOps operating model (see [Figure 13.9](#chap13.xhtml#fig13-9)) provides a solution on how to execute the DevSecOps implementation. It defines the responsibilities of the different roles as follows:

*DevSecOps Champion:*

*   Lead the DevSecOps program and is responsible for promoting the DevSecOps culture and help development teams establish the DevSecOps mindset.
*   Connect development teams and cybersecurity teams.
*   Collect feedback from the development teams and report to cyber-security teams or experts for them to provide technical/training solutions.

![](images/p444.jpg)

**Figure 13.9.**DevSecOps operating model

*Development teams:*

*   Integrate DevSecOps tools into the CI/CD pipeline to automate processes and visualize security scanning results at dashboards.
*   Take DevSecOps training to earn enough application security knowledge to have enough skills to fix vulnerabilities.
*   Use DevSecOps tools and knowledge in practical projects and their daily work to gradually change their mindset and establish the DevSecOps culture in the team.

*Cybersecurity Team:*

*   Provide support on DevSecOps tools.
*   Provide support on application security training.
*   Provide consultancy service if needed.

**13.7.3*Integrate DevSecOps Tools into CI/CD Pipelines***

After the evaluation, the security department decided to purchase a few numbers of commercial products as the DevSecOps tooling solution, such as Checkmarx (SAST tool), Sonatype IQ server (SCA tool), and Contrast Security (IAST). After successfully setting up the tools for the pilot teams, the next step is to integrate the tools into the CI/ CD pipeline to automate their security scanning execution. The scanning results and discovered vulnerabilities need to be displayed at the dashboard. If needed, the security rules inside the DevSecOps tools could be customized based on the team’s situations and demands.

In order to integrate the DevSecOps tools into the CI/CD pipeline, the first step is to install the relevant plugin at a CI server to connect the DevSecOps tooling server and the CI server. Here, we take Checkmarx and Jenkins as an example. Form the Jenkins dashboard (see [Figure 13.10](#chap13.xhtml#fig13-10)), click “Manage Jenkins” and go to “Manage Plugins” section. Once the “Plugin Manager” screen is displayed, select the “Available” tab and select the “Checkmarx Plugin” box. Click “install without restart” or “Download now and install after restart” and Jenkins will automatically install the plugin. After successfully installing the Checkmarx plugin at Jenkins server, you need to complete the Checkmarx configuration at Jenkins “Configuration System”.

![](images/p446.jpg)

**Figure 13.10.**Manage Jenkins Dashboard

![](images/p446-1.jpg)

**Figure 13.11.**Checkmarx scan configuration

Once all installation and configuration works are done, the next step is to create and configure a Jenkins job. There are two ways to configure a job at Jenkins to automate Checkmarx vulnerability scanning (see [Figure 13.11](#chap13.xhtml#fig13-11)). One solution is to go through the traditional configuration way by filling a form to create a job. From the “Jenkins Dashboard”, select a “job” and click Configure. Once the job Configuration is displayed, scroll down to “Build” section, click “Add build step” and select “Execute Checkmarx Scan”. Once the Execute Check Scan is displayed, fill below form by inputting the required information for Checkmarx server URL, Credentials, source code project/location, and other parameters.

After successfully running the Checkmarx scanning, the result will be displayed at both the Checkmarx dashboard and Jenkins Dashboard, where the vulnerabilities are classified into different categories, such as High, Medium, and Low.

**13.7.4*DevSecOps Training***

The main purpose in adopting DevSecOps tools is to help teams to discover vulnerabilities from the applications. However, tools cannot help the teams fix the security issues and the development teams should have enough capability to fix the vulnerabilities themselves. In order to achieve this, relevant training is essential as part of the DevSecOps program.

Some tools have already included study tutorials as part of their features to guide users when they find vulnerabilities and proposes on how to fix them. This kind of study material provides a practical and simple approach to educate developers. However, it may not cover enough numbers of vulnerabilities for users to understand.

Different from study tutorial in tools, online training courses provide a proper way to educate development teams on the overall knowledge of cybersecurity. However, people may feel bored when they take online training courses. In order to solve this problem, the security department purchased one online training platform which is based on an attacking story to guide the developers to learn the security knowledge in a practical way.

To establish the DevSecOps culture, a number of security coding competition events were organized. These events made it fun for the developers to write secure code, and measure and improve their security coding skills in a competitive and engaging environment. In addition, these events also provided opportunities for the development teams to evaluate their security maturity level with regards to secure development technique and practices.

**13.7.5*DevSecOps Maturity Model***

After introducing the DevSecOps tools to discover and visualize vulnerabilities from applications and providing training for the development teams to have enough skills to fix vulnerabilities, how can you measure the DevSecOps level achieved by the development teams? In addition, how can development teams/business benefit from the DevSecOps practices? The DevSecOps maturity model is born to answer these questions.

In the DevSecOps maturity model ([Figure 13.12](#chap13.xhtml#fig13-12)), there are five different levels. Several parameters are used to measure the application security capability of development teams from different angles. For example, how long to fix high-level vulnerability; the trend of vulnerability historical data; does everyone in the team take the minimum 2-hour training course, etc. [Figure 13.12](#chap13.xhtml#fig13-12) provides a simple example to measure and define the different DevSecOps levels based on the amount of time spent on training courses and the relevant skills needed to be achieved.

If a team would like to be evaluated and granted as the mature DevSecOps team, it needs to meet the following two conditions:

*   All team members need to pass Level One at least.
*   At least one member in the team has to achieve Level Three or above.

![](images/p448.jpg)

**Figure 13.12.**DevSecOps maturity model

This means that all team members should have the basic DevSecOps skills. For example, all team members need to be aware of application security while coding to minimize the risks from the source. In addition, all team members should be able to fix simple vulnerabilities. Another condition means there should be at least one “security expert” in the team to have advanced application security skills to help team members fix tough vulnerabilities and train other team members. If both these conditions are meet, the development team will be granted as the mature “DevSecOps team”.

Once the team passes the DevSecOps maturity assessment and becomes the matured DevSecOps team, the team will be awarded an exception from the security department, and it means that the mandatory security assessment process (prior to the release to the production) will be simplified, and therefore the delivery time will be reduced due to shorter security assessment time. In other words, if the application security has been run well at the early stages of the SDLC, then the same work does not need to be done again at the end of the SDLC.

After half a year of experiments in a few pilot teams, in August 2019, one pilot application team passed the DevSecOps maturity assessment and became the first matured DevSecOps team. Due to the success of DevSecOps program, the DevSecOps was defined as one of top 2020 strategies in Bank B for more applications teams to widely adopt.

**13.8Summary**

In the financial industry, the data is very sensitive, regulated, and highly proprietary. Financial service institutions continue to be the primary target of hackers, and therefore cybersecurity plays a key role in establishing a FinTech company of the future. DevOps is a revolution for development teams to develop software in a fast and good-quality way as well as saving on cost. However, rapid delivery conflicts with security in FinTech companies. Based on a study Venafi conducted in November 2016 \[[2](#chap13.xhtml#rref2)\] on the cryptographic security practices and attitudes of DevOps teams, although many financial services organizations have strong cybersecurity polices in their production environments, they often fail to enforce the same vital measures in their DevOps practices.

As one enhancement version of DevOps, DevSecOps (DevOps + Cyber Security) is a new methodology to combine DevOps with cybersecurity, and provides a solution to develop software and deliver business in both a fast and secure way. In this chapter, we mainly discussed the movement from DevOps to DevSecOps, as well as the DevSecOps challenges and best practices. Regarding the technology of DevSecOps, we mainly focused on DevSecOps tools, such as SAAT, IAST, DAST, and FOSS. Finally, we take one case from a global bank to demonstrate how to successfully implement DevSecOps into a real development environment.

**References**

[1](#chap13.xhtml#ref1).F. Raynaud, *DevSecOps Whitepaper,* DevSecCon, 2018.

[2](#chap13.xhtml#ref2).K. Bocek, “Venafi DevOps Study: Mature vs Adopting Programs,” Venafi, 2016. Accessed: April 1, 2021. \[Online\] Available: [https://www.venafi.com/research/mature-devops-study](https://www.venafi.com/research/mature-devops-study).

[3](#chap13.xhtml#ref3).N. MacDonald and I. Head, “DevSecOps: How to Seamlessly Integrate Security Into DevOps,” Gartner, 2016. Accessed: March 1, 2021. \[Online\]. Available: [https://www.gartner.com/en/documents/3463417/devsecops-how-to-seamlessly-integrate-security-into-devo](https://www.gartner.com/en/documents/3463417/devsecops-how-to-seamlessly-integrate-security-into-devo).

[4](#chap13.xhtml#ref4).“DevSecOps Community Survey 2020.” Sonatype. [https://www.sonatype.com/2020survey](https://www.sonatype.com/2020survey). Accessed: February 1, 2021.

[5](#chap13.xhtml#ref5).“DevSecOps Practices and Open Source Management in 2020,” Synopsys, 2020. Accessed: April 1, 2021. \[Online\]. Available: [https://www.synopsys.com/software-integrity/resources/analyst-reports/devsecops-practices-open-source-management.html](https://www.synopsys.com/software-integrity/resources/analyst-reports/devsecops-practices-open-source-management.html).

[6](#chap13.xhtml#ref6).“52% of Companies Sacrifice Cybersecurity for Speed — Webinar Recap,” Threat Stack, 2018. Accessed: March 1, 2021. \[Online\]. Available: [https://www.threatstack.com/blog/52-of-companies-sacrifice-cybersecurity-for-speed-webinar-recap](https://www.threatstack.com/blog/52-of-companies-sacrifice-cybersecurity-for-speed-webinar-recap).

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0014](https://doi.org/10.1142/9789811250903_0014)

Chapter 14

**MLOps in the Financial Industry: Philosophy, Practices, and Tools**

***Jun Xu***

**14.1The ML Lifecycle and Complexity**

As the concept of data-driven and tech-driven become slogans in most Financial Institutions (FIs), Artificial Intelligence (AI), Machine Learning (ML), and Data Science (DS) turn to one of the strongest forces to change the lifecycle of products internally. In other words, there is an increased demand to manage and track the ML lifecycle experimentations that could be deployed and drive outcomes.

Traditionally, through the entire software development lifecycle (SDLC), different groups of people work independently. For example, after finishing the software development, developers forward it to quality assurance (QA) testers, who in turn will forward the package to Operations for release and production support. As different groups of people have to wait on each other to fully complete their work, this process needs a long delivery time due to inefficient collaboration. Therefore, given the rapid movement in the market, there is a strong need to develop a much faster response to the market needs, and achieve agile product delivery.

In the real world, the ML lifecycle is a complex procedure, as illustrated in [Figure 14.1](#chap14.xhtml#fig14-1). The ML code of data science is only a small fraction of the ML lifecycle in production, and the majority of the lifecyle are related to engineering components (see [Figure 14.2](#chap14.xhtml#fig14-2) as Google indicated \[[1](#chap14.xhtml#rref1)\]), such as feature engineering and model operations. In fact, many engineering related pain points exist in the design, development, testing, deployment, and maintenance phases in ML lifecycle.

![](images/p452.jpg)

**Figure 14.1.**Major components in the ML lifecycle

![](images/p452-1.jpg)

**Figure 14.2.**ML code is a small fraction of the ML system

Firstly, the functional roles (see [Table 14.8](#chap14.xhtml#tab14-8) in the Appendix) are often distributed across different departments, and collaborations are limited. Negotiations across functions could cause delays in many cases. Furthermore, staff from different functions do not share the same mindsets and understanding. [Figure 14.3](#chap14.xhtml#fig14-3) shows a typical interaction between the different roles during the ML lifecycle. Developers and testers often take different views and perspectives. Data scientists pay more attention to data outliers, concept drift, and bias, and use that as the basis to build the model. However, testers may focus on the risks so that things do not go seriously wrong. This may lead to a scenario where a developer builds an armored vest, but the tester shoots the legs. In addition, a good data scientist skilled in ML algorithms and mathematical models may be not a good software engineer, as he may not be experienced in writing an end-to-end application. Furthermore, an operational staff responsible for software management in production may not understand AI and DS models, which then results in delays in deployment, misunderstanding, and misinterpreting of models.

![](images/p453.jpg)

**Figure 14.3.**Interactions among the different roles

The expertise mismatch always leads to this type of “myth” — a data scientist spends one month to develop a model; while until the end of the 10th month, the model appears in production; and the business end-users start to use it one year later. A survey shows that 87% of ML projects never go live,^([1](#chap14.xhtml#fn1)) mainly due to the complexity mentioned earlier. Enterprise ML development is slow and hard to standardize and scale when attached with too many tools and frameworks. These factors often lead to delays in the process, friction between teams, and wasted resources.

Secondly, the nature of ML development is generally continuous and iterative. Nothing ever stands still — new data, algorithm, libraries, and frameworks impact model performance continuously, and thus change the way to test, validate, and monitor.

Thirdly, the internal governance processes are often isolated from each other, which is usually manual and inefficient. In particular, due to the restricted regulations of FIs, the data and model validation and governance procedures are usually bureaucratic, manual, and slow. In many companies, there is no dedicated ML QA team with automated tools. Besides, there are some special requirements for ML development, e.g., production data may be used in the development environments; developers from the IT team may read the unmarked business data to understand its actual meaning; the model needs frequent retraining to keep its performance, etc.

Fourth, the dependencies of the AI production are generally complex in not only people, techniques, and tools, but also data change and business requirement shifts or increase. For example, some of the complex models (e.g., deep neural networks) have high computational complexity with a long time to train, which drives the high demands for accelerators, such as GPUs, TPUs, and FPGAs. Furthermore, a large effort often goes into wrangling the data and searching for the best set of features from the raw data for the best modeling. However, there are often lacks of a proper automated pipeline. At the same time, ML models shall be scalable, e.g., the models can move from small-scale to large-scale without pain in deployment and maintenance.

Last but not least, there are higher demands from external customers and more restricted requirements from regulators. We can see more new regulations and practices implemented in this area, e.g., AI ethics (see [Chapter 4](#chap4.xhtml)). The model assets shall not hide in the dark. All the models are well kept and become visible in the organization. For example, in risk applications, customers need to have clear-cut reasons for how they were adversely impacted by a decision, e.g., a credit card or a loan application.

In this regard, building an efficient ML lifecycle process becomes a challenge for the industry. Now DevOps (see [Chapter 12](#chap12.xhtml)) is here to solve this problem. In particular, the integration of DevOps and ML generates a new concept named MLOps (see [Figure 14.4](#chap14.xhtml#fig14-4)).

![](images/p455.jpg)

**Figure 14.4.**Integration into MLOps

**14.1.1*Characteristics***

The MLOps generally shall exhibit some special characteristics, such as Reproducibility, Auditability (accountability), Validation, Automation, Observability, Collaboration, and Scalability, as listed in [Table 14.1](#chap14.xhtml#tab14-1). For example, reproducibility is essential for fault tolerance, iterative filtration, and proper auditing of ML models. It needs to illuminate the source of variation in (i) model architecture; (ii) hyperparameters; (iii) initialization methods, e.g., layers weights (random initialization/gradient); (iv) shuffling of datasets; (v) training strategy, e.g., epic and error tolerance; (vi) ML/DL frameworks and libraries; (vii) CPU settings, e.g., multi-threading; and (viii) GPU settings, e.g., floating point, mixed precision.

Note that the concept of MLOps shall be agnostic to the ML framework, programming language, platform, and infrastructure. However, the actual implementation may be specific. As best practice, MLOps shall have a clear business objective with a ML target at the beginning, a validated high-quality dataset, a closely collaborative team (see [Table 14.8](#chap14.xhtml#tab14-8) in the Appendix) with efficient communication and complementary skills, a right development environment for ML experimentation, and reproduction using pipelines.

**Table 14.1.**Characteristics of MLOps

![](images/p456.jpg)

**14.1.2*Benefits***

With those characteristics implemented, a MLOps platform can develop and deploy ML products faster and easier in a reusable or reproducible manner, and more often:

*   Centralize feature or model tracking, versioning, and monitoring
*   Integrate different technologies, e.g., different types of ML/DL platforms, model formats, algorithm components, etc.
*   Reduce friction between science and engineering, and enhance collaboration between various roles, e.g., data science and IT/Ops teams
*   Minimize bias and improve explainability, e.g., the XAI components can be embedded into the framework
*   Mitigate risks, e.g., automate the auditable pipeline
*   Compare model quality and performance in a well-organized and efficient way
*   Move towards standardization in the field and enable reproductivity
*   Support continuous learning with the Continuous Integration/ Continuous Delivery (CI/CD) pipeline
*   Scale the ML model and system by swiftly and seamlessly converting the true potential of ML into the existing or innovative business processes and systems across the organization.

For example, risks in the production environments come from many aspects — the model may provide an unexpected prediction result; the performance may downgrade over time; the computational resource may be insufficient due to model complexity; or the model may be unavailable due to logic imperfection. With MLOps, the model is continuously monitored to detect exceptions in a real-time manner and thus the issues can be fixed in time (semi-)automatically. [Figure 14.5](#chap14.xhtml#fig14-5) illustrates the typical components in a simplified flow.

**14.2MLOps Concepts**

To achieve these benefits, we need to clarify some fundamental concepts, which may be different from the general software development \[[2](#chap14.xhtml#rref2), [3](#chap14.xhtml#rref3)\].

![](images/p458.jpg)

**Figure 14.5.**MLOps flow

**14.2.1*Metadata***

Metadata is an essence for the MLOps characteristics, e.g., Auditability and Reproducibility. It is “data that provides information about other data, i.e., data about data.”^([2](#chap14.xhtml#fn2)) In a ML lifecycle, besides the metadata of data, we also need to know:

*   What data did you train on?
*   How did you transform/exclude outliers?
*   What are the data statistical properties via exploratory data analysis (EDA)?
*   How did you transform the data for training?
*   What are the training results?
*   What kind of fairness tests have you completed?
*   Did anything change between code and production?
*   How are those results compared with previous results?
*   Which version was seen by a customer?
*   How to roll back to the previous version?
*   What model did you actually serve (to this person)? Etc.

Hence, there are three main types of metadata:

![](images/p459.jpg)

**Figure 14.6.**Feature store

1.  The metadata about the training, testing, or verification data and feature, as well as data serving (batch or streaming). An extended concept is DataOps, introduced in 2014 by IBM, which attempts to provide ready-to-use business data quickly, focusing on data quality and metadata management \[[2](#chap14.xhtml#rref2)\]. Another concept is feature store, viewed as an additional layer above the raw data (see [Figure 14.6](#chap14.xhtml#fig14-6)) to store and manage ML feature data.
2.  The metadata about the trained model, e.g., model code, training history, version, configuration, parameters, etc. A model registry shall be used to manage that information.
3.  The metadata about the operations, e.g., automated workflows, operational environments, deployment, outcome, exceptions, etc.

All those metadata shall be linked together to maintain their connection and lineage.

**14.2.2*Governance***

Data governance, model governance, and process governance are the three types of governances that need to be conducted:

1.  Data governance considers data availability, usability, integrity, security, and privacy under the internal data standard and external regulatory requirements. The goal is to ensure that data is organized, managed, and used properly. Strong governance policy can assure the appropriate usage of data for all business stakeholders, encourage data sharing, and generally leads to more accurate models. It goes across DataOps and MLOps.
2.  Model governance, e.g., code reviews and questionnaires, model performance, mode ethics, sign-offs before release, etc. MLOps can deliver rich ML experimentations when it is applied to artifacts on a massive scale. It may also allow snapshots of pipelines to be taken to analyze critical times. Logging facilities and audit trails of MLOps may also be applied to report and maintain compliance. Robust governance mechanisms and monitoring processes for models in production can help to maintain their accuracy consistently. Note that the automated model retrain and redeployment in the CD pipeline may have conflicts with some existing software governance policies, which motivates some potential changes, e.g., how to switch between old and new model during redeployment, how to coexist with multiple models, how to automate the retrain within the governance framework, etc.
3.  Process governance ensures all governance concerns have been addressed for each point of the ML lifecycle, and the necessary records have been fully and accurately kept. It focuses on formulizing the steps and processes in ML lifecycle. Some key steps shall be carefully reviewed and documented with supporting materials.

This governance procedure is usually tedious. However, with DevOps, the process becomes more efficient with automation. For example, automated monitoring tools can provide prompt feedback on data drift and model change, so that recalibration can be quickly adopted. In another sense, flexible automation in the DevOps pipeline requires standardization. That cannot happen with a single innovation. It also requires collective alignment, which takes time.

**14.2.3*People***

As shown in [Figure 14.3](#chap14.xhtml#fig14-3), there are many roles in the ML lifecycle (i.e., more roles than the general software development). Although each role has its “clear” job scope, it is usually required to understand more in the sphere of MLOps. However, due to the increasing system complexity, that becomes difficult to achieve. For example, not all data scientists have a DevOps background and always follow best practices, although the latter definitely brings more efficiency and effectiveness.

[Table 14.8](#chap14.xhtml#tab14-8) in the Appendix shows the general scope of some common roles in the ML production lifecycle \[[2](#chap14.xhtml#rref2)\]. Depending on the requirements for their job, the job scope of each role varies. For example, a ML engineer must straddle the multiple disciplines of Data Architecture and Engineering, Data Science and Statistics, and DevOps or Software Engineering in some startups, while the scope for their counterparts at large organizations could be much narrower.

At the same time, we can see that many roles have overlap on knowledge base (see [Figure 14.7](#chap14.xhtml#fig14-7)), and not all roles are required for a ML product delivery. For example, when developing and deploying in a public Cloud, a ML architect’s duty can be covered by a ML engineer, because the IT architecture is mostly maintained by the service providers in that scenario. If the ML engineer’s software development skills are good enough, there is no need to involve another software engineer to optimize the software architecture and code.

![](images/p461.jpg)

**Figure 14.7.**Knowledge domain for different roles

[Figure 14.8](#chap14.xhtml#fig14-8) gives a rough radar chart of the four roles and their skills scales, for example:

*   Data Engineers focus on the data lifecycle with more sophisticated technical and software skills on data processing.
*   Data Scientists are typically trained to be strong on mathematics and ML algorithms, with some domain knowledge.
*   ML Engineers are usually good at Computer Science, experienced in software engineering, and have some ML background.
*   Data Analysts spend more time on understanding the business requirements from the data point of view, and interpret data insights to business partners.
*   More role analyses are available in [Table 14.8](#chap14.xhtml#tab14-8) in the Appendix.

![](images/p462.jpg)

**Figure 14.8.**Skills difference among four roles

There may be many overlaps between these four roles, but it could be argued that a Data Scientist can take on the job responsibilities of a ML Engineer, a Data Analyst, and a Data Engineer at the same time, but not the other way. In this chapter, our view is that it is the team’s responsibility to collect, store, analyze, and present data for values. The team members need to reach a consensus on their duties and each role has its own contributions and importance. One key point is to ensure that management has all the information available for aligned decision-making, and the ML products can be delivered to the market in an efficient manner.

**14.2.4*CI/CD***

CI/CD is a key concept in the DevOps of software engineering (see [Chapter 12](#chap12.xhtml) and \[[4](#chap14.xhtml#rref4), [5](#chap14.xhtml#rref5)\]). Usually, the CI/CD process utilizes pipelines, which are triggered whenever code is changed (e.g., a git push or merge), to automatically build software assets, run tests, and deploy compiled packages.

However, the general software CI/CD pipelines are very different from the ML Pipelines (see [Table 14.2](#chap14.xhtml#tab14-2)). Besides the general actions in response to code changes, the ML pipelines are often operated upon (trigger) request or schedule due to model and data changes, as well as environment and configuration changes. On the other hand, CI components have the capability to test and validate data schemas, data, and models in MLOps, and CD components support the model deployment and the final model serving (possibly together with an application). Sometimes, another term, continuous testing (CT), is used to refer to the automatic model retraining and refinement inside the original CI/CD framework.

**14.2.5*Comparison***

MLOps workflows leverage DevOps principles, and can be applied in ML operations. For example, data or model versioning in MLOps is an additional requirement besides the code versioning in general DevOps. Model reproducibility is entirely different from software reuse, as the former needs tuning based on scenarios and data. In addition, reproducibility shall be implemented for both scheduled and on-demand tasks as the models decay over time partially due to data drift and concept drift.

**Table 14.2.**Comparisons between CI and CD

 
|  || **Continuous integration** || **Continuous delivery** |
| --- | --- | --- |
| Stages || ML development terms and workflow || ML operations (deployment, monitoring, maintenance, diagnosis) terms and workflow (sometimes, it may also include CI) |
| --- | --- | --- |
| Goal || Produce a packaged artifact that is ready to deploy onto a server or machine || Safely and repeatedly deliver artifacts into a production environment |
| General Actions || Develop, merge conflicts, manage code, check code integrity, check libraries/packages version, review code, test code (unit test/integration test), check security || Releasing, deploying, and monitoring applications |
| ML specific Actions || Check data/metadata/schema integrity, test and validate model (UAT/Staging, routine feature engineering); continuous training (CT) || Monitor model performance; trigger model re-train |

Besides MLOps, there are some other concepts derived from DevOps with unique features. DataOps workflows are built based on similar principles, e.g., collaboration and automation, as data management workflows. These workflows can eliminate silos originating at the data level. ModelOps covers ML experimentation. Here, DataOps and ModelOps are viewed as a part of MLOps, although some literature narrow MLOps as ModelOps. [Figure 14.9](#chap14.xhtml#fig14-9) illustrates the links among DataOps, ModelOps, and DevOps, which forms the MLOps flow to integrate and reuse the existing IT resources. GitOps is a specific MLOps with Git as the central component to complete the CI/ CD actions via Git requests, e.g., pull and merge. [Table 14.3](#chap14.xhtml#tab14-3) compares the differences among DevOps, DataOps, and MLOps.

![](images/p465.jpg)

**Figure 14.9.**A relation among DataOps, DevOps, and ModelOps into MLOps

**Table 14.3.**Comparison of DevOps, DataOps, and MLOps

![](images/p465-1.jpg)

Another concept, DevSecOps (see [Chapter 13](#chap13.xhtml)), unifies development, security, and operations principles into one unified framework. The workflow is usually automated with a continuous feedback loop. This ensures developers to devote their time on critical tasks and continually improve and secure the code. This idea can be also integrated into MLOps, as the ML data and models may be vulnerable to some attacks if the code security and model robustness are not sufficient (see [Chapter 3](#chap3.xhtml)). The combination of MLOps and Security (MLSecOps) can be used to prevent vulnerabilities from entering ML projects at the beginning.

The current MLOps is dominated by the model-centric approach. In particular, the ML experimentation almost focuses on the modeling selection and hyperparameter tuning and model validation. However, some researchers argue that the data-centric approach may be more nature for the future MLOps. The general aphorisms “garbage in, garbage out” and “data scientists spent about 80% of time on cleaning data” illustrate that data is actually one of the most important components in the ML lifecycle. It coincides with Andrew Ng’s statement, “Data is food for AI”.^([3](#chap14.xhtml#fn3)) The model-centric approach separates the ML flatforms from critical data pipelines and production environments, such that MLOps actions usually spread across several different platforms. As the data-centric approach attempts to get the best performance out of a “fixed” model, the data pipeline and model pipeline shall be seamlessly integrated. That means that the data and ML platforms with pipeline tools shall be redesigned and redeveloped to meet the new integration requirements.

**14.3MLOps Tools and Platforms**

Efforts to resolve MLOps challenges can be traced back to the time when people attempted to integrate some (open-source) ML and DevOps tools into a platform development. The AI (and ML) tool landscape is complex, with different tools specializing in different niches and, in some cases, there are competing tools approaching similar problems in different ways. [Table 14.4](#chap14.xhtml#tab14-4) shows some commonly used tools which can be used to build a specific MLOps platform.^([4](#chap14.xhtml#fn4)) We can find a more detailed landscape from Linux Foundation’s AI project for a categorized list of tools.^([5](#chap14.xhtml#fn5))

**Table 14.4.**AI/ML tool chains

 
| **Functionality** || **Tools (candidate)** |
| --- | --- |
| Data || Versioning: DVC, Pachyderm, DoltVersioning with time-travel queries and incremental pulling: Delta Lake, Apache Hudi, Apache IcebergLabelling: Labelbox, Scale, Prodigy, DiffgramValidation: TFX data validation, Deequ, Apache Beam, PanderaDatabase: Mysql, HBase, PostgreSQL, etc.Storage: AWS S3, Ceph, NFS, etc. |
| --- | --- |
| Feature store || Hopsworks, Feast, AWS feature store, Tecton, etc. |
| ML framework || Sklearn, Tensorflow, keras, pytorch, mxnet, etc. |
| IDE/workbench || colab, deepnote, coun, etc.Jupyter, Pycharm, visual code, spyder |
| Hyperparameter tuner/AutoML || Katib, Keras Tuner, Optuna, RayTune, Hyperas, SIGOPT, etc. H2O, DataRobot, etc. |
| Explainability || Ailibi, XAI, SHAP, LIME |
| SerializationSerializing, optimizing, || ONNX, joblib, openViNO, TensorRT, etc. |
| Model analysis || Google What-If tool |
| Version control and management || Source code: Github, bitbucket, gitee  
Model: ModelDB, DVC, Pachyderm, Snorkel |
| Orchestration ServingEndpoints, serving, || ML Experiment Management: ModelChimp, Randopt, ModelDB, Forge, Lore, Datmo, Studio ML, Domino, Sacred, MLFlow, PolyaxonOrchestration: Mesos, Airflow, Kubernetes, AWS ECS, KubeflowServing: Serving: Seldon, KFServing, TFServing |
| Deployment cloud || GCP, AWS, Azure, Heroku, paperspace, floydHub, etc. |
| Monitoring || Elasticsearch, Kibana, Prometheus, Sentry, Grafana, FluentBit, Datadog, Tensorflow board, hydrosphere.io, superwise.ai, etc. |
| SaaS || GCP AI Platform, AWS SageMaker, Azure ML Studio, Algorithmia, Determined AI, Databricks, Seldon IO, Daitaku DSS, Paperspace, H2O AI, Peltarion, FLOYD, Dotscience, Domino AI, Polyaxon, Weights & Biases, Spell, Gradient, Stack ML, Comet, Valohai, Neptune AI, Verta, etc. |

**Table 14.5.**Comparison of MLOps platform

![](images/p468.jpg)

As shown in [Tables 14.4](#chap14.xhtml#tab14-4) and [14.5](#chap14.xhtml#tab14-5), there are many components and platforms available for MLOps. However, most of them are half-baked solutions, and built on open-source technologies. Major Cloud service providers, e.g., AWS, Azure, and GCP, offer their SaaS MLOps platforms, and some startups work with the major players to provide complementary functionalities, such as Azure Databricks and Hopsworks feature store. To find a suitable solution for your company, it requires a deep understanding of knowledge from different domains as shown in [Figures 14.7](#chap14.xhtml#fig14-7) and [14.8](#chap14.xhtml#fig14-8). For in-house development using open-source tools, [Figure 14.10](#chap14.xhtml#fig14-10) shows the popularity of some MLOps and orchestration tools.

**14.4MLOps Implementation**

For FIs with strong technical teams, they may develop their customized MLOps platforms based on some popular open-source tools. For those who are interested in outsourcing and off-the-shelf products, they may use SaaS-based or the enterprise version of MLOps platforms. For example, the development team can use the open-source version of Git, Jupyterlab, MLflow, and Kubeflow to build a MLOps framework by themselves, or use AWS or Databricks’ AI platform directly.

[Figure 14.11](#chap14.xhtml#fig14-11) lists some major components (not all) to make a smooth MLOps for enterprises. For example, a unified portal for MLOps can be built to describe all the necessary steps and provision all the environments with full integration of agile development tools.

A new project must be registered in the “Project” management portal first, which is handled by the project owner or project manager with all the necessary information, e.g., title, business, objective, team members, fund, etc. Depending on the nature of the project, e.g., PoC, MVP, Prod, the items required are different. Users may search for similar cases in previous records as reference; or use “Marketplace” to engage with skilled teams. A Jira task list can be generated automatically based on the project nature with compulsory (regulatory or compliance) and complementary items. To make this happen, approval tasks need to be associated with the default person-in-charge via “Governance”.

![](images/p469.jpg)

**Figure 14.10.**Star history of MLOps platforms^([6](#chap14.xhtml#fn6))

![](images/p470.jpg)

**Figure 14.11.**Major components for a smooth MLOps

The provision components, e.g., Cloud VM, pipeline (orchestration), containers, and workbench, shall be under proper access control and governance. For example, the resource usages in Cloud and environment settings in containers shall have both cost and risk considerations. Workbench from some commercial software is expensive, and a rotative usage could be an efficient solution. See [Figure 14.12](#chap14.xhtml#fig14-12) for an illustration of the connection among the components.

Note that all data, feature, model, project, source code, and other artifacts within a project are connected to each other via API and/or platform plug-ins, manual scripts, and input, therefore, ML experimentation reproduction and auditing in pipeline becomes possible. For example, the model registry, similar to project management, contains all the necessary information on model artifacts, and these ML artifacts need to be organized in a graph network format.

Pipeline automation (CI/CD orchestration) is the spine of MLOps. Most IT departments of FIs have their own tools such as Jenkins and Control-M. Although some ML platforms have their built-in pipeline tools, e.g., Azure pipeline or Airflow in Hopsworks, these tools still need to be integrated with the FIs’ existing tools, as most of the governance procedures have already been embedded in the existing tools.

![](images/p471.jpg)

**Figure 14.12**Connections among the components

In this section, we provide two simplified but typical configurations to implement MLOps in a certain degree. Based on the different scenarios and requirements, the MLOps may not cover all aspects mentioned earlier.

**14.4.1*A Case Study Based on MLflow***

14.4.1.1*Introduction*

The MLflow is an open-source tool developed by Databricks to manage the ML lifecycle, e.g., ML experimentation, model registry, model reproducibility, and deployment. MLflow currently offers four major components as shown in [Table 14.6](#chap14.xhtml#tab14-6).

MLflow is agnostic to the ML library/framework and programming language, since all functions are accessible through CLI and REST API via multiple-languages, e.g., a Python API, R API, and Java API.

**Table 14.6.**MLflow components

 
| **Components** || **Explanation** |
| --- | --- |
| MLflow Tracking || APIs to record and query ML experiments, such as code, data, model, configuration, and results, via an interactive UI |
| --- | --- |
| MLflow projects || Package ML and system code in a format (from any ML library) for reproducibility on any platform such as Docker, GCP, Apache Spark, Azure ML and AWS SageMaker |
| MLflow models || Deploy ML models in various serving environments |
| MLflow Model registry || Store, annotate, discover, and (collaboratively) manage models in a central repository |

14.4.1.2*Scenario*

A bank intends to automate the ATM replenishment schedule via ML, e.g., when and how much to refill the ATMs. The main objective is to reduce the number of replenishments while maintaining the availability of cash. The main challenge is that a large number of models have to be built within a limited time, as there are more than 5,000 ATMs with different properties, e.g., location and capacity, and each ATM has its own ML prediction model. If we follow the traditional approach to build the models one by one, it is obviously inefficient and hard to achieve the goal in time.

14.4.1.3*Implementation*

A simplified pipeline is illustrated using MLflow and some other tools.

1.  This problem is essentially a ML regression problem which predicts the cash withdrawal pattern for each ATM. By calculating the remaining cash inside ATM, we can decide when the ATM will run out of cash.^([7](#chap14.xhtml#fn7)) The prediction is conducted in an hourly frequency.
2.  The developers’ IDEs are Jupyterlab^([8](#chap14.xhtml#fn8)) and Pycharm configured to the Github server.
3.  The raw data is extracted from the ATM core network into a database for every five minutes. A scheduler gets the data update and feeds it into the data processing server. A pre-processing function based on Pandas handles the potential data issues, e.g., missing data and logic errors. As some featured data is from external sources, e.g., the event and the weather, there is a table maintaining that information via a web interface. All these processes can be handled by a data engineering pipeline.
4.  For the feature engineering, data scientists may process it in Feature Store’s or the Databricks’ workbench. The features can be versioned inside Feature Store.^([9](#chap14.xhtml#fn9)) For the initial model building, data scientists may select some typical models, e.g., ARIMAS, LightGBM, Extra tree, LSTM, AutoEncode, etc., as the model candidates. Optuna is used as the hyperparameter tuner for the models. In order to reduce the computational cost to tune the model for every ATM, some typical ATM usage scenarios are identified according to EDA first.^([10](#chap14.xhtml#fn10)) Then the tuning procedure is only applied to the typical scenarios with selected samples. Both MLflow’s built-in functions and customized Python scripts are used inside the flow to record artifacts. The training results are stored in the MLflow tracking server, from where we can select the best algorithm or model candidate for each scenario. Once the tuning procedure for one scenario is done, the tuned model structures will be applied to the ATMs in the same group, unless some event triggers happen. The ML experimentation is refined by ML engineers as a pipeline.
5.  MLflow’s serving function can be used to generate the RESTful endpoint. However, it is generally a one-model-one-API, which may not suit this case. Instead, it can be used in the testing phase with small group of ATMs. In the production phase, an internal function is coded to load the model in batch for prediction.
6.  A Django-based web service is used as the user interface for operators to get the prediction information and some reports for replenishments. A background performance monitoring function is implemented to find the model performance downgrade and data drift, which can automatically trigger a model retraining procedure using the ML experimentation pipeline for the particular ATMs based on the pre-define control rules.^([11](#chap14.xhtml#fn11))

[Figure 14.13](#chap14.xhtml#fig14-13) shows an illustration of MLOps based on MLflow.

**14.4.2*A Case Study Based on Kubeflow + Github***

14.4.2.1*Introduction*

Kubeflow was originally developed by Google and released in 2018 as an open-source initiative for AI/ML applications that use Tensorflow on top of Kubernetes to minimize MLOps effort. Google has been using TFX (Tensorflow Extended)-based pipeline to deploy ML models in production over Kubernetes-based infrastructure. Nowadays, Kubeflow has been extended to other modern AI/ML frameworks e.g., PyTorch, MXNet, and Chainer, which allows developers to quickly create, train, and tune ML models within Kubernetes for dynamic resource provisioning. Kubeflow helps improve deployment, portability, and management of AI/ML models, as shown in [Figure 14.14](#chap14.xhtml#fig14-14).

[Figure 14.15](#chap14.xhtml#fig14-15) shows an illustration of the Kubeflow architecture with its major components. As an “open” structure, it may accept more functional items into its realm.

![](images/p475.jpg)

**Figure 14.13.**MLOps based on MLflow

![](images/p476.jpg)

**Figure 14.14.**The Kubeflow characteristics

![](images/p476-1.jpg)

**Figure 14.15.**The Kubeflow Architecture

14.4.2.2*Scenario*

We continue to use the ATM cash flow forecasting example earlier, but expand the deployment from one single market to the global market. The IT infrastructure varies by market; hence, we need to develop an efficient approach to make it happen within a limited time.

14.4.2.3*Implementation*

Kubernetes has several different variants, e.g., Google Kubernetes Engine (GKE),^([12](#chap14.xhtml#fn12)) Amazon Elastic Kubernetes Service (EKS),^([13](#chap14.xhtml#fn13)) and Microsoft Azure Kubernetes Service (AKS).^([14](#chap14.xhtml#fn14)) Therefore, users can choose their corresponding Cloud platforms with a specific toolkit; or use your on-premise settings with the original Kubernetes, or even a local Minikube cluster.

Although the Kubeflow is powerful enough to contain many tools we list in [Table 14.4](#chap14.xhtml#tab14-4), we only consider a simplified case with mainly Kubeflow and Gitlab. A sample procedure is listed as follows:

1.  The data scientist develops the source code to train the ML model based on the features derived from the historical data in a targeted development environment (usually Jupyter lab).
2.  The platform or some specific codes record the artifacts for each training as a run in an experiment.
3.  The data scientist queries the ML experiments for logged metrics from all the runs. If the metrics do not meet the desired criteria, loop back to Step 1 and iterate to refine the model.
4.  The data scientist or ML engineer may formalize the criteria and the thresholds into a test (pipeline) code. The features may be stored in Feature Store (if any) with the corresponding processing code and setting.
5.  Once a satisfactory run is found, the data scientist persists the model and registers it in the model registry. A scoring script of the pipeline shall be developed too.
6.  The data scientist or ML engineer formalizes the ML experimentation code and develops the source code for inference phases of the model.
7.  The data scientist or ML engineer commits the code to her/his own branch, submits a Pull/Merge Request with change descriptions, and then requests the merge into the (master) branch of the main repository. The request may come with an automated build and test; sometimes, it also comes with code quality and security check in a pipeline.
8.  A nominated reviewer or approver (e.g., a Senior Data Scientist/ ML Engineer) will review the code and model change (along with automated building (if any) and testing output), and comment on and provide feedback on the change. They may approve it for merging if all conditions are met eventually.
9.  The successful merge (or a new release) will trigger the deployment of the new code to Kubeflow in the CI/CD platform, i.e. a pipeline will be executed, or probably on a schedule. This usually happens in Development, or User Acceptance Testing (UAT) environments.
10.  New model artifacts possibly will be generated (e.g., configuration files, evaluation metrics, model distributions, etc.), and copied to a central repository (or separated model registry, git, etc.) Sometimes, it may use the data scientist’s trained model stored in any artifact repository directly for computationally intensive cases.
11.  The pipeline will automatically update the model information in the corresponding configuration in the repository, commit the change, and create a merge request so that the release version includes all changes.
12.  A nominated reviewer or approver (e.g., a Lead Data Scientist or Head of Data Science) will evaluate the model to ensure that the model satisfies all the requirements for deployment (e.g., performance, risks, ethics, etc.)
13.  The merge approval triggers another CD deployment to the UAT, staging, or production environment. The “Inference” application (links and models) will be updated. Usually, before the first production deployment, a UAT is required. It needs the business shareholder’s approval with feedback from subject domain experts (SMEs). The production re-deployment may or may not require a UAT.
14.  A monitoring and diagnosis pipeline maintained by the DevOps engineer will be executed after the ML is running in the production environments. Criteria for model decommissioning and model retrain shall be defined so that events will trigger the corresponding notification and pipeline to handle the difficult situations.

Note that major Cloud providers, such as GCP, Azure, AWS, and Aliyun, have their own pipelines too. For example, Azure MLOps enables a closer collaboration of teams and improves model lifecycle with faster development and deployment, and better monitoring, validating, and governance. Azure MLOps is able to reproduce a model with advanced tracking of all artifacts, such as datasets, features, configurations, and codes under advanced governance and management. It uses CI/CD to efficiently build and deploy models with autoscaling.

**14.5State of the Art: Not One-Size-Fits-All**

The MLOps is essential for the modern ML lifecycle, due to the collaborative nature between business stakeholders and various development roles, the complexity of ML lifecycle actions, challenges in data processing, restricted governance policies on data and model, time-consuming ML artifacts management, and the scalability requirement for ML serving, etc. More and more FIs are expected to adopt MLOps for their efficient and effective AI strategy. Based on the trend identified by Gartner, the MLOps market size is projected to grow to nearly US$4 billion by 2025.^([15](#chap14.xhtml#fn15))

A good MLOps solution might leverage existing Cloud ML platforms and tools, such as Amazon SageMaker, Microsoft Azure, and GCP, to expedite and simplify the ML production process, for humans-in-the-loop critical decision-making. Organizations shall take advantages of matured and democratized APIs, e.g., speech recognition, translation, and face recognition model, for modernized FinTech innovation.

However, due to multiple factors such as the company size, project nature, data volume, and developer skills, there is no one-size-fits-all solution. For example, the developers may encounter many different situations during the ML lifecycle, e.g., some may need high performance of real-time processing, but others may only require batch processing; some models may be too big to fit into the current infrastructure; old predictions are “throwaway”; some systems may need explainability, but others may require sustainability. As the saying goes, there are a thousand Hamlets in a thousand people’s eyes. The MLOps platform may be also different, e.g., the components in the ML lifecycle can be different, and some workflows may be interchangeable. The following lists some general considerations of MLOps, for example:

1.  Establish clear business objectives, which can be mapped to ML metrics.
2.  Ensure open communication and collaboration between ML roles; a skill-level overlap is encouraged so that team members can understand and support each other.
3.  Setup strategical MLOps toolkit and smooth CI/CD orchestration with containerization to automate some actions, accelerate the delivery, scale the deployment, and enable proactive monitoring. 
    1.  Automate data extraction, model (re-)train, testing, (re-) deployment, and monitoring into an end-to-end solution as visible as possible for a collaborative team and a scalable delivery.
    2.  Make ML production auditable and reproducible by storing all model training related artifacts (e.g., versioning data, parameters, and metadata).

[Table 14.7](#chap14.xhtml#tab14-7) summarizes some practices for the actions of three main assets in MLOps — (i) data (feature), (ii) model, and (iii) code.^([16](#chap14.xhtml#fn16))

**Table 14.7.**A summary of MLOps practices

![](images/p481.jpg)

![](images/p482.jpg)

![](images/p483.jpg)

**14.7Appendix: The Different Roles in MLOps**

The ML lifecycle is usually more complex than general software development, which involves more roles, e.g., Data Scientist, ML Engineer, ML Architect, etc \[[2](#chap14.xhtml#rref2)\].

**Table 14.8.**The different roles in MLOps \[[2](#chap14.xhtml#rref2)\]

 
| **Role** || **General scope** || **Roles in MLOps** |
| --- | --- | --- |
| Subject Matter Expert (SME) or Business owners || 

*   Provide business problem statement, objectives, or goals around of ML project
*   Continually validate the model output and ensure its performance aligns with or resolves the business need

 || 

*   Easy to explain model output in business terms with the help from the data scientist
*   Easy to feedback performance mismatch and exceptions with business expectations

 |
| --- | --- | --- |
| Data Scientist || 

*   Undertake exploratory data analysis
*   Build models and algorithms that address the business problem brought by SMEs
*   Deliver proper operationalizable models in the production environment using production data.
*   Assess model quality (of both training and testing and live) in tandem with SMEs to ensure they meet business requirements
*   Information (data/model) visualization
*   Similar roles — research scientist, applied scientist

 || 

*   Ability to investigate data pipelines of each model to make quick assessments and adjustments regardless of who originally built the model.
*   Ability to develop tests to determine the quality of deployed models and to make continual improvements.
*   Performance visibility and explainability of all deployed models

 |
| Business/Data Analyst || 

*   Understand the business requirements from the data point of view
*   Collect and interpret data
*   Identify data trends and patterns
*   Data visualization and reporting in statistical sense
*   Extension — Data Expert

 || 

*   Visibility into the business flow and data flow
*   Ability to provide data/program-level abstract of business logics

 |
| Data Engineer || 

*   Design data extraction, transformation, and loading (ETL) of data (or sometimes ELT)
*   Use and optimize (and possibly build) the infrastructure required for optimal ETL/ELT
*   Develop, construct, test, maintain, and process large dataset
*   Recommend ways to improve data reliability, efficiency, and quality; and sometimes implement them
*   Manage the entire data lifecycle and prepare the data to power ML models
*   Develop data processing pipelines for data modelling, mining, and production
*   Extension — Big Data Engineer

 || 

*   Ability to see the full picture of data engineering and details of individual data pipelines
*   Build various data pre-processing pipelines for ML in automation

 |
| ML Engineer || 

*   Design and develop ML/DL systems
*   (Re)implement the models and algorithms from data scientist using more (computational) efficient way
*   Possibly implement parallel and/or distributed computing algorithms to improve model efficiency
*   Run ML tests and experiences
*   Extension — Full stack ML engineer

 || 

*   Refine the ML experimentation code as pipelines
*   Visibility into performance of all deployed models.
*   Automated model packaging and deployment to production
*   Potentially use container and API technology; or write scripts for ML pipelines
*   ML artifacts versioning control

 |
| ML Architect || 

*   Ensure a scalable and flexible environment for the ML lifecycle, from design to development, deployment, and monitoring.
*   Introduce new technologies when appropriate that improve the ML model performance in production.

 || 

*   Design the overall ML lifecycle and its pipelines;
*   High-level overview of models and their required resources
*   Ensure the smooth execution of all MLOps stages
*   Capability to dig into ML pipelines to assess and adjust infrastructure needs.

 |
| Software Engineer || 

*   System development and integration with the ML using API, dashboard, etc.
*   Ensure that ML models work seamlessly with other non-ML-based components
*   Extension — Full-stack engineer

 || 

*   Versioning control and automatic tests.
*   The ability to scale the ML application in a parallel or a distributed way

 |
| Software Architect || 

*   All the software architecture other than ML architecture

 || 

*   Design the overall system integration and platform infrastructure

 |
| DevOps Engineer || 

*   Bring in processes, tools, and methodologies to balance needs throughout the ML lifecycle, from ML development and deployment, to maintenance and updates
*   Build and manage (CI/CD) pipelines

 || 

*   Help to implement MLOps pipelines for various aspects with other roles, e.g., ML engineer, data engineer, etc.
*   Integrate MLOps into the larger DevOps strategy of the enterprise
*   Implement MLOps for ML projects seamlessly, e.g., deployment pipeline with ML engineer
*   Implement automatic monitoring and maintenance strategy

 |
| Risk controller/Auditor || 

*   Minimize overall model risk to the company
*   Ensure compliance with internal and external regulatory requirements during the whole ML lifecycle (e.g., check before the model goes to production; periodically audit the model usage)

 || 

*   Use embedded ML risk and ethics monitoring tool (usually, a dashboard with reporting and logging) for continuous monitoring and auditing purpose.

 |
| Project manager/product owner || 

*   Define product scopes, e.g., business value, challenges, ROI, business requirement, data landscape (source, volume, velocity, quality, metadata, etc.), product delivery formats, schedule, etc.

 || 

*   Optimize the overall project progress and schedule using the potential benefits within MLOps framework

 |
| Scrum master || 

*   Carry out agile implementation with ML architect and data scientist
*   Decompose the ML project into major features and milestones, plan, and document user stories and tasks
*   Monitor the progress closely and adjust the schedule and tasks (sub-tasks)

 || 

*   Accelerate the MVP iteration in the ML lifecycle
*   Optimize the requirement change impact to the project via CI/CD pipeline
*   Manage the sprint (flexible with priority) and product backlog in tools like Jira, which is considered as part of MLOps platform

 |

**References**

[1](#chap14.xhtml#ref1).D. Sculley and *et al.,* “Hidden Technical Debt in Machine Learning Systems,” in *Conference on Neural Information Processing Systems (NIPS),* Montreal Canada, 2015.

[2](#chap14.xhtml#ref2).M. Treveil and Dataiku team, Introducing MLOps: How to scale machine learning in the enterprise, O’Reilly, 2020.

[3](#chap14.xhtml#ref3).S. Alla and S. K. Adari, Beginning MLOps with MLFlow: Deploy Models in AWS SageMaker, Google Cloud, and Microsoft Azure, Apress, 2021.

[4](#chap14.xhtml#ref4).H. Hapke and C. Nelson, Building Machine Learning Pipelines: Automating Model Life Cycles with TensorFlow, O’Reilly Media, 2020.

[5](#chap14.xhtml#ref5).S. Vajjala, B. Majumder, A. Gupta and H. Surana, Practical Natural Language Processing: A Comprehensive Guide to Building Real-World NLP Systems, O’Reilly Media, 2020.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

^([1](#chap14.xhtml#rfn1)) [https://venturebeat.com/2019/07/19/why-do-87-of-data-science-projects-nevermake-it-into-production/https://www.forbes.com/sites/enriquedans/2019/07/21/stop-experimentingwith-machine-learning-and-start-actually-usingit/?sh=5c8672703365](https://venturebeat.com/2019/07/19/why-do-87-of-data-science-projects-nevermake-it-into-production/https://www.forbes.com/sites/enriquedans/2019/07/21/stop-experimentingwith-machine-learning-and-start-actually-usingit/?sh=5c8672703365)

^([2](#chap14.xhtml#rfn2)) [https://en.wikipedia.org/wiki/Metadata](https://en.wikipedia.org/wiki/Metadata)

^([3](#chap14.xhtml#rfn3)) Gil Press, “Andrew Ng Launches A Campaign For Data-Centric AI” [https://www.forbes.com/sites/gilpress/2021/06/16/andrew-ng-launches-a-campaign-for-datacentric-ai/?sh=1f2f90ab74f5](https://www.forbes.com/sites/gilpress/2021/06/16/andrew-ng-launches-a-campaign-for-datacentric-ai/?sh=1f2f90ab74f5), retrieved at 21 Nov 2021.

^([4](#chap14.xhtml#rfn4)) “A curated list of awesome open source libraries to deploy, monitor, version and scale your machine learning.” Github. [https://github.com/EthicalML/awesome-production-machine-learning](https://github.com/EthicalML/awesome-production-machine-learning)

^([5](#chap14.xhtml#rfn5)) “Open Source AI and Data Landscape.” Github. [https://github.com/lfai/lfai-landscape](https://github.com/lfai/lfai-landscape)

^([6](#chap14.xhtml#rfn6)) This chart was created using tool from star-history.

^([7](#chap14.xhtml#rfn7)) Since the *ad hoc* replenishment is generally much more expensive than the batch process (i.e., replenish more ATMs in the nearby locations in a given time slot), we have to find a suitable time slot (which is usually from late night to early morning) for the ATM. This logic is implemented independently from ML model. We only consider ML process in the MLOps.

^([8](#chap14.xhtml#rfn8)) “A Git extension for JupyterLab.” Github, [https://github.com/jupyterlab/jupyterlab-git](https://github.com/jupyterlab/jupyterlab-git)

^([9](#chap14.xhtml#rfn9)) Note that we use Hopsworks as feature store shown in Figure 14.13, which may be replaced by Databricks enterprise version’s built-in feature store.

^([10](#chap14.xhtml#rfn10)) The EDA procedure is not integrated into the pipeline, which is generally a manual access by Data Scientists, although some tools and scripts are available. Some exceptional scenarios are handled separately.

^([11](#chap14.xhtml#rfn11)) In some companies, a manual auditing for any “new” model is required. If so, an email or a message shall notify the approver for next action.

^([12](#chap14.xhtml#rfn12)) [https://cloud.google.com/kubernetes-engine](https://cloud.google.com/kubernetes-engine)

^([13](#chap14.xhtml#rfn13)) [https://aws.amazon.com/eks/](https://aws.amazon.com/eks/)

^([14](#chap14.xhtml#rfn14)) [https://azure.microsoft.com/en-us/services/kubernetes-service](https://azure.microsoft.com/en-us/services/kubernetes-service)

^([15](#chap14.xhtml#rfn15)) Cognilytica, “The rapid growth of MLOps,” April 2, 2020.

^([16](#chap14.xhtml#rfn16)) Part of contents are from [https://ml-ops.org/content/mlops-principles](https://ml-ops.org/content/mlops-principles)

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_0015](https://doi.org/10.1142/9789811250903_0015)

Chapter 15

**The Open Banking Ecosystem and its Evolution**

***Yuling Zhang and Jun Xu***

**15.1Introduction**

Open banking is to further open banks by sharing data accesses via Application Programming Interfaces (APIs) to authorized third parties. Data includes public information provided by banks as well as client-specific data within banks. An API is an interface for programs to communicate with one another without the need to understand the detailed structure of its counterparty. With various data access APIs, data can be easily accessed across institutions with control. As this service is data-driven, open banking is also known as “open bank data”.

The introduction of open banking dates back to October 2015, when the European Parliament adopted the revised Payment Services Directive (PSD2) proposed by the European Commission. One of the key rules of PSD2 is to open the European Union (EU) payment market based on the access to information about the payment account, which forces legacy banks in European Economic Area (EEA) to share customer account information to authorized third parties. Major purposes of this adoption include promoting innovation as well as improving the security of payment services in EEA.

Sensing the momentum to advance banking and financial industries as well as the potentials of business use cases with open banking, multiple regulatory parties and commercial institutions from various countries and regions, take actions to follow up EU’s engagement on open banking. The United Kingdom (UK) and Australia introduced mandatory open banking implementation regulation for their major banks, while the Monetary Authority of Singapore (MAS) and the Hong Kong Monetary Authority (HKMA) adopted a guided and collaborative approach via issuing open API guidance. Some financial institutions (FIs) in China and the US also introduced their own open API platform to embrace the spirit of open banking.

From the government’s perspective, open banking is a new incentive to stimulate growth in the banking industry. With the implementation of open banking, financial technology (FinTech) companies enjoy convenience in efficiently gathering bank data with higher accuracy and security compared to direct web scraping. This clears some obstacles in obtaining data for small- and medium-sized FinTech companies, and hence, speeding up the innovative progress for the banking industry on numerous opportunities, including but not limited to customized financial products, more reliable credit checks, and account aggregation services. These innovative solutions can also be directly embedded into daily scenes through APIs for clients’ seamless financial service experience. Banking services are therefore getting more and more customer-centric, and closer and closer to clients’ daily life.

Meanwhile, open banking poses both challenges and opportunities for large traditional banks. Sharing data with third parties invites new competitors to the market. The potential loss in direct connection with clients, and extra obligations on data security and system maintenance further increase the operational risk for these banks. On the other hand, with data available from other large banks and their large customer base, large banks are still in a relatively advantageous position in open banking. They can expand their business by introducing innovative solutions to retain and attract new customers.

Given the significance of the potential innovative disruption that open banking brings, it is believed that a new banking ecosystem will be established, i.e., Bank 4.0. This ecosystem also comes with a groundbreaking banking model known as Banking-as-a-Service (BaaS). With all these opportunities and challenges, key stakeholders such as regulatory parties, traditional banks, and FinTech firms are adopting new strategies to embrace the evolution for open banking. In this chapter, we will uncover the veil of open banking, and demystify the new banking ecosystem and strategy evolution brought by open banking.

**15.2New Banking Ecosystem**

Surrounding APIs — the core of open banking — multiple opportunities can be discovered to provide a new point of growth for both API providers and API users. This wave of innovative opportunities is so disruptive that is likely to bring the banking industry into a new era, i.e., Bank 4.0. In this section, it starts with fundamental elements in open banking — API categories, followed by innovative opportunities — API use cases, and finally the new banking ecosystem built on top of them.

**15.2.1*API Categories***

There are commonly three categories of APIs provided by banks, i.e., bank’s informational APIs, client’s informational APIs, and supplemental or functional APIs (see [Figure 15.1](#chap15.xhtml#fig15-1)).

![](images/p491.jpg)

**Figure 15.1.**Three API categories

*Bank’s informational APIs* are direct access to a bank’s information. Common APIs of this type include the automated teller machine (ATM) or branch locator API, financial product policy API, and credit card reward or promotion API. Data can normally be acquired once the bank’s permission is obtained. The UK and Hong Kong both set this type of informational API as the first group of APIs introduced to the public.

*Client’s informational APIs* are the access to client-specific information, which includes account details, transaction records, and debit and credit card details. The client’s consent is required to access these records. Therefore, some facilitating APIs for authentication are developed to support this category of APIs. Some basic APIs only provide read-only access while other advanced APIs may support both read and write functions.

*Supplemental or functional APIs* do not provide data-sharing services; instead, they offer assistance or advanced services for open banking. Version control APIs and client’s authorization APIs are typical types of supplemental APIs. Payment API is one of the popular functional APIs utilized recently for banks and Internet financial institutions. It is commonly used to enable payment from FIs on third-party mobile applications or websites.

Besides these three categories, banks can also provide prime APIs for their prime clients, such as private banking clients. With prime APIs, banks can introduce selected external products to their clients and handle their prime client services with specific care, which increases client stickiness.

To manage these APIs, API management tools, such as Apigee (Google) Azure (Microsoft), Anypoint (Mulesoft) WSO2, and Tyk, can be used to integrate these APIs into a unified platform. In this process, as illustrated in [Figure 15.2](#chap15.xhtml#fig15-2), the APIs will normally be bundled into API products by incorporating access control, usage restrictions, and other designated business requirements. At the same time, API specifications specifying how an API works, how the API connects to other APIs, and the expected result when using the API will be created for users’ easy reference. Swagger is a common tool to generate API specifications. After creating a user portal via the API management tool, APIs products and specifications will be published to the portal. API users can then access the portal to use authorized open APIs, while API providers will monitor and control the use of APIs via the API management tool.

![](images/p493.jpg)

**Figure 15.2.**APIs and the API platform

For API users, open data APIs can lower the risk of account credential management while ensuring the accuracy of data retrieved. Without open data APIs, in order to enjoy aggregate banking service, users are required to provide personal credentials to a third-party service provider and the third-party service provider will use these credentials to log in to the user’s online banking websites and then use web crawler tools to identify and scratch relevant information from these websites. This method not only increases risks on the user’s bank account but also raises concerns on whether accurate information can be identified and retrieved. However, with open data APIs, these risks and concerns can be easily mitigated.

For API providers, the more companies link to the bank’s payment APIs, the wider the bank’s payment service spreads. Hence, clients of the bank can enjoy more convenient service across different daily scenes. Monetization opportunities, such as commission fees from intermediaries, may also incur simultaneously. Besides partnering with commercial institutions via APIs, banks can also utilize APIs to provide required information to regulatory parties, which reduces the costs of preparing multiple reports.

**15.2.2*API Use Cases***

With the abovementioned APIs available, developers and companies can develop various innovative functions to meet user’s needs.

*Personal finance management (PFM)* ranges from an individual’s budgeting to saving, spending, and investment tracking management. Supported by open APIs from various banks, users can easily handle their income and spending clearly in one place. Mint and Quicken are leading budget tracker and planner tools in the US. Users can access their service through web pages or mobile apps to monitor and manage their personal finance. The Singapore Financial Data Exchange (SGFinDex) provides a comprehensive view of a Singaporean’s wealth portfolio by consolidating her/his financial information.

*Mobile payments* enable users to pay with their mobile devices, which frees users from bringing physical cash or cards. Payment accesses from various banks can be integrated with the introduction of payment APIs. Common examples include PayPal, Apple Pay, Samsung Pay, Alipay, and WeChat Pay.

*Product comparison* can be realized by utilizing financial product information APIs from banks. MoneyHero is a website providing comprehensive financial comparison across personal loans, credit cards, insurance, securities accounts, and mortgage in Hong Kong.

*Credit checking* for loan origination can be conducted more quickly and accurately with clients’ historical financial data available from open banking APIs. This bolsters growth in online lending markets including peer-to-peer lending.

As illustrated in the above use cases, aggregating data or functions from multiple banks is one major source of innovation in open banking. Alternatively, banks can directly connect with non-bank institutions with their open bank APIs. For example, e-commerce platforms that partner with a specific bank may offer special spending installment plans for their clients. Banks may also target their large corporate clients to offer customized financial solutions by using their open bank APIs.

Besides simply giving out data, it is also a good choice for financial service providers to obtain these external data or functions to enhance their own services. For example, banks can access more information to perform credit screening, portray customers, and focus on target clients to provide customized services. This improves banking services across the whole value chain with external supports.

Though currently most open banking APIs are focusing on retail banking, from a long-term perspective, certain APIs may also be provided to serve SMEs or even large corporations. Cross-bank bookkeeping services, cross-bank liquidity and cash management, and cross-bank payment initiation and status tracking are potential target services for corporations. Another big barrier is the cross-border payment. Bank for International Settlements Innovation Hub Singapore Centre and the MAS initialized Project Nexus in July 2021 to enhancing global real-time retail payments network connectivity.

Open APIs can also be merged with other technologies to exploit new opportunities. With Natural Language Processing (NLP), Robotic Process Automation (RPA), and customer data from open APIs, clients may be able to enjoy the more convenient services from personalized chatbots to avoid waiting to optimized and customized know-your-customer (KYC) products. Cheques and other hard copy forms can also be recorded into bank’s system via APIs with the assistance of Optical Character Recognition (OCR) technology, reducing the need for clients to visit a physical retail branch. Open APIs can also be integrated into different scenes with mature Internet of Things (IoT) implemented, such as augmented reality (AR), virtual reality (VR), and mixed reality (MR). It will be extremely beneficial if the IoT system itself figures out what is needed, and then browses online and suggests the best deal and gets the deal paid directly through the open banking payment APIs. Mountainous opportunities are waiting to be evoked by talented developers or companies.

In addition to providing external API access to authorized third parties, some banks also open their open API platform to their internal users, looking forward to facilitating internal innovation development. Bank of China and Ping An Insurance in China have adopted this strategy, which offers a uniform and consistent platform for internal use.

**15.2.3*Banking-as-a-Service and Bank 4.0***

The core of open banking is to open data accesses and other functional accesses to third authorized parties. This adds an additional tier for innovation.

[Figure 15.3](#chap15.xhtml#fig15-3) illustrates the business models with and without the introduction of open banking. In the traditional model, when clients would like to fulfill their daily needs, clients have to go to each individual bank and handle their financial requirements manually, which is inconvenient. From the banks’ perspective, they are responsible for the whole banking value chain, i.e., from basic processing of transactions, banking product development, risk management, to customer relationships and technical maintenance. This wide coverage of the banking value chain also brings challenges to banks as it is difficult for banks to take good care of every activity on the value chain, especially when clients’ expectations are getting higher and higher.

With open banking, banking services are embedded in the clients’ daily scenes. Therefore, clients do not have to first go to attend to their daily needs and then go to the banks as illustrated in the traditional model. Clients can deal with their banking requests and their daily needs at the same time, which saves the clients’ effort to go to the banks. This scenario with open banking can be realized in two ways, i.e., (i) the introduction of aggregators, or (ii) a direct connection between daily scenes and banks.

![](images/p496.jpg)

**Figure 15.3.**Sample business models with and without open banking

In both methods, banks do not have to handle the whole value chain by themselves. Instead, banking services are chopped into small pieces. Whenever the banking service “pieces” fit the needs of the aggregators or businesses, these banking service “pieces” can be directly integrated into their platforms. As the banks still manage the banking services while the aggregators or businesses can enjoy these banking services without being concerned too much about detailed operations or licenses on banking services, this operating model is also known as Banking-as-a-Service (BaaS).

In BaaS, banks do not need to excel in every activity in the value chain, as third parties can take up some duties which used to be on banks’ value chain. The most essential role that banks still need to serve is the infrastructure layer of the whole ecosystem. This means that banks provide basic banking services and innovative ideas come in to stimulate development in the industry.

Even though banks are to be the infrastructure layer, they can still opt to take on other roles based on their strengths and strategies in this ecosystem. For example, banks can work as client-facing aggregators to provide better user experience to clients, or they can utilize their knowledge in compliance and risk control to serve other aggregators. On the other hand, banks may also supplement themselves from other providers, such as FinTech firms. Similar to BaaS, FinTech-as-a-Service (FaaS) refers to FinTech firms providing services to banks through APIs. These services could be operational improvement supported by tech capacities, such as AI, IoT, and OCR. Some banks also set up Bank as a Platform (BaaP) to welcome and manage external APIs.

The idea of banking service pieces also favors small and medium banks. They can put resources to activities on the value chain which yield the most. Services from aggregators also increase the chance that products and services offered by the small and medium banks are to be seen and chosen by the end clients.

Looking back, the banking industry has evolved along with the development of technology. Brett King illustrates the evolution of the banking industry in his book titled *Bank 4.0.* In his opinion, Bank 1.0 mainly relies on physical branches as the primary access point. With the introduction of the ATM and online banking services, Bank 2.0 provides banking services outside of the bank’s working hours, emphasizing the concept of self-service banking, which means clients are able to bank any time. When smartphones became popular, banking services had also moved to mobile devices, bringing new business models such as mobile payments and P2P. This is known as Bank 3.0, and clients can bank not only at any time but also anywhere.

In Bank 4.0, it focuses on ubiquitous frictionless engagement of banking service. Clients may not directly engage with banks, but they are using banking services everywhere. This is exactly the business models with open banking we introduce here. Therefore, open banking not only opens up the data and function from banks, but also opens a new chapter of the banking industry.

**15.3Strategy Evolution**

Since the first introduction of open banking from the EU, regulatory parties are rooted in open banking. At the same time, API providers and API users adopt new strategies in response to the evolution for open banking.

**15.3.1*Regulatory Parties***

As challenging the status quo is an obvious outcome of open banking, with the potential to advance the industry, regulatory parties naturally become core players to drive the transformation of open banking. Though different regulatory parties may view open banking from different standpoints, their responses to open banking normally fall in the following three types — (i) enacting legislation with mandatory open banking regulations, (ii) guiding banks or exploring open banking with the domestic banking industry, or (iii) letting the market itself to lead the progress of open banking development.

The EU, the UK, and Australia incorporated open banking in their legislation, mandating banks in these countries to adopt corresponding open banking strategies. Singapore and Hong Kong utilize a guided and collaborative method via publishing the API Playbook and the high-level open API framework respectively. On the other hand, no direct laws are issued from regulatory parties in China and the US, which gives large room for banking institutions and other technology companies to explore themselves.

*The EU*

Open banking works as an integrated part for the EU to create a level playing field for payment service providers. On January 12, 2016, the Payment Services Directive 2 (PSD2) went into force, being the key legislation in the EU and was aimed at fostering a more integrated and efficient European payment market. It is a revised version of the first Payment Service Directive (PSD1) by taking emerging and new types of payment services into account. One key addition of PSD2 is to level the playing field for third-party providers (TPPs) who offer account information and/or payment integration services to customers, which is realized by mandating banks to share customer’s data and open payment portals to authorized TPPs via APIs, i.e., the EU version of open banking. Countries in the European Economic Area (28 EU member states and 3 European Free Trade Association countries) are mandated to comply with this directive, and they must transpose PSD2 into their local legislation by January 13, 2018. PSD2 is planned to be fully enforced across EEA in 2019.

*The UK*

One of the most important functions of the UK’s open banking is to maintain adequate market competition in the banking and financial industry. In 2016, the Competition and Markets Authority (CMA) issued a report on the retail banking sector in the UK, concluding that older and larger banks do not have to fight as hard for consumers’ business as smaller and younger banks do.^([1](#chap15.xhtml#rfn1)) Hence, open banking was chosen as one of the strategies to boost the UK’s retail banking competitiveness. The Open Banking Implementation Entity (OBIE) was founded to deliver open banking, and nine banks with the largest market share in the UK were required to establish and adopt unified open banking services. Regarding PSD2, though Brexit was confirmed after the referendum on June 23, 2016, the UK chose to continue complying with PSD2 by introducing Payment Services Regulations 2017, which came fully into force in January 2018.

*Australia*

Open banking is one of the first applications on the Australian government’s introduction of consumer data rights. Following the Federal Treasurer’s announcement that the government would introduce open banking in the 2017–2018 budget, a review of open banking was performed to suggest the best way to implementing open banking in Australia. This review was published at the end of 2017 with a theme of giving customers choice, convenience, and confidence. The Australian Government later introduced the draft Consumer Data Right (CDR) Rules Framework,^([2](#chap15.xhtml#rfn2)) which was released for consultation in September 2018. It has been determined that the CDR would be first applied to the banking sector. The four major banks in Australia are required to make data available as the implementation plan, and all remaining banks are required to follow with an extra 12 months for each of the dates set for the four major banks. Other sectors including energy and telecommunications are proposed to follow as well.

*Singapore*

Singapore adopts a guided approach with support towards open banking. In November 2014, an initiative to drive the adoption of digital and smart technologies was proposed as one of the Smart Nation strategies, marking the start of open data and payments. Later in 2016, the Monetary Authority of Singapore (MAS), together with the Association of Banks in Singapore (ABS) released a detailed roadmap, titled “Finance-as-a-Service: API Playbook”, covering recommended APIs, API standards, governance, and use cases. The MAS also set up a Financial Industry API Register as the first landing place for open APIs from FIs.^([3](#chap15.xhtml#rfn3)) The API Exchange (APIX), a collaboration platform launched in November 2018, builds a bridge between FIs and FinTech firms. However, there is no set timeframe for open banking adoption that has been legislated or directed.

*Hong Kong*

The Hong Kong government adopts a collaborative and phased approach to open banking. The Hong Kong Monetary Authority (HKMA) announced its commitments on the New Era of Smart Banking in September 2017. Open banking is part of this long-term strategy. After a 6-month consultation with 41 responses, the HKMA released the Open API Framework for the Hong Kong Banking Sector. This framework outlines 4 phases to implement open banking in Hong Kong and provides guidance on API selection, implementation, and governance. Banks are expected to provide roadmaps of Open API implementation to the HKMA.

*China*

Although China does not mandate open banking, China has long been promoting Big Data development across the country. In May 2018, China Banking and Insurance Regulatory Commission (CBIRC) released the “Guidelines for the Data Management of Banking Financial Institutions”,^([4](#chap15.xhtml#rfn4)) requiring all relevant banking financial institutions to follow this guideline to unify their data governance approach. This is regarded as establishing a foundation for Big Data applications in the banking industry for the coming years. The Ministry of Industry and Information Technology also published Big Data Industry Development Plan (2016–2020),^([5](#chap15.xhtml#rfn5)) which encourages resource-rich, technologically advanced Big Data leaders to build Big Data platforms, open up basic resources such as platform data, computing power, and development environment, and reduce innovation and entrepreneurial costs. In February 2020, the People’s Bank of China (PBOC), which is China’s central bank, published a specification on commercial bank application programming interface secure management (JR/T 0185-2020).^([6](#chap15.xhtml#rfn6)) It references the Open Banking Standard from the UK, the Open API Framework from Hong Kong, and the API Playbook from Singapore. This specification mainly focuses on the security of API design, deployment, integration, operation and maintenance.

*The US*

There is no legislation or pending legislation in the US similar to PSD2 to create a framework for open banking implementation in the US. However, several regulatory parties have released other relevant guidelines. The Consumer Financial Protection Bureau (CFPB) issued a set of data sharing principles on the access and use of consumer data; the Federal Financial Institutions Examination Council (FFIEC) published guidance on retail payments systems and outsourcing technology services. Some industry groups also created standards for open banking themselves. These documents provide guiding supports to the implementation of open banking in the US from various perspectives.

[Figure 15.4](#chap15.xhtml#fig15-4) shows a summary of open banking coverage and implementation mode by different jurisdictions. The EU mandates all EEA members to transpose PSD2 into their local legislation; the UK requires CMA9 to apply open banking; Australia involves four major banks to open data first and the other banks to follow. For Singapore, Hong Kong, China, and the US, as open banking is not mandatory, the coverage is not specific.

![](images/p503.jpg)

**Figure 15.4.**Different regions and its bank coverage  
Note: \*The UK was an EU Member State until January 31, 2020.

Based on the timeline of open banking implementation by regulatory parties in different jurisdictions, Singapore is one of the earliest to publish a detailed technical guidance on open APIs (in 2016), while 2018 is a common year when a number of regions/countries published their guidance on open APIs. The EU published its Regulatory Technical Standards, and the UK updated its Open Banking Standard to Version 3.1 and introduced its Customer Experience Guideline. Hong Kong also issued its final open API framework after consultation in the middle of 2018. [Table 15.1](#chap15.xhtml#tab15-1) is a summary on details of open banking implementation by regulatory parties in different countries/regions.

Though different countries or regions may choose to implement open banking with different schedules or functions, most of them start from opening public informational data through APIs to client’s transactional data to payment functions, from read-only access to read and write access. [Figure 15.5](#chap15.xhtml#fig15-5) is an overview for the EU, the UK, Australia, and Hong Kong on their open banking implementation schedule.

The PSD2 came into force on January 12, 2016 and all EEA members are required to transpose it to their local legislation on or before January 13, 2018. All EEA members have successfully transposed their corresponding local version of PSD2, and PSD2 has been in full effect since September 14, 2019. For the UK, CMA9 begins by providing bank public informational APIs such as branch locator APIs and ATM locator APIs. Mid-data such as customer transaction data, running balance are proposed to open in the first quarter of 2017. One year later, the majority of use cases supported by open data and anonymized and aggregated data should be opened. By the first quarter of 2019, read and write access for transactions (i.e., payment) should be provided. In 2020, UK customers were able to manage their finances, access credit, and make payments through open banking APIs. The UK approved its final stages of the open banking roadmap in 2020. More payment functions, such as refunds, are expected to be delivered later.

Similarly, four major banks in Australia are required to provide product reference data on credit and debit cards, deposit and transaction accounts by July 1, 2019, and mortgage loan data and joint accounts by February 1, 2020, and consumer data on all products recommended by July 1, 2020. The remaining banks in Australia are generally mandated to comply with the schedule with an extra 12 months after the four major banks. So far, Australian customers can authorize third-party data recipients to access their mortgage and joint bank account data.

**Table 15.1.**A summary of open banking implementation according to country/region from the perspective of regulatory parties

![](images/p505.jpg)

![](images/p506.jpg)

![](images/p507.jpg)

![](images/p508.jpg)

**Figure 15.5.**An overview of the timeline of the different country/region’s open banking implementation schedule

Hong Kong identifies four phases for open banking implementation. During the first six months-phase ending in January 2019, readonly access for product and service information is proposed to be provided. The customer acquisition process is targeted in the second phase of the following 12 to 15 months. The schedule for the remaining two phases on account information retrieval and alteration and the function of payment is supposed to be determined later. The first phase was conducted as planned, and all open APIs can be found on a website called Data Studio from the Hong Kong Science and Technology Parks. HKMA also released its own open API platform in 2018. However, the progress has been suspended since November 2019 due to concerns about data security.^([7](#chap15.xhtml#rfn7)) Further arrangements on Phases III and IV are expected to be released in the second half of 2021.

**15.3.2*API Providers***

For banks under regulations, they generally have no choice but to comply with regulatory parities’ requirements. However, it is interesting to note that six banks of CMA9 told CMA that they would not be able to release all Read/Write personal current account and business current account data sets by 13 January 2018. Hence, the CMA released directions for these six banks respectively to stipulate the timeline for delivering the remaining data sets. Currently, most banks in the UK and the EEA have started adopting open banking and opening their data to authorized third parties as required by legislation, providing new chances to their local market.

Similarly, in Australia, Westpac and CommBank were also calling for an extended deadline for open banking due to high costs and security issues.^([8](#chap15.xhtml#rfn8)) On the other hand, National Australia Bank (NAB) and Australia and New Zealand Banking Group (ANZ) in Australia had already launched their own open banking API platform, supporting FX rates, locations, and authentication APIs. On July 1, 2020, all these four banks opened their data on time to kick start the open banking progress in Australia.

For other banks, though there is no requirement from their regulatory parties, they opt to adopt open banking themselves. Citibank is one of the forerunners in open banking. It introduced its developer hub in November 2016, opening APIs for accounts, cards, credit rewards, etc. The scope of its open data later expanded to Singapore and Hong Kong, which makes Citi the first bank in Hong Kong to provide open banking services. Citi also enrolled as a Payment Initiation Service Provider (PISP) in the UK Open Banking Directory,^([9](#chap15.xhtml#rfn9)) being one of the first corporate bank eligible users to use the UK banks’ open APIs.

DBS and OCBC Bank in Singapore, Ant Financials (now Ant Group) and WeChat Pay in China also announced their own open API platform. Compared to restricted user requirements of bank’s open platforms in EEA, some open platforms even allowed individual developers to access and develop their own apps.

Besides traditional banks, certain neobanks also integrate open APIs into their strategy. Some virtual banks in Hong Kong have released their open bank platforms while others have expressed their commitment to open APIs. They believe that they can introduce more innovative services with open APIs to tackle clients’ pain points.

**15.3.3*API Users***

With the increasing number of APIs provided by FIs, many businesses are founded to offer aggregated services to customers, including Mint and Quicken for personal finance management, PayPal and Apple Pay for aggregate payment service, and some other product comparison websites.

Besides FinTech start-ups, FIs themselves also act as active players in using open data. HSBC launched a Connected Money app^([10](#chap15.xhtml#rfn10)) in the UK to enable customers to see their accounts from different banks together in one place. Barclays also incorporated open banking services in its mobile banking app, allowing its customers to see their current accounts from other banks in one place.^([11](#chap15.xhtml#rfn11))

Card associations, such as Visa and MasterCard, are a special type of API users. They inherently aggregate data and payment functions from multiple banks, which makes them natural service aggregators. Visa and MasterCard, two giant international card associations, have proactively embraced open banking. In 2020, MasterCard acquired Finicity, a startup that offers financial data aggregation services for credit decisions.^([12](#chap15.xhtml#rfn12)) Similarly, in the same year, Visa proposed to acquire Plaid, a FinTech company that provides FinTech solutions to companies to connect people’s financial data to apps and services.^([13](#chap15.xhtml#rfn13)) Although Visa’s acquisition failed due to regulatory antitrust concerns, it still shows Visa’s strategic consideration in open banking. From the banks’ perspective, it is also of the banks’ interest to see these mature bank card associations proactively participating in open banking, as they serve as a part of the underlying infrastructure for open banking and take over certain risks in the process of API data/function sharing.

**15.4Evolution in China**

Although open banking is not mandatory in China, banks in China have also seized this opportunity to explore business potentials. Given the strong presence of mobile payment services in China, it is interesting to see how banks position themselves with the help of open banking. The digitalization process of the China banking industry could also be a good reference for other countries/regions. In the meantime, various service aggregators have come into being, covering payment, wealth management, personal finance management, and loan application.

**15.4.1*Banks***

Similar to some western countries, the banking industry in China is dominated by several major banks, including Industrial and Commercial Bank of China (ICBC), China Construction Bank (CCB), Agriculture Bank of China (ABC), and Bank of China (BOC). There are also 12 nationwide joint-stock commercial banks, which have increasing market share recently. Other banks such as urban commercial banks, private banks, and foreign banks also act as important roles in the China banking industry.

In China, mobile payment has been growing dramatically, covering a wide variety of daily payment scenes. On top of that, online shopping has also become more and more popular across the country. Banks that would like to meet their clients’ needs in mobile payment and online shopping have to open their payment and payment-related APIs to various third-party mobile payment providers or online merchants. Moreover, by taking the initiative in offering their APIs, banks also enjoy a higher possibility to partner with more institutions, which is likely to increase the use of their own banking services. Therefore, instead of solely starting from informational APIs, banks in China introduce payment APIs to maintain their own competitiveness.

Besides payment-related services, banks have also introduced a broader range of APIs lately, such as credit card applications, loan applications, and wealth management services. These APIs penetrate various scenes and generate new business ideas to support the banks’ business. For example, the SPD Bank has opened a credit card application channel on Alipay. Alipay is a widely-used mobile payment app in China. It also links to multiple online and offline merchants. After applying for the bank’s credit card through Alipay, clients can enjoy multiple discount offers customized by Alipay for the credit card specifically. Clients are therefore more likely to use their new credit card, which increases the retention rate of new credit card clients for the bank.

Open banking conventionally concerns more on retail clients, i.e., to C (Customer). As banks naturally have a deeper financial relationship with institutions, banks in China also explore API business opportunities with commercial clients and governments, i.e., to B (Business) and to G (Government). For example, corporations need to pay their employees or clients, which are high frequent payment scenes with various payment amounts. ICBC, Ping An Bank, China Minsheng Bank have come in to provide API solutions to support these frequent corporate payment scenes. ICBC has applied this use case to Huawei and China Life Insurance Company. Along with the digitalization process in China, the Chinese government also launched its initiative in simplifying government services. One major approach is to set up various smart city online service platforms. Some banks have also seized this opportunity. CCB has leveraged its FinTech capability to partner with governments at different levels across the country to support this initiative.

[Table 15.2](#chap15.xhtml#tab15-2) summarizes open bank platforms for banks in China. These banks are mainly state-owned commercial banks or nationwide joint-stock commercial banks. They generally support common technical functions, such as providing the Software Development Kit (SDK) for key programming languages and being applicable for various platforms. Their API category mainly covers product information, bank account services, loan services, wealth management services, and payment services. Several banks (e.g., CMB) also provide API on other key tech functions, such as OCR and facial recognition, to supplement their banking service. These open bank platforms typically open to external developers while banks such as BOC, CMB, and Ping An Bank also leverage this platform to internal staffs to encourage in-house innovation.

**Table 15.2.**A summary of the open bank platforms in China

![](images/p514.jpg)

![](images/p515.jpg)

To use APIs in these open platforms, developers generally need to register on these platforms with their phone number and email address. This will unlock the most fundamental functions of the developer portal. Developers need to have their real official name verified before they can start using APIs. This process is usually conducted by verifying the developer’s banking credentials if the developer owns a bank account at the bank concerned. Corporate developers also need to be verified by providing various corporate documents such as business licenses. After the registration and verification process, developers can create their application requests on the open bank platform and ask for relevant APIs. If this gets approval from the bank, developers will receive a testing certificate and a public-private key pair, and be able to use them to test their application in the sandbox provided by the bank. After completing the testing process, developers can apply for a new certificate for the actual production environment. However, it is worth noting that as banks own these APIs, it is at the banks’ discretion to approve it or not.

One major concern for banks regarding open banking is disintermediation, which means that banks may serve in the infrastructure layer in the financial industry in the future without frequently directly interacting with end clients. Instead of fully letting third-party service providers use these APIs and reaching the end clients, banks in China also take the initiative to leverage their API capability to explore business solutions for end users.

At a relatively early stage, open platforms only targeted developers and only list out available APIs, but recently, banks have started presenting possible business scenes on their open platforms. In this case, the banks’ open banking promotions better serve corporate leaders who focus more on business pain points, and corporations can directly match the banks’ solutions to their needs. After defining business needs, banks and corporations can go on technical details later, such as API specifications. Recent common scenes include credit card installment schemes, credit card applications, loan applications, carpark payments, and salary payments.

In addition to providing solutions on single business scenes, some banks go even further to provide multiple financial solutions at one go. Corporations and institutions normally engage in various financial scenes, such as paying salaries to employees, collecting miscellaneous fees, and supply chain financing. If they can all be combined in one platform or software, it would be much more convenient for these corporations or institutions. However, tech firms generally do not have sufficient commercial banking or corporate banking knowledge, and they do not have a direct connection with these corporations and institutions. On the other hand, banks naturally have deep financial relations with them. If banks can utilize their technical resources wisely, this pain point can be tackled. Therefore, some banks combine open APIs with other technologies, such as Cloud service, to provide various Software-as-a-Service (SaaS) or Platform-as-a-Service (PaaS) so that these corporations or institutions can directly come to the banks and integrate all their financial needs into one customized platform. ICBC offers Cloud solutions for various industries, including education, property management, and tourism scenic spots. CMB also proposes smart solutions for educational institutions, hospitals, and others. The smart education system from CMB has been served to the University of Science and Technology of China, Tongji University, and Shandong University. Specifically, CMB also presents their block-chain integrated service solution on their open platform for commodity tracing and transaction/financial information storage.

In order to stay competitive, banks can also provide flexibility for clients who may not hold the bank account of their banks. Ping An Bank directly offers cross-bank payment and cross-bank fund collection solutions on their open platform. ICBC also supports clients with non-ICBC bank account on their salary payment solution.

The wave of open banking also imposes challenges for smaller traditional banks in China. They typically do not have adequate technological capacities for open banking and the corresponding cyber services. For example, when they move their products online, they may not be able to detect online fraudulent activity, control cyber risks, or manage clients. Instead of building up the whole ecosystem themselves, a better choice for them is to work with a partner, e.g., a technical partner, and try to be integrated into a larger ecosystem.

Some banks see this technical potential in open banking, and they step up to offer technical supports. Industrial Bank set up a FinTech subsidiary CIB FinTech, specifically providing solutions for FIs, including open banking and open banking related solutions. Similarly, WeBank, a private bank founded by Tencent in 2014, also introduces a FinTech platform, aiming to shape Banking 4.0 with open platform, open innovation, and open collaboration. This platform particularly provides tech capability in AI, Blockchain, Cloud Computing, and Big Data. They can both be viewed as FinTech-as-a-Service (FaaS) in China.

Internet banks are also an emerging banking group in China. They are aimed at utilizing technology to provide better banking services. WeBank mentioned earlier is one of them. Although very few of them have opened an open platform to provide APIs of their own banking services, some news suggests that some of these banks are preparing APIs and partnering with external parties through APIs. These include aiBank (launched by China tech giant Baidu and China CITIC Bank) and Beijing Zhongguancun Bank.

Foreign banks in China are also exploring open banking. Standard Chartered Bank opened APIs to a third-party company for a virtual account API project in 2018. HSBC also introduced a smart trade solution based on API technology during the second China International Import Expo in 2019.

**15.4.2*Aggregators***

Besides banks themselves packing their own APIs to offer integrated solutions, there are also multiple third-party service providers aggregating various banking services to the end clients, covering services of payment, wealth management, personal finance management and loan application.

15.4.2.1*Payment*

Payment is one of the most common aggregated banking services. Payment aggregators accept fund transfers from various banks, and users can directly use their deposit or credit limit from various banks in their daily payments through a payment aggregator. It normally involves a QR code in the payment process. The merchants can scan the payers’ QR codes to receive payments or the payers can scan the merchants’ QR codes for their payments. They also generally support peer-to-peer money transfers.

Two renowned payment aggregators are Alipay from Alibaba and WeChat Pay from Tencent. They have both introduced multiple daily payment scenes on their portal or app. Users can directly make mobile bill payments or utility payments, order ride-hailing or food delivery, book event tickets or rail/flight tickets, or shop online through these payment apps. They have also introduced QR code payment for buses and metros for multiple cities in China. Inter-city trains are also supported. For example, in the Greater Bay Area, users can directly scan a designated QR code for Guangzhou–Shenzhen trains when they get into the station, without booking tickets in advance.

Besides payment scenes, they also offer money market wealth management products for users to manage their money in e-wallets. Alipay also provides credit limits so that users can spend first and pay back at the payment due date. Micro-loans and insurance are also offered on the platform.

Other major payment aggregators include JD Pay from [JD.com](http://www.JD.com), UnionPay App from UnionPay, and Dragon Pay from China Construction Bank (CCB). [JD.com](http://www.JD.com) is one of the largest e-commerce platforms in China. UnionPay is the sole bank card association founded in China.

Interestingly, they also provide open API platforms to explore more business opportunities. [Table 15.3](#chap15.xhtml#tab15-3) details functionalities, technology, API Category, and eligible users for them. Their APIs normally cover various payment methods, such as QR code payment, payment via websites, external apps, or in-app mini-programs, and other payment supporting functions including authentication, transaction inquiry, refund, and risk control.

**Table 15.3.**A summary of the open platform for non-bank API provider institutions in China

![](images/p520.jpg)

![](images/p521.jpg)

Similar to banks, they also use a scene-based approach to attract business on their open platforms. On top of this, they provide more developer training guidance. Alipay and UnionPay both offer tutorial videos for developer beginners. Alipay even creates a developer community for developers to discuss and communicate with each other. Moreover, WeChat Pay, Alipay, and UnionPay all welcome collaboration outside mainland China. They all offer an English version of their open platforms.

There are also aggregators over those payment aggregators mentioned above, including two common categories, i.e., (i) aggregate payment collection service providers, and (ii) technical service providers.

Due to the increasing number of payment methods from both banks and non-bank API provider institutions, the process of receiving payments from customers becomes complicated, and this is where aggregate payment collection services come in. The most common ones are to use one aggregate QR code for all customers to scan for various payment apps or to utilize one scanning gun for various QR codes from different apps. Saobei (Scanning) from Lichu Business and Quick POS are two representatives of this type.

In addition to payment equipment, providing technical service support for corporations and merchants for a comprehensive payment solution is another focus for firms like PING++ and Paymax. Through their services, users can quickly link to multiple APIs from various payment channels rather than figuring out the API connect methods one by one by users themselves.

[Figure 15.6](#chap15.xhtml#fig15-6) provides some examples of these two types of aggregators.

15.4.2.2*Wealth management*

Wealth management is another possible use case for service aggregation. Aggregators gather product information from various banks and display them on their apps. Users can compare these products and make their investment decisions accordingly. The bank wealth management products are normally referring to short-term money market instruments.

![](images/p523.jpg)

**Figure 15.6.**Aggregate payment service for merchants in China

Bicai Big Data Technology Group^([14](#chap15.xhtml#rfn14)) offers an app called Shibeibi, positioned as the third-party recommendation engine of bank wealth management. It has partnered with over 100 banks. Users can directly invest in these wealth management products through this app. The app will also recommend products to users based on their interests. Besides retail users, Bicai also opens its wealth management service to corporate clients. Corporations can link those banking wealth management products through APIs to their own platforms. Another initiative from Bicai is to integrate products from Hong Kong banks through the Hong Kong Open API framework to serve Hong Kong residents, mainland Chinese, and eligible overseas investors. Bicai received its pre-C-round^([15](#chap15.xhtml#rfn15)) funding for 100 million Chinese Yuan (approximately US$15 million) in April 2020.

Qianxiansheng^([16](#chap15.xhtml#rfn16)) is another app that provides similar functions. Direct banks can register on its platform and the banks’ products can later be displayed on the app for free. There are around 200 banks on this app. Public information shows that this firm got A-round^([17](#chap15.xhtml#rfn17)) funding in 2014.

Tech giants are also entering the bank wealth management product market, including Du Xiaoman Financial from Baidu and JD Digits from [JD.com](http://www.JD.com).

Compared with payment aggregators, wealth management aggregators are less mature. This is probably due to the relatively low awareness of mass investors on this type of aggregator. Investors’ concerns over the reliability of these apps may also deter the development of these aggregators.

15.4.2.3*Personal finance management and loan application*

Personal finance management (PFM) aggregators aggregate information of users’ bank cards across banks and provide supplementary services on them.

UnionPay App is one of the popular service providers on cross-bank bank card management. UnionPay is the only bank card association founded in China, which makes it a natural fit in providing such service. Users can check the balance and recent transactions of almost all bank cards from major Chinese banks and selected bank cards from foreign banks on the app. It also displays special offers from various banks, covering multiple scenes such as catering, accommodation, and traveling. Users can also pay back credit card bills on this app directly. Micro-loans are also provided on this app.

Other PFM service providers include Kaniu and 51 Credit Card Inc. They generally import users’ bank card statements from users’ bank statement emails or online banking. Additional services include reminders of credit card payment, setting auto credit card payments, credit card applications for various banks, special discount offers, micro-loan applications, and wealth management.

Regarding loan application services, service providers generally directly offer a rate for clients, rather than displaying loan product information from different banks, although the funding of these loans is possibly coming from banks. In this case, these service providers perform in-house client credit checking and take the loan risks themselves. From the clients’ perspective, by only involving loan service providers, the micro-loan origination process can be shortened into minutes or seconds, which brings more convenience.

**15.5Impacts and Recommendations**

Along with all these opportunities brought by open banking, there are several high-level key points for traditional banks and non-bank institutions to consider.

**15.5.1*Traditional Banks***

With the introduction of open banking, several major impacts can be foreseen for banks.

*More intense competition*

The bank’s data come from their own business operations and these data also refuel them to offer more suitable products for customers. Through opening their data access, these banks are inviting third parties to use their data to offer new products or services in their field, which increases the level of competition in the market sectors, especially the retail banking market.

*Higher technological requirement*

When providing public APIs, banks need to ensure the security of using their APIs along with potential cyber-attacks. At the same time, to meet users’ expectations, APIs are anticipated to run smoothly with low latency. Therefore, this additional obligation on open banking raises higher technological requirements for banks.

*Looser connection to customers*

With open banking, aggregators will become a new point of connection for individual customers. In this regard, it becomes more difficult for banks to directly promote products to customers. Moreover, with more choices aggregated by aggregators, customers can easily switch to products from other FIs.

Though open banking imposes large challenges for banks, there are still multiple opportunities for banks to explore in this field. There are four major roles in open banking, i.e., API providers, API users, regulatory parties, and facilitators ([Figure 15.7](#chap15.xhtml#fig15-7)). Banks are naturally API providers. From the other perspective, they can also take the role of API users to join the competition with aggregators.

In terms of the role of API providers and API users, banks are recommended to consider the following aspects.

*Customer’s needs*

Though open banking is changing the banking world, the core of banking services or products is not changing, i.e., how much value banks can provide to their customers. The products or services provided through the role of API providers or API users should also follow this principle. The more attractive the product is, the more likely customers will choose this product even from a third-party application.

*Technology*

To ensure a good user experience for the APIs or the aggregate service applications, technology is a major concern. This includes the fundamental infrastructure required to ensure the security of their technology products as well as some latest technologies that can provide additional new functions to their products, such as Artificial Intelligence (AI), Blockchain, and Internet of Things (IoT). In other words, the right balance between security concerns and the user experience shall need to be carefully studied.

![](images/p527.jpg)

**Figure 15.7.**Four major roles in open banking

*Governance*

Suggestions from internal staff may be an important source of innovation for banks themselves. Making good use of internal suggestions is likely to release huge positive energy. From a broader perspective, simplifying the implementation procedure of relevant innovation transformation and reducing duplicated work by leveraging achievements in the bank can possibly account for two important considerations for the implementation of open banking.

*Strategic direction*

Open banking is a clear trend for banks to consider, but it is still critical for individual banks to think about their comparative advantages over other banks or non-bank institutions. Banks are recommended to make the best use of their comparative advantages in their long-term strategic plan rather than solely pursuing the trend of open banking. Furthermore, even though the world tends to transform everything from offline to online, the physical presence of retail branches worldwide is still a great asset for banks, especially when comparing to newcomers in the retail banking industry. Utilizing this massive physical asset in the future will be an interesting topic for banks.

As banks dominate the present fundamental financial service market, their practical advice or comments count comparatively heavily for regulatory parties. Hence, instead of passively following the trend, banks can even lead the trend of future open banking. In this sense, banks are advised to go further to understand more about what other banks and FinTech start-ups are doing recently. They can also take the initiative to invite other parties together to set guidance or standards on the operating framework or technology framework of open banking, such as API standards, data security, data sharing boundary, partner entry policy, etc.

Currently, banks are still of great advantage over non-bank institutions. They have great customer bases, which reduces the difficulties for them to attract customers to their new products. For recruiting professionals, banks normally own a wide platform for talents, and they are more capable of offering a competitive benefits package compared to start-ups or SMEs. With their dominant market share in the banking service market, their reputation to customers gives an extra premium for them when exploring new digital products on open banking. However, as an increasing number of firms sense potential business opportunities with the trend of open banking, the banks’ advantages may diminish as time goes by. Therefore, banks are recommended to advance themselves with the chance of open banking earlier to make the most of their advantages.

**15.5.2*Non-bank Institutions***

As one of the key incentives of open banking is to open the door for non-bank institutions to invite more innovation in the banking industry, non-bank institutions are naturally the key beneficiaries with the promotion of open banking. However, competition among themselves and pressure from existing traditional banks should draw their attention. Here are aspects for non-bank institutions to consider.

*Customer’s needs*

Without a strong market presence compared to banks in the retail banking service market, how much the product meets customer’s needs becomes vital to building the foundation of success for nonbank institutions. The level of meeting customer’s needs can be measured by evaluating how much the product helps to reduce a customer’s own effort for the same task, or how much unexpected additional value is brought to a customer. Understanding a customer’s needs requires in-depth research, sharp market sense, and an innovative mindset from non-bank institutions.

*Security*

Security is always a major concern for stakeholders. In Europe, cybersecurity, data protection, and credit risk management have been incorporated in the European Central Bank (ECB) requirements for FinTech firms to get licensed. On top of complying with regulatory requirements, if a product commits a higher level of security standard, it may gain extra premium from customers and API providers. However, maintaining a satisfactory level of user experience is also crucial when ensuring security and reliability.

*Customer base*

Different from banks, acquiring customers for new aggregate products or services will probably be a great concern for non-bank institutions. WeChat Pay and Alipay offered billions of coupons for users to cultivate their payment behavior at the early stages, which had proven to be successful. Having large reputable firms as partners, suppliers, clients, or investors could also be helpful to attract customers.

Regarding the roles of non-bank institutions in open banking, besides being API users, they could also work as facilitators for open banking. For example, assisting aggregators in linking APIs provided by various API providers and building up customized platforms may be suitable for tech-savvy firms, while providing legal advice or financial support for aggregators may be a proper business direction for firms specialized in corresponding fields. Institutions are suggested to analyze their advantages over others and find the best path for themselves.

**15.5.3*Future Banking***

The unexpected COVID-19 pandemic has changed the world significantly, such as work-from-home orders, lockdowns, and social distance. People have changed their behaviors and are relying more on the digital services, such as online or mobile banking. As Brett King, the author of *Bank 4.0,* shared his post-COVID forecast in 2020, the current credit evaluation system will be changed, the behavioral credit scoring system will prevail for most of the world, and AI and behavioral gamification will be used to cultivate clients’ healthy behaviors in wealth management.

In fact, by building integrated and high-performance API platforms, open banking provides greater literacy, visibility, and flexibility for the users with frictionless banking services. Instead of considering open banking as a compliance requirement, FIs start to adopt it as a key business driving force e.g., create new business model and grow product diversity. They are encouraged to partner agilely with FinTech firms or establish their own FinTech subsidiaries to integrate more innovative services and functionalities via BaaS and FaaS, and eventually, build the platformization ecosystem to proactively satisfy client’s changing needs.

It is also interesting to note that although one of the main purposes of open banking is for data sharing, it is not the sole campaign for open data to blur industry boundaries. More and more professionals are advocating personal data ownership and control rights, such as the web decentralization project ‘Solid’ from the Massachusetts Institute of Technology (MIT)^([18](#chap15.xhtml#rfn18)) and digital identity management application Chekk.^([19](#chap15.xhtml#rfn19)) Foreseeing the growing trend of open data required by communities and governments, banks and other relevant institutions are recommended to get more prepared and positively react to open banking.

Open banking is still at its early stage in both physical and virtual worlds. Particularly when Metaverse (see [Chapter 2](#chap2.xhtml)) attracted more attention, open banking framework provided a direct entry ticket to it. With all these challenges and opportunities, it is thrilling to see what will come next and how the future banking will be.

**15.6Appendix: Websites for Open Platforms in China**

*   Agricultural Bank of China — Open Bank. URL: [https://openbank.abchina.com/Portal/index/index.html](https://openbank.abchina.com/Portal/index/index.html)
*   Alipay. URL: [https://global.alipay.com/](https://global.alipay.com/)
*   Bank of China — Open Platform. URL: [https://open.boc.cn/doc\_info\_4167.html](https://open.boc.cn/doc_info_4167.html)
*   China CITIC Bank — Open Bank. URL: [https://open.citicbank.com/#/](https://open.citicbank.com/#/)
*   China Construction Bank — Open Bank. URL: [https://open.ccb.com/](https://open.ccb.com/)
*   China Merchants Bank — Open API Platform. URL: [https://openapi.cmbchina.com/?category\_id=home](https://openapi.cmbchina.com/?category_id=home)
*   China Minsheng Bank — Open Bank. URL: [https://openbank.cmbc.com.cn/](https://openbank.cmbc.com.cn/)
*   CIB FinTech Open Bank Services. URL: [https://open.cibfintech.com/portal/index.html](https://open.cibfintech.com/portal/index.html)
*   Industrial and Commercial Bank of China — Open Platform. URL: [https://open.icbc.com.cn/](https://open.icbc.com.cn/)
*   JD Pay. URL: [https://www.jdpay.com/home/](https://www.jdpay.com/home/)
*   Ping An Bank — Open Platform. URL: [https://210.21.216.211:567/main.html](https://210.21.216.211:567/main.html)
*   Shanghai Hua Rui Bank — Open Platform. URL: [https://open.shrbank.com/index.html](https://open.shrbank.com/index.html)
*   SPD Bank — API Open Platform. URL: [https://open.spdb.com.cn/develop/#/index](https://open.spdb.com.cn/develop/#/index)
*   UnionPay international. URL: [https://www.unionpayintl.com/en/](https://www.unionpayintl.com/en/)
*   UnionPay Merchant Services — Open Platform. URL: [https://open.chinaums.com/index](https://open.chinaums.com/index)
*   WeBank FinTech. URL: [https://fintech.webank.com/](https://fintech.webank.com/)
*   WeChat Pay. URL: [https://pay.weixin.qq.com/](https://pay.weixin.qq.com/)

**References**

1.ABS and MAS. *ABS–MAS Financial World: Finance-as-a-Service API Playbook.* (2016). Accessed: September 13, 2021. Available: [https://abs.org.sg/docs/library/abs-api-playbook.pdf](https://abs.org.sg/docs/library/abs-api-playbook.pdf)

2.Department of the Treasury, “Review into Open Banking in Australia: final report,” Australia, 2018.

3.Deloitte, “2018 Banking Industry Outlook,” 2017. \[Online\]. Available: [https://www2.deloitte.com/si/en/pages/financial-services/articles/gx-banking-industry-outlook.html](https://www2.deloitte.com/si/en/pages/financial-services/articles/gx-banking-industry-outlook.html)

4.Hong Kong Monetary Authority. *Open API framework for the Hong Kong banking sector.* (2018). Accessed: December 1, 2021. \[Online\]. Available: [https://www.hkma.gov.hk/media/eng/doc/key-information/press-release/2018/20180718e5a2.pdf](https://www.hkma.gov.hk/media/eng/doc/key-information/press-release/2018/20180718e5a2.pdf)

5.Competition and Markets Authority, “Retail banking market investigation,” 2016.

6.HM Treasury, “The payment services regulations 2017,” 2017.

7.PwC. *Financial Crimes Observer — Open banking: US is next.* (2018). Accessed: December 1, 2021. \[Online\]. Available: [https://www.pwc.com/il/he/bankim/assets/2018/Open%20banking-US%20is%20next.pdf](https://www.pwc.com/il/he/bankim/assets/2018/Open%20banking-US%20is%20next.pdf)

8.European Parliament, “Directive (EU) 2015/2366 of the European Parliament and of the Council,” 2015.

9.B. King, *Bank 4.0: Banking everywhere, never at a bank,* 1st ed. The UK: Wiley, 2019.

 

 

 

 

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chap15.xhtml#fn1)“Retail banking market investigation”. GOV.UK. [https://www.gov.uk/cma-cases/review-of-banking-for-small-and-medium-sized-businesses-smes-in-the-uk](https://www.gov.uk/cma-cases/review-of-banking-for-small-and-medium-sized-businesses-smes-in-the-uk). Accessed: September 13, 2021.

[²](#chap15.xhtml#fn2)“Consumer data right (CDR)”. Australian Competition and Consumer Commission. [https://www.accc.gov.au/focus-areas/consumer-data-right](https://www.accc.gov.au/focus-areas/consumer-data-right). Accessed: September 13, 2021.

[³](#chap15.xhtml#fn3)“Financial Industry API Register”. Monetary Authority of Singapore. [http://www.mas.gov.sg/Singapore-Financial-Centre/Smart-Financial-Centre/Financial-Industry-API-Register.aspx](http://www.mas.gov.sg/Singapore-Financial-Centre/Smart-Financial-Centre/Financial-Industry-API-Register.aspx). Accessed: September 14, 2021.

[⁴](#chap15.xhtml#fn4)“China Banking and Insurance Regulatory Commission issued the ‘Guidelines for the Data Management of Banking Financial Institutions’”. The State Council of the People’s Republic of China. [http://www.gov.cn/xinwen/2018-05/23/content\_5292938.htm](http://www.gov.cn/xinwen/2018-05/23/content_5292938.htm). Accessed: December 1, 2021.

[⁵](#chap15.xhtml#fn5)“Big Data Industry Development Plan (2016–2020)”. [https://www.ndrc.gov.cn/fggz/fzzlgh/gjjzxgh/201706/t20170622\_1196822.html?code=&state=123](https://www.ndrc.gov.cn/fggz/fzzlgh/gjjzxgh/201706/t20170622_1196822.html?code=&state=123). Accessed: December 1, 2021.

[⁶](#chap15.xhtml#fn6)“‘Commercial bank application programming interface secure management specification’ financial industry standard officially released”. China Financial Standardization Technical Committee. [https://www.cfstc.org/en/2932554/2976200/index.html](https://www.cfstc.org/en/2932554/2976200/index.html). Accessed: September 13, 2021.

[⁷](#chap15.xhtml#fn7)“The Future of Banking: One year on, Hong Kong’s open banking initiative hits a roadblock”. S&P Global Ratings. [https://www.spglobal.com/ratings/en/research/articles/191003-the-future-of-banking-one-year-on-hong-kong-s-open-bankinginitiative-hits-a-roadblock-11181238](https://www.spglobal.com/ratings/en/research/articles/191003-the-future-of-banking-one-year-on-hong-kong-s-open-bankinginitiative-hits-a-roadblock-11181238). Accessed: December 1, 2021.

[⁸](#chap15.xhtml#fn8)“Westpac and CommBank hit back at Aus open banking plans”. Finextra. [https://www.finextra.com/newsarticle/31946/westpac-and-commbank-hit-back-at-ausopen-banking-plans](https://www.finextra.com/newsarticle/31946/westpac-and-commbank-hit-back-at-ausopen-banking-plans). Accessed: December 1, 2021.

[⁹](#chap15.xhtml#fn9)“Citi corporate bank joins UK open banking framework”. Finextra. [https://www.finextra.com/newsarticle/32194/citi-corporate-bank-joins-uk-open-bankingframework](https://www.finextra.com/newsarticle/32194/citi-corporate-bank-joins-uk-open-bankingframework). Accessed: December 1, 2021.

[^(10)](#chap15.xhtml#fn10)R. Browne. “HSBC’s new money management app has racked up 300,00 users in a year”. CNBC. [https://www.cnbc.com/2019/04/30/hsbc-connected-moneyapp-has-racked-up-300000-users-in-a-year.html](https://www.cnbc.com/2019/04/30/hsbc-connected-moneyapp-has-racked-up-300000-users-in-a-year.html). Accessed: December 1, 2021.

[^(11)](#chap15.xhtml#fn11)Barclays becomes the first UK high street bank to allow customers to bring their other current accounts into its Mobile Banking app”. Barclays. [https://home.barclays/news/press-releases/2018/090/barclays-becomes-the-first-uk-high-streetbank-to-allow-customer](https://home.barclays/news/press-releases/2018/090/barclays-becomes-the-first-uk-high-streetbank-to-allow-customer). Accessed: February 20, 2022.

[^(12)](#chap15.xhtml#fn12)“Mastercard extends open banking efforts with close of Finicity acquisition”. Mastercard Newsroom. [https://www.mastercard.com/news/press/2020/november/mastercard-extends-open-banking-efforts-with-close-of-finicityacquisition/](https://www.mastercard.com/news/press/2020/november/mastercard-extends-open-banking-efforts-with-close-of-finicityacquisition/). Accessed: December 1, 2021; “Visa and Plaid abandon merger after antitrust division’s suit to block”. The United States Department of Justice.

[^(13)](#chap15.xhtml#fn13)“Visa and Plaid Abandon Merger After Antitrust Division’s Suit to Block”. U.S. Department of Justice. [https://www.justice.gov/opa/pr/visa-and-plaid-abandonmerger-after-antitrust-division-s-suit-block](https://www.justice.gov/opa/pr/visa-and-plaid-abandonmerger-after-antitrust-division-s-suit-block). Accessed: December 1, 2021.

[^(14)](#chap15.xhtml#fn14)“Bicai is always a wise choice in finding the best WMP”. Bicai. [https://www.bicai365.com/about.html](https://www.bicai365.com/about.html). Accessed: December 1, 2021.

[^(15)](#chap15.xhtml#fn15)There are multiple rounds in raising funds. When it completes its B round but has not yet reached C round, the funding is called pre-C round.

[^(16)](#chap15.xhtml#fn16)“Qianxiansheng”. Qianxiansheng. [https://www.qianxs.com/website/index.html](https://www.qianxs.com/website/index.html). Accessed: December 1, 2021.

[^(17)](#chap15.xhtml#fn17)There are multiple rounds in raising funds. When it completes its funding from Angel investors but not yet reaches A round, the funding is called pre-A round funding.

[^(18)](#chap15.xhtml#fn18)“Solid: Your data, your choice”. Solid. [https://solidproject.org/](https://solidproject.org/). Accessed: December 1, 2021.

[^(19)](#chap15.xhtml#fn19)Chekk. [https://www.chekk.me/](https://www.chekk.me/). Accessed: February 17, 2022.

© 2022 World Scientific Publishing Company  
[https://doi.org/10.1142/9789811250903\_bmatter](https://doi.org/10.1142/9789811250903_bmatter)

**Conclusion**

Artificial intelligence (AI), Blockchain (and distributed ledger technology, or DLT), Cloud, Big Data, and Internet of Things (IoT), abbreviated as “ABCDI”, form the fundamental and technological driving forces for FinTech. For example, AI solutions using chatbot, optical character recognition (OCR), robot processing automation (RPA), and algorithmic trading have been widely adopted in the industry. Continuous developments and improvements on pre-trained models for natural language process (NLP), self-learning and few-shot, knowledge graph (KG) and privacy-preserving techniques make AI indispensable for financial institutions (FIs).

Together with technological advancements in associated areas such as quantum computing and metaverse, ABCDI and its integrated composite technological innovations lead the trend in FinTech. In fact, intensified competition for market share and products makes the underlying technology and digitalization innovations more important than ever. “No technology, no finance” has become an industry consensus.

FinTech applications and solutions exist across almost all business lines ranging from the digitization and automation of back-end information systems, the personalization and mobilization of front-end financial products and services, to the optimization of intelligent and flexible middle platforms. They are usually employed by different transactions relating to payment and settlement, digital currency, deposit, loan and capital raising, investment management, and market infrastructure.

To accelerate the innovation and adoption of FinTech, FIs shall increase investment in talent, technology, and data pools, cultivate an open and innovative culture, and incubate their ecosystem.

FinTech embodies an interdisciplinary approach that focuses on skills development on advanced analytical methods in economics and finance, and the effective use of ABCDI and associated technologies to promote innovations. Therefore, critical talents are generally equipped with knowledge and capabilities in multiple domains. They focus on data-driven applications in real scenarios, optimize business processes with the aid of FinTech, and monitor new ideas and trends in the tech space globally. Talent needs to be developed at all career levels starting from operators to technical experts, e.g., FIs need to develop a plan for FinTech career paths, and redesign leadership and technology tracks to keep critical talent engaged. In addition, the senior executives may consider revisiting their outsourcing strategy carefully.

FinTech innovations are transforming the nature of work every day. For example, the “lift and shift” Cloud migrations are toward Cloud-native platforms to scale the capability of “X-as-a-service” in distributed infrastructure; Machine Learning (ML) computing tends to use a privacy-enhanced computation environment for better security; cross-chain protocols and decentralized finance (DeFi) are becoming more robust for the Blockchain community; quantum computing are changing future banking’s computing infrastructure; and the metaverse might change the way how banks operate. To address the skill gaps, the talent pool needs to learn new skills if they are to fully participate in the new economy. The development of the talent pool is an ongoing and dynamic process.

To be agile, and actively taking a forwarding-looking approach for their technology pools, the FIs shall define a clear framework on technology evolution. That framework can be built based on the existing one, but shall be constantly adjusted and reconstructed to address new opportunities and challenges.

There are a few channels for FIs to grow their technology pool, including in-house development, acquiring other FinTech companies, purchasing IPs, as well as collaborating with vendors and institutions. For instance, while FIs can collaborate with external parties on the development of advanced AI technologies, such as transformers of NLP and AI-specific chip, they can also refine internal AI engineering, such as MLOps and responsible AI framework.

In addition to talent and technology, data is becoming one of the most valuable assets in FIs. Data usually forms the basis for business leaders to develop business strategies and turn opportunities into success. General concerns on the security of data collection and transmission, and the synergy between data processing, collaboration, and data sharing shall be embedded into the data pool construction.

Issues on data isolation, data privacy, and data quality could be overcome by integrating various technologies such as data middle platform, financial cloud, data fabric, data analytics store, and data mesh, into a unified framework. Once business requirements on business intelligence (BI) and AI are confirmed, FIs can decide on the form of fundamental data structure, i.e., data warehouse, data lake or data lakehouse. Based on the subscriptable data assets, FIs can build their technology and business platforms.

It is also important for FIs to build their open and innovative culture, with sound governance on risk control and regulatory compliance. FinTech innovations can be incremental or disruptive; while it brings enormous benefits for the efficiency of business decisions and operations, it could also lead to two major risks — (i) the risk associated with the technology, and (ii) the risk to new business driven by technology. For example, for scenario-based financial services (i.e., financial scenes), risks may come from process flow, data, transaction, and credit. Therefore, FIs must investigate sub-divided scenes to accurately acquire customers, accumulate scene data assets, control the use of credit line, and apply risk mitigation methods to relieve potential risks on operations, transaction, fraud, and default. For regulators, it is always important for them to drive the right directions. In other words, regulators shall also keep a close eye on emerging trends, and balance the needs between technology innovation and risk mitigation.

Finally, build the best FinTech ecosystem for your organization. Banking-as-a-Service (BaaS) is a natural expansion of open banking systems to enable FIs to penetrate other industries. FinTech-as-a-Service (FaaS), on the other hand, accelerates FIs’ adoption of new technical solutions from API platforms at FinTech firms. Their fusion further brings the so-called platformization ecosystem, which means services across different domains, such as transportation, healthcare, agriculture, education, construction, telecommunication, and pharmaceutics, are integrated into a common and unified platform. Through the ecosystem, FIs are in a better position to achieve their strategic objectives, such as financial democracy (e.g., Inclusive Finance), talent, and service diversity, as well as business sustainability (e.g., Green Finance and Carbon Neutrality), via this wide collaborative ecosystem.