
![](images/cover.jpg)

![Cover: Cause and Effect Business Analytics and Data Science, Chapman and Hall/CRC Series on Statistics in Business and Economics, written by Dominique Haughton, Jonathan Haughton, and Victor S.Y. Lo, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York, CRC Press is an imprint of the Taylor and Francis Group, an informa business, a Chapman and Hall book.](images/cover.jpg)

# CHAPMAN & HALL/CRC Series on Statistics in Business and Economics

The Chapman & Hall/CRC Series on Statistics in Business and Economics is a comprehensive collection of cutting-edge books dedicated to advancing the understanding and application of statistical methodologies in the realms of business and economics.

**Empirical Research in Accounting**
Tools and Methods
*Ian D. Gow and Tongqing Ding*

**Game Theory for Applied Econometricians**
Data Analytics with R
*Chritopher P. Adams*

**Bayesian Econometric Modelling for Big Data**
*Hang Qian*

**Cause and Effect Business Analytics and Data Science**
*Dominque Haughton, Jonathan Haughton, and Victor S. Y. Lo*

**Risk and Predictive Analytics in Business with R**
*Ozgur M. Araz and David L. Olson*

For more information about this series, please visit: [https://www.routledge.com/Chapman-and-HallCRC-Series-on-Statistics-in-Business-and-Economics/book-series/CHSBE](https://www.routledge.com/Chapman-and-HallCRC-Series-on-Statistics-in-Business-and-Economics/book-series/CHSBE)

Front cover image: filip robert/Shutterstock

First edition published 2026
by CRC Press
2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431
and by CRC Press
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

CRC Press is an imprint of Taylor & Francis Group, LLC

© 2026 Dominique Haughton, Jonathan Haughton, and Victor S.Y. Lo

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](https://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

Trademark notice: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

Library of Congress Cataloging-in-Publication Data
\[Insert LoC Data here when available\]

ISBN: 978-1-482-21647-9 (hbk)
ISBN: 978-1-041-07411-3 (pbk)
ISBN: 978-0-429-17258-8 (ebk)

DOI: [10.1201/9780429172588](https://doi.org/10.1201/9780429172588)

Typeset in Palatino
by KnowledgeWorks Global Ltd.

# About the Authors

**Dominique Haughton** (PhD MIT 1983) is a Professor Emerita of Mathematical Sciences and Global Studies at Bentley University near Boston, and an Affiliated Researcher at Université Paris 1 (Pantheon-Sorbonne, SAMM) and at Université Toulouse 1 (TSE-R). Her widely published work concentrates on how to best leverage modern analytics techniques to address questions of business or societal interest. She is an alumna of the Ecole Normale Supérieure and a Fellow of the American Statistical Association.

**Jonathan Haughton** earned his PhD in economics from Harvard University in 1983. He has published widely in the areas of economic development, taxation, the environment, and the analysis and measurement of poverty. Now emeritus, he chaired the economics department at Suffolk University, Boston, and he has taught or worked as a consultant in over 20 countries on five continents.

**Victor S.Y. Lo** is an executive with over three decades of consulting and corporate experience employing data-driven solutions in a wide variety of business areas, including Marketing, Risk Management, Financial Econometrics, Insurance, Product Development, Transportation, Healthcare, Operations Management, and Human Resources, and is a pioneer of uplift modeling. He is currently SVP, Data Science and AI at Fidelity Investments, and has led data science and analytics teams in various organizations. Victor earned a master's degree in Operational Research and a PhD in Statistics and was a Postdoctoral Fellow in Management Science.

# Acknowledgments

We would like to thank David Grubbs and his editorial team from CRC Press/Taylor & Francis for initiating the process for the book and for endless support, patience, and encouragement over the past decade. Thanks are also due to Mayank Sharma and the team at KnowledgeWorks Global for their expert editing.

We received very helpful reviews of drafts of our chapters from Alison Kelly, Jongbyung Jun, and Le (Sarah) Tang, all of from Suffolk University; and from Mingfei Li of Bentley University.

Dominique would like to thank Bentley University for its support over the years. And Jonathan is very grateful for support, including a sabbatical, from Suffolk University, which helped move the work forward.

First and foremost, Victor would like to thank the Lord Almighty for providing the opportunity, inspiration, and protection over the past many years during the writing of this book. He also would like to express his gratitude to his family for their gracious support over the countless number of weekends and their encouragement throughout this project. Last but not least, he would like to thank Jane Zheng and Karl Rexer for their valuable suggestions.

# 1 Introduction to Cause-and-Effect Business Analytics

DOI: [10.1201/9780429172588-1](https://doi.org/10.1201/9780429172588-1)

> *“In God we trust, all others bring data”*
>
> *W. Edwards Deming*

This book discusses two major related topics: Methods of causal analysis applied to business problems and uplift analytics. It is written to be accessible to anyone with a basic foundation in analytics, economics, statistics, marketing, and similar fields. It is likely to be useful for students in master's programs in related fields and for practitioners of analytics who want to expand their knowledge and skills.

The emphasis is on the concepts and on the essentials of important techniques. This should get the reader started, but mastery of any given technique will require further reading, digging, practice, and experimentation. We aim to provide the right path and the initial steps, but we have not written a programming cookbook, as we believe that readers should have little trouble finding the appropriate routines in Stata, SAS, Statistical Package for the Social Sciences (SPSS), R, Python, or in specialized software, once they know broadly what to look for.

The rest of this chapter discusses the importance of causality in thinking about business and suggests how readers may want to pick their way through the chapters in order to profit most fully from the book.

## 1.1 The Trend toward Business Analytics and Data Science
