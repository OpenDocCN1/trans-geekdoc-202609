

![](Images/9780137644728.jpg)

## About This eBook

ePUB is an open, industry-standard format for eBooks. However, support of ePUB and its many features varies across reading devices and applications. Use your device or app settings to customize the presentation to your liking. Settings that you can customize often include font, font size, single or double column, landscape or portrait mode, and figures that you can click or tap to enlarge. For additional information about the settings and features on your reading device or app, visit the device manufacturer’s Web site.

Many titles include programming code or configuration examples. To optimize the presentation of these elements, view the eBook in single-column, landscape mode and adjust the font size to the smallest setting. In addition to presenting code and configurations in the reflowable text format, we have included images of the code that mimic the presentation found in the print book; therefore, where the reflowable format may compromise the presentation of the code listing, you will see a “Click here to view code image” link. Click the link to view the print-fidelity code image. To return to the previous page viewed, click the Back button on your device or app.

# Model-Driven DevOps

# Model-Driven DevOps

Increasing agility and security in your physical network through DevOps

Steven Carter and Jason King

with

Josh Lothian and Mike Younkers

![](Images/pub.jpg)

Many of the designations used by manufacturers and sellers to distinguish their products are claimed as trademarks. Where those designations appear in this book, and the publisher was aware of a trademark claim, the designations have been printed with initial capital letters or in all capitals.

The authors and publisher have taken care in the preparation of this book, but make no expressed or implied warranty of any kind and assume no responsibility for errors or omissions. No liability is assumed for incidental or consequential damages in connection with or arising out of the use of the information or programs contained herein.

For information about buying this title in bulk quantities, or for special sales opportunities (which may include electronic versions; custom cover designs; and content particular to your business, training goals, marketing focus, or branding interests), please contact our corporate sales department at [corpsales@pearsoned.com](mailto:corpsales@pearsoned.com) or (800) 382-3419.

For government sales inquiries, please contact [governmentsales@pearsoned.com](mailto:governmentsales@pearsoned.com).

For questions about sales outside the U.S., please contact [intlcs@pearson.com](mailto:intlcs@pearson.com).

Visit us on the Web: [informit.com/aw](http://informit.com/aw)

Library of Congress Control Number: 2022938003

Copyright © 2023 Pearson Education, Inc.

All rights reserved. Printed in the United States of America. This publication is protected by copyright, and permission must be obtained from the publisher prior to any prohibited reproduction, storage in a retrieval system, or transmission in any form or by any means, electronic, mechanical, photocopying, recording, or likewise. For information regarding permissions, request forms and the appropriate contacts within the Pearson Education Global Rights & Permissions Department, please visit [www.pearsoned.com/permissions/](http://www.pearsoned.com/permissions/).

ISBN-13: 978-0-13-764467-4  

ISBN-10: 0-13-764467-1

**Editor-in-Chief**

Mark Taub

**Director, ITP Product Management**

Brett Bartow

**Executive Editor**

Nancy Davis

**Development Editor**

Christopher A. Cleveland

**Managing Editor**

Sandra Schroeder

**Senior Project Editor**

Tonya Simpson

**Copy Editor**

Chuck Hutchinson

**Indexer**

Erika Millen

**Proofreader**

Barbara Mack

**Technical Reviewer**

Gerald Dykeman

**Editorial Assistant**

Cindy Teeters

**Cover Designer**

Chuti Prasertsith

**Compositor**

codeMantra

## Pearson’s Commitment to Diversity, Equity, and Inclusion

Pearson is dedicated to creating bias-free content that reflects the diversity of all learners. We embrace the many dimensions of diversity, including but not limited to race, ethnicity, gender, socioeconomic status, ability, age, sexual orientation, and religious or political beliefs.

Education is a powerful force for equity and change in our world. It has the potential to deliver opportunities that improve lives and enable economic mobility. As we work with authors to create content for every product and service, we acknowledge our responsibility to demonstrate inclusivity and incorporate diverse scholarship so that everyone can achieve their potential through learning. As the world’s leading learning company, we have a duty to help drive change and live up to our purpose to help more people create a better life for themselves and to create a better world.

Our ambition is to purposefully contribute to a world where

*   Everyone has an equitable and lifelong opportunity to succeed through learning

*   Our educational products and services are inclusive and represent the rich diversity of learners

*   Our educational content accurately reflects the histories and experiences of the learners we serve

*   Our educational content prompts deeper discussions with learners and motivates them to expand their own learning (and worldview)

While we work hard to present unbiased content, we want to hear from you about any concerns or needs with this Pearson product so that we can investigate and address them.

Please contact us with concerns about any potential bias at [https://www.pearson.com/report-bias.html](https://www.pearson.com/report-bias.html).

*I dedicate this book to my beautiful wife, Ana, and my children, Renée, Michael, Andrew, Rita Maria, Therese, Emma, and Dominic. I am grateful to have had such amazing opportunities to work at companies with talented individuals that helped me build the experience presented in this book and provide a wonderful life for my family. My wife and children support me, inspire me, and love me.  

I thank God for them and all that He has given me.*

*—Steven Carter*

*I would like to dedicate this book to my wife, Erika, daughter, Julia, and son, Josh. It is* *cliche, but honestly, it would not have happened without them. It turns out that writing a book is not an individual effort undertaken solely by the author, but rather a team effort. Everybody on the team needs to make sacrifices, and my family certainly made many during the writing of this book. I sincerely hope that people find this book useful, because Erika has informed me that it is probably my last. It was unexpected, but I found great satisfaction in writing the fictional portions of this book. Who knows? Maybe I can convince her that Bob from ACME Corp is more than just a successful DevOps engineer, if only the world knew his shocking secret…*

*—Jason King*

## Table of Contents

[Chapter 1: A Lightbulb Goes Off](#ch01.xhtml#ch1)

[Enterprise IT as a Source of Risk to the Business](#ch01.xhtml#ch1lev1sec1)

[Observations of a Train Wreck](#ch01.xhtml#ch1lev2sec1)

[DevOps Seems Like a Better Way](#ch01.xhtml#ch1lev1sec2)

[What Is DevOps?](#ch01.xhtml#ch1lev2sec2)

[Automation](#ch01.xhtml#ch1lev2sec3)

[Infrastructure as Code](#ch01.xhtml#ch1lev2sec4)

[CI/CD](#ch01.xhtml#ch1lev2sec5)

[Apps vs. Infrastructure](#ch01.xhtml#ch1lev2sec6)

[Harnessing Automation-at-Scale](#ch01.xhtml#ch1lev2sec7)

[Why Are Enterprise IT Departments Not Adopting DevOps?](#ch01.xhtml#ch1lev1sec3)

[Human Factors](#ch01.xhtml#ch1lev2sec8)

[Business Factors](#ch01.xhtml#ch1lev2sec9)

[Summary](#ch01.xhtml#ch1lev1sec4)

[Chapter 2: A Better Way](#ch02.xhtml#ch2)

[The Goal: Business Transformation](#ch02.xhtml#ch2lev1sec1)

[Constraints-Based IT](#ch02.xhtml#ch2lev2sec1)

[Business Transformation](#ch02.xhtml#ch2lev2sec2)

[DevOps in Action](#ch02.xhtml#ch2lev2sec3)

