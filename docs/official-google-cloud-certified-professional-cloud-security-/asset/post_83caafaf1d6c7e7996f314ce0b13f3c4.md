
![](img/f681dfc12450e3a4c257352b70dbceca_0_0.png)

# Google Cloud Certified Professional Cloud Security Engineer Exam Guide

Become an expert and get Google Cloud certified with this practitioner's guide

ANKUSH CHOWDHARY | PRASHANT KULKARNI

Foreword by: PHIL VENABLES CHIEF INFORMATION SECURITY OFFICER, GOOGLE CLOUD

# Official Google Cloud Certified Professional Cloud Security Engineer Exam Guide

Become an expert and get Google Cloud certified with this practitioner’s guide

Ankush Chowdhury and Prashant Kulkarni

![](img/f681dfc12450e3a4c257352b70dbceca_1_0.png)

# Official Google Cloud Certified Professional Cloud Security Engineer Exam Guide

Copyright © 2023 Packt Publishing

All rights reserved. No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by means, without the prior written permission of the publisher, except in the case of brief quotations embedded in critical articles or reviews.

Every effort has been made in the preparation of this book to ensure the accuracy of the information presented. However, the information contained in this book is sold without warranty, either express or implied. Neither the authors, nor Pact Publishing or its dealers and distributors, will be liable for any damages caused or alleged to have been caused directly or indirectly by this book.

Packt Publishing has endeavored to provide trademark information about all of the companies and products mentioned in this book by the appropriate use of capitals. However, Packt Publishing cannot guarantee the accuracy of this information.

**Authors:** Ankush Chowdhary and Prashant Kulkarni

**Reviewers:** Hector Diaz, Assaf Namer, Lanre Ogunmola, Holly Willey

**Managing Editor:** Arun Nadar

**Development Editor:** M Keerthi Nair

**Production Editor:** Shantanu Zagade

**Editorial Board:** Vijin Boricha, Megan Carlisle, Alex Mazonowicz, Aaron Nash, and Ankita Thakur

**First published:** July 2023

**Production reference:** 1280723

Published by Packt Publishing Ltd.
Grosvenor House
11 St Paul's Square
Birmingham
B31RB

ISBN 978-1-80056-492-3
www.packpub.com

# Foreword

We are digitizing the planet at an increasing pace. Small and large businesses, governments, and other public institutions, the daily fabric of our lives increasingly depend on reliable and secure systems.

More of these systems are now operating in one or more hyperscale cloud providers. Such cloud providers continue to invest in security as a reflection of their importance to customers in critical infrastructures and of their own desire to manage risk for large numbers of organizations. Increasing security, resilience, reliability, and compliance in the cloud, many organizations are moving more data and workloads to get these benefits.

At Google Cloud, we are committed to providing our customers with the most secure and reliable cloud platform possible and we have invested significantly in security by design and secure by default approaches to provide higher assurance to help customers operate securely.

Our goal is to make Google Cloud as easy to secure as possible, we know that designing, configuring, and operating large cloud deployments for real workloads requires solid expertise and experience. We also know that security is not just about technology. It's all about people.

At Google, we have been focused on developing the cybersecurity workforce through our cybersecurity certificate programs and many other resources that not only grow the number of people available to organizations to improve cybersecurity, but also increase their depth and special in important fields like cloud security. Our Professional Cloud Security Engineer certification is one of the most comprehensive and respected certifications in the industry. It is a valuable credential for professionals to demonstrate their expertise, and for organizations to know they're working with someone who has mastered expertise and is committed to the right security practices as encoded by Google Cloud security experts.

Anush and Prashant, in developing this Official Google Cloud Certified Professional Cloud Security Engineer Exam Guide, are providing an immensely resource for professionals to learn and ready themselves for this important certification in a field with high demand for such skills. The guide serves as the authoritative source aligned with the exam blueprint and offers professionals an easy way to study not just what's relevant to the exam, but further reading material and paths to additional Google Cloud-provided training courses.

Well-configured cloud services represent a significantly increased level of security for many organizations that will bring continued societal benefits. We hope with the expertise gained from your Google Cloud Certified Professional Cloud Engineer status, you will be part of this security evolution.

Phil Venables
Chief Information Security Officer, Google Cloud

> "One who can see that all activities are performed by the body, which is created of material nature, and sees that the self does nothing, truly sees".

– Bhagavad Gita 13:30

# Contributors

# About the authors

### Ankush Chowdhary, Vice President - CISO, HPE

With an unwavering focus on technology spanning over two decades, Ankush remains genuinely dedicated to the ever-evolving realm of cybersecurity. Throughout his career, he has consistently upheld a deep commitment to assisting businesses on their journey towards modernization and embracing the digital age. His guidance has empowered numerous enterprises to prioritize and implement essential cybersecurity measures. He has had the privilege of being invited as a speaker at various global cybersecurity events, where he had the opportunity to share his insights and exert influence key decision-makers concerning cloud security and policy matters. Driven by an authentic passion for education and mentorship, he derives immense satisfaction from guiding, and mentoring others within the intricate domain of cybersecurity. The intent behind writing this book has been a modest endeavor to achieve the same purpose.

I want to express my deepest gratitude for the completion of this book. This accomplishment is not solely mine; it is the result of the collective contributions and support from many individuals in my professional and personal life.

To my family, friends, and all who have supported me, thank you for being the guiding forces and pillars of strength through this journey. Your unwavering support and belief in my abilities have fueled my determination and kept me grounded.

I am grateful for the wisdom and insights shared by my colleagues and mentors. Your contributions have added depth and richness to the content of this book.

I dedicate this book to all of you, for your invaluable presence and the influence you have had on its creation. Your collective efforts have shaped its realization and made it a reality.

### Prashant Kulkarni, Cloud Security Architect, Google Cloud

In his career, Prashant has worked directly with customers, helping overcome different security challenges in various product areas. These experiences have made him passionate about continuous learning, especially in the fast-changing security landscape. Joining Google 4 years back, he expanded his knowledge of Cloud Security. He is thankful for the support of customers, the infosec community, and his peers that have sharpened his technical skills and improved his ability to explain complex security concepts in a user-friendly way. This book aims to share his experiences and insights, empowering readers to navigate the ever-evolving security landscape with confidence. In his free time, Prashant indulges in his passion for astronomy, marveling at the vastness and beauty of the universe.

I would like to thank my loving family and friends, including my supportive wife, my two wonderful children, my parents, and our goofy labradoodle.

I would like to dedicate this book to all the passionate learners and seekers of knowledge who embrace the joy of learning. It is a tribute to those who see challenges as opportunities for growth and relish the journey of acquiring new skills and insights. May this book serve as a guiding light, empowering you to overcome hurdles and unlock the boundless potential within the world of Google Cloud security engineering. Your unwavering dedication to craft inspires us all!

Last but not least, I would like to thank our publisher, Packt, and the whole editing team who worked tirelessly to make this book the best we could!
