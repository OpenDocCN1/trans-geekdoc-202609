
![](img/ec668102bd6cbe5645156f246a7c2e8b_0_0.png)

## Artificial Intelligence and Deep Learning in Pathology

EDITED BY
STANLEY COHEN

![](img/ec668102bd6cbe5645156f246a7c2e8b_0_1.png)

## Artificial Intelligence and Deep Learning in Pathology

Edited by

Stanley Cohen, M.D.

Emeritus Chair of Pathology & Emeritus Founding Director
Center for Biophysical Pathology
Rutgers-New Jersey Medical School, Newark, NJ, United States

Adjunct Professor of Pathology
Perelman Medical School
University of Pennsylvania, Philadelphia, PA, United States

Adjunct Professor of Pathology
Kimmel School of Medicine
Jefferson University, Philadelphia, PA, United States

Elsevier
Radarweg 29, PO Box 211, 1000 AE Amsterdam, Netherlands
The Boulevard, Langford Lane, Kidlington, Oxford OX5 1GB, United Kingdom
50 Hampshire Street, 5th Floor, Cambridge, MA 02139, United States

Copyright © 2021 Elsevier Inc. All rights reserved.

No part of this publication may be reproduced or transmitted in any form or by any means, electronic or mechanical, including photocopying, recording, or any information storage and retrieval system, without permission in writing from the publisher. Details on how to seek permission, further information about the Publisher's permissions policies and our arrangements with organizations such as the Copyright Clearance Center and the Copyright Licensing Agency, can be found at our website: www.elsevier.com/permissions.

This book and the individual contributions contained in it are protected under copyright by the Publisher (other than as may be noted herein).

## Notices

Knowledge and best practice in this field are constantly changing. As new research and experience broaden our understanding, changes in research methods, professional practices, or medical treatment may become necessary.

Practitioners and researchers must always rely on their own experience and knowledge in evaluating and using any information, methods, compounds, or experiments described herein. In using such information or methods they should be mindful of their own safety and the safety of others, including parties for whom they have a professional responsibility.

To the fullest extent of the law, neither the Publisher nor the authors, contributors, or editors, assume any liability for any injury and/or damage to persons or property as a matter of products liability, negligence or otherwise, or from any use or operation of any methods, products, instructions, or ideas contained in the material herein.

## Library of Congress Cataloging-in-Publication Data

A catalog record for this book is available from the Library of Congress

## British Library Cataloguing-in-Publication Data

A catalogue record for this book is available from the British Library

ISBN: 978-0-323-67538-3

For information on all Elsevier publications visit our website at https://www.elsevier.com/books-and-journals

Publisher: Dolores Meloni
Acquisitions Editor: Michael Houston
Editorial Project Manager: Sam W. Young
Project Manager: Niranjan Bhaskaran
Cover Designer: Alan Studholme

Typeset by TNQ Technologies

![](img/ec668102bd6cbe5645156f246a7c2e8b_2_0.png)

This book is dedicated to the American Society for Investigative Pathology, and especially Mark Sobel and Martha Furie, for supporting my efforts to proselytize on behalf of artificial intelligence in pathology. It is also dedicated to the members of the Warren Alpert Center for Digital and Computational Pathology at Memorial Sloan-Kettering, under the leadership of David Klimstra and Meera Hameed, for nourishing my enthusiasm for this revolution in pathology. I am especially indebted to both Dean Christine Palus and the Departments of Computer Science and Mathematics at Villanova University for enabling me to get up to speed rapidly in this relatively new interest of mine while being so accommodating and friendly to a student older than his teachers. Most important, it is also dedicated to my wonderful wife and scientific colleague Marion, children (Laurie, Ron, and Ken), kids-in-law (Ron, Helen, and Kim respectively), and grandkids (Jessica, Rachel, Joanna, Julie, Emi, Risa, Brian, Seiji, and Ava). With natural intelligence like that, who needs artificial intelligence?

## Contributors

- **Tanishq Abraham**
  Department of Biomedical Engineering, University of California, Davis, CA, United States
- **Ognjen Arandjelović, M.Eng. (Oxon), Ph.D. (Cantab)**
  School of Computer Science, University of St Andrews, St Andrews, United Kingdom
- **Peter D. Caie, BSc, MRes, PhD**
  School of Medicine, QUAD Pathology, University of St Andrews, St Andrews, United Kingdom
- **Stanley Cohen, MD**
  Emeritus Chair of Pathology & Emeritus Founding Director, Center for Biophysical Pathology, Rutgers-New Jersey Medical School, Newark, NJ, United States; Adjunct Professor of Pathology, Perelman Medical School, University of Pennsylvania, Philadelphia, PA, United States; Adjunct Professor of Pathology, Kimmel School of Medicine, Jefferson University, Philadelphia, PA, United States
- **Neofytos Dimitriou, B.Sc.**
  School of Computer Science, University of St Andrews, St Andrews, United Kingdom
- **Michael Donovan**
  Department of Pathology, Icahn School of Medicine at Mount Sinai, New York, NY, United States
- **Gerardo Fernandez**
  Department of Pathology, Icahn School of Medicine at Mount Sinai, New York, NY, United States
- **Rajarsi Gupta, MD, PhD**
  Assistant Professor, Biomedical Informatics, Stony Brook Medicine, Stony Brook, NY, United States
- **Richard Levenson, MD**
  Professor and Vice Chair, Pathology and Laboratory Medicine, UC Davis Health, Sacramento, CA, United States
- **Bahram Marami**
  Department of Pathology, Icahn School of Medicine at Mount Sinai, New York, NY, United States
- **Benjamin R. Mitchell, BA, MSE, PhD**
  Assistant Professor, Department of Computing Sciences, Villanova University, Villanova, PA, United States
- **Daniel A. Orringer, MD**
  Associate Professor, Department of Surgery, NYU Langone Health, New York City, NY, United States
- **Anil V. Parwani, MD, PhD, MBA**
  Professor, Pathology and Biomedical Informatics, The Ohio State University, Columbus, OH, United States
- **Marcel Prastawa**
  Department of Pathology, Icahn School of Medicine at Mount Sinai, New York, NY, United States
- **Abishek Sainath Madduri**
  Department of Pathology, Icahn School of Medicine at Mount Sinai, New York, NY, United States
- **Joel Haskin Saltz, MD, PhD**
  Professor, Chair, Biomedical Informatics, Stony Brook University, Stony Brook, NY, United States
- **Richard Scott**
  Department of Pathology, Icahn School of Medicine at Mount Sinai, New York, NY, United States
- **Austin Todd**
  UT Health, San Antonio, TX, United States
- **John E. Tomaszewski, MD**
  SUNY Distinguished Professor and Chair, Pathology and Anatomical Sciences, University at Buffalo, State University of New York, Buffalo, NY, United States
- **Jack Zeineh**
  Department of Pathology, Icahn School of Medicine at Mount Sinai, New York, NY, United States

## Preface

It is now well recognized that artificial intelligence (AI) represents an inflection point for society at least as profound as was the Industrial Revolution. It plays increasing roles in industry, education, recreation, and transportation, as well as science and engineering. As one example of its ubiquity, a recent headline proclaimed that “Novak Djokovic used AI to Train for Wimbledon!”

In particular, AI has become important for both biomedical research and clinical practice. Part of the reason for this is the sheer amount of data currently obtainable by modern techniques. In the past, we would study one or a few enzymes or transduction pathways at a time. Now we can sequence the entire genome, develop gene expression arrays that allow us to dissect out critical networks and pathways, study the entire microbiome instead of a few bacterial species in isolation, and so on. We can also use AI to look for important patterns in the massive data that have already been collected, i.e., data mining both in defined datasets and in natural language sources. Also, we can take advantage of the power of AI in pattern recognition to analyze and classify pictorial data not only for classification tasks but also to extract information not obvious to an individual limited to direct observations through the microscope, a device that has never received FDA approval.

Radiologists have been among the first clinical specialists to embrace AI to assist in the processing and interpretation of X-ray images. Pathologists have lagged, in part because the visual content of the images that pathologists use is at least an order of magnitude greater than those of radiology. Another factor has been the delay of the major industrial players to enter this arena, as well as limited hospital resources based on perceived differences in hospital profitability between radiology and pathology practices. However, more and more pathology departments are embracing digital pathology via whole slide imaging (WSI), and WSI provides the infrastructure both for advanced imaging modalities and the archiving of annotated datasets needed for AI training and implementation. An ever-increasing number of articles utilizing AI are appearing in the literature, and a number of professional societies devoted to this field have emerged. Existing societies and journals in pathology have begun to create subsections specifically devoted to AI.

Unfortunately, existing texts on machine learning, deep learning, and AI (terms that are distinct, but loosely overlap) tend to be either very general and superficial overviews for the layman or highly technical tomes assuming a background in linear algebra, multivariate calculus, and programming languages. They do not therefore serve as a useful introduction for most pathologists, as well as physicians in other
