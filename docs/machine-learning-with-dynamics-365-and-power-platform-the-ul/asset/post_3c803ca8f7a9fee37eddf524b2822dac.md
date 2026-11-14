

## FOREWORD BY RACHEL PROFITT
## AFTERWORD BY FAWAD KHAN

AURELIEN CLERE
VINNIE BANSAL

## MACHINE LEARNING WITH DYNAMICS 365 AND POWER PLATFORM

## THE ULTIMATE GUIDE TO APPLY PREDICTIVE ANALYTICS

![](img/62da674fd5b031cf7705f5424f5bc7c5_0_0.png)

WILEY

## Table of Contents

- Cover
- Title Page
- Copyright
- Foreword
- Preface
- WHY DID WE WRITE THIS BOOK?
- WHAT WAS THE INSPIRATION BEHIND THIS SUBJECT?
- Acknowledgments
- About the Authors
- CHAPTER 1: Dynamics 365, Power Platform, and Machine Learning
- INTRODUCTION TO DYNAMICS 365
- INTRODUCTION TO POWER PLATFORM
- WHAT IS MACHINE LEARNING: HOW HAS IT EVOLVED?
- DEFINITION OF MACHINE LEARNING
- CHAPTER 2: Artificial Intelligence and Pre-Built Machine Learning in Dynamics 365
- AZURE AI PLATFORM
- AZURE MACHINE LEARNING SERVICE
- KNOWLEDGE MINING
- CHAPTER 3: ML/AI Features and Their Applications in Dynamics 365
- VIRTUAL AGENT FOR CUSTOMER SERVICE IN DYNAMICS 365
- ARTIFICIAL INTELLIGENCE IN POWER APPS WITH AI BUILDER
- WHAT IS MIXED REALITY?
- CHAPTER 4: Dynamics 365 and Custom ML Models Using Azure ML
- CHAPTER 5: Deep Dive in Machine Learning Custom Models
- Chapter 6: Machine Learning with Dynamics 365 Use Cases
- ML FOR FINANCE
- DEMAND FORECASTING
- CONNECTED STORE
- ML FOR HUMAN RESOURCES MANAGEMENT
- MACHINE LEARNING AT THE WORKPLACE
- Afterword
- Index
- End User License Agreement

## List of Tables

Chapter 4
TABLE 4.1 Data guardrails.

## List of Illustrations

Chapter 1
- FIGURE 1.1 Understanding the three tools of the Power Platform.
- FIGURE 1.2 Evolution of machine learning.
- FIGURE 1.3 Machine learning lifecycle.
- FIGURE 1.4 Data preparation process.
- FIGURE 1.5 Machine learning algorithms.

Chapter 2
- FIGURE 2.1 Azure Cognitive Services.
- FIGURE 2.2 Types of vision APIs.
- FIGURE 2.3 Types of speech APIs.
- FIGURE 2.4 Speech services.
- FIGURE 2.5 Language services.
- FIGURE 2.6 Knowledge services.
- FIGURE 2.7 Bot building stages.
- FIGURE 2.8 Three phases of knowledge mining.

## Chapter 3

- FIGURE 3.1 Artificial intelligence capabilities within Customer Insights.
- FIGURE 3.2 Five elements of the card.
- FIGURE 3.3 Timeline of Dynamics 365 Sales.
- FIGURE 3.4 Untracked email with tracking link on right.
- FIGURE 3.5 How Power Apps can help organizations.
- FIGURE 3.6 Mixed Reality component.

## Chapter 4

- FIGURE 4.1 Select dataset.
- FIGURE 4.2 Upload your data file.
- FIGURE 4.3 Configure run.
- FIGURE 4.4 Select task and settings.
- FIGURE 4.5 Additional configurations.
- FIGURE 4.6 Pipeline.

## Chapter 6

- FIGURE 6.1 Automatic receipt recognition.

## MACHINE LEARNING WITH DYNAMICS 365 AND POWER PLATFORM

## The Ultimate Guide to Apply Predictive Analytics

AURELIEN CLERE
VINNIE BANSAL

WILEY

Copyright © 2022 by John Wiley & Sons, Inc. All rights reserved.

Published by John Wiley & Sons, Inc., Hoboken, New Jersey.
Published simultaneously in Canada.

No part of this publication may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, electronic, mechanical, photocopying, recording, scanning, or otherwise, except as permitted under Section 107 or 108 of the 1976 United States Copyright Act, without either the prior written permission of the Publisher, or authorization through payment of the appropriate per-copy fee to the Copyright Clearance Center, Inc., 222 Rosewood Drive, Danvers, MA 01923, (978) 750-8400, fax (978) 750-4470, or on the web at www.copyright.com. Requests to the Publisher for permission should be addressed to the Permissions Department, John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, (201) 748-6011, fax (201) 748-6008, or online at http://www.wiley.com/go/permission.

Limit of Liability/Disclaimer of Warranty: While the publisher and author have used their best efforts in preparing this book, they make no representations or warranties with respect to the accuracy or completeness of the contents of this book and specifically disclaim any implied warranties of merchantability or fitness for a particular purpose. No warranty may be created or extended by sales representatives or written sales materials. The advice and strategies contained herein may not be suitable for your situation. You should consult with a professional where appropriate. Neither the publisher nor author shall be liable for any loss of profit or any other commercial damages, including but not limited to special, incidental, consequential, or other damages.

For general information on our other products and services or for technical support, please contact our Customer Care Department within the United States at (800) 762-2974, outside the United States at (317) 572-3993 or fax (317) 572-4002.

Wiley also publishes its books in a variety of electronic formats. Some content that appears in print may not be available in electronic formats. For more information about Wiley products, visit our web site at www.wiley.com.

## Library of Congress Cataloging-in-Publication Data

Names: Clere, Aurelien, author. | Bansal, Vinnie, author.

Title: Machine learning with Dynamics 365 and Power Platform : the ultimate guide to apply predictive analytics / Aurelien Clere, Vinnie Bansal.

Description: Hoboken, New Jersey : Wiley, [2022] | Includes index.

Identifiers: LCCN 2021040966 (print) | LCCN 2021040967 (ebook) | ISBN 9781119771296 (cloth) | ISBN 9781119771319 (adobe pdf) | ISBN 9781119771302 (epub)

Subjects: LCSH: Microsoft Corporation. | Machine learning.

Classification: LCC Q325.5 .C54 2022 (print) | LCC Q325.5 (ebook) | DDC 006.3/1 –dc23
LC record available at https://lccn.loc.gov/2021040966
LC ebook record available at https://lccn.loc.gov/2021040967
Cover Design: Wiley
Cover Image: © Immersion Imagery/Shutterstock

## Foreword

YOU MIGHT BE WONDERING what machine learning and artificial intelligence (ML/AI) along with Microsoft Dynamics 365 and the Microsoft Power Platform have in common or even what they have to do with each other. But I might challenge you to think bigger and ask not what they have to do with each other; rather, ask how they can work together.

It is not enough these days to just implement your enterprise resource planning (ERP) or customer relationship management (CRM) system and walk away. Sure, you can optimize and improve business processes with a new system, but if you really want to digitally transform and reduce your operating costs to see the full return on investment, then you will need to look beyond just moving your basic business processes into a new system. This is where ML/AI can come into play.

Most organizations don't choose to replace their ERP system for the sake of replacement. Instead, ERP systems are replaced by necessity and a culmination of events and circumstances that usually require a system to be replaced. Replacing an ERP is a difficult and time-consuming process in and of itself, but you would be remiss to not consider how you can leverage emerging technologies such as ML/AI in this process to get more value out of your investment. Whether you are considering a new ERP, or you have been running Dynamics 365 for some time, this book offers practical advice for leveraging ML/AI to achieve more with your solution.

There are tons of books out there that can give you all the technical and mathematical theory that goes along with ML/AI, but this book is the first to bring real-life examples and experiences that show you how to apply ML/AI to your Dynamics 365 and Power Platform projects.

In my 12-part TechTalk series on using the Power Platform to extend Dynamics 365 Finance and Operations apps, one key message throughout is about using the technologies together to bring more value at a faster pace. The authors of this book capture this essence and take it three steps further by giving you all the details you need to be successful in making your solution come to life with Dynamics 365, the Power Platform, and ML/AI.

What I like about this book is that the authors really showcase their expertise. They provide not only real-life examples to help you relate to your business, but they also provide the details and technical advice required to achieve similar results in your own organization. I can recall the first time I worked with Aurelien to co-present at a virtual conference on the topic of virtual entities with Finance and Operations apps. His passion for adopting and using hot new technology was evident. The passion shown by Aurelien and Vinnie for helping the community with their knowledge and expertise has always been evident, and this book is just another great example. I believe that when you combine the passion for the technology with the passion for the community, the reader can only benefit from the knowledge and experience of the authors.

I recommend that you read this insightful book, full of practical advice and technical guidance no matter where you are in your Dynamics 365 implementation to help shape your digital transformation.

Rachel Profitt
Senior Program Manager, Microsoft

