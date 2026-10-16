
![image](images/Cover.jpg)

Multimodality Imaging, Volume 1

Deep learning applications

**Edited by**  
Mainak Biswas  
*Vignan’s Foundation for Science, Technology and Research, India*  
**Jasjit S Suri**  
*AtheroPoint(TM), Roseville, CA, USA*  
**IOP** Publishing, Bristol, UK  
© IOP Publishing Ltd 2022  
All rights reserved. No part of this publication may be reproduced, stored in a retrieval system or transmitted in any form or by any means, electronic, mechanical, photocopying, recording or otherwise, without the prior permission of the publisher, or as expressly permitted by law or under terms agreed with the appropriate rights organization. Multiple copying is permitted in accordance with the terms of licences issued by the Copyright Licensing Agency, the Copyright Clearance Centre and other reproduction rights organizations.

Permission to make use of IOP Publishing content other than as set out above may be sought at [permissions@ioppublishing.org](mailto:permissions@ioppublishing.org).

Mainak Biswas and Jasjit S Suri have asserted their right to be identified as the editors of this work in accordance with sections 77 and 78 of the Copyright, Designs and Patents Act 1988.

ISBN 978-0-7503-2244-7 (ebook)  
ISBN 978-0-7503-2242-3 (print)  
ISBN 978-0-7503-2245-4 (myPrint)  
ISBN 978-0-7503-2243-0 (mobi)  
DOI 10.1088/978-0-7503-2244-7  
Version: 20221201  
IOP ebooks  
British Library Cataloguing-in-Publication Data: A catalogue record for this book is available from the British Library.  
Published by IOP Publishing, wholly owned by The Institute of Physics, London  
IOP Publishing, No.2 The Distillery, Glassfields, Avon Street, Bristol, BS2 0GR, UK  
US Office: IOP Publishing, Inc., 190 North Independence Mall West, Suite 601, Philadelphia, PA 19106, USA  
To my late parents, and to my wife and daughter.  
—Mainak Biswas  
To all my collaborators around the world.  
—Jasjit S Suri  

# Contents

[Preface](#Preface.xhtml#tit1)

[Editor biographies](#Editor_biographies.xhtml#tit1)

[List of contributors](#Listofcontr.xhtml#tit1)

[Part I Deep learning and its applications](#Part_I.xhtml#bk978-0-7503-2244-7ptI)

[1 Deep learning and augmented radiology](#Chapter_1.xhtml#bk978-0-7503-2244-7ch1)

Mainak Biswas and Jasjit S Suri

[1.1 Introduction](#Chapter_1.xhtml#ST15)

[1.2 The present](#Chapter_1.xhtml#ST16)

[1.2.1 Fatty liver disease risk stratification](#Chapter_1.xhtml#ST17)

[1.2.2 Carotid intima–media thickness (cIMT) measurement using DL for segmentation](#Chapter_1.xhtml#ST18)

[1.2.3 Assessment of the treatment effects in acute ischemic stroke (AIS) using DL from MR images](#Chapter_1.xhtml#ST19)

[1.2.4 Diagnosis of prostate cancer using DL](#Chapter_1.xhtml#ST20)

[1.2.5 CT-based respiratory disease prognosis using DL](#Chapter_1.xhtml#ST21)

[1.3 Future](#Chapter_1.xhtml#ST22)

[1.3.1 DL in radiology](#Chapter_1.xhtml#ST23)

[1.3.2 The future of radiology](#Chapter_1.xhtml#ST24)

[1.4 The potential of deep learning](#Chapter_1.xhtml#ST25)

[1.4.1 Economy](#Chapter_1.xhtml#ST26)

[1.4.2 Augmented radiology and DL](#Chapter_1.xhtml#ST27)

[1.4.3 Further development of DL](#Chapter_1.xhtml#ST28)

[1.5 Challenges and risks in DL](#Chapter_1.xhtml#ST29)

[1.5.1 Safety](#Chapter_1.xhtml#ST30)

[1.5.2 Privacy](#Chapter_1.xhtml#ST31)

[1.5.3 Legality](#Chapter_1.xhtml#ST32)

[1.6 Conclusion](#Chapter_1.xhtml#ST33)

[References](#Chapter_1.xhtml#ST34)

[2 Deep learning in biomedical imaging](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2)

Mainak Biswas and Jasjit S Suri

[2.1 Introduction](#Chapter_2.xhtml#ST37)

[2.2 Deep learning models](#Chapter_2.xhtml#ST38)

[2.2.1 Deep belief networks](#Chapter_2.xhtml#ST39)

[2.2.2 Autoencoder](#Chapter_2.xhtml#ST40)

[2.2.3 Convolutional neural networks](#Chapter_2.xhtml#ST41)

[2.2.4 Deep residual network](#Chapter_2.xhtml#ST42)

[2.3 DL based biomedical imaging systems](#Chapter_2.xhtml#ST43)

[2.3.1 Cardiovascular application](#Chapter_2.xhtml#ST44)

[2.3.2 Neurology application](#Chapter_2.xhtml#ST50)

[2.3.3 Mammography application](#Chapter_2.xhtml#ST53)

[2.3.4 Microscopy applications](#Chapter_2.xhtml#ST56)

[2.3.5 Dermatology application](#Chapter_2.xhtml#ST59)

[2.3.6 Gastroenterology applications](#Chapter_2.xhtml#ST61)

[2.3.7 Pulmonary application](#Chapter_2.xhtml#ST63)

[2.4 Discussion](#Chapter_2.xhtml#ST65)

[2.4.1 Graphics processing unit and open-source software for deep learning](#Chapter_2.xhtml#ST66)

[References](#Chapter_2.xhtml#ST67)

[Part II Deep learning in brain imaging](#Part_II.xhtml#bk978-0-7503-2244-7ptII)

[3 A review of artificial intelligence in brain tumor classification and segmentation](#Chapter_3.xhtml#bk978-0-7503-2244-7ch3)

Mainak Biswas and Jasjit S Suri

[3.1 Introduction](#Chapter_3.xhtml#ST71)

[3.2 Brain cancer pathophysiology](#Chapter_3.xhtml#ST72)

[3.2.1 Architecture at the cellular level](#Chapter_3.xhtml#ST73)

[3.2.2 Links between brain tumors and genes](#Chapter_3.xhtml#ST74)

[3.3 Imaging modality](#Chapter_3.xhtml#ST75)

[3.3.1 Computed tomography imaging](#Chapter_3.xhtml#ST76)

[3.3.2 Magnetic resonance imaging](#Chapter_3.xhtml#ST77)

[3.3.3 Biopsy](#Chapter_3.xhtml#ST78)

[3.3.4 Hyperstereoscopy imaging](#Chapter_3.xhtml#ST79)

[3.3.5 MR spectroscopy](#Chapter_3.xhtml#ST80)

[3.4 Guidelines for tumor grading by the WHO](#Chapter_3.xhtml#ST81)

[3.5 Brain tumor tests](#Chapter_3.xhtml#ST82)

[3.5.1 Biomarker test](#Chapter_3.xhtml#ST83)

[3.5.2 Biopsy](#Chapter_3.xhtml#ST84)

[3.5.3 Imaging test](#Chapter_3.xhtml#ST85)

[3.6 Classification methods](#Chapter_3.xhtml#ST86)

[3.6.1 Machine learning](#Chapter_3.xhtml#ST87)

[3.6.2 Deep learning](#Chapter_3.xhtml#ST93)

[3.6.3 Brain image analysis using deep learning](#Chapter_3.xhtml#ST94)

[3.6.4 A plausible solution for brain cancer classification](#Chapter_3.xhtml#ST97)

[3.7 Brain cancer and other brain disorders](#Chapter_3.xhtml#ST98)

[3.7.1 Stroke](#Chapter_3.xhtml#ST99)

[3.7.2 Alzheimer’s disease](#Chapter_3.xhtml#ST100)

[3.7.3 Parkinson’s disease](#Chapter_3.xhtml#ST101)

[3.7.4 Leukoaraiosis](#Chapter_3.xhtml#ST102)

[3.7.5 Multiple sclerosis](#Chapter_3.xhtml#ST103)

[3.7.6 Wilson’s disease](#Chapter_3.xhtml#ST104)

[3.8 Discussion](#Chapter_3.xhtml#ST105)

[3.8.1 A note on cancer detection biomarkers](#Chapter_3.xhtml#ST106)

[3.9 Conclusion](#Chapter_3.xhtml#ST107)

[References](#Chapter_3.xhtml#ST108)

[4 MRI based brain tumor classification and its validation: a transfer learning paradigm](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4)

Luca Saba, Gopal S Tandel, Mainak Biswas, Michele Porcu, N N Khanna, Monica Turk, Christopher K Asare, Annabel A Ankrah and Jasjit S Suri

[4.1 Introduction](#Chapter_4.xhtml#ST111)

[4.2 Background literature survey](#Chapter_4.xhtml#ST112)

[4.3 Demographics and data preparation](#Chapter_4.xhtml#ST113)

[4.3.1 Patient demographics](#Chapter_4.xhtml#ST114)

[4.3.2 Data preparation](#Chapter_4.xhtml#ST115)

[4.4 Methodology](#Chapter_4.xhtml#ST116)

[4.4.1 CNN model](#Chapter_4.xhtml#ST117)

[4.4.2 The architecture of AlexNet](#Chapter_4.xhtml#ST118)

[4.4.3 Transfer learning and workflow](#Chapter_4.xhtml#ST119)

[4.4.4 Weight optimization](#Chapter_4.xhtml#ST120)

[4.4.5 A generalization system for tumor classification](#Chapter_4.xhtml#ST121)

[4.5 Experimental protocol, results, and performance evaluation](#Chapter_4.xhtml#ST122)

[4.5.1 Parameter selection and simulation](#Chapter_4.xhtml#ST123)

[4.5.2 Results](#Chapter_4.xhtml#ST124)

[4.5.3 Performance evaluation](#Chapter_4.xhtml#ST125)

[4.6 Model validation and verification](#Chapter_4.xhtml#ST126)

[4.6.1 Hypothesis validation](#Chapter_4.xhtml#ST127)

[4.6.2 Software verification](#Chapter_4.xhtml#ST128)

[4.7 Discussion](#Chapter_4.xhtml#ST129)

[4.8 Conclusion](#Chapter_4.xhtml#ST130)

[References](#Chapter_4.xhtml#ST132)

[5 Magnetic resonance based Wilson’s disease tissue characterization in an artificial intelligence framework using transfer learning](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5)
