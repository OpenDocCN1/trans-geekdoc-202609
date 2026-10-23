
## Research Methodology and Data Analysis

### Machine Learning Analysis of qPCR Data Using R

Luigi Marongiu

![](img/7ea01e6937e09d043e45c73fff9eaed3_0_0.png)

NOVA

![](img/7ea01e6937e09d043e45c73fff9eaed3_2_0.png)

No part of this digital document may be reproduced, stored in a retrieval system or transmitted in any form or by any means. The publisher has taken reasonable care in the preparation of this digital document, but makes no expressed or implied warranty of any kind and assumes no responsibility for any errors or omissions. No liability is assumed for incidental or consequential damages in connection with or arising out of information contained herein. This digital document is sold with the clear understanding that the publisher is not engaged in rendering legal, medical or any other professional services.

## Research Methodology and Data Analysis

- **E-Records Integrity Requirements**
  Orlando López  
  2022 ISBN: 978-1-68507-553-8 (Hardcover)  
  2022 ISBN: 978-1-68507-726-6 (eBook)

- **Predictive Analytics for Data Driven Decision Making – Tools and Techniques for Solving Real World Problems**
  B. Uma Maheswari, PhD, L. Ashok Kumar, PhD, R. Sujatha, PhD  
  2022 ISBN: 978-1-68507-650-4 (Hardcover)  
  2022 ISBN: 978-1-68507-770-9 (eBook)

- **Top 10 Challenges of Big Data Analytics**
  Maria José Sousa, PhD, Manuel Au-Yong Oliveira (Editors)  
  2021 ISBN: 978-1-53619-133-2 (Hardcover)  
  2021 ISBN: 978-1-53619-189-9 (eBook)

- **Validation of Instruments for the Investigation of Sexuality in Vulnerable Groups**
  Lubia del Carmen Castillo Arcos (Editor)  
  2020 ISBN: 978-1-53618-340-5 (Hardcover)  
  2020 ISBN: 978-1-53618-471-6 (eBook)

- **Statistical Modelling of Complex Correlated and Clustered Data: Household Surveys in Africa**
  Ngianga-Bakwin Kandala, PhD, Lawrence Kazembe, PhD (Editors)  
  2019 ISBN: 978-1-53615-981-3 (Hardcover)  
  2019 ISBN: 978-1-53615-982-0 (eBook)

More information about this series can be found at https://novapublishers.com/product-category/series/research-methodology-and-data-analysis/.

## Machine Learning Analysis of qPCR Data Using R

Luigi Marongiu

## Copyright © 2022 by Nova Science Publishers, Inc.

DOI: 10.52305/ZSFR3404.

All rights reserved. No part of this book may be reproduced, stored in a retrieval system or transmitted in any form or by any means: electronic, electrostatic, magnetic, tape, mechanical photocopying, recording or otherwise without the written permission of the Publisher.

We have partnered with Copyright Clearance Center to make it easy for you to obtain permissions to reuse content from this publication. Simply navigate to this publication’s page on Nova’s website and locate the “Get Permission” button below the title description. This button is linked directly to the title’s permission page on copyright.com. Alternatively, you can visit copyright.com and search by title, ISBN, or ISSN.

For further questions about using the service on copyright.com, please contact:

Copyright Clearance Center  
Phone: +1-(978) 750-8400  
Fax: +1-(978) 750-4470  
E-mail: info@copyright.com.

## Notice to the Reader

The Publisher has taken reasonable care in the preparation of this book, but makes no expressed or implied warranty of any kind and assumes no responsibility for any errors or omissions. No liability is assumed for incidental or consequential damages in connection with or arising out of information contained in this book. The Publisher shall not be liable for any special, consequential, or exemplary damages resulting, in whole or in part, from the readers’ use of, or reliance upon, this material. Any parts of this book based on government reports are so indicated and copyright is claimed for those parts to the extent applicable to compilations of such works.

Independent verification should be sought for any data, advice or recommendations contained in this book. In addition, no responsibility is assumed by the Publisher for any injury and/or damage to persons or property arising from any methods, products, instructions, ideas or otherwise contained in this publication.

This publication is designed to provide accurate and authoritative information with regard to the subject matter covered herein. It is sold with the clear understanding that the Publisher is not engaged in rendering legal or any other professional services. If legal or any other expert assistance is required, the services of a competent person should be sought. FROM A DECLARATION OF PARTICIPANTS JOINTLY ADOPTED BY A COMMITTEE OF THE AMERICAN BAR ASSOCIATION AND A COMMITTEE OF PUBLISHERS.

Additional color graphics may be available in the e-book version of this book.

## Library of Congress Cataloging-in-Publication Data

ISBN: 979-8-88697-380-8 (eBook)

Published by Nova Science Publishers, Inc. † New York

This book is dedicated to Bruno, who left too early, and to Prof. Sascha Venturelli, my first real mentor.

## Contents

- Acknowledgments ........................................................... ix
- Introduction ............................................................... xi
- Chapter 1 The Role of qPCR in the Diagnosis of Diseases ............... 1
- Chapter 2 Quantification by PCR ........................................... 39
- Chapter 3 Application of Machine Learning to *maxRatio* qPCR Analysis ............................................... 73
- Conclusion ............................................................... 121
- References ............................................................... 123
- Author’s Contact Information ............................................... 131
- Index ................................................................. 133

## Acknowledgments

I would like to thank Dr Maria Serena Beato and Dr Lara Cavicchio of the Laboratory of Virology, Istituto Zooprofilattico Sperimentale delle Venezie (Experimental Zooprophylactic Institute, Venice), Italy, for kindly providing the SIV data set. I am also indebted to Mr Eric Shain, the inventor of *maxRatio*, for his invaluable support and patience during the past years of collaboration and his critical reading of the manuscript.

## Introduction

The quantitative polymerase chain reaction (qPCR) is a versatile and popular assay for quantifying nucleic acids. With the recent expansion of the number of reactions per assay, there is a need for an accurate method to report the data suitable for automation. The present book will describe such a method, based on machine learning analysis, and implement it with publicly available tools. The book is intended for researchers and will provide a detailed introduction to the programming language R, including references for the most common functions. Thus, this work will provide an advanced strategy for the objective analysis of qPCR data suitable for experts in the field and an introduction to qPCR and computational analysis for the students.

## Chapter 1

### The Role of qPCR in the Diagnosis of Diseases

### Koch’s Postulates as Foundation of Diagnostics

The germ theory introduced by Louis Pasteur (Casanova and Abel, 2013) has one important corollary: to confirm the diagnosis of an infectious disease, physicians must somehow recover the suspected microbial pathogen from a patient’s specimen. This was not always the case: many esteemed professors and medical practitioners fiercely rejected the theses advanced not only by Pasteur but also by, to cite just a few, Friedrich Henle, Edwin Klebs and Robert Koch regarding the role of microbes in the establishment of diseases. Back in the day, the mainstream medicine favored the role of air and other pollutants as etiological factors (Elliott, 1870; Williams, 1871; Burns, 2007).

In a seminal work published in 1882, Koch wrote regarding his studies on the involvement of bacteria in the development of tuberculosis (Koch, 1882):

> To prove that tuberculosis is a parasitic disease… it was necessary to isolate the bacilli from the body: to grow them in pure culture… and, by administering the isolated bacilli to animals, to reproduce the same morbid condition.

He stressed such observations in 1890 (Koch, 1890):

> If, however, it can be proved: First, that the parasite is met with in each individual case of the particular disease and under conditions which correspond to the pathological changes and the clinical course of the disease; secondly, that in no other disease is found as an accidental non-pathogenic guest; and, thirdly, that if completely isolated from the body and cultivated in pure cultures with sufficient frequency, it can reproduce the disease — then it can no longer be considered an accidental accompaniment.
