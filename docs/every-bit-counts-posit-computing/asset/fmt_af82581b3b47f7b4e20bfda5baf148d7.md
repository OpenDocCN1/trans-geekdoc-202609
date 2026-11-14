
# Every Bit Counts: Posit Computing

![](images/cover.jpg)

![Cover: Every Bit Counts: Posit Computing, Chapman & Hall/CRC Computational Science, written by John L. Gustafson, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York, CRC Press is an imprint of the Taylor and Francis Group, an informa business, a Chapman and Hall book.](images/cover.jpg)

## Chapman & Hall/CRC Computational Science Series

**Series Editor:** Horst Simon and Doug Kothe

### Titles in this Series

- **Methods and Applications of Autonomous Experimentation**  
  *Daniela Ushizima, Marcus M. Noack*

- **Data-Intensive Science**  
  Terence Critchlow, Kerstin Kleese van Dam

- **Grid Computing: Techniques and Applications**  
  *Barry Wilkinson*

- **Scientific Computing with Multicore and Accelerators**  
  *Jakub Kurzak, David A. Bader, Jack Dongarra*

- **Introduction to the Simulation of Dynamics Using Simulink**  
  *Michael A. Gray*

- **Introduction to Scheduling**  
  *Yves Robert, Frederic Vivien*

- **Introduction to Modeling and Simulation with MATLAB® and Python**  
  *Steven I. Gordon, Brian Guilfoos*

- **Fundamentals of Multicore Software Development**  
  *Victor Pankratius, Ali-Reza Adl-Tabatabai, Walter Tichy*

- **Programming for Hybrid Multi/Manycore MPP Systems**  
  *John Levesque, Aaron Vose*

- **Exascale Scientific Applications: Scalability and Performance Portability**  
  *Tjerk P. Straatsma, Katerina B. Antypas, Timothy J. Williams*

- **GPU Parallel Program Development Using CUDA**  
  *Tolga Soyata*

- **Parallel Programming with Co-arrays**  
  *Robert W. Numrich*

- **Contemporary High Performance Computing: From Petascale toward Exascale, Volume 3**  
  *Jeffrey S. Vetter*

- **Unmatched: 50 Years of Supercomputing**  
  *David Barkai*

For more information about this series please visit: [https://www.crcpress.com/Chapman--HallCRC-Computational-Science/book-series/CHCOMPUTSCI](https://www.crcpress.com/Chapman--HallCRC-Computational-Science/book-series/CHCOMPUTSCI)

Designed cover image: Sumei Chew

MATLAB® and Simulink® are trademarks of The MathWorks, Inc. and are used with permission. The MathWorks does not warrant the accuracy of the text or exercises in this book. This book's use or discussion of MATLAB® or Simulink® software or related products does not constitute endorsement or sponsorship by The MathWorks of a particular pedagogical approach or particular use of the MATLAB® and Simulink® software.

## Publication Information

First edition published 2025 by CRC Press

2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2025 John L. Gustafson

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](https://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice:* Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

*Library of Congress Cataloging-in-Publication Data*

Names: Gustafson, John L., 1955-author.

Title: Every bit counts : posit computing / John L. Gustafson.

Description: First edition. | Boca Raton, FL : CRC Press, 2025. | Series: Chapman & Hall/CRC computational science | Includes bibliographical references and index. | Summary: “Written by one of the foremost experts in high-performance computing and the inventor of Gustafson's law, Every Bit Counts: Posit Computing explains the foundations of a new way for computers to calculate that saves time, storage, energy, and power by packing more information into every bit than do legacy approaches. Both the AI and HPC communities are increasingly using the posit approach that Gustafson introduced in 2017, which may be the future of technical computing. What may seem like a dry subject is made engaging by including the human and historical side of the struggle to represent numbers on machines. The book is richly illustrated in full color throughout, with every effort made to make the material as clear and accessible as possible, and even humorous. Starting with the simplest form of the idea, the chapters gradually add concepts according to stated mathematical and engineering design principles, building a robust tool kit for creating application-specific number systems. There is also a thorough explanation of the Posit Standard (2022), with motivations and examples that expand on that terse 12-page document”-- Provided by publisher.

Identifiers: LCCN 2024036235 (print) | LCCN 2024036236 (ebook) | ISBN 9781032738062 (hbk) | ISBN 9781032738055 (pbk) | ISBN 9781003466024 (ebk)

Subjects: LCSH: Computer science--Mathematics.

Classification: LCC QA76.9.M35 G84 2025 (print) | LCC QA76.9.M35 (ebook) | DDC 004.01/51--dc23/eng/20240910

LC record available at [https://lccn.loc.gov/2024036235](https://lccn.loc.gov/2024036235)

LC ebook record available at [https://lccn.loc.gov/2024036236](https://lccn.loc.gov/2024036236)

## ISBNs

- ISBN: 978-1-032-73806-2 (hbk)
- ISBN: 978-1-032-73805-5 (pbk)
- ISBN: 978-1-003-46602-4 (ebk)

DOI: [10.1201/9781003466024](https://doi.org/10.1201/9781003466024)

Typeset in Source Sans Pro by KnowledgeWorks Global Ltd.

*Publisher's note:* This book has been prepared from camera-ready copy provided by the authors.

## Dedication

For Nan Ripley, who is definitely not a number.

# Preface

![](images/pgxv_1.jpg)

In 1920, a chemist might write a scientific paper with language like this:

By around 1960, the wording would be more like this:

In the present day, I would not be surprised to see it written like this:

Technical writing seems to have acquired a style designed not so much to communicate to you as to impress you with how intelligent the author is. This is not that kind of book. Einstein once said, “You do not really understand something unless you can explain it to your grandmother.” So I wrote this book with that in mind and tested it. I had a grandmother (not mine) with no math training read it, and it passed. She totally gets it. (Thank you, Ms. Levitt!)

Even though this is a book about computer arithmetic, it is aimed at a general audience. It presents the human side of things using the historical record along with my own personal experiences. You do not need calculus or anything more advanced than a K-12 math background to read this book. I have done everything in my power to make this very dry subject as clear and interesting as possible. And sometimes funny. Borderline outrageous.
