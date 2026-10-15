
All rights reserved, including rights for text and data mining and training of artificial intelligence technologies or similar technologies. No part of this publication may be reproduced, stored in a retrieval system, or transmitted, in any form or by any means, electronic, mechanical, photocopying, recording or otherwise, except as permitted by law. Advice on how to obtain permission to reuse material from this title is available at [http://www.wiley.com/go/permissions](http://www.wiley.com/go/permissions).

The right of Jason Edwards to be identified as the author of this work has been asserted in accordance with law.

`Registered Offices`  

John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, USA  

John Wiley & Sons Ltd, New Era House, 8 Oldlands Way, Bognor Regis, West Sussex, PO22 9NQ, UK

For details of our global editorial offices, customer services, and more information about Wiley products visit us at [www.wiley.com](http://www.wiley.com).

The manufacturer's authorized representative according to the EU General Product Safety Regulation is Wiley-VCH GmbH, Boschstr. 12, 69469 Weinheim, Germany, e-mail: [Product_Safety@wiley.com](mailto:Product_Safety@wiley.com).

Wiley also publishes its books in a variety of electronic formats and by print-on-demand. Some content that appears in standard print versions of this book may not be available in other formats.

Trademarks: Wiley and the Wiley logo are trademarks or registered trademarks of John Wiley & Sons, Inc. and/or its affiliates in the United States and other countries and may not be used without written permission. All other trademarks are the property of their respective owners. John Wiley & Sons, Inc. is not associated with any product or vendor mentioned in this book.

`Limit of Liability/Disclaimer of Warranty`  

While the publisher and the authors have used their best efforts in preparing this work, including a review of the content of the work, neither the publisher nor the authors make any representations or warranties with respect to the accuracy or completeness of the contents of this work and specifically disclaim all warranties, including without limitation any implied warranties of merchantability or fitness for a particular purpose. No warranty may be created or extended by sales representatives, written sales materials or promotional statements for this work. The fact that an organization, website, or product is referred to in this work as a citation and/or potential source of further information does not mean that the publisher and authors endorse the information or services the organization, website, or product may provide or recommendations it may make. This work is sold with the understanding that the publisher is not engaged in rendering professional services. The advice and strategies contained herein may not be suitable for your situation. You should consult with a specialist where appropriate. Further, readers should be aware that websites listed in this work may have changed or disappeared between when this work was written and when it is read. Neither the publisher nor authors shall be liable for any loss of profit or any other commercial damages, including but not limited to special, incidental, consequential, or other damages.

`***Library of Congress Cataloging-in-Publication Data Applied for***`

Hardback ISBN:`9781394402038`  

ePDF ISBN:`9781394402052`  

ePUB ISBN:`9781394402045`

Cover Design:`Wiley`  

Cover Image:`© sankai/Getty Images`

`***To my beloved family. To my mom and dad, who are no longer with us but whose love and guidance continue to inspire me every day. To my wife, Selda, and my children, Michelle, Chris, Ceylin, and Mayra, for your endless love, patience, and encouragement. To my close family members: Derek, Meltem, Nilos, and Ken. And to my sisters, Robin, Kelly, and Lynn. This book is dedicated to you, with all my love and gratitude.***`

# Preface

Artificial intelligence has moved rapidly from research projects to systems that make decisions in healthcare, finance, defense, and daily life. With this growth comes a sobering reality: intelligent systems are vulnerable. They can be manipulated, deceived, or subverted in ways that traditional security practices were never designed to address. That reality is what inspired me to write this book.

For more than two decades, I have worked in cybersecurity, and in recent years, I have focused much of my effort on education—both in the classroom at several universities and through [BareMetalCyber.com](http://baremetalcyber.com), where I develop resources for learners and professionals alike. Across all of these settings, I have seen a growing demand for practical guidance on how to secure AI systems, not just how to build or apply them. Students, engineers, analysts, and executives all ask the same core questions: How do these attacks work? What risks do they pose? And what can we do to defend against them?

This book is written to answer those questions. It is intended for a wide range of readers—engineers and scientists designing AI models, security professionals tasked with defending them, students preparing to enter the field, and decision-makers who must evaluate risk and policy. Rather than simply cataloging threats, the chapters are designed to build a framework for understanding how adversaries operate and how defenders must respond. Throughout, I have included real-world examples, case studies, and exercises to make the material as relevant and actionable as possible.

The work I do with learners, both through Bare Metal Cyber and in academic programs, has shown me how vital it is to bridge theory with practice. That is the spirit in which this book is offered. My hope is that it not only equips readers with tools and knowledge but also encourages a culture of responsibility, resilience, and trust in the systems we are building for the future.

`*Dr. Jason Edwards*`

October 30<sup>(th)</sup>, 2025

New Braunfels, TX, USA

# Acknowledgments

I am deeply grateful to all those who have contributed to the creation of this book. First and foremost, I would like to express my heartfelt appreciation to my family for their unwavering support and understanding throughout the writing process. To my wife, Selda, and my children, Michelle, Chris, Ceylin, and Mayra, your patience and encouragement have been my anchor. I am also thankful for the love and support from my extended family: Derek, Meltem, Nilos, and Ken, and my sisters Robin, Kelly, and Lynn.

I am indebted to the organizations and the many fellow educators who have been pivotal in my professional development and the success of this book: Hallmark University, Moravian University, IronCircle, Cybrary, and the more than 100K LinkedIn subscribers who follow me.

To the millions of readers and listeners who follow my cybersecurity content each year on [BareMetalCyber.com](http://BareMetalCyber.com), your trust and engagement are the fuel that keeps this work moving forward. Thank you for making this journey possible.

I also encourage everyone reading this to support a cause close to my heart—the Beagle Freedom Project, which fights for the rights and rescue of animals used in laboratory testing. You can learn more about their work and my children's cybersecurity book series, starring Darwin the Cyber Beagle, at CyberBeagle.kids.

To find more of my books, check out CyberAuthor.Me. To join a community of Cybersecurity Professionals visit [BareMetalCyber.com](http://BareMetalCyber.com).

# From the Author
